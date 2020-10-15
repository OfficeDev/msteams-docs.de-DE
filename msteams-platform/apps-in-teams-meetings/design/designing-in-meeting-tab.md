---
title: Besprechungs-Registerkarte entwerfen
author: heath-hamilton
description: Hier erfahren Sie, wie Sie eine in-Meeting-Registerkarte für Microsoft Teams effektiv entwerfen.
ms.author: lajanuar
ms.topic: conceptual
ms.openlocfilehash: a5c4d0cc0d2c61f422ea9bc189f164d02b28aae0
ms.sourcegitcommit: d61f14053fc695bc1956bf50e83956613c19ccca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "48452659"
---
# <a name="design-an-in-meeting-tab"></a><span data-ttu-id="d2b0e-103">Besprechungs-Registerkarte entwerfen</span><span class="sxs-lookup"><span data-stu-id="d2b0e-103">Design an in-meeting tab</span></span>

<span data-ttu-id="d2b0e-104">Die Registerkarte in-Meeting ist eine Arbeitsfläche zum Erweitern der Zusammenarbeit während Besprechungen.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-104">The in-meeting tab is a canvas for augmenting collaboration during meetings.</span></span> <span data-ttu-id="d2b0e-105">Basierend auf den registerkartenfunktionen von Teams können Teilnehmer App-Inhalte in einem dedizierten Raum außerhalb der Besprechungs Phase über freigegebene oder rollenbasierte Ansichten anzeigen und interagieren.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-105">Based on the Teams tab capability, attendees can see and interact with app content in a dedicated space outside the meeting stage through shared or role-based views.</span></span>

## <a name="use-cases"></a><span data-ttu-id="d2b0e-106">Anwendungsfälle</span><span class="sxs-lookup"><span data-stu-id="d2b0e-106">Use cases</span></span>

<span data-ttu-id="d2b0e-107">Die Registerkarte "in-Meeting" wird von den Benutzern möglicherweise verwendet:</span><span class="sxs-lookup"><span data-stu-id="d2b0e-107">People might use the in-meeting tab to:</span></span>

* <span data-ttu-id="d2b0e-108">Bereitstellen eines detaillierten Feedbacks (zum Beispiel Auswerten eines Bewerbers)</span><span class="sxs-lookup"><span data-stu-id="d2b0e-108">Provide detailed feedback (for example, evaluate a job candidate)</span></span>
* <span data-ttu-id="d2b0e-109">Schnelles Erstellen einer Umfrage, Umfrage oder eines Aufgabenelements für die Besprechungsteilnehmer</span><span class="sxs-lookup"><span data-stu-id="d2b0e-109">Quickly create a poll, survey, or task item for the meeting participants</span></span>
* <span data-ttu-id="d2b0e-110">Anzeigen von Notizen, die für die Besprechung relevant sind (beispielsweise Informationen zu einem Verkaufsleiter)</span><span class="sxs-lookup"><span data-stu-id="d2b0e-110">Display notes relevant to the meeting (for example, information about a sales lead)</span></span>

## <a name="example"></a><span data-ttu-id="d2b0e-111">Beispiel</span><span class="sxs-lookup"><span data-stu-id="d2b0e-111">Example</span></span>

<span data-ttu-id="d2b0e-112">Das folgende Beispiel zeigt die Registerkarte in der Besprechung, in der Umfrage-App-Inhalte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-112">The following example shows the in-meeting tab displaying survey app content.</span></span>

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-organizer-view.png" alt-text="Das Beispiel zeigt, wie die Registerkarte Besprechung in der Besprechung aus der Perspektive eines Besprechungsorganisators aussehen könnte.":::

<span data-ttu-id="d2b0e-114"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Das vollständige Szenario anzeigen (Figma)</a></span><span class="sxs-lookup"><span data-stu-id="d2b0e-114"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">See the full scenario (Figma)</a></span></span>

<span data-ttu-id="d2b0e-115"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Siehe andere Beispiele für Anwendungsfälle (Figma)</a></span><span class="sxs-lookup"><span data-stu-id="d2b0e-115"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">See other example use cases (Figma)</a></span></span>

