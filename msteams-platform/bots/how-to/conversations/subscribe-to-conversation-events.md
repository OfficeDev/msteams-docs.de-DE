---
title: Unterhaltungsereignisse
author: WashingtonKayaker
description: So arbeiten Sie mit Unterhaltungsereignissen aus Ihrem Microsoft Teams-Bot.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: af06dba58b3784a03dbcbbc627fa38fce681eeb8
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696346"
---
# <a name="conversation-events-in-your-teams-bot"></a><span data-ttu-id="80262-103">Unterhaltungsereignisse in Ihrem Teams-Bot</span><span class="sxs-lookup"><span data-stu-id="80262-103">Conversation events in your Teams bot</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="80262-104">Beim Erstellen Ihrer Unterhaltungsbots für Microsoft Teams können Sie mit Unterhaltungsereignissen arbeiten.</span><span class="sxs-lookup"><span data-stu-id="80262-104">When building your conversational bots for Microsoft Teams, you can work with conversation events.</span></span> <span data-ttu-id="80262-105">Teams sendet Benachrichtigungen an Ihren Bot für Unterhaltungsereignisse, die in Bereiche auftreten, in denen Ihr Bot aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="80262-105">Teams sends notifications to your bot for conversation events that happen in scopes where your bot is active.</span></span> <span data-ttu-id="80262-106">Sie können diese Ereignisse in Ihrem Code erfassen und die folgenden Aktionen ausführen:</span><span class="sxs-lookup"><span data-stu-id="80262-106">You can capture these events in your code and take the following actions:</span></span>

* <span data-ttu-id="80262-107">Auslösen einer Willkommensnachricht, wenn Ihr Bot einem Team hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="80262-107">Trigger a welcome message when your bot is added to a team.</span></span>
* <span data-ttu-id="80262-108">Auslösen einer Willkommensnachricht, wenn ein neues Teammitglied hinzugefügt oder entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="80262-108">Trigger a welcome message when a new team member is added or removed.</span></span>
* <span data-ttu-id="80262-109">Auslösen einer Benachrichtigung, wenn ein Kanal erstellt, umbenannt oder gelöscht wird.</span><span class="sxs-lookup"><span data-stu-id="80262-109">Trigger a notification when a channel is created, renamed, or deleted.</span></span>
* <span data-ttu-id="80262-110">Wenn eine Botnachricht von einem Benutzer gemocht wird.</span><span class="sxs-lookup"><span data-stu-id="80262-110">When a bot message is liked by a user.</span></span>

## <a name="conversation-update-events"></a><span data-ttu-id="80262-111">Aktualisierungsereignisse in Unterhaltungen</span><span class="sxs-lookup"><span data-stu-id="80262-111">Conversation update events</span></span>

<span data-ttu-id="80262-112">Sie können Unterhaltungsupdateereignisse verwenden, um bessere Benachrichtigungen und effektivere Botaktionen zu bieten.</span><span class="sxs-lookup"><span data-stu-id="80262-112">You can use conversation update events to provide better notifications and more effective bot actions.</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="80262-113">Sie können jederzeit neue Ereignisse hinzufügen, und Ihr Bot beginnt, sie zu empfangen.</span><span class="sxs-lookup"><span data-stu-id="80262-113">You can add new events any time and your bot begins to receive them.</span></span>
> * <span data-ttu-id="80262-114">Sie müssen Ihren Bot so entwerfen, dass unerwartete Ereignisse empfangen werden.</span><span class="sxs-lookup"><span data-stu-id="80262-114">You must design your bot to receive unexpected events.</span></span>
> * <span data-ttu-id="80262-115">Wenn Sie das Bot Framework SDK verwenden, antwortet Ihr Bot automatisch mit einem auf Ereignisse, die `200 - OK` Sie nicht behandeln möchten.</span><span class="sxs-lookup"><span data-stu-id="80262-115">If you are using the Bot Framework SDK, your bot automatically responds with a `200 - OK` to any events you choose not to handle.</span></span>

<span data-ttu-id="80262-116">Ein Bot empfängt `conversationUpdate` in einem der folgenden Fälle ein Ereignis:</span><span class="sxs-lookup"><span data-stu-id="80262-116">A bot receives a `conversationUpdate` event in either of the following cases:</span></span>

* <span data-ttu-id="80262-117">Wenn bot zu einer Unterhaltung hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="80262-117">When bot has been added to a conversation.</span></span>
* <span data-ttu-id="80262-118">Andere Mitglieder werden einer Unterhaltung hinzugefügt oder aus ihr entfernt.</span><span class="sxs-lookup"><span data-stu-id="80262-118">Other members are added to or removed from a conversation.</span></span>
* <span data-ttu-id="80262-119">Unterhaltungsmetadaten haben sich geändert.</span><span class="sxs-lookup"><span data-stu-id="80262-119">Conversation metadata has changed.</span></span>

<span data-ttu-id="80262-120">Das `conversationUpdate`-Ereignis wird an Ihren Bot gesendet, wenn er Informationen zu Mitgliedschaftsaktualisierungen für Teams empfängt, denen er hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="80262-120">The `conversationUpdate` event is sent to your bot when it receives information on membership updates for teams where it has been added.</span></span> <span data-ttu-id="80262-121">Es erhält auch ein Update, wenn es zum ersten Mal für persönliche Unterhaltungen hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="80262-121">It also receives an update when it has been added for the first time for personal conversations.</span></span>

<span data-ttu-id="80262-122">Die folgende Tabelle enthält eine Liste der Ereignisse für Das Aktualisieren von Teams-Unterhaltungen mit weiteren Details:</span><span class="sxs-lookup"><span data-stu-id="80262-122">The following table shows a list of Teams conversation update events with more details:</span></span>

