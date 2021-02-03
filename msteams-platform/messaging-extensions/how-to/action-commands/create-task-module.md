---
title: Erstellen und Senden des Aufgabenmoduls
author: clearab
description: Behandeln der anfänglichen Aufrufaktion und Reagieren mit einem Aufgabenmodul über einen Befehl für eine Aktions-Messaging-Erweiterung
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 58fb7e1ff5690b33c2e23f68529f05869afa9016
ms.sourcegitcommit: ce74f821660b1258c72b3c3f71c1cf177e7e92ef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2021
ms.locfileid: "50072875"
---
# <a name="create-and-send-the-task-module"></a>Erstellen und Senden des Aufgabenmoduls

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Wenn Sie das Aufgabenmodul nicht mit Parametern auffüllen, die im App-Manifest definiert sind, müssen Sie das Aufgabenmodul für Benutzer erstellen. Verwenden Sie entweder eine adaptive Karte oder eine eingebettete Webansicht.

## <a name="the-initial-invoke-request"></a>Die ursprüngliche Aufrufanforderung

Bei Verwendung dieser Methode erhält Ihr Dienst ein Objekt vom Typ, und Sie müssen mit einem Objekt antworten, das entweder die adaptive Karte oder eine URL zur eingebetteten `Activity` `composeExtension/fetchTask` `task` Webansicht enthält. Zusammen mit den standardmäßigen Botaktivitätseigenschaften enthält die ursprüngliche Aufrufnutzlast die folgenden Anforderungsmetadaten:

|Eigenschaftenname|Zweck|
|---|---|
|`type`| Anforderungstyp. Es muss sein `invoke` . |
|`name`| Typ des Befehls, der für Ihren Dienst ausgegeben wird. Es muss sein `composeExtension/fetchTask` . |
|`from.id`| ID des Benutzers, der die Anforderung gesendet hat. |
|`from.name`| Name des Benutzers, der die Anforderung gesendet hat. |
|`from.aadObjectId`| Azure Active Directory-Objekt-ID des Benutzers, der die Anforderung gesendet hat. |
|`channelData.tenant.id`| Azure Active Directory Mandanten-ID. |
|`channelData.channel.id`| Kanal-ID (wenn die Anforderung in einem Kanal gestellt wurde). |
|`channelData.team.id`| Team-ID (wenn die Anforderung in einem Kanal gestellt wurde). |
|`value.commandId` | Enthält die ID des Befehls, der aufgerufen wurde. |
|`value.commandContext` | Der Kontext, der das Ereignis ausgelöst hat. Es muss sein `compose` . |
|`value.context.theme` | Das Clientdesign des Benutzers, nützlich für die Formatierung eingebetteter Webansichten. Es muss sein `default` , `contrast` oder `dark` . |

### <a name="payload-activity-properties-when-invoked-a-task-module-from-11-chat-are-listed-in-the-following-section"></a>Nutzlastaktivitätseigenschaften beim Aufrufen eines Aufgabenmoduls aus dem 1:1-Chat werden im folgenden Abschnitt aufgeführt:

|Eigenschaftenname|Zweck|
|---|---|
|`type`| Anforderungstyp. Es muss sein `invoke` . |
|`name`| Typ des Befehls, der für Ihren Dienst ausgegeben wird. Es muss sein `composeExtension/fetchTask` . |
|`from.id`| ID des Benutzers, der die Anforderung gesendet hat. |
|`from.name`| Name des Benutzers, der die Anforderung gesendet hat. |
|`from.aadObjectId`| Azure Active Directory-Objekt-ID des Benutzers, der die Anforderung gesendet hat. |
|`channelData.tenant.id`| Azure Active Directory Mandanten-ID. |
|`channelData.source.name`| Der Quellname, von dem aus das Aufgabenmodul aufgerufen wird. |
|`ChannelData.legacy. replyToId`| Ruft die ID der Nachricht ab, auf die diese Nachricht eine Antwort ist, oder legt sie fest. |
|`value.commandId` | Enthält die ID des Befehls, der aufgerufen wurde. |
|`value.commandContext` | Der Kontext, der das Ereignis ausgelöst hat. Es muss sein `compose` . |
|`value.context.theme` | Das Clientdesign des Benutzers, nützlich für die Formatierung eingebetteter Webansichten. Es muss sein `default` , `contrast` oder `dark` . |

### <a name="payload-activity-properties-when-invoked-a-task-module-from-a-group-chat-are-listed-in-the-following-section"></a>Nutzlastaktivitätseigenschaften beim Aufrufen eines Aufgabenmoduls aus einem Gruppenchat werden im folgenden Abschnitt aufgeführt:

|Eigenschaftenname|Zweck|
|---|---|
|`type`| Anforderungstyp. Es muss sein `invoke` . |
|`name`| Typ des Befehls, der für Ihren Dienst ausgegeben wird. Es muss sein `composeExtension/fetchTask` . |
|`from.id`| ID des Benutzers, der die Anforderung gesendet hat. |
|`from.name`| Name des Benutzers, der die Anforderung gesendet hat. |
|`from.aadObjectId`| Azure Active Directory-Objekt-ID des Benutzers, der die Anforderung gesendet hat. |
|`channelData.tenant.id`| Azure Active Directory Mandanten-ID. |
|`channelData.source.name`| Der Quellname, von dem aus das Aufgabenmodul aufgerufen wird. |
|`ChannelData.legacy. replyToId`| Ruft die ID der Nachricht ab, auf die diese Nachricht eine Antwort ist, oder legt sie fest. |
|`value.commandId` | Enthält die ID des Befehls, der aufgerufen wurde. |
|`value.commandContext` | Der Kontext, der das Ereignis ausgelöst hat. Es muss sein `compose` . |
|`value.context.theme` | Das Clientdesign des Benutzers, nützlich für die Formatierung eingebetteter Webansichten. Es muss sein `default` , `contrast` oder `dark` . |

### <a name="payload-activity-properties-when-invoked-a-task-module-from-a-channel-new-post-are-listed-in-the-following-section"></a>Nutzlastaktivitätseigenschaften beim Aufrufen eines Aufgabenmoduls aus einem Kanal (neuer Beitrag) sind im folgenden Abschnitt aufgeführt:

|Eigenschaftenname|Zweck|
|---|---|
|`type`| Anforderungstyp. Es muss sein `invoke` . |
|`name`| Typ des Befehls, der für Ihren Dienst ausgegeben wird. Es muss sein `composeExtension/fetchTask` . |
|`from.id`| ID des Benutzers, der die Anforderung gesendet hat. |
|`from.name`| Name des Benutzers, der die Anforderung gesendet hat. |
|`from.aadObjectId`| Azure Active Directory-Objekt-ID des Benutzers, der die Anforderung gesendet hat. |
|`channelData.tenant.id`| Azure Active Directory Mandanten-ID. |
|`channelData.channel.id`| Kanal-ID (wenn die Anforderung in einem Kanal gestellt wurde). |
|`channelData.team.id`| Team-ID (wenn die Anforderung in einem Kanal gestellt wurde). |
|`channelData.source.name`| Der Quellname, von dem aus das Aufgabenmodul aufgerufen wird. |
|`ChannelData.legacy. replyToId`| Ruft die ID der Nachricht ab, auf die diese Nachricht eine Antwort ist, oder legt sie fest. |
|`value.commandId` | Enthält die ID des Befehls, der aufgerufen wurde. |
|`value.commandContext` | Der Kontext, der das Ereignis ausgelöst hat. Es muss sein `compose` . |
|`value.context.theme` | Das Clientdesign des Benutzers, nützlich für die Formatierung eingebetteter Webansichten. Es muss sein `default` , `contrast` oder `dark` . |

### <a name="payload-activity-properties-when-invoked-a-task-module-from-a-channel-reply-to-thread-are-listed-in-the-following-section"></a>Nutzlastaktivitätseigenschaften beim Aufrufen eines Aufgabenmoduls aus einem Kanal (Antwort an Thread) sind im folgenden Abschnitt aufgeführt:

|Eigenschaftenname|Zweck|
|---|---|
|`type`| Anforderungstyp. Es muss sein `invoke` . |
|`name`| Typ des Befehls, der für Ihren Dienst ausgegeben wird. Es muss sein `composeExtension/fetchTask` . |
|`from.id`| ID des Benutzers, der die Anforderung gesendet hat. |
|`from.name`| Name des Benutzers, der die Anforderung gesendet hat. |
|`from.aadObjectId`| Azure Active Directory-Objekt-ID des Benutzers, der die Anforderung gesendet hat. |
|`channelData.tenant.id`| Azure Active Directory Mandanten-ID. |
|`channelData.channel.id`| Kanal-ID (wenn die Anforderung in einem Kanal gestellt wurde). |
|`channelData.team.id`| Team-ID (wenn die Anforderung in einem Kanal gestellt wurde). |
|`channelData.source.name`| Der Quellname, von dem aus das Aufgabenmodul aufgerufen wird. |
|`ChannelData.legacy. replyToId`| Ruft die ID der Nachricht ab, auf die diese Nachricht eine Antwort ist, oder legt sie fest. |
|`value.commandId` | Enthält die ID des Befehls, der aufgerufen wurde. |
|`value.commandContext` | Der Kontext, der das Ereignis ausgelöst hat. Es muss sein `compose` . |
|`value.context.theme` | Das Clientdesign des Benutzers, nützlich für die Formatierung eingebetteter Webansichten. Es muss sein `default` , `contrast` oder `dark` . |

