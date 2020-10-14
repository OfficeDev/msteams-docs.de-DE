---
title: Besprechungs-Dialogfeld entwerfen
author: heath-hamilton
description: Hier erfahren Sie, wie Sie ein in-Meeting-Dialogfeld für Microsoft Teams effektiv entwerfen.
ms.author: lajanuar
ms.topic: conceptual
ms.openlocfilehash: f2ac0df3ce28293d9e3f61f45dd2d460dc01f2e9
ms.sourcegitcommit: d61f14053fc695bc1956bf50e83956613c19ccca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "48452673"
---
# <a name="design-an-in-meeting-dialog"></a><span data-ttu-id="27858-103">Besprechungs-Dialogfeld entwerfen</span><span class="sxs-lookup"><span data-stu-id="27858-103">Design an in-meeting dialog</span></span>

<span data-ttu-id="27858-104">In-Meeting-Dialoge werden in der Teams-Besprechungs Phase angezeigt.</span><span class="sxs-lookup"><span data-stu-id="27858-104">In-meeting dialogs display on the Teams meeting stage.</span></span> <span data-ttu-id="27858-105">Sie benötigen Aufmerksamkeit, Bestätigung oder Interaktion eines Benutzers, sind jedoch subtil und unterbrechen die Besprechung nicht.</span><span class="sxs-lookup"><span data-stu-id="27858-105">They require a user's attention, confirmation, or interaction but are subtle and don't interrupt the meeting.</span></span>

## <a name="use-cases"></a><span data-ttu-id="27858-106">Anwendungsfälle</span><span class="sxs-lookup"><span data-stu-id="27858-106">Use cases</span></span>

<span data-ttu-id="27858-107">In-Meeting-Dialogfelder werden von einem Benutzer (wie dem Besprechungsorganisator) ausgelöst, der den Teilnehmern möglicherweise Folgendes wünscht:</span><span class="sxs-lookup"><span data-stu-id="27858-107">In-meeting dialogs are triggered by a user (such as the meeting organizer) who might want participants to:</span></span>

* <span data-ttu-id="27858-108">Kurzes Feedback geben</span><span class="sxs-lookup"><span data-stu-id="27858-108">Provide brief feedback</span></span>
* <span data-ttu-id="27858-109">Eine kurze Umfrage oder Umfrage durchführen</span><span class="sxs-lookup"><span data-stu-id="27858-109">Take a short survey or poll</span></span>
* <span data-ttu-id="27858-110">Übermitteln von Genehmigungen</span><span class="sxs-lookup"><span data-stu-id="27858-110">Submit approvals</span></span>
* <span data-ttu-id="27858-111">Erinnerungen abrufen</span><span class="sxs-lookup"><span data-stu-id="27858-111">Get reminders</span></span>

## <a name="example"></a><span data-ttu-id="27858-112">Beispiel</span><span class="sxs-lookup"><span data-stu-id="27858-112">Example</span></span>

<span data-ttu-id="27858-113">Im folgenden Beispiel wird gezeigt, wie der in-Meeting-Dialog aus der Perspektive eines Besprechungsteilnehmers aussehen könnte.</span><span class="sxs-lookup"><span data-stu-id="27858-113">The following example shows what the in-meeting dialog might look like from a meeting participant's perspective.</span></span> <span data-ttu-id="27858-114">Wie Sie sehen können, sind der Inhalt und die Aufgabe leicht.</span><span class="sxs-lookup"><span data-stu-id="27858-114">As you can see, the content and task are lightweight.</span></span>

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-participant-view.png" alt-text="Beispiel zeigt, wie der in-Meeting-Dialog aus der Perspektive eines Besprechungsteilnehmers aussehen könnte.":::

<span data-ttu-id="27858-116"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Das vollständige Szenario anzeigen (Figma)</a></span><span class="sxs-lookup"><span data-stu-id="27858-116"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">See the full scenario (Figma)</a></span></span>

<span data-ttu-id="27858-117"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Siehe andere Beispiele für Anwendungsfälle (Figma)</a></span><span class="sxs-lookup"><span data-stu-id="27858-117"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">See other example use cases (Figma)</a></span></span>

