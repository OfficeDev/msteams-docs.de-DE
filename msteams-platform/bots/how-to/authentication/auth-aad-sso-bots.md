---
title: Unterstützung für einmaliges Anmelden für Bots
description: Beschreibt, wie ein Benutzertoken abgerufen wird. Derzeit kann ein bot-Entwickler eine Anmeldekarte oder den Azure bot-Dienst mit der OAuth-Kartenunterstützung verwenden.
keywords: Token, Benutzertoken, SSO-Unterstützung für Bots
ms.openlocfilehash: a056ce1a8bf0e59c9f4f30392df3bce7e8c63e00
ms.sourcegitcommit: 64acd30eee8af5fe151e9866c13226ed3f337c72
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2020
ms.locfileid: "49346854"
---
# <a name="single-sign-on-sso-support-for-bots"></a><span data-ttu-id="43e00-105">Unterstützung für einmaliges Anmelden (SSO) für Bots</span><span class="sxs-lookup"><span data-stu-id="43e00-105">Single sign-on (SSO) support for bots</span></span>

<span data-ttu-id="43e00-106">Authentifizierung mit einmaligem Anmelden in Azure Active Directory (Azure AD) minimiert, wie oft Benutzer ihre Anmeldeinformationen eingeben müssen, indem Sie das Authentifizierungstoken automatisch aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="43e00-106">Single sign-on authentication in Azure Active Directory (Azure AD) minimizes the number of times users need to enter their login credentials by silently refreshing the authentication token.</span></span> <span data-ttu-id="43e00-107">Wenn Benutzer einwilligen, Ihre APP zu verwenden, müssen Sie nicht erneut auf einem anderen Gerät zustimmen und werden automatisch angemeldet.</span><span class="sxs-lookup"><span data-stu-id="43e00-107">If users agrees to use your app, they will not have to consent again on another device and will be signed in automatically.</span></span> <span data-ttu-id="43e00-108">Der Fluss ähnelt der [SSO-Unterstützung der Teams-Registerkarte]( ../../../tabs/how-to/authentication/auth-aad-sso.md).</span><span class="sxs-lookup"><span data-stu-id="43e00-108">The flow is very similar to the [Teams tab SSO support]( ../../../tabs/how-to/authentication/auth-aad-sso.md).</span></span> <span data-ttu-id="43e00-109">Der Unterschied ist das Protokoll dafür, wie ein bot Token anfordert und Antworten erhält.</span><span class="sxs-lookup"><span data-stu-id="43e00-109">The difference is the protocol for how a bot requests tokens and receives responses.</span></span>

<span data-ttu-id="43e00-110">OAuth 2.0 ist ein offener Standard für Authentifizierung und Autorisierung, der von Azure Active Directory (Azure AD) und vielen anderen Identitätsanbietern verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="43e00-110">OAuth 2.0 is an open standard for authentication and authorization used by Azure Active Directory (Azure AD) and many other identity providers.</span></span> <span data-ttu-id="43e00-111">Ein grundlegendes Verständnis von OAuth 2,0 ist eine Voraussetzung für die Verwendung von Authentifizierung in Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="43e00-111">A basic understanding of OAuth 2.0 is a prerequisite for working with authentication in Teams.</span></span>

## <a name="bot-sso-at-runtime"></a><span data-ttu-id="43e00-112">Bot-SSO zur Laufzeit</span><span class="sxs-lookup"><span data-stu-id="43e00-112">Bot SSO at runtime</span></span>

![Bot-SSO im laufzeitdiagramm](../../../assets/images/bots/bots-sso-diagram.png)

1. <span data-ttu-id="43e00-114">Der bot sendet eine Nachricht mit einem OAuthCard, das die `tokenExchangeResource` Eigenschaft enthält.</span><span class="sxs-lookup"><span data-stu-id="43e00-114">The bot sends a message with an OAuthCard that contains the `tokenExchangeResource` property.</span></span> <span data-ttu-id="43e00-115">Es weist Microsoft Teams an, ein Authentifizierungstoken für die bot-Anwendung zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="43e00-115">It tells Teams to obtain an authentication token for the bot application.</span></span> <span data-ttu-id="43e00-116">Der Benutzer empfängt Nachrichten an allen aktiven Endpunkten des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="43e00-116">The user receives messages at all the active endpoints of the user.</span></span>

