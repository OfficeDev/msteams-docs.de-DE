---
title: Authentifizierung für Bots mit Azure-Active Directory
description: Beschreibt Azure AD Authentifizierung in Microsoft Teams und deren Verwendung in ihren Bots
keywords: Teams Authentication Bots Aad
ms.date: 03/01/2018
ms.openlocfilehash: 268af02c51b21b65214bce4673b54ac564a125ae
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674387"
---
# <a name="authenticate-a-user-in-a-microsoft-teams-bot"></a><span data-ttu-id="e6867-104">Authentifizieren eines Benutzers in einem Microsoft Teams-bot</span><span class="sxs-lookup"><span data-stu-id="e6867-104">Authenticate a user in a Microsoft Teams bot</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="e6867-105">Es gibt viele Dienste, die Sie in Ihrer Teams-App möglicherweise nutzen möchten, und die meisten dieser Dienste erfordern Authentifizierung und Autorisierung, um Zugriff auf den Dienst zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="e6867-105">There are many services that you may wish to consume inside your Teams app, and most of those services require authentication and authorization to get access to the service.</span></span> <span data-ttu-id="e6867-106">Zu den Diensten gehören Facebook, Twitter und natürlich Teams.</span><span class="sxs-lookup"><span data-stu-id="e6867-106">Services include Facebook, Twitter, and of course Teams.</span></span> <span data-ttu-id="e6867-107">Benutzer von Teams haben Benutzerprofilinformationen, die in Azure Active Directory (Azure AD) mit Microsoft Graph gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="e6867-107">Users of Teams have user profile information stored in Azure Active Directory (Azure AD) using Microsoft Graph.</span></span> <span data-ttu-id="e6867-108">Dieser Artikel konzentriert sich auf die Authentifizierung mit Azure AD, um Zugriff auf diese Informationen zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="e6867-108">This article will focus on authentication using Azure AD to get access to this information.</span></span>

<span data-ttu-id="e6867-109">OAuth 2,0 ist ein offener Standard für die Authentifizierung, der von Azure AD und vielen anderen Dienstanbietern verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="e6867-109">OAuth 2.0 is an open standard for authentication used by Azure AD and many other service providers.</span></span> <span data-ttu-id="e6867-110">Das Verständnis von OAuth 2,0 ist eine Voraussetzung für die Verwendung der Authentifizierung in Microsoft Teams und Azure AD.</span><span class="sxs-lookup"><span data-stu-id="e6867-110">Understanding OAuth 2.0 is a prerequisite for working with authentication in Teams and Azure AD.</span></span> <span data-ttu-id="e6867-111">Die folgenden Beispiele verwenden den impliziten Grant-Fluss von OAuth 2,0 mit dem Ziel, die Profilinformationen des Benutzers schließlich aus Azure AD und Microsoft Graph zu lesen.</span><span class="sxs-lookup"><span data-stu-id="e6867-111">The examples below use the OAuth 2.0 Implicit Grant flow with the goal of eventually reading the user's profile information from Azure AD and Microsoft Graph.</span></span>

<span data-ttu-id="e6867-112">Der in diesem Artikel beschriebene Authentifizierungs Fluss ähnelt dem von Tabs, mit der Ausnahme, dass Registerkarten den webbasierten Authentifizierungs Fluss verwenden können, und Bots erfordern, dass die Authentifizierung von Code gesteuert wird.</span><span class="sxs-lookup"><span data-stu-id="e6867-112">The authentication flow described in this article is very similar to that of tabs except that tabs can use web based authentication flow, and bots require authentication to be driven from code.</span></span> <span data-ttu-id="e6867-113">Die Konzepte in diesem Artikel sind auch hilfreich, wenn Sie die Authentifizierung von der mobilen Plattform implementieren.</span><span class="sxs-lookup"><span data-stu-id="e6867-113">The concepts in this article will also be useful when implementing authentication from the mobile platform.</span></span>

<span data-ttu-id="e6867-114">Eine allgemeine Übersicht über den Authentifizierungsablauf für Bots finden Sie im Thema [Authentifizierungs Fluss in Bots](~/resources/bot-v3/bot-authentication/auth-flow-bot.md).</span><span class="sxs-lookup"><span data-stu-id="e6867-114">For a general overview of authentication flow for bots see the topic [Authentication flow in bots](~/resources/bot-v3/bot-authentication/auth-flow-bot.md).</span></span>

## <a name="configuring-identity-providers"></a><span data-ttu-id="e6867-115">Konfigurieren von Identitätsanbietern</span><span class="sxs-lookup"><span data-stu-id="e6867-115">Configuring identity providers</span></span>

