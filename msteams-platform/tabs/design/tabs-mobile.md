---
title: Registerkarten auf mobilen Geräten
description: Beschreibt die Richtlinien für das Entwerfen von Registerkarten, die auf mobilen Geräten funktionieren.
keywords: Teams-Entwurfsrichtlinien – Referenzrahmen-Mobile Registerkarten für persönliche apps
ms.openlocfilehash: 6fe40b9cc5b6e898d0f0bce14b3dfedfd2c14032
ms.sourcegitcommit: 61c93b22490526b1de87c0b14a3c7eb6e046caf6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2020
ms.locfileid: "44455520"
---
# <a name="tabs-on-mobile"></a><span data-ttu-id="0414c-104">Registerkarten auf mobilen Geräten</span><span class="sxs-lookup"><span data-stu-id="0414c-104">Tabs on mobile</span></span>

<span data-ttu-id="0414c-105">Benutzerdefinierte Registerkarten können Teil eines Kanals, Gruppenchats oder einer persönlichen APP sein (apps, die statische Registerkarten und/oder einen 1:1-bot enthalten).</span><span class="sxs-lookup"><span data-stu-id="0414c-105">Custom tabs can be part of a channel, group chat, or personal app (apps that contain static tabs and/or a one-to-one bot).</span></span>

<span data-ttu-id="0414c-106">Persönliche apps sind auf mobilen Clients in der APP-Schublade verfügbar.</span><span class="sxs-lookup"><span data-stu-id="0414c-106">Personal apps are available on mobile clients in the App Drawer.</span></span> <span data-ttu-id="0414c-107">Die APP kann nur von einem Desktop-oder WebClient installiert werden, und es kann bis zu 24 Stunden dauern, bis Sie auf mobilen Clients angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="0414c-107">The app can only be installed from a desktop or web client, and can take up to 24 hours to appear on mobile clients.</span></span>

<span data-ttu-id="0414c-108">Gruppen-und Kanal Registerkarten sind auch auf mobilen Clients verfügbar.</span><span class="sxs-lookup"><span data-stu-id="0414c-108">Group and channel tabs are available on mobile clients as well.</span></span> <span data-ttu-id="0414c-109">Das Standardverhalten besteht derzeit darin, dass Sie Ihre `websiteUrl` Registerkarte in einem Browserfenster starten können.</span><span class="sxs-lookup"><span data-stu-id="0414c-109">The default behavior is currently to use your `websiteUrl` to launch your tab in a browser window.</span></span> <span data-ttu-id="0414c-110">Sie können jedoch auf einem mobilen Client geladen werden, indem Sie auf das `...` Überlaufmenü neben der Registerkarte und dann auf **Öffnen**klicken, mit dem Sie `contentUrl` die Registerkarte in den mobilen Microsoft Teams-Client laden.</span><span class="sxs-lookup"><span data-stu-id="0414c-110">However, they can be loaded on a mobile client by clicking the `...` overflow menu next to the tab and choosing **Open**, which will use your `contentUrl` to load the tab inside the Teams mobile client.</span></span>

![Mobile App Schublade](../../assets/images/personal-app-mobile.png)

## <a name="developer-considerations-for-mobile-support"></a><span data-ttu-id="0414c-112">Entwickler Überlegungen für die Mobile Unterstützung</span><span class="sxs-lookup"><span data-stu-id="0414c-112">Developer considerations for mobile support</span></span>

<span data-ttu-id="0414c-113">Wenn Sie eine APP erstellen, die eine Registerkarte enthält, müssen Sie prüfen (und testen), wie Ihre Registerkarte sowohl auf den Android-als auch IOS-Microsoft Teams-Clients funktioniert.</span><span class="sxs-lookup"><span data-stu-id="0414c-113">When you're building an app that includes a tab, you need to consider (and test) how your tab will function on both the Android and iOS Microsoft Teams clients.</span></span> <span data-ttu-id="0414c-114">In den folgenden Abschnitten werden einige der wichtigsten Szenarien beschrieben, die Sie in diesem Punkt behandeln müssen.</span><span class="sxs-lookup"><span data-stu-id="0414c-114">The sections below outline some of the key scenarios you need to consider.</span></span>