### <a name="payload-activity-properties-when-invoked-a-task-module-from-a-command-box-are-listed-in-the-following-section"></a>Nutzlastaktivitätseigenschaften, wenn ein Aufgabenmodul über ein Befehlsfeld aufgerufen wird, sind im folgenden Abschnitt aufgeführt:

|Eigenschaftenname|Zweck|
|---|---|
|`type`| Anforderungstyp. Es muss sein `invoke` . |
|`name`| Typ des Befehls, der für Ihren Dienst ausgegeben wird. Es muss sein `composeExtension/fetchTask` . |
|`from.id`| ID des Benutzers, der die Anforderung gesendet hat. |
|`from.name`| Name des Benutzers, der die Anforderung gesendet hat. |
|`from.aadObjectId`| Azure Active Directory-Objekt-ID des Benutzers, der die Anforderung gesendet hat. |
|`channelData.tenant.id`| Azure Active Directory Mandanten-ID. |
|`channelData.source.name`| Der Quellname, von dem aus das Aufgabenmodul aufgerufen wird. |
|`value.commandId` | Enthält die ID des Befehls, der aufgerufen wurde. |
|`value.commandContext` | Der Kontext, der das Ereignis ausgelöst hat. Es muss sein `compose` . |
|`value.context.theme` | Das Clientdesign des Benutzers, nützlich für die Formatierung eingebetteter Webansichten. Es muss sein `default` , `contrast` oder `dark` . |

### <a name="example-fetchtask-request"></a>Beispiel für fetchTask-Anforderung

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionFetchTaskAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  //handle fetch task
}
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreviewBot extends TeamsActivityHandler {
  handleTeamsMessagingExtensionFetchTask(context, action) {
    //hand fetch task
  }
}
```

# <a name="json"></a>[Json](#tab/json)

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

## <a name="initial-invoke-request-from-a-message"></a>Ursprüngliche Aufrufanforderung aus einer Nachricht

Wenn Ihr Bot von einer Nachricht und nicht vom Bereich zum Verfassen oder von der Befehlsleiste aufgerufen wird, muss das Objekt in der ursprünglichen Anforderung die Details der Nachricht enthalten, aus der Ihre Messagingerweiterung `value` aufgerufen wird. Im folgenden Abschnitt finden Sie ein Beispiel für dieses Objekt. Die Arrays und Arrays sind optional und sind nicht vorhanden, wenn in der ursprünglichen Nachricht keine Reaktionen oder `reactions` `mentions` Erwähnungen vorhanden sind.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionFetchTaskAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  var messageText = action.MessagePayload.Body.Content;
  var fromId = action.MessagePayload.From.User.Id;

  //finish handling the fetchTask
}
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
  handleTeamsMessagingExtensionFetchTask(context, action) {
    const messageText = action.messagePayload.body.content;

    //finish handling the fetchTask
  }
}
```

# <a name="json"></a>[Json](#tab/json)

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

## <a name="respond-to-the-fetchtask"></a>Antworten auf "fetchTask"

Reagieren Sie auf die Aufrufanforderung mit einem Objekt, das entweder ein Objekt mit der adaptiven Karte oder Web-URL oder eine einfache `task` `taskInfo` Zeichenfolgennachricht enthält.

|Eigenschaftenname|Zweck|
|---|---|
|`type`| Dies kann entweder `continue` sein, um ein Formular oder ein `message` einfaches Popup zu präsentieren. |
|`value`| Entweder ein `taskInfo` Objekt für ein Formular oder ein Objekt für eine `string` Nachricht. |

Das Schema für das taskInfo -Objekt ist:

|Eigenschaftenname|Zweck|
|---|---|
|`title`| Der Titel des Aufgabenmoduls.|
|`height`| Es muss entweder eine ganze Zahl (in Pixel) oder `small` , `medium` `large` sein.|
|`width`| Es muss entweder eine ganze Zahl (in Pixel) oder `small` , `medium` `large` sein.|
|`card`| Die adaptive Karte, die das Formular definiert (bei Verwendung eines Formulars).
|`url`| Die URL, die innerhalb des Aufgabenmoduls als eingebettete Webansicht geöffnet werden soll.|
|`fallbackUrl`| Wenn ein Client das Aufgabenmodulfeature nicht unterstützt, wird diese URL auf einer Browserregisterkarte geöffnet. |

### <a name="with-an-adaptive-card"></a>Mit einer adaptiven Karte

Wenn Sie eine adaptive Karte verwenden, müssen Sie mit einem Objekt mit dem Objekt `task` `value` antworten, das eine adaptive Karte enthält.

#### <a name="example-fetchtask-response-with-an-adaptive-card"></a>Beispiel für fetchTask-Antwort mit einer adaptiven Karte

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

