---
title: Initiieren von Aktionen mit Messaging Erweiterungen
description: Erstellen Aktions basierter Messaging Erweiterungen, um Benutzern das Auslösen externer Dienste zu ermöglichen
keywords: Microsoft Teams Messaging Extensions Messaging Extensions Search
ms.openlocfilehash: 4eb5984f4a75f185accfe7ba87e9389361946959
ms.sourcegitcommit: 6c786434b56cc8c2765a14aa1f6149870245f309
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2020
ms.locfileid: "44801370"
---
# <a name="initiate-actions-with-messaging-extensions"></a><span data-ttu-id="76700-104">Initiieren von Aktionen mit Messaging Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="76700-104">Initiate actions with messaging extensions</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-me.md)]

<span data-ttu-id="76700-105">Aktionsbasierte Messaging Erweiterungen ermöglichen es Ihren Benutzern, Aktionen in externen Diensten innerhalb von Teams auszulösen.</span><span class="sxs-lookup"><span data-stu-id="76700-105">Action-based messaging extensions allow your users to trigger actions in external services while inside of Teams.</span></span>

![Beispiel für eine Messaging Erweiterungskarte](~/assets/images/compose-extensions/ceexample.png)

<span data-ttu-id="76700-107">In den folgenden Abschnitten wird die Vorgehensweise beschrieben.</span><span class="sxs-lookup"><span data-stu-id="76700-107">The following sections describe how to do this.</span></span>

[!include[Common content for creating extensions](~/includes/messaging-extensions/messaging-extensions-common.md)]

### <a name="action-type-message-extensions"></a><span data-ttu-id="76700-108">Nachrichten Erweiterungen für Aktionstypen</span><span class="sxs-lookup"><span data-stu-id="76700-108">Action type message extensions</span></span>

<span data-ttu-id="76700-109">Um Aktionen aus einer Messaging Erweiterung zu initiieren `type` , legen Sie den Parameter auf fest `action` .</span><span class="sxs-lookup"><span data-stu-id="76700-109">To initiate actions from a  messaging extension set the `type` parameter to `action`.</span></span> <span data-ttu-id="76700-110">Unten sehen Sie ein Beispiel für ein Manifest mit einer Suche und einem Create-Befehl.</span><span class="sxs-lookup"><span data-stu-id="76700-110">Below is an example of a manifest with a search and a create command.</span></span> <span data-ttu-id="76700-111">Eine einzelne Messaging Erweiterung kann bis zu zehn verschiedene Befehle haben.</span><span class="sxs-lookup"><span data-stu-id="76700-111">A single messaging extension can have up to 10 different commands.</span></span> <span data-ttu-id="76700-112">Dies kann sowohl mehrere Suchfunktionen als auch mehrere Aktionsbasierte Befehle umfassen.</span><span class="sxs-lookup"><span data-stu-id="76700-112">This can include both multiple search and multiple action-based commands.</span></span>

#### <a name="complete-app-manifest-example"></a><span data-ttu-id="76700-113">Beispiel für ein vollständiges App-Manifest</span><span class="sxs-lookup"><span data-stu-id="76700-113">Complete app manifest example</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json",
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

### <a name="initiate-actions-from-messages"></a><span data-ttu-id="76700-114">Initiieren von Aktionen aus Nachrichten</span><span class="sxs-lookup"><span data-stu-id="76700-114">Initiate actions from messages</span></span>

