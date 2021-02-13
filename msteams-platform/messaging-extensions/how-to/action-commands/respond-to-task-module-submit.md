---
title: Reagieren auf die Aktion zum Senden des Aufgabenmoduls
author: clearab
description: Beschreibt, wie auf die Aktion zum Senden des Aufgabenmoduls über einen Befehl für eine Aktion für die Nachrichtenerweiterung reagiert wird.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 1fb2f2dc51d7de1208a5a913abf2d38cb80c401a
ms.sourcegitcommit: e3b6bc31059ec77de5fbef9b15c17d358abbca0f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/12/2021
ms.locfileid: "50231645"
---
# <a name="respond-to-the-task-module-submit-action"></a>Reagieren auf die Aktion zum Senden des Aufgabenmoduls

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Nachdem ein Benutzer das Aufgabenmodul übermittelt hat, empfängt ihr Webdienst eine Aufrufnachricht mit der Befehls-ID `composeExtension/submitAction` und den Parameterwerten. Ihre App hat fünf Sekunden Zeit, um auf den Aufruf zu reagieren, andernfalls erhält der Benutzer eine Fehlermeldung, die die App nicht erreichen *kann,* und alle Antworten auf den Aufruf werden vom Client von Teams ignoriert.

Sie haben die folgenden Optionen, um zu reagieren:

* Keine Antwort – Sie können die Aktion "Übermitteln" verwenden, um einen Prozess in einem externen System auszulösen, und dem Benutzer kein Feedback geben. Dies kann für lange dauernde Prozesse nützlich sein, und Sie können feedback auf andere Weise (z. B. mit einer [proaktiven Nachricht) bereitstellen.](~/bots/how-to/conversations/send-proactive-messages.md)
* [Ein weiteres Aufgabenmodul:](#respond-with-another-task-module) Sie können im Rahmen einer mehrstufigen Interaktion mit einem zusätzlichen Aufgabenmodul antworten.
* [Kartenantwort:](#respond-with-a-card-inserted-into-the-compose-message-area) Sie können mit einer Karte antworten, mit der der Benutzer dann interagieren und/oder in eine Nachricht einfügen kann.
* [Adaptive Karte vom Bot –](#bot-response-with-adaptive-card) Fügen Sie eine adaptive Karte direkt in die Unterhaltung ein.
* [Anfordern der Benutzerauthentifizierung](~/messaging-extensions/how-to/add-authentication.md)
* [Anfordern einer zusätzlichen Konfiguration durch den Benutzer](~/messaging-extensions/how-to/add-configuration-page.md)

Für die Authentifizierung oder Konfiguration wird der ursprüngliche Aufruf, nachdem der Benutzer den Fluss abgeschlossen hat, erneut an ihren Webdienst gesendet. Die folgende Tabelle zeigt, welche Arten von Antworten basierend auf dem Aufrufspeicherort der `commandContext` Messagingerweiterung verfügbar sind: 

|Antworttyp | compose | Befehlsleiste | message |
|--------------|:-------------:|:-------------:|:---------:|
|Kartenantwort | x | x | x |
|Ein weiteres Aufgabenmodul | x | x | x |
|Bot mit adaptiver Karte | x |  | x |
| Keine Antwort | x | x | x |

## <a name="the-submitaction-invoke-event"></a>Das submitAction -Aufrufereignis

Beispiele für den Empfang der aufgerufenen Nachricht sind:

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

# <a name="json"></a>[Json](#tab/json)

Dies ist ein Beispiel für das JSON-Objekt, das Sie erhalten. Der `commandContext` Parameter gibt an, von wo ihre Messagingerweiterung ausgelöst wurde. Das Objekt enthält die Felder im Formular als Parameter und die vom `data` Benutzer übermittelten Werte. Das hier gezeigte JSON-Objekt wird verkürzt, um die relevantesten Felder zu markieren.

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

Am häufigsten wird auf die Anforderung mit einer Karte reagiert, die in den Bereich zum Verfassen `composeExtension/submitAction` von Nachrichten eingefügt wird. Der Benutzer kann dann auswählen, ob die Karte an die Unterhaltung übermittelt werden soll. Weitere Informationen zur Verwendung von Karten finden Sie unter [Karten und Kartenaktionen.](~/task-modules-and-cards/cards/cards-actions.md)

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

# <a name="json"></a>[Json](#tab/json)

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

Sie können auf das Ereignis mit einem `submitAction` zusätzlichen Aufgabenmodul reagieren. Dies kann hilfreich sein, wenn:

* Sie müssen große Mengen von Informationen sammeln.
* Wenn Sie dynamisch ändern müssen, welche Informationen Basierend auf Benutzereingaben gesammelt werden
* Wenn Sie die vom Benutzer übermittelten Informationen überprüfen und das Formular möglicherweise erneut mit einer Fehlermeldung senden müssen, wenn ein Fehler auftritt. 

Die Methode für die Antwort ist identisch mit der [Antwort auf das ursprüngliche `fetchTask` Ereignis.](~/messaging-extensions/how-to/action-commands/create-task-module.md) Wenn Sie das Bot Framework SDK verwenden, werden dieselben Ereignisauslöser für beide Absendenaktionen ausgelöst. Dies bedeutet, dass Sie Logik hinzufügen müssen, die die richtige Antwort bestimmt.

## <a name="bot-response-with-adaptive-card"></a>Botantwort mit adaptiver Karte

>[!Note]
>Dieser Fluss erfordert, dass Sie das Objekt zu Ihrem App-Manifest hinzufügen und den erforderlichen Bereich für `bot` den Bot definiert haben. Verwenden Sie die gleiche ID wie Ihre Messagingerweiterung für Ihren Bot.

Sie können auch auf die Absendeaktion reagieren, indem Sie mit einem Bot eine Nachricht mit einer adaptiven Karte in den Kanal einfügen. Der Benutzer kann eine Vorschau der Nachricht anzeigen, bevor er sie übermittelt, und sie möglicherweise auch bearbeiten oder mit ihr interagieren. Dies kann sehr nützlich sein in Szenarien, in denen Sie Informationen von Ihren Benutzern sammeln, bevor Sie eine adaptive Kartenantwort erstellen, oder wenn Sie die Karte aktualisieren, nachdem jemand damit interagiert hat. Das folgende Szenario zeigt, wie die App Polly diesen Fluss verwendet, um eine Umfrage zu konfigurieren, ohne die Konfigurationsschritte in der Kanalunterhaltung zu verwenden:

1. Der Benutzer wählt die Messagingerweiterung aus, um das Aufgabenmodul auszulösen.
2. Der Benutzer konfiguriert die Abfrage mit dem Aufgabenmodul.
3. Nach dem Übermitteln des Aufgabenmoduls verwendet die App die bereitgestellten Informationen, um die Umfrage als adaptive Karte zu erstellen, und sendet sie als Antwort `botMessagePreview` an den Client.
4. Der Benutzer kann dann eine Vorschau der Nachricht mit der adaptiven Karte anzeigen, bevor der Bot sie in den Kanal einf?en. Wenn die App noch kein Mitglied des Kanals ist, wird sie durch Auswahl `Send` der Option addiert.
   1. Der Benutzer kann auch die Nachricht auswählen, die sie an das `Edit` ursprüngliche Aufgabenmodul zurückgibt.
5. Die Interaktion mit der adaptiven Karte ändert die Nachricht, bevor sie gesendet wird.
6. Nachdem der Benutzer den `Send` Bot ausgewählt hat, wird die Nachricht an den Kanal gesendet.

### <a name="respond-to-initial-submit-action"></a>Reagieren auf die erste Absendenaktion

Um diesen Fluss zu aktivieren, sollte Ihr Aufgabenmodul auf die ursprüngliche Nachricht mit einer Vorschau der Karte antworten, die der Bot `composeExtension/submitAction` an den Kanal sendet. Dies gibt dem Benutzer die Möglichkeit, die Karte vor dem Senden zu überprüfen, und auch zu versuchen, Ihren Bot in der Unterhaltung zu installieren, wenn er noch nicht installiert ist.

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

# <a name="json"></a>[Json](#tab/json)

>[!Note]
>Der `activityPreview` muss eine Aktivität mit genau `message` 1 adaptiver Kartenanlage enthalten. Der `<< Card Payload >>` Wert ist ein Platzhalter für die Karte, die Sie senden möchten.

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

### <a name="the-botmessagepreview-send-and-edit-events"></a>Die BotMessagePreview-Sende- und -Bearbeitungsereignisse

Ihre Nachrichtenerweiterung muss jetzt auf zwei neue Varianten des Aufrufs `composeExtension/submitAction` reagieren, wobei und `value.botMessagePreviewAction = "send"` `value.botMessagePreviewAction = "edit"` .

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

# <a name="json"></a>[Json](#tab/json)

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

### <a name="respond-to-botmessagepreview-edit"></a>Reagieren auf die Bearbeitung von "botMessagePreview"

Wenn der Benutzer die Karte vor dem Senden bearbeitet, indem er auf die Schaltfläche **"Bearbeiten"** klickt, erhalten Sie einen `composeExtension/submitAction` Aufruf mit `value.botMessagePreviewAction = edit` . Sie sollten in der Regel antworten, indem Sie das Aufgabenmodul zurückgeben, das Sie als Reaktion auf den ersten Aufruf gesendet haben, `composeExtension/fetchTask` der die Interaktion begonnen hat. Dadurch kann der Benutzer den Prozess durch erneutes Eingeben der ursprünglichen Informationen starten. Verwenden Sie die verfügbaren Informationen, um das Aufgabenmodul vorab zu füllen, damit der Benutzer nicht alle Informationen von Grund auf ausfüllen muss.

Siehe ["Reagieren auf das ursprüngliche `fetchTask` Ereignis".](~/messaging-extensions/how-to/action-commands/create-task-module.md)

### <a name="respond-to-botmessagepreview-send"></a>Reagieren auf das Senden von botMessagePreview

Nachdem der Benutzer die Schaltfläche **"Senden"** ausgewählt hat, erhalten Sie einen `composeExtension/submitAction` Aufruf mit `value.botMessagePreviewAction = send` . Ihr Webdienst muss eine proaktive Nachricht mit der adaptiven Karte erstellen und an die Unterhaltung senden und auch auf den Aufruf antworten.

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

# <a name="json"></a>[Json](#tab/json)

Sie erhalten eine neue `composeExtension/submitAction` Nachricht ähnlich der folgenden:

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

### <a name="user-attribution-for-bots-messages"></a>Benutzerzuschreibung für Bots-Nachrichten 

In Szenarien, in denen ein Bot Nachrichten im Auftrag eines Benutzers sendet, kann das Zuweisen der Nachricht an diesen Benutzer bei der Interaktion hilfreich sein und einen natürlicheren Interaktionsfluss präsentieren. Mit diesem Feature können Sie eine Nachricht von Ihrem Bot einem Benutzer enannen, in dessen Namen sie gesendet wurde.

In der folgenden Abbildung befindet sich auf der  linken Seite eine Kartennachricht, die von einem  Bot ohne Benutzerzuschreibung gesendet wird, und rechts ist eine Karte, die von einem Bot mit Benutzerzuschreibung gesendet wird.

![Screenshot](../../../assets/images/messaging-extension/user-attribution-bots.png)

Um die Benutzerzuschreibung in Teams zu verwenden, müssen Sie die Erwähnungsentität zu Ihrer Nutzlast hinzufügen, die `OnBehalfOf` `ChannelData` an Teams gesendet `Activity` wird.

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

# <a name="json"></a>[Json](#tab/json-1)

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

Der folgende Abschnitt enthält eine Beschreibung der Entitäten im `OnBehalfOf` Array:

#### <a name="details-of--onbehalfof-entity-schema"></a>Details zum  `OnBehalfOf` Entitätsschema

|Feld|Typ|Beschreibung|
|:---|:---|:---|
|`itemId`|Ganze Zahl|Sollte 0 sein|
|`mentionType`|Zeichenfolge|Sollte "Person" sein|
|`mri`|Zeichenfolge|MrI (Message Resource Identifier) der Person, in deren Namen die Nachricht gesendet wird. Der Name des Nachrichtensenders würde als " über " \<user\> \<bot name\> angezeigt.|
|`displayName`|Zeichenfolge|Name der Person. Wird als Fallback verwendet, wenn die Namensauflösung nicht verfügbar ist.|
  
## <a name="next-steps"></a>Nächste Schritte

Hinzufügen eines Suchbefehls

* [Definition von Suchbefehlen](~/messaging-extensions/how-to/search-commands/define-search-command.md)

[!include[messaging-extension-learn-more](~/includes/messaging-extensions/learn-more.md)]