## <a name="anatomy"></a><span data-ttu-id="d2b0e-116">Anatomie</span><span class="sxs-lookup"><span data-stu-id="d2b0e-116">Anatomy</span></span>

<span data-ttu-id="d2b0e-117">Auf der Registerkarte in-Meeting werden Ihre APP-Inhalte mit den folgenden Dimensionen angezeigt:</span><span class="sxs-lookup"><span data-stu-id="d2b0e-117">The in-meeting tab displays your app content using the following dimensions:</span></span>

* <span data-ttu-id="d2b0e-118">**Breite**: 280 Pixel für den WebView-Bereich.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-118">**Width**: 280 pixels for the webview area.</span></span> <span data-ttu-id="d2b0e-119">Auf der linken und rechten Seite des Webviews befinden sich 20 Pixel Textabstand.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-119">There are 20 pixels of padding on the left and right sides of the webview.</span></span>
* <span data-ttu-id="d2b0e-120">**Höhe**: vollständiges Anfärben am unteren Rand der Registerkarte. Zwischen dem WebView-Bereich und der Registerkartenüberschrift befinden sich 20 Pixelabstand.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-120">**Height**: Full bleed to the bottom of the tab. There are 20 pixels of padding between the webview area and tab header.</span></span>

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-anatomy.png" alt-text="Das Beispiel zeigt, wie die Registerkarte Besprechung in der Besprechung aus der Perspektive eines Besprechungsorganisators aussehen könnte." border="false":::

1. <span data-ttu-id="d2b0e-122">**App-Symbol**: der Einstiegspunkt zur Registerkarte in der Besprechung.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-122">**App icon**: The entry point to the in-meeting tab.</span></span>
1. <span data-ttu-id="d2b0e-123">**Kopfzeile**: schließt den Registerkartennamen ein.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-123">**Header**: Includes the tab name.</span></span>
1. <span data-ttu-id="d2b0e-124">**Name**: der Name der Registerkarten Instanz.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-124">**Name**: The name of the tab instance.</span></span>
1. <span data-ttu-id="d2b0e-125">**Entlassen**: die Registerkarte wird geschlossen. Verwenden Sie immer das obere rechte Schließsymbol anstelle einer Aktion in der Fußzeile.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-125">**Dismiss**: Dismisses the tab. Always use the upper-right close icon instead of an action in the footer.</span></span>
1. <span data-ttu-id="d2b0e-126">**WebView**: zeigt alle Inhalte von Drittanbieter-apps an.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-126">**Webview**: Displays all third-party app content.</span></span>

## <a name="behavior"></a><span data-ttu-id="d2b0e-127">Verhalten</span><span class="sxs-lookup"><span data-stu-id="d2b0e-127">Behavior</span></span>

### <a name="scale"></a><span data-ttu-id="d2b0e-128">Skalierung</span><span class="sxs-lookup"><span data-stu-id="d2b0e-128">Scale</span></span>

<span data-ttu-id="d2b0e-129">Derzeit ist die Breite der in-Meeting-Registerkarte festgelegt.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-129">Currently, the width of the in-meeting tab is fixed.</span></span>

### <a name="scrolling"></a><span data-ttu-id="d2b0e-130">Scrollen</span><span class="sxs-lookup"><span data-stu-id="d2b0e-130">Scrolling</span></span>

<span data-ttu-id="d2b0e-131">Hier erfahren Sie, was Sie über das Scrollen auf der Registerkarte "in-Meeting" wissen:</span><span class="sxs-lookup"><span data-stu-id="d2b0e-131">Here's what to know about scrolling in the in-meeting tab:</span></span>

