---
title: Erhalten Sie Kontext für Ihren Microsoft Teams-Bot
description: Beschreibt, wie Sie Kontext für Bots in Microsoft Teams
keywords: Teams Bots Kontext
ms.topic: conceptual
localization_priority: Normal
ms.date: 05/20/2019
ms.openlocfilehash: cda2e24816330964342b097f52bb955c8846c54a
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566488"
---
# <a name="get-context-for-your-microsoft-teams-bot"></a><span data-ttu-id="1e06c-104">Erhalten Sie Kontext für Ihren Microsoft Teams-Bot</span><span class="sxs-lookup"><span data-stu-id="1e06c-104">Get context for your Microsoft Teams bot</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="1e06c-105">Ihr Bot kann auf zusätzlichen Kontext über das Team oder den Chat zugreifen, z. B. auf das Benutzerprofil.</span><span class="sxs-lookup"><span data-stu-id="1e06c-105">Your bot can access additional context about the team or chat, such as user profile.</span></span> <span data-ttu-id="1e06c-106">Diese Informationen können verwendet werden, um die Funktionalität Ihres Bots zu bereichern und eine personalisierteerfahrung zu bieten.</span><span class="sxs-lookup"><span data-stu-id="1e06c-106">This information can be used to enrich your bot's functionality and provide a more personalized experience.</span></span>

