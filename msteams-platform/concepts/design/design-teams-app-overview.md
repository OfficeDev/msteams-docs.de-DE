---
title: Entwerfen Ihrer benutzerdefinierten App
author: heath-hamilton
description: Erfahren Sie, wie Sie Microsoft Teams-Apps entwerfen. Zu den Ressourcen gehören das Microsoft Teams UI Kit, bewährte Methoden, Beispiele und vieles mehr.
ms.author: lajanuar
ms.topic: overview
ms.openlocfilehash: 7a6786cdf9091b04f89ebd6c8bb03799eb7d127a
ms.sourcegitcommit: b50f6d68482cad43a60642a9947d1be17809a7df
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2021
ms.locfileid: "51634495"
---
# <a name="designing-your-microsoft-teams-app"></a><span data-ttu-id="02b44-104">Entwerfen Ihrer Microsoft Teams-App</span><span class="sxs-lookup"><span data-stu-id="02b44-104">Designing your Microsoft Teams app</span></span>

:::image type="content" source="../../assets/images/design-guidelines-overview.png" alt-text="Konzeptionelle Abbildung, in der die Microsoft Teams-Entwurfsrichtlinien vorgestellt werden.":::

<span data-ttu-id="02b44-106">Unabhängig davon, ob Sie Designer, Produktmanager, Entwickler oder Hersteller mit Tools mit niedrigem Code sind, können Diese Richtlinien Ihnen dabei helfen, schnell die richtigen Entwurfsentscheidungen für Ihre Microsoft Teams-App zu treffen.</span><span class="sxs-lookup"><span data-stu-id="02b44-106">Whether you're a designer, product manager, developer, or maker using low-code tools, these guidelines can help you quickly make the right design decisions for your Microsoft Teams app.</span></span>

## <a name="teams-app-design-principles"></a><span data-ttu-id="02b44-107">Entwurfsprinzipien für Teams-Apps</span><span class="sxs-lookup"><span data-stu-id="02b44-107">Teams app design principles</span></span>

<span data-ttu-id="02b44-108">Teams-Apps helfen Den Menschen, gemeinsam mehr zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="02b44-108">Teams apps help people achieve more together.</span></span> <span data-ttu-id="02b44-109">Verwenden Sie diese Prinzipien, um Ihr Design zu leiten.</span><span class="sxs-lookup"><span data-stu-id="02b44-109">Use these principles to guide your design.</span></span>

:::row:::
   :::column span="":::

### <a name="collaborative"></a><span data-ttu-id="02b44-110">Zusammenarbeit</span><span class="sxs-lookup"><span data-stu-id="02b44-110">Collaborative</span></span>

<span data-ttu-id="02b44-111">Teams-Apps helfen Den Menschen, gemeinsam mehr zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="02b44-111">Teams apps help people achieve more together.</span></span> <span data-ttu-id="02b44-112">Verwenden Sie diese Prinzipien, um Ihr Design zu leiten.</span><span class="sxs-lookup"><span data-stu-id="02b44-112">Use these principles to guide your design.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="trustworthy"></a><span data-ttu-id="02b44-113">Vertrauenswürdig</span><span class="sxs-lookup"><span data-stu-id="02b44-113">Trustworthy</span></span>

<span data-ttu-id="02b44-114">Die App ist sicher und kompatibel.</span><span class="sxs-lookup"><span data-stu-id="02b44-114">The app is secure and compliant.</span></span> <span data-ttu-id="02b44-115">Benutzer können auf einfache Weise Informationen zum Datenschutz finden.</span><span class="sxs-lookup"><span data-stu-id="02b44-115">Users can easily find information about privacy.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="globally-inclusive"></a><span data-ttu-id="02b44-116">Global inklusive</span><span class="sxs-lookup"><span data-stu-id="02b44-116">Globally inclusive</span></span>

<span data-ttu-id="02b44-117">Personen aller Hintergründe, Fähigkeiten und Disziplinen können die App verwenden.</span><span class="sxs-lookup"><span data-stu-id="02b44-117">People of all backgrounds, skillsets, and disciplines can use the app.</span></span> <span data-ttu-id="02b44-118">Sie ist kulturell, rassistisch und gesellschaftlich bewusst.</span><span class="sxs-lookup"><span data-stu-id="02b44-118">It’s culturally, racially, and socially aware.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="light"></a><span data-ttu-id="02b44-119">Niedrig</span><span class="sxs-lookup"><span data-stu-id="02b44-119">Light</span></span>

