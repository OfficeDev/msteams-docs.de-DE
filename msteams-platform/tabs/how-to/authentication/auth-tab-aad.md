---
title: Authentifizierung für Registerkarten mit Azure Active Directory
description: Beschreibt die Authentifizierung in Teams und deren Verwendung auf Registerkarten
ms.topic: how-to
keywords: Teams-Authentifizierungsregisterkarten AAD
ms.openlocfilehash: 1502d2634b39230e0428863383bf97ada0be0359
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014565"
---
# <a name="authenticate-a-user-in-a-microsoft-teams-tab"></a>Authentifizieren eines Benutzers auf einer Microsoft Teams-Registerkarte

> [!Note]
> Damit die Authentifizierung für Ihre Registerkarte auf mobilen Clients funktioniert, müssen Sie sicherstellen, dass Sie Version 1.4.1 oder höher des JavaScript SDK für Teams verwenden.

Es gibt viele Dienste, die Sie in Ihrer Teams-App nutzen möchten, und die meisten dieser Dienste erfordern Authentifizierung und Autorisierung, um Zugriff auf den Dienst zu erhalten. Zu den Diensten gehören Facebook, Twitter und natürlich Teams. Benutzer von Teams verfügen über Benutzerprofilinformationen, die in Azure Active Directory (Azure AD) mithilfe von Microsoft Graph gespeichert sind, und dieser Artikel konzentriert sich auf die Authentifizierung mithilfe von Azure AD, um Zugriff auf diese Informationen zu erhalten.

OAuth 2.0 ist ein offener Standard für die Authentifizierung, der von Azure AD und vielen anderen Dienstanbietern verwendet wird. Das Verständnis von OAuth 2.0 ist eine Voraussetzung für die Arbeit mit der Authentifizierung in Teams und Azure AD. In den folgenden Beispielen wird der Fluss "Implizite OAuth 2.0-Genehmigung" verwendet, um schließlich die Profilinformationen des Benutzers aus Azure AD und Microsoft Graph zu lesen.

