---
title: Abrufen des spezifischen Kontexts des Teams für Ihren bot
author: laujan
description: Hier erfahren Sie, wie Sie den spezifischen Kontext des Microsoft Teams für Ihren bot abrufen, einschließlich der Liste der Unterhaltungen, Details und Kanäle.
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: 36ec992e009a7f45064021ae1235b159d100b9cd
ms.sourcegitcommit: 3fc7ad33e2693f07170c3cb1a0d396261fc5c619
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "48796344"
---
# <a name="get-teams-specific-context-for-your-bot"></a><span data-ttu-id="48a15-103">Abrufen des spezifischen Kontexts des Teams für Ihren bot</span><span class="sxs-lookup"><span data-stu-id="48a15-103">Get Team's specific context for your bot</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="48a15-104">Ein Bot kann auf zusätzliche Kontextdaten zu einem Team oder Chat zugreifen, in dem es installiert ist.</span><span class="sxs-lookup"><span data-stu-id="48a15-104">A bot can access additional context data about a team or chat it is installed in.</span></span> <span data-ttu-id="48a15-105">Diese Informationen können verwendet werden, um die Funktionalität des bot zu bereichern und eine personalisierte Erfahrung zu bieten.</span><span class="sxs-lookup"><span data-stu-id="48a15-105">This information can be used to enrich the bot's functionality and provide a more personalized experience.</span></span>

## <a name="fetching-the-roster-or-user-profile"></a><span data-ttu-id="48a15-106">Abrufen des Dienstplan-oder Benutzerprofils</span><span class="sxs-lookup"><span data-stu-id="48a15-106">Fetching the roster or user profile</span></span>

<span data-ttu-id="48a15-107">Ihr Bot kann eine Abfrage nach der Liste der Mitglieder und ihren grundlegenden Profilen durchführen, einschließlich Microsoft Teams-Benutzer-IDs und Azure Active Directory Informationen (Azure AD) wie Name und ObjectID.</span><span class="sxs-lookup"><span data-stu-id="48a15-107">Your bot can query for the list of members and their basic profiles, including Teams user IDs and Azure Active Directory (Azure AD) information such as name and objectId.</span></span> <span data-ttu-id="48a15-108">Sie können diese Informationen verwenden, um Benutzeridentitäten zu korrelieren, beispielsweise um zu überprüfen, ob ein Benutzer, der bei einer Registerkarte über Azure AD Anmeldeinformationen angemeldet ist, Mitglied des Teams ist.</span><span class="sxs-lookup"><span data-stu-id="48a15-108">You can use this information to correlate user identities, e.g., to check whether a user, logged into a tab through Azure AD credentials, is a member of the team.</span></span> <span data-ttu-id="48a15-109">Im folgenden Beispielcode wird der ausgelagerte Endpunkt zum Abrufen der Liste verwendet.</span><span class="sxs-lookup"><span data-stu-id="48a15-109">The sample code below uses the paged endpoint for retrieving the roster.</span></span> <span data-ttu-id="48a15-110">Obwohl Sie die nicht ausgelagerte Version möglicherweise weiterhin verwenden, ist Sie in großen Teams unzuverlässig und sollte nicht verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="48a15-110">Although you may still use the non-paged version, it will be unreliable in large teams and should not be used.</span></span> <span data-ttu-id="48a15-111">Weitere Informationen finden Sie in [diesem Artikel](~/resources/team-chat-member-api-changes.md) .</span><span class="sxs-lookup"><span data-stu-id="48a15-111">See [this article](~/resources/team-chat-member-api-changes.md) for additional information.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="48a15-112">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="48a15-112">C#/.NET</span></span>](#tab/dotnet)

