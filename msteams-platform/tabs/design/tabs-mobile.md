---
title: Registerkarten auf mobilen Geräten
description: Beschreibt die Richtlinien für das Entwerfen von Registerkarten, die auf Mobilen funktionieren.
ms.topic: conceptual
localization_priority: Normal
keywords: teams design guidelines reference framework personal apps mobile tabs
ms.openlocfilehash: b9f09ce2603ee2617b8b93ba2132b900c61f2c31
ms.sourcegitcommit: 1256639fa424e3833b44207ce847a245824d48e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2021
ms.locfileid: "52088759"
---
# <a name="tabs-on-mobile"></a><span data-ttu-id="707e0-104">Registerkarten auf mobilen Geräten</span><span class="sxs-lookup"><span data-stu-id="707e0-104">Tabs on mobile</span></span>

<span data-ttu-id="707e0-105">Sie können Registerkarten in Teams mobilen Kanälen, Chats und persönlichen Apps hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="707e0-105">You can include tabs in Teams mobile channels, chats, and personal apps.</span></span>

## <a name="accessing-personal-tabs"></a><span data-ttu-id="707e0-106">Zugreifen auf persönliche Registerkarten</span><span class="sxs-lookup"><span data-stu-id="707e0-106">Accessing personal tabs</span></span>

<span data-ttu-id="707e0-107">Sie können auf persönliche Registerkarten in der App-Schublade zugreifen.</span><span class="sxs-lookup"><span data-stu-id="707e0-107">You can access personal tabs in the app drawer.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-app-drawer.png" alt-text="Abbildung der Teams mobilen App-Schublade." border="false":::

## <a name="accessing-channel-tabs"></a><span data-ttu-id="707e0-109">Zugreifen auf Kanalregisterkarten</span><span class="sxs-lookup"><span data-stu-id="707e0-109">Accessing channel tabs</span></span>

<span data-ttu-id="707e0-110">Sie können auf Kanal- und Gruppenregisterkarten zugreifen, indem Sie die Schaltfläche **Mehr** im Kanal oder Chat auswählen, in dem sie hinzugefügt wurden.</span><span class="sxs-lookup"><span data-stu-id="707e0-110">You can access channel and group tabs by selecting the **More** button in the channel or chat in which they've been added.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab.png" alt-text="Abbildung einer Teams mobilen Registerkarte." border="false":::

## <a name="design-considerations"></a><span data-ttu-id="707e0-112">Überlegungen zum Entwurf</span><span class="sxs-lookup"><span data-stu-id="707e0-112">Design considerations</span></span>

<span data-ttu-id="707e0-113">Unsere mobile Plattform ermöglicht Apps eine immersive Erfahrung mit den App-Inhalten, die den ganzen Bildschirm außer der Hauptnavigation Teams werden.</span><span class="sxs-lookup"><span data-stu-id="707e0-113">Our mobile platform allows apps to be an immersive experience with the app content taking up all of the screen apart from main Teams navigation.</span></span> <span data-ttu-id="707e0-114">Befolgen Sie diese Richtlinien, um ein immersives Erlebnis zu Teams erstellen.</span><span class="sxs-lookup"><span data-stu-id="707e0-114">To create an immersive experience that fits with Teams, follow these guidelines.</span></span>

### <a name="responsive-design"></a><span data-ttu-id="707e0-115">Dynamisches Designs</span><span class="sxs-lookup"><span data-stu-id="707e0-115">Responsive design</span></span>

<span data-ttu-id="707e0-116">Da Ihre Registerkarte auf Geräten mit einer vielzahl von Bildschirmgrößen geöffnet werden kann, muss sie [reaktionsfähige Entwurfsprinzipien](https://www.w3schools.com/html/html_responsive.asp) befolgen.</span><span class="sxs-lookup"><span data-stu-id="707e0-116">Because your tab can be opened on devices with a wide range of screen sizes, it needs to follow [responsive design](https://www.w3schools.com/html/html_responsive.asp) principles.</span></span> <span data-ttu-id="707e0-117">Alle wichtigen Konstrukte sollten auf mobilen Geräten zugänglich sein, und die Ansichten sollten nicht verzerrt werden.</span><span class="sxs-lookup"><span data-stu-id="707e0-117">All of the key constructs should be accessible on mobile devices, and the views should not be distorted.</span></span> <span data-ttu-id="707e0-118">Stellen Sie sicher, dass beim Laden der Registerkarte auf einem mobilen Gerät über die fingerbasierte Navigation problemlos auf alle Schaltflächen und Links zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="707e0-118">Ensure that when your tab is loaded on a mobile device, all buttons and links are easily accessible using finger-based navigation.</span></span>

### <a name="layouts"></a><span data-ttu-id="707e0-119">Layouts</span><span class="sxs-lookup"><span data-stu-id="707e0-119">Layouts</span></span>

<span data-ttu-id="707e0-120">Die Auswahl des richtigen Layouts für Ihre Registerkarte ist wichtig.</span><span class="sxs-lookup"><span data-stu-id="707e0-120">Choosing the correct layout for your tab is important.</span></span> <span data-ttu-id="707e0-121">Sie sollten die Art von Informationen berücksichtigen, die Sie präsentieren, und ein Layout auswählen, das sie zur einfachen Nutzung organisiert.</span><span class="sxs-lookup"><span data-stu-id="707e0-121">You should consider the kind of information you're presenting, and choose a layout that organizes it for easy consumption.</span></span> <span data-ttu-id="707e0-122">Einige potenzielle Optionen sind unten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="707e0-122">Some potential options are outlined below.</span></span>

#### <a name="single-canvas"></a><span data-ttu-id="707e0-123">Einzelner Canvas</span><span class="sxs-lookup"><span data-stu-id="707e0-123">Single canvas</span></span>

<span data-ttu-id="707e0-124">Dies ist ein großer Bereich, in dem die Arbeit erledigt wird.</span><span class="sxs-lookup"><span data-stu-id="707e0-124">This is one large area where work gets done.</span></span> <span data-ttu-id="707e0-125">Die Teams Wiki-App folgt diesem Muster.</span><span class="sxs-lookup"><span data-stu-id="707e0-125">The Teams Wiki app follows this pattern.</span></span> <span data-ttu-id="707e0-126">Wenn Sie über eine App verfügen, die Inhalte nicht in kleinere Komponenten trennt, ist dies eine gute Passform.</span><span class="sxs-lookup"><span data-stu-id="707e0-126">If you have an app that doesn’t separate content into smaller components this would be a good fit.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-single-canvas.png" alt-text="Abbildung einer Teams mobilen Registerkarte für einen einzelnen Zeichenbereich." border="false":::

#### <a name="list"></a><span data-ttu-id="707e0-128">Liste</span><span class="sxs-lookup"><span data-stu-id="707e0-128">List</span></span>

<span data-ttu-id="707e0-129">Listen nen sich gut zum Sortieren und Filtern großer Datenmengen nen und nen, um die wichtigsten Dinge oben zu behalten.</span><span class="sxs-lookup"><span data-stu-id="707e0-129">Lists are great for sorting and filtering large quantities of data and are great at keeping the most important things at the top.</span></span> <span data-ttu-id="707e0-130">Es ist hilfreich, sortierbare Spalten zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="707e0-130">It is helpful to use sortable columns.</span></span> <span data-ttu-id="707e0-131">Aktionen können zu jedem Listenelement unter dem Auslassungsmenü hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="707e0-131">Actions can be added to each list item under the ellipsis menu.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-list.png" alt-text="Abbildung einer Teams mobilen Listenregisterkarte." border="false":::

#### <a name="grid"></a><span data-ttu-id="707e0-133">Grid</span><span class="sxs-lookup"><span data-stu-id="707e0-133">Grid</span></span>

<span data-ttu-id="707e0-134">Raster n nen nützlich sein, um Elemente zu zeigen, die hochgradig visuell sind.</span><span class="sxs-lookup"><span data-stu-id="707e0-134">Grids are useful for showing elements which are highly visual.</span></span> <span data-ttu-id="707e0-135">Es hilft, einen Filter oder ein Suchsteuerelement oben zu enthalten.</span><span class="sxs-lookup"><span data-stu-id="707e0-135">It helps to include a filter or search control at the top.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-grid.png" alt-text="Abbildung einer Teams mobilen Registerkarte mit einem Rasterlayout." border="false":::

### <a name="tabs-with-bots-on-mobile"></a><span data-ttu-id="707e0-137">Registerkarten mit Bots auf Mobilgeräten</span><span class="sxs-lookup"><span data-stu-id="707e0-137">Tabs with bots on mobile</span></span>

<span data-ttu-id="707e0-138">Das folgende Beispiel ist eine persönliche App mit Registerkarten und einem Bot.</span><span class="sxs-lookup"><span data-stu-id="707e0-138">The following example is a personal app that has tabs and a bot.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-with-bot.png" alt-text="Abbildung, die zeigt, Teams app mit Registerkarten und einem Bot." border="false":::

## <a name="ui-components"></a><span data-ttu-id="707e0-140">Benutzeroberflächenkomponenten</span><span class="sxs-lookup"><span data-stu-id="707e0-140">UI components</span></span>

### <a name="color-palettes"></a><span data-ttu-id="707e0-141">Farbpaletten</span><span class="sxs-lookup"><span data-stu-id="707e0-141">Color palettes</span></span>

<span data-ttu-id="707e0-142">Die Verwendung unserer genehmigten neutralen Palette für Hintergründe, Benachrichtigungen, Text und Schaltflächen hilft Ihrer App, sich in ihrem Teams.</span><span class="sxs-lookup"><span data-stu-id="707e0-142">Using our approved neutral palette for backgrounds, notifications, text, and buttons will help your app feel more at home in Teams.</span></span> <span data-ttu-id="707e0-143">Da Teams mobile zwei Farbthemen (hell und dunkel) hat, sollten Sie sicherstellen, dass Ihre App in beiden Designs großartig aussieht.</span><span class="sxs-lookup"><span data-stu-id="707e0-143">Since Teams mobile has two colour themes (light and dark), it’s a good idea to make sure your app looks great in both.</span></span>

#### <a name="light-color"></a><span data-ttu-id="707e0-144">Helle Farbe</span><span class="sxs-lookup"><span data-stu-id="707e0-144">Light color</span></span>

![Helle Farbpalette](../../assets/images/light-color.png)

#### <a name="dark-color"></a><span data-ttu-id="707e0-146">Dunkle Farbe</span><span class="sxs-lookup"><span data-stu-id="707e0-146">Dark color</span></span>

![Dunkle Farbpalette](../../assets/images/dark-color.png)

### <a name="buttons-and-controls"></a><span data-ttu-id="707e0-148">Schaltflächen und Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="707e0-148">Buttons and controls</span></span>

<span data-ttu-id="707e0-149">Die Art und Weise, wie Schaltflächen gestylt werden, hilft zu kommunizieren, welche Art von Aktion sie auslösen.</span><span class="sxs-lookup"><span data-stu-id="707e0-149">The way buttons are styled helps communicate what kind of action they trigger.</span></span> <span data-ttu-id="707e0-150">Wir verwalten eine vielzahl von Schaltflächen, die so formatiert sind, dass sie unterschiedliche Betonungsebenen anzeigen.</span><span class="sxs-lookup"><span data-stu-id="707e0-150">We maintain a wide range of buttons that are formatted to show different levels of emphasis.</span></span> <span data-ttu-id="707e0-151">Schaltflächen können Text, ein Symbol oder eine Kombination aus Text und einem Symbol enthalten.</span><span class="sxs-lookup"><span data-stu-id="707e0-151">Buttons can have text, an icon, or a combination of text and an icon.</span></span> <span data-ttu-id="707e0-152">Um verschiedene Ebenen in einer Hierarchie zu kommunizieren, haben wir primäre und sekundäre Schaltflächen in jeder Kategorie entworfen.</span><span class="sxs-lookup"><span data-stu-id="707e0-152">To communicate different levels in a hierarchy, we designed primary and secondary buttons within each category.</span></span>

#### <a name="buttons"></a><span data-ttu-id="707e0-153">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="707e0-153">Buttons</span></span>

<span data-ttu-id="707e0-154">Primäre und sekundäre Schaltflächen.</span><span class="sxs-lookup"><span data-stu-id="707e0-154">Primary and secondary buttons.</span></span>

![Schaltflächenbild](../../assets/images/buttons.png)

#### <a name="selection-controls"></a><span data-ttu-id="707e0-156">Auswahlsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="707e0-156">Selection controls</span></span>

<span data-ttu-id="707e0-157">Optionsfelder, Kontrollkästchen und Umschaltflächen.</span><span class="sxs-lookup"><span data-stu-id="707e0-157">Radio buttons, checkboxes, and toggles.</span></span>

![Auswahlsteuerelemente](../../assets/images/selection-controls.png)

#### <a name="chiclets-and-pills"></a><span data-ttu-id="707e0-159">Schickchen und Pillen</span><span class="sxs-lookup"><span data-stu-id="707e0-159">Chiclets and pills</span></span>

![Zichorlets und Pillen](../../assets/images/chiclets-and-pills.png)

### <a name="typography"></a><span data-ttu-id="707e0-161">Typografie</span><span class="sxs-lookup"><span data-stu-id="707e0-161">Typography</span></span>

<span data-ttu-id="707e0-162">Die Typografie sollte klar und zweckvoll sein.</span><span class="sxs-lookup"><span data-stu-id="707e0-162">Typography should be clear and purposeful.</span></span> <span data-ttu-id="707e0-163">Heben Sie wichtige Informationen hervor, und vermeiden Sie die Verwendung mehrerer Schriftarten und Größen, um Verwirrung zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="707e0-163">Emphasize important information and avoid using multiple fonts and sizes to reduce confusion.</span></span> <span data-ttu-id="707e0-164">Es wird empfohlen, den Satzfall zu verwenden und die Verwendung aller Obergrenzen für die Lokalisierung und Lesbarkeit zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="707e0-164">We recommend using sentence case and avoiding the usage of all caps for localization and legibility.</span></span>

![Mobile Typografie](../../assets/images/mobile-typography.png)

### <a name="fields-and-flyouts"></a><span data-ttu-id="707e0-166">Felder und Flyouts</span><span class="sxs-lookup"><span data-stu-id="707e0-166">Fields and flyouts</span></span>

<span data-ttu-id="707e0-167">Felder sind Bereiche, in denen Benutzer Text eingeben können.</span><span class="sxs-lookup"><span data-stu-id="707e0-167">Fields are areas where users can input text.</span></span> <span data-ttu-id="707e0-168">Flyouts sind leichter als Dialogfelder und werden im oberen Bereich angezeigt.</span><span class="sxs-lookup"><span data-stu-id="707e0-168">Flyouts are more lightweight than dialogs and appear from the top pane.</span></span>

#### <a name="list-controls"></a><span data-ttu-id="707e0-169">Steuerelemente auflisten</span><span class="sxs-lookup"><span data-stu-id="707e0-169">List controls</span></span>

![Steuerelemente für mobile Listen](../../assets/images/mobile-list-controls.png)

#### <a name="field-controls"></a><span data-ttu-id="707e0-171">Feldsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="707e0-171">Field controls</span></span>

![Steuerelemente für mobile Felde](../../assets/images/mobile-field-controls.png)

## <a name="developer-considerations"></a><span data-ttu-id="707e0-173">Überlegungen zu Entwicklern</span><span class="sxs-lookup"><span data-stu-id="707e0-173">Developer considerations</span></span>

<span data-ttu-id="707e0-174">Wenn Sie eine App erstellen, die eine Registerkarte enthält, müssen Sie berücksichtigen (und testen), wie Ihre Registerkarte sowohl auf den Android- als auch auf iOS-Microsoft Teams funktioniert.</span><span class="sxs-lookup"><span data-stu-id="707e0-174">When you're building an app that includes a tab, you need to consider (and test) how your tab will function on both the Android and iOS Microsoft Teams clients.</span></span> <span data-ttu-id="707e0-175">In den folgenden Abschnitten werden einige der wichtigsten Szenarien beschrieben, die Sie berücksichtigen müssen.</span><span class="sxs-lookup"><span data-stu-id="707e0-175">The sections below outline some of the key scenarios you need to consider.</span></span>

### <a name="authentication"></a><span data-ttu-id="707e0-176">Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="707e0-176">Authentication</span></span>

<span data-ttu-id="707e0-177">Damit die Authentifizierung auf mobilen Clients funktioniert, müssen Sie Teams JavaScript SDK auf mindestens Version 1.4.1 aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="707e0-177">For authentication to work on mobile clients, you must upgrade you Teams JavaScript SDK to at least version 1.4.1.</span></span>

### <a name="low-bandwidth-and-intermittent-connections"></a><span data-ttu-id="707e0-178">Niedrige Bandbreite und zeitweilige Verbindungen</span><span class="sxs-lookup"><span data-stu-id="707e0-178">Low bandwidth and intermittent connections</span></span>

<span data-ttu-id="707e0-179">Mobile Clients müssen regelmäßig mit geringer Bandbreite und zeitweiligen Verbindungen funktionieren.</span><span class="sxs-lookup"><span data-stu-id="707e0-179">Mobile clients regularly need to function with low bandwidth and intermittent connections.</span></span> <span data-ttu-id="707e0-180">Ihre App sollte timeouts entsprechend behandeln, indem sie dem Benutzer eine kontextbezogene Nachricht zur Verfügung stellt.</span><span class="sxs-lookup"><span data-stu-id="707e0-180">Your app should handle any timeouts appropriately by providing a contextual message to the user.</span></span> <span data-ttu-id="707e0-181">Sie sollten auch Fortschrittsindikatoren der Benutzer verwenden, um Ihren Benutzern Feedback für alle lang laufenden Prozesse zu geben.</span><span class="sxs-lookup"><span data-stu-id="707e0-181">You should also user progress indicators to provide feedback to your users for any long-running processes.</span></span>

> [!NOTE]
> <span data-ttu-id="707e0-182">Registerkarten werden auf mobilen Geräten nur aktiviert, nachdem die Anwendung einer Zulassungsliste hinzugefügt wurde, basierend auf der Eingabe des Genehmigungsteams.</span><span class="sxs-lookup"><span data-stu-id="707e0-182">Tabs are enabled on mobile only after the application is added to an allow list, based on the input of the approval team.</span></span> <span data-ttu-id="707e0-183">Um die Reaktionsfähigkeit mobiler Geräte zu überprüfen, erreichen Sie die teamsubm@microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="707e0-183">To check mobile responsiveness, reach out to teamsubm@microsoft.com.</span></span>

### <a name="testing-on-mobile-clients"></a><span data-ttu-id="707e0-184">Testen auf mobilen Clients</span><span class="sxs-lookup"><span data-stu-id="707e0-184">Testing on mobile clients</span></span>

<span data-ttu-id="707e0-185">Sie müssen überprüfen, ob Ihre Registerkarte auf mobilen Geräten unterschiedlicher Größe und Qualität ordnungsgemäß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="707e0-185">You need to validate that your tab functions properly on mobile devices of various sizes and qualities.</span></span> <span data-ttu-id="707e0-186">Für Android-Geräte können Sie [devTools](~/tabs/how-to/developer-tools.md) verwenden, um Ihre Registerkarte während der Ausführung zu debuggen.</span><span class="sxs-lookup"><span data-stu-id="707e0-186">For Android devices, you can use the [DevTools](~/tabs/how-to/developer-tools.md) to debug your tab while it is running.</span></span> <span data-ttu-id="707e0-187">Es wird empfohlen, sowohl auf Geräten mit hoher als auch auf niedriger Leistung zu testen, einschließlich eines Tablets.</span><span class="sxs-lookup"><span data-stu-id="707e0-187">We recommend that you test on both high- and low-performance devices, including a tablet.</span></span>

### <a name="distribution"></a><span data-ttu-id="707e0-188">Verteilung</span><span class="sxs-lookup"><span data-stu-id="707e0-188">Distribution</span></span>

<span data-ttu-id="707e0-189">Apps, die im Teams-Store aufgeführt sind, müssen für die mobile Verwendung genehmigt werden, damit sie im mobilen Client Teams funktionieren.</span><span class="sxs-lookup"><span data-stu-id="707e0-189">Apps listed on the Teams store must be approved for mobile use to function properly in the Teams mobile client.</span></span> <span data-ttu-id="707e0-190">Verfügbarkeit und Verhalten von Registerkarten hängen davon ab, ob Ihre App genehmigt wurde.</span><span class="sxs-lookup"><span data-stu-id="707e0-190">Tab availability and behavior depends on whether your app is approved.</span></span>

#### <a name="apps-on-teams-store-approved-for-mobile"></a><span data-ttu-id="707e0-191">Apps im Teams für Mobilgeräte genehmigt</span><span class="sxs-lookup"><span data-stu-id="707e0-191">Apps on Teams store approved for mobile</span></span>

<span data-ttu-id="707e0-192">In der folgenden Tabelle werden die Verfügbarkeit und das Verhalten von Registerkarten beschrieben, wenn die App im Teams und für die mobile Verwendung genehmigt ist.</span><span class="sxs-lookup"><span data-stu-id="707e0-192">The following table describes tab availability and behavior when the app is listed on the Teams store and approved for mobile use.</span></span>

|<span data-ttu-id="707e0-193">Funktion</span><span class="sxs-lookup"><span data-stu-id="707e0-193">Capability</span></span>   |<span data-ttu-id="707e0-194">Mobile Verfügbarkeit?</span><span class="sxs-lookup"><span data-stu-id="707e0-194">Mobile availability?</span></span>   |<span data-ttu-id="707e0-195">Mobiles Verhalten</span><span class="sxs-lookup"><span data-stu-id="707e0-195">Mobile behavior</span></span>|
|----------|-----------|------------|
|<span data-ttu-id="707e0-196">Kanal</span><span class="sxs-lookup"><span data-stu-id="707e0-196">Channel</span></span> <br /> <span data-ttu-id="707e0-197">Registerkarte "Gruppe" und "Gruppe"</span><span class="sxs-lookup"><span data-stu-id="707e0-197">and group tab</span></span>|<span data-ttu-id="707e0-198">Ja</span><span class="sxs-lookup"><span data-stu-id="707e0-198">Yes</span></span>|<span data-ttu-id="707e0-199">Die Registerkarte wird im Teams mobilen Client mithilfe der Konfiguration Ihrer App `contentUrl` geöffnet.</span><span class="sxs-lookup"><span data-stu-id="707e0-199">Tab opens in the Teams mobile client using your app's `contentUrl` configuration.</span></span>|
|<span data-ttu-id="707e0-200">Persönliche App</span><span class="sxs-lookup"><span data-stu-id="707e0-200">Personal app</span></span>|<span data-ttu-id="707e0-201">Ja</span><span class="sxs-lookup"><span data-stu-id="707e0-201">Yes</span></span>|<span data-ttu-id="707e0-202">Jede Registerkarte auf der Registerkarte persönliche App wird im Teams mobilen Client mit der entsprechenden Konfiguration `contentUrl` geöffnet.</span><span class="sxs-lookup"><span data-stu-id="707e0-202">Each tab in the personal app tab opens in the Teams mobile client using its respective `contentUrl` configuration.</span></span>|

#### <a name="apps-on-teams-store-not-approved-for-mobile"></a><span data-ttu-id="707e0-203">Apps im Teams store nicht für mobilgeräte genehmigt</span><span class="sxs-lookup"><span data-stu-id="707e0-203">Apps on Teams store not approved for mobile</span></span>

<span data-ttu-id="707e0-204">In der folgenden Tabelle werden die Verfügbarkeit und das Verhalten von Registerkarten beschrieben, wenn die App im Teams, aber nicht für die mobile Verwendung genehmigt ist.</span><span class="sxs-lookup"><span data-stu-id="707e0-204">The following table describes tab availability and behavior when the app is listed on the Teams store but not approved for mobile use.</span></span>

|<span data-ttu-id="707e0-205">Funktion</span><span class="sxs-lookup"><span data-stu-id="707e0-205">Capability</span></span>   |<span data-ttu-id="707e0-206">Mobile Verfügbarkeit?</span><span class="sxs-lookup"><span data-stu-id="707e0-206">Mobile availability?</span></span>|<span data-ttu-id="707e0-207">Mobiles Verhalten</span><span class="sxs-lookup"><span data-stu-id="707e0-207">Mobile behavior</span></span>|
|----------|-----------|------------|
|<span data-ttu-id="707e0-208">Registerkarte "Kanal" und "Gruppe"</span><span class="sxs-lookup"><span data-stu-id="707e0-208">Channel and group tab</span></span>|<span data-ttu-id="707e0-209">Ja</span><span class="sxs-lookup"><span data-stu-id="707e0-209">Yes</span></span>|<span data-ttu-id="707e0-210">Die Registerkarte wird im Standardbrowser des Geräts anstelle des Teams mobilen Clients geöffnet, der die Konfiguration Ihrer App verwendet (die auch in der Quellcodefunktion `websiteUrl` enthalten `setSettings()` [sein muss).](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest#functions)</span><span class="sxs-lookup"><span data-stu-id="707e0-210">Tab opens in the device's default browser instead of the Teams mobile client using your app's `websiteUrl` configuration (which also must be included in your source code's `setSettings()` [function](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest#functions)).</span></span> <span data-ttu-id="707e0-211">Benutzer können die Registerkarte jedoch weiterhin im mobilen Client  Teams anzeigen, indem Sie neben der App weitere auswählen und **Öffnen** auswählen, wodurch die Konfiguration Ihrer App ausgelöst `contentUrl` wird.</span><span class="sxs-lookup"><span data-stu-id="707e0-211">However, users can still view the tab in the Teams mobile client by selecting **More** next to the app and choosing **Open**, which triggers your app’s `contentUrl` configuration.</span></span>|
|<span data-ttu-id="707e0-212">Persönliche App</span><span class="sxs-lookup"><span data-stu-id="707e0-212">Personal app</span></span>|<span data-ttu-id="707e0-213">Nein</span><span class="sxs-lookup"><span data-stu-id="707e0-213">No</span></span>|<span data-ttu-id="707e0-214">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="707e0-214">Not applicable</span></span>|

#### <a name="apps-not-on-teams-store"></a><span data-ttu-id="707e0-215">Apps, die nicht im Teams sind</span><span class="sxs-lookup"><span data-stu-id="707e0-215">Apps not on Teams store</span></span>

<span data-ttu-id="707e0-216">Wenn Sie Ihre App oder Veröffentlichung querladen im App-Katalog einer Organisation, ist das Registerkartenverhalten identisch mit Teams von Microsoft für Mobile genehmigten Store-Apps.</span><span class="sxs-lookup"><span data-stu-id="707e0-216">If you're sideloading your app or publishing to an org's app catalog, tab behavior will be the same as Teams store apps approved by Microsoft for mobile.</span></span>
