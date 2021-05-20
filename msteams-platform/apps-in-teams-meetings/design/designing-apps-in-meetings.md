---
title: Entwerfen ihrer Besprechungserweiterung
author: heath-hamilton
description: Erfahren Sie, wie Sie Apps in Teams Meetings entwerfen und das Microsoft Teams UI Kit abrufen.
ms.author: lajanuar
localization_priority: Normal
ms.topic: conceptual
ms.openlocfilehash: 0a888c333305e9caafcd0bac0e5549bf08ead424
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566026"
---
# <a name="designing-your-microsoft-teams-meeting-extension"></a><span data-ttu-id="e207b-103">Entwerfen der Microsoft Teams Besprechungserweiterung</span><span class="sxs-lookup"><span data-stu-id="e207b-103">Designing your Microsoft Teams meeting extension</span></span>

<span data-ttu-id="e207b-104">Sie können Apps erstellen, um Besprechungen produktiver zu gestalten.</span><span class="sxs-lookup"><span data-stu-id="e207b-104">You can create apps to make meetings more productive.</span></span> <span data-ttu-id="e207b-105">Bitten Sie beispielsweise Personen, während eines Anrufs eine Umfrage abzuschließen, oder senden Sie eine schnelle Erinnerung, die den Ablauf der Besprechung nicht unterbricht.</span><span class="sxs-lookup"><span data-stu-id="e207b-105">For example, ask people to complete a survey during a call or send a quick reminder that doesn’t interrupt the flow of the meeting.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="e207b-106">Microsoft Teams-UI-Kit</span><span class="sxs-lookup"><span data-stu-id="e207b-106">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="e207b-107">Umfassendere Entwurfsrichtlinien, einschließlich Elemente, die Sie bei Bedarf greifen und ändern können, finden Sie im Microsoft Teams UI Kit.</span><span class="sxs-lookup"><span data-stu-id="e207b-107">You can find more comprehensive design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e207b-108">Holen Sie sich das Microsoft Teams-UI-Kit (Figma)</span><span class="sxs-lookup"><span data-stu-id="e207b-108">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-meeting-extension"></a><span data-ttu-id="e207b-109">Hinzufügen einer Besprechungserweiterung</span><span class="sxs-lookup"><span data-stu-id="e207b-109">Add a meeting extension</span></span>

<span data-ttu-id="e207b-110">Sie können eine Besprechungserweiterung vor und während der Besprechungen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="e207b-110">You can add a meeting extension before and during meetings.</span></span> <span data-ttu-id="e207b-111">Sie können auch eine App für eine bestimmte Besprechung direkt aus dem Teams Store (AppSource) hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="e207b-111">You also can add an app for a specific meeting directly from the Teams store (AppSource).</span></span>

### <a name="add-before-a-meeting"></a><span data-ttu-id="e207b-112">Hinzufügen vor einer Besprechung</span><span class="sxs-lookup"><span data-stu-id="e207b-112">Add before a meeting</span></span>

<span data-ttu-id="e207b-113">Wählen Sie in den Besprechungsdetails **eine Registerkarte hinzufügen aus,** um das App-Flyout zu öffnen und für Besprechungen optimierte Apps zu finden.</span><span class="sxs-lookup"><span data-stu-id="e207b-113">In the meeting details, select **Add a tab +** to open the app flyout and find apps optimized for meetings.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/add-before-meeting.png" alt-text="Das Beispiel zeigt, wie sie eine Besprechungserweiterung vor einer Besprechung hinzufügen." border="false":::

### <a name="add-during-a-meeting"></a><span data-ttu-id="e207b-115">Hinzufügen während einer Besprechung</span><span class="sxs-lookup"><span data-stu-id="e207b-115">Add during a meeting</span></span>

Wählen Sie in einer Besprechung **Weitere** :::image type="icon" source="../../assets/icons/teams-client-more.png":::  >  **Informationen zum Hinzufügen einer App** aus, und wählen Sie die gewünschte App aus.

:::image type="content" source="../../assets/images/apps-in-meetings/add-during-meeting.png" alt-text="Das Beispiel zeigt, wie sie während einer Besprechung eine Besprechungserweiterung hinzufügen." border="false":::

## <a name="before-a-meeting"></a><span data-ttu-id="e207b-118">Vor einer Besprechung</span><span class="sxs-lookup"><span data-stu-id="e207b-118">Before a meeting</span></span>

<span data-ttu-id="e207b-119">Vor Ihrer Besprechung können Sie Inhalte auf der Registerkarte hinzufügen. Das folgende Beispiel zeigt einen Umfrageentwurf, den die Teilnehmer während des Anrufs beantworten.</span><span class="sxs-lookup"><span data-stu-id="e207b-119">Prior to your meeting, you can add content in the tab. The following example shows a draft survey question that people will answer during the call.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/before-meeting-tab.png" alt-text="Das Beispiel zeigt, wie Sie Inhalte in den Besprechungsdetails vor einem Anruf anzeigen." border="false":::

### <a name="anatomy-meeting-tab-before-and-after-meetings"></a><span data-ttu-id="e207b-121">Anatomie: Registerkarte Meeting (vor und nach Besprechungen)</span><span class="sxs-lookup"><span data-stu-id="e207b-121">Anatomy: Meeting tab (before and after meetings)</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/meeting-details-tab-anatomy.png" alt-text="Das Beispiel zeigt die strukturelle Anatomie einer Besprechungsregisterkarte vor und nach einer Besprechung." border="false":::

