---
title: Erste Schritte – Erstellen Ihrer ersten Microsoft Teams-App mit React
author: adrianhall
description: Erstellen Sie mithilfe von Microsoft Teams-Toolkit und React schnell eine Microsoft Teams-App, die die Meldung "Hallo, Welt!" anzeigt.
ms.author: adhal
ms.date: 05/27/2021
ms.topic: quickstart
ms.openlocfilehash: c257bcd805a6b7b38ab657cb31cad961df1c4704
ms.sourcegitcommit: 9d63611974ba8a7e7f19ceea35e50189a2e90434
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2021
ms.locfileid: "53254321"
---
# <a name="build-and-run-your-first-microsoft-teams-app-with-react"></a><span data-ttu-id="71afa-104">Erstellen und Ausführen Ihrer ersten Microsoft Teams-App mit React</span><span class="sxs-lookup"><span data-stu-id="71afa-104">Build and run your first Microsoft Teams app with React</span></span>

<span data-ttu-id="71afa-105">In diesem Lernprogramm erfahren Sie, wie Sie eine neue Microsoft Teams-App in React erstellen, die eine einfache persönliche App zum Abrufen von Informationen aus dem Microsoft Graph implementiert.</span><span class="sxs-lookup"><span data-stu-id="71afa-105">In this tutorial, you will learn how to create a new Microsoft Teams app in React that implements a simple personal app to pull information from the Microsoft Graph.</span></span> <span data-ttu-id="71afa-106">Beispielsweise enthält eine *persönliche App* eine Reihe von Registerkarten für die individuelle Verwendung.</span><span class="sxs-lookup"><span data-stu-id="71afa-106">For example, a *personal app* includes a set of tabs for individual use.</span></span> <span data-ttu-id="71afa-107">Während des Lernprogramms erfahren Sie mehr über die Struktur einer Teams-App, wie Sie eine App lokal ausführen und wie Sie die App in Azure bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="71afa-107">During the tutorial, you will learn about the structure of a Teams app, how to run an app locally, and how to deploy the app to Azure.</span></span>

<span data-ttu-id="71afa-108">In der erstellten App werden grundlegende Benutzerinformationen für den aktuellen Benutzer angezeigt.</span><span class="sxs-lookup"><span data-stu-id="71afa-108">The app that is built displays basic user information for the current user.</span></span> <span data-ttu-id="71afa-109">Wenn die Berechtigung dazu erteilt wurde, stellt die App eine Verbindung mit Microsoft Graph als aktueller Benutzer her, um das vollständige Profil zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="71afa-109">When permission is granted, the app will connect to the Microsoft Graph as the current user to get the complete profile.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="71afa-110">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="71afa-110">Before you begin</span></span>

<span data-ttu-id="71afa-111">Stellen Sie sicher, dass Ihre Entwicklungsumgebung eingerichtet ist, indem Sie die erforderlichen Komponenten installieren.</span><span class="sxs-lookup"><span data-stu-id="71afa-111">Make sure your development environment is set up by installing the prerequisites.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="71afa-112">Erforderliche Komponenten installieren</span><span class="sxs-lookup"><span data-stu-id="71afa-112">Install prerequisites</span></span>](prerequisites.md)

## <a name="create-your-project"></a><span data-ttu-id="71afa-113">Erstellen Ihres Projekts</span><span class="sxs-lookup"><span data-stu-id="71afa-113">Create your project</span></span>

<span data-ttu-id="71afa-114">Verwenden Sie zum Erstellen Ihres ersten Projekts das Microsoft Teams-Toolkit:</span><span class="sxs-lookup"><span data-stu-id="71afa-114">Use the Teams Toolkit to create your first project:</span></span>

# <a name="visual-studio-code"></a>[<span data-ttu-id="71afa-115">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="71afa-115">Visual Studio Code</span></span>](#tab/vscode)

1. <span data-ttu-id="71afa-116">Öffnen Sie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="71afa-116">Open Visual Studio code.</span></span>
1. <span data-ttu-id="71afa-117">Öffnen Sie das Teams Toolkit, und wählen Sie das symbol Teams in der Seitenleiste aus:</span><span class="sxs-lookup"><span data-stu-id="71afa-117">Open the Teams Toolkit and select the Teams icon in the sidebar:</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="Das Microsoft Teams-Symbol in der Visual Studio Code-Randleiste.":::

