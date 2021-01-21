---
title: Entwerfen Ihrer benutzerdefinierten App
author: heath-hamilton
description: Erfahren Sie, wie Sie Microsoft Teams-Apps entwerfen. Zu den Ressourcen gehören das Microsoft Teams UI Kit, bewährte Methoden, Beispiele und vieles mehr.
ms.author: lajanuar
ms.topic: overview
ms.openlocfilehash: 0c791b1e4733cd2a015e443ca5c4d0c433dd4d31
ms.sourcegitcommit: 00c657e3bf57d3b92aca7da941cde47a2eeff4d0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "49911905"
---
# <a name="designing-your-microsoft-teams-app"></a><span data-ttu-id="4a2b9-104">Entwerfen Ihrer Microsoft Teams-App</span><span class="sxs-lookup"><span data-stu-id="4a2b9-104">Designing your Microsoft Teams app</span></span>

:::image type="content" source="../../assets/images/design-guidelines-overview.png" alt-text="Konzeptionelle Abbildung zur Einführung in die Microsoft Teams-Entwurfsrichtlinien.":::

<span data-ttu-id="4a2b9-106">Unabhängig davon, ob Sie Designer, Produktmanager, Entwickler oder Hersteller mit Tools mit wenig Code sind, können Sie mit diesen Richtlinien schnell die richtigen Designentscheidungen für Ihre Microsoft Teams-App treffen.</span><span class="sxs-lookup"><span data-stu-id="4a2b9-106">Whether you're a designer, product manager, developer, or maker using low-code tools, these guidelines can help you quickly make the right design decisions for your Microsoft Teams app.</span></span>

## <a name="teams-app-design-principles"></a><span data-ttu-id="4a2b9-107">Entwurfsgrundsätze für Teams-Apps</span><span class="sxs-lookup"><span data-stu-id="4a2b9-107">Teams app design principles</span></span>

<span data-ttu-id="4a2b9-108">Mit Den Apps von Teams können Personen mehr zusammen erreichen.</span><span class="sxs-lookup"><span data-stu-id="4a2b9-108">Teams apps help people achieve more together.</span></span> <span data-ttu-id="4a2b9-109">Verwenden Sie diese Prinzipien, um Ihr Design zu leiten.</span><span class="sxs-lookup"><span data-stu-id="4a2b9-109">Use these principles to guide your design.</span></span>

:::row:::
   :::column span="":::

### <a name="collaborative"></a><span data-ttu-id="4a2b9-110">Collaborative</span><span class="sxs-lookup"><span data-stu-id="4a2b9-110">Collaborative</span></span>

<span data-ttu-id="4a2b9-111">Mit Den Apps von Teams können Personen mehr zusammen erreichen.</span><span class="sxs-lookup"><span data-stu-id="4a2b9-111">Teams apps help people achieve more together.</span></span> <span data-ttu-id="4a2b9-112">Verwenden Sie diese Prinzipien, um Ihren Entwurf zu leiten.</span><span class="sxs-lookup"><span data-stu-id="4a2b9-112">Use these principles to guide your design.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="trustworthy"></a><span data-ttu-id="4a2b9-113">Vertrauenswürdig</span><span class="sxs-lookup"><span data-stu-id="4a2b9-113">Trustworthy</span></span>

<span data-ttu-id="4a2b9-114">Die App ist sicher und kompatibel.</span><span class="sxs-lookup"><span data-stu-id="4a2b9-114">The app is secure and compliant.</span></span> <span data-ttu-id="4a2b9-115">Benutzer können auf einfache Weise Informationen zum Datenschutz finden.</span><span class="sxs-lookup"><span data-stu-id="4a2b9-115">Users can easily find information about privacy.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="globally-inclusive"></a><span data-ttu-id="4a2b9-116">Global inklusiv</span><span class="sxs-lookup"><span data-stu-id="4a2b9-116">Globally inclusive</span></span>

