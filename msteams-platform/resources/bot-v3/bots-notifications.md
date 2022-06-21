---
title: Behandeln von Botereignissen
description: In diesem Modul erfahren Sie, wie Sie Ereignisse in Bots für Microsoft Teams, Teams Mitglied oder Bot-Addition, entferntes Teammitglied oder Bot behandeln und vieles mehr
ms.date: 05/20/2019
ms.topic: how-to
ms.localizationpriority: medium
ms.author: lajanuar
author: surbhigupta
ms.openlocfilehash: 95d6439d396a61471c0e7dbe5942d4b88cc00a87
ms.sourcegitcommit: 7bbb7caf729a00b267ceb8af7defffc91903d945
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2022
ms.locfileid: "66189319"
---
# <a name="handle-bot-events-in-microsoft-teams"></a>Behandeln von Botereignissen in Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Microsoft Teams sendet Benachrichtigungen an Ihren Bot für Änderungen oder Ereignisse, die in Bereichen stattfinden, in denen Ihr Bot aktiv ist. Sie können diese Ereignisse verwenden, um Dienstlogik auszulösen, z. B. folgendes:

* Auslösen einer Willkommensnachricht, wenn Ihr Bot einem Team hinzugefügt ist.
* Abfragen und Zwischenspeichern von Gruppeninformationen, wenn der Bot einem Gruppenchat hinzugefügt ist.
* Aktualisieren zwischengespeicherte Informationen zur Teammitgliedschaft oder zu Kanalinformationen.
* Entfernen zwischengespeicherter Informationen für ein Team, wenn der Bot entfernt wird.
* Wenn eine Botnachricht von einem Benutzer mit „Gefällt mir“ markiert wird.

Jedes Botereignis wird als ein `Activity`-Objekt gesendet, in dem `messageType` definiert, welche Informationen sich im Objekt befinden. Für Nachrichten vom Typ `message` lesen Sie [Nachrichten senden und empfangen](~/resources/bot-v3/bot-conversations/bots-conversations.md).

Teams- und Gruppenereignissen, die `conversationUpdate` vom Typ ausgelöst werden, werden mehr Teams Ereignisinformationen als Teil des Objekts `channelData` übergeben, und daher muss der Ereignishandler die `channelData` Nutzlast für die Teams `eventType` und ereignisspezifischere Metadaten abfragen.

In der folgenden Tabelle sind die Ereignisse aufgeführt, die Ihr Bot empfangen und für die er entsprechende Maßnahmen ergreifen kann.

