---
title: Erstellen von Apps mit dem Microsoft Teams Toolkit und Visual Studio Code
description: Beginnen Sie mit dem Erstellen großartiger benutzerdefinierter Apps direkt innerhalb Visual Studio Code mit dem Microsoft Teams Toolkit
keywords: Teams Visual Studio Code Toolkit
localization_priority: Normal
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: efd0962e9c4c0d64dbac47caf29b2e56907937b3
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566558"
---
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio-code"></a><span data-ttu-id="46517-104">Erstellen Sie Apps mit dem Teams Toolkit und Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="46517-104">Build apps with the Teams Toolkit and Visual Studio Code</span></span>

<span data-ttu-id="46517-105">Mithilfe des Microsoft Teams-Toolkits können Sie benutzerdefinierte Teams-Apps direkt innerhalb der Visual Studio Code-Umgebung erstellen.</span><span class="sxs-lookup"><span data-stu-id="46517-105">The Microsoft Teams Toolkit enables you to create custom Teams apps directly within the Visual Studio Code environment.</span></span> <span data-ttu-id="46517-106">Das Toolkit führt Sie durch den Vorgang und bietet alles, was Sie zum Erstellen, Debuggen und Starten Ihrer Teams-App benötigen.</span><span class="sxs-lookup"><span data-stu-id="46517-106">The toolkit guides you through the process and provides everything you need to build, debug, and launch your Teams app.</span></span>

## <a name="installing-the-teams-toolkit"></a><span data-ttu-id="46517-107">Installieren des Teams Toolkits</span><span class="sxs-lookup"><span data-stu-id="46517-107">Installing the Teams Toolkit</span></span>

