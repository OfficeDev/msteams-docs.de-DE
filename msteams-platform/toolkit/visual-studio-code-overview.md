---
title: Erstellen von Apps mit dem Microsoft Teams Toolkit und Visual Studio Code
description: Erste Schritte beim Erstellen großartiger benutzerdefinierter Apps direkt Visual Studio Code mit dem Microsoft Teams Toolkit
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
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio-code"></a><span data-ttu-id="caae1-104">Erstellen von Apps mit dem Teams Toolkit und Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="caae1-104">Build apps with the Teams Toolkit and Visual Studio Code</span></span>

<span data-ttu-id="caae1-105">Mithilfe des Microsoft Teams-Toolkits können Sie benutzerdefinierte Teams-Apps direkt innerhalb der Visual Studio Code-Umgebung erstellen.</span><span class="sxs-lookup"><span data-stu-id="caae1-105">The Microsoft Teams Toolkit enables you to create custom Teams apps directly within the Visual Studio Code environment.</span></span> <span data-ttu-id="caae1-106">Das Toolkit führt Sie durch den Vorgang und bietet alles, was Sie zum Erstellen, Debuggen und Starten Ihrer Teams-App benötigen.</span><span class="sxs-lookup"><span data-stu-id="caae1-106">The toolkit guides you through the process and provides everything you need to build, debug, and launch your Teams app.</span></span>

## <a name="installing-the-teams-toolkit"></a><span data-ttu-id="caae1-107">Installieren des Teams Toolkits</span><span class="sxs-lookup"><span data-stu-id="caae1-107">Installing the Teams Toolkit</span></span>

