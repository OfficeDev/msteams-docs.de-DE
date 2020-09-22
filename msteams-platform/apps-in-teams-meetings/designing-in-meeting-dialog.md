---
title: Entwerfen eines Besprechungs Dialogfelds in Microsoft Teams
author: heath-hamilton
description: Anleitungen und bewährte Methoden für das Entwerfen eines in-Meeting-Dialogs für Microsoft Teams.
ms.author: lajanuar
ms.topic: conceptual
ms.openlocfilehash: 8e9671d8d284311d3d0a299573d3f0e08b195e97
ms.sourcegitcommit: b01986739a05c65094618fbe76aeb53d038b1c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "48178330"
---
# <a name="design-an-in-meeting-dialog"></a><span data-ttu-id="fd9b2-103">Entwerfen eines Besprechungs Dialogfelds</span><span class="sxs-lookup"><span data-stu-id="fd9b2-103">Design an in-meeting dialog</span></span>

<span data-ttu-id="fd9b2-104">In-Meeting-Dialoge werden in der Teams-Besprechungs Phase angezeigt.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-104">In-meeting dialogs display on the Teams meeting stage.</span></span> <span data-ttu-id="fd9b2-105">Sie benötigen Aufmerksamkeit, Bestätigung oder Interaktion eines Benutzers, sind jedoch subtil und unterbrechen die Besprechung nicht.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-105">They require a user's attention, confirmation, or interaction but are subtle and don't interrupt the meeting.</span></span>

## <a name="use-cases"></a><span data-ttu-id="fd9b2-106">Anwendungsfälle</span><span class="sxs-lookup"><span data-stu-id="fd9b2-106">Use cases</span></span>

<span data-ttu-id="fd9b2-107">In-Meeting-Dialogfelder werden von einem Benutzer (wie dem Besprechungsorganisator) ausgelöst, der den Teilnehmern möglicherweise Folgendes wünscht:</span><span class="sxs-lookup"><span data-stu-id="fd9b2-107">In-meeting dialogs are triggered by a user (such as the meeting organizer) who might want participants to:</span></span>

* <span data-ttu-id="fd9b2-108">Kurzes Feedback geben</span><span class="sxs-lookup"><span data-stu-id="fd9b2-108">Provide brief feedback</span></span>
* <span data-ttu-id="fd9b2-109">Eine kurze Umfrage oder Umfrage durchführen</span><span class="sxs-lookup"><span data-stu-id="fd9b2-109">Take a short survey or poll</span></span>
* <span data-ttu-id="fd9b2-110">Übermitteln von Genehmigungen</span><span class="sxs-lookup"><span data-stu-id="fd9b2-110">Submit approvals</span></span>
* <span data-ttu-id="fd9b2-111">Erinnerungen abrufen</span><span class="sxs-lookup"><span data-stu-id="fd9b2-111">Get reminders</span></span>

## <a name="example"></a><span data-ttu-id="fd9b2-112">Beispiel</span><span class="sxs-lookup"><span data-stu-id="fd9b2-112">Example</span></span>

<span data-ttu-id="fd9b2-113">Im folgenden Beispiel wird gezeigt, wie der in-Meeting-Dialog aus der Perspektive eines Besprechungsteilnehmers aussehen könnte.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-113">The following example shows what the in-meeting dialog might look like from a meeting participant's perspective.</span></span> <span data-ttu-id="fd9b2-114">Wie Sie sehen können, sind der Inhalt und die Aufgabe leicht.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-114">As you can see, the content and task are lightweight.</span></span>

:::image type="content" source="../assets/images/calls-and-meetings/in-meeting-dialog-participant-view.png" alt-text="Beispiel zeigt, wie der in-Meeting-Dialog aus der Perspektive eines Besprechungsteilnehmers aussehen könnte.":::

<span data-ttu-id="fd9b2-116"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Das vollständige Szenario anzeigen (Figma)</a></span><span class="sxs-lookup"><span data-stu-id="fd9b2-116"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">See the full scenario (Figma)</a></span></span>

<span data-ttu-id="fd9b2-117"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Siehe andere Beispiele für Anwendungsfälle (Figma)</a></span><span class="sxs-lookup"><span data-stu-id="fd9b2-117"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">See other example use cases (Figma)</a></span></span>

