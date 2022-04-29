---
title: SSO-Unterstützung für Ihre Nachrichtenerweiterungen
author: KirtiPereira
description: Erfahren Sie, wie Sie die SSO-Unterstützung für Ihre Messaging-Erweiterungen mit Codebeispielen aktivieren.
ms.localizationpriority: high
ms.topic: conceptual
ms.author: surbhigupta
ms.openlocfilehash: 148e8c59acc520e7771ac23c38b4b17c43d4d74d
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111255"
---
# <a name="single-sign-on-support-for-message-extensions"></a>Unterstützung für einmaliges Anmelden für Nachrichtenerweiterungen

Die Unterstützung für Single Sign-On (SSO) ist jetzt auch für Nachrichtenerweiterungen und die Entfaltung von Links verfügbar. Durch die standardmäßige Aktivierung von Single Sign-On für Nachrichtenerweiterungen wird das Authentifizierungs-Token aktualisiert, wodurch die Anzahl der erforderlichen Eingaben der Anmeldedaten für Microsoft Teams minimiert wird.

In diesem Dokument erfahren Sie, wie Sie den SSO aktivieren und Ihr Authentifizierungstoken bei Bedarf speichern.

## <a name="prerequisites"></a>Voraussetzungen

Die Voraussetzung für die Aktivierung von SSO für Nachrichtenerweiterungen und die Verbreitung von Links lautet wie folgt:

* Sie müssen über ein [Azure-Konto](https://azure.microsoft.com/free/) verfügen.
* Sie müssen Ihre App über das Azure AD-Portal konfigurieren und Teams Anwendungsmanifest ihres Bots aktualisieren, wie in [der Registrierung Ihrer App über das Azure AD-Portal](../../bots/how-to/authentication/auth-aad-sso-bots.md#register-your-app-through-the-azure-ad-portal) definiert.

> [!NOTE]
> Weitere Informationen zum Erstellen eines Azure-Kontos und aktualisieren Ihres App-Manifests finden Sie unter [SSO-Unterstützung (Single Sign-On) für Bots](../../bots/how-to/authentication/auth-aad-sso-bots.md).

## <a name="enable-sso-for-message-extensions-and-link-unfurling"></a>Aktivieren von SSO für Nachrichtenerweiterungen und Die Verbreitung von Links

Nachdem die Voraussetzungen erfüllt sind, können Sie SSO für Nachrichtenerweiterungen und die Verbreitung von Links aktivieren.

So aktivieren Sie SSO:

1. Aktualisieren Sie die [OAuth-Verbindungs](../../bots/how-to/authentication/auth-aad-sso-bots.md#update-the-azure-portal-with-the-oauth-connection)Details Ihrer Bots im Microsoft Azure Portal.
2. Laden Sie das [Beispiel für Nachrichtenerweiterungen](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config) herunter, und folgen Sie den Setupanweisungen des Assistenten.
   > [!NOTE]
   > Verwenden Sie ihre OAuth-Verbindung für Bots, wenn Sie Ihre Nachrichtenerweiterungen einrichten.
3. Aktualisieren Sie in der Datei [TeamsMessagingExtensionsSearchAuthConfigBot.cs](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config/Bots/TeamsMessagingExtensionsSearchAuthConfigBot.cs) den Wert von *auth* auf *silentAuth* in den Feldern `OnTeamsMessagingExtensionQueryAsync` und / oder `OnTeamsAppBasedLinkQueryAsync`.  

    > [!NOTE]
    > Wir unterstützen keine anderen Handler SSO, außer `OnTeamsMessagingExtensionQueryAsync` und `OnTeamsAppBasedLinkQueryAsync` aus der TeamsMessagingExtensionsSearchAuthConfigBot.cs-Datei.

4. Sie erhalten das Token im `OnTeamsMessagingExtensionQueryAsync` Handler in der `turnContext.Activity.Value` Nutzlast oder in dem `OnTeamsAppBasedLinkQueryAsync`, je nachdem, für welches Szenario Sie das SSO aktivieren für:

    ```json
    JObject valueObject=JObject.FromObject(turnContext.Activity.Value);
    if(valueObject["authentication"] !=null)
     {
        JObject authenticationObject=JObject.FromObject(valueObject["authentication"]);
        if(authenticationObject["token"] !=null)
     }
    
     ```
  
    Wenn Sie die OAuth-Verbindung verwenden, fügen Sie den folgenden Code in die Datei TeamsMessagingExtensionsSearchAuthConfigBot.cs ein, um das Token im Speicher zu aktualisieren oder hinzuzufügen:

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

* [Hinzufügen der Authentifizierung zu Ihren Nachrichtenerweiterungen](add-authentication.md)
* [Verwenden von SSO für Bots](../../bots/how-to/authentication/auth-aad-sso-bots.md)
* [Verbreiten von Links](link-unfurling.md)
