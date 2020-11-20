---
title: Besprechungs-Registerkarte entwerfen
author: heath-hamilton
description: Hier erfahren Sie, wie Sie eine in-Meeting-Registerkarte für Microsoft Teams effektiv entwerfen.
ms.author: lajanuar
ms.topic: conceptual
ms.openlocfilehash: fc10c5b60672d243ac2e330ce93b4e01c2e7a278
ms.sourcegitcommit: 64acd30eee8af5fe151e9866c13226ed3f337c72
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2020
ms.locfileid: "49346672"
---
# <a name="design-an-in-meeting-tab"></a><span data-ttu-id="4324b-103">Besprechungs-Registerkarte entwerfen</span><span class="sxs-lookup"><span data-stu-id="4324b-103">Design an in-meeting tab</span></span>

<span data-ttu-id="4324b-104">Die Registerkarte in-Meeting ist eine Arbeitsfläche zum Erweitern der Zusammenarbeit während Besprechungen.</span><span class="sxs-lookup"><span data-stu-id="4324b-104">The in-meeting tab is a canvas for augmenting collaboration during meetings.</span></span> <span data-ttu-id="4324b-105">Basierend auf den registerkartenfunktionen von Teams können Teilnehmer App-Inhalte in einem dedizierten Raum außerhalb der Besprechungs Phase über freigegebene oder rollenbasierte Ansichten anzeigen und interagieren.</span><span class="sxs-lookup"><span data-stu-id="4324b-105">Based on the Teams tab capability, attendees can see and interact with app content in a dedicated space outside the meeting stage through shared or role-based views.</span></span>

## <a name="use-cases"></a><span data-ttu-id="4324b-106">Anwendungsfälle</span><span class="sxs-lookup"><span data-stu-id="4324b-106">Use cases</span></span>

<span data-ttu-id="4324b-107">Die Registerkarte "in-Meeting" wird von den Benutzern möglicherweise verwendet:</span><span class="sxs-lookup"><span data-stu-id="4324b-107">People might use the in-meeting tab to:</span></span>

* <span data-ttu-id="4324b-108">Bereitstellen eines detaillierten Feedbacks (zum Beispiel Auswerten eines Bewerbers)</span><span class="sxs-lookup"><span data-stu-id="4324b-108">Provide detailed feedback (for example, evaluate a job candidate)</span></span>
* <span data-ttu-id="4324b-109">Schnelles Erstellen einer Umfrage, Umfrage oder eines Aufgabenelements für die Besprechungsteilnehmer</span><span class="sxs-lookup"><span data-stu-id="4324b-109">Quickly create a poll, survey, or task item for the meeting participants</span></span>
* <span data-ttu-id="4324b-110">Anzeigen von Notizen, die für die Besprechung relevant sind (beispielsweise Informationen zu einem Verkaufsleiter)</span><span class="sxs-lookup"><span data-stu-id="4324b-110">Display notes relevant to the meeting (for example, information about a sales lead)</span></span>

## <a name="example"></a><span data-ttu-id="4324b-111">Beispiel</span><span class="sxs-lookup"><span data-stu-id="4324b-111">Example</span></span>

<span data-ttu-id="4324b-112">Das folgende Beispiel zeigt die Registerkarte in der Besprechung, in der Umfrage-App-Inhalte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="4324b-112">The following example shows the in-meeting tab displaying survey app content.</span></span>

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-organizer-view.png" alt-text="Das Beispiel zeigt, wie die Registerkarte Besprechung in der Besprechung aus der Perspektive eines Besprechungsorganisators aussehen könnte.":::

<span data-ttu-id="4324b-114"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Das vollständige Szenario anzeigen (Figma)</a></span><span class="sxs-lookup"><span data-stu-id="4324b-114"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">See the full scenario (Figma)</a></span></span>

<span data-ttu-id="4324b-115"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Siehe andere Beispiele für Anwendungsfälle (Figma)</a></span><span class="sxs-lookup"><span data-stu-id="4324b-115"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">See other example use cases (Figma)</a></span></span>

## <a name="anatomy"></a><span data-ttu-id="4324b-116">Anatomie</span><span class="sxs-lookup"><span data-stu-id="4324b-116">Anatomy</span></span>

