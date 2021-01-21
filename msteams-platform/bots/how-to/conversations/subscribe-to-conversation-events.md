---
title: Abonnieren von Unterhaltungsereignissen
author: WashingtonKayaker
description: Abonnieren von Unterhaltungsereignissen von Ihrem Microsoft Teams-Bot.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 17d13d51ab26aba60defb962dd425c1aed5b4133
ms.sourcegitcommit: 00c657e3bf57d3b92aca7da941cde47a2eeff4d0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "49911961"
---
# <a name="subscribe-to-conversation-events"></a><span data-ttu-id="d3ada-103">Abonnieren von Unterhaltungsereignissen</span><span class="sxs-lookup"><span data-stu-id="d3ada-103">Subscribe to conversation events</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="d3ada-104">Microsoft Teams sendet Benachrichtigungen an Ihren Bot für Ereignisse, die in Bereichen stattfinden, in denen Ihr Bot aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="d3ada-104">Microsoft Teams sends notifications to your bot for events that happen in scopes where your bot is active.</span></span> <span data-ttu-id="d3ada-105">Sie können diese Ereignisse in Ihrem Code erfassen und mit Aktionen darauf reagieren, z. B. wie folgt:</span><span class="sxs-lookup"><span data-stu-id="d3ada-105">You can capture these events in your code and take action on them, such as the following:</span></span>

* <span data-ttu-id="d3ada-106">Auslösen einer Willkommensnachricht, wenn Ihr Bot zu einem Team hinzugefügt wird</span><span class="sxs-lookup"><span data-stu-id="d3ada-106">Trigger a welcome message when your bot is added to a team</span></span>
* <span data-ttu-id="d3ada-107">Auslösen einer Willkommensnachricht, wenn ein neues Teammitglied hinzugefügt oder entfernt wird</span><span class="sxs-lookup"><span data-stu-id="d3ada-107">Trigger a welcome message when a new team member is added or removed</span></span>
* <span data-ttu-id="d3ada-108">Auslösen einer Benachrichtigung, wenn ein Kanal erstellt, umbenannt oder gelöscht wird</span><span class="sxs-lookup"><span data-stu-id="d3ada-108">Trigger a notification when a channel is created, renamed or deleted</span></span>
* <span data-ttu-id="d3ada-109">Wenn eine Botnachricht von einem Benutzer mit "Gefällt mir" gefällt</span><span class="sxs-lookup"><span data-stu-id="d3ada-109">When a bot message is liked by a user</span></span>

## <a name="conversation-update-events"></a><span data-ttu-id="d3ada-110">Aktualisierungsereignisse in Unterhaltungen</span><span class="sxs-lookup"><span data-stu-id="d3ada-110">Conversation update events</span></span>

> [!Important]
> <span data-ttu-id="d3ada-111">Neue Ereignisse können jederzeit hinzugefügt werden, und Ihr Bot beginnt, sie zu empfangen.</span><span class="sxs-lookup"><span data-stu-id="d3ada-111">New events can be added at any time, and your bot will begin to receive them.</span></span>
> <span data-ttu-id="d3ada-112">Sie müssen die Möglichkeit, unerwartete Ereignisse zu empfangen, entwerfen.</span><span class="sxs-lookup"><span data-stu-id="d3ada-112">You must design for the possibility of receiving unexpected events.</span></span>
> <span data-ttu-id="d3ada-113">Wenn Sie das Bot Framework SDK verwenden, antwortet Ihr Bot automatisch mit einem auf Ereignisse, die Sie `200 - OK` nicht behandeln möchten.</span><span class="sxs-lookup"><span data-stu-id="d3ada-113">If you are using the Bot Framework SDK, your bot will automatically respond with a `200 - OK` to any events you do not choose to handle.</span></span>

<span data-ttu-id="d3ada-114">Ein Bot empfängt ein `conversationUpdate`-Ereignis, wenn er zu einer Unterhaltung hinzugefügt wurde, andere Mitglieder zu einer Unterhaltung hinzugefügt oder daraus entfernt wurden oder sich die Metadaten einer Unterhaltung geändert haben.</span><span class="sxs-lookup"><span data-stu-id="d3ada-114">A bot receives a `conversationUpdate` event when it has been added to a conversation, other members have been added to or removed from a conversation, or conversation metadata has changed.</span></span>

