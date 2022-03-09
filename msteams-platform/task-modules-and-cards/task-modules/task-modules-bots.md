---
title: Verwenden von Aufgabenmodulen in Microsoft Teams Bots
description: Verwenden von Aufgabenmodulen mit Microsoft Teams Bots, einschließlich Bot Framework-Karten, adaptiven Karten und Deep-Links.
ms.localizationpriority: medium
ms.topic: how-to
keywords: Taskmodule Teams Bots Deep Links adaptive Karte
ms.openlocfilehash: 39df7f3845cc11e6e15da03c72b0c792a795af35
ms.sourcegitcommit: 2fdca6fb0ade3f6b460eb9a4dfea0a8e2ab8d3b9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2022
ms.locfileid: "63355720"
---
# <a name="use-task-modules-from-bots"></a>Verwenden von Aufgabenmodulen aus Bots
 
Aufgabenmodule können von Microsoft Teams Bots mithilfe von Schaltflächen auf adaptiven Karten und Bot Framework-Karten aufgerufen werden, die Hero-, Miniaturansicht- und Office 365 Connector sind. Aufgabenmodule sind häufig eine bessere Benutzererfahrung als mehrere Unterhaltungsschritte. Verfolgen Sie den Botstatus, und erlauben Sie dem Benutzer, die Sequenz zu unterbrechen oder abzubrechen.

Es gibt zwei Möglichkeiten zum Aufrufen von Aufgabenmodulen:

