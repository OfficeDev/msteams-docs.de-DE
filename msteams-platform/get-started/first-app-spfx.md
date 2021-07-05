---
title: Erste Schritte – Erstellen Ihrer ersten Teams-App mit SPFx
author: zhenyasav
description: Erfahren Sie, wie Sie eine benutzerdefinierte Registerkarte mit dem SharePoint-Framework
ms.author: zhenyasa
ms.date: 05/19/2021
ms.topic: quickstart
ms.openlocfilehash: 4df2bb71837af520a2d2500a45b8605e5fae08b2
ms.sourcegitcommit: 9d63611974ba8a7e7f19ceea35e50189a2e90434
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2021
ms.locfileid: "53254223"
---
# <a name="build-and-run-your-first-microsoft-teams-app-with-sharepoint-framework-spfx"></a><span data-ttu-id="dce92-103">Erstellen und Ausführen Ihrer ersten Microsoft Teams-App mit SharePoint-Framework (SPFx)</span><span class="sxs-lookup"><span data-stu-id="dce92-103">Build and run your first Microsoft Teams app with SharePoint Framework (SPFx)</span></span>

<span data-ttu-id="dce92-104">In diesem Lernprogramm erfahren Sie, wie Sie eine neue Microsoft Teams-App in SharePoint-Framework SPFx erstellen, die eine einfache persönliche App implementiert.</span><span class="sxs-lookup"><span data-stu-id="dce92-104">In this tutorial, you will learn how to create a new Microsoft Teams app in SharePoint Framework SPFx that implements a simple personal app.</span></span> <span data-ttu-id="dce92-105">Beispielsweise enthält eine *persönliche App* eine Reihe von Registerkarten für die individuelle Verwendung.</span><span class="sxs-lookup"><span data-stu-id="dce92-105">For example, a *personal app* includes a set of tabs for individual use.</span></span> <span data-ttu-id="dce92-106">Während des Lernprogramms erfahren Sie mehr über die Struktur einer Teams-App, wie Sie eine App lokal ausführen und wie Sie die App für SharePoint bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="dce92-106">During the tutorial, you will learn about the structure of a Teams app, how to run an app locally, and how to deploy the app to SharePoint.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="dce92-107">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="dce92-107">Before you begin</span></span>

<span data-ttu-id="dce92-108">Stellen Sie sicher, dass Ihre Entwicklungsumgebung eingerichtet ist, indem Sie die erforderlichen Komponenten installieren.</span><span class="sxs-lookup"><span data-stu-id="dce92-108">Make sure your development environment is set up by installing the prerequisites.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dce92-109">Erforderliche Komponenten installieren</span><span class="sxs-lookup"><span data-stu-id="dce92-109">Install prerequisites</span></span>](prerequisites.md)

## <a name="get-organized"></a><span data-ttu-id="dce92-110">Besser organisiert sein</span><span class="sxs-lookup"><span data-stu-id="dce92-110">Get organized</span></span>

<span data-ttu-id="dce92-111">Zusätzlich zu den Voraussetzungen müssen Sie auch Administrator für eine SharePoint-Websitesammlung sein.</span><span class="sxs-lookup"><span data-stu-id="dce92-111">In addition to the prerequisites, you also need to be an Administrator for a SharePoint Site Collection.</span></span>  <span data-ttu-id="dce92-112">Hier stellen Sie Ihre App für das Hosting bereit.</span><span class="sxs-lookup"><span data-stu-id="dce92-112">This is where you will deploy your app for hosting.</span></span>  <span data-ttu-id="dce92-113">Wenn Sie einen Mandanten des M365-Entwicklerprogramms verwenden, verwenden Sie das Administratorkonto, das Sie bei der Registrierung für das Programm eingerichtet haben.</span><span class="sxs-lookup"><span data-stu-id="dce92-113">If you are using an M365 developer program tenant, use the administrator account you set up when you registered for the program.</span></span>  

## <a name="create-your-project"></a><span data-ttu-id="dce92-114">Erstellen Ihres Projekts</span><span class="sxs-lookup"><span data-stu-id="dce92-114">Create your project</span></span>

<span data-ttu-id="dce92-115">Verwenden Sie zum Erstellen Ihres ersten Projekts das Microsoft Teams-Toolkit:</span><span class="sxs-lookup"><span data-stu-id="dce92-115">Use the Teams Toolkit to create your first project:</span></span>

# <a name="visual-studio-code"></a>[<span data-ttu-id="dce92-116">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="dce92-116">Visual Studio Code</span></span>](#tab/vscode)

