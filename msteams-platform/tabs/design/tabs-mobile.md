---
title: Registerkarten auf mobilen Geräten
description: Beschreibt die Richtlinien zum Entwerfen von Registerkarten, die auf Mobilgeräten funktionieren.
ms.topic: conceptual
localization_priority: Normal
keywords: Teams entwerfen Richtlinien Referenz Framework persönliche Apps mobile Registerkarten
ms.openlocfilehash: 853ab2c52edd1f4faedcc92e6f0e8d0821b580c7
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566698"
---
# <a name="tabs-on-mobile"></a><span data-ttu-id="c02b4-104">Registerkarten auf mobilen Geräten</span><span class="sxs-lookup"><span data-stu-id="c02b4-104">Tabs on mobile</span></span>

<span data-ttu-id="c02b4-105">Sie können Registerkarten in Teams mobilen Kanälen, Chats und persönlichen Apps einschließen.</span><span class="sxs-lookup"><span data-stu-id="c02b4-105">You can include tabs in Teams mobile channels, chats, and personal apps.</span></span>

## <a name="accessing-personal-tabs"></a><span data-ttu-id="c02b4-106">Zugriff auf persönliche Registerkarten</span><span class="sxs-lookup"><span data-stu-id="c02b4-106">Accessing personal tabs</span></span>

<span data-ttu-id="c02b4-107">Sie können auf persönliche Registerkarten in der App-Schublade zugreifen.</span><span class="sxs-lookup"><span data-stu-id="c02b4-107">You can access personal tabs in the app drawer.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-app-drawer.png" alt-text="Abbildung mit der Teams mobilen App-Schublade." border="false":::

## <a name="accessing-channel-tabs"></a><span data-ttu-id="c02b4-109">Zugriff auf Kanalregisterkarten</span><span class="sxs-lookup"><span data-stu-id="c02b4-109">Accessing channel tabs</span></span>

<span data-ttu-id="c02b4-110">Sie können auf Kanal- und Gruppenregisterkarten zugreifen, indem Sie die Schaltfläche **Mehr** im Kanal oder Chat auswählen, in dem sie hinzugefügt wurden.</span><span class="sxs-lookup"><span data-stu-id="c02b4-110">You can access channel and group tabs by selecting the **More** button in the channel or chat in which they've been added.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab.png" alt-text="Abbildung mit einer Teams mobilen Registerkarte." border="false":::

## <a name="design-considerations"></a><span data-ttu-id="c02b4-112">Überlegungen zum Entwurf</span><span class="sxs-lookup"><span data-stu-id="c02b4-112">Design considerations</span></span>

<span data-ttu-id="c02b4-113">Unsere mobile Plattform ermöglicht Apps ein immersives Erlebnis mit den App-Inhalten, die den gesamten Bildschirm außer der Haupt-Teams Navigation einnehmen.</span><span class="sxs-lookup"><span data-stu-id="c02b4-113">Our mobile platform allows apps to be an immersive experience with the app content taking up all of the screen apart from main Teams navigation.</span></span> <span data-ttu-id="c02b4-114">Um ein immersives Erlebnis zu schaffen, das zu Teams passt, befolgen Sie diese Richtlinien.</span><span class="sxs-lookup"><span data-stu-id="c02b4-114">To create an immersive experience that fits with Teams, follow these guidelines.</span></span>

### <a name="responsive-design"></a><span data-ttu-id="c02b4-115">Dynamisches Designs</span><span class="sxs-lookup"><span data-stu-id="c02b4-115">Responsive design</span></span>

