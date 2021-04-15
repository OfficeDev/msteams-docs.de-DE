---
title: Verwenden von Aufgabenmodulen in Microsoft Teams-Bots
description: Verwenden von Aufgabenmodulen mit Microsoft Teams-Bots, einschließlich Bot Framework-Karten, adaptiven Karten und Tiefenlinks.
ms.topic: how-to
keywords: Aufgabenmodule Teams Bots
ms.openlocfilehash: d87b55bf202184f315abf69dfc34fc4db9125c4f
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696472"
---
# <a name="using-task-modules-from-microsoft-teams-bots"></a><span data-ttu-id="9f70a-104">Verwenden von Aufgabenmodulen aus Microsoft Teams-Bots</span><span class="sxs-lookup"><span data-stu-id="9f70a-104">Using task modules from Microsoft Teams bots</span></span>

<span data-ttu-id="9f70a-105">Aufgabenmodule können von Microsoft Teams-Bots mithilfe von Schaltflächen auf adaptiven Karten und Bot Framework-Karten (Hero, Thumbnail und Office 365 Connector) aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="9f70a-105">Task modules can be invoked from Microsoft Teams bots using buttons on Adaptive cards and Bot Framework cards (Hero, Thumbnail, and Office 365 Connector).</span></span> <span data-ttu-id="9f70a-106">Aufgabenmodule sind häufig eine bessere Benutzeroberfläche als mehrere Unterhaltungsschritte, bei denen Sie als Entwickler den Botstatus nachverfolgen und dem Benutzer das Unterbrechen/Abbrechen der Sequenz ermöglichen müssen.</span><span class="sxs-lookup"><span data-stu-id="9f70a-106">Task modules are often a better user experience than multiple conversation steps where you as a developer have to keep track of bot state and allow the user to interrupt/cancel the sequence.</span></span>

<span data-ttu-id="9f70a-107">Es gibt zwei Möglichkeiten zum Aufrufen von Aufgabenmodulen:</span><span class="sxs-lookup"><span data-stu-id="9f70a-107">There are two ways of invoking task modules:</span></span>