|Typ|Nutzdatenobjekt|Teams-eventType |Beschreibung|Bereich|
|---|---|---|---|---|
| `conversationUpdate` |`membersAdded`| `teamMemberAdded`|[Mitglied zum Team hinzugefügt](#team-member-or-bot-addition)| alle |
| `conversationUpdate` |`membersRemoved`| `teamMemberRemoved`|[Mitglied wurde aus dem Team entfernt](#team-member-or-bot-removed)| `groupChat` & `team` |
| `conversationUpdate` | |`teamRenamed`| [Team wurde umbenannt](#team-name-updates)| `team` |
| `conversationUpdate` | |`channelCreated`| [Ein Kanal wurde erstellt](#channel-updates)|`team` |
| `conversationUpdate` | |`channelRenamed`| [Ein Kanal wurde umbenannt](#channel-updates)|`team` |
| `conversationUpdate` | |`channelDeleted`| [Ein Kanal wurde gelöscht](#channel-updates)|`team` |
| `messageReaction` |`reactionsAdded`|| [Reaktion auf Botnachricht](#reactions)| alle |
| `messageReaction` |`reactionsRemoved`|| [Reaktion aus Botnachricht entfernt](#reactions)| alle |

## <a name="team-member-or-bot-addition"></a>Hinzufügen von Teammitglied oder Bot

Das [`conversationUpdate`](/azure/bot-service/dotnet/bot-builder-dotnet-activities?view=azure-bot-service-3.0#conversationupdate&preserve-view=true)-Ereignis wird an Ihren Bot gesendet, wenn er Informationen zu Mitgliedschaftsaktualisierungen für Teams empfängt, denen er hinzugefügt wurde. Er empfängt außerdem eine Aktualisierung, wenn er zum ersten Mal hinzugefügt wurde, speziell für persönliche Unterhaltungen. Die Benutzerinformationen (`Id`) sind für Ihren Bot eindeutig und können für die zukünftige Verwendung durch Ihren Dienst zwischengespeichert werden, z. B. das Senden einer Nachricht an einen bestimmten Benutzer.

### <a name="bot-or-user-added-to-a-team"></a>Bot oder Benutzer zu einem Team hinzugefügt

Das `conversationUpdate`-Ereignis mit dem `membersAdded`-Objekt in den Nutzdaten wird gesendet, wenn entweder einem Team ein Bot hinzugefügt wird, oder wenn ein neuer Benutzer zu einem Team hinzugefügt wird, in dem ein Bot hinzugefügt wurde. Teams fügt das `channelData` Objekt ebenfalls hinzu`eventType.teamMemberAdded`.

Da dieses Ereignis in beiden Fällen gesendet wird, sollten Sie das `membersAdded`-Objekt parsen, um zu bestimmen, ob das hinzugefügte Objekt ein Benutzer oder der Bot selbst war. Für Letzteres empfiehlt es sich, eine [Willkommensnachricht](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#best-practice-welcome-messages-in-teams) an den Kanal zu senden, damit Benutzer die Features verstehen können, die Ihr Bot bereitstellt.

#### <a name="example-code-checking-whether-bot-was-the-added-member"></a>Beispielcode: Überprüfen, ob der Bot das hinzugefügte Mitglied war

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

### <a name="user-added-to-a-meeting"></a>Benutzer zu einer Besprechung hinzugefügt

Das `conversationUpdate`-Ereignis mit dem `membersAdded`-Objekt in den Nutzdaten wird gesendet, wenn ein Benutzer zu einer privaten geplanten Besprechung hinzugefügt wird. Die Ereignisdetails werden auch dann gesendet, wenn anonyme Benutzer an der Besprechung teilnehmen.

> [!NOTE]
>
>* Wenn ein anonymer Benutzer zu einer Besprechung hinzugefügt wird, verfügt das membersAdded-Nutzdatenobjekt nicht über das `aadObjectId`-Feld.
>* Wenn ein anonymer Benutzer zu einer Besprechung hinzugefügt wird, weist das `from`-Objekt in den Nutzdaten immer die ID des Besprechungsorganisators auf, auch wenn der anonyme Benutzer von einem anderen Referenten hinzugefügt wurde.

#### <a name="schema-example-user-added-to-meeting"></a>Schemabeispiel: Benutzer zu Besprechung hinzugefügt

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

### <a name="bot-added-for-personal-context-only"></a>Bot nur für privaten Kontext hinzugefügt

Ihr Bot erhält eine `conversationUpdate` mit `membersAdded`, wenn ein Benutzer ihn direkt für den privaten Chat hinzufügt. In diesem Fall enthalten die Nutzdaten, die Ihr Bot empfängt, nicht das `channelData.team`-Objekt. Sie sollten dies als Filter verwenden, falls Ihr Bot abhängig vom Bereich eine unterschiedliche [Willkommensnachricht](~/resources/bot-v3/bot-conversations/bots-conv-personal.md#best-practice-welcome-messages-in-personal-conversations) anbieten soll.

> [!NOTE]
> Bei Bots für den privaten Bereich wird Ihr Bot das `conversationUpdate`-Ereignis mehrmals empfangen, auch wenn der Bot entfernt und erneut hinzugefügt wird. Für Entwicklungs- und Testzwecke kann es hilfreich sein, eine Hilfsfunktion hinzuzufügen, die Ihnen erlaubt, Ihren Bot vollständig zurückzusetzen. Weitere Informationen zu dieser Implementierung finden Sie in einem [Node.js-Beispiel](https://github.com/OfficeDev/microsoft-teams-sample-complete-node/blob/master/src/middleware/SimulateResetBotChat.ts) oder einem [C#-Beispiel](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp/blob/master/template-bot-master-csharp/src/controllers/MessagesController.cs#L238).

#### <a name="schema-example-bot-added-to-personal-context"></a>Schemabeispiel: Bot zum privaten Kontext hinzugefügt

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

Das `conversationUpdate`-Ereignis mit dem `membersRemoved`-Objekt in den Nutzdaten wird gesendet, wenn entweder Ihr Bot aus einem Team entfernt wird, oder wenn ein Benutzer aus einem Team entfernt wird, in dem ein Bot hinzugefügt wurde. Teams fügt das `channelData` Objekt ebenfalls hinzu`eventType.teamMemberRemoved`. Wie beim `membersAdded`-Objekt sollten Sie das `membersRemoved`-Objekt für die App-ID Ihres Bots parsen, um zu bestimmen, wer entfernt wurde.

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

Das `conversationUpdate`-Ereignis mit dem `membersRemoved`-Objekt in den Nutzdaten wird gesendet, wenn ein Benutzer aus einer privaten geplanten Besprechung entfernt wird. Die Ereignisdetails werden auch dann gesendet, wenn anonyme Benutzer an der Besprechung teilnehmen.

> [!NOTE]
>
>* Wenn ein anonymer Benutzer aus einer Besprechung entfernt wird, verfügt das membersRemoved-Nutzdatenobjekt nicht über das `aadObjectId`-Feld.
>* Wenn ein anonymer Benutzer aus einer Besprechung entfernt wird, weist das `from`-Objekt in den Nutzdaten immer die ID des Besprechungsorganisators auf, auch wenn der anonyme Benutzer von einem anderen Referenten entfernt wurde.

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

## <a name="team-name-updates"></a>Aktualisierungen des Teamnamens

> [!NOTE]
> Es gibt keine Funktionalität zum Abfragen aller Teamnamen, und der Teamname wird nicht in Nutzdaten von anderen Ereignissen zurückgegeben.

Ihr Bot wird benachrichtigt, wenn das Team, in dem er sich befindet, umbenannt wurde. Er empfängt ein `conversationUpdate`-Ereignis mit `eventType.teamRenamed` im `channelData`-Objekt. Beachten Sie, dass es keine Benachrichtigungen für die Teamerstellung oder -löschung gibt, da Bots nur als Teil von Teams vorhanden sind und keine Sichtbarkeit außerhalb des Bereichs haben, in dem sie hinzugefügt wurden.

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

Ihr Bot wird benachrichtigt, wenn ein Kanal in einem Team erstellt, umbenannt oder gelöscht wird, in dem er hinzugefügt wurde. Auch hier wird das `conversationUpdate`-Ereignis empfangen, und ein Teams-spezifischer Ereignisbezeichner wird als Teil des `channelData.eventType`-Objekts gesendet. wobei die `channel.id` der Kanaldaten die GUID für den Kanal ist, und `channel.name` den Kanalnamen selbst enthält.

Die Kanalereignisse sind wie folgt:

* **channelCreated**&emsp;Ein Benutzer fügt dem Team einen neuen Kanal hinzu.
* **channelRenamed**&emsp;Ein Benutzer benennt einen vorhandenen Kanal um.
* **channelDeleted**&emsp;Ein Benutzer entfernt einen Kanal.

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

### <a name="schema-excerpt-channeldata-for-channeldeleted"></a>Schemaauszug: channelData für channelDeleted

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

Das `messageReaction` Ereignis wird gesendet, wenn ein Benutzer seine Reaktion auf eine Nachricht hinzufügt oder entfernt, die ursprünglich von Ihrem Bot gesendet wurde. `replyToId` enthält die ID der spezifischen Nachricht.

### <a name="schema-example-a-user-likes-a-message"></a>Schemabeispiel: Einem Benutzer markiert eine Nachricht mit „Gefällt mir“

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

### <a name="schema-example-a-user-un-likes-a-message"></a>Schemabeispiel: Ein Benutzer hebt die „Gefällt mit“-Markierung einer Nachricht auf.

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
