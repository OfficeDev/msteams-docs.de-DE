---
title: Get Team's specific context for your bot
author: laujan
description: Hier erfahren Sie, wie Sie den spezifischen Kontext von Microsoft Team für Ihren Bot, einschließlich Unterhaltungsliste, Details und Kanalliste, erhalten.
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: dfbf5e1638a2397492714b1e1945721450428d63
ms.sourcegitcommit: 0206ed48c6a287d14aec3739540194a91766f0a3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/26/2021
ms.locfileid: "51378336"
---
# <a name="get-teams-specific-context-for-your-bot"></a><span data-ttu-id="8fb53-103">Get Team's specific context for your bot</span><span class="sxs-lookup"><span data-stu-id="8fb53-103">Get Team's specific context for your bot</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="8fb53-104">Ein Bot kann auf zusätzliche Kontextdaten zu einem Team oder Chat zugreifen, in dem er installiert ist.</span><span class="sxs-lookup"><span data-stu-id="8fb53-104">A bot can access additional context data about a team or chat it is installed in.</span></span> <span data-ttu-id="8fb53-105">Diese Informationen können verwendet werden, um die Funktionalität des Bots zu erweitern und eine personalisiertere Benutzererfahrung zu bieten.</span><span class="sxs-lookup"><span data-stu-id="8fb53-105">This information can be used to enrich the bot's functionality and provide a more personalized experience.</span></span>

## <a name="fetching-the-roster-or-user-profile"></a><span data-ttu-id="8fb53-106">Abrufen des Dienstplans oder Benutzerprofils</span><span class="sxs-lookup"><span data-stu-id="8fb53-106">Fetching the roster or user profile</span></span>

