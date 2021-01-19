---
title: Entwerfen der Besprechungserweiterung
author: heath-hamilton
description: Erfahren Sie, wie Sie Apps in Teams-Besprechungen entwerfen und das Microsoft Teams UI Kit erhalten.
ms.author: lajanuar
ms.topic: conceptual
ms.openlocfilehash: c6e76356b698da4e32e279b0842ab2cc35254e99
ms.sourcegitcommit: 84f408aa2854aa7a5cefaa66ce9a373b19e0864a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/18/2021
ms.locfileid: "49886758"
---
# <a name="designing-your-microsoft-teams-meeting-extension"></a><span data-ttu-id="c17fb-103">Entwerfen Ihrer Microsoft Teams-Besprechungserweiterung</span><span class="sxs-lookup"><span data-stu-id="c17fb-103">Designing your Microsoft Teams meeting extension</span></span>

<span data-ttu-id="c17fb-104">Sie können Apps erstellen, um Besprechungen produktiver zu gestalten.</span><span class="sxs-lookup"><span data-stu-id="c17fb-104">You can create apps to make meetings more productive.</span></span> <span data-ttu-id="c17fb-105">Bitten Sie beispielsweise Personen, während eines Anrufs eine Umfrage zu führen, oder senden Sie eine kurze Erinnerung, die den Ablauf der Besprechung nicht unterbricht.</span><span class="sxs-lookup"><span data-stu-id="c17fb-105">For example, ask people to complete a survey during a call or send a quick reminder that doesn’t interrupt the flow of the meeting.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="c17fb-106">Microsoft Teams UI Kit</span><span class="sxs-lookup"><span data-stu-id="c17fb-106">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="c17fb-107">Umfassendere Designrichtlinien, einschließlich Elemente, die Sie bei Bedarf verwenden und ändern können, finden Sie im Microsoft Teams UI Kit.</span><span class="sxs-lookup"><span data-stu-id="c17fb-107">You can find more comprehensive design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c17fb-108">Microsoft Teams UI Kit (Bissma)</span><span class="sxs-lookup"><span data-stu-id="c17fb-108">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-meeting-extension"></a><span data-ttu-id="c17fb-109">Hinzufügen einer Besprechungserweiterung</span><span class="sxs-lookup"><span data-stu-id="c17fb-109">Add a meeting extension</span></span>

<span data-ttu-id="c17fb-110">Sie können vor und während Besprechungen eine Besprechungserweiterung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="c17fb-110">You can add a meeting extension before and during meetings.</span></span> <span data-ttu-id="c17fb-111">Sie können eine App für eine bestimmte Besprechung auch direkt aus dem Teams Store (AppSource) hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="c17fb-111">You also can add an app for a specific meeting directly from the Teams store (AppSource).</span></span>

### <a name="add-before-a-meeting"></a><span data-ttu-id="c17fb-112">Hinzufügen vor einer Besprechung</span><span class="sxs-lookup"><span data-stu-id="c17fb-112">Add before a meeting</span></span>

<span data-ttu-id="c17fb-113">Wählen Sie in den Besprechungsdetails "Registerkarte **hinzufügen" aus,** um das App-Flyout zu öffnen und apps zu suchen, die für Besprechungen optimiert sind.</span><span class="sxs-lookup"><span data-stu-id="c17fb-113">In the meeting details, select **Add a tab +** to open the app flyout and find apps optimized for meetings.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/add-before-meeting.png" alt-text="Im Beispiel wird gezeigt, wie Sie vor einer Besprechung eine Besprechungserweiterung hinzufügen." border="false":::

### <a name="add-during-a-meeting"></a><span data-ttu-id="c17fb-115">Hinzufügen während einer Besprechung</span><span class="sxs-lookup"><span data-stu-id="c17fb-115">Add during a meeting</span></span>

Wählen Sie in einer Besprechung **"Weitere** :::image type="icon" source="../../assets/icons/teams-client-more.png":::  >  **Hinzufügen einer App"** aus, und wählen Sie die App aus, die Sie wünschen.

:::image type="content" source="../../assets/images/apps-in-meetings/add-during-meeting.png" alt-text="Beispiel zeigt, wie sie während einer Besprechung eine Besprechungserweiterung hinzufügen." border="false":::

## <a name="before-a-meeting"></a><span data-ttu-id="c17fb-118">Vor einer Besprechung</span><span class="sxs-lookup"><span data-stu-id="c17fb-118">Before a meeting</span></span>

<span data-ttu-id="c17fb-119">Vor Ihrer Besprechung können Sie Inhalte auf der Registerkarte hinzufügen. Das folgende Beispiel zeigt einen Umfrageentwurf, den Personen während des Anrufs beantworten.</span><span class="sxs-lookup"><span data-stu-id="c17fb-119">Prior to your meeting, you can add content in the tab. The following example shows a draft survey question that people will answer during the call.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/before-meeting-tab.png" alt-text="Im Beispiel wird gezeigt, wie Inhalte in den Besprechungsdetails vor einem Anruf app-n." border="false":::

### <a name="anatomy-meeting-tab-before-and-after-meetings"></a><span data-ttu-id="c17fb-121">Anatomie: Registerkarte "Besprechung" (vor und nach Besprechungen)</span><span class="sxs-lookup"><span data-stu-id="c17fb-121">Anatomy: Meeting tab (before and after meetings)</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/meeting-details-tab-anatomy.png" alt-text="Beispiel zeigt die strukturell angepasste Struktur einer Besprechungsregisterkarte vor und nach einer Besprechung." border="false":::

