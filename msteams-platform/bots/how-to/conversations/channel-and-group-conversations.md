---
title: Kanal- und Gruppenunterhaltungen mit einem Bot
author: clearab
description: Senden, Empfangen und Behandeln von Nachrichten für einen Bot in einem Kanal- oder Gruppenchat.
ms.topic: conceptual
localization_priority: Normal
ms.author: anclear
ms.openlocfilehash: 2d7eece1fc74781456024f6dcb9414fefbadb8f4
ms.sourcegitcommit: d90c5dafea09e2893dea8da46ee49516bbaa04b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2021
ms.locfileid: "52075752"
---
# <a name="channel-and-group-chat-conversations-with-a-bot"></a>Kanal- und Gruppenchatunterhaltungen mit einem Bot

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Um den Microsoft Teams in einem Team- oder Gruppenchat zu installieren, fügen Sie dem Bot den Bereich oder `teams` `groupchat` den Bereich hinzu. Dadurch können alle Mitglieder der Unterhaltung mit Ihrem Bot interagieren. Nachdem der Bot installiert wurde, hat er Zugriff auf Metadaten zur Unterhaltung, z. B. auf die Liste der Unterhaltungsmitglieder. Wenn er in einem Team installiert ist, hat der Bot außerdem Zugriff auf Details zu diesem Team und die vollständige Liste der Kanäle.

Bots in einer Gruppe oder einem Kanal empfangen nur Nachrichten, wenn sie erwähnt `@botname` werden. Sie erhalten keine weiteren Nachrichten, die an die Unterhaltung gesendet werden.

> [!NOTE]
> Der Bot muss direkt `@mentioned` sein. Ihr Bot erhält keine Nachricht, wenn das Team oder der Kanal erwähnt wird oder wenn jemand auf eine Nachricht von Ihrem Bot antwortet, ohne @mentioning senden.

## <a name="design-guidelines"></a>Richtlinien für den Entwurf

Im Gegensatz zu persönlichen Chats muss Ihr Bot in Gruppenchats und Kanälen eine schnelle Einführung bereitstellen. Sie müssen diese und weitere Richtlinien für das Botdesign befolgen. Weitere Informationen zum Entwerfen von Bots in Teams finden Sie unter Entwerfen von Botunterhaltungen [in Kanälen und Chats.](~/bots/design/bots.md)

Jetzt können Sie neue Unterhaltungsthreads erstellen und problemlos verschiedene Unterhaltungen in Kanälen verwalten.

## <a name="create-new-conversation-threads"></a>Erstellen neuer Unterhaltungsthreads

Wenn Ihr Bot in einem Team installiert ist, müssen Sie einen neuen Unterhaltungsthread erstellen, anstatt auf einen vorhandenen zu antworten. Manchmal ist es schwierig, zwischen zwei Unterhaltungen zu unterscheiden. Wenn die Unterhaltung threaded ist, ist es einfacher, verschiedene Unterhaltungen in Kanälen zu organisieren und zu verwalten. Dies ist eine Form von [proaktivem Messaging.](~/bots/how-to/conversations/send-proactive-messages.md)

Als Nächstes können Sie Erwähnungen mithilfe des Objekts abrufen und Ihren Nachrichten Erwähnungen `entities` hinzufügen, indem Sie das Objekt `Mention` verwenden.

## <a name="work-with-mentions"></a>Arbeiten mit Erwähnungen

Jede Nachricht an Ihren Bot aus einer Gruppe oder einem Kanal enthält eine @mention deren Name im Nachrichtentext enthalten ist. Stellen Sie sicher, dass die Nachrichten parsing @mention. Ihr Bot kann auch andere Benutzer abrufen, die in einer Nachricht erwähnt werden, und Allen nachrichten, die er sendet, Erwähnungen hinzufügen.

Sie müssen auch die @mentions aus dem Inhalt der Nachricht, die Ihr Bot empfängt, herausstreifen.

### <a name="retrieve-mentions"></a>Abrufen von Erwähnungen

