---
title: Verwenden von Microsoft Graph zur Aktivierung der proaktiven bot-Installation und-Nachrichten in Teams
description: Beschreibt proaktives Messaging in Microsoft Teams und die Implementierung.
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: Overview
keywords: Microsoft Teams Proactive Messaging Chat-Installations Diagramm
ms.openlocfilehash: f1d2c51957eefbc548918210b843e408eb1107c8
ms.sourcegitcommit: 7a2da3b65246a125d441a971e7e6a6418355adbe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "46587741"
---
# <a name="enable-proactive-bot-installation-and-proactive-messaging-in-teams-with-microsoft-graph-public-preview"></a>Aktivieren der proaktiven bot-Installation und proaktiver Nachrichten in Microsoft Graph-Teams (öffentliche Vorschau)

>[!IMPORTANT]
> Öffentliche Vorschaubilder von Microsoft Graph sind für den frühzeitigen Zugriff und Feedback verfügbar. Obwohl diese Version umfangreiche Tests unterzogen wurde, ist Sie nicht für die Verwendung in der Produktion vorgesehen.

## <a name="proactive-messaging-in-teams"></a>Proaktives Messaging in Microsoft Teams

Proaktive Nachrichten werden von Bots initiiert, um Unterhaltungen mit einem Benutzer zu starten. Sie dienen zahlreichen Zwecken, beispielsweise beim Senden von Begrüßungsnachrichten, durchführen von Umfragen oder Umfragen sowie bei der Ausstrahlung organisationsweiter Benachrichtigungen.  Proaktive Nachrichten in Microsoft Teams können entweder als **Ad-hoc** -oder **dialogbasierte** Unterhaltungen bereitgestellt werden:

|Nachrichtentyp | Beschreibung |
|----------------|-------------- |
|Ad-hoc-proaktive Nachricht| Der bot interject eine Nachricht, ohne den Unterhaltungs Fluss zu unterbrechen.|
|Dialog basierte proaktive Nachricht | Der bot erstellt einen neuen Dialog-Thread, übernimmt die Steuerung einer Unterhaltung, liefert die proaktive Nachricht, schließt und gibt die Steuerung an das vorherige Dialogfeld zurück.|

*Siehe*, [senden proaktiver Benachrichtigungen an Benutzer SDK V4](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp)

## <a name="proactive-app-installation-in-teams"></a>Proaktive App-Installation in Microsoft Teams

Bevor Ihr bot einen Benutzer proaktiv Nachrichten kann, muss er entweder als persönliche APP oder in einem Team installiert sein, in dem der Benutzer Mitglied ist. Gelegentlich müssen Sie Benutzer proaktiv Nachrichten, die noch _nicht_ mit Ihrer APP installiert oder zuvor interagiert haben. Zum Beispiel die Notwendigkeit, wichtige Informationen an alle Benutzer in Ihrer Organisation zu senden. Für solche Szenarien können Sie die Microsoft Graph-API verwenden, um Ihren bot proaktiv für Ihre Benutzer zu installieren.

## <a name="permissions"></a>Berechtigungen

Mit den [Ressourcentypen](/graph/api/resources/teamsappinstallation?view=graph-rest-1.0) Berechtigungen von Microsoft Graph teamsAppInstallation können Sie den Installationslebenszyklus Ihrer APP für alle Benutzer (persönlichen) oder Team (Kanal) Bereiche innerhalb der Microsoft Teams-Plattform verwalten:

|Anwendungsberechtigung | Beschreibung|
|------------------|---------------------|
|`TeamsAppInstallation.ReadWriteSelfForUser.All`|Ermöglicht einer Teams-APP, sich selbst für einen beliebigen **Benutzer**ohne vorherige Anmeldung oder Verwendung zu lesen, zu installieren, zu aktualisieren und zu deinstallieren.|
|`TeamsAppInstallation.ReadWriteSelfForTeam.All`|Ermöglicht einer Teams-APP, sich selbst in jedem **Team**zu lesen, zu installieren, zu aktualisieren und zu deinstallieren, ohne vorherige Anmeldung oder Verwendung.|

