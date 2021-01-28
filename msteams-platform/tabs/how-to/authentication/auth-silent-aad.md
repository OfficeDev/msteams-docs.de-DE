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
# <a name="silent-authentication"></a><span data-ttu-id="4446f-104">Automatische Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="4446f-104">Silent authentication</span></span>

> [!NOTE]
> <span data-ttu-id="4446f-105">Damit die Authentifizierung für Ihre Registerkarte auf mobilen Clients funktioniert, müssen Sie sicherstellen, dass Sie mindestens die Version 1.4.1 des JavaScript SDK für Teams verwenden.</span><span class="sxs-lookup"><span data-stu-id="4446f-105">For authentication to work for your tab on mobile clients, you need to ensure you're using at least the 1.4.1 version of the Teams JavaScript SDK.</span></span>

<span data-ttu-id="4446f-106">Bei der automatischen Authentifizierung in Azure Active Directory (Azure AD) wird die Anzahl der Benutzer zum Eingeben ihrer Anmeldeinformationen minimiert, indem das Authentifizierungstoken automatisch aktualisiert wird.</span><span class="sxs-lookup"><span data-stu-id="4446f-106">Silent authentication in Azure Active Directory (Azure AD) minimizes the number of times a user needs to enter their login credentials by silently refreshing the authentication token.</span></span> <span data-ttu-id="4446f-107">(For true single sign-on support, view our [SSO Documentation](~/tabs/how-to/authentication/auth-aad-sso.md))</span><span class="sxs-lookup"><span data-stu-id="4446f-107">(For true single sign-on support, view our [SSO Documentation](~/tabs/how-to/authentication/auth-aad-sso.md))</span></span>

<span data-ttu-id="4446f-108">Wenn Sie Ihren Code vollständig clientseitig halten möchten, können Sie die [Azure Active Directory-Authentifizierungsbibliothek](/azure/active-directory/develop/active-directory-authentication-libraries) für JavaScript verwenden, um im Hintergrund zu versuchen, ein Azure AD-Zugriffstoken zu erwerben.</span><span class="sxs-lookup"><span data-stu-id="4446f-108">If you want to keep your code completely client-side, you can use the [Azure Active Directory Authentication Library](/azure/active-directory/develop/active-directory-authentication-libraries) for JavaScript to attempt to acquire an Azure AD access token silently.</span></span> <span data-ttu-id="4446f-109">Dies bedeutet, dass dem Benutzer möglicherweise kein Popupdialogfeld angezeigt wird, wenn er sich kürzlich angemeldet hat.</span><span class="sxs-lookup"><span data-stu-id="4446f-109">This means that the user may never see a popup dialog if they have signed in recently.</span></span>

<span data-ttu-id="4446f-110">Auch wenn die ADAL.js für AngularJS-Anwendungen optimiert ist, funktioniert sie auch mit reinen JavaScript-Einzelseitenanwendungen.</span><span class="sxs-lookup"><span data-stu-id="4446f-110">Even though the ADAL.js library is optimized for AngularJS applications, it also works with pure JavaScript single-page applications.</span></span>

> [!NOTE]
> <span data-ttu-id="4446f-111">Derzeit funktioniert die automatische Authentifizierung nur für Registerkarten.</span><span class="sxs-lookup"><span data-stu-id="4446f-111">Currently, silent authentication only works for tabs.</span></span> <span data-ttu-id="4446f-112">Es funktioniert noch nicht, wenn Sie sich von einem Bot anmelden.</span><span class="sxs-lookup"><span data-stu-id="4446f-112">It does not yet work when signing in from a bot.</span></span>

## <a name="how-silent-authentication-works"></a><span data-ttu-id="4446f-113">Funktionsweise der automatischen Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="4446f-113">How silent authentication works</span></span>

<span data-ttu-id="4446f-114">Die ADAL.js erstellt einen ausgeblendeten iframe für den impliziten OAuth 2.0-Genehmigungsfluss, gibt jedoch an, dass Azure AD die Anmeldeseite `prompt=none` niemals zeigt.</span><span class="sxs-lookup"><span data-stu-id="4446f-114">The ADAL.js library creates a hidden iframe for OAuth 2.0 implicit grant flow, but it specifies `prompt=none` so that Azure AD never shows the login page.</span></span> <span data-ttu-id="4446f-115">Wenn eine Benutzerinteraktion erforderlich ist, weil sich der Benutzer anmelden oder Zugriff auf die Anwendung gewähren muss, gibt Azure AD sofort einen Fehler zurück, der ADAL.js dann an Ihre App meldet.</span><span class="sxs-lookup"><span data-stu-id="4446f-115">If user interaction is required because the user needs to log in or grant access to the application, Azure AD will immediately return an error that ADAL.js then reports to your app.</span></span> <span data-ttu-id="4446f-116">An diesem Punkt kann Ihre App bei Bedarf eine Anmeldeschaltfläche anzeigen.</span><span class="sxs-lookup"><span data-stu-id="4446f-116">At this point your app can show a login button if needed.</span></span>