## <a name="anatomy"></a><span data-ttu-id="27858-118">Anatomie</span><span class="sxs-lookup"><span data-stu-id="27858-118">Anatomy</span></span>

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-anatomy.png" alt-text="Beispiel zeigt, wie der in-Meeting-Dialog aus der Perspektive eines Besprechungsteilnehmers aussehen könnte." border="false":::

1. <span data-ttu-id="27858-120">**App-Symbol**</span><span class="sxs-lookup"><span data-stu-id="27858-120">**App icon**</span></span>
1. <span data-ttu-id="27858-121">**App-Name**</span><span class="sxs-lookup"><span data-stu-id="27858-121">**App name**</span></span>
1. <span data-ttu-id="27858-122">**Aktionszeichenfolge**</span><span class="sxs-lookup"><span data-stu-id="27858-122">**Action string**</span></span>
1. <span data-ttu-id="27858-123">**Symbol schließen:** Schließt ein einzelnes Dialogfeld.</span><span class="sxs-lookup"><span data-stu-id="27858-123">**Dismiss icon:** Closes a single dialog.</span></span> <span data-ttu-id="27858-124">Verwenden Sie immer das obere rechte Schließsymbol anstelle einer Aktion in der Fußzeile.</span><span class="sxs-lookup"><span data-stu-id="27858-124">Always use the upper-right close icon instead of an action in the footer.</span></span>
1. <span data-ttu-id="27858-125">**WebView**: zeigt alle Inhalte und Schaltflächen von Drittanbieter-apps an (Standard-Teams-Schaltflächen werden empfohlen).</span><span class="sxs-lookup"><span data-stu-id="27858-125">**Webview**: Displays all third-party app content and buttons (standard Teams buttons recommended).</span></span>

### <a name="sizing"></a><span data-ttu-id="27858-126">Dimensionierung</span><span class="sxs-lookup"><span data-stu-id="27858-126">Sizing</span></span>

<span data-ttu-id="27858-127">In-Meeting-Dialogfelder können in der Größe variieren, um verschiedene Anwendungsfälle zu berücksichtigen, aber Sie müssen stets Abstand und Komponentengröße beibehalten.</span><span class="sxs-lookup"><span data-stu-id="27858-127">In-meeting dialogs can vary in size to account for different use cases, but you must always maintain padding and component sizes.</span></span>

* <span data-ttu-id="27858-128">**Height**: die Höhe des Dialogs wird durch den Inhalt in der WebView bestimmt.</span><span class="sxs-lookup"><span data-stu-id="27858-128">**Height**: The height of the dialog is determined by the content in the webview.</span></span> <span data-ttu-id="27858-129">Der vertikale Bildlauf übernimmt den Inhalt, der die von Ihnen angegebene maximale Höhe überschreitet.</span><span class="sxs-lookup"><span data-stu-id="27858-129">Vertical scroll takes over for content that exceeds the maximum height you specify.</span></span>
* <span data-ttu-id="27858-130">**Width**: die Breite der WebView ist ein absoluter Wert innerhalb des angegebenen Bereichs.</span><span class="sxs-lookup"><span data-stu-id="27858-130">**Width**: The width of the webview is an absolute value within the range you specify.</span></span>

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-sizing.png" alt-text="Beispiel zeigt, wie der in-Meeting-Dialog aus der Perspektive eines Besprechungsteilnehmers aussehen könnte." border="false":::

## <a name="behavior"></a><span data-ttu-id="27858-132">Verhalten</span><span class="sxs-lookup"><span data-stu-id="27858-132">Behavior</span></span>

<span data-ttu-id="27858-133">Weitere Informationen finden Sie unter Allgemeines in-Meeting-Dialog Verhalten wie Rest, laden und vieles mehr in <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Figma</a>.</span><span class="sxs-lookup"><span data-stu-id="27858-133">See general in-meeting dialog behavior, such as rest, loading, and more, in <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Figma</a>.</span></span>

### <a name="position"></a><span data-ttu-id="27858-134">Position</span><span class="sxs-lookup"><span data-stu-id="27858-134">Position</span></span>

