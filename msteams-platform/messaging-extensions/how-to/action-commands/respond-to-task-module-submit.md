---
title: Reagieren auf die Absendenaktion des Aufgabenmoduls
author: clearab
description: Beschreibt, wie sie auf die Aktion zum Übermitteln des Aufgabenmoduls über einen Befehl für die Messagingerweiterungsaktion reagieren.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: fecc0ace5f767da3764529a9e8a590b37e547bb0
ms.sourcegitcommit: 1ce74ed167bb81bf09f7f6f8d518093efafb549e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2021
ms.locfileid: "50827942"
---
# <a name="respond-to-the-task-module-submit-action"></a>Reagieren auf die Absendenaktion des Aufgabenmoduls

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Nachdem ein Benutzer das Aufgabenmodul übermittelt hat, empfängt ihr Webdienst eine Aufrufnachricht mit der Befehls-ID `composeExtension/submitAction` und den Parameterwerten. Ihre App hat fünf Sekunden Zeit, um auf den  Aufruf zu reagieren, andernfalls erhält der Benutzer eine Fehlermeldung Nicht erreichbar, und eine Antwort auf den Aufruf wird vom Teams-Client ignoriert.

Sie haben die folgenden Optionen, um zu antworten:

* Keine Antwort – Sie können die Submit-Aktion verwenden, um einen Prozess in einem externen System auszulösen, und dem Benutzer kein Feedback geben. Dies kann für lange laufende Prozesse nützlich sein, und Sie können feedback auf andere Weise (z. B. mit einer proaktiven [Nachricht) bereitstellen.](~/bots/how-to/conversations/send-proactive-messages.md)
* [Ein weiteres Aufgabenmodul:](#respond-with-another-task-module) Sie können im Rahmen einer mehrstufigen Interaktion mit einem zusätzlichen Aufgabenmodul antworten.
* [Kartenantwort:](#respond-with-a-card-inserted-into-the-compose-message-area) Sie können mit einer Karte antworten, mit der der Benutzer dann interagieren und/oder in eine Nachricht einfügen kann.
* [Adaptive Karte vom Bot](#bot-response-with-adaptive-card) – Fügen Sie eine adaptive Karte direkt in die Unterhaltung ein.
* [Anfordern der Benutzerauthentifizierung](~/messaging-extensions/how-to/add-authentication.md)
* [Anfordern, dass der Benutzer eine zusätzliche Konfiguration bereitstellen kann](~/messaging-extensions/how-to/add-configuration-page.md)

Für die Authentifizierung oder Konfiguration wird der ursprüngliche Aufruf nach Abschluss des Datenflusses erneut an Den Webdienst gesendet. Die folgende Tabelle zeigt, welche Arten von Antworten basierend auf dem Aufrufspeicherort der `commandContext` Messagingerweiterung verfügbar sind: 

|Antworttyp | compose | Befehlsleiste | message |
|--------------|:-------------:|:-------------:|:---------:|
|Kartenantwort | x | x | x |
|Ein weiteres Aufgabenmodul | x | x | x |
|Bot mit adaptiver Karte | x |  | x |
| Keine Antwort | x | x | x |

> [!NOTE]
> * Wenn Sie **Action.Submit** through ME-Karten auswählen, sendet sie aufrufaktivität mit dem Namen **composeExtension**, wobei der Wert der üblichen Nutzlast entspricht.
> * Wenn Sie **Action.Submit** through conversation auswählen, erhalten Sie Nachrichtenaktivität mit dem Namen **onCardButtonClicked**, wobei der Wert der üblichen Nutzlast entspricht.

## <a name="the-submitaction-invoke-event"></a>Das submitAction-Aufrufereignis

Beispiele für den Empfang der aufrufenden Nachricht sind:

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

Dies ist ein Beispiel für das JSON-Objekt, das Sie erhalten. Der `commandContext` Parameter gibt an, von wo ihre Messagingerweiterung ausgelöst wurde. Das Objekt enthält die Felder im Formular als Parameter und die `data` vom Benutzer übermittelten Werte. Das hier gezeigte JSON-Objekt wird verkürzt, um die relevantesten Felder zu markieren.

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

## <a name="respond-with-a-card-inserted-into-the-compose-message-area"></a>Antworten mit einer Karte, die in den Bereich "Verfassen von Nachrichten" eingefügt wurde

Die häufigste Möglichkeit, auf die Anforderung zu reagieren, ist eine Karte, die in den Bereich "Verfassen `composeExtension/submitAction` von Nachrichten" eingefügt wird. Der Benutzer kann dann die Karte an die Unterhaltung übermitteln. Weitere Informationen zum Verwenden von Karten finden Sie [unter Karten und Kartenaktionen](~/task-modules-and-cards/cards/cards-actions.md).

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

## <a name="respond-with-another-task-module"></a>Reagieren mit einem anderen Aufgabenmodul

Sie können auf das Ereignis mit einem `submitAction` zusätzlichen Aufgabenmodul reagieren. Dies kann nützlich sein, wenn:

* Sie müssen große Mengen von Informationen sammeln.
* Wenn Sie die von Ihnen gesammelten Informationen basierend auf Benutzereingaben dynamisch ändern müssen
* Wenn Sie die vom Benutzer übermittelten Informationen überprüfen und das Formular möglicherweise erneut mit einer Fehlermeldung senden müssen, wenn etwas falsch ist. 

Die Methode für die Antwort ist identisch mit der [Antwort auf das ursprüngliche `fetchTask` Ereignis](~/messaging-extensions/how-to/action-commands/create-task-module.md). Wenn Sie das Bot Framework SDK verwenden, werden für beide Absendenaktionen dieselben Ereignisauslöser ausgelöst. Dies bedeutet, dass Sie Logik hinzufügen müssen, die die richtige Antwort bestimmt.

## <a name="bot-response-with-adaptive-card"></a>Botantwort mit adaptiver Karte

>[!Note]
>Dieser Fluss erfordert, dass Sie das Objekt zu Ihrem App-Manifest hinzufügen und den erforderlichen Bereich für `bot` den Bot definiert haben. Verwenden Sie die gleiche ID wie Ihre Messagingerweiterung für Ihren Bot.

Sie können auch auf die Submit-Aktion reagieren, indem Sie eine Nachricht mit einer adaptiven Karte mit einem Bot in den Kanal einfügen. Der Benutzer kann eine Vorschau der Nachricht anzeigen, bevor er sie übermittelt, und möglicherweise auch bearbeiten oder damit interagieren. Dies kann sehr nützlich sein in Szenarien, in denen Sie Informationen von Ihren Benutzern sammeln, bevor Sie eine adaptive Kartenantwort erstellen, oder wenn Sie die Karte aktualisieren, nachdem jemand mit ihr interagiert hat. Das folgende Szenario zeigt, wie die App Polly diesen Fluss verwendet, um eine Abfrage zu konfigurieren, ohne die Konfigurationsschritte in die Kanalunterhaltung zu verwenden:

1. Der Benutzer wählt die Messagingerweiterung aus, um das Aufgabenmodul auszulösen.
2. Der Benutzer konfiguriert die Abfrage mit dem Aufgabenmodul.
3. Nach dem Übermitteln des Aufgabenmoduls verwendet die App die bereitgestellten Informationen, um die Abfrage als adaptive Karte zu erstellen, und sendet sie als Antwort `botMessagePreview` an den Client.
4. Der Benutzer kann dann eine Vorschau der adaptiven Kartennachricht anzeigen, bevor der Bot sie in den Kanal einfüge. Wenn die App nicht bereits Mitglied des Kanals ist, wird sie durch Auswahl `Send` der App ergänzt.
   1. Der Benutzer kann auch die Nachricht `Edit` auswählen, die sie an das ursprüngliche Aufgabenmodul zurückgibt.
5. Durch die Interaktion mit der adaptiven Karte wird die Nachricht vor dem Senden geändert.
6. Nachdem der Benutzer den `Send` Bot ausgewählt hat, wird die Nachricht an den Kanal gesendet.

### <a name="respond-to-initial-submit-action"></a>Reagieren auf erste Absendenaktion

Um diesen Fluss zu aktivieren, sollte Ihr Aufgabenmodul auf die anfängliche Nachricht mit einer Vorschau der Karte antworten, die der Bot an `composeExtension/submitAction` den Kanal sendet. Dies gibt dem Benutzer die Möglichkeit, die Karte vor dem Senden zu überprüfen und auch zu versuchen, den Bot in der Unterhaltung zu installieren, wenn er noch nicht installiert ist.

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

### <a name="respond-to-botmessagepreview-edit"></a>Reagieren auf botMessagePreview-Bearbeitung

Wenn der Benutzer die Karte vor dem Senden bearbeitet, indem er die Schaltfläche **Bearbeiten** aus wählt, erhalten Sie einen `composeExtension/submitAction` Aufruf mit `value.botMessagePreviewAction = edit` . Sie sollten in der Regel antworten, indem Sie das Aufgabenmodul zurückgeben, das Sie als Antwort auf den anfänglichen Aufruf gesendet haben, `composeExtension/fetchTask` der mit der Interaktion begonnen hat. Auf diese Weise kann der Benutzer den Prozess durch erneutes Eingeben der ursprünglichen Informationen starten. Verwenden Sie die verfügbaren Informationen, um das Aufgabenmodul vorab zu füllen, damit der Benutzer nicht alle Informationen von Grund auf ausfüllen muss.

Weitere [Informationen finden Sie unter Antworten auf das anfängliche `fetchTask` Ereignis](~/messaging-extensions/how-to/action-commands/create-task-module.md).

### <a name="respond-to-botmessagepreview-send"></a>Reagieren auf botMessagePreview send

Nachdem der Benutzer die **Schaltfläche** Senden ausgewählt hat, erhalten Sie einen Aufruf mit `composeExtension/submitAction` `value.botMessagePreviewAction = send` . Ihr Webdienst muss eine proaktive Nachricht mit der adaptiven Karte an die Unterhaltung erstellen und senden und auch auf den Aufruf antworten.

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

Sie erhalten eine neue `composeExtension/submitAction` Nachricht wie die folgende:

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

In Szenarien, in denen ein Bot Nachrichten im Auftrag eines Benutzers sendet, kann das Zuweisen der Nachricht an diesen Benutzer bei der Interaktion helfen und einen natürlicheren Interaktionsfluss präsentieren. Mit diesem Feature können Sie einer Benutzerin, in deren Auftrag sie gesendet wurde, eine Nachricht von Ihrem Bot entributen.

In der folgenden Abbildung ist links eine Kartennachricht, die von einem Bot ohne Benutzerzuschreibung  gesendet wird, und rechts eine Karte, die von einem Bot mit Benutzerzuschreibung gesendet wird. 

![Screenshot](../../../assets/images/messaging-extension/user-attribution-bots.png)

Um die Benutzerzuschreibung in Teams zu verwenden, müssen Sie die Erwähnungsentität zu Ihrer Nutzlast hinzufügen, `OnBehalfOf` die an Teams gesendet `ChannelData` `Activity` wird.

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

#### <a name="details-of--onbehalfof-entity-schema"></a>Details des  `OnBehalfOf` Entitätsschemas

|Feld|Typ|Beschreibung|
|:---|:---|:---|
|`itemId`|Ganze Zahl|Sollte 0 sein|
|`mentionType`|String|Sollte "Person" sein|
|`mri`|String|MrI (Message Resource Identifier) der Person, in deren Auftrag die Nachricht gesendet wird. Der Name des Absenders der Nachricht würde als " über " \<user\> \<bot name\> angezeigt.|
|`displayName`|String|Name der Person. Wird als Fallback verwendet, wenn die Namensauflösung nicht verfügbar ist.|
  
## <a name="next-steps"></a>Nächste Schritte

Hinzufügen eines Suchbefehls

* [Definition von Suchbefehlen](~/messaging-extensions/how-to/search-commands/define-search-command.md)

[!include[messaging-extension-learn-more](~/includes/messaging-extensions/learn-more.md)]
