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
# <a name="create-and-send-the-task-module"></a><span data-ttu-id="6b269-103">Erstellen und Senden des Aufgabenmoduls</span><span class="sxs-lookup"><span data-stu-id="6b269-103">Create and send the task module</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

<span data-ttu-id="6b269-104">Wenn Sie Ihr Aufgabenmodul nicht mit Parametern auffüllen, die in Ihrem App-Manifest definiert sind, müssen Sie das Aufgabenmodul erstellen, das den Benutzern angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="6b269-104">If you are not populating your task module with parameters defined in your app manifest, you'll need to create the task module to be presented to your users.</span></span> <span data-ttu-id="6b269-105">Sie können entweder eine Adaptive Karte oder eine eingebettete Webansicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="6b269-105">You can use either an Adaptive Card or an embedded web view.</span></span>

## <a name="the-initial-invoke-request"></a><span data-ttu-id="6b269-106">Die anfängliche Invoke-Anforderung</span><span class="sxs-lookup"><span data-stu-id="6b269-106">The initial invoke request</span></span>

<span data-ttu-id="6b269-107">Wenn Sie diese Methode verwenden, erhalten Sie `Activity` ein Objekt vom `composeExtension/fetchTask`Typ, und Sie müssen mit einem `task` Objekt Antworten, das entweder die Adaptive Karte oder eine URL zur eingebetteten Webansicht enthält.</span><span class="sxs-lookup"><span data-stu-id="6b269-107">Using this method you service will receive an `Activity` object of type `composeExtension/fetchTask`, and you'll need to respond with a `task` object containing either the adaptive card or a URL to the embedded web view.</span></span> <span data-ttu-id="6b269-108">Zusätzlich zu den Eigenschaften der standardmäßigen bot-Aktivität enthält die anfängliche Invoke-Nutzlast die folgenden Anforderungs Metadaten:</span><span class="sxs-lookup"><span data-stu-id="6b269-108">In addition to the standard bot activity properties, the initial invoke payload contains the following request metadata:</span></span>

|<span data-ttu-id="6b269-109">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="6b269-109">Property name</span></span>|<span data-ttu-id="6b269-110">Zweck</span><span class="sxs-lookup"><span data-stu-id="6b269-110">Purpose</span></span>|
|---|---|
|`type`| <span data-ttu-id="6b269-111">Typ der Anforderung; muss sein `invoke`.</span><span class="sxs-lookup"><span data-stu-id="6b269-111">Type of request; must be `invoke`.</span></span> |
|`name`| <span data-ttu-id="6b269-112">Der Typ des Befehls, der für den Dienst ausgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="6b269-112">Type of command that is issued to your service.</span></span> <span data-ttu-id="6b269-113">Wird `composeExtension/fetchTask`.</span><span class="sxs-lookup"><span data-stu-id="6b269-113">Will be `composeExtension/fetchTask`.</span></span> |
|`from.id`| <span data-ttu-id="6b269-114">Die ID des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="6b269-114">ID of the user that sent the request.</span></span> |
|`from.name`| <span data-ttu-id="6b269-115">Der Name des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="6b269-115">Name of the user that sent the request.</span></span> |
|`from.aadObjectId`| <span data-ttu-id="6b269-116">Azure Active Directory Objekt-ID des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="6b269-116">Azure Active Directory object id of the user that sent the request.</span></span> |
|`channelData.tenant.id`| <span data-ttu-id="6b269-117">Azure Active Directory Mandanten-ID.</span><span class="sxs-lookup"><span data-stu-id="6b269-117">Azure Active Directory tenant ID.</span></span> |
|`channelData.channel.id`| <span data-ttu-id="6b269-118">Kanal-ID (wenn die Anforderung in einem Kanal erfolgt ist).</span><span class="sxs-lookup"><span data-stu-id="6b269-118">Channel ID (if the request was made in a channel).</span></span> |
|`channelData.team.id`| <span data-ttu-id="6b269-119">Team-ID (wenn die Anforderung in einem Kanal erfolgt ist).</span><span class="sxs-lookup"><span data-stu-id="6b269-119">Team ID (if the request was made in a channel).</span></span> |
|`value.commandId` | <span data-ttu-id="6b269-120">Enthält die ID des aufgerufenen Befehls.</span><span class="sxs-lookup"><span data-stu-id="6b269-120">Contains the Id of the command that was invoked.</span></span> |
|`value.commandContext` | <span data-ttu-id="6b269-121">Der Kontext, der das Ereignis ausgelöst hat.</span><span class="sxs-lookup"><span data-stu-id="6b269-121">The context that triggered the event.</span></span> <span data-ttu-id="6b269-122">Wird `compose`.</span><span class="sxs-lookup"><span data-stu-id="6b269-122">Will be `compose`.</span></span> |
|`value.context.theme` | <span data-ttu-id="6b269-123">Das Client Design des Benutzers, nützlich für die eingebettete Webansicht-Formatierung.</span><span class="sxs-lookup"><span data-stu-id="6b269-123">The user's client theme, useful for embedded web view formatting.</span></span> <span data-ttu-id="6b269-124">`default`Ist `contrast` oder `dark`.</span><span class="sxs-lookup"><span data-stu-id="6b269-124">Will be `default`, `contrast` or `dark`.</span></span> |

