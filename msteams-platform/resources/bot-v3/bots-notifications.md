---
title: Behandeln von Botereignissen
description: Beschreibt, wie Ereignisse in Bots für Microsoft Teams behandelt werden
keywords: Teams-Bots-Ereignisse
ms.date: 05/20/2019
ms.topic: how-to
localization_priority: Normal
ms.author: lajanuar
author: surbhigupta
ms.openlocfilehash: 6a9eaab388927fcff51d7883e1a61ca1cec81fac
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069076"
---
# <a name="handle-bot-events-in-microsoft-teams"></a>Behandeln von Botereignissen in Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Microsoft Teams sendet Benachrichtigungen an Ihren Bot für Änderungen oder Ereignisse, die in Bereichen auftreten, in denen Ihr Bot aktiv ist. Sie können diese Ereignisse verwenden, um Dienstlogik auszulösen, z. B.:

* Lösen Sie eine Willkommensnachricht aus, wenn Ihr Bot zu einem Team hinzugefügt wird.
* Abfragen und Zwischenspeichern von Gruppeninformationen, wenn der Bot einem Gruppenchat hinzugefügt wird.
* Aktualisieren sie zwischengespeicherte Informationen zur Teammitgliedschaft oder Kanalinformationen.
* Entfernt zwischengespeicherte Informationen für ein Team, wenn der Bot entfernt wird.
* Wenn eine Bot-Nachricht von einem Benutzer gefällt.

Jedes Bot-Ereignis wird als `Activity` Objekt gesendet, in dem `messageType` definiert wird, welche Informationen im Objekt enthalten sind. Nachrichten vom Typ finden Sie unter Senden und Empfangen von `message` [Nachrichten.](~/resources/bot-v3/bot-conversations/bots-conversations.md)

Teams- und Gruppenereignisse, die in der Regel vom Typ ausgelöst werden, verfügen über `conversationUpdate` zusätzliche Teams Ereignisinformationen, die als Teil des Objekts übergeben `channelData` werden. Daher muss der Ereignishandler die `channelData` Nutzlast nach der Teams und `eventType` zusätzlichen ereignisspezifischen Metadaten abfragen.

In der folgenden Tabelle sind die Ereignisse aufgeführt, die Ihr Bot empfangen und entsprechende Maßnahmen ergreifen kann.

