---
title: Meldungen in Bot-Unterhaltungen
description: Beschreibt Möglichkeiten für eine Unterhaltung mit einem Microsoft Teams-Bot
ms.topic: overview
ms.author: anclear
localization_priority: Normal
keyword: receive message send message picture message channel data adaptive cards
ms.openlocfilehash: 49e6af7ef71d0794210e554d8d8b42fe714fbe592d3ca7de43c7996283f54a2c
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2021
ms.locfileid: "57707550"
---
# <a name="messages-in-bot-conversations"></a>Meldungen in Bot-Unterhaltungen

Jede Nachricht in einer Unterhaltung ist ein `Activity` Objekt vom Typ `messageType: message` . Wenn ein Benutzer eine Nachricht sendet, sendet Teams die Nachricht an Ihren Bot. Teams sendet ein JSON-Objekt an den Messaging-Endpunkt Ihres Bots. Ihr Bot überprüft die Nachricht, um ihren Typ zu ermitteln, und antwortet entsprechend.

Grundlegende Unterhaltungen werden über den Bot Framework-Connector, eine einzelne REST-API, verarbeitet. Diese API ermöglicht Es Ihrem Bot, mit Teams und anderen Kanälen zu kommunizieren. Das Bot Builder SDK bietet die folgenden Features:

* Einfacher Zugriff auf den Bot Framework-Connector.
* Zusätzliche Funktionen zum Verwalten von Unterhaltungsfluss und -status.
* Einfache Möglichkeiten, kognitive Dienste wie die Verarbeitung natürlicher Sprache (Natural Language Processing, NLP) zu integrieren.

Ihr Bot empfängt Nachrichten von Teams mithilfe der `Text` Eigenschaft und sendet einzelne oder mehrere Nachrichtenantworten an die Benutzer.

## <a name="receive-a-message"></a>Empfangen einer Nachricht

Um eine Textnachricht zu empfangen, verwenden Sie die `Text`-Eigenschaft des `Activity`-Objekts. Verwenden Sie im Aktivitäts-Handler des Bots die `Activity` des Turn-Kontextobjekts, um eine einzelne Nachrichtenanforderung zu lesen.

Der folgende Code zeigt ein Beispiel für den Empfang einer Nachricht:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  await turnContext.SendActivityAsync(MessageFactory.Text($"Echo: {turnContext.Activity.Text}"), cancellationToken);
}

```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

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

# <a name="json"></a>[JSON](#tab/json)

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

Um eine Textnachricht zu senden, geben Sie die Zeichenfolge an, die Sie als Aktivität senden möchten. Verwenden Sie im Aktivitätshandler des Bots die Methode des Turn-Kontextobjekts, `SendActivityAsync` um eine einzelne Nachrichtenantwort zu senden. Verwenden Sie die Methode des `SendActivitiesAsync` Objekts, um mehrere Antworten gleichzeitig zu senden.

Der folgende Code zeigt ein Beispiel für das Senden einer Nachricht, wenn ein Benutzer zu einer Unterhaltung hinzugefügt wird:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
protected override async Task OnMembersAddedAsync(IList<ChannelAccount> membersAdded, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
  await turnContext.SendActivityAsync(MessageFactory.Text($"Hello and welcome!"), cancellationToken);
}

```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

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

# <a name="json"></a>[JSON](#tab/json)

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
> Das Teilen von Nachrichten erfolgt, wenn eine Textnachricht und eine Anlage in derselben Aktivitätsnutzlast gesendet werden. Diese Aktivität wird durch Microsoft Teams in separate Aktivitäten aufgeteilt, eines mit nur einer Textnachricht und das andere mit einer Anlage. Wenn die Aktivität geteilt ist, erhalten Sie nicht die Nachrichten-ID als Antwort, die verwendet wird, um die Nachricht proaktiv zu aktualisieren oder zu [löschen.](~/bots/how-to/update-and-delete-bot-messages.md) Es wird empfohlen, separate Aktivitäten zu senden, anstatt von der Nachrichtenteilung abhängig zu sein.

Nachrichten, die zwischen Benutzern und Bots gesendet werden, enthalten interne Kanaldaten innerhalb der Nachricht. Diese Daten ermöglichen es dem Bot, ordnungsgemäß in diesem Kanal zu kommunizieren. Mit dem Bot Builder SDK können Sie die Nachrichtenstruktur ändern.

## <a name="teams-channel-data"></a>Teams Kanaldaten

Das `channelData` Objekt enthält Teams-spezifische Informationen und ist eine endgültige Quelle für Team- und Kanal-IDs. Optional können Sie diese IDs als Schlüssel für den lokalen Speicher zwischenspeichern und verwenden. Im `TeamsActivityHandler` SDK werden wichtige Informationen aus dem Objekt `channelData` abgerufen, damit sie leicht zugänglich sind. Sie können jedoch immer auf die ursprünglichen Daten aus dem `turnContext` Objekt zugreifen.

