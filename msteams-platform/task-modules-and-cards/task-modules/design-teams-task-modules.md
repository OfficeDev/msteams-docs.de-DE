---
title: Entwerfen von Aufgaben Modulen
author: heath-hamilton
description: Hier erfahren Sie, wie Sie Aufgaben Module für Teams-apps entwerfen und das Microsoft Teams UI Kit abrufen.
ms.author: lajanuar
ms.topic: reference
ms.openlocfilehash: 41584ecf58ca7718290e58e5845549e4579dac64
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "49606199"
---
# <a name="designing-task-modules-for-your-microsoft-teams-app"></a><span data-ttu-id="b2abd-103">Entwerfen von Aufgaben Modulen für Ihre Microsoft Teams-App</span><span class="sxs-lookup"><span data-stu-id="b2abd-103">Designing task modules for your Microsoft Teams app</span></span>

<span data-ttu-id="b2abd-104">Sie können modale Popup-Erlebnisse in Ihrer Teams-App mit Aufgaben Modulen erstellen.</span><span class="sxs-lookup"><span data-stu-id="b2abd-104">You can create modal popup experiences in your Teams app with task modules.</span></span> <span data-ttu-id="b2abd-105">Verwenden Sie diese Funktion, um Rich-Medien und-Informationen anzuzeigen oder eine komplexe Aufgabe abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="b2abd-105">Use this capability to display rich media and information or complete a complex task.</span></span>

:::image type="content" source="../../assets/images/task-module/task-module-overview.png" alt-text="Beispiel zeigt ein Aufgabenmodul." border="false":::

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="b2abd-107">Microsoft Teams-UI-Kit</span><span class="sxs-lookup"><span data-stu-id="b2abd-107">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="b2abd-108">Ausführlichere Entwurfsrichtlinien für Aufgaben Module, einschließlich der Elemente, die Sie nach Bedarf erfassen und ändern können, finden Sie im Microsoft Teams UI Kit.</span><span class="sxs-lookup"><span data-stu-id="b2abd-108">You can find more comprehensive task module design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b2abd-109">Abrufen des Microsoft Teams UI Kit (Figma)</span><span class="sxs-lookup"><span data-stu-id="b2abd-109">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="open-a-task-module"></a><span data-ttu-id="b2abd-110">Öffnen eines Aufgabenmoduls</span><span class="sxs-lookup"><span data-stu-id="b2abd-110">Open a task module</span></span>

<span data-ttu-id="b2abd-111">Aufgaben Module können von fast überall in Ihrer APP gestartet werden.</span><span class="sxs-lookup"><span data-stu-id="b2abd-111">Task modules can be launched from almost anywhere in your app.</span></span>

* <span data-ttu-id="b2abd-112">**Tab**: ein Aufgabenmodul kann von einem beliebigen Link innerhalb einer Registerkarte oder eines IFRAME gestartet werden.</span><span class="sxs-lookup"><span data-stu-id="b2abd-112">**Tab**: A task module can be launched from any link within a tab or iframe.</span></span> <span data-ttu-id="b2abd-113">Verwenden Sie in Szenarien, in denen der Benutzer sich auf eine Interaktion konzentrieren soll.</span><span class="sxs-lookup"><span data-stu-id="b2abd-113">Use in scenarios where you want the user to focus on an interaction.</span></span>
* <span data-ttu-id="b2abd-114">**Bot**: ein Aufgabenmodul kann über einen Link in einer bot-Nachricht gestartet werden.</span><span class="sxs-lookup"><span data-stu-id="b2abd-114">**Bot**: A task module can be launched from a link inside a bot message.</span></span>
* <span data-ttu-id="b2abd-115">**Adaptive Karte**: ein Aufgabenmodul kann von einer adaptiven Karte gestartet werden (mit einer Messaging Erweiterung oder einem bot gesendet), wenn ein Benutzer eine Schaltfläche auswählt.</span><span class="sxs-lookup"><span data-stu-id="b2abd-115">**Adaptive Card**: A task module can be launched from an Adaptive Card (sent with a messaging extension or by a bot) when a user selects a button.</span></span>
* <span data-ttu-id="b2abd-116">**Messaging-Erweiterung (Aktionsbefehle)**: mit Messaging Erweiterungen können Sie eine bestimmte Aktion für Nachrichteninhalte durchführen.</span><span class="sxs-lookup"><span data-stu-id="b2abd-116">**Messaging extension (action commands)**: Messaging extensions allow you to take a particular action on message content.</span></span> <span data-ttu-id="b2abd-117">Durch Auswählen einer Aktion wird ein Aufgabenmodul geöffnet.</span><span class="sxs-lookup"><span data-stu-id="b2abd-117">Selecting an action opens a task module.</span></span>
* <span data-ttu-id="b2abd-118">**Messaging Erweiterung (Kontext des verfassen-Felds)**: im Feld Verfassen können Sie eine Messaging Erweiterung entwerfen, um anstelle des typischen Flyouts ein Aufgabenmodul zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="b2abd-118">**Messaging extension (compose box context)**: In the compose box, you can design a messaging extension to open a task module instead of the typical flyout.</span></span> <span data-ttu-id="b2abd-119">Reservieren Sie Aufgaben Module für komplexe Interaktionen, beispielsweise das Ausfüllen eines Formulars.</span><span class="sxs-lookup"><span data-stu-id="b2abd-119">Reserve task modules for complex interactions, such as completing a form.</span></span>

