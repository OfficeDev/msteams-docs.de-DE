---
title: Entwerfen der Besprechungserweiterung
author: heath-hamilton
description: Erfahren Sie, wie Sie Apps in Teams-Besprechungen entwerfen und das Microsoft Teams UI Kit erhalten.
ms.author: lajanuar
ms.topic: conceptual
ms.openlocfilehash: e4e7bb05fbc9717a4eb8323302d1a10eac4c77dd
ms.sourcegitcommit: f5ee3fa5ef6126d9bf845948d27d9067b3bbb994
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2021
ms.locfileid: "51596252"
---
# <a name="designing-your-microsoft-teams-meeting-extension"></a><span data-ttu-id="f9c26-103">Entwerfen Ihrer Microsoft Teams-Besprechungserweiterung</span><span class="sxs-lookup"><span data-stu-id="f9c26-103">Designing your Microsoft Teams meeting extension</span></span>

<span data-ttu-id="f9c26-104">Sie können Apps erstellen, um Besprechungen produktiver zu gestalten.</span><span class="sxs-lookup"><span data-stu-id="f9c26-104">You can create apps to make meetings more productive.</span></span> <span data-ttu-id="f9c26-105">Bitten Sie z. B. Personen, während eines Anrufs eine Umfrage zu führen, oder senden Sie eine kurze Erinnerung, die den Ablauf der Besprechung nicht unterbricht.</span><span class="sxs-lookup"><span data-stu-id="f9c26-105">For example, ask people to complete a survey during a call or send a quick reminder that doesn’t interrupt the flow of the meeting.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="f9c26-106">Microsoft Teams UI Kit</span><span class="sxs-lookup"><span data-stu-id="f9c26-106">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="f9c26-107">Umfassendere Entwurfsrichtlinien, einschließlich Elemente, die Sie bei Bedarf packen und ändern können, finden Sie im Microsoft Teams UI Kit.</span><span class="sxs-lookup"><span data-stu-id="f9c26-107">You can find more comprehensive design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f9c26-108">Microsoft Teams UI Kit (Figma)</span><span class="sxs-lookup"><span data-stu-id="f9c26-108">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-meeting-extension"></a><span data-ttu-id="f9c26-109">Hinzufügen einer Besprechungserweiterung</span><span class="sxs-lookup"><span data-stu-id="f9c26-109">Add a meeting extension</span></span>

<span data-ttu-id="f9c26-110">Sie können eine Besprechungserweiterung vor und während Besprechungen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f9c26-110">You can add a meeting extension before and during meetings.</span></span> <span data-ttu-id="f9c26-111">Sie können auch eine App für eine bestimmte Besprechung direkt aus dem Teams Store (AppSource) hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f9c26-111">You also can add an app for a specific meeting directly from the Teams store (AppSource).</span></span>

### <a name="add-before-a-meeting"></a><span data-ttu-id="f9c26-112">Hinzufügen vor einer Besprechung</span><span class="sxs-lookup"><span data-stu-id="f9c26-112">Add before a meeting</span></span>

<span data-ttu-id="f9c26-113">Wählen Sie in den Besprechungsdetails **Registerkarte hinzufügen +** aus, um das App-Flyout zu öffnen und apps zu finden, die für Besprechungen optimiert sind.</span><span class="sxs-lookup"><span data-stu-id="f9c26-113">In the meeting details, select **Add a tab +** to open the app flyout and find apps optimized for meetings.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/add-before-meeting.png" alt-text="Beispiel zeigt, wie Sie eine Besprechungserweiterung vor einer Besprechung hinzufügen." border="false":::

### <a name="add-during-a-meeting"></a><span data-ttu-id="f9c26-115">Hinzufügen während einer Besprechung</span><span class="sxs-lookup"><span data-stu-id="f9c26-115">Add during a meeting</span></span>

Wählen Sie in einer Besprechung **weitere App** :::image type="icon" source="../../assets/icons/teams-client-more.png":::  >  **hinzufügen aus,** und wählen Sie die app aus, die Sie möchten.

:::image type="content" source="../../assets/images/apps-in-meetings/add-during-meeting.png" alt-text="Beispiel zeigt, wie Sie während einer Besprechung eine Besprechungserweiterung hinzufügen." border="false":::

## <a name="before-a-meeting"></a><span data-ttu-id="f9c26-118">Vor einer Besprechung</span><span class="sxs-lookup"><span data-stu-id="f9c26-118">Before a meeting</span></span>

<span data-ttu-id="f9c26-119">Vor Ihrer Besprechung können Sie Inhalte auf der Registerkarte hinzufügen. Das folgende Beispiel zeigt eine Entwurfsfrage, die während des Anrufs beantwortet wird.</span><span class="sxs-lookup"><span data-stu-id="f9c26-119">Prior to your meeting, you can add content in the tab. The following example shows a draft survey question that people will answer during the call.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/before-meeting-tab.png" alt-text="Beispiel zeigt, wie Inhalte in den Besprechungsdetails vor einem Anruf app-App." border="false":::

### <a name="anatomy-meeting-tab-before-and-after-meetings"></a><span data-ttu-id="f9c26-121">Anatomie: Registerkarte Besprechung (vor und nach Besprechungen)</span><span class="sxs-lookup"><span data-stu-id="f9c26-121">Anatomy: Meeting tab (before and after meetings)</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/meeting-details-tab-anatomy.png" alt-text="Beispiel zeigt die Strukturanatomie einer Besprechungsregisterkarte vor und nach einer Besprechung." border="false":::

