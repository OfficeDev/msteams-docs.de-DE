---
title: Verwenden von Aufgabenmodulen in Microsoft Teams Bots
description: Verwenden von Aufgabenmodulen mit Microsoft Teams Bots, einschließlich Bot Framework-Karten, adaptiven Karten und Deep-Links.
localization_priority: Normal
ms.topic: how-to
keywords: Taskmodule Teams-Bots
ms.openlocfilehash: 5d9aa2b651a4c99cee75aada62a4d1176a589d79
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140307"
---
# <a name="use-task-modules-from-bots"></a><span data-ttu-id="84889-104">Verwenden von Aufgabenmodulen von Bots</span><span class="sxs-lookup"><span data-stu-id="84889-104">Use task modules from bots</span></span>

<span data-ttu-id="84889-105">Aufgabenmodule können von Microsoft Teams Bots mithilfe von Schaltflächen auf adaptiven Karten und Bot Framework-Karten aufgerufen werden, die Hero, Miniaturansicht und Office 365 Connector sind.</span><span class="sxs-lookup"><span data-stu-id="84889-105">Task modules can be invoked from Microsoft Teams bots using buttons on Adaptive Cards and Bot Framework cards that is hero, thumbnail, and Office 365 Connector.</span></span> <span data-ttu-id="84889-106">Aufgabenmodule sind häufig eine bessere Benutzererfahrung als mehrere Unterhaltungsschritte.</span><span class="sxs-lookup"><span data-stu-id="84889-106">Task modules are often a better user experience than multiple conversation steps.</span></span> <span data-ttu-id="84889-107">Verfolgen Sie den Botstatus, und erlauben Sie dem Benutzer, die Sequenz zu unterbrechen oder abzubrechen.</span><span class="sxs-lookup"><span data-stu-id="84889-107">Keep track of bot state and allow the user to interrupt or cancel the sequence.</span></span>

<span data-ttu-id="84889-108">Es gibt zwei Möglichkeiten zum Aufrufen von Aufgabenmodulen:</span><span class="sxs-lookup"><span data-stu-id="84889-108">There are two ways of invoking task modules:</span></span>

