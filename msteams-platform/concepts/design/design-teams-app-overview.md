---
title: Entwerfen Ihrer benutzerdefinierten App
author: heath-hamilton
description: Erfahren Sie, wie Sie Microsoft Teams entwerfen. Zu den Ressourcen gehören Microsoft Teams UI Kit, bewährte Methoden, Beispiele und vieles mehr.
localization_priority: Normal
ms.author: surbhigupta
ms.topic: overview
ms.openlocfilehash: 19b8f8cbcbc52aa02ccd5d94f5bc4c088f2ae28a
ms.sourcegitcommit: 4224c44d169b1a289cbf1d3353de6bc6de7c7ea8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2021
ms.locfileid: "52644875"
---
# <a name="designing-your-microsoft-teams-app"></a><span data-ttu-id="26517-104">Entwerfen Ihrer Microsoft Teams App</span><span class="sxs-lookup"><span data-stu-id="26517-104">Designing your Microsoft Teams app</span></span>

:::image type="content" source="../../assets/images/design-guidelines-overview.png" alt-text="Konzeptionelles Bild, in dem Microsoft Teams Entwurfsrichtlinien vorgestellt werden.":::

<span data-ttu-id="26517-106">Unabhängig davon, ob Sie Designer, Produktmanager, Entwickler oder Hersteller sind, die Tools mit niedrigem Code verwenden, können diese Richtlinien Ihnen helfen, schnell die richtigen Entwurfsentscheidungen für Ihre Microsoft Teams treffen.</span><span class="sxs-lookup"><span data-stu-id="26517-106">Whether you're a designer, product manager, developer, or maker using low-code tools, these guidelines can help you quickly make the right design decisions for your Microsoft Teams app.</span></span>

## <a name="creating-a-cohesive-experience"></a><span data-ttu-id="26517-107">Erstellen einer gemeinsamen Erfahrung</span><span class="sxs-lookup"><span data-stu-id="26517-107">Creating a cohesive experience</span></span>

<span data-ttu-id="26517-108">Das Entwerfen Teams app ist wie das Entwerfen einer herkömmlichen Web-App – aber auch ein wenig anders.</span><span class="sxs-lookup"><span data-stu-id="26517-108">Designing a Teams app is like designing a conventional web app—but also a little different.</span></span> <span data-ttu-id="26517-109">Ein effektives Design hebt die eindeutigen Attribute Ihrer App hervor und passt sich natürlich Teams Features und Kontexten an.</span><span class="sxs-lookup"><span data-stu-id="26517-109">An effective design highlights your app's unique attributes while fitting naturally with Teams features and contexts.</span></span>

<span data-ttu-id="26517-110">Diese Richtlinien und Ressourcen können Ihnen dabei helfen, dieses Gleichgewicht zu finden.</span><span class="sxs-lookup"><span data-stu-id="26517-110">These guidelines and resources can help you strike that balance.</span></span> <span data-ttu-id="26517-111">Sie wissen, was Sie beim Entwerfen Ihrer Teams -App (z. B. mehrstufige Navigation auf einer Registerkarte) vermeiden sollten.</span><span class="sxs-lookup"><span data-stu-id="26517-111">You'll know what to do and what to avoid when designing your Teams app (such as multi-level navigation in a tab).</span></span>

## <a name="teams-app-design-principles"></a><span data-ttu-id="26517-112">Teams von App-Designprinzipien</span><span class="sxs-lookup"><span data-stu-id="26517-112">Teams app design principles</span></span>

<span data-ttu-id="26517-113">Teams Apps helfen, gemeinsam mehr zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="26517-113">Teams apps help people achieve more together.</span></span> <span data-ttu-id="26517-114">Verwenden Sie diese Prinzipien, um Ihr Design zu leiten.</span><span class="sxs-lookup"><span data-stu-id="26517-114">Use these principles to guide your design.</span></span>

:::row:::
   :::column span="":::

### <a name="collaborative"></a><span data-ttu-id="26517-115">Zusammenarbeit</span><span class="sxs-lookup"><span data-stu-id="26517-115">Collaborative</span></span>