<span data-ttu-id="27858-135">In-Meeting-Dialogfelder werden in der Mitte der Besprechungs Phase ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="27858-135">In-meeting dialogs are aligned in the center of the meeting stage.</span></span> <span data-ttu-id="27858-136">Sie können nicht gezogen werden und arbeiten im Rahmen von Microsoft Teams-Benachrichtigungen auf Systemebene.</span><span class="sxs-lookup"><span data-stu-id="27858-136">They can’t be dragged and work within the framework of Teams system-level notifications.</span></span>

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-position.png" alt-text="Beispiel zeigt, wie der in-Meeting-Dialog aus der Perspektive eines Besprechungsteilnehmers aussehen könnte." border="false":::

### <a name="aggregation"></a><span data-ttu-id="27858-138">Aggregation</span><span class="sxs-lookup"><span data-stu-id="27858-138">Aggregation</span></span>

<span data-ttu-id="27858-139">Es wird jeweils nur ein Dialogfeld angezeigt, wobei das Stapel Ranking von zuletzt bis zuletzt an den unteren Rand gesendet wurde.</span><span class="sxs-lookup"><span data-stu-id="27858-139">Only one dialog displays at a time, stack ranking from last to most recent sent to the bottom.</span></span> <span data-ttu-id="27858-140">Sobald ein Dialogfeld aufgelöst oder entlassen wurde, nimmt der nächste an seiner Stelle an.</span><span class="sxs-lookup"><span data-stu-id="27858-140">Once a dialog is resolved or dismissed, the next one take its place.</span></span>

<span data-ttu-id="27858-141"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Siehe ein Beispiel (Figma)</a></span><span class="sxs-lookup"><span data-stu-id="27858-141"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">See an example (Figma)</a></span></span>

### <a name="scrolling"></a><span data-ttu-id="27858-142">Scrollen</span><span class="sxs-lookup"><span data-stu-id="27858-142">Scrolling</span></span>

<span data-ttu-id="27858-143">Der Bildlauf erfolgt im WebView-Teil eines in-Meeting-Dialogs.</span><span class="sxs-lookup"><span data-stu-id="27858-143">Scrolling occurs in the webview portion of an in-meeting dialog.</span></span> <span data-ttu-id="27858-144">Beachten Sie beim Scrollen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="27858-144">Remember the following about scrolling:</span></span>

* <span data-ttu-id="27858-145">Sie sollten nur vertikal scrollen können.</span><span class="sxs-lookup"><span data-stu-id="27858-145">You should only be able to scroll vertically.</span></span>
* <span data-ttu-id="27858-146">Sie können nur den Inhalt sehen, zu dem Sie einen Bildlauf durchgeführt haben (nichts oberhalb oder unterhalb).</span><span class="sxs-lookup"><span data-stu-id="27858-146">You can only see the content you've scrolled to (nothing above or below).</span></span>

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-scroll.png" alt-text="Beispiel zeigt, wie der in-Meeting-Dialog aus der Perspektive eines Besprechungsteilnehmers aussehen könnte." border="false":::

### <a name="buttons"></a><span data-ttu-id="27858-148">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="27858-148">Buttons</span></span>

