---
title: Initiieren von Aktionen mit Messagingerweiterungen
description: Erstellen von aktionsbasierten Messagingerweiterungen, damit Benutzer externe Dienste auslösen können
ms.topic: how-to
keywords: Suche nach Messagingerweiterungen für Teams-Messagingerweiterungen
ms.openlocfilehash: c95139cea22569901e04effb0b1283c6979454b9
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696094"
---
# <a name="initiate-actions-with-messaging-extensions"></a>Initiieren von Aktionen mit Messagingerweiterungen

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-me.md)]

Aktionsbasierte Messagingerweiterungen ermöglichen Es Benutzern, Aktionen in externen Diensten innerhalb von Teams auszulösen.

![Beispiel für Eine Messaging-Erweiterungskarte](~/assets/images/compose-extensions/ceexample.png)

In den folgenden Abschnitten wird dies beschrieben.

[!include[Common content for creating extensions](~/includes/messaging-extensions/messaging-extensions-common.md)]

### <a name="action-type-message-extensions"></a>Nachrichtenerweiterungen des Aktionstyps

Legen Sie zum Initiieren von Aktionen aus einer Messagingerweiterung den `type` Parameter auf . `action` Im Folgenden finden Sie ein Beispiel für ein Manifest mit einem Such- und einem Create-Befehl. Eine einzelne Messagingerweiterung kann über bis zu 10 verschiedene Befehle verfügen. Dies kann sowohl mehrere Suchbefehle als auch mehrere aktionsbasierte Befehle umfassen.

#### <a name="complete-app-manifest-example"></a>Vollständiges Beispiel für das App-Manifest

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

