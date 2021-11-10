---
title: Unterstützung für einmaliges Anmelden für Bots
description: Beschreibt, wie ein Benutzertoken abgerufen wird. Derzeit kann ein Bot-Entwickler eine Anmeldekarte oder den Azure-Bot-Dienst mit OAuth-Kartenunterstützung verwenden.
keywords: Token, Benutzertoken, SSO-Unterstützung für Bots, Berechtigung, Microsoft Graph, AAD
ms.localizationpriority: medium
ms.topic: conceptual
ms.openlocfilehash: 55f1185dfca79a2457e563bcf5ebbc035859a7f2
ms.sourcegitcommit: af1d0a4041ce215e7863ac12c71b6f1fa3e3ba81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2021
ms.locfileid: "60887866"
---
# <a name="single-sign-on-sso-support-for-bots"></a>SSO-Unterstützung (Single Sign-On) für Bots

Die Single Sign-On-Authentifizierung in Azure Active Directory (AAD) minimiert, wie oft Benutzer ihre Anmeldeinformationen eingeben müssen, indem sie das Authentifizierungstoken im Hintergrund aktualisieren. Wenn Benutzer der Verwendung Ihrer App zustimmen, müssen sie auf einem anderen Gerät keine erneute Zustimmung erteilen und können sich automatisch anmelden. Der Fluss ähnelt dem von [Microsoft Teams SSO-Unterstützung](../../../tabs/how-to/authentication/auth-aad-sso.md)für Registerkarten. Der Unterschied besteht jedoch im Protokoll für die Art und Weise, wie ein Bot [Token anfordert](#request-a-bot-token) und [Antworten empfängt.](#receive-the-bot-token)

>[!NOTE]
> OAuth 2.0 ist ein offener Standard für die Authentifizierung und Autorisierung, der von AAD und vielen anderen Identitätsanbietern verwendet wird. Ein grundlegendes Verständnis von OAuth 2.0 ist eine Voraussetzung für die Arbeit mit der Authentifizierung in Teams.

## <a name="bot-sso-at-runtime"></a>Bot-SSO zur Laufzeit

![Bot-SSO zur Laufzeit (Diagramm)](../../../assets/images/bots/bots-sso-diagram.png)

Führen Sie die folgenden Schritte aus, um Authentifizierungs- und Botanwendungstoken abzurufen:

1. Der Bot sendet eine Nachricht mit einer OAuthCard, welche die `tokenExchangeResource`-Eigenschaft enthält. Er weist Teams an, ein Authentifizierungstoken für die Bot-Anwendung abzurufen. Der Benutzer erhält auf allen aktiven Benutzerendpunkten Nachrichten.

    > [!NOTE]
    >* Ein Benutzer kann mehrere aktive Endpunkte gleichzeitig haben.
    >* Der Bot-Token wird von jedem aktiven Benutzerendpunkt erhalten.
    >* Die App muss für SSO-Support im persönlichen Bereich installiert sein.

1. Wenn der aktuelle Benutzer Ihre Bot-Anwendung zum ersten Mal verwendet, wird eine Anforderungsaufforderung angezeigt, um den Benutzer aufzufordern, eine der folgenden Aktionen auszuführen:
    * Geben Sie ihre Zustimmung, falls erforderlich.
    * Erhöhte Authentifizierung durchführen, z. B. die zweistufige Authentifizierung.

1. Teams fordert das Botanwendungstoken vom AAD-Endpunkt für den aktuellen Benutzer an.

1. AAD sendet das Bot-Anwendungstoken an die Teams Anwendung.

1. Teams sendet das Token an den Bot als Teil des Wertobjekts, das von der Aufrufaktivität mit dem Namen **"sign-in"/"tokenExchange"** zurückgegeben wird.
  
1. Das analysierte Token in der Bot-Anwendung stellt die erforderlichen Informationen zur Verfügung, wie z. B. die E-Mail-Adresse des Benutzers.
  
## <a name="develop-an-sso-teams-bot"></a>Entwickeln eines SSO-Teams-Bots
  
Führen Sie die folgenden Schritte aus, um einen SSO-Teams-Bot zu entwickeln:

1. [Registrieren Sie Ihre App über das AAD Portal.](#register-your-app-through-the-aad-portal)
1. [Aktualisieren Sie Ihr Teams Anwendungsmanifest für Ihren Bot.](#update-your-teams-application-manifest-for-your-bot)
1. [Fügen Sie den Code hinzu, um ein Bottoken anzufordern und zu erhalten.](#add-the-code-to-request-and-receive-a-bot-token)

### <a name="register-your-app-through-the-aad-portal"></a>Registrieren Ihrer App über das AAD Portal

Die Schritte zum Registrieren Ihrer App über das AAD-Portal ähneln dem [SSO-Fluss](../../../tabs/how-to/authentication/auth-aad-sso.md)der Registerkarte. Führen Sie die folgenden Schritte aus, um Ihre App zu registrieren:

1. Registrieren Sie eine neue Anwendung im [Portal Azure Active Directory – App-Registrierungen.](https://go.microsoft.com/fwlink/?linkid=2083908)
2. Wählen Sie **"Neue Registrierung"** aus. Die Seite **"Anwendung registrieren"** wird angezeigt.
3. Geben Sie auf der Seite **"Anwendung registrieren"** die folgenden Werte ein:
    1. Geben Sie einen **Namen** für Ihre App ein.
    2. Wählen Sie die **unterstützten Kontotypen** aus, wählen Sie den Kontotyp "Einzelner Mandant" oder "Mehrinstanzenkonto" aus.

        > [!NOTE]
        >
        > Die Benutzer werden nicht zur Zustimmung aufgefordert und erhalten sofort Zugriffstoken, wenn die AAD-App im selben Mandanten registriert ist, in dem sie eine Authentifizierungsanforderung in Teams stellen. Die Benutzer müssen jedoch den Berechtigungen zustimmen, wenn die AAD-App in einem anderen Mandanten registriert ist.

    3. Wählen Sie **Registrieren** aus.
4. Kopieren und speichern Sie auf der Übersichtsseite die **Anwendungs-ID (Client-ID).** Sie benötigen ihn später beim Aktualisieren des Teams Anwendungsmanifests.
5. Wählen Sie unter **Verwalten** die Option **Eine API verfügbar machen** aus. 

   > [!IMPORTANT]
    > * Wenn Sie einen eigenständigen Bot erstellen, geben Sie den Anwendungs-ID-URI als `api://botid-{YourBotId}` . Hier **ist YourBotId** Ihre AAD Anwendungs-ID.
    > * Wenn Sie eine App mit einem Bot und einer Registerkarte erstellen, geben Sie den Anwendungs-ID-URI als `api://fully-qualified-domain-name.com/botid-{YourBotId}` .

5. Wählen Sie die Berechtigungen aus, die Ihre Anwendung für den AAD Endpunkt und optional für Microsoft Graph benötigt.
6. [Erteilen von Berechtigungen](/azure/active-directory/develop/v2-permissions-and-consent) für Teams Desktop-, Web- und mobile Anwendungen.
7. Wählen Sie **Bereich hinzufügen**.
8. Fügen Sie im daraufhin geöffneten Bereich eine Client-App hinzu, indem Sie `access_as_user` sie als **Bereichsnamen** eingeben.

    >[!NOTE]
    > Der Bereich "access_as_user", der zum Hinzufügen einer Client-App verwendet wird, richtet sich an "Administratoren und Benutzer".
    >
    > Sie müssen sich der folgenden wichtigen Einschränkungen bewusst sein:
    >
    > * Es werden nur Microsoft Graph API-Berechtigungen auf Benutzerebene unterstützt, z. B. E-Mail, Profil, offline_access und OpenId. Wenn Sie Zugriff auf andere Microsoft Graph Bereiche benötigen, z. B. `User.Read` oder , finden Sie weitere Informationen unter Abrufen eines `Mail.Read` [Zugriffstokens mit Graph Berechtigungen.](../../../tabs/how-to/authentication/auth-aad-sso.md#get-an-access-token-with-graph-permissions)
    > * Der Domänenname Ihrer Anwendung muss mit dem Domänennamen übereinstimmen, den Sie für Ihre AAD Anwendung registriert haben.
    > * Mehrere Domänen pro App werden derzeit nicht unterstützt.
    > * Anwendungen, die die Domäne verwenden, werden nicht unterstützt, da sie häufig vorkommen `azurewebsites.net` und ein Sicherheitsrisiko darstellen können.

#### <a name="update-the-azure-portal-with-the-oauth-connection"></a>Aktualisieren des Azure-Portals mit der OAuth-Verbindung

Führen Sie die folgenden Schritte aus, um das Azure-Portal mit der OAuth-Verbindung zu aktualisieren:

1. Wechseln Sie im Azure-Portal zu **App-Registrierungen.**

2. Wechseln Sie zu **API-Berechtigungen.** Wählen Sie "Microsoft Graph Delegierte **Berechtigungen" eine Berechtigung** hinzufügen  >    >  aus, und fügen Sie dann die folgenden Berechtigungen aus der Microsoft Graph-API hinzu:
    * User.Read (standardmäßig aktiviert)
    * email
    * offline_access
    * Openid
    * Profil

3. Wechseln Sie im Azure-Portal zu [ **AzureBot**](https://ms.portal.azure.com/#create/Microsoft.AzureBot)
4. Wählen Sie im linken Bereich die Option **"Konfiguration"** aus.
5. Wählen **Sie OAuth-Verbindung hinzufügen Einstellungen** aus.

    ![SSOBotHandle2-Ansicht](~/assets\Contosoairlines123.png)

6. Führen Sie die folgenden Schritte aus, um das Formular **"Neue Verbindungseinstellung"** auszufüllen:

    >[!NOTE]
    > **Die implizite Genehmigung** kann in der AAD Anwendung erforderlich sein.

    1. Geben Sie auf der Seite **"Neue Verbindungseinstellung"** einen **Namen** ein. Dies ist der Name, auf den in den Einstellungen Ihres Bot-Dienstcodes in *Schritt 5* von [Bot SSO zur Laufzeit](#bot-sso-at-runtime)verwiesen wird.
    2. Wählen Sie in der Dropdownliste des **Dienstanbieters** **Azure Active Directory v2** aus.
    3. Geben Sie die Clientanmeldeinformationen ein, z. B. **Client-ID** und **geheimer Clientschlüssel** für die AAD Anwendung.
    4. Verwenden Sie für die **Token-Exchange-URL** den bereichswert, der in [Update Your Teams application manifest for your bot](#update-your-teams-application-manifest-for-your-bot)definiert ist. Die Token-Exchange-URL gibt dem SDK an, dass diese AAD-Anwendung für SSO konfiguriert ist.
    5. Geben Sie im **Feld "Mandanten-ID"** *die allgemeine*.
    6. Fügen Sie alle **Bereiche** hinzu, die beim Angeben von Berechtigungen für downstream-APIs für Ihre AAD-Anwendung konfiguriert sind. Mit der bereitgestellten Client-ID und dem geheimen Clientschlüssel tauscht der Tokenspeicher das Token gegen ein Diagrammtoken mit definierten Berechtigungen aus.
    7. Klicken Sie auf **Speichern**.

    ![Einstellungsansicht für VuSSOBotConnection](../../../assets/images/bots/bots-vuSSOBotConnection-settings.png)

### <a name="update-your-teams-application-manifest-for-your-bot"></a>Aktualisieren Ihres Teams-Anwendungsmanifests für Ihren Bot

Wenn die Anwendung einen eigenständigen Bot enthält, verwenden Sie den folgenden Code, um dem Teams Anwendungsmanifest neue Eigenschaften hinzuzufügen:

```json
    "webApplicationInfo": 
        {
            "id": "00000000-0000-0000-0000-000000000000",
            "resource": "api://botid-00000000-0000-0000-0000-000000000000"
        }
```
Wenn die Anwendung einen Bot und eine Registerkarte enthält, verwenden Sie den folgenden Code, um dem Teams Anwendungsmanifest neue Eigenschaften hinzuzufügen:

```json
    "webApplicationInfo": 
        {
            "id": "00000000-0000-0000-0000-000000000000",
            "resource": "api://subdomain.example.com/botid-00000000-0000-0000-0000-000000000000"
        }
```

**webApplicationInfo** ist das übergeordnete Element der folgenden Elemente:

* **id** – Die Client-ID der Anwendung. Dies ist die Anwendungs-ID, die Sie beim Registrieren der Anwendung bei AAD erhalten haben. Geben Sie diese Anwendungs-ID nicht für mehrere Teams Apps frei. Erstellen Sie eine neue AAD-App für jedes Anwendungsmanifest, das `webApplicationInfo` verwendet.
* **ressource** – Die Domäne und Unterdomäne Ihrer Anwendung. Dies ist der gleiche URI, einschließlich des `api://` Protokolls, das Sie beim Erstellen Ihrer App im Portal AAD registriert `scope` [haben.](#register-your-app-through-the-aad-portal) Sie dürfen den Pfad nicht `access_as_user` in Ihre Ressource einschließen. Der Domänenteil dieses URI muss mit der Domäne und den Unterdomänen übereinstimmen, die in den URLs Ihres Teams Anwendungsmanifests verwendet werden.

### <a name="add-the-code-to-request-and-receive-a-bot-token"></a>Hinzufügen des Codes zum Anfordern und Empfangen eines Bottokens

#### <a name="request-a-bot-token"></a>Anfordern eines Bottokens

Die Anforderung zum Abrufen des Tokens ist eine normale POST-Nachrichtenanforderung mithilfe des vorhandenen Nachrichtenschemas. Sie ist in den Anlagen einer OAuthCard enthalten. Das Schema für die OAuthCard-Klasse ist in [Microsoft Bot Schema 4.0](/dotnet/api/microsoft.bot.schema.oauthcard?view=botbuilder-dotnet-stable&preserve-view=true) definiert und ähnelt einer Anmeldekarte. Teams behandelt diese Anforderung als automatische Tokenerfassung, wenn die `TokenExchangeResource` Eigenschaft auf der Karte aufgefüllt wird. Für den Teams Kanal wird nur die `Id` Eigenschaft berücksichtigt, die eine Tokenanforderung eindeutig identifiziert.

>[!NOTE]
> Die Microsoft Bot Framework `OAuthPrompt` oder die wird für die `MultiProviderAuthDialog` SSO-Authentifizierung unterstützt.

Wenn der Benutzer die Anwendung zum ersten Mal verwendet und die Zustimmung des Benutzers erforderlich ist, wird das folgende Dialogfeld angezeigt, um mit der Zustimmung fortzufahren:

![Dialogfeld "Zustimmung"](../../../assets/images/bots/bots-consent-dialogbox.png)

Wenn der Benutzer **Weiter** auswählt, treten die folgenden Ereignisse auf:

* Wenn der Bot eine Anmeldeschaltfläche definiert, wird der Anmeldefluss für Bots ähnlich wie der Anmeldefluss von einer OAuth-Kartenschaltfläche in einem Nachrichtendatenstrom ausgelöst. Der Entwickler muss entscheiden, welche Berechtigungen die Zustimmung des Benutzers erfordern. Dieser Ansatz wird empfohlen, wenn Sie ein Token mit berechtigungen `openId` übersteigt. Wenn Sie z. B. das Token gegen Graph-Ressourcen austauschen möchten.

* Wenn der Bot keine Anmeldeschaltfläche auf der OAuth-Karte bereitstellt, ist die Zustimmung des Benutzers für einen minimalen Satz von Berechtigungen erforderlich. Dieses Token ist nützlich für die Standardauthentifizierung und zum Abrufen der E-Mail-Adresse des Benutzers.

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

Die Antwort mit dem Token wird über eine Aufrufaktivität mit demselben Schema wie andere Aufrufaktivitäten gesendet, die die Bots heute erhalten. Der einzige Unterschied ist der Aufrufname, **die Anmeldung/tokenExchange** und das **Wertfeld.** Das **Wertfeld** enthält die **ID**, eine Zeichenfolge der anfänglichen Anforderung zum Abrufen des Tokens und das **Tokenfeld,** einen Zeichenfolgenwert einschließlich des Tokens.

>[!NOTE]
> Sie erhalten möglicherweise mehrere Antworten auf eine bestimmte Anforderung, wenn der Benutzer über mehrere aktive Endpunkte verfügt. Sie müssen die Antworten mit dem Token deduplizieren.

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

### <a name="token-exchange-failure"></a>Fehler beim Austausch von Token

Verwenden Sie im Falle eines Fehlers beim Austausch von Token den folgenden Code:

```json
{ 
    "status": "<response code>", 
    "body": 
    { 
        "id":"<unique Id>", 
        "connectionName": "<connection Name on the bot (from the OAuth card)>", 
        "failureDetail": "<failure reason if status code is not 200, null otherwise>" 
    } 
}
```

Um zu verstehen, was der Bot tut, wenn der Tokenaustausch keine Zustimmungsaufforderung auslöst, führen Sie die folgenden Schritte aus:

>[!NOTE]
> Es ist keine Benutzeraktion erforderlich, wenn der Bot die Aktionen ausführt, wenn der Tokenaustausch fehlschlägt.

1. Der Client startet eine Unterhaltung mit dem Bot, der ein OAuth-Szenario auslöst.
2. Der Bot sendet eine OAuth-Karte an den Client zurück.
3. Der Client fängt die OAuth-Karte ab, bevor sie dem Benutzer angezeigt wird, und überprüft, ob sie eine `TokenExchangeResource` Eigenschaft enthält.
4. Wenn die Eigenschaft vorhanden ist, sendet der Client einen `TokenExchangeInvokeRequest` an den Bot. Der Client muss über ein austauschbares Token für den Benutzer verfügen, bei dem es sich um ein Azure AD v2-Token handelt und dessen Zielgruppe mit der Eigenschaft identisch sein `TokenExchangeResource.Uri` muss. Der Client sendet eine Aufrufaktivität mit dem folgenden Code an den Bot:

    ```json
    {
        "type": "Invoke",
        "name": "signin/tokenExchange",
        "value": 
        {
            "id": "<any unique Id>",
            "connectionName": "<connection Name on the skill bot (from the OAuth card)>",
            "token": "<exchangeable token>"
        }
    }
    ```

5. Der Bot verarbeitet die `TokenExchangeInvokeRequest` und gibt einen Zurück an den Client `TokenExchangeInvokeResponse` zurück. Der Client muss warten, bis er die `TokenExchangeInvokeResponse` .

    ```json
    {
        "status": "<response code>",
        "body": 
        {
            "id":"<unique Id>",
            "connectionName": "<connection Name on the skill bot (from the OAuth card)>",
            "failureDetail": "<failure reason if status code is not 200, null otherwise>"
        }
    }
    ```

6. Wenn der über `TokenExchangeInvokeResponse` einen `status` von `200` verfügt, zeigt der Client die OAuth-Karte nicht an. Sehen Sie sich das [normale Flussbild an.](/azure/bot-service/bot-builder-concept-sso?view=azure-bot-service-4.0#sso-components-interaction&preserve-view=true) Bei anderen Oder wenn der Client `status` `TokenExchangeInvokeResponse` nicht empfangen wird, zeigt der Client dem Benutzer die OAuth-Karte an. Sehen Sie sich das [Fallback-Flussbild](/azure/bot-service/bot-builder-concept-sso?view=azure-bot-service-4.0#sso-components-interaction&preserve-view=true)an. Dadurch wird sichergestellt, dass der SSO-Fluss auf den normalen OAuthCard-Fluss zurückfällt, wenn Fehler oder nicht behandelte Abhängigkeiten wie die Zustimmung des Benutzers auftreten.


### <a name="update-the-auth-sample"></a>Aktualisieren des Authentifizierungsbeispiels

Öffnen [Sie Teams Authentifizierungsbeispiel,](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth) und führen Sie dann die folgenden Schritte aus, um es zu aktualisieren:

1. Aktualisieren Sie TeamsBot, um die Deduping der eingehenden Anforderung zu verarbeiten, indem Sie den folgenden Code einschließen:

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
  
2. Aktualisieren `appsettings.json` Sie, um das `botId` Kennwort und den im Update des [Azure-Portals mit der OAuth-Verbindung](#update-the-azure-portal-with-the-oauth-connection)definierten Verbindungsnamen einzuschließen.
3. Aktualisieren Sie das Manifest, und stellen Sie sicher, dass es `token.botframework.com` sich in der Liste der gültigen Domänen befindet. Weitere Informationen finden Sie unter [Teams Authentifizierungsbeispiel.](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth)
4. Zippen Sie das Manifest mit den Profilimages, und installieren Sie es in Teams.

## <a name="code-sample"></a>Codebeispiel
|**Beispielname** | **Beschreibung** |**.NET** | 
|----------------|-----------------|--------------|
|Bot framework SDK | Beispiel für die Verwendung des Bot Framework SDK. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/experimental/teams-sso/csharp_dotnetcore)|
