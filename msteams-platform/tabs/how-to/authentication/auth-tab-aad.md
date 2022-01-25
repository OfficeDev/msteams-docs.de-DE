---
title: Authentifizierung für Registerkarten mit Azure Active Directory
description: Beschreibt die Authentifizierung in Teams und deren Verwendung in Registerkarten
ms.topic: how-to
ms.localizationpriority: medium
keywords: Teams-Authentifizierungsregisterkarten Azure AD
ms.openlocfilehash: 6fb7e608cd89183a6207fc16b4e42a0e31e4db32
ms.sourcegitcommit: 7209e5af27e1ebe34f7e26ca1e6b17cb7290bc06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2022
ms.locfileid: "62212440"
---
# <a name="authenticate-a-user-in-a-microsoft-teams-tab"></a>Authentifizieren eines Benutzers auf einer Microsoft Teams Registerkarte

> [!Note]
> Damit die Authentifizierung für Ihre Registerkarte auf mobilen Clients funktioniert, müssen Sie sicherstellen, dass Sie Version 1.4.1 oder höher des Teams JavaScript SDK verwenden.

Es gibt viele Dienste, die Sie in Ihrer Teams-App nutzen möchten, und die meisten dieser Dienste erfordern Authentifizierung und Autorisierung, um Zugriff auf den Dienst zu erhalten. Zu den Diensten gehören Facebook, Twitter und Teams. Teams Benutzerprofilinformationen werden in Azure Active Directory unter Verwendung von Microsoft Graph gespeichert, und dieser Artikel konzentriert sich auf die Authentifizierung mit Azure AD, um Zugriff auf diese Informationen zu erhalten.

OAuth 2.0 ist ein offener Standard für die Authentifizierung, der von Azure AD und vielen anderen Dienstanbietern verwendet wird. Das Verständnis von OAuth 2.0 ist eine Voraussetzung für die Arbeit mit der Authentifizierung in Teams und Azure AD. In den folgenden Beispielen wird der Fluss "Implizite OAuth 2.0-Genehmigung" verwendet, um die Profilinformationen des Benutzers aus Azure AD und Microsoft Graph zu lesen.