|Typ|Payload-Objekt|Teams eventType |Beschreibung|Bereich|
|---|---|---|---|---|
| `conversationUpdate` |`membersAdded`| `teamMemberAdded`|[Mitglied zum Team hinzugefügt](#team-member-or-bot-addition)| Alle |
| `conversationUpdate` |`membersRemoved`| `teamMemberRemoved`|[Mitglied wurde aus Team entfernt](#team-member-or-bot-removed)| `groupChat` & `team` |
| `conversationUpdate` | |`teamRenamed`| [Team wurde umbenannt](#team-name-updates)| `team` |
| `conversationUpdate` | |`channelCreated`| [Ein Kanal wurde erstellt](#channel-updates)|`team` |
| `conversationUpdate` | |`channelRenamed`| [Ein Kanal wurde umbenannt](#channel-updates)|`team` |
| `conversationUpdate` | |`channelDeleted`| [Ein Kanal wurde gelöscht.](#channel-updates)|`team` |
| `messageReaction` |`reactionsAdded`|| [Reaktion auf Bot-Nachricht](#reactions)| Alle |
| `messageReaction` |`reactionsRemoved`|| [Reaktion aus Botnachricht entfernt](#reactions)| Alle |

## <a name="team-member-or-bot-addition"></a>Hinzufügen eines Teammitglieds oder Bots

Das [`conversationUpdate`](/azure/bot-service/dotnet/bot-builder-dotnet-activities?view=azure-bot-service-3.0#conversationupdate&preserve-view=true) Ereignis wird an Ihren Bot gesendet, wenn er Informationen zu Mitgliedschaftsupdates für Teams empfängt, in denen es hinzugefügt wurde. Er empfängt außerdem eine Aktualisierung, wenn er zum ersten Mal hinzugefügt wurde, speziell für persönliche Unterhaltungen. Beachten Sie, dass die Benutzerinformationen ( `Id` ) für Ihren Bot eindeutig sind und für die zukünftige Verwendung durch Ihren Dienst zwischengespeichert werden können, z. B. das Senden einer Nachricht an einen bestimmten Benutzer.

### <a name="bot-or-user-added-to-a-team"></a>Bot oder Benutzer, der einem Team hinzugefügt wurde

Das `conversationUpdate` Ereignis mit dem Objekt in der Nutzlast wird `membersAdded` gesendet, wenn einem Team entweder ein Bot oder ein neuer Benutzer zu einem Team hinzugefügt wird, in dem ein Bot hinzugefügt wurde. Microsoft Teams fügt `eventType.teamMemberAdded` auch das Objekt `channelData` hinzu.

Da dieses Ereignis in beiden Fällen gesendet wird, sollten Sie das `membersAdded` Objekt analysieren, um zu bestimmen, ob der Zusatz ein Benutzer oder der Bot selbst war. Für Letzteres empfiehlt es sich, eine [Willkommensnachricht](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#best-practice-welcome-messages-in-teams) an den Kanal zu senden, damit Benutzer die Features verstehen können, die Ihr Bot bereitstellt.

#### <a name="example-code-checking-whether-bot-was-the-added-member"></a>Beispielcode: Überprüfen, ob bot das hinzugefügte Mitglied war

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

#### <a name="schema-example-bot-added-to-team"></a>Schemabeispiel: Bot zum Team hinzugefügt

```json
{
   "membersAdded":[
      {
         "id":"28:f5d48856-5b42-41a0-8c3a-c5f944b679b0"
      }
   ],
   "type":"conversationUpdate",
   "timestamp":"2017-02-23T19:38:35.312Z",
   "localTimestamp":"2017-02-23T12:38:35.312-07:00",
   "id":"f:5f85c2ad",
   "channelId":"msteams",
   "serviceUrl":"https://smba.trafficmanager.net/amer-client-ss.msg/",
   "from":{
      "id":"29:1I9Is_Sx0OIy2rQ7Xz1lcaPKlO9eqmBRTBuW6XzkFtcjqxTjPaCMij8BVMdBcL9L_RwWNJyAHFQb0TRzXgyQvA"
   },
   "conversation":{
      "isGroup":true,
      "conversationType":"channel",
      "id":"19:efa9296d959346209fea44151c742e73@thread.skype"
   },
   "recipient":{
      "id":"28:f5d48856-5b42-41a0-8c3a-c5f944b679b0",
      "name":"SongsuggesterBot"
   },
   "channelData":{
      "team":{
         "id":"19:efa9296d959346209fea44151c742e73@thread.skype"
      },
      "eventType":"teamMemberAdded",
      "tenant":{
         "id":"72f988bf-86f1-41af-91ab-2d7cd011db47"
      }
   }
}
```

### <a name="user-added-to-a-meeting"></a>Zu einer Besprechung hinzugefügter Benutzer

Das `conversationUpdate` Ereignis mit dem Objekt in der Nutzlast wird `membersAdded` gesendet, wenn ein Benutzer zu einer privaten geplanten Besprechung hinzugefügt wird. Die Ereignisdetails werden auch gesendet, wenn anonyme Benutzer an der Besprechung teilnehmen. 

> [!NOTE]
>
>* Wenn ein anonymer Benutzer zu einer Besprechung hinzugefügt wird, verfügt das MembersAdded-Nutzlastobjekt nicht über `aadObjectId` ein Feld.
>* Wenn ein anonymer Benutzer zu einer Besprechung hinzugefügt wird, `from` hat das Objekt in der Nutzlast immer die ID des Besprechungsorganisators, auch wenn der anonyme Benutzer von einem anderen Referenten hinzugefügt wurde.

#### <a name="schema-example-user-added-to-meeting"></a>Schemabeispiel: Benutzer zur Besprechung hinzugefügt

```json
{
   "membersAdded":[
      {
         "id":"229:1Z_XHWBMhDuehhDBYoPQD6Y1DSFsTtqOZx-SA5Jh9Y4zHKm4VbFGRn7-rK7SWiW1JECwxkMdrWpHoBut2sSyQPA"
      }
   ],
   "type":"conversationUpdate",
   "timestamp":"2017-02-23T19:38:35.312Z",
   "localTimestamp":"2020-09-29T21:11:38.6542339Z",
   "id":"f:a8cd1b51-9ddb-bd35-624b-7f7474165df8",
   "channelId":"msteams",
   "serviceUrl":"https://canary.botapi.skype.com/amer/",
   "from":{
      "id":"29:1siKxZhSoTapsXvI0gyf7Gywm_HM-4kEQW4BJnWuFYVIVu87xCNP99nidgQRCcwD3L3p_schiMShzx8IDRzf8mw",
      "aadObjectId":"f30ba569-abef-4e97-8762-35f85cbae706"
   },
   "conversation":{
      "isGroup":true,
      "tenantId":"e15762ef-a8d8-416b-871c-25516354f1fe",
      "id":"19:meeting_MWJlNGViOTgtMGExYi00NDA3LWExODgtOTZhMWNlYjM4ZTRj@thread.v2"
   },
   "recipient":{
      "id":"28:3af3604a-d4fc-486b-911e-86fab41aa91c",
      "name":"EchoBot1_Rename"
   },
   "channelData":{
      "tenant":{
         "id":"e15762ef-a8d8-416b-871c-25516354f1fe"
      },
      "source":null,
      "meeting":{
         "id":"MCMxOTptZWV0aW5nX01XSmxOR1ZpT1RndE1HRXhZaTAwTkRBM0xXRXhPRGd0T1RaaE1XTmxZak00WlRSakB0aHJlYWQudjIjMA=="
      }
   }
}

```

### <a name="bot-added-for-personal-context-only"></a>Bot nur für persönlichen Kontext hinzugefügt

Ihr Bot erhält ein `conversationUpdate` `membersAdded` With, wenn ein Benutzer ihn direkt für den persönlichen Chat hinzufügt. In diesem Fall enthält die Nutzlast, die Ihr Bot empfängt, das `channelData.team` Objekt nicht. Sie sollten dies als Filter verwenden, falls Ihr Bot je nach Umfang eine andere [Willkommensnachricht](~/resources/bot-v3/bot-conversations/bots-conv-personal.md#best-practice-welcome-messages-in-personal-conversations) anbieten soll.

> [!NOTE]
> Bei bots mit persönlichem Bereich empfängt Ihr Bot das `conversationUpdate` Ereignis mehrmals, auch wenn der Bot entfernt und erneut hinzugefügt wird. Für Entwicklung und Tests kann es hilfreich sein, eine Hilfsfunktion hinzuzufügen, mit der Sie Ihren Bot vollständig zurücksetzen können. Weitere Informationen zur Implementierung finden Sie in einem [Node.js Beispiel](https://github.com/OfficeDev/microsoft-teams-sample-complete-node/blob/master/src/middleware/SimulateResetBotChat.ts) oder [C#-Beispiel.](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp/blob/master/template-bot-master-csharp/src/controllers/MessagesController.cs#L238)

#### <a name="schema-example-bot-added-to-personal-context"></a>Schemabeispiel: Bot zum persönlichen Kontext hinzugefügt

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
    "aadObjectId": "***"
  },
  "conversation": {
    "conversationType": "personal",
    "id": "***"
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

## <a name="team-member-or-bot-removed"></a>Teammitglied oder Bot entfernt

Das `conversationUpdate` Ereignis mit dem Objekt in der Nutzlast wird `membersRemoved` gesendet, wenn entweder Ihr Bot aus einem Team oder ein Benutzer aus einem Team entfernt wird, in dem ein Bot hinzugefügt wurde. Microsoft Teams fügt `eventType.teamMemberRemoved` auch das Objekt `channelData` hinzu. Wie beim `membersAdded` Objekt sollten Sie das Objekt für die `membersRemoved` App-ID Ihres Bots analysieren, um zu bestimmen, wer entfernt wurde.

### <a name="schema-example-team-member-removed"></a>Schemabeispiel: Teammitglied entfernt

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

### <a name="user-removed-from-a-meeting"></a>Benutzer aus einer Besprechung entfernt

Das `conversationUpdate` Ereignis mit dem Objekt in der Nutzlast wird `membersRemoved` gesendet, wenn ein Benutzer aus einer privaten geplanten Besprechung entfernt wird. Die Ereignisdetails werden auch gesendet, wenn anonyme Benutzer an der Besprechung teilnehmen. 

> [!NOTE]
>
>* Wenn ein anonymer Benutzer aus einer Besprechung entfernt wird, hat das membersRemoved-Nutzlastobjekt kein `aadObjectId` Feld.
>* Wenn ein anonymer Benutzer aus einer Besprechung entfernt wird, `from` hat das Objekt in der Nutzlast immer die ID des Besprechungsorganisators, auch wenn der anonyme Benutzer von einem anderen Referenten entfernt wurde.

#### <a name="schema-example-user-removed-from-meeting"></a>Schemabeispiel: Benutzer aus Besprechung entfernt

```
{   
      "membersRemoved": 
        {  
          "id": "29:1Z_XHWBMhDuehhDBYoPQD6Y1DSFsTtqOZx-SA5Jh9Y4zHKm4VbFGRn7-rK7SWiW1JECwxkMdrWpHoBut2sSyQPA"   
        }   
      ],   
      "type": "conversationUpdate",   
      "timestamp": "2020-09-29T21:15:08.6391139Z",   
      "id": "f:ee8dfdf3-54ac-51de-05da-9d49514974bb",   
      "channelId": "msteams",   
      "serviceUrl": "https://canary.botapi.skype.com/amer/",   
      "from": {   
        "id": "29:1siKxZhSoTapsXvI0gyf7Gywm_HM-4kEQW4BJnWuFYVIVu87xCNP99nidgQRCcwD3L3p_schiMShzx8IDRzf8mw",   
        "aadObjectId": "f30ba569-abef-4e97-8762-35f85cbae706"   
      },   
      "conversation": {    
        "isGroup": true,   
        "tenantId": "e15762ef-a8d8-416b-871c-25516354f1fe",   
        "id": "19:meeting_MWJlNGViOTgtMGExYi00NDA3LWExODgtOTZhMWNlYjM4ZTRj@thread.v2"   
      },   
      "recipient": {   
        "id": "28:3af3604a-d4fc-486b-911e-86fab41aa91c",   
        "name": "EchoBot1_Rename"   
      },   
      "channelData": {   
        "tenant": {   
          "id": "e15762ef-a8d8-416b-871c-25516354f1fe"   
        },   
        "source": null,   
        "meeting": {   
          "id": "MCMxOTptZWV0aW5nX01XSmxOR1ZpT1RndE1HRXhZaTAwTkRBM0xXRXhPRGd0T1RaaE1XTmxZak00WlRSakB0aHJlYWQudjIjMA=="   
        }   
      }   
}
```

## <a name="team-name-updates"></a>Aktualisierungen von Teamnamen

> [!NOTE]
> Es gibt keine Funktion zum Abfragen aller Teamnamen, und teamname wird nicht in Nutzlasten von anderen Ereignissen zurückgegeben.

Ihr Bot wird benachrichtigt, wenn das Team, in dem er sich befindet, umbenannt wurde. Es empfängt ein `conversationUpdate` Ereignis mit `eventType.teamRenamed` im `channelData` Objekt. Bitte beachten Sie, dass es keine Benachrichtigungen für die Erstellung oder Löschung von Teams gibt, da Bots nur als Teil von Teams vorhanden sind und keine Sichtbarkeit außerhalb des Bereichs haben, in dem sie hinzugefügt wurden.

### <a name="schema-example-team-renamed"></a>Schemabeispiel: Team umbenannt

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

## <a name="channel-updates"></a>Kanalupdates

Ihr Bot wird benachrichtigt, wenn ein Kanal in einem Team erstellt, umbenannt oder gelöscht wird, in dem er hinzugefügt wurde. Auch hier wird das `conversationUpdate` Ereignis empfangen, und ein Teams-spezifischer Ereignisbezeichner wird als Teil des `channelData.eventType` Objekts gesendet, wobei die Kanaldaten `channel.id` die GUID für den Kanal sind und den `channel.name` Kanalnamen selbst enthält.

Die Kanalereignisse sind wie folgt:

* **channelCreated** &emsp; Ein Benutzer fügt dem Team einen neuen Kanal hinzu.
* **channelRenamed** &emsp; Ein Benutzer benennt einen vorhandenen Kanal um.
* **channelDeleted** &emsp; Ein Benutzer entfernt einen Kanal.

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

### <a name="schema-excerpt-channeldata-for-channelrenamed"></a>Schemaauszug: channelData für channelRenamed

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

### <a name="schema-excerpt-channeldata-for-channeldeleted"></a>Schemaauszug: channelData for channelDeleted

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

Das `messageReaction` Ereignis wird gesendet, wenn ein Benutzer seine Reaktion auf eine Nachricht, die ursprünglich von Ihrem Bot gesendet wurde, hinzufügt oder entfernt. `replyToId` enthält die ID der bestimmten Nachricht.

### <a name="schema-example-a-user-likes-a-message"></a>Schemabeispiel: Einem Benutzer gefällt eine Nachricht

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

### <a name="schema-example-a-user-un-likes-a-message"></a>Schemabeispiel: Ein Benutzer hebt die Gefällt mir einer Nachricht auf

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