Zusätzlich zum Initiieren von Aktionen aus dem Bereich zum Verfassen von Nachrichten können Sie auch Ihre Messagingerweiterung verwenden, um eine Aktion aus einer Nachricht zu initiieren. Auf diese Weise können Sie den Inhalt der Nachricht zur Verarbeitung an Ihren Bot senden und optional auf diese Nachricht mit einer Antwort antworten, indem Sie die unter Antworten auf Absenden beschriebene Methode [verwenden.](#responding-to-submit) Die Antwort wird als Antwort auf die Nachricht eingefügt, die Ihre Benutzer vor der Übermittlung bearbeiten können. Ihre Benutzer können über das Überlaufmenü auf Ihre Messagingerweiterung zugreifen und dann `...` wie im folgenden Bild `Take action` auswählen.

![Beispiel für das Initiieren einer Aktion aus einer Nachricht](~/assets/images/compose-extensions/messageextensions_messageaction.png)

Damit Ihre Messagingerweiterung von einer Nachricht aus funktioniert, müssen Sie den Parameter dem Objekt Ihrer Messagingerweiterung in Ihrem App-Manifest wie im folgenden `context` `commands` Beispiel hinzufügen. Gültige Zeichenfolgen für `context` das Array sind , und `"message"` `"commandBox"` `"compose"` . Der Standardwert ist `["compose", "commandBox"]`. Vollständige Details [zum](#define-commands) Parameter finden Sie im Abschnitt Befehle `context` definieren.

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

Nachfolgend sehen Sie ein Beispiel für das Objekt, das die Nachrichtendetails enthält, die als Teil der Anforderung an Ihren `value` `composeExtension` Bot gesendet werden.

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

### <a name="test-via-uploading"></a>Testen über Hochladen

Sie können Ihre Messagingerweiterung testen, indem Sie Ihre App hochladen. Weitere Informationen finden Sie unter [Hochladen Ihrer App in](~/concepts/deploy-and-publish/apps-upload.md) einem Team.

Um Ihre Messagingerweiterung zu öffnen, navigieren Sie zu ihren Chats oder Kanälen. Wählen Sie **die** Schaltfläche Weitere Optionen (**&#8943;**) im Verfassenfeld aus, und wählen Sie Ihre Messagingerweiterung aus.

## <a name="collecting-input-from-users"></a>Sammeln von Eingaben von Benutzern

Es gibt drei Möglichkeiten, Informationen von einem Endbenutzer in Teams zu sammeln.

### <a name="static-parameter-list"></a>Statische Parameterliste

In dieser Methode müssen Sie nur eine statische Liste von Parametern im Manifest definieren, wie oben im Befehl "To Do erstellen" gezeigt. Um diese Methode zu verwenden, stellen Sie sicher, dass auf festgelegt ist und Dass `fetchTask` Sie Ihre Parameter im Manifest `false` definieren.

Wenn ein Benutzer einen Befehl mit statischen Parametern aus wählt, generiert Teams ein Formular in einem Aufgabenmodul mit den im Manifest definierten Parametern. Beim Drücken von Submit a `composeExtension/submitAction` wird an den Bot gesendet. Weitere Informationen zum erwarteten Satz von Antworten finden Sie im Thema [Antworten](#responding-to-submit) auf Absenden.

### <a name="dynamic-input-using-an-adaptive-card"></a>Dynamische Eingabe mithilfe einer adaptiven Karte

Bei dieser Methode kann Ihr Dienst eine benutzerdefinierte adaptive Karte definieren, um die Endbenutzereingaben zu erfassen. Legen Sie für diesen Ansatz den `fetchTask` Parameter im `true` Manifest auf. Beachten Sie, dass beim Festlegen auf statische Parameter, die für den Befehl `fetchTask` `true` definiert sind, ignoriert wird.

Bei dieser Methode erhält Ihr Dienst ein Ereignis und muss mit einer `composeExtension/fetchTask` adaptiven kartenbasierten [Aufgabenmodulantwort antworten.](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) Nachfolgend finden Sie eine Beispielantwort mit einer adaptiven Karte:

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

Der Bot kann auch mit einer Authentifizierungs-/Konfigurationsantwort antworten, wenn der Benutzer die Erweiterung authentifizieren oder konfigurieren muss, bevor er die Benutzereingabe erhalten kann.

### <a name="dynamic-input-using-a-web-view"></a>Dynamische Eingabe mithilfe einer Webansicht

In dieser Methode kann Ihr Dienst ein basiertes Widget anzeigen, um `<iframe>` benutzerdefinierte Benutzeroberflächen anzuzeigen und Benutzereingaben zu erfassen. Legen Sie für diesen Ansatz den `fetchTask` Parameter im `true` Manifest auf.

Wie beim adaptiven Kartenfluss wird Ihr Dienst ein Ereignis senden und muss mit einer URL-basierten `fetchTask` [Aufgabenmodulantwort antworten.](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) Nachfolgend finden Sie eine Beispielantwort mit einer adaptiven Karte:

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

### <a name="request-to-install-your-conversational-bot"></a>Anforderung zum Installieren des Unterhaltungsbots

Wenn Ihre App auch einen Unterhaltungsbot enthält, muss vor dem Laden des Aufgabenmoduls möglicherweise sichergestellt werden, dass Ihr Bot in der Unterhaltung installiert ist. Dies kann in Situationen hilfreich sein, in denen Sie zusätzlichen Kontext für Ihr Aufgabenmodul erhalten müssen. Sie müssen z. B. die Liste abrufen, um ein Personenauswahlsteuerelement oder die Liste der Kanäle in einem Team auffüllen zu können.

Um diesen Fluss zu erleichtern, wenn Ihre Messagingerweiterung zuerst die Aufrufüberprüfung empfängt, um zu überprüfen, ob Ihr Bot im aktuellen Kontext installiert ist (Sie könnten dies beispielsweise durch den Aufruf des Abrufplans `composeExtension/fetchTask` erreichen). Wenn Ihr Bot nicht installiert ist, geben Sie eine adaptive Karte mit einer Aktion zurück, die den Benutzer zur Installation des Bots anfordert Siehe das folgende Beispiel. Beachten Sie, dass der Benutzer über die Berechtigung zum Installieren von Apps an diesem Speicherort verfügen muss. Wenn dies nicht möglich ist, wird ihnen eine Meldung angezeigt, in der sie aufgefordert werden, sich an ihren Administrator zu wenden.

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

Sobald der Benutzer die Installation abgeschlossen hat, erhält ihr Bot eine weitere Aufrufnachricht mit `name = composeExtension/submitAction` , und `value.data.msteams.justInTimeInstall = true` .

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

Sie sollten auf diesen Aufruf mit derselben Aufgabenantwort reagieren, mit der Sie geantwortet hätten, wenn der Bot bereits installiert wurde.

## <a name="responding-to-submit"></a>Reagieren auf Absenden

Sobald ein Benutzer seine Eingabe abgeschlossen hat, erhält der Bot ein Ereignis mit der Befehls-ID `composeExtension/submitAction` und den festgelegten Parameterwerten.

Dies sind die unterschiedlichen erwarteten Antworten auf eine `submitAction` .

### <a name="task-module-response"></a>Antwort des Aufgabenmoduls

Dies wird verwendet, wenn Ihre Erweiterung Dialogfelder miteinander verketten muss, um weitere Informationen zu erhalten. Die Antwort ist genau die gleiche wie `fetchTask` zuvor erwähnt.

### <a name="compose-extension-authconfig-response"></a>Antwort der Verfassenerweiterung auth/config

Dies wird verwendet, wenn Ihre Erweiterung entweder authentifiziert oder konfiguriert werden muss, um fortzufahren. Weitere [Informationen finden Sie im](~/resources/messaging-extension-v3/search-extensions.md#authentication) Abschnitt Authentifizierung im Abschnitt Suche.

### <a name="compose-extension-result-response"></a>Antwort zum Verfassen des Erweiterungsergebniss

Dies wurde zum Einfügen einer Karte in das Verfassenfeld als Ergebnis eines Befehls verwendet. Es ist dieselbe Antwort, die im Suchbefehl verwendet wird, aber sie ist auf eine Karte oder ein Ergebnis im Array beschränkt.

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

### <a name="respond-with-an-adaptive-card-message-sent-from-a-bot"></a>Antworten mit einer adaptiven Kartennachricht, die von einem Bot gesendet wurde

Sie können auch auf die Submit-Aktion reagieren, indem Sie eine Nachricht mit einer adaptiven Karte mit einem Bot in den Kanal einfügen. Ihr Benutzer kann eine Vorschau der Nachricht anzeigen, bevor er sie übermittelt, und möglicherweise auch bearbeiten/interagieren. Dies kann in Szenarien sehr nützlich sein, in denen Sie Informationen von Ihren Benutzern sammeln müssen, bevor Sie eine adaptive Kartenantwort erstellen. Das folgende Szenario zeigt, wie Sie diesen Fluss verwenden können, um eine Abfrage zu konfigurieren, ohne die Konfigurationsschritte in die Kanalnachricht zu verwenden.

1. Der Benutzer klickt auf die Messagingerweiterung, um das Aufgabenmodul auszulösen.
1. Der Benutzer verwendet das Aufgabenmodul, um die Abfrage zu konfigurieren.
1. Nach dem Übermitteln des Konfigurationsaufgabesmoduls verwendet die App die im Aufgabenmodul bereitgestellten Informationen, um eine adaptive Karte zu erstellen und sie als Antwort an `botMessagePreview` den Client zu senden.
1. Der Benutzer kann dann eine Vorschau der adaptiven Kartennachricht anzeigen, bevor der Bot sie in den Kanal einfüge. Wenn der Bot nicht bereits Mitglied des Kanals ist, wird durch Klicken `Send` auf den Bot der Bot hinzugefügt.
1. Durch die Interaktion mit der adaptiven Karte wird die Nachricht vor dem Senden geändert.
1. Sobald der Benutzer auf `Send` den Bot klickt, wird die Nachricht an den Kanal gesendet.

Um diesen Fluss zu aktivieren, sollte Ihr Aufgabenmodul wie im folgenden Beispiel antworten, in dem dem Benutzer die Vorschaunachricht angezeigt wird.

>[!Note]
>Der `activityPreview` muss eine Aktivität mit genau `message` 1 adaptiver Kartenanlage enthalten.

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

Ihre Nachrichtenerweiterung muss nun auf zwei neue Arten von Interaktionen `value.botMessagePreviewAction = "send"` reagieren, und `value.botMessagePreviewAction = "edit"` . Im Folgenden finden Sie ein Beispiel für `value` das Objekt, das Sie verarbeiten müssen:

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

Wenn Sie auf die Anforderung antworten, sollten Sie mit einer Antwort mit den Werten antworten, die mit den Informationen gefüllt sind, die der Benutzer `edit` `task` bereits übermittelt hat. Wenn Sie auf die Anforderung antworten, sollten Sie eine Nachricht an den Kanal senden, `send` der die endgültige adaptive Karte enthält.

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

*Siehe auch* [Bot Framework-Beispiele](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

In diesem Beispiel wird dieser Fluss mithilfe des [Microsoft.Bot.Connector.Teams SDK (v3) veranschaulicht.](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams)

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
