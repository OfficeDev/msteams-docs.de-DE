---
title: Automatische Authentifizierung
description: Beschreibt die automatische Authentifizierung
ms.topic: conceptual
keywords: teams authentication SSO silent AAD
ms.openlocfilehash: db8409cd4a6edface6d5dc3b3de6698852eaaa24
ms.sourcegitcommit: 5cb3453e918bec1173899e7591b48a48113cf8f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2021
ms.locfileid: "50449228"
---
# <a name="silent-authentication"></a>Automatische Authentifizierung

> [!NOTE]
> Damit die Authentifizierung für Ihre Registerkarte auf mobilen Clients funktioniert, stellen Sie sicher, dass Sie mindestens die Version 1.4.1 des Teams JavaScript SDK verwenden.

Die automatische Authentifizierung in Azure Active Directory (AAD) minimiert die Anzahl der Anmeldeinformationen, mit der ein Benutzer seine Anmeldeinformationen einzahlt, indem das Authentifizierungstoken automatisch aktualisiert wird. Eine echte Unterstützung für einmaliges Anmelden finden Sie in [der SSO-Dokumentation](~/tabs/how-to/authentication/auth-aad-sso.md).

Wenn Sie Ihren Code vollständig clientseitig halten möchten, können Sie die AAD-Authentifizierungsbibliothek für JavaScript verwenden, um im Hintergrund ein AAD-Zugriffstoken abzurufen. [](/azure/active-directory/develop/active-directory-authentication-libraries) Wenn sich der Benutzer kürzlich angemeldet hat, wird nie ein Popupdialogfeld angezeigt.

Auch wenn die ADAL.js für AngularJS-Anwendungen optimiert ist, funktioniert sie auch mit reinen JavaScript-Einseitenanwendungen.

> [!NOTE]
> Derzeit funktioniert die automatische Authentifizierung nur für Registerkarten. Es funktioniert nicht, wenn Sie sich über einen Bot anmelden.

## <a name="how-silent-authentication-works"></a>Funktionsweise der automatischen Authentifizierung

Die ADAL.js erstellt einen ausgeblendeten iframe für den impliziten OAuth 2.0-Erteilungsfluss. Die Bibliothek gibt jedoch `prompt=none` an, sodass Azure AD die Anmeldeseite niemals zeigt. Wenn benutzerinteraktion erforderlich ist, da sich der Benutzer anmelden oder Zugriff auf die Anwendung gewähren muss, gibt AAD sofort einen Fehler zurück, der ADAL.js App meldet. An diesem Punkt kann Ihre App bei Bedarf eine Anmeldeschaltfläche anzeigen.

## <a name="how-to-do-silent-authentication"></a>So gehen Sie zur automatischen Authentifizierung

Der Code in diesem Artikel stammt aus der Teams-Beispiel-App, bei der es sich um [den Beispielknoten für die Teams-Authentifizierung handelt.](https://github.com/OfficeDev/Microsoft-Teams-Samples/blob/main/samples/app-auth/nodejs/src/views/tab/silent/silent.hbs)

### <a name="include-and-configure-adal"></a>Include and configure ADAL

Fügen Sie die ADAL.js in Ihre Registerkartenseiten ein, und konfigurieren Sie ADAL mit Ihrer Client-ID und Umleitungs-URL:

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

Rufen Sie auf der Inhaltsseite der Registerkarte auf, um einen Anmeldehinweis für den `microsoftTeams.getContext()` aktuellen Benutzer zu erhalten. Dies wird als loginHint im Aufruf von AAD verwendet.

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

Wenn ADAL ein nicht gefundenes Token für den Benutzer zwischengespeichert hat, verwenden Sie das Token. Versuchen Sie alternativ, ein Token im Hintergrund abzurufen, indem Sie `acquireToken(resource, callback)` aufrufen. ADAL.js aufruft die Rückruffunktion mit dem angeforderten Token oder gibt einen Fehler aus, wenn die Authentifizierung fehlschlägt.

Wenn sie einen Fehler in der Rückruffunktion erhalten, zeigen Sie eine Anmeldeschaltfläche an, und stürzen Sie auf eine explizite Anmeldung zurück.

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

ADAL.js analysiert das Ergebnis von AAD durch Aufrufen `AuthenticationContext.handleWindowCallback(hash)` der Rückrufseite für die Anmeldung.

Überprüfen Sie, ob Sie über einen gültigen Benutzer verfügen, und rufen Sie auf, oder melden Sie den Status ihrer `microsoftTeams.authentication.notifySuccess()` `microsoftTeams.authentication.notifyFailure()` Inhaltsseite für die Hauptregisterkarte.

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