> [!NOTE]
>* <span data-ttu-id="43e00-117">Ein Benutzer kann gleichzeitig mehr als einen aktiven Endpunkt aufweisen.</span><span class="sxs-lookup"><span data-stu-id="43e00-117">A user can have more than one active endpoint at a time.</span></span>  
>* <span data-ttu-id="43e00-118">Das bot-Token wird von jedem aktiven Endpunkt des Benutzers empfangen.</span><span class="sxs-lookup"><span data-stu-id="43e00-118">The bot token is received from every active endpoint of the user.</span></span>
>* <span data-ttu-id="43e00-119">Die Unterstützung für einmaliges Anmelden erfordert derzeit, dass die APP im persönlichen Bereich installiert wird.</span><span class="sxs-lookup"><span data-stu-id="43e00-119">Single sign-on support currently requires the app to be installed in personal scope.</span></span>

2. <span data-ttu-id="43e00-120">Wenn der aktuelle Benutzer ihre bot-Anwendung zum ersten Mal verwendet hat, wird eine Anforderungs Aufforderung zur Zustimmung (sofern Zustimmung erforderlich ist) oder zur Behandlung der Step-up-Authentifizierung (beispielsweise zweistufige Authentifizierung) angezeigt.</span><span class="sxs-lookup"><span data-stu-id="43e00-120">If it is the first time the current user has used your bot application, there will be a request prompt to consent (if consent is required) or to handle step-up authentication (such as two-factor authentication).</span></span>

3. <span data-ttu-id="43e00-121">Microsoft Teams fordert das bot-Anwendungs Token vom Azure AD-Endpunkt für den aktuellen Benutzer an.</span><span class="sxs-lookup"><span data-stu-id="43e00-121">Microsoft Teams requests the bot application token from the Azure AD endpoint for the current user.</span></span>

4. <span data-ttu-id="43e00-122">Azure AD sendet das bot-Anwendungs Token an die Teams-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="43e00-122">Azure AD sends the bot application token to the Teams application.</span></span>

5. <span data-ttu-id="43e00-123">Microsoft Teams sendet das Token an den bot als Teil des Value-Objekts, das von der Invoke-Aktivität mit dem Namen Sign-in/tokenExchange zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="43e00-123">Microsoft Teams sends the token to the bot as part of the value object returned by the invoke activity with the name sign-in/tokenExchange.</span></span>
  
6. <span data-ttu-id="43e00-124">Das Token wird in der bot-Anwendung analysiert, um die erforderlichen Informationen zu extrahieren, beispielsweise die e-Mail-Adresse des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="43e00-124">The token will be parsed in the bot application to extract the needed information, such as the user's email address.</span></span>
  
## <a name="develop-a-single-sign-on-microsoft-teams-bot"></a><span data-ttu-id="43e00-125">Entwickeln eines Single Sign-on Microsoft Teams-bot</span><span class="sxs-lookup"><span data-stu-id="43e00-125">Develop a Single sign-on Microsoft Teams bot</span></span>
  
<span data-ttu-id="43e00-126">Die folgenden Schritte sind erforderlich, um einen SSO-Microsoft Teams-bot zu entwickeln:</span><span class="sxs-lookup"><span data-stu-id="43e00-126">The following steps: are required to develop an SSO Microsoft Teams bot:</span></span>

