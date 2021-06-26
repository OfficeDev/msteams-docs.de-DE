---
title: Aufrufen und Schließen von Aufgabenmodulen
description: Aufrufen und Schließen von Aufgabenmodulen.
author: surbhigupta12
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: a23d5cee3f13967772a4b58ed973bf08906e36a6
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140772"
---
# <a name="invoke-and-dismiss-task-modules"></a><span data-ttu-id="dd981-103">Aufrufen und Schließen von Aufgabenmodulen</span><span class="sxs-lookup"><span data-stu-id="dd981-103">Invoke and dismiss task modules</span></span>

<span data-ttu-id="dd981-104">Aufgabenmodule können über Registerkarten, Bots oder Deep-Links aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="dd981-104">Task modules can be invoked from tabs, bots, or deep links.</span></span> <span data-ttu-id="dd981-105">Die Antwort kann entweder in HTML, JavaScript oder als adaptive Karte erfolgen.</span><span class="sxs-lookup"><span data-stu-id="dd981-105">The response can be either in HTML, JavaScript, or as an Adaptive Card.</span></span> <span data-ttu-id="dd981-106">Es gibt eine große Flexibilität hinsichtlich der Art und Weise, wie Aufgabenmodule aufgerufen werden und wie sie mit der Reaktion der Benutzerinteraktion umzugehen sind.</span><span class="sxs-lookup"><span data-stu-id="dd981-106">There is a lot of flexibility in terms of how task modules are invoked and how to deal with the response of the user's interaction.</span></span> <span data-ttu-id="dd981-107">In der folgenden Tabelle wird die Funktionsweise zusammengefasst:</span><span class="sxs-lookup"><span data-stu-id="dd981-107">The following table summarizes how this works:</span></span>

