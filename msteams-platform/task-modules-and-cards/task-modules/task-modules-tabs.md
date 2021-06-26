---
title: Verwenden von Aufgabenmodulen in Microsoft Teams Registerkarten
description: Erläutert das Aufrufen von Aufgabenmodulen von Teams Registerkarten mithilfe des Microsoft Teams-Client-SDKs.
localization_priority: Normal
ms.topic: how-to
keywords: Teams-Registerkarten-Client-SDK für Aufgabenmodule
ms.openlocfilehash: 8afd2c93261f28aa7ced4c98d29be27dca35f8b1
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140552"
---
# <a name="use-task-modules-in-tabs"></a><span data-ttu-id="40d53-104">Verwenden von Aufgabenmodulen in Registerkarten</span><span class="sxs-lookup"><span data-stu-id="40d53-104">Use task modules in tabs</span></span>

<span data-ttu-id="40d53-105">Fügen Sie Ihrer Registerkarte ein Aufgabenmodul hinzu, um die Benutzererfahrung für workflows zu vereinfachen, die eine Dateneingabe erfordern.</span><span class="sxs-lookup"><span data-stu-id="40d53-105">Add a task module to your tab to simplify your user's experience for any workflows that require data input.</span></span> <span data-ttu-id="40d53-106">Mit Aufgabenmodulen können Sie ihre Eingaben in einem Microsoft Teams-Aware-Popup erfassen.</span><span class="sxs-lookup"><span data-stu-id="40d53-106">Task modules allow you to gather their input in a Microsoft Teams-Aware pop-up.</span></span> <span data-ttu-id="40d53-107">Ein gutes Beispiel hierfür ist das Bearbeiten von Planner-Karten.</span><span class="sxs-lookup"><span data-stu-id="40d53-107">A good example of this is editing Planner cards.</span></span> <span data-ttu-id="40d53-108">Sie können Aufgabenmodule verwenden, um eine ähnliche Oberfläche zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="40d53-108">You can use task modules to create a similar experience.</span></span>

<span data-ttu-id="40d53-109">Zur Unterstützung des Aufgabenmodulfeatures werden dem [Teams-Client-SDK](/javascript/api/overview/msteams-client)zwei neue Funktionen hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="40d53-109">To support the task module feature, two new functions are added to the [Teams client SDK](/javascript/api/overview/msteams-client).</span></span> <span data-ttu-id="40d53-110">Der folgende Code zeigt ein Beispiel für diese beiden Funktionen:</span><span class="sxs-lookup"><span data-stu-id="40d53-110">The following code shows an example of these two functions:</span></span>

```typescript
microsoftTeams.tasks.startTask(
    taskInfo: TaskInfo,
    submitHandler?: (err: string, result: string | any) => void
): void;

microsoftTeams.tasks.submitTask(
    result?: string | any,
    appIds?: string | string[]
): void;
```

<span data-ttu-id="40d53-111">Sie können sehen, wie das Aufrufen eines Aufgabenmoduls über eine Registerkarte und das Übermitteln des Ergebnisses eines Aufgabenmoduls funktioniert.</span><span class="sxs-lookup"><span data-stu-id="40d53-111">You can see how invoking a task module from a tab and submitting the result of a task module works.</span></span>

## <a name="invoke-a-task-module-from-a-tab"></a><span data-ttu-id="40d53-112">Aufrufen eines Aufgabenmoduls über eine Registerkarte</span><span class="sxs-lookup"><span data-stu-id="40d53-112">Invoke a task module from a tab</span></span>

<span data-ttu-id="40d53-113">Zum Aufrufen eines Aufgabenmoduls über eine Registerkarte übergeben Sie `microsoftTeams.tasks.startTask()` ein [TaskInfo-Objekt](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object) und eine optionale `submitHandler` Rückruffunktion.</span><span class="sxs-lookup"><span data-stu-id="40d53-113">To invoke a task module from a tab use `microsoftTeams.tasks.startTask()` passing a [TaskInfo object](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object) and an optional `submitHandler` callback function.</span></span> <span data-ttu-id="40d53-114">Es gibt zwei Zu berücksichtigende Fälle:</span><span class="sxs-lookup"><span data-stu-id="40d53-114">There are two cases to consider:</span></span>

