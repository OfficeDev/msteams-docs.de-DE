---
title: Registerkarten auf mobilen Geräten
description: Beschreibt die Richtlinien für das Entwerfen von Registerkarten, die auf mobilen Geräten funktionieren.
ms.topic: conceptual
keywords: Teams Design Guidelines reference framework personal apps mobile tabs
ms.openlocfilehash: 70ff46e446b146b134f34830e8867133cbeeca14
ms.sourcegitcommit: f74b74d5bed1df193e59f46121ada443fb57277b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2021
ms.locfileid: "50093288"
---
# <a name="tabs-on-mobile"></a><span data-ttu-id="da850-104">Registerkarten auf mobilen Geräten</span><span class="sxs-lookup"><span data-stu-id="da850-104">Tabs on mobile</span></span>

> [!NOTE]
> <span data-ttu-id="da850-105">Wenn Sie ihre Kanal-/Gruppenregisterkarte auf mobilen Teams-Clients anzeigen möchten, muss die Konfiguration einen Wert für die Eigenschaft haben `setSettings()` `websiteUrl` (siehe unten).</span><span class="sxs-lookup"><span data-stu-id="da850-105">If you choose to have your channel/group tab appear on Teams mobile clients, the `setSettings()` configuration must have a value for the `websiteUrl` property (see below).</span></span>

<span data-ttu-id="da850-106">Benutzerdefinierte Registerkarten können Teil eines Kanals, Eines Gruppenchats oder einer persönlichen App sein (Apps, die statische Registerkarten und/oder einen 1:1-Bot enthalten).</span><span class="sxs-lookup"><span data-stu-id="da850-106">Custom tabs can be part of a channel, group chat, or personal app (apps that contain static tabs and/or a one-to-one bot).</span></span>

<span data-ttu-id="da850-107">Persönliche Apps sind auf mobilen Clients in der App-Drawer verfügbar.</span><span class="sxs-lookup"><span data-stu-id="da850-107">Personal apps are available on mobile clients in the app drawer.</span></span> <span data-ttu-id="da850-108">Die App kann nur von einem Desktop- oder Webclient installiert werden und kann bis zu 24 Stunden dauern, bis sie auf mobilen Clients angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="da850-108">The app can only be installed from a desktop or web client, and can take up to 24 hours to appear on mobile clients.</span></span>

<span data-ttu-id="da850-109">Kanalregisterkarten sind auch für Mobilgeräte verfügbar.</span><span class="sxs-lookup"><span data-stu-id="da850-109">Channel tabs are also available on mobile.</span></span> <span data-ttu-id="da850-110">Das Standardverhalten besteht derzeit in der Verwendung ihrer Registerkarte, um die `websiteUrl` Registerkarte in einem Browserfenster zu starten.</span><span class="sxs-lookup"><span data-stu-id="da850-110">The default behavior is currently to use your `websiteUrl` to launch your tab in a browser window.</span></span> <span data-ttu-id="da850-111">Sie können jedoch auf einem mobilen Client geladen werden, indem Sie auf das Überlaufmenü neben der Registerkarte klicken und "Öffnen" auswählen, wodurch Sie die Registerkarte im mobilen Client von `...` Teams  `contentUrl` laden.</span><span class="sxs-lookup"><span data-stu-id="da850-111">However, they can be loaded on a mobile client by clicking the `...` overflow menu next to the tab and choosing **Open**, which will use your `contentUrl` to load the tab inside the Teams mobile client.</span></span>

## <a name="accessing-personal-tabs"></a><span data-ttu-id="da850-112">Zugreifen auf persönliche Registerkarten</span><span class="sxs-lookup"><span data-stu-id="da850-112">Accessing personal tabs</span></span>

<span data-ttu-id="da850-113">Die folgende Abbildung zeigt, wie Sie auf eine persönliche Registerkarte auf mobilen Geräten zugreifen.</span><span class="sxs-lookup"><span data-stu-id="da850-113">The following illustration shows how you access a personal tab on mobile.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-app-drawer.png" alt-text="Illustration showing the Teams mobile app drawer." border="false":::

## <a name="accessing-channel-tabs"></a><span data-ttu-id="da850-115">Zugreifen auf Kanalregisterkarten</span><span class="sxs-lookup"><span data-stu-id="da850-115">Accessing channel tabs</span></span>

