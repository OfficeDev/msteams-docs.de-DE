---
title: Kanal-und Gruppenchat Unterhaltungen mit Bots
description: Beschreibt das End-to-End-Szenario, dass eine Unterhaltung mit einem bot in einem Kanal in Microsoft Teams vorliegt.
keywords: Teams Szenarien Kanäle Conversation bot
ms.date: 06/25/2019
ms.openlocfilehash: d2d72bdba43de6ebb10c7504dd309459cb09d56c
ms.sourcegitcommit: fdcd91b270d4c2e98ab2b2c1029c76c49bb807fa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "44801279"
---
# <a name="channel-and-group-chat-conversations-with-a-microsoft-teams-bot"></a>Kanal und Gruppenchatunterhaltungen mit einem Microsoft Teams-Bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Microsoft Teams ermöglicht es Benutzern, Bots in Ihren Kanal-oder Gruppenchat-Unterhaltungen zu integrieren. Durch Hinzufügen eines bot zu einem Team oder Chat können alle Benutzer der Unterhaltung die bot-Funktionalität direkt in der Unterhaltung nutzen. Sie können auch auf Teams-spezifische Funktionen innerhalb Ihres bot zugreifen, wie Team Informationen Abfragen und @mentioning Benutzer.

Chat in Kanälen und Gruppenchats unterscheiden sich vom persönlichen Chat dadurch, dass der Benutzer den bot @mention muss. Wenn ein bot in mehreren Bereichen (Personal, Groupchat oder Kanal) verwendet wird, müssen Sie ermitteln, von welchem Bereich die bot-Nachrichten stammen, und diese entsprechend verarbeiten.

## <a name="designing-a-great-bot-for-channels-or-groups"></a>Entwerfen eines großen bot für Kanäle oder Gruppen

Bots, die einem Team hinzugefügt werden, werden ein weiteres Teammitglied, das als Teil der Unterhaltung @mentioned werden kann. Bots empfangen tatsächlich nur Nachrichten, wenn Sie @mentioned sind, sodass andere Unterhaltungen im Kanal nicht an den bot gesendet werden.

> [!NOTE]
> Zur Vereinfachung beim Antworten auf bot-Nachrichten in einem Kanal wird der Name des bot automatisch im Meldungsfeld verfassen vorangestellt.

Ein bot in einer Gruppe oder einem Kanal sollte Informationen enthalten, die für alle Mitglieder relevant und angemessen sind. Während Ihr bot sicherlich alle Informationen zur Verfügung stellen kann, die für die Benutzeroberfläche relevant sind, sollten Sie berücksichtigen, dass die Unterhaltungen für alle sichtbar sind. Ein großer bot in einer Gruppe oder einem Kanal sollte daher allen Benutzern einen Mehrwert geben und sicherlich nicht versehentlich Informationen in einer 1:1-Unterhaltung besser austauschen.

Ihr bot ist möglicherweise vollständig relevant in allen Bereichen, und es ist keine nennenswerte zusätzliche Arbeit erforderlich, damit Ihr bot über diese hinweg arbeiten kann. In Microsoft Teams wird nicht davon ausgegangen, dass Ihre bot-Funktion in allen Bereichen, aber Sie sollten sicherstellen, dass Ihr bot Benutzerwert in welchem Bereich (n), die Sie zur Unterstützung bereitstellt. Weitere Informationen zu Bereichen finden Sie unter [apps in Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md).

Die Entwicklung eines bot, der in Gruppen oder Kanälen funktioniert, verwendet einen Großteil der gleichen Funktionalität aus persönlichen Unterhaltungen. Zusätzliche Ereignisse und Daten in der Nutzlast bieten Teams-Gruppen-und Kanalinformationen. Diese Unterschiede sowie wesentliche Unterschiede in der allgemeinen Funktionalität werden in den folgenden Abschnitten beschrieben.

### <a name="creating-messages"></a>Erstellen von Nachrichten

