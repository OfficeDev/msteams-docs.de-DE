---
title: Erste Schritte – Erstellen Der ersten App-Übersicht und der voraussetzungen
author: girliemac
description: Erfahren Sie, wie Sie mit der Entwicklung von Microsoft Teams-Apps beginnen und Ihre Umgebung einrichten.
ms.author: timura
ms.date: 03/18/2021
ms.topic: quickstart
ms.openlocfilehash: 3bc99c535ea659f046b65dc26d9a60de0dd49cab
ms.sourcegitcommit: 303fc214aa04757779a171337f31a6539f47fd03
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2021
ms.locfileid: "52068573"
---
# <a name="get-started-with-microsoft-teams-app-development"></a><span data-ttu-id="3d6b7-103">Erste Schritte mit der Entwicklung von Microsoft Teams-Apps</span><span class="sxs-lookup"><span data-stu-id="3d6b7-103">Get started with Microsoft Teams app development</span></span>

<span data-ttu-id="3d6b7-104">Erstellen Sie eine einfache App, um die Grundlagen der Teams-App-Entwicklung zu erlernen.</span><span class="sxs-lookup"><span data-stu-id="3d6b7-104">Build a simple app to learn the basics of Teams app development.</span></span> <span data-ttu-id="3d6b7-105">Sobald Sie "Hello, World!" sehen, testen Sie einen der anderen Artikel für erste Schritte, um weitere Informationen zu allgemeinen Tools, grundlegenden Konzepten und erweiterten Features zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="3d6b7-105">Once you see "Hello, World!", try any of the other get started articles for more information on common tools, fundamental concepts, and advanced features.</span></span>



## <a name="what-youll-learn"></a><span data-ttu-id="3d6b7-106">Was Sie lernen werden</span><span class="sxs-lookup"><span data-stu-id="3d6b7-106">What you'll learn</span></span>

* <span data-ttu-id="3d6b7-107">Schnelles Arbeiten mit dem Teams Toolkit, einer Visual Studio Codeerweiterung</span><span class="sxs-lookup"><span data-stu-id="3d6b7-107">Get up and running quickly with the Teams Toolkit, a Visual Studio Code extension</span></span> 
* <span data-ttu-id="3d6b7-108">Konfigurieren Ihrer App mit App Studio</span><span class="sxs-lookup"><span data-stu-id="3d6b7-108">Configure your app with App Studio</span></span> 
* <span data-ttu-id="3d6b7-109">Machen Sie sich mit Teams-Entwicklertools und SDKs vertraut</span><span class="sxs-lookup"><span data-stu-id="3d6b7-109">Get familiar with Teams developer tools and SDKs</span></span>
* <span data-ttu-id="3d6b7-110">Berücksichtigen wichtiger Teams-App-Konzepte, z. B. bewährte Methoden für Authentifizierung und Entwurf</span><span class="sxs-lookup"><span data-stu-id="3d6b7-110">Consider important Teams app concepts, such as authentication and design best practices</span></span>

<span data-ttu-id="3d6b7-111">Sie können eine Teams-App mit einer beliebigen Technologie erstellen, z. B. der Befehlszeilenschnittstelle (CLI).</span><span class="sxs-lookup"><span data-stu-id="3d6b7-111">You can build Teams app using any technology of your choice, for example, command-line interface (CLI).</span></span> <span data-ttu-id="3d6b7-112">Diese Artikel helfen Ihnen jedoch, mit den folgenden empfohlenen Tools und Technologien zu beginnen:</span><span class="sxs-lookup"><span data-stu-id="3d6b7-112">But, these articles help you get started with the following recommended tools and technologies:</span></span>

* <span data-ttu-id="3d6b7-113">Teams Toolkit, eine Visual Studio Codeerweiterung</span><span class="sxs-lookup"><span data-stu-id="3d6b7-113">Teams Toolkit, a Visual Studio Code extension</span></span>
* <span data-ttu-id="3d6b7-114">React.js für Registerkarten</span><span class="sxs-lookup"><span data-stu-id="3d6b7-114">React.js for tabs</span></span>
* <span data-ttu-id="3d6b7-115">Node.js für Bots und Messagingerweiterungen</span><span class="sxs-lookup"><span data-stu-id="3d6b7-115">Node.js for bots and messaging extensions</span></span>


## <a name="teams-app-fundamentals"></a><span data-ttu-id="3d6b7-116">Grundlagen der Teams-App</span><span class="sxs-lookup"><span data-stu-id="3d6b7-116">Teams app fundamentals</span></span>

