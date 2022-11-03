---
title: Meldungen in Bot-Unterhaltungen
description: Erfahren Sie, wie Sie eine Nachricht, vorgeschlagene Aktionen, Benachrichtigungen, Anlagen, Bilder, adaptive Karte und Statusfehlercodeantworten senden.
ms.topic: overview
ms.author: anclear
ms.localizationpriority: medium
ms.openlocfilehash: 16849a9e8ed97854e91934aef9de463eb355fec5
ms.sourcegitcommit: c3601696cced9aadc764f1e734646ee7711f154c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2022
ms.locfileid: "68833205"
---
# <a name="messages-in-bot-conversations"></a>Meldungen in Bot-Unterhaltungen

Jede Nachricht in einer Unterhaltung ist ein `Activity` Objekt vom Typ `messageType: message`. Wenn ein Benutzer eine Nachricht sendet, sendet Microsoft Teams die Nachricht an Ihren Bot. Teams sendet ein JSON-Objekt an den Messagingendpunkt Ihres Bots, und Teams lässt nur einen Endpunkt für Messaging zu. Ihr Bot untersucht die Nachricht, um ihren Typ zu bestimmen und entsprechend zu reagieren.

Grundlegende Unterhaltungen werden über den Bot Framework-Connector verarbeitet, eine einzelne REST-API. Diese API ermöglicht Es Ihrem Bot, mit Teams und anderen Kanälen zu kommunizieren. Das Bot Builder SDK bietet die folgenden Features:

* Einfacher Zugriff auf den Bot Framework-Connector.
* Funktionalität zum Verwalten des Konversationsflusses und -zustands.
* Einfache Möglichkeiten zum Integrieren von Cognitive Services, z. B. verarbeitung natürlicher Sprache (Natural Language Processing, NLP).

Ihr Bot empfängt Nachrichten von Teams mithilfe der `Text` -Eigenschaft und sendet einzelne oder mehrere Nachrichtenantworten an die Benutzer.

