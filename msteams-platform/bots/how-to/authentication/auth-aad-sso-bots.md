---
title: Unterstützung für einmaliges Anmelden für Bots
description: Beschreibt, wie ein Benutzertoken abgerufen wird. Derzeit kann ein bot-Entwickler eine Anmeldekarte oder den Azure bot-Dienst mit der OAuth-Kartenunterstützung verwenden.
keywords: Token, Benutzertoken, SSO-Unterstützung für Bots
ms.openlocfilehash: f2f04cefdea874c42961404339f54b8eb581c7ee
ms.sourcegitcommit: aca9990e1f84b07b9e77c08bfeca4440eb4e64f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "49409099"
---
# <a name="single-sign-on-sso-support-for-bots"></a><span data-ttu-id="47605-105">Unterstützung für einmaliges Anmelden (SSO) für Bots</span><span class="sxs-lookup"><span data-stu-id="47605-105">Single sign-on (SSO) support for bots</span></span>

<span data-ttu-id="47605-106">Authentifizierung mit einmaligem Anmelden in Azure Active Directory (Azure AD) minimiert, wie oft Benutzer ihre Anmeldeinformationen eingeben müssen, indem Sie das Authentifizierungstoken automatisch aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="47605-106">Single sign-on authentication in Azure Active Directory (Azure AD) minimizes the number of times users need to enter their login credentials by silently refreshing the authentication token.</span></span> <span data-ttu-id="47605-107">Wenn Benutzer einwilligen, Ihre APP zu verwenden, müssen Sie nicht erneut auf einem anderen Gerät zustimmen und werden automatisch angemeldet.</span><span class="sxs-lookup"><span data-stu-id="47605-107">If users agrees to use your app, they will not have to consent again on another device and will be signed in automatically.</span></span> <span data-ttu-id="47605-108">Der Fluss ähnelt der [SSO-Unterstützung der Teams-Registerkarte]( ../../../tabs/how-to/authentication/auth-aad-sso.md).</span><span class="sxs-lookup"><span data-stu-id="47605-108">The flow is very similar to the [Teams tab SSO support]( ../../../tabs/how-to/authentication/auth-aad-sso.md).</span></span> <span data-ttu-id="47605-109">Der Unterschied ist das Protokoll dafür, wie ein bot Token anfordert und Antworten erhält.</span><span class="sxs-lookup"><span data-stu-id="47605-109">The difference is the protocol for how a bot requests tokens and receives responses.</span></span>

<span data-ttu-id="47605-110">OAuth 2.0 ist ein offener Standard für Authentifizierung und Autorisierung, der von Azure Active Directory (Azure AD) und vielen anderen Identitätsanbietern verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="47605-110">OAuth 2.0 is an open standard for authentication and authorization used by Azure Active Directory (Azure AD) and many other identity providers.</span></span> <span data-ttu-id="47605-111">Ein grundlegendes Verständnis von OAuth 2,0 ist eine Voraussetzung für die Verwendung von Authentifizierung in Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="47605-111">A basic understanding of OAuth 2.0 is a prerequisite for working with authentication in Teams.</span></span>

## <a name="bot-sso-at-runtime"></a><span data-ttu-id="47605-112">Bot-SSO zur Laufzeit</span><span class="sxs-lookup"><span data-stu-id="47605-112">Bot SSO at runtime</span></span>

![Bot-SSO im laufzeitdiagramm](../../../assets/images/bots/bots-sso-diagram.png)

1. <span data-ttu-id="47605-114">Der bot sendet eine Nachricht mit einem OAuthCard, das die `tokenExchangeResource` Eigenschaft enthält.</span><span class="sxs-lookup"><span data-stu-id="47605-114">The bot sends a message with an OAuthCard that contains the `tokenExchangeResource` property.</span></span> <span data-ttu-id="47605-115">Es weist Microsoft Teams an, ein Authentifizierungstoken für die bot-Anwendung zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="47605-115">It tells Teams to obtain an authentication token for the bot application.</span></span> <span data-ttu-id="47605-116">Der Benutzer empfängt Nachrichten an allen aktiven Endpunkten des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="47605-116">The user receives messages at all the active endpoints of the user.</span></span>