|<span data-ttu-id="f9c26-123">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="f9c26-123">Counter</span></span>|<span data-ttu-id="f9c26-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f9c26-124">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="f9c26-125">1</span><span class="sxs-lookup"><span data-stu-id="f9c26-125">1</span></span>|<span data-ttu-id="f9c26-126">**Registerkartenname:** Navigationsbezeichnung für Ihre Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="f9c26-126">**Tab name**: Navigation label for your tab.</span></span>|
|<span data-ttu-id="f9c26-127">2</span><span class="sxs-lookup"><span data-stu-id="f9c26-127">2</span></span>|<span data-ttu-id="f9c26-128">**Registerkartenüberlauf**: Öffnet Registerkartenaktionen, z. B. Umbenennen und Entfernen.</span><span class="sxs-lookup"><span data-stu-id="f9c26-128">**Tab overflow**: Opens tab actions, such as rename and remove.</span></span>|
|<span data-ttu-id="f9c26-129">3</span><span class="sxs-lookup"><span data-stu-id="f9c26-129">3</span></span>|<span data-ttu-id="f9c26-130">**iframe**: Zeigt Ihre App-Inhalte an.</span><span class="sxs-lookup"><span data-stu-id="f9c26-130">**iframe**: Displays your app content.</span></span>|

### <a name="designing-with-ui-templates"></a><span data-ttu-id="f9c26-131">Entwerfen mit Benutzeroberflächenvorlagen</span><span class="sxs-lookup"><span data-stu-id="f9c26-131">Designing with UI templates</span></span>

<span data-ttu-id="f9c26-132">Verwenden Sie eine der folgenden Teams-UI-Vorlagen, um Ihre Besprechungsregisterkarte zu entwerfen:</span><span class="sxs-lookup"><span data-stu-id="f9c26-132">Use one of the following Teams UI templates to help design your meeting tab:</span></span>