|<span data-ttu-id="c17fb-123">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="c17fb-123">Counter</span></span>|<span data-ttu-id="c17fb-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c17fb-124">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="c17fb-125">1</span><span class="sxs-lookup"><span data-stu-id="c17fb-125">1</span></span>|<span data-ttu-id="c17fb-126">**Registerkartenname:** Navigationsbezeichnung für Ihre Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="c17fb-126">**Tab name**: Navigation label for your tab.</span></span>|
|<span data-ttu-id="c17fb-127">2 </span><span class="sxs-lookup"><span data-stu-id="c17fb-127">2</span></span>|<span data-ttu-id="c17fb-128">**Registerkartenüberlauf:** Öffnet Registerkartenaktionen, z. B. Umbenennen und Entfernen.</span><span class="sxs-lookup"><span data-stu-id="c17fb-128">**Tab overflow**: Opens tab actions, such as rename and remove.</span></span>|
|<span data-ttu-id="c17fb-129">3</span><span class="sxs-lookup"><span data-stu-id="c17fb-129">3</span></span>|<span data-ttu-id="c17fb-130">**iframe**: Zeigt Ihre App-Inhalte an.</span><span class="sxs-lookup"><span data-stu-id="c17fb-130">**iframe**: Displays your app content.</span></span>|

### <a name="designing-with-ui-templates"></a><span data-ttu-id="c17fb-131">Entwerfen mit Benutzeroberflächenvorlagen</span><span class="sxs-lookup"><span data-stu-id="c17fb-131">Designing with UI templates</span></span>

<span data-ttu-id="c17fb-132">Verwenden Sie eine der folgenden Teams-UI-Vorlagen, um Ihre Besprechungsregisterkarte zu entwerfen:</span><span class="sxs-lookup"><span data-stu-id="c17fb-132">Use one of the following Teams UI templates to help design your meeting tab:</span></span>