<span data-ttu-id="4a2b9-117">Personen mit allen Hintergründen, Fertigkeiten und Fächern können die App verwenden.</span><span class="sxs-lookup"><span data-stu-id="4a2b9-117">People of all backgrounds, skillsets, and disciplines can use the app.</span></span> <span data-ttu-id="4a2b9-118">Sie ist kulturell, rassisch und kulturell bekannt.</span><span class="sxs-lookup"><span data-stu-id="4a2b9-118">It’s culturally, racially, and socially aware.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="light"></a><span data-ttu-id="4a2b9-119">Niedrig</span><span class="sxs-lookup"><span data-stu-id="4a2b9-119">Light</span></span>

<span data-ttu-id="4a2b9-120">Die App konzentriert sich auf Kernszenarien, die mit Teams-Workflows kombiniert werden.</span><span class="sxs-lookup"><span data-stu-id="4a2b9-120">The app focuses on core scenarios that blend with Teams workflows.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="native-or-distinct"></a><span data-ttu-id="4a2b9-121">Systemeigene oder unterschiedliche</span><span class="sxs-lookup"><span data-stu-id="4a2b9-121">Native or distinct</span></span>

<span data-ttu-id="4a2b9-122">Die App verwendet systemeigene Teams-Designkomponenten oder eigene.</span><span class="sxs-lookup"><span data-stu-id="4a2b9-122">The app uses native Teams design components or your own.</span></span> <span data-ttu-id="4a2b9-123">Es gibt keine Mischung aus Farbschemas, Steuerelementen usw.</span><span class="sxs-lookup"><span data-stu-id="4a2b9-123">There’s no blend of color schemes, controls, etc.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="useful"></a><span data-ttu-id="4a2b9-124">Nützlich</span><span class="sxs-lookup"><span data-stu-id="4a2b9-124">Useful</span></span>

<span data-ttu-id="4a2b9-125">Die App basiert auf einem Szenario, das personen in Teams tun müssen.</span><span class="sxs-lookup"><span data-stu-id="4a2b9-125">The app is based on a scenario people need to do in Teams.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="easy-to-use"></a><span data-ttu-id="4a2b9-126">Einfach zu verwenden</span><span class="sxs-lookup"><span data-stu-id="4a2b9-126">Easy to use</span></span>

<span data-ttu-id="4a2b9-127">Die Benutzeroberfläche ist leicht zu verstehen, angenehm in Aussehen und Tonfall und macht die Produktivität der Benutzer produktiver.</span><span class="sxs-lookup"><span data-stu-id="4a2b9-127">The UI is easy to understand, pleasant in look and tone, and makes people more productive.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="responsive"></a><span data-ttu-id="4a2b9-128">Reaktionsfähig</span><span class="sxs-lookup"><span data-stu-id="4a2b9-128">Responsive</span></span>

<span data-ttu-id="4a2b9-129">Die App ist geräte- und bildschirmunabhängig.</span><span class="sxs-lookup"><span data-stu-id="4a2b9-129">The app is device and screen agnostic.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="accessible"></a><span data-ttu-id="4a2b9-130">Barrierefrei</span><span class="sxs-lookup"><span data-stu-id="4a2b9-130">Accessible</span></span>

<span data-ttu-id="4a2b9-131">Die App erfüllt die Barrierefreiheitsanforderungen von Teams in Bezug auf Farbkontrast, Navigationsalternativen und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="4a2b9-131">The app meets Teams accessibility requirements in terms of color contrast, navigation alternatives, and more.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="well-described"></a><span data-ttu-id="4a2b9-132">Gut beschrieben</span><span class="sxs-lookup"><span data-stu-id="4a2b9-132">Well described</span></span>

<span data-ttu-id="4a2b9-133">Text, Symbole und Bilder machen deutlich, wofür die App steht und wie sie verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="4a2b9-133">Text, icons, and images make it clear what the app is for and how to use it.</span></span>

   :::column-end:::
:::row-end:::

