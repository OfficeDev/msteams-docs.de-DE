---
title: Initiieren von Aktionen mit Messagingerweiterungen
description: Erstellen aktionsbasierter Messagingerweiterungen, damit Benutzer externe Dienste auslösen können
localization_priority: Normal
ms.topic: how-to
keywords: Teams Messaging-Erweiterungen Messaging-Erweiterungen Suche
ms.openlocfilehash: bfb3295726c355164f080c15e3759ea36a99d914
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566740"
---
# <a name="initiate-actions-with-messaging-extensions"></a><span data-ttu-id="06923-104">Initiieren von Aktionen mit Messagingerweiterungen</span><span class="sxs-lookup"><span data-stu-id="06923-104">Initiate actions with messaging extensions</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-me.md)]

<span data-ttu-id="06923-105">Aktionsbasierte Messagingerweiterungen ermöglichen es Benutzern, Aktionen in externen Diensten auszulösen, während sie sich innerhalb Teams.</span><span class="sxs-lookup"><span data-stu-id="06923-105">Action-based messaging extensions allow your users to trigger actions in external services while inside of Teams.</span></span>

![Beispiel für Messaging-Erweiterungskarte](~/assets/images/compose-extensions/ceexample.png)

<span data-ttu-id="06923-107">In den folgenden Abschnitten wird beschrieben, wie Sie dies tun.</span><span class="sxs-lookup"><span data-stu-id="06923-107">The following sections describe how to do this.</span></span>

[!include[Common content for creating extensions](~/includes/messaging-extensions/messaging-extensions-common.md)]

### <a name="action-type-message-extensions"></a><span data-ttu-id="06923-108">Aktionstyp-Nachrichtenerweiterungen</span><span class="sxs-lookup"><span data-stu-id="06923-108">Action type message extensions</span></span>

<span data-ttu-id="06923-109">Um Aktionen aus einer Messagingerweiterung zu initiieren, legen Sie den `type` Parameter auf `action` .</span><span class="sxs-lookup"><span data-stu-id="06923-109">To initiate actions from a  messaging extension set the `type` parameter to `action`.</span></span> <span data-ttu-id="06923-110">Im Folgenden finden Sie ein Beispiel für ein Manifest mit einem Such- und einem Create-Befehl.</span><span class="sxs-lookup"><span data-stu-id="06923-110">Below is an example of a manifest with a search and a create command.</span></span> <span data-ttu-id="06923-111">Eine einzelne Messagingerweiterung kann bis zu 10 verschiedene Befehle haben.</span><span class="sxs-lookup"><span data-stu-id="06923-111">A single messaging extension can have up to 10 different commands.</span></span> <span data-ttu-id="06923-112">Dies kann sowohl mehrere Such- als auch mehrere aktionsbasierte Befehle umfassen.</span><span class="sxs-lookup"><span data-stu-id="06923-112">This can include both multiple search and multiple action-based commands.</span></span>