<span data-ttu-id="4324b-117">Auf der Registerkarte in-Meeting werden Ihre APP-Inhalte mit den folgenden Dimensionen angezeigt:</span><span class="sxs-lookup"><span data-stu-id="4324b-117">The in-meeting tab displays your app content using the following dimensions:</span></span>

* <span data-ttu-id="4324b-118">**Breite**: 280 Pixel für den WebView-Bereich.</span><span class="sxs-lookup"><span data-stu-id="4324b-118">**Width**: 280 pixels for the webview area.</span></span> <span data-ttu-id="4324b-119">Auf der linken und rechten Seite des Webviews befinden sich 20 Pixel Textabstand.</span><span class="sxs-lookup"><span data-stu-id="4324b-119">There are 20 pixels of padding on the left and right sides of the webview.</span></span>
* <span data-ttu-id="4324b-120">**Höhe**: vollständiges Anfärben am unteren Rand der Registerkarte. Zwischen dem WebView-Bereich und der Registerkartenüberschrift befinden sich 20 Pixelabstand.</span><span class="sxs-lookup"><span data-stu-id="4324b-120">**Height**: Full bleed to the bottom of the tab. There are 20 pixels of padding between the webview area and tab header.</span></span>

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-anatomy.png" alt-text="Abbildung der UI-Anatomie einer Besprechungs Erweiterung in der Besprechungs Registerkarte." border="false":::

1. <span data-ttu-id="4324b-122">**App-Symbol**: der Einstiegspunkt zur Registerkarte in der Besprechung.</span><span class="sxs-lookup"><span data-stu-id="4324b-122">**App icon**: The entry point to the in-meeting tab.</span></span>
1. <span data-ttu-id="4324b-123">**Kopfzeile**: schließt den Registerkartennamen ein.</span><span class="sxs-lookup"><span data-stu-id="4324b-123">**Header**: Includes the tab name.</span></span>
1. <span data-ttu-id="4324b-124">**Name**: der Name der Registerkarten Instanz.</span><span class="sxs-lookup"><span data-stu-id="4324b-124">**Name**: The name of the tab instance.</span></span>
1. <span data-ttu-id="4324b-125">**Entlassen**: die Registerkarte wird geschlossen. Verwenden Sie immer das obere rechte Schließsymbol anstelle einer Aktion in der Fußzeile.</span><span class="sxs-lookup"><span data-stu-id="4324b-125">**Dismiss**: Dismisses the tab. Always use the upper-right close icon instead of an action in the footer.</span></span>
1. <span data-ttu-id="4324b-126">**WebView**: zeigt alle Inhalte von Drittanbieter-apps an.</span><span class="sxs-lookup"><span data-stu-id="4324b-126">**Webview**: Displays all third-party app content.</span></span>

## <a name="behavior"></a><span data-ttu-id="4324b-127">Verhalten</span><span class="sxs-lookup"><span data-stu-id="4324b-127">Behavior</span></span>

### <a name="scale"></a><span data-ttu-id="4324b-128">Skalierung</span><span class="sxs-lookup"><span data-stu-id="4324b-128">Scale</span></span>

<span data-ttu-id="4324b-129">Derzeit ist die Breite der in-Meeting-Registerkarte festgelegt.</span><span class="sxs-lookup"><span data-stu-id="4324b-129">Currently, the width of the in-meeting tab is fixed.</span></span>

### <a name="scrolling"></a><span data-ttu-id="4324b-130">Scrollen</span><span class="sxs-lookup"><span data-stu-id="4324b-130">Scrolling</span></span>

<span data-ttu-id="4324b-131">Hier erfahren Sie, was Sie über das Scrollen auf der Registerkarte "in-Meeting" wissen:</span><span class="sxs-lookup"><span data-stu-id="4324b-131">Here's what to know about scrolling in the in-meeting tab:</span></span>