1. <span data-ttu-id="71afa-119">Klicken Sie auf **Neues Projekt erstellen**.</span><span class="sxs-lookup"><span data-stu-id="71afa-119">Select **Create New Project**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project.png" alt-text="Ort des Links „Neues Projekt erstellen“ in der Randleiste des Microsoft Teams-Toolkits.":::

1. <span data-ttu-id="71afa-121">Wählen Sie **Neue Microsoft Teams-App erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="71afa-121">Select **Create a new Teams app**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-new-project-intro.png" alt-text="Starten des Assistenten für „Neues Projekt erstellen“":::

1. <span data-ttu-id="71afa-123">Geben Sie im Abschnitt **"Funktionen auswählen"** an, dass **"Tab"** ausgewählt ist, und wählen Sie **"OK"** aus.</span><span class="sxs-lookup"><span data-stu-id="71afa-123">In the **Select capabilities** section, varify that **Tab** is selected and select **OK**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-capabilities.png" alt-text="Screenshot, der zeigt, wie Ihrer neuen App Funktionen hinzufügt werden können.":::

1. <span data-ttu-id="71afa-125">Wählen Sie im Abschnitt **"Frontend-Hostingtyp"** **Azure** aus.</span><span class="sxs-lookup"><span data-stu-id="71afa-125">In the **Frontend hosting type** section, select **Azure**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-hosting.png" alt-text="Screenshot, der zeigt, wie das Hosting für Ihre neue App ausgewählt wird.":::

1. <span data-ttu-id="71afa-127">Wählen Sie im Abschnitt **"Cloudressourcen"** **OK** aus.</span><span class="sxs-lookup"><span data-stu-id="71afa-127">In the **Cloud resources** section, select **OK**.</span></span>  <span data-ttu-id="71afa-128">Für dieses Lernprogramm werden keine zusätzlichen Cloudressourcen benötigt.</span><span class="sxs-lookup"><span data-stu-id="71afa-128">We do not need additional cloud resources for this tutorial.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-cloud-resources.png" alt-text="Screenshot, der zeigt, wie Cloudressourcen für Ihre neue App hinzugefügt werden.":::

1. <span data-ttu-id="71afa-130">Wählen Sie im Abschnitt **"Programmiersprache"** **JavaScript** aus.</span><span class="sxs-lookup"><span data-stu-id="71afa-130">In the **Programming Language** section, select **JavaScript**.</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-programming-languages.png" alt-text="Screenshot, der zeigt, wie die Programmiersprache ausgewählt wird.":::

1. <span data-ttu-id="71afa-132">Wählen Sie einen Arbeitsbereichsordner aus.</span><span class="sxs-lookup"><span data-stu-id="71afa-132">Select a workspace folder.</span></span> <span data-ttu-id="71afa-133">Ein Ordner wird in Ihrem Arbeitsbereichsordner für das Projekt erstellt, das Sie erstellen.</span><span class="sxs-lookup"><span data-stu-id="71afa-133">A folder is created within your workspace folder for the project you are creating.</span></span>

1. <span data-ttu-id="71afa-134">Geben Sie einen passenden Namen für Ihre App ein, wie z. B. `helloworld`.</span><span class="sxs-lookup"><span data-stu-id="71afa-134">Enter a suitable name for your app, like `helloworld`.</span></span> <span data-ttu-id="71afa-135">Der Name der App darf nur aus alphanumerischen Zeichen bestehen.</span><span class="sxs-lookup"><span data-stu-id="71afa-135">The name of the app must consist only of alphanumeric characters.</span></span>  <span data-ttu-id="71afa-136">Drücken Sie die **EINGABETASTE**, um fortzufahren.</span><span class="sxs-lookup"><span data-stu-id="71afa-136">Press **Enter** to continue.</span></span>

   <span data-ttu-id="71afa-137">Ihre Teams-App wird innerhalb weniger Sekunden erstellt.</span><span class="sxs-lookup"><span data-stu-id="71afa-137">Your Teams app is created within a few seconds.</span></span>

