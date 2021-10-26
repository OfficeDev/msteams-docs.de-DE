---
title: Reagieren auf die Sendeaktion des Aufgabenmoduls
author: surbhigupta
description: Beschreibt, wie auf die Aufgabenmodul-Sendeaktion über einen Aktionsbefehl für Messaging-Erweiterungen reagiert wird
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 92a7080d57b1ea6de3924da53a968d3fc960029a
ms.sourcegitcommit: 781e7b82240075e9d1f55e97f3f1dcbba82a5e4d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2021
ms.locfileid: "60566386"
---
# <a name="respond-to-the-task-module-submit-action"></a>Reagieren auf die Sendeaktion des Aufgabenmoduls

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

In diesem Dokument erfahren Sie, wie Ihre App auf die Aktionsbefehle reagiert, z. B. das Aufgabenmodul des Benutzers, um eine Aktion zu übermitteln.
Nachdem ein Benutzer das Aufgabenmodul übermittelt hat, empfängt Ihr Webdienst eine `composeExtension/submitAction` Aufrufnachricht mit der Befehls-ID und den Parameterwerten. Ihre App hat fünf Sekunden Zeit, um auf den Aufruf zu reagieren. Andernfalls erhält der Benutzer eine Fehlermeldung, **die die App nicht erreichen kann,** und jede Aufforderung wird vom Teams Client ignoriert.

Sie haben die folgenden Optionen, um zu antworten:

