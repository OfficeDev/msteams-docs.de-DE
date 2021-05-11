---
title: Automatische Authentifizierung
description: Beschreibt die automatische Authentifizierung
ms.topic: conceptual
localization_priority: Normal
keywords: teams authentication SSO silent AAD
ms.openlocfilehash: 0c75c6d50fd1191b6ea8548d65c9df4ce8453898
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019601"
---
# <a name="silent-authentication"></a><span data-ttu-id="c19fd-104">Automatische Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="c19fd-104">Silent authentication</span></span>

> [!NOTE]
> <span data-ttu-id="c19fd-105">Damit die Authentifizierung für Ihre Registerkarte auf mobilen Clients funktioniert, stellen Sie sicher, dass Sie mindestens die Version 1.4.1 des Teams JavaScript SDK verwenden.</span><span class="sxs-lookup"><span data-stu-id="c19fd-105">For authentication to work for your tab on mobile clients, ensure you are using at least 1.4.1 version of the Teams JavaScript SDK.</span></span>

<span data-ttu-id="c19fd-106">Die automatische Authentifizierung in Azure Active Directory (AAD) minimiert die Anzahl, mit der ein Benutzer seine Anmeldeinformationen einzahlt, indem das Authentifizierungstoken automatisch aktualisiert wird.</span><span class="sxs-lookup"><span data-stu-id="c19fd-106">Silent authentication in Azure Active Directory (AAD) minimizes the number of times a user enters their sign in credentials by silently refreshing the authentication token.</span></span> <span data-ttu-id="c19fd-107">Eine echte Unterstützung für einmaliges Anmelden finden Sie in [der SSO-Dokumentation](~/tabs/how-to/authentication/auth-aad-sso.md).</span><span class="sxs-lookup"><span data-stu-id="c19fd-107">For true single sign-on support, see [SSO documentation](~/tabs/how-to/authentication/auth-aad-sso.md).</span></span>

<span data-ttu-id="c19fd-108">Wenn Sie Ihren Code vollständig clientseitig halten möchten, können Sie die AAD-Authentifizierungsbibliothek für JavaScript verwenden, um im Hintergrund ein AAD-Zugriffstoken abzurufen. [](/azure/active-directory/develop/active-directory-authentication-libraries)</span><span class="sxs-lookup"><span data-stu-id="c19fd-108">If you want to keep your code completely client-side, you can use the [AAD authentication library](/azure/active-directory/develop/active-directory-authentication-libraries) for JavaScript to get an AAD access token silently.</span></span> <span data-ttu-id="c19fd-109">Wenn sich der Benutzer kürzlich angemeldet hat, wird nie ein Popupdialogfeld angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c19fd-109">If the user has signed in recently, they never see a popup dialog box.</span></span>

<span data-ttu-id="c19fd-110">Auch wenn die ADAL.js für AngularJS-Anwendungen optimiert ist, funktioniert sie auch mit reinen JavaScript-Einseitenanwendungen.</span><span class="sxs-lookup"><span data-stu-id="c19fd-110">Even though the ADAL.js library is optimized for AngularJS applications, it also works with pure JavaScript single-page applications.</span></span>

> [!NOTE]
> <span data-ttu-id="c19fd-111">Derzeit funktioniert die automatische Authentifizierung nur für Registerkarten.</span><span class="sxs-lookup"><span data-stu-id="c19fd-111">Currently, silent authentication only works for tabs.</span></span> <span data-ttu-id="c19fd-112">Es funktioniert nicht, wenn Sie sich über einen Bot anmelden.</span><span class="sxs-lookup"><span data-stu-id="c19fd-112">It does not work when signing in from a bot.</span></span>

## <a name="how-silent-authentication-works"></a><span data-ttu-id="c19fd-113">Funktionsweise der automatischen Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="c19fd-113">How silent authentication works</span></span>

