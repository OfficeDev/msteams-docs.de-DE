---
title: Registerkarten auf mobilen Geräten
description: Beschreibt die Richtlinien für das Entwerfen von Registerkarten, die auf Mobilen funktionieren.
ms.topic: conceptual
localization_priority: Normal
keywords: teams design guidelines reference framework personal apps mobile tabs
ms.openlocfilehash: cdcaddf5ba0fb18537e87daa4b459c7377225f76
ms.sourcegitcommit: d90c5dafea09e2893dea8da46ee49516bbaa04b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2021
ms.locfileid: "52075696"
---
# <a name="tabs-on-mobile"></a><span data-ttu-id="f1f40-104">Registerkarten auf mobilen Geräten</span><span class="sxs-lookup"><span data-stu-id="f1f40-104">Tabs on mobile</span></span>

<span data-ttu-id="f1f40-105">Sie können Registerkarten in mobilen Teams-Kanälen, Chats und persönlichen Apps hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f1f40-105">You can include tabs in Teams mobile channels, chats, and personal apps.</span></span>

## <a name="accessing-personal-tabs"></a><span data-ttu-id="f1f40-106">Zugreifen auf persönliche Registerkarten</span><span class="sxs-lookup"><span data-stu-id="f1f40-106">Accessing personal tabs</span></span>

<span data-ttu-id="f1f40-107">Sie können auf persönliche Registerkarten in der App-Schublade zugreifen.</span><span class="sxs-lookup"><span data-stu-id="f1f40-107">You can access personal tabs in the app drawer.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-app-drawer.png" alt-text="Abbildung der Mobile -App-Schublade von Teams." border="false":::

## <a name="accessing-channel-tabs"></a><span data-ttu-id="f1f40-109">Zugreifen auf Kanalregisterkarten</span><span class="sxs-lookup"><span data-stu-id="f1f40-109">Accessing channel tabs</span></span>

<span data-ttu-id="f1f40-110">Sie können auf Kanal- und Gruppenregisterkarten zugreifen, indem Sie die Schaltfläche **Mehr** im Kanal oder Chat auswählen, in dem sie hinzugefügt wurden.</span><span class="sxs-lookup"><span data-stu-id="f1f40-110">You can access channel and group tabs by selecting the **More** button in the channel or chat in which they've been added.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab.png" alt-text="Abbildung einer mobilen Registerkarte &quot;Teams&quot;." border="false":::

## <a name="design-considerations"></a><span data-ttu-id="f1f40-112">Überlegungen zum Entwurf</span><span class="sxs-lookup"><span data-stu-id="f1f40-112">Design considerations</span></span>

<span data-ttu-id="f1f40-113">Unsere mobile Plattform ermöglicht Apps eine immersive Erfahrung mit den App-Inhalten, die den ganzen Bildschirm außer der Hauptnavigation von Teams nutzen.</span><span class="sxs-lookup"><span data-stu-id="f1f40-113">Our mobile platform allows apps to be an immersive experience with the app content taking up all of the screen apart from main Teams navigation.</span></span> <span data-ttu-id="f1f40-114">Befolgen Sie diese Richtlinien, um ein immersives Erlebnis zu erstellen, das zu Teams passt.</span><span class="sxs-lookup"><span data-stu-id="f1f40-114">To create an immersive experience that fits with Teams, follow these guidelines.</span></span>

### <a name="responsive-design"></a><span data-ttu-id="f1f40-115">Dynamisches Designs</span><span class="sxs-lookup"><span data-stu-id="f1f40-115">Responsive design</span></span>

