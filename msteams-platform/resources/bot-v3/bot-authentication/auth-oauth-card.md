---
title: Verwenden des Azure bot-Diensts für die Authentifizierung in Microsoft Teams
description: Beschreibt den Azure bot-Dienst OAuthCard und wie er für die Authentifizierung verwendet wird
keywords: Microsoft Teams-Authentifizierung OAuthCard OAuth Card Azure bot Service
ms.openlocfilehash: 0397c45b39470d97c1158b2681462038de618a39
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674388"
---
# <a name="using-azure-bot-service-for-authentication-in-teams"></a><span data-ttu-id="f8db9-104">Verwenden des Azure bot-Diensts für die Authentifizierung in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="f8db9-104">Using Azure Bot Service for Authentication in Teams</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="f8db9-105">Ohne den OAuthCard des Azure bot-Diensts ist es kompliziert, die Authentifizierung in einem bot zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="f8db9-105">Without the Azure Bot Service’s OAuthCard it is complicated to implement authentication in a bot.</span></span> <span data-ttu-id="f8db9-106">Es handelt sich um eine Full-Stack-Herausforderung, die das Erstellen einer Weberfahrung, die Integration mit externen OAuth-Anbietern, die Tokenverwaltung und das Behandeln der richtigen Server-zu-Server-API-Aufrufe zum Sicherstellen des vollständigen Authentifizierungs Flusses umfasst.</span><span class="sxs-lookup"><span data-stu-id="f8db9-106">It is a full-stack challenge that involving building a web experience, integrating with external OAuth providers, token management, and handling the right server-to-server API calls to complete authentication flow securely.</span></span> <span data-ttu-id="f8db9-107">Dies kann zu klobigen Erfahrungen führen, die die Eingabe von "Magic Numbers" erfordern.</span><span class="sxs-lookup"><span data-stu-id="f8db9-107">This can result in clunky experiences requiring the entry of “magic numbers”.</span></span>

<span data-ttu-id="f8db9-108">Mit dem OAuthCard des Azure bot-Diensts ist es für Ihre Teams einfacher, sich bei ihren Benutzern anzumelden und auf externe Datenanbieter zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="f8db9-108">With Azure Bot Service’s OAuthCard, it is easier for your Teams bot to sign in your users and access external data providers.</span></span> <span data-ttu-id="f8db9-109">Unabhängig davon, ob Sie die Authentifizierung bereits implementiert haben und auf eine einfachere Funktion umstellen möchten, oder wenn Sie das erste Mal die Authentifizierung zu Ihrem bot-Dienst hinzufügen möchten, können Sie das OAuthCard vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="f8db9-109">Whether you’ve already implemented auth and you want to switch over to something simpler, or if you are looking to add authentication to your bot service for the first time, the OAuthCard can make it easier.</span></span>

<span data-ttu-id="f8db9-110">In anderen Themen in der [Authentifizierung](~/resources/bot-v3/bot-authentication/auth-flow-bot.md) wird die Authentifizierung ohne Verwendung des OAuthCard beschrieben, wenn Sie also die Authentifizierung in Microsoft Teams genauer verstehen möchten oder eine Situation haben, in der Sie die OAuthCard nicht verwenden können, können Sie sich trotzdem auf diese Themen berufen.</span><span class="sxs-lookup"><span data-stu-id="f8db9-110">Other topics in [Authentication](~/resources/bot-v3/bot-authentication/auth-flow-bot.md) describe authentication without using the OAuthCard, so if you want to understand authentication in Teams more deeply, or have a situation where you can not use the OAuthCard, you can still refer to those topics.</span></span>

## <a name="support-for-the-oauthcard"></a><span data-ttu-id="f8db9-111">Unterstützung für die OAuthCard</span><span class="sxs-lookup"><span data-stu-id="f8db9-111">Support for the OAuthCard</span></span>

<span data-ttu-id="f8db9-112">Es gibt derzeit einige Einschränkungen, wo Sie die OAuthCard verwenden können.</span><span class="sxs-lookup"><span data-stu-id="f8db9-112">There are currently some restrictions to where you can use the OAuthCard.</span></span> <span data-ttu-id="f8db9-113">Zu diesen zählen:</span><span class="sxs-lookup"><span data-stu-id="f8db9-113">These include:</span></span>

