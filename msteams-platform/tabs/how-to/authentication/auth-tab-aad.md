---
title: Konfigurieren der OAuth-Authentifizierung von Drittanbietern
description: In diesem Artikel lernen Sie die Registerkarten für die Teams-Authentifizierung Microsoft Azure AD, die Authentifizierung in Teams und die Verwendung in Registerkarten kennen.
ms.topic: how-to
ms.localizationpriority: medium
ms.openlocfilehash: 1afc7e7512c75c9002849801cfc14fb8eb1aa726
ms.sourcegitcommit: 36c6a5ba1dcd27a15ba31f479e534eab69aa17e1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2022
ms.locfileid: "67465372"
---
# <a name="configure-third-party-oauth-idp-authentication"></a>Konfigurieren der OAuth-IdP-Authentifizierung von Drittanbietern

> [!Note]
> Damit die Authentifizierung für Ihre Registerkarte auf mobilen Clients funktioniert, stellen Sie sicher, dass Sie Version 1.4.1 oder höher des Teams JavaScript SDK verwenden.

Es gibt viele Dienste, die Sie möglicherweise in Ihrer Teams-App nutzen möchten, und die meisten dieser Dienste erfordern Authentifizierung und Autorisierung, um Zugriff auf den Dienst zu erhalten. Zu den Diensten gehören Facebook, Twitter und Teams.
Teams-Benutzerprofilinformationen werden in Azure AD mitHilfe von Microsoft Graph gespeichert, und dieser Artikel konzentriert sich auf die Authentifizierung mitHilfe von Azure AD, um Zugriff auf diese Informationen zu erhalten.

OAuth 2.0 ist ein offener Standard für die Authentifizierung, der von Azure AD und vielen anderen Dienstanbietern verwendet wird. Das Verständnis von OAuth 2.0 ist eine Voraussetzung für die Arbeit mit der Authentifizierung in Teams und Azure AD. In den folgenden Beispielen wird der Fluss für implizite OAuth 2.0-Genehmigungen verwendet. Er liest die Profilinformationen des Benutzers aus Azure AD und Microsoft Graph.

Der Code in diesem Artikel stammt aus dem [Microsoft Teams-Authentifizierungsbeispiel (Knoten) der Microsoft](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-auth/nodejs) Teams-Beispiel-App. Sie enthält eine statische Registerkarte, die ein Zugriffstoken für Microsoft Graph anfordert, und zeigt die grundlegenden Profilinformationen des aktuellen Benutzers aus Azure AD an.

Eine Übersicht über den Authentifizierungsfluss für Registerkarten finden Sie [unter Authentifizierungsfluss auf Registerkarten](~/tabs/how-to/authentication/auth-flow-tab.md).

Der Authentifizierungsfluss auf Registerkarten unterscheidet sich vom Authentifizierungsfluss in Bots.

[!INCLUDE [sdk-include](~/includes/sdk-include.md)]

## <a name="configure-your-app-to-use-azure-ad-as-an-identity-provider"></a>Konfigurieren Ihrer App für die Verwendung von Azure AD als Identitätsanbieter

Identitätsanbieter, die OAuth 2.0 unterstützen, authentifizieren keine Anforderungen von unbekannten Anwendungen. Sie müssen die Anwendungen vorab registrieren. Führen Sie die folgenden Schritte aus, um dies mit Azure AD zu tun:

