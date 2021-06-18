---
title: App-Entwurfsprozess
author: heath-hamilton
description: Erhalten Sie eine allgemeine Vorstellung davon, wie und wann Sie Microsoft-Tools und -Ressourcen verwenden können, um eine effektive Microsoft Teams-App zu entwerfen.
localization_priority: Normal
ms.author: surbhigupta
ms.topic: overview
ms.openlocfilehash: 225859da18cb50741ab49c68d89bc318c6c9034c
ms.sourcegitcommit: 14409950307b135265c8582408be5277b35131dd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2021
ms.locfileid: "52994210"
---
# <a name="design-process-for-microsoft-teams-apps"></a><span data-ttu-id="0e0e7-103">Entwurfsprozess für Microsoft Teams-Apps</span><span class="sxs-lookup"><span data-stu-id="0e0e7-103">Design process for Microsoft Teams apps</span></span>

<span data-ttu-id="0e0e7-104">Es gibt mehrere Tools und Ressourcen für das Entwerfen Ihrer Microsoft Teams-App.</span><span class="sxs-lookup"><span data-stu-id="0e0e7-104">There are multiple tools and resources for designing your Microsoft Teams app.</span></span> <span data-ttu-id="0e0e7-105">In den folgenden Schritten wird beschrieben, wann und wie Sie diese während des Entwurfsprozesses verwenden können.</span><span class="sxs-lookup"><span data-stu-id="0e0e7-105">The following steps describe when and how you might use these during the design process.</span></span> <span data-ttu-id="0e0e7-106">(Einige Schritte befinden sich möglicherweise außerhalb des Entwurfsprozesses, sind aber für zusätzlichen Kontext enthalten.)</span><span class="sxs-lookup"><span data-stu-id="0e0e7-106">(Some of steps might be technically outside the design process but are included for additional context.)</span></span>

:::image type="content" source="~/assets/images/design-guidelines/teams-app-design-process.png" alt-text="Diagramm mit einem Beispiel für den Teams App-Entwurfsprozess." border="false":::

## <a name="plan-your-app"></a><span data-ttu-id="0e0e7-108">Planen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="0e0e7-108">Plan your app</span></span>

<span data-ttu-id="0e0e7-109">Für das Entwerfen einer qualitativ hochwertigen Teams-App müssen Sie wissen, was die App tun soll und wie Sie davon aus gehen, dass Benutzer sie verwenden.</span><span class="sxs-lookup"><span data-stu-id="0e0e7-109">Designing a high-quality Teams app requires understanding what you want the app to do and how you think people will use it.</span></span> <span data-ttu-id="0e0e7-110">Bevor Sie mit dem Entwerfen beginnen, beantworten Sie jedoch die folgenden Fragen:</span><span class="sxs-lookup"><span data-stu-id="0e0e7-110">Before you start designing, however, answer the following questions:</span></span>

* <span data-ttu-id="0e0e7-111">Wer sind Ihre Benutzer?</span><span class="sxs-lookup"><span data-stu-id="0e0e7-111">Who are your users?</span></span>
* <span data-ttu-id="0e0e7-112">Was ist ihr Problem?</span><span class="sxs-lookup"><span data-stu-id="0e0e7-112">What’s their problem?</span></span>
* <span data-ttu-id="0e0e7-113">Wie kann Ihre App ihr Problem lösen?</span><span class="sxs-lookup"><span data-stu-id="0e0e7-113">How can your app solve their problem?</span></span>
* <span data-ttu-id="0e0e7-114">Wie oft wird Ihre App verwendet?</span><span class="sxs-lookup"><span data-stu-id="0e0e7-114">How often will your app be used?</span></span>
* <span data-ttu-id="0e0e7-115">Wie viele Personen verwenden Ihre App?</span><span class="sxs-lookup"><span data-stu-id="0e0e7-115">How many people will use your app?</span></span>
* <span data-ttu-id="0e0e7-116">Welche Art von Rendite kann Ihre App bereitstellen?</span><span class="sxs-lookup"><span data-stu-id="0e0e7-116">What kind of return on investment can your app provide?</span></span>

<span data-ttu-id="0e0e7-117">Weitere Informationen finden Sie unter [Verstehen der Anwendungsfälle Ihrer App](~/concepts/design/understand-use-cases.md) und [Zuordnen von Anwendungsfällen zu Teams.](~/concepts/design/map-use-cases.md)</span><span class="sxs-lookup"><span data-stu-id="0e0e7-117">For more information, see [understand your app’s use cases](~/concepts/design/understand-use-cases.md) and [map use cases to Teams](~/concepts/design/map-use-cases.md).</span></span>

