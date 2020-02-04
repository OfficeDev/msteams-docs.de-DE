---
title: Grundlagen der Unterhaltung
author: clearab
description: Vorgehensweise bei einer Unterhaltung mit einem Microsoft Teams-bot
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 2d241ad04509c596e97647138bab2a749fa0f74c
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674225"
---
# <a name="conversation-basics"></a>Grundlagen der Unterhaltung

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Bei einer Unterhaltung handelt es sich um eine Reihe von Nachrichten, die zwischen Ihrem bot und einem oder mehreren Benutzern gesendet werden. Es gibt drei Arten von Unterhaltungen (auch als Bereiche bezeichnet) in Microsoft Teams:

* `teams`Wird auch als Kanal Unterhaltungen bezeichnet, die für alle Mitglieder des Kanals sichtbar sind.
* `personal`Unterhaltungen zwischen Bots und einem einzelnen Benutzer.
* `groupChat`Chat zwischen einem bot und zwei oder mehr Benutzern. Aktiviert ihren bot auch in Besprechungs Chats.

Ein bot verhält sich je nach Art der Unterhaltung, in der er beteiligt ist, etwas anders:

* Bots in Kanal-und Gruppenchat Unterhaltungen erfordern, dass der Benutzer @ den bot erwähnt, um ihn in einem Kanal aufzurufen.
* Bots in einer 1:1-Unterhaltung benötigen keine @ mention. Alle Nachrichten, die vom Benutzer gesendet werden, werden an Ihren bot weitergeleitet.

Um Ihren bot in einem bestimmten Bereich zu aktivieren, fügen Sie diesen Bereich Ihrem [App-Manifest](~/resources/schema/manifest-schema.md)hinzu.

## <a name="activities"></a>Aktivitäten

Jede Nachricht ist ein `Activity` Objekt vom Typ `messageType: message`. Wenn ein Benutzer eine Nachricht sendet, stellt Microsoft Teams die Nachricht an Ihren bot. insbesondere wird ein JSON-Objekt an den Messaging Endpunkt Ihres bot gesendet. Ihr bot überprüft die Nachricht, um den Typ zu bestimmen, und antwortet dementsprechend.

Grundlegende Unterhaltungen werden über den bot-Framework-Konnektor behandelt, eine einzelne Rest-API, mit der ihr bot mit Teams und anderen Kanälen kommunizieren kann. Das bot-Generator-SDK bietet einfachen Zugriff auf diese API, zusätzliche Funktionen zum Verwalten des Unterhaltungs Flusses und-Zustands sowie einfache Methoden zum Integrieren von kognitiven Diensten wie etwa die Natural Language Processing (NLP).

## <a name="receive-a-message"></a>Empfangen einer Nachricht

Verwenden Sie die `Text` -Eigenschaft des- `Activity` Objekts, um eine Textnachricht zu erhalten. Verwenden Sie im Aktivitäts Handler des bot-Objekts das Turn-Kontext `Activity` Objekt, um eine einzelne Nachrichtenanforderung zu lesen.

Der folgende Code zeigt ein Beispiel.

# <a name="cnettabdotnet"></a>[C#-/.net](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  await turnContext.SendActivityAsync(MessageFactory.Text($"Echo: {turnContext.Activity.Text}"), cancellationToken);
}

```

# <a name="typescriptnodejstabtypescript"></a>[Manuskript/Node. js](#tab/typescript)

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

# <a name="pythontabpython"></a>[Python](#tab/python)

<!-- Verify -->
```python

async def on_message_activity(self, turn_context: TurnContext):
    return await turn_context.send_activity(MessageFactory.text(f"Echo: {turn_context.activity.text}"))

```

# <a name="jsontabjson"></a>[Json](#tab/json)

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

Geben Sie zum Senden einer Textnachricht die Zeichenfolge an, die Sie als Aktivität senden möchten. Verwenden Sie in den Aktivitäts Handlern des bot die `SendActivityAsync` Methode zum Drehen des Kontextobjekts, um eine einzelne Nachrichten Antwort zu senden. Sie können auch die `SendActivitiesAsync` Methode des Objekts verwenden, um mehrere Antworten gleichzeitig zu senden. Der folgende Code zeigt ein Beispiel für das Senden einer Nachricht, wenn jemand einer Unterhaltung hinzugefügt wird.  

# <a name="cnettabdotnet"></a>[C#-/.net](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  await turnContext.SendActivityAsync(MessageFactory.Text($"Hello and welcome!"), cancellationToken);
}

```

# <a name="typescriptnodejstabtypescript"></a>[Manuskript/Node. js](#tab/typescript)

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

# <a name="pythontabpython"></a>[Python](#tab/python)

<!-- Verify -->

```python

async def on_members_added_activity(
    self, members_added: [ChannelAccount], turn_context: TurnContext
):
    for member in teams_members_added:
        await turn_context.send_activity(f"Welcome your new team member {member.id}")
    return

```

# <a name="jsontabjson"></a>[Json](#tab/json)

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

## <a name="teams-channel-data"></a>Teams-Kanaldaten

Das `channelData` Objekt enthält Teams-spezifische Informationen und ist die endgültige Quelle für Team-und Kanal-IDs. Sie müssen möglicherweise Zwischenspeichern und diese IDs als Schlüssel für den lokalen Speicher verwenden. `TeamsActivityHandler` Im SDK werden normalerweise wichtige Informationen aus dem `channelData` Objekt herausgezogen, damit es leichter zugänglich ist, Sie können jedoch jederzeit auf die ursprünglichen Informationen des `turnContext` Objekts zugreifen.

