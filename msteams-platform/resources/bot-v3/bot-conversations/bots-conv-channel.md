---
title: Kanal- und Gruppenchatunterhaltungen mit Bots
description: Beschreibt das End-to-End-Szenario einer Unterhaltung mit einem Bot in einem Kanal in Microsoft Teams
keywords: teams scenarios channels conversation bot
ms.date: 06/25/2019
ms.openlocfilehash: e556eb006257a83ddf93adb62f79857201d6a9ad
ms.sourcegitcommit: e3b6bc31059ec77de5fbef9b15c17d358abbca0f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/12/2021
ms.locfileid: "50231631"
---
# <a name="channel-and-group-chat-conversations-with-a-microsoft-teams-bot"></a>Kanal und Gruppenchatunterhaltungen mit einem Microsoft Teams-Bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Microsoft Teams ermöglicht Benutzern, Bots in ihre Kanal- oder Gruppenchatunterhaltungen zu bringen. Durch Hinzufügen eines Bots zu einem Team oder Chat können alle Benutzer der Unterhaltung die Botfunktionalität direkt in der Unterhaltung nutzen. Sie können auch auf Teams-spezifische Funktionen innerhalb Ihres Bots zugreifen, z. B. Teaminformationen abfragen und @mentioning verwenden.

Chats in Kanälen und Gruppenchats unterscheiden sich von persönlichen Chats, da der Benutzer den @mention muss. Wenn ein Bot in mehreren Bereiche (persönlich, Groupchat oder Kanal) verwendet wird, müssen Sie erkennen, aus welchem Bereich die Botnachrichten stammten, und diese entsprechend verarbeiten.

## <a name="designing-a-great-bot-for-channels-or-groups"></a>Entwerfen eines großartigen Bots für Kanäle oder Gruppen

Bots, die einem Team hinzugefügt wurden, werden ein weiteres Teammitglied und können @mentioned Teil der Unterhaltung hinzugefügt werden. Bots empfangen nachrichten nur, wenn sie @mentioned, sodass andere Unterhaltungen im Kanal nicht an den Bot gesendet werden.

Ein Bot in einer Gruppe oder einem Kanal sollte relevante und für alle Mitglieder geeignete Informationen bereitstellen. Während Ihr Bot mit Sicherheit alle für die Erfahrung relevanten Informationen bereitstellen kann, denken Sie daran, dass Unterhaltungen damit für alle sichtbar sind. Daher sollte ein großartiger Bot in einer Gruppe oder einem Kanal einen Mehrwert für alle Benutzer schaffen und sicher nicht versehentlich Informationen freigeben, die für eine 1:1-Unterhaltung besser geeignet sind.

Ihr Bot kann, genau wie er ist, in allen Bereiche ohne zusätzliche Arbeit vollständig relevant sein. In Microsoft Teams wird nicht erwartet, dass Ihr Bot in allen Bereiche funktioniert. Sie sollten jedoch sicherstellen, dass Ihr Bot einen Benutzerwert in jedem Bereich(n) bietet, den Sie unterstützen möchten. Weitere Informationen zu Bereich finden Sie unter ["Apps in Microsoft Teams".](~/concepts/build-and-test/app-studio-overview.md)

Die Entwicklung eines Bots, der in Gruppen oder Kanälen funktioniert, nutzt die gleiche Funktionalität wie persönliche Unterhaltungen. Zusätzliche Ereignisse und Daten in der Nutzlast stellen Gruppen- und Kanalinformationen für Teams zur Verfügung. Diese Unterschiede sowie wichtige Unterschiede bei allgemeinen Funktionen werden in den folgenden Abschnitten beschrieben.

### <a name="creating-messages"></a>Erstellen von Nachrichten

Weitere Informationen zu Bots, die Nachrichten in Kanälen erstellen, finden Sie unter [Proaktives Messaging](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md)für Bots und insbesondere zum Erstellen [einer Kanal-Unterhaltung.](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md#creating-a-channel-conversation)

### <a name="receiving-messages"></a>Empfangen von Nachrichten

Für einen Bot in einer Gruppe oder [](https://docs.botframework.com/core-concepts/reference/#activity)einem Kanal erhält Ihr Bot zusätzlich zum regulären Nachrichtenschema auch die folgenden Eigenschaften:

* `channelData`Siehe [Teams-Kanaldaten.](~/resources/bot-v3/bot-conversations/bots-conversations.md#teams-channel-data) Enthält in einem Gruppenchat spezifische Informationen zu diesem Chat.
* `conversation.id` Die Antwortketten-ID, bestehend aus Kanal-ID und der ID der ersten Nachricht in der Antwortkette
* `conversation.isGroup` Für `true` Botnachrichten in Kanälen oder Gruppenchats
* `conversation.conversationType` Entweder `groupChat` oder `channel`
* `entities` Kann eine oder mehrere Erwähnungen enthalten (siehe [Erwähnungen](#-mentions))

### <a name="replying-to-messages"></a>Antworten auf Nachrichten

Um auf eine vorhandene Nachricht zu antworten, rufen Sie [`ReplyToActivity`](/bot-framework/dotnet/bot-builder-dotnet-connector#send-a-reply) in .NET oder [`session.send`](/bot-framework/nodejs/bot-builder-nodejs-use-default-message-handler) in Node.js. Das Bot Builder SDK verarbeitet alle Details.

Wenn Sie die REST-API verwenden möchten, können Sie auch den Endpunkt [`/conversations/{conversationId}/activities/{activityId}`](/bot-framework/rest-api/bot-framework-rest-connector-send-and-receive-messages#send-the-reply) aufrufen.

In einem Kanal wird das Antworten auf eine Nachricht als Antwort an die initiierende Antwortkette angezeigt. Der `conversation.id` enthält den Kanal und die Nachrichten-ID der obersten Ebene. Obwohl das Bot Framework die Details übernimmt, können Sie dies für zukünftige Antworten `conversation.id` auf den Unterhaltungsthread nach Bedarf zwischenspeichern.

### <a name="best-practice-welcome-messages-in-teams"></a>Bewährte Methode: Willkommensnachrichten in Teams

Wenn Ihr Bot zum ersten Mal der Gruppe oder dem Team hinzugefügt wird, ist es in der Regel hilfreich, allen Benutzern eine Willkommensnachricht zu senden, in der der Bot eingeführt wird. Die Willkommensnachricht sollte eine Beschreibung der Funktionalität und der Benutzervorteile des Bots enthalten. Im Idealfall sollte die Nachricht auch Befehle enthalten, mit denen der Benutzer mit der App interagieren kann. Stellen Sie dazu sicher, dass Ihr Bot auf die Nachricht mit dem `conversationUpdate` `teamsAddMembers` eventType im Objekt `channelData` reagiert. Stellen Sie sicher, dass die ID die App-ID des Bots selbst ist, da dasselbe Ereignis gesendet wird, wenn ein Benutzer `memberAdded` zu einem Team hinzugefügt wird. Weitere [Informationen finden Sie unter "Teammitglied oder Bot-Ergänzung".](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition)

Sie können auch eine persönliche Nachricht an jedes Mitglied des Teams senden, wenn der Bot hinzugefügt wird. Dazu können Sie die [Teamliste](~/resources/bot-v3/bots-context.md#fetch-the-team-roster) abrufen und jedem Benutzer eine direkte [Nachricht senden.](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md)

Es wird empfohlen, dass Ihr *Bot* in den folgenden Situationen keine Willkommensnachricht sendet:

* Das Team ist groß (natürlich subjektiv, aber z. B. größer als 100 Mitglieder). Ihr Bot wird möglicherweise als "Spammy" betrachtet, und die Person, die ihn hinzugefügt hat, wird möglicherweise beschwert, es sei denn, Sie teilen das Wertversprechen Ihres Bots jedem klar mit, der die Willkommensnachricht sieht.
* Ihr Bot wird zuerst in einer Gruppe oder einem Kanal erwähnt (im Gegensatz zum ersten Hinzufügen zu einem Team)
* Eine Gruppe oder ein Kanal wird umbenannt
* Ein Teammitglied wird einer Gruppe oder einem Kanal hinzugefügt

## <a name="-mentions"></a>@ Erwähnungen

Da Bots in einer Gruppe oder einem Kanal nur antworten, wenn sie in einer Nachricht ("@_Botname")_ erwähnt werden, enthält jede Nachricht, die von einem Bot in einem Gruppenkanal empfangen wird, einen eigenen Namen, und Sie müssen sicherstellen, dass ihre Nachrichtenparsierung dies verarbeitet. Darüber hinaus können Bots andere erwähnte Benutzer analysieren und Benutzer als Teil ihrer Nachrichten erwähnen.

### <a name="retrieving-mentions"></a>Abrufen von Erwähnungen

Erwähnungen werden in der Nutzlast des Objekts zurückgegeben und enthalten sowohl die eindeutige ID des Benutzers als auch in den meisten Fällen den Namen `entities` des erwähnten Benutzers. Sie können alle Erwähnungen in der Nachricht abrufen, indem Sie die Funktion im Bot Builder SDK für .NET aufrufen, das ein Array von `GetMentions` Objekten `Mentioned` zurückgibt.

#### <a name="net-example-code-check-for-and-strip-bot-mention"></a>.NET-Beispielcode: Suchen nach und @bot Erwähnung

```csharp
Mention[] m = sourceMessage.GetMentions();
var messageText = sourceMessage.Text;

for (int i = 0;i < m.Length;i++)
{
    if (m[i].Mentioned.Id == sourceMessage.Recipient.Id)
    {
        //Bot is in the @mention list.
        //The below example will strip the bot name out of the message, so you can parse it as if it wasn't included. Note that the Text object will contain the full bot name, if applicable.
        if (m[i].Text != null)
            messageText = messageText.Replace(m[i].Text, "");
    }
}
```

> [!NOTE]
> Sie können auch die Erweiterungsfunktion "Teams" verwenden, mit der alle Erwähnungen, einschließlich `GetTextWithoutMentions` des Bots, entfernt werden.

#### <a name="nodejs-example-code-check-for-and-strip-bot-mention"></a>Node.js Beispielcode: Suchen nach erwähnungen und @bot sie aus.

```javascript
var text = message.text;
if (message.entities) {
    message.entities
        .filter(entity => ((entity.type === "mention") && (entity.mentioned.id.toLowerCase() === botId)))
        .forEach(entity => {
            text = text.replace(entity.text, "");
        });
    text = text.trim();
}
```

Sie können auch die Erweiterungsfunktion "Teams" verwenden, mit der alle Erwähnungen, einschließlich `getTextWithoutMentions` des Bots, entfernt werden.

### <a name="constructing-mentions"></a>Erstellen von Erwähnungen

Ihr Bot kann andere Benutzer in Nachrichten erwähnen, die in Kanälen gepostet werden. Dazu muss Ihre Nachricht folgendes tun:

* Im `<at>@username</at>` Nachrichtentext enthalten
* Schließen Sie `mention` das Objekt in die Entitätensammlung ein.

#### <a name="net-example"></a>.NET-Beispiel

In diesem Beispiel wird das [Microsoft.Bot.Connector.Teams-NuGet-Paket](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) verwendet.

```csharp
// Create reply activity
Activity replyActivity = activity.CreateReply();

// Construct text of the form @sender Hello
replyActivity.Text = "Hello ";
replyActivity.AddMentionToText(activity.From, MentionTextLocation.AppendText);

// Send the reply activity
await client.Conversations.ReplyToActivityAsync(replyActivity);
```

#### <a name="nodejs-example"></a>Node.js Beispiel

```javascript
// User to mention
var toMention: builder.IIdentity = {
    name: 'John Doe',
    id: userId
};

// Create a message and add mention to it
var msg = new teams.TeamsMessage(session).text(teams.TeamsMessage.getTenantId(session.message));
var mentionedMsg = msg.addMentionToText(toMention);

// Post the message
var generalMessage = mentionedMsg.routeReplyToGeneralChannel();
session.send(generalMessage);
```

#### <a name="example-outgoing-message-with-user-mentioned"></a>Beispiel: Ausgehende Nachricht mit erwähnten Benutzern

```json
{
    "type": "message", 
    "text": "Hey <at>Pranav Smith</at> check out this message",
    "timestamp": "2017-10-29T00:51:05.9908157Z",
    "localTimestamp": "2017-10-28T17:51:05.9908157-07:00",
    "serviceUrl": "https://skype.botframework.com",
    "channelId": "msteams",
    "from": {
        "id": "28:9e52142b-5e5e-4d7b-bb3e- e82dcf620000",
        "name": "SchemaTestBot"
    },
    "conversation": {
        "id": "19:aebd0ad4d6ab42c8b9ed19c251c2fc37@thread.skype;messageid=1481567603816"
    },
    "recipient": {
        "id": "8:orgid:6aebbad0-e5a5-424a-834a-20fb051f3c1a",
        "name": "stlrgload100"
    },
    "attachments": [
        {
            "contentType": "image/png",
            "contentUrl": "https://upload.wikimedia.org/wikipedia/en/a/a6/Bender_Rodriguez.png",
            "name": "Bender_Rodriguez.png"
        }
    ],
    "entities": [
        {
            "type":"mention",
            "mentioned":{
                "id":"29:08q2j2o3jc09au90eucae",
                "name":"Pranav Smith"
            },
            "text": "<at>@Pranav Smith</at>"
        }
    ],
    "replyToId": "3UP4UTkzUk1zzeyW"
}
```

## <a name="accessing-groupchat-or-channel-scope"></a>Zugreifen auf groupChat- oder Kanalbereich

Ihr Bot kann mehr tun als Nachrichten in Gruppen und Teams zu senden und zu empfangen. Beispielsweise kann sie auch die Liste der Mitglieder, einschließlich ihrer Profilinformationen, sowie die Liste der Kanäle abrufen. Weitere Informationen finden Sie unter "Kontext [für Ihren Microsoft Teams-Bot".](~/resources/bot-v3/bots-context.md)

*Siehe auch* [Bot Framework-Beispiele.](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)
