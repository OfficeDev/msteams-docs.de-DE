---
title: Verwenden von Aufgabenmodulen in Microsoft Teams-Registerkarten
description: Erläutert das Aufrufen von Aufgabenmodulen von Teams-Registerkarten mithilfe des Microsoft Teams-Client-SDK.
ms.topic: how-to
keywords: task modules teams tabs client sdk
ms.openlocfilehash: dbcc6ce0ba31bae43335334dfb1c354acc33a2a0
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696031"
---
# <a name="using-task-modules-in-tabs"></a><span data-ttu-id="71d75-104">Verwenden von Aufgabenmodulen in Registerkarten</span><span class="sxs-lookup"><span data-stu-id="71d75-104">Using task modules in tabs</span></span>

<span data-ttu-id="71d75-105">Das Hinzufügen eines Aufgabenmoduls zu Ihrer Registerkarte kann die Benutzererfahrung für Workflows, für die Dateneingaben erforderlich sind, erheblich vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="71d75-105">Adding a task module to your tab can greatly simplify your user's experience for any workflows that require data input.</span></span> <span data-ttu-id="71d75-106">Mit Aufgabenmodulen können Sie ihre Eingaben in einem Teams-bewussten Popup erfassen.</span><span class="sxs-lookup"><span data-stu-id="71d75-106">Task modules allow you to gather their input in a Teams-aware popup.</span></span> <span data-ttu-id="71d75-107">Ein gutes Beispiel hierin ist die Bearbeitung von Planner-Karten. Sie können Aufgabenmodule verwenden, um eine ähnliche Erfahrung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="71d75-107">A good example of this is editing Planner cards; you can use task modules to create a similar experience.</span></span>

<span data-ttu-id="71d75-108">Zur Unterstützung des Aufgabenmodulfeatures wurden dem [Microsoft Teams-Client-SDK](/javascript/api/overview/msteams-client)zwei neue Funktionen hinzugefügt:</span><span class="sxs-lookup"><span data-stu-id="71d75-108">To support the task module feature, two new functions were added to the [Microsoft Teams client SDK](/javascript/api/overview/msteams-client):</span></span>

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

<span data-ttu-id="71d75-109">Sehen wir uns an, wie jeder von ihnen funktioniert.</span><span class="sxs-lookup"><span data-stu-id="71d75-109">Let's see how each of them work.</span></span>

## <a name="invoking-a-task-module-from-a-tab"></a><span data-ttu-id="71d75-110">Aufrufen eines Aufgabenmoduls über eine Registerkarte</span><span class="sxs-lookup"><span data-stu-id="71d75-110">Invoking a task module from a tab</span></span>

<span data-ttu-id="71d75-111">Verwenden Sie zum Aufrufen eines Aufgabenmoduls von einer Registerkarte aus das Übergeben `microsoftTeams.tasks.startTask()` eines [TaskInfo-Objekts](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) und einer optionalen `submitHandler` Rückruffunktion.</span><span class="sxs-lookup"><span data-stu-id="71d75-111">To invoke a task module from a tab use `microsoftTeams.tasks.startTask()` passing a [TaskInfo object](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) and an optional `submitHandler` callback function.</span></span> <span data-ttu-id="71d75-112">Wie bereits beschrieben, sind zwei Fälle zu berücksichtigen:</span><span class="sxs-lookup"><span data-stu-id="71d75-112">As described earlier, there are two cases to consider:</span></span>

