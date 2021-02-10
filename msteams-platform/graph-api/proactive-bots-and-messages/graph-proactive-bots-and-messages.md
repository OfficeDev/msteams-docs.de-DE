---
title: Verwenden von Microsoft Graph zum Aktivieren der proaktiven Botinstallation und -messaging in Teams
description: Beschreibt proaktives Messaging in Teams und die Implementierung.
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: Overview
keywords: Graph zur proaktiven Messaging-Chatinstallation für Teams
ms.openlocfilehash: 4f26b4d2f4e82fcf50b7a35c46bcd07e5afecf19
ms.sourcegitcommit: b99ed616db734371e4af4594b7e895c5b05737c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2021
ms.locfileid: "50162894"
---
# <a name="enable-proactive-bot-installation-and-proactive-messaging-in-teams-with-microsoft-graph-public-preview"></a>Aktivieren einer proaktiven Botinstallation und proaktivem Messaging in Teams mit Microsoft Graph (Public Preview)

>[!IMPORTANT]
> Microsoft Graph und Microsoft Teams public previews are available for early-access and feedback. Obwohl diese Version umfassenden Tests unterzogen wurde, ist sie nicht für die Verwendung in der Produktion vorgesehen.

## <a name="proactive-messaging-in-teams"></a>Proaktives Messaging in Teams

Proaktive Nachrichten werden von Bots initiiert, um Unterhaltungen mit einem Benutzer zu beginnen. Sie dienen vielen Zwecken, z. B. dem Senden von Begrüßungsnachrichten, dem Durchführen von Umfragen oder Umfragen und der Übertragung organisationsweiter Benachrichtigungen.  Proaktive Nachrichten in Teams können als **Ad-hoc-** oder **dialogbasierte Unterhaltungen übermittelt** werden:

|Nachrichtentyp | Beschreibung |
|----------------|-------------- |
|Proaktive Ad-hoc-Nachricht| Der Bot interjects a message without interrupting the conversation flow.|
|Dialogbasierte proaktive Nachricht | Der Bot erstellt einen neuen Dialogthread, übernimmt die Kontrolle über eine Unterhaltung, übermittelt die proaktive Nachricht, schließt und gibt die Steuerung an das vorherige Dialogfeld zurück.|

*Siehe*, [proaktive Benachrichtigungen an Benutzer SDK v4 senden](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true)

## <a name="proactive-app-installation-in-teams"></a>Proaktive App-Installation in Teams

Bevor Ihr Bot proaktiv eine Nachricht an einen Benutzer senden kann, muss er entweder als persönliche App oder in einem Team installiert werden, in dem der Benutzer Mitglied ist. Manchmal müssen Sie benutzer, die nicht  installiert oder zuvor mit Ihrer App interagiert haben, proaktiv nachrichten. Beispielsweise müssen wichtige Informationen an alle In ihrer Organisation gesendet werden. Für solche Szenarien können Sie die Microsoft Graph-API verwenden, um Ihren Bot proaktiv für Ihre Benutzer zu installieren.

## <a name="permissions"></a>Berechtigungen

Mit Microsoft Graph [teamsAppInstallation-Ressourcentypberechtigungen](/graph/api/resources/teamsappinstallation?view=graph-rest-1.0&preserve-view=true) können Sie den Installationslebenszyklus Ihrer App für alle Benutzer- oder Teambereiche (Kanal) innerhalb der Microsoft Teams-Plattform verwalten:

|Anwendungsberechtigung | Beschreibung|
|------------------|---------------------|
|`TeamsAppInstallation.ReadWriteSelfForUser.All`|Ermöglicht einer Teams-App, sich selbst für jeden Benutzer ohne vorherige Anmeldung oder Verwendung zu lesen, zu installieren, zu aktualisieren und zu deinstallieren.|
|`TeamsAppInstallation.ReadWriteSelfForTeam.All`|Ermöglicht einer Teams-App, sich selbst in einem beliebigen Team zu lesen, zu installieren, zu aktualisieren und zu deinstallieren, ohne sich vorher anmelden oder verwenden zu müssen.|

