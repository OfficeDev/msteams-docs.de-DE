---
title: Erste Schritte – Erstellen Ihrer ersten Teams-App mit SPFx
author: zhenyasav
description: Erfahren Sie, wie Sie eine benutzerdefinierte Registerkarte mit dem SharePoint-Framework erstellen
ms.author: zhenyasa
ms.date: 05/19/2021
ms.topic: quickstart
ms.openlocfilehash: 23df721a28225a8c453274e6e77efa8f756e84f3
ms.sourcegitcommit: 14409950307b135265c8582408be5277b35131dd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2021
ms.locfileid: "52994371"
---
# <a name="build-and-run-your-first-microsoft-teams-app-with-sharepoint-framework-spfx"></a><span data-ttu-id="1f983-103">Erstellen und Ausführen Ihrer ersten Microsoft Teams-App mit SharePoint Framework (SPFx)</span><span class="sxs-lookup"><span data-stu-id="1f983-103">Build and run your first Microsoft Teams app with SharePoint Framework (SPFx)</span></span>

<span data-ttu-id="1f983-104">In diesem Lernprogramm erstellen Sie eine neue Microsoft Teams-App in SharePoint Framework (SPFx), die eine einfache persönliche App implementiert.</span><span class="sxs-lookup"><span data-stu-id="1f983-104">In this tutorial, you will create a new Microsoft Teams app in SharePoint Framework (SPFx) that implements a simple personal app.</span></span> <span data-ttu-id="1f983-105">(Eine *persönliche App* enthält eine Reihe von Registerkarten, die für die individuelle Verwendung vorgesehen sind.) Während des Lernprogramms erfahren Sie mehr über die Struktur einer Teams-App, wie Sie die App lokal ausführen und wie Sie die App in SharePoint bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="1f983-105">(A *personal app* includes a set of tabs scoped for individual use.) During the tutorial, you will learn about the structure of a Teams app, how to run the app locally, and how to deploy the app to SharePoint.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="1f983-106">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="1f983-106">Before you begin</span></span>

<span data-ttu-id="1f983-107">Stellen Sie sicher, dass Ihre Entwicklungsumgebung eingerichtet ist, indem Sie die [erforderlichen Komponenten](prerequisites.md) installieren.</span><span class="sxs-lookup"><span data-stu-id="1f983-107">Make sure your development environment is set up by installing the [prerequisites](prerequisites.md)</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1f983-108">Erforderliche Komponenten installieren</span><span class="sxs-lookup"><span data-stu-id="1f983-108">Install prerequisites</span></span>](prerequisites.md)

## <a name="get-organized"></a><span data-ttu-id="1f983-109">Besser organisiert sein</span><span class="sxs-lookup"><span data-stu-id="1f983-109">Get organized</span></span>

<span data-ttu-id="1f983-110">Zusätzlich zu den Voraussetzungen müssen Sie auch Administrator für eine SharePoint-Websitesammlung sein.</span><span class="sxs-lookup"><span data-stu-id="1f983-110">In addition to the prerequisites, you also need to be an Administrator for a SharePoint Site Collection.</span></span>  <span data-ttu-id="1f983-111">Hier stellen Sie Ihre App für das Hosting bereit.</span><span class="sxs-lookup"><span data-stu-id="1f983-111">This is where you will deploy your app for hosting.</span></span>  <span data-ttu-id="1f983-112">Wenn Sie einen Mandanten des M365-Entwicklerprogramms verwenden, verwenden Sie das Administratorkonto, das Sie bei der Registrierung für das Programm eingerichtet haben.</span><span class="sxs-lookup"><span data-stu-id="1f983-112">If you are using an M365 developer program tenant, use the administrator account you set up when you registered for the program.</span></span>  

## <a name="create-your-project"></a><span data-ttu-id="1f983-113">Erstellen Ihres Projekts</span><span class="sxs-lookup"><span data-stu-id="1f983-113">Create your project</span></span>

<span data-ttu-id="1f983-114">Verwenden Sie zum Erstellen Ihres ersten Projekts das Microsoft Teams-Toolkit:</span><span class="sxs-lookup"><span data-stu-id="1f983-114">Use the Teams Toolkit to create your first project:</span></span>

# <a name="visual-studio-code"></a>[<span data-ttu-id="1f983-115">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="1f983-115">Visual Studio Code</span></span>](#tab/vscode)

