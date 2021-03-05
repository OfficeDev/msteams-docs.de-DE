---
title: Grundlagen zu Unterhaltungen
description: Beschreibt Möglichkeiten für eine Unterhaltung mit einem Microsoft Teams-Bot
ms.topic: overview
ms.author: anclear
keyword: conversations basics receive message send message picture message channel data adaptive cards
ms.openlocfilehash: 4eba22e9b29f5378dc03480ba5f6ba421f816eb3
ms.sourcegitcommit: 5cb3453e918bec1173899e7591b48a48113cf8f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2021
ms.locfileid: "50449507"
---
# <a name="conversation-basics"></a>Grundlagen zu Unterhaltungen

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Eine Unterhaltung ist eine Reihe von Nachrichten, die zwischen Ihrem Bot und einem oder mehreren Benutzern gesendet werden. Es gibt drei Arten von Unterhaltungen, die auch als Bereiche in Teams bezeichnet werden:

| Unterhaltungstyp | Beschreibung |
| ------- | ----------- |
|  `teams` | Wird auch als Kanalunterhaltungen bezeichnet, die für alle Mitglieder des Kanals sichtbar sind. |
| `personal` | Unterhaltungen zwischen Bots und einem einzelnen Benutzer. |
| `groupChat` | Chatten zwischen einem Bot und zwei oder mehr Benutzern. Aktiviert ihren Bot auch in Besprechungschats. |

Ein Bot verhält sich je nach Art der Unterhaltung etwas anders:

* Bots in Kanal- und Gruppenchatunterhaltungen erfordern, dass der Benutzer den Bot @ erwähnt, um ihn in einem Kanal aufgerufen zu haben.
* Bots in einer 1:1-Unterhaltung erfordern keine @-Erwähnung. Alle nachrichten, die vom Benutzer gesendet werden, werden an Ihren Bot gesendet.

Um Ihren Bot in einem bestimmten Bereich zu aktivieren, fügen Sie diesen Bereich ihrem [App-Manifest hinzu.](~/resources/schema/manifest-schema.md)

## <a name="activities"></a>Aktivitäten

Jede Nachricht ist ein `Activity`-Objekt vom Typ `messageType: message`. Wenn ein Benutzer eine Nachricht sendet, postet Teams die Nachricht auf Ihrem Bot. Spezifisch erfolgt dies durch Senden eines JSON-Objekts an den Nachrichtenendpunkt des Bots. Ihr Bot untersucht die Nachricht, um ihren Typ zu bestimmen, und antwortet entsprechend.

Grundlegende Unterhaltungen werden über den Bot Framework Connector, eine einzelne REST-API, behandelt. Mit dieser API kann Ihr Bot mit Teams und anderen Kanälen kommunizieren. Das Bot Builder SDK bietet einfachen Zugriff auf diese API, zusätzliche Funktionen zum Verwalten des Unterhaltungsflusses und -zustands sowie einfache Möglichkeiten, kognitive Dienste wie die Verarbeitung natürlicher Sprachen (Natural Language Processing, NLP) zu integrieren.

## <a name="receive-a-message"></a>Empfangen einer Nachricht

Um eine Textnachricht zu empfangen, verwenden Sie die `Text`-Eigenschaft des `Activity`-Objekts. Verwenden Sie im Aktivitäts-Handler des Bots die `Activity` des Turn-Kontextobjekts, um eine einzelne Nachrichtenanforderung zu lesen.

Im folgenden Code ist ein Beispiel dargestellt:

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  await turnContext.SendActivityAsync(MessageFactory.Text($"Echo: {turnContext.Activity.Text}"), cancellationToken);
}

```

# <a name="typescriptnodejs"></a>[TypeScript/Node.js](#tab/typescript)

```typescript

export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onMessage(async (context, next) => {
            await context.sendActivity(`Echo: '${context.activity.text}'`);
            await next();
        });
    }
}

```

# <a name="python"></a>[Python](#tab/python)

<!-- Verify -->
```python

async def on_message_activity(self, turn_context: TurnContext):
    return await turn_context.send_activity(MessageFactory.text(f"Echo: {turn_context.activity.text}"))

