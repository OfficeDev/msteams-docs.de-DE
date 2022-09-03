---
title: Automatische Authentifizierung
description: Konfigurieren Sie Ihre Registerkarten-App mit Azure AD für Registerkarten und deren Funktionsweise.
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: ef80c44e38e32666f68b13e42e1f815a4c351353
ms.sourcegitcommit: 82c585d287d61924ce3a3bba3e9caeff35c9a27a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2022
ms.locfileid: "67586777"
---
# <a name="use-silent-authentication-in-azure-ad"></a>Stille Authentifizierung in Azure AD verwenden

> [!IMPORTANT]
> Der Support und die Entwicklung von Microsoft für die Active Directory-Authentifizierungsbibliothek (ADAL) einschließlich der Sicherheitsfixes endet am **30. Juni 2022**. Um weiterhin Support zu erhalten, aktualisieren Sie Ihre Anwendungen so, dass microsoft Authentication Library (MSAL) verwendet wird. Siehe [Migrieren von Anwendungen zur Microsoft-Authentifizierungsbibliothek (MSAL).](/azure/active-directory/develop/msal-migration)

> [!NOTE]
> Damit die Authentifizierung für Ihre Registerkarte auf mobilen Clients funktioniert, stellen Sie sicher, dass Sie Teams JavaScript SDK Version 1.4.1 oder höher verwenden.

Die automatische Authentifizierung in Azure AD minimiert, wie oft ein Benutzer seine Anmeldeinformationen eingibt, indem das Authentifizierungstoken automatisch aktualisiert wird. Eine echte Unterstützung für einmaliges Anmelden finden Sie in der [SSO-Dokumentation](~/tabs/how-to/authentication/tab-sso-overview.md).

Verwenden Sie die [Azure AD-Authentifizierungsbibliothek](/azure/active-directory/develop/active-directory-authentication-libraries) für JavaScript, um ein Microsoft Azure Active Directory (Azure AD)-Zugriffstoken im Hintergrund abzurufen, um den Code clientseitig zu verwalten. Wenn sich der Benutzer kürzlich angemeldet hat, wird kein Popupdialogfeld angezeigt.

Die Active Directory-Authentifizierungsbibliothek ist zwar für AngularJS-Anwendungen optimiert, funktioniert aber auch mit JavaScript-Einzelseitenanwendungen (Single-Page Applications, SPA).

> [!NOTE]
> Derzeit funktioniert die automatische Authentifizierung nur für Registerkarten. Es funktioniert nicht, wenn Sie sich von einem Bot anmelden.

## <a name="how-silent-authentication-works"></a>Funktionsweise der automatischen Authentifizierung

Die Active Directory-Authentifizierungsbibliothek erstellt einen ausgeblendeten iFrame für den impliziten OAuth 2.0-Genehmigungsfluss. Die Bibliothek gibt jedoch an, sodass `prompt=none`Azure AD die Anmeldeseite nicht anzeigt. Eine Benutzerinteraktion kann erforderlich sein, wenn sich der Benutzer anmelden oder Zugriff auf die Anwendung gewähren muss. Wenn Eine Benutzerinteraktion erforderlich ist, gibt Azure AD einen Fehler zurück, den die Bibliothek an Ihre App meldet. Bei Bedarf kann ihre App jetzt eine Anmeldeoption anzeigen.

## <a name="how-to-do-silent-authentication"></a>Durchführen der automatischen Authentifizierung

