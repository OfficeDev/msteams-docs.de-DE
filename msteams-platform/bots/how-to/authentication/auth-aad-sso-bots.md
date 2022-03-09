---
title: Unterstützung für einmaliges Anmelden für Bots
description: Beschreibt, wie ein Benutzertoken abgerufen wird. Derzeit kann ein Bot-Entwickler eine Anmeldekarte oder den Azure-Bot-Dienst mit OAuth-Kartenunterstützung verwenden.
keywords: Token, Benutzertoken, SSO-Unterstützung für Bots, Berechtigung, Microsoft Graph, Azure AD
ms.localizationpriority: medium
ms.topic: conceptual
ms.openlocfilehash: a51b96cdb5d2b37f826f533dae58bed117b71700
ms.sourcegitcommit: 830fdc80556a5fde642850dd6b4d1b7efda3609d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/09/2022
ms.locfileid: "63399366"
---
# <a name="single-sign-on-sso-support-for-bots"></a>SSO-Unterstützung (Single Sign-On) für Bots

Die Single Sign-On-Authentifizierung in Microsoft Azure Active Directory (Azure AD) aktualisiert das Authentifizierungstoken im Hintergrund, um zu minimieren, wie oft Benutzer ihre Anmeldeinformationen eingeben müssen. Wenn Benutzer der Verwendung Ihrer App zustimmen, müssen sie auf einem anderen Gerät nicht erneut zustimmen, da sie automatisch angemeldet sind. Registerkarten und Bots weisen einen ähnlichen Ablauf für die SSO-Unterstützung auf. Bot [fordert jedoch Token an](#request-a-bot-token) und [empfängt Antworten](#receive-the-bot-token) mit einem anderen Protokoll.

>[!NOTE]
> OAuth 2.0 ist ein offener Standard für die Authentifizierung und Autorisierung, der von Azure AD und vielen anderen Identitätsanbietern verwendet wird. Ein grundlegendes Verständnis von OAuth 2.0 ist eine Voraussetzung für die Arbeit mit der Authentifizierung in Teams.

## <a name="bot-sso-at-runtime"></a>Bot-SSO zur Laufzeit

Die folgende Abbildung veranschaulicht den Fluss von SSO in Bots:

![Bot-SSO zur Laufzeit (Diagramm)](../../../assets/images/bots/bots-sso-diagram.png)

Die folgenden Schritte helfen Ihnen bei Authentifizierungs- und Bot-Anwendungstoken:

1. Der Bot sendet eine Nachricht an Teams mit einer OAuthCard, die ein Authentifizierungstoken für die Botanwendung enthält`tokenExchangeResource`. Der Benutzer erhält auf allen aktiven Benutzerendpunkten Nachrichten.

   > [!NOTE]
   >
   > * Ein Benutzer kann mehrere aktive Endpunkte gleichzeitig haben.
   > * Der Bot-Token wird von jedem aktiven Benutzerendpunkt erhalten.
   > * Die App muss für SSO-Support im persönlichen Bereich installiert sein.

1. Wenn der aktuelle Benutzer Ihre Bot-Anwendung zum ersten Mal verwendet, wird dem Benutzer eine Anforderungsaufforderung angezeigt, um eine der folgenden Aktionen auszuführen:
    * Falls notwendig die Zustimmung geben.
    * Erhöhte Authentifizierung durchführen, z. B. die zweistufige Authentifizierung.

1. Teams fordert das Botanwendungstoken vom Azure AD Endpunkt für den aktuellen Benutzer an.

1. Azure AD sendet das Bot-Anwendungstoken an die Teams Anwendung.

1. Teams sendet das Token als Teil des Wertobjekts, das vom Aufrufen mit **Anmeldung/tokenExchange** zurückgegeben wird, an den Bot.
  
1. Das analysierte Token in der Bot-Anwendung stellt die erforderlichen Informationen zur Verfügung, wie z. B. die E-Mail-Adresse des Benutzers.
  
## <a name="develop-an-sso-teams-bot"></a>Entwickeln eines SSO-Teams-Bots
  
Die folgenden Schritte führen Sie zum Entwickeln von SSO Teams Bot:

1. [Registrieren Sie Ihre App über das Azure AD Portal](#register-your-app-through-the-azure-ad-portal).
1. [Aktualisieren Sie Ihr Teams Anwendungsmanifest für Ihren Bot](#update-your-teams-application-manifest-for-your-bot).
1. [Fügen Sie den Code hinzu, um ein Bottoken anzufordern und zu erhalten](#add-the-code-to-request-and-receive-a-bot-token).

### <a name="register-your-app-through-the-azure-ad-portal"></a>Registrieren Ihrer App über das Azure AD-Portal

Die Schritte zum Registrieren Ihrer App über das Azure AD-Portal ähneln dem [SSO-Fluss der Registerkarte](../../../tabs/how-to/authentication/auth-aad-sso.md). Die folgenden Schritte führen Sie zum Registrieren Ihrer App:

1. Registrieren Sie eine neue Anwendung im [Portal Azure Active Directory – App-Registrierungen](https://go.microsoft.com/fwlink/?linkid=2083908).

1. Wählen Sie **Neue Registrierung** aus. Die Seite **Anwendung registrieren** wird angezeigt.

    ![Neue Registrierung](~/assets/images/authentication/SSO-bots-auth/app-registration.png)

1. **Führen Sie im Register an application** die folgenden Schritte aus:

   > [!NOTE]
   >
   > Die Benutzer werden nicht zur Zustimmung aufgefordert und erhalten sofort Zugriffstoken, wenn die Azure AD-App im selben Mandanten registriert ist, in dem sie eine Authentifizierungsanforderung in Teams stellen. Die Benutzer müssen den Berechtigungen jedoch zustimmen, wenn die Azure AD-App in einem anderen Mandanten registriert ist.

    * Geben Sie **den Namen** für Ihre App ein.
    * Wählen Sie **unterstützte Kontotypen** aus, z. B. einzelmandant oder mehrinstanzenfähig.
    * Wählen Sie **Registrieren** aus.

    ![Registrieren einer Anwendung](~/assets/images/authentication/SSO-bots-auth/register-application.png)

1. Wechseln Sie zur Übersichtsseite.
1. Kopieren Sie den Wert der **Anwendungs-ID (Client-ID).**
1. Wechseln **Sie unter "Verwalten**" zu **"API verfügbar machen**".

   > [!TIP]
   > Um Ihr App-Manifest später zu aktualisieren, speichern Sie den **Wert der Anwendungs-ID (Client-ID).**

   > [!IMPORTANT]
   >
   > * Wenn Sie einen eigenständigen Bot erstellen, geben Sie den Anwendungs-ID-URI als `api://botid-{YourBotId}`. Hier *ist YourBotId* Ihre Azure AD Anwendungs-ID.
   > * Wenn Sie eine App mit einem Bot und einer Registerkarte erstellen, geben Sie den Anwendungs-ID-URI als `api://fully-qualified-domain-name.com/botid-{YourBotId}` ein.

1. Wählen Sie **Bereich hinzufügen**.
1. Geben Sie `access_as_user` in dem Eingabeaufforderungsbereich als **Bereichsname** ein.

   >[!NOTE]
   > Der Bereich "access_as_user", der zum Hinzufügen einer Client-App verwendet wird, richtet sich an "Administratoren und Benutzer".
   >
   > Sie müssen sich der folgenden wichtigen Einschränkungen bewusst sein:
   >
   > * Es werden nur Microsoft Graph API-Berechtigungen auf Benutzerebene unterstützt, z. B. E-Mail, Profil, offline_access und OpenId. Wenn Sie Zugriff auf andere Microsoft Graph Bereiche benötigen, z`User.Read`. B. oder `Mail.Read`, finden Sie weitere Informationen unter [Abrufen eines Zugriffstokens mit Graph Berechtigungen](../../../tabs/how-to/authentication/auth-aad-sso.md#get-an-access-token-with-graph-permissions).
   > * Der Domänenname Ihrer Anwendung muss mit dem Domänennamen übereinstimmen, den Sie für Ihre Azure AD Anwendung registriert haben.
   > * Mehrere Domänen pro App werden derzeit nicht unterstützt.
   > * Anwendungen, die die `azurewebsites.net` Domäne verwenden, werden nicht unterstützt, da sie häufig vorkommen und ein Sicherheitsrisiko darstellen können.

1. Geben Sie in der **Wer zustimmen können?**, **Administratoren und Benutzer** ein.
1. Geben Sie die folgenden Details ein, um die Administrator- und Benutzerzustimmungsaufforderungen mit werten zu konfigurieren, die für den `access_as_user`Bereich geeignet sind.
    * **Anzeigename der Administratorzustimmung**: Teams können auf das Profil des Benutzers zugreifen.
    * **Beschreibung der Administratoreinwilligung**: Teams können die Web-APIs der App als aktueller Benutzer aufrufen.
    * **Anzeigename der Zustimmung des Benutzers**: Teams können auf Ihr Profil zugreifen und Anforderungen in Ihrem Auftrag stellen.
    * **Beschreibung der Benutzergenehmigung**: Teams können die APIs dieser App mit den gleichen Rechten aufrufen wie Sie.

    ![Administrator und Benutzer](~/assets/images/authentication/SSO-bots-auth/add-a-scope.png)

1. Stellen Sie sicher, dass der Status auf **"Aktiviert**" festgelegt ist.

    ![Status](~/assets/images/authentication/SSO-bots-auth/enabled-state.png)

1. Wählen Sie **Bereich hinzufügen** aus, um die Details zu speichern. Der Domänenteil des angezeigten **Bereichsnamens** muss automatisch mit dem **Anwendungs-ID-URI** übereinstimmen, der im vorherigen Schritt festgelegt wurde, und `/access_as_user` muss am Ende `api://subdomain.example.com/00000000-0000-0000-0000-000000000000/access_as_user`angefügt werden.

1. Identifizieren Sie in den **autorisierten Clientanwendungen** die Anwendungen, die Sie für die Webanwendung Ihrer App autorisieren möchten.
1. **Hinzufügen einer Clientanwendung** auswählen.

    ![Clientanwendung](~/assets/images/authentication/SSO-bots-auth/add-client-application.png)

1. Geben Sie jede der folgenden Client-IDs ein, und wählen Sie den autorisierten Bereich aus, den Sie im vorherigen Schritt erstellt haben:
    * `1fec8e78-bce4-4aaf-ab1b-5451cc387264` für Teams Mobile oder Desktopanwendung.
    * `5e3ce6c0-2b1f-4285-8d4b-75ee78787346` für Teams-Webanwendung.

    ![Client-ID](~/assets/images/authentication/SSO-bots-auth/add-client-id.png)

1. Wechseln Sie zur **Authentifizierung**.
1. Wählen Sie in **Plattformkonfigurationen** **die Option "Plattform hinzufügen**" aus.

    ![Plattform](~/assets/images/authentication/SSO-bots-auth/platform-configuration.png)

1. Klicken Sie auf **Web**.

    ![Konfigurieren der Plattform](~/assets/images/authentication/SSO-bots-auth/configure-platform.png)

1. Geben Sie die **Umleitungs-URIs** für Ihre App ein.

   >[!NOTE]
   > Dieser URI sollte ein vollqualifizierte Domänenname sein. Es folgt auch die API-Route, an die eine Authentifizierungsantwort gesendet wird. Wenn Sie einem der Teams-Beispiele folgen, lautet der URI `https://token.botframework.com/.auth/web/redirect`. Weitere Informationen finden Sie unter [OAuth 2.0-Autorisierungscodefluss](/azure/active-directory/develop/v2-oauth2-auth-code-flow).

    ![Umleitungs-URIs](~/assets/images/authentication/SSO-bots-auth/configure-web.png)

1. Die folgenden Schritte helfen Ihnen beim Aktivieren der impliziten Genehmigung:
    * Wählen Sie im linken Bereich die **Authentifizierung** aus.
    * Aktivieren Sie die Kontrollkästchen **für Zugriffstoken** und **ID-Token** .

    ![Genehmigungsfluss](~/assets/images/authentication/SSO-bots-auth/grant-flow.png)

    * Wählen Sie **"Speichern** " aus, um die Änderungen zu speichern.

1. Fügen Sie die erforderlichen **API-Berechtigungen hinzu**.
    * Wählen Sie im linken Bereich **API-Berechtigungen** aus.
    * Wählen Sie " **Plattform hinzufügen** " aus, um alle Berechtigungen hinzuzufügen, die Ihre App für downstream-APIs benötigt, z. B. User.Read.

#### <a name="update-manifest-in-microsoft-azure-portal"></a>Aktualisieren des Manifests im Microsoft Azure Portal

Die folgenden Schritte führen Sie zum Aktualisieren des Bot-Manifests im Azure-Portal:

1. Select **Manifest** from the left pane.
1. Stellen Sie sicher, dass das Konfigurationselement auf **"accessTokenAcceptedVersion" festgelegt ist: 2**. Wenn dies nicht der Fall ist, ändern Sie den Wert in **2**.

    ![Updatemanifest](~/assets/images/bots/update-manifest.png)

   >[!NOTE]
   > Wenn Sie Ihren Bot bereits in Teams testen, müssen Sie sich von dieser App abmelden und sich von Teams abmelden. Melden Sie sich dann erneut an, um diese Änderung zu sehen.

1. Wählen Sie **Speichern** aus.

#### <a name="update-the-azure-portal-with-the-oauth-connection"></a>Aktualisieren des Azure-Portals mit der OAuth-Verbindung

Die folgenden Schritte führen Sie zum Aktualisieren des Azure-Portals mit der OAuth-Verbindung:

1. Wechseln Sie im Azure-Portal zu [**AzureBot**](https://ms.portal.azure.com/#create/Microsoft.AzureBot)
1. Wechseln Sie im linken Bereich zu **"Konfiguration** ".
1. Wählen Sie **OAuth-Verbindungs-Einstellungen hinzufügen** aus.

    ![Konfigurationseinstellung](~/assets/images/authentication/SSO-bots-auth/auth-setting2.png)

1. Die folgenden Schritte führen Sie zum Ausfüllen des Formulars für neue **Verbindungseinstellungen** :

   >[!NOTE]
   > **Die implizite Genehmigung** kann in der Azure AD Anwendung erforderlich sein.

    * Geben Sie auf der Seite **"Neue Verbindungseinstellung**" den **Namen** ein.

    >[!NOTE]
    > Der **Name** wird auf die Einstellungen Ihres Bot-Dienstcodes in *Schritt 5* von [Bot SSO zur Laufzeit](#bot-sso-at-runtime) verwiesen.

    * Wählen Sie in der Dropdownliste "**Dienstanbieter**" **Azure Active Directory v2** aus.
    * Geben Sie die Clientanmeldeinformationen ein, z. B. **Client-ID** und **geheimer Clientschlüssel** für die Azure AD Anwendung.
    * Verwenden Sie für die **Token-Exchange-URL** den bereichswert, der in [Update Your Teams application manifest for your bot](#update-your-teams-application-manifest-for-your-bot) for example, `api://botid-<your-app-id>/`definiert ist. Die Token-Exchange-URL gibt dem SDK an, dass diese Azure AD Anwendung für SSO konfiguriert ist.
    * Geben Sie in der **Mandanten-ID** *"Allgemein*" ein.
    * Fügen Sie alle **Bereiche** hinzu, die beim Angeben von Berechtigungen für downstreame APIs für Ihre Azure AD-Anwendung konfiguriert sind. Mit der bereitgestellten Client-ID und dem geheimen Clientschlüssel tauscht der Tokenspeicher das Token gegen ein Diagrammtoken mit definierten Berechtigungen aus.
    * Wählen Sie **Speichern** aus.
    * Wählen Sie **Anwenden** aus.

    ![Verbindungseinstellung](~/assets/images/authentication/Bot-connection-setting.png)

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

* **id** – Die Client-ID der Anwendung. Dies ist die Anwendungs-ID, die Sie beim Registrieren der Anwendung bei Azure AD erhalten haben. Geben Sie diese Anwendungs-ID nicht für mehrere Teams Apps frei. Erstellen Sie eine neue Azure AD-App für jedes Anwendungsmanifest, das `webApplicationInfo`verwendet.
* **ressource** – Die Domäne und Unterdomäne Ihrer Anwendung. Es handelt sich um den gleichen URI, einschließlich des Protokolls, das `api://` Sie beim Erstellen Ihrer `scope` [App in "Registrieren" über das Azure AD-Portal registriert haben](#register-your-app-through-the-azure-ad-portal). Fügen Sie den `access_as_user` Pfad nicht in Ihre Ressource ein. Der Domänenteil dieses URI muss mit der Domäne und den Unterdomänen übereinstimmen, die in den URLs Ihres Teams Anwendungsmanifests verwendet werden.

### <a name="add-the-code-to-request-and-receive-a-bot-token"></a>Hinzufügen des Codes zum Anfordern und Empfangen eines Bottokens

#### <a name="request-a-bot-token"></a>Anfordern eines Bottokens

Die Anforderung zum Abrufen des Tokens ist eine normale POST-Nachrichtenanforderung mithilfe des vorhandenen Nachrichtenschemas. Es ist in den Anlagen einer OAuthCard enthalten. Das Schema für die OAuthCard-Klasse ist in [Microsoft Bot Schema 4.0](/dotnet/api/microsoft.bot.schema.oauthcard?view=botbuilder-dotnet-stable&preserve-view=true) definiert und ähnelt einer Anmeldekarte. Teams behandelt diese Anforderung als automatische Tokenerfassung, wenn die `TokenExchangeResource` Eigenschaft auf der Karte aufgefüllt wird. Für den Teams Kanal wird nur die `Id` Eigenschaft berücksichtigt, die eine Tokenanforderung eindeutig identifiziert.

>[!NOTE]
> Die Microsoft Bot Framework `OAuthPrompt` oder die wird für die `MultiProviderAuthDialog` SSO-Authentifizierung unterstützt.

Wenn der Benutzer die Anwendung zum ersten Mal verwendet und die Zustimmung des Benutzers erforderlich ist, wird das folgende Dialogfeld angezeigt, um mit der Zustimmung fortzufahren:

![Dialogfeld "Zustimmung"](~/assets/images/authentication/SSO-bots-auth/bot-consent-box.png)

Wenn der Benutzer **Weiter** auswählt, treten die folgenden Ereignisse auf:

* Wenn der Bot eine Anmeldeschaltfläche definiert, wird der Anmeldefluss für Bots aktiviert, der dem Anmeldefluss von einer OAuth-Kartenschaltfläche in einem Nachrichtendatenstrom ähnelt. Der Entwickler muss entscheiden, welche Berechtigungen die Zustimmung des Benutzers erfordern. Dieser Ansatz wird empfohlen, wenn Sie ein Token mit berechtigungen übersteigt `openId`. Wenn Sie z. B. das Token gegen Graph-Ressourcen austauschen möchten.

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

Die Antwort mit dem Token wird über eine Aufrufaktivität mit demselben Schema wie andere Aufrufaktivitäten gesendet, die die Bots heute erhalten. Der einzige Unterschied ist der Aufrufname, **die Anmeldung/tokenExchange** und das **Wertfeld** . Das **Wertfeld** enthält die **ID**, eine Zeichenfolge der anfänglichen Anforderung zum Abrufen des Tokens und das **Tokenfeld** , einen Zeichenfolgenwert einschließlich des Tokens.

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

Wenn ein Fehler beim Austausch von Token auftritt, verwenden Sie den folgenden Code:

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
4. Wenn die Eigenschaft vorhanden ist, sendet der Client einen `TokenExchangeInvokeRequest` an den Bot. Der Client muss über ein austauschbares Token für den Benutzer verfügen, bei dem es sich um ein Azure AD v2-Token handelt und dessen Zielgruppe mit der Eigenschaft identisch `TokenExchangeResource.Uri` sein muss. Der Client sendet eine Aufrufaktivität mit dem folgenden Code an den Bot:

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

5. Der Bot verarbeitet die `TokenExchangeInvokeRequest` und gibt einen `TokenExchangeInvokeResponse` Zurück an den Client zurück. Der Client muss warten, bis er die `TokenExchangeInvokeResponse`.

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

6. Wenn dies `TokenExchangeInvokeResponse` der `status` `200`Fall ist, zeigt der Client die OAuth-Karte nicht an. Sehen Sie sich das [normale Flussbild an](/azure/bot-service/bot-builder-concept-sso?view=azure-bot-service-4.0#sso-components-interaction&preserve-view=true). Bei anderen `status` Oder wenn der `TokenExchangeInvokeResponse` Client nicht empfangen wird, zeigt der Client dem Benutzer die OAuth-Karte an. Sehen Sie sich das [Fallback-Flussbild an](/azure/bot-service/bot-builder-concept-sso?view=azure-bot-service-4.0#sso-components-interaction&preserve-view=true). Wenn Fehler oder nicht erfüllte Abhängigkeiten wie die Zustimmung des Benutzers vorhanden sind, stellt diese Aktivität sicher, dass der SSO-Fluss auf den normalen OAuthCard-Fluss zurückfällt.

### <a name="update-the-auth-sample"></a>Aktualisieren des Authentifizierungsbeispiels

Öffnen [Sie Teams Authentifizierungsbeispiel](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth), und führen Sie dann die folgenden Schritte aus, um es zu aktualisieren:

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
  
2. Aktualisieren Sie `appsettings.json` , um das `botId`Kennwort und den im [Azure-Portal mit der OAuth-Verbindung](#update-the-azure-portal-with-the-oauth-connection) definierten Verbindungsnamen einzuschließen.
3. Aktualisieren Sie das Manifest, und stellen Sie sicher, dass es `token.botframework.com` sich in der Liste der gültigen Domänen befindet. Weitere Informationen finden Sie unter [Teams Authentifizierungsbeispiel](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth).
4. Zippen Sie das Manifest mit den Profilimages, und installieren Sie es in Teams.

## <a name="code-sample"></a>Codebeispiel

|**Beispielname** | **Beschreibung** |**.NET** |
|----------------|-----------------|--------------|
|Bot framework SDK | Beispiel für die Verwendung des Bot Framework SDK. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/46.teams-auth)|

## <a name="step-by-step-guide"></a>Schrittweise Anleitung

Befolgen Sie die [schrittweise Anleitung](../../../sbs-bots-with-sso.yml), die Ihnen beim Erstellen eines Bots mit aktivierter SSO-Authentifizierung hilft.
