---
title: Registerkarten auf mobilen Geräten
description: Beschreibt die Richtlinien für das Entwerfen von Registerkarten, die auf mobilen Geräten funktionieren.
keywords: Teams-Entwurfsrichtlinien – Referenzrahmen-Mobile Registerkarten für persönliche apps
ms.openlocfilehash: a1939465b04a1fe4b803efaf83402852ca536059
ms.sourcegitcommit: b51a4982842948336cfabedb63bdf8f72703585e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2020
ms.locfileid: "48279776"
---
# <a name="tabs-on-mobile"></a><span data-ttu-id="8a9c9-104">Registerkarten auf mobilen Geräten</span><span class="sxs-lookup"><span data-stu-id="8a9c9-104">Tabs on mobile</span></span>

> [!NOTE]
> <span data-ttu-id="8a9c9-105">Wenn die Registerkarte Kanal/Gruppe auf mobilen Teams-Clients angezeigt werden soll, `setSettings()` muss die Konfiguration über einen Wert für die `websiteUrl` Eigenschaft verfügen (siehe unten).</span><span class="sxs-lookup"><span data-stu-id="8a9c9-105">If you choose to have your channel/group tab appear on Teams mobile clients, the `setSettings()` configuration must have a value for the `websiteUrl` property (see below).</span></span>

<span data-ttu-id="8a9c9-106">Benutzerdefinierte Registerkarten können Teil eines Kanals, Gruppenchats oder einer persönlichen APP sein (apps, die statische Registerkarten und/oder einen 1:1-bot enthalten).</span><span class="sxs-lookup"><span data-stu-id="8a9c9-106">Custom tabs can be part of a channel, group chat, or personal app (apps that contain static tabs and/or a one-to-one bot).</span></span>

<span data-ttu-id="8a9c9-107">Persönliche apps sind auf mobilen Clients in der APP-Schublade verfügbar.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-107">Personal apps are available on mobile clients in the app drawer.</span></span> <span data-ttu-id="8a9c9-108">Die APP kann nur von einem Desktop-oder WebClient installiert werden, und es kann bis zu 24 Stunden dauern, bis Sie auf mobilen Clients angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-108">The app can only be installed from a desktop or web client, and can take up to 24 hours to appear on mobile clients.</span></span>

<span data-ttu-id="8a9c9-109">Kanal Registerkarten sind auch auf mobilen Geräten verfügbar.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-109">Channel tabs are also available on mobile.</span></span> <span data-ttu-id="8a9c9-110">Das Standardverhalten besteht derzeit darin, dass Sie Ihre `websiteUrl` Registerkarte in einem Browserfenster starten können.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-110">The default behavior is currently to use your `websiteUrl` to launch your tab in a browser window.</span></span> <span data-ttu-id="8a9c9-111">Sie können jedoch auf einem mobilen Client geladen werden, indem Sie auf das `...` Überlaufmenü neben der Registerkarte und dann auf **Öffnen**klicken, mit dem Sie `contentUrl` die Registerkarte in den mobilen Microsoft Teams-Client laden.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-111">However, they can be loaded on a mobile client by clicking the `...` overflow menu next to the tab and choosing **Open**, which will use your `contentUrl` to load the tab inside the Teams mobile client.</span></span>

## <a name="accessing-personal-tabs"></a><span data-ttu-id="8a9c9-112">Zugreifen auf persönliche Registerkarten</span><span class="sxs-lookup"><span data-stu-id="8a9c9-112">Accessing personal tabs</span></span>

<span data-ttu-id="8a9c9-113">In der folgenden Abbildung wird gezeigt, wie Sie auf eine persönliche Registerkarte in Mobile zugreifen.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-113">The following illustration shows how you access a personal tab on mobile.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-app-drawer.png" alt-text="Abbildung mit den Teams Mobile App Schublade." border="false":::

## <a name="accessing-channel-tabs"></a><span data-ttu-id="8a9c9-115">Zugreifen auf Kanal Registerkarten</span><span class="sxs-lookup"><span data-stu-id="8a9c9-115">Accessing channel tabs</span></span>