* Eine neue Art von Aufrufnachricht `task/fetch`: Die Verwendung der `invoke` [Kartenaktion](~/task-modules-and-cards/cards/cards-actions.md#action-type-invoke) für Bot Framework-Karten oder der `Action.Submit` [Kartenaktion](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) für adaptive Karten mit `task/fetch`dem Aufgabenmodul einer URL oder einer adaptiven Karte wird dynamisch von Ihrem Bot abgerufen.
* Deep-Link-URLs: Mithilfe der [Deep Link-Syntax für Aufgabenmodule](~/task-modules-and-cards/task-modules/invoking-task-modules.md#task-module-deep-link-syntax) können Sie die `openUrl` [Kartenaktion](~/task-modules-and-cards/cards/cards-actions.md#action-type-openurl) für Bot Framework-Karten bzw. die `Action.OpenUrl` [Kartenaktion](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) für adaptive Karten verwenden. Bei Deep-Link-URLs ist die URL des Aufgabenmoduls oder der Textkörper für adaptive Karten bereits bekannt, um einen Server-Roundtrip relativ zu zu vermeiden `task/fetch`.

> [!IMPORTANT]
> Jedes `url` muss `fallbackUrl` das HTTPS-Verschlüsselungsprotokoll implementieren.

Der nächste Abschnitt enthält Details zum Aufrufen eines Aufgabenmoduls mit .`task/fetch`

## <a name="invoke-a-task-module-using-taskfetch"></a>Aufrufen eines Aufgabenmoduls mithilfe von "task/fetch"

Wenn das `value` Objekt der `invoke` Kartenaktion initialisiert oder `Action.Submit` initialisiert wird und ein Benutzer die Schaltfläche auswählt, wird eine `invoke` Nachricht an den Bot gesendet. In der HTTP-Antwort auf die `invoke` Nachricht ist ein [TaskInfo-Objekt](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object) in ein Wrapperobjekt eingebettet, das Teams zum Anzeigen des Aufgabenmoduls verwendet.

![Task-/Fetch-Anforderung oder -Antwort](~/assets/images/task-module/task-module-invoke-request-response.png)

Die folgenden Schritte stellen das Aufgabenmodul "Aufrufen" mithilfe von "task/fetch" bereit:

1. Diese Abbildung zeigt eine Bot Framework-Hero-Karte mit einer **Aktion "Karte kaufen** `invoke` ["](~/task-modules-and-cards/cards/cards-actions.md#action-type-invoke). Der Wert der `type` Eigenschaft ist `task/fetch` , und der Rest des `value` Objekts kann Von Ihrer Wahl sein.
1. Der Bot empfängt die `invoke` HTTP POST-Nachricht.
1. Der Bot erstellt ein Antwortobjekt und gibt es im Textkörper der POST-Antwort mit einem HTTP 200-Antwortcode zurück. Weitere Informationen zum Schema für Antworten finden Sie [in der Erläuterung zu Aufgabe/Übermittlung](#the-flexibility-of-tasksubmit). Der folgende Code enthält ein Beispiel für den Textkörper der HTTP-Antwort, die ein in ein Wrapperobjekt eingebettetes [TaskInfo-Objekt](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object) enthält:

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

    Das `task/fetch` Ereignis und seine Antwort für Bots ähneln der `microsoftTeams.tasks.startTask()` Funktion im Client-SDK.

1. Microsoft Teams zeigt das Aufgabenmodul an.

Der nächste Abschnitt enthält Details zum Übermitteln des Ergebnisses eines Aufgabenmoduls.

## <a name="submit-the-result-of-a-task-module"></a>Übermitteln des Ergebnisses eines Aufgabenmoduls

Wenn der Benutzer mit dem Aufgabenmodul fertig ist, ähnelt das Senden des Ergebnisses an den Bot der Funktionsweise mit Registerkarten. Weitere Informationen finden Sie im [Beispiel zum Übermitteln des Ergebnisses eines Aufgabenmoduls](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-of-submitting-the-result-of-a-task-module). Es gibt einige Unterschiede:

* HTML oder JavaScript, d `TaskInfo.url`. h.: Nachdem Sie überprüft haben, was der Benutzer eingegeben hat, rufen Sie die `microsoftTeams.tasks.submitTask()` SDK-Funktion auf, die nachfolgend als `submitTask()` aus Lesbarkeitsgründen bezeichnet wird. Sie können ohne Parameter aufrufen`submitTask()`, wenn Teams das Aufgabenmodul schließen möchten, Aber Sie müssen ein Objekt oder eine Zeichenfolge an Ihre `submitHandler`übergeben. Übergeben Sie ihn als ersten Parameter, `result`. Teams aufgerufen `submitHandler`wird, `err` ist `null`und `result` ist das Objekt oder die Zeichenfolge, an `submitTask()`die Sie übergeben haben. Wenn Sie mit einem Parameter aufrufen`submitTask()`, müssen Sie ein `appId` oder ein Array von Zeichenfolgen `appId` `result` übergeben. Dadurch können Teams überprüfen, ob die App, die das Ergebnis sendet, dieselbe ist, die das Aufgabenmodul aufgerufen hat. Ihr Bot empfängt eine `task/submit` Nachricht einschließlich `result`. Weitere Informationen finden Sie unter [Nutzlast und `task/fetch` `task/submit` Nachrichten](#payload-of-taskfetch-and-tasksubmit-messages).
* Adaptive Karte, d. h.: `TaskInfo.card`Der vom Benutzer ausgefüllte Textkörper der adaptiven Karte wird über eine Nachricht an den Bot gesendet, wenn der Benutzer eine `task/submit` beliebige `Action.Submit` Schaltfläche auswählt.

Der nächste Abschnitt enthält Details zur Flexibilität von `task/submit`.

## <a name="the-flexibility-of-tasksubmit"></a>Die Flexibilität von Aufgabe/Übermittlung

Wenn der Benutzer mit einem Aufgabenmodul fertig ist, das von einem Bot aufgerufen wird, erhält der Bot immer eine `task/submit invoke` Nachricht. Sie haben mehrere Optionen, wenn Sie auf die `task/submit` Nachricht wie folgt reagieren:

| HTTP-Textkörperantwort                      | Szenario                                |
| --------------------------------------- | --------------------------------------- |
| Keine ignoriert die `task/submit` Nachricht | Die einfachste Antwort ist gar keine Antwort. Ihr Bot muss nicht antworten, wenn der Benutzer mit dem Aufgabenmodul fertig ist. |
| <pre>{<br/>  "task": {<br/>    "type": "message",<br/>    "value": "Message text"<br/>  }<br/>}</pre> | Teams zeigt den Wert in `value` einem Popup-Meldungsfeld an. |
| <pre>{<br/>  "task": {<br/>    "type": "continue",<br/>    "value": &lt;TaskInfo object&gt;<br/>  }<br/>}</pre> | Ermöglicht ihnen das Verketten von Sequenzen adaptiver Karten in einem Assistenten oder einer mehrstufigen Oberfläche. |

> [!NOTE]
> Das Verketten adaptiver Karten in einer Sequenz ist ein erweitertes Szenario. Die Node.js-Beispiel-App unterstützt sie. Weitere Informationen finden Sie unter [Microsoft Teams Aufgabenmodul Node.js](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs#implementation-notes).

Der nächste Abschnitt enthält Details zur Nutzlast und `task/fetch` `task/submit` zu Nachrichten.

## <a name="payload-of-taskfetch-and-tasksubmit-messages"></a>Nutzlast von Aufgaben-/Abruf- und Aufgaben-/Sendenachrichten

In diesem Abschnitt wird das Schema definiert, was Ihr Bot empfängt, wenn er ein `task/fetch` Bot Framework-Objekt `task/submit` `Activity` empfängt. Die folgende Tabelle enthält die Eigenschaften der Nutzlast und `task/submit` der `task/fetch` Nachrichten:

| Eigenschaft | Beschreibung                          |
| -------- | ------------------------------------ |
| `type`   | Ist immer `invoke`.           |
| `name`   | Ist entweder `task/fetch` oder `task/submit`. |
| `value`  | Ist die vom Entwickler definierte Nutzlast. Die Struktur des `value` Objekts entspricht dem, was von Teams gesendet wird. In diesem Fall ist dies jedoch anders. Es erfordert Unterstützung für das dynamische Abrufen, das `task/fetch` sowohl vom Bot-Framework stammt, als `value` auch von adaptiven Kartenaktionen `Action.Submit` , also `data`. Eine Möglichkeit, Teams `context` an den Bot zu kommunizieren, ist zusätzlich zu dem, was in `value` oder `data`enthalten ist, erforderlich.<br/><br/>Kombinieren Sie "Wert" und "Daten" in einem übergeordneten Objekt:<br/><br/><pre>{<br/>  "context": {<br/>    "theme": "default" &vert; "dark" &vert; "contrast",<br/>  },<br/>  "data": [value field from Bot Framework card] &vert; [data field from Adaptive Card] <br/>}</pre>  |

Der nächste Abschnitt enthält ein Beispiel für das Empfangen und Reagieren auf `task/fetch` und `task/submit` Aufrufen von Nachrichten in Node.js.

## <a name="example-of-taskfetch-and-tasksubmit-invoke-messages-in-nodejs-and-c"></a>Beispiel für Task-/Fetch- und Task/Submit-Aufrufnachrichten in Node.js und C #

# <a name="nodejs"></a>[Node.js](#tab/nodejs)

```typescript
handleTeamsTaskModuleFetch(context, taskModuleRequest) {
    // Called when the user selects an options from the displayed HeroCard or
    // AdaptiveCard.  The result is the action to perform.

    const cardTaskFetchValue = taskModuleRequest.data.data;
    var taskInfo = {}; // TaskModuleTaskInfo

    if (cardTaskFetchValue === TaskModuleIds.YouTube) {
        // Display the YouTube.html page
        taskInfo.url = taskInfo.fallbackUrl = this.baseUrl + '/' + TaskModuleIds.YouTube + '.html';
        this.setTaskInfo(taskInfo, TaskModuleUIConstants.YouTube);
    } else if (cardTaskFetchValue === TaskModuleIds.CustomForm) {
        // Display the CustomForm.html page, and post the form data back via
        // handleTeamsTaskModuleSubmit.
        taskInfo.url = taskInfo.fallbackUrl = this.baseUrl + '/' + TaskModuleIds.CustomForm + '.html';
        this.setTaskInfo(taskInfo, TaskModuleUIConstants.CustomForm);
    } else if (cardTaskFetchValue === TaskModuleIds.AdaptiveCard) {
        // Display an AdaptiveCard to prompt user for text, and post it back via
        // handleTeamsTaskModuleSubmit.
        taskInfo.card = this.createAdaptiveCardAttachment();
        this.setTaskInfo(taskInfo, TaskModuleUIConstants.AdaptiveCard);
    }

    return TaskModuleResponseFactory.toTaskModuleResponse(taskInfo);
}

async handleTeamsTaskModuleSubmit(context, taskModuleRequest) {
    // Called when data is being returned from the selected option (see `handleTeamsTaskModuleFetch').

    // Echo the users input back.  In a production bot, this is where you'd add behavior in
    // response to the input.
    await context.sendActivity(MessageFactory.text('handleTeamsTaskModuleSubmit: ' + JSON.stringify(taskModuleRequest.data)));

    // Return TaskModuleResponse
    return {
        // TaskModuleMessageResponse
        task: {
            type: 'message',
            value: 'Thanks!'
        }
    };
}

setTaskInfo(taskInfo, uiSettings) {
    taskInfo.height = uiSettings.height;
    taskInfo.width = uiSettings.width;
    taskInfo.title = uiSettings.title;
}
```

# <a name="c"></a>[C#](#tab/csharp)

```csharp
protected override Task<TaskModuleResponse> OnTeamsTaskModuleFetchAsync(ITurnContext<IInvokeActivity> turnContext, TaskModuleRequest taskModuleRequest, CancellationToken cancellationToken)
{
    var asJobject = JObject.FromObject(taskModuleRequest.Data);
    var value = asJobject.ToObject<CardTaskFetchValue<string>>()?.Data;

    var taskInfo = new TaskModuleTaskInfo();
    switch (value)
    {
        case TaskModuleIds.YouTube:
            taskInfo.Url = taskInfo.FallbackUrl = _baseUrl + "/" + TaskModuleIds.YouTube;
            SetTaskInfo(taskInfo, TaskModuleUIConstants.YouTube);
            break;
        case TaskModuleIds.CustomForm:
            taskInfo.Url = taskInfo.FallbackUrl = _baseUrl + "/" + TaskModuleIds.CustomForm;
            SetTaskInfo(taskInfo, TaskModuleUIConstants.CustomForm);
            break;
        case TaskModuleIds.AdaptiveCard:
            taskInfo.Card = CreateAdaptiveCardAttachment();
            SetTaskInfo(taskInfo, TaskModuleUIConstants.AdaptiveCard);
            break;
        default:
            break;
    }

    return Task.FromResult(taskInfo.ToTaskModuleResponse());
}

protected override async Task<TaskModuleResponse> OnTeamsTaskModuleSubmitAsync(ITurnContext<IInvokeActivity> turnContext, TaskModuleRequest taskModuleRequest, CancellationToken cancellationToken)
{
    var reply = MessageFactory.Text("OnTeamsTaskModuleSubmitAsync Value: " + JsonConvert.SerializeObject(taskModuleRequest));
    await turnContext.SendActivityAsync(reply, cancellationToken);

    return TaskModuleResponseFactory.CreateResponse("Thanks!");
}

private static void SetTaskInfo(TaskModuleTaskInfo taskInfo, UISettings uIConstants)
{
    taskInfo.Height = uIConstants.Height;
    taskInfo.Width = uIConstants.Width;
    taskInfo.Title = uIConstants.Title.ToString();
}
```

---

### <a name="bot-framework-card-actions-vs-adaptive-card-actionsubmit-actions"></a>Bot Framework-Kartenaktionen im Vergleich zu Aktionen für adaptive Karten.Submit-Aktionen

Das Schema für Bot Framework-Kartenaktionen unterscheidet sich von adaptiven Kartenaktionen `Action.Submit` , und die Möglichkeit zum Aufrufen von Aufgabenmodulen unterscheidet sich ebenfalls. Das `data` Objekt enthält `Action.Submit` ein `msteams` Objekt, sodass es andere Eigenschaften auf der Karte nicht beeinträchtigt. Die folgende Tabelle zeigt ein Beispiel für jede Kartenaktion:

| Bot Framework-Kartenaktion                              | Aktion für adaptive Karten.Submit-Aktion                     |
| ------------------------------------------------------ | ------------------------------------------------------ |
| <pre>{<br/>  "type": "invoke",<br/>  "title": "Buy",<br/>  "value": {<br/>    "type": "task/fetch",<br/>    &lt;...&gt;<br/>  }<br/>}</pre> | <pre>{<br/>  "type": "Action.Submit",<br/>  "id": "btnBuy",<br/>  "title": "Buy",<br/>  "data": {<br/>    &lt;...&gt;,<br/>    "msteams": {<br/>      "type": "task/fetch"<br/>    }<br/>  }<br/>}</pre>  |

## <a name="code-sample"></a>Codebeispiel

|Beispielname | Beschreibung | .NET | Node.js|
|----------------|-----------------|--------------|----------------|
|Aufgabenmodul-Beispielbots-V4 | Beispiele zum Erstellen von Aufgabenmodulen. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/54.teams-task-module)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/54.teams-task-module)|

## <a name="step-by-step-guide"></a>Schrittweise Anleitung

Befolgen Sie die schrittweise Anleitung zum Erstellen und Abrufen [des Aufgabenmodul-Bots](../../sbs-botbuilder-taskmodule.yml) in Teams.

## <a name="see-also"></a>Siehe auch

* [Beispielcode für Microsoft Teams Aufgabenmodul in Node.js](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs/blob/master/src/TeamsBot.ts)
* [Bot Framework-Beispiele](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)
