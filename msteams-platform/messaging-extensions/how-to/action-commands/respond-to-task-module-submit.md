---
title: Reagieren auf die Aufgabe Modul Submit-Aktion
author: clearab
description: Beschreibt, wie auf die Aufgabenmodul Aktion über einen Aktionsbefehl für die Nachrichten Erweiterung reagiert wird.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: cc62bd6643fad9b3f2054d6595dd509b75c59680
ms.sourcegitcommit: d0ca6a4856ffd03d197d47338e633126723fa78a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2020
ms.locfileid: "45137661"
---
# <a name="respond-to-the-task-module-submit-action"></a>Reagieren auf die Aufgabe Modul Submit-Aktion

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Sobald ein Benutzer das Aufgabenmodul übermittelt hat, erhält der Webdienst eine `composeExtension/submitAction` Invoke-Meldung mit den festgelegten Befehls-ID-und Parameterwerten. Ihre APP hat fünf Sekunden Zeit, um auf den Aufruf zu reagieren, andernfalls erhält der Benutzer die Fehlermeldung "die APP kann nicht erreicht werden", und jede Antwort auf die Invoke wird vom Microsoft Teams-Client ignoriert.

Sie haben die folgenden Optionen für die Antwort.

* Keine Antwort: Sie können die Submit-Aktion verwenden, um einen Prozess in einem externen System auszulösen und kein Feedback für den Benutzer bereitzustellen. Dies kann für langwierige Prozesse nützlich sein, und Sie können auswählen, dass Sie Feedback auf andere Weise bereitstellen möchten (beispielsweise mit einer [proaktiven Nachricht](~/bots/how-to/conversations/send-proactive-messages.md).
* [Ein weiterer Aufgabenmodul](#respond-with-another-task-module) -Sie können mit einem zusätzlichen Aufgabenmodul als Teil einer mehrstufigen Interaktion Antworten.
* [Karten Antwort](#respond-with-a-card-inserted-into-the-compose-message-area) : Sie können mit einer Karte Antworten, mit der der Benutzer interagieren und/oder in eine Nachricht einfügen kann.
* [Adaptive Karte von bot](#bot-response-with-adaptive-card) – fügen Sie eine Adaptive Karte direkt in die Unterhaltung ein.
* [Anfordern der Authentifizierung durch den Benutzer](~/messaging-extensions/how-to/add-authentication.md)
* [Anforderung des Benutzers zur Bereitstellung zusätzlicher Konfiguration](~/messaging-extensions/how-to/add-configuration-page.md)

Die folgende Tabelle zeigt, welche Arten von Antworten basierend auf dem Aufruf Speicherort ( `commandContext` ) der Messaging Erweiterung zur Verfügung stehen. Wenn der Benutzer den Fluss abgeschlossen hat, wird der ursprüngliche Aufruf für die Authentifizierung oder Konfiguration erneut an den Webdienst gesendet.

|Antworttyp | Verfassen | Befehlsleiste | message |
|--------------|:-------------:|:-------------:|:---------:|
|Karten Antwort | x | x | x |
|Ein weiteres Aufgabenmodul | x | x | x |
|Bot mit adaptiver Karte | x |  | x |
| Keine Antwort | x | x | x |

## <a name="the-submitaction-invoke-event"></a>Das Submit-Aufrufereignis

Im folgenden finden Sie Beispiele für den Empfang der Invoke-Nachricht.

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

Dies ist ein Beispiel für das JSON-Objekt, das Sie erhalten werden. Der `commandContext` Parameter gibt an, woher Ihre Messaging-Erweiterung ausgelöst wurde. Das- `data` Objekt enthält die Felder auf dem Formular als Parameter und die Werte, die der Benutzer übermittelt hat. Das JSON-Objekt wird hier verkürzt, um die relevantesten Felder hervorzuheben.

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

## <a name="respond-with-a-card-inserted-into-the-compose-message-area"></a>Antworten mit einer im Nachrichtenbereich "Verfassen" eingefügten Karte

Die häufigste Möglichkeit zur Reaktion auf die `composeExtension/submitAction` Anforderung ist eine Karte, die in den Bereich zum Verfassen von Nachrichten eingefügt wird. Der Benutzer kann dann beschließen, die Karte an die Unterhaltung zu senden. Weitere Informationen zur Verwendung von Karten finden Sie unter [Cards and Card Actions](~/task-modules-and-cards/cards/cards-actions.md).

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionSubmitActionAsync(
  ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
    dynamic Data = JObject.Parse(action.Data.ToString());
    var response = new MessagingExtensionActionResponse
    {
        ComposeExtension = new MessagingExtensionResult
        {
            AttachmentLayout = "list",
            Type = "result",
        },
    };
    var card = new HeroCard
    {
        Title = Data["formField1"] as string,
        Subtitle = Data["formField2"]  as string,
        Text = Data["formField3"]  as string,
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

Sie können beschließen, auf das `submitAction` Ereignis mit einem zusätzlichen Aufgabenmodul zu reagieren. Dies kann hilfreich sein, wenn:

* Sie müssen große Mengen an Informationen sammeln.
* Wenn Sie die gesammelten Informationen dynamisch basierend auf der Benutzereingabe ändern müssen
* Wenn Sie die vom Benutzer übermittelten Informationen validieren und das Formular möglicherweise mit einer Fehlermeldung erneut senden müssen, wenn etwas nicht stimmt. 

Die Methode für die Antwort ist identisch mit der Reaktion [auf das anfängliche `fetchTask` Ereignis](~/messaging-extensions/how-to/action-commands/create-task-module.md). Wenn Sie das bot Framework SDK verwenden, wird für beide Submit-Aktionen dasselbe Ereignis ausgelöst. Dies bedeutet, dass Sie unbedingt Logik hinzufügen müssen, die die richtige Antwort bestimmt.

## <a name="bot-response-with-adaptive-card"></a>Bot-Antwort mit adaptiver Karte

>[!Note]
>Für diesen Fluss ist es erforderlich, dass Sie das `bot` Objekt Ihrem App-Manifest hinzufügen und dass Sie den erforderlichen Bereich für den bot definiert haben. Verwenden Sie dieselbe ID wie Ihre Messaging Erweiterung für Ihren bot.

Sie können auch auf die Submit-Aktion reagieren, indem Sie eine Nachricht mit einer adaptiven Karte in den Kanal mit einem bot einfügen. Der Benutzer kann die Nachricht in einer Vorschau anzeigen, bevor er ihn sendet, und möglicherweise auch mit ihm bearbeiten/interagieren. Dies kann in Szenarien hilfreich sein, in denen Sie Informationen von Ihren Benutzern sammeln müssen, bevor Sie eine Adaptive Karten Antwort erstellen, oder wenn Sie die Karte aktualisieren müssen, nachdem eine Person mit ihr interagiert. Das folgende Szenario zeigt, wie die APP Polly diesen Fluss verwendet, um eine Umfrage zu konfigurieren, ohne die Konfigurationsschritte in der Kanal Unterhaltung zu unterbinden.

1. Der Benutzer klickt auf die Messaging Erweiterung, um den Aufgabenmodul auszulösen.
2. Der Benutzer konfiguriert die Umfrage mit dem Aufgabenmodul.
3. Nach dem Senden des Aufgabenmoduls verwendet die APP die bereitgestellten Informationen, um die Umfrage als Adaptive Karte zu erstellen und sendet sie als `botMessagePreview` Antwort an den Client.
4. Der Benutzer kann dann eine Vorschau der adaptiven Karten Nachricht anzeigen, bevor der bot ihn in den Kanal einfügt. Wenn die APP noch kein Mitglied des Kanals ist, `Send` wird Sie durch Klicken hinzugefügt.
   1. Der Benutzer kann auch `Edit` die Nachricht auswählen, die Sie an das ursprüngliche Aufgabenmodul zurückgibt.
5. Bei der Interaktion mit der adaptiven Karte wird die Nachricht vor dem Senden geändert.
6. Nachdem der Benutzer `Send` auf den bot geklickt hat, sendet er die Nachricht an den Kanal.

### <a name="respond-to-initial-submit-action"></a>Reagieren auf die anfängliche Submit-Aktion

Um diesen Fluss zu aktivieren, sollte Ihr Aufgabenmodul auf die anfängliche `composeExtension/submitAction` Nachricht mit einer Vorschau der Karte Antworten, die der bot an den Kanal senden wird. Dies gibt dem Benutzer die Möglichkeit, die Karte vor dem senden zu überprüfen, und versucht außerdem, den bot in der Unterhaltung zu installieren, falls er noch nicht installiert ist.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionSubmitActionAsync(
  ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  dynamic Data = JObject.Parse(action.Data.ToString());
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
>Das `activityPreview` muss eine `message` Aktivität mit genau 1 adaptiver Karten Anlage enthalten. Der `<< Card Payload >>` Wert ist ein Platzhalter für die Karte, die Sie senden möchten.

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

### <a name="the-botmessagepreview-send-and-edit-events"></a>Das botMessagePreview-Ereignis zum Senden und bearbeiten

Die Nachrichten Erweiterung muss nun auf zwei neue Varianten des Invoke-Objektes reagieren `composeExtension/submitAction` , wobei `value.botMessagePreviewAction = "send"` und ist `value.botMessagePreviewAction = "edit"` .

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

### <a name="respond-to-botmessagepreview-edit"></a>Reagieren auf botMessagePreview Edit

Wenn der Benutzer entscheidet, die Karte vor dem senden zu bearbeiten, indem er auf die Schaltfläche **Bearbeiten** klickt, wird ein `composeExtension/submitAction` Invoke mit angezeigt `value.botMessagePreviewAction = edit` . Sie sollten in der Regel durch Zurückgeben des Aufgabenmoduls Antworten, das Sie als Antwort auf die anfängliche Invoke gesendet haben `composeExtension/fetchTask` , die die Interaktion begann. Dadurch kann der Benutzer den Prozess über die erneute Eingabe der ursprünglichen Informationen starten. Sie sollten auch die Informationen verwenden, die Sie jetzt zur Verfügung haben, um den Aufgabenmodul vorab aufzufüllen, damit der Benutzer nicht alle Informationen aus dem nichts ausfüllt.

Siehe [Antworten auf das anfängliche `fetchTask` Ereignis](~/messaging-extensions/how-to/action-commands/create-task-module.md).

### <a name="respond-to-botmessagepreview-send"></a>Auf botMessagePreview senden Antworten

Nachdem der Benutzer auf die Schaltfläche **senden** geklickt hat, wird ein `composeExtension/submitAction` Aufruf mit angezeigt `value.botMessagePreviewAction = send` . Ihr Webdienst muss eine proaktive Nachricht mit der adaptiven Karte an die Unterhaltung erstellen und senden und auch auf die Invoke Antworten.

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

Sie erhalten eine neue `composeExtension/submitAction` Nachricht, die der folgenden ähnlich ist.

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

In Szenarien, in denen ein bot Nachrichten im Auftrag eines Benutzers sendet, kann die Nachricht dem Benutzer mit Engagement helfen und einen natürlichen Interaktions Fluss präsentieren. Mit dieser Funktion können Sie eine Nachricht von Ihrem bot einem Benutzer zuordnen, in dessen Auftrag er gesendet wurde.

Im Bild unten links sehen Sie eine Karten Nachricht, die von einem bot *ohne* Benutzerzuordnung gesendet wurde, und auf der rechten Seite ist eine Karte, die von einem bot *mit* Benutzerzuordnung gesendet wird.

![Screenshot](../../../assets/images/messaging-extension/user-attribution-bots.png)

Um die Benutzerzuordnung in Microsoft Teams zu verwenden, müssen Sie die `OnBehalfOf` mention-Entität `ChannelData` in ihrer Nutzlast hinzufügen, die `Activity` an Teams gesendet wird.

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

Im folgenden finden Sie eine Beschreibung der Entitäten in der `OnBehalfOf` von-Array:

#### <a name="details-of--onbehalfof-entity-schema"></a>Details des `OnBehalfOf` Entitätsschemas

|Feld|Typ|Beschreibung|
|:---|:---|:---|
|`itemId`|Ganze Zahl|Sollte 0 sein.|
|`mentionType`|Zeichenfolge|Sollte "Person" sein|
|`mri`|Zeichenfolge|Nachrichten Ressourcenbezeichner (MRI) der Person, in deren Auftrag die Nachricht gesendet wird. Der Name des Nachrichtenabsenders wird als " \<user\> via \<bot name\> " angezeigt.|
|`displayName`|Zeichenfolge|Der Name der Person. Wird als Fallback verwendet, falls die Namensauflösung nicht verfügbar ist.|
  
## <a name="next-steps"></a>Nächste Schritte

Hinzufügen eines Suchbefehls

* [Definition von Suchbefehlen](~/messaging-extensions/how-to/search-commands/define-search-command.md)

[!include[messaging-extension-learn-more](~/includes/messaging-extensions/learn-more.md)]
