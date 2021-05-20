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
# <a name="using-task-modules-from-microsoft-teams-bots"></a><span data-ttu-id="fe992-104">Verwenden von Task-Modulen aus Microsoft Teams Bots</span><span class="sxs-lookup"><span data-stu-id="fe992-104">Using task modules from Microsoft Teams bots</span></span>

<span data-ttu-id="fe992-105">Task-Module können von Microsoft Teams Bots mithilfe von Schaltflächen auf Adaptive-Karten und Bot Framework-Karten (Hero, Thumbnail und Office 365 Connector) aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="fe992-105">Task modules can be invoked from Microsoft Teams bots using buttons on Adaptive cards and Bot Framework cards (Hero, Thumbnail, and Office 365 Connector).</span></span> <span data-ttu-id="fe992-106">Aufgabenmodule sind oft eine bessere Benutzererfahrung als mehrere Unterhaltungsschritte, bei denen Sie als Entwickler den Bot-Status nachverfolgen und dem Benutzer erlauben müssen, die Sequenz zu unterbrechen/abzubrechen.</span><span class="sxs-lookup"><span data-stu-id="fe992-106">Task modules are often a better user experience than multiple conversation steps where you as a developer have to keep track of bot state and allow the user to interrupt/cancel the sequence.</span></span>

<span data-ttu-id="fe992-107">Es gibt zwei Möglichkeiten, Aufgabenmodule aufzuberufen:</span><span class="sxs-lookup"><span data-stu-id="fe992-107">There are two ways of invoking task modules:</span></span>

