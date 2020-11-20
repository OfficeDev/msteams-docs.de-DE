---
title: Verwenden von Aufgaben Modulen in Microsoft Teams-Bots
description: Vorgehensweise verwenden von Aufgaben Modulen mit Microsoft Teams-Bots, einschließlich bot-Framework-Karten, Adaptive Karten und Deep Links.
keywords: Aufgaben Module-Bots für Teams
ms.openlocfilehash: 1400fec0ef86448f8632018c7675999b6b1881a0
ms.sourcegitcommit: 64acd30eee8af5fe151e9866c13226ed3f337c72
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2020
ms.locfileid: "49346721"
---
# <a name="using-task-modules-from-microsoft-teams-bots"></a>Verwenden von Aufgaben Modulen von Microsoft Teams-Bots

Aufgaben Module können von Microsoft Teams-Bots mithilfe von Schaltflächen auf adaptiven Karten und bot-Framework-Karten (Hero, Thumbnail und Office 365-Konnektor) aufgerufen werden. Aufgaben Module sind häufig eine bessere Benutzeroberfläche als mehrere Unterhaltungs Schritte, bei denen Sie als Entwickler den Status von bot überwachen und dem Benutzer die Unterbrechung/Absage der Sequenz ermöglichen müssen.

Es gibt zwei Möglichkeiten zum Aufrufen von Aufgaben Modulen:

* **Eine neue Art von Invoke `task/fetch` -Nachricht.** Wenn Sie die Karten `invoke` [Aktion](~/task-modules-and-cards/cards/cards-actions.md#invoke) für bot-Framework-Karten verwenden oder die Karten `Action.Submit` [Aktion](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) für Adaptive Karten mit `task/fetch` , wird das Aufgabenmodul (entweder eine URL oder eine Adaptive Karte) dynamisch von Ihrem bot abgerufen.
* **Deep Link-URLs.** Mithilfe der [Deep Link-Syntax für Aufgaben Module](~/task-modules-and-cards/what-are-task-modules.md#task-module-deep-link-syntax)können Sie die Karten `openUrl` [Aktion](~/task-modules-and-cards/cards/cards-actions.md#openurl) für bot-frameworkkarten oder die `Action.OpenUrl` [Karten Aktion](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) für Adaptive Karten verwenden. Bei Deep Link-URLs ist die URL des Aufgabenmoduls oder der Adaptive Kartentext offensichtlich vorab bekannt, sodass ein Server-Roundtrip relativ zu vermieden wird `task/fetch` .

>[!IMPORTANT]
>Um die sichere Kommunikation sicherzustellen `url` , `fallbackUrl` müssen Sie das HTTPS-Verschlüsselungsprotokoll implementieren.

## <a name="invoking-a-task-module-via-taskfetch"></a>Aufrufen eines Aufgabenmoduls über Task/FETCH

Wenn das `value` Objekt der `invoke` Karte `Action.Submit` auf ordnungsgemäße Weise initialisiert wird (im folgenden näher erläutert), wird beim Drücken der Schaltfläche eine `invoke` Nachricht an den bot gesendet. In der HTTP-Antwort auf die `invoke` Nachricht gibt es ein [taskinfo-Objekt](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) , das in ein Wrapperobjekt eingebettet ist, das die Teams zum Anzeigen des Aufgabenmoduls verwenden.

![Aufgabe/Abrufanforderung/Antwort](~/assets/images/task-module/task-module-invoke-request-response.png)

Lassen Sie uns die einzelnen Schritte etwas ausführlicher betrachten:

1. In diesem Beispiel wird eine Hero-Karte für bot-Frameworks mit einer "Buy" `invoke` - [Karten Aktion](~/task-modules-and-cards/cards/cards-actions.md#invoke)gezeigt. Der Wert der `type` Eigenschaft ist `task/fetch` -der Rest des `value` Objekts kann sein, was Sie möchten.
2. Der bot erhält die `invoke` http-Post-Nachricht.
3. Der bot erstellt ein Response-Objekt und gibt es im Text der Post-Antwort mit einem HTTP 200-Antwortcode zurück. Das Schema für Antworten wird [im folgenden in der Diskussion über Aufgabe/Submit](#the-flexibility-of-tasksubmit)beschrieben, aber wichtig ist jetzt, dass der Text der HTTP-Antwort ein [taskinfo-Objekt](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) enthält, das in ein Wrapperobjekt eingebettet ist, beispielsweise:

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

    Das `task/fetch` Ereignis und seine Antwort auf Bots ähneln konzeptuell der `microsoftTeams.tasks.startTask()` Funktion im Client-SDK.
4. Microsoft Teams zeigt den Aufgabenmodul an.

## <a name="submitting-the-result-of-a-task-module"></a>Übermitteln des Ergebnisses eines Aufgabenmoduls

Wenn der Benutzer mit dem Aufgabenmodul fertig ist, ist das Senden des Ergebnisses zurück an den bot ähnlich wie [bei Registerkarten](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-submitting-the-result-of-a-task-module), es gibt jedoch einige Unterschiede, die daher auch hier beschrieben werden.

* **HTML/JavaScript ( `TaskInfo.url` )**. Nachdem Sie überprüft haben, was der Benutzer eingegeben hat, rufen Sie die `microsoftTeams.tasks.submitTask()` SDK-Funktion auf (wird im folgenden als `submitTask()` Zweck der Lesbarkeit bezeichnet). Sie können `submitTask()` ohne Parameter aufrufen, wenn Sie lediglich möchten, dass Teams den Aufgabenmodul schließen, aber in den meisten Fällen möchten Sie ein Objekt oder eine Zeichenfolge an Ihren übergeben `submitHandler` . Übergeben Sie es einfach als ersten Parameter, `result` . Teams werden aufgerufen `submitHandler` : `err` wird `null` und ist `result` das Objekt/die Zeichenfolge, die Sie an übergeben haben `submitTask()` . Wenn Sie `submitTask()` einen `result` Parameter aufrufen, **müssen** Sie ein `appId` oder ein Array von `appId` Zeichenfolgen übergeben: Dadurch können Teams überprüfen, ob die APP, die das Ergebnis sendet, dieselbe ist, die das Aufgabenmodul aufgerufen hat. Ihr bot erhält eine `task/submit` Nachricht `result` wie [unten](#payload-of-taskfetch-and-tasksubmit-messages)beschrieben.
* **Adaptive Karte ( `TaskInfo.card` )**. Der Adaptive Kartentext (wie vom Benutzer ausgefüllt) wird über eine Nachricht an den bot gesendet, `task/submit` Wenn der Benutzer eine beliebige `Action.Submit` Schaltfläche drückt.

## <a name="the-flexibility-of-tasksubmit"></a>Flexibilität von Task/Submit

Im vorherigen Abschnitt haben Sie gelernt, dass der bot immer eine Nachricht erhält, wenn der Benutzer mit einem Aufgabenmodul endet, das von einem bot aufgerufen wird `task/submit invoke` . Als Entwickler haben Sie mehrere Möglichkeiten, wenn Sie auf die Nachricht *reagieren* `task/submit` :

| HTTP-Text Antwort                      | Szenario                                |
| --------------------------------------- | --------------------------------------- |
| None (Nachricht ignorieren `task/submit` ) | Die einfachste Antwort ist überhaupt keine Antwort. Ihr bot muss nicht Antworten, wenn der Benutzer mit dem Aufgabenmodul fertig ist. |
| <pre>{<br/>  "task": {<br/>    "type": "message",<br/>    "value": "Message text"<br/>  }<br/>}</pre> | In Microsoft Teams wird der Wert `value` in einem Popupmeldungsfeld angezeigt. |
| <pre>{<br/>  "task": {<br/>    "type": "continue",<br/>    "value": &lt;TaskInfo object&gt;<br/>  }<br/>}</pre> | Ermöglicht es Ihnen, Sequenzen von adaptiven Karten in einer Assistenten-/mehrstufigen Umgebung zu "verketten". _Beachten Sie, dass das Verketten von adaptiven Karten in eine Sequenz ein erweitertes Szenario ist und hier nicht dokumentiert ist. Die Node.js-Beispiel-App unterstützt Sie jedoch und wie Sie funktioniert, ist in der [Readme.MD-Datei](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs#implementation-notes)dokumentiert._ |

## <a name="payload-of-taskfetch-and-tasksubmit-messages"></a>Nutzlast von Task/FETCH und Task/Submit-Nachrichten

Dieser Abschnitt definiert das Schema dessen, was Ihr bot erhält, wenn er ein `task/fetch` oder `task/submit` bot Framework `Activity` -Objekt empfängt. Die wichtige obere Ebene wird unten angezeigt:

| Eigenschaft | Beschreibung                          |
| -------- | ------------------------------------ |
| `type`   | Wird immer `invoke`              |
| `name`   | Entweder `task/fetch` oder `task/submit` |
| `value`  | Die vom Entwickler definierte Nutzlast. Normalerweise spiegelt die Struktur des `value` Objekts das, was von Teams gesendet wurde. In diesem Fall ist es jedoch anders, da wir Dynamic FETCH ( `task/fetch` ) sowohl von bot-Framework () als `value` auch von Adaptive Card-Aktionen () unterstützen möchten `Action.Submit` `data` , und wir benötigen eine Möglichkeit, Teams `context` mit dem bot zu kommunizieren, zusätzlich zu dem, was in enthalten war `value` / `data` .<br/><br/>Dies erfolgt durch Kombinieren der beiden Elemente in einem übergeordneten Objekt:<br/><br/><pre>{<br/>  "context": {<br/>    "theme": "default" &vert; "dark" &vert; "contrast",<br/>  },<br/>  "data": [value field from Bot Framework card] &vert; [data field from Adaptive Card] <br/>}</pre>  |

## <a name="example-receiving-and-responding-to-taskfetch-and-tasksubmit-invoke-messages---nodejs"></a>Beispiel: empfangen und reagieren auf Tasks/FETCH-und Task/Submit-Invoke-Nachrichten – Node.js

> [!NOTE]
> Der folgende Beispielcode wurde zwischen der technischen Vorschau und der endgültigen Version dieses Features geändert: das Schema der `task/fetch` Anforderung wurde geändert, um zu verfolgen, was [im vorherigen Abschnitt dokumentiert](#payload-of-taskfetch-and-tasksubmit-messages)wurde. Das heißt, die Dokumentation war richtig, aber die Implementierung war nicht. In den `// for Technical Preview [...]` Kommentaren unten finden Sie Informationen zu den geänderten Funktionen.

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

*See also*, [Microsoft Teams task module sample code — nodejs](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs/blob/master/src/TeamsBot.ts) and  [Bot Framework samples](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).
```
## <a name="example-receiving-and-responding-to-taskfetch-and-tasksubmit-invoke-messages---c"></a>Beispiel: empfangen und reagieren auf Tasks/FETCH-und Task/Submit-Invoke-Nachrichten-C #

In C#-Bots `invoke` werden Nachrichten von einem `HttpResponseMessage()` Controller verarbeitet, der eine `Activity` Nachricht verarbeitet. Die `task/fetch` `task/submit` Anforderungen und Antworten sind JSON. In C# ist es nicht so bequem, sich mit RAW-JSON wie in Node.js zu beschäftigen, daher benötigen Sie Wrapperklassen, um die Serialisierung von und zu JSON zu verarbeiten. Es gibt noch keine direkte Unterstützung dafür im Microsoft Teams [C# SDK](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) , aber Sie sehen ein Beispiel dafür, wie diese einfachen Wrapperklassen in der c#-Beispiel- [App](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Models/TaskModel.cs)aussehen würden.

Im folgenden finden Sie Beispielcode in C# zur Behandlung `task/fetch` und `task/submit` Nachrichten mit diesen Wrapperklassen ( `TaskInfo` , `TaskEnvelope` ), die aus dem [Beispiel](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs)entnommen wurden:

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
```
## <a name="example-receiving-and-responding-to-taskfetch-and-tasksubmit-invoke-messages---python"></a>Beispiel: empfangen und reagieren auf Tasks/FETCH-und Task-/Submit Invoke-Nachrichten-python
```
async def on_teams_task_module_fetch(
        self, turn_context: TurnContext, task_module_request: TaskModuleRequest
    ) -> TaskModuleResponse:
        """
        Called when the user selects an options from the displayed HeroCard or
        AdaptiveCard.  The result is the action to perform.
        """

        card_task_fetch_value = task_module_request.data["data"]

        task_info = TaskModuleTaskInfo()
        if card_task_fetch_value == TaskModuleIds.YOUTUBE:
            # Display the YouTube.html page
            task_info.url = task_info.fallback_url = (
                self.__base_url + "/" + TaskModuleIds.YOUTUBE + ".html"
            )
            TeamsTaskModuleBot.__set_task_info(task_info, TaskModuleUIConstants.YOUTUBE)
        elif card_task_fetch_value == TaskModuleIds.CUSTOM_FORM:
            # Display the CustomForm.html page, and post the form data back via
            # on_teams_task_module_submit.
            task_info.url = task_info.fallback_url = (
                self.__base_url + "/" + TaskModuleIds.CUSTOM_FORM + ".html"
            )
            TeamsTaskModuleBot.__set_task_info(
                task_info, TaskModuleUIConstants.CUSTOM_FORM
            )
        elif card_task_fetch_value == TaskModuleIds.ADAPTIVE_CARD:
            # Display an AdaptiveCard to prompt user for text, and post it back via
            # on_teams_task_module_submit.
            task_info.card = TeamsTaskModuleBot.__create_adaptive_card_attachment()
            TeamsTaskModuleBot.__set_task_info(
                task_info, TaskModuleUIConstants.ADAPTIVE_CARD
            )

        return TaskModuleResponseFactory.to_task_module_response(task_info)

    async def on_teams_task_module_submit(
        self, turn_context: TurnContext, task_module_request: TaskModuleRequest
    ) -> TaskModuleResponse:
        """
        Called when data is being returned from the selected option (see `on_teams_task_module_fetch').
        """

        # Echo the users input back.  In a production bot, this is where you'd add behavior in
        # response to the input.
        await turn_context.send_activity(
            MessageFactory.text(
                f"on_teams_task_module_submit: {json.dumps(task_module_request.data)}"
            )
        )

        message_response = TaskModuleMessageResponse(value="Thanks!")
        return TaskModuleResponse(task=message_response)

Not shown in the above example is the `SetTaskInfo()` function, which sets the `height`, `width`, and `title` properties of the `TaskInfo` object for each case. Here's the [source code for SetTaskInfo()](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs).
```
### <a name="bot-framework-card-actions-vs-adaptive-card-actionsubmit-actions"></a>Bot-Framework-Karten Aktionen vs. Adaptive Karten Aktion. Submit-Aktionen

Das Schema für Aktionen von bot-Framework-Karten unterscheidet sich geringfügig von adaptiven Karten `Action.Submit` Aktionen. Dadurch unterscheidet sich auch die Möglichkeit zum Aufrufen von Aufgaben Modulen geringfügig: das `data` Objekt in `Action.Submit` enthält ein `msteams` Objekt, sodass es nicht mit anderen Eigenschaften in der Karte in Konflikt kommt. Die folgende Tabelle zeigt ein Beispiel:

| Bot-Framework-Karten Aktion                              | Adaptive Karten Aktion. Submit-Aktion                     |
| ------------------------------------------------------ | ------------------------------------------------------ |
| <pre>{<br/>  "type": "invoke",<br/>  "title": "Buy",<br/>  "value": {<br/>    "type": "task/fetch",<br/>    &lt;...&gt;<br/>  }<br/>}</pre> | <pre>{<br/>  "type": "Action.Submit",<br/>  "id": "btnBuy",<br/>  "title": "Buy",<br/>  "data": {<br/>    &lt;...&gt;,<br/>    "msteams": {<br/>      "type": "task/fetch"<br/>    }<br/>  }<br/>}</pre>  |