# <a name="command-line"></a>[<span data-ttu-id="71afa-138">Befehlszeile</span><span class="sxs-lookup"><span data-stu-id="71afa-138">Command line</span></span>](#tab/cli)

<span data-ttu-id="71afa-139">Verwenden Sie die `teamsfx`-CLI zum Erstellen Ihres ersten Projekts.</span><span class="sxs-lookup"><span data-stu-id="71afa-139">Use the `teamsfx` CLI to create your first project.</span></span>  <span data-ttu-id="71afa-140">Beginnen Sie in dem Ordner, in dem Sie den Projektordner erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="71afa-140">Start from the folder where you want to create the project folder.</span></span>

``` bash
teamsfx new
```

<span data-ttu-id="71afa-141">Die CLI führt durch einige Fragen zum Erstellen des Projekts.</span><span class="sxs-lookup"><span data-stu-id="71afa-141">The CLI walks through some questions to create the project.</span></span> <span data-ttu-id="71afa-142">Mit jeder Frage erfahren Sie, wie Sie sie beantworten können, z. B. verwenden Sie Pfeiltasten, um eine Option auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="71afa-142">Each question will tell you how to answer it, for example, use arrow keys to select an option.</span></span> <span data-ttu-id="71afa-143">Wenn Sie eine Frage beantwortet haben, bestätigen Sie Ihre Auswahl, indem Sie die **EINGABETASTE** drücken.</span><span class="sxs-lookup"><span data-stu-id="71afa-143">When you have answered the question, confirm your choice by pressing **Enter**.</span></span>

1. <span data-ttu-id="71afa-144">Wählen Sie **Neue Microsoft Teams-App erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="71afa-144">Select **Create a new Teams app**.</span></span>
1. <span data-ttu-id="71afa-145">Wählen Sie die **Registerkartenfunktion** aus.</span><span class="sxs-lookup"><span data-stu-id="71afa-145">Select the **Tab** capability.</span></span>
1. <span data-ttu-id="71afa-146">Wählen Sie **Azure**-Frontend-Hosting aus.</span><span class="sxs-lookup"><span data-stu-id="71afa-146">Select **Azure** frontend hosting.</span></span> <span data-ttu-id="71afa-147">Wählen Sie keine Cloudressourcen aus.</span><span class="sxs-lookup"><span data-stu-id="71afa-147">Do not select any cloud resources.</span></span>
1. <span data-ttu-id="71afa-148">Wählen Sie **JavaScript** als Programmiersprache aus.</span><span class="sxs-lookup"><span data-stu-id="71afa-148">Select **JavaScript** as the programming language.</span></span>
1. <span data-ttu-id="71afa-149">Drücken Sie die **EINGABETASTE**, um den Standardordner des Arbeitsbereichs auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="71afa-149">Press **Enter** to select the default workspace folder.</span></span>
1. <span data-ttu-id="71afa-150">Geben Sie einen passenden Namen für Ihre App ein, wie z. B. `helloworld`.</span><span class="sxs-lookup"><span data-stu-id="71afa-150">Enter a suitable name for your app, like `helloworld`.</span></span>  <span data-ttu-id="71afa-151">Der Name der App darf nur aus alphanumerischen Zeichen bestehen.</span><span class="sxs-lookup"><span data-stu-id="71afa-151">The name of the app must consist only of alphanumeric characters.</span></span>

   <span data-ttu-id="71afa-152">Nachdem alle Fragen beantwortet wurden, wird Ihr Projekt erstellt.</span><span class="sxs-lookup"><span data-stu-id="71afa-152">After all the questions have been answered, your project is created.</span></span>

---

## <a name="take-a-tour-of-the-source-code"></a><span data-ttu-id="71afa-153">Machen Sie einen Rundgang durch den Quellcode</span><span class="sxs-lookup"><span data-stu-id="71afa-153">Take a tour of the source code</span></span>

