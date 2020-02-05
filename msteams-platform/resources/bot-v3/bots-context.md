---
title: Kontext für Ihren bot abrufen
description: Beschreibt, wie Kontext für Bots in Microsoft Teams abgerufen wird.
keywords: Teams-Bots-Kontext
ms.date: 05/20/2019
ms.openlocfilehash: 2dea6fd51e7274fa899d9ae882441a21618d7e09
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674567"
---
# <a name="get-context-for-your-microsoft-teams-bot"></a><span data-ttu-id="0569d-104">Kontext für Ihren Microsoft Teams-bot abrufen</span><span class="sxs-lookup"><span data-stu-id="0569d-104">Get context for your Microsoft Teams bot</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="0569d-105">Ihr Bot kann auf zusätzlichen Kontext über das Team oder den Chat zugreifen, beispielsweise auf das Benutzerprofil.</span><span class="sxs-lookup"><span data-stu-id="0569d-105">Your bot can access additional context about the team or chat, such as user profile.</span></span> <span data-ttu-id="0569d-106">Diese Informationen können verwendet werden, um die Funktionalität Ihres bot zu bereichern und eine personalisierte Erfahrung zu bieten.</span><span class="sxs-lookup"><span data-stu-id="0569d-106">This information can be used to enrich your bot's functionality and provide a more personalized experience.</span></span>

> [!NOTE]
> <span data-ttu-id="0569d-107">Diese Microsoft Teams&ndash;-spezifischen bot-APIs werden am besten über unsere Erweiterungen für das bot Builder SDK aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="0569d-107">These Microsoft Teams&ndash;specific bot APIs are best accessed through our extensions for the Bot Builder SDK.</span></span> <span data-ttu-id="0569d-108">Für C#-/.net laden Sie unser [Microsoft. bot. Connector. Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet-Paket herunter.</span><span class="sxs-lookup"><span data-stu-id="0569d-108">For C#/.NET, download our [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet package.</span></span> <span data-ttu-id="0569d-109">Für die Entwicklung von Node. js können Sie das NPM-Paket für [botbuilder-Teams](https://www.npmjs.com/package/botbuilder-teams) installieren.</span><span class="sxs-lookup"><span data-stu-id="0569d-109">For Node.js development, you can install the [botbuilder-teams](https://www.npmjs.com/package/botbuilder-teams) npm package.</span></span> <span data-ttu-id="0569d-110">Beide SDKs Zielen auf bot Builder v3 ab.</span><span class="sxs-lookup"><span data-stu-id="0569d-110">Both SDKs target Bot Builder v3.</span></span>

## <a name="fetching-the-team-roster"></a><span data-ttu-id="0569d-111">Abrufen des Team Arbeitsplans</span><span class="sxs-lookup"><span data-stu-id="0569d-111">Fetching the team roster</span></span>

<span data-ttu-id="0569d-112">Ihr Bot kann eine Abfrage für die Liste der Teammitglieder und ihrer grundlegenden profile durchführen, einschließlich Microsoft Teams-Benutzer-IDs und Azure Active Directory Informationen (Azure AD) wie Name und ObjectID.</span><span class="sxs-lookup"><span data-stu-id="0569d-112">Your bot can query for the list of team members and their basic profiles, which includes Teams user IDs and Azure Active Directory (Azure AD) information such as name and objectId.</span></span> <span data-ttu-id="0569d-113">Sie können diese Informationen verwenden, um Benutzeridentitäten zu korrelieren; um beispielsweise zu überprüfen, ob ein Benutzer, der bei einer Registerkarte über Azure AD Anmeldeinformationen angemeldet ist, ein Mitglied des Teams ist.</span><span class="sxs-lookup"><span data-stu-id="0569d-113">You can use this information to correlate user identities; for example, to check whether a user logged into a tab through Azure AD credentials is a member of the team.</span></span>

### <a name="rest-api-example"></a><span data-ttu-id="0569d-114">Rest-API-Beispiel</span><span class="sxs-lookup"><span data-stu-id="0569d-114">REST API example</span></span>