<span data-ttu-id="02b44-120">Die App konzentriert sich auf Kernszenarien, die mit Teams-Workflows kombiniert werden.</span><span class="sxs-lookup"><span data-stu-id="02b44-120">The app focuses on core scenarios that blend with Teams workflows.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="native-or-distinct"></a><span data-ttu-id="02b44-121">Native oder unterschiedliche</span><span class="sxs-lookup"><span data-stu-id="02b44-121">Native or distinct</span></span>

<span data-ttu-id="02b44-122">Die App verwendet systemeigene Teams-Entwurfskomponenten oder eigene.</span><span class="sxs-lookup"><span data-stu-id="02b44-122">The app uses native Teams design components or your own.</span></span> <span data-ttu-id="02b44-123">Es gibt keine Mischung aus Farbschemas, Steuerelementen usw.</span><span class="sxs-lookup"><span data-stu-id="02b44-123">There’s no blend of color schemes, controls, etc.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="useful"></a><span data-ttu-id="02b44-124">Nützlich</span><span class="sxs-lookup"><span data-stu-id="02b44-124">Useful</span></span>

<span data-ttu-id="02b44-125">Die App basiert auf einem Szenario, das personen in Teams tun müssen.</span><span class="sxs-lookup"><span data-stu-id="02b44-125">The app is based on a scenario people need to do in Teams.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="easy-to-use"></a><span data-ttu-id="02b44-126">Einfach zu verwenden</span><span class="sxs-lookup"><span data-stu-id="02b44-126">Easy to use</span></span>

<span data-ttu-id="02b44-127">Die Benutzeroberfläche ist leicht zu verstehen, angenehm in Aussehen und Ton und macht die Benutzer produktiver.</span><span class="sxs-lookup"><span data-stu-id="02b44-127">The UI is easy to understand, pleasant in look and tone, and makes people more productive.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="responsive"></a><span data-ttu-id="02b44-128">Reaktionsfähig</span><span class="sxs-lookup"><span data-stu-id="02b44-128">Responsive</span></span>

<span data-ttu-id="02b44-129">Die App ist geräte- und bildschirmunabhängig.</span><span class="sxs-lookup"><span data-stu-id="02b44-129">The app is device and screen agnostic.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="accessible"></a><span data-ttu-id="02b44-130">Barrierefrei</span><span class="sxs-lookup"><span data-stu-id="02b44-130">Accessible</span></span>

<span data-ttu-id="02b44-131">Die App erfüllt die Anforderungen an die Barrierefreiheit von Teams in Bezug auf Farbkontrast, Navigationsalternativen und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="02b44-131">The app meets Teams accessibility requirements in terms of color contrast, navigation alternatives, and more.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="well-described"></a><span data-ttu-id="02b44-132">Gut beschrieben</span><span class="sxs-lookup"><span data-stu-id="02b44-132">Well described</span></span>

<span data-ttu-id="02b44-133">Text, Symbole und Bilder machen deutlich, wofür die App steht und wie sie verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="02b44-133">Text, icons, and images make it clear what the app is for and how to use it.</span></span>

   :::column-end:::
:::row-end:::

## <a name="creating-a-cohesive-experience"></a><span data-ttu-id="02b44-134">Erstellen einer gemeinsamen Erfahrung</span><span class="sxs-lookup"><span data-stu-id="02b44-134">Creating a cohesive experience</span></span>

<span data-ttu-id="02b44-135">Das Entwerfen einer Teams-App gleicht dem Entwerfen einer herkömmlichen Web-App – aber auch etwas anders.</span><span class="sxs-lookup"><span data-stu-id="02b44-135">Designing a Teams app is like designing a conventional web app—but also a little different.</span></span> <span data-ttu-id="02b44-136">Ein effektives Design hebt die eindeutigen Attribute Ihrer App hervor und passt sich natürlich an die Features und Kontexte von Teams an.</span><span class="sxs-lookup"><span data-stu-id="02b44-136">An effective design highlights your app's unique attributes while fitting naturally with Teams features and contexts.</span></span>

<span data-ttu-id="02b44-137">Diese Richtlinien und Ressourcen können Ihnen dabei helfen, dieses Gleichgewicht zu finden.</span><span class="sxs-lookup"><span data-stu-id="02b44-137">These guidelines and resources can help you strike that balance.</span></span> <span data-ttu-id="02b44-138">Sie wissen, was Sie beim Entwerfen Ihrer Teams-App vermeiden sollten (z. B. mehrstufige Navigation auf einer Registerkarte).</span><span class="sxs-lookup"><span data-stu-id="02b44-138">You'll know what to do and what to avoid when designing your Teams app (such as multi-level navigation in a tab).</span></span>

