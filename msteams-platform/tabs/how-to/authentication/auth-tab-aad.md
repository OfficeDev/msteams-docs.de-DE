---
title: Authentifizierung für Registerkarten mit Azure Active Directory
description: Beschreibt die Authentifizierung in Teams und deren Verwendung in Registerkarten
ms.topic: how-to
localization_priority: Normal
keywords: Teams-Authentifizierungsregisterkarten AAD
ms.openlocfilehash: 2fdfc4448abb6980cca97e90951d7772611108da
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020387"
---
# <a name="authenticate-a-user-in-a-microsoft-teams-tab"></a><span data-ttu-id="b74cf-104">Authentifizieren eines Benutzers auf einer Microsoft Teams-Registerkarte</span><span class="sxs-lookup"><span data-stu-id="b74cf-104">Authenticate a user in a Microsoft Teams tab</span></span>

> [!Note]
> <span data-ttu-id="b74cf-105">Damit die Authentifizierung für Ihre Registerkarte auf mobilen Clients funktioniert, müssen Sie sicherstellen, dass Sie Version 1.4.1 oder höher des Teams JavaScript SDK verwenden.</span><span class="sxs-lookup"><span data-stu-id="b74cf-105">For authentication to work for your tab on mobile clients, you need to ensure you're using version 1.4.1 or later of the Teams JavaScript SDK.</span></span>

<span data-ttu-id="b74cf-106">Es gibt viele Dienste, die Sie in Ihrer Teams-App nutzen möchten, und die meisten dieser Dienste erfordern Authentifizierung und Autorisierung, um Zugriff auf den Dienst zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="b74cf-106">There are many services that you may wish to consume inside your Teams app, and most of those services require authentication and authorization to get access to the service.</span></span> <span data-ttu-id="b74cf-107">Zu den Diensten gehören Facebook, Twitter und natürlich Teams.</span><span class="sxs-lookup"><span data-stu-id="b74cf-107">Services include Facebook, Twitter, and of course Teams.</span></span> <span data-ttu-id="b74cf-108">Benutzer von Teams verfügen über Benutzerprofilinformationen, die in Azure Active Directory (Azure AD) mithilfe von Microsoft Graph gespeichert sind, und dieser Artikel konzentriert sich auf die Authentifizierung mithilfe von Azure AD, um Zugriff auf diese Informationen zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="b74cf-108">Users of Teams have user profile information stored in Azure Active Directory (Azure AD) using Microsoft Graph and this article will focus on authentication using Azure AD to get access to this information.</span></span>

<span data-ttu-id="b74cf-109">OAuth 2.0 ist ein offener Standard für die Authentifizierung, der von Azure AD und vielen anderen Dienstanbietern verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="b74cf-109">OAuth 2.0 is an open standard for authentication used by Azure AD and many other service providers.</span></span> <span data-ttu-id="b74cf-110">Das Verständnis von OAuth 2.0 ist eine Voraussetzung für die Arbeit mit der Authentifizierung in Teams und Azure AD.</span><span class="sxs-lookup"><span data-stu-id="b74cf-110">Understanding OAuth 2.0 is a prerequisite for working with authentication in Teams and Azure AD.</span></span> <span data-ttu-id="b74cf-111">In den folgenden Beispielen wird der OAuth 2.0 Implicit Grant-Fluss verwendet, um schließlich die Profilinformationen des Benutzers aus Azure AD und Microsoft Graph zu lesen.</span><span class="sxs-lookup"><span data-stu-id="b74cf-111">The examples below use the OAuth 2.0 Implicit Grant flow with the goal of eventually reading the user's profile information from Azure AD and Microsoft Graph.</span></span>