<span data-ttu-id="0569d-115">Sie können eine get [`/conversations/{teamId}/members/`](/bot-framework/rest-api/bot-framework-rest-connector-api-reference#get-conversation-members)-Anforderung direkt unter Verwendung des Werts von `serviceUrl` als Endpunkt ausgeben.</span><span class="sxs-lookup"><span data-stu-id="0569d-115">You can directly issue a GET request on [`/conversations/{teamId}/members/`](/bot-framework/rest-api/bot-framework-rest-connector-api-reference#get-conversation-members), using the value of `serviceUrl` as the endpoint.</span></span>

<span data-ttu-id="0569d-116">Der `teamId` kann im `channeldata` Objekt der Aktivitäts Nutzlast gefunden werden, die ihr bot in den folgenden Szenarien erhält:</span><span class="sxs-lookup"><span data-stu-id="0569d-116">The `teamId` can be found in the `channeldata` object of the activity payload that your bot receives in the following scenarios:</span></span>
* <span data-ttu-id="0569d-117">Wenn ein Benutzer mit dem bot in einem Teamkontext Nachrichten oder interagiert (siehe [empfangen von Nachrichten](~/resources/bot-v3/bot-conversations/bots-conversations.md#receiving-messages))</span><span class="sxs-lookup"><span data-stu-id="0569d-117">When a user messages or interacts with your bot in a team context (see [Receiving Messages](~/resources/bot-v3/bot-conversations/bots-conversations.md#receiving-messages))</span></span>
* <span data-ttu-id="0569d-118">Wenn einem Team ein neuer Benutzer oder bot hinzugefügt wird (siehe [bot oder Benutzer, der einem Team hinzugefügt](~/resources/bot-v3/bots-notifications.md#bot-or-user-added-to-a-team)wurde)</span><span class="sxs-lookup"><span data-stu-id="0569d-118">When a new user or bot is added to a team (see [Bot or user added to a team](~/resources/bot-v3/bots-notifications.md#bot-or-user-added-to-a-team))</span></span>

> [!NOTE]
>* <span data-ttu-id="0569d-119">Stellen Sie sicher, dass Sie die Team-ID verwenden, wenn Sie die API aufrufen</span><span class="sxs-lookup"><span data-stu-id="0569d-119">Make sure to use the team id when calling the api</span></span>
>* <span data-ttu-id="0569d-120">Der Wert von `serviceUrl` neigt dazu, stabil zu sein, aber kann sich ändern.</span><span class="sxs-lookup"><span data-stu-id="0569d-120">The value of `serviceUrl` tends to be stable but can change.</span></span> <span data-ttu-id="0569d-121">Wenn eine neue Nachricht eintrifft, sollte Ihr bot den gespeicherten Wert von `serviceUrl`überprüfen.</span><span class="sxs-lookup"><span data-stu-id="0569d-121">When a new message arrives, your bot should verify its stored value of `serviceUrl`.</span></span>

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

### <a name="net-example"></a><span data-ttu-id="0569d-122">.NET-Beispiel</span><span class="sxs-lookup"><span data-stu-id="0569d-122">.NET example</span></span>

<span data-ttu-id="0569d-123">Aufrufen `GetConversationMembersAsync` mit `Team.Id` , um eine Liste von Benutzer-IDs zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="0569d-123">Call `GetConversationMembersAsync` using `Team.Id` to return a list of user IDs.</span></span>

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

### <a name="nodejstypescript-example"></a><span data-ttu-id="0569d-124">Beispiel für Node. js/Transcript</span><span class="sxs-lookup"><span data-stu-id="0569d-124">Node.js/TypeScript example</span></span>

<span data-ttu-id="0569d-125">Im folgenden Beispiel werden die [Microsoft Teams-Erweiterungen für das bot Builder SDK für Node. js](https://www.npmjs.com/package/botbuilder-teams)verwendet.</span><span class="sxs-lookup"><span data-stu-id="0569d-125">The following example uses the [Microsoft Teams extensions for the Bot Builder SDK for Node.js](https://www.npmjs.com/package/botbuilder-teams).</span></span>

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

## <a name="fetching-user-profile-or-roster-in-personal-or-group-chat"></a><span data-ttu-id="0569d-126">Abrufen von Benutzerprofilen oder Dienstplänen im persönlichen oder Gruppenchat</span><span class="sxs-lookup"><span data-stu-id="0569d-126">Fetching user profile or roster in personal or group chat</span></span>

<span data-ttu-id="0569d-127">Sie können auch denselben API-Aufruf für einen persönlichen Chat durchführen, um die Profilinformationen des Benutzers zu erhalten, der mit Ihrem bot chattet.</span><span class="sxs-lookup"><span data-stu-id="0569d-127">You can also make the same API call for any personal chat to obtain the profile information of the user chatting with your bot.</span></span>

<span data-ttu-id="0569d-128">Die API-Aufruf-und SDK-Methoden sind identisch mit dem Abrufen des Team Arbeitsplans, ebenso wie das Response-Objekt.</span><span class="sxs-lookup"><span data-stu-id="0569d-128">The API call and SDK methods are identical to fetching the team roster, as is the response object.</span></span> <span data-ttu-id="0569d-129">Der einzige Unterschied besteht darin, `conversationId` dass Sie den `teamId`anstelle von übergeben.</span><span class="sxs-lookup"><span data-stu-id="0569d-129">The only difference is you pass the `conversationId` instead of the `teamId`.</span></span>

## <a name="fetching-the-list-of-channels-in-a-team"></a><span data-ttu-id="0569d-130">Abrufen der Liste der Kanäle in einem Team</span><span class="sxs-lookup"><span data-stu-id="0569d-130">Fetching the list of channels in a team</span></span>

<span data-ttu-id="0569d-131">Ihr Bot kann die Liste der Kanäle in einem Teamabfragen.</span><span class="sxs-lookup"><span data-stu-id="0569d-131">Your bot can query the list of channels in a team.</span></span>

> [!NOTE]
>
>* <span data-ttu-id="0569d-132">Der Name des standardmäßigen allgemeinen Kanals wird `null` zurückgegeben, um die Lokalisierung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="0569d-132">The name of the default General channel is returned as `null` to allow for localization.</span></span>
>* <span data-ttu-id="0569d-133">Die Kanal-ID für den allgemeinen Kanal stimmt immer mit der Team-ID überein.</span><span class="sxs-lookup"><span data-stu-id="0569d-133">The channel ID for the General channel always matches the team ID.</span></span>

### <a name="rest-api-example"></a><span data-ttu-id="0569d-134">Rest-API-Beispiel</span><span class="sxs-lookup"><span data-stu-id="0569d-134">REST API example</span></span>

<span data-ttu-id="0569d-135">Sie können eine get `/teams/{teamId}/conversations/`-Anforderung direkt unter Verwendung des Werts von `serviceUrl` als Endpunkt ausgeben.</span><span class="sxs-lookup"><span data-stu-id="0569d-135">You can directly issue a GET request on `/teams/{teamId}/conversations/`, using the value of `serviceUrl` as the endpoint.</span></span>

<span data-ttu-id="0569d-136">Die einzige Quelle für `teamId` ist eine Nachricht aus dem Teamkontext-entweder eine Nachricht von einem Benutzer oder die Nachricht, die ihr bot erhält, wenn er einem Team hinzugefügt wird (siehe [bot oder Benutzer, der einem Team hinzugefügt](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition)wurde).</span><span class="sxs-lookup"><span data-stu-id="0569d-136">The only source for `teamId` is a message from the team context - either a message from a user or the message that your bot receives when it is added to a team (see [Bot or user added to a team](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition)).</span></span>

> [!NOTE]
> <span data-ttu-id="0569d-137">Der Wert von `serviceUrl` neigt dazu, stabil zu sein, aber kann sich ändern.</span><span class="sxs-lookup"><span data-stu-id="0569d-137">The value of `serviceUrl` tends to be stable but can change.</span></span> <span data-ttu-id="0569d-138">Wenn eine neue Nachricht eintrifft, sollte Ihr bot den gespeicherten Wert von `serviceUrl`überprüfen.</span><span class="sxs-lookup"><span data-stu-id="0569d-138">When a new message arrives, your bot should verify its stored value of `serviceUrl`.</span></span>

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

#### <a name="net-example"></a><span data-ttu-id="0569d-139">.NET-Beispiel</span><span class="sxs-lookup"><span data-stu-id="0569d-139">.NET example</span></span>

<span data-ttu-id="0569d-140">Im folgenden Beispiel wird der `FetchChannelList` Aufruf von den [Microsoft Teams-Erweiterungen für das bot Builder SDK für .net](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams)verwendet:</span><span class="sxs-lookup"><span data-stu-id="0569d-140">The following example uses the `FetchChannelList` call from the [Microsoft Teams extensions for the Bot Builder SDK for .NET](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams):</span></span>

```csharp
ConversationList channels = client.GetTeamsConnectorClient().Teams.FetchChannelList(activity.GetChannelData<TeamsChannelData>().Team.Id);
```

#### <a name="nodejs-example"></a><span data-ttu-id="0569d-141">Node. js-Beispiel</span><span class="sxs-lookup"><span data-stu-id="0569d-141">Node.js example</span></span>

<span data-ttu-id="0569d-142">Im folgenden Beispiel wird `fetchChannelList` der Aufruf von [Microsoft Teams-Erweiterungen für das bot Builder SDK für Node. js](https://www.npmjs.com/package/botbuilder-teams)verwendet.</span><span class="sxs-lookup"><span data-stu-id="0569d-142">The following example uses `fetchChannelList` call from the [Microsoft Teams extensions for the Bot Builder SDK for Node.js](https://www.npmjs.com/package/botbuilder-teams).</span></span>

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