---
title: Abonnieren von Unterhaltungsereignissen
author: WashingtonKayaker
description: Abonnieren von Unterhaltungsereignissen von Ihrem Microsoft Teams-Bot.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: bc4ae36d8cffe5b19ee778a71e1c7b1c00c5e88c
ms.sourcegitcommit: b50f6d68482cad43a60642a9947d1be17809a7df
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2021
ms.locfileid: "51634502"
---
# <a name="subscribe-to-conversation-events"></a><span data-ttu-id="76421-103">Abonnieren von Unterhaltungsereignissen</span><span class="sxs-lookup"><span data-stu-id="76421-103">Subscribe to conversation events</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="76421-104">Microsoft Teams sendet Benachrichtigungen an Ihren Bot für Ereignisse, die in Bereichen stattfinden, in denen Ihr Bot aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="76421-104">Microsoft Teams sends notifications to your bot for events that happen in scopes where your bot is active.</span></span> <span data-ttu-id="76421-105">Sie können diese Ereignisse in Ihrem Code erfassen und mit Aktionen darauf reagieren, z. B. wie folgt:</span><span class="sxs-lookup"><span data-stu-id="76421-105">You can capture these events in your code and take action on them, such as the following:</span></span>

* <span data-ttu-id="76421-106">Auslösen einer Willkommensnachricht, wenn Ihr Bot zu einem Team hinzugefügt wird</span><span class="sxs-lookup"><span data-stu-id="76421-106">Trigger a welcome message when your bot is added to a team</span></span>
* <span data-ttu-id="76421-107">Auslösen einer Willkommensnachricht, wenn ein neues Teammitglied hinzugefügt oder entfernt wird</span><span class="sxs-lookup"><span data-stu-id="76421-107">Trigger a welcome message when a new team member is added or removed</span></span>
* <span data-ttu-id="76421-108">Auslösen einer Benachrichtigung beim Erstellen, Umbenennen oder Löschen eines Kanals</span><span class="sxs-lookup"><span data-stu-id="76421-108">Trigger a notification when a channel is created, renamed or deleted</span></span>
* <span data-ttu-id="76421-109">Wenn eine Botnachricht von einem Benutzer gemocht wird</span><span class="sxs-lookup"><span data-stu-id="76421-109">When a bot message is liked by a user</span></span>

## <a name="conversation-update-events"></a><span data-ttu-id="76421-110">Aktualisierungsereignisse in Unterhaltungen</span><span class="sxs-lookup"><span data-stu-id="76421-110">Conversation update events</span></span>

> [!Important]
> <span data-ttu-id="76421-111">Neue Ereignisse können jederzeit hinzugefügt werden, und Ihr Bot beginnt, sie zu empfangen.</span><span class="sxs-lookup"><span data-stu-id="76421-111">New events can be added at any time, and your bot will begin to receive them.</span></span>
> <span data-ttu-id="76421-112">Sie müssen entwerfen, ob unerwartete Ereignisse empfangen werden können.</span><span class="sxs-lookup"><span data-stu-id="76421-112">You must design for the possibility of receiving unexpected events.</span></span>
> <span data-ttu-id="76421-113">Wenn Sie das Bot Framework SDK verwenden, antwortet Ihr Bot automatisch mit einem auf Ereignisse, die Sie nicht `200 - OK` behandeln möchten.</span><span class="sxs-lookup"><span data-stu-id="76421-113">If you are using the Bot Framework SDK, your bot will automatically respond with a `200 - OK` to any events you do not choose to handle.</span></span>

<span data-ttu-id="76421-114">Ein Bot empfängt ein `conversationUpdate`-Ereignis, wenn er zu einer Unterhaltung hinzugefügt wurde, andere Mitglieder zu einer Unterhaltung hinzugefügt oder daraus entfernt wurden oder sich die Metadaten einer Unterhaltung geändert haben.</span><span class="sxs-lookup"><span data-stu-id="76421-114">A bot receives a `conversationUpdate` event when it has been added to a conversation, other members have been added to or removed from a conversation, or conversation metadata has changed.</span></span>

<span data-ttu-id="76421-115">Das `conversationUpdate`-Ereignis wird an Ihren Bot gesendet, wenn er Informationen zu Mitgliedschaftsaktualisierungen für Teams empfängt, denen er hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="76421-115">The `conversationUpdate` event is sent to your bot when it receives information on membership updates for teams where it has been added.</span></span> <span data-ttu-id="76421-116">Er empfängt außerdem eine Aktualisierung, wenn er zum ersten Mal hinzugefügt wurde, speziell für persönliche Unterhaltungen.</span><span class="sxs-lookup"><span data-stu-id="76421-116">It also receives an update when it has been added for the first time specifically for personal conversations.</span></span>

