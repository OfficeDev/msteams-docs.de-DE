---
title: Authentifizierung für Registerkarten mit Azure Active Directory
description: Beschreibung der Authentifizierung in Microsoft Teams und ihrer Verwendung in Registerkarten
keywords: Teams-Authentifizierungs Registerkarten Aad
ms.openlocfilehash: a1d3a96e23706012b643b5827701b49e2306d847
ms.sourcegitcommit: f9a2f5cedc9d30ef7a9cf78a47d01cfd277e150d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "48237783"
---
# <a name="authenticate-a-user-in-a-microsoft-teams-tab"></a>Authentifizieren eines Benutzers auf einer Microsoft Teams-Registerkarte

> [!Note]
> Damit die Authentifizierung für Ihre Registerkarte auf mobilen Clients funktioniert, müssen Sie sicherstellen, dass Sie die Version 1.4.1 oder höher des Microsoft Teams-JavaScript-SDK verwenden.

Es gibt viele Dienste, die Sie in Ihrer Teams-App möglicherweise nutzen möchten, und die meisten dieser Dienste erfordern Authentifizierung und Autorisierung, um Zugriff auf den Dienst zu erhalten. Zu den Diensten gehören Facebook, Twitter und natürlich Teams. Benutzer von Teams haben Benutzerprofilinformationen, die in Azure Active Directory (Azure AD) mit Microsoft Graph gespeichert sind, und dieser Artikel konzentriert sich auf die Authentifizierung mithilfe von Azure AD, um Zugriff auf diese Informationen zu erhalten.

OAuth 2,0 ist ein offener Standard für die Authentifizierung, der von Azure AD und vielen anderen Dienstanbietern verwendet wird. Das Verständnis von OAuth 2,0 ist eine Voraussetzung für die Verwendung der Authentifizierung in Microsoft Teams und Azure AD. Die folgenden Beispiele verwenden den impliziten Grant-Fluss von OAuth 2,0 mit dem Ziel, die Profilinformationen des Benutzers schließlich aus Azure AD und Microsoft Graph zu lesen.

