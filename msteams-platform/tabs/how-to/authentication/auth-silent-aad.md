---
title: Automatische Authentifizierung
description: Beschreibt die automatische Authentifizierung
ms.topic: conceptual
keywords: Teams authentication SSO silent AAD
ms.openlocfilehash: e55e415aba08fdedf4409abf39115838c3a5faf0
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014096"
---
# <a name="silent-authentication"></a>Automatische Authentifizierung

> [!NOTE]
> Damit die Authentifizierung für Ihre Registerkarte auf mobilen Clients funktioniert, müssen Sie sicherstellen, dass Sie mindestens die Version 1.4.1 des JavaScript SDK für Teams verwenden.

Bei der automatischen Authentifizierung in Azure Active Directory (Azure AD) wird die Anzahl der Benutzer zum Eingeben ihrer Anmeldeinformationen minimiert, indem das Authentifizierungstoken automatisch aktualisiert wird. (For true single sign-on support, view our [SSO Documentation](~/tabs/how-to/authentication/auth-aad-sso.md))

Wenn Sie Ihren Code vollständig clientseitig halten möchten, können Sie die [Azure Active Directory-Authentifizierungsbibliothek](/azure/active-directory/develop/active-directory-authentication-libraries) für JavaScript verwenden, um im Hintergrund zu versuchen, ein Azure AD-Zugriffstoken zu erwerben. Dies bedeutet, dass dem Benutzer möglicherweise kein Popupdialogfeld angezeigt wird, wenn er sich kürzlich angemeldet hat.

Auch wenn die ADAL.js für AngularJS-Anwendungen optimiert ist, funktioniert sie auch mit reinen JavaScript-Einzelseitenanwendungen.

> [!NOTE]
> Derzeit funktioniert die automatische Authentifizierung nur für Registerkarten. Es funktioniert noch nicht, wenn Sie sich von einem Bot anmelden.

## <a name="how-silent-authentication-works"></a>Funktionsweise der automatischen Authentifizierung

Die ADAL.js erstellt einen ausgeblendeten iframe für den impliziten OAuth 2.0-Genehmigungsfluss, gibt jedoch an, dass Azure AD die Anmeldeseite `prompt=none` niemals zeigt. Wenn eine Benutzerinteraktion erforderlich ist, weil sich der Benutzer anmelden oder Zugriff auf die Anwendung gewähren muss, gibt Azure AD sofort einen Fehler zurück, der ADAL.js dann an Ihre App meldet. An diesem Punkt kann Ihre App bei Bedarf eine Anmeldeschaltfläche anzeigen.

## <a name="how-to-do-silent-authentication"></a>So wird's bei der automatischen Authentifizierung

Der Code in diesem Artikel stammt aus der Microsoft Teams-Beispiel-App ["Microsoft Teams Authentication Sample (Node) ".](https://github.com/OfficeDev/microsoft-teams-sample-complete-node)

### <a name="include-and-configure-adal"></a>Include and configure ADAL

Schließen Sie ADAL.js Bibliothek in Ihre Registerkartenseiten ein, und konfigurieren Sie ADAL mit Ihrer Client-ID und Umleitungs-URL:

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

### <a name="get-the-user-context"></a>Benutzerkontext erhalten

Rufen Sie auf der Inhaltsseite der Registerkarte einen Anmeldehinweis `microsoftTeams.getContext()` für den aktuellen Benutzer ab. Dies wird als Login_hint beim Aufruf von Azure AD verwendet.

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

Wenn ADAL für den Benutzer ein nicht gelöschtes Token zwischengespeichert hat, verwenden Sie dies. Versuchen Sie andernfalls, ein Token im Hintergrund durch Aufrufen `acquireToken(resource, callback)` abzurufen. ADAL.js die Rückruffunktion mit dem angeforderten Token oder einen Fehler, wenn die Authentifizierung fehlschlägt.

Wenn in der Rückruffunktion ein Fehler angezeigt wird, zeigen Sie eine Anmeldeschaltfläche an, und stürzen Sie auf eine explizite Anmeldung zurück.

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

Lassen ADAL.js sich um die Analyse des Ergebnisses aus Azure AD kümmern, indem Sie `AuthenticationContext.handleWindowCallback(hash)` die Anmelderückrufseite aufrufen.

Überprüfen Sie, ob wir über einen gültigen Benutzer verfügen, und rufen Sie auf oder melden Sie den Status an die Inhaltsseite Ihrer `microsoftTeams.authentication.notifySuccess()` `microsoftTeams.authentication.notifyFailure()` Hauptregisterkarte zurück.

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
