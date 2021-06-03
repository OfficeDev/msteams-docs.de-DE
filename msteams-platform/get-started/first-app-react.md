---
title: Erste Schritte – Erstellen Ihrer ersten Microsoft Teams-App mit React
author: adrianhall
description: Erstellen Sie mithilfe von Microsoft Teams-Toolkit und React schnell eine Microsoft Teams-App, die die Meldung "Hallo, Welt!" anzeigt.
ms.author: adhal
ms.date: 05/27/2021
ms.topic: quickstart
ms.openlocfilehash: 8c6a957dc01cfaac0f8463166a6647d6b18babed
ms.sourcegitcommit: 33a43c61f27ae750776616b2cf90159455d8ba6c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2021
ms.locfileid: "52721836"
---
# <a name="build-and-run-your-first-microsoft-teams-app-with-react"></a><span data-ttu-id="ff4ac-104">Erstellen und Ausführen Ihrer ersten Microsoft Teams-App mit React</span><span class="sxs-lookup"><span data-stu-id="ff4ac-104">Build and run your first Microsoft Teams app with React</span></span>

<span data-ttu-id="ff4ac-105">In diesem Lernprogramm erstellen Sie eine neue Microsoft Teams-Anwendung in React, die eine einfache persönliche App implementiert, um Informationen aus Microsoft Graph abzurufen.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-105">In this tutorial, you will create a new Microsoft Teams app in React that implements a simple personal app to pull information from the Microsoft Graph.</span></span> <span data-ttu-id="ff4ac-106">(Eine *persönliche App* enthält eine Reihe von Registerkarten für die individuelle Verwendung.) Im Rahmen des Lernprogramms erfahren Sie Näheres zur Struktur einer Microsoft Teams-App, das lokale Ausführen einer App und die Bereitstellung der App in Azure.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-106">(A *personal app* includes a set of tabs scoped for individual use.) During the tutorial, you will learn about the structure of a Teams app, how to run an app locally, and how to deploy the app to Azure.</span></span>

<span data-ttu-id="ff4ac-107">In der erstellten App werden grundlegende Benutzerinformationen für den aktuellen Benutzer angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-107">The app that is built displays basic user information for the current user.</span></span>  <span data-ttu-id="ff4ac-108">Wenn die Berechtigung dazu erteilt wurde, stellt die App eine Verbindung mit Microsoft Graph als aktueller Benutzer her, um das vollständige Profil zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-108">When permission is granted, the app will connect to the Microsoft Graph as the current user to get the complete profile.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="ff4ac-109">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="ff4ac-109">Before you begin</span></span>

<span data-ttu-id="ff4ac-110">Stellen Sie sicher, dass Ihre Entwicklungsumgebung eingerichtet ist, indem Sie die [erforderlichen Komponenten](prerequisites.md) installieren.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-110">Make sure your development environment is set up by installing the [prerequisites](prerequisites.md)</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ff4ac-111">Erforderliche Komponenten installieren</span><span class="sxs-lookup"><span data-stu-id="ff4ac-111">Install prerequisites</span></span>](prerequisites.md)

## <a name="create-your-project"></a><span data-ttu-id="ff4ac-112">Erstellen Ihres Projekts</span><span class="sxs-lookup"><span data-stu-id="ff4ac-112">Create your project</span></span>

<span data-ttu-id="ff4ac-113">Verwenden Sie zum Erstellen Ihres ersten Projekts das Microsoft Teams-Toolkit:</span><span class="sxs-lookup"><span data-stu-id="ff4ac-113">Use the Teams Toolkit to create your first project:</span></span>

# <a name="visual-studio-code"></a>[<span data-ttu-id="ff4ac-114">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="ff4ac-114">Visual Studio Code</span></span>](#tab/vscode)