```

# <a name="json"></a>[Json](#tab/json)

```json
{
    "type": "message",
    "id": "1485983408511",
    "timestamp": "2017-02-01T21:10:07.437Z",
    "localTimestamp": "2017-02-01T14:10:07.437-07:00",
    "serviceUrl": "https://smba.trafficmanager.net/amer/",
    "channelId": "msteams",
    "from": {
        "id": "29:1XJKJMvc5GBtc2JwZq0oj8tHZmzrQgFmB39ATiQWA85gQtHieVkKilBZ9XHoq9j7Zaqt7CZ-NJWi7me2kHTL3Bw",
        "name": "Megan Bowen",
        "aadObjectId": "7faf8ab2-3d56-4244-b585-20c8a42ed2b8"
    },
    "conversation": {
        "conversationType": "personal",
        "id": "a:17I0kl9EkpE1O9PH5TWrzrLNwnWWcfrU7QZjKR0WSfOpzbfcAg2IaydGElSo10tVr4C7Fc6GtieTJX663WuJCc1uA83n4CSrHSgGBj5XNYLcVlJAs2ZX8DbYBPck201w-"
    },
    "recipient": {
        "id": "28:c9e8c047-2a74-40a2-b28a-b162d5f5327c",
        "name": "Teams TestBot"
    },
    "textFormat": "plain",
    "text": "Hello Teams TestBot",
    "entities": [
      { 
        "locale": "en-US",
        "country": "US",
        "platform": "Windows",
        "timezone": "America/Los_Angeles",
        "type": "clientInfo"
      }
    ],
    "channelData": {
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    },
    "locale": "en-US"
}
```

---

## <a name="send-a-message"></a>Senden einer Nachricht

Um eine Textnachricht zu senden, geben Sie die Zeichenfolge an, die Sie als Aktivität senden möchten. Verwenden Sie im Aktivitätshandler des Bots die Methode des Turn-Kontextobjekts, `SendActivityAsync` um eine einzelne Nachrichtenantwort zu senden. Verwenden Sie die Methode des `SendActivitiesAsync` Objekts, um mehrere Antworten gleichzeitig zu senden. Der folgende Code zeigt ein Beispiel für das Senden einer Nachricht, wenn jemand zu einer Unterhaltung hinzugefügt wird.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task OnMembersAddedAsync(IList<ChannelAccount> membersAdded, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
  await turnContext.SendActivityAsync(MessageFactory.Text($"Hello and welcome!"), cancellationToken);
}

```

# <a name="typescriptnodejs"></a>[TypeScript/Node.js](#tab/typescript)

```typescript

export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onMessage(async (context, next) => {
            await context.sendActivity('Hello and welcome!');
            await next();
        });
    }
}
```

# <a name="python"></a>[Python](#tab/python)

<!-- Verify -->

```python

async def on_members_added_activity(
    self, members_added: [ChannelAccount], turn_context: TurnContext
):
    for member in teams_members_added:
        await turn_context.send_activity(f"Welcome your new team member {member.id}")
    return

```

# <a name="json"></a>[Json](#tab/json)

```json
{
    "text": "hi",
    "textFormat": "plain",
    "type": "message",
    "timestamp": "2019-10-31T20:57:27.2347285Z",
    "localTimestamp": "2019-10-31T13:57:27.2347285-07:00",
    "id": "1572555447214",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer/",
    "from": {
        "id": "29:1Xv-kvy4dKirR0rZfSF_kAVUzotoT1SXuEzkC9XGkuZng8YBw8qyu5uh4128fQRjlGgvEiRLx-0XP4KYMwcgdZw",
        "name": "Jane Doe",
        "aadObjectId": "df486eae-88fd-42a5-b45e-c581588186db"
    },
    "conversation": {
        "conversationType": "personal",
        "tenantId": "72f988bf-86f1-41af-91ab-2d7cd011db47",
        "id": "a:1oAmWTVBBe9E0JrpGxauqNyx4CCE_iQf2ZuWon9D42722Fon3wYIpbhgbRChE3wgVS1Gwl9zS1pZy4FSu6-x1vGEq5KBQK-EbBgyPyeP_C-lbLBY3vxnGk9m9D_282jbg"
    },
    "recipient": {
        "id": "28:5baea8d1-d4ea-43a1-b101-882f4c8d9cb4",
        "name": "Imported Bot"
    },
    "entities": [
        {
            "locale": "en-US",
            "country": "US",
            "platform": "Windows",
            "type": "clientInfo"
        }
    ],
    "channelData": {
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    },
    "locale": "en-US"
}
```

---