### <a name="example-fetchtask-request"></a><span data-ttu-id="6b269-125">Beispiel für eine fetchTask-Anforderung</span><span class="sxs-lookup"><span data-stu-id="6b269-125">Example fetchTask request</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="6b269-126">C#-/.net</span><span class="sxs-lookup"><span data-stu-id="6b269-126">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionFetchTaskAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  //handle fetch task
}
```

# <a name="javascriptnodejstabjavascript"></a>[<span data-ttu-id="6b269-127">JavaScript/Node. js</span><span class="sxs-lookup"><span data-stu-id="6b269-127">JavaScript/Node.js</span></span>](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreviewBot extends TeamsActivityHandler {
  handleTeamsMessagingExtensionFetchTask(context, action) {
    //hand fetch task
  }
}
```

# <a name="jsontabjson"></a>[<span data-ttu-id="6b269-128">Json</span><span class="sxs-lookup"><span data-stu-id="6b269-128">JSON</span></span>](#tab/json)

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

## <a name="initial-invoke-request-from-a-message"></a><span data-ttu-id="6b269-129">Anfängliche Invoke-Anforderung aus einer Nachricht</span><span class="sxs-lookup"><span data-stu-id="6b269-129">Initial invoke request from a message</span></span>

<span data-ttu-id="6b269-130">Wenn Ihr bot aus einer Nachricht anstatt aus dem verfassenbereich oder der Befehlsleiste aufgerufen wird, enthält `value` das Objekt in der anfänglichen Anforderung die Details der Nachricht, aus der Ihre Messaging-Erweiterung aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="6b269-130">When your bot is invoked from a message rather than the compose area or the command bar, the `value` object in the initial request will contain the details of the message your messaging extension was invoked from.</span></span> <span data-ttu-id="6b269-131">Ein Beispiel für dieses Objekt ist unten.</span><span class="sxs-lookup"><span data-stu-id="6b269-131">An example of this object is below.</span></span> <span data-ttu-id="6b269-132">Die `reactions` - `mentions` und-Arrays sind optional und werden nicht angezeigt, wenn in der ursprünglichen Nachricht keine Reaktionen oder Erwähnungen vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="6b269-132">The `reactions` and `mentions` arrays are optional, and will not be present if there are no reactions or mentions in the original message.</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="6b269-133">C#-/.net</span><span class="sxs-lookup"><span data-stu-id="6b269-133">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionFetchTaskAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  var messageText = action.MessagePayload.Body.Content;
  var fromId = action.MessagePayload.From.User.Id;

  //finish handling the fetchTask
}
```

# <a name="javascriptnodejstabjavascript"></a>[<span data-ttu-id="6b269-134">JavaScript/Node. js</span><span class="sxs-lookup"><span data-stu-id="6b269-134">JavaScript/Node.js</span></span>](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
  handleTeamsMessagingExtensionFetchTask(context, action) {
    const messageText = action.messagePayload.body.content;

    //finish handling the fetchTask
  }
}
```

# <a name="jsontabjson"></a>[<span data-ttu-id="6b269-135">Json</span><span class="sxs-lookup"><span data-stu-id="6b269-135">JSON</span></span>](#tab/json)

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

