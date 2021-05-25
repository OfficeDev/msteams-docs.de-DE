---
title: App-Entwurfsprozess
author: heath-hamilton
description: Erhalten Sie eine allgemeine Vorstellung davon, wie und wann Sie Microsoft-Tools und -Ressourcen verwenden können, um eine effektive Microsoft Teams entwerfen.
localization_priority: Normal
ms.author: surbhigupta
ms.topic: overview
ms.openlocfilehash: 533d386db2aa784fc7de955f92f64d07789f0553
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "52631307"
---
# <a name="design-process-for-microsoft-teams-apps"></a><span data-ttu-id="104d3-103">Entwurfsprozess für Microsoft Teams Apps</span><span class="sxs-lookup"><span data-stu-id="104d3-103">Design process for Microsoft Teams apps</span></span>

<span data-ttu-id="104d3-104">Es gibt mehrere Tools und Ressourcen zum Entwerfen Ihrer Microsoft Teams App.</span><span class="sxs-lookup"><span data-stu-id="104d3-104">There are multiple tools and resources for designing your Microsoft Teams app.</span></span> <span data-ttu-id="104d3-105">In den folgenden Schritten wird beschrieben, wann und wie Sie diese während des Entwurfs verwenden können.</span><span class="sxs-lookup"><span data-stu-id="104d3-105">The following steps describe when and how you might use these during the design process.</span></span> <span data-ttu-id="104d3-106">(Einige der Schritte können technisch außerhalb des Entwurfsprozesses liegen, sind jedoch für zusätzlichen Kontext enthalten.)</span><span class="sxs-lookup"><span data-stu-id="104d3-106">(Some of steps might be technically outside the design process but are included for additional context.)</span></span>

:::image type="content" source="~/assets/images/design-guidelines/teams-app-design-process.png" alt-text="Diagramm, das ein Beispiel für den Teams-App-Entwurfsprozesses zeigt." border="false":::

## <a name="plan-your-app"></a><span data-ttu-id="104d3-108">Planen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="104d3-108">Plan your app</span></span>

<span data-ttu-id="104d3-109">Das Entwerfen einer qualitativ hochwertigen Teams erfordert, dass Sie verstehen, was die App tun soll und wie Sie denken, dass die App von den Personen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="104d3-109">Designing a high-quality Teams app requires understanding what you want the app to do and how you think people will use it.</span></span> <span data-ttu-id="104d3-110">Bevor Sie mit dem Entwerfen beginnen, beantworten Sie jedoch die folgenden Fragen:</span><span class="sxs-lookup"><span data-stu-id="104d3-110">Before you start designing, however, answer the following questions:</span></span>

* <span data-ttu-id="104d3-111">Wer sind Ihre Benutzer?</span><span class="sxs-lookup"><span data-stu-id="104d3-111">Who are your users?</span></span>
* <span data-ttu-id="104d3-112">Was ist ihr Problem?</span><span class="sxs-lookup"><span data-stu-id="104d3-112">What’s their problem?</span></span>
* <span data-ttu-id="104d3-113">Wie kann Ihre App ihr Problem lösen?</span><span class="sxs-lookup"><span data-stu-id="104d3-113">How can your app solve their problem?</span></span>
* <span data-ttu-id="104d3-114">Wie oft wird Ihre App verwendet?</span><span class="sxs-lookup"><span data-stu-id="104d3-114">How often will your app be used?</span></span>
* <span data-ttu-id="104d3-115">Wie viele Personen verwenden Ihre App?</span><span class="sxs-lookup"><span data-stu-id="104d3-115">How many people will use your app?</span></span>
* <span data-ttu-id="104d3-116">Welche Art von Rendite kann Ihre App bieten?</span><span class="sxs-lookup"><span data-stu-id="104d3-116">What kind of return on investment can your app provide?</span></span>

<span data-ttu-id="104d3-117">Weitere Informationen finden Sie unter [Verstehen der Anwendungsfälle](~/concepts/design/understand-use-cases.md) Ihrer App und [Zuordnung](~/concepts/design/map-use-cases.md)von Anwendungsfällen zu Teams .</span><span class="sxs-lookup"><span data-stu-id="104d3-117">For more information, see [understand your app’s use cases](~/concepts/design/understand-use-cases.md) and [map use cases to Teams](~/concepts/design/map-use-cases.md).</span></span>

## <a name="get-teams-design-tools"></a><span data-ttu-id="104d3-118">Get Teams design tools</span><span class="sxs-lookup"><span data-stu-id="104d3-118">Get Teams design tools</span></span>

