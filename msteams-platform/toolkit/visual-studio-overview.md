---
title: Erstellen von Apps mit dem Teams-Toolkit und Visual Studio
description: Erste Schritte beim Erstellen großartiger benutzerdefinierter Apps direkt in Visual Studio mit dem Microsoft Teams-Toolkit
keywords: Visual Studio-Toolkit für Teams
localization_priority: Normal
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: 996037f5bb1caaa2493e1eebe51039724822fef9
ms.sourcegitcommit: 9f499908437655d6ebdc6c4b3c3603ee220315b7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2021
ms.locfileid: "52949700"
---
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio"></a><span data-ttu-id="709f4-104">Erstellen von Apps mit dem Teams-Toolkit und Visual Studio</span><span class="sxs-lookup"><span data-stu-id="709f4-104">Build apps with the Teams Toolkit and Visual Studio</span></span>

<span data-ttu-id="709f4-105">Mithilfe des Microsoft Teams-Toolkits können Sie benutzerdefinierte Teams-Apps direkt innerhalb der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) von Visual Studio erstellen.</span><span class="sxs-lookup"><span data-stu-id="709f4-105">The Microsoft Teams Toolkit enables you to create custom Teams apps directly within the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="709f4-106">Das Microsoft Teams-Toolkit führt Sie durch den Vorgang und bietet alles, was Sie zum Erstellen, Debuggen und Starten Ihrer Teams-App benötigen.</span><span class="sxs-lookup"><span data-stu-id="709f4-106">The Microsoft Teams toolkit guides you through the process and provides everything you need to build, debug, and launch your Teams app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="709f4-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="709f4-107">Prerequisites</span></span>