* <span data-ttu-id="d2b0e-132">Sie sollten nur vertikal scrollen können.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-132">You should only be able to scroll vertically.</span></span>
* <span data-ttu-id="d2b0e-133">Sie können nur den Inhalt sehen, zu dem Sie einen Bildlauf durchgeführt haben (nichts oberhalb oder unterhalb).</span><span class="sxs-lookup"><span data-stu-id="d2b0e-133">You can only see the content you've scrolled to (nothing above or below).</span></span>
* <span data-ttu-id="d2b0e-134">Die ScrollBar ist Teil des WebView-Inhalts.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-134">The scrollbar is part of the webview content.</span></span>

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-scroll.png" alt-text="Das Beispiel zeigt, wie die Registerkarte Besprechung in der Besprechung aus der Perspektive eines Besprechungsorganisators aussehen könnte." border="false":::

### <a name="navigation"></a><span data-ttu-id="d2b0e-136">Navigation</span><span class="sxs-lookup"><span data-stu-id="d2b0e-136">Navigation</span></span>

<span data-ttu-id="d2b0e-137">Für Szenarien mit Navigationsebenen oder schweren Inhalten empfehlen wir, Benutzern das Navigieren zu einer sekundären Ebene zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-137">For scenarios with navigation layers or heavy content, we recommend allowing users to navigate to a secondary layer.</span></span> <span data-ttu-id="d2b0e-138">Benutzer müssen in der Lage sein, zur vorherigen Ebene zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-138">Users must be able to go back to the previous layer.</span></span>

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-nav.png" alt-text="Das Beispiel zeigt, wie die Registerkarte Besprechung in der Besprechung aus der Perspektive eines Besprechungsorganisators aussehen könnte." border="false":::

## <a name="components"></a><span data-ttu-id="d2b0e-140">Komponenten</span><span class="sxs-lookup"><span data-stu-id="d2b0e-140">Components</span></span>

<span data-ttu-id="d2b0e-141">In-Meeting-Registerkarten werden in erster Linie mit den folgenden <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">UI-Komponenten (Figma)</a>erstellt, die auf dem <a href="https://fluentsite.z22.web.core.windows.net/" target="_blank">Fluent-Entwurfs System</a>basieren.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-141">In-meeting tabs are built primarily with the following <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">UI components (Figma)</a>, which are based on the <a href="https://fluentsite.z22.web.core.windows.net/" target="_blank">Fluent Design System</a>.</span></span>

<span data-ttu-id="d2b0e-142">Komponente</span><span class="sxs-lookup"><span data-stu-id="d2b0e-142">Component</span></span> | <span data-ttu-id="d2b0e-143">Anleitungen</span><span class="sxs-lookup"><span data-stu-id="d2b0e-143">Guidelines</span></span> | <span data-ttu-id="d2b0e-144">Beispiel</span><span class="sxs-lookup"><span data-stu-id="d2b0e-144">Example</span></span>
 - | - | -
