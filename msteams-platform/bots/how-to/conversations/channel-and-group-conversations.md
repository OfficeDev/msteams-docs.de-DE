---
title: Kanal- und Gruppenunterhaltungen
author: clearab
description: Vorgehensweise zum Senden, empfangen und Verarbeiten von Nachrichten für einen bot in einem Kanal-oder Gruppenchat.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: ccc27d7638820cfa3c2b7cfe12b91b3a3a9fef1d
ms.sourcegitcommit: 61c93b22490526b1de87c0b14a3c7eb6e046caf6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2020
ms.locfileid: "44801340"
---
# <a name="channel-and-group-chat-conversations-with-a-microsoft-teams-bot"></a>Kanal und Gruppenchatunterhaltungen mit einem Microsoft Teams-Bot

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Indem Sie den `teams` oder `groupchat` -Bereich zu Ihrem bot hinzufügen, kann er für die Installation in einem Team-oder Gruppenchat zur Verfügung stehen. Dadurch können alle Mitglieder der Unterhaltung mit Ihrem Bot interagieren. Sobald er installiert ist, hat er auch Zugriff auf Metadaten zu der Unterhaltung wie der Liste der Unterhaltungsmitglieder, und wenn er in einem Team installiert wurde, auf Details zu diesem Team sowie die vollständige Liste der Kanäle.

Bots in einer Gruppe oder einem Kanal empfangen nur Nachrichten, wenn Sie erwähnt werden ("@botname"), Sie erhalten keine weiteren Nachrichten, die an die Unterhaltung gesendet werden.

> [!NOTE]
> Der Bot muss direkt @erwähnt werden. Ihr bot erhält keine Nachricht, wenn das Team oder der Kanal erwähnt wird oder wenn jemand auf eine Nachricht von Ihrem bot antwortet, ohne Sie zu @mentioning.

## <a name="design-considerations"></a>Überlegungen zum Entwurf

Ein bot sollte Informationen bereitstellen, die für alle Mitglieder in einer Gruppe oder einem Kanal geeignet und relevant sind. Unterhaltungen mit dieser sind für alle sichtbar, die Teil der Gruppe oder des Kanals sind. Ein gut konzipierter bot kann allen Benutzern einen Mehrwert geben, ohne versehentlich Informationen freizugeben, die in einer 1:1-Unterhaltung besser geeignet sind. Multi-Turn-Unterhaltungen wie Dialoge sollten vermieden werden – verwenden Sie Karten und/oder Aufgaben Module, um stattdessen Informationen zu sammeln.

## <a name="creating-new-conversation-threads"></a>Erstellen neuer Unterhaltungs Threads

Wenn Ihr bot in einem Team installiert ist, kann es manchmal erforderlich sein, einen neuen Unterhaltungsthread zu erstellen, statt einem vorhandenen zu antworten. Dies ist eine Form von [proaktivem Messaging](~/bots/how-to/conversations/send-proactive-messages.md).

## <a name="working-with-mentions"></a>Arbeiten mit Erwähnungen

Jede Nachricht von einer Gruppe oder einem Kanal an Ihren Bot enthält eine „@Erwähnung“ mit seinem eigenen Namen im Nachrichtentext, weshalb Sie sicherstellen müssen, dass Ihre Nachrichtenanalyse dies verarbeitet. Der Bot kann auch andere in einer Nachricht erwähnte Benutzer abrufen und jeder von ihm gesendeten Nachricht Erwähnungen hinzufügen.

### <a name="stripping-mentions-from-message-text"></a>Entfernen von Erwähnungen aus dem Nachrichtentext

Möglicherweise halten Sie es für notwendig, die @Erwähnungen aus dem Text der Nachricht zu entfernen, die ihr Bot empfängt.

### <a name="retrieving-mentions"></a>Abrufen von Erwähnungen