> [!NOTE]
>* <span data-ttu-id="47605-117">Ein Benutzer kann gleichzeitig mehr als einen aktiven Endpunkt aufweisen.</span><span class="sxs-lookup"><span data-stu-id="47605-117">A user can have more than one active endpoint at a time.</span></span>  
>* <span data-ttu-id="47605-118">Das bot-Token wird von jedem aktiven Endpunkt des Benutzers empfangen.</span><span class="sxs-lookup"><span data-stu-id="47605-118">The bot token is received from every active endpoint of the user.</span></span>
>* <span data-ttu-id="47605-119">Die Unterstützung für einmaliges Anmelden erfordert derzeit, dass die APP im persönlichen Bereich installiert wird.</span><span class="sxs-lookup"><span data-stu-id="47605-119">Single sign-on support currently requires the app to be installed in personal scope.</span></span>

2. <span data-ttu-id="47605-120">Wenn der aktuelle Benutzer ihre bot-Anwendung zum ersten Mal verwendet hat, wird eine Anforderungs Aufforderung zur Zustimmung (sofern Zustimmung erforderlich ist) oder zur Behandlung der Step-up-Authentifizierung (beispielsweise zweistufige Authentifizierung) angezeigt.</span><span class="sxs-lookup"><span data-stu-id="47605-120">If it is the first time the current user has used your bot application, there will be a request prompt to consent (if consent is required) or to handle step-up authentication (such as two-factor authentication).</span></span>

3. <span data-ttu-id="47605-121">Microsoft Teams fordert das bot-Anwendungs Token vom Azure AD-Endpunkt für den aktuellen Benutzer an.</span><span class="sxs-lookup"><span data-stu-id="47605-121">Microsoft Teams requests the bot application token from the Azure AD endpoint for the current user.</span></span>

4. <span data-ttu-id="47605-122">Azure AD sendet das bot-Anwendungs Token an die Teams-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="47605-122">Azure AD sends the bot application token to the Teams application.</span></span>

5. <span data-ttu-id="47605-123">Microsoft Teams sendet das Token an den bot als Teil des Value-Objekts, das von der Invoke-Aktivität mit dem Namen Sign-in/tokenExchange zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="47605-123">Microsoft Teams sends the token to the bot as part of the value object returned by the invoke activity with the name sign-in/tokenExchange.</span></span>
  
6. <span data-ttu-id="47605-124">Das Token wird in der bot-Anwendung analysiert, um die erforderlichen Informationen zu extrahieren, beispielsweise die e-Mail-Adresse des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="47605-124">The token will be parsed in the bot application to extract the needed information, such as the user's email address.</span></span>
  
## <a name="develop-a-single-sign-on-microsoft-teams-bot"></a><span data-ttu-id="47605-125">Entwickeln eines Single Sign-on Microsoft Teams-bot</span><span class="sxs-lookup"><span data-stu-id="47605-125">Develop a Single sign-on Microsoft Teams bot</span></span>
  
<span data-ttu-id="47605-126">Die folgenden Schritte sind erforderlich, um einen SSO-Microsoft Teams-bot zu entwickeln:</span><span class="sxs-lookup"><span data-stu-id="47605-126">The following steps: are required to develop an SSO Microsoft Teams bot:</span></span>

