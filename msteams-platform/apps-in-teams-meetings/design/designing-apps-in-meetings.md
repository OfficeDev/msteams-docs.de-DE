---
title: Entwerfen Ihrer Besprechungs Erweiterung
author: heath-hamilton
description: Hier erfahren Sie, wie Sie apps in Microsoft Teams-Besprechungen entwerfen und das Microsoft Teams UI Kit abrufen.
ms.author: lajanuar
ms.topic: conceptual
ms.openlocfilehash: 3d18895626d5f2846d10e7145a622834d82b2e98
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "49606132"
---
# <a name="designing-your-microsoft-teams-meeting-extension"></a><span data-ttu-id="ccd72-103">Entwerfen Ihrer Microsoft Teams-Besprechungs Erweiterung</span><span class="sxs-lookup"><span data-stu-id="ccd72-103">Designing your Microsoft Teams meeting extension</span></span>

<span data-ttu-id="ccd72-104">Sie können Apps erstellen, um Besprechungen produktiver zu gestalten.</span><span class="sxs-lookup"><span data-stu-id="ccd72-104">You can create apps to make meetings more productive.</span></span> <span data-ttu-id="ccd72-105">Bitten Sie beispielsweise die Personen, während eines Anrufs eine Umfrage abzuschließen oder eine schnell Erinnerung zu senden, die den Ablauf der Besprechung nicht unterbricht.</span><span class="sxs-lookup"><span data-stu-id="ccd72-105">For example, ask people to complete a survey during a call or send a quick reminder that doesn’t interrupt the flow of the meeting.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="ccd72-106">Microsoft Teams-UI-Kit</span><span class="sxs-lookup"><span data-stu-id="ccd72-106">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="ccd72-107">Ausführlichere Entwurfsrichtlinien, einschließlich der Elemente, die Sie nach Bedarf abrufen und ändern können, finden Sie im Microsoft Teams UI Kit.</span><span class="sxs-lookup"><span data-stu-id="ccd72-107">You can find more comprehensive design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ccd72-108">Abrufen des Microsoft Teams UI Kit (Figma)</span><span class="sxs-lookup"><span data-stu-id="ccd72-108">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-meeting-extension"></a><span data-ttu-id="ccd72-109">Hinzufügen einer Besprechungs Erweiterung</span><span class="sxs-lookup"><span data-stu-id="ccd72-109">Add a meeting extension</span></span>

<span data-ttu-id="ccd72-110">Sie können vor und während Besprechungen eine Besprechungs Erweiterung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ccd72-110">You can add a meeting extension before and during meetings.</span></span> <span data-ttu-id="ccd72-111">Sie können auch eine APP für eine bestimmte Besprechung direkt aus dem Microsoft Teams Store (AppSource).</span><span class="sxs-lookup"><span data-stu-id="ccd72-111">You also can an app for a specific meeting directly from the Teams store (AppSource).</span></span>

### <a name="add-before-a-meeting"></a><span data-ttu-id="ccd72-112">Vor einer Besprechung hinzufügen</span><span class="sxs-lookup"><span data-stu-id="ccd72-112">Add before a meeting</span></span>

<span data-ttu-id="ccd72-113">Wählen Sie vor einer Besprechung die Option **Add a Tab +** aus, um das App-Flyout zu öffnen und für Besprechungen optimierte apps zu finden.</span><span class="sxs-lookup"><span data-stu-id="ccd72-113">Before a meeting, the meeting details select **Add a tab +** to open the app flyout and find apps optimized for meetings.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/add-before-meeting.png" alt-text="Beispiel zeigt, wie eine Besprechungs Erweiterung vor einer Besprechung hinzugefügt wird." border="false":::

### <a name="add-during-a-meeting"></a><span data-ttu-id="ccd72-115">Während einer Besprechung hinzufügen</span><span class="sxs-lookup"><span data-stu-id="ccd72-115">Add during a meeting</span></span>

Wählen Sie in einer Besprechung **Weitere** :::image type="icon" source="../../assets/icons/teams-client-more.png":::  >  **app hinzufügen** aus, und wählen Sie die gewünschte App aus.

:::image type="content" source="../../assets/images/apps-in-meetings/add-during-meeting.png" alt-text="In diesem Beispiel wird gezeigt, wie während einer Besprechung eine Besprechungs Erweiterung hinzugefügt wird." border="false":::

## <a name="before-a-meeting"></a><span data-ttu-id="ccd72-118">Vor einer Besprechung</span><span class="sxs-lookup"><span data-stu-id="ccd72-118">Before a meeting</span></span>

<span data-ttu-id="ccd72-119">Sie können vor Ihrer Besprechung Inhalte auf der Registerkarte hinzufügen. Das folgende Beispiel zeigt eine Entwurfs Frage für Umfragen, die von Personen während des Anrufs beantwortet werden.</span><span class="sxs-lookup"><span data-stu-id="ccd72-119">Prior to your meeting, you can add content in the tab. The following example shows a draft survey question that people will answer during the call.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/before-meeting-tab.png" alt-text="Beispiel zeigt, wie der Inhalt der Besprechungsdetails vor einem Anruf App-Inhalte enthält." border="false":::

### <a name="anatomy-meeting-tab-before-and-after-meetings"></a><span data-ttu-id="ccd72-121">Anatomie: Registerkarte "Besprechung" (vor und nach Besprechungen)</span><span class="sxs-lookup"><span data-stu-id="ccd72-121">Anatomy: Meeting tab (before and after meetings)</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/meeting-details-tab-anatomy.png" alt-text="Beispiel zeigt die strukturelle Anatomie einer Besprechungs Registerkarte vor und nach einer Besprechung." border="false":::