Das `channelData` Objekt ist nicht in Nachrichten in persönlichen Unterhaltungen enthalten, da diese außerhalb eines Kanals stattfinden.

Ein `channelData` typisches Objekt in einer an Ihren Bot gesendeten Aktivität enthält die folgenden Informationen:

* `eventType`: Teams Ereignistyp, der nur bei [Kanaländerungsereignissen](~/bots/how-to/conversations/subscribe-to-conversation-events.md)übergeben wird.
* `tenant.id`: Azure Active Directory Mandanten-ID, die in allen Kontexten übergeben wird.
* `team`: Wird nur in Kanalkontexten übergeben, nicht im persönlichen Chat.
  * `id`: GUID für den Kanal.
  * `name`: Name des Teams, das nur bei [Team-Umbenennungsereignissen](~/bots/how-to/conversations/subscribe-to-conversation-events.md)übergeben wurde.
* `channel`: Wird nur in Kanalkontexten übergeben, wenn der Bot erwähnt wird, oder für Ereignisse in Kanälen in Teams, in denen der Bot hinzugefügt wurde.
  * `id`: GUID für den Kanal.
  * `name`: Kanalname wird nur in Fällen von [Kanaländerungsereignissen](~/bots/how-to/conversations/subscribe-to-conversation-events.md)übergeben.
* `channelData.teamsTeamId`: Veraltet. Diese Eigenschaft ist nur aus Gründen der Abwärtskompatibilität enthalten.
* `channelData.teamsChannelId`: Veraltet. Diese Eigenschaft ist nur aus Gründen der Abwärtskompatibilität enthalten.

### <a name="example-channeldata-object-or-channelcreated-event"></a>Beispiel für channelData-Objekt oder channelCreated-Ereignis

Der folgende Code zeigt ein Beispiel für ein channelData-Objekt:

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

Nachrichten, die von Ihrem Bot empfangen oder an diesen gesendet werden, können unterschiedliche Arten von Nachrichteninhalten enthalten.

## <a name="message-content"></a>Nachrichteninhalt

| Format    | Vom Benutzer zum Bot | Vom Bot zum Benutzer | Anmerkungen                                                                                   |
|-----------|------------------|------------------|-----------------------------------------------------------------------------------------|
| Rich-Text  | ✔                | ✔                | Ihr Bot kann Rich-Text, Bilder und Karten senden. Benutzer können Rich-Text und Bilder an Ihren Bot senden.                                                                                        |
| Bilder  | ✔                | ✔                | Maximal 1024×1024 und 1 MB im PNG-, JPEG- oder GIF-Format. Animierte GIF-Dateien werden nicht unterstützt.  |
| Karten     | ✖                | ✔                | In der [Teams Kartenreferenz](~/task-modules-and-cards/cards/cards-reference.md) finden Sie unterstützte Karten. |
| Emojis    | ✖                | ✔                | Teams unterstützt zurzeit Emojis über UTF-16, z. B. U+1F600 für graunendes Gesicht. |

Sie können Ihrer Nachricht auch mithilfe der Eigenschaft Benachrichtigungen `Notification.Alert` hinzufügen.

## <a name="notifications-to-your-message"></a>Benachrichtigungen an Ihre Nachricht

Benachrichtigungen informieren Benutzer über neue Aufgaben, Erwähnungen und Kommentare. Diese Warnungen beziehen sich darauf, worum es sich bei Benutzern handelt oder was sie sich ansehen müssen, indem sie einen Hinweis in ihren Aktivitätsfeed einfügen. Damit Benachrichtigungen von Ihrer Botnachricht ausgelöst werden, legen Sie die `TeamsChannelData` `Notification.Alert` Objekteigenschaft auf *"true"* fest. Ob eine Benachrichtigung ausgelöst wird, hängt von den Teams Einstellungen des einzelnen Benutzers ab, und Sie können diese Einstellungen nicht außer Kraft setzen. Der Benachrichtigungstyp ist entweder ein Banner oder sowohl ein Banner als auch eine E-Mail.

> [!NOTE]
> Im **Feld Zusammenfassung** wird beliebiger Text des Benutzers als Benachrichtigung im Feed angezeigt.

Der folgende Code zeigt ein Beispiel für das Hinzufügen von Benachrichtigungen zu Ihrer Nachricht:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  var message = MessageFactory.Text("You'll get a notification, if you've turned them on.");
  message.TeamsNotifyUser();

  await turnContext.SendActivityAsync(message);
}
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

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

# <a name="json"></a>[JSON](#tab/json)

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