<span data-ttu-id="da850-116">Die folgende Abbildung zeigt, wie Sie auf eine Kanalregisterkarte auf mobilen Geräten zugreifen.</span><span class="sxs-lookup"><span data-stu-id="da850-116">The following illustration shows how you access a channel tab on mobile.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab.png" alt-text="Abbildung einer mobilen Registerkarte &quot;Teams&quot;." border="false":::

## <a name="design-considerations"></a><span data-ttu-id="da850-118">Überlegungen zum Entwurf</span><span class="sxs-lookup"><span data-stu-id="da850-118">Design considerations</span></span>

<span data-ttu-id="da850-119">Unsere mobile Plattform ermöglicht Apps eine immersive Erfahrung mit den App-Inhalten, die den ganzen Bildschirm neben der Hauptnavigation von Teams nutzen.</span><span class="sxs-lookup"><span data-stu-id="da850-119">Our mobile platform allows apps to be an immersive experience with the app content taking up all of the screen apart from main Teams navigation.</span></span> <span data-ttu-id="da850-120">Befolgen Sie diese Richtlinien, um ein immersives Erlebnis zu erstellen, das zu Teams passt.</span><span class="sxs-lookup"><span data-stu-id="da850-120">To create an immersive experience that fits with Teams, follow these guidelines.</span></span>

### <a name="responsive-design"></a><span data-ttu-id="da850-121">Dynamisches Designs</span><span class="sxs-lookup"><span data-stu-id="da850-121">Responsive design</span></span>