1. <span data-ttu-id="ff4ac-115">Öffnen Sie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-115">Open Visual Studio code.</span></span>
1. <span data-ttu-id="ff4ac-116">Öffnen Sie das Microsoft Teams-Toolkit, indem Sie auf das Microsoft Teams-Symbol in der Randleiste klicken:</span><span class="sxs-lookup"><span data-stu-id="ff4ac-116">Open the Teams Toolkit by selecting the Teams icon in the sidebar:</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="Das Microsoft Teams-Symbol in der Visual Studio Code-Randleiste.":::

1. <span data-ttu-id="ff4ac-118">Klicken Sie auf **Neues Projekt erstellen**.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-118">Select **Create New Project**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project.png" alt-text="Ort des Links „Neues Projekt erstellen“ in der Randleiste des Microsoft Teams-Toolkits.":::

1. <span data-ttu-id="ff4ac-120">Wählen Sie **Neue Microsoft Teams-App erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-120">Select **Create a new Teams app**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-new-project-intro.png" alt-text="Starten des Assistenten für „Neues Projekt erstellen“":::

1. <span data-ttu-id="ff4ac-122">Im Schritt **Funktionen auswählen** ist die Funktion **Registerkarten** bereits ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-122">On the **Select capabilities** step, the **Tab** capability will already be selected.</span></span>  <span data-ttu-id="ff4ac-123">Drücken Sie **OK**.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-123">Press **OK**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-capabilities.png" alt-text="Screenshot, der zeigt, wie Ihrer neuen App Funktionen hinzufügt werden können.":::

1. <span data-ttu-id="ff4ac-125">Wählen Sie im Schritt **Frontend-Hostingtyp** die Option **Azure** aus.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-125">On the **Frontend hosting type** step, select **Azure**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-hosting.png" alt-text="Screenshot, der zeigt, wie das Hosting für Ihre neue App ausgewählt wird.":::

1. <span data-ttu-id="ff4ac-127">Drücken Sie im Schritt **Cloudressourcen** auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-127">On the **Cloud resources** step, press **OK**.</span></span>  <span data-ttu-id="ff4ac-128">Für dieses Lernprogramm werden keine zusätzlichen Cloudressourcen benötigt.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-128">We do not need additional cloud resources for this tutorial.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-cloud-resources.png" alt-text="Screenshot, der zeigt, wie Cloudressourcen für Ihre neue App hinzugefügt werden.":::

1. <span data-ttu-id="ff4ac-130">Wählen Sie im Schritt **Programmiersprache** die Option **JavaScript** aus.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-130">On the **Programming Language** step, select **JavaScript**.</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-programming-languages.png" alt-text="Screenshot, der zeigt, wie die Programmiersprache ausgewählt wird.":::

1. <span data-ttu-id="ff4ac-132">Wählen Sie einen Arbeitsbereichsordner aus.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-132">Select a workspace folder.</span></span>  <span data-ttu-id="ff4ac-133">Innerhalb Ihres Arbeitsbereichsordners wird für das von Ihnen erstellte Projekt ein Ordner erstellt.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-133">A folder will be created within your workspace folder for the project you are creating.</span></span>

1. <span data-ttu-id="ff4ac-134">Geben Sie einen passenden Namen für Ihre App ein, wie z. B. `helloworld`.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-134">Enter a suitable name for your app, like `helloworld`.</span></span>  <span data-ttu-id="ff4ac-135">Der Name der App darf nur aus alphanumerischen Zeichen bestehen.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-135">The name of the app must consist only of alphanumeric characters.</span></span>  <span data-ttu-id="ff4ac-136">Drücken Sie die **EINGABETASTE**, um fortzufahren.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-136">Press **Enter** to continue.</span></span>

<span data-ttu-id="ff4ac-137">Ihre Microsoft Teams-App wird innerhalb weniger Sekunden erstellt.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-137">Your Teams app will be created within a few seconds.</span></span>

# <a name="command-line"></a>[<span data-ttu-id="ff4ac-138">Befehlszeile</span><span class="sxs-lookup"><span data-stu-id="ff4ac-138">Command line</span></span>](#tab/cli)

