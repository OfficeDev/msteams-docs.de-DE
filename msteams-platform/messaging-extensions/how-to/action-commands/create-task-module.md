---
title: Erstellen und Senden des Aufgabenmoduls
author: clearab
description: Vorgehensweise behandeln der anfänglichen Invoke-Aktion und Antworten mit einem Aufgabenmodul aus einem Aktions-Messaging-Erweiterungs Befehl
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: f5f96e71517d45f52d17d2d70c583ec1eec3babd
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674398"
---
# <a name="create-and-send-the-task-module"></a>Erstellen und Senden des Aufgabenmoduls

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Wenn Sie Ihr Aufgabenmodul nicht mit Parametern auffüllen, die in Ihrem App-Manifest definiert sind, müssen Sie das Aufgabenmodul erstellen, das den Benutzern angezeigt werden soll. Sie können entweder eine Adaptive Karte oder eine eingebettete Webansicht verwenden.

## <a name="the-initial-invoke-request"></a>Die anfängliche Invoke-Anforderung

Wenn Sie diese Methode verwenden, erhalten Sie `Activity` ein Objekt vom `composeExtension/fetchTask`Typ, und Sie müssen mit einem `task` Objekt Antworten, das entweder die Adaptive Karte oder eine URL zur eingebetteten Webansicht enthält. Zusätzlich zu den Eigenschaften der standardmäßigen bot-Aktivität enthält die anfängliche Invoke-Nutzlast die folgenden Anforderungs Metadaten:

|Eigenschaftenname|Zweck|
|---|---|
|`type`| Typ der Anforderung; muss sein `invoke`. |
|`name`| Der Typ des Befehls, der für den Dienst ausgestellt wird. Wird `composeExtension/fetchTask`. |
|`from.id`| Die ID des Benutzers, der die Anforderung gesendet hat. |
|`from.name`| Der Name des Benutzers, der die Anforderung gesendet hat. |
|`from.aadObjectId`| Azure Active Directory Objekt-ID des Benutzers, der die Anforderung gesendet hat. |
|`channelData.tenant.id`| Azure Active Directory Mandanten-ID. |
|`channelData.channel.id`| Kanal-ID (wenn die Anforderung in einem Kanal erfolgt ist). |
|`channelData.team.id`| Team-ID (wenn die Anforderung in einem Kanal erfolgt ist). |
|`value.commandId` | Enthält die ID des aufgerufenen Befehls. |
|`value.commandContext` | Der Kontext, der das Ereignis ausgelöst hat. Wird `compose`. |
|`value.context.theme` | Das Client Design des Benutzers, nützlich für die eingebettete Webansicht-Formatierung. `default`Ist `contrast` oder `dark`. |

### <a name="example-fetchtask-request"></a>Beispiel für eine fetchTask-Anforderung

# <a name="cnettabdotnet"></a>[C#-/.net](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionFetchTaskAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  //handle fetch task
}
```

# <a name="javascriptnodejstabjavascript"></a>[JavaScript/Node. js](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreviewBot extends TeamsActivityHandler {
  handleTeamsMessagingExtensionFetchTask(context, action) {
    //hand fetch task
  }
}
```

# <a name="jsontabjson"></a>[Json](#tab/json)

