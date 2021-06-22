---
title: Unterhaltungsereignisse
author: WashingtonKayaker
description: So arbeiten Sie mit Unterhaltungsereignissen aus Ihrem Microsoft Teams-Bot.
ms.topic: conceptual
localization_priority: Normal
ms.author: anclear
ms.openlocfilehash: 39d3a6d54b275fd6b9f28eb38b124435e9ba8bfd
ms.sourcegitcommit: 3d02dfc13331b28cffba42b39560cfeb1503abe2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53049045"
---
# <a name="conversation-events-in-your-teams-bot"></a><span data-ttu-id="31579-103">Unterhaltungsereignisse in Ihrem Teams-Bot</span><span class="sxs-lookup"><span data-stu-id="31579-103">Conversation events in your Teams bot</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="31579-104">Wenn Sie Ihre Unterhaltungsbots für Microsoft Teams erstellen, können Sie mit Unterhaltungsereignissen arbeiten.</span><span class="sxs-lookup"><span data-stu-id="31579-104">When building your conversational bots for Microsoft Teams, you can work with conversation events.</span></span> <span data-ttu-id="31579-105">Teams sendet Benachrichtigungen an Ihren Bot für Unterhaltungsereignisse, die in Bereichen stattfinden, in denen Ihr Bot aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="31579-105">Teams sends notifications to your bot for conversation events that happen in scopes where your bot is active.</span></span> <span data-ttu-id="31579-106">Sie können diese Ereignisse in Ihrem Code erfassen und die folgenden Aktionen ausführen:</span><span class="sxs-lookup"><span data-stu-id="31579-106">You can capture these events in your code and take the following actions:</span></span>

* <span data-ttu-id="31579-107">Lösen Sie eine Willkommensnachricht aus, wenn Ihr Bot zu einem Team hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="31579-107">Trigger a welcome message when your bot is added to a team.</span></span>
* <span data-ttu-id="31579-108">Lösen Sie eine Willkommensnachricht aus, wenn ein neues Teammitglied hinzugefügt oder entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="31579-108">Trigger a welcome message when a new team member is added or removed.</span></span>
* <span data-ttu-id="31579-109">Lösen Sie eine Benachrichtigung aus, wenn ein Kanal erstellt, umbenannt oder gelöscht wird.</span><span class="sxs-lookup"><span data-stu-id="31579-109">Trigger a notification when a channel is created, renamed, or deleted.</span></span>
* <span data-ttu-id="31579-110">Wenn eine Bot-Nachricht von einem Benutzer gefällt.</span><span class="sxs-lookup"><span data-stu-id="31579-110">When a bot message is liked by a user.</span></span>

## <a name="conversation-update-events"></a><span data-ttu-id="31579-111">Aktualisierungsereignisse in Unterhaltungen</span><span class="sxs-lookup"><span data-stu-id="31579-111">Conversation update events</span></span>

<span data-ttu-id="31579-112">Sie können Unterhaltungsaktualisierungsereignisse verwenden, um bessere Benachrichtigungen und effektivere Botaktionen bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="31579-112">You can use conversation update events to provide better notifications and more effective bot actions.</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="31579-113">Sie können neue Ereignisse jederzeit hinzufügen, und Ihr Bot beginnt, sie zu empfangen.</span><span class="sxs-lookup"><span data-stu-id="31579-113">You can add new events any time and your bot begins to receive them.</span></span>
> * <span data-ttu-id="31579-114">Sie müssen Ihren Bot so entwerfen, dass er unerwartete Ereignisse empfängt.</span><span class="sxs-lookup"><span data-stu-id="31579-114">You must design your bot to receive unexpected events.</span></span>
> * <span data-ttu-id="31579-115">Wenn Sie das Bot Framework SDK verwenden, antwortet Ihr Bot automatisch mit a `200 - OK` auf alle Ereignisse, die Sie nicht behandeln möchten.</span><span class="sxs-lookup"><span data-stu-id="31579-115">If you are using the Bot Framework SDK, your bot automatically responds with a `200 - OK` to any events you choose not to handle.</span></span>

<span data-ttu-id="31579-116">Ein Bot empfängt in einem der folgenden Fälle ein `conversationUpdate` Ereignis:</span><span class="sxs-lookup"><span data-stu-id="31579-116">A bot receives a `conversationUpdate` event in either of the following cases:</span></span>

* <span data-ttu-id="31579-117">Wenn Bot zu einer Unterhaltung hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="31579-117">When bot has been added to a conversation.</span></span>
* <span data-ttu-id="31579-118">Andere Mitglieder werden einer Unterhaltung hinzugefügt oder daraus entfernt.</span><span class="sxs-lookup"><span data-stu-id="31579-118">Other members are added to or removed from a conversation.</span></span>
* <span data-ttu-id="31579-119">Unterhaltungsmetadaten wurden geändert.</span><span class="sxs-lookup"><span data-stu-id="31579-119">Conversation metadata has changed.</span></span>

<span data-ttu-id="31579-120">Das `conversationUpdate`-Ereignis wird an Ihren Bot gesendet, wenn er Informationen zu Mitgliedschaftsaktualisierungen für Teams empfängt, denen er hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="31579-120">The `conversationUpdate` event is sent to your bot when it receives information on membership updates for teams where it has been added.</span></span> <span data-ttu-id="31579-121">Es erhält auch ein Update, wenn es zum ersten Mal für persönliche Unterhaltungen hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="31579-121">It also receives an update when it has been added for the first time for personal conversations.</span></span>

<span data-ttu-id="31579-122">Die folgende Tabelle enthält eine Liste Teams Unterhaltungsaktualisierungsereignisse mit weiteren Details:</span><span class="sxs-lookup"><span data-stu-id="31579-122">The following table shows a list of Teams conversation update events with more details:</span></span>