1. [<span data-ttu-id="43e00-127">Erstellen eines freien Azure-Kontos</span><span class="sxs-lookup"><span data-stu-id="43e00-127">Create an Azure free account</span></span>](#create-an-azure-account)
2. [<span data-ttu-id="43e00-128">Aktualisieren des Teams-App-Manifests</span><span class="sxs-lookup"><span data-stu-id="43e00-128">Update your Teams app manifest</span></span>](#update-your-app-manifest)
3. [<span data-ttu-id="43e00-129">Hinzufügen des Codes zum Anfordern und empfangen des bot-Tokens</span><span class="sxs-lookup"><span data-stu-id="43e00-129">Add the code to request and receive the bot token</span></span>](#request-a-bot-token)

### <a name="create-an-azure-account"></a><span data-ttu-id="43e00-130">Erstellen eines Azure-Kontos</span><span class="sxs-lookup"><span data-stu-id="43e00-130">Create an Azure account</span></span>

<span data-ttu-id="43e00-131">Dieser Schritt ähnelt dem [Registerkarten-SSO-Fluss](../../../tabs/how-to/authentication/auth-aad-sso.md):</span><span class="sxs-lookup"><span data-stu-id="43e00-131">This step is similar to the [tab SSO flow](../../../tabs/how-to/authentication/auth-aad-sso.md):</span></span>

1. <span data-ttu-id="43e00-132">Rufen Sie Ihre [Azure AD-Anwendungs-ID](/azure/active-directory/develop/howto-create-service-principal-portal#get-values-for-signing-in)ab.</span><span class="sxs-lookup"><span data-stu-id="43e00-132">Get your [Azure AD Application ID](/azure/active-directory/develop/howto-create-service-principal-portal#get-values-for-signing-in).</span></span>
2. <span data-ttu-id="43e00-133">Geben Sie die Berechtigungen an, die Ihre Anwendung für den Azure AD-Endpunkt und optional für Microsoft Graph benötigt.</span><span class="sxs-lookup"><span data-stu-id="43e00-133">Specify the permissions that your application needs for the Azure AD endpoint and, optionally, Microsoft Graph.</span></span>
3. <span data-ttu-id="43e00-134">[Erteilen von Berechtigungen](/azure/active-directory/develop/howto-create-service-principal-portal#configure-access-policies-on-resources) für Desktop-, Webanwendungen und Mobile Microsoft Teams-Anwendungen</span><span class="sxs-lookup"><span data-stu-id="43e00-134">[Grant permissions](/azure/active-directory/develop/howto-create-service-principal-portal#configure-access-policies-on-resources) for Teams desktop, web, and mobile applications.</span></span>
4. <span data-ttu-id="43e00-135">Vorautorisieren von Teams durch Auswählen der Schaltfläche **Bereich hinzufügen** und Eingeben des `access_as_user` **Bereichsnamens** in das geöffnete Fenster.</span><span class="sxs-lookup"><span data-stu-id="43e00-135">Pre-authorize Teams by selecting the **Add a scope** button and in the panel that opens, enter `access_as_user` as the **Scope name**.</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="43e00-136">Wenn Sie einen eigenständigen bot erstellen, legen Sie den Anwendungs-ID-URI auf fest `api://botid-{YourBotId}` .</span><span class="sxs-lookup"><span data-stu-id="43e00-136">If you are building a standalone bot, set the Application ID URI to `api://botid-{YourBotId}` .</span></span>
> * <span data-ttu-id="43e00-137">Wenn Sie eine APP mit einem bot und einer RegisterkarteErstellen, legen Sie den Anwendungs-ID-URI auf fest `api://fully-qualified-domain-name.com/botid-{YourBotId}` .</span><span class="sxs-lookup"><span data-stu-id="43e00-137">If you are building an app with a bot and a tab, set the Application ID URI to `api://fully-qualified-domain-name.com/botid-{YourBotId}`.</span></span>

### <a name="update-your-app-manifest"></a><span data-ttu-id="43e00-138">Aktualisieren des App-Manifests</span><span class="sxs-lookup"><span data-stu-id="43e00-138">Update your app manifest</span></span>

<span data-ttu-id="43e00-139">Fügen Sie Ihrem Microsoft Teams-Manifest neue Eigenschaften hinzu:</span><span class="sxs-lookup"><span data-stu-id="43e00-139">Add new properties to your Microsoft Teams manifest:</span></span>

<span data-ttu-id="43e00-140">**WebApplicationInfo** -das übergeordnete Element der folgenden Elemente:</span><span class="sxs-lookup"><span data-stu-id="43e00-140">**WebApplicationInfo** - The parent of the following elements:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="43e00-141">**ID** – die Client-ID der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="43e00-141">**id** - The client ID of the application.</span></span> <span data-ttu-id="43e00-142">Dies ist die Anwendungs-ID, die Sie im Rahmen der Registrierung der Anwendung mit Azure AD erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="43e00-142">This is the application ID that you obtained as part of registering the application with Azure AD.</span></span>
>* <span data-ttu-id="43e00-143">**Resource** – die Domäne und Unterdomäne Ihrer Anwendung.</span><span class="sxs-lookup"><span data-stu-id="43e00-143">**resource** - The domain and subdomain of your application.</span></span> <span data-ttu-id="43e00-144">Hierbei handelt es sich um denselben URI (einschließlich des `api://` Protokolls), den Sie bei der Erstellung Ihres `scope` in Schritt 6 oben registriert haben.</span><span class="sxs-lookup"><span data-stu-id="43e00-144">This is the same URI (including the `api://` protocol) that you registered when creating your `scope` in step 6 above.</span></span> <span data-ttu-id="43e00-145">Sie sollten den `access_as_user` Pfad nicht in Ihre Ressource einschließen.</span><span class="sxs-lookup"><span data-stu-id="43e00-145">You shouldn't include the `access_as_user` path in your resource.</span></span> <span data-ttu-id="43e00-146">Der Domänenteil dieses URIs sollte der Domäne entsprechen, einschließlich aller Unterdomänen, die in den URLs Ihres Teams-Anwendungsmanifests verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="43e00-146">The domain part of this URI should match the domain, including any subdomains, used in the URLs of your Teams application manifest.</span></span>

```json
"webApplicationInfo": {
  "id": "00000000-0000-0000-0000-000000000000",
  "resource": "api://subdomain.example.com/00000000-0000-0000-0000-000000000000"
}
```

### <a name="request-a-bot-token"></a><span data-ttu-id="43e00-147">Anfordern eines bot-Tokens</span><span class="sxs-lookup"><span data-stu-id="43e00-147">Request a bot token</span></span>

<span data-ttu-id="43e00-148">Die Anforderung zum Abrufen des Tokens ist eine normale Post-Nachrichtenanforderung (unter Verwendung des vorhandenen Nachrichtenschemas).</span><span class="sxs-lookup"><span data-stu-id="43e00-148">The request to get the token is a normal POST message request (using the existing message schema).</span></span> <span data-ttu-id="43e00-149">Sie ist in den Anlagen eines OAuthCard enthalten.</span><span class="sxs-lookup"><span data-stu-id="43e00-149">It is included in the attachments of an OAuthCard.</span></span> <span data-ttu-id="43e00-150">Das Schema für die OAuthCard-Klasse ist im [Microsoft-bot-Schema 4,0](/dotnet/api/microsoft.bot.schema.oauthcard?view=botbuilder-dotnet-stable&preserve-view=true) definiert und ähnelt einer Anmeldekarte.</span><span class="sxs-lookup"><span data-stu-id="43e00-150">The schema for the OAuthCard class is defined in [Microsoft Bot Schema 4.0](/dotnet/api/microsoft.bot.schema.oauthcard?view=botbuilder-dotnet-stable&preserve-view=true) and it is very similar to a sign-in card.</span></span> <span data-ttu-id="43e00-151">Diese Anforderung wird von Microsoft Teams als automatische Token-Übernahme behandelt, wenn die `TokenExchangeResource` Eigenschaft auf der Karte aufgefüllt ist.</span><span class="sxs-lookup"><span data-stu-id="43e00-151">Teams will treat this request as a silent token acquisition if the `TokenExchangeResource` property is populated on the card.</span></span> <span data-ttu-id="43e00-152">Für den Teams-Kanal honorieren wir nur die `Id` Eigenschaft, die eine Token-Anforderung eindeutig identifiziert.</span><span class="sxs-lookup"><span data-stu-id="43e00-152">For the Teams channel we honor only the `Id` property, which uniquely identifies a token request.</span></span>

<span data-ttu-id="43e00-153">Wenn der Benutzer Ihre Anwendung zum ersten Mal verwendet und die Zustimmung des Benutzers erforderlich ist, wird dem Benutzer ein Dialogfeld angezeigt, in dem die Zustimmungs Erfahrung ähnlich wie unten fortgesetzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="43e00-153">If this is the first time the user is using your application and the user consent is required, the user will be shown a dialog to continue with the consent experience similar to the one below.</span></span> <span data-ttu-id="43e00-154">Wenn der Benutzer **Continue** auswählt, treten zwei verschiedene Dinge auf, je nachdem, ob der bot definiert ist oder nicht, und eine Anmeldeschaltfläche auf dem OAuthCard.</span><span class="sxs-lookup"><span data-stu-id="43e00-154">When the user selects **Continue**, two different things occur depending on whether the bot is defined or not and a sign-in button on the OAuthCard.</span></span>

![Dialogfeld Zustimmung](../../../assets/images/bots/bots-consent-dialogbox.png)

<span data-ttu-id="43e00-156">Wenn der bot eine Anmeldeschaltfläche definiert, wird der Anmelde Fluss für Bots ähnlich dem Anmelde Fluss von einer kartenschaltfläche in einem Nachrichtendatenstrom ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="43e00-156">If the bot defines a sign-in button, the sign-in flow for bots will be triggered similarly to the sign-in flow from a card button in a message stream.</span></span> <span data-ttu-id="43e00-157">Es liegt an dem Entwickler, zu entscheiden, welche Berechtigungen für den Benutzer erteilt werden sollen, um ihn zu genehmigen.</span><span class="sxs-lookup"><span data-stu-id="43e00-157">It is up to the developer to decide which permissions to ask for the user to consent.</span></span> <span data-ttu-id="43e00-158">Dieser Ansatz wird empfohlen, wenn Sie ein Token mit Berechtigungen darüber hinaus benötigen `openId` , beispielsweise wenn Sie das Token für Graph-Ressourcen austauschen möchten.</span><span class="sxs-lookup"><span data-stu-id="43e00-158">This approach is recommended if you need a token with permissions beyond `openId`, for example, if you want to exchange the token for graph resources.</span></span>

<span data-ttu-id="43e00-159">Wenn der bot keine Anmeldeschaltfläche auf der Karte bereitstellt, wird die Benutzer Zustimmung für einen minimalen Satz von Berechtigungen ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="43e00-159">If the bot is not providing a sign-in button on the card, it triggers user consent for a minimal set of permissions.</span></span> <span data-ttu-id="43e00-160">Dieses Token eignet sich für die Standardauthentifizierung und das erhalten der e-Mail-Adresse des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="43e00-160">This token is useful for basic authentication and getting the user email address.</span></span>

<span data-ttu-id="43e00-161">**C#-Token-Anforderung ohne Anmeldeschaltfläche**:</span><span class="sxs-lookup"><span data-stu-id="43e00-161">**C# token request without a sign-in button**:</span></span>

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

#### <a name="receiving-the-token"></a><span data-ttu-id="43e00-162">Empfangen des Tokens</span><span class="sxs-lookup"><span data-stu-id="43e00-162">Receiving the token</span></span>

<span data-ttu-id="43e00-163">Die Antwort mit dem Token wird über eine Invoke-Aktivität mit dem gleichen Schema gesendet wie andere Aktivitäten aufrufen, die die Bots heute empfangen.</span><span class="sxs-lookup"><span data-stu-id="43e00-163">The response with the token is sent through an invoke activity with the same schema as others invoke activities the bots receive today.</span></span> <span data-ttu-id="43e00-164">Der einzige Unterschied besteht darin, dass der Aufruf Name, die **Anmelde-tokenExchange** und das **Wertfeld** die **ID** (eine Zeichenfolge) der anfänglichen Anforderung zum Abrufen des Tokens und des **Token** -Felds (ein Zeichenfolgenwert einschließlich des Tokens) enthalten wird.</span><span class="sxs-lookup"><span data-stu-id="43e00-164">The only difference is the invoke name, **sign-in/tokenExchange** and the **value** field which will contain the **Id** (a string) of the initial request to get the token and the **token** field (a string value including the token).</span></span> <span data-ttu-id="43e00-165">Beachten Sie, dass Sie möglicherweise mehrere Antworten für eine bestimmte Anforderung erhalten, wenn der Benutzer über mehrere aktive Endpunkte verfügt.</span><span class="sxs-lookup"><span data-stu-id="43e00-165">Please note that you might receive multiple responses for a given request if the user has multiple active endpoints.</span></span> <span data-ttu-id="43e00-166">Es liegt an Ihnen, die Antworten mit dem Token zu deduplizieren.</span><span class="sxs-lookup"><span data-stu-id="43e00-166">It is up to you to deduplicate the responses with the token.</span></span>

<span data-ttu-id="43e00-167">**C#-Code zur Reaktion auf die Behandlung der Invoke-Aktivität**:</span><span class="sxs-lookup"><span data-stu-id="43e00-167">**C# code to respond to handle the invoke activity**:</span></span>

```csharp
protected override async Task<InvokeResponse> OnInvokeActivity
  (ITurnContext<IInvokeActivity> turnContext, CancellationToken cancellationToken)
        {
            try
            {
                if (turnContext.Activity.Name == SignInConstants.TokenExchangeOperationName && turnContext.Activity.ChannelId == Channels.Msteams)
                {
                    await OnTokenResponse(turnContext, cancellationToken);
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

<span data-ttu-id="43e00-168">Die `turnContext.activity.value` ist vom Typ [TokenExchangeInvokeRequest](/dotnet/api/microsoft.bot.schema.tokenexchangeinvokerequest?view=botbuilder-dotnet-stable&preserve-view=true) und enthält das Token, das von Ihrem bot weiter verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="43e00-168">The `turnContext.activity.value` is of type [TokenExchangeInvokeRequest](/dotnet/api/microsoft.bot.schema.tokenexchangeinvokerequest?view=botbuilder-dotnet-stable&preserve-view=true) and contains the token that can be further used by your bot.</span></span> <span data-ttu-id="43e00-169">Speichern Sie die Token aus Leistungsgründen sicher, und aktualisieren Sie Sie.</span><span class="sxs-lookup"><span data-stu-id="43e00-169">Store the tokens securely for performance reasons and refresh them.</span></span>

### <a name="update-the-azure-portal-with-the-oauth-connection"></a><span data-ttu-id="43e00-170">Aktualisieren des Azure-Portals mit der OAuth-Verbindung</span><span class="sxs-lookup"><span data-stu-id="43e00-170">Update the Azure portal with the OAuth connection</span></span>

1. <span data-ttu-id="43e00-171">Navigieren Sie im Azure-Portal zurück zur **Registrierung für bot-Kanäle**.</span><span class="sxs-lookup"><span data-stu-id="43e00-171">In the Azure Portal, navigate back to the **Bot Channels Registration**.</span></span>

2. <span data-ttu-id="43e00-172">Wechseln Sie zum Blade " **Einstellungen** ", und wählen Sie im Abschnitt OAuth-Verbindungseinstellungen die Option **Hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="43e00-172">Switch to the **Settings** blade and choose **Add Setting** under the OAuth Connection Settings section.</span></span>

![SSOBotHandle2-Ansicht](../../../assets/images/bots/bots-vuSSOBotHandle2-settings.png)

3. <span data-ttu-id="43e00-174">Schließen Sie das Formular für die **Verbindungseinstellung** ab:</span><span class="sxs-lookup"><span data-stu-id="43e00-174">Complete the **Connection Setting** form:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="43e00-175">Geben Sie einen Namen für die neue Verbindungseinstellung ein.</span><span class="sxs-lookup"><span data-stu-id="43e00-175">Enter a name for your new Connection Setting.</span></span> <span data-ttu-id="43e00-176">Dies ist der Name, auf den innerhalb der Einstellungen Ihres bot-Dienstcodes in **Schritt 5** verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="43e00-176">This will be the name that gets referenced inside the settings of your bot service code in **step 5**.</span></span>
> * <span data-ttu-id="43e00-177">Wählen Sie in der Dropdownliste Dienstanbieter die Option **Azure Active Directory v2** aus.</span><span class="sxs-lookup"><span data-stu-id="43e00-177">In the Service Provider dropdown, select **Azure Active Directory V2**.</span></span>
>* <span data-ttu-id="43e00-178">Geben Sie die Clientanmeldeinformationen für die Aad-Anwendung ein.</span><span class="sxs-lookup"><span data-stu-id="43e00-178">Enter the client credentials for the AAD application.</span></span>
>* <span data-ttu-id="43e00-179">Verwenden Sie für die Token-Exchange-URL den Bereichswert, der im vorherigen Schritt ihrer Aad-Anwendung definiert wurde.</span><span class="sxs-lookup"><span data-stu-id="43e00-179">For the Token Exchange URL, use the scope value defined in the previous step of your AAD application.</span></span> <span data-ttu-id="43e00-180">Das vorhanden sein der Token-Exchange-URL zeigt dem SDK an, dass diese Aad-Anwendung für SSO konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="43e00-180">The presence of the Token Exchange URL is indicating to the SDK that this AAD application is configured for SSO.</span></span>
>* <span data-ttu-id="43e00-181">Geben Sie "Common" als **Mandanten-ID** an.</span><span class="sxs-lookup"><span data-stu-id="43e00-181">Specify "common" as the **Tenant ID**.</span></span>
>* <span data-ttu-id="43e00-182">Fügen Sie alle Bereiche hinzu, die beim Angeben von Berechtigungen für Downstream-APIs für Ihre Aad-Anwendung konfiguriert wurden.</span><span class="sxs-lookup"><span data-stu-id="43e00-182">Add all the scopes configured when specifying permissions to downstream APIs for your AAD application.</span></span> <span data-ttu-id="43e00-183">Wenn die Client-ID und der geheime Client Schlüssel bereitgestellt werden, tauschen Tokenspeicher das Token für ein Diagramm Token mit definierten Berechtigungen für Sie aus.</span><span class="sxs-lookup"><span data-stu-id="43e00-183">With the client id and client secret provided, token store will exchange the token for a graph token with defined permissions for you.</span></span>
>* <span data-ttu-id="43e00-184">Klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="43e00-184">Select **Save**.</span></span>

![VuSSOBotConnection-Einstellungsansicht](../../../assets/images/bots/bots-vuSSOBotConnection-settings.png)

### <a name="update-the-auth-sample"></a><span data-ttu-id="43e00-186">Aktualisieren des Authentifizierungs Beispiels</span><span class="sxs-lookup"><span data-stu-id="43e00-186">Update the auth sample</span></span>

<span data-ttu-id="43e00-187">Beginnen Sie mit dem Microsoft [Teams-Authentifizierungs Beispiel](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth).</span><span class="sxs-lookup"><span data-stu-id="43e00-187">Start with the [teams auth sample](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth).</span></span>

1. <span data-ttu-id="43e00-188">Aktualisieren Sie die TeamsBot, um Folgendes einzuschließen.</span><span class="sxs-lookup"><span data-stu-id="43e00-188">Update the TeamsBot to include the following.</span></span> <span data-ttu-id="43e00-189">Informationen zum Verarbeiten des deduping der eingehenden Anforderung finden Sie weiter unten:</span><span class="sxs-lookup"><span data-stu-id="43e00-189">To handle the deduping of the incoming request, see below:</span></span>

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
  
2. <span data-ttu-id="43e00-190">Aktualisieren Sie das, `appsettings.json` um das `botId` obige, Kennwort und den oben definierten Verbindungsnamen einzubeziehen.</span><span class="sxs-lookup"><span data-stu-id="43e00-190">Update the `appsettings.json` to include the `botId`, password, and the connection name defined above.</span></span>
3. <span data-ttu-id="43e00-191">Aktualisieren Sie das Manifest, und stellen Sie sicher, dass `token.botframework.com` es sich im Abschnitt gültige Domänen befindet.</span><span class="sxs-lookup"><span data-stu-id="43e00-191">Update the manifest and ensure that `token.botframework.com` is in the valid domains section.</span></span>
4. <span data-ttu-id="43e00-192">Komprimieren Sie das Manifest mit den Profilbildern, und installieren Sie es in Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="43e00-192">Zip the manifest with the profile images and install it in Teams.</span></span>

#### <a name="additional-code-samples"></a><span data-ttu-id="43e00-193">Zusätzliche Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="43e00-193">Additional code samples</span></span>

* <span data-ttu-id="43e00-194">[C#-Beispiel mit dem bot Framework SDK](https://microsoft-my.sharepoint-df.com/:u:/p/vul/ETZQfeTViDlCv-frjgTIincB7dvk2HOnma1TLvcoeGGIxg?e=uPq62c).</span><span class="sxs-lookup"><span data-stu-id="43e00-194">[C# sample using the Bot Framework SDK](https://microsoft-my.sharepoint-df.com/:u:/p/vul/ETZQfeTViDlCv-frjgTIincB7dvk2HOnma1TLvcoeGGIxg?e=uPq62c).</span></span>

* <span data-ttu-id="43e00-195">[C#-Beispiel mit dem bot Framework SDK zum deduplizieren der Token-Anforderung](https://microsoft.sharepoint.com/:u:/t/ExtensibilityandFundamentals/Ea36rUGiN1BGt1RiLOb-mY8BGMF8NwPtronYGym0sCGOTw?e=4bB682).</span><span class="sxs-lookup"><span data-stu-id="43e00-195">[C# sample using the Bot Framework SDK to deduplicate the token request](https://microsoft.sharepoint.com/:u:/t/ExtensibilityandFundamentals/Ea36rUGiN1BGt1RiLOb-mY8BGMF8NwPtronYGym0sCGOTw?e=4bB682).</span></span>

* [<span data-ttu-id="43e00-196">C#-Beispiel ohne Verwendung des SDK-Token-Speichers für bot Framework</span><span class="sxs-lookup"><span data-stu-id="43e00-196">C# sample without using the Bot Framework SDK token store</span></span>](https://microsoft-my.sharepoint-df.com/:u:/p/tac/EceKDXrkMn5AuGbh6iGid8ABKEVQ6hkxArxK1y7-M8OVPw)