<span data-ttu-id="104d3-119">Microsoft stellt Tools bereit, mit deren Unterstützung Das Entwerfen Ihrer Teams erleichtert wird.</span><span class="sxs-lookup"><span data-stu-id="104d3-119">Microsoft provides tools to make it easier to design your Teams app.</span></span> <span data-ttu-id="104d3-120">Es wird dringend empfohlen, das Microsoft Teams UI Kit zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="104d3-120">At minimum, we strongly recommend using the Microsoft Teams UI Kit.</span></span>

### <a name="get-the-microsoft-teams-ui-kit"></a><span data-ttu-id="104d3-121">Get the Microsoft Teams UI Kit</span><span class="sxs-lookup"><span data-stu-id="104d3-121">Get the Microsoft Teams UI Kit</span></span>

<span data-ttu-id="104d3-122">Das Microsoft Teams UI Kit hilft Ihnen, eine effektive Teams app in kürzester Zeit zu entwickeln.</span><span class="sxs-lookup"><span data-stu-id="104d3-122">The Microsoft Teams UI Kit can help you develop an effective Teams app in the shortest amount of time.</span></span> <span data-ttu-id="104d3-123">Das Benutzeroberflächenkit enthält alles, was sie in diesen Dokumenten im Zusammenhang mit Teams App-Design und vielem mehr sehen, einschließlich umfangreicher Beispiele und Variationen.</span><span class="sxs-lookup"><span data-stu-id="104d3-123">The UI kit has everything you see in these docs related to Teams app design and much more, including extensive examples and variations.</span></span>

<span data-ttu-id="104d3-124">Das Benutzeroberflächenkit verfügt auch über vordefinierte Vorlagen und Komponenten, die Sie nach Bedarf kopieren und ändern können, sodass Sie mehr Zeit mit dem Entwerfen der besten Benutzeroberfläche verbringen können, anstatt sich Gedanken darüber zu machen, wie eine Schaltfläche aussehen soll.</span><span class="sxs-lookup"><span data-stu-id="104d3-124">The UI kit also has pre-built templates and components that you can copy and modify as needed, so you can spend more time designing the best user experience instead worrying about what a button should look like.</span></span>

> [!TIP]
> <span data-ttu-id="104d3-125">**Ist das Benutzeroberflächenkit für mich?**</span><span class="sxs-lookup"><span data-stu-id="104d3-125">**Is the UI kit for me?**</span></span> <span data-ttu-id="104d3-126">Wenn Sie eine Rolle beim Erstellen einer Teams haben, ja.</span><span class="sxs-lookup"><span data-stu-id="104d3-126">If you have any part in creating a Teams app, yes.</span></span> <span data-ttu-id="104d3-127">Das Erstellen einer Teams-App ist nicht nur designern, sondern auch Produktmanagern, Entwicklern, die IDEs verwenden, und Entwicklern, die mit Low-Code-Tools (z. B. der Microsoft Power Platform) erstellen, hilfreich.</span><span class="sxs-lookup"><span data-stu-id="104d3-127">Understanding how to craft a Teams app is not only helpful to designers but product managers, developers using IDEs, and makers building with low-code tools (such as the Microsoft Power Platform).</span></span>

1. <span data-ttu-id="104d3-128">Wechseln Sie zur [seite Microsoft Teams UI Kit Figma](https://www.figma.com/community/file/916836509871353159).</span><span class="sxs-lookup"><span data-stu-id="104d3-128">Go to the [Microsoft Teams UI Kit Figma page](https://www.figma.com/community/file/916836509871353159).</span></span>
1. <span data-ttu-id="104d3-129">Wählen **Sie Duplizieren** aus, um das Ui Kit zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="104d3-129">Select **Duplicate** to open the UI kit.</span></span> <span data-ttu-id="104d3-130">(Möglicherweise müssen Sie zuerst ein Feigenma-Konto erstellen.)</span><span class="sxs-lookup"><span data-stu-id="104d3-130">(You may have to first create a Figma account.)</span></span>

### <a name="try-the-sample-app"></a><span data-ttu-id="104d3-131">Testen der Beispiel-App</span><span class="sxs-lookup"><span data-stu-id="104d3-131">Try the sample app</span></span>

<span data-ttu-id="104d3-132">Sie können eine Beispiel-App hochladen, um zu sehen, wie Apps im Client aussehen und sich Teams verhalten sollen.</span><span class="sxs-lookup"><span data-stu-id="104d3-132">You can upload a sample app to see how apps should look and behave in the Teams client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="104d3-133">Die Beispiel-App (GitHub)</span><span class="sxs-lookup"><span data-stu-id="104d3-133">Get the sample app (GitHub)</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-ui-templates/ts)

## <a name="learn-teams-design-system"></a><span data-ttu-id="104d3-134">Informationen Teams Entwurfssystem</span><span class="sxs-lookup"><span data-stu-id="104d3-134">Learn Teams design system</span></span>

<span data-ttu-id="104d3-135">Erfahren Sie mehr über die Grundlagen des Teams, einschließlich Layout, Farbschemas und [vielem](design-teams-app-fundamentals.md)mehr, oder machen Sie sich zumindest mit den Grundlagen des App-Designs vertraut.</span><span class="sxs-lookup"><span data-stu-id="104d3-135">Read in depth about or at least familiarize yourself with the [fundamentals of Teams app design](design-teams-app-fundamentals.md), including layout, color schemes, and more.</span></span>

## <a name="choose-app-capabilities"></a><span data-ttu-id="104d3-136">Auswählen von App-Funktionen</span><span class="sxs-lookup"><span data-stu-id="104d3-136">Choose app capabilities</span></span>

<span data-ttu-id="104d3-137">Nach der Planungsphase können Sie bestimmen, welche Teams den Anwendungsfällen Ihrer App passen.</span><span class="sxs-lookup"><span data-stu-id="104d3-137">After the planning phase, you can determine which Teams capabilities fit your app’s use cases.</span></span> <span data-ttu-id="104d3-138">Wenn Sie z. B. Personen proaktiv benachrichtigen möchten, ist möglicherweise ein Bot die richtige Funktion.</span><span class="sxs-lookup"><span data-stu-id="104d3-138">For example, if you want to proactively notify people, a bot might be the right capability.</span></span>

<span data-ttu-id="104d3-139">Das Benutzeroberflächenkit verfügt über vordefinierte Designs, die Ihnen zeigen, wie Benutzer in der Regel jede Funktion hinzufügen, einrichten, verwenden und verwalten.</span><span class="sxs-lookup"><span data-stu-id="104d3-139">The UI kit has pre-built designs that show you how people typically add, set up, use, and manage each capability.</span></span> <span data-ttu-id="104d3-140">Kurzübersicht: Diese Informationen finden Sie auch in diesen Dokumenten. Mit dem UI Kit können Sie jedoch alle diese Designs kopieren und in das Design Ihrer App einfügen.</span><span class="sxs-lookup"><span data-stu-id="104d3-140">For quick reference, this information is also in these docs, but with the UI kit you can copy and paste any of these designs into your app’s design.</span></span>

1. <span data-ttu-id="104d3-141">Wechseln Sie im linken Navigationselement  des Benutzeroberflächenkits zu App-Funktionen, und wählen Sie die funktion aus, die Sie für Ihre App wünschen.</span><span class="sxs-lookup"><span data-stu-id="104d3-141">In the UI kit’s left nav, go to **App capabilities** and select the capability you want for your app.</span></span>
1. <span data-ttu-id="104d3-142">Kopieren Sie die benötigten Informationen von dieser Seite, um Ihre App zu entwerfen.</span><span class="sxs-lookup"><span data-stu-id="104d3-142">Copy what you need from that page to design your app.</span></span><br />
   <span data-ttu-id="104d3-143">Wenn Ihre App beispielsweise die Authentifizierung mit einmaligem Anmelden unterstützt, kopieren Und fügen Sie den Entwurf für die Verarbeitung dieses genauen Szenarios ein.</span><span class="sxs-lookup"><span data-stu-id="104d3-143">For example, if your app supports authentication with single sign-on, copy and paste the design for handling that exact scenario.</span></span>

## <a name="design-your-ux-flow"></a><span data-ttu-id="104d3-144">Entwerfen des UX-Fluss</span><span class="sxs-lookup"><span data-stu-id="104d3-144">Design your UX flow</span></span>

<span data-ttu-id="104d3-145">Sobald Sie über ein einfaches App-Design verfügen, können Sie es so weit wie möglich (und schnell) ändern und verfeinern, indem Sie Teams Benutzeroberflächenvorlagen und grundlegende Komponenten aus dem UI Kit kopieren.</span><span class="sxs-lookup"><span data-stu-id="104d3-145">Once you have a basic app design, you can modify and refine it as much as you want (and quickly) by copying Teams UI templates and basic components from the UI kit.</span></span>

