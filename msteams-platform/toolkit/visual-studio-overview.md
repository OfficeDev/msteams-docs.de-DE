---
title: Erstellen von apps mit dem Microsoft Teams-Toolkit und Visual Studio
description: Erste Schritte beim Erstellen großartiger benutzerdefinierter apps direkt in Visual Studio mit dem Microsoft Teams-Toolkit
keywords: Teams Visual Studio Toolkit
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: a1221945659b2dd0f45bdd3a966d9b029ddcde09
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "49604487"
---
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio"></a><span data-ttu-id="72ef0-104">Erstellen von apps mit dem Teams-Toolkit und Visual Studio</span><span class="sxs-lookup"><span data-stu-id="72ef0-104">Build apps with the Teams Toolkit and Visual Studio</span></span>

<span data-ttu-id="72ef0-105">Mithilfe des Microsoft Teams-Toolkits können Sie benutzerdefinierte Teams-Apps direkt innerhalb der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) von Visual Studio erstellen.</span><span class="sxs-lookup"><span data-stu-id="72ef0-105">The Microsoft Teams Toolkit enables you to create custom Teams apps directly within the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="72ef0-106">Das Microsoft Teams-Toolkit führt Sie durch den Vorgang und bietet alles, was Sie zum Erstellen, Debuggen und Starten Ihrer Teams-App benötigen.</span><span class="sxs-lookup"><span data-stu-id="72ef0-106">The Microsoft Teams toolkit guides you through the process and provides everything you need to build, debug, and launch your Teams app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="72ef0-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="72ef0-107">Prerequisites</span></span>