## <a name="respond-to-the-fetchtask"></a><span data-ttu-id="6b269-136">Antworten auf die fetchTask</span><span class="sxs-lookup"><span data-stu-id="6b269-136">Respond to the fetchTask</span></span>

<span data-ttu-id="6b269-137">Antworten Sie auf die Invoke-Anforderung `task` mit einem Objekt, das `taskInfo` entweder ein Objekt mit der adaptiven Karte oder die weburl oder eine einfache Zeichenfolgennachricht enthält.</span><span class="sxs-lookup"><span data-stu-id="6b269-137">Respond to the invoke request with a `task` object that contains either a `taskInfo` object with the adaptive card or web URL, or a simple string message.</span></span>

|<span data-ttu-id="6b269-138">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="6b269-138">Property name</span></span>|<span data-ttu-id="6b269-139">Zweck</span><span class="sxs-lookup"><span data-stu-id="6b269-139">Purpose</span></span>|
|---|---|
|`type`| <span data-ttu-id="6b269-140">Kann entweder `continue` zum Darstellen eines Formulars oder `message` für ein einfaches Popup-Objekt sein.</span><span class="sxs-lookup"><span data-stu-id="6b269-140">Can be either `continue` to present a form, or `message` for a simple popup.</span></span> |
|`value`| <span data-ttu-id="6b269-141">Entweder ein `taskInfo` Objekt für ein Formular oder ein `string` für eine Nachricht.</span><span class="sxs-lookup"><span data-stu-id="6b269-141">Either a `taskInfo` object for a form, or a `string` for a message.</span></span> |

<span data-ttu-id="6b269-142">Das Schema für das taskInfo-Objekt lautet:</span><span class="sxs-lookup"><span data-stu-id="6b269-142">The schema for the taskInfo object is:</span></span>

|<span data-ttu-id="6b269-143">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="6b269-143">Property name</span></span>|<span data-ttu-id="6b269-144">Zweck</span><span class="sxs-lookup"><span data-stu-id="6b269-144">Purpose</span></span>|
|---|---|
|`title`| <span data-ttu-id="6b269-145">Der Titel des Aufgabenmoduls.</span><span class="sxs-lookup"><span data-stu-id="6b269-145">The title of the task module.</span></span>|
|`height`| <span data-ttu-id="6b269-146">Kann eine ganze Zahl (in Pixeln) oder `small`, `medium`, `large`sein.</span><span class="sxs-lookup"><span data-stu-id="6b269-146">Can be either an integer (in pixels), or `small`, `medium`, `large`.</span></span>|
|`width`| <span data-ttu-id="6b269-147">Kann eine ganze Zahl (in Pixeln) oder `small`, `medium`, `large`sein.</span><span class="sxs-lookup"><span data-stu-id="6b269-147">Can be either an integer (in pixels), or `small`, `medium`, `large`.</span></span>|
|`card`| <span data-ttu-id="6b269-148">Die Adaptive Karte, die das Formular definiert (sofern eine verwendet wird).</span><span class="sxs-lookup"><span data-stu-id="6b269-148">The adaptive card defining the form (if using one).</span></span>
|`url`| <span data-ttu-id="6b269-149">Die URL, die innerhalb des Aufgabenmoduls als eingebettete Webansicht geöffnet werden soll.</span><span class="sxs-lookup"><span data-stu-id="6b269-149">The URL to be opened inside of the task module as an embedded web view.</span></span>|
|`fallbackUrl`| <span data-ttu-id="6b269-150">Wenn ein Client das Feature "Aufgabenmodul" nicht unterstützt, wird diese URL in einer Browserregister Karte geöffnet.</span><span class="sxs-lookup"><span data-stu-id="6b269-150">If a client does not support the task module feature, this URL is opened in a browser tab.</span></span> |

### <a name="with-an-adaptive-card"></a><span data-ttu-id="6b269-151">Mit einer adaptiven Karte</span><span class="sxs-lookup"><span data-stu-id="6b269-151">With an adaptive card</span></span>

<span data-ttu-id="6b269-152">Wenn Sie eine Adaptive Karte verwenden, müssen Sie mit einem `task` Objekt mit dem Objekt `value` Antworten, das eine Adaptive Karte enthält.</span><span class="sxs-lookup"><span data-stu-id="6b269-152">When using an adaptive card, you'll need to respond with a `task` object with the `value` object containing an adaptive card.</span></span>