* Keine Antwort: Verwenden Sie die Absenden-Aktion, um einen Prozess in einem externen System auszulösen, und geben Sie dem Benutzer kein Feedback, das für lange laufende Prozesse nützlich ist, und wählen Sie aus, ob Sie alternativ Feedback geben möchten. Sie können z. B. Feedback mit einer [proaktiven Nachricht](~/bots/how-to/conversations/send-proactive-messages.md)geben.
* [Ein weiteres Aufgabenmodul:](#respond-with-another-task-module)Sie können im Rahmen einer mehrstufigen Interaktion mit einem zusätzlichen Aufgabenmodul antworten.
* [Kartenantwort:](#respond-with-a-card-inserted-into-the-compose-message-area)Sie können mit einer Karte antworten, mit der der Benutzer interagieren oder in eine Nachricht einfügen kann.
* [Adaptive Karte vom Bot:](#bot-response-with-adaptive-card)Fügen Sie eine adaptive Karte direkt in die Unterhaltung ein.
* [Fordern Sie den Benutzer auf, sich zu authentifizieren.](~/messaging-extensions/how-to/add-authentication.md)
* [Fordern Sie den Benutzer auf, eine zusätzliche Konfiguration bereitzustellen]~/get-started/first-message-extension.md).

Bei der Authentifizierung oder Konfiguration wird der ursprüngliche Aufruf nach Abschluss des Prozesses erneut an Ihren Webdienst senden. Die folgende Tabelle zeigt, welche Arten von Antworten basierend auf dem Aufrufspeicherort `commandContext` der Messaging-Erweiterung verfügbar sind: 

|Antworttyp | Verfassen | Befehlsleiste | Message |
|--------------|:-------------:|:-------------:|:---------:|
|Kartenantwort | ✔ | ✔ | ✔ |
|Ein weiteres Aufgabenmodul | ✔ | ✔ | ✔ |
|Bot mit adaptiver Karte | ✔ | x | ✔ |
| Keine Antwort | ✔ | ✔ | ✔ |

> [!NOTE]
> * Wenn Sie **Action.Submit** über ME-Karten auswählen, sendet sie Aufrufaktivitäten mit dem Namen **composeExtension,** wobei der Wert der üblichen Nutzlast entspricht.
> * Wenn Sie **"Action.Submit** through conversation" auswählen, erhalten Sie eine Nachrichtenaktivität mit dem Namen **"onCardButtonClicked",** wobei der Wert der üblichen Nutzlast entspricht.

Wenn die App einen Unterhaltungs-Bot enthält, installieren Sie den Bot in der Unterhaltung, und laden Sie dann das Aufgabenmodul. Der Bot ist hilfreich, um zusätzlichen Kontext für das Aufgabenmodul abzurufen. Informationen zum Installieren eines Unterhaltungs-Bots finden Sie unter ["Anfordern der Installation Ihres Unterhaltungs-Bots".](create-task-module.md#request-to-install-your-conversational-bot)

## <a name="the-submitaction-invoke-event"></a>Das submitAction-Aufrufereignis

Beispiele für den Empfang der Aufrufnachricht sind:

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionSubmitActionAsync(
  ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken) {
  //code to handle the submit action
}
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
  constructor() {
  handleTeamsMessagingExtensionSubmitAction(context, action) {
  
  //code to handle the submit action
    }
  }
}
```

# <a name="json"></a>[JSON](#tab/json)

Dies ist ein Beispiel für das JSON-Objekt, das Sie erhalten. Der `commandContext` Parameter gibt an, von wo ihre Messaging-Erweiterung ausgelöst wurde. Das `data` Objekt enthält die Felder auf dem Formular als Parameter und die Werte, die der Benutzer übermittelt hat. Das JSON-Objekt hebt die relevantesten Felder hervor.

```json
{
  "name": "composeExtension/submitAction",
  "imdisplayname": "Bob Smith",
  "serviceUrl": "https://smba.trafficmanager.net/amer/",
  "value": {
    "commandId": "giveKudos",
    "commandContext": "compose",
    "context": {
      "theme": "default"
    },
    "data": {
      "id": "submitButton",
      "formField1": "formField1_value",
      "formField2": "formField2_value",
      "formField3": "formField3_value"
    }
  },
  "conversation": {
    "id": "19:7705841b240044b297123ad7f9c99217@thread.skype"
  }
}
```

* * *

## <a name="respond-with-a-card-inserted-into-the-compose-message-area"></a>Antworten mit einer Karte, die in den Bereich zum Verfassen von Nachrichten eingefügt wurde

Die gängigste Möglichkeit, auf die Anforderung zu `composeExtension/submitAction` antworten, ist eine Karte, die in den Bereich zum Verfassen von Nachrichten eingefügt wird. Der Benutzer sendet die Karte an die Unterhaltung. Weitere Informationen zum Verwenden von Karten finden Sie unter [Karten und Kartenaktionen.](~/task-modules-and-cards/cards/cards-actions.md)

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionSubmitActionAsync(
  ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
    var response = new MessagingExtensionActionResponse
    {
        ComposeExtension = new MessagingExtensionResult
        {
            AttachmentLayout = "list",
            Type = "result",
        },
    };
    var createCardData = ((JObject)action.Data).ToObject<CreateCardData>();
var card = new HeroCard
{
     Title = createCardData.Title,
     Subtitle = createCardData.Subtitle,
     Text = createCardData.Text,
};
    var attachments = new List<MessagingExtensionAttachment>();
    attachments.Add(new MessagingExtensionAttachment
    {
        Content = card,
        ContentType = HeroCard.ContentType,
        Preview = card.ToAttachment(),
    });
    response.ComposeExtension.Attachments = attachments;
    return response;
}
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
  handleTeamsMessagingExtensionSubmitAction(context, action) {
    const data = action.data;
    const heroCard = CardFactory.heroCard(data.title, data.text);
    heroCard.content.subtitle = data.subTitle;
    const attachment = { contentType: heroCard.contentType, content: heroCard.content, preview: heroCard };

    return {
      composeExtension: {
        type: 'result',
        attachmentLayout: 'list',
        attachments: [
          attachment
        ]
      }
    }
  }
}
```

# <a name="json"></a>[JSON](#tab/json)

```json
{
  "composeExtension": {
    "attachmentLayout": "list",
    "type": "result",
    "attachments": [
      {
        "preview": {
          "contentType": "application/vnd.microsoft.card.hero",
          "content": {
            "title": "formField1_value",
            "subtitle": "formField2_value",
            "text": "formField3_value"
          }
        },
        "contentType": "application/vnd.microsoft.card.hero",
        "content": {
          "title": "formField1_value",
          "subtitle": "formField2_value",
          "text": "formField3_value"
        }
      }
    ]
  }
}
```

* * *

## <a name="respond-with-another-task-module"></a>Antworten mit einem anderen Aufgabenmodul

Sie können auswählen, um auf das `submitAction` Ereignis mit einem zusätzlichen Aufgabenmodul zu reagieren. Dies ist nützlich, wenn Sie Folgendes benötigen:

* Erfassen Sie große Mengen von Informationen.
* Dynamisches Ändern der Informationssammlung basierend auf benutzereingaben.
* Überprüfen Sie die vom Benutzer übermittelten Informationen, und senden Sie das Formular erneut mit einer Fehlermeldung, wenn etwas nicht stimmt. 

Die Antwortmethode ist identisch mit [der Antwort auf das ursprüngliche `fetchTask` Ereignis.](~/messaging-extensions/how-to/action-commands/create-task-module.md) Wenn Sie das Bot Framework SDK verwenden, löst dasselbe Ereignis für beide Sendeaktionen aus. Damit dies funktioniert, müssen Sie Logik hinzufügen, die die richtige Antwort bestimmt.

## <a name="bot-response-with-adaptive-card"></a>Bot-Antwort mit adaptiver Karte

> [!NOTE]
> Voraussetzung für das Abrufen der Bot-Antwort mit einer adaptiven Karte ist, dass Sie das `bot` Objekt Ihrem App-Manifest hinzufügen und den erforderlichen Bereich für den Bot definieren müssen. Verwenden Sie die gleiche ID wie Ihre Messaging-Erweiterung für Ihren Bot.
 
Sie können auch darauf reagieren, indem Sie `submitAction` eine Nachricht mit einer adaptiven Karte mit einem Bot in den Kanal einfügen. Der Benutzer kann eine Vorschau der Nachricht anzeigen, bevor er sie übermittelt. Dies ist nützlich in Szenarien, in denen Sie Informationen von den Benutzern sammeln, bevor Sie eine Adaptive Kartenantwort erstellen, oder wenn Sie die Karte aktualisieren, nachdem jemand damit interagiert hat. 

Das folgende Szenario zeigt, wie die App Polly eine Abfrage konfiguriert, ohne die Konfigurationsschritte in die Kanalunterhaltung aufzunehmen:

**So konfigurieren Sie die Abfrage**

1. Der Benutzer wählt die Messaging-Erweiterung aus, um das Aufgabenmodul aufzurufen.
1. Der Benutzer konfiguriert die Abfrage mit dem Aufgabenmodul.
1. Nach dem Übermitteln des Aufgabenmoduls verwendet die App die bereitgestellten Informationen, um die Abfrage als adaptive Karte zu erstellen, und sendet sie als `botMessagePreview` Antwort an den Client.
1. Der Benutzer kann dann eine Vorschau der Adaptive Card-Nachricht anzeigen, bevor der Bot sie in den Kanal einfügt. Wenn die App kein Mitglied des Kanals ist, können Sie `Send` sie hinzufügen.

    > [!NOTE] 
    > * Die Benutzer können auch die `Edit` Nachricht auswählen, die sie an das ursprüngliche Aufgabenmodul zurückgibt. 
    > * Die Interaktion mit der adaptiven Karte ändert die Nachricht vor dem Senden.
1. Nachdem der Benutzer den Bot ausgewählt `Send` hat, wird die Nachricht an den Kanal veröffentlicht.

## <a name="respond-to-initial-submit-action"></a>Reagieren auf anfängliche Übermittlungsaktion

Ihr Aufgabenmodul muss auf die anfängliche `composeExtension/submitAction` Nachricht mit einer Vorschau der Karte antworten, die der Bot an den Kanal sendet. Der Benutzer kann die Karte vor dem Senden überprüfen und versuchen, ihren Bot in der Unterhaltung zu installieren, wenn der Bot noch nicht installiert ist.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionSubmitActionAsync(
  ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  dynamic createCardData = ((JObject) action.Data).ToObject(typeof(JObject));
  var response = new MessagingExtensionActionResponse
  {
    ComposeExtension = new MessagingExtensionResult
    {
      Type = "botMessagePreview",
      ActivityPreview = MessageFactory.Attachment(new Attachment
      {
        Content = new AdaptiveCard("1.0")
        {
          Body = new List<AdaptiveElement>()
          {
            new AdaptiveTextBlock() { Text = "FormField1 value was:", Size = AdaptiveTextSize.Large },
            new AdaptiveTextBlock() { Text = Data["FormField1"] as string }
          },
          Height = AdaptiveHeight.Auto,
          Actions = new List<AdaptiveAction>()
          {
            new AdaptiveSubmitAction
            {
              Type = AdaptiveSubmitAction.TypeName,
              Title = "Submit",
              Data = new JObject { { "submitLocation", "messagingExtensionFetchTask" } },
            },
          }
        },
        ContentType = AdaptiveCard.ContentType
      }) as Activity
    }
  };

  return response;
}
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
  handleTeamsMessagingExtensionSubmitAction(context, action) {
    const submittedData = action.data;
    const adaptiveCard = CardFactory.adaptiveCard({
      actions: [
        { type: 'Action.Submit', title: 'Submit', data: { submitLocation: 'messagingExtensionSubmit' } }
      ],
      body: [
          { text: 'Adaptive Card from Task Module', type: 'TextBlock', weight: 'bolder' },
          { text: `${ submittedData.Question }`, type: 'TextBlock', id: 'Question' },
          { id: 'Answer', placeholder: 'Answer here...', type: 'Input.Text' },
        {
          choices: [
            { title: submittedData.Option1, value: submittedData.Option1 },
            { title: submittedData.Option2, value: submittedData.Option2 },
            { title: submittedData.Option3, value: submittedData.Option3 }
          ],
          id: 'Choices',
          isMultiSelect: submittedData.MultiSelect,
          style: 'expanded',
          type: 'Input.ChoiceSet'
        }
      ],
      type: 'AdaptiveCard',
      version: '1.0'
    });
    return {
      composeExtension: {
        activityPreview: MessageFactory.attachment(adaptiveCard, null, null, InputHints.ExpectingInput),
        type: 'botMessagePreview'
      }
    };
  }
}
```

# <a name="json"></a>[JSON](#tab/json)

> [!NOTE]
> * Die `activityPreview` Muss eine Aktivität mit genau einer Adaptive `message` Card-Anlage enthalten. Der `<< Card Payload >>` Wert ist ein Platzhalter für die Karte, die Sie senden möchten.

```json
{
  "composeExtension": {
    "type": "botMessagePreview",
    "activityPreview": {
      "type": "message",
      "attachments":  [
        {
          "contentType": "application/vnd.microsoft.card.adaptive",
          "content": << Card Payload >>
        }
      ]
    }
  }
}
```

* * *

### <a name="the-botmessagepreview-send-and-edit-events"></a>Das botMessagePreview-Sende- und Bearbeitungsereignis

Ihre Messaging-Erweiterung muss auf zwei neue Arten des `composeExtension/submitAction` Aufrufs reagieren, wobei `value.botMessagePreviewAction = "send"` und `value.botMessagePreviewAction = "edit"` .

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionBotMessagePreviewEditAsync(
  ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  //handle the event
}

protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionBotMessagePreviewSendAsync(
  ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  //handle the event
}

```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
  handleTeamsMessagingExtensionBotMessagePreviewEdit(context, action) {

    //handle the event
  }
  
  handleTeamsMessagingExtensionBotMessagePreviewSend(context, action) {

    //handle the event
  }
}