<span data-ttu-id="26517-116">Teams Apps helfen, gemeinsam mehr zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="26517-116">Teams apps help people achieve more together.</span></span> <span data-ttu-id="26517-117">Verwenden Sie diese Prinzipien, um Ihr Design zu leiten.</span><span class="sxs-lookup"><span data-stu-id="26517-117">Use these principles to guide your design.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="trustworthy"></a><span data-ttu-id="26517-118">Vertrauenswürdig</span><span class="sxs-lookup"><span data-stu-id="26517-118">Trustworthy</span></span>

<span data-ttu-id="26517-119">Die App ist sicher und kompatibel.</span><span class="sxs-lookup"><span data-stu-id="26517-119">The app is secure and compliant.</span></span> <span data-ttu-id="26517-120">Benutzer können auf einfache Weise Informationen zum Datenschutz finden.</span><span class="sxs-lookup"><span data-stu-id="26517-120">Users can easily find information about privacy.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="globally-inclusive"></a><span data-ttu-id="26517-121">Global inklusive</span><span class="sxs-lookup"><span data-stu-id="26517-121">Globally inclusive</span></span>

<span data-ttu-id="26517-122">Personen aller Hintergründe, Fähigkeiten und Disziplinen können die App verwenden.</span><span class="sxs-lookup"><span data-stu-id="26517-122">People of all backgrounds, skillsets, and disciplines can use the app.</span></span> <span data-ttu-id="26517-123">Sie ist kulturell, rassistisch und gesellschaftlich bewusst.</span><span class="sxs-lookup"><span data-stu-id="26517-123">It’s culturally, racially, and socially aware.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="light"></a><span data-ttu-id="26517-124">Niedrig</span><span class="sxs-lookup"><span data-stu-id="26517-124">Light</span></span>

<span data-ttu-id="26517-125">Die App konzentriert sich auf Kernszenarien, die mit Teams werden.</span><span class="sxs-lookup"><span data-stu-id="26517-125">The app focuses on core scenarios that blend with Teams workflows.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="native-or-distinct"></a><span data-ttu-id="26517-126">Native oder unterschiedliche</span><span class="sxs-lookup"><span data-stu-id="26517-126">Native or distinct</span></span>

<span data-ttu-id="26517-127">Die App verwendet systemeigene Teams oder Eigene.</span><span class="sxs-lookup"><span data-stu-id="26517-127">The app uses native Teams design components or your own.</span></span> <span data-ttu-id="26517-128">Es gibt keine Mischung aus Farbschemas, Steuerelementen und so weiter.</span><span class="sxs-lookup"><span data-stu-id="26517-128">There’s no blend of color schemes, controls, and so on.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="useful"></a><span data-ttu-id="26517-129">Nützlich</span><span class="sxs-lookup"><span data-stu-id="26517-129">Useful</span></span>

<span data-ttu-id="26517-130">Die App basiert auf einem Szenario, das personen in einem Teams.</span><span class="sxs-lookup"><span data-stu-id="26517-130">The app is based on a scenario people need to do in Teams.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="easy-to-use"></a><span data-ttu-id="26517-131">Einfach zu verwenden</span><span class="sxs-lookup"><span data-stu-id="26517-131">Easy to use</span></span>

<span data-ttu-id="26517-132">Die Benutzeroberfläche ist leicht zu verstehen, angenehm in Aussehen und Ton und macht die Benutzer produktiver.</span><span class="sxs-lookup"><span data-stu-id="26517-132">The UI is easy to understand, pleasant in look and tone, and makes people more productive.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="responsive"></a><span data-ttu-id="26517-133">Reaktionsfähig</span><span class="sxs-lookup"><span data-stu-id="26517-133">Responsive</span></span>

<span data-ttu-id="26517-134">Die App ist geräte- und bildschirmunabhängig.</span><span class="sxs-lookup"><span data-stu-id="26517-134">The app is device and screen agnostic.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="accessible"></a><span data-ttu-id="26517-135">Barrierefrei</span><span class="sxs-lookup"><span data-stu-id="26517-135">Accessible</span></span>

<span data-ttu-id="26517-136">Die App erfüllt Teams Barrierefreiheitsanforderungen in Bezug auf Farbkontrast, Navigationsalternativen und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="26517-136">The app meets Teams accessibility requirements in terms of color contrast, navigation alternatives, and more.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="well-described"></a><span data-ttu-id="26517-137">Gut beschrieben</span><span class="sxs-lookup"><span data-stu-id="26517-137">Well described</span></span>