|<span data-ttu-id="e207b-123">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="e207b-123">Counter</span></span>|<span data-ttu-id="e207b-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e207b-124">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="e207b-125">1</span><span class="sxs-lookup"><span data-stu-id="e207b-125">1</span></span>|<span data-ttu-id="e207b-126">**Tab-Name**: Navigationsbeschriftung für Ihre Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="e207b-126">**Tab name**: Navigation label for your tab.</span></span>|
|<span data-ttu-id="e207b-127">2</span><span class="sxs-lookup"><span data-stu-id="e207b-127">2</span></span>|<span data-ttu-id="e207b-128">**Tab-Überlauf**: Öffnet Tabstoppaktionen, z. B. Umbenennen und Entfernen.</span><span class="sxs-lookup"><span data-stu-id="e207b-128">**Tab overflow**: Opens tab actions, such as rename and remove.</span></span>|
|<span data-ttu-id="e207b-129">3</span><span class="sxs-lookup"><span data-stu-id="e207b-129">3</span></span>|<span data-ttu-id="e207b-130">**iframe**: Zeigt Ihre App-Inhalte an.</span><span class="sxs-lookup"><span data-stu-id="e207b-130">**iframe**: Displays your app content.</span></span>|

### <a name="designing-with-ui-templates"></a><span data-ttu-id="e207b-131">Entwerfen mit UI-Vorlagen</span><span class="sxs-lookup"><span data-stu-id="e207b-131">Designing with UI templates</span></span>

<span data-ttu-id="e207b-132">Verwenden Sie eine der folgenden Teams UI-Vorlagen, um die Besprechungsregisterkarte zu entwerfen:</span><span class="sxs-lookup"><span data-stu-id="e207b-132">Use one of the following Teams UI templates to help design your meeting tab:</span></span>

