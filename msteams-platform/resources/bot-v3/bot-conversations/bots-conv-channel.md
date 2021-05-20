---
title: Kanal- und Gruppenchat-Gespräche mit Bots
description: Beschreibt das End-to-End-Szenario einer Unterhaltung mit einem Bot in einem Kanal in Microsoft Teams
keywords: Teams Szenarien Kanäle Konversation Bot
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

Microsoft Teams ermöglicht es Benutzern, Bots in ihren Kanal oder Gruppenchat-Gespräche zu bringen. Durch Hinzufügen eines Bots zu einem Team oder Chat können alle Benutzer der Unterhaltung die Vorteile der Bot-Funktionalität direkt in der Unterhaltung nutzen. Sie können auch auf Teams-spezifische Funktionen innerhalb Ihres Bots wie Abfragen von Teaminformationen und @mentioning Benutzer zugreifen.

Chat in Kanälen und Gruppenchats unterscheiden sich von persönlichen Chats dadurch, dass der Benutzer den Bot @mention muss. Wenn ein Bot in mehreren Bereichen wie Personal, Groupchat oder Channel verwendet wird, müssen Sie erkennen, aus welchem Bereich die Bot-Nachrichten stammen, und sie entsprechend verarbeiten.

## <a name="designing-a-great-bot-for-channels-or-groups"></a>Entwerfen eines großartigen Bots für Kanäle oder Gruppen

Bots, die einem Team hinzugefügt werden, werden ein weiteres Teammitglied und können als Teil des Gesprächs @mentioned werden. Tatsächlich empfangen Bots Nachrichten nur, wenn sie @mentioned sind, so dass andere Unterhaltungen auf dem Kanal nicht an den Bot gesendet werden.

Ein Bot in einer Gruppe oder einem Kanal sollte Informationen bereitstellen, die für alle Mitglieder relevant und angemessen sind. Während Ihr Bot kann sicherlich alle Informationen, die für die Erfahrung relevant, denken Sie daran, Gespräche mit ihm sind für jeden sichtbar. Daher sollte ein großartiger Bot in einer Gruppe oder einem Kanal allen Benutzern einen Mehrwert verleihen und sicherlich nicht versehentlich Informationen teilen, die für eine Einzelunterhaltung besser geeignet sind.

Ihr Bot, so wie er ist, kann in allen Bereichen völlig relevant sein, ohne dass zusätzliche Arbeit erforderlich ist. In Microsoft Teams gibt es keine Erwartung, dass Ihr Bot in allen Bereichen funktioniert, aber Sie sollten sicherstellen, dass Ihr Bot Benutzerwert in den Bereichen bietet, die Sie unterstützen möchten. Weitere Informationen zu Bereichen finden Sie [unter Apps in Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md).

Die Entwicklung eines Bots, der in Gruppen oder Kanälen funktioniert, verwendet viele der gleichen Funktionen wie persönliche Unterhaltungen. Zusätzliche Ereignisse und Daten in der Nutzlast stellen Teams Gruppen- und Kanalinformationen bereit. Diese Unterschiede sowie die wichtigsten Unterschiede in der allgemeinen Funktionalität werden in den folgenden Abschnitten beschrieben.

### <a name="creating-messages"></a>Erstellen von Nachrichten