1. [<span data-ttu-id="72ef0-108">Entwicklervorschau aktivieren</span><span class="sxs-lookup"><span data-stu-id="72ef0-108">Enable developer preview</span></span>](../resources/dev-preview/developer-preview-intro.md#enable-developer-preview)

1. <span data-ttu-id="72ef0-109">Stellen Sie sicher, dass das **<span>ASP.ne</span>T-und das Webentwicklungs Modul** zu Ihrer Visual Studio-Instanz hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="72ef0-109">Make sure that the **<span>ASP.NE</span>T and web development module** has been added to your Visual Studio instance.</span></span> <span data-ttu-id="72ef0-110">Sie können überprüfen, indem Sie die Schritte im [Visual Studio ändern durch Hinzufügen oder Entfernen von Arbeitslasten und Komponenten](/visualstudio/install/modify-visual-studio?view=vs-2019&preserve-view=true) Dokumentation durchführen.</span><span class="sxs-lookup"><span data-stu-id="72ef0-110">You can check by following the steps in the [Modify Visual Studio by adding or removing workloads and component](/visualstudio/install/modify-visual-studio?view=vs-2019&preserve-view=true) documentation.</span></span>

![Visual Studio-ASP.NET-Modul](../assets/images/visual-studio-web-dev-module.png)

3. <span data-ttu-id="72ef0-112">Wenn Sie Ihre APP testen möchten, indem Sie Sie aus Visual Studio bereitstellen, müssen Sie IIS (Internet Information Services) in Ihrer Entwicklungsumgebung installiert haben.</span><span class="sxs-lookup"><span data-stu-id="72ef0-112">If you would like test your app by deploy it from Visual Studio, you'll need to have IIS (Internet Information Services) installed in your development environment.</span></span> <span data-ttu-id="72ef0-113">Visual Studio enthält IIS nicht und ist nicht in der standardmäßigen Windows 10-, Windows 8-oder Windows 7-Konfiguration enthalten; Sie können die neueste Version jedoch aus dem [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=48264)herunterladen.</span><span class="sxs-lookup"><span data-stu-id="72ef0-113">Visual Studio does not include IIS and it isn't included in the default Windows 10, Windows 8, or Windows 7 configuration; however, you can download the latest version from the [Microsoft download center](https://www.microsoft.com/download/details.aspx?id=48264).</span></span>

![IIS-Downloadseiten Ansicht](../assets/images/iis.png)

## <a name="install-the-teams-toolkit"></a><span data-ttu-id="72ef0-115">Installieren des Teams-Toolkits</span><span class="sxs-lookup"><span data-stu-id="72ef0-115">Install the Teams Toolkit</span></span>

<span data-ttu-id="72ef0-116">Das Microsoft Teams-Toolkit für Visual Studio steht im [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.vsteamstemplate) oder direkt im Menü " **Erweiterungen** " in Visual Studio zum Download bereit.</span><span class="sxs-lookup"><span data-stu-id="72ef0-116">The Microsoft Teams Toolkit for Visual Studio is available for download from the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.vsteamstemplate) or directly from the **Extensions** menu within Visual Studio.</span></span>

## <a name="using-the-toolkit"></a><span data-ttu-id="72ef0-117">Verwenden des Toolkits</span><span class="sxs-lookup"><span data-stu-id="72ef0-117">Using the toolkit</span></span>

- [<span data-ttu-id="72ef0-118">Einrichten eines neuen Projekts</span><span class="sxs-lookup"><span data-stu-id="72ef0-118">Set up a new project</span></span>](#set-up-a-new-teams-project)
- [<span data-ttu-id="72ef0-119">Konfigurieren Sie die App</span><span class="sxs-lookup"><span data-stu-id="72ef0-119">Configure your app</span></span>](#configure-your-app)
- [<span data-ttu-id="72ef0-120">Verpacken Ihrer APP</span><span class="sxs-lookup"><span data-stu-id="72ef0-120">Package your app</span></span>](#package-your-app)
- [<span data-ttu-id="72ef0-121">Ausführen ihrer app in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="72ef0-121">Run your app in Teams</span></span>](#install-and-run-your-app-locally)
- [<span data-ttu-id="72ef0-122">Überprüfen Ihrer APP</span><span class="sxs-lookup"><span data-stu-id="72ef0-122">Validate your app</span></span>](#validate-your-app)
- [<span data-ttu-id="72ef0-123">Veröffentlichen Ihrer APP</span><span class="sxs-lookup"><span data-stu-id="72ef0-123">Publish your app</span></span>](#publish-your-app-to-teams)

## <a name="set-up-a-new-teams-project"></a><span data-ttu-id="72ef0-124">Einrichten eines neuen Teams-Projekts</span><span class="sxs-lookup"><span data-stu-id="72ef0-124">Set up a new Teams project</span></span>

1. <span data-ttu-id="72ef0-125">Wählen Sie **Neues Projekt erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="72ef0-125">Select **Create a new project**.</span></span>
1. <span data-ttu-id="72ef0-126">Klicken Sie auf **Microsoft Teams-App** , und wählen Sie **weiter** aus.</span><span class="sxs-lookup"><span data-stu-id="72ef0-126">Choose **Microsoft Teams App** and select **Next**.</span></span>
1. <span data-ttu-id="72ef0-127">Sie gelangen auf den Bildschirm **configure your New Project** , in dem Sie den **Projektnamen**, den **Speicherort** und den **Lösungsnamen** auswählen können.</span><span class="sxs-lookup"><span data-stu-id="72ef0-127">You will arrive at the **Configure your new project** screen where you can choose the **Project name**, **Location**, and **Solution name**.</span></span>
1. <span data-ttu-id="72ef0-128">Aktivieren Sie das Kontrollkästchen **Projektmappe und Projekt in demselben Verzeichnis platzieren**.</span><span class="sxs-lookup"><span data-stu-id="72ef0-128">Check the box labeled **Place solution and project in the same directory**.</span></span>
1. <span data-ttu-id="72ef0-129">Mit einem Popupfenster mit der Bezeichnung **Add-Funktionen** können Sie eine oder mehrere Funktionen für Ihr Projekt-Setup auswählen.</span><span class="sxs-lookup"><span data-stu-id="72ef0-129">A pop-up window labeled **Add Capabilities** will allow you to choose one or more capabilities for your project setup.</span></span>
1. <span data-ttu-id="72ef0-130">Klicken Sie auf die Schaltfläche **weiter** , um den Konfigurationsprozess abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="72ef0-130">Select the **Next** button to complete the configuration process.</span></span>
1. <span data-ttu-id="72ef0-131">Mit einem Popupfenster mit der Bezeichnung **Add-Funktionen** können Sie die Eigenschaften für jede ausgewählte Funktion auswählen.</span><span class="sxs-lookup"><span data-stu-id="72ef0-131">A pop-up window labeled **Add Capabilities** will allow you to choose the properties for each selected capability.</span></span>
1. <span data-ttu-id="72ef0-132">Wählen Sie **Fertig stellen** aus, und Sie werden auf der Startseite von **Microsoft Teams Toolkit** landen.</span><span class="sxs-lookup"><span data-stu-id="72ef0-132">Select **Finish** and you will  land on the **Microsoft Teams Toolkit** landing page.</span></span>

## <a name="configure-your-app"></a><span data-ttu-id="72ef0-133">Konfigurieren Sie die App</span><span class="sxs-lookup"><span data-stu-id="72ef0-133">Configure your app</span></span>

<span data-ttu-id="72ef0-134">Im Kern umfasst die Teams-app drei Komponenten:</span><span class="sxs-lookup"><span data-stu-id="72ef0-134">At its core, the Teams app embraces three components:</span></span>

  1. <span data-ttu-id="72ef0-135">Der Microsoft Teams-Client ("Internet", "Desktop" oder "Mobil"), auf dem Benutzer mit Ihrer APP interagieren.</span><span class="sxs-lookup"><span data-stu-id="72ef0-135">The Microsoft Teams client (web, desktop or mobile) where users interact with your app.</span></span>
  1. <span data-ttu-id="72ef0-136">Ein Server, der auf Anforderungen für Inhalte reagiert, die in Microsoft Teams angezeigt werden, beispielsweise HTML-Registerkarteninhalte oder eine bot-Adaptive Karte.</span><span class="sxs-lookup"><span data-stu-id="72ef0-136">A server that responds to requests for content that will be displayed in Teams, e.g., HTML tab content or a bot adaptive card .</span></span>
  1. <span data-ttu-id="72ef0-137">Ein Teams- [App-Paket](/concepts/build-and-test/apps-package.md) , bestehend aus drei Dateien:</span><span class="sxs-lookup"><span data-stu-id="72ef0-137">A Teams [app package](/concepts/build-and-test/apps-package.md) consisting of three files:</span></span>

  > [!div class="checklist"]
  >
  > - <span data-ttu-id="72ef0-138">Die manifest.jsauf</span><span class="sxs-lookup"><span data-stu-id="72ef0-138">The manifest.json</span></span>
  > - <span data-ttu-id="72ef0-139">Ein [Farbsymbol](../resources/schema/manifest-schema.md#icons) für Ihre APP, das im öffentlichen oder im Organisations-App-Katalog angezeigt wird</span><span class="sxs-lookup"><span data-stu-id="72ef0-139">A [color icon](../resources/schema/manifest-schema.md#icons) for your app to display in the public or organization app catalog</span></span>
 > - <span data-ttu-id="72ef0-140">Ein [Gliederungssymbol](../resources/schema/manifest-schema.md#icons) für die Anzeige in der Microsoft Teams-Aktivitäts Leiste.</span><span class="sxs-lookup"><span data-stu-id="72ef0-140">An [outline icon](../resources/schema/manifest-schema.md#icons) for display on the Teams activity bar.</span></span>

<span data-ttu-id="72ef0-141">Wenn eine APP installiert ist, analysiert der Microsoft Teams-Client die Manifestdatei, um benötigte Informationen wie den Namen Ihrer APP und die URL zu ermitteln, in der sich die Dienste befinden.</span><span class="sxs-lookup"><span data-stu-id="72ef0-141">When an app is installed, the Teams client parses the manifest file to determine needed information like the name of your app and the URL where the services are located.</span></span>

> [!NOTE]
><span data-ttu-id="72ef0-142">Wenn Sie dies noch nicht getan haben, müssen Sie sich bei Ihrem Microsoft 365 oder-Konto anmelden, damit der Entwicklungsprozess fortgesetzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="72ef0-142">If you haven't done so already, you will need to sign in to your Microsoft 365  or account to continue with the development process.</span></span>
>
> <span data-ttu-id="72ef0-143">Wenn Sie kein Microsoft 365-Konto haben, können Sie sich für ein [Microsoft 365-Entwicklerprogramm](https://developer.microsoft.com/microsoft-365/dev-program) Abonnement anmelden.</span><span class="sxs-lookup"><span data-stu-id="72ef0-143">If you don't have a Microsoft 365 account, you can sign up for a [Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program) subscription.</span></span> <span data-ttu-id="72ef0-144">Es ist für 90 Tage *kostenlos* und wird ständig erneuert, solange Sie es für Entwicklungsaktivitäten verwenden.</span><span class="sxs-lookup"><span data-stu-id="72ef0-144">It's *free* for 90 days and will continually renew as long as you're using it for development activity.</span></span> <span data-ttu-id="72ef0-145">Wenn Sie über ein Visual Studio *Enterprise* -oder *Professional* -Abonnement verfügen, enthalten beide Programme ein kostenloses Microsoft 365- [Entwickler Abonnement](https://aka.ms/MyVisualStudioBenefits), das für die Dauer Ihres Visual Studio Abonnements aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="72ef0-145">If you have a Visual Studio *Enterprise* or *Professional* subscription, both programs include a free Microsoft 365 [developer subscription](https://aka.ms/MyVisualStudioBenefits), active for the life of your Visual Studio subscription.</span></span> <span data-ttu-id="72ef0-146">*Weitere Informationen finden Sie unter* [Einrichten eines Microsoft 365 Developer-Abonnements](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started).</span><span class="sxs-lookup"><span data-stu-id="72ef0-146">*See* [Set up a Microsoft 365 developer subscription](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started).</span></span>
>

### <a name="configuration-steps"></a><span data-ttu-id="72ef0-147">Konfigurationsschritte </span><span class="sxs-lookup"><span data-stu-id="72ef0-147">Configuration steps</span></span>

1. <span data-ttu-id="72ef0-148">Um Ihre APP zu konfigurieren, wählen Sie auf der Startseite des **Microsoft Teams Toolkit** die Option **App-Paket bearbeiten** aus.</span><span class="sxs-lookup"><span data-stu-id="72ef0-148">To configure your app, on the **Microsoft Teams Toolkit** landing page, select **Edit app package** .</span></span>
1. <span data-ttu-id="72ef0-149">Wählen Sie im Dropdownmenü **meine Umgebungen** die Option **Entwicklung** aus.</span><span class="sxs-lookup"><span data-stu-id="72ef0-149">From the **My Environments** drop-down menu, select **development**.</span></span>
1. <span data-ttu-id="72ef0-150">Sie landen auf der Seite mit den **App-Details** , auf der Sie die Eigenschaften Felder Ihrer APP bearbeiten können.</span><span class="sxs-lookup"><span data-stu-id="72ef0-150">You will land on the **App details** page where you can edit your app's property fields.</span></span>
1. <span data-ttu-id="72ef0-151">Durch das Bearbeiten der Felder auf der Seite mit den App-Details wird der Inhalt der manifest.jsauf Datei aktualisiert, die letztendlich als Teil des App-Pakets ausgeliefert wird.</span><span class="sxs-lookup"><span data-stu-id="72ef0-151">Editing the fields in the App details page updates the contents of the manifest.json file that will ultimately ship as part of the app package.</span></span> [<span data-ttu-id="72ef0-152">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="72ef0-152">Learn more</span></span>](https://aka.ms/teams-toolkit-manifest)

## <a name="package-your-app"></a><span data-ttu-id="72ef0-153">Verpacken Ihrer APP</span><span class="sxs-lookup"><span data-stu-id="72ef0-153">Package your app</span></span>

<span data-ttu-id="72ef0-154">Wenn Sie die Seite " **App-Details** " ändern oder das **Manifest** oder **. env** -Dateien im Ordner "  **. Publish** " Ihrer APP aktualisieren, wird die **Development.zip** Datei automatisch generiert.</span><span class="sxs-lookup"><span data-stu-id="72ef0-154">Modifying the **app details** page or updating the **manifest**, or **.env** files in your app's  **.publish** folder will automatically generate your **Development.zip** file.</span></span> <span data-ttu-id="72ef0-155">Die Development.zip Datei enthält drei erforderliche Dateien – die **manifest.js** und [zwei Symbole](../concepts/build-and-test/apps-package.md#app-icons).</span><span class="sxs-lookup"><span data-stu-id="72ef0-155">The Development.zip file includes three required files — the **manifest.json** and [two icons](../concepts/build-and-test/apps-package.md#app-icons).</span></span>

## <a name="install-and-run-your-app-locally"></a><span data-ttu-id="72ef0-156">Lokal installieren und Ausführen der APP</span><span class="sxs-lookup"><span data-stu-id="72ef0-156">Install and run your app locally</span></span>

1. <span data-ttu-id="72ef0-157">Wählen Sie im Dropdownmenü **Lösungs Konfigurationen** die Option **Bereitstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="72ef0-157">From the **Solution Configurations** dropdown menu, select **Deploy**.</span></span>

![Menü "Lösungs Konfigurationen"](../assets/images/solution-configurations.png)

2. <span data-ttu-id="72ef0-159">Wählen Sie die Schaltfläche **ISS Express + Teams** aus.</span><span class="sxs-lookup"><span data-stu-id="72ef0-159">Select the **ISS Express + Teams** button.</span></span>

1. <span data-ttu-id="72ef0-160">Microsoft Teams wird gestartet, und der APP-Installationsdialog sollte im Microsoft Teams-Client angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="72ef0-160">Teams will launch and the app installation dialogue should appear in the Teams client.</span></span>

## <a name="validate-your-app"></a><span data-ttu-id="72ef0-161">Überprüfen Ihrer APP</span><span class="sxs-lookup"><span data-stu-id="72ef0-161">Validate your app</span></span>

<span data-ttu-id="72ef0-162">Auf der Seite über **prüfen** können Sie Ihr App-Paket überprüfen, bevor Sie Ihre APP an AppSource senden.</span><span class="sxs-lookup"><span data-stu-id="72ef0-162">The **Validate** page allows you to check your app package before submitting your app to AppSource.</span></span> <span data-ttu-id="72ef0-163">Laden Sie einfach das Manifest-Paket hoch, und das Überprüfungstool überprüft Ihre APP mit allen Manifest-bezogenen Testfällen.</span><span class="sxs-lookup"><span data-stu-id="72ef0-163">Simply upload the manifest package and the validation tool will check your app against all manifest related test cases.</span></span> <span data-ttu-id="72ef0-164">Bei jedem fehlgeschlagenen Test enthält die Beschreibung einen Link zur Dokumentation, mit dem Sie den Fehler beheben können.</span><span class="sxs-lookup"><span data-stu-id="72ef0-164">For each failed tests, the description provides a documentation link to help you fix the error.</span></span> <span data-ttu-id="72ef0-165">Bei den Tests, die schwer zu automatisieren sind, werden in der **vorläufigen Prüfliste** 7 der häufigsten fehlgeschlagenen Testfälle sowie Links zu einer vollständigen Übermittlungs Prüfliste aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="72ef0-165">For the tests that are hard to automate, the **Preliminary checklist** details 7 of the most common failed test cases as well as link to a complete submission checklist.</span></span>

## <a name="publish-your-app-to-teams"></a><span data-ttu-id="72ef0-166">Veröffentlichen Ihrer APP in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="72ef0-166">Publish your app to Teams</span></span>

<span data-ttu-id="72ef0-167">✔ Auf Ihrer Project-Startseite können Sie Ihre APP in ein Team hochladen, Ihre APP für Benutzer in Ihrer Organisation an den benutzerdefinierten APP-Speicher des Unternehmens übermitteln oder Ihre APP an die APP-Quelle für alle Microsoft Teams-Benutzer senden.</span><span class="sxs-lookup"><span data-stu-id="72ef0-167">✔ On your project home page, you can upload your app to a team, submit your app to your company custom app store for users in your organization, or submit your app to App Source for all Teams users.</span></span>

<span data-ttu-id="72ef0-168">✔ Ihr IT-Administrator diese Übermittlungen prüft.</span><span class="sxs-lookup"><span data-stu-id="72ef0-168">✔ Your IT admin will review these submissions.</span></span>

<span data-ttu-id="72ef0-169">✔ Können Sie zur Seite **veröffentlichen** zurückkehren, um den Übermittlungsstatus zu überprüfen und zu erfahren, ob Ihre APP von Ihrem IT-Administrator genehmigt oder abgelehnt wurde. In diesem Fall können Sie auch Aktualisierungen an Ihre APP übermitteln oder derzeit aktive Übermittlungen kündigen.</span><span class="sxs-lookup"><span data-stu-id="72ef0-169">✔  You can return to the **Publish** page to check on your submission status and learn if your app was approved or rejected by your IT admin. This is also where you'll come to submit updates to your app or cancel any currently active submissions.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="72ef0-170">Nächster Schritt: Verwalten und unterstützen Ihrer veröffentlichten App</span><span class="sxs-lookup"><span data-stu-id="72ef0-170">Next step: Maintaining and supporting your published app</span></span>](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
>