Das `channelData` Objekt wird nicht in Nachrichten in persönlichen Unterhaltungen eingeschlossen, da diese außerhalb eines Kanals stattfinden.

Ein typisches channelData-Objekt in einer an Ihren bot gesendeten Aktivität enthält die folgenden Informationen:

* `eventType`Teams-Ereignistyp; nur in Fällen von [Kanal Änderungsereignissen](~/bots/how-to/conversations/subscribe-to-conversation-events.md) übergeben
* `tenant.id`Azure Active Directory-Mandanten-ID; in allen Kontexten übergeben
* `team`Wird nur in Kanal Kontexten übergeben, nicht im persönlichen Chat.
  * `id`GUID für den Kanal
  * `name`Name des Teams; nur in Fällen von [Team Umbenennungs Ereignissen](~/bots/how-to/conversations/subscribe-to-conversation-events.md) übergeben
* `channel`Wird nur in Kanal Kontexten übergeben, wenn der bot erwähnt wird, oder für Ereignisse in Kanälen in Microsoft Teams, in denen der bot hinzugefügt wurde.
  * `id`GUID für den Kanal
  * `name`Kanal Name; nur in Fällen von [Kanal Änderungsereignissen](~/bots/how-to/conversations/subscribe-to-conversation-events.md)übergeben.
* `channelData.teamsTeamId`Veraltet. Diese Eigenschaft ist nur für die Abwärtskompatibilität enthalten.
* `channelData.teamsChannelId`Veraltet. Diese Eigenschaft ist nur für die Abwärtskompatibilität enthalten.

### <a name="example-channeldata-object-channelcreated-event"></a>Beispiel für ein channelData-Objekt (channelCreated-Ereignis)

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

Ihr Bot kann Rich-Text, Bilder und Karten senden. Benutzer können Rich-Text und Bilder an Ihren bot senden.

| Format    | Von Benutzer zu bot | Von bot zu Benutzer | Notes                                                                                   |
|-----------|------------------|------------------|-----------------------------------------------------------------------------------------|
| Rich-Text  | ✔                | ✔                |                                                                                         |
| Bilder  | ✔                | ✔                | Maximal 1024 × 1024 und 1 MB im PNG-, JPEG-oder GIF-Format; animierte GIF-Zeichen werden nicht unterstützt  |
| Karten     | ✖                | ✔                | Siehe die Microsoft [Teams-Karten Referenz](~/task-modules-and-cards/cards/cards-reference.md) für unterstützte Karten |
| Emojis    | ✖                | ✔                | Teams unterstützen derzeit Emojis über UTF-16 (wie U + 1F600 für grinsende Fläche)          |

## <a name="adding-notifications-to-your-message"></a>Hinzufügen von Benachrichtigungen zu Ihrer Nachricht

Benachrichtigungen benachrichtigen Benutzer über neue Aufgaben, Erwähnungen und Kommentare im Zusammenhang mit dem, woran Sie gerade arbeiten, oder müssen sich durch Einfügen eines Hinweises in ihren Aktivitäts Feed informieren. Sie können Benachrichtigungen so festlegen, dass Sie aus ihrer bot-Nachricht `TeamsChannelData` ausgelöst `Notification.Alert` werden, indem Sie die Objects-Eigenschaft auf true festlegen. Unabhängig davon, ob eine Benachrichtigung ausgelöst wird, hängt letztlich von den Microsoft Teams-Einstellungen des einzelnen Benutzers ab, und Sie können diese Einstellungen nicht programmgesteuert außer Kraft setzen. Der Typ der Benachrichtigung ist entweder ein Banner oder sowohl ein Banner als auch eine e-Mail.

# <a name="cnettabdotnet"></a>[C#-/.net](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  var message = MessageFactory.Text("You'll get a notification, if you've turned them on.");
  message.TeamsNotifyUser();

  await turnContext.SendActivityAsync(message);
}
```

# <a name="typescriptnodejstabtypescript"></a>[Manuskript/Node. js](#tab/typescript)

```typescript
this.onMessage(async (turnContext, next) => {
    let message = MessageFactory.text("You'll get a notification, if you've turned them on.");
    teamsNotifyUser(message);

    await turnContext.sendActivity(message);

    // By calling next() you ensure that the next BotHandler is run.
    await next();
});
```

# <a name="pythontabpython"></a>[Python](#tab/python)

```python

async def on_message_activity(self, turn_context: TurnContext):
    message = MessageFactory.text("You'll get a notification, if you've turned them on.")
    teams_notify_user(message)

    await turn_context.send_activity(message)

```

# <a name="jsontabjson"></a>[Json](#tab/json)

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

Bilder werden durch Hinzufügen von Anlagen zu einer Nachricht gesendet. Weitere Informationen zu Anlagen finden Sie in der [bot-Framework-Dokumentation](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments?view=azure-bot-service-3.0).

Bilder können im Format PNG, JPEG oder GIF maximal 1024 × 1024 und 1 MB sein; animierte GIF-Zeichen werden nicht unterstützt.

Es wird empfohlen, die Höhe und Breite jedes Bilds mithilfe von XML anzugeben. Wenn Sie den Abschlag verwenden, beträgt die Bildgröße standardmäßig 256 × 256. Zum Beispiel:

* Verwenden`<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>`
* Nicht verwenden-`![Duck on a rock](http://aka.ms/Fo983c)`

## <a name="next-steps"></a>Weitere Schritte

* [Senden proaktiver Nachrichten](~/bots/how-to/conversations/send-proactive-messages.md)
* [Abonnieren von unterhaltungsereignissen](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