<span data-ttu-id="e6867-116">Lesen Sie das Thema [configure Identity Providers](~/concepts/authentication/configure-identity-provider.md) for ausführliche steps on Configuring OAuth 2,0 Callback Redirect URL (s) bei Verwendung von Azure Active Directory als Identitätsanbieter.</span><span class="sxs-lookup"><span data-stu-id="e6867-116">See the topic [Configure identity providers](~/concepts/authentication/configure-identity-provider.md) for detailed steps on configuring OAuth 2.0 callback redirect URL(s) when using Azure Active Directory as an identity provider.</span></span>

## <a name="initiate-authentication-flow"></a><span data-ttu-id="e6867-117">Initiieren des Authentifizierungs Flusses</span><span class="sxs-lookup"><span data-stu-id="e6867-117">Initiate authentication flow</span></span>

<span data-ttu-id="e6867-118">Der Authentifizierungs Fluss sollte durch eine Benutzeraktion ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="e6867-118">Authentication flow should be triggered by a user action.</span></span> <span data-ttu-id="e6867-119">Sie sollten das Authentifizierungs Popup nicht automatisch öffnen, da dies wahrscheinlich den Popupblocker des Browsers auslösen und den Benutzer verwirren kann.</span><span class="sxs-lookup"><span data-stu-id="e6867-119">You should not open the authentication pop-up automatically because this is likely to trigger the browser's pop-up blocker as well as confuse the user.</span></span>

## <a name="add-ui-to-start-authentication"></a><span data-ttu-id="e6867-120">Hinzufügen einer Benutzeroberfläche zum Starten der Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="e6867-120">Add UI to start authentication</span></span>

<span data-ttu-id="e6867-121">Fügen Sie der bot-Benutzeroberfläche hinzu, um dem Benutzer die Anmeldung bei Bedarf zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="e6867-121">Add UI to the bot to enable the user to sign in when needed.</span></span> <span data-ttu-id="e6867-122">Hier erfolgt die Arbeit über eine Miniatur Ansichtskarte in einer Fingerabdruck Ansicht:</span><span class="sxs-lookup"><span data-stu-id="e6867-122">Here it is done from a Thumbnail card, in TypeScript:</span></span>

```typescript
// Show prompt of options
protected async promptForAction(session: builder.Session): Promise<void> {
    let msg = new builder.Message(session)
        .addAttachment(new builder.ThumbnailCard(session)
            .title(this.providerDisplayName)
            .buttons([
                 builder.CardAction.messageBack(session, "{}", "Sign in")
                     .text("SignIn")
                     .displayText("Sign in"),
                  builder.CardAction.messageBack(session, "{}", "Show profile")
                     .text("ShowProfile")
                     .displayText("Show profile"),
                  builder.CardAction.messageBack(session, "{}", "Sign out")
                     .text("SignOut")
                     .displayText("Sign out"),
            ]));
    session.send(msg);
}
```

<span data-ttu-id="e6867-123">Der Hero Card wurden drei Schaltflächen hinzugefügt: anmelden, Profil anzeigen und abmelden.</span><span class="sxs-lookup"><span data-stu-id="e6867-123">Three buttons have been added to the Hero Card: Sign in, Show Profile, and Sign out.</span></span>

## <a name="sign-the-user-in"></a><span data-ttu-id="e6867-124">Signieren des Benutzers in</span><span class="sxs-lookup"><span data-stu-id="e6867-124">Sign the user in</span></span>