<span data-ttu-id="27858-149">In-Meeting-Dialogfelder sind Teil der WebView ([Siehe einige Beispiele](#best-practices)).</span><span class="sxs-lookup"><span data-stu-id="27858-149">In-meeting dialog buttons are part of the webview ([see some examples](#best-practices)).</span></span>

<span data-ttu-id="27858-150">Im Gegensatz zu ähnlichen Komponenten werden Besprechungs Dialogfelder geschlossen, nachdem ein Benutzer eine Schaltfläche ausgewählt hat.</span><span class="sxs-lookup"><span data-stu-id="27858-150">Unlike similar components, in-meeting dialogs are dismissed once a user selects a button.</span></span>

## <a name="components"></a><span data-ttu-id="27858-151">Komponenten</span><span class="sxs-lookup"><span data-stu-id="27858-151">Components</span></span>

<span data-ttu-id="27858-152">In-Meeting-Dialoge werden in erster Linie mit den folgenden <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">UI-Komponenten (Figma)</a>erstellt, die auf dem <a href="https://fluentsite.z22.web.core.windows.net/" target="_blank">Fluent-Entwurfs System</a>basieren.</span><span class="sxs-lookup"><span data-stu-id="27858-152">In-meeting dialogs are built primarily with the following <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">UI components (Figma)</a>, which are based on the <a href="https://fluentsite.z22.web.core.windows.net/" target="_blank">Fluent Design System</a>.</span></span>

<span data-ttu-id="27858-153">Komponente</span><span class="sxs-lookup"><span data-stu-id="27858-153">Component</span></span> | <span data-ttu-id="27858-154">Anleitungen</span><span class="sxs-lookup"><span data-stu-id="27858-154">Guidelines</span></span> | <span data-ttu-id="27858-155">Beispiel</span><span class="sxs-lookup"><span data-stu-id="27858-155">Example</span></span>
 - | - | -
<span data-ttu-id="27858-156">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="27858-156">Button</span></span> | <span data-ttu-id="27858-157">Primäre und sekundäre Schaltflächen können Mittel oder klein sein</span><span class="sxs-lookup"><span data-stu-id="27858-157">Primary and secondary buttons can be medium or small</span></span> | <span data-ttu-id="27858-158">Senden einer Antwort</span><span class="sxs-lookup"><span data-stu-id="27858-158">Send a response</span></span>
<span data-ttu-id="27858-159">Input</span><span class="sxs-lookup"><span data-stu-id="27858-159">Input</span></span> | <span data-ttu-id="27858-160">Feld für eine kurze Benutzereingabe.</span><span class="sxs-lookup"><span data-stu-id="27858-160">Field for brief user input.</span></span> <span data-ttu-id="27858-161">Bezeichnungstext kann ein Symbol enthalten</span><span class="sxs-lookup"><span data-stu-id="27858-161">Label text can include an icon</span></span>  | <span data-ttu-id="27858-162">Feedback eingeben</span><span class="sxs-lookup"><span data-stu-id="27858-162">Enter feedback</span></span>
<span data-ttu-id="27858-163">Dropdown</span><span class="sxs-lookup"><span data-stu-id="27858-163">Dropdown</span></span> | <span data-ttu-id="27858-164">Wählen Sie eine oder mehrere Optionen aus einer Liste aus.</span><span class="sxs-lookup"><span data-stu-id="27858-164">Select one or more options from a list.</span></span> <span data-ttu-id="27858-165">Kann Such-und Mehrfachauswahl Funktionen umfassen</span><span class="sxs-lookup"><span data-stu-id="27858-165">Can include search and multi-selection features</span></span> | <span data-ttu-id="27858-166">Auswählen einer Sprache</span><span class="sxs-lookup"><span data-stu-id="27858-166">Choose a language</span></span>
<span data-ttu-id="27858-167">Auswahlsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="27858-167">Selection controls</span></span> | <span data-ttu-id="27858-168">Verwenden Sie Kontrollkästchen für mehrere Auswahlmöglichkeiten oder Optionsfelder, und schalten Sie Sie für einzelne Optionen ein.</span><span class="sxs-lookup"><span data-stu-id="27858-168">Use checkboxes for multiple choices or radio buttons and toggles for single choices.</span></span> <span data-ttu-id="27858-169">Für detailliertere Auswahlen verwenden Sie einen Schieberegler</span><span class="sxs-lookup"><span data-stu-id="27858-169">For more detailed selections, use a slider</span></span> | <span data-ttu-id="27858-170">Abstimmung in einer Umfrage</span><span class="sxs-lookup"><span data-stu-id="27858-170">Vote in a poll</span></span>
<span data-ttu-id="27858-171">Warnungen</span><span class="sxs-lookup"><span data-stu-id="27858-171">Alerts</span></span> | <span data-ttu-id="27858-172">Unabhängig davon, ob eine dringende Nachricht, ein Fehlerstatus oder eine Warnung angezeigt wird, die Nachricht sollte kurz sein und die aktuelle Aufgabe des Benutzers nicht unterbrechen.</span><span class="sxs-lookup"><span data-stu-id="27858-172">Whether displaying an urgent message, error state, or warning, the message should be short and won't interrupt the user's current task</span></span> | <span data-ttu-id="27858-173">Anzeigeproblem beim Senden einer Antwort</span><span class="sxs-lookup"><span data-stu-id="27858-173">Display issue when submitting a response</span></span>

## <a name="theming"></a><span data-ttu-id="27858-174">Designs</span><span class="sxs-lookup"><span data-stu-id="27858-174">Theming</span></span>

### <a name="colors"></a><span data-ttu-id="27858-175">Farben</span><span class="sxs-lookup"><span data-stu-id="27858-175">Colors</span></span>

<span data-ttu-id="27858-176">Verwenden Sie das <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Empfohlene Farbschema (Figma)</a> für Hintergründe, vordergrunde und förderzustände.</span><span class="sxs-lookup"><span data-stu-id="27858-176">Use the <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">recommended color scheme (Figma)</a> for backgrounds, foregrounds, and conveying states.</span></span>

### <a name="typography"></a><span data-ttu-id="27858-177">Typografie</span><span class="sxs-lookup"><span data-stu-id="27858-177">Typography</span></span>

<span data-ttu-id="27858-178">Verwenden Sie die <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">empfohlenen Schriftgrößen und-Gewichtungen (Figma)</a> für Titel, Textkörper und metadatentext.</span><span class="sxs-lookup"><span data-stu-id="27858-178">Use the <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">recommended font sizes and weights (Figma)</a> for titles, body text, and metadata text.</span></span>

## <a name="best-practices"></a><span data-ttu-id="27858-179">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="27858-179">Best practices</span></span>

<span data-ttu-id="27858-180">Während in-Meeting-Dialoge Anrufe effektiver gestalten können, können Sie auch Anrufe entgleisen, wenn Sie zu auffällig sind.</span><span class="sxs-lookup"><span data-stu-id="27858-180">While in-meeting dialogs can make calls more effective, they also can derail calls if too obtrusive.</span></span> <span data-ttu-id="27858-181">Im Allgemeinen verwenden Sie die Dialogfelder sparsam, und befolgen Sie diese bewährten Methoden.</span><span class="sxs-lookup"><span data-stu-id="27858-181">In general, use the dialogs sparingly and follow these best practices.</span></span>

### <a name="navigation"></a><span data-ttu-id="27858-182">Navigation</span><span class="sxs-lookup"><span data-stu-id="27858-182">Navigation</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-steps-do.png" alt-text="Beispiel zeigt, wie der in-Meeting-Dialog aus der Perspektive eines Besprechungsteilnehmers aussehen könnte." border="false":::

#### <a name="do-keep-it-contained"></a><span data-ttu-id="27858-184">Do: enthalten bleiben</span><span class="sxs-lookup"><span data-stu-id="27858-184">Do: Keep it contained</span></span>

<span data-ttu-id="27858-185">Beschränken Sie den Inhalt von Besprechungs Dialogen auf einen einzelnen Bildschirm, damit sich Benutzer auf die Besprechung konzentrieren können.</span><span class="sxs-lookup"><span data-stu-id="27858-185">Limit in-meeting dialog content to a single screen so users can focus on the meeting.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-steps-dont.png" alt-text="Beispiel zeigt, wie der in-Meeting-Dialog aus der Perspektive eines Besprechungsteilnehmers aussehen könnte." border="false":::

#### <a name="dont-include-multiple-steps"></a><span data-ttu-id="27858-187">Nicht: mehrere Schritte einschließen</span><span class="sxs-lookup"><span data-stu-id="27858-187">Don't: Include multiple steps</span></span>

<span data-ttu-id="27858-188">In-Besprechungs Dialogfelder sollten Benutzer nicht durch Inhalte navigieren müssen.</span><span class="sxs-lookup"><span data-stu-id="27858-188">In-meeting dialogs shouldn't require users to navigate through content.</span></span>

   :::column-end:::
:::row-end:::

### <a name="interactions"></a><span data-ttu-id="27858-189">Interaktionen</span><span class="sxs-lookup"><span data-stu-id="27858-189">Interactions</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-interactions-do.png" alt-text="Beispiel zeigt, wie der in-Meeting-Dialog aus der Perspektive eines Besprechungsteilnehmers aussehen könnte." border="false":::

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-interactions-dont.png" alt-text="Beispiel zeigt, wie der in-Meeting-Dialog aus der Perspektive eines Besprechungsteilnehmers aussehen könnte." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-tab-do.png" alt-text="Beispiel zeigt, wie der in-Meeting-Dialog aus der Perspektive eines Besprechungsteilnehmers aussehen könnte." border="false":::

#### <a name="do-limit-number-of-interactions"></a><span data-ttu-id="27858-193">Do: Begrenzen der Anzahl von Interaktionen</span><span class="sxs-lookup"><span data-stu-id="27858-193">Do: Limit number of interactions</span></span>

<span data-ttu-id="27858-194">Entfernen Sie unnötige Inhalte, die nicht dazu beitragen, dass Benutzer schnell etwas erreichen.</span><span class="sxs-lookup"><span data-stu-id="27858-194">Remove unnecessary content that doesn't help users accomplish something quickly.</span></span> <span data-ttu-id="27858-195">Wenn Sie komplexe Interaktionen benötigen, wird dringend empfohlen, ihre Inhalte stattdessen in einer einzelnen Spalte auf der Registerkarte "in-Meeting" anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="27858-195">If you need complex interactions, we strongly recommend displaying your content using a single column on the in-meeting tab instead.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-tab-dont.png" alt-text="Beispiel zeigt, wie der in-Meeting-Dialog aus der Perspektive eines Besprechungsteilnehmers aussehen könnte." border="false":::

#### <a name="dont-introduce-unnecessary-elements"></a><span data-ttu-id="27858-197">Nicht: Einführung unnötiger Elemente</span><span class="sxs-lookup"><span data-stu-id="27858-197">Don't: Introduce unnecessary elements</span></span>

<span data-ttu-id="27858-198">Sie können möglicherweise ein einzelnes Besprechungs Dialogfeld mit mehreren Interaktionen entwerfen, aber zu viele können von der Besprechung ablenken.</span><span class="sxs-lookup"><span data-stu-id="27858-198">You may be able to design a single in-meeting dialog with multiple interactions, but too many can distract from the meeting.</span></span>

   :::column-end:::
:::row-end:::

### <a name="layout"></a><span data-ttu-id="27858-199">Layout</span><span class="sxs-lookup"><span data-stu-id="27858-199">Layout</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-layout-do.png" alt-text="Beispiel zeigt, wie der in-Meeting-Dialog aus der Perspektive eines Besprechungsteilnehmers aussehen könnte." border="false":::

#### <a name="do-use-single-column-layouts"></a><span data-ttu-id="27858-201">Do: Verwenden von Einzel Spaltenlayouts</span><span class="sxs-lookup"><span data-stu-id="27858-201">Do: Use single-column layouts</span></span>

<span data-ttu-id="27858-202">Da sich die Dialogfelder in der Mitte der Besprechungs Phase befinden, sollte die Aufgaben Vervollständigung schnell und einfach sein, um Benutzer Frustration zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="27858-202">Since the dialogs are at the center of the meeting stage, task completion should be fast and simple to avoid user frustration.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-layout-dont.png" alt-text="Beispiel zeigt, wie der in-Meeting-Dialog aus der Perspektive eines Besprechungsteilnehmers aussehen könnte." border="false":::

#### <a name="dont-clutter-the-space"></a><span data-ttu-id="27858-204">Nicht: Übersichtlichkeit des Speicherplatzes</span><span class="sxs-lookup"><span data-stu-id="27858-204">Don't: Clutter the space</span></span>

<span data-ttu-id="27858-205">Dichte oder übermäßig strukturierte Inhalte können störend und überwältigend sein, vor allem während einer Besprechung.</span><span class="sxs-lookup"><span data-stu-id="27858-205">Dense or overly structured content can be distracting and overwhelming, especially during a meeting.</span></span>

   :::column-end:::
:::row-end:::

### <a name="size"></a><span data-ttu-id="27858-206">Größe</span><span class="sxs-lookup"><span data-stu-id="27858-206">Size</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-size-do.png" alt-text="Beispiel zeigt, wie der in-Meeting-Dialog aus der Perspektive eines Besprechungsteilnehmers aussehen könnte." border="false":::

#### <a name="do-keep-it-consistent"></a><span data-ttu-id="27858-208">Vorgehensweise: konsistent halten</span><span class="sxs-lookup"><span data-stu-id="27858-208">Do: Keep it consistent</span></span>

<span data-ttu-id="27858-209">Dies ist wichtig, da in-Meeting-Dialogfelder immer am gleichen Speicherort angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="27858-209">This is important because in-meeting dialogs always display in the same location.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-size-dont.png" alt-text="Beispiel zeigt, wie der in-Meeting-Dialog aus der Perspektive eines Besprechungsteilnehmers aussehen könnte." border="false":::

#### <a name="dont-always-fit-to-the-content"></a><span data-ttu-id="27858-211">Nicht: immer an den Inhalt anpassen</span><span class="sxs-lookup"><span data-stu-id="27858-211">Don't: Always fit to the content</span></span>

<span data-ttu-id="27858-212">Möglicherweise versuchen Sie, einen horizontalen Bildlauf zu vermeiden, aber mehrere in-Meeting-Dialog Größen innerhalb derselben App stellen eine inkonsistente Erfahrung dar.</span><span class="sxs-lookup"><span data-stu-id="27858-212">You may be trying to avoid horizontal scrolling, but multiple in-meeting dialog sizes within the same app is an inconsistent experience.</span></span>

   :::column-end:::
:::row-end:::

### <a name="controls"></a><span data-ttu-id="27858-213">Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="27858-213">Controls</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-controls-do.png" alt-text="Beispiel zeigt, wie der in-Meeting-Dialog aus der Perspektive eines Besprechungsteilnehmers aussehen könnte." border="false":::

#### <a name="do-right-align-the-primary-action"></a><span data-ttu-id="27858-215">Do: Rechtsbündiges Ausrichten der primären Aktion</span><span class="sxs-lookup"><span data-stu-id="27858-215">Do: Right align the primary action</span></span>

<span data-ttu-id="27858-216">Es wird empfohlen, die visuell intensivste Aktion an der am weitesten rechts gelegenen Stelle zu positionieren.</span><span class="sxs-lookup"><span data-stu-id="27858-216">We recommend positioning the most visually heavy action to the right-most location.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-controls-dont.png" alt-text="Beispiel zeigt, wie der in-Meeting-Dialog aus der Perspektive eines Besprechungsteilnehmers aussehen könnte." border="false":::

#### <a name="dont-left-or-center-align-actions"></a><span data-ttu-id="27858-218">Nicht: Links oder zentrierte Ausrichtungs Aktionen</span><span class="sxs-lookup"><span data-stu-id="27858-218">Don't: Left or center align actions</span></span>

<span data-ttu-id="27858-219">Dies weicht vom standardmäßigen Teams-Muster für die Platzierung von Steuerelementen in einem Dialogfeld ab und kann mit einem Dialogfeld hinter dem oberen Rand in Konflikt stehen.</span><span class="sxs-lookup"><span data-stu-id="27858-219">This deviates from the standard Teams pattern for control placement in a dialog and may conflict with a dialog behind the top one.</span></span>

   :::column-end:::
:::row-end:::

## <a name="accessibility"></a><span data-ttu-id="27858-220">Barrierefreiheit</span><span class="sxs-lookup"><span data-stu-id="27858-220">Accessibility</span></span>

<span data-ttu-id="27858-221">Informationen zur Barrierefreiheit finden Sie unter <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Figma</a>.</span><span class="sxs-lookup"><span data-stu-id="27858-221">For information on accessibility, see <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Figma</a>.</span></span>

## <a name="resources"></a><span data-ttu-id="27858-222">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="27858-222">Resources</span></span>

* <span data-ttu-id="27858-223"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Figma-Datei für Microsoft Teams-Besprechungs Erweiterungen</a></span><span class="sxs-lookup"><span data-stu-id="27858-223"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Microsoft Teams meeting extensions Figma file</a></span></span>

## <a name="validate-your-design"></a><span data-ttu-id="27858-224">Überprüfen des Designs</span><span class="sxs-lookup"><span data-stu-id="27858-224">Validate your design</span></span>

<span data-ttu-id="27858-225">Wenn Sie Ihre APP in AppSource veröffentlichen möchten, sollten Sie sich mit den Entwurfsproblemen vertraut machen, die häufig dazu führen, dass apps während der Übermittlung fehlschlagen.</span><span class="sxs-lookup"><span data-stu-id="27858-225">If you plan to publish your app to AppSource, you should understand the design issues that commonly cause apps to fail during submission.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="27858-226">Überprüfen der Entwurfs Validierungsrichtlinien</span><span class="sxs-lookup"><span data-stu-id="27858-226">Check design validation guidelines</span></span>](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines)
