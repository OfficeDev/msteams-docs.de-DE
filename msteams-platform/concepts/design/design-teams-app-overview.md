---
title: Entwerfen Ihrer benutzerdefinierten App
author: heath-hamilton
description: Hier erfahren Sie, wie Sie Microsoft Teams-apps entwerfen. Ressourcen umfassen das Microsoft Teams UI Kit, bewährte Methoden, Beispiele und vieles mehr.
ms.author: lajanuar
ms.topic: overview
ms.openlocfilehash: 0160a59ed4ebc51e900acbb5d74735ccae0b6083
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "49606014"
---
# <a name="designing-your-microsoft-teams-app"></a><span data-ttu-id="e8328-104">Entwerfen Ihrer Microsoft Teams-App</span><span class="sxs-lookup"><span data-stu-id="e8328-104">Designing your Microsoft Teams app</span></span>

:::image type="content" source="../../assets/images/design-guidelines-overview.png" alt-text="Konzept Bild Einführung in die Microsoft Teams-Entwurfsrichtlinien.":::

<span data-ttu-id="e8328-106">Unabhängig davon, ob Sie ein Designer, Produktmanager, Entwickler oder Hersteller mit Tools mit niedrigem Code sind, können diese Richtlinien Ihnen helfen, schnell die richtigen Entwurfsentscheidungen für Ihre Microsoft Teams-APP zu treffen.</span><span class="sxs-lookup"><span data-stu-id="e8328-106">Whether you're a designer, product manager, developer, or maker using low-code tools, these guidelines can help you quickly make the right design decisions for your Microsoft Teams app.</span></span>

## <a name="teams-app-design-principles"></a><span data-ttu-id="e8328-107">Teams-App-Entwurfsprinzipien</span><span class="sxs-lookup"><span data-stu-id="e8328-107">Teams app design principles</span></span>

<span data-ttu-id="e8328-108">Teams-Apps helfen Benutzern, mehr gemeinsam zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="e8328-108">Teams apps help people achieve more together.</span></span> <span data-ttu-id="e8328-109">Verwenden Sie diese Prinzipien, um Ihren Entwurf zu leiten.</span><span class="sxs-lookup"><span data-stu-id="e8328-109">Use these principles to guide your design.</span></span>

:::row:::
   :::column span="":::

### <a name="collaborative"></a><span data-ttu-id="e8328-110">Collaborative</span><span class="sxs-lookup"><span data-stu-id="e8328-110">Collaborative</span></span>

<span data-ttu-id="e8328-111">Teams-Apps helfen Benutzern, mehr gemeinsam zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="e8328-111">Teams apps help people achieve more together.</span></span> <span data-ttu-id="e8328-112">Verwenden Sie diese Prinzipien, um Ihren Entwurf zu leiten.</span><span class="sxs-lookup"><span data-stu-id="e8328-112">Use these principles to guide your design.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="trustworthy"></a><span data-ttu-id="e8328-113">Trustworthy</span><span class="sxs-lookup"><span data-stu-id="e8328-113">Trustworthy</span></span>

<span data-ttu-id="e8328-114">Die APP ist sicher und kompatibel.</span><span class="sxs-lookup"><span data-stu-id="e8328-114">The app is secure and compliant.</span></span> <span data-ttu-id="e8328-115">Benutzer können ganz einfach Informationen zum Datenschutz finden.</span><span class="sxs-lookup"><span data-stu-id="e8328-115">Users can easily find information about privacy.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="globally-inclusive"></a><span data-ttu-id="e8328-116">Global inklusive</span><span class="sxs-lookup"><span data-stu-id="e8328-116">Globally inclusive</span></span>

<span data-ttu-id="e8328-117">Personen aller Hintergründe, Skillsets und Disziplinen können die APP verwenden.</span><span class="sxs-lookup"><span data-stu-id="e8328-117">People of all backgrounds, skillsets, and disciplines can use the app.</span></span> <span data-ttu-id="e8328-118">Es ist kulturell, rassisch und sozial bewusst.</span><span class="sxs-lookup"><span data-stu-id="e8328-118">It’s culturally, racially, and socially aware.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="light"></a><span data-ttu-id="e8328-119">Niedrig</span><span class="sxs-lookup"><span data-stu-id="e8328-119">Light</span></span>

<span data-ttu-id="e8328-120">Die APP konzentriert sich auf Kern Szenarien, die sich mit Microsoft Teams-Workflows verschmelzen.</span><span class="sxs-lookup"><span data-stu-id="e8328-120">The app focuses on core scenarios that blend with Teams workflows.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="native-or-distinct"></a><span data-ttu-id="e8328-121">Systemeigen oder unterschiedlich</span><span class="sxs-lookup"><span data-stu-id="e8328-121">Native or distinct</span></span>

<span data-ttu-id="e8328-122">Die APP verwendet Native Teams-Designkomponenten oder Ihre eigenen.</span><span class="sxs-lookup"><span data-stu-id="e8328-122">The app uses native Teams design components or your own.</span></span> <span data-ttu-id="e8328-123">Es gibt keine Mischung aus Farbschemas, Steuerelementen usw.</span><span class="sxs-lookup"><span data-stu-id="e8328-123">There’s no blend of color schemes, controls, etc.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="useful"></a><span data-ttu-id="e8328-124">Nützlich</span><span class="sxs-lookup"><span data-stu-id="e8328-124">Useful</span></span>

<span data-ttu-id="e8328-125">Die APP basiert auf einem Szenario, das die Benutzer in Microsoft Teams ausführen müssen.</span><span class="sxs-lookup"><span data-stu-id="e8328-125">The app is based on a scenario people need to do in Teams.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="easy-to-use"></a><span data-ttu-id="e8328-126">Einfache Verwendung</span><span class="sxs-lookup"><span data-stu-id="e8328-126">Easy to use</span></span>

<span data-ttu-id="e8328-127">Die Benutzeroberfläche ist einfach zu verstehen, angenehm im Aussehen und Ton und macht die Mitarbeiter produktiver.</span><span class="sxs-lookup"><span data-stu-id="e8328-127">The UI is easy to understand, pleasant in look and tone, and makes people more productive.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="responsive"></a><span data-ttu-id="e8328-128">Reaktionsfähig</span><span class="sxs-lookup"><span data-stu-id="e8328-128">Responsive</span></span>

<span data-ttu-id="e8328-129">Die APP ist Geräte-und Bildschirm unabhängig.</span><span class="sxs-lookup"><span data-stu-id="e8328-129">The app is device and screen agnostic.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="accessible"></a><span data-ttu-id="e8328-130">Barrierefrei</span><span class="sxs-lookup"><span data-stu-id="e8328-130">Accessible</span></span>

<span data-ttu-id="e8328-131">Die APP erfüllt die Zugänglichkeitsanforderungen für Teams in Bezug auf Farbkontrast, Navigations Alternativen und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="e8328-131">The app meets Teams accessibility requirements in terms of color contrast, navigation alternatives, and more.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="well-described"></a><span data-ttu-id="e8328-132">Gut beschrieben</span><span class="sxs-lookup"><span data-stu-id="e8328-132">Well described</span></span>

<span data-ttu-id="e8328-133">Text, Symbole und Bilder machen deutlich, wofür die APP dient und wie Sie verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="e8328-133">Text, icons, and images make it clear what the app is for and how to use it.</span></span>

   :::column-end:::
:::row-end:::

## <a name="creating-a-cohesive-experience"></a><span data-ttu-id="e8328-134">Erstellen einer zusammengeschlossenen Umgebung</span><span class="sxs-lookup"><span data-stu-id="e8328-134">Creating a cohesive experience</span></span>

<span data-ttu-id="e8328-135">Das Entwerfen einer Teams-App ähnelt dem Entwerfen einer herkömmlichen Webanwendung – aber auch etwas anders.</span><span class="sxs-lookup"><span data-stu-id="e8328-135">Designing a Teams app is like designing a conventional web app—but also a little different.</span></span> <span data-ttu-id="e8328-136">Ein effektives Design hebt die eindeutigen Attribute Ihrer APP hervor, und passt natürlich zu den Microsoft Teams-Features und-Kontexten.</span><span class="sxs-lookup"><span data-stu-id="e8328-136">An effective design highlights your app's unique attributes while fitting naturally with Teams features and contexts.</span></span>