* <span data-ttu-id="4324b-132">Sie sollten nur vertikal scrollen können.</span><span class="sxs-lookup"><span data-stu-id="4324b-132">You should only be able to scroll vertically.</span></span>
* <span data-ttu-id="4324b-133">Sie können nur den Inhalt sehen, zu dem Sie einen Bildlauf durchgeführt haben (nichts oberhalb oder unterhalb).</span><span class="sxs-lookup"><span data-stu-id="4324b-133">You can only see the content you've scrolled to (nothing above or below).</span></span>
* <span data-ttu-id="4324b-134">Die ScrollBar ist Teil des WebView-Inhalts.</span><span class="sxs-lookup"><span data-stu-id="4324b-134">The scrollbar is part of the webview content.</span></span>

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-scroll.png" alt-text="Abbildung zeigt, wie der Bildlauf in der WebView-Inhalt auf der Registerkarte in-Meeting funktioniert." border="false":::

### <a name="navigation"></a><span data-ttu-id="4324b-136">Navigation</span><span class="sxs-lookup"><span data-stu-id="4324b-136">Navigation</span></span>

<span data-ttu-id="4324b-137">Für Szenarien mit Navigationsebenen oder schweren Inhalten empfehlen wir, Benutzern das Navigieren zu einer sekundären Ebene zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="4324b-137">For scenarios with navigation layers or heavy content, we recommend allowing users to navigate to a secondary layer.</span></span> <span data-ttu-id="4324b-138">Benutzer müssen in der Lage sein, zur vorherigen Ebene zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="4324b-138">Users must be able to go back to the previous layer.</span></span>

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-nav.png" alt-text="Abbildung, die zeigt, wie die Navigation zu einer sekundären Ebene auf der in-Meeting-Registerkarte funktioniert." border="false":::

## <a name="components"></a><span data-ttu-id="4324b-140">Komponenten</span><span class="sxs-lookup"><span data-stu-id="4324b-140">Components</span></span>

<span data-ttu-id="4324b-141">In-Meeting-Registerkarten werden in erster Linie mit den folgenden <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">UI-Komponenten (Figma)</a>erstellt, die auf dem <a href="https://fluentsite.z22.web.core.windows.net/" target="_blank">Fluent-Entwurfs System</a>basieren.</span><span class="sxs-lookup"><span data-stu-id="4324b-141">In-meeting tabs are built primarily with the following <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">UI components (Figma)</a>, which are based on the <a href="https://fluentsite.z22.web.core.windows.net/" target="_blank">Fluent Design System</a>.</span></span>

<span data-ttu-id="4324b-142">Komponente</span><span class="sxs-lookup"><span data-stu-id="4324b-142">Component</span></span> | <span data-ttu-id="4324b-143">Anleitungen</span><span class="sxs-lookup"><span data-stu-id="4324b-143">Guidelines</span></span> | <span data-ttu-id="4324b-144">Beispiel</span><span class="sxs-lookup"><span data-stu-id="4324b-144">Example</span></span>
 - | - | -