<span data-ttu-id="8a9c9-116">In der folgenden Abbildung wird gezeigt, wie Sie auf eine Kanal Registerkarte in Mobile zugreifen.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-116">The following illustration shows how you access a channel tab on mobile.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab.png" alt-text="Abbildung mit einer mobilen Teams-Registerkarte." border="false":::

## <a name="design-considerations"></a><span data-ttu-id="8a9c9-118">Überlegungen zum Entwurf</span><span class="sxs-lookup"><span data-stu-id="8a9c9-118">Design considerations</span></span>

<span data-ttu-id="8a9c9-119">Mit unserer mobilen Plattform können apps eine immersive Erfahrung mit dem App-Inhalt sein, der den gesamten Bildschirm außer der Navigation in den Haupt Teams aufnimmt.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-119">Our mobile platform allows apps to be an immersive experience with the app content taking up all of the screen apart from main Teams navigation.</span></span> <span data-ttu-id="8a9c9-120">Befolgen Sie diese Richtlinien, um eine immersive Umgebung zu erstellen, die in Microsoft Teams passt.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-120">To create an immersive experience that fits with Teams, follow these guidelines.</span></span>

### <a name="responsive-design"></a><span data-ttu-id="8a9c9-121">Dynamisches Designs</span><span class="sxs-lookup"><span data-stu-id="8a9c9-121">Responsive design</span></span>