## <a name="get-teams-design-tools"></a><span data-ttu-id="0e0e7-118">Abrufen Teams-Entwurfstools</span><span class="sxs-lookup"><span data-stu-id="0e0e7-118">Get Teams design tools</span></span>

<span data-ttu-id="0e0e7-119">Microsoft bietet Tools, die das Entwerfen Ihrer Teams-App vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="0e0e7-119">Microsoft provides tools to make it easier to design your Teams app.</span></span> <span data-ttu-id="0e0e7-120">Es wird dringend empfohlen, mindestens das Microsoft Teams UI Kit zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="0e0e7-120">At minimum, we strongly recommend using the Microsoft Teams UI Kit.</span></span>

### <a name="get-the-microsoft-teams-ui-kit"></a><span data-ttu-id="0e0e7-121">Abrufen des Microsoft Teams UI Kit</span><span class="sxs-lookup"><span data-stu-id="0e0e7-121">Get the Microsoft Teams UI Kit</span></span>

<span data-ttu-id="0e0e7-122">Das Microsoft Teams UI Kit kann Ihnen dabei helfen, in kürzester Zeit eine effektive Teams App zu entwickeln.</span><span class="sxs-lookup"><span data-stu-id="0e0e7-122">The Microsoft Teams UI Kit can help you develop an effective Teams app in the shortest amount of time.</span></span> <span data-ttu-id="0e0e7-123">Das UI-Kit enthält alles, was Sie in diesen Dokumenten im Zusammenhang mit Teams App-Design und vieles mehr sehen, einschließlich umfangreicher Beispiele und Variationen.</span><span class="sxs-lookup"><span data-stu-id="0e0e7-123">The UI kit has everything you see in these docs related to Teams app design and much more, including extensive examples and variations.</span></span>

<span data-ttu-id="0e0e7-124">Das UI-Kit verfügt auch über vordefinierte Vorlagen und Komponenten, die Sie bei Bedarf kopieren und ändern können, sodass Sie mehr Zeit mit dem Entwerfen der besten Benutzererfahrung verbringen können, anstatt sich Gedanken darüber zu machen, wie eine Schaltfläche aussehen sollte.</span><span class="sxs-lookup"><span data-stu-id="0e0e7-124">The UI kit also has pre-built templates and components that you can copy and modify as needed, so you can spend more time designing the best user experience instead worrying about what a button should look like.</span></span>

> [!TIP]
> <span data-ttu-id="0e0e7-125">**Ist das UI-Kit für mich geeignet?**</span><span class="sxs-lookup"><span data-stu-id="0e0e7-125">**Is the UI kit for me?**</span></span> <span data-ttu-id="0e0e7-126">Wenn Sie am Erstellen einer Teams App beteiligt sind, ja.</span><span class="sxs-lookup"><span data-stu-id="0e0e7-126">If you have any part in creating a Teams app, yes.</span></span> <span data-ttu-id="0e0e7-127">Das Erstellen einer Teams-App ist nicht nur für Designer hilfreich, sondern auch für Produktmanager, Entwickler, die IDEs verwenden, und Entwickler, die mit Tools mit wenig Code (z. B. microsoft Power Platform) erstellen.</span><span class="sxs-lookup"><span data-stu-id="0e0e7-127">Understanding how to craft a Teams app is not only helpful to designers but product managers, developers using IDEs, and makers building with low-code tools (such as the Microsoft Power Platform).</span></span>

