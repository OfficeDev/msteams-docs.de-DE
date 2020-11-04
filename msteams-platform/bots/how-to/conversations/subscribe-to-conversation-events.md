---
title: Abonnieren von Unterhaltungsereignissen
author: WashingtonKayaker
description: Abonnieren von unterhaltungsereignissen von Ihrem Microsoft Teams-bot.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: d6a385d4608239029a943c0a1365cfcb56b21b6b
ms.sourcegitcommit: df9448681d2a81f1029aad5a5e1989cd438d1ae0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2020
ms.locfileid: "48877036"
---
# <a name="subscribe-to-conversation-events"></a>Abonnieren von Unterhaltungsereignissen

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Microsoft Teams sendet Benachrichtigungen an Ihren Bot für Ereignisse, die in Bereichen stattfinden, in denen Ihr Bot aktiv ist. Sie können diese Ereignisse in Ihrem Code erfassen und mit Aktionen darauf reagieren, z. B. wie folgt:

* Auslösen einer Willkommensnachricht, wenn Ihr bot einem Team hinzugefügt wird
* Auslösen einer Willkommensnachricht beim Hinzufügen oder Entfernen eines neuen Teammitglieds
* Auslösen einer Benachrichtigung, wenn ein Kanal erstellt, umbenannt oder gelöscht wird
* Wenn eine bot-Nachricht von einem Benutzer gefällt wird

## <a name="conversation-update-events"></a>Aktualisierungsereignisse in Unterhaltungen

Ein Bot empfängt ein `conversationUpdate`-Ereignis, wenn er zu einer Unterhaltung hinzugefügt wurde, andere Mitglieder zu einer Unterhaltung hinzugefügt oder daraus entfernt wurden oder sich die Metadaten einer Unterhaltung geändert haben.

Das `conversationUpdate`-Ereignis wird an Ihren Bot gesendet, wenn er Informationen zu Mitgliedschaftsaktualisierungen für Teams empfängt, denen er hinzugefügt wurde. Er empfängt außerdem eine Aktualisierung, wenn er zum ersten Mal hinzugefügt wurde, speziell für persönliche Unterhaltungen.

Die folgende Tabelle enthält eine Liste der Teams-Unterhaltungs Update Ereignisse mit Links zu weiteren Details.