1. <span data-ttu-id="dce92-117">Öffnen Sie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="dce92-117">Open Visual Studio code.</span></span>
1. <span data-ttu-id="dce92-118">Wählen Sie das Symbol Teams in der Seitenleiste aus, um das Teams Toolkit zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="dce92-118">Select the Teams icon in the sidebar to open the Teams Toolkit.</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="Das Microsoft Teams-Symbol in der Visual Studio Code-Randleiste.":::

1. <span data-ttu-id="dce92-120">Klicken Sie auf **Neues Projekt erstellen**.</span><span class="sxs-lookup"><span data-stu-id="dce92-120">Select **Create New Project**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project.png" alt-text="Ort des Links „Neues Projekt erstellen“ in der Randleiste des Microsoft Teams-Toolkits.":::

1. <span data-ttu-id="dce92-122">Wählen Sie **Neue Microsoft Teams-App erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="dce92-122">Select **Create a new Teams app**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-new-project-intro.png" alt-text="Starten des Assistenten für „Neues Projekt erstellen“":::

1. <span data-ttu-id="dce92-124">Wählen Sie im Abschnitt **"Funktionen auswählen"** die Option **"Registerkarte"** und dann **"OK"** aus.</span><span class="sxs-lookup"><span data-stu-id="dce92-124">In the **Select capabilities** section, select **Tab** and select **OK**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-capabilities.png" alt-text="Screenshot, der zeigt, wie Ihrer neuen App Funktionen hinzufügt werden können.":::

1. <span data-ttu-id="dce92-126">Wählen Sie im Abschnitt **"Front-End-Hostingtyp"** **SharePoint-Framework (SPFx)** aus.</span><span class="sxs-lookup"><span data-stu-id="dce92-126">In the **Frontend hosting type** section, select **SharePoint Framework (SPFx)**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-hosting.png" alt-text="Screenshot, der zeigt, wie das Hosting für Ihre neue App ausgewählt wird.":::

1. <span data-ttu-id="dce92-128">Wählen Sie im Abschnitt **"Framework"** **React** aus.</span><span class="sxs-lookup"><span data-stu-id="dce92-128">In the **Framework** section, select **React**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-which-framework.png" alt-text="Auswählen des Frameworks":::

1. <span data-ttu-id="dce92-130">Wenn Sie nach einem **Webpartnamen** gefragt werden, drücken Sie die **EINGABETASTE,** um die Standardeinstellung zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="dce92-130">When asked for a **Webpart Name**, press **Enter** to accept the default.</span></span>

1. <span data-ttu-id="dce92-131">Wenn Sie nach der **Webpartbeschreibung** gefragt werden, drücken Sie die **EINGABETASTE,** um die Standardeinstellung zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="dce92-131">When asked for the **Webpart Description**, press **Enter** to accept the default.</span></span>

1. <span data-ttu-id="dce92-132">Wenn Sie nach der **Programmiersprache** gefragt werden, drücken Sie die **EINGABETASTE,** um die Standardeinstellung zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="dce92-132">When asked for the **Programming Language**, press **Enter** to accept the default.</span></span>

1. <span data-ttu-id="dce92-133">Wählen Sie einen Arbeitsbereichsordner aus.</span><span class="sxs-lookup"><span data-stu-id="dce92-133">Select a workspace folder.</span></span>  <span data-ttu-id="dce92-134">Innerhalb Ihres Arbeitsbereichsordners wird für das von Ihnen erstellte Projekt ein Ordner erstellt.</span><span class="sxs-lookup"><span data-stu-id="dce92-134">A folder will be created within your workspace folder for the project you are creating.</span></span>

1. <span data-ttu-id="dce92-135">Geben Sie einen passenden Namen für Ihre App ein, wie z. B. `helloworld`.</span><span class="sxs-lookup"><span data-stu-id="dce92-135">Enter a suitable name for your app, like `helloworld`.</span></span>  <span data-ttu-id="dce92-136">Der Name der App darf nur aus alphanumerischen Zeichen bestehen.</span><span class="sxs-lookup"><span data-stu-id="dce92-136">The name of the app must consist only of alphanumeric characters.</span></span>  <span data-ttu-id="dce92-137">Drücken Sie die **EINGABETASTE**, um fortzufahren.</span><span class="sxs-lookup"><span data-stu-id="dce92-137">Press **Enter** to continue.</span></span>

   <span data-ttu-id="dce92-138">Ihre Microsoft Teams-App wird innerhalb weniger Sekunden erstellt.</span><span class="sxs-lookup"><span data-stu-id="dce92-138">Your Teams app will be created within a few seconds.</span></span>