<span data-ttu-id="e6867-125">Aufgrund der Überprüfung, die aus Sicherheitsgründen ausgeführt werden muss, und der Unterstützung für die mobilen Versionen von Teams wird der Code hier nicht gezeigt, aber [hier sehen Sie ein Beispiel für den Code, der den Prozess startet, wenn der Benutzer auf die Schaltfläche Anmelden klickt.](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/e84020562d7c8b83f4a357a4a4d91298c5d2989d/src/dialogs/BaseIdentityDialog.ts#L154-L195).</span><span class="sxs-lookup"><span data-stu-id="e6867-125">Because of the validation that must be performed for security reasons and the support for the mobile versions of Teams, the code isn't shown here, but [here's an example of the code that kicks off the process when the user presses the Sign in button.](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/e84020562d7c8b83f4a357a4a4d91298c5d2989d/src/dialogs/BaseIdentityDialog.ts#L154-L195).</span></span>

<span data-ttu-id="e6867-126">Die Überprüfung und Mobile Unterstützung werden im Thema [Authentifizierungs Fluss in Bots](~/resources/bot-v3/bot-authentication/auth-flow-bot.md)erläutert.</span><span class="sxs-lookup"><span data-stu-id="e6867-126">The validation and mobile support are explained in the topic [Authentication flow in bots](~/resources/bot-v3/bot-authentication/auth-flow-bot.md).</span></span>

<span data-ttu-id="e6867-127">Stellen Sie sicher, dass Sie die Domäne ihrer Authentifizierungs Umleitungs-URL dem [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) Abschnitt des Manifests hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="e6867-127">Be sure to add the domain of your authentication redirect URL to the [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) section of the manifest.</span></span> <span data-ttu-id="e6867-128">Wenn dies nicht der Fall ist, wird das Anmeldefenster nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e6867-128">If you don't, the login popup will not appear.</span></span>

## <a name="showing-user-profile-information"></a><span data-ttu-id="e6867-129">Anzeigen von Benutzerprofilinformationen</span><span class="sxs-lookup"><span data-stu-id="e6867-129">Showing user profile information</span></span>

<span data-ttu-id="e6867-130">Obwohl das Abrufen eines Zugriffstokens aufgrund aller Übergänge zwischen verschiedenen Websites und der Sicherheitsprobleme, die behoben werden müssen, schwierig ist, wenn Sie über ein Token verfügen, ist das Abrufen von Informationen aus Azure Active Directory einfach.</span><span class="sxs-lookup"><span data-stu-id="e6867-130">Although getting an access token is difficult because of all the transitions back and forth across different websites and the security issues that must be addressed, once you have a token, obtaining information from Azure Active Directory is straightforward.</span></span> <span data-ttu-id="e6867-131">Der bot führt einen Aufruf des `me` Graph-Endpunkts mit dem Zugriffstoken aus.</span><span class="sxs-lookup"><span data-stu-id="e6867-131">The bot makes a call to the `me` Graph endpoint with the access token.</span></span> <span data-ttu-id="e6867-132">Graph antwortet mit den Benutzerinformationen für die Person, die sich angemeldet hat.</span><span class="sxs-lookup"><span data-stu-id="e6867-132">Graph responds with the user information for the person who logged in.</span></span> <span data-ttu-id="e6867-133">Informationen aus der Antwort werden verwendet, um eine bot-Karte zu erstellen und zu senden.</span><span class="sxs-lookup"><span data-stu-id="e6867-133">Information from the response is used to construct a bot card and sent.</span></span>

```typescript
// Show user profile
protected async showUserProfile(session: builder.Session): Promise<void> {
    let azureADApi = this.authProvider as AzureADv1Provider;
    let userToken = this.getUserToken(session);

    if (userToken) {
        let profile = await azureADApi.getProfileAsync(userToken.accessToken);
        let profileCard = new builder.ThumbnailCard()
            .title(profile.displayName)
            .subtitle(profile.mail)
            .text(`${profile.jobTitle}<br/> ${profile.officeLocation}`);
        session.send(new builder.Message().addAttachment(profileCard));
    } else {
        session.send("Please sign in to AzureAD so I can access your profile.");
    }

    await this.promptForAction(session);
}

// Helper function to make the Graph API call
public async getProfileAsync(accessToken: string): Promise<any> {
    let options = {
        url: "https://graph.microsoft.com/v1.0/me",
        json: true,
        headers: {
            "Authorization": `Bearer ${accessToken}`,
        },
    };
    return await request.get(options);
}
```

<span data-ttu-id="e6867-134">Wenn der Benutzer nicht angemeldet ist, werden Sie dazu aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="e6867-134">If the user is not signed in they are prompted to do so.</span></span>

## <a name="sign-the-user-out"></a><span data-ttu-id="e6867-135">Den Benutzer abmelden</span><span class="sxs-lookup"><span data-stu-id="e6867-135">Sign the user out</span></span>

```typescript
// Handle user logout request
private async handleLogout(session: builder.Session): Promise<void> {
    if (!utils.getUserToken(session, this.providerName)) {
        session.send(`You're already signed out of ${this.providerDisplayName}.`);
    } else {
        utils.setUserToken(session, this.providerName, null);
        session.send(`You're now signed out of ${this.providerDisplayName}.`);
    }

    await this.promptForAction(session);
}
```

## <a name="other-samples"></a><span data-ttu-id="e6867-136">Weitere Beispiele</span><span class="sxs-lookup"><span data-stu-id="e6867-136">Other samples</span></span>

<span data-ttu-id="e6867-137">Beispielcode zum Anzeigen des bot-Authentifizierungsprozesses finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="e6867-137">For sample code showing the bot authentication process see:</span></span>

* [<span data-ttu-id="e6867-138">Beispiel für Microsoft Teams-bot-Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="e6867-138">Microsoft Teams bot authentication sample</span></span>](https://github.com/OfficeDev/microsoft-teams-sample-auth-node)
