---
title: Erstellen Sie Apps mit dem Microsoft Teams Toolkit und Visual Studio
description: Beginnen Sie mit dem Erstellen großartiger benutzerdefinierter Apps direkt innerhalb Visual Studio mit dem Microsoft Teams Toolkit
keywords: Teams visuelles Studio-Toolkit
localization_priority: Normal
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: eb94a8de0355283344ebe890a6fa3a3050e243ea
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566551"
---
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio"></a><span data-ttu-id="9a0b3-104">Erstellen von Apps mit dem Teams Toolkit und Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9a0b3-104">Build apps with the Teams Toolkit and Visual Studio</span></span>

<span data-ttu-id="9a0b3-105">Mithilfe des Microsoft Teams-Toolkits können Sie benutzerdefinierte Teams-Apps direkt innerhalb der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) von Visual Studio erstellen.</span><span class="sxs-lookup"><span data-stu-id="9a0b3-105">The Microsoft Teams Toolkit enables you to create custom Teams apps directly within the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="9a0b3-106">Das Microsoft Teams-Toolkit führt Sie durch den Vorgang und bietet alles, was Sie zum Erstellen, Debuggen und Starten Ihrer Teams-App benötigen.</span><span class="sxs-lookup"><span data-stu-id="9a0b3-106">The Microsoft Teams toolkit guides you through the process and provides everything you need to build, debug, and launch your Teams app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9a0b3-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="9a0b3-107">Prerequisites</span></span>

