---
title: Behandeln von bot-Ereignissen
description: Beschreibt das Behandeln von Ereignissen in Bots für Microsoft Teams
keywords: Teams-Bots-Ereignisse
ms.date: 05/20/2019
author: laujan
ms.openlocfilehash: 5ef37a931d421f245cca4fbb984b69217f779785
ms.sourcegitcommit: 3fc7ad33e2693f07170c3cb1a0d396261fc5c619
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "48796176"
---
# <a name="handle-bot-events-in-microsoft-teams"></a>Behandeln von bot-Ereignissen in Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Microsoft Teams sendet Benachrichtigungen an Ihren bot für Änderungen oder Ereignisse, die in Bereichen auftreten, in denen Ihr bot aktiv ist. Sie können diese Ereignisse verwenden, um Dienstlogik auszulösen, beispielsweise die folgenden:

* Auslösen einer Willkommensnachricht, wenn Ihr bot einem Team hinzugefügt wird
* Abfrage-und Cache Gruppeninformationen, wenn der bot einem Gruppenchat hinzugefügt wird
* Aktualisieren zwischengespeicherter Informationen zu Teammitgliedschaften oder Kanalinformationen
* Entfernen zwischengespeicherter Informationen für ein Team, wenn der bot entfernt wird
* Wenn eine bot-Nachricht von einem Benutzer gefällt wird

Jedes bot-Ereignis wird als `Activity` Objekt gesendet, in dem `messageType` definiert wird, welche Informationen das Objekt enthält. `message`Informationen zum [senden und empfangen](~/resources/bot-v3/bot-conversations/bots-conversations.md)von Nachrichten vom Typ.

Teams und Gruppen Ereignisse, die in der Regel vom `conversationUpdate` Typ ausgelöst werden, haben zusätzliche Teams-Ereignisinformationen, die als Teil des `channelData` Objekts übergeben werden, und daher muss Ihr Ereignishandler die `channelData` Nutzlast für die Teams `eventType` und zusätzliche ereignisspezifische Metadaten Abfragen.

In der folgenden Tabelle sind die Ereignisse aufgeführt, die ihr bot empfangen kann, und Aktionen für ausführen.