<span data-ttu-id="3d6b7-117">Sie können benutzerdefinierte Teams-Apps für sich selbst, Personen in Ihrer Organisation oder Personen auf der ganzen Welt erstellen.</span><span class="sxs-lookup"><span data-stu-id="3d6b7-117">You can build custom Teams apps for yourself, people in your org, or people all over the world.</span></span> <span data-ttu-id="3d6b7-118">Bevor Sie beginnen, sollten Sie die folgenden grundlegenden Konzepte zur Entwicklung von Teams-Apps verstehen:</span><span class="sxs-lookup"><span data-stu-id="3d6b7-118">Before you begin, you should understand the following fundamental concepts about Teams app development:</span></span>

### <a name="common-app-use-cases"></a><span data-ttu-id="3d6b7-119">Häufige Anwendungsfälle für Apps</span><span class="sxs-lookup"><span data-stu-id="3d6b7-119">Common app use cases</span></span>

<span data-ttu-id="3d6b7-120">Einige typische Szenarien, bei denen eine benutzerdefinierte Teams-App hilfreich sein kann, sind:</span><span class="sxs-lookup"><span data-stu-id="3d6b7-120">Some typical scenarios that a custom Teams app can help with are:</span></span>

* <span data-ttu-id="3d6b7-121">Einbetten webbasierter Inhalte, z. B. einer Web-App oder eines Teils einer Website, in den Teams-Client</span><span class="sxs-lookup"><span data-stu-id="3d6b7-121">Embed web-based content, such as a web app or part of a website, in the Teams client</span></span>
* <span data-ttu-id="3d6b7-122">Schnelles Suchen von Informationen in einem anderen System und Hinzufügen zu einer Teams-Unterhaltung</span><span class="sxs-lookup"><span data-stu-id="3d6b7-122">Look up information quickly in another system and adding it to a Teams conversation</span></span> 
* <span data-ttu-id="3d6b7-123">Auslösen von Workflows und Prozessen direkt aus dem, was in einer Unterhaltung gesagt wird</span><span class="sxs-lookup"><span data-stu-id="3d6b7-123">Trigger workflows and processes directly from what's said in a conversation</span></span> 

### <a name="app-capabilities-and-tools"></a><span data-ttu-id="3d6b7-124">App-Funktionen und -Tools</span><span class="sxs-lookup"><span data-stu-id="3d6b7-124">App capabilities and tools</span></span>

<span data-ttu-id="3d6b7-125">Eine App besteht aus einer oder mehreren Teams-Funktionen und Benutzerinteraktionspunkten.</span><span class="sxs-lookup"><span data-stu-id="3d6b7-125">An app is made up of one or more Teams capabilities and user interaction points.</span></span> <span data-ttu-id="3d6b7-126">Ihr Entwicklungstoolset variiert je nach den von Ihnen verwendeten Funktionen.</span><span class="sxs-lookup"><span data-stu-id="3d6b7-126">Your development toolset will vary depending on the capabilities you want.</span></span>