Weitere Informationen zu Bots, die Nachrichten in Kanälen erstellen, finden Sie unter [Proaktive Nachrichten für Bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md)und speziell [erstellen einer Kanalunterhaltung](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md#creating-a-channel-conversation).

### <a name="receiving-messages"></a>Empfangen von Nachrichten

Für einen Bot in einer Gruppe oder einem Kanal erhält Ihr Bot zusätzlich zum [regulären Nachrichtenschema](https://docs.botframework.com/core-concepts/reference/#activity)auch die folgenden Eigenschaften:

* `channelData`Siehe [Teams Kanaldaten](~/resources/bot-v3/bot-conversations/bots-conversations.md#teams-channel-data). Enthält in einem Gruppenchat spezifische Informationen zu diesem Chat.
* `conversation.id` Die Antwortketten-ID, bestehend aus Kanal-ID plus der ID der ersten Nachricht in der Antwortkette.
* `conversation.isGroup` Ist `true` für Bot-Nachrichten in Kanälen oder Gruppenchats.
* `conversation.conversationType` Entweder `groupChat` oder `channel` .
* `entities` Kann eine oder mehrere Erwähnungen enthalten. Weitere Informationen finden Sie unter [Erwähnungen](#-mentions).

### <a name="replying-to-messages"></a>Antworten auf Nachrichten

Um auf eine vorhandene Nachricht zu antworten, rufen Sie [`ReplyToActivity`](/bot-framework/dotnet/bot-builder-dotnet-connector#send-a-reply) .NET oder [`session.send`](/bot-framework/nodejs/bot-builder-nodejs-use-default-message-handler) Node.js an. Das Bot Builder SDK verarbeitet alle Details.

Wenn Sie die REST-API verwenden, können Sie auch den [`/conversations/{conversationId}/activities/{activityId}`](/bot-framework/rest-api/bot-framework-rest-connector-send-and-receive-messages#send-the-reply) Endpunkt aufrufen.

In einem Kanal wird das Beantworten einer Nachricht als Antwort auf die einleitende Antwortkette angezeigt. Der `conversation.id` enthält den Kanal und die Nachrichten-ID der obersten Ebene. Obwohl das Bot Framework sich um die Details kümmert, können Sie dies `conversation.id` bei Bedarf für zukünftige Antworten auf diesen Unterhaltungsthread zwischenspeichern.

### <a name="best-practice-welcome-messages-in-teams"></a>Bewährte Verfahren: Willkommensbotschaften in Teams

Wenn Ihr Bot zum ersten Mal der Gruppe oder dem Team hinzugefügt wird, ist es im Allgemeinen nützlich, eine Willkommensnachricht zu senden, die den Bot an alle Benutzer einführt. Die Begrüßungsnachricht sollte eine Beschreibung der Funktionalität und der Vorteile des Bots enthalten. Idealerweise sollte die Nachricht auch Befehle enthalten, damit der Benutzer mit der App interagieren kann. Stellen Sie hierzu sicher, dass Ihr Bot mit dem eventType im Objekt auf die `conversationUpdate` Nachricht `teamsAddMembers` `channelData` reagiert. Stellen Sie sicher, dass die `memberAdded` ID die App-ID des Bots selbst ist, da dasselbe Ereignis gesendet wird, wenn ein Benutzer einem Team hinzugefügt wird. Weitere Informationen finden Sie unter [Teammitglied oder Bot-Hinzufügen.](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition)

Sie können auch eine persönliche Nachricht an jedes Teammitglied senden, wenn der Bot hinzugefügt wird. Dazu können Sie [den Teamdienst abrufen](~/resources/bot-v3/bots-context.md#fetch-the-team-roster) und jedem Benutzer eine [direkte Nachricht](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md)senden.

Wir empfehlen, dass Ihr Bot in den folgenden Situationen *keine* Willkommensnachricht sendet:

* Das Team ist groß (offensichtlich subjektiv, zum Beispiel mehr als 100 Mitglieder). Ihr Bot kann als "Spammy" angesehen werden und die Person, die ihn hinzugefügt hat, kann Beschwerden erhalten, es sei denn, Sie kommunizieren das Wertversprechen Ihres Bots eindeutig jedem, der die Willkommensnachricht sieht.
* Ihr Bot wird zuerst in einer Gruppe oder einem Kanal erwähnt, im Gegensatz zu einem Team.
* Eine Gruppe oder ein Kanal wird umbenannt.
* Ein Teammitglied wird einer Gruppe oder einem Kanal hinzugefügt.

## <a name="-mentions"></a>• Erwähnungen

Da Bots in einer Gruppe oder einem Kanal nur reagieren, wenn sie in einer Nachricht erwähnt werden _("Botname"),_ enthält jede Nachricht, die von einem Bot in einem Gruppenkanal empfangen wird, ihren eigenen Namen, und Sie müssen sicherstellen, dass Ihre Nachrichtenanalyse dies behandelt. Darüber hinaus können Bots andere Benutzer analysieren und Benutzer als Teil ihrer Nachrichten erwähnen.

### <a name="retrieving-mentions"></a>Abrufen von Erwähnungen

Erwähnungen werden im `entities` Objekt in der Nutzlast zurückgegeben und enthalten sowohl die eindeutige ID des Benutzers als auch in den meisten Fällen den Namen des genannten Benutzers. Sie können alle Erwähnungen in der Nachricht abrufen, indem Sie die `GetMentions` Funktion im Bot Builder SDK für .NET aufrufen, das ein Array von Objekten zurückgibt. `Mentioned`

#### <a name="net-example-code-check-for-and-strip-bot-mention"></a>.NET-Beispielcode: Überprüfen und Entfernen @bot erwähnen

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
> Sie können auch die Teams `GetTextWithoutMentions` Erweiterungsfunktion verwenden, die alle Erwähnungen, einschließlich des Bots, entfernt.

#### <a name="nodejs-example-code-check-for-and-strip-bot-mention"></a>Node.js Beispielcode: Überprüfen sie nach und streifen Sie @bot erwähnen

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

Sie können auch die Teams `getTextWithoutMentions` Erweiterungsfunktion verwenden, die alle Erwähnungen, einschließlich des Bots, entfernt.

### <a name="constructing-mentions"></a>Konstruktionserwähnungen

Ihr Bot kann andere Benutzer in Nachrichten erwähnen, die in Kanälen gesendet werden. Dazu muss Ihre Nachricht wie folgt gehen:

* Fügen Sie `<at>@username</at>` den Nachrichtentext ein.
* Schließen Sie das `mention` Objekt in die Entitätsauflistung ein.

#### <a name="net-example"></a>.NET-Beispiel

In diesem Beispiel wird das [NuGet-Paket Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) verwendet.

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

#### <a name="example-outgoing-message-with-user-mentioned"></a>Beispiel: Ausgehende Nachricht mit erwähntem Benutzer

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

## <a name="accessing-groupchat-or-channel-scope"></a>Zugriff auf groupChat oder Kanalbereich

Ihr Bot kann mehr als nur Nachrichten in Gruppen und Teams senden und empfangen. Beispielsweise kann es auch die Liste der Mitglieder abrufen, einschließlich ihrer Profilinformationen, sowie die Liste der Kanäle. Weitere Informationen finden Sie unter [Kontext abrufen für Ihren Microsoft Teams Bot](~/resources/bot-v3/bots-context.md).

## <a name="see-also"></a>Siehe auch

[Bot Framework-Beispiele](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)
