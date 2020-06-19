---
title: Authentifizierung für Registerkarten mit Azure Active Directory
description: Beschreibung der Authentifizierung in Microsoft Teams und ihrer Verwendung in Registerkarten
keywords: Teams-Authentifizierungs Registerkarten Aad
ms.openlocfilehash: 211c08ce1a51a8f0f13e622856a808661dc97b39
ms.sourcegitcommit: fdcd91b270d4c2e98ab2b2c1029c76c49bb807fa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "44801266"
---
# <a name="authenticate-a-user-in-a-microsoft-teams-tab"></a><span data-ttu-id="4b49d-104">Authentifizieren eines Benutzers auf einer Microsoft Teams-Registerkarte</span><span class="sxs-lookup"><span data-stu-id="4b49d-104">Authenticate a user in a Microsoft Teams tab</span></span>

> [!Note]
> <span data-ttu-id="4b49d-105">Damit die Authentifizierung für Ihre Registerkarte auf mobilen Clients funktioniert, müssen Sie sicherstellen, dass Sie die Version 1.4.1 oder höher des Microsoft Teams-JavaScript-SDK verwenden.</span><span class="sxs-lookup"><span data-stu-id="4b49d-105">For authentication to work for your tab on mobile clients, you need to ensure you're using version 1.4.1 or later of the Teams JavaScript SDK.</span></span>

<span data-ttu-id="4b49d-106">Es gibt viele Dienste, die Sie in Ihrer Teams-App möglicherweise nutzen möchten, und die meisten dieser Dienste erfordern Authentifizierung und Autorisierung, um Zugriff auf den Dienst zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="4b49d-106">There are many services that you may wish to consume inside your Teams app, and most of those services require authentication and authorization to get access to the service.</span></span> <span data-ttu-id="4b49d-107">Zu den Diensten gehören Facebook, Twitter und natürlich Teams.</span><span class="sxs-lookup"><span data-stu-id="4b49d-107">Services include Facebook, Twitter, and of course Teams.</span></span> <span data-ttu-id="4b49d-108">Benutzer von Teams haben Benutzerprofilinformationen, die in Azure Active Directory (Azure AD) mit Microsoft Graph gespeichert sind, und dieser Artikel konzentriert sich auf die Authentifizierung mithilfe von Azure AD, um Zugriff auf diese Informationen zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="4b49d-108">Users of Teams have user profile information stored in Azure Active Directory (Azure AD) using Microsoft Graph and this article will focus on authentication using Azure AD to get access to this information.</span></span>

<span data-ttu-id="4b49d-109">OAuth 2,0 ist ein offener Standard für die Authentifizierung, der von Azure AD und vielen anderen Dienstanbietern verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="4b49d-109">OAuth 2.0 is an open standard for authentication used by Azure AD and many other service providers.</span></span> <span data-ttu-id="4b49d-110">Das Verständnis von OAuth 2,0 ist eine Voraussetzung für die Verwendung der Authentifizierung in Microsoft Teams und Azure AD.</span><span class="sxs-lookup"><span data-stu-id="4b49d-110">Understanding OAuth 2.0 is a prerequisite for working with authentication in Teams and Azure AD.</span></span> <span data-ttu-id="4b49d-111">Die folgenden Beispiele verwenden den impliziten Grant-Fluss von OAuth 2,0 mit dem Ziel, die Profilinformationen des Benutzers schließlich aus Azure AD und Microsoft Graph zu lesen.</span><span class="sxs-lookup"><span data-stu-id="4b49d-111">The examples below use the OAuth 2.0 Implicit Grant flow with the goal of eventually reading the user's profile information from Azure AD and Microsoft Graph.</span></span>

