---
title: Kanal- und Gruppenchatunterhaltungen mit Bots
description: Beschreibt das End-to-End-Szenario einer Unterhaltung mit einem Bot in einem Kanal in Microsoft Teams
keywords: teams scenarios channels conversation bot
localization_priority: Normal
ms.topic: conceptual
ms.date: 06/25/2019
ms.openlocfilehash: e254302271cf101638c897e1a1952d302705d6a4
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566796"
---
# <a name="channel-and-group-chat-conversations-with-a-microsoft-teams-bot"></a>Kanal und Gruppenchatunterhaltungen mit einem Microsoft Teams-Bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Microsoft Teams ermöglicht Benutzern, Bots in ihren Kanal oder Gruppenchatunterhaltungen zu bringen. Durch Hinzufügen eines Bots zu einem Team oder Chat können alle Benutzer der Unterhaltung die Botfunktionalität direkt in der Unterhaltung nutzen. Sie können auch auf Teams-spezifischen Funktionen innerhalb Ihres Bots zugreifen, z. B. das Abfragen von Teaminformationen und @mentioning Benutzern.

Chats in Kanälen und Gruppenchats unterscheiden sich von persönlichen Chats, da der Benutzer den @mention muss. Wenn ein Bot in mehreren Bereiche wie persönlichen, Groupchats oder Kanälen verwendet wird, müssen Sie erkennen, aus welchem Bereich die Botnachrichten stammten, und diese entsprechend verarbeiten.

## <a name="designing-a-great-bot-for-channels-or-groups"></a>Entwerfen eines großartigen Bots für Kanäle oder Gruppen

Bots, die einem Team hinzugefügt wurden, werden ein weiteres Teammitglied und können @mentioned Teil der Unterhaltung hinzugefügt werden. Bots empfangen nachrichten nur, wenn sie @mentioned werden, sodass andere Unterhaltungen auf dem Kanal nicht an den Bot gesendet werden.

Ein Bot in einer Gruppe oder einem Kanal sollte relevante und für alle Mitglieder geeignete Informationen bereitstellen. Während Ihr Bot sicherlich alle informationen bereitstellen kann, die für die Erfahrung relevant sind, denken Sie daran, dass Unterhaltungen mit ihm für alle sichtbar sind. Daher sollte ein großartiger Bot in einer Gruppe oder einem Kanal allen Benutzern einen Mehrwert bringen und sicher nicht versehentlich Informationen freigeben, die besser für eine 1:1-Unterhaltung geeignet sind.

Ihr Bot ist möglicherweise in allen Bereiche vollständig relevant, ohne dass zusätzliche Arbeit erforderlich ist. In Microsoft Teams wird nicht erwartet, dass Ihre Botfunktion in allen Bereiche funktioniert. Sie sollten jedoch sicherstellen, dass Ihr Bot den Benutzerwert in welchem Bereich(n) Sie unterstützen. Weitere Informationen zu Bereich finden Sie unter [Apps in Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md).

Die Entwicklung eines Bots, der in Gruppen oder Kanälen funktioniert, verwendet viele der gleichen Funktionen wie persönliche Unterhaltungen. Zusätzliche Ereignisse und Daten in der Nutzlast Teams Gruppen- und Kanalinformationen. Diese Unterschiede sowie wichtige Unterschiede bei den allgemeinen Funktionen werden in den folgenden Abschnitten beschrieben.

### <a name="creating-messages"></a>Erstellen von Nachrichten

Weitere Informationen zu Bots, die Nachrichten in Kanälen erstellen, finden Sie unter [Proaktives Messaging](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md)für Bots und insbesondere [Erstellen einer Kanal unterhaltung.](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md#creating-a-channel-conversation)

### <a name="receiving-messages"></a>Empfangen von Nachrichten

Für einen Bot in einer Gruppe oder [](https://docs.botframework.com/core-concepts/reference/#activity)einem Kanal erhält ihr Bot zusätzlich zum regulären Nachrichtenschema auch die folgenden Eigenschaften:

* `channelData`Siehe [Teams Kanaldaten](~/resources/bot-v3/bot-conversations/bots-conversations.md#teams-channel-data). Enthält in einem Gruppenchat spezifische Informationen für diesen Chat.
* `conversation.id` Die Antwortkette-ID, die aus Kanal-ID und der ID der ersten Nachricht in der Antwortkette besteht.
* `conversation.isGroup` Ist `true` für Botnachrichten in Kanälen oder Gruppenchats.
* `conversation.conversationType` Entweder `groupChat` oder `channel` .
* `entities` Kann eine oder mehrere Erwähnungen enthalten. Weitere Informationen finden Sie unter [Erwähnungen](#-mentions).

### <a name="replying-to-messages"></a>Antworten auf Nachrichten

Um auf eine vorhandene Nachricht zu antworten, rufen Sie [`ReplyToActivity`](/bot-framework/dotnet/bot-builder-dotnet-connector#send-a-reply) in .NET oder [`session.send`](/bot-framework/nodejs/bot-builder-nodejs-use-default-message-handler) in Node.js. Das Bot Builder SDK verarbeitet alle Details.

Wenn Sie die REST-API verwenden möchten, können Sie auch den Endpunkt [`/conversations/{conversationId}/activities/{activityId}`](/bot-framework/rest-api/bot-framework-rest-connector-send-and-receive-messages#send-the-reply) aufrufen.

In einem Kanal wird die Antwort auf eine Nachricht als Antwort auf die initiierende Antwortkette angezeigt. Der `conversation.id` enthält den Kanal und die Nachrichten-ID der obersten Ebene. Obwohl das Bot Framework sich um die Details kümmert, können Sie dies für zukünftige Antworten auf den `conversation.id` Unterhaltungsthread nach Bedarf zwischenspeichern.

### <a name="best-practice-welcome-messages-in-teams"></a>Bewährte Methode: Willkommensnachrichten in Teams

Wenn Ihr Bot zum ersten Mal der Gruppe oder dem Team hinzugefügt wird, ist es im Allgemeinen hilfreich, eine Willkommensnachricht zu senden, in der der Bot für alle Benutzer eingeführt wird. Die Willkommensnachricht sollte eine Beschreibung der Funktionalität und der Benutzervorteile des Bots enthalten. Idealerweise sollte die Nachricht auch Befehle enthalten, mit denen der Benutzer mit der App interagieren kann. Stellen Sie dazu sicher, dass Ihr Bot auf die Nachricht mit `conversationUpdate` `teamsAddMembers` dem eventType im Objekt `channelData` antwortet. Stellen Sie sicher, dass die ID die App-ID des Bots selbst ist, da dasselbe Ereignis gesendet wird, wenn ein Benutzer einem `memberAdded` Team hinzugefügt wird. Weitere Informationen finden Sie unter [Teammitglied oder](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) Bot-Ergänzung.

Sie können auch eine persönliche Nachricht an jedes Mitglied des Teams senden, wenn der Bot hinzugefügt wird. Dazu können Sie die [Teamliste](~/resources/bot-v3/bots-context.md#fetch-the-team-roster) abrufen und jedem Benutzer eine direkte [Nachricht senden.](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md)

Es wird empfohlen, dass Ihr *Bot* in den folgenden Situationen keine Willkommensnachricht sendet:

* Das Team ist groß (natürlich subjektiv, z. B. mehr als 100 Mitglieder). Ihr Bot kann als "Spammy" betrachtet werden, und die Person, die ihn hinzugefügt hat, kann Beschwerden erhalten, es sei denn, Sie teilen die Wertversprechen Ihres Bots jedem klar mit, der die Willkommensnachricht sieht.
* Ihr Bot wird zuerst in einer Gruppe oder einem Kanal erwähnt, statt zuerst einem Team hinzugefügt zu werden.
* Eine Gruppe oder ein Kanal wird umbenannt.
* Ein Teammitglied wird einer Gruppe oder einem Kanal hinzugefügt.

## <a name="-mentions"></a>@ Erwähnungen

Da Bots in einer Gruppe oder einem Kanal nur antworten, wenn sie in einer Nachricht ("@_botname")_ erwähnt werden, enthält jede Nachricht, die von einem Bot in einem Gruppenkanal empfangen wird, einen eigenen Namen, und Sie müssen sicherstellen, dass die Nachrichten parsing dies verarbeitet. Darüber hinaus können Bots andere erwähnten Benutzer analysieren und Benutzer als Teil ihrer Nachrichten erwähnen.

### <a name="retrieving-mentions"></a>Abrufen von Erwähnungen

Erwähnungen werden im Objekt in nutzlast zurückgegeben und enthalten sowohl die eindeutige ID des Benutzers als auch in den meisten Fällen den Namen `entities` des erwähnten Benutzers. Sie können alle Erwähnungen in der Nachricht abrufen, indem Sie die Funktion `GetMentions` im Bot Builder SDK für .NET aufrufen, das ein Array von Objekten `Mentioned` zurückgibt.

#### <a name="net-example-code-check-for-and-strip-bot-mention"></a>.NET-Beispielcode: Überprüfen sie, ob eine Erwähnung @bot wird.

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
> Sie können auch die erweiterungsfunktion Teams, die alle Erwähnungen `GetTextWithoutMentions` ausstreift, einschließlich des Bots.

#### <a name="nodejs-example-code-check-for-and-strip-bot-mention"></a>Node.js Beispielcode: Überprüfen sie, ob eine Erwähnung @bot wird.

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

Sie können auch die erweiterungsfunktion Teams, die alle Erwähnungen `getTextWithoutMentions` ausstreift, einschließlich des Bots.

### <a name="constructing-mentions"></a>Erstellen von Erwähnungen

Ihr Bot kann andere Benutzer in Nachrichten erwähnen, die in Kanälen gepostet werden. Dazu muss Ihre Nachricht folgendes tun:

* In `<at>@username</at>` den Nachrichtentext eingeben.
* Schließen Sie `mention` das Objekt in die Entitätssammlung ein.

#### <a name="net-example"></a>.NET-Beispiel

In diesem Beispiel wird das [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet verwendet.

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

## <a name="accessing-groupchat-or-channel-scope"></a>Zugreifen auf groupChat oder Kanalbereich

Ihr Bot kann mehr als nachrichten in Gruppen und Teams senden und empfangen. Beispielsweise kann sie auch die Liste der Mitglieder abrufen, einschließlich ihrer Profilinformationen, sowie die Liste der Kanäle. Weitere Informationen finden Sie unter [Get context for your Microsoft Teams bot](~/resources/bot-v3/bots-context.md).

## <a name="see-also"></a>Siehe auch

[Bot Framework-Beispiele](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)
