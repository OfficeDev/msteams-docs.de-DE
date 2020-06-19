---
title: Kontext für Ihren bot abrufen
description: Beschreibt, wie Kontext für Bots in Microsoft Teams abgerufen wird.
keywords: Teams-Bots-Kontext
ms.date: 05/20/2019
ms.openlocfilehash: 8f054661664850ffb843714230e209c8e4737f0a
ms.sourcegitcommit: fdcd91b270d4c2e98ab2b2c1029c76c49bb807fa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "44801230"
---
# <a name="get-context-for-your-microsoft-teams-bot"></a><span data-ttu-id="06a8b-104">Kontext für Ihren Microsoft Teams-bot abrufen</span><span class="sxs-lookup"><span data-stu-id="06a8b-104">Get context for your Microsoft Teams bot</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="06a8b-105">Ihr Bot kann auf zusätzlichen Kontext über das Team oder den Chat zugreifen, beispielsweise auf das Benutzerprofil.</span><span class="sxs-lookup"><span data-stu-id="06a8b-105">Your bot can access additional context about the team or chat, such as user profile.</span></span> <span data-ttu-id="06a8b-106">Diese Informationen können verwendet werden, um die Funktionalität Ihres bot zu bereichern und eine personalisierte Erfahrung zu bieten.</span><span class="sxs-lookup"><span data-stu-id="06a8b-106">This information can be used to enrich your bot's functionality and provide a more personalized experience.</span></span>

> [!NOTE]
> <span data-ttu-id="06a8b-107">Diese Microsoft Teams &ndash; -spezifischen bot-APIs werden am besten über unsere Erweiterungen für das bot Builder SDK aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="06a8b-107">These Microsoft Teams&ndash;specific bot APIs are best accessed through our extensions for the Bot Builder SDK.</span></span> <span data-ttu-id="06a8b-108">Für C#-/.net laden Sie unser [Microsoft. bot. Connector. Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet-Paket herunter.</span><span class="sxs-lookup"><span data-stu-id="06a8b-108">For C#/.NET, download our [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet package.</span></span> <span data-ttu-id="06a8b-109">Für Node.js Entwicklung wurde die BotBuilder für Microsoft Teams-Funktionen in das [bot Framework SDK](https://github.com/microsoft/botframework-sdk) ab v 4.6 integriert.</span><span class="sxs-lookup"><span data-stu-id="06a8b-109">For Node.js development, the BotBuilder for Microsoft Teams functionality has been incorporated into the [Bot Framework SDK](https://github.com/microsoft/botframework-sdk) as of v4.6.</span></span>

## <a name="fetching-the-team-roster"></a><span data-ttu-id="06a8b-110">Abrufen des Team Arbeitsplans</span><span class="sxs-lookup"><span data-stu-id="06a8b-110">Fetching the team roster</span></span>

<span data-ttu-id="06a8b-111">Ihr Bot kann eine Abfrage für die Liste der Teammitglieder und ihrer grundlegenden profile durchführen, einschließlich Microsoft Teams-Benutzer-IDs und Azure Active Directory Informationen (Azure AD) wie Name und ObjectID.</span><span class="sxs-lookup"><span data-stu-id="06a8b-111">Your bot can query for the list of team members and their basic profiles, which includes Teams user IDs and Azure Active Directory (Azure AD) information such as name and objectId.</span></span> <span data-ttu-id="06a8b-112">Sie können diese Informationen verwenden, um Benutzeridentitäten zu korrelieren; um beispielsweise zu überprüfen, ob ein Benutzer, der bei einer Registerkarte über Azure AD Anmeldeinformationen angemeldet ist, ein Mitglied des Teams ist.</span><span class="sxs-lookup"><span data-stu-id="06a8b-112">You can use this information to correlate user identities; for example, to check whether a user logged into a tab through Azure AD credentials is a member of the team.</span></span>

### <a name="rest-api-example"></a><span data-ttu-id="06a8b-113">Rest-API-Beispiel</span><span class="sxs-lookup"><span data-stu-id="06a8b-113">REST API example</span></span>