<span data-ttu-id="8a9c9-122">Da die Registerkarte auf Geräten mit einer großen Bandbreite von Bildschirmgrößen geöffnet werden kann, muss Sie den Grundsätzen für das [reagieren auf Designs](https://www.w3schools.com/html/html_responsive.asp) entsprechen.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-122">Because your tab can be opened on devices with a wide range of screen sizes, it needs to follow [responsive design](https://www.w3schools.com/html/html_responsive.asp) principles.</span></span> <span data-ttu-id="8a9c9-123">Auf alle Schlüssel Konstrukte sollte auf mobilen Geräten zugegriffen werden können, und die Ansichten sollten nicht verzerrt werden.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-123">All of the key constructs should be accessible on mobile devices, and the views should not be distorted.</span></span> <span data-ttu-id="8a9c9-124">Stellen Sie sicher, dass beim Laden der Registerkarte auf einem mobilen Gerät alle Schaltflächen und Links leicht über die Finger basierte Navigation zugänglich sind.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-124">Ensure that when your tab is loaded on a mobile device, all buttons and links are easily accessible using finger-based navigation.</span></span>

### <a name="layouts"></a><span data-ttu-id="8a9c9-125">Layouts</span><span class="sxs-lookup"><span data-stu-id="8a9c9-125">Layouts</span></span>

<span data-ttu-id="8a9c9-126">Die Auswahl des richtigen Layouts für Ihre Registerkarte ist wichtig.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-126">Choosing the correct layout for your tab is important.</span></span> <span data-ttu-id="8a9c9-127">Sie sollten die Art von Informationen berücksichtigen, die Sie präsentieren, und ein Layout auswählen, das es für einen einfachen Verbrauch organisiert.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-127">You should consider the kind of information you're presenting, and choose a layout that organizes it for easy consumption.</span></span> <span data-ttu-id="8a9c9-128">Einige potenzielle Optionen werden unten erläutert.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-128">Some potential options are outlined below.</span></span>

#### <a name="single-canvas"></a><span data-ttu-id="8a9c9-129">Einzelne Leinwand</span><span class="sxs-lookup"><span data-stu-id="8a9c9-129">Single canvas</span></span>

<span data-ttu-id="8a9c9-130">Dies ist ein großer Bereich, in dem Arbeit erledigt wird.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-130">This is one large area where work gets done.</span></span> <span data-ttu-id="8a9c9-131">Die wiki-app "Teams" folgt diesem Muster.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-131">The Teams Wiki app follows this pattern.</span></span> <span data-ttu-id="8a9c9-132">Wenn Sie über eine APP verfügen, die Inhalte nicht in kleinere Komponenten unterteilt, wäre dies gut geeignet.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-132">If you have an app that doesn’t separate content into smaller components this would be a good fit.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-single-canvas.png" alt-text="Abbildung mit einer mobilen Teams-Registerkarte mit einer einzelnen Leinwand." border="false":::

#### <a name="list"></a><span data-ttu-id="8a9c9-134">Liste</span><span class="sxs-lookup"><span data-stu-id="8a9c9-134">List</span></span>

<span data-ttu-id="8a9c9-135">Listen eignen sich hervorragend zum Sortieren und Filtern großer Datenmengen und bieten eine große Rolle, um die wichtigsten Dinge am besten zu halten.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-135">Lists are great for sorting and filtering large quantities of data and are great at keeping the most important things at the top.</span></span> <span data-ttu-id="8a9c9-136">Es ist hilfreich, sortierbare Spalten zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-136">It is helpful to use sortable columns.</span></span> <span data-ttu-id="8a9c9-137">Im Menü mit den Auslassungspunkten können jedem Listenelementaktionen hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-137">Actions can be added to each list item under the ellipsis menu.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-list.png" alt-text="Abbildung mit einer mobilen Teams-Listen Registerkarte." border="false":::

#### <a name="grid"></a><span data-ttu-id="8a9c9-139">Raster</span><span class="sxs-lookup"><span data-stu-id="8a9c9-139">Grid</span></span>

<span data-ttu-id="8a9c9-140">Raster sind nützlich, um Elemente anzuzeigen, die sehr visuell sind.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-140">Grids are useful for showing elements which are highly visual.</span></span> <span data-ttu-id="8a9c9-141">Es hilft, ein Filter-oder Suchsteuerelement am oberen Rand einzuschließen.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-141">It helps to include a filter or search control at the top.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-grid.png" alt-text="Abbildung zeigt eine Mobile Teams-Registerkarte mit einem Rasterlayout." border="false":::

### <a name="tabs-with-bots-on-mobile"></a><span data-ttu-id="8a9c9-143">Tabs mit Bots auf mobilen Geräten</span><span class="sxs-lookup"><span data-stu-id="8a9c9-143">Tabs with bots on mobile</span></span>

<span data-ttu-id="8a9c9-144">Das folgende Beispiel ist eine persönliche APP, die über Registerkarten und einen bot verfügt.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-144">The following example is a personal app that has tabs and a bot.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-with-bot.png" alt-text="Abbildung, die zeigt, wie Mobile Teams-App mit Registerkarten und bot." border="false":::

## <a name="ui-components"></a><span data-ttu-id="8a9c9-146">Benutzeroberflächenkomponenten</span><span class="sxs-lookup"><span data-stu-id="8a9c9-146">UI components</span></span>

### <a name="color-palettes"></a><span data-ttu-id="8a9c9-147">Farbpaletten</span><span class="sxs-lookup"><span data-stu-id="8a9c9-147">Color palettes</span></span>

<span data-ttu-id="8a9c9-148">Die Verwendung unserer genehmigten neutralen Palette für Hintergründe, Benachrichtigungen, Text und Schaltflächen hilft Ihrer APP, sich in Microsoft Teams zu Hause zu fühlen.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-148">Using our approved neutral palette for backgrounds, notifications, text, and buttons will help your app feel more at home in Teams.</span></span> <span data-ttu-id="8a9c9-149">Da Teams Mobile zwei Farbdesigns (hell und dunkel) aufweist, sollten Sie sicherstellen, dass Ihre APP in beiden Farben gut aussieht.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-149">Since Teams mobile has two colour themes (light and dark), it’s a good idea to make sure your app looks great in both.</span></span>

#### <a name="light-color"></a><span data-ttu-id="8a9c9-150">Helle Farbe</span><span class="sxs-lookup"><span data-stu-id="8a9c9-150">Light color</span></span>

![helle Farbpalette](../../assets/images/light-color.png)

#### <a name="dark-color"></a><span data-ttu-id="8a9c9-152">Dunkle Farbe</span><span class="sxs-lookup"><span data-stu-id="8a9c9-152">Dark color</span></span>

![dunkle Farbpalette](../../assets/images/dark-color.png)

### <a name="buttons-and-controls"></a><span data-ttu-id="8a9c9-154">Schaltflächen und Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="8a9c9-154">Buttons and controls</span></span>

<span data-ttu-id="8a9c9-155">Die Art und Weise, wie Schaltflächen formatiert werden, hilft bei der Kommunikation, welche Art von Aktion ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-155">The way buttons are styled helps communicate what kind of action they trigger.</span></span> <span data-ttu-id="8a9c9-156">Wir halten eine Vielzahl von Schaltflächen, die formatiert sind, um unterschiedliche Schwerpunkte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-156">We maintain a wide range of buttons that are formatted to show different levels of emphasis.</span></span> <span data-ttu-id="8a9c9-157">Schaltflächen können Text, ein Symbol oder eine Kombination aus Text und Symbol aufweisen.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-157">Buttons can have text, an icon, or a combination of text and an icon.</span></span> <span data-ttu-id="8a9c9-158">Um verschiedene Ebenen in einer Hierarchie zu kommunizieren, haben wir die primären und sekundären Schaltflächen innerhalb der einzelnen Kategorien entworfen.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-158">To communicate different levels in a hierarchy, we designed primary and secondary buttons within each category.</span></span>

#### <a name="buttons"></a><span data-ttu-id="8a9c9-159">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="8a9c9-159">Buttons</span></span>

<span data-ttu-id="8a9c9-160">Primäre und sekundäre Schaltflächen.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-160">Primary and secondary buttons.</span></span>

![Schaltflächenbild](../../assets/images/buttons.png)

#### <a name="selection-controls"></a><span data-ttu-id="8a9c9-162">Auswahlsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="8a9c9-162">Selection controls</span></span>

<span data-ttu-id="8a9c9-163">Optionsfelder, Kontrollkästchen und Umschaltflächen.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-163">Radio buttons, checkboxes, and toggles.</span></span>

![Auswahlsteuerelemente](../../assets/images/selection-controls.png)

#### <a name="chiclets-and-pills"></a><span data-ttu-id="8a9c9-165">Chiclets und Pillen</span><span class="sxs-lookup"><span data-stu-id="8a9c9-165">Chiclets and pills</span></span>

![Chiclets und Pillen](../../assets/images/chiclets-and-pills.png)

### <a name="typography"></a><span data-ttu-id="8a9c9-167">Typografie</span><span class="sxs-lookup"><span data-stu-id="8a9c9-167">Typography</span></span>

<span data-ttu-id="8a9c9-168">Typografie sollte eindeutig und zielgerichtet sein.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-168">Typography should be clear and purposeful.</span></span> <span data-ttu-id="8a9c9-169">Betonen Sie wichtige Informationen, und vermeiden Sie die Verwendung mehrerer Schriftarten und Größen zur Verringerung von Verwirrung.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-169">Emphasize important information and avoid using multiple fonts and sizes to reduce confusion.</span></span> <span data-ttu-id="8a9c9-170">Wir empfehlen die Verwendung von satzfall und vermeiden die Verwendung aller Caps für Lokalisierung und Lesbarkeit.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-170">We recommend using sentence case and avoiding the usage of all caps for localization and legibility.</span></span>

![Mobile Typograph](../../assets/images/mobile-typography.png)

### <a name="fields-and-flyouts"></a><span data-ttu-id="8a9c9-172">Felder und Flyouts</span><span class="sxs-lookup"><span data-stu-id="8a9c9-172">Fields and flyouts</span></span>

<span data-ttu-id="8a9c9-173">Felder sind Bereiche, in denen Benutzer Text eingeben können.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-173">Fields are areas where users can input text.</span></span> <span data-ttu-id="8a9c9-174">Flyouts sind leichter als Dialogfelder und werden aus dem oberen Bereich angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-174">Flyouts are more lightweight than dialogs and appear from the top pane.</span></span>

#### <a name="list-controls"></a><span data-ttu-id="8a9c9-175">Steuerelemente auflisten</span><span class="sxs-lookup"><span data-stu-id="8a9c9-175">List controls</span></span>

![Mobile Listensteuerelemente](../../assets/images/mobile-list-controls.png)

#### <a name="field-controls"></a><span data-ttu-id="8a9c9-177">Feldsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="8a9c9-177">Field controls</span></span>

![Mobile Feldsteuerelemente](../../assets/images/mobile-field-controls.png)

## <a name="developer-considerations"></a><span data-ttu-id="8a9c9-179">Entwickler Überlegungen</span><span class="sxs-lookup"><span data-stu-id="8a9c9-179">Developer considerations</span></span>

<span data-ttu-id="8a9c9-180">Wenn Sie eine APP erstellen, die eine Registerkarte enthält, müssen Sie prüfen (und testen), wie Ihre Registerkarte sowohl auf den Android-als auch IOS-Microsoft Teams-Clients funktioniert.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-180">When you're building an app that includes a tab, you need to consider (and test) how your tab will function on both the Android and iOS Microsoft Teams clients.</span></span> <span data-ttu-id="8a9c9-181">In den folgenden Abschnitten werden einige der wichtigsten Szenarien beschrieben, die Sie in diesem Punkt behandeln müssen.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-181">The sections below outline some of the key scenarios you need to consider.</span></span>

### <a name="testing-on-mobile-clients"></a><span data-ttu-id="8a9c9-182">Testen auf mobilen Clients</span><span class="sxs-lookup"><span data-stu-id="8a9c9-182">Testing on mobile clients</span></span>

<span data-ttu-id="8a9c9-183">Sie müssen überprüfen, ob Ihre Registerkarte auf mobilen Geräten in verschiedenen Größen und Qualitäten ordnungsgemäß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-183">You need to validate that your tab functions properly on mobile devices of various sizes and qualities.</span></span> <span data-ttu-id="8a9c9-184">Für Android-Geräte können Sie die [devtools](~/tabs/how-to/developer-tools.md) verwenden, um Ihre Registerkarte während der Ausführung zu debuggen.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-184">For Android devices, you can use the [DevTools](~/tabs/how-to/developer-tools.md) to debug your tab while it is running.</span></span> <span data-ttu-id="8a9c9-185">Es wird empfohlen, sowohl auf High-als auch auf niedrig leistungsfähigen Geräten sowie auf einem Tablet zu testen.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-185">We recommend that you test on both high and low performing devices, as well as on a tablet.</span></span>

### <a name="authentication"></a><span data-ttu-id="8a9c9-186">Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="8a9c9-186">Authentication</span></span>

<span data-ttu-id="8a9c9-187">Damit die Authentifizierung auf mobilen Clients funktioniert, müssen Sie Microsoft Teams JavaScript SDK auf mindestens Version 1.4.1 aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-187">For authentication to work on mobile clients, you must upgrade you Teams JavaScript SDK to at least version 1.4.1.</span></span>

### <a name="low-bandwidth-and-intermittent-connections"></a><span data-ttu-id="8a9c9-188">Niedrige Bandbreite und zeitweilige Verbindungen</span><span class="sxs-lookup"><span data-stu-id="8a9c9-188">Low bandwidth and intermittent connections</span></span>

<span data-ttu-id="8a9c9-189">Mobile Clients müssen regelmäßig mit niedriger Bandbreite und zeitweiligen Verbindungen arbeiten.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-189">Mobile clients regularly need to function with low bandwidth and intermittent connections.</span></span> <span data-ttu-id="8a9c9-190">Ihre APP sollte alle Timeouts entsprechend behandeln, indem Sie dem Benutzer eine Kontext Meldung bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-190">Your app should handle any timeouts appropriately by providing a contextual message to the user.</span></span> <span data-ttu-id="8a9c9-191">Sie sollten auch Benutzer Fortschrittsindikatoren angeben, um Ihren Benutzern Feedback für alle langwierigen Prozesse zur Verfügung zu stellen.</span><span class="sxs-lookup"><span data-stu-id="8a9c9-191">You should also user progress indicators to provide feedback to your users for any long-running processes.</span></span>
