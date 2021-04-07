---
title: Grundlagen zu Unterhaltungen
description: Beschreibt Möglichkeiten für eine Unterhaltung mit einem Microsoft Teams-Bot
ms.topic: overview
ms.author: anclear
keyword: conversations basics receive message send message picture message channel data adaptive cards
ms.openlocfilehash: 193a93dbf775389383e0385207fa4112440bffe5
ms.sourcegitcommit: 82bda0599ba2676ab9348c2f4284f73c7dad0838
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2021
ms.locfileid: "51596674"
---
# <a name="conversation-basics"></a>Grundlagen zu Unterhaltungen

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Eine Unterhaltung ist eine Reihe von Nachrichten, die zwischen Ihrem Microsoft Teams-Bot und einem oder mehreren Benutzern gesendet werden. Es gibt drei Arten von Unterhaltungen, die auch als Bereiche in Teams bezeichnet werden:

| Unterhaltungstyp | Beschreibung |
| ------- | ----------- |
| `channel` | Dieser Unterhaltungstyp ist für alle Mitglieder des Kanals sichtbar. |
| `personal` | Dieser Unterhaltungstyp enthält Unterhaltungen zwischen Bots und einem einzelnen Benutzer. |
| `groupChat` | Dieser Unterhaltungstyp umfasst Chats zwischen einem Bot und zwei oder mehr Benutzern. Es aktiviert ihren Bot auch in Besprechungschats. |

Ein Bot verhält sich abhängig von der Unterhaltung, an der er beteiligt ist, unterschiedlich:

* Bots in Kanal- und Gruppenchatunterhaltungen erfordern, dass der Benutzer den Bot @ erwähnt, um ihn in einem Kanal aufgerufen zu haben.
* Bots in einer 1:1-Unterhaltung erfordern keine @-Erwähnung. Alle nachrichten, die vom Benutzer gesendet werden, werden an Ihren Bot gesendet.

Damit der Bot in einer bestimmten Unterhaltung oder einem bestimmten Bereich funktioniert, fügen Sie diesem Bereich unterstützung im [App-Manifest hinzu.](~/resources/schema/manifest-schema.md)

## <a name="messages-in-bot-conversations"></a>Nachrichten in Botunterhaltungen

Jede Nachricht in einer Unterhaltung ist ein `Activity` Objekt vom Typ `messageType: message` . Wenn ein Benutzer eine Nachricht sendet, sendet Teams die Nachricht an Ihren Bot. Teams sendet ein JSON-Objekt an den Messagingendpunkt Ihres Bots. Ihr Bot untersucht die Nachricht, um ihren Typ zu bestimmen, und antwortet entsprechend.

Grundlegende Unterhaltungen werden über den Bot Framework-Connector, eine einzelne REST-API, behandelt. Mit dieser API kann Ihr Bot mit Teams und anderen Kanälen kommunizieren. Das Bot Builder SDK bietet Folgendes:

* Einfacher Zugriff auf den Bot Framework-Connector.
* Zusätzliche Funktionalität zum Verwalten des Unterhaltungsflusses und -zustands.
* Einfache Möglichkeiten zum Integrieren von kognitiven Diensten wie der Verarbeitung natürlicher Sprachen (Natural Language Processing, NLP).

Ihr Bot empfängt Nachrichten von Teams mithilfe der Eigenschaft und sendet einzelne oder `Text` mehrere Nachrichtenantworten an die Benutzer.

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

Um eine Textnachricht zu senden, geben Sie die Zeichenfolge an, die Sie als Aktivität senden möchten. Verwenden Sie im Aktivitätshandler des Bots die Methode des Turn-Kontextobjekts, `SendActivityAsync` um eine einzelne Nachrichtenantwort zu senden. Verwenden Sie die Methode des `SendActivitiesAsync` Objekts, um mehrere Antworten gleichzeitig zu senden. Der folgende Code zeigt ein Beispiel für das Senden einer Nachricht, wenn ein Benutzer einer Unterhaltung hinzugefügt wird:

Der folgende Code zeigt ein Beispiel für das Senden einer Nachricht:

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
> Die Nachrichtenaufteilung erfolgt, wenn eine Textnachricht und eine Anlage in derselben Aktivitätsnutzlast gesendet werden. Diese Aktivität wird von Microsoft Teams in separate Aktivitäten aufgeteilt, eine mit einer Textnachricht und die andere mit einer Anlage. Wenn die Aktivität geteilt wird, erhalten Sie nicht die Nachrichten-ID als Antwort, die verwendet wird, um die Nachricht proaktiv zu aktualisieren oder zu löschen. [](~/bots/how-to/update-and-delete-bot-messages.md) Es wird empfohlen, separate Aktivitäten zu senden, anstatt je nach Nachrichtenteilung.