| <span data-ttu-id="31579-123">Ausgeführte Aktion</span><span class="sxs-lookup"><span data-stu-id="31579-123">Action taken</span></span>        | <span data-ttu-id="31579-124">EventType</span><span class="sxs-lookup"><span data-stu-id="31579-124">EventType</span></span>         | <span data-ttu-id="31579-125">Aufgerufene Methode</span><span class="sxs-lookup"><span data-stu-id="31579-125">Method called</span></span>              | <span data-ttu-id="31579-126">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="31579-126">Description</span></span>                | <span data-ttu-id="31579-127">Bereich</span><span class="sxs-lookup"><span data-stu-id="31579-127">Scope</span></span> |
| ------------------- | ----------------- | -------------------------- | -------------------------- | ----- |
| <span data-ttu-id="31579-128">Kanal erstellt</span><span class="sxs-lookup"><span data-stu-id="31579-128">Channel created</span></span>     | <span data-ttu-id="31579-129">channelCreated</span><span class="sxs-lookup"><span data-stu-id="31579-129">channelCreated</span></span>    | <span data-ttu-id="31579-130">OnTeamsChannelCreatedAsync</span><span class="sxs-lookup"><span data-stu-id="31579-130">OnTeamsChannelCreatedAsync</span></span> | <span data-ttu-id="31579-131">[Ein Kanal wird erstellt.](#channel-created)</span><span class="sxs-lookup"><span data-stu-id="31579-131">[A channel is created](#channel-created).</span></span> | <span data-ttu-id="31579-132">Team</span><span class="sxs-lookup"><span data-stu-id="31579-132">Team</span></span> |
| <span data-ttu-id="31579-133">Kanal umbenannt</span><span class="sxs-lookup"><span data-stu-id="31579-133">Channel renamed</span></span>     | <span data-ttu-id="31579-134">channelRenamed</span><span class="sxs-lookup"><span data-stu-id="31579-134">channelRenamed</span></span>    | <span data-ttu-id="31579-135">OnTeamsChannelRenamedAsync</span><span class="sxs-lookup"><span data-stu-id="31579-135">OnTeamsChannelRenamedAsync</span></span> | <span data-ttu-id="31579-136">[Ein Kanal wird umbenannt.](#channel-renamed)</span><span class="sxs-lookup"><span data-stu-id="31579-136">[A channel is renamed](#channel-renamed).</span></span> | <span data-ttu-id="31579-137">Team</span><span class="sxs-lookup"><span data-stu-id="31579-137">Team</span></span> |
| <span data-ttu-id="31579-138">Kanal gelöscht</span><span class="sxs-lookup"><span data-stu-id="31579-138">Channel deleted</span></span>     | <span data-ttu-id="31579-139">channelDeleted</span><span class="sxs-lookup"><span data-stu-id="31579-139">channelDeleted</span></span>    | <span data-ttu-id="31579-140">OnTeamsChannelDeletedAsync</span><span class="sxs-lookup"><span data-stu-id="31579-140">OnTeamsChannelDeletedAsync</span></span> | <span data-ttu-id="31579-141">[Ein Kanal wird gelöscht.](#channel-deleted)</span><span class="sxs-lookup"><span data-stu-id="31579-141">[A channel is deleted](#channel-deleted).</span></span> | <span data-ttu-id="31579-142">Team</span><span class="sxs-lookup"><span data-stu-id="31579-142">Team</span></span> |
| <span data-ttu-id="31579-143">Kanal wiederhergestellt</span><span class="sxs-lookup"><span data-stu-id="31579-143">Channel restored</span></span>    | <span data-ttu-id="31579-144">channelRestored</span><span class="sxs-lookup"><span data-stu-id="31579-144">channelRestored</span></span>    | <span data-ttu-id="31579-145">OnTeamsChannelRestoredAsync</span><span class="sxs-lookup"><span data-stu-id="31579-145">OnTeamsChannelRestoredAsync</span></span> | <span data-ttu-id="31579-146">[Ein Kanal wird wiederhergestellt.](#channel-deleted)</span><span class="sxs-lookup"><span data-stu-id="31579-146">[A channel is restored](#channel-deleted).</span></span> | <span data-ttu-id="31579-147">Team</span><span class="sxs-lookup"><span data-stu-id="31579-147">Team</span></span> |
| <span data-ttu-id="31579-148">Hinzugefügte Mitglieder</span><span class="sxs-lookup"><span data-stu-id="31579-148">Members added</span></span>   | <span data-ttu-id="31579-149">membersAdded</span><span class="sxs-lookup"><span data-stu-id="31579-149">membersAdded</span></span>   | <span data-ttu-id="31579-150">OnTeamsMembersAddedAsync</span><span class="sxs-lookup"><span data-stu-id="31579-150">OnTeamsMembersAddedAsync</span></span>   | <span data-ttu-id="31579-151">[Ein Element wird hinzugefügt.](#team-members-added)</span><span class="sxs-lookup"><span data-stu-id="31579-151">[A member is added](#team-members-added).</span></span> | <span data-ttu-id="31579-152">Alle</span><span class="sxs-lookup"><span data-stu-id="31579-152">All</span></span> |
| <span data-ttu-id="31579-153">Elemente entfernt</span><span class="sxs-lookup"><span data-stu-id="31579-153">Members removed</span></span> | <span data-ttu-id="31579-154">membersRemoved</span><span class="sxs-lookup"><span data-stu-id="31579-154">membersRemoved</span></span> | <span data-ttu-id="31579-155">OnTeamsMembersRemovedAsync</span><span class="sxs-lookup"><span data-stu-id="31579-155">OnTeamsMembersRemovedAsync</span></span> | <span data-ttu-id="31579-156">[Ein Element wird entfernt.](#team-members-removed)</span><span class="sxs-lookup"><span data-stu-id="31579-156">[A member is removed](#team-members-removed).</span></span> | <span data-ttu-id="31579-157">groupChat und Team</span><span class="sxs-lookup"><span data-stu-id="31579-157">groupChat and team</span></span> |
| <span data-ttu-id="31579-158">Team umbenannt</span><span class="sxs-lookup"><span data-stu-id="31579-158">Team renamed</span></span>        | <span data-ttu-id="31579-159">teamRenamed</span><span class="sxs-lookup"><span data-stu-id="31579-159">teamRenamed</span></span>       | <span data-ttu-id="31579-160">OnTeamsTeamRenamedAsync</span><span class="sxs-lookup"><span data-stu-id="31579-160">OnTeamsTeamRenamedAsync</span></span>    | <span data-ttu-id="31579-161">[Ein Team wird umbenannt.](#team-renamed)</span><span class="sxs-lookup"><span data-stu-id="31579-161">[A team is renamed](#team-renamed).</span></span>       | <span data-ttu-id="31579-162">Team</span><span class="sxs-lookup"><span data-stu-id="31579-162">Team</span></span> |
| <span data-ttu-id="31579-163">Team gelöscht</span><span class="sxs-lookup"><span data-stu-id="31579-163">Team deleted</span></span>        | <span data-ttu-id="31579-164">teamDeleted</span><span class="sxs-lookup"><span data-stu-id="31579-164">teamDeleted</span></span>       | <span data-ttu-id="31579-165">OnTeamsTeamDeletedAsync</span><span class="sxs-lookup"><span data-stu-id="31579-165">OnTeamsTeamDeletedAsync</span></span>    | <span data-ttu-id="31579-166">[Ein Team wird gelöscht.](#team-deleted)</span><span class="sxs-lookup"><span data-stu-id="31579-166">[A team is deleted](#team-deleted).</span></span>       | <span data-ttu-id="31579-167">Team</span><span class="sxs-lookup"><span data-stu-id="31579-167">Team</span></span> |
| <span data-ttu-id="31579-168">Team archiviert</span><span class="sxs-lookup"><span data-stu-id="31579-168">Team archived</span></span>        | <span data-ttu-id="31579-169">teamArchived</span><span class="sxs-lookup"><span data-stu-id="31579-169">teamArchived</span></span>       | <span data-ttu-id="31579-170">OnTeamsTeamArchivedAsync</span><span class="sxs-lookup"><span data-stu-id="31579-170">OnTeamsTeamArchivedAsync</span></span>    | <span data-ttu-id="31579-171">[Ein Team wird archiviert.](#team-archived)</span><span class="sxs-lookup"><span data-stu-id="31579-171">[A team is archived](#team-archived).</span></span>       | <span data-ttu-id="31579-172">Team</span><span class="sxs-lookup"><span data-stu-id="31579-172">Team</span></span> |
| <span data-ttu-id="31579-173">Team nicht archiviert</span><span class="sxs-lookup"><span data-stu-id="31579-173">Team unarchived</span></span>        | <span data-ttu-id="31579-174">teamUnarchived</span><span class="sxs-lookup"><span data-stu-id="31579-174">teamUnarchived</span></span>       | <span data-ttu-id="31579-175">OnTeamsTeamUnarchivedAsync</span><span class="sxs-lookup"><span data-stu-id="31579-175">OnTeamsTeamUnarchivedAsync</span></span>    | <span data-ttu-id="31579-176">[Ein Team wird nicht archiviert.](#team-unarchived)</span><span class="sxs-lookup"><span data-stu-id="31579-176">[A team is unarchived](#team-unarchived).</span></span>       | <span data-ttu-id="31579-177">Team</span><span class="sxs-lookup"><span data-stu-id="31579-177">Team</span></span> |
| <span data-ttu-id="31579-178">Team wiederhergestellt</span><span class="sxs-lookup"><span data-stu-id="31579-178">Team restored</span></span>        | <span data-ttu-id="31579-179">teamRestored</span><span class="sxs-lookup"><span data-stu-id="31579-179">teamRestored</span></span>      | <span data-ttu-id="31579-180">OnTeamsTeamRestoredAsync</span><span class="sxs-lookup"><span data-stu-id="31579-180">OnTeamsTeamRestoredAsync</span></span>    | [<span data-ttu-id="31579-181">Ein Team wird wiederhergestellt</span><span class="sxs-lookup"><span data-stu-id="31579-181">A team is restored</span></span>](#team-restored)       | <span data-ttu-id="31579-182">Team</span><span class="sxs-lookup"><span data-stu-id="31579-182">Team</span></span> |

### <a name="channel-created"></a><span data-ttu-id="31579-183">Kanal erstellt</span><span class="sxs-lookup"><span data-stu-id="31579-183">Channel created</span></span>

<span data-ttu-id="31579-184">Das vom Kanal erstellte Ereignis wird immer dann an Ihren Bot gesendet, wenn ein neuer Kanal in einem Team erstellt wird, in dem Ihr Bot installiert ist.</span><span class="sxs-lookup"><span data-stu-id="31579-184">The channel created event is sent to your bot whenever a new channel is created in a team where your bot is installed.</span></span>

<span data-ttu-id="31579-185">Der folgende Code zeigt ein Beispiel für ein Kanalerstellungsereignis:</span><span class="sxs-lookup"><span data-stu-id="31579-185">The following code shows an example of channel created event:</span></span>

# <a name="c"></a>[<span data-ttu-id="31579-186">C#</span><span class="sxs-lookup"><span data-stu-id="31579-186">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelCreatedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the Channel created");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescript"></a>[<span data-ttu-id="31579-187">TypeScript</span><span class="sxs-lookup"><span data-stu-id="31579-187">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="31579-188">Json</span><span class="sxs-lookup"><span data-stu-id="31579-188">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="31579-189">Python</span><span class="sxs-lookup"><span data-stu-id="31579-189">Python</span></span>](#tab/python)

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

---

### <a name="channel-renamed"></a><span data-ttu-id="31579-190">Kanal umbenannt</span><span class="sxs-lookup"><span data-stu-id="31579-190">Channel renamed</span></span>

<span data-ttu-id="31579-191">Das umbenannte Kanalereignis wird an Ihren Bot gesendet, wenn ein Kanal in einem Team umbenannt wird, in dem Ihr Bot installiert ist.</span><span class="sxs-lookup"><span data-stu-id="31579-191">The channel renamed event is sent to your bot whenever a channel is renamed in a team where your bot is installed.</span></span>

<span data-ttu-id="31579-192">Der folgende Code zeigt ein Beispiel für ein Kanal-Umbenennungsereignis:</span><span class="sxs-lookup"><span data-stu-id="31579-192">The following code shows an example of channel renamed event:</span></span>

# <a name="c"></a>[<span data-ttu-id="31579-193">C#</span><span class="sxs-lookup"><span data-stu-id="31579-193">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelRenamedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the new Channel name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescript"></a>[<span data-ttu-id="31579-194">TypeScript</span><span class="sxs-lookup"><span data-stu-id="31579-194">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="31579-195">Json</span><span class="sxs-lookup"><span data-stu-id="31579-195">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="31579-196">Python</span><span class="sxs-lookup"><span data-stu-id="31579-196">Python</span></span>](#tab/python)

```python
async def on_teams_channel_renamed(
    self, channel_info: ChannelInfo, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The new channel name is {channel_info.name}")
    )
```

---

### <a name="channel-deleted"></a><span data-ttu-id="31579-197">Kanal gelöscht</span><span class="sxs-lookup"><span data-stu-id="31579-197">Channel deleted</span></span>

<span data-ttu-id="31579-198">Das Ereignis "Kanal gelöscht" wird immer dann an Ihren Bot gesendet, wenn ein Kanal in einem Team gelöscht wird, in dem Ihr Bot installiert ist.</span><span class="sxs-lookup"><span data-stu-id="31579-198">The channel deleted event is sent to your bot whenever a channel is deleted in a team where your bot is installed.</span></span>

<span data-ttu-id="31579-199">Der folgende Code zeigt ein Beispiel für das Ereignis "Kanal gelöscht":</span><span class="sxs-lookup"><span data-stu-id="31579-199">The following code shows an example of channel deleted event:</span></span>

# <a name="c"></a>[<span data-ttu-id="31579-200">C#</span><span class="sxs-lookup"><span data-stu-id="31579-200">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelDeletedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the Channel deleted");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescript"></a>[<span data-ttu-id="31579-201">TypeScript</span><span class="sxs-lookup"><span data-stu-id="31579-201">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="31579-202">Json</span><span class="sxs-lookup"><span data-stu-id="31579-202">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="31579-203">Python</span><span class="sxs-lookup"><span data-stu-id="31579-203">Python</span></span>](#tab/python)

```python
async def on_teams_channel_deleted(
    self, channel_info: ChannelInfo, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The deleted channel is {channel_info.name}")
    )
```

---

### <a name="channel-restored"></a><span data-ttu-id="31579-204">Kanal wiederhergestellt</span><span class="sxs-lookup"><span data-stu-id="31579-204">Channel restored</span></span>

<span data-ttu-id="31579-205">Das Wiederherstellungsereignis des Kanals wird immer dann an Ihren Bot gesendet, wenn ein zuvor gelöschter Kanal in einem Team wiederhergestellt wird, in dem Ihr Bot bereits installiert ist.</span><span class="sxs-lookup"><span data-stu-id="31579-205">The channel restored event is sent to your bot whenever a channel that was previously deleted is restored in a team where your bot is already installed.</span></span>

<span data-ttu-id="31579-206">Der folgende Code zeigt ein Beispiel für ein Wiederherstellungsereignis des Kanals:</span><span class="sxs-lookup"><span data-stu-id="31579-206">The following code shows an example of channel restored event:</span></span>

# <a name="c"></a>[<span data-ttu-id="31579-207">C#</span><span class="sxs-lookup"><span data-stu-id="31579-207">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelRestoredAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the Channel restored.");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescript"></a>[<span data-ttu-id="31579-208">TypeScript</span><span class="sxs-lookup"><span data-stu-id="31579-208">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="31579-209">Json</span><span class="sxs-lookup"><span data-stu-id="31579-209">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="31579-210">Python</span><span class="sxs-lookup"><span data-stu-id="31579-210">Python</span></span>](#tab/python)

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

---

### <a name="team-members-added"></a><span data-ttu-id="31579-211">Teammitglieder hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="31579-211">Team members added</span></span>

<span data-ttu-id="31579-212">Das `teamMemberAdded` Ereignis wird an Ihren Bot gesendet, wenn es zum ersten Mal zu einer Unterhaltung hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="31579-212">The `teamMemberAdded` event is sent to your bot the first time it is added to a conversation.</span></span> <span data-ttu-id="31579-213">Das Ereignis wird jedes Mal an Ihren Bot gesendet, wenn ein neuer Benutzer zu einem Team- oder Gruppenchat hinzugefügt wird, in dem Ihr Bot installiert ist.</span><span class="sxs-lookup"><span data-stu-id="31579-213">The event is sent to your bot every time a new user is added to a team or group chat where your bot is installed.</span></span> <span data-ttu-id="31579-214">Die Benutzerinformationen, die ID sind, sind für Ihren Bot eindeutig und können für die zukünftige Verwendung durch Ihren Dienst zwischengespeichert werden, z. B. das Senden einer Nachricht an einen bestimmten Benutzer.</span><span class="sxs-lookup"><span data-stu-id="31579-214">The user information that is ID is unique for your bot and can be cached for future use by your service, such as sending a message to a specific user.</span></span>

<span data-ttu-id="31579-215">Der folgende Code zeigt ein Beispiel für das hinzugefügte Ereignis für Teammitglieder:</span><span class="sxs-lookup"><span data-stu-id="31579-215">The following code shows an example of team members added event:</span></span>

# <a name="c"></a>[<span data-ttu-id="31579-216">C#</span><span class="sxs-lookup"><span data-stu-id="31579-216">C#</span></span>](#tab/dotnet)

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

# <a name="typescript"></a>[<span data-ttu-id="31579-217">TypeScript</span><span class="sxs-lookup"><span data-stu-id="31579-217">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="31579-218">Json</span><span class="sxs-lookup"><span data-stu-id="31579-218">JSON</span></span>](#tab/json)

<span data-ttu-id="31579-219">Dies ist die Nachricht, die Ihr Bot erhält, wenn der Bot einem Team hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="31579-219">This is the message your bot receives when the bot is added to a team.</span></span>

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

<span data-ttu-id="31579-220">Dies ist die Nachricht, die Ihr Bot erhält, wenn der Bot zu einem 1:1-Chat hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="31579-220">This is the message your bot receives when the bot is added to a one-to-one chat.</span></span>

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

# <a name="python"></a>[<span data-ttu-id="31579-221">Python</span><span class="sxs-lookup"><span data-stu-id="31579-221">Python</span></span>](#tab/python)

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

---

### <a name="team-members-removed"></a><span data-ttu-id="31579-222">Teammitglieder entfernt</span><span class="sxs-lookup"><span data-stu-id="31579-222">Team members removed</span></span>

<span data-ttu-id="31579-223">Das `teamMemberRemoved` Ereignis wird an Ihren Bot gesendet, wenn es aus einem Team entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="31579-223">The `teamMemberRemoved` event is sent to your bot if it is removed from a team.</span></span> <span data-ttu-id="31579-224">Das Ereignis wird jedes Mal an Ihren Bot gesendet, wenn ein Beliebiger Benutzer aus einem Team entfernt wird, in dem Ihr Bot Mitglied ist.</span><span class="sxs-lookup"><span data-stu-id="31579-224">The event is sent to your bot every time any user is removed from a team where your bot is a member.</span></span> <span data-ttu-id="31579-225">Um festzustellen, ob das neue Mitglied entfernt wurde, der Bot selbst oder ein Benutzer war, überprüfen Sie das `Activity` Objekt des `turnContext` .</span><span class="sxs-lookup"><span data-stu-id="31579-225">To determine if the new member removed was the bot itself or a user, check the `Activity` object of the `turnContext`.</span></span>  <span data-ttu-id="31579-226">Wenn das `Id` Feld des Objekts mit dem Feld des Objekts identisch `MembersRemoved` `Id` `Recipient` ist, ist das entfernte Element der Bot, andernfalls ein Benutzer.</span><span class="sxs-lookup"><span data-stu-id="31579-226">If the `Id` field of the `MembersRemoved` object is the same as the `Id` field of the `Recipient` object, then the member removed is the bot, else it is a user.</span></span> <span data-ttu-id="31579-227">Der Bot `Id` ist im Allgemeinen `28:<MicrosoftAppId>` .</span><span class="sxs-lookup"><span data-stu-id="31579-227">The bot's `Id` generally is `28:<MicrosoftAppId>`.</span></span>

> [!NOTE]
> <span data-ttu-id="31579-228">Wenn ein Benutzer dauerhaft aus einem Mandanten gelöscht wird, `membersRemoved conversationUpdate` wird das Ereignis ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="31579-228">When a user is permanently deleted from a tenant, `membersRemoved conversationUpdate` event is triggered.</span></span>

<span data-ttu-id="31579-229">Der folgende Code zeigt ein Beispiel für ein Ereignis, bei dem Teammitglieder entfernt wurden:</span><span class="sxs-lookup"><span data-stu-id="31579-229">The following code shows an example of team members removed event:</span></span>

# <a name="c"></a>[<span data-ttu-id="31579-230">C#</span><span class="sxs-lookup"><span data-stu-id="31579-230">C#</span></span>](#tab/dotnet)

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

# <a name="typescript"></a>[<span data-ttu-id="31579-231">TypeScript</span><span class="sxs-lookup"><span data-stu-id="31579-231">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="31579-232">Json</span><span class="sxs-lookup"><span data-stu-id="31579-232">JSON</span></span>](#tab/json)

<span data-ttu-id="31579-233">Das `channelData` Objekt im folgenden Nutzlastbeispiel basiert auf dem Hinzufügen eines Mitglieds zu einem Team anstelle eines Gruppenchats oder dem Initiieren einer neuen 1:1-Unterhaltung:</span><span class="sxs-lookup"><span data-stu-id="31579-233">The `channelData` object in the following payload example is based on adding a member to a team rather than a group chat, or initiating a new one-to-one conversation:</span></span>

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


# <a name="python"></a>[<span data-ttu-id="31579-234">Python</span><span class="sxs-lookup"><span data-stu-id="31579-234">Python</span></span>](#tab/python)

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

---

### <a name="team-renamed"></a><span data-ttu-id="31579-235">Team umbenannt</span><span class="sxs-lookup"><span data-stu-id="31579-235">Team renamed</span></span>

<span data-ttu-id="31579-236">Ihr Bot wird benachrichtigt, wenn das Team, in dem er sich befindet, umbenannt wurde.</span><span class="sxs-lookup"><span data-stu-id="31579-236">Your bot is notified when the team it is in has been renamed.</span></span> <span data-ttu-id="31579-237">Es empfängt ein `conversationUpdate` Ereignis mit `eventType.teamRenamed` im `channelData` Objekt.</span><span class="sxs-lookup"><span data-stu-id="31579-237">It receives a `conversationUpdate` event with `eventType.teamRenamed` in the `channelData` object.</span></span>

<span data-ttu-id="31579-238">Der folgende Code zeigt ein Beispiel für ein umbenanntes Teamereignis:</span><span class="sxs-lookup"><span data-stu-id="31579-238">The following code shows an example of team renamed event:</span></span>

# <a name="c"></a>[<span data-ttu-id="31579-239">C#</span><span class="sxs-lookup"><span data-stu-id="31579-239">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamRenamedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the new Team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescript"></a>[<span data-ttu-id="31579-240">TypeScript</span><span class="sxs-lookup"><span data-stu-id="31579-240">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="31579-241">Json</span><span class="sxs-lookup"><span data-stu-id="31579-241">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="31579-242">Python</span><span class="sxs-lookup"><span data-stu-id="31579-242">Python</span></span>](#tab/python)

```python
async def on_teams_team_renamed(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The new team name is {team_info.name}")
    )
```

---

### <a name="team-deleted"></a><span data-ttu-id="31579-243">Team gelöscht</span><span class="sxs-lookup"><span data-stu-id="31579-243">Team deleted</span></span>

<span data-ttu-id="31579-244">Ihr Bot wird benachrichtigt, wenn das Team, in dem er sich befindet, gelöscht wurde.</span><span class="sxs-lookup"><span data-stu-id="31579-244">Your bot is notified when the team it is in has been deleted.</span></span> <span data-ttu-id="31579-245">Es empfängt ein `conversationUpdate` Ereignis mit `eventType.teamDeleted` im `channelData` Objekt.</span><span class="sxs-lookup"><span data-stu-id="31579-245">It receives a `conversationUpdate` event with `eventType.teamDeleted` in the `channelData` object.</span></span>

<span data-ttu-id="31579-246">Der folgende Code zeigt ein Beispiel für ein Team-Deleted-Ereignis:</span><span class="sxs-lookup"><span data-stu-id="31579-246">The following code shows an example of team deleted event:</span></span>

# <a name="c"></a>[<span data-ttu-id="31579-247">C#</span><span class="sxs-lookup"><span data-stu-id="31579-247">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamDeletedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    //handle delete event
}
```

# <a name="typescript"></a>[<span data-ttu-id="31579-248">TypeScript</span><span class="sxs-lookup"><span data-stu-id="31579-248">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="31579-249">Json</span><span class="sxs-lookup"><span data-stu-id="31579-249">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="31579-250">Python</span><span class="sxs-lookup"><span data-stu-id="31579-250">Python</span></span>](#tab/python)

```python
async def on_teams_team_deleted(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    //handle delete event
    )
```

---

### <a name="team-restored"></a><span data-ttu-id="31579-251">Team wiederhergestellt</span><span class="sxs-lookup"><span data-stu-id="31579-251">Team restored</span></span>

<span data-ttu-id="31579-252">Der Bot erhält eine Benachrichtigung, wenn ein Team nach dem Löschen wiederhergestellt wird.</span><span class="sxs-lookup"><span data-stu-id="31579-252">The bot receives a notification when a team is restored after being deleted.</span></span> <span data-ttu-id="31579-253">Es empfängt ein `conversationUpdate` Ereignis mit `eventType.teamrestored` im `channelData` Objekt.</span><span class="sxs-lookup"><span data-stu-id="31579-253">It receives a `conversationUpdate` event with `eventType.teamrestored` in the `channelData` object.</span></span>

<span data-ttu-id="31579-254">Der folgende Code zeigt ein Beispiel für ein Wiederherstellungsereignis des Teams:</span><span class="sxs-lookup"><span data-stu-id="31579-254">The following code shows an example of team restored event:</span></span>

# <a name="c"></a>[<span data-ttu-id="31579-255">C#</span><span class="sxs-lookup"><span data-stu-id="31579-255">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamrestoredAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescript"></a>[<span data-ttu-id="31579-256">TypeScript</span><span class="sxs-lookup"><span data-stu-id="31579-256">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="31579-257">Json</span><span class="sxs-lookup"><span data-stu-id="31579-257">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="31579-258">Python</span><span class="sxs-lookup"><span data-stu-id="31579-258">Python</span></span>](#tab/python)

```python
async def on_teams_team_restored(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The team name is {team_info.name}")
    )
```

---

### <a name="team-archived"></a><span data-ttu-id="31579-259">Team archiviert</span><span class="sxs-lookup"><span data-stu-id="31579-259">Team archived</span></span>

<span data-ttu-id="31579-260">Der Bot erhält eine Benachrichtigung, wenn das Team, in dem er installiert ist, archiviert wird.</span><span class="sxs-lookup"><span data-stu-id="31579-260">The bot receives a notification when the team it is installed in is archived.</span></span> <span data-ttu-id="31579-261">Es empfängt ein `conversationUpdate` Ereignis mit `eventType.teamarchived` im `channelData` Objekt.</span><span class="sxs-lookup"><span data-stu-id="31579-261">It receives a `conversationUpdate` event with `eventType.teamarchived` in the `channelData` object.</span></span>

<span data-ttu-id="31579-262">Der folgende Code zeigt ein Beispiel für ein teamarchiviertes Ereignis:</span><span class="sxs-lookup"><span data-stu-id="31579-262">The following code shows an example of team archived event:</span></span>

# <a name="c"></a>[<span data-ttu-id="31579-263">C#</span><span class="sxs-lookup"><span data-stu-id="31579-263">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamArchivedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescript"></a>[<span data-ttu-id="31579-264">TypeScript</span><span class="sxs-lookup"><span data-stu-id="31579-264">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="31579-265">Json</span><span class="sxs-lookup"><span data-stu-id="31579-265">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="31579-266">Python</span><span class="sxs-lookup"><span data-stu-id="31579-266">Python</span></span>](#tab/python)

```python
async def on_teams_team_archived(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The team name is {team_info.name}")
    )
```

---


### <a name="team-unarchived"></a><span data-ttu-id="31579-267">Team nicht archiviert</span><span class="sxs-lookup"><span data-stu-id="31579-267">Team unarchived</span></span>

<span data-ttu-id="31579-268">Der Bot erhält eine Benachrichtigung, wenn das Team, in dem er installiert ist, nicht archiviert wird.</span><span class="sxs-lookup"><span data-stu-id="31579-268">The bot receives a notification when the team it is installed in is unarchived.</span></span> <span data-ttu-id="31579-269">Es empfängt ein `conversationUpdate` Ereignis mit `eventType.teamUnarchived` im `channelData` Objekt.</span><span class="sxs-lookup"><span data-stu-id="31579-269">It receives a `conversationUpdate` event with `eventType.teamUnarchived` in the `channelData` object.</span></span>

<span data-ttu-id="31579-270">Der folgende Code zeigt ein Beispiel für ein Nichtarchiviertes Teamereignis:</span><span class="sxs-lookup"><span data-stu-id="31579-270">The following code shows an example of team unarchived event:</span></span>

# <a name="c"></a>[<span data-ttu-id="31579-271">C#</span><span class="sxs-lookup"><span data-stu-id="31579-271">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamUnarchivedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescript"></a>[<span data-ttu-id="31579-272">TypeScript</span><span class="sxs-lookup"><span data-stu-id="31579-272">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="31579-273">Json</span><span class="sxs-lookup"><span data-stu-id="31579-273">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="31579-274">Python</span><span class="sxs-lookup"><span data-stu-id="31579-274">Python</span></span>](#tab/python)

```python
async def on_teams_team_unarchived(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The team name is {team_info.name}")
    )
```

---

<span data-ttu-id="31579-275">Nachdem Sie nun mit den Unterhaltungsaktualisierungsereignissen gearbeitet haben, können Sie die Nachrichtenreaktionsereignisse verstehen, die für unterschiedliche Reaktionen auf eine Nachricht auftreten.</span><span class="sxs-lookup"><span data-stu-id="31579-275">Now that you have worked with the conversation update events, you can understand the message reaction events that occur for different reactions to a message.</span></span>

## <a name="message-reaction-events"></a><span data-ttu-id="31579-276">Nachrichtenreaktionsereignisse</span><span class="sxs-lookup"><span data-stu-id="31579-276">Message reaction events</span></span>

<span data-ttu-id="31579-277">Das `messageReaction` Ereignis wird gesendet, wenn ein Benutzer Reaktionen auf eine Nachricht hinzufügt oder entfernt, die von Ihrem Bot gesendet wurde.</span><span class="sxs-lookup"><span data-stu-id="31579-277">The `messageReaction` event is sent when a user adds or removes reactions to a message which was sent by your bot.</span></span> <span data-ttu-id="31579-278">Die `replyToId` enthält die ID der Nachricht und die Art der Reaktion im `Type` Textformat.</span><span class="sxs-lookup"><span data-stu-id="31579-278">The `replyToId` contains the ID of the message, and the `Type` is the type of reaction in text format.</span></span> <span data-ttu-id="31579-279">Die Arten von Reaktionen umfassen Zärtlich, Herz, Heiterkeit, z. B. "Leider" und "Überrascht".</span><span class="sxs-lookup"><span data-stu-id="31579-279">The types of reactions include angry, heart, laugh, like, sad, and surprised.</span></span> <span data-ttu-id="31579-280">Dieses Ereignis enthält nicht den Inhalt der ursprünglichen Nachricht.</span><span class="sxs-lookup"><span data-stu-id="31579-280">This event does not contain the contents of the original message.</span></span> <span data-ttu-id="31579-281">Wenn die Verarbeitung von Reaktionen auf Ihre Nachrichten für Ihren Bot wichtig ist, müssen Sie die Nachrichten beim Senden speichern.</span><span class="sxs-lookup"><span data-stu-id="31579-281">If processing reactions to your messages is important for your bot, you must store the messages when you send them.</span></span> <span data-ttu-id="31579-282">Die folgende Tabelle enthält weitere Informationen zum Ereignistyp und zu Nutzlastobjekten:</span><span class="sxs-lookup"><span data-stu-id="31579-282">The following table provides more information about the event type and payload objects:</span></span>

| <span data-ttu-id="31579-283">EventType</span><span class="sxs-lookup"><span data-stu-id="31579-283">EventType</span></span>       | <span data-ttu-id="31579-284">Payload-Objekt</span><span class="sxs-lookup"><span data-stu-id="31579-284">Payload object</span></span>   | <span data-ttu-id="31579-285">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="31579-285">Description</span></span>                                                             | <span data-ttu-id="31579-286">Bereich</span><span class="sxs-lookup"><span data-stu-id="31579-286">Scope</span></span> |
| --------------- | ---------------- | ----------------------------------------------------------------------- | ----- |
| <span data-ttu-id="31579-287">messageReaction</span><span class="sxs-lookup"><span data-stu-id="31579-287">messageReaction</span></span> | <span data-ttu-id="31579-288">reactionsAdded</span><span class="sxs-lookup"><span data-stu-id="31579-288">reactionsAdded</span></span>   | <span data-ttu-id="31579-289">[Reaktionen zu Bot-Nachricht hinzugefügt.](#reactions-added-to-bot-message)</span><span class="sxs-lookup"><span data-stu-id="31579-289">[Reactions added to bot message](#reactions-added-to-bot-message).</span></span>           | <span data-ttu-id="31579-290">Alle</span><span class="sxs-lookup"><span data-stu-id="31579-290">All</span></span>   |
| <span data-ttu-id="31579-291">messageReaction</span><span class="sxs-lookup"><span data-stu-id="31579-291">messageReaction</span></span> | <span data-ttu-id="31579-292">reactionsRemoved</span><span class="sxs-lookup"><span data-stu-id="31579-292">reactionsRemoved</span></span> | <span data-ttu-id="31579-293">[Reaktionen aus Bot-Nachricht entfernt.](#reactions-removed-from-bot-message)</span><span class="sxs-lookup"><span data-stu-id="31579-293">[Reactions removed from bot message](#reactions-removed-from-bot-message).</span></span> | <span data-ttu-id="31579-294">Alle</span><span class="sxs-lookup"><span data-stu-id="31579-294">All</span></span> |

### <a name="reactions-added-to-bot-message"></a><span data-ttu-id="31579-295">Reaktionen, die zu Bot-Nachrichten hinzugefügt wurden</span><span class="sxs-lookup"><span data-stu-id="31579-295">Reactions added to bot message</span></span>

<span data-ttu-id="31579-296">Der folgende Code zeigt ein Beispiel für Reaktionen auf eine Bot-Nachricht:</span><span class="sxs-lookup"><span data-stu-id="31579-296">The following code shows an example of reactions to a bot message:</span></span>

# <a name="c"></a>[<span data-ttu-id="31579-297">C#</span><span class="sxs-lookup"><span data-stu-id="31579-297">C#</span></span>](#tab/dotnet)

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

# <a name="typescript"></a>[<span data-ttu-id="31579-298">TypeScript</span><span class="sxs-lookup"><span data-stu-id="31579-298">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="31579-299">Json</span><span class="sxs-lookup"><span data-stu-id="31579-299">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="31579-300">Python</span><span class="sxs-lookup"><span data-stu-id="31579-300">Python</span></span>](#tab/python)

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

---

### <a name="reactions-removed-from-bot-message"></a><span data-ttu-id="31579-301">Reaktionen aus Bot-Nachricht entfernt</span><span class="sxs-lookup"><span data-stu-id="31579-301">Reactions removed from bot message</span></span>

<span data-ttu-id="31579-302">Der folgende Code zeigt ein Beispiel für Reaktionen, die aus der Bot-Nachricht entfernt wurden:</span><span class="sxs-lookup"><span data-stu-id="31579-302">The following code shows an example of reactions removed from bot message:</span></span>

# <a name="c"></a>[<span data-ttu-id="31579-303">C#</span><span class="sxs-lookup"><span data-stu-id="31579-303">C#</span></span>](#tab/dotnet)

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

# <a name="typescript"></a>[<span data-ttu-id="31579-304">TypeScript</span><span class="sxs-lookup"><span data-stu-id="31579-304">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="31579-305">Json</span><span class="sxs-lookup"><span data-stu-id="31579-305">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="31579-306">Python</span><span class="sxs-lookup"><span data-stu-id="31579-306">Python</span></span>](#tab/python)

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

---

## <a name="installation-update-event"></a><span data-ttu-id="31579-307">Installationsupdateereignis</span><span class="sxs-lookup"><span data-stu-id="31579-307">Installation update event</span></span>

<span data-ttu-id="31579-308">Der Bot empfängt ein `installationUpdate` Ereignis, wenn Sie einen Bot in einem Unterhaltungsthread installieren.</span><span class="sxs-lookup"><span data-stu-id="31579-308">The bot receives an `installationUpdate` event when you install a bot to a conversation thread.</span></span> <span data-ttu-id="31579-309">Die Deinstallation des Bots aus dem Thread löst auch das Ereignis aus.</span><span class="sxs-lookup"><span data-stu-id="31579-309">Uninstallation of the bot from the thread also triggers the event.</span></span> <span data-ttu-id="31579-310">Bei der Installation eines Bots wird das **Aktionsfeld** im Ereignis so festgelegt, dass *es hinzugefügt* wird, und wenn der Bot deinstalliert wird, wird das **Aktionsfeld** so festgelegt, dass *es entfernt* wird.</span><span class="sxs-lookup"><span data-stu-id="31579-310">On installing a bot, the **action** field in the event is set to *add*, and when the bot is uninstalled the **action** field is set to *remove*.</span></span>
 
> [!NOTE]
> <span data-ttu-id="31579-311">Wenn Sie eine Anwendung aktualisieren und dann einen Bot hinzufügen oder entfernen, löst die Aktion auch das `installationUpdate` Ereignis aus.</span><span class="sxs-lookup"><span data-stu-id="31579-311">When you upgrade an application, and then add or remove a bot, the action also triggers the `installationUpdate` event.</span></span> <span data-ttu-id="31579-312">Das **Aktionsfeld** wird auf *"Add-Upgrade"* festgelegt, wenn Sie einen Bot hinzufügen, oder *"remove-upgrade",* wenn Sie einen Bot entfernen.</span><span class="sxs-lookup"><span data-stu-id="31579-312">The **action** field is set to *add-upgrade* if you add a bot or *remove-upgrade* if you remove a bot.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="31579-313">Installationsupdateereignisse befinden sich heute in der Entwicklervorschau und werden im März 2021 allgemein verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="31579-313">Installation update events are in developer preview today and will be Generally Available (GA) in March 2021.</span></span> <span data-ttu-id="31579-314">Um die Installationsupdateereignisse anzuzeigen, können Sie Ihren Teams-Client in die öffentliche Entwicklervorschau verschieben und Ihre App persönlich oder zu einem Team oder einem Chat hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="31579-314">To see the installation update events, you can move your Teams client to public developer preview, and add your app personally or to a team or a chat.</span></span>

### <a name="install-update-event"></a><span data-ttu-id="31579-315">Updateereignis installieren</span><span class="sxs-lookup"><span data-stu-id="31579-315">Install update event</span></span>
<span data-ttu-id="31579-316">Verwenden Sie das Ereignis, um bei der `installationUpdate` Installation eine Einführungsnachricht von Ihrem Bot zu senden.</span><span class="sxs-lookup"><span data-stu-id="31579-316">Use the `installationUpdate` event to send an introductory message from your bot on installation.</span></span> <span data-ttu-id="31579-317">Dieses Ereignis hilft Ihnen, Ihre Datenschutz- und Datenaufbewahrungsanforderungen zu erfüllen.</span><span class="sxs-lookup"><span data-stu-id="31579-317">This event helps you to meet your privacy and data retention requirements.</span></span> <span data-ttu-id="31579-318">Sie können auch Benutzer- oder Threaddaten bereinigen und löschen, wenn der Bot deinstalliert wird.</span><span class="sxs-lookup"><span data-stu-id="31579-318">You can also clean up and delete user or thread data when the bot is uninstalled.</span></span>

# <a name="c"></a>[<span data-ttu-id="31579-319">C#</span><span class="sxs-lookup"><span data-stu-id="31579-319">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task
OnInstallationUpdateActivityAsync(ITurnContext<IInstallationUpdateActivity> turnContext, CancellationToken cancellationToken) {
var activity = turnContext.Activity; if
(string.Equals(activity.Action, "Add",
StringComparison.InvariantCultureIgnoreCase)) {
// TO:DO Installation workflow }
else
{ // TO:DO Uninstallation workflow
} return; }
```

<span data-ttu-id="31579-320">Sie können auch einen dedizierten Handler zum *Hinzufügen* oder *Entfernen* von Szenarien als alternative Methode verwenden, um ein Ereignis zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="31579-320">You can also use a dedicated handler for *add* or *remove* scenarios as an alternative method to capture an event.</span></span>

```csharp
protected override async Task
OnInstallationUpdateAddAsync(ITurnContext<IInstallationUpdateActivity>
turnContext, CancellationToken cancellationToken) {
// TO:DO Installation workflow return;
}
```

# <a name="typescript"></a>[<span data-ttu-id="31579-321">TypeScript</span><span class="sxs-lookup"><span data-stu-id="31579-321">TypeScript</span></span>](#tab/typescript)

<span data-ttu-id="31579-322">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="31579-322">Not available</span></span>

# <a name="json"></a>[<span data-ttu-id="31579-323">Json</span><span class="sxs-lookup"><span data-stu-id="31579-323">JSON</span></span>](#tab/json)

```json
{ 
  "action": "add", 
  "type": "installationUpdate", 
  "timestamp": "2020-10-20T22:08:07.869Z", 
  "id": "f:3033745319439849398", 
  "channelId": "msteams", 
  "serviceUrl": "https://smba.trafficmanager.net/amer/", 
  "from": { 
    "id": "sample id", 
    "aadObjectId": "sample AAD Object ID" 
  },
  "conversation": { 
    "isGroup": true, 
    "conversationType": "channel", 
    "tenantId": "sample tenant ID", 
    "id": "sample conversation Id@thread.skype" 
  }, 

  "recipient": { 
    "id": "sample reciepent bot ID", 
    "name": "bot name" 
  }, 
  "entities": [ 
    { 
      "locale": "en", 
      "platform": "Windows", 
      "type": "clientInfo" 
    } 
  ], 
  "channelData": { 
    "settings": { 
      "selectedChannel": { 
        "id": "sample channel ID@thread.skype" 
      } 
    }, 
    "channel": { 
      "id": "sample channel ID" 
    }, 
    "team": { 
      "id": "sample team ID" 
    }, 
    "tenant": { 
      "id": "sample tenant ID" 
    }, 
    "source": { 
      "name": "message" 
    } 
  }, 
  "locale": "en" 
}
```

# <a name="python"></a>[<span data-ttu-id="31579-324">Python</span><span class="sxs-lookup"><span data-stu-id="31579-324">Python</span></span>](#tab/python)

<span data-ttu-id="31579-325">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="31579-325">Not available</span></span>

---

## <a name="uninstall-behavior-for-personal-app-with-bot"></a><span data-ttu-id="31579-326">Deinstallationsverhalten für persönliche Apps mit Bot</span><span class="sxs-lookup"><span data-stu-id="31579-326">Uninstall behavior for personal app with bot</span></span>

> [!NOTE]
> <span data-ttu-id="31579-327">Das Deinstallationsverhalten für persönliche Apps mit Bot ist derzeit nur in der [öffentlichen Entwicklervorschau](../../../resources/dev-preview/developer-preview-intro.md)verfügbar.</span><span class="sxs-lookup"><span data-stu-id="31579-327">Uninstall behavior for personal app with bot is currently available only in [public developer preview](../../../resources/dev-preview/developer-preview-intro.md).</span></span>

<span data-ttu-id="31579-328">Wenn Sie eine App deinstallieren, wird der Bot ebenfalls deinstalliert.</span><span class="sxs-lookup"><span data-stu-id="31579-328">When you uninstall an app, the bot is also uninstalled.</span></span> <span data-ttu-id="31579-329">Wenn ein Benutzer eine Nachricht an Ihre App sendet, erhält er den Antwortcode 403.</span><span class="sxs-lookup"><span data-stu-id="31579-329">When a user sends a message to your app, they receive a 403 response code.</span></span> <span data-ttu-id="31579-330">Ihr Bot erhält einen 403-Antwortcode für neue Nachrichten, die von Ihrem Bot gepostet wurden.</span><span class="sxs-lookup"><span data-stu-id="31579-330">Your bot receives a 403 response code for new messages posted by your bot.</span></span> <span data-ttu-id="31579-331">Das Verhalten der Postdeinstallation für Bots im persönlichen Bereich mit den Bereichen Teams und groupChat wird nun ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="31579-331">The post uninstall behavior for bots in the personal scope with the Teams and groupChat scopes are now aligned.</span></span> <span data-ttu-id="31579-332">Sie können keine Nachrichten senden oder empfangen, nachdem eine App deinstalliert wurde.</span><span class="sxs-lookup"><span data-stu-id="31579-332">You cannot send or receive messages after an app has been uninstalled.</span></span>

<img src="~/assets/images/bots/uninstallbot.png" alt="Uninstall event" width="900" height="900"/>

## <a name="event-handling-for-install-and-uninstall-events"></a><span data-ttu-id="31579-333">Ereignisbehandlung für Installations- und Deinstallationsereignisse</span><span class="sxs-lookup"><span data-stu-id="31579-333">Event handling for install and uninstall events</span></span>

<span data-ttu-id="31579-334">Wenn Sie diese Installations- und Deinstallationsereignisse verwenden, gibt es einige Fälle, in denen Bots Ausnahmen beim Empfangen unerwarteter Ereignisse von Teams gewähren.</span><span class="sxs-lookup"><span data-stu-id="31579-334">When you use these install and uninstall events, there are some instances where bots give exceptions on receiving unexpected events from Teams.</span></span> <span data-ttu-id="31579-335">Dies geschieht in den folgenden Fällen:</span><span class="sxs-lookup"><span data-stu-id="31579-335">This occurs in the following cases:</span></span>

* <span data-ttu-id="31579-336">Sie erstellen Ihren Bot ohne das Microsoft Bot Framework SDK, und daher gibt der Bot eine Ausnahme beim Empfangen eines unerwarteten Ereignisses.</span><span class="sxs-lookup"><span data-stu-id="31579-336">You build your bot without the Microsoft Bot Framework SDK, and as a result the bot gives an exception on receiving an unexpected event.</span></span>
* <span data-ttu-id="31579-337">Sie erstellen Ihren Bot mit dem Microsoft Bot Framework SDK, und Sie können das Standardereignisverhalten ändern, indem Sie das Basisereignishandle überschreiben.</span><span class="sxs-lookup"><span data-stu-id="31579-337">You build your bot with the Microsoft Bot Framework SDK, and you select to alter the default event behavior by overriding the base event handle.</span></span>

<span data-ttu-id="31579-338">Es ist wichtig zu wissen, dass neue Ereignisse jederzeit in der Zukunft hinzugefügt werden können und Ihr Bot beginnt, sie zu empfangen.</span><span class="sxs-lookup"><span data-stu-id="31579-338">It is important to know that new events can be added anytime in the future and your bot begins to receive them.</span></span> <span data-ttu-id="31579-339">Daher müssen Sie die Möglichkeit entwerfen, unerwartete Ereignisse zu empfangen.</span><span class="sxs-lookup"><span data-stu-id="31579-339">So you must design for the possibility of receiving unexpected events.</span></span> <span data-ttu-id="31579-340">Wenn Sie das Bot Framework SDK verwenden, antwortet Ihr Bot automatisch mit einem 200 – OK auf alle Ereignisse, die Sie nicht behandeln möchten.</span><span class="sxs-lookup"><span data-stu-id="31579-340">If you are using the Bot Framework SDK, your bot automatically responds with a 200 – OK to any events you do not choose to handle.</span></span>

## <a name="code-sample"></a><span data-ttu-id="31579-341">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="31579-341">Code sample</span></span>

| <span data-ttu-id="31579-342">**Beispielname**</span><span class="sxs-lookup"><span data-stu-id="31579-342">**Sample name**</span></span> | <span data-ttu-id="31579-343">**Description**</span><span class="sxs-lookup"><span data-stu-id="31579-343">**Description**</span></span> | <span data-ttu-id="31579-344">**.NET**</span><span class="sxs-lookup"><span data-stu-id="31579-344">**.NET**</span></span> | <span data-ttu-id="31579-345">**Node.js**</span><span class="sxs-lookup"><span data-stu-id="31579-345">**Node.js**</span></span> | <span data-ttu-id="31579-346">**Python**</span><span class="sxs-lookup"><span data-stu-id="31579-346">**Python**</span></span> |
|----------|-----------------|----------|
| <span data-ttu-id="31579-347">Unterhaltungsbot</span><span class="sxs-lookup"><span data-stu-id="31579-347">Conversation bot</span></span> | <span data-ttu-id="31579-348">Beispielcode für Bots-Unterhaltungsereignisse.</span><span class="sxs-lookup"><span data-stu-id="31579-348">Sample code for bots conversation events.</span></span> | [<span data-ttu-id="31579-349">View</span><span class="sxs-lookup"><span data-stu-id="31579-349">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot)  | [<span data-ttu-id="31579-350">View</span><span class="sxs-lookup"><span data-stu-id="31579-350">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/57.teams-conversation-bot) | [<span data-ttu-id="31579-351">View</span><span class="sxs-lookup"><span data-stu-id="31579-351">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/57.teams-conversation-bot) |

## <a name="next-step"></a><span data-ttu-id="31579-352">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="31579-352">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="31579-353">Senden proaktiver Nachrichten</span><span class="sxs-lookup"><span data-stu-id="31579-353">Send proactive messages</span></span>](~/bots/how-to/conversations/send-proactive-messages.md)