Der Code in diesem Artikel stammt aus dem Beispiel für [Microsoft Teams-Beispiel-App-Registerkarten Authentifizierung (Knoten)](https://github.com/OfficeDev/microsoft-teams-sample-complete-node). Sie enthält eine statische Registerkarte, die ein Zugriffstoken für Microsoft Graph anfordert und die grundlegenden Profilinformationen des aktuellen Benutzers aus Azure AD anzeigt.

Eine allgemeine Übersicht über den Authentifizierungs Fluss für Registerkarten finden Sie im Thema [Authentifizierungs Fluss in Registerkarten](~/tabs/how-to/authentication/auth-flow-tab.md).

Der Authentifizierungs Fluss in Registerkarten unterscheidet sich geringfügig vom Authentifizierungs Fluss in Bots.

## <a name="configuring-identity-providers"></a>Konfigurieren von Identitätsanbietern

Lesen Sie das Thema [configure Identity Providers](~/concepts/authentication/configure-identity-provider.md) for ausführliche steps on Configuring OAuth 2,0 Callback Redirect URL (s) bei Verwendung von Azure Active Directory als Identitätsanbieter.

## <a name="initiate-authentication-flow"></a>Initiieren des Authentifizierungs Flusses

Der Authentifizierungs Fluss sollte durch eine Benutzeraktion ausgelöst werden. Sie sollten das Authentifizierungs Popup nicht automatisch öffnen, da dies wahrscheinlich den Popupblocker des Browsers auslösen und den Benutzer verwirren kann.

Fügen Sie Ihrer Konfiguration oder Inhaltsseite eine Schaltfläche hinzu, um dem Benutzer die Anmeldung bei Bedarf zu ermöglichen. Dies kann auf der Seite "Tab- [Konfiguration](~/tabs/how-to/create-tab-pages/configuration-page.md) " oder einer beliebigen [Inhalts](~/tabs/how-to/create-tab-pages/content-page.md) Seite erfolgen.

Azure AD, wie bei den meisten Identitätsanbietern, lässt nicht zu, dass der Inhalt in einen iframe eingefügt wird. Dies bedeutet, dass Sie eine Popupseite zum Hosten des Identitätsanbieters hinzufügen müssen. Im folgenden Beispiel ist diese Seite `/tab-auth/simple-start` . Verwenden Sie die `microsoftTeams.authenticate()` Funktion des Microsoft Teams-Client-SDK, um diese Seite zu starten, wenn Ihre Schaltfläche ausgewählt ist.

```javascript
microsoftTeams.authentication.authenticate({
    url: window.location.origin + "/tab-auth/simple-start",
    width: 600,
    height: 535,
    successCallback: function (result) {
        getUserProfile(result.accessToken);
    },
    failureCallback: function (reason) {
        handleAuthError(reason);
    }
});
```

### <a name="notes"></a>Notes

* Die URL, an die Sie übergeben werden, `microsoftTeams.authentication.authenticate()` ist die Startseite des Authentifizierungs Flusses. In diesem Beispiel ist dies `/tab-auth/simple-start` . Dies sollte mit dem übereinstimmen, was Sie im [Azure AD-Anwendungs Registrierungs Portal](https://apps.dev.microsoft.com)registriert haben.

* Der Authentifizierungs Fluss muss auf einer Seite beginnen, die sich in Ihrer Domäne befindet. Diese Domäne sollte auch im [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) Abschnitt des Manifests aufgeführt werden. Andernfalls wird ein leeres Popup angezeigt.

* Wenn die Verwendung `microsoftTeams.authentication.authenticate()` nicht möglich ist, wird das Popup-Fenster am Ende des Anmeldevorgangs nicht geschlossen.

## <a name="navigate-to-the-authorization-page-from-your-popup-page"></a>Navigieren Sie von ihrer Popupseite zur Autorisierungs Seite.

Wenn Ihre Popup-Seite ( `/tab-auth/simple-start` ) angezeigt wird, wird der folgende Code ausgeführt. Das Hauptziel dieser Seite ist die Umleitung an Ihren Identitätsanbieter, damit der Benutzer sich anmelden kann. Diese Umleitung kann auf der Serverseite mithilfe von HTTP 302 ausgeführt werden, in diesem Fall wird Sie jedoch auf der Clientseite mit einem Aufruf von ausgeführt `window.location.assign()` . Dies ermöglicht auch das `microsoftTeams.getContext()` Abrufen von Hinweis Informationen, die an Azure AD übergeben werden können.

```javascript
microsoftTeams.getContext(function (context) {
    // Generate random state string and store it, so we can verify it in the callback
    let state = _guid(); // _guid() is a helper function in the sample
    localStorage.setItem("simple.state", state);
    localStorage.removeItem("simple.error");
    // Go to the Azure AD authorization endpoint
    let queryParams = {
        client_id: "YOUR_APP_ID_HERE",
        response_type: "id_token token",
        response_mode: "fragment",
        resource: "https://graph.microsoft.com/User.Read openid",
        redirect_uri: window.location.origin + "/tab-auth/simple-end",
        nonce: _guid(),
        state: state,
        // The context object is populated by Teams; the loginHint attribute
         // is used as hinting information
        login_hint: context.loginHint,
    };

    let authorizeEndpoint = "https://login.microsoftonline.com/" + context.tid + "/oauth2/v2.0/authorize?" + toQueryString(queryParams);
    window.location.assign(authorizeEndpoint);
});
```

Nachdem der Benutzer die Autorisierung abgeschlossen hat, wird der Benutzer zur Rückruf Seite umgeleitet, die Sie für Ihre APP unter angegeben haben `/tab-auth/simple-end` .

### <a name="notes"></a>Notes

* Informationen zum Erstellen von Authentifizierungsanforderungen und-URLs finden Sie unter [Abrufen von Benutzerkontextinformationen](~/tabs/how-to/access-teams-context.md) . Sie können beispielsweise den Anmeldenamen des Benutzers als `login_hint` Wert für Azure AD Anmeldung verwenden, was bedeutet, dass der Benutzer möglicherweise less eingeben muss. Denken Sie daran, dass Sie diesen Kontext nicht direkt als Identitätsnachweis verwenden sollten, da ein Angreifer die Seite in einen bösartigen Browser laden und ihm alle gewünschten Informationen bereitstellen kann.
* Obwohl der Registerkartenkontext nützliche Informationen für den Benutzer bereitstellt, verwenden Sie diese Informationen nicht, um den Benutzer zu authentifizieren, unabhängig davon, ob Sie ihn als URL-Parameter zu ihrer Registerkarten-Inhalts-URL oder durch Aufrufen der `microsoftTeams.getContext()` Funktion im Microsoft Teams-Client-SDK erhalten. Ein böswilliger Akteur könnte Ihre Registerkarteninhalts-URL mit seinen eigenen Parametern aufrufen, und eine Webseite, die Microsoft Teams imitiert, kann die URL Ihres Registerkarteninhalts in einen iframe laden und eigene Daten an die Funktion zurückgeben `getContext()` . Sie sollten die identitätsbezogenen Informationen im Registerkartenkontext lediglich als Hinweise behandeln und diese vor der Verwendung validieren.
* Der `state` -Parameter wird verwendet, um zu bestätigen, dass der Dienst, der den Rückruf-URI aufruft, der von Ihnen aufgerufene Dienst ist. Wenn der `state` Parameter im Rückruf nicht mit dem Parameter übereinstimmt, den Sie während des Anrufs gesendet haben, wird der Rückgabe Aufruf nicht überprüft und sollte beendet werden.
* Es ist nicht erforderlich, die Domäne des Identitätsanbieters in die `validDomains` Liste im manifest.jsder app in der Datei einzuschließen.

## <a name="the-callback-page"></a>Die Rückruf Seite

Im letzten Abschnitt haben Sie den Azure AD Autorisierungsdienst aufgerufen und in Benutzer-und App-Informationen übergeben, damit Azure AD dem Benutzer eine eigene monolithische Autorisierungs Erfahrung präsentieren kann. Ihre APP hat keine Kontrolle darüber, was in dieser Erfahrung geschieht. Er weiß nur, was zurückgegeben wird, wenn Azure Ad die von Ihnen angegebene Rückruf Seite aufruft ( `/tab-auth/simple-end` ).

Auf dieser Seite müssen Sie den Erfolg oder Misserfolg basierend auf den von Azure AD und Call oder zurückgegebenen Informationen ermitteln `microsoftTeams.authentication.notifySuccess()` `microsoftTeams.authentication.notifyFailure()` . Wenn die Anmeldung erfolgreich verlaufen ist, haben Sie Zugriff auf Dienst Ressourcen.

````javascript
// Split the key-value pairs passed from Azure AD
// getHashParameters is a helper function that parses the arguments sent
// to the callback URL by Azure AD after the authorization call
let hashParams = getHashParameters();
if (hashParams["error"]) {
    // Authentication/authorization failed
    microsoftTeams.authentication.notifyFailure(hashParams["error"]);
} else if (hashParams["access_token"]) {
    // Get the stored state parameter and compare with incoming state
    // This validates that the data is coming from Azure AD
    let expectedState = localStorage.getItem("simple.state");
    if (expectedState !== hashParams["state"]) {
        // State does not match, report error
        microsoftTeams.authentication.notifyFailure("StateDoesNotMatch");
    } else {
        // Success: return token information to the tab
        microsoftTeams.authentication.notifySuccess({
            idToken: hashParams["id_token"],
            accessToken: hashParams["access_token"],
            tokenType: hashParams["token_type"],
            expiresIn: hashParams["expires_in"]
        })
    }
} else {
    // Unexpected condition: hash does not contain error or access_token parameter
    microsoftTeams.authentication.notifyFailure("UnexpectedFailure");
}
````

Dieser Code analysiert die Schlüssel-Wert-Paare, die von Azure AD in `window.location.hash` mit der `getHashParameters()` Hilfsfunktion empfangen werden. Wenn er einen findet `access_token` und der Wert mit dem `state` identisch ist, der am Anfang des Authentifizierungs Flusses bereitgestellt wurde, wird das Zugriffstoken durch Aufrufen an die Registerkarte zurückgegeben `notifySuccess()` ; andernfalls meldet er einen Fehler mit `notifyFailure()` .

### <a name="notes"></a>Notes

`NotifyFailure()` weist die folgenden vordefinierten Fehlerursachen auf:

* `CancelledByUser` der Benutzer hat das Popupfenster geschlossen, bevor der Authentifizierungs Fluss abgeschlossen wurde.
* `FailedToOpenWindow` das Popupfenster konnte nicht geöffnet werden. Bei der Ausführung von Microsoft Teams in einem Browser bedeutet dies normalerweise, dass das Fenster von einem Popupblocker blockiert wurde.

Wenn die Methode erfolgreich verläuft, können Sie die Seite aktualisieren oder neu laden und Inhalte anzeigen, die für den jetzt authentifizierten Benutzer relevant sind. Wenn die Authentifizierung fehlschlägt, wird eine Fehlermeldung angezeigt.

Ihre APP kann ein eigenes Sitzungscookie festlegen, sodass sich der Benutzer nicht erneut anmelden muss, wenn er zur Registerkarte auf dem aktuellen Gerät zurückkehrt.

> [!NOTE]
> In Chrome 80, das für die Veröffentlichung Anfang 2020 vorgesehen ist, werden neue Cookiewerte eingeführt und standardmäßig Cookie-Richtlinien auferlegt. Es wird empfohlen, dass Sie die vorgesehene Verwendung für Ihre Cookies festlegen, anstatt sich auf das Standardbrowser Verhalten zu verlassen. *Siehe* [SameSite-Cookie-Attribut (2020 Update)](../../../resources/samesite-cookie-update.md).

>[!NOTE]
>Um das richtige Token für Microsoft Teams kostenlos und Gastbenutzer zu erhalten, ist es wichtig, dass die apps Mandanten spezifischer Endpunkt https://login.microsoftonline.com/ **{Mandanten**-Nr} verwenden. Sie können die Mandanten-Nr aus der bot-Nachricht oder dem Tab-Kontext abrufen. Wenn die apps verwendet werden https://login.microsoftonline.com/common , erhalten die Benutzer falsche Token und melden sich am "Home"-Mandanten anstelle des Mandanten an, an dem Sie derzeit angemeldet sind.

Weitere Informationen zum einmaligen Anmelden (SSO) finden Sie im Artikel [Silent Authentication](~/tabs/how-to/authentication/auth-silent-AAD.md).

## <a name="samples"></a>Beispiele

Beispielcode zum Anzeigen des Registerkarten Authentifizierungsprozesses mit Azure AD finden Sie unter:

* [Beispiel für Microsoft Teams-Registerkarten Authentifizierung (Knoten)](https://github.com/OfficeDev/microsoft-teams-sample-auth-node)
