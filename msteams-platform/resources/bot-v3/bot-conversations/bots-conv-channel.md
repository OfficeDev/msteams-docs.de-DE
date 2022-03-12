---
title: Kanal- und Gruppenchatunterhaltungen mit Bots
description: Beschreibt das End-to-End-Szenario einer Unterhaltung mit einem Bot in einem Kanal in Microsoft Teams
keywords: Teams-Szenarien Kanäle Unterhaltungs-Bot
ms.localizationpriority: medium
ms.topic: conceptual
ms.date: 06/25/2019
ms.openlocfilehash: 1b9d25b7ce6bc30c980634510b5fca7c60f155ef
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2022
ms.locfileid: "63453810"
---
# <a name="channel-and-group-chat-conversations-with-a-microsoft-teams-bot"></a>Kanal und Gruppenchatunterhaltungen mit einem Microsoft Teams-Bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Microsoft Teams ermöglicht Es Benutzern, Bots in ihre Kanal- oder Gruppenchatunterhaltungen zu bringen. Durch Hinzufügen eines Bots zu einem Team oder Chat können alle Benutzer der Unterhaltung die Bot-Funktionalität direkt in der Unterhaltung nutzen. Sie können auch auf Teams-spezifische Funktionen innerhalb Ihres Bots zugreifen, z. B. das Abfragen von Teaminformationen und @mentioning Benutzern.

Chats in Kanälen und Gruppenchats unterscheiden sich von persönlichen Chats darin, dass der Benutzer den Bot @mention muss. Wenn ein Bot in mehreren Bereichen verwendet wird, z. B. persönlich, Gruppenchat oder Kanal, müssen Sie ermitteln, aus welchem Bereich die Botnachrichten stammen, und diese entsprechend verarbeiten.

## <a name="designing-a-great-bot-for-channels-or-groups"></a>Entwerfen eines großartigen Bots für Kanäle oder Gruppen

Bots, die einem Team hinzugefügt werden, werden ein weiteres Teammitglied und können als Teil der Unterhaltung @mentioned werden. Tatsächlich erhalten Bots nur Nachrichten, wenn sie @mentioned sind, sodass andere Unterhaltungen im Kanal nicht an den Bot gesendet werden.

Ein Bot in einer Gruppe oder einem Kanal sollte Informationen bereitstellen, die für alle Mitglieder relevant und geeignet sind. Während Ihr Bot mit Sicherheit alle für die Erfahrung relevanten Informationen bereitstellen kann, denken Sie daran, dass Unterhaltungen mit ihm für jeden sichtbar sind. Daher sollte ein hervorragender Bot in einer Gruppe oder einem Kanal für alle Benutzer einen Mehrwert schaffen und sicher nicht versehentlich Informationen freigeben, die für eine 1:1-Unterhaltung besser geeignet sind.

Ihr Bot kann, wie er ist, in allen Bereichen völlig relevant sein, ohne dass zusätzliche Arbeit erforderlich ist. In Microsoft Teams wird nicht erwartet, dass Ihr Bot in allen Bereichen funktioniert, Aber Sie sollten sicherstellen, dass Ihr Bot einen Benutzerwert in jedem Bereich bereitstellt, den Sie unterstützen möchten. Weitere Informationen zu Bereichen finden Sie [unter Apps in Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md).

Die Entwicklung eines Bots, der in Gruppen oder Kanälen funktioniert, verwendet einen Großteil derselben Funktionalität wie persönliche Unterhaltungen. Zusätzliche Ereignisse und Daten in der Nutzlast stellen Teams Gruppen- und Kanalinformationen bereit. Diese Unterschiede sowie wichtige Unterschiede bei der gemeinsamen Funktionalität werden in den folgenden Abschnitten beschrieben.

### <a name="creating-messages"></a>Erstellen von Nachrichten

