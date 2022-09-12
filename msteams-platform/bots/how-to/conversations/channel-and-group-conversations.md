---
title: Erstellen von Unterhaltungs-Bots für Kanal- oder Gruppenchats
author: surbhigupta
description: Erfahren Sie, wie Sie Nachrichten für einen Bot in einem Kanal- oder Gruppenchat senden, empfangen und behandeln. Erfahren Sie mehr über Designrichtlinien und mehr.
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: anclear
ms.openlocfilehash: 91e696644698a609f6870aad9f4242e797b8e6bc
ms.sourcegitcommit: 2d48459e0cdf92c097954ecc785f0ea257d423b9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2022
ms.locfileid: "67646139"
---
# <a name="channel-and-group-chat-conversations-with-a-bot"></a>Kanal- und Gruppenchatunterhaltungen mit einem Bot

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Um den Microsoft Teams-Bot in einem Team- oder Gruppenchat zu installieren, fügen Sie den `teams` Oder-Bereich `groupchat` zu Ihrem Bot hinzu. Dadurch können alle Mitglieder der Unterhaltung mit Ihrem Bot interagieren. Nachdem der Bot installiert wurde, hat er Zugriff auf Metadaten zu der Unterhaltung, z. B. die Liste der Unterhaltungsmitglieder. Außerdem hat der Bot bei der Installation in einem Team Zugriff auf Details zu diesem Team und die vollständige Liste der Kanäle.

Bots in einer Gruppe oder einem Kanal empfangen Nachrichten nur, wenn sie @botname erwähnt werden. Sie erhalten keine anderen Nachrichten, die an die Unterhaltung gesendet werden. Der Bot muss direkt @erwähnt werden. Ihr Bot erhält keine Nachricht, wenn das Team oder der Kanal erwähnt wird oder wenn jemand auf eine Nachricht von Ihrem Bot antwortet, ohne sie @mentioning.

> [!NOTE]
> Dieses Feature ist derzeit nur in der [öffentlichen Entwicklervorschau](../../../resources/dev-preview/developer-preview-intro.md) verfügbar.
>
> Mithilfe der ressourcenspezifischen Zustimmung (Resource-Specific Consent, RSC) können Bots alle Kanalnachrichten in Teams empfangen, in denen sie installiert sind, ohne @mentioned zu werden. Weitere Informationen finden Sie unter ["Empfangen aller Kanalnachrichten mit RSC"](channel-messages-with-rsc.md).
>
> Das Veröffentlichen einer Nachricht oder adaptiven Karte in einem privaten Kanal wird derzeit nicht unterstützt.

Sehen Sie sich das folgende Video an, um mehr über Kanal- und Gruppenchatunterhaltungen mit einem Bot zu erfahren:
<br>