1. [<span data-ttu-id="47605-127">Erstellen eines freien Azure-Kontos</span><span class="sxs-lookup"><span data-stu-id="47605-127">Create an Azure free account</span></span>](#create-an-azure-account)
2. [<span data-ttu-id="47605-128">Aktualisieren des Teams-App-Manifests</span><span class="sxs-lookup"><span data-stu-id="47605-128">Update your Teams app manifest</span></span>](#update-your-app-manifest)
3. [<span data-ttu-id="47605-129">Hinzufügen des Codes zum Anfordern und empfangen des bot-Tokens</span><span class="sxs-lookup"><span data-stu-id="47605-129">Add the code to request and receive the bot token</span></span>](#request-a-bot-token)

### <a name="create-an-azure-account"></a><span data-ttu-id="47605-130">Erstellen eines Azure-Kontos</span><span class="sxs-lookup"><span data-stu-id="47605-130">Create an Azure account</span></span>

<span data-ttu-id="47605-131">Dieser Schritt ähnelt dem [Registerkarten-SSO-Fluss](../../../tabs/how-to/authentication/auth-aad-sso.md):</span><span class="sxs-lookup"><span data-stu-id="47605-131">This step is similar to the [tab SSO flow](../../../tabs/how-to/authentication/auth-aad-sso.md):</span></span>

1. <span data-ttu-id="47605-132">Rufen Sie Ihre [Azure AD-Anwendungs-ID](/azure/active-directory/develop/howto-create-service-principal-portal#get-values-for-signing-in) für Microsoft Teams-Desktop,-Webdienste oder Mobile Clients ab.</span><span class="sxs-lookup"><span data-stu-id="47605-132">Get your [Azure AD Application ID](/azure/active-directory/develop/howto-create-service-principal-portal#get-values-for-signing-in) for Teams desktop, web, or mobile client.</span></span>
2. <span data-ttu-id="47605-133">Geben Sie die Berechtigungen an, die Ihre Anwendung für den Azure AD-Endpunkt und optional für Microsoft Graph benötigt.</span><span class="sxs-lookup"><span data-stu-id="47605-133">Specify the permissions that your application needs for the Azure AD endpoint and, optionally, Microsoft Graph.</span></span>
3. <span data-ttu-id="47605-134">[Erteilen von Berechtigungen](/azure/active-directory/develop/howto-create-service-principal-portal#configure-access-policies-on-resources) für Desktop-, Webanwendungen und Mobile Microsoft Teams-Anwendungen</span><span class="sxs-lookup"><span data-stu-id="47605-134">[Grant permissions](/azure/active-directory/develop/howto-create-service-principal-portal#configure-access-policies-on-resources) for Teams desktop, web, and mobile applications.</span></span>
4. <span data-ttu-id="47605-135">Fügen Sie eine Client-App hinzu, indem Sie die Schaltfläche **Bereich hinzufügen** auswählen und im geöffneten Bereich `access_as_user` als **Bereichsnamen** eingeben.</span><span class="sxs-lookup"><span data-stu-id="47605-135">Add a client app by selecting the **Add a scope** button and in the panel that opens, enter `access_as_user` as the **Scope name**.</span></span>

>[!NOTE]
> <span data-ttu-id="47605-136">Der Bereich "access_as_user", der zum Hinzufügen einer Client-App verwendet wird, ist für "Administratoren und Benutzer".</span><span class="sxs-lookup"><span data-stu-id="47605-136">The "access_as_user" scope used to add a client app is for "Administrators and users".</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="47605-137">Wenn Sie einen eigenständigen bot erstellen, legen Sie den Anwendungs-ID-URI auf `api://botid-{YourBotId}` hier fest, **YourBotId** verweist auf Ihre Azure AD Anwendungs-ID.</span><span class="sxs-lookup"><span data-stu-id="47605-137">If you are building a standalone bot, set the Application ID URI to `api://botid-{YourBotId}` Here, **YourBotId** refers to your Azure AD application ID.</span></span>
> * <span data-ttu-id="47605-138">Wenn Sie eine APP mit einem bot und einer RegisterkarteErstellen, legen Sie den Anwendungs-ID-URI auf fest `api://fully-qualified-domain-name.com/botid-{YourBotId}` .</span><span class="sxs-lookup"><span data-stu-id="47605-138">If you are building an app with a bot and a tab, set the Application ID URI to `api://fully-qualified-domain-name.com/botid-{YourBotId}`.</span></span>

### <a name="update-your-app-manifest"></a><span data-ttu-id="47605-139">Aktualisieren des App-Manifests</span><span class="sxs-lookup"><span data-stu-id="47605-139">Update your app manifest</span></span>

<span data-ttu-id="47605-140">Fügen Sie Ihrem Microsoft Teams-Manifest neue Eigenschaften hinzu:</span><span class="sxs-lookup"><span data-stu-id="47605-140">Add new properties to your Microsoft Teams manifest:</span></span>

<span data-ttu-id="47605-141">**WebApplicationInfo** -das übergeordnete Element der folgenden Elemente:</span><span class="sxs-lookup"><span data-stu-id="47605-141">**WebApplicationInfo** - The parent of the following elements:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="47605-142">**ID** – die Client-ID der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="47605-142">**id** - The client ID of the application.</span></span> <span data-ttu-id="47605-143">Dies ist die Anwendungs-ID, die Sie im Rahmen der Registrierung der Anwendung mit Azure AD erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="47605-143">This is the application ID that you obtained as part of registering the application with Azure AD.</span></span>
>* <span data-ttu-id="47605-144">**Resource** – die Domäne und Unterdomäne Ihrer Anwendung.</span><span class="sxs-lookup"><span data-stu-id="47605-144">**resource** - The domain and subdomain of your application.</span></span> <span data-ttu-id="47605-145">Hierbei handelt es sich um denselben URI (einschließlich des `api://` Protokolls), den Sie bei der Erstellung Ihres `scope` in Schritt 6 oben registriert haben.</span><span class="sxs-lookup"><span data-stu-id="47605-145">This is the same URI (including the `api://` protocol) that you registered when creating your `scope` in step 6 above.</span></span> <span data-ttu-id="47605-146">Sie sollten den `access_as_user` Pfad nicht in Ihre Ressource einschließen.</span><span class="sxs-lookup"><span data-stu-id="47605-146">You shouldn't include the `access_as_user` path in your resource.</span></span> <span data-ttu-id="47605-147">Der Domänenteil dieses URIs sollte der Domäne entsprechen, einschließlich aller Unterdomänen, die in den URLs Ihres Teams-Anwendungsmanifests verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="47605-147">The domain part of this URI should match the domain, including any subdomains, used in the URLs of your Teams application manifest.</span></span>

```json
"webApplicationInfo": {
  "id": "00000000-0000-0000-0000-000000000000",
  "resource": "api://subdomain.example.com/00000000-0000-0000-0000-000000000000"
}
```

### <a name="request-a-bot-token"></a><span data-ttu-id="47605-148">Anfordern eines bot-Tokens</span><span class="sxs-lookup"><span data-stu-id="47605-148">Request a bot token</span></span>

<span data-ttu-id="47605-149">Die Anforderung zum Abrufen des Tokens ist eine normale Post-Nachrichtenanforderung (unter Verwendung des vorhandenen Nachrichtenschemas).</span><span class="sxs-lookup"><span data-stu-id="47605-149">The request to get the token is a normal POST message request (using the existing message schema).</span></span> <span data-ttu-id="47605-150">Sie ist in den Anlagen eines OAuthCard enthalten.</span><span class="sxs-lookup"><span data-stu-id="47605-150">It is included in the attachments of an OAuthCard.</span></span> <span data-ttu-id="47605-151">Das Schema für die OAuthCard-Klasse ist im [Microsoft-bot-Schema 4,0](/dotnet/api/microsoft.bot.schema.oauthcard?view=botbuilder-dotnet-stable&preserve-view=true) definiert und ähnelt einer Anmeldekarte.</span><span class="sxs-lookup"><span data-stu-id="47605-151">The schema for the OAuthCard class is defined in [Microsoft Bot Schema 4.0](/dotnet/api/microsoft.bot.schema.oauthcard?view=botbuilder-dotnet-stable&preserve-view=true) and it is very similar to a sign-in card.</span></span> <span data-ttu-id="47605-152">Diese Anforderung wird von Microsoft Teams als automatische Token-Übernahme behandelt, wenn die `TokenExchangeResource` Eigenschaft auf der Karte aufgefüllt ist.</span><span class="sxs-lookup"><span data-stu-id="47605-152">Teams will treat this request as a silent token acquisition if the `TokenExchangeResource` property is populated on the card.</span></span> <span data-ttu-id="47605-153">Für den Teams-Kanal honorieren wir nur die `Id` Eigenschaft, die eine Token-Anforderung eindeutig identifiziert.</span><span class="sxs-lookup"><span data-stu-id="47605-153">For the Teams channel we honor only the `Id` property, which uniquely identifies a token request.</span></span>

>[!NOTE]
> <span data-ttu-id="47605-154">Das bot `OAuthPrompt` -Framework oder das `MultiProviderAuthDialog` wird für die SSO-Authentifizierung (Single Sign-on, einmaliges Anmelden) unterstützt.</span><span class="sxs-lookup"><span data-stu-id="47605-154">The Bot Framework `OAuthPrompt` or the `MultiProviderAuthDialog` is supported for single sign-on (SSO) authentication.</span></span>

<span data-ttu-id="47605-155">Wenn der Benutzer Ihre Anwendung zum ersten Mal verwendet und die Zustimmung des Benutzers erforderlich ist, wird dem Benutzer ein Dialogfeld angezeigt, in dem die Zustimmungs Erfahrung ähnlich wie unten fortgesetzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="47605-155">If this is the first time the user is using your application and the user consent is required, the user will be shown a dialog to continue with the consent experience similar to the one below.</span></span> <span data-ttu-id="47605-156">Wenn der Benutzer **Continue** auswählt, treten zwei verschiedene Dinge auf, je nachdem, ob der bot definiert ist oder nicht, und eine Anmeldeschaltfläche auf dem OAuthCard.</span><span class="sxs-lookup"><span data-stu-id="47605-156">When the user selects **Continue**, two different things occur depending on whether the bot is defined or not and a sign-in button on the OAuthCard.</span></span>

![Dialogfeld Zustimmung](../../../assets/images/bots/bots-consent-dialogbox.png)

<span data-ttu-id="47605-158">Wenn der bot eine Anmeldeschaltfläche definiert, wird der Anmelde Fluss für Bots ähnlich dem Anmelde Fluss von einer kartenschaltfläche in einem Nachrichtendatenstrom ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="47605-158">If the bot defines a sign-in button, the sign-in flow for bots will be triggered similarly to the sign-in flow from a card button in a message stream.</span></span> <span data-ttu-id="47605-159">Es liegt an dem Entwickler, zu entscheiden, welche Berechtigungen für den Benutzer erteilt werden sollen, um ihn zu genehmigen.</span><span class="sxs-lookup"><span data-stu-id="47605-159">It is up to the developer to decide which permissions to ask for the user to consent.</span></span> <span data-ttu-id="47605-160">Dieser Ansatz wird empfohlen, wenn Sie ein Token mit Berechtigungen darüber hinaus benötigen `openId` , beispielsweise wenn Sie das Token für Graph-Ressourcen austauschen möchten.</span><span class="sxs-lookup"><span data-stu-id="47605-160">This approach is recommended if you need a token with permissions beyond `openId`, for example, if you want to exchange the token for graph resources.</span></span>

<span data-ttu-id="47605-161">Wenn der bot keine Anmeldeschaltfläche auf der Karte bereitstellt, wird die Benutzer Zustimmung für einen minimalen Satz von Berechtigungen ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="47605-161">If the bot is not providing a sign-in button on the card, it triggers user consent for a minimal set of permissions.</span></span> <span data-ttu-id="47605-162">Dieses Token eignet sich für die Standardauthentifizierung und das erhalten der e-Mail-Adresse des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="47605-162">This token is useful for basic authentication and getting the user email address.</span></span>

<span data-ttu-id="47605-163">**C#-Token-Anforderung ohne Anmeldeschaltfläche**:</span><span class="sxs-lookup"><span data-stu-id="47605-163">**C# token request without a sign-in button**:</span></span>

```csharp
var attachment = new Attachment
            {
                Content = new OAuthCard
                {
                    TokenExchangeResource = new TokenExchangeResource
                    {
                        Id = requestId
                    }
                },
                ContentType = OAuthCard.ContentType,
            };
            var activity = MessageFactory.Attachment(attachment);

            // NOTE: This activity needs to be sent in the 1:1 conversation between the bot and the user. 
            // If the bot supports group and channel scope, this code should be updated to send the request to the 1:1 chat. 

   await turnContext.SendActivityAsync(activity, cancellationToken);
```

#### <a name="receiving-the-token"></a><span data-ttu-id="47605-164">Empfangen des Tokens</span><span class="sxs-lookup"><span data-stu-id="47605-164">Receiving the token</span></span>

<span data-ttu-id="47605-165">Die Antwort mit dem Token wird über eine Invoke-Aktivität mit dem gleichen Schema gesendet wie andere Aktivitäten aufrufen, die die Bots heute empfangen.</span><span class="sxs-lookup"><span data-stu-id="47605-165">The response with the token is sent through an invoke activity with the same schema as others invoke activities the bots receive today.</span></span> <span data-ttu-id="47605-166">Der einzige Unterschied besteht darin, dass der Aufruf Name, die **Anmelde-tokenExchange** und das **Wertfeld** die **ID** (eine Zeichenfolge) der anfänglichen Anforderung zum Abrufen des Tokens und des **Token** -Felds (ein Zeichenfolgenwert einschließlich des Tokens) enthalten wird.</span><span class="sxs-lookup"><span data-stu-id="47605-166">The only difference is the invoke name, **sign-in/tokenExchange** and the **value** field which will contain the **Id** (a string) of the initial request to get the token and the **token** field (a string value including the token).</span></span> <span data-ttu-id="47605-167">Beachten Sie, dass Sie möglicherweise mehrere Antworten für eine bestimmte Anforderung erhalten, wenn der Benutzer über mehrere aktive Endpunkte verfügt.</span><span class="sxs-lookup"><span data-stu-id="47605-167">Please note that you might receive multiple responses for a given request if the user has multiple active endpoints.</span></span> <span data-ttu-id="47605-168">Es liegt an Ihnen, die Antworten mit dem Token zu deduplizieren.</span><span class="sxs-lookup"><span data-stu-id="47605-168">It is up to you to deduplicate the responses with the token.</span></span>

<span data-ttu-id="47605-169">**C#-Code zur Reaktion auf die Behandlung der Invoke-Aktivität**:</span><span class="sxs-lookup"><span data-stu-id="47605-169">**C# code to respond to handle the invoke activity**:</span></span>

```csharp
protected override async Task<InvokeResponse> OnInvokeActivityAsync
  (ITurnContext<IInvokeActivity> turnContext, CancellationToken cancellationToken)
        {
            try
            {
                if (turnContext.Activity.Name == SignInConstants.TokenExchangeOperationName && turnContext.Activity.ChannelId == Channels.Msteams)
                {
                    await OnTokenResponseEventAsync(turnContext, cancellationToken);
                    return new InvokeResponse() { Status = 200 };
                }
                else
                {
                    return await base.OnInvokeActivityAsync(turnContext, cancellationToken);
                }
            }
            catch (InvokeResponseException e)
            {
                return e.CreateInvokeResponse();
            }
        }
```

<span data-ttu-id="47605-170">Die `turnContext.activity.value` ist vom Typ [TokenExchangeInvokeRequest](/dotnet/api/microsoft.bot.schema.tokenexchangeinvokerequest?view=botbuilder-dotnet-stable&preserve-view=true) und enthält das Token, das von Ihrem bot weiter verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="47605-170">The `turnContext.activity.value` is of type [TokenExchangeInvokeRequest](/dotnet/api/microsoft.bot.schema.tokenexchangeinvokerequest?view=botbuilder-dotnet-stable&preserve-view=true) and contains the token that can be further used by your bot.</span></span> <span data-ttu-id="47605-171">Speichern Sie die Token aus Leistungsgründen sicher, und aktualisieren Sie Sie.</span><span class="sxs-lookup"><span data-stu-id="47605-171">Store the tokens securely for performance reasons and refresh them.</span></span>

### <a name="update-the-azure-portal-with-the-oauth-connection"></a><span data-ttu-id="47605-172">Aktualisieren des Azure-Portals mit der OAuth-Verbindung</span><span class="sxs-lookup"><span data-stu-id="47605-172">Update the Azure portal with the OAuth connection</span></span>

1. <span data-ttu-id="47605-173">Navigieren Sie im Azure-Portal zurück zur **Registrierung für bot-Kanäle**.</span><span class="sxs-lookup"><span data-stu-id="47605-173">In the Azure Portal, navigate back to the **Bot Channels Registration**.</span></span>

2. <span data-ttu-id="47605-174">Wechseln Sie zum Blade " **Einstellungen** ", und wählen Sie im Abschnitt OAuth-Verbindungseinstellungen die Option **Hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="47605-174">Switch to the **Settings** blade and choose **Add Setting** under the OAuth Connection Settings section.</span></span>

![SSOBotHandle2-Ansicht](../../../assets/images/bots/bots-vuSSOBotHandle2-settings.png)

3. <span data-ttu-id="47605-176">Schließen Sie das Formular für die **Verbindungseinstellung** ab:</span><span class="sxs-lookup"><span data-stu-id="47605-176">Complete the **Connection Setting** form:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="47605-177">Geben Sie einen Namen für die neue Verbindungseinstellung ein.</span><span class="sxs-lookup"><span data-stu-id="47605-177">Enter a name for your new Connection Setting.</span></span> <span data-ttu-id="47605-178">Dies ist der Name, auf den innerhalb der Einstellungen Ihres bot-Dienstcodes in **Schritt 5** verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="47605-178">This will be the name that gets referenced inside the settings of your bot service code in **step 5**.</span></span>
> * <span data-ttu-id="47605-179">Wählen Sie in der Dropdownliste Dienstanbieter die Option **Azure Active Directory v2** aus.</span><span class="sxs-lookup"><span data-stu-id="47605-179">In the Service Provider dropdown, select **Azure Active Directory V2**.</span></span>
>* <span data-ttu-id="47605-180">Geben Sie die Clientanmeldeinformationen für die Aad-Anwendung ein.</span><span class="sxs-lookup"><span data-stu-id="47605-180">Enter the client credentials for the AAD application.</span></span>

>[!NOTE]
> <span data-ttu-id="47605-181">**Implizite Zuwendungen** sind in der Aad-Anwendung möglicherweise erforderlich.</span><span class="sxs-lookup"><span data-stu-id="47605-181">**Implicit grant** may be required in the AAD application.</span></span>

>* <span data-ttu-id="47605-182">Verwenden Sie für die Token-Exchange-URL den Bereichswert, der im vorherigen Schritt ihrer Aad-Anwendung definiert wurde.</span><span class="sxs-lookup"><span data-stu-id="47605-182">For the Token Exchange URL, use the scope value defined in the previous step of your AAD application.</span></span> <span data-ttu-id="47605-183">Das vorhanden sein der Token-Exchange-URL zeigt dem SDK an, dass diese Aad-Anwendung für SSO konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="47605-183">The presence of the Token Exchange URL is indicating to the SDK that this AAD application is configured for SSO.</span></span>
>* <span data-ttu-id="47605-184">Geben Sie "Common" als **Mandanten-ID** an.</span><span class="sxs-lookup"><span data-stu-id="47605-184">Specify "common" as the **Tenant ID**.</span></span>
>* <span data-ttu-id="47605-185">Fügen Sie alle Bereiche hinzu, die beim Angeben von Berechtigungen für Downstream-APIs für Ihre Aad-Anwendung konfiguriert wurden.</span><span class="sxs-lookup"><span data-stu-id="47605-185">Add all the scopes configured when specifying permissions to downstream APIs for your AAD application.</span></span> <span data-ttu-id="47605-186">Wenn die Client-ID und der geheime Client Schlüssel bereitgestellt werden, tauschen Tokenspeicher das Token für ein Diagramm Token mit definierten Berechtigungen für Sie aus.</span><span class="sxs-lookup"><span data-stu-id="47605-186">With the client id and client secret provided, token store will exchange the token for a graph token with defined permissions for you.</span></span>
>* <span data-ttu-id="47605-187">Klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="47605-187">Select **Save**.</span></span>

![VuSSOBotConnection-Einstellungsansicht](../../../assets/images/bots/bots-vuSSOBotConnection-settings.png)

### <a name="update-the-auth-sample"></a><span data-ttu-id="47605-189">Aktualisieren des Authentifizierungs Beispiels</span><span class="sxs-lookup"><span data-stu-id="47605-189">Update the auth sample</span></span>

<span data-ttu-id="47605-190">Beginnen Sie mit dem Microsoft [Teams-Authentifizierungs Beispiel](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth).</span><span class="sxs-lookup"><span data-stu-id="47605-190">Start with the [teams auth sample](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth).</span></span>

1. <span data-ttu-id="47605-191">Aktualisieren Sie die TeamsBot, um Folgendes einzuschließen.</span><span class="sxs-lookup"><span data-stu-id="47605-191">Update the TeamsBot to include the following.</span></span> <span data-ttu-id="47605-192">Informationen zum Verarbeiten des deduping der eingehenden Anforderung finden Sie weiter unten:</span><span class="sxs-lookup"><span data-stu-id="47605-192">To handle the deduping of the incoming request, see below:</span></span>

```csharp
 protected override async Task OnSignInInvokeAsync(ITurnContext<IInvokeActivity> turnContext, CancellationToken cancellationToken)
        {
            await Dialog.RunAsync(turnContext, ConversationState.CreateProperty<DialogState>(nameof(DialogState)), cancellationToken);
        }
    protected override async Task OnTokenResponseEventAsync(ITurnContext<IEventActivity> turnContext, CancellationToken cancellationToken)
        {
            await Dialog.RunAsync(turnContext, ConversationState.CreateProperty<DialogState>(nameof(DialogState)), cancellationToken);
        }
```
  
2. <span data-ttu-id="47605-193">Aktualisieren Sie das, `appsettings.json` um das `botId` obige, Kennwort und den oben definierten Verbindungsnamen einzubeziehen.</span><span class="sxs-lookup"><span data-stu-id="47605-193">Update the `appsettings.json` to include the `botId`, password, and the connection name defined above.</span></span>
3. <span data-ttu-id="47605-194">Aktualisieren Sie das Manifest, und stellen Sie sicher, dass `token.botframework.com` es sich im Abschnitt gültige Domänen befindet.</span><span class="sxs-lookup"><span data-stu-id="47605-194">Update the manifest and ensure that `token.botframework.com` is in the valid domains section.</span></span>
4. <span data-ttu-id="47605-195">Komprimieren Sie das Manifest mit den Profilbildern, und installieren Sie es in Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="47605-195">Zip the manifest with the profile images and install it in Teams.</span></span>

#### <a name="additional-code-samples"></a><span data-ttu-id="47605-196">Zusätzliche Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="47605-196">Additional code samples</span></span>

* <span data-ttu-id="47605-197">[C#-Beispiel mit dem bot Framework SDK](https://microsoft-my.sharepoint-df.com/:u:/p/vul/ETZQfeTViDlCv-frjgTIincB7dvk2HOnma1TLvcoeGGIxg?e=uPq62c).</span><span class="sxs-lookup"><span data-stu-id="47605-197">[C# sample using the Bot Framework SDK](https://microsoft-my.sharepoint-df.com/:u:/p/vul/ETZQfeTViDlCv-frjgTIincB7dvk2HOnma1TLvcoeGGIxg?e=uPq62c).</span></span>

* <span data-ttu-id="47605-198">[C#-Beispiel mit dem bot Framework SDK zum deduplizieren der Token-Anforderung](https://microsoft.sharepoint.com/:u:/t/ExtensibilityandFundamentals/Ea36rUGiN1BGt1RiLOb-mY8BGMF8NwPtronYGym0sCGOTw?e=4bB682).</span><span class="sxs-lookup"><span data-stu-id="47605-198">[C# sample using the Bot Framework SDK to deduplicate the token request](https://microsoft.sharepoint.com/:u:/t/ExtensibilityandFundamentals/Ea36rUGiN1BGt1RiLOb-mY8BGMF8NwPtronYGym0sCGOTw?e=4bB682).</span></span>

* [<span data-ttu-id="47605-199">C#-Beispiel ohne Verwendung des SDK-Token-Speichers für bot Framework</span><span class="sxs-lookup"><span data-stu-id="47605-199">C# sample without using the Bot Framework SDK token store</span></span>](https://microsoft-my.sharepoint-df.com/:u:/p/tac/EceKDXrkMn5AuGbh6iGid8ABKEVQ6hkxArxK1y7-M8OVPw)
