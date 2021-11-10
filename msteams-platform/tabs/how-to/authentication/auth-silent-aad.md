---
title: Automatische Authentifizierung
description: Beschreibt die automatische Authentifizierung, einmaliges Anmelden Azure Active Directory für Registerkarten
ms.topic: conceptual
ms.localizationpriority: medium
keywords: Registerkarte "Teams-Authentifizierungs-SSO im hintergrund AAD"
ms.openlocfilehash: 2b3981ce43f09cc05bb2cb3837a90c0a92ef6deb
ms.sourcegitcommit: af1d0a4041ce215e7863ac12c71b6f1fa3e3ba81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2021
ms.locfileid: "60888027"
---
# <a name="silent-authentication"></a>Automatische Authentifizierung

> [!NOTE]
> Damit die Authentifizierung für Ihre Registerkarte auf mobilen Clients funktioniert, stellen Sie sicher, dass Sie mindestens version 1.4.1 des Teams JavaScript SDK verwenden.

Die automatische Authentifizierung in Azure Active Directory (AAD) minimiert, wie oft ein Benutzer seine Anmeldeinformationen eingibt, indem das Authentifizierungstoken im Hintergrund aktualisiert wird. Eine echte Unterstützung für einmaliges Anmelden finden Sie in der [SSO-Dokumentation.](~/tabs/how-to/authentication/auth-aad-sso.md)

Wenn Sie Ihren Code vollständig clientseitig beibehalten möchten, können Sie die [AAD-Authentifizierungsbibliothek](/azure/active-directory/develop/active-directory-authentication-libraries) für JavaScript verwenden, um ein AAD Zugriffstoken im Hintergrund abzurufen. Wenn sich der Benutzer kürzlich angemeldet hat, wird nie ein Popup-Dialogfeld angezeigt.

Obwohl die ADAL.js-Bibliothek für AngularJS-Anwendungen optimiert ist, funktioniert sie auch mit reinen JavaScript-Einzelseitenanwendungen.

> [!NOTE]
> Derzeit funktioniert die automatische Authentifizierung nur für Registerkarten. Es funktioniert nicht, wenn Sie sich von einem Bot anmelden.

## <a name="how-silent-authentication-works"></a>Funktionsweise der automatischen Authentifizierung

Die ADAL.js Bibliothek erstellt einen ausgeblendeten iframe für den impliziten OAuth 2.0-Genehmigungsfluss. Die Bibliothek gibt jedoch `prompt=none` an, dass Azure AD niemals die Anmeldeseite anzeigt. Wenn eine Benutzerinteraktion erforderlich ist, da sich der Benutzer anmelden oder Zugriff auf die Anwendung gewähren muss, gibt AAD sofort einen Fehler zurück, der ADAL.js An Ihre App meldet. An diesem Punkt kann Ihre App bei Bedarf eine Anmeldeschaltfläche anzeigen.

## <a name="how-to-do-silent-authentication"></a>So führen Sie die automatische Authentifizierung durch

Der Code in diesem Artikel stammt aus der Teams Beispiel-App, die [Teams Authentifizierungs-Beispielknoten](https://github.com/OfficeDev/Microsoft-Teams-Samples/blob/main/samples/app-auth/nodejs/src/views/tab/silent/silent.hbs)ist.

[Initiieren Sie die konfigurierbare Registerkarte für die automatische und einfache Authentifizierung mit AAD,](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-channel-group-config-page-auth/csharp) und befolgen Sie die Anweisungen, um das Beispiel auf Ihrem lokalen Computer auszuführen.

### <a name="include-and-configure-adal"></a>Einschließen und Konfigurieren von ADAL

Fügen Sie die ADAL.js Bibliothek in Ihre Registerkartenseiten ein, und konfigurieren Sie ADAL mit Ihrer Client-ID und Umleitungs-URL:

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

Rufen Sie auf der Inhaltsseite der Registerkarte `microsoftTeams.getContext()` auf, um einen Anmeldehinweis für den aktuellen Benutzer abzurufen. Dies wird als loginHint im Aufruf von AAD verwendet.

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

Wenn ADAL ein Token zwischengespeichert hat, das für den Benutzer nicht abgelaufen ist, verwenden Sie dieses Token. Versuchen Sie alternativ, ein Token im Hintergrund abzurufen, indem Sie `acquireToken(resource, callback)` . ADAL.js ruft die Rückruffunktion mit dem angeforderten Token auf oder gibt einen Fehler aus, wenn die Authentifizierung fehlschlägt.

Wenn in der Rückruffunktion ein Fehler auftritt, zeigen Sie eine Anmeldeschaltfläche an und greifen auf eine explizite Anmeldung zurück.

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

ADAL.js analysiert das Ergebnis aus AAD, indem `AuthenticationContext.handleWindowCallback(hash)` die Rückrufseite für die Anmeldung aufgerufen wird.

Überprüfen Sie, ob Sie über einen gültigen Benutzer und Anruf verfügen, oder melden Sie `microsoftTeams.authentication.notifySuccess()` den Status ihrer `microsoftTeams.authentication.notifyFailure()` Hauptregisterkarten-Inhaltsseite.

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

### <a name="handle-sign-out-flow"></a>Behandeln des Abmeldungsflusses

Verwenden Sie den folgenden Code, um den Abmeldungsfluss in AAD Authentifizierung zu behandeln:

> [!NOTE]
> Wenn Sie sich von Teams Registerkarte oder bot abmelden, wird die aktuelle Sitzung gelöscht.

```javascript
function logout() {
localStorage.clear();
window.location.href = "@Url.Action("<<Action Name>>", "<<Controller Name>>")";
}
```
## <a name="see-also"></a>Siehe auch

[Konfigurieren von Identitätsanbietern für die Verwendung von AAD](~/concepts/authentication/configure-identity-provider.md)