* <span data-ttu-id="fe992-108">**Eine neue Art von Aufrufnachricht `task/fetch` .**</span><span class="sxs-lookup"><span data-stu-id="fe992-108">**A new kind of invoke message `task/fetch`.**</span></span> <span data-ttu-id="fe992-109">Mit der `invoke` [Kartenaktion](~/task-modules-and-cards/cards/cards-actions.md#invoke) für Bot Framework-Karten oder der `Action.Submit` [Kartenaktion](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) für Adaptive-Karten wird `task/fetch` das Taskmodul (entweder eine URL oder eine adaptive Karte) dynamisch von Ihrem Bot abgerufen.</span><span class="sxs-lookup"><span data-stu-id="fe992-109">Using the `invoke` [card action](~/task-modules-and-cards/cards/cards-actions.md#invoke) for Bot Framework cards, or the `Action.Submit` [card action](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) for Adaptive cards, with `task/fetch`, the task module (either a URL or an Adaptive card) is fetched dynamically from your bot.</span></span>
* <span data-ttu-id="fe992-110">**Deep link URLs.**</span><span class="sxs-lookup"><span data-stu-id="fe992-110">**Deep link URLs.**</span></span> <span data-ttu-id="fe992-111">Mithilfe der [Deep Link-Syntax für Aufgabenmodule](~/task-modules-and-cards/what-are-task-modules.md#task-module-deep-link-syntax)können Sie die `openUrl` [Kartenaktion](~/task-modules-and-cards/cards/cards-actions.md#openurl) für Bot Framework-Karten bzw. die `Action.OpenUrl` [Kartenaktion](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) für Adaptive-Karten verwenden.</span><span class="sxs-lookup"><span data-stu-id="fe992-111">Using the [deep link syntax for task modules](~/task-modules-and-cards/what-are-task-modules.md#task-module-deep-link-syntax), you can use the `openUrl` [card action](~/task-modules-and-cards/cards/cards-actions.md#openurl) for Bot Framework cards or the `Action.OpenUrl` [card action](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) for Adaptive cards, respectively.</span></span> <span data-ttu-id="fe992-112">Mit Deep Link URLs ist die URL des Taskmoduls oder der Adaptive-Kartentext offensichtlich im Voraus bekannt, wodurch ein Server-Roundtrip relativ zu vermieden `task/fetch` wird.</span><span class="sxs-lookup"><span data-stu-id="fe992-112">With deep link URLs, the task module URL or Adaptive card body is obviously known in advance, avoiding a server round-trip relative to `task/fetch`.</span></span>

>[!IMPORTANT]
><span data-ttu-id="fe992-113">Um eine sichere Kommunikation zu gewährleisten, müssen die `url` einzelnen und müssen das `fallbackUrl` HTTPS-Verschlüsselungsprotokoll implementieren.</span><span class="sxs-lookup"><span data-stu-id="fe992-113">To ensure secure communications, each `url` and `fallbackUrl` must implement the HTTPS encryption protocol.</span></span>

## <a name="invoking-a-task-module-through-taskfetch"></a><span data-ttu-id="fe992-114">Aufrufen eines Aufgabenmoduls durch Aufgabe/Abruf</span><span class="sxs-lookup"><span data-stu-id="fe992-114">Invoking a task module through task/fetch</span></span>

<span data-ttu-id="fe992-115">Wenn das `value` Objekt der `invoke` Kartenaktion oder in der richtigen Weise `Action.Submit` initialisiert wird (weiter unten ausführlicher erläutert), wenn ein Benutzer die Taste drückt, wird eine `invoke` Nachricht an den Bot gesendet.</span><span class="sxs-lookup"><span data-stu-id="fe992-115">When the `value` object of the `invoke` card action or `Action.Submit` is initialized in the proper way (explained in more detail below), when a user presses the button an `invoke` message is sent to the bot.</span></span> <span data-ttu-id="fe992-116">In der HTTP-Antwort auf die `invoke` Nachricht befindet sich ein [TaskInfo-Objekt,](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) das in ein Wrapperobjekt eingebettet ist und Teams zum Anzeigen des Taskmoduls verwendet.</span><span class="sxs-lookup"><span data-stu-id="fe992-116">In the HTTP response to the `invoke` message, there's a [TaskInfo object](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) embedded in a wrapper object, which Teams uses to display the task module.</span></span>

![Task/Fetch-Anforderung/Antwort](~/assets/images/task-module/task-module-invoke-request-response.png)

<span data-ttu-id="fe992-118">Sehen wir uns jeden Schritt etwas genauer an:</span><span class="sxs-lookup"><span data-stu-id="fe992-118">Let's look at each step in a bit more detail:</span></span>

1. <span data-ttu-id="fe992-119">Dieses Beispiel zeigt eine Bot Framework Hero-Karte mit einer `invoke` ["Buy"-Kartenaktion](~/task-modules-and-cards/cards/cards-actions.md#invoke).</span><span class="sxs-lookup"><span data-stu-id="fe992-119">This example shows a Bot Framework Hero card with a "Buy" `invoke` [card action](~/task-modules-and-cards/cards/cards-actions.md#invoke).</span></span> <span data-ttu-id="fe992-120">Der Wert der `type` Eigenschaft ist - der Rest des `task/fetch` `value` Objekts kann sein, was Sie mögen.</span><span class="sxs-lookup"><span data-stu-id="fe992-120">The value of the `type` property is `task/fetch` - the rest of the `value` object can be whatever you like.</span></span>
1. <span data-ttu-id="fe992-121">Der Bot empfängt die `invoke` HTTP POST-Nachricht.</span><span class="sxs-lookup"><span data-stu-id="fe992-121">The bot receives the `invoke` HTTP POST message.</span></span>
1. <span data-ttu-id="fe992-122">Der Bot erstellt ein Antwortobjekt und gibt es im Text der POST-Antwort mit einem HTTP 200-Antwortcode zurück.</span><span class="sxs-lookup"><span data-stu-id="fe992-122">The bot creates a response object and returns it in the body of the POST response with an HTTP 200 response code.</span></span> <span data-ttu-id="fe992-123">Das Schema für Antworten wird [unten in der Diskussion über task/submit](#the-flexibility-of-tasksubmit)beschrieben, aber das Wichtige, was Sie sich jetzt merken sollten, ist, dass der Text der HTTP-Antwort ein [TaskInfo-Objekt](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) enthält, das in ein Wrapperobjekt eingebettet ist.</span><span class="sxs-lookup"><span data-stu-id="fe992-123">The schema for responses is described [below in the discussion on task/submit](#the-flexibility-of-tasksubmit), but the important thing to remember now is that the body of the HTTP response contains a [TaskInfo object](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) embedded in a wrapper object.</span></span> <span data-ttu-id="fe992-124">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="fe992-124">For example:</span></span>

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

    <span data-ttu-id="fe992-125">Das `task/fetch` Ereignis und seine Reaktion für Bots ist konzeptionell der Funktion im `microsoftTeams.tasks.startTask()` Client-SDK ähnlich.</span><span class="sxs-lookup"><span data-stu-id="fe992-125">The `task/fetch` event and its response for bots is similar, conceptually, to the `microsoftTeams.tasks.startTask()` function in the client SDK.</span></span>
1. <span data-ttu-id="fe992-126">Microsoft Teams zeigt das Aufgabenmodul an.</span><span class="sxs-lookup"><span data-stu-id="fe992-126">Microsoft Teams displays the task module.</span></span>

## <a name="submitting-the-result-of-a-task-module"></a><span data-ttu-id="fe992-127">Übermitteln des Ergebnisses eines Aufgabenmoduls</span><span class="sxs-lookup"><span data-stu-id="fe992-127">Submitting the result of a task module</span></span>

<span data-ttu-id="fe992-128">Wenn der Benutzer mit dem Taskmodul fertig ist, ist das Senden des Ergebnisses an den Bot ähnlich [wie bei Registerkarten,](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-submitting-the-result-of-a-task-module)aber es gibt ein paar Unterschiede, so dass es auch hier beschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="fe992-128">When the user is finished with the task module, submitting the result back to the bot is similar [to the way it works with tabs](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-submitting-the-result-of-a-task-module), but there are a few differences, so it's described here too.</span></span>

* <span data-ttu-id="fe992-129">**HTML/JavaScript ( `TaskInfo.url` )**.</span><span class="sxs-lookup"><span data-stu-id="fe992-129">**HTML/JavaScript (`TaskInfo.url`)**.</span></span> <span data-ttu-id="fe992-130">Nachdem Sie überprüft haben, was der Benutzer eingegeben hat, rufen Sie die `microsoftTeams.tasks.submitTask()` SDK-Funktion auf (im Folgenden als aus Gründen der `submitTask()` Lesbarkeit bezeichnet).</span><span class="sxs-lookup"><span data-stu-id="fe992-130">Once you've validated what the user has entered, you call the `microsoftTeams.tasks.submitTask()` SDK function (referred to hereafter as `submitTask()` for readability purposes).</span></span> <span data-ttu-id="fe992-131">Sie können ohne Parameter aufrufen, wenn Sie nur möchten, `submitTask()` dass Teams das Aufgabenmodul schließen möchten, aber die meiste Zeit ein Objekt oder eine Zeichenfolge an Ihre übergeben `submitHandler` möchten.</span><span class="sxs-lookup"><span data-stu-id="fe992-131">You can call `submitTask()` without any parameters if you just want Teams to close the task module, but most of the time you'll want to pass an object or a string to your `submitHandler`.</span></span> <span data-ttu-id="fe992-132">Übergeben Sie es einfach als ersten Parameter, `result` .</span><span class="sxs-lookup"><span data-stu-id="fe992-132">Simply pass it as the first parameter, `result`.</span></span> <span data-ttu-id="fe992-133">Teams ruft `submitHandler` auf : wird das `err` `null` `result` Objekt/die Zeichenfolge sein, die Sie an übergeben `submitTask()` haben.</span><span class="sxs-lookup"><span data-stu-id="fe992-133">Teams will invoke `submitHandler`: `err` will be `null` and `result` will be the object/string you passed to `submitTask()`.</span></span> <span data-ttu-id="fe992-134">Wenn Sie `submitTask()` mit einem `result` Parameter aufrufen, **müssen** Sie ein oder ein Array `appId` von `appId` Zeichenfolgen übergeben: Dies ermöglicht es Teams zu überprüfen, ob die App, die das Ergebnis sendet, dieselbe ist, die das Taskmodul aufgerufen hat.</span><span class="sxs-lookup"><span data-stu-id="fe992-134">If you do call `submitTask()` with a `result` parameter, you **must** pass an `appId` or an array of `appId` strings: this allows Teams to validate that the app sending the result is the same one which invoked the task module.</span></span> <span data-ttu-id="fe992-135">Ihr Bot erhält eine `task/submit` Nachricht, einschließlich `result` wie [unten](#payload-of-taskfetch-and-tasksubmit-messages)beschrieben .</span><span class="sxs-lookup"><span data-stu-id="fe992-135">Your bot will receive a `task/submit` message including `result` as described [below](#payload-of-taskfetch-and-tasksubmit-messages).</span></span>
* <span data-ttu-id="fe992-136">**Adaptive Karte ( `TaskInfo.card` )**.</span><span class="sxs-lookup"><span data-stu-id="fe992-136">**Adaptive card (`TaskInfo.card`)**.</span></span> <span data-ttu-id="fe992-137">Der Adaptive-Kartentext (wie vom Benutzer ausgefüllt) wird über eine Nachricht an den Bot `task/submit` gesendet, wenn der Benutzer eine `Action.Submit` beliebige Taste drückt.</span><span class="sxs-lookup"><span data-stu-id="fe992-137">The Adaptive card body (as filled in by the user) will be sent to the bot via a `task/submit` message when the user presses any `Action.Submit` button.</span></span>

## <a name="the-flexibility-of-tasksubmit"></a><span data-ttu-id="fe992-138">Die Flexibilität der Aufgabe/Einreichung</span><span class="sxs-lookup"><span data-stu-id="fe992-138">The flexibility of task/submit</span></span>

<span data-ttu-id="fe992-139">Im vorherigen Abschnitt haben Sie erfahren, dass der Bot immer eine Nachricht empfängt, wenn der Benutzer mit einem Taskmodul abgeschlossen ist, das von einem Bot aufgerufen `task/submit invoke` wird.</span><span class="sxs-lookup"><span data-stu-id="fe992-139">In the previous section, you learned that when the user finishes with a task module invoked from a bot, the bot always receives a `task/submit invoke` message.</span></span> <span data-ttu-id="fe992-140">Als Entwickler haben Sie mehrere Optionen, wenn Sie *auf* die Nachricht `task/submit` antworten:</span><span class="sxs-lookup"><span data-stu-id="fe992-140">As a developer, you have several options when *responding* to the `task/submit` message:</span></span>

| <span data-ttu-id="fe992-141">HTTP-Körperantwort</span><span class="sxs-lookup"><span data-stu-id="fe992-141">HTTP Body Response</span></span>                      | <span data-ttu-id="fe992-142">Szenario</span><span class="sxs-lookup"><span data-stu-id="fe992-142">Scenario</span></span>                                |
| --------------------------------------- | --------------------------------------- |
| <span data-ttu-id="fe992-143">Keine (ignorieren Sie die `task/submit` Nachricht)</span><span class="sxs-lookup"><span data-stu-id="fe992-143">None (ignore the `task/submit` message)</span></span> | <span data-ttu-id="fe992-144">Die einfachste Antwort ist überhaupt keine Antwort.</span><span class="sxs-lookup"><span data-stu-id="fe992-144">The simplest response is no response at all.</span></span> <span data-ttu-id="fe992-145">Ihr Bot muss nicht reagieren, wenn der Benutzer mit dem Taskmodul fertig ist.</span><span class="sxs-lookup"><span data-stu-id="fe992-145">Your bot is not required to respond when the user is finished with the task module.</span></span> |
| <pre>{<br/>  "task": {<br/>    "type": "message",<br/>    "value": "Message text"<br/>  }<br/>}</pre> | <span data-ttu-id="fe992-146">Teams zeigt den Wert von `value` in einem Popup-Meldungsfeld an.</span><span class="sxs-lookup"><span data-stu-id="fe992-146">Teams will display the value of `value` in a popup message box.</span></span> |
| <pre>{<br/>  "task": {<br/>    "type": "continue",<br/>    "value": &lt;TaskInfo object&gt;<br/>  }<br/>}</pre> | <span data-ttu-id="fe992-147">Ermöglicht es Ihnen, Sequenzen von adaptiven Karten in einem Assistenten/mehrstufigen Erlebnis zusammen zu "ketten".</span><span class="sxs-lookup"><span data-stu-id="fe992-147">Allows you to "chain" sequences of Adaptive cards together in a wizard/multi-step experience.</span></span> <span data-ttu-id="fe992-148">_Beachten Sie, dass das Verketten von adaptiven Karten in einer Sequenz ein erweitertes Szenario ist und hier nicht dokumentiert ist. Die Node.js-Beispiel-App unterstützt sie jedoch, und wie sie funktioniert, wird in [der README.md-Datei](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs#implementation-notes)dokumentiert._</span><span class="sxs-lookup"><span data-stu-id="fe992-148">_Note that chaining Adaptive cards into a sequence is an advanced scenario and not documented here. The Node.js sample app supports it, however, and how it works is documented in [its README.md file](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs#implementation-notes)._</span></span> |

## <a name="payload-of-taskfetch-and-tasksubmit-messages"></a><span data-ttu-id="fe992-149">Nutzlast von Aufgaben-/Abruf- und Aufgaben-/Absendenvon Nachrichten</span><span class="sxs-lookup"><span data-stu-id="fe992-149">Payload of task/fetch and task/submit messages</span></span>

<span data-ttu-id="fe992-150">In diesem Abschnitt wird das Schema dessen definiert, was Ihr Bot empfängt, wenn er ein `task/fetch` oder `task/submit` Bot `Activity` Framework-Objekt empfängt.</span><span class="sxs-lookup"><span data-stu-id="fe992-150">This section defines the schema of what your bot receives when it receives a `task/fetch` or `task/submit` Bot Framework `Activity` object.</span></span> <span data-ttu-id="fe992-151">Die wichtige oberste Ebene erscheint unten:</span><span class="sxs-lookup"><span data-stu-id="fe992-151">The important top-level appear below:</span></span>

| <span data-ttu-id="fe992-152">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="fe992-152">Property</span></span> | <span data-ttu-id="fe992-153">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="fe992-153">Description</span></span>                          |
| -------- | ------------------------------------ |
| `type`   | <span data-ttu-id="fe992-154">Wird immer `invoke`</span><span class="sxs-lookup"><span data-stu-id="fe992-154">Will always be `invoke`</span></span>              |
| `name`   | <span data-ttu-id="fe992-155">Entweder `task/fetch` oder `task/submit`</span><span class="sxs-lookup"><span data-stu-id="fe992-155">Either `task/fetch` or `task/submit`</span></span> |
| `value`  | <span data-ttu-id="fe992-156">Die vom Entwickler definierte Nutzlast.</span><span class="sxs-lookup"><span data-stu-id="fe992-156">The developer-defined payload.</span></span> <span data-ttu-id="fe992-157">Normalerweise spiegelt die Struktur des `value` Objekts wider, was von Teams gesendet wurde.</span><span class="sxs-lookup"><span data-stu-id="fe992-157">Normally the structure of the `value` object mirrors what was sent from Teams.</span></span> <span data-ttu-id="fe992-158">In diesem Fall ist es jedoch anders, weil wir dynamisches Abrufen ( ) von Bot Framework ( ) und Adaptive Card-Aktionen ( ) unterstützen `task/fetch` `value` `Action.Submit` `data` möchten, und wir benötigen eine Möglichkeit, Teams dem Bot `context` zusätzlich zu dem zu kommunizieren, was in enthalten `value` / `data` war.</span><span class="sxs-lookup"><span data-stu-id="fe992-158">In this case, however, it's different because we want to support dynamic fetch (`task/fetch`) from both Bot Framework (`value`) and Adaptive card `Action.Submit` actions (`data`), and we need a way to communicate Teams `context` to the bot in addition to what was included in `value`/`data`.</span></span><br/><br/><span data-ttu-id="fe992-159">Wir tun dies, indem wir die beiden zu einem übergeordneten Objekt kombinieren:</span><span class="sxs-lookup"><span data-stu-id="fe992-159">We do this by combining the two into a parent object:</span></span><br/><br/><pre>{<br/>  "context": {<br/>    "theme": "default" &vert; "dark" &vert; "contrast",<br/>  },<br/>  "data": [value field from Bot Framework card] &vert; [data field from Adaptive Card] <br/>}</pre>  |

## <a name="example-receiving-and-responding-to-taskfetch-and-tasksubmit-invoke-messages---nodejs"></a><span data-ttu-id="fe992-160">Beispiel: Empfangen und Beantworten von Aufgaben-/Abruf- und Aufgaben-/Sendeaufrufnachrichten - Node.js</span><span class="sxs-lookup"><span data-stu-id="fe992-160">Example: Receiving and responding to task/fetch and task/submit invoke messages - Node.js</span></span>

> [!NOTE]
> <span data-ttu-id="fe992-161">Der folgende Beispielcode wurde zwischen Technical Preview und der endgültigen Version dieser Funktion geändert: Das Schema der Anforderung wurde geändert, um den `task/fetch` im vorherigen Abschnitt [dokumentierten](#payload-of-taskfetch-and-tasksubmit-messages)Informationen zu folgen.</span><span class="sxs-lookup"><span data-stu-id="fe992-161">The sample code below was modified between Technical Preview and final release of this feature: the schema of the `task/fetch` request changed to follow what was [documented in the previous section](#payload-of-taskfetch-and-tasksubmit-messages).</span></span> <span data-ttu-id="fe992-162">Das heißt, die Dokumentation war korrekt, aber die Umsetzung nicht.</span><span class="sxs-lookup"><span data-stu-id="fe992-162">That is, the documentation was correct but the implementation was not.</span></span> <span data-ttu-id="fe992-163">Sehen Sie sich die `// for Technical Preview [...]` Kommentare unten an, was sich geändert hat.</span><span class="sxs-lookup"><span data-stu-id="fe992-163">See the `// for Technical Preview [...]` comments below for what changed.</span></span>

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

## <a name="example-receiving-and-responding-to-taskfetch-and-tasksubmit-invoke-messages---c"></a><span data-ttu-id="fe992-164">Beispiel: Empfangen und Reagieren auf Aufgaben-/Abruf- und Task-/Sendeaufrufnachrichten - C #</span><span class="sxs-lookup"><span data-stu-id="fe992-164">Example: Receiving and responding to task/fetch and task/submit invoke messages - C#</span></span>

<span data-ttu-id="fe992-165">In C-Bots werden Nachrichten von einem Controller verarbeitet, der `invoke` eine Nachricht `HttpResponseMessage()` `Activity` verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="fe992-165">In C# bots, `invoke` messages are processed by an `HttpResponseMessage()` controller processing an `Activity` message.</span></span> <span data-ttu-id="fe992-166">Die `task/fetch` und Anfragen und Antworten sind `task/submit` JSON.</span><span class="sxs-lookup"><span data-stu-id="fe992-166">The `task/fetch` and `task/submit` requests and responses are JSON.</span></span> <span data-ttu-id="fe992-167">Es ist nicht so bequem, mit rohem JSON umzugehen wie in Node.js, daher benötigen Sie Wrapperklassen, um die Serialisierung von und nach JSON zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="fe992-167">In C#, it's not as convenient to deal with raw JSON as it is in Node.js, so you need wrapper classes to handle the serialization to and from JSON.</span></span> <span data-ttu-id="fe992-168">Es gibt noch keine direkte Unterstützung dafür im Microsoft Teams [C-SDK,](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) aber Sie können ein Beispiel dafür sehen, wie diese einfachen Wrapperklassen in der [Beispiel-App von C-](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Models/TaskModel.cs)aussehen würden.</span><span class="sxs-lookup"><span data-stu-id="fe992-168">There's no direct support for this in the Microsoft Teams [C# SDK](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) yet, but you can see an example of what these simple wrapper classes would look like in the [C# sample app](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Models/TaskModel.cs).</span></span>

<span data-ttu-id="fe992-169">Im Folgenden finden Sie Beispielcode in C- für die Handhabung `task/fetch` und Nachrichten mit diesen `task/submit` Wrapperklassen ( `TaskInfo` , ), aus dem `TaskEnvelope` [Beispiel](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs):</span><span class="sxs-lookup"><span data-stu-id="fe992-169">Below is example code in C# for handling `task/fetch` and `task/submit` messages using these wrapper classes (`TaskInfo`, `TaskEnvelope`), excerpted from the [sample](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs):</span></span>

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

<span data-ttu-id="fe992-170">Nicht im obigen Beispiel wird die `SetTaskInfo()` Funktion angezeigt, die die `height` , und die Eigenschaften des `width` `title` `TaskInfo` Objekts für jeden Fall festlegt.</span><span class="sxs-lookup"><span data-stu-id="fe992-170">Not shown in the above example is the `SetTaskInfo()` function, which sets the `height`, `width`, and `title` properties of the `TaskInfo` object for each case.</span></span> <span data-ttu-id="fe992-171">Hier ist der [Quellcode für SetTaskInfo()](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs).</span><span class="sxs-lookup"><span data-stu-id="fe992-171">Here's the [source code for SetTaskInfo()](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs).</span></span>

### <a name="bot-framework-card-actions-vs-adaptive-card-actionsubmit-actions"></a><span data-ttu-id="fe992-172">Bot Framework-Kartenaktionen im Vergleich zu Adaptive Card Action.Submit-Aktionen</span><span class="sxs-lookup"><span data-stu-id="fe992-172">Bot Framework card actions vs. Adaptive card Action.Submit actions</span></span>

<span data-ttu-id="fe992-173">Das Schema für Bot Framework-Kartenaktionen unterscheidet sich geringfügig von adaptiven `Action.Submit` Kartenaktionen.</span><span class="sxs-lookup"><span data-stu-id="fe992-173">The schema for Bot Framework card actions is slightly different from Adaptive card `Action.Submit` actions.</span></span> <span data-ttu-id="fe992-174">Daher ist die Art und Weise, Aufgabenmodule aufzurufen, ebenfalls etwas anders: Das `data` Objekt in enthält ein `Action.Submit` `msteams` Objekt, sodass es andere Eigenschaften in der Karte nicht beeinträchtigt.</span><span class="sxs-lookup"><span data-stu-id="fe992-174">As a result, the way to invoke task modules is slightly different too: the `data` object in `Action.Submit` contains an `msteams` object so it won't interfere with other properties in the card.</span></span> <span data-ttu-id="fe992-175">Die folgende Tabelle zeigt ein Beispiel für jede:</span><span class="sxs-lookup"><span data-stu-id="fe992-175">The following table shows an example of each:</span></span>

| <span data-ttu-id="fe992-176">Bot Framework-Kartenaktion</span><span class="sxs-lookup"><span data-stu-id="fe992-176">Bot Framework card action</span></span>                              | <span data-ttu-id="fe992-177">Adaptive Karte Action.Submit-Aktion</span><span class="sxs-lookup"><span data-stu-id="fe992-177">Adaptive card Action.Submit action</span></span>                     |
| ------------------------------------------------------ | ------------------------------------------------------ |
| <pre>{<br/>  "type": "invoke",<br/>  "title": "Buy",<br/>  "value": {<br/>    "type": "task/fetch",<br/>    &lt;...&gt;<br/>  }<br/>}</pre> | <pre>{<br/>  "type": "Action.Submit",<br/>  "id": "btnBuy",<br/>  "title": "Buy",<br/>  "data": {<br/>    &lt;...&gt;,<br/>    "msteams": {<br/>      "type": "task/fetch"<br/>    }<br/>  }<br/>}</pre>  |

## <a name="see-also"></a><span data-ttu-id="fe992-178">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="fe992-178">See also</span></span>

* [<span data-ttu-id="fe992-179">Beispielcode Microsoft Teams Taskmodul — nodejs</span><span class="sxs-lookup"><span data-stu-id="fe992-179">Microsoft Teams task module sample code — nodejs</span></span>](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs/blob/master/src/TeamsBot.ts)
* <span data-ttu-id="fe992-180">[Bot Framework-Beispiele](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).</span><span class="sxs-lookup"><span data-stu-id="fe992-180">[Bot Framework samples](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).</span></span>