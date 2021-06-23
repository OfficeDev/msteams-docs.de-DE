---
title: Abrufen Teams spezifischen Kontexts für Ihren Bot
author: surbhigupta
description: So erhalten Sie den spezifischen Kontext des Microsoft-Teams für Ihren Bot, einschließlich der Unterhaltungsliste, Details und Kanalliste.
ms.topic: conceptual
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: ccbc04cbc1b2eb3162e886cd77273a4a0c37a6ec
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53068979"
---
# <a name="get-teams-specific-context-for-your-bot"></a><span data-ttu-id="90c85-103">Abrufen Teams spezifischen Kontexts für Ihren Bot</span><span class="sxs-lookup"><span data-stu-id="90c85-103">Get Teams specific context for your bot</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="90c85-104">Ein Bot kann auf zusätzliche Kontextdaten zu einem Team oder Chat zugreifen, in dem er installiert ist.</span><span class="sxs-lookup"><span data-stu-id="90c85-104">A bot can access additional context data about a team or chat where it is installed.</span></span> <span data-ttu-id="90c85-105">Diese Informationen können verwendet werden, um die Funktionalität des Bots zu erweitern und eine personalisierte Erfahrung zu bieten.</span><span class="sxs-lookup"><span data-stu-id="90c85-105">This information can be used to enrich the bot's functionality and provide a more personalized experience.</span></span>

## <a name="fetch-the-roster-or-user-profile"></a><span data-ttu-id="90c85-106">Abrufen des Listen- oder Benutzerprofils</span><span class="sxs-lookup"><span data-stu-id="90c85-106">Fetch the roster or user profile</span></span>

<span data-ttu-id="90c85-107">Ihr Bot kann die Liste der Mitglieder und deren grundlegende Benutzerprofile abfragen, einschließlich Teams Benutzer-IDs und Azure Active Directory (AAD)-Informationen, z. B. Name und ObjectId.</span><span class="sxs-lookup"><span data-stu-id="90c85-107">Your bot can query for the list of members and their basic user profiles, including Teams user IDs and Azure Active Directory (AAD) information, such as name and objectId.</span></span> <span data-ttu-id="90c85-108">Sie können diese Informationen verwenden, um Benutzeridentitäten zu korrelieren.</span><span class="sxs-lookup"><span data-stu-id="90c85-108">You can use this information to correlate user identities.</span></span> <span data-ttu-id="90c85-109">Um beispielsweise zu überprüfen, ob sich ein Benutzer über AAD-Anmeldeinformationen bei einer Registerkarte angemeldet hat, ist er Mitglied des Teams.</span><span class="sxs-lookup"><span data-stu-id="90c85-109">For example, to check whether a user logged into a tab through AAD credentials, is a member of the team.</span></span> <span data-ttu-id="90c85-110">Zum Abrufen von Unterhaltungsmitgliedern hängt die minimale oder maximale Seitengröße von der Implementierung ab.</span><span class="sxs-lookup"><span data-stu-id="90c85-110">For get conversation members, minimum or maximum page size depends on the implementation.</span></span> <span data-ttu-id="90c85-111">Seitengröße kleiner als 50, werden als 50 behandelt und größer als 500, sind auf 500 begrenzt.</span><span class="sxs-lookup"><span data-stu-id="90c85-111">Page size less than 50, are treated as 50, and greater than 500, are capped at 500.</span></span> <span data-ttu-id="90c85-112">Auch wenn Sie die nicht seitenweise Version verwenden, ist sie in großen Teams unzuverlässig und darf nicht verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="90c85-112">Even if you use the non-paged version, it is unreliable in large teams and must not be used.</span></span> <span data-ttu-id="90c85-113">Weitere Informationen finden Sie unter [Änderungen an Teams Bot-APIs zum Abrufen von Team- oder Chatmitgliedern.](~/resources/team-chat-member-api-changes.md)</span><span class="sxs-lookup"><span data-stu-id="90c85-113">For more information, see [changes to Teams Bot APIs for fetching team or chat members](~/resources/team-chat-member-api-changes.md).</span></span>