|<span data-ttu-id="ccd72-123">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="ccd72-123">Counter</span></span>|<span data-ttu-id="ccd72-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ccd72-124">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="ccd72-125">1</span><span class="sxs-lookup"><span data-stu-id="ccd72-125">1</span></span>|<span data-ttu-id="ccd72-126">**Tab Name**: Navigations Bezeichnung für die Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="ccd72-126">**Tab name**: Navigation label for your tab.</span></span>|
|<span data-ttu-id="ccd72-127">2 </span><span class="sxs-lookup"><span data-stu-id="ccd72-127">2</span></span>|<span data-ttu-id="ccd72-128">**Registerkarten Überlauf**: Öffnet Registerkarten Aktionen wie umbenennen und entfernen.</span><span class="sxs-lookup"><span data-stu-id="ccd72-128">**Tab overflow**: Opens tab actions, such as rename and remove.</span></span>|
|<span data-ttu-id="ccd72-129">3 </span><span class="sxs-lookup"><span data-stu-id="ccd72-129">3</span></span>|<span data-ttu-id="ccd72-130">**iframe**: zeigt den App-Inhalt an.</span><span class="sxs-lookup"><span data-stu-id="ccd72-130">**iframe**: Displays your app content.</span></span>|

### <a name="designing-with-ui-templates"></a><span data-ttu-id="ccd72-131">Entwerfen mit Benutzeroberflächenvorlagen</span><span class="sxs-lookup"><span data-stu-id="ccd72-131">Designing with UI templates</span></span>

<span data-ttu-id="ccd72-132">Verwenden Sie eine der folgenden Teams-Benutzeroberflächenvorlagen, um die Gestaltung ihrer Besprechungs Registerkarte zu unterstützen:</span><span class="sxs-lookup"><span data-stu-id="ccd72-132">Use one of the following Teams UI templates to help design your meeting tab:</span></span>