Erwähnungen werden im `entities` Objekt in Payload zurückgegeben und enthalten sowohl die eindeutige ID des Benutzers als auch in den meisten Fällen den Namen des erwähnten Benutzers. Der Text der Nachricht enthält außerdem die Erwähnung ähnlich wie `<at>@John Smith<at>`. Sie sollten sich jedoch nicht darauf verlassen, dass der Text in der Nachricht alle Informationen zum Benutzer abruft. Es ist möglich, dass die Person, die die Nachricht sendet, Sie ändert. Verwenden Sie stattdessen das- `entities` Objekt.

Sie können alle Erwähnungen in der Nachricht abrufen, indem Sie die `GetMentions` Funktion im bot Builder SDK aufrufen, das ein Array von Objekten zurückgibt `Mention` .

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
    Mention[] mentions = turnContext.Activity.GetMentions();
    if(mentions != null)
    {
        ChannelAccount firstMention = mentions[0].Mentioned;
        await turnContext.SendActivityAsync($"Hello {firstMention.Name}");
    }
    else
    {
        await turnContext.SendActivityAsync("Aw, no one was mentioned.");
    }
}
```

# <a name="typescriptnodejs"></a>[TypeScript/Node.js](#tab/typescript)

```typescript
this.onMessage(async (turnContext, next) => {
    const mentions = TurnContext.getMentions(turnContext.activity);
    if (mentions){
        const firstMention = mentions[0].mentioned;
        await turnContext.sendActivity(`Hello ${firstMention.name}.`);
    } else {
        await turnContext.sendActivity(`Aw, no one was mentioned.`);
    }

    await next();
});
```

# <a name="json"></a>[Json](#tab/json)

```json
{
    "type": "message",
    "text": "Hey <at>Pranav Smith</at> check out this message",
    "timestamp": "2017-10-29T00:51:05.9908157Z",
    "localTimestamp": "2017-10-28T17:51:05.9908157-07:00",
    "serviceUrl": "https://skype.botframework.com",
    "channelId": "msteams",
    "from": {
        "id": "29:9e52142b-5e5e-4d7b-bb3e-e82dcf620000",
        "name": "Jane Smith"
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

# <a name="python"></a>[Python](#tab/python)

```python
@staticmethod
def get_mentions(activity: Activity) -> List[Mention]:
    result: List[Mention] = []
    if activity.entities is not None:
        for entity in activity.entities:
            if entity.type.lower() == "mention":
                    result.append(entity)
     return result
```

* * *

### <a name="adding-mentions-to-your-messages"></a>Hinzufügen von Erwähnungen zu ihren Nachrichten

Ihr Bot kann andere Benutzer in Nachrichten erwähnen, die in Kanälen gepostet wurden. Hierzu muss Ihre Nachricht folgendermaßen vorgehen:

Das `Mention` Objekt verfügt über zwei Eigenschaften, die Sie festlegen müssen:

* Einschließen von <at>@username</at> im Nachrichtentext
* Einschließen des mention-Objekts in die Entities-Auflistung

Das bot-Framework-SDK stellt Hilfsmethoden und-Objekte bereit, damit die Erwähnung einfacher gestaltet wird.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
    var mention = new Mention
    {
        Mentioned = turnContext.Activity.From,
        Text = $"<at>{XmlConvert.EncodeName(turnContext.Activity.From.Name)}</at>",
    };

    var replyActivity = MessageFactory.Text($"Hello {mention.Text}.");
    replyActivity.Entities = new List<Entity> { mention };

    await turnContext.SendActivityAsync(replyActivity, cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[TypeScript/Node.js](#tab/typescript)

```typescript
this.onMessage(async (turnContext, next) => {
    const mention = {
        mentioned: turnContext.activity.from,
        text: `<at>${ new TextEncoder().encode(turnContext.activity.from.name) }</at>`,
    } as Mention;

    const replyActivity = MessageFactory.text(`Hello ${mention.text}`);
    replyActivity.entities = [mention];

    await turnContext.sendActivity(replyActivity);

    // By calling next() you ensure that the next BotHandler is run.
    await next();
});
```

# <a name="json"></a>[Json](#tab/json)

Das `text` Feld im Objekt im `entities` Array muss *exakt* mit einem Teil des Nachrichtenfelds übereinstimmen `text` . Wenn dies nicht der Fall ist, wird die Erwähnung ignoriert.

```json
{
    "type": "message",
    "text": "Hey <at>Pranav Smith</at> check out this message",
    "timestamp": "2017-10-29T00:51:05.9908157Z",
    "localTimestamp": "2017-10-28T17:51:05.9908157-07:00",
    "serviceUrl": "https://skype.botframework.com",
    "channelId": "msteams",
    "from": {
        "id": "29:9e52142b-5e5e-4d7b-bb3e-e82dcf620000",
        "name": "Jane Smith"
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

# <a name="python"></a>[Python](#tab/python)

```python
async def _mention_activity(self, turn_context: TurnContext):
        mention = Mention(
            mentioned=turn_context.activity.from_property,
            text=f"<at>{turn_context.activity.from_property.name}</at>",
            type="mention"
        )

        reply_activity = MessageFactory.text(f"Hello {mention.text}")
        reply_activity.entities = [Mention().deserialize(mention.serialize())]
        await turn_context.send_activity(reply_activity)
```

* * *

## <a name="sending-a-message-on-installation"></a>Senden einer Nachricht bei der Installation

Wenn Ihr bot zum ersten Mal der Gruppe oder dem Team hinzugefügt wird, kann es hilfreich sein, eine Nachricht mit der Einführung zu senden. Die Nachricht sollte eine kurze Beschreibung der Funktionen des bot enthalten und deren Verwendung. Sie möchten das `conversationUpdate` Ereignis mit dem `teamMemberAdded` eventType abonnieren.  Da das Ereignis gesendet wird, wenn ein neues Teammitglied hinzugefügt wird, müssen Sie überprüfen, ob das hinzugefügte neue Mitglied der Bot ist. Weitere Informationen finden Sie unter [Senden einer Willkommensnachricht an ein neues Teammitglied](~/bots/how-to/conversations/send-proactive-messages.md) .

Möglicherweise möchten Sie auch eine persönliche Nachricht an jedes Mitglied des Teams senden, wenn der bot hinzugefügt wird. Dazu können Sie das Team-Dienstplan erhalten und jedem Benutzer eine direkte Nachricht senden.

Es wird nicht empfohlen, eine Nachricht in den folgenden Situationen zu senden:

* Das Team ist groß (offensichtlich subjektiv, aber zum Beispiel größer als 100 Mitglieder). Ihr bot wird möglicherweise als "spammy" angesehen, und die Person, die Sie hinzugefügt hat, kann Beschwerden erhalten, es sei denn, Sie teilen dem Benutzer, der die Willkommensnachricht sieht, eindeutig den Wert Vorschlag Ihres bot mit.
* Ihr bot wird erstmals in einer Gruppe oder einem Kanal erwähnt (im Gegensatz zum ersten hinzufügen zu einem Team).
* Eine Gruppe oder ein Kanal wird umbenannt.
* Ein Teammitglied wird einer Gruppe oder einem Kanal hinzugefügt.

## <a name="learn-more"></a>Weitere Informationen

Ihr bot hat Zugriff auf zusätzliche Informationen über den Gruppenchat oder das Team, in dem er installiert ist. Weitere APIs für Ihren bot finden Sie unter [Get Teams Context](~/bots/how-to/get-teams-context.md) .

Es gibt auch zusätzliche Ereignisse, die ihr bot abonnieren und auf die Sie Antworten können. Weitere Informationen finden Sie unter [Subscribe to Conversation Events](~/bots/how-to/conversations/subscribe-to-conversation-events.md) .

[!INCLUDE [sample](~/includes/bots/teams-bot-samples.md)]
