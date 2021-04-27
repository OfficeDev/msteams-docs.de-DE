---
title: Integrieren von Web-Apps
author: Rajeshwari-v
description: Eine Übersicht über die Integration von Webanwendungen und Gerätefunktionen in die Microsoft Teams-App.
ms.topic: conceptual
ms.author: surbhigupta
ms.openlocfilehash: 6493f493b2bfc67a23aebfb5142aff60cf0afe93
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020242"
---
# <a name="integrate-web-apps"></a><span data-ttu-id="28be5-103">Integrieren von Web-Apps</span><span class="sxs-lookup"><span data-stu-id="28be5-103">Integrate web apps</span></span>

<span data-ttu-id="28be5-104">Sie können eine bereicherte Benutzererfahrung bereitstellen, indem Sie die Features einer vorhandenen Webanwendung in die Microsoft Teams-Plattform integrieren.</span><span class="sxs-lookup"><span data-stu-id="28be5-104">You can provide an enriched user experience by integrating the features of an existing web application into Microsoft Teams platform.</span></span> <span data-ttu-id="28be5-105">Achten Sie darauf, [die Entwurfsrichtlinien von Teams zu befolgen,](~/concepts/design/understand-use-cases.md) um Ihre App für Teams nativ zu machen.</span><span class="sxs-lookup"><span data-stu-id="28be5-105">Ensure to follow [Teams design guidelines](~/concepts/design/understand-use-cases.md) to make your app native to Teams.</span></span>
<span data-ttu-id="28be5-106">Dieses Dokument enthält eine Übersicht über die Voraussetzungen für die Integration von Webanwendungen in Teams, power platform to create Power apps, Power Virtual Agents, Virtual Assistant, App Templates, Shift Connectors, Moodle LMS, Erstellen einer Share-to-Teams-Schaltfläche für Ihre Website, Hinzufügen einer Microsoft Teams-Registerkarte in SharePoint, Erstellen von tiefen Links und Integrieren von Gerätefunktionen.</span><span class="sxs-lookup"><span data-stu-id="28be5-106">This document gives an overview of prerequisites to integrate web applications with Teams, Power platform to create Power apps, Power Virtual Agents, Virtual Assistant, app templates, Shift connectors, Moodle LMS, creating a Share-to-Teams button for your website, adding a Microsoft Teams tab in SharePoint, creating deep links, and integrating device capabilities.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="28be5-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="28be5-107">Prerequisites</span></span>   

<span data-ttu-id="28be5-108">Um eine effektive Integration zu gewährleisten, sollten Sie die folgenden Voraussetzungen besser verstehen:</span><span class="sxs-lookup"><span data-stu-id="28be5-108">For effective integration, ensure to have a better understanding of the following prerequisites:</span></span>
* <span data-ttu-id="28be5-109">Teams-Funktionen.</span><span class="sxs-lookup"><span data-stu-id="28be5-109">Teams capabilities.</span></span> 
* <span data-ttu-id="28be5-110">SharePoint-Anforderungen für Datei- und Datenspeicherung.</span><span class="sxs-lookup"><span data-stu-id="28be5-110">SharePoint requirements for file and data storage.</span></span>
* <span data-ttu-id="28be5-111">API-Anforderungen.</span><span class="sxs-lookup"><span data-stu-id="28be5-111">API requirements.</span></span>
* <span data-ttu-id="28be5-112">Authentifizierung.</span><span class="sxs-lookup"><span data-stu-id="28be5-112">Authentication.</span></span>
* <span data-ttu-id="28be5-113">Tiefe Verknüpfung Ihrer App mit Teams.</span><span class="sxs-lookup"><span data-stu-id="28be5-113">Deep linking of your app with Teams.</span></span>
* <span data-ttu-id="28be5-114">Ordnen Sie die Anwendungsfälle Ihrer App den Funktionen der Teams-Plattform zu.</span><span class="sxs-lookup"><span data-stu-id="28be5-114">Map your app's use cases to Teams platform capabilities.</span></span>
* <span data-ttu-id="28be5-115">Bestimmen Sie die Einstiegspunkte Ihrer App, z. B. persönliche Nutzung, Zusammenarbeit oder beides.</span><span class="sxs-lookup"><span data-stu-id="28be5-115">Determine your app's entry points, such as personal use, collaboration, or both.</span></span>

## <a name="low-code-platforms"></a><span data-ttu-id="28be5-116">Low-Code-Plattformen</span><span class="sxs-lookup"><span data-stu-id="28be5-116">Low code platforms</span></span>