| <span data-ttu-id="dd981-108">Wird mithilfe von</span><span class="sxs-lookup"><span data-stu-id="dd981-108">Invoked using</span></span> | <span data-ttu-id="dd981-109">Aufgabenmodul mit HTML oder JavaScript</span><span class="sxs-lookup"><span data-stu-id="dd981-109">Task module with HTML or JavaScript</span></span> | <span data-ttu-id="dd981-110">Aufgabenmodul mit adaptiver Karte</span><span class="sxs-lookup"><span data-stu-id="dd981-110">Task module with Adaptive Card</span></span> |
| --- | --- | --- |
| <span data-ttu-id="dd981-111">JavaScript auf einer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="dd981-111">JavaScript in a tab</span></span> | <span data-ttu-id="dd981-112">1. Verwenden Sie die Teams Client SDK-Funktion `tasks.startTask()` mit einer optionalen `submitHandler(err, result)` Rückruffunktion.</span><span class="sxs-lookup"><span data-stu-id="dd981-112">1. Use the Teams client SDK function `tasks.startTask()` with an optional `submitHandler(err, result)` callback function.</span></span> <br/><br/> <span data-ttu-id="dd981-113">2. Wenn der Benutzer die Aktionen ausgeführt hat, rufen Sie im Aufgabenmodulcode die Teams SDK-Funktion `tasks.submitTask()` mit einem Objekt als Parameter `result` auf.</span><span class="sxs-lookup"><span data-stu-id="dd981-113">2. In the task module code, when the user has performed the actions, call the Teams SDK function `tasks.submitTask()` with a `result` object as a parameter.</span></span> <span data-ttu-id="dd981-114">Wenn ein `submitHandler` Rückruf in angegeben `tasks.startTask()` wurde, ruft Teams ihn als Parameter `result` auf.</span><span class="sxs-lookup"><span data-stu-id="dd981-114">If a `submitHandler` callback was specified in `tasks.startTask()`, Teams calls it with `result` as a parameter.</span></span> <span data-ttu-id="dd981-115">Wenn beim Aufrufen ein Fehler aufgetreten `tasks.startTask()` ist, wird die `submitHandler` Funktion stattdessen mit einer `err` Zeichenfolge aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="dd981-115">If there was an error when invoking `tasks.startTask()`, the `submitHandler` function is called with an `err` string instead.</span></span> <br/><br/> <span data-ttu-id="dd981-116">3. Sie können auch eine `completionBotId` beim Aufrufen `teams.startTask()` angeben.</span><span class="sxs-lookup"><span data-stu-id="dd981-116">3. You can also specify a `completionBotId` when calling `teams.startTask()`.</span></span> <span data-ttu-id="dd981-117">Dann wird er `result` stattdessen an den Bot gesendet.</span><span class="sxs-lookup"><span data-stu-id="dd981-117">Then the `result` is sent to the bot instead.</span></span> | <span data-ttu-id="dd981-118">1. Rufen Sie die Teams `tasks.startTask()` Client-SDK-Funktion mit einem [TaskInfo-Objekt](#the-taskinfo-object) auf und `TaskInfo.card` enthalten den JSON-Code für die adaptive Karte, die im Popup des Aufgabenmoduls angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="dd981-118">1. Call the Teams client SDK function `tasks.startTask()` with a [TaskInfo object](#the-taskinfo-object) and `TaskInfo.card` containing the JSON for the Adaptive Card to show in the task module pop-up.</span></span> <br/><br/> <span data-ttu-id="dd981-119">2. Wenn ein `submitHandler` Rückruf in angegeben `tasks.startTask()` wurde, ruft Teams ihn mit einer `err` Zeichenfolge auf, wenn beim Aufrufen ein Fehler aufgetreten ist `tasks.startTask()` oder wenn der Benutzer das Aufgabenmodul-Popup mit dem X oben rechts schließt.</span><span class="sxs-lookup"><span data-stu-id="dd981-119">2. If a `submitHandler` callback was specified in `tasks.startTask()`, Teams calls it with an `err` string, if there was an error when invoking `tasks.startTask()` or if the user closes the task module pop-up using the X at the upper right.</span></span> <br/><br/> <span data-ttu-id="dd981-120">3. Wenn der Benutzer eine `Action.Submit` Schaltfläche drückt, wird sein `data` Objekt als Wert von `result` zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="dd981-120">3. If the user presses an `Action.Submit` button then its `data` object is returned as the value of `result`.</span></span> |
| <span data-ttu-id="dd981-121">Bot-Kartenschaltfläche</span><span class="sxs-lookup"><span data-stu-id="dd981-121">Bot card button</span></span> | <span data-ttu-id="dd981-122">1. Botkartenschaltflächen können, je nach Art der Schaltfläche, Aufgabenmodule auf zwei Arten aufrufen: eine Deep-Link-URL oder durch Senden einer `task/fetch` Nachricht.</span><span class="sxs-lookup"><span data-stu-id="dd981-122">1. Bot card buttons, depending on the type of button, can invoke task modules in two ways, a deep link URL or by sending a `task/fetch` message.</span></span> <br/><br/> <span data-ttu-id="dd981-123">2. Wenn die Aktion der Schaltfläche den Schaltflächentyp für adaptive Karten darstellt, wird ein Ereignis, bei dem es sich `type` um `task/fetch` einen `Action.Submit` `task/fetch invoke` HTTP-POST handelt, an den Bot gesendet.</span><span class="sxs-lookup"><span data-stu-id="dd981-123">2. If the button's action `type` is `task/fetch` that is `Action.Submit` button type for Adaptive Cards, a `task/fetch invoke` event that is an HTTP POST is sent to the bot.</span></span> <span data-ttu-id="dd981-124">Der Bot antwortet auf den POST mit HTTP 200 und den Antworttext, der einen Wrapper um das [TaskInfo -Objekt](#the-taskinfo-object)enthält.</span><span class="sxs-lookup"><span data-stu-id="dd981-124">The bot responds to the POST with HTTP 200 and the response body containing a wrapper around the [TaskInfo object](#the-taskinfo-object).</span></span> <span data-ttu-id="dd981-125">Weitere Informationen finden Sie unter [Aufrufen `task/fetch` eines Aufgabenmoduls mithilfe von ](~/task-modules-and-cards/task-modules/task-modules-bots.md#invoke-a-task-module-using-taskfetch).</span><span class="sxs-lookup"><span data-stu-id="dd981-125">For more information, see [invoking a task module using `task/fetch`](~/task-modules-and-cards/task-modules/task-modules-bots.md#invoke-a-task-module-using-taskfetch).</span></span> <span data-ttu-id="dd981-126">Teams zeigt das Aufgabenmodul an.</span><span class="sxs-lookup"><span data-stu-id="dd981-126">Teams displays the task module.</span></span> <br/><br/> <span data-ttu-id="dd981-127">3. Nachdem der Benutzer die Aktionen ausgeführt hat, rufen Sie die Teams SDK-Funktion `tasks.submitTask()` mit einem Objekt als Parameter `result` auf.</span><span class="sxs-lookup"><span data-stu-id="dd981-127">3. After the user has performed the actions, call the Teams SDK function `tasks.submitTask()` with a `result` object as a parameter.</span></span> <span data-ttu-id="dd981-128">Der Bot empfängt eine `task/submit invoke` Nachricht, die das `result` Objekt enthält.</span><span class="sxs-lookup"><span data-stu-id="dd981-128">The bot receives a `task/submit invoke` message that contains the `result` object.</span></span> <br/><br/> <span data-ttu-id="dd981-129">4. Sie haben drei verschiedene Möglichkeiten, auf die Nachricht zu reagieren, indem Sie `task/submit` nichts tun, was die Aufgabe erfolgreich abgeschlossen hat, indem Sie dem Benutzer eine Nachricht in einem Popupfenster anzeigen oder ein anderes Aufgabenmodulfenster aufrufen.</span><span class="sxs-lookup"><span data-stu-id="dd981-129">4. You have three different ways to respond to the `task/submit` message, by doing nothing that is the task completed successfully, by displaying a message to the user in a pop-up window, or by invoking another task module window.</span></span> <span data-ttu-id="dd981-130">Weitere Informationen finden Sie in [den ausführlichen Erläuterungen zu `task/submit` ](~/task-modules-and-cards/task-modules/task-modules-bots.md#the-flexibility-of-tasksubmit).</span><span class="sxs-lookup"><span data-stu-id="dd981-130">For more information, see [detailed discussion on `task/submit`](~/task-modules-and-cards/task-modules/task-modules-bots.md#the-flexibility-of-tasksubmit).</span></span> | <ul><li> <span data-ttu-id="dd981-131">Wie Schaltflächen auf Bot Framework-Karten unterstützen Schaltflächen auf adaptiven Karten zwei Möglichkeiten zum Aufrufen von Aufgabenmodulen, Deep-Link-URLs mit `Action.openUrl` Schaltflächen und `task/fetch` verwenden `Action.Submit` Schaltflächen.</span><span class="sxs-lookup"><span data-stu-id="dd981-131">Like buttons on Bot Framework cards, buttons on Adaptive Cards support two ways of invoking task modules, deep link URLs with `Action.openUrl` buttons, and `task/fetch` using `Action.Submit` buttons.</span></span> </li></ul> <br/><br/> <ul><li> <span data-ttu-id="dd981-132">Aufgabenmodule mit adaptiven Karten funktionieren sehr ähnlich wie der HTML- oder JavaScript-Fall.</span><span class="sxs-lookup"><span data-stu-id="dd981-132">Task modules with Adaptive Cards work very similarly to the HTML or JavaScript case.</span></span> <span data-ttu-id="dd981-133">Der Hauptunterschied besteht darin, dass es keine Möglichkeit gibt, adaptive Karten aufzurufen, da es kein JavaScript gibt, wenn Sie adaptive Karten `tasks.submitTask()` verwenden.</span><span class="sxs-lookup"><span data-stu-id="dd981-133">The major difference is that since there is no JavaScript when you are using Adaptive Cards, there is no way to call `tasks.submitTask()`.</span></span> <span data-ttu-id="dd981-134">Stattdessen übernimmt Teams das `data` Objekt und gibt es als Nutzlast des `Action.Submit` `task/submit` Ereignisses zurück.</span><span class="sxs-lookup"><span data-stu-id="dd981-134">Instead, Teams takes the `data` object from `Action.Submit` and returns it as the payload of the `task/submit` event.</span></span> <span data-ttu-id="dd981-135">Weitere Informationen finden Sie unter [Flexibilität von `task/submit` ](~/task-modules-and-cards/task-modules/task-modules-bots.md#the-flexibility-of-tasksubmit).</span><span class="sxs-lookup"><span data-stu-id="dd981-135">For more information, see [flexibility of `task/submit`](~/task-modules-and-cards/task-modules/task-modules-bots.md#the-flexibility-of-tasksubmit).</span></span> </li></ul> |
| <span data-ttu-id="dd981-136">Deep-Link-URL</span><span class="sxs-lookup"><span data-stu-id="dd981-136">Deep link URL</span></span> <br/>[<span data-ttu-id="dd981-137">URL-Syntax</span><span class="sxs-lookup"><span data-stu-id="dd981-137">URL syntax</span></span>](#task-module-deep-link-syntax) | <span data-ttu-id="dd981-138">1. Teams ruft das Aufgabenmodul auf, bei dem es sich um die URL handelt, die innerhalb des `<iframe>` angegebenen Im `url` Parameters des Deep-Links angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="dd981-138">1. Teams invokes the task module that is the URL that appears inside the `<iframe>` specified in the `url` parameter of the deep link.</span></span> <span data-ttu-id="dd981-139">Es gibt keinen `submitHandler` Rückruf.</span><span class="sxs-lookup"><span data-stu-id="dd981-139">There is no `submitHandler` callback.</span></span> <br/><br/> <span data-ttu-id="dd981-140">2. Rufen Sie innerhalb des JavaScript der Seite im Aufgabenmodul auf, `tasks.submitTask()` es mit einem Objekt als Parameter zu schließen, genauso wie beim Aufrufen von einer Registerkarte oder einer `result` Bot-Kartenschaltfläche.</span><span class="sxs-lookup"><span data-stu-id="dd981-140">2. Within the JavaScript of the page in the task module, call `tasks.submitTask()` to close it with a `result` object as a parameter, the same as when invoking it from a tab or a bot card button.</span></span> <span data-ttu-id="dd981-141">Die Abschlusslogik unterscheidet sich jedoch geringfügig.</span><span class="sxs-lookup"><span data-stu-id="dd981-141">However, completion logic is slightly different.</span></span> <span data-ttu-id="dd981-142">Wenn sich die Abschlusslogik auf dem Client befindet, der sich befindet, wenn kein Bot vorhanden ist, gibt es keinen `submitHandler` Rückruf, daher muss sich jede Vervollständigungslogik im Code vor dem Aufruf von `tasks.submitTask()` befinden.</span><span class="sxs-lookup"><span data-stu-id="dd981-142">If your completion logic resides on the client that is if there is no bot, there is no `submitHandler` callback, so any completion logic must be in the code preceding the call to `tasks.submitTask()`.</span></span> <span data-ttu-id="dd981-143">Aufruffehler werden nur über die Konsole gemeldet.</span><span class="sxs-lookup"><span data-stu-id="dd981-143">Invocation errors are only reported through the console.</span></span> <span data-ttu-id="dd981-144">Wenn Sie über einen Bot verfügen, können Sie `completionBotId` im Deep-Link einen Parameter angeben, um das Objekt über ein Ereignis zu `result` `task/submit` senden.</span><span class="sxs-lookup"><span data-stu-id="dd981-144">If you have a bot, then you can specify a `completionBotId` parameter in the deep link to send the `result` object through a `task/submit` event.</span></span> | <span data-ttu-id="dd981-145">1. Teams ruft das Aufgabenmodul auf, bei dem es sich um den JSON-Kartentext der adaptiven Karte handelt, die als URL-codierter Wert des `card` Parameters des Deep-Links angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="dd981-145">1. Teams invokes the task module that is the JSON card body of the Adaptive Card that is specified as a URL-encoded value of the `card` parameter of the deep link.</span></span> <br/><br/> <span data-ttu-id="dd981-146">2. Der Benutzer schließt das Aufgabenmodul, indem er das X oben rechts des Aufgabenmoduls auswählt oder `Action.Submit` eine Schaltfläche auf der Karte drückt.</span><span class="sxs-lookup"><span data-stu-id="dd981-146">2. The user closes the task module by selecting the X at the upper right of the task module or by pressing an `Action.Submit` button on the card.</span></span> <span data-ttu-id="dd981-147">Da kein `submitHandler` Aufruf erforderlich ist, muss der Benutzer über einen Bot verfügen, um den Wert der Felder für adaptive Karten zu senden.</span><span class="sxs-lookup"><span data-stu-id="dd981-147">Since there is no `submitHandler` to call, the user must have a bot to send the value of the Adaptive Card fields.</span></span> <span data-ttu-id="dd981-148">Der Benutzer muss den `completionBotId` Parameter im Deep-Link verwenden, um den Bot anzugeben, an den die Daten mithilfe eines Ereignisses gesendet werden `task/submit invoke` sollen.</span><span class="sxs-lookup"><span data-stu-id="dd981-148">The user must use the `completionBotId` parameter in the deep link to specify the bot to send the data to using a `task/submit invoke` event.</span></span> |

> [!NOTE]
> <span data-ttu-id="dd981-149">Das Aufrufen eines Aufgabenmoduls aus JavaScript wird auf mobilen Geräten nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="dd981-149">Invoking a task module from JavaScript is not supported on mobile.</span></span>

<span data-ttu-id="dd981-150">Im nächsten Abschnitt wird das `TaskInfo` Objekt angegeben, das bestimmte Attribute für ein Aufgabenmodul definiert.</span><span class="sxs-lookup"><span data-stu-id="dd981-150">The next section specifies the `TaskInfo` object that defines certain attributes for a task module.</span></span>

## <a name="the-taskinfo-object"></a><span data-ttu-id="dd981-151">Das TaskInfo-Objekt</span><span class="sxs-lookup"><span data-stu-id="dd981-151">The TaskInfo object</span></span>

<span data-ttu-id="dd981-152">Das `TaskInfo` Objekt enthält die Metadaten für ein Aufgabenmodul.</span><span class="sxs-lookup"><span data-stu-id="dd981-152">The `TaskInfo` object contains the metadata for a task module.</span></span> <span data-ttu-id="dd981-153">Definieren Sie den `url` für einen eingebetteten iFrame oder `card` für eine adaptive Karte.</span><span class="sxs-lookup"><span data-stu-id="dd981-153">Define the `url` for an embedded iFrame or `card` for an Adaptive Card.</span></span> <span data-ttu-id="dd981-154">Die folgende Tabelle enthält die Objektdefinition:</span><span class="sxs-lookup"><span data-stu-id="dd981-154">The following table provides the object definition:</span></span>

| <span data-ttu-id="dd981-155">Attribut</span><span class="sxs-lookup"><span data-stu-id="dd981-155">Attribute</span></span> | <span data-ttu-id="dd981-156">Typ</span><span class="sxs-lookup"><span data-stu-id="dd981-156">Type</span></span> | <span data-ttu-id="dd981-157">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="dd981-157">Description</span></span> |
| --- | --- | --- |
| `title` | <span data-ttu-id="dd981-158">string</span><span class="sxs-lookup"><span data-stu-id="dd981-158">string</span></span> | <span data-ttu-id="dd981-159">Dieses Attribut wird unter dem App-Namen und rechts neben dem App-Symbol angezeigt.</span><span class="sxs-lookup"><span data-stu-id="dd981-159">This attribute appears below the app name and to the right of the app icon.</span></span> |
| `height` | <span data-ttu-id="dd981-160">Zahl oder Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="dd981-160">number or string</span></span> | <span data-ttu-id="dd981-161">Dieses Attribut kann eine Zahl sein, die die Höhe des Aufgabenmoduls in Pixeln oder `small` `medium` , oder `large` darstellt.</span><span class="sxs-lookup"><span data-stu-id="dd981-161">This attribute can be a number representing the task module's height in pixels, or `small`, `medium`, or `large`.</span></span> <span data-ttu-id="dd981-162">Weitere Informationen finden Sie unter [Größe des Aufgabenmoduls.](#task-module-sizing)</span><span class="sxs-lookup"><span data-stu-id="dd981-162">For more information, see [task module sizing](#task-module-sizing).</span></span> |
| `width` | <span data-ttu-id="dd981-163">Zahl oder Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="dd981-163">number or string</span></span> | <span data-ttu-id="dd981-164">Dieses Attribut kann eine Zahl sein, die die Breite des Aufgabenmoduls in Pixeln oder `small` `medium` , oder `large` darstellt.</span><span class="sxs-lookup"><span data-stu-id="dd981-164">This attribute can be a number representing the task module's width in pixels, or `small`, `medium`, or `large`.</span></span> <span data-ttu-id="dd981-165">Weitere Informationen finden Sie unter [Größe des Aufgabenmoduls.](#task-module-sizing)</span><span class="sxs-lookup"><span data-stu-id="dd981-165">For more information, see [task module sizing](#task-module-sizing).</span></span> |
| `url` | <span data-ttu-id="dd981-166">string</span><span class="sxs-lookup"><span data-stu-id="dd981-166">string</span></span> | <span data-ttu-id="dd981-167">Dieses Attribut ist die URL der Seite, die als `<iframe>` innerhalb des Aufgabenmoduls geladen wurde.</span><span class="sxs-lookup"><span data-stu-id="dd981-167">This attribute is the URL of the page loaded as an `<iframe>` inside the task module.</span></span> <span data-ttu-id="dd981-168">Die Domäne der URL muss sich im [ValidDomains-Array](~/resources/schema/manifest-schema.md#validdomains) der App im Manifest Ihrer App befinden.</span><span class="sxs-lookup"><span data-stu-id="dd981-168">The URL's domain must be in the app's [validDomains array](~/resources/schema/manifest-schema.md#validdomains) in your app's manifest.</span></span> |
| `card` | <span data-ttu-id="dd981-169">Anlage einer adaptiven Karte oder eines Adaptive Card-Bots</span><span class="sxs-lookup"><span data-stu-id="dd981-169">Adaptive Card or Adaptive Card bot card attachment</span></span> | <span data-ttu-id="dd981-170">Dieses Attribut ist der JSON-Code für die adaptive Karte, die im Aufgabenmodul angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="dd981-170">This attribute is the JSON for the Adaptive Card to appear in the task module.</span></span> <span data-ttu-id="dd981-171">Wenn der Benutzer von einem Bot aufruft, verwenden Sie den JSON-Code für adaptive Karten in einem Bot `attachment` Framework-Objekt.</span><span class="sxs-lookup"><span data-stu-id="dd981-171">If the user is invoking from a bot, use the Adaptive Card JSON in a Bot Framework `attachment` object.</span></span> <span data-ttu-id="dd981-172">Auf einer Registerkarte muss der Benutzer eine adaptive Karte verwenden.</span><span class="sxs-lookup"><span data-stu-id="dd981-172">From a tab, the user must use an Adaptive Card.</span></span> <span data-ttu-id="dd981-173">Weitere Informationen finden Sie unter ["Adaptive Karte" oder "Botkartenanlage für adaptive Karten"](#adaptive-card-or-adaptive-card-bot-card-attachment)</span><span class="sxs-lookup"><span data-stu-id="dd981-173">For more information, see [Adaptive Card or Adaptive Card bot card attachment](#adaptive-card-or-adaptive-card-bot-card-attachment)</span></span> |
| `fallbackUrl` | <span data-ttu-id="dd981-174">string</span><span class="sxs-lookup"><span data-stu-id="dd981-174">string</span></span> | <span data-ttu-id="dd981-175">Dieses Attribut öffnet die URL in einer Browserregisterkarte, wenn ein Client das Aufgabenmodulfeature nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="dd981-175">This attribute opens the URL in a browser tab, if a client does not support the task module feature.</span></span> |
| `completionBotId` | <span data-ttu-id="dd981-176">string</span><span class="sxs-lookup"><span data-stu-id="dd981-176">string</span></span> | <span data-ttu-id="dd981-177">Dieses Attribut gibt eine Bot-App-ID an, um das Ergebnis der Benutzerinteraktion mit dem Aufgabenmodul zu senden.</span><span class="sxs-lookup"><span data-stu-id="dd981-177">This attribute specifies a bot App ID to send the result of the user's interaction with the task module.</span></span> <span data-ttu-id="dd981-178">Wenn angegeben, empfängt der Bot ein `task/submit invoke` Ereignis mit einem JSON-Objekt in der Ereignisnutzlast.</span><span class="sxs-lookup"><span data-stu-id="dd981-178">If specified, the bot receives a `task/submit invoke` event with a JSON object in the event payload.</span></span> |

> [!NOTE]
> <span data-ttu-id="dd981-179">Das Aufgabenmodulfeature erfordert, dass die Domänen aller URLs, die Sie laden möchten, im Array im Manifest Ihrer App enthalten `validDomains` sind.</span><span class="sxs-lookup"><span data-stu-id="dd981-179">The task module feature requires that the domains of any URLs you want to load are included in the `validDomains` array in your app's manifest.</span></span>

<span data-ttu-id="dd981-180">Im nächsten Abschnitt wird die Größe des Aufgabenmoduls angegeben, mit der der Benutzer die Höhe und Breite des Aufgabenmoduls festlegen kann.</span><span class="sxs-lookup"><span data-stu-id="dd981-180">The next section specifies task module sizing that enables the user to set the height and width of the task module.</span></span>

## <a name="task-module-sizing"></a><span data-ttu-id="dd981-181">Größe des Aufgabenmoduls</span><span class="sxs-lookup"><span data-stu-id="dd981-181">Task module sizing</span></span>

<span data-ttu-id="dd981-182">Die Verwendung ganzzahliger Zahlen für `TaskInfo.width` und legt die Höhe und Breite des `TaskInfo.height` Aufgabenmoduls in Pixel fest.</span><span class="sxs-lookup"><span data-stu-id="dd981-182">Using integers for `TaskInfo.width` and `TaskInfo.height`, sets the height and width of the task module in pixels.</span></span> <span data-ttu-id="dd981-183">Abhängig von der Größe des Fensters und der Bildschirmauflösung des Teams werden sie jedoch proportional reduziert, während das Seitenverhältnis, das breite oder höhe ist, beibehalten wird.</span><span class="sxs-lookup"><span data-stu-id="dd981-183">However, depending on the size of the Team's window and screen resolution they are reduced proportionally while maintaining the aspect ratio that is width or height.</span></span>

<span data-ttu-id="dd981-184">If `TaskInfo.width` and are , or , the size of the red rectangle in the following image `TaskInfo.height` is a proportion of the available `"small"` `"medium"` `"large"` space, 20%, 50% and 60% for `width` and 20%, 50% and 66% for `height` :</span><span class="sxs-lookup"><span data-stu-id="dd981-184">If `TaskInfo.width` and `TaskInfo.height` are `"small"`, `"medium"`, or `"large"`, the size of the red rectangle in the following image is a proportion of the available space, 20%, 50%, and 60% for `width` and 20%, 50%, and 66% for `height`:</span></span>

![Beispiel für ein Aufgabenmodul](~/assets/images/task-module/task-module-example.png)

<span data-ttu-id="dd981-186">Aufgabenmodule, die von einer Registerkarte aufgerufen werden, können dynamisch geändert werden.</span><span class="sxs-lookup"><span data-stu-id="dd981-186">Task modules invoked from a tab can be dynamically resized.</span></span> <span data-ttu-id="dd981-187">Nach dem Aufruf `tasks.startTask()` können Sie `tasks.updateTask(newSize)` aufrufen, wo die Höhen- und Breiteneigenschaften des newSize-Objekts der TaskInfo-Spezifikation entsprechen, z. `{ height: 'medium', width: 'medium' }` B. .</span><span class="sxs-lookup"><span data-stu-id="dd981-187">After calling `tasks.startTask()` you can call `tasks.updateTask(newSize)` where height and width properties on the newSize object conform to the TaskInfo specification, for example `{ height: 'medium', width: 'medium' }`.</span></span>

<span data-ttu-id="dd981-188">Der nächste Abschnitt enthält Beispiele für das Einbetten von Aufgabenmodulen in ein YouTube-Video und eine PowerApp.</span><span class="sxs-lookup"><span data-stu-id="dd981-188">The next section provides examples of embedding task modules in a YouTube video and a PowerApp.</span></span>

## <a name="task-module-css-for-html-or-javascript-task-modules"></a><span data-ttu-id="dd981-189">Aufgabenmodul-CSS für HTML- oder JavaScript-Aufgabenmodule</span><span class="sxs-lookup"><span data-stu-id="dd981-189">Task module CSS for HTML or JavaScript task modules</span></span>

<span data-ttu-id="dd981-190">HTML- oder JavaScript-basierte Aufgabenmodule haben Zugriff auf den gesamten Bereich des Aufgabenmoduls unterhalb des Headers.</span><span class="sxs-lookup"><span data-stu-id="dd981-190">HTML or JavaScript-based task modules have access to the entire area of the task module below the header.</span></span> <span data-ttu-id="dd981-191">Dies bietet zwar ein hohes Maß an Flexibilität, wenn Sie den Abstand an den Rändern an den Kopfzeilenelementen ausrichten möchten und unnötige Bildlaufleisten vermeiden möchten, muss der Benutzer das richtige CSS bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="dd981-191">While that offers a great deal of flexibility, if you want padding around the edges to align with the header elements and avoid unnecessary scroll bars, the user must provide the right CSS.</span></span> <span data-ttu-id="dd981-192">Die nächsten Abschnitte enthalten einige Beispiele für einige Anwendungsfälle.</span><span class="sxs-lookup"><span data-stu-id="dd981-192">The next sections provide some examples for a few use cases.</span></span>

<span data-ttu-id="dd981-193">**Beispiel 1: YouTube-Video**</span><span class="sxs-lookup"><span data-stu-id="dd981-193">**Example 1: YouTube video**</span></span>

<span data-ttu-id="dd981-194">YouTube bietet die Möglichkeit, Videos auf Webseiten einzubetten.</span><span class="sxs-lookup"><span data-stu-id="dd981-194">YouTube offers the ability to embed videos on web pages.</span></span> <span data-ttu-id="dd981-195">Videos können ganz einfach mithilfe einer einfachen Stub-Webseite in Webseiten in ein Aufgabenmodul eingebettet werden.</span><span class="sxs-lookup"><span data-stu-id="dd981-195">It is easy to embed videos on web pages in a task module using a simple stub web page.</span></span>

![YouTube-Video](~/assets/images/task-module/youtube-example.png)

<span data-ttu-id="dd981-197">Der folgende Code enthält ein Beispiel für den HTML-Code für die Webseite ohne CSS:</span><span class="sxs-lookup"><span data-stu-id="dd981-197">The following code provides an example of the HTML for the web page without the CSS:</span></span>

```html
<!DOCTYPE html>
<html lang="en">
<head>
  ⋮
</head>
<body>
  <div id="embed-container">
    <iframe width="1000" height="700" src="https://www.youtube.com/embed/rd0Rd8w3FZ0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen=""></iframe>
  </div>
</body>
</html>
```

<span data-ttu-id="dd981-198">Der folgende Code enthält ein Beispiel für das CSS:</span><span class="sxs-lookup"><span data-stu-id="dd981-198">The following code provides an example of the CSS:</span></span>

```css
#embed-container iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 95%;
    height: 95%;
    padding-left: 20px;
    padding-right: 20px;
    padding-top: 10px;
    padding-bottom: 10px;
    border-style: none;
}
```

<span data-ttu-id="dd981-199">**Beispiel 2: PowerApp**</span><span class="sxs-lookup"><span data-stu-id="dd981-199">**Example 2: PowerApp**</span></span>

<span data-ttu-id="dd981-200">Der Benutzer kann den gleichen Ansatz verwenden, um auch eine PowerApp einzubetten.</span><span class="sxs-lookup"><span data-stu-id="dd981-200">The user can use the same approach to embed a PowerApp as well.</span></span> <span data-ttu-id="dd981-201">Da die Höhe oder Breite einer einzelnen PowerApp angepasst werden kann, kann der Benutzer die Höhe und Breite anpassen, um die gewünschte Präsentation zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="dd981-201">As the height or width of any individual PowerApp is customizable, the user can adjust the height and width to achieve the desired presentation.</span></span>

![Ressourcenverwaltung PowerApp](~/assets/images/task-module/powerapp-example.png)

<span data-ttu-id="dd981-203">Der folgende Code enthält ein Beispiel für den HTML-Code für PowerApp:</span><span class="sxs-lookup"><span data-stu-id="dd981-203">The following code provides an example of the HTML for PowerApp:</span></span>

```html
<iframe width="720" height="520" src="https://web.powerapps.com/webplayer/iframeapp?source=iframe&screenColor=rgba(104,101,171,1)&appId=/providers/Microsoft.PowerApps/apps/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"></iframe>
```

<span data-ttu-id="dd981-204">Der folgende Code enthält ein Beispiel für das CSS:</span><span class="sxs-lookup"><span data-stu-id="dd981-204">The following code provides an example of the CSS:</span></span>

```css
#embed-container iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 94%;
    height: 95%;
    padding-left: 20px;
    padding-right: 20px;
    padding-top: 10px;
    padding-bottom: 10px;
    border-style: none;
}
```

<span data-ttu-id="dd981-205">Der nächste Abschnitt enthält Details zum Aufrufen Ihrer Karte mithilfe einer adaptiven Karte oder einer Adaptive Card-Bot-Kartenanlage.</span><span class="sxs-lookup"><span data-stu-id="dd981-205">The next section provides details on invoking your card using Adaptive Card or Adaptive Card bot card attachment.</span></span>

## <a name="adaptive-card-or-adaptive-card-bot-card-attachment"></a><span data-ttu-id="dd981-206">Anlage einer adaptiven Karte oder eines Adaptive Card-Bots</span><span class="sxs-lookup"><span data-stu-id="dd981-206">Adaptive Card or Adaptive Card bot card attachment</span></span>

<span data-ttu-id="dd981-207">Je nachdem, wie Sie Ihre `card` aufrufen, müssen Sie entweder eine adaptive Karte oder eine Adaptive Card-Bot-Kartenanlage verwenden, bei der es sich um eine adaptive Karte handelt, die in ein Anlagenobjekt eingeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="dd981-207">Depending on how you are invoking your `card`, you must use either an Adaptive Card or an Adaptive Card bot card attachment, which is an Adaptive Card wrapped in an attachment object.</span></span>

<span data-ttu-id="dd981-208">Wenn Sie von einer Registerkarte aufrufen, muss der Benutzer eine adaptive Karte verwenden.</span><span class="sxs-lookup"><span data-stu-id="dd981-208">When you are invoking from a tab, the user must use an Adaptive Card.</span></span>

<span data-ttu-id="dd981-209">Der folgende Code enthält ein Beispiel für eine adaptive Karte:</span><span class="sxs-lookup"><span data-stu-id="dd981-209">The following code provides an example of an Adaptive Card:</span></span>

```json
{
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
}
```

<span data-ttu-id="dd981-210">Der folgende Code enthält ein Beispiel für eine Adaptive Card-Bot-Kartenanlage, wenn Sie von einem Bot aufrufen:</span><span class="sxs-lookup"><span data-stu-id="dd981-210">The following code provides an example of an Adaptive Card bot card attachment when you are invoking from a bot:</span></span>

```json
{
    "contentType": "application/vnd.microsoft.card.adaptive",
    "content": {
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
    }
}
```

<span data-ttu-id="dd981-211">Der nächste Abschnitt enthält Details zur Deep Link-Syntax des Aufgabenmoduls, einschließlich des `TaskInfo` Objekts `APP_ID` und `BOT_APP_ID` .</span><span class="sxs-lookup"><span data-stu-id="dd981-211">The next section provides details on task module deep link syntax including the `TaskInfo` object and `APP_ID` and `BOT_APP_ID`.</span></span>

## <a name="task-module-deep-link-syntax"></a><span data-ttu-id="dd981-212">Deep Link-Syntax des Aufgabenmoduls</span><span class="sxs-lookup"><span data-stu-id="dd981-212">Task module deep link syntax</span></span>

<span data-ttu-id="dd981-213">Ein Deep-Link des Aufgabenmoduls ist eine Serialisierung des TaskInfo-Objekts mit den folgenden zwei weiteren Details `APP_ID` und optional `BOT_APP_ID` dem:</span><span class="sxs-lookup"><span data-stu-id="dd981-213">A task module deep link is a serialization of the TaskInfo object with the following two other details, `APP_ID` and optionally the `BOT_APP_ID`:</span></span>

`https://teams.microsoft.com/l/task/APP_ID?url=<TaskInfo.url>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID`

`https://teams.microsoft.com/l/task/APP_ID?card=<TaskInfo.card>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID`

<span data-ttu-id="dd981-214">Die Datentypen und zulässigen Werte für `<TaskInfo.url>` , , und , finden Sie unter `<TaskInfo.card>` `<TaskInfo.height>` `<TaskInfo.width>` `<TaskInfo.title>` [TaskInfo -Objekt](#the-taskinfo-object).</span><span class="sxs-lookup"><span data-stu-id="dd981-214">For the data types and allowable values for `<TaskInfo.url>`, `<TaskInfo.card>`, `<TaskInfo.height>`, `<TaskInfo.width>`, and `<TaskInfo.title>`, see [TaskInfo object](#the-taskinfo-object).</span></span>

> [!TIP]
> <span data-ttu-id="dd981-215">Die URL codiert den Deep-Link, wenn der Parameter verwendet wird, z. B. die `card` [ `encodeURI()` JavaScript-Funktion.](https://www.w3schools.com/jsref/jsref_encodeURI.asp)</span><span class="sxs-lookup"><span data-stu-id="dd981-215">URL encode the deep link when using the `card` parameter, for example, JavaScript's [`encodeURI()` function](https://www.w3schools.com/jsref/jsref_encodeURI.asp).</span></span>

<span data-ttu-id="dd981-216">Die folgende Tabelle enthält Informationen zu `APP_ID` `BOT_APP_ID` und:</span><span class="sxs-lookup"><span data-stu-id="dd981-216">The following table provides information on `APP_ID` and `BOT_APP_ID`:</span></span>

| <span data-ttu-id="dd981-217">Wert</span><span class="sxs-lookup"><span data-stu-id="dd981-217">Value</span></span> | <span data-ttu-id="dd981-218">Typ</span><span class="sxs-lookup"><span data-stu-id="dd981-218">Type</span></span> | <span data-ttu-id="dd981-219">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="dd981-219">Required</span></span> | <span data-ttu-id="dd981-220">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="dd981-220">Description</span></span> |
| --- | --- | --- | --- |
| `APP_ID` | <span data-ttu-id="dd981-221">string</span><span class="sxs-lookup"><span data-stu-id="dd981-221">string</span></span> | <span data-ttu-id="dd981-222">Ja</span><span class="sxs-lookup"><span data-stu-id="dd981-222">Yes</span></span> | <span data-ttu-id="dd981-223">Die [ID](~/resources/schema/manifest-schema.md#id) der App, die das Aufgabenmodul aufruft.</span><span class="sxs-lookup"><span data-stu-id="dd981-223">The [ID](~/resources/schema/manifest-schema.md#id) of the app invoking the task module.</span></span> <span data-ttu-id="dd981-224">Das [Array "validDomains"](~/resources/schema/manifest-schema.md#validdomains) im Manifest `APP_ID` muss die Domäne für `url` `url` "if" in der URL enthalten.</span><span class="sxs-lookup"><span data-stu-id="dd981-224">The [validDomains array](~/resources/schema/manifest-schema.md#validdomains) in the manifest for `APP_ID` must contain the domain for `url` if `url` is in the URL.</span></span> <span data-ttu-id="dd981-225">Die App-ID ist bereits bekannt, wenn ein Aufgabenmodul von einer Registerkarte oder einem Bot aufgerufen wird, weshalb sie nicht in enthalten `TaskInfo` ist.</span><span class="sxs-lookup"><span data-stu-id="dd981-225">The app ID is already known when a task module is invoked from a tab or a bot, which is why it is not included in `TaskInfo`.</span></span> |
| `BOT_APP_ID` | <span data-ttu-id="dd981-226">string</span><span class="sxs-lookup"><span data-stu-id="dd981-226">string</span></span> | <span data-ttu-id="dd981-227">Nein</span><span class="sxs-lookup"><span data-stu-id="dd981-227">No</span></span> | <span data-ttu-id="dd981-228">Wenn ein Wert für `completionBotId` angegeben wird, wird das `result` Objekt mithilfe einer Nachricht an den `task/submit invoke` angegebenen Bot gesendet.</span><span class="sxs-lookup"><span data-stu-id="dd981-228">If a value for `completionBotId` is specified, the `result` object is sent using a `task/submit invoke` message to the specified bot.</span></span> <span data-ttu-id="dd981-229">`BOT_APP_ID` muss im Manifest der App als Bot angegeben werden, d. h., Sie können ihn nicht an einen Bot senden.</span><span class="sxs-lookup"><span data-stu-id="dd981-229">`BOT_APP_ID` must be specified as a bot in the app's manifest, that is you cannot send it to any bot.</span></span> |

> [!NOTE]
> <span data-ttu-id="dd981-230">`APP_ID` und `BOT_APP_ID` kann in vielen Fällen identisch sein, wenn eine App über einen empfohlenen Bot verfügt, der als App-ID verwendet werden soll, falls vorhanden.</span><span class="sxs-lookup"><span data-stu-id="dd981-230">`APP_ID` and `BOT_APP_ID` can be the same in many cases, if an app has a recommended bot to use as an app's ID if there is one.</span></span>

<span data-ttu-id="dd981-231">Der nächste Abschnitt enthält Details zur Verwendung einer Tastatur mit dem Aufgabenmodul Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="dd981-231">The next section provides details on using a keyboard with your app's task module.</span></span>

## <a name="keyboard-and-accessibility-guidelines"></a><span data-ttu-id="dd981-232">Richtlinien für Tastatur und Barrierefreiheit</span><span class="sxs-lookup"><span data-stu-id="dd981-232">Keyboard and accessibility guidelines</span></span>

<span data-ttu-id="dd981-233">Bei HTML- oder JavaScript-basierten Aufgabenmodulen müssen Sie sicherstellen, dass das Aufgabenmodul Ihrer App mit einer Tastatur verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="dd981-233">With HTML or JavaScript-based task modules, you must ensure your app's task module can be used with a keyboard.</span></span> <span data-ttu-id="dd981-234">Sprachausgabeprogramme sind auch von der Möglichkeit abhängig, mit der Tastatur zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="dd981-234">Screen reader programs also depend on the ability to navigate using the keyboard.</span></span> <span data-ttu-id="dd981-235">Dazu gehören die folgenden beiden Dinge:</span><span class="sxs-lookup"><span data-stu-id="dd981-235">This includes the following two things:</span></span>

* <span data-ttu-id="dd981-236">Verwenden des [Tabindex-Attributs](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/tabindex) in Ihren HTML-Tags, um zu steuern, welche Elemente fokussiert werden können.</span><span class="sxs-lookup"><span data-stu-id="dd981-236">Using the [tabindex attribute](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/tabindex) in your HTML tags to control which elements can be focused.</span></span> <span data-ttu-id="dd981-237">Verwenden Sie außerdem das tabindex-Attribut, um zu ermitteln, wo es an der sequenziellen Tastaturnavigation beteiligt ist, in der Regel mit den Tasten <kbd>Tab und</kbd> <kbd>UMSCHALTTASTE.</kbd></span><span class="sxs-lookup"><span data-stu-id="dd981-237">Also, use tabindex attribute to identify where it participates in sequential keyboard navigation usually with the <kbd>Tab</kbd> and <kbd>Shift-Tab</kbd> keys.</span></span>
* <span data-ttu-id="dd981-238">Behandeln des <kbd>Esc-Schlüssels</kbd> im JavaScript für Ihr Aufgabenmodul.</span><span class="sxs-lookup"><span data-stu-id="dd981-238">Handling the <kbd>Esc</kbd> key in the JavaScript for your task module.</span></span> <span data-ttu-id="dd981-239">Der folgende Code enthält ein Beispiel <kbd></kbd> für die Behandlung des Esc-Schlüssels:</span><span class="sxs-lookup"><span data-stu-id="dd981-239">The following code provides an example of how to handle the <kbd>Esc</kbd> key:</span></span>

    ```javascript
    // Handle the Esc key
    document.onkeyup = function(event) {
    if ((event.key === 27) || (event.key === "Escape")) {
      microsoftTeams.submitTask(null); // this will return an err object to the completionHandler()
      }
    }
    ```

<span data-ttu-id="dd981-240">Microsoft Teams stellt sicher, dass die Tastaturnavigation vom Aufgabenmodulheader in Ihren HTML-Code ordnungsgemäß funktioniert und umgekehrt.</span><span class="sxs-lookup"><span data-stu-id="dd981-240">Microsoft Teams ensures that keyboard navigation works properly from the task module header into your HTML and vice-versa.</span></span>

## <a name="code-sample"></a><span data-ttu-id="dd981-241">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="dd981-241">Code sample</span></span>

|<span data-ttu-id="dd981-242">Beispielname</span><span class="sxs-lookup"><span data-stu-id="dd981-242">Sample name</span></span> | <span data-ttu-id="dd981-243">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="dd981-243">Description</span></span> | <span data-ttu-id="dd981-244">.NET</span><span class="sxs-lookup"><span data-stu-id="dd981-244">.NET</span></span> | <span data-ttu-id="dd981-245">Node.js</span><span class="sxs-lookup"><span data-stu-id="dd981-245">Node.js</span></span>|
|----------------|-----------------|--------------|----------------|
|<span data-ttu-id="dd981-246">Aufgabenmodul-Beispielbots-V4</span><span class="sxs-lookup"><span data-stu-id="dd981-246">Task module sample bots-V4</span></span> | <span data-ttu-id="dd981-247">Beispiele zum Erstellen von Aufgabenmodulen.</span><span class="sxs-lookup"><span data-stu-id="dd981-247">Samples for creating task modules.</span></span> |[<span data-ttu-id="dd981-248">View</span><span class="sxs-lookup"><span data-stu-id="dd981-248">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/54.teams-task-module)|[<span data-ttu-id="dd981-249">View</span><span class="sxs-lookup"><span data-stu-id="dd981-249">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/54.teams-task-module)|
|<span data-ttu-id="dd981-250">Aufgabenmodul-Beispielregisterkarten und Bots-V3</span><span class="sxs-lookup"><span data-stu-id="dd981-250">Task module sample tabs and bots-V3</span></span> | <span data-ttu-id="dd981-251">Beispiele zum Erstellen von Aufgabenmodulen.</span><span class="sxs-lookup"><span data-stu-id="dd981-251">Samples for creating task modules.</span></span> |[<span data-ttu-id="dd981-252">View</span><span class="sxs-lookup"><span data-stu-id="dd981-252">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/csharp)|[<span data-ttu-id="dd981-253">View</span><span class="sxs-lookup"><span data-stu-id="dd981-253">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/nodejs)| 

## <a name="see-also"></a><span data-ttu-id="dd981-254">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="dd981-254">See also</span></span>

* [<span data-ttu-id="dd981-255">Geräteberechtigungen anfordern</span><span class="sxs-lookup"><span data-stu-id="dd981-255">Request device permissions</span></span>](~/concepts/device-capabilities/native-device-permissions.md)
* [<span data-ttu-id="dd981-256">Integrieren von Medienfunktionen</span><span class="sxs-lookup"><span data-stu-id="dd981-256">Integrate media capabilities</span></span>](~/concepts/device-capabilities/mobile-camera-image-permissions.md)
* [<span data-ttu-id="dd981-257">Integrieren von QR- oder Strichcodescannern in Teams</span><span class="sxs-lookup"><span data-stu-id="dd981-257">Integrate QR or barcode scanner capability in Teams</span></span>](~/concepts/device-capabilities/qr-barcode-scanner-capability.md)
* [<span data-ttu-id="dd981-258">Integrieren von Standortfunktionen in Teams</span><span class="sxs-lookup"><span data-stu-id="dd981-258">Integrate location capabilities in Teams</span></span>](~/concepts/device-capabilities/location-capability.md)

## <a name="next-step"></a><span data-ttu-id="dd981-259">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="dd981-259">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dd981-260">Verwenden von Aufgabenmodulen in Registerkarten</span><span class="sxs-lookup"><span data-stu-id="dd981-260">Use task modules in tabs</span></span>](~/task-modules-and-cards/task-modules/task-modules-tabs.md)