| Ausgeführte Aktion        | EventType         | Methode mit dem Namen              | Beschreibung                | Bereich |
| ------------------- | ----------------- | -------------------------- | -------------------------- | ----- |
| erstellter Kanal     | channelCreated    | OnTeamsChannelCreatedAsync | [Es wurde ein Kanal erstellt.](#channel-created) | Team |
| Kanal umbenannt     | channelRenamed    | OnTeamsChannelRenamedAsync | [Ein Kanal wurde umbenannt](#channel-renamed) | Team |
| Kanal gelöscht     | channelDeleted    | OnTeamsChannelDeletedAsync | [Ein Kanal wurde gelöscht.](#channel-deleted) | Team |
| hinzugefügte Teammitglieder   | teamMemberAdded   | OnTeamsMembersAddedAsync   | [Ein Mitglied, das Team hinzugefügt wurde](#team-members-added)   | Alle |
| Teammitglieder entfernt | teamMemberRemoved | OnTeamsMembersRemovedAsync | [Ein Mitglied wurde aus dem Team entfernt.](#team-members-removed) | groupChat & Team |
| Team umbenannt        | teamRenamed       | OnTeamsTeamRenamedAsync    | [Ein Team wurde umbenannt](#team-renamed)       | Team |

### <a name="channel-created"></a>Erstellter Kanal

Das Ereignis "Channel created" wird an Ihren bot gesendet, wenn ein neuer Kanal in einem Team erstellt wird, in dem Ihr bot installiert ist.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelCreatedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the Channel created");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[TypeScript/Node.js](#tab/typescript)

<!-- From sample: botbuilder-js\libraries\botbuilder\tests\teams\conversationUpdate\src\conversationUpdateBot.ts -->

```typescript

export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onTeamsChannelCreatedEvent(async (channelInfo: ChannelInfo, teamInfo: TeamInfo, turnContext: TurnContext, next: () => Promise<void>): Promise<void> => {
            const card = CardFactory.heroCard('Channel Created', `${channelInfo.name} is the Channel created`);
            const message = MessageFactory.attachment(card);
            await turnContext.sendActivity(message);
            await next();
        });
    }
}

```

# <a name="json"></a>[Json](#tab/json)

```json
{
    "type": "conversationUpdate",
    "timestamp": "2017-02-23T19:34:07.478Z",
    "localTimestamp": "2017-02-23T12:34:07.478-07:00",
    "id": "f:dd6ec311",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
    "from": {
        "id": "29:1wR7IdIRIoerMIWbewMi75JA3scaMuxvFon9eRQW2Nix5loMDo0362st2IaRVRirPZBv1WdXT8TIFWWmlQCizZQ"
    },
    "conversation": {
        "isGroup": true,
        "conversationType": "channel",
        "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
    },
    "recipient": {
        "id": "28:f5d48856-5b42-41a0-8c3a-c5f944b679b0",
        "name": "SongsuggesterBot"
    },
    "channelData": {
        "channel": {
            "id": "19:6d97d816470f481dbcda38244b98689a@thread.skype",
            "name": "FunDiscussions"
        },
        "team": {
            "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
        },
        "eventType": "channelCreated",
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    }
}
```

# <a name="python"></a>[Python](#tab/python)

```python
async def on_teams_channel_created(
    self, channel_info: ChannelInfo, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(
            f"The new channel is {channel_info.name}. The channel id is {channel_info.id}"
        )
    )
```

* * *

### <a name="channel-renamed"></a>Kanal umbenannt

Das Ereignis "Kanal umbenannte" wird an Ihren bot gesendet, wenn ein Kanal in einem Team umbenannt wird, in dem Ihr bot installiert ist.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelRenamedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the new Channel name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[TypeScript/Node.js](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onTeamsChannelRenamedEvent(async (channelInfo: ChannelInfo, teamInfo: TeamInfo, turnContext: TurnContext, next: () => Promise<void>): Promise<void> => {
            const card = CardFactory.heroCard('Channel Renamed', `${channelInfo.name} is the new Channel name`);
            const message = MessageFactory.attachment(card);
            await turnContext.sendActivity(message);
            await next();
        });
    }
```

# <a name="json"></a>[Json](#tab/json)

```json
{
    "type": "conversationUpdate",
    "timestamp": "2017-02-23T19:34:07.478Z",
    "localTimestamp": "2017-02-23T12:34:07.478-07:00",
    "id": "f:dd6ec311",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
    "from": {
        "id": "29:1wR7IdIRIoerMIWbewMi75JA3scaMuxvFon9eRQW2Nix5loMDo0362st2IaRVRirPZBv1WdXT8TIFWWmlQCizZQ"
    },
    "conversation": {
        "isGroup": true,
        "conversationType": "channel",
        "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
    },
    "recipient": {
        "id": "28:f5d48856-5b42-41a0-8c3a-c5f944b679b0",
        "name": "SongsuggesterBot"
    },
    "channelData": {
        "channel": {
            "id": "19:6d97d816470f481dbcda38244b98689a@thread.skype",
            "name": "PhotographyUpdates"
        },
        "team": {
            "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
        },
        "eventType": "channelRenamed",
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    }
}
```

# <a name="python"></a>[Python](#tab/python)

```python
async def on_teams_channel_renamed(
    self, channel_info: ChannelInfo, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The new channel name is {channel_info.name}")
    )
```

* * *

### <a name="channel-deleted"></a>Kanal gelöscht

Das Channel Deleted-Ereignis wird an Ihren bot gesendet, wenn ein Kanal in einem Team gelöscht wird, in dem Ihr bot installiert ist.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelDeletedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the Channel deleted");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[TypeScript/Node.js](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onTeamsChannelDeletedEvent(async (channelInfo: ChannelInfo, teamInfo: TeamInfo, turnContext: TurnContext, next: () => Promise<void>): Promise<void> => {
            const card = CardFactory.heroCard('Channel Deleted', `${channelInfo.name} is the Channel deleted`);
            const message = MessageFactory.attachment(card);
            await turnContext.sendActivity(message);
            await next();
        });
    }
}

```

# <a name="json"></a>[Json](#tab/json)

```json
{
    "type": "conversationUpdate",
    "timestamp": "2017-02-23T19:34:07.478Z",
    "localTimestamp": "2017-02-23T12:34:07.478-07:00",
    "id": "f:dd6ec311",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
    "from": {
        "id": "29:1wR7IdIRIoerMIWbewMi75JA3scaMuxvFon9eRQW2Nix5loMDo0362st2IaRVRirPZBv1WdXT8TIFWWmlQCizZQ"
    },
    "conversation": {
        "isGroup": true,
        "conversationType": "channel",
        "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
    },
    "recipient": {
        "id": "28:f5d48856-5b42-41a0-8c3a-c5f944b679b0",
        "name": "SongsuggesterBot"
    },
    "channelData": {
        "channel": {
            "id": "19:6d97d816470f481dbcda38244b98689a@thread.skype",
            "name": "PhotographyUpdates"
        },
        "team": {
            "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
        },
        "eventType": "channelDeleted",
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    }
}
```

# <a name="python"></a>[Python](#tab/python)

```python
async def on_teams_channel_deleted(
    self, channel_info: ChannelInfo, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The deleted channel is {channel_info.name}")
    )
```

* * *

### <a name="team-members-added"></a>Hinzugefügte Team Mitglieder

Das `teamMemberAdded` Ereignis wird an Ihren bot gesendet, wenn es zum ersten Mal zu einer Unterhaltung hinzugefügt wird, und jedes Mal, wenn ein neuer Benutzer einem Team-oder Gruppenchat hinzugefügt wird, in dem der bot installiert ist. Die Benutzerinformationen (ID) sind für Ihren bot eindeutig und können für die zukünftige Verwendung durch ihren Dienst zwischengespeichert werden (beispielsweise das Senden einer Nachricht an einen bestimmten Benutzer).

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task OnTeamsMembersAddedAsync(IList<ChannelAccount> membersAdded, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    foreach (TeamsChannelAccount member in membersAdded)
    {
        if (member.Id == turnContext.Activity.Recipient.Id)
        {
            // Send a message to introduce the bot to the team
            var heroCard = new HeroCard(text: $"The {member.Name} bot has joined {teamInfo.Name}");
            await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
        }
        else
        {
            var heroCard = new HeroCard(text: $"{member.Name} joined {teamInfo.Name}");
            await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
        }
    }
}
```

# <a name="typescriptnodejs"></a>[TypeScript/Node.js](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onTeamsMembersAddedEvent(async (membersAdded: ChannelAccount[], teamInfo: TeamInfo, turnContext: TurnContext, next: () => Promise<void>): Promise<void> => {
                let newMembers: string = '';
                console.log(JSON.stringify(membersAdded));
                membersAdded.forEach((account) => {
                    newMembers += account.id + ' ';
                });
                const name = !teamInfo ? 'not in team' : teamInfo.name;
                const card = CardFactory.heroCard('Account Added', `${newMembers} joined ${name}.`);
                const message = MessageFactory.attachment(card);
                await turnContext.sendActivity(message);
                await next();
        });
    }
}

```

# <a name="json"></a>[Json](#tab/json)

Dies ist die Nachricht, die ihr bot erhalten wird, wenn der bot **einem Team** hinzugefügt wird.

```json
{
    "membersAdded": [
        {
            "id": "28:f5d48856-5b42-41a0-8c3a-c5f944b679b0"
        }
    ],
    "type": "conversationUpdate",
    "timestamp": "2017-02-23T19:38:35.312Z",
    "localTimestamp": "2017-02-23T12:38:35.312-07:00",
    "id": "f:5f85c2ad",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
    "from": {
        "id": "29:1I9Is_Sx0OIy2rQ7Xz1lcaPKlO9eqmBRTBuW6XzkFtcjqxTjPaCMij8BVMdBcL9L_RwWNJyAHFQb0TRzXgyQvA"
    },
    "conversation": {
        "isGroup": true,
        "conversationType": "channel",
        "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
    },
    "recipient": {
        "id": "28:f5d48856-5b42-41a0-8c3a-c5f944b679b0",
        "name": "SongsuggesterBot"
    },
    "channelData": {
        "team": {
            "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
        },
        "eventType": "teamMemberAdded",
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    }
}
```

Dies ist die Nachricht, die ihr bot erhält, wenn der bot * *einem 1:1-Chat* hinzugefügt wird.

```json
{
  "membersAdded": [{
      "id": "28:f5d48856-5b42-41a0-8c3a-c5f944b679b0"
    },
    {
      "id": "29:<userID>",
      "aadObjectId": "***"
    }
  ],
  "type": "conversationUpdate",
  "timestamp": "2019-04-23T10:17:44.349Z",
  "id": "f:5f85c2ad",
  "channelId": "msteams",
  "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
  "from": {
    "id": "29:<USERID>",
    "aadObjectId": "**_"
  },
  "conversation": {
    "conversationType": "personal",
    "id": "_*_"
  },
  "recipient": {
    "id": "28:<BOT ID>",
    "name": "<BOT NAME>"
  },
  "channelData": {
    "tenant": {
      "id": "<TENANT ID>"
    }
  }
}
```

# <a name="python"></a>[Python](#tab/python)

```python
async def on_teams_members_added(
    self, teams_members_added: [TeamsChannelAccount], turn_context: TurnContext
):
    for member in teams_members_added:
        await turn_context.send_activity(
            MessageFactory.text(f"Welcome your new team member {member.id}")
        )
    return
```

_ * *

### <a name="team-members-removed"></a>Team Mitglieder entfernt

Das `teamMemberRemoved` Ereignis wird an Ihren bot gesendet, wenn es aus einem Team entfernt wird und jedes Mal, wenn ein Benutzer aus einem Team entfernt wird, von dem Ihr bot Mitglied ist. Sie können ermitteln, ob das neue Element aus dem bot selbst oder einem Benutzer entfernt wurde, indem Sie sich das `Activity` Objekt von ansehen `turnContext` .  Wenn das `Id` Feld des Objekts mit dem `MembersRemoved` `Id` Feld des Objekts identisch ist `Recipient` , ist das Element entfernt der bot, andernfalls handelt es sich um einen Benutzer.  Der bot `Id` wird im allgemeinen: `28:<MicrosoftAppId>`

[!Note] Wenn ein Benutzer dauerhaft von einem Mandanten gelöscht wird, `membersRemoved conversationUpdate` wird das Ereignis ausgelöst.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task OnTeamsMembersRemovedAsync(IList<ChannelAccount> membersRemoved, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    foreach (TeamsChannelAccount member in membersRemoved)
    {
        if (member.Id == turnContext.Activity.Recipient.Id)
        {
            // The bot was removed
            // You should clear any cached data you have for this team
        }
        else
        {
            var heroCard = new HeroCard(text: $"{member.Name} was removed from {teamInfo.Name}");
            await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
        }
    }
}
```

# <a name="typescriptnodejs"></a>[TypeScript/Node.js](#tab/typescript)

```typescript

export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onTeamsMembersRemovedEvent(async (membersRemoved: ChannelAccount[], teamInfo: TeamInfo, turnContext: TurnContext, next: () => Promise<void>): Promise<void> => {
            let removedMembers: string = '';
            console.log(JSON.stringify(membersRemoved));
            membersRemoved.forEach((account) => {
                removedMembers += account.id + ' ';
            });
            const name = !teamInfo ? 'not in team' : teamInfo.name;
            const card = CardFactory.heroCard('Account Removed', `${removedMembers} removed from ${teamInfo.name}.`);
            const message = MessageFactory.attachment(card);
            await turnContext.sendActivity(message);
            await next();
        });
    }
}

```

# <a name="json"></a>[Json](#tab/json)

```json
{
    "membersRemoved": [
        {
            "id": "29:1_LCi5Up14pAy65yZuaJzG1uIT7ujYhjjSTsUNqjORsZHjLHKiQIBJa4cX2XsAsRoaY7va2w6ZymA9-1VtSY_g"
        }
    ],
    "type": "conversationUpdate",
    "timestamp": "2017-02-23T19:37:06.96Z",
    "localTimestamp": "2017-02-23T12:37:06.96-07:00",
    "id": "f:d8a6a4aa",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
    "from": {
        "id": "29:1I9Is_Sx0OIy2rQ7Xz1lcaPKlO9eqmBRTBuW6XzkFtcjqxTjPaCMij8BVMdBcL9L_RwWNJyAHFQb0TRzXgyQvA"
    },
    "conversation": {
        "isGroup": true,
        "conversationType": "channel",
        "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
    },
    "recipient":
    {
        "id": "28:f5d48856-5b42-41a0-8c3a-c5f944b679b0",
        "name": "SongsuggesterBot"
    },
    "channelData": {
        "team": {
            "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
        },
        "eventType": "teamMemberRemoved",
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    }
}
```


# <a name="python"></a>[Python](#tab/python)

```python
async def on_teams_members_removed(
    self, teams_members_removed: [TeamsChannelAccount], turn_context: TurnContext
):
    for member in teams_members_removed:
        await turn_context.send_activity(
            MessageFactory.text(f"Say goodbye to your team member {member.id}")
        )
    return
```

* * *

### <a name="team-renamed"></a>Team umbenannt

Ihr bot wird benachrichtigt, wenn das Team, in dem es sich befindet, umbenannt wurde. Es empfängt ein `conversationUpdate` Ereignis mit `eventType.teamRenamed` im `channelData` -Objekt.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamRenamedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the new Team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[TypeScript/Node.js](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onTeamsTeamRenamedEvent(async (teamInfo: TeamInfo, turnContext: TurnContext, next: () => Promise<void>): Promise<void> => {
            const card = CardFactory.heroCard('Team Renamed', `${teamInfo.name} is the new Team name`);
            const message = MessageFactory.attachment(card);
            await turnContext.sendActivity(message);
            await next();
        });
    }
}
```

# <a name="json"></a>[Json](#tab/json)

```json
{ 
    "type": "conversationUpdate",
    "timestamp": "2017-02-23T19:35:56.825Z",
    "localTimestamp": "2017-02-23T12:35:56.825-07:00",
    "id": "f:1406033e",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/", 
    "from": { 
        "id": "29:1I9Is_Sx0O-Iy2rQ7Xz1lcaPKlO9eqmBRTBuW6XzkFtcjqxTjPaCMij8BVMdBcL9L_RwWNJyAHFQb0TRzXgyQvA"
    }, 
    "conversation": {
        "isGroup": true,
        "conversationType": "channel",
        "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
    },
    "recipient": { 
        "id": "28:f5d48856-5b42-41a0-8c3a-c5f944b679b0",
        "name": "SongsuggesterLocal"
    },
    "channelData": {
        "team": {
            "id": "19:efa9296d959346209fea44151c742e73@thread.skype",
            "name": "New Team Name"
        },
        "eventType": "teamRenamed",
        "tenant": { 
           "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    }
}
```


# <a name="python"></a>[Python](#tab/python)

```python
async def on_teams_team_renamed(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The new team name is {team_info.name}")
    )
```

* * *

## <a name="message-reaction-events"></a>Nachrichten Reaktions Ereignisse

Das `messageReaction` Ereignis wird gesendet, wenn ein Benutzerreaktionen auf eine Nachricht hinzufügt oder entfernt, die von Ihrem bot gesendet wurde. Der `replyToId` enthält die ID der bestimmten Nachricht, und der `Type` Typ der Reaktion im Text Format.  Zu den Arten von Reaktionen gehören: "wütend", "Herz", "Lachen", "like", "Sad", "überrascht". Dieses Ereignis enthält nicht den Inhalt der ursprünglichen Nachricht, wenn also die Verarbeitung von Reaktionen auf Ihre Nachrichten für Ihren bot wichtig ist, müssen Sie die Nachrichten speichern, wenn Sie Sie senden.

| EventType       | Payload-Objekt   | Beschreibung                                                             | Bereich |
| --------------- | ---------------- | ----------------------------------------------------------------------- | ----- |
| messageReaction | reactionsAdded   | [Reaktion auf bot-Nachricht](#reactions-to-a-bot-message)                   | Alle   |
| messageReaction | reactionsRemoved | [Reaktion aus bot-Nachricht entfernt](#reactions-removed-from-bot-message) | Alle   |

### <a name="reactions-to-a-bot-message"></a>Reaktionen auf eine bot-Nachricht

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task OnReactionsAddedAsync(IList<MessageReaction> messageReactions, ITurnContext<IMessageReactionActivity> turnContext, CancellationToken cancellationToken)
{
    foreach (var reaction in messageReactions)
    {
      var newReaction = $"You reacted with '{reaction.Type}' to the following message: '{turnContext.Activity.ReplyToId}'";
      var replyActivity = MessageFactory.Text(newReaction);
      var resourceResponse = await turnContext.SendActivityAsync(replyActivity, cancellationToken);
    }
}
```

# <a name="typescriptnodejs"></a>[TypeScript/Node.js](#tab/typescript)

<!-- Verify -->

```typescript

export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onReactionsAdded(async (context, next) => {
           const reactionsAdded = context.activity.reactionsAdded;
            if (reactionsAdded && reactionsAdded.length > 0) {
                for (let i = 0; i < reactionsAdded.length; i++) {
                    const reaction = reactionsAdded[i];
                    const newReaction = `You reacted with '${reaction.type}' to the following message: '${context.activity.replyToId}'`;
                    const resourceResponse = context.sendActivity(newReaction);
                    // Save information about the sent message and its ID (resourceResponse.id).
                }
            }
        });
    }
}

```

# <a name="json"></a>[Json](#tab/json)

```json
{
    "reactionsAdded": [
        {
            "type": "like"
        }
    ],
    "type": "messageReaction",
    "timestamp": "2017-10-16T18:45:41.943Z",
    "id": "f:9f78d1f3",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
    "from": {
        "id": "29:1I9Is_Sx0O-Iy2rQ7Xz1lcaPKlO9eqmBRTBuW6XzkFtcjqxTjPaCMij8BVMdBcL9L_RwWNJyAHFQb0TRzXgyQvA",
        "aadObjectId": "c33aafc4-646d-4543-9d4c-abd28e4d2110"
    },
    "conversation": {
        "isGroup": true,
        "conversationType": "channel",
        "id": "19:3629591d4b774aa08cb0887902eee7c1@thread.skype"
    },
    "recipient": {
        "id": "28:f5d48856-5b42-41a0-8c3a-c5f944b679b0",
        "name": "SongsuggesterLocal"
    },
    "channelData": {
        "channel": {
            "id": "19:3629591d4b774aa08cb0887902eee7c1@thread.skype"
        },
        "team": {
            "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
        },
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    },
    "replyToId": "1575667808184",
    "legacy": {
      "replyToId": "1:19uJ8TZA1cZcms7-2HLOW3pWRF4nSWEoVnRqc0DPa_kY"
    }
}
```

# <a name="python"></a>[Python](#tab/python)

```python
async def on_reactions_added(
    self, message_reactions: List[MessageReaction], turn_context: TurnContext
):
    for reaction in message_reactions:
        activity = await self._log.find(turn_context.activity.reply_to_id)
        if not activity:
            await self._send_message_and_log_activity_id(
                turn_context,
                f"Activity {turn_context.activity.reply_to_id} not found in log",
            )
        else:
            await self._send_message_and_log_activity_id(
                turn_context,
                f"You added '{reaction.type}' regarding '{activity.text}'",
            )
    return
```

* * *

### <a name="reactions-removed-from-bot-message"></a>Aus der bot-Nachricht entfernte Reaktionen

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task OnReactionsRemovedAsync(IList<MessageReaction> messageReactions, ITurnContext<IMessageReactionActivity> turnContext, CancellationToken cancellationToken)
{
    foreach (var reaction in messageReactions)
    {
      var newReaction = $"You removed the reaction '{reaction.Type}' from the following message: '{turnContext.Activity.ReplyToId}'";
      var replyActivity = MessageFactory.Text(newReaction);
      var resourceResponse = await turnContext.SendActivityAsync(replyActivity, cancellationToken);
    }
}
```

# <a name="typescriptnodejs"></a>[TypeScript/Node.js](#tab/typescript)

<!-- Verify -->

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onReactionsRemoved(async(context,next)=>{
            const reactionsRemoved = context.activity.reactionsRemoved;
            if (reactionsRemoved && reactionsRemoved.length > 0) {
                for (let i = 0; i < reactionsRemoved.length; i++) {
                    const reaction = reactionsRemoved[i];
                    const newReaction = `You removed the reaction '${reaction.type}' from the message: '${context.activity.replyToId}'`;
                    const resourceResponse = context.sendActivity(newReaction);
                    // Save information about the sent message and its ID (resourceResponse.id).
                }
            }
        });
    }
}
```

# <a name="json"></a>[Json](#tab/json)

```json
{
    "reactionsRemoved": [
        {
            "type": "like"
        }
    ],
    "type": "messageReaction",
    "timestamp": "2017-10-16T18:45:41.943Z",
    "id": "f:9f78d1f3",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
    "from": {
        "id": "29:1I9Is_Sx0O-Iy2rQ7Xz1lcaPKlO9eqmBRTBuW6XzkFtcjqxTjPaCMij8BVMdBcL9L_RwWNJyAHFQb0TRzXgyQvA",
        "aadObjectId": "c33aafc4-646d-4543-9d4c-abd28e4d2110"
    },
    "conversation": {
        "isGroup": true,
        "conversationType": "channel",
        "id": "19:3629591d4b774aa08cb0887902eee7c1@thread.skype"
    },
    "recipient": {
        "id": "28:f5d48856-5b42-41a0-8c3a-c5f944b679b0",
        "name": "SongsuggesterLocal"
    },
    "channelData": {
        "channel": {
            "id": "19:3629591d4b774aa08cb0887902eee7c1@thread.skype"
        },
        "team": {
            "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
        },
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    },
    "replyToId": "1575667808184",
    "legacy": {
      "replyToId": "1:19uJ8TZA1cZcms7-2HLOW3pWRF4nSWEoVnRqc0DPa_kY"
    }
}
```

# <a name="python"></a>[Python](#tab/python)

```python
async def on_reactions_removed(
    self, message_reactions: List[MessageReaction], turn_context: TurnContext
):
    for reaction in message_reactions:
        activity = await self._log.find(turn_context.activity.reply_to_id)
        if not activity:
            await self._send_message_and_log_activity_id(
                turn_context,
                f"Activity {turn_context.activity.reply_to_id} not found in log",
            )
        else:
            await self._send_message_and_log_activity_id(
                turn_context,
                f"You removed '{reaction.type}' regarding '{activity.text}'",
            )
    return
```

* * *
