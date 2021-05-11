---
title: Kontext für Ihren Microsoft Teams erhalten
description: Beschreibt, wie Sie Kontext für Bots in Microsoft Teams
keywords: teams bots context
ms.topic: conceptual
localization_priority: Normal
ms.date: 05/20/2019
ms.openlocfilehash: 154a276c65987955cfe20e5b7ce4ed2e8973cbfd
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020660"
---
# <a name="get-context-for-your-microsoft-teams-bot"></a><span data-ttu-id="efe21-104">Kontext für Ihren Microsoft Teams erhalten</span><span class="sxs-lookup"><span data-stu-id="efe21-104">Get context for your Microsoft Teams bot</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="efe21-105">Ihr Bot kann auf zusätzlichen Kontext über das Team oder den Chat zugreifen, z. B. auf das Benutzerprofil.</span><span class="sxs-lookup"><span data-stu-id="efe21-105">Your bot can access additional context about the team or chat, such as user profile.</span></span> <span data-ttu-id="efe21-106">Diese Informationen können verwendet werden, um die Funktionalität Ihres Bots zu erweitern und eine personalisiertere Benutzererfahrung zu bieten.</span><span class="sxs-lookup"><span data-stu-id="efe21-106">This information can be used to enrich your bot's functionality and provide a more personalized experience.</span></span>