```

# <a name="json"></a>[JSON](#tab/json)

```json
{
  "name": "composeExtension/submitAction",
  "type": "invoke",
  "conversation": { "id": "19:c366b75791784100b6e8b515fd55b063@thread.skype" },
  "imdisplayname": "Pranav Smith",
  ...
  "value": {
    "botMessagePreviewAction": "edit | send",
    "botActivityPreview": [
      {
        "type": "message/card",
        "attachments": [
          {
            "content":
              {
                "type": "AdaptiveCard",
                "body": [{<<card payload>>}]
              },
            "contentType" : "application/vnd.microsoft.card.adaptive"
          }
        ],
        "context": { "theme": "default" }
      }
    ],
  }
}
```

* * *

### <a name="respond-to-botmessagepreview-edit"></a>Antworten auf botMessagePreview-Bearbeitung

Wenn der Benutzer die Karte vor dem Senden bearbeitet, erhalten Sie durch Auswählen von **"Bearbeiten"** einen `composeExtension/submitAction` Aufruf mit `value.botMessagePreviewAction = edit` . Antworten Sie, indem Sie das von Ihnen gesendete Aufgabenmodul als Reaktion auf den anfänglichen `composeExtension/fetchTask` Aufruf zurückgeben, der die Interaktion begonnen hat. Dadurch kann der Benutzer den Prozess starten, indem die ursprünglichen Informationen erneut angezeigt werden. Verwenden Sie die verfügbaren Informationen, um das Aufgabenmodul so zu aktualisieren, dass der Benutzer nicht alle Informationen von Grund auf ausfüllen muss.
Weitere Informationen zum Reagieren auf das ursprüngliche `fetchTask` Ereignis finden Sie unter ["Reagieren auf das ursprüngliche `fetchTask` Ereignis".](~/messaging-extensions/how-to/action-commands/create-task-module.md)

### <a name="respond-to-botmessagepreview-send"></a>Antworten auf botMessagePreview-Senden

Nachdem der Benutzer das **Senden** ausgewählt hat, erhalten Sie einen `composeExtension/submitAction` Aufruf mit `value.botMessagePreviewAction = send` . Ihr Webdienst muss eine proaktive Nachricht mit der adaptiven Karte erstellen und an die Unterhaltung senden sowie auf den Aufruf antworten.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionBotMessagePreviewSendAsync(
  ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  var activityPreview = action.BotActivityPreview[0];
  var attachmentContent = activityPreview.Attachments[0].Content;
  var previewedCard = JsonConvert.DeserializeObject<AdaptiveCard>(attachmentContent.ToString(),
          new JsonSerializerSettings { NullValueHandling = NullValueHandling.Ignore });
  
  previewedCard.Version = "1.0";

  var responseActivity = Activity.CreateMessageActivity();
  Attachment attachment = new Attachment()
  {
    ContentType = AdaptiveCard.ContentType,
    Content = previewedCard
  };
  responseActivity.Attachments.Add(attachment);
  
  // Attribute the message to the user on whose behalf the bot is posting
  responseActivity.ChannelData = new {
    OnBehalfOf = new []
    {
      new
      {
        ItemId = 0,
        MentionType = "person",
        Mri = turnContext.Activity.From.Id,
        DisplayName = turnContext.Activity.From.Name
      }  
    }
  };
  
  await turnContext.SendActivityAsync(responseActivity);

  return new MessagingExtensionActionResponse();
}
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
    async handleTeamsMessagingExtensionBotMessagePreviewSend(context, action) {
      // The data has been returned to the bot in the action structure.
      const activityPreview = action.botActivityPreview[0];
      const attachmentContent = activityPreview.attachments[0].content;
      const userText = attachmentContent.body[1].text;
      const choiceSet = attachmentContent.body[3];

      const submitData = {
        MultiSelect: choiceSet.isMultiSelect ? 'true' : 'false',
        Option1: choiceSet.choices[0].title,
        Option2: choiceSet.choices[1].title,
        Option3: choiceSet.choices[2].title,
        Question: userText
      };

      const adaptiveCard = CardFactory.adaptiveCard({
        actions: [
          { type: 'Action.Submit', title: 'Submit', data: { submitLocation: 'messagingExtensionSubmit' } }
        ],
        body: [
          { text: 'Adaptive Card from Task Module', type: 'TextBlock', weight: 'bolder' },
          { text: `${ submitData.Question }`, type: 'TextBlock', id: 'Question' },
          { id: 'Answer', placeholder: 'Answer here...', type: 'Input.Text' },
          {
            choices: [
                { title: submitData.Option1, value: submitData.Option1 },
                { title: submitData.Option2, value: submitData.Option2 },
                { title: submitData.Option3, value: submitData.Option3 }
            ],
            id: 'Choices',
            isMultiSelect: submitData.MultiSelect,
            style: 'expanded',
            type: 'Input.ChoiceSet'
          }
        ],
        type: 'AdaptiveCard',
        version: '1.0'
      });
      const responseActivity = { type: 'message', attachments: [adaptiveCard], channelData: {
          onBehalfOf: [
              { itemId: 0, mentionType: 'person', mri: context.activity.from.id, displayname: context.activity.from.name }
          ]
      }};

      await context.sendActivity(responseActivity);
    }
}
```

