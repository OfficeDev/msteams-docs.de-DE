---
title: Initiieren von Aktionen mit Messaging-Erweiterungen
description: Erstellen von aktionsbasierten Messaging-Erweiterungen, damit Benutzer externe Dienste auslösen können
ms.localizationpriority: medium
ms.topic: how-to
keywords: Messaging-Erweiterungen für Teams – Suche nach Messaging-Erweiterungen
ms.openlocfilehash: 56dcf316eb430b9745856469eaf837ffe7c0bc00
ms.sourcegitcommit: 22c9e44437720d30c992a4a3626a2a9f745983c1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2021
ms.locfileid: "60720379"
---
# <a name="initiate-actions-with-messaging-extensions"></a>Initiieren von Aktionen mit Messaging-Erweiterungen

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-me.md)]

Aktionsbasierte Messaging-Erweiterungen ermöglichen Es Ihren Benutzern, Aktionen in externen Diensten während Teams auszulösen.

![Beispiel für eine Messaging-Erweiterungskarte](~/assets/images/compose-extensions/ceexample.png)

In den folgenden Abschnitten wird dies beschrieben:

[!include[Common content for creating extensions](~/includes/messaging-extensions/messaging-extensions-common.md)]

### <a name="action-type-message-extensions"></a>Nachrichtenerweiterungen des Aktionstyps

Um Aktionen von einer Messaging-Erweiterung aus zu initiieren, legen Sie den `type` Parameter auf `action` . Unten sehen Sie ein Beispiel für ein Manifest mit einer Suche und einem Befehl zum Erstellen. Eine einzelne Messaging-Erweiterung kann bis zu 10 verschiedene Befehle enthalten. Dies kann sowohl mehrere Suchbefehle als auch mehrere aktionsbasierte Befehle umfassen.

#### <a name="complete-app-manifest-example"></a>Beispiel für ein vollständiges App-Manifest

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

### <a name="initiate-actions-from-messages"></a>Initiieren von Aktionen aus Nachrichten

