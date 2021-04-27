---
title: Registerkarten auf mobilen Geräten
description: Beschreibt die Richtlinien für das Entwerfen von Registerkarten, die auf Mobilen funktionieren.
ms.topic: conceptual
localization_priority: Normal
keywords: teams design guidelines reference framework personal apps mobile tabs
ms.openlocfilehash: 6459d6af7899859f25b28587021e26ce6440fbef
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020408"
---
# <a name="tabs-on-mobile"></a><span data-ttu-id="de0bb-104">Registerkarten auf mobilen Geräten</span><span class="sxs-lookup"><span data-stu-id="de0bb-104">Tabs on mobile</span></span>

> [!NOTE]
> <span data-ttu-id="de0bb-105">Wenn Sie ihre Kanal-/Gruppenregisterkarte auf mobilen Teams-Clients anzeigen möchten, muss die Konfiguration einen Wert für die Eigenschaft `setSettings()` `websiteUrl` haben (siehe unten).</span><span class="sxs-lookup"><span data-stu-id="de0bb-105">If you choose to have your channel/group tab appear on Teams mobile clients, the `setSettings()` configuration must have a value for the `websiteUrl` property (see below).</span></span>

<span data-ttu-id="de0bb-106">Benutzerdefinierte Registerkarten können Teil eines Kanals, Eines Gruppenchats oder einer persönlichen App sein (Apps, die statische Registerkarten und/oder einen 1:1-Bot enthalten).</span><span class="sxs-lookup"><span data-stu-id="de0bb-106">Custom tabs can be part of a channel, group chat, or personal app (apps that contain static tabs and/or a one-to-one bot).</span></span>

<span data-ttu-id="de0bb-107">Persönliche Apps sind auf mobilen Clients in der App-Schublade verfügbar.</span><span class="sxs-lookup"><span data-stu-id="de0bb-107">Personal apps are available on mobile clients in the app drawer.</span></span> <span data-ttu-id="de0bb-108">Die App kann nur von einem Desktop- oder Webclient installiert werden und kann bis zu 24 Stunden dauern, bis sie auf mobilen Clients angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="de0bb-108">The app can only be installed from a desktop or web client, and can take up to 24 hours to appear on mobile clients.</span></span> <span data-ttu-id="de0bb-109">Alternativ können Sie ein Erneutes Laden auf dem mobilen Client erzwingen, indem Sie sich ab- und anmelden.</span><span class="sxs-lookup"><span data-stu-id="de0bb-109">Alternatively, you can enforce a reload on the mobile client by signing out and in.</span></span> <span data-ttu-id="de0bb-110">Dadurch sollte die mobile App sofort verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="de0bb-110">This should make the mobile app available right away.</span></span>

<span data-ttu-id="de0bb-111">Kanalregisterkarten sind auch auf Mobilgeräten verfügbar.</span><span class="sxs-lookup"><span data-stu-id="de0bb-111">Channel tabs are also available on mobile.</span></span> <span data-ttu-id="de0bb-112">Das Standardverhalten besteht derzeit in der Verwendung Von zum Starten `websiteUrl` Ihrer Registerkarte in einem Browserfenster.</span><span class="sxs-lookup"><span data-stu-id="de0bb-112">The default behavior is currently to use your `websiteUrl` to launch your tab in a browser window.</span></span> <span data-ttu-id="de0bb-113">Sie können jedoch auf einem mobilen Client geladen werden, indem Sie auf das Überlaufmenü neben der Registerkarte klicken und Öffnen auswählen, mit dem Sie die Registerkarte im mobilen `...`  `contentUrl` Teams-Client laden.</span><span class="sxs-lookup"><span data-stu-id="de0bb-113">However, they can be loaded on a mobile client by clicking the `...` overflow menu next to the tab and choosing **Open**, which will use your `contentUrl` to load the tab inside the Teams mobile client.</span></span>