Erwähnungen werden im Objekt in nutzlast zurückgegeben und enthalten sowohl die eindeutige ID des Benutzers als auch den Namen `entities` des erwähnten Benutzers. Der Text der Nachricht enthält auch die Erwähnung, z. B. `<at>@John Smith<at>` . Verlassen Sie sich jedoch nicht auf den Text in der Nachricht, um Informationen über den Benutzer abzurufen. Die Person, die die Nachricht sendet, kann sie ändern. Verwenden Sie daher das `entities` Objekt.

Sie können alle Erwähnungen in der Nachricht abrufen, indem Sie die Funktion im Bot Builder SDK aufrufen, das `GetMentions` ein Array von Objekten `Mention` zurückgibt.

Der folgende Code zeigt ein Beispiel für das Abrufen von Erwähnungen:

# <a name="c"></a>[C#](#tab/dotnet)

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

# <a name="typescript"></a>[TypeScript](#tab/typescript)

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

### <a name="add-mentions-to-your-messages"></a>Hinzufügen von Erwähnungen zu Ihren Nachrichten

Ihr Bot kann andere Benutzer in Nachrichten erwähnen, die in Kanälen gepostet werden.

Das `Mention` Objekt verfügt über zwei Eigenschaften, die Sie mithilfe der folgenden Eigenschaften festlegen müssen:

* Fügen <at>@username</at> in den Nachrichtentext ein.
* Schließen Sie das Mention-Objekt in die Entitätssammlung ein.

Das Bot Framework SDK stellt Hilfsmethoden und Objekte zum Erstellen von Erwähnungen zur Verfügung.

Der folgende Code zeigt ein Beispiel für das Hinzufügen von Erwähnungen zu Ihren Nachrichten:

# <a name="c"></a>[C#](#tab/dotnet)

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

# <a name="typescript"></a>[TypeScript](#tab/typescript)

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

Das `text` Feld im Objekt im Array muss einem Teil des `entities` Nachrichtenfelds `text` entsprechen. Andern falls nicht, wird die Erwähnung ignoriert.

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

Jetzt können Sie eine Einführungsnachricht senden, wenn Ihr Bot zum ersten Mal installiert oder einer Gruppe oder einem Team hinzugefügt wird.

## <a name="send-a-message-on-installation"></a>Senden einer Nachricht bei der Installation

Wenn Ihr Bot zum ersten Mal der Gruppe oder dem Team hinzugefügt wird, muss eine Einführungsnachricht gesendet werden. Die Nachricht muss eine kurze Beschreibung der Funktionen des Bots und deren Verwendung enthalten. Sie müssen das Ereignis `conversationUpdate` mit dem `teamMemberAdded` eventType abonnieren.  Das Ereignis wird gesendet, wenn ein neues Teammitglied hinzugefügt wird. Überprüfen Sie, ob das hinzugefügte neue Mitglied der Bot ist. Weitere Informationen finden Sie unter [Senden einer Willkommensnachricht an ein neues Teammitglied](~/bots/how-to/conversations/send-proactive-messages.md).

Senden Sie eine persönliche Nachricht an jedes Teammitglied, wenn der Bot hinzugefügt wird. Dazu erhalten Sie die Teamliste, und senden Sie jedem Benutzer eine direkte Nachricht.

Senden Sie in den folgenden Fällen keine Nachricht:

* Das Team ist groß, z. B. größer als 100 Mitglieder. Ihr Bot kann als Spam gesehen werden, und die Person, die ihn hinzugefügt hat, kann Beschwerden erhalten. Sie müssen die Wertversprechung Ihres Bots jedem klar vermitteln, der die Willkommensnachricht sieht.
* Ihr Bot wird zuerst in einer Gruppe oder einem Kanal erwähnt, anstatt zuerst einem Team hinzugefügt zu werden.
* Eine Gruppe oder ein Kanal wird umbenannt.
* Ein Teammitglied wird einer Gruppe oder einem Kanal hinzugefügt.

[!INCLUDE [sample](~/includes/bots/teams-bot-samples.md)]

## <a name="see-also"></a>Siehe auch

[Get Teams context](~/bots/how-to/get-teams-context.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Abonnieren von Unterhaltungsereignissen](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
