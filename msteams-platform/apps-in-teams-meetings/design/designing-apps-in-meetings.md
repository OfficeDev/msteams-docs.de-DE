---
title: Entwerfen der Besprechungserweiterung
author: heath-hamilton
description: Erfahren Sie, wie Sie Apps in Teams entwerfen und das Microsoft Teams UI Kit erhalten.
ms.author: lajanuar
localization_priority: Normal
ms.topic: conceptual
ms.openlocfilehash: 33b11a6dfc759fabd54ca2fe2c68978a5d5d1475
ms.sourcegitcommit: 4224c44d169b1a289cbf1d3353de6bc6de7c7ea8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2021
ms.locfileid: "52644617"
---
# <a name="designing-your-microsoft-teams-meeting-extension"></a><span data-ttu-id="5cd5b-103">Entwerfen ihrer Microsoft Teams Besprechungserweiterung</span><span class="sxs-lookup"><span data-stu-id="5cd5b-103">Designing your Microsoft Teams meeting extension</span></span>

<span data-ttu-id="5cd5b-104">Sie können Apps erstellen, um Besprechungen produktiver zu gestalten.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-104">You can create apps to make meetings more productive.</span></span> <span data-ttu-id="5cd5b-105">Bitten Sie z. B. Personen, während eines Anrufs eine Umfrage zu führen, oder senden Sie eine kurze Erinnerung, die den Ablauf der Besprechung nicht unterbricht.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-105">For example, ask people to complete a survey during a call or send a quick reminder that doesn’t interrupt the flow of the meeting.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="5cd5b-106">Microsoft Teams-UI-Kit</span><span class="sxs-lookup"><span data-stu-id="5cd5b-106">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="5cd5b-107">Umfassendere Entwurfsrichtlinien, einschließlich Elemente, die Sie bei Bedarf packen und ändern können, finden Sie im Microsoft Teams UI Kit.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-107">You can find more comprehensive design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5cd5b-108">Holen Sie sich das Microsoft Teams-UI-Kit (Figma)</span><span class="sxs-lookup"><span data-stu-id="5cd5b-108">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-meeting-extension"></a><span data-ttu-id="5cd5b-109">Hinzufügen einer Besprechungserweiterung</span><span class="sxs-lookup"><span data-stu-id="5cd5b-109">Add a meeting extension</span></span>

<span data-ttu-id="5cd5b-110">Benutzer können vor und während besprechungen eine Besprechungserweiterung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-110">Users can add a meeting extension before and during meetings.</span></span> <span data-ttu-id="5cd5b-111">Sie können auch eine App für eine bestimmte Besprechung direkt aus dem Teams hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-111">They also can add an app for a specific meeting directly from the Teams store.</span></span>

### <a name="add-before-a-meeting"></a><span data-ttu-id="5cd5b-112">Hinzufügen vor einer Besprechung</span><span class="sxs-lookup"><span data-stu-id="5cd5b-112">Add before a meeting</span></span>

<span data-ttu-id="5cd5b-113">In den Besprechungsdetails können Benutzer registerkarte hinzufügen **+** auswählen, um das App-Flyout zu öffnen und apps zu finden, die für Besprechungen optimiert sind.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-113">In the meeting details, users can select **Add a tab +** to open the app flyout and find apps optimized for meetings.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/add-before-meeting.png" alt-text="Beispiel zeigt, wie Sie eine Besprechungserweiterung vor einer Besprechung hinzufügen." border="false":::

### <a name="add-during-a-meeting"></a><span data-ttu-id="5cd5b-115">Hinzufügen während einer Besprechung</span><span class="sxs-lookup"><span data-stu-id="5cd5b-115">Add during a meeting</span></span>

# <a name="desktop"></a>[<span data-ttu-id="5cd5b-116">Desktop</span><span class="sxs-lookup"><span data-stu-id="5cd5b-116">Desktop</span></span>](#tab/desktop)

In einer Besprechung können Benutzer **weitere** Hinzufügen einer :::image type="icon" source="../../assets/icons/teams-client-more.png":::  >  **App auswählen** und die app auswählen, die sie möchten.

