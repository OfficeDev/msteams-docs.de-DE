---
title: Unterstützung für einmaliges Anmelden für Bots
description: Beschreibt, wie sie ein Benutzertoken erhalten. Derzeit kann ein Botentwickler eine Anmeldekarte oder den Azure -Bot-Dienst mit der Unterstützung der OAuth-Karte verwenden.
keywords: Token, Benutzertoken, SSO-Unterstützung für Bots
ms.topic: conceptual
ms.openlocfilehash: 55b930ba50eede6ac970fbe0f901d418605f3f91
ms.sourcegitcommit: 5662bf23fafdbcc6d06f826a647f3696cd17f5e5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/22/2021
ms.locfileid: "49935254"
---
# <a name="single-sign-on-sso-support-for-bots"></a>Unterstützung für einmaliges Anmelden (Single Sign-On, SSO) für Bots

Die Authentifizierung mit einmaligem Anmelden in Azure Active Directory (AAD) minimiert die Anzahl der Benutzer, die ihre Anmeldeinformationen eingeben müssen, indem das Authentifizierungstoken automatisch aktualisiert wird. Wenn Benutzer der Verwendung Ihrer App zustimmen, müssen sie auf einem anderen Gerät keine weitere Zustimmung erteilen und können sich automatisch anmelden. Der Ablauf ähnelt dem der Unterstützung von [Microsoft Teams-Registerkarten-SSO,](../../../tabs/how-to/authentication/auth-aad-sso.md)der Unterschied besteht jedoch im Protokoll dafür, wie ein Bot Token [anfordert](#request-a-bot-token) und Antworten [empfängt.](#receive-the-bot-token)

>[!NOTE]
> OAuth 2.0 ist ein offener Standard für die Authentifizierung und Autorisierung, der von AAD und vielen anderen Identitätsanbietern verwendet wird. Ein grundlegendes Verständnis von OAuth 2.0 ist eine Voraussetzung für die Arbeit mit der Authentifizierung in Teams.

## <a name="bot-sso-at-runtime"></a>Bot-SSO zur Laufzeit

![Bot-SSO zur Laufzeit (Diagramm)](../../../assets/images/bots/bots-sso-diagram.png)

Führen Sie die folgenden Schritte aus, um Authentifizierungs- und Botanwendungstoken abzurufen:

1. Der Bot sendet eine Nachricht mit einer OAuthCard, die die Eigenschaft `tokenExchangeResource` enthält. Er weist Teams an, ein Authentifizierungstoken für die Botanwendung abzurufen. Der Benutzer empfängt Nachrichten an allen aktiven Benutzerendpunkten.

    > [!NOTE]
    >* Ein Benutzer kann mehrere aktive Endpunkte gleichzeitig haben.
    >* Das Bottoken wird von jedem aktiven Benutzerendpunkt empfangen.
    >* Die App muss im persönlichen Bereich für die Unterstützung von SSO installiert werden.

2. Wenn der aktuelle Benutzer Ihre Botanwendung zum ersten Mal verwendet, wird eine Anforderungsaufforderung angezeigt, in der der Benutzer aufgefordert wird, eine der folgenden Schritte zu tun:
    * Geben Sie ihre Zustimmung, falls erforderlich.
    * Behandeln Sie die Step-Up-Authentifizierung, z. B. die zweistufige Authentifizierung.

3. Teams fordert das Botanwendungstoken vom AAD-Endpunkt für den aktuellen Benutzer an.

4. AAD sendet das Botanwendungstoken an die Teams-Anwendung.

5. Teams sendet das Token als Teil des Wertobjekts, das von der Aufrufaktivität mit dem Namen **sign-in/tokenExchange zurückgegeben wird, an den Bot.**
  
6. Das analysierte Token in der Botanwendung stellt die erforderlichen Informationen zur Verfügung, z. B. die E-Mail-Adresse des Benutzers.
  
## <a name="develop-an-sso-teams-bot"></a>Entwickeln eines SSO -Teams-Bots
  
Führen Sie die folgenden Schritte aus, um einen SSO -Teams-Bot zu entwickeln:

1. [Registrieren Sie Ihre App über das AAD-Portal.](#register-your-app-through-the-aad-portal)
2. [Aktualisieren Sie Ihr Teams-Anwendungsmanifest für Ihren Bot.](#update-your-teams-application-manifest-for-your-bot)
3. [Fügen Sie den Code zum Anfordern und Empfangen eines Bottokens hinzu.](#add-the-code-to-request-and-receive-a-bot-token)

### <a name="register-your-app-through-the-aad-portal"></a>Registrieren Ihrer App über das AAD-Portal

Die Schritte zum Registrieren Ihrer App über das AAD-Portal ähneln dem [Registerkarten-SSO-Fluss.](../../../tabs/how-to/authentication/auth-aad-sso.md) Führen Sie die folgenden Schritte aus, um Ihre App zu registrieren:

1. Registrieren Sie eine neue Anwendung im [Azure Active Directory – App-Registrierungsportal.](https://go.microsoft.com/fwlink/?linkid=2083908)
2. Wählen Sie **"Neue Registrierung" aus.** Die **Seite "Anwendung registrieren"** wird angezeigt.
3. Geben Sie **auf der Seite "Anwendung registrieren"** die folgenden Werte ein:
    1. Geben Sie **einen Namen** für Ihre App ein.
    2. Wählen Sie die **unterstützten Kontotypen** aus, wählen Sie den Kontotyp für einen einzelnen Mandanten oder mehrere Mandanten aus.

        > [!NOTE]
        >
        > Die Benutzer werden nicht um Zustimmung gebeten und erhalten sofort Zugriffstoken, wenn die AAD-App im selben Mandanten registriert ist, in dem sie eine Authentifizierungsanforderung in Teams stellen. Die Benutzer müssen jedoch den Berechtigungen zustimmen, wenn die AAD-App in einem anderen Mandanten registriert ist.

    3. Wählen Sie **Registrieren** aus.
4. Kopieren und speichern Sie auf der Übersichtsseite die **Anwendungs-ID (Client-ID).** Sie benötigen sie später beim Aktualisieren Ihres Teams-Anwendungsmanifests.
5. Wählen Sie unter **Verwalten** die Option **Eine API verfügbar machen** aus. 

   > [!IMPORTANT]
    > * Wenn Sie einen eigenständigen Bot erstellen, geben Sie den Anwendungs-ID-URI als `api://botid-{YourBotId}` ein. Hier **ist YourBotId** Ihre AAD-Anwendungs-ID.
    > * Wenn Sie eine App mit einem Bot und einer Registerkarte erstellen, geben Sie den Anwendungs-ID-URI als `api://fully-qualified-domain-name.com/botid-{YourBotId}` ein.

5. Wählen Sie die Berechtigungen aus, die Ihre Anwendung für den AAD-Endpunkt und optional für Microsoft Graph benötigt.
6. [Erteilen von Berechtigungen](/azure/active-directory/develop/v2-permissions-and-consent) für Desktop-, Web- und mobile Anwendungen von Teams.
7. Wählen Sie **Bereich hinzufügen**.
8. Fügen Sie im Bereich, der geöffnet wird, eine Client-App hinzu, indem Sie `access_as_user` den **Bereichsnamen eingeben.**

    >[!NOTE]
    > Der "access_as_user"-Bereich, der zum Hinzufügen einer Client-App verwendet wird, ist für "Administratoren und Benutzer".
    >
    > Beachten Sie die folgenden wichtigen Einschränkungen:
    >
    > * Es werden nur Microsoft Graph-API-Berechtigungen auf Benutzerebene unterstützt, z. B. E-Mail, Profil, offline_access und OpenId. Wenn Sie Zugriff auf andere Microsoft Graph-Bereiche benötigen, z. B. oder , finden Sie weitere Informationen zur `User.Read` `Mail.Read` [empfohlenen Problemumgehung.](../../../tabs/how-to/authentication/auth-aad-sso.md#apps-that-require-additional-microsoft-graph-scopes)
    > * Der Domänenname Ihrer Anwendung muss mit dem Domänennamen identisch sein, den Sie für Ihre AAD-Anwendung registriert haben.
    > * Mehrere Domänen pro App werden derzeit nicht unterstützt.
    > * Anwendungen, die die Domäne verwenden, werden nicht unterstützt, da sie häufig verwendet werden `azurewebsites.net` und ein Sicherheitsrisiko darstellen können.

#### <a name="update-the-azure-portal-with-the-oauth-connection"></a>Aktualisieren des Azure-Portals mit der OAuth-Verbindung

Führen Sie die folgenden Schritte aus, um das Azure-Portal mit der OAuth-Verbindung zu aktualisieren:

1. Navigieren Sie im Azure Portal zu **"Bot Channels Registration".**

2. Wechseln Sie zu **"API-Berechtigungen".** Wählen **Sie "Delegierte Berechtigungen für** Microsoft Graph hinzufügen" aus, und fügen Sie dann die folgenden Berechtigungen aus der Microsoft  >    >  Graph-API hinzu:
    * User.Read (standardmäßig aktiviert)
    * email
    * offline_access
    * OpenId
    * Profil

3. Wählen **Sie im** linken Bereich "Einstellungen" und dann "Einstellung hinzufügen" im Abschnitt  **"OAuth-Verbindungseinstellungen"** aus.

    ![Ansicht SSOBotHandle2](../../../assets/images/bots/bots-vuSSOBotHandle2-settings.png)

4. Führen Sie die folgenden Schritte aus, um das Formular für neue **Verbindungseinstellungen** auszufüllen:

    >[!NOTE]
    > **In der** AAD-Anwendung ist möglicherweise eine implizite Gewährung erforderlich.

    1. Geben Sie **auf der Seite "Neue** **Verbindungseinstellung" einen Namen** ein. Dies ist der Name, auf den in den Einstellungen Ihres Botdienstcodes in Schritt *5* von Bot SSO zur Laufzeit [verwiesen wird.](#bot-sso-at-runtime)
    2. Wählen Sie **in der** Dropdownliste "Dienstanbieter" Azure Active **Directory v2 aus.**
    3. Geben Sie die Clientanmeldeinformationen ein, z. **B. Client-ID** und **geheimer Client für** die AAD-Anwendung.
    4. Verwenden Sie **für die Token-Exchange-URL** den Bereichswert, der in [Update your Teams application manifest for your bot definiert ist.](#update-your-teams-application-manifest-for-your-bot) Die Token-Exchange-URL gibt dem SDK an, dass diese AAD-Anwendung für SSO konfiguriert ist.
    5. Geben Sie **im Feld "Mandanten-ID"** eine *gemeinsame ein.*
    6. Fügen Sie alle **Bereiche hinzu,** die beim Angeben von Berechtigungen für downstream-APIs für Ihre AAD-Anwendung konfiguriert wurden. Wenn die Client-ID und der geheime Clientgeheimnis angegeben sind, tauscht der Tokenspeicher das Token gegen ein Diagrammtoken mit definierten Berechtigungen aus.
    7. Klicken Sie auf **Speichern**.

    ![Einstellungsansicht für VuSSOBotConnection](../../../assets/images/bots/bots-vuSSOBotConnection-settings.png)

### <a name="update-your-teams-application-manifest-for-your-bot"></a>Aktualisieren Ihres Teams-Anwendungsmanifests für Ihren Bot

Wenn die Anwendung einen eigenständigen Bot enthält, verwenden Sie den folgenden Code, um dem Anwendungsmanifest von Teams neue Eigenschaften hinzuzufügen:

```json
    "webApplicationInfo": 
        {
            "id": "00000000-0000-0000-0000-000000000000",
            "resource": "api://botid-00000000-0000-0000-0000-000000000000"
        }
```
Wenn die Anwendung einen Bot und eine Registerkarte enthält, verwenden Sie den folgenden Code, um dem Anwendungsmanifest von Teams neue Eigenschaften hinzuzufügen:

```json
    "webApplicationInfo": 
        {
            "id": "00000000-0000-0000-0000-000000000000",
            "resource": "api://subdomain.example.com/botid-00000000-0000-0000-0000-000000000000"
        }
```

**webApplicationInfo** ist das übergeordnete Element der folgenden Elemente:

* **id** – Die Client-ID der Anwendung. Dies ist die Anwendungs-ID, die Sie im Rahmen der Registrierung der Anwendung bei AAD erhalten haben.
* **resource** – Die Domäne und Unterdomäne Ihrer Anwendung. Dies ist der gleiche URI, einschließlich des Protokolls, das Sie beim Erstellen Ihrer App über das `api://` AAD-Portal registriert `scope` [haben.](#register-your-app-through-the-aad-portal) Sie dürfen den Pfad `access_as_user` nicht in ihre Ressource verwenden. Der Domänenteil dieses URI muss mit der Domäne und den Unterdomänen übereinstimmen, die in den URLs Ihres Anwendungsmanifests von Teams verwendet werden.

### <a name="add-the-code-to-request-and-receive-a-bot-token"></a>Hinzufügen des Codes zum Anfordern und Empfangen eines Bottokens

#### <a name="request-a-bot-token"></a>Anfordern eines Bottokens

Die Anforderung zum Anfordern des Tokens ist eine normale POST-Nachrichtenanforderung, die das vorhandene Nachrichtenschema verwendet. Sie ist in den Anlagen einer OAuthCard enthalten. Das Schema für die "OAuthCard"-Klasse ist in [Microsoft Bot Schema 4.0](/dotnet/api/microsoft.bot.schema.oauthcard?view=botbuilder-dotnet-stable&preserve-view=true) definiert und ähnelt einer Anmeldekarte. Teams behandelt diese Anforderung als automatischen Tokenerwerb, wenn die Eigenschaft `TokenExchangeResource` auf der Karte aufgefüllt wird. Für den Kanal "Teams" wird nur die Eigenschaft berücksichtigt, die eine `Id` Tokenanforderung eindeutig identifiziert.

>[!NOTE]
> Das Microsoft Bot Framework `OAuthPrompt` oder das wird für die `MultiProviderAuthDialog` SSO-Authentifizierung unterstützt.

Wenn der Benutzer die Anwendung zum ersten Mal verwendet und die Zustimmung des Benutzers erforderlich ist, wird im folgenden Dialogfeld die Zustimmungserfahrung angezeigt:

![Dialogfeld "Zustimmung"](../../../assets/images/bots/bots-consent-dialogbox.png)

Wenn der Benutzer **"Weiter"** auswählt, treten die folgenden Ereignisse auf:

* Wenn der Bot eine Anmeldeschaltfläche definiert, wird der Anmeldefluss für Bots ähnlich wie der Anmeldefluss von einer Schaltfläche für eine OAuth-Karte in einem Nachrichtendatenstrom ausgelöst. Der Entwickler muss entscheiden, welche Berechtigungen die Zustimmung des Benutzers erfordern. Dieser Ansatz wird empfohlen, wenn Sie ein Token mit Berechtigungen benötigen, die über `openId` diesen hinausgehen. Beispielsweise, wenn Sie das Token gegen Graphressourcen austauschen möchten.

* Wenn der Bot keine Anmeldeschaltfläche auf der OAuth-Karte zur Verfügung stellt, ist die Zustimmung des Benutzers für einen minimalen Satz von Berechtigungen erforderlich. Dieses Token ist nützlich für die Standardauthentifizierung und zum Erhalten der E-Mail-Adresse des Benutzers.

##### <a name="c-token-request-without-a-sign-in-button"></a>C#-Tokenanforderung ohne Anmeldeschaltfläche

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

#### <a name="receive-the-bot-token"></a>Empfangen des Bottokens

Die Antwort mit dem Token wird über eine Aufrufaktivität mit demselben Schema wie andere Aufrufaktivitäten gesendet, die die Bots heute erhalten. Der einzige Unterschied besteht im Aufrufnamen, **der Anmeldung/tokenExchange** und dem **Wertfeld.** Das **Wertfeld** enthält die **ID**, eine Zeichenfolge der  ursprünglichen Anforderung, um das Token und das Tokenfeld abzurufen, einen Zeichenfolgenwert einschließlich des Tokens.

>[!NOTE]
> Sie erhalten möglicherweise mehrere Antworten für eine bestimmte Anforderung, wenn der Benutzer über mehrere aktive Endpunkte verfügt. Sie müssen die Antworten mit dem Token deduplizieren.

##### <a name="c-code-to-handle-the-invoke-activity"></a>C#-Code zum Behandeln der Aufrufaktivität

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

Der `turnContext.activity.value` ist vom Typ [TokenExchangeInvokeRequest](/dotnet/api/microsoft.bot.schema.tokenexchangeinvokerequest?view=botbuilder-dotnet-stable&preserve-view=true) und enthält das Token, das von Ihrem Bot weiter verwendet werden kann. Sie müssen die Token aus Leistungsgründen speichern und aktualisieren.

### <a name="update-the-auth-sample"></a>Aktualisieren des Authentifizierungsbeispiels

Öffnen [Sie das Authentifizierungsbeispiel für Teams,](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth) und führen Sie dann die folgenden Schritte aus, um es zu aktualisieren:

1. Aktualisieren Sie den TeamsBot, um die Deduplikung der eingehenden Anforderung zu verarbeiten, indem Sie den folgenden Code verwenden:

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
  
2. Aktualisieren Sie das Update, um das , Kennwort und den verbindungsnamen, die `appsettings.json` `botId` in Aktualisieren des [Azure-Portals mit der OAuth-Verbindung definiert sind.](#update-the-azure-portal-with-the-oauth-connection)
3. Aktualisieren Sie das Manifest, und stellen `token.botframework.com` Sie sicher, dass es sich in der Liste der gültigen Domänen befindet. Weitere Informationen finden Sie im [Beispiel zur Teams-Authentifizierung.](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth)
4. Zippern Sie das Manifest mit den Profilabbildern, und installieren Sie es in Teams.

#### <a name="additional-code-samples"></a>Zusätzliche Codebeispiele

* [C#-Beispiel mit dem Bot Framework SDK](https://github.com/microsoft/BotBuilder-Samples/tree/main/experimental/teams-sso/csharp_dotnetcore).