<span data-ttu-id="06a8b-114">Sie können eine GET-Anforderung direkt unter [`/conversations/{teamId}/members/`](/bot-framework/rest-api/bot-framework-rest-connector-api-reference#get-conversation-members) Verwendung des Werts von `serviceUrl` als Endpunkt ausgeben.</span><span class="sxs-lookup"><span data-stu-id="06a8b-114">You can directly issue a GET request on [`/conversations/{teamId}/members/`](/bot-framework/rest-api/bot-framework-rest-connector-api-reference#get-conversation-members), using the value of `serviceUrl` as the endpoint.</span></span>

<span data-ttu-id="06a8b-115">Der `teamId` kann im `channeldata` Objekt der Aktivitäts Nutzlast gefunden werden, die ihr bot in den folgenden Szenarien erhält:</span><span class="sxs-lookup"><span data-stu-id="06a8b-115">The `teamId` can be found in the `channeldata` object of the activity payload that your bot receives in the following scenarios:</span></span>
* <span data-ttu-id="06a8b-116">Wenn ein Benutzer mit dem bot in einem Teamkontext Nachrichten oder interagiert (siehe [empfangen von Nachrichten](~/resources/bot-v3/bot-conversations/bots-conversations.md#receiving-messages))</span><span class="sxs-lookup"><span data-stu-id="06a8b-116">When a user messages or interacts with your bot in a team context (see [Receiving Messages](~/resources/bot-v3/bot-conversations/bots-conversations.md#receiving-messages))</span></span>
* <span data-ttu-id="06a8b-117">Wenn einem Team ein neuer Benutzer oder bot hinzugefügt wird (siehe [bot oder Benutzer, der einem Team hinzugefügt](~/resources/bot-v3/bots-notifications.md#bot-or-user-added-to-a-team)wurde)</span><span class="sxs-lookup"><span data-stu-id="06a8b-117">When a new user or bot is added to a team (see [Bot or user added to a team](~/resources/bot-v3/bots-notifications.md#bot-or-user-added-to-a-team))</span></span>

> [!NOTE]
>* <span data-ttu-id="06a8b-118">Stellen Sie sicher, dass Sie die Team-ID verwenden, wenn Sie die API aufrufen</span><span class="sxs-lookup"><span data-stu-id="06a8b-118">Make sure to use the team id when calling the api</span></span>
>* <span data-ttu-id="06a8b-119">Der Wert von `serviceUrl` neigt dazu, stabil zu sein, aber kann sich ändern.</span><span class="sxs-lookup"><span data-stu-id="06a8b-119">The value of `serviceUrl` tends to be stable but can change.</span></span> <span data-ttu-id="06a8b-120">Wenn eine neue Nachricht eintrifft, sollte Ihr bot den gespeicherten Wert von überprüfen `serviceUrl` .</span><span class="sxs-lookup"><span data-stu-id="06a8b-120">When a new message arrives, your bot should verify its stored value of `serviceUrl`.</span></span>

```json
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

### <a name="net-example"></a><span data-ttu-id="06a8b-121">.NET-Beispiel</span><span class="sxs-lookup"><span data-stu-id="06a8b-121">.NET example</span></span>

<span data-ttu-id="06a8b-122">Aufrufen `GetConversationMembersAsync` mit `Team.Id` , um eine Liste von Benutzer-IDs zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="06a8b-122">Call `GetConversationMembersAsync` using `Team.Id` to return a list of user IDs.</span></span>

```csharp
// Fetch the members in the current conversation
var connector = new ConnectorClient(new Uri(context.Activity.ServiceUrl));
var teamId = context.Activity.GetChannelData<TeamsChannelData>().Team.Id;
var members = await connector.Conversations.GetConversationMembersAsync(teamId);

// Concatenate information about all members into a string
var sb = new StringBuilder();
foreach (var member in members.AsTeamsChannelAccounts())
{
    sb.AppendFormat(
        "GivenName = {0}, TeamsMemberId = {1}",
        member.Name, member.Id);

    sb.AppendLine();
}

// Post the member info back into the conversation
await context.PostAsync($"People in this conversation: {sb.ToString()}");
```

### <a name="nodejstypescript-example"></a><span data-ttu-id="06a8b-123">Node.js/typescript-Beispiel</span><span class="sxs-lookup"><span data-stu-id="06a8b-123">Node.js/TypeScript example</span></span>

```typescript

[...]
import * as builder from "botbuilder";
[...]

var teamId = session.message.sourceEvent.team.id;
connector.fetchMembers(
  (<builder.IChatConnectorAddress>session.message.address).serviceUrl,
  teamId,
  (err, result) => {
    if (err) {
      session.endDialog('There is some error');
    }
    else {
      session.endDialog('%s', JSON.stringify(result));
    }
  }
);
```

<span data-ttu-id="06a8b-124">*Siehe auch* [bot Framework-Beispiele](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).</span><span class="sxs-lookup"><span data-stu-id="06a8b-124">*See also* [Bot Framework samples](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).</span></span>

## <a name="fetching-user-profile-or-roster-in-personal-or-group-chat"></a><span data-ttu-id="06a8b-125">Abrufen von Benutzerprofilen oder Dienstplänen im persönlichen oder Gruppenchat</span><span class="sxs-lookup"><span data-stu-id="06a8b-125">Fetching user profile or roster in personal or group chat</span></span>

<span data-ttu-id="06a8b-126">Sie können auch denselben API-Aufruf für einen persönlichen Chat durchführen, um die Profilinformationen des Benutzers zu erhalten, der mit Ihrem bot chattet.</span><span class="sxs-lookup"><span data-stu-id="06a8b-126">You can also make the same API call for any personal chat to obtain the profile information of the user chatting with your bot.</span></span>

<span data-ttu-id="06a8b-127">Die API-Aufruf-und SDK-Methoden sind identisch mit dem Abrufen des Team Arbeitsplans, ebenso wie das Response-Objekt.</span><span class="sxs-lookup"><span data-stu-id="06a8b-127">The API call and SDK methods are identical to fetching the team roster, as is the response object.</span></span> <span data-ttu-id="06a8b-128">Der einzige Unterschied besteht darin, dass Sie den `conversationId` anstelle von übergeben `teamId` .</span><span class="sxs-lookup"><span data-stu-id="06a8b-128">The only difference is you pass the `conversationId` instead of the `teamId`.</span></span>

## <a name="fetching-the-list-of-channels-in-a-team"></a><span data-ttu-id="06a8b-129">Abrufen der Liste der Kanäle in einem Team</span><span class="sxs-lookup"><span data-stu-id="06a8b-129">Fetching the list of channels in a team</span></span>

<span data-ttu-id="06a8b-130">Ihr Bot kann die Liste der Kanäle in einem Teamabfragen.</span><span class="sxs-lookup"><span data-stu-id="06a8b-130">Your bot can query the list of channels in a team.</span></span>

> [!NOTE]
>
>* <span data-ttu-id="06a8b-131">Der Name des standardmäßigen allgemeinen Kanals wird zurückgegeben `null` , um die Lokalisierung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="06a8b-131">The name of the default General channel is returned as `null` to allow for localization.</span></span>
>* <span data-ttu-id="06a8b-132">Die Kanal-ID für den allgemeinen Kanal stimmt immer mit der Team-ID überein.</span><span class="sxs-lookup"><span data-stu-id="06a8b-132">The channel ID for the General channel always matches the team ID.</span></span>

### <a name="rest-api-example"></a><span data-ttu-id="06a8b-133">Rest-API-Beispiel</span><span class="sxs-lookup"><span data-stu-id="06a8b-133">REST API example</span></span>

<span data-ttu-id="06a8b-134">Sie können eine GET-Anforderung direkt unter `/teams/{teamId}/conversations/` Verwendung des Werts von `serviceUrl` als Endpunkt ausgeben.</span><span class="sxs-lookup"><span data-stu-id="06a8b-134">You can directly issue a GET request on `/teams/{teamId}/conversations/`, using the value of `serviceUrl` as the endpoint.</span></span>

<span data-ttu-id="06a8b-135">Die einzige Quelle für `teamId` ist eine Nachricht aus dem Teamkontext-entweder eine Nachricht von einem Benutzer oder die Nachricht, die ihr bot erhält, wenn er einem Team hinzugefügt wird (siehe [bot oder Benutzer, der einem Team hinzugefügt](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition)wurde).</span><span class="sxs-lookup"><span data-stu-id="06a8b-135">The only source for `teamId` is a message from the team context - either a message from a user or the message that your bot receives when it is added to a team (see [Bot or user added to a team](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition)).</span></span>

> [!NOTE]
> <span data-ttu-id="06a8b-136">Der Wert von `serviceUrl` neigt dazu, stabil zu sein, aber kann sich ändern.</span><span class="sxs-lookup"><span data-stu-id="06a8b-136">The value of `serviceUrl` tends to be stable but can change.</span></span> <span data-ttu-id="06a8b-137">Wenn eine neue Nachricht eintrifft, sollte Ihr bot den gespeicherten Wert von überprüfen `serviceUrl` .</span><span class="sxs-lookup"><span data-stu-id="06a8b-137">When a new message arrives, your bot should verify its stored value of `serviceUrl`.</span></span>

```json
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

#### <a name="net-example"></a><span data-ttu-id="06a8b-138">.NET-Beispiel</span><span class="sxs-lookup"><span data-stu-id="06a8b-138">.NET example</span></span>

<span data-ttu-id="06a8b-139">Im folgenden Beispiel wird der `FetchChannelList` Aufruf von den [Microsoft Teams-Erweiterungen für das bot Builder SDK für .net](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams)verwendet:</span><span class="sxs-lookup"><span data-stu-id="06a8b-139">The following example uses the `FetchChannelList` call from the [Microsoft Teams extensions for the Bot Builder SDK for .NET](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams):</span></span>

```csharp
ConversationList channels = client.GetTeamsConnectorClient().Teams.FetchChannelList(activity.GetChannelData<TeamsChannelData>().Team.Id);
```

#### <a name="nodejs-example"></a><span data-ttu-id="06a8b-140">Node.js Beispiel</span><span class="sxs-lookup"><span data-stu-id="06a8b-140">Node.js example</span></span>

<span data-ttu-id="06a8b-141">Im folgenden Beispiel wird der `fetchChannelList` Aufruf von [Microsoft Teams-Erweiterungen für das bot Builder SDK für #b0 ](https://www.npmjs.com/package/botbuilder-teams)verwendet.</span><span class="sxs-lookup"><span data-stu-id="06a8b-141">The following example uses `fetchChannelList` call from the [Microsoft Teams extensions for the Bot Builder SDK for Node.js](https://www.npmjs.com/package/botbuilder-teams).</span></span>

```javascript
var teamId = session.message.sourceEvent.team.id;
connector.fetchChannelList(
  (session.message.address).serviceUrl,
  teamId,
  (err, result) => {
    if (err) {
      session.endDialog('There is an error');
    }
    else {
      session.endDialog('%s', JSON.stringify(result));
    }
  }
);
```
