---
title: Verwenden von Aufgaben Modulen in Microsoft Teams-Bots
description: Vorgehensweise verwenden von Aufgaben Modulen mit Microsoft Teams-Bots, einschließlich bot-Framework-Karten, Adaptive Karten und Deep Links.
keywords: Aufgaben Module-Bots für Teams
ms.openlocfilehash: 09b0ede85c613d5724c6ecddbccd2a59c43cad74
ms.sourcegitcommit: 6c5c0574228310f844c81df0d57f11e2037e90c8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2020
ms.locfileid: "42228094"
---
# <a name="using-task-modules-from-microsoft-teams-bots"></a><span data-ttu-id="d1960-104">Verwenden von Aufgaben Modulen von Microsoft Teams-Bots</span><span class="sxs-lookup"><span data-stu-id="d1960-104">Using task modules from Microsoft Teams bots</span></span>

<span data-ttu-id="d1960-105">Aufgaben Module können von Microsoft Teams-Bots mithilfe von Schaltflächen auf adaptiven Karten und bot-Framework-Karten (Hero, Thumbnail und Office 365-Konnektor) aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="d1960-105">Task modules can be invoked from Microsoft Teams bots using buttons on Adaptive cards and Bot Framework cards (Hero, Thumbnail, and Office 365 Connector).</span></span> <span data-ttu-id="d1960-106">Aufgaben Module sind häufig eine bessere Benutzeroberfläche als mehrere Unterhaltungs Schritte, bei denen Sie als Entwickler den Status von bot überwachen und dem Benutzer die Unterbrechung/Absage der Sequenz ermöglichen müssen.</span><span class="sxs-lookup"><span data-stu-id="d1960-106">Task modules are often a better user experience than multiple conversation steps where you as a developer have to keep track of bot state and allow the user to interrupt/cancel the sequence.</span></span>

<span data-ttu-id="d1960-107">Es gibt zwei Möglichkeiten zum Aufrufen von Aufgaben Modulen:</span><span class="sxs-lookup"><span data-stu-id="d1960-107">There are two ways of invoking task modules:</span></span>