<span data-ttu-id="d3ada-115">Das `conversationUpdate`-Ereignis wird an Ihren Bot gesendet, wenn er Informationen zu Mitgliedschaftsaktualisierungen für Teams empfängt, denen er hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="d3ada-115">The `conversationUpdate` event is sent to your bot when it receives information on membership updates for teams where it has been added.</span></span> <span data-ttu-id="d3ada-116">Er empfängt außerdem eine Aktualisierung, wenn er zum ersten Mal hinzugefügt wurde, speziell für persönliche Unterhaltungen.</span><span class="sxs-lookup"><span data-stu-id="d3ada-116">It also receives an update when it has been added for the first time specifically for personal conversations.</span></span>

<span data-ttu-id="d3ada-117">Die folgende Tabelle enthält eine Liste der Aktualisierungsereignisse für Teams-Unterhaltungen mit Links zu weiteren Details.</span><span class="sxs-lookup"><span data-stu-id="d3ada-117">The following table shows a list of Teams conversation update events, with links to more details.</span></span>

| <span data-ttu-id="d3ada-118">Ergriffene Aktion</span><span class="sxs-lookup"><span data-stu-id="d3ada-118">Action Taken</span></span>        | <span data-ttu-id="d3ada-119">EventType</span><span class="sxs-lookup"><span data-stu-id="d3ada-119">EventType</span></span>         | <span data-ttu-id="d3ada-120">Aufgerufene Methode</span><span class="sxs-lookup"><span data-stu-id="d3ada-120">Method Called</span></span>              | <span data-ttu-id="d3ada-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d3ada-121">Description</span></span>                | <span data-ttu-id="d3ada-122">Bereich</span><span class="sxs-lookup"><span data-stu-id="d3ada-122">Scope</span></span> |
| ------------------- | ----------------- | -------------------------- | -------------------------- | ----- |
| <span data-ttu-id="d3ada-123">Kanal erstellt</span><span class="sxs-lookup"><span data-stu-id="d3ada-123">channel created</span></span>     | <span data-ttu-id="d3ada-124">channelCreated</span><span class="sxs-lookup"><span data-stu-id="d3ada-124">channelCreated</span></span>    | <span data-ttu-id="d3ada-125">OnTeamsChannelCreatedAsync</span><span class="sxs-lookup"><span data-stu-id="d3ada-125">OnTeamsChannelCreatedAsync</span></span> | [<span data-ttu-id="d3ada-126">Ein Kanal wurde erstellt</span><span class="sxs-lookup"><span data-stu-id="d3ada-126">A channel was created</span></span>](#channel-created) | <span data-ttu-id="d3ada-127">Team</span><span class="sxs-lookup"><span data-stu-id="d3ada-127">Team</span></span> |
| <span data-ttu-id="d3ada-128">Kanal umbenannt</span><span class="sxs-lookup"><span data-stu-id="d3ada-128">channel renamed</span></span>     | <span data-ttu-id="d3ada-129">channelRenamed</span><span class="sxs-lookup"><span data-stu-id="d3ada-129">channelRenamed</span></span>    | <span data-ttu-id="d3ada-130">OnTeamsChannelRenamedAsync</span><span class="sxs-lookup"><span data-stu-id="d3ada-130">OnTeamsChannelRenamedAsync</span></span> | [<span data-ttu-id="d3ada-131">Ein Kanal wurde umbenannt</span><span class="sxs-lookup"><span data-stu-id="d3ada-131">A channel was renamed</span></span>](#channel-renamed) | <span data-ttu-id="d3ada-132">Team</span><span class="sxs-lookup"><span data-stu-id="d3ada-132">Team</span></span> |
| <span data-ttu-id="d3ada-133">Kanal gelöscht</span><span class="sxs-lookup"><span data-stu-id="d3ada-133">channel deleted</span></span>     | <span data-ttu-id="d3ada-134">channelDeleted</span><span class="sxs-lookup"><span data-stu-id="d3ada-134">channelDeleted</span></span>    | <span data-ttu-id="d3ada-135">OnTeamsChannelDeletedAsync</span><span class="sxs-lookup"><span data-stu-id="d3ada-135">OnTeamsChannelDeletedAsync</span></span> | [<span data-ttu-id="d3ada-136">Ein Kanal wurde gelöscht</span><span class="sxs-lookup"><span data-stu-id="d3ada-136">A channel was deleted</span></span>](#channel-deleted) | <span data-ttu-id="d3ada-137">Team</span><span class="sxs-lookup"><span data-stu-id="d3ada-137">Team</span></span> |
| <span data-ttu-id="d3ada-138">Kanal wiederhergestellt</span><span class="sxs-lookup"><span data-stu-id="d3ada-138">channel restored</span></span>    | <span data-ttu-id="d3ada-139">channelRestored</span><span class="sxs-lookup"><span data-stu-id="d3ada-139">channelRestored</span></span>    | <span data-ttu-id="d3ada-140">OnTeamsChannelRestoredAsync</span><span class="sxs-lookup"><span data-stu-id="d3ada-140">OnTeamsChannelRestoredAsync</span></span> | [<span data-ttu-id="d3ada-141">Ein Kanal wurde wiederhergestellt</span><span class="sxs-lookup"><span data-stu-id="d3ada-141">A channel was restored</span></span>](#channel-deleted) | <span data-ttu-id="d3ada-142">Team</span><span class="sxs-lookup"><span data-stu-id="d3ada-142">Team</span></span> |
| <span data-ttu-id="d3ada-143">Hinzugefügte Mitglieder</span><span class="sxs-lookup"><span data-stu-id="d3ada-143">members added</span></span>   | <span data-ttu-id="d3ada-144">membersAdded</span><span class="sxs-lookup"><span data-stu-id="d3ada-144">membersAdded</span></span>   | <span data-ttu-id="d3ada-145">OnTeamsMembersAddedAsync</span><span class="sxs-lookup"><span data-stu-id="d3ada-145">OnTeamsMembersAddedAsync</span></span>   | [<span data-ttu-id="d3ada-146">Ein hinzugefügtes Mitglied</span><span class="sxs-lookup"><span data-stu-id="d3ada-146">A member added</span></span>](#team-members-added)   | <span data-ttu-id="d3ada-147">Alle</span><span class="sxs-lookup"><span data-stu-id="d3ada-147">All</span></span> |
| <span data-ttu-id="d3ada-148">entfernte Mitglieder</span><span class="sxs-lookup"><span data-stu-id="d3ada-148">members removed</span></span> | <span data-ttu-id="d3ada-149">membersRemoved</span><span class="sxs-lookup"><span data-stu-id="d3ada-149">membersRemoved</span></span> | <span data-ttu-id="d3ada-150">OnTeamsMembersRemovedAsync</span><span class="sxs-lookup"><span data-stu-id="d3ada-150">OnTeamsMembersRemovedAsync</span></span> | [<span data-ttu-id="d3ada-151">Ein Mitglied wurde entfernt</span><span class="sxs-lookup"><span data-stu-id="d3ada-151">A member was removed</span></span>](#team-members-removed) | <span data-ttu-id="d3ada-152">groupChat & Team</span><span class="sxs-lookup"><span data-stu-id="d3ada-152">groupChat & team</span></span> |
| <span data-ttu-id="d3ada-153">Team umbenannt</span><span class="sxs-lookup"><span data-stu-id="d3ada-153">team renamed</span></span>        | <span data-ttu-id="d3ada-154">teamRenamed</span><span class="sxs-lookup"><span data-stu-id="d3ada-154">teamRenamed</span></span>       | <span data-ttu-id="d3ada-155">OnTeamsTeamRenamedAsync</span><span class="sxs-lookup"><span data-stu-id="d3ada-155">OnTeamsTeamRenamedAsync</span></span>    | [<span data-ttu-id="d3ada-156">Ein Team wurde umbenannt</span><span class="sxs-lookup"><span data-stu-id="d3ada-156">A Team was renamed</span></span>](#team-renamed)       | <span data-ttu-id="d3ada-157">Team</span><span class="sxs-lookup"><span data-stu-id="d3ada-157">Team</span></span> |
| <span data-ttu-id="d3ada-158">Team archiviert</span><span class="sxs-lookup"><span data-stu-id="d3ada-158">team archived</span></span>        | <span data-ttu-id="d3ada-159">teamArchived</span><span class="sxs-lookup"><span data-stu-id="d3ada-159">teamArchived</span></span>       | <span data-ttu-id="d3ada-160">OnTeamsTeamArchivedAsync</span><span class="sxs-lookup"><span data-stu-id="d3ada-160">OnTeamsTeamArchivedAsync</span></span>    | [<span data-ttu-id="d3ada-161">Ein Team wurde archiviert</span><span class="sxs-lookup"><span data-stu-id="d3ada-161">A Team was archived</span></span>](#team-archived)       | <span data-ttu-id="d3ada-162">Team</span><span class="sxs-lookup"><span data-stu-id="d3ada-162">Team</span></span> |
| <span data-ttu-id="d3ada-163">Team wiederhergestellt</span><span class="sxs-lookup"><span data-stu-id="d3ada-163">team restored</span></span>        | <span data-ttu-id="d3ada-164">teamRestored</span><span class="sxs-lookup"><span data-stu-id="d3ada-164">teamRestored</span></span>      | <span data-ttu-id="d3ada-165">OnTeamsTeamRestoredAsync</span><span class="sxs-lookup"><span data-stu-id="d3ada-165">OnTeamsTeamRestoredAsync</span></span>    | [<span data-ttu-id="d3ada-166">Ein Team wurde umbenannt</span><span class="sxs-lookup"><span data-stu-id="d3ada-166">A Team was renamed</span></span>](#team-renamed)       | <span data-ttu-id="d3ada-167">Team</span><span class="sxs-lookup"><span data-stu-id="d3ada-167">Team</span></span> |

### <a name="channel-created"></a><span data-ttu-id="d3ada-168">Erstellter Kanal</span><span class="sxs-lookup"><span data-stu-id="d3ada-168">Channel created</span></span>

<span data-ttu-id="d3ada-169">Das vom Kanal erstellte Ereignis wird an Ihren Bot gesendet, wenn ein neuer Kanal in einem Team erstellt wird, in dem Ihr Bot installiert ist.</span><span class="sxs-lookup"><span data-stu-id="d3ada-169">The channel created event is sent to your bot whenever a new channel is created in a team your bot is installed in.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="d3ada-170">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="d3ada-170">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelCreatedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the Channel created");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="d3ada-171">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="d3ada-171">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="d3ada-172">Json</span><span class="sxs-lookup"><span data-stu-id="d3ada-172">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="d3ada-173">Python</span><span class="sxs-lookup"><span data-stu-id="d3ada-173">Python</span></span>](#tab/python)

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

### <a name="channel-renamed"></a><span data-ttu-id="d3ada-174">Kanal umbenannt</span><span class="sxs-lookup"><span data-stu-id="d3ada-174">Channel renamed</span></span>

<span data-ttu-id="d3ada-175">Das kanalbenannte Ereignis wird an Ihren Bot gesendet, wenn ein Kanal in einem Team umbenannt wird, in dem Ihr Bot installiert ist.</span><span class="sxs-lookup"><span data-stu-id="d3ada-175">The channel renamed event is sent to your bot whenever a channel is renamed in a team your bot is installed in.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="d3ada-176">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="d3ada-176">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelRenamedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the new Channel name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="d3ada-177">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="d3ada-177">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="d3ada-178">Json</span><span class="sxs-lookup"><span data-stu-id="d3ada-178">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="d3ada-179">Python</span><span class="sxs-lookup"><span data-stu-id="d3ada-179">Python</span></span>](#tab/python)

```python
async def on_teams_channel_renamed(
    self, channel_info: ChannelInfo, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The new channel name is {channel_info.name}")
    )
```

* * *

### <a name="channel-deleted"></a><span data-ttu-id="d3ada-180">Kanal gelöscht</span><span class="sxs-lookup"><span data-stu-id="d3ada-180">Channel Deleted</span></span>

<span data-ttu-id="d3ada-181">Das Ereignis "Kanal gelöscht" wird an Ihren Bot gesendet, wenn ein Kanal in einem Team gelöscht wird, in dem Ihr Bot installiert ist.</span><span class="sxs-lookup"><span data-stu-id="d3ada-181">The channel deleted event is sent to your bot whenever a channel is deleted in a team your bot is installed in.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="d3ada-182">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="d3ada-182">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelDeletedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the Channel deleted");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="d3ada-183">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="d3ada-183">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="d3ada-184">Json</span><span class="sxs-lookup"><span data-stu-id="d3ada-184">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="d3ada-185">Python</span><span class="sxs-lookup"><span data-stu-id="d3ada-185">Python</span></span>](#tab/python)

```python
async def on_teams_channel_deleted(
    self, channel_info: ChannelInfo, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The deleted channel is {channel_info.name}")
    )
```

* * *

### <a name="channel-restored"></a><span data-ttu-id="d3ada-186">Kanal wiederhergestellt</span><span class="sxs-lookup"><span data-stu-id="d3ada-186">Channel restored</span></span>

<span data-ttu-id="d3ada-187">Das Kanal-wiederhergestellte Ereignis wird an Ihren Bot gesendet, wenn ein Kanal, der zuvor gelöscht wurde, in einem Team wiederhergestellt wird, in dem Ihr Bot bereits installiert ist.</span><span class="sxs-lookup"><span data-stu-id="d3ada-187">The channel restored event is sent to your bot whenever a channel that was previously deleted is restored in a team that your bot is already installed in.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="d3ada-188">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="d3ada-188">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelRestoredAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the Channel restored.");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="d3ada-189">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="d3ada-189">TypeScript/Node.js</span></span>](#tab/typescript)

<!-- From sample: botbuilder-js\libraries\botbuilder\tests\teams\conversationUpdate\src\conversationUpdateBot.ts -->

```typescript

export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onTeamsChannelRestoredEvent(async (channelInfo: ChannelInfo, teamInfo: TeamInfo, turnContext: TurnContext, next: () => Promise<void>): Promise<void> => {
            const card = CardFactory.heroCard('Channel Restored', `${channelInfo.name} is the Channel restored`);
            const message = MessageFactory.attachment(card);
            await turnContext.sendActivity(message);
            await next();
        });
    }
}

```

# <a name="json"></a>[<span data-ttu-id="d3ada-190">Json</span><span class="sxs-lookup"><span data-stu-id="d3ada-190">JSON</span></span>](#tab/json)

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
        "eventType": "channelRestored",
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    }
}
```

# <a name="python"></a>[<span data-ttu-id="d3ada-191">Python</span><span class="sxs-lookup"><span data-stu-id="d3ada-191">Python</span></span>](#tab/python)

```python
async def on_teams_channel_restored(
    self, channel_info: ChannelInfo, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(
            f"The restored channel is {channel_info.name}. The channel id is {channel_info.id}"
        )
    )
```

* * *

### <a name="team-members-added"></a><span data-ttu-id="d3ada-192">Hinzugefügte Teammitglieder</span><span class="sxs-lookup"><span data-stu-id="d3ada-192">Team members added</span></span>

<span data-ttu-id="d3ada-193">Das Ereignis wird an Ihren Bot gesendet, wenn es zum ersten Mal zu einer Unterhaltung hinzugefügt wird und jedes Mal, wenn ein neuer Benutzer zu einem Team- oder Gruppenchat hinzugefügt wird, in dem Ihr Bot `teamMemberAdded` installiert ist.</span><span class="sxs-lookup"><span data-stu-id="d3ada-193">The `teamMemberAdded` event is sent to your bot the first time it is added to a conversation and every time a new user is added to a team or group chat that your bot is installed in.</span></span> <span data-ttu-id="d3ada-194">Die Benutzerinformationen (ID) sind für Ihren Bot eindeutig und können für die zukünftige Verwendung durch Ihren Dienst zwischengespeichert werden (z. B. senden einer Nachricht an einen bestimmten Benutzer).</span><span class="sxs-lookup"><span data-stu-id="d3ada-194">The user information (ID) is unique for your bot and can be cached for future use by your service (such as sending a message to a specific user).</span></span>

# <a name="cnet"></a>[<span data-ttu-id="d3ada-195">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="d3ada-195">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsMembersAddedAsync(IList<TeamsChannelAccount> teamsMembersAdded , TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    foreach (TeamsChannelAccount member in teamsMembersAdded)
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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="d3ada-196">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="d3ada-196">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="d3ada-197">Json</span><span class="sxs-lookup"><span data-stu-id="d3ada-197">JSON</span></span>](#tab/json)

<span data-ttu-id="d3ada-198">Dies ist die Nachricht, die Ihr Bot erhält, wenn der Bot **zu einem Team hinzugefügt wird.**</span><span class="sxs-lookup"><span data-stu-id="d3ada-198">This is the message your bot will receive when the bot is added **to a team**.</span></span>

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

<span data-ttu-id="d3ada-199">Dies ist die Nachricht, die Ihr Bot erhält, wenn der Bot zu einem *1:1-Chat hinzugefügt wird.*</span><span class="sxs-lookup"><span data-stu-id="d3ada-199">This is the message your bot will receive when the bot is added \**to a one-to-one chat*.</span></span>

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

# <a name="python"></a>[<span data-ttu-id="d3ada-200">Python</span><span class="sxs-lookup"><span data-stu-id="d3ada-200">Python</span></span>](#tab/python)

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

<span data-ttu-id="d3ada-201">_ \* \*</span><span class="sxs-lookup"><span data-stu-id="d3ada-201">_ \* \*</span></span>

### <a name="team-members-removed"></a><span data-ttu-id="d3ada-202">Entfernte Teammitglieder</span><span class="sxs-lookup"><span data-stu-id="d3ada-202">Team members removed</span></span>

<span data-ttu-id="d3ada-203">Das Ereignis wird an Ihren Bot gesendet, wenn es aus einem Team entfernt wird und jedes Mal, wenn ein Benutzer aus einem Team entfernt wird, in dem Ihr Bot `teamMemberRemoved` Mitglied ist.</span><span class="sxs-lookup"><span data-stu-id="d3ada-203">The `teamMemberRemoved` event is sent to your bot if it is removed from a team and every time any user is removed from a team that your bot is a member of.</span></span> <span data-ttu-id="d3ada-204">Sie können feststellen, ob das neue Element der Bot selbst oder ein Benutzer war, indem Sie sich das `Activity` Objekt des . `turnContext`</span><span class="sxs-lookup"><span data-stu-id="d3ada-204">You can determine if the new member removed was the bot itself or a user by looking at the `Activity` object of the `turnContext`.</span></span>  <span data-ttu-id="d3ada-205">Wenn das Feld des Objekts mit dem Feld des Objekts identisch ist, ist das entfernte Element der Bot, andernfalls handelt es sich `Id` `MembersRemoved` um einen `Id` `Recipient` Benutzer.</span><span class="sxs-lookup"><span data-stu-id="d3ada-205">If the `Id` field of the `MembersRemoved` object is the same as the `Id` field of the `Recipient` object, then the member removed is the bot, otherwise, it is a user.</span></span>  <span data-ttu-id="d3ada-206">Die Bots `Id` sind im Allgemeinen: `28:<MicrosoftAppId>`</span><span class="sxs-lookup"><span data-stu-id="d3ada-206">The bot's `Id` will generally be: `28:<MicrosoftAppId>`</span></span>

[!Note] <span data-ttu-id="d3ada-207">Wenn ein Benutzer dauerhaft aus einem Mandanten gelöscht wird, `membersRemoved conversationUpdate` wird das Ereignis ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="d3ada-207">When a user is permanently deleted from a tenant, `membersRemoved conversationUpdate` event is triggered.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="d3ada-208">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="d3ada-208">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="d3ada-209">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="d3ada-209">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="d3ada-210">Json</span><span class="sxs-lookup"><span data-stu-id="d3ada-210">JSON</span></span>](#tab/json)

<span data-ttu-id="d3ada-211">Das Objekt im folgenden Nutzlastbeispiel basiert auf dem Hinzufügen eines Mitglieds zu einem Team anstelle eines Gruppenchats oder dem Initiieren einer neuen `channelData` 1:1-Unterhaltung:</span><span class="sxs-lookup"><span data-stu-id="d3ada-211">The `channelData` object in the following payload example is based on adding a member to a team rather than a group chat, or initiating a new one-to-one conversation:</span></span>

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


# <a name="python"></a>[<span data-ttu-id="d3ada-212">Python</span><span class="sxs-lookup"><span data-stu-id="d3ada-212">Python</span></span>](#tab/python)

```python
async def on_teams_members_removed(
    self, teams_members_removed: [TeamsChannelAccount], turn_context: TurnContext
):
    for member in teams_members_removed:
        await turn_context.send_activity(
            MessageFactory.text(f"Say goodbye to {member.id}")
        )
    return
```

* * *

### <a name="team-renamed"></a><span data-ttu-id="d3ada-213">Team umbenannt</span><span class="sxs-lookup"><span data-stu-id="d3ada-213">Team renamed</span></span>

<span data-ttu-id="d3ada-214">Ihr Bot wird benachrichtigt, wenn das Team, in dem er sich befindet, umbenannt wurde.</span><span class="sxs-lookup"><span data-stu-id="d3ada-214">Your bot is notified when the team it is in has been renamed.</span></span> <span data-ttu-id="d3ada-215">Es empfängt ein `conversationUpdate` Ereignis mit `eventType.teamRenamed` dem `channelData` Objekt.</span><span class="sxs-lookup"><span data-stu-id="d3ada-215">It receives a `conversationUpdate` event with `eventType.teamRenamed` in the `channelData` object.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="d3ada-216">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="d3ada-216">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamRenamedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the new Team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="d3ada-217">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="d3ada-217">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="d3ada-218">Json</span><span class="sxs-lookup"><span data-stu-id="d3ada-218">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="d3ada-219">Python</span><span class="sxs-lookup"><span data-stu-id="d3ada-219">Python</span></span>](#tab/python)

```python
async def on_teams_team_renamed(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The new team name is {team_info.name}")
    )
```

* * *

### <a name="team-archived"></a><span data-ttu-id="d3ada-220">Team archiviert</span><span class="sxs-lookup"><span data-stu-id="d3ada-220">Team archived</span></span>

<span data-ttu-id="d3ada-221">Der Bot erhält eine Benachrichtigung, wenn das Team archiviert wird, in dem er installiert ist.</span><span class="sxs-lookup"><span data-stu-id="d3ada-221">The bot receives a notification when the team it is installed in is archived.</span></span> <span data-ttu-id="d3ada-222">Es empfängt ein `conversationUpdate` Ereignis mit `eventType.teamarchived` dem `channelData` Objekt.</span><span class="sxs-lookup"><span data-stu-id="d3ada-222">It receives a `conversationUpdate` event with `eventType.teamarchived` in the `channelData` object.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="d3ada-223">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="d3ada-223">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamArchivedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="d3ada-224">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="d3ada-224">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onTeamsTeamArchivedEvent(async (teamInfo: TeamInfo, turnContext: TurnContext, next: () => Promise<void>): Promise<void> => {
            const card = CardFactory.heroCard('Team archived', `${teamInfo.name} is the team name`);
            const message = MessageFactory.attachment(card);
            await turnContext.sendActivity(message);
            await next();
        });
    }
}
```

# <a name="json"></a>[<span data-ttu-id="d3ada-225">Json</span><span class="sxs-lookup"><span data-stu-id="d3ada-225">JSON</span></span>](#tab/json)

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
            "name": "Team Name"
        },
        "eventType": "teamArchived",
        "tenant": { 
           "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    }
}
```

# <a name="python"></a>[<span data-ttu-id="d3ada-226">Python</span><span class="sxs-lookup"><span data-stu-id="d3ada-226">Python</span></span>](#tab/python)

```python
async def on_teams_team_archived(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The team name is {team_info.name}")
    )
```

* * *

### <a name="team-restored"></a><span data-ttu-id="d3ada-227">Team wiederhergestellt</span><span class="sxs-lookup"><span data-stu-id="d3ada-227">Team restored</span></span>

<span data-ttu-id="d3ada-228">Der Bot erhält eine Benachrichtigung, wenn das Team, in dem er installiert ist, wiederhergestellt wird.</span><span class="sxs-lookup"><span data-stu-id="d3ada-228">The bot receives a notification when the team it is installed in is restored.</span></span> <span data-ttu-id="d3ada-229">Es empfängt ein `conversationUpdate` Ereignis mit `eventType.teamrestored` dem `channelData` Objekt.</span><span class="sxs-lookup"><span data-stu-id="d3ada-229">It receives a `conversationUpdate` event with `eventType.teamrestored` in the `channelData` object.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="d3ada-230">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="d3ada-230">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamrestoredAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="d3ada-231">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="d3ada-231">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onTeamsTeamrestoredEvent(async (teamInfo: TeamInfo, turnContext: TurnContext, next: () => Promise<void>): Promise<void> => {
            const card = CardFactory.heroCard('Team restored', `${teamInfo.name} is the team name`);
            const message = MessageFactory.attachment(card);
            await turnContext.sendActivity(message);
            await next();
        });
    }
}
```

# <a name="json"></a>[<span data-ttu-id="d3ada-232">Json</span><span class="sxs-lookup"><span data-stu-id="d3ada-232">JSON</span></span>](#tab/json)

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
            "name": "Team Name"
        },
        "eventType": "teamrestored",
        "tenant": { 
           "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    }
}
```

# <a name="python"></a>[<span data-ttu-id="d3ada-233">Python</span><span class="sxs-lookup"><span data-stu-id="d3ada-233">Python</span></span>](#tab/python)

```python
async def on_teams_team_restored(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The team name is {team_info.name}")
    )
```

* * *

## <a name="message-reaction-events"></a><span data-ttu-id="d3ada-234">Nachrichtenreaktionsereignisse</span><span class="sxs-lookup"><span data-stu-id="d3ada-234">Message reaction events</span></span>

<span data-ttu-id="d3ada-235">Das Ereignis wird gesendet, wenn ein Benutzer Reaktionen auf eine Nachricht hinzufügt oder entfernt, die `messageReaction` von Ihrem Bot gesendet wurde.</span><span class="sxs-lookup"><span data-stu-id="d3ada-235">The `messageReaction` event is sent when a user adds or removes reactions to a message which was sent by your bot.</span></span> <span data-ttu-id="d3ada-236">Die `replyToId` enthält die ID der bestimmten Nachricht, und die ist die Art der Reaktion im `Type` Textformat.</span><span class="sxs-lookup"><span data-stu-id="d3ada-236">The `replyToId` contains the ID of the specific message, and the `Type` is the type of reaction in text format.</span></span>  <span data-ttu-id="d3ada-237">Die Reaktionstypen sind: "Heiter", "Herz", "Heiter", "Gefällt mir", "Sad", "Überrascht".</span><span class="sxs-lookup"><span data-stu-id="d3ada-237">The types of reactions include: "angry", "heart", "laugh", "like", "Sad", "surprised".</span></span> <span data-ttu-id="d3ada-238">Dieses Ereignis enthält nicht den Inhalt der ursprünglichen Nachricht. Wenn also die Verarbeitung von Reaktionen auf Ihre Nachrichten für Ihren Bot wichtig ist, müssen Sie die Nachrichten speichern, wenn Sie sie senden.</span><span class="sxs-lookup"><span data-stu-id="d3ada-238">This event does not contain the contents of the original message, so if processing reactions to your messages is important for your bot you'll need to store the messages when you send them.</span></span>

| <span data-ttu-id="d3ada-239">EventType</span><span class="sxs-lookup"><span data-stu-id="d3ada-239">EventType</span></span>       | <span data-ttu-id="d3ada-240">Payload (Objekt)</span><span class="sxs-lookup"><span data-stu-id="d3ada-240">Payload object</span></span>   | <span data-ttu-id="d3ada-241">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d3ada-241">Description</span></span>                                                             | <span data-ttu-id="d3ada-242">Bereich</span><span class="sxs-lookup"><span data-stu-id="d3ada-242">Scope</span></span> |
| --------------- | ---------------- | ----------------------------------------------------------------------- | ----- |
| <span data-ttu-id="d3ada-243">messageReaction</span><span class="sxs-lookup"><span data-stu-id="d3ada-243">messageReaction</span></span> | <span data-ttu-id="d3ada-244">reactionsAdded</span><span class="sxs-lookup"><span data-stu-id="d3ada-244">reactionsAdded</span></span>   | [<span data-ttu-id="d3ada-245">Reaktion auf Botnachricht</span><span class="sxs-lookup"><span data-stu-id="d3ada-245">Reaction to bot message</span></span>](#reactions-to-a-bot-message)                   | <span data-ttu-id="d3ada-246">Alle</span><span class="sxs-lookup"><span data-stu-id="d3ada-246">All</span></span>   |
| <span data-ttu-id="d3ada-247">messageReaction</span><span class="sxs-lookup"><span data-stu-id="d3ada-247">messageReaction</span></span> | <span data-ttu-id="d3ada-248">reactionsRemoved</span><span class="sxs-lookup"><span data-stu-id="d3ada-248">reactionsRemoved</span></span> | [<span data-ttu-id="d3ada-249">Reaktion aus Botnachricht entfernt</span><span class="sxs-lookup"><span data-stu-id="d3ada-249">Reaction removed from bot message</span></span>](#reactions-removed-from-bot-message) | <span data-ttu-id="d3ada-250">Alle</span><span class="sxs-lookup"><span data-stu-id="d3ada-250">All</span></span>   |

### <a name="reactions-to-a-bot-message"></a><span data-ttu-id="d3ada-251">Reaktionen auf eine Botnachricht</span><span class="sxs-lookup"><span data-stu-id="d3ada-251">Reactions to a bot message</span></span>

# <a name="cnet"></a>[<span data-ttu-id="d3ada-252">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="d3ada-252">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="d3ada-253">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="d3ada-253">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="d3ada-254">Json</span><span class="sxs-lookup"><span data-stu-id="d3ada-254">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="d3ada-255">Python</span><span class="sxs-lookup"><span data-stu-id="d3ada-255">Python</span></span>](#tab/python)

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

### <a name="reactions-removed-from-bot-message"></a><span data-ttu-id="d3ada-256">Aus bot-Nachricht entfernte Reaktionen</span><span class="sxs-lookup"><span data-stu-id="d3ada-256">Reactions removed from bot message</span></span>

# <a name="cnet"></a>[<span data-ttu-id="d3ada-257">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="d3ada-257">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="d3ada-258">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="d3ada-258">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="d3ada-259">Json</span><span class="sxs-lookup"><span data-stu-id="d3ada-259">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="d3ada-260">Python</span><span class="sxs-lookup"><span data-stu-id="d3ada-260">Python</span></span>](#tab/python)

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

## <a name="samples"></a><span data-ttu-id="d3ada-261">Beispiele</span><span class="sxs-lookup"><span data-stu-id="d3ada-261">Samples</span></span>
<span data-ttu-id="d3ada-262">Beispielcode, der die Unterhaltungsereignisse der Bots zeigt, finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="d3ada-262">For sample code showing the bots conversation events, see:</span></span>

[<span data-ttu-id="d3ada-263">Beispiel für Unterhaltungsereignisse für Microsoft Teams-Bots</span><span class="sxs-lookup"><span data-stu-id="d3ada-263">Microsoft Teams bots conversation events sample</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot)