## <a name="accessing-personal-tabs"></a><span data-ttu-id="de0bb-114">Zugreifen auf persönliche Registerkarten</span><span class="sxs-lookup"><span data-stu-id="de0bb-114">Accessing personal tabs</span></span>

<span data-ttu-id="de0bb-115">Die folgende Abbildung zeigt, wie Sie auf eine persönliche Registerkarte auf mobilen Geräten zugreifen.</span><span class="sxs-lookup"><span data-stu-id="de0bb-115">The following illustration shows how you access a personal tab on mobile.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-app-drawer.png" alt-text="Abbildung der Mobile -App-Schublade von Teams." border="false":::

## <a name="accessing-channel-tabs"></a><span data-ttu-id="de0bb-117">Zugreifen auf Kanalregisterkarten</span><span class="sxs-lookup"><span data-stu-id="de0bb-117">Accessing channel tabs</span></span>

<span data-ttu-id="de0bb-118">Die folgende Abbildung zeigt, wie Sie auf eine Kanalregisterkarte auf mobilen Geräten zugreifen.</span><span class="sxs-lookup"><span data-stu-id="de0bb-118">The following illustration shows how you access a channel tab on mobile.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab.png" alt-text="Abbildung einer mobilen Registerkarte &quot;Teams&quot;." border="false":::

## <a name="design-considerations"></a><span data-ttu-id="de0bb-120">Überlegungen zum Entwurf</span><span class="sxs-lookup"><span data-stu-id="de0bb-120">Design considerations</span></span>

<span data-ttu-id="de0bb-121">Unsere mobile Plattform ermöglicht Apps eine immersive Erfahrung mit den App-Inhalten, die den ganzen Bildschirm außer der Hauptnavigation von Teams nutzen.</span><span class="sxs-lookup"><span data-stu-id="de0bb-121">Our mobile platform allows apps to be an immersive experience with the app content taking up all of the screen apart from main Teams navigation.</span></span> <span data-ttu-id="de0bb-122">Befolgen Sie diese Richtlinien, um ein immersives Erlebnis zu erstellen, das zu Teams passt.</span><span class="sxs-lookup"><span data-stu-id="de0bb-122">To create an immersive experience that fits with Teams, follow these guidelines.</span></span>

### <a name="responsive-design"></a><span data-ttu-id="de0bb-123">Dynamisches Designs</span><span class="sxs-lookup"><span data-stu-id="de0bb-123">Responsive design</span></span>