### <a name="design-with-ui-templates"></a><span data-ttu-id="104d3-146">Entwerfen mit Benutzeroberflächenvorlagen</span><span class="sxs-lookup"><span data-stu-id="104d3-146">Design with UI templates</span></span>

<span data-ttu-id="104d3-147">Ui templates are complex, high-fidelity designs for common Teams use cases and workflows.</span><span class="sxs-lookup"><span data-stu-id="104d3-147">UI templates are complex, high-fidelity designs for common Teams use cases and workflows.</span></span> <span data-ttu-id="104d3-148">Anstatt von unten nach oben mit grundlegenden Komponenten zu beginnen, empfehlen wir, diese Vorlagen zu verwenden, um den Entwurfsprozess zu vereinfachen und zu beschleunigen.</span><span class="sxs-lookup"><span data-stu-id="104d3-148">Instead of starting from the bottom up with basic components, we recommend you use these templates to simplify and speed up the design process.</span></span>

1. <span data-ttu-id="104d3-149">Wechseln Sie im linken Navigationselement des Benutzeroberflächenkits zu **UI-Vorlagen**.</span><span class="sxs-lookup"><span data-stu-id="104d3-149">In the UI kit’s left nav, go to **UI templates**.</span></span>
1. <span data-ttu-id="104d3-150">Kopieren Sie Vorlagen, die für Ihr App-Design sinnvoll sind.</span><span class="sxs-lookup"><span data-stu-id="104d3-150">Copy templates that make sense for your app design.</span></span><br />
   <span data-ttu-id="104d3-151">Wenn Sie beispielsweise eine persönliche App entwerfen, sollten Sie eine Dashboardvorlage verwenden.</span><span class="sxs-lookup"><span data-stu-id="104d3-151">For example, if you’re designing a personal app, you may want to use a Dashboard template.</span></span>

### <a name="design-with-basic-ui-components"></a><span data-ttu-id="104d3-152">Entwurf mit einfachen Benutzeroberflächenkomponenten</span><span class="sxs-lookup"><span data-stu-id="104d3-152">Design with basic UI components</span></span>

<span data-ttu-id="104d3-153">Basierend auf der Fluent-Benutzeroberfläche sind dies die Kernelemente zum Erstellen vertrauter Teams Schnittstellen.</span><span class="sxs-lookup"><span data-stu-id="104d3-153">Based on Fluent UI, these are the core elements for creating familiar Teams interfaces.</span></span> <span data-ttu-id="104d3-154">Verwenden Sie diese Komponenten, wenn einer Benutzeroberflächenvorlage etwas fehlt, das Sie benötigen, oder Wenn Sie Ihre App einfach neu entwerfen möchten.</span><span class="sxs-lookup"><span data-stu-id="104d3-154">Use these components if a UI template is missing something you need or you just want to design your app from scratch.</span></span>

1. <span data-ttu-id="104d3-155">Wechseln Sie im linken Navigationselement des Benutzeroberflächenkits zu **Grundlegende Benutzeroberflächenkomponenten**.</span><span class="sxs-lookup"><span data-stu-id="104d3-155">In the UI kit’s left nav, go to **Basic UI components**.</span></span>
1. <span data-ttu-id="104d3-156">Kopieren Sie die Komponenten, die Sie für Ihr App-Design benötigen (z. B. eine Schaltfläche oder umschalten).</span><span class="sxs-lookup"><span data-stu-id="104d3-156">Copy the components you need for your app design (for example, a button or toggle).</span></span>

## <a name="implement-your-design"></a><span data-ttu-id="104d3-157">Implementieren Des Entwurfs</span><span class="sxs-lookup"><span data-stu-id="104d3-157">Implement your design</span></span>

<span data-ttu-id="104d3-158">Das Design ist fertig, und Sie können mit dem Erstellen beginnen.</span><span class="sxs-lookup"><span data-stu-id="104d3-158">The design is done and you’re ready to start building.</span></span> <span data-ttu-id="104d3-159">Die folgenden Tools können die Front-End-Entwicklung Ihrer App vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="104d3-159">The following tools can help simplify the front-end development of your app.</span></span>

### <a name="build-with-ui-templates"></a><span data-ttu-id="104d3-160">Erstellen mit Benutzeroberflächenvorlagen</span><span class="sxs-lookup"><span data-stu-id="104d3-160">Build with UI templates</span></span>