<span data-ttu-id="d2b0e-145">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="d2b0e-145">Button</span></span> | <span data-ttu-id="d2b0e-146">Primäre und sekundäre Schaltflächen können Mittel oder klein sein</span><span class="sxs-lookup"><span data-stu-id="d2b0e-146">Primary and secondary buttons can be medium or small</span></span> | <span data-ttu-id="d2b0e-147">Senden einer Antwort</span><span class="sxs-lookup"><span data-stu-id="d2b0e-147">Send a response</span></span>
<span data-ttu-id="d2b0e-148">Input</span><span class="sxs-lookup"><span data-stu-id="d2b0e-148">Input</span></span> | <span data-ttu-id="d2b0e-149">Feld für eine kurze Benutzereingabe.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-149">Field for brief user input.</span></span> <span data-ttu-id="d2b0e-150">Bezeichnungstext kann ein Symbol enthalten</span><span class="sxs-lookup"><span data-stu-id="d2b0e-150">Label text can include an icon</span></span>  | <span data-ttu-id="d2b0e-151">Feedback eingeben</span><span class="sxs-lookup"><span data-stu-id="d2b0e-151">Enter feedback</span></span>
<span data-ttu-id="d2b0e-152">Dropdown</span><span class="sxs-lookup"><span data-stu-id="d2b0e-152">Dropdown</span></span> | <span data-ttu-id="d2b0e-153">Wählen Sie eine oder mehrere Optionen aus einer Liste aus.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-153">Select one or more options from a list.</span></span> <span data-ttu-id="d2b0e-154">Kann Such-und Mehrfachauswahl Funktionen umfassen</span><span class="sxs-lookup"><span data-stu-id="d2b0e-154">Can include search and multi-selection features</span></span> | <span data-ttu-id="d2b0e-155">Auswählen einer Sprache</span><span class="sxs-lookup"><span data-stu-id="d2b0e-155">Choose a language</span></span>
<span data-ttu-id="d2b0e-156">Auswahlsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="d2b0e-156">Selection controls</span></span> | <span data-ttu-id="d2b0e-157">Verwenden Sie Kontrollkästchen für mehrere Auswahlmöglichkeiten oder Optionsfelder, und schalten Sie Sie für einzelne Optionen ein.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-157">Use checkboxes for multiple choices or radio buttons and toggles for single choices.</span></span> <span data-ttu-id="d2b0e-158">Für detailliertere Auswahlen verwenden Sie einen Schieberegler</span><span class="sxs-lookup"><span data-stu-id="d2b0e-158">For more detailed selections, use a slider</span></span> | <span data-ttu-id="d2b0e-159">Abstimmung in einer Umfrage</span><span class="sxs-lookup"><span data-stu-id="d2b0e-159">Vote in a poll</span></span>
<span data-ttu-id="d2b0e-160">Warnungen</span><span class="sxs-lookup"><span data-stu-id="d2b0e-160">Alerts</span></span> | <span data-ttu-id="d2b0e-161">Unabhängig davon, ob eine dringende Nachricht, ein Fehlerstatus oder eine Warnung angezeigt wird, die Nachricht sollte kurz sein und die aktuelle Aufgabe des Benutzers nicht unterbrechen.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-161">Whether displaying an urgent message, error state, or warning, the message should be short and won't interrupt the user's current task</span></span> | <span data-ttu-id="d2b0e-162">Anzeigeproblem beim Senden einer Antwort</span><span class="sxs-lookup"><span data-stu-id="d2b0e-162">Display issue when submitting a response</span></span>

## <a name="theming"></a><span data-ttu-id="d2b0e-163">Designs</span><span class="sxs-lookup"><span data-stu-id="d2b0e-163">Theming</span></span>

### <a name="colors"></a><span data-ttu-id="d2b0e-164">Farben</span><span class="sxs-lookup"><span data-stu-id="d2b0e-164">Colors</span></span>

<span data-ttu-id="d2b0e-165">Verwenden Sie das <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Empfohlene Farbschema (Figma)</a> für Hintergründe, vordergrunde und förderzustände.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-165">Use the <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">recommended color scheme (Figma)</a> for backgrounds, foregrounds, and conveying states.</span></span>

### <a name="typography"></a><span data-ttu-id="d2b0e-166">Typografie</span><span class="sxs-lookup"><span data-stu-id="d2b0e-166">Typography</span></span>

<span data-ttu-id="d2b0e-167">Verwenden Sie die <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">empfohlenen Schriftgrößen und-Gewichtungen (Figma)</a> für Titel, Textkörper und metadatentext.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-167">Use the <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">recommended font sizes and weights (Figma)</a> for titles, body text, and metadata text.</span></span>

## <a name="best-practices"></a><span data-ttu-id="d2b0e-168">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="d2b0e-168">Best practices</span></span>

### <a name="responsiveness"></a><span data-ttu-id="d2b0e-169">Suchen</span><span class="sxs-lookup"><span data-stu-id="d2b0e-169">Responsiveness</span></span>

<span data-ttu-id="d2b0e-170">In-Meeting-Registerkarten Layouts sollten in der Lage sein, verschiedene Größen zu skalieren.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-170">In-meeting tab layouts should be able to scale to various sizes.</span></span> <span data-ttu-id="d2b0e-171">Berücksichtigen Sie, wie die Registerkarte skaliert wird und wie Sie Form vor, während und nach der Besprechung nimmt.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-171">Consider how the tab will scale and take shape before, during, and after the meeting.</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-before-meeting.png" alt-text="Das Beispiel zeigt, wie die Registerkarte Besprechung in der Besprechung aus der Perspektive eines Besprechungsorganisators aussehen könnte." border="false":::

