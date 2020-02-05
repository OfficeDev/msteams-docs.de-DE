---
title: Authentifizierungs Fluss für Registerkarten
description: Beschreibt den Authentifizierungs Fluss in Registerkarten
keywords: Registerkarten für Teams-Authentifizierungs Fluss
ms.openlocfilehash: 6c669162f407924f0844b89625f5c5791e96b6f7
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674333"
---
# <a name="microsoft-teams-authentication-flow-for-tabs"></a><span data-ttu-id="a3483-104">Microsoft Teams-Authentifizierungs Fluss für Registerkarten</span><span class="sxs-lookup"><span data-stu-id="a3483-104">Microsoft Teams authentication flow for tabs</span></span>

> [!Note]
> <span data-ttu-id="a3483-105">Damit die Authentifizierung für Ihre Registerkarte auf mobilen Clients funktioniert, müssen Sie sicherstellen, dass Sie mindestens die Version 1.4.1 von Microsoft Teams JavaScript SDK verwenden.</span><span class="sxs-lookup"><span data-stu-id="a3483-105">For authentication to work for your tab on mobile clients, you need to ensure you're using at least the 1.4.1 version of the Teams JavaScript SDK.</span></span>

<span data-ttu-id="a3483-106">OAuth 2,0 ist ein offener Standard für Authentifizierung und Autorisierung, der von Azure AD und vielen anderen Identitätsanbietern verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="a3483-106">OAuth 2.0 is an open standard for authentication and authorization used by Azure AD and many other identity providers.</span></span> <span data-ttu-id="a3483-107">Ein grundlegendes Verständnis von OAuth 2,0 ist eine Voraussetzung für die Verwendung von Authentifizierung in Microsoft Teams. [hier finden Sie eine gute Übersicht](https://aaronparecki.com/oauth-2-simplified/) , die einfacher zu befolgen ist als die [formale Spezifikation](https://oauth.net/2/).</span><span class="sxs-lookup"><span data-stu-id="a3483-107">A basic understanding of OAuth 2.0 is a prerequisite for working with authentication in Teams; [here's a good overview](https://aaronparecki.com/oauth-2-simplified/) that's easier to follow than the [formal specification](https://oauth.net/2/).</span></span> <span data-ttu-id="a3483-108">Der Authentifizierungs Fluss für Registerkarten und Bots ist ein wenig anders, da Registerkarten sehr ähnlich zu Websites sind, sodass Sie OAuth 2,0 direkt verwenden können. Bots sind nicht und müssen ein paar Dinge unterschiedlich tun, aber die Kernkonzepte sind identisch.</span><span class="sxs-lookup"><span data-stu-id="a3483-108">Authentication flow for tabs and bots are a little different because tabs are very similar to websites so they can use OAuth 2.0 directly; bots are not and must do a few things differently, but the core concepts are identical.</span></span>

<span data-ttu-id="a3483-109">ein Beispiel zur Veranschaulichung des Authentifizierungs Flusses für Registerkarten und Bots mithilfe von Node mithilfe des [impliziten Grant-Typs OAuth 2,0](https://oauth.net/2/grant-types/implicit/).</span><span class="sxs-lookup"><span data-stu-id="a3483-109">for an example that demonstrates authentication flow for tabs and bots using Node using the [OAuth 2.0 implicit grant type](https://oauth.net/2/grant-types/implicit/).</span></span>

![Tab-Authentifizierungs-Sequenzdiagramm](~/assets/images/authentication/tab_auth_sequence_diagram.png)

1. <span data-ttu-id="a3483-111">Der Benutzer interagiert mit dem Inhalt auf der Registerkarte Konfiguration oder Inhaltsseite, häufig eine Schaltfläche mit der Bezeichnung "Anmelden" oder "Anmelden".</span><span class="sxs-lookup"><span data-stu-id="a3483-111">The user interacts with the content on the tab configuration or content page, commonly a button labeled "Sign in" or "Log in".</span></span>
2. <span data-ttu-id="a3483-112">Die Registerkarte erstellt die URL für Ihre Authentifizierungs Startseite, optional mithilfe von Informationen aus URL-Platzhaltern oder durch Aufrufen `microsoftTeams.getContext()` der Teams-Client-SDK-Methode, um die Authentifizierungs Erfahrung für den Benutzer zu rationalisieren.</span><span class="sxs-lookup"><span data-stu-id="a3483-112">The tab constructs the URL for its auth start page, optionally using information from URL placeholders or by calling `microsoftTeams.getContext()` Teams client SDK method to streamline the authentication experience for the user.</span></span> <span data-ttu-id="a3483-113">Wenn der `login_hint` Parameter beispielsweise bei der Authentifizierung mit Azure AD auf die e-Mail-Adresse des Benutzers festgelegt ist, muss sich der Benutzer möglicherweise nicht mehr anmelden, wenn er dies kürzlich getan hat, da Azure Ad die zwischengespeicherten Anmeldeinformationen des Benutzers nach Möglichkeit verwenden wird: das Popup blinkt kurz und wird dann ausgeblendet.</span><span class="sxs-lookup"><span data-stu-id="a3483-113">For example, when authenticating with Azure AD, if the `login_hint` parameter is set to the user's email address, the user may not even have to sign in if they have done so recently, because Azure AD will use the user's cached credentials if possible: the popup will flash briefly and then disappear.</span></span>
3. <span data-ttu-id="a3483-114">Anschließend ruft die Registerkarte `microsoftTeams.authentication.authenticate()` die-Methode auf `successCallback` und `failureCallback` registriert die Funktionen und.</span><span class="sxs-lookup"><span data-stu-id="a3483-114">The tab then calls the `microsoftTeams.authentication.authenticate()` method and registers the `successCallback` and `failureCallback` functions.</span></span>
4. <span data-ttu-id="a3483-115">Teams öffnet die Startseite in einem IFRAME in einem Popupfenster.</span><span class="sxs-lookup"><span data-stu-id="a3483-115">Teams opens the start page in an iframe in a pop-up window.</span></span> <span data-ttu-id="a3483-116">Auf der Startseite werden `state` zufällige Daten generiert, für die zukünftige Validierung gespeichert und an den `/authorize` Endpunkt des Identitätsanbieters umgeleitet (Beispiels `https://login.microsoftonline.com/<tenant ID>/oauth2/authorize` Weise für Azure AD).</span><span class="sxs-lookup"><span data-stu-id="a3483-116">The start page generates random `state` data, saves it for future validation, and redirects to the identity provider's `/authorize` endpoint such as `https://login.microsoftonline.com/<tenant ID>/oauth2/authorize` for Azure AD.</span></span> <span data-ttu-id="a3483-117">Ersetzen `<tenant id>` Sie durch ihre eigene Mandanten-ID (Context. TID).</span><span class="sxs-lookup"><span data-stu-id="a3483-117">Replace `<tenant id>` with your own tenant id (context.tid).</span></span>
    * <span data-ttu-id="a3483-118">Wie bei anderen Anwendungs Authentifizierungs Bewegungen in Microsoft Teams muss sich die Startseite in einer Domäne befinden, `validDomains` die sich in der Liste befindet, und in derselben Domäne wie die Umleitungsseite nach der Anmeldung.</span><span class="sxs-lookup"><span data-stu-id="a3483-118">Like other application auth flows in Teams, the start page must be on a domain that's in its `validDomains` list, and on the same domain as the post-login redirect page.</span></span>
    * <span data-ttu-id="a3483-119">**Wichtig**: der implizite Grant-Fluss von OAuth 2,0 `state` Ruft einen Parameter in der Authentifizierungsanforderung ab, der eindeutige Sitzungsdaten enthält, um einen [Fälschungs Angriff auf standortübergreifendes anfordern](https://en.wikipedia.org/wiki/Cross-site_request_forgery)zu verhindern.</span><span class="sxs-lookup"><span data-stu-id="a3483-119">**IMPORTANT**: The OAuth 2.0 implicit grant flow calls for a `state` parameter in the authentication request which contains unique session data to prevent a [cross-site request forgery attack](https://en.wikipedia.org/wiki/Cross-site_request_forgery).</span></span> <span data-ttu-id="a3483-120">In den folgenden Beispielen wird eine zufällig generierte GUID für die `state` Daten verwendet.</span><span class="sxs-lookup"><span data-stu-id="a3483-120">The examples below use a randomly-generated GUID for the `state` data.</span></span>
5. <span data-ttu-id="a3483-121">Der Benutzer meldet sich auf der Website des Anbieters an und erteilt Zugriff auf die Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="a3483-121">On the provider's site, the user signs in and grants access to the tab.</span></span>
6. <span data-ttu-id="a3483-122">Der Anbieter führt den Benutzer zur Umleitungsseite der Registerkarte OAuth 2,0 mit einem Zugriffstoken.</span><span class="sxs-lookup"><span data-stu-id="a3483-122">The provider takes the user to the tab's OAuth 2.0 redirect page with an access token.</span></span>
7. <span data-ttu-id="a3483-123">Auf der Registerkarte wird überprüft `state` , ob der zurückgegebene Wert mit `microsoftTeams.authentication.notifySuccess()`dem zuvor gespeicherten übereinstimmt, `successCallback` und Aufrufe, die wiederum die in Schritt 3 registrierte Funktion aufrufen.</span><span class="sxs-lookup"><span data-stu-id="a3483-123">The tab checks that the returned `state` value matches what was saved earlier, and calls `microsoftTeams.authentication.notifySuccess()`, which in turn calls the `successCallback` function registered in step 3.</span></span>
8. <span data-ttu-id="a3483-124">Das Popupfenster wird von Microsoft Teams geschlossen.</span><span class="sxs-lookup"><span data-stu-id="a3483-124">Teams closes the pop-up window.</span></span>
9. <span data-ttu-id="a3483-125">Auf der Registerkarte wird entweder die Konfigurationsbenutzeroberfläche angezeigt oder der Inhalt der Registerkarten aktualisiert oder neu geladen, je nachdem, von wo aus der Benutzer gestartet hat.</span><span class="sxs-lookup"><span data-stu-id="a3483-125">The tab either displays configuration UI or refreshes or reloads the tabs content, depending on where the user started from.</span></span>

## <a name="treat-tab-context-as-hints"></a><span data-ttu-id="a3483-126">Behandeln des Registerkarten Kontexts als Hinweise</span><span class="sxs-lookup"><span data-stu-id="a3483-126">Treat tab context as hints</span></span>

<span data-ttu-id="a3483-127">Obwohl der Registerkartenkontext nützliche Informationen für den Benutzer bereitstellt, verwenden Sie diese Informationen nicht, um den Benutzer zu authentifizieren, unabhängig davon, ob Sie ihn als URL-Parameter `microsoftTeams.getContext()` zu ihrer Registerkarten-Inhalts-URL oder durch Aufrufen der Funktion im Microsoft Teams-Client-SDK erhalten.</span><span class="sxs-lookup"><span data-stu-id="a3483-127">Although the tab context provides useful information regarding the user, don't use this information to authenticate the user whether you get it as URL parameters to your tab content URL or by calling the `microsoftTeams.getContext()` function in the Microsoft Teams client SDK.</span></span> <span data-ttu-id="a3483-128">Ein böswilliger Akteur könnte Ihre Registerkarteninhalts-URL mit seinen eigenen Parametern aufrufen, und eine Webseite, die Microsoft Teams imitiert, kann die URL Ihres Registerkarteninhalts in einen iframe laden `getContext()` und eigene Daten an die Funktion zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="a3483-128">A malicious actor could invoke your tab content URL with its own parameters, and a web page impersonating Microsoft Teams could load your tab content URL in an iframe and return its own data to the `getContext()` function.</span></span> <span data-ttu-id="a3483-129">Sie sollten die identitätsbezogenen Informationen im Registerkartenkontext lediglich als Hinweise behandeln und diese vor der Verwendung validieren.</span><span class="sxs-lookup"><span data-stu-id="a3483-129">You should treat the identity-related information in the tab context simply as hints and validate them before use.</span></span>

## <a name="samples"></a><span data-ttu-id="a3483-130">Beispiele</span><span class="sxs-lookup"><span data-stu-id="a3483-130">Samples</span></span>

<span data-ttu-id="a3483-131">Beispielcode zum Anzeigen des Registerkarten Authentifizierungsprozesses finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="a3483-131">For sample code showing the tab authentication process see:</span></span>

* [<span data-ttu-id="a3483-132">Beispiel für Microsoft Teams-Registerkarten Authentifizierung (Knoten)</span><span class="sxs-lookup"><span data-stu-id="a3483-132">Microsoft Teams tab authentication sample (Node)</span></span>](https://github.com/OfficeDev/microsoft-teams-sample-complete-node)
* [<span data-ttu-id="a3483-133">Microsoft Teams-Registerkarten Authentifizierung (Beispiel) (C#)</span><span class="sxs-lookup"><span data-stu-id="a3483-133">Microsoft Teams tab authentication sample (C#)</span></span>](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp)

## <a name="more-details"></a><span data-ttu-id="a3483-134">Weitere Details</span><span class="sxs-lookup"><span data-stu-id="a3483-134">More details</span></span>

<span data-ttu-id="a3483-135">Eine ausführliche Implementierungs Exemplarische Vorgehensweise für die Registerkarten Authentifizierung für Azure Active Directory finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="a3483-135">For a detailed implementation walkthrough for tab authentication targeting Azure Active Directory see:</span></span>

* [<span data-ttu-id="a3483-136">Authentifizieren eines Benutzers auf einer Microsoft Teams-Registerkarte</span><span class="sxs-lookup"><span data-stu-id="a3483-136">Authenticate a user in a Microsoft Teams tab</span></span>](~/tabs/how-to/authentication/auth-tab-AAD.md)
* [<span data-ttu-id="a3483-137">Automatische Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="a3483-137">Silent authentication</span></span>](~/tabs/how-to/authentication/auth-silent-AAD.md)