<span data-ttu-id="de0bb-124">Da Ihre Registerkarte auf Geräten mit einer vielzahl von Bildschirmgrößen geöffnet werden kann, muss sie [reaktionsfähige Entwurfsprinzipien](https://www.w3schools.com/html/html_responsive.asp) befolgen.</span><span class="sxs-lookup"><span data-stu-id="de0bb-124">Because your tab can be opened on devices with a wide range of screen sizes, it needs to follow [responsive design](https://www.w3schools.com/html/html_responsive.asp) principles.</span></span> <span data-ttu-id="de0bb-125">Alle wichtigen Konstrukte sollten auf mobilen Geräten zugänglich sein, und die Ansichten sollten nicht verzerrt werden.</span><span class="sxs-lookup"><span data-stu-id="de0bb-125">All of the key constructs should be accessible on mobile devices, and the views should not be distorted.</span></span> <span data-ttu-id="de0bb-126">Stellen Sie sicher, dass beim Laden der Registerkarte auf einem mobilen Gerät über die fingerbasierte Navigation problemlos auf alle Schaltflächen und Links zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="de0bb-126">Ensure that when your tab is loaded on a mobile device, all buttons and links are easily accessible using finger-based navigation.</span></span>

### <a name="layouts"></a><span data-ttu-id="de0bb-127">Layouts</span><span class="sxs-lookup"><span data-stu-id="de0bb-127">Layouts</span></span>

<span data-ttu-id="de0bb-128">Die Auswahl des richtigen Layouts für Ihre Registerkarte ist wichtig.</span><span class="sxs-lookup"><span data-stu-id="de0bb-128">Choosing the correct layout for your tab is important.</span></span> <span data-ttu-id="de0bb-129">Sie sollten die Art von Informationen berücksichtigen, die Sie präsentieren, und ein Layout auswählen, das sie zur einfachen Nutzung organisiert.</span><span class="sxs-lookup"><span data-stu-id="de0bb-129">You should consider the kind of information you're presenting, and choose a layout that organizes it for easy consumption.</span></span> <span data-ttu-id="de0bb-130">Einige potenzielle Optionen sind unten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="de0bb-130">Some potential options are outlined below.</span></span>

#### <a name="single-canvas"></a><span data-ttu-id="de0bb-131">Einzelner Canvas</span><span class="sxs-lookup"><span data-stu-id="de0bb-131">Single canvas</span></span>

<span data-ttu-id="de0bb-132">Dies ist ein großer Bereich, in dem die Arbeit erledigt wird.</span><span class="sxs-lookup"><span data-stu-id="de0bb-132">This is one large area where work gets done.</span></span> <span data-ttu-id="de0bb-133">Die Teams Wiki-App folgt diesem Muster.</span><span class="sxs-lookup"><span data-stu-id="de0bb-133">The Teams Wiki app follows this pattern.</span></span> <span data-ttu-id="de0bb-134">Wenn Sie über eine App verfügen, die Inhalte nicht in kleinere Komponenten trennt, ist dies eine gute Passform.</span><span class="sxs-lookup"><span data-stu-id="de0bb-134">If you have an app that doesn’t separate content into smaller components this would be a good fit.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-single-canvas.png" alt-text="Abbildung einer mobilen Registerkarte für einen einzelnen Zeichenbereich von Teams." border="false":::

#### <a name="list"></a><span data-ttu-id="de0bb-136">Liste</span><span class="sxs-lookup"><span data-stu-id="de0bb-136">List</span></span>

<span data-ttu-id="de0bb-137">Listen nen sich gut zum Sortieren und Filtern großer Datenmengen nen und nen, um die wichtigsten Dinge oben zu behalten.</span><span class="sxs-lookup"><span data-stu-id="de0bb-137">Lists are great for sorting and filtering large quantities of data and are great at keeping the most important things at the top.</span></span> <span data-ttu-id="de0bb-138">Es ist hilfreich, sortierbare Spalten zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="de0bb-138">It is helpful to use sortable columns.</span></span> <span data-ttu-id="de0bb-139">Aktionen können zu jedem Listenelement unter dem Auslassungsmenü hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="de0bb-139">Actions can be added to each list item under the ellipsis menu.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-list.png" alt-text="Abbildung einer mobilen Listenregisterkarte von Teams." border="false":::

#### <a name="grid"></a><span data-ttu-id="de0bb-141">Grid</span><span class="sxs-lookup"><span data-stu-id="de0bb-141">Grid</span></span>

<span data-ttu-id="de0bb-142">Raster n nen nützlich sein, um Elemente zu zeigen, die hochgradig visuell sind.</span><span class="sxs-lookup"><span data-stu-id="de0bb-142">Grids are useful for showing elements which are highly visual.</span></span> <span data-ttu-id="de0bb-143">Es hilft, einen Filter oder ein Suchsteuerelement oben zu enthalten.</span><span class="sxs-lookup"><span data-stu-id="de0bb-143">It helps to include a filter or search control at the top.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-grid.png" alt-text="Abbildung einer mobilen Registerkarte von Teams mit einem Rasterlayout." border="false":::

### <a name="tabs-with-bots-on-mobile"></a><span data-ttu-id="de0bb-145">Registerkarten mit Bots auf Mobilgeräten</span><span class="sxs-lookup"><span data-stu-id="de0bb-145">Tabs with bots on mobile</span></span>

<span data-ttu-id="de0bb-146">Das folgende Beispiel ist eine persönliche App mit Registerkarten und einem Bot.</span><span class="sxs-lookup"><span data-stu-id="de0bb-146">The following example is a personal app that has tabs and a bot.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-with-bot.png" alt-text="Abbildung der mobilen Teams-App mit Registerkarten und einem Bot." border="false":::

## <a name="ui-components"></a><span data-ttu-id="de0bb-148">Benutzeroberflächenkomponenten</span><span class="sxs-lookup"><span data-stu-id="de0bb-148">UI components</span></span>

### <a name="color-palettes"></a><span data-ttu-id="de0bb-149">Farbpaletten</span><span class="sxs-lookup"><span data-stu-id="de0bb-149">Color palettes</span></span>

<span data-ttu-id="de0bb-150">Die Verwendung unserer genehmigten neutralen Palette für Hintergründe, Benachrichtigungen, Text und Schaltflächen hilft Ihrer App, sich in Teams wohler zu fühlen.</span><span class="sxs-lookup"><span data-stu-id="de0bb-150">Using our approved neutral palette for backgrounds, notifications, text, and buttons will help your app feel more at home in Teams.</span></span> <span data-ttu-id="de0bb-151">Da Teams mobile zwei Farbthemen (hell und dunkel) hat, sollten Sie sicherstellen, dass Ihre App in beiden Designs großartig aussieht.</span><span class="sxs-lookup"><span data-stu-id="de0bb-151">Since Teams mobile has two colour themes (light and dark), it’s a good idea to make sure your app looks great in both.</span></span>

#### <a name="light-color"></a><span data-ttu-id="de0bb-152">Helle Farbe</span><span class="sxs-lookup"><span data-stu-id="de0bb-152">Light color</span></span>

![Helle Farbpalette](../../assets/images/light-color.png)

#### <a name="dark-color"></a><span data-ttu-id="de0bb-154">Dunkle Farbe</span><span class="sxs-lookup"><span data-stu-id="de0bb-154">Dark color</span></span>

![Dunkle Farbpalette](../../assets/images/dark-color.png)

### <a name="buttons-and-controls"></a><span data-ttu-id="de0bb-156">Schaltflächen und Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="de0bb-156">Buttons and controls</span></span>

<span data-ttu-id="de0bb-157">Die Art und Weise, wie Schaltflächen gestylt werden, hilft zu kommunizieren, welche Art von Aktion sie auslösen.</span><span class="sxs-lookup"><span data-stu-id="de0bb-157">The way buttons are styled helps communicate what kind of action they trigger.</span></span> <span data-ttu-id="de0bb-158">Wir verwalten eine vielzahl von Schaltflächen, die so formatiert sind, dass sie unterschiedliche Betonungsebenen anzeigen.</span><span class="sxs-lookup"><span data-stu-id="de0bb-158">We maintain a wide range of buttons that are formatted to show different levels of emphasis.</span></span> <span data-ttu-id="de0bb-159">Schaltflächen können Text, ein Symbol oder eine Kombination aus Text und einem Symbol enthalten.</span><span class="sxs-lookup"><span data-stu-id="de0bb-159">Buttons can have text, an icon, or a combination of text and an icon.</span></span> <span data-ttu-id="de0bb-160">Um verschiedene Ebenen in einer Hierarchie zu kommunizieren, haben wir primäre und sekundäre Schaltflächen in jeder Kategorie entworfen.</span><span class="sxs-lookup"><span data-stu-id="de0bb-160">To communicate different levels in a hierarchy, we designed primary and secondary buttons within each category.</span></span>

#### <a name="buttons"></a><span data-ttu-id="de0bb-161">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="de0bb-161">Buttons</span></span>

<span data-ttu-id="de0bb-162">Primäre und sekundäre Schaltflächen.</span><span class="sxs-lookup"><span data-stu-id="de0bb-162">Primary and secondary buttons.</span></span>

![Schaltflächenbild](../../assets/images/buttons.png)

#### <a name="selection-controls"></a><span data-ttu-id="de0bb-164">Auswahlsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="de0bb-164">Selection controls</span></span>

<span data-ttu-id="de0bb-165">Optionsfelder, Kontrollkästchen und Umschaltflächen.</span><span class="sxs-lookup"><span data-stu-id="de0bb-165">Radio buttons, checkboxes, and toggles.</span></span>

![Auswahlsteuerelemente](../../assets/images/selection-controls.png)

#### <a name="chiclets-and-pills"></a><span data-ttu-id="de0bb-167">Schickchen und Pillen</span><span class="sxs-lookup"><span data-stu-id="de0bb-167">Chiclets and pills</span></span>

![Zichorlets und Pillen](../../assets/images/chiclets-and-pills.png)

### <a name="typography"></a><span data-ttu-id="de0bb-169">Typografie</span><span class="sxs-lookup"><span data-stu-id="de0bb-169">Typography</span></span>

<span data-ttu-id="de0bb-170">Die Typografie sollte klar und zweckvoll sein.</span><span class="sxs-lookup"><span data-stu-id="de0bb-170">Typography should be clear and purposeful.</span></span> <span data-ttu-id="de0bb-171">Heben Sie wichtige Informationen hervor, und vermeiden Sie die Verwendung mehrerer Schriftarten und Größen, um Verwirrung zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="de0bb-171">Emphasize important information and avoid using multiple fonts and sizes to reduce confusion.</span></span> <span data-ttu-id="de0bb-172">Es wird empfohlen, den Satzfall zu verwenden und die Verwendung aller Obergrenzen für die Lokalisierung und Lesbarkeit zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="de0bb-172">We recommend using sentence case and avoiding the usage of all caps for localization and legibility.</span></span>

![Mobile Typografie](../../assets/images/mobile-typography.png)

### <a name="fields-and-flyouts"></a><span data-ttu-id="de0bb-174">Felder und Flyouts</span><span class="sxs-lookup"><span data-stu-id="de0bb-174">Fields and flyouts</span></span>

<span data-ttu-id="de0bb-175">Felder sind Bereiche, in denen Benutzer Text eingeben können.</span><span class="sxs-lookup"><span data-stu-id="de0bb-175">Fields are areas where users can input text.</span></span> <span data-ttu-id="de0bb-176">Flyouts sind leichter als Dialogfelder und werden im oberen Bereich angezeigt.</span><span class="sxs-lookup"><span data-stu-id="de0bb-176">Flyouts are more lightweight than dialogs and appear from the top pane.</span></span>

#### <a name="list-controls"></a><span data-ttu-id="de0bb-177">Steuerelemente auflisten</span><span class="sxs-lookup"><span data-stu-id="de0bb-177">List controls</span></span>

![Steuerelemente für mobile Listen](../../assets/images/mobile-list-controls.png)

#### <a name="field-controls"></a><span data-ttu-id="de0bb-179">Feldsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="de0bb-179">Field controls</span></span>

![Steuerelemente für mobile Felde](../../assets/images/mobile-field-controls.png)

## <a name="developer-considerations"></a><span data-ttu-id="de0bb-181">Überlegungen zu Entwicklern</span><span class="sxs-lookup"><span data-stu-id="de0bb-181">Developer considerations</span></span>

<span data-ttu-id="de0bb-182">Wenn Sie eine App erstellen, die eine Registerkarte enthält, müssen Sie berücksichtigen (und testen), wie Ihre Registerkarte sowohl auf den Android- als auch auf iOS Microsoft Teams-Clients funktioniert.</span><span class="sxs-lookup"><span data-stu-id="de0bb-182">When you're building an app that includes a tab, you need to consider (and test) how your tab will function on both the Android and iOS Microsoft Teams clients.</span></span> <span data-ttu-id="de0bb-183">In den folgenden Abschnitten werden einige der wichtigsten Szenarien beschrieben, die Sie berücksichtigen müssen.</span><span class="sxs-lookup"><span data-stu-id="de0bb-183">The sections below outline some of the key scenarios you need to consider.</span></span>

### <a name="testing-on-mobile-clients"></a><span data-ttu-id="de0bb-184">Testen auf mobilen Clients</span><span class="sxs-lookup"><span data-stu-id="de0bb-184">Testing on mobile clients</span></span>

<span data-ttu-id="de0bb-185">Sie müssen überprüfen, ob Ihre Registerkarte auf mobilen Geräten unterschiedlicher Größe und Qualität ordnungsgemäß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="de0bb-185">You need to validate that your tab functions properly on mobile devices of various sizes and qualities.</span></span> <span data-ttu-id="de0bb-186">Für Android-Geräte können Sie [devTools](~/tabs/how-to/developer-tools.md) verwenden, um Ihre Registerkarte während der Ausführung zu debuggen.</span><span class="sxs-lookup"><span data-stu-id="de0bb-186">For Android devices, you can use the [DevTools](~/tabs/how-to/developer-tools.md) to debug your tab while it is running.</span></span> <span data-ttu-id="de0bb-187">Es wird empfohlen, sowohl auf Geräten mit hoher und niedriger Leistung als auch auf einem Tablet zu testen.</span><span class="sxs-lookup"><span data-stu-id="de0bb-187">We recommend that you test on both high and low performing devices, as well as on a tablet.</span></span>

### <a name="authentication"></a><span data-ttu-id="de0bb-188">Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="de0bb-188">Authentication</span></span>

<span data-ttu-id="de0bb-189">Damit die Authentifizierung auf mobilen Clients funktioniert, müssen Sie das Teams JavaScript SDK auf mindestens Version 1.4.1 aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="de0bb-189">For authentication to work on mobile clients, you must upgrade you Teams JavaScript SDK to at least version 1.4.1.</span></span>

### <a name="low-bandwidth-and-intermittent-connections"></a><span data-ttu-id="de0bb-190">Niedrige Bandbreite und zeitweilige Verbindungen</span><span class="sxs-lookup"><span data-stu-id="de0bb-190">Low bandwidth and intermittent connections</span></span>

<span data-ttu-id="de0bb-191">Mobile Clients müssen regelmäßig mit geringer Bandbreite und zeitweiligen Verbindungen funktionieren.</span><span class="sxs-lookup"><span data-stu-id="de0bb-191">Mobile clients regularly need to function with low bandwidth and intermittent connections.</span></span> <span data-ttu-id="de0bb-192">Ihre App sollte timeouts entsprechend behandeln, indem sie dem Benutzer eine kontextbezogene Nachricht zur Verfügung stellt.</span><span class="sxs-lookup"><span data-stu-id="de0bb-192">Your app should handle any timeouts appropriately by providing a contextual message to the user.</span></span> <span data-ttu-id="de0bb-193">Sie sollten auch Fortschrittsindikatoren der Benutzer verwenden, um Ihren Benutzern Feedback für alle lang laufenden Prozesse zu geben.</span><span class="sxs-lookup"><span data-stu-id="de0bb-193">You should also user progress indicators to provide feedback to your users for any long-running processes.</span></span>

> [!NOTE]
> <span data-ttu-id="de0bb-194">Registerkarten werden auf mobilen Geräten nur aktiviert, nachdem die Anwendung einer Zulassungsliste hinzugefügt wurde, basierend auf der Eingabe des Genehmigungsteams.</span><span class="sxs-lookup"><span data-stu-id="de0bb-194">Tabs are enabled on mobile only after the application is added to an allow list, based on the input of the approval team.</span></span> <span data-ttu-id="de0bb-195">Um die Reaktionsfähigkeit mobiler Geräte zu überprüfen, erreichen Sie die teamsubm@microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="de0bb-195">To check mobile responsiveness, reach out to teamsubm@microsoft.com.</span></span> 
