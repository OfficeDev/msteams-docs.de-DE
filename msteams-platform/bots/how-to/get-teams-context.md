---
title: Abrufen des spezifischen Kontexts des Teams für Ihren bot
author: clearab
description: Hier erfahren Sie, wie Sie den spezifischen Kontext des Microsoft Teams für Ihren bot abrufen, einschließlich der Liste der Unterhaltungen, Details und Kanäle.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 9f70e3e052903365f03c541db83f196f33fc2322
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674468"
---
# <a name="get-teams-specific-context-for-your-bot"></a><span data-ttu-id="368e6-103">Abrufen des spezifischen Kontexts des Teams für Ihren bot</span><span class="sxs-lookup"><span data-stu-id="368e6-103">Get Team's specific context for your bot</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="368e6-104">Ein Bot kann auf zusätzliche Kontextdaten zu einem Team oder Chat zugreifen, in dem es installiert ist.</span><span class="sxs-lookup"><span data-stu-id="368e6-104">A bot can access additional context data about a team or chat it is installed in.</span></span> <span data-ttu-id="368e6-105">Diese Informationen können verwendet werden, um die Funktionalität des bot zu bereichern und eine personalisierte Erfahrung zu bieten.</span><span class="sxs-lookup"><span data-stu-id="368e6-105">This information can be used to enrich the bot's functionality and provide a more personalized experience.</span></span>

## <a name="fetching-the-roster-or-user-profile"></a><span data-ttu-id="368e6-106">Abrufen des Dienstplan-oder Benutzerprofils</span><span class="sxs-lookup"><span data-stu-id="368e6-106">Fetching the roster or user profile</span></span>

<span data-ttu-id="368e6-107">Ihr Bot kann eine Abfrage nach der Liste der Mitglieder und ihren grundlegenden Profilen durchführen, einschließlich Microsoft Teams-Benutzer-IDs und Azure Active Directory Informationen (Azure AD) wie Name und ObjectID.</span><span class="sxs-lookup"><span data-stu-id="368e6-107">Your bot can query for the list of members and their basic profiles, including Teams user IDs and Azure Active Directory (Azure AD) information such as name and objectId.</span></span> <span data-ttu-id="368e6-108">Sie können diese Informationen verwenden, um Benutzeridentitäten zu korrelieren, beispielsweise um zu überprüfen, ob ein Benutzer, der bei einer Registerkarte über Azure AD Anmeldeinformationen angemeldet ist, Mitglied des Teams ist.</span><span class="sxs-lookup"><span data-stu-id="368e6-108">You can use this information to correlate user identities, e.g., to check whether a user, logged into a tab through Azure AD credentials, is a member of the team.</span></span> <span data-ttu-id="368e6-109">Sie können diesen Anruf auch in einem 1:1-Chat verwenden, um zusätzliche Informationen zu Ihrem Benutzer zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="368e6-109">You can also use this call in a one-to-one chat to gain additional information about your user.</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="368e6-110">C#-/.net</span><span class="sxs-lookup"><span data-stu-id="368e6-110">C#/.NET</span></span>](#tab/dotnet)

```csharp
public class MyBot : TeamsActivityHandler
{
    protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
    {
        IEnumerable<TeamsChannelAccount> members = await TeamsInfo.GetMembersAsync(turnContext, cancellationToken);
    }
}
```

