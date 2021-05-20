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
# <a name="initiate-actions-with-messaging-extensions"></a>Initiieren von Aktionen mit Messagingerweiterungen

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-me.md)]

Aktionsbasierte Messagingerweiterungen ermöglichen es Benutzern, Aktionen in externen Diensten auszulösen, während sie sich innerhalb Teams.

![Beispiel für Messaging-Erweiterungskarte](~/assets/images/compose-extensions/ceexample.png)

In den folgenden Abschnitten wird beschrieben, wie Sie dies tun.

[!include[Common content for creating extensions](~/includes/messaging-extensions/messaging-extensions-common.md)]

### <a name="action-type-message-extensions"></a>Aktionstyp-Nachrichtenerweiterungen

Um Aktionen aus einer Messagingerweiterung zu initiieren, legen Sie den `type` Parameter auf `action` . Im Folgenden finden Sie ein Beispiel für ein Manifest mit einem Such- und einem Create-Befehl. Eine einzelne Messagingerweiterung kann bis zu 10 verschiedene Befehle haben. Dies kann sowohl mehrere Such- als auch mehrere aktionsbasierte Befehle umfassen.

#### <a name="complete-app-manifest-example"></a>Vollständiges App-Manifestbeispiel

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

Zusätzlich zum Initiieren von Aktionen aus dem Nachrichtenbereich zum Verfassen können Sie auch die Messagingerweiterung verwenden, um eine Aktion aus einer Nachricht zu initiieren. Auf diese Weise können Sie den Inhalt der Nachricht zur Verarbeitung an Ihren Bot senden und optional auf diese Nachricht mit einer Antwort mit der unter [Antworten auf Senden](#responding-to-submit)beschriebenen Methode antworten. Die Antwort wird als Antwort auf die Nachricht eingefügt, die Ihre Benutzer vor dem Absenden bearbeiten können. Ihre Benutzer können über das Überlaufmenü auf Ihre Messagingerweiterung zugreifen `...` und dann wie in der folgenden Abbildung `Take action` auswählen:

![Beispiel für das Anleiten einer Aktion aus einer Nachricht](~/assets/images/compose-extensions/messageextensions_messageaction.png)

Damit Ihre Messagingerweiterung von einer Nachricht aus funktioniert, müssen Sie den `context` Parameter dem Objekt Ihrer Messagingerweiterung in Ihrem App-Manifest hinzufügen, `commands` wie im folgenden Beispiel. Gültige Zeichenfolgen für das `context` Array sind , und `"message"` `"commandBox"` `"compose"` . Der Standardwert ist `["compose", "commandBox"]`. Ausführliche Informationen zum Parameter finden Sie im Abschnitt [Befehle](#define-commands) `context` definieren.

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

Im Folgenden finden Sie ein Beispiel für das `value` Objekt, das die Nachrichtendetails enthält, die als Teil der `composeExtension` Anforderung an Ihren Bot gesendet werden.

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

### <a name="test-via-uploading"></a>Test über Upload

Sie können Ihre Messaging-Erweiterung testen, indem Sie Ihre App hochladen. Weitere Informationen finden Sie unter [Hochladen Ihrer App in einem Team](~/concepts/deploy-and-publish/apps-upload.md).

Um Ihre Messaging-Erweiterung zu öffnen, navigieren Sie zu einem Ihrer Chats oder Kanäle. Wählen Sie im Feld Verfassen die Schaltfläche **Weitere Optionen** (**&#8943;**) aus, und wählen Sie Ihre Messaging-Erweiterung aus.

## <a name="collecting-input-from-users"></a>Sammeln von Eingaben von Benutzern

Es gibt drei Möglichkeiten, Informationen von einem Endbenutzer in Teams zu sammeln.

### <a name="static-parameter-list"></a>Statische Parameterliste

Bei dieser Methode müssen Sie lediglich eine statische Liste von Parametern im Manifest definieren, wie oben im Befehl "erstellen To Do" gezeigt. Um diese Methode zu verwenden, stellen `fetchTask` Sie sicher, dass auf festgelegt ist `false` und dass Sie Ihre Parameter im Manifest definieren.

Wenn ein Benutzer einen Befehl mit statischen Parametern auswählt, generiert Teams ein Formular in einem Taskmodul mit den im Manifest definierten Parametern. Beim Schlagen wird Ein `composeExtension/submitAction` sende per Bot gesendet. Weitere Informationen zu den erwarteten Antworten finden Sie unter [Antworten zum Senden](#responding-to-submit).

### <a name="dynamic-input-using-an-adaptive-card"></a>Dynamischer Eingang mit einer adaptiven Karte

Bei dieser Methode kann Ihr Dienst eine benutzerdefinierte adaptive Karte definieren, um die Endbenutzereingabe zu erfassen. Legen Sie für diesen Ansatz den `fetchTask` Parameter `true` im Manifest fest. Beachten Sie, dass, wenn Sie auf statische Parameter festlegen, `fetchTask` die für den Befehl definiert `true` sind, ignoriert werden.

Bei dieser Methode erhält Ihr Dienst ein `composeExtension/fetchTask` Ereignis und muss mit einer adaptiven kartenbasierten [Aufgabenmodulantwort](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object)antworten. Im Folgenden finden Sie eine Beispielantwort mit einer adaptiven Karte:

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

Der Bot kann auch mit einer auth/config-Antwort antworten, wenn der Benutzer die Erweiterung authentifizieren oder konfigurieren muss, bevor er die Benutzereingabe erhält.

### <a name="dynamic-input-using-a-web-view"></a>Dynamische Eingabe über eine Webansicht

Bei dieser Methode kann Ihr Dienst ein basiertes Widget anzeigen, `<iframe>` um jede benutzerdefinierte Benutzeroberfläche anzuzeigen und Benutzereingaben zu sammeln. Legen Sie für diesen Ansatz den `fetchTask` Parameter `true` im Manifest fest.

Genau wie im adaptiven Kartenfluss wird Ihr Dienst ein Ereignis senden `fetchTask` und muss mit einer URL-basierten [Taskmodulantwort](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object)antworten. Im Folgenden finden Sie eine Beispielantwort mit einer adaptiven Karte:

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

### <a name="request-to-install-your-conversational-bot"></a>Anfrage zur Installation Ihres Konversationsbots

Wenn Ihre App auch einen Konversationsbot enthält, kann es erforderlich sein, sicherzustellen, dass Ihr Bot in der Unterhaltung installiert ist, bevor Sie Ihr Aufgabenmodul laden. Dies kann in Situationen nützlich sein, in denen Sie zusätzlichen Kontext für Ihr Aufgabenmodul abrufen müssen. Sie müssen z. B. den Dienstplan abrufen, um ein Personenauswahlsteuerelement oder die Liste der Kanäle in einem Team aufzufüllen.

Um diesen Fluss zu erleichtern, wenn Ihre Messagingerweiterung zum ersten Mal die `composeExtension/fetchTask` Aufrufprüfung empfängt, um zu sehen, ob Ihr Bot im aktuellen Kontext installiert ist. Sie können dies erreichen, indem Sie den Abrufen von Dienstplanaufrufen versuchen, z. B. Wenn Ihr Bot nicht installiert ist, geben Sie eine Adaptive Karte mit einer Aktion zurück, die den Benutzer auffordert, Ihren Bot zu installieren. Siehe das Beispiel unten. Beachten Sie, dass der Benutzer über die Berechtigung zum Installieren von Apps an diesem Speicherort verfügt. Wenn sie dies nicht können, wird ihnen eine Meldung angezeigt, in der sie aufgefordert werden, sich an ihren Administrator zu wenden.

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

Sobald der Benutzer die Installation abgeschlossen hat, erhält Ihr Bot eine weitere Aufrufnachricht mit `name = composeExtension/submitAction` . und `value.data.msteams.justInTimeInstall = true` .

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

Sie sollten auf diesen Aufruf mit derselben Taskantwort antworten, mit der Sie geantwortet hätten, wenn der Bot bereits installiert war.

## <a name="responding-to-submit"></a>Reagieren auf Dieübermittlung

Sobald ein Benutzer die Eingabe seiner Eingabe abgeschlossen hat, erhält Ihr Bot ein `composeExtension/submitAction` Ereignis mit der Befehls-ID und den Parameterwerten.

Dies sind die unterschiedlichen erwarteten Antworten auf eine `submitAction` .

### <a name="task-module-response"></a>Task-Modul-Antwort

Dies wird verwendet, wenn Ihre Erweiterung Dialoge miteinander verketten muss, um weitere Informationen zu erhalten. Die Antwort ist genau die gleiche wie `fetchTask` zuvor erwähnt.

### <a name="compose-extension-authconfig-response"></a>Komponieren der Erweiterung auth/config-Antwort

Dies wird verwendet, wenn ihre Erweiterung sich authentifizieren oder konfigurieren muss, um fortzufahren. Weitere Informationen finden Sie im [Abschnitt Authentifizierung](~/resources/messaging-extension-v3/search-extensions.md#authentication) im Suchabschnitt.

### <a name="compose-extension-result-response"></a>Komponieren der Antwort auf die Erweiterungsergebnisantwort

Dadurch wurde eine Karte als Ergebnis eines Befehls in das Verfassenfeld eingefügt. Es ist die gleiche Antwort, die im Suchbefehl verwendet wird, aber es ist auf eine Karte oder ein Ergebnis im Array beschränkt.

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

### <a name="respond-with-an-adaptive-card-message-sent-from-a-bot"></a>Reagieren mit einer adaptiven Kartennachricht, die von einem Bot gesendet wurde

Sie können auch auf die Sendeaktion reagieren, indem Sie eine Nachricht mit einer Adaptive Card mit einem Bot in den Kanal einfügen. Der Benutzer kann die Nachricht vor dem Absenden in der Vorschau anzeigen und möglicherweise auch bearbeiten/interagieren. Dies kann in Szenarien sehr nützlich sein, in denen Sie Informationen von Benutzern sammeln müssen, bevor Sie eine adaptive Kartenantwort erstellen. Das folgende Szenario zeigt, wie Sie diesen Flow verwenden können, um eine Umfrage zu konfigurieren, ohne die Konfigurationsschritte in die Kanalnachricht einzuschließen.

1. Der Benutzer klickt auf die Messagingerweiterung, um das Taskmodul auszulösen.
1. Der Benutzer verwendet das Taskmodul, um die Abfrage zu konfigurieren.
1. Nach dem Absenden des Konfigurationsaufgabenmoduls verwendet die App die im Aufgabenmodul bereitgestellten Informationen, um eine adaptive Karte zu erstellen, und sendet sie als `botMessagePreview` Antwort an den Client.
1. Der Benutzer kann dann eine Vorschau der adaptiven Kartennachricht anzeigen, bevor der Bot sie in den Kanal einfügt. Wenn der Bot noch kein Mitglied des Kanals ist, wird der Bot durch Klicken `Send` hinzugefügt.
1. Durch die Interaktion mit der adaptiven Karte wird die Nachricht vor dem Senden geändert.
1. Sobald der Benutzer `Send` klickt, wird der Bot die Nachricht an den Kanal senden.

Um diesen Flow zu aktivieren, sollte Ihr Aufgabenmodul wie im folgenden Beispiel antworten, in dem dem Benutzer die Vorschaunachricht angezeigt wird.

>[!Note]
>Der `activityPreview` muss eine Aktivität mit genau 1 `message` adaptivem Kartenanhang enthalten.

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

Ihre Nachrichtenerweiterung muss nun auf zwei neue Arten von Interaktionen reagieren, `value.botMessagePreviewAction = "send"` und `value.botMessagePreviewAction = "edit"` . Im Folgenden finden Sie ein Beispiel für das `value` Objekt, das Sie verarbeiten müssen:

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

Wenn Sie auf die Anforderung antworten, `edit` sollten Sie mit einer Antwort mit den Werten antworten, die mit den Informationen aufgefüllt sind, die der Benutzer bereits übermittelt `task` hat. Wenn Sie auf die Anforderung antworten, `send` sollten Sie eine Nachricht an den Kanal senden, der die abgeschlossene adaptive Karte enthält.

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

Dieses Beispiel zeigt diesen Flow mit dem [Microsoft.Bot.Connector.Teams SDK (v3)](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams).

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