```json
{
  "name": "composeExtension/fetchTask",
  "type": "invoke",
  "timestamp": "2019-07-01T22:57:22.175Z",
  "localTimestamp": "2019-07-01T15:57:22.175-07:00",
  "id": "f:0123456878990178955",
  "channelId": "msteams",
  "serviceURL": "https://smba.trafficmanager.net/amer/",
  "from": {
    "id": "29:1test2GgHIa0DXzDT_OGwL5vSMZdAxDlGR7hYxZ6_JBVqHz2Zq9Nm44FUNWqHCdGBwHg8WrlFRsYrd0cCAS7dig",
    "name": "John Smith",
    "aadObjectId": "1234567d-1234-462a-8952-35b75f16f1e1"
  },
  "conversation": {
    "isGroup": true,
    "conversationType": "channel",
    "tenantId": "1234abcd-1234-12ab-12ab-35b75f16f1e1",
    "id": "19:83ed1d507cb5427c93495cf914326310@thread.skype"
  },
  "recipient": {
    "id": "28:049566e0-4401-4bcf-86a1-ce22082ce03a",
    "name": "mess"
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
    "channel": {
      "id": "19:83ab1d507cb5427c93495cf912345678@thread.skype"
    },
    "team": {
      "id": "19:83ab1d507cb5427c93495cf912345678@thread.skype"
    },
    "tenant": {
      "id": "1234abcd-1234-12ab-12ab-35b75f16f1e1"
    },
    "source": {
      "name": "compose"
    }
  },
  "value": {
    "commandId": "hello",
    "commandContext": "compose",
    "context": {
      "theme": "dark"
    }
  },
  "locale": "en-US"
}
```

* * *

## <a name="initial-invoke-request-from-a-message"></a>Anfängliche Invoke-Anforderung aus einer Nachricht

Wenn Ihr bot aus einer Nachricht anstatt aus dem verfassenbereich oder der Befehlsleiste aufgerufen wird, enthält `value` das Objekt in der anfänglichen Anforderung die Details der Nachricht, aus der Ihre Messaging-Erweiterung aufgerufen wurde. Ein Beispiel für dieses Objekt ist unten. Die `reactions` - `mentions` und-Arrays sind optional und werden nicht angezeigt, wenn in der ursprünglichen Nachricht keine Reaktionen oder Erwähnungen vorhanden sind.

# <a name="cnettabdotnet"></a>[C#-/.net](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionFetchTaskAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  var messageText = action.MessagePayload.Body.Content;
  var fromId = action.MessagePayload.From.User.Id;

  //finish handling the fetchTask
}
```

# <a name="javascriptnodejstabjavascript"></a>[JavaScript/Node. js](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
  handleTeamsMessagingExtensionFetchTask(context, action) {
    const messageText = action.messagePayload.body.content;

    //finish handling the fetchTask
  }
}
```

# <a name="jsontabjson"></a>[Json](#tab/json)

```json
{
  "name": "composeExtension/submitAction",
  "type": "invoke",
...
  "value": {
    "commandId": "setReminder",
    "commandContext": "message",
    "messagePayload": {
      "id": "1111111111",
      "replyToId": null,
      "createdDateTime": "2019-02-25T21:29:36.065Z",
      "lastModifiedDateTime": null,
      "deleted": false,
      "subject": "Message subject",
      "summary": null,
      "importance": "normal",
      "locale": "en-us",
      "body": {
        "contentType": "html",
        "content": "This is the message the messaging extension was invoked from."
    },
      "from": {
        "device": null,
        "conversation": null,
        "user": {
          "userIdentityType": "aadUser",
          "id": "wxyz12ab8-ab12-cd34-ef56-098abc123876",
          "displayName": "Jamie Smythe"
        },
        "application": null
      },
      "reactions": [
        {
          "reactionType": "like",
          "createdDateTime": "2019-02-25T22:40:40.806Z",
          "user": {
            "device": null,
            "conversation": null,
            "user": {
              "userIdentityType": "aadUser",
              "id": "qrst12346-ab12-cd34-ef56-098abc123876",
              "displayName": "Jim Brown"
            },
            "application": null
          }
        }
      ],
      "mentions": [
        {
          "id": 0,
          "mentionText": "Sarah",
          "mentioned": {
            "device": null,
            "conversation": null,
            "user": {
              "userIdentityType": "aadUser",
              "id": "ab12345678-ab12-cd34-ef56-098abc123876",
              "displayName": "Sarah"
            },
            "application": null
          }
        }
      ]
    }
  ...
```

* * *

## <a name="respond-to-the-fetchtask"></a>Antworten auf die fetchTask

Antworten Sie auf die Invoke-Anforderung `task` mit einem Objekt, das `taskInfo` entweder ein Objekt mit der adaptiven Karte oder die weburl oder eine einfache Zeichenfolgennachricht enthält.