| <span data-ttu-id="80262-123">Ergriffene Aktion</span><span class="sxs-lookup"><span data-stu-id="80262-123">Action taken</span></span>        | <span data-ttu-id="80262-124">EventType</span><span class="sxs-lookup"><span data-stu-id="80262-124">EventType</span></span>         | <span data-ttu-id="80262-125">Methode aufgerufen</span><span class="sxs-lookup"><span data-stu-id="80262-125">Method called</span></span>              | <span data-ttu-id="80262-126">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="80262-126">Description</span></span>                | <span data-ttu-id="80262-127">Bereich</span><span class="sxs-lookup"><span data-stu-id="80262-127">Scope</span></span> |
| ------------------- | ----------------- | -------------------------- | -------------------------- | ----- |
| <span data-ttu-id="80262-128">Kanal erstellt</span><span class="sxs-lookup"><span data-stu-id="80262-128">Channel created</span></span>     | <span data-ttu-id="80262-129">channelCreated</span><span class="sxs-lookup"><span data-stu-id="80262-129">channelCreated</span></span>    | <span data-ttu-id="80262-130">OnTeamsChannelCreatedAsync</span><span class="sxs-lookup"><span data-stu-id="80262-130">OnTeamsChannelCreatedAsync</span></span> | <span data-ttu-id="80262-131">[Ein Kanal wird erstellt.](#channel-created)</span><span class="sxs-lookup"><span data-stu-id="80262-131">[A channel is created](#channel-created).</span></span> | <span data-ttu-id="80262-132">Team</span><span class="sxs-lookup"><span data-stu-id="80262-132">Team</span></span> |
| <span data-ttu-id="80262-133">Kanal umbenannt</span><span class="sxs-lookup"><span data-stu-id="80262-133">Channel renamed</span></span>     | <span data-ttu-id="80262-134">channelRenamed</span><span class="sxs-lookup"><span data-stu-id="80262-134">channelRenamed</span></span>    | <span data-ttu-id="80262-135">OnTeamsChannelRenamedAsync</span><span class="sxs-lookup"><span data-stu-id="80262-135">OnTeamsChannelRenamedAsync</span></span> | <span data-ttu-id="80262-136">[Ein Kanal wird umbenannt.](#channel-renamed)</span><span class="sxs-lookup"><span data-stu-id="80262-136">[A channel is renamed](#channel-renamed).</span></span> | <span data-ttu-id="80262-137">Team</span><span class="sxs-lookup"><span data-stu-id="80262-137">Team</span></span> |
| <span data-ttu-id="80262-138">Kanal gelöscht</span><span class="sxs-lookup"><span data-stu-id="80262-138">Channel deleted</span></span>     | <span data-ttu-id="80262-139">channelDeleted</span><span class="sxs-lookup"><span data-stu-id="80262-139">channelDeleted</span></span>    | <span data-ttu-id="80262-140">OnTeamsChannelDeletedAsync</span><span class="sxs-lookup"><span data-stu-id="80262-140">OnTeamsChannelDeletedAsync</span></span> | <span data-ttu-id="80262-141">[Ein Kanal wird gelöscht.](#channel-deleted)</span><span class="sxs-lookup"><span data-stu-id="80262-141">[A channel is deleted](#channel-deleted).</span></span> | <span data-ttu-id="80262-142">Team</span><span class="sxs-lookup"><span data-stu-id="80262-142">Team</span></span> |
| <span data-ttu-id="80262-143">Kanal wiederhergestellt</span><span class="sxs-lookup"><span data-stu-id="80262-143">Channel restored</span></span>    | <span data-ttu-id="80262-144">channelRestored</span><span class="sxs-lookup"><span data-stu-id="80262-144">channelRestored</span></span>    | <span data-ttu-id="80262-145">OnTeamsChannelRestoredAsync</span><span class="sxs-lookup"><span data-stu-id="80262-145">OnTeamsChannelRestoredAsync</span></span> | <span data-ttu-id="80262-146">[Ein Kanal wird wiederhergestellt.](#channel-deleted)</span><span class="sxs-lookup"><span data-stu-id="80262-146">[A channel is restored](#channel-deleted).</span></span> | <span data-ttu-id="80262-147">Team</span><span class="sxs-lookup"><span data-stu-id="80262-147">Team</span></span> |
| <span data-ttu-id="80262-148">Hinzugefügte Mitglieder</span><span class="sxs-lookup"><span data-stu-id="80262-148">Members added</span></span>   | <span data-ttu-id="80262-149">membersAdded</span><span class="sxs-lookup"><span data-stu-id="80262-149">membersAdded</span></span>   | <span data-ttu-id="80262-150">OnTeamsMembersAddedAsync</span><span class="sxs-lookup"><span data-stu-id="80262-150">OnTeamsMembersAddedAsync</span></span>   | <span data-ttu-id="80262-151">[Ein Element wird hinzugefügt.](#team-members-added)</span><span class="sxs-lookup"><span data-stu-id="80262-151">[A member is added](#team-members-added).</span></span> | <span data-ttu-id="80262-152">Alle</span><span class="sxs-lookup"><span data-stu-id="80262-152">All</span></span> |
| <span data-ttu-id="80262-153">Entfernte Mitglieder</span><span class="sxs-lookup"><span data-stu-id="80262-153">Members removed</span></span> | <span data-ttu-id="80262-154">membersRemoved</span><span class="sxs-lookup"><span data-stu-id="80262-154">membersRemoved</span></span> | <span data-ttu-id="80262-155">OnTeamsMembersRemovedAsync</span><span class="sxs-lookup"><span data-stu-id="80262-155">OnTeamsMembersRemovedAsync</span></span> | <span data-ttu-id="80262-156">[Ein Element wird entfernt.](#team-members-removed)</span><span class="sxs-lookup"><span data-stu-id="80262-156">[A member is removed](#team-members-removed).</span></span> | <span data-ttu-id="80262-157">groupChat und Team</span><span class="sxs-lookup"><span data-stu-id="80262-157">groupChat and team</span></span> |
| <span data-ttu-id="80262-158">Team umbenannt</span><span class="sxs-lookup"><span data-stu-id="80262-158">Team renamed</span></span>        | <span data-ttu-id="80262-159">teamRenamed</span><span class="sxs-lookup"><span data-stu-id="80262-159">teamRenamed</span></span>       | <span data-ttu-id="80262-160">OnTeamsTeamRenamedAsync</span><span class="sxs-lookup"><span data-stu-id="80262-160">OnTeamsTeamRenamedAsync</span></span>    | <span data-ttu-id="80262-161">[Ein Team wird umbenannt.](#team-renamed)</span><span class="sxs-lookup"><span data-stu-id="80262-161">[A team is renamed](#team-renamed).</span></span>       | <span data-ttu-id="80262-162">Team</span><span class="sxs-lookup"><span data-stu-id="80262-162">Team</span></span> |
| <span data-ttu-id="80262-163">Team gelöscht</span><span class="sxs-lookup"><span data-stu-id="80262-163">Team deleted</span></span>        | <span data-ttu-id="80262-164">teamDeleted</span><span class="sxs-lookup"><span data-stu-id="80262-164">teamDeleted</span></span>       | <span data-ttu-id="80262-165">OnTeamsTeamDeletedAsync</span><span class="sxs-lookup"><span data-stu-id="80262-165">OnTeamsTeamDeletedAsync</span></span>    | <span data-ttu-id="80262-166">[Ein Team wird gelöscht.](#team-deleted)</span><span class="sxs-lookup"><span data-stu-id="80262-166">[A team is deleted](#team-deleted).</span></span>       | <span data-ttu-id="80262-167">Team</span><span class="sxs-lookup"><span data-stu-id="80262-167">Team</span></span> |
| <span data-ttu-id="80262-168">Team archiviert</span><span class="sxs-lookup"><span data-stu-id="80262-168">Team archived</span></span>        | <span data-ttu-id="80262-169">teamArchived</span><span class="sxs-lookup"><span data-stu-id="80262-169">teamArchived</span></span>       | <span data-ttu-id="80262-170">OnTeamsTeamArchivedAsync</span><span class="sxs-lookup"><span data-stu-id="80262-170">OnTeamsTeamArchivedAsync</span></span>    | <span data-ttu-id="80262-171">[Ein Team wird archiviert.](#team-archived)</span><span class="sxs-lookup"><span data-stu-id="80262-171">[A team is archived](#team-archived).</span></span>       | <span data-ttu-id="80262-172">Team</span><span class="sxs-lookup"><span data-stu-id="80262-172">Team</span></span> |
| <span data-ttu-id="80262-173">Team wird nicht archiviert</span><span class="sxs-lookup"><span data-stu-id="80262-173">Team unarchived</span></span>        | <span data-ttu-id="80262-174">teamUnarchived</span><span class="sxs-lookup"><span data-stu-id="80262-174">teamUnarchived</span></span>       | <span data-ttu-id="80262-175">OnTeamsTeamUnarchivedAsync</span><span class="sxs-lookup"><span data-stu-id="80262-175">OnTeamsTeamUnarchivedAsync</span></span>    | <span data-ttu-id="80262-176">[Ein Team wird nicht archiviert.](#team-unarchived)</span><span class="sxs-lookup"><span data-stu-id="80262-176">[A team is unarchived](#team-unarchived).</span></span>       | <span data-ttu-id="80262-177">Team</span><span class="sxs-lookup"><span data-stu-id="80262-177">Team</span></span> |
| <span data-ttu-id="80262-178">Team wiederhergestellt</span><span class="sxs-lookup"><span data-stu-id="80262-178">Team restored</span></span>        | <span data-ttu-id="80262-179">teamRestored</span><span class="sxs-lookup"><span data-stu-id="80262-179">teamRestored</span></span>      | <span data-ttu-id="80262-180">OnTeamsTeamRestoredAsync</span><span class="sxs-lookup"><span data-stu-id="80262-180">OnTeamsTeamRestoredAsync</span></span>    | [<span data-ttu-id="80262-181">Ein Team wird wiederhergestellt</span><span class="sxs-lookup"><span data-stu-id="80262-181">A team is restored</span></span>](#team-restored)       | <span data-ttu-id="80262-182">Team</span><span class="sxs-lookup"><span data-stu-id="80262-182">Team</span></span> |

### <a name="channel-created"></a><span data-ttu-id="80262-183">Kanal erstellt</span><span class="sxs-lookup"><span data-stu-id="80262-183">Channel created</span></span>

<span data-ttu-id="80262-184">Das vom Kanal erstellte Ereignis wird an Ihren Bot gesendet, wenn ein neuer Kanal in einem Team erstellt wird, in dem Ihr Bot installiert ist.</span><span class="sxs-lookup"><span data-stu-id="80262-184">The channel created event is sent to your bot whenever a new channel is created in a team where your bot is installed.</span></span>

<span data-ttu-id="80262-185">Der folgende Code zeigt ein Beispiel für ein Kanalereignis, das erstellt wurde:</span><span class="sxs-lookup"><span data-stu-id="80262-185">The following code shows an example of channel created event:</span></span>

# <a name="c"></a>[<span data-ttu-id="80262-186">C#</span><span class="sxs-lookup"><span data-stu-id="80262-186">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelCreatedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the Channel created");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescript"></a>[<span data-ttu-id="80262-187">TypeScript</span><span class="sxs-lookup"><span data-stu-id="80262-187">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="80262-188">Json</span><span class="sxs-lookup"><span data-stu-id="80262-188">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="80262-189">Python</span><span class="sxs-lookup"><span data-stu-id="80262-189">Python</span></span>](#tab/python)

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

### <a name="channel-renamed"></a><span data-ttu-id="80262-190">Kanal umbenannt</span><span class="sxs-lookup"><span data-stu-id="80262-190">Channel renamed</span></span>

<span data-ttu-id="80262-191">Das umbenannte Kanalereignis wird an Ihren Bot gesendet, wenn ein Kanal in einem Team umbenannt wird, in dem Ihr Bot installiert ist.</span><span class="sxs-lookup"><span data-stu-id="80262-191">The channel renamed event is sent to your bot whenever a channel is renamed in a team where your bot is installed.</span></span>

<span data-ttu-id="80262-192">Der folgende Code zeigt ein Beispiel für ein kanalbenenntes Ereignis:</span><span class="sxs-lookup"><span data-stu-id="80262-192">The following code shows an example of channel renamed event:</span></span>

# <a name="c"></a>[<span data-ttu-id="80262-193">C#</span><span class="sxs-lookup"><span data-stu-id="80262-193">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelRenamedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the new Channel name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescript"></a>[<span data-ttu-id="80262-194">TypeScript</span><span class="sxs-lookup"><span data-stu-id="80262-194">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="80262-195">Json</span><span class="sxs-lookup"><span data-stu-id="80262-195">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="80262-196">Python</span><span class="sxs-lookup"><span data-stu-id="80262-196">Python</span></span>](#tab/python)

```python
async def on_teams_channel_renamed(
    self, channel_info: ChannelInfo, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The new channel name is {channel_info.name}")
    )
```

* * *

### <a name="channel-deleted"></a><span data-ttu-id="80262-197">Kanal gelöscht</span><span class="sxs-lookup"><span data-stu-id="80262-197">Channel deleted</span></span>

<span data-ttu-id="80262-198">Das Kanal gelöschte Ereignis wird an Ihren Bot gesendet, wenn ein Kanal in einem Team gelöscht wird, in dem Ihr Bot installiert ist.</span><span class="sxs-lookup"><span data-stu-id="80262-198">The channel deleted event is sent to your bot whenever a channel is deleted in a team where your bot is installed.</span></span>

<span data-ttu-id="80262-199">Der folgende Code zeigt ein Beispiel für ein kanal gelöschtes Ereignis:</span><span class="sxs-lookup"><span data-stu-id="80262-199">The following code shows an example of channel deleted event:</span></span>

# <a name="c"></a>[<span data-ttu-id="80262-200">C#</span><span class="sxs-lookup"><span data-stu-id="80262-200">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelDeletedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the Channel deleted");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescript"></a>[<span data-ttu-id="80262-201">TypeScript</span><span class="sxs-lookup"><span data-stu-id="80262-201">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="80262-202">Json</span><span class="sxs-lookup"><span data-stu-id="80262-202">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="80262-203">Python</span><span class="sxs-lookup"><span data-stu-id="80262-203">Python</span></span>](#tab/python)

```python
async def on_teams_channel_deleted(
    self, channel_info: ChannelInfo, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The deleted channel is {channel_info.name}")
    )
```

* * *

### <a name="channel-restored"></a><span data-ttu-id="80262-204">Kanal wiederhergestellt</span><span class="sxs-lookup"><span data-stu-id="80262-204">Channel restored</span></span>

<span data-ttu-id="80262-205">Das kanalwiederherstellende Ereignis wird an Ihren Bot gesendet, wenn ein kanal, der zuvor gelöscht wurde, in einem Team wiederhergestellt wird, in dem Ihr Bot bereits installiert ist.</span><span class="sxs-lookup"><span data-stu-id="80262-205">The channel restored event is sent to your bot whenever a channel that was previously deleted is restored in a team where your bot is already installed.</span></span>

<span data-ttu-id="80262-206">Der folgende Code zeigt ein Beispiel für das wiederhergestellte Kanalereignis:</span><span class="sxs-lookup"><span data-stu-id="80262-206">The following code shows an example of channel restored event:</span></span>

# <a name="c"></a>[<span data-ttu-id="80262-207">C#</span><span class="sxs-lookup"><span data-stu-id="80262-207">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelRestoredAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the Channel restored.");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescript"></a>[<span data-ttu-id="80262-208">TypeScript</span><span class="sxs-lookup"><span data-stu-id="80262-208">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="80262-209">Json</span><span class="sxs-lookup"><span data-stu-id="80262-209">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="80262-210">Python</span><span class="sxs-lookup"><span data-stu-id="80262-210">Python</span></span>](#tab/python)

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

### <a name="team-members-added"></a><span data-ttu-id="80262-211">Hinzugefügte Teammitglieder</span><span class="sxs-lookup"><span data-stu-id="80262-211">Team members added</span></span>

<span data-ttu-id="80262-212">Das `teamMemberAdded` Ereignis wird an Ihren Bot gesendet, wenn es zum ersten Mal einer Unterhaltung hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="80262-212">The `teamMemberAdded` event is sent to your bot the first time it is added to a conversation.</span></span> <span data-ttu-id="80262-213">Das Ereignis wird jedes Mal an Ihren Bot gesendet, wenn einem Team- oder Gruppenchat, in dem Ihr Bot installiert ist, ein neuer Benutzer hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="80262-213">The event is sent to your bot every time a new user is added to a team or group chat where your bot is installed.</span></span> <span data-ttu-id="80262-214">Die Benutzerinformationen, die ID sind, sind für Ihren Bot eindeutig und können für die zukünftige Verwendung durch Ihren Dienst zwischengespeichert werden, z. B. das Senden einer Nachricht an einen bestimmten Benutzer.</span><span class="sxs-lookup"><span data-stu-id="80262-214">The user information that is ID is unique for your bot and can be cached for future use by your service, such as sending a message to a specific user.</span></span>

<span data-ttu-id="80262-215">Der folgende Code zeigt ein Beispiel für das hinzugefügte Ereignis von Teammitgliedern:</span><span class="sxs-lookup"><span data-stu-id="80262-215">The following code shows an example of team members added event:</span></span>

# <a name="c"></a>[<span data-ttu-id="80262-216">C#</span><span class="sxs-lookup"><span data-stu-id="80262-216">C#</span></span>](#tab/dotnet)

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

# <a name="typescript"></a>[<span data-ttu-id="80262-217">TypeScript</span><span class="sxs-lookup"><span data-stu-id="80262-217">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="80262-218">Json</span><span class="sxs-lookup"><span data-stu-id="80262-218">JSON</span></span>](#tab/json)

<span data-ttu-id="80262-219">Dies ist die Nachricht, die Ihr Bot empfängt, wenn der Bot zu einem Team hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="80262-219">This is the message your bot receives when the bot is added to a team.</span></span>

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

<span data-ttu-id="80262-220">Dies ist die Nachricht, die Ihr Bot empfängt, wenn der Bot zu einem 1:1-Chat hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="80262-220">This is the message your bot receives when the bot is added to a one-to-one chat.</span></span>

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

# <a name="python"></a>[<span data-ttu-id="80262-221">Python</span><span class="sxs-lookup"><span data-stu-id="80262-221">Python</span></span>](#tab/python)

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

### <a name="team-members-removed"></a><span data-ttu-id="80262-222">Entfernte Teammitglieder</span><span class="sxs-lookup"><span data-stu-id="80262-222">Team members removed</span></span>

<span data-ttu-id="80262-223">Das `teamMemberRemoved` Ereignis wird an Ihren Bot gesendet, wenn es aus einem Team entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="80262-223">The `teamMemberRemoved` event is sent to your bot if it is removed from a team.</span></span> <span data-ttu-id="80262-224">Das Ereignis wird jedes Mal an Ihren Bot gesendet, wenn ein Benutzer aus einem Team entfernt wird, in dem Ihr Bot Mitglied ist.</span><span class="sxs-lookup"><span data-stu-id="80262-224">The event is sent to your bot every time any user is removed from a team where your bot is a member.</span></span> <span data-ttu-id="80262-225">Um festzustellen, ob das entfernte neue Element der Bot selbst oder ein Benutzer war, überprüfen Sie das `Activity` Objekt des `turnContext` .</span><span class="sxs-lookup"><span data-stu-id="80262-225">To determine if the new member removed was the bot itself or a user, check the `Activity` object of the `turnContext`.</span></span>  <span data-ttu-id="80262-226">Wenn das Feld des Objekts mit dem Feld des Objekts identisch ist, ist das entfernte Element der Bot, sonst handelt es sich `Id` `MembersRemoved` um einen `Id` `Recipient` Benutzer.</span><span class="sxs-lookup"><span data-stu-id="80262-226">If the `Id` field of the `MembersRemoved` object is the same as the `Id` field of the `Recipient` object, then the member removed is the bot, else it is a user.</span></span> <span data-ttu-id="80262-227">Der Bot ist `Id` im Allgemeinen `28:<MicrosoftAppId>` .</span><span class="sxs-lookup"><span data-stu-id="80262-227">The bot's `Id` generally is `28:<MicrosoftAppId>`.</span></span>

> [!NOTE]
> <span data-ttu-id="80262-228">Wenn ein Benutzer dauerhaft aus einem Mandanten gelöscht wird, `membersRemoved conversationUpdate` wird das Ereignis ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="80262-228">When a user is permanently deleted from a tenant, `membersRemoved conversationUpdate` event is triggered.</span></span>

<span data-ttu-id="80262-229">Der folgende Code zeigt ein Beispiel für das ereignis entfernte Teammitglieder:</span><span class="sxs-lookup"><span data-stu-id="80262-229">The following code shows an example of team members removed event:</span></span>

# <a name="c"></a>[<span data-ttu-id="80262-230">C#</span><span class="sxs-lookup"><span data-stu-id="80262-230">C#</span></span>](#tab/dotnet)

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

# <a name="typescript"></a>[<span data-ttu-id="80262-231">TypeScript</span><span class="sxs-lookup"><span data-stu-id="80262-231">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="80262-232">Json</span><span class="sxs-lookup"><span data-stu-id="80262-232">JSON</span></span>](#tab/json)

<span data-ttu-id="80262-233">Das Objekt im folgenden Nutzlastbeispiel basiert auf dem Hinzufügen eines Mitglieds zu einem Team anstelle eines Gruppenchats oder dem Initiieren einer neuen `channelData` 1:1-Unterhaltung:</span><span class="sxs-lookup"><span data-stu-id="80262-233">The `channelData` object in the following payload example is based on adding a member to a team rather than a group chat, or initiating a new one-to-one conversation:</span></span>

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


# <a name="python"></a>[<span data-ttu-id="80262-234">Python</span><span class="sxs-lookup"><span data-stu-id="80262-234">Python</span></span>](#tab/python)

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

### <a name="team-renamed"></a><span data-ttu-id="80262-235">Team umbenannt</span><span class="sxs-lookup"><span data-stu-id="80262-235">Team renamed</span></span>

<span data-ttu-id="80262-236">Ihr Bot wird benachrichtigt, wenn das Team, in dem er sich befindet, umbenannt wurde.</span><span class="sxs-lookup"><span data-stu-id="80262-236">Your bot is notified when the team it is in has been renamed.</span></span> <span data-ttu-id="80262-237">Es empfängt ein `conversationUpdate` Ereignis mit `eventType.teamRenamed` im `channelData` Objekt.</span><span class="sxs-lookup"><span data-stu-id="80262-237">It receives a `conversationUpdate` event with `eventType.teamRenamed` in the `channelData` object.</span></span>

<span data-ttu-id="80262-238">Der folgende Code zeigt ein Beispiel für das in Team umbenannte Ereignis:</span><span class="sxs-lookup"><span data-stu-id="80262-238">The following code shows an example of team renamed event:</span></span>

# <a name="c"></a>[<span data-ttu-id="80262-239">C#</span><span class="sxs-lookup"><span data-stu-id="80262-239">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamRenamedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the new Team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescript"></a>[<span data-ttu-id="80262-240">TypeScript</span><span class="sxs-lookup"><span data-stu-id="80262-240">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="80262-241">Json</span><span class="sxs-lookup"><span data-stu-id="80262-241">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="80262-242">Python</span><span class="sxs-lookup"><span data-stu-id="80262-242">Python</span></span>](#tab/python)

```python
async def on_teams_team_renamed(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The new team name is {team_info.name}")
    )
```

* * *

### <a name="team-deleted"></a><span data-ttu-id="80262-243">Team gelöscht</span><span class="sxs-lookup"><span data-stu-id="80262-243">Team deleted</span></span>

<span data-ttu-id="80262-244">Ihr Bot wird benachrichtigt, wenn das Team, in dem er sich befindet, gelöscht wurde.</span><span class="sxs-lookup"><span data-stu-id="80262-244">Your bot is notified when the team it is in has been deleted.</span></span> <span data-ttu-id="80262-245">Es empfängt ein `conversationUpdate` Ereignis mit `eventType.teamDeleted` im `channelData` Objekt.</span><span class="sxs-lookup"><span data-stu-id="80262-245">It receives a `conversationUpdate` event with `eventType.teamDeleted` in the `channelData` object.</span></span>

<span data-ttu-id="80262-246">Der folgende Code zeigt ein Beispiel für das gelöschte Teamereignis:</span><span class="sxs-lookup"><span data-stu-id="80262-246">The following code shows an example of team deleted event:</span></span>

# <a name="c"></a>[<span data-ttu-id="80262-247">C#</span><span class="sxs-lookup"><span data-stu-id="80262-247">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamDeletedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    //handle delete event
}
```

# <a name="typescript"></a>[<span data-ttu-id="80262-248">TypeScript</span><span class="sxs-lookup"><span data-stu-id="80262-248">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="80262-249">Json</span><span class="sxs-lookup"><span data-stu-id="80262-249">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="80262-250">Python</span><span class="sxs-lookup"><span data-stu-id="80262-250">Python</span></span>](#tab/python)

```python
async def on_teams_team_deleted(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    //handle delete event
    )
```

* * *

### <a name="team-restored"></a><span data-ttu-id="80262-251">Team wiederhergestellt</span><span class="sxs-lookup"><span data-stu-id="80262-251">Team restored</span></span>

<span data-ttu-id="80262-252">Der Bot erhält eine Benachrichtigung, wenn ein Team nach dem Löschen wiederhergestellt wird.</span><span class="sxs-lookup"><span data-stu-id="80262-252">The bot receives a notification when a team is restored after being deleted.</span></span> <span data-ttu-id="80262-253">Es empfängt ein `conversationUpdate` Ereignis mit `eventType.teamrestored` im `channelData` Objekt.</span><span class="sxs-lookup"><span data-stu-id="80262-253">It receives a `conversationUpdate` event with `eventType.teamrestored` in the `channelData` object.</span></span>

<span data-ttu-id="80262-254">Der folgende Code zeigt ein Beispiel für ein vom Team wiederhergestelltes Ereignis:</span><span class="sxs-lookup"><span data-stu-id="80262-254">The following code shows an example of team restored event:</span></span>

# <a name="c"></a>[<span data-ttu-id="80262-255">C#</span><span class="sxs-lookup"><span data-stu-id="80262-255">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamrestoredAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescript"></a>[<span data-ttu-id="80262-256">TypeScript</span><span class="sxs-lookup"><span data-stu-id="80262-256">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="80262-257">Json</span><span class="sxs-lookup"><span data-stu-id="80262-257">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="80262-258">Python</span><span class="sxs-lookup"><span data-stu-id="80262-258">Python</span></span>](#tab/python)

```python
async def on_teams_team_restored(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The team name is {team_info.name}")
    )
```

* * *

### <a name="team-archived"></a><span data-ttu-id="80262-259">Team archiviert</span><span class="sxs-lookup"><span data-stu-id="80262-259">Team archived</span></span>

<span data-ttu-id="80262-260">Der Bot empfängt eine Benachrichtigung, wenn das Team archiviert wird, in dem er installiert ist.</span><span class="sxs-lookup"><span data-stu-id="80262-260">The bot receives a notification when the team it is installed in is archived.</span></span> <span data-ttu-id="80262-261">Es empfängt ein `conversationUpdate` Ereignis mit `eventType.teamarchived` im `channelData` Objekt.</span><span class="sxs-lookup"><span data-stu-id="80262-261">It receives a `conversationUpdate` event with `eventType.teamarchived` in the `channelData` object.</span></span>

<span data-ttu-id="80262-262">Der folgende Code zeigt ein Beispiel für ein teamarchiviertes Ereignis:</span><span class="sxs-lookup"><span data-stu-id="80262-262">The following code shows an example of team archived event:</span></span>

# <a name="c"></a>[<span data-ttu-id="80262-263">C#</span><span class="sxs-lookup"><span data-stu-id="80262-263">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamArchivedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescript"></a>[<span data-ttu-id="80262-264">TypeScript</span><span class="sxs-lookup"><span data-stu-id="80262-264">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="80262-265">Json</span><span class="sxs-lookup"><span data-stu-id="80262-265">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="80262-266">Python</span><span class="sxs-lookup"><span data-stu-id="80262-266">Python</span></span>](#tab/python)

```python
async def on_teams_team_archived(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The team name is {team_info.name}")
    )
```

* * *


### <a name="team-unarchived"></a><span data-ttu-id="80262-267">Team wird nicht archiviert</span><span class="sxs-lookup"><span data-stu-id="80262-267">Team unarchived</span></span>

<span data-ttu-id="80262-268">Der Bot empfängt eine Benachrichtigung, wenn das Team, in dem er installiert ist, nicht archiviert ist.</span><span class="sxs-lookup"><span data-stu-id="80262-268">The bot receives a notification when the team it is installed in is unarchived.</span></span> <span data-ttu-id="80262-269">Es empfängt ein `conversationUpdate` Ereignis mit `eventType.teamUnarchived` im `channelData` Objekt.</span><span class="sxs-lookup"><span data-stu-id="80262-269">It receives a `conversationUpdate` event with `eventType.teamUnarchived` in the `channelData` object.</span></span>

<span data-ttu-id="80262-270">Der folgende Code zeigt ein Beispiel für ein nicht archiviertes Teamereignis:</span><span class="sxs-lookup"><span data-stu-id="80262-270">The following code shows an example of team unarchived event:</span></span>

# <a name="c"></a>[<span data-ttu-id="80262-271">C#</span><span class="sxs-lookup"><span data-stu-id="80262-271">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamUnarchivedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescript"></a>[<span data-ttu-id="80262-272">TypeScript</span><span class="sxs-lookup"><span data-stu-id="80262-272">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="80262-273">Json</span><span class="sxs-lookup"><span data-stu-id="80262-273">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="80262-274">Python</span><span class="sxs-lookup"><span data-stu-id="80262-274">Python</span></span>](#tab/python)

```python
async def on_teams_team_unarchived(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The team name is {team_info.name}")
    )
```

* * *

<span data-ttu-id="80262-275">Nachdem Sie nun mit den Unterhaltungsaktualisierungsereignissen gearbeitet haben, können Sie die Nachrichtenreaktionsereignisse verstehen, die für unterschiedliche Reaktionen auf eine Nachricht auftreten.</span><span class="sxs-lookup"><span data-stu-id="80262-275">Now that you have worked with the conversation update events, you can understand the message reaction events that occur for different reactions to a message.</span></span>

## <a name="message-reaction-events"></a><span data-ttu-id="80262-276">Nachrichtenreaktionsereignisse</span><span class="sxs-lookup"><span data-stu-id="80262-276">Message reaction events</span></span>

<span data-ttu-id="80262-277">Das Ereignis wird gesendet, wenn ein Benutzer Reaktionen auf eine Nachricht hinzufügt oder entfernt, die von Ihrem `messageReaction` Bot gesendet wurde.</span><span class="sxs-lookup"><span data-stu-id="80262-277">The `messageReaction` event is sent when a user adds or removes reactions to a message which was sent by your bot.</span></span> <span data-ttu-id="80262-278">Der `replyToId` enthält die ID der Nachricht, und der ist der Typ der Reaktion im `Type` Textformat.</span><span class="sxs-lookup"><span data-stu-id="80262-278">The `replyToId` contains the ID of the message, and the `Type` is the type of reaction in text format.</span></span> <span data-ttu-id="80262-279">Die Arten von Reaktionen sind z. B. "empörend", "Herz", "Gelächter", "Gefällt mir", "Betrübt" und "überrascht".</span><span class="sxs-lookup"><span data-stu-id="80262-279">The types of reactions include angry, heart, laugh, like, sad, and surprised.</span></span> <span data-ttu-id="80262-280">Dieses Ereignis enthält nicht den Inhalt der ursprünglichen Nachricht.</span><span class="sxs-lookup"><span data-stu-id="80262-280">This event does not contain the contents of the original message.</span></span> <span data-ttu-id="80262-281">Wenn die Verarbeitung von Reaktionen auf Ihre Nachrichten für Ihren Bot wichtig ist, müssen Sie die Nachrichten speichern, wenn Sie sie senden.</span><span class="sxs-lookup"><span data-stu-id="80262-281">If processing reactions to your messages is important for your bot, you must store the messages when you send them.</span></span> <span data-ttu-id="80262-282">Die folgende Tabelle enthält weitere Informationen zum Ereignistyp und zu Nutzlastobjekten:</span><span class="sxs-lookup"><span data-stu-id="80262-282">The following table provides more information about the event type and payload objects:</span></span>

| <span data-ttu-id="80262-283">EventType</span><span class="sxs-lookup"><span data-stu-id="80262-283">EventType</span></span>       | <span data-ttu-id="80262-284">Payload-Objekt</span><span class="sxs-lookup"><span data-stu-id="80262-284">Payload object</span></span>   | <span data-ttu-id="80262-285">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="80262-285">Description</span></span>                                                             | <span data-ttu-id="80262-286">Bereich</span><span class="sxs-lookup"><span data-stu-id="80262-286">Scope</span></span> |
| --------------- | ---------------- | ----------------------------------------------------------------------- | ----- |
| <span data-ttu-id="80262-287">messageReaction</span><span class="sxs-lookup"><span data-stu-id="80262-287">messageReaction</span></span> | <span data-ttu-id="80262-288">reactionsAdded</span><span class="sxs-lookup"><span data-stu-id="80262-288">reactionsAdded</span></span>   | [<span data-ttu-id="80262-289">Reaktionen auf eine Botnachricht</span><span class="sxs-lookup"><span data-stu-id="80262-289">Reactions to a bot message</span></span>](#reactions-to-a-bot-message)                   | <span data-ttu-id="80262-290">Alle</span><span class="sxs-lookup"><span data-stu-id="80262-290">All</span></span>   |
| <span data-ttu-id="80262-291">messageReaction</span><span class="sxs-lookup"><span data-stu-id="80262-291">messageReaction</span></span> | <span data-ttu-id="80262-292">reactionsRemoved</span><span class="sxs-lookup"><span data-stu-id="80262-292">reactionsRemoved</span></span> | [<span data-ttu-id="80262-293">Aus bot-Nachricht entfernte Reaktionen</span><span class="sxs-lookup"><span data-stu-id="80262-293">Reactions removed from bot message</span></span>](#reactions-removed-from-bot-message) | <span data-ttu-id="80262-294">Alle</span><span class="sxs-lookup"><span data-stu-id="80262-294">All</span></span>   |

### <a name="reactions-to-a-bot-message"></a><span data-ttu-id="80262-295">Reaktionen auf eine Botnachricht</span><span class="sxs-lookup"><span data-stu-id="80262-295">Reactions to a bot message</span></span>

<span data-ttu-id="80262-296">Der folgende Code zeigt ein Beispiel für Reaktionen auf eine Botnachricht:</span><span class="sxs-lookup"><span data-stu-id="80262-296">The following code shows an example of reactions to a bot message:</span></span>

# <a name="c"></a>[<span data-ttu-id="80262-297">C#</span><span class="sxs-lookup"><span data-stu-id="80262-297">C#</span></span>](#tab/dotnet)

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

# <a name="typescript"></a>[<span data-ttu-id="80262-298">TypeScript</span><span class="sxs-lookup"><span data-stu-id="80262-298">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="80262-299">Json</span><span class="sxs-lookup"><span data-stu-id="80262-299">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="80262-300">Python</span><span class="sxs-lookup"><span data-stu-id="80262-300">Python</span></span>](#tab/python)

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

### <a name="reactions-removed-from-bot-message"></a><span data-ttu-id="80262-301">Aus bot-Nachricht entfernte Reaktionen</span><span class="sxs-lookup"><span data-stu-id="80262-301">Reactions removed from bot message</span></span>

<span data-ttu-id="80262-302">Der folgende Code zeigt ein Beispiel für aus bot-Nachrichten entfernte Reaktionen:</span><span class="sxs-lookup"><span data-stu-id="80262-302">The following code shows an example of reactions removed from bot message:</span></span>

# <a name="c"></a>[<span data-ttu-id="80262-303">C#</span><span class="sxs-lookup"><span data-stu-id="80262-303">C#</span></span>](#tab/dotnet)

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

# <a name="typescript"></a>[<span data-ttu-id="80262-304">TypeScript</span><span class="sxs-lookup"><span data-stu-id="80262-304">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="80262-305">Json</span><span class="sxs-lookup"><span data-stu-id="80262-305">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="80262-306">Python</span><span class="sxs-lookup"><span data-stu-id="80262-306">Python</span></span>](#tab/python)

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

## <a name="code-sample"></a><span data-ttu-id="80262-307">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="80262-307">Code sample</span></span>

<span data-ttu-id="80262-308">Die folgende Tabelle enthält ein einfaches Codebeispiel, das Bots-Unterhaltungsereignisse in eine Teams-Anwendung integriert:</span><span class="sxs-lookup"><span data-stu-id="80262-308">The following table provides a simple code sample that incorporates bots conversation events into a Teams application:</span></span>

| <span data-ttu-id="80262-309">Beispiel</span><span class="sxs-lookup"><span data-stu-id="80262-309">Sample</span></span> | <span data-ttu-id="80262-310">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="80262-310">Description</span></span> | <span data-ttu-id="80262-311">.NET Core</span><span class="sxs-lookup"><span data-stu-id="80262-311">.NET Core</span></span> |
|--------|------------- |---|
| <span data-ttu-id="80262-312">Beispiel für Teams-Bots-Unterhaltungsereignisse</span><span class="sxs-lookup"><span data-stu-id="80262-312">Teams bots conversation events sample</span></span> | <span data-ttu-id="80262-313">Bot Framework v4 conversation bot sample for Teams.</span><span class="sxs-lookup"><span data-stu-id="80262-313">Bot Framework v4 conversation bot sample for Teams.</span></span> | [<span data-ttu-id="80262-314">View</span><span class="sxs-lookup"><span data-stu-id="80262-314">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot)|

## <a name="next-step"></a><span data-ttu-id="80262-315">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="80262-315">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="80262-316">Senden proaktiver Nachrichten</span><span class="sxs-lookup"><span data-stu-id="80262-316">Send proactive messages</span></span>](~/bots/how-to/conversations/send-proactive-messages.md)
