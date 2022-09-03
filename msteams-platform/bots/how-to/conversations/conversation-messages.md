---
title: Meldungen in Bot-Unterhaltungen
description: Erfahren Sie, wie Sie eine Nachricht, vorgeschlagene Aktionen, Benachrichtigungen, Anlagen, Bilder, adaptive Karten, Statusfehlercodeantworten für Drosselung senden.
ms.topic: overview
ms.author: anclear
ms.localizationpriority: medium
ms.openlocfilehash: e9cb272717b5bffc11224b319f40872ec2698c5d
ms.sourcegitcommit: 82c585d287d61924ce3a3bba3e9caeff35c9a27a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2022
ms.locfileid: "67586987"
---
# <a name="messages-in-bot-conversations"></a>Meldungen in Bot-Unterhaltungen

Jede Nachricht in einer Unterhaltung ist ein `Activity` Objekt vom Typ `messageType: message`. Wenn ein Benutzer eine Nachricht sendet, sendet Microsoft Teams die Nachricht an Ihren Bot. Teams sendet ein JSON-Objekt an den Messaging-Endpunkt Ihres Bots, und Teams ermöglicht nur einen Endpunkt für Messaging. Ihr Bot untersucht die Nachricht, um ihren Typ zu bestimmen und entsprechend zu reagieren.

Grundlegende Unterhaltungen werden über den Bot Framework-Connector, eine einzelne REST-API, behandelt. Diese API ermöglicht Es Ihrem Bot, mit Teams und anderen Kanälen zu kommunizieren. Das Bot Builder SDK bietet die folgenden Features:

* Einfacher Zugriff auf den Bot Framework-Connector.
* Zusätzliche Funktionen zum Verwalten von Unterhaltungsfluss und -zustand.
* Einfache Methoden zum Integrieren von kognitiven Diensten, z. B. natürliche Sprachverarbeitung (NLP).

Ihr Bot empfängt Nachrichten von Teams mithilfe der `Text` Eigenschaft und sendet einzelne oder mehrere Nachrichtenantworten an die Benutzer.

Weitere Informationen finden Sie [unter Benutzerzuordnung für Bot-Nachrichten](/microsoftteams/platform/messaging-extensions/how-to/action-commands/respond-to-task-module-submit?tabs=dotnet%2Cdotnet-1&branch=pr-en-us-5926#user-attribution-for-bots-messages)

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
    "text": "Hello Teams TestBot.Sending bold-italic rich text",
    "attachments": [
      {
            "contentType": "text/html",
            "content": "<div><div>Hello Teams TestBot. Sending <strong>bold</strong>-<em>italic</em> rich text.</div>\n</div>"
      } 
    ],
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

Um eine Textnachricht zu senden, geben Sie die Zeichenfolge an, die Sie als Aktivität senden möchten. Verwenden Sie im Aktivitätshandler des Bots die Methode des Turn-Kontextobjekts `SendActivityAsync` , um eine einzelne Nachrichtenantwort zu senden. Verwenden Sie die Methode des Objekts `SendActivitiesAsync` , um mehrere Antworten gleichzeitig zu senden.

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

    this.onMembersAddedActivity(async (context, next) => {
        await Promise.all((context.activity.membersAdded || []).map(async (member) => {
            if (member.id !== context.activity.recipient.id) {
                await context.sendActivity(
                    `Welcome to the team ${member.givenName} ${member.surname}`
                );
            }
        }));

        await next();
    });
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
    "type": "message",
    "from": {
        "id": "28:c9e8c047-2a34-40a1-b28a-b162d5f5327c",
        "name": "Teams TestBot"
    },
    "conversation": {
        "id": "a:17I0kl8EkpE1O9PH5TWrzrLNwnWWcfrU7QZjKR0WSfOpzbfcAg2IaydGElSo10tVr4C7Fc6GtieTJX663WuJCc1uA83n4CSrHSgGBj5XNYLcVlJAs2ZX8DbYBPck201w-",
        "name": "Convo1"
   },
   "recipient": {
        "id": "29:1XJKJMvc5GBtc2JwZq0oj8tHZmzrQgFmB25ATiQWA85gQtHieVkKilBZ9XHoq9j7Zaqt7CZ-NJWi7me2kHTL3Bw",
        "name": "Megan Bowen"
    },
    "text": "My bot's reply",
    "replyToId": "1632474074231"
}