# <a name="command-line"></a>[<span data-ttu-id="dce92-139">Befehlszeile</span><span class="sxs-lookup"><span data-stu-id="dce92-139">Command line</span></span>](#tab/cli)

<span data-ttu-id="dce92-140">Verwenden Sie die `teamsfx`-CLI zum Erstellen Ihres ersten Projekts.</span><span class="sxs-lookup"><span data-stu-id="dce92-140">Use the `teamsfx` CLI to create your first project.</span></span>  <span data-ttu-id="dce92-141">Beginnen Sie in dem Ordner, in dem Sie den Projektordner erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="dce92-141">Start from the folder where you want to create the project folder.</span></span>

``` bash
teamsfx new
```

<span data-ttu-id="dce92-142">Die CLI führt durch einige Fragen zum Erstellen des Projekts.</span><span class="sxs-lookup"><span data-stu-id="dce92-142">The CLI walks through some questions to create the project.</span></span>  <span data-ttu-id="dce92-143">Bei jeder Frage wird angegeben, wie Sie sie beantworten können (z. B. mithilfe von Pfeiltasten, um eine Option auszuwählen).</span><span class="sxs-lookup"><span data-stu-id="dce92-143">Each question will tell you how to answer it (for example, to use arrow keys to select an option).</span></span>  <span data-ttu-id="dce92-144">Wenn Sie eine Frage beantwortet haben, bestätigen Sie Ihre Auswahl, indem Sie die **EINGABETASTE** drücken.</span><span class="sxs-lookup"><span data-stu-id="dce92-144">When you have answered the question, confirm your choice by pressing **Enter**.</span></span>

1. <span data-ttu-id="dce92-145">Wählen Sie **Neue Microsoft Teams-App erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="dce92-145">Select **Create a new Teams app**.</span></span>
1. <span data-ttu-id="dce92-146">Registerkarte **auswählen.**</span><span class="sxs-lookup"><span data-stu-id="dce92-146">Select **Tab**.</span></span>
1. <span data-ttu-id="dce92-147">Wählen Sie **SharePoint-Framework (SPFx)** Front-End-Hosting aus.</span><span class="sxs-lookup"><span data-stu-id="dce92-147">Select **SharePoint Framework (SPFx)** frontend hosting.</span></span>
1. <span data-ttu-id="dce92-148">Wählen Sie **React** Framework aus.</span><span class="sxs-lookup"><span data-stu-id="dce92-148">Select **React** framework.</span></span>
1. <span data-ttu-id="dce92-149">Drücken Sie die **EINGABETASTE** für den **Webpartnamen.**</span><span class="sxs-lookup"><span data-stu-id="dce92-149">Press **Enter** for the **Webpart Name**.</span></span>
1. <span data-ttu-id="dce92-150">Drücken Sie die **EINGABETASTE** für die **Webpartbeschreibung.**</span><span class="sxs-lookup"><span data-stu-id="dce92-150">Press **Enter** for the **Webpart Description**.</span></span>
1. <span data-ttu-id="dce92-151">Drücken Sie die **EINGABETASTE** für die **Programmiersprache.**</span><span class="sxs-lookup"><span data-stu-id="dce92-151">Press **Enter** for the **Programming Language**.</span></span>
1. <span data-ttu-id="dce92-152">Drücken Sie die **EINGABETASTE**, um den Standardordner des Arbeitsbereichs auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="dce92-152">Press **Enter** to select the default workspace folder.</span></span>
1. <span data-ttu-id="dce92-153">Geben Sie einen passenden Namen für Ihre App ein, wie z. B. `helloworld`.</span><span class="sxs-lookup"><span data-stu-id="dce92-153">Enter a suitable name for your app, like `helloworld`.</span></span>  <span data-ttu-id="dce92-154">Der Name der App darf nur aus alphanumerischen Zeichen bestehen.</span><span class="sxs-lookup"><span data-stu-id="dce92-154">The name of the app must consist only of alphanumeric characters.</span></span>

   <span data-ttu-id="dce92-155">Nachdem alle Fragen beantwortet wurden, wird Ihr Projekt erstellt.</span><span class="sxs-lookup"><span data-stu-id="dce92-155">After all the questions have been answered, your project will be created.</span></span>

---

- [<span data-ttu-id="dce92-156">Weitere Informationen zum Entwickeln für SharePoint-Framework</span><span class="sxs-lookup"><span data-stu-id="dce92-156">Learn more about developing for SharePoint Framework</span></span>](/sharepoint/dev/spfx/sharepoint-framework-overview)

## <a name="take-a-tour-of-the-source-code"></a><span data-ttu-id="dce92-157">Machen Sie einen Rundgang durch den Quellcode</span><span class="sxs-lookup"><span data-stu-id="dce92-157">Take a tour of the source code</span></span>