* <span data-ttu-id="ccd72-133">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem scannable-Format anzeigen und Benutzern das Ausführen von Aktionen für eine gesamte Liste oder einzelne Elemente gestatten.</span><span class="sxs-lookup"><span data-stu-id="ccd72-133">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="ccd72-134">[Task Board](../../concepts/design/design-teams-app-ui-templates.md#task-board): ein Aufgaben Gremium, das manchmal als Kanban-Board oder als Swim Lanes bezeichnet wird, ist eine Sammlung von Karten, die häufig zum Nachverfolgen des Status von Arbeitsaufgaben oder Tickets verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ccd72-134">[Task board](../../concepts/design/design-teams-app-ui-templates.md#task-board): A task board, sometimes called a kanban board or swim lanes, is a collection of cards often used to track the status of work items or tickets.</span></span>
* <span data-ttu-id="ccd72-135">[Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): ein Dashboard ist eine Leinwand mit mehreren Karten, die eine Übersicht über Daten oder Inhalte bieten.</span><span class="sxs-lookup"><span data-stu-id="ccd72-135">[Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): A dashboard is a canvas containing multiple cards that provide an overview of data or content.</span></span>
* <span data-ttu-id="ccd72-136">[Formular](../../concepts/design/design-teams-app-ui-templates.md#form): Formulare dienen zum Sammeln, validieren und Übermitteln von Benutzereingaben in strukturierter Form.</span><span class="sxs-lookup"><span data-stu-id="ccd72-136">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="ccd72-137">[Leer State](../../concepts/design/design-teams-app-ui-templates.md#empty-state): die leere Statusvorlage kann für viele Szenarien verwendet werden, einschließlich Anmeldung, Erstausführung, Fehlermeldungen und mehr.</span><span class="sxs-lookup"><span data-stu-id="ccd72-137">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>
* <span data-ttu-id="ccd72-138">[Linker NAV](../../concepts/design/design-teams-app-ui-templates.md#left-nav): die linke Navigationsvorlage kann hilfreich sein, wenn Ihre Registerkarte eine Navigation erfordert.</span><span class="sxs-lookup"><span data-stu-id="ccd72-138">[Left nav](../../concepts/design/design-teams-app-ui-templates.md#left-nav): The left nav template can help if your tab requires some navigation.</span></span> <span data-ttu-id="ccd72-139">Im Allgemeinen sollten Sie die Registerkartennavigation auf ein Minimum beschränken.</span><span class="sxs-lookup"><span data-stu-id="ccd72-139">In general, you should keep tab navigation to a minimum.</span></span>

## <a name="use-an-in-meeting-tab"></a><span data-ttu-id="ccd72-140">Verwenden einer in-Meeting-Registerkarte</span><span class="sxs-lookup"><span data-stu-id="ccd72-140">Use an in-meeting tab</span></span>

<span data-ttu-id="ccd72-141">Die Registerkarte in-Meeting ist eine Arbeitsfläche zum Erweitern der Zusammenarbeit während Besprechungen.</span><span class="sxs-lookup"><span data-stu-id="ccd72-141">The in-meeting tab is a canvas for augmenting collaboration during meetings.</span></span> <span data-ttu-id="ccd72-142">Teilnehmer können App-Inhalte in einem dedizierten Bereich außerhalb der Besprechungs Phase über freigegebene oder rollenbasierte Ansichten anzeigen und mit ihnen interagieren.</span><span class="sxs-lookup"><span data-stu-id="ccd72-142">Attendees can see and interact with app content in a dedicated space outside the meeting stage through shared or role-based views.</span></span>

### <a name="use-cases"></a><span data-ttu-id="ccd72-143">Anwendungsfälle</span><span class="sxs-lookup"><span data-stu-id="ccd72-143">Use cases</span></span>

<span data-ttu-id="ccd72-144">Die Registerkarte "in-Meeting" wird von den Benutzern möglicherweise verwendet:</span><span class="sxs-lookup"><span data-stu-id="ccd72-144">People might use the in-meeting tab to:</span></span>

* <span data-ttu-id="ccd72-145">Bereitstellen eines detaillierten Feedbacks (zum Beispiel Auswerten eines Bewerbers)</span><span class="sxs-lookup"><span data-stu-id="ccd72-145">Provide detailed feedback (for example, evaluate a job candidate)</span></span>
* <span data-ttu-id="ccd72-146">Schnelles Erstellen einer Umfrage, Umfrage oder eines Aufgabenelements für die Besprechungsteilnehmer</span><span class="sxs-lookup"><span data-stu-id="ccd72-146">Quickly create a poll, survey, or task item for the meeting participants</span></span>
* <span data-ttu-id="ccd72-147">Anzeigen von Notizen, die für die Besprechung relevant sind (beispielsweise Informationen zu einem Verkaufsleiter)</span><span class="sxs-lookup"><span data-stu-id="ccd72-147">Display notes relevant to the meeting (for example, information about a sales lead)</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-tab.png" alt-text="Beispiel zeigt, wie Sie Abstimmungs Inhalte auf einer Registerkarte in der Besprechung präsentieren können." border="false":::

### <a name="anatomy-in-meeting-tab"></a><span data-ttu-id="ccd72-149">Anatomie: Registerkarte "in der Besprechung"</span><span class="sxs-lookup"><span data-stu-id="ccd72-149">Anatomy: In-meeting tab</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-anatomy.png" alt-text="Beispiel zeigt die strukturelle Anatomie einer in-Meeting-Registerkarte." border="false":::

|<span data-ttu-id="ccd72-151">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="ccd72-151">Counter</span></span>|<span data-ttu-id="ccd72-152">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ccd72-152">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="ccd72-153">1</span><span class="sxs-lookup"><span data-stu-id="ccd72-153">1</span></span>|<span data-ttu-id="ccd72-154">**App-Symbol (ausgewählt)**: transparentes 16-Pixel-App-Logo.</span><span class="sxs-lookup"><span data-stu-id="ccd72-154">**App icon (selected)**: 16-pixel transparent app logo.</span></span>|
|<span data-ttu-id="ccd72-155">2 </span><span class="sxs-lookup"><span data-stu-id="ccd72-155">2</span></span>|<span data-ttu-id="ccd72-156">**App-Name**</span><span class="sxs-lookup"><span data-stu-id="ccd72-156">**App name**</span></span>|
|<span data-ttu-id="ccd72-157">3 </span><span class="sxs-lookup"><span data-stu-id="ccd72-157">3</span></span>|<span data-ttu-id="ccd72-158">**Kopfzeile**: enthält Ihren APP-Namen.</span><span class="sxs-lookup"><span data-stu-id="ccd72-158">**Header**: Includes your app name.</span></span>|
|<span data-ttu-id="ccd72-159">4 </span><span class="sxs-lookup"><span data-stu-id="ccd72-159">4</span></span>|<span data-ttu-id="ccd72-160">**Schließen (Schaltfläche**): die Registerkarte wird verworfen. Verwenden Sie immer das obere rechte Schließsymbol anstelle einer Aktion in der Fußzeile.</span><span class="sxs-lookup"><span data-stu-id="ccd72-160">**Close button**: Dismisses the tab. Always use the upper-right close icon instead of an action in the footer.</span></span>|
|<span data-ttu-id="ccd72-161">5 </span><span class="sxs-lookup"><span data-stu-id="ccd72-161">5</span></span>|<span data-ttu-id="ccd72-162">**Benachrichtigungsleiste**: Fehlermeldungen werden direkt unterhalb der Kopfzeile angezeigt, und der iframe-Inhalt wird um 20 Pixel nach unten verschoben.</span><span class="sxs-lookup"><span data-stu-id="ccd72-162">**Notification bar**: Error alerts display directly below the header and push the iframe content down by 20 pixels.</span></span>|
|<span data-ttu-id="ccd72-163">6 </span><span class="sxs-lookup"><span data-stu-id="ccd72-163">6</span></span>|<span data-ttu-id="ccd72-164">**iframe**: zeigt den App-Inhalt an.</span><span class="sxs-lookup"><span data-stu-id="ccd72-164">**iframe**: Displays your app content.</span></span>|

### <a name="spacing"></a><span data-ttu-id="ccd72-165">Abstand</span><span class="sxs-lookup"><span data-stu-id="ccd72-165">Spacing</span></span>

<span data-ttu-id="ccd72-166">Optimieren Sie Ihre in-Meeting-Registerkarte, um Edge-to-Edge im Bereich von 280 Pixel breitem IFRAME anzupassen.</span><span class="sxs-lookup"><span data-stu-id="ccd72-166">Optimize your in-meeting tab to fit edge-to-edge within the 280 pixel-wide iframe area.</span></span> <span data-ttu-id="ccd72-167">Es gibt 20 Pixel Textabstand auf der linken und rechten Seite des IFRAME und zwischen dem Registerkarten Kopf.</span><span class="sxs-lookup"><span data-stu-id="ccd72-167">There are 20 pixels of padding on the left and right sides of the iframe and between the tab header.</span></span> <span data-ttu-id="ccd72-168">Der iframe ist vollständig am unteren Rand der Registerkarte angefüllt.</span><span class="sxs-lookup"><span data-stu-id="ccd72-168">The iframe is full bleed to the bottom of the tab.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-spacing.png" alt-text="In diesem Beispiel werden Bemaßungen im Abstands Abstand im Besprechungs Register dargestellt." border="false":::

### <a name="scrolling"></a><span data-ttu-id="ccd72-170">Scrollen</span><span class="sxs-lookup"><span data-stu-id="ccd72-170">Scrolling</span></span>

<span data-ttu-id="ccd72-171">Iframe-Inhalte sollten vertikal scrollen.</span><span class="sxs-lookup"><span data-stu-id="ccd72-171">Iframe contents should scroll vertically.</span></span> <span data-ttu-id="ccd72-172">Sie können nur den Inhalt sehen, zu dem Sie einen Bildlauf durchgeführt haben (nichts oberhalb oder unterhalb).</span><span class="sxs-lookup"><span data-stu-id="ccd72-172">You can only see the content you've scrolled to (nothing above or below).</span></span> <span data-ttu-id="ccd72-173">Die ScrollBar ist Teil des IFRAME-Inhalts.</span><span class="sxs-lookup"><span data-stu-id="ccd72-173">The scrollbar is part of the iframe content.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-scrolling.png" alt-text="Beispiel zeigt, wie die in-Meeting-Registerkarte einen Bildlauf durchführt." border="false":::

### <a name="navigation"></a><span data-ttu-id="ccd72-175">Navigation</span><span class="sxs-lookup"><span data-stu-id="ccd72-175">Navigation</span></span>

<span data-ttu-id="ccd72-176">Für Szenarien mit Navigationsebenen oder schweren Inhalten empfehlen wir, Benutzern das Navigieren zu einer sekundären Ebene zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="ccd72-176">For scenarios with navigation layers or heavy content, we recommend allowing users to navigate to a secondary layer.</span></span> <span data-ttu-id="ccd72-177">Benutzer müssen in der Lage sein, zur vorherigen Ebene zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="ccd72-177">Users must be able to go back to the previous layer.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav.png" alt-text="Beispiel zeigt die in-Meeting-Navigation." border="false":::

## <a name="use-an-in-meeting-dialog"></a><span data-ttu-id="ccd72-179">Verwenden eines in-Meeting-Dialogs</span><span class="sxs-lookup"><span data-stu-id="ccd72-179">Use an in-meeting dialog</span></span>

<span data-ttu-id="ccd72-180">In-Meeting-Dialoge werden in der Teams-Besprechungs Phase angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ccd72-180">In-meeting dialogs display on the Teams meeting stage.</span></span> <span data-ttu-id="ccd72-181">Sie benötigen Aufmerksamkeit, Bestätigung oder Interaktion eines Benutzers, sind jedoch subtil und unterbrechen die Besprechung nicht.</span><span class="sxs-lookup"><span data-stu-id="ccd72-181">They require a user's attention, confirmation, or interaction but are subtle and don't interrupt the meeting.</span></span> <span data-ttu-id="ccd72-182">Sie sollten diese sparsam und für Szenarien verwenden, die leicht und aufgabenorientiert sind.</span><span class="sxs-lookup"><span data-stu-id="ccd72-182">You should use these sparingly and for scenarios that are light and task oriented.</span></span>

### <a name="use-cases"></a><span data-ttu-id="ccd72-183">Anwendungsfälle</span><span class="sxs-lookup"><span data-stu-id="ccd72-183">Use cases</span></span>

<span data-ttu-id="ccd72-184">In-Meeting-Dialogfelder werden von einem Benutzer (wie dem Besprechungsorganisator) ausgelöst, der den Teilnehmern möglicherweise Folgendes wünscht:</span><span class="sxs-lookup"><span data-stu-id="ccd72-184">In-meeting dialogs are triggered by a user (such as the meeting organizer) who might want participants to:</span></span>

* <span data-ttu-id="ccd72-185">Kurzes Feedback geben</span><span class="sxs-lookup"><span data-stu-id="ccd72-185">Provide brief feedback</span></span>
* <span data-ttu-id="ccd72-186">Eine kurze Umfrage oder Umfrage durchführen</span><span class="sxs-lookup"><span data-stu-id="ccd72-186">Take a short survey or poll</span></span>
* <span data-ttu-id="ccd72-187">Übermitteln von Genehmigungen</span><span class="sxs-lookup"><span data-stu-id="ccd72-187">Submit approvals</span></span>
* <span data-ttu-id="ccd72-188">Erinnerungen abrufen</span><span class="sxs-lookup"><span data-stu-id="ccd72-188">Get reminders</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-dialog.png" alt-text="Beispiel zeigt, wie Sie ein in-Meeting-Dialogfeldverwenden können." border="false":::

### <a name="anatomy-in-meeting-dialog"></a><span data-ttu-id="ccd72-190">Anatomie: Dialogfeld "in der Besprechung"</span><span class="sxs-lookup"><span data-stu-id="ccd72-190">Anatomy: In-meeting dialog</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-anatomy.png" alt-text="Beispiel zeigt die strukturelle Anatomie eines in-Meeting-Dialogs." border="false":::

|<span data-ttu-id="ccd72-192">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="ccd72-192">Counter</span></span>|<span data-ttu-id="ccd72-193">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ccd72-193">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="ccd72-194">1</span><span class="sxs-lookup"><span data-stu-id="ccd72-194">1</span></span>|<span data-ttu-id="ccd72-195">**Kopfzeile**: schließt das App-Symbol, den Namen, die Aktionszeichenfolge und das Schließsymbol ein.</span><span class="sxs-lookup"><span data-stu-id="ccd72-195">**Header**: Includes app icon, name, action string, and close icon.</span></span>|
|<span data-ttu-id="ccd72-196">2 </span><span class="sxs-lookup"><span data-stu-id="ccd72-196">2</span></span>|<span data-ttu-id="ccd72-197">**iframe**: zeigt den App-Inhalt an.</span><span class="sxs-lookup"><span data-stu-id="ccd72-197">**iframe**: Displays your app content.</span></span>|

### <a name="anatomy-in-meeting-dialog-header"></a><span data-ttu-id="ccd72-198">Anatomie: in-Meeting-Dialogfeld Kopfzeile</span><span class="sxs-lookup"><span data-stu-id="ccd72-198">Anatomy: In-meeting dialog header</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-header-anatomy.png" alt-text="Beispiel zeigt die strukturelle Anatomie einer in-Meeting-Dialogfeld Kopfzeile." border="false":::

<span data-ttu-id="ccd72-200">Es gibt zwei Header Varianten.</span><span class="sxs-lookup"><span data-stu-id="ccd72-200">There are two header variants.</span></span> <span data-ttu-id="ccd72-201">Verwenden Sie nach Möglichkeit die Variante mit dem Avatar, um zu verstärken, dass das Dialogfeld von einer Person kommt.</span><span class="sxs-lookup"><span data-stu-id="ccd72-201">When possible, use the variant with the avatar to reinforce that the dialog is coming from a person.</span></span>

|<span data-ttu-id="ccd72-202">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="ccd72-202">Counter</span></span>|<span data-ttu-id="ccd72-203">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ccd72-203">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="ccd72-204">1</span><span class="sxs-lookup"><span data-stu-id="ccd72-204">1</span></span>|<span data-ttu-id="ccd72-205">**Avatar**: Person, die den in-Meeting-Dialog initiiert.</span><span class="sxs-lookup"><span data-stu-id="ccd72-205">**Avatar**: Person who initiates the in-meeting dialog.</span></span>|
|<span data-ttu-id="ccd72-206">2 </span><span class="sxs-lookup"><span data-stu-id="ccd72-206">2</span></span>|<span data-ttu-id="ccd72-207">**App-Symbol**</span><span class="sxs-lookup"><span data-stu-id="ccd72-207">**App icon**</span></span>|
|<span data-ttu-id="ccd72-208">3 </span><span class="sxs-lookup"><span data-stu-id="ccd72-208">3</span></span>|<span data-ttu-id="ccd72-209">**App-Name**</span><span class="sxs-lookup"><span data-stu-id="ccd72-209">**App name**</span></span>|
|<span data-ttu-id="ccd72-210">4 </span><span class="sxs-lookup"><span data-stu-id="ccd72-210">4</span></span>|<span data-ttu-id="ccd72-211">**Schaltfläche Schließen**: das Dialogfeld wird geschlossen.</span><span class="sxs-lookup"><span data-stu-id="ccd72-211">**Close button**: Dismisses the dialog.</span></span>|
|<span data-ttu-id="ccd72-212">5 </span><span class="sxs-lookup"><span data-stu-id="ccd72-212">5</span></span>|<span data-ttu-id="ccd72-213">**Aktionszeichenfolge**: beschreibt normalerweise, wer das Dialogfeld initiiert hat.</span><span class="sxs-lookup"><span data-stu-id="ccd72-213">**Action string**: Typically describes who initiated the dialog.</span></span>|

### <a name="responsive-behavior"></a><span data-ttu-id="ccd72-214">Dynamisches Verhalten</span><span class="sxs-lookup"><span data-stu-id="ccd72-214">Responsive behavior</span></span>

<span data-ttu-id="ccd72-215">In-Meeting-Dialogfelder können in der Größe variieren, um verschiedene Szenarien zu berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="ccd72-215">In-meeting dialogs can vary in size to account for different scenarios.</span></span> <span data-ttu-id="ccd72-216">Stellen Sie sicher, dass der Abstand und die Komponentengrößen beibehalten werden.</span><span class="sxs-lookup"><span data-stu-id="ccd72-216">Make sure to maintain padding and component sizes.</span></span>

* <span data-ttu-id="ccd72-217">**Width**: die iframe-Breite ist ein absoluter Wert innerhalb des angegebenen Bereichs.</span><span class="sxs-lookup"><span data-stu-id="ccd72-217">**Width**: The iframe width is an absolute value within the range you specify.</span></span>
* <span data-ttu-id="ccd72-218">**Height**: die Höhe des Dialogs wird durch den Inhalt im IFRAME bestimmt.</span><span class="sxs-lookup"><span data-stu-id="ccd72-218">**Height**: The height of the dialog is determined by the content in the iframe.</span></span> <span data-ttu-id="ccd72-219">Der vertikale Bildlauf übernimmt den Inhalt, der die maximale Höhe überschreitet.</span><span class="sxs-lookup"><span data-stu-id="ccd72-219">Vertical scroll takes over for content that exceeds the maximum height.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-responsive.png" alt-text="Beispiel wird das in-Meeting-Dialogfeld angezeigt. Breite: min--280 Pixel (248 Pixel IFRAME). Max--460 Pixel (428 Pixel IFRAME). Höhe: 300 Pixel (IFRAME)." border="false":::

## <a name="after-a-meeting"></a><span data-ttu-id="ccd72-221">Nach einer Besprechung</span><span class="sxs-lookup"><span data-stu-id="ccd72-221">After a meeting</span></span>

<span data-ttu-id="ccd72-222">Sie können nach dem Beenden zu einer Besprechung zurückkehren und App-Inhalte anzeigen.</span><span class="sxs-lookup"><span data-stu-id="ccd72-222">You can go back to a meeting after it ends and view app content.</span></span> <span data-ttu-id="ccd72-223">In diesem Beispiel kann der Besprechungsorganisator die Umfrageergebnisse auf der Registerkarte " **contoso** " anzeigen. (Hinweis: aus Entwurfssicht gibt es keinen Unterschied zwischen der Benutzeroberfläche vor und nach der Besprechung.)</span><span class="sxs-lookup"><span data-stu-id="ccd72-223">In this example, the meeting organizer can look at poll results in the **Contoso** tab. (Note: From a design standpoint, there's no difference between a the pre- and post-meeting tab experience.)</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/post-meeting-experience.png" alt-text="Beispiel zeigt eine Registerkarte Nachbesprechung." border="false":::

## <a name="best-practices"></a><span data-ttu-id="ccd72-225">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="ccd72-225">Best practices</span></span>

### <a name="interactions"></a><span data-ttu-id="ccd72-226">Interaktionen</span><span class="sxs-lookup"><span data-stu-id="ccd72-226">Interactions</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-do.png" alt-text="Beispiel für eine bewährte Methode für die Besprechungs Erweiterung." border="false":::

#### <a name="do-limit-the-number-of-interactions"></a><span data-ttu-id="ccd72-228">Do: Begrenzen der Anzahl von Interaktionen</span><span class="sxs-lookup"><span data-stu-id="ccd72-228">Do: Limit the number of interactions</span></span>

<span data-ttu-id="ccd72-229">Entfernen Sie für in-Meeting-Dialogfelder unnötige Inhalte, die nicht dazu beitragen, dass Benutzer schnell etwas erreichen.</span><span class="sxs-lookup"><span data-stu-id="ccd72-229">For in-meeting dialogs, remove unnecessary content that doesn't help users accomplish something quickly.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-dont.png" alt-text="Beispiel für eine bewährte Methode für die Besprechungs Erweiterung." border="false":::

#### <a name="dont-introduce-unnecessary-elements"></a><span data-ttu-id="ccd72-231">Nicht: Einführung unnötiger Elemente</span><span class="sxs-lookup"><span data-stu-id="ccd72-231">Don't: Introduce unnecessary elements</span></span>

<span data-ttu-id="ccd72-232">Ein einzelnes in-Meeting-Dialogfeld mit mehreren Interaktionen kann vom Anruf ablenken.</span><span class="sxs-lookup"><span data-stu-id="ccd72-232">A single in-meeting dialog with multiple interactions can distract from the call.</span></span>

   :::column-end:::
:::row-end:::

### <a name="layout"></a><span data-ttu-id="ccd72-233">Layout</span><span class="sxs-lookup"><span data-stu-id="ccd72-233">Layout</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-do.png" alt-text="Beispiel für eine bewährte Methode für die Besprechungs Erweiterung." border="false":::

#### <a name="do-use-single-column-layouts"></a><span data-ttu-id="ccd72-235">Do: Verwenden von Einzel Spaltenlayouts</span><span class="sxs-lookup"><span data-stu-id="ccd72-235">Do: Use single-column layouts</span></span>

<span data-ttu-id="ccd72-236">Da sich die Dialogfelder in der Mitte der Besprechungs Phase befinden, sollte die Aufgaben Vervollständigung schnell und einfach sein, um Benutzer Frustration zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="ccd72-236">Since the dialogs are at the center of the meeting stage, task completion should be fast and simple to avoid user frustration.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-dont.png" alt-text="Beispiel für eine bewährte Methode für die Besprechungs Erweiterung." border="false":::

#### <a name="dont-clutter-the-space"></a><span data-ttu-id="ccd72-238">Nicht: Übersichtlichkeit des Speicherplatzes</span><span class="sxs-lookup"><span data-stu-id="ccd72-238">Don't: Clutter the space</span></span>

<span data-ttu-id="ccd72-239">Dichte oder übermäßig strukturierte Inhalte können störend und überwältigend sein, vor allem während einer Besprechung.</span><span class="sxs-lookup"><span data-stu-id="ccd72-239">Dense or overly structured content can be distracting and overwhelming, especially during a meeting.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-do.png" alt-text="Beispiel für eine bewährte Methode für die Besprechungs Erweiterung." border="false":::

#### <a name="do-use-single-columns"></a><span data-ttu-id="ccd72-241">Do: einzelne Spalten verwenden</span><span class="sxs-lookup"><span data-stu-id="ccd72-241">Do: Use single columns</span></span>

<span data-ttu-id="ccd72-242">Angesichts der engen Natur in der Besprechungs Registerkarte wird dringend empfohlen, den Inhalt in einer einzelnen Spalte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="ccd72-242">Given the in-meeting tab's narrow nature, we strongly recommend displaying the contents in a single column.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-dont.png" alt-text="Beispiel für eine bewährte Methode für die Besprechungs Erweiterung." border="false":::

#### <a name="dont-use-multiple-columns"></a><span data-ttu-id="ccd72-244">Nicht: mehrere Spalten verwenden</span><span class="sxs-lookup"><span data-stu-id="ccd72-244">Don't: Use multiple columns</span></span>

<span data-ttu-id="ccd72-245">Aufgrund des begrenzten Speicherplatzes der in-Meeting-Registerkarte werden Layouts mit mehr als einer Spalte nicht empfohlen.</span><span class="sxs-lookup"><span data-stu-id="ccd72-245">Due to the limited space of the in-meeting tab, layouts with more than one column aren’t recommended.</span></span>

   :::column-end:::
:::row-end:::

### <a name="controls"></a><span data-ttu-id="ccd72-246">Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="ccd72-246">Controls</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-do.png" alt-text="Beispiel für eine bewährte Methode für die Besprechungs Erweiterung." border="false":::

#### <a name="do-right-align-the-primary-action"></a><span data-ttu-id="ccd72-248">Do: Rechtsbündiges Ausrichten der primären Aktion</span><span class="sxs-lookup"><span data-stu-id="ccd72-248">Do: Right align the primary action</span></span>

<span data-ttu-id="ccd72-249">Es wird empfohlen, die positioiningste Aktion am am weitesten rechts gelegenen Ort zu übersichtlich.</span><span class="sxs-lookup"><span data-stu-id="ccd72-249">We recommend positioining the most visually heavy action to the right-most location.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-dont.png" alt-text="Beispiel für eine bewährte Methode für die Besprechungs Erweiterung." border="false":::

#### <a name="dont-left-or-center-align-actions"></a><span data-ttu-id="ccd72-251">Nicht: Links oder zentrierte Ausrichtungs Aktionen</span><span class="sxs-lookup"><span data-stu-id="ccd72-251">Don't: Left or center align actions</span></span>

<span data-ttu-id="ccd72-252">Dies weicht vom standardmäßigen Teams-Muster für die Platzierung von Steuerelementen in einem Dialogfeld ab und kann mit einem Dialogfeld hinter dem oberen Rand in Konflikt stehen.</span><span class="sxs-lookup"><span data-stu-id="ccd72-252">This deviates from the standard Teams pattern for control placement in a dialog and may conflict with a dialog behind the top one.</span></span>

   :::column-end:::
:::row-end:::

### <a name="scroll"></a><span data-ttu-id="ccd72-253">Bildlauf</span><span class="sxs-lookup"><span data-stu-id="ccd72-253">Scroll</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-do.png" alt-text="Beispiel für eine bewährte Methode für die Besprechungs Erweiterung." border="false":::

#### <a name="do-scroll-vertically"></a><span data-ttu-id="ccd72-255">Do: vertikal scrollen</span><span class="sxs-lookup"><span data-stu-id="ccd72-255">Do: Scroll vertically</span></span>

<span data-ttu-id="ccd72-256">Es wird empfohlen, die visuell intensivste Aktion an der am weitesten rechts gelegenen Stelle zu positionieren.</span><span class="sxs-lookup"><span data-stu-id="ccd72-256">We recommend positioning the most visually heavy action to the right-most location.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-dont.png" alt-text="Beispiel für eine bewährte Methode für die Besprechungs Erweiterung." border="false":::

#### <a name="dont-scroll-horizontally"></a><span data-ttu-id="ccd72-258">Nicht: horizontal scrollen</span><span class="sxs-lookup"><span data-stu-id="ccd72-258">Don't: Scroll horizontally</span></span>

<span data-ttu-id="ccd72-259">Ein horizontaler Bildlauf ist kein erwartetes Verhalten in Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="ccd72-259">Horizontal scrolling isn’t an expected behavior in Teams.</span></span> <span data-ttu-id="ccd72-260">Andere Canvases in der Besprechungs Umgebung Scrollen vertikal.</span><span class="sxs-lookup"><span data-stu-id="ccd72-260">Other canvases in the meeting environment scroll vertically.</span></span>

   :::column-end:::
:::row-end:::

### <a name="workflows"></a><span data-ttu-id="ccd72-261">Workflows</span><span class="sxs-lookup"><span data-stu-id="ccd72-261">Workflows</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-workflow-do.png" alt-text="Beispiel für eine bewährte Methode für die Besprechungs Erweiterung." border="false":::

#### <a name="do-surface-complex-scenarios-in-the-in-meeting-tab"></a><span data-ttu-id="ccd72-263">Do: Oberflächen komplexe Szenarien auf der Registerkarte "in-Meeting"</span><span class="sxs-lookup"><span data-stu-id="ccd72-263">Do: Surface complex scenarios in the in-meeting tab</span></span>

<span data-ttu-id="ccd72-264">Wenn Ihre APP mehrere Aufgaben umfasst, wird ein Layout mit einer einzelnen Spalte auf einer Registerkarte in der Besprechung dringend empfohlen.</span><span class="sxs-lookup"><span data-stu-id="ccd72-264">If your app includes multiple tasks, we strongly recommend a single-column layout in an in-meeting tab.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-workflow-dont.png" alt-text="Beispiel für eine bewährte Methode für die Besprechungs Erweiterung." border="false":::

#### <a name="dont-package-complex-scenarios-in-the-in-meeting-dialog"></a><span data-ttu-id="ccd72-266">Nicht: Verpacken komplexer Szenarien im Dialogfeld "in-Meeting"</span><span class="sxs-lookup"><span data-stu-id="ccd72-266">Don't: Package complex scenarios in the in-meeting dialog</span></span>

<span data-ttu-id="ccd72-267">In-Meeting-Dialoge sind für kurze Interaktionen vorgesehen.</span><span class="sxs-lookup"><span data-stu-id="ccd72-267">In-meeting dialogs are intended for brief interactions.</span></span>

   :::column-end:::
:::row-end:::

### <a name="theming"></a><span data-ttu-id="ccd72-268">Designs</span><span class="sxs-lookup"><span data-stu-id="ccd72-268">Theming</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-do.png" alt-text="Beispiel für eine bewährte Methode für die Besprechungs Erweiterung." border="false":::

#### <a name="do-use-teams-color-tokens"></a><span data-ttu-id="ccd72-270">Do: Verwenden von Microsoft Teams-Farb Token</span><span class="sxs-lookup"><span data-stu-id="ccd72-270">Do: Use Teams color tokens</span></span>

<span data-ttu-id="ccd72-271">Microsoft Teams-Besprechungen sind für den dunklen Modus optimiert, um visuelles und kognitives Rauschen zu reduzieren, sodass sich Benutzer auf die Diskussion und den freigegebenen Inhalt konzentrieren können.</span><span class="sxs-lookup"><span data-stu-id="ccd72-271">Teams meetings are optimized for dark mode to help reduce visual and cognitive noise so users can focus on the discussion and shared content.</span></span> <span data-ttu-id="ccd72-272">Erfahren Sie mehr über die Verwendung von <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">Farb Token (Fluent UI)</a>.</span><span class="sxs-lookup"><span data-stu-id="ccd72-272">Learn about using <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">color tokens (Fluent UI)</a>.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-dont.png" alt-text="Beispiel für eine bewährte Methode für die Besprechungs Erweiterung." border="false":::

#### <a name="dont-include-another-dismiss-button"></a><span data-ttu-id="ccd72-274">Nicht: andere Schaltfläche "Schließen" einschließen</span><span class="sxs-lookup"><span data-stu-id="ccd72-274">Don't: Include another dismiss button</span></span>

<span data-ttu-id="ccd72-275">Das Bereitstelleneiner Option zum Schließen von Inhalten in Besprechungs Registerkarten kann Probleme verursachen, da bereits eine Schaltfläche in der Kopfzeile vorhanden ist, um die in-Meeting-Registerkarte selbst zu schließen.</span><span class="sxs-lookup"><span data-stu-id="ccd72-275">Providing an option to close in-meeting tab content may cause issues since there’s already a button in the header to dismiss the in-meeting tab itself.</span></span>

   :::column-end:::
:::row-end:::

### <a name="navigation"></a><span data-ttu-id="ccd72-276">Navigation</span><span class="sxs-lookup"><span data-stu-id="ccd72-276">Navigation</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-do.png" alt-text="Beispiel für eine bewährte Methode für die Besprechungs Erweiterung." border="false":::

#### <a name="do-have-a-back-button"></a><span data-ttu-id="ccd72-278">Do: verfügen über eine Schaltfläche "zurück"</span><span class="sxs-lookup"><span data-stu-id="ccd72-278">Do: Have a back button</span></span>

<span data-ttu-id="ccd72-279">Wenn auf einer Registerkarte in der Besprechung mehr als eine Navigationsebene vorhanden ist, müssen die Benutzer in der Lage sein, zu ihren vorherigen Ansichten zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="ccd72-279">If you have more than one layer of navigation in an in-meeting tab, users must be able to go back to their previous views.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-dont.png" alt-text="Beispiel für eine bewährte Methode für die Besprechungs Erweiterung." border="false":::

#### <a name="dont-include-another-dismiss-button"></a><span data-ttu-id="ccd72-281">Nicht: andere Schaltfläche "Schließen" einschließen</span><span class="sxs-lookup"><span data-stu-id="ccd72-281">Don't: Include another dismiss button</span></span>

<span data-ttu-id="ccd72-282">Das Bereitstelleneiner Option zum Schließen von Inhalten in Besprechungs Registerkarten kann Probleme verursachen, da bereits eine Schaltfläche in der Kopfzeile vorhanden ist, um die in-Meeting-Registerkarte selbst zu schließen.</span><span class="sxs-lookup"><span data-stu-id="ccd72-282">Providing an option to close in-meeting tab content may cause issues since there’s already a button in the header to dismiss the in-meeting tab itself.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-caution.png" alt-text="Beispiel für eine bewährte Methode für die Besprechungs Erweiterung." border="false":::

#### <a name="caution-avoid-modals-within-the-in-meeting-tab"></a><span data-ttu-id="ccd72-284">Vorsicht: Vermeiden von modaldaten auf der Registerkarte "in-Meeting"</span><span class="sxs-lookup"><span data-stu-id="ccd72-284">Caution: Avoid modals within the in-meeting tab</span></span>

<span data-ttu-id="ccd72-285">Modals (auch als Vorgangs Module bezeichnet) in der ohnehin engen Registerkarte "in-Meeting" kann den Inhalt Umbrechen und verdecken.</span><span class="sxs-lookup"><span data-stu-id="ccd72-285">Modals (also known as task modules) in the already narrow in-meeting tab might wrap and obscure the content.</span></span>

   :::column-end:::
:::row-end:::

## <a name="validate-your-design"></a><span data-ttu-id="ccd72-286">Überprüfen des Designs</span><span class="sxs-lookup"><span data-stu-id="ccd72-286">Validate your design</span></span>

<span data-ttu-id="ccd72-287">Wenn Sie Ihre APP in AppSource veröffentlichen möchten, sollten Sie sich mit den Entwurfsproblemen vertraut machen, die häufig dazu führen, dass apps während der Übermittlung fehlschlagen.</span><span class="sxs-lookup"><span data-stu-id="ccd72-287">If you plan to publish your app to AppSource, you should understand the design issues that commonly cause apps to fail during submission.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ccd72-288">Überprüfen der Entwurfs Validierungsrichtlinien</span><span class="sxs-lookup"><span data-stu-id="ccd72-288">Check design validation guidelines</span></span>](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines--most-failed-test-cases)