<span data-ttu-id="28be5-117">Plattformen mit geringem Code bieten einen intuitiven Ansatz für die Softwareentwicklung und erfordern wenig oder keine Codierung zum Erstellen von Anwendungen und Prozessen.</span><span class="sxs-lookup"><span data-stu-id="28be5-117">Low code platforms provide an intuitive approach to software development and require little or no coding to build applications and processes.</span></span> <span data-ttu-id="28be5-118">Sie können benutzerdefinierte Apps ganz einfach mit Low-Code-Plattformen erstellen.</span><span class="sxs-lookup"><span data-stu-id="28be5-118">You can create custom apps easily with low code platforms.</span></span> <span data-ttu-id="28be5-119">Diese Plattformen bestehen aus einer visuellen Schnittstelle, Connectors für Back-End-Dienste und einem integrierten App-Lebenszyklusverwaltungssystem zum Erstellen, Debuggen, Bereitstellen und Verwalten von Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="28be5-119">These platforms consist of a visual interface, connectors to back end services, and a built-in app lifecycle management system to build, debug, deploy, and maintain applications.</span></span> <span data-ttu-id="28be5-120">Microsoft bietet die folgenden innovative Gateways zum schnellen Erstellen von Teams-kompatiblen Apps mithilfe von Attributen mit geringem Code:</span><span class="sxs-lookup"><span data-stu-id="28be5-120">Microsoft provides the following innovative gateways to rapidly build Teams-compatible apps using low code attributes:</span></span>
* <span data-ttu-id="28be5-121">Microsoft Power-Plattform</span><span class="sxs-lookup"><span data-stu-id="28be5-121">Microsoft Power platform</span></span>
* <span data-ttu-id="28be5-122">Microsoft Teams-App-Vorlagen</span><span class="sxs-lookup"><span data-stu-id="28be5-122">Microsoft Teams app templates</span></span>

## <a name="microsoft-power-platform"></a><span data-ttu-id="28be5-123">Microsoft Power-Plattform</span><span class="sxs-lookup"><span data-stu-id="28be5-123">Microsoft Power platform</span></span>

<span data-ttu-id="28be5-124">Die Microsoft Power-Plattform kombiniert vier robuste Microsoft-Technologien, z. B. Power BI, Power Apps, Power Automate und Power Virtual Agents in einer leistungsstarken Anwendungsplattform.</span><span class="sxs-lookup"><span data-stu-id="28be5-124">Microsoft Power platform combines four robust Microsoft technologies, such as Power BI, Power Apps, Power Automate, and Power Virtual Agents in one powerful application platform.</span></span> <span data-ttu-id="28be5-125">Mit diesen Technologien können Sie Lösungen erstellen, Prozesse automatisieren, Daten analysieren und virtuelle Agents in einer einheitlichen und integrierten Umgebung erstellen.</span><span class="sxs-lookup"><span data-stu-id="28be5-125">These technologies empower you to build solutions, automate processes, analyze data, and create virtual agents within a unified and integrated environment.</span></span>

### <a name="power-apps"></a><span data-ttu-id="28be5-126">Power Apps</span><span class="sxs-lookup"><span data-stu-id="28be5-126">Power Apps</span></span>

<span data-ttu-id="28be5-127">Mit Power Apps können Sie Geschäfts-Apps erstellen, die eine Verbindung mit Ihren Geschäftsdaten herstellen und auf die Anforderungen Ihrer Organisation zugeschnitten sind.</span><span class="sxs-lookup"><span data-stu-id="28be5-127">With Power Apps, you can build business apps that connect to your business data and are tailored to your organization's needs.</span></span> <span data-ttu-id="28be5-128">Power Apps ermöglichen eine vielzahl von App-Szenarien, um geschäftliche Herausforderungen mithilfe von Canvas-Apps zu lösen.</span><span class="sxs-lookup"><span data-stu-id="28be5-128">Power Apps enable a wide range of app scenarios to solve business challenges through canvas apps.</span></span> <span data-ttu-id="28be5-129">Nach dem Erstellen der App können Sie sie aus dem Power Apps-Herstellerportal exportieren und in Microsoft Teams einbetten.</span><span class="sxs-lookup"><span data-stu-id="28be5-129">After building the app, you can export it from the Power Apps maker portal and embed in Microsoft Teams.</span></span>