> [!NOTE]
>
> * <span data-ttu-id="efe21-107">Microsoft Teams bot-APIs werden am besten über unsere Erweiterungen für das Bot Builder SDK zugegriffen.</span><span class="sxs-lookup"><span data-stu-id="efe21-107">Microsoft Teams-specific bot APIs are best accessed through our extensions for the Bot Builder SDK.</span></span>
> * <span data-ttu-id="efe21-108">Für C# oder .NET laden Sie unser [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet herunter.</span><span class="sxs-lookup"><span data-stu-id="efe21-108">For C# or .NET, download our [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet package.</span></span>
> * <span data-ttu-id="efe21-109">Für Node.js Entwicklung ist der Bot Builder für Teams in [das Bot Framework SDK](https://github.com/microsoft/botframework-sdk) v4.6 integriert.</span><span class="sxs-lookup"><span data-stu-id="efe21-109">For Node.js development, the Bot Builder for Teams functionality is incorporated into the [Bot Framework SDK](https://github.com/microsoft/botframework-sdk) v4.6.</span></span>

## <a name="fetch-the-team-roster"></a><span data-ttu-id="efe21-110">Abrufen der Teamliste</span><span class="sxs-lookup"><span data-stu-id="efe21-110">Fetch the team roster</span></span>

<span data-ttu-id="efe21-111">Ihr Bot kann die Liste der Teammitglieder und deren Basisprofile abfragen.</span><span class="sxs-lookup"><span data-stu-id="efe21-111">Your bot can query for the list of team members and their basic profiles.</span></span> <span data-ttu-id="efe21-112">Die grundlegenden Profile umfassen Teams Benutzer-IDs und Azure Active Directory (AAD) wie Name und Objekt-ID.</span><span class="sxs-lookup"><span data-stu-id="efe21-112">The basic profiles include Teams user IDs and Azure Active Directory (AAD) information such as name and object ID.</span></span> <span data-ttu-id="efe21-113">Sie können diese Informationen verwenden, um Benutzeridentitäten zu korrelieren.</span><span class="sxs-lookup"><span data-stu-id="efe21-113">You can use this information to correlate user identities.</span></span> <span data-ttu-id="efe21-114">Überprüfen Sie beispielsweise, ob ein Benutzer, der sich über AAD-Anmeldeinformationen bei einer Registerkarte angemeldet hat, ein Teammitglied ist.</span><span class="sxs-lookup"><span data-stu-id="efe21-114">For example, check if a user logged into a tab through AAD credentials is a team member.</span></span>

### <a name="rest-api-example"></a><span data-ttu-id="efe21-115">REST-API-Beispiel</span><span class="sxs-lookup"><span data-stu-id="efe21-115">REST API example</span></span>

<span data-ttu-id="efe21-116">Stellen Sie direkt eine GET-Anforderung für [`/conversations/{teamId}/members/`](/bot-framework/rest-api/bot-framework-rest-connector-api-reference#get-conversation-members) aus, und verwenden Sie `serviceUrl` den Wert als Endpunkt.</span><span class="sxs-lookup"><span data-stu-id="efe21-116">Directly issue a GET request on [`/conversations/{teamId}/members/`](/bot-framework/rest-api/bot-framework-rest-connector-api-reference#get-conversation-members), using the `serviceUrl` value as the endpoint.</span></span>

<span data-ttu-id="efe21-117">Die `teamId` finden Sie im Objekt der `channeldata` Aktivitätsnutzlast, die Ihr Bot in den folgenden Szenarien empfängt:</span><span class="sxs-lookup"><span data-stu-id="efe21-117">The `teamId` can be found in the `channeldata` object of the activity payload that your bot receives in the following scenarios:</span></span>

* <span data-ttu-id="efe21-118">Wenn ein Benutzer ihren Bot in einem Teamkontext ansagt oder mit ihm interagiert.</span><span class="sxs-lookup"><span data-stu-id="efe21-118">When a user messages or interacts with your bot in a team context.</span></span> <span data-ttu-id="efe21-119">Weitere Informationen finden Sie unter [Empfangen von Nachrichten](~/resources/bot-v3/bot-conversations/bots-conversations.md#receiving-messages).</span><span class="sxs-lookup"><span data-stu-id="efe21-119">For more information, see [receiving messages](~/resources/bot-v3/bot-conversations/bots-conversations.md#receiving-messages).</span></span>
* <span data-ttu-id="efe21-120">Wenn einem Team ein neuer Benutzer oder Bot hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="efe21-120">When a new user or bot is added to a team.</span></span> <span data-ttu-id="efe21-121">Weitere Informationen finden Sie unter [Bot oder Benutzer, der einem Team hinzugefügt wurde.](~/resources/bot-v3/bots-notifications.md#bot-or-user-added-to-a-team)</span><span class="sxs-lookup"><span data-stu-id="efe21-121">For more information, see [bot or user added to a team](~/resources/bot-v3/bots-notifications.md#bot-or-user-added-to-a-team).</span></span>

> [!NOTE]
>
>* <span data-ttu-id="efe21-122">Verwenden Sie beim Aufrufen der API immer die Team-ID.</span><span class="sxs-lookup"><span data-stu-id="efe21-122">Always use the team ID when calling the API.</span></span>
>* <span data-ttu-id="efe21-123">Der `serviceUrl` Wert ist in der Regel stabil, kann sich jedoch ändern.</span><span class="sxs-lookup"><span data-stu-id="efe21-123">The `serviceUrl` value tends to be stable but can change.</span></span> <span data-ttu-id="efe21-124">Wenn eine neue Nachricht eintrifft, muss Ihr Bot seinen gespeicherten Wert `serviceUrl` überprüfen.</span><span class="sxs-lookup"><span data-stu-id="efe21-124">When a new message arrives, your bot must verify its stored `serviceUrl` value.</span></span>

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

### <a name="net-example"></a><span data-ttu-id="efe21-125">.NET-Beispiel</span><span class="sxs-lookup"><span data-stu-id="efe21-125">.NET example</span></span>

<span data-ttu-id="efe21-126">Rufen `GetConversationMembersAsync` Sie die Verwendung `Team.Id` auf, um eine Liste der Benutzer-IDs zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="efe21-126">Call `GetConversationMembersAsync` using `Team.Id` to return a list of user IDs.</span></span>

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

### <a name="nodejs-or-typescript-example"></a><span data-ttu-id="efe21-127">Node.js oder TypeScript-Beispiel</span><span class="sxs-lookup"><span data-stu-id="efe21-127">Node.js or TypeScript example</span></span>

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

<span data-ttu-id="efe21-128">Weitere Informationen finden Sie unter [Bot Framework Samples](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).</span><span class="sxs-lookup"><span data-stu-id="efe21-128">Also, see [Bot Framework samples](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).</span></span>

## <a name="fetch-user-profile-or-roster-in-personal-or-group-chat"></a><span data-ttu-id="efe21-129">Abrufen von Benutzerprofilen oder -dienstplan in persönlichen Chats oder Gruppenchats</span><span class="sxs-lookup"><span data-stu-id="efe21-129">Fetch user profile or roster in personal or group chat</span></span>

<span data-ttu-id="efe21-130">Sie können den API-Aufruf für jeden persönlichen Chat machen, um die Profilinformationen des Benutzers zu erhalten, der mit Ihrem Bot chatt.</span><span class="sxs-lookup"><span data-stu-id="efe21-130">You can make the API call for any personal chat to obtain the profile information of the user chatting with your bot.</span></span>

<span data-ttu-id="efe21-131">Der API-Aufruf, die SDK-Methoden und das Antwortobjekt sind identisch mit dem Abrufen der Teamliste.</span><span class="sxs-lookup"><span data-stu-id="efe21-131">The API call, SDK methods, and the response object are identical to fetching the team roster.</span></span> <span data-ttu-id="efe21-132">Der einzige Unterschied ist, dass Sie anstelle des `conversationId` `teamId` übergeben.</span><span class="sxs-lookup"><span data-stu-id="efe21-132">The only difference is you pass the `conversationId` instead of the `teamId`.</span></span>

## <a name="fetch-the-list-of-channels-in-a-team"></a><span data-ttu-id="efe21-133">Abrufen der Liste der Kanäle in einem Team</span><span class="sxs-lookup"><span data-stu-id="efe21-133">Fetch the list of channels in a team</span></span>

<span data-ttu-id="efe21-134">Ihr Bot kann die Liste der Kanäle in einem Team abfragen.</span><span class="sxs-lookup"><span data-stu-id="efe21-134">Your bot can query the list of channels in a team.</span></span>

> [!NOTE]
>
>* <span data-ttu-id="efe21-135">Der Name des standardmäßigen allgemeinen Kanals wird zurückgegeben, `null` um die Lokalisierung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="efe21-135">The name of the default General channel is returned as `null` to allow for localization.</span></span>
>* <span data-ttu-id="efe21-136">Die Kanal-ID für den allgemeinen Kanal entspricht immer der Team-ID.</span><span class="sxs-lookup"><span data-stu-id="efe21-136">The channel ID for the General channel always matches the team ID.</span></span>

### <a name="rest-api-example"></a><span data-ttu-id="efe21-137">REST-API-Beispiel</span><span class="sxs-lookup"><span data-stu-id="efe21-137">REST API example</span></span>

<span data-ttu-id="efe21-138">Stellen Sie direkt eine GET-Anforderung für `/teams/{teamId}/conversations/` aus, und verwenden Sie `serviceUrl` den Wert als Endpunkt.</span><span class="sxs-lookup"><span data-stu-id="efe21-138">Directly issue a GET request on `/teams/{teamId}/conversations/`, using the `serviceUrl` value as the endpoint.</span></span>

<span data-ttu-id="efe21-139">Die einzige Quelle für `teamId` ist eine Nachricht aus dem Teamkontext.</span><span class="sxs-lookup"><span data-stu-id="efe21-139">The only source for `teamId` is a message from the team context.</span></span> <span data-ttu-id="efe21-140">Die Nachricht ist entweder eine Nachricht eines Benutzers oder die Nachricht, die Ihr Bot empfängt, wenn sie einem Team hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="efe21-140">The message is either a message from a user or the message that your bot receives when it is added to a team.</span></span> <span data-ttu-id="efe21-141">Weitere Informationen finden Sie unter [Bot oder Benutzer, der einem Team hinzugefügt wurde.](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition)</span><span class="sxs-lookup"><span data-stu-id="efe21-141">For more information, see [bot or user added to a team](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition).</span></span>

> [!NOTE]
> <span data-ttu-id="efe21-142">Der `serviceUrl` Wert ist in der Regel stabil, kann sich jedoch ändern.</span><span class="sxs-lookup"><span data-stu-id="efe21-142">The `serviceUrl` value tends to be stable but can change.</span></span> <span data-ttu-id="efe21-143">Wenn eine neue Nachricht eintrifft, muss Ihr Bot seinen gespeicherten Wert `serviceUrl` überprüfen.</span><span class="sxs-lookup"><span data-stu-id="efe21-143">When a new message arrives, your bot must verify its stored `serviceUrl` value.</span></span>

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

#### <a name="net-example"></a><span data-ttu-id="efe21-144">.NET-Beispiel</span><span class="sxs-lookup"><span data-stu-id="efe21-144">.NET example</span></span>

<span data-ttu-id="efe21-145">Im folgenden Beispiel wird der Aufruf aus den Teams für das `FetchChannelList` Bot Builder SDK für [.NET verwendet:](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams)</span><span class="sxs-lookup"><span data-stu-id="efe21-145">The following example uses the `FetchChannelList` call from the [Teams extensions for the Bot Builder SDK for .NET](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams):</span></span>

```csharp
ConversationList channels = client.GetTeamsConnectorClient().Teams.FetchChannelList(activity.GetChannelData<TeamsChannelData>().Team.Id);
```

#### <a name="nodejs-example"></a><span data-ttu-id="efe21-146">Node.js Beispiel</span><span class="sxs-lookup"><span data-stu-id="efe21-146">Node.js example</span></span>

<span data-ttu-id="efe21-147">Im folgenden Beispiel wird der Aufruf der Teams für das `fetchChannelList` Bot Builder SDK für [Node.js: ](https://www.npmjs.com/package/botbuilder-teams)</span><span class="sxs-lookup"><span data-stu-id="efe21-147">The following example uses `fetchChannelList` call from the [Teams extensions for the Bot Builder SDK for Node.js](https://www.npmjs.com/package/botbuilder-teams):</span></span>

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

## <a name="get-clientinfo-in-your-bot-context"></a><span data-ttu-id="efe21-148">ClientInfo in Ihrem Botkontext abrufen</span><span class="sxs-lookup"><span data-stu-id="efe21-148">Get clientInfo in your bot context</span></span>

<span data-ttu-id="efe21-149">Sie können die clientInfo innerhalb der Aktivität Ihres Bots abrufen.</span><span class="sxs-lookup"><span data-stu-id="efe21-149">You can fetch the clientInfo within your bot's activity.</span></span> <span data-ttu-id="efe21-150">Die clientInfo enthält die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="efe21-150">The clientInfo contains the following properties:</span></span>

* <span data-ttu-id="efe21-151">Locale</span><span class="sxs-lookup"><span data-stu-id="efe21-151">Locale</span></span>
* <span data-ttu-id="efe21-152">Land</span><span class="sxs-lookup"><span data-stu-id="efe21-152">Country</span></span>
* <span data-ttu-id="efe21-153">Plattform</span><span class="sxs-lookup"><span data-stu-id="efe21-153">Platform</span></span>
* <span data-ttu-id="efe21-154">Zeitzone</span><span class="sxs-lookup"><span data-stu-id="efe21-154">Timezone</span></span>

### <a name="json-example"></a><span data-ttu-id="efe21-155">JSON-Beispiel</span><span class="sxs-lookup"><span data-stu-id="efe21-155">JSON example</span></span>

```json
[
    {
        "type": "clientInfo",
        "locale": "en-US",
        "country": "US",
        "platform": "Windows",
        "timezone": "Asia/Calcutta"
    }
]
```

### <a name="c-example"></a><span data-ttu-id="efe21-156">C# Beispiel</span><span class="sxs-lookup"><span data-stu-id="efe21-156">C# example</span></span>

```csharp
var connector = new ConnectorClient(new Uri(context.Activity.ServiceUrl));

{
    var clientinfo = context.Activity.Entities[0];
    await context.PostAsync($"ClientInfo: clientinfo ");
}
```