## <a name="planning-your-app"></a><span data-ttu-id="02b44-139">Planen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="02b44-139">Planning your app</span></span>

<span data-ttu-id="02b44-140">Um eine qualitativ hochwertige Teams-App zu entwerfen, müssen Sie zunächst wissen, was Ihre App tun soll und wie sie von den Personen verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="02b44-140">To design a high-quality Teams app, you must first understand what you want your app to do and how you think people will use it.</span></span> <span data-ttu-id="02b44-141">Wenn Sie dies noch nicht gemacht haben, nehmen Sie sich etwas Zeit, um Ihre [App ordnungsgemäß zu planen.](../../concepts/extensibility-points.md)</span><span class="sxs-lookup"><span data-stu-id="02b44-141">If you haven't already, take some time to properly [plan your app](../../concepts/extensibility-points.md).</span></span>

## <a name="design-fundamentals"></a><span data-ttu-id="02b44-142">Grundlegendes zur Gestaltung</span><span class="sxs-lookup"><span data-stu-id="02b44-142">Design fundamentals</span></span>

<span data-ttu-id="02b44-143">Erfahren Sie [mehr über die Grundlagen des Teams-App-Designs,](design-teams-app-fundamentals.md)einschließlich Layout, Farbschemas und mehr.</span><span class="sxs-lookup"><span data-stu-id="02b44-143">Learn the [fundamentals of Teams app design](design-teams-app-fundamentals.md), including layout, color schemes, and more.</span></span>

## <a name="basic-fluent-ui-components-for-teams"></a><span data-ttu-id="02b44-144">Grundlegende Komponenten der Fluent-Benutzeroberfläche für Teams</span><span class="sxs-lookup"><span data-stu-id="02b44-144">Basic Fluent UI components for Teams</span></span>

<span data-ttu-id="02b44-145">Basierend auf der Fluent-Benutzeroberfläche sind dies die [Kernelemente zum Erstellen vertrauter Teams-Schnittstellen.](design-teams-app-basic-ui-components.md)</span><span class="sxs-lookup"><span data-stu-id="02b44-145">Based on Fluent UI, these are the [core elements for creating familiar Teams interfaces](design-teams-app-basic-ui-components.md).</span></span>

## <a name="ui-templates"></a><span data-ttu-id="02b44-146">Vorlagen für Benutzeroberflächen</span><span class="sxs-lookup"><span data-stu-id="02b44-146">UI templates</span></span>

<span data-ttu-id="02b44-147">Erstellen Sie schnell komplexe Designs mit hoher Genauigkeit mit [Vorlagen für häufige Teams-Verwendungsfälle und Workflows.](design-teams-app-ui-templates.md)</span><span class="sxs-lookup"><span data-stu-id="02b44-147">Quickly create complex, high-fidelity designs with [templates for common Teams use cases and workflows](design-teams-app-ui-templates.md).</span></span>

## <a name="app-capabilities"></a><span data-ttu-id="02b44-148">App-Funktionen</span><span class="sxs-lookup"><span data-stu-id="02b44-148">App capabilities</span></span>

<span data-ttu-id="02b44-149">Erfahren Sie, wie Benutzer Teams-Apps hinzufügen, verwenden und verwalten, um die einzelnen Funktionen in Ihrem Entwurf zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="02b44-149">Understand how people add, use, and manage Teams apps to make the most of each capability in your design.</span></span>

* [<span data-ttu-id="02b44-150">Persönliche Apps</span><span class="sxs-lookup"><span data-stu-id="02b44-150">Personal apps</span></span>](../../concepts/design/personal-apps.md)
* [<span data-ttu-id="02b44-151">Tabs</span><span class="sxs-lookup"><span data-stu-id="02b44-151">Tabs</span></span>](../../tabs/design/tabs.md)
* [<span data-ttu-id="02b44-152">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="02b44-152">Messaging extensions</span></span>](../../messaging-extensions/design/messaging-extension-design.md)
* [<span data-ttu-id="02b44-153">Bots</span><span class="sxs-lookup"><span data-stu-id="02b44-153">Bots</span></span>](../../bots/design/bots.md)
* [<span data-ttu-id="02b44-154">Besprechungserweiterungen</span><span class="sxs-lookup"><span data-stu-id="02b44-154">Meeting extensions</span></span>](../../apps-in-teams-meetings/design/designing-apps-in-meetings.md)
* [<span data-ttu-id="02b44-155">Aufgabenmodule</span><span class="sxs-lookup"><span data-stu-id="02b44-155">Task modules</span></span>](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)
* [<span data-ttu-id="02b44-156">Adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="02b44-156">Adaptive Cards</span></span>](../../task-modules-and-cards/cards/design-effective-cards.md)