<span data-ttu-id="90c85-114">Im folgenden Beispielcode wird der seitenierte Endpunkt zum Abrufen der Teilnehmerliste verwendet:</span><span class="sxs-lookup"><span data-stu-id="90c85-114">The following sample code uses the paged endpoint for fetching the roster:</span></span>

# <a name="c"></a>[<span data-ttu-id="90c85-115">C#</span><span class="sxs-lookup"><span data-stu-id="90c85-115">C#</span></span>](#tab/dotnet)

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

# <a name="typescript"></a>[<span data-ttu-id="90c85-116">TypeScript</span><span class="sxs-lookup"><span data-stu-id="90c85-116">TypeScript</span></span>](#tab/typescript)

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

# <a name="python"></a>[<span data-ttu-id="90c85-117">Python</span><span class="sxs-lookup"><span data-stu-id="90c85-117">Python</span></span>](#tab/python)

```python
async def _show_members(
    self, turn_context: TurnContext
):
    members = await TeamsInfo.get_team_members(turn_context)
```

# <a name="json"></a>[<span data-ttu-id="90c85-118">Json</span><span class="sxs-lookup"><span data-stu-id="90c85-118">JSON</span></span>](#tab/json)

<span data-ttu-id="90c85-119">Sie können eine GET-Anforderung direkt auf ausgeben, indem Sie `/v3/conversations/{conversationId}/pagedmembers?pageSize={pageSize}&continuationToken={continuationToken}` den Wert von als Endpunkt `serviceUrl` verwenden.</span><span class="sxs-lookup"><span data-stu-id="90c85-119">You can directly issue a GET request on `/v3/conversations/{conversationId}/pagedmembers?pageSize={pageSize}&continuationToken={continuationToken}`, using the value of `serviceUrl` as the endpoint.</span></span> <span data-ttu-id="90c85-120">Der Wert von `serviceUrl` ist stabil, kann sich aber ändern.</span><span class="sxs-lookup"><span data-stu-id="90c85-120">The value of `serviceUrl` is stable but can change.</span></span> <span data-ttu-id="90c85-121">Wenn eine neue Nachricht eintrifft, muss Ihr Bot seinen gespeicherten Wert für `serviceUrl` überprüfen.</span><span class="sxs-lookup"><span data-stu-id="90c85-121">When a new message arrives, your bot must verify its stored value for `serviceUrl`.</span></span> <span data-ttu-id="90c85-122">Die Antwortnutzlast gibt auch an, ob der Benutzer ein regulärer oder anonymer Benutzer ist.</span><span class="sxs-lookup"><span data-stu-id="90c85-122">The response payload also indicates if the user is a regular or anonymous user.</span></span>

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

<span data-ttu-id="90c85-123">Nachdem Sie die Liste oder das Benutzerprofil abgerufen haben, können Sie Details zu einem einzelnen Mitglied abrufen.</span><span class="sxs-lookup"><span data-stu-id="90c85-123">After you fetch the roster or user profile, you can get details of a single member.</span></span> <span data-ttu-id="90c85-124">Verwenden Sie derzeit die Microsoft Teams-Bot-APIs `TeamsInfo.GetMembersAsync` für C# oder TypeScript-APIs, um Informationen für ein oder mehrere Mitglieder eines Chats oder `TeamsInfo.getMembers` Teams abzurufen.</span><span class="sxs-lookup"><span data-stu-id="90c85-124">Currently, to retrieve information for one or more members of a chat or team, use the Microsoft Teams bot APIs `TeamsInfo.GetMembersAsync` for C# or `TeamsInfo.getMembers` for TypeScript APIs.</span></span>

## <a name="get-single-member-details"></a><span data-ttu-id="90c85-125">Abrufen von Details zu einzelnen Membern</span><span class="sxs-lookup"><span data-stu-id="90c85-125">Get single member details</span></span>

