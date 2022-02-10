---
title: Automatische Authentifizierung
description: Beschreibt die automatische Authentifizierung, single-sign-on, Microsoft Azure Active Directory (Azure AD) für Registerkarten
ms.topic: conceptual
ms.localizationpriority: medium
keywords: Registerkarte "Teams-Authentifizierungs-SSO– automatische Microsoft Azure Active Directory (Azure AD) "
ms.openlocfilehash: 700f0d3f752beb7b09b76a805f2bbcd7adf82fb9
ms.sourcegitcommit: 90587b1ec04bf20d716ed6feb8ccca4313e87f8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/10/2022
ms.locfileid: "62518464"
---
# <a name="silent-authentication"></a>Automatische Authentifizierung

> [!IMPORTANT]
> Der Support und die Entwicklung von Microsoft für die Active Directory-Authentifizierungsbibliothek (Active Directory Authentication Library, ADAL) einschließlich der Sicherheitsupdates endet am **30. Juni 2022**. Aktualisieren Sie Ihre Anwendungen so, dass sie Microsoft Authentication Library (MSAL) verwenden, um weiterhin Support zu erhalten. Weitere Informationen finden Sie unter [Migrieren von Anwendungen zur Microsoft-Authentifizierungsbibliothek (MSAL).](/azure/active-directory/develop/msal-migration)

> [!NOTE]
> Damit die Authentifizierung für Ihre Registerkarte auf mobilen Clients funktioniert, stellen Sie sicher, dass Sie Teams JavaScript SDK Version 1.4.1 oder höher verwenden.

Die automatische Authentifizierung in Microsoft Azure Active Directory (Azure AD) minimiert, wie oft ein Benutzer seine Anmeldeinformationen eingibt, indem das Authentifizierungstoken im Hintergrund aktualisiert wird. Eine echte Unterstützung für einmaliges Anmelden finden Sie in der [SSO-Dokumentation](~/tabs/how-to/authentication/auth-aad-sso.md).

Um Ihren Code clientseitig zu halten, verwenden Sie die [Microsoft Azure Active Directory (Azure AD)-Authentifizierungsbibliothek](/azure/active-directory/develop/active-directory-authentication-libraries) für JavaScript, um ein Microsoft Azure Active Directory (Azure AD) Zugriffstoken im Hintergrund abzurufen. Wenn sich der Benutzer kürzlich angemeldet hat, wird kein Popupdialogfeld angezeigt.

Die Active Directory-Authentifizierungsbibliothek ist zwar für AngularJS-Anwendungen optimiert, funktioniert aber auch mit JavaScript-Single-Page-Anwendungen (SPA).

> [!NOTE]
> Derzeit funktioniert die automatische Authentifizierung nur für Registerkarten. Es funktioniert nicht, wenn Sie sich von einem Bot anmelden.

## <a name="how-silent-authentication-works"></a>Funktionsweise der automatischen Authentifizierung

Die Active Directory-Authentifizierungsbibliothek erstellt einen ausgeblendeten iframe für den impliziten OAuth 2.0-Genehmigungsfluss. Die Bibliothek gibt jedoch an`prompt=none`, dass Microsoft Azure Active Directory (Azure AD) die Anmeldeseite nicht anzeigt. Benutzerinteraktionen sind möglicherweise erforderlich, wenn sich der Benutzer anmelden oder Zugriff auf die Anwendung gewähren muss. Wenn eine Benutzerinteraktion erforderlich ist, gibt Microsoft Azure Active Directory (Azure AD) einen Fehler zurück, den die Bibliothek an Ihre App meldet. Bei Bedarf kann Ihre App jetzt eine Anmeldeoption anzeigen.

## <a name="how-to-do-silent-authentication"></a>So führen Sie die automatische Authentifizierung durch

Der Code in diesem Artikel stammt aus der Teams Beispiel-App[, die Teams Authentifizierungsbeispielknoten](https://github.com/OfficeDev/Microsoft-Teams-Samples/blob/main/samples/app-auth/nodejs/src/views/tab/silent/silent.hbs) ist.

[Initiieren Sie die konfigurierbare Registerkarte für die automatische und einfache Authentifizierung mit Microsoft Azure Active Directory (Azure AD),](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-channel-group-config-page-auth/csharp) und befolgen Sie die Anweisungen, um das Beispiel auf Ihrem lokalen Computer auszuführen.

### <a name="include-and-configure-active-directory-authentication-library"></a>Einschließen und Konfigurieren der Active Directory-Authentifizierungsbibliothek

Schließen Sie die Active Directory-Authentifizierungsbibliothek in Ihre Registerkartenseiten ein, und konfigurieren Sie die Bibliothek mit Ihrer Client-ID und Umleitungs-URL:

```html
<script src="https://secure.aadcdn.microsoftonline-p.com/lib/1.0.15/js/adal.min.js" integrity="sha384-lIk8T3uMxKqXQVVfFbiw0K/Nq+kt1P3NtGt/pNexiDby2rKU6xnDY8p16gIwKqgI" crossorigin="anonymous"></script>
<script type="text/javascript">
    // Active Directory Authentication Library configuration
    let config = {
        clientId: "YOUR_APP_ID_HERE",
        // redirectUri must be in the list of redirect URLs for the Microsoft Azure Active Directory (Azure AD) app
        redirectUri: window.location.origin + "/tab-auth/silent-end",
        cacheLocation: "localStorage",
        navigateToLoginRequestUrl: false,
    };
</script>
```

### <a name="get-the-user-context"></a>Abrufen des Benutzerkontexts

Rufen `microsoftTeams.getContext()` Sie auf der Inhaltsseite der Registerkarte auf, um einen Anmeldehinweis für den aktuellen Benutzer abzurufen. Der Hinweis wird im Aufruf von Microsoft Azure Active Directory (Azure AD) als `loginHint` Eins verwendet.

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

Wenn in der Rückruffunktion ein Fehler auftritt, zeigen Sie eine explizite Anmeldeoption an und verwenden Sie diese.

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

Die Active Directory-Authentifizierungsbibliothek analysiert das Ergebnis aus Microsoft Azure Active Directory (Azure AD), indem die Anmelderückrufseite aufgerufen `AuthenticationContext.handleWindowCallback(hash)` wird.

Überprüfen Sie, ob Sie über einen gültigen Benutzer und Anruf `microsoftTeams.authentication.notifySuccess()` verfügen, oder `microsoftTeams.authentication.notifyFailure()` melden Sie den Status ihrer Hauptregisterkarten-Inhaltsseite.

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

### <a name="handle-the-sign-out-flow"></a>Behandeln des Abmeldungsflusses

Verwenden Sie den folgenden Code, um den Abmeldungsfluss in Microsoft Azure Active Directory (Azure AD)-Authentifizierung zu behandeln:

> [!NOTE]
> Wenn Sie sich von Teams Registerkarte oder bot abmelden, wird die aktuelle Sitzung gelöscht.

```javascript
function logout() {
localStorage.clear();
window.location.href = "@Url.Action("<<Action Name>>", "<<Controller Name>>")";
}
```

## <a name="see-also"></a>Weitere Artikel

* [Konfigurieren von Identitätsanbietern für die Verwendung von Microsoft Azure Active Directory (Azure AD)](../../../concepts/authentication/configure-identity-provider.md)
* [Informationen zur Microsoft-Authentifizierungsbibliothek (MSAL)](/azure/active-directory/develop/msal-overview)