### <a name="power-virtual-agents"></a><span data-ttu-id="28be5-130">Power Virtual Agents</span><span class="sxs-lookup"><span data-stu-id="28be5-130">Power Virtual Agents</span></span>

<span data-ttu-id="28be5-131">Power Virtual Agent ist keine codegesteuerte grafische Benutzeroberflächenlösung.</span><span class="sxs-lookup"><span data-stu-id="28be5-131">Power Virtual Agent is a no code, guided graphical interface solution.</span></span> <span data-ttu-id="28be5-132">Es baut auf der Microsoft Power Platform und dem Bot Framework auf.</span><span class="sxs-lookup"><span data-stu-id="28be5-132">It is built on the Microsoft Power Platform and the Bot Framework.</span></span> <span data-ttu-id="28be5-133">Es ermöglicht jedem Mitglied Ihres Teams, umfassende Chatbots für Unterhaltungen zu erstellen und zu verwalten, die problemlos in die Teams-Plattform integriert werden können.</span><span class="sxs-lookup"><span data-stu-id="28be5-133">It empowers every member of your team to create and maintain rich conversational chatbots that easily integrate with the Teams platform.</span></span> <span data-ttu-id="28be5-134">Sie können intelligente virtuelle Agents für Teams entwerfen, entwickeln und veröffentlichen, ohne eine Entwicklungsumgebung einrichten, einen Webdienst erstellen oder sich direkt beim Bot Framework registrieren zu müssen.</span><span class="sxs-lookup"><span data-stu-id="28be5-134">You can design, develop, and publish intelligent virtual agents for Teams without having to setup a development environment, create a web service, or directly register with the Bot Framework.</span></span>

### <a name="create-virtual-assistant"></a><span data-ttu-id="28be5-135">Erstellen des virtuellen Assistenten</span><span class="sxs-lookup"><span data-stu-id="28be5-135">Create Virtual Assistant</span></span>

<span data-ttu-id="28be5-136">Der virtuelle Assistent ist eine Open-Source-Vorlage von Microsoft, mit der Sie eine stabile Unterhaltungslösung erstellen und gleichzeitig die vollständige Kontrolle über die Benutzeroberfläche, das Unternehmensbranding und die erforderlichen Daten beibehalten können.</span><span class="sxs-lookup"><span data-stu-id="28be5-136">Virtual Assistant is a Microsoft open-source template that enables you to create a robust conversational solution while maintaining full control of user experience, organizational branding, and necessary data.</span></span> 

## <a name="app-templates"></a><span data-ttu-id="28be5-137">App-Vorlagen</span><span class="sxs-lookup"><span data-stu-id="28be5-137">App templates</span></span>

<span data-ttu-id="28be5-138">Sie können die App-Vorlage verwenden, um benutzerdefinierte Apps zu erstellen, die Ihren Organisatorischen Anforderungen entsprechen.</span><span class="sxs-lookup"><span data-stu-id="28be5-138">You can use app template to create custom made apps to suit your organizational needs.</span></span> <span data-ttu-id="28be5-139">Dies sind produktionsbereite Apps für Microsoft Teams, die communitygesteuert, open-source und auf GitHub verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="28be5-139">These are production-ready apps for Microsoft Teams that are community driven, open-source, and available on GitHub.</span></span> <span data-ttu-id="28be5-140">Jede Vorlage enthält ausführliche Anweisungen zum Bereitstellen und Installieren der App für Ihre Organisation.</span><span class="sxs-lookup"><span data-stu-id="28be5-140">Each template contains detailed instructions to deploy and install the app for your organization.</span></span> <span data-ttu-id="28be5-141">Es stellt eine einsatzbereite Anwendung bereit, die Sie sofort installieren und verwenden können.</span><span class="sxs-lookup"><span data-stu-id="28be5-141">It provides a ready-to-use application that you can install and start using immediately.</span></span> 

## <a name="teams-shifts-work-force-management-connectors"></a><span data-ttu-id="28be5-142">Teams verschiebt Arbeitskraftverwaltungsconnectors</span><span class="sxs-lookup"><span data-stu-id="28be5-142">Teams Shifts Work Force Management connectors</span></span>