#### <a name="before-the-meeting"></a><span data-ttu-id="d2b0e-173">Vor der Besprechung</span><span class="sxs-lookup"><span data-stu-id="d2b0e-173">Before the meeting</span></span>

<span data-ttu-id="d2b0e-174">Stellen Sie sicher, dass sich das registerkartenlayout an ein rechts-oder links Layout für unterschiedliche Sprachen anpassen kann und dass Steuerelemente an die richtigen Stellen verschoben werden.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-174">Make sure your tab layout can adapt to a right or left layout for different languages and that controls move to the correct locations.</span></span> <span data-ttu-id="d2b0e-175">(Vorab-Besprechungs Layouts können auch auf Post-Meeting-Layouts angewendet werden.)</span><span class="sxs-lookup"><span data-stu-id="d2b0e-175">(Pre-meeting layouts can also apply to post-meeting layouts.)</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-during-meeting.png" alt-text="Das Beispiel zeigt, wie die Registerkarte Besprechung in der Besprechung aus der Perspektive eines Besprechungsorganisators aussehen könnte." border="false":::

#### <a name="during-the-meeting"></a><span data-ttu-id="d2b0e-177">Während der Besprechung</span><span class="sxs-lookup"><span data-stu-id="d2b0e-177">During the meeting</span></span>

<span data-ttu-id="d2b0e-178">Der Inhalt der Registerkarte wird an das Layout und die Position in der Besprechungs Registerkarte angepasst.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-178">Tab content adjusts to the in-meeting tab layout and location.</span></span>

   :::column-end:::
:::row-end:::

### <a name="theming"></a><span data-ttu-id="d2b0e-179">Designs</span><span class="sxs-lookup"><span data-stu-id="d2b0e-179">Theming</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-theming-do.png" alt-text="Das Beispiel zeigt, wie die Registerkarte Besprechung in der Besprechung aus der Perspektive eines Besprechungsorganisators aussehen könnte." border="false":::

#### <a name="do-design-for-a-dark-theme"></a><span data-ttu-id="d2b0e-181">Do: Design für ein dunkles Design</span><span class="sxs-lookup"><span data-stu-id="d2b0e-181">Do: Design for a dark theme</span></span>

<span data-ttu-id="d2b0e-182">Microsoft Teams-Besprechungen sind für den dunklen Modus optimiert, um visuelles und kognitives Rauschen zu reduzieren, sodass sich Benutzer auf die Diskussion und den freigegebenen Inhalt konzentrieren können.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-182">Teams meetings are optimized for dark mode to help reduce visual and cognitive noise so users can focus on the discussion and shared content.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-theming-dont.png" alt-text="Das Beispiel zeigt, wie die Registerkarte Besprechung in der Besprechung aus der Perspektive eines Besprechungsorganisators aussehen könnte." border="false":::

#### <a name="dont-use-unfamiliar-colors"></a><span data-ttu-id="d2b0e-184">Nicht: Unbekannte Farben verwenden</span><span class="sxs-lookup"><span data-stu-id="d2b0e-184">Don't: Use unfamiliar colors</span></span>

<span data-ttu-id="d2b0e-185">Farben, die mit der Besprechungs Umgebung kollidieren, sind möglicherweise störend und werden in Microsoft Teams eher als systemeigen dargestellt.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-185">Colors that clash with the meeting environment may be distracting and appear less native to Teams.</span></span>

   :::column-end:::
:::row-end:::

### <a name="scrolling"></a><span data-ttu-id="d2b0e-186">Scrollen</span><span class="sxs-lookup"><span data-stu-id="d2b0e-186">Scrolling</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-scroll-do.png" alt-text="Das Beispiel zeigt, wie die Registerkarte Besprechung in der Besprechung aus der Perspektive eines Besprechungsorganisators aussehen könnte." border="false":::