Zusätzlich zum Initiieren von Aktionen aus dem Bereich zum Verfassen von Nachrichten können Sie auch Ihre Messaging-Erweiterung verwenden, um eine Aktion aus einer Nachricht auszulösen. Auf diese Weise können Sie den Nachrichteninhalt zur Verarbeitung an Ihren Bot senden und optional mit einer Antwort mithilfe der Methode antworten, die unter [Antworten zum Senden](#responding-to-submit)beschrieben wird. Die Antwort wird als Antwort auf die Nachricht eingefügt, die Ihre Benutzer vor dem Senden bearbeiten können. Ihre Benutzer können über das Überlaufmenü auf die Messaging-Erweiterung zugreifen `...` und dann wie in der folgenden Abbildung `Take action` auswählen:

![Beispiel für das Initiieren einer Aktion aus einer Nachricht](~/assets/images/compose-extensions/messageextensions_messageaction.png)

Damit Ihre Messaging-Erweiterung von einer Nachricht aus funktioniert, fügen Sie den `context` Parameter dem Objekt Ihrer Messaging-Erweiterung im `commands` App-Manifest hinzu, wie im folgenden Beispiel gezeigt. Gültige Zeichenfolgen für das `context` Array sind , und `"message"` `"commandBox"` `"compose"` . Der Standardwert ist `["compose", "commandBox"]`. Ausführliche Informationen zum Parameter finden Sie im Abschnitt zum Definieren von [Befehlen:](#define-commands) `context`

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

Unten sehen Sie ein Beispiel für das `value` Objekt, das die Nachrichtendetails enthält, die als Teil der `composeExtension` Anforderung gesendet werden, die an Ihren Bot gesendet werden.

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

### <a name="test-via-uploading"></a>Testen per Upload

Sie können Ihre Messaging-Erweiterung testen, indem Sie Ihre App hochladen. Weitere Informationen finden Sie unter [Hochladen Ihrer App in einem Team.](~/concepts/deploy-and-publish/apps-upload.md)

Um Ihre Messaging-Erweiterung zu öffnen, navigieren Sie zu einem Ihrer Chats oder Kanäle. Wählen Sie die Schaltfläche **"Weitere Optionen"** **(&#8943;)** im Feld "Verfassen" aus, und wählen Sie Ihre Messaging-Erweiterung aus.

## <a name="collecting-input-from-users"></a>Sammeln von Eingaben von Benutzern

Es gibt drei Möglichkeiten, Informationen von einem Endbenutzer in Teams zu sammeln.

### <a name="static-parameter-list"></a>Liste statischer Parameter

Bei dieser Methode müssen Sie lediglich eine statische Liste von Parametern im Manifest definieren, wie oben im Befehl "Erstellen To Do" dargestellt. Um diese Methode zu verwenden, stellen Sie sicher, dass sie `fetchTask` festgelegt ist und Dass Sie Die Parameter im Manifest `false` definieren.

Wenn ein Benutzer einen Befehl mit statischen Parametern auswählt, generiert Teams ein Formular in einem Aufgabenmodul mit den definierten Parametern im Manifest. Wenn Sie auf "Absenden" klicken, wird eine `composeExtension/submitAction` an den Bot gesendet. Weitere Informationen zu dem erwarteten Satz von Antworten finden Sie unter [Antworten zur Übermittlung.](#responding-to-submit)

### <a name="dynamic-input-using-an-adaptive-card"></a>Dynamische Eingabe mithilfe einer adaptiven Karte

Bei dieser Methode kann Ihr Dienst eine benutzerdefinierte adaptive Karte definieren, um die Benutzereingaben zu erfassen. Legen Sie für diesen Ansatz den `fetchTask` Parameter `true` im Manifest fest. Wenn Sie festlegen, `fetchTask` `true` werden statische Parameter, die für den Befehl definiert sind, ignoriert.

Bei dieser Methode empfängt Ihr Dienst ein `composeExtension/fetchTask` Ereignis und antwortet mit einer Antwort des adaptiven kartenbasierten [Aufgabenmoduls.](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object) Es folgt eine Beispielantwort mit einer adaptiven Karte:

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

Der Bot kann auch mit einer Authentifizierungs-/Konfigurationsantwort antworten, wenn der Benutzer die Erweiterung authentifizieren oder konfigurieren muss, bevor er die Benutzereingabe erhält.

### <a name="dynamic-input-using-a-web-view"></a>Dynamische Eingabe mithilfe einer Webansicht

Bei dieser Methode kann Ihr Dienst ein basiertes Widget anzeigen, `<iframe>` um eine benutzerdefinierte Benutzeroberfläche anzuzeigen und Benutzereingaben zu sammeln. Legen Sie für diesen Ansatz den `fetchTask` Parameter `true` im Manifest fest.

Genau wie im adaptiven Kartenfluss sendet Ihr Dienst ein `fetchTask` Ereignis und antwortet mit einer URL-basierten [Aufgabenmodulantwort.](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object) Es folgt eine Beispielantwort mit einer adaptiven Karte:

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

### <a name="request-to-install-your-conversational-bot"></a>Anfordern der Installation Ihres Unterhaltungs-Bots

Wenn Ihre App einen Unterhaltungsbot enthält, stellen Sie sicher, dass er in der Unterhaltung installiert ist, bevor Sie das Aufgabenmodul laden. Dies kann in Situationen hilfreich sein, in denen Sie zusätzlichen Kontext für Ihr Aufgabenmodul abrufen müssen. Beispielsweise müssen Sie möglicherweise die Liste abrufen, um ein Personenauswahl-Steuerelement oder die Liste der Kanäle in einem Team aufzufüllen.

Um diesen Fluss zu vereinfachen, wenn Ihre Messaging-Erweiterung zum ersten Mal die `composeExtension/fetchTask` Aufrufüberprüfung empfängt, um festzustellen, ob Ihr Bot im aktuellen Kontext installiert ist. Sie können dies erreichen, indem Sie versuchen, einen Listenanruf zu erhalten. Wenn Ihr Bot beispielsweise nicht installiert ist, geben Sie eine adaptive Karte mit einer Aktion zurück, die den Benutzer zur Installation des Bots anfordert. Der Benutzer muss über die Berechtigung zum Installieren von Apps an diesem Speicherort verfügen. Wenn sie nicht installiert werden können, wird die Nachricht aufgefordert, sich an den Administrator zu wenden.

Hier ist ein Beispiel für die Antwort:

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

Sobald der Benutzer die Installation abgeschlossen hat, erhält Ihr Bot eine weitere Aufrufnachricht mit `name = composeExtension/submitAction` , und `value.data.msteams.justInTimeInstall = true` .

Hier ist ein Beispiel für den Aufruf:

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

Antworten Sie auf den Aufruf mit der gleichen Aufgabenantwort, mit der Sie geantwortet hätten, wenn der Bot bereits installiert wäre.

## <a name="responding-to-submit"></a>Antworten auf Übermittlung

Sobald ein Benutzer die Eingabe abgeschlossen hat, empfängt der Bot ein `composeExtension/submitAction` Ereignis mit der Befehls-ID und den festgelegten Parameterwerten.

Dies sind die unterschiedlichen erwarteten Antworten auf ein `submitAction` .

### <a name="task-module-response"></a>Antwort des Aufgabenmoduls

Dies wird verwendet, wenn Ihre Erweiterung Dialogfelder miteinander verketten muss, um weitere Informationen zu erhalten. Die Antwort ist genau die gleiche wie `fetchTask` zuvor erwähnt.

### <a name="compose-extension-authconfig-response"></a>Verfassen-Erweiterungs-Authentifizierungs-/Konfigurationsantwort

Dies wird verwendet, wenn ihre Erweiterung entweder authentifiziert oder konfiguriert werden muss, um fortzufahren. Weitere Informationen finden Sie im [Abschnitt "Authentifizierung"](~/resources/messaging-extension-v3/search-extensions.md#authentication) im Suchabschnitt.

### <a name="compose-extension-result-response"></a>Ergebnisantwort der Erstellerweiterung

Dies wird verwendet, um eine Karte als Ergebnis des Befehls in das Feld zum Verfassen einzufügen. Es ist die gleiche Antwort, die im Suchbefehl verwendet wird, aber sie ist auf eine Karte oder ein Ergebnis im Array beschränkt.

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

### <a name="respond-with-an-adaptive-card-message-sent-from-a-bot"></a>Antworten mit einer von einem Bot gesendeten adaptiven Kartennachricht

Reagieren Sie auf die Sendeaktion, indem Sie eine Nachricht mit einer adaptiven Karte mit einem Bot in den Kanal einfügen. Ihr Benutzer kann eine Vorschau der Nachricht anzeigen, bevor er sie übermittelt, und möglicherweise auch bearbeiten/mit ihr interagieren. Dies kann in Szenarien nützlich sein, in denen Sie Informationen von Ihren Benutzern sammeln müssen, bevor Sie eine adaptive Kartenantwort erstellen. Das folgende Szenario zeigt, wie Sie diesen Fluss verwenden können, um eine Abfrage zu konfigurieren, ohne die Konfigurationsschritte in die Kanalnachricht einzuschließen.

1. Der Benutzer wählt die Messaging-Erweiterung aus, um das Aufgabenmodul auszulösen.
1. Der Benutzer verwendet das Aufgabenmodul, um die Abfrage zu konfigurieren.
1. Nach dem Übermitteln des Konfigurationsaufgabenmoduls verwendet die App die im Aufgabenmodul bereitgestellten Informationen, um eine adaptive Karte zu erstellen, und sendet sie als `botMessagePreview` Antwort an den Client.
1. Der Benutzer kann dann eine Vorschau der adaptiven Kartennachricht anzeigen, bevor der Bot sie in den Kanal einfügt. Wenn der Bot noch kein Mitglied des Kanals ist, wird durch Klicken auf `Send` den Bot der Bot hinzugefügt.
1. Durch die Interaktion mit der adaptiven Karte wird die Nachricht vor dem Senden geändert.
1. Sobald der Benutzer den Bot auswählt, `Send` wird die Nachricht an den Kanal gesendet.

Um diesen Fluss zu aktivieren, sollte Ihr Aufgabenmodul wie im folgenden Beispiel antworten, in dem dem Benutzer die Vorschaunachricht angezeigt wird.

>[!Note]
>Die `activityPreview` muss eine Aktivität mit genau `message` 1 adaptiver Kartenanlage enthalten.

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

Ihre Nachrichtenerweiterung muss jetzt auf zwei neue Arten von Interaktionen reagieren, `value.botMessagePreviewAction = "send"` und `value.botMessagePreviewAction = "edit"` . Unten sehen Sie ein Beispiel für das `value` Objekt, das Sie verarbeiten müssen:

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

Wenn Sie auf die `edit` Anforderung antworten, sollten Sie mit einer Antwort mit den Werten antworten, `task` die mit den Informationen gefüllt sind, die der Benutzer bereits übermittelt hat. Wenn Sie auf die `send` Anforderung antworten, sollten Sie eine Nachricht an den Kanal senden, der die fertige adaptive Karte enthält.

# <a name="typescriptnodejs"></a>[TypeScript/Node.js](#tab/typescript)

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

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

In diesem Beispiel wird dieser Ablauf mithilfe des [Microsoft.Bot.Connector.Teams SDK (v3)](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams)veranschaulicht.

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

## <a name="see-also"></a>Siehe auch

[Bot Framework-Beispiele](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)