## <a name="how-to-do-silent-authentication"></a><span data-ttu-id="4446f-117">So wird's bei der automatischen Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="4446f-117">How to do silent authentication</span></span>

<span data-ttu-id="4446f-118">Der Code in diesem Artikel stammt aus der Microsoft Teams-Beispiel-App ["Microsoft Teams Authentication Sample (Node) ".](https://github.com/OfficeDev/microsoft-teams-sample-complete-node)</span><span class="sxs-lookup"><span data-stu-id="4446f-118">The code in this article comes from the Teams sample app [Microsoft Teams Authentication Sample (Node)](https://github.com/OfficeDev/microsoft-teams-sample-complete-node).</span></span>

### <a name="include-and-configure-adal"></a><span data-ttu-id="4446f-119">Include and configure ADAL</span><span class="sxs-lookup"><span data-stu-id="4446f-119">include and configure ADAL</span></span>

<span data-ttu-id="4446f-120">Schließen Sie ADAL.js Bibliothek in Ihre Registerkartenseiten ein, und konfigurieren Sie ADAL mit Ihrer Client-ID und Umleitungs-URL:</span><span class="sxs-lookup"><span data-stu-id="4446f-120">Include the ADAL.js library in your tab pages and configure ADAL with your client ID and redirect URL:</span></span>

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

### <a name="get-the-user-context"></a><span data-ttu-id="4446f-121">Benutzerkontext erhalten</span><span class="sxs-lookup"><span data-stu-id="4446f-121">Get the user context</span></span>

<span data-ttu-id="4446f-122">Rufen Sie auf der Inhaltsseite der Registerkarte einen Anmeldehinweis `microsoftTeams.getContext()` für den aktuellen Benutzer ab.</span><span class="sxs-lookup"><span data-stu-id="4446f-122">In the tab's content page, call `microsoftTeams.getContext()` to get a login hint for the current user.</span></span> <span data-ttu-id="4446f-123">Dies wird als Login_hint beim Aufruf von Azure AD verwendet.</span><span class="sxs-lookup"><span data-stu-id="4446f-123">This will be used as a login_hint in the call to Azure AD.</span></span>

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

### <a name="authenticate"></a><span data-ttu-id="4446f-124">Authentifizieren</span><span class="sxs-lookup"><span data-stu-id="4446f-124">Authenticate</span></span>

<span data-ttu-id="4446f-125">Wenn ADAL für den Benutzer ein nicht gelöschtes Token zwischengespeichert hat, verwenden Sie dies.</span><span class="sxs-lookup"><span data-stu-id="4446f-125">If ADAL has an unexpired token cached for the user, use that.</span></span> <span data-ttu-id="4446f-126">Versuchen Sie andernfalls, ein Token im Hintergrund durch Aufrufen `acquireToken(resource, callback)` abzurufen.</span><span class="sxs-lookup"><span data-stu-id="4446f-126">Otherwise, attempt to get a token silently by calling `acquireToken(resource, callback)`.</span></span> <span data-ttu-id="4446f-127">ADAL.js die Rückruffunktion mit dem angeforderten Token oder einen Fehler, wenn die Authentifizierung fehlschlägt.</span><span class="sxs-lookup"><span data-stu-id="4446f-127">ADAL.js will call your callback function with the requested token, or an error if authentication fails.</span></span>

<span data-ttu-id="4446f-128">Wenn in der Rückruffunktion ein Fehler angezeigt wird, zeigen Sie eine Anmeldeschaltfläche an, und stürzen Sie auf eine explizite Anmeldung zurück.</span><span class="sxs-lookup"><span data-stu-id="4446f-128">If you get an error in the callback function, show a login button and fall back to an explicit login.</span></span>

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

### <a name="process-the-return-value"></a><span data-ttu-id="4446f-129">Verarbeiten des Rückgabewerts</span><span class="sxs-lookup"><span data-stu-id="4446f-129">Process the return value</span></span>

<span data-ttu-id="4446f-130">Lassen ADAL.js sich um die Analyse des Ergebnisses aus Azure AD kümmern, indem Sie `AuthenticationContext.handleWindowCallback(hash)` die Anmelderückrufseite aufrufen.</span><span class="sxs-lookup"><span data-stu-id="4446f-130">Let ADAL.js take care of parsing the result from Azure AD by calling `AuthenticationContext.handleWindowCallback(hash)` in the login callback page.</span></span>

<span data-ttu-id="4446f-131">Überprüfen Sie, ob wir über einen gültigen Benutzer verfügen, und rufen Sie auf oder melden Sie den Status an die Inhaltsseite Ihrer `microsoftTeams.authentication.notifySuccess()` `microsoftTeams.authentication.notifyFailure()` Hauptregisterkarte zurück.</span><span class="sxs-lookup"><span data-stu-id="4446f-131">Check that we have a valid user and call `microsoftTeams.authentication.notifySuccess()` or `microsoftTeams.authentication.notifyFailure()` to report status back to your main tab content page.</span></span>

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