#### <a name="do-scroll-vertically"></a><span data-ttu-id="d2b0e-188">Do: vertikal scrollen</span><span class="sxs-lookup"><span data-stu-id="d2b0e-188">Do: Scroll vertically</span></span>

<span data-ttu-id="d2b0e-189">Benutzer erwarten vertikales Scrollen in Microsoft Teams (und anderswo).</span><span class="sxs-lookup"><span data-stu-id="d2b0e-189">Users anticipate vertical scrolling in Teams (and elsewhere).</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-scroll-dont.png" alt-text="Das Beispiel zeigt, wie die Registerkarte Besprechung in der Besprechung aus der Perspektive eines Besprechungsorganisators aussehen könnte." border="false":::

#### <a name="dont-scroll-horizontally"></a><span data-ttu-id="d2b0e-191">Nicht: horizontal scrollen</span><span class="sxs-lookup"><span data-stu-id="d2b0e-191">Don't: Scroll horizontally</span></span>

<span data-ttu-id="d2b0e-192">Ein horizontaler Bildlauf ist kein erwartetes Verhalten in Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-192">Horizontal scrolling isn’t an expected behavior in Teams.</span></span> <span data-ttu-id="d2b0e-193">Andere Canvases in der Besprechungs Umgebung Scrollen vertikal.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-193">Other canvases in the meeting environment scroll vertically.</span></span>

   :::column-end:::
:::row-end:::

### <a name="layout"></a><span data-ttu-id="d2b0e-194">Layout</span><span class="sxs-lookup"><span data-stu-id="d2b0e-194">Layout</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-layout-do.png" alt-text="Das Beispiel zeigt, wie die Registerkarte Besprechung in der Besprechung aus der Perspektive eines Besprechungsorganisators aussehen könnte." border="false":::

#### <a name="do-single-columns"></a><span data-ttu-id="d2b0e-196">Do: einzelne Spalten</span><span class="sxs-lookup"><span data-stu-id="d2b0e-196">Do: Single columns</span></span>

<span data-ttu-id="d2b0e-197">Angesichts der engen Natur in der Besprechungs Registerkarte wird dringend empfohlen, den Inhalt in einer einzelnen Spalte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-197">Given the in-meeting tab’s narrow nature, we strongly recommend displaying the contents in a single column.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-layout-dont.png" alt-text="Das Beispiel zeigt, wie die Registerkarte Besprechung in der Besprechung aus der Perspektive eines Besprechungsorganisators aussehen könnte." border="false":::

#### <a name="dont-multiple-columns"></a><span data-ttu-id="d2b0e-199">Nicht: mehrere Spalten</span><span class="sxs-lookup"><span data-stu-id="d2b0e-199">Don't: Multiple columns</span></span>

<span data-ttu-id="d2b0e-200">Aufgrund des begrenzten Speicherplatzes der in-Meeting-Registerkarte werden Layouts mit mehr als einer Spalte nicht empfohlen.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-200">Due to the limited space of the in-meeting tab, layouts with more than one column aren’t recommended.</span></span>

   :::column-end:::
:::row-end:::

### <a name="navigation"></a><span data-ttu-id="d2b0e-201">Navigation</span><span class="sxs-lookup"><span data-stu-id="d2b0e-201">Navigation</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-nav-do.png" alt-text="Das Beispiel zeigt, wie die Registerkarte Besprechung in der Besprechung aus der Perspektive eines Besprechungsorganisators aussehen könnte." border="false":::

#### <a name="do-have-a-back-button"></a><span data-ttu-id="d2b0e-203">Do: verfügen über eine Schaltfläche "zurück"</span><span class="sxs-lookup"><span data-stu-id="d2b0e-203">Do: Have a back button</span></span>