<span data-ttu-id="28be5-143">Teams Shifts Work Force Management Connectors sind produktionsbereite, Open-Source- und communitygesteuerte Integrationen.</span><span class="sxs-lookup"><span data-stu-id="28be5-143">Teams Shifts Work Force Management connectors are production-ready, open-source, and community-driven integrations.</span></span> <span data-ttu-id="28be5-144">Sie bieten eine nahtlose Erfahrung und einen schnellen Prozess für die digitale Transformation von FirstLine-Mitarbeitern mit Teams Shifts.</span><span class="sxs-lookup"><span data-stu-id="28be5-144">They offer a seamless experience and quick process for the digital transformation of firstline workers with Teams Shifts.</span></span>

## <a name="install-moodle-lms"></a><span data-ttu-id="28be5-145">Installieren von Moodle LMS</span><span class="sxs-lookup"><span data-stu-id="28be5-145">Install Moodle LMS</span></span>

<span data-ttu-id="28be5-146">Moodle ist ein beliebtes Open-Source Learning Management System (LMS).</span><span class="sxs-lookup"><span data-stu-id="28be5-146">Moodle is a popular open-source Learning Management System (LMS).</span></span> <span data-ttu-id="28be5-147">Es ist jetzt in Microsoft Teams integriert.</span><span class="sxs-lookup"><span data-stu-id="28be5-147">It is now integrated with Microsoft Teams.</span></span> <span data-ttu-id="28be5-148">Diese Integration hilft Lehrkräften und Lehrkräften bei der Zusammenarbeit an Kursen von Moodle, beim Stellen von Fragen zu Noten und Aufgaben und bei der Aktualisierung von Benachrichtigungen direkt in Teams.</span><span class="sxs-lookup"><span data-stu-id="28be5-148">This integration helps educators and teachers to collaborate around Moodle courses, ask questions about grades and assignments, and stay updated with notifications directly within Teams.</span></span>

## <a name="create-a-share-to-teams-button-for-your-website"></a><span data-ttu-id="28be5-149">Erstellen einer Schaltfläche zum Teilen in Teams für Ihre Website</span><span class="sxs-lookup"><span data-stu-id="28be5-149">Create a Share-to-Teams button for your website</span></span>

<span data-ttu-id="28be5-150">Websites von Drittanbietern können das Startstartskript verwenden, um Schaltflächen für die Freigabe in Teams auf ihren Webseiten einzubetten.</span><span class="sxs-lookup"><span data-stu-id="28be5-150">Third-party websites can use the launcher script to embed Share to Teams buttons on their webpages.</span></span> <span data-ttu-id="28be5-151">Wenn Sie die Schaltfläche auswählen, wird die Share to Teams-Erfahrung in einem Popupfenster gestartet.</span><span class="sxs-lookup"><span data-stu-id="28be5-151">When you select the button, it launches the Share to Teams experience in a pop-up window.</span></span> <span data-ttu-id="28be5-152">Auf diese Weise können Sie einen Link direkt für jede Person oder einen Microsoft Teams-Kanal freigeben, ohne den Kontext zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="28be5-152">This allows you to share a link directly to any person or Microsoft Teams channel without switching context.</span></span>

## <a name="add-a-microsoft-teams-tab-in-sharepoint"></a><span data-ttu-id="28be5-153">Hinzufügen einer Microsoft Teams-Registerkarte in SharePoint</span><span class="sxs-lookup"><span data-stu-id="28be5-153">Add a Microsoft Teams tab in SharePoint</span></span>

<span data-ttu-id="28be5-154">Sie können eine umfassende Integrationserfahrung zwischen Microsoft Teams und SharePoint erhalten, indem Sie eine Microsoft Teams-Registerkarte in SharePoint als SPFx-Web part hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="28be5-154">You can get a rich integration experience between Microsoft Teams and SharePoint by adding a Microsoft Teams tab in SharePoint as an SPFx web part.</span></span> 

## <a name="create-deep-link"></a><span data-ttu-id="28be5-155">Erstellen eines Tiefenlinks</span><span class="sxs-lookup"><span data-stu-id="28be5-155">Create deep link</span></span>

<span data-ttu-id="28be5-156">Sie können tiefe Links zu den Entitäten in Teams erstellen.</span><span class="sxs-lookup"><span data-stu-id="28be5-156">You can create deep links to the entities in Teams.</span></span> <span data-ttu-id="28be5-157">Sie können Links zu Informationen und Features in Teams erstellen.</span><span class="sxs-lookup"><span data-stu-id="28be5-157">You can create links to information and features within Teams.</span></span> <span data-ttu-id="28be5-158">Diese tiefen Links navigieren zu Inhalten und Informationen auf Ihrer Registerkarte. Sie können tiefe Links verwenden, um Ihre App mit Teams zu verknüpfen, da sie mehrere Teile einer App für eine nativere Teams-Erfahrung verbinden.</span><span class="sxs-lookup"><span data-stu-id="28be5-158">These deep links navigate to content and information within your tab. You can use deep links to link your app with Teams as they tie together multiple pieces of an app for a more native Teams experience.</span></span>

