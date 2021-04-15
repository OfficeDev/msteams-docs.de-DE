---
title: Verwenden von Azure Bot Service für die Authentifizierung in Teams
description: Beschreibt den Azure Bot Service OAuthCard und seine Verwendung für die Authentifizierung
ms.topic: conceptual
keywords: Teams-Authentifizierung OAuthCard OAuth Card Azure Bot Service
ms.openlocfilehash: 6e609daba1374f4e971e1634810d3b217ce55371
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696675"
---
# <a name="using-azure-bot-service-for-authentication-in-teams"></a><span data-ttu-id="9fa2e-104">Verwenden von Azure Bot Service für die Authentifizierung in Teams</span><span class="sxs-lookup"><span data-stu-id="9fa2e-104">Using Azure Bot Service for Authentication in Teams</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="9fa2e-105">Ohne die OAuthCard des Azure Bot Service ist es kompliziert, die Authentifizierung in einem Bot zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-105">Without the Azure Bot Service’s OAuthCard it is complicated to implement authentication in a bot.</span></span> <span data-ttu-id="9fa2e-106">Es handelt sich um eine Herausforderung mit vollem Stapel, die das Erstellen einer Weberfahrung, die Integration mit externen OAuth-Anbietern, die Tokenverwaltung und die Verarbeitung der richtigen Server-zu-Server-API-Aufrufe zum sicheren Abschließen des Authentifizierungsflusses erfordert.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-106">It is a full-stack challenge that involving building a web experience, integrating with external OAuth providers, token management, and handling the right server-to-server API calls to complete authentication flow securely.</span></span> <span data-ttu-id="9fa2e-107">Dies kann zu unübersichtlichen Erfahrungen führen, bei denen die Eingabe von "magischen Zahlen" erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-107">This can result in clunky experiences requiring the entry of “magic numbers”.</span></span>

<span data-ttu-id="9fa2e-108">Mit der OAuthCard von Azure Bot Service ist es für Ihren Teams-Bot einfacher, sich bei Ihren Benutzern zu registrieren und auf externe Datenanbieter zu zugreifen.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-108">With Azure Bot Service’s OAuthCard, it is easier for your Teams bot to sign in your users and access external data providers.</span></span> <span data-ttu-id="9fa2e-109">Unabhängig davon, ob Sie die Authentifizierung bereits implementiert haben und zu einer einfacheren Lösung wechseln möchten oder wenn Sie ihren Botdienst zum ersten Mal Authentifizierung hinzufügen möchten, kann die OAuthCard dies vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-109">Whether you’ve already implemented auth and you want to switch over to something simpler, or if you are looking to add authentication to your bot service for the first time, the OAuthCard can make it easier.</span></span>

<span data-ttu-id="9fa2e-110">In anderen Themen in [der](~/resources/bot-v3/bot-authentication/auth-flow-bot.md) Authentifizierung wird die Authentifizierung ohne OAuthCard beschrieben. Wenn Sie also die Authentifizierung in Teams genauer verstehen möchten oder die OAuthCard nicht verwenden können, können Sie sich weiterhin auf diese Themen beziehen.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-110">Other topics in [Authentication](~/resources/bot-v3/bot-authentication/auth-flow-bot.md) describe authentication without using the OAuthCard, so if you want to understand authentication in Teams more deeply, or have a situation where you can not use the OAuthCard, you can still refer to those topics.</span></span>

## <a name="support-for-the-oauthcard"></a><span data-ttu-id="9fa2e-111">Unterstützung für OAuthCard</span><span class="sxs-lookup"><span data-stu-id="9fa2e-111">Support for the OAuthCard</span></span>

<span data-ttu-id="9fa2e-112">Es gibt derzeit einige Einschränkungen, wo Sie OAuthCard verwenden können.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-112">There are currently some restrictions to where you can use the OAuthCard.</span></span> <span data-ttu-id="9fa2e-113">Zu diesen zählen:</span><span class="sxs-lookup"><span data-stu-id="9fa2e-113">These include:</span></span>

