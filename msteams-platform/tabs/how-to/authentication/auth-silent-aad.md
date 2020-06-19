---
title: Automatische Authentifizierung
description: Beschreibung der automatischen Authentifizierung
keywords: Microsoft Teams Authentication SSO Silent Aad
ms.openlocfilehash: b8a5b8cb9328635f5730ca089da29140d0a17ac4
ms.sourcegitcommit: fdcd91b270d4c2e98ab2b2c1029c76c49bb807fa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "44801219"
---
# <a name="silent-authentication"></a>Automatische Authentifizierung

> [!NOTE]
> Damit die Authentifizierung für Ihre Registerkarte auf mobilen Clients funktioniert, müssen Sie sicherstellen, dass Sie mindestens die Version 1.4.1 von Microsoft Teams JavaScript SDK verwenden.

Bei der automatischen Authentifizierung in Azure Active Directory (Azure AD) wird minimiert, wie oft ein Benutzer seine Anmeldeinformationen eingeben muss, indem er das Authentifizierungstoken automatisch aktualisiert. (Für eine echte Unterstützung für einmaliges Anmelden sehen Sie sich unsere [SSO-Dokumentation](~/tabs/how-to/authentication/auth-aad-sso.md)an)

Wenn Sie den Code vollständig clientseitig beibehalten möchten, können Sie die [Azure Active Directory-Authentifizierungsbibliothek](/azure/active-directory/develop/active-directory-authentication-libraries) für JavaScript verwenden, um zu versuchen, ein Azure AD Zugriffstoken im Hintergrund abzurufen. Dies bedeutet, dass dem Benutzer möglicherweise kein Popupdialogfeld angezeigt wird, wenn er sich kürzlich angemeldet hat.

Auch wenn die ADAL.js Bibliothek für AngularJS-Anwendungen optimiert ist, funktioniert Sie auch mit reinen JavaScript-Einzelseiten-Anwendungen.

> [!NOTE]
> Derzeit funktioniert die unbeaufsichtigte Authentifizierung nur für Registerkarten. Sie funktioniert noch nicht, wenn Sie sich von einem bot aus anmelden.

## <a name="how-silent-authentication-works"></a>Funktionsweise der automatischen Authentifizierung

Die ADAL.js Bibliothek erstellt einen ausgeblendeten IFRAME für den impliziten Grant Flow von OAuth 2,0, gibt jedoch an `prompt=none` , dass Azure Ad die Anmeldeseite nie anzeigt. Wenn Benutzerinteraktionen erforderlich sind, da der Benutzer sich anmelden oder Zugriff auf die Anwendung gewähren muss, gibt Azure AD umgehend einen Fehler zurück, der ADAL.js dann an Ihre APP meldet. An dieser Position kann Ihre APP bei Bedarf eine Anmeldeschaltfläche anzeigen.

## <a name="how-to-do-silent-authentication"></a>Vorgehensweise zur automatischen Authentifizierung

Der Code in diesem Artikel stammt aus der Beispiel-APP [Microsoft Teams-Authentifizierungs Beispiel (Knoten)](https://github.com/OfficeDev/microsoft-teams-sample-complete-node)von Teams.

### <a name="include-and-configure-adal"></a>einschließen und Konfigurieren von Adal

Schließen Sie die ADAL.js Bibliothek in Ihre Registerkartenseiten ein, und konfigurieren Sie Adal mit Ihrer Client-ID und der Umleitungs-URL:

```html
<script src="https://secure.aadcdn.microsoftonline-p.com/lib/1.0.15/js/adal.min.js" integrity="sha384-lIk8T3uMxKqXQVVfFbiw0K/Nq+kt1P3NtGt/pNexiDby2rKU6xnDY8p16gIwKqgI" crossorigin="anonymous"></script>
<script type="text/javascript">
    // ADAL.js configuration
    let config = {
        clientId: "YOUR_APP_ID_HERE",
        // redirectUri must be in the list of redirect URLs for the Azure AD app
        redirectUri: window.location.origin + "/tab-auth/silent-end",
        cacheLocation: "localStorage",
        navigateToLoginRequestUrl: false,
    };
</script>
```

### <a name="get-the-user-context"></a>Abrufen des Benutzerkontexts

Rufen Sie auf der Registerkarte Inhaltsseite `microsoftTeams.getContext()` einen Anmelde Hinweis für den aktuellen Benutzer ab. Dies wird als login_hint im Aufruf von Azure AD verwendet.

```javascript
// Set up extra query parameters for ADAL
// - openid and profile scope adds profile information to the id_token
// - login_hint provides the expected user name
if (loginHint) {
    config.extraQueryParameter = "scope=openid+profile&login_hint=" + encodeURIComponent(loginHint);
} else {
    config.extraQueryParameter = "scope=openid+profile";
}
```

### <a name="authenticate"></a>Authentifizieren

Wenn Adal ein nicht abgelaufenes Token für den Benutzer zwischengespeichert hat, verwenden Sie diese. Andernfalls wird versucht, ein Token im Hintergrund abzurufen, indem es aufgerufen wird `acquireToken(resource, callback)` . ADAL.js rufen ihre Rückruffunktion mit dem angeforderten Token auf, oder es tritt ein Fehler auf, wenn die Authentifizierung fehlschlägt.

Wenn Sie in der Rückruffunktion einen Fehler erhalten, zeigen Sie eine Anmeldeschaltfläche an, und greifen Sie auf eine explizite Anmeldung zurück.

```javascript
let authContext = new AuthenticationContext(config); // from the ADAL.js library
// See if there's a cached user and it matches the expected user
let user = authContext.getCachedUser();
if (user) {
    if (user.profile.oid !== userObjectId) {
        // User doesn't match, clear the cache
        authContext.clearCache();
    }
}

// In this example we are getting an id token (which ADAL.js returns if we ask for resource = clientId)
authContext.acquireToken(config.clientId, function (errDesc, token, err, tokenType) {
    if (token) {
        // Make sure ADAL gave us an id token
        if (tokenType !== authContext.CONSTANTS.ID_TOKEN) {
            token = authContext.getCachedToken(config.clientId);
        }
        showProfileInformation(idToken);
    } else {
        console.log("Renewal failed: " + err);
        // Failed to get the token silently; show the login button
        showLoginButton();
        // You could attempt to launch the login popup here, but in browsers this could be blocked by
        // a popup blocker, in which case the login attempt will fail with the reason FailedToOpenWindow.
    }
});
```

### <a name="process-the-return-value"></a>Verarbeiten des Rückgabewerts

Lassen Sie ADAL.js das Ergebnis aus Azure AD analysieren, indem Sie `AuthenticationContext.handleWindowCallback(hash)` die Anmelde Rückruf Seite aufrufen.

Stellen Sie sicher, dass wir über einen gültigen Benutzer verfügen und den `microsoftTeams.authentication.notifySuccess()` `microsoftTeams.authentication.notifyFailure()` Status zurück zur Inhaltsseite des Hauptregisterkarten Berichts aufrufen.

```javascript
if (authContext.isCallback(window.location.hash)) {
    authContext.handleWindowCallback(window.location.hash);
    if (window.parent === window) {
        if (authContext.getCachedUser()) {
            microsoftTeams.authentication.notifySuccess();
        } else {
            microsoftTeams.authentication.notifyFailure(authContext.getLoginError());
        }
    }
}
```