Um Ihre Nachricht zu verbessern, können Sie Bilder als Anlagen zu dieser Nachricht einfügen.

## <a name="picture-messages"></a>Bildnachrichten

Bilder werden durch Hinzufügen von Anlagen zu einer Nachricht gesendet. Weitere Informationen zu Anlagen finden Sie in der [Bot Framework-Dokumentation.](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments)

Bilder können höchstens 1024×1024 und 1 MB im PNG-, JPEG- oder GIF-Format sein. Animierte GIF-Dateien werden nicht unterstützt.

Geben Sie die Höhe und Breite jedes Bilds mithilfe von XML an. In Markdown ist die Bildgröße standardmäßig 256×256. Beispiel:

* Verwenden Sie: `<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>` .
* Verwenden Sie nicht: `![Duck on a rock](http://aka.ms/Fo983c)` .

Ein Unterhaltungsbot kann adaptive Karten enthalten, die Geschäftsworkflows vereinfachen. Adaptive Karten bieten umfangreiche anpassbare Text-, Sprach-, Bild-, Schaltflächen- und Eingabefelder.

## <a name="adaptive-cards"></a>Adaptive Karten

Adaptive Karten können in einem Bot erstellt und in mehreren Apps wie Teams, Ihrer Website usw. angezeigt werden. Weitere Informationen finden Sie unter [Adaptive Karten.](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

Der folgende Code zeigt ein Beispiel für das Senden einer einfachen adaptiven Karte:

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

Weitere Informationen zu Karten und Karten in Bots finden Sie in der [Kartendokumentation.](~/task-modules-and-cards/what-are-cards.md)

## <a name="status-code-responses"></a>Statuscodeantworten

Nachfolgend sind die Statuscodes und deren Fehlercode sowie Meldungswerte aufgeführt:

| Statuscode | Fehlercode und Meldungswerte | Beschreibung |
|----------------|-----------------|-----------------|
| 403 | **Code:**`ConversationBlockedByUser` <br/> **Meldung:** Der Benutzer hat die Unterhaltung mit dem Bot blockiert. | Der Benutzer hat den Bot im 1:1-Chat oder einem Kanal über Moderationseinstellungen blockiert. |
| 403 | **Code:**`BotNotInConversationRoster` <br/> **Nachricht:** Der Bot ist nicht Teil der Unterhaltungsliste. | Der Bot ist nicht Teil der Unterhaltung. |
| 403 | **Code:**`BotDisabledByAdmin` <br/> **Meldung:** Der Mandantenadministrator hat diesen Bot deaktiviert. | Der Mandant hat den Bot blockiert. |
| 401 | **Code:**`BotNotRegistered` <br/> **Meldung:** Für diesen Bot wurde keine Registrierung gefunden. | Die Registrierung für diesen Bot wurde nicht gefunden. |
| 412 | **Code:**`PreconditionFailed` <br/> **Meldung:** Vorbedingung fehlgeschlagen, versuchen Sie es erneut. | Eine Vorbedingung ist bei einer unserer Abhängigkeiten aufgrund mehrerer gleichzeitiger Vorgänge in derselben Unterhaltung fehlgeschlagen. |
| 404 | **Code:**`ConversationNotFound` <br/> **Meldung:** Unterhaltung nicht gefunden. | Die Unterhaltung wurde nicht gefunden. |
| 413 | **Code:**`MessageSizeTooBig` <br/> **Nachricht:** Nachrichtengröße zu groß. | Die Größe der eingehenden Anforderung war zu groß. |
| 429 | **Code:**`Throttled` <br/> **Meldung:** Zu viele Anforderungen. Gibt auch den Zeitpunkt zurück, nach dem der Vorgang wiederholt werden soll. | Zu viele Anforderungen wurden vom Bot gesendet. Weitere Informationen finden Sie unter ["Zinslimit".](~/bots/how-to/rate-limit.md) |

## <a name="code-sample"></a>Codebeispiel

|Beispielname | Beschreibung | .NETCore | Node.js | Python |
|----------------|-----------------|--------------|----------------|-----------|
| Teams-Unterhaltungsbot | Behandlung von Nachrichten- und Unterhaltungsereignissen. |[Anzeigen](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot)|[Anzeigen](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/57.teams-conversation-bot)| [Anzeigen](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/57.teams-conversation-bot) |

## <a name="see-also"></a>Siehe auch

- [Senden proaktiver Nachrichten](~/bots/how-to/conversations/send-proactive-messages.md)

- [Abonnieren von Unterhaltungsereignissen](~/bots/how-to/conversations/subscribe-to-conversation-events.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Bot-Befehlsmenüs](~/bots/how-to/create-a-bot-commands-menu.md)
