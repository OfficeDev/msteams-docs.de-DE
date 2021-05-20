---
title: SSO-Unterstützung für Ihre Messaging-Erweiterungen
author: KirtiPereira
description: So aktivieren Sie die SSO-Unterstützung für Ihre Messaging-Erweiterungen
localization_priority: Normal
ms.topic: conceptual
ms.author: surbhigupta
ms.openlocfilehash: 02d08506a07e955693531908f4f3cf16573a02c0
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566201"
---
# <a name="single-sign-on-sso-support-for-messaging-extensions"></a>SSO-Unterstützung (Single Sign-On) für Messagingerweiterungen
 
Single Sign-On-Unterstützung ist jetzt für Messaging-Erweiterungen und Link-Entfurling verfügbar. Wenn Sie Single Sign-On (SSO) für Messagingerweiterungen aktivieren, wird das Authentifizierungstoken automatisch aktualisiert, wodurch die Anzahl der Anmeldeinformationen für Microsoft Teams minimiert wird.

In diesem Dokument erfahren Sie, wie Sie das SSO aktivieren und bei Bedarf Ihr Authentifizierungstoken speichern.

## <a name="prerequisites"></a>Voraussetzungen

Die Voraussetzung für die Aktivierung von SSO für Messagingerweiterungen und die Entfaltung der Verknüpfung ist wie folgt:
* Sie müssen über ein [Azure-Konto](https://azure.microsoft.com/en-us/free/) verfügen.
* Sie müssen Ihre App über das AAD-Portal konfigurieren und Ihr Teams Anwendungsmanifest für Ihren Bot aktualisieren, wie in [Registrieren Ihrer App über das AAD-Portal](../../bots/how-to/authentication/auth-aad-sso-bots.md#register-your-app-through-the-aad-portal)definiert.

> [!NOTE]
> Weitere Informationen zum Erstellen eines Azure-Kontos und zum Aktualisieren Ihres App-Manifests finden Sie unter [SSO-Unterstützung (Single Sign-On) für Bots](../../bots/how-to/authentication/auth-aad-sso-bots.md).

## <a name="enable-sso-for-messaging-extensions-and-link-unfurling"></a>Aktivieren von SSO für Messaging-Erweiterungen und Verbindungsentflechtung

Nachdem die Voraussetzungen erfüllt sind, können Sie SSO für Messagingerweiterungen und die Entfurtung der Verknüpfung aktivieren.

**So aktivieren Sie SSO**
1. Aktualisieren Sie Ihre [OAuth-Verbindungsdetails](../../bots/how-to/authentication/auth-aad-sso-bots.md#update-the-azure-portal-with-the-oauth-connection) für Bots im Azure-Portal.
2. Laden Sie das Beispiel für [Messagingerweiterungen herunter,](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config) und befolgen Sie die vom Assistenten bereitgestellten Setupanweisungen.
   > [!NOTE]
   > Verwenden Sie Ihre Bots OAuth-Verbindung beim Einrichten Ihrer Messaging-Erweiterungen.
3. Aktualisieren Sie in der Datei [TeamsMessagingExtensionsSearchAuthConfigBot.cs](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config/Bots/TeamsMessagingExtensionsSearchAuthConfigBot.cs) den Wert von *auth* auf *silentAuth* in `OnTeamsMessagingExtensionQueryAsync` und/ oder `OnTeamsAppBasedLinkQueryAsync` .  

    > [!NOTE]
    > Andere Handler SSO werden nicht unterstützt, außer `OnTeamsMessagingExtensionQueryAsync` und aus der Datei `OnTeamsAppBasedLinkQueryAsync` TeamsMessagingExtensionsSearchAuthConfigBot.cs.
   
4. Sie erhalten das Token im `OnTeamsMessagingExtensionQueryAsync` Handler in der `turnContext.Activity.Value` Nutzlast oder im `OnTeamsAppBasedLinkQueryAsync` , je nachdem, für welches Szenario Sie das SSO aktivieren:

    ```json
    JObject valueObject=JObject.FromObject(turnContext.Activity.Value);
    if(valueObject["authentication"] !=null)
     {
        JObject authenticationObject=JObject.FromObject(valueObject["authentication"]);
        if(authenticationObject["token"] !=null)
     }
    
     ```
  
    Wenn Sie die OAuth-Verbindung verwenden, fügen Sie dem TeamsMessagingExtensionsSearchAuthConfigBot den folgenden Code hinzu.cs Datei, um das Token im Speicher zu aktualisieren oder hinzuzufügen:
    
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

## <a name="see-also"></a>Siehe auch

* [Hinzufügen von Authentifizierung zu Ihren Messagingerweiterungen](add-authentication.md)
* [Verwenden von SSO für Bots](../../bots/how-to/authentication/auth-aad-sso-bots.md)
* [Entfalten von Links](link-unfurling.md)