> [!NOTE]
>
> * <span data-ttu-id="1e06c-107">Microsoft Teams-spezifische Bot-APIs sind am besten über unsere Erweiterungen für das Bot Builder SDK zugänglich.</span><span class="sxs-lookup"><span data-stu-id="1e06c-107">Microsoft Teams-specific bot APIs are best accessed through our extensions for the Bot Builder SDK.</span></span>
> * <span data-ttu-id="1e06c-108">Laden Sie unser [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet-Paket herunter.</span><span class="sxs-lookup"><span data-stu-id="1e06c-108">For C# or .NET, download our [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet package.</span></span>
> * <span data-ttu-id="1e06c-109">Für Node.js Entwicklung ist der Bot Builder für Teams Funktionalität in das [Bot Framework SDK](https://github.com/microsoft/botframework-sdk) v4.6 integriert.</span><span class="sxs-lookup"><span data-stu-id="1e06c-109">For Node.js development, the Bot Builder for Teams functionality is incorporated into the [Bot Framework SDK](https://github.com/microsoft/botframework-sdk) v4.6.</span></span>

## <a name="fetch-the-team-roster"></a><span data-ttu-id="1e06c-110">Abrufen des Team-Kaders</span><span class="sxs-lookup"><span data-stu-id="1e06c-110">Fetch the team roster</span></span>

<span data-ttu-id="1e06c-111">Ihr Bot kann die Liste der Teammitglieder und deren Grundlegende Profile abfragen.</span><span class="sxs-lookup"><span data-stu-id="1e06c-111">Your bot can query for the list of team members and their basic profiles.</span></span> <span data-ttu-id="1e06c-112">Die Basisprofile enthalten Teams Benutzer-IDs und Azure Active Directory (AAD)-Informationen wie Name und Objekt-ID.</span><span class="sxs-lookup"><span data-stu-id="1e06c-112">The basic profiles include Teams user IDs and Azure Active Directory (AAD) information such as name and object ID.</span></span> <span data-ttu-id="1e06c-113">Sie können diese Informationen verwenden, um Benutzeridentitäten zu korrelieren.</span><span class="sxs-lookup"><span data-stu-id="1e06c-113">You can use this information to correlate user identities.</span></span> <span data-ttu-id="1e06c-114">Überprüfen Sie beispielsweise, ob ein Benutzer, der sich über AAD-Anmeldeinformationen bei einer Registerkarte angemeldet hat, ein Teammitglied ist.</span><span class="sxs-lookup"><span data-stu-id="1e06c-114">For example, check if a user logged into a tab through AAD credentials is a team member.</span></span>

### <a name="rest-api-example"></a><span data-ttu-id="1e06c-115">REST-API-Beispiel</span><span class="sxs-lookup"><span data-stu-id="1e06c-115">REST API example</span></span>

<span data-ttu-id="1e06c-116">Geben Sie direkt eine GET-Anforderung an [`/conversations/{teamId}/members/`](/bot-framework/rest-api/bot-framework-rest-connector-api-reference#get-conversation-members) , mit dem Wert als `serviceUrl` Endpunkt.</span><span class="sxs-lookup"><span data-stu-id="1e06c-116">Directly issue a GET request on [`/conversations/{teamId}/members/`](/bot-framework/rest-api/bot-framework-rest-connector-api-reference#get-conversation-members), using the `serviceUrl` value as the endpoint.</span></span>

<span data-ttu-id="1e06c-117">Die `teamId` befindet sich im Objekt der `channeldata` Aktivitätsnutzlast, die Ihr Bot in den folgenden Szenarien empfängt:</span><span class="sxs-lookup"><span data-stu-id="1e06c-117">The `teamId` can be found in the `channeldata` object of the activity payload that your bot receives in the following scenarios:</span></span>

* <span data-ttu-id="1e06c-118">Wenn ein Benutzer in einem Teamkontext Nachrichten eingibt oder mit Ihrem Bot interagiert.</span><span class="sxs-lookup"><span data-stu-id="1e06c-118">When a user messages or interacts with your bot in a team context.</span></span> <span data-ttu-id="1e06c-119">Weitere Informationen finden Sie unter [Empfangen von Nachrichten](~/resources/bot-v3/bot-conversations/bots-conversations.md#receiving-messages).</span><span class="sxs-lookup"><span data-stu-id="1e06c-119">For more information, see [receiving messages](~/resources/bot-v3/bot-conversations/bots-conversations.md#receiving-messages).</span></span>
* <span data-ttu-id="1e06c-120">Wenn ein neuer Benutzer oder Bot zu einem Team hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="1e06c-120">When a new user or bot is added to a team.</span></span> <span data-ttu-id="1e06c-121">Weitere Informationen finden Sie unter [Bot oder Benutzer, die einem Team hinzugefügt wurden.](~/resources/bot-v3/bots-notifications.md#bot-or-user-added-to-a-team)</span><span class="sxs-lookup"><span data-stu-id="1e06c-121">For more information, see [bot or user added to a team](~/resources/bot-v3/bots-notifications.md#bot-or-user-added-to-a-team).</span></span>

> [!NOTE]
>
>* <span data-ttu-id="1e06c-122">Verwenden Sie immer die Team-ID, wenn Sie die API aufrufen.</span><span class="sxs-lookup"><span data-stu-id="1e06c-122">Always use the team ID when calling the API.</span></span>
>* <span data-ttu-id="1e06c-123">Der `serviceUrl` Wert ist tendenziell stabil, kann sich aber ändern.</span><span class="sxs-lookup"><span data-stu-id="1e06c-123">The `serviceUrl` value tends to be stable but can change.</span></span> <span data-ttu-id="1e06c-124">Wenn eine neue Nachricht eintrifft, muss Ihr Bot seinen gespeicherten `serviceUrl` Wert überprüfen.</span><span class="sxs-lookup"><span data-stu-id="1e06c-124">When a new message arrives, your bot must verify its stored `serviceUrl` value.</span></span>

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

### <a name="net-example"></a><span data-ttu-id="1e06c-125">.NET-Beispiel</span><span class="sxs-lookup"><span data-stu-id="1e06c-125">.NET example</span></span>

<span data-ttu-id="1e06c-126">Rufen `GetConversationMembersAsync` Sie `Team.Id` mit, um eine Liste der Benutzer-IDs zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="1e06c-126">Call `GetConversationMembersAsync` using `Team.Id` to return a list of user IDs.</span></span>

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

### <a name="nodejs-or-typescript-example"></a><span data-ttu-id="1e06c-127">Node.js oder TypeScript-Beispiel</span><span class="sxs-lookup"><span data-stu-id="1e06c-127">Node.js or TypeScript example</span></span>

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

## <a name="fetch-user-profile-or-roster-in-personal-or-group-chat"></a><span data-ttu-id="1e06c-128">Abrufen von Benutzerprofil oder Dienstplan im persönlichen oder Gruppenchat</span><span class="sxs-lookup"><span data-stu-id="1e06c-128">Fetch user profile or roster in personal or group chat</span></span>

<span data-ttu-id="1e06c-129">Sie können den API-Aufruf für jeden persönlichen Chat durchführen, um die Profilinformationen des Benutzers zu erhalten, der mit Ihrem Bot chattet.</span><span class="sxs-lookup"><span data-stu-id="1e06c-129">You can make the API call for any personal chat to obtain the profile information of the user chatting with your bot.</span></span>

<span data-ttu-id="1e06c-130">Der API-Aufruf, die SDK-Methoden und das Antwortobjekt sind identisch mit dem Abrufen der Teamliste.</span><span class="sxs-lookup"><span data-stu-id="1e06c-130">The API call, SDK methods, and the response object are identical to fetching the team roster.</span></span> <span data-ttu-id="1e06c-131">Der einzige Unterschied besteht darin, dass Sie die `conversationId` anstelle der `teamId` übergeben.</span><span class="sxs-lookup"><span data-stu-id="1e06c-131">The only difference is you pass the `conversationId` instead of the `teamId`.</span></span>

## <a name="fetch-the-list-of-channels-in-a-team"></a><span data-ttu-id="1e06c-132">Abrufen der Liste der Kanäle in einem Team</span><span class="sxs-lookup"><span data-stu-id="1e06c-132">Fetch the list of channels in a team</span></span>

<span data-ttu-id="1e06c-133">Ihr Bot kann die Liste der Kanäle in einem Team abfragen.</span><span class="sxs-lookup"><span data-stu-id="1e06c-133">Your bot can query the list of channels in a team.</span></span>

> [!NOTE]
>
>* <span data-ttu-id="1e06c-134">Der Name des Standardkanals "Allgemein" wird `null` zurückgegeben, um die Lokalisierung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="1e06c-134">The name of the default General channel is returned as `null` to allow for localization.</span></span>
>* <span data-ttu-id="1e06c-135">Die Kanal-ID für den allgemeinen Kanal stimmt immer mit der Team-ID überein.</span><span class="sxs-lookup"><span data-stu-id="1e06c-135">The channel ID for the General channel always matches the team ID.</span></span>

### <a name="rest-api-example"></a><span data-ttu-id="1e06c-136">REST-API-Beispiel</span><span class="sxs-lookup"><span data-stu-id="1e06c-136">REST API example</span></span>

<span data-ttu-id="1e06c-137">Geben Sie direkt eine GET-Anforderung an `/teams/{teamId}/conversations/` , mit dem Wert als `serviceUrl` Endpunkt.</span><span class="sxs-lookup"><span data-stu-id="1e06c-137">Directly issue a GET request on `/teams/{teamId}/conversations/`, using the `serviceUrl` value as the endpoint.</span></span>

<span data-ttu-id="1e06c-138">Die einzige Quelle für `teamId` ist eine Nachricht aus dem Teamkontext.</span><span class="sxs-lookup"><span data-stu-id="1e06c-138">The only source for `teamId` is a message from the team context.</span></span> <span data-ttu-id="1e06c-139">Die Nachricht ist entweder eine Nachricht von einem Benutzer oder die Nachricht, die Ihr Bot empfängt, wenn er einem Team hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="1e06c-139">The message is either a message from a user or the message that your bot receives when it is added to a team.</span></span> <span data-ttu-id="1e06c-140">Weitere Informationen finden Sie unter [Bot oder Benutzer, die einem Team hinzugefügt wurden.](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition)</span><span class="sxs-lookup"><span data-stu-id="1e06c-140">For more information, see [bot or user added to a team](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition).</span></span>

> [!NOTE]
> <span data-ttu-id="1e06c-141">Der `serviceUrl` Wert ist tendenziell stabil, kann sich aber ändern.</span><span class="sxs-lookup"><span data-stu-id="1e06c-141">The `serviceUrl` value tends to be stable but can change.</span></span> <span data-ttu-id="1e06c-142">Wenn eine neue Nachricht eintrifft, muss Ihr Bot seinen gespeicherten `serviceUrl` Wert überprüfen.</span><span class="sxs-lookup"><span data-stu-id="1e06c-142">When a new message arrives, your bot must verify its stored `serviceUrl` value.</span></span>

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

#### <a name="net-example"></a><span data-ttu-id="1e06c-143">.NET-Beispiel</span><span class="sxs-lookup"><span data-stu-id="1e06c-143">.NET example</span></span>

<span data-ttu-id="1e06c-144">Im folgenden Beispiel wird der `FetchChannelList` Aufruf aus den Teams [Erweiterungen für das Bot Builder SDK für .NET](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams)verwendet:</span><span class="sxs-lookup"><span data-stu-id="1e06c-144">The following example uses the `FetchChannelList` call from the [Teams extensions for the Bot Builder SDK for .NET](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams):</span></span>

```csharp
ConversationList channels = client.GetTeamsConnectorClient().Teams.FetchChannelList(activity.GetChannelData<TeamsChannelData>().Team.Id);
```

#### <a name="nodejs-example"></a><span data-ttu-id="1e06c-145">Node.js Beispiel</span><span class="sxs-lookup"><span data-stu-id="1e06c-145">Node.js example</span></span>

<span data-ttu-id="1e06c-146">Im folgenden Beispiel wird `fetchChannelList` der Aufruf aus den Teams [Erweiterungen für das Bot Builder SDK für Node.js](https://www.npmjs.com/package/botbuilder-teams)verwendet:</span><span class="sxs-lookup"><span data-stu-id="1e06c-146">The following example uses `fetchChannelList` call from the [Teams extensions for the Bot Builder SDK for Node.js](https://www.npmjs.com/package/botbuilder-teams):</span></span>

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

## <a name="get-clientinfo-in-your-bot-context"></a><span data-ttu-id="1e06c-147">Abrufen von clientInfo in Ihrem Bot-Kontext</span><span class="sxs-lookup"><span data-stu-id="1e06c-147">Get clientInfo in your bot context</span></span>

<span data-ttu-id="1e06c-148">Sie können die clientInfo innerhalb der Aktivität Ihres Bots abrufen.</span><span class="sxs-lookup"><span data-stu-id="1e06c-148">You can fetch the clientInfo within your bot's activity.</span></span> <span data-ttu-id="1e06c-149">ClientInfo enthält die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="1e06c-149">The clientInfo contains the following properties:</span></span>

* <span data-ttu-id="1e06c-150">Locale</span><span class="sxs-lookup"><span data-stu-id="1e06c-150">Locale</span></span>
* <span data-ttu-id="1e06c-151">Land</span><span class="sxs-lookup"><span data-stu-id="1e06c-151">Country</span></span>
* <span data-ttu-id="1e06c-152">Plattform</span><span class="sxs-lookup"><span data-stu-id="1e06c-152">Platform</span></span>
* <span data-ttu-id="1e06c-153">Zeitzone</span><span class="sxs-lookup"><span data-stu-id="1e06c-153">Timezone</span></span>

### <a name="json-example"></a><span data-ttu-id="1e06c-154">JSON-Beispiel</span><span class="sxs-lookup"><span data-stu-id="1e06c-154">JSON example</span></span>

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

### <a name="c-example"></a><span data-ttu-id="1e06c-155">Beispiel für C-Code</span><span class="sxs-lookup"><span data-stu-id="1e06c-155">C# example</span></span>

```csharp
var connector = new ConnectorClient(new Uri(context.Activity.ServiceUrl));

{
    var clientinfo = context.Activity.Entities[0];
    await context.PostAsync($"ClientInfo: clientinfo ");
}
```

## <a name="see-also"></a><span data-ttu-id="1e06c-156">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="1e06c-156">See also</span></span>

<span data-ttu-id="1e06c-157">[Bot Framework-Beispiele](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).</span><span class="sxs-lookup"><span data-stu-id="1e06c-157">[Bot Framework samples](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).</span></span>