```

---

> [!NOTE]
>
>* Die Nachrichtenaufteilung erfolgt, wenn eine Textnachricht und eine Anlage in derselben Aktivitätsnutzlast gesendet werden. Diese Aktivität wird von Microsoft Teams in separate Aktivitäten unterteilt, eine mit nur einer Textnachricht und die andere mit einer Anlage. Wenn die Aktivität geteilt ist, erhalten Sie als Antwort keine Nachrichten-ID, die verwendet wird, um die Nachricht proaktiv zu [aktualisieren oder zu löschen](~/bots/how-to/update-and-delete-bot-messages.md) . Es wird empfohlen, getrennte Aktivitäten zu senden, anstatt je nach Nachrichtenteilung.
>* Gesendete Nachrichten können lokalisiert werden, um eine Personalisierung bereitzustellen. Weitere Informationen finden Sie [unter Lokalisieren Ihrer App](../../../concepts/build-and-test/apps-localization.md).

Nachrichten, die zwischen Benutzern und Bots gesendet werden, enthalten interne Kanaldaten innerhalb der Nachricht. Diese Daten ermöglichen es dem Bot, in diesem Kanal ordnungsgemäß zu kommunizieren. Mit dem Bot Builder SDK können Sie die Nachrichtenstruktur ändern.

## <a name="send-suggested-actions"></a>Vorgeschlagene Aktionen senden

Vorgeschlagene Aktionen ermöglichen es Ihrem Bot, Schaltflächen darzustellen, die der Benutzer auswählen kann, um Eingaben bereitzustellen. Vorgeschlagene Aktionen verbessern die Benutzerfreundlichkeit, indem sie es dem Benutzer ermöglichen, eine Frage zu beantworten oder eine Auswahl mit einer Schaltfläche zu treffen, anstatt eine Antwort mit einer Tastatur einzugeben.
Die Schaltflächen bleiben in den Rich-Karten für den Benutzer sichtbar und zugänglich, auch nachdem der Benutzer eine Auswahl getroffen hat, während für vorgeschlagene Aktionen keine Schaltflächen verfügbar sind. Dadurch wird verhindert, dass der Benutzer veraltete Schaltflächen in einer Unterhaltung auswährt.

Wenn Sie einer Nachricht vorgeschlagene Aktionen hinzufügen möchten, legen Sie die `suggestedActions` Eigenschaft des [Activity-Objekts](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference) fest, um die Liste der [CardAction-Objekte](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference) anzugeben, die die Schaltflächen darstellen, die dem Benutzer angezeigt werden sollen. Weitere Informationen finden Sie unter [`SugestedActions`](/dotnet/api/microsoft.bot.builder.messagefactory.suggestedactions)

Es folgt ein Beispiel für die Implementierung und Erfahrung mit vorgeschlagenen Aktionen:

``` json
"suggestedActions": {
    "actions": [
      {
        "type": "imBack",
        "title": "Action 1",
        "value": "Action 1"
      },
      {
        "type": "imBack",
        "title": "Action 2",
        "value": "Action 2"
      }
    ],
    "to": [<list of recepientIds>]
  }