## <a name="creating-a-cohesive-experience"></a><span data-ttu-id="4a2b9-134">Erstellen einer gemeinsamen Besensung</span><span class="sxs-lookup"><span data-stu-id="4a2b9-134">Creating a cohesive experience</span></span>

<span data-ttu-id="4a2b9-135">Das Entwerfen einer Teams-App ist wie das Entwerfen einer herkömmlichen Web-App, aber auch ein wenig anders.</span><span class="sxs-lookup"><span data-stu-id="4a2b9-135">Designing a Teams app is like designing a conventional web app—but also a little different.</span></span> <span data-ttu-id="4a2b9-136">Ein effektives Design hebt die einzigartigen Attribute Ihrer App hervor und passt natürlich in die Features und Kontexte von Teams.</span><span class="sxs-lookup"><span data-stu-id="4a2b9-136">An effective design highlights your app's unique attributes while fitting naturally with Teams features and contexts.</span></span>

<span data-ttu-id="4a2b9-137">Diese Richtlinien und Ressourcen können Ihnen dabei helfen, dieses Gleichgewicht zu finden.</span><span class="sxs-lookup"><span data-stu-id="4a2b9-137">These guidelines and resources can help you strike that balance.</span></span> <span data-ttu-id="4a2b9-138">You'll know what to do and what to avoid when designing your Teams app (such as multi-level navigation in a tab).</span><span class="sxs-lookup"><span data-stu-id="4a2b9-138">You'll know what to do and what to avoid when designing your Teams app (such as multi-level navigation in a tab).</span></span>

## <a name="planning-your-app"></a><span data-ttu-id="4a2b9-139">Planen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="4a2b9-139">Planning your app</span></span>

<span data-ttu-id="4a2b9-140">Zum Entwerfen einer qualitativ hochwertigen Teams-App müssen Sie zunächst wissen, was Ihre App tun soll und wie sie von Denk personen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="4a2b9-140">To design a high-quality Teams app, you must first understand what you want your app to do and how you think people will use it.</span></span> <span data-ttu-id="4a2b9-141">Wenn Sie dies noch nicht gemacht haben, nehmen Sie sich etwas Zeit, um Ihre [App ordnungsgemäß zu planen.](../../concepts/extensibility-points.md)</span><span class="sxs-lookup"><span data-stu-id="4a2b9-141">If you haven't already, take some time to properly [plan your app](../../concepts/extensibility-points.md).</span></span>

## <a name="design-fundamentals"></a><span data-ttu-id="4a2b9-142">Grundlegendes zur Gestaltung</span><span class="sxs-lookup"><span data-stu-id="4a2b9-142">Design fundamentals</span></span>

<span data-ttu-id="4a2b9-143">Erfahren Sie [mehr über die Grundlagen des Teams-App-Designs,](design-teams-app-fundamentals.md)einschließlich Layout, Farbschemas und mehr.</span><span class="sxs-lookup"><span data-stu-id="4a2b9-143">Learn the [fundamentals of Teams app design](design-teams-app-fundamentals.md), including layout, color schemes, and more.</span></span>

## <a name="basic-fluent-ui-components-for-teams"></a><span data-ttu-id="4a2b9-144">Grundlegende Komponenten der Fluent-Benutzeroberfläche für Teams</span><span class="sxs-lookup"><span data-stu-id="4a2b9-144">Basic Fluent UI components for Teams</span></span>

<span data-ttu-id="4a2b9-145">Basierend auf der Fluent UI sind dies die [Kernelemente zum Erstellen vertrauter Teams-Schnittstellen.](design-teams-app-basic-ui-components.md)</span><span class="sxs-lookup"><span data-stu-id="4a2b9-145">Based on Fluent UI, these are the [core elements for creating familiar Teams interfaces](design-teams-app-basic-ui-components.md).</span></span>

## <a name="ui-templates"></a><span data-ttu-id="4a2b9-146">Vorlagen für Benutzeroberflächen</span><span class="sxs-lookup"><span data-stu-id="4a2b9-146">UI templates</span></span>