Nachrichten, die zwischen Benutzern und Bots gesendet werden, enthalten interne Kanaldaten innerhalb der Nachricht. Diese Daten ermöglichen es dem Bot, ordnungsgemäß auf diesem Kanal zu kommunizieren. Mit dem Bot Builder SDK können Sie die Nachrichtenstruktur ändern.

## <a name="teams-channel-data"></a>Teams-Kanaldaten

Das `channelData` Objekt enthält Teams-spezifische Informationen und ist eine definitive Quelle für Team- und Kanal-IDs. Optional können Sie diese IDs zwischenspeichern und als Schlüssel für den lokalen Speicher verwenden. Im SDK werden in der Regel wichtige Informationen aus dem Objekt `TeamsActivityHandler` `channelData` herausgeziehen, um leicht darauf zu barrierefrei zu werden. Sie können jedoch immer über das Objekt auf die ursprünglichen Daten `turnContext` zugreifen.

Das `channelData` Objekt ist nicht in Nachrichten in persönlichen Unterhaltungen enthalten, da diese außerhalb eines Kanals stattfinden.

Ein `channelData` typisches Objekt in einer Aktivität, die an Ihren Bot gesendet wird, enthält die folgenden Informationen:

* `eventType`: Teams-Ereignistyp, der nur bei [Kanaländerungsereignissen übergeben wird.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
* `tenant.id`: Azure Active Directory-Mandanten-ID, die in allen Kontexten übergeben wird.
* `team`: Wird nur in Kanalkontexten übergeben, nicht in persönlichen Chats.
  * `id`: GUID für den Kanal.
  * `name`: Name des Teams, das nur in Fällen von [Teambenennungsereignissen übergeben wird.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
* `channel`: Wird nur in Kanalkontexten übergeben, wenn der Bot erwähnt wird, oder für Ereignisse in Kanälen in Teams, in denen der Bot hinzugefügt wurde.
  * `id`: GUID für den Kanal.
  * `name`: Kanalname, der nur bei [Kanaländerungsereignissen übergeben wird.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
* `channelData.teamsTeamId`: Veraltet. Diese Eigenschaft ist nur aus Abwärtskompatibilität enthalten.
* `channelData.teamsChannelId`: Veraltet. Diese Eigenschaft ist nur aus Abwärtskompatibilität enthalten.

### <a name="example-channeldata-object-channelcreated-event"></a>Beispiel-channelData-Objekt (channelCreated-Ereignis)

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

Nachrichten, die von Ihrem Bot empfangen oder an diesen gesendet werden, können verschiedene Arten von Nachrichteninhalten enthalten.

## <a name="message-content"></a>Nachrichteninhalt

Ihr Bot kann Rich-Text, Bilder und Karten senden. Benutzer können Rich-Text und Bilder an Ihren Bot senden.

| Format    | Vom Benutzer zum Bot | Vom Bot zum Benutzer | Notes                                                                                   |
|-----------|------------------|------------------|-----------------------------------------------------------------------------------------|
| Rich-Text  | ✔                | ✔                |                                                                                         |
| Bilder  | ✔                | ✔                | Maximal 1024×1024 und 1 MB im PNG-, JPEG- oder GIF-Format. Animierte GIF wird nicht unterstützt.  |
| Karten     | ✖                | ✔                | Informationen zu [unterstützten Karten finden Sie](~/task-modules-and-cards/cards/cards-reference.md) in der Referenz zu Den Teams-Karten. |
| Emojis    | ✖                | ✔                | Teams unterstützt derzeit Emojis über UTF-16, z. B. U+1F600 zum Schmunzeln des Gesichts. |

Sie können ihrer Nachricht auch mithilfe der -Eigenschaft Benachrichtigungen `Notification.Alert` hinzufügen.

## <a name="notifications-to-your-message"></a>Benachrichtigungen an Ihre Nachricht

Benachrichtigungen warnen Benutzer über neue Aufgaben, Erwähnungen und Kommentare. Diese Warnungen stehen im Zusammenhang mit dem, wofür Benutzer arbeiten oder was sie sehen müssen, indem sie einen Hinweis in ihren Aktivitätsfeed einfügen. Damit Benachrichtigungen von Ihrer Botnachricht ausgelöst werden, legen Sie die `TeamsChannelData` `Notification.Alert` Objects-Eigenschaft auf true. Ob eine Benachrichtigung ausgelöst wird, hängt von den Teams-Einstellungen des einzelnen Benutzers ab, und Sie können diese Einstellungen nicht außer Kraft setzen. Der Benachrichtigungstyp ist entweder ein Banner oder ein Banner und eine E-Mail.

> [!NOTE]
> Im **Feld Zusammenfassung** wird ein beliebiger Text des Benutzers als Benachrichtigung im Feed angezeigt.

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

Um Ihre Nachricht zu verbessern, können Sie Bilder als Anlagen zu dieser Nachricht hinzufügen.

## <a name="picture-messages"></a>Bildnachrichten

Bilder werden durch Hinzufügen von Anlagen zu einer Nachricht gesendet. Weitere Informationen zu Anlagen finden Sie in [der Bot Framework-Dokumentation](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments).

Bilder können im PNG-, JPEG- oder GIF-Format mindestens 1024×1024 und 1 MB groß sein. Animierte GIF wird nicht unterstützt.

Geben Sie die Höhe und Breite der einzelnen Bilder mithilfe von XML an. In markdown ist die Bildgröße standardmäßig auf 256×256 festgelegt. Zum Beispiel:

* Verwenden Sie: `<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>` .
* Verwenden Sie nicht: `![Duck on a rock](http://aka.ms/Fo983c)` .

Ein Unterhaltungsbot kann adaptive Karten enthalten, die Geschäftsworkflows vereinfachen. Adaptive Karten bieten umfangreiche anpassbare Text-, Sprach-, Bild-, Schaltflächen- und Eingabefelder.

## <a name="adaptive-cards"></a>Adaptive Karten

Adaptive Karten können in einem Bot verfasst und in mehreren Apps wie Teams, Ihrer Website und so weiter angezeigt werden. Weitere Informationen finden Sie unter [Adaptive Karten](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card).

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

Weitere Informationen zu Karten und Karten in Bots finden Sie in [der Kartendokumentation](~/task-modules-and-cards/what-are-cards.md).

Der nächste Abschnitt enthält Statuscodeantworten für Fehler, die von Bot-APIs generiert werden.

## <a name="status-code-responses"></a>Statuscodeantworten

Im Folgenden finden Sie die Statuscodes und deren Fehlercode- und Meldungswerte:

| Statuscode | Fehlercode und Nachrichtenwerte | Beschreibung |
|----------------|-----------------|-----------------|
| 403 | **Code**: `ConversationBlockedByUser` <br/> **Meldung:**"Benutzer hat die Unterhaltung mit dem Bot blockiert." | Der Benutzer hat den Bot im 1:1-Chat oder in einem Kanal über Moderationseinstellungen blockiert. |
| 403 | **Code**: `BotNotInConversationRoster` <br/> **Meldung:**"Der Bot ist nicht Teil des Unterhaltungsplans." | Der Bot ist nicht Teil der Unterhaltung. |
| 403 | **Code**: `BotDisabledByAdmin` <br/> **Meldung:**"Der Mandantenadministrator hat diesen Bot deaktiviert." | Der Mandant hat den Bot blockiert. |
| 401 | **Code**: `BotNotRegistered` <br/> **Meldung:**"Es wurde keine Registrierung für diesen Bot gefunden." | Die Registrierung für diesen Bot wurde nicht gefunden. |
| 412 | **Code**: `PreconditionFailed` <br/> **Meldung:**"Vorbedingung fehlgeschlagen, versuchen Sie es bitte erneut." | Eine Voraussetzung für eine unserer Abhängigkeiten ist aufgrund mehrerer gleichzeitiger Vorgänge in derselben Unterhaltung fehlgeschlagen. |
| 404 | **Code**: `ConversationNotFound` <br/> **Meldung**: "Unterhaltung nicht gefunden". | Die Unterhaltung wurde nicht gefunden. |
| 413 | **Code**: `MessageSizeTooBig` <br/> **Meldung:**"Nachrichtengröße zu groß". | Die Größe der eingehenden Anforderung war zu groß. |
| 429 | **Code**: `Throttled` <br/> **Meldung**: "Zu viele Anforderungen". Gibt außerdem zurück, wann nach dem Versuch erneut geversucht werden soll. | Zu viele Anforderungen wurden vom Bot gesendet. Weitere Informationen finden Sie unter [Rate limit](~/bots/how-to/rate-limit.md). |

Im nächsten Abschnitt wird ein einfaches Codebeispiel veranschaulicht, das den grundlegenden Unterhaltungsfluss in eine Teams-Anwendung integriert.

## <a name="code-sample"></a>Codebeispiel

Im Folgenden finden Sie die Codebeispiele für den Teams-Unterhaltungsbot:

|Beispielname | Beschreibung | . NETCore | Node.js | Python |
|----------------|-----------------|--------------|----------------|-----------|
| Teams-Unterhaltungsbot | Nachrichten- und Unterhaltungsereignisbehandlung. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/57.teams-conversation-bot)| [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/57.teams-conversation-bot) |

## <a name="see-also"></a>Siehe auch

> [!div class="nextstepaction"]
> [Versenden proaktiver Nachrichten](~/bots/how-to/conversations/send-proactive-messages.md)
> [!div class="nextstepaction"]
> [Abonnieren von Unterhaltungsereignissen](~/bots/how-to/conversations/subscribe-to-conversation-events.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Bot-Befehlsmenüs](~/bots/how-to/create-a-bot-commands-menu.md)