```csharp
public class MyBot : TeamsActivityHandler
{
    protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
    {
        var members = new List<TeamsChannelAccount>();
        string continuationToken = null;

        do
        {
            var currentPage = await TeamsInfo.GetPagedMembersAsync(turnContext, 100, continuationToken, cancellationToken);
            continuationToken = currentPage.ContinuationToken;
            members.AddRange(currentPage.Members);
         }
         while (continuationToken != null);
     }
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="48a15-113">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="48a15-113">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();

        // See https://aka.ms/about-bot-activity-message to learn more about the message and other activity types.
        this.onMessage(async (turnContext, next) => {
            var continuationToken;
            var members = [];

            do {
                var pagedMembers = await TeamsInfo.getPagedMembers(context, 100, continuationToken);
                continuationToken = pagedMembers.continuationToken;
                members.push(...pagedMembers.members);
            }
            while(continuationToken !== undefined)

            // By calling next() you ensure that the next BotHandler is run.
            await next();
        });
    }
}
```

# <a name="python"></a>[<span data-ttu-id="48a15-114">Python</span><span class="sxs-lookup"><span data-stu-id="48a15-114">Python</span></span>](#tab/python)

```python
async def _show_members(
    self, turn_context: TurnContext
):
    members = await TeamsInfo.get_team_members(turn_context)
```

# <a name="json"></a>[<span data-ttu-id="48a15-115">Json</span><span class="sxs-lookup"><span data-stu-id="48a15-115">JSON</span></span>](#tab/json)

<span data-ttu-id="48a15-116">Sie können eine GET-Anforderung direkt unter `/v3/conversations/{conversationId}/pagedmembers?pageSize={pageSize}&continuationToken={continuationToken}` Verwendung des Werts von `serviceUrl` als Endpunkt ausgeben.</span><span class="sxs-lookup"><span data-stu-id="48a15-116">You can directly issue a GET request on `/v3/conversations/{conversationId}/pagedmembers?pageSize={pageSize}&continuationToken={continuationToken}`, using the value of `serviceUrl` as the endpoint.</span></span> <span data-ttu-id="48a15-117">Der Wert von `serviceUrl` neigt dazu, stabil zu sein, aber kann sich ändern.</span><span class="sxs-lookup"><span data-stu-id="48a15-117">The value of `serviceUrl` tends to be stable but can change.</span></span> <span data-ttu-id="48a15-118">Wenn eine neue Nachricht eingeht, sollte Ihr bot den gespeicherten Wert für überprüfen `serviceUrl` .</span><span class="sxs-lookup"><span data-stu-id="48a15-118">When a new message arrives, your bot should verify its stored value for `serviceUrl`.</span></span> <span data-ttu-id="48a15-119">Die Antwort Nutzlast gibt außerdem an, ob der Benutzer ein normaler oder anonymer Benutzer ist.</span><span class="sxs-lookup"><span data-stu-id="48a15-119">The response payload will also indicate if the user is a regular or anonymous user.</span></span>

```http
GET /v3/conversations/19:meeting_N2QzYTA3YmItYmMwOC00OTJmLThkYzMtZWMzZGU0NGIyZGI0@thread.v2/pagedmembers?pageSize=100&continuationToken=asdfasdfalkdsjfalksjdf

Response body
{
   "continuationToken":"asdfqwerueiqpiewr",
   "members":[
      {
         "id":"29:1GcS4EyB_oSI8A88XmWBN7NJFyMqe3QGnJdgLfFGkJnVelzRGos0bPbpsfJjcbAD22bmKc4GMbrY2g4JDrrA8vM06X1-cHHle4zOE6U4ttcc",
         "name":"Anon1 (Guest)",
         "tenantId":"29:1UX7p8Fkx7p93MZlBFS71swTB9juQOCfnXf2L3wxOUITCcIGpFcRX-JiFjLDVZhxGpEfzSTGNsZeEyTKr1iu3Vw",
         "userRole":"anonymous"
      },
      {
         "id":"29:1bSnHZ7Js2STWrgk6ScEErLk1Lp2zQuD5H2qQ960rtvstKp8tKLl-3r8b6DoW0QxZimuTxk_kupZ1DBMpvIQQUAZL-PNj0EORDvRZXy8kvWk",
         "objectId":"76b0b09f-d410-48fd-993e-84da521a597b",
         "givenName":"John",
         "surname":"Patterson",
         "email":"johnp@fabrikam.com",
         "userPrincipalName":"johnp@fabrikam.com",
         "tenantId":"29:1UX7p8Fkx7p93MZlBFS71swTB9juQOCfnXf2L3wxOUITCcIGpFcRX-JiFjLDVZhxGpEfzSTGNsZeEyTKr1iu3Vw",
         "userRole":"user"
      },
      {
         "id":"29:1URzNQM1x1PNMr1D7L5_lFe6qF6gEfAbkdG8_BUxOW2mTKryQqEZtBTqDt10-MghkzjYDuUj4KG6nvg5lFAyjOLiGJ4jzhb99WrnI7XKriCs",
         "objectId":"6b7b3b2a-2c4b-4175-8582-41c9e685c1b5",
         "givenName":"Rick",
         "surname":"Stevens",
         "email":"Rick.Stevens@fabrikam.com",
         "userPrincipalName":"rstevens@fabrikam.com",
         "tenantId":"29:1UX7p8Fkx7p93MZlBFS71swTB9juQOCfnXf2L3wxOUITCcIGpFcRX-JiFjLDVZhxGpEfzSTGNsZeEyTKr1iu3Vw",
         "userRole":"user"
      }
   ]
}
```