<span data-ttu-id="d2b0e-204">Wenn Sie mehr als eine Navigations Schicht haben, müssen die Benutzer in der Lage sein, zur vorherigen Ansicht zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-204">If you have more than one layer of navigation, users must be able to go back to their previous view.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-nav-dont.png" alt-text="Das Beispiel zeigt, wie die Registerkarte Besprechung in der Besprechung aus der Perspektive eines Besprechungsorganisators aussehen könnte." border="false":::

#### <a name="dont-include-another-close-button"></a><span data-ttu-id="d2b0e-206">Nicht: Einschließen einer weiteren schließen-Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="d2b0e-206">Don't: Include another close button</span></span>

<span data-ttu-id="d2b0e-207">Das Bereitstelleneiner Option zum Schließen von Inhalten in Besprechungs Registerkarten kann Probleme verursachen, da bereits eine Schaltfläche zum Schließen in der Kopfzeile vorhanden ist, um die in-Meeting-Registerkarte selbst zu schließen.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-207">Providing an option to close in-meeting tab content may cause issues since there’s already a close button in the header to dismiss the in-meeting tab itself.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-nav-caution.png" alt-text="Das Beispiel zeigt, wie die Registerkarte Besprechung in der Besprechung aus der Perspektive eines Besprechungsorganisators aussehen könnte." border="false":::

#### <a name="caution-using-dialogs-in-a-narrow-space"></a><span data-ttu-id="d2b0e-209">Vorsicht: Verwenden von Dialogfeldern auf engstem Raum</span><span class="sxs-lookup"><span data-stu-id="d2b0e-209">Caution: Using dialogs in a narrow space</span></span>

<span data-ttu-id="d2b0e-210">Dialogfelder, beispielsweise Vorgangs Module, können den Inhalt in der bereits engen Registerkarte in Besprechungen Umbrechen und verdecken.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-210">Dialogs, such as task modules, in the already narrow in-meeting tab might wrap and obscure the content.</span></span>

   :::column-end:::
:::row-end:::

## <a name="accessibility"></a><span data-ttu-id="d2b0e-211">Barrierefreiheit</span><span class="sxs-lookup"><span data-stu-id="d2b0e-211">Accessibility</span></span>

<span data-ttu-id="d2b0e-212">Informationen zur Barrierefreiheit finden Sie unter <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Figma</a>.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-212">For information on accessibility, see <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Figma</a>.</span></span>

## <a name="resources"></a><span data-ttu-id="d2b0e-213">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="d2b0e-213">Resources</span></span>

* <span data-ttu-id="d2b0e-214"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Figma-Datei für Microsoft Teams-Besprechungs Erweiterungen</a></span><span class="sxs-lookup"><span data-stu-id="d2b0e-214"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Microsoft Teams meeting extensions Figma file</a></span></span>
* [<span data-ttu-id="d2b0e-215">Entwurfsrichtlinien für Registerkarten</span><span class="sxs-lookup"><span data-stu-id="d2b0e-215">Tabs design guidelines</span></span>](../../tabs/design/tabs.md)
* [<span data-ttu-id="d2b0e-216">Entwurfsrichtlinien für Tabs für mobile Geräte</span><span class="sxs-lookup"><span data-stu-id="d2b0e-216">Tabs design guidelines for mobile</span></span>](../../tabs/design/tabs-mobile.md)

## <a name="validate-your-design"></a><span data-ttu-id="d2b0e-217">Überprüfen des Designs</span><span class="sxs-lookup"><span data-stu-id="d2b0e-217">Validate your design</span></span>

<span data-ttu-id="d2b0e-218">Wenn Sie Ihre APP in AppSource veröffentlichen möchten, sollten Sie sich mit den Entwurfsproblemen vertraut machen, die häufig dazu führen, dass apps während der Übermittlung fehlschlagen.</span><span class="sxs-lookup"><span data-stu-id="d2b0e-218">If you plan to publish your app to AppSource, you should understand the design issues that commonly cause apps to fail during submission.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d2b0e-219">Überprüfen der Entwurfs Validierungsrichtlinien</span><span class="sxs-lookup"><span data-stu-id="d2b0e-219">Check design validation guidelines</span></span>](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines)