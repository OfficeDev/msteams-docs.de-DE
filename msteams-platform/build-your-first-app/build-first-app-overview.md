---
title: Erste Schritte - Erstellen Sie Ihre erste App-Übersicht und -Voraussetzungen
author: girliemac
description: Erfahren Sie, wie Sie mit Microsoft Teams App-Entwicklung beginnen und Ihre Umgebung einrichten.
ms.author: timura
ms.date: 03/18/2021
ms.topic: quickstart
ms.openlocfilehash: dae942be9383ef1e0a931d238e6148651f334ef5
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565879"
---
# <a name="get-started-with-microsoft-teams-app-development"></a><span data-ttu-id="1050a-103">Erste Schritte mit Microsoft Teams App-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="1050a-103">Get started with Microsoft Teams app development</span></span>

<span data-ttu-id="1050a-104">Erstellen Sie eine einfache App, um die Grundlagen der Teams App-Entwicklung zu erlernen.</span><span class="sxs-lookup"><span data-stu-id="1050a-104">Build a simple app to learn the basics of Teams app development.</span></span> <span data-ttu-id="1050a-105">Sobald Sie "Hello, World!" sehen, versuchen Sie einen der anderen ersten Artikel für weitere Informationen über allgemeine Tools, grundlegende Konzepte und erweiterte Funktionen.</span><span class="sxs-lookup"><span data-stu-id="1050a-105">Once you see "Hello, World!", try any of the other get started articles for more information on common tools, fundamental concepts, and advanced features.</span></span>



## <a name="what-youll-learn"></a><span data-ttu-id="1050a-106">Was Sie lernen werden</span><span class="sxs-lookup"><span data-stu-id="1050a-106">What you'll learn</span></span>

* <span data-ttu-id="1050a-107">Mit dem Teams Toolkit, einer Visual Studio Code-Erweiterung, können Sie schnell losfahren.</span><span class="sxs-lookup"><span data-stu-id="1050a-107">Get up and running quickly with the Teams Toolkit, a Visual Studio Code extension.</span></span> 
* <span data-ttu-id="1050a-108">Konfigurieren Sie Ihre App mit App Studio.</span><span class="sxs-lookup"><span data-stu-id="1050a-108">Configure your app with App Studio.</span></span>
* <span data-ttu-id="1050a-109">Machen Sie sich mit Teams Entwicklertools und SDKs vertraut.</span><span class="sxs-lookup"><span data-stu-id="1050a-109">Get familiar with Teams developer tools and SDKs.</span></span>
* <span data-ttu-id="1050a-110">Berücksichtigen Sie wichtige Teams App-Konzepten, z. B. Authentifizierung und Best Practices für das Design.</span><span class="sxs-lookup"><span data-stu-id="1050a-110">Consider important Teams app concepts, such as authentication and design best practices.</span></span>

<span data-ttu-id="1050a-111">Sie können eine Teams-App mit jeder Technologie Ihrer Wahl erstellen, z. B. Befehlszeilenschnittstelle (CLI).</span><span class="sxs-lookup"><span data-stu-id="1050a-111">You can build a Teams app using any technology of your choice, for example, command-line interface (CLI).</span></span> <span data-ttu-id="1050a-112">Diese Artikel helfen Ihnen jedoch bei den ersten Schritte mit den folgenden empfohlenen Tools und Technologien:</span><span class="sxs-lookup"><span data-stu-id="1050a-112">But, these articles help you get started with the following recommended tools and technologies:</span></span>

* <span data-ttu-id="1050a-113">Teams Toolkit, eine Visual Studio Code Erweiterung</span><span class="sxs-lookup"><span data-stu-id="1050a-113">Teams Toolkit, a Visual Studio Code extension</span></span>
* <span data-ttu-id="1050a-114">React.js für Tabs</span><span class="sxs-lookup"><span data-stu-id="1050a-114">React.js for tabs</span></span>
* <span data-ttu-id="1050a-115">Node.js für Bots und Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="1050a-115">Node.js for bots and messaging extensions</span></span>


## <a name="teams-app-fundamentals"></a><span data-ttu-id="1050a-116">Teams-App-Grundlagen</span><span class="sxs-lookup"><span data-stu-id="1050a-116">Teams app fundamentals</span></span>