<span data-ttu-id="e8328-137">Diese Richtlinien und Ressourcen können Ihnen dabei helfen, diesen Ausgleich zu finden.</span><span class="sxs-lookup"><span data-stu-id="e8328-137">These guidelines and resources can help you strike that balance.</span></span> <span data-ttu-id="e8328-138">Sie wissen, was zu tun ist und was Sie vermeiden sollten, wenn Sie Ihre Teams-App entwerfen (beispielsweise mehrstufige Navigation auf einer Registerkarte).</span><span class="sxs-lookup"><span data-stu-id="e8328-138">You'll know what to do and what to avoid when designing your Teams app (such as multi-level navigation in a tab).</span></span>

## <a name="planning-your-app"></a><span data-ttu-id="e8328-139">Planen Ihrer APP</span><span class="sxs-lookup"><span data-stu-id="e8328-139">Planning your app</span></span>

<span data-ttu-id="e8328-140">Um eine qualitativ hochwertige Teams-APP zu entwerfen, müssen Sie zunächst verstehen, was Ihre APP tun soll und wie Sie denken, dass Sie von den Benutzern verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="e8328-140">To design a high-quality Teams app, you must first understand what you want your app to do and how you think people will use it.</span></span> <span data-ttu-id="e8328-141">Wenn Sie dies noch nicht getan haben, nehmen Sie sich etwas Zeit, um [Ihre APP](../../concepts/extensibility-points.md)richtig zu planen.</span><span class="sxs-lookup"><span data-stu-id="e8328-141">If you haven't already, take some time to properly [plan your app](../../concepts/extensibility-points.md).</span></span>

## <a name="design-fundamentals"></a><span data-ttu-id="e8328-142">Entwurfsgrundlagen</span><span class="sxs-lookup"><span data-stu-id="e8328-142">Design fundamentals</span></span>

<span data-ttu-id="e8328-143">Erfahren Sie mehr [über die Grundlagen des App-Designs von Teams](design-teams-app-fundamentals.md), einschließlich Layout, Farbschemas und vielem mehr.</span><span class="sxs-lookup"><span data-stu-id="e8328-143">Learn the [fundamentals of Teams app design](design-teams-app-fundamentals.md), including layout, color schemes, and more.</span></span>

## <a name="basic-fluent-ui-components-for-teams"></a><span data-ttu-id="e8328-144">Grundlegende Fluent-UI-Komponenten für Teams</span><span class="sxs-lookup"><span data-stu-id="e8328-144">Basic Fluent UI components for Teams</span></span>

<span data-ttu-id="e8328-145">Basierend auf der Fluent-Benutzeroberfläche sind dies die [Kernelemente für die Erstellung vertrauter Teams-Schnittstellen](design-teams-app-basic-ui-components.md).</span><span class="sxs-lookup"><span data-stu-id="e8328-145">Based on Fluent UI, these are the [core elements for creating familiar Teams interfaces](design-teams-app-basic-ui-components.md).</span></span>

## <a name="app-capabilities"></a><span data-ttu-id="e8328-146">App-Funktionen</span><span class="sxs-lookup"><span data-stu-id="e8328-146">App capabilities</span></span>

<span data-ttu-id="e8328-147">Erfahren Sie, wie Benutzer Teams-apps hinzufügen, verwenden und verwalten, um jede Funktion in Ihrem Design optimal nutzen zu können.</span><span class="sxs-lookup"><span data-stu-id="e8328-147">Understand how people add, use, and manage Teams apps to make the most of each capability in your design.</span></span>

* [<span data-ttu-id="e8328-148">Persönliche Apps</span><span class="sxs-lookup"><span data-stu-id="e8328-148">Personal apps</span></span>](../../concepts/design/personal-apps.md)
* [<span data-ttu-id="e8328-149">Registerkarten</span><span class="sxs-lookup"><span data-stu-id="e8328-149">Tabs</span></span>](../../tabs/design/tabs.md)
* [<span data-ttu-id="e8328-150">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="e8328-150">Messaging extensions</span></span>](../../messaging-extensions/design/messaging-extension-design.md)
* [<span data-ttu-id="e8328-151">Bots</span><span class="sxs-lookup"><span data-stu-id="e8328-151">Bots</span></span>](../../bots/design/bots.md)
* [<span data-ttu-id="e8328-152">Besprechungs Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="e8328-152">Meeting extensions</span></span>](../../apps-in-teams-meetings/design/designing-apps-in-meetings.md)
* [<span data-ttu-id="e8328-153">Aufgabenmodule</span><span class="sxs-lookup"><span data-stu-id="e8328-153">Task modules</span></span>](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)
* [<span data-ttu-id="e8328-154">Adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="e8328-154">Adaptive Cards</span></span>](../../task-modules-and-cards/cards/design-effective-cards.md)