Weitere Informationen zu Bots zum Erstellen von Nachrichten in Kanälen finden Sie unter [proaktives Messaging für Bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md)und speziell [Erstellen einer Kanal Unterhaltung](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md#creating-a-channel-conversation).

### <a name="receiving-messages"></a>Empfangen von Nachrichten

Für einen bot in einer Gruppe oder einem Kanal erhält Ihr bot zusätzlich zum [regulären Nachrichtenschema](https://docs.botframework.com/core-concepts/reference/#activity)auch die folgenden Eigenschaften:

* `channelData`Weitere Informationen finden Sie unter [Teams-Kanaldaten](~/resources/bot-v3/bot-conversations/bots-conversations.md#teams-channel-data). In einem Gruppenchat enthält Informationen, die für diesen Chat spezifisch sind.
* `conversation.id`Die Antwortketten-ID, bestehend aus Kanal-ID und der ID der ersten Nachricht in der Antwort Kette
* `conversation.isGroup`Ist `true` für bot-Nachrichten in Kanälen oder Gruppenchats
* `conversation.conversationType`Entweder `groupChat` oder`channel`
* `entities`Kann ein oder mehrere Erwähnungen enthalten (siehe [Erwähnungen](#-mentions))

### <a name="replying-to-messages"></a>Antworten auf Nachrichten

Um auf eine vorhandene Nachricht zu antworten, rufen Sie [`ReplyToActivity`](/bot-framework/dotnet/bot-builder-dotnet-connector#send-a-reply) .net oder [`session.send`](/bot-framework/nodejs/bot-builder-nodejs-use-default-message-handler) Node.js auf. Das Robot Builder SDK verarbeitet alle Details.

Wenn Sie sich für die Verwendung der Rest-API entscheiden, können Sie auch den [`/conversations/{conversationId}/activities/{activityId}`](/bot-framework/rest-api/bot-framework-rest-connector-send-and-receive-messages#send-the-reply) Endpunkt aufrufen.

In einem Kanal wird eine Antwort auf eine Nachricht als Antwort auf die initiierende Antwort Kette angezeigt. Der `conversation.id` enthält den Kanal und die Nachrichten-ID der obersten Ebene. Obwohl sich das bot-Framework um die Details kümmert, können Sie dieses `conversation.id` bei Bedarf für zukünftige Antworten auf diesen Gesprächs Thread Zwischenspeichern.

### <a name="best-practice-welcome-messages-in-teams"></a>Bewährte Methode: Willkommensnachrichten in Microsoft Teams

Wenn Ihr bot zum ersten Mal der Gruppe oder dem Team hinzugefügt wird, ist es generell sinnvoll, eine Willkommensnachricht zu senden, die den bot allen Benutzern vorstellt. Die Willkommensnachricht sollte eine Beschreibung der Funktionen und Benutzer Vorteile des bot enthalten. Im Idealfall sollte die Nachricht auch Befehle enthalten, damit der Benutzer mit der APP interagieren können. Stellen Sie dazu sicher, dass Ihr bot auf die `conversationUpdate` Nachricht reagiert, wobei der `teamsAddMembers` eventType im `channelData` Objekt ist. Stellen Sie sicher, dass die `memberAdded` ID die APP-ID des bot selbst ist, da dasselbe Ereignis gesendet wird, wenn ein Benutzer einem Team hinzugefügt wird. Weitere Informationen finden Sie unter [Team Mitglied oder bot-Erweiterung](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) .

Möglicherweise möchten Sie auch eine persönliche Nachricht an jedes Mitglied des Teams senden, wenn der bot hinzugefügt wird. Dazu können Sie [das Team-Dienstplan abrufen](~/resources/bot-v3/bots-context.md#fetching-the-team-roster) und jedem Benutzer eine [direkte Nachricht](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md)senden.

Es wird empfohlen, dass Ihr bot in den folgenden Situationen *keine* Willkommensnachricht sendet:

* Das Team ist groß (offensichtlich subjektiv, aber zum Beispiel größer als 100 Mitglieder). Ihr bot wird möglicherweise als "spammy" angesehen, und die Person, die Sie hinzugefügt hat, kann Beschwerden erhalten, es sei denn, Sie teilen dem Benutzer, der die Willkommensnachricht sieht, eindeutig den Wert Vorschlag Ihres bot mit.
* Ihr bot wird erstmals in einer Gruppe oder einem Kanal erwähnt (im Gegensatz zum ersten hinzufügen zu einem Team).
* Eine Gruppe oder ein Kanal wird umbenannt.
* Ein Teammitglied wird einer Gruppe oder einem Kanal hinzugefügt.

## <a name="-mentions"></a>@ Erwähnungen

Da Bots in einer Gruppe oder einem Kanal nur dann reagieren, wenn Sie in einer Nachricht erwähnt werden ("@_botname_"), enthält jede Nachricht, die von einem bot in einem Gruppenkanal empfangen wird, einen eigenen Namen, und Sie müssen sicherstellen, dass Ihre Nachrichten Analyse diese behandelt. Darüber hinaus können Bots andere Benutzer, die erwähnt werden, analysieren und Benutzer als Teil Ihrer Nachrichten erwähnen.

### <a name="retrieving-mentions"></a>Abrufen von Erwähnungen

Erwähnungen werden im `entities` Objekt in Payload zurückgegeben und enthalten sowohl die eindeutige ID des Benutzers als auch in den meisten Fällen den Namen des erwähnten Benutzers. Sie können alle Erwähnungen in der Nachricht abrufen, indem Sie die `GetMentions` Funktion im bot Builder SDK für .net aufrufen, wodurch ein Array von Objekten zurückgegeben wird `Mentioned` .

#### <a name="net-example-code-check-for-and-strip-bot-mention"></a>.NET-Beispielcode: überprüfen und entfernen @bot Erwähnung

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
> Sie können auch die Microsoft Teams-Erweiterungsfunktion verwenden `GetTextWithoutMentions` , die alle Erwähnungen, einschließlich des bot, abstreift.

#### <a name="nodejs-example-code-check-for-and-strip-bot-mention"></a>Node.js Beispielcode: überprüfen und entfernen @bot Erwähnung

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

Sie können auch die Microsoft Teams-Erweiterungsfunktion verwenden `getTextWithoutMentions` , die alle Erwähnungen, einschließlich des bot, abstreift.

### <a name="constructing-mentions"></a>Erstellen von Erwähnungen

Ihr Bot kann andere Benutzer in Nachrichten erwähnen, die in Kanälen gepostet wurden. Hierzu muss Ihre Nachricht folgendermaßen vorgehen:

* `<at>@username</at>`In den Nachrichtentext einbeziehen
* Einschließen des `mention` Objekts in die Entities-Auflistung

#### <a name="net-example"></a>.NET-Beispiel

In diesem Beispiel wird das [Microsoft. bot. Connector. Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) -NuGet-Paket verwendet.

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

#### <a name="example-outgoing-message-with-user-mentioned"></a>Beispiel: ausgehende Nachricht mit erwähntem Benutzer

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

Ihr Bot kann mehr als senden und empfangen von Nachrichten in Gruppen und Teams. Beispielsweise kann es auch die Liste der Mitglieder, einschließlich ihrer Profilinformationen, sowie die Liste der Kanäle abrufen. Weitere Informationen finden Sie unter [Kontext für Ihren Microsoft Teams-bot abrufen](~/resources/bot-v3/bots-context.md) .

*Siehe auch* [bot Framework-Beispiele](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).
