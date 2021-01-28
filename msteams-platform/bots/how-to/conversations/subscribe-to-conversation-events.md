---
title: Abonnieren von Unterhaltungsereignissen
author: WashingtonKayaker
description: Abonnieren von Unterhaltungsereignissen von Ihrem Microsoft Teams-Bot.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: b4dc70e4619043bd0b675206770093b086fc5ec6
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014320"
---
# <a name="subscribe-to-conversation-events"></a><span data-ttu-id="b9e51-103">Abonnieren von Unterhaltungsereignissen</span><span class="sxs-lookup"><span data-stu-id="b9e51-103">Subscribe to conversation events</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="b9e51-104">Microsoft Teams sendet Benachrichtigungen an Ihren Bot für Ereignisse, die in Bereichen stattfinden, in denen Ihr Bot aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="b9e51-104">Microsoft Teams sends notifications to your bot for events that happen in scopes where your bot is active.</span></span> <span data-ttu-id="b9e51-105">Sie können diese Ereignisse in Ihrem Code erfassen und mit Aktionen darauf reagieren, z. B. wie folgt:</span><span class="sxs-lookup"><span data-stu-id="b9e51-105">You can capture these events in your code and take action on them, such as the following:</span></span>

* <span data-ttu-id="b9e51-106">Auslösen einer Willkommensnachricht, wenn Ihr Bot zu einem Team hinzugefügt wird</span><span class="sxs-lookup"><span data-stu-id="b9e51-106">Trigger a welcome message when your bot is added to a team</span></span>
* <span data-ttu-id="b9e51-107">Auslösen einer Willkommensnachricht, wenn ein neues Teammitglied hinzugefügt oder entfernt wird</span><span class="sxs-lookup"><span data-stu-id="b9e51-107">Trigger a welcome message when a new team member is added or removed</span></span>
* <span data-ttu-id="b9e51-108">Auslösen einer Benachrichtigung, wenn ein Kanal erstellt, umbenannt oder gelöscht wird</span><span class="sxs-lookup"><span data-stu-id="b9e51-108">Trigger a notification when a channel is created, renamed or deleted</span></span>
* <span data-ttu-id="b9e51-109">Wenn eine Botnachricht von einem Benutzer mit "Gefällt mir" gefällt</span><span class="sxs-lookup"><span data-stu-id="b9e51-109">When a bot message is liked by a user</span></span>

## <a name="conversation-update-events"></a><span data-ttu-id="b9e51-110">Aktualisierungsereignisse in Unterhaltungen</span><span class="sxs-lookup"><span data-stu-id="b9e51-110">Conversation update events</span></span>

> [!Important]
> <span data-ttu-id="b9e51-111">Neue Ereignisse können jederzeit hinzugefügt werden, und Ihr Bot beginnt, sie zu empfangen.</span><span class="sxs-lookup"><span data-stu-id="b9e51-111">New events can be added at any time, and your bot will begin to receive them.</span></span>
> <span data-ttu-id="b9e51-112">Sie müssen die Möglichkeit, unerwartete Ereignisse zu empfangen, entwerfen.</span><span class="sxs-lookup"><span data-stu-id="b9e51-112">You must design for the possibility of receiving unexpected events.</span></span>
> <span data-ttu-id="b9e51-113">Wenn Sie das Bot Framework SDK verwenden, antwortet Ihr Bot automatisch mit einem auf Ereignisse, die Sie `200 - OK` nicht behandeln möchten.</span><span class="sxs-lookup"><span data-stu-id="b9e51-113">If you are using the Bot Framework SDK, your bot will automatically respond with a `200 - OK` to any events you do not choose to handle.</span></span>

<span data-ttu-id="b9e51-114">Ein Bot empfängt ein `conversationUpdate`-Ereignis, wenn er zu einer Unterhaltung hinzugefügt wurde, andere Mitglieder zu einer Unterhaltung hinzugefügt oder daraus entfernt wurden oder sich die Metadaten einer Unterhaltung geändert haben.</span><span class="sxs-lookup"><span data-stu-id="b9e51-114">A bot receives a `conversationUpdate` event when it has been added to a conversation, other members have been added to or removed from a conversation, or conversation metadata has changed.</span></span>

<span data-ttu-id="b9e51-115">Das `conversationUpdate`-Ereignis wird an Ihren Bot gesendet, wenn er Informationen zu Mitgliedschaftsaktualisierungen für Teams empfängt, denen er hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="b9e51-115">The `conversationUpdate` event is sent to your bot when it receives information on membership updates for teams where it has been added.</span></span> <span data-ttu-id="b9e51-116">Er empfängt außerdem eine Aktualisierung, wenn er zum ersten Mal hinzugefügt wurde, speziell für persönliche Unterhaltungen.</span><span class="sxs-lookup"><span data-stu-id="b9e51-116">It also receives an update when it has been added for the first time specifically for personal conversations.</span></span>

