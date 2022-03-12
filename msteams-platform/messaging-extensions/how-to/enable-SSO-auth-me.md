---
title: SSO-Unterstützung für Ihre Messaging-Erweiterungen
author: KirtiPereira
description: Erfahren Sie, wie Sie die SSO-Unterstützung für Ihre Messaging-Erweiterungen mit Codebeispielen aktivieren.
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: surbhigupta
ms.openlocfilehash: 3543d86d15755642a1617e07514db95a6a812313
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2022
ms.locfileid: "63453467"
---
# <a name="single-sign-on-support-for-messaging-extensions"></a>Unterstützung für einmaliges Anmelden für Messaging-Erweiterungen

SSO-Unterstützung (Single Sign-On) ist jetzt für Messaging-Erweiterungen und die Verbreitung von Links verfügbar. Wenn Sie das einmalige Anmelden für Messaging-Erweiterungen standardmäßig aktivieren, wird das Authentifizierungstoken aktualisiert, wodurch die Anzahl der Eingaben der Anmeldeinformationen für Microsoft Teams minimiert wird.

In diesem Dokument erfahren Sie, wie Sie das SSO aktivieren und Bei Bedarf Ihr Authentifizierungstoken speichern.

## <a name="prerequisites"></a>Voraussetzungen

Die Voraussetzungen zum Aktivieren von SSO für Messaging-Erweiterungen und die Verbreitung von Links sind wie folgt:

* Sie benötigen ein [Azure-Konto](https://azure.microsoft.com/free/) .
* Sie müssen Ihre App über das Azure AD-Portal konfigurieren und Teams Anwendungsmanifest Ihres Bots aktualisieren, wie in [der Registrierung Ihrer App über das Azure AD-Portal](../../bots/how-to/authentication/auth-aad-sso-bots.md#register-your-app-through-the-azure-ad-portal) definiert.

> [!NOTE]
> Weitere Informationen zum Erstellen eines Azure-Kontos und aktualisieren Ihres [App-Manifests finden Sie unter SSO-Unterstützung (Single Sign-On) für Bots](../../bots/how-to/authentication/auth-aad-sso-bots.md).

## <a name="enable-sso-for-messaging-extensions-and-link-unfurling"></a>Aktivieren von SSO für Messaging-Erweiterungen und Die Verbreitung von Links

Nachdem die Voraussetzungen erfüllt sind, können Sie SSO für Messaging-Erweiterungen und die Verbreitung von Links aktivieren.

So aktivieren Sie SSO:

1. Aktualisieren Sie ihre [OAuth-Verbindungsdetails](../../bots/how-to/authentication/auth-aad-sso-bots.md#update-the-azure-portal-with-the-oauth-connection) für Bots im Microsoft Azure Portal.
2. Laden Sie das [Beispiel für Messaging-Erweiterungen herunter](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config) , und folgen Sie den Setupanweisungen des Assistenten.
   > [!NOTE]
   > Verwenden Sie Ihre Bots-OAuth-Verbindung beim Einrichten Ihrer Messaging-Erweiterungen.
3. Aktualisieren Sie in der Datei ["TeamsMessagingExtensionsSearchAuthConfigBot.cs](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config/Bots/TeamsMessagingExtensionsSearchAuthConfigBot.cs) " den Wert von *"auth* " in *"silentAuth* " im `OnTeamsMessagingExtensionQueryAsync` und/oder `OnTeamsAppBasedLinkQueryAsync`.  

    > [!NOTE]
    > Wir unterstützen keine anderen Handler SSO, mit Ausnahme `OnTeamsMessagingExtensionQueryAsync` `OnTeamsAppBasedLinkQueryAsync` der Datei "TeamsMessagingExtensionsSearchAuthConfigBot.cs".

4. Sie erhalten das Token im `OnTeamsMessagingExtensionQueryAsync` Handler in der `turnContext.Activity.Value` Nutzlast oder im `OnTeamsAppBasedLinkQueryAsync`, je nachdem, für welches Szenario Sie SSO aktivieren:

    ```json
    JObject valueObject=JObject.FromObject(turnContext.Activity.Value);
    if(valueObject["authentication"] !=null)
     {
        JObject authenticationObject=JObject.FromObject(valueObject["authentication"]);
        if(authenticationObject["token"] !=null)
     }
    
     ```
  
    Wenn Sie die OAuth-Verbindung verwenden, fügen Sie den folgenden Code zur Datei "TeamsMessagingExtensionsSearchAuthConfigBot.cs" hinzu, um das Token im Speicher zu aktualisieren oder hinzuzufügen:

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
                var userTokenClient = turnContext.TurnState.Get<UserTokenClient>();
                tokenExchangeResponse = await userTokenClient.ExchangeTokenAsync(
                                turnContext.Activity.From.Id,
                                 _connectionName,
                                 turnContext.Activity.ChannelId,
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