<span data-ttu-id="46517-108">Das Microsoft Teams Toolkit for Visual Studio Code steht im [Visual Studio Marketplace](https://aka.ms/teams-toolkit) oder direkt als Erweiterung innerhalb Visual Studio Code zum Download zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="46517-108">The Microsoft Teams Toolkit for Visual Studio Code is available for download from the [Visual Studio Marketplace](https://aka.ms/teams-toolkit) or directly as an extension within Visual Studio Code.</span></span>

> [!TIP]
> <span data-ttu-id="46517-109">Nach der Installation sollte das Teams Toolkit in der Aktivitätsleiste Visual Studio Code angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="46517-109">After installation, you should see the Teams Toolkit in the Visual Studio Code activity bar.</span></span> <span data-ttu-id="46517-110">Wenn dies nicht der Fall ist, klicken Sie mit der rechten Maustaste in die Aktivitätsleiste, und wählen Sie **Microsoft Teams** aus, um das Toolkit für einen einfachen Zugriff anzuheften.</span><span class="sxs-lookup"><span data-stu-id="46517-110">If not, right-click within the activity bar and select **Microsoft Teams** to pin the toolkit for easy access.</span></span>

## <a name="using-the-toolkit"></a><span data-ttu-id="46517-111">Verwenden des Toolkits</span><span class="sxs-lookup"><span data-stu-id="46517-111">Using the toolkit</span></span>

- [<span data-ttu-id="46517-112">Einrichten eines neuen Projekts</span><span class="sxs-lookup"><span data-stu-id="46517-112">Set up a new project</span></span>](#set-up-a-new-teams-project)
- [<span data-ttu-id="46517-113">Importieren eines vorhandenen Projekts</span><span class="sxs-lookup"><span data-stu-id="46517-113">Import an existing project</span></span>](#import-an-existing-teams-app-project)
- [<span data-ttu-id="46517-114">Konfigurieren Sie die App</span><span class="sxs-lookup"><span data-stu-id="46517-114">Configure your app</span></span>](#configure-your-app)
- [<span data-ttu-id="46517-115">Verpacken Sie Ihre App</span><span class="sxs-lookup"><span data-stu-id="46517-115">Package your app</span></span>](#package-your-app)
- [<span data-ttu-id="46517-116">Führen Sie Ihre App lokal oder in Teams</span><span class="sxs-lookup"><span data-stu-id="46517-116">Run your app locally or in Teams</span></span>](#run-your-app)

## <a name="set-up-a-new-teams-project"></a><span data-ttu-id="46517-117">Einrichten eines neuen Teams Projekts</span><span class="sxs-lookup"><span data-stu-id="46517-117">Set up a new Teams project</span></span>

1. <span data-ttu-id="46517-118">Erstellen Sie einen Arbeitsbereich oder Ordner für Ihr Projekt in Ihrer lokalen Umgebung.</span><span class="sxs-lookup"><span data-stu-id="46517-118">Create a workspace or folder for your project in your local environment.</span></span>
1. <span data-ttu-id="46517-119">Wählen Sie in Visual Studio Code das Teams-Symbol aus.</span><span class="sxs-lookup"><span data-stu-id="46517-119">In Visual Studio Code, select the Teams icon</span></span> ![Teams-Symbol](../assets/icons/favicon-16x16.png) <span data-ttu-id="46517-121">aus der Aktivitätsleiste auf der linken Seite des Fensters.</span><span class="sxs-lookup"><span data-stu-id="46517-121">from the activity bar on the left side of the window.</span></span>
1. <span data-ttu-id="46517-122">Wählen Sie Microsoft Teams Toolkit im Befehlsmenü **öffnen** aus.</span><span class="sxs-lookup"><span data-stu-id="46517-122">Select **Open the Microsoft Teams Toolkit** from the command menu.</span></span>
1. <span data-ttu-id="46517-123">Wählen Sie im Befehlsmenü die Option **Neue Teams App erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="46517-123">Select **Create a new Teams app** from the command menu.</span></span>
1. <span data-ttu-id="46517-124">Wenn Sie dazu aufgefordert werden, geben Sie den Namen des Arbeitsbereichs ein.</span><span class="sxs-lookup"><span data-stu-id="46517-124">When prompted, enter the name of the workspace .</span></span> <span data-ttu-id="46517-125">Dies wird sowohl als Name des Ordners, in dem sich das Projekt befindet, als auch als Standardname Ihrer App verwendet.</span><span class="sxs-lookup"><span data-stu-id="46517-125">This will be used as both the name of the folder where your project will reside, and the default name of your app.</span></span>
1. <span data-ttu-id="46517-126">Drücken Sie **die Eingabetaste,** und Sie gelangen zum Bildschirm **"Funktionen hinzufügen",** um die Eigenschaften für Ihre neue App zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="46517-126">Press **Enter** and you will arrive at the **Add capabilities** screen configure the properties for your new app.</span></span>
1. <span data-ttu-id="46517-127">Wählen Sie die Schaltfläche **Fertig stellen** aus, um den Konfigurationsvorgang abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="46517-127">Select the **Finish** button to complete the configuration process.</span></span>

## <a name="import-an-existing-teams-app-project"></a><span data-ttu-id="46517-128">Importieren eines vorhandenen Teams-App-Projekts</span><span class="sxs-lookup"><span data-stu-id="46517-128">Import an existing Teams app project</span></span>

1. <span data-ttu-id="46517-129">Wählen Sie in Visual Studio Code das Teams-Symbol aus.</span><span class="sxs-lookup"><span data-stu-id="46517-129">In Visual Studio Code, select the Teams icon</span></span> ![Teams-Symbol](../assets/icons/favicon-16x16.png) <span data-ttu-id="46517-131">aus der Aktivitätsleiste auf der linken Seite des Fensters.</span><span class="sxs-lookup"><span data-stu-id="46517-131">from the activity bar on the left side of the window.</span></span>
1. <span data-ttu-id="46517-132">Wählen Sie **App-Paket** importieren aus dem Befehlsmenü aus.</span><span class="sxs-lookup"><span data-stu-id="46517-132">Select **Import app package** from the command menu.</span></span>
1. <span data-ttu-id="46517-133">Wählen Sie Ihre vorhandene [Teams App-Paket](../concepts/build-and-test/apps-package.md) ZIP-Datei.</span><span class="sxs-lookup"><span data-stu-id="46517-133">Choose your existing [Teams app package](../concepts/build-and-test/apps-package.md) zip file.</span></span>
1. <span data-ttu-id="46517-134">Wählen Sie die Schaltfläche **Veröffentlichungspaket auswählen** aus.</span><span class="sxs-lookup"><span data-stu-id="46517-134">Choose the **Select publishing package** button.</span></span> <span data-ttu-id="46517-135">Die Konfigurationsregisterkarte des Toolkits sollte nun mit den Details Ihrer App aufgefüllt werden.</span><span class="sxs-lookup"><span data-stu-id="46517-135">The configuration tab of the toolkit should now be populated with your app's details.</span></span>
1. <span data-ttu-id="46517-136">Wählen Sie in Visual Studio Code **Dateiordner** zum Arbeitsbereich hinzufügen aus,  ->   um das Quellcodeverzeichnis zum Visual Studio Code Arbeitsbereich hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="46517-136">In Visual Studio Code, select **File** -> **Add Folder to Workspace** to add your source code directory to the Visual Studio Code workspace.</span></span>

## <a name="configure-your-app"></a><span data-ttu-id="46517-137">Konfigurieren Sie die App</span><span class="sxs-lookup"><span data-stu-id="46517-137">Configure your app</span></span>

<span data-ttu-id="46517-138">Im Kern umfasst die Teams-App drei Komponenten:</span><span class="sxs-lookup"><span data-stu-id="46517-138">At its core, the Teams app embraces three components:</span></span>

  1. <span data-ttu-id="46517-139">Der Microsoft Teams Client (Web, Desktop oder Mobile), auf dem Benutzer mit Ihrer App interagieren.</span><span class="sxs-lookup"><span data-stu-id="46517-139">The Microsoft Teams client (web, desktop or mobile) where users interact with your app.</span></span>
  1. <span data-ttu-id="46517-140">Ein Server, der auf Anforderungen für Inhalte reagiert, die in Teams angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="46517-140">A server that responds to requests for content that will be displayed in Teams.</span></span> <span data-ttu-id="46517-141">Zum Beispiel HTML-Registerkarteninhalt oder eine adaptive Bot-Karte.</span><span class="sxs-lookup"><span data-stu-id="46517-141">For example, HTML tab content or a bot adaptive card.</span></span>
  1. <span data-ttu-id="46517-142">Ein Teams [App-Paket,](/concepts/build-and-test/apps-package.md) das aus drei Dateien besteht:</span><span class="sxs-lookup"><span data-stu-id="46517-142">A Teams [app package](/concepts/build-and-test/apps-package.md) consisting of three files:</span></span>

      > [!div class="checklist"]
      >
      > - <span data-ttu-id="46517-143">Die manifest.jsweiter.</span><span class="sxs-lookup"><span data-stu-id="46517-143">The manifest.json.</span></span> 
      > - <span data-ttu-id="46517-144">Ein [Farbsymbol](../resources/schema/manifest-schema.md#icons) für Ihre App, das im öffentlichen oder Organisations-App-Katalog angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="46517-144">A [color icon](../resources/schema/manifest-schema.md#icons) for your app to display in the public or organization app catalog.</span></span>
      > - <span data-ttu-id="46517-145">Ein [Gliederungssymbol](../resources/schema/manifest-schema.md#icons) für die Anzeige in der Teams Aktivitätsleiste.</span><span class="sxs-lookup"><span data-stu-id="46517-145">An [outline icon](../resources/schema/manifest-schema.md#icons) for display on the Teams activity bar.</span></span>

<span data-ttu-id="46517-146">Wenn eine App installiert ist, analysiert der Teams-Client die Manifestdatei, um die erforderlichen Informationen wie den Namen Ihrer App und die URL zu ermitteln, unter denen sich die Dienste befinden.</span><span class="sxs-lookup"><span data-stu-id="46517-146">When an app is installed, the Teams client parses the manifest file to determine needed information like the name of your app and the URL where the services are located.</span></span>

1. <span data-ttu-id="46517-147">Um Ihre App zu konfigurieren, navigieren Sie zur Registerkarte **Microsoft Teams Toolkit** in Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="46517-147">To configure your app, navigate to the **Microsoft Teams Toolkit** tab in Visual Studio Code.</span></span>
1. <span data-ttu-id="46517-148">Wählen Sie **App-Paket bearbeiten** aus, um die **App-Detailseite** anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="46517-148">Select **Edit app package** to view the **App details** page.</span></span>
1. <span data-ttu-id="46517-149">Durch das Bearbeiten der Felder auf der Seite App-Details wird der Inhalt der manifest.jsin der Datei aktualisiert, die letztendlich als Teil des App-Pakets ausgeliefert wird.</span><span class="sxs-lookup"><span data-stu-id="46517-149">Editing the fields in the App details page updates the contents of the manifest.json file that will ultimately ship as part of the app package.</span></span> <span data-ttu-id="46517-150">Weitere Informationen finden Sie im [App Studio-Manifesteditor](https://aka.ms/teams-toolkit-manifest)</span><span class="sxs-lookup"><span data-stu-id="46517-150">For more information, See [App Studio manifest editor](https://aka.ms/teams-toolkit-manifest)</span></span>

## <a name="package-your-app"></a><span data-ttu-id="46517-151">Verpacken Sie Ihre App</span><span class="sxs-lookup"><span data-stu-id="46517-151">Package your app</span></span>

<span data-ttu-id="46517-152">Wenn Sie die **App-Detailseite,** das **Manifest** oder **die .env-Dateien** im  **.publish-Ordner** Ihrer App ändern, werden automatisch Ihre **Development.zip** Datei generiert.</span><span class="sxs-lookup"><span data-stu-id="46517-152">Modifying the **app details** page, **manifest**, or **.env** files in your app's  **.publish** folder will automatically generate your **Development.zip** file.</span></span> <span data-ttu-id="46517-153">Sie müssen zwei [Symbole](../concepts/build-and-test/apps-package.md#app-icons) in demselben Ordner einschließen.</span><span class="sxs-lookup"><span data-stu-id="46517-153">You'll need to include [two icons](../concepts/build-and-test/apps-package.md#app-icons) in that same folder.</span></span>

## <a name="install-and-run-your-app-locally"></a><span data-ttu-id="46517-154">Installieren und Ausführen Ihrer App lokal</span><span class="sxs-lookup"><span data-stu-id="46517-154">Install and run your app locally</span></span>

## <a name="run-your-app"></a><span data-ttu-id="46517-155">Ausführen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="46517-155">Run your app</span></span>

### <a name="install-and-run-your-app-locally"></a><span data-ttu-id="46517-156">Installieren und Ausführen Ihrer App lokal</span><span class="sxs-lookup"><span data-stu-id="46517-156">Install and run your app locally</span></span>

<span data-ttu-id="46517-157">Ausführliche Anweisungen zum Verpacken und Testen Ihrer App finden Sie auf der Projekthomepage zum **Erstellen und Ausführen** von Inhalten.</span><span class="sxs-lookup"><span data-stu-id="46517-157">Refer to the **Build and Run** content in your project homepage for detailed instructions on how to package and test your app.</span></span> <span data-ttu-id="46517-158">Im Allgemeinen müssen Sie den Server Ihrer App installieren, ihn ausführen lassen und dann eine Tunnellösung einrichten, damit Teams auf Inhalte zugreifen können, die von localhost ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="46517-158">In general, you need to install your app's server, get it running, then setup a tunneling solution so that Teams can access content running from localhost.</span></span>

### <a name="enable-development-from-localhost"></a><span data-ttu-id="46517-159">Ermöglichen der Entwicklung von localhost</span><span class="sxs-lookup"><span data-stu-id="46517-159">Enable development from localhost</span></span>

<span data-ttu-id="46517-160">Wenn Sie Ihre tabbasierte App auf localhost mithilfe von HTTPS debuggen möchten, müssen Sie Ihren Browser anweisen, der von bereitgestellten App zu <https://localhost> vertrauen.</span><span class="sxs-lookup"><span data-stu-id="46517-160">If you wish to debug your tab based app on localhost using HTTPS, you will need to tell your browser to trust the app being served from <https://localhost>.</span></span> <span data-ttu-id="46517-161">Navigieren Sie zu <https://localhost:3000/tab>.</span><span class="sxs-lookup"><span data-stu-id="46517-161">Navigate to <https://localhost:3000/tab>.</span></span> <span data-ttu-id="46517-162">Wenn eine Warnung angezeigt wird, die darauf hinweist, dass die Website nicht vertrauenswürdig ist, wählen Sie die Option aus, um trotzdem fortzufahren.</span><span class="sxs-lookup"><span data-stu-id="46517-162">If you see a warning indicating that the site isn't trusted, choose the option to proceed anyway.</span></span> <span data-ttu-id="46517-163">Auf Ihre App sollte jetzt vom Teams Client zugegriffen werden können.</span><span class="sxs-lookup"><span data-stu-id="46517-163">Your app should now be accessible from the Teams client.</span></span>

### <a name="run-your-app-in-teams"></a><span data-ttu-id="46517-164">Führen Sie Ihre App in Teams</span><span class="sxs-lookup"><span data-stu-id="46517-164">Run your app in Teams</span></span>

<span data-ttu-id="46517-165">Voraussetzungen: [Aktivieren Teams Entwicklervorschaumodus](https://aka.ms/teams-toolkit-enable-devpreview)</span><span class="sxs-lookup"><span data-stu-id="46517-165">Prerequisites: [Enable Teams developer preview mode](https://aka.ms/teams-toolkit-enable-devpreview)</span></span>

1. <span data-ttu-id="46517-166">Navigieren Sie zur Aktivitätsleiste auf der linken Seite des Visual Studio Code Fensters.</span><span class="sxs-lookup"><span data-stu-id="46517-166">Navigate to the activity bar on the left side of the Visual Studio Code window.</span></span>
1. <span data-ttu-id="46517-167">Wählen Sie das **Symbol Ausführen** aus, um die Ansicht Ausführen **und Debuggen** anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="46517-167">Select the **Run** icon to display the **Run and Debug** view.</span></span>
1. <span data-ttu-id="46517-168">Sie können auch die Tastenkombination `Ctrl+Shift+D` verwenden.</span><span class="sxs-lookup"><span data-stu-id="46517-168">You can also use the keyboard shortcut `Ctrl+Shift+D`.</span></span>

## <a name="next-step"></a><span data-ttu-id="46517-169">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="46517-169">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="46517-170">Verwalten und Unterstützen Ihrer veröffentlichten App</span><span class="sxs-lookup"><span data-stu-id="46517-170">Maintaining and supporting your published app</span></span>](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