Weitere Informationen finden Sie unter [Benutzerzuordnung für Botnachrichten](/microsoftteams/platform/messaging-extensions/how-to/action-commands/respond-to-task-module-submit?tabs=dotnet%2Cdotnet-1&branch=pr-en-us-5926#user-attribution-for-bots-messages).

## <a name="receive-a-message"></a>Empfangen einer Nachricht

Verwenden Sie die `Text` -Eigenschaft eines `Activity` -Objekts, um eine SMS zu empfangen. Verwenden Sie im Aktivitäts-Handler des Bots die `Activity` des Turn-Kontextobjekts, um eine einzelne Nachrichtenanforderung zu lesen.

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

Um eine SMS zu senden, geben Sie die Zeichenfolge an, die Sie als Aktivität senden möchten. Verwenden Sie im Aktivitätshandler des Bots die Methode des Turn-Kontextobjekts `SendActivityAsync` , um eine einzelne Nachrichtenantwort zu senden. Verwenden Sie die -Methode des `SendActivitiesAsync` -Objekts, um mehrere Antworten zu senden.

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
>* Die Nachrichtenaufteilung erfolgt, wenn eine SMS und eine Anlage in derselben Aktivitätsnutzlast gesendet werden. Teams teilt diese Aktivität in zwei separate Aktivitäten auf, eine mit einer SMS und die andere mit einer Anlage. Da die Aktivität aufgeteilt wird, erhalten Sie nicht die Nachrichten-ID als Antwort, die verwendet wird, um die Nachricht proaktiv zu [aktualisieren oder zu löschen](~/bots/how-to/update-and-delete-bot-messages.md) . Es wird empfohlen, separate Aktivitäten zu senden, anstatt von der Nachrichtenaufteilung abhängig zu sein.
>* Gesendete Nachrichten können lokalisiert werden, um eine Personalisierung bereitzustellen. Weitere Informationen finden Sie unter [Lokalisieren Ihrer App](../../../concepts/build-and-test/apps-localization.md).

Nachrichten, die zwischen Benutzern und Bots gesendet werden, enthalten interne Kanaldaten in der Nachricht. Diese Daten ermöglichen es dem Bot, auf diesem Kanal ordnungsgemäß zu kommunizieren. Mit dem Bot Builder SDK können Sie die Nachrichtenstruktur ändern.

## <a name="send-suggested-actions"></a>Vorgeschlagene Aktionen senden

Die vorgeschlagenen Aktionen ermöglichen es Ihrem Bot, Schaltflächen anzuzeigen, die der Benutzer auswählen kann, um Eingaben bereitzustellen. Vorgeschlagene Aktionen verbessern die Benutzerfreundlichkeit, indem sie es dem Benutzer ermöglichen, eine Frage zu beantworten oder eine Auswahl mit auswahl einer Schaltfläche zu treffen, anstatt eine Antwort mit einer Tastatur einzugeben.
Wenn der Benutzer eine Schaltfläche auswählt, bleibt sie in den Rich Cards sichtbar und zugänglich, aber nicht für die vorgeschlagenen Aktionen. Dadurch wird verhindert, dass der Benutzer veraltete Schaltflächen innerhalb einer Unterhaltung auswählen kann.

Um einer Nachricht vorgeschlagene Aktionen hinzuzufügen, legen Sie die `suggestedActions` -Eigenschaft eines [Aktivitätsobjekts](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference) fest, um die Liste der [Kartenaktionsobjekte](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference) anzugeben, die die Schaltflächen darstellen, die dem Benutzer angezeigt werden sollen. Weitere Informationen finden Sie unter [`sugestedActions`](/dotnet/api/microsoft.bot.builder.messagefactory.suggestedactions).

Im Folgenden finden Sie ein Beispiel für die Implementierung und Erfahrung von vorgeschlagenen Aktionen:

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

Im Folgenden wird ein Beispiel für vorgeschlagene Aktionen veranschaulicht:

:::image type="content" source="~/assets/images/Cards/suggested-actions.png" alt-text="Vorgeschlagene Botaktionen" border="true":::

> [!NOTE]
>
> * `SuggestedActions` werden nur für 1:1-Chatbots und textbasierte Nachrichten und nicht für adaptive Karten oder Anlagen unterstützt.
> * `imBack` ist der einzige unterstützte Aktionstyp, und Teams zeigt bis zu drei vorgeschlagene Aktionen an.

## <a name="teams-channel-data"></a>Teams-Kanaldaten

Das `channelData` Objekt enthält Teams-spezifische Informationen und ist eine definitive Quelle für Team- und Kanal-IDs. Optional können Sie diese IDs zwischenspeichern und als Schlüssel für den lokalen Speicher verwenden. Der `TeamsActivityHandler` im SDK ruft wichtige Informationen aus dem `channelData` Objekt ab, um es zugänglich zu machen. Sie können jedoch immer über das -Objekt auf die `turnContext` ursprünglichen Daten zugreifen.

Das `channelData` -Objekt ist nicht in Nachrichten in persönlichen Unterhaltungen enthalten, da diese außerhalb eines Kanals stattfinden.

Ein typisches `channelData` Objekt in einer Aktivität, die an Ihren Bot gesendet wird, enthält die folgenden Informationen:

* `eventType`: Teams-Ereignistyp wird nur in Fällen von [Kanaländerungsereignissen](~/bots/how-to/conversations/subscribe-to-conversation-events.md) übergeben.
* `tenant.id`: Microsoft Azure Active Directory (Azure AD)-Mandanten-ID, die in allen Kontexten übergeben wird.
* `team`: Wird nur in Kanalkontexten übergeben, nicht im persönlichen Chat.
  * `id`: GUID für den Kanal.
  * `name`: Name des Teams wird nur in Fällen von [Teambenennungsereignissen](subscribe-to-conversation-events.md#team-renamed) übergeben.
* `channel`: Wird nur in Kanalkontexten übergeben, wenn der Bot erwähnt wird, oder für Ereignisse in Kanälen in Teams, in denen der Bot hinzugefügt wurde.
  * `id`: GUID für den Kanal.
  * `name`: Kanalname wird nur in Fällen von [Kanaländerungsereignissen](~/bots/how-to/conversations/subscribe-to-conversation-events.md) übergeben.
* `channelData.teamsTeamId`:Veraltet. Diese Eigenschaft ist nur aus Gründen der Abwärtskompatibilität enthalten.
* `channelData.teamsChannelId`:Veraltet. Diese Eigenschaft ist nur aus Gründen der Abwärtskompatibilität enthalten.

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
| Bilder  | ✔️                | ✔️                | Maximal 1.024 × 1.024 Pixel und 1 MB im PNG-, JPEG- oder GIF-Format. Unterstützt das animierte GIF nicht. |
| Karten     | ❌                | ✔️                | Informationen zu unterstützten Karten finden Sie [unter Teams-Kartenreferenz](~/task-modules-and-cards/cards/cards-reference.md) . |
| Emojis    | ✔️                | ✔️                | Teams unterstützt derzeit Emojis über UTF-16, z. B. U+1F600 für grinsendes Gesicht. |

### <a name="picture-messages"></a>Bildnachrichten

Um Ihre Nachricht zu verbessern, können Sie Bilder als Anlagen zu dieser Nachricht hinzufügen. Weitere Informationen zu Anlagen finden [Sie unter Hinzufügen von Medienanlagen zu Nachrichten](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments).

Bilder können maximal 1.024 × 1.024 Pixel und 1 MB im PNG-, JPEG- oder GIF-Format sein. Animierte GIFs werden nicht unterstützt.

Geben Sie die Höhe und Breite der einzelnen Bilder mithilfe von XML an. In Markdown ist die Bildgröße standardmäßig 256×256. Beispiel:

* Verwenden Sie: `<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>`.
* Verwenden Sie nicht: `![Duck on a rock](http://aka.ms/Fo983c)`.

Ein Konversationsbot kann adaptive Karten enthalten, die Geschäftsworkflows vereinfachen. Adaptive Karten bieten umfangreiche anpassbare Text-, Sprach-, Bild-, Schaltflächen- und Eingabefelder.

### <a name="adaptive-cards"></a>Adaptive Karten

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

#### <a name="form-completion-feedback"></a>Feedback zum Ausfüllen des Formulars

Sie können Feedback zum Ausfüllen von Formularen mithilfe einer adaptiven Karte erstellen. Die Meldung zum Ausfüllen des Formulars wird in adaptiven Karten angezeigt, während eine Antwort an den Bot gesendet wird. Die Meldung kann zwei Typen aufweisen: Fehler oder Erfolg:

* **Fehler**: Wenn eine an den Bot gesendete Antwort nicht erfolgreich ist, ist **ein Fehler aufgetreten, wird die Meldung Erneut versuchen** angezeigt.

     :::image type="content" source="../../../assets/images/Cards/error-message.png" alt-text="Fehlermeldung"border="true":::

* **Erfolg**: Wenn eine an den Bot gesendete Antwort erfolgreich ist, wird **Ihre Antwort an die App-Nachricht gesendet** angezeigt.

     :::image type="content" source="../../../assets/images/Cards/success.PNG" alt-text="Erfolgsmeldung"border="true":::

     Sie können **Schließen** oder Chat wechseln auswählen, um die Nachricht zu schließen.

     Wenn Sie die Erfolgsmeldung nicht anzeigen möchten, legen Sie das -Attribut `hide` in der `msTeams` `feedback` -Eigenschaft auf `true` fest. Es folgt ein Beispiel:

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

## <a name="add-notifications-to-your-message"></a>Hinzufügen von Benachrichtigungen zu Ihrer Nachricht

Es gibt zwei Möglichkeiten, eine Benachrichtigung über Ihre Anwendung zu senden:

* Durch Festlegen der `Notification.Alert` -Eigenschaft für die Botnachricht.
* Durch Senden einer Aktivitätsfeedbenachrichtigung mithilfe des Graph-API.

Mit der `Notification.Alert` -Eigenschaft können Sie Ihrer Nachricht Benachrichtigungen hinzufügen. Benachrichtigungen benachrichtigen Benutzer auf ein Ereignis in Ihrer Anwendung, z. B. neue Aufgaben, Erwähnungen oder Kommentare. Diese Warnungen beziehen sich darauf, worüber Benutzer arbeiten oder was sie sich ansehen müssen, indem sie einen Hinweis in ihren Aktivitätsfeed einfügen. Legen Sie für Benachrichtigungen, die von Ihrer Botnachricht ausgelöst werden sollen, die `TeamsChannelData` Eigenschaft objects `Notification.Alert` auf *true* fest. Ob eine Benachrichtigung ausgelöst wird, hängt von den Teams-Einstellungen des einzelnen Benutzers ab, und Sie können diese Einstellungen nicht überschreiben.

Wenn Sie eine beliebige Benachrichtigung generieren möchten, ohne eine Nachricht an den Benutzer zu senden, können Sie die Graph-API verwenden. Weitere Informationen finden Sie unter [Senden von Aktivitätsfeedbenachrichtigungen mithilfe von Graph-API](/graph/teams-send-activityfeednotifications) zusammen mit den [bewährten Methoden](/graph/teams-activity-feed-notifications-best-practices).

> [!NOTE]
> Im Feld **Zusammenfassung** wird beliebiger Text des Benutzers als Benachrichtigung im Feed angezeigt.

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

## <a name="status-codes-from-bot-conversational-apis"></a>Statuscodes von Bot-Konversations-APIs

Stellen Sie sicher, dass Sie diese Fehler in Ihrer Teams-App entsprechend behandeln. In der folgenden Tabelle sind die Fehlercodes und die Beschreibungen aufgeführt, unter denen die Fehler generiert werden:

| Statuscode | Fehlercode und Meldungswerte | Beschreibung | Wiederholungsanforderung | Entwickleraktion |
|----------------|-----------------|-----------------|----------------|----------------|
| 400 | **Code**: `Bad Argument` <br/> **Meldung**: *szenariospezifisch | Vom Bot bereitgestellte ungültige Anforderungsnutzlast. Weitere Informationen finden Sie in der Fehlermeldung. | Nein | Erneutes Auswerten der Anforderungsnutzlast auf Fehler. Überprüfen Sie die zurückgegebene Fehlermeldung auf Details. |
| 401 | **Code**: `BotNotRegistered` <br/> **Meldung**: Für diesen Bot wurde keine Registrierung gefunden. | Die Registrierung für diesen Bot wurde nicht gefunden. | Nein | Überprüfen Sie die Bot-ID und das Kennwort. Stellen Sie sicher, dass die Bot-ID (AAD-ID) im Teams-Entwicklerportal oder über die Azure-Botkanalregistrierung in Azure mit aktiviertem "Teams"-Kanal registriert ist.|
| 403 | **Code**: `BotDisabledByAdmin` <br/> **Meldung**: Der Mandantenadministrator hat diesen Bot deaktiviert. | Der Mandantenadministrator hat Interaktionen zwischen Dem Benutzer und der Bot-App blockiert. Der Mandantenadministrator muss die App für den Benutzer innerhalb von App-Richtlinien zulassen. Weitere Informationen finden Sie unter [App-Richtlinien](/microsoftteams/app-policies). | Nein | Beenden Sie die Veröffentlichung in einer Unterhaltung, bis die Interaktion mit dem Bot explizit von einem Benutzer in der Unterhaltung initiiert wurde, der angibt, dass der Bot nicht mehr blockiert ist. |
| 403 | **Code**: `BotNotInConversationRoster` <br/> **Meldung**: Der Bot ist nicht Teil der Konversationsliste. | Der Bot ist nicht Teil der Unterhaltung. Die App muss in der Unterhaltung neu installiert werden. | Nein | Bevor Sie versuchen, eine weitere Konversationsanforderung zu senden, warten Sie auf ein [`installationUpdate`](~/bots/how-to/conversations/subscribe-to-conversation-events.md#install-update-event) Ereignis, das angibt, dass der Bot erneut hinzugefügt wurde.|
| 403 | **Code**: `ConversationBlockedByUser` <br/> **Meldung**: Der Benutzer hat die Konversation mit dem Bot blockiert. | Der Benutzer hat den Bot im persönlichen Chat oder in einem Kanal über Moderationseinstellungen blockiert. | Nein | Löschen Sie die Konversation aus dem Cache. Beenden Sie den Versuch, In Unterhaltungen zu posten, bis die Interaktion mit dem Bot explizit von einem Benutzer in der Unterhaltung initiiert wird, was darauf hinweist, dass der Bot nicht mehr blockiert wird. |
| 403 |**Code**: `InvalidBotApiHost` <br/> **Meldung**: Ungültiger Bot-API-Host. Rufen `https://smba.infra.gcc.teams.microsoft.com`Sie für GCC-Mandanten auf.|Der Bot hat den öffentlichen API-Endpunkt für eine Konversation aufgerufen, die zu einem GCC-Mandanten gehört.| Nein | Aktualisieren Sie die Dienst-URL für die Konversation auf , `https://smba.infra.gcc.teams.microsoft.com` und wiederholen Sie die Anforderung.|
| 403 | **Code**: `NotEnoughPermissions` <br/> **Meldung**: *szenariospezifisch | Der Bot verfügt nicht über die erforderlichen Berechtigungen zum Ausführen der angeforderten Aktion. | Nein | Bestimmen Sie die erforderliche Aktion anhand der Fehlermeldung. |
| 404 | **Code**: `ActivityNotFoundInConversation` <br/> **Meldung**: Unterhaltung nicht gefunden. | Die angegebene Nachrichten-ID konnte in der Unterhaltung nicht gefunden werden. Die Nachricht ist nicht vorhanden, oder sie wurde gelöscht. | Nein | Überprüfen Sie, ob die gesendete Nachrichten-ID ein erwarteter Wert ist. Entfernen Sie die ID, wenn sie zwischengespeichert wurde. |
| 404 | **Code**: `ConversationNotFound` <br/> **Meldung**: Unterhaltung nicht gefunden. | Die Konversation wurde nicht gefunden, da sie nicht vorhanden ist oder gelöscht wurde. | Nein | Überprüfen Sie, ob die gesendete Konversations-ID ein erwarteter Wert ist. Entfernen Sie die ID, wenn sie zwischengespeichert wurde. |
| 412 | **Code**: `PreconditionFailed` <br/> **Meldung**: Fehler bei der Vorbedingung. Versuchen Sie es erneut. | Eine Vorbedingung ist für eine unserer Abhängigkeiten aufgrund mehrerer gleichzeitiger Vorgänge in derselben Konversation fehlgeschlagen. | Ja | Wiederholen Sie den Vorgang mit exponentiellem Backoff. |
| 413 | **Code**: `MessageSizeTooBig` <br/> **Nachricht**: Die Nachrichtengröße ist zu groß. | Die Größe der eingehenden Anforderung war zu groß. Weitere Informationen finden Sie unter [Formatieren Ihrer Botnachrichten](/microsoftteams/platform/bots/how-to/format-your-bot-messages). | Nein | Reduzieren Sie die Nutzlastgröße. |
| 429 | **Code**: `Throttled` <br/> **Meldung**: Zu viele Anforderungen. Gibt auch den Zeitpunkt zurück, nach dem versucht werden soll. | Vom Bot wurden zu viele Anforderungen gesendet. Weitere Informationen finden Sie unter [Ratenlimit](/microsoftteams/platform/bots/how-to/rate-limit). | Ja | Versuchen Sie es mit dem `Retry-After` Header, um die Backoffzeit zu bestimmen. |
| 500 | **Code**: `ServiceError` <br/> **Meldung**: *verschiedene | Internal server error. (Interner Serverfehler) | Nein | Melden Sie das Problem in der [Entwicklercommunity](~/feedback.md#developer-community-help). |
| 502 | **Code**: `ServiceError` <br/> **Meldung**: *verschiedene | Dienstabhängigkeitsproblem. | Ja | Wiederholen Sie den Vorgang mit exponentiellem Backoff. Wenn das Problem weiterhin besteht, melden Sie das Problem in der [Entwicklercommunity](~/feedback.md#developer-community-help). |
| 503 | | Der Dienst ist nicht verfügbar. | Ja | Wiederholen Sie den Vorgang mit exponentiellem Backoff. Wenn das Problem weiterhin besteht, melden Sie das Problem in der [Entwicklercommunity](~/feedback.md#developer-community-help). |
| 504 | | Gatewaytimeout. | Ja | Wiederholen Sie den Vorgang mit exponentiellem Backoff. Wenn das Problem weiterhin besteht, melden Sie das Problem in der [Entwicklercommunity](~/feedback.md#developer-community-help). |

### <a name="status-codes-retry-guidance"></a>Anleitung zur Wiederholung von Statuscodes

Der allgemeine Wiederholungsleitfaden für jeden Statuscode ist in der folgenden Tabelle aufgeführt. Der Bot muss verhindern, dass statuscodes wiederholt werden, die nicht angegeben sind:

|Statuscode | Wiederholungsstrategie |
|----------------|-----------------|
| 403 | Wiederholen Sie den Vorgang, indem Sie die GCC-API `https://smba.infra.gcc.teams.microsoft.com` für `InvalidBotApiHost`aufrufen.|
| 412 | Wiederholen Sie den Vorgang mit exponentiellem Backoff. |
| 429 | Versuchen Sie es mit dem `Retry-After` -Header, um die Wartezeit in Sekunden und zwischen Anforderungen zu bestimmen, falls verfügbar. Wiederholen Sie andernfalls nach Möglichkeit das exponentielle Backoff mit der Thread-ID. |
| 502 | Wiederholen Sie den Vorgang mit exponentiellem Backoff. |
| 503 | Wiederholen Sie den Vorgang mit exponentiellem Backoff. |
| 504 | Wiederholen Sie den Vorgang mit exponentiellem Backoff. |

## <a name="code-sample"></a>Codebeispiel

| Beispielname | Beschreibung | Node.js | .NETCore | Python | .NET |
|----------------|-----------------|--------------|----------------|-----------|-----|
| Teams-Unterhaltungsbot | Verarbeitung von Nachrichten- und Unterhaltungsereignissen. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/57.teams-conversation-bot) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot) | [Anzeigen](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/57.teams-conversation-bot) | – |
| Lokalisierung von Teams-Apps | Teams-App-Lokalisierung mithilfe von Bot und Registerkarte. | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-localization/nodejs) | – | – | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-localization/csharp) |

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Bot-Befehlsmenüs](~/bots/how-to/create-a-bot-commands-menu.md)

## <a name="see-also"></a>Siehe auch

* [Senden proaktiver Nachrichten](~/bots/how-to/conversations/send-proactive-messages.md)
* [Abonnieren von Unterhaltungsereignissen](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
* [Senden und Empfangen von Dateien über den Bot](~/bots/how-to/bots-filesv4.md)
* [Senden der Mandanten-ID und Konversations-ID an die Anforderungsheader des Bots](~/bots/how-to/conversations/request-headers-of-the-bot.md)
* [Lokalisieren IhrerApp](../../../concepts/build-and-test/apps-localization.md)