<span data-ttu-id="4324b-145">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="4324b-145">Button</span></span> | <span data-ttu-id="4324b-146">Primäre und sekundäre Schaltflächen können Mittel oder klein sein</span><span class="sxs-lookup"><span data-stu-id="4324b-146">Primary and secondary buttons can be medium or small</span></span> | <span data-ttu-id="4324b-147">Senden einer Antwort</span><span class="sxs-lookup"><span data-stu-id="4324b-147">Send a response</span></span>
<span data-ttu-id="4324b-148">Input</span><span class="sxs-lookup"><span data-stu-id="4324b-148">Input</span></span> | <span data-ttu-id="4324b-149">Feld für eine kurze Benutzereingabe.</span><span class="sxs-lookup"><span data-stu-id="4324b-149">Field for brief user input.</span></span> <span data-ttu-id="4324b-150">Bezeichnungstext kann ein Symbol enthalten</span><span class="sxs-lookup"><span data-stu-id="4324b-150">Label text can include an icon</span></span>  | <span data-ttu-id="4324b-151">Feedback eingeben</span><span class="sxs-lookup"><span data-stu-id="4324b-151">Enter feedback</span></span>
<span data-ttu-id="4324b-152">Dropdown</span><span class="sxs-lookup"><span data-stu-id="4324b-152">Dropdown</span></span> | <span data-ttu-id="4324b-153">Wählen Sie eine oder mehrere Optionen aus einer Liste aus.</span><span class="sxs-lookup"><span data-stu-id="4324b-153">Select one or more options from a list.</span></span> <span data-ttu-id="4324b-154">Kann Such-und Mehrfachauswahl Funktionen umfassen</span><span class="sxs-lookup"><span data-stu-id="4324b-154">Can include search and multi-selection features</span></span> | <span data-ttu-id="4324b-155">Auswählen einer Sprache</span><span class="sxs-lookup"><span data-stu-id="4324b-155">Choose a language</span></span>
<span data-ttu-id="4324b-156">Auswahlsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="4324b-156">Selection controls</span></span> | <span data-ttu-id="4324b-157">Verwenden Sie Kontrollkästchen für mehrere Auswahlmöglichkeiten oder Optionsfelder, und schalten Sie Sie für einzelne Optionen ein.</span><span class="sxs-lookup"><span data-stu-id="4324b-157">Use checkboxes for multiple choices or radio buttons and toggles for single choices.</span></span> <span data-ttu-id="4324b-158">Für detailliertere Auswahlen verwenden Sie einen Schieberegler</span><span class="sxs-lookup"><span data-stu-id="4324b-158">For more detailed selections, use a slider</span></span> | <span data-ttu-id="4324b-159">Abstimmung in einer Umfrage</span><span class="sxs-lookup"><span data-stu-id="4324b-159">Vote in a poll</span></span>
<span data-ttu-id="4324b-160">Warnungen</span><span class="sxs-lookup"><span data-stu-id="4324b-160">Alerts</span></span> | <span data-ttu-id="4324b-161">Unabhängig davon, ob eine dringende Nachricht, ein Fehlerstatus oder eine Warnung angezeigt wird, die Nachricht sollte kurz sein und die aktuelle Aufgabe des Benutzers nicht unterbrechen.</span><span class="sxs-lookup"><span data-stu-id="4324b-161">Whether displaying an urgent message, error state, or warning, the message should be short and won't interrupt the user's current task</span></span> | <span data-ttu-id="4324b-162">Anzeigeproblem beim Senden einer Antwort</span><span class="sxs-lookup"><span data-stu-id="4324b-162">Display issue when submitting a response</span></span>

## <a name="theming"></a><span data-ttu-id="4324b-163">Designs</span><span class="sxs-lookup"><span data-stu-id="4324b-163">Theming</span></span>

### <a name="colors"></a><span data-ttu-id="4324b-164">Farben</span><span class="sxs-lookup"><span data-stu-id="4324b-164">Colors</span></span>

<span data-ttu-id="4324b-165">Verwenden Sie das <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Empfohlene Farbschema (Figma)</a> für Hintergründe, vordergrunde und förderzustände.</span><span class="sxs-lookup"><span data-stu-id="4324b-165">Use the <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">recommended color scheme (Figma)</a> for backgrounds, foregrounds, and conveying states.</span></span>

### <a name="typography"></a><span data-ttu-id="4324b-166">Typografie</span><span class="sxs-lookup"><span data-stu-id="4324b-166">Typography</span></span>

<span data-ttu-id="4324b-167">Verwenden Sie die <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">empfohlenen Schriftgrößen und-Gewichtungen (Figma)</a> für Titel, Textkörper und metadatentext.</span><span class="sxs-lookup"><span data-stu-id="4324b-167">Use the <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">recommended font sizes and weights (Figma)</a> for titles, body text, and metadata text.</span></span>

## <a name="best-practices"></a><span data-ttu-id="4324b-168">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="4324b-168">Best practices</span></span>

### <a name="responsiveness"></a><span data-ttu-id="4324b-169">Suchen</span><span class="sxs-lookup"><span data-stu-id="4324b-169">Responsiveness</span></span>

<span data-ttu-id="4324b-170">In-Meeting-Registerkarten Layouts sollten in der Lage sein, verschiedene Größen zu skalieren.</span><span class="sxs-lookup"><span data-stu-id="4324b-170">In-meeting tab layouts should be able to scale to various sizes.</span></span> <span data-ttu-id="4324b-171">Berücksichtigen Sie, wie die Registerkarte skaliert wird und wie Sie Form vor, während und nach der Besprechung nimmt.</span><span class="sxs-lookup"><span data-stu-id="4324b-171">Consider how the tab will scale and take shape before, during, and after the meeting.</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-before-meeting.png" alt-text="Abbildung zeigt, dass der Inhalt der Besprechungs Registerkarte vor und nach einer Besprechung wie eine voll Bild Registerkarte aussieht." border="false":::

