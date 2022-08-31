---
title: Unterstützung für einmaliges Anmelden für Bots
description: Erfahren Sie, wie Sie ein Benutzertoken erhalten, und ein Bot-Entwickler kann eine Anmeldekarte oder den Azure-Botdienst mit der OAuth-Kartenunterstützung verwenden.
ms.localizationpriority: medium
ms.topic: conceptual
ms.openlocfilehash: 46f9ee905f470563fb2a402f9addabfcf09601b6
ms.sourcegitcommit: 36c6a5ba1dcd27a15ba31f479e534eab69aa17e1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2022
ms.locfileid: "67465379"
---
# <a name="use-sso-authentication-for-bots"></a>Verwenden der SSO-Authentifizierung für Bots

Die Single-Sign-On-Authentifizierung in Microsoft Azure Active Directory (Azure AD) aktualisiert das Authentifizierungstoken im Hintergrund, um die Anzahl der Male zu minimieren, die Benutzer ihre Anmeldeinformationen eingeben müssen. Wenn Benutzer der Verwendung Ihrer App zustimmen, müssen sie ihre Zustimmung auf einem anderen Gerät nicht erneut erteilen, da sie automatisch angemeldet werden. Registerkarten und Bots haben einen ähnlichen Fluss für die SSO-Unterstützung. Aber Bot [fordert Token](#request-a-bot-token) an und [erhält Antworten](#receive-the-bot-token) mit einem anderen Protokoll.

>[!NOTE]
> * OAuth 2.0 ist ein offener Standard für die Authentifizierung und Autorisierung, der von Azure AD und vielen anderen Identitätsanbietern verwendet wird. Ein grundlegendes Verständnis von OAuth 2.0 ist Voraussetzung für die Arbeit mit Authentifizierung in Teams.
>
> * Bot-SSO wird nur in Einem-zu-Eins-Chat unterstützt.

Im folgenden Video erfahren Sie mehr über die SSO-Unterstützung (Single Sign-On) für Bots:
<br>
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4OASc]
<br>

## <a name="bot-sso-at-runtime"></a>Bot-SSO zur Laufzeit

Das Bild zeigt den Ablauf von SSO in Bots:

![Diagramm für Bot-SSO zur Laufzeit](../../../assets/images/bots/bots-sso-diagram.png)

Die folgenden Schritte helfen Ihnen bei der Authentifizierung und Bot-Anwendungstoken:

1. Der Bot sendet eine Nachricht an Teams mit einer OAuthCard, die `tokenExchangeResource` enthält, um ein Authentifizierungstoken für die Bot-Anwendung zu erhalten. Der Benutzer erhält auf allen aktiven Benutzerendpunkten Nachrichten.

   > [!NOTE]
   >
   > * Ein Benutzer kann mehrere aktive Endpunkte gleichzeitig haben.
   > * Der Bot-Token wird von jedem aktiven Benutzerendpunkt erhalten.
   > * Die App muss für SSO-Support im persönlichen Bereich installiert sein.

1. Wenn der aktuelle Benutzer Ihre Bot-Anwendung zum ersten Mal verwendet, wird dem Benutzer eine Aufforderung angezeigt, eine der folgenden Aktionen auszuführen:
    * Falls notwendig die Zustimmung geben.
    * Erhöhte Authentifizierung durchführen, z. B. die zweistufige Authentifizierung.

1. Teams fordert das Bot-Anwendungstoken vom Azure AD-Endpunkt für den aktuellen Benutzer an.

1. Azure AD sendet das Bot-Anwendungstoken an die Teams-Anwendung.

1. Teams sendet das Token als Teil des Wertobjekts, das durch den Aufruf mit **sign in/tokenExchange** zurückgegeben wird, an den Bot.
  
1. Das analysierte Token in der Bot-Anwendung stellt die erforderlichen Informationen zur Verfügung, wie z. B. die E-Mail-Adresse des Benutzers.
  
## <a name="develop-an-sso-teams-bot"></a>Entwickeln Sie einen SSO Teams-Bot
  
Die folgenden Schritte führen Sie zur Entwicklung des SSO Teams-Bots:

1. [Registrieren Sie Ihre App über das Azure AD-Portal](#register-your-app-through-the-azure-ad-portal).
1. [Aktualisieren Sie Ihr Teams-Anwendungsmanifest für Ihren Bot](#update-your-teams-application-manifest-for-your-bot).
1. [Fügen Sie den anzufordernden Code hinzu und erhalten Sie ein Bot-Token](#add-the-code-to-request-and-receive-a-bot-token).

### <a name="register-your-app-through-the-azure-ad-portal"></a>Registrieren Sie Ihre App über das Azure AD-Portal

Die Schritte zum Registrieren Ihrer App über das Azure AD-Portal ähneln denen auf der Registerkarte [SSO-Ablauf](../../../tabs/how-to/authentication/tab-sso-overview.md). Die folgenden Schritte führen Sie zur Registrierung Ihrer App:

1. Registrieren Sie eine neue Anwendung im Portal [Azure Active Directory – App-Registrierungen](https://go.microsoft.com/fwlink/?linkid=2083908).

1. Wählen Sie **Neue Registrierung** aus. Die Seite **Anwendung registrieren** wird angezeigt.

    ![Neue Registrierung](~/assets/images/authentication/SSO-bots-auth/app-registration.png)

1. Führen Sie unter **Anwendung registrieren** die folgenden Schritte aus:

   > [!NOTE]
   >
   > Die Benutzer werden nicht um Zustimmung gebeten und erhalten sofort Zugriffstoken, wenn die Azure AD-App in demselben Mandanten registriert ist, in dem sie eine Authentifizierungsanforderung in Teams stellen. Allerdings müssen die Benutzer den Berechtigungen zustimmen, wenn die Azure AD-App in einem anderen Mandanten registriert ist.

    * Geben Sie **Name** für Ihre Anwendung ein.
    * Wählen Sie **Unterstützte Kontotypen** aus, z. B. Einzelinstanzenfähig oder Mehrinstanzenfähig.
    * Wählen Sie **Registrieren** aus.

    ![Registrieren einer Anwendung](~/assets/images/authentication/SSO-bots-auth/register-application.png)

1. Zur Übersichtsseite gehen.
1. Kopieren Sie den Wert der **Anwendungs-(Client-)ID**.
1. Gehen Sie unter **Verwalten** zu **API verfügbar machen**.

   > [!TIP]
   > Um Ihr Anwendungsmanifest später zu aktualisieren, speichern Sie den Wert für die **Anwendungs-(Client-)ID**.

   > [!IMPORTANT]
   >
   > * Wenn Sie einen eigenständigen Bot erstellen, geben Sie den Anwendungs-ID-URI als `api://botid-{YourBotId}` ein. Hier ist *YourBotId* Ihre Azure AD-Anwendungs-ID.
   > * Wenn Sie eine App mit einem Bot und einer Registerkarte erstellen, geben Sie den Anwendungs-ID-URI als `api://fully-qualified-domain-name.com/botid-{YourBotId}` ein.

1. Wählen Sie **Bereich hinzufügen**.
1. Geben Sie im Fenster mit der Aufforderung `access_as_user` als **Bereichsname** ein.

   >[!NOTE]
   > Der zum Hinzufügen einer Client-App verwendete Bereich „access_as_user“ gilt für „Administratoren und Benutzer“.
   >
   > Sie müssen sich der folgenden wichtigen Einschränkungen bewusst sein:
   >
   > * Nur Microsoft Graph-API-Berechtigungen auf Benutzerebene wie E-Mail, Profil, Offlinezugriff und OpenId werden unterstützt. Wenn Sie Zugriff auf andere Microsoft Graph-Bereiche benötigen, z `User.Read` . B. oder `Mail.Read`, lesen Sie ["Registerkarten-App erweitern" mit Microsoft Graph-Berechtigungen und -Bereich](../../../tabs/how-to/authentication/tab-sso-graph-api.md).
   > * Der Domänenname Ihrer Anwendung muss mit dem Domänennamen übereinstimmen, den Sie für Ihre Azure AD-Anwendung registriert haben.
   > * Mehrere Domänen pro App werden derzeit nicht unterstützt.
   > * Anwendungen, die die Domäne `azurewebsites.net` verwenden, werden nicht unterstützt, da dies häufig vorkommt und ein Sicherheitsrisiko darstellen kann.

1. Geben Sie im Feld **Wer kann zustimmen?** **Administratoren und Nutzer** ein.
1. Geben Sie die folgenden Details ein, um die Administrator- und Benutzereinwilligungsaufforderungen mit Werten zu konfigurieren, die für den Bereich `access_as_user` geeignet sind.
    * **Anzeigename für die Administratoreinwilligung:** Teams kann auf das Profil des Benutzers zugreifen.
    * **Beschreibung der Administratoreinwilligung**: Teams können die Web-APIs der App als aktueller Benutzer aufrufen.
    * **Anzeigename der Nutzereinwilligung**: Teams können auf Ihr Profil zugreifen und Anfragen in Ihrem Namen stellen.
    * **Beschreibung der Benutzereinwilligung**: Teams können die APIs dieser App mit denselben Rechten wie Sie aufrufen.

    ![Administrator und Benutzer](~/assets/images/authentication/SSO-bots-auth/add-a-scope.png)

1. Stellen Sie sicher, dass der Status auf **Aktiviert** gesetzt ist.

    ![Status](~/assets/images/authentication/SSO-bots-auth/enabled-state.png)

1. Wählen Sie **Bereich hinzufügen** aus, um die Details zu speichern. Der Domänenteil des angezeigten **Bereichsnamens** muss automatisch mit dem im vorherigen Schritt festgelegten **Anwendungs-ID**-URI übereinstimmen, wobei `/access_as_user` an das Ende `api://subdomain.example.com/00000000-0000-0000-0000-000000000000/access_as_user` angehängt wird.

1. Identifizieren Sie in den **Autorisierten Clientanwendungen** die Anwendungen, die Sie für die Webanwendung Ihrer App autorisieren möchten.
1. **Hinzufügen einer Clientanwendung** auswählen.

    ![Client-Anwendung](~/assets/images/authentication/SSO-bots-auth/add-client-application.png)

1. Geben Sie jede der folgenden Client-IDs ein, und wählen Sie den autorisierten Bereich aus, den Sie im vorherigen Schritt erstellt haben:
    * `1fec8e78-bce4-4aaf-ab1b-5451cc387264` für Teams Mobile oder Desktopanwendung.
    * `5e3ce6c0-2b1f-4285-8d4b-75ee78787346` für Teams-Webanwendung.

    ![Kunden ID](~/assets/images/authentication/SSO-bots-auth/add-client-id.png)

1. Gehen Sie zu **Authentifizierung**.
1. Wählen Sie unter **Plattformkonfigurationen** die Option **Plattform hinzufügen** aus.

    ![Plattform](~/assets/images/authentication/SSO-bots-auth/platform-configuration.png)

1. Klicken Sie auf **Web**.

    ![Plattform konfigurieren](~/assets/images/authentication/SSO-bots-auth/configure-platform.png)

1. Geben Sie die **Umleitungs-URIs** für Ihre Anwendung ein.

   >[!NOTE]
   > Dieser URI sollte ein vollständig qualifizierter Domänenname sein. Es folgt auch die API-Route, an die eine Authentifizierungsantwort gesendet wird. Wenn Sie einem der Teams-Beispiele folgen, lautet der URI `https://token.botframework.com/.auth/web/redirect`. Weitere Informationen finden Sie unter [OAuth 2.0-Autorisierungscodefluss](/azure/active-directory/develop/v2-oauth2-auth-code-flow).

    ![Uris umleiten](~/assets/images/authentication/SSO-bots-auth/configure-web.png)

1. Die folgenden Schritte helfen Ihnen, die implizite Gewährung zu aktivieren:
    * Wählen Sie im linken Bereich **Authentifizierung** aus.
    * Aktivieren Sie die Kontrollkästchen **Zugriffstokens** und **ID-Tokens**.

    ![Fluss gewähren](~/assets/images/authentication/SSO-bots-auth/grant-flow.png)

    * Wählen Sie **Speichern** aus, um die Änderungen zu speichern.

1. Fügen Sie die erforderlichen **API-Berechtigungen** hinzu.
    * Wählen Sie im linken Bereich **API-Berechtigungen** aus.
    * Wählen Sie **Plattform hinzufügen** aus, um alle Berechtigungen hinzuzufügen, die Ihre App für nachgelagerte APIs benötigt, z. B. User.Read.

#### <a name="update-manifest-in-microsoft-azure-portal"></a>Aktualisieren Sie das Manifest im Microsoft Azure-Portal

Die folgenden Schritte führen Sie zum Aktualisieren des Bot-Manifests im Azure-Portal:

1. Wählen Sie im linken Bereich **Manifest** aus.
1. Stellen Sie sicher, dass das Konfigurationselement auf **"accessTokenAcceptedVersion": 2** eingestellt ist. Wenn nicht, ändern Sie den Wert auf **2**.

    ![Aktualisieren des Manifests](~/assets/images/bots/update-manifest.png)

   >[!NOTE]
   > Wenn Sie Ihren Bot bereits in Teams testen, müssen Sie sich von dieser App und von Teams abmelden. Melden Sie sich dann erneut an, um diese Änderung zu sehen.

1. Wählen Sie **Speichern**.

#### <a name="update-the-azure-portal-with-the-oauth-connection"></a>Aktualisieren Sie das Azure-Portal mit der OAuth-Verbindung

Die folgenden Schritte führen Sie zum Aktualisieren des Azure-Portals mit der OAuth-Verbindung:

1. Gehen Sie im Azure-Portal zu [**AzureBot**](https://ms.portal.azure.com/#create/Microsoft.AzureBot).
1. Gehen Sie im linken Bereich zu **Konfiguration**.
1. Wählen Sie **OAuth-Verbindungseinstellungen hinzufügen** aus.

    ![Konfigurationseinstellung](~/assets/images/authentication/SSO-bots-auth/auth-setting2.png)

1. Die folgenden Schritte führen Sie zum Ausfüllen des Formulars **Neue Verbindungseinstellung**:

   >[!NOTE]
   > In der Azure AD-Anwendung kann eine **implizite Gewährung** erforderlich sein.

    * Geben Sie **Name** auf der Seite **Neue Verbindungseinstellung** ein.

    >[!NOTE]
    > Der **Name** bezieht sich auf die Einstellungen Ihres Bot-Dienstcodes in *Schritt 5* von [Bot-SSO zur Laufzeit](#bot-sso-at-runtime).

    * Wählen Sie im Dropdown-Menü **Dienstanbieter** die Option **Azure Active Directory v2** aus.
    * Geben Sie die Client-Anmeldedaten wie **Client-ID** und **Client-Secret** für die Azure AD-Anwendung ein.
    * Verwenden Sie für die **Token-Austausch-URL** den unter [Aktualisieren Sie Ihr Teams-Anwendungsmanifest für Ihren Bot](#update-your-teams-application-manifest-for-your-bot) definierten Bereichswert, zum Beispiel `api://botid-<your-app-id>/`. Die Token Exchange-URL zeigt dem SDK an, dass diese Azure AD-Anwendung für SSO konfiguriert ist.
    * Geben Sie in die **Mandanten-ID** *common* ein.
    * Fügen Sie alle konfigurierten **Bereiche** hinzu, wenn Sie Berechtigungen für nachgelagerte APIs für Ihre Azure AD-Anwendung angeben. Mit der bereitgestellten Client-ID und dem Client-Geheimnis tauscht der Token-Speicher den Token gegen einen Graph-Token mit definierten Berechtigungen aus.
    * Wählen Sie **Speichern**.
    * Wählen Sie **Anwenden** aus.

    ![Verbindungseinstellung](~/assets/images/authentication/Bot-connection-setting.png)

### <a name="update-your-teams-application-manifest-for-your-bot"></a>Aktualisieren Sie Ihr Teams-Anwendungsmanifest für Ihren bot

Wenn die Anwendung einen eigenständigen Bot enthält, verwenden Sie den folgenden Code, um dem Teams-Anwendungsmanifest neue Eigenschaften hinzuzufügen:

```json
    "webApplicationInfo": 
        {
            "id": "00000000-0000-0000-0000-000000000000",
            "resource": "api://botid-00000000-0000-0000-0000-000000000000"
        }
```

Wenn die Anwendung einen Bot und eine Registerkarte enthält, verwenden Sie den folgenden Code, um dem Teams-Anwendungsmanifest neue Eigenschaften hinzuzufügen:

```json
    "webApplicationInfo": 
        {
            "id": "00000000-0000-0000-0000-000000000000",
            "resource": "api://subdomain.example.com/botid-00000000-0000-0000-0000-000000000000"
        }
```

**webApplicationInfo** ist das übergeordnete Element der folgenden Elemente:

* **id** – Die Client-ID der Anwendung. Dies ist die Anwendungs-ID, die Sie im Rahmen der Registrierung der Anwendung bei Azure AD erhalten haben. Teilen Sie diese Anwendungs-ID nicht mit mehreren Teams-Apps. Erstellen Sie eine neue Azure AD-App für jedes Anwendungsmanifest, das `webApplicationInfo` verwendet.
* **ressource** – Die Domäne und Unterdomäne Ihrer Anwendung. Es ist derselbe URI, einschließlich des `api://`-Protokolls, das Sie beim Erstellen Ihrer `scope` unter [App über das Azure AD-Portal registrieren](#register-your-app-through-the-azure-ad-portal) registriert haben. Schließen Sie den `access_as_user`-Pfad nicht in Ihre Ressource ein. Der Domänenteil dieses URI muss mit der Domäne und den Unterdomänen übereinstimmen, die in den URLs Ihres Teams-Anwendungsmanifests verwendet werden.

### <a name="add-the-code-to-request-and-receive-a-bot-token"></a>Fügen Sie den anzufordernden Code hinzu und erhalten Sie ein Bot-Token

#### <a name="request-a-bot-token"></a>Fordern Sie ein Bot-Token an

Die Anforderung zum Abrufen des Tokens ist eine normale POST-Nachrichtenanforderung, die das vorhandene Nachrichtenschema verwendet. Es ist in den Anhängen einer OAuthCard enthalten. Das Schema für die OAuthCard-Klasse ist in [Microsoft Bot Schema 4.0](/dotnet/api/microsoft.bot.schema.oauthcard?view=botbuilder-dotnet-stable&preserve-view=true) definiert und ähnelt einer Anmeldekarte. Teams behandelt diese Anforderung als unbeaufsichtigten Tokenerwerb, wenn die `TokenExchangeResource`-Eigenschaft auf der Karte ausgefüllt ist. Für den Teams-Kanal wird nur die Eigenschaft `Id` berücksichtigt, die eine Tokenanforderung eindeutig identifiziert.

>[!NOTE]
> Das Microsoft Bot Framework `OAuthPrompt` oder `MultiProviderAuthDialog` wird für die SSO-Authentifizierung unterstützt.

Wenn der Benutzer die Anwendung zum ersten Mal verwendet und die Zustimmung des Benutzers erforderlich ist, wird das folgende Dialogfeld angezeigt, um mit der Zustimmungserfahrung fortzufahren:

![Zustimmungsdialogfeld](~/assets/images/authentication/SSO-bots-auth/bot-consent-box.png)

Wenn der Benutzer **Weiter** auswählt, treten die folgenden Ereignisse auf:

* Wenn der Bot eine Anmeldeschaltfläche definiert, wird der Anmeldeablauf für Bots aktiviert, der dem Anmeldeablauf von einer OAuth-Kartenschaltfläche in einem Nachrichtenstrom ähnelt. Der Entwickler muss entscheiden, welche Berechtigungen die Zustimmung des Benutzers erfordern. Dieser Ansatz wird empfohlen, wenn Sie ein Token mit Berechtigungen über `openId` hinaus benötigen. Zum Beispiel, wenn Sie den Token gegen Graph-Ressourcen eintauschen möchten.

* Wenn der Bot keine Anmeldeschaltfläche auf der OAuth-Karte bereitstellt, ist die Zustimmung des Benutzers für einen minimalen Satz von Berechtigungen erforderlich. Dieses Token ist nützlich für die grundlegende Authentifizierung und zum Abrufen der E-Mail-Adresse des Benutzers.

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

#### <a name="receive-the-bot-token"></a>Das Bot-Token erhalten

Die Antwort mit dem Token wird über eine Aufrufaktivität mit demselben Schema gesendet wie andere Aufrufaktivitäten, die die Bots heute erhalten. Der einzige Unterschied ist der Name des Aufrufs, **Anmeldung/TokenExchange** und das Feld **Wert**. Das Feld **Wert** enthält die **ID**, eine Zeichenfolge der ursprünglichen Anforderung zum Abrufen des Tokens, und das Feld **Token**, einen Zeichenfolgenwert, der das Token enthält.

>[!NOTE]
> Sie erhalten möglicherweise mehrere Antworten für eine bestimmte Anfrage, wenn der Benutzer mehrere aktive Endpunkte hat. Sie müssen die Antworten mit dem Token deduplizieren.

##### <a name="c-code-to-handle-the-invoke-activity"></a>C#-Code zum Verarbeiten der Aufrufaktivität

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

`turnContext.activity.value` ist vom Typ [TokenExchangeInvokeRequest](/dotnet/api/microsoft.bot.schema.tokenexchangeinvokerequest?view=botbuilder-dotnet-stable&preserve-view=true) und enthält das Token, das von Ihrem Bot weiter verwendet werden kann. Sie müssen die Token aus Leistungsgründen speichern und aktualisieren.

### <a name="token-exchange-failure"></a>Fehler beim Token-Austausch

Wenn beim Token-Austausch ein Fehler auftritt, verwenden Sie den folgenden Code:

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

Um zu verstehen, was der Bot tut, wenn der Token-Austausch keine Zustimmungsaufforderung auslöst, sehen Sie sich die folgenden Schritte an:

>[!NOTE]
> Es ist keine Benutzeraktion erforderlich, da der Bot die Aktionen ausführt, wenn der Token-Austausch fehlschlägt.

1. Der Client beginnt eine Konversation mit dem Bot, der ein OAuth-Szenario auslöst.
2. Der Bot sendet eine OAuth-Karte an den Client zurück.
3. Der Client fängt die OAuth-Karte ab, bevor er sie dem Benutzer anzeigt, und prüft, ob sie eine `TokenExchangeResource`-Eigenschaft enthält.
4. Wenn die Eigenschaft vorhanden ist, sendet der Client eine `TokenExchangeInvokeRequest` an den Bot. Der Client muss über ein austauschbares Token für den Benutzer verfügen, das ein Azure AD v2-Token sein muss und dessen Zielgruppe mit der `TokenExchangeResource.Uri`-Eigenschaft identisch sein muss. Der Client sendet eine Aufrufaktivität mit dem folgenden Code an den Bot:

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

5. Der Bot verarbeitet die `TokenExchangeInvokeRequest` und gibt eine `TokenExchangeInvokeResponse` an den Client zurück. Der Client muss warten, bis er die `TokenExchangeInvokeResponse` erhält.

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

6. Wenn `TokenExchangeInvokeResponse` eine `status` von `200` hat, zeigt der Client die OAuth-Karte nicht an. Sehen Sie sich das [normale Flussbild](/azure/bot-service/bot-builder-concept-sso?view=azure-bot-service-4.0#sso-components-interaction&preserve-view=true) an. Für alle anderen `status` oder wenn `TokenExchangeInvokeResponse` nicht empfangen wird, zeigt der Client dem Benutzer die OAuth-Karte. Sehen Sie sich das [Fallback-Flow-Bild](/azure/bot-service/bot-builder-concept-sso?view=azure-bot-service-4.0#sso-components-interaction&preserve-view=true) an. Wenn Fehler oder nicht erfüllte Abhängigkeiten wie die Benutzereinwilligung vorliegen, stellt diese Aktivität sicher, dass der SSO-Fluss auf den normalen OAuthCard-Fluss zurückfällt.

### <a name="update-the-auth-sample"></a>Aktualisieren Sie das Authentifizierungsbeispiel

Öffnen Sie das [Teams-Authentifizierungsbeispiel](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth), und führen Sie dann die folgenden Schritte aus, um es zu aktualisieren:

1. Aktualisieren Sie den TeamsBot, um die Deduplizierung der eingehenden Anfrage zu handhaben, indem Sie den folgenden Code einfügen:

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
  
2. Aktualisieren Sie `appsettings.json` so, dass es `botId`, das Kennwort und den Verbindungsnamen enthält, der in [Azure-Portal mit der OAuth-Verbindung aktualisieren](#update-the-azure-portal-with-the-oauth-connection) definiert ist.
3. Aktualisieren Sie das Manifest und stellen Sie sicher, dass `token.botframework.com` in der Liste der gültigen Domänen enthalten ist. Weitere Informationen finden Sie unter [Teams-Authentifizierungsbeispiel](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth).
4. Zippen Sie das Manifest mit den Profilbildern, und installieren Sie es in Teams.

## <a name="code-sample"></a>Codebeispiel

|**Beispielname** | **Beschreibung** |**.NET** |**C#** |**Node.js** |
|----------------|-----------------|--------------|--------------|--------------|
|Bot-Framework-SDK | Dieser Beispielcode veranschaulicht, wie Sie mit der Authentifizierung in einem Bot für Microsoft Teams beginnen. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/46.teams-auth)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-conversation-sso-quickstart/csharp_dotnetcore/BotConversationSsoQuickstart)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-conversation-sso-quickstart/js)|

## <a name="step-by-step-guide"></a>Schrittweise Anleitung

Befolgen Sie die [schrittweise Anleitung](../../../sbs-bots-with-sso.yml), um einen Bot mit SSO-Authentifizierung zu erstellen.