<span data-ttu-id="4a2b9-147">Erstellen Sie schnell komplexe, originalgetreue Designs mit [Vorlagen für häufige Verwendungsfälle](design-teams-app-ui-templates.md)und Workflows von Teams.</span><span class="sxs-lookup"><span data-stu-id="4a2b9-147">Quickly create complex, high-fidelity designs with [templates for common Teams use cases and workflows](design-teams-app-ui-templates.md).</span></span>

## <a name="app-capabilities"></a><span data-ttu-id="4a2b9-148">App-Funktionen</span><span class="sxs-lookup"><span data-stu-id="4a2b9-148">App capabilities</span></span>

<span data-ttu-id="4a2b9-149">Erfahren Sie, wie Benutzer Teams-Apps hinzufügen, verwenden und verwalten, um die einzelnen Funktionen in Ihrem Design zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="4a2b9-149">Understand how people add, use, and manage Teams apps to make the most of each capability in your design.</span></span>

* [<span data-ttu-id="4a2b9-150">Persönliche Apps</span><span class="sxs-lookup"><span data-stu-id="4a2b9-150">Personal apps</span></span>](../../concepts/design/personal-apps.md)
* [<span data-ttu-id="4a2b9-151">Registerkarten</span><span class="sxs-lookup"><span data-stu-id="4a2b9-151">Tabs</span></span>](../../tabs/design/tabs.md)
* [<span data-ttu-id="4a2b9-152">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="4a2b9-152">Messaging extensions</span></span>](../../messaging-extensions/design/messaging-extension-design.md)
* [<span data-ttu-id="4a2b9-153">Bots</span><span class="sxs-lookup"><span data-stu-id="4a2b9-153">Bots</span></span>](../../bots/design/bots.md)
* [<span data-ttu-id="4a2b9-154">Besprechungserweiterungen</span><span class="sxs-lookup"><span data-stu-id="4a2b9-154">Meeting extensions</span></span>](../../apps-in-teams-meetings/design/designing-apps-in-meetings.md)
* [<span data-ttu-id="4a2b9-155">Aufgabenmodule</span><span class="sxs-lookup"><span data-stu-id="4a2b9-155">Task modules</span></span>](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)
* [<span data-ttu-id="4a2b9-156">Adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="4a2b9-156">Adaptive Cards</span></span>](../../task-modules-and-cards/cards/design-effective-cards.md)

## <a name="tools-and-samples"></a><span data-ttu-id="4a2b9-157">Tools und Beispiele</span><span class="sxs-lookup"><span data-stu-id="4a2b9-157">Tools and samples</span></span>

<span data-ttu-id="4a2b9-158">Die folgenden Tools helfen Designern und Entwicklern bei den ersten Schritte.</span><span class="sxs-lookup"><span data-stu-id="4a2b9-158">The following tools can help designers and developers get started.</span></span>

### <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="4a2b9-159">Microsoft Teams UI Kit</span><span class="sxs-lookup"><span data-stu-id="4a2b9-159">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="4a2b9-160">Entwerfen Sie eine Teams-App mit Benutzeroberflächenkomponenten, Vorlagen und Beispielen, die Sie nach Bedarf ziehen, ablegen und ändern können.</span><span class="sxs-lookup"><span data-stu-id="4a2b9-160">Design a Teams app with UI components, templates, and examples that you can drag, drop, and modify as needed.</span></span> <span data-ttu-id="4a2b9-161">Das UI Kit enthält auch umfassende Informationen dazu, wie Apps in verschiedenen Teams-Szenarien aussehen und sich verhalten sollten.</span><span class="sxs-lookup"><span data-stu-id="4a2b9-161">The UI kit also includes comprehensive information about how apps should look and behave in different Teams scenarios.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4a2b9-162">Benutzeroberflächenkit (Bissma)</span><span class="sxs-lookup"><span data-stu-id="4a2b9-162">Get the UI kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