<span data-ttu-id="1050a-117">Sie können benutzerdefinierte Teams Apps für sich selbst, Personen in Ihrer Organisation oder Personen auf der ganzen Welt erstellen.</span><span class="sxs-lookup"><span data-stu-id="1050a-117">You can build custom Teams apps for yourself, people in your org, or people all over the world.</span></span> <span data-ttu-id="1050a-118">Bevor Sie beginnen, sollten Sie die folgenden grundlegenden Konzepte zur Teams App-Entwicklung verstehen:</span><span class="sxs-lookup"><span data-stu-id="1050a-118">Before you begin, you should understand the following fundamental concepts about Teams app development:</span></span>

### <a name="common-app-use-cases"></a><span data-ttu-id="1050a-119">Häufige Anwendungsfälle für Apps</span><span class="sxs-lookup"><span data-stu-id="1050a-119">Common app use cases</span></span>

<span data-ttu-id="1050a-120">Einige typische Szenarien, bei denen eine benutzerdefinierte Teams App helfen kann, sind:</span><span class="sxs-lookup"><span data-stu-id="1050a-120">Some typical scenarios that a custom Teams app can help with are:</span></span>

* <span data-ttu-id="1050a-121">Einbetten webbasierter Inhalte, z. B. einer Web-App oder eines Teils einer Website, in den Teams Client.</span><span class="sxs-lookup"><span data-stu-id="1050a-121">Embed web-based content, such as a web app or part of a website, in the Teams client.</span></span>
* <span data-ttu-id="1050a-122">Suchen Sie Informationen schnell in einem anderen System und fügen Sie sie einer Teams Unterhaltung hinzu.</span><span class="sxs-lookup"><span data-stu-id="1050a-122">Look up information quickly in another system and adding it to a Teams conversation.</span></span>
* <span data-ttu-id="1050a-123">Lösen Sie Workflows und Prozesse direkt aus dem, was in einer Unterhaltung gesagt wird.</span><span class="sxs-lookup"><span data-stu-id="1050a-123">Trigger workflows and processes directly from what's said in a conversation.</span></span>

### <a name="app-capabilities-and-tools"></a><span data-ttu-id="1050a-124">App-Funktionen und -Tools</span><span class="sxs-lookup"><span data-stu-id="1050a-124">App capabilities and tools</span></span>

<span data-ttu-id="1050a-125">Eine App besteht aus einer oder mehreren Teams Funktionen und Benutzerinteraktionspunkten.</span><span class="sxs-lookup"><span data-stu-id="1050a-125">An app is made up of one or more Teams capabilities and user interaction points.</span></span> <span data-ttu-id="1050a-126">Ihr Entwicklungstoolset hängt von den gewünschten Funktionen ab.</span><span class="sxs-lookup"><span data-stu-id="1050a-126">Your development toolset will vary depending on the capabilities you want.</span></span>