## <a name="app-customization"></a><span data-ttu-id="02b44-157">App-Anpassung</span><span class="sxs-lookup"><span data-stu-id="02b44-157">App customization</span></span>

<span data-ttu-id="02b44-158">Erfahren Sie, wie der Teams-Administrator die App je nach Bedarf der Organisation anpassen oder neubranden kann.</span><span class="sxs-lookup"><span data-stu-id="02b44-158">Understand how the Teams admin can customize or rebrand the app based on the organization's need.</span></span> <span data-ttu-id="02b44-159">Diese Anpassung ist aktiviert, wenn Sie die `configurableProperties` im Manifestschema definieren.</span><span class="sxs-lookup"><span data-stu-id="02b44-159">This customization is enabled if you define the `configurableProperties` in the manifest schema.</span></span> <span data-ttu-id="02b44-160">Weitere Informationen finden Sie unter [Anpassen von Apps in Microsoft Teams](/MicrosoftTeams/customize-apps).</span><span class="sxs-lookup"><span data-stu-id="02b44-160">For more information, see [Customize apps in Microsoft Teams](/MicrosoftTeams/customize-apps).</span></span>

> [!NOTE]
> <span data-ttu-id="02b44-161">Dieses Feature ist derzeit nur in der Entwicklervorschau verfügbar.</span><span class="sxs-lookup"><span data-stu-id="02b44-161">This feature is currently available in developer preview only.</span></span>
> 
> <span data-ttu-id="02b44-162">Mithilfe der App-Anpassung können Administratoren das Aussehen und Die-Gefühl der Apps ändern, die über Bots, Messagingerweiterungen, Registerkarten und Connectors geladen werden.</span><span class="sxs-lookup"><span data-stu-id="02b44-162">App customization enables admins to change the look-and-feel of the apps loaded through bots, messaging extensions, tabs, and connectors.</span></span> <span data-ttu-id="02b44-163">Wenn der Teams-Administrator beispielsweise den Namen einer App von *Contoso* in *Contoso Agent* anpasst, wird die App benutzern mit dem neuen Namen *Contoso Agent* angezeigt.</span><span class="sxs-lookup"><span data-stu-id="02b44-163">For example, if the Teams admin customizes the name of an app from *Contoso* to *Contoso Agent*, then the app will appear with the new name *Contoso Agent* to users.</span></span> <span data-ttu-id="02b44-164">Beim Hinzufügen eines Connectors zu einem Chat wird in der Liste der Connectors jedoch weiterhin der Name der App als *Contoso angezeigt.*</span><span class="sxs-lookup"><span data-stu-id="02b44-164">However, while adding a connector to a chat, in the list the connectors will still show the name of the app as *Contoso*.</span></span>
> 
> <span data-ttu-id="02b44-165">Als bewährte Methode müssen Sie Anpassungsrichtlinien für App-Benutzer und -Kunden bereitstellen, die sie beim Anpassen Ihrer App befolgen müssen.</span><span class="sxs-lookup"><span data-stu-id="02b44-165">As a best practice, you must provide customization guidelines for app users and customers to follow when customizing your app.</span></span> <span data-ttu-id="02b44-166">Weitere Informationen finden Sie unter [Anpassen von Apps in Microsoft Teams](/MicrosoftTeams/customize-apps).</span><span class="sxs-lookup"><span data-stu-id="02b44-166">For more information, see [customize apps in Microsoft Teams](/MicrosoftTeams/customize-apps).</span></span>

## <a name="tools-and-samples"></a><span data-ttu-id="02b44-167">Tools und Beispiele</span><span class="sxs-lookup"><span data-stu-id="02b44-167">Tools and samples</span></span>

<span data-ttu-id="02b44-168">Die folgenden Tools helfen Designern und Entwicklern bei den ersten Schritte:</span><span class="sxs-lookup"><span data-stu-id="02b44-168">The following tools can help designers and developers get started:</span></span>