| <span data-ttu-id="3d6b7-127">**App-Funktionen**</span><span class="sxs-lookup"><span data-stu-id="3d6b7-127">**App capabilities**</span></span>| <span data-ttu-id="3d6b7-128">**Interaktionspunkte**</span><span class="sxs-lookup"><span data-stu-id="3d6b7-128">**Interaction points**</span></span> | <span data-ttu-id="3d6b7-129">**Empfohlene Tools**</span><span class="sxs-lookup"><span data-stu-id="3d6b7-129">**Recommended tools**</span></span> | <span data-ttu-id="3d6b7-130">**SDKs**</span><span class="sxs-lookup"><span data-stu-id="3d6b7-130">**SDKs**</span></span> | <span data-ttu-id="3d6b7-131">**Technologiestapel**</span><span class="sxs-lookup"><span data-stu-id="3d6b7-131">**Technology stacks**</span></span> |
|--------|--------|--------|--------|--------|
| <span data-ttu-id="3d6b7-132">Registerkarten</span><span class="sxs-lookup"><span data-stu-id="3d6b7-132">Tabs</span></span> | <span data-ttu-id="3d6b7-133">Räume, in denen Benutzer mit eingebetteten Webinhalten in persönlichen und freigegebenen Kontexten interagieren können</span><span class="sxs-lookup"><span data-stu-id="3d6b7-133">Spaces where users can interact with embedded web content in personal and shared contexts</span></span> | <span data-ttu-id="3d6b7-134">VS-Code mit Teams Toolkit-Erweiterung oder Yeoman-Generator</span><span class="sxs-lookup"><span data-stu-id="3d6b7-134">VS Code with Teams Toolkit extension or Yeoman Generator</span></span> | <span data-ttu-id="3d6b7-135">Microsoft Teams JavaScript-Client-SDK</span><span class="sxs-lookup"><span data-stu-id="3d6b7-135">Teams JavaScript client SDK</span></span> | <span data-ttu-id="3d6b7-136">Allgemeine Webtechnologien (HTML, CSS und JavaScript) oder React.js</span><span class="sxs-lookup"><span data-stu-id="3d6b7-136">General web technologies (HTML, CSS, and JavaScript) or React.js</span></span> |
| <span data-ttu-id="3d6b7-137">Bots</span><span class="sxs-lookup"><span data-stu-id="3d6b7-137">Bots</span></span> | <span data-ttu-id="3d6b7-138">Chatbots, die mit Benutzern in persönlichen und freigegebenen Kontexten interagieren</span><span class="sxs-lookup"><span data-stu-id="3d6b7-138">Chatbots that interact with users in personal and shared contexts</span></span> | <span data-ttu-id="3d6b7-139">VS-Code mit Teams Toolkit-Erweiterung oder Yeoman-Generator</span><span class="sxs-lookup"><span data-stu-id="3d6b7-139">VS Code with Teams Toolkit extension or Yeoman Generator</span></span> | <span data-ttu-id="3d6b7-140">Bot Franework SDK</span><span class="sxs-lookup"><span data-stu-id="3d6b7-140">Bot Franework SDK</span></span> | <span data-ttu-id="3d6b7-141">Node.js, C# oder Python</span><span class="sxs-lookup"><span data-stu-id="3d6b7-141">Node.js, C#, or Python</span></span> | 
| <span data-ttu-id="3d6b7-142">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="3d6b7-142">Messaging extensions</span></span> | <span data-ttu-id="3d6b7-143">Verknüpfungen zum Einfügen von App-Inhalten oder Zum Handeln in einer Nachricht, ohne aus der Unterhaltung zu navigieren</span><span class="sxs-lookup"><span data-stu-id="3d6b7-143">Shortcuts for inserting app content or acting on a message without navigating away from the conversation</span></span> | <span data-ttu-id="3d6b7-144">VS-Code mit Teams Toolkit-Erweiterung oder Yeoman-Generator</span><span class="sxs-lookup"><span data-stu-id="3d6b7-144">VS Code with Teams Toolkit extension or Yeoman Generator</span></span> | <span data-ttu-id="3d6b7-145">Bot Framework SDK</span><span class="sxs-lookup"><span data-stu-id="3d6b7-145">Bot Framework SDK</span></span> | <span data-ttu-id="3d6b7-146">Node.js, C# oder Python</span><span class="sxs-lookup"><span data-stu-id="3d6b7-146">Node.js, C#, or Python</span></span> |

### <a name="teams-doesnt-host-your-app"></a><span data-ttu-id="3d6b7-147">Teams hosten Ihre App nicht</span><span class="sxs-lookup"><span data-stu-id="3d6b7-147">Teams doesn't host your app</span></span>

<span data-ttu-id="3d6b7-148">Wenn ein Benutzer Ihre App in Teams installiert, installiert er nur ein App-Paket, das eine Konfigurationsdatei (auch als App-Manifest bezeichnet) und die Symbole Ihrer App enthält.</span><span class="sxs-lookup"><span data-stu-id="3d6b7-148">When a user installs your app in Teams, they only install an app package that contains a configuration file (also known as an app manifest) and your app’s icons.</span></span> <span data-ttu-id="3d6b7-149">Die Logik und datenspeicherung Ihrer App werden an anderer Stelle gehostet, z. B. Azure Web Services oder localhost während der Entwicklung.</span><span class="sxs-lookup"><span data-stu-id="3d6b7-149">Your app’s logic and data storage are hosted elsewhere, such as Azure Web Services or localhost during development.</span></span> <span data-ttu-id="3d6b7-150">Teams zugrifft über HTTPS auf diese Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="3d6b7-150">Teams accesses these resources via HTTPS.</span></span>

:::image type="content" source="../assets/images/build-your-first-app/app-in-cloud.png" alt-text="Abbildung, die Ihre App in Teams zeigt, zeigt auf Ihre App-Logik auf dem Cloudserver.":::

## <a name="next-step"></a><span data-ttu-id="3d6b7-152">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="3d6b7-152">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3d6b7-153">Erstellen und Ausführen Ihrer ersten Teams-App</span><span class="sxs-lookup"><span data-stu-id="3d6b7-153">Build and run your first Teams app</span></span>](../build-your-first-app/build-and-run.md)