1. <span data-ttu-id="709f4-108">[Aktivieren Sie die Entwicklervorschau.](../resources/dev-preview/developer-preview-intro.md#enable-developer-preview)</span><span class="sxs-lookup"><span data-stu-id="709f4-108">[Enable developer preview](../resources/dev-preview/developer-preview-intro.md#enable-developer-preview).</span></span>

1. <span data-ttu-id="709f4-109">Stellen Sie sicher, dass der Visual Studio-Instanz das **<span>ASP.NE</span>T- und Webentwicklungsmodul** hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="709f4-109">Make sure that the **<span>ASP.NE</span>T and web development module** has been added to your Visual Studio instance.</span></span> <span data-ttu-id="709f4-110">Sie können dies überprüfen, indem Sie die Schritte im Ändern von Visual Studio ausführen, [indem Sie Workloads und Komponentendokumentation hinzufügen oder entfernen.](/visualstudio/install/modify-visual-studio?view=vs-2019&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="709f4-110">You can check by following the steps in the [modify Visual Studio by adding or removing workloads and component](/visualstudio/install/modify-visual-studio?view=vs-2019&preserve-view=true) documentation.</span></span>

![Visual Studio asp.net-Modul](../assets/images/visual-studio-web-dev-module.png)

3. <span data-ttu-id="709f4-112">Wenn Sie Ihre App testen möchten, indem Sie sie in Visual Studio bereitstellen, müssen Sie Internetinformationsdienste (Internet Information Services, IIS)) in Ihrer Entwicklungsumgebung installiert haben.</span><span class="sxs-lookup"><span data-stu-id="709f4-112">If you want to test your app by deploying it from Visual Studio, you must have Internet Information Services (IIS)) installed in your development environment.</span></span> <span data-ttu-id="709f4-113">Visual Studio enthält iis nicht und ist nicht in der Standardkonfiguration für Windows 10, Windows 8 oder Windows 7 enthalten. Sie können jedoch die neueste Version aus dem [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=48264)herunterladen.</span><span class="sxs-lookup"><span data-stu-id="709f4-113">Visual Studio does not include IIS and it is not included in the default Windows 10, Windows 8, or Windows 7 configuration; however, you can download the latest version from the [Microsoft download center](https://www.microsoft.com/download/details.aspx?id=48264).</span></span>

![IIS-Downloadseitenansicht](../assets/images/iis.png)

## <a name="install-the-teams-toolkit"></a><span data-ttu-id="709f4-115">Installieren des Teams-Toolkits</span><span class="sxs-lookup"><span data-stu-id="709f4-115">Install the Teams Toolkit</span></span>

<span data-ttu-id="709f4-116">Das Microsoft Teams-Toolkit für Visual Studio steht im [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.vsteamstemplate) oder direkt über das Menü **"Erweiterungen"** in Visual Studio zum Download zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="709f4-116">The Microsoft Teams Toolkit for Visual Studio is available for download from the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.vsteamstemplate) or directly from the **Extensions** menu within Visual Studio.</span></span> <span data-ttu-id="709f4-117">Laden Sie auch das [Teams-Toolkit für Visual Studio 2019](https://marketplace.visualstudio.com/items?itemName=msft-vsteamstoolkit.vsteamstoolkit)aus dem Visual Studio Marketplace herunter.</span><span class="sxs-lookup"><span data-stu-id="709f4-117">From the Visual Studio Marketplace also download [Teams Toolkit for Visual Studio 2019](https://marketplace.visualstudio.com/items?itemName=msft-vsteamstoolkit.vsteamstoolkit).</span></span>

## <a name="using-the-toolkit"></a><span data-ttu-id="709f4-118">Verwenden des Toolkits</span><span class="sxs-lookup"><span data-stu-id="709f4-118">Using the toolkit</span></span>

- [<span data-ttu-id="709f4-119">Einrichten eines neuen Projekts</span><span class="sxs-lookup"><span data-stu-id="709f4-119">Set up a new project</span></span>](#set-up-a-new-teams-project)
- [<span data-ttu-id="709f4-120">Konfigurieren Sie die App</span><span class="sxs-lookup"><span data-stu-id="709f4-120">Configure your app</span></span>](#configure-your-app)
- [<span data-ttu-id="709f4-121">Verpacken Ihrer App</span><span class="sxs-lookup"><span data-stu-id="709f4-121">Package your app</span></span>](#package-your-app)
- [<span data-ttu-id="709f4-122">Installieren und Ausführen Ihrer App in Teams</span><span class="sxs-lookup"><span data-stu-id="709f4-122">Install and run your app in Teams</span></span>](#install-and-run-your-app-locally)
- [<span data-ttu-id="709f4-123">Validieren Ihrer App</span><span class="sxs-lookup"><span data-stu-id="709f4-123">Validate your app</span></span>](#validate-your-app)
- [<span data-ttu-id="709f4-124">Veröffentlichen eigener Apps</span><span class="sxs-lookup"><span data-stu-id="709f4-124">Publish your app</span></span>](#publish-your-app-to-teams)

## <a name="set-up-a-new-teams-project"></a><span data-ttu-id="709f4-125">Einrichten eines neuen Teams-Projekts</span><span class="sxs-lookup"><span data-stu-id="709f4-125">Set up a new Teams project</span></span>

![Teams-Toolkit installiert](../assets/images/teamstoolkiticon.png)

1. <span data-ttu-id="709f4-127">Klicken Sie auf **Neues Projekt erstellen**.</span><span class="sxs-lookup"><span data-stu-id="709f4-127">Select **Create New Project**.</span></span>

    ![Erstellen eines neuen Projekts](../assets/images/createnewproject.png)

1. <span data-ttu-id="709f4-129">Wählen Sie das Schnellstarttool für **die Microsoft Teams-App** aus, und wählen Sie **"Weiter"** aus.</span><span class="sxs-lookup"><span data-stu-id="709f4-129">Choose the quickstart tool for **Microsoft Teams App** and select **Next**.</span></span>
1. <span data-ttu-id="709f4-130">Geben Sie auf der Seite **"Neues Projekt konfigurieren"** den **Projektnamen,** **den Speicherort** und den **Projektmappennamen** ein.</span><span class="sxs-lookup"><span data-stu-id="709f4-130">In the **Configure your new project** page, enter the **Project name**, **Location**, and **Solution name**.</span></span>
1. <span data-ttu-id="709f4-131">Aktivieren Sie das Kontrollkästchen **"Projektmappe und Projekt im selben Verzeichnis** platzieren".</span><span class="sxs-lookup"><span data-stu-id="709f4-131">Select the **Place solution and project in the same directory** checkbox.</span></span>
1. <span data-ttu-id="709f4-132">Wählen Sie im Popupfenster **"Funktionen hinzufügen"** eine oder mehrere Funktionen für das Projektsetup aus.</span><span class="sxs-lookup"><span data-stu-id="709f4-132">In the **Add Capabilities** pop-up window, choose one or more capabilities for your project setup.</span></span>
1. <span data-ttu-id="709f4-133">Wählen Sie die Schaltfläche **"Weiter"** aus, um den Konfigurationsprozess abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="709f4-133">Select the **Next** button to complete the configuration process.</span></span>
1. <span data-ttu-id="709f4-134">Wählen Sie im Popupfenster **"Funktionen hinzufügen"** die Eigenschaften für jede ausgewählte Funktion aus.</span><span class="sxs-lookup"><span data-stu-id="709f4-134">In the **Add Capabilities** pop-up window, choose the properties for each selected capability.</span></span>
1. <span data-ttu-id="709f4-135">Klicken Sie auf **Fertigstellen**.</span><span class="sxs-lookup"><span data-stu-id="709f4-135">Select **Finish**.</span></span> <span data-ttu-id="709f4-136">Die Startseite des **Microsoft Teams-Toolkits** wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="709f4-136">The **Microsoft Teams Toolkit** landing page is shown.</span></span>

    ![Startseite des Teams-Toolkits](../assets/images/Teamstoolkitpage.png)

## <a name="configure-your-app"></a><span data-ttu-id="709f4-138">Konfigurieren Sie die App</span><span class="sxs-lookup"><span data-stu-id="709f4-138">Configure your app</span></span>

<span data-ttu-id="709f4-139">Im Kern umfasst die Teams-App drei Komponenten:</span><span class="sxs-lookup"><span data-stu-id="709f4-139">At its core, the Teams app embraces three components:</span></span>

  1. <span data-ttu-id="709f4-140">Der Microsoft Teams-Client, einschließlich Web, Desktop oder Mobil, in dem Benutzer mit Ihrer App interagieren.</span><span class="sxs-lookup"><span data-stu-id="709f4-140">The Microsoft Teams client including web, desktop, or mobile, where users interact with your app.</span></span>
  1. <span data-ttu-id="709f4-141">Ein Server, der auf Anforderungen für Inhalte reagiert, die in Teams angezeigt werden, z. B. HTML-Registerkarteninhalte oder eine adaptive Bot-Karte.</span><span class="sxs-lookup"><span data-stu-id="709f4-141">A server that responds to requests for content that is displayed in Teams, for example, HTML tab content or a bot adaptive card.</span></span>
  1. <span data-ttu-id="709f4-142">Ein Teams-App-Paket besteht aus drei Dateien:</span><span class="sxs-lookup"><span data-stu-id="709f4-142">A Teams app package consists of three files:</span></span>

      - <span data-ttu-id="709f4-143">Die manifest.json</span><span class="sxs-lookup"><span data-stu-id="709f4-143">The manifest.json</span></span>
      - <span data-ttu-id="709f4-144">Ein [Farbsymbol](../resources/schema/manifest-schema.md#icons) für Ihre App, das im öffentlichen App- oder Organisations-App-Katalog angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="709f4-144">A [color icon](../resources/schema/manifest-schema.md#icons) for your app to display in the public or organization app catalog.</span></span>
      - <span data-ttu-id="709f4-145">Ein [Gliederungssymbol](../resources/schema/manifest-schema.md#icons) für die Anzeige auf der Teams-Aktivitätsleiste.</span><span class="sxs-lookup"><span data-stu-id="709f4-145">An [outline icon](../resources/schema/manifest-schema.md#icons) for display on the Teams activity bar.</span></span>

<span data-ttu-id="709f4-146">Wenn eine App installiert ist, analysiert der Teams-Client die Manifestdatei, um die erforderlichen Informationen wie den Namen Ihrer App und die URL zu ermitteln, unter der sich die Dienste befinden.</span><span class="sxs-lookup"><span data-stu-id="709f4-146">When an app is installed, the Teams client parses the manifest file to determine needed information like the name of your app and the URL where the services are located.</span></span>

> [!NOTE]
><span data-ttu-id="709f4-147">Wenn sie dies noch nicht getan haben, müssen Sie sich bei Ihrem Microsoft 365-Konto anmelden, um den Entwicklungsprozess fortzusetzen.</span><span class="sxs-lookup"><span data-stu-id="709f4-147">If you have not done so already, you must sign in to your Microsoft 365 account to continue with the development process.</span></span>
>
> <span data-ttu-id="709f4-148">Wenn Sie kein Microsoft 365-Konto haben, können Sie sich für ein Abonnement des [Microsoft 365-Entwicklerprogramms](https://developer.microsoft.com/microsoft-365/dev-program) registrieren.</span><span class="sxs-lookup"><span data-stu-id="709f4-148">If you do not have a Microsoft 365 account, you can sign up for a [Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program) subscription.</span></span> <span data-ttu-id="709f4-149">Es ist 90 Tage kostenlos und wird verlängert, solange Sie es für Entwicklungsaktivitäten verwenden.</span><span class="sxs-lookup"><span data-stu-id="709f4-149">It's free for 90 days and renews as long as you are using it for development activity.</span></span> <span data-ttu-id="709f4-150">Wenn Sie über ein Visual Studio Enterprise- oder Professional-Abonnement verfügen, enthalten beide Programme ein kostenloses Microsoft [365-Entwicklerabonnement,](https://aka.ms/MyVisualStudioBenefits)das für die Lebensdauer Ihres Visual Studio-Abonnements aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="709f4-150">If you have a Visual Studio Enterprise or Professional subscription, both programs include a free Microsoft 365 [developer subscription](https://aka.ms/MyVisualStudioBenefits), active for the life of your Visual Studio subscription.</span></span> <span data-ttu-id="709f4-151">Weitere Informationen finden Sie unter [Einrichten eines Microsoft 365-Entwicklerabonnements.](/office/developer-program/office-365-developer-program-get-started)</span><span class="sxs-lookup"><span data-stu-id="709f4-151">For more information, see [set up a Microsoft 365 developer subscription](/office/developer-program/office-365-developer-program-get-started).</span></span>

### <a name="configuration-steps"></a><span data-ttu-id="709f4-152">Konfigurationsschritte </span><span class="sxs-lookup"><span data-stu-id="709f4-152">Configuration steps</span></span>

1. <span data-ttu-id="709f4-153">Um Ihre App zu konfigurieren, wählen Sie auf der Startseite des **Microsoft Teams-Toolkits** **"App-Paket bearbeiten"** aus.</span><span class="sxs-lookup"><span data-stu-id="709f4-153">To configure your app, on the **Microsoft Teams Toolkit** landing page, select **Edit app package**.</span></span>
1. <span data-ttu-id="709f4-154">Wählen Sie im Dropdownmenü **"Meine Umgebungen"** die Option **"Entwicklung"** aus.</span><span class="sxs-lookup"><span data-stu-id="709f4-154">From the **My Environments** drop-down menu, select **development**.</span></span>
1. <span data-ttu-id="709f4-155">Bearbeiten Sie auf der Seite **"App-Details"** die Eigenschaftenfelder Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="709f4-155">In the **App details** page, edit your app's property fields.</span></span>
    
    <span data-ttu-id="709f4-156">Durch das Bearbeiten der Felder auf der Seite "App-Details" wird der Inhalt der manifest.jsauf der Datei aktualisiert, die als Teil des App-Pakets ausgeliefert wird.</span><span class="sxs-lookup"><span data-stu-id="709f4-156">Editing the fields in the App details page updates the contents of the manifest.json file that will ship as part of the app package.</span></span> <span data-ttu-id="709f4-157">Weitere Informationen finden Sie im [Teams-Toolkit-Manifest.](https://aka.ms/teams-toolkit-manifest)</span><span class="sxs-lookup"><span data-stu-id="709f4-157">For more information, see [Teams Toolkit manifest](https://aka.ms/teams-toolkit-manifest).</span></span>

## <a name="package-your-app"></a><span data-ttu-id="709f4-158">Verpacken Ihrer App</span><span class="sxs-lookup"><span data-stu-id="709f4-158">Package your app</span></span>

<span data-ttu-id="709f4-159">Wenn Sie die **App-Detailseite** ändern oder das **Manifest** oder **ENV-Dateien** im  **Veröffentlichungsordner** Ihrer App aktualisieren, wird automatisch Ihre **Development.zip** Datei generiert.</span><span class="sxs-lookup"><span data-stu-id="709f4-159">Modifying the **app details** page or updating the **manifest**, or **.env** files in your app's  **.publish** folder will automatically generate your **Development.zip** file.</span></span> <span data-ttu-id="709f4-160">Die Development.zip-Datei enthält drei erforderliche Dateien, die **manifest.jsund** [zwei Symbole.](../concepts/build-and-test/apps-package.md#app-icons)</span><span class="sxs-lookup"><span data-stu-id="709f4-160">The Development.zip file includes three required files, the **manifest.json** and [two icons](../concepts/build-and-test/apps-package.md#app-icons).</span></span>

## <a name="install-and-run-your-app-locally"></a><span data-ttu-id="709f4-161">Lokales Installieren und Ausführen der App</span><span class="sxs-lookup"><span data-stu-id="709f4-161">Install and run your app locally</span></span>

1. <span data-ttu-id="709f4-162">Wählen Sie im Dropdownmenü **"Lösungskonfigurationen"** die Option **"Bereitstellen"** aus, wie in der folgenden Abbildung dargestellt:</span><span class="sxs-lookup"><span data-stu-id="709f4-162">From the **Solution Configurations** dropdown menu, select **Deploy** as shown in the following image:</span></span>

    ![Menü "Lösungskonfigurationen"](../assets/images/solution-configurations.png)

1. <span data-ttu-id="709f4-164">Wählen Sie die Schaltfläche **IIS Express + Teams** aus.</span><span class="sxs-lookup"><span data-stu-id="709f4-164">Select the **IIS Express + Teams** button.</span></span>

    <span data-ttu-id="709f4-165">Das Dialogfeld für die App-Installation wird im Teams-Client angezeigt.</span><span class="sxs-lookup"><span data-stu-id="709f4-165">The app installation dialog box appears in the Teams client.</span></span>

## <a name="validate-your-app"></a><span data-ttu-id="709f4-166">Validieren Ihrer App</span><span class="sxs-lookup"><span data-stu-id="709f4-166">Validate your app</span></span>

<span data-ttu-id="709f4-167">Auf der Seite **"Überprüfen"** können Sie Ihr App-Paket überprüfen, bevor Sie Ihre App an AppSource übermitteln.</span><span class="sxs-lookup"><span data-stu-id="709f4-167">The **Validate** page allows you to check your app package before submitting your app to AppSource.</span></span> <span data-ttu-id="709f4-168">Laden Sie einfach das Manifestpaket hoch, und das Überprüfungstool überprüft Ihre App anhand aller Testfälle im Zusammenhang mit dem Manifest.</span><span class="sxs-lookup"><span data-stu-id="709f4-168">Simply upload the manifest package and the validation tool will check your app against all manifest related test cases.</span></span> <span data-ttu-id="709f4-169">Für jeden fehlgeschlagenen Test enthält die Beschreibung einen Link zur Dokumentation, über den Sie den Fehler beheben können.</span><span class="sxs-lookup"><span data-stu-id="709f4-169">For each failed tests, the description provides a documentation link to help you fix the error.</span></span> <span data-ttu-id="709f4-170">Für die Tests, die schwer zu automatisieren sind, enthält die **vorläufige Prüfliste** 7 der häufigsten fehlgeschlagenen Testfälle sowie einen Link zu einer vollständigen Übermittlungscheckliste.</span><span class="sxs-lookup"><span data-stu-id="709f4-170">For the tests that are hard to automate, the **Preliminary checklist** details 7 of the most common failed test cases as well as link to a complete submission checklist.</span></span>

## <a name="publish-your-app-to-teams"></a><span data-ttu-id="709f4-171">Veröffentlichen Ihrer App in Teams</span><span class="sxs-lookup"><span data-stu-id="709f4-171">Publish your app to Teams</span></span>

* <span data-ttu-id="709f4-172">Auf Ihrer Projekthomepage können Sie Ihre App in ein Team hochladen, Ihre App für Benutzer in Ihrer Organisation an den benutzerdefinierten App Store Ihres Unternehmens senden oder Ihre App für alle Teambenutzer an App Source senden.</span><span class="sxs-lookup"><span data-stu-id="709f4-172">On your project home page, you can upload your app to a team, submit your app to your company custom app store for users in your organization, or submit your app to App Source for all Teams users.</span></span>

* <span data-ttu-id="709f4-173">Ihr IT-Administrator wird diese Übermittlungen überprüfen.</span><span class="sxs-lookup"><span data-stu-id="709f4-173">Your IT admin will review these submissions.</span></span>

* <span data-ttu-id="709f4-174">Sie können zur **Veröffentlichungsseite** zurückkehren, um ihren Übermittlungsstatus zu überprüfen und zu erfahren, ob Ihre App von Ihrem IT-Administrator genehmigt oder abgelehnt wurde. Hier können Sie auch Updates für Ihre App übermitteln oder alle derzeit aktiven Übermittlungen abbrechen.</span><span class="sxs-lookup"><span data-stu-id="709f4-174">You can return to the **Publish** page to check on your submission status and learn if your app was approved or rejected by your IT admin. This is also where you can submit updates to your app or cancel any currently active submissions.</span></span>

## <a name="next-step"></a><span data-ttu-id="709f4-175">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="709f4-175">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="709f4-176">Verwalten und Unterstützen Ihrer veröffentlichten App</span><span class="sxs-lookup"><span data-stu-id="709f4-176">Maintaining and supporting your published app</span></span>](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
>