### <a name="testing-on-mobile-clients"></a><span data-ttu-id="0414c-115">Testen auf mobilen Clients</span><span class="sxs-lookup"><span data-stu-id="0414c-115">Testing on mobile clients</span></span>

<span data-ttu-id="0414c-116">Sie müssen überprüfen, ob Ihre Registerkarte auf mobilen Geräten in verschiedenen Größen und Qualitäten ordnungsgemäß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="0414c-116">You need to validate that your tab functions properly on mobile devices of various sizes and qualities.</span></span> <span data-ttu-id="0414c-117">Für Android-Geräte können Sie die [devtools](~/tabs/how-to/developer-tools.md) verwenden, um Ihre Registerkarte während der Ausführung zu debuggen.</span><span class="sxs-lookup"><span data-stu-id="0414c-117">For Android devices you can use the [DevTools](~/tabs/how-to/developer-tools.md) to debug your tab while it is running.</span></span> <span data-ttu-id="0414c-118">Es wird empfohlen, sowohl auf High-als auch auf niedrig leistungsfähigen Geräten sowie auf einem Tablet zu testen.</span><span class="sxs-lookup"><span data-stu-id="0414c-118">We recommend that you test on both high and low performing devices, as well as on a tablet.</span></span>

### <a name="responsive-design"></a><span data-ttu-id="0414c-119">Dynamisches Designs</span><span class="sxs-lookup"><span data-stu-id="0414c-119">Responsive design</span></span>