<span data-ttu-id="dce92-158">Wenn Sie diesen Abschnitt vorerst überspringen möchten, können Sie [Ihre App lokal ausführen](#run-your-app-locally).</span><span class="sxs-lookup"><span data-stu-id="dce92-158">If you wish to skip this section for now, you can [run your app locally](#run-your-app-locally).</span></span>

<span data-ttu-id="dce92-159">Nachdem das Teams Toolkit Ihr Projekt konfiguriert hat, verfügen Sie über die Komponenten zum Erstellen einer einfachen persönlichen App für Teams, die im SharePoint-Framework gehostet wird.</span><span class="sxs-lookup"><span data-stu-id="dce92-159">After the Teams Toolkit configures your project, you have the components to build a basic personal app for Teams that is hosted within the SharePoint Framework.</span></span>  <span data-ttu-id="dce92-160">Die Projektverzeichnisse und -dateien werden im Explorer-Bereich von Visual Studio Code angezeigt.</span><span class="sxs-lookup"><span data-stu-id="dce92-160">The project directories and files display in the Explorer area of Visual Studio Code.</span></span>

:::image type="content" source="../assets/images/teams-toolkit-v2/app-project-files-spfx.png" alt-text="Screenshot der App-Projektdateien für eine persönliche App in Visual Studio Code":::

<span data-ttu-id="dce92-162">Das Toolkit erstellt im Projektverzeichnis automatisch Ordner basierend auf den Funktionen, die Sie während des Setups hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="dce92-162">The Toolkit automatically creates scaffolding for you in the project directory based on the capabilities you added during setup.</span></span> <span data-ttu-id="dce92-163">Das Microsoft Teams Toolkit behält seinen Status für Ihre App im `.fx`-Verzeichnis bei.</span><span class="sxs-lookup"><span data-stu-id="dce92-163">The Teams Toolkit maintains its state for your app in the `.fx` directory.</span></span>  <span data-ttu-id="dce92-164">Weitere Elemente in diesem Verzeichnis:</span><span class="sxs-lookup"><span data-stu-id="dce92-164">Among other items in this directory:</span></span>

- <span data-ttu-id="dce92-165">Die App-Symbole werden als PNG-Dateien in `color.png` und `outline.png` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="dce92-165">The app icons are stored as PNG files in `color.png` and `outline.png`.</span></span>
- <span data-ttu-id="dce92-166">Das App-Manifest für die Veröffentlichung im Entwicklerportal für Teams wird in `manifest.source.json` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="dce92-166">The app manifest for publishing to Developer Portal for Teams is stored in `manifest.source.json`.</span></span>
- <span data-ttu-id="dce92-167">Die Einstellungen, die Sie beim Erstellen des Projekts ausgewählt haben, werden in `settings.json` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="dce92-167">The settings you chose when creating the project are stored in `settings.json`.</span></span>

<span data-ttu-id="dce92-168">Da Sie ein SPFx Webpart-Projekt ausgewählt haben, sind die folgenden Dateien für Die Benutzeroberfläche relevant:</span><span class="sxs-lookup"><span data-stu-id="dce92-168">Since you selected a SPFx Webpart project, the following files are relevant to your UI:</span></span>

- <span data-ttu-id="dce92-169">Der Ordner `SPFx/src/webparts/{webpart}` enthält Ihr SPFx-Webpart.</span><span class="sxs-lookup"><span data-stu-id="dce92-169">The folder `SPFx/src/webparts/{webpart}` contains your SPFx webpart.</span></span>
- <span data-ttu-id="dce92-170">Die Datei `.vscode/launch.json` beschreibt die Debugkonfigurationen, die in der Debugpalette verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="dce92-170">The file `.vscode/launch.json` describes the debugging configurations available in the debug palette.</span></span>

<span data-ttu-id="dce92-171">Weitere Informationen zu SharePoint Webparts für Teams [finden Sie in der SharePoint Dokumentation.](/sharepoint/dev/spfx/build-for-teams-overview)</span><span class="sxs-lookup"><span data-stu-id="dce92-171">For more information about SharePoint Webparts for Teams, [refer to the SharePoint documentation](/sharepoint/dev/spfx/build-for-teams-overview).</span></span>

## <a name="run-your-app-locally"></a><span data-ttu-id="dce92-172">Lokales Ausführen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="dce92-172">Run your app locally</span></span>

<span data-ttu-id="dce92-173">Teams Mit dem Toolkit können Sie Ihre App lokal hosten und über die [SharePoint-Framework Workbench](/sharepoint/dev/spfx/debug-in-vscode)ausführen.</span><span class="sxs-lookup"><span data-stu-id="dce92-173">Teams Toolkit allows you to host your app locally and run it through the [SharePoint Framework Workbench](/sharepoint/dev/spfx/debug-in-vscode).</span></span>

### <a name="build-and-run-your-app-locally-in-visual-studio-code"></a><span data-ttu-id="dce92-174">Erstellen und lokales Ausführen der App in Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="dce92-174">Build and run your app locally in Visual Studio Code</span></span>

<span data-ttu-id="dce92-175">So erstellen Sie Ihre App und führen sie lokal aus:</span><span class="sxs-lookup"><span data-stu-id="dce92-175">To build and run your app locally:</span></span>

1. <span data-ttu-id="dce92-176">Drücken Sie Visual Studio Code die **F5-TASTE.**</span><span class="sxs-lookup"><span data-stu-id="dce92-176">From Visual Studio Code, press the **F5** key.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-debug-local.png" alt-text="Screenshot, der zeigt, wie sie eine SPFx-App in einer lokalen Workbench starten.":::

   > [!NOTE]
   > <span data-ttu-id="dce92-178">Wenn Sie die App zum ersten Mal ausführen, werden alle Abhängigkeiten heruntergeladen und die App wird erstellt.</span><span class="sxs-lookup"><span data-stu-id="dce92-178">When you run the app for the first time, all dependencies are downloaded and the app is built.</span></span>  <span data-ttu-id="dce92-179">Ein Browserfenster wird automatisch geöffnet und die SharePoint Workbench geladen, wenn der Build abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="dce92-179">A browser window automatically opens and loads the SharePoint Workbench when the build is complete.</span></span>  <span data-ttu-id="dce92-180">Dies kann 3 bis 5 Minuten dauern.</span><span class="sxs-lookup"><span data-stu-id="dce92-180">This can take 3-5 minutes to complete.</span></span>

   <span data-ttu-id="dce92-181">Nachdem die SharePoint Workbench geladen wurde.</span><span class="sxs-lookup"><span data-stu-id="dce92-181">After the SharePoint Workbench is loaded.</span></span>

   >[!NOTE]
   > <span data-ttu-id="dce92-182">Sie werden vom Toolkit aufgefordert, bei Bedarf ein lokales Zertifikat zu installieren.</span><span class="sxs-lookup"><span data-stu-id="dce92-182">The Toolkit will prompt you to install a local certificate if needed.</span></span> <span data-ttu-id="dce92-183">Mit diesem Zertifikat kann Microsoft Teams Ihre Anwendung von `https://localhost` laden.</span><span class="sxs-lookup"><span data-stu-id="dce92-183">This certificate allows Teams to load your application from `https://localhost`.</span></span> <span data-ttu-id="dce92-184">Wählen Sie "Ja" aus, wenn das folgende Dialogfenster angezeigt wird:</span><span class="sxs-lookup"><span data-stu-id="dce92-184">Select yes when the following dialog appears:</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/ssl-prompt.png" alt-text="Screenshot mit Dialogfenster zum Installieren eines SSL-Zertifikats, damit Microsoft Teams Ihre Anwendung von localhost laden kann.":::

1. <span data-ttu-id="dce92-186">Wählen Sie **"Webpart hinzufügen+** Symbole" aus, um das Webpart hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="dce92-186">Select **Add Webpart +** icons to add your webpart.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-workbench-addpart.png" alt-text="Screenshot der SPFx Workbench, die mit dem Popup ausgeführt wird, um ein Webpart hinzuzufügen.":::

1. <span data-ttu-id="dce92-188">Wählen Sie ihr Webpart aus dem Menü aus.</span><span class="sxs-lookup"><span data-stu-id="dce92-188">Select your webpart from the menu.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-workbench-addpart2.png" alt-text="Screenshot der SPFx Workbench, die mit dem Popup ausgeführt wird, um eine Webpartauswahl hinzuzufügen.":::

   <span data-ttu-id="dce92-190">Ihre App sollte jetzt ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="dce92-190">Your app should now be running.</span></span>  <span data-ttu-id="dce92-191">Sie können normale Debugaktivitäten ausführen, als wäre dies ein anderes SPFx Webpart (z. B. festlegen von Haltepunkten).</span><span class="sxs-lookup"><span data-stu-id="dce92-191">You can do normal debugging activities as if this were any other SPFx webpart (such as setting breakpoints).</span></span>

   > [!TIP]
   > <span data-ttu-id="dce92-192">Versuchen Sie, Haltepunkte in der Rendermethode des Browserfensters zu platzieren `SPFx/src/webparts/{webpart}/{webpart}.ts` und neu zu laden.</span><span class="sxs-lookup"><span data-stu-id="dce92-192">Try placing breakpoints in the render method of `SPFx/src/webparts/{webpart}/{webpart}.ts` and reloading the browser window.</span></span> <span data-ttu-id="dce92-193">VS Code wird an Haltepunkten im Code beendet.</span><span class="sxs-lookup"><span data-stu-id="dce92-193">VS Code will stop on breakpoints in your code.</span></span>

## <a name="deploy-your-app-to-sharepoint"></a><span data-ttu-id="dce92-194">Bereitstellen der App für SharePoint</span><span class="sxs-lookup"><span data-stu-id="dce92-194">Deploy your app to SharePoint</span></span>

<span data-ttu-id="dce92-195">Stellen Sie sicher, dass in Ihrer Bereitstellung ein SharePoint App-Katalog vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="dce92-195">Ensure a SharePoint App Catalog exists in your deployment.</span></span>  <span data-ttu-id="dce92-196">Wenn eine nicht vorhanden ist, [erstellen Sie eine](/sharepoint/use-app-catalog).</span><span class="sxs-lookup"><span data-stu-id="dce92-196">If one does not exist, [create one](/sharepoint/use-app-catalog).</span></span>  <span data-ttu-id="dce92-197">Es kann bis zu 15 Minuten dauern, bis der App-Katalog vollständig erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="dce92-197">It may take up to 15 minutes for the app catalog to be fully created.</span></span>

# <a name="visual-studio-code"></a>[<span data-ttu-id="dce92-198">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="dce92-198">Visual Studio Code</span></span>](#tab/vscode)

1. <span data-ttu-id="dce92-199">Öffnen Sie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="dce92-199">Open Visual Studio Code.</span></span>
1. <span data-ttu-id="dce92-200">Wählen Sie das Teams Toolkit in der Seitenleiste aus, indem Sie das Symbol Teams auswählen.</span><span class="sxs-lookup"><span data-stu-id="dce92-200">Select the Teams Toolkit from the sidebar by selecting the Teams icon.</span></span>
1. <span data-ttu-id="dce92-201">Wählen Sie **"Bereitstellung in der Cloud" aus.**</span><span class="sxs-lookup"><span data-stu-id="dce92-201">Select **Provision in the Cloud**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/provisioning-commands.png" alt-text="Screenshot der Bereitstellungsbefehle":::

   <span data-ttu-id="dce92-203">Sie können den Fortschritt überwachen, indem Sie sich die Dialogfelder in der unteren rechten Ecke ansehen.</span><span class="sxs-lookup"><span data-stu-id="dce92-203">You can monitor the progress by watching the dialogs in the bottom right corner.</span></span>  <span data-ttu-id="dce92-204">Nach ein paar Sekunden wird der folgende Hinweis angezeigt:</span><span class="sxs-lookup"><span data-stu-id="dce92-204">After a few seconds, you will see the following notice:</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/provision-complete.png" alt-text="Screenshot des Dialogfelds &quot;Bereitstellung abgeschlossen&quot;.":::

1. <span data-ttu-id="dce92-206">Wählen Sie nach Abschluss der Bereitstellung die Option **"In der Cloud bereitstellen"** aus.</span><span class="sxs-lookup"><span data-stu-id="dce92-206">After provisioning is complete, select **Deploy to the cloud**.</span></span>

1. <span data-ttu-id="dce92-207">Derzeit ist keine automatisierte Bereitstellung verfügbar.</span><span class="sxs-lookup"><span data-stu-id="dce92-207">Currently, automated deployment is not available.</span></span>  <span data-ttu-id="dce92-208">Ein Dialogfeld wird angezeigt, in dem Sie aufgefordert werden, manuell zu erstellen und bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="dce92-208">A dialog will pop up prompting you to build and deploy manually.</span></span> <span data-ttu-id="dce92-209">Wählen Sie **"Build SharePoint Package" aus.**</span><span class="sxs-lookup"><span data-stu-id="dce92-209">Select **Build SharePoint Package**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/build-sharepoint-package.png" alt-text="Screenshot des Dialogfelds &quot;Sharepoint-Paket erstellen&quot;":::

# <a name="command-line"></a>[<span data-ttu-id="dce92-211">Befehlszeile</span><span class="sxs-lookup"><span data-stu-id="dce92-211">Command line</span></span>](#tab/cli)

<span data-ttu-id="dce92-212">In Ihrem Terminalfenster:</span><span class="sxs-lookup"><span data-stu-id="dce92-212">In your terminal window:</span></span>

1. <span data-ttu-id="dce92-213">Ausführen `teamsfx provision`.</span><span class="sxs-lookup"><span data-stu-id="dce92-213">Run `teamsfx provision`.</span></span>

   ``` bash
   teamsfx provision
   ```

   <span data-ttu-id="dce92-214">Möglicherweise werden Sie aufgefordert, sich bei Ihrem Azure-Abonnement anzumelden.</span><span class="sxs-lookup"><span data-stu-id="dce92-214">You may be prompted to log in to your Azure subscription.</span></span>  <span data-ttu-id="dce92-215">Bei Bedarf werden Sie aufgefordert, ein Azure-Abonnement auszuwählen, das für die Azure-Ressourcen verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="dce92-215">If required, you will be prompted to select an Azure subscription to use for the Azure resources.</span></span>

   > [!NOTE]
   > <span data-ttu-id="dce92-216">Es werden immer einige Azure-Ressourcen zum Hosten Ihrer App verwendet.</span><span class="sxs-lookup"><span data-stu-id="dce92-216">There are always some Azure resources used for hosting your app.</span></span>

1. <span data-ttu-id="dce92-217">Ausführen `teamsfx deploy`.</span><span class="sxs-lookup"><span data-stu-id="dce92-217">Run `teamsfx deploy`.</span></span>

   ``` bash
   teamsfx deploy
   ```

1. <span data-ttu-id="dce92-218">Wenn Sie dazu aufgefordert werden, wählen Sie **"Build SharePoint Package"** aus.</span><span class="sxs-lookup"><span data-stu-id="dce92-218">When prompted, select **Build SharePoint Package**.</span></span>

---

<span data-ttu-id="dce92-219">Das SharePoint-Paket befindet sich in `SPFx/sharepoint/solution` Ihrem Projekt.</span><span class="sxs-lookup"><span data-stu-id="dce92-219">The SharePoint package is located in `SPFx/sharepoint/solution` within your project.</span></span>  <span data-ttu-id="dce92-220">Hochladen das Paket an SharePoint:</span><span class="sxs-lookup"><span data-stu-id="dce92-220">Upload the package to SharePoint:</span></span>

1. <span data-ttu-id="dce92-221">Melden Sie sich bei der M365 Admin Console an, und navigieren Sie dann zum SharePoint App-Katalog.</span><span class="sxs-lookup"><span data-stu-id="dce92-221">Log into the M365 Admin Console, then navigate to the SharePoint App Catalog.</span></span>

   1. <span data-ttu-id="dce92-222">Öffnen `https://admin.microsoft.com/AdminPortal/Home` Sie .</span><span class="sxs-lookup"><span data-stu-id="dce92-222">Open `https://admin.microsoft.com/AdminPortal/Home`.</span></span>
   1. <span data-ttu-id="dce92-223">Wählen Sie unter **Admin Center** das **SharePoint** Admin Center aus.</span><span class="sxs-lookup"><span data-stu-id="dce92-223">Under **Admin centers**, select the **SharePoint** admin center.</span></span>
   1. <span data-ttu-id="dce92-224">Wählen Sie im Randleistenmenü **weitere Features** aus.</span><span class="sxs-lookup"><span data-stu-id="dce92-224">Select **More features** from the sidebar menu.</span></span>
   1. <span data-ttu-id="dce92-225">Drücken Sie **"Öffnen"** unter **"Apps".**</span><span class="sxs-lookup"><span data-stu-id="dce92-225">Press **Open** under **Apps**.</span></span>
   1. <span data-ttu-id="dce92-226">Wählen Sie **App-Katalog** aus.</span><span class="sxs-lookup"><span data-stu-id="dce92-226">Select **App Catalog**.</span></span>

1. <span data-ttu-id="dce92-227">Wählen Sie **"Apps für SharePoint verteilen"** aus.</span><span class="sxs-lookup"><span data-stu-id="dce92-227">Select **Distribute apps for SharePoint**.</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-distribute-apps.png" alt-text="Verteilen von Apps für SharePoint.":::

1. <span data-ttu-id="dce92-229">Wählen Sie **Hochladen** aus.</span><span class="sxs-lookup"><span data-stu-id="dce92-229">Select **Upload**.</span></span>

1. <span data-ttu-id="dce92-230">Wählen Sie **"Datei auswählen"** aus.</span><span class="sxs-lookup"><span data-stu-id="dce92-230">Select **Choose File**.</span></span>

1. <span data-ttu-id="dce92-231">Suchen Sie Ihre `{project}.sppkg` Datei im Ordner in Ihrem `SPFx/sharepoint/solution` Projekt.</span><span class="sxs-lookup"><span data-stu-id="dce92-231">Locate your `{project}.sppkg` file in the `SPFx/sharepoint/solution` folder within your project.</span></span> <span data-ttu-id="dce92-232">Klicken Sie auf **Öffnen**.</span><span class="sxs-lookup"><span data-stu-id="dce92-232">Select **Open**.</span></span>

1. <span data-ttu-id="dce92-233">Wählen Sie **OK** aus.</span><span class="sxs-lookup"><span data-stu-id="dce92-233">Select **OK**.</span></span>

1. <span data-ttu-id="dce92-234">Der SharePoint Bereitstellungsprozess wird automatisch gestartet.</span><span class="sxs-lookup"><span data-stu-id="dce92-234">The SharePoint deployment process will automatically start.</span></span> <span data-ttu-id="dce92-235">Stellen Sie sicher, dass **diese Lösung für alle Websites in der Organisation verfügbar** ist.</span><span class="sxs-lookup"><span data-stu-id="dce92-235">Verify that **Make this solution available to all sites in the organization** is selected.</span></span> <span data-ttu-id="dce92-236">Wählen Sie dann **Bereitstellen aus.**</span><span class="sxs-lookup"><span data-stu-id="dce92-236">Then select **Deploy**.</span></span>

1. <span data-ttu-id="dce92-237">Wählen Sie die Registerkarte **"DATEIEN" aus.**</span><span class="sxs-lookup"><span data-stu-id="dce92-237">Select the **FILES** tab.</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-appcatalog-filestab.png" alt-text="Wählen Sie die Registerkarte &quot;Dateien&quot; im SharePoint App-Katalog aus.":::

1. <span data-ttu-id="dce92-239">wählen Sie das bereitgestellte Paket aus, und wählen Sie dann in der oberen rechten Ecke die Option **"Synchronisieren" aus, um Teams.**</span><span class="sxs-lookup"><span data-stu-id="dce92-239">select the package you deployed, then select **Sync to Teams** from the upper right corner.</span></span>

    > [!Note]
    > <span data-ttu-id="dce92-240">Der Vorgang "Mit Teams synchronisieren" kann einige Minuten dauern.</span><span class="sxs-lookup"><span data-stu-id="dce92-240">The Sync to Teams process can take a couple of minutes.</span></span>  <span data-ttu-id="dce92-241">Auf der rechten Seite des Browsers wird eine Meldung angezeigt, die angibt, dass die App erfolgreich mit Teams synchronisiert wurde.</span><span class="sxs-lookup"><span data-stu-id="dce92-241">You will see a message on the right-hand side of the browser indicating that the app has successfully synchronized to Teams.</span></span>

   <span data-ttu-id="dce92-242">Öffnen Sie die Teams Anwendung (oder melden Sie sich bei `https://teams.microsoft.com` ) an.</span><span class="sxs-lookup"><span data-stu-id="dce92-242">Open the Teams application (or sign in at `https://teams.microsoft.com`).</span></span>  <span data-ttu-id="dce92-243">Drücken Sie den dreistelligen Punkt auf der Seitenleiste, und wählen Sie dann **alle Apps** aus.</span><span class="sxs-lookup"><span data-stu-id="dce92-243">Press the triple-dot on the sidebar, then select **All apps**.</span></span>  <span data-ttu-id="dce92-244">Die App wird in der Kategorie "Apps" platziert, die **für Ihre Organisationskategorie erstellt wurden.**</span><span class="sxs-lookup"><span data-stu-id="dce92-244">The app will be placed in the **Apps built for your org** category.</span></span>  <span data-ttu-id="dce92-245">Sie können die App von dort hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="dce92-245">You can add the app from there.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-app-in-teams.png" alt-text="Screenshot der App in Teams":::

## <a name="see-also"></a><span data-ttu-id="dce92-247">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="dce92-247">See also</span></span>

* [<span data-ttu-id="dce92-248">Übersicht über Lernprogramme</span><span class="sxs-lookup"><span data-stu-id="dce92-248">Tutorials Overview</span></span>](code-samples.md)
* [<span data-ttu-id="dce92-249">Erstellen einer Unterhaltungs-Bot-App</span><span class="sxs-lookup"><span data-stu-id="dce92-249">Create a conversational bot app</span></span>](first-app-bot.md)
* [<span data-ttu-id="dce92-250">Erstellen einer Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="dce92-250">Create a messaging extension</span></span>](first-message-extension.md)
* [<span data-ttu-id="dce92-251">Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="dce92-251">Code Samples</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples)