<span data-ttu-id="104d3-161">Wenn Sie benutzeroberflächenvorlagen in Ihrem Entwurf verwendet haben, können Sie diese Vorlagen mit der Microsoft Teams-Benutzeroberflächenbibliothek (eine React-Komponentenbibliothek basierend auf der Fluent-Benutzeroberfläche) implementieren.</span><span class="sxs-lookup"><span data-stu-id="104d3-161">If you used UI templates in your design, you can implement these templates with the Microsoft Teams UI Library (a React component library based on Fluent UI).</span></span>

<span data-ttu-id="104d3-162">Derzeit sind nicht alle im UI Kit aufgeführten Vorlagen in der Bibliothek verfügbar.</span><span class="sxs-lookup"><span data-stu-id="104d3-162">Currently, not all templates listed in the UI kit are available in the library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="104d3-163">Bibliothek (GitHub)</span><span class="sxs-lookup"><span data-stu-id="104d3-163">Get the library (GitHub)</span></span>](https://github.com/OfficeDev/microsoft-teams-ui-component-library)

### <a name="build-with-basic-ui-components"></a><span data-ttu-id="104d3-164">Erstellen mit grundlegenden Benutzeroberflächenkomponenten</span><span class="sxs-lookup"><span data-stu-id="104d3-164">Build with basic UI components</span></span>

<span data-ttu-id="104d3-165">Im Gegensatz zur Entwurfsphase können Sie diese Fluent-UI-Komponenten in Ihrem App-Projekt verwenden, wenn eine Benutzeroberflächenvorlage fehlt oder Sie die App einfach von Grund auf neu erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="104d3-165">Not unlike the design phase, you can use these Fluent UI components in your app project if a UI template is missing something you need, or you just want to build the app from scratch.</span></span> 

<span data-ttu-id="104d3-166">(Hinweis: Wenn Sie bemerken, dass etwas fehlt oder sie eine Idee für eine Vorlage haben, sollten Sie einen Beitrag zum Repository Teams Ui Library leisten.)</span><span class="sxs-lookup"><span data-stu-id="104d3-166">(Note: If you notice something missing or have an idea for a template, consider contributing to the Teams UI Library repo.)</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="104d3-167">Bibliothek erhalten (Fluent UI)</span><span class="sxs-lookup"><span data-stu-id="104d3-167">Get the library (Fluent UI)</span></span>](https://fluentsite.z22.web.core.windows.net/)

## <a name="review-design-resources"></a><span data-ttu-id="104d3-168">Überprüfen von Entwurfsressourcen</span><span class="sxs-lookup"><span data-stu-id="104d3-168">Review design resources</span></span>

<span data-ttu-id="104d3-169">Unabhängig davon, ob Sie gerade mit Ihrer App beginnen oder in der Nähe einer produktionsbereiten App sind, wird empfohlen, die folgenden Ressourcen regelmäßig zu überprüfen:</span><span class="sxs-lookup"><span data-stu-id="104d3-169">Whether you’re just starting on your app or close to a production-ready app, we recommend that you periodically review the following resources:</span></span>

* <span data-ttu-id="104d3-170">**Microsoft Teams Richtlinien für die** Storeüberprüfung: Stellt Standards zur Verfügung, die alle Teams apps anstreben sollten (nicht nur Apps, die im Store aufgeführt sind).</span><span class="sxs-lookup"><span data-stu-id="104d3-170">**Microsoft Teams store validation guidelines**: Provides standards that all Teams apps should strive for (not just apps listed in the store).</span></span> <span data-ttu-id="104d3-171">Weitere Informationen finden Sie in den [Richtlinien](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="104d3-171">For more information, see the [guidelines](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md).</span></span>
* <span data-ttu-id="104d3-172">**Bewährte Entwurfsmethoden:** Diese Dokumente und das UI Kit bieten bewährte Methoden für das Entwerfen qualitativ hochwertiger Apps.</span><span class="sxs-lookup"><span data-stu-id="104d3-172">**Design best practices**: These docs and the UI kit provide best practices for designing high-quality apps.</span></span> <span data-ttu-id="104d3-173">Lesen Sie beispielsweise die [bewährten Methoden für das Entwerfen von Bots](~/bots/design/bots.md#best-practices).</span><span class="sxs-lookup"><span data-stu-id="104d3-173">For example, see the [best practices for designing bots](~/bots/design/bots.md#best-practices).</span></span>