Um diese Berechtigungen zu verwenden, müssen Sie Ihrem App-Manifest einen [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) -Schlüssel mit den folgenden Werten hinzufügen:
> [!div class="checklist"]
> [!div class="checklist"]
>
> * **ID** – ihre Azure AD App-ID.
> * **Resource** – die Ressourcen-URL für die app.
>

>[!NOTE]
>
> * Ihr bot erfordert keine _Benutzer Delegierten_ Berechtigungen für die _Anwendung_ , da die Installation nicht für sich selbst, sondern für andere ist.
>
> * Ein Azure AD mandantenadministrator muss [explizit Berechtigungen für eine Anwendung erteilen](/graph/security-authorization#grant-permissions-to-an-application). Nachdem einer Anwendung Berechtigungen erteilt wurden, erhalten _alle_ Mitglieder des Azure AD Mandanten die gewährten Berechtigungen.

## <a name="enable-proactive-app-installation-and-messaging"></a>Aktivieren der proaktiven App-Installation und des Messaging

 > [!IMPORTANT]
>In Microsoft Graph werden nur apps installiert, die im [App-Katalog](../../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) Ihres Unternehmens oder in [AppSource](https://appsource.microsoft.com/)veröffentlicht wurden.

### <a name="-create-and-publish-your-proactive-messaging-bot-for-teams"></a>✔ Erstellen und Veröffentlichen Ihres proaktiven Messaging-bot für Teams

Für die ersten Schritte benötigen Sie einen [bot für Teams](../../bots/how-to/create-a-bot-for-teams.md) mit [proaktiven Messaging](../../concepts/bots/bot-conversations/bots-conv-proactive.md) Funktionen, die im [App-Katalog](../../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) Ihres Unternehmens oder in [AppSource](https://appsource.microsoft.com/) [veröffentlicht](../../concepts/deploy-and-publish/overview.md) werden.

>[!TIP]
> Die produktionsfertige [**Unternehmens-Communicator**](../..//samples/app-templates.md#company-communicator) -App-Vorlage aktiviert Broadcastnachrichten und ist eine gute Grundlage für die Erstellung Ihrer proaktiven bot-Anwendung.

### <a name="-get-the-teamsappid-for-your-app"></a>✔ Abrufen der `teamsAppId` für Ihre APP

**1.** Sie benötigen die `teamsAppId` für die nächsten Schritte.

Der `teamsAppId` kann aus dem App-Katalog Ihrer Organisation abgerufen werden:

**Microsoft Graph-Seitenreferenz:** [teamsApp Resource Type](/graph/api/resources/teamsapp?view=graph-rest-1.0)

**HTTP Get** -Anforderung:

```http
GET https://graph.microsoft.com/beta/appCatalogs/teamsApps?$filter=externalId eq '{IdFromManifest}'
```

Die Anforderung gibt ein `teamsApp` -Objekt zurück. Das zurückgegebene Objekt ist `id` die vom Katalog generierte APP-ID der APP und unterscheidet sich von der ID:, die Sie in Ihrem Teams-App-Manifest angegeben haben:

```json
{
  "value": [
    {
      "id": "b1c5353a-7aca-41b3-830f-27d5218fe0e5",
      "externalId": "f31b1263-ba99-435a-a679-911d24850d7c",
      "name": "Test App",
      "version": "1.0.1",
      "distributionMethod": "Organization"
    }
  ]
}
```

**2.** Wenn Ihre APP bereits für einen Benutzer im persönlichen Bereich hochgeladen/quer geladene wurde, können Sie die `teamsAppId` wie folgt abrufen:

**Microsoft Graph-Seitenreferenz:** [Auflisten von apps, die für den Benutzer installiert](/graph/api/user-list-teamsappinstallation?view=graph-rest-beta&tabs=http) sind

**HTTP Get** -Anforderung:

```http
GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

**3.** Wenn Ihre APP bereits für einen Kanal im Teambereich hochgeladen/quer geladene wurde, können Sie die `teamsAppId` wie folgt abrufen:

**Microsoft Graph-Seitenreferenz:** [Auflisten von apps im Team](/graph/api/teamsappinstallation-list?view=graph-rest-beta&tabs=http)

**HTTP Get** -Anforderung:

```http
GET https://graph.microsoft.com/beta/teams/{team-id}/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{manifestId}'
```

>[!TIP]
> Sie können nach einem der Felder des [**teamsApp**](/graph/api/resources/teamsapp?view=graph-rest-1.0) -Objekts filtern, um die Ergebnisliste einzugrenzen.

### <a name="-determine-whether-your-bot-is-currently-installed-for-a-message-recipient"></a>✔ Bestimmen, ob Ihr bot derzeit für einen Nachrichtenempfänger installiert ist

**Microsoft Graph-Seitenreferenz:** [Auflisten von apps, die für den Benutzer installiert](/graph/api/user-list-teamsappinstallation?view=graph-rest-beta&tabs=http) sind

**HTTP Get** -Anforderung:

```http
GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

Diese Anforderung gibt ein leeres Array zurück, wenn die APP nicht installiert ist, oder ein Array mit einem einzelnen [teamsAppInstallation](/graph/api/resources/teamsappinstallation?view=graph-rest-beta) -Objekt, wenn es installiert wurde.

### <a name="-install-your-app"></a>✔ Installieren Ihrer APP

**Microsoft Graph-Referenz:** [Installieren der APP für den Benutzer](/graph/api/user-add-teamsappinstallation?view=graph-rest-beta&tabs=http)

**Http Post** -Anforderung:

```http
POST https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps
{
   "teamsApp@odata.bind" : "https://graph.microsoft.com/beta/appCatalogs/teamsApps/{teamsAppId}"
}
```

Wenn der Benutzer Microsoft Teams ausführt, wird möglicherweise sofort die APP-Installation angezeigt. Alternativ kann ein Neustart erforderlich sein, um die installierte App anzuzeigen.

### <a name="-retrieve-the-conversation-chatid"></a>✔ Abrufen der Unterhaltungs- **Chat** -Funktion

Wenn Ihre APP für den Benutzer installiert ist, erhält der bot eine `conversationUpdate` [Ereignisbenachrichtigung](../../resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) , die die erforderlichen Informationen zum Senden der proaktiven Nachricht enthalten wird.

Die `chatId` kann auch wie folgt abgerufen werden:

**Microsoft Graph-Referenz:** [Chat abrufen](/graph/api/chat-get?view=graph-rest-beta&tabs=http)

**1.** Sie benötigen Ihre apps `{teamsAppInstallationId}` . Wenn Sie diesen nicht haben, verwenden Sie Folgendes:

**HTTP Get** -Anforderung:

```http
GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

Die **ID** -Eigenschaft der Antwort ist die `teamsAppInstallationId` .

**2.** führen Sie die folgende Anforderung aus, um Folgendes abzurufen `chatId` :

**HTTP Get** -Anforderung (Berechtigung `TeamsAppInstallation.ReadWriteSelfForUser.All` ):  

```http
 GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps/{teamsAppInstallationId}/chat
```

Die **ID** -Eigenschaft der Antwort ist die `chatId` .

Alternativ können Sie die `chatId` mit der folgenden Anforderung abrufen, aber Sie erfordert die breitere `Chat.Read.All` Berechtigung:

**HTTP Get** -Anforderung (Berechtigung `Chat.Read.All` ):

```http
GET https://graph.microsoft.com/beta/users/{user-id}/chats?$filter=installedApps/any(a:a/teamsApp/id eq '{teamsAppId}')
```

### <a name="-send-proactive-messages"></a>✔ Senden von proaktiven Nachrichten

Sobald Ihr bot für einen Benutzer oder ein Team hinzugefügt wurde und die erforderlichen Benutzerinformationen erworben hat, kann er mit dem [senden proaktiver Nachrichten](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp)beginnen.

# <a name="c--net"></a>[C#/.net](#tab/csharp)

Der folgende Codeausschnitt stammt aus den [Microsoft bot Framework-Beispielen für C#.](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/16.proactive-messages)

```csharp
using System.Collections.Concurrent;
using System.Collections.Generic;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.Bot.Builder;
using Microsoft.Bot.Schema;

namespace Microsoft.BotBuilderSamples
{
    public class ProactiveBot : ActivityHandler
    {
        // Message to send to users when the bot receives a Conversation Update event
        private const string WelcomeMessage = "Welcome to the Proactive Bot sample.  Navigate to http://localhost:3978/api/notify to proactively message everyone who has previously messaged this bot.";

        // Dependency injected dictionary for storing ConversationReference objects used in NotifyController to proactively message users
        private readonly ConcurrentDictionary<string, ConversationReference> _conversationReferences;

        public ProactiveBot(ConcurrentDictionary<string, ConversationReference> conversationReferences)
        {
            _conversationReferences = conversationReferences;
        }

        private void AddConversationReference(Activity activity)
        {
            var conversationReference = activity.GetConversationReference();
            _conversationReferences.AddOrUpdate(conversationReference.User.Id, conversationReference, (key, newValue) => conversationReference);
        }

        protected override Task OnConversationUpdateActivityAsync(ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
        {
            AddConversationReference(turnContext.Activity as Activity);

            return base.OnConversationUpdateActivityAsync(turnContext, cancellationToken);
        }

        protected override async Task OnMembersAddedAsync(IList<ChannelAccount> membersAdded, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
        {
            foreach (var member in membersAdded)
            {
                // Greet anyone that was not the target (recipient) of this message.
                if (member.Id != turnContext.Activity.Recipient.Id)
                {
                    await turnContext.SendActivityAsync(MessageFactory.Text(WelcomeMessage), cancellationToken);
                }
            }
        }

        protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
        {
            AddConversationReference(turnContext.Activity as Activity);

            // Echo back what the user said
            await turnContext.SendActivityAsync(MessageFactory.Text($"You sent '{turnContext.Activity.Text}'"), cancellationToken);
        }
    }
}
```

# <a name="javascript"></a>[JavaScript](#tab/javascript)

Der folgende Codeausschnitt stammt aus den [Microsoft bot Framework-Beispielen für JavaScript](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/16.proactive-messages).

```javascript
const { ActivityHandler, TurnContext } = require('botbuilder');

class ProactiveBot extends ActivityHandler {
    constructor(conversationReferences) {
        super();

        // Dependency injected dictionary for storing ConversationReference objects used in NotifyController to proactively message users
        this.conversationReferences = conversationReferences;

        this.onConversationUpdate(async (context, next) => {
            this.addConversationReference(context.activity);

            await next();
        });

        this.onMembersAdded(async (context, next) => {
            const membersAdded = context.activity.membersAdded;
            for (let cnt = 0; cnt < membersAdded.length; cnt++) {
                if (membersAdded[cnt].id !== context.activity.recipient.id) {
                    const welcomeMessage = 'Welcome to the Proactive Bot sample.  Navigate to http://localhost:3978/api/notify to proactively message everyone who has previously messaged this bot.';
                    await context.sendActivity(welcomeMessage);
                }
            }

            // By calling next() you ensure that the next BotHandler is run.
            await next();
        });

        this.onMessage(async (context, next) => {
            this.addConversationReference(context.activity);

            // Echo back what the user said
            await context.sendActivity(`You sent '${ context.activity.text }'`);
            await next();
        });
    }

    addConversationReference(activity) {
        const conversationReference = TurnContext.getConversationReference(activity);
        this.conversationReferences[conversationReference.conversation.id] = conversationReference;
    }
}

module.exports.ProactiveBot = ProactiveBot;

```
---

## <a name="related-topic-for-teams-administrators"></a>Verwandtes Thema für Microsoft Teams-Administratoren
>
> [!div class="nextstepaction"]
> [**Verwalten von App-Setup Richtlinien in Microsoft Teams**](/MicrosoftTeams/teams-app-setup-policies#create-a-custom-app-setup-policy)

## <a name="view-additional-code-samples"></a>Anzeigen zusätzlicher Codebeispiele
>
> [!div class="nextstepaction"]
> [**Proaktive Messaging-Codebeispiele für Teams**](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)
>
