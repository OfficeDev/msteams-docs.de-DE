---
title: Verwenden Sie Aufgabenmodule in Microsoft Teams-Bots
description: So verwenden Sie Aufgabenmodule mit Microsoft Teams-Bots, einschließlich Bot Framework-Karten, adaptive Karten und Deep Links.
ms.localizationpriority: high
ms.topic: how-to
keywords: Aufgabenmodule Teams Bots Deep Links Adaptive Karte
ms.openlocfilehash: 1074eee616ca7a5d78a071fb42c23d0010a8300d
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111332"
---
# <a name="use-task-modules-from-bots"></a>Verwenden von Aufgabenmodulen aus Bots

Aufgabenmodule können von Microsoft Teams-Bots mithilfe von Schaltflächen auf Adaptive Cards und Bot Framework-Karten aufgerufen werden, d. h. Hero, Thumbnail und Office 365 Connector. Aufgabenmodule bieten oft eine bessere Benutzererfahrung als mehrere Konversationsschritte. Verfolgen Sie den Bot-Status und erlauben Sie dem Benutzer, die Sequenz zu unterbrechen oder abzubrechen.

Es gibt zwei Möglichkeiten, Aufgabenmodule aufzurufen:

* Eine neue Art von Aufrufnachricht `task/fetch`: Die Verwendung der `invoke` [Kartenaktion](~/task-modules-and-cards/cards/cards-actions.md#action-type-invoke) für Bot Framework-Karten oder die `Action.Submit` [Kartenaktion](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) für adaptive Karten mit `task/fetch`einem Aufgabenmodul entweder einer URL oder einer adaptiven Karte wird dynamisch von Ihrem Bot abgerufen.
* Deep-Link-URLs: Mithilfe der [Deep-Link-Syntax für Aufgabenmodule](~/task-modules-and-cards/task-modules/invoking-task-modules.md#task-module-deep-link-syntax) können Sie die `openUrl` [Kartenaktion](~/task-modules-and-cards/cards/cards-actions.md#action-type-openurl) für Bot Framework-Karten bzw. die `Action.OpenUrl` [Kartenaktion](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) für adaptive Karten verwenden. Bei Deep-Link-URLs ist die Aufgabenmodul-URL oder der Textkörper der adaptiven Karte bereits bekannt, um einen Server-Roundtrip relativ zu zu zu `task/fetch`vermeiden.

> [!IMPORTANT]
> `fallbackUrl` Jeder `url` muss das HTTPS-Verschlüsselungsprotokoll implementieren.

Der nächste Abschnitt enthält Details zum Aufrufen eines Aufgabenmoduls mithilfe von `task/fetch`.

## <a name="invoke-a-task-module-using-taskfetch"></a>Aufrufen eines Aufgabenmoduls mithilfe von Task/Fetch

Wenn das `value` Objekt der `invoke` Kartenaktion initialisiert wird oder `Action.Submit` wenn ein Benutzer die Schaltfläche auswählt, wird eine `invoke` Nachricht an den Bot gesendet. In der HTTP-Antwort auf die `invoke` Nachricht ist ein [TaskInfo-Objekt](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object) in ein Wrapperobjekt eingebettet, das Teams verwendet, um das Aufgabenmodul anzuzeigen.

:::image type="content" source="../../assets/images/task-module/task-module-invoke-request-response.png" alt-text="Aufgaben-/Abrufanforderung oder -Antwort":::

Die folgenden Schritte stellen das Aufrufen des Aufgabenmoduls mithilfe von Task/Fetch bereit:

1. Diese Abbildung zeigt eine Bot Framework-Hero-Karte mit einer **Aktion "Karte kaufen** `invoke` ["](~/task-modules-and-cards/cards/cards-actions.md#action-type-invoke). Der Wert der `type` Eigenschaft ist `task/fetch`, und der Rest des `value` Objekts kann von Ihrer Wahl sein.
1. Der Bot empfängt die `invoke` HTTP POST-Nachricht.
1. Der Bot erstellt ein Antwortobjekt und gibt es im Textkörper der POST-Antwort mit einem HTTP 200-Antwortcode zurück. Weitere Informationen zum Schema für Antworten finden Sie [in der Diskussion zu Aufgabe/Absenden](#the-flexibility-of-tasksubmit). Der folgende Code enthält ein Beispiel für den Textkörper der HTTP-Antwort, der ein in ein Wrapperobjekt eingebettetes [TaskInfo-Objekt](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object) enthält:

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

## <a name="submit-the-result-of-a-task-module"></a>Senden Sie das Ergebnis eines Aufgabenmoduls

Wenn der Benutzer mit dem Aufgabenmodul fertig ist, wird das Ergebnis an den Bot zurückgesendet, ähnlich wie bei Registerkarten. Weitere Informationen finden Sie im [Beispiel zum Übermitteln des Ergebnisses eines Aufgabenmoduls](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-of-submitting-the-result-of-a-task-module). Es gibt einige Unterschiede wie folgt:

* HTML oder JavaScript: `TaskInfo.url`Nachdem Sie überprüft haben, was der Benutzer eingegeben hat, rufen Sie die SDK-Funktion auf, auf die `microsoftTeams.tasks.submitTask()` im Folgenden `submitTask()` aus Gründen der Lesbarkeit verwiesen wird. Sie können ohne Parameter aufrufen`submitTask()`, wenn Sie Teams das Aufgabenmodul schließen möchten, aber Sie müssen ein Objekt oder eine Zeichenfolge an Das `submitHandler`übergeben. Übergeben Sie ihn als ersten Parameter, `result`. Teams aufruft`submitHandler`, `err` ist `null`und `result` ist das Objekt oder die Zeichenfolge, das `submitTask()`Sie übergeben haben. Wenn Sie einen Aufruf mit einem Parameter ausführen`submitTask()`, müssen Sie ein `appId` oder ein Array von Zeichenfolgen `appId` `result` übergeben. Auf diese Weise können Teams überprüfen, ob die App, die das Ergebnis sendet, das gleiche ist, das das Aufgabenmodul aufgerufen hat. Ihr Bot erhält eine `task/submit` Nachricht, einschließlich `result`. Weitere Informationen finden Sie unter [Nutzlast und `task/fetch` `task/submit` Nachrichten](#payload-of-taskfetch-and-tasksubmit-messages).
* Adaptive Karte: `TaskInfo.card`Der Textkörper der adaptiven Karte, wie er vom Benutzer ausgefüllt wurde, wird über eine Nachricht an den Bot gesendet, wenn der Benutzer eine `task/submit` beliebige `Action.Submit` Schaltfläche auswählt.

Der nächste Abschnitt enthält Details zur Flexibilität von `task/submit`.

## <a name="the-flexibility-of-tasksubmit"></a>Die Flexibilität von Aufgabe/Absenden

Wenn der Benutzer mit einem Aufgabenmodul fertig ist, das von einem Bot aufgerufen wird, erhält der Bot immer eine `task/submit invoke` Nachricht. Beim Antworten auf die `task/submit` Nachricht stehen ihnen mehrere Optionen zur Verfügung:

| HTTP-Textantwort                      | Szenario                                |
| --------------------------------------- | --------------------------------------- |
| Keine ignoriert die `task/submit` Nachricht | Die einfachste Antwort ist überhaupt keine Antwort. Ihr Bot muss nicht reagieren, wenn der Benutzer mit dem Aufgabenmodul fertig ist. |
| <pre>{<br/>  "task": {<br/>    "type": "message",<br/>    "value": "Message text"<br/>  }<br/>}</pre> | Teams zeigt den Wert in `value` einem Popup-Meldungsfeld an. |
| <pre>{<br/>  "task": {<br/>    "type": "continue",<br/>    "value": &lt;TaskInfo object&gt;<br/>  }<br/>}</pre> | Ermöglicht es Ihnen, Sequenzen adaptiver Karten in einem Assistenten oder in mehreren Schritten miteinander zu verketten. |

> [!NOTE]
> Das Verketten adaptiver Karten in einer Sequenz ist ein fortgeschrittenes Szenario. Die Node.js-Beispiel-App unterstützt dies. Weitere Informationen finden Sie [unter Microsoft Teams Aufgabenmodul Node.js](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs#implementation-notes).

Der nächste Abschnitt enthält Details zu Nutzlast und `task/fetch` `task/submit` Nachrichten.

## <a name="payload-of-taskfetch-and-tasksubmit-messages"></a>Nutzlast von Aufgaben-/Abruf- und Aufgaben-/Sendenachrichten

In diesem Abschnitt wird das Schema definiert, das Ihr Bot erhält, wenn er ein `task/fetch` Oder `task/submit` Bot Framework-Objekt `Activity` empfängt. Die folgende Tabelle enthält die Eigenschaften von Nutzlast und `task/fetch` `task/submit` Nachrichten:

| Eigenschaft | Beschreibung                          |
| -------- | ------------------------------------ |
| `type`   | Ist immer `invoke`.           |
| `name`   | Ist entweder `task/fetch` oder `task/submit`. |
| `value`  | Ist die vom Entwickler definierte Nutzlast. Die Struktur des `value` Objekts entspricht der Struktur, die von Teams gesendet wird. In diesem Fall ist es jedoch anders. Es erfordert Unterstützung für `task/fetch` dynamisches Abrufen, das sowohl vom Bot-Framework, das heißt, als `value` auch von Adaptive Card-Aktionen `Action.Submit`, also `data`. Eine Möglichkeit, Teams `context` mit dem Bot zu kommunizieren, ist zusätzlich zu dem, was in oder enthalten ist, `value` erforderlich `data`.<br/><br/>Kombinieren Sie "Wert" und "Daten" in einem übergeordneten Objekt:<br/><br/><pre>{<br/>  "context": {<br/>    "theme": "default" &vert; "dark" &vert; "contrast",<br/>  },<br/>  "data": [value field from Bot Framework card] &vert; [data field from Adaptive Card] <br/>}</pre>  |

Der nächste Abschnitt enthält ein Beispiel für das Empfangen, Antworten `task/fetch` und `task/submit` Aufrufen von Nachrichten in Node.js.

## <a name="example-of-taskfetch-and-tasksubmit-invoke-messages-in-nodejs-and-c"></a>Beispiel für Aufrufen von Aufgaben-/Abruf- und Aufgaben-/Absenden-Nachrichten in Node.js und C #

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

### <a name="bot-framework-card-actions-vs-adaptive-card-actionsubmit-actions"></a>Bot Framework-Kartenaktionen im Vergleich zu Aktionsaktionen für adaptive Karten.Übermitteln von Aktionen

Das Schema für Bot Framework-Kartenaktionen unterscheidet sich von Aktionen für adaptive Karten `Action.Submit`, und auch das Aufrufen von Aufgabenmodulen unterscheidet sich. Das `data` Objekt in `Action.Submit` enthält ein `msteams` Objekt, sodass es andere Eigenschaften auf der Karte nicht stört. Die folgende Tabelle zeigt ein Beispiel für jede Kartenaktion:

| Bot Framework-Kartenaktion                              | Aktion für adaptive Karten.Submit                     |
| ------------------------------------------------------ | ------------------------------------------------------ |
| <pre>{<br/>  "type": "invoke",<br/>  "title": "Buy",<br/>  "value": {<br/>    "type": "task/fetch",<br/>    &lt;...&gt;<br/>  }<br/>}</pre> | <pre>{<br/>  "type": "Action.Submit",<br/>  "id": "btnBuy",<br/>  "title": "Buy",<br/>  "data": {<br/>    &lt;...&gt;,<br/>    "msteams": {<br/>      "type": "task/fetch"<br/>    }<br/>  }<br/>}</pre>  |

## <a name="code-sample"></a>Codebeispiel

|Beispielname | Beschreibung | .NET | Node.js|
|----------------|-----------------|--------------|----------------|
|Aufgabenmodul-Beispiel-Bots-V4 | Beispiele für das Erstellen von Aufgabenmodulen. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/54.teams-task-module)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/54.teams-task-module)|

## <a name="step-by-step-guide"></a>Schrittweise Anleitung

Befolgen Sie die schrittweise Anleitung zum Erstellen und Abrufen [des Aufgabenmodul-Bots](../../sbs-botbuilder-taskmodule.yml) in Teams.

## <a name="see-also"></a>Siehe auch

* [beispielcode für Microsoft Teams Aufgabenmodul in Node.js](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs/blob/master/src/TeamsBot.ts)
* [Bot Framework-Beispiele](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)