# <a name="json"></a>[JSON](#tab/json)

Sie erhalten eine neue `composeExtension/submitAction` Nachricht, die der folgenden ähnelt:

```json
{
  "name": "composeExtension/submitAction",
  "type": "invoke",
  "conversation": { "id": "19:c366b75791784100b6e8b515fd55b063@thread.skype" },
  "imdisplayname": "Pranav Smith",
  ...
  "value": {
    "botMessagePreviewAction": "send",
    "botActivityPreview": [
      {
        "type": "message/card",
        "attachments": [
          {
            "content":
              {
                "type": "AdaptiveCard",
                "body": [{<<card payload>>}]
              },
            "contentType" : "application/vnd.microsoft.card.adaptive"
          }
        ],
        "context": { "theme": "default" }
      }
    ],
  }
}
```

* * *

### <a name="user-attribution-for-bots-messages"></a>Benutzerzuordnung für Bots-Nachrichten 

In Szenarien, in denen ein Bot Nachrichten im Namen eines Benutzers sendet, hilft die Zuweisung der Nachricht an diesen Benutzer bei der Interaktion und zeigt einen natürlicheren Interaktionsfluss. Mit diesem Feature können Sie einem Benutzer, in dessen Auftrag er gesendet wurde, eine Nachricht von Ihrem Bot zuordnen.