#### <a name="before-the-meeting"></a><span data-ttu-id="4324b-173">Vor der Besprechung</span><span class="sxs-lookup"><span data-stu-id="4324b-173">Before the meeting</span></span>

<span data-ttu-id="4324b-174">Stellen Sie sicher, dass sich das registerkartenlayout an ein rechts-oder links Layout für unterschiedliche Sprachen anpassen kann und dass Steuerelemente an die richtigen Stellen verschoben werden.</span><span class="sxs-lookup"><span data-stu-id="4324b-174">Make sure your tab layout can adapt to a right or left layout for different languages and that controls move to the correct locations.</span></span> <span data-ttu-id="4324b-175">(Vorab-Besprechungs Layouts können auch auf Post-Meeting-Layouts angewendet werden.)</span><span class="sxs-lookup"><span data-stu-id="4324b-175">(Pre-meeting layouts can also apply to post-meeting layouts.)</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-during-meeting.png" alt-text="Abbildung, die zeigt, wie der Inhalt der Registerkarte &quot;Pre-Meeting&quot; auf die Registerkarte &quot;in-Meeting&quot; während einer Besprechung verkürzt wird." border="false":::

#### <a name="during-the-meeting"></a><span data-ttu-id="4324b-177">Während der Besprechung</span><span class="sxs-lookup"><span data-stu-id="4324b-177">During the meeting</span></span>

<span data-ttu-id="4324b-178">Der Inhalt der Registerkarte wird an das Layout und die Position in der Besprechungs Registerkarte angepasst.</span><span class="sxs-lookup"><span data-stu-id="4324b-178">Tab content adjusts to the in-meeting tab layout and location.</span></span>

   :::column-end:::
:::row-end:::

### <a name="theming"></a><span data-ttu-id="4324b-179">Designs</span><span class="sxs-lookup"><span data-stu-id="4324b-179">Theming</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-theming-do.png" alt-text="Illustration, die zeigt, wie Sie die in-Meeting-Registerkarte für das dunkle Design entwerfen, das in Microsoft Teams-Besprechungen verwendet wird." border="false":::

#### <a name="do-design-for-a-dark-theme"></a><span data-ttu-id="4324b-181">Do: Design für ein dunkles Design</span><span class="sxs-lookup"><span data-stu-id="4324b-181">Do: Design for a dark theme</span></span>

<span data-ttu-id="4324b-182">Microsoft Teams-Besprechungen sind für den dunklen Modus optimiert, um visuelles und kognitives Rauschen zu reduzieren, sodass sich Benutzer auf die Diskussion und den freigegebenen Inhalt konzentrieren können.</span><span class="sxs-lookup"><span data-stu-id="4324b-182">Teams meetings are optimized for dark mode to help reduce visual and cognitive noise so users can focus on the discussion and shared content.</span></span> <span data-ttu-id="4324b-183">Auf der Registerkarte "in-Meeting" sollte ein dunkles Design angewendet werden, und die Richtlinien für die Besprechung sollten befolgt werden.</span><span class="sxs-lookup"><span data-stu-id="4324b-183">The in-meeting tab should apply a dark theme and should follow theming guidelines.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-theming-dont.png" alt-text="Abbildung zeigt, dass Sie keine Farben verwenden sollten, die dem dunklen Design von Teams nicht förderlich sind." border="false":::

#### <a name="dont-use-unfamiliar-colors"></a><span data-ttu-id="4324b-185">Nicht: Unbekannte Farben verwenden</span><span class="sxs-lookup"><span data-stu-id="4324b-185">Don't: Use unfamiliar colors</span></span>

<span data-ttu-id="4324b-186">Farben, die mit der Besprechungs Umgebung kollidieren, sind möglicherweise störend und werden in Microsoft Teams eher als systemeigen dargestellt.</span><span class="sxs-lookup"><span data-stu-id="4324b-186">Colors that clash with the meeting environment may be distracting and appear less native to Teams.</span></span>

   :::column-end:::
:::row-end:::

