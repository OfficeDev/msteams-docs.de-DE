---
title: Abrufen des Kontexts für Ihren Microsoft Teams-Bot
description: Beschreibt, wie Kontext für Bots in Microsoft Teams
keywords: Teams-Bots-Kontext
ms.topic: conceptual
ms.localizationpriority: medium
ms.date: 05/20/2019
ms.openlocfilehash: c4f2df1168b5e429b1d5a1107cd07264e10243bc
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2022
ms.locfileid: "63453145"
---
# <a name="get-context-for-your-microsoft-teams-bot"></a>Abrufen des Kontexts für Ihren Microsoft Teams-Bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Ihr Bot kann auf zusätzlichen Kontext über das Team oder den Chat zugreifen, z. B. auf das Benutzerprofil. Diese Informationen können verwendet werden, um die Funktionalität Ihres Bots zu erweitern und eine personalisierte Erfahrung zu bieten.

> [!NOTE]
>
> * Microsoft Teams-spezifischen Bot-APIs können Sie am besten über unsere Erweiterungen für das Bot Builder SDK aufrufen.
> * Laden Sie für C# oder .NET unser [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet-Paket herunter.
> * Für Node.js Entwicklung ist der Bot Builder für Teams Funktionalität in das [Bot Framework SDK](https://github.com/microsoft/botframework-sdk) v4.6 integriert.

## <a name="fetch-the-team-roster"></a>Abrufen der Teamliste

Ihr Bot kann die Liste der Teammitglieder und deren grundlegende Profile abfragen. Die grundlegenden Profile umfassen Teams Benutzer-IDs und Microsoft Azure Active Directory (Azure AD) Informationen wie Name und Objekt-ID. Sie können diese Informationen verwenden, um Benutzeridentitäten zu korrelieren. Überprüfen Sie beispielsweise, ob ein Benutzer, der sich über Microsoft Azure Active Directory (Azure AD)-Anmeldeinformationen bei einer Registerkarte angemeldet hat, ein Teammitglied ist.

### <a name="rest-api-example"></a>REST-API-Beispiel

Stellen Sie direkt eine GET-Anforderung auf [`/conversations/{teamId}/members/`](/bot-framework/rest-api/bot-framework-rest-connector-api-reference#get-conversation-members), wobei der `serviceUrl` Wert als Endpunkt verwendet wird.

Dies `teamId` befindet sich im `channeldata` Objekt der Aktivitätsnutzlast, die Ihr Bot in den folgenden Szenarien empfängt:

* Wenn ein Benutzer nachrichten oder mit Ihrem Bot in einem Teamkontext interagiert. Weitere Informationen finden Sie unter ["Empfangen von Nachrichten](~/resources/bot-v3/bot-conversations/bots-conversations.md#receiving-messages)".
* Wenn ein neuer Benutzer oder Bot zu einem Team hinzugefügt wird. Weitere Informationen finden Sie unter [Bot oder Benutzer, der einem Team hinzugefügt wurde](~/resources/bot-v3/bots-notifications.md#bot-or-user-added-to-a-team).

> [!NOTE]
>
>* Verwenden Sie beim Aufrufen der API immer die Team-ID.
>* Der `serviceUrl` Wert ist in der Regel stabil, kann sich aber ändern. Wenn eine neue Nachricht eintrifft, muss Ihr Bot seinen gespeicherten `serviceUrl` Wert überprüfen.

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

Aufruf `GetConversationMembersAsync` , mit dem `Team.Id` eine Liste von Benutzer-IDs zurückgegeben wird.

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

### <a name="nodejs-or-typescript-example"></a>Node.js- oder TypeScript-Beispiel

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

## <a name="fetch-user-profile-or-roster-in-personal-or-group-chat"></a>Abrufen von Benutzerprofilen oder Listen in persönlichen Chats oder Gruppenchats

Sie können den API-Aufruf für jeden persönlichen Chat durchführen, um die Profilinformationen des Benutzers abzurufen, der mit Ihrem Bot chatten soll.

Der API-Aufruf, die SDK-Methoden und das Antwortobjekt sind identisch mit dem Abrufen der Teamliste. Der einzige Unterschied besteht darin, dass Sie anstelle `conversationId` der `teamId`.

## <a name="fetch-the-list-of-channels-in-a-team"></a>Abrufen der Liste der Kanäle in einem Team

Ihr Bot kann die Liste der Kanäle in einem Team abfragen.

> [!NOTE]
>
>* Der Name des standardmäßigen Kanals "Allgemein" wird zurückgegeben `null` , um die Lokalisierung zuzulassen.
>* Die Kanal-ID für den Kanal "Allgemein" stimmt immer mit der Team-ID überein.

### <a name="rest-api-example"></a>REST-API-Beispiel

Stellen Sie direkt eine GET-Anforderung auf `/teams/{teamId}/conversations/`, wobei der `serviceUrl` Wert als Endpunkt verwendet wird.

Die einzige Quelle ist `teamId` eine Nachricht aus dem Teamkontext. Die Nachricht ist entweder eine Nachricht von einem Benutzer oder die Nachricht, die Ihr Bot empfängt, wenn er einem Team hinzugefügt wird. Weitere Informationen finden Sie unter [Bot oder Benutzer, der einem Team hinzugefügt wurde](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition).

> [!NOTE]
> Der `serviceUrl` Wert ist in der Regel stabil, kann sich aber ändern. Wenn eine neue Nachricht eintrifft, muss Ihr Bot seinen gespeicherten `serviceUrl` Wert überprüfen.

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

Im folgenden Beispiel wird der `FetchChannelList` Aufruf der [Teams-Erweiterungen für das Bot Builder SDK für .NET verwendet](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams):

```csharp
ConversationList channels = client.GetTeamsConnectorClient().Teams.FetchChannelList(activity.GetChannelData<TeamsChannelData>().Team.Id);
```

#### <a name="nodejs-example"></a>Node.js Beispiel

Im folgenden Beispiel wird `fetchChannelList` ein Aufruf von den [Teams-Erweiterungen für das Bot Builder SDK für Node.js](https://www.npmjs.com/package/botbuilder-teams)verwendet:

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

## <a name="get-clientinfo-in-your-bot-context"></a>ClientInfo in Ihrem Botkontext abrufen

Sie können die clientInfo in der Aktivität Ihres Bots abrufen. ClientInfo enthält die folgenden Eigenschaften:

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

### <a name="c-example"></a>C#-Beispiel

```csharp
var connector = new ConnectorClient(new Uri(context.Activity.ServiceUrl));

{
    var clientinfo = context.Activity.Entities[0];
    await context.PostAsync($"ClientInfo: clientinfo ");
}
```

## <a name="see-also"></a>Siehe auch

[Bot Framework-Beispiele](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).
