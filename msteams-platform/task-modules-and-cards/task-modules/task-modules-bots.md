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
# <a name="using-task-modules-from-microsoft-teams-bots"></a><span data-ttu-id="d78df-104">Verwenden von Aufgaben Modulen von Microsoft Teams-Bots</span><span class="sxs-lookup"><span data-stu-id="d78df-104">Using task modules from Microsoft Teams bots</span></span>

<span data-ttu-id="d78df-105">Aufgaben Module können von Microsoft Teams-Bots mithilfe von Schaltflächen auf adaptiven Karten und bot-Framework-Karten (Hero, Thumbnail und Office 365-Konnektor) aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="d78df-105">Task modules can be invoked from Microsoft Teams bots using buttons on Adaptive cards and Bot Framework cards (Hero, Thumbnail, and Office 365 Connector).</span></span> <span data-ttu-id="d78df-106">Aufgaben Module sind häufig eine bessere Benutzeroberfläche als mehrere Unterhaltungs Schritte, bei denen Sie als Entwickler den Status von bot überwachen und dem Benutzer die Unterbrechung/Absage der Sequenz ermöglichen müssen.</span><span class="sxs-lookup"><span data-stu-id="d78df-106">Task modules are often a better user experience than multiple conversation steps where you as a developer have to keep track of bot state and allow the user to interrupt/cancel the sequence.</span></span>

<span data-ttu-id="d78df-107">Es gibt zwei Möglichkeiten zum Aufrufen von Aufgaben Modulen:</span><span class="sxs-lookup"><span data-stu-id="d78df-107">There are two ways of invoking task modules:</span></span>