<span data-ttu-id="b74cf-112">Der Code in diesem Artikel stammt aus dem Microsoft Teams-Beispiel für die Registerkartenauthentifizierung [(Node) der Microsoft Teams-Beispielanwendung.](https://github.com/OfficeDev/microsoft-teams-sample-complete-node)</span><span class="sxs-lookup"><span data-stu-id="b74cf-112">The code in this article comes from the Teams sample app [Microsoft Teams tab authentication sample (Node)](https://github.com/OfficeDev/microsoft-teams-sample-complete-node).</span></span> <span data-ttu-id="b74cf-113">Sie enthält eine statische Registerkarte, die ein Zugriffstoken für Microsoft Graph anfordert und die grundlegenden Profilinformationen des aktuellen Benutzers aus Azure AD zeigt.</span><span class="sxs-lookup"><span data-stu-id="b74cf-113">It contains a static tab that requests an access token for Microsoft Graph and shows the current user's basic profile information from Azure AD.</span></span>

<span data-ttu-id="b74cf-114">Eine allgemeine Übersicht über den Authentifizierungsfluss für Registerkarten finden Sie im Thema [Authentifizierungsfluss in Registerkarten](~/tabs/how-to/authentication/auth-flow-tab.md).</span><span class="sxs-lookup"><span data-stu-id="b74cf-114">For a general overview of authentication flow for tabs see the topic [Authentication flow in tabs](~/tabs/how-to/authentication/auth-flow-tab.md).</span></span>

<span data-ttu-id="b74cf-115">Der Authentifizierungsfluss in Registerkarten unterscheidet sich geringfügig vom Authentifizierungsfluss in Bots.</span><span class="sxs-lookup"><span data-stu-id="b74cf-115">Authentication flow in tabs differs slightly from authentication flow in bots.</span></span>

## <a name="configuring-identity-providers"></a><span data-ttu-id="b74cf-116">Konfigurieren von Identitätsanbietern</span><span class="sxs-lookup"><span data-stu-id="b74cf-116">Configuring identity providers</span></span>

<span data-ttu-id="b74cf-117">Ausführliche Schritte [zum](~/concepts/authentication/configure-identity-provider.md) Konfigurieren von OAuth 2.0-Rückrufumleitungs-URL(n) bei Verwendung von Azure Active Directory als Identitätsanbieter finden Sie im Thema Konfigurieren von Identitätsanbietern.</span><span class="sxs-lookup"><span data-stu-id="b74cf-117">See the topic [Configure identity providers](~/concepts/authentication/configure-identity-provider.md) for detailed steps on configuring OAuth 2.0 callback redirect URL(s) when using Azure Active Directory as an identity provider.</span></span>

## <a name="initiate-authentication-flow"></a><span data-ttu-id="b74cf-118">Initiieren des Authentifizierungsflusses</span><span class="sxs-lookup"><span data-stu-id="b74cf-118">Initiate authentication flow</span></span>

<span data-ttu-id="b74cf-119">Der Authentifizierungsfluss sollte durch eine Benutzeraktion ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="b74cf-119">Authentication flow should be triggered by a user action.</span></span> <span data-ttu-id="b74cf-120">Sie sollten das Popup für die Authentifizierung nicht automatisch öffnen, da dies wahrscheinlich den Popupblocker des Browsers auslöst und den Benutzer verwechselt.</span><span class="sxs-lookup"><span data-stu-id="b74cf-120">You should not open the authentication pop-up automatically because this is likely to trigger the browser's pop-up blocker as well as confuse the user.</span></span>

<span data-ttu-id="b74cf-121">Fügen Sie Ihrer Konfigurations- oder Inhaltsseite eine Schaltfläche hinzu, damit sich der Benutzer bei Bedarf anmelden kann.</span><span class="sxs-lookup"><span data-stu-id="b74cf-121">Add a button to your configuration or content page to enable the user to sign in when needed.</span></span> <span data-ttu-id="b74cf-122">Dies kann auf der [Registerkartenkonfigurationsseite](~/tabs/how-to/create-tab-pages/configuration-page.md) oder auf einer beliebigen [Inhaltsseite geschehen.](~/tabs/how-to/create-tab-pages/content-page.md)</span><span class="sxs-lookup"><span data-stu-id="b74cf-122">This can be done in the tab [configuration](~/tabs/how-to/create-tab-pages/configuration-page.md) page or any [content](~/tabs/how-to/create-tab-pages/content-page.md) page.</span></span>

<span data-ttu-id="b74cf-123">Azure AD lässt wie die meisten Identitätsanbieter nicht zu, dass seine Inhalte in einem iframe platziert werden.</span><span class="sxs-lookup"><span data-stu-id="b74cf-123">Azure AD, like most identity providers, does not allow its content to be placed in an iframe.</span></span> <span data-ttu-id="b74cf-124">Dies bedeutet, dass Sie eine Popupseite zum Hosten des Identitätsanbieters hinzufügen müssen.</span><span class="sxs-lookup"><span data-stu-id="b74cf-124">This means that you will need to add a pop-up page to host the identity provider.</span></span> <span data-ttu-id="b74cf-125">Im folgenden Beispiel ist diese Seite `/tab-auth/simple-start` .</span><span class="sxs-lookup"><span data-stu-id="b74cf-125">In the following example this page is `/tab-auth/simple-start`.</span></span> <span data-ttu-id="b74cf-126">Verwenden Sie `microsoftTeams.authenticate()` die Funktion des Microsoft Teams-Client-SDK, um diese Seite zu starten, wenn Ihre Schaltfläche ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="b74cf-126">Use the `microsoftTeams.authenticate()` function of the Microsoft Teams client SDK to launch this page when your button is selected.</span></span>

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

### <a name="notes"></a><span data-ttu-id="b74cf-127">Notes</span><span class="sxs-lookup"><span data-stu-id="b74cf-127">Notes</span></span>

* <span data-ttu-id="b74cf-128">Die URL, an die Sie `microsoftTeams.authentication.authenticate()` übergeben, ist die Startseite des Authentifizierungsflusses.</span><span class="sxs-lookup"><span data-stu-id="b74cf-128">The URL you pass to `microsoftTeams.authentication.authenticate()` is the start page of the authentication flow.</span></span> <span data-ttu-id="b74cf-129">In diesem Beispiel ist dies `/tab-auth/simple-start` .</span><span class="sxs-lookup"><span data-stu-id="b74cf-129">In this example that is `/tab-auth/simple-start`.</span></span> <span data-ttu-id="b74cf-130">Dies sollte mit dem übereinstimmen, was Sie im [Azure AD Application Registration Portal registriert haben.](https://apps.dev.microsoft.com)</span><span class="sxs-lookup"><span data-stu-id="b74cf-130">This should match what you registered in the [Azure AD Application Registration Portal](https://apps.dev.microsoft.com).</span></span>

* <span data-ttu-id="b74cf-131">Der Authentifizierungsfluss muss auf einer Seite in Ihrer Domäne beginnen.</span><span class="sxs-lookup"><span data-stu-id="b74cf-131">Authentication flow must start on a page that's on your domain.</span></span> <span data-ttu-id="b74cf-132">Diese Domäne sollte auch im Abschnitt [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) des Manifests aufgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="b74cf-132">This domain should also be listed in the [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) section of the manifest.</span></span> <span data-ttu-id="b74cf-133">Anderns führt dies zu einem leeren Popup.</span><span class="sxs-lookup"><span data-stu-id="b74cf-133">Failure to do so will result in an empty pop-up.</span></span>

* <span data-ttu-id="b74cf-134">Wenn sie nicht verwendet wird, wird ein Problem damit verursacht, dass das Popup am Ende des Anmeldevorgangs `microsoftTeams.authentication.authenticate()` nicht geschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="b74cf-134">Failing to use `microsoftTeams.authentication.authenticate()` will cause a problem with the popup not closing at the end of the sign in process.</span></span>

## <a name="navigate-to-the-authorization-page-from-your-popup-page"></a><span data-ttu-id="b74cf-135">Navigieren Sie von Ihrer Popupseite zur Autorisierungsseite</span><span class="sxs-lookup"><span data-stu-id="b74cf-135">Navigate to the authorization page from your popup page</span></span>

<span data-ttu-id="b74cf-136">Wenn Ihre Popupseite ( `/tab-auth/simple-start` ) angezeigt wird, wird der folgende Code ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="b74cf-136">When your popup page (`/tab-auth/simple-start`) is displayed the following code is run.</span></span> <span data-ttu-id="b74cf-137">Das Hauptziel dieser Seite besteht in der Umleitung an Ihren Identitätsanbieter, damit sich der Benutzer anmelden kann.</span><span class="sxs-lookup"><span data-stu-id="b74cf-137">The main goal of this page is to redirect to your identity provider so the user can sign in.</span></span> <span data-ttu-id="b74cf-138">Diese Umleitung kann auf Serverseite mithilfe von HTTP 302 durchgeführt werden, in diesem Fall erfolgt sie jedoch auf Clientseite mithilfe eines Aufrufs von `window.location.assign()` .</span><span class="sxs-lookup"><span data-stu-id="b74cf-138">This redirection could be done on the server side using HTTP 302, but in this case it is done on the client side using with a call to `window.location.assign()`.</span></span> <span data-ttu-id="b74cf-139">Dies ermöglicht `microsoftTeams.getContext()` auch das Abrufen von Hinweisinformationen, die an Azure AD übergeben werden können.</span><span class="sxs-lookup"><span data-stu-id="b74cf-139">This also allows `microsoftTeams.getContext()` to be used to retrieve hinting information which can be passed to Azure AD.</span></span>

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

<span data-ttu-id="b74cf-140">Nachdem der Benutzer die Autorisierung abgeschlossen hat, wird der Benutzer zur Rückrufseite umgeleitet, die Sie für Ihre App unter angegeben `/tab-auth/simple-end` haben.</span><span class="sxs-lookup"><span data-stu-id="b74cf-140">After the user completes authorization, the user is redirected to the callback page you specified for your app at `/tab-auth/simple-end`.</span></span>

### <a name="notes"></a><span data-ttu-id="b74cf-141">Notes</span><span class="sxs-lookup"><span data-stu-id="b74cf-141">Notes</span></span>

* <span data-ttu-id="b74cf-142">Informationen [zum Erstellen von Authentifizierungsanforderungen](~/tabs/how-to/access-teams-context.md) und URLs finden Sie unter Get user context information.</span><span class="sxs-lookup"><span data-stu-id="b74cf-142">See [get user context information](~/tabs/how-to/access-teams-context.md) for help building authentication requests and URLs.</span></span> <span data-ttu-id="b74cf-143">Sie können beispielsweise den Anmeldenamen des Benutzers als Wert für die Azure AD-Anmeldung verwenden, was bedeutet, dass der Benutzer möglicherweise `login_hint` weniger eingeben muss.</span><span class="sxs-lookup"><span data-stu-id="b74cf-143">For example, you can use the user's login name as the `login_hint` value for Azure AD sign-in, which means the user might need to type less.</span></span> <span data-ttu-id="b74cf-144">Denken Sie daran, dass Sie diesen Kontext nicht direkt als Identitätsnachweis verwenden sollten, da ein Angreifer Ihre Seite in einem schädlichen Browser laden und ihr alle informationen zur Verfügung stellen kann, die sie wünschen.</span><span class="sxs-lookup"><span data-stu-id="b74cf-144">Remember that you should not use this context directly as proof of identity since an attacker could load your page in a malicious browser and provide it with any information they want.</span></span>
* <span data-ttu-id="b74cf-145">Obwohl der Registerkartenkontext nützliche Informationen zum Benutzer enthält, verwenden Sie diese Informationen nicht, um den Benutzer zu authentifizieren, ob Sie ihn als URL-Parameter zu Ihrer Registerkarteninhalts-URL oder durch Aufrufen der Funktion im `microsoftTeams.getContext()` Microsoft Teams-Client-SDK erhalten.</span><span class="sxs-lookup"><span data-stu-id="b74cf-145">Although the tab context provides useful information regarding the user, don't use this information to authenticate the user whether you get it as URL parameters to your tab content URL or by calling the `microsoftTeams.getContext()` function in the Microsoft Teams client SDK.</span></span> <span data-ttu-id="b74cf-146">Ein böswilliger Akteur könnte Ihre Registerkarteninhalts-URL mit eigenen Parametern aufrufen, und eine Webseite, die microsoft Teams als Identitätswechsel bezeichnet, könnte Ihre Registerkarteninhalts-URL in einem iframe laden und eigene Daten an die Funktion `getContext()` zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="b74cf-146">A malicious actor could invoke your tab content URL with its own parameters, and a web page impersonating Microsoft Teams could load your tab content URL in an iframe and return its own data to the `getContext()` function.</span></span> <span data-ttu-id="b74cf-147">Sie sollten die identitätsbezogenen Informationen im Registerkartenkontext einfach als Hinweise behandeln und vor der Verwendung überprüfen.</span><span class="sxs-lookup"><span data-stu-id="b74cf-147">You should treat the identity-related information in the tab context simply as hints and validate them before use.</span></span>
* <span data-ttu-id="b74cf-148">Der Parameter wird verwendet, um zu bestätigen, dass der Dienst, der `state` den Rückruf-URI aufruft, der von Ihnen aufgerufene Dienst ist.</span><span class="sxs-lookup"><span data-stu-id="b74cf-148">The `state` parameter is used to confirm that the service calling the callback URI is the service you called.</span></span> <span data-ttu-id="b74cf-149">Wenn der Parameter im Rückruf nicht mit dem Parameter übereinstimmen, den Sie während des Anrufs gesendet haben, wird der Rückgabeaufruf nicht überprüft und sollte `state` beendet werden.</span><span class="sxs-lookup"><span data-stu-id="b74cf-149">If the `state` parameter in the callback does not match the parameter you sent during the call the return call is not verified and should be terminated.</span></span>
* <span data-ttu-id="b74cf-150">Es ist nicht erforderlich, die Domäne des Identitätsanbieters in die Liste in die Datei `validDomains` "manifest.json" der App zu fügen.</span><span class="sxs-lookup"><span data-stu-id="b74cf-150">It is not necessary to include the identity provider's domain in the `validDomains` list in the app's manifest.json file.</span></span>

## <a name="the-callback-page"></a><span data-ttu-id="b74cf-151">Die Rückrufseite</span><span class="sxs-lookup"><span data-stu-id="b74cf-151">The callback page</span></span>

<span data-ttu-id="b74cf-152">Im letzten Abschnitt haben Sie den Azure AD-Autorisierungsdienst aufgerufen und Benutzer- und App-Informationen übergeben, damit Azure AD dem Benutzer eine eigene monolithische Autorisierungserfahrung bieten kann.</span><span class="sxs-lookup"><span data-stu-id="b74cf-152">In the last section you called the Azure AD authorization service and passed in user and app information so that Azure AD could present the user with its own monolithic authorization experience.</span></span> <span data-ttu-id="b74cf-153">Ihre App hat keine Kontrolle darüber, was in dieser Erfahrung geschieht.</span><span class="sxs-lookup"><span data-stu-id="b74cf-153">Your app has no control over what happens in this experience.</span></span> <span data-ttu-id="b74cf-154">Es weiß nur, was zurückgegeben wird, wenn Azure AD die von Ihnen bereitgestellte Rückrufseite aufruft ( `/tab-auth/simple-end` ).</span><span class="sxs-lookup"><span data-stu-id="b74cf-154">All it knows is what is returned when Azure AD calls the  callback page that you provided (`/tab-auth/simple-end`).</span></span>

<span data-ttu-id="b74cf-155">Auf dieser Seite müssen Sie Erfolg oder Fehler basierend auf den von Azure AD zurückgegebenen Informationen und aufrufen oder `microsoftTeams.authentication.notifySuccess()` `microsoftTeams.authentication.notifyFailure()` ermitteln.</span><span class="sxs-lookup"><span data-stu-id="b74cf-155">In this page you need to determine success or failure based on the information returned by Azure AD and call `microsoftTeams.authentication.notifySuccess()` or `microsoftTeams.authentication.notifyFailure()`.</span></span> <span data-ttu-id="b74cf-156">Wenn die Anmeldung erfolgreich war, haben Sie Zugriff auf Dienstressourcen.</span><span class="sxs-lookup"><span data-stu-id="b74cf-156">If the login was successful you will have access to service resources.</span></span>

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

<span data-ttu-id="b74cf-157">Dieser Code analysiert die Schlüssel-Wert-Paare, die von Azure AD empfangen wurden, mithilfe `window.location.hash` der `getHashParameters()` Hilfsfunktion.</span><span class="sxs-lookup"><span data-stu-id="b74cf-157">This code parses the key-value pairs received from Azure AD in `window.location.hash` using the `getHashParameters()` helper function.</span></span> <span data-ttu-id="b74cf-158">Wenn ein gefunden wird und der Wert mit dem wert identisch ist, der zu Beginn des Authentifizierungsflusses bereitgestellt wird, wird das Zugriffstoken durch Aufrufen an die Registerkarte zurückgegeben. Andernfalls wird ein Fehler mit `access_token` `state` `notifySuccess()` `notifyFailure()` gemeldet.</span><span class="sxs-lookup"><span data-stu-id="b74cf-158">If it finds an `access_token`, and the `state` value is the same as the one provided at the start of the authentication flow, it returns the access token to the tab by calling `notifySuccess()`; otherwise it reports an error with `notifyFailure()`.</span></span>

### <a name="notes"></a><span data-ttu-id="b74cf-159">Notes</span><span class="sxs-lookup"><span data-stu-id="b74cf-159">Notes</span></span>

<span data-ttu-id="b74cf-160">`NotifyFailure()` hat die folgenden vordefinierten Fehlergründe:</span><span class="sxs-lookup"><span data-stu-id="b74cf-160">`NotifyFailure()` has the following predefined failure reasons:</span></span>

* <span data-ttu-id="b74cf-161">`CancelledByUser` Der Benutzer hat das Popupfenster geschlossen, bevor er den Authentifizierungsfluss abgeschlossen hat.</span><span class="sxs-lookup"><span data-stu-id="b74cf-161">`CancelledByUser` the user closed the popup window before completing the authentication flow.</span></span>
* <span data-ttu-id="b74cf-162">`FailedToOpenWindow` das Popupfenster konnte nicht geöffnet werden.</span><span class="sxs-lookup"><span data-stu-id="b74cf-162">`FailedToOpenWindow` the popup window could not be opened.</span></span> <span data-ttu-id="b74cf-163">Wenn Microsoft Teams in einem Browser ausgeführt wird, bedeutet dies in der Regel, dass das Fenster von einem Popupblocker blockiert wurde.</span><span class="sxs-lookup"><span data-stu-id="b74cf-163">When running Microsoft Teams in a browser, this typically means that the window was blocked by a popup blocker.</span></span>

<span data-ttu-id="b74cf-164">Wenn dies erfolgreich ist, können Sie die Seite aktualisieren oder neu laden und inhalte anzeigen, die für den jetzt authentifizierten Benutzer relevant sind.</span><span class="sxs-lookup"><span data-stu-id="b74cf-164">If successful, you can refresh or reload the page and show content relevant to the now-authenticated user.</span></span> <span data-ttu-id="b74cf-165">Wenn die Authentifizierung fehlschlägt, wird eine Fehlermeldung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b74cf-165">If authentication fails, display an error message.</span></span>

<span data-ttu-id="b74cf-166">Ihre App kann ein eigenes Sitzungscookie festlegen, sodass sich der Benutzer nicht erneut anmelden muss, wenn er zu Ihrer Registerkarte auf dem aktuellen Gerät zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="b74cf-166">Your app can set its own session cookie so that the user need not sign in again when they return to your tab on the current device.</span></span>

> [!NOTE]
> <span data-ttu-id="b74cf-167">Chrome 80, das anfang 2020 veröffentlicht werden soll, führt neue Cookiewerte ein und setzt standardmäßig Cookierichtlinien auf.</span><span class="sxs-lookup"><span data-stu-id="b74cf-167">Chrome 80, scheduled for release in early 2020, introduces new cookie values and imposes cookie policies by default.</span></span> <span data-ttu-id="b74cf-168">Es wird empfohlen, dass Sie die beabsichtigte Verwendung für Ihre Cookies festlegen, anstatt sich auf das Standardverhalten des Browsers zu verlassen.</span><span class="sxs-lookup"><span data-stu-id="b74cf-168">It's recommended that you set the intended use for your cookies rather than rely on default browser behavior.</span></span> <span data-ttu-id="b74cf-169">*Weitere Informationen* [finden Sie unter SameSite cookie attribute (2020 update)](../../../resources/samesite-cookie-update.md).</span><span class="sxs-lookup"><span data-stu-id="b74cf-169">*See* [SameSite cookie attribute (2020 update)](../../../resources/samesite-cookie-update.md).</span></span>

>[!NOTE]
><span data-ttu-id="b74cf-170">Um das richtige Token für Microsoft Teams Free- und Gastbenutzer abzurufen, ist es wichtig, dass die Apps mandantenspezifische https://login.microsoftonline.com/ **Endpunkte {tenantId} verwenden.**</span><span class="sxs-lookup"><span data-stu-id="b74cf-170">To get the correct token for Microsoft Teams Free and guest users, it is important that the apps use tenant specific endpoint https://login.microsoftonline.com/**{tenantId}**.</span></span> <span data-ttu-id="b74cf-171">Sie können tenantId aus dem Botnachrichten- oder Registerkartenkontext erhalten.</span><span class="sxs-lookup"><span data-stu-id="b74cf-171">You can get tenantId from the bot message or tab context.</span></span> <span data-ttu-id="b74cf-172">Wenn die Apps verwenden, erhalten die Benutzer falsche Token und melden sich beim "home"-Mandanten anstatt beim Mandanten an, bei dem sie https://login.microsoftonline.com/common derzeit angemeldet sind.</span><span class="sxs-lookup"><span data-stu-id="b74cf-172">If the apps use https://login.microsoftonline.com/common, the users will get incorrect tokens and will log on to the "home" tenant instead of the tenant that they are currently signed into.</span></span>

<span data-ttu-id="b74cf-173">Weitere Informationen zu single Sign-On (SSO) finden Sie im Artikel [Automatische Authentifizierung](~/tabs/how-to/authentication/auth-silent-AAD.md).</span><span class="sxs-lookup"><span data-stu-id="b74cf-173">For more information on Single Sign-On (SSO) see the article [Silent authentication](~/tabs/how-to/authentication/auth-silent-AAD.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="b74cf-174">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="b74cf-174">Code sample</span></span>

<span data-ttu-id="b74cf-175">Beispielcode, der den Vorgang der Registerkartenauthentifizierung mit Azure AD zeigt:</span><span class="sxs-lookup"><span data-stu-id="b74cf-175">Sample code showing the tab authentication process using Azure AD:</span></span>

| <span data-ttu-id="b74cf-176">**Beispielname**</span><span class="sxs-lookup"><span data-stu-id="b74cf-176">**Sample name**</span></span> | <span data-ttu-id="b74cf-177">**description**</span><span class="sxs-lookup"><span data-stu-id="b74cf-177">**description**</span></span> | <span data-ttu-id="b74cf-178">**.NET**</span><span class="sxs-lookup"><span data-stu-id="b74cf-178">**.NET**</span></span> | <span data-ttu-id="b74cf-179">**Node.js**</span><span class="sxs-lookup"><span data-stu-id="b74cf-179">**Node.js**</span></span> |
|-----------------|-----------------|-------------|
| <span data-ttu-id="b74cf-180">Microsoft Teams-Registerkartenauthentifizierung</span><span class="sxs-lookup"><span data-stu-id="b74cf-180">Microsoft Teams tab authentication</span></span> | <span data-ttu-id="b74cf-181">Tab-Authentifizierungsprozess mit Azure AD.</span><span class="sxs-lookup"><span data-stu-id="b74cf-181">Tab authentication process using Azure AD.</span></span> | [<span data-ttu-id="b74cf-182">View</span><span class="sxs-lookup"><span data-stu-id="b74cf-182">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-channel-group-config-page-auth/csharp) | [<span data-ttu-id="b74cf-183">View</span><span class="sxs-lookup"><span data-stu-id="b74cf-183">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-auth/nodejs) |