1. Öffnen Sie das [Anwendungsregistrierungsportal](https://ms.portal.azure.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade).

2. Wählen Sie Ihre App aus, um deren Eigenschaften anzuzeigen, oder wählen Sie die Schaltfläche "Neue Registrierung" aus. Suchen Sie den **Abschnitt "Umleitungs-URI** " für die App.

3. Wählen Sie im Dropdownmenü " **Web** " aus. Aktualisieren Sie die URL zu Ihrem Authentifizierungsendpunkt. Für die TypeScript/Node.js- und C#-Beispiel-Apps auf GitHub ähneln die Umleitungs-URLs den folgenden:

    Umleitungs-URLs: `https://<hostname>/bot-auth/simple-start`

Ersetzen Sie `<hostname>` sie durch Ihren eigentlichen Host. Dieser Host kann eine dedizierte Hostingwebsite wie Azure, Glitch oder ein ngrok-Tunnel zu localhost auf Ihrem Entwicklungscomputer sein, z `abcd1234.ngrok.io`. B. . Wenn Sie nicht über diese Informationen verfügen, stellen Sie sicher, dass Sie Ihre App (oder die Beispiel-App) abgeschlossen oder gehostet haben. Setzen Sie diesen Vorgang fort, wenn Sie über diese Informationen verfügen.

> [!NOTE]
> Sie können einen beliebigen Drittanbieter für OAuth auswählen, z. B. LinkedIn, Google und andere. Das Verfahren zum Aktivieren der Authentifizierung für diese Anbieter ähnelt der Verwendung von Azure AD als OAuth-Anbieter eines Drittanbieters. Weitere Informationen zur Nutzung von OAuth-Drittanbietern finden Sie auf der Website des jeweiligen Anbieters.

## <a name="initiate-authentication-flow"></a>Initiieren des Authentifizierungsflusses

Der Authentifizierungsfluss sollte durch eine Benutzeraktion ausgelöst werden. Sie sollten das Authentifizierungspopup nicht automatisch öffnen, da dies wahrscheinlich den Popupblocker des Browsers auslöst und den Benutzer verwirren wird.

Fügen Sie Ihrer Konfigurations- oder Inhaltsseite eine Schaltfläche hinzu, damit sich der Benutzer bei Bedarf anmelden kann. Dies kann auf der [Registerkartenkonfigurationsseite](~/tabs/how-to/create-tab-pages/configuration-page.md) oder auf einer beliebigen [Inhaltsseite](~/tabs/how-to/create-tab-pages/content-page.md) erfolgen.

Wie die meisten Identitätsanbieter lässt Azure AD nicht zu, dass seine Inhalte in einem `iframe`platziert werden. Dies bedeutet, dass Sie eine Popupseite hinzufügen müssen, um den Identitätsanbieter zu hosten. Im folgenden Beispiel ist `/tab-auth/simple-start`diese Seite . Verwenden Sie die `authentication.authenticate()` Funktion des Microsoft Teams-Client-SDK, um diese Seite zu starten, wenn die Schaltfläche ausgewählt ist.

# <a name="teamsjs-v2"></a>[TeamsJS v2](#tab/teamsjs-v2)

```javascript
import { authentication } from "@microsoft/teams-js";
authentication.authenticate({
    url: window.location.origin + "/tab/simple-start-v2",
    width: 600,
    height: 535})
.then((result) => {
    console.log("Login succeeded: " + result);
    let data = localStorage.getItem(result);
    localStorage.removeItem(result);
    let tokenResult = JSON.parse(data);
    showIdTokenAndClaims(tokenResult.idToken);
    getUserProfile(tokenResult.accessToken);
})
.catch((reason) => {
    console.log("Login failed: " + reason);
    handleAuthError(reason);
});
```

# <a name="teamsjs-v1"></a>[TeamsJS v1](#tab/teamsjs-v1)

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
---

### <a name="notes"></a>Anmerkungen

* Die URL, die Sie übergeben, `authenticate()` ist die Startseite des Authentifizierungsflusses. In diesem Beispiel ist dies `/tab-auth/simple-start`. Dies sollte mit dem übereinstimmen, was Sie im [Azure AD-Anwendungsregistrierungsportal](https://apps.dev.microsoft.com) registriert haben.

* Der Authentifizierungsfluss muss auf einer Seite beginnen, die sich in Ihrer Domäne befindet. Diese Domäne sollte auch im [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) Abschnitt des Manifests aufgeführt werden. Andernfalls wird ein leeres Popup angezeigt.

* Wenn sie nicht verwendet `authenticate()` wird, tritt ein Problem auf, da das Popup am Ende des Anmeldevorgangs nicht geschlossen wird.

## <a name="navigate-to-the-authorization-page-from-your-pop-up-page"></a>Navigieren Sie von ihrer Popupseite zur Autorisierungsseite.

Wenn Ihre Popupseite (`/tab-auth/simple-start`) angezeigt wird, wird der folgende Code ausgeführt. Das Hauptziel der Seite besteht darin, zu Ihrem Identitätsanbieter umzuleiten, damit sich der Benutzer anmelden kann. Diese Umleitung kann serverseitig mitHILFE von HTTP 302 erfolgen, in diesem Fall erfolgt dies jedoch auf clientseitiger Seite mithilfe eines Aufrufs von `window.location.assign()`. Dies ermöglicht `app.getContext()` auch das Abrufen von Hinweisinformationen, die an Azure AD übergeben werden können.

# <a name="teamsjs-v2"></a>[TeamsJS v2](#tab/teamsjs-v2)

```javascript
app.getContext().then((context) => {
    // Generate random state string and store it, so we can verify it in the callback
    let state = _guid(); // _guid() is a helper function in the sample
    localStorage.setItem("simple.state", state);
    localStorage.removeItem("simple.error");

    // Go to the Azure AD authorization endpoint
    let queryParams = {
        client_id: "{{appId}}",
        response_type: "id_token token",
        response_mode: "fragment",
        scope: "https://graph.microsoft.com/User.Read openid",
        redirect_uri: window.location.origin + "/tab/simple-end",
        nonce: _guid(),
        state: state,
        // The context object is populated by Teams; the loginHint attribute
        // is used as hinting information
        login_hint: context.user.loginHint,
    };

    let authorizeEndpoint = `https://login.microsoftonline.com/${context.user.tenant.id}/oauth2/v2.0/authorize?${toQueryString(queryParams)}`;
    window.location.assign(authorizeEndpoint);
});
```

# <a name="teamsjs-v1"></a>[TeamsJS v1](#tab/teamsjs-v1)

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

---

Nachdem der Benutzer die Autorisierung abgeschlossen hat, wird der Benutzer zu der Rückrufseite umgeleitet, die Sie für Ihre App unter `/tab-auth/simple-end`angegeben haben.

### <a name="notes"></a>Anmerkungen

* Informationen zum [Abrufen von Benutzerkontextinformationen](~/tabs/how-to/access-teams-context.md) finden Sie unter Hilfe beim Erstellen von Authentifizierungsanforderungen und URLs. Beispielsweise können Sie den Anmeldenamen des Benutzers als Wert für die `login_hint` Azure AD-Anmeldung verwenden, was bedeutet, dass der Benutzer möglicherweise weniger eingeben muss. Denken Sie daran, dass Sie diesen Kontext nicht direkt als Identitätsnachweis verwenden sollten, da ein Angreifer Ihre Seite in einen böswilligen Browser laden und ihr alle gewünschten Informationen bereitstellen kann.
* Obwohl der Registerkartenkontext nützliche Informationen zum Benutzer bereitstellt, verwenden Sie diese Informationen nicht, um den Benutzer zu authentifizieren, unabhängig davon, ob Sie ihn als URL-Parameter zu Ihrer Registerkarteninhalts-URL oder durch Aufrufen der `app.getContext()` Funktion im Microsoft Teams-Client-SDK erhalten. Ein böswilliger Akteur könnte Ihre Registerkarteninhalts-URL mit eigenen Parametern aufrufen, und eine Webseite, die die Identität von Microsoft Teams angibt, könnte Ihre Registerkarteninhalts-URL in einem iframe laden und ihre eigenen Daten an die `getContext()` Funktion zurückgeben. Sie sollten die identitätsbezogenen Informationen im Registerkartenkontext einfach als Hinweise behandeln und vor der Verwendung überprüfen.
* Der `state` Parameter wird verwendet, um zu bestätigen, dass der Dienst, der den Rückruf-URI aufruft, der Dienst ist, den Sie aufgerufen haben. Wenn der `state` Parameter im Rückruf nicht mit dem Parameter übereinstimmt, den Sie während des Aufrufs gesendet haben, wird der Rückgabeaufruf nicht überprüft und sollte beendet werden.
* Es ist nicht erforderlich, die Domäne des Identitätsanbieters in die Liste in der `validDomains` Datei "manifest.json" der App aufzunehmen.

## <a name="the-callback-page"></a>Die Rückrufseite

Im letzten Abschnitt haben Sie den Azure AD-Autorisierungsdienst aufgerufen und Benutzer- und App-Informationen übergeben, damit Azure AD dem Benutzer eine eigene monolithische Autorisierungserfahrung bieten kann. Ihre App hat keine Kontrolle darüber, was in dieser Umgebung geschieht. Sie wissen nur, was zurückgegeben wird, wenn Azure AD die von Ihnen bereitgestellte Rückrufseite aufruft (`/tab-auth/simple-end`).

Auf dieser Seite müssen Sie Erfolg oder Fehler basierend auf den von Azure AD zurückgegebenen Informationen und dem Anruf `authentication.notifySuccess()` oder `authentication.notifyFailure()`ermitteln. Wenn die Anmeldung erfolgreich war, haben Sie Zugriff auf Dienstressourcen.

```javascript
// Split the key-value pairs passed from Azure AD
// getHashParameters is a helper function that parses the arguments sent
// to the callback URL by Azure AD after the authorization call
let hashParams = getHashParameters();
if (hashParams["error"]) {
    // Authentication/authorization failed
    localStorage.setItem("simple.error", JSON.stringify(hashParams));
} else if (hashParams["access_token"]) {
    // Get the stored state parameter and compare with incoming state
    let expectedState = localStorage.getItem("simple.state");
    if (expectedState !== hashParams["state"]) {
        // State does not match, report error
        localStorage.setItem("simple.error", JSON.stringify(hashParams));
        authentication.notifyFailure("StateDoesNotMatch");
    } else {
        // Success -- return token information to the parent page.
        // Use localStorage to avoid passing the token via notifySuccess; instead we send the item key.
        let key = "simple.result";
        localStorage.setItem(key, JSON.stringify({
            idToken: hashParams["id_token"],
            accessToken: hashParams["access_token"],
            tokenType: hashParams["token_type"],
            expiresIn: hashParams["expires_in"]
        }));
        authentication.notifySuccess(key);
    }
} else {
    // Unexpected condition: hash does not contain error or access_token parameter
    localStorage.setItem("simple.error", JSON.stringify(hashParams));
    authentication.notifyFailure("UnexpectedFailure");
}
```

Dieser Code analysiert die von Azure AD empfangenen Schlüssel-Wert-Paare mithilfe `window.location.hash` der `getHashParameters()` Hilfsfunktion. Wenn ein Wert gefunden `access_token`wird und der `state` Wert mit dem wert übereinstimmt, der zu Beginn des Authentifizierungsflusses bereitgestellt wird, wird das Zugriffstoken für die Registerkarte durch Aufrufen `notifySuccess()`zurückgegeben. Andernfalls wird ein Fehler mit `notifyFailure()`gemeldet.

### <a name="notes"></a>Anmerkungen

`NotifyFailure()` hat die folgenden vordefinierten Fehlerursachen:

* `CancelledByUser` der Benutzer das Popupfenster geschlossen hat, bevor der Authentifizierungsfluss abgeschlossen wurde.
* `FailedToOpenWindow` das Popupfenster konnte nicht geöffnet werden. Wenn Sie Microsoft Teams in einem Browser ausführen, bedeutet dies in der Regel, dass das Fenster durch einen Popupblocker blockiert wurde.

Bei erfolgreicher Ausführung können Sie die Seite aktualisieren oder erneut laden und Inhalte anzeigen, die für den jetzt authentifizierten Benutzer relevant sind. Wenn die Authentifizierung fehlschlägt, wird eine Fehlermeldung angezeigt.

Ihre App kann ein eigenes Sitzungscookie festlegen, sodass sich der Benutzer nicht erneut anmelden muss, wenn er auf dem aktuellen Gerät zu Ihrer Registerkarte zurückkehrt.

> [!NOTE]
>
> * Chrome 80, das Anfang 2020 veröffentlicht werden soll, führt neue Cookiewerte ein und erzwingt standardmäßig Cookierichtlinien. Es wird empfohlen, die beabsichtigte Verwendung für Ihre Cookies festzulegen, anstatt sich auf das Standardverhalten des Browsers zu verlassen. *Siehe* [SameSite-Cookieattribut (Update 2020)](../../../resources/samesite-cookie-update.md).
> * Um das richtige Token für Microsoft Teams Free- und Gastbenutzer zu erhalten, ist es wichtig, dass die Apps den mandantenspezifischen Endpunkt `https://login.microsoftonline.com/**{tenantId}**`verwenden. Sie können tenantId aus der Botnachricht oder dem Registerkartenkontext abrufen. Wenn die Apps verwenden `https://login.microsoftonline.com/common`, erhalten die Benutzer falsche Token und melden sich beim "Home"-Mandanten anstelle des Mandanten an, bei dem sie derzeit angemeldet sind.

