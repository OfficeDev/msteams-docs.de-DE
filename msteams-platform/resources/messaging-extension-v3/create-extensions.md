---
title: Initiieren von Aktionen mit Messaging Erweiterungen
description: Erstellen Aktions basierter Messaging Erweiterungen, um Benutzern das Auslösen externer Dienste zu ermöglichen
keywords: Microsoft Teams Messaging Extensions Messaging Extensions Search
ms.openlocfilehash: dd88360e342788fc0505809c6c8281c64fb7afbb
ms.sourcegitcommit: 0aeb60027f423d8ceff3b377db8c3efbb6da4d17
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2020
ms.locfileid: "48997993"
---
# <a name="initiate-actions-with-messaging-extensions"></a>Initiieren von Aktionen mit Messaging Erweiterungen

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-me.md)]

Aktionsbasierte Messaging Erweiterungen ermöglichen es Ihren Benutzern, Aktionen in externen Diensten innerhalb von Teams auszulösen.

![Beispiel für eine Messaging Erweiterungskarte](~/assets/images/compose-extensions/ceexample.png)

In den folgenden Abschnitten wird die Vorgehensweise beschrieben.

[!include[Common content for creating extensions](~/includes/messaging-extensions/messaging-extensions-common.md)]

### <a name="action-type-message-extensions"></a>Nachrichten Erweiterungen für Aktionstypen

Um Aktionen aus einer Messaging Erweiterung zu initiieren `type` , legen Sie den Parameter auf fest `action` . Unten sehen Sie ein Beispiel für ein Manifest mit einer Suche und einem Create-Befehl. Eine einzelne Messaging Erweiterung kann bis zu zehn verschiedene Befehle haben. Dies kann sowohl mehrere Suchfunktionen als auch mehrere Aktionsbasierte Befehle umfassen.

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