# <a name="typescriptnodejstabtypescript"></a>[<span data-ttu-id="368e6-111">Manuskript/Node. js</span><span class="sxs-lookup"><span data-stu-id="368e6-111">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();

        // See https://aka.ms/about-bot-activity-message to learn more about the message and other activity types.
        this.onMessage(async (turnContext, next) => {
            const members = await TeamsInfo.getMembers(turnContext);

            // By calling next() you ensure that the next BotHandler is run.
            await next();
        });
    }
}
```

# <a name="jsontabjson"></a>[<span data-ttu-id="368e6-112">Json</span><span class="sxs-lookup"><span data-stu-id="368e6-112">JSON</span></span>](#tab/json)
<span data-ttu-id="368e6-113">Sie können eine get `/v3/conversations/{teamId}/members/`-Anforderung direkt unter Verwendung des Werts von `serviceUrl` als Endpunkt ausgeben.</span><span class="sxs-lookup"><span data-stu-id="368e6-113">You can directly issue a GET request on `/v3/conversations/{teamId}/members/`, using the value of `serviceUrl` as the endpoint.</span></span> <span data-ttu-id="368e6-114">Der Wert von `serviceUrl` neigt dazu, stabil zu sein, aber kann sich ändern.</span><span class="sxs-lookup"><span data-stu-id="368e6-114">The value of `serviceUrl` tends to be stable but can change.</span></span> <span data-ttu-id="368e6-115">Wenn eine neue Nachricht eingeht, sollte Ihr bot den gespeicherten Wert für `serviceUrl`überprüfen.</span><span class="sxs-lookup"><span data-stu-id="368e6-115">When a new message arrives, your bot should verify its stored value for `serviceUrl`.</span></span>

```http
GET /v3/conversations/19:ja0cu120i1jod12j@skype.net/members

Response body
[{
    "id": "29:1GcS4EyB_oSI8A88XmWBN7NJFyMqe3QGnJdgLfFGkJnVelzRGos0bPbpsfJjcbAD22bmKc4GMbrY2g4JDrrA8vM06X1-cHHle4zOE6U4ttcc",
    "objectId": "9d3e08f9-a7ae-43aa-a4d3-de3f319a8a9c",
    "givenName": "Larry",
    "surname": "Brown",
    "email": "Larry.Brown@fabrikam.com",
    "userPrincipalName": "labrown@fabrikam.com"
}, {
    "id": "29:1bSnHZ7Js2STWrgk6ScEErLk1Lp2zQuD5H2qQ960rtvstKp8tKLl-3r8b6DoW0QxZimuTxk_kupZ1DBMpvIQQUAZL-PNj0EORDvRZXy8kvWk",
    "objectId": "76b0b09f-d410-48fd-993e-84da521a597b",
    "givenName": "John",
    "surname": "Patterson",
    "email": "johnp@fabrikam.com",
    "userPrincipalName": "johnp@fabrikam.com"
}, {
    "id": "29:1URzNQM1x1PNMr1D7L5_lFe6qF6gEfAbkdG8_BUxOW2mTKryQqEZtBTqDt10-MghkzjYDuUj4KG6nvg5lFAyjOLiGJ4jzhb99WrnI7XKriCs",
    "objectId": "6b7b3b2a-2c4b-4175-8582-41c9e685c1b5",
    "givenName": "Rick",
    "surname": "Stevens",
    "email": "Rick.Stevens@fabrikam.com",
    "userPrincipalName": "rstevens@fabrikam.com"
}]
```

# <a name="pythontabpython"></a>[<span data-ttu-id="368e6-116">Python</span><span class="sxs-lookup"><span data-stu-id="368e6-116">Python</span></span>](#tab/python)

```python
async def _show_members(
    self, turn_context: TurnContext
):
    members = await TeamsInfo.get_team_members(turn_context)