## <a name="integrate-device-capabilities"></a><span data-ttu-id="28be5-159">Integrieren von Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="28be5-159">Integrate device capabilities</span></span>

<span data-ttu-id="28be5-160">Die Microsoft Teams-Plattform verbessert kontinuierlich die Entwicklerfunktionen, die auf integrierte Erfahrungen von Erstentwicklern ausgerichtet sind.</span><span class="sxs-lookup"><span data-stu-id="28be5-160">Microsoft Teams platform is continuously enhancing developer capabilities aligning with built-in first-party experiences.</span></span> <span data-ttu-id="28be5-161">Die erweiterte Teams-Plattform ermöglicht Partnern den Zugriff und die Integration der systemeigenen Gerätefunktionen, z. B. Kamera, QR- oder Strichcodescanner, Fotogalerie, Mikrofon und Standort mithilfe dedizierter APIs, die im Microsoft Teams JavaScript-Client-SDK verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="28be5-161">The enhanced Teams platform allows partners to access and integrate the native device capabilities, such as camera, QR or barcode scanner, photo gallery, microphone, and location using dedicated APIs available in Microsoft Teams JavaScript client SDK.</span></span> 

## <a name="see-also"></a><span data-ttu-id="28be5-162">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="28be5-162">See also</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="28be5-163">Ordnen Sie die Anwendungsfälle Ihrer App den Funktionen der Teams-Plattform zu.</span><span class="sxs-lookup"><span data-stu-id="28be5-163">Map your app's use cases to Teams platform capabilities</span></span>](~/concepts/design/map-use-cases.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="28be5-164">Bestimmen der Einstiegspunkte Ihrer App</span><span class="sxs-lookup"><span data-stu-id="28be5-164">Determine your app's entry points</span></span>](~/concepts/extensibility-points.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="28be5-165">Integrieren von Web-Apps</span><span class="sxs-lookup"><span data-stu-id="28be5-165">Integrate web apps</span></span>](~/samples/integrating-web-apps.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="28be5-166">Erstellen von benutzerdefinierten Apps mit geringem Code für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="28be5-166">Create low-code custom apps for Microsoft Teams</span></span>](~/samples/teams-low-code-solutions.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="28be5-167">Hinzufügen eines Power Virtual Agent-Chatbots</span><span class="sxs-lookup"><span data-stu-id="28be5-167">Add a Power Virtual Agents chatbot</span></span>](~/bots/how-to/add-power-virtual-agents-bot-to-teams.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="28be5-168">Erstellen eines virtuellen Assistenten</span><span class="sxs-lookup"><span data-stu-id="28be5-168">Create virtual assistant</span></span>](~/samples/virtual-assistant.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="28be5-169">App-Vorlagen für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="28be5-169">App templates for Microsoft Teams</span></span>](~/samples/app-templates.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="28be5-170">Produktionsbereite Umschaltconnectors</span><span class="sxs-lookup"><span data-stu-id="28be5-170">Production-ready Shift Connectors</span></span>](~/samples/shifts-wfm-connectors.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="28be5-171">Installieren von Moodle LMS</span><span class="sxs-lookup"><span data-stu-id="28be5-171">Install Moodle LMS</span></span>](~/resources/moodleinstructions.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="28be5-172">Erstellen einer Schaltfläche zum Teilen in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="28be5-172">Create a Share-to-Teams button</span></span>](~/concepts/build-and-test/share-to-teams.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="28be5-173">Hinzufügen einer Microsoft Teams-Registerkarte zu SharePoint</span><span class="sxs-lookup"><span data-stu-id="28be5-173">Add a Teams tab to SharePoint</span></span>](~/tabs/how-to/tabs-in-sharepoint.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="28be5-174">Erstellen von Deep-Links</span><span class="sxs-lookup"><span data-stu-id="28be5-174">Create deep links</span></span>](~/concepts/build-and-test/deep-links.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="28be5-175">Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="28be5-175">Device capabilities</span></span>](~/concepts/device-capabilities/device-capabilities-overview.md)