1. <span data-ttu-id="1f983-116">Öffnen Sie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="1f983-116">Open Visual Studio code.</span></span>
1. <span data-ttu-id="1f983-117">Öffnen Sie das Microsoft Teams-Toolkit, indem Sie auf das Microsoft Teams-Symbol in der Randleiste klicken:</span><span class="sxs-lookup"><span data-stu-id="1f983-117">Open the Teams Toolkit by selecting the Teams icon in the sidebar:</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="Das Microsoft Teams-Symbol in der Visual Studio Code-Randleiste.":::

1. <span data-ttu-id="1f983-119">Klicken Sie auf **Neues Projekt erstellen**.</span><span class="sxs-lookup"><span data-stu-id="1f983-119">Select **Create New Project**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project.png" alt-text="Ort des Links „Neues Projekt erstellen“ in der Randleiste des Microsoft Teams-Toolkits.":::

1. <span data-ttu-id="1f983-121">Wählen Sie **Neue Microsoft Teams-App erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="1f983-121">Select **Create a new Teams app**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-new-project-intro.png" alt-text="Starten des Assistenten für „Neues Projekt erstellen“":::

1. <span data-ttu-id="1f983-123">Im Schritt **Funktionen auswählen** ist die Funktion **Registerkarten** bereits ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="1f983-123">On the **Select capabilities** step, the **Tab** capability will already be selected.</span></span>  <span data-ttu-id="1f983-124">Drücken Sie **OK**.</span><span class="sxs-lookup"><span data-stu-id="1f983-124">Press **OK**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-capabilities.png" alt-text="Screenshot, der zeigt, wie Ihrer neuen App Funktionen hinzufügt werden können.":::

1. <span data-ttu-id="1f983-126">Wählen Sie im **Frontend-Hostingtypschritt** **SharePoint Framework (SPFx)** aus.</span><span class="sxs-lookup"><span data-stu-id="1f983-126">On the **Frontend hosting type** step, select **SharePoint Framework (SPFx)**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-hosting.png" alt-text="Screenshot, der zeigt, wie das Hosting für Ihre neue App ausgewählt wird.":::

1. <span data-ttu-id="1f983-128">Wählen Sie im **Schritt "Framework"** **react** aus.</span><span class="sxs-lookup"><span data-stu-id="1f983-128">On the **Framework** step, select **React**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-which-framework.png" alt-text="Auswählen des Frameworks":::

1. <span data-ttu-id="1f983-130">Wenn Sie nach einem **Webpartnamen** gefragt werden, drücken Sie die **EINGABETASTE,** um die Standardeinstellung zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="1f983-130">When asked for a **Webpart Name**, press **Enter** to accept the default.</span></span>

1. <span data-ttu-id="1f983-131">Wenn Sie nach der **Webpartbeschreibung** gefragt werden, drücken Sie die **EINGABETASTE,** um die Standardeinstellung zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="1f983-131">When asked for the **Webpart Description**, press **Enter** to accept the default.</span></span>

1. <span data-ttu-id="1f983-132">Wenn Sie nach der **Programmiersprache** gefragt werden, drücken Sie die **EINGABETASTE,** um die Standardeinstellung zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="1f983-132">When asked for the **Programming Language**, press **Enter** to accept the default.</span></span>

1. <span data-ttu-id="1f983-133">Wählen Sie einen Arbeitsbereichsordner aus.</span><span class="sxs-lookup"><span data-stu-id="1f983-133">Select a workspace folder.</span></span>  <span data-ttu-id="1f983-134">Innerhalb Ihres Arbeitsbereichsordners wird für das von Ihnen erstellte Projekt ein Ordner erstellt.</span><span class="sxs-lookup"><span data-stu-id="1f983-134">A folder will be created within your workspace folder for the project you are creating.</span></span>

1. <span data-ttu-id="1f983-135">Geben Sie einen passenden Namen für Ihre App ein, wie z. B. `helloworld`.</span><span class="sxs-lookup"><span data-stu-id="1f983-135">Enter a suitable name for your app, like `helloworld`.</span></span>  <span data-ttu-id="1f983-136">Der Name der App darf nur aus alphanumerischen Zeichen bestehen.</span><span class="sxs-lookup"><span data-stu-id="1f983-136">The name of the app must consist only of alphanumeric characters.</span></span>  <span data-ttu-id="1f983-137">Drücken Sie die **EINGABETASTE**, um fortzufahren.</span><span class="sxs-lookup"><span data-stu-id="1f983-137">Press **Enter** to continue.</span></span>

<span data-ttu-id="1f983-138">Ihre Microsoft Teams-App wird innerhalb weniger Sekunden erstellt.</span><span class="sxs-lookup"><span data-stu-id="1f983-138">Your Teams app will be created within a few seconds.</span></span>

# <a name="command-line"></a>[<span data-ttu-id="1f983-139">Befehlszeile</span><span class="sxs-lookup"><span data-stu-id="1f983-139">Command line</span></span>](#tab/cli)