Der Code in diesem Artikel stammt aus der Teams Beispiel-App [Microsoft Teams Registerkartenauthentifizierungsbeispiel (Node).](https://github.com/OfficeDev/microsoft-teams-sample-complete-node) Sie enthält eine statische Registerkarte, die ein Zugriffstoken für Microsoft Graph anfordert und die grundlegenden Profilinformationen des aktuellen Benutzers aus Azure AD anzeigt.

Eine allgemeine Übersicht über den Authentifizierungsfluss für Registerkarten finden Sie unter [Authentifizierungsfluss auf Registerkarten.](~/tabs/how-to/authentication/auth-flow-tab.md)

Der Authentifizierungsfluss in Registerkarten unterscheidet sich geringfügig vom Authentifizierungsfluss in Bots.

## <a name="configuring-identity-providers"></a>Konfigurieren von Identitätsanbietern

Ausführliche Schritte zum Konfigurieren von OAuth 2.0-Rückrufumleitungs-URL(n) bei Verwendung von Azure Active Directory als Identitätsanbieter finden Sie im Thema ["Konfigurieren](~/concepts/authentication/configure-identity-provider.md) von Identitätsanbietern".

## <a name="initiate-authentication-flow"></a>Initiieren des Authentifizierungsflusses

Der Authentifizierungsfluss sollte durch eine Benutzeraktion ausgelöst werden. Sie sollten das Authentifizierungs-Popup nicht automatisch öffnen, da dies wahrscheinlich den Popupblocker des Browsers auslöst und den Benutzer verwirren kann.

Fügen Sie ihrer Konfigurations- oder Inhaltsseite eine Schaltfläche hinzu, damit sich der Benutzer bei Bedarf anmelden kann. Dies kann auf der [Registerkartenkonfigurationsseite](~/tabs/how-to/create-tab-pages/configuration-page.md) oder auf einer beliebigen [Inhaltsseite](~/tabs/how-to/create-tab-pages/content-page.md) erfolgen.

Azure AD lässt wie die meisten Identitätsanbieter nicht zu, dass ihre Inhalte in einem iFrame platziert werden. Dies bedeutet, dass Sie eine Popupseite hinzufügen müssen, um den Identitätsanbieter zu hosten. Im folgenden Beispiel ist diese Seite `/tab-auth/simple-start` . Verwenden Sie die `microsoftTeams.authenticate()` Funktion des Microsoft Teams Client-SDKs, um diese Seite zu starten, wenn Die Schaltfläche ausgewählt ist.

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

### <a name="notes"></a>Anmerkungen

* Die URL, an die Sie übergeben, `microsoftTeams.authentication.authenticate()` ist die Startseite des Authentifizierungsflusses. In diesem Beispiel ist dies `/tab-auth/simple-start` . Dies sollte mit dem übereinstimmen, was Sie im [Azure AD Anwendungsregistrierungsportal](https://apps.dev.microsoft.com)registriert haben.

* Der Authentifizierungsfluss muss auf einer Seite beginnen, die sich in Ihrer Domäne befindet. Diese Domäne sollte auch im Abschnitt des Manifests aufgeführt [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) werden. Andernfalls wird ein leeres Popup angezeigt.

* Wenn sie nicht verwendet `microsoftTeams.authentication.authenticate()` wird, tritt ein Problem auf, wenn das Popup am Ende des Anmeldevorgangs nicht geschlossen wird.

## <a name="navigate-to-the-authorization-page-from-your-pop-up-page"></a>Navigieren Sie von ihrer Popupseite zur Autorisierungsseite

Wenn Die Popupseite ( `/tab-auth/simple-start` ) angezeigt wird, wird der folgende Code ausgeführt. Das Hauptziel dieser Seite besteht darin, zu Ihrem Identitätsanbieter umzuleiten, damit sich der Benutzer anmelden kann. Diese Umleitung kann serverseitig mit HTTP 302 erfolgen, in diesem Fall erfolgt die Umleitung jedoch auf clientseitiger Basis mithilfe eines Aufrufs von `window.location.assign()` . Dies ermöglicht auch das Abrufen von `microsoftTeams.getContext()` Hinweisinformationen, die an Azure AD übergeben werden können.

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
        scope: "https://graph.microsoft.com/User.Read openid",
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

Nachdem der Benutzer die Autorisierung abgeschlossen hat, wird der Benutzer zur Rückrufseite umgeleitet, die Sie für Ihre App unter angegeben `/tab-auth/simple-end` haben.

### <a name="notes"></a>Anmerkungen

* Hilfe beim Erstellen von Authentifizierungsanforderungen und URLs finden Sie unter "Abrufen von [Benutzerkontextinformationen".](~/tabs/how-to/access-teams-context.md) Sie können z. B. den Anmeldenamen des Benutzers als `login_hint` Wert für Azure AD Anmeldung verwenden, was bedeutet, dass der Benutzer möglicherweise weniger eingeben muss. Denken Sie daran, dass Sie diesen Kontext nicht direkt als Identitätsnachweis verwenden sollten, da ein Angreifer Ihre Seite in einem schädlichen Browser laden und ihm alle gewünschten Informationen bereitstellen könnte.
* Obwohl der Registerkartenkontext nützliche Informationen zum Benutzer bereitstellt, verwenden Sie diese Informationen nicht, um den Benutzer zu authentifizieren, unabhängig davon, ob Sie ihn als URL-Parameter zu Ihrer URL für Registerkarteninhalte erhalten, oder indem Sie die `microsoftTeams.getContext()` Funktion im Microsoft Teams-Client-SDK aufrufen. Ein böswilliger Akteur könnte Ihre URL für Registerkarteninhalte mit eigenen Parametern aufrufen, und eine Webseite, die Microsoft Teams ihre URL für Registerkarteninhalte in einem iframe laden und eigene Daten an die Funktion zurückgeben `getContext()` könnte. Sie sollten die identitätsbezogenen Informationen im Registerkartenkontext einfach als Hinweise behandeln und sie vor der Verwendung überprüfen.
* Der `state` Parameter wird verwendet, um zu bestätigen, dass der Dienst, der den Rückruf-URI aufruft, der von Ihnen aufgerufene Dienst ist. Wenn der `state` Parameter im Rückruf nicht mit dem Parameter übereinstimmt, den Sie während des Anrufs gesendet haben, wird der Rückgabeaufruf nicht überprüft und sollte beendet werden.
* Es ist nicht erforderlich, die Domäne des Identitätsanbieters in die `validDomains` Liste in der Manifest.json-Datei der App einzuschließen.

## <a name="the-callback-page"></a>Die Rückrufseite

Im letzten Abschnitt haben Sie den Azure AD Autorisierungsdienst aufgerufen und Benutzer- und App-Informationen übergeben, damit Azure AD dem Benutzer eine eigene benutzerdefinierte Autorisierungserfahrung präsentieren können. Ihre App hat keine Kontrolle darüber, was in dieser Oberfläche geschieht. Es weiß nur, was zurückgegeben wird, wenn Azure AD die von Ihnen bereitgestellte Rückrufseite aufruft ( `/tab-auth/simple-end` ).

Auf dieser Seite müssen Sie Erfolg oder Fehler anhand der Informationen bestimmen, die von Azure AD und Anruf oder zurückgegeben `microsoftTeams.authentication.notifySuccess()` `microsoftTeams.authentication.notifyFailure()` werden. Wenn die Anmeldung erfolgreich war, haben Sie Zugriff auf Dienstressourcen.

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

Dieser Code analysiert die Schlüssel-Wert-Paare, die von Azure AD `window.location.hash` mithilfe der Hilfsfunktion empfangen `getHashParameters()` wurden. Wenn ein Wert gefunden `access_token` wird und der Wert mit dem wert übereinstimmt, der zu Beginn des `state` Authentifizierungsflusses angegeben wurde, wird das Zugriffstoken durch Aufrufen an die Registerkarte `notifySuccess()` zurückgegeben. Andernfalls wird ein Fehler mit `notifyFailure()` gemeldet.

### <a name="notes"></a>Anmerkungen

`NotifyFailure()` hat die folgenden vordefinierten Fehlerursachen:

* `CancelledByUser` Der Benutzer hat das Popupfenster geschlossen, bevor er den Authentifizierungsfluss abgeschlossen hat.
* `FailedToOpenWindow` Das Popupfenster konnte nicht geöffnet werden. Wenn Microsoft Teams in einem Browser ausgeführt wird, bedeutet dies in der Regel, dass das Fenster durch einen Popupblocker blockiert wurde.

Wenn dies erfolgreich war, können Sie die Seite aktualisieren oder neu laden und Inhalte anzeigen, die für den jetzt authentifizierten Benutzer relevant sind. Wenn die Authentifizierung fehlschlägt, wird eine Fehlermeldung angezeigt.

Ihre App kann ein eigenes Sitzungscookie festlegen, damit sich der Benutzer nicht erneut anmelden muss, wenn er zu Ihrer Registerkarte auf dem aktuellen Gerät zurückkehrt.

> [!NOTE]
> Chrome 80, das Anfang 2020 veröffentlicht werden soll, führt neue Cookiewerte ein und erlegt standardmäßig Cookierichtlinien auf. Es wird empfohlen, die beabsichtigte Verwendung für Ihre Cookies festzulegen, anstatt sich auf das Standardverhalten des Browsers zu verlassen. *Siehe* [SameSite-Cookieattribut (Update 2020).](../../../resources/samesite-cookie-update.md)

>[!NOTE]
>Um das richtige Token für Microsoft Teams kostenlose und Gastbenutzer zu erhalten, ist es wichtig, dass die Apps mandantenspezifischen Endpunkt `https://login.microsoftonline.com/**{tenantId}**` verwenden. Sie können tenantId aus der Bot-Nachricht oder dem Registerkartenkontext abrufen. Wenn die Apps verwendet `https://login.microsoftonline.com/common` werden, erhalten die Benutzer falsche Token und melden sich beim "Home"-Mandanten anstelle des Mandanten an, bei dem sie derzeit angemeldet sind.

Weitere Informationen zu einzelnen Sign-On (Single Sign-On, SSO) finden Sie im Artikel ["Automatische Authentifizierung".](~/tabs/how-to/authentication/auth-silent-AAD.md)

## <a name="code-sample"></a>Codebeispiel

Beispielcode, der den Vorgang der Registerkartenauthentifizierung mit Azure AD zeigt:

| **Beispielname** | **description** | **.NET** | **Node.js** |
|-----------------|-----------------|-------------|
| Microsoft Teams Registerkartenauthentifizierung | Registerkartenauthentifizierungsprozess mit Azure AD. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-channel-group-config-page-auth/csharp) | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-auth/nodejs) |

## <a name="see-also"></a>Siehe auch

* [Planen der Benutzerauthentifizierung](../../../concepts/design/understand-use-cases.md#provide-authentication)
* [Entwerfen Sie Ihre Registerkarte für Microsoft Teams](~/tabs/design/tabs.md)
* [Automatische Authentifizierung](~/tabs/how-to/authentication/auth-silent-aad.md)
* [Hinzufügen einer Authentifizierung zu Ihrer Messaging-Erweiterung](~/messaging-extensions/how-to/add-authentication.md)
* [SSO-Unterstützung (Single Sign-On) für Bots](~/bots/how-to/authentication/auth-aad-sso-bots.md)