* <span data-ttu-id="f8db9-114">Die Karte kann nicht mit [Gastzugriff](/MicrosoftTeams/guest-access) verwendet werden</span><span class="sxs-lookup"><span data-stu-id="f8db9-114">The card will not work with [guest access](/MicrosoftTeams/guest-access)</span></span>
* <span data-ttu-id="f8db9-115">Es kann nicht mit [Microsoft Teams kostenlos](https://products.office.com/microsoft-teams/free) verwendet werden</span><span class="sxs-lookup"><span data-stu-id="f8db9-115">It will not work with [Microsoft Teams free](https://products.office.com/microsoft-teams/free)</span></span>
* <span data-ttu-id="f8db9-116">Sie kann nur für die bot-Authentifizierung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f8db9-116">It can only be used for bot authentication</span></span>
* <span data-ttu-id="f8db9-117">Es funktioniert nur für Bots, die im [Azure bot-Dienst](https://azure.microsoft.com/services/bot-service/) registriert sind.</span><span class="sxs-lookup"><span data-stu-id="f8db9-117">It only works for bots registered in the [Azure Bot Service](https://azure.microsoft.com/services/bot-service/)</span></span>

## <a name="how-does-the-azure-bot-service-help-me-do-authentication"></a><span data-ttu-id="f8db9-118">Wie hilft mir der Azure bot-Dienst bei der Authentifizierung?</span><span class="sxs-lookup"><span data-stu-id="f8db9-118">How does the Azure Bot Service help me do authentication?</span></span>

<span data-ttu-id="f8db9-119">Eine vollständige Dokumentation mit OAuthCard steht im Thema: [Add Authentication to your bot via Azure bot Service](/azure/bot-service/bot-builder-tutorial-authentication?view=azure-bot-service-3.0)zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="f8db9-119">Full documentation using the OAuthCard is available in the topic: [Add authentication to your bot via Azure Bot Service](/azure/bot-service/bot-builder-tutorial-authentication?view=azure-bot-service-3.0).</span></span> <span data-ttu-id="f8db9-120">Beachten Sie, dass dieses Thema in der Azure bot Framework-Dokumentationsgruppe liegt und nicht für Teams spezifisch ist.</span><span class="sxs-lookup"><span data-stu-id="f8db9-120">Note that this topic is in the Azure Bot Framework documentation set, and is not specific to Teams.</span></span>

<span data-ttu-id="f8db9-121">In den folgenden Abschnitten erfahren Sie, wie Sie das OAuthCard in Microsoft Teams verwenden.</span><span class="sxs-lookup"><span data-stu-id="f8db9-121">The following sections tell how to use the OAuthCard in Teams.</span></span>

## <a name="main-benefits-for-teams-developers"></a><span data-ttu-id="f8db9-122">Hauptvorteile für Entwickler von Teams</span><span class="sxs-lookup"><span data-stu-id="f8db9-122">Main benefits for Teams developers</span></span>

<span data-ttu-id="f8db9-123">Das OAuthCard hilft bei der Authentifizierung auf folgende Weise:</span><span class="sxs-lookup"><span data-stu-id="f8db9-123">The OAuthCard helps with authentication in the following ways:</span></span>

* <span data-ttu-id="f8db9-124">Stellt einen Out-of-Box-webbasierten Authentifizierungs Fluss bereit: Sie müssen keine Webseite mehr schreiben und hosten, um an externe Anmeldeinformationen zu verweisen oder eine Umleitung bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="f8db9-124">Provides an out-of-box web-based authentication flow: you no longer have to write and host a web page to direct to external login experiences or provide a redirect.</span></span>
* <span data-ttu-id="f8db9-125">Ist nahtlos für Endbenutzer: führen Sie das vollständige anmeldeerlebnis direkt in Microsoft Teams aus.</span><span class="sxs-lookup"><span data-stu-id="f8db9-125">Is seamless for end users: complete the full sign in experience right within Teams.</span></span>
* <span data-ttu-id="f8db9-126">Enthält einfache Tokenverwaltung: Sie müssen kein Tokenspeicher mehr implementieren – stattdessen übernimmt der bot-Dienst die Token-Zwischenspeicherung und stellt einen sicheren Mechanismus zum Abrufen dieser Token bereit.</span><span class="sxs-lookup"><span data-stu-id="f8db9-126">Includes easy token management: you no longer have to implement a token storage system – instead, the Bot Service takes care of token caching and provides a secure mechanism for fetching those tokens.</span></span>
* <span data-ttu-id="f8db9-127">Wird von Complete SDKs unterstützt: einfach zu integrieren und von Ihrem bot-Dienst zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="f8db9-127">Is supported by complete SDKs: easy to integrate and consume from your bot service.</span></span>
* <span data-ttu-id="f8db9-128">Verfügt über eine Out-of-Box-Unterstützung für viele beliebte OAuth-Anbieter wie Azure AD/MSA, Facebook und Google.</span><span class="sxs-lookup"><span data-stu-id="f8db9-128">Has out-of-box support for many popular OAuth providers, such as Azure AD/MSA, Facebook, and Google.</span></span>

## <a name="when-should-i-implement-my-own-solution"></a><span data-ttu-id="f8db9-129">Wann sollte ich eine eigene Lösung implementieren?</span><span class="sxs-lookup"><span data-stu-id="f8db9-129">When should I implement my own solution?</span></span>

<span data-ttu-id="f8db9-130">Da es sich bei Zugriffstoken um vertrauliche Informationen handelt, möchten Sie möglicherweise nicht, dass Sie in einem externen Dienst gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="f8db9-130">Because access tokens are sensitive information, you may not wish to have them stored in an external service.</span></span> <span data-ttu-id="f8db9-131">In diesem Fall können Sie sich entscheiden, weiterhin Ihr eigenes Token-Verwaltungssystem und ihre Anmelde Erfahrung in Microsoft Teams zu implementieren, wie in den restlichen Teams- [Authentifizierungs](~/resources/bot-v3/bot-authentication/auth-flow-bot.md) Themen beschrieben.</span><span class="sxs-lookup"><span data-stu-id="f8db9-131">In this case, you may choose to still implement your own token management system and login experience within Teams, as described in the rest of the Teams [Authentication](~/resources/bot-v3/bot-authentication/auth-flow-bot.md) topics.</span></span>

## <a name="getting-started-with-oauthcard-in-teams"></a><span data-ttu-id="f8db9-132">Erste Schritte mit OAuthCard in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="f8db9-132">Getting started with OAuthCard in Teams</span></span>

> [!NOTE]
> <span data-ttu-id="f8db9-133">In diesem Leitfaden wird das bot Framework V3 SDK verwendet.</span><span class="sxs-lookup"><span data-stu-id="f8db9-133">This guide is using the Bot Framework v3 SDK.</span></span> <span data-ttu-id="f8db9-134">Sie können die V4-Implementierung [hier](/azure/bot-service/bot-builder-authentication?view=azure-bot-service-4.0&tabs=csharp)finden.</span><span class="sxs-lookup"><span data-stu-id="f8db9-134">You can find the v4 implementation [here](/azure/bot-service/bot-builder-authentication?view=azure-bot-service-4.0&tabs=csharp).</span></span> <span data-ttu-id="f8db9-135">Sie müssen dennoch ein Manifest erstellen und Token.botframework.com in den `validDomains` Abschnitt einbeziehen, da andernfalls die Schaltfläche Anmelden das Authentifizierungsfenster nicht öffnet.</span><span class="sxs-lookup"><span data-stu-id="f8db9-135">You will still need to create a manifest and include token.botframework.com in the `validDomains` section, because otherwise the Sign in button will not open the authentication window.</span></span> <span data-ttu-id="f8db9-136">Verwenden Sie das [App Studio](~/concepts/build-and-test/app-studio-overview.md) , um Ihr Manifest zu generieren.</span><span class="sxs-lookup"><span data-stu-id="f8db9-136">Use the [App Studio](~/concepts/build-and-test/app-studio-overview.md) to generate your manifest.</span></span>

<span data-ttu-id="f8db9-137">Zunächst müssen Sie Ihren Azure bot-Dienst konfigurieren, um externe Authentifizierungsanbieter einzurichten.</span><span class="sxs-lookup"><span data-stu-id="f8db9-137">You’ll first need to configure your Azure bot service to set up external authentication providers.</span></span> <span data-ttu-id="f8db9-138">Lesen Sie [Konfigurieren von Identitätsanbietern](~/concepts/authentication/configure-identity-provider.md) für detaillierte Schritte.</span><span class="sxs-lookup"><span data-stu-id="f8db9-138">Read [Configuring identity providers](~/concepts/authentication/configure-identity-provider.md) for detailed steps.</span></span>

<span data-ttu-id="f8db9-139">Um die Authentifizierung mit dem Azure bot-Dienst zu aktivieren, müssen Sie diese Ergänzungen an Ihrem Code vornehmen:</span><span class="sxs-lookup"><span data-stu-id="f8db9-139">To enable authentication using the Azure Bot Service, you need to make these additions to your code:</span></span>

1. <span data-ttu-id="f8db9-140">Schließen Sie Token.botframework.com in `validDomains` den Abschnitt des App-Manifests ein, da Microsoft Teams die Anmeldeseite des bot-Diensts einbetten wird.</span><span class="sxs-lookup"><span data-stu-id="f8db9-140">Include token.botframework.com in the `validDomains` section of your app manifest because Teams will embed the Bot Service’s login page.</span></span>
2. <span data-ttu-id="f8db9-141">Holen Sie das Token aus dem bot-Dienst, wenn Ihr bot Zugriff auf authentifizierte Ressourcen benötigt.</span><span class="sxs-lookup"><span data-stu-id="f8db9-141">Fetch the token from the Bot Service whenever your bot needs to access authenticated resources.</span></span> <span data-ttu-id="f8db9-142">Wenn kein Token verfügbar ist, senden Sie eine Nachricht mit einem OAuthCard an den Benutzer, der Sie anfordert, sich beim externen Dienst anzumelden.</span><span class="sxs-lookup"><span data-stu-id="f8db9-142">If no token is available, send a message with an OAuthCard to the user requesting them to log into the external service.</span></span>
3. <span data-ttu-id="f8db9-143">Behandeln Sie die Anmelde Abschlussaktivität.</span><span class="sxs-lookup"><span data-stu-id="f8db9-143">Handle the login completion activity.</span></span> <span data-ttu-id="f8db9-144">Dadurch wird sichergestellt, dass die Authentifizierungsanforderung und das Token dem Benutzer zugeordnet sind, der derzeit mit Ihrem bot interagiert.</span><span class="sxs-lookup"><span data-stu-id="f8db9-144">This ensures that the authentication request and the token are associated with the user currently interacting with your bot.</span></span>
4. <span data-ttu-id="f8db9-145">Rufen Sie das Token ab, wenn Ihr bot authentifizierte Aktionen durchführen muss, beispielsweise das Aufrufen externer Rest-APIs.</span><span class="sxs-lookup"><span data-stu-id="f8db9-145">Retrieve the token whenever your bot needs to perform authenticated actions, such as calling external REST APIs.</span></span>

<span data-ttu-id="f8db9-146">In Ihrem Dialogfeldcode müssen Sie diesen Codeausschnitt (C#) hinzufügen, der nach einem vorhandenen Zugriffstoken sucht:</span><span class="sxs-lookup"><span data-stu-id="f8db9-146">In your dialog code, you’ll need to add this snippet (C#), which checks for an existing access token:</span></span>

```CSharp
// First ask Bot Service if it already has a token for this user
var token = await context.GetUserTokenAsync(ConnectionName).ConfigureAwait(false);
if (token != null)
{
    // use the token to do exciting things!
}
else
{
    // If Bot Service does not have a token, send an OAuth card to sign in 
    await SendOAuthCardAsync(context, (Activity)context.Activity);
}
```

<span data-ttu-id="f8db9-147">Wenn kein Zugriffstoken vorhanden ist, sendet Ihr Code dann eine Nachricht mit einem OAuthCard an den Benutzer:</span><span class="sxs-lookup"><span data-stu-id="f8db9-147">If an access token doesn’t exist, your code will then send a message with an OAuthCard to the user:</span></span>

```CSharp
private async Task SendOAuthCardAsync(IDialogContext context, Activity activity)
{
    await context.PostAsync($"To do this, you'll first need to sign in.");

    var reply = await context.Activity.CreateOAuthReplyAsync(_connectionName, _signInMessage, _buttonLabel).ConfigureAwait(false);
    await context.PostAsync(reply);

    context.Wait(WaitForToken);
}
```

<span data-ttu-id="f8db9-148">Um die vollständige Anmeldungs Aktivität zu verarbeiten, müssen Sie diesen Aufruf verarbeiten:</span><span class="sxs-lookup"><span data-stu-id="f8db9-148">To handle the login complete activity, you’ll need to process this Invoke:</span></span>

```CSharp
if (activity.Name == "signin/verifyState")
{
  // We do this so that we can pass handling to the right logic in the dialog. You can
  // set this to be whatever string you want.
  activity.Text = "loginComplete";
  await Conversation.SendAsync(activity, () => new Dialogs.RootDialog());

  return Request.CreateResponse(HttpStatusCode.OK);
}
```

<span data-ttu-id="f8db9-149">Im Dialogfeldcode können Sie das Token dann aus dem bot-Authentifizierungsdienst abrufen:</span><span class="sxs-lookup"><span data-stu-id="f8db9-149">In your dialog code, you can then retrieve the token from the Bot authentication service:</span></span>

```CSharp
if (text.Contains("loginComplete"))
  {
    // Handle login completion event.
    JObject ctx = activity.Value as JObject;

    if (ctx != null)
    {
      string code = ctx["state"].ToString();

      var oauthClient = activity.GetOAuthClient();
      var token = await oauthClient.OAuthApi.GetUserTokenAsync(activity.From.Id, ConnectionName, magicCode: code).ConfigureAwait(false);
      if (token != null)
      {
        // Make whatever API calls here you want
        await context.PostAsync($"Success! You are now signed in.");
      }
    }
  // Need to respond to the Invoke.
  return;
}
```

## <a name="using-oauthcard-with-messaging-extensions"></a><span data-ttu-id="f8db9-150">Verwenden von OAuthCard mit Messaging Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="f8db9-150">Using OAuthCard with messaging extensions</span></span>

<span data-ttu-id="f8db9-151">Sie können auch den Azure bot-Dienst verwenden, um Drittanbieter mit Ihrer Messaging Erweiterung zu verbinden.</span><span class="sxs-lookup"><span data-stu-id="f8db9-151">You can also use Azure Bot Service to connect third-party providers to your messaging extension.</span></span> <span data-ttu-id="f8db9-152">Der Fluss ist identisch mit einem bot, es sei denn, es wird ein OAuthCard zurückgegeben, Ihr Dienst gibt eine Anmeldeaufforderung zurück.</span><span class="sxs-lookup"><span data-stu-id="f8db9-152">The flow is the same as with a bot, except instead of returning an OAuthCard, your service will return a login prompt.</span></span>

<span data-ttu-id="f8db9-153">Der folgende Codeausschnitt (C#) veranschaulicht, wie die Anmelde Antwort erstellt wird:</span><span class="sxs-lookup"><span data-stu-id="f8db9-153">The following snippet (C#) illustrates how to craft the login response:</span></span>

```CSharp
var token = await client.OAuthApi.GetUserTokenAsync(activity.From.Id, ConnectionName).ConfigureAwait(false);

if (token == null)
{
  // Send the login response with the auth link.
  string link = await client.OAuthApi.GetSignInLinkAsync(activity, ConnectionName);

  response = new ComposeExtensionResponse()
  {
    ComposeExtension = new ComposeExtensionResult()
  };
  response.ComposeExtension.Type = "auth";
  response.ComposeExtension.SuggestedActions = new ComposeExtensionSuggestedAction()
  {
    Actions = new List<CardAction>()
      {
        new CardAction(ActionTypes.OpenUrl, title: "Sign into this app", value: link)
      }
    };
  return response;
}
```

<span data-ttu-id="f8db9-154">Beachten Sie, dass Sie im obigen Beispiel den Aufruf direkt für `GetSignInLinkAsync` die `client.OAuthApi` Eigenschaft vornehmen müssen.</span><span class="sxs-lookup"><span data-stu-id="f8db9-154">Note that in the example above you need to make the call to `GetSignInLinkAsync` directly against the `client.OAuthApi` property.</span></span>

<span data-ttu-id="f8db9-155">Wenn der Benutzer die Anmeldesequenz erfolgreich abgeschlossen hat, erhält der Dienst eine weitere Invoke-Anforderung, die die ursprüngliche Benutzerabfrage enthält, zusammen mit einer Statusparameter Zeichenfolge, die den "Magic Code" enthält.</span><span class="sxs-lookup"><span data-stu-id="f8db9-155">When the user successfully completes the login sequence, your service will receive another Invoke request containing the original user query, along with a state parameter string containing the “magic code”.</span></span> <span data-ttu-id="f8db9-156">Sie können nun das Token mit dieser Zeichenfolge zusammen mit der Benutzer-ID und dem Verbindungsnamen abrufen.</span><span class="sxs-lookup"><span data-stu-id="f8db9-156">You can now fetch the token using this string, along with the user ID and connection name.</span></span>

```CSharp
var query = activity.GetComposeExtensionQueryData();
JObject data = activity.Value as JObject;

var client = activity.GetOAuthClient();

// Check if the request comes with login state
if (data != null && data["state"] != null)
{
  var token = await client.OAuthApi.GetUserTokenAsync(activity.From.Id, ConnectionName, data["state"].ToString());

  // Do stuff with the token here.

}
```
