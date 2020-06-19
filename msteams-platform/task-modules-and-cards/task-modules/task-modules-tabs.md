---
title: Verwenden von Aufgaben Modulen in Microsoft Teams-Registerkarten
description: Erläutert das Aufrufen von Aufgaben Modulen aus Microsoft Teams-Registerkarten mithilfe des Microsoft Teams-Client-SDK.
keywords: Aufgaben Module-Registerkarten für Microsoft Teams-Client SDK
ms.openlocfilehash: e10958195713f338a9b5e0a0672d8b6a29da9264
ms.sourcegitcommit: 2a84a3c8b10771e37ce51bf603a967633947a3e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "44801198"
---
# <a name="using-task-modules-in-tabs"></a><span data-ttu-id="70a52-104">Verwenden von Aufgaben Modulen in Registerkarten</span><span class="sxs-lookup"><span data-stu-id="70a52-104">Using task modules in tabs</span></span>

<span data-ttu-id="70a52-105">Das Hinzufügen eines Aufgabenmoduls zur Registerkarte kann die Benutzerfreundlichkeit für Workflows erheblich vereinfachen, die Dateneingaben erfordern.</span><span class="sxs-lookup"><span data-stu-id="70a52-105">Adding a task module to your tab can greatly simplify your user's experience for any workflows that require data input.</span></span> <span data-ttu-id="70a52-106">Aufgaben Module ermöglichen es Ihnen, Ihre Eingaben in einem Teams-fähigen Popup-Fenster zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="70a52-106">Task modules allow you to gather their input in a Teams-aware popup.</span></span> <span data-ttu-id="70a52-107">Ein gutes Beispiel hierfür ist das Bearbeiten von Planner-Karten; Sie können Aufgaben Module verwenden, um eine ähnliche Erfahrung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="70a52-107">A good example of this is editing Planner cards; you can use task modules to create a similar experience.</span></span>

<span data-ttu-id="70a52-108">Zur Unterstützung der Funktion "Aufgabenmodul" wurden dem [Microsoft Teams-Client SDK](/javascript/api/overview/msteams-client)zwei neue Funktionen hinzugefügt:</span><span class="sxs-lookup"><span data-stu-id="70a52-108">To support the task module feature, two new functions were added to the [Microsoft Teams client SDK](/javascript/api/overview/msteams-client):</span></span>

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

<span data-ttu-id="70a52-109">Mal sehen, wie jeder von Ihnen funktioniert.</span><span class="sxs-lookup"><span data-stu-id="70a52-109">Let's see how each of them work.</span></span>

## <a name="invoking-a-task-module-from-a-tab"></a><span data-ttu-id="70a52-110">Aufrufen eines Aufgabenmoduls über eine Registerkarte</span><span class="sxs-lookup"><span data-stu-id="70a52-110">Invoking a task module from a tab</span></span>

<span data-ttu-id="70a52-111">Zum Aufrufen eines Aufgabenmoduls aus einer Registerkarte verwenden Sie `microsoftTeams.tasks.startTask()` das Übergeben eines [taskinfo-Objekts](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) und einer optionalen `submitHandler` Rückruffunktion.</span><span class="sxs-lookup"><span data-stu-id="70a52-111">To invoke a task module from a tab use `microsoftTeams.tasks.startTask()` passing a [TaskInfo object](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) and an optional `submitHandler` callback function.</span></span> <span data-ttu-id="70a52-112">Wie zuvor beschrieben, gibt es zwei Fälle, die beachtet werden sollten:</span><span class="sxs-lookup"><span data-stu-id="70a52-112">As described earlier, there are two cases to consider:</span></span>