## <a name="ui-templates"></a><span data-ttu-id="e8328-155">Benutzeroberflächenvorlagen</span><span class="sxs-lookup"><span data-stu-id="e8328-155">UI templates</span></span>

<span data-ttu-id="e8328-156">Erstellen Sie schnell komplexe, hochwertige Designs mit [Vorlagen für gängige Teams-Anwendungsfälle und Workflows](design-teams-app-ui-templates.md).</span><span class="sxs-lookup"><span data-stu-id="e8328-156">Quickly create complex, high-fidelity designs with [templates for common Teams use cases and workflows](design-teams-app-ui-templates.md).</span></span>

## <a name="get-started-with-the-microsoft-teams-ui-kit"></a><span data-ttu-id="e8328-157">Erste Schritte mit dem Microsoft Teams UI Kit</span><span class="sxs-lookup"><span data-stu-id="e8328-157">Get started with the Microsoft Teams UI Kit</span></span>

<span data-ttu-id="e8328-158">Das Microsoft Teams UI Kit verfügt über Benutzeroberflächenkomponenten, Vorlagen und Beispiele, die Sie nach Bedarf ziehen, ablegen und ändern können.</span><span class="sxs-lookup"><span data-stu-id="e8328-158">The Microsoft Teams UI Kit has UI components, templates, and examples that you can drag, drop, and modify as needed.</span></span> <span data-ttu-id="e8328-159">Das UI-Kit enthält auch umfassende Informationen darüber, wie apps in verschiedenen Teams-Szenarien aussehen und sich Verhalten sollten.</span><span class="sxs-lookup"><span data-stu-id="e8328-159">The UI kit also includes comprehensive information about how apps should look and behave in different Teams scenarios.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e8328-160">Abrufen des Microsoft Teams UI Kit (Figma)</span><span class="sxs-lookup"><span data-stu-id="e8328-160">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="other-resources"></a><span data-ttu-id="e8328-161">Sonstige Ressourcen</span><span class="sxs-lookup"><span data-stu-id="e8328-161">Other resources</span></span>

<span data-ttu-id="e8328-162">Um weitere Informationen zu erhalten, probieren Sie eine der folgenden Ressourcen aus.</span><span class="sxs-lookup"><span data-stu-id="e8328-162">To learn more, try one of the following resources.</span></span>

### <a name="fluent-ui"></a><span data-ttu-id="e8328-163">Fluent-Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="e8328-163">Fluent UI</span></span>

<span data-ttu-id="e8328-164">Dient zum Abrufen von Codebeispielen und Implementierungsdetails für die Fluent-UI-basierten Komponenten, die zum Erstellen von Teams-Erfahrungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e8328-164">Get code samples and implementation details for the Fluent UI-based components used to build Teams experiences.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e8328-165">Testen von Microsoft Teams-Benutzeroberflächenkomponenten (Fluent-Benutzeroberfläche)</span><span class="sxs-lookup"><span data-stu-id="e8328-165">Try out Teams UI components (Fluent UI)</span></span>](https://fluentsite.z22.web.core.windows.net/)

### <a name="adaptive-cards-designer"></a><span data-ttu-id="e8328-166">Adaptive Cards-Designer</span><span class="sxs-lookup"><span data-stu-id="e8328-166">Adaptive Cards designer</span></span>

<span data-ttu-id="e8328-167">Entwerfen Sie Adaptive Karten in einem webbasierten Tool.</span><span class="sxs-lookup"><span data-stu-id="e8328-167">Design Adaptive Cards in a web-based tool.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e8328-168">Testen des Adaptive Cards-Designers</span><span class="sxs-lookup"><span data-stu-id="e8328-168">Try the Adaptive Cards designer</span></span>](https://adaptivecards.io/designer/)