In der folgenden Abbildung befindet sich auf der linken Seite eine Kartennachricht, die von einem Bot ohne Benutzerzuschreibung gesendet wird, und auf der rechten Seite befindet sich eine Karte, die von einem Bot mit Benutzerzuschreibung gesendet wird.

![Benutzerzuschreibungs-Bots](../../../assets/images/messaging-extension/user-attribution-bots.png)

Um die Benutzerzuordnung in Teams zu verwenden, müssen Sie die `OnBehalfOf` Erwähnungsentität `ChannelData` in Ihrer Nutzlast `Activity` hinzufügen, die an Teams gesendet wird.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet-1)

```csharp
    OnBehalfOf = new []
    {
      new
      {
        ItemId = 0,
        MentionType = "person",
        Mri = turnContext.Activity.From.Id,
        DisplayName = turnContext.Activity.From.Name
      }  
    }

```

# <a name="json"></a>[JSON](#tab/json-1)

```json
{
    "text": "Hello World!",
    "ChannelData": {
        "OnBehalfOf": [{
            "itemid": 0,
            "mentionType": "person",
            "mri": "29:orgid:89e6508d-6c0f-4ffe-9f6a-b58416d965ae",
            "displayName": "Sowrabh N R S"
        }]
    }
}
```

* * *

