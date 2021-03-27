---
title: SSO-Unterstützung für Ihre Messagingerweiterungen
author: KirtiPereira
description: Aktivieren der SSO-Unterstützung für Ihre Messagingerweiterungen
ms.topic: conceptual
ms.author: surbhigupta
ms.openlocfilehash: a5f75ef59a3d6fa3fe190b4dba4a1e5736a87562
ms.sourcegitcommit: 0206ed48c6a287d14aec3739540194a91766f0a3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/26/2021
ms.locfileid: "51378346"
---
# <a name="single-sign-on-sso-support-for-messaging-extensions"></a><span data-ttu-id="c94be-103">Unterstützung für einmaliges Anmelden (Single Sign-On, SSO) für Messagingerweiterungen</span><span class="sxs-lookup"><span data-stu-id="c94be-103">Single sign-on (SSO) support for messaging extensions</span></span>
 
<span data-ttu-id="c94be-104">Die Unterstützung für einmaliges Anmelden ist jetzt für Messagingerweiterungen und die Verknüpfungsentfurling verfügbar.</span><span class="sxs-lookup"><span data-stu-id="c94be-104">Single sign-on support is now available for messaging extensions and link unfurling.</span></span> <span data-ttu-id="c94be-105">Wenn Sie einmaliges Anmelden (Single Sign-On, SSO) für Messagingerweiterungen aktivieren, wird das Authentifizierungstoken automatisch aktualisiert, wodurch die Anzahl der Anmeldeinformationen für Microsoft Teams minimiert wird.</span><span class="sxs-lookup"><span data-stu-id="c94be-105">Enabling Single sign-on (SSO) for messaging extensions silently refreshes the authentication token, which minimizes the number of times you need to enter your sign in credentials for Microsoft Teams.</span></span>

<span data-ttu-id="c94be-106">In diesem Dokument erfahren Sie, wie Sie den SSO aktivieren und Ihr Authentifizierungstoken bei Bedarf speichern.</span><span class="sxs-lookup"><span data-stu-id="c94be-106">This document guides you on how to enable the SSO and store your authentication token, if required.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c94be-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="c94be-107">Prerequisites</span></span>