<span data-ttu-id="c02b4-116">Da Ihre Registerkarte auf Geräten mit einer Vielzahl von Bildschirmgrößen geöffnet werden kann, muss sie [den Grundsätzen des responsiven Designs](https://www.w3schools.com/html/html_responsive.asp) folgen.</span><span class="sxs-lookup"><span data-stu-id="c02b4-116">Because your tab can be opened on devices with a wide range of screen sizes, it needs to follow [responsive design](https://www.w3schools.com/html/html_responsive.asp) principles.</span></span> <span data-ttu-id="c02b4-117">Alle Schlüsselkonstrukte sollten auf mobilen Geräten zugänglich sein, und die Ansichten sollten nicht verzerrt werden.</span><span class="sxs-lookup"><span data-stu-id="c02b4-117">All of the key constructs should be accessible on mobile devices, and the views should not be distorted.</span></span> <span data-ttu-id="c02b4-118">Stellen Sie sicher, dass beim Laden der Registerkarte auf einem mobilen Gerät alle Schaltflächen und Links über die fingerbasierte Navigation leicht zugänglich sind.</span><span class="sxs-lookup"><span data-stu-id="c02b4-118">Ensure that when your tab is loaded on a mobile device, all buttons and links are easily accessible using finger-based navigation.</span></span>

### <a name="layouts"></a><span data-ttu-id="c02b4-119">Layouts</span><span class="sxs-lookup"><span data-stu-id="c02b4-119">Layouts</span></span>

<span data-ttu-id="c02b4-120">Es ist wichtig, das richtige Layout für Ihre Registerkarte auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="c02b4-120">Choosing the correct layout for your tab is important.</span></span> <span data-ttu-id="c02b4-121">Sie sollten die Art der Informationen berücksichtigen, die Sie präsentieren, und ein Layout auswählen, das es für den einfachen Verbrauch organisiert.</span><span class="sxs-lookup"><span data-stu-id="c02b4-121">You should consider the kind of information you're presenting, and choose a layout that organizes it for easy consumption.</span></span> <span data-ttu-id="c02b4-122">Im Folgenden werden einige mögliche Optionen erläutert.</span><span class="sxs-lookup"><span data-stu-id="c02b4-122">Some potential options are outlined below.</span></span>

#### <a name="single-canvas"></a><span data-ttu-id="c02b4-123">Einzelleinwand</span><span class="sxs-lookup"><span data-stu-id="c02b4-123">Single canvas</span></span>

<span data-ttu-id="c02b4-124">Dies ist ein großer Bereich, in dem gearbeitet wird.</span><span class="sxs-lookup"><span data-stu-id="c02b4-124">This is one large area where work gets done.</span></span> <span data-ttu-id="c02b4-125">Die Teams Wiki-App folgt diesem Muster.</span><span class="sxs-lookup"><span data-stu-id="c02b4-125">The Teams Wiki app follows this pattern.</span></span> <span data-ttu-id="c02b4-126">Wenn Sie eine App haben, die Inhalte nicht in kleinere Komponenten aufteilt, würde dies gut passen.</span><span class="sxs-lookup"><span data-stu-id="c02b4-126">If you have an app that doesn’t separate content into smaller components this would be a good fit.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-single-canvas.png" alt-text="Abbildung mit einer Teams mobilen Registerkarte für einzelne Arbeitsfläche." border="false":::

#### <a name="list"></a><span data-ttu-id="c02b4-128">Liste</span><span class="sxs-lookup"><span data-stu-id="c02b4-128">List</span></span>

<span data-ttu-id="c02b4-129">Listen eignen sich hervorragend zum Sortieren und Filtern großer Datenmengen und eignen sich hervorragend, um die wichtigsten Dinge an der Spitze zu halten.</span><span class="sxs-lookup"><span data-stu-id="c02b4-129">Lists are great for sorting and filtering large quantities of data and are great at keeping the most important things at the top.</span></span> <span data-ttu-id="c02b4-130">Es ist hilfreich, sortierbare Spalten zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="c02b4-130">It is helpful to use sortable columns.</span></span> <span data-ttu-id="c02b4-131">Aktionen können jedem Listenelement im Menü auslipsisiell hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="c02b4-131">Actions can be added to each list item under the ellipsis menu.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-list.png" alt-text="Abbildung mit einer Registerkarte Teams mobilen Liste." border="false":::

#### <a name="grid"></a><span data-ttu-id="c02b4-133">Raster</span><span class="sxs-lookup"><span data-stu-id="c02b4-133">Grid</span></span>

<span data-ttu-id="c02b4-134">Raster sind nützlich, um Elemente zu zeigen, die sehr visuell sind.</span><span class="sxs-lookup"><span data-stu-id="c02b4-134">Grids are useful for showing elements which are highly visual.</span></span> <span data-ttu-id="c02b4-135">Es hilft, einen Filter oder suchgesteuert an der Spitze einzuschließen.</span><span class="sxs-lookup"><span data-stu-id="c02b4-135">It helps to include a filter or search control at the top.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-grid.png" alt-text="Abbildung mit einer Teams mobilen Registerkarte mit einem Rasterlayout." border="false":::

### <a name="tabs-with-bots-on-mobile"></a><span data-ttu-id="c02b4-137">Tabs mit Bots auf Mobilgeräten</span><span class="sxs-lookup"><span data-stu-id="c02b4-137">Tabs with bots on mobile</span></span>

<span data-ttu-id="c02b4-138">Das folgende Beispiel ist eine persönliche App mit Registerkarten und einem Bot:</span><span class="sxs-lookup"><span data-stu-id="c02b4-138">The following example is a personal app that has tabs and a bot:</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-with-bot.png" alt-text="Abbildung zeigt, wie mobile Teams App mit Registerkarten und einem Bot." border="false":::

## <a name="ui-components"></a><span data-ttu-id="c02b4-140">UI-Komponenten</span><span class="sxs-lookup"><span data-stu-id="c02b4-140">UI components</span></span>

### <a name="color-palettes"></a><span data-ttu-id="c02b4-141">Farbpaletten</span><span class="sxs-lookup"><span data-stu-id="c02b4-141">Color palettes</span></span>

<span data-ttu-id="c02b4-142">Wenn Sie unsere genehmigte neutrale Palette für Hintergründe, Benachrichtigungen, Text und Schaltflächen verwenden, fühlen Sie sich Ihrer App in Teams mehr zu Hause.</span><span class="sxs-lookup"><span data-stu-id="c02b4-142">Using our approved neutral palette for backgrounds, notifications, text, and buttons will help your app feel more at home in Teams.</span></span> <span data-ttu-id="c02b4-143">Da Teams-Mobil zwei Farbthemen (hell und dunkel) hat, ist es eine gute Idee, sicherzustellen, dass Ihre App in beiden Bereichen gut aussieht.</span><span class="sxs-lookup"><span data-stu-id="c02b4-143">Since Teams mobile has two colour themes (light and dark), it’s a good idea to make sure your app looks great in both.</span></span>

#### <a name="light-color"></a><span data-ttu-id="c02b4-144">Lichtfarbe</span><span class="sxs-lookup"><span data-stu-id="c02b4-144">Light color</span></span>

![Helle Farbpalette](../../assets/images/light-color.png)

#### <a name="dark-color"></a><span data-ttu-id="c02b4-146">Dunkle Farbe</span><span class="sxs-lookup"><span data-stu-id="c02b4-146">Dark color</span></span>

![dunkle Farbpalette](../../assets/images/dark-color.png)

### <a name="buttons-and-controls"></a><span data-ttu-id="c02b4-148">Tasten und Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="c02b4-148">Buttons and controls</span></span>

<span data-ttu-id="c02b4-149">Die Art und Weise, wie Schaltflächen gestylt werden, hilft zu kommunizieren, welche Art von Aktion sie auslösen.</span><span class="sxs-lookup"><span data-stu-id="c02b4-149">The way buttons are styled helps communicate what kind of action they trigger.</span></span> <span data-ttu-id="c02b4-150">Wir pflegen eine breite Palette von Tasten, die formatiert sind, um verschiedene Schwerpunkte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="c02b4-150">We maintain a wide range of buttons that are formatted to show different levels of emphasis.</span></span> <span data-ttu-id="c02b4-151">Schaltflächen können Text, ein Symbol oder eine Kombination aus Text und Symbol enthalten.</span><span class="sxs-lookup"><span data-stu-id="c02b4-151">Buttons can have text, an icon, or a combination of text and an icon.</span></span> <span data-ttu-id="c02b4-152">Um verschiedene Ebenen in einer Hierarchie zu kommunizieren, haben wir primäre und sekundäre Schaltflächen innerhalb jeder Kategorie entworfen.</span><span class="sxs-lookup"><span data-stu-id="c02b4-152">To communicate different levels in a hierarchy, we designed primary and secondary buttons within each category.</span></span>

#### <a name="buttons"></a><span data-ttu-id="c02b4-153">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="c02b4-153">Buttons</span></span>

<span data-ttu-id="c02b4-154">Primäre und sekundäre Schaltflächen.</span><span class="sxs-lookup"><span data-stu-id="c02b4-154">Primary and secondary buttons.</span></span>

![Schaltflächenbild](../../assets/images/buttons.png)

#### <a name="selection-controls"></a><span data-ttu-id="c02b4-156">Auswahlsteuerungen</span><span class="sxs-lookup"><span data-stu-id="c02b4-156">Selection controls</span></span>

<span data-ttu-id="c02b4-157">Optionsfelder, Kontrollkästchen und Umschalter.</span><span class="sxs-lookup"><span data-stu-id="c02b4-157">Radio buttons, checkboxes, and toggles.</span></span>

![Auswahlsteuerungen](../../assets/images/selection-controls.png)

#### <a name="chiclets-and-pills"></a><span data-ttu-id="c02b4-159">Chiclets und Pillen</span><span class="sxs-lookup"><span data-stu-id="c02b4-159">Chiclets and pills</span></span>

![Chiclets und Pillen](../../assets/images/chiclets-and-pills.png)

### <a name="typography"></a><span data-ttu-id="c02b4-161">Typografie</span><span class="sxs-lookup"><span data-stu-id="c02b4-161">Typography</span></span>

<span data-ttu-id="c02b4-162">Die Typografie sollte klar und zielgerichtet sein.</span><span class="sxs-lookup"><span data-stu-id="c02b4-162">Typography should be clear and purposeful.</span></span> <span data-ttu-id="c02b4-163">Betonen Sie wichtige Informationen, und vermeiden Sie die Verwendung mehrerer Schriftarten und Größen, um Verwirrung zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="c02b4-163">Emphasize important information and avoid using multiple fonts and sizes to reduce confusion.</span></span> <span data-ttu-id="c02b4-164">Wir empfehlen, den Satzfall zu verwenden und die Verwendung aller Kappen für Lokalisierung und Lesbarkeit zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="c02b4-164">We recommend using sentence case and avoiding the usage of all caps for localization and legibility.</span></span>

![mobiler Typograph](../../assets/images/mobile-typography.png)

### <a name="fields-and-flyouts"></a><span data-ttu-id="c02b4-166">Felder und Flyouts</span><span class="sxs-lookup"><span data-stu-id="c02b4-166">Fields and flyouts</span></span>

<span data-ttu-id="c02b4-167">Felder sind Bereiche, in die Benutzer Text eingeben können.</span><span class="sxs-lookup"><span data-stu-id="c02b4-167">Fields are areas where users can input text.</span></span> <span data-ttu-id="c02b4-168">Flyouts sind leichter als Dialoge und werden im oberen Bereich angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c02b4-168">Flyouts are more lightweight than dialogs and appear from the top pane.</span></span>

#### <a name="list-controls"></a><span data-ttu-id="c02b4-169">Steuerelemente auflisten</span><span class="sxs-lookup"><span data-stu-id="c02b4-169">List controls</span></span>

![Mobile Listensteuerungen](../../assets/images/mobile-list-controls.png)

#### <a name="field-controls"></a><span data-ttu-id="c02b4-171">Feldkontrollen</span><span class="sxs-lookup"><span data-stu-id="c02b4-171">Field controls</span></span>

![mobile Feldsteuerungen](../../assets/images/mobile-field-controls.png)

## <a name="developer-considerations"></a><span data-ttu-id="c02b4-173">Überlegungen zu Entwicklern</span><span class="sxs-lookup"><span data-stu-id="c02b4-173">Developer considerations</span></span>

<span data-ttu-id="c02b4-174">Wenn Sie eine App erstellen, die eine Registerkarte enthält, müssen Sie berücksichtigen (und testen), wie Ihre Registerkarte sowohl auf Android- als auch auf iOS-Microsoft Teams-Clients funktioniert.</span><span class="sxs-lookup"><span data-stu-id="c02b4-174">When you're building an app that includes a tab, you need to consider (and test) how your tab will function on both the Android and iOS Microsoft Teams clients.</span></span> <span data-ttu-id="c02b4-175">In den folgenden Abschnitten werden einige der wichtigsten Szenarien beschrieben, die Sie berücksichtigen müssen.</span><span class="sxs-lookup"><span data-stu-id="c02b4-175">The sections below outline some of the key scenarios you need to consider.</span></span>

### <a name="authentication"></a><span data-ttu-id="c02b4-176">Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="c02b4-176">Authentication</span></span>

<span data-ttu-id="c02b4-177">Damit die Authentifizierung auf mobilen Clients funktioniert, müssen Sie Teams JavaScript SDK auf mindestens Version 1.4.1 aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="c02b4-177">For authentication to work on mobile clients, you must upgrade you Teams JavaScript SDK to at least version 1.4.1.</span></span>

### <a name="low-bandwidth-and-intermittent-connections"></a><span data-ttu-id="c02b4-178">Geringe Bandbreite und intermittierende Verbindungen</span><span class="sxs-lookup"><span data-stu-id="c02b4-178">Low bandwidth and intermittent connections</span></span>

<span data-ttu-id="c02b4-179">Mobile Clients müssen regelmäßig mit geringer Bandbreite und intermittierenden Verbindungen funktionieren.</span><span class="sxs-lookup"><span data-stu-id="c02b4-179">Mobile clients regularly need to function with low bandwidth and intermittent connections.</span></span> <span data-ttu-id="c02b4-180">Ihre App sollte alle Timeouts entsprechend behandeln, indem sie dem Benutzer eine kontextbezogene Nachricht bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="c02b4-180">Your app should handle any timeouts appropriately by providing a contextual message to the user.</span></span> <span data-ttu-id="c02b4-181">Sie sollten auch Benutzerfortschrittsindikatoren verwenden, um Ihren Benutzern Feedback für lang andauernde Prozesse zu geben.</span><span class="sxs-lookup"><span data-stu-id="c02b4-181">You should also user progress indicators to provide feedback to your users for any long-running processes.</span></span>

> [!NOTE]
> <span data-ttu-id="c02b4-182">Registerkarten werden auf Mobilgeräten erst aktiviert, nachdem die Anwendung basierend auf der Eingabe des Genehmigungsteams zu einer Zulassungsliste hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="c02b4-182">Tabs are enabled on mobile only after the application is added to an allow list, based on the input of the approval team.</span></span> <span data-ttu-id="c02b4-183">Um die mobile Reaktionsfähigkeit zu überprüfen, wenden Sie sich an teamsubm@microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="c02b4-183">To check mobile responsiveness, reach out to teamsubm@microsoft.com.</span></span>

### <a name="testing-on-mobile-clients"></a><span data-ttu-id="c02b4-184">Testen auf mobilen Clients</span><span class="sxs-lookup"><span data-stu-id="c02b4-184">Testing on mobile clients</span></span>

<span data-ttu-id="c02b4-185">Sie müssen überprüfen, ob Ihre Registerkarte auf mobilen Geräten unterschiedlicher Größe und Qualität ordnungsgemäß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="c02b4-185">You need to validate that your tab functions properly on mobile devices of various sizes and qualities.</span></span> <span data-ttu-id="c02b4-186">Für Android-Geräte können Sie die [DevTools](~/tabs/how-to/developer-tools.md) verwenden, um Ihre Registerkarte zu debuggen, während sie ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c02b4-186">For Android devices, you can use the [DevTools](~/tabs/how-to/developer-tools.md) to debug your tab while it is running.</span></span> <span data-ttu-id="c02b4-187">Es wird empfohlen, sowohl auf Geräten mit hoher als auch auf niedriger Leistung, einschließlich eines Tablets, zu testen.</span><span class="sxs-lookup"><span data-stu-id="c02b4-187">We recommend that you test on both high- and low-performance devices, including a tablet.</span></span>

### <a name="distribution"></a><span data-ttu-id="c02b4-188">Verteilung</span><span class="sxs-lookup"><span data-stu-id="c02b4-188">Distribution</span></span>

<span data-ttu-id="c02b4-189">Apps, die im Teams Store aufgeführt sind, müssen für die mobile Verwendung genehmigt werden, damit sie im Teams mobilen Clients ordnungsgemäß funktionieren.</span><span class="sxs-lookup"><span data-stu-id="c02b4-189">Apps listed on the Teams store must be approved for mobile use to function properly in the Teams mobile client.</span></span> <span data-ttu-id="c02b4-190">Die Verfügbarkeit und das Verhalten der Registerkartehängt hängt davon ab, ob Ihre App genehmigt wurde.</span><span class="sxs-lookup"><span data-stu-id="c02b4-190">Tab availability and behavior depends on whether your app is approved.</span></span>

#### <a name="apps-on-teams-store-approved-for-mobile"></a><span data-ttu-id="c02b4-191">Apps auf Teams Store für Mobilgeräte zugelassen</span><span class="sxs-lookup"><span data-stu-id="c02b4-191">Apps on Teams store approved for mobile</span></span>

<span data-ttu-id="c02b4-192">In der folgenden Tabelle wird die Verfügbarkeit und das Verhalten der Registerkarten beschrieben, wenn die App im Teams Store aufgeführt und für die mobile Verwendung zugelassen ist:</span><span class="sxs-lookup"><span data-stu-id="c02b4-192">The following table describes tab availability and behavior when the app is listed on the Teams store and approved for mobile use:</span></span>

|<span data-ttu-id="c02b4-193">Funktion</span><span class="sxs-lookup"><span data-stu-id="c02b4-193">Capability</span></span>   |<span data-ttu-id="c02b4-194">Mobile Verfügbarkeit?</span><span class="sxs-lookup"><span data-stu-id="c02b4-194">Mobile availability?</span></span>   |<span data-ttu-id="c02b4-195">Mobiles Verhalten</span><span class="sxs-lookup"><span data-stu-id="c02b4-195">Mobile behavior</span></span>|
|----------|-----------|------------|
|<span data-ttu-id="c02b4-196">Kanal</span><span class="sxs-lookup"><span data-stu-id="c02b4-196">Channel</span></span> <br /> <span data-ttu-id="c02b4-197">und Gruppenregisterkarte</span><span class="sxs-lookup"><span data-stu-id="c02b4-197">and group tab</span></span>|<span data-ttu-id="c02b4-198">Ja</span><span class="sxs-lookup"><span data-stu-id="c02b4-198">Yes</span></span>|<span data-ttu-id="c02b4-199">Die Registerkarte wird im Teams mobilen Clients mithilfe der Konfiguration Ihrer App `contentUrl` geöffnet.</span><span class="sxs-lookup"><span data-stu-id="c02b4-199">Tab opens in the Teams mobile client using your app's `contentUrl` configuration.</span></span>|
|<span data-ttu-id="c02b4-200">Persönliche App</span><span class="sxs-lookup"><span data-stu-id="c02b4-200">Personal app</span></span>|<span data-ttu-id="c02b4-201">Ja</span><span class="sxs-lookup"><span data-stu-id="c02b4-201">Yes</span></span>|<span data-ttu-id="c02b4-202">Jede Registerkarte in der Registerkarte Persönliche App wird im Teams mobileclient mit der entsprechenden `contentUrl` Konfiguration geöffnet.</span><span class="sxs-lookup"><span data-stu-id="c02b4-202">Each tab in the personal app tab opens in the Teams mobile client using its respective `contentUrl` configuration.</span></span>|

#### <a name="apps-on-teams-store-not-approved-for-mobile"></a><span data-ttu-id="c02b4-203">Apps auf Teams Store nicht für Mobilgeräte zugelassen</span><span class="sxs-lookup"><span data-stu-id="c02b4-203">Apps on Teams store not approved for mobile</span></span>

<span data-ttu-id="c02b4-204">In der folgenden Tabelle wird die Verfügbarkeit und das Verhalten der Registerkarten beschrieben, wenn die App im Teams Store aufgeführt, aber nicht für die mobile Verwendung zugelassen ist:</span><span class="sxs-lookup"><span data-stu-id="c02b4-204">The following table describes tab availability and behavior when the app is listed on the Teams store but not approved for mobile use:</span></span>

| <span data-ttu-id="c02b4-205">Funktion</span><span class="sxs-lookup"><span data-stu-id="c02b4-205">Capability</span></span> | <span data-ttu-id="c02b4-206">Mobile Verfügbarkeit?</span><span class="sxs-lookup"><span data-stu-id="c02b4-206">Mobile availability?</span></span> | <span data-ttu-id="c02b4-207">Mobiles Verhalten</span><span class="sxs-lookup"><span data-stu-id="c02b4-207">Mobile behavior</span></span> |
|----------|-----------|------------|
|<span data-ttu-id="c02b4-208">Kanal- und Gruppenregisterkarte</span><span class="sxs-lookup"><span data-stu-id="c02b4-208">Channel and group tab</span></span>|<span data-ttu-id="c02b4-209">Ja</span><span class="sxs-lookup"><span data-stu-id="c02b4-209">Yes</span></span>|<span data-ttu-id="c02b4-210">Die Registerkarte wird im Standardbrowser des Geräts anstelle des Teams mobilen Clients mithilfe der Konfiguration Ihrer App `websiteUrl` geöffnet, die ebenfalls in die Funktion Ihres Quellcodes einbezogen werden `setSettings()` [](/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest#functions&preserve-view=true)muss.</span><span class="sxs-lookup"><span data-stu-id="c02b4-210">Tab opens in the device's default browser instead of the Teams mobile client using your app's `websiteUrl` configuration, which also must be included in your source code's `setSettings()` [function](/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest#functions&preserve-view=true).</span></span> <span data-ttu-id="c02b4-211">Benutzer können die Registerkarte jedoch weiterhin im Teams mobilen Clients anzeigen, indem sie neben der App **Mehr** auswählen und **Öffnen** auswählen, was die Konfiguration Ihrer App `contentUrl` auslöst.</span><span class="sxs-lookup"><span data-stu-id="c02b4-211">However, users can still view the tab in the Teams mobile client by selecting **More** next to the app and choosing **Open**, which triggers your app’s `contentUrl` configuration.</span></span>|
|<span data-ttu-id="c02b4-212">Persönliche App</span><span class="sxs-lookup"><span data-stu-id="c02b4-212">Personal app</span></span>|<span data-ttu-id="c02b4-213">Nein</span><span class="sxs-lookup"><span data-stu-id="c02b4-213">No</span></span>|<span data-ttu-id="c02b4-214">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="c02b4-214">Not applicable</span></span>|

#### <a name="apps-not-on-teams-store"></a><span data-ttu-id="c02b4-215">Apps, die nicht auf Teams Store sind</span><span class="sxs-lookup"><span data-stu-id="c02b4-215">Apps not on Teams store</span></span>

<span data-ttu-id="c02b4-216">Wenn Sie Ihre App nebeneinander laden oder im App-Katalog einer Organisation veröffentlichen, entspricht das Tabstoppverhalten mit Teams Store-Apps, die von Microsoft für Mobilgeräte genehmigt wurden.</span><span class="sxs-lookup"><span data-stu-id="c02b4-216">If you're sideloading your app or publishing to an org's app catalog, tab behavior will be the same as Teams store apps approved by Microsoft for mobile.</span></span>