#### <a name="details-of--onbehalfof-entity-schema"></a>Details zum  `OnBehalfOf` Entitätsschema

Der folgende Abschnitt enthält eine Beschreibung der Entitäten im `OnBehalfOf` Array:

|Feld|Typ|Beschreibung|
|:---|:---|:---|
|`itemId`|Ganzzahl|Beschreibt die Identifikation des Elements. Der Wert muss `0` .|
|`mentionType`|Zeichenfolge|Beschreibt die Erwähnung einer "Person".|
|`mri`|Zeichenfolge|Nachrichtenressourcenbezeichner (Message Resource Identifier, MRI) der Person, in deren Auftrag die Nachricht gesendet wird. Der Name des Absenders der Nachricht würde als " \<user\> bis \<bot name\> " angezeigt.|
|`displayName`|Zeichenfolge|Name der Person. Wird als Fallback verwendet, wenn die Namensauflösung nicht verfügbar ist.|
  
## <a name="code-sample"></a>Codebeispiel

| Beispielname           | Beschreibung | .NET    | Node.js   |   
|:---------------------|:--------------|:---------|:--------|
|Teams Messaging-Erweiterungsaktion| Beschreibt, wie Aktionsbefehle definiert, Aufgabenmodul erstellt und auf Aufgabenmodul-Sendeaktion reagiert wird. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) | 
|Teams Messaging-Erweiterungssuche   |  Beschreibt, wie Suchbefehle definiert und auf Suchvorgänge reagiert wird.        |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)|

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Definition von Suchbefehlen](~/messaging-extensions/how-to/search-commands/define-search-command.md)