<span data-ttu-id="da850-122">Da Ihre Registerkarte auf Geräten mit einer vielzahl von Bildschirmgrößen geöffnet werden kann, muss sie den Prinzipien des [reaktionsschnellen Designs](https://www.w3schools.com/html/html_responsive.asp) entsprechen.</span><span class="sxs-lookup"><span data-stu-id="da850-122">Because your tab can be opened on devices with a wide range of screen sizes, it needs to follow [responsive design](https://www.w3schools.com/html/html_responsive.asp) principles.</span></span> <span data-ttu-id="da850-123">Alle wichtigen Konstrukte sollten auf mobilen Geräten zugänglich sein, und die Ansichten sollten nicht verzerrt sein.</span><span class="sxs-lookup"><span data-stu-id="da850-123">All of the key constructs should be accessible on mobile devices, and the views should not be distorted.</span></span> <span data-ttu-id="da850-124">Stellen Sie sicher, dass beim Laden der Registerkarte auf einem mobilen Gerät alle Schaltflächen und Links über die fingerbasierte Navigation leicht zugänglich sind.</span><span class="sxs-lookup"><span data-stu-id="da850-124">Ensure that when your tab is loaded on a mobile device, all buttons and links are easily accessible using finger-based navigation.</span></span>

### <a name="layouts"></a><span data-ttu-id="da850-125">Layouts</span><span class="sxs-lookup"><span data-stu-id="da850-125">Layouts</span></span>

<span data-ttu-id="da850-126">Die Auswahl des richtigen Layouts für Ihre Registerkarte ist wichtig.</span><span class="sxs-lookup"><span data-stu-id="da850-126">Choosing the correct layout for your tab is important.</span></span> <span data-ttu-id="da850-127">Sie sollten die Art von Informationen berücksichtigen, die Sie präsentieren, und ein Layout auswählen, das sie für einen einfachen Verbrauch organisiert.</span><span class="sxs-lookup"><span data-stu-id="da850-127">You should consider the kind of information you're presenting, and choose a layout that organizes it for easy consumption.</span></span> <span data-ttu-id="da850-128">Im Folgenden werden einige mögliche Optionen beschrieben.</span><span class="sxs-lookup"><span data-stu-id="da850-128">Some potential options are outlined below.</span></span>

#### <a name="single-canvas"></a><span data-ttu-id="da850-129">Einzelner Zeichenbereich</span><span class="sxs-lookup"><span data-stu-id="da850-129">Single canvas</span></span>

<span data-ttu-id="da850-130">Dies ist ein großer Bereich, in dem Arbeit erledigt wird.</span><span class="sxs-lookup"><span data-stu-id="da850-130">This is one large area where work gets done.</span></span> <span data-ttu-id="da850-131">Die Teams-Wiki-App folgt diesem Muster.</span><span class="sxs-lookup"><span data-stu-id="da850-131">The Teams Wiki app follows this pattern.</span></span> <span data-ttu-id="da850-132">Wenn Sie über eine App verfügen, die Inhalte nicht in kleinere Komponenten aufteilen, ist dies gut geeignet.</span><span class="sxs-lookup"><span data-stu-id="da850-132">If you have an app that doesn’t separate content into smaller components this would be a good fit.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-single-canvas.png" alt-text="Abbildung einer mobilen Registerkarte mit einem einzelnen Zeichenbereich in Teams." border="false":::

#### <a name="list"></a><span data-ttu-id="da850-134">List</span><span class="sxs-lookup"><span data-stu-id="da850-134">List</span></span>

<span data-ttu-id="da850-135">Listen n nen sich gut zum Sortieren und Filtern großer Datenmengen nnen und sind gut dafür, die wichtigsten Dinge ganz oben zu behalten.</span><span class="sxs-lookup"><span data-stu-id="da850-135">Lists are great for sorting and filtering large quantities of data and are great at keeping the most important things at the top.</span></span> <span data-ttu-id="da850-136">Es ist hilfreich, sortierbare Spalten zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="da850-136">It is helpful to use sortable columns.</span></span> <span data-ttu-id="da850-137">Aktionen können jedem Listenelement unter dem Auslassungspunktmenü hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="da850-137">Actions can be added to each list item under the ellipsis menu.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-list.png" alt-text="Abbildung einer Registerkarte für mobile Teams-Listen." border="false":::

#### <a name="grid"></a><span data-ttu-id="da850-139">Raster</span><span class="sxs-lookup"><span data-stu-id="da850-139">Grid</span></span>

<span data-ttu-id="da850-140">Raster sind nützlich, um Elemente zu zeigen, die hochgradig visuell sind.</span><span class="sxs-lookup"><span data-stu-id="da850-140">Grids are useful for showing elements which are highly visual.</span></span> <span data-ttu-id="da850-141">Es hilft, oben einen Filter oder ein Suchsteuerelement zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="da850-141">It helps to include a filter or search control at the top.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-grid.png" alt-text="Abbildung einer mobilen Registerkarte von Teams mit einem Rasterlayout." border="false":::

### <a name="tabs-with-bots-on-mobile"></a><span data-ttu-id="da850-143">Registerkarten mit Bots auf Mobilgeräten</span><span class="sxs-lookup"><span data-stu-id="da850-143">Tabs with bots on mobile</span></span>

<span data-ttu-id="da850-144">Das folgende Beispiel ist eine persönliche App mit Registerkarten und einem Bot.</span><span class="sxs-lookup"><span data-stu-id="da850-144">The following example is a personal app that has tabs and a bot.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-with-bot.png" alt-text="Illustration showing how mobile Teams app that has tabs and a bot." border="false":::

## <a name="ui-components"></a><span data-ttu-id="da850-146">Benutzeroberflächenkomponenten</span><span class="sxs-lookup"><span data-stu-id="da850-146">UI components</span></span>

### <a name="color-palettes"></a><span data-ttu-id="da850-147">Farbpaletten</span><span class="sxs-lookup"><span data-stu-id="da850-147">Color palettes</span></span>

<span data-ttu-id="da850-148">Die Verwendung unserer genehmigten neutralen Palette für Hintergründe, Benachrichtigungen, Text und Schaltflächen hilft Ihrer App, sich in Teams besser zu hause zu fühlen.</span><span class="sxs-lookup"><span data-stu-id="da850-148">Using our approved neutral palette for backgrounds, notifications, text, and buttons will help your app feel more at home in Teams.</span></span> <span data-ttu-id="da850-149">Da Teams Mobile zwei helle Designs (hell und dunkel) hat, sollten Sie sicherstellen, dass Ihre App in beiden Designs gut aussieht.</span><span class="sxs-lookup"><span data-stu-id="da850-149">Since Teams mobile has two colour themes (light and dark), it’s a good idea to make sure your app looks great in both.</span></span>

#### <a name="light-color"></a><span data-ttu-id="da850-150">Helle Farbe</span><span class="sxs-lookup"><span data-stu-id="da850-150">Light color</span></span>

![Helle Farbpalette](../../assets/images/light-color.png)

#### <a name="dark-color"></a><span data-ttu-id="da850-152">Dunkle Farbe</span><span class="sxs-lookup"><span data-stu-id="da850-152">Dark color</span></span>

![Dunkle Farbpalette](../../assets/images/dark-color.png)

### <a name="buttons-and-controls"></a><span data-ttu-id="da850-154">Schaltflächen und Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="da850-154">Buttons and controls</span></span>

<span data-ttu-id="da850-155">Die Art und Weise, wie Schaltflächen formatiert werden, hilft zu kommunizieren, welche Art von Aktion sie auslösen.</span><span class="sxs-lookup"><span data-stu-id="da850-155">The way buttons are styled helps communicate what kind of action they trigger.</span></span> <span data-ttu-id="da850-156">Wir verwalten eine Vielzahl von Schaltflächen, die so formatiert sind, dass sie unterschiedliche Akzentstufen anzeigen.</span><span class="sxs-lookup"><span data-stu-id="da850-156">We maintain a wide range of buttons that are formatted to show different levels of emphasis.</span></span> <span data-ttu-id="da850-157">Schaltflächen können Text, ein Symbol oder eine Kombination aus Text und einem Symbol enthalten.</span><span class="sxs-lookup"><span data-stu-id="da850-157">Buttons can have text, an icon, or a combination of text and an icon.</span></span> <span data-ttu-id="da850-158">Um verschiedene Ebenen in einer Hierarchie zu kommunizieren, haben wir primäre und sekundäre Schaltflächen innerhalb jeder Kategorie entworfen.</span><span class="sxs-lookup"><span data-stu-id="da850-158">To communicate different levels in a hierarchy, we designed primary and secondary buttons within each category.</span></span>

#### <a name="buttons"></a><span data-ttu-id="da850-159">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="da850-159">Buttons</span></span>

<span data-ttu-id="da850-160">Primäre und sekundäre Schaltflächen.</span><span class="sxs-lookup"><span data-stu-id="da850-160">Primary and secondary buttons.</span></span>

![Schaltflächenbild](../../assets/images/buttons.png)

#### <a name="selection-controls"></a><span data-ttu-id="da850-162">Auswahlsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="da850-162">Selection controls</span></span>

<span data-ttu-id="da850-163">Optionsfelder, Kontrollkästchen und Umschaltflächen.</span><span class="sxs-lookup"><span data-stu-id="da850-163">Radio buttons, checkboxes, and toggles.</span></span>

![Auswahlsteuerelemente](../../assets/images/selection-controls.png)

#### <a name="chiclets-and-pills"></a><span data-ttu-id="da850-165">Kapseln und Kapseln</span><span class="sxs-lookup"><span data-stu-id="da850-165">Chiclets and pills</span></span>

![- und -kapseln](../../assets/images/chiclets-and-pills.png)

### <a name="typography"></a><span data-ttu-id="da850-167">Typografie</span><span class="sxs-lookup"><span data-stu-id="da850-167">Typography</span></span>

<span data-ttu-id="da850-168">Typografie sollte klar und zielvoll sein.</span><span class="sxs-lookup"><span data-stu-id="da850-168">Typography should be clear and purposeful.</span></span> <span data-ttu-id="da850-169">Heben Sie wichtige Informationen hervor, und vermeiden Sie die Verwendung mehrerer Schriftarten und Größen, um Verwirrung zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="da850-169">Emphasize important information and avoid using multiple fonts and sizes to reduce confusion.</span></span> <span data-ttu-id="da850-170">Wir empfehlen die Verwendung von Groß-/B0 und die Verwendung von Großbuchstaben für die Lokalisierung und Lesbarkeit.</span><span class="sxs-lookup"><span data-stu-id="da850-170">We recommend using sentence case and avoiding the usage of all caps for localization and legibility.</span></span>

![Mobile Typografie](../../assets/images/mobile-typography.png)

### <a name="fields-and-flyouts"></a><span data-ttu-id="da850-172">Felder und Flyouts</span><span class="sxs-lookup"><span data-stu-id="da850-172">Fields and flyouts</span></span>

<span data-ttu-id="da850-173">Felder sind Bereiche, in denen Benutzer Text eingeben können.</span><span class="sxs-lookup"><span data-stu-id="da850-173">Fields are areas where users can input text.</span></span> <span data-ttu-id="da850-174">Flyouts sind einfacher als Dialogfelder und werden im oberen Bereich angezeigt.</span><span class="sxs-lookup"><span data-stu-id="da850-174">Flyouts are more lightweight than dialogs and appear from the top pane.</span></span>

#### <a name="list-controls"></a><span data-ttu-id="da850-175">Steuerelemente auflisten</span><span class="sxs-lookup"><span data-stu-id="da850-175">List controls</span></span>

![Mobile Listensteuerelemente](../../assets/images/mobile-list-controls.png)

#### <a name="field-controls"></a><span data-ttu-id="da850-177">Feldsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="da850-177">Field controls</span></span>

![Mobile Feldsteuerelemente](../../assets/images/mobile-field-controls.png)

## <a name="developer-considerations"></a><span data-ttu-id="da850-179">Überlegungen für Entwickler</span><span class="sxs-lookup"><span data-stu-id="da850-179">Developer considerations</span></span>

<span data-ttu-id="da850-180">Wenn Sie eine App erstellen, die eine Registerkarte enthält, müssen Sie berücksichtigen (und testen), wie Ihre Registerkarte auf den Android- und iOS Microsoft Teams-Clients funktioniert.</span><span class="sxs-lookup"><span data-stu-id="da850-180">When you're building an app that includes a tab, you need to consider (and test) how your tab will function on both the Android and iOS Microsoft Teams clients.</span></span> <span data-ttu-id="da850-181">In den folgenden Abschnitten werden einige der wichtigsten Szenarien beschrieben, die Sie berücksichtigen müssen.</span><span class="sxs-lookup"><span data-stu-id="da850-181">The sections below outline some of the key scenarios you need to consider.</span></span>

### <a name="testing-on-mobile-clients"></a><span data-ttu-id="da850-182">Testen auf mobilen Clients</span><span class="sxs-lookup"><span data-stu-id="da850-182">Testing on mobile clients</span></span>

<span data-ttu-id="da850-183">Sie müssen überprüfen, ob Ihre Registerkarte auf mobilen Geräten verschiedener Größen und Qualitäten ordnungsgemäß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="da850-183">You need to validate that your tab functions properly on mobile devices of various sizes and qualities.</span></span> <span data-ttu-id="da850-184">Für Android-Geräte können Sie [die DevTools](~/tabs/how-to/developer-tools.md) verwenden, um Ihre Registerkarte während der Ausführung zu debuggen.</span><span class="sxs-lookup"><span data-stu-id="da850-184">For Android devices, you can use the [DevTools](~/tabs/how-to/developer-tools.md) to debug your tab while it is running.</span></span> <span data-ttu-id="da850-185">Es wird empfohlen, sowohl auf Geräten mit hoher und niedriger Leistung als auch auf einem Tablet zu testen.</span><span class="sxs-lookup"><span data-stu-id="da850-185">We recommend that you test on both high and low performing devices, as well as on a tablet.</span></span>

### <a name="authentication"></a><span data-ttu-id="da850-186">Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="da850-186">Authentication</span></span>

<span data-ttu-id="da850-187">Damit die Authentifizierung auf mobilen Clients funktioniert, müssen Sie Das JavaScript SDK für Teams auf mindestens Version 1.4.1 aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="da850-187">For authentication to work on mobile clients, you must upgrade you Teams JavaScript SDK to at least version 1.4.1.</span></span>

### <a name="low-bandwidth-and-intermittent-connections"></a><span data-ttu-id="da850-188">Geringe Bandbreite und zeitweilige Verbindungen</span><span class="sxs-lookup"><span data-stu-id="da850-188">Low bandwidth and intermittent connections</span></span>

<span data-ttu-id="da850-189">Mobile Clients müssen regelmäßig mit geringer Bandbreite und zeitweilig unterbrochenen Verbindungen funktionieren.</span><span class="sxs-lookup"><span data-stu-id="da850-189">Mobile clients regularly need to function with low bandwidth and intermittent connections.</span></span> <span data-ttu-id="da850-190">Ihre App sollte alle Timeouts entsprechend behandeln, indem sie dem Benutzer eine Kontextnachricht zur Verfügung stellt.</span><span class="sxs-lookup"><span data-stu-id="da850-190">Your app should handle any timeouts appropriately by providing a contextual message to the user.</span></span> <span data-ttu-id="da850-191">Sie sollten auch Statusindikatoren für Benutzer verwenden, um Ihren Benutzern Feedback für lang dauernde Prozesse zu geben.</span><span class="sxs-lookup"><span data-stu-id="da850-191">You should also user progress indicators to provide feedback to your users for any long-running processes.</span></span>

> [!NOTE]
> <span data-ttu-id="da850-192">Registerkarten werden auf mobilen Geräten nur aktiviert, nachdem die Anwendung basierend auf der Eingabe des Genehmigungsteams einer Zulassungsliste hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="da850-192">Tabs are enabled on mobile only after the application is added to an allow list, based on the input of the approval team.</span></span> <span data-ttu-id="da850-193">Um die Reaktionsfähigkeit mobiler Geräte zu überprüfen, greifen Sie auf teamsubm@microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="da850-193">To check mobile responsiveness, reach out to teamsubm@microsoft.com.</span></span> 