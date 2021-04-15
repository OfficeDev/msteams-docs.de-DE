---
title: Verwenden von Aufgabenmodulen in Microsoft Teams-Bots
description: Verwenden von Aufgabenmodulen mit Microsoft Teams-Bots, einschließlich Bot Framework-Karten, adaptiven Karten und Tiefenlinks.
ms.topic: how-to
keywords: Aufgabenmodule Teams Bots
ms.openlocfilehash: d87b55bf202184f315abf69dfc34fc4db9125c4f
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696472"
---
# <a name="using-task-modules-from-microsoft-teams-bots"></a>Verwenden von Aufgabenmodulen aus Microsoft Teams-Bots

Aufgabenmodule können von Microsoft Teams-Bots mithilfe von Schaltflächen auf adaptiven Karten und Bot Framework-Karten (Hero, Thumbnail und Office 365 Connector) aufgerufen werden. Aufgabenmodule sind häufig eine bessere Benutzeroberfläche als mehrere Unterhaltungsschritte, bei denen Sie als Entwickler den Botstatus nachverfolgen und dem Benutzer das Unterbrechen/Abbrechen der Sequenz ermöglichen müssen.

Es gibt zwei Möglichkeiten zum Aufrufen von Aufgabenmodulen:

* **Eine neue Art von Aufrufnachricht `task/fetch` .** Mithilfe der Kartenaktion für Bot Framework-Karten oder der Kartenaktion für adaptive Karten mit wird das Aufgabenmodul (entweder eine URL oder eine adaptive Karte) dynamisch von Ihrem Bot `invoke` [](~/task-modules-and-cards/cards/cards-actions.md#invoke) `Action.Submit` [](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) `task/fetch` abgerufen.
* **UrLs für Tiefe Verknüpfungen.** Mithilfe der [Deep Link-Syntax](~/task-modules-and-cards/what-are-task-modules.md#task-module-deep-link-syntax)für Aufgabenmodule können Sie die Kartenaktion für Bot Framework-Karten oder die `openUrl` [](~/task-modules-and-cards/cards/cards-actions.md#openurl) `Action.OpenUrl` [Kartenaktion](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) für adaptive Karten verwenden. Bei URLs mit tiefen Verknüpfungen ist die URL des Aufgabenmoduls oder der Adaptive Kartentext offensichtlich im Voraus bekannt, um einen Servertrip relativ zu zu `task/fetch` vermeiden.

>[!IMPORTANT]
>Um eine sichere Kommunikation sicherzustellen, `url` müssen alle `fallbackUrl` das HTTPS-Verschlüsselungsprotokoll implementieren.

## <a name="invoking-a-task-module-via-taskfetch"></a>Aufrufen eines Aufgabenmoduls über Aufgabe/Abruf

Wenn das Objekt der Kartenaktion oder auf die richtige Weise initialisiert wird (unten ausführlicher erläutert), wenn ein Benutzer die Schaltfläche drückt, wird eine Nachricht an den Bot `value` `invoke` `Action.Submit` `invoke` gesendet. In der HTTP-Antwort auf die Nachricht ist ein TaskInfo-Objekt in ein Wrapperobjekt eingebettet, das von Teams zum Anzeigen `invoke` des Aufgabenmoduls [](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) verwendet wird.

![task/fetch request/response](~/assets/images/task-module/task-module-invoke-request-response.png)

Sehen wir uns die einzelnen Schritte genauer an:

1. In diesem Beispiel wird eine Bot Framework Hero-Karte mit einer Kartenaktion "Kaufen" `invoke` [gezeigt.](~/task-modules-and-cards/cards/cards-actions.md#invoke) Der Wert der Eigenschaft ist - der Rest des Objekts kann nach Bes `type` `task/fetch` `value` nnen sein.
2. Der Bot empfängt die `invoke` HTTP-POST-Nachricht.
3. Der Bot erstellt ein Antwortobjekt und gibt es im Textkörper der POST-Antwort mit einem HTTP 200-Antwortcode zurück. Das Schema für Antworten wird unten in der Diskussion über [Aufgabe/Absenden](#the-flexibility-of-tasksubmit)beschrieben. Es ist jedoch wichtig, dass der Textkörper der HTTP-Antwort ein [TaskInfo-Objekt](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) enthält, das in ein Wrapperobjekt eingebettet ist, z. B.:

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

    Das `task/fetch` Ereignis und seine Antwort für Bots ähneln konzeptionell der Funktion im Client `microsoftTeams.tasks.startTask()` SDK.
4. Microsoft Teams zeigt das Aufgabenmodul an.

## <a name="submitting-the-result-of-a-task-module"></a>Übermitteln des Ergebnisses eines Aufgabenmoduls

Wenn der Benutzer mit dem Aufgabenmodul fertig ist, ähnelt das Zurücksenden des [Ergebnisses](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-submitting-the-result-of-a-task-module)an den Bot der Art und Weise, wie es mit Registerkarten funktioniert, aber es gibt einige Unterschiede, daher wird es auch hier beschrieben.

* **HTML/JavaScript ( `TaskInfo.url` )**. Nachdem Sie überprüft haben, was der Benutzer eingegeben hat, rufen Sie die SDK-Funktion auf (nachfolgend als zu `microsoftTeams.tasks.submitTask()` `submitTask()` Lesbarkeitszwecken bezeichnet). Sie können ohne Parameter aufrufen, wenn Sie nur möchten, dass Teams das Aufgabenmodul schließt, aber meistens möchten Sie ein Objekt oder eine Zeichenfolge an `submitTask()` Ihre `submitHandler` übergeben. Übergeben Sie ihn einfach als ersten Parameter, `result` . Teams ruft auf : ist und ist das Objekt/die Zeichenfolge, `submitHandler` das Sie an übergeben `err` `null` `result` `submitTask()` haben. Wenn Sie einen Parameter aufrufen, müssen Sie ein oder ein Array von Zeichenfolgen übergeben: Auf diese Weise kann Teams überprüfen, ob die App, die das Ergebnis sendet, dieselbe ist, die das Aufgabenmodul aufgerufen `submitTask()` `result`  `appId` `appId` hat. Ihr Bot erhält eine `task/submit` Nachricht, einschließlich `result` wie unten [beschrieben.](#payload-of-taskfetch-and-tasksubmit-messages)
* **Adaptive Karte ( `TaskInfo.card` )**. Der Adaptive Kartentext (vom Benutzer ausgefüllt) wird über eine Nachricht an den Bot gesendet, wenn der Benutzer `task/submit` eine beliebige Schaltfläche `Action.Submit` drückt.

## <a name="the-flexibility-of-tasksubmit"></a>Die Flexibilität von Aufgabe/Absenden

Im vorherigen Abschnitt haben Sie erfahren, dass der Bot immer eine Nachricht empfängt, wenn der Benutzer mit einem Aufgabenmodul fertig ist, das von einem Bot aufgerufen `task/submit invoke` wird. Als Entwickler haben Sie mehrere Optionen, wenn *Sie auf* die Nachricht `task/submit` antworten:

| HTTP-Textkörperantwort                      | Szenario                                |
| --------------------------------------- | --------------------------------------- |
| Keine (Nachricht `task/submit` ignorieren) | Die einfachste Antwort ist überhaupt keine Antwort. Ihr Bot muss nicht reagieren, wenn der Benutzer mit dem Aufgabenmodul fertig ist. |
| <pre>{<br/>  "task": {<br/>    "type": "message",<br/>    "value": "Message text"<br/>  }<br/>}</pre> | Teams zeigt den Wert in `value` einem Popup-Meldungsfeld an. |
| <pre>{<br/>  "task": {<br/>    "type": "continue",<br/>    "value": &lt;TaskInfo object&gt;<br/>  }<br/>}</pre> | Ermöglicht es Ihnen, Sequenzen adaptiver Karten in einer Assistenten-/Mehrschritt-Erfahrung zu "verketten". _Beachten Sie, dass das Verketten adaptiver Karten in einer Sequenz ein erweitertes Szenario ist und hier nicht dokumentiert ist. Die Node.js-Beispiel-App unterstützt sie jedoch, und ihre Funktionsweise wird in der README.md [dokumentiert.](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs#implementation-notes)_ |

## <a name="payload-of-taskfetch-and-tasksubmit-messages"></a>Nutzlast von Aufgaben-/Abruf- und Vorgangs-/Absendennachrichten

In diesem Abschnitt wird das Schema definiert, was Ihr Bot empfängt, wenn er ein `task/fetch` oder `task/submit` ein Bot Framework-Objekt `Activity` empfängt. Die wichtige oberste Ebene wird unten angezeigt:

| Eigenschaft | Beschreibung                          |
| -------- | ------------------------------------ |
| `type`   | Wird immer sein `invoke`              |
| `name`   | Entweder `task/fetch` oder `task/submit` |
| `value`  | Die vom Entwickler definierte Nutzlast. Normalerweise spiegelt die Struktur des `value` Objekts wider, was von Teams gesendet wurde. In diesem Fall ist dies jedoch anders, da wir den dynamischen Abruf ( ) sowohl von Bot Framework ( ) als auch von adaptiven Kartenaktionen ( ) unterstützen möchten, und wir benötigen eine Möglichkeit, Teams mit dem Bot zu kommunizieren, zusätzlich zu dem, was in enthalten `task/fetch` `value` `Action.Submit` `data` `context` `value` / `data` war.<br/><br/>Dazu kombinieren wir die beiden zu einem übergeordneten Objekt:<br/><br/><pre>{<br/>  "context": {<br/>    "theme": "default" &vert; "dark" &vert; "contrast",<br/>  },<br/>  "data": [value field from Bot Framework card] &vert; [data field from Adaptive Card] <br/>}</pre>  |

## <a name="example-receiving-and-responding-to-taskfetch-and-tasksubmit-invoke-messages---nodejs"></a>Beispiel: Empfangen und Reagieren auf Aufgaben-/Abruf- und Task-/Submit-Aufrufnachrichten – Node.js

> [!NOTE]
> Der folgende Beispielcode wurde zwischen Technical Preview und der endgültigen Version dieses Features geändert: Das Schema der Anforderung wurde geändert, um dem im vorherigen Abschnitt `task/fetch` [dokumentierten Schema zu folgen.](#payload-of-taskfetch-and-tasksubmit-messages) Das heißt, die Dokumentation war richtig, aber die Implementierung nicht. Was sich geändert hat, erfahren Sie in `// for Technical Preview [...]` den kommentaren unten.

```typescript
// Handle requests and responses for a "Custom Form" and an "Adaptive card" task module.
// Assumes request is coming from an Adaptive card Action.Submit button that has a "taskModule" property indicating what to invoke
private async onInvoke(event: builder.IEvent, cb: (err: Error, body: any, status?: number) => void): Promise<void> {
    let invokeType = (event as any).name;
    let invokeValue = (event as any).value;
    if (invokeType === undefined) {
        invokeType = null;
    }
    switch (invokeType) {
        case "task/fetch": {
            if (invokeValue !== undefined && invokeValue.data.taskModule === "customform") { // for Technical Preview, was invokeValue.taskModule
                // Return the specified task module response to the bot
                let fetchTemplate: any = {
                    "task": {
                        "type": "continue",
                        "value": {
                            "title": "Custom Form",
                            "height": 510,
                            "width": 430,
                            "fallbackUrl": "https://contoso.com/teamsapp/customform",
                            "url": "https://contoso.com/teamsapp/customform",
                        }
                    }
                };
                cb(null, fetchTemplate, 200);
            };
            if (invokeValue !== undefined && invokeValue.data.taskModule === "adaptivecard") { // for Technical Preview, was invokeValue.taskModule
                let adaptiveCard = {
                    "type": "AdaptiveCard",
                    "body": [
                        {
                            "type": "TextBlock",
                            "text": "Here is a ninja cat:"
                        },
                        {
                            "type": "Image",
                            "url": "http://adaptivecards.io/content/cats/1.png",
                            "size": "Medium"
                        }
                    ],
                    "version": "1.0"
                };
                // Return the specified task module response to the bot
                let fetchTemplate: any = {
                    "task": {
                        "type": "continue",
                        "value": {
                            "title": "Ninja Cat",
                            "height": "small",
                            "width": "small",
                            "card": {
                                contentType: "application/vnd.microsoft.card.adaptive",
                                content: adaptiveCard,
                            }
                        }
                    }
                };
                cb(null, fetchTemplate, 200);
            };
            break;
        }
        case "task/submit": {
            if (invokeValue.data !== undefined) {
                // It's a valid task module response
                let submitResponse: any = {
                    "task": {
                        "type": "message",
                        "value": "Task complete!",
                    }
                };
                cb(null, fetchTemplates.submitMessageResponse, 200)
            }
        }
    }
}
```

*Weitere Informationen finden* Sie unter Beispielcode des [Microsoft Teams-Aufgabenmoduls – nodejs](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs/blob/master/src/TeamsBot.ts) und [Bot Framework-Beispiele.](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)

## <a name="example-receiving-and-responding-to-taskfetch-and-tasksubmit-invoke-messages---c"></a>Beispiel: Empfangen und Antworten auf Aufgaben-/Abruf- und Task-/Submit-Aufrufnachrichten - C #

In C# werden Nachrichten von einem Controller verarbeitet, der `invoke` `HttpResponseMessage()` eine Nachricht `Activity` verarbeitet. Die `task/fetch` Anforderungen und Antworten sind `task/submit` JSON. In C# ist es nicht so praktisch, mit unformatiertem JSON zu umgehen wie in Node.js, daher benötigen Sie Wrapperklassen, um die Serialisierung von und zu JSON zu verarbeiten. Es gibt noch keine direkte Unterstützung dafür im Microsoft Teams [C# SDK,](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) aber Sie können ein Beispiel dafür sehen, wie diese einfachen Wrapperklassen in der [C#-Beispiel-App aussehen würden.](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Models/TaskModel.cs)

Nachfolgend finden Sie Beispielcode in C# für die Behandlung und Nachrichten mithilfe dieser `task/fetch` `task/submit` Wrapperklassen ( `TaskInfo` , ), `TaskEnvelope` auszugsweise aus dem [Beispiel](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs):

```csharp
private HttpResponseMessage HandleInvokeMessages(Activity activity)
{
    var activityValue = activity.Value.ToString();
    if (activity.Name == "task/fetch")
    {
        var action = Newtonsoft.Json.JsonConvert.DeserializeObject<Models.BotFrameworkCardValue<string>>(activityValue);

        Models.TaskInfo taskInfo = GetTaskInfo(action.Data);
        Models.TaskEnvelope taskEnvelope = new Models.TaskEnvelope
        {
            Task = new Models.Task()
            {
                Type = Models.TaskType.Continue,
                TaskInfo = taskInfo
            }
        };
        return Request.CreateResponse(HttpStatusCode.OK, taskEnvelope);
    }
    else if (activity.Name == "task/submit")
    {
        ConnectorClient connector = new ConnectorClient(new Uri(activity.ServiceUrl));
        Activity reply = activity.CreateReply("Received = " + activity.Value.ToString());
        connector.Conversations.ReplyToActivity(reply);
    }
    return new HttpResponseMessage(HttpStatusCode.Accepted);
}

// Helper function for building the TaskInfo object based on the incoming request
private static Models.TaskInfo GetTaskInfo(string actionInfo)
{
    Models.TaskInfo taskInfo = new Models.TaskInfo();
    switch (actionInfo)
    {
        case TaskModuleIds.YouTube:
            taskInfo.Url = taskInfo.FallbackUrl = ApplicationSettings.BaseUrl + "/" + TaskModuleIds.YouTube;
            SetTaskInfo(taskInfo, TaskModuleUIConstants.YouTube);
            break;
        case TaskModuleIds.PowerApp:
            taskInfo.Url = taskInfo.FallbackUrl = ApplicationSettings.BaseUrl + "/" + TaskModuleIds.PowerApp;
            SetTaskInfo(taskInfo, TaskModuleUIConstants.PowerApp);
            break;
        case TaskModuleIds.CustomForm:
            taskInfo.Url = taskInfo.FallbackUrl = ApplicationSettings.BaseUrl + "/" + TaskModuleIds.CustomForm;
            SetTaskInfo(taskInfo, TaskModuleUIConstants.CustomForm);
            break;
        case TaskModuleIds.AdaptiveCard:
            taskInfo.Card = AdaptiveCardHelper.GetAdaptiveCard();
            SetTaskInfo(taskInfo, TaskModuleUIConstants.AdaptiveCard);
            break;
        default:
            break;
    }
    return taskInfo;
}
```

Im obigen Beispiel wird die Funktion nicht angezeigt, mit der die Eigenschaften , und des Objekts `SetTaskInfo()` für jeden Fall festgelegt `height` `width` `title` `TaskInfo` werden. Hier ist der [Quellcode für SetTaskInfo()](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs).

### <a name="bot-framework-card-actions-vs-adaptive-card-actionsubmit-actions"></a>Aktionen von Bot Framework-Karten im Vergleich zu Aktionen für adaptive Karten Action.Submit

Das Schema für Bot Framework-Kartenaktionen ist etwas anders als adaptive `Action.Submit` Kartenaktionen. Daher ist auch die Methode zum Aufrufen von Aufgabenmodulen etwas anders: Das Objekt in enthält ein Objekt, sodass es keine anderen Eigenschaften in der Karte `data` `Action.Submit` `msteams` beeinträchtigt. Die folgende Tabelle zeigt ein Beispiel für die einzelnen Beispiele:

| Bot Framework-Kartenaktion                              | Aktion für adaptive Karten Action.Submit                     |
| ------------------------------------------------------ | ------------------------------------------------------ |
| <pre>{<br/>  "type": "invoke",<br/>  "title": "Buy",<br/>  "value": {<br/>    "type": "task/fetch",<br/>    &lt;...&gt;<br/>  }<br/>}</pre> | <pre>{<br/>  "type": "Action.Submit",<br/>  "id": "btnBuy",<br/>  "title": "Buy",<br/>  "data": {<br/>    &lt;...&gt;,<br/>    "msteams": {<br/>      "type": "task/fetch"<br/>    }<br/>  }<br/>}</pre>  |
