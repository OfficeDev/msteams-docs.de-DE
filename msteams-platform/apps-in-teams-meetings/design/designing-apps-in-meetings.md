---
title: Entwerfen Ihrer Besprechungserweiterung
author: heath-hamilton
description: Erfahren Sie, wie Sie Apps in Teams Besprechungen entwerfen und das Microsoft Teams UI Kit erhalten.
ms.author: lajanuar
localization_priority: Normal
ms.topic: conceptual
ms.openlocfilehash: 7196017f92bebb776d1b73680893ebfe3684a74c
ms.sourcegitcommit: 6e4d2c8e99426125f7b72b9640ee4a4b4f374401
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/24/2021
ms.locfileid: "53114309"
---
# <a name="designing-your-microsoft-teams-meeting-extension"></a><span data-ttu-id="ac24e-103">Entwerfen ihrer Microsoft Teams Besprechungserweiterung</span><span class="sxs-lookup"><span data-stu-id="ac24e-103">Designing your Microsoft Teams meeting extension</span></span>

<span data-ttu-id="ac24e-104">Sie können Apps erstellen, um Besprechungen produktiver zu gestalten.</span><span class="sxs-lookup"><span data-stu-id="ac24e-104">You can create apps to make meetings more productive.</span></span> <span data-ttu-id="ac24e-105">Bitten Sie personen beispielsweise, während eines Anrufs eine Umfrage durchzuführen, oder senden Sie eine kurze Erinnerung, die den Besprechungsfluss nicht unterbricht.</span><span class="sxs-lookup"><span data-stu-id="ac24e-105">For example, ask people to complete a survey during a call or send a quick reminder that doesn’t interrupt the flow of the meeting.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="ac24e-106">Microsoft Teams-UI-Kit</span><span class="sxs-lookup"><span data-stu-id="ac24e-106">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="ac24e-107">Umfassendere Entwurfsrichtlinien, einschließlich Elementen, die Sie bei Bedarf abrufen und ändern können, finden Sie im Microsoft Teams UI Kit.</span><span class="sxs-lookup"><span data-stu-id="ac24e-107">You can find more comprehensive design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ac24e-108">Holen Sie sich das Microsoft Teams-UI-Kit (Figma)</span><span class="sxs-lookup"><span data-stu-id="ac24e-108">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-meeting-extension"></a><span data-ttu-id="ac24e-109">Hinzufügen einer Besprechungserweiterung</span><span class="sxs-lookup"><span data-stu-id="ac24e-109">Add a meeting extension</span></span>

<span data-ttu-id="ac24e-110">Benutzer können vor und während Besprechungen eine Besprechungserweiterung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ac24e-110">Users can add a meeting extension before and during meetings.</span></span> <span data-ttu-id="ac24e-111">Sie können eine App für eine bestimmte Besprechung auch direkt aus dem Teams Store hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ac24e-111">They also can add an app for a specific meeting directly from the Teams store.</span></span>

### <a name="add-before-a-meeting"></a><span data-ttu-id="ac24e-112">Hinzufügen vor einer Besprechung</span><span class="sxs-lookup"><span data-stu-id="ac24e-112">Add before a meeting</span></span>

<span data-ttu-id="ac24e-113">In den Besprechungsdetails können Benutzer **eine Registerkarte hinzufügen +** auswählen, um das App-Flyout zu öffnen und apps zu finden, die für Besprechungen optimiert sind.</span><span class="sxs-lookup"><span data-stu-id="ac24e-113">In the meeting details, users can select **Add a tab +** to open the app flyout and find apps optimized for meetings.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/add-before-meeting.png" alt-text="Beispiel zeigt, wie Sie eine Besprechungserweiterung vor einer Besprechung hinzufügen." border="false":::

### <a name="add-during-a-meeting"></a><span data-ttu-id="ac24e-115">Während einer Besprechung hinzufügen</span><span class="sxs-lookup"><span data-stu-id="ac24e-115">Add during a meeting</span></span>

# <a name="desktop"></a>[<span data-ttu-id="ac24e-116">Desktop</span><span class="sxs-lookup"><span data-stu-id="ac24e-116">Desktop</span></span>](#tab/desktop)

In einer Besprechung können Benutzer **weitere** :::image type="icon" source="../../assets/icons/teams-client-more.png":::  >  **Apps hinzufügen** und die gewünschte App auswählen.