Der Code in diesem Artikel stammt aus der Teams-Beispiel-App, bei der es sich um einen [Beispielknoten für die Teams-Authentifizierung](https://github.com/OfficeDev/Microsoft-Teams-Samples/blob/main/samples/app-auth/nodejs/src/views/tab/silent/silent.hbs) handelt.

[Initiieren Sie die konfigurierbare Registerkarte "Automatische und einfache Authentifizierung" mitHilfe von Azure AD](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-channel-group-config-page-auth/csharp) , und folgen Sie den Anweisungen, um das Beispiel auf Ihrem lokalen Computer auszuführen.

### <a name="include-and-configure-active-directory-authentication-library"></a>Einschließen und Konfigurieren der Active Directory-Authentifizierungsbibliothek

Schließen Sie die Active Directory-Authentifizierungsbibliothek in Ihre Registerkartenseiten ein, und konfigurieren Sie die Bibliothek mit Ihrer Client-ID und Umleitungs-URL:

```html
<script src="https://secure.aadcdn.microsoftonline-p.com/lib/1.0.15/js/adal.min.js" integrity="sha384-lIk8T3uMxKqXQVVfFbiw0K/Nq+kt1P3NtGt/pNexiDby2rKU6xnDY8p16gIwKqgI" crossorigin="anonymous"></script>
<script type="text/javascript">
    // Active Directory Authentication Library configuration
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

Rufen `app.getContext()` Sie auf der Inhaltsseite der Registerkarte einen Anmeldehinweis für den aktuellen Benutzer ab. Der Hinweis wird als ein `loginHint` Aufruf von Azure AD verwendet.

```javascript
// Set up extra query parameters for Active Directory Authentication Library
// - openid and profile scope adds profile information to the id_token
// - login_hint provides the expected user name
if (loginHint) {
    config.extraQueryParameter = "scope=openid+profile&login_hint=" + encodeURIComponent(loginHint);
} else {
    config.extraQueryParameter = "scope=openid+profile";
}
```

### <a name="authenticate"></a>Authentifizieren

Wenn in der Active Directory-Authentifizierungsbibliothek ein nicht abgelaufenes Token für den Benutzer zwischengespeichert ist, verwenden Sie das Token. Alternativ können Sie aufrufen `acquireToken(resource, callback)` , um im Hintergrund ein Token zu erhalten. Die Bibliothek ruft eine Rückruffunktion mit dem angeforderten Token auf oder generiert einen Fehler, wenn die Authentifizierung fehlschlägt.

Wenn sie einen Fehler in der Rückruffunktion erhalten, zeigen Sie eine explizite Anmeldeoption an, und verwenden Sie sie.

```javascript
let authContext = new AuthenticationContext(config); // from Active Directory Authentication Library
// See if there is a cached user and it matches the expected user
let user = authContext.getCachedUser();
if (user) {
    if (user.profile.oid !== userObjectId) {
        // User doesn't match, clear the cache
        authContext.clearCache();
    }
}

// In this example we are getting an id token (which Active Directory Authentication Library returns if we ask for resource = clientId)
authContext.acquireToken(config.clientId, function (errDesc, token, err, tokenType) {
    if (token) {
        // Make sure Active Directory Authentication Library gave us an ID token
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

Die Active Directory-Authentifizierungsbibliothek analysiert das Ergebnis von Azure AD, indem die Anmelderückrufseite aufgerufen `AuthenticationContext.handleWindowCallback(hash)` wird.

Überprüfen Sie, ob Sie über einen gültigen Benutzer verfügen, und rufen `authentication.notifySuccess()` Sie den Status auf der Hauptinhaltsseite der Registerkarte an oder `authentication.notifyFailure()` melden Sie ihn.

```javascript
import { authentication } from "@microsoft/teams-js";
if (authContext.isCallback(window.location.hash)) {
    authContext.handleWindowCallback(window.location.hash);
    if (window.parent === window) {
        if (authContext.getCachedUser()) {
            authentication.notifySuccess();
        } else {
            authentication.notifyFailure(authContext.getLoginError());
        }
    }
}
```

### <a name="handle-the-sign-out-flow"></a>Behandeln des Abmeldungsflusses

Verwenden Sie den folgenden Code, um den Abmeldungsfluss in der Azure AD-Authentifizierung zu behandeln:

> [!NOTE]
> Wenn Sie sich von der Registerkarte oder dem Bot von Teams abmelden, wird die aktuelle Sitzung gelöscht.

```javascript
function logout() {
localStorage.clear();
window.location.href = "@Url.Action("<<Action Name>>", "<<Controller Name>>")";
}
```

## <a name="see-also"></a>Siehe auch

* [Konfigurieren von Identitätsanbietern für die Verwendung von Azure AD](../../../concepts/authentication/configure-identity-provider.md)
* [Informationen zur Microsoft-Authentifizierungsbibliothek (MSAL)](/azure/active-directory/develop/msal-overview)