<span data-ttu-id="76700-115">Zusätzlich zum Initiieren von Aktionen aus dem Bereich zum Verfassen von Nachrichten können Sie auch Ihre Messaging Erweiterung verwenden, um eine Aktion aus einer Nachricht zu initiieren.</span><span class="sxs-lookup"><span data-stu-id="76700-115">In addition to initiating actions from the compose message area, you can also use your messaging extension to initiate an action from a message.</span></span> <span data-ttu-id="76700-116">Auf diese Weise können Sie den Inhalt der Nachricht an Ihren bot zur Verarbeitung senden und auf diese Nachricht optional mit einer Antwort Antworten, die unter [Antworten auf Senden](#responding-to-submit)beschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="76700-116">This will allow you to send the contents of the message to your bot for processing, and optionally reply to that message with a response using the method described in [Responding to submit](#responding-to-submit).</span></span> <span data-ttu-id="76700-117">Die Antwort wird als Antwort auf die Nachricht eingefügt, die Ihre Benutzer vor dem Senden bearbeiten können.</span><span class="sxs-lookup"><span data-stu-id="76700-117">The response will be inserted as a reply to the message that your users can edit before submitting.</span></span> <span data-ttu-id="76700-118">Ihre Benutzer können über das Menü Überlauf auf Ihre Messaging Erweiterung zugreifen `...` und dann `Take action` wie in der Abbildung unten auswählen.</span><span class="sxs-lookup"><span data-stu-id="76700-118">Your users can access your messaging extension from the overflow `...` menu and then selecting `Take action` as in the image below.</span></span>

![Beispiel für das Initiieren einer Aktion aus einer Nachricht](~/assets/images/compose-extensions/messageextensions_messageaction.png)

<span data-ttu-id="76700-120">Damit Ihre Messaging Erweiterung mit einer Nachricht funktioniert, müssen Sie den `context` Parameter dem Objekt Ihrer Messaging Erweiterung im App-Manifest hinzufügen, `commands` wie im folgenden Beispiel dargestellt.</span><span class="sxs-lookup"><span data-stu-id="76700-120">To enable your messaging extension to work from a message you'll need to add the `context` parameter to your messaging extension's `commands` object in your app manifest as in the example below.</span></span> <span data-ttu-id="76700-121">Gültige Zeichenfolgen für das `context` Array sind `"message"` , `"commandBox"` und `"compose"` .</span><span class="sxs-lookup"><span data-stu-id="76700-121">Valid strings for the `context` array are `"message"`, `"commandBox"`, and `"compose"`.</span></span> <span data-ttu-id="76700-122">Der Standardwert ist `["compose", "commandBox"]`.</span><span class="sxs-lookup"><span data-stu-id="76700-122">The default value is `["compose", "commandBox"]`.</span></span> <span data-ttu-id="76700-123">Ausführliche Informationen zum Parameter finden Sie im Abschnitt [define Commands](#define-commands) `context` .</span><span class="sxs-lookup"><span data-stu-id="76700-123">See the [define commands](#define-commands) section for complete details on the `context` parameter.</span></span>

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

<span data-ttu-id="76700-124">Unten sehen Sie ein Beispiel für das Objekt, das `value` die Nachrichtendetails enthält, die gesendet werden, wenn ein Teil der `composeExtension` Anforderung an Ihren bot gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="76700-124">Below is an example of the `value` object containing the message details that will be sent as part of the `composeExtension` request be sent to your bot.</span></span>

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

### <a name="test-via-uploading"></a><span data-ttu-id="76700-125">Testen über hochladen</span><span class="sxs-lookup"><span data-stu-id="76700-125">Test via uploading</span></span>

<span data-ttu-id="76700-126">Sie können Ihre Messaging Erweiterung testen, indem Sie Ihre APP hochladen.</span><span class="sxs-lookup"><span data-stu-id="76700-126">You can test your messaging extension by uploading your app.</span></span> <span data-ttu-id="76700-127">Weitere Informationen finden Sie unter [Hochladen Ihrer APP in einem Team](~/concepts/deploy-and-publish/apps-upload.md) .</span><span class="sxs-lookup"><span data-stu-id="76700-127">See [Uploading your app in a team](~/concepts/deploy-and-publish/apps-upload.md) for details.</span></span>

<span data-ttu-id="76700-128">Um Ihre Messaging Erweiterung zu öffnen, navigieren Sie zu einem beliebigen Chat oder Kanal.</span><span class="sxs-lookup"><span data-stu-id="76700-128">To open your messaging extension, navigate to any of your chats or channels.</span></span> <span data-ttu-id="76700-129">Wählen Sie im Feld Verfassen die Schaltfläche **Weitere Optionen** (**&#8943;**) aus, und wählen Sie Ihre Messaging Erweiterung aus.</span><span class="sxs-lookup"><span data-stu-id="76700-129">Choose the **More options** (**&#8943;**) button in the compose box, and choose your messaging extension.</span></span>

## <a name="collecting-input-from-users"></a><span data-ttu-id="76700-130">Sammeln von Eingaben von Benutzern</span><span class="sxs-lookup"><span data-stu-id="76700-130">Collecting input from users</span></span>

<span data-ttu-id="76700-131">Es gibt drei Möglichkeiten zum Erfassen von Informationen von einem Endbenutzer in Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="76700-131">There are three ways to collect information from an end user in Teams.</span></span>

### <a name="static-parameter-list"></a><span data-ttu-id="76700-132">Liste der statischen Parameter</span><span class="sxs-lookup"><span data-stu-id="76700-132">Static parameter list</span></span>

<span data-ttu-id="76700-133">In dieser Methode müssen Sie lediglich eine statische Liste von Parametern im Manifest definieren, wie oben im Befehl "Create to do" dargestellt.</span><span class="sxs-lookup"><span data-stu-id="76700-133">In this method, all you need to do is define a static list of parameters in the manifest as shown above in the "Create To Do" command.</span></span> <span data-ttu-id="76700-134">Um diese Methode zu verwenden, ist sichergestellt, `fetchTask` `false` dass Sie die Parameter im Manifest definieren und festlegen.</span><span class="sxs-lookup"><span data-stu-id="76700-134">To use this method ensure `fetchTask` is set to `false` and that you define your parameters in the manifest.</span></span>

<span data-ttu-id="76700-135">Wenn ein Benutzer einen Befehl mit statischen Parametern auswählt, generiert Microsoft Teams ein Formular in einem Aufgabenmodul, wobei die im Manifest definierten Parameter verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="76700-135">When a user chooses a command with static parameters, Teams will generate a form in a Task Module with the parameters defined in the manifest.</span></span> <span data-ttu-id="76700-136">Beim Drücken von Submit `composeExtension/submitAction` wird a an den bot gesendet.</span><span class="sxs-lookup"><span data-stu-id="76700-136">On hitting Submit a `composeExtension/submitAction` is sent to the bot.</span></span> <span data-ttu-id="76700-137">Weitere Informationen zu den erwarteten Antworten finden Sie im Thema [Antworten auf Submit](#responding-to-submit) .</span><span class="sxs-lookup"><span data-stu-id="76700-137">See the topic [Responding to submit](#responding-to-submit) for more information on the expected set of responses.</span></span>

### <a name="dynamic-input-using-an-adaptive-card"></a><span data-ttu-id="76700-138">Dynamische Eingabe mithilfe einer adaptiven Karte</span><span class="sxs-lookup"><span data-stu-id="76700-138">Dynamic input using an adaptive card</span></span>

<span data-ttu-id="76700-139">Bei dieser Methode kann Ihr Dienst eine benutzerdefinierte Adaptive Karte definieren, um die Benutzereingabe zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="76700-139">In this method, your service can define a custom adaptive card to collect the end user input.</span></span> <span data-ttu-id="76700-140">Legen Sie für diesen Ansatz den `fetchTask` Parameter auf `true` im Manifest fest.</span><span class="sxs-lookup"><span data-stu-id="76700-140">For this approach, set the `fetchTask` parameter to `true` in the manifest.</span></span> <span data-ttu-id="76700-141">Beachten Sie, dass bei Festlegung `fetchTask` auf `true` statische Parameter, die für den Befehl definiert sind, ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="76700-141">Note that if you set `fetchTask` to `true` any static parameters defined for the command will be ignored.</span></span>

<span data-ttu-id="76700-142">In dieser Methode erhält Ihr Dienst ein `composeExtension/fetchTask` Ereignis und muss mit einer adaptiven kartenbasierten Antwort auf [Aufgabenmodul](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object)Antworten.</span><span class="sxs-lookup"><span data-stu-id="76700-142">In this method your service will receive a `composeExtension/fetchTask` event and needs to respond with an adaptive card based [task module response](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object).</span></span> <span data-ttu-id="76700-143">Unten sehen Sie eine Beispielantwort mit einer adaptiven Karte:</span><span class="sxs-lookup"><span data-stu-id="76700-143">Below is an sample response with an adaptive card:</span></span>

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

<span data-ttu-id="76700-144">Der Bot kann auch mit einer auth/config-Antwort Antworten, wenn der Benutzer die Erweiterung authentifizieren oder konfigurieren muss, bevor er die Benutzereingabe erhält.</span><span class="sxs-lookup"><span data-stu-id="76700-144">The bot can also respond with an auth/config response if the user needs to authenticate or configure the extension before getting the user input.</span></span>

### <a name="dynamic-input-using-a-web-view"></a><span data-ttu-id="76700-145">Dynamische Eingabe mithilfe einer Webansicht</span><span class="sxs-lookup"><span data-stu-id="76700-145">Dynamic input using a web view</span></span>

<span data-ttu-id="76700-146">In dieser Methode kann Ihr Dienst ein `<iframe>` basiertes Widget anzeigen, um eine benutzerdefinierte Benutzeroberfläche anzuzeigen und Benutzereingaben zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="76700-146">In this method your service can show an `<iframe>` based widget to show any custom UI and collect user input.</span></span> <span data-ttu-id="76700-147">Legen Sie für diesen Ansatz den `fetchTask` Parameter auf `true` im Manifest fest.</span><span class="sxs-lookup"><span data-stu-id="76700-147">For this approach, set the `fetchTask` parameter to `true` in the manifest.</span></span>

<span data-ttu-id="76700-148">Genau wie beim adaptiven Karten Fluss wird Ihr Dienst ein Ereignis senden `fetchTask` und muss mit einer URL-basierten [Aufgabenmodul Antwort](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object)Antworten.</span><span class="sxs-lookup"><span data-stu-id="76700-148">Just like in the adaptive card flow your service will be send a `fetchTask` event and needs to respond with a URL based [task module response](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object).</span></span> <span data-ttu-id="76700-149">Unten sehen Sie eine Beispielantwort mit einer adaptiven Karte:</span><span class="sxs-lookup"><span data-stu-id="76700-149">Below is an sample response with an Adaptive card:</span></span>

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

### <a name="request-to-install-your-conversational-bot"></a><span data-ttu-id="76700-150">Anforderung zum Installieren Ihres Unterhaltungs-bot</span><span class="sxs-lookup"><span data-stu-id="76700-150">Request to install your conversational bot</span></span>

<span data-ttu-id="76700-151">Wenn Ihre APP auch einen Unterhaltungs-bot enthält, müssen Sie möglicherweise sicherstellen, dass Ihr bot in der Unterhaltung installiert ist, bevor Sie den Aufgabenmodul laden.</span><span class="sxs-lookup"><span data-stu-id="76700-151">If your app also contains a conversational bot, it may be necessary to ensure that your bot is installed in the conversation before loading your task module.</span></span> <span data-ttu-id="76700-152">Dies kann in Situationen hilfreich sein, in denen Sie zusätzlichen Kontext für Ihr Aufgabenmodul erhalten müssen.</span><span class="sxs-lookup"><span data-stu-id="76700-152">This can be useful in situations where you need to get additional context for you task module.</span></span> <span data-ttu-id="76700-153">Beispielsweise müssen Sie möglicherweise das Dienstplan Verzeichnis abrufen, um ein Personenauswahl-Steuerelement oder die Liste der Kanäle in einem Team aufzufüllen.</span><span class="sxs-lookup"><span data-stu-id="76700-153">For example, you may need to fetch the roster to populate a people picker control, or the list of channels in a team.</span></span>

<span data-ttu-id="76700-154">Um diesen Fluss zu erleichtern, wenn Ihre Messaging-Erweiterung zuerst die `composeExtension/fetchTask` Invoke-Überprüfung erhält, um festzustellen, ob Ihr bot im aktuellen Kontext installiert ist (Sie können dies beispielsweisedurch den Aufruf des Get-Dienstplan Aufrufs erreichen).</span><span class="sxs-lookup"><span data-stu-id="76700-154">To facilitate this flow, when your messaging extension first receives the `composeExtension/fetchTask` invoke check to see if your bot is installed in the current context (you could accomplish this by attempting the get roster call, for example).</span></span> <span data-ttu-id="76700-155">Wenn Ihr bot nicht installiert ist, geben Sie eine Adaptive Karte mit einer Aktion zurück, die den Benutzer anfordert, ihren bot zu installieren, siehe das Beispiel unten.</span><span class="sxs-lookup"><span data-stu-id="76700-155">If your bot is not installed, you return an Adaptive Card with an action that requests the user to install your bot See the example below.</span></span> <span data-ttu-id="76700-156">Beachten Sie, dass dies erfordert, dass der Benutzer über die Berechtigung zum Installieren von apps an diesem Speicherort verfügt. Wenn dies nicht möglich ist, wird eine Meldung angezeigt, in der Sie aufgefordert werden, Ihren Administrator zu kontaktieren.</span><span class="sxs-lookup"><span data-stu-id="76700-156">Note that this requires the user to have permission to install apps in that location; if they cannot they will be presented with a message asking them to contact their administrator.</span></span>

<span data-ttu-id="76700-157">Hier ist ein Beispiel für die Antwort:</span><span class="sxs-lookup"><span data-stu-id="76700-157">Here's an example of the response:</span></span>

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

<span data-ttu-id="76700-158">Sobald der Benutzer die Installation abgeschlossen hat, erhält der bot eine weitere Invoke-Nachricht mit `name = composeExtension/submitAction` und `value.data.msteams.justInTimeInstall = true` .</span><span class="sxs-lookup"><span data-stu-id="76700-158">Once the user completes the installation, your bot will receive another invoke message with `name = composeExtension/submitAction`, and `value.data.msteams.justInTimeInstall = true`.</span></span>

<span data-ttu-id="76700-159">Hier ist ein Beispiel für den Aufruf:</span><span class="sxs-lookup"><span data-stu-id="76700-159">Here's an example of the invoke:</span></span>

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

<span data-ttu-id="76700-160">Sie sollten auf diesen Aufruf mit derselben Antwort Antworten, auf die Sie reagiert haben, wenn der bot bereits installiert wurde.</span><span class="sxs-lookup"><span data-stu-id="76700-160">You should respond to this invoke with the same task response you would have responded with if the bot was already installed.</span></span>

## <a name="responding-to-submit"></a><span data-ttu-id="76700-161">Reagieren auf Submit</span><span class="sxs-lookup"><span data-stu-id="76700-161">Responding to submit</span></span>

<span data-ttu-id="76700-162">Sobald ein Benutzer seine Eingabe abgeschlossen hat, erhält der bot ein `composeExtension/submitAction` Ereignis mit den festgelegten Befehls-IDs und Parameterwerten.</span><span class="sxs-lookup"><span data-stu-id="76700-162">Once a user completes entering their input your bot will receive a `composeExtension/submitAction` event with the command id and parameter values set.</span></span>

<span data-ttu-id="76700-163">Dies sind die unterschiedlichen erwarteten Antworten auf a `submitAction` .</span><span class="sxs-lookup"><span data-stu-id="76700-163">These are the different expected responses to a `submitAction`.</span></span>

### <a name="task-module-response"></a><span data-ttu-id="76700-164">Antwort des Aufgabenmoduls</span><span class="sxs-lookup"><span data-stu-id="76700-164">Task Module response</span></span>

<span data-ttu-id="76700-165">Dies wird verwendet, wenn Ihre Erweiterung Dialogfelder miteinander verketten muss, um weitere Informationen zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="76700-165">This is used when your extension needs to chain dialogs together to get more information.</span></span> <span data-ttu-id="76700-166">Die Antwort ist genau die gleiche wie `fetchTask` zuvor erwähnt.</span><span class="sxs-lookup"><span data-stu-id="76700-166">The response is exactly the same as `fetchTask` mentioned earlier.</span></span>

### <a name="compose-extension-authconfig-response"></a><span data-ttu-id="76700-167">Antwort zum Verfassen der Durchwahl Authentifizierung/-Konfiguration</span><span class="sxs-lookup"><span data-stu-id="76700-167">Compose extension auth/config response</span></span>

<span data-ttu-id="76700-168">Dies wird verwendet, wenn Ihre Erweiterung entweder authentifiziert oder konfiguriert werden muss, um den Vorgang fortzusetzen.</span><span class="sxs-lookup"><span data-stu-id="76700-168">This is used when your extension needs to either authenticate or configure in order to continue.</span></span> <span data-ttu-id="76700-169">Weitere Informationen finden Sie im [Abschnitt "Authentifizierung"](~/resources/messaging-extension-v3/search-extensions.md#authentication) im Abschnitt "Suche".</span><span class="sxs-lookup"><span data-stu-id="76700-169">See [authentication section](~/resources/messaging-extension-v3/search-extensions.md#authentication) in the search section for more details.</span></span>

### <a name="compose-extension-result-response"></a><span data-ttu-id="76700-170">Antwort zum Verfassen der Ergebnis Erweiterung</span><span class="sxs-lookup"><span data-stu-id="76700-170">Compose extension result response</span></span>

<span data-ttu-id="76700-171">Dadurch wird eine Karte als Ergebnis eines Befehls in das Feld Verfassen eingefügt.</span><span class="sxs-lookup"><span data-stu-id="76700-171">This used to insert a card into the compose box as a result of a the command.</span></span> <span data-ttu-id="76700-172">Es ist die gleiche Antwort, die im Suchbefehl verwendet wird, aber Sie ist auf eine Karte oder ein Ergebnis im Array limitiert.</span><span class="sxs-lookup"><span data-stu-id="76700-172">It's the same response that's used in the search command, but it's limited to one card or one result in the array.</span></span>

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
              "activityImage": "https://placekitten.com/200/200"
            },
            {
              "title": "Details",
              "facts": [
                {
                  "name": "Assigned to:",
                  "value": "[Larry Brown](mailto:larryb@example.com)"
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

### <a name="respond-with-an-adaptive-card-message-sent-from-a-bot"></a><span data-ttu-id="76700-173">Antworten mit einer adaptiven Karten Nachricht, die von einem bot gesendet wurde</span><span class="sxs-lookup"><span data-stu-id="76700-173">Respond with an adaptive card message sent from a bot</span></span>

<span data-ttu-id="76700-174">Sie können auch auf die Submit-Aktion reagieren, indem Sie eine Nachricht mit einer adaptiven Karte in den Kanal mit einem bot einfügen.</span><span class="sxs-lookup"><span data-stu-id="76700-174">You can also respond to the submit action by inserting a message with an Adaptive Card into the channel with a bot.</span></span> <span data-ttu-id="76700-175">Der Benutzer kann die Nachricht in einer Vorschau anzeigen, bevor er ihn sendet, und möglicherweise auch mit ihm bearbeiten/interagieren.</span><span class="sxs-lookup"><span data-stu-id="76700-175">Your user will be able to preview the message before submitting it, and potentially edit/interact with it as well.</span></span> <span data-ttu-id="76700-176">Dies kann in Szenarien hilfreich sein, in denen Sie Informationen von Ihren Benutzern sammeln müssen, bevor Sie eine Adaptive Karten Antwort erstellen.</span><span class="sxs-lookup"><span data-stu-id="76700-176">This can be very useful in scenarios where you need to gather information from your users before creating an adaptive card response.</span></span> <span data-ttu-id="76700-177">Das folgende Szenario zeigt, wie Sie diesen Fluss zum Konfigurieren einer Umfrage verwenden können, ohne die Konfigurationsschritte in die Kanal Nachricht einzuschließen.</span><span class="sxs-lookup"><span data-stu-id="76700-177">The following scenario shows how you can use this flow to configure a poll without including the configuration steps in the channel message.</span></span>

1. <span data-ttu-id="76700-178">Der Benutzer klickt auf die Messaging Erweiterung, um den Aufgabenmodul auszulösen.</span><span class="sxs-lookup"><span data-stu-id="76700-178">The user clicks the messaging extension to trigger the task module.</span></span>
1. <span data-ttu-id="76700-179">Der Benutzer verwendet den Aufgabenmodul zum Konfigurieren der Umfrage.</span><span class="sxs-lookup"><span data-stu-id="76700-179">The user uses the task module to configure the poll.</span></span>
1. <span data-ttu-id="76700-180">Nach dem Senden des Konfigurationsaufgaben Moduls verwendet die APP die im Aufgabenmodul bereitgestellten Informationen, um eine Adaptive Karte zu basteln und Sie als `botMessagePreview` Antwort an den Client zu senden.</span><span class="sxs-lookup"><span data-stu-id="76700-180">After submitting the configuration task module the app uses the information provided in the task module to craft an adaptive card and sends it as a `botMessagePreview` response to the client.</span></span>
1. <span data-ttu-id="76700-181">Der Benutzer kann dann eine Vorschau der adaptiven Karten Nachricht anzeigen, bevor der bot ihn in den Kanal einfügt.</span><span class="sxs-lookup"><span data-stu-id="76700-181">The user can then preview the adaptive card message before the bot will inserts it into the channel.</span></span> <span data-ttu-id="76700-182">Wenn der bot noch kein Mitglied des Kanals ist, `Send` wird der bot durch Klicken hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="76700-182">If the bot is not already a member of the channel, clicking `Send` will add the bot.</span></span>
1. <span data-ttu-id="76700-183">Bei der Interaktion mit der adaptiven Karte wird die Nachricht vor dem Senden geändert.</span><span class="sxs-lookup"><span data-stu-id="76700-183">Interacting with the adaptive card will change the message before sending it.</span></span>
1. <span data-ttu-id="76700-184">Nachdem der Benutzer `Send` auf den bot geklickt hat, wird die Nachricht an den Kanal gesendet.</span><span class="sxs-lookup"><span data-stu-id="76700-184">Once the user clicks `Send` the bot will post the message to the channel.</span></span>

<span data-ttu-id="76700-185">Zum Aktivieren dieses Flusses sollte Ihr Aufgabenmodul wie im folgenden Beispiel reagieren, das die Vorschau Nachricht an den Benutzer weiter gibt.</span><span class="sxs-lookup"><span data-stu-id="76700-185">To enable this flow your task module should respond as in the example below, which will present the preview message to the user.</span></span>

>[!Note]
><span data-ttu-id="76700-186">Das `activityPreview` muss eine `message` Aktivität mit genau 1 adaptiver Karten Anlage enthalten.</span><span class="sxs-lookup"><span data-stu-id="76700-186">The `activityPreview` must contain a `message` activity with exactly 1 adaptive card attachment.</span></span>

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

<span data-ttu-id="76700-187">Ihre Nachrichten Erweiterung muss nun auf zwei neue Arten von Interaktionen reagieren `value.botMessagePreviewAction = "send"` und `value.botMessagePreviewAction = "edit"` .</span><span class="sxs-lookup"><span data-stu-id="76700-187">Your message extension will now need to respond to two new types of interactions, `value.botMessagePreviewAction = "send"` and `value.botMessagePreviewAction = "edit"`.</span></span> <span data-ttu-id="76700-188">Nachfolgend finden Sie ein Beispiel für das `value` Objekt, das Sie verarbeiten müssen:</span><span class="sxs-lookup"><span data-stu-id="76700-188">Below is an example of the `value` object you will need to process:</span></span>

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

<span data-ttu-id="76700-189">Bei der Antwort auf die `edit` Anforderung sollten Sie mit einer `task` Antwort mit den Werten Antworten, die mit den Informationen aufgefüllt sind, die der Benutzer bereits übermittelt hat.</span><span class="sxs-lookup"><span data-stu-id="76700-189">When responding to the `edit` request you should respond with a `task` response with the values populated with the information the user has already submitted.</span></span> <span data-ttu-id="76700-190">Wenn Sie auf die `send` Anforderung reagieren, sollten Sie eine Nachricht an den Kanal senden, der die fertige Adaptive Karte enthält.</span><span class="sxs-lookup"><span data-stu-id="76700-190">When responding to the `send` request you should send a message to the channel containing the finalized adaptive card.</span></span>

# <a name="typescriptnodejs"></a>[<span data-ttu-id="76700-191">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="76700-191">TypeScript/Node.js</span></span>](#tab/typescript)

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

<span data-ttu-id="76700-192">*Siehe auch* [bot Framework-Beispiele](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).</span><span class="sxs-lookup"><span data-stu-id="76700-192">*See also* [Bot Framework samples](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).</span></span>

# <a name="cnet"></a>[<span data-ttu-id="76700-193">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="76700-193">C#/.NET</span></span>](#tab/dotnet)

<span data-ttu-id="76700-194">In diesem Beispiel wird dieser Ablauf mithilfe des [Microsoft. bot. Connector. Teams SDK (v3)](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams)veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="76700-194">This sample shows this flow using the [Microsoft.Bot.Connector.Teams SDK (v3)](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams).</span></span>

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