:::image type="content" source="../../assets/images/apps-in-meetings/add-during-meeting.png" alt-text="Beispiel zeigt, wie sie während einer Besprechung eine Besprechungserweiterung hinzufügen." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="ac24e-119">Mobil</span><span class="sxs-lookup"><span data-stu-id="ac24e-119">Mobile</span></span>](#tab/mobile)

In einer Besprechung können Benutzer **mehr** :::image type="icon" source="../../assets/icons/teams-client-more.png"::: auswählen und die gewünschte App auswählen.

:::image type="content" source="../../assets/images/apps-in-meetings/mobile-add-during-meeting.png" alt-text="Beispiel zeigt, wie sie während einer Besprechung auf mobilen Geräten eine Besprechungserweiterung hinzufügen." border="false":::

---

## <a name="before-a-meeting"></a><span data-ttu-id="ac24e-122">Vor einer Besprechung</span><span class="sxs-lookup"><span data-stu-id="ac24e-122">Before a meeting</span></span>

<span data-ttu-id="ac24e-123">Vor einer Besprechung können Benutzer Inhalte auf der Registerkarte hinzufügen. Das folgende Beispiel zeigt einen Entwurf einer Umfragefrage, die während des Anrufs beantwortet wird.</span><span class="sxs-lookup"><span data-stu-id="ac24e-123">Prior to a meeting, users can add content in the tab. The following example shows a draft survey question that people will answer during the call.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/before-meeting-tab.png" alt-text="Beispiel zeigt, wie Sie Inhalte in den Besprechungsdetails vor einem Anruf appieren." border="false":::

### <a name="anatomy-meeting-tab-before-and-after-meetings"></a><span data-ttu-id="ac24e-125">Anatomie: Besprechungsregisterkarte (vor und nach Besprechungen)</span><span class="sxs-lookup"><span data-stu-id="ac24e-125">Anatomy: Meeting tab (before and after meetings)</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/meeting-details-tab-anatomy.png" alt-text="Beispiel zeigt die strukturelle Anatomie einer Besprechungsregisterkarte vor und nach einer Besprechung." border="false":::

|<span data-ttu-id="ac24e-127">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="ac24e-127">Counter</span></span>|<span data-ttu-id="ac24e-128">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ac24e-128">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="ac24e-129">1</span><span class="sxs-lookup"><span data-stu-id="ac24e-129">1</span></span>|<span data-ttu-id="ac24e-130">**Registerkartenname:** Navigationsbezeichnung für Ihre Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="ac24e-130">**Tab name**: Navigation label for your tab.</span></span>|
|<span data-ttu-id="ac24e-131">2 </span><span class="sxs-lookup"><span data-stu-id="ac24e-131">2</span></span>|<span data-ttu-id="ac24e-132">**Registerkartenüberlauf:** Öffnet Registerkartenaktionen, z. B. Umbenennen und Entfernen.</span><span class="sxs-lookup"><span data-stu-id="ac24e-132">**Tab overflow**: Opens tab actions, such as rename and remove.</span></span>|
|<span data-ttu-id="ac24e-133">3 </span><span class="sxs-lookup"><span data-stu-id="ac24e-133">3</span></span>|<span data-ttu-id="ac24e-134">**iframe:** Zeigt Ihre App-Inhalte an.</span><span class="sxs-lookup"><span data-stu-id="ac24e-134">**iframe**: Displays your app content.</span></span>|

### <a name="designing-with-ui-templates"></a><span data-ttu-id="ac24e-135">Entwerfen mit UI-Vorlagen</span><span class="sxs-lookup"><span data-stu-id="ac24e-135">Designing with UI templates</span></span>

<span data-ttu-id="ac24e-136">Verwenden Sie eine der folgenden Teams Ui-Vorlagen, um die Besprechungsregisterkarte zu entwerfen:</span><span class="sxs-lookup"><span data-stu-id="ac24e-136">Use one of the following Teams UI templates to help design your meeting tab:</span></span>

* <span data-ttu-id="ac24e-137">[Liste:](../../concepts/design/design-teams-app-ui-templates.md#list)Listen können verwandte Elemente in einem scannbaren Format anzeigen und Benutzern ermöglichen, Aktionen für eine gesamte Liste oder einzelne Elemente auszuführen.</span><span class="sxs-lookup"><span data-stu-id="ac24e-137">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="ac24e-138">[Task Board:](../../concepts/design/design-teams-app-ui-templates.md#task-board)Ein Task Board, manchmal auch als "Tickets Board" oder "Sperre" bezeichnet, ist eine Sammlung von Karten, die häufig verwendet werden, um den Status von Arbeitselementen oder Tickets nachzuverfolgen.</span><span class="sxs-lookup"><span data-stu-id="ac24e-138">[Task board](../../concepts/design/design-teams-app-ui-templates.md#task-board): A task board, sometimes called a kanban board or swim lanes, is a collection of cards often used to track the status of work items or tickets.</span></span>
* <span data-ttu-id="ac24e-139">[Dashboard:](../../concepts/design/design-teams-app-ui-templates.md#dashboard)Ein Dashboard ist eine Canvas mit mehreren Karten, die eine Übersicht über Daten oder Inhalte bieten.</span><span class="sxs-lookup"><span data-stu-id="ac24e-139">[Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): A dashboard is a canvas containing multiple cards that provide an overview of data or content.</span></span>
* <span data-ttu-id="ac24e-140">[Formular:](../../concepts/design/design-teams-app-ui-templates.md#form)Formulare dienen zum strukturierten Sammeln, Überprüfen und Übermitteln von Benutzereingaben.</span><span class="sxs-lookup"><span data-stu-id="ac24e-140">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="ac24e-141">[Leerer Zustand:](../../concepts/design/design-teams-app-ui-templates.md#empty-state)Die leere Statusvorlage kann für viele Szenarien verwendet werden, einschließlich Anmeldung, Erste Ausführung, Fehlermeldungen und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="ac24e-141">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>
* <span data-ttu-id="ac24e-142">[Linke Navigation:](../../concepts/design/design-teams-app-advanced-ui-components.md#left-nav)Die linke Navigationskomponente kann hilfreich sein, wenn ihre Registerkarte eine Navigation erfordert.</span><span class="sxs-lookup"><span data-stu-id="ac24e-142">[Left nav](../../concepts/design/design-teams-app-advanced-ui-components.md#left-nav): The left nav component can help if your tab requires some navigation.</span></span> <span data-ttu-id="ac24e-143">Im Allgemeinen sollten Sie die Navigation auf ein Minimum beschränken.</span><span class="sxs-lookup"><span data-stu-id="ac24e-143">In general, you should keep navigation to a minimum.</span></span>

## <a name="use-an-in-meeting-tab"></a><span data-ttu-id="ac24e-144">Verwenden einer Besprechungsregisterkarte</span><span class="sxs-lookup"><span data-stu-id="ac24e-144">Use an in-meeting tab</span></span>

<span data-ttu-id="ac24e-145">Die Registerkarte "Besprechungsinterne Besprechung" ist ein Zeichenbereich zum Erweitern der Zusammenarbeit während Besprechungen.</span><span class="sxs-lookup"><span data-stu-id="ac24e-145">The in-meeting tab is a canvas for augmenting collaboration during meetings.</span></span> <span data-ttu-id="ac24e-146">Teilnehmer können App-Inhalte in einem dedizierten Bereich außerhalb der Besprechungsphase über freigegebene oder rollenbasierte Ansichten anzeigen und mit ihnen interagieren.</span><span class="sxs-lookup"><span data-stu-id="ac24e-146">Attendees can see and interact with app content in a dedicated space outside the meeting stage through shared or role-based views.</span></span>

### <a name="use-cases"></a><span data-ttu-id="ac24e-147">Anwendungsfälle</span><span class="sxs-lookup"><span data-stu-id="ac24e-147">Use cases</span></span>

<span data-ttu-id="ac24e-148">Personen können die Registerkarte "Besprechungsinterne Besprechung" für Folgendes verwenden:</span><span class="sxs-lookup"><span data-stu-id="ac24e-148">People might use the in-meeting tab to:</span></span>

* <span data-ttu-id="ac24e-149">Geben Sie ausführliches Feedback.</span><span class="sxs-lookup"><span data-stu-id="ac24e-149">Provide detailed feedback.</span></span> <span data-ttu-id="ac24e-150">Bewerten Sie beispielsweise einen Stellenkandidaten.</span><span class="sxs-lookup"><span data-stu-id="ac24e-150">For example, evaluate a job candidate.</span></span>
* <span data-ttu-id="ac24e-151">Erstellen Sie eine Umfrage, eine Umfrage oder ein Aufgabenelement für die Besprechungsteilnehmer.</span><span class="sxs-lookup"><span data-stu-id="ac24e-151">Create a poll, survey, or task item for the meeting participants.</span></span>
* <span data-ttu-id="ac24e-152">Zeigt notizen an, die für die Besprechung relevant sind.</span><span class="sxs-lookup"><span data-stu-id="ac24e-152">Display notes relevant to the meeting.</span></span> <span data-ttu-id="ac24e-153">Beispielsweise Informationen zu einem Vertriebsleiter.</span><span class="sxs-lookup"><span data-stu-id="ac24e-153">For example, information about a sales lead.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="ac24e-154">Desktop</span><span class="sxs-lookup"><span data-stu-id="ac24e-154">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-tab.png" alt-text="Beispiel zeigt, wie Sie Abfrageinhalte auf einer Besprechungsregisterkarte darstellen können." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="ac24e-156">Mobil</span><span class="sxs-lookup"><span data-stu-id="ac24e-156">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/apps-in-meetings/mobile-use-in-meeting-tab.png" alt-text="Beispiel zeigt, wie Sie Umfrageinhalte auf einer Besprechungsregisterkarte auf mobilen Geräten anzeigen können." border="false":::

---

### <a name="anatomy-in-meeting-tab"></a><span data-ttu-id="ac24e-158">Anatomie: Registerkarte "In-Meeting"</span><span class="sxs-lookup"><span data-stu-id="ac24e-158">Anatomy: In-meeting tab</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-anatomy.png" alt-text="Beispiel zeigt die strukturelle Anatomie einer Besprechungsregisterkarte." border="false":::

|<span data-ttu-id="ac24e-160">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="ac24e-160">Counter</span></span>|<span data-ttu-id="ac24e-161">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ac24e-161">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="ac24e-162">1</span><span class="sxs-lookup"><span data-stu-id="ac24e-162">1</span></span>|<span data-ttu-id="ac24e-163">**App-Symbol (ausgewählt):** 16 Pixel transparentes App-Logo.</span><span class="sxs-lookup"><span data-stu-id="ac24e-163">**App icon (selected)**: 16-pixel transparent app logo.</span></span>|
|<span data-ttu-id="ac24e-164">2 </span><span class="sxs-lookup"><span data-stu-id="ac24e-164">2</span></span>|<span data-ttu-id="ac24e-165">**App-Name**</span><span class="sxs-lookup"><span data-stu-id="ac24e-165">**App name**</span></span>|
|<span data-ttu-id="ac24e-166">3 </span><span class="sxs-lookup"><span data-stu-id="ac24e-166">3</span></span>|<span data-ttu-id="ac24e-167">**Header:** Enthält ihren App-Namen.</span><span class="sxs-lookup"><span data-stu-id="ac24e-167">**Header**: Includes your app name.</span></span>|
|<span data-ttu-id="ac24e-168">4 </span><span class="sxs-lookup"><span data-stu-id="ac24e-168">4</span></span>|<span data-ttu-id="ac24e-169">**Schaltfläche "Schließen":** Schließt die Registerkarte. Verwenden Sie immer das Symbol zum Schließen oben rechts anstelle einer Aktion in der Fußzeile.</span><span class="sxs-lookup"><span data-stu-id="ac24e-169">**Close button**: Dismisses the tab. Always use the upper-right close icon instead of an action in the footer.</span></span>|
|<span data-ttu-id="ac24e-170">5 </span><span class="sxs-lookup"><span data-stu-id="ac24e-170">5</span></span>|<span data-ttu-id="ac24e-171">**Benachrichtigungsleiste:** Fehlerwarnungen werden direkt unterhalb der Kopfzeile angezeigt, und der iframe-Inhalt wird um 20 Pixel nach unten verschoben.</span><span class="sxs-lookup"><span data-stu-id="ac24e-171">**Notification bar**: Error alerts display directly below the header and push the iframe content down by 20 pixels.</span></span>|
|<span data-ttu-id="ac24e-172">6 </span><span class="sxs-lookup"><span data-stu-id="ac24e-172">6</span></span>|<span data-ttu-id="ac24e-173">**iframe:** Zeigt Ihre App-Inhalte an.</span><span class="sxs-lookup"><span data-stu-id="ac24e-173">**iframe**: Displays your app content.</span></span>|

### <a name="spacing"></a><span data-ttu-id="ac24e-174">Abstand</span><span class="sxs-lookup"><span data-stu-id="ac24e-174">Spacing</span></span>

<span data-ttu-id="ac24e-175">Optimieren Sie Ihre Besprechungsregisterkarte so, dass sie in den 280 Pixel breiten iFramebereich passt.</span><span class="sxs-lookup"><span data-stu-id="ac24e-175">Optimize your in-meeting tab to fit edge-to-edge within the 280 pixel-wide iframe area.</span></span> <span data-ttu-id="ac24e-176">Es gibt 20 Pixel Abstand auf der linken und rechten Seite des iframe und zwischen der Registerkartenkopfzeile.</span><span class="sxs-lookup"><span data-stu-id="ac24e-176">There are 20 pixels of padding on the left and right sides of the iframe and between the tab header.</span></span> <span data-ttu-id="ac24e-177">Der iframe ist vollständig beschnitten bis zum unteren Rand der Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="ac24e-177">The iframe is full bleed to the bottom of the tab.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-spacing.png" alt-text="Beispiel zeigt die Größe des Tababstands in besprechungsinternen Besprechungen." border="false":::

### <a name="scrolling"></a><span data-ttu-id="ac24e-179">Scrollen</span><span class="sxs-lookup"><span data-stu-id="ac24e-179">Scrolling</span></span>

<span data-ttu-id="ac24e-180">Beachten Sie Folgendes, wenn Sie den Bildlauf zulassen:</span><span class="sxs-lookup"><span data-stu-id="ac24e-180">Remember the following if you allow scrolling:</span></span>

* <span data-ttu-id="ac24e-181">Inhalte im iframe-Inhalt sollten nur vertikal scrollen.</span><span class="sxs-lookup"><span data-stu-id="ac24e-181">Content in the iframe contents should only scroll vertically.</span></span>
* <span data-ttu-id="ac24e-182">Benutzer sollten nur den Inhalt sehen, zu dem sie einen Bildlauf durchgeführt haben (nichts über oder darunter).</span><span class="sxs-lookup"><span data-stu-id="ac24e-182">Users should only see the content they've scrolled to (nothing above or below).</span></span> 
* <span data-ttu-id="ac24e-183">Die Bildlaufleiste ist Teil des iframe-Inhalts.</span><span class="sxs-lookup"><span data-stu-id="ac24e-183">The scrollbar is part of the iframe content.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-scrolling.png" alt-text="Beispiel zeigt, wie die Besprechungsregisterkarte scrollt." border="false":::

### <a name="navigation"></a><span data-ttu-id="ac24e-185">Navigation</span><span class="sxs-lookup"><span data-stu-id="ac24e-185">Navigation</span></span>

<span data-ttu-id="ac24e-186">Für Szenarien mit Navigationsebenen oder umfangreichen Inhalten wird empfohlen, Benutzern das Navigieren zu einer sekundären Ebene zu gestatten.</span><span class="sxs-lookup"><span data-stu-id="ac24e-186">For scenarios with navigation layers or heavy content, we recommend allowing users to navigate to a secondary layer.</span></span> <span data-ttu-id="ac24e-187">Benutzer müssen in der Lage sein, zur vorherigen Ebene zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="ac24e-187">Users must be able to go back to the previous layer.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav.png" alt-text="Beispiel zeigt die Navigation in Besprechungen." border="false":::

## <a name="use-an-in-meeting-dialog"></a><span data-ttu-id="ac24e-189">Verwenden eines Besprechungsdialogfelds</span><span class="sxs-lookup"><span data-stu-id="ac24e-189">Use an in-meeting dialog</span></span>

<span data-ttu-id="ac24e-190">Dialogfelder in Besprechungen werden auf der Teams Besprechungsphase angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ac24e-190">In-meeting dialogs display on the Teams meeting stage.</span></span> <span data-ttu-id="ac24e-191">Sie erfordern die Aufmerksamkeit, Bestätigung oder Interaktion eines Benutzers, sind aber dezent und unterbrechen die Besprechung nicht.</span><span class="sxs-lookup"><span data-stu-id="ac24e-191">They require a user's attention, confirmation, or interaction but are subtle and don't interrupt the meeting.</span></span> <span data-ttu-id="ac24e-192">Sie sollten diese sparsam und für Szenarien verwenden, die leicht und aufgabenorientiert sind.</span><span class="sxs-lookup"><span data-stu-id="ac24e-192">You should use these sparingly and for scenarios that are light and task oriented.</span></span>

### <a name="use-cases"></a><span data-ttu-id="ac24e-193">Anwendungsfälle</span><span class="sxs-lookup"><span data-stu-id="ac24e-193">Use cases</span></span>

<span data-ttu-id="ac24e-194">In-Meeting-Dialogfelder werden von einem Benutzer (z. B. dem Besprechungsorganisator) ausgelöst, der Teilnehmer möglicherweise folgendes wünschen:</span><span class="sxs-lookup"><span data-stu-id="ac24e-194">In-meeting dialogs are triggered by a user (such as the meeting organizer) who might want participants to:</span></span>

* <span data-ttu-id="ac24e-195">Geben Sie kurzes Feedback</span><span class="sxs-lookup"><span data-stu-id="ac24e-195">Provide brief feedback</span></span>
* <span data-ttu-id="ac24e-196">Nehmen Sie an einer kurzen Umfrage oder Umfrage teil</span><span class="sxs-lookup"><span data-stu-id="ac24e-196">Take a short survey or poll</span></span>
* <span data-ttu-id="ac24e-197">Übermitteln von Genehmigungen</span><span class="sxs-lookup"><span data-stu-id="ac24e-197">Submit approvals</span></span>
* <span data-ttu-id="ac24e-198">Abrufen von Erinnerungen</span><span class="sxs-lookup"><span data-stu-id="ac24e-198">Get reminders</span></span>

# <a name="desktop"></a>[<span data-ttu-id="ac24e-199">Desktop</span><span class="sxs-lookup"><span data-stu-id="ac24e-199">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-dialog.png" alt-text="Beispiel zeigt, wie Sie ein Besprechungsdialogfeld verwenden können." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="ac24e-201">Mobil</span><span class="sxs-lookup"><span data-stu-id="ac24e-201">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/apps-in-meetings/mobile-use-in-meeting-dialog.png" alt-text="Beispiel zeigt, wie Sie ein Besprechungsdialogfeld auf mobilgeräten verwenden können." border="false":::

---

### <a name="anatomy-in-meeting-dialog"></a><span data-ttu-id="ac24e-203">Anatomie: Besprechungsdialogfeld</span><span class="sxs-lookup"><span data-stu-id="ac24e-203">Anatomy: In-meeting dialog</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-anatomy.png" alt-text="Beispiel zeigt die strukturelle Anatomie eines Besprechungsdialogfelds." border="false":::

|<span data-ttu-id="ac24e-205">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="ac24e-205">Counter</span></span>|<span data-ttu-id="ac24e-206">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ac24e-206">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="ac24e-207">1</span><span class="sxs-lookup"><span data-stu-id="ac24e-207">1</span></span>|<span data-ttu-id="ac24e-208">**Kopfzeile:** Enthält das App-Symbol, den Namen, die Aktionszeichenfolge und das Schließen-Symbol.</span><span class="sxs-lookup"><span data-stu-id="ac24e-208">**Header**: Includes app icon, name, action string, and close icon.</span></span>|
|<span data-ttu-id="ac24e-209">2 </span><span class="sxs-lookup"><span data-stu-id="ac24e-209">2</span></span>|<span data-ttu-id="ac24e-210">**iframe:** Zeigt Ihre App-Inhalte an.</span><span class="sxs-lookup"><span data-stu-id="ac24e-210">**iframe**: Displays your app content.</span></span>|

### <a name="anatomy-in-meeting-dialog-header"></a><span data-ttu-id="ac24e-211">Anatomie: Kopfzeile des Besprechungsdialogfelds</span><span class="sxs-lookup"><span data-stu-id="ac24e-211">Anatomy: In-meeting dialog header</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-header-anatomy.png" alt-text="Beispiel zeigt die strukturelle Anatomie einer Besprechungsdialogkopfzeile." border="false":::

<span data-ttu-id="ac24e-213">Es gibt zwei Kopfzeilenvarianten.</span><span class="sxs-lookup"><span data-stu-id="ac24e-213">There are two header variants.</span></span> <span data-ttu-id="ac24e-214">Verwenden Sie nach Möglichkeit die Variante mit dem Avatar, um zu bestätigen, dass das Dialogfeld von einer Person stammt.</span><span class="sxs-lookup"><span data-stu-id="ac24e-214">When possible, use the variant with the avatar to reinforce that the dialog is coming from a person.</span></span>

|<span data-ttu-id="ac24e-215">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="ac24e-215">Counter</span></span>|<span data-ttu-id="ac24e-216">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ac24e-216">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="ac24e-217">1</span><span class="sxs-lookup"><span data-stu-id="ac24e-217">1</span></span>|<span data-ttu-id="ac24e-218">**Avatar**: Person, die das Besprechungsdialogfeld initiiert.</span><span class="sxs-lookup"><span data-stu-id="ac24e-218">**Avatar**: Person who initiates the in-meeting dialog.</span></span>|
|<span data-ttu-id="ac24e-219">2 </span><span class="sxs-lookup"><span data-stu-id="ac24e-219">2</span></span>|<span data-ttu-id="ac24e-220">**App-Symbol**</span><span class="sxs-lookup"><span data-stu-id="ac24e-220">**App icon**</span></span>|
|<span data-ttu-id="ac24e-221">3 </span><span class="sxs-lookup"><span data-stu-id="ac24e-221">3</span></span>|<span data-ttu-id="ac24e-222">**App-Name**</span><span class="sxs-lookup"><span data-stu-id="ac24e-222">**App name**</span></span>|
|<span data-ttu-id="ac24e-223">4 </span><span class="sxs-lookup"><span data-stu-id="ac24e-223">4</span></span>|<span data-ttu-id="ac24e-224">**Schaltfläche "Schließen":** Schließt das Dialogfeld.</span><span class="sxs-lookup"><span data-stu-id="ac24e-224">**Close button**: Dismisses the dialog.</span></span>|
|<span data-ttu-id="ac24e-225">5 </span><span class="sxs-lookup"><span data-stu-id="ac24e-225">5</span></span>|<span data-ttu-id="ac24e-226">**Aktionszeichenfolge:** Beschreibt in der Regel, wer das Dialogfeld initiiert hat.</span><span class="sxs-lookup"><span data-stu-id="ac24e-226">**Action string**: Typically describes who initiated the dialog.</span></span>|

### <a name="responsive-behavior-in-meeting-dialogs"></a><span data-ttu-id="ac24e-227">Reaktionsfähiges Verhalten: Dialogfelder in Besprechungen</span><span class="sxs-lookup"><span data-stu-id="ac24e-227">Responsive behavior: In-meeting dialogs</span></span>

<span data-ttu-id="ac24e-228">Dialogfelder in Besprechungen können je nach Größe variieren, um unterschiedliche Szenarien zu berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="ac24e-228">In-meeting dialogs can vary in size to account for different scenarios.</span></span> <span data-ttu-id="ac24e-229">Achten Sie darauf, abstands- und komponentengrößen beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="ac24e-229">Make sure to maintain padding and component sizes.</span></span>

* <span data-ttu-id="ac24e-230">**Breite:** Sie können die Breite des iframe des Dialogfelds an einer beliebigen Stelle innerhalb des unterstützten Größenbereichs angeben.</span><span class="sxs-lookup"><span data-stu-id="ac24e-230">**Width**: You can specify the width of the dialog's iframe anywhere within the supported size range.</span></span>
* <span data-ttu-id="ac24e-231">**Höhe:** Sie können die Höhe des iFrames des Dialogfelds an einer beliebigen Stelle innerhalb des unterstützten Größenbereichs angeben.</span><span class="sxs-lookup"><span data-stu-id="ac24e-231">**Height**: You can specify the height of the dialog's iframe anywhere within the supported size range.</span></span> <span data-ttu-id="ac24e-232">Sie können Benutzern auch den vertikalen Bildlauf ermöglichen, wenn Der App-Inhalt die maximale Höhe überschreitet.</span><span class="sxs-lookup"><span data-stu-id="ac24e-232">You also can allow users to scroll vertically if your app content exceeds the maximum height.</span></span>

<span data-ttu-id="ac24e-233">Geben Sie zum Implementieren die Breite und Höhe mithilfe des [`externalResourceUrl`](~/apps-in-teams-meetings/create-apps-for-teams-meetings.md#notificationsignal-api) Schlüssels an.</span><span class="sxs-lookup"><span data-stu-id="ac24e-233">To implement, specify the width and height using the [`externalResourceUrl`](~/apps-in-teams-meetings/create-apps-for-teams-meetings.md#notificationsignal-api) key.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-responsive.png" alt-text="Beispiel zeigt das Dialogfeld &quot;In-Meeting&quot;. Breite: Min.-280 Pixel (248 Pixel iframe). Max-460 Pixel (428 Pixel iframe). Höhe: 300 Pixel (iframe)." border="false":::

## <a name="use-the-shared-meeting-stage"></a><span data-ttu-id="ac24e-235">Verwenden der freigegebenen Besprechungsphase</span><span class="sxs-lookup"><span data-stu-id="ac24e-235">Use the shared meeting stage</span></span>

<span data-ttu-id="ac24e-236">Die freigegebene Besprechungsphase hilft Besprechungsteilnehmern, in Echtzeit mit App-Inhalten zu interagieren und daran zusammenzuarbeiten.</span><span class="sxs-lookup"><span data-stu-id="ac24e-236">Shared meeting stage helps meeting participants interact with and collaborate on app content in real-time.</span></span> <span data-ttu-id="ac24e-237">Benutzer können sich beispielsweise auf das Bearbeiten eines Dokuments, brainstorming mit einem Whiteboard oder das Überprüfen eines Dashboards konzentrieren.</span><span class="sxs-lookup"><span data-stu-id="ac24e-237">For example, users can focus their call on editing a document, brainstorming with a whiteboard, or reviewing a dashboard.</span></span>

<span data-ttu-id="ac24e-238">Für die Besprechungsphase freigegebene Apps belegen den gleichen Platz wie ein freigegebener Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="ac24e-238">Apps shared to the meeting stage occupy the same space as a shared screen.</span></span> <span data-ttu-id="ac24e-239">Die Phase wird für alle Besprechungsteilnehmer neu ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="ac24e-239">The stage reorients for all meeting participants.</span></span>

### <a name="use-cases"></a><span data-ttu-id="ac24e-240">Anwendungsfälle</span><span class="sxs-lookup"><span data-stu-id="ac24e-240">Use cases</span></span>

<span data-ttu-id="ac24e-241">In der gemeinsamen Besprechungsphase geht es um Zusammenarbeit und Teilnahme.</span><span class="sxs-lookup"><span data-stu-id="ac24e-241">The shared meeting stage is all about collaboration and participation.</span></span> <span data-ttu-id="ac24e-242">Hier sind einige Beispielszenarien, die Ihnen bei den ersten Schritten helfen.</span><span class="sxs-lookup"><span data-stu-id="ac24e-242">Here are some example scenarios to help you get started.</span></span>

:::row:::
   :::column span="1":::

<span data-ttu-id="ac24e-243">**Bearbeiten und Überprüfen:** Machen Sie sich mit Dashboards vertraut und planen Sie mit allen Anrufern.</span><span class="sxs-lookup"><span data-stu-id="ac24e-243">**Edit and review**: Dive into dashboards and planning with everyone on the call.</span></span>

   :::column-end:::
   :::column span="3":::

:::image type="content" source="~/assets/images/apps-in-meetings/shared-meeting-stage-edit-review.png" alt-text="Beispiel zeigt ein Dashboard, das in der freigegebenen Besprechungsphase überprüft wird." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="1":::

<span data-ttu-id="ac24e-245">**Whiteboard:** Zeichnen und Zusammenstellen auf einer freigegebenen Canvas.</span><span class="sxs-lookup"><span data-stu-id="ac24e-245">**Whiteboard**: Draw and ideate together on a shared canvas.</span></span>

   :::column-end:::
   :::column span="3":::

:::image type="content" source="~/assets/images/apps-in-meetings/shared-meeting-stage-whiteboard.png" alt-text="Beispiel zeigt ein Whiteboard in der freigegebenen Besprechungsphase." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="1":::

<span data-ttu-id="ac24e-247">**Quiz:** Testen Sie Wissen und gewinnen Sie Einblicke mit interaktiven Materialien.</span><span class="sxs-lookup"><span data-stu-id="ac24e-247">**Quiz**: Test knowledge and gain insights with interactive materials.</span></span>

   :::column-end:::
   :::column span="3":::

:::image type="content" source="~/assets/images/apps-in-meetings/shared-meeting-stage-quiz.png" alt-text="Beispiel zeigt ein Quiz in der phase der freigegebenen Besprechung." border="false":::

   :::column-end:::
:::row-end:::

### <a name="anatomy-shared-meeting-stage"></a><span data-ttu-id="ac24e-249">Anatomie: Gemeinsame Besprechungsphase</span><span class="sxs-lookup"><span data-stu-id="ac24e-249">Anatomy: Shared meeting stage</span></span>

:::image type="content" source="~/assets/images/apps-in-meetings/shared-meeting-stage-anatomy.png" alt-text="Die Abbildung zeigt die Design-Anatomie der freigegebenen Besprechungsphase." border="false":::

|<span data-ttu-id="ac24e-251">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="ac24e-251">Counter</span></span>|<span data-ttu-id="ac24e-252">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ac24e-252">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="ac24e-253">1</span><span class="sxs-lookup"><span data-stu-id="ac24e-253">1</span></span>|<span data-ttu-id="ac24e-254">**App-Symbol:** Das hervorgehobene Symbol gibt an, dass die Registerkarte "In-Meeting" der App geöffnet ist.</span><span class="sxs-lookup"><span data-stu-id="ac24e-254">**App icon**: The highlighted icon indicates the app's in-meeting tab is open.</span></span>|
|<span data-ttu-id="ac24e-255">2 </span><span class="sxs-lookup"><span data-stu-id="ac24e-255">2</span></span>|<span data-ttu-id="ac24e-256">**Schaltfläche "Für Besprechungsphase freigeben":** Der Einstiegspunkt, an dem die App für die Besprechungsphase freigegeben werden soll.</span><span class="sxs-lookup"><span data-stu-id="ac24e-256">**Share to meeting stage button**: The entry point to share the app to the meeting stage.</span></span> <span data-ttu-id="ac24e-257">Zeigt an, ob Sie Ihre App für die Verwendung der freigegebenen Besprechungsphase konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="ac24e-257">Displays if you configure your app to use the shared meeting stage.</span></span>|
|<span data-ttu-id="ac24e-258">3 </span><span class="sxs-lookup"><span data-stu-id="ac24e-258">3</span></span>|<span data-ttu-id="ac24e-259">**iframe:** Zeigt Ihre App-Inhalte an.</span><span class="sxs-lookup"><span data-stu-id="ac24e-259">**iframe**: Displays your app content.</span></span>|
|<span data-ttu-id="ac24e-260">4 </span><span class="sxs-lookup"><span data-stu-id="ac24e-260">4</span></span>|<span data-ttu-id="ac24e-261">**Schaltfläche "Freigabe beenden":** Beendet die Freigabe der App für die Besprechungsphase.</span><span class="sxs-lookup"><span data-stu-id="ac24e-261">**Stop sharing button**: Stops sharing the app to the meeting stage.</span></span> <span data-ttu-id="ac24e-262">Zeigt nur für den Teilnehmer an, der die Freigabe gestartet hat.</span><span class="sxs-lookup"><span data-stu-id="ac24e-262">Displays only for the participant who started the share.</span></span>|
|<span data-ttu-id="ac24e-263">5 </span><span class="sxs-lookup"><span data-stu-id="ac24e-263">5</span></span>|<span data-ttu-id="ac24e-264">**Zuschreibung** des Referenten: Zeigt den Namen des Teilnehmers an, der die App freigegeben hat.</span><span class="sxs-lookup"><span data-stu-id="ac24e-264">**Presenter attribution**: Displays the name of the participant who shared the app.</span></span>|

### <a name="responsive-behavior-shared-meeting-stage"></a><span data-ttu-id="ac24e-265">Reaktionsfähiges Verhalten: Freigegebene Besprechungsphase</span><span class="sxs-lookup"><span data-stu-id="ac24e-265">Responsive behavior: Shared meeting stage</span></span>

<span data-ttu-id="ac24e-266">Apps, die für die Besprechungsphase freigegeben wurden, variieren je nach Größe des Besprechungsstatus und der Größe des Fensters durch den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="ac24e-266">Apps shared to the meeting stage vary in size based on the state of the meeting and how the user resizes the window.</span></span> <span data-ttu-id="ac24e-267">Verwalten Sie den Abstand und das dynamische Layout von Navigation und Steuerelementen genau wie in einem Browser.</span><span class="sxs-lookup"><span data-stu-id="ac24e-267">Maintain padding and the responsive layout of navigation and controls just as you would in a browser.</span></span>

* <span data-ttu-id="ac24e-268">**Seitenbereich:** Ein Benutzer kann den Seitenbereich jederzeit während einer Besprechung öffnen lassen, um zu chatten, die Teilnehmerliste anzuzeigen oder eine App zu verwenden (z. B. die Registerkarte "In-Meeting").</span><span class="sxs-lookup"><span data-stu-id="ac24e-268">**Side panel**: A user can have the side panel open at any time during a meeting to chat, view the roster, or use an app (i.e., in-meeting tab).</span></span> <span data-ttu-id="ac24e-269">Die Phase wird dynamisch neu angeordnet, wenn das Panel geöffnet ist.</span><span class="sxs-lookup"><span data-stu-id="ac24e-269">The stage dynamically rearranges when the panel is open.</span></span>
* <span data-ttu-id="ac24e-270">**Video- und Audioraster:** Das Video- und Audioraster ist immer sichtbar, um Besprechungsteilnehmer anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="ac24e-270">**Video and audio grid**: The video and audio grid is always visible to show meeting participants.</span></span> <span data-ttu-id="ac24e-271">Wenn ein Benutzer eine Person in der Besprechung ins Blickfeld rückt oder anheftet, erhöht dies die Höhe oder Breite des Teilnehmerrasters je nach Ausrichtung.</span><span class="sxs-lookup"><span data-stu-id="ac24e-271">When a user spotlights or pins someone in the meeting, this increases the height or width of the participant grid depending on the orientation.</span></span>

#### <a name="meeting-stage-without-side-panel"></a><span data-ttu-id="ac24e-272">Besprechungsphase (ohne Seitenbereich)</span><span class="sxs-lookup"><span data-stu-id="ac24e-272">Meeting stage (without side panel)</span></span>

<span data-ttu-id="ac24e-273">Wenn der Seitenbereich nicht geöffnet ist, beträgt die Besprechungsphase standardmäßig 994 x 678 Pixel und kann mindestens 792 x 382 Pixel betragen.</span><span class="sxs-lookup"><span data-stu-id="ac24e-273">When the side panel isn't open, the meeting stage is 994x678 pixels by default and can be a minimum 792x382 pixels.</span></span>

:::image type="content" source="~/assets/images/apps-in-meetings/meeting-stage-no-side-panel.png" alt-text="Abbildung der Reaktionsfähigkeit der freigegebenen Besprechungsphase mit geschlossener Seitenleiste." border="false":::

#### <a name="meeting-stage-with-side-panel"></a><span data-ttu-id="ac24e-275">Besprechungsphase (mit Seitenbereich)</span><span class="sxs-lookup"><span data-stu-id="ac24e-275">Meeting stage (with side panel)</span></span>

<span data-ttu-id="ac24e-276">Wenn der Seitenbereich geöffnet ist, beträgt die Besprechungsphase standardmäßig 918 x 540 Pixel und kann mindestens 472 x 382 Pixel betragen.</span><span class="sxs-lookup"><span data-stu-id="ac24e-276">When the side panel is open, the meeting stage is 918x540 pixels by default and can be a minimum 472x382 pixels.</span></span>

:::image type="content" source="~/assets/images/apps-in-meetings/meeting-stage-with-side-panel.png" alt-text="Abbildung der Reaktionsfähigkeit der freigegebenen Besprechungsphase mit geöffneter Seitenleiste." border="false":::

## <a name="after-a-meeting"></a><span data-ttu-id="ac24e-278">Nach einer Besprechung</span><span class="sxs-lookup"><span data-stu-id="ac24e-278">After a meeting</span></span>

<span data-ttu-id="ac24e-279">Sie können zu einer Besprechung zurückkehren, nachdem sie beendet wurde, und App-Inhalte anzeigen.</span><span class="sxs-lookup"><span data-stu-id="ac24e-279">You can go back to a meeting after it ends and view app content.</span></span> <span data-ttu-id="ac24e-280">In diesem Beispiel kann sich der Besprechungsorganisator die Umfrageergebnisse auf der Registerkarte **"Contoso"** ansehen. (Hinweis: Aus Entwurfssicht gibt es keinen Unterschied zwischen der Registerkarte "Vor" und "Nach der Besprechung".)</span><span class="sxs-lookup"><span data-stu-id="ac24e-280">In this example, the meeting organizer can look at poll results in the **Contoso** tab. (Note: From a design standpoint, there's no difference between a the pre- and post-meeting tab experience.)</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/post-meeting-experience.png" alt-text="Die Beispieldarstellung zeigt eine Registerkarte nach der Besprechung." border="false":::

## <a name="best-practices"></a><span data-ttu-id="ac24e-282">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="ac24e-282">Best practices</span></span>

<span data-ttu-id="ac24e-283">Verwenden Sie diese Empfehlungen, um eine hochwertige App-Erfahrung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="ac24e-283">Use these recommendations to create a quality app experience.</span></span>

### <a name="interactions"></a><span data-ttu-id="ac24e-284">Interaktionen</span><span class="sxs-lookup"><span data-stu-id="ac24e-284">Interactions</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-do.png" alt-text="Beispiel, in dem gezeigt wird, wie die Anzahl der Interaktionen begrenzt wird." border="false":::

#### <a name="do-limit-the-number-of-interactions"></a><span data-ttu-id="ac24e-286">Do: Beschränken der Anzahl von Interaktionen</span><span class="sxs-lookup"><span data-stu-id="ac24e-286">Do: Limit the number of interactions</span></span>

<span data-ttu-id="ac24e-287">Entfernen Sie für Besprechungsdialogfelder unnötige Inhalte, die Benutzern nicht helfen, schnell etwas zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="ac24e-287">For in-meeting dialogs, remove unnecessary content that doesn't help users accomplish something quickly.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-dont.png" alt-text="Beispiel, in dem gezeigt wird, wie keine unnötigen Elemente eingeführt werden." border="false":::

#### <a name="dont-introduce-unnecessary-elements"></a><span data-ttu-id="ac24e-289">Nicht empfohlen: Einführen unnötiger Elemente</span><span class="sxs-lookup"><span data-stu-id="ac24e-289">Don't: Introduce unnecessary elements</span></span>

<span data-ttu-id="ac24e-290">Ein einzelnes Besprechungsdialogfeld mit mehreren Interaktionen kann vom Anruf ablenken.</span><span class="sxs-lookup"><span data-stu-id="ac24e-290">A single in-meeting dialog with multiple interactions can distract from the call.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-shared-stage-do.png" alt-text="Beispiel für das Erstellen einer fokussierten Umgebung." border="false":::

#### <a name="do-create-a-focused-environment"></a><span data-ttu-id="ac24e-292">Do: Erstellen einer fokussierten Umgebung</span><span class="sxs-lookup"><span data-stu-id="ac24e-292">Do: Create a focused environment</span></span>

<span data-ttu-id="ac24e-293">Es wird empfohlen, die App-Erfahrung nur auf die Besprechungsphase zu beschränken.</span><span class="sxs-lookup"><span data-stu-id="ac24e-293">We recommend keeping your app’s experience scoped to just the meeting stage.</span></span> <span data-ttu-id="ac24e-294">Sie können eine Besprechungsregisterkarte im Seitenbereich als sekundäre, private Ansicht für bestimmte Szenarien verwenden.</span><span class="sxs-lookup"><span data-stu-id="ac24e-294">You can use an in-meeting tab in the side panel as a secondary, private view for certain scenarios.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-shared-stage-dont.png" alt-text="Beispiel, in dem gezeigt wird, wie sie während Besprechungen keine konkurrierten Oberflächen einschließen." border="false":::

#### <a name="dont-include-competing-surfaces"></a><span data-ttu-id="ac24e-296">Nicht empfohlen: Einschließen von Oberflächen im Wettbewerb</span><span class="sxs-lookup"><span data-stu-id="ac24e-296">Don't: Include competing surfaces</span></span>

<span data-ttu-id="ac24e-297">Ihre App sollte die Benutzer nur auffordern, sich auf eine einzelne Oberfläche zu konzentrieren, unabhängig davon, ob sie auf der Stufe zusammenarbeitet oder auf ein Besprechungsdialogfeld reagiert.</span><span class="sxs-lookup"><span data-stu-id="ac24e-297">Your app should only ask users to focus on a single surface a time, whether it's collaborating on the stage or responding to an in-meeting dialog.</span></span> <span data-ttu-id="ac24e-298">(Hinweis: Dialogfelder, die von anderen Apps ausgelöst werden, können nicht beibehalten werden, während Sich Ihre App auf der Stufe befindet.)</span><span class="sxs-lookup"><span data-stu-id="ac24e-298">(Note: You can’t keep dialogs being triggered by other apps while your app is on the stage.)</span></span> 

   :::column-end:::
:::row-end:::

### <a name="layout"></a><span data-ttu-id="ac24e-299">Layout</span><span class="sxs-lookup"><span data-stu-id="ac24e-299">Layout</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-do.png" alt-text="Beispiel für die Verwendung eines einspaltigen Dialogfeldlayouts." border="false":::

#### <a name="do-use-a-one-column-dialog"></a><span data-ttu-id="ac24e-301">Do: Verwenden eines einspaltigen Dialogfelds</span><span class="sxs-lookup"><span data-stu-id="ac24e-301">Do: Use a one-column dialog</span></span>

<span data-ttu-id="ac24e-302">Da die Dialogfelder im Mittelpunkt der Besprechungsphase stehen, sollte der Aufgabenabschluss schnell und einfach sein, um Benutzerfrustration zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="ac24e-302">Since the dialogs are at the center of the meeting stage, task completion should be fast and simple to avoid user frustration.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-dont.png" alt-text="Beispiel, das zeigt, dass Sie den Raum einer Besprechungserweiterung nicht überladen sollten." border="false":::

#### <a name="dont-clutter-the-space"></a><span data-ttu-id="ac24e-304">Don't: Clutter the space</span><span class="sxs-lookup"><span data-stu-id="ac24e-304">Don't: Clutter the space</span></span>

<span data-ttu-id="ac24e-305">Dichte oder übermäßig strukturierte Inhalte können ablenkend und überwältigend sein, insbesondere während einer Besprechung.</span><span class="sxs-lookup"><span data-stu-id="ac24e-305">Dense or overly structured content can be distracting and overwhelming, especially during a meeting.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-do.png" alt-text="Beispiel für ein einspaltiges Registerkartenlayout." border="false":::

#### <a name="do-use-a-one-column-tab"></a><span data-ttu-id="ac24e-307">Do: Verwenden einer einspaltigen Registerkarte</span><span class="sxs-lookup"><span data-stu-id="ac24e-307">Do: Use a one-column tab</span></span>

<span data-ttu-id="ac24e-308">Angesichts der schmalen Natur der Besprechungsregisterkarte wird dringend empfohlen, den Inhalt in einer einzelnen Spalte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="ac24e-308">Given the in-meeting tab's narrow nature, we strongly recommend displaying the contents in a single column.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-dont.png" alt-text="Beispiel für eine Registerkarte mit mehreren Spalten." border="false":::

#### <a name="dont-use-multiple-columns"></a><span data-ttu-id="ac24e-310">Don't: Use multiple columns</span><span class="sxs-lookup"><span data-stu-id="ac24e-310">Don't: Use multiple columns</span></span>

<span data-ttu-id="ac24e-311">Aufgrund des begrenzten Platzes der Besprechungsregisterkarte werden Layouts mit mehr als einer Spalte nicht empfohlen.</span><span class="sxs-lookup"><span data-stu-id="ac24e-311">Due to the limited space of the in-meeting tab, layouts with more than one column aren’t recommended.</span></span>

   :::column-end:::
:::row-end:::

### <a name="controls"></a><span data-ttu-id="ac24e-312">Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="ac24e-312">Controls</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-do.png" alt-text="Beispiel, das zeigt, wie primäre Steuerelemente rechts ausgerichtet werden." border="false":::

#### <a name="do-right-align-the-primary-action"></a><span data-ttu-id="ac24e-314">Do: Rechtsgündige Ausrichtung der primären Aktion</span><span class="sxs-lookup"><span data-stu-id="ac24e-314">Do: Right align the primary action</span></span>

<span data-ttu-id="ac24e-315">Wir empfehlen, die visuell schwerste Aktion am rechten Ort zu positionieren.</span><span class="sxs-lookup"><span data-stu-id="ac24e-315">We recommend positioning the most visually heavy action to the right-most location.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-dont.png" alt-text="Beispiel, das zeigt, wie Sie primäre Steuerelemente nicht linksbündig ausrichten sollten." border="false":::

#### <a name="dont-left-or-center-align-actions"></a><span data-ttu-id="ac24e-317">Nicht empfohlen: Aktionen links oder zentr werden ausgerichtet</span><span class="sxs-lookup"><span data-stu-id="ac24e-317">Don't: Left or center align actions</span></span>

<span data-ttu-id="ac24e-318">Dies weicht vom standard Teams Muster für die Platzierung von Steuerelementen in einem Dialogfeld ab und kann mit einem Dialogfeld hinter dem oberen Dialogfeld in Konflikt geraten.</span><span class="sxs-lookup"><span data-stu-id="ac24e-318">This deviates from the standard Teams pattern for control placement in a dialog and may conflict with a dialog behind the top one.</span></span>

   :::column-end:::
:::row-end:::

### <a name="scrolling"></a><span data-ttu-id="ac24e-319">Scrollen</span><span class="sxs-lookup"><span data-stu-id="ac24e-319">Scrolling</span></span>

:::row:::
   :::column span="":::

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-do.png" alt-text="Beispiel für den vertikalen Bildlauf auf einer Besprechungsregisterkarte." border="false":::

:::image type="content" source="../../assets/images/apps-in-meetings/shared-meeting-stage-scroll-do.png" alt-text="Beispiel für den vertikalen Bildlauf in der freigegebenen Besprechungsphase." border="false":::

#### <a name="do-scroll-vertically"></a><span data-ttu-id="ac24e-322">Do: Vertikaler Bildlauf</span><span class="sxs-lookup"><span data-stu-id="ac24e-322">Do: Scroll vertically</span></span>

<span data-ttu-id="ac24e-323">Benutzer erwarten vertikalen Bildlauf in Teams (und an anderer Stelle).</span><span class="sxs-lookup"><span data-stu-id="ac24e-323">Users expect vertical scrolling in Teams (and elsewhere).</span></span> <span data-ttu-id="ac24e-324">Dies gilt möglicherweise nicht, wenn Sie über eine kreative Canvas verfügen, z. B. ein Whiteboard, das Benutzer über die X- und Y-Achse schwenken können.</span><span class="sxs-lookup"><span data-stu-id="ac24e-324">This may not apply if you have a creative canvas, such as a whiteboard, which users can pan across the x and y axis.</span></span>

   :::column-end:::
   :::column span="":::

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-dont.png" alt-text="Beispiel für einen horizontalen Bildlauf auf einer Besprechungsregisterkarte." border="false":::

:::image type="content" source="../../assets/images/apps-in-meetings/shared-meeting-stage-scroll-dont.png" alt-text="Beispiel für den horizontalen Bildlauf in der freigegebenen Besprechungsphase." border="false":::

#### <a name="dont-scroll-horizontally"></a><span data-ttu-id="ac24e-327">Nicht ausführen: Horizontaler Bildlauf</span><span class="sxs-lookup"><span data-stu-id="ac24e-327">Don't: Scroll horizontally</span></span>

<span data-ttu-id="ac24e-328">Der horizontale Bildlauf ist kein erwartetes Verhalten in Teams (einschließlich der Besprechungsumgebung).</span><span class="sxs-lookup"><span data-stu-id="ac24e-328">Horizontal scrolling isn’t an expected behavior in Teams (including the meeting environment).</span></span>

   :::column-end:::
:::row-end:::

### <a name="workflows"></a><span data-ttu-id="ac24e-329">Workflows</span><span class="sxs-lookup"><span data-stu-id="ac24e-329">Workflows</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-workflow-do.png" alt-text="Beispiel für ein komplexes Szenario auf einer Besprechungsregisterkarte." border="false":::

#### <a name="do-surface-complex-scenarios-in-the-in-meeting-tab"></a><span data-ttu-id="ac24e-331">Do: Surface complex scenarios in the in-meeting tab</span><span class="sxs-lookup"><span data-stu-id="ac24e-331">Do: Surface complex scenarios in the in-meeting tab</span></span>

<span data-ttu-id="ac24e-332">Wenn Ihre App mehrere Aufgaben enthält, wird dringend empfohlen, eine Besprechungsregisterkarte mit einem einspaltigen Layout zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="ac24e-332">If your app includes multiple tasks, we strongly recommend using an in-meeting tab with a single-column layout.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-workflow-dont.png" alt-text="Beispiel für komplexe Szenarien in einem Besprechungsdialogfeld." border="false":::

#### <a name="dont-make-in-meeting-dialogs-complex"></a><span data-ttu-id="ac24e-334">Nicht empfohlen: In-Meeting-Dialogfelder komplex gestalten</span><span class="sxs-lookup"><span data-stu-id="ac24e-334">Don't: Make in-meeting dialogs complex</span></span>

<span data-ttu-id="ac24e-335">Besprechungsdialogfelder sind für kurze Interaktionen vorgesehen.</span><span class="sxs-lookup"><span data-stu-id="ac24e-335">In-meeting dialogs are intended for brief interactions.</span></span>

   :::column-end:::
:::row-end:::

### <a name="theming"></a><span data-ttu-id="ac24e-336">Design</span><span class="sxs-lookup"><span data-stu-id="ac24e-336">Theming</span></span>

:::row:::
   :::column span="":::

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-do.png" alt-text="Beispiel für eine Besprechungserweiterung mit dem dunklen Design." border="false":::

:::image type="content" source="../../assets/images/apps-in-meetings/shared-meeting-stage-theming-do.png" alt-text="Ein weiteres Beispiel für die Besprechungserweiterung mit dem dunklen Design." border="false":::

#### <a name="do-focus-on-dark-theme"></a><span data-ttu-id="ac24e-339">Do: Fokus auf dunklem Design</span><span class="sxs-lookup"><span data-stu-id="ac24e-339">Do: Focus on dark theme</span></span>

<span data-ttu-id="ac24e-340">Teams Besprechungen sind für dunkles Design optimiert, um visuelles und kognitives Rauschen zu reduzieren, damit sich Benutzer auf die Diskussion und freigegebene Inhalte konzentrieren können.</span><span class="sxs-lookup"><span data-stu-id="ac24e-340">Teams meetings are optimized for dark theme to help reduce visual and cognitive noise so users can focus on the discussion and shared content.</span></span> <span data-ttu-id="ac24e-341">Beachten Sie, dass bestimmte Arten von Apps (z. B. Whiteboarding und Dokumentbearbeitung) keinen dunklen Zeichenbereich benötigen.</span><span class="sxs-lookup"><span data-stu-id="ac24e-341">Keep in mind certain types of apps (such as whiteboarding and document editing) don't need a dark canvas.</span></span>

   :::column-end:::
   :::column span="":::

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-dont.png" alt-text="Beispiel für eine Besprechungserweiterung mit Farben, die nicht mit dem Besprechungsdesign übereinstimmen." border="false":::

:::image type="content" source="../../assets/images/apps-in-meetings/shared-meeting-stage-theming-dont.png" alt-text="Ein weiteres Beispiel für eine Besprechungserweiterung mit Farben, die nicht mit dem Besprechungsdesign übereinstimmen." border="false":::

#### <a name="dont-use-unfamiliar-colors"></a><span data-ttu-id="ac24e-344">Don't: Verwenden Sie unbekannte Farben</span><span class="sxs-lookup"><span data-stu-id="ac24e-344">Don't: Use unfamiliar colors</span></span>

<span data-ttu-id="ac24e-345">Farben, die mit der Besprechungsumgebung in Konflikt stehen, können ablenkend sein und für Teams weniger nativ erscheinen.</span><span class="sxs-lookup"><span data-stu-id="ac24e-345">Colors that clash with the meeting environment may be distracting and appear less native to Teams.</span></span> <span data-ttu-id="ac24e-346">Erfahren Sie mehr über die Teams [Farbhierarchie,](https://developer.microsoft.com/fluentui#/styles/web/colors/products)einschließlich Anrufdesign-Neutralen.</span><span class="sxs-lookup"><span data-stu-id="ac24e-346">Learn about the Teams [color ramp](https://developer.microsoft.com/fluentui#/styles/web/colors/products), including call theme neutrals.</span></span>

   :::column-end:::
:::row-end:::

### <a name="navigation"></a><span data-ttu-id="ac24e-347">Navigation</span><span class="sxs-lookup"><span data-stu-id="ac24e-347">Navigation</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-do.png" alt-text="Beispiel für eine Besprechungserweiterung mit einer Schaltfläche &quot;Zurück&quot;." border="false":::

#### <a name="do-have-a-back-button"></a><span data-ttu-id="ac24e-349">Do: Have a Back button</span><span class="sxs-lookup"><span data-stu-id="ac24e-349">Do: Have a back button</span></span>

<span data-ttu-id="ac24e-350">Wenn Sie auf einer Besprechungsregisterkarte mehr als eine Navigationsebene haben, müssen Benutzer in der Lage sein, zu ihren vorherigen Ansichten zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="ac24e-350">If you have more than one layer of navigation in an in-meeting tab, users must be able to go back to their previous views.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-dont.png" alt-text="Beispiel für eine Besprechungserweiterung mit zwei Schaltflächen zum Schließen." border="false":::

#### <a name="dont-include-another-dismiss-button"></a><span data-ttu-id="ac24e-352">Don't: Include another dismiss button</span><span class="sxs-lookup"><span data-stu-id="ac24e-352">Don't: Include another dismiss button</span></span>

<span data-ttu-id="ac24e-353">Das Bereitstellen einer Option zum Schließen von Besprechungsregisterkarteninhalten kann zu Problemen führen, da bereits eine Schaltfläche in der Kopfzeile vorhanden ist, um die Registerkarte in der Besprechung selbst zu schließen.</span><span class="sxs-lookup"><span data-stu-id="ac24e-353">Providing an option to close in-meeting tab content may cause issues since there’s already a button in the header to dismiss the in-meeting tab itself.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-caution.png" alt-text="Beispiel für modale Elemente (oder Aufgabenmodule) innerhalb einer Besprechungsregisterkarte." border="false":::

#### <a name="caution-avoid-modals-within-the-in-meeting-tab"></a><span data-ttu-id="ac24e-355">Vorsicht: Vermeiden Sie modale Elemente auf der Registerkarte "Besprechung".</span><span class="sxs-lookup"><span data-stu-id="ac24e-355">Caution: Avoid modals within the in-meeting tab</span></span>

<span data-ttu-id="ac24e-356">Modale Elemente (auch als Aufgabenmodule bezeichnet) auf der bereits schmalen Besprechungsregisterkarte können den Inhalt umschließen und verdecken.</span><span class="sxs-lookup"><span data-stu-id="ac24e-356">Modals (also known as task modules) in the already narrow in-meeting tab might wrap and obscure the content.</span></span>

   :::column-end:::
:::row-end:::

### <a name="responsive-behavior"></a><span data-ttu-id="ac24e-357">Dynamisches Verhalten</span><span class="sxs-lookup"><span data-stu-id="ac24e-357">Responsive behavior</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/shared-meeting-stage-responsiveness-do.png" alt-text="Beispiel, das zeigt, wie die Größe einer Besprechungserweiterung ordnungsgemäß angepasst wird." border="false":::

#### <a name="do-resize-and-scale-your-app-responsively"></a><span data-ttu-id="ac24e-359">Gehen Sie vor: Anpassen der Größe und dynamisches Skalieren Ihrer App</span><span class="sxs-lookup"><span data-stu-id="ac24e-359">Do: Resize and scale your app responsively</span></span>

<span data-ttu-id="ac24e-360">App-Inhalte sollten in kleineren Fenstern dynamisch angepasst und verkleinert werden.</span><span class="sxs-lookup"><span data-stu-id="ac24e-360">App content should dynamically resize and condense in smaller windows.</span></span> <span data-ttu-id="ac24e-361">Halten Sie die Hauptnavigation Ihrer App und alle unverankerten Steuerelemente sichtbar.</span><span class="sxs-lookup"><span data-stu-id="ac24e-361">Keep your app’s main navigation and any floating controls visible.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/shared-meeting-stage-responsiveness-dont.png" alt-text="Beispiel, das zeigt, wie die Größe einer Besprechungserweiterung nicht ordnungsgemäß angepasst wird." border="false":::

#### <a name="dont-crop-or-clip-primary-ui-components"></a><span data-ttu-id="ac24e-363">Nicht empfohlen: Zuschneiden oder Beschneiden der primären UI-Komponenten</span><span class="sxs-lookup"><span data-stu-id="ac24e-363">Don't: Crop or clip primary UI components</span></span>

<span data-ttu-id="ac24e-364">Die unverankerte Navigation und Steuerelemente außerhalb des Bildschirms und das Suchen eines Bildlaufs können für Benutzer verwirrend sein.</span><span class="sxs-lookup"><span data-stu-id="ac24e-364">Floating navigation and controls off screen and requiring a scroll to find can be confusing for users.</span></span> <span data-ttu-id="ac24e-365">Ihre App-Inhalte sollten nicht horizontal scrollen, wenn sie nicht in den iframe passen können.</span><span class="sxs-lookup"><span data-stu-id="ac24e-365">Your app content shouldn’t scroll horizontally when it can't fit in the iframe.</span></span>

   :::column-end:::
:::row-end:::

## <a name="next-step"></a><span data-ttu-id="ac24e-366">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="ac24e-366">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ac24e-367">Konfigurieren Ihrer App für Besprechungen</span><span class="sxs-lookup"><span data-stu-id="ac24e-367">Configure your app for meetings</span></span>](~/apps-in-teams-meetings/enable-and-configure-your-app-for-teams-meetings.md)