Weitere Informationen zu Single Sign-On (SSO) finden Sie im Artikel [Automatische Authentifizierung](~/tabs/how-to/authentication/auth-silent-AAD.md).

## <a name="code-sample"></a>Codebeispiel

Beispielcode, der den Registerkartenauthentifizierungsprozess mitHilfe von Azure AD zeigt:

| **Beispielname** | **description** | **.NET** | **Node.js** |
|-----------------|-----------------|-------------|
| Microsoft Teams-Registerkartenauthentifizierung | Registerkartenauthentifizierung mitHilfe von Azure AD. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-channel-group-config-page-auth/csharp) | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-auth/nodejs) |

## <a name="see-also"></a>Siehe auch

* [Planen der Benutzerauthentifizierung](../../../concepts/design/understand-use-cases.md)
* [Entwerfen Sie Ihre Registerkarte für Microsoft Teams](~/tabs/design/tabs.md)
* [Automatische Authentifizierung](~/tabs/how-to/authentication/auth-silent-aad.md)
* [Hinzufügen der Authentifizierung zu Ihrer Nachrichtenerweiterung](~/messaging-extensions/how-to/add-authentication.md)
* [Single-Sign-On (SSO)-Unterstützung für Bots](~/bots/how-to/authentication/auth-aad-sso-bots.md)