<span data-ttu-id="caae1-108">Das Microsoft Teams Toolkit für Visual Studio Code steht im [Visual Studio Marketplace](https://aka.ms/teams-toolkit) oder direkt als Erweiterung innerhalb von Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="caae1-108">The Microsoft Teams Toolkit for Visual Studio Code is available for download from the [Visual Studio Marketplace](https://aka.ms/teams-toolkit) or directly as an extension within Visual Studio Code.</span></span>

> [!TIP]
> <span data-ttu-id="caae1-109">Nach der Installation sollte das Teams Toolkit in der Visual Studio Code angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="caae1-109">After installation, you should see the Teams Toolkit in the Visual Studio Code activity bar.</span></span> <span data-ttu-id="caae1-110">Wenn nicht, klicken Sie mit der  rechten Maustaste in der Aktivitätsleiste, und wählen Microsoft Teams, um das Toolkit für den einfachen Zugriff anheften.</span><span class="sxs-lookup"><span data-stu-id="caae1-110">If not, right-click within the activity bar and select **Microsoft Teams** to pin the toolkit for easy access.</span></span>

## <a name="using-the-toolkit"></a><span data-ttu-id="caae1-111">Verwenden des Toolkits</span><span class="sxs-lookup"><span data-stu-id="caae1-111">Using the toolkit</span></span>

- [<span data-ttu-id="caae1-112">Einrichten eines neuen Projekts</span><span class="sxs-lookup"><span data-stu-id="caae1-112">Set up a new project</span></span>](#set-up-a-new-teams-project)
- [<span data-ttu-id="caae1-113">Importieren eines vorhandenen Projekts</span><span class="sxs-lookup"><span data-stu-id="caae1-113">Import an existing project</span></span>](#import-an-existing-teams-app-project)
- [<span data-ttu-id="caae1-114">Konfigurieren Sie die App</span><span class="sxs-lookup"><span data-stu-id="caae1-114">Configure your app</span></span>](#configure-your-app)
- [<span data-ttu-id="caae1-115">Packen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="caae1-115">Package your app</span></span>](#package-your-app)
- [<span data-ttu-id="caae1-116">Führen Sie Ihre App lokal oder in einem Teams</span><span class="sxs-lookup"><span data-stu-id="caae1-116">Run your app locally or in Teams</span></span>](#run-your-app)

## <a name="set-up-a-new-teams-project"></a><span data-ttu-id="caae1-117">Einrichten eines neuen Teams Projekt</span><span class="sxs-lookup"><span data-stu-id="caae1-117">Set up a new Teams project</span></span>

1. <span data-ttu-id="caae1-118">Erstellen Sie einen Arbeitsbereich oder Ordner für Ihr Projekt in Ihrer lokalen Umgebung.</span><span class="sxs-lookup"><span data-stu-id="caae1-118">Create a workspace or folder for your project in your local environment.</span></span>
1. <span data-ttu-id="caae1-119">Wählen Visual Studio Code das Symbol Teams aus.</span><span class="sxs-lookup"><span data-stu-id="caae1-119">In Visual Studio Code, select the Teams icon</span></span> ![Teams-Symbol](../assets/icons/favicon-16x16.png) <span data-ttu-id="caae1-121">aus der Aktivitätsleiste auf der linken Seite des Fensters.</span><span class="sxs-lookup"><span data-stu-id="caae1-121">from the activity bar on the left side of the window.</span></span>
1. <span data-ttu-id="caae1-122">Wählen **Sie im Befehlsmenü Microsoft Teams Toolkit** öffnen aus.</span><span class="sxs-lookup"><span data-stu-id="caae1-122">Select **Open the Microsoft Teams Toolkit** from the command menu.</span></span>
1. <span data-ttu-id="caae1-123">Wählen **Sie im Befehlsmenü Teams Neue** App erstellen aus.</span><span class="sxs-lookup"><span data-stu-id="caae1-123">Select **Create a new Teams app** from the command menu.</span></span>
1. <span data-ttu-id="caae1-124">Wenn Sie dazu aufgefordert werden, geben Sie den Namen des Arbeitsbereichs ein.</span><span class="sxs-lookup"><span data-stu-id="caae1-124">When prompted, enter the name of the workspace .</span></span> <span data-ttu-id="caae1-125">Dies wird sowohl als Name des Ordners verwendet, in dem sich Ihr Projekt befindet, als auch als Standardname Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="caae1-125">This will be used as both the name of the folder where your project will reside, and the default name of your app.</span></span>
1. <span data-ttu-id="caae1-126">Drücken **Sie die** EINGABETASTE, und Sie gelangen zum Bildschirm Funktionen hinzufügen, um die Eigenschaften für Ihre neue App zu konfigurieren. </span><span class="sxs-lookup"><span data-stu-id="caae1-126">Press **Enter** and you will arrive at the **Add capabilities** screen configure the properties for your new app.</span></span>
1. <span data-ttu-id="caae1-127">Wählen Sie die **Schaltfläche Fertig** stellen aus, um den Konfigurationsprozess zu beenden.</span><span class="sxs-lookup"><span data-stu-id="caae1-127">Select the **Finish** button to complete the configuration process.</span></span>

## <a name="import-an-existing-teams-app-project"></a><span data-ttu-id="caae1-128">Importieren eines vorhandenen Teams-App-Projekts</span><span class="sxs-lookup"><span data-stu-id="caae1-128">Import an existing Teams app project</span></span>

1. <span data-ttu-id="caae1-129">Wählen Visual Studio Code das Symbol Teams aus.</span><span class="sxs-lookup"><span data-stu-id="caae1-129">In Visual Studio Code, select the Teams icon</span></span> ![Teams-Symbol](../assets/icons/favicon-16x16.png) <span data-ttu-id="caae1-131">aus der Aktivitätsleiste auf der linken Seite des Fensters.</span><span class="sxs-lookup"><span data-stu-id="caae1-131">from the activity bar on the left side of the window.</span></span>
1. <span data-ttu-id="caae1-132">Wählen **Sie im Befehlsmenü App-Paket** importieren aus.</span><span class="sxs-lookup"><span data-stu-id="caae1-132">Select **Import app package** from the command menu.</span></span>
1. <span data-ttu-id="caae1-133">Wählen Sie Ihre [vorhandene Teams-App-Paket-ZIP-Datei](../concepts/build-and-test/apps-package.md) aus.</span><span class="sxs-lookup"><span data-stu-id="caae1-133">Choose your existing [Teams app package](../concepts/build-and-test/apps-package.md) zip file.</span></span>
1. <span data-ttu-id="caae1-134">Wählen Sie die **Schaltfläche Veröffentlichungspaket auswählen** aus.</span><span class="sxs-lookup"><span data-stu-id="caae1-134">Choose the **Select publishing package** button.</span></span> <span data-ttu-id="caae1-135">Die Konfigurationsregisterkarte des Toolkits sollte nun mit den Details Ihrer App gefüllt werden.</span><span class="sxs-lookup"><span data-stu-id="caae1-135">The configuration tab of the toolkit should now be populated with your app's details.</span></span>
1. <span data-ttu-id="caae1-136">Wählen Visual Studio Code Ordner **zum** Arbeitsbereich hinzufügen aus, um das Quellcodeverzeichnis dem Arbeitsbereich Visual Studio Code  ->   hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="caae1-136">In Visual Studio Code, select **File** -> **Add Folder to Workspace** to add your source code directory to the Visual Studio Code workspace.</span></span>

## <a name="configure-your-app"></a><span data-ttu-id="caae1-137">Konfigurieren Sie die App</span><span class="sxs-lookup"><span data-stu-id="caae1-137">Configure your app</span></span>

<span data-ttu-id="caae1-138">Im Kern umfasst die Teams drei Komponenten:</span><span class="sxs-lookup"><span data-stu-id="caae1-138">At its core, the Teams app embraces three components:</span></span>

  1. <span data-ttu-id="caae1-139">Der Microsoft Teams (Web, Desktop oder Mobile), auf dem Benutzer mit Ihrer App interagieren.</span><span class="sxs-lookup"><span data-stu-id="caae1-139">The Microsoft Teams client (web, desktop or mobile) where users interact with your app.</span></span>
  1. <span data-ttu-id="caae1-140">Ein Server, der auf Anforderungen nach Inhalten reagiert, die in der Teams.</span><span class="sxs-lookup"><span data-stu-id="caae1-140">A server that responds to requests for content that will be displayed in Teams.</span></span> <span data-ttu-id="caae1-141">Beispiel: HTML-Registerkarteninhalt oder eine adaptive Botkarte.</span><span class="sxs-lookup"><span data-stu-id="caae1-141">For example, HTML tab content or a bot adaptive card.</span></span>
  1. <span data-ttu-id="caae1-142">Ein [Teams-App-Paket,](/concepts/build-and-test/apps-package.md) das aus drei Dateien besteht:</span><span class="sxs-lookup"><span data-stu-id="caae1-142">A Teams [app package](/concepts/build-and-test/apps-package.md) consisting of three files:</span></span>

      > [!div class="checklist"]
      >
      > - <span data-ttu-id="caae1-143">Die manifest.jsein.</span><span class="sxs-lookup"><span data-stu-id="caae1-143">The manifest.json.</span></span> 
      > - <span data-ttu-id="caae1-144">Ein [Farbsymbol](../resources/schema/manifest-schema.md#icons) für Ihre App, das im öffentlichen Oder Organisations-App-Katalog angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="caae1-144">A [color icon](../resources/schema/manifest-schema.md#icons) for your app to display in the public or organization app catalog.</span></span>
      > - <span data-ttu-id="caae1-145">Ein [Gliederungssymbol](../resources/schema/manifest-schema.md#icons) für die Anzeige Teams Aktivitätsleiste.</span><span class="sxs-lookup"><span data-stu-id="caae1-145">An [outline icon](../resources/schema/manifest-schema.md#icons) for display on the Teams activity bar.</span></span>

<span data-ttu-id="caae1-146">Wenn eine App installiert ist, analysiert Teams-Client die Manifestdatei, um die erforderlichen Informationen wie den Namen Ihrer App und die URL zu ermitteln, in der sich die Dienste befinden.</span><span class="sxs-lookup"><span data-stu-id="caae1-146">When an app is installed, the Teams client parses the manifest file to determine needed information like the name of your app and the URL where the services are located.</span></span>

1. <span data-ttu-id="caae1-147">Um Ihre App zu konfigurieren, navigieren Sie zur **Registerkarte Microsoft Teams Toolkit** in Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="caae1-147">To configure your app, navigate to the **Microsoft Teams Toolkit** tab in Visual Studio Code.</span></span>
1. <span data-ttu-id="caae1-148">Wählen **Sie App-Paket bearbeiten aus,** um die **Seite App-Details anzuzeigen.**</span><span class="sxs-lookup"><span data-stu-id="caae1-148">Select **Edit app package** to view the **App details** page.</span></span>
1. <span data-ttu-id="caae1-149">Durch Bearbeiten der Felder auf der Seite App-Details werden die Inhalte der datei manifest.jsaktualisiert, die letztendlich als Teil des App-Pakets versandt werden.</span><span class="sxs-lookup"><span data-stu-id="caae1-149">Editing the fields in the App details page updates the contents of the manifest.json file that will ultimately ship as part of the app package.</span></span> <span data-ttu-id="caae1-150">Weitere Informationen finden Sie unter [App Studio-Manifest-Editor.](https://aka.ms/teams-toolkit-manifest)</span><span class="sxs-lookup"><span data-stu-id="caae1-150">For more information, See [App Studio manifest editor](https://aka.ms/teams-toolkit-manifest)</span></span>

## <a name="package-your-app"></a><span data-ttu-id="caae1-151">Packen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="caae1-151">Package your app</span></span>

<span data-ttu-id="caae1-152">Wenn Sie die **App-Details-,**  **Manifest-** oder **ENV-Dateien** im Veröffentlichungsordner Ihrer App ändern, wird ihreDevelopment.zip **generiert.**</span><span class="sxs-lookup"><span data-stu-id="caae1-152">Modifying the **app details** page, **manifest**, or **.env** files in your app's  **.publish** folder will automatically generate your **Development.zip** file.</span></span> <span data-ttu-id="caae1-153">Sie müssen zwei Symbole [in](../concepts/build-and-test/apps-package.md#app-icons) denselben Ordner hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="caae1-153">You'll need to include [two icons](../concepts/build-and-test/apps-package.md#app-icons) in that same folder.</span></span>

## <a name="install-and-run-your-app-locally"></a><span data-ttu-id="caae1-154">Installieren und Ausführen der App lokal</span><span class="sxs-lookup"><span data-stu-id="caae1-154">Install and run your app locally</span></span>

## <a name="run-your-app"></a><span data-ttu-id="caae1-155">Ausführen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="caae1-155">Run your app</span></span>

### <a name="install-and-run-your-app-locally"></a><span data-ttu-id="caae1-156">Installieren und Ausführen der App lokal</span><span class="sxs-lookup"><span data-stu-id="caae1-156">Install and run your app locally</span></span>

<span data-ttu-id="caae1-157">Ausführliche Anweisungen zum **Packen** und Testen Ihrer App finden Sie unter Erstellen und Ausführen von Inhalten in Ihrer Projekthomepage.</span><span class="sxs-lookup"><span data-stu-id="caae1-157">Refer to the **Build and Run** content in your project homepage for detailed instructions on how to package and test your app.</span></span> <span data-ttu-id="caae1-158">Im Allgemeinen müssen Sie den Server Ihrer App installieren, ausführen und dann eine Tunnellösung einrichten, damit Teams auf Inhalte zugreifen können, die von localhost ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="caae1-158">In general, you need to install your app's server, get it running, then setup a tunneling solution so that Teams can access content running from localhost.</span></span>

### <a name="enable-development-from-localhost"></a><span data-ttu-id="caae1-159">Aktivieren der Entwicklung von localhost</span><span class="sxs-lookup"><span data-stu-id="caae1-159">Enable development from localhost</span></span>

<span data-ttu-id="caae1-160">Wenn Sie Ihre registerkartenbasierte App auf localhost mithilfe von HTTPS debuggen möchten, müssen Sie Ihrem Browser mitteilen, dass er der App vertraut, von der sie bedient <https://localhost> wird.</span><span class="sxs-lookup"><span data-stu-id="caae1-160">If you wish to debug your tab based app on localhost using HTTPS, you will need to tell your browser to trust the app being served from <https://localhost>.</span></span> <span data-ttu-id="caae1-161">Navigieren Sie zu <https://localhost:3000/tab>.</span><span class="sxs-lookup"><span data-stu-id="caae1-161">Navigate to <https://localhost:3000/tab>.</span></span> <span data-ttu-id="caae1-162">Wenn eine Warnung angezeigt wird, die angibt, dass die Website nicht vertrauenswürdig ist, wählen Sie die Option aus, um trotzdem fortzufahren.</span><span class="sxs-lookup"><span data-stu-id="caae1-162">If you see a warning indicating that the site isn't trusted, choose the option to proceed anyway.</span></span> <span data-ttu-id="caae1-163">Der Zugriff auf Ihre App sollte jetzt über den Teams sein.</span><span class="sxs-lookup"><span data-stu-id="caae1-163">Your app should now be accessible from the Teams client.</span></span>

### <a name="run-your-app-in-teams"></a><span data-ttu-id="caae1-164">Führen Sie Ihre App in Teams</span><span class="sxs-lookup"><span data-stu-id="caae1-164">Run your app in Teams</span></span>

<span data-ttu-id="caae1-165">Voraussetzungen: [Aktivieren Teams Vorschaumodus für Entwickler](https://aka.ms/teams-toolkit-enable-devpreview)</span><span class="sxs-lookup"><span data-stu-id="caae1-165">Prerequisites: [Enable Teams developer preview mode](https://aka.ms/teams-toolkit-enable-devpreview)</span></span>

1. <span data-ttu-id="caae1-166">Navigieren Sie zur Aktivitätsleiste auf der linken Seite des Visual Studio Code Fensters.</span><span class="sxs-lookup"><span data-stu-id="caae1-166">Navigate to the activity bar on the left side of the Visual Studio Code window.</span></span>
1. <span data-ttu-id="caae1-167">Wählen Sie das **Symbol Ausführen** aus, um die Ansicht Ausführen **und Debuggen anzeigen.**</span><span class="sxs-lookup"><span data-stu-id="caae1-167">Select the **Run** icon to display the **Run and Debug** view.</span></span>
1. <span data-ttu-id="caae1-168">Sie können auch die Tastenkombination `Ctrl+Shift+D` verwenden.</span><span class="sxs-lookup"><span data-stu-id="caae1-168">You can also use the keyboard shortcut `Ctrl+Shift+D`.</span></span>

## <a name="next-step"></a><span data-ttu-id="caae1-169">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="caae1-169">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="caae1-170">Verwalten und Unterstützen Ihrer veröffentlichten App</span><span class="sxs-lookup"><span data-stu-id="caae1-170">Maintaining and supporting your published app</span></span>](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