#### <a name="example-fetchtask-response-with-an-adaptive-card"></a><span data-ttu-id="6b269-153">Beispiel für eine fetchTask-Antwort mit einer adaptiven Karte</span><span class="sxs-lookup"><span data-stu-id="6b269-153">Example fetchTask response with an adaptive card</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="6b269-154">C#-/.net</span><span class="sxs-lookup"><span data-stu-id="6b269-154">C#/.NET</span></span>](#tab/dotnet)

<span data-ttu-id="6b269-155">In diesem Beispiel wird das [AdaptiveCards-NuGet-Paket](https://www.nuget.org/packages/AdaptiveCards) zusätzlich zum bot Framework SDK verwendet.</span><span class="sxs-lookup"><span data-stu-id="6b269-155">This sample uses the [AdaptiveCards NuGet package](https://www.nuget.org/packages/AdaptiveCards) in addition to the Bot Framework SDK.</span></span>

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

# <a name="javascriptnodejstabjavascript"></a>[<span data-ttu-id="6b269-156">JavaScript/Node. js</span><span class="sxs-lookup"><span data-stu-id="6b269-156">JavaScript/Node.js</span></span>](#tab/javascript)

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

# <a name="jsontabjson"></a>[<span data-ttu-id="6b269-157">Json</span><span class="sxs-lookup"><span data-stu-id="6b269-157">JSON</span></span>](#tab/json)

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

### <a name="with-an-embedded-web-view"></a><span data-ttu-id="6b269-158">Mit einer eingebetteten Webansicht</span><span class="sxs-lookup"><span data-stu-id="6b269-158">With an embedded web view</span></span>

<span data-ttu-id="6b269-159">Bei Verwendung einer eingebetteten Webansicht müssen Sie mit einem `task` Objekt mit dem `value` Objekt Antworten, das die URL zu dem Webformular enthält, das Sie laden möchten.</span><span class="sxs-lookup"><span data-stu-id="6b269-159">When using an embedded web view, you'll need to respond with a `task` object with the `value` object containing the URL to the web form you'd like to load.</span></span> <span data-ttu-id="6b269-160">Die Domänen einer beliebigen URL, die Sie laden möchten, müssen in dem `validDomains` Array im App-Manifest enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="6b269-160">The domains of any URL you want to load must be included in the `validDomains` array in your app's manifest.</span></span> <span data-ttu-id="6b269-161">Ausführliche Informationen zum Erstellen Ihrer eingebetteten Webansicht finden Sie in der [Dokumentation zum Aufgabenmodul](~/task-modules-and-cards/what-are-task-modules.md) .</span><span class="sxs-lookup"><span data-stu-id="6b269-161">See the [task module documentation](~/task-modules-and-cards/what-are-task-modules.md) for complete information on building your embedded web view.</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="6b269-162">C#-/.net</span><span class="sxs-lookup"><span data-stu-id="6b269-162">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="javascriptnodejstabjavascript"></a>[<span data-ttu-id="6b269-163">JavaScript/Node. js</span><span class="sxs-lookup"><span data-stu-id="6b269-163">JavaScript/Node.js</span></span>](#tab/javascript)

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

# <a name="jsontabjson"></a>[<span data-ttu-id="6b269-164">Json</span><span class="sxs-lookup"><span data-stu-id="6b269-164">JSON</span></span>](#tab/json)

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

## <a name="next-steps"></a><span data-ttu-id="6b269-165">Weitere Schritte</span><span class="sxs-lookup"><span data-stu-id="6b269-165">Next steps</span></span>

<span data-ttu-id="6b269-166">Wenn Sie zulassen, dass Ihre Benutzer eine Antwort vom Aufgabenmodul zurücksenden können, müssen Sie die Submit-Aktion behandeln.</span><span class="sxs-lookup"><span data-stu-id="6b269-166">If you allow your users to send a response back from the task module, you'll need to handle the submit action.</span></span>

* [<span data-ttu-id="6b269-167">Erstellen und Antworten mit einem Aufgabenmodul</span><span class="sxs-lookup"><span data-stu-id="6b269-167">Create and respond with a task module</span></span>](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md)

[!include[messaging-extension-learn-more](~/includes/messaging-extensions/learn-more.md)]