## <a name="anatomy"></a><span data-ttu-id="b2abd-120">Anatomie</span><span class="sxs-lookup"><span data-stu-id="b2abd-120">Anatomy</span></span>

:::image type="content" source="../../assets/images/task-module/task-module-anatomy.png" alt-text="Illustration, die die Benutzeroberflächen Anatomie eines Aufgabenmoduls veranschaulicht." border="false":::

<span data-ttu-id="b2abd-122">Aufgaben Module sind sehr flexible Oberflächen.</span><span class="sxs-lookup"><span data-stu-id="b2abd-122">Task modules are very flexible surfaces.</span></span> <span data-ttu-id="b2abd-123">Sie können mit iframes erstellt werden, indem Sie andere Benutzeroberflächenvorlagen einziehen, um von Partnern erstellte Erfahrungen zu hosten.</span><span class="sxs-lookup"><span data-stu-id="b2abd-123">They can be built with iframes, pulling in other UI templates, to host partner-built experiences.</span></span> <span data-ttu-id="b2abd-124">Dies wird für die meiste polierte Erfahrung bevorzugt.</span><span class="sxs-lookup"><span data-stu-id="b2abd-124">This is preferred for the most polished experience.</span></span>

<span data-ttu-id="b2abd-125">Sie können auch mit dem [Adaptive Card](../../task-modules-and-cards/cards/design-effective-cards.md) -Framework erstellt werden, was eine einfachere und schnellere Möglichkeit zur Ausführung häufig auftretender Szenarien (beispielsweise Formulare) darstellen kann.</span><span class="sxs-lookup"><span data-stu-id="b2abd-125">They can also be built with the [Adaptive Card](../../task-modules-and-cards/cards/design-effective-cards.md) framework, which can be a simpler and faster way to execute common scenarios (such as forms).</span></span>