* <span data-ttu-id="f9c26-133">[Liste](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem scannierbaren Format anzeigen und Benutzern das Ausführen von Aktionen für eine gesamte Liste oder einzelne Elemente ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="f9c26-133">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="f9c26-134">[Task board:](../../concepts/design/design-teams-app-ui-templates.md#task-board)Ein Task Board, manchmal auch als Kanbanboard oder Schwimmstreifen bezeichnet, ist eine Sammlung von Karten, die häufig zum Nachverfolgen des Status von Arbeitselementen oder Tickets verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f9c26-134">[Task board](../../concepts/design/design-teams-app-ui-templates.md#task-board): A task board, sometimes called a kanban board or swim lanes, is a collection of cards often used to track the status of work items or tickets.</span></span>
* <span data-ttu-id="f9c26-135">[Dashboard:](../../concepts/design/design-teams-app-ui-templates.md#dashboard)Ein Dashboard ist ein Canvas mit mehreren Karten, die eine Übersicht über Daten oder Inhalte bieten.</span><span class="sxs-lookup"><span data-stu-id="f9c26-135">[Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): A dashboard is a canvas containing multiple cards that provide an overview of data or content.</span></span>
* <span data-ttu-id="f9c26-136">[Formular](../../concepts/design/design-teams-app-ui-templates.md#form): Formulare sind für die strukturierte Erfassung, Validierung und Übermittlung von Benutzereingaben.</span><span class="sxs-lookup"><span data-stu-id="f9c26-136">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="f9c26-137">[Leerer](../../concepts/design/design-teams-app-ui-templates.md#empty-state)Zustand: Die Vorlage für den leeren Zustand kann für viele Szenarien verwendet werden, z. B. für die Anmeldung, die Erstlauferfahrung, Fehlermeldungen und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="f9c26-137">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>
* <span data-ttu-id="f9c26-138">[Linkes](../../concepts/design/design-teams-app-ui-templates.md#left-nav)Navigationsmenü: Die linke Navigationsvorlage kann hilfreich sein, wenn Ihre Registerkarte eine Navigation erfordert.</span><span class="sxs-lookup"><span data-stu-id="f9c26-138">[Left nav](../../concepts/design/design-teams-app-ui-templates.md#left-nav): The left nav template can help if your tab requires some navigation.</span></span> <span data-ttu-id="f9c26-139">Im Allgemeinen sollten Sie die Registerkartennavigation auf ein Minimum beschränken.</span><span class="sxs-lookup"><span data-stu-id="f9c26-139">In general, you should keep tab navigation to a minimum.</span></span>

## <a name="use-an-in-meeting-tab"></a><span data-ttu-id="f9c26-140">Verwenden einer Registerkarte in Besprechungen</span><span class="sxs-lookup"><span data-stu-id="f9c26-140">Use an in-meeting tab</span></span>

<span data-ttu-id="f9c26-141">Die Registerkarte "In-Meeting" ist ein Zeichenbereich für die Erweiterung der Zusammenarbeit in Besprechungen.</span><span class="sxs-lookup"><span data-stu-id="f9c26-141">The in-meeting tab is a canvas for augmenting collaboration during meetings.</span></span> <span data-ttu-id="f9c26-142">Teilnehmer können app-Inhalte in einem dedizierten Bereich außerhalb der Besprechungsphase über freigegebene oder rollenbasierte Ansichten anzeigen und mit ihnen interagieren.</span><span class="sxs-lookup"><span data-stu-id="f9c26-142">Attendees can see and interact with app content in a dedicated space outside the meeting stage through shared or role-based views.</span></span>

### <a name="use-cases"></a><span data-ttu-id="f9c26-143">Anwendungsfälle</span><span class="sxs-lookup"><span data-stu-id="f9c26-143">Use cases</span></span>

<span data-ttu-id="f9c26-144">Personen können die Registerkarte "In-Meeting" verwenden, um:</span><span class="sxs-lookup"><span data-stu-id="f9c26-144">People might use the in-meeting tab to:</span></span>

* <span data-ttu-id="f9c26-145">Bereitstellen detaillierten Feedbacks (z. B. Bewerten eines Stellenkandidaten)</span><span class="sxs-lookup"><span data-stu-id="f9c26-145">Provide detailed feedback (for example, evaluate a job candidate)</span></span>
* <span data-ttu-id="f9c26-146">Schnelles Erstellen einer Umfrage, umfrage oder eines Aufgabenelements für die Besprechungsteilnehmer</span><span class="sxs-lookup"><span data-stu-id="f9c26-146">Quickly create a poll, survey, or task item for the meeting participants</span></span>
* <span data-ttu-id="f9c26-147">Anzeigen von für die Besprechung relevanten Notizen (z. B. Informationen zu einem Vertriebsleiter)</span><span class="sxs-lookup"><span data-stu-id="f9c26-147">Display notes relevant to the meeting (for example, information about a sales lead)</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-tab.png" alt-text="Ein Beispiel zeigt, wie Sie Umfrageinhalte auf einer Registerkarte in besprechungen präsentieren können." border="false":::

### <a name="anatomy-in-meeting-tab"></a><span data-ttu-id="f9c26-149">Anatomie: Registerkarte "In-Meeting"</span><span class="sxs-lookup"><span data-stu-id="f9c26-149">Anatomy: In-meeting tab</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-anatomy.png" alt-text="Beispiel zeigt die Strukturanatomie einer Registerkarte in Besprechungen." border="false":::

|<span data-ttu-id="f9c26-151">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="f9c26-151">Counter</span></span>|<span data-ttu-id="f9c26-152">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f9c26-152">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="f9c26-153">1</span><span class="sxs-lookup"><span data-stu-id="f9c26-153">1</span></span>|<span data-ttu-id="f9c26-154">**App-Symbol (ausgewählt):** 16 Pixel transparentes App-Logo.</span><span class="sxs-lookup"><span data-stu-id="f9c26-154">**App icon (selected)**: 16-pixel transparent app logo.</span></span>|
|<span data-ttu-id="f9c26-155">2</span><span class="sxs-lookup"><span data-stu-id="f9c26-155">2</span></span>|<span data-ttu-id="f9c26-156">**App-Name**</span><span class="sxs-lookup"><span data-stu-id="f9c26-156">**App name**</span></span>|
|<span data-ttu-id="f9c26-157">3</span><span class="sxs-lookup"><span data-stu-id="f9c26-157">3</span></span>|<span data-ttu-id="f9c26-158">**Header**: Enthält Ihren App-Namen.</span><span class="sxs-lookup"><span data-stu-id="f9c26-158">**Header**: Includes your app name.</span></span>|
|<span data-ttu-id="f9c26-159">4 </span><span class="sxs-lookup"><span data-stu-id="f9c26-159">4</span></span>|<span data-ttu-id="f9c26-160">**Schaltfläche Schließen**: Schließt die Registerkarte. Verwenden Sie immer das schließende Symbol oben rechts anstelle einer Aktion in der Fußzeile.</span><span class="sxs-lookup"><span data-stu-id="f9c26-160">**Close button**: Dismisses the tab. Always use the upper-right close icon instead of an action in the footer.</span></span>|
|<span data-ttu-id="f9c26-161">5 </span><span class="sxs-lookup"><span data-stu-id="f9c26-161">5</span></span>|<span data-ttu-id="f9c26-162">**Benachrichtigungsleiste**: Fehlerwarnungen werden direkt unterhalb der Kopfzeile angezeigt, und der iframe-Inhalt wird um 20 Pixel nach unten geschoben.</span><span class="sxs-lookup"><span data-stu-id="f9c26-162">**Notification bar**: Error alerts display directly below the header and push the iframe content down by 20 pixels.</span></span>|
|<span data-ttu-id="f9c26-163">6 </span><span class="sxs-lookup"><span data-stu-id="f9c26-163">6</span></span>|<span data-ttu-id="f9c26-164">**iframe**: Zeigt Ihre App-Inhalte an.</span><span class="sxs-lookup"><span data-stu-id="f9c26-164">**iframe**: Displays your app content.</span></span>|

### <a name="spacing"></a><span data-ttu-id="f9c26-165">Abstand</span><span class="sxs-lookup"><span data-stu-id="f9c26-165">Spacing</span></span>

<span data-ttu-id="f9c26-166">Optimieren Sie ihre Registerkarte in Besprechungen so, dass sie in den 280 Pixel breiten iframe-Bereich passt.</span><span class="sxs-lookup"><span data-stu-id="f9c26-166">Optimize your in-meeting tab to fit edge-to-edge within the 280 pixel-wide iframe area.</span></span> <span data-ttu-id="f9c26-167">Es gibt 20 Pixel Abstand auf der linken und rechten Seite des iframes und zwischen der Registerkartenkopfzeile.</span><span class="sxs-lookup"><span data-stu-id="f9c26-167">There are 20 pixels of padding on the left and right sides of the iframe and between the tab header.</span></span> <span data-ttu-id="f9c26-168">Der iframe wird bis zum unteren Rand der Registerkarte vollständig ausblutet.</span><span class="sxs-lookup"><span data-stu-id="f9c26-168">The iframe is full bleed to the bottom of the tab.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-spacing.png" alt-text="Beispiel zeigt Die Größe der Registerkartenabstände in Besprechungen." border="false":::

### <a name="scrolling"></a><span data-ttu-id="f9c26-170">Bildlauf</span><span class="sxs-lookup"><span data-stu-id="f9c26-170">Scrolling</span></span>

<span data-ttu-id="f9c26-171">Der Iframeinhalt sollte vertikal gescrollt werden.</span><span class="sxs-lookup"><span data-stu-id="f9c26-171">Iframe contents should scroll vertically.</span></span> <span data-ttu-id="f9c26-172">Sie können nur den Inhalt sehen, zu dem Sie einen Bildlauf durchgeführt haben (nichts oben oder unten).</span><span class="sxs-lookup"><span data-stu-id="f9c26-172">You can only see the content you've scrolled to (nothing above or below).</span></span> <span data-ttu-id="f9c26-173">Die Bildlaufleiste ist Teil des iframe-Inhalts.</span><span class="sxs-lookup"><span data-stu-id="f9c26-173">The scrollbar is part of the iframe content.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-scrolling.png" alt-text="Beispiel zeigt, wie die Registerkarte in Besprechungen scrollt." border="false":::

### <a name="navigation"></a><span data-ttu-id="f9c26-175">Navigation</span><span class="sxs-lookup"><span data-stu-id="f9c26-175">Navigation</span></span>

<span data-ttu-id="f9c26-176">Für Szenarien mit Navigationsebenen oder hohen Inhalten wird empfohlen, benutzern die Navigation zu einer sekundären Ebene zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="f9c26-176">For scenarios with navigation layers or heavy content, we recommend allowing users to navigate to a secondary layer.</span></span> <span data-ttu-id="f9c26-177">Benutzer müssen wieder zur vorherigen Ebene wechseln können.</span><span class="sxs-lookup"><span data-stu-id="f9c26-177">Users must be able to go back to the previous layer.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav.png" alt-text="Beispiel zeigt die Navigation in Besprechungen." border="false":::

## <a name="use-an-in-meeting-dialog"></a><span data-ttu-id="f9c26-179">Verwenden eines Besprechungsdialogfelds</span><span class="sxs-lookup"><span data-stu-id="f9c26-179">Use an in-meeting dialog</span></span>

<span data-ttu-id="f9c26-180">Dialoge in Besprechungen werden in der Besprechungsphase von Teams angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f9c26-180">In-meeting dialogs display on the Teams meeting stage.</span></span> <span data-ttu-id="f9c26-181">Sie erfordern die Aufmerksamkeit, Bestätigung oder Interaktion eines Benutzers, sind jedoch subtil und unterbrechen die Besprechung nicht.</span><span class="sxs-lookup"><span data-stu-id="f9c26-181">They require a user's attention, confirmation, or interaction but are subtle and don't interrupt the meeting.</span></span> <span data-ttu-id="f9c26-182">Sie sollten diese sparsam und für Szenarien verwenden, die leicht und aufgabenorientiert sind.</span><span class="sxs-lookup"><span data-stu-id="f9c26-182">You should use these sparingly and for scenarios that are light and task oriented.</span></span>

### <a name="use-cases"></a><span data-ttu-id="f9c26-183">Anwendungsfälle</span><span class="sxs-lookup"><span data-stu-id="f9c26-183">Use cases</span></span>

<span data-ttu-id="f9c26-184">Dialoge in Besprechungen werden von einem Benutzer (z. B. dem Besprechungsorganisator) ausgelöst, der die Teilnehmer möglicherweise wie folgt verwenden möchte:</span><span class="sxs-lookup"><span data-stu-id="f9c26-184">In-meeting dialogs are triggered by a user (such as the meeting organizer) who might want participants to:</span></span>

* <span data-ttu-id="f9c26-185">Kurzes Feedback</span><span class="sxs-lookup"><span data-stu-id="f9c26-185">Provide brief feedback</span></span>
* <span data-ttu-id="f9c26-186">Eine kurze Umfrage oder Umfrage</span><span class="sxs-lookup"><span data-stu-id="f9c26-186">Take a short survey or poll</span></span>
* <span data-ttu-id="f9c26-187">Übermitteln von Genehmigungen</span><span class="sxs-lookup"><span data-stu-id="f9c26-187">Submit approvals</span></span>
* <span data-ttu-id="f9c26-188">Erinnerungen erhalten</span><span class="sxs-lookup"><span data-stu-id="f9c26-188">Get reminders</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-dialog.png" alt-text="Beispiel zeigt, wie Sie ein Besprechungsdialogfeld verwenden können." border="false":::

### <a name="anatomy-in-meeting-dialog"></a><span data-ttu-id="f9c26-190">Anatomie: Dialogfeld "In-Meeting"</span><span class="sxs-lookup"><span data-stu-id="f9c26-190">Anatomy: In-meeting dialog</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-anatomy.png" alt-text="Beispiel zeigt die Strukturanatomie eines Besprechungsdialogfelds." border="false":::

|<span data-ttu-id="f9c26-192">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="f9c26-192">Counter</span></span>|<span data-ttu-id="f9c26-193">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f9c26-193">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="f9c26-194">1</span><span class="sxs-lookup"><span data-stu-id="f9c26-194">1</span></span>|<span data-ttu-id="f9c26-195">**Header**: Enthält App-Symbol, Name, Aktionszeichenfolge und Schließen-Symbol.</span><span class="sxs-lookup"><span data-stu-id="f9c26-195">**Header**: Includes app icon, name, action string, and close icon.</span></span>|
|<span data-ttu-id="f9c26-196">2</span><span class="sxs-lookup"><span data-stu-id="f9c26-196">2</span></span>|<span data-ttu-id="f9c26-197">**iframe**: Zeigt Ihre App-Inhalte an.</span><span class="sxs-lookup"><span data-stu-id="f9c26-197">**iframe**: Displays your app content.</span></span>|

### <a name="anatomy-in-meeting-dialog-header"></a><span data-ttu-id="f9c26-198">Anatomie: In-Meeting-Dialogkopfzeile</span><span class="sxs-lookup"><span data-stu-id="f9c26-198">Anatomy: In-meeting dialog header</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-header-anatomy.png" alt-text="Beispiel zeigt die Strukturanatomie eines Besprechungsdialogkopfs." border="false":::

<span data-ttu-id="f9c26-200">Es gibt zwei Kopfzeilenvarianten.</span><span class="sxs-lookup"><span data-stu-id="f9c26-200">There are two header variants.</span></span> <span data-ttu-id="f9c26-201">Verwenden Sie nach Möglichkeit die Variante mit dem Avatar, um zu verstärken, dass das Dialogfeld von einer Person kommt.</span><span class="sxs-lookup"><span data-stu-id="f9c26-201">When possible, use the variant with the avatar to reinforce that the dialog is coming from a person.</span></span>

|<span data-ttu-id="f9c26-202">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="f9c26-202">Counter</span></span>|<span data-ttu-id="f9c26-203">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f9c26-203">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="f9c26-204">1</span><span class="sxs-lookup"><span data-stu-id="f9c26-204">1</span></span>|<span data-ttu-id="f9c26-205">**Avatar**: Person, die das Dialogfeld in der Besprechung initiiert.</span><span class="sxs-lookup"><span data-stu-id="f9c26-205">**Avatar**: Person who initiates the in-meeting dialog.</span></span>|
|<span data-ttu-id="f9c26-206">2</span><span class="sxs-lookup"><span data-stu-id="f9c26-206">2</span></span>|<span data-ttu-id="f9c26-207">**App-Symbol**</span><span class="sxs-lookup"><span data-stu-id="f9c26-207">**App icon**</span></span>|
|<span data-ttu-id="f9c26-208">3</span><span class="sxs-lookup"><span data-stu-id="f9c26-208">3</span></span>|<span data-ttu-id="f9c26-209">**App-Name**</span><span class="sxs-lookup"><span data-stu-id="f9c26-209">**App name**</span></span>|
|<span data-ttu-id="f9c26-210">4 </span><span class="sxs-lookup"><span data-stu-id="f9c26-210">4</span></span>|<span data-ttu-id="f9c26-211">**Schaltfläche Schließen**: Schließt das Dialogfeld.</span><span class="sxs-lookup"><span data-stu-id="f9c26-211">**Close button**: Dismisses the dialog.</span></span>|
|<span data-ttu-id="f9c26-212">5 </span><span class="sxs-lookup"><span data-stu-id="f9c26-212">5</span></span>|<span data-ttu-id="f9c26-213">**Aktionszeichenfolge**: In der Regel wird beschrieben, wer das Dialogfeld initiiert hat.</span><span class="sxs-lookup"><span data-stu-id="f9c26-213">**Action string**: Typically describes who initiated the dialog.</span></span>|

### <a name="responsive-behavior"></a><span data-ttu-id="f9c26-214">Dynamisches Verhalten</span><span class="sxs-lookup"><span data-stu-id="f9c26-214">Responsive behavior</span></span>

<span data-ttu-id="f9c26-215">Besprechungsdialogfelder können in der Größe variieren, um unterschiedliche Szenarien zu berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="f9c26-215">In-meeting dialogs can vary in size to account for different scenarios.</span></span> <span data-ttu-id="f9c26-216">Achten Sie darauf, abstands- und komponentengrößen zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="f9c26-216">Make sure to maintain padding and component sizes.</span></span>

* <span data-ttu-id="f9c26-217">**Width**: Sie können die Breite des iframe des Dialogfelds an einer beliebigen Stelle innerhalb des unterstützten Größenbereichs angeben.</span><span class="sxs-lookup"><span data-stu-id="f9c26-217">**Width**: You can specify the width of the dialog's iframe anywhere within the supported size range.</span></span>
* <span data-ttu-id="f9c26-218">**Height**: Sie können die Höhe des iframe des Dialogfelds an einer beliebigen Stelle innerhalb des unterstützten Größenbereichs angeben.</span><span class="sxs-lookup"><span data-stu-id="f9c26-218">**Height**: You can specify the height of the dialog's iframe anywhere within the supported size range.</span></span> <span data-ttu-id="f9c26-219">Sie können Benutzern auch erlauben, vertikal zu scrollen, wenn Ihre App-Inhalte die maximale Höhe überschreitet.</span><span class="sxs-lookup"><span data-stu-id="f9c26-219">You also can allow users to scroll vertically if your app content exceeds the maximum height.</span></span>

<span data-ttu-id="f9c26-220">Geben Sie zum Implementieren die Breite und Höhe mithilfe des Schlüssels [`externalResourceUrl`](~/apps-in-teams-meetings/create-apps-for-teams-meetings.md#notificationsignal-api) an.</span><span class="sxs-lookup"><span data-stu-id="f9c26-220">To implement, specify the width and height using the [`externalResourceUrl`](~/apps-in-teams-meetings/create-apps-for-teams-meetings.md#notificationsignal-api) key.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-responsive.png" alt-text="Beispiel zeigt das Dialogfeld in der Besprechung. Breite: Min--280 Pixel (248 Pixel iframe). Max.-460 Pixel (428 Pixel iframe). Höhe: 300 Pixel (iframe)." border="false":::

## <a name="after-a-meeting"></a><span data-ttu-id="f9c26-222">Nach einer Besprechung</span><span class="sxs-lookup"><span data-stu-id="f9c26-222">After a meeting</span></span>

<span data-ttu-id="f9c26-223">Sie können nach dem Ende zu einer Besprechung wechseln und App-Inhalte anzeigen.</span><span class="sxs-lookup"><span data-stu-id="f9c26-223">You can go back to a meeting after it ends and view app content.</span></span> <span data-ttu-id="f9c26-224">In diesem Beispiel kann der Besprechungsorganisator die Umfrageergebnisse auf der Registerkarte **Contoso** anzeigen. (Hinweis: Aus Entwurfs sicht gibt es keinen Unterschied zwischen der Registerkartenerfahrung vor und nach der Besprechung.)</span><span class="sxs-lookup"><span data-stu-id="f9c26-224">In this example, the meeting organizer can look at poll results in the **Contoso** tab. (Note: From a design standpoint, there's no difference between a the pre- and post-meeting tab experience.)</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/post-meeting-experience.png" alt-text="Die Beispielillustration zeigt eine Registerkarte nach der Besprechung." border="false":::

## <a name="best-practices"></a><span data-ttu-id="f9c26-226">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="f9c26-226">Best practices</span></span>

### <a name="interactions"></a><span data-ttu-id="f9c26-227">Interaktionen</span><span class="sxs-lookup"><span data-stu-id="f9c26-227">Interactions</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-do.png" alt-text="Beispiel zum Einschränken der Anzahl von Interaktionen." border="false":::

#### <a name="do-limit-the-number-of-interactions"></a><span data-ttu-id="f9c26-229">Do: Beschränken der Anzahl von Interaktionen</span><span class="sxs-lookup"><span data-stu-id="f9c26-229">Do: Limit the number of interactions</span></span>

<span data-ttu-id="f9c26-230">Entfernen Sie in Besprechungsdialogfeldern unnötige Inhalte, die Benutzern nicht helfen, schnell etwas zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="f9c26-230">For in-meeting dialogs, remove unnecessary content that doesn't help users accomplish something quickly.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-dont.png" alt-text="Beispiel, in dem gezeigt wird, wie sie keine unnötigen Elemente einführen." border="false":::

#### <a name="dont-introduce-unnecessary-elements"></a><span data-ttu-id="f9c26-232">Don't: Einführung unnötiger Elemente</span><span class="sxs-lookup"><span data-stu-id="f9c26-232">Don't: Introduce unnecessary elements</span></span>

<span data-ttu-id="f9c26-233">Ein einzelnes Besprechungsdialogfeld mit mehreren Interaktionen kann vom Anruf ablenken.</span><span class="sxs-lookup"><span data-stu-id="f9c26-233">A single in-meeting dialog with multiple interactions can distract from the call.</span></span>

   :::column-end:::
:::row-end:::

### <a name="layout"></a><span data-ttu-id="f9c26-234">Layout</span><span class="sxs-lookup"><span data-stu-id="f9c26-234">Layout</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-do.png" alt-text="Beispiel für die Verwendung eines Einspaltendialogfelds." border="false":::

#### <a name="do-use-a-single-column-dialog-layout"></a><span data-ttu-id="f9c26-236">Do: Verwenden eines einspaltig geöffneten Dialogfeldlayouts</span><span class="sxs-lookup"><span data-stu-id="f9c26-236">Do: Use a single-column dialog layout</span></span>

<span data-ttu-id="f9c26-237">Da die Dialoge im Mittelpunkt der Besprechungsphase stehen, sollte der Aufgabenabschluss schnell und einfach sein, um Frust der Benutzer zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="f9c26-237">Since the dialogs are at the center of the meeting stage, task completion should be fast and simple to avoid user frustration.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-dont.png" alt-text="Beispiel: Sie sollten den Raum einer Besprechungserweiterung nicht überladen." border="false":::

#### <a name="dont-clutter-the-space"></a><span data-ttu-id="f9c26-239">Don't: Clutter the space</span><span class="sxs-lookup"><span data-stu-id="f9c26-239">Don't: Clutter the space</span></span>

<span data-ttu-id="f9c26-240">Dichte oder überstrukturierte Inhalte können ablenkend und überwältigend sein, insbesondere während einer Besprechung.</span><span class="sxs-lookup"><span data-stu-id="f9c26-240">Dense or overly structured content can be distracting and overwhelming, especially during a meeting.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-do.png" alt-text="Beispiel für ein Einspaltenregisterkartenlayout." border="false":::

#### <a name="do-use-a-single-column-tab-layout"></a><span data-ttu-id="f9c26-242">Do: Verwenden eines einspaltig geöffneten Registerkartenlayouts</span><span class="sxs-lookup"><span data-stu-id="f9c26-242">Do: Use a single-column tab layout</span></span>

<span data-ttu-id="f9c26-243">Aufgrund des schmalen Charakters der Registerkarte in der Besprechung wird dringend empfohlen, den Inhalt in einer einzelnen Spalte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="f9c26-243">Given the in-meeting tab's narrow nature, we strongly recommend displaying the contents in a single column.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-dont.png" alt-text="Beispiel für eine Registerkarte mit mehreren Spalten." border="false":::

#### <a name="dont-use-multiple-columns"></a><span data-ttu-id="f9c26-245">Don't: Verwenden mehrerer Spalten</span><span class="sxs-lookup"><span data-stu-id="f9c26-245">Don't: Use multiple columns</span></span>

<span data-ttu-id="f9c26-246">Aufgrund des begrenzten Speicherplatzes der Registerkarte "Besprechung" werden Layouts mit mehr als einer Spalte nicht empfohlen.</span><span class="sxs-lookup"><span data-stu-id="f9c26-246">Due to the limited space of the in-meeting tab, layouts with more than one column aren’t recommended.</span></span>

   :::column-end:::
:::row-end:::

### <a name="controls"></a><span data-ttu-id="f9c26-247">Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="f9c26-247">Controls</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-do.png" alt-text="Beispiel, in dem gezeigt wird, wie primäre Steuerelemente rechts ausgerichtet werden." border="false":::

#### <a name="do-right-align-the-primary-action"></a><span data-ttu-id="f9c26-249">Do: Rechte Ausrichtung der primären Aktion</span><span class="sxs-lookup"><span data-stu-id="f9c26-249">Do: Right align the primary action</span></span>

<span data-ttu-id="f9c26-250">Es wird empfohlen, die visuell schwerste Aktion am rechten Ort zu positionieren.</span><span class="sxs-lookup"><span data-stu-id="f9c26-250">We recommend positioning the most visually heavy action to the right-most location.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-dont.png" alt-text="Beispiel, in dem gezeigt wird, wie Sie primäre Steuerelemente nicht ausrichten sollten." border="false":::

#### <a name="dont-left-or-center-align-actions"></a><span data-ttu-id="f9c26-252">Don't: Aktionen links oder zentriert ausrichten</span><span class="sxs-lookup"><span data-stu-id="f9c26-252">Don't: Left or center align actions</span></span>

<span data-ttu-id="f9c26-253">Dies weicht vom standardmäßigen Teams-Muster für die Steuerelementplatzierung in einem Dialogfeld ab und kann mit einem Dialogfeld hinter dem oberen in Konflikt stehen.</span><span class="sxs-lookup"><span data-stu-id="f9c26-253">This deviates from the standard Teams pattern for control placement in a dialog and may conflict with a dialog behind the top one.</span></span>

   :::column-end:::
:::row-end:::

### <a name="scroll"></a><span data-ttu-id="f9c26-254">Bildlauf</span><span class="sxs-lookup"><span data-stu-id="f9c26-254">Scroll</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-do.png" alt-text="Beispiel für vertikalen Bildlauf auf einer Registerkarte in Besprechungen." border="false":::

#### <a name="do-scroll-vertically"></a><span data-ttu-id="f9c26-256">Do: Vertikal scrollen</span><span class="sxs-lookup"><span data-stu-id="f9c26-256">Do: Scroll vertically</span></span>

<span data-ttu-id="f9c26-257">Benutzer erwarten vertikalen Bildlauf in Teams (und an anderer Stelle).</span><span class="sxs-lookup"><span data-stu-id="f9c26-257">Users expect vertical scrolling in Teams (and elsewhere).</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-dont.png" alt-text="Beispiel für einen horizontalen Bildlauf auf einer Registerkarte in Besprechungen." border="false":::

#### <a name="dont-scroll-horizontally"></a><span data-ttu-id="f9c26-259">Don't: Horizontal scrollen</span><span class="sxs-lookup"><span data-stu-id="f9c26-259">Don't: Scroll horizontally</span></span>

<span data-ttu-id="f9c26-260">Horizontaler Bildlauf ist in Teams kein erwartetes Verhalten.</span><span class="sxs-lookup"><span data-stu-id="f9c26-260">Horizontal scrolling isn’t an expected behavior in Teams.</span></span> <span data-ttu-id="f9c26-261">Andere Canvases in der Besprechungsumgebung scrollen vertikal.</span><span class="sxs-lookup"><span data-stu-id="f9c26-261">Other canvases in the meeting environment scroll vertically.</span></span>

   :::column-end:::
:::row-end:::

### <a name="workflows"></a><span data-ttu-id="f9c26-262">Workflows</span><span class="sxs-lookup"><span data-stu-id="f9c26-262">Workflows</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-workflow-do.png" alt-text="Beispiel für ein komplexes Szenario auf einer Registerkarte in Besprechungen." border="false":::

#### <a name="do-surface-complex-scenarios-in-the-in-meeting-tab"></a><span data-ttu-id="f9c26-264">Do: Komplexe Szenarien auf der Registerkarte Besprechungsoberfläche</span><span class="sxs-lookup"><span data-stu-id="f9c26-264">Do: Surface complex scenarios in the in-meeting tab</span></span>

<span data-ttu-id="f9c26-265">Wenn Ihre App mehrere Aufgaben umfasst, wird dringend empfohlen, eine Registerkarte in Besprechungen mit einem Layout mit einer einzelnen Spalte zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="f9c26-265">If your app includes multiple tasks, we strongly recommend using an in-meeting tab with a single-column layout.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-workflow-dont.png" alt-text="Beispiel für komplexe Szenarien in einem Besprechungsdialogfeld." border="false":::

#### <a name="dont-make-in-meeting-dialogs-complex"></a><span data-ttu-id="f9c26-267">Don't: In-Meeting-Dialoge komplex machen</span><span class="sxs-lookup"><span data-stu-id="f9c26-267">Don't: Make in-meeting dialogs complex</span></span>

<span data-ttu-id="f9c26-268">Besprechungsdialogfelder sind für kurze Interaktionen vorgesehen.</span><span class="sxs-lookup"><span data-stu-id="f9c26-268">In-meeting dialogs are intended for brief interactions.</span></span>

   :::column-end:::
:::row-end:::

### <a name="theming"></a><span data-ttu-id="f9c26-269">Designs</span><span class="sxs-lookup"><span data-stu-id="f9c26-269">Theming</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-do.png" alt-text="Beispiel für eine Besprechungserweiterung mit dem dunklen Design." border="false":::

#### <a name="do-use-teams-color-tokens"></a><span data-ttu-id="f9c26-271">Do: Verwenden von Teams-Farbtoken</span><span class="sxs-lookup"><span data-stu-id="f9c26-271">Do: Use Teams color tokens</span></span>

<span data-ttu-id="f9c26-272">Teams-Besprechungen sind für den dunklen Modus optimiert, um visuelles und kognitives Rauschen zu reduzieren, damit benutzer sich auf die Diskussion und freigegebene Inhalte konzentrieren können.</span><span class="sxs-lookup"><span data-stu-id="f9c26-272">Teams meetings are optimized for dark mode to help reduce visual and cognitive noise so users can focus on the discussion and shared content.</span></span> <span data-ttu-id="f9c26-273">Erfahren Sie mehr <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">über die Verwendung von Farbtoken (Fluent UI).</a></span><span class="sxs-lookup"><span data-stu-id="f9c26-273">Learn about using <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">color tokens (Fluent UI)</a>.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-dont.png" alt-text="Beispiel für eine Besprechungserweiterung mit einem (hellen) Standarddesign." border="false":::

#### <a name="dont-hard-code-hex-values"></a><span data-ttu-id="f9c26-275">Don't: Hexwerte für Hartcode</span><span class="sxs-lookup"><span data-stu-id="f9c26-275">Don't: Hard code hex values</span></span>

<span data-ttu-id="f9c26-276">Wenn Sie keine Teams-Farbtoken verwenden, sind Ihre Designs weniger skalierbar und brauchen mehr Zeit für die Verwaltung.</span><span class="sxs-lookup"><span data-stu-id="f9c26-276">If you don’t use Teams color tokens, your designs will be less scalable and take more time to manage.</span></span>

   :::column-end:::
:::row-end:::

### <a name="navigation"></a><span data-ttu-id="f9c26-277">Navigation</span><span class="sxs-lookup"><span data-stu-id="f9c26-277">Navigation</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-do.png" alt-text="Beispiel für eine Besprechungserweiterung mit einer Schaltfläche &quot;Zurück&quot;." border="false":::

#### <a name="do-have-a-back-button"></a><span data-ttu-id="f9c26-279">Do: Have a back button</span><span class="sxs-lookup"><span data-stu-id="f9c26-279">Do: Have a back button</span></span>

<span data-ttu-id="f9c26-280">Wenn sie mehr als eine Navigationsebene auf einer Registerkarte in Besprechungen haben, müssen Benutzer wieder zu ihren vorherigen Ansichten wechseln können.</span><span class="sxs-lookup"><span data-stu-id="f9c26-280">If you have more than one layer of navigation in an in-meeting tab, users must be able to go back to their previous views.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-dont.png" alt-text="Beispiel für eine Besprechungserweiterung mit zwei Schaltflächen zum Schließen." border="false":::

#### <a name="dont-include-another-dismiss-button"></a><span data-ttu-id="f9c26-282">Don't: Include another dismiss button</span><span class="sxs-lookup"><span data-stu-id="f9c26-282">Don't: Include another dismiss button</span></span>

<span data-ttu-id="f9c26-283">Das Bereitstellen einer Option zum Schließen von Registerkarteninhalten in Besprechungen kann Probleme verursachen, da bereits eine Schaltfläche in der Kopfzeile vorhanden ist, um die Registerkarte in der Besprechung selbst zu schließen.</span><span class="sxs-lookup"><span data-stu-id="f9c26-283">Providing an option to close in-meeting tab content may cause issues since there’s already a button in the header to dismiss the in-meeting tab itself.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-caution.png" alt-text="Beispiel für modale (oder Aufgabenmodule) innerhalb einer Registerkarte in Besprechungen." border="false":::

#### <a name="caution-avoid-modals-within-the-in-meeting-tab"></a><span data-ttu-id="f9c26-285">Vorsicht: Vermeiden von Modalen auf der Registerkarte "Besprechung"</span><span class="sxs-lookup"><span data-stu-id="f9c26-285">Caution: Avoid modals within the in-meeting tab</span></span>

<span data-ttu-id="f9c26-286">Modale (auch als Aufgabenmodule bezeichnet) auf der bereits schmalen Registerkarte in Besprechungen können den Inhalt umschließen und verhüllen.</span><span class="sxs-lookup"><span data-stu-id="f9c26-286">Modals (also known as task modules) in the already narrow in-meeting tab might wrap and obscure the content.</span></span>

   :::column-end:::
:::row-end:::

## <a name="validate-your-design"></a><span data-ttu-id="f9c26-287">Überprüfen Des Entwurfs</span><span class="sxs-lookup"><span data-stu-id="f9c26-287">Validate your design</span></span>

<span data-ttu-id="f9c26-288">Wenn Sie planen, Ihre App in AppSource zu veröffentlichen, sollten Sie die Entwurfsprobleme verstehen, die häufig dazu führen, dass Apps während der Übermittlung fehlschlagen.</span><span class="sxs-lookup"><span data-stu-id="f9c26-288">If you plan to publish your app to AppSource, you should understand the design issues that commonly cause apps to fail during submission.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f9c26-289">Überprüfen der Richtlinien für die Entwurfsüberprüfung</span><span class="sxs-lookup"><span data-stu-id="f9c26-289">Check design validation guidelines</span></span>](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines--most-failed-test-cases)