* <span data-ttu-id="40d53-115">Der Wert von `TaskInfo.url` ist auf eine URL festgelegt.</span><span class="sxs-lookup"><span data-stu-id="40d53-115">The value of `TaskInfo.url` is set to a URL.</span></span> <span data-ttu-id="40d53-116">Das Aufgabenmodulfenster wird angezeigt und `TaskModule.url` als `<iframe>` darin geladen.</span><span class="sxs-lookup"><span data-stu-id="40d53-116">The task module window appears and `TaskModule.url` is loaded as an `<iframe>` inside it.</span></span> <span data-ttu-id="40d53-117">JavaScript auf dieser Seite ruft `microsoftTeams.initialize()` .</span><span class="sxs-lookup"><span data-stu-id="40d53-117">JavaScript on that page calls `microsoftTeams.initialize()`.</span></span> <span data-ttu-id="40d53-118">Wenn eine Funktion auf der Seite vorhanden `submitHandler` ist und beim Aufrufen ein Fehler `microsoftTeams.tasks.startTask()` auftritt, wird dieser `submitHandler` aufgerufen, wobei die `err` Fehlerzeichenfolge auf dieselbe festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="40d53-118">If there is a `submitHandler` function on the page and there is an error when invoking `microsoftTeams.tasks.startTask()`, then `submitHandler` is invoked with `err` set to the error string indicating the same.</span></span> <span data-ttu-id="40d53-119">Weitere Informationen finden Sie unter [Fehler beim Aufrufen des Aufgabenmoduls.](#task-module-invocation-errors)</span><span class="sxs-lookup"><span data-stu-id="40d53-119">For more information, see [task module invocation errors](#task-module-invocation-errors).</span></span>
* <span data-ttu-id="40d53-120">Der Wert von `taskInfo.card` ist der [JSON-Code für eine adaptive Karte.](~/task-modules-and-cards/task-modules/invoking-task-modules.md#adaptive-card-or-adaptive-card-bot-card-attachment)</span><span class="sxs-lookup"><span data-stu-id="40d53-120">The value of `taskInfo.card` is the [JSON for an Adaptive Card](~/task-modules-and-cards/task-modules/invoking-task-modules.md#adaptive-card-or-adaptive-card-bot-card-attachment).</span></span> <span data-ttu-id="40d53-121">Es gibt keine JavaScript-Funktion, die aufgerufen werden `submitHandler` kann, wenn der Benutzer eine Schaltfläche auf der adaptiven Karte schließt oder drückt.</span><span class="sxs-lookup"><span data-stu-id="40d53-121">There is no JavaScript `submitHandler` function to call when the user closes or presses a button on the Adaptive Card.</span></span> <span data-ttu-id="40d53-122">Die einzige Möglichkeit, die vom Benutzer eingegebenen Informationen zu erhalten, besteht darin, das Ergebnis an einen Bot zu übergeben.</span><span class="sxs-lookup"><span data-stu-id="40d53-122">The only way to receive what the user entered is by passing the result to a bot.</span></span> <span data-ttu-id="40d53-123">Um ein Aufgabenmodul für adaptive Karten auf einer Registerkarte zu verwenden, muss Ihre App einen Bot enthalten, um eine Antwort des Benutzers zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="40d53-123">To use an Adaptive Card task module from a tab, your app must include a bot to get any response from the user.</span></span>

<span data-ttu-id="40d53-124">Der nächste Abschnitt enthält ein Beispiel für das Aufrufen eines Aufgabenmoduls.</span><span class="sxs-lookup"><span data-stu-id="40d53-124">The next section gives an example of invoking a task module.</span></span>

## <a name="example-of-invoking-a-task-module"></a><span data-ttu-id="40d53-125">Beispiel für das Aufrufen eines Aufgabenmoduls</span><span class="sxs-lookup"><span data-stu-id="40d53-125">Example of invoking a task module</span></span>

<span data-ttu-id="40d53-126">In der folgenden Abbildung wird das Aufgabenmodul angezeigt:</span><span class="sxs-lookup"><span data-stu-id="40d53-126">The following image displays the task module:</span></span>

![Aufgabenmodul – benutzerdefiniertes Formular](~/assets/images/task-module/task-module-custom-form.png)

<span data-ttu-id="40d53-128">Der folgende Code basiert auf [dem Aufgabenmodulbeispiel:](~/task-modules-and-cards/task-modules/invoking-task-modules.md#code-sample)</span><span class="sxs-lookup"><span data-stu-id="40d53-128">The following code is adapted from [the task module sample](~/task-modules-and-cards/task-modules/invoking-task-modules.md#code-sample):</span></span>

```javascript
let taskInfo = {
    title: null,
    height: null,
    width: null,
    url: null,
    card: null,
    fallbackUrl: null,
    completionBotId: null,
};

taskInfo.url = "https://contoso.com/teamsapp/customform";
taskInfo.title = "Custom Form";
taskInfo.height = 510;
taskInfo.width = 430;
submitHandler = (err, result) => {
    console.log(`Submit handler - err: ${err}`);
    console.log(`Submit handler - result\rName: ${result.name}\rEmail: ${result.email}\rFavorite book: ${result.favoriteBook}`);
};
microsoftTeams.tasks.startTask(taskInfo, submitHandler);
```

<span data-ttu-id="40d53-129">Dies `submitHandler` ist sehr einfach und entspricht dem Wert der Konsole oder der `err` `result` Konsole.</span><span class="sxs-lookup"><span data-stu-id="40d53-129">The `submitHandler` is very simple and it echoes the value of `err` or `result` to the console.</span></span>

## <a name="submit-the-result-of-a-task-module"></a><span data-ttu-id="40d53-130">Übermitteln des Ergebnisses eines Aufgabenmoduls</span><span class="sxs-lookup"><span data-stu-id="40d53-130">Submit the result of a task module</span></span>

<span data-ttu-id="40d53-131">Die `submitHandler` Funktion befindet sich auf der Webseite und wird mit `TaskInfo.url` `TaskInfo.url` verwendet.</span><span class="sxs-lookup"><span data-stu-id="40d53-131">The `submitHandler` function resides in the `TaskInfo.url` web page and is used with `TaskInfo.url`.</span></span> <span data-ttu-id="40d53-132">Wenn beim Aufrufen des Aufgabenmoduls ein Fehler auftritt, wird Ihre `submitHandler` Funktion sofort mit einer Zeichenfolge `err` aufgerufen, die angibt, welcher [Fehler aufgetreten ist.](#task-module-invocation-errors)</span><span class="sxs-lookup"><span data-stu-id="40d53-132">If there is an error when invoking the task module, your `submitHandler` function is immediately invoked with an `err` string indicating what [error occurred](#task-module-invocation-errors).</span></span> <span data-ttu-id="40d53-133">Die `submitHandler` Funktion wird auch mit einer Zeichenfolge `err` aufgerufen, wenn der Benutzer X oben rechts im Aufgabenmodul auswählt, um sie zu schließen.</span><span class="sxs-lookup"><span data-stu-id="40d53-133">The `submitHandler` function is also called with an `err` string when the user selects X at the upper right of the task module to close it.</span></span>

<span data-ttu-id="40d53-134">Wenn kein Aufruffehler auftritt und der Benutzer X nicht auswählt, um es zu schließen, wählt der Benutzer nach Abschluss eine Schaltfläche aus.</span><span class="sxs-lookup"><span data-stu-id="40d53-134">If there is no invocation error and the user does not select X to dismiss it, the user chooses a button when finished.</span></span> <span data-ttu-id="40d53-135">Je nachdem, ob es sich um eine URL oder eine adaptive Karte im Aufgabenmodul handelt, enthalten die nächsten Abschnitte Details dazu, was passiert.</span><span class="sxs-lookup"><span data-stu-id="40d53-135">Depending on whether it is a URL or an Adaptive Card in the task module, the next sections provide details on what occurs.</span></span>

### <a name="html-or-javascript-taskinfourl"></a><span data-ttu-id="40d53-136">HTML oder JavaScript `TaskInfo.url`</span><span class="sxs-lookup"><span data-stu-id="40d53-136">HTML or JavaScript `TaskInfo.url`</span></span>

<span data-ttu-id="40d53-137">Rufen Sie nach dem Überprüfen der Eingaben des Benutzers die `microsoftTeams.tasks.submitTask()` SDK-Funktion auf, die als `submitTask()` bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="40d53-137">After validating the user's inputs, call the `microsoftTeams.tasks.submitTask()` SDK function referred to as `submitTask()`.</span></span> <span data-ttu-id="40d53-138">Rufen `submitTask()` Sie ohne Parameter auf, wenn Sie nur möchten, dass Teams das Aufgabenmodul schließt.</span><span class="sxs-lookup"><span data-stu-id="40d53-138">Call `submitTask()` without any parameters if you just want Teams to close the task module.</span></span> <span data-ttu-id="40d53-139">Sie können ein Objekt oder eine Zeichenfolge an Ihre `submitHandler` übergeben.</span><span class="sxs-lookup"><span data-stu-id="40d53-139">You can pass an object or a string to your `submitHandler`.</span></span>

<span data-ttu-id="40d53-140">Übergeben Sie Ihr Ergebnis als ersten Parameter.</span><span class="sxs-lookup"><span data-stu-id="40d53-140">Pass your result as the first parameter.</span></span> <span data-ttu-id="40d53-141">Teams ruft auf, wo sich das Objekt oder die Zeichenfolge befindet `submitHandler` `err` und `null` `result` ist, an die Sie übergeben `submitTask()` haben.</span><span class="sxs-lookup"><span data-stu-id="40d53-141">Teams invokes `submitHandler` where `err` is `null` and `result` is the object or string you passed to `submitTask()`.</span></span> <span data-ttu-id="40d53-142">Wenn Sie `submitTask()` mit einem Parameter `result` aufrufen, müssen Sie ein oder ein Array von `appId` `appId` Zeichenfolgen übergeben.</span><span class="sxs-lookup"><span data-stu-id="40d53-142">If you call `submitTask()` with a `result` parameter, you must pass an `appId` or an array of `appId` strings.</span></span> <span data-ttu-id="40d53-143">Dadurch können Teams überprüfen, ob die App, die das Ergebnis sendet, mit dem aufgerufenen Aufgabenmodul übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="40d53-143">This permits Teams to validate that the app sending the result is same as the invoked task module.</span></span>

### <a name="adaptive-card-taskinfocard"></a><span data-ttu-id="40d53-144">Adaptive Karte `TaskInfo.card`</span><span class="sxs-lookup"><span data-stu-id="40d53-144">Adaptive Card `TaskInfo.card`</span></span>

<span data-ttu-id="40d53-145">Wenn Sie das Aufgabenmodul mit einer aufrufen `submitHandler` und der Benutzer eine Schaltfläche auswählt, werden die Werte auf der Karte als Wert von `Action.Submit` `result` zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="40d53-145">When you invoke the task module with a `submitHandler` and the user selects an `Action.Submit` button, the values in the card are returned as the value of `result`.</span></span> <span data-ttu-id="40d53-146">Wenn der Benutzer die Esc-Taste oder X oben rechts auswählt, `err` wird stattdessen zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="40d53-146">If the user selects the Esc key or X at the top right, `err` is returned instead.</span></span> <span data-ttu-id="40d53-147">Wenn Ihre App zusätzlich zu einer Registerkarte einen Bot enthält, können Sie einfach den `appId` Bot als Wert in das Objekt `completionBotId` `TaskInfo` einschließen.</span><span class="sxs-lookup"><span data-stu-id="40d53-147">If your app contains a bot in addition to a tab, you can simply include the `appId` of the bot as the value of `completionBotId` in the `TaskInfo` object.</span></span> <span data-ttu-id="40d53-148">Der vom Benutzer ausgefüllte Textkörper der adaptiven Karte wird mithilfe einer Nachricht an den Bot `task/submit invoke` gesendet, wenn der Benutzer eine Schaltfläche auswählt. `Action.Submit`</span><span class="sxs-lookup"><span data-stu-id="40d53-148">The Adaptive Card body as filled in by the user is sent to the bot using a `task/submit invoke` message when the user selects an `Action.Submit` button.</span></span> <span data-ttu-id="40d53-149">Das Schema für das empfangene Objekt ähnelt dem [Schema, das Sie für Aufgaben-/Abruf- und Aufgaben-/Sendenachrichten erhalten.](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages)</span><span class="sxs-lookup"><span data-stu-id="40d53-149">The schema for the object you receive is very similar to [the schema you receive for task/fetch and task/submit messages](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages).</span></span> <span data-ttu-id="40d53-150">Der einzige Unterschied besteht darin, dass das Schema des JSON-Objekts ein Adaptive Card-Objekt im Gegensatz zu einem Objekt ist, das ein Adaptive Card-Objekt enthält, als [wenn adaptive Karten mit Bots verwendet werden.](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages)</span><span class="sxs-lookup"><span data-stu-id="40d53-150">The only difference is that the schema of the JSON object is an Adaptive Card object as opposed to an object containing an Adaptive Card object as [when Adaptive cards are used with bots](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages).</span></span>

<span data-ttu-id="40d53-151">Der nächste Abschnitt enthält ein Beispiel für das Übermitteln des Ergebnisses eines Aufgabenmoduls.</span><span class="sxs-lookup"><span data-stu-id="40d53-151">The next section gives an example of submitting the result of a task module.</span></span>

## <a name="example-of-submitting-the-result-of-a-task-module"></a><span data-ttu-id="40d53-152">Beispiel für das Übermitteln des Ergebnisses eines Aufgabenmoduls</span><span class="sxs-lookup"><span data-stu-id="40d53-152">Example of submitting the result of a task module</span></span>

<span data-ttu-id="40d53-153">Weitere Informationen finden Sie [im HTML-Formular im Aufgabenmodul.](#example-of-invoking-a-task-module)</span><span class="sxs-lookup"><span data-stu-id="40d53-153">For more information, see the [HTML form in the task module](#example-of-invoking-a-task-module).</span></span> <span data-ttu-id="40d53-154">Der folgende Code enthält ein Beispiel dafür, wo das Formular definiert ist:</span><span class="sxs-lookup"><span data-stu-id="40d53-154">The following code gives an example of where the form is defined:</span></span>

```html
<form method="POST" id="customerForm" action="/register" onSubmit="return validateForm()">
```

<span data-ttu-id="40d53-155">Es gibt fünf Felder in diesem Formular, aber für dieses Beispiel sind nur drei Werte erforderlich, `name` und `email` `favoriteBook` .</span><span class="sxs-lookup"><span data-stu-id="40d53-155">There are five fields on this form but for this example only three values are required, `name`, `email`, and `favoriteBook`.</span></span>

<span data-ttu-id="40d53-156">Der folgende Code enthält ein Beispiel für die `validateForm()` Funktion, die `submitTask()` aufruft:</span><span class="sxs-lookup"><span data-stu-id="40d53-156">The following code gives an example of the `validateForm()` function that calls `submitTask()`:</span></span>

```javascript
function validateForm() {
    var customerInfo = {
        name: document.forms["customerForm"]["name"].value,
        email: document.forms["customerForm"]["email"].value,
        favoriteBook: document.forms["customerForm"]["favoriteBook"].value
    }
    microsoftTeams.tasks.submitTask(customerInfo, "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx");
    return true;
}
```

<span data-ttu-id="40d53-157">Der nächste Abschnitt enthält Aufrufprobleme des Aufgabenmoduls und deren Fehlermeldungen.</span><span class="sxs-lookup"><span data-stu-id="40d53-157">The next section provides task module invocation problems and their error messages.</span></span>

## <a name="task-module-invocation-errors"></a><span data-ttu-id="40d53-158">Fehler beim Aufrufen des Aufgabenmoduls</span><span class="sxs-lookup"><span data-stu-id="40d53-158">Task module invocation errors</span></span>

<span data-ttu-id="40d53-159">Die folgende Tabelle enthält die möglichen `err` Werte, die von Ihnen empfangen werden `submitHandler` können:</span><span class="sxs-lookup"><span data-stu-id="40d53-159">The following table provides the possible values of `err` that can be received by your `submitHandler`:</span></span>

| <span data-ttu-id="40d53-160">Problem</span><span class="sxs-lookup"><span data-stu-id="40d53-160">Problem</span></span> | <span data-ttu-id="40d53-161">Fehlermeldung, die den Wert von `err`</span><span class="sxs-lookup"><span data-stu-id="40d53-161">Error message that is value of `err`</span></span> |
| ------- | ------------------------------ |
| <span data-ttu-id="40d53-162">Werte für beide `TaskInfo.url` werte und `TaskInfo.card` wurden angegeben.</span><span class="sxs-lookup"><span data-stu-id="40d53-162">Values for both `TaskInfo.url` and `TaskInfo.card` were specified.</span></span> | <span data-ttu-id="40d53-163">Werte für Karte und URL wurden angegeben.</span><span class="sxs-lookup"><span data-stu-id="40d53-163">Values for both card and URL were specified.</span></span> <span data-ttu-id="40d53-164">Der eine oder andere, aber nicht beide, sind zulässig.</span><span class="sxs-lookup"><span data-stu-id="40d53-164">One or the other, but not both, are allowed.</span></span> |
| <span data-ttu-id="40d53-165">`TaskInfo.url`Weder `TaskInfo.card` angegeben noch angegeben.</span><span class="sxs-lookup"><span data-stu-id="40d53-165">Neither `TaskInfo.url` nor `TaskInfo.card` specified.</span></span> | <span data-ttu-id="40d53-166">Sie müssen einen Wert für karte oder URL angeben.</span><span class="sxs-lookup"><span data-stu-id="40d53-166">You must specify a value for either card or URL.</span></span> |
| <span data-ttu-id="40d53-167">`appId`Ungültig.</span><span class="sxs-lookup"><span data-stu-id="40d53-167">Invalid `appId`.</span></span> | <span data-ttu-id="40d53-168">Ungültige App-ID.</span><span class="sxs-lookup"><span data-stu-id="40d53-168">Invalid app ID.</span></span> |
| <span data-ttu-id="40d53-169">Der Benutzer hat die X-Schaltfläche ausgewählt und sie geschlossen.</span><span class="sxs-lookup"><span data-stu-id="40d53-169">User selected X button, closing it.</span></span> | <span data-ttu-id="40d53-170">Der Benutzer hat das Aufgabenmodul abgebrochen oder geschlossen.</span><span class="sxs-lookup"><span data-stu-id="40d53-170">User cancelled or closed the task module.</span></span> |

## <a name="code-sample"></a><span data-ttu-id="40d53-171">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="40d53-171">Code sample</span></span>

|<span data-ttu-id="40d53-172">Beispielname</span><span class="sxs-lookup"><span data-stu-id="40d53-172">Sample name</span></span> | <span data-ttu-id="40d53-173">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="40d53-173">Description</span></span> | <span data-ttu-id="40d53-174">.NET</span><span class="sxs-lookup"><span data-stu-id="40d53-174">.NET</span></span> | <span data-ttu-id="40d53-175">Node.js</span><span class="sxs-lookup"><span data-stu-id="40d53-175">Node.js</span></span>|
|----------------|-----------------|--------------|----------------|
|<span data-ttu-id="40d53-176">Aufgabenmodul-Beispielregisterkarten und Bots-V3</span><span class="sxs-lookup"><span data-stu-id="40d53-176">Task module sample tabs and bots-V3</span></span> | <span data-ttu-id="40d53-177">Beispiele zum Erstellen von Aufgabenmodulen.</span><span class="sxs-lookup"><span data-stu-id="40d53-177">Samples for creating task modules.</span></span> |[<span data-ttu-id="40d53-178">View</span><span class="sxs-lookup"><span data-stu-id="40d53-178">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/csharp)|[<span data-ttu-id="40d53-179">View</span><span class="sxs-lookup"><span data-stu-id="40d53-179">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/nodejs)| 

## <a name="see-also"></a><span data-ttu-id="40d53-180">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="40d53-180">See also</span></span>

[<span data-ttu-id="40d53-181">Aufrufen und Schließen von Aufgabenmodulen</span><span class="sxs-lookup"><span data-stu-id="40d53-181">Invoke and dismiss task modules</span></span>](~/task-modules-and-cards/task-modules/invoking-task-modules.md)

## <a name="next-step"></a><span data-ttu-id="40d53-182">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="40d53-182">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="40d53-183">Verwenden von Aufgabenmodulen von Bots</span><span class="sxs-lookup"><span data-stu-id="40d53-183">Using task modules from bots</span></span>](~/task-modules-and-cards/task-modules/task-modules-bots.md)