* <span data-ttu-id="9fa2e-114">Die Karte funktioniert nicht mit [gastzugriff](/MicrosoftTeams/guest-access)</span><span class="sxs-lookup"><span data-stu-id="9fa2e-114">The card will not work with [guest access](/MicrosoftTeams/guest-access)</span></span>
* <span data-ttu-id="9fa2e-115">Es funktioniert nicht kostenlos [mit Microsoft Teams](https://products.office.com/microsoft-teams/free)</span><span class="sxs-lookup"><span data-stu-id="9fa2e-115">It will not work with [Microsoft Teams free](https://products.office.com/microsoft-teams/free)</span></span>
* <span data-ttu-id="9fa2e-116">Es kann nur für die Botauthentifizierung verwendet werden</span><span class="sxs-lookup"><span data-stu-id="9fa2e-116">It can only be used for bot authentication</span></span>
* <span data-ttu-id="9fa2e-117">Es funktioniert nur für Bots, die im [Azure Bot Service registriert sind.](https://azure.microsoft.com/services/bot-service/)</span><span class="sxs-lookup"><span data-stu-id="9fa2e-117">It only works for bots registered in the [Azure Bot Service](https://azure.microsoft.com/services/bot-service/)</span></span>

## <a name="how-does-the-azure-bot-service-help-me-do-authentication"></a><span data-ttu-id="9fa2e-118">Wie hilft mir der Azure Bot Service bei der Authentifizierung?</span><span class="sxs-lookup"><span data-stu-id="9fa2e-118">How does the Azure Bot Service help me do authentication?</span></span>

<span data-ttu-id="9fa2e-119">Vollständige Dokumentation mit der OAuthCard finden Sie im Thema: Hinzufügen der Authentifizierung [zu Ihrem Bot über Azure Bot Service](/azure/bot-service/bot-builder-tutorial-authentication?view=azure-bot-service-3.0&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="9fa2e-119">Full documentation using the OAuthCard is available in the topic: [Add authentication to your bot via Azure Bot Service](/azure/bot-service/bot-builder-tutorial-authentication?view=azure-bot-service-3.0&preserve-view=true).</span></span> <span data-ttu-id="9fa2e-120">Beachten Sie, dass sich dieses Thema im Azure Bot Framework-Dokumentationssatz befindet und nicht für Teams spezifisch ist.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-120">Note that this topic is in the Azure Bot Framework documentation set, and is not specific to Teams.</span></span>

<span data-ttu-id="9fa2e-121">In den folgenden Abschnitten wird die Verwendung der OAuthCard in Teams erläutert.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-121">The following sections tell how to use the OAuthCard in Teams.</span></span>

## <a name="main-benefits-for-teams-developers"></a><span data-ttu-id="9fa2e-122">Hauptvorteile für Teams-Entwickler</span><span class="sxs-lookup"><span data-stu-id="9fa2e-122">Main benefits for Teams developers</span></span>

<span data-ttu-id="9fa2e-123">Die OAuthCard hilft bei der Authentifizierung auf folgende Weise:</span><span class="sxs-lookup"><span data-stu-id="9fa2e-123">The OAuthCard helps with authentication in the following ways:</span></span>

* <span data-ttu-id="9fa2e-124">Stellt einen standardbasierten webbasierten Authentifizierungsfluss zur Verfügung: Sie müssen keine Webseite mehr schreiben und hosten, um an externe Anmeldeerfahrungen zu leiten oder eine Umleitung bereitstellen zu können.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-124">Provides an out-of-box web-based authentication flow: you no longer have to write and host a web page to direct to external login experiences or provide a redirect.</span></span>
* <span data-ttu-id="9fa2e-125">Ist nahtlos für Endbenutzer: Füllen Sie die vollständige Anmeldeerfahrung direkt in Teams aus.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-125">Is seamless for end users: complete the full sign in experience right within Teams.</span></span>
* <span data-ttu-id="9fa2e-126">Umfasst eine einfache Tokenverwaltung: Sie müssen kein Tokenspeichersystem mehr implementieren– stattdessen übernimmt der Bot-Dienst die Zwischenspeicherung von Token und stellt einen sicheren Mechanismus zum Abrufen dieser Token zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-126">Includes easy token management: you no longer have to implement a token storage system – instead, the Bot Service takes care of token caching and provides a secure mechanism for fetching those tokens.</span></span>
* <span data-ttu-id="9fa2e-127">Wird von vollständigen SDKs unterstützt: einfach zu integrieren und von Ihrem Botdienst zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-127">Is supported by complete SDKs: easy to integrate and consume from your bot service.</span></span>
* <span data-ttu-id="9fa2e-128">Verfügt über eine out-of-box-Unterstützung für viele beliebte OAuth-Anbieter, z. B. Azure AD/MSA, Facebook und Google.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-128">Has out-of-box support for many popular OAuth providers, such as Azure AD/MSA, Facebook, and Google.</span></span>

## <a name="when-should-i-implement-my-own-solution"></a><span data-ttu-id="9fa2e-129">Wann sollte ich meine eigene Lösung implementieren?</span><span class="sxs-lookup"><span data-stu-id="9fa2e-129">When should I implement my own solution?</span></span>

<span data-ttu-id="9fa2e-130">Da Zugriffstoken vertrauliche Informationen sind, möchten Sie sie möglicherweise nicht in einem externen Dienst speichern lassen.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-130">Because access tokens are sensitive information, you may not wish to have them stored in an external service.</span></span> <span data-ttu-id="9fa2e-131">In diesem Fall können Sie ihr eigenes Tokenverwaltungssystem und die Anmeldeerfahrung weiterhin in Teams implementieren, wie in den restlichen [Teams-Authentifizierungsthemen](~/resources/bot-v3/bot-authentication/auth-flow-bot.md) beschrieben.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-131">In this case, you may choose to still implement your own token management system and login experience within Teams, as described in the rest of the Teams [Authentication](~/resources/bot-v3/bot-authentication/auth-flow-bot.md) topics.</span></span>

## <a name="getting-started-with-oauthcard-in-teams"></a><span data-ttu-id="9fa2e-132">Erste Schritte mit OAuthCard in Teams</span><span class="sxs-lookup"><span data-stu-id="9fa2e-132">Getting started with OAuthCard in Teams</span></span>

> [!NOTE]
> <span data-ttu-id="9fa2e-133">In diesem Handbuch wird das Bot Framework v3 SDK verwendet.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-133">This guide is using the Bot Framework v3 SDK.</span></span> <span data-ttu-id="9fa2e-134">Die v4-Implementierung finden Sie [hier](/azure/bot-service/bot-builder-authentication?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="9fa2e-134">You can find the v4 implementation [here](/azure/bot-service/bot-builder-authentication?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true).</span></span> <span data-ttu-id="9fa2e-135">Sie müssen weiterhin ein Manifest erstellen und token.botframework.com in den Abschnitt hinzufügen, da andernfalls das Authentifizierungsfenster nicht mit der Schaltfläche Anmelden `validDomains` geöffnet wird.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-135">You will still need to create a manifest and include token.botframework.com in the `validDomains` section, because otherwise the Sign in button will not open the authentication window.</span></span> <span data-ttu-id="9fa2e-136">Verwenden Sie [das App Studio,](~/concepts/build-and-test/app-studio-overview.md) um Ihr Manifest zu generieren.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-136">Use the [App Studio](~/concepts/build-and-test/app-studio-overview.md) to generate your manifest.</span></span>

<span data-ttu-id="9fa2e-137">Sie müssen zunächst Ihren Azure-Botdienst konfigurieren, um externe Authentifizierungsanbieter einrichten zu können.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-137">You’ll first need to configure your Azure bot service to set up external authentication providers.</span></span> <span data-ttu-id="9fa2e-138">Ausführliche [Schritte finden Sie unter](~/concepts/authentication/configure-identity-provider.md) Konfigurieren von Identitätsanbietern.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-138">Read [Configuring identity providers](~/concepts/authentication/configure-identity-provider.md) for detailed steps.</span></span>

<span data-ttu-id="9fa2e-139">Um die Authentifizierung mithilfe des Azure Bot Service zu aktivieren, müssen Sie die folgenden Ergänzungen zu Ihrem Code erstellen:</span><span class="sxs-lookup"><span data-stu-id="9fa2e-139">To enable authentication using the Azure Bot Service, you need to make these additions to your code:</span></span>

1. <span data-ttu-id="9fa2e-140">Schließen token.botframework.com in den Abschnitt Ihres App-Manifests ein, da Teams die Anmeldeseite des `validDomains` Botdiensts einbetten wird.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-140">Include token.botframework.com in the `validDomains` section of your app manifest because Teams will embed the Bot Service’s login page.</span></span>
2. <span data-ttu-id="9fa2e-141">Rufen Sie das Token aus dem Botdienst ab, wenn Ihr Bot auf authentifizierte Ressourcen zugreifen muss.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-141">Fetch the token from the Bot Service whenever your bot needs to access authenticated resources.</span></span> <span data-ttu-id="9fa2e-142">Wenn kein Token verfügbar ist, senden Sie eine Nachricht mit einer OAuthCard an den Benutzer, der ihn anfordert, sich beim externen Dienst zu melden.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-142">If no token is available, send a message with an OAuthCard to the user requesting them to log into the external service.</span></span>
3. <span data-ttu-id="9fa2e-143">Behandeln Sie die Anmeldeabschlussaktivität.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-143">Handle the login completion activity.</span></span> <span data-ttu-id="9fa2e-144">Dadurch wird sichergestellt, dass die Authentifizierungsanforderung und das Token dem Benutzer zugeordnet sind, der derzeit mit Ihrem Bot interagiert.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-144">This ensures that the authentication request and the token are associated with the user currently interacting with your bot.</span></span>
4. <span data-ttu-id="9fa2e-145">Rufen Sie das Token ab, wenn Ihr Bot authentifizierte Aktionen ausführen muss, z. B. das Aufrufen externer REST-APIs.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-145">Retrieve the token whenever your bot needs to perform authenticated actions, such as calling external REST APIs.</span></span>

<span data-ttu-id="9fa2e-146">Im Dialogfeldcode müssen Sie diesen Codeausschnitt (C#) hinzufügen, der nach einem vorhandenen Zugriffstoken sucht:</span><span class="sxs-lookup"><span data-stu-id="9fa2e-146">In your dialog code, you’ll need to add this snippet (C#), which checks for an existing access token:</span></span>

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

<span data-ttu-id="9fa2e-147">Wenn kein Zugriffstoken vorhanden ist, sendet Ihr Code eine Nachricht mit einer OAuthCard an den Benutzer:</span><span class="sxs-lookup"><span data-stu-id="9fa2e-147">If an access token doesn’t exist, your code will then send a message with an OAuthCard to the user:</span></span>

```CSharp
private async Task SendOAuthCardAsync(IDialogContext context, Activity activity)
{
    await context.PostAsync($"To do this, you'll first need to sign in.");

    var reply = await context.Activity.CreateOAuthReplyAsync(_connectionName, _signInMessage, _buttonLabel).ConfigureAwait(false);
    await context.PostAsync(reply);

    context.Wait(WaitForToken);
}
```

<span data-ttu-id="9fa2e-148">Zum Verarbeiten der vollständigen Anmeldeaktivität müssen Sie diesen Aufruf verarbeiten:</span><span class="sxs-lookup"><span data-stu-id="9fa2e-148">To handle the login complete activity, you’ll need to process this Invoke:</span></span>

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

<span data-ttu-id="9fa2e-149">In Ihrem Dialogfeldcode können Sie das Token dann vom Bot-Authentifizierungsdienst abrufen:</span><span class="sxs-lookup"><span data-stu-id="9fa2e-149">In your dialog code, you can then retrieve the token from the Bot authentication service:</span></span>

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

## <a name="using-oauthcard-with-messaging-extensions"></a><span data-ttu-id="9fa2e-150">Verwenden von OAuthCard mit Messagingerweiterungen</span><span class="sxs-lookup"><span data-stu-id="9fa2e-150">Using OAuthCard with messaging extensions</span></span>

<span data-ttu-id="9fa2e-151">Sie können azure bot Service auch verwenden, um Drittanbieter mit Ihrer Messagingerweiterung zu verbinden.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-151">You can also use Azure Bot Service to connect third-party providers to your messaging extension.</span></span> <span data-ttu-id="9fa2e-152">Der Fluss ist mit einem Bot identisch, außer anstatt eine OAuthCard zurück zu geben, gibt Ihr Dienst eine Anmeldeaufforderung zurück.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-152">The flow is the same as with a bot, except instead of returning an OAuthCard, your service will return a login prompt.</span></span>

<span data-ttu-id="9fa2e-153">Der folgende Codeausschnitt (C#) veranschaulicht das Erstellen der Anmeldeantwort:</span><span class="sxs-lookup"><span data-stu-id="9fa2e-153">The following snippet (C#) illustrates how to craft the login response:</span></span>

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

<span data-ttu-id="9fa2e-154">Beachten Sie, dass Sie im obigen Beispiel den Aufruf direkt `GetSignInLinkAsync` für die Eigenschaft erstellen `client.OAuthApi` müssen.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-154">Note that in the example above you need to make the call to `GetSignInLinkAsync` directly against the `client.OAuthApi` property.</span></span>

<span data-ttu-id="9fa2e-155">Wenn der Benutzer die Anmeldesequenz erfolgreich abgeschlossen hat, erhält Ihr Dienst eine weitere Invoke-Anforderung, die die ursprüngliche Benutzerabfrage enthält, sowie eine State-Parameterzeichenfolge, die den "magischen Code" enthält.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-155">When the user successfully completes the login sequence, your service will receive another Invoke request containing the original user query, along with a state parameter string containing the “magic code”.</span></span> <span data-ttu-id="9fa2e-156">Sie können nun das Token mit dieser Zeichenfolge zusammen mit der Benutzer-ID und dem Verbindungsnamen abrufen.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-156">You can now fetch the token using this string, along with the user ID and connection name.</span></span>

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