Der Code in diesem Artikel stammt aus dem Microsoft Teams-Beispiel für die Registerkartenauthentifizierung [der Microsoft Teams-Beispielanwendung (Node).](https://github.com/OfficeDev/microsoft-teams-sample-complete-node) Sie enthält eine statische Registerkarte, die ein Zugriffstoken für Microsoft Graph anfordert und die grundlegenden Profilinformationen des aktuellen Benutzers aus Azure AD zeigt.

Eine allgemeine Übersicht über den Authentifizierungsfluss für Registerkarten finden Sie im Thema [Authentifizierungsfluss auf Registerkarten.](~/tabs/how-to/authentication/auth-flow-tab.md)

Der Authentifizierungsfluss in Registerkarten unterscheidet sich geringfügig vom Authentifizierungsfluss in Bots.

## <a name="configuring-identity-providers"></a>Konfigurieren von Identitätsanbietern

Weitere Informationen [zum](~/concepts/authentication/configure-identity-provider.md) Konfigurieren von OAuth 2.0-Rückrufumleitungs-URL(n) bei Verwendung von Azure Active Directory als Identitätsanbieter finden Sie im Thema "Konfigurieren von Identitätsanbietern".

## <a name="initiate-authentication-flow"></a>Initiieren des Authentifizierungsflusses

Der Authentifizierungsfluss sollte durch eine Benutzeraktion ausgelöst werden. Sie sollten das Popupfenster für die Authentifizierung nicht automatisch öffnen, da dies wahrscheinlich den Popupblocker des Browsers auslöst und den Benutzer verwechselt.

Fügen Sie ihrer Konfigurations- oder Inhaltsseite eine Schaltfläche hinzu, damit sich der Benutzer bei Bedarf anmelden kann. Dies kann auf [](~/tabs/how-to/create-tab-pages/configuration-page.md) der Registerkartenkonfigurationsseite oder auf einer beliebigen [Inhaltsseite geschehen.](~/tabs/how-to/create-tab-pages/content-page.md)

Azure AD lässt wie die meisten Identitätsanbieter nicht zu, dass seine Inhalte in einem iFrame platziert werden. Dies bedeutet, dass Sie eine Popupseite hinzufügen müssen, um den Identitätsanbieter zu hosten. Im folgenden Beispiel ist diese Seite `/tab-auth/simple-start` . Verwenden Sie `microsoftTeams.authenticate()` die Funktion des Microsoft Teams-Client-SDK, um diese Seite zu starten, wenn Ihre Schaltfläche ausgewählt ist.

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

* Die URL, die Sie `microsoftTeams.authentication.authenticate()` übergeben, ist die Startseite des Authentifizierungsflusses. In diesem Beispiel ist dies `/tab-auth/simple-start` . Dies sollte mit dem übereinstimmen, was Sie im [Azure AD-Anwendungsregistrierungsportal registriert haben.](https://apps.dev.microsoft.com)

* Der Authentifizierungsfluss muss auf einer Seite in Ihrer Domäne beginnen. Diese Domäne sollte auch im Abschnitt [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) des Manifests aufgeführt werden. Andern wenn dies nicht der Fehler ist, wird ein leeres Popupfenster entsteht.

* Wenn sie nicht verwendet wird, wird ein Problem damit verursacht, dass das Popup am Ende des Anmeldevorgangs `microsoftTeams.authentication.authenticate()` nicht geschlossen wird.

## <a name="navigate-to-the-authorization-page-from-your-popup-page"></a>Navigieren Sie von Ihrer Popupseite zur Autorisierungsseite.

Wenn Ihre Popupseite ( `/tab-auth/simple-start` ) angezeigt wird, wird der folgende Code ausgeführt. Das Hauptziel dieser Seite besteht in der Umleitung an Ihren Identitätsanbieter, damit sich der Benutzer anmelden kann. Diese Umleitung kann auf der Serverseite mithilfe von HTTP 302 durchgeführt werden, in diesem Fall erfolgt sie jedoch auf Clientseite mithilfe eines Aufrufs von `window.location.assign()` . Dies ermöglicht auch das Abrufen von `microsoftTeams.getContext()` Hinweisinformationen, die an Azure AD übergeben werden können.

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

### <a name="notes"></a>Notes

* Informationen [zum Erstellen von Authentifizierungsanforderungen](~/tabs/how-to/access-teams-context.md) und URLs finden Sie unter "Informationen zum Benutzerkontext". Sie können beispielsweise den Anmeldenamen des Benutzers als Wert für die Azure AD-Anmeldung verwenden, was bedeutet, dass der Benutzer möglicherweise weniger `login_hint` eingeben muss. Denken Sie daran, dass Sie diesen Kontext nicht direkt als Identitätsnachweis verwenden sollten, da ein Angreifer Ihre Seite in einen schädlichen Browser laden und ihr beliebige Informationen bereitstellen kann.
* Obwohl der Registerkartenkontext nützliche Informationen zum Benutzer enthält, sollten Sie diese Informationen nicht verwenden, um den Benutzer zu authentifizieren, unabhängig davon, ob Sie sie als URL-Parameter zu Ihrer Registerkarteninhalts-URL oder durch Aufrufen der Funktion im `microsoftTeams.getContext()` Microsoft Teams-Client-SDK erhalten. Ein böswilliger Akteur könnte die URL des Registerkarteninhalts mit eigenen Parametern aufrufen, und eine Webseite, die die Identität von Microsoft Teams antsprecht, könnte die URL des Registerkarteninhalts in einem iframe laden und eigene Daten an die Funktion `getContext()` zurückgeben. Sie sollten die identitätsbezogenen Informationen im Registerkartenkontext einfach als Hinweise behandeln und vor der Verwendung überprüfen.
* Der Parameter wird verwendet, um zu bestätigen, dass der Dienst, der den `state` Rückruf-URI aufruft, der von Ihnen aufgerufene Dienst ist. Wenn der Parameter im Rückruf nicht mit dem Parameter, den Sie während des Anrufs gesendet haben, übereinstimmen, wird der Rückgabeaufruf nicht überprüft und sollte `state` beendet werden.
* Es ist nicht erforderlich, die Domäne des Identitätsanbieters in die Liste in der Datei des manifest.js`validDomains` hinzuzufügen.

## <a name="the-callback-page"></a>Die Rückrufseite

Im letzten Abschnitt haben Sie den Azure AD-Autorisierungsdienst aufgerufen und Benutzer- und App-Informationen übergeben, damit Azure AD dem Benutzer eine eigene, für die autorisierungsfreundliche Erfahrung bereitstellen kann. Ihre App hat keine Kontrolle darüber, was in dieser Erfahrung geschieht. Es weiß nur, was zurückgegeben wird, wenn Azure AD die von Ihnen bereitgestellte Rückrufseite aufruft ( `/tab-auth/simple-end` ).

Auf dieser Seite müssen Sie Erfolg oder Fehler basierend auf den von Azure AD zurückgegebenen Informationen und aufrufen oder `microsoftTeams.authentication.notifySuccess()` `microsoftTeams.authentication.notifyFailure()` ermitteln. Wenn die Anmeldung erfolgreich war, haben Sie Zugriff auf Dienstressourcen.

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

Dieser Code analysiert die Schlüssel-Wert-Paare, die von Azure AD empfangen werden, mithilfe `window.location.hash` der `getHashParameters()` Hilfsfunktion. Wenn eine gefunden wird und der Wert mit dem wert identisch ist, der zu Beginn des Authentifizierungsflusses angegeben wird, wird das Zugriffstoken durch Aufrufen an die Registerkarte zurückgegeben. Andernfalls wird ein Fehler mit `access_token` `state` `notifySuccess()` `notifyFailure()` gemeldet.

### <a name="notes"></a>Notes

`NotifyFailure()` hat die folgenden vordefinierten Fehlergründe:

* `CancelledByUser` Der Benutzer hat das Popupfenster geschlossen, bevor der Authentifizierungsfluss abgeschlossen wurde.
* `FailedToOpenWindow` Das Popupfenster konnte nicht geöffnet werden. Wenn Microsoft Teams in einem Browser ausgeführt wird, bedeutet dies in der Regel, dass das Fenster von einem Popupblocker blockiert wurde.

Wenn dies erfolgreich war, können Sie die Seite aktualisieren oder erneut laden und inhalte anzeigen, die für den jetzt authentifizierten Benutzer relevant sind. Wenn die Authentifizierung fehlschlägt, wird eine Fehlermeldung angezeigt.

Ihre App kann ein eigenes Sitzungscookie festlegen, sodass sich der Benutzer nicht erneut anmelden muss, wenn er zu Ihrer Registerkarte auf dem aktuellen Gerät zurückzukehren.

> [!NOTE]
> Chrome 80, das Anfang 2020 veröffentlicht werden soll, führt neue Cookiewerte ein und legt standardmäßig Cookierichtlinien fest. Es wird empfohlen, die beabsichtigte Verwendung für Ihre Cookies zu verwenden, anstatt sich auf das Standardverhalten des Browsers zu verlassen. *Siehe* [SameSite cookie attribute (2020 update)](../../../resources/samesite-cookie-update.md).

>[!NOTE]
>Um das richtige Token für Microsoft Teams Free- und Gastbenutzer zu erhalten, ist es wichtig, dass die Apps mandantenspezifische https://login.microsoftonline.com/ **Endpunkte {tenantId} verwenden.** Sie können tenantId aus der Botnachricht oder dem Registerkartenkontext erhalten. Wenn die Apps verwenden, erhalten die Benutzer falsche Token und melden sich beim "Home"-Mandanten anstatt beim Mandanten an, bei dem sie https://login.microsoftonline.com/common derzeit angemeldet sind.

Weitere Informationen zu einmaligem Sign-On (Single Sign-On, SSO) finden Sie im Artikel ["Automatische Authentifizierung".](~/tabs/how-to/authentication/auth-silent-AAD.md)

## <a name="samples"></a>Beispiele

Beispielcode, der den Prozess der Registerkartenauthentifizierung mit Azure AD zeigt, finden Sie unter:

* [Beispiel für die Microsoft Teams-Registerkartenauthentifizierung (Knoten)](https://github.com/OfficeDev/microsoft-teams-sample-auth-node)