<span data-ttu-id="0414c-120">Da die Registerkarte auf Geräten mit einer großen Bandbreite von Bildschirmgrößen geöffnet werden kann, muss Sie den Grundsätzen für das [reagieren auf Designs](https://www.w3schools.com/html/html_responsive.asp) entsprechen.</span><span class="sxs-lookup"><span data-stu-id="0414c-120">Because your tab can be opened on devices with a wide range of screen sizes, it needs to follow [responsive design](https://www.w3schools.com/html/html_responsive.asp) principles.</span></span> <span data-ttu-id="0414c-121">Auf alle Schlüssel Konstrukte sollte auf mobilen Geräten zugegriffen werden können, und die Ansichten sollten nicht verzerrt werden.</span><span class="sxs-lookup"><span data-stu-id="0414c-121">All of the key constructs should be accessible on mobile devices, and the views should not be distorted.</span></span> <span data-ttu-id="0414c-122">Stellen Sie sicher, dass beim Laden der Registerkarte auf einem mobilen Gerät alle Schaltflächen und Links leicht über die Finger basierte Navigation zugänglich sind.</span><span class="sxs-lookup"><span data-stu-id="0414c-122">Ensure that when your tab is loaded on a mobile device, all buttons and links are easily accessible using finger-based navigation.</span></span>

### <a name="authentication"></a><span data-ttu-id="0414c-123">Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="0414c-123">Authentication</span></span>

<span data-ttu-id="0414c-124">Damit die Authentifizierung auf mobilen Clients funktioniert, müssen Sie Microsoft Teams js SDK auf mindestens Version 1.4.1 aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="0414c-124">For authentication to work on mobile clients, you must upgrade you Teams JS SDK to at least version 1.4.1.</span></span>

### <a name="low-bandwidth--intermittent-connections"></a><span data-ttu-id="0414c-125">Geringe Bandbreiten & intermittierende Verbindungen</span><span class="sxs-lookup"><span data-stu-id="0414c-125">Low bandwidth & intermittent connections</span></span>

<span data-ttu-id="0414c-126">Mobile Clients müssen regelmäßig mit niedriger Bandbreite und zeitweiligen Verbindungen arbeiten.</span><span class="sxs-lookup"><span data-stu-id="0414c-126">Mobile clients regularly need to function with low bandwidth and intermittent connections.</span></span> <span data-ttu-id="0414c-127">Ihre APP sollte alle Timeouts entsprechend behandeln, indem Sie dem Benutzer eine Kontext Meldung bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="0414c-127">Your app should handle any timeouts appropriately by providing a contextual message to the user.</span></span> <span data-ttu-id="0414c-128">Sie sollten auch Benutzer Fortschrittsindikatoren angeben, um Ihren Benutzern Feedback für alle langwierigen Prozesse zur Verfügung zu stellen.</span><span class="sxs-lookup"><span data-stu-id="0414c-128">You should also user progress indicators to provide feedback to your users for any long-running processes.</span></span>

## <a name="design-considerations-for-mobile"></a><span data-ttu-id="0414c-129">Entwurfsüberlegungen für mobile Geräte</span><span class="sxs-lookup"><span data-stu-id="0414c-129">Design considerations for mobile</span></span>

<span data-ttu-id="0414c-130">Mit unserer mobilen Plattform können apps eine immersive Erfahrung mit dem App-Inhalt sein, der den gesamten Bildschirm außer der Navigation in den Haupt Teams aufnimmt.</span><span class="sxs-lookup"><span data-stu-id="0414c-130">Our mobile platform allows apps to be an immersive experience with the app content taking up all of the screen apart from main Teams navigation.</span></span> <span data-ttu-id="0414c-131">Befolgen Sie die nachstehenden Richtlinien, um eine immersive Umgebung zu erstellen, die nahtlos in den Microsoft Teams-Client passt.</span><span class="sxs-lookup"><span data-stu-id="0414c-131">To create an immersive experience that fits seamlessly within the Microsoft Teams client, follow the guidelines below.</span></span>

### <a name="layouts"></a><span data-ttu-id="0414c-132">Layouts</span><span class="sxs-lookup"><span data-stu-id="0414c-132">Layouts</span></span>

<span data-ttu-id="0414c-133">Die Auswahl des richtigen Layouts für Ihre Registerkarte ist wichtig.</span><span class="sxs-lookup"><span data-stu-id="0414c-133">Choosing the correct layout for your tab is important.</span></span> <span data-ttu-id="0414c-134">Sie sollten die Art von Informationen berücksichtigen, die Sie präsentieren, und ein Layout auswählen, das es für einen einfachen Verbrauch organisiert.</span><span class="sxs-lookup"><span data-stu-id="0414c-134">You should consider the kind of information you're presenting, and choose a layout that organizes it for easy consumption.</span></span> <span data-ttu-id="0414c-135">Einige potenzielle Optionen werden unten erläutert.</span><span class="sxs-lookup"><span data-stu-id="0414c-135">Some potential options are outlined below.</span></span>

#### <a name="single-canvas"></a><span data-ttu-id="0414c-136">Einzelne Leinwand</span><span class="sxs-lookup"><span data-stu-id="0414c-136">Single canvas</span></span>

<span data-ttu-id="0414c-137">Dies ist ein großer Bereich, in dem Arbeit erledigt wird.</span><span class="sxs-lookup"><span data-stu-id="0414c-137">This is one large area where work gets done.</span></span> <span data-ttu-id="0414c-138">Die wiki-app folgt diesem Muster.</span><span class="sxs-lookup"><span data-stu-id="0414c-138">The Wiki app follows this pattern.</span></span> <span data-ttu-id="0414c-139">Wenn Sie über eine APP verfügen, die Inhalte nicht in kleinere Komponenten unterteilt, wäre dies gut geeignet.</span><span class="sxs-lookup"><span data-stu-id="0414c-139">If you have an app that doesn’t separate content into smaller components this would be a good fit.</span></span>

![einzelnes Canvas-Layout](~/assets/images/mobile-single-canvas.png)

#### <a name="list"></a><span data-ttu-id="0414c-141">Auflisten</span><span class="sxs-lookup"><span data-stu-id="0414c-141">List</span></span>

<span data-ttu-id="0414c-142">Listen eignen sich hervorragend zum Sortieren und Filtern großer Datenmengen und bieten eine große Rolle, um die wichtigsten Dinge am besten zu halten.</span><span class="sxs-lookup"><span data-stu-id="0414c-142">Lists are great for sorting and filtering large quantities of data and are great at keeping the most important things at the top.</span></span> <span data-ttu-id="0414c-143">Es ist hilfreich, sortierbare Spalten zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="0414c-143">It is helpful to use sortable columns.</span></span> <span data-ttu-id="0414c-144">Im Menü mit den Auslassungspunkten können jedem Listenelementaktionen hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="0414c-144">Actions can be added to each list item under the ellipsis menu.</span></span>

![Listenlayout](~/assets/images/mobile-list.png)

#### <a name="grid"></a><span data-ttu-id="0414c-146">Raster</span><span class="sxs-lookup"><span data-stu-id="0414c-146">Grid</span></span>

<span data-ttu-id="0414c-147">Raster sind nützlich, um Elemente anzuzeigen, die sehr visuell sind.</span><span class="sxs-lookup"><span data-stu-id="0414c-147">Grids are useful for showing elements which are highly visual.</span></span> <span data-ttu-id="0414c-148">Es hilft, ein Filter-oder Suchsteuerelement am oberen Rand einzuschließen.</span><span class="sxs-lookup"><span data-stu-id="0414c-148">It helps to include a filter or search control at the top.</span></span>

![Rasterlayout](~/assets/images/mobile-grid.png)

### <a name="tabs-with-bots-on-mobile"></a><span data-ttu-id="0414c-150">Tabs mit Bots auf mobilen Geräten</span><span class="sxs-lookup"><span data-stu-id="0414c-150">Tabs with bots on mobile</span></span>

<span data-ttu-id="0414c-151">Im folgenden finden Sie ein Beispiel für eine persönliche APP, die zwei statische Registerkarten und einen bot enthält.</span><span class="sxs-lookup"><span data-stu-id="0414c-151">The below is an example personal app that contains two static tabs and a bot.</span></span>

![Tabs und Bots auf mobilen Geräten](~/assets/images/mobile-tab-with-bot.png)

### <a name="ui-components"></a><span data-ttu-id="0414c-153">Komponenten der Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="0414c-153">UI Components</span></span>

#### <a name="color-palettes"></a><span data-ttu-id="0414c-154">Farbpaletten</span><span class="sxs-lookup"><span data-stu-id="0414c-154">Color palettes</span></span>

<span data-ttu-id="0414c-155">Die Verwendung unserer genehmigten neutralen Palette für Hintergründe, Benachrichtigungen, Text und Schaltflächen hilft Ihrer APP, sich in Microsoft Teams zu Hause zu fühlen.</span><span class="sxs-lookup"><span data-stu-id="0414c-155">Using our approved neutral palette for backgrounds, notifications, text, and buttons will help your app feel more at home in Teams.</span></span> <span data-ttu-id="0414c-156">Da Teams Mobile zwei Farbdesigns (hell und dunkel) aufweist, sollten Sie sicherstellen, dass Ihre APP in beiden Farben gut aussieht.</span><span class="sxs-lookup"><span data-stu-id="0414c-156">Since Teams mobile has two colour themes (light and dark), it’s a good idea to make sure your app looks great in both.</span></span>

##### <a name="light-color"></a><span data-ttu-id="0414c-157">Helle Farbe</span><span class="sxs-lookup"><span data-stu-id="0414c-157">Light color</span></span>

![helle Farbpalette](~/assets/images/light-color.png)

##### <a name="dark-color"></a><span data-ttu-id="0414c-159">Dunkle Farbe</span><span class="sxs-lookup"><span data-stu-id="0414c-159">Dark color</span></span>

![dunkle Farbpalette](~/assets/images/dark-color.png)

#### <a name="buttons-and-controls"></a><span data-ttu-id="0414c-161">Schaltflächen und Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="0414c-161">Buttons and controls</span></span>

<span data-ttu-id="0414c-162">Die Art und Weise, wie Schaltflächen formatiert werden, hilft bei der Kommunikation, welche Art von Aktion ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="0414c-162">The way buttons are styled helps communicate what kind of action they trigger.</span></span> <span data-ttu-id="0414c-163">Wir halten eine Vielzahl von Schaltflächen, die formatiert sind, um unterschiedliche Schwerpunkte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="0414c-163">We maintain a wide range of buttons that are formatted to show different levels of emphasis.</span></span> <span data-ttu-id="0414c-164">Schaltflächen können Text, ein Symbol oder eine Kombination aus Text und Symbol aufweisen.</span><span class="sxs-lookup"><span data-stu-id="0414c-164">Buttons can have text, an icon, or a combination of text and an icon.</span></span> <span data-ttu-id="0414c-165">Um verschiedene Ebenen in einer Hierarchie zu kommunizieren, haben wir die primären und sekundären Schaltflächen innerhalb der einzelnen Kategorien entworfen.</span><span class="sxs-lookup"><span data-stu-id="0414c-165">To communicate different levels in a hierarchy, we designed primary and secondary buttons within each category.</span></span>

![Schaltflächen](~/assets/images/buttons.png)

![Auswahlsteuerelemente](~/assets/images/selection-controls.png)

![Chiclets und Pillen](~/assets/images/chiclets-and-pills.png)

#### <a name="typography"></a><span data-ttu-id="0414c-169">Typografie</span><span class="sxs-lookup"><span data-stu-id="0414c-169">Typography</span></span>

<span data-ttu-id="0414c-170">Typografie sollte eindeutig und zielgerichtet sein.</span><span class="sxs-lookup"><span data-stu-id="0414c-170">Typography should be clear and purposeful.</span></span> <span data-ttu-id="0414c-171">Betonen Sie wichtige Informationen, und vermeiden Sie die Verwendung mehrerer Schriftarten und Größen zur Verringerung von Verwirrung.</span><span class="sxs-lookup"><span data-stu-id="0414c-171">Emphasize important information and avoid using multiple fonts and sizes to reduce confusion.</span></span> <span data-ttu-id="0414c-172">Wir empfehlen die Verwendung von satzfall und vermeiden die Verwendung aller Caps für Lokalisierung und Lesbarkeit.</span><span class="sxs-lookup"><span data-stu-id="0414c-172">We recommend using sentence case and avoiding the usage of all caps for localization and legibility.</span></span>

![Mobile Typograph](~/assets/images/mobile-typography.png)

#### <a name="fields-and-flyouts"></a><span data-ttu-id="0414c-174">Felder und Flyouts</span><span class="sxs-lookup"><span data-stu-id="0414c-174">Fields and Flyouts</span></span>

<span data-ttu-id="0414c-175">Felder sind Bereiche, in denen Benutzer Text eingeben können.</span><span class="sxs-lookup"><span data-stu-id="0414c-175">Fields are areas where users can input text.</span></span> <span data-ttu-id="0414c-176">Flyouts sind leichter als Dialogfelder und werden aus dem oberen Bereich angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0414c-176">Flyouts are more lightweight than dialogs, and appear from the top pane.</span></span>

##### <a name="list-controls"></a><span data-ttu-id="0414c-177">Steuerelemente auflisten</span><span class="sxs-lookup"><span data-stu-id="0414c-177">List controls</span></span>

![Mobile Listensteuerelemente](~/assets/images/mobile-list-controls.png)

##### <a name="field-controls"></a><span data-ttu-id="0414c-179">Feldsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="0414c-179">Field controls</span></span>

![Mobile Feldsteuerelemente](~/assets/images/mobile-field-controls.png)