<span data-ttu-id="90c85-126">Sie können die Details eines bestimmten Benutzers auch mithilfe seiner Teams Benutzer-ID, UPN oder AAD-Objekt-ID abrufen.</span><span class="sxs-lookup"><span data-stu-id="90c85-126">You can also retrieve the details of a particular user using their Teams user ID, UPN, or AAD Object ID.</span></span>

<span data-ttu-id="90c85-127">Der folgende Beispielcode wird verwendet, um Details zu einzelnen Membern abzurufen:</span><span class="sxs-lookup"><span data-stu-id="90c85-127">The following sample code is used to get single member details:</span></span>

# <a name="c"></a>[<span data-ttu-id="90c85-128">C#</span><span class="sxs-lookup"><span data-stu-id="90c85-128">C#</span></span>](#tab/dotnet)

```csharp
public class MyBot : TeamsActivityHandler
{
    protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
    {
        var member = await TeamsInfo.GetMemberAsync(turnContext, turnContext.Activity.From.Id, cancellationToken);
    }
}
```

# <a name="typescript"></a>[<span data-ttu-id="90c85-129">TypeScript</span><span class="sxs-lookup"><span data-stu-id="90c85-129">TypeScript</span></span>](#tab/typescript)

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

# <a name="python"></a>[<span data-ttu-id="90c85-130">Python</span><span class="sxs-lookup"><span data-stu-id="90c85-130">Python</span></span>](#tab/python)

```python
async def _show_members(
    self, turn_context: TurnContext
):
    member = await TeamsInfo.get_member(turn_context, turn_context.activity.from_property.id)
```

# <a name="json"></a>[<span data-ttu-id="90c85-131">Json</span><span class="sxs-lookup"><span data-stu-id="90c85-131">JSON</span></span>](#tab/json)

<span data-ttu-id="90c85-132">Sie können eine GET-Anforderung direkt auf ausgeben, indem Sie `/v3/conversations/{conversationId}/members/{userId}` den Wert von als Endpunkt `serviceUrl` verwenden.</span><span class="sxs-lookup"><span data-stu-id="90c85-132">You can directly issue a GET request on `/v3/conversations/{conversationId}/members/{userId}`, using the value of `serviceUrl` as the endpoint.</span></span> <span data-ttu-id="90c85-133">Der Wert von `serviceUrl` ist stabil, kann sich aber ändern.</span><span class="sxs-lookup"><span data-stu-id="90c85-133">The value of `serviceUrl` is stable but can change.</span></span> <span data-ttu-id="90c85-134">Wenn eine neue Nachricht eintrifft, muss Ihr Bot seinen gespeicherten Wert für `serviceUrl` überprüfen.</span><span class="sxs-lookup"><span data-stu-id="90c85-134">When a new message arrives, your bot must verify its stored value for `serviceUrl`.</span></span> <span data-ttu-id="90c85-135">Dies kann für reguläre und anonyme Benutzer verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="90c85-135">This can be used for regular users and anonymous users.</span></span>

<span data-ttu-id="90c85-136">Im Folgenden finden Sie das Antwortbeispiel für reguläre Benutzer:</span><span class="sxs-lookup"><span data-stu-id="90c85-136">The following is the response sample for regular user:</span></span>

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

<span data-ttu-id="90c85-137">Im Folgenden finden Sie das Antwortbeispiel für anonyme Benutzer:</span><span class="sxs-lookup"><span data-stu-id="90c85-137">The following is the response sample for anonymous user:</span></span>

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

<span data-ttu-id="90c85-138">Nachdem Sie Details zu einem einzelnen Mitglied erhalten haben, können Sie Details des Teams abrufen.</span><span class="sxs-lookup"><span data-stu-id="90c85-138">After you get details of a single member, you can get details of the team.</span></span> <span data-ttu-id="90c85-139">Verwenden Sie derzeit die Microsoft Teams-Bot-APIs `TeamsInfo.GetMemberDetailsAsync` für C# oder TypeScript, um Informationen für ein Team `TeamsInfo.getTeamDetails` abzurufen.</span><span class="sxs-lookup"><span data-stu-id="90c85-139">Currently, to retrieve information for a team, use the Microsoft Teams bot APIs `TeamsInfo.GetMemberDetailsAsync` for C# or `TeamsInfo.getTeamDetails` for TypeScript.</span></span>