* * *

## <a name="get-single-member-details"></a><span data-ttu-id="48a15-120">Einzelne Element Details abrufen</span><span class="sxs-lookup"><span data-stu-id="48a15-120">Get single member details</span></span>

<span data-ttu-id="48a15-121">Sie können die Details eines bestimmten Benutzers auch mithilfe der jeweiligen Teams-Benutzer-ID, UPN-oder Aad-Objekt-ID abrufen.</span><span class="sxs-lookup"><span data-stu-id="48a15-121">You can also retrieve the details of a particular user using their Teams user Id, UPN, or AAD Object Id.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="48a15-122">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="48a15-122">C#/.NET</span></span>](#tab/dotnet)

```csharp
public class MyBot : TeamsActivityHandler
{
    protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
    {
        var member = await TeamsInfo.GetMemberAsync(turnContext, turnContext.Activity.From.Id, cancellationToken);
    }
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="48a15-123">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="48a15-123">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();

        // See https://aka.ms/about-bot-activity-message to learn more about the message and other activity types.
        const member = await TeamsInfo.getMember(context, encodeURI('someone@somecompany.com'));

        // By calling next() you ensure that the next BotHandler is run.
        await next();
        });
    }
}
```

# <a name="python"></a>[<span data-ttu-id="48a15-124">Python</span><span class="sxs-lookup"><span data-stu-id="48a15-124">Python</span></span>](#tab/python)

```python
async def _show_members(
    self, turn_context: TurnContext
):
    member = TeamsInfo.get_member(turn_context, turn_context.activity.from_property.id)
```

# <a name="json"></a>[<span data-ttu-id="48a15-125">Json</span><span class="sxs-lookup"><span data-stu-id="48a15-125">JSON</span></span>](#tab/json)

<span data-ttu-id="48a15-126">Sie können eine GET-Anforderung direkt unter `/v3/conversations/{conversationId}/members/{userId}` Verwendung des Werts von `serviceUrl` als Endpunkt ausgeben.</span><span class="sxs-lookup"><span data-stu-id="48a15-126">You can directly issue a GET request on `/v3/conversations/{conversationId}/members/{userId}`, using the value of `serviceUrl` as the endpoint.</span></span> <span data-ttu-id="48a15-127">Der Wert von `serviceUrl` neigt dazu, stabil zu sein, aber kann sich ändern.</span><span class="sxs-lookup"><span data-stu-id="48a15-127">The value of `serviceUrl` tends to be stable but can change.</span></span> <span data-ttu-id="48a15-128">Wenn eine neue Nachricht eingeht, sollte Ihr bot den gespeicherten Wert für überprüfen `serviceUrl` .</span><span class="sxs-lookup"><span data-stu-id="48a15-128">When a new message arrives, your bot should verify its stored value for `serviceUrl`.</span></span> <span data-ttu-id="48a15-129">Dies kann für Benutzer und anonyme Benutzer verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="48a15-129">This can be used for regualr users and anonymous users.</span></span>