* <span data-ttu-id="84889-109">Eine neue Art von `task/fetch` Aufrufnachricht: Die Verwendung der `invoke` [Kartenaktion](~/task-modules-and-cards/cards/cards-actions.md#action-type-invoke) für Bot Framework-Karten oder der `Action.Submit` [Kartenaktion](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) für adaptive Karten mit dem `task/fetch` Aufgabenmodul einer URL oder einer adaptiven Karte wird dynamisch von Ihrem Bot abgerufen.</span><span class="sxs-lookup"><span data-stu-id="84889-109">A new kind of invoke message `task/fetch`: Using the `invoke` [card action](~/task-modules-and-cards/cards/cards-actions.md#action-type-invoke) for Bot Framework cards, or the `Action.Submit` [card action](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) for Adaptive cards, with `task/fetch`, task module either a URL or an Adaptive Card, is fetched dynamically from your bot.</span></span>
* <span data-ttu-id="84889-110">Deep-Link-URLs: Mithilfe der [Deep Link-Syntax für Aufgabenmodule](~/task-modules-and-cards/task-modules/invoking-task-modules.md#task-module-deep-link-syntax)können Sie die `openUrl` [Kartenaktion](~/task-modules-and-cards/cards/cards-actions.md#action-type-openurl) für Bot Framework-Karten bzw. die `Action.OpenUrl` [Kartenaktion](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) für adaptive Karten verwenden.</span><span class="sxs-lookup"><span data-stu-id="84889-110">Deep link URLs: Using the [deep link syntax for task modules](~/task-modules-and-cards/task-modules/invoking-task-modules.md#task-module-deep-link-syntax), you can use the `openUrl` [card action](~/task-modules-and-cards/cards/cards-actions.md#action-type-openurl) for Bot Framework cards or the `Action.OpenUrl` [card action](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) for Adaptive Cards, respectively.</span></span> <span data-ttu-id="84889-111">Bei Deep-Link-URLs ist die URL des Aufgabenmoduls oder der Textkörper für adaptive Karten bereits bekannt, um einen Server-Roundtrip relativ zu zu `task/fetch` vermeiden.</span><span class="sxs-lookup"><span data-stu-id="84889-111">With deep link URLs, the task module URL or Adaptive Card body is already known to avoid a server round-trip relative to `task/fetch`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="84889-112">Jedes `url` muss `fallbackUrl` das HTTPS-Verschlüsselungsprotokoll implementieren.</span><span class="sxs-lookup"><span data-stu-id="84889-112">Each `url` and `fallbackUrl` must implement the HTTPS encryption protocol.</span></span>

<span data-ttu-id="84889-113">Der nächste Abschnitt enthält Details zum Aufrufen eines Aufgabenmoduls mit `task/fetch` .</span><span class="sxs-lookup"><span data-stu-id="84889-113">The next section provides details on invoking a task module using `task/fetch`.</span></span>

## <a name="invoke-a-task-module-using-taskfetch"></a><span data-ttu-id="84889-114">Aufrufen eines Aufgabenmoduls mithilfe von "task/fetch"</span><span class="sxs-lookup"><span data-stu-id="84889-114">Invoke a task module using task/fetch</span></span>

<span data-ttu-id="84889-115">Wenn das `value` Objekt der `invoke` Kartenaktion `Action.Submit` initialisiert oder initialisiert wird und ein Benutzer die Schaltfläche auswählt, wird eine `invoke` Nachricht an den Bot gesendet.</span><span class="sxs-lookup"><span data-stu-id="84889-115">When the `value` object of the `invoke` card action or `Action.Submit` is initialized and when a user selects the button, an `invoke` message is sent to the bot.</span></span> <span data-ttu-id="84889-116">In der HTTP-Antwort auf die `invoke` Nachricht ist ein [TaskInfo-Objekt](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object) in ein Wrapperobjekt eingebettet, das Teams zum Anzeigen des Aufgabenmoduls verwendet.</span><span class="sxs-lookup"><span data-stu-id="84889-116">In the HTTP response to the `invoke` message, there is a [TaskInfo object](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object) embedded in a wrapper object, which Teams uses to display the task module.</span></span>

![Task-/Fetch-Anforderung oder -Antwort](~/assets/images/task-module/task-module-invoke-request-response.png)

<span data-ttu-id="84889-118">Die folgenden Schritte stellen das Aufgabenmodul "Aufrufen" mithilfe von "task/fetch" bereit:</span><span class="sxs-lookup"><span data-stu-id="84889-118">The following steps provides the invoke task module using task/fetch:</span></span>

1. <span data-ttu-id="84889-119">Diese Abbildung zeigt eine Bot Framework-Hero-Karte mit einer **Aktion** `invoke` ["Karte kaufen".](~/task-modules-and-cards/cards/cards-actions.md#action-type-invoke)</span><span class="sxs-lookup"><span data-stu-id="84889-119">This image shows a Bot Framework hero card with a **Buy** `invoke` [card action](~/task-modules-and-cards/cards/cards-actions.md#action-type-invoke).</span></span> <span data-ttu-id="84889-120">Der Wert der `type` Eigenschaft `task/fetch` ist, und der Rest des `value` Objekts kann Von Ihrer Wahl sein.</span><span class="sxs-lookup"><span data-stu-id="84889-120">The value of the `type` property is `task/fetch` and the rest of the `value` object can be of your choice.</span></span>
1. <span data-ttu-id="84889-121">Der Bot empfängt die `invoke` HTTP POST-Nachricht.</span><span class="sxs-lookup"><span data-stu-id="84889-121">The bot receives the `invoke` HTTP POST message.</span></span>
1. <span data-ttu-id="84889-122">Der Bot erstellt ein Antwortobjekt und gibt es im Textkörper der POST-Antwort mit einem HTTP 200-Antwortcode zurück.</span><span class="sxs-lookup"><span data-stu-id="84889-122">The bot creates a response object and returns it in the body of the POST response with an HTTP 200 response code.</span></span> <span data-ttu-id="84889-123">Weitere Informationen zum Schema für Antworten finden Sie [in der Erläuterung zum Thema "Aufgabe/Absenden".](#the-flexibility-of-tasksubmit)</span><span class="sxs-lookup"><span data-stu-id="84889-123">For more information on schema for responses, see [the discussion on task/submit](#the-flexibility-of-tasksubmit).</span></span> <span data-ttu-id="84889-124">Der folgende Code enthält ein Beispiel für den Textkörper der HTTP-Antwort, die ein in ein Wrapperobjekt eingebettetes [TaskInfo-Objekt](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object) enthält:</span><span class="sxs-lookup"><span data-stu-id="84889-124">The following code provides an example of body of the HTTP response that contains a [TaskInfo object](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object) embedded in a wrapper object:</span></span>

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

    <span data-ttu-id="84889-125">Das `task/fetch` Ereignis und seine Antwort für Bots ähneln der Funktion im `microsoftTeams.tasks.startTask()` Client-SDK.</span><span class="sxs-lookup"><span data-stu-id="84889-125">The `task/fetch` event and its response for bots is similar to the `microsoftTeams.tasks.startTask()` function in the client SDK.</span></span>

1. <span data-ttu-id="84889-126">Microsoft Teams zeigt das Aufgabenmodul an.</span><span class="sxs-lookup"><span data-stu-id="84889-126">Microsoft Teams displays the task module.</span></span>

<span data-ttu-id="84889-127">Der nächste Abschnitt enthält Details zum Übermitteln des Ergebnisses eines Aufgabenmoduls.</span><span class="sxs-lookup"><span data-stu-id="84889-127">The next section provides details on submitting the result of a task module.</span></span>

## <a name="submit-the-result-of-a-task-module"></a><span data-ttu-id="84889-128">Übermitteln des Ergebnisses eines Aufgabenmoduls</span><span class="sxs-lookup"><span data-stu-id="84889-128">Submit the result of a task module</span></span>

<span data-ttu-id="84889-129">Wenn der Benutzer mit dem Aufgabenmodul fertig ist, ähnelt das Senden des Ergebnisses an den Bot der Funktionsweise mit Registerkarten.</span><span class="sxs-lookup"><span data-stu-id="84889-129">When the user is finished with the task module, submitting the result back to the bot is similar to the way it works with tabs.</span></span> <span data-ttu-id="84889-130">Weitere Informationen finden Sie im [Beispiel zum Übermitteln des Ergebnisses eines Aufgabenmoduls.](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-of-submitting-the-result-of-a-task-module)</span><span class="sxs-lookup"><span data-stu-id="84889-130">For more information, see [example of submitting the result of a task module](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-of-submitting-the-result-of-a-task-module).</span></span> <span data-ttu-id="84889-131">Es gibt einige Unterschiede:</span><span class="sxs-lookup"><span data-stu-id="84889-131">There are a few differences as follows:</span></span>

* <span data-ttu-id="84889-132">HTML oder JavaScript, d. `TaskInfo.url` h.: Nachdem Sie überprüft haben, was der Benutzer eingegeben hat, rufen Sie die SDK-Funktion auf, `microsoftTeams.tasks.submitTask()` die nachfolgend als aus `submitTask()` Lesbarkeitsgründen bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="84889-132">HTML or JavaScript that is `TaskInfo.url`: Once you have validated what the user has entered, you call the `microsoftTeams.tasks.submitTask()` SDK function referred to hereafter as `submitTask()` for readability purposes.</span></span> <span data-ttu-id="84889-133">Sie können `submitTask()` ohne Parameter aufrufen, wenn Teams das Aufgabenmodul schließen möchten, Aber Sie müssen ein Objekt oder eine Zeichenfolge an Ihre `submitHandler` übergeben.</span><span class="sxs-lookup"><span data-stu-id="84889-133">You can call `submitTask()` without any parameters if you want Teams to close the task module, but you must pass an object or a string to your `submitHandler`.</span></span> <span data-ttu-id="84889-134">Übergeben Sie ihn als ersten Parameter, `result` .</span><span class="sxs-lookup"><span data-stu-id="84889-134">Pass it as the first parameter, `result`.</span></span> <span data-ttu-id="84889-135">Teams aufruft, `submitHandler` `err` ist `null` und `result` ist das Objekt oder die Zeichenfolge, an die Sie übergeben `submitTask()` haben.</span><span class="sxs-lookup"><span data-stu-id="84889-135">Teams invokes `submitHandler`, `err` is `null`, and `result` is the object or string you passed to `submitTask()`.</span></span> <span data-ttu-id="84889-136">Wenn Sie `submitTask()` mit einem Parameter `result` aufrufen, müssen Sie ein oder ein Array von `appId` `appId` Zeichenfolgen übergeben.</span><span class="sxs-lookup"><span data-stu-id="84889-136">If you call `submitTask()` with a `result` parameter, you must pass an `appId` or an array of `appId` strings.</span></span> <span data-ttu-id="84889-137">Dadurch können Teams überprüfen, ob die App, die das Ergebnis sendet, dieselbe ist, die das Aufgabenmodul aufgerufen hat.</span><span class="sxs-lookup"><span data-stu-id="84889-137">This allows Teams to validate that the app sending the result is the same one which invoked the task module.</span></span> <span data-ttu-id="84889-138">Ihr Bot empfängt eine `task/submit` Nachricht einschließlich `result` .</span><span class="sxs-lookup"><span data-stu-id="84889-138">Your bot receives a `task/submit` message including `result`.</span></span> <span data-ttu-id="84889-139">Weitere Informationen finden Sie unter [Nutzlast `task/fetch` und `task/submit` Nachrichten.](#payload-of-taskfetch-and-tasksubmit-messages)</span><span class="sxs-lookup"><span data-stu-id="84889-139">For more information, see [payload of `task/fetch` and `task/submit` messages](#payload-of-taskfetch-and-tasksubmit-messages).</span></span>
* <span data-ttu-id="84889-140">Adaptive Karte, d. `TaskInfo.card` h.: Der vom Benutzer ausgefüllte Textkörper der adaptiven Karte wird über eine Nachricht an den Bot `task/submit` gesendet, wenn der Benutzer eine beliebige Schaltfläche auswählt. `Action.Submit`</span><span class="sxs-lookup"><span data-stu-id="84889-140">Adaptive Card that is `TaskInfo.card`: The Adaptive Card body as filled in by the user is sent to the bot through a `task/submit` message when the user selects any `Action.Submit` button.</span></span>

<span data-ttu-id="84889-141">Der nächste Abschnitt enthält Details zur Flexibilität von `task/submit` .</span><span class="sxs-lookup"><span data-stu-id="84889-141">The next section provides details on the flexibility of `task/submit`.</span></span>

## <a name="the-flexibility-of-tasksubmit"></a><span data-ttu-id="84889-142">Die Flexibilität von Aufgabe/Übermittlung</span><span class="sxs-lookup"><span data-stu-id="84889-142">The flexibility of task/submit</span></span>

<span data-ttu-id="84889-143">Wenn der Benutzer mit einem Aufgabenmodul fertig ist, das von einem Bot aufgerufen wird, erhält der Bot immer eine `task/submit invoke` Nachricht.</span><span class="sxs-lookup"><span data-stu-id="84889-143">When the user finishes with a task module invoked from a bot, the bot always receives a `task/submit invoke` message.</span></span> <span data-ttu-id="84889-144">Sie haben mehrere Optionen, wenn Sie auf die `task/submit` Nachricht wie folgt reagieren:</span><span class="sxs-lookup"><span data-stu-id="84889-144">You have several options when responding to the `task/submit` message as follows:</span></span>

| <span data-ttu-id="84889-145">HTTP-Textkörperantwort</span><span class="sxs-lookup"><span data-stu-id="84889-145">HTTP body response</span></span>                      | <span data-ttu-id="84889-146">Szenario</span><span class="sxs-lookup"><span data-stu-id="84889-146">Scenario</span></span>                                |
| --------------------------------------- | --------------------------------------- |
| <span data-ttu-id="84889-147">Keine ignoriert die `task/submit` Nachricht</span><span class="sxs-lookup"><span data-stu-id="84889-147">None ignore the `task/submit` message</span></span> | <span data-ttu-id="84889-148">Die einfachste Antwort ist überhaupt keine Antwort.</span><span class="sxs-lookup"><span data-stu-id="84889-148">The simplest response is no response at all.</span></span> <span data-ttu-id="84889-149">Ihr Bot muss nicht antworten, wenn der Benutzer mit dem Aufgabenmodul fertig ist.</span><span class="sxs-lookup"><span data-stu-id="84889-149">Your bot is not required to respond when the user is finished with the task module.</span></span> |
| <pre>{<br/>  "task": {<br/>    "type": "message",<br/>    "value": "Message text"<br/>  }<br/>}</pre> | <span data-ttu-id="84889-150">Teams zeigt den Wert `value` in einem Popup-Meldungsfeld an.</span><span class="sxs-lookup"><span data-stu-id="84889-150">Teams displays the value of `value` in a pop-up message box.</span></span> |
| <pre>{<br/>  "task": {<br/>    "type": "continue",<br/>    "value": &lt;TaskInfo object&gt;<br/>  }<br/>}</pre> | <span data-ttu-id="84889-151">Ermöglicht ihnen das Verketten von Sequenzen adaptiver Karten in einem Assistenten oder einer mehrstufigen Oberfläche.</span><span class="sxs-lookup"><span data-stu-id="84889-151">Allows you to chain sequences of Adaptive Cards together in a wizard or multi-step experience.</span></span> |

> [!NOTE]
> <span data-ttu-id="84889-152">Das Verketten adaptiver Karten in einer Sequenz ist ein erweitertes Szenario.</span><span class="sxs-lookup"><span data-stu-id="84889-152">Chaining Adaptive Cards into a sequence is an advanced scenario.</span></span> <span data-ttu-id="84889-153">Die Node.js-Beispiel-App unterstützt sie.</span><span class="sxs-lookup"><span data-stu-id="84889-153">The Node.js sample app supports it.</span></span> <span data-ttu-id="84889-154">Weitere Informationen finden Sie unter [Microsoft Teams Aufgabenmodul Node.js. ](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs#implementation-notes)</span><span class="sxs-lookup"><span data-stu-id="84889-154">For more information, see [Microsoft Teams task module Node.js](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs#implementation-notes).</span></span>

<span data-ttu-id="84889-155">Der nächste Abschnitt enthält Details zur Nutzlast `task/fetch` und `task/submit` zu Nachrichten.</span><span class="sxs-lookup"><span data-stu-id="84889-155">The next section provides details on payload of `task/fetch` and `task/submit` messages.</span></span>

## <a name="payload-of-taskfetch-and-tasksubmit-messages"></a><span data-ttu-id="84889-156">Nutzlast von Aufgaben-/Abruf- und Aufgaben-/Sendenachrichten</span><span class="sxs-lookup"><span data-stu-id="84889-156">Payload of task/fetch and task/submit messages</span></span>

<span data-ttu-id="84889-157">In diesem Abschnitt wird das Schema definiert, was Ihr Bot empfängt, wenn er ein `task/fetch` `task/submit` Bot Framework-Objekt `Activity` empfängt.</span><span class="sxs-lookup"><span data-stu-id="84889-157">This section defines the schema of what your bot receives when it receives a `task/fetch` or `task/submit` Bot Framework `Activity` object.</span></span> <span data-ttu-id="84889-158">Die folgende Tabelle enthält die Eigenschaften der Nutzlast und der `task/fetch` `task/submit` Nachrichten:</span><span class="sxs-lookup"><span data-stu-id="84889-158">The following table provides the properties of payload of `task/fetch` and `task/submit` messages:</span></span>

| <span data-ttu-id="84889-159">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="84889-159">Property</span></span> | <span data-ttu-id="84889-160">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="84889-160">Description</span></span>                          |
| -------- | ------------------------------------ |
| `type`   | <span data-ttu-id="84889-161">Ist immer `invoke` .</span><span class="sxs-lookup"><span data-stu-id="84889-161">Is always `invoke`.</span></span>           |
| `name`   | <span data-ttu-id="84889-162">Ist entweder `task/fetch` oder `task/submit` .</span><span class="sxs-lookup"><span data-stu-id="84889-162">Is either `task/fetch` or `task/submit`.</span></span> |
| `value`  | <span data-ttu-id="84889-163">Ist die vom Entwickler definierte Nutzlast.</span><span class="sxs-lookup"><span data-stu-id="84889-163">Is the developer-defined payload.</span></span> <span data-ttu-id="84889-164">Die Struktur des `value` Objekts entspricht dem, was von Teams gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="84889-164">The structure of the `value` object is the same as what is sent from Teams.</span></span> <span data-ttu-id="84889-165">In diesem Fall ist dies jedoch anders.</span><span class="sxs-lookup"><span data-stu-id="84889-165">In this case, however, it is different.</span></span> <span data-ttu-id="84889-166">Es erfordert Unterstützung für das dynamische Abrufen, das `task/fetch` sowohl vom Bot-Framework stammt, als auch von `value` `Action.Submit` adaptiven Kartenaktionen, also `data` .</span><span class="sxs-lookup"><span data-stu-id="84889-166">It requires support for dynamic fetch that is `task/fetch` from both Bot Framework, which is `value` and Adaptive Card `Action.Submit` actions, which is `data`.</span></span> <span data-ttu-id="84889-167">Eine Möglichkeit, Teams `context` an den Bot zu kommunizieren, ist zusätzlich zu dem, was in oder enthalten ist, `value` `data` erforderlich.</span><span class="sxs-lookup"><span data-stu-id="84889-167">A way to communicate Teams `context` to the bot is required in addition to what is included in `value` or `data`.</span></span><br/><br/><span data-ttu-id="84889-168">Kombinieren Sie "Wert" und "Daten" in einem übergeordneten Objekt:</span><span class="sxs-lookup"><span data-stu-id="84889-168">Combine 'value' and 'data' into a parent object:</span></span><br/><br/><pre>{<br/>  "context": {<br/>    "theme": "default" &vert; "dark" &vert; "contrast",<br/>  },<br/>  "data": [value field from Bot Framework card] &vert; [data field from Adaptive Card] <br/>}</pre>  |

<span data-ttu-id="84889-169">Der nächste Abschnitt enthält ein Beispiel für das Empfangen und Reagieren auf und Aufrufen von `task/fetch` `task/submit` Nachrichten in Node.js.</span><span class="sxs-lookup"><span data-stu-id="84889-169">The next section provides an example of receiving and responding to `task/fetch` and `task/submit` invoke messages in Node.js.</span></span>

## <a name="example-of-taskfetch-and-tasksubmit-invoke-messages-in-nodejs-and-c"></a><span data-ttu-id="84889-170">Beispiel für Task-/Fetch- und Task/Submit-Aufrufnachrichten in Node.js und C #</span><span class="sxs-lookup"><span data-stu-id="84889-170">Example of task/fetch and task/submit invoke messages in Node.js and C#</span></span>

# <a name="nodejs"></a>[<span data-ttu-id="84889-171">Node.js</span><span class="sxs-lookup"><span data-stu-id="84889-171">Node.js</span></span>](#tab/nodejs)

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

# <a name="c"></a>[<span data-ttu-id="84889-172">C#</span><span class="sxs-lookup"><span data-stu-id="84889-172">C#</span></span>](#tab/csharp)

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

### <a name="bot-framework-card-actions-vs-adaptive-card-actionsubmit-actions"></a><span data-ttu-id="84889-173">Bot Framework-Kartenaktionen im Vergleich zu Aktionen für adaptive Karten.Submit-Aktionen</span><span class="sxs-lookup"><span data-stu-id="84889-173">Bot Framework card actions vs. Adaptive Card Action.Submit actions</span></span>

<span data-ttu-id="84889-174">Das Schema für Bot Framework-Kartenaktionen unterscheidet sich von `Action.Submit` adaptiven Kartenaktionen, und die Möglichkeit zum Aufrufen von Aufgabenmodulen unterscheidet sich ebenfalls.</span><span class="sxs-lookup"><span data-stu-id="84889-174">The schema for Bot Framework card actions is different from Adaptive Card `Action.Submit` actions and the way to invoke task modules is also different.</span></span> <span data-ttu-id="84889-175">Das `data` Objekt enthält ein `Action.Submit` `msteams` Objekt, sodass es andere Eigenschaften auf der Karte nicht beeinträchtigt.</span><span class="sxs-lookup"><span data-stu-id="84889-175">The `data` object in `Action.Submit` contains an `msteams` object so it does not interfere with other properties in the card.</span></span> <span data-ttu-id="84889-176">Die folgende Tabelle zeigt ein Beispiel für jede Kartenaktion:</span><span class="sxs-lookup"><span data-stu-id="84889-176">The following table shows an example of each card action:</span></span>

| <span data-ttu-id="84889-177">Bot Framework-Kartenaktion</span><span class="sxs-lookup"><span data-stu-id="84889-177">Bot Framework card action</span></span>                              | <span data-ttu-id="84889-178">Aktion für adaptive Karten.Submit-Aktion</span><span class="sxs-lookup"><span data-stu-id="84889-178">Adaptive Card Action.Submit action</span></span>                     |
| ------------------------------------------------------ | ------------------------------------------------------ |
| <pre>{<br/>  "type": "invoke",<br/>  "title": "Buy",<br/>  "value": {<br/>    "type": "task/fetch",<br/>    &lt;...&gt;<br/>  }<br/>}</pre> | <pre>{<br/>  "type": "Action.Submit",<br/>  "id": "btnBuy",<br/>  "title": "Buy",<br/>  "data": {<br/>    &lt;...&gt;,<br/>    "msteams": {<br/>      "type": "task/fetch"<br/>    }<br/>  }<br/>}</pre>  |

## <a name="code-sample"></a><span data-ttu-id="84889-179">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="84889-179">Code sample</span></span>

|<span data-ttu-id="84889-180">Beispielname</span><span class="sxs-lookup"><span data-stu-id="84889-180">Sample name</span></span> | <span data-ttu-id="84889-181">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="84889-181">Description</span></span> | <span data-ttu-id="84889-182">.NET</span><span class="sxs-lookup"><span data-stu-id="84889-182">.NET</span></span> | <span data-ttu-id="84889-183">Node.js</span><span class="sxs-lookup"><span data-stu-id="84889-183">Node.js</span></span>|
|----------------|-----------------|--------------|----------------|
|<span data-ttu-id="84889-184">Aufgabenmodul-Beispielbots-V4</span><span class="sxs-lookup"><span data-stu-id="84889-184">Task module sample bots-V4</span></span> | <span data-ttu-id="84889-185">Beispiele zum Erstellen von Aufgabenmodulen.</span><span class="sxs-lookup"><span data-stu-id="84889-185">Samples for creating task modules.</span></span> |[<span data-ttu-id="84889-186">View</span><span class="sxs-lookup"><span data-stu-id="84889-186">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/54.teams-task-module)|[<span data-ttu-id="84889-187">View</span><span class="sxs-lookup"><span data-stu-id="84889-187">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/54.teams-task-module)|

## <a name="see-also"></a><span data-ttu-id="84889-188">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="84889-188">See also</span></span>

* [<span data-ttu-id="84889-189">Beispielcode für Microsoft Teams Aufgabenmodul in Node.js</span><span class="sxs-lookup"><span data-stu-id="84889-189">Microsoft Teams task module sample code in Node.js</span></span>](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs/blob/master/src/TeamsBot.ts)
* [<span data-ttu-id="84889-190">Bot Framework-Beispiele</span><span class="sxs-lookup"><span data-stu-id="84889-190">Bot Framework samples</span></span>](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)