<span data-ttu-id="26517-138">Text, Symbole und Bilder machen deutlich, wofür die App steht und wie sie verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="26517-138">Text, icons, and images make it clear what the app is for and how to use it.</span></span>

   :::column-end:::
:::row-end:::

## <a name="teams-design-system"></a><span data-ttu-id="26517-139">Teams-Designsystem</span><span class="sxs-lookup"><span data-stu-id="26517-139">Teams design system</span></span>

<span data-ttu-id="26517-140">Lernen Sie [die Grundlagen des Teams-App-Designs,](design-teams-app-fundamentals.md)einschließlich Layout, Farbschemas und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="26517-140">Learn the [fundamentals of Teams app design](design-teams-app-fundamentals.md), including layout, color schemes, and more.</span></span>

## <a name="app-capabilities"></a><span data-ttu-id="26517-141">App-Funktionen</span><span class="sxs-lookup"><span data-stu-id="26517-141">App capabilities</span></span>

<span data-ttu-id="26517-142">Erfahren Sie, wie Personen apps hinzufügen, Teams verwenden und verwalten, um die einzelnen Funktionen in Ihrem Entwurf zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="26517-142">Understand how people add, use, and manage Teams apps to make the most of each capability in your design.</span></span>

* [<span data-ttu-id="26517-143">Persönliche Apps</span><span class="sxs-lookup"><span data-stu-id="26517-143">Personal apps</span></span>](../../concepts/design/personal-apps.md)
* [<span data-ttu-id="26517-144">Registerkarten</span><span class="sxs-lookup"><span data-stu-id="26517-144">Tabs</span></span>](../../tabs/design/tabs.md)
* [<span data-ttu-id="26517-145">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="26517-145">Messaging extensions</span></span>](../../messaging-extensions/design/messaging-extension-design.md)
* [<span data-ttu-id="26517-146">Bots</span><span class="sxs-lookup"><span data-stu-id="26517-146">Bots</span></span>](../../bots/design/bots.md)
* [<span data-ttu-id="26517-147">Besprechungserweiterungen</span><span class="sxs-lookup"><span data-stu-id="26517-147">Meeting extensions</span></span>](../../apps-in-teams-meetings/design/designing-apps-in-meetings.md)

## <a name="ui-templates"></a><span data-ttu-id="26517-148">Vorlagen für Benutzeroberflächen</span><span class="sxs-lookup"><span data-stu-id="26517-148">UI templates</span></span>

<span data-ttu-id="26517-149">Erstellen Sie schnell komplexe Designs mit hoher Genauigkeit mit Vorlagen für [Teams und Workflows](design-teams-app-ui-templates.md).</span><span class="sxs-lookup"><span data-stu-id="26517-149">Quickly create complex, high-fidelity designs with [templates for common Teams use cases and workflows](design-teams-app-ui-templates.md).</span></span>

## <a name="basic-ui-components"></a><span data-ttu-id="26517-150">Grundlegende Benutzeroberflächenkomponenten</span><span class="sxs-lookup"><span data-stu-id="26517-150">Basic UI components</span></span>

<span data-ttu-id="26517-151">Basierend auf der Fluent-Benutzeroberfläche sind dies die [Kernelemente,](design-teams-app-basic-ui-components.md) die Sie verwenden können, um Teams von Grund auf neu zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="26517-151">Based on Fluent UI, these are the [core elements](design-teams-app-basic-ui-components.md) you can use to create Teams experiences from scratch.</span></span>

## <a name="tools-and-samples"></a><span data-ttu-id="26517-152">Tools und Beispiele</span><span class="sxs-lookup"><span data-stu-id="26517-152">Tools and samples</span></span>

<span data-ttu-id="26517-153">Die folgenden Tools helfen Designern und Entwicklern bei den ersten Schritte:</span><span class="sxs-lookup"><span data-stu-id="26517-153">The following tools can help designers and developers get started:</span></span>