* <span data-ttu-id="d78df-108">**Eine neue Art von Invoke `task/fetch` -Nachricht.**</span><span class="sxs-lookup"><span data-stu-id="d78df-108">**A new kind of invoke message `task/fetch`.**</span></span> <span data-ttu-id="d78df-109">Wenn Sie die Karten `invoke` [Aktion](~/task-modules-and-cards/cards/cards-actions.md#invoke) für bot-Framework-Karten verwenden oder die Karten `Action.Submit` [Aktion](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) für Adaptive Karten mit `task/fetch` , wird das Aufgabenmodul (entweder eine URL oder eine Adaptive Karte) dynamisch von Ihrem bot abgerufen.</span><span class="sxs-lookup"><span data-stu-id="d78df-109">Using the `invoke` [card action](~/task-modules-and-cards/cards/cards-actions.md#invoke) for Bot Framework cards, or the `Action.Submit` [card action](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) for Adaptive cards, with `task/fetch`, the task module (either a URL or an Adaptive card) is fetched dynamically from your bot.</span></span>
* <span data-ttu-id="d78df-110">**Deep Link-URLs.**</span><span class="sxs-lookup"><span data-stu-id="d78df-110">**Deep link URLs.**</span></span> <span data-ttu-id="d78df-111">Mithilfe der [Deep Link-Syntax für Aufgaben Module](~/task-modules-and-cards/what-are-task-modules.md#task-module-deep-link-syntax)können Sie die Karten `openUrl` [Aktion](~/task-modules-and-cards/cards/cards-actions.md#openurl) für bot-frameworkkarten oder die `Action.OpenUrl` [Karten Aktion](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) für Adaptive Karten verwenden.</span><span class="sxs-lookup"><span data-stu-id="d78df-111">Using the [deep link syntax for task modules](~/task-modules-and-cards/what-are-task-modules.md#task-module-deep-link-syntax), you can use the `openUrl` [card action](~/task-modules-and-cards/cards/cards-actions.md#openurl) for Bot Framework cards or the `Action.OpenUrl` [card action](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) for Adaptive cards, respectively.</span></span> <span data-ttu-id="d78df-112">Bei Deep Link-URLs ist die URL des Aufgabenmoduls oder der Adaptive Kartentext offensichtlich vorab bekannt, sodass ein Server-Roundtrip relativ zu vermieden wird `task/fetch` .</span><span class="sxs-lookup"><span data-stu-id="d78df-112">With deep link URLs, the task module URL or Adaptive card body is obviously known in advance, avoiding a server round-trip relative to `task/fetch`.</span></span>

>[!IMPORTANT]
><span data-ttu-id="d78df-113">Um die sichere Kommunikation sicherzustellen `url` , `fallbackUrl` müssen Sie das HTTPS-Verschlüsselungsprotokoll implementieren.</span><span class="sxs-lookup"><span data-stu-id="d78df-113">To ensure secure communications, each `url` and `fallbackUrl` must implement the HTTPS encryption protocol.</span></span>

## <a name="invoking-a-task-module-via-taskfetch"></a><span data-ttu-id="d78df-114">Aufrufen eines Aufgabenmoduls über Task/FETCH</span><span class="sxs-lookup"><span data-stu-id="d78df-114">Invoking a task module via task/fetch</span></span>

<span data-ttu-id="d78df-115">Wenn das `value` Objekt der `invoke` Karte `Action.Submit` auf ordnungsgemäße Weise initialisiert wird (im folgenden näher erläutert), wird beim Drücken der Schaltfläche eine `invoke` Nachricht an den bot gesendet.</span><span class="sxs-lookup"><span data-stu-id="d78df-115">When the `value` object of the `invoke` card action or `Action.Submit` is initialized in the proper way (explained in more detail below), when a user presses the button an `invoke` message is sent to the bot.</span></span> <span data-ttu-id="d78df-116">In der HTTP-Antwort auf die `invoke` Nachricht gibt es ein [taskinfo-Objekt](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) , das in ein Wrapperobjekt eingebettet ist, das die Teams zum Anzeigen des Aufgabenmoduls verwenden.</span><span class="sxs-lookup"><span data-stu-id="d78df-116">In the HTTP response to the `invoke` message, there's a [TaskInfo object](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) embedded in a wrapper object, which Teams uses to display the task module.</span></span>

![Aufgabe/Abrufanforderung/Antwort](~/assets/images/task-module/task-module-invoke-request-response.png)

<span data-ttu-id="d78df-118">Lassen Sie uns die einzelnen Schritte etwas ausführlicher betrachten:</span><span class="sxs-lookup"><span data-stu-id="d78df-118">Let's look at each step in a bit more detail:</span></span>

1. <span data-ttu-id="d78df-119">In diesem Beispiel wird eine Hero-Karte für bot-Frameworks mit einer "Buy" `invoke` - [Karten Aktion](~/task-modules-and-cards/cards/cards-actions.md#invoke)gezeigt.</span><span class="sxs-lookup"><span data-stu-id="d78df-119">This example shows a Bot Framework Hero card with a "Buy" `invoke` [card action](~/task-modules-and-cards/cards/cards-actions.md#invoke).</span></span> <span data-ttu-id="d78df-120">Der Wert der `type` Eigenschaft ist `task/fetch` -der Rest des `value` Objekts kann sein, was Sie möchten.</span><span class="sxs-lookup"><span data-stu-id="d78df-120">The value of the `type` property is `task/fetch` - the rest of the `value` object can be whatever you like.</span></span>
2. <span data-ttu-id="d78df-121">Der bot erhält die `invoke` http-Post-Nachricht.</span><span class="sxs-lookup"><span data-stu-id="d78df-121">The bot receives the `invoke` HTTP POST message.</span></span>
3. <span data-ttu-id="d78df-122">Der bot erstellt ein Response-Objekt und gibt es im Text der Post-Antwort mit einem HTTP 200-Antwortcode zurück.</span><span class="sxs-lookup"><span data-stu-id="d78df-122">The bot creates a response object and returns it in the body of the POST response with an HTTP 200 response code.</span></span> <span data-ttu-id="d78df-123">Das Schema für Antworten wird [im folgenden in der Diskussion über Aufgabe/Submit](#the-flexibility-of-tasksubmit)beschrieben, aber wichtig ist jetzt, dass der Text der HTTP-Antwort ein [taskinfo-Objekt](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) enthält, das in ein Wrapperobjekt eingebettet ist, beispielsweise:</span><span class="sxs-lookup"><span data-stu-id="d78df-123">The schema for responses is described [below in the discussion on task/submit](#the-flexibility-of-tasksubmit), but the important thing to remember now is that the body of the HTTP response contains a [TaskInfo object](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) embedded in a wrapper object, e.g.:</span></span>

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

    <span data-ttu-id="d78df-124">Das `task/fetch` Ereignis und seine Antwort auf Bots ähneln konzeptuell der `microsoftTeams.tasks.startTask()` Funktion im Client-SDK.</span><span class="sxs-lookup"><span data-stu-id="d78df-124">The `task/fetch` event and its response for bots is similar, conceptually, to the `microsoftTeams.tasks.startTask()` function in the client SDK.</span></span>
4. <span data-ttu-id="d78df-125">Microsoft Teams zeigt den Aufgabenmodul an.</span><span class="sxs-lookup"><span data-stu-id="d78df-125">Microsoft Teams displays the task module.</span></span>

## <a name="submitting-the-result-of-a-task-module"></a><span data-ttu-id="d78df-126">Übermitteln des Ergebnisses eines Aufgabenmoduls</span><span class="sxs-lookup"><span data-stu-id="d78df-126">Submitting the result of a task module</span></span>

<span data-ttu-id="d78df-127">Wenn der Benutzer mit dem Aufgabenmodul fertig ist, ist das Senden des Ergebnisses zurück an den bot ähnlich wie [bei Registerkarten](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-submitting-the-result-of-a-task-module), es gibt jedoch einige Unterschiede, die daher auch hier beschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="d78df-127">When the user is finished with the task module, submitting the result back to the bot is similar [to the way it works with tabs](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-submitting-the-result-of-a-task-module), but there are a few differences, so it's described here too.</span></span>

* <span data-ttu-id="d78df-128">**HTML/JavaScript ( `TaskInfo.url` )**.</span><span class="sxs-lookup"><span data-stu-id="d78df-128">**HTML/JavaScript (`TaskInfo.url`)**.</span></span> <span data-ttu-id="d78df-129">Nachdem Sie überprüft haben, was der Benutzer eingegeben hat, rufen Sie die `microsoftTeams.tasks.submitTask()` SDK-Funktion auf (wird im folgenden als `submitTask()` Zweck der Lesbarkeit bezeichnet).</span><span class="sxs-lookup"><span data-stu-id="d78df-129">Once you've validated what the user has entered, you call the `microsoftTeams.tasks.submitTask()` SDK function (referred to hereafter as `submitTask()` for readability purposes).</span></span> <span data-ttu-id="d78df-130">Sie können `submitTask()` ohne Parameter aufrufen, wenn Sie lediglich möchten, dass Teams den Aufgabenmodul schließen, aber in den meisten Fällen möchten Sie ein Objekt oder eine Zeichenfolge an Ihren übergeben `submitHandler` .</span><span class="sxs-lookup"><span data-stu-id="d78df-130">You can call `submitTask()` without any parameters if you just want Teams to close the task module, but most of the time you'll want to pass an object or a string to your `submitHandler`.</span></span> <span data-ttu-id="d78df-131">Übergeben Sie es einfach als ersten Parameter, `result` .</span><span class="sxs-lookup"><span data-stu-id="d78df-131">Simply pass it as the first parameter, `result`.</span></span> <span data-ttu-id="d78df-132">Teams werden aufgerufen `submitHandler` : `err` wird `null` und ist `result` das Objekt/die Zeichenfolge, die Sie an übergeben haben `submitTask()` .</span><span class="sxs-lookup"><span data-stu-id="d78df-132">Teams will invoke `submitHandler`: `err` will be `null` and `result` will be the object/string you passed to `submitTask()`.</span></span> <span data-ttu-id="d78df-133">Wenn Sie `submitTask()` einen `result` Parameter aufrufen, **müssen** Sie ein `appId` oder ein Array von `appId` Zeichenfolgen übergeben: Dadurch können Teams überprüfen, ob die APP, die das Ergebnis sendet, dieselbe ist, die das Aufgabenmodul aufgerufen hat.</span><span class="sxs-lookup"><span data-stu-id="d78df-133">If you do call `submitTask()` with a `result` parameter, you **must** pass an `appId` or an array of `appId` strings: this allows Teams to validate that the app sending the result is the same one which invoked the task module.</span></span> <span data-ttu-id="d78df-134">Ihr bot erhält eine `task/submit` Nachricht `result` wie [unten](#payload-of-taskfetch-and-tasksubmit-messages)beschrieben.</span><span class="sxs-lookup"><span data-stu-id="d78df-134">Your bot will receive a `task/submit` message including `result` as described [below](#payload-of-taskfetch-and-tasksubmit-messages).</span></span>
* <span data-ttu-id="d78df-135">**Adaptive Karte ( `TaskInfo.card` )**.</span><span class="sxs-lookup"><span data-stu-id="d78df-135">**Adaptive card (`TaskInfo.card`)**.</span></span> <span data-ttu-id="d78df-136">Der Adaptive Kartentext (wie vom Benutzer ausgefüllt) wird über eine Nachricht an den bot gesendet, `task/submit` Wenn der Benutzer eine beliebige `Action.Submit` Schaltfläche drückt.</span><span class="sxs-lookup"><span data-stu-id="d78df-136">The Adaptive card body (as filled in by the user) will be sent to the bot via a `task/submit` message when the user presses any `Action.Submit` button.</span></span>

## <a name="the-flexibility-of-tasksubmit"></a><span data-ttu-id="d78df-137">Flexibilität von Task/Submit</span><span class="sxs-lookup"><span data-stu-id="d78df-137">The flexibility of task/submit</span></span>

<span data-ttu-id="d78df-138">Im vorherigen Abschnitt haben Sie gelernt, dass der bot immer eine Nachricht erhält, wenn der Benutzer mit einem Aufgabenmodul endet, das von einem bot aufgerufen wird `task/submit invoke` .</span><span class="sxs-lookup"><span data-stu-id="d78df-138">In the previous section, you learned that when the user finishes with a task module invoked from a bot, the bot always receives a `task/submit invoke` message.</span></span> <span data-ttu-id="d78df-139">Als Entwickler haben Sie mehrere Möglichkeiten, wenn Sie auf die Nachricht *reagieren* `task/submit` :</span><span class="sxs-lookup"><span data-stu-id="d78df-139">As a developer, you have several options when *responding* to the `task/submit` message:</span></span>

| <span data-ttu-id="d78df-140">HTTP-Text Antwort</span><span class="sxs-lookup"><span data-stu-id="d78df-140">HTTP Body Response</span></span>                      | <span data-ttu-id="d78df-141">Szenario</span><span class="sxs-lookup"><span data-stu-id="d78df-141">Scenario</span></span>                                |
| --------------------------------------- | --------------------------------------- |
| <span data-ttu-id="d78df-142">None (Nachricht ignorieren `task/submit` )</span><span class="sxs-lookup"><span data-stu-id="d78df-142">None (ignore the `task/submit` message)</span></span> | <span data-ttu-id="d78df-143">Die einfachste Antwort ist überhaupt keine Antwort.</span><span class="sxs-lookup"><span data-stu-id="d78df-143">The simplest response is no response at all.</span></span> <span data-ttu-id="d78df-144">Ihr bot muss nicht Antworten, wenn der Benutzer mit dem Aufgabenmodul fertig ist.</span><span class="sxs-lookup"><span data-stu-id="d78df-144">Your bot is not required to respond when the user is finished with the task module.</span></span> |
| <pre>{<br/>  "task": {<br/>    "type": "message",<br/>    "value": "Message text"<br/>  }<br/>}</pre> | <span data-ttu-id="d78df-145">In Microsoft Teams wird der Wert `value` in einem Popupmeldungsfeld angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d78df-145">Teams will display the value of `value` in a popup message box.</span></span> |
| <pre>{<br/>  "task": {<br/>    "type": "continue",<br/>    "value": &lt;TaskInfo object&gt;<br/>  }<br/>}</pre> | <span data-ttu-id="d78df-146">Ermöglicht es Ihnen, Sequenzen von adaptiven Karten in einer Assistenten-/mehrstufigen Umgebung zu "verketten".</span><span class="sxs-lookup"><span data-stu-id="d78df-146">Allows you to "chain" sequences of Adaptive cards together in a wizard/multi-step experience.</span></span> <span data-ttu-id="d78df-147">_Beachten Sie, dass das Verketten von adaptiven Karten in eine Sequenz ein erweitertes Szenario ist und hier nicht dokumentiert ist. Die Node.js-Beispiel-App unterstützt Sie jedoch und wie Sie funktioniert, ist in der [Readme.MD-Datei](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs#implementation-notes)dokumentiert._</span><span class="sxs-lookup"><span data-stu-id="d78df-147">_Note that chaining Adaptive cards into a sequence is an advanced scenario and not documented here. The Node.js sample app supports it, however, and how it works is documented in [its README.md file](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs#implementation-notes)._</span></span> |

## <a name="payload-of-taskfetch-and-tasksubmit-messages"></a><span data-ttu-id="d78df-148">Nutzlast von Task/FETCH und Task/Submit-Nachrichten</span><span class="sxs-lookup"><span data-stu-id="d78df-148">Payload of task/fetch and task/submit messages</span></span>

<span data-ttu-id="d78df-149">Dieser Abschnitt definiert das Schema dessen, was Ihr bot erhält, wenn er ein `task/fetch` oder `task/submit` bot Framework `Activity` -Objekt empfängt.</span><span class="sxs-lookup"><span data-stu-id="d78df-149">This section defines the schema of what your bot receives when it receives a `task/fetch` or `task/submit` Bot Framework `Activity` object.</span></span> <span data-ttu-id="d78df-150">Die wichtige obere Ebene wird unten angezeigt:</span><span class="sxs-lookup"><span data-stu-id="d78df-150">The important top-level appear below:</span></span>

| <span data-ttu-id="d78df-151">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="d78df-151">Property</span></span> | <span data-ttu-id="d78df-152">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d78df-152">Description</span></span>                          |
| -------- | ------------------------------------ |
| `type`   | <span data-ttu-id="d78df-153">Wird immer `invoke`</span><span class="sxs-lookup"><span data-stu-id="d78df-153">Will always be `invoke`</span></span>              |
| `name`   | <span data-ttu-id="d78df-154">Entweder `task/fetch` oder `task/submit`</span><span class="sxs-lookup"><span data-stu-id="d78df-154">Either `task/fetch` or `task/submit`</span></span> |
| `value`  | <span data-ttu-id="d78df-155">Die vom Entwickler definierte Nutzlast.</span><span class="sxs-lookup"><span data-stu-id="d78df-155">The developer-defined payload.</span></span> <span data-ttu-id="d78df-156">Normalerweise spiegelt die Struktur des `value` Objekts das, was von Teams gesendet wurde.</span><span class="sxs-lookup"><span data-stu-id="d78df-156">Normally the structure of the `value` object mirrors what was sent from Teams.</span></span> <span data-ttu-id="d78df-157">In diesem Fall ist es jedoch anders, da wir Dynamic FETCH ( `task/fetch` ) sowohl von bot-Framework () als `value` auch von Adaptive Card-Aktionen () unterstützen möchten `Action.Submit` `data` , und wir benötigen eine Möglichkeit, Teams `context` mit dem bot zu kommunizieren, zusätzlich zu dem, was in enthalten war `value` / `data` .</span><span class="sxs-lookup"><span data-stu-id="d78df-157">In this case, however, it's different because we want to support dynamic fetch (`task/fetch`) from both Bot Framework (`value`) and Adaptive card `Action.Submit` actions (`data`), and we need a way to communicate Teams `context` to the bot in addition to what was included in `value`/`data`.</span></span><br/><br/><span data-ttu-id="d78df-158">Dies erfolgt durch Kombinieren der beiden Elemente in einem übergeordneten Objekt:</span><span class="sxs-lookup"><span data-stu-id="d78df-158">We do this by combining the two into a parent object:</span></span><br/><br/><pre>{<br/>  "context": {<br/>    "theme": "default" &vert; "dark" &vert; "contrast",<br/>  },<br/>  "data": [value field from Bot Framework card] &vert; [data field from Adaptive Card] <br/>}</pre>  |

## <a name="example-receiving-and-responding-to-taskfetch-and-tasksubmit-invoke-messages---nodejs"></a><span data-ttu-id="d78df-159">Beispiel: empfangen und reagieren auf Tasks/FETCH-und Task/Submit-Invoke-Nachrichten – Node.js</span><span class="sxs-lookup"><span data-stu-id="d78df-159">Example: Receiving and responding to task/fetch and task/submit invoke messages - Node.js</span></span>

> [!NOTE]
> <span data-ttu-id="d78df-160">Der folgende Beispielcode wurde zwischen der technischen Vorschau und der endgültigen Version dieses Features geändert: das Schema der `task/fetch` Anforderung wurde geändert, um zu verfolgen, was [im vorherigen Abschnitt dokumentiert](#payload-of-taskfetch-and-tasksubmit-messages)wurde.</span><span class="sxs-lookup"><span data-stu-id="d78df-160">The sample code below was modified between Technical Preview and final release of this feature: the schema of the `task/fetch` request changed to follow what was [documented in the previous section](#payload-of-taskfetch-and-tasksubmit-messages).</span></span> <span data-ttu-id="d78df-161">Das heißt, die Dokumentation war richtig, aber die Implementierung war nicht.</span><span class="sxs-lookup"><span data-stu-id="d78df-161">That is, the documentation was correct but the implementation was not.</span></span> <span data-ttu-id="d78df-162">In den `// for Technical Preview [...]` Kommentaren unten finden Sie Informationen zu den geänderten Funktionen.</span><span class="sxs-lookup"><span data-stu-id="d78df-162">See the `// for Technical Preview [...]` comments below for what changed.</span></span>

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
## <a name="example-receiving-and-responding-to-taskfetch-and-tasksubmit-invoke-messages---c"></a><span data-ttu-id="d78df-163">Beispiel: empfangen und reagieren auf Tasks/FETCH-und Task/Submit-Invoke-Nachrichten-C #</span><span class="sxs-lookup"><span data-stu-id="d78df-163">Example: Receiving and responding to task/fetch and task/submit invoke messages - C#</span></span>

<span data-ttu-id="d78df-164">In C#-Bots `invoke` werden Nachrichten von einem `HttpResponseMessage()` Controller verarbeitet, der eine `Activity` Nachricht verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="d78df-164">In C# bots, `invoke` messages are processed by an `HttpResponseMessage()` controller processing an `Activity` message.</span></span> <span data-ttu-id="d78df-165">Die `task/fetch` `task/submit` Anforderungen und Antworten sind JSON.</span><span class="sxs-lookup"><span data-stu-id="d78df-165">The `task/fetch` and `task/submit` requests and responses are JSON.</span></span> <span data-ttu-id="d78df-166">In C# ist es nicht so bequem, sich mit RAW-JSON wie in Node.js zu beschäftigen, daher benötigen Sie Wrapperklassen, um die Serialisierung von und zu JSON zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="d78df-166">In C#, it's not as convenient to deal with raw JSON as it is in Node.js, so you need wrapper classes to handle the serialization to and from JSON.</span></span> <span data-ttu-id="d78df-167">Es gibt noch keine direkte Unterstützung dafür im Microsoft Teams [C# SDK](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) , aber Sie sehen ein Beispiel dafür, wie diese einfachen Wrapperklassen in der c#-Beispiel- [App](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Models/TaskModel.cs)aussehen würden.</span><span class="sxs-lookup"><span data-stu-id="d78df-167">There's no direct support for this in the Microsoft Teams [C# SDK](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) yet, but you can see an example of what these simple wrapper classes would look like in the [C# sample app](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Models/TaskModel.cs).</span></span>

<span data-ttu-id="d78df-168">Im folgenden finden Sie Beispielcode in C# zur Behandlung `task/fetch` und `task/submit` Nachrichten mit diesen Wrapperklassen ( `TaskInfo` , `TaskEnvelope` ), die aus dem [Beispiel](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs)entnommen wurden:</span><span class="sxs-lookup"><span data-stu-id="d78df-168">Below is example code in C# for handling `task/fetch` and `task/submit` messages using these wrapper classes (`TaskInfo`, `TaskEnvelope`), excerpted from the [sample](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs):</span></span>

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
## <a name="example-receiving-and-responding-to-taskfetch-and-tasksubmit-invoke-messages---python"></a><span data-ttu-id="d78df-169">Beispiel: empfangen und reagieren auf Tasks/FETCH-und Task-/Submit Invoke-Nachrichten-python</span><span class="sxs-lookup"><span data-stu-id="d78df-169">Example: Receiving and responding to task/fetch and task/submit invoke messages - Python</span></span>
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
### <a name="bot-framework-card-actions-vs-adaptive-card-actionsubmit-actions"></a><span data-ttu-id="d78df-170">Bot-Framework-Karten Aktionen vs. Adaptive Karten Aktion. Submit-Aktionen</span><span class="sxs-lookup"><span data-stu-id="d78df-170">Bot Framework card actions vs. Adaptive card Action.Submit actions</span></span>

<span data-ttu-id="d78df-171">Das Schema für Aktionen von bot-Framework-Karten unterscheidet sich geringfügig von adaptiven Karten `Action.Submit` Aktionen.</span><span class="sxs-lookup"><span data-stu-id="d78df-171">The schema for Bot Framework card actions is slightly different from Adaptive card `Action.Submit` actions.</span></span> <span data-ttu-id="d78df-172">Dadurch unterscheidet sich auch die Möglichkeit zum Aufrufen von Aufgaben Modulen geringfügig: das `data` Objekt in `Action.Submit` enthält ein `msteams` Objekt, sodass es nicht mit anderen Eigenschaften in der Karte in Konflikt kommt.</span><span class="sxs-lookup"><span data-stu-id="d78df-172">As a result, the way to invoke task modules is slightly different too: the `data` object in `Action.Submit` contains an `msteams` object so it won't interfere with other properties in the card.</span></span> <span data-ttu-id="d78df-173">Die folgende Tabelle zeigt ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="d78df-173">The following table shows an example of each:</span></span>

| <span data-ttu-id="d78df-174">Bot-Framework-Karten Aktion</span><span class="sxs-lookup"><span data-stu-id="d78df-174">Bot Framework card action</span></span>                              | <span data-ttu-id="d78df-175">Adaptive Karten Aktion. Submit-Aktion</span><span class="sxs-lookup"><span data-stu-id="d78df-175">Adaptive card Action.Submit action</span></span>                     |
| ------------------------------------------------------ | ------------------------------------------------------ |
| <pre>{<br/>  "type": "invoke",<br/>  "title": "Buy",<br/>  "value": {<br/>    "type": "task/fetch",<br/>    &lt;...&gt;<br/>  }<br/>}</pre> | <pre>{<br/>  "type": "Action.Submit",<br/>  "id": "btnBuy",<br/>  "title": "Buy",<br/>  "data": {<br/>    &lt;...&gt;,<br/>    "msteams": {<br/>      "type": "task/fetch"<br/>    }<br/>  }<br/>}</pre>  |