<span data-ttu-id="8fb53-107">Ihr Bot kann die Liste der Mitglieder und deren grundlegende Profile abfragen, einschließlich Teams-Benutzer-IDs und Azure Active Directory (Azure AD)-Informationen wie Name und objectId.</span><span class="sxs-lookup"><span data-stu-id="8fb53-107">Your bot can query for the list of members and their basic profiles, including Teams user IDs and Azure Active Directory (Azure AD) information such as name and objectId.</span></span> <span data-ttu-id="8fb53-108">Sie können diese Informationen verwenden, um Benutzeridentitäten zu korrelieren, z. B. um zu überprüfen, ob ein Benutzer, der über Azure AD-Anmeldeinformationen bei einer Registerkarte angemeldet ist, Mitglied des Teams ist.</span><span class="sxs-lookup"><span data-stu-id="8fb53-108">You can use this information to correlate user identities, e.g., to check whether a user, logged into a tab through Azure AD credentials, is a member of the team.</span></span> <span data-ttu-id="8fb53-109">Der folgende Beispielcode verwendet den seitenseitigen Endpunkt zum Abrufen der Liste.</span><span class="sxs-lookup"><span data-stu-id="8fb53-109">The sample code below uses the paged endpoint for retrieving the roster.</span></span> <span data-ttu-id="8fb53-110">Zum Erhalten von Unterhaltungsmitgliedern hängt die minimale oder maximale Seitengröße von der Implementierung ab.</span><span class="sxs-lookup"><span data-stu-id="8fb53-110">For get conversation members, minimum or maximum page size depends on the implementation.</span></span> <span data-ttu-id="8fb53-111">Seitengröße kleiner als 50, werden als 50 behandelt, und die Seitengröße größer als 500 ist auf 500 begrenzt.</span><span class="sxs-lookup"><span data-stu-id="8fb53-111">Page size less than 50, are treated as 50, and page size greater than 500, are capped at 500.</span></span> <span data-ttu-id="8fb53-112">Obwohl Sie die nicht aus seiteierte Version weiterhin verwenden können, ist sie in großen Teams unzuverlässig und sollte nicht verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="8fb53-112">Although you may still use the non-paged version, it will be unreliable in large teams and should not be used.</span></span> <span data-ttu-id="8fb53-113">*Weitere* [Informationen finden Sie unter Changes to Teams Bot APIs for Fetching Team/Chat Members.](~/resources/team-chat-member-api-changes.md)</span><span class="sxs-lookup"><span data-stu-id="8fb53-113">*See* [Changes to Teams Bot APIs for Fetching Team/Chat Members](~/resources/team-chat-member-api-changes.md) for additional information.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="8fb53-114">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="8fb53-114">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="8fb53-115">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="8fb53-115">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="python"></a>[<span data-ttu-id="8fb53-116">Python</span><span class="sxs-lookup"><span data-stu-id="8fb53-116">Python</span></span>](#tab/python)

```python
async def _show_members(
    self, turn_context: TurnContext
):
    members = await TeamsInfo.get_team_members(turn_context)
```

# <a name="json"></a>[<span data-ttu-id="8fb53-117">Json</span><span class="sxs-lookup"><span data-stu-id="8fb53-117">JSON</span></span>](#tab/json)

<span data-ttu-id="8fb53-118">Sie können eine GET-Anforderung direkt auf `/v3/conversations/{conversationId}/pagedmembers?pageSize={pageSize}&continuationToken={continuationToken}` aus, indem Sie den Wert von `serviceUrl` als Endpunkt verwenden.</span><span class="sxs-lookup"><span data-stu-id="8fb53-118">You can directly issue a GET request on `/v3/conversations/{conversationId}/pagedmembers?pageSize={pageSize}&continuationToken={continuationToken}`, using the value of `serviceUrl` as the endpoint.</span></span> <span data-ttu-id="8fb53-119">Der Wert von `serviceUrl` ist in der Regel stabil, kann sich jedoch ändern.</span><span class="sxs-lookup"><span data-stu-id="8fb53-119">The value of `serviceUrl` tends to be stable but can change.</span></span> <span data-ttu-id="8fb53-120">Wenn eine neue Nachricht eintrifft, sollte Ihr Bot seinen gespeicherten Wert für `serviceUrl` überprüfen.</span><span class="sxs-lookup"><span data-stu-id="8fb53-120">When a new message arrives, your bot should verify its stored value for `serviceUrl`.</span></span> <span data-ttu-id="8fb53-121">Die Antwortnutzlast gibt außerdem an, ob der Benutzer ein regulärer oder anonymer Benutzer ist.</span><span class="sxs-lookup"><span data-stu-id="8fb53-121">The response payload will also indicate if the user is a regular or anonymous user.</span></span>

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

## <a name="get-single-member-details"></a><span data-ttu-id="8fb53-122">Details zu einzelnen Membern erhalten</span><span class="sxs-lookup"><span data-stu-id="8fb53-122">Get single member details</span></span>

<span data-ttu-id="8fb53-123">Sie können auch die Details eines bestimmten Benutzers mithilfe der Teams-Benutzer-ID, des UPN oder der AAD-Objekt-ID abrufen.</span><span class="sxs-lookup"><span data-stu-id="8fb53-123">You can also retrieve the details of a particular user using their Teams user Id, UPN, or AAD Object Id.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="8fb53-124">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="8fb53-124">C#/.NET</span></span>](#tab/dotnet)

```csharp
public class MyBot : TeamsActivityHandler
{
    protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
    {
        var member = await TeamsInfo.GetMemberAsync(turnContext, turnContext.Activity.From.Id, cancellationToken);
    }
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="8fb53-125">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="8fb53-125">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="python"></a>[<span data-ttu-id="8fb53-126">Python</span><span class="sxs-lookup"><span data-stu-id="8fb53-126">Python</span></span>](#tab/python)

```python
async def _show_members(
    self, turn_context: TurnContext
):
    member = TeamsInfo.get_member(turn_context, turn_context.activity.from_property.id)
```

# <a name="json"></a>[<span data-ttu-id="8fb53-127">Json</span><span class="sxs-lookup"><span data-stu-id="8fb53-127">JSON</span></span>](#tab/json)

<span data-ttu-id="8fb53-128">Sie können eine GET-Anforderung direkt auf `/v3/conversations/{conversationId}/members/{userId}` aus, indem Sie den Wert von `serviceUrl` als Endpunkt verwenden.</span><span class="sxs-lookup"><span data-stu-id="8fb53-128">You can directly issue a GET request on `/v3/conversations/{conversationId}/members/{userId}`, using the value of `serviceUrl` as the endpoint.</span></span> <span data-ttu-id="8fb53-129">Der Wert von `serviceUrl` ist in der Regel stabil, kann sich jedoch ändern.</span><span class="sxs-lookup"><span data-stu-id="8fb53-129">The value of `serviceUrl` tends to be stable but can change.</span></span> <span data-ttu-id="8fb53-130">Wenn eine neue Nachricht eintrifft, sollte Ihr Bot seinen gespeicherten Wert für `serviceUrl` überprüfen.</span><span class="sxs-lookup"><span data-stu-id="8fb53-130">When a new message arrives, your bot should verify its stored value for `serviceUrl`.</span></span> <span data-ttu-id="8fb53-131">Dies kann für reguläre und anonyme Benutzer verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="8fb53-131">This can be used for regular users and anonymous users.</span></span>

<span data-ttu-id="8fb53-132">Nachfolgend finden Sie ein Antwortbeispiel für reguläre Benutzer</span><span class="sxs-lookup"><span data-stu-id="8fb53-132">Below is a response sample for regular user</span></span>

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

<span data-ttu-id="8fb53-133">Nachfolgend finden Sie die Antwort für anonymen Benutzer</span><span class="sxs-lookup"><span data-stu-id="8fb53-133">Below is response for anonymous user</span></span>

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

## <a name="get-teams-details"></a><span data-ttu-id="8fb53-134">Details des Teams erhalten</span><span class="sxs-lookup"><span data-stu-id="8fb53-134">Get team's details</span></span>

<span data-ttu-id="8fb53-135">Bei der Installation in einem Team kann Ihr Bot Metadaten zu diesem Team abfragen, einschließlich der Azure AD groupId.</span><span class="sxs-lookup"><span data-stu-id="8fb53-135">When installed in a team, your bot can query for metadata about that team including the Azure AD groupId.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="8fb53-136">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="8fb53-136">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="8fb53-137">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="8fb53-137">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="python"></a>[<span data-ttu-id="8fb53-138">Python</span><span class="sxs-lookup"><span data-stu-id="8fb53-138">Python</span></span>](#tab/python)

```python
async def _show_details(self, turn_context: TurnContext):
    team_details = await TeamsInfo.get_team_details(turn_context)
    reply = MessageFactory.text(f"The team name is {team_details.name}. The team ID is {team_details.id}. The AADGroupID is {team_details.aad_group_id}.")
    await turn_context.send_activity(reply)
```

# <a name="json"></a>[<span data-ttu-id="8fb53-139">Json</span><span class="sxs-lookup"><span data-stu-id="8fb53-139">JSON</span></span>](#tab/json)

<span data-ttu-id="8fb53-140">Sie können eine GET-Anforderung direkt auf `/v3/teams/{teamId}` aus, indem Sie den Wert von `serviceUrl` als Endpunkt verwenden.</span><span class="sxs-lookup"><span data-stu-id="8fb53-140">You can directly issue a GET request on `/v3/teams/{teamId}`, using the value of `serviceUrl` as the endpoint.</span></span> <span data-ttu-id="8fb53-141">Der Wert von `serviceUrl` ist in der Regel stabil, kann sich jedoch ändern.</span><span class="sxs-lookup"><span data-stu-id="8fb53-141">The value of `serviceUrl` tends to be stable but can change.</span></span> <span data-ttu-id="8fb53-142">Wenn eine neue Nachricht eintrifft, sollte Ihr Bot seinen gespeicherten Wert für `serviceUrl` überprüfen.</span><span class="sxs-lookup"><span data-stu-id="8fb53-142">When a new message arrives, your bot should verify its stored value for `serviceUrl`.</span></span>

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

## <a name="get-the-list-of-channels-in-a-team"></a><span data-ttu-id="8fb53-143">Liste der Kanäle in einem Team erhalten</span><span class="sxs-lookup"><span data-stu-id="8fb53-143">Get the list of channels in a team</span></span>

<span data-ttu-id="8fb53-144">Ihr Bot kann die Liste der Kanäle in einem Team abfragen.</span><span class="sxs-lookup"><span data-stu-id="8fb53-144">Your bot can query the list of channels in a team.</span></span>

> [!NOTE]
>
>* <span data-ttu-id="8fb53-145">Der Name des standardmäßigen allgemeinen Kanals wird zurückgegeben, `null` um die Lokalisierung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="8fb53-145">The name of the default General channel is returned as `null` to allow for localization.</span></span>
>* <span data-ttu-id="8fb53-146">Die Kanal-ID für den allgemeinen Kanal entspricht immer der Team-ID.</span><span class="sxs-lookup"><span data-stu-id="8fb53-146">The channel ID for the General channel always matches the team ID.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="8fb53-147">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="8fb53-147">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="8fb53-148">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="8fb53-148">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="python"></a>[<span data-ttu-id="8fb53-149">Python</span><span class="sxs-lookup"><span data-stu-id="8fb53-149">Python</span></span>](#tab/python)

```python
async def _show_channels(
    self, turn_context: TurnContext
):
    channels = await TeamsInfo.get_team_channels(turn_context)
    reply = MessageFactory.text(f"Total of {len(channels)} channels are currently in team")
    await turn_context.send_activity(reply)
```

# <a name="json"></a>[<span data-ttu-id="8fb53-150">Json</span><span class="sxs-lookup"><span data-stu-id="8fb53-150">JSON</span></span>](#tab/json)

<span data-ttu-id="8fb53-151">Sie können eine GET-Anforderung direkt auf `/v3/teams/{teamId}/conversations` aus, indem Sie den Wert von `serviceUrl` als Endpunkt verwenden.</span><span class="sxs-lookup"><span data-stu-id="8fb53-151">You can directly issue a GET request on `/v3/teams/{teamId}/conversations`, using the value of `serviceUrl` as the endpoint.</span></span> <span data-ttu-id="8fb53-152">Der Wert von `serviceUrl` ist in der Regel stabil, kann sich jedoch ändern.</span><span class="sxs-lookup"><span data-stu-id="8fb53-152">The value of `serviceUrl` tends to be stable but can change.</span></span> <span data-ttu-id="8fb53-153">Wenn eine neue Nachricht eintrifft, sollte Ihr Bot seinen gespeicherten Wert für `serviceUrl` überprüfen.</span><span class="sxs-lookup"><span data-stu-id="8fb53-153">When a new message arrives, your bot should verify its stored value for `serviceUrl`.</span></span>

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