|Typ|Payload-Objekt|Teams-Ereignistyp |Beschreibung|Bereich|
|---|---|---|---|---|
| `conversationUpdate` |`membersAdded`| `teamMemberAdded`|[Mitglied zum Team hinzugefügt](#team-member-or-bot-addition)| Alle |
| `conversationUpdate` |`membersRemoved`| `teamMemberRemoved`|[Das Mitglied wurde aus dem Team entfernt.](#team-member-or-bot-removed)| `groupChat` & `team` |
| `conversationUpdate` | |`teamRenamed`| [Team wurde umbenannt](#team-name-updates)| `team` |
| `conversationUpdate` | |`channelCreated`| [Es wurde ein Kanal erstellt.](#channel-updates)|`team` |
| `conversationUpdate` | |`channelRenamed`| [Ein Kanal wurde umbenannt](#channel-updates)|`team` |
| `conversationUpdate` | |`channelDeleted`| [Ein Kanal wurde gelöscht.](#channel-updates)|`team` |
| `messageReaction` |`reactionsAdded`|| [Reaktion auf bot-Nachricht](#reactions)| Alle |
| `messageReaction` |`reactionsRemoved`|| [Reaktion aus bot-Nachricht entfernt](#reactions)| Alle |

## <a name="team-member-or-bot-addition"></a>Team Mitglied oder bot-Addition

Das [`conversationUpdate`](/azure/bot-service/dotnet/bot-builder-dotnet-activities?view=azure-bot-service-3.0#conversationupdate) Ereignis wird an Ihren bot gesendet, wenn es Informationen über Mitgliedschafts Aktualisierungen für Teams erhält, in denen es hinzugefügt wurde. Er empfängt außerdem eine Aktualisierung, wenn er zum ersten Mal hinzugefügt wurde, speziell für persönliche Unterhaltungen. Beachten Sie, dass die Benutzerinformationen ( `Id` ) für Ihren bot eindeutig sind und für die zukünftige Verwendung durch ihren Dienst zwischengespeichert werden können (beispielsweise das Senden einer Nachricht an einen bestimmten Benutzer).

### <a name="bot-or-user-added-to-a-team"></a>Bot oder Benutzer, der einem Team hinzugefügt wurde

Das `conversationUpdate` Ereignis mit dem `membersAdded` Objekt in der Nutzlast wird gesendet, wenn entweder ein bot einem Team hinzugefügt wird oder ein neuer Benutzer einem Team hinzugefügt wird, in dem ein bot hinzugefügt wurde. Microsoft Teams fügt `eventType.teamMemberAdded` das Objekt ebenfalls hinzu `channelData` .

Da dieses Ereignis in beiden Fällen gesendet wird, sollten Sie das Objekt analysieren, `membersAdded` um festzustellen, ob es sich bei dem Zusatz um einen Benutzer oder den bot selbst handelt. Für letztere empfiehlt es sich, eine [Willkommensnachricht](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#best-practice-welcome-messages-in-teams) an den Kanal zu senden, damit Benutzer die von Ihrem bot bereitgestellten Funktionen verstehen können.

#### <a name="example-code-checking-whether-bot-was-the-added-member"></a>Beispielcode: überprüfen, ob bot das hinzugefügte Mitglied war

##### <a name="net"></a>.NET

```csharp
    for (int i = 0; i < sourceMessage.MembersAdded.Count; i++)
    {
        if (sourceMessage.MembersAdded[i].Id == sourceMessage.Recipient.Id)
        {
            addedBot = true;
            break;
        }
    }
```

##### <a name="nodejs"></a>Node.js

```javascript
const builder = require('botbuilder');

var c = new builder.ChatConnector({appId: BOT_APP_ID, appPassword: .BOT_SECRET});
var bot = new builder.UniversalBot(c);

bot.on('conversationUpdate', (msg) => {
    var members = msg.membersAdded;
    // Loop through all members that were just added to the team
    for (var i = 0; i < members.length; i++) {

        // See if the member added was our bot
        if (members[i].id.includes(BOT_APP_ID)) {
            var botmessage = new builder.Message()
                .address(msg.address)
                .text('Hello World!');

            bot.send(botmessage, function(err) {});
        }
    }
});
```

#### <a name="schema-example-bot-added-to-team"></a>Schema Beispiel: bot zum Team hinzugefügt

```json
{
    "membersAdded": [
        {
            "id": "28:f5d48856-5b42-41a0-8c3a-c5f944b679b0"
        }
    ],
    "type": "conversationUpdate",
    "timestamp": "2017-02-23T19:38:35.312Z",
    "localTimestamp": "2017-02-23T12:38:35.312-07:00",
    "id": "f:5f85c2ad",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
    "from": {
        "id": "29:1I9Is_Sx0OIy2rQ7Xz1lcaPKlO9eqmBRTBuW6XzkFtcjqxTjPaCMij8BVMdBcL9L_RwWNJyAHFQb0TRzXgyQvA"
    },
    "conversation": {
        "isGroup": true,
        "conversationType": "channel",
        "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
    },
    "recipient": {
        "id": "28:f5d48856-5b42-41a0-8c3a-c5f944b679b0",
        "name": "SongsuggesterBot"
    },
    "channelData": {
        "team": {
            "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
        },
        "eventType": "teamMemberAdded",
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    }
}
```

### <a name="bot-added-for-personal-context-only"></a>Bot nur für persönlichen Kontext hinzugefügt

Ihr bot erhält ein `conversationUpdate` mit `membersAdded` , wenn ein Benutzer es direkt für persönlichen Chat hinzufügt. In diesem Fall enthält die von Ihrem bot empfangene Nutzlast das `channelData.team` Objekt nicht. Sie sollten dies als Filter verwenden, falls Ihr bot je nach Bereich eine andere [Willkommensnachricht](~/resources/bot-v3/bot-conversations/bots-conv-personal.md#best-practice-welcome-messages-in-personal-conversations) anbieten soll.

> [!NOTE]
> Für Bots mit persönlicher Reichweite empfängt Ihr bot das `conversationUpdate` Ereignis nur ein einziges Mal, auch wenn der bot entfernt und erneut hinzugefügt wird. Für die Entwicklung und das Testen kann es hilfreich sein, eine Hilfsfunktion hinzuzufügen, mit der Sie Ihren bot vollständig zurücksetzen können. Weitere Informationen zur Implementierung dieses Beispiels finden Sie unter [Node.js Beispiel](https://github.com/OfficeDev/microsoft-teams-sample-complete-node/blob/master/src/middleware/SimulateResetBotChat.ts) oder [C#-Beispiel](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp/blob/master/template-bot-master-csharp/src/controllers/MessagesController.cs#L238) .

#### <a name="schema-example-bot-added-to-personal-context"></a>Schema Beispiel: bot zum persönlichen Kontext hinzugefügt

```json
{
  "membersAdded": [{
      "id": "28:f5d48856-5b42-41a0-8c3a-c5f944b679b0"
    },
    {
      "id": "29:<userID>",
      "aadObjectId": "***"
    }
  ],
  "type": "conversationUpdate",
  "timestamp": "2019-04-23T10:17:44.349Z",
  "id": "f:5f85c2ad",
  "channelId": "msteams",
  "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
  "from": {
    "id": "29:<USERID>",
    "aadObjectId": "**_"
  },
  "conversation": {
    "conversationType": "personal",
    "id": "_*_"
  },
  "recipient": {
    "id": "28:<BOT ID>",
    "name": "<BOT NAME>"
  },
  "channelData": {
    "tenant": {
      "id": "<TENANT ID>"
    }
  }
}
```

## <a name="team-member-or-bot-removed"></a>Team Mitglied oder bot entfernt

Das `conversationUpdate` Ereignis mit dem `membersRemoved` Objekt in der Nutzlast wird gesendet, wenn entweder Ihr bot aus einem Team entfernt wird oder ein Benutzer aus einem Team entfernt wird, in dem ein bot hinzugefügt wurde. Microsoft Teams fügt `eventType.teamMemberRemoved` das Objekt ebenfalls hinzu `channelData` . Wie beim `membersAdded` Objekt sollten Sie das `membersRemoved` Objekt für die APP-ID Ihres bot analysieren, um festzustellen, wer entfernt wurde.

### <a name="schema-example-team-member-removed"></a>Schema Beispiel: entferntes Team Mitglied

```json
{
    "membersRemoved": [
        {
            "id": "29:1_LCi5Up14pAy65yZuaJzG1uIT7ujYhjjSTsUNqjORsZHjLHKiQIBJa4cX2XsAsRoaY7va2w6ZymA9-1VtSY_g"
        }
    ],
    "type": "conversationUpdate",
    "timestamp": "2017-02-23T19:37:06.96Z",
    "localTimestamp": "2017-02-23T12:37:06.96-07:00",
    "id": "f:d8a6a4aa",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
    "from": {
        "id": "29:1I9Is_Sx0OIy2rQ7Xz1lcaPKlO9eqmBRTBuW6XzkFtcjqxTjPaCMij8BVMdBcL9L_RwWNJyAHFQb0TRzXgyQvA"
    },
    "conversation": {
        "isGroup": true,
        "conversationType": "channel",
        "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
    },
    "recipient":
    {
        "id": "28:f5d48856-5b42-41a0-8c3a-c5f944b679b0",
        "name": "SongsuggesterBot"
    },
    "channelData": {
        "team": {
            "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
        },
        "eventType": "teamMemberRemoved",
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    }
}
```

## <a name="team-name-updates"></a>Team namens Updates

> [!NOTE]
> Es gibt keine Funktionen zum Abfragen aller Team Namen, und der Teamname wird nicht in Nutzdaten von anderen Ereignissen zurückgegeben.

Ihr bot wird benachrichtigt, wenn das Team, in dem es sich befindet, umbenannt wurde. Es empfängt ein `conversationUpdate` Ereignis mit `eventType.teamRenamed` im `channelData` -Objekt. Beachten Sie, dass es keine Benachrichtigungen zum Erstellen oder Löschen von Teams gibt, da Bots nur als Teil von Teams vorhanden sind und keine Sichtbarkeit außerhalb des Bereichs haben, in dem Sie hinzugefügt wurden.

### <a name="schema-example-team-renamed"></a>Schema Beispiel: Team umbenannt

```json
{ 
    "type": "conversationUpdate",
    "timestamp": "2017-02-23T19:35:56.825Z",
    "localTimestamp": "2017-02-23T12:35:56.825-07:00",
    "id": "f:1406033e",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/", 
    "from": { 
        "id": "29:1I9Is_Sx0O-Iy2rQ7Xz1lcaPKlO9eqmBRTBuW6XzkFtcjqxTjPaCMij8BVMdBcL9L_RwWNJyAHFQb0TRzXgyQvA"
    }, 
    "conversation": {
        "isGroup": true,
        "conversationType": "channel",
        "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
    },
    "recipient": { 
        "id": "28:f5d48856-5b42-41a0-8c3a-c5f944b679b0",
        "name": "SongsuggesterLocal"
    },
    "channelData": {
        "team": {
            "id": "19:efa9296d959346209fea44151c742e73@thread.skype",
            "name": "New Team Name"
        },
        "eventType": "teamRenamed",
        "tenant": { 
           "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    }
}
```

## <a name="channel-updates"></a>Kanal Aktualisierungen

Ihr bot wird benachrichtigt, wenn ein Kanal in einem Team erstellt, umbenannt oder gelöscht wurde, in dem er hinzugefügt wurde. Erneut wird das `conversationUpdate` Ereignis empfangen, und eine Teams-spezifische Ereignis-ID wird als Teil des Objekts gesendet `channelData.eventType` , wobei die Kanaldaten  `channel.id` die GUID für den Kanal ist und `channel.name` den Kanalnamen selbst enthält.

Die Kanal Ereignisse lauten wie folgt:

_ **channelCreated** &emsp; ein Benutzer fügt dem Team einen neuen Kanal hinzu
* **channelRenamed** &emsp; Ein Benutzer benennt einen vorhandenen Kanal um
* **channelDeleted** &emsp; Ein Benutzer entfernt einen Kanal

### <a name="full-schema-example-channelcreated"></a>Vollständiges Schemabeispiel: channelCreated

```json
{
    "type": "conversationUpdate",
    "timestamp": "2017-02-23T19:34:07.478Z",
    "localTimestamp": "2017-02-23T12:34:07.478-07:00",
    "id": "f:dd6ec311",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
    "from": {
        "id": "29:1wR7IdIRIoerMIWbewMi75JA3scaMuxvFon9eRQW2Nix5loMDo0362st2IaRVRirPZBv1WdXT8TIFWWmlQCizZQ"
    },
    "conversation": {
        "isGroup": true,
        "conversationType": "channel",
        "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
    },
    "recipient": {
        "id": "28:f5d48856-5b42-41a0-8c3a-c5f944b679b0",
        "name": "SongsuggesterBot"
    },
    "channelData": {
        "channel": {
            "id": "19:6d97d816470f481dbcda38244b98689a@thread.skype",
            "name": "FunDiscussions"
        },
        "team": {
            "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
        },
        "eventType": "channelCreated",
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    }
}
```

### <a name="schema-excerpt-channeldata-for-channelrenamed"></a>Schema Auszug: channelData für channelRenamed

```json
⋮
"channelData": {
    "channel": {
        "id": "19:6d97d816470f481dbcda38244b98689a@thread.skype",
        "name": "PhotographyUpdates"
    },
    "team": {
        "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
    },
    "eventType": "channelRenamed",
    "tenant": {
        "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
    }
}
⋮
```

### <a name="schema-excerpt-channeldata-for-channeldeleted"></a>Schema Auszug: channelData für channelDeleted

```json
⋮
"channelData": {
    "channel": {
        "id": "19:6d97d816470f481dbcda38244b98689a@thread.skype",
        "name": "PhotographyUpdates"
    },
    "team": {
        "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
    },
    "eventType": "channelDeleted",
    "tenant": {
        "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
    }
}
⋮
```

## <a name="reactions"></a>Reaktionen

Das `messageReaction` Ereignis wird gesendet, wenn ein Benutzer seine Reaktion auf eine Nachricht hinzufügt oder entfernt, die ursprünglich von Ihrem bot gesendet wurde. `replyToId` enthält die ID der jeweiligen Nachricht.

### <a name="schema-example-a-user-likes-a-message"></a>Schema Beispiel: ein Benutzer mag eine Nachricht

```json
{
    "reactionsAdded": [
        {
            "type": "like"
        }
    ],
    "type": "messageReaction",
    "timestamp": "2017-10-16T18:45:41.943Z",
    "id": "f:9f78d1f3",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
    "from": {
        "id": "29:1I9Is_Sx0O-Iy2rQ7Xz1lcaPKlO9eqmBRTBuW6XzkFtcjqxTjPaCMij8BVMdBcL9L_RwWNJyAHFQb0TRzXgyQvA",
        "aadObjectId": "c33aafc4-646d-4543-9d4c-abd28e4d2110"
    },
    "conversation": {
        "isGroup": true,
        "conversationType": "channel",
        "id": "19:3629591d4b774aa08cb0887902eee7c1@thread.skype"
    },
    "recipient": {
        "id": "28:f5d48856-5b42-41a0-8c3a-c5f944b679b0",
        "name": "SongsuggesterLocal"
    },
    "channelData": {
        "channel": {
            "id": "19:3629591d4b774aa08cb0887902eee7c1@thread.skype"
        },
        "team": {
            "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
        },
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    },
    "replyToId": "1575667808184"
}
```

### <a name="schema-example-a-user-un-likes-a-message"></a>Schema Beispiel: ein Benutzer Unlike a Message

```json
{
    "reactionsRemoved": [
        {
            "type": "like"
        }
    ],
    "type": "messageReaction",
    "timestamp": "2017-10-16T18:45:41.943Z",
    "id": "f:9f78d1f3",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
    "from": {
        "id": "29:1I9Is_Sx0O-Iy2rQ7Xz1lcaPKlO9eqmBRTBuW6XzkFtcjqxTjPaCMij8BVMdBcL9L_RwWNJyAHFQb0TRzXgyQvA",
        "aadObjectId": "c33aafc4-646d-4543-9d4c-abd28e4d2110"
    },
    "conversation": {
        "isGroup": true,
        "conversationType": "channel",
        "id": "19:3629591d4b774aa08cb0887902eee7c1@thread.skype"
    },
    "recipient": {
        "id": "28:f5d48856-5b42-41a0-8c3a-c5f944b679b0",
        "name": "SongsuggesterLocal"
    },
    "channelData": {
        "channel": {
            "id": "19:3629591d4b774aa08cb0887902eee7c1@thread.skype"
        },
        "team": {
            "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
        },
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    },
    "replyToId": "1575667808184"
}
```