|<span data-ttu-id="b2abd-126">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="b2abd-126">Counter</span></span>|<span data-ttu-id="b2abd-127">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b2abd-127">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="b2abd-128">1</span><span class="sxs-lookup"><span data-stu-id="b2abd-128">1</span></span>|<span data-ttu-id="b2abd-129">**App-Symbol**</span><span class="sxs-lookup"><span data-stu-id="b2abd-129">**App icon**</span></span>|
|<span data-ttu-id="b2abd-130">2 </span><span class="sxs-lookup"><span data-stu-id="b2abd-130">2</span></span>|<span data-ttu-id="b2abd-131">**App-Name**: vollständiger Name Ihrer APP.</span><span class="sxs-lookup"><span data-stu-id="b2abd-131">**App name**: Full name of your app.</span></span>|
|<span data-ttu-id="b2abd-132">3 </span><span class="sxs-lookup"><span data-stu-id="b2abd-132">3</span></span>|<span data-ttu-id="b2abd-133">**Kopfzeile**: machen Sie Kopfzeilen klar und prägnant.</span><span class="sxs-lookup"><span data-stu-id="b2abd-133">**Header**: Make headers clear and concise.</span></span> <span data-ttu-id="b2abd-134">Beschreiben Sie die Aufgabe, die die Benutzer ausführen sollen.</span><span class="sxs-lookup"><span data-stu-id="b2abd-134">Describe the task you want users to complete.</span></span>
|<span data-ttu-id="b2abd-135">4 </span><span class="sxs-lookup"><span data-stu-id="b2abd-135">4</span></span>|<span data-ttu-id="b2abd-136">**Schaltfläche Schließen**: ermöglicht Benutzern das Auffinden von App-Inhalten, die Sie einfügen möchten.</span><span class="sxs-lookup"><span data-stu-id="b2abd-136">**Close button**: Allows users to find app content they want to insert.</span></span>|
|<span data-ttu-id="b2abd-137">5 </span><span class="sxs-lookup"><span data-stu-id="b2abd-137">5</span></span>|<span data-ttu-id="b2abd-138">**iframe**: reaktionsfähiger Speicherplatz, der Ihre APP-Inhalte hostet.</span><span class="sxs-lookup"><span data-stu-id="b2abd-138">**iframe**: Responsive space that hosts your app content.</span></span>|
|<span data-ttu-id="b2abd-139">6 </span><span class="sxs-lookup"><span data-stu-id="b2abd-139">6</span></span>|<span data-ttu-id="b2abd-140">**Aktionen (optional)**: Schaltflächen im Zusammenhang mit Ihrem App-Inhalt.</span><span class="sxs-lookup"><span data-stu-id="b2abd-140">**Actions (optional)**: Buttons related to your app content.</span></span>|

## <a name="designing-with-ui-templates"></a><span data-ttu-id="b2abd-141">Entwerfen mit Benutzeroberflächenvorlagen</span><span class="sxs-lookup"><span data-stu-id="b2abd-141">Designing with UI templates</span></span>

<span data-ttu-id="b2abd-142">Sie sollten Vorlagen für allgemeine Layouts in ihren Aufgaben Modulen verwenden.</span><span class="sxs-lookup"><span data-stu-id="b2abd-142">Consider using templates for common layouts inside your task modules.</span></span> <span data-ttu-id="b2abd-143">Jeder besteht aus kleineren Komponenten, um ein elegantes, reaktionsfähiges Design zu erstellen, das aus dem Karton oder für Ihr Szenario oder ihr Marken-Erscheinungsbild verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="b2abd-143">Each one is made up of smaller components to create an elegant, responsive design that can be used out of the box or customized for your scenario or with your brand look and feel.</span></span>