<span data-ttu-id="b9e51-117">Die folgende Tabelle enthält eine Liste der Aktualisierungsereignisse für Teams-Unterhaltungen mit Links zu weiteren Details.</span><span class="sxs-lookup"><span data-stu-id="b9e51-117">The following table shows a list of Teams conversation update events, with links to more details.</span></span>

| <span data-ttu-id="b9e51-118">Ergriffene Aktion</span><span class="sxs-lookup"><span data-stu-id="b9e51-118">Action Taken</span></span>        | <span data-ttu-id="b9e51-119">EventType</span><span class="sxs-lookup"><span data-stu-id="b9e51-119">EventType</span></span>         | <span data-ttu-id="b9e51-120">Aufgerufene Methode</span><span class="sxs-lookup"><span data-stu-id="b9e51-120">Method Called</span></span>              | <span data-ttu-id="b9e51-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b9e51-121">Description</span></span>                | <span data-ttu-id="b9e51-122">Bereich</span><span class="sxs-lookup"><span data-stu-id="b9e51-122">Scope</span></span> |
| ------------------- | ----------------- | -------------------------- | -------------------------- | ----- |
| <span data-ttu-id="b9e51-123">Kanal erstellt</span><span class="sxs-lookup"><span data-stu-id="b9e51-123">channel created</span></span>     | <span data-ttu-id="b9e51-124">channelCreated</span><span class="sxs-lookup"><span data-stu-id="b9e51-124">channelCreated</span></span>    | <span data-ttu-id="b9e51-125">OnTeamsChannelCreatedAsync</span><span class="sxs-lookup"><span data-stu-id="b9e51-125">OnTeamsChannelCreatedAsync</span></span> | [<span data-ttu-id="b9e51-126">Ein Kanal wurde erstellt</span><span class="sxs-lookup"><span data-stu-id="b9e51-126">A channel was created</span></span>](#channel-created) | <span data-ttu-id="b9e51-127">Team</span><span class="sxs-lookup"><span data-stu-id="b9e51-127">Team</span></span> |
| <span data-ttu-id="b9e51-128">Kanal umbenannt</span><span class="sxs-lookup"><span data-stu-id="b9e51-128">channel renamed</span></span>     | <span data-ttu-id="b9e51-129">channelRenamed</span><span class="sxs-lookup"><span data-stu-id="b9e51-129">channelRenamed</span></span>    | <span data-ttu-id="b9e51-130">OnTeamsChannelRenamedAsync</span><span class="sxs-lookup"><span data-stu-id="b9e51-130">OnTeamsChannelRenamedAsync</span></span> | [<span data-ttu-id="b9e51-131">Ein Kanal wurde umbenannt</span><span class="sxs-lookup"><span data-stu-id="b9e51-131">A channel was renamed</span></span>](#channel-renamed) | <span data-ttu-id="b9e51-132">Team</span><span class="sxs-lookup"><span data-stu-id="b9e51-132">Team</span></span> |
| <span data-ttu-id="b9e51-133">Kanal gelöscht</span><span class="sxs-lookup"><span data-stu-id="b9e51-133">channel deleted</span></span>     | <span data-ttu-id="b9e51-134">channelDeleted</span><span class="sxs-lookup"><span data-stu-id="b9e51-134">channelDeleted</span></span>    | <span data-ttu-id="b9e51-135">OnTeamsChannelDeletedAsync</span><span class="sxs-lookup"><span data-stu-id="b9e51-135">OnTeamsChannelDeletedAsync</span></span> | [<span data-ttu-id="b9e51-136">Ein Kanal wurde gelöscht</span><span class="sxs-lookup"><span data-stu-id="b9e51-136">A channel was deleted</span></span>](#channel-deleted) | <span data-ttu-id="b9e51-137">Team</span><span class="sxs-lookup"><span data-stu-id="b9e51-137">Team</span></span> |
| <span data-ttu-id="b9e51-138">Kanal wiederhergestellt</span><span class="sxs-lookup"><span data-stu-id="b9e51-138">channel restored</span></span>    | <span data-ttu-id="b9e51-139">channelRestored</span><span class="sxs-lookup"><span data-stu-id="b9e51-139">channelRestored</span></span>    | <span data-ttu-id="b9e51-140">OnTeamsChannelRestoredAsync</span><span class="sxs-lookup"><span data-stu-id="b9e51-140">OnTeamsChannelRestoredAsync</span></span> | [<span data-ttu-id="b9e51-141">Ein Kanal wurde wiederhergestellt</span><span class="sxs-lookup"><span data-stu-id="b9e51-141">A channel was restored</span></span>](#channel-deleted) | <span data-ttu-id="b9e51-142">Team</span><span class="sxs-lookup"><span data-stu-id="b9e51-142">Team</span></span> |
| <span data-ttu-id="b9e51-143">Hinzugefügte Mitglieder</span><span class="sxs-lookup"><span data-stu-id="b9e51-143">members added</span></span>   | <span data-ttu-id="b9e51-144">membersAdded</span><span class="sxs-lookup"><span data-stu-id="b9e51-144">membersAdded</span></span>   | <span data-ttu-id="b9e51-145">OnTeamsMembersAddedAsync</span><span class="sxs-lookup"><span data-stu-id="b9e51-145">OnTeamsMembersAddedAsync</span></span>   | [<span data-ttu-id="b9e51-146">Ein hinzugefügtes Mitglied</span><span class="sxs-lookup"><span data-stu-id="b9e51-146">A member added</span></span>](#team-members-added)   | <span data-ttu-id="b9e51-147">Alle</span><span class="sxs-lookup"><span data-stu-id="b9e51-147">All</span></span> |
| <span data-ttu-id="b9e51-148">entfernte Mitglieder</span><span class="sxs-lookup"><span data-stu-id="b9e51-148">members removed</span></span> | <span data-ttu-id="b9e51-149">membersRemoved</span><span class="sxs-lookup"><span data-stu-id="b9e51-149">membersRemoved</span></span> | <span data-ttu-id="b9e51-150">OnTeamsMembersRemovedAsync</span><span class="sxs-lookup"><span data-stu-id="b9e51-150">OnTeamsMembersRemovedAsync</span></span> | [<span data-ttu-id="b9e51-151">Ein Mitglied wurde entfernt</span><span class="sxs-lookup"><span data-stu-id="b9e51-151">A member was removed</span></span>](#team-members-removed) | <span data-ttu-id="b9e51-152">groupChat & Team</span><span class="sxs-lookup"><span data-stu-id="b9e51-152">groupChat & team</span></span> |
| <span data-ttu-id="b9e51-153">Team umbenannt</span><span class="sxs-lookup"><span data-stu-id="b9e51-153">team renamed</span></span>        | <span data-ttu-id="b9e51-154">teamRenamed</span><span class="sxs-lookup"><span data-stu-id="b9e51-154">teamRenamed</span></span>       | <span data-ttu-id="b9e51-155">OnTeamsTeamRenamedAsync</span><span class="sxs-lookup"><span data-stu-id="b9e51-155">OnTeamsTeamRenamedAsync</span></span>    | [<span data-ttu-id="b9e51-156">Ein Team wurde umbenannt</span><span class="sxs-lookup"><span data-stu-id="b9e51-156">A Team was renamed</span></span>](#team-renamed)       | <span data-ttu-id="b9e51-157">Team</span><span class="sxs-lookup"><span data-stu-id="b9e51-157">Team</span></span> |
| <span data-ttu-id="b9e51-158">Team gelöscht</span><span class="sxs-lookup"><span data-stu-id="b9e51-158">team deleted</span></span>        | <span data-ttu-id="b9e51-159">teamDeleted</span><span class="sxs-lookup"><span data-stu-id="b9e51-159">teamDeleted</span></span>       | <span data-ttu-id="b9e51-160">OnTeamsTeamDeletedAsync</span><span class="sxs-lookup"><span data-stu-id="b9e51-160">OnTeamsTeamDeletedAsync</span></span>    | [<span data-ttu-id="b9e51-161">Ein Team wurde gelöscht</span><span class="sxs-lookup"><span data-stu-id="b9e51-161">A Team was deleted</span></span>](#team-deleted)       | <span data-ttu-id="b9e51-162">Team</span><span class="sxs-lookup"><span data-stu-id="b9e51-162">Team</span></span> |
| <span data-ttu-id="b9e51-163">Team archiviert</span><span class="sxs-lookup"><span data-stu-id="b9e51-163">team archived</span></span>        | <span data-ttu-id="b9e51-164">teamArchived</span><span class="sxs-lookup"><span data-stu-id="b9e51-164">teamArchived</span></span>       | <span data-ttu-id="b9e51-165">OnTeamsTeamArchivedAsync</span><span class="sxs-lookup"><span data-stu-id="b9e51-165">OnTeamsTeamArchivedAsync</span></span>    | [<span data-ttu-id="b9e51-166">Ein Team wurde archiviert</span><span class="sxs-lookup"><span data-stu-id="b9e51-166">A Team was archived</span></span>](#team-archived)       | <span data-ttu-id="b9e51-167">Team</span><span class="sxs-lookup"><span data-stu-id="b9e51-167">Team</span></span> |
| <span data-ttu-id="b9e51-168">team unarchived</span><span class="sxs-lookup"><span data-stu-id="b9e51-168">team unarchived</span></span>        | <span data-ttu-id="b9e51-169">teamUnarchived</span><span class="sxs-lookup"><span data-stu-id="b9e51-169">teamUnarchived</span></span>       | <span data-ttu-id="b9e51-170">OnTeamsTeamUnarchivedAsync</span><span class="sxs-lookup"><span data-stu-id="b9e51-170">OnTeamsTeamUnarchivedAsync</span></span>    | [<span data-ttu-id="b9e51-171">Ein Team wurde nicht archiviert</span><span class="sxs-lookup"><span data-stu-id="b9e51-171">A Team was unarchived</span></span>](#team-unarchived)       | <span data-ttu-id="b9e51-172">Team</span><span class="sxs-lookup"><span data-stu-id="b9e51-172">Team</span></span> |
| <span data-ttu-id="b9e51-173">Team wiederhergestellt</span><span class="sxs-lookup"><span data-stu-id="b9e51-173">team restored</span></span>        | <span data-ttu-id="b9e51-174">teamRestored</span><span class="sxs-lookup"><span data-stu-id="b9e51-174">teamRestored</span></span>      | <span data-ttu-id="b9e51-175">OnTeamsTeamRestoredAsync</span><span class="sxs-lookup"><span data-stu-id="b9e51-175">OnTeamsTeamRestoredAsync</span></span>    | [<span data-ttu-id="b9e51-176">Ein Team wurde wiederhergestellt</span><span class="sxs-lookup"><span data-stu-id="b9e51-176">A Team was restored</span></span>](#team-restored)       | <span data-ttu-id="b9e51-177">Team</span><span class="sxs-lookup"><span data-stu-id="b9e51-177">Team</span></span> |

### <a name="channel-created"></a><span data-ttu-id="b9e51-178">Erstellter Kanal</span><span class="sxs-lookup"><span data-stu-id="b9e51-178">Channel created</span></span>

<span data-ttu-id="b9e51-179">Das vom Kanal erstellte Ereignis wird an Ihren Bot gesendet, wenn ein neuer Kanal in einem Team erstellt wird, in dem Ihr Bot installiert ist.</span><span class="sxs-lookup"><span data-stu-id="b9e51-179">The channel created event is sent to your bot whenever a new channel is created in a team your bot is installed in.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="b9e51-180">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="b9e51-180">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelCreatedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the Channel created");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="b9e51-181">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="b9e51-181">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="b9e51-182">Json</span><span class="sxs-lookup"><span data-stu-id="b9e51-182">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="b9e51-183">Python</span><span class="sxs-lookup"><span data-stu-id="b9e51-183">Python</span></span>](#tab/python)

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

### <a name="channel-renamed"></a><span data-ttu-id="b9e51-184">Kanal umbenannt</span><span class="sxs-lookup"><span data-stu-id="b9e51-184">Channel renamed</span></span>

<span data-ttu-id="b9e51-185">Das kanalbenannte Ereignis wird an Ihren Bot gesendet, wenn ein Kanal in einem Team umbenannt wird, in dem Ihr Bot installiert ist.</span><span class="sxs-lookup"><span data-stu-id="b9e51-185">The channel renamed event is sent to your bot whenever a channel is renamed in a team your bot is installed in.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="b9e51-186">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="b9e51-186">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelRenamedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the new Channel name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="b9e51-187">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="b9e51-187">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="b9e51-188">Json</span><span class="sxs-lookup"><span data-stu-id="b9e51-188">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="b9e51-189">Python</span><span class="sxs-lookup"><span data-stu-id="b9e51-189">Python</span></span>](#tab/python)

```python
async def on_teams_channel_renamed(
    self, channel_info: ChannelInfo, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The new channel name is {channel_info.name}")
    )
```

* * *

### <a name="channel-deleted"></a><span data-ttu-id="b9e51-190">Kanal gelöscht</span><span class="sxs-lookup"><span data-stu-id="b9e51-190">Channel Deleted</span></span>

<span data-ttu-id="b9e51-191">Das gelöschte Kanalereignis wird an Ihren Bot gesendet, wenn ein Kanal in einem Team gelöscht wird, in dem Ihr Bot installiert ist.</span><span class="sxs-lookup"><span data-stu-id="b9e51-191">The channel deleted event is sent to your bot whenever a channel is deleted in a team your bot is installed in.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="b9e51-192">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="b9e51-192">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelDeletedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the Channel deleted");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="b9e51-193">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="b9e51-193">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="b9e51-194">Json</span><span class="sxs-lookup"><span data-stu-id="b9e51-194">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="b9e51-195">Python</span><span class="sxs-lookup"><span data-stu-id="b9e51-195">Python</span></span>](#tab/python)

```python
async def on_teams_channel_deleted(
    self, channel_info: ChannelInfo, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The deleted channel is {channel_info.name}")
    )
```

* * *

### <a name="channel-restored"></a><span data-ttu-id="b9e51-196">Kanal wiederhergestellt</span><span class="sxs-lookup"><span data-stu-id="b9e51-196">Channel restored</span></span>

<span data-ttu-id="b9e51-197">Das Kanal-wiederhergestellte Ereignis wird an Ihren Bot gesendet, wenn ein Kanal, der zuvor gelöscht wurde, in einem Team wiederhergestellt wird, in dem Ihr Bot bereits installiert ist.</span><span class="sxs-lookup"><span data-stu-id="b9e51-197">The channel restored event is sent to your bot whenever a channel that was previously deleted is restored in a team that your bot is already installed in.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="b9e51-198">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="b9e51-198">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelRestoredAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the Channel restored.");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="b9e51-199">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="b9e51-199">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="b9e51-200">Json</span><span class="sxs-lookup"><span data-stu-id="b9e51-200">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="b9e51-201">Python</span><span class="sxs-lookup"><span data-stu-id="b9e51-201">Python</span></span>](#tab/python)

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

### <a name="team-members-added"></a><span data-ttu-id="b9e51-202">Hinzugefügte Teammitglieder</span><span class="sxs-lookup"><span data-stu-id="b9e51-202">Team members added</span></span>

<span data-ttu-id="b9e51-203">Das Ereignis wird an Ihren Bot gesendet, wenn es zum ersten Mal zu einer Unterhaltung hinzugefügt wird und jedes Mal, wenn ein neuer Benutzer zu einem Team- oder Gruppenchat hinzugefügt wird, in dem Ihr Bot `teamMemberAdded` installiert ist.</span><span class="sxs-lookup"><span data-stu-id="b9e51-203">The `teamMemberAdded` event is sent to your bot the first time it is added to a conversation and every time a new user is added to a team or group chat that your bot is installed in.</span></span> <span data-ttu-id="b9e51-204">Die Benutzerinformationen (ID) sind für Ihren Bot eindeutig und können für die zukünftige Verwendung durch Ihren Dienst zwischengespeichert werden (z. B. senden einer Nachricht an einen bestimmten Benutzer).</span><span class="sxs-lookup"><span data-stu-id="b9e51-204">The user information (ID) is unique for your bot and can be cached for future use by your service (such as sending a message to a specific user).</span></span>

# <a name="cnet"></a>[<span data-ttu-id="b9e51-205">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="b9e51-205">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="b9e51-206">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="b9e51-206">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="b9e51-207">Json</span><span class="sxs-lookup"><span data-stu-id="b9e51-207">JSON</span></span>](#tab/json)

<span data-ttu-id="b9e51-208">Dies ist die Nachricht, die Ihr Bot erhält, wenn der Bot **einem Team hinzugefügt wird.**</span><span class="sxs-lookup"><span data-stu-id="b9e51-208">This is the message your bot will receive when the bot is added **to a team**.</span></span>

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

<span data-ttu-id="b9e51-209">Dies ist die Nachricht, die Ihr Bot erhält, wenn der Bot zu einem *1:1-Chat hinzugefügt wird.*</span><span class="sxs-lookup"><span data-stu-id="b9e51-209">This is the message your bot will receive when the bot is added \**to a one-to-one chat*.</span></span>

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

# <a name="python"></a>[<span data-ttu-id="b9e51-210">Python</span><span class="sxs-lookup"><span data-stu-id="b9e51-210">Python</span></span>](#tab/python)

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

<span data-ttu-id="b9e51-211">_ \* \*</span><span class="sxs-lookup"><span data-stu-id="b9e51-211">_ \* \*</span></span>

### <a name="team-members-removed"></a><span data-ttu-id="b9e51-212">Entfernte Teammitglieder</span><span class="sxs-lookup"><span data-stu-id="b9e51-212">Team members removed</span></span>

<span data-ttu-id="b9e51-213">Das Ereignis wird an Ihren Bot gesendet, wenn es aus einem Team entfernt wird und jedes Mal, wenn ein Benutzer aus einem Team entfernt wird, in dem Ihr Bot `teamMemberRemoved` Mitglied ist.</span><span class="sxs-lookup"><span data-stu-id="b9e51-213">The `teamMemberRemoved` event is sent to your bot if it is removed from a team and every time any user is removed from a team that your bot is a member of.</span></span> <span data-ttu-id="b9e51-214">Sie können feststellen, ob das neue Element der Bot selbst oder ein Benutzer war, indem Sie sich das `Activity` Objekt des . `turnContext`</span><span class="sxs-lookup"><span data-stu-id="b9e51-214">You can determine if the new member removed was the bot itself or a user by looking at the `Activity` object of the `turnContext`.</span></span>  <span data-ttu-id="b9e51-215">Wenn das Feld des Objekts mit dem Feld des Objekts identisch ist, ist das entfernte Element der Bot, andernfalls handelt es sich `Id` `MembersRemoved` um einen `Id` `Recipient` Benutzer.</span><span class="sxs-lookup"><span data-stu-id="b9e51-215">If the `Id` field of the `MembersRemoved` object is the same as the `Id` field of the `Recipient` object, then the member removed is the bot, otherwise, it is a user.</span></span>  <span data-ttu-id="b9e51-216">Die Bots `Id` sind im Allgemeinen: `28:<MicrosoftAppId>`</span><span class="sxs-lookup"><span data-stu-id="b9e51-216">The bot's `Id` will generally be: `28:<MicrosoftAppId>`</span></span>

[!Note] <span data-ttu-id="b9e51-217">Wenn ein Benutzer dauerhaft aus einem Mandanten gelöscht wird, `membersRemoved conversationUpdate` wird das Ereignis ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="b9e51-217">When a user is permanently deleted from a tenant, `membersRemoved conversationUpdate` event is triggered.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="b9e51-218">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="b9e51-218">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="b9e51-219">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="b9e51-219">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="b9e51-220">Json</span><span class="sxs-lookup"><span data-stu-id="b9e51-220">JSON</span></span>](#tab/json)

<span data-ttu-id="b9e51-221">Das Objekt im folgenden Nutzlastbeispiel basiert auf dem Hinzufügen eines Mitglieds zu einem Team anstelle eines Gruppenchats oder dem Initiieren einer neuen `channelData` 1:1-Unterhaltung:</span><span class="sxs-lookup"><span data-stu-id="b9e51-221">The `channelData` object in the following payload example is based on adding a member to a team rather than a group chat, or initiating a new one-to-one conversation:</span></span>

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


# <a name="python"></a>[<span data-ttu-id="b9e51-222">Python</span><span class="sxs-lookup"><span data-stu-id="b9e51-222">Python</span></span>](#tab/python)

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

### <a name="team-renamed"></a><span data-ttu-id="b9e51-223">Team umbenannt</span><span class="sxs-lookup"><span data-stu-id="b9e51-223">Team renamed</span></span>

<span data-ttu-id="b9e51-224">Ihr Bot wird benachrichtigt, wenn das Team, in dem er sich befindet, umbenannt wurde.</span><span class="sxs-lookup"><span data-stu-id="b9e51-224">Your bot is notified when the team it is in has been renamed.</span></span> <span data-ttu-id="b9e51-225">Es empfängt ein `conversationUpdate` Ereignis mit `eventType.teamRenamed` dem `channelData` Objekt.</span><span class="sxs-lookup"><span data-stu-id="b9e51-225">It receives a `conversationUpdate` event with `eventType.teamRenamed` in the `channelData` object.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="b9e51-226">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="b9e51-226">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamRenamedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the new Team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="b9e51-227">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="b9e51-227">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="b9e51-228">Json</span><span class="sxs-lookup"><span data-stu-id="b9e51-228">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="b9e51-229">Python</span><span class="sxs-lookup"><span data-stu-id="b9e51-229">Python</span></span>](#tab/python)

```python
async def on_teams_team_renamed(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The new team name is {team_info.name}")
    )
```

* * *

### <a name="team-deleted"></a><span data-ttu-id="b9e51-230">Team gelöscht</span><span class="sxs-lookup"><span data-stu-id="b9e51-230">Team deleted</span></span>

<span data-ttu-id="b9e51-231">Ihr Bot wird benachrichtigt, wenn das Team, in dem er sich befindet, gelöscht wurde.</span><span class="sxs-lookup"><span data-stu-id="b9e51-231">Your bot is notified when the team it is in has been deleted.</span></span> <span data-ttu-id="b9e51-232">Es empfängt ein `conversationUpdate` Ereignis mit `eventType.teamDeleted` dem `channelData` Objekt.</span><span class="sxs-lookup"><span data-stu-id="b9e51-232">It receives a `conversationUpdate` event with `eventType.teamDeleted` in the `channelData` object.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="b9e51-233">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="b9e51-233">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamDeletedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    //handle delete event
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="b9e51-234">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="b9e51-234">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onTeamsTeamDeletedEvent(async (teamInfo: TeamInfo, turnContext: TurnContext, next: () => Promise<void>): Promise<void> => {
            //handle delete event
            await next();
        });
    }
}
```

# <a name="json"></a>[<span data-ttu-id="b9e51-235">Json</span><span class="sxs-lookup"><span data-stu-id="b9e51-235">JSON</span></span>](#tab/json)

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
        "eventType": "teamDeleted",
        "tenant": { 
           "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    }
}
```

# <a name="python"></a>[<span data-ttu-id="b9e51-236">Python</span><span class="sxs-lookup"><span data-stu-id="b9e51-236">Python</span></span>](#tab/python)

```python
async def on_teams_team_deleted(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    //handle delete event
    )
```

* * *

### <a name="team-restored"></a><span data-ttu-id="b9e51-237">Team wiederhergestellt</span><span class="sxs-lookup"><span data-stu-id="b9e51-237">Team restored</span></span>

<span data-ttu-id="b9e51-238">Der Bot erhält eine Benachrichtigung, wenn er nach dem Löschen wiederhergestellt wird.</span><span class="sxs-lookup"><span data-stu-id="b9e51-238">The bot receives a notification when it is restored from deletion.</span></span> <span data-ttu-id="b9e51-239">Es empfängt ein `conversationUpdate` Ereignis mit `eventType.teamrestored` dem `channelData` Objekt.</span><span class="sxs-lookup"><span data-stu-id="b9e51-239">It receives a `conversationUpdate` event with `eventType.teamrestored` in the `channelData` object.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="b9e51-240">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="b9e51-240">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamrestoredAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="b9e51-241">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="b9e51-241">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="b9e51-242">Json</span><span class="sxs-lookup"><span data-stu-id="b9e51-242">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="b9e51-243">Python</span><span class="sxs-lookup"><span data-stu-id="b9e51-243">Python</span></span>](#tab/python)

```python
async def on_teams_team_restored(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The team name is {team_info.name}")
    )
```

* * *

### <a name="team-archived"></a><span data-ttu-id="b9e51-244">Team archiviert</span><span class="sxs-lookup"><span data-stu-id="b9e51-244">Team archived</span></span>

<span data-ttu-id="b9e51-245">Der Bot erhält eine Benachrichtigung, wenn das Team archiviert wird, in dem er installiert ist.</span><span class="sxs-lookup"><span data-stu-id="b9e51-245">The bot receives a notification when the team it is installed in is archived.</span></span> <span data-ttu-id="b9e51-246">Es empfängt ein `conversationUpdate` Ereignis mit `eventType.teamarchived` dem `channelData` Objekt.</span><span class="sxs-lookup"><span data-stu-id="b9e51-246">It receives a `conversationUpdate` event with `eventType.teamarchived` in the `channelData` object.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="b9e51-247">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="b9e51-247">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamArchivedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="b9e51-248">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="b9e51-248">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="b9e51-249">Json</span><span class="sxs-lookup"><span data-stu-id="b9e51-249">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="b9e51-250">Python</span><span class="sxs-lookup"><span data-stu-id="b9e51-250">Python</span></span>](#tab/python)

```python
async def on_teams_team_archived(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The team name is {team_info.name}")
    )
```

* * *


### <a name="team-unarchived"></a><span data-ttu-id="b9e51-251">Team wurde archiviert</span><span class="sxs-lookup"><span data-stu-id="b9e51-251">Team unarchived</span></span>

<span data-ttu-id="b9e51-252">Der Bot erhält eine Benachrichtigung, wenn das Team, in dem er installiert ist, nicht mehr archiviert wird.</span><span class="sxs-lookup"><span data-stu-id="b9e51-252">The bot receives a notification when the team it is installed in is unarchived.</span></span> <span data-ttu-id="b9e51-253">Es empfängt ein `conversationUpdate` Ereignis mit `eventType.teamUnarchived` dem `channelData` Objekt.</span><span class="sxs-lookup"><span data-stu-id="b9e51-253">It receives a `conversationUpdate` event with `eventType.teamUnarchived` in the `channelData` object.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="b9e51-254">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="b9e51-254">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamUnarchivedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="b9e51-255">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="b9e51-255">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onTeamsTeamUnarchivedEvent(async (teamInfo: TeamInfo, turnContext: TurnContext, next: () => Promise<void>): Promise<void> => {
            const card = CardFactory.heroCard('Team archived', `${teamInfo.name} is the team name`);
            const message = MessageFactory.attachment(card);
            await turnContext.sendActivity(message);
            await next();
        });
    }
}
```

# <a name="json"></a>[<span data-ttu-id="b9e51-256">Json</span><span class="sxs-lookup"><span data-stu-id="b9e51-256">JSON</span></span>](#tab/json)

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
        "eventType": "teamUnarchived",
        "tenant": { 
           "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    }
}
```

# <a name="python"></a>[<span data-ttu-id="b9e51-257">Python</span><span class="sxs-lookup"><span data-stu-id="b9e51-257">Python</span></span>](#tab/python)

```python
async def on_teams_team_unarchived(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The team name is {team_info.name}")
    )
```

* * *

## <a name="message-reaction-events"></a><span data-ttu-id="b9e51-258">Nachrichtenreaktionsereignisse</span><span class="sxs-lookup"><span data-stu-id="b9e51-258">Message reaction events</span></span>

<span data-ttu-id="b9e51-259">Das Ereignis wird gesendet, wenn ein Benutzer Reaktionen auf eine Nachricht hinzufügt oder entfernt, die `messageReaction` von Ihrem Bot gesendet wurde.</span><span class="sxs-lookup"><span data-stu-id="b9e51-259">The `messageReaction` event is sent when a user adds or removes reactions to a message which was sent by your bot.</span></span> <span data-ttu-id="b9e51-260">Die `replyToId` enthält die ID der bestimmten Nachricht, und die ist die Art der Reaktion im `Type` Textformat.</span><span class="sxs-lookup"><span data-stu-id="b9e51-260">The `replyToId` contains the ID of the specific message, and the `Type` is the type of reaction in text format.</span></span>  <span data-ttu-id="b9e51-261">Die Reaktionstypen sind: "Heiter", "Herz", "Heiter", "Gefällt mir", "Sad", "Überrascht".</span><span class="sxs-lookup"><span data-stu-id="b9e51-261">The types of reactions include: "angry", "heart", "laugh", "like", "Sad", "surprised".</span></span> <span data-ttu-id="b9e51-262">Dieses Ereignis enthält nicht den Inhalt der ursprünglichen Nachricht. Wenn also die Verarbeitung von Reaktionen auf Ihre Nachrichten für Ihren Bot wichtig ist, müssen Sie die Nachrichten speichern, wenn Sie sie senden.</span><span class="sxs-lookup"><span data-stu-id="b9e51-262">This event does not contain the contents of the original message, so if processing reactions to your messages is important for your bot you'll need to store the messages when you send them.</span></span>

| <span data-ttu-id="b9e51-263">EventType</span><span class="sxs-lookup"><span data-stu-id="b9e51-263">EventType</span></span>       | <span data-ttu-id="b9e51-264">Payload (Objekt)</span><span class="sxs-lookup"><span data-stu-id="b9e51-264">Payload object</span></span>   | <span data-ttu-id="b9e51-265">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b9e51-265">Description</span></span>                                                             | <span data-ttu-id="b9e51-266">Bereich</span><span class="sxs-lookup"><span data-stu-id="b9e51-266">Scope</span></span> |
| --------------- | ---------------- | ----------------------------------------------------------------------- | ----- |
| <span data-ttu-id="b9e51-267">messageReaction</span><span class="sxs-lookup"><span data-stu-id="b9e51-267">messageReaction</span></span> | <span data-ttu-id="b9e51-268">reactionsAdded</span><span class="sxs-lookup"><span data-stu-id="b9e51-268">reactionsAdded</span></span>   | [<span data-ttu-id="b9e51-269">Reaktion auf Botnachricht</span><span class="sxs-lookup"><span data-stu-id="b9e51-269">Reaction to bot message</span></span>](#reactions-to-a-bot-message)                   | <span data-ttu-id="b9e51-270">Alle</span><span class="sxs-lookup"><span data-stu-id="b9e51-270">All</span></span>   |
| <span data-ttu-id="b9e51-271">messageReaction</span><span class="sxs-lookup"><span data-stu-id="b9e51-271">messageReaction</span></span> | <span data-ttu-id="b9e51-272">reactionsRemoved</span><span class="sxs-lookup"><span data-stu-id="b9e51-272">reactionsRemoved</span></span> | [<span data-ttu-id="b9e51-273">Reaktion aus Botnachricht entfernt</span><span class="sxs-lookup"><span data-stu-id="b9e51-273">Reaction removed from bot message</span></span>](#reactions-removed-from-bot-message) | <span data-ttu-id="b9e51-274">Alle</span><span class="sxs-lookup"><span data-stu-id="b9e51-274">All</span></span>   |

### <a name="reactions-to-a-bot-message"></a><span data-ttu-id="b9e51-275">Reaktionen auf eine Botnachricht</span><span class="sxs-lookup"><span data-stu-id="b9e51-275">Reactions to a bot message</span></span>

# <a name="cnet"></a>[<span data-ttu-id="b9e51-276">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="b9e51-276">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="b9e51-277">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="b9e51-277">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="b9e51-278">Json</span><span class="sxs-lookup"><span data-stu-id="b9e51-278">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="b9e51-279">Python</span><span class="sxs-lookup"><span data-stu-id="b9e51-279">Python</span></span>](#tab/python)

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

### <a name="reactions-removed-from-bot-message"></a><span data-ttu-id="b9e51-280">Aus bot-Nachricht entfernte Reaktionen</span><span class="sxs-lookup"><span data-stu-id="b9e51-280">Reactions removed from bot message</span></span>

# <a name="cnet"></a>[<span data-ttu-id="b9e51-281">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="b9e51-281">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="b9e51-282">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="b9e51-282">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="b9e51-283">Json</span><span class="sxs-lookup"><span data-stu-id="b9e51-283">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="b9e51-284">Python</span><span class="sxs-lookup"><span data-stu-id="b9e51-284">Python</span></span>](#tab/python)

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

## <a name="samples"></a><span data-ttu-id="b9e51-285">Beispiele</span><span class="sxs-lookup"><span data-stu-id="b9e51-285">Samples</span></span>
<span data-ttu-id="b9e51-286">Beispielcode, der die Unterhaltungsereignisse der Bots zeigt, finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="b9e51-286">For sample code showing the bots conversation events, see:</span></span>

[<span data-ttu-id="b9e51-287">Beispiel für Unterhaltungsereignisse für Microsoft Teams-Bots</span><span class="sxs-lookup"><span data-stu-id="b9e51-287">Microsoft Teams bots conversation events sample</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot)