Zusätzlich zum Initiieren von Aktionen aus dem Bereich zum Verfassen von Nachrichten können Sie auch Ihre Messaging Erweiterung verwenden, um eine Aktion aus einer Nachricht zu initiieren. Auf diese Weise können Sie den Inhalt der Nachricht an Ihren bot zur Verarbeitung senden und auf diese Nachricht optional mit einer Antwort Antworten, die unter [Antworten auf Senden](#responding-to-submit)beschrieben wird. Die Antwort wird als Antwort auf die Nachricht eingefügt, die Ihre Benutzer vor dem Senden bearbeiten können. Ihre Benutzer können über das Menü Überlauf auf Ihre Messaging Erweiterung zugreifen `...` und dann `Take action` wie in der Abbildung unten auswählen.

![Beispiel für das Initiieren einer Aktion aus einer Nachricht](~/assets/images/compose-extensions/messageextensions_messageaction.png)

Damit Ihre Messaging Erweiterung mit einer Nachricht funktioniert, müssen Sie den `context` Parameter dem Objekt Ihrer Messaging Erweiterung im App-Manifest hinzufügen, `commands` wie im folgenden Beispiel dargestellt. Gültige Zeichenfolgen für das `context` Array sind `"message"` , `"commandBox"` und `"compose"` . Der Standardwert ist `["compose", "commandBox"]`. Ausführliche Informationen zum Parameter finden Sie im Abschnitt [define Commands](#define-commands) `context` .

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

Unten sehen Sie ein Beispiel für das Objekt, das `value` die Nachrichtendetails enthält, die gesendet werden, wenn ein Teil der `composeExtension` Anforderung an Ihren bot gesendet wird.

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

### <a name="test-via-uploading"></a>Testen über hochladen

Sie können Ihre Messaging Erweiterung testen, indem Sie Ihre APP hochladen. Weitere Informationen finden Sie unter [Hochladen Ihrer APP in einem Team](~/concepts/deploy-and-publish/apps-upload.md) .

Um Ihre Messaging Erweiterung zu öffnen, navigieren Sie zu einem beliebigen Chat oder Kanal. Wählen Sie im Feld Verfassen die Schaltfläche **Weitere Optionen** ( **&#8943;** ) aus, und wählen Sie Ihre Messaging Erweiterung aus.

## <a name="collecting-input-from-users"></a>Sammeln von Eingaben von Benutzern

Es gibt drei Möglichkeiten zum Erfassen von Informationen von einem Endbenutzer in Microsoft Teams.

### <a name="static-parameter-list"></a>Liste der statischen Parameter

In dieser Methode müssen Sie lediglich eine statische Liste von Parametern im Manifest definieren, wie oben im Befehl "Create to do" dargestellt. Um diese Methode zu verwenden, ist sichergestellt, `fetchTask` `false` dass Sie die Parameter im Manifest definieren und festlegen.

Wenn ein Benutzer einen Befehl mit statischen Parametern auswählt, generiert Microsoft Teams ein Formular in einem Aufgabenmodul, wobei die im Manifest definierten Parameter verwendet werden. Beim Drücken von Submit `composeExtension/submitAction` wird a an den bot gesendet. Weitere Informationen zu den erwarteten Antworten finden Sie im Thema [Antworten auf Submit](#responding-to-submit) .

### <a name="dynamic-input-using-an-adaptive-card"></a>Dynamische Eingabe mithilfe einer adaptiven Karte

Bei dieser Methode kann Ihr Dienst eine benutzerdefinierte Adaptive Karte definieren, um die Benutzereingabe zu erfassen. Legen Sie für diesen Ansatz den `fetchTask` Parameter auf `true` im Manifest fest. Beachten Sie, dass bei Festlegung `fetchTask` auf `true` statische Parameter, die für den Befehl definiert sind, ignoriert werden.

In dieser Methode erhält Ihr Dienst ein `composeExtension/fetchTask` Ereignis und muss mit einer adaptiven kartenbasierten Antwort auf [Aufgabenmodul](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object)Antworten. Unten sehen Sie eine Beispielantwort mit einer adaptiven Karte:

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

Der Bot kann auch mit einer auth/config-Antwort Antworten, wenn der Benutzer die Erweiterung authentifizieren oder konfigurieren muss, bevor er die Benutzereingabe erhält.

### <a name="dynamic-input-using-a-web-view"></a>Dynamische Eingabe mithilfe einer Webansicht

In dieser Methode kann Ihr Dienst ein `<iframe>` basiertes Widget anzeigen, um eine benutzerdefinierte Benutzeroberfläche anzuzeigen und Benutzereingaben zu erfassen. Legen Sie für diesen Ansatz den `fetchTask` Parameter auf `true` im Manifest fest.

Genau wie beim adaptiven Karten Fluss wird Ihr Dienst ein Ereignis senden `fetchTask` und muss mit einer URL-basierten [Aufgabenmodul Antwort](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object)Antworten. Unten sehen Sie eine Beispielantwort mit einer adaptiven Karte:

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

### <a name="request-to-install-your-conversational-bot"></a>Anforderung zum Installieren Ihres Unterhaltungs-bot

Wenn Ihre APP auch einen Unterhaltungs-bot enthält, müssen Sie möglicherweise sicherstellen, dass Ihr bot in der Unterhaltung installiert ist, bevor Sie den Aufgabenmodul laden. Dies kann in Situationen hilfreich sein, in denen Sie zusätzlichen Kontext für Ihr Aufgabenmodul erhalten müssen. Beispielsweise müssen Sie möglicherweise das Dienstplan Verzeichnis abrufen, um ein Personenauswahl-Steuerelement oder die Liste der Kanäle in einem Team aufzufüllen.

Um diesen Fluss zu erleichtern, wenn Ihre Messaging-Erweiterung zuerst die `composeExtension/fetchTask` Invoke-Überprüfung erhält, um festzustellen, ob Ihr bot im aktuellen Kontext installiert ist (Sie können dies beispielsweisedurch den Aufruf des Get-Dienstplan Aufrufs erreichen). Wenn Ihr bot nicht installiert ist, geben Sie eine Adaptive Karte mit einer Aktion zurück, die den Benutzer anfordert, ihren bot zu installieren, siehe das Beispiel unten. Beachten Sie, dass dies erfordert, dass der Benutzer über die Berechtigung zum Installieren von apps an diesem Speicherort verfügt. Wenn dies nicht möglich ist, wird eine Meldung angezeigt, in der Sie aufgefordert werden, Ihren Administrator zu kontaktieren.

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

Sobald der Benutzer die Installation abgeschlossen hat, erhält der bot eine weitere Invoke-Nachricht mit `name = composeExtension/submitAction` und `value.data.msteams.justInTimeInstall = true` .

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

Sie sollten auf diesen Aufruf mit derselben Antwort Antworten, auf die Sie reagiert haben, wenn der bot bereits installiert wurde.

## <a name="responding-to-submit"></a>Reagieren auf Submit

Sobald ein Benutzer seine Eingabe abgeschlossen hat, erhält der bot ein `composeExtension/submitAction` Ereignis mit den festgelegten Befehls-IDs und Parameterwerten.

Dies sind die unterschiedlichen erwarteten Antworten auf a `submitAction` .

### <a name="task-module-response"></a>Antwort des Aufgabenmoduls

Dies wird verwendet, wenn Ihre Erweiterung Dialogfelder miteinander verketten muss, um weitere Informationen zu erhalten. Die Antwort ist genau die gleiche wie `fetchTask` zuvor erwähnt.

### <a name="compose-extension-authconfig-response"></a>Antwort zum Verfassen der Durchwahl Authentifizierung/-Konfiguration

Dies wird verwendet, wenn Ihre Erweiterung entweder authentifiziert oder konfiguriert werden muss, um den Vorgang fortzusetzen. Weitere Informationen finden Sie im [Abschnitt "Authentifizierung"](~/resources/messaging-extension-v3/search-extensions.md#authentication) im Abschnitt "Suche".

### <a name="compose-extension-result-response"></a>Antwort zum Verfassen der Ergebnis Erweiterung

Dadurch wird eine Karte als Ergebnis eines Befehls in das Feld Verfassen eingefügt. Es ist die gleiche Antwort, die im Suchbefehl verwendet wird, aber Sie ist auf eine Karte oder ein Ergebnis im Array limitiert.

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

### <a name="respond-with-an-adaptive-card-message-sent-from-a-bot"></a>Antworten mit einer adaptiven Karten Nachricht, die von einem bot gesendet wurde

Sie können auch auf die Submit-Aktion reagieren, indem Sie eine Nachricht mit einer adaptiven Karte in den Kanal mit einem bot einfügen. Der Benutzer kann die Nachricht in einer Vorschau anzeigen, bevor er ihn sendet, und möglicherweise auch mit ihm bearbeiten/interagieren. Dies kann in Szenarien hilfreich sein, in denen Sie Informationen von Ihren Benutzern sammeln müssen, bevor Sie eine Adaptive Karten Antwort erstellen. Das folgende Szenario zeigt, wie Sie diesen Fluss zum Konfigurieren einer Umfrage verwenden können, ohne die Konfigurationsschritte in die Kanal Nachricht einzuschließen.

1. Der Benutzer klickt auf die Messaging Erweiterung, um den Aufgabenmodul auszulösen.
1. Der Benutzer verwendet den Aufgabenmodul zum Konfigurieren der Umfrage.
1. Nach dem Senden des Konfigurationsaufgaben Moduls verwendet die APP die im Aufgabenmodul bereitgestellten Informationen, um eine Adaptive Karte zu basteln und Sie als `botMessagePreview` Antwort an den Client zu senden.
1. Der Benutzer kann dann eine Vorschau der adaptiven Karten Nachricht anzeigen, bevor der bot ihn in den Kanal einfügt. Wenn der bot noch kein Mitglied des Kanals ist, `Send` wird der bot durch Klicken hinzugefügt.
1. Bei der Interaktion mit der adaptiven Karte wird die Nachricht vor dem Senden geändert.
1. Nachdem der Benutzer `Send` auf den bot geklickt hat, wird die Nachricht an den Kanal gesendet.

Zum Aktivieren dieses Flusses sollte Ihr Aufgabenmodul wie im folgenden Beispiel reagieren, das die Vorschau Nachricht an den Benutzer weiter gibt.

>[!Note]
>Das `activityPreview` muss eine `message` Aktivität mit genau 1 adaptiver Karten Anlage enthalten.

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

Ihre Nachrichten Erweiterung muss nun auf zwei neue Arten von Interaktionen reagieren `value.botMessagePreviewAction = "send"` und `value.botMessagePreviewAction = "edit"` . Nachfolgend finden Sie ein Beispiel für das `value` Objekt, das Sie verarbeiten müssen:

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

Bei der Antwort auf die `edit` Anforderung sollten Sie mit einer `task` Antwort mit den Werten Antworten, die mit den Informationen aufgefüllt sind, die der Benutzer bereits übermittelt hat. Wenn Sie auf die `send` Anforderung reagieren, sollten Sie eine Nachricht an den Kanal senden, der die fertige Adaptive Karte enthält.

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

*Siehe auch* [bot Framework-Beispiele](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

In diesem Beispiel wird dieser Ablauf mithilfe des [Microsoft. bot. Connector. Teams SDK (v3)](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams)veranschaulicht.

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
