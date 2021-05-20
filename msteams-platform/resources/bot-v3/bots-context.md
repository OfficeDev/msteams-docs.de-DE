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
# <a name="get-context-for-your-microsoft-teams-bot"></a>Erhalten Sie Kontext für Ihren Microsoft Teams-Bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Ihr Bot kann auf zusätzlichen Kontext über das Team oder den Chat zugreifen, z. B. auf das Benutzerprofil. Diese Informationen können verwendet werden, um die Funktionalität Ihres Bots zu bereichern und eine personalisierteerfahrung zu bieten.

> [!NOTE]
>
> * Microsoft Teams-spezifische Bot-APIs sind am besten über unsere Erweiterungen für das Bot Builder SDK zugänglich.
> * Laden Sie unser [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet-Paket herunter.
> * Für Node.js Entwicklung ist der Bot Builder für Teams Funktionalität in das [Bot Framework SDK](https://github.com/microsoft/botframework-sdk) v4.6 integriert.

## <a name="fetch-the-team-roster"></a>Abrufen des Team-Kaders

Ihr Bot kann die Liste der Teammitglieder und deren Grundlegende Profile abfragen. Die Basisprofile enthalten Teams Benutzer-IDs und Azure Active Directory (AAD)-Informationen wie Name und Objekt-ID. Sie können diese Informationen verwenden, um Benutzeridentitäten zu korrelieren. Überprüfen Sie beispielsweise, ob ein Benutzer, der sich über AAD-Anmeldeinformationen bei einer Registerkarte angemeldet hat, ein Teammitglied ist.

### <a name="rest-api-example"></a>REST-API-Beispiel

Geben Sie direkt eine GET-Anforderung an [`/conversations/{teamId}/members/`](/bot-framework/rest-api/bot-framework-rest-connector-api-reference#get-conversation-members) , mit dem Wert als `serviceUrl` Endpunkt.

Die `teamId` befindet sich im Objekt der `channeldata` Aktivitätsnutzlast, die Ihr Bot in den folgenden Szenarien empfängt:

* Wenn ein Benutzer in einem Teamkontext Nachrichten eingibt oder mit Ihrem Bot interagiert. Weitere Informationen finden Sie unter [Empfangen von Nachrichten](~/resources/bot-v3/bot-conversations/bots-conversations.md#receiving-messages).
* Wenn ein neuer Benutzer oder Bot zu einem Team hinzugefügt wird. Weitere Informationen finden Sie unter [Bot oder Benutzer, die einem Team hinzugefügt wurden.](~/resources/bot-v3/bots-notifications.md#bot-or-user-added-to-a-team)

> [!NOTE]
>
>* Verwenden Sie immer die Team-ID, wenn Sie die API aufrufen.
>* Der `serviceUrl` Wert ist tendenziell stabil, kann sich aber ändern. Wenn eine neue Nachricht eintrifft, muss Ihr Bot seinen gespeicherten `serviceUrl` Wert überprüfen.

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

### <a name="net-example"></a>.NET-Beispiel

Rufen `GetConversationMembersAsync` Sie `Team.Id` mit, um eine Liste der Benutzer-IDs zurückzugeben.

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

### <a name="nodejs-or-typescript-example"></a>Node.js oder TypeScript-Beispiel

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

## <a name="fetch-user-profile-or-roster-in-personal-or-group-chat"></a>Abrufen von Benutzerprofil oder Dienstplan im persönlichen oder Gruppenchat

Sie können den API-Aufruf für jeden persönlichen Chat durchführen, um die Profilinformationen des Benutzers zu erhalten, der mit Ihrem Bot chattet.

Der API-Aufruf, die SDK-Methoden und das Antwortobjekt sind identisch mit dem Abrufen der Teamliste. Der einzige Unterschied besteht darin, dass Sie die `conversationId` anstelle der `teamId` übergeben.

## <a name="fetch-the-list-of-channels-in-a-team"></a>Abrufen der Liste der Kanäle in einem Team

Ihr Bot kann die Liste der Kanäle in einem Team abfragen.

> [!NOTE]
>
>* Der Name des Standardkanals "Allgemein" wird `null` zurückgegeben, um die Lokalisierung zu ermöglichen.
>* Die Kanal-ID für den allgemeinen Kanal stimmt immer mit der Team-ID überein.

### <a name="rest-api-example"></a>REST-API-Beispiel

Geben Sie direkt eine GET-Anforderung an `/teams/{teamId}/conversations/` , mit dem Wert als `serviceUrl` Endpunkt.

Die einzige Quelle für `teamId` ist eine Nachricht aus dem Teamkontext. Die Nachricht ist entweder eine Nachricht von einem Benutzer oder die Nachricht, die Ihr Bot empfängt, wenn er einem Team hinzugefügt wird. Weitere Informationen finden Sie unter [Bot oder Benutzer, die einem Team hinzugefügt wurden.](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition)

> [!NOTE]
> Der `serviceUrl` Wert ist tendenziell stabil, kann sich aber ändern. Wenn eine neue Nachricht eintrifft, muss Ihr Bot seinen gespeicherten `serviceUrl` Wert überprüfen.

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

#### <a name="net-example"></a>.NET-Beispiel

Im folgenden Beispiel wird der `FetchChannelList` Aufruf aus den Teams [Erweiterungen für das Bot Builder SDK für .NET](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams)verwendet:

```csharp
ConversationList channels = client.GetTeamsConnectorClient().Teams.FetchChannelList(activity.GetChannelData<TeamsChannelData>().Team.Id);
```

#### <a name="nodejs-example"></a>Node.js Beispiel

Im folgenden Beispiel wird `fetchChannelList` der Aufruf aus den Teams [Erweiterungen für das Bot Builder SDK für Node.js](https://www.npmjs.com/package/botbuilder-teams)verwendet:

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

## <a name="get-clientinfo-in-your-bot-context"></a>Abrufen von clientInfo in Ihrem Bot-Kontext

Sie können die clientInfo innerhalb der Aktivität Ihres Bots abrufen. ClientInfo enthält die folgenden Eigenschaften:

* Locale
* Land
* Plattform
* Zeitzone

### <a name="json-example"></a>JSON-Beispiel

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

### <a name="c-example"></a>Beispiel für C-Code

```csharp
var connector = new ConnectorClient(new Uri(context.Activity.ServiceUrl));

{
    var clientinfo = context.Activity.Entities[0];
    await context.PostAsync($"ClientInfo: clientinfo ");
}
```

## <a name="see-also"></a>Siehe auch

[Bot Framework-Beispiele](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).