## <a name="anatomy"></a><span data-ttu-id="fd9b2-118">Anatomie</span><span class="sxs-lookup"><span data-stu-id="fd9b2-118">Anatomy</span></span>

:::image type="content" source="../assets/images/calls-and-meetings/in-meeting-dialog-anatomy.png" alt-text="UI-Anatomie einer in-Meeting-Dialogfeldansicht." border="false":::

1. <span data-ttu-id="fd9b2-120">**App-Symbol**</span><span class="sxs-lookup"><span data-stu-id="fd9b2-120">**App icon**</span></span>
1. <span data-ttu-id="fd9b2-121">**App-Name**</span><span class="sxs-lookup"><span data-stu-id="fd9b2-121">**App name**</span></span>
1. <span data-ttu-id="fd9b2-122">**Aktionszeichenfolge**</span><span class="sxs-lookup"><span data-stu-id="fd9b2-122">**Action string**</span></span>
1. <span data-ttu-id="fd9b2-123">**Symbol schließen:** Schließt ein einzelnes Dialogfeld.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-123">**Dismiss icon:** Closes a single dialog.</span></span> <span data-ttu-id="fd9b2-124">Verwenden Sie immer das obere rechte Schließsymbol anstelle einer Aktion in der Fußzeile.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-124">Always use the upper-right close icon instead of an action in the footer.</span></span>
1. <span data-ttu-id="fd9b2-125">**WebView**: zeigt alle Inhalte und Schaltflächen von Drittanbieter-apps an (Standard-Teams-Schaltflächen werden empfohlen).</span><span class="sxs-lookup"><span data-stu-id="fd9b2-125">**Webview**: Displays all third-party app content and buttons (standard Teams buttons recommended).</span></span>

### <a name="sizing"></a><span data-ttu-id="fd9b2-126">Dimensionierung</span><span class="sxs-lookup"><span data-stu-id="fd9b2-126">Sizing</span></span>

<span data-ttu-id="fd9b2-127">In-Meeting-Dialogfelder können in der Größe variieren, um verschiedene Anwendungsfälle zu berücksichtigen, aber Sie müssen stets Abstand und Komponentengröße beibehalten.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-127">In-meeting dialogs can vary in size to account for different use cases, but you must always maintain padding and component sizes.</span></span>

* <span data-ttu-id="fd9b2-128">**Height**: die Höhe des Dialogs wird durch den Inhalt in der WebView bestimmt.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-128">**Height**: The height of the dialog is determined by the content in the webview.</span></span> <span data-ttu-id="fd9b2-129">Der vertikale Bildlauf übernimmt den Inhalt, der die von Ihnen angegebene maximale Höhe überschreitet.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-129">Vertical scroll takes over for content that exceeds the maximum height you specify.</span></span>
* <span data-ttu-id="fd9b2-130">**Width**: die Breite der WebView ist ein absoluter Wert innerhalb des angegebenen Bereichs.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-130">**Width**: The width of the webview is an absolute value within the range you specify.</span></span>

:::image type="content" source="../assets/images/calls-and-meetings/in-meeting-dialog-sizing.png" alt-text="Abbildung mit den möglichen Dimensionen eines in-Meeting-Dialogs. Height: die Höhe des Dialogs wird durch den Inhalt in der WebView bestimmt. Der vertikale Bildlauf übernimmt den Inhalt, der die von Ihnen definierte maximale Höhe überschreitet. Min: keine. Max: 400 Pixel (320 Pixel WebView). Width: die Breite der WebView ist ein absoluter Wert innerhalb des angegebenen Bereichs. Min.: 288 Pixel (256 Pixel WebView). Max: 468 Pixel (436 Pixel WebView)." border="false":::

## <a name="behavior"></a><span data-ttu-id="fd9b2-132">Verhalten</span><span class="sxs-lookup"><span data-stu-id="fd9b2-132">Behavior</span></span>

<span data-ttu-id="fd9b2-133">Weitere Informationen finden Sie unter Allgemeines in-Meeting-Dialog Verhalten wie Rest, laden und vieles mehr in <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Figma</a>.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-133">See general in-meeting dialog behavior, such as rest, loading, and more, in <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Figma</a>.</span></span>

### <a name="position"></a><span data-ttu-id="fd9b2-134">Position</span><span class="sxs-lookup"><span data-stu-id="fd9b2-134">Position</span></span>