* <span data-ttu-id="b2abd-144">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem scannable-Format anzeigen und Benutzern das Ausführen von Aktionen für eine gesamte Liste oder einzelne Elemente gestatten.</span><span class="sxs-lookup"><span data-stu-id="b2abd-144">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="b2abd-145">[Formular](../../concepts/design/design-teams-app-ui-templates.md#form): Formulare dienen zum Sammeln, validieren und Übermitteln von Benutzereingaben in strukturierter Form.</span><span class="sxs-lookup"><span data-stu-id="b2abd-145">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="b2abd-146">[Leer State](../../concepts/design/design-teams-app-ui-templates.md#empty-state): die leere Statusvorlage kann für viele Szenarien verwendet werden, einschließlich Anmeldung, Erstausführung, Fehlermeldungen und mehr.</span><span class="sxs-lookup"><span data-stu-id="b2abd-146">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>

## <a name="examples"></a><span data-ttu-id="b2abd-147">Beispiele</span><span class="sxs-lookup"><span data-stu-id="b2abd-147">Examples</span></span>

### <a name="list"></a><span data-ttu-id="b2abd-148">List</span><span class="sxs-lookup"><span data-stu-id="b2abd-148">List</span></span>

<span data-ttu-id="b2abd-149">Listen funktionieren in einem Aufgabenmodul gut, da Sie einfach zu überprüfen sind.</span><span class="sxs-lookup"><span data-stu-id="b2abd-149">Lists work nicely in a task module because they’re easy to scan.</span></span>

:::image type="content" source="../../assets/images/task-module/list.png" alt-text="Beispielliste in einem Aufgabenmodul." border="false":::

### <a name="form"></a><span data-ttu-id="b2abd-151">Formular</span><span class="sxs-lookup"><span data-stu-id="b2abd-151">Form</span></span>

<span data-ttu-id="b2abd-152">Aufgaben Module eignen sich hervorragend zum Aufstellen von Formularen mit sequenziellen Benutzereingaben und Inline Überprüfung.</span><span class="sxs-lookup"><span data-stu-id="b2abd-152">Task modules are a great place to surface forms with sequential user inputs and inline validation.</span></span> <span data-ttu-id="b2abd-153">Sie können Adaptive Karten als Möglichkeit zum Einbetten von Formularelementen nutzen.</span><span class="sxs-lookup"><span data-stu-id="b2abd-153">You can leverage Adaptive Cards as a way to embed form elements.</span></span>

:::image type="content" source="../../assets/images/task-module/form.png" alt-text="Beispielformular in einem Aufgabenmodul." border="false":::

### <a name="sign-in"></a><span data-ttu-id="b2abd-155">Anmelden</span><span class="sxs-lookup"><span data-stu-id="b2abd-155">Sign in</span></span>

<span data-ttu-id="b2abd-156">Erstellen Sie einen fokussierten Anmelde-oder Registrierungs Fluss mit einer Reihe von Aufgaben Modulen, sodass Benutzer problemlos durch sequenzielle Schritte navigieren können.</span><span class="sxs-lookup"><span data-stu-id="b2abd-156">Create a focused sign in or sign-up flow with a series of task modules, letting users move easily through sequential steps.</span></span>

:::image type="content" source="../../assets/images/task-module/sign-in.png" alt-text="Beispiel für ein anmeldeerlebnis in einem Aufgabenmodul." border="false":::

### <a name="media"></a><span data-ttu-id="b2abd-158">Medien</span><span class="sxs-lookup"><span data-stu-id="b2abd-158">Media</span></span>

<span data-ttu-id="b2abd-159">Einbetten von Medieninhalten in einen Aufgabenmodul für eine fokussierte Anzeigeoberfläche.</span><span class="sxs-lookup"><span data-stu-id="b2abd-159">Embed media content in a task module for a focused viewing experience.</span></span>

:::image type="content" source="../../assets/images/task-module/media.png" alt-text="Beispiel Medieninhalte in einem Aufgabenmodul." border="false":::

### <a name="empty-state"></a><span data-ttu-id="b2abd-161">Leerer Zustand</span><span class="sxs-lookup"><span data-stu-id="b2abd-161">Empty state</span></span>

<span data-ttu-id="b2abd-162">Verwenden Sie für Willkommens-, Fehler-und Erfolgsmeldungen.</span><span class="sxs-lookup"><span data-stu-id="b2abd-162">Use for welcome, error, and success messages.</span></span>

:::image type="content" source="../../assets/images/task-module/empty-state.png" alt-text="Beispiel für einen leeren Zustand in einem Aufgabenmodul." border="false":::

### <a name="image-gallery"></a><span data-ttu-id="b2abd-164">Bildergalerie</span><span class="sxs-lookup"><span data-stu-id="b2abd-164">Image gallery</span></span>

<span data-ttu-id="b2abd-165">Einbetten eines Galerie Karussells in einen iframe.</span><span class="sxs-lookup"><span data-stu-id="b2abd-165">Embed a gallery carousel inside an iframe.</span></span>

:::image type="content" source="../../assets/images/task-module/image-gallery.png" alt-text="Beispielbild Galerie in einem Aufgabenmodul." border="false":::

### <a name="poll"></a><span data-ttu-id="b2abd-167">Umfrage</span><span class="sxs-lookup"><span data-stu-id="b2abd-167">Poll</span></span>

<span data-ttu-id="b2abd-168">In diesem Beispiel werden Umfrageergebnisse angezeigt, die von einer adaptiven Karte gestartet wurden.</span><span class="sxs-lookup"><span data-stu-id="b2abd-168">This example shows poll results launched from an Adaptive Card.</span></span>

:::image type="content" source="../../assets/images/task-module/poll.png" alt-text="Beispielabfrage in einem Aufgabenmodul." border="false":::

## <a name="best-practices"></a><span data-ttu-id="b2abd-170">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="b2abd-170">Best practices</span></span>

### <a name="usability"></a><span data-ttu-id="b2abd-171">Benutzerfreundlichkeit</span><span class="sxs-lookup"><span data-stu-id="b2abd-171">Usability</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/usability-do.png" alt-text="Beispiel mit einem Aufgabenmodul bewährte Methode." border="false":::

#### <a name="do-use-one-task-module-at-a-time"></a><span data-ttu-id="b2abd-173">Do: Gleichzeitiges verwenden eines Aufgabenmoduls</span><span class="sxs-lookup"><span data-stu-id="b2abd-173">Do: Use one task module at a time</span></span>

<span data-ttu-id="b2abd-174">Das Ziel besteht darin, den Benutzer darauf zu konzentrieren, eine Aufgabe abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="b2abd-174">The goal is to focus the user on completing a task after all!</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/usability-dont.png" alt-text="Beispiel mit einem Aufgabenmodul bewährte Methode." border="false":::

#### <a name="dont-pop-a-dialog-on-top-of-a-task-module"></a><span data-ttu-id="b2abd-176">Nicht: Pop ein Dialogfeld oberhalb eines Aufgabenmoduls</span><span class="sxs-lookup"><span data-stu-id="b2abd-176">Don't: Pop a dialog on top of a task module</span></span>

<span data-ttu-id="b2abd-177">Dadurch entsteht eine unfokussierte, verwirrende Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="b2abd-177">This creates an unfocused, confusing user experience.</span></span>

   :::column-end:::
:::row-end:::

### <a name="responsive"></a><span data-ttu-id="b2abd-178">Reaktionsfähig</span><span class="sxs-lookup"><span data-stu-id="b2abd-178">Responsive</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/responsive-do.png" alt-text="Beispiel mit einem Aufgabenmodul bewährte Methode." border="false":::

#### <a name="do-make-sure-the-content-is-responsive"></a><span data-ttu-id="b2abd-180">Do: sicherstellen, dass der Inhalt reagiert</span><span class="sxs-lookup"><span data-stu-id="b2abd-180">Do: Make sure the content is responsive</span></span>

<span data-ttu-id="b2abd-181">Während Adaptive Karten, die in einem Aufgabenmodul gehostet werden, auf mobilen Geräten gut gerendert werden, sollten Sie, wenn Sie einen IFRAME zum Hosten von App-Inhalten auswählen, sicherstellen, dass die Benutzeroberfläche reagiert und auf allen Geräten gut funktioniert.</span><span class="sxs-lookup"><span data-stu-id="b2abd-181">While Adaptive Cards hosted in a task module render well on mobile devices, if you choose to use an iframe to host app content, make sure the UI is responsive and works well across devices.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/responsive-dont.png" alt-text="Beispiel mit einem Aufgabenmodul bewährte Methode." border="false":::

#### <a name="dont-use-horizontal-scrollbars"></a><span data-ttu-id="b2abd-183">Nicht: horizontale Bildlaufleisten verwenden</span><span class="sxs-lookup"><span data-stu-id="b2abd-183">Don't: Use horizontal scrollbars</span></span>

<span data-ttu-id="b2abd-184">Es ist eine bewährte Methode, Inhalte konzentriert und nicht zu lang zu halten.</span><span class="sxs-lookup"><span data-stu-id="b2abd-184">It's a best practice to keep content focused and not too lengthy.</span></span> <span data-ttu-id="b2abd-185">Wenn ein Bildlauf erforderlich ist, Scrollen Sie vertikal und nicht horizontal.</span><span class="sxs-lookup"><span data-stu-id="b2abd-185">If a scroll is necessary, scroll vertically and not horizontally.</span></span>

   :::column-end:::
:::row-end:::

### <a name="simplicity"></a><span data-ttu-id="b2abd-186">Einfachheit</span><span class="sxs-lookup"><span data-stu-id="b2abd-186">Simplicity</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/simplicity-do.png" alt-text="Beispiel mit einem Aufgabenmodul bewährte Methode." border="false":::

#### <a name="do-keep-it-short"></a><span data-ttu-id="b2abd-188">Do: kurz halten</span><span class="sxs-lookup"><span data-stu-id="b2abd-188">Do: Keep it short</span></span>

<span data-ttu-id="b2abd-189">Sie können ganz einfach einen mehrstufigen Assistenten erstellen, aber das bedeutet nicht unbedingt, dass Sie dies sollten!</span><span class="sxs-lookup"><span data-stu-id="b2abd-189">You can easily create a multi-step wizard, but that doesn't necessarily mean you should!</span></span> <span data-ttu-id="b2abd-190">Ein Aufgabenmodul mit mehreren Bildschirmen kann problematisch sein, da eingehende Nachrichten ablenken und Benutzer zum Beenden verleiten.</span><span class="sxs-lookup"><span data-stu-id="b2abd-190">A multi-screen task module can be problematic because incoming messages are distracting and tempt users to exit.</span></span> <span data-ttu-id="b2abd-191">Wenn Ihre Aufgabe wirklich involviert ist, gehen Sie zu einer vollständigen Webseite anstelle eines Aufgabenmoduls.</span><span class="sxs-lookup"><span data-stu-id="b2abd-191">If your task is really involved, pop out to a full webpage instead of a task module.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/simplicity-dont.png" alt-text="Beispiel mit einem Aufgabenmodul bewährte Methode." border="false":::

#### <a name="dont-do-long-interactions"></a><span data-ttu-id="b2abd-193">Nicht: lange Interaktionen ausführen</span><span class="sxs-lookup"><span data-stu-id="b2abd-193">Don't: Do long interactions</span></span>

<span data-ttu-id="b2abd-194">Versuchen Sie, ihre Interaktionen kurz und auf den neuesten Stand zu bringen.</span><span class="sxs-lookup"><span data-stu-id="b2abd-194">Try to keep your interactions short and to the point.</span></span>

   :::column-end:::
:::row-end:::

### <a name="error-messages"></a><span data-ttu-id="b2abd-195">Fehlermeldungen</span><span class="sxs-lookup"><span data-stu-id="b2abd-195">Error messages</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/error-messages-do.png" alt-text="Beispiel mit einem Aufgabenmodul bewährte Methode." border="false":::

#### <a name="do-use-inline-error-messages"></a><span data-ttu-id="b2abd-197">Do: Verwenden von Inline Fehlermeldungen</span><span class="sxs-lookup"><span data-stu-id="b2abd-197">Do: Use inline error messages</span></span>

<span data-ttu-id="b2abd-198">Anleitungen zur Inline Fehlerbehandlung finden Sie in der Forms-Benutzeroberflächen Vorlage.</span><span class="sxs-lookup"><span data-stu-id="b2abd-198">See the forms UI template for guidelines on inline error handling.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/error-messages-dont.png" alt-text="Beispiel mit einem Aufgabenmodul bewährte Methode." border="false":::

#### <a name="dont-put-error-messages-in-dialogs"></a><span data-ttu-id="b2abd-200">Nicht: Put-Fehlermeldungen in Dialogfeldern</span><span class="sxs-lookup"><span data-stu-id="b2abd-200">Don't: Put error messages in dialogs</span></span>

<span data-ttu-id="b2abd-201">Keine Fehlermeldung in einem Dialogfeld oberhalb eines Aufgabenmoduls Pop.</span><span class="sxs-lookup"><span data-stu-id="b2abd-201">Don't pop an error message in a dialog on top of a task modules.</span></span> <span data-ttu-id="b2abd-202">Dadurch wird eine verwirrende Benutzeroberfläche erstellt.</span><span class="sxs-lookup"><span data-stu-id="b2abd-202">It creates a confusing user experience.</span></span>

   :::column-end:::
:::row-end:::