<span data-ttu-id="c19fd-114">Die ADAL.js erstellt einen ausgeblendeten iframe für den impliziten OAuth 2.0-Erteilungsfluss.</span><span class="sxs-lookup"><span data-stu-id="c19fd-114">The ADAL.js library creates a hidden iframe for OAuth 2.0 implicit grant flow.</span></span> <span data-ttu-id="c19fd-115">Die Bibliothek gibt jedoch `prompt=none` an, sodass Azure AD die Anmeldeseite niemals zeigt.</span><span class="sxs-lookup"><span data-stu-id="c19fd-115">But the library specifies `prompt=none`, so Azure AD never shows the sign in page.</span></span> <span data-ttu-id="c19fd-116">Wenn benutzerinteraktion erforderlich ist, da sich der Benutzer anmelden oder Zugriff auf die Anwendung gewähren muss, gibt AAD sofort einen Fehler zurück, der ADAL.js App meldet.</span><span class="sxs-lookup"><span data-stu-id="c19fd-116">If user interaction is required because the user needs to sign in or grant access to the application, AAD immediately returns an error that ADAL.js reports to your app.</span></span> <span data-ttu-id="c19fd-117">An diesem Punkt kann Ihre App bei Bedarf eine Anmeldeschaltfläche anzeigen.</span><span class="sxs-lookup"><span data-stu-id="c19fd-117">At this point your app can show a sign in button if required.</span></span>

## <a name="how-to-do-silent-authentication"></a><span data-ttu-id="c19fd-118">So gehen Sie zur automatischen Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="c19fd-118">How to do silent authentication</span></span>