1. <span data-ttu-id="0e0e7-128">Wechseln Sie zur [Seite Microsoft Teams UI Kit -Kits](https://www.figma.com/community/file/916836509871353159).</span><span class="sxs-lookup"><span data-stu-id="0e0e7-128">Go to the [Microsoft Teams UI Kit Figma page](https://www.figma.com/community/file/916836509871353159).</span></span>
1. <span data-ttu-id="0e0e7-129">Wählen Sie **"Duplizieren"** aus, um das UI-Kit zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="0e0e7-129">Select **Duplicate** to open the UI kit.</span></span> <span data-ttu-id="0e0e7-130">(Möglicherweise müssen Sie zuerst ein Numma-Konto erstellen.)</span><span class="sxs-lookup"><span data-stu-id="0e0e7-130">(You may have to first create a Figma account.)</span></span>

### <a name="try-the-sample-app"></a><span data-ttu-id="0e0e7-131">Probieren Sie die Beispiel-App aus</span><span class="sxs-lookup"><span data-stu-id="0e0e7-131">Try the sample app</span></span>

<span data-ttu-id="0e0e7-132">Sie können eine Beispiel-App hochladen, um zu sehen, wie Apps im Teams-Client aussehen und sich verhalten sollen.</span><span class="sxs-lookup"><span data-stu-id="0e0e7-132">You can upload a sample app to see how apps should look and behave in the Teams client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0e0e7-133">Abrufen der Beispiel-App (GitHub)</span><span class="sxs-lookup"><span data-stu-id="0e0e7-133">Get the sample app (GitHub)</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-ui-templates/ts)

## <a name="learn-teams-design-system"></a><span data-ttu-id="0e0e7-134">Informationen zum Teams-Entwurfssystem</span><span class="sxs-lookup"><span data-stu-id="0e0e7-134">Learn Teams design system</span></span>

<span data-ttu-id="0e0e7-135">Informieren Sie sich ausführlich über die [Grundlagen Teams App-Designs,](design-teams-app-fundamentals.md)einschließlich Layout, Farbschemas und mehr, oder machen Sie sich mit ihnen vertraut.</span><span class="sxs-lookup"><span data-stu-id="0e0e7-135">Read in depth about or at least familiarize yourself with the [fundamentals of Teams app design](design-teams-app-fundamentals.md), including layout, color schemes, and more.</span></span>

## <a name="choose-app-capabilities"></a><span data-ttu-id="0e0e7-136">Auswählen von App-Funktionen</span><span class="sxs-lookup"><span data-stu-id="0e0e7-136">Choose app capabilities</span></span>

<span data-ttu-id="0e0e7-137">Nach der Planungsphase können Sie ermitteln, welche Teams Funktionen zu den Anwendungsfällen Ihrer App passen.</span><span class="sxs-lookup"><span data-stu-id="0e0e7-137">After the planning phase, you can determine which Teams capabilities fit your app’s use cases.</span></span> <span data-ttu-id="0e0e7-138">Wenn Sie z. B. proaktiv Personen benachrichtigen möchten, ist ein Bot möglicherweise die richtige Funktion.</span><span class="sxs-lookup"><span data-stu-id="0e0e7-138">For example, if you want to proactively notify people, a bot might be the right capability.</span></span>

<span data-ttu-id="0e0e7-139">Das UI-Kit verfügt über vordefinierte Designs, die ihnen zeigen, wie Benutzer in der Regel jede Funktion hinzufügen, einrichten, verwenden und verwalten.</span><span class="sxs-lookup"><span data-stu-id="0e0e7-139">The UI kit has pre built designs that show you how people typically add, set up, use, and manage each capability.</span></span> <span data-ttu-id="0e0e7-140">Als Kurzübersicht finden Sie diese Informationen auch in diesen Dokumenten, aber mit dem UI-Kit können Sie eines dieser Designs kopieren und in das Design Ihrer App einfügen.</span><span class="sxs-lookup"><span data-stu-id="0e0e7-140">For quick reference, this information is also in these docs, but with the UI kit you can copy and paste any of these designs into your app’s design.</span></span>

1. <span data-ttu-id="0e0e7-141">Wechseln Sie im linken Navigationsbereich des UI-Kits zu den **App-Funktionen,** und wählen Sie die gewünschte Funktion für Ihre App aus.</span><span class="sxs-lookup"><span data-stu-id="0e0e7-141">In the UI kit’s left nav, go to **App capabilities** and select the capability you want for your app.</span></span>
1. <span data-ttu-id="0e0e7-142">Kopieren Sie das, was Sie von dieser Seite benötigen, um Ihre App zu entwerfen.</span><span class="sxs-lookup"><span data-stu-id="0e0e7-142">Copy what you need from that page to design your app.</span></span><br />
   <span data-ttu-id="0e0e7-143">Wenn Ihre App beispielsweise die Authentifizierung mit einmaligem Anmelden unterstützt, kopieren Sie das Design, und fügen Sie es ein, um dieses genaue Szenario zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="0e0e7-143">For example, if your app supports authentication with single sign-on, copy and paste the design for handling that exact scenario.</span></span>

## <a name="design-your-ux-flow"></a><span data-ttu-id="0e0e7-144">Entwerfen des UX-Flusses</span><span class="sxs-lookup"><span data-stu-id="0e0e7-144">Design your UX flow</span></span>

<span data-ttu-id="0e0e7-145">Sobald Sie über ein einfaches App-Design verfügen, können Sie es beliebig ändern und verfeinern, indem Sie Teams UI-Vorlagen und grundlegende Komponenten aus dem UI-Kit kopieren.</span><span class="sxs-lookup"><span data-stu-id="0e0e7-145">Once you have a basic app design, you can modify and refine it as much as you want by copying Teams UI templates and basic components from the UI kit.</span></span>

### <a name="design-with-ui-templates"></a><span data-ttu-id="0e0e7-146">Entwerfen mit Benutzeroberflächenvorlagen</span><span class="sxs-lookup"><span data-stu-id="0e0e7-146">Design with UI templates</span></span>

<span data-ttu-id="0e0e7-147">Benutzeroberflächenvorlagen sind komplexe, präzise Designs für gängige Teams Anwendungsfälle und Workflows.</span><span class="sxs-lookup"><span data-stu-id="0e0e7-147">UI templates are complex, high-fidelity designs for common Teams use cases and workflows.</span></span> <span data-ttu-id="0e0e7-148">Anstatt von unten nach oben mit grundlegenden Komponenten zu beginnen, empfehlen wir, diese Vorlagen zu verwenden, um den Entwurfsprozess zu vereinfachen und zu beschleunigen.</span><span class="sxs-lookup"><span data-stu-id="0e0e7-148">Instead of starting from the bottom up with basic components, we recommend you use these templates to simplify and speed up the design process.</span></span>

1. <span data-ttu-id="0e0e7-149">Wechseln Sie im linken Navigationsbereich des UI-Kits zu **UI-Vorlagen.**</span><span class="sxs-lookup"><span data-stu-id="0e0e7-149">In the UI kit’s left nav, go to **UI templates**.</span></span>
1. <span data-ttu-id="0e0e7-150">Kopieren Sie Vorlagen, die für Ihr App-Design sinnvoll sind.</span><span class="sxs-lookup"><span data-stu-id="0e0e7-150">Copy templates that make sense for your app design.</span></span><br />
   <span data-ttu-id="0e0e7-151">Wenn Sie beispielsweise eine persönliche App entwerfen, sollten Sie eine Dashboardvorlage verwenden.</span><span class="sxs-lookup"><span data-stu-id="0e0e7-151">For example, if you’re designing a personal app, you may want to use a Dashboard template.</span></span>

### <a name="design-with-basic-ui-components"></a><span data-ttu-id="0e0e7-152">Design mit einfachen UI-Komponenten</span><span class="sxs-lookup"><span data-stu-id="0e0e7-152">Design with basic UI components</span></span>

<span data-ttu-id="0e0e7-153">Basierend auf Fluent Ui sind dies die Kernelemente zum Erstellen vertrauter Teams-Schnittstellen.</span><span class="sxs-lookup"><span data-stu-id="0e0e7-153">Based on Fluent UI, these are the core elements for creating familiar Teams interfaces.</span></span> <span data-ttu-id="0e0e7-154">Verwenden Sie diese Komponenten, wenn eine UI-Vorlage etwas fehlt, das Sie benötigen, oder Sie Ihre App einfach von Grund auf neu entwerfen möchten.</span><span class="sxs-lookup"><span data-stu-id="0e0e7-154">Use these components if a UI template is missing something you need or you just want to design your app from scratch.</span></span>

1. <span data-ttu-id="0e0e7-155">Wechseln Sie im linken Navigationsbereich des UI-Kits zu **grundlegenden UI-Komponenten.**</span><span class="sxs-lookup"><span data-stu-id="0e0e7-155">In the UI kit’s left nav, go to **Basic UI components**.</span></span>
1. <span data-ttu-id="0e0e7-156">Kopieren Sie die Komponenten, die Sie für Ihr App-Design benötigen (z. B. eine Schaltfläche oder einen Umschalter).</span><span class="sxs-lookup"><span data-stu-id="0e0e7-156">Copy the components you need for your app design (for example, a button or toggle).</span></span>

## <a name="implement-your-design"></a><span data-ttu-id="0e0e7-157">Implementieren Ihres Designs</span><span class="sxs-lookup"><span data-stu-id="0e0e7-157">Implement your design</span></span>

<span data-ttu-id="0e0e7-158">Das Design ist fertig, und Sie können mit dem Erstellen beginnen.</span><span class="sxs-lookup"><span data-stu-id="0e0e7-158">The design is done and you’re ready to start building.</span></span> <span data-ttu-id="0e0e7-159">Die folgenden Tools können ihnen helfen, die Front-End-Entwicklung Ihrer App zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="0e0e7-159">The following tools can help simplify the front-end development of your app.</span></span>

### <a name="build-with-ui-templates"></a><span data-ttu-id="0e0e7-160">Erstellen mit Benutzeroberflächenvorlagen</span><span class="sxs-lookup"><span data-stu-id="0e0e7-160">Build with UI templates</span></span>

<span data-ttu-id="0e0e7-161">Wenn Sie benutzeroberflächenvorlagen in Ihrem Entwurf verwendet haben, können Sie diese Vorlagen mit der Microsoft Teams Benutzeroberflächenbibliothek (einer React-Komponentenbibliothek basierend auf Fluent Benutzeroberfläche) implementieren.</span><span class="sxs-lookup"><span data-stu-id="0e0e7-161">If you used UI templates in your design, you can implement these templates with the Microsoft Teams UI Library (a React component library based on Fluent UI).</span></span>

<span data-ttu-id="0e0e7-162">Derzeit sind nicht alle im UI-Kit aufgeführten Vorlagen in der Bibliothek verfügbar.</span><span class="sxs-lookup"><span data-stu-id="0e0e7-162">Currently, not all templates listed in the UI kit are available in the library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0e0e7-163">Abrufen der Bibliothek (GitHub)</span><span class="sxs-lookup"><span data-stu-id="0e0e7-163">Get the library (GitHub)</span></span>](https://github.com/OfficeDev/microsoft-teams-ui-component-library)

### <a name="build-with-basic-ui-components"></a><span data-ttu-id="0e0e7-164">Erstellen mit einfachen UI-Komponenten</span><span class="sxs-lookup"><span data-stu-id="0e0e7-164">Build with basic UI components</span></span>

<span data-ttu-id="0e0e7-165">Nicht anders als in der Entwurfsphase können Sie diese Fluent UI-Komponenten in Ihrem App-Projekt verwenden, wenn eine Benutzeroberflächenvorlage etwas fehlt, das Sie benötigen, oder Sie die App einfach von Grund auf neu erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="0e0e7-165">Not unlike the design phase, you can use these Fluent UI components in your app project if a UI template is missing something you need, or you just want to build the app from scratch.</span></span> 

<span data-ttu-id="0e0e7-166">(Hinweis: Wenn Sie etwas fehlendes bemerken oder eine Idee für eine Vorlage haben, sollten Sie einen Beitrag zum Repository der Teams UI-Bibliothek leisten.)</span><span class="sxs-lookup"><span data-stu-id="0e0e7-166">(Note: If you notice something missing or have an idea for a template, consider contributing to the Teams UI Library repo.)</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0e0e7-167">Abrufen der Bibliothek (Fluent Benutzeroberfläche)</span><span class="sxs-lookup"><span data-stu-id="0e0e7-167">Get the library (Fluent UI)</span></span>](https://fluentsite.z22.web.core.windows.net/)

## <a name="review-design-resources"></a><span data-ttu-id="0e0e7-168">Überprüfen von Designressourcen</span><span class="sxs-lookup"><span data-stu-id="0e0e7-168">Review design resources</span></span>

<span data-ttu-id="0e0e7-169">Unabhängig davon, ob Sie gerade mit Ihrer App beginnen oder sich in der Nähe einer produktionsbereiten App befinden, empfehlen wir Ihnen, die folgenden Ressourcen regelmäßig zu überprüfen:</span><span class="sxs-lookup"><span data-stu-id="0e0e7-169">Whether you’re just starting on your app or close to a production-ready app, we recommend that you periodically review the following resources:</span></span>

* <span data-ttu-id="0e0e7-170">Microsoft Teams Richtlinien für die **Store-Validierung:** Bietet Standards, nach denen alle Teams Apps suchen sollten, und nicht nur apps, die im Store aufgeführt sind.</span><span class="sxs-lookup"><span data-stu-id="0e0e7-170">**Microsoft Teams store validation guidelines**: Provides standards that all Teams apps should strive for, and not just apps listed in the store.</span></span> <span data-ttu-id="0e0e7-171">Weitere Informationen finden Sie in den [Richtlinien.](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md)</span><span class="sxs-lookup"><span data-stu-id="0e0e7-171">For more information, see the [guidelines](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md).</span></span>
* <span data-ttu-id="0e0e7-172">Bewährte Methoden für das **Entwerfen:** Diese Dokumente und das UI-Kit bieten bewährte Methoden für das Entwerfen von qualitativ hochwertigen Apps.</span><span class="sxs-lookup"><span data-stu-id="0e0e7-172">**Design best practices**: These docs and the UI kit provide best practices for designing high-quality apps.</span></span> <span data-ttu-id="0e0e7-173">Sehen Sie sich beispielsweise die bewährten Methoden für das [Entwerfen von Bots an.](~/bots/design/bots.md#best-practices)</span><span class="sxs-lookup"><span data-stu-id="0e0e7-173">For example, see the [best practices for designing bots](~/bots/design/bots.md#best-practices).</span></span>