<span data-ttu-id="48a15-130">Im folgenden finden Sie ein Antwortbeispiel für reguläre Benutzer.</span><span class="sxs-lookup"><span data-stu-id="48a15-130">Below is a response sample for regular user</span></span>

```http
GET /v3/conversations/19:ja0cu120i1jod12j@skype.net/members/29:1GcS4EyB_oSI8A88XmWBN7NJFyMqe3QGnJdgLfFGkJnVelzRGos0bPbpsfJjcbAD22bmKc4GMbrY2g4JDrrA8vM06X1-cHHle4zOE6U4ttcc

Response body
{
    "id": "29:1GcS4EyB_oSI8A88XmWBN7NJFyMqe3QGnJdgLfFGkJnVelzRGos0bPbpsfJjcbAD22bmKc4GMbrY2g4JDrrA8vM06X1-cHHle4zOE6U4ttcc",
    "objectId": "9d3e08f9-a7ae-43aa-a4d3-de3f319a8a9c",
    "givenName": "Larry",
    "surname": "Brown",
    "email": "Larry.Brown@fabrikam.com",
    "userPrincipalName": "labrown@fabrikam.com",
    "tenantId":"72f988bf-86f1-41af-91ab-2d7cd011db47", 
    "userRole":"user"
}
```

<span data-ttu-id="48a15-131">Unten ist die Antwort für anonyme Benutzer</span><span class="sxs-lookup"><span data-stu-id="48a15-131">Below is response for anonymous user</span></span>

```http
GET /v3/conversations/19:ja0cu120i1jod12j@skype.net/members/<anonymous user id>"

Response body
{
    "id": "29:1GcS4EyB_oSI8A88XmWBN7NJFyMqe3QGnJdgLfFGkJnVelzRGos0bPbpsfJjcbAD22bmKc4GMbrY2g4JDrrA8vM06X1-cHHle4zOE6U4ttcc",
    "name": "Anon1 (Guest)",
    "tenantId":"72f988bf-86f1-41af-91ab-2d7cd011db47", 
    "userRole":"anonymous"
}
```

* * *

## <a name="get-teams-details"></a><span data-ttu-id="48a15-132">Teamdetails abrufen</span><span class="sxs-lookup"><span data-stu-id="48a15-132">Get team's details</span></span>