| <span data-ttu-id="1050a-127">**App-Funktionen**</span><span class="sxs-lookup"><span data-stu-id="1050a-127">**App capabilities**</span></span>| <span data-ttu-id="1050a-128">**Interaktionspunkte**</span><span class="sxs-lookup"><span data-stu-id="1050a-128">**Interaction points**</span></span> | <span data-ttu-id="1050a-129">**Empfohlene Werkzeuge**</span><span class="sxs-lookup"><span data-stu-id="1050a-129">**Recommended tools**</span></span> | <span data-ttu-id="1050a-130">**SDKs**</span><span class="sxs-lookup"><span data-stu-id="1050a-130">**SDKs**</span></span> | <span data-ttu-id="1050a-131">**Technologie-Stacks**</span><span class="sxs-lookup"><span data-stu-id="1050a-131">**Technology stacks**</span></span> |
|--------|--------|--------|--------|--------|
| <span data-ttu-id="1050a-132">Registerkarten</span><span class="sxs-lookup"><span data-stu-id="1050a-132">Tabs</span></span> | <span data-ttu-id="1050a-133">Räume, in denen Benutzer mit eingebetteten Webinhalten in persönlichen und freigegebenen Kontexten interagieren können.</span><span class="sxs-lookup"><span data-stu-id="1050a-133">Spaces where users can interact with embedded web content in personal and shared contexts.</span></span> | <span data-ttu-id="1050a-134">VS Code mit Teams Toolkit-Erweiterung oder Yeoman Generator</span><span class="sxs-lookup"><span data-stu-id="1050a-134">VS Code with Teams Toolkit extension or Yeoman Generator</span></span> | <span data-ttu-id="1050a-135">Microsoft Teams JavaScript-Client-SDK</span><span class="sxs-lookup"><span data-stu-id="1050a-135">Teams JavaScript client SDK</span></span> | <span data-ttu-id="1050a-136">Allgemeine Webtechnologien (HTML, CSS und JavaScript) oder React.js</span><span class="sxs-lookup"><span data-stu-id="1050a-136">General web technologies (HTML, CSS, and JavaScript) or React.js</span></span> |
| <span data-ttu-id="1050a-137">Bots</span><span class="sxs-lookup"><span data-stu-id="1050a-137">Bots</span></span> | <span data-ttu-id="1050a-138">Chatbots, die mit Benutzern in persönlichen und gemeinsam genutzten Kontexten interagieren.</span><span class="sxs-lookup"><span data-stu-id="1050a-138">Chatbots that interact with users in personal and shared contexts.</span></span> | <span data-ttu-id="1050a-139">VS Code mit Teams Toolkit-Erweiterung oder Yeoman Generator</span><span class="sxs-lookup"><span data-stu-id="1050a-139">VS Code with Teams Toolkit extension or Yeoman Generator</span></span> | <span data-ttu-id="1050a-140">Bot Framework SDK</span><span class="sxs-lookup"><span data-stu-id="1050a-140">Bot Framework SDK</span></span> | <span data-ttu-id="1050a-141">Node.js, C-Code oder Python</span><span class="sxs-lookup"><span data-stu-id="1050a-141">Node.js, C#, or Python</span></span> | 
| <span data-ttu-id="1050a-142">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="1050a-142">Messaging extensions</span></span> | <span data-ttu-id="1050a-143">Verknüpfungen zum Einfügen von App-Inhalten oder zum Handeln auf einer Nachricht, ohne von der Unterhaltung weg zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="1050a-143">Shortcuts for inserting app content or acting on a message without navigating away from the conversation.</span></span> | <span data-ttu-id="1050a-144">VS Code mit Teams Toolkit-Erweiterung oder Yeoman Generator</span><span class="sxs-lookup"><span data-stu-id="1050a-144">VS Code with Teams Toolkit extension or Yeoman Generator</span></span> | <span data-ttu-id="1050a-145">Bot Framework SDK</span><span class="sxs-lookup"><span data-stu-id="1050a-145">Bot Framework SDK</span></span> | <span data-ttu-id="1050a-146">Node.js, C-Code oder Python</span><span class="sxs-lookup"><span data-stu-id="1050a-146">Node.js, C#, or Python</span></span> |

### <a name="teams-doesnt-host-your-app"></a><span data-ttu-id="1050a-147">Teams hostt Ihre App nicht</span><span class="sxs-lookup"><span data-stu-id="1050a-147">Teams doesn't host your app</span></span>

<span data-ttu-id="1050a-148">Wenn ein Benutzer Ihre App in Teams installiert, installiert er nur ein App-Paket, das eine Konfigurationsdatei (auch als App-Manifest bezeichnet) und die Symbole Ihrer App enthält.</span><span class="sxs-lookup"><span data-stu-id="1050a-148">When a user installs your app in Teams, they only install an app package that contains a configuration file (also known as an app manifest) and your app’s icons.</span></span> <span data-ttu-id="1050a-149">Die Logik und der Datenspeicher Ihrer App werden an anderer Stelle gehostet, z. B. Azure Web Services oder localhost während der Entwicklung.</span><span class="sxs-lookup"><span data-stu-id="1050a-149">Your app’s logic and data storage are hosted elsewhere, such as Azure Web Services or localhost during development.</span></span> <span data-ttu-id="1050a-150">Teams greift über HTTPS auf diese Ressourcen zu.</span><span class="sxs-lookup"><span data-stu-id="1050a-150">Teams accesses these resources via HTTPS.</span></span>

:::image type="content" source="../assets/images/build-your-first-app/app-in-cloud.png" alt-text="Abbildungen, die Ihre App auf Teams zeigen, verweisen auf Ihre App-Logik im Cloudserver.":::

## <a name="next-step"></a><span data-ttu-id="1050a-152">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="1050a-152">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1050a-153">Erstellen und Ausführen Ihrer ersten Teams-App</span><span class="sxs-lookup"><span data-stu-id="1050a-153">Build and run your first Teams app</span></span>](../build-your-first-app/build-and-run.md)
