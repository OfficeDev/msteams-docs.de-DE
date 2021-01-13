---
title: Kanal- und Gruppenunterhaltungen mit einem Bot
author: clearab
description: Senden, Empfangen und Behandeln von Nachrichten für einen Bot in einem Kanal- oder Gruppenchat.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 8a9a58208fff5cc2fe376fcb9932bad6ac2bf36f
ms.sourcegitcommit: 4539479289b43812eaae07a1c0f878bed815d2d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/12/2021
ms.locfileid: "49797841"
---
# <a name="channel-and-group-chat-conversations-with-a-microsoft-teams-bot"></a>Kanal- und Gruppenchatunterhaltungen mit einem Microsoft Teams-Bot

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Durch Hinzufügen des Bereichs oder des Bereichs zu Ihrem Bot kann er in einem Team- oder `teams` `groupchat` Gruppenchat installiert werden. Dadurch können alle Mitglieder der Unterhaltung mit Ihrem Bot interagieren. Sobald er installiert ist, hat er auch Zugriff auf Metadaten zu der Unterhaltung wie der Liste der Unterhaltungsmitglieder, und wenn er in einem Team installiert wurde, auf Details zu diesem Team sowie die vollständige Liste der Kanäle.

Bots in einer Gruppe oder einem Kanal empfangen nachrichten nur, wenn sie erwähnt werden (@botname), sie empfangen keine anderen Nachrichten, die an die Unterhaltung gesendet werden.

> [!NOTE]
> Der Bot muss direkt @erwähnt werden. Ihr Bot erhält keine Nachricht, wenn das Team oder der Kanal erwähnt wird oder wenn jemand auf eine Nachricht von Ihrem Bot antwortet, ohne @mentioning senden.

## <a name="design-guidelines"></a>Richtlinien für den Entwurf

Erfahren Sie, wie [Sie Botunterhaltungen in Kanälen und Chats entwerfen.](~/bots/design/bots.md)

## <a name="creating-new-conversation-threads"></a>Erstellen neuer Unterhaltungsthreads

Wenn Ihr Bot in einem Team installiert ist, kann es manchmal erforderlich sein, einen neuen Unterhaltungsthread zu erstellen, anstatt auf einen vorhandenen zu antworten. Dies ist eine Form von [proaktivem Messaging.](~/bots/how-to/conversations/send-proactive-messages.md)

## <a name="working-with-mentions"></a>Arbeiten mit Erwähnungen

Jede Nachricht von einer Gruppe oder einem Kanal an Ihren Bot enthält eine „@Erwähnung“ mit seinem eigenen Namen im Nachrichtentext, weshalb Sie sicherstellen müssen, dass Ihre Nachrichtenanalyse dies verarbeitet. Der Bot kann auch andere in einer Nachricht erwähnte Benutzer abrufen und jeder von ihm gesendeten Nachricht Erwähnungen hinzufügen.

### <a name="stripping-mentions-from-message-text"></a>Beschneiden von Erwähnungen aus dem Nachrichtentext

Möglicherweise halten Sie es für notwendig, die @Erwähnungen aus dem Text der Nachricht zu entfernen, die ihr Bot empfängt.

### <a name="retrieving-mentions"></a>Abrufen von Erwähnungen

Erwähnungen werden in der Nutzlast des Objekts zurückgegeben und enthalten sowohl die eindeutige ID des Benutzers als auch in den meisten Fällen den Namen `entities` des erwähnten Benutzers. Der Text der Nachricht enthält außerdem die Erwähnung ähnlich wie `<at>@John Smith<at>`. Sie sollten sich jedoch nicht auf den Text in der Nachricht verlassen, um Informationen über den Benutzer abzurufen. Die Person, die die Nachricht sendet, kann sie ändern. Verwenden Sie stattdessen das `entities` Objekt.

Sie können alle Erwähnungen in der Nachricht abrufen, indem Sie die Funktion im Bot Builder SDK aufrufen, die `GetMentions` ein Array von Objekten `Mention` zurückgibt.

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

### <a name="adding-mentions-to-your-messages"></a>Hinzufügen von Erwähnungen zu Ihren Nachrichten

Ihr Bot kann andere Benutzer in Nachrichten erwähnen, die in Kanälen gepostet werden. Dazu muss Ihre Nachricht folgendes tun:

Das `Mention` Objekt verfügt über zwei Eigenschaften, die Sie festlegen müssen:

* Schließen <at>@username</at> in den Nachrichtentext ein
* Schließen Sie das Erwähnungsobjekt in die Entitätensammlung ein.

Das Bot Framework SDK bietet Hilfsmethoden und Objekte, um die Erstellung der Erwähnung zu vereinfachen.

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

Das Feld im Objekt im Array muss genau mit einem Teil `text` `entities` des Nachrichtenfelds  `text` übereinstimmen. Andern falls nicht, wird die Erwähnung ignoriert.

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

Wenn Ihr Bot zum ersten Mal der Gruppe oder dem Team hinzugefügt wird, kann es hilfreich sein, eine Nachricht zu senden, die ihn einf?nist. Die Nachricht sollte eine kurze Beschreibung der Funktionen des Bots und deren Verwendung enthalten. Sie möchten das Ereignis mit dem `conversationUpdate` `teamMemberAdded` eventType abonnieren.  Da das Ereignis gesendet wird, wenn ein neues Teammitglied hinzugefügt wird, müssen Sie überprüfen, ob das neue hinzugefügte Mitglied der Bot ist. Weitere [Informationen finden Sie unter "Senden einer Willkommensnachricht an](~/bots/how-to/conversations/send-proactive-messages.md) ein neues Teammitglied".

Möglicherweise möchten Sie auch eine persönliche Nachricht an jedes Mitglied des Teams senden, wenn der Bot hinzugefügt wird. Dazu können Sie die Teamliste erhalten und jedem Benutzer eine direkte Nachricht senden.

Es wird nicht empfohlen, in den folgenden Situationen eine Nachricht zu senden:

* Das Team ist groß (natürlich subjektiv, aber z. B. größer als 100 Mitglieder). Ihr Bot wird möglicherweise als "Spammy" betrachtet, und die Person, die ihn hinzugefügt hat, kann Beanstandungen erhalten, es sei denn, Sie teilen das Wertversprechen Ihres Bots jedem klar mit, der die Willkommensnachricht sieht.
* Ihr Bot wird zuerst in einer Gruppe oder einem Kanal erwähnt (im Gegensatz zum ersten Hinzufügen zu einem Team)
* Eine Gruppe oder ein Kanal wird umbenannt
* Ein Teammitglied wird einer Gruppe oder einem Kanal hinzugefügt

## <a name="learn-more"></a>Weitere Informationen

Ihr Bot hat Zugriff auf zusätzliche Informationen über den Gruppenchat oder das Team, in dem er installiert ist. Weitere APIs, die für Ihren Bot verfügbar sind, finden Sie unter ["Teams-Kontext](~/bots/how-to/get-teams-context.md) erhalten".

Es gibt auch weitere Ereignisse, die Ihr Bot abonnieren und beantworten kann. Erfahren [Sie, wie Sie Unterhaltungsereignisse](~/bots/how-to/conversations/subscribe-to-conversation-events.md) abonnieren.

[!INCLUDE [sample](~/includes/bots/teams-bot-samples.md)]