> [!VIDEO <https://www.microsoft.com/en-us/videoplayer/embed/RE4NzEs>]
<br>

## <a name="design-guidelines"></a>Richtlinien für den Entwurf

Im Gegensatz zu persönlichen Chats muss Ihr Bot in Gruppenchats und Kanälen eine kurze Einführung bereitstellen. Sie müssen diese und weitere Bot-Designrichtlinien befolgen. Weitere Informationen zum Entwerfen von Bots in Teams finden Sie unter [Entwerfen von Bot-Unterhaltungen in Kanälen und Chats](~/bots/design/bots.md).

Jetzt können Sie neue Unterhaltungsthreads erstellen und ganz einfach verschiedene Unterhaltungen in Kanälen verwalten.

## <a name="create-new-conversation-threads"></a>Erstellen neuer Unterhaltungsthreads

Wenn Ihr Bot in einem Team installiert ist, müssen Sie einen neuen Unterhaltungsthread erstellen, anstatt auf einen vorhandenen zu antworten. Manchmal ist es schwierig, zwischen zwei Unterhaltungen zu unterscheiden. Wenn die Unterhaltung threaded ist, ist es einfacher, verschiedene Unterhaltungen in Kanälen zu organisieren und zu verwalten. Dies ist eine Form von [proaktivem Messaging](~/bots/how-to/conversations/send-proactive-messages.md).

Als Nächstes können Sie Erwähnungen mithilfe des `entities` Objekts abrufen und Ihren Nachrichten Erwähnungen mithilfe des `Mention` Objekts hinzufügen.

## <a name="work-with-mentions"></a>Arbeiten mit Erwähnungen

Jede Nachricht von einer Gruppe oder einem Kanal an Ihren Bot enthält eine @mention mit ihrem Namen im Nachrichtentext. Ihr Bot kann auch andere Benutzer abrufen, die in einer Nachricht erwähnt werden, und allen von ihr gesendeten Nachrichten Erwähnungen hinzufügen.

Sie müssen auch die @mentions aus dem Inhalt der Nachricht entfernen, die Ihr Bot empfängt.

### <a name="retrieve-mentions"></a>Abrufen von Erwähnungen

Erwähnungen werden im Objekt in nutzlast `entities` zurückgegeben und enthalten sowohl die eindeutige ID des Benutzers als auch den Namen des erwähnten Benutzers. Der Text der Nachricht enthält auch die Erwähnung, z `<at>@John Smith<at>`. B. . Verlassen Sie sich jedoch nicht auf den Text in der Nachricht, um Informationen über den Benutzer abzurufen. Es ist möglich, dass die Person, die die Nachricht sendet, sie ändert. Verwenden Sie daher das `entities` Objekt.

Sie können alle Erwähnungen in der Nachricht abrufen, indem Sie die `GetMentions` Funktion im Bot Builder SDK aufrufen, die ein Array von `Mention` Objekten zurückgibt.

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

# <a name="json"></a>[JSON](#tab/json)

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

Ihr Bot kann andere Benutzer in Nachrichten erwähnen, die in Kanälen gepostet wurden.

Das `Mention` Objekt verfügt über zwei Eigenschaften, die Sie mit den folgenden Eigenschaften festlegen müssen:

* Fügen Sie *@username* in den Nachrichtentext ein.
* Schließen Sie das Erwähnungsobjekt in die Entitätenauflistung ein.

Das Bot Framework SDK stellt Hilfsmethoden und Objekte zum Erstellen von Erwähnungen bereit.

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

# <a name="json"></a>[JSON](#tab/json)

Das `text` Feld im Objekt im `entities` Array muss mit einem Teil des Nachrichtenfelds `text` übereinstimmen. Andernfalls wird die Erwähnung ignoriert.

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

Jetzt können Sie eine Einführungsnachricht senden, wenn Ihr Bot zum ersten Mal installiert oder zu einer Gruppe oder einem Team hinzugefügt wird.

## <a name="send-a-message-on-installation"></a>Senden einer Nachricht bei der Installation

Wenn Ihr Bot zum ersten Mal der Gruppe oder dem Team hinzugefügt wird, muss eine Einführungsnachricht gesendet werden. Die Nachricht muss eine kurze Beschreibung der Features des Bots und deren Verwendung enthalten. Sie müssen das `conversationUpdate` Ereignis mit eventType `teamMemberAdded` abonnieren.  Das Ereignis wird gesendet, wenn ein neues Teammitglied hinzugefügt wird. Überprüfen Sie, ob es sich bei dem hinzugefügten neuen Mitglied um den Bot handelt. Weitere Informationen finden Sie unter [Senden einer Willkommensnachricht an ein neues Teammitglied](~/bots/how-to/conversations/send-proactive-messages.md).

Sie können eine persönliche Nachricht an jedes Mitglied des Teams senden, wenn der Bot hinzugefügt wird. Rufen Sie dazu [die Teamliste](../../../resources/bot-v3/bots-context.md#fetch-the-team-roster) ab, und senden Sie jedem Benutzer eine [direkte Nachricht](../../../resources/bot-v3/bot-conversations/bots-conv-proactive.md).

>[!NOTE]
> Stellen Sie sicher, dass die vom Bot gesendete Nachricht relevant ist und der ursprünglichen Nachricht einen Mehrwert hinzufügt und die Benutzer nicht spammt.

Senden Sie in den folgenden Fällen keine Nachricht:

* Wenn das Team groß ist, z. B. größer als 100 Mitglieder. Ihr Bot kann als Spam angesehen werden, und die Person, die ihn hinzugefügt hat, kann Beschwerden erhalten. Sie müssen das Wertversprechen Ihres Bots klar an alle Personen kommunizieren, die die Willkommensnachricht sehen.
* Ihr Bot wird zuerst in einer Gruppe oder einem Kanal erwähnt, anstatt zuerst einem Team hinzugefügt zu werden.
* Eine Gruppe oder ein Kanal wird umbenannt.
* Ein Teammitglied wird einer Gruppe oder einem Kanal hinzugefügt.

[!INCLUDE [sample](~/includes/bots/teams-bot-samples.md)]

## <a name="step-by-step-guide"></a>Schrittweise Anleitung

Befolgen Sie die [schrittweise Anleitung](../../../sbs-teams-conversation-bot.yml) zum Erstellen eines Teams-Unterhaltungs-Bots.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Abonnieren von Unterhaltungsereignissen](~/bots/how-to/conversations/subscribe-to-conversation-events.md)

## <a name="see-also"></a>Siehe auch

* [Microsoft Teams-Kontext abrufen](~/bots/how-to/get-teams-context.md)
* [Erstellen eines privaten Kanals im Namen des Benutzers](/graph/api/channel-post#example-2-create-private-channel-on-behalf-of-user)
* [Verbinden eines Bots mit Webchat Kanal](/azure/bot-service/bot-service-channel-connect-webchat)