* <span data-ttu-id="9f70a-108">**Eine neue Art von Aufrufnachricht `task/fetch` .**</span><span class="sxs-lookup"><span data-stu-id="9f70a-108">**A new kind of invoke message `task/fetch`.**</span></span> <span data-ttu-id="9f70a-109">Mithilfe der Kartenaktion für Bot Framework-Karten oder der Kartenaktion für adaptive Karten mit wird das Aufgabenmodul (entweder eine URL oder eine adaptive Karte) dynamisch von Ihrem Bot `invoke` [](~/task-modules-and-cards/cards/cards-actions.md#invoke) `Action.Submit` [](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) `task/fetch` abgerufen.</span><span class="sxs-lookup"><span data-stu-id="9f70a-109">Using the `invoke` [card action](~/task-modules-and-cards/cards/cards-actions.md#invoke) for Bot Framework cards, or the `Action.Submit` [card action](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) for Adaptive cards, with `task/fetch`, the task module (either a URL or an Adaptive card) is fetched dynamically from your bot.</span></span>
* <span data-ttu-id="9f70a-110">**UrLs für Tiefe Verknüpfungen.**</span><span class="sxs-lookup"><span data-stu-id="9f70a-110">**Deep link URLs.**</span></span> <span data-ttu-id="9f70a-111">Mithilfe der [Deep Link-Syntax](~/task-modules-and-cards/what-are-task-modules.md#task-module-deep-link-syntax)für Aufgabenmodule können Sie die Kartenaktion für Bot Framework-Karten oder die `openUrl` [](~/task-modules-and-cards/cards/cards-actions.md#openurl) `Action.OpenUrl` [Kartenaktion](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) für adaptive Karten verwenden.</span><span class="sxs-lookup"><span data-stu-id="9f70a-111">Using the [deep link syntax for task modules](~/task-modules-and-cards/what-are-task-modules.md#task-module-deep-link-syntax), you can use the `openUrl` [card action](~/task-modules-and-cards/cards/cards-actions.md#openurl) for Bot Framework cards or the `Action.OpenUrl` [card action](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) for Adaptive cards, respectively.</span></span> <span data-ttu-id="9f70a-112">Bei URLs mit tiefen Verknüpfungen ist die URL des Aufgabenmoduls oder der Adaptive Kartentext offensichtlich im Voraus bekannt, um einen Servertrip relativ zu zu `task/fetch` vermeiden.</span><span class="sxs-lookup"><span data-stu-id="9f70a-112">With deep link URLs, the task module URL or Adaptive card body is obviously known in advance, avoiding a server round-trip relative to `task/fetch`.</span></span>

>[!IMPORTANT]
><span data-ttu-id="9f70a-113">Um eine sichere Kommunikation sicherzustellen, `url` müssen alle `fallbackUrl` das HTTPS-Verschlüsselungsprotokoll implementieren.</span><span class="sxs-lookup"><span data-stu-id="9f70a-113">To ensure secure communications, each `url` and `fallbackUrl` must implement the HTTPS encryption protocol.</span></span>

## <a name="invoking-a-task-module-via-taskfetch"></a><span data-ttu-id="9f70a-114">Aufrufen eines Aufgabenmoduls über Aufgabe/Abruf</span><span class="sxs-lookup"><span data-stu-id="9f70a-114">Invoking a task module via task/fetch</span></span>

<span data-ttu-id="9f70a-115">Wenn das Objekt der Kartenaktion oder auf die richtige Weise initialisiert wird (unten ausführlicher erläutert), wenn ein Benutzer die Schaltfläche drückt, wird eine Nachricht an den Bot `value` `invoke` `Action.Submit` `invoke` gesendet.</span><span class="sxs-lookup"><span data-stu-id="9f70a-115">When the `value` object of the `invoke` card action or `Action.Submit` is initialized in the proper way (explained in more detail below), when a user presses the button an `invoke` message is sent to the bot.</span></span> <span data-ttu-id="9f70a-116">In der HTTP-Antwort auf die Nachricht ist ein TaskInfo-Objekt in ein Wrapperobjekt eingebettet, das von Teams zum Anzeigen `invoke` des Aufgabenmoduls [](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="9f70a-116">In the HTTP response to the `invoke` message, there's a [TaskInfo object](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) embedded in a wrapper object, which Teams uses to display the task module.</span></span>

![task/fetch request/response](~/assets/images/task-module/task-module-invoke-request-response.png)

<span data-ttu-id="9f70a-118">Sehen wir uns die einzelnen Schritte genauer an:</span><span class="sxs-lookup"><span data-stu-id="9f70a-118">Let's look at each step in a bit more detail:</span></span>

1. <span data-ttu-id="9f70a-119">In diesem Beispiel wird eine Bot Framework Hero-Karte mit einer Kartenaktion "Kaufen" `invoke` [gezeigt.](~/task-modules-and-cards/cards/cards-actions.md#invoke)</span><span class="sxs-lookup"><span data-stu-id="9f70a-119">This example shows a Bot Framework Hero card with a "Buy" `invoke` [card action](~/task-modules-and-cards/cards/cards-actions.md#invoke).</span></span> <span data-ttu-id="9f70a-120">Der Wert der Eigenschaft ist - der Rest des Objekts kann nach Bes `type` `task/fetch` `value` nnen sein.</span><span class="sxs-lookup"><span data-stu-id="9f70a-120">The value of the `type` property is `task/fetch` - the rest of the `value` object can be whatever you like.</span></span>
2. <span data-ttu-id="9f70a-121">Der Bot empfängt die `invoke` HTTP-POST-Nachricht.</span><span class="sxs-lookup"><span data-stu-id="9f70a-121">The bot receives the `invoke` HTTP POST message.</span></span>
3. <span data-ttu-id="9f70a-122">Der Bot erstellt ein Antwortobjekt und gibt es im Textkörper der POST-Antwort mit einem HTTP 200-Antwortcode zurück.</span><span class="sxs-lookup"><span data-stu-id="9f70a-122">The bot creates a response object and returns it in the body of the POST response with an HTTP 200 response code.</span></span> <span data-ttu-id="9f70a-123">Das Schema für Antworten wird unten in der Diskussion über [Aufgabe/Absenden](#the-flexibility-of-tasksubmit)beschrieben. Es ist jedoch wichtig, dass der Textkörper der HTTP-Antwort ein [TaskInfo-Objekt](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) enthält, das in ein Wrapperobjekt eingebettet ist, z. B.:</span><span class="sxs-lookup"><span data-stu-id="9f70a-123">The schema for responses is described [below in the discussion on task/submit](#the-flexibility-of-tasksubmit), but the important thing to remember now is that the body of the HTTP response contains a [TaskInfo object](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) embedded in a wrapper object, e.g.:</span></span>

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

    <span data-ttu-id="9f70a-124">Das `task/fetch` Ereignis und seine Antwort für Bots ähneln konzeptionell der Funktion im Client `microsoftTeams.tasks.startTask()` SDK.</span><span class="sxs-lookup"><span data-stu-id="9f70a-124">The `task/fetch` event and its response for bots is similar, conceptually, to the `microsoftTeams.tasks.startTask()` function in the client SDK.</span></span>
4. <span data-ttu-id="9f70a-125">Microsoft Teams zeigt das Aufgabenmodul an.</span><span class="sxs-lookup"><span data-stu-id="9f70a-125">Microsoft Teams displays the task module.</span></span>

## <a name="submitting-the-result-of-a-task-module"></a><span data-ttu-id="9f70a-126">Übermitteln des Ergebnisses eines Aufgabenmoduls</span><span class="sxs-lookup"><span data-stu-id="9f70a-126">Submitting the result of a task module</span></span>

<span data-ttu-id="9f70a-127">Wenn der Benutzer mit dem Aufgabenmodul fertig ist, ähnelt das Zurücksenden des [Ergebnisses](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-submitting-the-result-of-a-task-module)an den Bot der Art und Weise, wie es mit Registerkarten funktioniert, aber es gibt einige Unterschiede, daher wird es auch hier beschrieben.</span><span class="sxs-lookup"><span data-stu-id="9f70a-127">When the user is finished with the task module, submitting the result back to the bot is similar [to the way it works with tabs](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-submitting-the-result-of-a-task-module), but there are a few differences, so it's described here too.</span></span>

* <span data-ttu-id="9f70a-128">**HTML/JavaScript ( `TaskInfo.url` )**.</span><span class="sxs-lookup"><span data-stu-id="9f70a-128">**HTML/JavaScript (`TaskInfo.url`)**.</span></span> <span data-ttu-id="9f70a-129">Nachdem Sie überprüft haben, was der Benutzer eingegeben hat, rufen Sie die SDK-Funktion auf (nachfolgend als zu `microsoftTeams.tasks.submitTask()` `submitTask()` Lesbarkeitszwecken bezeichnet).</span><span class="sxs-lookup"><span data-stu-id="9f70a-129">Once you've validated what the user has entered, you call the `microsoftTeams.tasks.submitTask()` SDK function (referred to hereafter as `submitTask()` for readability purposes).</span></span> <span data-ttu-id="9f70a-130">Sie können ohne Parameter aufrufen, wenn Sie nur möchten, dass Teams das Aufgabenmodul schließt, aber meistens möchten Sie ein Objekt oder eine Zeichenfolge an `submitTask()` Ihre `submitHandler` übergeben.</span><span class="sxs-lookup"><span data-stu-id="9f70a-130">You can call `submitTask()` without any parameters if you just want Teams to close the task module, but most of the time you'll want to pass an object or a string to your `submitHandler`.</span></span> <span data-ttu-id="9f70a-131">Übergeben Sie ihn einfach als ersten Parameter, `result` .</span><span class="sxs-lookup"><span data-stu-id="9f70a-131">Simply pass it as the first parameter, `result`.</span></span> <span data-ttu-id="9f70a-132">Teams ruft auf : ist und ist das Objekt/die Zeichenfolge, `submitHandler` das Sie an übergeben `err` `null` `result` `submitTask()` haben.</span><span class="sxs-lookup"><span data-stu-id="9f70a-132">Teams will invoke `submitHandler`: `err` will be `null` and `result` will be the object/string you passed to `submitTask()`.</span></span> <span data-ttu-id="9f70a-133">Wenn Sie einen Parameter aufrufen, müssen Sie ein oder ein Array von Zeichenfolgen übergeben: Auf diese Weise kann Teams überprüfen, ob die App, die das Ergebnis sendet, dieselbe ist, die das Aufgabenmodul aufgerufen `submitTask()` `result`  `appId` `appId` hat.</span><span class="sxs-lookup"><span data-stu-id="9f70a-133">If you do call `submitTask()` with a `result` parameter, you **must** pass an `appId` or an array of `appId` strings: this allows Teams to validate that the app sending the result is the same one which invoked the task module.</span></span> <span data-ttu-id="9f70a-134">Ihr Bot erhält eine `task/submit` Nachricht, einschließlich `result` wie unten [beschrieben.](#payload-of-taskfetch-and-tasksubmit-messages)</span><span class="sxs-lookup"><span data-stu-id="9f70a-134">Your bot will receive a `task/submit` message including `result` as described [below](#payload-of-taskfetch-and-tasksubmit-messages).</span></span>
* <span data-ttu-id="9f70a-135">**Adaptive Karte ( `TaskInfo.card` )**.</span><span class="sxs-lookup"><span data-stu-id="9f70a-135">**Adaptive card (`TaskInfo.card`)**.</span></span> <span data-ttu-id="9f70a-136">Der Adaptive Kartentext (vom Benutzer ausgefüllt) wird über eine Nachricht an den Bot gesendet, wenn der Benutzer `task/submit` eine beliebige Schaltfläche `Action.Submit` drückt.</span><span class="sxs-lookup"><span data-stu-id="9f70a-136">The Adaptive card body (as filled in by the user) will be sent to the bot via a `task/submit` message when the user presses any `Action.Submit` button.</span></span>

## <a name="the-flexibility-of-tasksubmit"></a><span data-ttu-id="9f70a-137">Die Flexibilität von Aufgabe/Absenden</span><span class="sxs-lookup"><span data-stu-id="9f70a-137">The flexibility of task/submit</span></span>

<span data-ttu-id="9f70a-138">Im vorherigen Abschnitt haben Sie erfahren, dass der Bot immer eine Nachricht empfängt, wenn der Benutzer mit einem Aufgabenmodul fertig ist, das von einem Bot aufgerufen `task/submit invoke` wird.</span><span class="sxs-lookup"><span data-stu-id="9f70a-138">In the previous section, you learned that when the user finishes with a task module invoked from a bot, the bot always receives a `task/submit invoke` message.</span></span> <span data-ttu-id="9f70a-139">Als Entwickler haben Sie mehrere Optionen, wenn *Sie auf* die Nachricht `task/submit` antworten:</span><span class="sxs-lookup"><span data-stu-id="9f70a-139">As a developer, you have several options when *responding* to the `task/submit` message:</span></span>

| <span data-ttu-id="9f70a-140">HTTP-Textkörperantwort</span><span class="sxs-lookup"><span data-stu-id="9f70a-140">HTTP Body Response</span></span>                      | <span data-ttu-id="9f70a-141">Szenario</span><span class="sxs-lookup"><span data-stu-id="9f70a-141">Scenario</span></span>                                |
| --------------------------------------- | --------------------------------------- |
| <span data-ttu-id="9f70a-142">Keine (Nachricht `task/submit` ignorieren)</span><span class="sxs-lookup"><span data-stu-id="9f70a-142">None (ignore the `task/submit` message)</span></span> | <span data-ttu-id="9f70a-143">Die einfachste Antwort ist überhaupt keine Antwort.</span><span class="sxs-lookup"><span data-stu-id="9f70a-143">The simplest response is no response at all.</span></span> <span data-ttu-id="9f70a-144">Ihr Bot muss nicht reagieren, wenn der Benutzer mit dem Aufgabenmodul fertig ist.</span><span class="sxs-lookup"><span data-stu-id="9f70a-144">Your bot is not required to respond when the user is finished with the task module.</span></span> |
| <pre>{<br/>  "task": {<br/>    "type": "message",<br/>    "value": "Message text"<br/>  }<br/>}</pre> | <span data-ttu-id="9f70a-145">Teams zeigt den Wert in `value` einem Popup-Meldungsfeld an.</span><span class="sxs-lookup"><span data-stu-id="9f70a-145">Teams will display the value of `value` in a popup message box.</span></span> |
| <pre>{<br/>  "task": {<br/>    "type": "continue",<br/>    "value": &lt;TaskInfo object&gt;<br/>  }<br/>}</pre> | <span data-ttu-id="9f70a-146">Ermöglicht es Ihnen, Sequenzen adaptiver Karten in einer Assistenten-/Mehrschritt-Erfahrung zu "verketten".</span><span class="sxs-lookup"><span data-stu-id="9f70a-146">Allows you to "chain" sequences of Adaptive cards together in a wizard/multi-step experience.</span></span> <span data-ttu-id="9f70a-147">_Beachten Sie, dass das Verketten adaptiver Karten in einer Sequenz ein erweitertes Szenario ist und hier nicht dokumentiert ist. Die Node.js-Beispiel-App unterstützt sie jedoch, und ihre Funktionsweise wird in der README.md [dokumentiert.](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs#implementation-notes)_</span><span class="sxs-lookup"><span data-stu-id="9f70a-147">_Note that chaining Adaptive cards into a sequence is an advanced scenario and not documented here. The Node.js sample app supports it, however, and how it works is documented in [its README.md file](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs#implementation-notes)._</span></span> |

## <a name="payload-of-taskfetch-and-tasksubmit-messages"></a><span data-ttu-id="9f70a-148">Nutzlast von Aufgaben-/Abruf- und Vorgangs-/Absendennachrichten</span><span class="sxs-lookup"><span data-stu-id="9f70a-148">Payload of task/fetch and task/submit messages</span></span>

<span data-ttu-id="9f70a-149">In diesem Abschnitt wird das Schema definiert, was Ihr Bot empfängt, wenn er ein `task/fetch` oder `task/submit` ein Bot Framework-Objekt `Activity` empfängt.</span><span class="sxs-lookup"><span data-stu-id="9f70a-149">This section defines the schema of what your bot receives when it receives a `task/fetch` or `task/submit` Bot Framework `Activity` object.</span></span> <span data-ttu-id="9f70a-150">Die wichtige oberste Ebene wird unten angezeigt:</span><span class="sxs-lookup"><span data-stu-id="9f70a-150">The important top-level appear below:</span></span>

| <span data-ttu-id="9f70a-151">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="9f70a-151">Property</span></span> | <span data-ttu-id="9f70a-152">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9f70a-152">Description</span></span>                          |
| -------- | ------------------------------------ |
| `type`   | <span data-ttu-id="9f70a-153">Wird immer sein `invoke`</span><span class="sxs-lookup"><span data-stu-id="9f70a-153">Will always be `invoke`</span></span>              |
| `name`   | <span data-ttu-id="9f70a-154">Entweder `task/fetch` oder `task/submit`</span><span class="sxs-lookup"><span data-stu-id="9f70a-154">Either `task/fetch` or `task/submit`</span></span> |
| `value`  | <span data-ttu-id="9f70a-155">Die vom Entwickler definierte Nutzlast.</span><span class="sxs-lookup"><span data-stu-id="9f70a-155">The developer-defined payload.</span></span> <span data-ttu-id="9f70a-156">Normalerweise spiegelt die Struktur des `value` Objekts wider, was von Teams gesendet wurde.</span><span class="sxs-lookup"><span data-stu-id="9f70a-156">Normally the structure of the `value` object mirrors what was sent from Teams.</span></span> <span data-ttu-id="9f70a-157">In diesem Fall ist dies jedoch anders, da wir den dynamischen Abruf ( ) sowohl von Bot Framework ( ) als auch von adaptiven Kartenaktionen ( ) unterstützen möchten, und wir benötigen eine Möglichkeit, Teams mit dem Bot zu kommunizieren, zusätzlich zu dem, was in enthalten `task/fetch` `value` `Action.Submit` `data` `context` `value` / `data` war.</span><span class="sxs-lookup"><span data-stu-id="9f70a-157">In this case, however, it's different because we want to support dynamic fetch (`task/fetch`) from both Bot Framework (`value`) and Adaptive card `Action.Submit` actions (`data`), and we need a way to communicate Teams `context` to the bot in addition to what was included in `value`/`data`.</span></span><br/><br/><span data-ttu-id="9f70a-158">Dazu kombinieren wir die beiden zu einem übergeordneten Objekt:</span><span class="sxs-lookup"><span data-stu-id="9f70a-158">We do this by combining the two into a parent object:</span></span><br/><br/><pre>{<br/>  "context": {<br/>    "theme": "default" &vert; "dark" &vert; "contrast",<br/>  },<br/>  "data": [value field from Bot Framework card] &vert; [data field from Adaptive Card] <br/>}</pre>  |

## <a name="example-receiving-and-responding-to-taskfetch-and-tasksubmit-invoke-messages---nodejs"></a><span data-ttu-id="9f70a-159">Beispiel: Empfangen und Reagieren auf Aufgaben-/Abruf- und Task-/Submit-Aufrufnachrichten – Node.js</span><span class="sxs-lookup"><span data-stu-id="9f70a-159">Example: Receiving and responding to task/fetch and task/submit invoke messages - Node.js</span></span>

> [!NOTE]
> <span data-ttu-id="9f70a-160">Der folgende Beispielcode wurde zwischen Technical Preview und der endgültigen Version dieses Features geändert: Das Schema der Anforderung wurde geändert, um dem im vorherigen Abschnitt `task/fetch` [dokumentierten Schema zu folgen.](#payload-of-taskfetch-and-tasksubmit-messages)</span><span class="sxs-lookup"><span data-stu-id="9f70a-160">The sample code below was modified between Technical Preview and final release of this feature: the schema of the `task/fetch` request changed to follow what was [documented in the previous section](#payload-of-taskfetch-and-tasksubmit-messages).</span></span> <span data-ttu-id="9f70a-161">Das heißt, die Dokumentation war richtig, aber die Implementierung nicht.</span><span class="sxs-lookup"><span data-stu-id="9f70a-161">That is, the documentation was correct but the implementation was not.</span></span> <span data-ttu-id="9f70a-162">Was sich geändert hat, erfahren Sie in `// for Technical Preview [...]` den kommentaren unten.</span><span class="sxs-lookup"><span data-stu-id="9f70a-162">See the `// for Technical Preview [...]` comments below for what changed.</span></span>

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

<span data-ttu-id="9f70a-163">*Weitere Informationen finden* Sie unter Beispielcode des [Microsoft Teams-Aufgabenmoduls – nodejs](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs/blob/master/src/TeamsBot.ts) und [Bot Framework-Beispiele.](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)</span><span class="sxs-lookup"><span data-stu-id="9f70a-163">*See also*, [Microsoft Teams task module sample code — nodejs](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs/blob/master/src/TeamsBot.ts) and  [Bot Framework samples](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).</span></span>

## <a name="example-receiving-and-responding-to-taskfetch-and-tasksubmit-invoke-messages---c"></a><span data-ttu-id="9f70a-164">Beispiel: Empfangen und Antworten auf Aufgaben-/Abruf- und Task-/Submit-Aufrufnachrichten - C #</span><span class="sxs-lookup"><span data-stu-id="9f70a-164">Example: Receiving and responding to task/fetch and task/submit invoke messages - C#</span></span>

<span data-ttu-id="9f70a-165">In C# werden Nachrichten von einem Controller verarbeitet, der `invoke` `HttpResponseMessage()` eine Nachricht `Activity` verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="9f70a-165">In C# bots, `invoke` messages are processed by an `HttpResponseMessage()` controller processing an `Activity` message.</span></span> <span data-ttu-id="9f70a-166">Die `task/fetch` Anforderungen und Antworten sind `task/submit` JSON.</span><span class="sxs-lookup"><span data-stu-id="9f70a-166">The `task/fetch` and `task/submit` requests and responses are JSON.</span></span> <span data-ttu-id="9f70a-167">In C# ist es nicht so praktisch, mit unformatiertem JSON zu umgehen wie in Node.js, daher benötigen Sie Wrapperklassen, um die Serialisierung von und zu JSON zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="9f70a-167">In C#, it's not as convenient to deal with raw JSON as it is in Node.js, so you need wrapper classes to handle the serialization to and from JSON.</span></span> <span data-ttu-id="9f70a-168">Es gibt noch keine direkte Unterstützung dafür im Microsoft Teams [C# SDK,](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) aber Sie können ein Beispiel dafür sehen, wie diese einfachen Wrapperklassen in der [C#-Beispiel-App aussehen würden.](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Models/TaskModel.cs)</span><span class="sxs-lookup"><span data-stu-id="9f70a-168">There's no direct support for this in the Microsoft Teams [C# SDK](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) yet, but you can see an example of what these simple wrapper classes would look like in the [C# sample app](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Models/TaskModel.cs).</span></span>

<span data-ttu-id="9f70a-169">Nachfolgend finden Sie Beispielcode in C# für die Behandlung und Nachrichten mithilfe dieser `task/fetch` `task/submit` Wrapperklassen ( `TaskInfo` , ), `TaskEnvelope` auszugsweise aus dem [Beispiel](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs):</span><span class="sxs-lookup"><span data-stu-id="9f70a-169">Below is example code in C# for handling `task/fetch` and `task/submit` messages using these wrapper classes (`TaskInfo`, `TaskEnvelope`), excerpted from the [sample](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs):</span></span>

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

<span data-ttu-id="9f70a-170">Im obigen Beispiel wird die Funktion nicht angezeigt, mit der die Eigenschaften , und des Objekts `SetTaskInfo()` für jeden Fall festgelegt `height` `width` `title` `TaskInfo` werden.</span><span class="sxs-lookup"><span data-stu-id="9f70a-170">Not shown in the above example is the `SetTaskInfo()` function, which sets the `height`, `width`, and `title` properties of the `TaskInfo` object for each case.</span></span> <span data-ttu-id="9f70a-171">Hier ist der [Quellcode für SetTaskInfo()](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs).</span><span class="sxs-lookup"><span data-stu-id="9f70a-171">Here's the [source code for SetTaskInfo()](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs).</span></span>

### <a name="bot-framework-card-actions-vs-adaptive-card-actionsubmit-actions"></a><span data-ttu-id="9f70a-172">Aktionen von Bot Framework-Karten im Vergleich zu Aktionen für adaptive Karten Action.Submit</span><span class="sxs-lookup"><span data-stu-id="9f70a-172">Bot Framework card actions vs. Adaptive card Action.Submit actions</span></span>

<span data-ttu-id="9f70a-173">Das Schema für Bot Framework-Kartenaktionen ist etwas anders als adaptive `Action.Submit` Kartenaktionen.</span><span class="sxs-lookup"><span data-stu-id="9f70a-173">The schema for Bot Framework card actions is slightly different from Adaptive card `Action.Submit` actions.</span></span> <span data-ttu-id="9f70a-174">Daher ist auch die Methode zum Aufrufen von Aufgabenmodulen etwas anders: Das Objekt in enthält ein Objekt, sodass es keine anderen Eigenschaften in der Karte `data` `Action.Submit` `msteams` beeinträchtigt.</span><span class="sxs-lookup"><span data-stu-id="9f70a-174">As a result, the way to invoke task modules is slightly different too: the `data` object in `Action.Submit` contains an `msteams` object so it won't interfere with other properties in the card.</span></span> <span data-ttu-id="9f70a-175">Die folgende Tabelle zeigt ein Beispiel für die einzelnen Beispiele:</span><span class="sxs-lookup"><span data-stu-id="9f70a-175">The following table shows an example of each:</span></span>

| <span data-ttu-id="9f70a-176">Bot Framework-Kartenaktion</span><span class="sxs-lookup"><span data-stu-id="9f70a-176">Bot Framework card action</span></span>                              | <span data-ttu-id="9f70a-177">Aktion für adaptive Karten Action.Submit</span><span class="sxs-lookup"><span data-stu-id="9f70a-177">Adaptive card Action.Submit action</span></span>                     |
| ------------------------------------------------------ | ------------------------------------------------------ |
| <pre>{<br/>  "type": "invoke",<br/>  "title": "Buy",<br/>  "value": {<br/>    "type": "task/fetch",<br/>    &lt;...&gt;<br/>  }<br/>}</pre> | <pre>{<br/>  "type": "Action.Submit",<br/>  "id": "btnBuy",<br/>  "title": "Buy",<br/>  "data": {<br/>    &lt;...&gt;,<br/>    "msteams": {<br/>      "type": "task/fetch"<br/>    }<br/>  }<br/>}</pre>  |