## <a name="get-teams-details"></a><span data-ttu-id="90c85-140">Abrufen von Teamdetails</span><span class="sxs-lookup"><span data-stu-id="90c85-140">Get team's details</span></span>

<span data-ttu-id="90c85-141">Wenn er in einem Team installiert ist, kann Ihr Bot Metadaten zu diesem Team abfragen, einschließlich der AAD-Gruppen-ID.</span><span class="sxs-lookup"><span data-stu-id="90c85-141">When installed in a team, your bot can query for metadata about that team including the AAD group ID.</span></span>

<span data-ttu-id="90c85-142">Der folgende Beispielcode wird verwendet, um die Details des Teams abzurufen:</span><span class="sxs-lookup"><span data-stu-id="90c85-142">The following sample code is used to get team's details:</span></span>

# <a name="c"></a>[<span data-ttu-id="90c85-143">C#</span><span class="sxs-lookup"><span data-stu-id="90c85-143">C#</span></span>](#tab/dotnet)

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

# <a name="typescript"></a>[<span data-ttu-id="90c85-144">TypeScript</span><span class="sxs-lookup"><span data-stu-id="90c85-144">TypeScript</span></span>](#tab/typescript)

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

# <a name="python"></a>[<span data-ttu-id="90c85-145">Python</span><span class="sxs-lookup"><span data-stu-id="90c85-145">Python</span></span>](#tab/python)

```python
async def _show_details(self, turn_context: TurnContext):
    team_details = await TeamsInfo.get_team_details(turn_context)
    reply = MessageFactory.text(f"The team name is {team_details.name}. The team ID is {team_details.id}. The AADGroupID is {team_details.aad_group_id}.")
    await turn_context.send_activity(reply)
```

# <a name="json"></a>[<span data-ttu-id="90c85-146">Json</span><span class="sxs-lookup"><span data-stu-id="90c85-146">JSON</span></span>](#tab/json)

<span data-ttu-id="90c85-147">Sie können eine GET-Anforderung direkt auf ausgeben, indem Sie `/v3/teams/{teamId}` den Wert von als Endpunkt `serviceUrl` verwenden.</span><span class="sxs-lookup"><span data-stu-id="90c85-147">You can directly issue a GET request on `/v3/teams/{teamId}`, using the value of `serviceUrl` as the endpoint.</span></span> <span data-ttu-id="90c85-148">Der Wert von `serviceUrl` ist stabil, kann sich aber ändern.</span><span class="sxs-lookup"><span data-stu-id="90c85-148">The value of `serviceUrl` is stable but can change.</span></span> <span data-ttu-id="90c85-149">Wenn eine neue Nachricht eintrifft, muss Ihr Bot seinen gespeicherten Wert für `serviceUrl` überprüfen.</span><span class="sxs-lookup"><span data-stu-id="90c85-149">When a new message arrives, your bot must verify its stored value for `serviceUrl`.</span></span>

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

<span data-ttu-id="90c85-150">Nachdem Sie Details zum Team erhalten haben, können Sie die Liste der Kanäle in einem Team abrufen.</span><span class="sxs-lookup"><span data-stu-id="90c85-150">After you get details of the team, you can get the list of channels in a team.</span></span> <span data-ttu-id="90c85-151">Verwenden Sie derzeit die Microsoft Teams-Bot-APIs `TeamsInfo.GetTeamChannelsAsync` für C# oder TypeScript-APIs, um Informationen für eine Liste von Kanälen in einem Team `TeamsInfo.getTeamChannels` abzurufen.</span><span class="sxs-lookup"><span data-stu-id="90c85-151">Currently, to retrieve information for a list of channels in a team, use the Microsoft Teams bot APIs `TeamsInfo.GetTeamChannelsAsync` for C# or `TeamsInfo.getTeamChannels` for TypeScript APIs.</span></span>