<span data-ttu-id="ff4ac-139">Verwenden Sie die `teamsfx`-CLI zum Erstellen Ihres ersten Projekts.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-139">Use the `teamsfx` CLI to create your first project.</span></span>  <span data-ttu-id="ff4ac-140">Beginnen Sie in dem Ordner, in dem Sie den Projektordner erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-140">Start from the folder where you want to create the project folder.</span></span>

``` bash
teamsfx new
```

<span data-ttu-id="ff4ac-141">Die CLI führt durch einige Fragen zum Erstellen des Projekts.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-141">The CLI walks through some questions to create the project.</span></span>  <span data-ttu-id="ff4ac-142">Bei jeder Frage wird angegeben, wie Sie sie beantworten können (z. B. mithilfe von Pfeiltasten, um eine Option auszuwählen).</span><span class="sxs-lookup"><span data-stu-id="ff4ac-142">Each question will tell you how to answer it (for example, to use arrow keys to select an option).</span></span>  <span data-ttu-id="ff4ac-143">Wenn Sie eine Frage beantwortet haben, bestätigen Sie Ihre Auswahl, indem Sie die **EINGABETASTE** drücken.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-143">When you have answered the question, confirm your choice by pressing **Enter**.</span></span>

1. <span data-ttu-id="ff4ac-144">Wählen Sie **Neue Microsoft Teams-App erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-144">Select **Create a new Teams app**.</span></span>
1. <span data-ttu-id="ff4ac-145">Wählen Sie die Funktion **Registerkarte** aus.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-145">Choose the **Tab** capability.</span></span>
1. <span data-ttu-id="ff4ac-146">Wählen Sie **Azure**-Frontend-Hosting aus.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-146">Select **Azure** frontend hosting.</span></span>
1. <span data-ttu-id="ff4ac-147">Wählen Sie keine Cloudressourcen aus.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-147">Do not select any cloud resources.</span></span>
1. <span data-ttu-id="ff4ac-148">Wählen Sie **JavaScript** als Programmiersprache aus.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-148">Select **JavaScript** as the programming language.</span></span>
1. <span data-ttu-id="ff4ac-149">Drücken Sie die **EINGABETASTE**, um den Standardordner des Arbeitsbereichs auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-149">Press **Enter** to select the default workspace folder.</span></span>
1. <span data-ttu-id="ff4ac-150">Geben Sie einen passenden Namen für Ihre App ein, wie z. B. `helloworld`.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-150">Enter a suitable name for your app, like `helloworld`.</span></span>  <span data-ttu-id="ff4ac-151">Der Name der App darf nur aus alphanumerischen Zeichen bestehen.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-151">The name of the app must consist only of alphanumeric characters.</span></span>

<span data-ttu-id="ff4ac-152">Sobald alle Fragen beantwortet wurden, wird Ihr Projekt erstellt.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-152">Once all the questions have been answered, your project will be created.</span></span>

---

## <a name="take-a-tour-of-the-source-code"></a><span data-ttu-id="ff4ac-153">Machen Sie einen Rundgang durch den Quellcode</span><span class="sxs-lookup"><span data-stu-id="ff4ac-153">Take a tour of the source code</span></span>