<span data-ttu-id="fd9b2-135">In-Meeting-Dialogfelder werden in der Mitte der Besprechungs Phase ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-135">In-meeting dialogs are aligned in the center of the meeting stage.</span></span> <span data-ttu-id="fd9b2-136">Sie können nicht gezogen werden und arbeiten im Rahmen von Microsoft Teams-Benachrichtigungen auf Systemebene.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-136">They can’t be dragged and work within the framework of Teams system-level notifications.</span></span>

:::image type="content" source="../assets/images/calls-and-meetings/in-meeting-dialog-position.png" alt-text="Abbildung der UI-Anatomie eines in-Meeting-Dialogs." border="false":::

### <a name="aggregation"></a><span data-ttu-id="fd9b2-138">Aggregation</span><span class="sxs-lookup"><span data-stu-id="fd9b2-138">Aggregation</span></span>

<span data-ttu-id="fd9b2-139">Es wird jeweils nur ein Dialogfeld angezeigt, wobei das Stapel Ranking von zuletzt bis zuletzt an den unteren Rand gesendet wurde.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-139">Only one dialog displays at a time, stack ranking from last to most recent sent to the bottom.</span></span> <span data-ttu-id="fd9b2-140">Sobald ein Dialogfeld aufgelöst oder entlassen wurde, nimmt der nächste an seiner Stelle an.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-140">Once a dialog is resolved or dismissed, the next one take its place.</span></span>

<span data-ttu-id="fd9b2-141"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Siehe ein Beispiel (Figma)</a></span><span class="sxs-lookup"><span data-stu-id="fd9b2-141"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">See an example (Figma)</a></span></span>

### <a name="scrolling"></a><span data-ttu-id="fd9b2-142">Scrollen</span><span class="sxs-lookup"><span data-stu-id="fd9b2-142">Scrolling</span></span>

<span data-ttu-id="fd9b2-143">Der Bildlauf erfolgt im WebView-Teil eines in-Meeting-Dialogs.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-143">Scrolling occurs in the webview portion of an in-meeting dialog.</span></span> <span data-ttu-id="fd9b2-144">Beachten Sie beim Scrollen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="fd9b2-144">Remember the following about scrolling:</span></span>

* <span data-ttu-id="fd9b2-145">Sie sollten nur vertikal scrollen können.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-145">You should only be able to scroll vertically.</span></span>
* <span data-ttu-id="fd9b2-146">Sie können nur den Inhalt sehen, zu dem Sie einen Bildlauf durchgeführt haben (nichts oberhalb oder unterhalb).</span><span class="sxs-lookup"><span data-stu-id="fd9b2-146">You can only see the content you've scrolled to (nothing above or below).</span></span>

:::image type="content" source="../assets/images/calls-and-meetings/in-meeting-dialog-scroll.png" alt-text="Abbildung zeigt, wie der Bildlauf im WebView-Inhalt im in-Meeting-Dialog funktioniert." border="false":::

### <a name="buttons"></a><span data-ttu-id="fd9b2-148">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="fd9b2-148">Buttons</span></span>