<span data-ttu-id="4b49d-112">Der Code in diesem Artikel stammt aus dem Beispiel für [Microsoft Teams-Beispiel-App-Registerkarten Authentifizierung (Knoten)](https://github.com/OfficeDev/microsoft-teams-sample-complete-node).</span><span class="sxs-lookup"><span data-stu-id="4b49d-112">The code in this article comes from the Teams sample app [Microsoft Teams tab authentication sample (Node)](https://github.com/OfficeDev/microsoft-teams-sample-complete-node).</span></span> <span data-ttu-id="4b49d-113">Sie enthält eine statische Registerkarte, die ein Zugriffstoken für Microsoft Graph anfordert und die grundlegenden Profilinformationen des aktuellen Benutzers aus Azure AD anzeigt.</span><span class="sxs-lookup"><span data-stu-id="4b49d-113">It contains a static tab that requests an access token for Microsoft Graph and shows the current user's basic profile information from Azure AD.</span></span>

<span data-ttu-id="4b49d-114">Eine allgemeine Übersicht über den Authentifizierungs Fluss für Registerkarten finden Sie im Thema [Authentifizierungs Fluss in Registerkarten](~/tabs/how-to/authentication/auth-flow-tab.md).</span><span class="sxs-lookup"><span data-stu-id="4b49d-114">For a general overview of authentication flow for tabs see the topic [Authentication flow in tabs](~/tabs/how-to/authentication/auth-flow-tab.md).</span></span>

<span data-ttu-id="4b49d-115">Der Authentifizierungs Fluss in Registerkarten unterscheidet sich geringfügig vom Authentifizierungs Fluss in Bots.</span><span class="sxs-lookup"><span data-stu-id="4b49d-115">Authentication flow in tabs differs slightly from authentication flow in bots.</span></span>

## <a name="configuring-identity-providers"></a><span data-ttu-id="4b49d-116">Konfigurieren von Identitätsanbietern</span><span class="sxs-lookup"><span data-stu-id="4b49d-116">Configuring identity providers</span></span>

<span data-ttu-id="4b49d-117">Lesen Sie das Thema [configure Identity Providers](~/concepts/authentication/configure-identity-provider.md) for ausführliche steps on Configuring OAuth 2,0 Callback Redirect URL (s) bei Verwendung von Azure Active Directory als Identitätsanbieter.</span><span class="sxs-lookup"><span data-stu-id="4b49d-117">See the topic [Configure identity providers](~/concepts/authentication/configure-identity-provider.md) for detailed steps on configuring OAuth 2.0 callback redirect URL(s) when using Azure Active Directory as an identity provider.</span></span>

## <a name="initiate-authentication-flow"></a><span data-ttu-id="4b49d-118">Initiieren des Authentifizierungs Flusses</span><span class="sxs-lookup"><span data-stu-id="4b49d-118">Initiate authentication flow</span></span>

<span data-ttu-id="4b49d-119">Der Authentifizierungs Fluss sollte durch eine Benutzeraktion ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="4b49d-119">Authentication flow should be triggered by a user action.</span></span> <span data-ttu-id="4b49d-120">Sie sollten das Authentifizierungs Popup nicht automatisch öffnen, da dies wahrscheinlich den Popupblocker des Browsers auslösen und den Benutzer verwirren kann.</span><span class="sxs-lookup"><span data-stu-id="4b49d-120">You should not open the authentication pop-up automatically because this is likely to trigger the browser's pop-up blocker as well as confuse the user.</span></span>

<span data-ttu-id="4b49d-121">Fügen Sie Ihrer Konfiguration oder Inhaltsseite eine Schaltfläche hinzu, um dem Benutzer die Anmeldung bei Bedarf zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="4b49d-121">Add a button to your configuration or content page to enable the user to sign in when needed.</span></span> <span data-ttu-id="4b49d-122">Dies kann auf der Seite "Tab- [Konfiguration](~/tabs/how-to/create-tab-pages/configuration-page.md) " oder einer beliebigen [Inhalts](~/tabs/how-to/create-tab-pages/content-page.md) Seite erfolgen.</span><span class="sxs-lookup"><span data-stu-id="4b49d-122">This can be done in the tab [configuration](~/tabs/how-to/create-tab-pages/configuration-page.md) page or any [content](~/tabs/how-to/create-tab-pages/content-page.md) page.</span></span>

<span data-ttu-id="4b49d-123">Azure AD, wie bei den meisten Identitätsanbietern, lässt nicht zu, dass der Inhalt in einen iframe eingefügt wird.</span><span class="sxs-lookup"><span data-stu-id="4b49d-123">Azure AD, like most identity providers, does not allow its content to be placed in an iframe.</span></span> <span data-ttu-id="4b49d-124">Dies bedeutet, dass Sie eine Popupseite zum Hosten des Identitätsanbieters hinzufügen müssen.</span><span class="sxs-lookup"><span data-stu-id="4b49d-124">This means that you will need to add a pop-up page to host the identity provider.</span></span> <span data-ttu-id="4b49d-125">Im folgenden Beispiel ist diese Seite `/tab-auth/simple-start` .</span><span class="sxs-lookup"><span data-stu-id="4b49d-125">In the following example this page is `/tab-auth/simple-start`.</span></span> <span data-ttu-id="4b49d-126">Verwenden Sie die `microsoftTeams.authenticate()` Funktion des Microsoft Teams-Client-SDK, um diese Seite zu starten, wenn Ihre Schaltfläche ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="4b49d-126">Use the `microsoftTeams.authenticate()` function of the Microsoft Teams client SDK to launch this page when your button is selected.</span></span>

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

### <a name="notes"></a><span data-ttu-id="4b49d-127">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="4b49d-127">Notes</span></span>

* <span data-ttu-id="4b49d-128">Die URL, an die Sie übergeben werden, `microsoftTeams.authentication.authenticate()` ist die Startseite des Authentifizierungs Flusses.</span><span class="sxs-lookup"><span data-stu-id="4b49d-128">The URL you pass to `microsoftTeams.authentication.authenticate()` is the start page of the authentication flow.</span></span> <span data-ttu-id="4b49d-129">In diesem Beispiel ist dies `/tab-auth/simple-start` .</span><span class="sxs-lookup"><span data-stu-id="4b49d-129">In this example that is `/tab-auth/simple-start`.</span></span> <span data-ttu-id="4b49d-130">Dies sollte mit dem übereinstimmen, was Sie im [Azure AD-Anwendungs Registrierungs Portal](https://apps.dev.microsoft.com)registriert haben.</span><span class="sxs-lookup"><span data-stu-id="4b49d-130">This should match what you registered in the [Azure AD Application Registration Portal](https://apps.dev.microsoft.com).</span></span>

* <span data-ttu-id="4b49d-131">Der Authentifizierungs Fluss muss auf einer Seite beginnen, die sich in Ihrer Domäne befindet.</span><span class="sxs-lookup"><span data-stu-id="4b49d-131">Authentication flow must start on a page that's on your domain.</span></span> <span data-ttu-id="4b49d-132">Diese Domäne sollte auch im [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) Abschnitt des Manifests aufgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="4b49d-132">This domain should also be listed in the [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) section of the manifest.</span></span> <span data-ttu-id="4b49d-133">Andernfalls wird ein leeres Popup angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4b49d-133">Failure to do so will result in an empty pop-up.</span></span>

* <span data-ttu-id="4b49d-134">Wenn die Verwendung `microsoftTeams.authentication.authenticate()` nicht möglich ist, wird das Popup-Fenster am Ende des Anmeldevorgangs nicht geschlossen.</span><span class="sxs-lookup"><span data-stu-id="4b49d-134">Failing to use `microsoftTeams.authentication.authenticate()` will cause a problem with the popup not closing at the end of the sign in process.</span></span>

## <a name="navigate-to-the-authorization-page-from-your-popup-page"></a><span data-ttu-id="4b49d-135">Navigieren Sie von ihrer Popupseite zur Autorisierungs Seite.</span><span class="sxs-lookup"><span data-stu-id="4b49d-135">Navigate to the authorization page from your popup page</span></span>

<span data-ttu-id="4b49d-136">Wenn Ihre Popup-Seite ( `/tab-auth/simple-start` ) angezeigt wird, wird der folgende Code ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="4b49d-136">When your popup page (`/tab-auth/simple-start`) is displayed the following code is run.</span></span> <span data-ttu-id="4b49d-137">Das Hauptziel dieser Seite ist die Umleitung an Ihren Identitätsanbieter, damit der Benutzer sich anmelden kann.</span><span class="sxs-lookup"><span data-stu-id="4b49d-137">The main goal of this page is to redirect to your identity provider so the user can sign in.</span></span> <span data-ttu-id="4b49d-138">Diese Umleitung kann auf der Serverseite mithilfe von HTTP 302 ausgeführt werden, in diesem Fall wird Sie jedoch auf der Clientseite mit einem Aufruf von ausgeführt `window.location.assign()` .</span><span class="sxs-lookup"><span data-stu-id="4b49d-138">This redirection could be done on the server side using HTTP 302, but in this case it is done on the client side using with a call to `window.location.assign()`.</span></span> <span data-ttu-id="4b49d-139">Dies ermöglicht auch das `microsoftTeams.getContext()` Abrufen von Hinweis Informationen, die an Azure AD übergeben werden können.</span><span class="sxs-lookup"><span data-stu-id="4b49d-139">This also allows `microsoftTeams.getContext()` to be used to retrieve hinting information which can be passed to Azure AD.</span></span>

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
        resource: "https://graph.microsoft.com/User.Read openid",
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

<span data-ttu-id="4b49d-140">Nachdem der Benutzer die Autorisierung abgeschlossen hat, wird der Benutzer zur Rückruf Seite umgeleitet, die Sie für Ihre APP unter angegeben haben `/tab-auth/simple-end` .</span><span class="sxs-lookup"><span data-stu-id="4b49d-140">After the user completes authorization, the user is redirected to the callback page you specified for your app at `/tab-auth/simple-end`.</span></span>

### <a name="notes"></a><span data-ttu-id="4b49d-141">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="4b49d-141">Notes</span></span>

* <span data-ttu-id="4b49d-142">Informationen zum Erstellen von Authentifizierungsanforderungen und-URLs finden Sie unter [Abrufen von Benutzerkontextinformationen](~/tabs/how-to/access-teams-context.md) .</span><span class="sxs-lookup"><span data-stu-id="4b49d-142">See [get user context information](~/tabs/how-to/access-teams-context.md) for help building authentication requests and URLs.</span></span> <span data-ttu-id="4b49d-143">Sie können beispielsweise den Anmeldenamen des Benutzers als `login_hint` Wert für Azure AD Anmeldung verwenden, was bedeutet, dass der Benutzer möglicherweise less eingeben muss.</span><span class="sxs-lookup"><span data-stu-id="4b49d-143">For example, you can use the user's login name as the `login_hint` value for Azure AD sign-in, which means the user might need to type less.</span></span> <span data-ttu-id="4b49d-144">Denken Sie daran, dass Sie diesen Kontext nicht direkt als Identitätsnachweis verwenden sollten, da ein Angreifer die Seite in einen bösartigen Browser laden und ihm alle gewünschten Informationen bereitstellen kann.</span><span class="sxs-lookup"><span data-stu-id="4b49d-144">Remember that you should not use this context directly as proof of identity since an attacker could load your page in a malicious browser and provide it with any information they want.</span></span>
* <span data-ttu-id="4b49d-145">Obwohl der Registerkartenkontext nützliche Informationen für den Benutzer bereitstellt, verwenden Sie diese Informationen nicht, um den Benutzer zu authentifizieren, unabhängig davon, ob Sie ihn als URL-Parameter zu ihrer Registerkarten-Inhalts-URL oder durch Aufrufen der `microsoftTeams.getContext()` Funktion im Microsoft Teams-Client-SDK erhalten.</span><span class="sxs-lookup"><span data-stu-id="4b49d-145">Although the tab context provides useful information regarding the user, don't use this information to authenticate the user whether you get it as URL parameters to your tab content URL or by calling the `microsoftTeams.getContext()` function in the Microsoft Teams client SDK.</span></span> <span data-ttu-id="4b49d-146">Ein böswilliger Akteur könnte Ihre Registerkarteninhalts-URL mit seinen eigenen Parametern aufrufen, und eine Webseite, die Microsoft Teams imitiert, kann die URL Ihres Registerkarteninhalts in einen iframe laden und eigene Daten an die Funktion zurückgeben `getContext()` .</span><span class="sxs-lookup"><span data-stu-id="4b49d-146">A malicious actor could invoke your tab content URL with its own parameters, and a web page impersonating Microsoft Teams could load your tab content URL in an iframe and return its own data to the `getContext()` function.</span></span> <span data-ttu-id="4b49d-147">Sie sollten die identitätsbezogenen Informationen im Registerkartenkontext lediglich als Hinweise behandeln und diese vor der Verwendung validieren.</span><span class="sxs-lookup"><span data-stu-id="4b49d-147">You should treat the identity-related information in the tab context simply as hints and validate them before use.</span></span>
* <span data-ttu-id="4b49d-148">Der `state` -Parameter wird verwendet, um zu bestätigen, dass der Dienst, der den Rückruf-URI aufruft, der von Ihnen aufgerufene Dienst ist.</span><span class="sxs-lookup"><span data-stu-id="4b49d-148">The `state` parameter is used to confirm that the service calling the callback URI is the service you called.</span></span> <span data-ttu-id="4b49d-149">Wenn der `state` Parameter im Rückruf nicht mit dem Parameter übereinstimmt, den Sie während des Anrufs gesendet haben, wird der Rückgabe Aufruf nicht überprüft und sollte beendet werden.</span><span class="sxs-lookup"><span data-stu-id="4b49d-149">If the `state` parameter in the callback does not match the parameter you sent during the call the return call is not verified and should be terminated.</span></span>
* <span data-ttu-id="4b49d-150">Es ist nicht erforderlich, die Domäne des Identitätsanbieters in die `validDomains` Liste im manifest.jsder app in der Datei einzuschließen.</span><span class="sxs-lookup"><span data-stu-id="4b49d-150">It is not necessary to include the identity provider's domain in the `validDomains` list in the app's manifest.json file.</span></span>

## <a name="the-callback-page"></a><span data-ttu-id="4b49d-151">Die Rückruf Seite</span><span class="sxs-lookup"><span data-stu-id="4b49d-151">The callback page</span></span>

<span data-ttu-id="4b49d-152">Im letzten Abschnitt haben Sie den Azure AD Autorisierungsdienst aufgerufen und in Benutzer-und App-Informationen übergeben, damit Azure AD dem Benutzer eine eigene monolithische Autorisierungs Erfahrung präsentieren kann.</span><span class="sxs-lookup"><span data-stu-id="4b49d-152">In the last section you called the Azure AD authorization service and passed in user and app information so that Azure AD could present the user with its own monolithic authorization experience.</span></span> <span data-ttu-id="4b49d-153">Ihre APP hat keine Kontrolle darüber, was in dieser Erfahrung geschieht.</span><span class="sxs-lookup"><span data-stu-id="4b49d-153">Your app has no control over what happens in this experience.</span></span> <span data-ttu-id="4b49d-154">Er weiß nur, was zurückgegeben wird, wenn Azure Ad die von Ihnen angegebene Rückruf Seite aufruft ( `/tab-auth/simple-end` ).</span><span class="sxs-lookup"><span data-stu-id="4b49d-154">All it knows is what is returned when Azure AD calls the  callback page that you provided (`/tab-auth/simple-end`).</span></span>

<span data-ttu-id="4b49d-155">Auf dieser Seite müssen Sie den Erfolg oder Misserfolg basierend auf den von Azure AD und Call oder zurückgegebenen Informationen ermitteln `microsoftTeams.authentication.notifySuccess()` `microsoftTeams.authentication.notifyFailure()` .</span><span class="sxs-lookup"><span data-stu-id="4b49d-155">In this page you need to determine success or failure based on the information returned by Azure AD and call `microsoftTeams.authentication.notifySuccess()` or `microsoftTeams.authentication.notifyFailure()`.</span></span> <span data-ttu-id="4b49d-156">Wenn die Anmeldung erfolgreich verlaufen ist, haben Sie Zugriff auf Dienst Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="4b49d-156">If the login was successful you will have access to service resources.</span></span>

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

<span data-ttu-id="4b49d-157">Dieser Code analysiert die Schlüssel-Wert-Paare, die von Azure AD in `window.location.hash` mit der `getHashParameters()` Hilfsfunktion empfangen werden.</span><span class="sxs-lookup"><span data-stu-id="4b49d-157">This code parses the key-value pairs received from Azure AD in `window.location.hash` using the `getHashParameters()` helper function.</span></span> <span data-ttu-id="4b49d-158">Wenn er einen findet `access_token` und der Wert mit dem `state` identisch ist, der am Anfang des Authentifizierungs Flusses bereitgestellt wurde, wird das Zugriffstoken durch Aufrufen an die Registerkarte zurückgegeben `notifySuccess()` ; andernfalls meldet er einen Fehler mit `notifyFailure()` .</span><span class="sxs-lookup"><span data-stu-id="4b49d-158">If it finds an `access_token`, and the `state` value is the same as the one provided at the start of the authentication flow, it returns the access token to the tab by calling `notifySuccess()`; otherwise it reports an error with `notifyFailure()`.</span></span>

### <a name="notes"></a><span data-ttu-id="4b49d-159">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="4b49d-159">Notes</span></span>

<span data-ttu-id="4b49d-160">`NotifyFailure()`weist die folgenden vordefinierten Fehlerursachen auf:</span><span class="sxs-lookup"><span data-stu-id="4b49d-160">`NotifyFailure()` has the following predefined failure reasons:</span></span>

* <span data-ttu-id="4b49d-161">`CancelledByUser`der Benutzer hat das Popupfenster geschlossen, bevor der Authentifizierungs Fluss abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="4b49d-161">`CancelledByUser` the user closed the popup window before completing the authentication flow.</span></span>
* <span data-ttu-id="4b49d-162">`FailedToOpenWindow`das Popupfenster konnte nicht geöffnet werden.</span><span class="sxs-lookup"><span data-stu-id="4b49d-162">`FailedToOpenWindow` the popup window could not be opened.</span></span> <span data-ttu-id="4b49d-163">Bei der Ausführung von Microsoft Teams in einem Browser bedeutet dies normalerweise, dass das Fenster von einem Popupblocker blockiert wurde.</span><span class="sxs-lookup"><span data-stu-id="4b49d-163">When running Microsoft Teams in a browser, this typically means that the window was blocked by a popup blocker.</span></span>

<span data-ttu-id="4b49d-164">Wenn die Methode erfolgreich verläuft, können Sie die Seite aktualisieren oder neu laden und Inhalte anzeigen, die für den jetzt authentifizierten Benutzer relevant sind.</span><span class="sxs-lookup"><span data-stu-id="4b49d-164">If successful, you can refresh or reload the page and show content relevant to the now-authenticated user.</span></span> <span data-ttu-id="4b49d-165">Wenn die Authentifizierung fehlschlägt, wird eine Fehlermeldung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4b49d-165">If authentication fails, display an error message.</span></span>

<span data-ttu-id="4b49d-166">Ihre APP kann ein eigenes Sitzungscookie festlegen, sodass sich der Benutzer nicht erneut anmelden muss, wenn er zur Registerkarte auf dem aktuellen Gerät zurückkehrt.</span><span class="sxs-lookup"><span data-stu-id="4b49d-166">Your app can set its own session cookie so that the user need not sign in again when they return to your tab on the current device.</span></span>

> [!NOTE]
> <span data-ttu-id="4b49d-167">In Chrome 80, das für die Veröffentlichung Anfang 2020 vorgesehen ist, werden neue Cookiewerte eingeführt und standardmäßig Cookie-Richtlinien auferlegt.</span><span class="sxs-lookup"><span data-stu-id="4b49d-167">Chrome 80, scheduled for release in early 2020, introduces new cookie values and imposes cookie policies by default.</span></span> <span data-ttu-id="4b49d-168">Es wird empfohlen, dass Sie die vorgesehene Verwendung für Ihre Cookies festlegen, anstatt sich auf das Standardbrowser Verhalten zu verlassen.</span><span class="sxs-lookup"><span data-stu-id="4b49d-168">It's recommended that you set the intended use for your cookies rather than rely on default browser behavior.</span></span> <span data-ttu-id="4b49d-169">*Siehe* [SameSite-Cookie-Attribut (2020 Update)](../../../resources/samesite-cookie-update.md).</span><span class="sxs-lookup"><span data-stu-id="4b49d-169">*See* [SameSite cookie attribute (2020 update)](../../../resources/samesite-cookie-update.md).</span></span>

<span data-ttu-id="4b49d-170">Weitere Informationen zum einmaligen Anmelden (SSO) finden Sie im Artikel [Silent Authentication](~/tabs/how-to/authentication/auth-silent-AAD.md).</span><span class="sxs-lookup"><span data-stu-id="4b49d-170">For more information on Single Sign-On (SSO) see the article [Silent authentication](~/tabs/how-to/authentication/auth-silent-AAD.md).</span></span>

## <a name="samples"></a><span data-ttu-id="4b49d-171">Beispiele</span><span class="sxs-lookup"><span data-stu-id="4b49d-171">Samples</span></span>

<span data-ttu-id="4b49d-172">Beispielcode zum Anzeigen des Registerkarten Authentifizierungsprozesses mit Azure AD finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="4b49d-172">For sample code showing the tab authentication process using Azure AD see:</span></span>

* [<span data-ttu-id="4b49d-173">Beispiel für Microsoft Teams-Registerkarten Authentifizierung (Knoten)</span><span class="sxs-lookup"><span data-stu-id="4b49d-173">Microsoft Teams tab authentication sample (Node)</span></span>](https://github.com/OfficeDev/microsoft-teams-sample-auth-node)