<span data-ttu-id="c94be-108">Die Voraussetzungen für die Aktivierung von SSO für Messagingerweiterungen und das Entf?nden von Links sind wie folgt:</span><span class="sxs-lookup"><span data-stu-id="c94be-108">The prerequisite to enable SSO for messaging extensions and link unfurling are as follows:</span></span>
* <span data-ttu-id="c94be-109">Sie müssen über ein [Azure-Konto](https://azure.microsoft.com/en-us/free/) verfügen.</span><span class="sxs-lookup"><span data-stu-id="c94be-109">You must have an [Azure](https://azure.microsoft.com/en-us/free/) account.</span></span>
* <span data-ttu-id="c94be-110">Sie müssen Ihre App über das AAD-Portal konfigurieren und Ihr Teams-Anwendungsmanifest für Ihren Bot aktualisieren, wie in der Registrierung Ihrer App über [das AAD-Portal definiert.](../../bots/how-to/authentication/auth-aad-sso-bots.md#register-your-app-through-the-aad-portal)</span><span class="sxs-lookup"><span data-stu-id="c94be-110">You must configure your app through the AAD portal, and update your Teams application manifest for your bot as defined in [register your app through the AAD portal](../../bots/how-to/authentication/auth-aad-sso-bots.md#register-your-app-through-the-aad-portal).</span></span>

> [!NOTE]
> <span data-ttu-id="c94be-111">Weitere Informationen zum Erstellen eines Azure-Kontos und zum Aktualisieren Ihres App-Manifests finden Sie unter [Single Sign-On (SSO) support for bots](../../bots/how-to/authentication/auth-aad-sso-bots.md).</span><span class="sxs-lookup"><span data-stu-id="c94be-111">For more information on creating an Azure account and updating your app manifest, see [Single sign-on (SSO) support for bots](../../bots/how-to/authentication/auth-aad-sso-bots.md).</span></span>

## <a name="enable-sso-for-messaging-extensions-and-link-unfurling"></a><span data-ttu-id="c94be-112">Aktivieren von SSO für Messagingerweiterungen und Entfurling von Verknüpfungen</span><span class="sxs-lookup"><span data-stu-id="c94be-112">Enable SSO for messaging extensions and link unfurling</span></span>

<span data-ttu-id="c94be-113">Nachdem die voraussetzungen erfüllt sind, können Sie SSO für Messagingerweiterungen aktivieren und die Verknüpfungsentfings aktivieren.</span><span class="sxs-lookup"><span data-stu-id="c94be-113">After the prerequisites are completed, you can enable SSO for messaging extensions and link unfurling.</span></span>

<span data-ttu-id="c94be-114">**So aktivieren Sie SSO**</span><span class="sxs-lookup"><span data-stu-id="c94be-114">**To enable SSO**</span></span>
1. <span data-ttu-id="c94be-115">Aktualisieren Sie Ihre [Bots-OAuth-Verbindungsdetails](../../bots/how-to/authentication/auth-aad-sso-bots.md#update-the-azure-portal-with-the-oauth-connection) im Azure-Portal.</span><span class="sxs-lookup"><span data-stu-id="c94be-115">Update your bots [OAuth connection](../../bots/how-to/authentication/auth-aad-sso-bots.md#update-the-azure-portal-with-the-oauth-connection) details in the Azure portal.</span></span>
2. <span data-ttu-id="c94be-116">Laden Sie das [Beispiel für Messagingerweiterungen herunter,](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config) und befolgen Sie die Vom Assistenten bereitgestellten Setupanweisungen.</span><span class="sxs-lookup"><span data-stu-id="c94be-116">Download the [messaging extensions sample](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config) and follow the setup instructions provided by the wizard.</span></span>
   > [!NOTE]
   > <span data-ttu-id="c94be-117">Verwenden Sie ihre Bots-OAuth-Verbindung, wenn Sie Ihre Messagingerweiterungen einrichten.</span><span class="sxs-lookup"><span data-stu-id="c94be-117">Use your bots OAuth connection when setting up your messaging extensions.</span></span>
3. <span data-ttu-id="c94be-118">Aktualisieren Sie in der [Datei TeamsMessagingExtensionsSearchAuthConfigBot.cs](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config/Bots/TeamsMessagingExtensionsSearchAuthConfigBot.cs) den Wert von *auth* auf *silentAuth* im `OnTeamsMessagingExtensionQueryAsync` und/oder `OnTeamsAppBasedLinkQueryAsync` .</span><span class="sxs-lookup"><span data-stu-id="c94be-118">In the [TeamsMessagingExtensionsSearchAuthConfigBot.cs](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config/Bots/TeamsMessagingExtensionsSearchAuthConfigBot.cs) file, update the value from *auth* to *silentAuth* in the `OnTeamsMessagingExtensionQueryAsync` and / or `OnTeamsAppBasedLinkQueryAsync`.</span></span>  

    > [!NOTE]
    > <span data-ttu-id="c94be-119">Wir unterstützen keine anderen Handler-SSO, außer und aus der `OnTeamsMessagingExtensionQueryAsync` `OnTeamsAppBasedLinkQueryAsync` Datei TeamsMessagingExtensionsSearchAuthConfigBot.cs.</span><span class="sxs-lookup"><span data-stu-id="c94be-119">We do not support other handlers SSO, except `OnTeamsMessagingExtensionQueryAsync` and `OnTeamsAppBasedLinkQueryAsync` from the TeamsMessagingExtensionsSearchAuthConfigBot.cs file.</span></span>
   
4. <span data-ttu-id="c94be-120">Sie erhalten das Token im Handler in der Nutzlast oder im , je nachdem, welches Szenario Sie für das `OnTeamsMessagingExtensionQueryAsync` `turnContext.Activity.Value` `OnTeamsAppBasedLinkQueryAsync` SSO aktivieren:</span><span class="sxs-lookup"><span data-stu-id="c94be-120">You receive the token in `OnTeamsMessagingExtensionQueryAsync` handler in the `turnContext.Activity.Value` payload or in the `OnTeamsAppBasedLinkQueryAsync`, depending on which scenario you are enabling the SSO for:</span></span>

    ```json
    JObject valueObject=JObject.FromObject(turnContext.Activity.Value);
    if(valueObject["authentication"] !=null)
     {
        JObject authenticationObject=JObject.FromObject(valueObject["authentication"]);
        if(authenticationObject["token"] !=null)
     }
    
     ```
  
    <span data-ttu-id="c94be-121">Wenn Sie die OAuth-Verbindung verwenden, fügen Sie der Datei TeamsMessagingExtensionsSearchAuthConfigBot.cs den folgenden Code hinzu, um das Token im Store zu aktualisieren oder hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="c94be-121">If you are using the OAuth connection, add the following code to the TeamsMessagingExtensionsSearchAuthConfigBot.cs file to update or add the token in the store:</span></span>
    
   ```C#
   protected override async Task<InvokeResponse> OnInvokeActivityAsync(ITurnContext<IInvokeActivity> turnContext, CancellationToken cancellationToken)
        {
            JObject valueObject = JObject.FromObject(turnContext.Activity.Value);
            if (valueObject["authentication"] != null)
            {
                JObject authenticationObject = JObject.FromObject(valueObject["authentication"]);
                if (authenticationObject["token"] != null)
                {
                    //If the token is NOT exchangeable, then return 412 to require user consent
                    if (await TokenIsExchangeable(turnContext, cancellationToken))
                    {
                        return await base.OnInvokeActivityAsync(turnContext, cancellationToken).ConfigureAwait(false);
                    }
                    else
                    {
                        var response = new InvokeResponse();
                        response.Status = 412;
                        return response;
                    }
                }
            }
            return await base.OnInvokeActivityAsync(turnContext, cancellationToken).ConfigureAwait(false);
        }
        private async Task<bool> TokenIsExchangeable(ITurnContext turnContext, CancellationToken cancellationToken)
        {
            TokenResponse tokenExchangeResponse = null;
            try
            {
                JObject valueObject = JObject.FromObject(turnContext.Activity.Value);
                var tokenExchangeRequest =
                ((JObject)valueObject["authentication"])?.ToObject<TokenExchangeInvokeRequest>();
                tokenExchangeResponse = await (turnContext.Adapter as IExtendedUserTokenProvider).ExchangeTokenAsync(
                 turnContext,
                 _connectionName,
                 turnContext.Activity.From.Id,
                 new TokenExchangeRequest
                 {
                     Token = tokenExchangeRequest.Token,
                 },
                 cancellationToken).ConfigureAwait(false);
            }
    #pragma warning disable CA1031 //Do not catch general exception types (ignoring, see comment below)
            catch
    #pragma warning restore CA1031 //Do not catch general exception types
            {
                //ignore exceptions
                //if token exchange failed for any reason, tokenExchangeResponse above remains null, and a failure invoke response is sent to the caller.
                //This ensures the caller knows that the invoke has failed.
            }
            if (tokenExchangeResponse == null || string.IsNullOrEmpty(tokenExchangeResponse.Token))
            {
                return false;
            }
            return true;
        }
    
    ```    

## <a name="see-also"></a><span data-ttu-id="c94be-122">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="c94be-122">See also</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c94be-123">Hinzufügen der Authentifizierung zu Ihren Messagingerweiterungen</span><span class="sxs-lookup"><span data-stu-id="c94be-123">Add authentication to your messaging extensions</span></span>](add-authentication.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="c94be-124">Verwenden von SSO für Bots</span><span class="sxs-lookup"><span data-stu-id="c94be-124">Use SSO for bots</span></span>](../../bots/how-to/authentication/auth-aad-sso-bots.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="c94be-125">Entfalten von Links</span><span class="sxs-lookup"><span data-stu-id="c94be-125">Link unfurling</span></span>](link-unfurling.md)