<span data-ttu-id="71afa-154">Wenn Sie diesen Abschnitt vorerst überspringen möchten, können Sie [Ihre App lokal ausführen](#run-your-app-locally).</span><span class="sxs-lookup"><span data-stu-id="71afa-154">If you wish to skip this section for now, you can [run your app locally](#run-your-app-locally).</span></span>

<span data-ttu-id="71afa-155">Nachdem das Teams Toolkit Ihr Projekt konfiguriert hat, verfügen Sie über die Komponenten zum Erstellen einer einfachen persönlichen App für Teams.</span><span class="sxs-lookup"><span data-stu-id="71afa-155">After the Teams Toolkit configures your project, you have the components to build a basic personal app for Teams.</span></span> <span data-ttu-id="71afa-156">Die Projektverzeichnisse und -dateien werden im Explorer-Bereich von Visual Studio Code angezeigt.</span><span class="sxs-lookup"><span data-stu-id="71afa-156">The project directories and files display in the Explorer area of Visual Studio Code.</span></span>

:::image type="content" source="../assets/images/teams-toolkit-v2/react-app-project.png" alt-text="Screenshot der App-Projektdateien für eine persönliche App in Visual Studio Code":::

<span data-ttu-id="71afa-158">Das Toolkit erstellt im Projektverzeichnis automatisch Ordner basierend auf den Funktionen, die Sie während des Setups hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="71afa-158">The Toolkit automatically creates scaffolding for you in the project directory based on the capabilities you added during setup.</span></span> <span data-ttu-id="71afa-159">Das Microsoft Teams Toolkit behält seinen Status für Ihre App im `.fx`-Verzeichnis bei.</span><span class="sxs-lookup"><span data-stu-id="71afa-159">The Teams Toolkit maintains its state for your app in the `.fx` directory.</span></span>  <span data-ttu-id="71afa-160">Weitere Elemente in diesem Verzeichnis:</span><span class="sxs-lookup"><span data-stu-id="71afa-160">Among other items in this directory:</span></span>

- <span data-ttu-id="71afa-161">Die App-Symbole werden als PNG-Dateien in `color.png` und `outline.png` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="71afa-161">The app icons are stored as PNG files in `color.png` and `outline.png`.</span></span>
- <span data-ttu-id="71afa-162">Das App-Manifest für die Veröffentlichung im Entwicklerportal für Microsoft Teams wird in `manifest.source.json` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="71afa-162">The app manifest for publishing to the Developer Portal for Teams is stored in `manifest.source.json`.</span></span>
- <span data-ttu-id="71afa-163">Die Einstellungen, die Sie beim Erstellen des Projekts ausgewählt haben, werden in `settings.json` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="71afa-163">The settings you chose when creating the project are stored in `settings.json`.</span></span>

<span data-ttu-id="71afa-164">Da Sie während des Setups die Registerkartenfunktion ausgewählt haben, erstellt das Microsoft Teams-Toolkit den erforderlichen Code für eine einfache Registerkarte im `tabs`-Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="71afa-164">Since you selected the tab capability during setup, the Teams Toolkit scaffolds all the necessary code for a basic tab in the `tabs` directory.</span></span> <span data-ttu-id="71afa-165">In diesem Verzeichnis befinden sich mehrere wichtige Dateien:</span><span class="sxs-lookup"><span data-stu-id="71afa-165">Within this directory there are several important files:</span></span>

- <span data-ttu-id="71afa-166">`tabs/src/index.jsx` ist der Einstiegspunkt der Front-End-App, an dem die `App`-Hauptkomponente mit `ReactDOM.render()` gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="71afa-166">`tabs/src/index.jsx` is the front-end app's entry point, where the main `App` component is rendered with `ReactDOM.render()`.</span></span>
- <span data-ttu-id="71afa-167">`tabs/src/components/App.jsx` übernimmt das URL-Routing in Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="71afa-167">`tabs/src/components/App.jsx` handles URL routing in your app.</span></span> <span data-ttu-id="71afa-168">Es ruft das [Microsoft Teams JavaScript-Client-SDK](../tabs/how-to/using-teams-client-sdk.md) auf, um die Kommunikation zwischen Ihrer App und Microsoft Teams herzustellen.</span><span class="sxs-lookup"><span data-stu-id="71afa-168">It calls the [Microsoft Teams JavaScript client SDK](../tabs/how-to/using-teams-client-sdk.md) to establish communication between your app and Teams.</span></span>
- <span data-ttu-id="71afa-169">`tabs/src/components/Tab.jsx` enthält den Code zum Implementieren der Benutzeroberfläche Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="71afa-169">`tabs/src/components/Tab.jsx` contains the code to implement the UI of your app.</span></span>
- <span data-ttu-id="71afa-170">`tabs/src/components/TabConfig.jsx` enthält den Code zum Implementieren der Benutzeroberfläche, die Ihre App konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="71afa-170">`tabs/src/components/TabConfig.jsx` contains the code to implement the UI that configures your app.</span></span>

<span data-ttu-id="71afa-171">Für die Microsoft Teams-Laufzeit sind mehrere Registerkarten erforderlich, darunter für Datenschutzhinweis, Nutzungsbedingungen und Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="71afa-171">Several tabs are required by the Teams runtime, including the privacy notice, terms of use, and configuration tabs.</span></span>  <span data-ttu-id="71afa-172">Der Code für den Datenschutzhinweis und die Nutzungsbedingungen befindet sich in demselben Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="71afa-172">The code for the privacy notice and terms of use are located in the same directory.</span></span>

<span data-ttu-id="71afa-173">Wenn Sie Cloudfunktionen hinzufügen, werden dem Projekt zusätzliche Verzeichnisse hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="71afa-173">When you add cloud functionality, additional directories are added to the project.</span></span>  <span data-ttu-id="71afa-174">Besonders wichtig: Das `api`-Verzeichnis enthält den Code für alle von Ihnen geschriebenen Azure-Funktionen.</span><span class="sxs-lookup"><span data-stu-id="71afa-174">Most notably, the `api` directory holds the code to any Azure Functions you write.</span></span>

## <a name="run-your-app-locally"></a><span data-ttu-id="71afa-175">Lokales Ausführen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="71afa-175">Run your app locally</span></span>

<span data-ttu-id="71afa-176">Das Microsoft Teams-Toolkit ermöglicht es Ihnen, Ihre App lokal auszuführen.</span><span class="sxs-lookup"><span data-stu-id="71afa-176">Teams Toolkit allows you to run your app locally.</span></span>  <span data-ttu-id="71afa-177">Dies besteht aus mehreren Teilen, die für die Bereitstellung der richtigen, von Microsoft Teams erwarteten Infrastruktur erforderlich sind:</span><span class="sxs-lookup"><span data-stu-id="71afa-177">This consists of several parts that are necessary to provide the correct infrastructure that Teams expects:</span></span>

- <span data-ttu-id="71afa-178">Es wird eine Anwendung bei Azure Active Directory registriert.</span><span class="sxs-lookup"><span data-stu-id="71afa-178">An application is registered with Azure Active Directory.</span></span>  <span data-ttu-id="71afa-179">Diese Anwendung verfügt über Berechtigungen, die mit dem Speicherort, von dem die App geladen wird, und allen Back-End-Ressourcen verknüpft sind, auf die sie zugreift.</span><span class="sxs-lookup"><span data-stu-id="71afa-179">This application has permissions associated with the location that the app is loaded from and any backend resources it accesses.</span></span>
- <span data-ttu-id="71afa-180">Es wird eine Web-API zur Unterstützung von Authentifizierungsaufgaben gehostet, die als Proxy zwischen der App und Azure Active Directory agiert.</span><span class="sxs-lookup"><span data-stu-id="71afa-180">A web API is hosted to assist with authentication tasks, acting as a proxy between the app and Azure Active Directory.</span></span>  <span data-ttu-id="71afa-181">Dies wird über die Azure Functions Core Tools ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="71afa-181">This is run by Azure Functions Core Tools.</span></span>  <span data-ttu-id="71afa-182">Der Zugriff darauf ist über die URL-Adresse `https://localhost:5000` möglich.</span><span class="sxs-lookup"><span data-stu-id="71afa-182">It can be accessed at the URL `https://localhost:5000`.</span></span>
- <span data-ttu-id="71afa-183">Die HTML-, CSS- und JavaScript-Ressourcen, aus denen das Front-End der App besteht, werden in einem lokalen Dienst gehostet.</span><span class="sxs-lookup"><span data-stu-id="71afa-183">The HTML, CSS, and JavaScript resources that make up the front end of the app are hosted on a local service.</span></span> <span data-ttu-id="71afa-184">Der Zugriff darauf ist über `https://localhost:3000` möglich.</span><span class="sxs-lookup"><span data-stu-id="71afa-184">It can be accessed at `https://localhost:3000`.</span></span>
- <span data-ttu-id="71afa-185">Es wird ein App-Manifest generiert und im Entwicklerportal für Microsoft Teams verfügbar gemacht.</span><span class="sxs-lookup"><span data-stu-id="71afa-185">An app manifest is generated and exists in the Developer Portal for Teams.</span></span>  <span data-ttu-id="71afa-186">Microsoft Teams verwendet das App-Manifest, um die verbundenen Clients darüber zu informieren, von wo die App geladen werden soll.</span><span class="sxs-lookup"><span data-stu-id="71afa-186">Teams uses the app manifest to tell connected clients where to load the app from.</span></span>

<span data-ttu-id="71afa-187">Danach kann die App innerhalb des Teams-Clients geladen werden.</span><span class="sxs-lookup"><span data-stu-id="71afa-187">After this is done, the app can be loaded within the Teams client.</span></span>  <span data-ttu-id="71afa-188">Wir verwenden den Microsoft Teams-Webclient, um den HTML-, CSS- und JavaScript-Code in einer standardmäßigen Webentwicklungsumgebung anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="71afa-188">We use the Teams web client so that we can see the HTML, CSS, and JavaScript code within a standard web development environment.</span></span>

### <a name="build-and-run-your-app-locally-in-visual-studio-code"></a><span data-ttu-id="71afa-189">Erstellen und lokales Ausführen der App in Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="71afa-189">Build and run your app locally in Visual Studio Code</span></span>

<span data-ttu-id="71afa-190">So erstellen Sie Ihre App und führen sie lokal aus:</span><span class="sxs-lookup"><span data-stu-id="71afa-190">To build and run your app locally:</span></span>

1. <span data-ttu-id="71afa-191">Drücken Sie in Visual Studio Code **F5**, um die Anwendung im Debugmodus auszuführen.</span><span class="sxs-lookup"><span data-stu-id="71afa-191">From Visual Studio Code, press **F5** to run your application in debug mode.</span></span>

   > <span data-ttu-id="71afa-192">Wenn Sie die App zum ersten Mal ausführen, werden alle Abhängigkeiten heruntergeladen und die App wird erstellt.</span><span class="sxs-lookup"><span data-stu-id="71afa-192">When you run the app for the first time, all dependencies are downloaded and the app is built.</span></span>  <span data-ttu-id="71afa-193">Wenn die Erstellung abgeschlossen ist, wird automatisch ein Browserfenster geöffnet.</span><span class="sxs-lookup"><span data-stu-id="71afa-193">A browser window automatically opens when the build is complete.</span></span>  <span data-ttu-id="71afa-194">Dies kann 3 bis 5 Minuten dauern.</span><span class="sxs-lookup"><span data-stu-id="71afa-194">This can take 3-5 minutes to complete.</span></span>

   <span data-ttu-id="71afa-195">Das Toolkit fordert Sie auf, bei Bedarf ein lokales Zertifikat zu installieren.</span><span class="sxs-lookup"><span data-stu-id="71afa-195">The Toolkit prompts you to install a local certificate if required.</span></span> <span data-ttu-id="71afa-196">Mit diesem Zertifikat kann Microsoft Teams Ihre Anwendung von `https://localhost` laden.</span><span class="sxs-lookup"><span data-stu-id="71afa-196">This certificate allows Teams to load your application from `https://localhost`.</span></span> <span data-ttu-id="71afa-197">Wählen Sie "Ja" aus, wenn das folgende Dialogfenster angezeigt wird:</span><span class="sxs-lookup"><span data-stu-id="71afa-197">Select yes when the following dialog appears:</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/ssl-prompt.png" alt-text="Screenshot mit Dialogfenster zum Installieren eines SSL-Zertifikats, damit Microsoft Teams Ihre Anwendung von localhost laden kann.":::

1. <span data-ttu-id="71afa-199">Ihr Webbrowser beginnt mit der Ausführung der App.</span><span class="sxs-lookup"><span data-stu-id="71afa-199">Your web browser starts to run the app.</span></span> <span data-ttu-id="71afa-200">Wenn Sie aufgefordert werden, Teams Desktop zu öffnen, wählen Sie **"Abbrechen"** aus, um im Browser zu verbleiben.</span><span class="sxs-lookup"><span data-stu-id="71afa-200">If prompted to open Teams desktop, select **Cancel** to remain in the browser.</span></span> <span data-ttu-id="71afa-201">Sie werden möglicherweise auch aufgefordert, zu anderen Zeiten zu Teams Desktop zu wechseln. wählen Sie in diesem Fall die Teams Web-App aus.</span><span class="sxs-lookup"><span data-stu-id="71afa-201">You may also be prompted to switch to Teams desktop at other times; select the Teams web app when this happens.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/launch-web-browser-and-pick-webapp.png" alt-text="Screenshot, der zeigt, wie die Web-Version von Microsoft Teams beim Start ausgewählt wird.":::

1. <span data-ttu-id="71afa-203">Melden Sie sich bei Aufforderung mit Ihrem M365-Konto an.</span><span class="sxs-lookup"><span data-stu-id="71afa-203">Sign in with your M365 account when prompted.</span></span>
1. <span data-ttu-id="71afa-204">Wenn Sie aufgefordert werden, die App in Microsoft Teams zu installieren, drücken Sie **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="71afa-204">When prompted to install the app onto Teams, press **Add**.</span></span>

<span data-ttu-id="71afa-205">Ihre App wird jetzt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="71afa-205">Your app is now displayed:</span></span>

:::image type="content" source="../assets/images/teams-toolkit-v2/react-finished-app.png" alt-text="Screenshot der fertiggestellten App":::

<span data-ttu-id="71afa-207">Sie können normale Debugaktivitäten ausführen, als wäre dies eine andere Webanwendung, z. B. das Festlegen von Haltepunkten.</span><span class="sxs-lookup"><span data-stu-id="71afa-207">You can do normal debugging activities as if this were any other web application, such as setting breakpoints.</span></span> <span data-ttu-id="71afa-208">Die App unterstützt Hot Reloading.</span><span class="sxs-lookup"><span data-stu-id="71afa-208">The app supports hot reloading.</span></span> <span data-ttu-id="71afa-209">Wenn Sie eine Datei innerhalb des Projekts ändern, wird die Seite neu geladen.</span><span class="sxs-lookup"><span data-stu-id="71afa-209">If you change any file within the project, the page will be reloaded.</span></span>

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="71afa-210">Erfahren Sie, was geschieht, wenn Sie Ihre App lokal im Debugger ausführen.</span><span class="sxs-lookup"><span data-stu-id="71afa-210">Learn what happens when you run your app locally in the debugger.</span></span></summary>

<span data-ttu-id="71afa-211">Wenn Sie **F5** drücken, hat das Teams Toolkit Folgendes:</span><span class="sxs-lookup"><span data-stu-id="71afa-211">When you press the **F5** key, the Teams Toolkit:</span></span>

* <span data-ttu-id="71afa-212">Registriert Ihre Anwendung bei Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="71afa-212">Registers your application with Azure Active Directory.</span></span>
* <span data-ttu-id="71afa-213">*Lädt* Ihre App in Teams quer.</span><span class="sxs-lookup"><span data-stu-id="71afa-213">*Sideloads* your app in Teams.</span></span>
* <span data-ttu-id="71afa-214">Startet ihr Anwendungs-Back-End, das lokal mithilfe von [Azure Function Core Tools](/azure/azure-functions/functions-run-local?#start)ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="71afa-214">Starts your application backend running locally using [Azure Function Core Tools](/azure/azure-functions/functions-run-local?#start).</span></span>
* <span data-ttu-id="71afa-215">Startet das lokal gehostete Anwendungs-Front-End.</span><span class="sxs-lookup"><span data-stu-id="71afa-215">Starts your application front-end hosted locally.</span></span>
* <span data-ttu-id="71afa-216">Startet Microsoft Teams in einem Webbrowser mit einem Befehl, um Teams anzuweisen, die Anwendung `https://localhost:3000/tab` querzuladen.</span><span class="sxs-lookup"><span data-stu-id="71afa-216">Starts Microsoft Teams in a web browser with a command to instruct Teams to side load the application from `https://localhost:3000/tab`.</span></span> <span data-ttu-id="71afa-217">Dies ist die im Anwendungsmanifest registrierte URL.</span><span class="sxs-lookup"><span data-stu-id="71afa-217">This is the URL registered in the application manifest.</span></span>

</details>

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="71afa-218">Erfahren Sie, wie Sie häufige Probleme bei dem lokalen Ausführen Ihrer App lösen können.</span><span class="sxs-lookup"><span data-stu-id="71afa-218">Learn how to troubleshoot common issues when running your app locally.</span></span></summary>

<span data-ttu-id="71afa-219">Um Ihre App in Microsoft Teams erfolgreich auszuführen, müssen Sie über ein Microsoft Teams-Konto verfügen, das das Querladen von Apps zulässt.</span><span class="sxs-lookup"><span data-stu-id="71afa-219">To successfully run your app in Teams, you must have a Teams account that allows app sideloading.</span></span> <span data-ttu-id="71afa-220">Weitere Informationen zum Öffnen eines Kontos finden Sie unter [Erforderliche Komponenten](prerequisites.md#enable-sideloading).</span><span class="sxs-lookup"><span data-stu-id="71afa-220">For more information on account opening, see [prerequisites](prerequisites.md#enable-sideloading).</span></span>

</details>

[!INCLUDE [Provision and Deploy your app on Azure](~/includes/get-started/azure-provisioning-instructions.md)]

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="71afa-221">Erfahren Sie, was geschieht, wenn Sie Ihre App in Azure bereitstellen</span><span class="sxs-lookup"><span data-stu-id="71afa-221">Learn what happens when you deployed your app to Azure</span></span></summary>

<span data-ttu-id="71afa-222">Vor der Bereitstellung wurde die Anwendung lokal ausgeführt:</span><span class="sxs-lookup"><span data-stu-id="71afa-222">Before deployment, the application has been running locally:</span></span>

* <span data-ttu-id="71afa-223">Das Back-End unter Verwendung von **Azure Functions Core Tools** ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="71afa-223">The backend runs using **Azure Functions Core Tools**.</span></span>
* <span data-ttu-id="71afa-224">Der HTTP-Endpunkt der Anwendung, an dem Microsoft Teams die Anwendung lädt, wird lokal ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="71afa-224">The application HTTP endpoint, where Microsoft Teams loads the application, runs locally.</span></span>

<span data-ttu-id="71afa-225">Die Bereitstellung umfasst die Bereitstellung von Ressourcen für ein aktives Azure-Abonnement sowie das Bereitstellen oder Hochladen des Back-End- und Front-End-Codes für die Anwendung in Azure.</span><span class="sxs-lookup"><span data-stu-id="71afa-225">Deployment involves provisioning resources on an active Azure subscription and deploying or uploading the backend and frontend code for the application to Azure.</span></span>

* <span data-ttu-id="71afa-226">Das Back-End, wenn es konfiguriert ist, verwendet eine Vielzahl von Azure-Diensten, einschließlich Azure App Service und Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="71afa-226">The backend if configured uses a variety of Azure services, including Azure App Service and Azure Storage.</span></span>
* <span data-ttu-id="71afa-227">Die Front-End-Anwendung wird in einem Azure Storage-Konto bereitgestellt, das für statisches Webhosting konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="71afa-227">The frontend application will be deployed to an Azure Storage account configured for static web hosting.</span></span>

</details>

## <a name="see-also"></a><span data-ttu-id="71afa-228">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="71afa-228">See also</span></span>

* [<span data-ttu-id="71afa-229">Übersicht über Lernprogramme</span><span class="sxs-lookup"><span data-stu-id="71afa-229">Tutorials Overview</span></span>](code-samples.md)
* [<span data-ttu-id="71afa-230">Erstellen einer Unterhaltungs-Bot-App</span><span class="sxs-lookup"><span data-stu-id="71afa-230">Create a conversational bot app</span></span>](first-app-bot.md)
* [<span data-ttu-id="71afa-231">Erstellen einer Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="71afa-231">Create a messaging extension</span></span>](first-message-extension.md)
* [<span data-ttu-id="71afa-232">Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="71afa-232">Code Samples</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples)