#### <a name="complete-app-manifest-example"></a><span data-ttu-id="06923-113">Vollständiges App-Manifestbeispiel</span><span class="sxs-lookup"><span data-stu-id="06923-113">Complete app manifest example</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",
  "manifestVersion": "1.5",
  "version": "1.0",
  "id": "57a3c29f-1fc5-4d97-a142-35bb662b7b23",
  "packageName": "com.microsoft.teams.samples.Todo",
  "developer": {
    "name": "John Developer",
    "websiteUrl": "http://todobotservice.azurewebsites.net/",
    "privacyUrl": "http://todobotservice.azurewebsites.net/privacy",
    "termsOfUseUrl": "http://todobotservice.azurewebsites.net/termsofuse"
  },
  "name": {
    "short": "To Do",
    "full": "To Do"
  },
  "description": {
    "short": "Find or create a new task in To Do",
    "full": "Find or create a new task in To Do"
  },
  "icons": {
    "outline": "todo-outline.jpg",
    "color": "todo-color.jpg"
  },
  "accentColor": "#ff6a00",
  "composeExtensions": [
    {
      "botId": "57a3c29f-1fc5-4d97-a142-35bb662b7b23",
      "canUpdateConfiguration": true,
      "commands": [
        {
          "id": "searchCmd",
          "description": "Search you Todo's",
          "title": "Search",
          "initialRun": true,
          "context": ["commandBox", "compose"],
          "parameters": [
            {
              "name": "searchKeyword",
              "description": "Enter your search keywords",
              "title": "Keywords"
            }
          ]
        },
        {
          "id": "addTodo",
          "description": "Create a To Do item",
          "title": "Create To Do",
          "type": "action",
          "context": ["commandBox", "message", "compose"],
          "parameters": [
            {
              "name": "Name",
              "description": "To Do Title",
              "title": "Title",
              "inputType": "text"
            },
            {
              "name": "Description",
              "description": "Description of the task",
              "title": "Description",
              "inputType": "textarea"
            },
            {
              "name": "Date",
              "description": "Due date for the task",
              "title": "Date",
              "inputType": "date"
            }
          ]
        },
        {
          "id": "reassignTodo",
          "description": "Reassign a todo item",
          "title": "Reassign a todo item",
          "type": "action",
          "fetchTask": true,
          "parameters": [
            {
              "name": "Name",
              "title": "Title"
            }
          ]
        }
      ]
    }
  ],
  "permissions": [
    "identity",
    "messageTeamMembers"
  ],
  "validDomains": [
    "todobotservice.azurewebsites.net",
    "*.todobotservice.azurewebsites.net"
  ]
}
```

### <a name="initiate-actions-from-messages"></a><span data-ttu-id="06923-114">Initiieren von Aktionen aus Nachrichten</span><span class="sxs-lookup"><span data-stu-id="06923-114">Initiate actions from messages</span></span>

<span data-ttu-id="06923-115">Zusätzlich zum Initiieren von Aktionen aus dem Nachrichtenbereich zum Verfassen können Sie auch die Messagingerweiterung verwenden, um eine Aktion aus einer Nachricht zu initiieren.</span><span class="sxs-lookup"><span data-stu-id="06923-115">In addition to initiating actions from the compose message area, you can also use your messaging extension to initiate an action from a message.</span></span> <span data-ttu-id="06923-116">Auf diese Weise können Sie den Inhalt der Nachricht zur Verarbeitung an Ihren Bot senden und optional auf diese Nachricht mit einer Antwort mit der unter [Antworten auf Senden](#responding-to-submit)beschriebenen Methode antworten.</span><span class="sxs-lookup"><span data-stu-id="06923-116">This will allow you to send the contents of the message to your bot for processing, and optionally reply to that message with a response using the method described in [Responding to submit](#responding-to-submit).</span></span> <span data-ttu-id="06923-117">Die Antwort wird als Antwort auf die Nachricht eingefügt, die Ihre Benutzer vor dem Absenden bearbeiten können.</span><span class="sxs-lookup"><span data-stu-id="06923-117">The response will be inserted as a reply to the message that your users can edit before submitting.</span></span> <span data-ttu-id="06923-118">Ihre Benutzer können über das Überlaufmenü auf Ihre Messagingerweiterung zugreifen `...` und dann wie in der folgenden Abbildung `Take action` auswählen:</span><span class="sxs-lookup"><span data-stu-id="06923-118">Your users can access your messaging extension from the overflow `...` menu and then selecting `Take action` as in the following image:</span></span>

![Beispiel für das Anleiten einer Aktion aus einer Nachricht](~/assets/images/compose-extensions/messageextensions_messageaction.png)

<span data-ttu-id="06923-120">Damit Ihre Messagingerweiterung von einer Nachricht aus funktioniert, müssen Sie den `context` Parameter dem Objekt Ihrer Messagingerweiterung in Ihrem App-Manifest hinzufügen, `commands` wie im folgenden Beispiel.</span><span class="sxs-lookup"><span data-stu-id="06923-120">To enable your messaging extension to work from a message you'll need to add the `context` parameter to your messaging extension's `commands` object in your app manifest as in the example below.</span></span> <span data-ttu-id="06923-121">Gültige Zeichenfolgen für das `context` Array sind , und `"message"` `"commandBox"` `"compose"` .</span><span class="sxs-lookup"><span data-stu-id="06923-121">Valid strings for the `context` array are `"message"`, `"commandBox"`, and `"compose"`.</span></span> <span data-ttu-id="06923-122">Der Standardwert ist `["compose", "commandBox"]`.</span><span class="sxs-lookup"><span data-stu-id="06923-122">The default value is `["compose", "commandBox"]`.</span></span> <span data-ttu-id="06923-123">Ausführliche Informationen zum Parameter finden Sie im Abschnitt [Befehle](#define-commands) `context` definieren.</span><span class="sxs-lookup"><span data-stu-id="06923-123">See the [define commands](#define-commands) section for complete details on the `context` parameter.</span></span>

```json
"composeExtensions": [
  {
    "botId": "57a3c29f-1fc5-4d97-a142-35bb662b7b23",
    "canUpdateConfiguration": true,
    "commands": [
      {
        "id": "reassignTodo",
        "description": "Reassign a todo item",
        "title": "Create To Do",
        "type": "Action",
        "context": ["message"],
        "fetchTask": true
    }]
    ...

```

<span data-ttu-id="06923-124">Im Folgenden finden Sie ein Beispiel für das `value` Objekt, das die Nachrichtendetails enthält, die als Teil der `composeExtension` Anforderung an Ihren Bot gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="06923-124">Below is an example of the `value` object containing the message details that will be sent as part of the `composeExtension` request be sent to your bot.</span></span>

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
        "content": "this is the message"
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

### <a name="test-via-uploading"></a><span data-ttu-id="06923-125">Test über Upload</span><span class="sxs-lookup"><span data-stu-id="06923-125">Test via uploading</span></span>

<span data-ttu-id="06923-126">Sie können Ihre Messaging-Erweiterung testen, indem Sie Ihre App hochladen.</span><span class="sxs-lookup"><span data-stu-id="06923-126">You can test your messaging extension by uploading your app.</span></span> <span data-ttu-id="06923-127">Weitere Informationen finden Sie unter [Hochladen Ihrer App in einem Team](~/concepts/deploy-and-publish/apps-upload.md).</span><span class="sxs-lookup"><span data-stu-id="06923-127">For more information, see [Uploading your app in a team](~/concepts/deploy-and-publish/apps-upload.md).</span></span>

<span data-ttu-id="06923-128">Um Ihre Messaging-Erweiterung zu öffnen, navigieren Sie zu einem Ihrer Chats oder Kanäle.</span><span class="sxs-lookup"><span data-stu-id="06923-128">To open your messaging extension, navigate to any of your chats or channels.</span></span> <span data-ttu-id="06923-129">Wählen Sie im Feld Verfassen die Schaltfläche **Weitere Optionen** (**&#8943;**) aus, und wählen Sie Ihre Messaging-Erweiterung aus.</span><span class="sxs-lookup"><span data-stu-id="06923-129">Choose the **More options** (**&#8943;**) button in the compose box, and choose your messaging extension.</span></span>

## <a name="collecting-input-from-users"></a><span data-ttu-id="06923-130">Sammeln von Eingaben von Benutzern</span><span class="sxs-lookup"><span data-stu-id="06923-130">Collecting input from users</span></span>

<span data-ttu-id="06923-131">Es gibt drei Möglichkeiten, Informationen von einem Endbenutzer in Teams zu sammeln.</span><span class="sxs-lookup"><span data-stu-id="06923-131">There are three ways to collect information from an end user in Teams.</span></span>

### <a name="static-parameter-list"></a><span data-ttu-id="06923-132">Statische Parameterliste</span><span class="sxs-lookup"><span data-stu-id="06923-132">Static parameter list</span></span>

<span data-ttu-id="06923-133">Bei dieser Methode müssen Sie lediglich eine statische Liste von Parametern im Manifest definieren, wie oben im Befehl "erstellen To Do" gezeigt.</span><span class="sxs-lookup"><span data-stu-id="06923-133">In this method, all you need to do is define a static list of parameters in the manifest as shown above in the "Create To Do" command.</span></span> <span data-ttu-id="06923-134">Um diese Methode zu verwenden, stellen `fetchTask` Sie sicher, dass auf festgelegt ist `false` und dass Sie Ihre Parameter im Manifest definieren.</span><span class="sxs-lookup"><span data-stu-id="06923-134">To use this method ensure `fetchTask` is set to `false` and that you define your parameters in the manifest.</span></span>

<span data-ttu-id="06923-135">Wenn ein Benutzer einen Befehl mit statischen Parametern auswählt, generiert Teams ein Formular in einem Taskmodul mit den im Manifest definierten Parametern.</span><span class="sxs-lookup"><span data-stu-id="06923-135">When a user chooses a command with static parameters, Teams will generate a form in a Task Module with the parameters defined in the manifest.</span></span> <span data-ttu-id="06923-136">Beim Schlagen wird Ein `composeExtension/submitAction` sende per Bot gesendet.</span><span class="sxs-lookup"><span data-stu-id="06923-136">On hitting Submit a `composeExtension/submitAction` is sent to the bot.</span></span> <span data-ttu-id="06923-137">Weitere Informationen zu den erwarteten Antworten finden Sie unter [Antworten zum Senden](#responding-to-submit).</span><span class="sxs-lookup"><span data-stu-id="06923-137">For more information on the expected set of responses, see [Responding to submit](#responding-to-submit).</span></span>

### <a name="dynamic-input-using-an-adaptive-card"></a><span data-ttu-id="06923-138">Dynamischer Eingang mit einer adaptiven Karte</span><span class="sxs-lookup"><span data-stu-id="06923-138">Dynamic input using an adaptive card</span></span>

<span data-ttu-id="06923-139">Bei dieser Methode kann Ihr Dienst eine benutzerdefinierte adaptive Karte definieren, um die Endbenutzereingabe zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="06923-139">In this method, your service can define a custom adaptive card to collect the end user input.</span></span> <span data-ttu-id="06923-140">Legen Sie für diesen Ansatz den `fetchTask` Parameter `true` im Manifest fest.</span><span class="sxs-lookup"><span data-stu-id="06923-140">For this approach, set the `fetchTask` parameter to `true` in the manifest.</span></span> <span data-ttu-id="06923-141">Beachten Sie, dass, wenn Sie auf statische Parameter festlegen, `fetchTask` die für den Befehl definiert `true` sind, ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="06923-141">Note that if you set `fetchTask` to `true` any static parameters defined for the command will be ignored.</span></span>

<span data-ttu-id="06923-142">Bei dieser Methode erhält Ihr Dienst ein `composeExtension/fetchTask` Ereignis und muss mit einer adaptiven kartenbasierten [Aufgabenmodulantwort](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object)antworten.</span><span class="sxs-lookup"><span data-stu-id="06923-142">In this method your service will receive a `composeExtension/fetchTask` event and needs to respond with an adaptive card based [task module response](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object).</span></span> <span data-ttu-id="06923-143">Im Folgenden finden Sie eine Beispielantwort mit einer adaptiven Karte:</span><span class="sxs-lookup"><span data-stu-id="06923-143">Following is a sample response with an adaptive card:</span></span>

```json
{
    "task": {
        "type": "continue",
        "value": {
            "card": {
                "contentType": "application/vnd.microsoft.card.adaptive",
                "content": {
                    "body": [
                        {
                            "type": "TextBlock",
                            "text": "Please enter the following information:"
                        },
                        {
                            "type": "TextBlock",
                            "text": "Name"
                        },
                        {
                            "type": "Input.Text",
                            "spacing": "None",
                            "title": "New Input.Toggle",
                            "placeholder": "Placeholder text"
                        },
                        {
                            "type": "TextBlock",
                            "text": "Date of birth"
                        },
                        {
                            "type": "Input.Date",
                            "spacing": "None",
                            "title": "New Input.Toggle"
                        }
                    ],
                    "type": "AdaptiveCard",
                    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
                    "version": "1.0"
                }
            }
        }
    }
}
```

<span data-ttu-id="06923-144">Der Bot kann auch mit einer auth/config-Antwort antworten, wenn der Benutzer die Erweiterung authentifizieren oder konfigurieren muss, bevor er die Benutzereingabe erhält.</span><span class="sxs-lookup"><span data-stu-id="06923-144">The bot can also respond with an auth/config response if the user needs to authenticate or configure the extension before getting the user input.</span></span>

### <a name="dynamic-input-using-a-web-view"></a><span data-ttu-id="06923-145">Dynamische Eingabe über eine Webansicht</span><span class="sxs-lookup"><span data-stu-id="06923-145">Dynamic input using a web view</span></span>

<span data-ttu-id="06923-146">Bei dieser Methode kann Ihr Dienst ein basiertes Widget anzeigen, `<iframe>` um jede benutzerdefinierte Benutzeroberfläche anzuzeigen und Benutzereingaben zu sammeln.</span><span class="sxs-lookup"><span data-stu-id="06923-146">In this method your service can show an `<iframe>` based widget to show any custom UI and collect user input.</span></span> <span data-ttu-id="06923-147">Legen Sie für diesen Ansatz den `fetchTask` Parameter `true` im Manifest fest.</span><span class="sxs-lookup"><span data-stu-id="06923-147">For this approach, set the `fetchTask` parameter to `true` in the manifest.</span></span>

<span data-ttu-id="06923-148">Genau wie im adaptiven Kartenfluss wird Ihr Dienst ein Ereignis senden `fetchTask` und muss mit einer URL-basierten [Taskmodulantwort](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object)antworten.</span><span class="sxs-lookup"><span data-stu-id="06923-148">Just like in the adaptive card flow your service will be send a `fetchTask` event and needs to respond with a URL based [task module response](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object).</span></span> <span data-ttu-id="06923-149">Im Folgenden finden Sie eine Beispielantwort mit einer adaptiven Karte:</span><span class="sxs-lookup"><span data-stu-id="06923-149">Following is a sample response with an Adaptive card:</span></span>

```json
{
    "task": {
        "value": {
            "url": "http://mywebapp.com/input"
        },
        "type": "continue"
    }
}
```

### <a name="request-to-install-your-conversational-bot"></a><span data-ttu-id="06923-150">Anfrage zur Installation Ihres Konversationsbots</span><span class="sxs-lookup"><span data-stu-id="06923-150">Request to install your conversational bot</span></span>

<span data-ttu-id="06923-151">Wenn Ihre App auch einen Konversationsbot enthält, kann es erforderlich sein, sicherzustellen, dass Ihr Bot in der Unterhaltung installiert ist, bevor Sie Ihr Aufgabenmodul laden.</span><span class="sxs-lookup"><span data-stu-id="06923-151">If your app also contains a conversational bot, it may be necessary to ensure that your bot is installed in the conversation before loading your task module.</span></span> <span data-ttu-id="06923-152">Dies kann in Situationen nützlich sein, in denen Sie zusätzlichen Kontext für Ihr Aufgabenmodul abrufen müssen.</span><span class="sxs-lookup"><span data-stu-id="06923-152">This can be useful in situations where you need to get additional context for you task module.</span></span> <span data-ttu-id="06923-153">Sie müssen z. B. den Dienstplan abrufen, um ein Personenauswahlsteuerelement oder die Liste der Kanäle in einem Team aufzufüllen.</span><span class="sxs-lookup"><span data-stu-id="06923-153">For example, you may need to fetch the roster to populate a people picker control, or the list of channels in a team.</span></span>

<span data-ttu-id="06923-154">Um diesen Fluss zu erleichtern, wenn Ihre Messagingerweiterung zum ersten Mal die `composeExtension/fetchTask` Aufrufprüfung empfängt, um zu sehen, ob Ihr Bot im aktuellen Kontext installiert ist.</span><span class="sxs-lookup"><span data-stu-id="06923-154">To facilitate this flow, when your messaging extension first receives the `composeExtension/fetchTask` invoke check to see if your bot is installed in the current context.</span></span> <span data-ttu-id="06923-155">Sie können dies erreichen, indem Sie den Abrufen von Dienstplanaufrufen versuchen, z. B. Wenn Ihr Bot nicht installiert ist, geben Sie eine Adaptive Karte mit einer Aktion zurück, die den Benutzer auffordert, Ihren Bot zu installieren. Siehe das Beispiel unten.</span><span class="sxs-lookup"><span data-stu-id="06923-155">You could accomplish this by attempting the get roster call, for example, If your bot is not installed, you return an Adaptive Card with an action that requests the user to install your bot See the example below.</span></span> <span data-ttu-id="06923-156">Beachten Sie, dass der Benutzer über die Berechtigung zum Installieren von Apps an diesem Speicherort verfügt. Wenn sie dies nicht können, wird ihnen eine Meldung angezeigt, in der sie aufgefordert werden, sich an ihren Administrator zu wenden.</span><span class="sxs-lookup"><span data-stu-id="06923-156">Note that this requires the user to have permission to install apps in that location; if they cannot they will be presented with a message asking them to contact their administrator.</span></span>

<span data-ttu-id="06923-157">Hier ist ein Beispiel für die Antwort:</span><span class="sxs-lookup"><span data-stu-id="06923-157">Here's an example of the response:</span></span>

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

<span data-ttu-id="06923-158">Sobald der Benutzer die Installation abgeschlossen hat, erhält Ihr Bot eine weitere Aufrufnachricht mit `name = composeExtension/submitAction` . und `value.data.msteams.justInTimeInstall = true` .</span><span class="sxs-lookup"><span data-stu-id="06923-158">Once the user completes the installation, your bot will receive another invoke message with `name = composeExtension/submitAction`, and `value.data.msteams.justInTimeInstall = true`.</span></span>

<span data-ttu-id="06923-159">Hier ist ein Beispiel für den Aufruf:</span><span class="sxs-lookup"><span data-stu-id="06923-159">Here's an example of the invoke:</span></span>

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

<span data-ttu-id="06923-160">Sie sollten auf diesen Aufruf mit derselben Taskantwort antworten, mit der Sie geantwortet hätten, wenn der Bot bereits installiert war.</span><span class="sxs-lookup"><span data-stu-id="06923-160">You should respond to this invoke with the same task response you would have responded with if the bot was already installed.</span></span>

## <a name="responding-to-submit"></a><span data-ttu-id="06923-161">Reagieren auf Dieübermittlung</span><span class="sxs-lookup"><span data-stu-id="06923-161">Responding to submit</span></span>

<span data-ttu-id="06923-162">Sobald ein Benutzer die Eingabe seiner Eingabe abgeschlossen hat, erhält Ihr Bot ein `composeExtension/submitAction` Ereignis mit der Befehls-ID und den Parameterwerten.</span><span class="sxs-lookup"><span data-stu-id="06923-162">Once a user completes entering their input your bot will receive a `composeExtension/submitAction` event with the command id and parameter values set.</span></span>

<span data-ttu-id="06923-163">Dies sind die unterschiedlichen erwarteten Antworten auf eine `submitAction` .</span><span class="sxs-lookup"><span data-stu-id="06923-163">These are the different expected responses to a `submitAction`.</span></span>

### <a name="task-module-response"></a><span data-ttu-id="06923-164">Task-Modul-Antwort</span><span class="sxs-lookup"><span data-stu-id="06923-164">Task Module response</span></span>

<span data-ttu-id="06923-165">Dies wird verwendet, wenn Ihre Erweiterung Dialoge miteinander verketten muss, um weitere Informationen zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="06923-165">This is used when your extension needs to chain dialogs together to get more information.</span></span> <span data-ttu-id="06923-166">Die Antwort ist genau die gleiche wie `fetchTask` zuvor erwähnt.</span><span class="sxs-lookup"><span data-stu-id="06923-166">The response is exactly the same as `fetchTask` mentioned earlier.</span></span>

### <a name="compose-extension-authconfig-response"></a><span data-ttu-id="06923-167">Komponieren der Erweiterung auth/config-Antwort</span><span class="sxs-lookup"><span data-stu-id="06923-167">Compose extension auth/config response</span></span>

<span data-ttu-id="06923-168">Dies wird verwendet, wenn ihre Erweiterung sich authentifizieren oder konfigurieren muss, um fortzufahren.</span><span class="sxs-lookup"><span data-stu-id="06923-168">This is used when your extension needs to either authenticate or configure in order to continue.</span></span> <span data-ttu-id="06923-169">Weitere Informationen finden Sie im [Abschnitt Authentifizierung](~/resources/messaging-extension-v3/search-extensions.md#authentication) im Suchabschnitt.</span><span class="sxs-lookup"><span data-stu-id="06923-169">For more information, see [authentication section](~/resources/messaging-extension-v3/search-extensions.md#authentication) in the search section.</span></span>

### <a name="compose-extension-result-response"></a><span data-ttu-id="06923-170">Komponieren der Antwort auf die Erweiterungsergebnisantwort</span><span class="sxs-lookup"><span data-stu-id="06923-170">Compose extension result response</span></span>

<span data-ttu-id="06923-171">Dadurch wurde eine Karte als Ergebnis eines Befehls in das Verfassenfeld eingefügt.</span><span class="sxs-lookup"><span data-stu-id="06923-171">This used to insert a card into the compose box as a result of a the command.</span></span> <span data-ttu-id="06923-172">Es ist die gleiche Antwort, die im Suchbefehl verwendet wird, aber es ist auf eine Karte oder ein Ergebnis im Array beschränkt.</span><span class="sxs-lookup"><span data-stu-id="06923-172">It's the same response that's used in the search command, but it's limited to one card or one result in the array.</span></span>

```json
{
  "composeExtension": {
    "type": "result",
    "attachmentLayout": "list",
    "preview": {
          "contentType": "application/vnd.microsoft.card.thumbnail",
          "content": {
            "title": "85069: Create a cool app",
            "images": [
              {
                "url": "https://placekitten.com/200/200"
              }
            ]
          }
        },
    "attachments": [
      {  
        "contentType": "application/vnd.microsoft.teams.card.o365connector",
        "content": {
          "sections": [
            {
              "activityTitle": "[85069]: Create a cool app",
              "activityImage&quot;: &quot;https://placekitten.com/200/200"
            },
            {
              "title": "Details",
              "facts": [
                {
                  "name": "Assigned to:",
                  "value&quot;: &quot;[Larry Brown](mailto:larryb@example.com)"
                },
                {
                  "name": "State:",
                  "value": "Active"
                }
              ]
            }
          ]
        }
      }
    ]
  }
}
```

### <a name="respond-with-an-adaptive-card-message-sent-from-a-bot"></a><span data-ttu-id="06923-173">Reagieren mit einer adaptiven Kartennachricht, die von einem Bot gesendet wurde</span><span class="sxs-lookup"><span data-stu-id="06923-173">Respond with an adaptive card message sent from a bot</span></span>

<span data-ttu-id="06923-174">Sie können auch auf die Sendeaktion reagieren, indem Sie eine Nachricht mit einer Adaptive Card mit einem Bot in den Kanal einfügen.</span><span class="sxs-lookup"><span data-stu-id="06923-174">You can also respond to the submit action by inserting a message with an Adaptive Card into the channel with a bot.</span></span> <span data-ttu-id="06923-175">Der Benutzer kann die Nachricht vor dem Absenden in der Vorschau anzeigen und möglicherweise auch bearbeiten/interagieren.</span><span class="sxs-lookup"><span data-stu-id="06923-175">Your user will be able to preview the message before submitting it, and potentially edit/interact with it as well.</span></span> <span data-ttu-id="06923-176">Dies kann in Szenarien sehr nützlich sein, in denen Sie Informationen von Benutzern sammeln müssen, bevor Sie eine adaptive Kartenantwort erstellen.</span><span class="sxs-lookup"><span data-stu-id="06923-176">This can be very useful in scenarios where you need to gather information from your users before creating an adaptive card response.</span></span> <span data-ttu-id="06923-177">Das folgende Szenario zeigt, wie Sie diesen Flow verwenden können, um eine Umfrage zu konfigurieren, ohne die Konfigurationsschritte in die Kanalnachricht einzuschließen.</span><span class="sxs-lookup"><span data-stu-id="06923-177">The following scenario shows how you can use this flow to configure a poll without including the configuration steps in the channel message.</span></span>

1. <span data-ttu-id="06923-178">Der Benutzer klickt auf die Messagingerweiterung, um das Taskmodul auszulösen.</span><span class="sxs-lookup"><span data-stu-id="06923-178">The user clicks the messaging extension to trigger the task module.</span></span>
1. <span data-ttu-id="06923-179">Der Benutzer verwendet das Taskmodul, um die Abfrage zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="06923-179">The user uses the task module to configure the poll.</span></span>
1. <span data-ttu-id="06923-180">Nach dem Absenden des Konfigurationsaufgabenmoduls verwendet die App die im Aufgabenmodul bereitgestellten Informationen, um eine adaptive Karte zu erstellen, und sendet sie als `botMessagePreview` Antwort an den Client.</span><span class="sxs-lookup"><span data-stu-id="06923-180">After submitting the configuration task module the app uses the information provided in the task module to craft an adaptive card and sends it as a `botMessagePreview` response to the client.</span></span>
1. <span data-ttu-id="06923-181">Der Benutzer kann dann eine Vorschau der adaptiven Kartennachricht anzeigen, bevor der Bot sie in den Kanal einfügt.</span><span class="sxs-lookup"><span data-stu-id="06923-181">The user can then preview the adaptive card message before the bot will inserts it into the channel.</span></span> <span data-ttu-id="06923-182">Wenn der Bot noch kein Mitglied des Kanals ist, wird der Bot durch Klicken `Send` hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="06923-182">If the bot is not already a member of the channel, clicking `Send` will add the bot.</span></span>
1. <span data-ttu-id="06923-183">Durch die Interaktion mit der adaptiven Karte wird die Nachricht vor dem Senden geändert.</span><span class="sxs-lookup"><span data-stu-id="06923-183">Interacting with the adaptive card will change the message before sending it.</span></span>
1. <span data-ttu-id="06923-184">Sobald der Benutzer `Send` klickt, wird der Bot die Nachricht an den Kanal senden.</span><span class="sxs-lookup"><span data-stu-id="06923-184">Once the user clicks `Send` the bot will post the message to the channel.</span></span>

<span data-ttu-id="06923-185">Um diesen Flow zu aktivieren, sollte Ihr Aufgabenmodul wie im folgenden Beispiel antworten, in dem dem Benutzer die Vorschaunachricht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="06923-185">To enable this flow your task module should respond as in the example below, which will present the preview message to the user.</span></span>

>[!Note]
><span data-ttu-id="06923-186">Der `activityPreview` muss eine Aktivität mit genau 1 `message` adaptivem Kartenanhang enthalten.</span><span class="sxs-lookup"><span data-stu-id="06923-186">The `activityPreview` must contain a `message` activity with exactly 1 adaptive card attachment.</span></span>

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

<span data-ttu-id="06923-187">Ihre Nachrichtenerweiterung muss nun auf zwei neue Arten von Interaktionen reagieren, `value.botMessagePreviewAction = "send"` und `value.botMessagePreviewAction = "edit"` .</span><span class="sxs-lookup"><span data-stu-id="06923-187">Your message extension will now need to respond to two new types of interactions, `value.botMessagePreviewAction = "send"` and `value.botMessagePreviewAction = "edit"`.</span></span> <span data-ttu-id="06923-188">Im Folgenden finden Sie ein Beispiel für das `value` Objekt, das Sie verarbeiten müssen:</span><span class="sxs-lookup"><span data-stu-id="06923-188">Below is an example of the `value` object you will need to process:</span></span>

```json
{
  "name": "composeExtension/submitAction",
  "type": "invoke",
  "conversation": { "id": "19:c366b75791784100b6e8b515fd55b063@thread.skype" },
  "imdisplayname": "Pranav Smith",
  ...
  "value": {
    "botMessagePreviewAction": "send" | "edit",
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

<span data-ttu-id="06923-189">Wenn Sie auf die Anforderung antworten, `edit` sollten Sie mit einer Antwort mit den Werten antworten, die mit den Informationen aufgefüllt sind, die der Benutzer bereits übermittelt `task` hat.</span><span class="sxs-lookup"><span data-stu-id="06923-189">When responding to the `edit` request you should respond with a `task` response with the values populated with the information the user has already submitted.</span></span> <span data-ttu-id="06923-190">Wenn Sie auf die Anforderung antworten, `send` sollten Sie eine Nachricht an den Kanal senden, der die abgeschlossene adaptive Karte enthält.</span><span class="sxs-lookup"><span data-stu-id="06923-190">When responding to the `send` request you should send a message to the channel containing the finalized adaptive card.</span></span>

# <a name="typescriptnodejs"></a>[<span data-ttu-id="06923-191">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="06923-191">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript
teamChatConnector.onComposeExtensionSubmitAction((
    event: builder.IEvent,
    request: teamBuilder.IComposeExtensionActionCommandRequest,
    callback: (err: Error, result: any, statusCode: number) => void) => {
        let invokeValue = (<any> event).value;

        if (invokeValue.botMessagePreviewAction ) {
            let attachment = invokeValue.botActivityPreview[0].attachments[0];

            if (invokeValue.botMessagePreviewAction === 'send') {
                let msg = new builder.Message()
                    .address(event.address)
                    .addAttachment(attachment);
                teamChatConnector.send([msg.toMessage()],
                    (error) => {
                        if(error){
                            //TODO: Handle error and callback
                        }
                        else {
                            callback(null, null, 200);
                        }
                    }
                );
            }

            else if (invokeValue.botMessagePreviewAction === 'edit') {
              // Create the card and populate with user-inputted information
              let card = { ... }

              let taskResponse = {
                task: {
                  type: "continue",
                  value: {
                    title: "Card Preview",
                    card: {
                      contentType: 'application/vnd.microsoft.card.adaptive',
                      content: card
                    }
                  }
                }
              }
              callback(null, taskResponse, 200);
            }

        else {
            let attachment = {
                  //create adaptive card
                };
            let activity = new builder.Message().addAttachment(attachment).toMessage();
            let response = teamBuilder.ComposeExtensionResponse.messagePreview()
                .preview(activity)
                .toResponse();
            callback(null, response, 200);
        }
    });
```

# <a name="cnet"></a>[<span data-ttu-id="06923-192">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="06923-192">C#/.NET</span></span>](#tab/dotnet)

<span data-ttu-id="06923-193">Dieses Beispiel zeigt diesen Flow mit dem [Microsoft.Bot.Connector.Teams SDK (v3)](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams).</span><span class="sxs-lookup"><span data-stu-id="06923-193">This sample shows this flow using the [Microsoft.Bot.Connector.Teams SDK (v3)](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams).</span></span>

```csharp
public class MessagesController : ApiController
{

    [BotAuthentication]
    public async Task<HttpResponseMessage> Post([FromBody]Activity activity)
    {
        MicrosoftAppCredentials.TrustServiceUrl(activity.ServiceUrl, DateTime.MaxValue);
        ConnectorClient connectorClient = new ConnectorClient(
            new Uri(activity.ServiceUrl),
            ConfigurationManager.AppSettings[MicrosoftAppCredentials.MicrosoftAppIdKey],
            ConfigurationManager.AppSettings[MicrosoftAppCredentials.MicrosoftAppPasswordKey]);

        if (activity.Type == ActivityTypes.Invoke)
        {
            // Initial task module presented to the user
            if (activity.Name == "composeExtension/fetchTask")
            {
                string task = GetTaskModule();

                return Request.CreateResponse(HttpStatusCode.OK, JObject.Parse(task));
            }
            else if (activity.Name == "composeExtension/submitAction")
            {
                dynamic activityValue = JObject.FromObject(activity.Value);
                string botMessagePreviewAction = activityValue["botMessagePreviewAction"];

                //This is the initial card response sent after the task module is submitted
                if (botMessagePreviewAction is null)
                {
                    string text = activityValue.data.cardMessage;

                    AdaptiveCard card = new AdaptiveCard(new AdaptiveSchemaVersion("1.0"));
                    card.Body.Add(new AdaptiveTextBlock()
                    {
                        Text = "This card will be inserted into the conversation by the bot.",
                        Size = AdaptiveTextSize.Large,
                        Wrap = true
                    });
                    card.Body.Add(new AdaptiveTextBlock()
                    {
                        Text = "The text below is what you provided."
                    });
                    card.Body.Add(new AdaptiveTextBlock()
                    {
                        Text = text,
                    });

                    string cardJson = card.ToJson();

                    string cardMessage = $@"{{
                        'composeExtension': {{
                        'type': 'botMessagePreview',
                        'activityPreview': {{
                            'type': 'message',
                            'attachments': [{{
                                'contentType': 'application/vnd.microsoft.card.adaptive',
                                'content': {cardJson}
                            }}]
                        }}
                        }}
                    }}";

                    JObject res = JObject.Parse(cardMessage);
                    return Request.CreateResponse(HttpStatusCode.OK, res);

                }
                else
                {
                    //This is the "send the card to the channel" event
                    if (botMessagePreviewAction.Equals("send"))
                    {
                        string cardJson = JsonConvert.SerializeObject(activityValue.botActivityPreview[0].attachments[0].content);

                        AdaptiveCardParseResult cardResult = AdaptiveCard.FromJson(cardJson);
                        AdaptiveCard card = cardResult.Card;
                        Attachment cardAttachment = new Attachment
                        {
                            ContentType = AdaptiveCard.ContentType,
                            Content = card
                        };


                        Activity response = activity.CreateReply();
                        response.Attachments.Add(cardAttachment);

                        var result = await connectorClient.Conversations.SendToConversationAsync(response);
                    }
                    //This is fired if the user edits the card before sending it
                    else if (botMessagePreviewAction.Equals("edit"))
                    {
                        string task = GetTaskModule();

                        return Request.CreateResponse(HttpStatusCode.OK, JObject.Parse(task));
                    }
                    else
                    {
                        return Request.CreateResponse(HttpStatusCode.NotImplemented);
                    }
                }
            }
        }

        return Request.CreateResponse(HttpStatusCode.NotImplemented);

    }

    private static string GetTaskModule()
    {
        AdaptiveCard card = new AdaptiveCard(new AdaptiveSchemaVersion("1.0"));
        card.Body.Add(new AdaptiveTextBlock()
        {
            Text = "Please enter the following information:",
            Size = AdaptiveTextSize.Large
        });
        card.Body.Add(new AdaptiveTextBlock()
        {
            Text = "Card Message:"
        });
        card.Body.Add(new AdaptiveTextInput()
        {
            Id = "cardMessage",
            Spacing = AdaptiveSpacing.None,
            Placeholder = "Card message goes here."
        });
        card.Actions.Add(new AdaptiveSubmitAction()
        {
            Title = "Submit"
        });

        string cardJson = card.ToJson();

        //Create the task module response
        string task = $@"{{
                            'task': {{
                                'type': 'continue',
                                'value': {{
                                    'card': {{
                                        'contentType': 'application/vnd.microsoft.card.adaptive',
                                        'content': {cardJson}
                                        }}
                                    }}
                                }}
                            }}";
        return task;
    }

}
```

## <a name="see-also"></a><span data-ttu-id="06923-194">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="06923-194">See also</span></span>

[<span data-ttu-id="06923-195">Bot Framework-Beispiele</span><span class="sxs-lookup"><span data-stu-id="06923-195">Bot Framework samples</span></span>](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)