<span data-ttu-id="f1f40-116">Da Ihre Registerkarte auf Geräten mit einer vielzahl von Bildschirmgrößen geöffnet werden kann, muss sie [reaktionsfähige Entwurfsprinzipien](https://www.w3schools.com/html/html_responsive.asp) befolgen.</span><span class="sxs-lookup"><span data-stu-id="f1f40-116">Because your tab can be opened on devices with a wide range of screen sizes, it needs to follow [responsive design](https://www.w3schools.com/html/html_responsive.asp) principles.</span></span> <span data-ttu-id="f1f40-117">Alle wichtigen Konstrukte sollten auf mobilen Geräten zugänglich sein, und die Ansichten sollten nicht verzerrt werden.</span><span class="sxs-lookup"><span data-stu-id="f1f40-117">All of the key constructs should be accessible on mobile devices, and the views should not be distorted.</span></span> <span data-ttu-id="f1f40-118">Stellen Sie sicher, dass beim Laden der Registerkarte auf einem mobilen Gerät über die fingerbasierte Navigation problemlos auf alle Schaltflächen und Links zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="f1f40-118">Ensure that when your tab is loaded on a mobile device, all buttons and links are easily accessible using finger-based navigation.</span></span>

### <a name="layouts"></a><span data-ttu-id="f1f40-119">Layouts</span><span class="sxs-lookup"><span data-stu-id="f1f40-119">Layouts</span></span>

<span data-ttu-id="f1f40-120">Die Auswahl des richtigen Layouts für Ihre Registerkarte ist wichtig.</span><span class="sxs-lookup"><span data-stu-id="f1f40-120">Choosing the correct layout for your tab is important.</span></span> <span data-ttu-id="f1f40-121">Sie sollten die Art von Informationen berücksichtigen, die Sie präsentieren, und ein Layout auswählen, das sie zur einfachen Nutzung organisiert.</span><span class="sxs-lookup"><span data-stu-id="f1f40-121">You should consider the kind of information you're presenting, and choose a layout that organizes it for easy consumption.</span></span> <span data-ttu-id="f1f40-122">Einige potenzielle Optionen sind unten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="f1f40-122">Some potential options are outlined below.</span></span>

#### <a name="single-canvas"></a><span data-ttu-id="f1f40-123">Einzelner Canvas</span><span class="sxs-lookup"><span data-stu-id="f1f40-123">Single canvas</span></span>

<span data-ttu-id="f1f40-124">Dies ist ein großer Bereich, in dem die Arbeit erledigt wird.</span><span class="sxs-lookup"><span data-stu-id="f1f40-124">This is one large area where work gets done.</span></span> <span data-ttu-id="f1f40-125">Die Teams Wiki-App folgt diesem Muster.</span><span class="sxs-lookup"><span data-stu-id="f1f40-125">The Teams Wiki app follows this pattern.</span></span> <span data-ttu-id="f1f40-126">Wenn Sie über eine App verfügen, die Inhalte nicht in kleinere Komponenten trennt, ist dies eine gute Passform.</span><span class="sxs-lookup"><span data-stu-id="f1f40-126">If you have an app that doesn’t separate content into smaller components this would be a good fit.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-single-canvas.png" alt-text="Abbildung einer mobilen Registerkarte für einen einzelnen Zeichenbereich von Teams." border="false":::

#### <a name="list"></a><span data-ttu-id="f1f40-128">Liste</span><span class="sxs-lookup"><span data-stu-id="f1f40-128">List</span></span>

<span data-ttu-id="f1f40-129">Listen nen sich gut zum Sortieren und Filtern großer Datenmengen nen und nen, um die wichtigsten Dinge oben zu behalten.</span><span class="sxs-lookup"><span data-stu-id="f1f40-129">Lists are great for sorting and filtering large quantities of data and are great at keeping the most important things at the top.</span></span> <span data-ttu-id="f1f40-130">Es ist hilfreich, sortierbare Spalten zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="f1f40-130">It is helpful to use sortable columns.</span></span> <span data-ttu-id="f1f40-131">Aktionen können zu jedem Listenelement unter dem Auslassungsmenü hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="f1f40-131">Actions can be added to each list item under the ellipsis menu.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-list.png" alt-text="Abbildung einer mobilen Listenregisterkarte von Teams." border="false":::

#### <a name="grid"></a><span data-ttu-id="f1f40-133">Grid</span><span class="sxs-lookup"><span data-stu-id="f1f40-133">Grid</span></span>

<span data-ttu-id="f1f40-134">Raster n nen nützlich sein, um Elemente zu zeigen, die hochgradig visuell sind.</span><span class="sxs-lookup"><span data-stu-id="f1f40-134">Grids are useful for showing elements which are highly visual.</span></span> <span data-ttu-id="f1f40-135">Es hilft, einen Filter oder ein Suchsteuerelement oben zu enthalten.</span><span class="sxs-lookup"><span data-stu-id="f1f40-135">It helps to include a filter or search control at the top.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-grid.png" alt-text="Abbildung einer mobilen Registerkarte von Teams mit einem Rasterlayout." border="false":::

### <a name="tabs-with-bots-on-mobile"></a><span data-ttu-id="f1f40-137">Registerkarten mit Bots auf Mobilgeräten</span><span class="sxs-lookup"><span data-stu-id="f1f40-137">Tabs with bots on mobile</span></span>

<span data-ttu-id="f1f40-138">Das folgende Beispiel ist eine persönliche App mit Registerkarten und einem Bot.</span><span class="sxs-lookup"><span data-stu-id="f1f40-138">The following example is a personal app that has tabs and a bot.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-with-bot.png" alt-text="Abbildung der mobilen Teams-App mit Registerkarten und einem Bot." border="false":::

## <a name="ui-components"></a><span data-ttu-id="f1f40-140">Benutzeroberflächenkomponenten</span><span class="sxs-lookup"><span data-stu-id="f1f40-140">UI components</span></span>

### <a name="color-palettes"></a><span data-ttu-id="f1f40-141">Farbpaletten</span><span class="sxs-lookup"><span data-stu-id="f1f40-141">Color palettes</span></span>

<span data-ttu-id="f1f40-142">Die Verwendung unserer genehmigten neutralen Palette für Hintergründe, Benachrichtigungen, Text und Schaltflächen hilft Ihrer App, sich in Teams wohler zu fühlen.</span><span class="sxs-lookup"><span data-stu-id="f1f40-142">Using our approved neutral palette for backgrounds, notifications, text, and buttons will help your app feel more at home in Teams.</span></span> <span data-ttu-id="f1f40-143">Da Teams mobile zwei Farbthemen (hell und dunkel) hat, sollten Sie sicherstellen, dass Ihre App in beiden Designs großartig aussieht.</span><span class="sxs-lookup"><span data-stu-id="f1f40-143">Since Teams mobile has two colour themes (light and dark), it’s a good idea to make sure your app looks great in both.</span></span>

#### <a name="light-color"></a><span data-ttu-id="f1f40-144">Helle Farbe</span><span class="sxs-lookup"><span data-stu-id="f1f40-144">Light color</span></span>

![Helle Farbpalette](../../assets/images/light-color.png)

#### <a name="dark-color"></a><span data-ttu-id="f1f40-146">Dunkle Farbe</span><span class="sxs-lookup"><span data-stu-id="f1f40-146">Dark color</span></span>

![Dunkle Farbpalette](../../assets/images/dark-color.png)

### <a name="buttons-and-controls"></a><span data-ttu-id="f1f40-148">Schaltflächen und Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="f1f40-148">Buttons and controls</span></span>

<span data-ttu-id="f1f40-149">Die Art und Weise, wie Schaltflächen gestylt werden, hilft zu kommunizieren, welche Art von Aktion sie auslösen.</span><span class="sxs-lookup"><span data-stu-id="f1f40-149">The way buttons are styled helps communicate what kind of action they trigger.</span></span> <span data-ttu-id="f1f40-150">Wir verwalten eine vielzahl von Schaltflächen, die so formatiert sind, dass sie unterschiedliche Betonungsebenen anzeigen.</span><span class="sxs-lookup"><span data-stu-id="f1f40-150">We maintain a wide range of buttons that are formatted to show different levels of emphasis.</span></span> <span data-ttu-id="f1f40-151">Schaltflächen können Text, ein Symbol oder eine Kombination aus Text und einem Symbol enthalten.</span><span class="sxs-lookup"><span data-stu-id="f1f40-151">Buttons can have text, an icon, or a combination of text and an icon.</span></span> <span data-ttu-id="f1f40-152">Um verschiedene Ebenen in einer Hierarchie zu kommunizieren, haben wir primäre und sekundäre Schaltflächen in jeder Kategorie entworfen.</span><span class="sxs-lookup"><span data-stu-id="f1f40-152">To communicate different levels in a hierarchy, we designed primary and secondary buttons within each category.</span></span>

#### <a name="buttons"></a><span data-ttu-id="f1f40-153">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="f1f40-153">Buttons</span></span>

<span data-ttu-id="f1f40-154">Primäre und sekundäre Schaltflächen.</span><span class="sxs-lookup"><span data-stu-id="f1f40-154">Primary and secondary buttons.</span></span>

![Schaltflächenbild](../../assets/images/buttons.png)

#### <a name="selection-controls"></a><span data-ttu-id="f1f40-156">Auswahlsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="f1f40-156">Selection controls</span></span>

<span data-ttu-id="f1f40-157">Optionsfelder, Kontrollkästchen und Umschaltflächen.</span><span class="sxs-lookup"><span data-stu-id="f1f40-157">Radio buttons, checkboxes, and toggles.</span></span>

![Auswahlsteuerelemente](../../assets/images/selection-controls.png)

#### <a name="chiclets-and-pills"></a><span data-ttu-id="f1f40-159">Schickchen und Pillen</span><span class="sxs-lookup"><span data-stu-id="f1f40-159">Chiclets and pills</span></span>

![Zichorlets und Pillen](../../assets/images/chiclets-and-pills.png)

### <a name="typography"></a><span data-ttu-id="f1f40-161">Typografie</span><span class="sxs-lookup"><span data-stu-id="f1f40-161">Typography</span></span>

<span data-ttu-id="f1f40-162">Die Typografie sollte klar und zweckvoll sein.</span><span class="sxs-lookup"><span data-stu-id="f1f40-162">Typography should be clear and purposeful.</span></span> <span data-ttu-id="f1f40-163">Heben Sie wichtige Informationen hervor, und vermeiden Sie die Verwendung mehrerer Schriftarten und Größen, um Verwirrung zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="f1f40-163">Emphasize important information and avoid using multiple fonts and sizes to reduce confusion.</span></span> <span data-ttu-id="f1f40-164">Es wird empfohlen, den Satzfall zu verwenden und die Verwendung aller Obergrenzen für die Lokalisierung und Lesbarkeit zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="f1f40-164">We recommend using sentence case and avoiding the usage of all caps for localization and legibility.</span></span>

![Mobile Typografie](../../assets/images/mobile-typography.png)

### <a name="fields-and-flyouts"></a><span data-ttu-id="f1f40-166">Felder und Flyouts</span><span class="sxs-lookup"><span data-stu-id="f1f40-166">Fields and flyouts</span></span>

<span data-ttu-id="f1f40-167">Felder sind Bereiche, in denen Benutzer Text eingeben können.</span><span class="sxs-lookup"><span data-stu-id="f1f40-167">Fields are areas where users can input text.</span></span> <span data-ttu-id="f1f40-168">Flyouts sind leichter als Dialogfelder und werden im oberen Bereich angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f1f40-168">Flyouts are more lightweight than dialogs and appear from the top pane.</span></span>

#### <a name="list-controls"></a><span data-ttu-id="f1f40-169">Steuerelemente auflisten</span><span class="sxs-lookup"><span data-stu-id="f1f40-169">List controls</span></span>

![Steuerelemente für mobile Listen](../../assets/images/mobile-list-controls.png)

#### <a name="field-controls"></a><span data-ttu-id="f1f40-171">Feldsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="f1f40-171">Field controls</span></span>

![Steuerelemente für mobile Felde](../../assets/images/mobile-field-controls.png)

## <a name="developer-considerations"></a><span data-ttu-id="f1f40-173">Überlegungen zu Entwicklern</span><span class="sxs-lookup"><span data-stu-id="f1f40-173">Developer considerations</span></span>

<span data-ttu-id="f1f40-174">Wenn Sie eine App erstellen, die eine Registerkarte enthält, müssen Sie berücksichtigen (und testen), wie Ihre Registerkarte sowohl auf den Android- als auch auf iOS Microsoft Teams-Clients funktioniert.</span><span class="sxs-lookup"><span data-stu-id="f1f40-174">When you're building an app that includes a tab, you need to consider (and test) how your tab will function on both the Android and iOS Microsoft Teams clients.</span></span> <span data-ttu-id="f1f40-175">In den folgenden Abschnitten werden einige der wichtigsten Szenarien beschrieben, die Sie berücksichtigen müssen.</span><span class="sxs-lookup"><span data-stu-id="f1f40-175">The sections below outline some of the key scenarios you need to consider.</span></span>

### <a name="authentication"></a><span data-ttu-id="f1f40-176">Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="f1f40-176">Authentication</span></span>

<span data-ttu-id="f1f40-177">Damit die Authentifizierung auf mobilen Clients funktioniert, müssen Sie das Teams JavaScript SDK auf mindestens Version 1.4.1 aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="f1f40-177">For authentication to work on mobile clients, you must upgrade you Teams JavaScript SDK to at least version 1.4.1.</span></span>

### <a name="low-bandwidth-and-intermittent-connections"></a><span data-ttu-id="f1f40-178">Niedrige Bandbreite und zeitweilige Verbindungen</span><span class="sxs-lookup"><span data-stu-id="f1f40-178">Low bandwidth and intermittent connections</span></span>

<span data-ttu-id="f1f40-179">Mobile Clients müssen regelmäßig mit geringer Bandbreite und zeitweiligen Verbindungen funktionieren.</span><span class="sxs-lookup"><span data-stu-id="f1f40-179">Mobile clients regularly need to function with low bandwidth and intermittent connections.</span></span> <span data-ttu-id="f1f40-180">Ihre App sollte timeouts entsprechend behandeln, indem sie dem Benutzer eine kontextbezogene Nachricht zur Verfügung stellt.</span><span class="sxs-lookup"><span data-stu-id="f1f40-180">Your app should handle any timeouts appropriately by providing a contextual message to the user.</span></span> <span data-ttu-id="f1f40-181">Sie sollten auch Fortschrittsindikatoren der Benutzer verwenden, um Ihren Benutzern Feedback für alle lang laufenden Prozesse zu geben.</span><span class="sxs-lookup"><span data-stu-id="f1f40-181">You should also user progress indicators to provide feedback to your users for any long-running processes.</span></span>

> [!NOTE]
> <span data-ttu-id="f1f40-182">Registerkarten werden auf mobilen Geräten nur aktiviert, nachdem die Anwendung einer Zulassungsliste hinzugefügt wurde, basierend auf der Eingabe des Genehmigungsteams.</span><span class="sxs-lookup"><span data-stu-id="f1f40-182">Tabs are enabled on mobile only after the application is added to an allow list, based on the input of the approval team.</span></span> <span data-ttu-id="f1f40-183">Um die Reaktionsfähigkeit mobiler Geräte zu überprüfen, erreichen Sie die teamsubm@microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="f1f40-183">To check mobile responsiveness, reach out to teamsubm@microsoft.com.</span></span>

### <a name="testing-on-mobile-clients"></a><span data-ttu-id="f1f40-184">Testen auf mobilen Clients</span><span class="sxs-lookup"><span data-stu-id="f1f40-184">Testing on mobile clients</span></span>

<span data-ttu-id="f1f40-185">Sie müssen überprüfen, ob Ihre Registerkarte auf mobilen Geräten unterschiedlicher Größe und Qualität ordnungsgemäß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="f1f40-185">You need to validate that your tab functions properly on mobile devices of various sizes and qualities.</span></span> <span data-ttu-id="f1f40-186">Für Android-Geräte können Sie [devTools](~/tabs/how-to/developer-tools.md) verwenden, um Ihre Registerkarte während der Ausführung zu debuggen.</span><span class="sxs-lookup"><span data-stu-id="f1f40-186">For Android devices, you can use the [DevTools](~/tabs/how-to/developer-tools.md) to debug your tab while it is running.</span></span> <span data-ttu-id="f1f40-187">Es wird empfohlen, sowohl auf Geräten mit hoher und niedriger Leistung als auch auf einem Tablet zu testen.</span><span class="sxs-lookup"><span data-stu-id="f1f40-187">We recommend that you test on both high and low performing devices, as well as on a tablet.</span></span>

### <a name="distribution"></a><span data-ttu-id="f1f40-188">Verteilung</span><span class="sxs-lookup"><span data-stu-id="f1f40-188">Distribution</span></span>

<span data-ttu-id="f1f40-189">Apps, die im Teams Store aufgeführt sind, müssen für die mobile Verwendung genehmigt werden, damit sie im mobilen Teams-Client ordnungsgemäß funktionieren.</span><span class="sxs-lookup"><span data-stu-id="f1f40-189">Apps listed on the Teams store must be approved for mobile use to function properly in the Teams mobile client.</span></span> <span data-ttu-id="f1f40-190">Das Verhalten von Registerkarten hängt davon ab, ob Ihre App genehmigt ist.</span><span class="sxs-lookup"><span data-stu-id="f1f40-190">How tabs behave depends on whether your app is approved.</span></span>

#### <a name="channel-and-group-tab-behavior"></a><span data-ttu-id="f1f40-191">Kanal- und Gruppenregisterkartenverhalten</span><span class="sxs-lookup"><span data-stu-id="f1f40-191">Channel and group tab behavior</span></span>

* <span data-ttu-id="f1f40-192">**Verhalten bei Genehmigung:** Wird im mobilen Teams-Client mithilfe der Konfiguration Ihrer App `contentUrl` geöffnet.</span><span class="sxs-lookup"><span data-stu-id="f1f40-192">**Behavior when approved**: Opens in the Teams mobile client using your app's `contentUrl` configuration.</span></span>
* <span data-ttu-id="f1f40-193">**Verhalten bei nicht genehmigter** Genehmigung : Wird im Standardbrowser des Geräts mithilfe der Konfiguration Ihrer App geöffnet (die auch in der Quellcodefunktion `websiteUrl` enthalten sein `setSettings()` muss).</span><span class="sxs-lookup"><span data-stu-id="f1f40-193">**Behavior when not approved**: Opens in the device’s default browser using your app's `websiteUrl` configuration (which also must be included in your source code's `setSettings()` function).</span></span> <span data-ttu-id="f1f40-194">Benutzer können die Registerkarte jedoch weiterhin im mobilen Teams-Client laden, indem sie neben der App Weitere auswählen und **Öffnen** auswählen, wodurch die Konfiguration Ihrer App ausgelöst  `contentUrl` wird.</span><span class="sxs-lookup"><span data-stu-id="f1f40-194">However, users can still load the tab in the Teams mobile client by selecting **More** next to the app and choosing **Open**, which triggers your app’s `contentUrl` configuration.</span></span>