<span data-ttu-id="48a15-133">Wenn Ihr bot in einem Team installiert ist, kann er Metadaten zu diesem Teamabfragen, einschließlich der Azure Ad Gruppen-Nr.</span><span class="sxs-lookup"><span data-stu-id="48a15-133">When installed in a team, your bot can query for metadata about that team including the Azure AD groupId.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="48a15-134">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="48a15-134">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="48a15-135">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="48a15-135">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="python"></a>[<span data-ttu-id="48a15-136">Python</span><span class="sxs-lookup"><span data-stu-id="48a15-136">Python</span></span>](#tab/python)

```python
async def _show_details(self, turn_context: TurnContext):
    team_details = await TeamsInfo.get_team_details(turn_context)
    reply = MessageFactory.text(f"The team name is {team_details.name}. The team ID is {team_details.id}. The AADGroupID is {team_details.aad_group_id}.")
    await turn_context.send_activity(reply)
```

# <a name="json"></a>[<span data-ttu-id="48a15-137">Json</span><span class="sxs-lookup"><span data-stu-id="48a15-137">JSON</span></span>](#tab/json)

<span data-ttu-id="48a15-138">Sie können eine GET-Anforderung direkt unter `/v3/teams/{teamId}` Verwendung des Werts von `serviceUrl` als Endpunkt ausgeben.</span><span class="sxs-lookup"><span data-stu-id="48a15-138">You can directly issue a GET request on `/v3/teams/{teamId}`, using the value of `serviceUrl` as the endpoint.</span></span> <span data-ttu-id="48a15-139">Der Wert von `serviceUrl` neigt dazu, stabil zu sein, aber kann sich ändern.</span><span class="sxs-lookup"><span data-stu-id="48a15-139">The value of `serviceUrl` tends to be stable but can change.</span></span> <span data-ttu-id="48a15-140">Wenn eine neue Nachricht eingeht, sollte Ihr bot den gespeicherten Wert für überprüfen `serviceUrl` .</span><span class="sxs-lookup"><span data-stu-id="48a15-140">When a new message arrives, your bot should verify its stored value for `serviceUrl`.</span></span>

```http
GET /v3/teams/19:ja0cu120i1jod12j@skype.net

Response body
{
    "id": "29:1GcS4EyB_oSI8A88XmWBN7NJFyMqe3QGnJdgLfFGkJnVelzRGos0bPbpsfJjcbAD22bmKc4GMbrY2g4JDrrA8vM06X1-cHHle4zOE6U4ttcc",
    "name": "The Team Name",
    "aadGroupId": "02ce3874-dd86-41ba-bddc-013f34019978"
}
```

* * *

## <a name="get-the-list-of-channels-in-a-team"></a><span data-ttu-id="48a15-141">Abrufen der Liste der Kanäle in einem Team</span><span class="sxs-lookup"><span data-stu-id="48a15-141">Get the list of channels in a team</span></span>

<span data-ttu-id="48a15-142">Ihr Bot kann die Liste der Kanäle in einem Teamabfragen.</span><span class="sxs-lookup"><span data-stu-id="48a15-142">Your bot can query the list of channels in a team.</span></span>

> [!NOTE]
>
>* <span data-ttu-id="48a15-143">Der Name des standardmäßigen allgemeinen Kanals wird zurückgegeben `null` , um die Lokalisierung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="48a15-143">The name of the default General channel is returned as `null` to allow for localization.</span></span>
>* <span data-ttu-id="48a15-144">Die Kanal-ID für den allgemeinen Kanal stimmt immer mit der Team-ID überein.</span><span class="sxs-lookup"><span data-stu-id="48a15-144">The channel ID for the General channel always matches the team ID.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="48a15-145">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="48a15-145">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="48a15-146">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="48a15-146">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="python"></a>[<span data-ttu-id="48a15-147">Python</span><span class="sxs-lookup"><span data-stu-id="48a15-147">Python</span></span>](#tab/python)

```python
async def _show_channels(
    self, turn_context: TurnContext
):
    channels = await TeamsInfo.get_team_channels(turn_context)
    reply = MessageFactory.text(f"Total of {len(channels)} channels are currently in team")
    await turn_context.send_activity(reply)
```

# <a name="json"></a>[<span data-ttu-id="48a15-148">Json</span><span class="sxs-lookup"><span data-stu-id="48a15-148">JSON</span></span>](#tab/json)

<span data-ttu-id="48a15-149">Sie können eine GET-Anforderung direkt unter `/v3/teams/{teamId}/conversations` Verwendung des Werts von `serviceUrl` als Endpunkt ausgeben.</span><span class="sxs-lookup"><span data-stu-id="48a15-149">You can directly issue a GET request on `/v3/teams/{teamId}/conversations`, using the value of `serviceUrl` as the endpoint.</span></span> <span data-ttu-id="48a15-150">Der Wert von `serviceUrl` neigt dazu, stabil zu sein, aber kann sich ändern.</span><span class="sxs-lookup"><span data-stu-id="48a15-150">The value of `serviceUrl` tends to be stable but can change.</span></span> <span data-ttu-id="48a15-151">Wenn eine neue Nachricht eingeht, sollte Ihr bot den gespeicherten Wert für überprüfen `serviceUrl` .</span><span class="sxs-lookup"><span data-stu-id="48a15-151">When a new message arrives, your bot should verify its stored value for `serviceUrl`.</span></span>

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

* * *

[!INCLUDE [sample](~/includes/bots/teams-bot-samples.md)]