### <a name="scrolling"></a><span data-ttu-id="4324b-187">Scrollen</span><span class="sxs-lookup"><span data-stu-id="4324b-187">Scrolling</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-scroll-do.png" alt-text="Die Abbildung zeigt, dass Sie auf der Registerkarte &quot;in-Meeting&quot; nur den vertikalen Bildlauf zulassen sollten." border="false":::

#### <a name="do-scroll-vertically"></a><span data-ttu-id="4324b-189">Do: vertikal scrollen</span><span class="sxs-lookup"><span data-stu-id="4324b-189">Do: Scroll vertically</span></span>

<span data-ttu-id="4324b-190">Benutzer erwarten vertikales Scrollen in Microsoft Teams (und anderswo).</span><span class="sxs-lookup"><span data-stu-id="4324b-190">Users anticipate vertical scrolling in Teams (and elsewhere).</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-scroll-dont.png" alt-text="Die Abbildung zeigt, dass auf der Registerkarte &quot;in-Meeting&quot; kein horizontaler Bildlauf zulässig ist." border="false":::

#### <a name="dont-scroll-horizontally"></a><span data-ttu-id="4324b-192">Nicht: horizontal scrollen</span><span class="sxs-lookup"><span data-stu-id="4324b-192">Don't: Scroll horizontally</span></span>

<span data-ttu-id="4324b-193">Ein horizontaler Bildlauf ist kein erwartetes Verhalten in Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="4324b-193">Horizontal scrolling isn’t an expected behavior in Teams.</span></span> <span data-ttu-id="4324b-194">Andere Canvases in der Besprechungs Umgebung Scrollen vertikal.</span><span class="sxs-lookup"><span data-stu-id="4324b-194">Other canvases in the meeting environment scroll vertically.</span></span>

   :::column-end:::
:::row-end:::

### <a name="layout"></a><span data-ttu-id="4324b-195">Layout</span><span class="sxs-lookup"><span data-stu-id="4324b-195">Layout</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-layout-do.png" alt-text="Abbildung mit dem empfohlenen Layout mit einer einzelnen Spalte auf der Registerkarte &quot;in-Meeting&quot;." border="false":::

#### <a name="do-single-columns"></a><span data-ttu-id="4324b-197">Do: einzelne Spalten</span><span class="sxs-lookup"><span data-stu-id="4324b-197">Do: Single columns</span></span>

<span data-ttu-id="4324b-198">Angesichts der engen Natur in der Besprechungs Registerkarte wird dringend empfohlen, den Inhalt in einer einzelnen Spalte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="4324b-198">Given the in-meeting tab’s narrow nature, we strongly recommend displaying the contents in a single column.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-layout-dont.png" alt-text="Abbildung zeigt, wie ein zweispaltiges Layout auf der Registerkarte &quot;in-Meeting&quot; nicht ideal ist." border="false":::

#### <a name="dont-multiple-columns"></a><span data-ttu-id="4324b-200">Nicht: mehrere Spalten</span><span class="sxs-lookup"><span data-stu-id="4324b-200">Don't: Multiple columns</span></span>

<span data-ttu-id="4324b-201">Aufgrund des begrenzten Speicherplatzes der in-Meeting-Registerkarte werden Layouts mit mehr als einer Spalte nicht empfohlen.</span><span class="sxs-lookup"><span data-stu-id="4324b-201">Due to the limited space of the in-meeting tab, layouts with more than one column aren’t recommended.</span></span>

   :::column-end:::
:::row-end:::

### <a name="navigation"></a><span data-ttu-id="4324b-202">Navigation</span><span class="sxs-lookup"><span data-stu-id="4324b-202">Navigation</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-nav-do.png" alt-text="Abbildung zeigt, dass Sie immer eine Schaltfläche &quot;zurück&quot; bereitstellen sollten, wenn Ihre in-Meeting-Registerkarten-app mehr als eine Navigationsebene aufweist." border="false":::

#### <a name="do-have-a-back-button"></a><span data-ttu-id="4324b-204">Do: verfügen über eine Schaltfläche "zurück"</span><span class="sxs-lookup"><span data-stu-id="4324b-204">Do: Have a back button</span></span>