Weitere Informationen zu Bots, die Nachrichten in Kanälen erstellen, finden Sie unter [Proaktives Messaging für Bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) und insbesondere [erstellen einer Kanalunterhaltung](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md#creating-a-channel-conversation).

### <a name="receiving-messages"></a>Empfangen von Nachrichten

Für einen Bot in einer Gruppe oder einem Kanal erhält Ihr Bot zusätzlich zum [regulären Nachrichtenschema](https://docs.botframework.com/core-concepts/reference/#activity) auch die folgenden Eigenschaften:

* `channelData`Siehe [Teams Kanaldaten](~/resources/bot-v3/bot-conversations/bots-conversations.md#teams-channel-data). Enthält in einem Gruppenchat spezifische Informationen für diesen Chat.
* `conversation.id` Die Antwortketten-ID, bestehend aus Kanal-ID und der ID der ersten Nachricht in der Antwortkette.
* `conversation.isGroup` Gilt `true` für Bot-Nachrichten in Kanälen oder Gruppenchats.
* `conversation.conversationType` Entweder `groupChat` oder `channel`.
* `entities` Kann eine oder mehrere Erwähnungen enthalten. Weitere Informationen finden Sie unter ["Erwähnungen"](#-mentions).

### <a name="replying-to-messages"></a>Antworten auf Nachrichten

Um auf eine vorhandene Nachricht zu antworten, rufen Sie [`ReplyToActivity`](/bot-framework/dotnet/bot-builder-dotnet-connector#send-a-reply) in .NET oder [`session.send`](/bot-framework/nodejs/bot-builder-nodejs-use-default-message-handler) in Node.js auf. Das Bot Builder SDK verarbeitet alle Details.

Wenn Sie die REST-API verwenden, können Sie auch den [`/conversations/{conversationId}/activities/{activityId}`](/bot-framework/rest-api/bot-framework-rest-connector-send-and-receive-messages#send-the-reply) Endpunkt aufrufen.

In einem Kanal wird das Antworten auf eine Nachricht als Antwort auf die initiierende Antwortkette angezeigt. Enthält `conversation.id` den Kanal und die Nachrichten-ID der obersten Ebene. Obwohl sich das Bot Framework um die Details kümmert, können Sie dies `conversation.id` für zukünftige Antworten auf diesen Unterhaltungsthread nach Bedarf zwischenspeichern.

### <a name="best-practice-welcome-messages-in-teams"></a>Bewährte Methode: Willkommensnachrichten in Teams

Wenn Ihr Bot zum ersten Mal der Gruppe oder dem Team hinzugefügt wird, ist es in der Regel hilfreich, eine Willkommensnachricht zu senden, in der der Bot allen Benutzern vorgestellt wird. Die Willkommensnachricht sollte eine Beschreibung der Funktionalität des Bots und der Benutzervorteile enthalten. Im Idealfall sollte die Nachricht auch Befehle enthalten, mit denen der Benutzer mit der App interagieren kann. Stellen Sie hierzu sicher, dass Ihr Bot auf die Nachricht mit dem `conversationUpdate` `teamsAddMembers` eventType im `channelData` Objekt antwortet. Stellen Sie sicher, dass die `memberAdded` ID die App-ID des Bots selbst ist, da dasselbe Ereignis gesendet wird, wenn ein Benutzer zu einem Team hinzugefügt wird. Weitere Details finden Sie [unter "Teammitglied" oder "Bot"](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) .

Möglicherweise möchten Sie auch eine persönliche Nachricht an jedes Mitglied des Teams senden, wenn der Bot hinzugefügt wird. Dazu können Sie [die Teamliste abrufen](~/resources/bot-v3/bots-context.md#fetch-the-team-roster) und jedem Benutzer eine [direkte Nachricht](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) senden.

Es wird empfohlen, dass Ihr Bot in den folgenden Situationen *keine* Willkommensnachricht sendet:

* Das Team ist groß (natürlich auch von über 100 Mitgliedern). Ihr Bot wird möglicherweise als "Spammy" betrachtet, und die Person, die ihn hinzugefügt hat, kann Beschwerden erhalten, es sei denn, Sie teilen allen, die die Willkommensnachricht sehen, den Wertbeitrag Ihres Bots deutlich mit.
* Ihr Bot wird zuerst in einer Gruppe oder einem Kanal erwähnt, statt zuerst zu einem Team hinzugefügt zu werden.
* Eine Gruppe oder ein Kanal wird umbenannt.
* Ein Teammitglied wird einer Gruppe oder einem Kanal hinzugefügt.

## <a name="-mentions"></a>@ Erwähnungen

Da Bots in einer Gruppe oder einem Kanal nur antworten, wenn sie in einer Nachricht erwähnt werden ("@*Botname*"), enthält jede Nachricht, die von einem Bot in einem Gruppenkanal empfangen wird, einen eigenen Namen, und Sie müssen sicherstellen, dass ihre Nachrichtenparsing dies verarbeitet. Darüber hinaus können Bots andere erwähnten Benutzer analysieren und Benutzer als Teil ihrer Nachrichten erwähnen.

### <a name="retrieving-mentions"></a>Abrufen von Erwähnungen

Erwähnungen werden im `entities` Objekt in Nutzlast zurückgegeben und enthalten sowohl die eindeutige ID des Benutzers als auch in den meisten Fällen den Namen des erwähnten Benutzers. Sie können alle Erwähnungen in der Nachricht abrufen, indem Sie die `GetMentions` Funktion im Bot Builder SDK für .NET aufrufen, das ein Array von `Mentioned` Objekten zurückgibt.

#### <a name="net-example-code-check-for-and-strip-bot-mention"></a>.NET-Beispielcode: Suchen nach und Entfernen @bot Erwähnung

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
> Sie können auch die Teams Erweiterungsfunktion `GetTextWithoutMentions`verwenden, die alle Erwähnungen entfernt, einschließlich des Bots.

#### <a name="nodejs-example-code-check-for-and-strip-bot-mention"></a>Node.js Beispielcode: @bot Erwähnung suchen und entfernen

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

Sie können auch die Teams Erweiterungsfunktion `getTextWithoutMentions`verwenden, die alle Erwähnungen entfernt, einschließlich des Bots.

### <a name="constructing-mentions"></a>Erstellen von Erwähnungen

Ihr Bot kann andere Benutzer in Nachrichten erwähnen, die in Kanälen veröffentlicht wurden. Dazu muss Ihre Nachricht Folgendes tun:

* In den Nachrichtentext einschließen `<at>@username</at>` .
* Schließen Sie das `mention` Objekt in die Entitätensammlung ein.

#### <a name="net-example"></a>.NET-Beispiel

In diesem Beispiel wird das [Paket "Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet" verwendet.

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

Ihr Bot kann mehr als nur Nachrichten in Gruppen und Teams senden und empfangen. Sie kann beispielsweise auch die Liste der Mitglieder, einschließlich ihrer Profilinformationen, sowie die Liste der Kanäle abrufen. Weitere Informationen finden Sie unter ["Kontext für Ihren Microsoft Teams-Bot abrufen](~/resources/bot-v3/bots-context.md)".

## <a name="see-also"></a>Siehe auch

[Bot Framework-Beispiele](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)