1. <span data-ttu-id="70a52-113">Der Wert von `TaskInfo.url` ist auf eine URL festgelegt.</span><span class="sxs-lookup"><span data-stu-id="70a52-113">The value of `TaskInfo.url` is set to a URL.</span></span> <span data-ttu-id="70a52-114">Das Fenster Aufgabenmodul wird angezeigt, und `TaskModule.url` es wird als `<iframe>` darin geladen.</span><span class="sxs-lookup"><span data-stu-id="70a52-114">The task module window appears and `TaskModule.url` is loaded as an `<iframe>` inside it.</span></span> <span data-ttu-id="70a52-115">JavaScript auf dieser Seite sollte aufgerufen werden `microsoftTeams.initialize()` .</span><span class="sxs-lookup"><span data-stu-id="70a52-115">JavaScript on that page should call `microsoftTeams.initialize()`.</span></span> <span data-ttu-id="70a52-116">Wenn `submitHandler` auf der Seite eine Funktion vorhanden ist und beim Aufrufen ein Fehler auftritt `microsoftTeams.tasks.startTask()` , `submitHandler` wird mit `err` festgelegt, dass die Fehlerzeichenfolge den Fehler wie [unten](#task-module-invocation-errors)beschrieben angibt.</span><span class="sxs-lookup"><span data-stu-id="70a52-116">If there is a `submitHandler` function on the page and there is an error when invoking `microsoftTeams.tasks.startTask()`, then `submitHandler` is invoked with `err` set to the error string indicating the error as described [below](#task-module-invocation-errors).</span></span>
1. <span data-ttu-id="70a52-117">Der Wert von `taskInfo.card` ist [JSON für eine Adaptive Karte](~/task-modules-and-cards/what-are-task-modules.md#adaptive-card-or-adaptive-card-bot-card-attachment).</span><span class="sxs-lookup"><span data-stu-id="70a52-117">The value of `taskInfo.card` is the [JSON for an Adaptive card](~/task-modules-and-cards/what-are-task-modules.md#adaptive-card-or-adaptive-card-bot-card-attachment).</span></span> <span data-ttu-id="70a52-118">In diesem Fall gibt es natürlich keine JavaScript- `submitHandler` Funktion, die aufgerufen wird, wenn der Benutzer eine Schaltfläche auf der adaptiven Karte schließt oder drückt; die einzige Möglichkeit, die Eingabe des Benutzers zu erhalten, besteht darin, das Ergebnis an einen bot zu übergeben.</span><span class="sxs-lookup"><span data-stu-id="70a52-118">In this case there's obviously not any JavaScript `submitHandler` function to call when the user closes or presses a button on the Adaptive card; the only way to receive what the user entered is by passing the result to a bot.</span></span> <span data-ttu-id="70a52-119">Um einen Adaptive Card-Aufgabenmodul aus einer Registerkarte zu verwenden, muss Ihre APP einen bot enthalten, um alle Informationen vom Benutzer zurück zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="70a52-119">To use an Adaptive card task module from a tab your app must include a bot to get any information back from the user.</span></span> <span data-ttu-id="70a52-120">Dies wird im folgenden erläutert.</span><span class="sxs-lookup"><span data-stu-id="70a52-120">This is explained below.</span></span>

## <a name="example-invoking-a-task-module"></a><span data-ttu-id="70a52-121">Beispiel: Aufrufen eines Aufgabenmoduls</span><span class="sxs-lookup"><span data-stu-id="70a52-121">Example: Invoking a task module</span></span>

<span data-ttu-id="70a52-122">Der folgende Code wird aus [dem Aufgabenmodul Beispiel](~/task-modules-and-cards/what-are-task-modules.md#task-module-samples)angepasst.</span><span class="sxs-lookup"><span data-stu-id="70a52-122">The code below is adapted from [the task module sample](~/task-modules-and-cards/what-are-task-modules.md#task-module-samples).</span></span> <span data-ttu-id="70a52-123">Hier sehen Sie, wie das Aufgabenmodul aussieht:</span><span class="sxs-lookup"><span data-stu-id="70a52-123">Here's what the task module looks like:</span></span>

![Aufgabenmodul – benutzerdefiniertes Formular](~/assets/images/task-module/task-module-custom-form.png)

<span data-ttu-id="70a52-125">Das `submitHandler` ist sehr einfach; er gibt nur den Wert von `err` oder `result` in der Konsole wieder:</span><span class="sxs-lookup"><span data-stu-id="70a52-125">The `submitHandler` is very simple; it just echoes the value of `err` or `result` to the console:</span></span>

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

## <a name="submitting-the-result-of-a-task-module"></a><span data-ttu-id="70a52-126">Übermitteln des Ergebnisses eines Aufgabenmoduls</span><span class="sxs-lookup"><span data-stu-id="70a52-126">Submitting the result of a task module</span></span>

<span data-ttu-id="70a52-127">Die `submitHandler` -Funktion wird mit verwendet `TaskInfo.url` .</span><span class="sxs-lookup"><span data-stu-id="70a52-127">The `submitHandler` function is used with `TaskInfo.url`.</span></span> <span data-ttu-id="70a52-128">Die `submitHandler` Funktion befindet sich auf der `TaskInfo.url` Webseite.</span><span class="sxs-lookup"><span data-stu-id="70a52-128">The `submitHandler` function resides in the `TaskInfo.url` web page.</span></span> <span data-ttu-id="70a52-129">Wenn beim Aufrufen des Aufgabenmoduls ein Fehler auftritt `submitHandler` , wird die Funktion sofort mit einer `err` Zeichenfolge aufgerufen, die angibt, welcher [Fehler aufgetreten](#task-module-invocation-errors)ist.</span><span class="sxs-lookup"><span data-stu-id="70a52-129">If there's an error when invoking the task module your `submitHandler` function will be immediately invoked with an `err` string indicating which [error occurred](#task-module-invocation-errors).</span></span> <span data-ttu-id="70a52-130">Die `submitHandler` Funktion wird auch mit einer `err` Zeichenfolge aufgerufen, wenn der Benutzer das X in der oberen rechten Ecke des Aufgabenmoduls drückt.</span><span class="sxs-lookup"><span data-stu-id="70a52-130">The `submitHandler` function is also called with an `err` string when the user presses the X at the upper right of task module.</span></span>

<span data-ttu-id="70a52-131">Wenn kein Aufruffehler vorliegt und der Benutzer nicht X drückt, um ihn zu schließen, drückt der Benutzer nach Abschluss eine Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="70a52-131">If there's no invocation error and the user doesn't press X to dismiss it, the user presses a button when finished.</span></span> <span data-ttu-id="70a52-132">In Abhängigkeit davon, ob es sich um eine URL oder eine Adaptive Karte im Aufgabenmodul handelt, gehen Sie folgendermaßen vor:</span><span class="sxs-lookup"><span data-stu-id="70a52-132">Depending on whether it's a URL or an Adaptive card in the task module, here's what happens:</span></span>

### <a name="htmljavascript-taskinfourl"></a><span data-ttu-id="70a52-133">HTML/JavaScript ( `TaskInfo.url` )</span><span class="sxs-lookup"><span data-stu-id="70a52-133">HTML/JavaScript (`TaskInfo.url`)</span></span>

<span data-ttu-id="70a52-134">Nachdem Sie überprüft haben, was der Benutzer eingegeben hat, rufen Sie die `microsoftTeams.tasks.submitTask()` SDK-Funktion auf (wird im folgenden als `submitTask()` Zweck der Lesbarkeit bezeichnet).</span><span class="sxs-lookup"><span data-stu-id="70a52-134">Once you've validated what the user has entered you call the `microsoftTeams.tasks.submitTask()` SDK function (referred to hereafter as `submitTask()` for readability purposes).</span></span> <span data-ttu-id="70a52-135">Sie können `submitTask()` ohne Parameter aufrufen, wenn Sie lediglich möchten, dass Teams den Aufgabenmodul schließen, aber in den meisten Fällen möchten Sie ein Objekt oder eine Zeichenfolge an Ihren übergeben `submitHandler` .</span><span class="sxs-lookup"><span data-stu-id="70a52-135">You can call `submitTask()` without any parameters if you just want Teams to close the task module, but most of the time you'll want to pass an object or a string to your `submitHandler`.</span></span>

<span data-ttu-id="70a52-136">Übergeben Sie das Ergebnis als ersten Parameter.</span><span class="sxs-lookup"><span data-stu-id="70a52-136">Pass your result as the first parameter.</span></span> <span data-ttu-id="70a52-137">Teams rufen an, `submitHandler` wo `err` `null` `result` das Objekt/die Zeichenfolge, an das Sie übergeben werden, sein wird und wird `submitTask()` .</span><span class="sxs-lookup"><span data-stu-id="70a52-137">Teams will invoke `submitHandler` where `err` will be `null` and `result` will be the object/string you passed to `submitTask()`.</span></span> <span data-ttu-id="70a52-138">Wenn Sie `submitTask()` einen `result` Parameter aufrufen, **müssen** Sie ein `appId` oder ein Array von `appId` Zeichenfolgen übergeben: Dadurch können Teams überprüfen, ob die APP, die das Ergebnis sendet, dieselbe ist, die das Aufgabenmodul aufgerufen hat.</span><span class="sxs-lookup"><span data-stu-id="70a52-138">If you do call `submitTask()` with a `result` parameter, you **must** pass an `appId` or an array of `appId` strings: this allows Teams to validate that the app sending the result is the same one which invoked the task module.</span></span>

### <a name="adaptive-card-taskinfocard"></a><span data-ttu-id="70a52-139">Adaptive Karte ( `TaskInfo.card` )</span><span class="sxs-lookup"><span data-stu-id="70a52-139">Adaptive card (`TaskInfo.card`)</span></span>

<span data-ttu-id="70a52-140">Wenn Sie den Aufgabenmodul mit einem aufgerufen `submitHandler` haben und der Benutzer eine Schaltfläche drückt, werden `Action.Submit` die Werte in der Karte als Wert von zurückgegeben `result` .</span><span class="sxs-lookup"><span data-stu-id="70a52-140">If you invoked the task module with a `submitHandler`, when the user presses an `Action.Submit` button the values in the card will be returned as the value of `result`.</span></span> <span data-ttu-id="70a52-141">Wenn der Benutzer die ESC-Taste drückt oder das X drückt, `err` wird stattdessen zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="70a52-141">If the user presses the Esc button or presses the X, `err` will be returned instead.</span></span> <span data-ttu-id="70a52-142">Alternativ können Sie, wenn Ihre APP zusätzlich zu einer Registerkarte einen bot enthält, den `appId` des bot einfach als Wert `completionBotId` in das `TaskInfo` Objekt einschließen.</span><span class="sxs-lookup"><span data-stu-id="70a52-142">Alternatively, if your app contains a bot in addition to a tab you can simply include the `appId` of the bot as the value of `completionBotId` in the `TaskInfo` object.</span></span> <span data-ttu-id="70a52-143">Der Adaptive Kartentext (wie vom Benutzer ausgefüllt) wird über eine Nachricht an den bot gesendet, `task/submit invoke` Wenn der Benutzer eine `Action.Submit` Schaltfläche drückt.</span><span class="sxs-lookup"><span data-stu-id="70a52-143">The Adaptive card body (as filled in by the user) will be sent to the bot via a `task/submit invoke` message when the user presses an `Action.Submit` button.</span></span> <span data-ttu-id="70a52-144">Das Schema für das empfangene Objekt ähnelt [dem Schema, das Sie für Aufgaben/FETCH-und Task-/Submit-Nachrichten erhalten](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages). der einzige Unterschied besteht darin, dass das Schema des JSON-Objekts ein adaptives Kartenobjekt im Gegensatz zu einem Objekt ist, das ein adaptives Kartenobjekt *enthält* , als [Wenn Adaptive Karten mit Bots verwendet werden](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages).</span><span class="sxs-lookup"><span data-stu-id="70a52-144">The schema for the object you receive is very similar to [the schema you receive for task/fetch and task/submit messages](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages); the only difference is that the schema of the JSON object is an Adaptive card object as opposed to an object *containing* an Adaptive card object as [when Adaptive cards are used with bots](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages).</span></span>

## <a name="example-submitting-the-result-of-a-task-module"></a><span data-ttu-id="70a52-145">Beispiel: übermitteln des Ergebnisses eines Aufgabenmoduls</span><span class="sxs-lookup"><span data-stu-id="70a52-145">Example: submitting the result of a task module</span></span>

<span data-ttu-id="70a52-146">Rufen Sie das [Formular im obigen Aufgabenmodul](#example-invoking-a-task-module) mit einem HTML-Formular auf.</span><span class="sxs-lookup"><span data-stu-id="70a52-146">Recall the [form in the task module above](#example-invoking-a-task-module) with an HTML form.</span></span> <span data-ttu-id="70a52-147">Hier wird das Formular definiert:</span><span class="sxs-lookup"><span data-stu-id="70a52-147">Here's where the form is defined:</span></span>

```html
<form method="POST" id="customerForm" action="/register" onSubmit="return validateForm()">
```

<span data-ttu-id="70a52-148">Es gibt fünf Felder in diesem Formular, aber wir sind nur an den Werten von drei für dieses Beispiel interessiert: `name` , `email` und `favoriteBook` .</span><span class="sxs-lookup"><span data-stu-id="70a52-148">There are five fields on this form but we're only interested in the values of three of them for this example: `name`, `email`, and `favoriteBook`.</span></span>

<span data-ttu-id="70a52-149">Hier ist die `validateForm()` Funktion, die `submitTask()` Folgendes aufruft:</span><span class="sxs-lookup"><span data-stu-id="70a52-149">Here's the `validateForm()` function that calls `submitTask()`:</span></span>

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

## <a name="task-module-invocation-errors"></a><span data-ttu-id="70a52-150">Fehler beim Aufrufen des Aufgabenmoduls</span><span class="sxs-lookup"><span data-stu-id="70a52-150">Task module invocation errors</span></span>

<span data-ttu-id="70a52-151">Hier sind die möglichen Werte `err` , die von Ihrem empfangen werden können `submitHandler` :</span><span class="sxs-lookup"><span data-stu-id="70a52-151">Here are the possible values of `err` that can be received by your `submitHandler`:</span></span>

| <span data-ttu-id="70a52-152">Problem</span><span class="sxs-lookup"><span data-stu-id="70a52-152">Problem</span></span> | <span data-ttu-id="70a52-153">Fehlermeldung (Wert von `err` )</span><span class="sxs-lookup"><span data-stu-id="70a52-153">Error message (value of `err`)</span></span> |
| ------- | ------------------------------ |
| <span data-ttu-id="70a52-154">Werte für beide `TaskInfo.url` und `TaskInfo.card` wurden angegeben.</span><span class="sxs-lookup"><span data-stu-id="70a52-154">Values for both `TaskInfo.url` and `TaskInfo.card` were specified.</span></span> | <span data-ttu-id="70a52-155">"Die Werte für Karte und URL wurden angegeben.</span><span class="sxs-lookup"><span data-stu-id="70a52-155">"Values for both card and url were specified.</span></span> <span data-ttu-id="70a52-156">Die eine oder die andere, aber nicht beides, sind zulässig. "</span><span class="sxs-lookup"><span data-stu-id="70a52-156">One or the other, but not both, are allowed."</span></span> |
| <span data-ttu-id="70a52-157">Weder `TaskInfo.url` noch `TaskInfo.card` angegeben.</span><span class="sxs-lookup"><span data-stu-id="70a52-157">Neither `TaskInfo.url` nor `TaskInfo.card` specified.</span></span> | <span data-ttu-id="70a52-158">"Sie müssen einen Wert für die Karten-oder URL-Adresse angeben."</span><span class="sxs-lookup"><span data-stu-id="70a52-158">"You must specify a value for either card or url."</span></span> |
| <span data-ttu-id="70a52-159">Ungültig `appId` .</span><span class="sxs-lookup"><span data-stu-id="70a52-159">Invalid `appId`.</span></span> | <span data-ttu-id="70a52-160">"Ungültige Typkennung".</span><span class="sxs-lookup"><span data-stu-id="70a52-160">"Invalid appId."</span></span> |
| <span data-ttu-id="70a52-161">Der Benutzer hat die X-Schaltfläche gedrückt und geschlossen.</span><span class="sxs-lookup"><span data-stu-id="70a52-161">User pressed X button, closing it.</span></span> | <span data-ttu-id="70a52-162">"Benutzer hat den Aufgabenmodul storniert/geschlossen."</span><span class="sxs-lookup"><span data-stu-id="70a52-162">"User cancelled/closed the task module."</span></span> |