### <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="02b44-169">Microsoft Teams-UI-Kit</span><span class="sxs-lookup"><span data-stu-id="02b44-169">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="02b44-170">Entwerfen Sie eine Teams-App mit Benutzeroberflächenkomponenten, Vorlagen und Beispielen, die Sie nach Bedarf ziehen, ablegen und ändern können.</span><span class="sxs-lookup"><span data-stu-id="02b44-170">Design a Teams app with UI components, templates, and examples that you can drag, drop, and modify as needed.</span></span> <span data-ttu-id="02b44-171">Das UI Kit enthält außerdem umfassende Informationen dazu, wie Apps in verschiedenen Teams-Szenarien aussehen und sich verhalten sollten.</span><span class="sxs-lookup"><span data-stu-id="02b44-171">The UI kit also includes comprehensive information about how apps should look and behave in different Teams scenarios.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="02b44-172">Benutzeroberflächenkit (Figma)</span><span class="sxs-lookup"><span data-stu-id="02b44-172">Get the UI kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

### <a name="microsoft-teams-ui-library"></a><span data-ttu-id="02b44-173">Benutzeroberflächenbibliothek von Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="02b44-173">Microsoft Teams UI Library</span></span>

<span data-ttu-id="02b44-174">Anzeigen und Testen einzelner Teams-UI-Vorlagen und zugehöriger Komponenten in Ihrem Browser.</span><span class="sxs-lookup"><span data-stu-id="02b44-174">View and test individual Teams UI templates and related components in your browser.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="02b44-175">Probieren Sie die Benutzeroberflächenbibliothek (Playground) aus.</span><span class="sxs-lookup"><span data-stu-id="02b44-175">Try the UI library (playground)</span></span>](https://dev-int.teams.microsoft.com/storybook/main/index.html)

<span data-ttu-id="02b44-176">Importieren Sie diese Vorlagen und zugehörigen Komponenten direkt in Ihr Teams-App-Projekt.</span><span class="sxs-lookup"><span data-stu-id="02b44-176">Import these templates and related components directly into your Teams app project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="02b44-177">Abrufen der Benutzeroberflächenbibliothek (GitHub)</span><span class="sxs-lookup"><span data-stu-id="02b44-177">Get the UI library (GitHub)</span></span>](https://github.com/OfficeDev/microsoft-teams-ui-component-library)

### <a name="sample-app"></a><span data-ttu-id="02b44-178">Beispiel-App</span><span class="sxs-lookup"><span data-stu-id="02b44-178">Sample app</span></span>

<span data-ttu-id="02b44-179">Installieren Sie eine Beispiel-App, um zu sehen, wie Benutzeroberflächenvorlagen in Teams-Kontexten aussehen und sich verhalten.</span><span class="sxs-lookup"><span data-stu-id="02b44-179">Install a sample app to see how UI templates look and behave within Teams contexts.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="02b44-180">Abrufen der Beispiel-App (GitHub)</span><span class="sxs-lookup"><span data-stu-id="02b44-180">Get the sample app (GitHub)</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-ui-templates/ts)

## <a name="other-resources"></a><span data-ttu-id="02b44-181">Sonstige Ressourcen</span><span class="sxs-lookup"><span data-stu-id="02b44-181">Other resources</span></span>

<span data-ttu-id="02b44-182">Weitere Informationen finden Sie in einer der folgenden Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="02b44-182">To learn more, try one of the following resources.</span></span>

### <a name="fluent-ui-documentation"></a><span data-ttu-id="02b44-183">Dokumentation zur Fluent-Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="02b44-183">Fluent UI documentation</span></span>

<span data-ttu-id="02b44-184">Hier finden Sie Codebeispiele und Implementierungsdetails für die Fluent UI-basierten Komponenten, die zum Erstellen von Teams-Erfahrungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="02b44-184">Get code samples and implementation details for the Fluent UI-based components used to build Teams experiences.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="02b44-185">Testen von Teams-UI-Komponenten (Fluent UI)</span><span class="sxs-lookup"><span data-stu-id="02b44-185">Try Teams UI components (Fluent UI)</span></span>](https://fluentsite.z22.web.core.windows.net/)

### <a name="adaptive-cards-designer"></a><span data-ttu-id="02b44-186">Designer für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="02b44-186">Adaptive Cards designer</span></span>

<span data-ttu-id="02b44-187">Entwerfen Sie adaptive Karten in unserem webbasierten Tool.</span><span class="sxs-lookup"><span data-stu-id="02b44-187">Design Adaptive Cards in our web-based tool.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="02b44-188">Testen des Designers für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="02b44-188">Try the Adaptive Cards designer</span></span>](https://adaptivecards.io/designer/)
