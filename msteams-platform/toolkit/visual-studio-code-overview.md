---
title: Erstellen von apps mit dem Microsoft Teams-Toolkit und Visual Studio Code
description: Erste Schritte beim Erstellen großartiger benutzerdefinierter apps direkt in Visual Studio Code mit dem Microsoft Teams-Toolkit
keywords: Teams Visual Studio Code Toolkit
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: 41b0eeaeef1c7094fc9c8cbdc05c2db899245fc6
ms.sourcegitcommit: 7e47bf158249050c36d97509eea00e77089a54e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "49476930"
---
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio-code"></a><span data-ttu-id="8ca91-104">Erstellen von apps mit dem Teams-Toolkit und Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="8ca91-104">Build apps with the Teams Toolkit and Visual Studio Code</span></span>

<span data-ttu-id="8ca91-105">Mithilfe des Microsoft Teams-Toolkits können Sie benutzerdefinierte Teams-Apps direkt innerhalb der Visual Studio Code-Umgebung erstellen.</span><span class="sxs-lookup"><span data-stu-id="8ca91-105">The Microsoft Teams Toolkit enables you to create custom Teams apps directly within the Visual Studio Code environment.</span></span> <span data-ttu-id="8ca91-106">Das Toolkit führt Sie durch den Vorgang und bietet alles, was Sie zum Erstellen, Debuggen und Starten Ihrer Teams-App benötigen.</span><span class="sxs-lookup"><span data-stu-id="8ca91-106">The toolkit guides you through the process and provides everything you need to build, debug, and launch your Teams app.</span></span>

## <a name="installing-the-teams-toolkit"></a><span data-ttu-id="8ca91-107">Installieren des Teams-Toolkits</span><span class="sxs-lookup"><span data-stu-id="8ca91-107">Installing the Teams Toolkit</span></span>