<span data-ttu-id="4324b-205">Wenn Sie mehr als eine Navigations Schicht haben, müssen die Benutzer in der Lage sein, zur vorherigen Ansicht zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="4324b-205">If you have more than one layer of navigation, users must be able to go back to their previous view.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-nav-dont.png" alt-text="Abbildung zeigt, dass das Hinzufügen einer weiteren Schaltfläche Schließen auf der Registerkarte in-Meeting für die Navigation redundant ist und Probleme verursachen könnte." border="false":::

#### <a name="dont-include-another-close-button"></a><span data-ttu-id="4324b-207">Nicht: Einschließen einer weiteren schließen-Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="4324b-207">Don't: Include another close button</span></span>

<span data-ttu-id="4324b-208">Das Bereitstelleneiner Option zum Schließen von Inhalten in Besprechungs Registerkarten kann Probleme verursachen, da bereits eine Schaltfläche zum Schließen in der Kopfzeile vorhanden ist, um die in-Meeting-Registerkarte selbst zu schließen.</span><span class="sxs-lookup"><span data-stu-id="4324b-208">Providing an option to close in-meeting tab content may cause issues since there’s already a close button in the header to dismiss the in-meeting tab itself.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-nav-caution.png" alt-text="Abbildung zeigt, dass Sie bei der Verwendung von modals (also Aufgaben Modulen) auf der Registerkarte &quot;in-Meeting&quot; mit dem begrenzten Platz Vorsicht walten lassen müssen." border="false":::

#### <a name="caution-using-dialogs-in-a-narrow-space"></a><span data-ttu-id="4324b-210">Vorsicht: Verwenden von Dialogfeldern auf engstem Raum</span><span class="sxs-lookup"><span data-stu-id="4324b-210">Caution: Using dialogs in a narrow space</span></span>

<span data-ttu-id="4324b-211">Dialogfelder, beispielsweise Vorgangs Module, können den Inhalt in der bereits engen Registerkarte in Besprechungen Umbrechen und verdecken.</span><span class="sxs-lookup"><span data-stu-id="4324b-211">Dialogs, such as task modules, in the already narrow in-meeting tab might wrap and obscure the content.</span></span>

   :::column-end:::
:::row-end:::

## <a name="accessibility"></a><span data-ttu-id="4324b-212">Barrierefreiheit</span><span class="sxs-lookup"><span data-stu-id="4324b-212">Accessibility</span></span>

<span data-ttu-id="4324b-213">Informationen zur Barrierefreiheit finden Sie unter <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Figma</a>.</span><span class="sxs-lookup"><span data-stu-id="4324b-213">For information on accessibility, see <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Figma</a>.</span></span>

## <a name="resources"></a><span data-ttu-id="4324b-214">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="4324b-214">Resources</span></span>

* <span data-ttu-id="4324b-215"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Figma-Datei für Microsoft Teams-Besprechungs Erweiterungen</a></span><span class="sxs-lookup"><span data-stu-id="4324b-215"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Microsoft Teams meeting extensions Figma file</a></span></span>
* [<span data-ttu-id="4324b-216">Entwurfsrichtlinien für Registerkarten</span><span class="sxs-lookup"><span data-stu-id="4324b-216">Tabs design guidelines</span></span>](../../tabs/design/tabs.md)
* [<span data-ttu-id="4324b-217">Entwurfsrichtlinien für Tabs für mobile Geräte</span><span class="sxs-lookup"><span data-stu-id="4324b-217">Tabs design guidelines for mobile</span></span>](../../tabs/design/tabs-mobile.md)

## <a name="validate-your-design"></a><span data-ttu-id="4324b-218">Überprüfen des Designs</span><span class="sxs-lookup"><span data-stu-id="4324b-218">Validate your design</span></span>

<span data-ttu-id="4324b-219">Wenn Sie Ihre APP in AppSource veröffentlichen möchten, sollten Sie sich mit den Entwurfsproblemen vertraut machen, die häufig dazu führen, dass apps während der Übermittlung fehlschlagen.</span><span class="sxs-lookup"><span data-stu-id="4324b-219">If you plan to publish your app to AppSource, you should understand the design issues that commonly cause apps to fail during submission.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4324b-220">Überprüfen der Entwurfs Validierungsrichtlinien</span><span class="sxs-lookup"><span data-stu-id="4324b-220">Check design validation guidelines</span></span>](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines--most-failed-test-cases)