#### <a name="personal-app-behavior"></a><span data-ttu-id="f1f40-195">Verhalten von persönlichen Apps</span><span class="sxs-lookup"><span data-stu-id="f1f40-195">Personal app behavior</span></span>

* <span data-ttu-id="f1f40-196">**Verhalten bei Genehmigung:** Jede Registerkarte in der persönlichen App wird im mobilen Teams-Client mit der entsprechenden Konfiguration `contentUrl` angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f1f40-196">**Behavior when approved**: Each tab in the personal app displays in the Teams mobile client using their respective `contentUrl` configuration.</span></span>
* <span data-ttu-id="f1f40-197">**Verhalten bei nicht genehmigter** Genehmigung: Die persönliche App ist im mobilen Teams-Client nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="f1f40-197">**Behavior when not approved**: The personal app is unavailable in the Teams mobile client.</span></span>

#### <a name="non-teams-store-app-behavior"></a><span data-ttu-id="f1f40-198">Verhalten von Nicht-Teams-Store-Apps</span><span class="sxs-lookup"><span data-stu-id="f1f40-198">Non-Teams store app behavior</span></span>

<span data-ttu-id="f1f40-199">Wenn Sie Ihre App oder Veröffentlichung querladen im App-Katalog einer Organisation, ist das Registerkartenverhalten mit den von Microsoft für Mobile genehmigten Microsoft Store-Apps identisch.</span><span class="sxs-lookup"><span data-stu-id="f1f40-199">If you're sideloading your app or publishing to an org's app catalog, tab behavior will be the same as Teams store apps approved by Microsoft for mobile.</span></span>