### <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="26517-154">Microsoft Teams-UI-Kit</span><span class="sxs-lookup"><span data-stu-id="26517-154">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="26517-155">Entwerfen Sie Teams App mit Benutzeroberflächenkomponenten, Vorlagen und Beispielen, die Sie nach Bedarf ziehen, ablegen und ändern können.</span><span class="sxs-lookup"><span data-stu-id="26517-155">Design a Teams app with UI components, templates, and examples that you can drag, drop, and modify as needed.</span></span> <span data-ttu-id="26517-156">Das UI Kit enthält außerdem umfassende Informationen dazu, wie Apps in unterschiedlichen Szenarien aussehen und Teams sollten.</span><span class="sxs-lookup"><span data-stu-id="26517-156">The UI kit also includes comprehensive information about how apps should look and behave in different Teams scenarios.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="26517-157">Benutzeroberflächenkit (Figma)</span><span class="sxs-lookup"><span data-stu-id="26517-157">Get the UI kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

### <a name="microsoft-teams-ui-library"></a><span data-ttu-id="26517-158">Microsoft Teams Benutzeroberflächenbibliothek</span><span class="sxs-lookup"><span data-stu-id="26517-158">Microsoft Teams UI Library</span></span>

<span data-ttu-id="26517-159">Anzeigen und Testen einzelner Teams benutzeroberflächenvorlagen und zugehörigen Komponenten in Ihrem Browser.</span><span class="sxs-lookup"><span data-stu-id="26517-159">View and test individual Teams UI templates and related components in your browser.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="26517-160">Probieren Sie die Benutzeroberflächenbibliothek (Playground) aus.</span><span class="sxs-lookup"><span data-stu-id="26517-160">Try the UI library (playground)</span></span>](https://dev-int.teams.microsoft.com/storybook/main/index.html)

<span data-ttu-id="26517-161">Importieren Sie diese Vorlagen und zugehörigen Komponenten direkt in Teams App-Projekt.</span><span class="sxs-lookup"><span data-stu-id="26517-161">Import these templates and related components directly into your Teams app project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="26517-162">Benutzeroberflächenbibliothek (GitHub)</span><span class="sxs-lookup"><span data-stu-id="26517-162">Get the UI library (GitHub)</span></span>](https://github.com/OfficeDev/microsoft-teams-ui-component-library)

### <a name="sample-app"></a><span data-ttu-id="26517-163">Beispiel-App</span><span class="sxs-lookup"><span data-stu-id="26517-163">Sample app</span></span>

<span data-ttu-id="26517-164">Sie können eine Beispiel-App hochladen, um zu sehen, wie Apps im Client aussehen und sich Teams verhalten sollen.</span><span class="sxs-lookup"><span data-stu-id="26517-164">You can upload a sample app to see how apps should look and behave in the Teams client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="26517-165">Die Beispiel-App (GitHub)</span><span class="sxs-lookup"><span data-stu-id="26517-165">Get the sample app (GitHub)</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-ui-templates/ts)

## <a name="other-resources"></a><span data-ttu-id="26517-166">Sonstige Ressourcen</span><span class="sxs-lookup"><span data-stu-id="26517-166">Other resources</span></span>

<span data-ttu-id="26517-167">Weitere Informationen finden Sie in einer der folgenden Ressourcen:</span><span class="sxs-lookup"><span data-stu-id="26517-167">To learn more, try one of the following resources:</span></span>

### <a name="fluent-ui-documentation"></a><span data-ttu-id="26517-168">Dokumentation zur Fluent-Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="26517-168">Fluent UI documentation</span></span>

<span data-ttu-id="26517-169">Hier finden Sie Codebeispiele und Implementierungsdetails für die grundlegenden Fluent UI-Komponenten, die zum Erstellen Teams werden.</span><span class="sxs-lookup"><span data-stu-id="26517-169">Get code samples and implementation details for the basic Fluent UI components used to build Teams experiences.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="26517-170">Testen Teams Benutzeroberflächenkomponenten (Fluent UI)</span><span class="sxs-lookup"><span data-stu-id="26517-170">Try Teams UI components (Fluent UI)</span></span>](https://fluentsite.z22.web.core.windows.net/)

### <a name="adaptive-cards-designer"></a><span data-ttu-id="26517-171">Designer für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="26517-171">Adaptive Cards designer</span></span>

<span data-ttu-id="26517-172">Entwerfen Sie adaptive Karten in unserem webbasierten Tool.</span><span class="sxs-lookup"><span data-stu-id="26517-172">Design Adaptive Cards in our web-based tool.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="26517-173">Testen des Designers für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="26517-173">Try the Adaptive Cards designer</span></span>](https://adaptivecards.io/designer/)