<span data-ttu-id="1f983-140">Verwenden Sie die `teamsfx`-CLI zum Erstellen Ihres ersten Projekts.</span><span class="sxs-lookup"><span data-stu-id="1f983-140">Use the `teamsfx` CLI to create your first project.</span></span>  <span data-ttu-id="1f983-141">Beginnen Sie in dem Ordner, in dem Sie den Projektordner erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="1f983-141">Start from the folder where you want to create the project folder.</span></span>

``` bash
teamsfx new
```

<span data-ttu-id="1f983-142">Die CLI führt durch einige Fragen zum Erstellen des Projekts.</span><span class="sxs-lookup"><span data-stu-id="1f983-142">The CLI walks through some questions to create the project.</span></span>  <span data-ttu-id="1f983-143">Bei jeder Frage wird angegeben, wie Sie sie beantworten können (z. B. mithilfe von Pfeiltasten, um eine Option auszuwählen).</span><span class="sxs-lookup"><span data-stu-id="1f983-143">Each question will tell you how to answer it (for example, to use arrow keys to select an option).</span></span>  <span data-ttu-id="1f983-144">Wenn Sie eine Frage beantwortet haben, bestätigen Sie Ihre Auswahl, indem Sie die **EINGABETASTE** drücken.</span><span class="sxs-lookup"><span data-stu-id="1f983-144">When you have answered the question, confirm your choice by pressing **Enter**.</span></span>

1. <span data-ttu-id="1f983-145">Wählen Sie **Neue Microsoft Teams-App erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="1f983-145">Select **Create a new Teams app**.</span></span>
1. <span data-ttu-id="1f983-146">Wählen Sie die Funktion **Registerkarte** aus.</span><span class="sxs-lookup"><span data-stu-id="1f983-146">Choose the **Tab** capability.</span></span>
1. <span data-ttu-id="1f983-147">Wählen Sie **SharePoint Framework (SPFx)-Front-End-Hosting** aus.</span><span class="sxs-lookup"><span data-stu-id="1f983-147">Select **SharePoint Framework (SPFx)** frontend hosting.</span></span>
1. <span data-ttu-id="1f983-148">Wählen Sie **React-Framework** aus.</span><span class="sxs-lookup"><span data-stu-id="1f983-148">Select **React** framework.</span></span>
1. <span data-ttu-id="1f983-149">Drücken Sie die **EINGABETASTE** für den **Webpartnamen.**</span><span class="sxs-lookup"><span data-stu-id="1f983-149">Press **Enter** for the **Webpart Name**.</span></span>
1. <span data-ttu-id="1f983-150">Drücken Sie die **EINGABETASTE** für die **Webpartbeschreibung.**</span><span class="sxs-lookup"><span data-stu-id="1f983-150">Press **Enter** for the **Webpart Description**.</span></span>
1. <span data-ttu-id="1f983-151">Drücken Sie die **EINGABETASTE** für die **Programmiersprache.**</span><span class="sxs-lookup"><span data-stu-id="1f983-151">Press **Enter** for the **Programming Language**.</span></span>
1. <span data-ttu-id="1f983-152">Drücken Sie die **EINGABETASTE**, um den Standardordner des Arbeitsbereichs auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="1f983-152">Press **Enter** to select the default workspace folder.</span></span>
1. <span data-ttu-id="1f983-153">Geben Sie einen passenden Namen für Ihre App ein, wie z. B. `helloworld`.</span><span class="sxs-lookup"><span data-stu-id="1f983-153">Enter a suitable name for your app, like `helloworld`.</span></span>  <span data-ttu-id="1f983-154">Der Name der App darf nur aus alphanumerischen Zeichen bestehen.</span><span class="sxs-lookup"><span data-stu-id="1f983-154">The name of the app must consist only of alphanumeric characters.</span></span>

<span data-ttu-id="1f983-155">Sobald alle Fragen beantwortet wurden, wird Ihr Projekt erstellt.</span><span class="sxs-lookup"><span data-stu-id="1f983-155">Once all the questions have been answered, your project will be created.</span></span>

---

- [<span data-ttu-id="1f983-156">Weitere Informationen zur Entwicklung für SharePoint Framework</span><span class="sxs-lookup"><span data-stu-id="1f983-156">Learn more about developing for SharePoint Framework</span></span>](/sharepoint/dev/spfx/sharepoint-framework-overview)

## <a name="take-a-tour-of-the-source-code"></a><span data-ttu-id="1f983-157">Machen Sie einen Rundgang durch den Quellcode</span><span class="sxs-lookup"><span data-stu-id="1f983-157">Take a tour of the source code</span></span>