```

* * *

## <a name="get-teams-details"></a><span data-ttu-id="368e6-117">Teamdetails abrufen</span><span class="sxs-lookup"><span data-stu-id="368e6-117">Get team's details</span></span>

<span data-ttu-id="368e6-118">Wenn Ihr bot in einem Team installiert ist, kann er Metadaten zu diesem Teamabfragen, einschließlich der Azure Ad Gruppen-Nr.</span><span class="sxs-lookup"><span data-stu-id="368e6-118">When installed in a team, your bot can query for metadata about that team including the Azure AD groupId.</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="368e6-119">C#-/.net</span><span class="sxs-lookup"><span data-stu-id="368e6-119">C#/.NET</span></span>](#tab/dotnet)

```csharp
public class MyBot : TeamsActivityHandler
{
    protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
    {
        TeamDetails teamDetails = await TeamsInfo.GetTeamDetailsAsync(turnContext, turnContext.Activity.TeamsGetTeamInfo().Id, cancellationToken);
        if (teamDetails != null) {
            await turnContext.SendActivityAsync($"The groupId is: {teamDetails.AadGroupId}");
        }
        else {
            await turnContext.SendActivityAsync($"Message did not come from a channel in a team.");
        }
    }
}
```

# <a name="typescriptnodejstabtypescript"></a>[<span data-ttu-id="368e6-120">Manuskript/Node. js</span><span class="sxs-lookup"><span data-stu-id="368e6-120">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();

        // See https://aka.ms/about-bot-activity-message to learn more about the message and other activity types.
        this.onMessage(async (turnContext, next) => {
            const teamDetails = await TeamsInfo.getTeamDetails(turnContext);
            if (teamDetails) {
                await turnContext.sendActivity(`The group ID is: ${teamDetails.aadGroupId}`);
            } else {
                await turnContext.sendActivity('This message did not come from a channel in a team.');
            }

            // By calling next() you ensure that the next BotHandler is run.
            await next();
        });
    }
}
```

# <a name="jsontabjson"></a>[<span data-ttu-id="368e6-121">Json</span><span class="sxs-lookup"><span data-stu-id="368e6-121">JSON</span></span>](#tab/json)

<span data-ttu-id="368e6-122">Sie können eine get `/v3/teams/{teamId}`-Anforderung direkt unter Verwendung des Werts von `serviceUrl` als Endpunkt ausgeben.</span><span class="sxs-lookup"><span data-stu-id="368e6-122">You can directly issue a GET request on `/v3/teams/{teamId}`, using the value of `serviceUrl` as the endpoint.</span></span> <span data-ttu-id="368e6-123">Der Wert von `serviceUrl` neigt dazu, stabil zu sein, aber kann sich ändern.</span><span class="sxs-lookup"><span data-stu-id="368e6-123">The value of `serviceUrl` tends to be stable but can change.</span></span> <span data-ttu-id="368e6-124">Wenn eine neue Nachricht eingeht, sollte Ihr bot den gespeicherten Wert für `serviceUrl`überprüfen.</span><span class="sxs-lookup"><span data-stu-id="368e6-124">When a new message arrives, your bot should verify its stored value for `serviceUrl`.</span></span>

```http
GET /v3/teams/19:ja0cu120i1jod12j@skype.net

Response body
{
    "id": "29:1GcS4EyB_oSI8A88XmWBN7NJFyMqe3QGnJdgLfFGkJnVelzRGos0bPbpsfJjcbAD22bmKc4GMbrY2g4JDrrA8vM06X1-cHHle4zOE6U4ttcc",
    "name": "The Team Name",
    "aadGroupId": "02ce3874-dd86-41ba-bddc-013f34019978"
}
```

# <a name="pythontabpython"></a>[<span data-ttu-id="368e6-125">Python</span><span class="sxs-lookup"><span data-stu-id="368e6-125">Python</span></span>](#tab/python)

```python
async def _show_details(self, turn_context: TurnContext):
    team_details = await TeamsInfo.get_team_details(turn_context)
    reply = MessageFactory.text(f"The team name is {team_details.name}. The team ID is {team_details.id}. The AADGroupID is {team_details.aad_group_id}.")
    await turn_context.send_activity(reply)
```

* * *

## <a name="get-the-list-of-channels-in-a-team"></a><span data-ttu-id="368e6-126">Abrufen der Liste der Kanäle in einem Team</span><span class="sxs-lookup"><span data-stu-id="368e6-126">Get the list of channels in a team</span></span>

<span data-ttu-id="368e6-127">Ihr Bot kann die Liste der Kanäle in einem Teamabfragen.</span><span class="sxs-lookup"><span data-stu-id="368e6-127">Your bot can query the list of channels in a team.</span></span>