|Eigenschaftenname|Zweck|
|---|---|
|`type`| Kann entweder `continue` zum Darstellen eines Formulars oder `message` für ein einfaches Popup-Objekt sein. |
|`value`| Entweder ein `taskInfo` Objekt für ein Formular oder ein `string` für eine Nachricht. |

Das Schema für das taskInfo-Objekt lautet:

|Eigenschaftenname|Zweck|
|---|---|
|`title`| Der Titel des Aufgabenmoduls.|
|`height`| Kann eine ganze Zahl (in Pixeln) oder `small`, `medium`, `large`sein.|
|`width`| Kann eine ganze Zahl (in Pixeln) oder `small`, `medium`, `large`sein.|
|`card`| Die Adaptive Karte, die das Formular definiert (sofern eine verwendet wird).
|`url`| Die URL, die innerhalb des Aufgabenmoduls als eingebettete Webansicht geöffnet werden soll.|
|`fallbackUrl`| Wenn ein Client das Feature "Aufgabenmodul" nicht unterstützt, wird diese URL in einer Browserregister Karte geöffnet. |

### <a name="with-an-adaptive-card"></a>Mit einer adaptiven Karte

Wenn Sie eine Adaptive Karte verwenden, müssen Sie mit einem `task` Objekt mit dem Objekt `value` Antworten, das eine Adaptive Karte enthält.

#### <a name="example-fetchtask-response-with-an-adaptive-card"></a>Beispiel für eine fetchTask-Antwort mit einer adaptiven Karte

# <a name="cnettabdotnet"></a>[C#-/.net](#tab/dotnet)

In diesem Beispiel wird das [AdaptiveCards-NuGet-Paket](https://www.nuget.org/packages/AdaptiveCards) zusätzlich zum bot Framework SDK verwendet.

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionFetchTaskAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  string placeholder = "Not invoked from message";

  if (action.MessagePayload != null)
  {
      var messageText = action.MessagePayload.Body.Content;
      var fromId = action.MessagePayload.From.User.Id;
      placeholder = "Invoked from message";
  }

  var response = new MessagingExtensionActionResponse()
  {
    Task = new TaskModuleContinueResponse()
    {
      Value = new TaskModuleTaskInfo()
      {
        Height = "small",
        Width = "small",
        Title = "Example task module",
        Card = new Attachment()
        {
          ContentType = AdaptiveCard.ContentType,
          Content = new AdaptiveCard("1.0")
          {
            Body = new List<AdaptiveElement>()
            {
              new AdaptiveTextInput() { Id = "FormField1", Placeholder = placeholder},
              new AdaptiveTextInput() { Id = "FormField2", Placeholder = "FormField2"},
              new AdaptiveTextInput() { Id = "FormField3", Placeholder = "FormField3"},
            },
            Actions = new List<AdaptiveAction>()
            {
              new AdaptiveSubmitAction()
              {
                Type = AdaptiveSubmitAction.TypeName,
                Title = "Submit",
              },
            },
          },
        },
      },
    },
  };
  return response;
}
```

# <a name="javascriptnodejstabjavascript"></a>[JavaScript/Node. js](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
    handleTeamsMessagingExtensionFetchTask(context, action) {
      const adaptiveCard = CardFactory.adaptiveCard({
        actions: [{
          data: { submitLocation: 'messagingExtensionFetchTask'},
          title: 'Submit',
          type: 'Action.Submit'
        }],
        body: [
          { text: 'Task Module', type: 'TextBlock', weight: 'bolder'},
          { type: 'TextBlock', text: 'Enter text for Question:' },
          { id: 'Question', placeholder: 'Question text here', type: 'Input.Text', value: userText },
          { type: 'TextBlock', text: 'Options for Question:' },
          { type: 'TextBlock', text: 'Is Multi-Select:' },
          {
            choices: [{ title: 'True', value: 'true' }, { title: 'False', value: 'false' }],
            id: 'MultiSelect',
            isMultiSelect: false,
            style: 'expanded',
            type: 'Input.ChoiceSet',
            value: isMultiSelect ? 'true' : 'false'
          },
          { id: 'Option1', placeholder: 'Option 1 here', type: 'Input.Text', value: option1 },
          { id: 'Option2', placeholder: 'Option 2 here', type: 'Input.Text', value: option2 }
        ],
        type: 'AdaptiveCard',
        version: '1.0'
      });

      return {
        task: {
          type: 'continue',
          value: {
            card: adaptiveCard,
            height: 450,
            title: 'Task Module Fetch Example',
            url: null,
            width: 500
          }
        }
      };
    }
}
```