<span data-ttu-id="ff4ac-154">Wenn Sie diesen Abschnitt vorerst überspringen möchten, können Sie [Ihre App lokal ausführen](#run-your-app-locally).</span><span class="sxs-lookup"><span data-stu-id="ff4ac-154">If you wish to skip this section for now, you can [run your app locally](#run-your-app-locally).</span></span>

<span data-ttu-id="ff4ac-155">Nachdem das Microsoft Teams Toolkit Ihr Projekt konfiguriert hat, verfügen Sie über die Komponenten zum Erstellen einer einfachen persönlichen App für Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-155">Once the Teams Toolkit configures your project, you have the components to build a basic personal app for Teams.</span></span> <span data-ttu-id="ff4ac-156">Die Projektverzeichnisse und -dateien werden im Explorer-Bereich von Visual Studio Code angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-156">The project directories and files display in the Explorer area of Visual Studio Code.</span></span>

:::image type="content" source="../assets/images/teams-toolkit-v2/react-app-project.png" alt-text="Screenshot der App-Projektdateien für eine persönliche App in Visual Studio Code":::

<span data-ttu-id="ff4ac-158">Das Toolkit erstellt im Projektverzeichnis automatisch Ordner basierend auf den Funktionen, die Sie während des Setups hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-158">The Toolkit automatically creates scaffolding for you in the project directory based on the capabilities you added during setup.</span></span> <span data-ttu-id="ff4ac-159">Das Microsoft Teams Toolkit behält seinen Status für Ihre App im `.fx`-Verzeichnis bei.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-159">The Teams Toolkit maintains its state for your app in the `.fx` directory.</span></span>  <span data-ttu-id="ff4ac-160">Weitere Elemente in diesem Verzeichnis:</span><span class="sxs-lookup"><span data-stu-id="ff4ac-160">Among other items in this directory:</span></span>

- <span data-ttu-id="ff4ac-161">Die App-Symbole werden als PNG-Dateien in `color.png` und `outline.png` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-161">The app icons are stored as PNG files in `color.png` and `outline.png`.</span></span>
- <span data-ttu-id="ff4ac-162">Das App-Manifest für die Veröffentlichung im Entwicklerportal für Microsoft Teams wird in `manifest.source.json` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-162">The app manifest for publishing to the Developer Portal for Teams is stored in `manifest.source.json`.</span></span>
- <span data-ttu-id="ff4ac-163">Die Einstellungen, die Sie beim Erstellen des Projekts ausgewählt haben, werden in `settings.json` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-163">The settings you chose when creating the project are stored in `settings.json`.</span></span>

<span data-ttu-id="ff4ac-164">Da Sie während des Setups die Registerkartenfunktion ausgewählt haben, erstellt das Microsoft Teams-Toolkit den erforderlichen Code für eine einfache Registerkarte im `tabs`-Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-164">Since you selected the tab capability during setup, the Teams Toolkit scaffolds all the necessary code for a basic tab in the `tabs` directory.</span></span> <span data-ttu-id="ff4ac-165">In diesem Verzeichnis befinden sich mehrere wichtige Dateien:</span><span class="sxs-lookup"><span data-stu-id="ff4ac-165">Within this directory there are several important files:</span></span>

- <span data-ttu-id="ff4ac-166">`tabs/src/index.jsx` ist der Einstiegspunkt der Front-End-App, an dem die `App`-Hauptkomponente mit `ReactDOM.render()` gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-166">`tabs/src/index.jsx` is the front-end app's entry point, where the main `App` component is rendered with `ReactDOM.render()`.</span></span>
- <span data-ttu-id="ff4ac-167">`tabs/src/components/App.jsx` übernimmt das URL-Routing in Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-167">`tabs/src/components/App.jsx` handles URL routing in your app.</span></span> <span data-ttu-id="ff4ac-168">Es ruft das [Microsoft Teams JavaScript-Client-SDK](../tabs/how-to/using-teams-client-sdk.md) auf, um die Kommunikation zwischen Ihrer App und Microsoft Teams herzustellen.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-168">It calls the [Microsoft Teams JavaScript client SDK](../tabs/how-to/using-teams-client-sdk.md) to establish communication between your app and Teams.</span></span>
- <span data-ttu-id="ff4ac-169">`tabs/src/components/Tab.jsx` enthält den Code zum Implementieren der Benutzeroberfläche Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-169">`tabs/src/components/Tab.jsx` contains the code to implement the UI of your app.</span></span>
- <span data-ttu-id="ff4ac-170">`tabs/src/components/TabConfig.jsx` enthält den Code zum Implementieren der Benutzeroberfläche, die Ihre App konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-170">`tabs/src/components/TabConfig.jsx` contains the code to implement the UI that configures your app.</span></span>

<span data-ttu-id="ff4ac-171">Für die Microsoft Teams-Laufzeit sind mehrere Registerkarten erforderlich, darunter für Datenschutzhinweis, Nutzungsbedingungen und Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-171">Several tabs are required by the Teams runtime, including the privacy notice, terms of use, and configuration tabs.</span></span>  <span data-ttu-id="ff4ac-172">Der Code für den Datenschutzhinweis und die Nutzungsbedingungen befindet sich in demselben Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-172">The code for the privacy notice and terms of use are located in the same directory.</span></span>

<span data-ttu-id="ff4ac-173">Wenn Sie Cloudfunktionen hinzufügen, werden dem Projekt zusätzliche Verzeichnisse hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-173">When you add cloud functionality, additional directories are added to the project.</span></span>  <span data-ttu-id="ff4ac-174">Besonders wichtig: Das `api`-Verzeichnis enthält den Code für alle von Ihnen geschriebenen Azure-Funktionen.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-174">Most notably, the `api` directory holds the code to any Azure Functions you write.</span></span>

## <a name="run-your-app-locally"></a><span data-ttu-id="ff4ac-175">Lokales Ausführen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="ff4ac-175">Run your app locally</span></span>

<span data-ttu-id="ff4ac-176">Das Microsoft Teams-Toolkit ermöglicht es Ihnen, Ihre App lokal auszuführen.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-176">Teams Toolkit allows you to run your app locally.</span></span>  <span data-ttu-id="ff4ac-177">Dies besteht aus mehreren Teilen, die für die Bereitstellung der richtigen, von Microsoft Teams erwarteten Infrastruktur erforderlich sind:</span><span class="sxs-lookup"><span data-stu-id="ff4ac-177">This consists of several parts that are necessary to provide the correct infrastructure that Teams expects:</span></span>

- <span data-ttu-id="ff4ac-178">Es wird eine Anwendung bei Azure Active Directory registriert.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-178">An application is registered with Azure Active Directory.</span></span>  <span data-ttu-id="ff4ac-179">Diese Anwendung verfügt über Berechtigungen, die mit dem Speicherort, von dem die App geladen wird, und allen Back-End-Ressourcen verknüpft sind, auf die sie zugreift.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-179">This application has permissions associated with the location that the app is loaded from and any backend resources it accesses.</span></span>
- <span data-ttu-id="ff4ac-180">Es wird eine Web-API zur Unterstützung von Authentifizierungsaufgaben gehostet, die als Proxy zwischen der App und Azure Active Directory agiert.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-180">A web API is hosted to assist with authentication tasks, acting as a proxy between the app and Azure Active Directory.</span></span>  <span data-ttu-id="ff4ac-181">Dies wird über die Azure Functions Core Tools ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-181">This is run by Azure Functions Core Tools.</span></span>  <span data-ttu-id="ff4ac-182">Der Zugriff darauf ist über die URL-Adresse `https://localhost:5000` möglich.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-182">It can be accessed at the URL `https://localhost:5000`.</span></span>
- <span data-ttu-id="ff4ac-183">Die HTML-, CSS- und JavaScript-Ressourcen, aus denen das Front-End der App besteht, werden in einem lokalen Dienst gehostet.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-183">The HTML, CSS, and JavaScript resources that make up the front end of the app are hosted on a local service.</span></span> <span data-ttu-id="ff4ac-184">Der Zugriff darauf ist über `https://localhost:3000` möglich.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-184">It can be accessed at `https://localhost:3000`.</span></span>
- <span data-ttu-id="ff4ac-185">Es wird ein App-Manifest generiert und im Entwicklerportal für Microsoft Teams verfügbar gemacht.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-185">An app manifest is generated and exists in the Developer Portal for Teams.</span></span>  <span data-ttu-id="ff4ac-186">Microsoft Teams verwendet das App-Manifest, um die verbundenen Clients darüber zu informieren, von wo die App geladen werden soll.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-186">Teams uses the app manifest to tell connected clients where to load the app from.</span></span>

<span data-ttu-id="ff4ac-187">Sobald dies erfolgt ist, kann die App im Microsoft Teams-Client geladen werden.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-187">Once this is done, the app can be loaded within the Teams client.</span></span>  <span data-ttu-id="ff4ac-188">Wir verwenden den Microsoft Teams-Webclient, um den HTML-, CSS- und JavaScript-Code in einer standardmäßigen Webentwicklungsumgebung anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-188">We use the Teams web client so that we can see the HTML, CSS, and JavaScript code within a standard web development environment.</span></span>

### <a name="build-and-run-your-app-locally-in-visual-studio-code"></a><span data-ttu-id="ff4ac-189">Erstellen und lokales Ausführen der App in Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="ff4ac-189">Build and run your app locally in Visual Studio Code</span></span>

<span data-ttu-id="ff4ac-190">So erstellen Sie Ihre App und führen sie lokal aus:</span><span class="sxs-lookup"><span data-stu-id="ff4ac-190">To build and run your app locally:</span></span>

1. <span data-ttu-id="ff4ac-191">Drücken Sie in Visual Studio Code **F5**, um die Anwendung im Debugmodus auszuführen.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-191">From Visual Studio Code, press **F5** to run your application in debug mode.</span></span>

   > <span data-ttu-id="ff4ac-192">Wenn Sie die App zum ersten Mal ausführen, werden alle Abhängigkeiten heruntergeladen und die App wird erstellt.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-192">When you run the app for the first time, all dependencies are downloaded and the app is built.</span></span>  <span data-ttu-id="ff4ac-193">Wenn die Erstellung abgeschlossen ist, wird automatisch ein Browserfenster geöffnet.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-193">A browser window automatically opens when the build is complete.</span></span>  <span data-ttu-id="ff4ac-194">Dies kann 3 bis 5 Minuten dauern.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-194">This can take 3-5 minutes to complete.</span></span>

   <span data-ttu-id="ff4ac-195">Sie werden vom Toolkit aufgefordert, bei Bedarf ein lokales Zertifikat zu installieren.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-195">The Toolkit will prompt you to install a local certificate if needed.</span></span> <span data-ttu-id="ff4ac-196">Mit diesem Zertifikat kann Microsoft Teams Ihre Anwendung von `https://localhost` laden.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-196">This certificate allows Teams to load your application from `https://localhost`.</span></span> <span data-ttu-id="ff4ac-197">Wählen Sie "Ja" aus, wenn das folgende Dialogfenster angezeigt wird:</span><span class="sxs-lookup"><span data-stu-id="ff4ac-197">Select yes when the following dialog appears:</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/ssl-prompt.png" alt-text="Screenshot mit Dialogfenster zum Installieren eines SSL-Zertifikats, damit Microsoft Teams Ihre Anwendung von localhost laden kann.":::

1. <span data-ttu-id="ff4ac-199">Ihr Webbrowser startet mit der Ausführung der App.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-199">Your web browser starts to run the app.</span></span> <span data-ttu-id="ff4ac-200">Wenn Sie aufgefordert werden, Teams desktop zu öffnen, wählen **Sie Abbrechen** aus, um im Browser zu verbleiben.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-200">If prompted to open Teams desktop, select **Cancel** to remain in the browser.</span></span> <span data-ttu-id="ff4ac-201">Sie werden möglicherweise auch aufgefordert, zu anderen Teams zu wechseln. wählen Sie Teams Web-App aus, wenn dies geschieht.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-201">You may also be prompted to switch to Teams desktop at other times; select the Teams web app when this happens.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/launch-web-browser-and-pick-webapp.png" alt-text="Screenshot, der zeigt, wie die Web-Version von Microsoft Teams beim Start ausgewählt wird.":::

1. <span data-ttu-id="ff4ac-203">Möglicherweise werden Sie aufgefordert, sich anzumelden.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-203">You may be prompted to sign in.</span></span>  <span data-ttu-id="ff4ac-204">Melden Sie sich in diesem Fall mit Ihrem M365-Konto an.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-204">If so, sign in with your M365 account.</span></span>
1. <span data-ttu-id="ff4ac-205">Wenn Sie aufgefordert werden, die App in Microsoft Teams zu installieren, drücken Sie **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-205">When prompted to install the app onto Teams, press **Add**.</span></span>

<span data-ttu-id="ff4ac-206">Ihre App wird nun angezeigt:</span><span class="sxs-lookup"><span data-stu-id="ff4ac-206">Your app will now be displayed:</span></span>

:::image type="content" source="../assets/images/teams-toolkit-v2/react-finished-app.png" alt-text="Screenshot der fertiggestellten App":::

<span data-ttu-id="ff4ac-208">Sie können normale Debugaktivitäten wie bei jeder anderen Webanwendung ausführen (z. B. Haltepunkte festlegen).</span><span class="sxs-lookup"><span data-stu-id="ff4ac-208">You can do normal debugging activities as if this were any other web application (such as setting breakpoints).</span></span> <span data-ttu-id="ff4ac-209">Die App unterstützt Hot Reloading.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-209">The app supports hot reloading.</span></span>  <span data-ttu-id="ff4ac-210">Wenn Sie eine Datei innerhalb des Projekts ändern, wird die Seite neu geladen.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-210">If you change any file within the project, the page will be reloaded.</span></span>

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="ff4ac-211">Erfahren Sie, was geschieht, wenn Sie Ihre App lokal im Debugger ausführen.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-211">Learn what happens when you run your app locally in the debugger.</span></span></summary>

<span data-ttu-id="ff4ac-212">Wenn Sie F5 gedrückt haben, hat das Microsoft Teams-Toolkit Folgendes getan:</span><span class="sxs-lookup"><span data-stu-id="ff4ac-212">When you pressed F5, the Teams Toolkit:</span></span>

1. <span data-ttu-id="ff4ac-213">Ihre Anwendung bei Azure Active Directory registriert</span><span class="sxs-lookup"><span data-stu-id="ff4ac-213">Registered your application with Azure Active Directory.</span></span>
1. <span data-ttu-id="ff4ac-214">Ihre Anwendung in Microsoft Teams *quergeladen*</span><span class="sxs-lookup"><span data-stu-id="ff4ac-214">*Sideloaded* your app in Teams.</span></span>
1. <span data-ttu-id="ff4ac-215">Ihr Anwendungs-Back-End mithilfe von [Azure Function Core Tools](/azure/azure-functions/functions-run-local?#start) lokal gestartet</span><span class="sxs-lookup"><span data-stu-id="ff4ac-215">Started your application backend running locally using [Azure Function Core Tools](/azure/azure-functions/functions-run-local?#start).</span></span>
1. <span data-ttu-id="ff4ac-216">Das lokal gehostete Anwendungs-Front-End gestartet</span><span class="sxs-lookup"><span data-stu-id="ff4ac-216">Started your application front-end hosted locally.</span></span>
1. <span data-ttu-id="ff4ac-217">Microsoft Teams in einem Webbrowser mit der Anweisung gestartet, die App von `https://localhost:3000/tab` (die im Anwendungsmanifest registrierte URL) querzuladen.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-217">Started Microsoft Teams in a web browser with a command to instruct Teams to side load the application from `https://localhost:3000/tab` (the URL is registered inside the application manifest).</span></span>

</details>

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="ff4ac-218">Erfahren Sie, wie Sie häufige Probleme bei dem lokalen Ausführen Ihrer App lösen können.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-218">Learn how to troubleshoot common issues when running your app locally.</span></span></summary>

<span data-ttu-id="ff4ac-219">Um Ihre App in Microsoft Teams erfolgreich auszuführen, müssen Sie über ein Microsoft Teams-Konto verfügen, das das Querladen von Apps zulässt.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-219">To successfully run your app in Teams, you must have a Teams account that allows app sideloading.</span></span> <span data-ttu-id="ff4ac-220">Weitere Informationen zum Öffnen eines Kontos finden Sie unter [Erforderliche Komponenten](prerequisites.md#enable-sideloading).</span><span class="sxs-lookup"><span data-stu-id="ff4ac-220">For more information on account opening, see [prerequisites](prerequisites.md#enable-sideloading).</span></span>

</details>

[!INCLUDE [Provision and Deploy your app on Azure](~/includes/get-started/azure-provisioning-instructions.md)]

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="ff4ac-221">Erfahren Sie, was geschieht, wenn Sie Ihre App in Azure bereitstellen</span><span class="sxs-lookup"><span data-stu-id="ff4ac-221">Learn what happens when you deployed your app to Azure</span></span></summary>

<span data-ttu-id="ff4ac-222">Vor der Bereitstellung wurde die Anwendung lokal ausgeführt:</span><span class="sxs-lookup"><span data-stu-id="ff4ac-222">Before deployment, the application has been running locally:</span></span>

1. <span data-ttu-id="ff4ac-223">Das Back-End unter Verwendung von _Azure Functions Core Tools_ ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-223">The backend runs using _Azure Functions Core Tools_.</span></span>
1. <span data-ttu-id="ff4ac-224">Der HTTP-Endpunkt der Anwendung, an dem Microsoft Teams die Anwendung lädt, wird lokal ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-224">The application HTTP endpoint, where Microsoft Teams loads the application, runs locally.</span></span>

<span data-ttu-id="ff4ac-225">Die Bereitstellung umfasst das Bereitstellen von Ressourcen für ein aktives Azure-Abonnement und das Bereitstellen (Hochladen) des Back-End- und des Frontend-Codes für die Anwendung in Azure.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-225">Deployment involves provisioning resources on an active Azure subscription and deploying (uploading) the backend and frontend code for the application to Azure.</span></span>

1. <span data-ttu-id="ff4ac-226">Das Back-End (sofern konfiguriert) nutzt eine Vielzahl von Azure-Diensten, einschließlich Azure App Service und Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-226">The backend (if configured) uses a variety of Azure services, including Azure App Service and Azure Storage.</span></span>
1. <span data-ttu-id="ff4ac-227">Die Front-End-Anwendung wird in einem Azure Storage-Konto bereitgestellt, das für statisches Webhosting konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="ff4ac-227">The frontend application will be deployed to an Azure Storage account configured for static web hosting.</span></span>

</details>

## <a name="next-steps"></a><span data-ttu-id="ff4ac-228">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="ff4ac-228">Next steps</span></span>

<span data-ttu-id="ff4ac-229">Informationen zu anderen Methoden zum Erstellen von Microsoft Teams-Apps finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="ff4ac-229">Learn about other methods for creating Teams apps:</span></span>

- [<span data-ttu-id="ff4ac-230">Erstellen einer Microsoft Teams-App mit Blazor</span><span class="sxs-lookup"><span data-stu-id="ff4ac-230">Create a Teams app with Blazor</span></span>](first-app-blazor.md)
- <span data-ttu-id="ff4ac-231">[Erstellen einer Microsoft Teams-App als SharePoint-Webpart](first-app-spfx.md) (Azure nicht erforderlich)</span><span class="sxs-lookup"><span data-stu-id="ff4ac-231">[Create a Teams app as a SharePoint Web Part](first-app-spfx.md) (Azure not required)</span></span>
- [<span data-ttu-id="ff4ac-232">Erstellen einer Unterhaltungs-Bot-App</span><span class="sxs-lookup"><span data-stu-id="ff4ac-232">Create a conversational bot app</span></span>](first-app-bot.md)
- [<span data-ttu-id="ff4ac-233">Erstellen einer Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="ff4ac-233">Create a messaging extension</span></span>](first-message-extension.md)