<span data-ttu-id="c19fd-119">Der Code in diesem Artikel stammt aus Teams Beispiel-App, die Teams [Authentifizierungsbeispielknoten ist.](https://github.com/OfficeDev/Microsoft-Teams-Samples/blob/main/samples/app-auth/nodejs/src/views/tab/silent/silent.hbs)</span><span class="sxs-lookup"><span data-stu-id="c19fd-119">The code in this article comes from the Teams sample app that is [Teams authentication sample node](https://github.com/OfficeDev/Microsoft-Teams-Samples/blob/main/samples/app-auth/nodejs/src/views/tab/silent/silent.hbs).</span></span>

<span data-ttu-id="c19fd-120">[Initiieren Sie die konfigurierbare Registerkarte](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-channel-group-config-page-auth/csharp) für die automatische und einfache Authentifizierung mithilfe von AAD, und befolgen Sie die Anweisungen zum Ausführen des Beispiels auf Dem lokalen Computer.</span><span class="sxs-lookup"><span data-stu-id="c19fd-120">[Initiate silent and simple authentication configurable tab using AAD](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-channel-group-config-page-auth/csharp) and follow the instructions to run the sample on your local machine.</span></span>

### <a name="include-and-configure-adal"></a><span data-ttu-id="c19fd-121">Ein- und Konfigurieren von ADAL</span><span class="sxs-lookup"><span data-stu-id="c19fd-121">Include and configure ADAL</span></span>

<span data-ttu-id="c19fd-122">Fügen Sie die ADAL.js in Ihre Registerkartenseiten ein, und konfigurieren Sie ADAL mit Ihrer Client-ID und Umleitungs-URL:</span><span class="sxs-lookup"><span data-stu-id="c19fd-122">Include the ADAL.js library in your tab pages and configure ADAL with your client ID and redirect URL:</span></span>

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

### <a name="get-the-user-context"></a><span data-ttu-id="c19fd-123">Benutzerkontext erhalten</span><span class="sxs-lookup"><span data-stu-id="c19fd-123">Get the user context</span></span>

<span data-ttu-id="c19fd-124">Rufen Sie auf der Inhaltsseite der Registerkarte auf, um einen Anmeldehinweis für den `microsoftTeams.getContext()` aktuellen Benutzer zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="c19fd-124">In the tab's content page, call `microsoftTeams.getContext()` to get a sign in hint for the current user.</span></span> <span data-ttu-id="c19fd-125">Dies wird als loginHint im Aufruf von AAD verwendet.</span><span class="sxs-lookup"><span data-stu-id="c19fd-125">This is used as a loginHint in the call to AAD.</span></span>

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

### <a name="authenticate"></a><span data-ttu-id="c19fd-126">Authentifizieren</span><span class="sxs-lookup"><span data-stu-id="c19fd-126">Authenticate</span></span>

<span data-ttu-id="c19fd-127">Wenn ADAL ein Token für den Benutzer zwischengespeichert hat, das nicht abgelaufen ist, verwenden Sie dieses Token.</span><span class="sxs-lookup"><span data-stu-id="c19fd-127">If ADAL has a token cached for the user that has not expired, use that token.</span></span> <span data-ttu-id="c19fd-128">Versuchen Sie alternativ, ein Token im Hintergrund abzurufen, indem Sie `acquireToken(resource, callback)` aufrufen.</span><span class="sxs-lookup"><span data-stu-id="c19fd-128">Alternately, attempt to get a token silently by calling `acquireToken(resource, callback)`.</span></span> <span data-ttu-id="c19fd-129">ADAL.js ruft die Rückruffunktion mit dem angeforderten Token auf oder gibt einen Fehler zurück, wenn die Authentifizierung fehlschlägt.</span><span class="sxs-lookup"><span data-stu-id="c19fd-129">ADAL.js calls the callback function with the requested token, or gives an error if authentication fails.</span></span>

<span data-ttu-id="c19fd-130">Wenn sie einen Fehler in der Rückruffunktion erhalten, zeigen Sie eine Anmeldeschaltfläche an, und stürzen Sie auf eine explizite Anmeldung zurück.</span><span class="sxs-lookup"><span data-stu-id="c19fd-130">If you get an error in the callback function, show a sign in button and fall back to an explicit sign in.</span></span>

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

### <a name="process-the-return-value"></a><span data-ttu-id="c19fd-131">Verarbeiten des Rückgabewerts</span><span class="sxs-lookup"><span data-stu-id="c19fd-131">Process the return value</span></span>

<span data-ttu-id="c19fd-132">ADAL.js analysiert das Ergebnis von AAD durch Aufrufen `AuthenticationContext.handleWindowCallback(hash)` der Rückrufseite für die Anmeldung.</span><span class="sxs-lookup"><span data-stu-id="c19fd-132">ADAL.js parses the result from AAD by calling `AuthenticationContext.handleWindowCallback(hash)` in the sign in callback page.</span></span>

<span data-ttu-id="c19fd-133">Überprüfen Sie, ob Sie über einen gültigen Benutzer verfügen, und rufen Sie auf, oder melden Sie den Status ihrer `microsoftTeams.authentication.notifySuccess()` `microsoftTeams.authentication.notifyFailure()` Inhaltsseite für die Hauptregisterkarte.</span><span class="sxs-lookup"><span data-stu-id="c19fd-133">Check that you have a valid user and call `microsoftTeams.authentication.notifySuccess()` or `microsoftTeams.authentication.notifyFailure()` to report the status to your main tab content page.</span></span>

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

### <a name="handle-sign-out-flow"></a><span data-ttu-id="c19fd-134">Behandeln des Abmeldeflusses</span><span class="sxs-lookup"><span data-stu-id="c19fd-134">Handle sign out flow</span></span>

<span data-ttu-id="c19fd-135">Verwenden Sie den folgenden Code, um den Abmeldefluss in AAD Auth zu behandeln:</span><span class="sxs-lookup"><span data-stu-id="c19fd-135">Use the following code to handle sign out flow in AAD Auth:</span></span>

> [!NOTE]
> <span data-ttu-id="c19fd-136">Während die Anmeldung für Teams oder Bot erfolgt ist, wird die aktuelle Sitzung ebenfalls geräumt.</span><span class="sxs-lookup"><span data-stu-id="c19fd-136">While logout for Teams tab or bot is done, the current session is also cleared.</span></span>

```javascript
function logout() {
localStorage.clear();
window.location.href = "@Url.Action("<<Action Name>>", "<<Controller Name>>")";
}
```