### <a name="microsoft-teams-ui-library"></a><span data-ttu-id="4a2b9-163">Microsoft Teams UI Library</span><span class="sxs-lookup"><span data-stu-id="4a2b9-163">Microsoft Teams UI Library</span></span>

<span data-ttu-id="4a2b9-164">Zeigen Sie einzelne Benutzeroberflächenvorlagen und zugehörige Komponenten von Teams in Ihrem Browser an, und testen Sie sie.</span><span class="sxs-lookup"><span data-stu-id="4a2b9-164">View and test individual Teams UI templates and related components in your browser.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4a2b9-165">Probieren Sie die Benutzeroberflächenbibliothek (Playground) aus.</span><span class="sxs-lookup"><span data-stu-id="4a2b9-165">Try the UI library (playground)</span></span>](https://dev-int.teams.microsoft.com/storybook/main/index.html)

<span data-ttu-id="4a2b9-166">Importieren Sie diese Vorlagen und zugehörigen Komponenten direkt in Ihr Teams-App-Projekt.</span><span class="sxs-lookup"><span data-stu-id="4a2b9-166">Import these templates and related components directly into your Teams app project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4a2b9-167">Abrufen der Benutzeroberflächenbibliothek (GitHub)</span><span class="sxs-lookup"><span data-stu-id="4a2b9-167">Get the UI library (GitHub)</span></span>](https://github.com/OfficeDev/microsoft-teams-ui-component-library)

### <a name="sample-app"></a><span data-ttu-id="4a2b9-168">Beispiel-App</span><span class="sxs-lookup"><span data-stu-id="4a2b9-168">Sample app</span></span>

<span data-ttu-id="4a2b9-169">Installieren Sie eine Beispiel-App, um zu sehen, wie Benutzeroberflächenvorlagen in Kontexten von Teams aussehen und sich verhalten.</span><span class="sxs-lookup"><span data-stu-id="4a2b9-169">Install a sample app to see how UI templates look and behave within Teams contexts.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4a2b9-170">Abrufen der Beispiel-App (GitHub)</span><span class="sxs-lookup"><span data-stu-id="4a2b9-170">Get the sample app (GitHub)</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-ui-templates/ts)

## <a name="other-resources"></a><span data-ttu-id="4a2b9-171">Sonstige Ressourcen</span><span class="sxs-lookup"><span data-stu-id="4a2b9-171">Other resources</span></span>

<span data-ttu-id="4a2b9-172">Weitere Informationen finden Sie in einer der folgenden Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="4a2b9-172">To learn more, try one of the following resources.</span></span>

### <a name="fluent-ui-documentation"></a><span data-ttu-id="4a2b9-173">Dokumentation zur Fluent-UI</span><span class="sxs-lookup"><span data-stu-id="4a2b9-173">Fluent UI documentation</span></span>

<span data-ttu-id="4a2b9-174">Erhalten Sie Codebeispiele und Implementierungsdetails für die Fluent UI-basierten Komponenten, die zum Erstellen von Teams-Erfahrungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="4a2b9-174">Get code samples and implementation details for the Fluent UI-based components used to build Teams experiences.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4a2b9-175">Testen von Komponenten der Benutzeroberfläche von Teams (Fluent UI)</span><span class="sxs-lookup"><span data-stu-id="4a2b9-175">Try Teams UI components (Fluent UI)</span></span>](https://fluentsite.z22.web.core.windows.net/)

### <a name="adaptive-cards-designer"></a><span data-ttu-id="4a2b9-176">Designer für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="4a2b9-176">Adaptive Cards designer</span></span>

<span data-ttu-id="4a2b9-177">Entwerfen Sie adaptive Karten in unserem webbasierten Tool.</span><span class="sxs-lookup"><span data-stu-id="4a2b9-177">Design Adaptive Cards in our web-based tool.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4a2b9-178">Testen des Designers für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="4a2b9-178">Try the Adaptive Cards designer</span></span>](https://adaptivecards.io/designer/)