> [!NOTE]
>
>* <span data-ttu-id="368e6-128">Der Name des standardmäßigen allgemeinen Kanals wird `null` zurückgegeben, um die Lokalisierung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="368e6-128">The name of the default General channel is returned as `null` to allow for localization.</span></span>
>* <span data-ttu-id="368e6-129">Die Kanal-ID für den allgemeinen Kanal stimmt immer mit der Team-ID überein.</span><span class="sxs-lookup"><span data-stu-id="368e6-129">The channel ID for the General channel always matches the team ID.</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="368e6-130">C#-/.net</span><span class="sxs-lookup"><span data-stu-id="368e6-130">C#/.NET</span></span>](#tab/dotnet)

```csharp
public class MyBot : TeamsActivityHandler
{
    protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
    {
        IEnumerable<ChannelInfo> channels = await TeamsInfo.GetTeamChannelsAsync(turnContext, turnContext.Activity.TeamsGetTeamInfo().Id, cancellationToken);

        await turnContext.SendActivityAsync($"The channel count is: {channels.Count()}");
    }
}
```

# <a name="typescriptnodejstabtypescript"></a>[<span data-ttu-id="368e6-131">Manuskript/Node. js</span><span class="sxs-lookup"><span data-stu-id="368e6-131">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();

        // See https://aka.ms/about-bot-activity-message to learn more about the message and other activity types.
        this.onMessage(async (turnContext, next) => {
            const channels = await TeamsInfo.getTeamChannels(turnContext);

            await turnContext.sendActivity(`The channel count is: ${channels.length}`);

            // By calling next() you ensure that the next BotHandler is run.
            await next();
        });
    }
}
```

# <a name="jsontabjson"></a>[<span data-ttu-id="368e6-132">Json</span><span class="sxs-lookup"><span data-stu-id="368e6-132">JSON</span></span>](#tab/json)

<span data-ttu-id="368e6-133">Sie können eine get `/v3/teams/{teamId}/conversations`-Anforderung direkt unter Verwendung des Werts von `serviceUrl` als Endpunkt ausgeben.</span><span class="sxs-lookup"><span data-stu-id="368e6-133">You can directly issue a GET request on `/v3/teams/{teamId}/conversations`, using the value of `serviceUrl` as the endpoint.</span></span> <span data-ttu-id="368e6-134">Der Wert von `serviceUrl` neigt dazu, stabil zu sein, aber kann sich ändern.</span><span class="sxs-lookup"><span data-stu-id="368e6-134">The value of `serviceUrl` tends to be stable but can change.</span></span> <span data-ttu-id="368e6-135">Wenn eine neue Nachricht eingeht, sollte Ihr bot den gespeicherten Wert für `serviceUrl`überprüfen.</span><span class="sxs-lookup"><span data-stu-id="368e6-135">When a new message arrives, your bot should verify its stored value for `serviceUrl`.</span></span>

```http
GET /v3/teams/19%3A033451497ea84fcc83d17ed7fb08a1b6%40thread.skype/conversations

Response body
{
    "conversations": [{
        "id": "19:033451497ea84fcc83d17ed7fb08a1b6@thread.skype",
        "name": null
    }, {
        "id": "19:cc25e4aae50746ecbb11473bba24c70a@thread.skype",
        "name": "Materials"
    }, {
        "id": "19:b7b84cba410c406ba671dbbf5e0a3519@thread.skype",
        "name": "Design"
    }, {
        "id": "19:fc5db2aed489454e8f8c06829ed6c986@thread.skype",
        "name": "Marketing"
    }]
}
```


# <a name="pythontabpython"></a>[<span data-ttu-id="368e6-136">Python</span><span class="sxs-lookup"><span data-stu-id="368e6-136">Python</span></span>](#tab/python)

```python
async def _show_channels(
    self, turn_context: TurnContext
):
    channels = await TeamsInfo.get_team_channels(turn_context)
    reply = MessageFactory.text(f"Total of {len(channels)} channels are currently in team")
    await turn_context.send_activity(reply)
```

* * *

[!INCLUDE [sample](~/includes/bots/teams-bot-samples.md)]