<span data-ttu-id="76421-117">In der folgenden Tabelle ist eine Liste der Unterhaltungsaktualisierungsereignisse von Teams mit Links zu weiteren Details aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="76421-117">The following table shows a list of Teams conversation update events, with links to more details.</span></span>

| <span data-ttu-id="76421-118">Ergriffene Aktion</span><span class="sxs-lookup"><span data-stu-id="76421-118">Action Taken</span></span>        | <span data-ttu-id="76421-119">EventType</span><span class="sxs-lookup"><span data-stu-id="76421-119">EventType</span></span>         | <span data-ttu-id="76421-120">Methode aufgerufen</span><span class="sxs-lookup"><span data-stu-id="76421-120">Method Called</span></span>              | <span data-ttu-id="76421-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="76421-121">Description</span></span>                | <span data-ttu-id="76421-122">Bereich</span><span class="sxs-lookup"><span data-stu-id="76421-122">Scope</span></span> |
| ------------------- | ----------------- | -------------------------- | -------------------------- | ----- |
| <span data-ttu-id="76421-123">Kanal erstellt</span><span class="sxs-lookup"><span data-stu-id="76421-123">channel created</span></span>     | <span data-ttu-id="76421-124">channelCreated</span><span class="sxs-lookup"><span data-stu-id="76421-124">channelCreated</span></span>    | <span data-ttu-id="76421-125">OnTeamsChannelCreatedAsync</span><span class="sxs-lookup"><span data-stu-id="76421-125">OnTeamsChannelCreatedAsync</span></span> | [<span data-ttu-id="76421-126">Ein Kanal wurde erstellt</span><span class="sxs-lookup"><span data-stu-id="76421-126">A channel was created</span></span>](#channel-created) | <span data-ttu-id="76421-127">Team</span><span class="sxs-lookup"><span data-stu-id="76421-127">Team</span></span> |
| <span data-ttu-id="76421-128">Kanal umbenannt</span><span class="sxs-lookup"><span data-stu-id="76421-128">channel renamed</span></span>     | <span data-ttu-id="76421-129">channelRenamed</span><span class="sxs-lookup"><span data-stu-id="76421-129">channelRenamed</span></span>    | <span data-ttu-id="76421-130">OnTeamsChannelRenamedAsync</span><span class="sxs-lookup"><span data-stu-id="76421-130">OnTeamsChannelRenamedAsync</span></span> | [<span data-ttu-id="76421-131">Ein Kanal wurde umbenannt</span><span class="sxs-lookup"><span data-stu-id="76421-131">A channel was renamed</span></span>](#channel-renamed) | <span data-ttu-id="76421-132">Team</span><span class="sxs-lookup"><span data-stu-id="76421-132">Team</span></span> |
| <span data-ttu-id="76421-133">Kanal gelöscht</span><span class="sxs-lookup"><span data-stu-id="76421-133">channel deleted</span></span>     | <span data-ttu-id="76421-134">channelDeleted</span><span class="sxs-lookup"><span data-stu-id="76421-134">channelDeleted</span></span>    | <span data-ttu-id="76421-135">OnTeamsChannelDeletedAsync</span><span class="sxs-lookup"><span data-stu-id="76421-135">OnTeamsChannelDeletedAsync</span></span> | [<span data-ttu-id="76421-136">Ein Kanal wurde gelöscht</span><span class="sxs-lookup"><span data-stu-id="76421-136">A channel was deleted</span></span>](#channel-deleted) | <span data-ttu-id="76421-137">Team</span><span class="sxs-lookup"><span data-stu-id="76421-137">Team</span></span> |
| <span data-ttu-id="76421-138">Kanal wiederhergestellt</span><span class="sxs-lookup"><span data-stu-id="76421-138">channel restored</span></span>    | <span data-ttu-id="76421-139">channelRestored</span><span class="sxs-lookup"><span data-stu-id="76421-139">channelRestored</span></span>    | <span data-ttu-id="76421-140">OnTeamsChannelRestoredAsync</span><span class="sxs-lookup"><span data-stu-id="76421-140">OnTeamsChannelRestoredAsync</span></span> | [<span data-ttu-id="76421-141">Ein Kanal wurde wiederhergestellt</span><span class="sxs-lookup"><span data-stu-id="76421-141">A channel was restored</span></span>](#channel-deleted) | <span data-ttu-id="76421-142">Team</span><span class="sxs-lookup"><span data-stu-id="76421-142">Team</span></span> |
| <span data-ttu-id="76421-143">hinzugefügte Mitglieder</span><span class="sxs-lookup"><span data-stu-id="76421-143">members added</span></span>   | <span data-ttu-id="76421-144">membersAdded</span><span class="sxs-lookup"><span data-stu-id="76421-144">membersAdded</span></span>   | <span data-ttu-id="76421-145">OnTeamsMembersAddedAsync</span><span class="sxs-lookup"><span data-stu-id="76421-145">OnTeamsMembersAddedAsync</span></span>   | [<span data-ttu-id="76421-146">Ein hinzugefügtes Mitglied</span><span class="sxs-lookup"><span data-stu-id="76421-146">A member added</span></span>](#team-members-added)   | <span data-ttu-id="76421-147">Alle</span><span class="sxs-lookup"><span data-stu-id="76421-147">All</span></span> |
| <span data-ttu-id="76421-148">Entfernte Mitglieder</span><span class="sxs-lookup"><span data-stu-id="76421-148">members removed</span></span> | <span data-ttu-id="76421-149">membersRemoved</span><span class="sxs-lookup"><span data-stu-id="76421-149">membersRemoved</span></span> | <span data-ttu-id="76421-150">OnTeamsMembersRemovedAsync</span><span class="sxs-lookup"><span data-stu-id="76421-150">OnTeamsMembersRemovedAsync</span></span> | [<span data-ttu-id="76421-151">Ein Mitglied wurde entfernt</span><span class="sxs-lookup"><span data-stu-id="76421-151">A member was removed</span></span>](#team-members-removed) | <span data-ttu-id="76421-152">groupChat & Team</span><span class="sxs-lookup"><span data-stu-id="76421-152">groupChat & team</span></span> |
| <span data-ttu-id="76421-153">Team umbenannt</span><span class="sxs-lookup"><span data-stu-id="76421-153">team renamed</span></span>        | <span data-ttu-id="76421-154">teamRenamed</span><span class="sxs-lookup"><span data-stu-id="76421-154">teamRenamed</span></span>       | <span data-ttu-id="76421-155">OnTeamsTeamRenamedAsync</span><span class="sxs-lookup"><span data-stu-id="76421-155">OnTeamsTeamRenamedAsync</span></span>    | [<span data-ttu-id="76421-156">Ein Team wurde umbenannt</span><span class="sxs-lookup"><span data-stu-id="76421-156">A Team was renamed</span></span>](#team-renamed)       | <span data-ttu-id="76421-157">Team</span><span class="sxs-lookup"><span data-stu-id="76421-157">Team</span></span> |
| <span data-ttu-id="76421-158">Team gelöscht</span><span class="sxs-lookup"><span data-stu-id="76421-158">team deleted</span></span>        | <span data-ttu-id="76421-159">teamDeleted</span><span class="sxs-lookup"><span data-stu-id="76421-159">teamDeleted</span></span>       | <span data-ttu-id="76421-160">OnTeamsTeamDeletedAsync</span><span class="sxs-lookup"><span data-stu-id="76421-160">OnTeamsTeamDeletedAsync</span></span>    | [<span data-ttu-id="76421-161">Ein Team wurde gelöscht</span><span class="sxs-lookup"><span data-stu-id="76421-161">A Team was deleted</span></span>](#team-deleted)       | <span data-ttu-id="76421-162">Team</span><span class="sxs-lookup"><span data-stu-id="76421-162">Team</span></span> |
| <span data-ttu-id="76421-163">Team archiviert</span><span class="sxs-lookup"><span data-stu-id="76421-163">team archived</span></span>        | <span data-ttu-id="76421-164">teamArchived</span><span class="sxs-lookup"><span data-stu-id="76421-164">teamArchived</span></span>       | <span data-ttu-id="76421-165">OnTeamsTeamArchivedAsync</span><span class="sxs-lookup"><span data-stu-id="76421-165">OnTeamsTeamArchivedAsync</span></span>    | [<span data-ttu-id="76421-166">Ein Team wurde archiviert</span><span class="sxs-lookup"><span data-stu-id="76421-166">A Team was archived</span></span>](#team-archived)       | <span data-ttu-id="76421-167">Team</span><span class="sxs-lookup"><span data-stu-id="76421-167">Team</span></span> |
| <span data-ttu-id="76421-168">Team wird nicht archiviert</span><span class="sxs-lookup"><span data-stu-id="76421-168">team unarchived</span></span>        | <span data-ttu-id="76421-169">teamUnarchived</span><span class="sxs-lookup"><span data-stu-id="76421-169">teamUnarchived</span></span>       | <span data-ttu-id="76421-170">OnTeamsTeamUnarchivedAsync</span><span class="sxs-lookup"><span data-stu-id="76421-170">OnTeamsTeamUnarchivedAsync</span></span>    | [<span data-ttu-id="76421-171">Ein Team wurde nicht archiviert</span><span class="sxs-lookup"><span data-stu-id="76421-171">A Team was unarchived</span></span>](#team-unarchived)       | <span data-ttu-id="76421-172">Team</span><span class="sxs-lookup"><span data-stu-id="76421-172">Team</span></span> |
| <span data-ttu-id="76421-173">Team wiederhergestellt</span><span class="sxs-lookup"><span data-stu-id="76421-173">team restored</span></span>        | <span data-ttu-id="76421-174">teamRestored</span><span class="sxs-lookup"><span data-stu-id="76421-174">teamRestored</span></span>      | <span data-ttu-id="76421-175">OnTeamsTeamRestoredAsync</span><span class="sxs-lookup"><span data-stu-id="76421-175">OnTeamsTeamRestoredAsync</span></span>    | [<span data-ttu-id="76421-176">Ein Team wurde wiederhergestellt</span><span class="sxs-lookup"><span data-stu-id="76421-176">A Team was restored</span></span>](#team-restored)       | <span data-ttu-id="76421-177">Team</span><span class="sxs-lookup"><span data-stu-id="76421-177">Team</span></span> |

### <a name="channel-created"></a><span data-ttu-id="76421-178">Kanal erstellt</span><span class="sxs-lookup"><span data-stu-id="76421-178">Channel created</span></span>

<span data-ttu-id="76421-179">Das vom Kanal erstellte Ereignis wird an Ihren Bot gesendet, wenn ein neuer Kanal in einem Team erstellt wird, in dem Ihr Bot installiert ist.</span><span class="sxs-lookup"><span data-stu-id="76421-179">The channel created event is sent to your bot whenever a new channel is created in a team your bot is installed in.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="76421-180">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="76421-180">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelCreatedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the Channel created");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="76421-181">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="76421-181">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="76421-182">Json</span><span class="sxs-lookup"><span data-stu-id="76421-182">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="76421-183">Python</span><span class="sxs-lookup"><span data-stu-id="76421-183">Python</span></span>](#tab/python)

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

### <a name="channel-renamed"></a><span data-ttu-id="76421-184">Kanal umbenannt</span><span class="sxs-lookup"><span data-stu-id="76421-184">Channel renamed</span></span>

<span data-ttu-id="76421-185">Das umbenannte Kanalereignis wird an Ihren Bot gesendet, wenn ein Kanal in einem Team umbenannt wird, in dem Ihr Bot installiert ist.</span><span class="sxs-lookup"><span data-stu-id="76421-185">The channel renamed event is sent to your bot whenever a channel is renamed in a team your bot is installed in.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="76421-186">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="76421-186">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelRenamedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the new Channel name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="76421-187">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="76421-187">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="76421-188">Json</span><span class="sxs-lookup"><span data-stu-id="76421-188">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="76421-189">Python</span><span class="sxs-lookup"><span data-stu-id="76421-189">Python</span></span>](#tab/python)

```python
async def on_teams_channel_renamed(
    self, channel_info: ChannelInfo, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The new channel name is {channel_info.name}")
    )
```

* * *

### <a name="channel-deleted"></a><span data-ttu-id="76421-190">Kanal gelöscht</span><span class="sxs-lookup"><span data-stu-id="76421-190">Channel Deleted</span></span>

<span data-ttu-id="76421-191">Das Kanal gelöschte Ereignis wird an Ihren Bot gesendet, wenn ein Kanal in einem Team gelöscht wird, in dem Ihr Bot installiert ist.</span><span class="sxs-lookup"><span data-stu-id="76421-191">The channel deleted event is sent to your bot whenever a channel is deleted in a team your bot is installed in.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="76421-192">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="76421-192">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelDeletedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the Channel deleted");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="76421-193">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="76421-193">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="76421-194">Json</span><span class="sxs-lookup"><span data-stu-id="76421-194">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="76421-195">Python</span><span class="sxs-lookup"><span data-stu-id="76421-195">Python</span></span>](#tab/python)

```python
async def on_teams_channel_deleted(
    self, channel_info: ChannelInfo, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The deleted channel is {channel_info.name}")
    )
```

* * *

### <a name="channel-restored"></a><span data-ttu-id="76421-196">Kanal wiederhergestellt</span><span class="sxs-lookup"><span data-stu-id="76421-196">Channel restored</span></span>

<span data-ttu-id="76421-197">Das kanalwiederherstellende Ereignis wird an Ihren Bot gesendet, wenn ein kanal, der zuvor gelöscht wurde, in einem Team wiederhergestellt wird, in dem Ihr Bot bereits installiert ist.</span><span class="sxs-lookup"><span data-stu-id="76421-197">The channel restored event is sent to your bot whenever a channel that was previously deleted is restored in a team that your bot is already installed in.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="76421-198">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="76421-198">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelRestoredAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the Channel restored.");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="76421-199">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="76421-199">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="76421-200">Json</span><span class="sxs-lookup"><span data-stu-id="76421-200">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="76421-201">Python</span><span class="sxs-lookup"><span data-stu-id="76421-201">Python</span></span>](#tab/python)

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

### <a name="team-members-added"></a><span data-ttu-id="76421-202">Hinzugefügte Teammitglieder</span><span class="sxs-lookup"><span data-stu-id="76421-202">Team members added</span></span>

<span data-ttu-id="76421-203">Das Ereignis wird an Ihren Bot gesendet, wenn es zum ersten Mal zu einer Unterhaltung hinzugefügt wird und jedes Mal, wenn ein neuer Benutzer zu einem Team- oder Gruppenchat hinzugefügt wird, in dem Ihr Bot `teamMemberAdded` installiert ist.</span><span class="sxs-lookup"><span data-stu-id="76421-203">The `teamMemberAdded` event is sent to your bot the first time it is added to a conversation and every time a new user is added to a team or group chat that your bot is installed in.</span></span> <span data-ttu-id="76421-204">Die Benutzerinformationen (ID) sind für Ihren Bot eindeutig und können für die zukünftige Verwendung durch Ihren Dienst zwischengespeichert werden (z. B. senden einer Nachricht an einen bestimmten Benutzer).</span><span class="sxs-lookup"><span data-stu-id="76421-204">The user information (ID) is unique for your bot and can be cached for future use by your service (such as sending a message to a specific user).</span></span>

# <a name="cnet"></a>[<span data-ttu-id="76421-205">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="76421-205">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="76421-206">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="76421-206">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="76421-207">Json</span><span class="sxs-lookup"><span data-stu-id="76421-207">JSON</span></span>](#tab/json)

<span data-ttu-id="76421-208">Dies ist die Nachricht, die Ihr Bot erhält, wenn der Bot zu **einem Team hinzugefügt wird.**</span><span class="sxs-lookup"><span data-stu-id="76421-208">This is the message your bot will receive when the bot is added **to a team**.</span></span>

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

<span data-ttu-id="76421-209">Dies ist die Nachricht, die Ihr Bot erhält, wenn der Bot zu einem *1:1-Chat* hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="76421-209">This is the message your bot will receive when the bot is added \**to a one-to-one chat*.</span></span>

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
    "aadObjectId": "***"
  },
  "conversation": {
    "conversationType": "personal",
    "id": "***"
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

# <a name="python"></a>[<span data-ttu-id="76421-210">Python</span><span class="sxs-lookup"><span data-stu-id="76421-210">Python</span></span>](#tab/python)

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

* * *

### <a name="team-members-removed"></a><span data-ttu-id="76421-211">Entfernte Teammitglieder</span><span class="sxs-lookup"><span data-stu-id="76421-211">Team members removed</span></span>

<span data-ttu-id="76421-212">Das Ereignis wird an Ihren Bot gesendet, wenn es aus einem Team entfernt wird und jedes Mal, wenn ein Benutzer aus einem Team entfernt wird, in dem Ihr Bot `teamMemberRemoved` Mitglied ist.</span><span class="sxs-lookup"><span data-stu-id="76421-212">The `teamMemberRemoved` event is sent to your bot if it is removed from a team and every time any user is removed from a team that your bot is a member of.</span></span> <span data-ttu-id="76421-213">Sie können ermitteln, ob das entfernte neue Mitglied der Bot selbst oder ein Benutzer war, indem Sie sich das `Activity` Objekt des anschauen. `turnContext`</span><span class="sxs-lookup"><span data-stu-id="76421-213">You can determine if the new member removed was the bot itself or a user by looking at the `Activity` object of the `turnContext`.</span></span>  <span data-ttu-id="76421-214">Wenn das Feld des Objekts mit dem Feld des Objekts identisch ist, ist das entfernte Element der Bot, andernfalls handelt es sich `Id` `MembersRemoved` um einen `Id` `Recipient` Benutzer.</span><span class="sxs-lookup"><span data-stu-id="76421-214">If the `Id` field of the `MembersRemoved` object is the same as the `Id` field of the `Recipient` object, then the member removed is the bot, otherwise, it is a user.</span></span>  <span data-ttu-id="76421-215">Die Bots `Id` sind in der Regel: `28:<MicrosoftAppId>`</span><span class="sxs-lookup"><span data-stu-id="76421-215">The bot's `Id` will generally be: `28:<MicrosoftAppId>`</span></span>

[!Note] <span data-ttu-id="76421-216">Wenn ein Benutzer dauerhaft aus einem Mandanten gelöscht wird, `membersRemoved conversationUpdate` wird das Ereignis ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="76421-216">When a user is permanently deleted from a tenant, `membersRemoved conversationUpdate` event is triggered.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="76421-217">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="76421-217">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="76421-218">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="76421-218">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="76421-219">Json</span><span class="sxs-lookup"><span data-stu-id="76421-219">JSON</span></span>](#tab/json)

<span data-ttu-id="76421-220">Das Objekt im folgenden Nutzlastbeispiel basiert auf dem Hinzufügen eines Mitglieds zu einem Team anstelle eines Gruppenchats oder dem Initiieren einer neuen `channelData` 1:1-Unterhaltung:</span><span class="sxs-lookup"><span data-stu-id="76421-220">The `channelData` object in the following payload example is based on adding a member to a team rather than a group chat, or initiating a new one-to-one conversation:</span></span>

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


# <a name="python"></a>[<span data-ttu-id="76421-221">Python</span><span class="sxs-lookup"><span data-stu-id="76421-221">Python</span></span>](#tab/python)

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

### <a name="team-renamed"></a><span data-ttu-id="76421-222">Team umbenannt</span><span class="sxs-lookup"><span data-stu-id="76421-222">Team renamed</span></span>

<span data-ttu-id="76421-223">Ihr Bot wird benachrichtigt, wenn das Team, in dem er sich befindet, umbenannt wurde.</span><span class="sxs-lookup"><span data-stu-id="76421-223">Your bot is notified when the team it is in has been renamed.</span></span> <span data-ttu-id="76421-224">Es empfängt ein `conversationUpdate` Ereignis mit `eventType.teamRenamed` im `channelData` Objekt.</span><span class="sxs-lookup"><span data-stu-id="76421-224">It receives a `conversationUpdate` event with `eventType.teamRenamed` in the `channelData` object.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="76421-225">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="76421-225">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamRenamedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the new Team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="76421-226">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="76421-226">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="76421-227">Json</span><span class="sxs-lookup"><span data-stu-id="76421-227">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="76421-228">Python</span><span class="sxs-lookup"><span data-stu-id="76421-228">Python</span></span>](#tab/python)

```python
async def on_teams_team_renamed(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The new team name is {team_info.name}")
    )
```

* * *

### <a name="team-deleted"></a><span data-ttu-id="76421-229">Team gelöscht</span><span class="sxs-lookup"><span data-stu-id="76421-229">Team deleted</span></span>

<span data-ttu-id="76421-230">Ihr Bot wird benachrichtigt, wenn das Team, in dem er sich befindet, gelöscht wurde.</span><span class="sxs-lookup"><span data-stu-id="76421-230">Your bot is notified when the team it is in has been deleted.</span></span> <span data-ttu-id="76421-231">Es empfängt ein `conversationUpdate` Ereignis mit `eventType.teamDeleted` im `channelData` Objekt.</span><span class="sxs-lookup"><span data-stu-id="76421-231">It receives a `conversationUpdate` event with `eventType.teamDeleted` in the `channelData` object.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="76421-232">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="76421-232">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamDeletedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    //handle delete event
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="76421-233">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="76421-233">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="76421-234">Json</span><span class="sxs-lookup"><span data-stu-id="76421-234">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="76421-235">Python</span><span class="sxs-lookup"><span data-stu-id="76421-235">Python</span></span>](#tab/python)

```python
async def on_teams_team_deleted(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    //handle delete event
    )
```

* * *

### <a name="team-restored"></a><span data-ttu-id="76421-236">Team wiederhergestellt</span><span class="sxs-lookup"><span data-stu-id="76421-236">Team restored</span></span>

<span data-ttu-id="76421-237">Der Bot erhält eine Benachrichtigung, wenn das Team nach dem Löschen wiederhergestellt wird.</span><span class="sxs-lookup"><span data-stu-id="76421-237">The bot receives a notification when the team is restored from deletion.</span></span> <span data-ttu-id="76421-238">Der Bot empfängt `conversationUpdate` ein Ereignis mit im `eventType.teamrestored` `channelData` Objekt.</span><span class="sxs-lookup"><span data-stu-id="76421-238">The bot receives a `conversationUpdate` event with `eventType.teamrestored` in the `channelData` object.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="76421-239">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="76421-239">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamrestoredAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="76421-240">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="76421-240">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="76421-241">Json</span><span class="sxs-lookup"><span data-stu-id="76421-241">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="76421-242">Python</span><span class="sxs-lookup"><span data-stu-id="76421-242">Python</span></span>](#tab/python)

```python
async def on_teams_team_restored(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The team name is {team_info.name}")
    )
```

* * *

### <a name="team-archived"></a><span data-ttu-id="76421-243">Team archiviert</span><span class="sxs-lookup"><span data-stu-id="76421-243">Team archived</span></span>

<span data-ttu-id="76421-244">Der Bot empfängt eine Benachrichtigung, wenn das Team archiviert wird, in dem er installiert ist.</span><span class="sxs-lookup"><span data-stu-id="76421-244">The bot receives a notification when the team it is installed in is archived.</span></span> <span data-ttu-id="76421-245">Es empfängt ein `conversationUpdate` Ereignis mit `eventType.teamarchived` im `channelData` Objekt.</span><span class="sxs-lookup"><span data-stu-id="76421-245">It receives a `conversationUpdate` event with `eventType.teamarchived` in the `channelData` object.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="76421-246">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="76421-246">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamArchivedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="76421-247">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="76421-247">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="76421-248">Json</span><span class="sxs-lookup"><span data-stu-id="76421-248">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="76421-249">Python</span><span class="sxs-lookup"><span data-stu-id="76421-249">Python</span></span>](#tab/python)

```python
async def on_teams_team_archived(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The team name is {team_info.name}")
    )
```

* * *


### <a name="team-unarchived"></a><span data-ttu-id="76421-250">Team wird nicht archiviert</span><span class="sxs-lookup"><span data-stu-id="76421-250">Team unarchived</span></span>

<span data-ttu-id="76421-251">Der Bot empfängt eine Benachrichtigung, wenn das Team, in dem er installiert ist, nicht archiviert ist.</span><span class="sxs-lookup"><span data-stu-id="76421-251">The bot receives a notification when the team it is installed in is unarchived.</span></span> <span data-ttu-id="76421-252">Es empfängt ein `conversationUpdate` Ereignis mit `eventType.teamUnarchived` im `channelData` Objekt.</span><span class="sxs-lookup"><span data-stu-id="76421-252">It receives a `conversationUpdate` event with `eventType.teamUnarchived` in the `channelData` object.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="76421-253">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="76421-253">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamUnarchivedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="76421-254">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="76421-254">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="76421-255">Json</span><span class="sxs-lookup"><span data-stu-id="76421-255">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="76421-256">Python</span><span class="sxs-lookup"><span data-stu-id="76421-256">Python</span></span>](#tab/python)

```python
async def on_teams_team_unarchived(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The team name is {team_info.name}")
    )
```

* * *

## <a name="message-reaction-events"></a><span data-ttu-id="76421-257">Nachrichtenreaktionsereignisse</span><span class="sxs-lookup"><span data-stu-id="76421-257">Message reaction events</span></span>

<span data-ttu-id="76421-258">Das Ereignis wird gesendet, wenn ein Benutzer Reaktionen auf eine Nachricht hinzufügt oder entfernt, die von Ihrem `messageReaction` Bot gesendet wurde.</span><span class="sxs-lookup"><span data-stu-id="76421-258">The `messageReaction` event is sent when a user adds or removes reactions to a message which was sent by your bot.</span></span> <span data-ttu-id="76421-259">Der enthält die ID der bestimmten Nachricht, und die ist die Art der Reaktion `replyToId` im `Type` Textformat.</span><span class="sxs-lookup"><span data-stu-id="76421-259">The `replyToId` contains the ID of the specific message, and the `Type` is the type of reaction in text format.</span></span>  <span data-ttu-id="76421-260">Die Reaktionstypen sind: "verärgert", "herz", "heiter", "gefällt mir", "Sad", "überrascht".</span><span class="sxs-lookup"><span data-stu-id="76421-260">The types of reactions include: "angry", "heart", "laugh", "like", "Sad", "surprised".</span></span> <span data-ttu-id="76421-261">Dieses Ereignis enthält nicht den Inhalt der ursprünglichen Nachricht. Wenn also die Verarbeitung von Reaktionen auf Ihre Nachrichten für Ihren Bot wichtig ist, müssen Sie die Nachrichten speichern, wenn Sie sie senden.</span><span class="sxs-lookup"><span data-stu-id="76421-261">This event does not contain the contents of the original message, so if processing reactions to your messages is important for your bot you'll need to store the messages when you send them.</span></span>

| <span data-ttu-id="76421-262">EventType</span><span class="sxs-lookup"><span data-stu-id="76421-262">EventType</span></span>       | <span data-ttu-id="76421-263">Payload-Objekt</span><span class="sxs-lookup"><span data-stu-id="76421-263">Payload object</span></span>   | <span data-ttu-id="76421-264">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="76421-264">Description</span></span>                                                             | <span data-ttu-id="76421-265">Bereich</span><span class="sxs-lookup"><span data-stu-id="76421-265">Scope</span></span> |
| --------------- | ---------------- | ----------------------------------------------------------------------- | ----- |
| <span data-ttu-id="76421-266">messageReaction</span><span class="sxs-lookup"><span data-stu-id="76421-266">messageReaction</span></span> | <span data-ttu-id="76421-267">reactionsAdded</span><span class="sxs-lookup"><span data-stu-id="76421-267">reactionsAdded</span></span>   | [<span data-ttu-id="76421-268">Reaktion auf Botnachricht</span><span class="sxs-lookup"><span data-stu-id="76421-268">Reaction to bot message</span></span>](#reactions-to-a-bot-message)                   | <span data-ttu-id="76421-269">Alle</span><span class="sxs-lookup"><span data-stu-id="76421-269">All</span></span>   |
| <span data-ttu-id="76421-270">messageReaction</span><span class="sxs-lookup"><span data-stu-id="76421-270">messageReaction</span></span> | <span data-ttu-id="76421-271">reactionsRemoved</span><span class="sxs-lookup"><span data-stu-id="76421-271">reactionsRemoved</span></span> | [<span data-ttu-id="76421-272">Reaktion aus Botnachricht entfernt</span><span class="sxs-lookup"><span data-stu-id="76421-272">Reaction removed from bot message</span></span>](#reactions-removed-from-bot-message) | <span data-ttu-id="76421-273">Alle</span><span class="sxs-lookup"><span data-stu-id="76421-273">All</span></span>   |

### <a name="reactions-to-a-bot-message"></a><span data-ttu-id="76421-274">Reaktionen auf eine Botnachricht</span><span class="sxs-lookup"><span data-stu-id="76421-274">Reactions to a bot message</span></span>

# <a name="cnet"></a>[<span data-ttu-id="76421-275">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="76421-275">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="76421-276">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="76421-276">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="76421-277">Json</span><span class="sxs-lookup"><span data-stu-id="76421-277">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="76421-278">Python</span><span class="sxs-lookup"><span data-stu-id="76421-278">Python</span></span>](#tab/python)

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

### <a name="reactions-removed-from-bot-message"></a><span data-ttu-id="76421-279">Aus bot-Nachricht entfernte Reaktionen</span><span class="sxs-lookup"><span data-stu-id="76421-279">Reactions removed from bot message</span></span>

# <a name="cnet"></a>[<span data-ttu-id="76421-280">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="76421-280">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="76421-281">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="76421-281">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="76421-282">Json</span><span class="sxs-lookup"><span data-stu-id="76421-282">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="76421-283">Python</span><span class="sxs-lookup"><span data-stu-id="76421-283">Python</span></span>](#tab/python)

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

## <a name="samples"></a><span data-ttu-id="76421-284">Beispiele</span><span class="sxs-lookup"><span data-stu-id="76421-284">Samples</span></span>

<span data-ttu-id="76421-285">Beispielcode, der die Bots-Unterhaltungsereignisse zeigt, finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="76421-285">For sample code showing the bots conversation events, see:</span></span>

[<span data-ttu-id="76421-286">Beispiel für Unterhaltungsereignisse in Microsoft Teams bots</span><span class="sxs-lookup"><span data-stu-id="76421-286">Microsoft Teams bots conversation events sample</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot)