## <a name="get-the-list-of-channels-in-a-team"></a><span data-ttu-id="90c85-152">Abrufen der Liste der Kanäle in einem Team</span><span class="sxs-lookup"><span data-stu-id="90c85-152">Get the list of channels in a team</span></span>

<span data-ttu-id="90c85-153">Ihr Bot kann die Liste der Kanäle in einem Team abfragen.</span><span class="sxs-lookup"><span data-stu-id="90c85-153">Your bot can query the list of channels in a team.</span></span>

> [!NOTE]
> * <span data-ttu-id="90c85-154">Der Name des standardmäßigen Kanals "Allgemein" wird `null` zurückgegeben, um die Lokalisierung zuzulassen.</span><span class="sxs-lookup"><span data-stu-id="90c85-154">The name of the default General channel is returned as `null` to allow for localization.</span></span>
> * <span data-ttu-id="90c85-155">Die Kanal-ID für den Kanal "Allgemein" stimmt immer mit der Team-ID überein.</span><span class="sxs-lookup"><span data-stu-id="90c85-155">The channel ID for the General channel always matches the team ID.</span></span>

<span data-ttu-id="90c85-156">Der folgende Beispielcode wird verwendet, um die Liste der Kanäle in einem Team abzurufen:</span><span class="sxs-lookup"><span data-stu-id="90c85-156">The following sample code is used to get the list of channels in a team:</span></span>

# <a name="c"></a>[<span data-ttu-id="90c85-157">C#</span><span class="sxs-lookup"><span data-stu-id="90c85-157">C#</span></span>](#tab/dotnet)

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

# <a name="typescript"></a>[<span data-ttu-id="90c85-158">TypeScript</span><span class="sxs-lookup"><span data-stu-id="90c85-158">TypeScript</span></span>](#tab/typescript)

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

# <a name="python"></a>[<span data-ttu-id="90c85-159">Python</span><span class="sxs-lookup"><span data-stu-id="90c85-159">Python</span></span>](#tab/python)

```python
async def _show_channels(
    self, turn_context: TurnContext
):
    channels = await TeamsInfo.get_team_channels(turn_context)
    reply = MessageFactory.text(f"Total of {len(channels)} channels are currently in team")
    await turn_context.send_activity(reply)
```

# <a name="json"></a>[<span data-ttu-id="90c85-160">Json</span><span class="sxs-lookup"><span data-stu-id="90c85-160">JSON</span></span>](#tab/json)

<span data-ttu-id="90c85-161">Sie können eine GET-Anforderung direkt auf ausgeben, indem Sie `/v3/teams/{teamId}/conversations` den Wert von als Endpunkt `serviceUrl` verwenden.</span><span class="sxs-lookup"><span data-stu-id="90c85-161">You can directly issue a GET request on `/v3/teams/{teamId}/conversations`, using the value of `serviceUrl` as the endpoint.</span></span> <span data-ttu-id="90c85-162">Der Wert von `serviceUrl` ist stabil, kann sich aber ändern.</span><span class="sxs-lookup"><span data-stu-id="90c85-162">The value of `serviceUrl` is stable but can change.</span></span> <span data-ttu-id="90c85-163">Wenn eine neue Nachricht eintrifft, muss Ihr Bot seinen gespeicherten Wert für `serviceUrl` überprüfen.</span><span class="sxs-lookup"><span data-stu-id="90c85-163">When a new message arrives, your bot must verify its stored value for `serviceUrl`.</span></span>

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

## <a name="next-step"></a><span data-ttu-id="90c85-164">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="90c85-164">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="90c85-165">Senden und Empfangen von Dateien über den Bot</span><span class="sxs-lookup"><span data-stu-id="90c85-165">Send and receive files through the bot</span></span>](~/bots/how-to/bots-filesv4.md)
