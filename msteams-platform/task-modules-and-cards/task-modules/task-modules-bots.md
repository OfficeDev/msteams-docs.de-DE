---
title: Verwenden von Taskmodulen in Microsoft Teams Bots
description: So verwenden Sie Aufgabenmodule mit Microsoft Teams Bots, einschließlich Bot Framework-Karten, Adaptive-Karten und Deep Links
localization_priority: Normal
ms.topic: how-to
keywords: Task-Module Teams Bots
ms.openlocfilehash: bfaf3dfe791c1736aeb418e2689e513908f04534
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566568"
---
# <a name="using-task-modules-from-microsoft-teams-bots"></a>Verwenden von Task-Modulen aus Microsoft Teams Bots

Task-Module können von Microsoft Teams Bots mithilfe von Schaltflächen auf Adaptive-Karten und Bot Framework-Karten (Hero, Thumbnail und Office 365 Connector) aufgerufen werden. Aufgabenmodule sind oft eine bessere Benutzererfahrung als mehrere Unterhaltungsschritte, bei denen Sie als Entwickler den Bot-Status nachverfolgen und dem Benutzer erlauben müssen, die Sequenz zu unterbrechen/abzubrechen.

Es gibt zwei Möglichkeiten, Aufgabenmodule aufzuberufen:

* **Eine neue Art von Aufrufnachricht `task/fetch` .** Mit der `invoke` [Kartenaktion](~/task-modules-and-cards/cards/cards-actions.md#invoke) für Bot Framework-Karten oder der `Action.Submit` [Kartenaktion](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) für Adaptive-Karten wird `task/fetch` das Taskmodul (entweder eine URL oder eine adaptive Karte) dynamisch von Ihrem Bot abgerufen.
* **Deep link URLs.** Mithilfe der [Deep Link-Syntax für Aufgabenmodule](~/task-modules-and-cards/what-are-task-modules.md#task-module-deep-link-syntax)können Sie die `openUrl` [Kartenaktion](~/task-modules-and-cards/cards/cards-actions.md#openurl) für Bot Framework-Karten bzw. die `Action.OpenUrl` [Kartenaktion](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) für Adaptive-Karten verwenden. Mit Deep Link URLs ist die URL des Taskmoduls oder der Adaptive-Kartentext offensichtlich im Voraus bekannt, wodurch ein Server-Roundtrip relativ zu vermieden `task/fetch` wird.

>[!IMPORTANT]
>Um eine sichere Kommunikation zu gewährleisten, müssen die `url` einzelnen und müssen das `fallbackUrl` HTTPS-Verschlüsselungsprotokoll implementieren.

## <a name="invoking-a-task-module-through-taskfetch"></a>Aufrufen eines Aufgabenmoduls durch Aufgabe/Abruf

Wenn das `value` Objekt der `invoke` Kartenaktion oder in der richtigen Weise `Action.Submit` initialisiert wird (weiter unten ausführlicher erläutert), wenn ein Benutzer die Taste drückt, wird eine `invoke` Nachricht an den Bot gesendet. In der HTTP-Antwort auf die `invoke` Nachricht befindet sich ein [TaskInfo-Objekt,](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) das in ein Wrapperobjekt eingebettet ist und Teams zum Anzeigen des Taskmoduls verwendet.

![Task/Fetch-Anforderung/Antwort](~/assets/images/task-module/task-module-invoke-request-response.png)

Sehen wir uns jeden Schritt etwas genauer an:

1. Dieses Beispiel zeigt eine Bot Framework Hero-Karte mit einer `invoke` ["Buy"-Kartenaktion](~/task-modules-and-cards/cards/cards-actions.md#invoke). Der Wert der `type` Eigenschaft ist - der Rest des `task/fetch` `value` Objekts kann sein, was Sie mögen.
1. Der Bot empfängt die `invoke` HTTP POST-Nachricht.
1. Der Bot erstellt ein Antwortobjekt und gibt es im Text der POST-Antwort mit einem HTTP 200-Antwortcode zurück. Das Schema für Antworten wird [unten in der Diskussion über task/submit](#the-flexibility-of-tasksubmit)beschrieben, aber das Wichtige, was Sie sich jetzt merken sollten, ist, dass der Text der HTTP-Antwort ein [TaskInfo-Objekt](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) enthält, das in ein Wrapperobjekt eingebettet ist. Zum Beispiel:

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

    Das `task/fetch` Ereignis und seine Reaktion für Bots ist konzeptionell der Funktion im `microsoftTeams.tasks.startTask()` Client-SDK ähnlich.
1. Microsoft Teams zeigt das Aufgabenmodul an.

## <a name="submitting-the-result-of-a-task-module"></a>Übermitteln des Ergebnisses eines Aufgabenmoduls

Wenn der Benutzer mit dem Taskmodul fertig ist, ist das Senden des Ergebnisses an den Bot ähnlich [wie bei Registerkarten,](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-submitting-the-result-of-a-task-module)aber es gibt ein paar Unterschiede, so dass es auch hier beschrieben wird.

* **HTML/JavaScript ( `TaskInfo.url` )**. Nachdem Sie überprüft haben, was der Benutzer eingegeben hat, rufen Sie die `microsoftTeams.tasks.submitTask()` SDK-Funktion auf (im Folgenden als aus Gründen der `submitTask()` Lesbarkeit bezeichnet). Sie können ohne Parameter aufrufen, wenn Sie nur möchten, `submitTask()` dass Teams das Aufgabenmodul schließen möchten, aber die meiste Zeit ein Objekt oder eine Zeichenfolge an Ihre übergeben `submitHandler` möchten. Übergeben Sie es einfach als ersten Parameter, `result` . Teams ruft `submitHandler` auf : wird das `err` `null` `result` Objekt/die Zeichenfolge sein, die Sie an übergeben `submitTask()` haben. Wenn Sie `submitTask()` mit einem `result` Parameter aufrufen, **müssen** Sie ein oder ein Array `appId` von `appId` Zeichenfolgen übergeben: Dies ermöglicht es Teams zu überprüfen, ob die App, die das Ergebnis sendet, dieselbe ist, die das Taskmodul aufgerufen hat. Ihr Bot erhält eine `task/submit` Nachricht, einschließlich `result` wie [unten](#payload-of-taskfetch-and-tasksubmit-messages)beschrieben .
* **Adaptive Karte ( `TaskInfo.card` )**. Der Adaptive-Kartentext (wie vom Benutzer ausgefüllt) wird über eine Nachricht an den Bot `task/submit` gesendet, wenn der Benutzer eine `Action.Submit` beliebige Taste drückt.

## <a name="the-flexibility-of-tasksubmit"></a>Die Flexibilität der Aufgabe/Einreichung

Im vorherigen Abschnitt haben Sie erfahren, dass der Bot immer eine Nachricht empfängt, wenn der Benutzer mit einem Taskmodul abgeschlossen ist, das von einem Bot aufgerufen `task/submit invoke` wird. Als Entwickler haben Sie mehrere Optionen, wenn Sie *auf* die Nachricht `task/submit` antworten:

| HTTP-Körperantwort                      | Szenario                                |
| --------------------------------------- | --------------------------------------- |
| Keine (ignorieren Sie die `task/submit` Nachricht) | Die einfachste Antwort ist überhaupt keine Antwort. Ihr Bot muss nicht reagieren, wenn der Benutzer mit dem Taskmodul fertig ist. |
| <pre>{<br/>  "task": {<br/>    "type": "message",<br/>    "value": "Message text"<br/>  }<br/>}</pre> | Teams zeigt den Wert von `value` in einem Popup-Meldungsfeld an. |
| <pre>{<br/>  "task": {<br/>    "type": "continue",<br/>    "value": &lt;TaskInfo object&gt;<br/>  }<br/>}</pre> | Ermöglicht es Ihnen, Sequenzen von adaptiven Karten in einem Assistenten/mehrstufigen Erlebnis zusammen zu "ketten". _Beachten Sie, dass das Verketten von adaptiven Karten in einer Sequenz ein erweitertes Szenario ist und hier nicht dokumentiert ist. Die Node.js-Beispiel-App unterstützt sie jedoch, und wie sie funktioniert, wird in [der README.md-Datei](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs#implementation-notes)dokumentiert._ |

## <a name="payload-of-taskfetch-and-tasksubmit-messages"></a>Nutzlast von Aufgaben-/Abruf- und Aufgaben-/Absendenvon Nachrichten

In diesem Abschnitt wird das Schema dessen definiert, was Ihr Bot empfängt, wenn er ein `task/fetch` oder `task/submit` Bot `Activity` Framework-Objekt empfängt. Die wichtige oberste Ebene erscheint unten:

| Eigenschaft | Beschreibung                          |
| -------- | ------------------------------------ |
| `type`   | Wird immer `invoke`              |
| `name`   | Entweder `task/fetch` oder `task/submit` |
| `value`  | Die vom Entwickler definierte Nutzlast. Normalerweise spiegelt die Struktur des `value` Objekts wider, was von Teams gesendet wurde. In diesem Fall ist es jedoch anders, weil wir dynamisches Abrufen ( ) von Bot Framework ( ) und Adaptive Card-Aktionen ( ) unterstützen `task/fetch` `value` `Action.Submit` `data` möchten, und wir benötigen eine Möglichkeit, Teams dem Bot `context` zusätzlich zu dem zu kommunizieren, was in enthalten `value` / `data` war.<br/><br/>Wir tun dies, indem wir die beiden zu einem übergeordneten Objekt kombinieren:<br/><br/><pre>{<br/>  "context": {<br/>    "theme": "default" &vert; "dark" &vert; "contrast",<br/>  },<br/>  "data": [value field from Bot Framework card] &vert; [data field from Adaptive Card] <br/>}</pre>  |

## <a name="example-receiving-and-responding-to-taskfetch-and-tasksubmit-invoke-messages---nodejs"></a>Beispiel: Empfangen und Beantworten von Aufgaben-/Abruf- und Aufgaben-/Sendeaufrufnachrichten - Node.js

> [!NOTE]
> Der folgende Beispielcode wurde zwischen Technical Preview und der endgültigen Version dieser Funktion geändert: Das Schema der Anforderung wurde geändert, um den `task/fetch` im vorherigen Abschnitt [dokumentierten](#payload-of-taskfetch-and-tasksubmit-messages)Informationen zu folgen. Das heißt, die Dokumentation war korrekt, aber die Umsetzung nicht. Sehen Sie sich die `// for Technical Preview [...]` Kommentare unten an, was sich geändert hat.

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

## <a name="example-receiving-and-responding-to-taskfetch-and-tasksubmit-invoke-messages---c"></a>Beispiel: Empfangen und Reagieren auf Aufgaben-/Abruf- und Task-/Sendeaufrufnachrichten - C #

In C-Bots werden Nachrichten von einem Controller verarbeitet, der `invoke` eine Nachricht `HttpResponseMessage()` `Activity` verarbeitet. Die `task/fetch` und Anfragen und Antworten sind `task/submit` JSON. Es ist nicht so bequem, mit rohem JSON umzugehen wie in Node.js, daher benötigen Sie Wrapperklassen, um die Serialisierung von und nach JSON zu verarbeiten. Es gibt noch keine direkte Unterstützung dafür im Microsoft Teams [C-SDK,](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) aber Sie können ein Beispiel dafür sehen, wie diese einfachen Wrapperklassen in der [Beispiel-App von C-](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Models/TaskModel.cs)aussehen würden.

Im Folgenden finden Sie Beispielcode in C- für die Handhabung `task/fetch` und Nachrichten mit diesen `task/submit` Wrapperklassen ( `TaskInfo` , ), aus dem `TaskEnvelope` [Beispiel](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs):

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

Nicht im obigen Beispiel wird die `SetTaskInfo()` Funktion angezeigt, die die `height` , und die Eigenschaften des `width` `title` `TaskInfo` Objekts für jeden Fall festlegt. Hier ist der [Quellcode für SetTaskInfo()](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs).

### <a name="bot-framework-card-actions-vs-adaptive-card-actionsubmit-actions"></a>Bot Framework-Kartenaktionen im Vergleich zu Adaptive Card Action.Submit-Aktionen

Das Schema für Bot Framework-Kartenaktionen unterscheidet sich geringfügig von adaptiven `Action.Submit` Kartenaktionen. Daher ist die Art und Weise, Aufgabenmodule aufzurufen, ebenfalls etwas anders: Das `data` Objekt in enthält ein `Action.Submit` `msteams` Objekt, sodass es andere Eigenschaften in der Karte nicht beeinträchtigt. Die folgende Tabelle zeigt ein Beispiel für jede:

| Bot Framework-Kartenaktion                              | Adaptive Karte Action.Submit-Aktion                     |
| ------------------------------------------------------ | ------------------------------------------------------ |
| <pre>{<br/>  "type": "invoke",<br/>  "title": "Buy",<br/>  "value": {<br/>    "type": "task/fetch",<br/>    &lt;...&gt;<br/>  }<br/>}</pre> | <pre>{<br/>  "type": "Action.Submit",<br/>  "id": "btnBuy",<br/>  "title": "Buy",<br/>  "data": {<br/>    &lt;...&gt;,<br/>    "msteams": {<br/>      "type": "task/fetch"<br/>    }<br/>  }<br/>}</pre>  |

## <a name="see-also"></a>Siehe auch

* [Beispielcode Microsoft Teams Taskmodul — nodejs](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs/blob/master/src/TeamsBot.ts)
* [Bot Framework-Beispiele](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).