Um diese Berechtigungen zu verwenden, müssen Sie ihrem [App-Manifest einen webApplicationInfo-Schlüssel](../../resources/schema/manifest-schema.md#webapplicationinfo) mit den folgenden Werten hinzufügen:
> [!div class="checklist"]
> [!div class="checklist"]
>
> * **id**  – Ihre Azure AD-App-ID.
> * **-Ressource** – die Ressourcen-URL für die App.
>

>[!NOTE]
>
> * Ihr Bot erfordert _keine delegierten_ Berechtigungen _der_ Anwendung, da die Installation nicht für sie selbst, sondern für andere personen ist.
>
> * Ein Azure AD-Mandantenadministrator muss [einer Anwendung explizit Berechtigungen erteilen.](/graph/security-authorization#grant-permissions-to-an-application) Nachdem einer Anwendung Berechtigungen erteilt wurden, _erhalten_ alle Mitglieder des Azure AD-Mandanten die erteilten Berechtigungen.

## <a name="enable-proactive-app-installation-and-messaging"></a>Aktivieren der proaktiven Installation und Messaging von Apps

 > [!IMPORTANT]
>Microsoft Graph installiert nur Apps, die [](../../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) im App-Katalog Ihrer Organisation oder in [AppSource veröffentlicht wurden.](https://appsource.microsoft.com/)

### <a name="-create-and-publish-your-proactive-messaging-bot-for-teams"></a>✔ Erstellen und Veröffentlichen Ihres proaktiven Messaging-Bots für Teams

Für die ersten Schritte benötigen Sie [](../../concepts/bots/bot-conversations/bots-conv-proactive.md) einen Bot [](../../concepts/deploy-and-publish/overview.md) für [Teams](../../bots/how-to/create-a-bot-for-teams.md) mit [](../../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) proaktiven Messagingfunktionen, der im App-Katalog Ihrer Organisation oder in [AppSource veröffentlicht wird.](https://appsource.microsoft.com/)

>[!TIP]
> Die produktionsbereite [**Unternehmens-Communicator-App-Vorlage**](../..//samples/app-templates.md#company-communicator) ermöglicht Übertragungsnachrichten und ist eine gute Grundlage für die Erstellung Ihrer proaktiven Botanwendung.

### <a name="-get-the-teamsappid-for-your-app"></a>✔ Für Ihre `teamsAppId` App erhalten

**1.** Sie benötigen den `teamsAppId`  für die nächsten Schritte.

Der `teamsAppId` kann aus dem App-Katalog Ihrer Organisation abgerufen werden:

**Microsoft Graph-Seitenreferenz:** [teamsApp-Ressourcentyp](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true)

**HTTP GET-Anforderung:**

```http
GET https://graph.microsoft.com/v1.0/appCatalogs/teamsApps?$filter=externalId eq '{IdFromManifest}'
```

Die Anforderung gibt ein Objekt `teamsApp`  zurück. Die zurückgegebenen Objekte sind die vom App-Katalog generierte App-ID und unterscheiden sich von der "ID:", die Sie in Ihrem `id`  Teams-App-Manifest angegeben haben:

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

**2.**  Wenn Ihre App bereits für einen Benutzer im persönlichen Bereich hochgeladen oder sideloaded wurde, können Sie folgendes `teamsAppId` abrufen:

**Microsoft Graph-Seitenreferenz: Für** [Benutzer installierte Apps auflisten](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

**HTTP GET-Anforderung:**

```http
GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
```

**3.** Wenn Ihre App bereits für einen Kanal im Teambereich hochgeladen/sideloaded wurde, können Sie folgendes `teamsAppId` abrufen:

**Microsoft Graph-Seitenreferenz: Apps** [im Team auflisten](/graph/api/team-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

**HTTP GET-Anforderung:**

```http
GET https://graph.microsoft.com/v1.0/teams/{team-id}/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
```

>[!TIP]
> Sie können nach den Feldern des [**teamsApp-Objekts**](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true) filtern, um die Liste der Ergebnisse zu einengt.

### <a name="-determine-whether-your-bot-is-currently-installed-for-a-message-recipient"></a>✔ Bestimmen, ob Ihr Bot derzeit für einen Nachrichtenempfänger installiert ist

**Microsoft Graph-Seitenreferenz: Für** [Benutzer installierte Apps auflisten](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

**HTTP GET-Anforderung:**

```http
GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

Diese Anforderung gibt ein leeres Array zurück, wenn die App nicht installiert ist, oder ein Array mit einem einzelnen [teamsAppInstallation-Objekt,](/graph/api/resources/teamsappinstallation?view=graph-rest-v1.0&preserve-view=true) falls es installiert wurde.

### <a name="-install-your-app"></a>✔ Installieren Ihrer App

**Microsoft Graph-Seitenreferenz: Installieren** [der App für den Benutzer](/graph/api/userteamwork-post-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

**HTTP POST-Anforderung:**

```http
POST https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps
{
   "teamsApp@odata.bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/{teamsAppId}"
}
```

Wenn der Benutzer Microsoft Teams ausgeführt hat, wird die App möglicherweise sofort installiert. Alternativ kann ein Neustart erforderlich sein, um die installierte App zu sehen.

### <a name="-retrieve-the-conversation-chatid"></a>✔ Abrufen der **Chat-ID** der Unterhaltung

Wenn Ihre App für den Benutzer installiert ist, erhält der Bot eine Ereignisbenachrichtigung, die die erforderlichen Informationen zum Senden der `conversationUpdate` [](../../resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) proaktiven Nachricht enthält.

Der `chatId` kann auch wie folgt abgerufen werden:

**Microsoft Graph-Seitenreferenz: Chat** [erhalten](/graph/api/chat-get?view=graph-rest-beta&tabs=http&preserve-view=true)

**1.** Sie benötigen die . `{teamsAppInstallationId}` Verwenden Sie Folgendes, wenn Sie es nicht haben:

**HTTP GET-Anforderung:**

```http
GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

Die **id-Eigenschaft** der Antwort ist die `teamsAppInstallationId` .

**2. Stellen Sie** die folgende Anforderung, um folgendes zu `chatId` erhalten:

**HTTP -GET-Anforderung** (Berechtigung - `TeamsAppInstallation.ReadWriteSelfForUser.All` ):  

```http
 GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps/{teamsAppInstallationId}/chat
```

Die **id-Eigenschaft** der Antwort ist die `chatId` .

Alternativ können Sie die mit der unten aufgeführten Anforderung abrufen, benötigen `chatId`  jedoch die umfassendere `Chat.Read.All` Berechtigung:

**HTTP -GET-Anforderung** (Berechtigung - `Chat.Read.All` ):

```http
GET https://graph.microsoft.com/beta/users/{user-id}/chats?$filter=installedApps/any(a:a/teamsApp/id eq '{teamsAppId}')
```

### <a name="-send-proactive-messages"></a>✔ Proaktive Nachrichten senden

Nachdem Ihr Bot für einen Benutzer oder ein Team hinzugefügt wurde und die erforderlichen Benutzerinformationen erhalten hat, kann er mit dem Senden proaktiver [Nachrichten beginnen.](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true)

# <a name="c--net"></a>[C# / .NET](#tab/csharp)

Der folgende Codeausschnitt ist aus den [Microsoft Bot #A0 für C# enthalten.](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/16.proactive-messages)

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

Der folgende Codeausschnitt ist aus den [Microsoft Bot -Framework-Beispielen für JavaScript .](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/16.proactive-messages)

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

## <a name="related-topic-for-teams-administrators"></a>Verwandtes Thema für Teams-Administratoren
>
> [!div class="nextstepaction"]
> [**Verwalten von Richtlinien für App-Setup in Teams**](/MicrosoftTeams/teams-app-setup-policies#create-a-custom-app-setup-policy)

## <a name="view-additional-code-samples"></a>Anzeigen zusätzlicher Codebeispiele
>
> [!div class="nextstepaction"]
> [**Proaktive Codebeispiele für Messaging in Teams**](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)
>
