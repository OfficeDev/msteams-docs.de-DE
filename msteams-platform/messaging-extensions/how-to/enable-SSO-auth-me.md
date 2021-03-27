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
# <a name="single-sign-on-sso-support-for-messaging-extensions"></a>Unterstützung für einmaliges Anmelden (Single Sign-On, SSO) für Messagingerweiterungen
 
Die Unterstützung für einmaliges Anmelden ist jetzt für Messagingerweiterungen und die Verknüpfungsentfurling verfügbar. Wenn Sie einmaliges Anmelden (Single Sign-On, SSO) für Messagingerweiterungen aktivieren, wird das Authentifizierungstoken automatisch aktualisiert, wodurch die Anzahl der Anmeldeinformationen für Microsoft Teams minimiert wird.

In diesem Dokument erfahren Sie, wie Sie den SSO aktivieren und Ihr Authentifizierungstoken bei Bedarf speichern.

## <a name="prerequisites"></a>Voraussetzungen

Die Voraussetzungen für die Aktivierung von SSO für Messagingerweiterungen und das Entf?nden von Links sind wie folgt:
* Sie müssen über ein [Azure-Konto](https://azure.microsoft.com/en-us/free/) verfügen.
* Sie müssen Ihre App über das AAD-Portal konfigurieren und Ihr Teams-Anwendungsmanifest für Ihren Bot aktualisieren, wie in der Registrierung Ihrer App über [das AAD-Portal definiert.](../../bots/how-to/authentication/auth-aad-sso-bots.md#register-your-app-through-the-aad-portal)

> [!NOTE]
> Weitere Informationen zum Erstellen eines Azure-Kontos und zum Aktualisieren Ihres App-Manifests finden Sie unter [Single Sign-On (SSO) support for bots](../../bots/how-to/authentication/auth-aad-sso-bots.md).

## <a name="enable-sso-for-messaging-extensions-and-link-unfurling"></a>Aktivieren von SSO für Messagingerweiterungen und Entfurling von Verknüpfungen

Nachdem die voraussetzungen erfüllt sind, können Sie SSO für Messagingerweiterungen aktivieren und die Verknüpfungsentfings aktivieren.

**So aktivieren Sie SSO**
1. Aktualisieren Sie Ihre [Bots-OAuth-Verbindungsdetails](../../bots/how-to/authentication/auth-aad-sso-bots.md#update-the-azure-portal-with-the-oauth-connection) im Azure-Portal.
2. Laden Sie das [Beispiel für Messagingerweiterungen herunter,](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config) und befolgen Sie die Vom Assistenten bereitgestellten Setupanweisungen.
   > [!NOTE]
   > Verwenden Sie ihre Bots-OAuth-Verbindung, wenn Sie Ihre Messagingerweiterungen einrichten.
3. Aktualisieren Sie in der [Datei TeamsMessagingExtensionsSearchAuthConfigBot.cs](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config/Bots/TeamsMessagingExtensionsSearchAuthConfigBot.cs) den Wert von *auth* auf *silentAuth* im `OnTeamsMessagingExtensionQueryAsync` und/oder `OnTeamsAppBasedLinkQueryAsync` .  

    > [!NOTE]
    > Wir unterstützen keine anderen Handler-SSO, außer und aus der `OnTeamsMessagingExtensionQueryAsync` `OnTeamsAppBasedLinkQueryAsync` Datei TeamsMessagingExtensionsSearchAuthConfigBot.cs.
   
4. Sie erhalten das Token im Handler in der Nutzlast oder im , je nachdem, welches Szenario Sie für das `OnTeamsMessagingExtensionQueryAsync` `turnContext.Activity.Value` `OnTeamsAppBasedLinkQueryAsync` SSO aktivieren:

    ```json
    JObject valueObject=JObject.FromObject(turnContext.Activity.Value);
    if(valueObject["authentication"] !=null)
     {
        JObject authenticationObject=JObject.FromObject(valueObject["authentication"]);
        if(authenticationObject["token"] !=null)
     }
    
     ```
  
    Wenn Sie die OAuth-Verbindung verwenden, fügen Sie der Datei TeamsMessagingExtensionsSearchAuthConfigBot.cs den folgenden Code hinzu, um das Token im Store zu aktualisieren oder hinzuzufügen:
    
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

## <a name="see-also"></a>Weitere Informationen

> [!div class="nextstepaction"]
> [Hinzufügen der Authentifizierung zu Ihren Messagingerweiterungen](add-authentication.md)

> [!div class="nextstepaction"]
> [Verwenden von SSO für Bots](../../bots/how-to/authentication/auth-aad-sso-bots.md)

> [!div class="nextstepaction"]
> [Entfalten von Links](link-unfurling.md)

