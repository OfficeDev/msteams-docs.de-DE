---
title: Auf die Aktion zum Absenden des Aufgabenmoduls reagieren
author: surbhigupta
description: Erfahren Sie, wie Sie mithilfe eines Aktionsbefehls für die Nachrichtenerweiterung mit proaktiver Nachricht auf die Aufgabenmodul-Sendeaktion reagieren. Definieren Sie Suchbefehle, und reagieren Sie auf Suchvorgänge.
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 827c939080aa2eff182115966351356b0d71e3a9
ms.sourcegitcommit: 75d0072c021609af33ce584d671f610d78b3aaef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2022
ms.locfileid: "68100483"
---
# <a name="respond-to-the-task-module-submit-action"></a>Auf die Aktion zum Absenden des Aufgabenmoduls reagieren

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

In diesem Dokument erfahren Sie, wie Ihre App auf Aktionsbefehle reagiert, z. B. auf die Aktion "Aufgabenmodul einreichen" des Benutzers.
Nachdem ein Benutzer das Aufgabenmodul abgeschickt hat, erhält Ihr Webdienst eine`composeExtension/submitAction`Aufrufnachricht mit der Befehls-ID und den Parameterwerten. Ihre App hat fünf Sekunden Zeit, um auf den Aufruf zu reagieren. Andernfalls erhält der Benutzer die Fehlermeldung **Kann die App nicht erreichen**, und jede Antwort auf den Aufruf wird vom Teams-Client ignoriert.

Sie haben die folgenden Möglichkeiten zu antworten:

* Keine Antwort: Verwenden Sie die Submit-Aktion, um einen Prozess in einem externen System auszulösen und dem Benutzer keine Rückmeldung zu geben. Es ist nützlich für lang andauernde Prozesse und um abwechselnd Feedback zu geben. Sie können z. B. Feedback mit einer [proaktiven Nachricht](~/bots/how-to/conversations/send-proactive-messages.md) geben.
* [Ein weiteres Aufgabenmodul](#respond-with-another-task-module): Sie können mit einem zusätzlichen Aufgabenmodul als Teil einer mehrstufigen Interaktion antworten.
* [Kartenantwort](#respond-with-a-card-inserted-into-the-compose-message-area): mit einer Karte antworten, mit der der Benutzer interagieren oder die er in eine Nachricht einfügen kann
* [Adaptive Karte vom Bot](#bot-response-with-adaptive-card): Fügen Sie eine adaptive Karte direkt in die Unterhaltung ein.
* [Fordern Sie den Benutzer auf, sich zu authentifizieren](~/messaging-extensions/how-to/add-authentication.md).
* [Fordern Sie den Benutzer auf, zusätzliche Konfigurationen bereitzustellen](~/get-started/first-message-extension.md).

Für die Authentifizierung oder Konfiguration wird der ursprüngliche Aufruf an Ihren Webdienst zurückgesendet, nachdem der Benutzer den Vorgang abgeschlossen hat. Die folgende Tabelle zeigt, welche Arten von Antworten verfügbar sind, basierend auf dem Aufrufspeicherort `commandContext` der Nachrichtenerweiterung:

|Antworttyp | Verfassen | Befehlsleiste | Message |
|--------------|:-------------:|:-------------:|:---------:|
|Kartenantwort | ✔️ | ✔️ | ✔️ |
|Ein weiteres Aufgabenmodul | ✔️ | ✔️ | ✔️ |
|Bot mit adaptiver Karte | ✔️ | ❌ | ✔️ |
| Keine Antwort | ✔️ | ✔️ | ✔️ |

> [!NOTE]
>
> * Wenn Sie **Action.Submit** über ME-Karten auswählen, wird eine Aufrufaktivität mit dem Namen **composeExtension** gesendet, wobei der Wert der üblichen Nutzlast entspricht.
> * Wenn Sie **Action.Submit** über ME-Karten auswählen, wird eine Aufrufaktivität mit dem Namen **composeExtension** gesendet, wobei der Wert der üblichen Nutzlast entspricht.

Wenn die App einen Unterhaltungs-Bot enthält, installieren Sie den Bot in der Unterhaltung, und laden Sie dann das Aufgabenmodul. Der Bot ist nützlich, um zusätzlichen Kontext für das Aufgabenmodul abzurufen. Informationen zum Installieren eines Konversationsbots finden Sie unter [Anfordern der Installation Ihres Konversationsbots](create-task-module.md#request-to-install-your-conversational-bot).

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

Dies ist ein Beispiel für das JSON-Objekt, das Sie erhalten. Der parameter `commandContext` gibt an, von wo ihre Nachrichtenerweiterung ausgelöst wurde. Das `data`Objekt enthält die Felder im Formular als Parameter und die Werte, die der Benutzer übermittelt hat. Das JSON-Objekt hebt die relevantesten Felder hervor.

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

## <a name="respond-with-a-card-inserted-into-the-compose-message-area"></a>Antworten mit einer Karte, die in den Nachrichtenbereich zum Verfassen eingefügt wurde

Die gängigste Möglichkeit, auf die `composeExtension/submitAction` Anforderung zu reagieren, besteht darin, dass eine Karte in den Nachrichtenbereich zum Verfassen eingefügt wird. Der Benutzer übergibt die Karte an das Gespräch. Weitere Informationen zur Verwendung von Karten finden Sie unter [Karten und Kartenaktionen](~/task-modules-and-cards/cards/cards-actions.md).

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

Sie können auswählen, dass Sie mit einem zusätzlichen Aufgabenmodul auf das ereignis `submitAction` reagieren möchten. Dies ist nützlich, wenn Sie es brauchen:

* Sammeln Sie große Mengen an Informationen.
* Ändern Sie die Informationssammlung dynamisch auf der Grundlage von Benutzereingaben.
* Validieren Sie die vom Benutzer eingegebenen Informationen und senden Sie das Formular mit einer Fehlermeldung erneut ab, wenn etwas nicht stimmt.

Die Antwortmethode ist identisch mit [der Reaktion auf das ursprüngliche `fetchTask` Ereignis](~/messaging-extensions/how-to/action-commands/create-task-module.md). Wenn Sie das Bot Framework SDK verwenden, wird das gleiche Ereignis für beide Übermittlungsaktionen ausgelöst. Damit dies funktioniert, müssen Sie Logik hinzufügen, die die richtige Antwort bestimmt.

## <a name="bot-response-with-adaptive-card"></a>Bot-Antwort mit Adaptiver Karte

> [!NOTE]
> Die Voraussetzung für das Abrufen der Botantwort mit einer adaptiven Karte ist, dass Sie das `bot` -Objekt ihrem App-Manifest hinzufügen und den erforderlichen Bereich für den Bot definieren müssen. Verwenden Sie dieselbe ID wie Ihre Nachrichtenerweiterung für Ihren Bot.

Sie können auch auf die `submitAction` reagieren, indem Sie eine Nachricht mit einer adaptiven Karte mit einem Bot in den Kanal einfügen. Der Benutzer kann eine Vorschau der Nachricht anzeigen, bevor er sie übermittelt. Dies ist in Szenarien nützlich, in denen Sie Informationen von den Benutzern sammeln, bevor Sie eine adaptive Kartenantwort erstellen, oder wenn Sie die Karte aktualisieren, nachdem jemand mit ihr interagiert hat.

Das folgende Szenario zeigt, wie die App Polly eine Umfrage konfiguriert, ohne die Konfigurationsschritte in die Kanalunterhaltung einzubeziehen:

So konfigurieren Sie die Umfrage:

1. Der Benutzer wählt die Nachrichtenerweiterung aus, um das Aufgabenmodul aufzurufen.
1. Der Benutzer konfiguriert die Abfrage mit dem Aufgabenmodul.
1. Nach dem Übermitteln des Aufgabenmoduls verwendet die App die bereitgestellten Informationen, um die Abstimmung als adaptive Karte zu erstellen, und sendet sie als `botMessagePreview` Antwort an den Client.
1. Der Benutzer kann dann eine Vorschau der Adaptive Card-Nachricht anzeigen, bevor der Bot sie in den Kanal einfügt. Wenn die App kein Mitglied des Kanals ist, wählen Sie diese Option `Send` aus, um sie hinzuzufügen.

    > [!NOTE]
    >
    > * Die Benutzer können auch auswählen, dass `Edit`die Nachricht werden soll, wodurch sie an das ursprüngliche Aufgabenmodul zurückgegeben werden.
    > * Durch die Interaktion mit der adaptiven Karte wird die Nachricht vor dem Senden geändert.
    >
1. Nachdem der Benutzer die Option ausgewählt hat `Send`, sendet der Bot die Nachricht an den Kanal.

## <a name="respond-to-initial-submit-action"></a>Reagieren auf erste Übermittlungsaktion

Ihr Aufgabenmodul muss auf die anfängliche `composeExtension/submitAction` Nachricht mit einer Vorschau der Karte reagieren, die der Bot an den Kanal sendet. Der Benutzer kann die Karte vor dem Senden überprüfen und versuchen, Ihren Bot in der Unterhaltung zu installieren, wenn der Bot bereits installiert ist.

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
>
> * Die `activityPreview` muss eine `message` Aktivität mit genau einer Adaptive Card-Anlage enthalten. Der `<< Card Payload >>` Wert ist ein Platzhalter für die Karte, die Sie senden möchten.

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

Die Nachrichtenerweiterung muss auf zwei neue Typen des `composeExtension/submitAction` -Aufrufs reagieren, wobei `value.botMessagePreviewAction = "send"`und `value.botMessagePreviewAction = "edit"`.

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

### <a name="respond-to-botmessagepreview-edit"></a>Reagieren auf botMessagePreview-Bearbeitung

Wenn der Benutzer die Karte vor dem Versenden bearbeitet, indem er **Bearbeiten** wählt, erhalten Sie eine`composeExtension/submitAction` Aufforderung mit `value.botMessagePreviewAction = edit`. Antworten Sie, indem Sie das von Ihnen gesendete Aufgabenmodul als Reaktion auf die anfängliche `composeExtension/fetchTask` Aufrufen zurückgeben, die die Interaktion gestartet haben. Dadurch kann der Benutzer den Prozess starten, indem die ursprünglichen Informationen erneut eingegeben werden. Verwenden Sie die verfügbaren Informationen, um das Aufgabenmodul so zu aktualisieren, dass der Benutzer nicht alle Informationen von Grund auf neu ausfüllen muss.
Weitere Informationen zum Reagieren auf das erste `fetchTask` Ereignis finden Sie unter [Reagieren auf das erste `fetchTask` Ereignis](~/messaging-extensions/how-to/action-commands/create-task-module.md).

### <a name="respond-to-botmessagepreview-send"></a>Auf botMessagePreview-Sendevorgang antworten

Nachdem der Benutzer " **Senden**" ausgewählt hat, erhalten Sie einen `composeExtension/submitAction` Aufruf mit `value.botMessagePreviewAction = send`. Ihr Webdienst muss eine proaktive Nachricht mit der adaptiven Karte erstellen und an die Konversation senden und auch auf den Aufruf antworten.

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

Sie erhalten eine neue `composeExtension/submitAction` Meldung ähnlich der folgenden:

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

In Szenarien, in denen ein Bot Nachrichten im Namen eines Benutzers sendet, hilft das Attributieren der Nachricht an diesen Benutzer bei der Interaktion und veranschaulicht einen natürlicheren Interaktionsfluss. Mit diesem Feature können Sie eine Nachricht von Ihrem Bot einem Benutzer zuordnen, in dessen Auftrag er gesendet wurde.

In der folgenden Abbildung befindet sich auf der linken Seite eine Kartennachricht, die von einem Bot ohne Benutzerzuordnung gesendet wird, und auf der rechten Seite ist eine Karte, die von einem Bot mit Benutzerzuordnung gesendet wird.

:::image type="content" source="../../../assets/images/messaging-extension/user-attribution-bots.png" alt-text="Benutzerzuordnungsbots":::

Um die Benutzerzuordnung in Teams zu verwenden, müssen Sie die Entität " `OnBehalfOf` Erwähnen" zu `ChannelData` in Ihrer `Activity` Nutzlast hinzufügen, die an Teams gesendet wird.

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

#### <a name="details-of--onbehalfof-entity-schema"></a>Details  `OnBehalfOf` Entitätsschemas

Der folgende Abschnitt enthält eine Beschreibung der Entitäten im `OnBehalfOf` Array:

|Feld|Typ|Beschreibung|
|:---|:---|:---|
|`itemId`|Ganzzahl|Beschreibt die Identifizierung des Elements. Der Wert muss `0`sein.|
|`mentionType`|Zeichenfolge|Beschreibt die Erwähnung einer "Person".|
|`mri`|Zeichenfolge|Nachrichtenressourcenbezeichner (MESSAGE Resource Identifier, MRI) der Person, in deren Auftrag die Nachricht gesendet wird. Der Absendername der Nachricht wird als "\<user\> bis \<bot name\>" angezeigt.|
|`displayName`|Zeichenfolge|Name der Person. Wird als Fallback für den Fall verwendet, dass die Namensauflösung nicht verfügbar ist.|
  
## <a name="code-sample"></a>Codebeispiel

| Beispielname           | Beschreibung | .NET    | Node.js   |
|:---------------------|:--------------|:---------|:--------|
|Teams-Nachrichtenerweiterungen – Aktion| Beschreibt, wie Aktionsbefehle definiert werden, ein Aufgabenmodul erstellt und auf Aufgabenmodul-Sendeaktionen reagiert wird. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) |
|Teams Nachrichtenerweiterungen – Suche   |  Beschreibt, wie Suchbefehle definiert und auf Suchvorgänge reagiert wird.        |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)|

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Definition von Suchbefehlen](~/messaging-extensions/how-to/search-commands/define-search-command.md)

## <a name="see-also"></a>Siehe auch

[ Reagieren Sie auf den Suchbefehl ](~/messaging-extensions/how-to/search-commands/respond-to-search.md)