* <span data-ttu-id="c17fb-133">[Liste](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem scannierbaren Format anzeigen und Benutzern das Ausführen von Aktionen für eine gesamte Liste oder einzelne Elemente ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="c17fb-133">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="c17fb-134">[Task Board:](../../concepts/design/design-teams-app-ui-templates.md#task-board)Ein Task Board, manchmal auch als Kanban Board oder Rettungsweg bezeichnet, ist eine Sammlung von Karten, die häufig verwendet werden, um den Status von Arbeitselementen oder Tickets nachverfolgt.</span><span class="sxs-lookup"><span data-stu-id="c17fb-134">[Task board](../../concepts/design/design-teams-app-ui-templates.md#task-board): A task board, sometimes called a kanban board or swim lanes, is a collection of cards often used to track the status of work items or tickets.</span></span>
* <span data-ttu-id="c17fb-135">[Dashboard:](../../concepts/design/design-teams-app-ui-templates.md#dashboard)Ein Dashboard ist eine Canvas mit mehreren Karten, die eine Übersicht über Daten oder Inhalte bieten.</span><span class="sxs-lookup"><span data-stu-id="c17fb-135">[Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): A dashboard is a canvas containing multiple cards that provide an overview of data or content.</span></span>
* <span data-ttu-id="c17fb-136">[Formular:](../../concepts/design/design-teams-app-ui-templates.md#form)Formulare sind für die strukturierte Erfassung, Validierung und Übermittlung von Benutzereingaben.</span><span class="sxs-lookup"><span data-stu-id="c17fb-136">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="c17fb-137">[Leerer](../../concepts/design/design-teams-app-ui-templates.md#empty-state)Zustand: Die Vorlage "Leerer Zustand" kann für viele Szenarien verwendet werden, z. B. anmeldung, Erste Ausführung, Fehlermeldungen und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="c17fb-137">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>
* <span data-ttu-id="c17fb-138">[Linke Navigationsleiste:](../../concepts/design/design-teams-app-ui-templates.md#left-nav)Die linke Navigationsvorlage kann hilfreich sein, wenn ihre Registerkarte eine gewisse Navigation erfordert.</span><span class="sxs-lookup"><span data-stu-id="c17fb-138">[Left nav](../../concepts/design/design-teams-app-ui-templates.md#left-nav): The left nav template can help if your tab requires some navigation.</span></span> <span data-ttu-id="c17fb-139">Im Allgemeinen sollten Sie die Registerkartennavigation auf ein Minimum beschränken.</span><span class="sxs-lookup"><span data-stu-id="c17fb-139">In general, you should keep tab navigation to a minimum.</span></span>

## <a name="use-an-in-meeting-tab"></a><span data-ttu-id="c17fb-140">Verwenden einer Registerkarte für Besprechungen</span><span class="sxs-lookup"><span data-stu-id="c17fb-140">Use an in-meeting tab</span></span>

<span data-ttu-id="c17fb-141">Die Registerkarte "Besprechung" ist eine Canvas zum Erweitern der Zusammenarbeit während Besprechungen.</span><span class="sxs-lookup"><span data-stu-id="c17fb-141">The in-meeting tab is a canvas for augmenting collaboration during meetings.</span></span> <span data-ttu-id="c17fb-142">Teilnehmer können über freigegebene oder rollenbasierte Ansichten in einem dedizierten Bereich außerhalb der Besprechungsphase mit den Inhalten der App interagieren.</span><span class="sxs-lookup"><span data-stu-id="c17fb-142">Attendees can see and interact with app content in a dedicated space outside the meeting stage through shared or role-based views.</span></span>

### <a name="use-cases"></a><span data-ttu-id="c17fb-143">Anwendungsfälle</span><span class="sxs-lookup"><span data-stu-id="c17fb-143">Use cases</span></span>

<span data-ttu-id="c17fb-144">Personen können die Registerkarte "Besprechung" verwenden, um:</span><span class="sxs-lookup"><span data-stu-id="c17fb-144">People might use the in-meeting tab to:</span></span>

* <span data-ttu-id="c17fb-145">Geben Sie detailliertes Feedback (z. B. Bewerten eines Stellenkandidaten)</span><span class="sxs-lookup"><span data-stu-id="c17fb-145">Provide detailed feedback (for example, evaluate a job candidate)</span></span>
* <span data-ttu-id="c17fb-146">Schnelles Erstellen eines Umfrage-, Umfrage- oder Aufgabenelements für die Besprechungsteilnehmer</span><span class="sxs-lookup"><span data-stu-id="c17fb-146">Quickly create a poll, survey, or task item for the meeting participants</span></span>
* <span data-ttu-id="c17fb-147">Anzeigen von für die Besprechung relevanten Notizen (z. B. Informationen zu einem Vertriebsleiter)</span><span class="sxs-lookup"><span data-stu-id="c17fb-147">Display notes relevant to the meeting (for example, information about a sales lead)</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-tab.png" alt-text="Ein Beispiel zeigt, wie Sie Umfrageinhalte auf einer Registerkarte für Besprechungen präsentieren können." border="false":::

### <a name="anatomy-in-meeting-tab"></a><span data-ttu-id="c17fb-149">Aufbau: Registerkarte "In-Meeting"</span><span class="sxs-lookup"><span data-stu-id="c17fb-149">Anatomy: In-meeting tab</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-anatomy.png" alt-text="Beispiel zeigt die strukturell angepasste Struktur einer Registerkarte in Besprechungen." border="false":::

|<span data-ttu-id="c17fb-151">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="c17fb-151">Counter</span></span>|<span data-ttu-id="c17fb-152">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c17fb-152">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="c17fb-153">1</span><span class="sxs-lookup"><span data-stu-id="c17fb-153">1</span></span>|<span data-ttu-id="c17fb-154">**App-Symbol (ausgewählt):** 16 Pixel transparentes App-Logo.</span><span class="sxs-lookup"><span data-stu-id="c17fb-154">**App icon (selected)**: 16-pixel transparent app logo.</span></span>|
|<span data-ttu-id="c17fb-155">2 </span><span class="sxs-lookup"><span data-stu-id="c17fb-155">2</span></span>|<span data-ttu-id="c17fb-156">**App-Name**</span><span class="sxs-lookup"><span data-stu-id="c17fb-156">**App name**</span></span>|
|<span data-ttu-id="c17fb-157">3</span><span class="sxs-lookup"><span data-stu-id="c17fb-157">3</span></span>|<span data-ttu-id="c17fb-158">**Header:** Enthält den App-Namen.</span><span class="sxs-lookup"><span data-stu-id="c17fb-158">**Header**: Includes your app name.</span></span>|
|<span data-ttu-id="c17fb-159">4 </span><span class="sxs-lookup"><span data-stu-id="c17fb-159">4</span></span>|<span data-ttu-id="c17fb-160">**Schaltfläche "Schließen":** Schließt die Registerkarte. Verwenden Sie immer das obere rechte Schließensymbol anstelle einer Aktion in der Fußzeile.</span><span class="sxs-lookup"><span data-stu-id="c17fb-160">**Close button**: Dismisses the tab. Always use the upper-right close icon instead of an action in the footer.</span></span>|
|<span data-ttu-id="c17fb-161">5 </span><span class="sxs-lookup"><span data-stu-id="c17fb-161">5</span></span>|<span data-ttu-id="c17fb-162">**Benachrichtigungsleiste:** Fehlerwarnungen werden direkt unterhalb der Kopfzeile angezeigt, und der iframe-Inhalt wird um 20 Pixel nach unten geschoben.</span><span class="sxs-lookup"><span data-stu-id="c17fb-162">**Notification bar**: Error alerts display directly below the header and push the iframe content down by 20 pixels.</span></span>|
|<span data-ttu-id="c17fb-163">6 </span><span class="sxs-lookup"><span data-stu-id="c17fb-163">6</span></span>|<span data-ttu-id="c17fb-164">**iframe**: Zeigt Ihre App-Inhalte an.</span><span class="sxs-lookup"><span data-stu-id="c17fb-164">**iframe**: Displays your app content.</span></span>|

### <a name="spacing"></a><span data-ttu-id="c17fb-165">Abstand</span><span class="sxs-lookup"><span data-stu-id="c17fb-165">Spacing</span></span>

<span data-ttu-id="c17fb-166">Optimieren Sie Ihre Registerkarte in Besprechungen so, dass sie in den 280 Pixel breiten iframe-Bereich von Rand zu Rand passt.</span><span class="sxs-lookup"><span data-stu-id="c17fb-166">Optimize your in-meeting tab to fit edge-to-edge within the 280 pixel-wide iframe area.</span></span> <span data-ttu-id="c17fb-167">Es gibt 20 Pixel Abstand auf der linken und rechten Seite des iframe und zwischen der Registerkartenüberschrift.</span><span class="sxs-lookup"><span data-stu-id="c17fb-167">There are 20 pixels of padding on the left and right sides of the iframe and between the tab header.</span></span> <span data-ttu-id="c17fb-168">Der iframe ist vollständig beschnitten bis unten auf der Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="c17fb-168">The iframe is full bleed to the bottom of the tab.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-spacing.png" alt-text="Beispiel zeigt die Abmessungen des Abstands von Registerkarten in Besprechungen." border="false":::

### <a name="scrolling"></a><span data-ttu-id="c17fb-170">Scrollen</span><span class="sxs-lookup"><span data-stu-id="c17fb-170">Scrolling</span></span>

<span data-ttu-id="c17fb-171">Der Bildlauf von Iframeinhalten sollte vertikal durchgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="c17fb-171">Iframe contents should scroll vertically.</span></span> <span data-ttu-id="c17fb-172">Sie können nur den Inhalt sehen, zu dem Sie einen Bildlauf durchgeführt haben (nichts über oder darunter).</span><span class="sxs-lookup"><span data-stu-id="c17fb-172">You can only see the content you've scrolled to (nothing above or below).</span></span> <span data-ttu-id="c17fb-173">Die Bildlaufleiste ist Teil des iframe-Inhalts.</span><span class="sxs-lookup"><span data-stu-id="c17fb-173">The scrollbar is part of the iframe content.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-scrolling.png" alt-text="Beispiel zeigt, wie die Registerkarte in der Besprechung scrollt." border="false":::

### <a name="navigation"></a><span data-ttu-id="c17fb-175">Navigation</span><span class="sxs-lookup"><span data-stu-id="c17fb-175">Navigation</span></span>

<span data-ttu-id="c17fb-176">Für Szenarien mit Navigationsebenen oder hohen Inhalten wird empfohlen, Benutzern die Navigation zu einer sekundären Ebene zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="c17fb-176">For scenarios with navigation layers or heavy content, we recommend allowing users to navigate to a secondary layer.</span></span> <span data-ttu-id="c17fb-177">Benutzer müssen zur vorherigen Ebene zurück wechseln können.</span><span class="sxs-lookup"><span data-stu-id="c17fb-177">Users must be able to go back to the previous layer.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav.png" alt-text="Beispiel zeigt die Navigation in Besprechungen." border="false":::

## <a name="use-an-in-meeting-dialog"></a><span data-ttu-id="c17fb-179">Verwenden eines Besprechungsdialogfelds</span><span class="sxs-lookup"><span data-stu-id="c17fb-179">Use an in-meeting dialog</span></span>

<span data-ttu-id="c17fb-180">Dialoge in Besprechungen werden auf der Besprechungsphase von Teams angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c17fb-180">In-meeting dialogs display on the Teams meeting stage.</span></span> <span data-ttu-id="c17fb-181">Sie erfordern die Aufmerksamkeit, Bestätigung oder Interaktion eines Benutzers, sind aber dezent und unterbrechen die Besprechung nicht.</span><span class="sxs-lookup"><span data-stu-id="c17fb-181">They require a user's attention, confirmation, or interaction but are subtle and don't interrupt the meeting.</span></span> <span data-ttu-id="c17fb-182">Sie sollten diese sparsam und für Szenarien verwenden, die einfach und aufgabenorientiert sind.</span><span class="sxs-lookup"><span data-stu-id="c17fb-182">You should use these sparingly and for scenarios that are light and task oriented.</span></span>

### <a name="use-cases"></a><span data-ttu-id="c17fb-183">Anwendungsfälle</span><span class="sxs-lookup"><span data-stu-id="c17fb-183">Use cases</span></span>

<span data-ttu-id="c17fb-184">Dialogfelder in Besprechungen werden von einem Benutzer (z. B. dem Besprechungsorganisator) ausgelöst, der die Teilnehmer möglicherweise zu den:</span><span class="sxs-lookup"><span data-stu-id="c17fb-184">In-meeting dialogs are triggered by a user (such as the meeting organizer) who might want participants to:</span></span>

* <span data-ttu-id="c17fb-185">Bereitstellen von kurzem Feedback</span><span class="sxs-lookup"><span data-stu-id="c17fb-185">Provide brief feedback</span></span>
* <span data-ttu-id="c17fb-186">Nehmen Sie eine kurze Umfrage oder Umfrage vor.</span><span class="sxs-lookup"><span data-stu-id="c17fb-186">Take a short survey or poll</span></span>
* <span data-ttu-id="c17fb-187">Übermitteln von Genehmigungen</span><span class="sxs-lookup"><span data-stu-id="c17fb-187">Submit approvals</span></span>
* <span data-ttu-id="c17fb-188">Erinnerungen erhalten</span><span class="sxs-lookup"><span data-stu-id="c17fb-188">Get reminders</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-dialog.png" alt-text="Im Beispiel wird gezeigt, wie Sie ein Dialogfeld in Besprechungen verwenden können." border="false":::

### <a name="anatomy-in-meeting-dialog"></a><span data-ttu-id="c17fb-190">Aufbau: Dialogfeld "In-Meeting"</span><span class="sxs-lookup"><span data-stu-id="c17fb-190">Anatomy: In-meeting dialog</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-anatomy.png" alt-text="Das Beispiel zeigt die strukturell anatomische Struktur eines Dialogfelds in der Besprechung." border="false":::

|<span data-ttu-id="c17fb-192">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="c17fb-192">Counter</span></span>|<span data-ttu-id="c17fb-193">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c17fb-193">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="c17fb-194">1</span><span class="sxs-lookup"><span data-stu-id="c17fb-194">1</span></span>|<span data-ttu-id="c17fb-195">**Header:** Enthält App-Symbol, -Name, Aktionszeichenfolge und Schließen-Symbol.</span><span class="sxs-lookup"><span data-stu-id="c17fb-195">**Header**: Includes app icon, name, action string, and close icon.</span></span>|
|<span data-ttu-id="c17fb-196">2 </span><span class="sxs-lookup"><span data-stu-id="c17fb-196">2</span></span>|<span data-ttu-id="c17fb-197">**iframe**: Zeigt Ihre App-Inhalte an.</span><span class="sxs-lookup"><span data-stu-id="c17fb-197">**iframe**: Displays your app content.</span></span>|

### <a name="anatomy-in-meeting-dialog-header"></a><span data-ttu-id="c17fb-198">Aufbau: Kopfzeile des Dialogfelds "In-Meeting"</span><span class="sxs-lookup"><span data-stu-id="c17fb-198">Anatomy: In-meeting dialog header</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-header-anatomy.png" alt-text="Das Beispiel zeigt die strukturell angepasste Struktur eines Dialogkopfs in besprechungsind." border="false":::

<span data-ttu-id="c17fb-200">Es gibt zwei Kopfzeilenvarianten.</span><span class="sxs-lookup"><span data-stu-id="c17fb-200">There are two header variants.</span></span> <span data-ttu-id="c17fb-201">Verwenden Sie nach Möglichkeit die Variante mit dem Avatar, um zu verstärken, dass das Dialogfeld von einer Person kommt.</span><span class="sxs-lookup"><span data-stu-id="c17fb-201">When possible, use the variant with the avatar to reinforce that the dialog is coming from a person.</span></span>

|<span data-ttu-id="c17fb-202">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="c17fb-202">Counter</span></span>|<span data-ttu-id="c17fb-203">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c17fb-203">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="c17fb-204">1</span><span class="sxs-lookup"><span data-stu-id="c17fb-204">1</span></span>|<span data-ttu-id="c17fb-205">**Avatar:** Person, die das Dialogfeld in der Besprechung initiiert.</span><span class="sxs-lookup"><span data-stu-id="c17fb-205">**Avatar**: Person who initiates the in-meeting dialog.</span></span>|
|<span data-ttu-id="c17fb-206">2 </span><span class="sxs-lookup"><span data-stu-id="c17fb-206">2</span></span>|<span data-ttu-id="c17fb-207">**Symbol "App"**</span><span class="sxs-lookup"><span data-stu-id="c17fb-207">**App icon**</span></span>|
|<span data-ttu-id="c17fb-208">3</span><span class="sxs-lookup"><span data-stu-id="c17fb-208">3</span></span>|<span data-ttu-id="c17fb-209">**App-Name**</span><span class="sxs-lookup"><span data-stu-id="c17fb-209">**App name**</span></span>|
|<span data-ttu-id="c17fb-210">4 </span><span class="sxs-lookup"><span data-stu-id="c17fb-210">4</span></span>|<span data-ttu-id="c17fb-211">**Schaltfläche "Schließen":** Schließt das Dialogfeld.</span><span class="sxs-lookup"><span data-stu-id="c17fb-211">**Close button**: Dismisses the dialog.</span></span>|
|<span data-ttu-id="c17fb-212">5 </span><span class="sxs-lookup"><span data-stu-id="c17fb-212">5</span></span>|<span data-ttu-id="c17fb-213">**Aktionszeichenfolge:** In der Regel wird beschrieben, wer das Dialogfeld initiiert hat.</span><span class="sxs-lookup"><span data-stu-id="c17fb-213">**Action string**: Typically describes who initiated the dialog.</span></span>|

### <a name="responsive-behavior"></a><span data-ttu-id="c17fb-214">Dynamisches Verhalten</span><span class="sxs-lookup"><span data-stu-id="c17fb-214">Responsive behavior</span></span>

<span data-ttu-id="c17fb-215">Dialoge in Besprechungen können je nach Größe variieren, um unterschiedliche Szenarien zu berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="c17fb-215">In-meeting dialogs can vary in size to account for different scenarios.</span></span> <span data-ttu-id="c17fb-216">Achten Sie darauf, abstands- und komponentengrößen zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="c17fb-216">Make sure to maintain padding and component sizes.</span></span>

* <span data-ttu-id="c17fb-217">**Breite:** Die Breite des iframe ist ein absoluter Wert innerhalb des angegebenen Bereichs.</span><span class="sxs-lookup"><span data-stu-id="c17fb-217">**Width**: The iframe width is an absolute value within the range you specify.</span></span>
* <span data-ttu-id="c17fb-218">**Höhe:** Die Höhe des Dialogfelds wird durch den Inhalt im iframe bestimmt.</span><span class="sxs-lookup"><span data-stu-id="c17fb-218">**Height**: The height of the dialog is determined by the content in the iframe.</span></span> <span data-ttu-id="c17fb-219">Der vertikale Bildlauf übernimmt den Inhalt, der die maximale Höhe überschreitet.</span><span class="sxs-lookup"><span data-stu-id="c17fb-219">Vertical scroll takes over for content that exceeds the maximum height.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-responsive.png" alt-text="Das Beispiel zeigt das Dialogfeld &quot;In-Meeting&quot;. Breite: Min--280 Pixel (248 Pixel iframe). Max- 460 Pixel (428 Pixel iframe). Höhe: 300 Pixel (iframe)." border="false":::

## <a name="after-a-meeting"></a><span data-ttu-id="c17fb-221">Nach einer Besprechung</span><span class="sxs-lookup"><span data-stu-id="c17fb-221">After a meeting</span></span>

<span data-ttu-id="c17fb-222">Sie können zu einer Besprechung zurück wechseln, nachdem sie beendet wurde, und den Inhalt der App anzeigen.</span><span class="sxs-lookup"><span data-stu-id="c17fb-222">You can go back to a meeting after it ends and view app content.</span></span> <span data-ttu-id="c17fb-223">In diesem Beispiel kann der Besprechungsorganisator die Umfrageergebnisse auf der Registerkarte **"Contoso"** anzeigen. (Hinweis: Aus Entwurfs sicht gibt es keinen Unterschied zwischen der Registerkartenerfahrung vor und nach der Besprechung.)</span><span class="sxs-lookup"><span data-stu-id="c17fb-223">In this example, the meeting organizer can look at poll results in the **Contoso** tab. (Note: From a design standpoint, there's no difference between a the pre- and post-meeting tab experience.)</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/post-meeting-experience.png" alt-text="Beispiel zeigt eine Registerkarte nach der Besprechung." border="false":::

## <a name="best-practices"></a><span data-ttu-id="c17fb-225">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="c17fb-225">Best practices</span></span>

### <a name="interactions"></a><span data-ttu-id="c17fb-226">Interaktionen</span><span class="sxs-lookup"><span data-stu-id="c17fb-226">Interactions</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-do.png" alt-text="Beispiel, in dem gezeigt wird, wie die Anzahl der Interaktionen begrenzt wird." border="false":::

#### <a name="do-limit-the-number-of-interactions"></a><span data-ttu-id="c17fb-228">Do: Limit the number of interactions</span><span class="sxs-lookup"><span data-stu-id="c17fb-228">Do: Limit the number of interactions</span></span>

<span data-ttu-id="c17fb-229">Entfernen Sie in Besprechungsdialogfeldern nicht benötigte Inhalte, die Benutzern nicht helfen, schnell etwas zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="c17fb-229">For in-meeting dialogs, remove unnecessary content that doesn't help users accomplish something quickly.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-dont.png" alt-text="Beispiel, in dem gezeigt wird, wie sie keine unnötigen Elemente einführen." border="false":::

#### <a name="dont-introduce-unnecessary-elements"></a><span data-ttu-id="c17fb-231">Nicht erforderlich: Unnötige Elemente einführen</span><span class="sxs-lookup"><span data-stu-id="c17fb-231">Don't: Introduce unnecessary elements</span></span>

<span data-ttu-id="c17fb-232">Ein einzelnes Besprechungsdialogfeld mit mehreren Interaktionen kann vom Anruf ablenken.</span><span class="sxs-lookup"><span data-stu-id="c17fb-232">A single in-meeting dialog with multiple interactions can distract from the call.</span></span>

   :::column-end:::
:::row-end:::

### <a name="layout"></a><span data-ttu-id="c17fb-233">Layout</span><span class="sxs-lookup"><span data-stu-id="c17fb-233">Layout</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-do.png" alt-text="Beispiel für die Verwendung eines Einspaltendialogfelds." border="false":::

#### <a name="do-use-a-single-column-dialog-layout"></a><span data-ttu-id="c17fb-235">Do: Use a single-column dialog layout</span><span class="sxs-lookup"><span data-stu-id="c17fb-235">Do: Use a single-column dialog layout</span></span>

<span data-ttu-id="c17fb-236">Da die Dialogfelder im Mittelpunkt der Besprechungsphase stehen, sollte der Aufgabenabschluss schnell und einfach sein, um Frustration der Benutzer zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="c17fb-236">Since the dialogs are at the center of the meeting stage, task completion should be fast and simple to avoid user frustration.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-dont.png" alt-text="Beispiel, in dem gezeigt wird, dass Sie den Platz einer Besprechungserweiterung nicht überladen sollten." border="false":::

#### <a name="dont-clutter-the-space"></a><span data-ttu-id="c17fb-238">Nicht zu vergessen: Überladen des Leerzeichens</span><span class="sxs-lookup"><span data-stu-id="c17fb-238">Don't: Clutter the space</span></span>

<span data-ttu-id="c17fb-239">Dichte oder zu strukturierte Inhalte können ablenkend und überwältigend sein, insbesondere während einer Besprechung.</span><span class="sxs-lookup"><span data-stu-id="c17fb-239">Dense or overly structured content can be distracting and overwhelming, especially during a meeting.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-do.png" alt-text="Beispiel für ein Einspalten-Registerkartenlayout." border="false":::

#### <a name="do-use-a-single-column-tab-layout"></a><span data-ttu-id="c17fb-241">Verwenden eines einspaltig angezeigten Registerkartenlayouts</span><span class="sxs-lookup"><span data-stu-id="c17fb-241">Do: Use a single-column tab layout</span></span>

<span data-ttu-id="c17fb-242">Aufgrund der schmalen Art der Registerkarte in der Besprechung wird dringend empfohlen, den Inhalt in einer einzelnen Spalte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="c17fb-242">Given the in-meeting tab's narrow nature, we strongly recommend displaying the contents in a single column.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-dont.png" alt-text="Beispiel für eine Registerkarte mit mehreren Spalten." border="false":::

#### <a name="dont-use-multiple-columns"></a><span data-ttu-id="c17fb-244">Nicht zu verwenden: Verwenden mehrerer Spalten</span><span class="sxs-lookup"><span data-stu-id="c17fb-244">Don't: Use multiple columns</span></span>

<span data-ttu-id="c17fb-245">Aufgrund des begrenzten Speicherplatzes auf der Registerkarte "Besprechung" werden Layouts mit mehr als einer Spalte nicht empfohlen.</span><span class="sxs-lookup"><span data-stu-id="c17fb-245">Due to the limited space of the in-meeting tab, layouts with more than one column aren’t recommended.</span></span>

   :::column-end:::
:::row-end:::

### <a name="controls"></a><span data-ttu-id="c17fb-246">Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="c17fb-246">Controls</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-do.png" alt-text="Beispiel, in dem gezeigt wird, wie primäre Steuerelemente rechts ausgerichtet werden." border="false":::

#### <a name="do-right-align-the-primary-action"></a><span data-ttu-id="c17fb-248">Do: Right align the primary action</span><span class="sxs-lookup"><span data-stu-id="c17fb-248">Do: Right align the primary action</span></span>

<span data-ttu-id="c17fb-249">Es wird empfohlen, die visuell schwierigste Aktion am rechten Ort zu positionieren.</span><span class="sxs-lookup"><span data-stu-id="c17fb-249">We recommend positioning the most visually heavy action to the right-most location.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-dont.png" alt-text="Beispiel, in dem gezeigt wird, wie primäre Steuerelemente nicht linksb ausgerichtet werden sollen." border="false":::

#### <a name="dont-left-or-center-align-actions"></a><span data-ttu-id="c17fb-251">Nicht zu verwenden: Links- oder zentriert ausgerichtete Aktionen</span><span class="sxs-lookup"><span data-stu-id="c17fb-251">Don't: Left or center align actions</span></span>

<span data-ttu-id="c17fb-252">Dies weicht vom standardmäßigen Teams-Muster für die Steuerelementplatzierung in einem Dialogfeld ab und kann mit einem Dialogfeld hinter dem oberen Dialogfeld in Konflikt stehen.</span><span class="sxs-lookup"><span data-stu-id="c17fb-252">This deviates from the standard Teams pattern for control placement in a dialog and may conflict with a dialog behind the top one.</span></span>

   :::column-end:::
:::row-end:::

### <a name="scroll"></a><span data-ttu-id="c17fb-253">Bildlauf</span><span class="sxs-lookup"><span data-stu-id="c17fb-253">Scroll</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-do.png" alt-text="Beispiel für einen vertikalen Bildlauf auf einer Registerkarte in Besprechungen." border="false":::

#### <a name="do-scroll-vertically"></a><span data-ttu-id="c17fb-255">Do: Scroll vertically</span><span class="sxs-lookup"><span data-stu-id="c17fb-255">Do: Scroll vertically</span></span>

<span data-ttu-id="c17fb-256">Benutzer erwarten vertikales Scrollen in Teams (und an anderer Stelle).</span><span class="sxs-lookup"><span data-stu-id="c17fb-256">Users expect vertical scrolling in Teams (and elsewhere).</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-dont.png" alt-text="Beispiel für einen horizontalen Bildlauf auf einer Registerkarte in einer Besprechung." border="false":::

#### <a name="dont-scroll-horizontally"></a><span data-ttu-id="c17fb-258">Nicht: Horizontaler Bildlauf</span><span class="sxs-lookup"><span data-stu-id="c17fb-258">Don't: Scroll horizontally</span></span>

<span data-ttu-id="c17fb-259">Horizontales Scrollen ist in Teams kein erwartetes Verhalten.</span><span class="sxs-lookup"><span data-stu-id="c17fb-259">Horizontal scrolling isn’t an expected behavior in Teams.</span></span> <span data-ttu-id="c17fb-260">Andere Zeichenblätter in der Besprechungsumgebung scrollen vertikal.</span><span class="sxs-lookup"><span data-stu-id="c17fb-260">Other canvases in the meeting environment scroll vertically.</span></span>

   :::column-end:::
:::row-end:::

### <a name="workflows"></a><span data-ttu-id="c17fb-261">Workflows</span><span class="sxs-lookup"><span data-stu-id="c17fb-261">Workflows</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-workflow-do.png" alt-text="Beispiel für ein komplexes Szenario auf einer Registerkarte in einer Besprechung." border="false":::

#### <a name="do-surface-complex-scenarios-in-the-in-meeting-tab"></a><span data-ttu-id="c17fb-263">Do: Surface complex scenarios in the in-meeting tab</span><span class="sxs-lookup"><span data-stu-id="c17fb-263">Do: Surface complex scenarios in the in-meeting tab</span></span>

<span data-ttu-id="c17fb-264">Wenn Ihre App mehrere Aufgaben umfasst, wird dringend empfohlen, eine Registerkarte in Besprechungen mit einem layout mit einer Spalte zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="c17fb-264">If your app includes multiple tasks, we strongly recommend using an in-meeting tab with a single-column layout.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-workflow-dont.png" alt-text="Beispiel für komplexe Szenarien in einem Besprechungsdialogfeld." border="false":::

#### <a name="dont-make-in-meeting-dialogs-complex"></a><span data-ttu-id="c17fb-266">Nicht zu verwenden: Dialoge in Besprechungen komplex machen</span><span class="sxs-lookup"><span data-stu-id="c17fb-266">Don't: Make in-meeting dialogs complex</span></span>

<span data-ttu-id="c17fb-267">Dialoge in Besprechungen sind für kurze Interaktionen vorgesehen.</span><span class="sxs-lookup"><span data-stu-id="c17fb-267">In-meeting dialogs are intended for brief interactions.</span></span>

   :::column-end:::
:::row-end:::

### <a name="theming"></a><span data-ttu-id="c17fb-268">Designs</span><span class="sxs-lookup"><span data-stu-id="c17fb-268">Theming</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-do.png" alt-text="Beispiel für eine Besprechungserweiterung mit dunklem Design." border="false":::

#### <a name="do-use-teams-color-tokens"></a><span data-ttu-id="c17fb-270">Verwenden von Teams-Farbtoken</span><span class="sxs-lookup"><span data-stu-id="c17fb-270">Do: Use Teams color tokens</span></span>

<span data-ttu-id="c17fb-271">Teams-Besprechungen sind für den dunklen Modus optimiert, um visuelle und kognitive Rauschgeräusche zu reduzieren, damit benutzer sich auf die Diskussion und freigegebene Inhalte konzentrieren können.</span><span class="sxs-lookup"><span data-stu-id="c17fb-271">Teams meetings are optimized for dark mode to help reduce visual and cognitive noise so users can focus on the discussion and shared content.</span></span> <span data-ttu-id="c17fb-272">Erfahren Sie mehr über <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">die Verwendung von Farbtoken (Fluent UI)</a>.</span><span class="sxs-lookup"><span data-stu-id="c17fb-272">Learn about using <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">color tokens (Fluent UI)</a>.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-dont.png" alt-text="Beispiel für eine Besprechungserweiterung mit einem (hellen) Standarddesign." border="false":::

#### <a name="dont-hard-code-hex-values"></a><span data-ttu-id="c17fb-274">Nicht zu beachten: Hartcode-Hexadezimalwerte</span><span class="sxs-lookup"><span data-stu-id="c17fb-274">Don't: Hard code hex values</span></span>

<span data-ttu-id="c17fb-275">Wenn Sie keine Farbtoken von Teams verwenden, sind Ihre Designs weniger skalierbar und nehmen mehr Zeit in Die Verwaltung.</span><span class="sxs-lookup"><span data-stu-id="c17fb-275">If you don’t use Teams color tokens, your designs will be less scalable and take more time to manage.</span></span>

   :::column-end:::
:::row-end:::

### <a name="navigation"></a><span data-ttu-id="c17fb-276">Navigation</span><span class="sxs-lookup"><span data-stu-id="c17fb-276">Navigation</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-do.png" alt-text="Beispiel für eine Besprechungserweiterung mit einer Schaltfläche &quot;Zurück&quot;." border="false":::

#### <a name="do-have-a-back-button"></a><span data-ttu-id="c17fb-278">Do: Have a Back button</span><span class="sxs-lookup"><span data-stu-id="c17fb-278">Do: Have a back button</span></span>

<span data-ttu-id="c17fb-279">Wenn sie auf einer Registerkarte in Besprechungen mehrere Navigationsebenen haben, müssen Benutzer wieder zu ihren vorherigen Ansichten wechseln können.</span><span class="sxs-lookup"><span data-stu-id="c17fb-279">If you have more than one layer of navigation in an in-meeting tab, users must be able to go back to their previous views.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-dont.png" alt-text="Beispiel für eine Besprechungserweiterung mit zwei Schaltflächen zum Schließen." border="false":::

#### <a name="dont-include-another-dismiss-button"></a><span data-ttu-id="c17fb-281">Don't: Include another dismiss button</span><span class="sxs-lookup"><span data-stu-id="c17fb-281">Don't: Include another dismiss button</span></span>

<span data-ttu-id="c17fb-282">Das Bereitstellen einer Option zum Schließen von Registerkarteninhalten in Besprechungen kann Probleme verursachen, da bereits eine Schaltfläche in der Kopfzeile vorhanden ist, um die Registerkarte in der Besprechung selbst zu schließen.</span><span class="sxs-lookup"><span data-stu-id="c17fb-282">Providing an option to close in-meeting tab content may cause issues since there’s already a button in the header to dismiss the in-meeting tab itself.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-caution.png" alt-text="Beispiel mit modalen Modalitäten (oder Aufgabenmodulen) auf einer Registerkarte für Besprechungen." border="false":::

#### <a name="caution-avoid-modals-within-the-in-meeting-tab"></a><span data-ttu-id="c17fb-284">Achtung: Vermeiden Sie Modalitäten auf der Registerkarte "Besprechung".</span><span class="sxs-lookup"><span data-stu-id="c17fb-284">Caution: Avoid modals within the in-meeting tab</span></span>

<span data-ttu-id="c17fb-285">Modale Modalitäten (auch als Aufgabenmodule bezeichnet) auf der bereits schmalen Registerkarte für Besprechungen können den Inhalt umschließen und verfemen.</span><span class="sxs-lookup"><span data-stu-id="c17fb-285">Modals (also known as task modules) in the already narrow in-meeting tab might wrap and obscure the content.</span></span>

   :::column-end:::
:::row-end:::

## <a name="validate-your-design"></a><span data-ttu-id="c17fb-286">Überprüfen Des Designs</span><span class="sxs-lookup"><span data-stu-id="c17fb-286">Validate your design</span></span>

<span data-ttu-id="c17fb-287">Wenn Sie Ihre App in AppSource veröffentlichen möchten, sollten Sie die Designprobleme verstehen, die häufig dazu führen, dass Apps während der Übermittlung fehlschlagen.</span><span class="sxs-lookup"><span data-stu-id="c17fb-287">If you plan to publish your app to AppSource, you should understand the design issues that commonly cause apps to fail during submission.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c17fb-288">Überprüfen der Entwurfsüberprüfungsrichtlinien</span><span class="sxs-lookup"><span data-stu-id="c17fb-288">Check design validation guidelines</span></span>](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines--most-failed-test-cases)