* <span data-ttu-id="e207b-133">[Liste](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem scannbaren Format anzeigen und Benutzern ermöglichen, Aktionen für eine gesamte Liste oder einzelne Elemente auszuführen.</span><span class="sxs-lookup"><span data-stu-id="e207b-133">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="e207b-134">[Aufgabentafel](../../concepts/design/design-teams-app-ui-templates.md#task-board): Ein Aufgabenbrett, manchmal auch Kanban-Board oder Schwimmbahnen genannt, ist eine Sammlung von Karten, die oft verwendet werden, um den Status von Arbeitsaufgaben oder Tickets zu verfolgen.</span><span class="sxs-lookup"><span data-stu-id="e207b-134">[Task board](../../concepts/design/design-teams-app-ui-templates.md#task-board): A task board, sometimes called a kanban board or swim lanes, is a collection of cards often used to track the status of work items or tickets.</span></span>
* <span data-ttu-id="e207b-135">[Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): Ein Dashboard ist ein Canvas mit mehreren Karten, die einen Überblick über Daten oder Inhalte bieten.</span><span class="sxs-lookup"><span data-stu-id="e207b-135">[Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): A dashboard is a canvas containing multiple cards that provide an overview of data or content.</span></span>
* <span data-ttu-id="e207b-136">[Formular](../../concepts/design/design-teams-app-ui-templates.md#form): Formulare sind zum Sammeln, Validieren und Übermitteln von Benutzereingaben auf strukturierte Weise.</span><span class="sxs-lookup"><span data-stu-id="e207b-136">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="e207b-137">[Leerer Zustand](../../concepts/design/design-teams-app-ui-templates.md#empty-state): Die leere Statusvorlage kann für viele Szenarien verwendet werden, einschließlich Anmeldung, Erstausführung, Fehlermeldungen und mehr.</span><span class="sxs-lookup"><span data-stu-id="e207b-137">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>
* <span data-ttu-id="e207b-138">[Linkes Navi](../../concepts/design/design-teams-app-ui-templates.md#left-nav): Die linke Navi-Vorlage kann helfen, wenn Ihre Registerkarte eine Gewisse Navigation erfordert.</span><span class="sxs-lookup"><span data-stu-id="e207b-138">[Left nav](../../concepts/design/design-teams-app-ui-templates.md#left-nav): The left nav template can help if your tab requires some navigation.</span></span> <span data-ttu-id="e207b-139">Im Allgemeinen sollten Sie die Tab-Navigation auf ein Minimum beschränken.</span><span class="sxs-lookup"><span data-stu-id="e207b-139">In general, you should keep tab navigation to a minimum.</span></span>

## <a name="use-an-in-meeting-tab"></a><span data-ttu-id="e207b-140">Verwenden einer Registerkarte in Besprechungen</span><span class="sxs-lookup"><span data-stu-id="e207b-140">Use an in-meeting tab</span></span>

<span data-ttu-id="e207b-141">Die Registerkarte "In-Meeting" ist eine Arbeitsfläche zum Erweitern der Zusammenarbeit während Besprechungen.</span><span class="sxs-lookup"><span data-stu-id="e207b-141">The in-meeting tab is a canvas for augmenting collaboration during meetings.</span></span> <span data-ttu-id="e207b-142">Teilnehmer können App-Inhalte in einem dedizierten Bereich außerhalb der Besprechungsphase durch freigegebene oder rollenbasierte Ansichten anzeigen und mit ihnen interagieren.</span><span class="sxs-lookup"><span data-stu-id="e207b-142">Attendees can see and interact with app content in a dedicated space outside the meeting stage through shared or role-based views.</span></span>

### <a name="use-cases"></a><span data-ttu-id="e207b-143">Anwendungsfälle</span><span class="sxs-lookup"><span data-stu-id="e207b-143">Use cases</span></span>

<span data-ttu-id="e207b-144">Personen können die Registerkarte "In-Meeting" verwenden, um:</span><span class="sxs-lookup"><span data-stu-id="e207b-144">People might use the in-meeting tab to:</span></span>

* <span data-ttu-id="e207b-145">Geben Sie detailliertes Feedback.</span><span class="sxs-lookup"><span data-stu-id="e207b-145">Provide detailed feedback.</span></span> <span data-ttu-id="e207b-146">Bewerten Sie beispielsweise einen Stellenbewerber.</span><span class="sxs-lookup"><span data-stu-id="e207b-146">For example, evaluate a job candidate.</span></span>
* <span data-ttu-id="e207b-147">Erstellen Sie eine Umfrage, Umfrage oder ein Aufgabenelement für die Besprechungsteilnehmer.</span><span class="sxs-lookup"><span data-stu-id="e207b-147">Create a poll, survey, or task item for the meeting participants.</span></span>
* <span data-ttu-id="e207b-148">Zeigt Notizen an, die für die Besprechung relevant sind.</span><span class="sxs-lookup"><span data-stu-id="e207b-148">Display notes relevant to the meeting.</span></span> <span data-ttu-id="e207b-149">Beispiel: Informationen zu einem Verkaufsleiter.</span><span class="sxs-lookup"><span data-stu-id="e207b-149">For example, information about a sales lead.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-tab.png" alt-text="Das Beispiel zeigt, wie Sie Umfrageinhalte auf einer Besprechungsregisterkarte darstellen können." border="false":::

### <a name="anatomy-in-meeting-tab"></a><span data-ttu-id="e207b-151">Anatomie: Registerkarte "In-Meeting"</span><span class="sxs-lookup"><span data-stu-id="e207b-151">Anatomy: In-meeting tab</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-anatomy.png" alt-text="Das Beispiel zeigt die strukturelle Anatomie einer Registerkarte in Besprechungen." border="false":::

|<span data-ttu-id="e207b-153">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="e207b-153">Counter</span></span>|<span data-ttu-id="e207b-154">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e207b-154">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="e207b-155">1</span><span class="sxs-lookup"><span data-stu-id="e207b-155">1</span></span>|<span data-ttu-id="e207b-156">**App-Symbol (ausgewählt):** 16-Pixel-transparentes App-Logo.</span><span class="sxs-lookup"><span data-stu-id="e207b-156">**App icon (selected)**: 16-pixel transparent app logo.</span></span>|
|<span data-ttu-id="e207b-157">2</span><span class="sxs-lookup"><span data-stu-id="e207b-157">2</span></span>|<span data-ttu-id="e207b-158">**App-Name**</span><span class="sxs-lookup"><span data-stu-id="e207b-158">**App name**</span></span>|
|<span data-ttu-id="e207b-159">3</span><span class="sxs-lookup"><span data-stu-id="e207b-159">3</span></span>|<span data-ttu-id="e207b-160">**Header**: Enthält Ihren App-Namen.</span><span class="sxs-lookup"><span data-stu-id="e207b-160">**Header**: Includes your app name.</span></span>|
|<span data-ttu-id="e207b-161">4 </span><span class="sxs-lookup"><span data-stu-id="e207b-161">4</span></span>|<span data-ttu-id="e207b-162">**Schaltfläche Schließen**: Schließt die Registerkarte ab. Verwenden Sie immer das obere rechte Nahsymbol anstelle einer Aktion in der Fußzeile.</span><span class="sxs-lookup"><span data-stu-id="e207b-162">**Close button**: Dismisses the tab. Always use the upper-right close icon instead of an action in the footer.</span></span>|
|<span data-ttu-id="e207b-163">5 </span><span class="sxs-lookup"><span data-stu-id="e207b-163">5</span></span>|<span data-ttu-id="e207b-164">**Benachrichtigungsleiste**: Fehlerwarnungen werden direkt unter der Kopfzeile angezeigt und drücken den iframe-Inhalt um 20 Pixel nach unten.</span><span class="sxs-lookup"><span data-stu-id="e207b-164">**Notification bar**: Error alerts display directly below the header and push the iframe content down by 20 pixels.</span></span>|
|<span data-ttu-id="e207b-165">6 </span><span class="sxs-lookup"><span data-stu-id="e207b-165">6</span></span>|<span data-ttu-id="e207b-166">**iframe**: Zeigt Ihre App-Inhalte an.</span><span class="sxs-lookup"><span data-stu-id="e207b-166">**iframe**: Displays your app content.</span></span>|

### <a name="spacing"></a><span data-ttu-id="e207b-167">Abstand</span><span class="sxs-lookup"><span data-stu-id="e207b-167">Spacing</span></span>

<span data-ttu-id="e207b-168">Optimieren Sie Ihre Registerkarte in Meetings, um Edge-to-Edge innerhalb des 280 Pixel breiten iframe-Bereichs anzupassen.</span><span class="sxs-lookup"><span data-stu-id="e207b-168">Optimize your in-meeting tab to fit edge-to-edge within the 280 pixel-wide iframe area.</span></span> <span data-ttu-id="e207b-169">Auf der linken und rechten Seite des iframes und zwischen dem Tab-Header befinden sich 20 Pixel Auffüllung.</span><span class="sxs-lookup"><span data-stu-id="e207b-169">There are 20 pixels of padding on the left and right sides of the iframe and between the tab header.</span></span> <span data-ttu-id="e207b-170">Der iframe ist voll bluten bis zum unteren Rand der Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="e207b-170">The iframe is full bleed to the bottom of the tab.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-spacing.png" alt-text="Das Beispiel zeigt in-Meeting-Tababstanddimensionen." border="false":::

### <a name="scrolling"></a><span data-ttu-id="e207b-172">Scrollen</span><span class="sxs-lookup"><span data-stu-id="e207b-172">Scrolling</span></span>

<span data-ttu-id="e207b-173">Iframe-Inhalte sollten vertikal scrollen.</span><span class="sxs-lookup"><span data-stu-id="e207b-173">Iframe contents should scroll vertically.</span></span> <span data-ttu-id="e207b-174">Sie können nur den Inhalt sehen, zu dem Sie gescrollt haben (nichts über oder unter).</span><span class="sxs-lookup"><span data-stu-id="e207b-174">You can only see the content you've scrolled to (nothing above or below).</span></span> <span data-ttu-id="e207b-175">Die Bildlaufleiste ist Teil des iframe-Inhalts.</span><span class="sxs-lookup"><span data-stu-id="e207b-175">The scrollbar is part of the iframe content.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-scrolling.png" alt-text="Das Beispiel zeigt, wie die Registerkarte in Besprechung scrollt." border="false":::

### <a name="navigation"></a><span data-ttu-id="e207b-177">Navigation</span><span class="sxs-lookup"><span data-stu-id="e207b-177">Navigation</span></span>

<span data-ttu-id="e207b-178">Für Szenarien mit Navigationsebenen oder schwerem Inhalt wird empfohlen, Benutzern das Navigieren zu einer sekundären Ebene zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="e207b-178">For scenarios with navigation layers or heavy content, we recommend allowing users to navigate to a secondary layer.</span></span> <span data-ttu-id="e207b-179">Benutzer müssen in der Lage sein, zur vorherigen Ebene zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="e207b-179">Users must be able to go back to the previous layer.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav.png" alt-text="Beispiel zeigt in Der Besprechungsnavigation." border="false":::

## <a name="use-an-in-meeting-dialog"></a><span data-ttu-id="e207b-181">Verwenden eines Dialogfelds in der Besprechung</span><span class="sxs-lookup"><span data-stu-id="e207b-181">Use an in-meeting dialog</span></span>

<span data-ttu-id="e207b-182">In-Meeting-Dialoge werden auf der Teams Besprechungsphase angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e207b-182">In-meeting dialogs display on the Teams meeting stage.</span></span> <span data-ttu-id="e207b-183">Sie erfordern die Aufmerksamkeit, Bestätigung oder Interaktion eines Benutzers, sind jedoch subtil und unterbrechen die Besprechung nicht.</span><span class="sxs-lookup"><span data-stu-id="e207b-183">They require a user's attention, confirmation, or interaction but are subtle and don't interrupt the meeting.</span></span> <span data-ttu-id="e207b-184">Sie sollten diese sparsam und für Szenarien verwenden, die licht- und aufgabenorientiert sind.</span><span class="sxs-lookup"><span data-stu-id="e207b-184">You should use these sparingly and for scenarios that are light and task oriented.</span></span>

### <a name="use-cases"></a><span data-ttu-id="e207b-185">Anwendungsfälle</span><span class="sxs-lookup"><span data-stu-id="e207b-185">Use cases</span></span>

<span data-ttu-id="e207b-186">In Besprechungsdialogen werden von einem Benutzer (z. B. dem Besprechungsorganisator) ausgelöst, der teilnehmer möglicherweise wie folgt:</span><span class="sxs-lookup"><span data-stu-id="e207b-186">In-meeting dialogs are triggered by a user (such as the meeting organizer) who might want participants to:</span></span>

* <span data-ttu-id="e207b-187">Kurzes Feedback geben</span><span class="sxs-lookup"><span data-stu-id="e207b-187">Provide brief feedback</span></span>
* <span data-ttu-id="e207b-188">Nehmen Sie an einer kurzen Umfrage oder Umfrage teil</span><span class="sxs-lookup"><span data-stu-id="e207b-188">Take a short survey or poll</span></span>
* <span data-ttu-id="e207b-189">Bewillisch einreichen</span><span class="sxs-lookup"><span data-stu-id="e207b-189">Submit approvals</span></span>
* <span data-ttu-id="e207b-190">Erhalten Sie Erinnerungen</span><span class="sxs-lookup"><span data-stu-id="e207b-190">Get reminders</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-dialog.png" alt-text="Das Beispiel zeigt, wie Sie ein Dialogfeld in der Besprechung verwenden können." border="false":::

### <a name="anatomy-in-meeting-dialog"></a><span data-ttu-id="e207b-192">Anatomie: Dialog im Gespräch</span><span class="sxs-lookup"><span data-stu-id="e207b-192">Anatomy: In-meeting dialog</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-anatomy.png" alt-text="Das Beispiel zeigt die strukturelle Anatomie eines Dialogfelds im Besprechungsdialog." border="false":::

|<span data-ttu-id="e207b-194">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="e207b-194">Counter</span></span>|<span data-ttu-id="e207b-195">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e207b-195">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="e207b-196">1</span><span class="sxs-lookup"><span data-stu-id="e207b-196">1</span></span>|<span data-ttu-id="e207b-197">**Kopfzeile**: Enthält App-Symbol, Name, Aktionszeichenfolge und Schließen-Symbol.</span><span class="sxs-lookup"><span data-stu-id="e207b-197">**Header**: Includes app icon, name, action string, and close icon.</span></span>|
|<span data-ttu-id="e207b-198">2</span><span class="sxs-lookup"><span data-stu-id="e207b-198">2</span></span>|<span data-ttu-id="e207b-199">**iframe**: Zeigt Ihre App-Inhalte an.</span><span class="sxs-lookup"><span data-stu-id="e207b-199">**iframe**: Displays your app content.</span></span>|

### <a name="anatomy-in-meeting-dialog-header"></a><span data-ttu-id="e207b-200">Anatomie: Dialogkopf im Besprechungsgespräch</span><span class="sxs-lookup"><span data-stu-id="e207b-200">Anatomy: In-meeting dialog header</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-header-anatomy.png" alt-text="Das Beispiel zeigt die strukturelle Anatomie eines Dialogheaders in Besprechungen." border="false":::

<span data-ttu-id="e207b-202">Es gibt zwei Headervarianten.</span><span class="sxs-lookup"><span data-stu-id="e207b-202">There are two header variants.</span></span> <span data-ttu-id="e207b-203">Wenn möglich, verwenden Sie die Variante mit dem Avatar, um zu verstärken, dass der Dialog von einer Person kommt.</span><span class="sxs-lookup"><span data-stu-id="e207b-203">When possible, use the variant with the avatar to reinforce that the dialog is coming from a person.</span></span>

|<span data-ttu-id="e207b-204">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="e207b-204">Counter</span></span>|<span data-ttu-id="e207b-205">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e207b-205">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="e207b-206">1</span><span class="sxs-lookup"><span data-stu-id="e207b-206">1</span></span>|<span data-ttu-id="e207b-207">**Avatar**: Person, die den Dialog im Besprechungsdialog initiiert.</span><span class="sxs-lookup"><span data-stu-id="e207b-207">**Avatar**: Person who initiates the in-meeting dialog.</span></span>|
|<span data-ttu-id="e207b-208">2</span><span class="sxs-lookup"><span data-stu-id="e207b-208">2</span></span>|<span data-ttu-id="e207b-209">**App-Symbol**</span><span class="sxs-lookup"><span data-stu-id="e207b-209">**App icon**</span></span>|
|<span data-ttu-id="e207b-210">3</span><span class="sxs-lookup"><span data-stu-id="e207b-210">3</span></span>|<span data-ttu-id="e207b-211">**App-Name**</span><span class="sxs-lookup"><span data-stu-id="e207b-211">**App name**</span></span>|
|<span data-ttu-id="e207b-212">4 </span><span class="sxs-lookup"><span data-stu-id="e207b-212">4</span></span>|<span data-ttu-id="e207b-213">**Schaltfläche Schließen**: Schließt das Dialogfeld ab.</span><span class="sxs-lookup"><span data-stu-id="e207b-213">**Close button**: Dismisses the dialog.</span></span>|
|<span data-ttu-id="e207b-214">5 </span><span class="sxs-lookup"><span data-stu-id="e207b-214">5</span></span>|<span data-ttu-id="e207b-215">**Aktionszeichenfolge**: Beschreibt in der Regel, wer das Dialogfeld initiiert hat.</span><span class="sxs-lookup"><span data-stu-id="e207b-215">**Action string**: Typically describes who initiated the dialog.</span></span>|

### <a name="responsive-behavior"></a><span data-ttu-id="e207b-216">Dynamisches Verhalten</span><span class="sxs-lookup"><span data-stu-id="e207b-216">Responsive behavior</span></span>

<span data-ttu-id="e207b-217">In Besprechungsdialogen kann in der Größe variieren, um verschiedene Szenarien zu berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="e207b-217">In-meeting dialogs can vary in size to account for different scenarios.</span></span> <span data-ttu-id="e207b-218">Achten Sie darauf, die Polsterung und die Komponentengrößen beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="e207b-218">Make sure to maintain padding and component sizes.</span></span>

* <span data-ttu-id="e207b-219">**Breite**: Sie können die Breite des iframes des Dialogfelds an einer beliebigen Stelle innerhalb des unterstützten Größenbereichs angeben.</span><span class="sxs-lookup"><span data-stu-id="e207b-219">**Width**: You can specify the width of the dialog's iframe anywhere within the supported size range.</span></span>
* <span data-ttu-id="e207b-220">**Höhe**: Sie können die Höhe des iframes des Dialogfelds an einer beliebigen Stelle innerhalb des unterstützten Größenbereichs angeben.</span><span class="sxs-lookup"><span data-stu-id="e207b-220">**Height**: You can specify the height of the dialog's iframe anywhere within the supported size range.</span></span> <span data-ttu-id="e207b-221">Sie können Benutzern auch erlauben, vertikal zu scrollen, wenn Ihr App-Inhalt die maximale Höhe überschreitet.</span><span class="sxs-lookup"><span data-stu-id="e207b-221">You also can allow users to scroll vertically if your app content exceeds the maximum height.</span></span>

<span data-ttu-id="e207b-222">Geben Sie zum Implementieren die Breite und Höhe mithilfe des [`externalResourceUrl`](~/apps-in-teams-meetings/create-apps-for-teams-meetings.md#notificationsignal-api) Schlüssels an.</span><span class="sxs-lookup"><span data-stu-id="e207b-222">To implement, specify the width and height using the [`externalResourceUrl`](~/apps-in-teams-meetings/create-apps-for-teams-meetings.md#notificationsignal-api) key.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-responsive.png" alt-text="Das Beispiel zeigt das Dialogfeld in der Besprechung. Breite: Min--280 Pixel (248 Pixel iframe). Max--460 Pixel (428 Pixel iframe). Höhe: 300 Pixel (iframe)." border="false":::

## <a name="after-a-meeting"></a><span data-ttu-id="e207b-224">Nach einem Meeting</span><span class="sxs-lookup"><span data-stu-id="e207b-224">After a meeting</span></span>

<span data-ttu-id="e207b-225">Sie können nach dem Ende zu einer Besprechung zurückkehren und App-Inhalte anzeigen.</span><span class="sxs-lookup"><span data-stu-id="e207b-225">You can go back to a meeting after it ends and view app content.</span></span> <span data-ttu-id="e207b-226">In diesem Beispiel kann sich der Besprechungsorganisator die Umfrageergebnisse auf der **Registerkarte Contoso** ansehen. (Hinweis: Vom Entwurfsstandpunkt aus gibt es keinen Unterschied zwischen einer Registerkarte vor und nach dem Meeting.)</span><span class="sxs-lookup"><span data-stu-id="e207b-226">In this example, the meeting organizer can look at poll results in the **Contoso** tab. (Note: From a design standpoint, there's no difference between a the pre- and post-meeting tab experience.)</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/post-meeting-experience.png" alt-text="Die Beispielabbildung zeigt eine Registerkarte nach dem Meeting." border="false":::

## <a name="best-practices"></a><span data-ttu-id="e207b-228">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="e207b-228">Best practices</span></span>

<span data-ttu-id="e207b-229">Verwenden Sie diese Empfehlungen, um eine hochwertige App-Erfahrung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="e207b-229">Use these recommendations to create a quality app experience.</span></span>

### <a name="interactions"></a><span data-ttu-id="e207b-230">Interaktionen</span><span class="sxs-lookup"><span data-stu-id="e207b-230">Interactions</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-do.png" alt-text="Beispiel, das zeigt, wie die Anzahl der Interaktionen begrenzt wird." border="false":::

#### <a name="do-limit-the-number-of-interactions"></a><span data-ttu-id="e207b-232">Tun: Beschränken sie die Anzahl der Interaktionen</span><span class="sxs-lookup"><span data-stu-id="e207b-232">Do: Limit the number of interactions</span></span>

<span data-ttu-id="e207b-233">Entfernen Sie bei Besprechungsdialogen unnötige Inhalte, die Benutzern nicht dabei helfen, schnell etwas zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="e207b-233">For in-meeting dialogs, remove unnecessary content that doesn't help users accomplish something quickly.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-dont.png" alt-text="Beispiel, das zeigt, wie keine unnötigen Elemente eingeführt werden." border="false":::

#### <a name="dont-introduce-unnecessary-elements"></a><span data-ttu-id="e207b-235">Nicht: Unnötige Elemente einführen</span><span class="sxs-lookup"><span data-stu-id="e207b-235">Don't: Introduce unnecessary elements</span></span>

<span data-ttu-id="e207b-236">Ein einzelner Dialog mit mehreren Interaktionen kann vom Aufruf ablenken.</span><span class="sxs-lookup"><span data-stu-id="e207b-236">A single in-meeting dialog with multiple interactions can distract from the call.</span></span>

   :::column-end:::
:::row-end:::

### <a name="layout"></a><span data-ttu-id="e207b-237">Layout</span><span class="sxs-lookup"><span data-stu-id="e207b-237">Layout</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-do.png" alt-text="Beispiel, das zeigt, wie Sie ein einspaltiges Dialogfeldlayout verwenden sollten." border="false":::

#### <a name="do-use-a-single-column-dialog-layout"></a><span data-ttu-id="e207b-239">Tun: Verwenden eines einspaltigen Dialoglayouts</span><span class="sxs-lookup"><span data-stu-id="e207b-239">Do: Use a single-column dialog layout</span></span>

<span data-ttu-id="e207b-240">Da die Dialoge im Mittelpunkt der Besprechungsphase stehen, sollte die Aufgabenvervollständigung schnell und einfach sein, um Benutzerfrustrationen zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="e207b-240">Since the dialogs are at the center of the meeting stage, task completion should be fast and simple to avoid user frustration.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-dont.png" alt-text="Beispiel, das zeigt, dass Sie den Raum einer Besprechungserweiterung nicht überladen sollten." border="false":::

#### <a name="dont-clutter-the-space"></a><span data-ttu-id="e207b-242">Nicht: Den Raum überladen</span><span class="sxs-lookup"><span data-stu-id="e207b-242">Don't: Clutter the space</span></span>

<span data-ttu-id="e207b-243">Dichte oder zu strukturierte Inhalte können ablenkend und überwältigend sein, insbesondere während eines Meetings.</span><span class="sxs-lookup"><span data-stu-id="e207b-243">Dense or overly structured content can be distracting and overwhelming, especially during a meeting.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-do.png" alt-text="Beispiel für ein einspaltiges Registerkartenlayout." border="false":::

#### <a name="do-use-a-single-column-tab-layout"></a><span data-ttu-id="e207b-245">Tun: Verwenden eines einspaltigen Registerkartenlayouts</span><span class="sxs-lookup"><span data-stu-id="e207b-245">Do: Use a single-column tab layout</span></span>

<span data-ttu-id="e207b-246">Angesichts der engen Natur der Registerkarte "In-Meeting" wird dringend empfohlen, den Inhalt in einer einzelnen Spalte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="e207b-246">Given the in-meeting tab's narrow nature, we strongly recommend displaying the contents in a single column.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-dont.png" alt-text="Beispiel, das eine Registerkarte mit mehreren Spalten anzeigt." border="false":::

#### <a name="dont-use-multiple-columns"></a><span data-ttu-id="e207b-248">Nicht: Verwenden Sie mehrere Spalten</span><span class="sxs-lookup"><span data-stu-id="e207b-248">Don't: Use multiple columns</span></span>

<span data-ttu-id="e207b-249">Aufgrund des begrenzten Platzes auf der Registerkarte "In-Meeting" werden Layouts mit mehr als einer Spalte nicht empfohlen.</span><span class="sxs-lookup"><span data-stu-id="e207b-249">Due to the limited space of the in-meeting tab, layouts with more than one column aren’t recommended.</span></span>

   :::column-end:::
:::row-end:::

### <a name="controls"></a><span data-ttu-id="e207b-250">Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="e207b-250">Controls</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-do.png" alt-text="Beispiel, das zeigt, wie primäre Steuerelemente rechts ausgerichtet werden." border="false":::

#### <a name="do-right-align-the-primary-action"></a><span data-ttu-id="e207b-252">Tun: Rechts richten Sie die primäre Aktion aus</span><span class="sxs-lookup"><span data-stu-id="e207b-252">Do: Right align the primary action</span></span>

<span data-ttu-id="e207b-253">Wir empfehlen, die visuell schwerste Aktion an der richtigen Stelle zu positionieren.</span><span class="sxs-lookup"><span data-stu-id="e207b-253">We recommend positioning the most visually heavy action to the right-most location.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-dont.png" alt-text="Beispiel, das zeigt, wie Sie primäre Steuerelemente nicht links ausrichten sollten." border="false":::

#### <a name="dont-left-or-center-align-actions"></a><span data-ttu-id="e207b-255">Nicht: Aktionen nach links oder in der Mitte ausrichten</span><span class="sxs-lookup"><span data-stu-id="e207b-255">Don't: Left or center align actions</span></span>

<span data-ttu-id="e207b-256">Dies weicht vom Standardmuster Teams für die Steuerplatzierung in einem Dialog feldieren und kann mit einem Dialog feldieren.</span><span class="sxs-lookup"><span data-stu-id="e207b-256">This deviates from the standard Teams pattern for control placement in a dialog and may conflict with a dialog behind the top one.</span></span>

   :::column-end:::
:::row-end:::

### <a name="scroll"></a><span data-ttu-id="e207b-257">Bildlauf</span><span class="sxs-lookup"><span data-stu-id="e207b-257">Scroll</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-do.png" alt-text="Beispiel für vertikales Scrollen auf einer Besprechungsregisterkarte." border="false":::

#### <a name="do-scroll-vertically"></a><span data-ttu-id="e207b-259">Tun: Vertikal scrollen</span><span class="sxs-lookup"><span data-stu-id="e207b-259">Do: Scroll vertically</span></span>

<span data-ttu-id="e207b-260">Benutzer erwarten vertikales Scrollen in Teams (und anderswo).</span><span class="sxs-lookup"><span data-stu-id="e207b-260">Users expect vertical scrolling in Teams (and elsewhere).</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-dont.png" alt-text="Beispiel für horizontales Scrollen in einer Besprechungsregisterkarte." border="false":::

#### <a name="dont-scroll-horizontally"></a><span data-ttu-id="e207b-262">Nicht: Horizontal scrollen</span><span class="sxs-lookup"><span data-stu-id="e207b-262">Don't: Scroll horizontally</span></span>

<span data-ttu-id="e207b-263">Horizontales Scrollen ist kein erwartetes Verhalten in Teams.</span><span class="sxs-lookup"><span data-stu-id="e207b-263">Horizontal scrolling isn’t an expected behavior in Teams.</span></span> <span data-ttu-id="e207b-264">Andere Leinwände in der Besprechungsumgebung scrollen vertikal.</span><span class="sxs-lookup"><span data-stu-id="e207b-264">Other canvases in the meeting environment scroll vertically.</span></span>

   :::column-end:::
:::row-end:::

### <a name="workflows"></a><span data-ttu-id="e207b-265">Workflows</span><span class="sxs-lookup"><span data-stu-id="e207b-265">Workflows</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-workflow-do.png" alt-text="Beispiel für das Zeigen eines komplexen Szenarios auf einer Registerkarte in Besprechungen." border="false":::

#### <a name="do-surface-complex-scenarios-in-the-in-meeting-tab"></a><span data-ttu-id="e207b-267">Tun: Komplexe Szenarien auf der Registerkarte "In-Meeting" anzeigen</span><span class="sxs-lookup"><span data-stu-id="e207b-267">Do: Surface complex scenarios in the in-meeting tab</span></span>

<span data-ttu-id="e207b-268">Wenn Ihre App mehrere Aufgaben enthält, wird dringend empfohlen, eine Registerkarte in Besprechungen mit einem einspaltigen Layout zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="e207b-268">If your app includes multiple tasks, we strongly recommend using an in-meeting tab with a single-column layout.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-workflow-dont.png" alt-text="Beispiel für komplexe Szenarien in einem Besprechungsdialog." border="false":::

#### <a name="dont-make-in-meeting-dialogs-complex"></a><span data-ttu-id="e207b-270">Nicht: In-Meeting-Dialoge komplex machen</span><span class="sxs-lookup"><span data-stu-id="e207b-270">Don't: Make in-meeting dialogs complex</span></span>

<span data-ttu-id="e207b-271">In Besprechungsdialogen sind für kurze Interaktionen vorgesehen.</span><span class="sxs-lookup"><span data-stu-id="e207b-271">In-meeting dialogs are intended for brief interactions.</span></span>

   :::column-end:::
:::row-end:::

### <a name="theming"></a><span data-ttu-id="e207b-272">Designs</span><span class="sxs-lookup"><span data-stu-id="e207b-272">Theming</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-do.png" alt-text="Beispiel für eine Besprechungserweiterung mit dem dunklen Thema." border="false":::

#### <a name="do-use-teams-color-tokens"></a><span data-ttu-id="e207b-274">Tun: Verwenden Teams Farbtoken</span><span class="sxs-lookup"><span data-stu-id="e207b-274">Do: Use Teams color tokens</span></span>

<span data-ttu-id="e207b-275">Teams Meetings sind für den dunklen Modus optimiert, um visuelles und kognitives Rauschen zu reduzieren, sodass sich Benutzer auf die Diskussion und freigegebene Inhalte konzentrieren können.</span><span class="sxs-lookup"><span data-stu-id="e207b-275">Teams meetings are optimized for dark mode to help reduce visual and cognitive noise so users can focus on the discussion and shared content.</span></span> <span data-ttu-id="e207b-276">Erfahren Sie mehr über die Verwendung von <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">Farbtoken (Fluent UI)</a>.</span><span class="sxs-lookup"><span data-stu-id="e207b-276">Learn about using <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">color tokens (Fluent UI)</a>.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-dont.png" alt-text="Beispiel für eine Besprechungserweiterung mit einem Standarddesign (Licht)." border="false":::

#### <a name="dont-hard-code-hex-values"></a><span data-ttu-id="e207b-278">Nicht: Hartcode-Hex-Werte</span><span class="sxs-lookup"><span data-stu-id="e207b-278">Don't: Hard code hex values</span></span>

<span data-ttu-id="e207b-279">Wenn Sie keine Teams Farbtoken verwenden, sind Ihre Designs weniger skalierbar und nehmen mehr Zeit in Anspruch.</span><span class="sxs-lookup"><span data-stu-id="e207b-279">If you don’t use Teams color tokens, your designs will be less scalable and take more time to manage.</span></span>

   :::column-end:::
:::row-end:::

### <a name="navigation"></a><span data-ttu-id="e207b-280">Navigation</span><span class="sxs-lookup"><span data-stu-id="e207b-280">Navigation</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-do.png" alt-text="Beispiel für eine Besprechungserweiterung mit einer Zurück-Schaltfläche." border="false":::

#### <a name="do-have-a-back-button"></a><span data-ttu-id="e207b-282">Do: Haben Sie eine Zurück-Taste</span><span class="sxs-lookup"><span data-stu-id="e207b-282">Do: Have a back button</span></span>

<span data-ttu-id="e207b-283">Wenn Sie mehr als eine Navigationsebene auf einer Registerkarte in Besprechungen haben, müssen Benutzer in der Lage sein, zu ihren vorherigen Ansichten zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="e207b-283">If you have more than one layer of navigation in an in-meeting tab, users must be able to go back to their previous views.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-dont.png" alt-text="Beispiel für eine Besprechungserweiterung mit zwei Abweisungsschaltflächen." border="false":::

#### <a name="dont-include-another-dismiss-button"></a><span data-ttu-id="e207b-285">Nicht: Fügen Sie eine weitere Abweisungsschaltfläche ein</span><span class="sxs-lookup"><span data-stu-id="e207b-285">Don't: Include another dismiss button</span></span>

<span data-ttu-id="e207b-286">Das Bereitstellen einer Option zum Schließen von Besprechungsregisterkarteninhalten kann Probleme verursachen, da sich bereits eine Schaltfläche im Header befindet, um die Registerkarte in Besprechungen selbst zu schließen.</span><span class="sxs-lookup"><span data-stu-id="e207b-286">Providing an option to close in-meeting tab content may cause issues since there’s already a button in the header to dismiss the in-meeting tab itself.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-caution.png" alt-text="Beispiel für Modals (oder Aufgabenmodule) auf einer Registerkarte in Besprechungen." border="false":::

#### <a name="caution-avoid-modals-within-the-in-meeting-tab"></a><span data-ttu-id="e207b-288">Achtung: Vermeiden Sie Modals innerhalb der Registerkarte in Besprechungen</span><span class="sxs-lookup"><span data-stu-id="e207b-288">Caution: Avoid modals within the in-meeting tab</span></span>

<span data-ttu-id="e207b-289">Modals (auch als Taskmodule bezeichnet) auf der bereits schmalen Registerkarte in Besprechungen können den Inhalt umschließen und verschleiern.</span><span class="sxs-lookup"><span data-stu-id="e207b-289">Modals (also known as task modules) in the already narrow in-meeting tab might wrap and obscure the content.</span></span>

   :::column-end:::
:::row-end:::