* <span data-ttu-id="d1960-108">**Eine neue Art von Invoke- `task/fetch`Nachricht.**</span><span class="sxs-lookup"><span data-stu-id="d1960-108">**A new kind of invoke message `task/fetch`.**</span></span> <span data-ttu-id="d1960-109">Wenn Sie `invoke` die Karten [Aktion](~/task-modules-and-cards/cards/cards-actions.md#invoke) für bot-Framework-Karten `Action.Submit` verwenden oder die Karten [Aktion](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) für Adaptive Karten mit `task/fetch`, wird das Aufgabenmodul (entweder eine URL oder eine Adaptive Karte) dynamisch von Ihrem bot abgerufen.</span><span class="sxs-lookup"><span data-stu-id="d1960-109">Using the `invoke` [card action](~/task-modules-and-cards/cards/cards-actions.md#invoke) for Bot Framework cards, or the `Action.Submit` [card action](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) for Adaptive cards, with `task/fetch`, the task module (either a URL or an Adaptive card) is fetched dynamically from your bot.</span></span>
* <span data-ttu-id="d1960-110">**Deep Link-URLs.**</span><span class="sxs-lookup"><span data-stu-id="d1960-110">**Deep link URLs.**</span></span> <span data-ttu-id="d1960-111">Mithilfe der [Deep Link-Syntax für Aufgaben Module](~/task-modules-and-cards/what-are-task-modules.md#task-module-deep-link-syntax)können Sie die `openUrl` Karten [Aktion](~/task-modules-and-cards/cards/cards-actions.md#openurl) für bot-frameworkkarten oder die `Action.OpenUrl` [Karten Aktion](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) für Adaptive Karten verwenden.</span><span class="sxs-lookup"><span data-stu-id="d1960-111">Using the [deep link syntax for task modules](~/task-modules-and-cards/what-are-task-modules.md#task-module-deep-link-syntax), you can use the `openUrl` [card action](~/task-modules-and-cards/cards/cards-actions.md#openurl) for Bot Framework cards or the `Action.OpenUrl` [card action](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) for Adaptive cards, respectively.</span></span> <span data-ttu-id="d1960-112">Bei Deep Link-URLs ist die URL des Aufgabenmoduls oder der Adaptive Kartentext offensichtlich vorab bekannt, sodass ein Server- `task/fetch`Roundtrip relativ zu vermieden wird.</span><span class="sxs-lookup"><span data-stu-id="d1960-112">With deep link URLs, the task module URL or Adaptive card body is obviously known in advance, avoiding a server round-trip relative to `task/fetch`.</span></span>

## <a name="invoking-a-task-module-via-taskfetch"></a><span data-ttu-id="d1960-113">Aufrufen eines Aufgabenmoduls über Task/FETCH</span><span class="sxs-lookup"><span data-stu-id="d1960-113">Invoking a task module via task/fetch</span></span>

<span data-ttu-id="d1960-114">Wenn das `value` Objekt der `invoke` Karte auf Ordnungs `Action.Submit` gemäße Weise initialisiert wird (im folgenden näher erläutert), wird beim Drücken der Schaltfläche eine `invoke` Nachricht an den bot gesendet.</span><span class="sxs-lookup"><span data-stu-id="d1960-114">When the `value` object of the `invoke` card action or `Action.Submit` is initialized in the proper way (explained in more detail below), when a user presses the button an `invoke` message is sent to the bot.</span></span> <span data-ttu-id="d1960-115">In der HTTP-Antwort auf `invoke` die Nachricht gibt es ein [taskinfo-Objekt](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) , das in ein Wrapperobjekt eingebettet ist, das die Teams zum Anzeigen des Aufgabenmoduls verwenden.</span><span class="sxs-lookup"><span data-stu-id="d1960-115">In the HTTP response to the `invoke` message, there's a [TaskInfo object](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) embedded in a wrapper object, which Teams uses to display the task module.</span></span>

![Aufgabe/Abrufanforderung/Antwort](~/assets/images/task-module/task-module-invoke-request-response.png)

<span data-ttu-id="d1960-117">Lassen Sie uns die einzelnen Schritte etwas ausführlicher betrachten:</span><span class="sxs-lookup"><span data-stu-id="d1960-117">Let's look at each step in a bit more detail:</span></span>

1. <span data-ttu-id="d1960-118">In diesem Beispiel wird eine Hero-Karte für bot-Frameworks `invoke` mit einer "Buy"- [Karten Aktion](~/task-modules-and-cards/cards/cards-actions.md#invoke)gezeigt.</span><span class="sxs-lookup"><span data-stu-id="d1960-118">This example shows a Bot Framework Hero card with a "Buy" `invoke` [card action](~/task-modules-and-cards/cards/cards-actions.md#invoke).</span></span> <span data-ttu-id="d1960-119">Der Wert der `type` Eigenschaft ist `task/fetch` -der Rest des `value` Objekts kann sein, was Sie möchten.</span><span class="sxs-lookup"><span data-stu-id="d1960-119">The value of the `type` property is `task/fetch` - the rest of the `value` object can be whatever you like.</span></span>
2. <span data-ttu-id="d1960-120">Der bot erhält die `invoke` HTTP-Post-Nachricht.</span><span class="sxs-lookup"><span data-stu-id="d1960-120">The bot receives the `invoke` HTTP POST message.</span></span>
3. <span data-ttu-id="d1960-121">Der bot erstellt ein Response-Objekt und gibt es im Text der Post-Antwort mit einem HTTP 200-Antwortcode zurück.</span><span class="sxs-lookup"><span data-stu-id="d1960-121">The bot creates a response object and returns it in the body of the POST response with an HTTP 200 response code.</span></span> <span data-ttu-id="d1960-122">Das Schema für Antworten wird [im folgenden in der Diskussion über Aufgabe/Submit](#the-flexibility-of-tasksubmit)beschrieben, aber wichtig ist jetzt, dass der Text der HTTP-Antwort ein [taskinfo-Objekt](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) enthält, das in ein Wrapperobjekt eingebettet ist, beispielsweise:</span><span class="sxs-lookup"><span data-stu-id="d1960-122">The schema for responses is described [below in the discussion on task/submit](#the-flexibility-of-tasksubmit), but the important thing to remember now is that the body of the HTTP response contains a [TaskInfo object](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) embedded in a wrapper object, e.g.:</span></span>

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
    
    <span data-ttu-id="d1960-123">Das `task/fetch` Ereignis und seine Antwort auf Bots ähneln konzeptuell der `microsoftTeams.tasks.startTask()` Funktion im Client-SDK.</span><span class="sxs-lookup"><span data-stu-id="d1960-123">The `task/fetch` event and its response for bots is similar, conceptually, to the `microsoftTeams.tasks.startTask()` function in the client SDK.</span></span>
4. <span data-ttu-id="d1960-124">Microsoft Teams zeigt den Aufgabenmodul an.</span><span class="sxs-lookup"><span data-stu-id="d1960-124">Microsoft Teams displays the task module.</span></span>

## <a name="submitting-the-result-of-a-task-module"></a><span data-ttu-id="d1960-125">Übermitteln des Ergebnisses eines Aufgabenmoduls</span><span class="sxs-lookup"><span data-stu-id="d1960-125">Submitting the result of a task module</span></span>

<span data-ttu-id="d1960-126">Wenn der Benutzer mit dem Aufgabenmodul fertig ist, ist das Senden des Ergebnisses zurück an den bot ähnlich wie [bei Registerkarten](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-submitting-the-result-of-a-task-module), es gibt jedoch einige Unterschiede, die daher auch hier beschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="d1960-126">When the user is finished with the task module, submitting the result back to the bot is similar [to the way it works with tabs](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-submitting-the-result-of-a-task-module), but there are a few differences, so it's described here too.</span></span>

* <span data-ttu-id="d1960-127">**HTML/JavaScript (`TaskInfo.url`)**.</span><span class="sxs-lookup"><span data-stu-id="d1960-127">**HTML/JavaScript (`TaskInfo.url`)**.</span></span> <span data-ttu-id="d1960-128">Nachdem Sie überprüft haben, was der Benutzer eingegeben hat, rufen Sie `microsoftTeams.tasks.submitTask()` die SDK-Funktion auf (wird `submitTask()` im folgenden als Zweck der Lesbarkeit bezeichnet).</span><span class="sxs-lookup"><span data-stu-id="d1960-128">Once you've validated what the user has entered, you call the `microsoftTeams.tasks.submitTask()` SDK function (referred to hereafter as `submitTask()` for readability purposes).</span></span> <span data-ttu-id="d1960-129">Sie können ohne `submitTask()` Parameter aufrufen, wenn Sie lediglich möchten, dass Teams den Aufgabenmodul schließen, aber in den meisten Fällen möchten Sie ein Objekt oder eine Zeichenfolge an Ihren `submitHandler`übergeben.</span><span class="sxs-lookup"><span data-stu-id="d1960-129">You can call `submitTask()` without any parameters if you just want Teams to close the task module, but most of the time you'll want to pass an object or a string to your `submitHandler`.</span></span> <span data-ttu-id="d1960-130">Übergeben Sie es einfach als ersten Parameter, `result`.</span><span class="sxs-lookup"><span data-stu-id="d1960-130">Simply pass it as the first parameter, `result`.</span></span> <span data-ttu-id="d1960-131">Teams werden aufgerufen `submitHandler`: `err` wird `null` und `result` ist das Objekt/die Zeichenfolge, die Sie `submitTask()`an übergeben haben.</span><span class="sxs-lookup"><span data-stu-id="d1960-131">Teams will invoke `submitHandler`: `err` will be `null` and `result` will be the object/string you passed to `submitTask()`.</span></span> <span data-ttu-id="d1960-132">Wenn Sie einen `submitTask()` `result` Parameter aufrufen, **müssen** Sie ein `appId` oder ein Array von `appId` Zeichenfolgen übergeben: Dadurch können Teams überprüfen, ob die APP, die das Ergebnis sendet, dieselbe ist, die das Aufgabenmodul aufgerufen hat.</span><span class="sxs-lookup"><span data-stu-id="d1960-132">If you do call `submitTask()` with a `result` parameter, you **must** pass an `appId` or an array of `appId` strings: this allows Teams to validate that the app sending the result is the same one which invoked the task module.</span></span> <span data-ttu-id="d1960-133">Ihr bot erhält eine `task/submit` Nachricht `result` wie [unten](#payload-of-taskfetch-and-tasksubmit-messages)beschrieben.</span><span class="sxs-lookup"><span data-stu-id="d1960-133">Your bot will receive a `task/submit` message including `result` as described [below](#payload-of-taskfetch-and-tasksubmit-messages).</span></span>
* <span data-ttu-id="d1960-134">**Adaptive Karte`TaskInfo.card`()**.</span><span class="sxs-lookup"><span data-stu-id="d1960-134">**Adaptive card (`TaskInfo.card`)**.</span></span> <span data-ttu-id="d1960-135">Der Adaptive Kartentext (wie vom Benutzer ausgefüllt) wird über eine `task/submit` Nachricht an den bot gesendet, wenn der Benutzer eine beliebige `Action.Submit` Schaltfläche drückt.</span><span class="sxs-lookup"><span data-stu-id="d1960-135">The Adaptive card body (as filled in by the user) will be sent to the bot via a `task/submit` message when the user presses any `Action.Submit` button.</span></span>

## <a name="the-flexibility-of-tasksubmit"></a><span data-ttu-id="d1960-136">Flexibilität von Task/Submit</span><span class="sxs-lookup"><span data-stu-id="d1960-136">The flexibility of task/submit</span></span>

<span data-ttu-id="d1960-137">Im vorherigen Abschnitt haben Sie gelernt, dass der bot immer eine `task/submit invoke` Nachricht erhält, wenn der Benutzer mit einem Aufgabenmodul endet, das von einem bot aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="d1960-137">In the previous section, you learned that when the user finishes with a task module invoked from a bot, the bot always receives a `task/submit invoke` message.</span></span> <span data-ttu-id="d1960-138">Als Entwickler haben Sie mehrere Möglichkeiten, wenn Sie \*\* auf die `task/submit` Nachricht reagieren:</span><span class="sxs-lookup"><span data-stu-id="d1960-138">As a developer, you have several options when *responding* to the `task/submit` message:</span></span>

| <span data-ttu-id="d1960-139">HTTP-Text Antwort</span><span class="sxs-lookup"><span data-stu-id="d1960-139">HTTP Body Response</span></span>                      | <span data-ttu-id="d1960-140">Szenario</span><span class="sxs-lookup"><span data-stu-id="d1960-140">Scenario</span></span>                                |
| --------------------------------------- | --------------------------------------- |
| <span data-ttu-id="d1960-141">None ( `task/submit` Nachricht ignorieren)</span><span class="sxs-lookup"><span data-stu-id="d1960-141">None (ignore the `task/submit` message)</span></span> | <span data-ttu-id="d1960-142">Die einfachste Antwort ist überhaupt keine Antwort.</span><span class="sxs-lookup"><span data-stu-id="d1960-142">The simplest response is no response at all.</span></span> <span data-ttu-id="d1960-143">Ihr bot muss nicht Antworten, wenn der Benutzer mit dem Aufgabenmodul fertig ist.</span><span class="sxs-lookup"><span data-stu-id="d1960-143">Your bot is not required to respond when the user is finished with the task module.</span></span> |
| <pre>{<br/>  "task": {<br/>    "type": "message",<br/>    "value": "Message text"<br/>  }<br/>}</pre> | <span data-ttu-id="d1960-144">`value` In Microsoft Teams wird der Wert in einem Popupmeldungsfeld angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d1960-144">Teams will display the value of `value` in a popup message box.</span></span> |
| <pre>{<br/>  "task": {<br/>    "type": "continue",<br/>    "value": &lt;TaskInfo object&gt;<br/>  }<br/>}</pre> | <span data-ttu-id="d1960-145">Ermöglicht es Ihnen, Sequenzen von adaptiven Karten in einer Assistenten-/mehrstufigen Umgebung zu "verketten".</span><span class="sxs-lookup"><span data-stu-id="d1960-145">Allows you to "chain" sequences of Adaptive cards together in a wizard/multi-step experience.</span></span> <span data-ttu-id="d1960-146">_Beachten Sie, dass das Verketten von adaptiven Karten in eine Sequenz ein erweitertes Szenario ist und hier nicht dokumentiert ist. Die Beispiel-App Node. js unterstützt Sie jedoch und wie Sie funktioniert, ist in [der Readme.MD-Datei](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs#implementation-notes)dokumentiert._</span><span class="sxs-lookup"><span data-stu-id="d1960-146">_Note that chaining Adaptive cards into a sequence is an advanced scenario and not documented here. The Node.js sample app supports it, however, and how it works is documented in [its README.md file](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs#implementation-notes)._</span></span> |

## <a name="payload-of-taskfetch-and-tasksubmit-messages"></a><span data-ttu-id="d1960-147">Nutzlast von Task/FETCH und Task/Submit-Nachrichten</span><span class="sxs-lookup"><span data-stu-id="d1960-147">Payload of task/fetch and task/submit messages</span></span>

<span data-ttu-id="d1960-148">Dieser Abschnitt definiert das Schema dessen, was Ihr bot erhält, wenn er `task/fetch` ein `task/submit` oder bot `Activity` Framework-Objekt empfängt.</span><span class="sxs-lookup"><span data-stu-id="d1960-148">This section defines the schema of what your bot receives when it receives a `task/fetch` or `task/submit` Bot Framework `Activity` object.</span></span> <span data-ttu-id="d1960-149">Die wichtige obere Ebene wird unten angezeigt:</span><span class="sxs-lookup"><span data-stu-id="d1960-149">The important top-level appear below:</span></span>

| <span data-ttu-id="d1960-150">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="d1960-150">Property</span></span> | <span data-ttu-id="d1960-151">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d1960-151">Description</span></span>                          |
| -------- | ------------------------------------ |
| `type`   | <span data-ttu-id="d1960-152">Wird immer`invoke`</span><span class="sxs-lookup"><span data-stu-id="d1960-152">Will always be `invoke`</span></span>              |
| `name`   | <span data-ttu-id="d1960-153">Entweder `task/fetch` oder`task/submit`</span><span class="sxs-lookup"><span data-stu-id="d1960-153">Either `task/fetch` or `task/submit`</span></span> |
| `value`  | <span data-ttu-id="d1960-154">Die vom Entwickler definierte Nutzlast.</span><span class="sxs-lookup"><span data-stu-id="d1960-154">The developer-defined payload.</span></span> <span data-ttu-id="d1960-155">Normalerweise spiegelt die `value` Struktur des Objekts das, was von Teams gesendet wurde.</span><span class="sxs-lookup"><span data-stu-id="d1960-155">Normally the structure of the `value` object mirrors what was sent from Teams.</span></span> <span data-ttu-id="d1960-156">In diesem Fall ist es jedoch anders, da wir Dynamic FETCH (`task/fetch`) sowohl von bot-Framework (`value`) als auch von Adaptive Card `Action.Submit` -Aktionen`data`() unterstützen möchten, und wir benötigen eine `context` Möglichkeit, Teams mit dem bot zu kommunizieren, zusätzlich `value` / `data`zu dem, was in enthalten war.</span><span class="sxs-lookup"><span data-stu-id="d1960-156">In this case, however, it's different because we want to support dynamic fetch (`task/fetch`) from both Bot Framework (`value`) and Adaptive card `Action.Submit` actions (`data`), and we need a way to communicate Teams `context` to the bot in addition to what was included in `value`/`data`.</span></span><br/><br/><span data-ttu-id="d1960-157">Dies erfolgt durch Kombinieren der beiden Elemente in einem übergeordneten Objekt:</span><span class="sxs-lookup"><span data-stu-id="d1960-157">We do this by combining the two into a parent object:</span></span><br/><br/><pre>{<br/>  "context": {<br/>    "theme": "default" &vert; "dark" &vert; "contrast",<br/>  },<br/>  "data": [value field from Bot Framework card] &vert; [data field from Adaptive Card] <br/>}</pre>  |

## <a name="example-receiving-and-responding-to-taskfetch-and-tasksubmit-invoke-messages---nodejs"></a><span data-ttu-id="d1960-158">Beispiel: empfangen und reagieren auf Tasks/FETCH-und Task/Submit-Invoke-Nachrichten-Node. js</span><span class="sxs-lookup"><span data-stu-id="d1960-158">Example: Receiving and responding to task/fetch and task/submit invoke messages - Node.js</span></span>

> [!NOTE]
> <span data-ttu-id="d1960-159">Der folgende Beispielcode wurde zwischen der technischen Vorschau und der endgültigen Version dieses Features geändert: das Schema der `task/fetch` Anforderung wurde geändert, um zu verfolgen, was [im vorherigen Abschnitt dokumentiert](#payload-of-taskfetch-and-tasksubmit-messages)wurde.</span><span class="sxs-lookup"><span data-stu-id="d1960-159">The sample code below was modified between Technical Preview and final release of this feature: the schema of the `task/fetch` request changed to follow what was [documented in the previous section](#payload-of-taskfetch-and-tasksubmit-messages).</span></span> <span data-ttu-id="d1960-160">Das heißt, die Dokumentation war richtig, aber die Implementierung war nicht.</span><span class="sxs-lookup"><span data-stu-id="d1960-160">That is, the documentation was correct but the implementation was not.</span></span> <span data-ttu-id="d1960-161">In den `// for Technical Preview [...]` Kommentaren unten finden Sie Informationen zu den geänderten Funktionen.</span><span class="sxs-lookup"><span data-stu-id="d1960-161">See the `// for Technical Preview [...]` comments below for what changed.</span></span>

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

<span data-ttu-id="d1960-162">*Siehe auch* [Microsoft Teams-Beispielcode für Aufgaben Module –](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs/blob/master/src/TeamsBot.ts) Beispiele für nodejs und [bot-Framework](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).</span><span class="sxs-lookup"><span data-stu-id="d1960-162">*See also*, [Microsoft Teams task module sample code — nodejs](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs/blob/master/src/TeamsBot.ts) and  [Bot Framework samples](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).</span></span>

## <a name="example-receiving-and-responding-to-taskfetch-and-tasksubmit-invoke-messages---c"></a><span data-ttu-id="d1960-163">Beispiel: empfangen und reagieren auf Tasks/FETCH-und Task/Submit-Invoke-Nachrichten-C #</span><span class="sxs-lookup"><span data-stu-id="d1960-163">Example: Receiving and responding to task/fetch and task/submit invoke messages - C#</span></span>

<span data-ttu-id="d1960-164">In C#-Bots `invoke` werden Nachrichten von einem `HttpResponseMessage()` Controller verarbeitet, `Activity` der eine Nachricht verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="d1960-164">In C# bots, `invoke` messages are processed by an `HttpResponseMessage()` controller processing an `Activity` message.</span></span> <span data-ttu-id="d1960-165">Die `task/fetch` `task/submit` Anforderungen und Antworten sind JSON.</span><span class="sxs-lookup"><span data-stu-id="d1960-165">The `task/fetch` and `task/submit` requests and responses are JSON.</span></span> <span data-ttu-id="d1960-166">In C# ist es nicht so bequem, mit RAW-JSON wie in Node. js umzugehen, sodass Sie Wrapperklassen benötigen, um die Serialisierung von und zu JSON zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="d1960-166">In C#, it's not as convenient to deal with raw JSON as it is in Node.js, so you need wrapper classes to handle the serialization to and from JSON.</span></span> <span data-ttu-id="d1960-167">Es gibt noch keine direkte Unterstützung dafür im Microsoft Teams [C# SDK](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) , aber Sie sehen ein Beispiel dafür, wie diese einfachen Wrapperklassen in der c#-Beispiel- [App](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Models/TaskModel.cs)aussehen würden.</span><span class="sxs-lookup"><span data-stu-id="d1960-167">There's no direct support for this in the Microsoft Teams [C# SDK](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) yet, but you can see an example of what these simple wrapper classes would look like in the [C# sample app](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Models/TaskModel.cs).</span></span>

<span data-ttu-id="d1960-168">Im folgenden finden Sie Beispielcode in C# `task/fetch` zur `task/submit` Behandlung und Nachrichten mit diesen`TaskInfo`Wrapper `TaskEnvelope`Klassen (,), die aus dem [Beispiel](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs)entnommen wurden:</span><span class="sxs-lookup"><span data-stu-id="d1960-168">Below is example code in C# for handling `task/fetch` and `task/submit` messages using these wrapper classes (`TaskInfo`, `TaskEnvelope`), excerpted from the [sample](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs):</span></span>

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

<span data-ttu-id="d1960-169">Im obigen Beispiel nicht dargestellt `SetTaskInfo()` ist die-Funktion, die die `height`, `width`und `title` die Eigenschaften des `TaskInfo` Objekts für jeden Fall festlegt.</span><span class="sxs-lookup"><span data-stu-id="d1960-169">Not shown in the above example is the `SetTaskInfo()` function, which sets the `height`, `width`, and `title` properties of the `TaskInfo` object for each case.</span></span> <span data-ttu-id="d1960-170">Hier ist der [Quellcode für SetTaskInfo ()](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs).</span><span class="sxs-lookup"><span data-stu-id="d1960-170">Here's the [source code for SetTaskInfo()](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs).</span></span>

### <a name="bot-framework-card-actions-vs-adaptive-card-actionsubmit-actions"></a><span data-ttu-id="d1960-171">Bot-Framework-Karten Aktionen vs. Adaptive Karten Aktion. Submit-Aktionen</span><span class="sxs-lookup"><span data-stu-id="d1960-171">Bot Framework card actions vs. Adaptive card Action.Submit actions</span></span>

<span data-ttu-id="d1960-172">Das Schema für Aktionen von bot-Framework-Karten unterscheidet `Action.Submit` sich geringfügig von adaptiven Karten Aktionen.</span><span class="sxs-lookup"><span data-stu-id="d1960-172">The schema for Bot Framework card actions is slightly different from Adaptive card `Action.Submit` actions.</span></span> <span data-ttu-id="d1960-173">Dadurch unterscheidet sich auch die Möglichkeit zum Aufrufen von Aufgaben Modulen geringfügig: `data` das Objekt `Action.Submit` in enthält `msteams` ein Objekt, sodass es nicht mit anderen Eigenschaften in der Karte in Konflikt kommt.</span><span class="sxs-lookup"><span data-stu-id="d1960-173">As a result, the way to invoke task modules is slightly different too: the `data` object in `Action.Submit` contains an `msteams` object so it won't interfere with other properties in the card.</span></span> <span data-ttu-id="d1960-174">Die folgende Tabelle zeigt ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="d1960-174">The following table shows an example of each:</span></span>

| <span data-ttu-id="d1960-175">Bot-Framework-Karten Aktion</span><span class="sxs-lookup"><span data-stu-id="d1960-175">Bot Framework card action</span></span>                              | <span data-ttu-id="d1960-176">Adaptive Karten Aktion. Submit-Aktion</span><span class="sxs-lookup"><span data-stu-id="d1960-176">Adaptive card Action.Submit action</span></span>                     |
| ------------------------------------------------------ | ------------------------------------------------------ |
| <pre>{<br/>  "type": "invoke",<br/>  "title": "Buy",<br/>  "value": {<br/>    "type": "task/fetch",<br/>    &lt;...&gt;<br/>  }<br/>}</pre> | <pre>{<br/>  "type": "Action.Submit",<br/>  "id": "btnBuy",<br/>  "title": "Buy",<br/>  "data": {<br/>    &lt;...&gt;,<br/>    "msteams": {<br/>      "type": "task/fetch"<br/>    }<br/>  }<br/>}</pre>  |