<span data-ttu-id="8ca91-108">Das Microsoft Teams-Toolkit für Visual Studio Code steht vom [Visual Studio Marketplace](https://aka.ms/teams-toolkit) oder direkt als Erweiterung innerhalb Visual Studio Codes zum Download zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="8ca91-108">The Microsoft Teams Toolkit for Visual Studio Code is available for download from the [Visual Studio Marketplace](https://aka.ms/teams-toolkit) or directly as an extension within Visual Studio Code.</span></span>

> [!TIP]
> <span data-ttu-id="8ca91-109">Nach der Installation sollte das Teams-Toolkit in der Leiste Visual Studio Code-Aktivität angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="8ca91-109">After installation, you should see the Teams Toolkit in the Visual Studio Code activity bar.</span></span> <span data-ttu-id="8ca91-110">Wenn dies nicht der Fall ist, klicken Sie mit der rechten Maustaste in die Aktivitäts Leiste, und wählen Sie **Microsoft Teams** aus, um das Toolkit für einfachen Zugriff zu fixieren</span><span class="sxs-lookup"><span data-stu-id="8ca91-110">If not, right-click within the activity bar and select **Microsoft Teams** to pin the toolkit for easy access.</span></span>

## <a name="using-the-toolkit"></a><span data-ttu-id="8ca91-111">Verwenden des Toolkits</span><span class="sxs-lookup"><span data-stu-id="8ca91-111">Using the toolkit</span></span>

- [<span data-ttu-id="8ca91-112">Einrichten eines neuen Projekts</span><span class="sxs-lookup"><span data-stu-id="8ca91-112">Set up a new project</span></span>](#set-up-a-new-teams-project)
- [<span data-ttu-id="8ca91-113">Importieren eines vorhandenen Projekts</span><span class="sxs-lookup"><span data-stu-id="8ca91-113">Import an existing project</span></span>](#import-an-existing-teams-app-project)
- [<span data-ttu-id="8ca91-114">Konfigurieren Sie die App</span><span class="sxs-lookup"><span data-stu-id="8ca91-114">Configure your app</span></span>](#configure-your-app)
- [<span data-ttu-id="8ca91-115">Verpacken Ihrer APP</span><span class="sxs-lookup"><span data-stu-id="8ca91-115">Package your app</span></span>](#package-your-app)
- [<span data-ttu-id="8ca91-116">Ausführen der APP lokal oder in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="8ca91-116">Run your app locally or in Teams</span></span>](#run-your-app)

## <a name="set-up-a-new-teams-project"></a><span data-ttu-id="8ca91-117">Einrichten eines neuen Teams-Projekts</span><span class="sxs-lookup"><span data-stu-id="8ca91-117">Set up a new Teams project</span></span>

1. <span data-ttu-id="8ca91-118">Erstellen Sie in Ihrer lokalen Umgebung einen Arbeitsbereich/Ordner für Ihr Projekt.</span><span class="sxs-lookup"><span data-stu-id="8ca91-118">Create a workspace/folder for your project in your local environment.</span></span>
1. <span data-ttu-id="8ca91-119">Wählen Sie in Visual Studio Code das Symbol Teams aus.</span><span class="sxs-lookup"><span data-stu-id="8ca91-119">In Visual Studio Code, select the Teams icon</span></span> ![Teams-Symbol](../assets/icons/favicon-16x16.png) <span data-ttu-id="8ca91-121">in der Aktivitäts Leiste auf der linken Seite des Fensters.</span><span class="sxs-lookup"><span data-stu-id="8ca91-121">from the activity bar on the left side of the window.</span></span>
1. <span data-ttu-id="8ca91-122">Wählen Sie im Menü Command **die Option Microsoft Teams Toolkit öffnen** aus.</span><span class="sxs-lookup"><span data-stu-id="8ca91-122">Select **Open the Microsoft Teams Toolkit** from the command menu.</span></span>
1. <span data-ttu-id="8ca91-123">Wählen Sie im Menü Command die Option **neue Teams-app erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="8ca91-123">Select **Create a new Teams app** from the command menu.</span></span>
1. <span data-ttu-id="8ca91-124">Wenn Sie dazu aufgefordert werden, geben Sie den Namen des Arbeitsbereichs ein.</span><span class="sxs-lookup"><span data-stu-id="8ca91-124">When prompted, enter the name of the workspace .</span></span> <span data-ttu-id="8ca91-125">Dies wird sowohl als Name des Ordners, in dem sich Ihr Projekt befindet, als auch als Standardname Ihrer APP verwendet.</span><span class="sxs-lookup"><span data-stu-id="8ca91-125">This will be used as both the name of the folder where your project will reside, and the default name of your app.</span></span>
1. <span data-ttu-id="8ca91-126">Drücken Sie die **EINGABETASTE** , und Sie gelangen auf den Bildschirm **Funktionen hinzufügen** , um die Eigenschaften ihrer neuen App zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="8ca91-126">Press **Enter** and you will arrive at the **Add capabilities** screen configure the properties for your new app.</span></span>
1. <span data-ttu-id="8ca91-127">Klicken Sie auf die Schaltfläche **Fertig stellen** , um den Konfigurationsprozess abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="8ca91-127">Select the **Finish** button to complete the configuration process.</span></span>

## <a name="import-an-existing-teams-app-project"></a><span data-ttu-id="8ca91-128">Importieren eines vorhandenen Teams-App-Projekts</span><span class="sxs-lookup"><span data-stu-id="8ca91-128">Import an existing Teams app project</span></span>

1. <span data-ttu-id="8ca91-129">Wählen Sie in Visual Studio Code das Symbol Teams aus.</span><span class="sxs-lookup"><span data-stu-id="8ca91-129">In Visual Studio Code, select the Teams icon</span></span> ![Teams-Symbol](../assets/icons/favicon-16x16.png) <span data-ttu-id="8ca91-131">in der Aktivitäts Leiste auf der linken Seite des Fensters.</span><span class="sxs-lookup"><span data-stu-id="8ca91-131">from the activity bar on the left side of the window.</span></span>
1. <span data-ttu-id="8ca91-132">Wählen Sie im Menü Command die Option **App-Paket importieren** aus.</span><span class="sxs-lookup"><span data-stu-id="8ca91-132">Select **Import app package** from the command menu.</span></span>
1. <span data-ttu-id="8ca91-133">Wählen Sie die ZIP-Datei des vorhandenen [Teams-App-Pakets](../concepts/build-and-test/apps-package.md) aus.</span><span class="sxs-lookup"><span data-stu-id="8ca91-133">Choose your existing [Teams app package](../concepts/build-and-test/apps-package.md) zip file.</span></span>
1. <span data-ttu-id="8ca91-134">Klicken Sie auf die Schaltfläche **veröffentlichungspaket auswählen** .</span><span class="sxs-lookup"><span data-stu-id="8ca91-134">Choose the **Select publishing package** button.</span></span> <span data-ttu-id="8ca91-135">Die Registerkarte Konfiguration des Toolkits sollte nun mit den Details Ihrer APP aufgefüllt werden.</span><span class="sxs-lookup"><span data-stu-id="8ca91-135">The configuration tab of the toolkit should now be populated with your app's details.</span></span>
1. <span data-ttu-id="8ca91-136">Wählen Sie in Visual Studio Code **Datei**  ->  **Ordner zu Arbeitsbereich hinzufügen** aus, um das Quell Code Verzeichnis dem Arbeitsbereich Visual Studio Code hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="8ca91-136">In Visual Studio Code, select **File** -> **Add Folder to Workspace** to add your source code directory to the Visual Studio Code workspace.</span></span>

## <a name="configure-your-app"></a><span data-ttu-id="8ca91-137">Konfigurieren Sie die App</span><span class="sxs-lookup"><span data-stu-id="8ca91-137">Configure your app</span></span>

<span data-ttu-id="8ca91-138">Im Kern umfasst die Teams-app drei Komponenten:</span><span class="sxs-lookup"><span data-stu-id="8ca91-138">At its core, the Teams app embraces three components:</span></span>

  1. <span data-ttu-id="8ca91-139">Der Microsoft Teams-Client ("Internet", "Desktop" oder "Mobil"), auf dem Benutzer mit Ihrer APP interagieren.</span><span class="sxs-lookup"><span data-stu-id="8ca91-139">The Microsoft Teams client (web, desktop or mobile) where users interact with your app.</span></span>
  1. <span data-ttu-id="8ca91-140">Ein Server, der auf Anforderungen für Inhalte reagiert, die in Microsoft Teams angezeigt werden, beispielsweise HTML-Registerkarteninhalte oder eine bot-Adaptive Karte.</span><span class="sxs-lookup"><span data-stu-id="8ca91-140">A server that responds to requests for content that will be displayed in Teams, e.g., HTML tab content or a bot adaptive card .</span></span>
  1. <span data-ttu-id="8ca91-141">Ein Teams- [App-Paket](/concepts/build-and-test/apps-package.md) , bestehend aus drei Dateien:</span><span class="sxs-lookup"><span data-stu-id="8ca91-141">A Teams [app package](/concepts/build-and-test/apps-package.md) consisting of three files:</span></span>

  > [!div class="checklist"]
  >
  > - <span data-ttu-id="8ca91-142">Die manifest.jsauf</span><span class="sxs-lookup"><span data-stu-id="8ca91-142">The manifest.json</span></span> 
  > - <span data-ttu-id="8ca91-143">Ein [Farbsymbol](../resources/schema/manifest-schema.md#icons) für Ihre APP, das im öffentlichen oder im Organisations-App-Katalog angezeigt wird</span><span class="sxs-lookup"><span data-stu-id="8ca91-143">A [color icon](../resources/schema/manifest-schema.md#icons) for your app to display in the public or organization app catalog</span></span>
 > - <span data-ttu-id="8ca91-144">Ein [Gliederungssymbol](../resources/schema/manifest-schema.md#icons) für die Anzeige in der Microsoft Teams-Aktivitäts Leiste.</span><span class="sxs-lookup"><span data-stu-id="8ca91-144">An [outline icon](../resources/schema/manifest-schema.md#icons) for display on the Teams activity bar.</span></span>

<span data-ttu-id="8ca91-145">Wenn eine APP installiert ist, analysiert der Microsoft Teams-Client die Manifestdatei, um benötigte Informationen wie den Namen Ihrer APP und die URL zu ermitteln, in der sich die Dienste befinden.</span><span class="sxs-lookup"><span data-stu-id="8ca91-145">When an app is installed, the Teams client parses the manifest file to determine needed information like the name of your app and the URL where the services are located.</span></span>

1. <span data-ttu-id="8ca91-146">Um Ihre APP zu konfigurieren, navigieren Sie in Visual Studio Code zur Registerkarte **Microsoft Teams Toolkit** .</span><span class="sxs-lookup"><span data-stu-id="8ca91-146">To configure your app, navigate to the **Microsoft Teams Toolkit** tab in Visual Studio Code.</span></span>
1. <span data-ttu-id="8ca91-147">Wählen Sie **App-Paket bearbeiten** aus, um die Seite **App-Details** anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="8ca91-147">Select **Edit app package** to view the **App details** page.</span></span>
1. <span data-ttu-id="8ca91-148">Durch das Bearbeiten der Felder auf der Seite mit den App-Details wird der Inhalt der manifest.jsauf Datei aktualisiert, die letztendlich als Teil des App-Pakets ausgeliefert wird.</span><span class="sxs-lookup"><span data-stu-id="8ca91-148">Editing the fields in the App details page updates the contents of the manifest.json file that will ultimately ship as part of the app package.</span></span> <span data-ttu-id="8ca91-149">*Siehe* [App Studio-Manifest-Editor](https://aka.ms/teams-toolkit-manifest)</span><span class="sxs-lookup"><span data-stu-id="8ca91-149">*See* [App Studio manifest editor](https://aka.ms/teams-toolkit-manifest)</span></span>

## <a name="package-your-app"></a><span data-ttu-id="8ca91-150">Verpacken Ihrer APP</span><span class="sxs-lookup"><span data-stu-id="8ca91-150">Package your app</span></span>

<span data-ttu-id="8ca91-151">Wenn Sie die Seite " **App-Details** " ändern oder das **Manifest** oder **. env** -Dateien im Ordner "  **. Publish** " Ihrer APP aktualisieren, wird die **Development.zip** Datei automatisch generiert.</span><span class="sxs-lookup"><span data-stu-id="8ca91-151">Modifying the **app details** page or updating the **manifest**, or **.env** files in your app's  **.publish** folder will automatically generate your **Development.zip** file.</span></span> <span data-ttu-id="8ca91-152">Sie müssen [zwei Symbole](../concepts/build-and-test/apps-package.md#icons) in den gleichen Ordner einschließen.</span><span class="sxs-lookup"><span data-stu-id="8ca91-152">You'll need to include [two icons](../concepts/build-and-test/apps-package.md#icons) in that same folder.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="8ca91-153">Ausführen der APP</span><span class="sxs-lookup"><span data-stu-id="8ca91-153">Run your app</span></span>

### <a name="install-and-run-your-app-locally"></a><span data-ttu-id="8ca91-154">Lokal installieren und Ausführen der APP</span><span class="sxs-lookup"><span data-stu-id="8ca91-154">Install and run your app locally</span></span>

<span data-ttu-id="8ca91-155">Ausführliche Anweisungen zum Verpacken und Testen Ihrer APP erhalten Sie im Abschnitt \**Erstellen und ausführen* von Inhalten auf der Startseite des Projekts.</span><span class="sxs-lookup"><span data-stu-id="8ca91-155">Refer to the \**Build and Run* content in your project homepage for detailed instructions on how to package and test your app.</span></span> <span data-ttu-id="8ca91-156">Im Allgemeinen müssen Sie den Server Ihrer APP installieren, ihn ausführen lassen und dann eine Tunnellösung einrichten, damit Teams auf Inhalte zugreifen können, die von localhost aus gestartet werden.</span><span class="sxs-lookup"><span data-stu-id="8ca91-156">In general, you need to install your app's server, get it running, then setup a tunneling solution so that Teams can access content running from localhost.</span></span>

### <a name="enable-development-from-localhost"></a><span data-ttu-id="8ca91-157">Aktivieren der Entwicklung von localhost</span><span class="sxs-lookup"><span data-stu-id="8ca91-157">Enable development from localhost</span></span>

<span data-ttu-id="8ca91-158">Wenn Sie Ihre registerkartenbasierte App auf localhost mithilfe von HTTPS debuggen möchten, müssen Sie Ihrem Browser mitteilen, dass der APP, von der bedient wird, Vertrauen muss <https://localhost> .</span><span class="sxs-lookup"><span data-stu-id="8ca91-158">If you wish to debug your tab based app on localhost using HTTPS, you will need to tell your browser to trust the app being served from <https://localhost>.</span></span> <span data-ttu-id="8ca91-159">Navigieren Sie zu <https://localhost:3000/tab>.</span><span class="sxs-lookup"><span data-stu-id="8ca91-159">Navigate to <https://localhost:3000/tab>.</span></span> <span data-ttu-id="8ca91-160">Wenn eine Warnung angezeigt wird, die besagt, dass die Website nicht vertrauenswürdig ist, wählen Sie die Option aus, um den Vorgang fortzusetzen.</span><span class="sxs-lookup"><span data-stu-id="8ca91-160">If you see a warning indicating that the site isn't trusted, choose the option to proceed anyway.</span></span> <span data-ttu-id="8ca91-161">Auf Ihre APP sollte nun über den Teams-Client zugegriffen werden.</span><span class="sxs-lookup"><span data-stu-id="8ca91-161">Your app should now be accessible from the Teams client.</span></span>

### <a name="run-your-app-in-teams"></a><span data-ttu-id="8ca91-162">Ausführen ihrer app in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="8ca91-162">Run your app in Teams</span></span>

<span data-ttu-id="8ca91-163">Voraussetzungen: Aktivieren von Microsoft [Teams Developer Preview Mode](https://aka.ms/teams-toolkit-enable-devpreview)</span><span class="sxs-lookup"><span data-stu-id="8ca91-163">Prerequisites: [Enable Teams developer preview mode](https://aka.ms/teams-toolkit-enable-devpreview)</span></span>

1. <span data-ttu-id="8ca91-164">Navigieren Sie auf der linken Seite des Visual Studio Code Fensters zur Aktivitäts Leiste.</span><span class="sxs-lookup"><span data-stu-id="8ca91-164">Navigate to the activity bar on the left side of the Visual Studio Code window.</span></span>
1. <span data-ttu-id="8ca91-165">Wählen Sie das Symbol **Ausführen** aus, um die Ansicht **ausführen und Debuggen** anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="8ca91-165">Select the **Run** icon to display the **Run and Debug** view.</span></span>
1. <span data-ttu-id="8ca91-166">Sie können auch die Tastenkombination verwenden `Ctrl+Shift+D` .</span><span class="sxs-lookup"><span data-stu-id="8ca91-166">You can also use the keyboard shortcut `Ctrl+Shift+D`.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8ca91-167">Nächster Schritt: Verwalten und unterstützen Ihrer veröffentlichten App</span><span class="sxs-lookup"><span data-stu-id="8ca91-167">Next step: Maintaining and supporting your published app</span></span>](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
