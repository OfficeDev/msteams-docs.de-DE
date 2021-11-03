---
title: SSO-Unterstützung für Ihre Messaging-Erweiterungen
author: KirtiPereira
description: So aktivieren Sie die SSO-Unterstützung für Ihre Messaging-Erweiterungen
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: surbhigupta
ms.openlocfilehash: fb9f323b81ff6e42e0ae78bc2bb476b629bfb206
ms.sourcegitcommit: 22c9e44437720d30c992a4a3626a2a9f745983c1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2021
ms.locfileid: "60720057"
---
# <a name="single-sign-on-support-for-messaging-extensions"></a>Unterstützung für einmaliges Anmelden für Messaging-Erweiterungen
 
SSO-Unterstützung (Single Sign-On) ist jetzt für Messaging-Erweiterungen und die Verbreitung von Links verfügbar. Wenn Sie das einmalige Anmelden für Messaging-Erweiterungen standardmäßig aktivieren, wird das Authentifizierungstoken aktualisiert. Dadurch wird minimiert, wie oft Sie die Anmeldeinformationen für Microsoft Teams eingeben müssen.

In diesem Dokument erfahren Sie, wie Sie das SSO aktivieren und Bei Bedarf Ihr Authentifizierungstoken speichern.

## <a name="prerequisites"></a>Voraussetzungen

Die Voraussetzungen zum Aktivieren von SSO für Messaging-Erweiterungen und die Verbreitung von Links sind wie folgt:
* Sie benötigen [](https://azure.microsoft.com/free/) ein Azure-Konto.
* Sie müssen Ihre App über das AAD Portal konfigurieren und Teams Anwendungsmanifest Ihres Bots aktualisieren, wie in [der Registrierung Ihrer App über das AAD-Portal](../../bots/how-to/authentication/auth-aad-sso-bots.md#register-your-app-through-the-aad-portal)definiert.

> [!NOTE]
> Weitere Informationen zum Erstellen eines Azure-Kontos und aktualisieren Ihres App-Manifests finden Sie unter [SSO-Unterstützung (Single Sign-On) für Bots.](../../bots/how-to/authentication/auth-aad-sso-bots.md)

## <a name="enable-sso-for-messaging-extensions-and-link-unfurling"></a>Aktivieren von SSO für Messaging-Erweiterungen und Die Verbreitung von Links

Nachdem die Voraussetzungen erfüllt sind, können Sie SSO für Messaging-Erweiterungen und die Verbreitung von Links aktivieren.

**So aktivieren Sie SSO**
1. Aktualisieren Sie Ihre [OAuth-Verbindungsdetails](../../bots/how-to/authentication/auth-aad-sso-bots.md#update-the-azure-portal-with-the-oauth-connection) für Bots im Azure-Portal.
2. Laden Sie das [Beispiel für Messaging-Erweiterungen herunter,](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config) und folgen Sie den Setupanweisungen des Assistenten.
   > [!NOTE]
   > Verwenden Sie Ihre Bots-OAuth-Verbindung beim Einrichten Ihrer Messaging-Erweiterungen.
3. Aktualisieren Sie in der Datei ["TeamsMessagingExtensionsSearchAuthConfigBot.cs"](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config/Bots/TeamsMessagingExtensionsSearchAuthConfigBot.cs) den Wert von *"auth"* in *"silentAuth"* im `OnTeamsMessagingExtensionQueryAsync` und/oder `OnTeamsAppBasedLinkQueryAsync` .  

    > [!NOTE]
    > Wir unterstützen keine anderen Handler SSO, mit Ausnahme `OnTeamsMessagingExtensionQueryAsync` `OnTeamsAppBasedLinkQueryAsync` der Datei "TeamsMessagingExtensionsSearchAuthConfigBot.cs".
   
4. Sie erhalten das Token im `OnTeamsMessagingExtensionQueryAsync` Handler in der Nutzlast oder im , je `turnContext.Activity.Value` `OnTeamsAppBasedLinkQueryAsync` nachdem, für welches Szenario Sie SSO aktivieren:

    ```json
    JObject valueObject=JObject.FromObject(turnContext.Activity.Value);
    if(valueObject["authentication"] !=null)
     {
        JObject authenticationObject=JObject.FromObject(valueObject["authentication"]);
        if(authenticationObject["token"] !=null)
     }
    
     ```
  
    Wenn Sie die OAuth-Verbindung verwenden, fügen Sie der Datei "TeamsMessagingExtensionsSearchAuthConfigBot.cs" den folgenden Code hinzu, um das Token im Speicher zu aktualisieren oder hinzuzufügen:
    
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

* [Hinzufügen der Authentifizierung zu Ihren Messaging-Erweiterungen](add-authentication.md)
* [Verwenden von SSO für Bots](../../bots/how-to/authentication/auth-aad-sso-bots.md)
* [Verbreiten von Links](link-unfurling.md)