1. <span data-ttu-id="9a0b3-108">[Aktivieren Sie die Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md#enable-developer-preview).</span><span class="sxs-lookup"><span data-stu-id="9a0b3-108">[Enable developer preview](../resources/dev-preview/developer-preview-intro.md#enable-developer-preview).</span></span>

1. <span data-ttu-id="9a0b3-109">Stellen Sie sicher, dass das **<span>ASP.NE</span>T- und Webentwicklungsmodul** zu Ihrer Visual Studio-Instanz hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="9a0b3-109">Make sure that the **<span>ASP.NE</span>T and web development module** has been added to your Visual Studio instance.</span></span> <span data-ttu-id="9a0b3-110">Sie können die folgenden Schritte im Visual Studio ändern ausführen, [indem Sie Workloads und Komponentendokumentation hinzufügen oder entfernen.](/visualstudio/install/modify-visual-studio?view=vs-2019&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="9a0b3-110">You can check by following the steps in the [Modify Visual Studio by adding or removing workloads and component](/visualstudio/install/modify-visual-studio?view=vs-2019&preserve-view=true) documentation.</span></span>

![Visual Studio asp.net Modul](../assets/images/visual-studio-web-dev-module.png)

3. <span data-ttu-id="9a0b3-112">Wenn Sie Ihre App testen möchten, indem Sie sie von Visual Studio bereitstellen, müssen Sie IIS (Internetinformationsdienste) in Ihrer Entwicklungsumgebung installiert haben.</span><span class="sxs-lookup"><span data-stu-id="9a0b3-112">If you would like test your app by deploying it from Visual Studio, you'll need to have IIS (Internet Information Services) installed in your development environment.</span></span> <span data-ttu-id="9a0b3-113">Visual Studio enthält iIS nicht und ist nicht in der Standardkonfiguration Windows 10, Windows 8 oder Windows 7 enthalten. Sie können jedoch die neueste Version aus dem [Microsoft-Downloadcenter](https://www.microsoft.com/download/details.aspx?id=48264)herunterladen.</span><span class="sxs-lookup"><span data-stu-id="9a0b3-113">Visual Studio does not include IIS and it isn't included in the default Windows 10, Windows 8, or Windows 7 configuration; however, you can download the latest version from the [Microsoft download center](https://www.microsoft.com/download/details.aspx?id=48264).</span></span>

![IIS-Downloadseite ansicht](../assets/images/iis.png)

## <a name="install-the-teams-toolkit"></a><span data-ttu-id="9a0b3-115">Installieren des Teams Toolkits</span><span class="sxs-lookup"><span data-stu-id="9a0b3-115">Install the Teams Toolkit</span></span>

<span data-ttu-id="9a0b3-116">Das Microsoft Teams Toolkit for Visual Studio steht im [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.vsteamstemplate) oder direkt im Menü **Erweiterungen** innerhalb Visual Studio zum Download bereit.</span><span class="sxs-lookup"><span data-stu-id="9a0b3-116">The Microsoft Teams Toolkit for Visual Studio is available for download from the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.vsteamstemplate) or directly from the **Extensions** menu within Visual Studio.</span></span>

## <a name="using-the-toolkit"></a><span data-ttu-id="9a0b3-117">Verwenden des Toolkits</span><span class="sxs-lookup"><span data-stu-id="9a0b3-117">Using the toolkit</span></span>

- [<span data-ttu-id="9a0b3-118">Einrichten eines neuen Projekts</span><span class="sxs-lookup"><span data-stu-id="9a0b3-118">Set up a new project</span></span>](#set-up-a-new-teams-project)
- [<span data-ttu-id="9a0b3-119">Konfigurieren Sie die App</span><span class="sxs-lookup"><span data-stu-id="9a0b3-119">Configure your app</span></span>](#configure-your-app)
- [<span data-ttu-id="9a0b3-120">Verpacken Sie Ihre App</span><span class="sxs-lookup"><span data-stu-id="9a0b3-120">Package your app</span></span>](#package-your-app)
- [<span data-ttu-id="9a0b3-121">Führen Sie Ihre App in Teams</span><span class="sxs-lookup"><span data-stu-id="9a0b3-121">Run your app in Teams</span></span>](#install-and-run-your-app-locally)
- [<span data-ttu-id="9a0b3-122">Validieren Ihrer App</span><span class="sxs-lookup"><span data-stu-id="9a0b3-122">Validate your app</span></span>](#validate-your-app)
- [<span data-ttu-id="9a0b3-123">Veröffentlichen eigener Apps</span><span class="sxs-lookup"><span data-stu-id="9a0b3-123">Publish your app</span></span>](#publish-your-app-to-teams)

## <a name="set-up-a-new-teams-project"></a><span data-ttu-id="9a0b3-124">Einrichten eines neuen Teams Projekts</span><span class="sxs-lookup"><span data-stu-id="9a0b3-124">Set up a new Teams project</span></span>

1. <span data-ttu-id="9a0b3-125">Wählen **Sie Erstellen eines neuen Projekts** aus.</span><span class="sxs-lookup"><span data-stu-id="9a0b3-125">Select **Create a new project**.</span></span>
1. <span data-ttu-id="9a0b3-126">Wählen Sie **Microsoft Teams App** und wählen Sie **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="9a0b3-126">Choose **Microsoft Teams App** and select **Next**.</span></span>
1. <span data-ttu-id="9a0b3-127">Sie gelangen zum **neuen Projektbildschirm Konfigurieren,** auf dem Sie den **Project Namen**, **Standort** und **Projektmappennamen** auswählen können.</span><span class="sxs-lookup"><span data-stu-id="9a0b3-127">You will arrive at the **Configure your new project** screen where you can choose the **Project name**, **Location**, and **Solution name**.</span></span>
1. <span data-ttu-id="9a0b3-128">Aktivieren Sie das Kontrollkästchen **Lösung und Projekt platzieren im selben Verzeichnis**.</span><span class="sxs-lookup"><span data-stu-id="9a0b3-128">Check the box labeled **Place solution and project in the same directory**.</span></span>
1. <span data-ttu-id="9a0b3-129">In einem Popupfenster mit der Bezeichnung **"Funktionen hinzufügen"** können Sie eine oder mehrere Funktionen für ihre Projekteinrichtung auswählen.</span><span class="sxs-lookup"><span data-stu-id="9a0b3-129">A pop-up window labeled **Add Capabilities** will allow you to choose one or more capabilities for your project setup.</span></span>
1. <span data-ttu-id="9a0b3-130">Wählen Sie die Schaltfläche **Weiter** aus, um den Konfigurationsvorgang abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="9a0b3-130">Select the **Next** button to complete the configuration process.</span></span>
1. <span data-ttu-id="9a0b3-131">In einem Popupfenster mit der Bezeichnung **"Funktionen hinzufügen"** können Sie die Eigenschaften für jede ausgewählte Funktion auswählen.</span><span class="sxs-lookup"><span data-stu-id="9a0b3-131">A pop-up window labeled **Add Capabilities** will allow you to choose the properties for each selected capability.</span></span>
1. <span data-ttu-id="9a0b3-132">Wählen Sie **Fertig stellen** und Sie werden auf der **Microsoft Teams Toolkit-Zielseite** landen.</span><span class="sxs-lookup"><span data-stu-id="9a0b3-132">Select **Finish** and you will  land on the **Microsoft Teams Toolkit** landing page.</span></span>

## <a name="configure-your-app"></a><span data-ttu-id="9a0b3-133">Konfigurieren Sie die App</span><span class="sxs-lookup"><span data-stu-id="9a0b3-133">Configure your app</span></span>

<span data-ttu-id="9a0b3-134">Im Kern umfasst die Teams-App drei Komponenten:</span><span class="sxs-lookup"><span data-stu-id="9a0b3-134">At its core, the Teams app embraces three components:</span></span>

  1. <span data-ttu-id="9a0b3-135">Der Microsoft Teams Client (Web, Desktop oder Mobile), auf dem Benutzer mit Ihrer App interagieren.</span><span class="sxs-lookup"><span data-stu-id="9a0b3-135">The Microsoft Teams client (web, desktop or mobile) where users interact with your app.</span></span>
  1. <span data-ttu-id="9a0b3-136">Ein Server, der auf Anfragen nach Inhalten reagiert, die in Teams angezeigt werden, z. B. HTML-Registerkarteninhalt oder eine adaptive Bot-Karte .</span><span class="sxs-lookup"><span data-stu-id="9a0b3-136">A server that responds to requests for content that will be displayed in Teams, e.g., HTML tab content or a bot adaptive card .</span></span>
  1. <span data-ttu-id="9a0b3-137">Ein Teams-App-Paket besteht aus drei Dateien:</span><span class="sxs-lookup"><span data-stu-id="9a0b3-137">A Teams app package consists of three files:</span></span>

      > [!div class="checklist"]
      >
      > - <span data-ttu-id="9a0b3-138">Die manifest.jsauf</span><span class="sxs-lookup"><span data-stu-id="9a0b3-138">The manifest.json</span></span>
      > - <span data-ttu-id="9a0b3-139">Ein [Farbsymbol](../resources/schema/manifest-schema.md#icons) für Ihre App, das im öffentlichen oder Organisations-App-Katalog angezeigt werden soll</span><span class="sxs-lookup"><span data-stu-id="9a0b3-139">A [color icon](../resources/schema/manifest-schema.md#icons) for your app to display in the public or organization app catalog</span></span>
      > - <span data-ttu-id="9a0b3-140">Ein [Gliederungssymbol](../resources/schema/manifest-schema.md#icons) für die Anzeige in der Teams Aktivitätsleiste.</span><span class="sxs-lookup"><span data-stu-id="9a0b3-140">An [outline icon](../resources/schema/manifest-schema.md#icons) for display on the Teams activity bar.</span></span>

<span data-ttu-id="9a0b3-141">Wenn eine App installiert ist, analysiert der Teams-Client die Manifestdatei, um die erforderlichen Informationen wie den Namen Ihrer App und die URL zu ermitteln, unter denen sich die Dienste befinden.</span><span class="sxs-lookup"><span data-stu-id="9a0b3-141">When an app is installed, the Teams client parses the manifest file to determine needed information like the name of your app and the URL where the services are located.</span></span>

> [!NOTE]
><span data-ttu-id="9a0b3-142">Wenn Sie dies noch nicht getan haben, müssen Sie sich bei Ihrem Microsoft 365 oder Konto anmelden, um mit dem Entwicklungsprozess fortzufahren.</span><span class="sxs-lookup"><span data-stu-id="9a0b3-142">If you haven't done so already, you will need to sign in to your Microsoft 365  or account to continue with the development process.</span></span>
>
> <span data-ttu-id="9a0b3-143">Wenn Sie kein Microsoft 365 Konto haben, können Sie sich für ein [Abonnement des Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program) anmelden.</span><span class="sxs-lookup"><span data-stu-id="9a0b3-143">If you don't have a Microsoft 365 account, you can sign up for a [Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program) subscription.</span></span> <span data-ttu-id="9a0b3-144">Es ist 90 Tage *lang kostenlos* und wird kontinuierlich verlängert, solange Sie es für Entwicklungsaktivitäten verwenden.</span><span class="sxs-lookup"><span data-stu-id="9a0b3-144">It's *free* for 90 days and will continually renew as long as you're using it for development activity.</span></span> <span data-ttu-id="9a0b3-145">Wenn Sie über ein Visual Studio *Enterprise* oder *Professional* Abonnement verfügen, verfügen beide Programme über ein kostenloses Microsoft 365 [Entwicklerabonnement,](https://aka.ms/MyVisualStudioBenefits)das für die Dauer Ihres Visual Studio Abonnements aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="9a0b3-145">If you have a Visual Studio *Enterprise* or *Professional* subscription, both programs include a free Microsoft 365 [developer subscription](https://aka.ms/MyVisualStudioBenefits), active for the life of your Visual Studio subscription.</span></span> <span data-ttu-id="9a0b3-146">Weitere Informationen finden Sie unter [Einrichten eines Microsoft 365 Entwicklerabonnements](/office/developer-program/office-365-developer-program-get-started).</span><span class="sxs-lookup"><span data-stu-id="9a0b3-146">For more information, See [Set up a Microsoft 365 developer subscription](/office/developer-program/office-365-developer-program-get-started).</span></span>
>

### <a name="configuration-steps"></a><span data-ttu-id="9a0b3-147">Konfigurationsschritte </span><span class="sxs-lookup"><span data-stu-id="9a0b3-147">Configuration steps</span></span>

1. <span data-ttu-id="9a0b3-148">Um Ihre App zu konfigurieren, wählen Sie auf der **Zielseite Microsoft Teams Toolkit** **App-Paket bearbeiten** aus.</span><span class="sxs-lookup"><span data-stu-id="9a0b3-148">To configure your app, on the **Microsoft Teams Toolkit** landing page, select **Edit app package**.</span></span>
1. <span data-ttu-id="9a0b3-149">Wählen Sie im Dropdown-Menü **Meine Umgebungen** die **Option Entwicklung** aus.</span><span class="sxs-lookup"><span data-stu-id="9a0b3-149">From the **My Environments** drop-down menu, select **development**.</span></span>
1. <span data-ttu-id="9a0b3-150">Sie landen auf der **App-Detailseite,** auf der Sie die Eigenschaftenfelder Ihrer App bearbeiten können.</span><span class="sxs-lookup"><span data-stu-id="9a0b3-150">You will land on the **App details** page where you can edit your app's property fields.</span></span>
1. <span data-ttu-id="9a0b3-151">Durch das Bearbeiten der Felder auf der Seite App-Details wird der Inhalt der manifest.jsin der Datei aktualisiert, die letztendlich als Teil des App-Pakets ausgeliefert wird.</span><span class="sxs-lookup"><span data-stu-id="9a0b3-151">Editing the fields in the App details page updates the contents of the manifest.json file that will ultimately ship as part of the app package.</span></span> [<span data-ttu-id="9a0b3-152">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="9a0b3-152">Learn more</span></span>](https://aka.ms/teams-toolkit-manifest)

## <a name="package-your-app"></a><span data-ttu-id="9a0b3-153">Verpacken Sie Ihre App</span><span class="sxs-lookup"><span data-stu-id="9a0b3-153">Package your app</span></span>

<span data-ttu-id="9a0b3-154">Wenn Sie die **App-Detailseite** ändern oder die **Manifest-** oder **.env-Dateien** im  **.publish-Ordner** Ihrer App aktualisieren, werden automatisch Ihre **Development.zip** Datei generiert.</span><span class="sxs-lookup"><span data-stu-id="9a0b3-154">Modifying the **app details** page or updating the **manifest**, or **.env** files in your app's  **.publish** folder will automatically generate your **Development.zip** file.</span></span> <span data-ttu-id="9a0b3-155">Die Development.zip-Datei enthält drei erforderliche Dateien – die **manifest.jsein** und [zwei Symbole](../concepts/build-and-test/apps-package.md#app-icons).</span><span class="sxs-lookup"><span data-stu-id="9a0b3-155">The Development.zip file includes three required files — the **manifest.json** and [two icons](../concepts/build-and-test/apps-package.md#app-icons).</span></span>

## <a name="install-and-run-your-app-locally"></a><span data-ttu-id="9a0b3-156">Installieren und Ausführen Ihrer App lokal</span><span class="sxs-lookup"><span data-stu-id="9a0b3-156">Install and run your app locally</span></span>

1. <span data-ttu-id="9a0b3-157">Wählen Sie im Dropdownmenü **Lösungskonfigurationen** die Option **Bereitstellen** wie im folgenden Bild gezeigt aus:</span><span class="sxs-lookup"><span data-stu-id="9a0b3-157">From the **Solution Configurations** dropdown menu, select **Deploy** as shown in the following image:</span></span>

    ![Menü für Lösungskonfigurationen](../assets/images/solution-configurations.png)

2. <span data-ttu-id="9a0b3-159">Wählen Sie die Schaltfläche **IIS Express + Teams** aus.</span><span class="sxs-lookup"><span data-stu-id="9a0b3-159">Select the **IIS Express + Teams** button.</span></span>

1. <span data-ttu-id="9a0b3-160">Teams wird gestartet, und der App-Installationsdialog sollte im Teams-Client angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="9a0b3-160">Teams will launch and the app installation dialogue should appear in the Teams client.</span></span>

## <a name="validate-your-app"></a><span data-ttu-id="9a0b3-161">Validieren Ihrer App</span><span class="sxs-lookup"><span data-stu-id="9a0b3-161">Validate your app</span></span>

<span data-ttu-id="9a0b3-162">Auf der Seite **"Validieren"** können Sie Ihr App-Paket überprüfen, bevor Sie Ihre App an AppSource senden.</span><span class="sxs-lookup"><span data-stu-id="9a0b3-162">The **Validate** page allows you to check your app package before submitting your app to AppSource.</span></span> <span data-ttu-id="9a0b3-163">Laden Sie einfach das Manifestpaket hoch und das Validierungstool überprüft Ihre App mit allen manifesten Testfällen.</span><span class="sxs-lookup"><span data-stu-id="9a0b3-163">Simply upload the manifest package and the validation tool will check your app against all manifest related test cases.</span></span> <span data-ttu-id="9a0b3-164">Für jeden fehlgeschlagenen Test enthält die Beschreibung einen Dokumentationslink, mit dem Sie den Fehler beheben können.</span><span class="sxs-lookup"><span data-stu-id="9a0b3-164">For each failed tests, the description provides a documentation link to help you fix the error.</span></span> <span data-ttu-id="9a0b3-165">Für die schwer zu automatisierenden Tests werden in der **vorläufigen Checkliste** 7 der häufigsten fehlgeschlagenen Testfälle sowie ein Link zu einer vollständigen Übermittlungs-Checkliste angezeigt.</span><span class="sxs-lookup"><span data-stu-id="9a0b3-165">For the tests that are hard to automate, the **Preliminary checklist** details 7 of the most common failed test cases as well as link to a complete submission checklist.</span></span>

## <a name="publish-your-app-to-teams"></a><span data-ttu-id="9a0b3-166">Veröffentlichen Ihrer App in Teams</span><span class="sxs-lookup"><span data-stu-id="9a0b3-166">Publish your app to Teams</span></span>

<span data-ttu-id="9a0b3-167">✔ Auf Ihrer Projekthomepage können Sie Ihre App in ein Team hochladen, Ihre App an den benutzerdefinierten App Store Ihres Unternehmens für Benutzer in Ihrer Organisation senden oder Ihre App an App Source für alle Teams Benutzer senden.</span><span class="sxs-lookup"><span data-stu-id="9a0b3-167">✔ On your project home page, you can upload your app to a team, submit your app to your company custom app store for users in your organization, or submit your app to App Source for all Teams users.</span></span>

<span data-ttu-id="9a0b3-168">✔ Ihr IT-Administrator überprüft diese Einsendungen.</span><span class="sxs-lookup"><span data-stu-id="9a0b3-168">✔ Your IT admin will review these submissions.</span></span>

<span data-ttu-id="9a0b3-169">✔ Sie können zur **Seite Veröffentlichen** zurückkehren, um Ihren Übermittlungsstatus zu überprüfen und zu erfahren, ob Ihre App von Ihrem IT-Administrator genehmigt oder abgelehnt wurde. Hier werden Sie auch kommen, um Updates an Ihre App zu senden oder alle derzeit aktiven Übermittlungen abzubrechen.</span><span class="sxs-lookup"><span data-stu-id="9a0b3-169">✔  You can return to the **Publish** page to check on your submission status and learn if your app was approved or rejected by your IT admin. This is also where you'll come to submit updates to your app or cancel any currently active submissions.</span></span>

## <a name="next-step"></a><span data-ttu-id="9a0b3-170">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="9a0b3-170">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9a0b3-171">Verwalten und Unterstützen Ihrer veröffentlichten App</span><span class="sxs-lookup"><span data-stu-id="9a0b3-171">Maintaining and supporting your published app</span></span>](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
>
