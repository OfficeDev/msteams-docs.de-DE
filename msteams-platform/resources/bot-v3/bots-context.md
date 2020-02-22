---
title: Kontext für Ihren bot abrufen
description: Beschreibt, wie Kontext für Bots in Microsoft Teams abgerufen wird.
keywords: Teams-Bots-Kontext
ms.date: 05/20/2019
ms.openlocfilehash: 8f054661664850ffb843714230e209c8e4737f0a
ms.sourcegitcommit: 6c5c0574228310f844c81df0d57f11e2037e90c8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2020
ms.locfileid: "42228000"
---
# <a name="get-context-for-your-microsoft-teams-bot"></a>Kontext für Ihren Microsoft Teams-bot abrufen

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Ihr Bot kann auf zusätzlichen Kontext über das Team oder den Chat zugreifen, beispielsweise auf das Benutzerprofil. Diese Informationen können verwendet werden, um die Funktionalität Ihres bot zu bereichern und eine personalisierte Erfahrung zu bieten.

> [!NOTE]
> Diese Microsoft Teams&ndash;-spezifischen bot-APIs werden am besten über unsere Erweiterungen für das bot Builder SDK aufgerufen. Für C#-/.net laden Sie unser [Microsoft. bot. Connector. Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet-Paket herunter. Für die Entwicklung von Node. js wurde die BotBuilder für Microsoft Teams-Funktionen in das [bot Framework SDK](https://github.com/microsoft/botframework-sdk) ab v 4.6 integriert.

## <a name="fetching-the-team-roster"></a>Abrufen des Team Arbeitsplans

Ihr Bot kann eine Abfrage für die Liste der Teammitglieder und ihrer grundlegenden profile durchführen, einschließlich Microsoft Teams-Benutzer-IDs und Azure Active Directory Informationen (Azure AD) wie Name und ObjectID. Sie können diese Informationen verwenden, um Benutzeridentitäten zu korrelieren; um beispielsweise zu überprüfen, ob ein Benutzer, der bei einer Registerkarte über Azure AD Anmeldeinformationen angemeldet ist, ein Mitglied des Teams ist.

### <a name="rest-api-example"></a>Rest-API-Beispiel

Sie können eine get [`/conversations/{teamId}/members/`](/bot-framework/rest-api/bot-framework-rest-connector-api-reference#get-conversation-members)-Anforderung direkt unter Verwendung des Werts von `serviceUrl` als Endpunkt ausgeben.

Der `teamId` kann im `channeldata` Objekt der Aktivitäts Nutzlast gefunden werden, die ihr bot in den folgenden Szenarien erhält:
* Wenn ein Benutzer mit dem bot in einem Teamkontext Nachrichten oder interagiert (siehe [empfangen von Nachrichten](~/resources/bot-v3/bot-conversations/bots-conversations.md#receiving-messages))
* Wenn einem Team ein neuer Benutzer oder bot hinzugefügt wird (siehe [bot oder Benutzer, der einem Team hinzugefügt](~/resources/bot-v3/bots-notifications.md#bot-or-user-added-to-a-team)wurde)

> [!NOTE]
>* Stellen Sie sicher, dass Sie die Team-ID verwenden, wenn Sie die API aufrufen
>* Der Wert von `serviceUrl` neigt dazu, stabil zu sein, aber kann sich ändern. Wenn eine neue Nachricht eintrifft, sollte Ihr bot den gespeicherten Wert von `serviceUrl`überprüfen.

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

Aufrufen `GetConversationMembersAsync` mit `Team.Id` , um eine Liste von Benutzer-IDs zurückzugeben.

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

### <a name="nodejstypescript-example"></a>Beispiel für Node. js/Transcript

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

*Siehe auch* [bot Framework-Beispiele](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).

## <a name="fetching-user-profile-or-roster-in-personal-or-group-chat"></a>Abrufen von Benutzerprofilen oder Dienstplänen im persönlichen oder Gruppenchat

Sie können auch denselben API-Aufruf für einen persönlichen Chat durchführen, um die Profilinformationen des Benutzers zu erhalten, der mit Ihrem bot chattet.

Die API-Aufruf-und SDK-Methoden sind identisch mit dem Abrufen des Team Arbeitsplans, ebenso wie das Response-Objekt. Der einzige Unterschied besteht darin, `conversationId` dass Sie den `teamId`anstelle von übergeben.

## <a name="fetching-the-list-of-channels-in-a-team"></a>Abrufen der Liste der Kanäle in einem Team

Ihr Bot kann die Liste der Kanäle in einem Teamabfragen.

> [!NOTE]
>
>* Der Name des standardmäßigen allgemeinen Kanals wird `null` zurückgegeben, um die Lokalisierung zu ermöglichen.
>* Die Kanal-ID für den allgemeinen Kanal stimmt immer mit der Team-ID überein.

### <a name="rest-api-example"></a>Rest-API-Beispiel

Sie können eine get `/teams/{teamId}/conversations/`-Anforderung direkt unter Verwendung des Werts von `serviceUrl` als Endpunkt ausgeben.

Die einzige Quelle für `teamId` ist eine Nachricht aus dem Teamkontext-entweder eine Nachricht von einem Benutzer oder die Nachricht, die ihr bot erhält, wenn er einem Team hinzugefügt wird (siehe [bot oder Benutzer, der einem Team hinzugefügt](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition)wurde).

> [!NOTE]
> Der Wert von `serviceUrl` neigt dazu, stabil zu sein, aber kann sich ändern. Wenn eine neue Nachricht eintrifft, sollte Ihr bot den gespeicherten Wert von `serviceUrl`überprüfen.

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

Im folgenden Beispiel wird der `FetchChannelList` Aufruf von den [Microsoft Teams-Erweiterungen für das bot Builder SDK für .net](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams)verwendet:

```csharp
ConversationList channels = client.GetTeamsConnectorClient().Teams.FetchChannelList(activity.GetChannelData<TeamsChannelData>().Team.Id);
```

#### <a name="nodejs-example"></a>Node. js-Beispiel

Im folgenden Beispiel wird `fetchChannelList` der Aufruf von [Microsoft Teams-Erweiterungen für das bot Builder SDK für Node. js](https://www.npmjs.com/package/botbuilder-teams)verwendet.

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