In diesem Beispiel wird das [AdaptiveCards-NuGet-Paket](https://www.nuget.org/packages/AdaptiveCards) zusätzlich zum Bot Framework SDK verwendet.

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

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

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

# <a name="json"></a>[Json](#tab/json)

```json
 {
  "task": {
    "type": "continue",
    "value": {
      "title": "Task module title",
      "height": 500,
      "width": "medium",
      "card": {
        "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
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
        ]
      }
    }
  }
}
```

* * *

### <a name="with-an-embedded-web-view"></a>Mit einer eingebetteten Webansicht

Wenn Sie eine eingebettete Webansicht verwenden, müssen Sie mit einem Objekt mit dem Objekt antworten, das die URL zu dem Webformular enthält, das `task` `value` Sie laden möchten. Die Domänen aller URLs, die Sie laden möchten, müssen im Array im Manifest Ihrer `validDomains` App enthalten sein. Vollständige Informationen [zum](~/task-modules-and-cards/what-are-task-modules.md) Erstellen der eingebetteten Webansicht finden Sie in der Dokumentation zum Aufgabenmodul.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

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

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

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

# <a name="json"></a>[Json](#tab/json)

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

### <a name="request-to-install-your-conversational-bot"></a>Anfordern der Installation Ihres Unterhaltungsbots

Wenn die App einen Unterhaltungsbot enthält, installieren Sie den Bot in der Unterhaltung, bevor Sie das Aufgabenmodul laden. Es ist hilfreich, zusätzlichen Kontext für das Aufgabenmodul zu erhalten. Ein typisches Beispiel für dieses Szenario ist das Abrufen der Liste zum Auffüllen eines Personenauswahlsteuerelements oder der Liste der Kanäle in einem Team.

Wenn die Messagingerweiterung den Aufruf empfängt, überprüfen Sie, ob der Bot im aktuellen Kontext installiert ist, `composeExtension/fetchTask` um den Fluss zu vereinfachen. Überprüfen Sie z. B. den Ablauf mit einem Anruf zum Abruf der Dienstliste. Wenn der Bot nicht installiert ist, geben Sie eine adaptive Karte mit einer Aktion zurück, die den Benutzer zur Installation des Bots anfordert. Siehe die Aktion im folgenden Beispiel. Der Benutzer muss zum Überprüfen über die Berechtigung zum Installieren der Apps an diesem Speicherort verfügen. Wenn die Installation der App nicht erfolgreich ist, erhält der Benutzer eine Meldung, um sich an den Administrator zu wenden.

#### <a name="example-of-the-response"></a>Beispiel für die Antwort:

```json
{
  "type": "AdaptiveCard",
  "body": [
    {
      "type": "TextBlock",
      "text": "Looks like you haven't used Disco in this team/chat"
    }
  ],
  "actions": [
    {
      "type": "Action.Submit",
      "title": "Continue",
      "data": {
        "msteams": {
          "justInTimeInstall": true
        }
      }
    }
  ],
  "version": "1.0"
}
```

Nach der Installation empfängt der Bot eine weitere Aufrufnachricht mit `name = composeExtension/submitAction` und `value.data.msteams.justInTimeInstall = true` .

#### <a name="example-of-the-invoke"></a>Beispiel für den Aufruf:

```json
{
  "value": {
    "commandId": "giveKudos",
    "commandContext": "compose",
    "context": {
      "theme": "default"
    },
    "data": {
      "msteams": {
        "justInTimeInstall": true
      }
    }
  },
  "conversation": {
    "id": "19:7705841b240044b297123ad7f9c99217@thread.skype"
  },
  "name": "composeExtension/submitAction",
  "imdisplayname": "Bob Smith"
}
```

Die Aufgabenantwort auf den Aufruf muss mit der des installierten Bots vergleichbar sein.

#### <a name="example-of-just-in-time-installation-of-app-with-adaptive-card"></a>Beispiel für die Just-In-Time-Installation der App mit adaptiver Karte: 

```csharp
private static Attachment GetAdaptiveCardAttachmentFromFile(string fileName)
  {
      //Read the card json and create attachment.
         string[] paths = { ".", "Resources", fileName };
         var adaptiveCardJson = File.ReadAllText(Path.Combine(paths));
         var adaptiveCardAttachment = new Attachment()
            {
                ContentType = "application/vnd.microsoft.card.adaptive",
                Content = JsonConvert.DeserializeObject(adaptiveCardJson),
            };
            return adaptiveCardAttachment;
        }
```

* * *

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie Ihren Benutzern erlauben, eine Antwort vom Aufgabenmodul zurück zu senden, müssen Sie die Sendeaktion verarbeiten.

* [Erstellen und Antworten mit einem Aufgabenmodul](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md)

[!include[messaging-extension-learn-more](~/includes/messaging-extensions/learn-more.md)]