# <a name="jsontabjson"></a>[Json](#tab/json)

```json
{
  "task": {
    "type": "continue",
    "value": {
      "card":
      {
        "type": "AdaptiveCard",
        "version": "1.0",
        "body": [
          {
            "type": "Input.Text",
            "placeholder": "FormField1",
            "id": "FormField1"
          },
          {
            "type": "Input.Text",
            "placeholder": "FormField2",
            "id": "FormField2"
          },
          {
            "type": "Input.Text",
            "placeholder": "FormField3",
            "id": "FormField3"
          },
          {
            "type": "ActionSet",
            "actions": [
              {
                "type": "Action.Submit",
                "title": "Action.Submit",
                "id": "submitAction"
              }
            ]
          }
        ],
        "$schema": "http://adaptivecards.io/schemas/adaptive-card.json"
      }
    }
  }
}
```

* * *

### <a name="with-an-embedded-web-view"></a>Mit einer eingebetteten Webansicht

Bei Verwendung einer eingebetteten Webansicht müssen Sie mit einem `task` Objekt mit dem `value` Objekt Antworten, das die URL zu dem Webformular enthält, das Sie laden möchten. Die Domänen einer beliebigen URL, die Sie laden möchten, müssen in dem `validDomains` Array im App-Manifest enthalten sein. Ausführliche Informationen zum Erstellen Ihrer eingebetteten Webansicht finden Sie in der [Dokumentation zum Aufgabenmodul](~/task-modules-and-cards/what-are-task-modules.md) .

# <a name="cnettabdotnet"></a>[C#-/.net](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionFetchTaskAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  string placeholder = "Not invoked from message";

  if (action.MessagePayload != null)
  {
      var messageText = action.MessagePayload.Body.Content;
      var fromId = action.MessagePayload.From.User.Id;
      placeholder = "Invoked from message";
  }

  var response = new MessagingExtensionActionResponse()
  {
    Task = new TaskModuleContinueResponse()
    {
      Value = new TaskModuleTaskInfo()
      {
        Height = "small",
        Width = "small",
        Title = "Example task module",
        Url = "https://contoso.com/msteams/taskmodules/newcustomer",
        },
      },
    },
  };
  return response;
}
```

# <a name="javascriptnodejstabjavascript"></a>[JavaScript/Node. js](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
  handleTeamsMessagingExtensionFetchTask(context, action) {
    return {
      task: {
        type: 'continue',
        value: {
          width: 500,
          height: 450,
          title: 'Task Module Fetch Example',
          url: 'https://contoso.com/msteams/taskmodules/newcustomer',
          fallbackUrl: 'https://contoso.com/msteams/taskmodules/newcustomer'
        }
      }
    };
  }
}
```

# <a name="jsontabjson"></a>[Json](#tab/json)

```json
{
  "task": {
    "type": "continue",
    "value": {
      "title": "Task module title",
      "height": 500,
      "width": "medium",
      "url": "https://contoso.com/msteams/taskmodules/newcustomer",
      "fallbackUrl": "https://contoso.com/msteams/taskmodules/newcustomer"
    }
  }
}
```

* * *

## <a name="next-steps"></a>Weitere Schritte

Wenn Sie zulassen, dass Ihre Benutzer eine Antwort vom Aufgabenmodul zurücksenden können, müssen Sie die Submit-Aktion behandeln.

* [Erstellen und Antworten mit einem Aufgabenmodul](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md)

[!include[messaging-extension-learn-more](~/includes/messaging-extensions/learn-more.md)]