1. <span data-ttu-id="71d75-113">Der Wert von `TaskInfo.url` ist auf eine URL festgelegt.</span><span class="sxs-lookup"><span data-stu-id="71d75-113">The value of `TaskInfo.url` is set to a URL.</span></span> <span data-ttu-id="71d75-114">Das Aufgabenmodulfenster wird angezeigt und `TaskModule.url` als innen `<iframe>` geladen.</span><span class="sxs-lookup"><span data-stu-id="71d75-114">The task module window appears and `TaskModule.url` is loaded as an `<iframe>` inside it.</span></span> <span data-ttu-id="71d75-115">JavaScript auf dieser Seite sollte `microsoftTeams.initialize()` aufrufen.</span><span class="sxs-lookup"><span data-stu-id="71d75-115">JavaScript on that page should call `microsoftTeams.initialize()`.</span></span> <span data-ttu-id="71d75-116">Wenn auf der Seite eine Funktion enthalten ist und beim Aufrufen ein Fehler auftritt, wird mit set auf die Fehlerzeichenfolge aufgerufen, die den Fehler angibt, wie `submitHandler` `microsoftTeams.tasks.startTask()` unten `submitHandler` `err` [beschrieben.](#task-module-invocation-errors)</span><span class="sxs-lookup"><span data-stu-id="71d75-116">If there is a `submitHandler` function on the page and there is an error when invoking `microsoftTeams.tasks.startTask()`, then `submitHandler` is invoked with `err` set to the error string indicating the error as described [below](#task-module-invocation-errors).</span></span>
1. <span data-ttu-id="71d75-117">Der Wert von `taskInfo.card` ist der [JSON für eine adaptive Karte](~/task-modules-and-cards/what-are-task-modules.md#adaptive-card-or-adaptive-card-bot-card-attachment).</span><span class="sxs-lookup"><span data-stu-id="71d75-117">The value of `taskInfo.card` is the [JSON for an Adaptive card](~/task-modules-and-cards/what-are-task-modules.md#adaptive-card-or-adaptive-card-bot-card-attachment).</span></span> <span data-ttu-id="71d75-118">In diesem Fall gibt es offensichtlich keine JavaScript-Funktion zum Aufrufen, wenn der Benutzer eine Schaltfläche auf der adaptiven Karte schließt oder drückt. Die einzige Möglichkeit, das eingegebene Ergebnis zu erhalten, besteht in der Übergabe des Ergebnisses an einen `submitHandler` Bot.</span><span class="sxs-lookup"><span data-stu-id="71d75-118">In this case there's obviously not any JavaScript `submitHandler` function to call when the user closes or presses a button on the Adaptive card; the only way to receive what the user entered is by passing the result to a bot.</span></span> <span data-ttu-id="71d75-119">Um ein Aufgabenmodul für adaptive Karten auf einer Registerkarte verwenden zu können, muss Ihre App einen Bot enthalten, um Informationen vom Benutzer zurück zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="71d75-119">To use an Adaptive card task module from a tab your app must include a bot to get any information back from the user.</span></span> <span data-ttu-id="71d75-120">Dies wird unten erläutert.</span><span class="sxs-lookup"><span data-stu-id="71d75-120">This is explained below.</span></span>

## <a name="example-invoking-a-task-module"></a><span data-ttu-id="71d75-121">Beispiel: Aufrufen eines Aufgabenmoduls</span><span class="sxs-lookup"><span data-stu-id="71d75-121">Example: Invoking a task module</span></span>

<span data-ttu-id="71d75-122">Der folgende Code wird aus dem [Aufgabenmodulbeispiel angepasst.](~/task-modules-and-cards/what-are-task-modules.md#code-sample)</span><span class="sxs-lookup"><span data-stu-id="71d75-122">The code below is adapted from [the task module sample](~/task-modules-and-cards/what-are-task-modules.md#code-sample).</span></span> <span data-ttu-id="71d75-123">So sieht das Aufgabenmodul aus:</span><span class="sxs-lookup"><span data-stu-id="71d75-123">Here's what the task module looks like:</span></span>

![Aufgabenmodul – Benutzerdefiniertes Formular](~/assets/images/task-module/task-module-custom-form.png)

<span data-ttu-id="71d75-125">Das `submitHandler` ist sehr einfach; es echot einfach den Wert von oder an die `err` `result` Konsole:</span><span class="sxs-lookup"><span data-stu-id="71d75-125">The `submitHandler` is very simple; it just echoes the value of `err` or `result` to the console:</span></span>

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

## <a name="submitting-the-result-of-a-task-module"></a><span data-ttu-id="71d75-126">Übermitteln des Ergebnisses eines Aufgabenmoduls</span><span class="sxs-lookup"><span data-stu-id="71d75-126">Submitting the result of a task module</span></span>

<span data-ttu-id="71d75-127">Die `submitHandler` Funktion wird mit `TaskInfo.url` verwendet.</span><span class="sxs-lookup"><span data-stu-id="71d75-127">The `submitHandler` function is used with `TaskInfo.url`.</span></span> <span data-ttu-id="71d75-128">Die `submitHandler` Funktion befindet sich auf der `TaskInfo.url` Webseite.</span><span class="sxs-lookup"><span data-stu-id="71d75-128">The `submitHandler` function resides in the `TaskInfo.url` web page.</span></span> <span data-ttu-id="71d75-129">Wenn beim Aufrufen des Aufgabenmoduls ein Fehler auftritt, wird Ihre Funktion sofort mit einer Zeichenfolge aufgerufen, die angibt, `submitHandler` `err` welcher Fehler aufgetreten [ist.](#task-module-invocation-errors)</span><span class="sxs-lookup"><span data-stu-id="71d75-129">If there's an error when invoking the task module your `submitHandler` function will be immediately invoked with an `err` string indicating which [error occurred](#task-module-invocation-errors).</span></span> <span data-ttu-id="71d75-130">Die Funktion wird auch mit einer Zeichenfolge aufgerufen, wenn der Benutzer das X oben `submitHandler` `err` rechts im Aufgabenmodul drückt.</span><span class="sxs-lookup"><span data-stu-id="71d75-130">The `submitHandler` function is also called with an `err` string when the user presses the X at the upper right of task module.</span></span>

<span data-ttu-id="71d75-131">Wenn kein Aufruffehler auftritt und der Benutzer X nicht drückt, um ihn zu schließen, drückt der Benutzer nach Abschluss eine Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="71d75-131">If there's no invocation error and the user doesn't press X to dismiss it, the user presses a button when finished.</span></span> <span data-ttu-id="71d75-132">Je nachdem, ob es sich um eine URL oder eine adaptive Karte im Aufgabenmodul geht, geschieht dies:</span><span class="sxs-lookup"><span data-stu-id="71d75-132">Depending on whether it's a URL or an Adaptive card in the task module, here's what happens:</span></span>

### <a name="htmljavascript-taskinfourl"></a><span data-ttu-id="71d75-133">HTML/JavaScript ( `TaskInfo.url` )</span><span class="sxs-lookup"><span data-stu-id="71d75-133">HTML/JavaScript (`TaskInfo.url`)</span></span>

<span data-ttu-id="71d75-134">Nachdem Sie überprüft haben, was der Benutzer eingegeben hat, rufen Sie die SDK-Funktion auf (im Folgenden als zu `microsoftTeams.tasks.submitTask()` `submitTask()` Lesbarkeitszwecken bezeichnet).</span><span class="sxs-lookup"><span data-stu-id="71d75-134">Once you've validated what the user has entered you call the `microsoftTeams.tasks.submitTask()` SDK function (referred to hereafter as `submitTask()` for readability purposes).</span></span> <span data-ttu-id="71d75-135">Sie können ohne Parameter aufrufen, wenn Sie nur möchten, dass Teams das Aufgabenmodul schließt, aber meistens möchten Sie ein Objekt oder eine Zeichenfolge an `submitTask()` Ihre `submitHandler` übergeben.</span><span class="sxs-lookup"><span data-stu-id="71d75-135">You can call `submitTask()` without any parameters if you just want Teams to close the task module, but most of the time you'll want to pass an object or a string to your `submitHandler`.</span></span>

<span data-ttu-id="71d75-136">Übergeben Sie Ihr Ergebnis als ersten Parameter.</span><span class="sxs-lookup"><span data-stu-id="71d75-136">Pass your result as the first parameter.</span></span> <span data-ttu-id="71d75-137">Teams ruft das Objekt/die Zeichenfolge auf, das Sie `submitHandler` `err` an übergeben `null` `result` `submitTask()` haben.</span><span class="sxs-lookup"><span data-stu-id="71d75-137">Teams will invoke `submitHandler` where `err` will be `null` and `result` will be the object/string you passed to `submitTask()`.</span></span> <span data-ttu-id="71d75-138">Wenn Sie einen Parameter aufrufen, müssen Sie ein oder ein Array von Zeichenfolgen übergeben: Auf diese Weise kann Teams überprüfen, ob die App, die das Ergebnis sendet, dieselbe ist, die das Aufgabenmodul aufgerufen `submitTask()` `result`  `appId` `appId` hat.</span><span class="sxs-lookup"><span data-stu-id="71d75-138">If you do call `submitTask()` with a `result` parameter, you **must** pass an `appId` or an array of `appId` strings: this allows Teams to validate that the app sending the result is the same one which invoked the task module.</span></span>

### <a name="adaptive-card-taskinfocard"></a><span data-ttu-id="71d75-139">Adaptive Karte ( `TaskInfo.card` )</span><span class="sxs-lookup"><span data-stu-id="71d75-139">Adaptive card (`TaskInfo.card`)</span></span>

<span data-ttu-id="71d75-140">Wenn Sie das Aufgabenmodul mit einem aufgerufen haben, werden die Werte auf der Karte als Wert von zurückgegeben, wenn der Benutzer eine Schaltfläche `submitHandler` `Action.Submit` `result` drückt.</span><span class="sxs-lookup"><span data-stu-id="71d75-140">If you invoked the task module with a `submitHandler`, when the user presses an `Action.Submit` button the values in the card will be returned as the value of `result`.</span></span> <span data-ttu-id="71d75-141">Wenn der Benutzer die Esc-Taste drückt oder das X drückt, `err` wird stattdessen zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="71d75-141">If the user presses the Esc button or presses the X, `err` will be returned instead.</span></span> <span data-ttu-id="71d75-142">Wenn Ihre App zusätzlich zu einer Registerkarte einen Bot enthält, können Sie auch einfach den des Bots als `appId` Wert in das Objekt `completionBotId` `TaskInfo` hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="71d75-142">Alternatively, if your app contains a bot in addition to a tab you can simply include the `appId` of the bot as the value of `completionBotId` in the `TaskInfo` object.</span></span> <span data-ttu-id="71d75-143">Der adaptive Kartentext (wie vom Benutzer ausgefüllt) wird über eine Nachricht an den Bot gesendet, wenn der Benutzer `task/submit invoke` eine Schaltfläche `Action.Submit` drückt.</span><span class="sxs-lookup"><span data-stu-id="71d75-143">The Adaptive card body (as filled in by the user) will be sent to the bot via a `task/submit invoke` message when the user presses an `Action.Submit` button.</span></span> <span data-ttu-id="71d75-144">Das Schema für das empfangene Objekt ähnelt dem Schema, das Sie für [Aufgaben-/Abruf- und Aufgaben-/Absenden von Nachrichten erhalten.](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages) Der einzige Unterschied ist, dass das Schema des JSON-Objekts ein  adaptives Kartenobjekt ist, im Gegensatz zu einem Objekt, das ein adaptives Kartenobjekt enthält, als wenn adaptive Karten mit [Bots verwendet werden.](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages)</span><span class="sxs-lookup"><span data-stu-id="71d75-144">The schema for the object you receive is very similar to [the schema you receive for task/fetch and task/submit messages](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages); the only difference is that the schema of the JSON object is an Adaptive card object as opposed to an object *containing* an Adaptive card object as [when Adaptive cards are used with bots](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages).</span></span>

## <a name="example-submitting-the-result-of-a-task-module"></a><span data-ttu-id="71d75-145">Beispiel: Übermitteln des Ergebnisses eines Aufgabenmoduls</span><span class="sxs-lookup"><span data-stu-id="71d75-145">Example: submitting the result of a task module</span></span>

<span data-ttu-id="71d75-146">Rufen Sie [das Formular im obigen Aufgabenmodul mit](#example-invoking-a-task-module) einem HTML-Formular auf.</span><span class="sxs-lookup"><span data-stu-id="71d75-146">Recall the [form in the task module above](#example-invoking-a-task-module) with an HTML form.</span></span> <span data-ttu-id="71d75-147">Hier ist das Formular definiert:</span><span class="sxs-lookup"><span data-stu-id="71d75-147">Here's where the form is defined:</span></span>

```html
<form method="POST" id="customerForm" action="/register" onSubmit="return validateForm()">
```

<span data-ttu-id="71d75-148">Es gibt fünf Felder in diesem Formular, aber wir interessieren uns nur für die Werte von drei von ihnen für dieses Beispiel: `name` `email` , , und `favoriteBook` .</span><span class="sxs-lookup"><span data-stu-id="71d75-148">There are five fields on this form but we're only interested in the values of three of them for this example: `name`, `email`, and `favoriteBook`.</span></span>

<span data-ttu-id="71d75-149">Hier ist die `validateForm()` Funktion, die `submitTask()` aufruft:</span><span class="sxs-lookup"><span data-stu-id="71d75-149">Here's the `validateForm()` function that calls `submitTask()`:</span></span>

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

## <a name="task-module-invocation-errors"></a><span data-ttu-id="71d75-150">Fehler beim Aufrufen des Aufgabenmoduls</span><span class="sxs-lookup"><span data-stu-id="71d75-150">Task module invocation errors</span></span>

<span data-ttu-id="71d75-151">Hier sind die möglichen `err` Werte, die von Ihrem empfangen werden `submitHandler` können:</span><span class="sxs-lookup"><span data-stu-id="71d75-151">Here are the possible values of `err` that can be received by your `submitHandler`:</span></span>

| <span data-ttu-id="71d75-152">Problem</span><span class="sxs-lookup"><span data-stu-id="71d75-152">Problem</span></span> | <span data-ttu-id="71d75-153">Fehlermeldung (Wert von `err` )</span><span class="sxs-lookup"><span data-stu-id="71d75-153">Error message (value of `err`)</span></span> |
| ------- | ------------------------------ |
| <span data-ttu-id="71d75-154">Werte für beide `TaskInfo.url` und `TaskInfo.card` wurden angegeben.</span><span class="sxs-lookup"><span data-stu-id="71d75-154">Values for both `TaskInfo.url` and `TaskInfo.card` were specified.</span></span> | <span data-ttu-id="71d75-155">"Werte für Karte und URL wurden angegeben.</span><span class="sxs-lookup"><span data-stu-id="71d75-155">"Values for both card and url were specified.</span></span> <span data-ttu-id="71d75-156">Das eine oder andere, aber nicht beides, ist zulässig."</span><span class="sxs-lookup"><span data-stu-id="71d75-156">One or the other, but not both, are allowed."</span></span> |
| <span data-ttu-id="71d75-157">Weder `TaskInfo.url` angegeben noch `TaskInfo.card` angegeben.</span><span class="sxs-lookup"><span data-stu-id="71d75-157">Neither `TaskInfo.url` nor `TaskInfo.card` specified.</span></span> | <span data-ttu-id="71d75-158">"Sie müssen einen Wert für eine Karte oder url angeben."</span><span class="sxs-lookup"><span data-stu-id="71d75-158">"You must specify a value for either card or url."</span></span> |
| <span data-ttu-id="71d75-159">`appId`Ungültig.</span><span class="sxs-lookup"><span data-stu-id="71d75-159">Invalid `appId`.</span></span> | <span data-ttu-id="71d75-160">"Ungültige appId."</span><span class="sxs-lookup"><span data-stu-id="71d75-160">"Invalid appId."</span></span> |
| <span data-ttu-id="71d75-161">Der Benutzer hat die X-Taste gedrückt und sie geschlossen.</span><span class="sxs-lookup"><span data-stu-id="71d75-161">User pressed X button, closing it.</span></span> | <span data-ttu-id="71d75-162">"Der Benutzer hat das Aufgabenmodul abgebrochen/geschlossen."</span><span class="sxs-lookup"><span data-stu-id="71d75-162">"User cancelled/closed the task module."</span></span> |