> [!NOTE]
> Die Nachrichtenaufteilung erfolgt, wenn eine Textnachricht und eine Anlage in derselben Aktivitätsnutzlast gesendet werden. Diese Aktivität wird von Microsoft Teams in separate Aktivitäten aufgeteilt, eine Aktivität mit nur einer Textnachricht und die andere mit einer Anlage. Wenn die Aktivität geteilt wird, erhalten Sie nicht die Nachrichten-ID als Antwort, die verwendet wird, um die Nachricht proaktiv zu aktualisieren oder zu löschen. [](~/bots/how-to/update-and-delete-bot-messages.md) Es wird empfohlen, separate Aktivitäten zu senden, anstatt je nach Nachrichtenteilung.

## <a name="teams-channel-data"></a>Teams-Kanaldaten

Das `channelData` Objekt enthält Teams-spezifische Informationen und ist eine definitive Quelle für Team- und Kanal-IDs. Möglicherweise müssen Sie diese IDs zwischenspeichern und als Schlüssel für den lokalen Speicher verwenden. Im SDK werden in der Regel wichtige Informationen aus dem Objekt herausgezieht, um `TeamsActivityHandler` den Zugriff auf das Objekt zu `channelData` erreichen. Sie können jedoch immer über das Objekt auf die ursprünglichen Daten `turnContext` zugreifen.

Das Objekt ist nicht in Nachrichten in persönlichen Unterhaltungen enthalten, da `channelData` diese außerhalb eines Kanals stattfinden.

Ein typisches channelData-Objekt in einer Aktivität, die an Ihren Bot gesendet wird, enthält die folgenden Informationen:

* `eventType`#A0 nur bei [Kanaländerungsereignissen übergeben.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
* `tenant.id` Azure Active Directory-Mandanten-ID, die in allen Kontexten übergeben wird.
* `team` Wird nur in Kanalkontexten übergeben, nicht in persönlichen Chats.
  * `id` GUID für den Kanal.
  * `name`Name des Teams; nur bei [Teambenennungsereignissen übergeben.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
* `channel` Wird nur in Kanalkontexten übergeben, wenn der Bot erwähnt wird, oder für Ereignisse in Kanälen in Teams, in denen der Bot hinzugefügt wurde.
  * `id` GUID für den Kanal.
  * `name`Kanalname; nur bei [Kanaländerungsereignissen übergeben.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
* `channelData.teamsTeamId` Veraltet. Diese Eigenschaft ist nur aus Abwärtskompatibilität enthalten.
* `channelData.teamsChannelId` Veraltet. Diese Eigenschaft ist nur aus Abwärtskompatibilität enthalten.

### <a name="example-channeldata-object-channelcreated-event"></a>Beispiel-channelData-Objekt (channelCreated-Ereignis)

```json
"channelData": {
    "eventType": "channelCreated",
    "tenant": {
        "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
    },
    "channel": {
        "id": "19:693ecdb923ac4458a5c23661b505fc84@thread.skype",
        "name": "My New Channel"
    },
    "team": {
        "id": "19:693ecdb923ac4458a5c23661b505fc84@thread.skype"
    }
}
```

## <a name="message-content"></a>Nachrichteninhalt

Ihr Bot kann Rich-Text, Bilder und Karten senden. Benutzer können Rich-Text und Bilder an Ihren Bot senden.

| Format    | Vom Benutzer zum Bot | Vom Bot zum Benutzer | Anmerkungen                                                                                   |
|-----------|------------------|------------------|-----------------------------------------------------------------------------------------|
| Rich-Text  | ✔                | ✔                |                                                                                         |
| Bilder  | ✔                | ✔                | Maximal 1024×1024 und 1 MB im PNG-, JPEG- oder GIF-Format; animierte GIF werden nicht unterstützt  |
| Karten     | ✖                | ✔                | Informationen zu unterstützten Karten finden Sie in [der Teams-Kartenreferenz](~/task-modules-and-cards/cards/cards-reference.md) |
| Emojis    | ✖                | ✔                | Teams unterstützt derzeit Emojis über UTF-16 (z. B. U+1F600 für schmunzelende Gesichter)          |

## <a name="adding-notifications-to-your-message"></a>Hinzufügen von Benachrichtigungen zu Ihrer Nachricht

Benachrichtigungen warnen Benutzer über neue Aufgaben, Erwähnungen und Kommentare im Zusammenhang mit dem, wofür sie arbeiten oder die sie betrachten müssen, indem sie einen Hinweis in ihren Aktivitätsfeed einfügen. Sie können festlegen, dass Benachrichtigungen aus Ihrer Botnachricht ausgelöst werden, indem Sie die `TeamsChannelData` `Notification.Alert` Objects-Eigenschaft auf true festlegen. Ob eine Benachrichtigung ausgelöst wird, hängt letztlich von den Teams-Einstellungen des einzelnen Benutzers ab, und Sie können diese Einstellungen nicht programmgesteuert außer Kraft setzen. Der Typ der Benachrichtigung ist entweder ein Banner oder ein Banner und eine E-Mail.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  var message = MessageFactory.Text("You'll get a notification, if you've turned them on.");
  message.TeamsNotifyUser();

  await turnContext.SendActivityAsync(message);
}
```

# <a name="typescriptnodejs"></a>[TypeScript/Node.js](#tab/typescript)

```typescript
this.onMessage(async (turnContext, next) => {
    let message = MessageFactory.text("You'll get a notification, if you've turned them on.");
    teamsNotifyUser(message);

    await turnContext.sendActivity(message);

    // By calling next() you ensure that the next BotHandler is run.
    await next();
});
```

# <a name="python"></a>[Python](#tab/python)

```python

async def on_message_activity(self, turn_context: TurnContext):
    message = MessageFactory.text("You'll get a notification, if you've turned them on.")
    teams_notify_user(message)

    await turn_context.send_activity(message)

```

# <a name="json"></a>[Json](#tab/json)

```json
{
  "type": "message",
  "timestamp": "2017-04-24T21:46:00.9663655Z",
  "localTimestamp": "2017-04-24T14:46:00.9663655-07:00",
  "serviceUrl": "https://callback.com",
  "channelId": "msteams",
  "from": {
    "id": "28:e4fda94a-4b80-40eb-9bf0-6314491bc793",
    "name": "The bot"
  },
  "conversation": {
    "id": "a:1pL6i0oY3C0K8oAj8"
  },
  "recipient": {
    "id": "29:1rsVJmSSFMScF0YFyCXpvNWlo",
    "name": "User"
  },
  "text": "John Phillips assigned you a weekly todo",
  "summary": "Don't forget to meet with Marketing next week",
  "channelData": {
    "notification": {
      "alert": true
    }
  },
  "replyToId": "1493070356924"
}
```

---

## <a name="picture-messages"></a>Bildnachrichten

Bilder werden durch Hinzufügen von Anlagen zu einer Nachricht gesendet. Weitere Informationen zu Anlagen finden Sie in der [Bot Framework-Dokumentation](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments).

Bilder können im PNG-, JPEG- oder GIF-Format mindestens 1024×1024 und 1 MB groß sein. Animierte GIF wird nicht unterstützt.

Geben Sie die Höhe und Breite jedes Bilds immer mithilfe von XML an. In Markdown ist die Bildgröße standardmäßig auf 256×256 festgelegt. Beispiel:

* Verwenden – `<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>`
* Nicht verwenden – `![Duck on a rock](http://aka.ms/Fo983c)`

## <a name="adaptive-cards"></a>Adaptive Karten

Verwenden Sie den folgenden Code, um eine einfache adaptive Karte zu senden:

```json
{
    "type": "AdaptiveCard",
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.5",
    "body": [
    {
        "items": [
        {
            "size": "large",
            "text": " Simple Adaptivecard Example with a Textbox",
            "type": "TextBlock",
            "weight": "bolder",
            "wrap": true
        },
        ],
        "spacing": "extraLarge",
        "type": "Container",
        "verticalContentAlignment": "center"
    }
    ]
}
```

Weitere Informationen zu Karten und Karten in Bots finden Sie in [der Kartendokumentation](~/task-modules-and-cards/what-are-cards.md).

## <a name="code-sample"></a>Codebeispiel

|**Beispielname** | **Beschreibung** | **. NETCore** | **JavaScript** | **Python**|
|----------------|-----------------|--------------|----------------|-----------|
| Teams Conversation Bot | Nachrichten- und Unterhaltungsereignisbehandlung. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/57.teams-conversation-bot)| [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/57.teams-conversation-bot) |

## <a name="next-steps"></a>Nächste Schritte

* [Senden proaktiver Nachrichten](~/bots/how-to/conversations/send-proactive-messages.md)
* [Abonnieren von Unterhaltungsereignissen](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