<span data-ttu-id="fd9b2-149">In-Meeting-Dialogfelder sind Teil der WebView ([Siehe einige Beispiele](#best-practices)).</span><span class="sxs-lookup"><span data-stu-id="fd9b2-149">In-meeting dialog buttons are part of the webview ([see some examples](#best-practices)).</span></span>

<span data-ttu-id="fd9b2-150">Im Gegensatz zu ähnlichen Komponenten werden Besprechungs Dialogfelder geschlossen, nachdem ein Benutzer eine Schaltfläche ausgewählt hat.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-150">Unlike similar components, in-meeting dialogs are dismissed once a user selects a button.</span></span>

## <a name="components"></a><span data-ttu-id="fd9b2-151">Komponenten</span><span class="sxs-lookup"><span data-stu-id="fd9b2-151">Components</span></span>

<span data-ttu-id="fd9b2-152">In-Meeting-Dialoge werden in erster Linie mit den folgenden <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">UI-Komponenten (Figma)</a>erstellt, die auf dem <a href="https://fluentsite.z22.web.core.windows.net/" target="_blank">Fluent-Entwurfs System</a>basieren.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-152">In-meeting dialogs are built primarily with the following <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">UI components (Figma)</a>, which are based on the <a href="https://fluentsite.z22.web.core.windows.net/" target="_blank">Fluent Design System</a>.</span></span>

<span data-ttu-id="fd9b2-153">Komponente</span><span class="sxs-lookup"><span data-stu-id="fd9b2-153">Component</span></span> | <span data-ttu-id="fd9b2-154">Anleitungen</span><span class="sxs-lookup"><span data-stu-id="fd9b2-154">Guidelines</span></span> | <span data-ttu-id="fd9b2-155">Beispiel</span><span class="sxs-lookup"><span data-stu-id="fd9b2-155">Example</span></span>
 - | - | -
<span data-ttu-id="fd9b2-156">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="fd9b2-156">Button</span></span> | <span data-ttu-id="fd9b2-157">Primäre und sekundäre Schaltflächen können Mittel oder klein sein</span><span class="sxs-lookup"><span data-stu-id="fd9b2-157">Primary and secondary buttons can be medium or small</span></span> | <span data-ttu-id="fd9b2-158">Senden einer Antwort</span><span class="sxs-lookup"><span data-stu-id="fd9b2-158">Send a response</span></span>
<span data-ttu-id="fd9b2-159">Input</span><span class="sxs-lookup"><span data-stu-id="fd9b2-159">Input</span></span> | <span data-ttu-id="fd9b2-160">Feld für eine kurze Benutzereingabe.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-160">Field for brief user input.</span></span> <span data-ttu-id="fd9b2-161">Bezeichnungstext kann ein Symbol enthalten</span><span class="sxs-lookup"><span data-stu-id="fd9b2-161">Label text can include an icon</span></span>  | <span data-ttu-id="fd9b2-162">Feedback eingeben</span><span class="sxs-lookup"><span data-stu-id="fd9b2-162">Enter feedback</span></span>
<span data-ttu-id="fd9b2-163">Dropdown</span><span class="sxs-lookup"><span data-stu-id="fd9b2-163">Dropdown</span></span> | <span data-ttu-id="fd9b2-164">Wählen Sie eine oder mehrere Optionen aus einer Liste aus.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-164">Select one or more options from a list.</span></span> <span data-ttu-id="fd9b2-165">Kann Such-und Mehrfachauswahl Funktionen umfassen</span><span class="sxs-lookup"><span data-stu-id="fd9b2-165">Can include search and multi-selection features</span></span> | <span data-ttu-id="fd9b2-166">Auswählen einer Sprache</span><span class="sxs-lookup"><span data-stu-id="fd9b2-166">Choose a language</span></span>
<span data-ttu-id="fd9b2-167">Auswahlsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="fd9b2-167">Selection controls</span></span> | <span data-ttu-id="fd9b2-168">Verwenden Sie Kontrollkästchen für mehrere Auswahlmöglichkeiten oder Optionsfelder, und schalten Sie Sie für einzelne Optionen ein.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-168">Use checkboxes for multiple choices or radio buttons and toggles for single choices.</span></span> <span data-ttu-id="fd9b2-169">Für detailliertere Auswahlen verwenden Sie einen Schieberegler</span><span class="sxs-lookup"><span data-stu-id="fd9b2-169">For more detailed selections, use a slider</span></span> | <span data-ttu-id="fd9b2-170">Abstimmung in einer Umfrage</span><span class="sxs-lookup"><span data-stu-id="fd9b2-170">Vote in a poll</span></span>
<span data-ttu-id="fd9b2-171">Warnungen</span><span class="sxs-lookup"><span data-stu-id="fd9b2-171">Alerts</span></span> | <span data-ttu-id="fd9b2-172">Unabhängig davon, ob eine dringende Nachricht, ein Fehlerstatus oder eine Warnung angezeigt wird, die Nachricht sollte kurz sein und die aktuelle Aufgabe des Benutzers nicht unterbrechen.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-172">Whether displaying an urgent message, error state, or warning, the message should be short and won't interrupt the user's current task</span></span> | <span data-ttu-id="fd9b2-173">Anzeigeproblem beim Senden einer Antwort</span><span class="sxs-lookup"><span data-stu-id="fd9b2-173">Display issue when submitting a response</span></span>

## <a name="theming"></a><span data-ttu-id="fd9b2-174">Designs</span><span class="sxs-lookup"><span data-stu-id="fd9b2-174">Theming</span></span>

### <a name="colors"></a><span data-ttu-id="fd9b2-175">Farben</span><span class="sxs-lookup"><span data-stu-id="fd9b2-175">Colors</span></span>

<span data-ttu-id="fd9b2-176">Verwenden Sie das <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Empfohlene Farbschema (Figma)</a> für Hintergründe, vordergrunde und förderzustände.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-176">Use the <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">recommended color scheme (Figma)</a> for backgrounds, foregrounds, and conveying states.</span></span>

### <a name="typography"></a><span data-ttu-id="fd9b2-177">Typografie</span><span class="sxs-lookup"><span data-stu-id="fd9b2-177">Typography</span></span>

<span data-ttu-id="fd9b2-178">Verwenden Sie die <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">empfohlenen Schriftgrößen und-Gewichtungen (Figma)</a> für Titel, Textkörper und metadatentext.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-178">Use the <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">recommended font sizes and weights (Figma)</a> for titles, body text, and metadata text.</span></span>

## <a name="best-practices"></a><span data-ttu-id="fd9b2-179">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="fd9b2-179">Best practices</span></span>

<span data-ttu-id="fd9b2-180">Während in-Meeting-Dialoge Anrufe effektiver gestalten können, können Sie auch Anrufe entgleisen, wenn Sie zu auffällig sind.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-180">While in-meeting dialogs can make calls more effective, they also can derail calls if too obtrusive.</span></span> <span data-ttu-id="fd9b2-181">Im Allgemeinen verwenden Sie die Dialogfelder sparsam, und befolgen Sie diese bewährten Methoden.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-181">In general, use the dialogs sparingly and follow these best practices.</span></span>

### <a name="navigation"></a><span data-ttu-id="fd9b2-182">Navigation</span><span class="sxs-lookup"><span data-stu-id="fd9b2-182">Navigation</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../assets/images/calls-and-meetings/in-meeting-dialog-steps-do.png" alt-text="Abbildung, die zeigt, wie der Inhalt von Besprechungs Dialogen auf einen einzelnen Bildschirm beschränkt wird, damit sich Benutzer auf die Besprechung konzentrieren können." border="false":::

#### <a name="do-keep-it-contained"></a><span data-ttu-id="fd9b2-184">Do: enthalten bleiben</span><span class="sxs-lookup"><span data-stu-id="fd9b2-184">Do: Keep it contained</span></span>

<span data-ttu-id="fd9b2-185">Beschränken Sie den Inhalt von Besprechungs Dialogen auf einen einzelnen Bildschirm, damit sich Benutzer auf die Besprechung konzentrieren können.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-185">Limit in-meeting dialog content to a single screen so users can focus on the meeting.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../assets/images/calls-and-meetings/in-meeting-dialog-steps-dont.png" alt-text="Abbildung zeigt, wie in-Meeting-Dialogfeldern nicht erforderlich ist, dass Benutzer durch Inhalte navigieren." border="false":::

#### <a name="dont-include-multiple-steps"></a><span data-ttu-id="fd9b2-187">Nicht: mehrere Schritte einschließen</span><span class="sxs-lookup"><span data-stu-id="fd9b2-187">Don't: Include multiple steps</span></span>

<span data-ttu-id="fd9b2-188">In-Besprechungs Dialogfelder sollten Benutzer nicht durch Inhalte navigieren müssen.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-188">In-meeting dialogs shouldn't require users to navigate through content.</span></span>

   :::column-end:::
:::row-end:::

### <a name="interactions"></a><span data-ttu-id="fd9b2-189">Interaktionen</span><span class="sxs-lookup"><span data-stu-id="fd9b2-189">Interactions</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../assets/images/calls-and-meetings/in-meeting-dialog-interactions-do.png" alt-text="Abbildung, die zeigt, warum Sie unnötige Inhalte entfernen sollten, die Benutzern nicht dabei helfen, schnell etwas zu erreichen." border="false":::

   :::column-end:::
   :::column span="":::
:::image type="content" source="../assets/images/calls-and-meetings/in-meeting-dialog-interactions-dont.png" alt-text="Eine weitere Abbildung zeigt, warum Sie unnötige Inhalte entfernen sollten, die nicht dazu beitragen, dass Benutzer schnell etwas erreichen." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../assets/images/calls-and-meetings/in-meeting-dialog-tab-do.png" alt-text="Abbildung zeigt, dass Sie, wenn Sie komplexe Interaktionen benötigen, stattdessen eine einzelne Spalte im rechten Bereich der Besprechung verwenden sollten." border="false":::

#### <a name="do-limit-number-of-interactions"></a><span data-ttu-id="fd9b2-193">Do: Begrenzen der Anzahl von Interaktionen</span><span class="sxs-lookup"><span data-stu-id="fd9b2-193">Do: Limit number of interactions</span></span>

<span data-ttu-id="fd9b2-194">Entfernen Sie unnötige Inhalte, die nicht dazu beitragen, dass Benutzer schnell etwas erreichen.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-194">Remove unnecessary content that doesn't help users accomplish something quickly.</span></span> <span data-ttu-id="fd9b2-195">Wenn Sie komplexe Interaktionen benötigen, wird dringend empfohlen, ihre Inhalte stattdessen in einer einzelnen Spalte auf der Registerkarte "in-Meeting" anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-195">If you need complex interactions, we strongly recommend displaying your content using a single column on the in-meeting tab instead.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../assets/images/calls-and-meetings/in-meeting-dialog-tab-dont.png" alt-text="Abbildung zeigt, dass zu viele Interaktionen im Dialogfeld "in-Meeting" von der Besprechung ablenken." border="false":::

#### <a name="dont-introduce-unnecessary-elements"></a><span data-ttu-id="fd9b2-197">Nicht: Einführung unnötiger Elemente</span><span class="sxs-lookup"><span data-stu-id="fd9b2-197">Don't: Introduce unnecessary elements</span></span>

<span data-ttu-id="fd9b2-198">Sie können möglicherweise ein einzelnes Besprechungs Dialogfeld mit mehreren Interaktionen entwerfen, aber zu viele können von der Besprechung ablenken.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-198">You may be able to design a single in-meeting dialog with multiple interactions, but too many can distract from the meeting.</span></span>

   :::column-end:::
:::row-end:::

### <a name="layout"></a><span data-ttu-id="fd9b2-199">Layout</span><span class="sxs-lookup"><span data-stu-id="fd9b2-199">Layout</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../assets/images/calls-and-meetings/in-meeting-dialog-layout-do.png" alt-text="Abbildung mit einem idealen Layout für in-Meeting-Dialoge." border="false":::

#### <a name="do-use-single-column-layouts"></a><span data-ttu-id="fd9b2-201">Do: Verwenden von Einzel Spaltenlayouts</span><span class="sxs-lookup"><span data-stu-id="fd9b2-201">Do: Use single-column layouts</span></span>

<span data-ttu-id="fd9b2-202">Da sich die Dialogfelder in der Mitte der Besprechungs Phase befinden, sollte die Aufgaben Vervollständigung schnell und einfach sein, um Benutzer Frustration zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-202">Since the dialogs are at the center of the meeting stage, task completion should be fast and simple to avoid user frustration.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../assets/images/calls-and-meetings/in-meeting-dialog-layout-dont.png" alt-text="Abbildung mit Layout für in-Besprechungs Dialogfelder, die nicht empfohlen werden." border="false":::

#### <a name="dont-clutter-the-space"></a><span data-ttu-id="fd9b2-204">Nicht: Übersichtlichkeit des Speicherplatzes</span><span class="sxs-lookup"><span data-stu-id="fd9b2-204">Don't: Clutter the space</span></span>

<span data-ttu-id="fd9b2-205">Dichte oder übermäßig strukturierte Inhalte können störend und überwältigend sein, vor allem während einer Besprechung.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-205">Dense or overly structured content can be distracting and overwhelming, especially during a meeting.</span></span>

   :::column-end:::
:::row-end:::

### <a name="size"></a><span data-ttu-id="fd9b2-206">Größe</span><span class="sxs-lookup"><span data-stu-id="fd9b2-206">Size</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../assets/images/calls-and-meetings/in-meeting-dialog-size-do.png" alt-text="Abbildung, die zeigt, wie die Größe des Dialogfelds in der Besprechung immer identisch sein sollte." border="false":::

#### <a name="do-keep-it-consistent"></a><span data-ttu-id="fd9b2-208">Vorgehensweise: konsistent halten</span><span class="sxs-lookup"><span data-stu-id="fd9b2-208">Do: Keep it consistent</span></span>

<span data-ttu-id="fd9b2-209">Dies ist wichtig, da in-Meeting-Dialogfelder immer am gleichen Speicherort angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-209">This is important because in-meeting dialogs always display in the same location.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../assets/images/calls-and-meetings/in-meeting-dialog-size-dont.png" alt-text="Abbildung zeigt, wie Sie nicht unterschiedliche Dialog Größen verwenden sollten." border="false":::

#### <a name="dont-always-fit-to-the-content"></a><span data-ttu-id="fd9b2-211">Nicht: immer an den Inhalt anpassen</span><span class="sxs-lookup"><span data-stu-id="fd9b2-211">Don't: Always fit to the content</span></span>

<span data-ttu-id="fd9b2-212">Möglicherweise versuchen Sie, einen horizontalen Bildlauf zu vermeiden, aber mehrere in-Meeting-Dialog Größen innerhalb derselben App stellen eine inkonsistente Erfahrung dar.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-212">You may be trying to avoid horizontal scrolling, but multiple in-meeting dialog sizes within the same app is an inconsistent experience.</span></span>

   :::column-end:::
:::row-end:::

### <a name="controls"></a><span data-ttu-id="fd9b2-213">Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="fd9b2-213">Controls</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../assets/images/calls-and-meetings/in-meeting-dialog-controls-do.png" alt-text="Illustration, in der die Schaltflächen im Dialogfeld "in-Meeting" platziert werden." border="false":::

#### <a name="do-right-align-the-primary-action"></a><span data-ttu-id="fd9b2-215">Do: Rechtsbündiges Ausrichten der primären Aktion</span><span class="sxs-lookup"><span data-stu-id="fd9b2-215">Do: Right align the primary action</span></span>

<span data-ttu-id="fd9b2-216">Es wird empfohlen, die visuell intensivste Aktion an der am weitesten rechts gelegenen Stelle zu positionieren.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-216">We recommend positioning the most visually heavy action to the right-most location.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../assets/images/calls-and-meetings/in-meeting-dialog-controls-dont.png" alt-text="Illustration, in der die Schaltflächen im Dialogfeld "in-Meeting" nicht platziert werden." border="false":::

#### <a name="dont-left-or-center-align-actions"></a><span data-ttu-id="fd9b2-218">Nicht: Links oder zentrierte Ausrichtungs Aktionen</span><span class="sxs-lookup"><span data-stu-id="fd9b2-218">Don't: Left or center align actions</span></span>

<span data-ttu-id="fd9b2-219">Dies weicht vom standardmäßigen Teams-Muster für die Platzierung von Steuerelementen in einem Dialogfeld ab und kann mit einem Dialogfeld hinter dem oberen Rand in Konflikt stehen.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-219">This deviates from the standard Teams pattern for control placement in a dialog and may conflict with a dialog behind the top one.</span></span>

   :::column-end:::
:::row-end:::

## <a name="accessibility"></a><span data-ttu-id="fd9b2-220">Barrierefreiheit</span><span class="sxs-lookup"><span data-stu-id="fd9b2-220">Accessibility</span></span>

<span data-ttu-id="fd9b2-221">Informationen zur Barrierefreiheit finden Sie unter <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Figma</a>.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-221">For information on accessibility, see <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Figma</a>.</span></span>

## <a name="resources"></a><span data-ttu-id="fd9b2-222">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="fd9b2-222">Resources</span></span>

* <span data-ttu-id="fd9b2-223"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Figma-Datei für Microsoft Teams-Besprechungs Erweiterungen</a></span><span class="sxs-lookup"><span data-stu-id="fd9b2-223"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Microsoft Teams meeting extensions Figma file</a></span></span>

## <a name="validate-your-design"></a><span data-ttu-id="fd9b2-224">Überprüfen des Designs</span><span class="sxs-lookup"><span data-stu-id="fd9b2-224">Validate your design</span></span>

<span data-ttu-id="fd9b2-225">Wenn Sie Ihre APP in AppSource veröffentlichen möchten, sollten Sie sich mit den Entwurfsproblemen vertraut machen, die häufig dazu führen, dass apps während der Übermittlung fehlschlagen.</span><span class="sxs-lookup"><span data-stu-id="fd9b2-225">If you plan to publish your app to AppSource, you should understand the design issues that commonly cause apps to fail during submission.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fd9b2-226">Überprüfen der Entwurfs Validierungsrichtlinien</span><span class="sxs-lookup"><span data-stu-id="fd9b2-226">Check design validation guidelines</span></span>](../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines)