```

:::image type="content" source="~/assets/images/Cards/suggested-actions.png" alt-text="Bot vorgeschlagene Aktionen" border="true":::

> [!NOTE]
>
> * `SuggestedActions` werden nur für 1:1-Chat-Bots und textbasierte Nachrichten und nicht für adaptive Karten oder Anlagen unterstützt.
> * Derzeit `imBack` ist der einzige unterstützte Aktionstyp, und Teams zeigt bis zu drei vorgeschlagene Aktionen an.

## <a name="teams-channel-data"></a>Teams-Kanaldaten

Das `channelData` Objekt enthält Teams-spezifische Informationen und ist eine definitive Quelle für Team- und Kanal-IDs. Optional können Sie diese IDs zwischenspeichern und als Schlüssel für den lokalen Speicher verwenden. Das `TeamsActivityHandler` SDK ruft wichtige Informationen aus dem `channelData` Objekt ab, um es leicht zugänglich zu machen. Sie können jedoch immer über das Objekt auf die `turnContext` ursprünglichen Daten zugreifen.

Das `channelData` Objekt ist nicht in Nachrichten in persönlichen Unterhaltungen enthalten, da diese außerhalb eines Kanals stattfinden.

Ein typisches `channelData` Objekt in einer Aktivität, die an Ihren Bot gesendet wird, enthält die folgenden Informationen:

* `eventType`: Teams-Ereignistyp, der nur in Fällen von [Kanaländerungsereignissen](~/bots/how-to/conversations/subscribe-to-conversation-events.md) übergeben wird.
* `tenant.id`: Microsoft Azure Active Directory (Azure AD)-Mandanten-ID, die in allen Kontexten übergeben wird.
* `team`: Wird nur in Kanalkontexten und nicht im persönlichen Chat übergeben.
  * `id`: GUID für den Kanal.
  * `name`: Der Name des Teams, das nur in Fällen von [Teamneunamenereignissen](subscribe-to-conversation-events.md#team-renamed) übergeben wurde.
* `channel`: Wird nur in Kanalkontexten übergeben, wenn der Bot erwähnt wird oder für Ereignisse in Kanälen in Teams, in denen der Bot hinzugefügt wurde.
  * `id`: GUID für den Kanal.
  * `name`: Kanalname, der nur in Fällen von [Kanaländerungsereignissen](~/bots/how-to/conversations/subscribe-to-conversation-events.md) übergeben wird.
* `channelData.teamsTeamId`: Veraltet. Diese Eigenschaft ist nur aus Gründen der Abwärtskompatibilität enthalten.
* `channelData.teamsChannelId`: Veraltet. Diese Eigenschaft ist nur aus Gründen der Abwärtskompatibilität enthalten.

### <a name="example-channeldata-object-channelcreated-event"></a>Beispiel eines channelData-Objekts (channelCreated-Ereignis)

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

## <a name="message-content"></a>Nachrichteninhalt

Nachrichten, die von Ihrem Bot empfangen oder an diesen gesendet werden, können verschiedene Arten von Nachrichteninhalten enthalten.

| Format    | Vom Benutzer zum Bot | Vom Bot zum Benutzer | Anmerkungen                                                                                   |
|-----------|------------------|------------------|-----------------------------------------------------------------------------------------|
| Rich-Text  | ✔️                | ✔️                | Ihr Bot kann Rich-Text, Bilder und Karten senden. Benutzer können Rich-Text und Bilder an Ihren Bot senden.                                                                                        |
| Bilder  | ✔️                | ✔️                | Maximal 1024 × 1024 Pixel und 1 MB im PNG-, JPEG- oder GIF-Format. Animierte GIFs werden nicht unterstützt.  |
| Karten     | ❌                | ✔️                | Informationen zu unterstützten Karten finden Sie in der [Teams-Kartenreferenz](~/task-modules-and-cards/cards/cards-reference.md) . |
| Emojis    | ✔️                | ✔️                | Teams unterstützt derzeit Emojis über UTF-16, z. B. U+1F600 zum Grinsen im Gesicht. |

## <a name="notifications-to-your-message"></a>Benachrichtigungen an Ihre Nachricht

Sie können Ihrer Nachricht auch mithilfe der `Notification.Alert` Eigenschaft Benachrichtigungen hinzufügen. Benachrichtigungen benachrichtigen Benutzer über neue Aufgaben, Erwähnungen und Kommentare. Diese Warnungen beziehen sich auf das, was Benutzer gerade bearbeiten oder was sie durch Einfügen einer Benachrichtigung in ihren Aktivitätsfeed anzeigen müssen. Damit Benachrichtigungen von Ihrer Bot-Nachricht ausgelöst werden, legen Sie die `TeamsChannelData` Objekteigenschaft `Notification.Alert` auf *"true"* fest. Ob eine Benachrichtigung ausgelöst wird, hängt von den Teams-Einstellungen des einzelnen Benutzers ab, und Sie können diese Einstellungen nicht außer Kraft setzen. Der Benachrichtigungstyp ist entweder ein Banner oder sowohl ein Banner als auch eine E-Mail.

> [!NOTE]
> Im Feld **"Zusammenfassung** " wird text vom Benutzer als Benachrichtigung im Feed angezeigt.

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

Um Ihre Nachricht zu verbessern, können Sie Bilder als Anlagen zu dieser Nachricht hinzufügen.

## <a name="picture-messages"></a>Bildnachrichten

Bilder werden gesendet, indem Anhänge zu einer Nachricht hinzugefügt werden. Weitere Informationen zu Anlagen finden Sie unter [Hinzufügen von Medienanlagen zu Nachrichten](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments).

Bilder können höchstens 1024×1024 MB und 1 MB im PNG-, JPEG- oder GIF-Format sein. Animierte GIFs werden nicht unterstützt.

Geben Sie die Höhe und Breite der einzelnen Bilder mithilfe von XML an. In Markdown ist die Bildgröße standardmäßig 256×256. Beispiel:

* Verwenden Sie: `<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>`.
* Verwenden Sie nicht: `![Duck on a rock](http://aka.ms/Fo983c)`.

Ein Unterhaltungsbot kann adaptive Karten enthalten, die Geschäftsworkflows vereinfachen. Adaptive Karten bieten anpassbaren Text, Sprache, Bilder, Schaltflächen und Eingabefelder.

## <a name="adaptive-cards"></a>Adaptive Karten

Adaptive Karten können in einem Bot erstellt und in mehreren Apps wie Teams, Ihrer Website usw. angezeigt werden. Weitere Informationen finden Sie unter [Adaptive Karten](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card).

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

### <a name="form-completion-feedback"></a>Feedback zum Ausfüllen des Formulars

Die Meldung zum Ausfüllen des Formulars wird in adaptiven Karten angezeigt, während eine Antwort an den Bot gesendet wird. Die Nachricht kann zwei Typen aufweisen: Fehler oder Erfolg:

* **Fehler**: Wenn eine an den Bot gesendete Antwort nicht erfolgreich war, **hat etwas nicht geklappt. Die Meldung "Erneut versuchen** " wird angezeigt.

     :::image type="content" source="../../../assets/images/Cards/error-message.png" alt-text="Fehlermeldung"border="true":::

* **Erfolg**: Wenn eine an den Bot gesendete Antwort erfolgreich ist, **wird Ihre Antwort an die App-Nachricht gesendet** .

     :::image type="content" source="../../../assets/images/Cards/success.PNG" alt-text="Erfolgsmeldung"border="true":::

     Sie können den Chat **schließen** oder wechseln, um die Nachricht zu schließen.

     Wenn Sie die Erfolgsmeldung nicht anzeigen möchten, legen Sie das Attribut `hide` in der `msTeams` `feedback` Eigenschaft fest`true`. Es folgt ein Beispiel:

     ```json
        "content": {
            "type": "AdaptiveCard",
            "title": "Card with hidden footer messages",
            "version": "1.0",
            "actions": [
            {
                "type": "Action.Submit",
                "title": "Submit",
                "msTeams": {
                    "feedback": {
                    "hide": true
                    }
                }
            }
            ]
        } 
     ```

Weitere Informationen zu Karten und Karten in Bots finden Sie in der [Kartendokumentation](~/task-modules-and-cards/what-are-cards.md).

## <a name="status-code-responses"></a>Statuscodeantworten

Es folgen die Statuscodes und deren Fehlercode- und Meldungswerte:

| Statuscode | Fehlercode- und Meldungswerte | Beschreibung |
|----------------|-----------------|-----------------|
| 403 | **Code**: `ConversationBlockedByUser` <br/> **Nachricht**: Der Benutzer hat die Unterhaltung mit dem Bot blockiert. | Der Benutzer hat den Bot im 1:1-Chat oder einem Kanal über Moderationseinstellungen blockiert. |
| 403 | **Code**: `BotNotInConversationRoster` <br/> **Nachricht**: Der Bot ist nicht Teil der Unterhaltungsliste. | Der Bot ist nicht Teil der Unterhaltung. |
| 403 | **Code**: `BotDisabledByAdmin` <br/> **Nachricht**: Der Mandantenadministrator hat diesen Bot deaktiviert. | Der Mandant hat den Bot blockiert. |
| 401 | **Code**: `BotNotRegistered` <br/> **Nachricht**: Für diesen Bot wurde keine Registrierung gefunden. | Die Registrierung für diesen Bot wurde nicht gefunden. |
| 412 | **Code**: `PreconditionFailed` <br/> **Meldung**: Voraussetzung fehlgeschlagen, bitte versuchen Sie es erneut. | Eine Vorbedingung für eine unserer Abhängigkeiten ist aufgrund mehrerer gleichzeitiger Vorgänge in derselben Unterhaltung fehlgeschlagen. |
| 404 | **Code**: `ConversationNotFound` <br/> **Nachricht**: Unterhaltung nicht gefunden. | Die Unterhaltung wurde nicht gefunden. |
| 413 | **Code**: `MessageSizeTooBig` <br/> **Nachricht**: Nachrichtengröße zu groß. | Die Größe der eingehenden Anforderung war zu groß. |
| 429 | **Code**: `Throttled` <br/> **Nachricht**: Zu viele Anforderungen. Gibt auch zurück, wann der Wiederholungsversuch ausgeführt werden soll. | Zu viele Anfragen wurden vom Bot gesendet. Weitere Informationen finden Sie [unter Zinslimit](~/bots/how-to/rate-limit.md). |

## <a name="code-sample"></a>Codebeispiel

| Beispielname | Beschreibung | Node.js | .NETCore | Python | .NET |
|----------------|-----------------|--------------|----------------|-----------|-----|
| Teams-Unterhaltungsbot | Verarbeitung von Nachrichten- und Unterhaltungsereignissen. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/57.teams-conversation-bot) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot) | [Anzeigen](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/57.teams-conversation-bot) | – |
| Lokalisierung von Teams-Apps | Lokalisierung von Teams-Apps mithilfe von Bot und Registerkarte. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-localization/nodejs) | – | – | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-localization/csharp) |

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Bot-Befehlsmenüs](~/bots/how-to/create-a-bot-commands-menu.md)

## <a name="see-also"></a>Siehe auch

* [Senden proaktiver Nachrichten](~/bots/how-to/conversations/send-proactive-messages.md)
* [Abonnieren von Unterhaltungsereignissen](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
* [Senden und Empfangen von Dateien über den Bot](~/bots/how-to/bots-filesv4.md)
* [Senden der Mandanten-ID und Konversations-ID an die Anforderungsheader des Bots](~/bots/how-to/conversations/request-headers-of-the-bot.md)
* [Lokalisieren IhrerApp](../../../concepts/build-and-test/apps-localization.md)