<span data-ttu-id="1f983-158">Wenn Sie diesen Abschnitt vorerst überspringen möchten, können Sie [Ihre App lokal ausführen](#run-your-app-locally).</span><span class="sxs-lookup"><span data-stu-id="1f983-158">If you wish to skip this section for now, you can [run your app locally](#run-your-app-locally).</span></span>

<span data-ttu-id="1f983-159">Sobald das Teams-Toolkit Ihr Projekt konfiguriert hat, verfügen Sie über die Komponenten zum Erstellen einer einfachen persönlichen App für Teams, die im SharePoint-Framework gehostet wird.</span><span class="sxs-lookup"><span data-stu-id="1f983-159">Once the Teams Toolkit configures your project, you have the components to build a basic personal app for Teams that is hosted within the SharePoint Framework.</span></span>  <span data-ttu-id="1f983-160">Die Projektverzeichnisse und -dateien werden im Explorer-Bereich von Visual Studio Code angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1f983-160">The project directories and files display in the Explorer area of Visual Studio Code.</span></span>

:::image type="content" source="../assets/images/teams-toolkit-v2/app-project-files-spfx.png" alt-text="Screenshot der App-Projektdateien für eine persönliche App in Visual Studio Code":::

<span data-ttu-id="1f983-162">Das Toolkit erstellt im Projektverzeichnis automatisch Ordner basierend auf den Funktionen, die Sie während des Setups hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="1f983-162">The Toolkit automatically creates scaffolding for you in the project directory based on the capabilities you added during setup.</span></span> <span data-ttu-id="1f983-163">Das Microsoft Teams Toolkit behält seinen Status für Ihre App im `.fx`-Verzeichnis bei.</span><span class="sxs-lookup"><span data-stu-id="1f983-163">The Teams Toolkit maintains its state for your app in the `.fx` directory.</span></span>  <span data-ttu-id="1f983-164">Weitere Elemente in diesem Verzeichnis:</span><span class="sxs-lookup"><span data-stu-id="1f983-164">Among other items in this directory:</span></span>

- <span data-ttu-id="1f983-165">Die App-Symbole werden als PNG-Dateien in `color.png` und `outline.png` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="1f983-165">The app icons are stored as PNG files in `color.png` and `outline.png`.</span></span>
- <span data-ttu-id="1f983-166">Das App-Manifest für die Veröffentlichung im Entwicklerportal für Teams wird in `manifest.source.json` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="1f983-166">The app manifest for publishing to Developer Portal for Teams is stored in `manifest.source.json`.</span></span>
- <span data-ttu-id="1f983-167">Die Einstellungen, die Sie beim Erstellen des Projekts ausgewählt haben, werden in `settings.json` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="1f983-167">The settings you chose when creating the project are stored in `settings.json`.</span></span>

<span data-ttu-id="1f983-168">Da Sie ein SPFx-Webpart-Projekt ausgewählt haben, sind die folgenden Dateien für Ihre Benutzeroberfläche relevant:</span><span class="sxs-lookup"><span data-stu-id="1f983-168">Since you selected an SPFx Webpart project, the following files are relevant to your UI:</span></span>

- <span data-ttu-id="1f983-169">Der Ordner `SPFx/src/webparts/{webpart}` enthält Ihr SPFx-Webpart.</span><span class="sxs-lookup"><span data-stu-id="1f983-169">The folder `SPFx/src/webparts/{webpart}` contains your SPFx webpart.</span></span>
- <span data-ttu-id="1f983-170">Die Datei `.vscode/launch.json` beschreibt die Debugkonfigurationen, die in der Debugpalette verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="1f983-170">The file `.vscode/launch.json` describes the debugging configurations available in the debug palette.</span></span>

<span data-ttu-id="1f983-171">Weitere Informationen zu SharePoint-Webparts für Teams [finden Sie in der SharePoint-Dokumentation.](/sharepoint/dev/spfx/build-for-teams-overview)</span><span class="sxs-lookup"><span data-stu-id="1f983-171">For more information about SharePoint Webparts for Teams, [refer to the SharePoint documentation](/sharepoint/dev/spfx/build-for-teams-overview).</span></span>

## <a name="run-your-app-locally"></a><span data-ttu-id="1f983-172">Lokales Ausführen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="1f983-172">Run your app locally</span></span>

<span data-ttu-id="1f983-173">Mit dem Teams-Toolkit können Sie Ihre App lokal hosten und über die [SharePoint-Framework-Workbench](/sharepoint/dev/spfx/debug-in-vscode)ausführen.</span><span class="sxs-lookup"><span data-stu-id="1f983-173">Teams Toolkit allows you to host your app locally and run it through the [SharePoint Framework Workbench](/sharepoint/dev/spfx/debug-in-vscode).</span></span>

### <a name="build-and-run-your-app-locally-in-visual-studio-code"></a><span data-ttu-id="1f983-174">Erstellen und lokales Ausführen der App in Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="1f983-174">Build and run your app locally in Visual Studio Code</span></span>

<span data-ttu-id="1f983-175">So erstellen Sie Ihre App und führen sie lokal aus:</span><span class="sxs-lookup"><span data-stu-id="1f983-175">To build and run your app locally:</span></span>

1. <span data-ttu-id="1f983-176">Drücken Sie in Visual Studio Code **F5.**</span><span class="sxs-lookup"><span data-stu-id="1f983-176">From Visual Studio Code, press **F5**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-debug-local.png" alt-text="Screenshot, der zeigt, wie Sie eine SPFx-App in einer lokalen Workbench starten.":::

   > [!NOTE]
   > <span data-ttu-id="1f983-178">Wenn Sie die App zum ersten Mal ausführen, werden alle Abhängigkeiten heruntergeladen und die App wird erstellt.</span><span class="sxs-lookup"><span data-stu-id="1f983-178">When you run the app for the first time, all dependencies are downloaded and the app is built.</span></span>  <span data-ttu-id="1f983-179">Ein Browserfenster wird automatisch geöffnet und die SharePoint Workbench geladen, wenn der Build abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="1f983-179">A browser window automatically opens and loads the SharePoint Workbench when the build is complete.</span></span>  <span data-ttu-id="1f983-180">Dies kann 3 bis 5 Minuten dauern.</span><span class="sxs-lookup"><span data-stu-id="1f983-180">This can take 3-5 minutes to complete.</span></span>

   <span data-ttu-id="1f983-181">Nachdem die SharePoint Workbench geladen wurde.</span><span class="sxs-lookup"><span data-stu-id="1f983-181">Once the SharePoint Workbench is loaded.</span></span>

   >[!NOTE]
   > <span data-ttu-id="1f983-182">Sie werden vom Toolkit aufgefordert, bei Bedarf ein lokales Zertifikat zu installieren.</span><span class="sxs-lookup"><span data-stu-id="1f983-182">The Toolkit will prompt you to install a local certificate if needed.</span></span> <span data-ttu-id="1f983-183">Mit diesem Zertifikat kann Microsoft Teams Ihre Anwendung von `https://localhost` laden.</span><span class="sxs-lookup"><span data-stu-id="1f983-183">This certificate allows Teams to load your application from `https://localhost`.</span></span> <span data-ttu-id="1f983-184">Wählen Sie "Ja" aus, wenn das folgende Dialogfenster angezeigt wird:</span><span class="sxs-lookup"><span data-stu-id="1f983-184">Select yes when the following dialog appears:</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/ssl-prompt.png" alt-text="Screenshot mit Dialogfenster zum Installieren eines SSL-Zertifikats, damit Microsoft Teams Ihre Anwendung von localhost laden kann.":::

1. <span data-ttu-id="1f983-186">Drücken Sie eines der **Add Webpart** (+)-Symbole, um ihr Webpart hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="1f983-186">Press one of the **Add Webpart** (+) icons to add your webpart.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-workbench-addpart.png" alt-text="Screenshot der SPFx-Workbench, die mit dem Popup ausgeführt wird, um ein Webpart hinzuzufügen.":::

1. <span data-ttu-id="1f983-188">Wählen Sie ihr Webpart aus dem Menü aus.</span><span class="sxs-lookup"><span data-stu-id="1f983-188">Choose your webpart from the menu.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-workbench-addpart2.png" alt-text="Screenshot der SPFx-Workbench, die mit dem Popup ausgeführt wird, um eine Webpartauswahl hinzuzufügen.":::

<span data-ttu-id="1f983-190">Ihre App sollte jetzt ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="1f983-190">Your app should now be running.</span></span>  <span data-ttu-id="1f983-191">Sie können normale Debugaktivitäten ausführen, als wäre dies ein anderes SPFx-Webpart (z. B. das Festlegen von Haltepunkten).</span><span class="sxs-lookup"><span data-stu-id="1f983-191">You can do normal debugging activities as if this were any other SPFx webpart (such as setting breakpoints).</span></span>

> [!TIP]
> <span data-ttu-id="1f983-192">Versuchen Sie, Haltepunkte in der Rendermethode des Browserfensters zu platzieren `SPFx/src/webparts/{webpart}/{webpart}.ts` und neu zu laden.</span><span class="sxs-lookup"><span data-stu-id="1f983-192">Try placing breakpoints in the render method of `SPFx/src/webparts/{webpart}/{webpart}.ts` and reloading the browser window.</span></span> <span data-ttu-id="1f983-193">VS-Code wird an Haltepunkten im Code beendet.</span><span class="sxs-lookup"><span data-stu-id="1f983-193">VS Code will stop on breakpoints in your code.</span></span>

## <a name="deploy-your-app-to-sharepoint"></a><span data-ttu-id="1f983-194">Bereitstellen Ihrer App in SharePoint</span><span class="sxs-lookup"><span data-stu-id="1f983-194">Deploy your app to SharePoint</span></span>

<span data-ttu-id="1f983-195">Stellen Sie sicher, dass in Ihrer Bereitstellung ein SharePoint-App-Katalog vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="1f983-195">Ensure a SharePoint App Catalog exists in your deployment.</span></span>  <span data-ttu-id="1f983-196">Wenn eine nicht vorhanden ist, [erstellen Sie eine](/sharepoint/use-app-catalog).</span><span class="sxs-lookup"><span data-stu-id="1f983-196">If one does not exist, [create one](/sharepoint/use-app-catalog).</span></span>  <span data-ttu-id="1f983-197">Es kann bis zu 15 Minuten dauern, bis der App-Katalog vollständig erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="1f983-197">It may take up to 15 minutes for the app catalog to be fully created.</span></span>

# <a name="visual-studio-code"></a>[<span data-ttu-id="1f983-198">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="1f983-198">Visual Studio Code</span></span>](#tab/vscode)

1. <span data-ttu-id="1f983-199">Öffnen Sie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="1f983-199">Open Visual Studio Code.</span></span>
1. <span data-ttu-id="1f983-200">Wählen Sie das Teams-Toolkit in der Seitenleiste aus, indem Sie das Symbol "Teams" auswählen.</span><span class="sxs-lookup"><span data-stu-id="1f983-200">Select the Teams Toolkit from the sidebar by selecting the Teams icon.</span></span>
1. <span data-ttu-id="1f983-201">Wählen Sie **"Bereitstellung in der Cloud" aus.**</span><span class="sxs-lookup"><span data-stu-id="1f983-201">Select **Provision in the Cloud**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/provisioning-commands.png" alt-text="Screenshot der Bereitstellungsbefehle":::

1. <span data-ttu-id="1f983-203">Sie können den Fortschritt überwachen, indem Sie sich die Dialogfelder in der unteren rechten Ecke ansehen.</span><span class="sxs-lookup"><span data-stu-id="1f983-203">You can monitor the progress by watching the dialogs in the bottom right corner.</span></span>  <span data-ttu-id="1f983-204">Nach ein paar Sekunden wird der folgende Hinweis angezeigt:</span><span class="sxs-lookup"><span data-stu-id="1f983-204">After a few seconds, you will see the following notice:</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/provision-complete.png" alt-text="Screenshot des Dialogfelds &quot;Bereitstellung abgeschlossen&quot;.":::

1. <span data-ttu-id="1f983-206">Sobald die Bereitstellung abgeschlossen ist, wählen Sie **"In der Cloud bereitstellen"** aus.</span><span class="sxs-lookup"><span data-stu-id="1f983-206">Once provisioning is complete, select **Deploy to the cloud**.</span></span>

1. <span data-ttu-id="1f983-207">Derzeit ist keine automatisierte Bereitstellung verfügbar.</span><span class="sxs-lookup"><span data-stu-id="1f983-207">Currently, automated deployment is not available.</span></span>  <span data-ttu-id="1f983-208">Ein Dialogfeld wird angezeigt, in dem Sie aufgefordert werden, manuell zu erstellen und bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="1f983-208">A dialog will pop up prompting you to build and deploy manually.</span></span> <span data-ttu-id="1f983-209">Drücken **Sie build SharePoint Package**.</span><span class="sxs-lookup"><span data-stu-id="1f983-209">Press **Build SharePoint Package**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/build-sharepoint-package.png" alt-text="Screenshot des Dialogfelds &quot;Sharepoint-Paket erstellen&quot;":::

# <a name="command-line"></a>[<span data-ttu-id="1f983-211">Befehlszeile</span><span class="sxs-lookup"><span data-stu-id="1f983-211">Command line</span></span>](#tab/cli)

<span data-ttu-id="1f983-212">In Ihrem Terminalfenster:</span><span class="sxs-lookup"><span data-stu-id="1f983-212">In your terminal window:</span></span>

1. <span data-ttu-id="1f983-213">Führen Sie `teamsfx provision` aus.</span><span class="sxs-lookup"><span data-stu-id="1f983-213">Run `teamsfx provision`.</span></span>

   ``` bash
   teamsfx provision
   ```

   <span data-ttu-id="1f983-214">Möglicherweise werden Sie aufgefordert, sich bei Ihrem Azure-Abonnement anzumelden.</span><span class="sxs-lookup"><span data-stu-id="1f983-214">You may be prompted to log in to your Azure subscription.</span></span>  <span data-ttu-id="1f983-215">Bei Bedarf werden Sie aufgefordert, ein Azure-Abonnement auszuwählen, das für die Azure-Ressourcen verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="1f983-215">If required, you will be prompted to select an Azure subscription to use for the Azure resources.</span></span>

   > [!NOTE]
   > <span data-ttu-id="1f983-216">Es werden immer einige Azure-Ressourcen zum Hosten Ihrer App verwendet.</span><span class="sxs-lookup"><span data-stu-id="1f983-216">There are always some Azure resources used for hosting your app.</span></span>

1. <span data-ttu-id="1f983-217">Führen Sie `teamsfx deploy` aus.</span><span class="sxs-lookup"><span data-stu-id="1f983-217">Run `teamsfx deploy`.</span></span>

   ``` bash
   teamsfx deploy
   ```

1. <span data-ttu-id="1f983-218">Wenn Sie dazu aufgefordert werden, wählen Sie **Build SharePoint Package** aus.</span><span class="sxs-lookup"><span data-stu-id="1f983-218">When prompted, select **Build SharePoint Package**.</span></span>

---

<span data-ttu-id="1f983-219">Das SharePoint-Paket befindet sich in `SPFx/sharepoint/solution` Ihrem Projekt.</span><span class="sxs-lookup"><span data-stu-id="1f983-219">The SharePoint package is located in `SPFx/sharepoint/solution` within your project.</span></span>  <span data-ttu-id="1f983-220">Hochladen Sie das Paket an SharePoint:</span><span class="sxs-lookup"><span data-stu-id="1f983-220">Upload the package to SharePoint:</span></span>

1. <span data-ttu-id="1f983-221">Melden Sie sich bei der M365 Admin Console an, und navigieren Sie dann zum SharePoint App-Katalog.</span><span class="sxs-lookup"><span data-stu-id="1f983-221">Log into the M365 Admin Console, then navigate to the SharePoint App Catalog.</span></span>

   - <span data-ttu-id="1f983-222">Öffnen `https://admin.microsoft.com/AdminPortal/Home` Sie .</span><span class="sxs-lookup"><span data-stu-id="1f983-222">Open `https://admin.microsoft.com/AdminPortal/Home`.</span></span>
   - <span data-ttu-id="1f983-223">Wählen Sie unter **Admin Center** das **SharePoint** Admin Center aus.</span><span class="sxs-lookup"><span data-stu-id="1f983-223">Under **Admin centers**, select the **SharePoint** admin center.</span></span>
   - <span data-ttu-id="1f983-224">Wählen Sie im Randleistenmenü **weitere Features** aus.</span><span class="sxs-lookup"><span data-stu-id="1f983-224">Select **More features** from the sidebar menu.</span></span>
   - <span data-ttu-id="1f983-225">Drücken Sie **"Öffnen"** unter **"Apps".**</span><span class="sxs-lookup"><span data-stu-id="1f983-225">Press **Open** under **Apps**.</span></span>
   - <span data-ttu-id="1f983-226">Wählen Sie **App-Katalog** aus.</span><span class="sxs-lookup"><span data-stu-id="1f983-226">Select **App Catalog**.</span></span>

1. <span data-ttu-id="1f983-227">Wählen Sie **"Apps für SharePoint verteilen"** aus.</span><span class="sxs-lookup"><span data-stu-id="1f983-227">Select **Distribute apps for SharePoint**.</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-distribute-apps.png" alt-text="Verteilen von Apps für SharePoint.":::

1. <span data-ttu-id="1f983-229">Wählen Sie **Hochladen** aus.</span><span class="sxs-lookup"><span data-stu-id="1f983-229">Select **Upload**.</span></span>

1. <span data-ttu-id="1f983-230">Drücken **Sie "Datei auswählen".**</span><span class="sxs-lookup"><span data-stu-id="1f983-230">Press **Choose File**.</span></span>

1. <span data-ttu-id="1f983-231">Suchen Sie Ihre `{project}.sppkg` Datei im Ordner in Ihrem `SPFx/sharepoint/solution` Projekt.</span><span class="sxs-lookup"><span data-stu-id="1f983-231">Locate your `{project}.sppkg` file, located in the `SPFx/sharepoint/solution` folder within your project.</span></span>  <span data-ttu-id="1f983-232">Drücken Sie **"Öffnen".**</span><span class="sxs-lookup"><span data-stu-id="1f983-232">Press **Open**.</span></span>

1. <span data-ttu-id="1f983-233">Drücken Sie **OK**.</span><span class="sxs-lookup"><span data-stu-id="1f983-233">Press **OK**.</span></span>

1. <span data-ttu-id="1f983-234">Der SharePoint Bereitstellungsprozess wird automatisch gestartet.</span><span class="sxs-lookup"><span data-stu-id="1f983-234">The SharePoint deployment process will automatically start.</span></span>  <span data-ttu-id="1f983-235">Stellen **Sie sicher, dass diese Lösung für alle Websites in der Organisation aktiviert** ist, und klicken Sie dann auf **"Bereitstellen".**</span><span class="sxs-lookup"><span data-stu-id="1f983-235">Ensure **Make this solution available to all sites in the organization** is checked, then press **Deploy**.</span></span>

1. <span data-ttu-id="1f983-236">Wählen Sie die Registerkarte **"DATEIEN" aus.**</span><span class="sxs-lookup"><span data-stu-id="1f983-236">Select the **FILES** tab.</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-appcatalog-filestab.png" alt-text="Wählen Sie die Registerkarte &quot;Dateien&quot; im SharePoint App-Katalog aus.":::

1. <span data-ttu-id="1f983-238">Wählen Sie das bereitgestellte Paket aus, und drücken Sie dann die **Synchronisierung, um** im Menüband Teams.</span><span class="sxs-lookup"><span data-stu-id="1f983-238">select the package you deployed, then press **Sync to Teams** in the ribbon.</span></span>

    > [!Note]
    > <span data-ttu-id="1f983-239">Der Vorgang "Mit Teams synchronisieren" kann einige Minuten dauern.</span><span class="sxs-lookup"><span data-stu-id="1f983-239">The Sync to Teams process can take a couple of minutes.</span></span>  <span data-ttu-id="1f983-240">Auf der rechten Seite des Browsers wird eine Meldung angezeigt, die angibt, dass die App erfolgreich mit Teams synchronisiert wurde.</span><span class="sxs-lookup"><span data-stu-id="1f983-240">You will see a message on the right-hand side of the browser indicating that the app has successfully synchronized to Teams.</span></span>

<span data-ttu-id="1f983-241">Öffnen Sie die Teams Anwendung (oder melden Sie sich `https://teams.microsoft.com` an).</span><span class="sxs-lookup"><span data-stu-id="1f983-241">Open the Teams application (or sign in at `https://teams.microsoft.com`).</span></span>  <span data-ttu-id="1f983-242">Drücken Sie den dreistelligen Punkt auf der Seitenleiste, und wählen Sie dann **alle Apps** aus.</span><span class="sxs-lookup"><span data-stu-id="1f983-242">Press the triple-dot on the sidebar, then select **All apps**.</span></span>  <span data-ttu-id="1f983-243">Die App wird in der Kategorie "Apps" platziert, die **für Ihre Organisationskategorie erstellt wurden.**</span><span class="sxs-lookup"><span data-stu-id="1f983-243">The app will be placed in the **Apps built for your org** category.</span></span>  <span data-ttu-id="1f983-244">Sie können die App von dort hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="1f983-244">You can add the app from there.</span></span>

:::image type="content" source="../assets/images/teams-toolkit-v2/spfx-app-in-teams.png" alt-text="Screenshot der App in Teams":::

## <a name="see-also"></a><span data-ttu-id="1f983-246">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="1f983-246">See also</span></span>

- [<span data-ttu-id="1f983-247">Erstellen einer Teams-App mit React</span><span class="sxs-lookup"><span data-stu-id="1f983-247">Create a Teams app with React</span></span>](first-app-react.md)
- [<span data-ttu-id="1f983-248">Erstellen einer Teams-App mit Blazor</span><span class="sxs-lookup"><span data-stu-id="1f983-248">Create a Teams app with Blazor</span></span>](first-app-blazor.md)
- [<span data-ttu-id="1f983-249">Erstellen einer Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="1f983-249">Create a messaging extension</span></span>](first-message-extension.md)

## <a name="next-step"></a><span data-ttu-id="1f983-250">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="1f983-250">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1f983-251">Erstellen einer Unterhaltungs-Bot-App</span><span class="sxs-lookup"><span data-stu-id="1f983-251">Create a conversational bot app</span></span>](first-app-bot.md)