:::image type="content" source="../../assets/images/apps-in-meetings/add-during-meeting.png" alt-text="Beispiel zeigt, wie Sie während einer Besprechung eine Besprechungserweiterung hinzufügen." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="5cd5b-119">Mobil</span><span class="sxs-lookup"><span data-stu-id="5cd5b-119">Mobile</span></span>](#tab/mobile)

In einer Besprechung können Benutzer **mehr** auswählen und die :::image type="icon" source="../../assets/icons/teams-client-more.png"::: app auswählen, die sie möchten.

:::image type="content" source="../../assets/images/apps-in-meetings/mobile-add-during-meeting.png" alt-text="Beispiel zeigt, wie Sie eine Besprechungserweiterung während einer Besprechung auf mobilen Geräten hinzufügen." border="false":::

---

## <a name="before-a-meeting"></a><span data-ttu-id="5cd5b-122">Vor einer Besprechung</span><span class="sxs-lookup"><span data-stu-id="5cd5b-122">Before a meeting</span></span>

<span data-ttu-id="5cd5b-123">Vor einer Besprechung können Benutzer Inhalte auf der Registerkarte hinzufügen. Das folgende Beispiel zeigt eine Entwurfsfrage, die während des Anrufs beantwortet wird.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-123">Prior to a meeting, users can add content in the tab. The following example shows a draft survey question that people will answer during the call.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/before-meeting-tab.png" alt-text="Beispiel zeigt, wie Inhalte in den Besprechungsdetails vor einem Anruf app-App." border="false":::

### <a name="anatomy-meeting-tab-before-and-after-meetings"></a><span data-ttu-id="5cd5b-125">Anatomie: Registerkarte Besprechung (vor und nach Besprechungen)</span><span class="sxs-lookup"><span data-stu-id="5cd5b-125">Anatomy: Meeting tab (before and after meetings)</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/meeting-details-tab-anatomy.png" alt-text="Beispiel zeigt die Strukturanatomie einer Besprechungsregisterkarte vor und nach einer Besprechung." border="false":::

|<span data-ttu-id="5cd5b-127">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="5cd5b-127">Counter</span></span>|<span data-ttu-id="5cd5b-128">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5cd5b-128">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="5cd5b-129">1</span><span class="sxs-lookup"><span data-stu-id="5cd5b-129">1</span></span>|<span data-ttu-id="5cd5b-130">**Registerkartenname:** Navigationsbezeichnung für Ihre Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-130">**Tab name**: Navigation label for your tab.</span></span>|
|<span data-ttu-id="5cd5b-131">2</span><span class="sxs-lookup"><span data-stu-id="5cd5b-131">2</span></span>|<span data-ttu-id="5cd5b-132">**Registerkartenüberlauf**: Öffnet Registerkartenaktionen, z. B. Umbenennen und Entfernen.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-132">**Tab overflow**: Opens tab actions, such as rename and remove.</span></span>|
|<span data-ttu-id="5cd5b-133">3</span><span class="sxs-lookup"><span data-stu-id="5cd5b-133">3</span></span>|<span data-ttu-id="5cd5b-134">**iframe**: Zeigt Ihre App-Inhalte an.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-134">**iframe**: Displays your app content.</span></span>|

### <a name="designing-with-ui-templates"></a><span data-ttu-id="5cd5b-135">Entwerfen mit Benutzeroberflächenvorlagen</span><span class="sxs-lookup"><span data-stu-id="5cd5b-135">Designing with UI templates</span></span>

<span data-ttu-id="5cd5b-136">Verwenden Sie eine der folgenden Teams-UI-Vorlagen, um Die Besprechungsregisterkarte zu entwerfen:</span><span class="sxs-lookup"><span data-stu-id="5cd5b-136">Use one of the following Teams UI templates to help design your meeting tab:</span></span>

* <span data-ttu-id="5cd5b-137">[Liste](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem scannierbaren Format anzeigen und Benutzern das Ausführen von Aktionen für eine gesamte Liste oder einzelne Elemente ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-137">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="5cd5b-138">[Task board:](../../concepts/design/design-teams-app-ui-templates.md#task-board)Ein Task Board, manchmal auch als Kanbanboard oder Schwimmstreifen bezeichnet, ist eine Sammlung von Karten, die häufig zum Nachverfolgen des Status von Arbeitselementen oder Tickets verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-138">[Task board](../../concepts/design/design-teams-app-ui-templates.md#task-board): A task board, sometimes called a kanban board or swim lanes, is a collection of cards often used to track the status of work items or tickets.</span></span>
* <span data-ttu-id="5cd5b-139">[Dashboard:](../../concepts/design/design-teams-app-ui-templates.md#dashboard)Ein Dashboard ist ein Canvas mit mehreren Karten, die eine Übersicht über Daten oder Inhalte bieten.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-139">[Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): A dashboard is a canvas containing multiple cards that provide an overview of data or content.</span></span>
* <span data-ttu-id="5cd5b-140">[Formular](../../concepts/design/design-teams-app-ui-templates.md#form): Formulare sind für die strukturierte Erfassung, Validierung und Übermittlung von Benutzereingaben.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-140">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="5cd5b-141">[Leerer](../../concepts/design/design-teams-app-ui-templates.md#empty-state)Zustand: Die Vorlage für den leeren Zustand kann für viele Szenarien verwendet werden, z. B. für die Anmeldung, die Erstlauferfahrung, Fehlermeldungen und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-141">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>
* <span data-ttu-id="5cd5b-142">[Linkes](../../concepts/design/design-teams-app-advanced-ui-components.md#left-nav)Navigationselement: Die linke Navigationskomponente kann hilfreich sein, wenn Ihre Registerkarte eine Navigation erfordert.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-142">[Left nav](../../concepts/design/design-teams-app-advanced-ui-components.md#left-nav): The left nav component can help if your tab requires some navigation.</span></span> <span data-ttu-id="5cd5b-143">Im Allgemeinen sollten Sie die Navigation auf ein Minimum beschränken.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-143">In general, you should keep navigation to a minimum.</span></span>

## <a name="use-an-in-meeting-tab"></a><span data-ttu-id="5cd5b-144">Verwenden einer Registerkarte in Besprechungen</span><span class="sxs-lookup"><span data-stu-id="5cd5b-144">Use an in-meeting tab</span></span>

<span data-ttu-id="5cd5b-145">Die Registerkarte "In-Meeting" ist ein Zeichenbereich für die Erweiterung der Zusammenarbeit in Besprechungen.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-145">The in-meeting tab is a canvas for augmenting collaboration during meetings.</span></span> <span data-ttu-id="5cd5b-146">Teilnehmer können app-Inhalte in einem dedizierten Bereich außerhalb der Besprechungsphase über freigegebene oder rollenbasierte Ansichten anzeigen und mit ihnen interagieren.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-146">Attendees can see and interact with app content in a dedicated space outside the meeting stage through shared or role-based views.</span></span>

### <a name="use-cases"></a><span data-ttu-id="5cd5b-147">Anwendungsfälle</span><span class="sxs-lookup"><span data-stu-id="5cd5b-147">Use cases</span></span>

<span data-ttu-id="5cd5b-148">Personen können die Registerkarte "In-Meeting" verwenden, um:</span><span class="sxs-lookup"><span data-stu-id="5cd5b-148">People might use the in-meeting tab to:</span></span>

* <span data-ttu-id="5cd5b-149">Geben Sie ausführliches Feedback.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-149">Provide detailed feedback.</span></span> <span data-ttu-id="5cd5b-150">Bewerten Sie beispielsweise einen Stellenkandidaten.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-150">For example, evaluate a job candidate.</span></span>
* <span data-ttu-id="5cd5b-151">Erstellen Sie eine Umfrage, eine Umfrage oder ein Aufgabenelement für die Besprechungsteilnehmer.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-151">Create a poll, survey, or task item for the meeting participants.</span></span>
* <span data-ttu-id="5cd5b-152">Anzeigen von Notizen, die für die Besprechung relevant sind.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-152">Display notes relevant to the meeting.</span></span> <span data-ttu-id="5cd5b-153">Beispielsweise Informationen zu einem Vertriebsleiter.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-153">For example, information about a sales lead.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="5cd5b-154">Desktop</span><span class="sxs-lookup"><span data-stu-id="5cd5b-154">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-tab.png" alt-text="Ein Beispiel zeigt, wie Sie Umfrageinhalte auf einer Registerkarte in besprechungen präsentieren können." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="5cd5b-156">Mobil</span><span class="sxs-lookup"><span data-stu-id="5cd5b-156">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/apps-in-meetings/mobile-use-in-meeting-tab.png" alt-text="Beispiel zeigt, wie Sie Umfrageinhalte auf einer Registerkarte für Besprechungen auf mobilen Geräten präsentieren können." border="false":::

---

### <a name="anatomy-in-meeting-tab"></a><span data-ttu-id="5cd5b-158">Anatomie: Registerkarte "In-Meeting"</span><span class="sxs-lookup"><span data-stu-id="5cd5b-158">Anatomy: In-meeting tab</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-anatomy.png" alt-text="Beispiel zeigt die Strukturanatomie einer Registerkarte in Besprechungen." border="false":::

|<span data-ttu-id="5cd5b-160">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="5cd5b-160">Counter</span></span>|<span data-ttu-id="5cd5b-161">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5cd5b-161">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="5cd5b-162">1</span><span class="sxs-lookup"><span data-stu-id="5cd5b-162">1</span></span>|<span data-ttu-id="5cd5b-163">**App-Symbol (ausgewählt):** 16 Pixel transparentes App-Logo.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-163">**App icon (selected)**: 16-pixel transparent app logo.</span></span>|
|<span data-ttu-id="5cd5b-164">2</span><span class="sxs-lookup"><span data-stu-id="5cd5b-164">2</span></span>|<span data-ttu-id="5cd5b-165">**App-Name**</span><span class="sxs-lookup"><span data-stu-id="5cd5b-165">**App name**</span></span>|
|<span data-ttu-id="5cd5b-166">3</span><span class="sxs-lookup"><span data-stu-id="5cd5b-166">3</span></span>|<span data-ttu-id="5cd5b-167">**Header**: Enthält Ihren App-Namen.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-167">**Header**: Includes your app name.</span></span>|
|<span data-ttu-id="5cd5b-168">4 </span><span class="sxs-lookup"><span data-stu-id="5cd5b-168">4</span></span>|<span data-ttu-id="5cd5b-169">**Schaltfläche Schließen**: Schließt die Registerkarte. Verwenden Sie immer das schließende Symbol oben rechts anstelle einer Aktion in der Fußzeile.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-169">**Close button**: Dismisses the tab. Always use the upper-right close icon instead of an action in the footer.</span></span>|
|<span data-ttu-id="5cd5b-170">5 </span><span class="sxs-lookup"><span data-stu-id="5cd5b-170">5</span></span>|<span data-ttu-id="5cd5b-171">**Benachrichtigungsleiste**: Fehlerwarnungen werden direkt unterhalb der Kopfzeile angezeigt, und der iframe-Inhalt wird um 20 Pixel nach unten geschoben.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-171">**Notification bar**: Error alerts display directly below the header and push the iframe content down by 20 pixels.</span></span>|
|<span data-ttu-id="5cd5b-172">6 </span><span class="sxs-lookup"><span data-stu-id="5cd5b-172">6</span></span>|<span data-ttu-id="5cd5b-173">**iframe**: Zeigt Ihre App-Inhalte an.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-173">**iframe**: Displays your app content.</span></span>|

### <a name="spacing"></a><span data-ttu-id="5cd5b-174">Abstand</span><span class="sxs-lookup"><span data-stu-id="5cd5b-174">Spacing</span></span>

<span data-ttu-id="5cd5b-175">Optimieren Sie ihre Registerkarte in Besprechungen so, dass sie in den 280 Pixel breiten iframe-Bereich passt.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-175">Optimize your in-meeting tab to fit edge-to-edge within the 280 pixel-wide iframe area.</span></span> <span data-ttu-id="5cd5b-176">Es gibt 20 Pixel Abstand auf der linken und rechten Seite des iframes und zwischen der Registerkartenkopfzeile.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-176">There are 20 pixels of padding on the left and right sides of the iframe and between the tab header.</span></span> <span data-ttu-id="5cd5b-177">Der iframe wird bis zum unteren Rand der Registerkarte vollständig ausblutet.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-177">The iframe is full bleed to the bottom of the tab.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-spacing.png" alt-text="Beispiel zeigt Die Größe der Registerkartenabstände in Besprechungen." border="false":::

### <a name="scrolling"></a><span data-ttu-id="5cd5b-179">Bildlauf</span><span class="sxs-lookup"><span data-stu-id="5cd5b-179">Scrolling</span></span>

<span data-ttu-id="5cd5b-180">Der Iframeinhalt sollte vertikal gescrollt werden.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-180">Iframe contents should scroll vertically.</span></span> <span data-ttu-id="5cd5b-181">Sie können nur den Inhalt sehen, zu dem Sie einen Bildlauf durchgeführt haben (nichts oben oder unten).</span><span class="sxs-lookup"><span data-stu-id="5cd5b-181">You can only see the content you've scrolled to (nothing above or below).</span></span> <span data-ttu-id="5cd5b-182">Die Bildlaufleiste ist Teil des iframe-Inhalts.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-182">The scrollbar is part of the iframe content.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-scrolling.png" alt-text="Beispiel zeigt, wie die Registerkarte in Besprechungen scrollt." border="false":::

### <a name="navigation"></a><span data-ttu-id="5cd5b-184">Navigation</span><span class="sxs-lookup"><span data-stu-id="5cd5b-184">Navigation</span></span>

<span data-ttu-id="5cd5b-185">Für Szenarien mit Navigationsebenen oder hohen Inhalten wird empfohlen, benutzern die Navigation zu einer sekundären Ebene zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-185">For scenarios with navigation layers or heavy content, we recommend allowing users to navigate to a secondary layer.</span></span> <span data-ttu-id="5cd5b-186">Benutzer müssen wieder zur vorherigen Ebene wechseln können.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-186">Users must be able to go back to the previous layer.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav.png" alt-text="Beispiel zeigt die Navigation in Besprechungen." border="false":::

## <a name="use-an-in-meeting-dialog"></a><span data-ttu-id="5cd5b-188">Verwenden eines Besprechungsdialogfelds</span><span class="sxs-lookup"><span data-stu-id="5cd5b-188">Use an in-meeting dialog</span></span>

<span data-ttu-id="5cd5b-189">Besprechungsdialogfelder werden in der Teams angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-189">In-meeting dialogs display on the Teams meeting stage.</span></span> <span data-ttu-id="5cd5b-190">Sie erfordern die Aufmerksamkeit, Bestätigung oder Interaktion eines Benutzers, sind jedoch subtil und unterbrechen die Besprechung nicht.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-190">They require a user's attention, confirmation, or interaction but are subtle and don't interrupt the meeting.</span></span> <span data-ttu-id="5cd5b-191">Sie sollten diese sparsam und für Szenarien verwenden, die leicht und aufgabenorientiert sind.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-191">You should use these sparingly and for scenarios that are light and task oriented.</span></span>

### <a name="use-cases"></a><span data-ttu-id="5cd5b-192">Anwendungsfälle</span><span class="sxs-lookup"><span data-stu-id="5cd5b-192">Use cases</span></span>

<span data-ttu-id="5cd5b-193">Dialoge in Besprechungen werden von einem Benutzer (z. B. dem Besprechungsorganisator) ausgelöst, der die Teilnehmer möglicherweise wie folgt verwenden möchte:</span><span class="sxs-lookup"><span data-stu-id="5cd5b-193">In-meeting dialogs are triggered by a user (such as the meeting organizer) who might want participants to:</span></span>

* <span data-ttu-id="5cd5b-194">Kurzes Feedback</span><span class="sxs-lookup"><span data-stu-id="5cd5b-194">Provide brief feedback</span></span>
* <span data-ttu-id="5cd5b-195">Eine kurze Umfrage oder Umfrage</span><span class="sxs-lookup"><span data-stu-id="5cd5b-195">Take a short survey or poll</span></span>
* <span data-ttu-id="5cd5b-196">Übermitteln von Genehmigungen</span><span class="sxs-lookup"><span data-stu-id="5cd5b-196">Submit approvals</span></span>
* <span data-ttu-id="5cd5b-197">Erinnerungen erhalten</span><span class="sxs-lookup"><span data-stu-id="5cd5b-197">Get reminders</span></span>

# <a name="desktop"></a>[<span data-ttu-id="5cd5b-198">Desktop</span><span class="sxs-lookup"><span data-stu-id="5cd5b-198">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-dialog.png" alt-text="Beispiel zeigt, wie Sie ein Besprechungsdialogfeld verwenden können." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="5cd5b-200">Mobil</span><span class="sxs-lookup"><span data-stu-id="5cd5b-200">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/apps-in-meetings/mobile-use-in-meeting-dialog.png" alt-text="Beispiel zeigt, wie Sie ein Besprechungsdialogfeld auf Mobilgeräten verwenden können." border="false":::

---

### <a name="anatomy-in-meeting-dialog"></a><span data-ttu-id="5cd5b-202">Anatomie: Dialogfeld "In-Meeting"</span><span class="sxs-lookup"><span data-stu-id="5cd5b-202">Anatomy: In-meeting dialog</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-anatomy.png" alt-text="Beispiel zeigt die Strukturanatomie eines Besprechungsdialogfelds." border="false":::

|<span data-ttu-id="5cd5b-204">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="5cd5b-204">Counter</span></span>|<span data-ttu-id="5cd5b-205">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5cd5b-205">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="5cd5b-206">1</span><span class="sxs-lookup"><span data-stu-id="5cd5b-206">1</span></span>|<span data-ttu-id="5cd5b-207">**Header**: Enthält App-Symbol, Name, Aktionszeichenfolge und Schließen-Symbol.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-207">**Header**: Includes app icon, name, action string, and close icon.</span></span>|
|<span data-ttu-id="5cd5b-208">2</span><span class="sxs-lookup"><span data-stu-id="5cd5b-208">2</span></span>|<span data-ttu-id="5cd5b-209">**iframe**: Zeigt Ihre App-Inhalte an.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-209">**iframe**: Displays your app content.</span></span>|

### <a name="anatomy-in-meeting-dialog-header"></a><span data-ttu-id="5cd5b-210">Anatomie: In-Meeting-Dialogkopfzeile</span><span class="sxs-lookup"><span data-stu-id="5cd5b-210">Anatomy: In-meeting dialog header</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-header-anatomy.png" alt-text="Beispiel zeigt die Strukturanatomie eines Besprechungsdialogkopfs." border="false":::

<span data-ttu-id="5cd5b-212">Es gibt zwei Kopfzeilenvarianten.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-212">There are two header variants.</span></span> <span data-ttu-id="5cd5b-213">Verwenden Sie nach Möglichkeit die Variante mit dem Avatar, um zu verstärken, dass das Dialogfeld von einer Person kommt.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-213">When possible, use the variant with the avatar to reinforce that the dialog is coming from a person.</span></span>

|<span data-ttu-id="5cd5b-214">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="5cd5b-214">Counter</span></span>|<span data-ttu-id="5cd5b-215">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5cd5b-215">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="5cd5b-216">1</span><span class="sxs-lookup"><span data-stu-id="5cd5b-216">1</span></span>|<span data-ttu-id="5cd5b-217">**Avatar**: Person, die das Dialogfeld in der Besprechung initiiert.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-217">**Avatar**: Person who initiates the in-meeting dialog.</span></span>|
|<span data-ttu-id="5cd5b-218">2</span><span class="sxs-lookup"><span data-stu-id="5cd5b-218">2</span></span>|<span data-ttu-id="5cd5b-219">**App-Symbol**</span><span class="sxs-lookup"><span data-stu-id="5cd5b-219">**App icon**</span></span>|
|<span data-ttu-id="5cd5b-220">3</span><span class="sxs-lookup"><span data-stu-id="5cd5b-220">3</span></span>|<span data-ttu-id="5cd5b-221">**App-Name**</span><span class="sxs-lookup"><span data-stu-id="5cd5b-221">**App name**</span></span>|
|<span data-ttu-id="5cd5b-222">4 </span><span class="sxs-lookup"><span data-stu-id="5cd5b-222">4</span></span>|<span data-ttu-id="5cd5b-223">**Schaltfläche Schließen**: Schließt das Dialogfeld.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-223">**Close button**: Dismisses the dialog.</span></span>|
|<span data-ttu-id="5cd5b-224">5 </span><span class="sxs-lookup"><span data-stu-id="5cd5b-224">5</span></span>|<span data-ttu-id="5cd5b-225">**Aktionszeichenfolge**: In der Regel wird beschrieben, wer das Dialogfeld initiiert hat.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-225">**Action string**: Typically describes who initiated the dialog.</span></span>|

### <a name="responsive-behavior"></a><span data-ttu-id="5cd5b-226">Dynamisches Verhalten</span><span class="sxs-lookup"><span data-stu-id="5cd5b-226">Responsive behavior</span></span>

<span data-ttu-id="5cd5b-227">Besprechungsdialogfelder können in der Größe variieren, um unterschiedliche Szenarien zu berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-227">In-meeting dialogs can vary in size to account for different scenarios.</span></span> <span data-ttu-id="5cd5b-228">Achten Sie darauf, abstands- und komponentengrößen zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-228">Make sure to maintain padding and component sizes.</span></span>

* <span data-ttu-id="5cd5b-229">**Width**: Sie können die Breite des iframe des Dialogfelds an einer beliebigen Stelle innerhalb des unterstützten Größenbereichs angeben.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-229">**Width**: You can specify the width of the dialog's iframe anywhere within the supported size range.</span></span>
* <span data-ttu-id="5cd5b-230">**Height**: Sie können die Höhe des iframe des Dialogfelds an einer beliebigen Stelle innerhalb des unterstützten Größenbereichs angeben.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-230">**Height**: You can specify the height of the dialog's iframe anywhere within the supported size range.</span></span> <span data-ttu-id="5cd5b-231">Sie können Benutzern auch erlauben, vertikal zu scrollen, wenn Ihre App-Inhalte die maximale Höhe überschreitet.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-231">You also can allow users to scroll vertically if your app content exceeds the maximum height.</span></span>

<span data-ttu-id="5cd5b-232">Geben Sie zum Implementieren die Breite und Höhe mithilfe des Schlüssels [`externalResourceUrl`](~/apps-in-teams-meetings/create-apps-for-teams-meetings.md#notificationsignal-api) an.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-232">To implement, specify the width and height using the [`externalResourceUrl`](~/apps-in-teams-meetings/create-apps-for-teams-meetings.md#notificationsignal-api) key.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-responsive.png" alt-text="Beispiel zeigt das Dialogfeld in der Besprechung. Breite: Min--280 Pixel (248 Pixel iframe). Max.-460 Pixel (428 Pixel iframe). Höhe: 300 Pixel (iframe)." border="false":::

## <a name="after-a-meeting"></a><span data-ttu-id="5cd5b-234">Nach einer Besprechung</span><span class="sxs-lookup"><span data-stu-id="5cd5b-234">After a meeting</span></span>

<span data-ttu-id="5cd5b-235">Sie können nach dem Ende zu einer Besprechung wechseln und App-Inhalte anzeigen.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-235">You can go back to a meeting after it ends and view app content.</span></span> <span data-ttu-id="5cd5b-236">In diesem Beispiel kann der Besprechungsorganisator die Umfrageergebnisse auf der Registerkarte **Contoso** anzeigen. (Hinweis: Aus Entwurfs sicht gibt es keinen Unterschied zwischen der Registerkartenerfahrung vor und nach der Besprechung.)</span><span class="sxs-lookup"><span data-stu-id="5cd5b-236">In this example, the meeting organizer can look at poll results in the **Contoso** tab. (Note: From a design standpoint, there's no difference between a the pre- and post-meeting tab experience.)</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/post-meeting-experience.png" alt-text="Die Beispielillustration zeigt eine Registerkarte nach der Besprechung." border="false":::

## <a name="best-practices"></a><span data-ttu-id="5cd5b-238">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="5cd5b-238">Best practices</span></span>

<span data-ttu-id="5cd5b-239">Verwenden Sie diese Empfehlungen, um eine hochwertige App-Erfahrung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-239">Use these recommendations to create a quality app experience.</span></span>

### <a name="interactions"></a><span data-ttu-id="5cd5b-240">Interaktionen</span><span class="sxs-lookup"><span data-stu-id="5cd5b-240">Interactions</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-do.png" alt-text="Beispiel zum Einschränken der Anzahl von Interaktionen." border="false":::

#### <a name="do-limit-the-number-of-interactions"></a><span data-ttu-id="5cd5b-242">Do: Beschränken der Anzahl von Interaktionen</span><span class="sxs-lookup"><span data-stu-id="5cd5b-242">Do: Limit the number of interactions</span></span>

<span data-ttu-id="5cd5b-243">Entfernen Sie in Besprechungsdialogfeldern unnötige Inhalte, die Benutzern nicht helfen, schnell etwas zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-243">For in-meeting dialogs, remove unnecessary content that doesn't help users accomplish something quickly.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-dont.png" alt-text="Beispiel, in dem gezeigt wird, wie sie keine unnötigen Elemente einführen." border="false":::

#### <a name="dont-introduce-unnecessary-elements"></a><span data-ttu-id="5cd5b-245">Don't: Einführung unnötiger Elemente</span><span class="sxs-lookup"><span data-stu-id="5cd5b-245">Don't: Introduce unnecessary elements</span></span>

<span data-ttu-id="5cd5b-246">Ein einzelnes Besprechungsdialogfeld mit mehreren Interaktionen kann vom Anruf ablenken.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-246">A single in-meeting dialog with multiple interactions can distract from the call.</span></span>

   :::column-end:::
:::row-end:::

### <a name="layout"></a><span data-ttu-id="5cd5b-247">Layout</span><span class="sxs-lookup"><span data-stu-id="5cd5b-247">Layout</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-do.png" alt-text="Beispiel für die Verwendung eines Einspaltendialogfelds." border="false":::

#### <a name="do-use-a-single-column-dialog-layout"></a><span data-ttu-id="5cd5b-249">Do: Verwenden eines einspaltig geöffneten Dialogfeldlayouts</span><span class="sxs-lookup"><span data-stu-id="5cd5b-249">Do: Use a single-column dialog layout</span></span>

<span data-ttu-id="5cd5b-250">Da die Dialoge im Mittelpunkt der Besprechungsphase stehen, sollte der Aufgabenabschluss schnell und einfach sein, um Frust der Benutzer zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-250">Since the dialogs are at the center of the meeting stage, task completion should be fast and simple to avoid user frustration.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-dont.png" alt-text="Beispiel: Sie sollten den Raum einer Besprechungserweiterung nicht überladen." border="false":::

#### <a name="dont-clutter-the-space"></a><span data-ttu-id="5cd5b-252">Don't: Clutter the space</span><span class="sxs-lookup"><span data-stu-id="5cd5b-252">Don't: Clutter the space</span></span>

<span data-ttu-id="5cd5b-253">Dichte oder überstrukturierte Inhalte können ablenkend und überwältigend sein, insbesondere während einer Besprechung.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-253">Dense or overly structured content can be distracting and overwhelming, especially during a meeting.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-do.png" alt-text="Beispiel für ein Einspaltenregisterkartenlayout." border="false":::

#### <a name="do-use-a-single-column-tab-layout"></a><span data-ttu-id="5cd5b-255">Do: Verwenden eines einspaltig geöffneten Registerkartenlayouts</span><span class="sxs-lookup"><span data-stu-id="5cd5b-255">Do: Use a single-column tab layout</span></span>

<span data-ttu-id="5cd5b-256">Aufgrund des schmalen Charakters der Registerkarte in der Besprechung wird dringend empfohlen, den Inhalt in einer einzelnen Spalte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-256">Given the in-meeting tab's narrow nature, we strongly recommend displaying the contents in a single column.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-dont.png" alt-text="Beispiel für eine Registerkarte mit mehreren Spalten." border="false":::

#### <a name="dont-use-multiple-columns"></a><span data-ttu-id="5cd5b-258">Don't: Verwenden mehrerer Spalten</span><span class="sxs-lookup"><span data-stu-id="5cd5b-258">Don't: Use multiple columns</span></span>

<span data-ttu-id="5cd5b-259">Aufgrund des begrenzten Speicherplatzes der Registerkarte "Besprechung" werden Layouts mit mehr als einer Spalte nicht empfohlen.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-259">Due to the limited space of the in-meeting tab, layouts with more than one column aren’t recommended.</span></span>

   :::column-end:::
:::row-end:::

### <a name="controls"></a><span data-ttu-id="5cd5b-260">Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="5cd5b-260">Controls</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-do.png" alt-text="Beispiel, in dem gezeigt wird, wie primäre Steuerelemente rechts ausgerichtet werden." border="false":::

#### <a name="do-right-align-the-primary-action"></a><span data-ttu-id="5cd5b-262">Do: Rechte Ausrichtung der primären Aktion</span><span class="sxs-lookup"><span data-stu-id="5cd5b-262">Do: Right align the primary action</span></span>

<span data-ttu-id="5cd5b-263">Es wird empfohlen, die visuell schwerste Aktion am rechten Ort zu positionieren.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-263">We recommend positioning the most visually heavy action to the right-most location.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-dont.png" alt-text="Beispiel, in dem gezeigt wird, wie Sie primäre Steuerelemente nicht ausrichten sollten." border="false":::

#### <a name="dont-left-or-center-align-actions"></a><span data-ttu-id="5cd5b-265">Don't: Aktionen links oder zentriert ausrichten</span><span class="sxs-lookup"><span data-stu-id="5cd5b-265">Don't: Left or center align actions</span></span>

<span data-ttu-id="5cd5b-266">Dies weicht vom Standardmuster Teams für die Platzierung von Steuerelementen in einem Dialogfeld ab und kann mit einem Dialogfeld hinter dem oberen Dialogfeld in Konflikt stehen.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-266">This deviates from the standard Teams pattern for control placement in a dialog and may conflict with a dialog behind the top one.</span></span>

   :::column-end:::
:::row-end:::

### <a name="scroll"></a><span data-ttu-id="5cd5b-267">Bildlauf</span><span class="sxs-lookup"><span data-stu-id="5cd5b-267">Scroll</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-do.png" alt-text="Beispiel für vertikalen Bildlauf auf einer Registerkarte in Besprechungen." border="false":::

#### <a name="do-scroll-vertically"></a><span data-ttu-id="5cd5b-269">Do: Vertikal scrollen</span><span class="sxs-lookup"><span data-stu-id="5cd5b-269">Do: Scroll vertically</span></span>

<span data-ttu-id="5cd5b-270">Benutzer erwarten vertikalen Bildlauf in Teams (und an anderer Stelle).</span><span class="sxs-lookup"><span data-stu-id="5cd5b-270">Users expect vertical scrolling in Teams (and elsewhere).</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-dont.png" alt-text="Beispiel für einen horizontalen Bildlauf auf einer Registerkarte in Besprechungen." border="false":::

#### <a name="dont-scroll-horizontally"></a><span data-ttu-id="5cd5b-272">Don't: Horizontal scrollen</span><span class="sxs-lookup"><span data-stu-id="5cd5b-272">Don't: Scroll horizontally</span></span>

<span data-ttu-id="5cd5b-273">Horizontaler Bildlauf ist kein erwartetes Verhalten in Teams.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-273">Horizontal scrolling isn’t an expected behavior in Teams.</span></span> <span data-ttu-id="5cd5b-274">Andere Canvases in der Besprechungsumgebung scrollen vertikal.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-274">Other canvases in the meeting environment scroll vertically.</span></span>

   :::column-end:::
:::row-end:::

### <a name="workflows"></a><span data-ttu-id="5cd5b-275">Workflows</span><span class="sxs-lookup"><span data-stu-id="5cd5b-275">Workflows</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-workflow-do.png" alt-text="Beispiel für ein komplexes Szenario auf einer Registerkarte in Besprechungen." border="false":::

#### <a name="do-surface-complex-scenarios-in-the-in-meeting-tab"></a><span data-ttu-id="5cd5b-277">Do: Komplexe Szenarien auf der Registerkarte Besprechungsoberfläche</span><span class="sxs-lookup"><span data-stu-id="5cd5b-277">Do: Surface complex scenarios in the in-meeting tab</span></span>

<span data-ttu-id="5cd5b-278">Wenn Ihre App mehrere Aufgaben umfasst, wird dringend empfohlen, eine Registerkarte in Besprechungen mit einem Layout mit einer einzelnen Spalte zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-278">If your app includes multiple tasks, we strongly recommend using an in-meeting tab with a single-column layout.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-workflow-dont.png" alt-text="Beispiel für komplexe Szenarien in einem Besprechungsdialogfeld." border="false":::

#### <a name="dont-make-in-meeting-dialogs-complex"></a><span data-ttu-id="5cd5b-280">Don't: In-Meeting-Dialoge komplex machen</span><span class="sxs-lookup"><span data-stu-id="5cd5b-280">Don't: Make in-meeting dialogs complex</span></span>

<span data-ttu-id="5cd5b-281">Besprechungsdialogfelder sind für kurze Interaktionen vorgesehen.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-281">In-meeting dialogs are intended for brief interactions.</span></span>

   :::column-end:::
:::row-end:::

### <a name="theming"></a><span data-ttu-id="5cd5b-282">Designs</span><span class="sxs-lookup"><span data-stu-id="5cd5b-282">Theming</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-do.png" alt-text="Beispiel für eine Besprechungserweiterung mit dem dunklen Design." border="false":::

#### <a name="do-use-teams-color-tokens"></a><span data-ttu-id="5cd5b-284">Do: Verwenden Teams Farbtoken</span><span class="sxs-lookup"><span data-stu-id="5cd5b-284">Do: Use Teams color tokens</span></span>

<span data-ttu-id="5cd5b-285">Teams Besprechungen sind für den dunklen Modus optimiert, um visuelles und kognitives Rauschen zu reduzieren, damit benutzer sich auf die Diskussion und freigegebene Inhalte konzentrieren können.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-285">Teams meetings are optimized for dark mode to help reduce visual and cognitive noise so users can focus on the discussion and shared content.</span></span> <span data-ttu-id="5cd5b-286">Erfahren Sie mehr <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">über die Verwendung von Farbtoken (Fluent UI).</a></span><span class="sxs-lookup"><span data-stu-id="5cd5b-286">Learn about using <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">color tokens (Fluent UI)</a>.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-dont.png" alt-text="Beispiel für eine Besprechungserweiterung mit einem (hellen) Standarddesign." border="false":::

#### <a name="dont-hard-code-hex-values"></a><span data-ttu-id="5cd5b-288">Don't: Hexwerte für Hartcode</span><span class="sxs-lookup"><span data-stu-id="5cd5b-288">Don't: Hard code hex values</span></span>

<span data-ttu-id="5cd5b-289">Wenn Sie keine Teams verwenden, sind Ihre Designs weniger skalierbar und nehmen sich mehr Zeit für die Verwaltung.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-289">If you don’t use Teams color tokens, your designs will be less scalable and take more time to manage.</span></span>

   :::column-end:::
:::row-end:::

### <a name="navigation"></a><span data-ttu-id="5cd5b-290">Navigation</span><span class="sxs-lookup"><span data-stu-id="5cd5b-290">Navigation</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-do.png" alt-text="Beispiel für eine Besprechungserweiterung mit einer Schaltfläche &quot;Zurück&quot;." border="false":::

#### <a name="do-have-a-back-button"></a><span data-ttu-id="5cd5b-292">Do: Have a back button</span><span class="sxs-lookup"><span data-stu-id="5cd5b-292">Do: Have a back button</span></span>

<span data-ttu-id="5cd5b-293">Wenn sie mehr als eine Navigationsebene auf einer Registerkarte in Besprechungen haben, müssen Benutzer wieder zu ihren vorherigen Ansichten wechseln können.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-293">If you have more than one layer of navigation in an in-meeting tab, users must be able to go back to their previous views.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-dont.png" alt-text="Beispiel für eine Besprechungserweiterung mit zwei Schaltflächen zum Schließen." border="false":::

#### <a name="dont-include-another-dismiss-button"></a><span data-ttu-id="5cd5b-295">Don't: Include another dismiss button</span><span class="sxs-lookup"><span data-stu-id="5cd5b-295">Don't: Include another dismiss button</span></span>

<span data-ttu-id="5cd5b-296">Das Bereitstellen einer Option zum Schließen von Registerkarteninhalten in Besprechungen kann Probleme verursachen, da bereits eine Schaltfläche in der Kopfzeile vorhanden ist, um die Registerkarte in der Besprechung selbst zu schließen.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-296">Providing an option to close in-meeting tab content may cause issues since there’s already a button in the header to dismiss the in-meeting tab itself.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-caution.png" alt-text="Beispiel für modale (oder Aufgabenmodule) innerhalb einer Registerkarte in Besprechungen." border="false":::

#### <a name="caution-avoid-modals-within-the-in-meeting-tab"></a><span data-ttu-id="5cd5b-298">Vorsicht: Vermeiden von Modalen auf der Registerkarte "Besprechung"</span><span class="sxs-lookup"><span data-stu-id="5cd5b-298">Caution: Avoid modals within the in-meeting tab</span></span>

<span data-ttu-id="5cd5b-299">Modale (auch als Aufgabenmodule bezeichnet) auf der bereits schmalen Registerkarte in Besprechungen können den Inhalt umschließen und verhüllen.</span><span class="sxs-lookup"><span data-stu-id="5cd5b-299">Modals (also known as task modules) in the already narrow in-meeting tab might wrap and obscure the content.</span></span>

   :::column-end:::
:::row-end:::
