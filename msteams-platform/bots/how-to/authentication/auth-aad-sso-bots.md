---
title: Unterstützung für einmaliges Anmelden für Bots
description: Beschreibt, wie ein Benutzertoken abgerufen wird. Derzeit kann ein bot-Entwickler eine Anmeldekarte oder den Azure bot-Dienst mit der OAuth-Kartenunterstützung verwenden.
keywords: Token, Benutzertoken, SSO-Unterstützung für Bots
ms.openlocfilehash: 0b896f7e13847f529075b5562a6c3eb2542482bf
ms.sourcegitcommit: df9448681d2a81f1029aad5a5e1989cd438d1ae0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2020
ms.locfileid: "48877850"
---
# <a name="single-sign-on-sso-support-for-bots"></a>Unterstützung für einmaliges Anmelden (SSO) für Bots

Authentifizierung mit einmaligem Anmelden in Azure Active Directory (Azure AD) minimiert, wie oft Benutzer ihre Anmeldeinformationen eingeben müssen, indem Sie das Authentifizierungstoken automatisch aktualisieren. Wenn Benutzer einwilligen, Ihre APP zu verwenden, müssen Sie nicht erneut auf einem anderen Gerät zustimmen und werden automatisch angemeldet. Der Fluss ähnelt der [SSO-Unterstützung der Teams-Registerkarte]( ../../../tabs/how-to/authentication/auth-aad-sso.md). Der Unterschied ist das Protokoll dafür, wie ein bot Token anfordert und Antworten erhält.

OAuth 2.0 ist ein offener Standard für Authentifizierung und Autorisierung, der von Azure Active Directory (Azure AD) und vielen anderen Identitätsanbietern verwendet wird. Ein grundlegendes Verständnis von OAuth 2,0 ist eine Voraussetzung für die Verwendung von Authentifizierung in Microsoft Teams.

## <a name="bot-sso-at-runtime"></a>Bot-SSO zur Laufzeit

![Bot-SSO im laufzeitdiagramm](../../../assets/images/bots/bots-sso-diagram.png)

1. Der bot sendet eine Nachricht mit einem OAuthCard, das die `tokenExchangeResource` Eigenschaft enthält. Es weist Microsoft Teams an, ein Authentifizierungstoken für die bot-Anwendung zu erhalten. Der Benutzer empfängt Nachrichten an allen aktiven Endpunkten des Benutzers.

> [!NOTE]
> ✔ Ein Benutzer gleichzeitig mehr als einen aktiven Endpunkt haben kann.  
> ✔ Das bot-Token von jedem aktiven Endpunkt des Benutzers empfangen wird.
> Bei ✔ Unterstützung für einmaliges Anmelden muss die APP derzeit im persönlichen Bereich installiert werden.

2. Wenn der aktuelle Benutzer ihre bot-Anwendung zum ersten Mal verwendet hat, wird eine Anforderungs Aufforderung zur Zustimmung (sofern Zustimmung erforderlich ist) oder zur Behandlung der Step-up-Authentifizierung (beispielsweise zweistufige Authentifizierung) angezeigt.

3. Microsoft Teams fordert das bot-Anwendungs Token vom Azure AD-Endpunkt für den aktuellen Benutzer an.

4. Azure AD sendet das bot-Anwendungs Token an die Teams-Anwendung.

5. Microsoft Teams sendet das Token an den bot als Teil des Value-Objekts, das von der Invoke-Aktivität mit dem Namen Sign-in/tokenExchange zurückgegeben wird.
  
6. Das Token wird in der bot-Anwendung analysiert, um die erforderlichen Informationen zu extrahieren, beispielsweise die e-Mail-Adresse des Benutzers.
  
## <a name="develop-an-single-sign-on-microsoft-teams-bot"></a>Entwickeln eines Single Sign-on Microsoft Teams-bot
  
Die folgenden Schritte sind erforderlich, um einen SSO-Microsoft Teams-bot zu entwickeln:

1. [Erstellen eines kostenlosen Azure-Kontos](#create-an-azure-account)
2. [Aktualisieren des Teams-App-Manifests](#update-your-app-manifest)
3. [Hinzufügen des Codes zum Anfordern und empfangen des bot-Tokens](#request-a-bot-token)

### <a name="create-an-azure-account"></a>Erstellen eines Azure-Kontos

Dieser Schritt ähnelt dem [Durchfluss der Registerkarte SSO](../../../tabs/how-to/authentication/auth-aad-sso.md) :

1. Rufen Sie Ihre [Azure AD-Anwendungs-ID](/azure/active-directory/develop/howto-create-service-principal-portal#get-values-for-signing-in)ab.
2. Geben Sie die Berechtigungen an, die Ihre Anwendung für den Azure AD-Endpunkt und optional für Microsoft Graph benötigt.
3. [Erteilen von Berechtigungen](/azure/active-directory/develop/howto-create-service-principal-portal#configure-access-policies-on-resources) für Desktop-, Webanwendungen und Mobile Microsoft Teams-Anwendungen
4. Vorautorisieren von Teams durch Auswählen der Schaltfläche **Bereich hinzufügen** und Eingeben des `access_as_user` **Bereichsnamens** in das geöffnete Fenster.

> [!IMPORTANT]
> * Wenn Sie einen eigenständigen bot erstellen, legen Sie den Anwendungs-ID-URI auf fest `api://botid-{YourBotId}` .
> * Wenn Sie eine APP mit einem bot und einer RegisterkarteErstellen, legen Sie den Anwendungs-ID-URI auf fest `api://fully-qualified-domain-name.com/botid-{YourBotId}` .

### <a name="update-your-app-manifest"></a>Aktualisieren des App-Manifests

Fügen Sie Ihrem Microsoft Teams-Manifest neue Eigenschaften hinzu:

**WebApplicationInfo** -das übergeordnete Element der folgenden Elemente:

> [!div class="checklist"]
>
> * **ID** – die Client-ID der Anwendung. Dies ist die Anwendungs-ID, die Sie im Rahmen der Registrierung der Anwendung mit Azure AD erhalten haben.
>* **Resource** – die Domäne und Unterdomäne Ihrer Anwendung. Hierbei handelt es sich um denselben URI (einschließlich des `api://` Protokolls), den Sie bei der Erstellung Ihres `scope` in Schritt 6 oben registriert haben. Sie sollten den `access_as_user` Pfad nicht in Ihre Ressource einschließen. Der Domänenteil dieses URIs sollte der Domäne entsprechen, einschließlich aller Unterdomänen, die in den URLs Ihres Teams-Anwendungsmanifests verwendet werden.

```json
"webApplicationInfo": {
  "id": "00000000-0000-0000-0000-000000000000",
  "resource": "api://subdomain.example.com/00000000-0000-0000-0000-000000000000"
}
```

### <a name="request-a-bot-token"></a>Anfordern eines bot-Tokens

Die Anforderung zum Abrufen des Tokens ist eine normale Post-Nachrichtenanforderung (unter Verwendung des vorhandenen Nachrichtenschemas). Sie ist in den Anlagen eines OAuthCard enthalten. Das Schema für die OAuthCard-Klasse ist im [Microsoft-bot-Schema 4,0](/dotnet/api/microsoft.bot.schema.oauthcard?view=botbuilder-dotnet-stable&preserve-view=true) definiert und ähnelt einer Anmeldekarte. Diese Anforderung wird von Microsoft Teams als automatische Token-Übernahme behandelt, wenn die `TokenExchangeResource` Eigenschaft auf der Karte aufgefüllt ist. Für den Teams-Kanal honorieren wir nur die `Id` Eigenschaft, die eine Token-Anforderung eindeutig identifiziert.

Wenn der Benutzer Ihre Anwendung zum ersten Mal verwendet und die Zustimmung des Benutzers erforderlich ist, wird dem Benutzer ein Dialogfeld angezeigt, in dem die Zustimmungs Erfahrung ähnlich wie unten fortgesetzt werden kann. Wenn der Benutzer **Continue** auswählt, treten zwei verschiedene Dinge auf, je nachdem, ob der bot definiert ist oder nicht, und eine Anmeldeschaltfläche auf dem OAuthCard.

![Dialogfeld Zustimmung](../../../assets/images/bots/bots-consent-dialogbox.png)

Wenn der bot eine Anmeldeschaltfläche definiert, wird der Anmelde Fluss für Bots ähnlich dem Anmelde Fluss von einer kartenschaltfläche in einem Nachrichtendatenstrom ausgelöst. Es liegt an dem Entwickler, zu entscheiden, welche Berechtigungen für den Benutzer erteilt werden sollen, um ihn zu genehmigen. Dieser Ansatz wird empfohlen, wenn Sie ein Token mit Berechtigungen darüber hinaus benötigen `openId` , beispielsweise wenn Sie das Token für Graph-Ressourcen austauschen möchten.

Wenn der bot keine Anmeldeschaltfläche auf der Karte bereitstellt, wird die Benutzer Zustimmung für einen minimalen Satz von Berechtigungen ausgelöst. Dieses Token eignet sich für die Standardauthentifizierung und das erhalten der e-Mail-Adresse des Benutzers.

**C#-Token-Anforderung ohne Anmeldeschaltfläche** :

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

#### <a name="receiving-the-token"></a>Empfangen des Tokens

Die Antwort mit dem Token wird über eine Invoke-Aktivität mit dem gleichen Schema gesendet wie andere Aktivitäten aufrufen, die die Bots heute empfangen. Der einzige Unterschied besteht darin, dass der Aufruf Name, die **Anmelde-tokenExchange** und das **Wertfeld** die **ID** (eine Zeichenfolge) der anfänglichen Anforderung zum Abrufen des Tokens und des **Token** -Felds (ein Zeichenfolgenwert einschließlich des Tokens) enthalten wird. Beachten Sie, dass Sie möglicherweise mehrere Antworten für eine bestimmte Anforderung erhalten, wenn der Benutzer über mehrere aktive Endpunkte verfügt. Es liegt an Ihnen, die Antworten mit dem Token zu deduplizieren.

**C#-Code zur Reaktion auf die Behandlung der Invoke-Aktivität** :

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

Die `turnContext.activity.value` ist vom Typ [TokenExchangeInvokeRequest](/dotnet/api/microsoft.bot.schema.tokenexchangeinvokerequest?view=botbuilder-dotnet-stable&preserve-view=true) und enthält das Token, das von Ihrem bot weiter verwendet werden kann. Speichern Sie die Token aus Leistungsgründen sicher, und aktualisieren Sie Sie.

### <a name="update-the-azure-portal-with-the-oauth-connection"></a>Aktualisieren des Azure-Portals mit der OAuth-Verbindung

1. Navigieren Sie im Azure-Portal zurück zur **Registrierung für bot-Kanäle**.

2. Wechseln Sie zum Blade " **Einstellungen** ", und wählen Sie im Abschnitt OAuth-Verbindungseinstellungen die Option **Hinzufügen** .

![SSOBotHandle2-Ansicht](../../../assets/images/bots/bots-vuSSOBotHandle2-settings.png)

3. Schließen Sie das Formular für die **Verbindungseinstellung** ab:

> [!div class="checklist"]
>
> * Geben Sie einen Namen für die neue Verbindungseinstellung ein. Dies ist der Name, auf den innerhalb der Einstellungen Ihres bot-Dienstcodes in **Schritt 5** verwiesen wird.
> * Wählen Sie in der Dropdownliste Dienstanbieter die Option **Azure Active Directory v2** aus.
>* Geben Sie die Clientanmeldeinformationen für die Aad-Anwendung ein.
>* Verwenden Sie für die Token-Exchange-URL den Bereichswert, der im vorherigen Schritt ihrer Aad-Anwendung definiert wurde. Das vorhanden sein der Token-Exchange-URL zeigt dem SDK an, dass diese Aad-Anwendung für SSO konfiguriert ist.
>* Geben Sie "Common" als **Mandanten-ID** an.
>* Fügen Sie alle Bereiche hinzu, die beim Angeben von Berechtigungen für Downstream-APIs für Ihre Aad-Anwendung konfiguriert wurden. Wenn die Client-ID und der geheime Client Schlüssel bereitgestellt werden, tauschen Tokenspeicher das Token für ein Diagramm Token mit definierten Berechtigungen für Sie aus.
>* Wählen Sie **Speichern** aus.

![VuSSOBotConnection-Einstellungsansicht](../../../assets/images/bots/bots-vuSSOBotConnection-settings.png)

### <a name="update-the-auth-sample"></a>Aktualisieren des Authentifizierungs Beispiels

Beginnen Sie mit dem Microsoft [Teams-Authentifizierungs Beispiel](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth).

1. Aktualisieren Sie die TeamsBot, um Folgendes einzuschließen. Informationen zum Verarbeiten des deduping der eingehenden Anforderung finden Sie weiter unten:

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
  
2. Aktualisieren Sie das, `appsettings.json` um das `botId` obige, Kennwort und den oben definierten Verbindungsnamen einzubeziehen.
3. Aktualisieren Sie das Manifest, und stellen Sie sicher, dass `token.botframework.com` es sich im Abschnitt gültige Domänen befindet.
4. Komprimieren Sie das Manifest mit den Profilbildern, und installieren Sie es in Microsoft Teams.

#### <a name="additional-code-samples"></a>Zusätzliche Codebeispiele

* [C#-Beispiel mit dem bot Framework SDK](https://microsoft-my.sharepoint-df.com/:u:/p/vul/ETZQfeTViDlCv-frjgTIincB7dvk2HOnma1TLvcoeGGIxg?e=uPq62c).

* [C#-Beispiel mit dem bot Framework SDK zum deduplizieren der Token-Anforderung](https://microsoft.sharepoint.com/:u:/t/ExtensibilityandFundamentals/Ea36rUGiN1BGt1RiLOb-mY8BGMF8NwPtronYGym0sCGOTw?e=4bB682).

* [C#-Beispiel ohne Verwendung des SDK-Token-Speichers für bot Framework](https://microsoft-my.sharepoint-df.com/:u:/p/tac/EceKDXrkMn5AuGbh6iGid8ABKEVQ6hkxArxK1y7-M8OVPw)
