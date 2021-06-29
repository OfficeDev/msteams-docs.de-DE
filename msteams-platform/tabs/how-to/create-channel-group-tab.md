---
title: Erstellen einer Kanal- oder Gruppenregisterkarte
author: laujan
description: Eine Schnellstartanleitung zum Erstellen einer Kanal- und Gruppenregisterkarte mit dem Yeoman-Generator für Microsoft Teams.
localization_priority: Normal
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: fedaf3ec639917110e16c666734fa3eedbcda18e
ms.sourcegitcommit: 85a52119df6c4cb4536572e6d2e7407f0e5e8a23
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2021
ms.locfileid: "53179994"
---
# <a name="create-a-channel-or-group-tab"></a><span data-ttu-id="8bbc9-103">Erstellen einer Kanal- oder Gruppenregisterkarte</span><span class="sxs-lookup"><span data-stu-id="8bbc9-103">Create a channel or group tab</span></span>

## <a name="create-a-custom-channel-or-group-tab"></a><span data-ttu-id="8bbc9-104">Erstellen einer benutzerdefinierten Kanal- oder Gruppenregisterkarte</span><span class="sxs-lookup"><span data-stu-id="8bbc9-104">Create a custom channel or group tab</span></span>

<span data-ttu-id="8bbc9-105">Sie können eine Kanal- oder Gruppenregisterkarte mit Node.js und yeoman Generator, ASP.NETCore oder ASP.NETCore MVC erstellen.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-105">You can create a channel or group tab using Node.js and the Yeoman Generator, ASP.NETCore, or ASP.NETCore MVC.</span></span>

# <a name="nodejs"></a>[<span data-ttu-id="8bbc9-106">Node.js</span><span class="sxs-lookup"><span data-stu-id="8bbc9-106">Node.js</span></span>](#tab/nodejs)

### <a name="create-a-custom-channel-and-group-tab-using-nodejs-and-the-yeoman-generator"></a><span data-ttu-id="8bbc9-107">Erstellen eines benutzerdefinierten Kanals und einer gruppenregisterkarte mit Node.js und dem Yeoman-Generator</span><span class="sxs-lookup"><span data-stu-id="8bbc9-107">Create a custom channel and group tab using Node.js and the Yeoman Generator</span></span>

> [!NOTE]
> <span data-ttu-id="8bbc9-108">Dieser Artikel folgt den Schritten, die im [Build Ihres ersten Microsoft Teams App-Wiki](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) im Microsoft OfficeDev-GitHub-Repository beschrieben sind.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-108">This article follows the steps outlined in the [build Your first Microsoft Teams app](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) Wiki found in the Microsoft OfficeDev GitHub repository.</span></span>

<span data-ttu-id="8bbc9-109">Sie können eine benutzerdefinierte Kanal- oder Gruppenregisterkarte mithilfe des [Teams Yeoman-Generators](https://github.com/OfficeDev/generator-teams/)erstellen.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-109">You can create a custom channel or group tab using the [Teams Yeoman generator](https://github.com/OfficeDev/generator-teams/).</span></span>

### <a name="prerequisites-for-apps"></a><span data-ttu-id="8bbc9-110">Voraussetzungen für Apps</span><span class="sxs-lookup"><span data-stu-id="8bbc9-110">Prerequisites for apps</span></span>

<span data-ttu-id="8bbc9-111">Sie müssen die folgenden Voraussetzungen verstehen:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-111">You must have an understanding of the following prerequisites:</span></span>

- <span data-ttu-id="8bbc9-112">Sie müssen einen Office 365 Mandanten und ein Team mit aktivierter **Option "Hochladen benutzerdefinierter Apps zulassen"** konfiguriert haben.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-112">You must have an Office 365 tenant and a team configured with **Allow uploading custom apps** enabled.</span></span> <span data-ttu-id="8bbc9-113">Weitere Informationen finden Sie unter [Vorbereiten Ihres Office 365 Mandanten.](~/concepts/build-and-test/prepare-your-o365-tenant.md)</span><span class="sxs-lookup"><span data-stu-id="8bbc9-113">For more information, see [prepare your Office 365 tenant](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="8bbc9-114">Wenn Sie derzeit kein Office 365 Konto haben, können Sie sich über das Office 365-Entwicklerprogramm für ein kostenloses Abonnement registrieren.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-114">If you do not currently have an Office 365 account, you can sign up for a free subscription through the Office 365 Developer Program.</span></span> <span data-ttu-id="8bbc9-115">Das Abonnement bleibt aktiv, solange Sie es für die fortlaufende Entwicklung verwenden.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-115">The subscription remains active as long as you are using it for ongoing development.</span></span> <span data-ttu-id="8bbc9-116">Willkommen [beim Office 365-Entwicklerprogramm.](/office/developer-program/microsoft-365-developer-program)</span><span class="sxs-lookup"><span data-stu-id="8bbc9-116">See [welcome to the Office 365 Developer Program](/office/developer-program/microsoft-365-developer-program).</span></span>

<span data-ttu-id="8bbc9-117">Darüber hinaus muss für dieses Projekt Folgendes in Ihrer Entwicklungsumgebung installiert sein:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-117">In addition, this project requires that you have the following installed in your development environment:</span></span>

- <span data-ttu-id="8bbc9-118">Ein beliebiger Text-Editor oder eine beliebige IDE.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-118">Any text editor or IDE.</span></span> <span data-ttu-id="8bbc9-119">Sie können [Visual Studio Code](https://code.visualstudio.com/download) kostenlos installieren und verwenden.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-119">You can install and use [Visual Studio Code](https://code.visualstudio.com/download) for free.</span></span>

- <span data-ttu-id="8bbc9-120">[Node.js/npm](https://nodejs.org/en/).</span><span class="sxs-lookup"><span data-stu-id="8bbc9-120">[Node.js/npm](https://nodejs.org/en/).</span></span> <span data-ttu-id="8bbc9-121">Verwenden Sie die neueste LTS-Version.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-121">Use the latest LTS version.</span></span> <span data-ttu-id="8bbc9-122">Die Node Paket-Manager (npm) wird in Ihrem System mit der Installation von Node.js installiert.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-122">The Node Package Manager (npm) installs in your system with the installation of Node.js.</span></span>

- <span data-ttu-id="8bbc9-123">Nachdem Sie Node.js erfolgreich installiert haben, installieren Sie die [Yeoman-](https://yeoman.io/) und [gulp-cli-Pakete,](https://www.npmjs.com/package/gulp-cli) indem Sie in der Eingabeaufforderung Folgendes eingeben:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-123">After you have successfully installed Node.js, install the [Yeoman](https://yeoman.io/) and [gulp-cli](https://www.npmjs.com/package/gulp-cli) packages by entering the following in your command prompt:</span></span>

    ```bash
    npm install yo gulp-cli --global
    ```

- <span data-ttu-id="8bbc9-124">Installieren Sie den Microsoft Teams Apps-Generator, indem Sie in der Eingabeaufforderung Folgendes eingeben:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-124">Install the Microsoft Teams Apps generator by entering the following in your command prompt:</span></span>

    ```bash
    npm install generator-teams --global
    ```

### <a name="generate-your-project"></a><span data-ttu-id="8bbc9-125">Generieren Ihres Projekts</span><span class="sxs-lookup"><span data-stu-id="8bbc9-125">Generate your project</span></span>

<span data-ttu-id="8bbc9-126">**So generieren Sie Ihr Projekt**</span><span class="sxs-lookup"><span data-stu-id="8bbc9-126">**To generate your project**</span></span>

1. <span data-ttu-id="8bbc9-127">Erstellen Sie an einer Eingabeaufforderung ein neues Verzeichnis für Ihr Registerkartenprojekt.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-127">At a command prompt, create a new directory for your tab project.</span></span>

1. <span data-ttu-id="8bbc9-128">Um den Generator zu starten, wechseln Sie zu Ihrem neuen Verzeichnis, und geben Sie den folgenden Befehl ein:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-128">To start the generator, go to your new directory and type the following command:</span></span>

    ```bash
    yo teams
    ```

1. <span data-ttu-id="8bbc9-129">Geben Sie als Nächstes eine Reihe von Werten an, die in der **manifest.js** der Anwendung in der Datei verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-129">Next, provide a series of values that are used in your application's **manifest.json** file:</span></span>

    ![Screenshot zum Öffnen des Generators](/microsoftteams/platform/assets/images/tab-images/teamsTabScreenshot.PNG)

    <span data-ttu-id="8bbc9-131">**Wie lautet der Name Ihrer Lösung?**</span><span class="sxs-lookup"><span data-stu-id="8bbc9-131">**What is your solution name?**</span></span>

    <span data-ttu-id="8bbc9-132">Dies ist ihr Projektname.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-132">This is your project name.</span></span> <span data-ttu-id="8bbc9-133">Sie können den vorgeschlagenen Namen akzeptieren, indem Sie die **EINGABETASTE** drücken.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-133">You can accept the suggested name by selecting the **Enter** key.</span></span>

    <span data-ttu-id="8bbc9-134">**Wohin möchten Sie die Daten verschieben?**</span><span class="sxs-lookup"><span data-stu-id="8bbc9-134">**Where do you want to place the files?**</span></span>

    <span data-ttu-id="8bbc9-135">Sie befinden sich derzeit in Ihrem Projektverzeichnis.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-135">You are currently in your project directory.</span></span> <span data-ttu-id="8bbc9-136">Drücken Sie **die EINGABETASTE.**</span><span class="sxs-lookup"><span data-stu-id="8bbc9-136">Select **Enter**.</span></span>

    <span data-ttu-id="8bbc9-137">**Titel Ihres Microsoft Teams App-Projekts?**</span><span class="sxs-lookup"><span data-stu-id="8bbc9-137">**Title of your Microsoft Teams app project?**</span></span>

    <span data-ttu-id="8bbc9-138">Dies ist der Name Ihres App-Pakets und wird im App-Manifest und in der Beschreibung verwendet.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-138">This is your app package name and will be used in the app manifest and description.</span></span> <span data-ttu-id="8bbc9-139">Geben Sie einen Titel ein, oder drücken Sie **die EINGABETASTE,** um den Standardnamen zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-139">Enter a title or select **Enter** to accept the default name.</span></span>

    <span data-ttu-id="8bbc9-140">**Ihr (Firmen-)Name? (max. 32 Zeichen)**</span><span class="sxs-lookup"><span data-stu-id="8bbc9-140">**Your (company) name? (max 32 characters)**</span></span>

    <span data-ttu-id="8bbc9-141">Ihr Firmenname wird im App-Manifest verwendet.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-141">Your company name will be used in the app manifest.</span></span> <span data-ttu-id="8bbc9-142">Geben Sie einen Firmennamen ein, oder drücken Sie die **EINGABETASTE,** um den Standardnamen zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-142">Enter a company name or select **Enter** to accept the default name.</span></span>

    <span data-ttu-id="8bbc9-143">**Welche Manifestversion möchten Sie verwenden?**</span><span class="sxs-lookup"><span data-stu-id="8bbc9-143">**Which manifest version would you like to use?**</span></span>

    <span data-ttu-id="8bbc9-144">Wählen Sie das Standardschema aus.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-144">Select the default schema.</span></span>

    <span data-ttu-id="8bbc9-145">**Schnelles Gerüst? (J/n)**</span><span class="sxs-lookup"><span data-stu-id="8bbc9-145">**Quick scaffolding? (Y/n)**</span></span>

    <span data-ttu-id="8bbc9-146">Der Standardwert ist "ja". Geben Sie **n** ein, um Ihre Microsoft Partner-ID einzugeben.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-146">The default is yes; enter **n** to enter your Microsoft Partner Id.</span></span>

    <span data-ttu-id="8bbc9-147">**Geben Sie Ihre Microsoft Partner-ID ein, wenn Sie eine haben? (Leer lassen, um zu überspringen)**</span><span class="sxs-lookup"><span data-stu-id="8bbc9-147">**Enter your Microsoft Partner Id, if you have one? (Leave blank to skip)**</span></span>

    <span data-ttu-id="8bbc9-148">Dieses Feld ist nicht erforderlich und sollte nur verwendet werden, wenn Sie bereits Teil des [Microsoft Partner Network](https://partner.microsoft.com)sind.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-148">This field is not required and should only be used if you are already part of the [Microsoft Partner Network](https://partner.microsoft.com).</span></span>

    <span data-ttu-id="8bbc9-149">**Was möchten Sie Ihrem Projekt hinzufügen?**</span><span class="sxs-lookup"><span data-stu-id="8bbc9-149">**What do you want to add to your project?**</span></span>

    <span data-ttu-id="8bbc9-150">Select **( ) A &ast; Tab**.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-150">Select **( &ast; ) A Tab**.</span></span>

    <span data-ttu-id="8bbc9-151">**Die URL, unter der Sie diese Lösung hosten werden?**</span><span class="sxs-lookup"><span data-stu-id="8bbc9-151">**The URL where you will host this solution?**</span></span>

    <span data-ttu-id="8bbc9-152">Standardmäßig schlägt der Generator eine Azure-Website-URL vor.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-152">By default the generator suggests an Azure Web Sites URL.</span></span> <span data-ttu-id="8bbc9-153">Sie testen Ihre App nur lokal, daher ist keine gültige URL erforderlich.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-153">You are only testing your app locally, therefore, a valid URL is not necessary.</span></span>

    <span data-ttu-id="8bbc9-154">**Möchten Sie eine Ladeanzeige anzeigen, wenn Ihre App/Registerkarte geladen wird?**</span><span class="sxs-lookup"><span data-stu-id="8bbc9-154">**Would you like show a loading indicator when your app/tab loads?**</span></span>

    <span data-ttu-id="8bbc9-155">Schließen Sie beim Laden ihrer App oder Registerkarte **keine** Ladeanzeige ein.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-155">Choose **not** to include a loading indicator when your app or tab loads.</span></span> <span data-ttu-id="8bbc9-156">The default is no, enter **n**.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-156">The default is no, enter **n**.</span></span>

   <span data-ttu-id="8bbc9-157">**Möchten Sie, dass persönliche Apps ohne eine Registerkarten-Kopfleiste dargestellt werden?**</span><span class="sxs-lookup"><span data-stu-id="8bbc9-157">**Would you like personal apps to be rendered without a tab header-bar?**</span></span>

    <span data-ttu-id="8bbc9-158">Fügen Sie **keine** persönlichen Apps ein, die ohne Registerkartenkopfleiste gerendert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-158">Choose **not** to include personal apps to be rendered without a tab header-bar.</span></span> <span data-ttu-id="8bbc9-159">Der Standardwert ist "Nein", geben Sie **"n"** ein.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-159">Default is no, enter **n**.</span></span>

    <span data-ttu-id="8bbc9-160">**Möchten Sie testframework und erste Tests einbeziehen? (y/N)**</span><span class="sxs-lookup"><span data-stu-id="8bbc9-160">**Would you like to include Test framework and initial tests? (y/N)**</span></span>

    <span data-ttu-id="8bbc9-161">Schließen Sie **kein** Testframework für dieses Projekt ein.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-161">Choose **not** to include a test framework for this project.</span></span> <span data-ttu-id="8bbc9-162">Der Standardwert ist "ja". geben Sie **n** ein.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-162">The default is yes; enter **n**.</span></span>

    <span data-ttu-id="8bbc9-163">**Möchten Sie Azure Applications Insights für Telemetrie verwenden? (y/N)**</span><span class="sxs-lookup"><span data-stu-id="8bbc9-163">**Would you like to use Azure Applications Insights for telemetry? (y/N)**</span></span>

    <span data-ttu-id="8bbc9-164">Wählen Sie **aus, dass** [Azure Application Insights](/azure/azure-monitor/app/app-insights-overview)nicht eingeschlossen werden soll.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-164">Choose **not** to include [Azure Application Insights](/azure/azure-monitor/app/app-insights-overview).</span></span> <span data-ttu-id="8bbc9-165">Der Standardwert ist "nein". geben Sie **n** ein.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-165">The default is no; enter **n**.</span></span>

    <span data-ttu-id="8bbc9-166">**Standardregisterkartenname (max. 16 Zeichen)?**</span><span class="sxs-lookup"><span data-stu-id="8bbc9-166">**Default Tab Name (max 16 characters)?**</span></span>

    <span data-ttu-id="8bbc9-167">Nennen Sie Ihre Registerkarte. Dieser Registerkartenname wird im gesamten Projekt als Datei- oder URL-Pfadkomponente verwendet.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-167">Name your tab. This tab name will be used throughout your project as a file or URL path component.</span></span>

    <span data-ttu-id="8bbc9-168">**Welche Art von Registerkarte möchten Sie erstellen?**</span><span class="sxs-lookup"><span data-stu-id="8bbc9-168">**What kind of Tab would you like to create?**</span></span>

    <span data-ttu-id="8bbc9-169">Verwenden Sie die Pfeiltasten, um die **konfigurierbare** Registerkarte auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-169">Use the arrow keys to select **Configurable** tab.</span></span>

    <span data-ttu-id="8bbc9-170">**Welche Bereiche möchten Sie für Ihre Registerkarte verwenden?**</span><span class="sxs-lookup"><span data-stu-id="8bbc9-170">**What scopes do you intend to use for your Tab?**</span></span>

    <span data-ttu-id="8bbc9-171">Sie können ein Team oder einen Gruppenchat auswählen.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-171">You can select a team or a group chat.</span></span>

    <span data-ttu-id="8bbc9-172">**Benötigen Sie Azure AD-Unterstützung für einmaliges Anmelden (Single-Sign-On, SSO) für die Registerkarte?**</span><span class="sxs-lookup"><span data-stu-id="8bbc9-172">**Do you require Azure AD Single-Sign-On support for the tab?**</span></span>

    <span data-ttu-id="8bbc9-173">Wählen Sie aus, dass die Azure AD-Single Sign-On-Unterstützung für die Registerkarte **nicht** eingeschlossen werden soll. Der Standardwert ist "Ja", geben Sie **"n"** ein.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-173">Choose **not** to include Azure AD Single-Sign-On support for the tab. The default is yes, enter **n**.</span></span>

    <span data-ttu-id="8bbc9-174">**Soll diese Registerkarte in SharePoint Online verfügbar sein? (J/n)**</span><span class="sxs-lookup"><span data-stu-id="8bbc9-174">**Do you want this tab to be available in SharePoint Online? (Y/n)**</span></span>

    <span data-ttu-id="8bbc9-175">Geben Sie **n** ein.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-175">Enter **n**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="8bbc9-176">The path component **yourDefaultTabNameTab**, is the value that you entered in the generator for **Default Tab Name** plus the word **Tab**.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-176">The path component **yourDefaultTabNameTab**, is the value that you entered in the generator for **Default Tab Name** plus the word **Tab**.</span></span>
    >
    > <span data-ttu-id="8bbc9-177">Beispiel: DefaultTabName: **MyTab**  >  **/MyTabTab/**</span><span class="sxs-lookup"><span data-stu-id="8bbc9-177">For example: DefaultTabName: **MyTab** > **/MyTabTab/**</span></span>

1. <span data-ttu-id="8bbc9-178">Wechseln Sie in Visual Studio Code oder einem beliebigen Code-Editor zu Ihrem Projektverzeichnis, und öffnen Sie die folgende Datei:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-178">In Visual Studio Code or any code editor, go to your project directory and open the following file:</span></span>

    ```bash
    ./src/app/scripts/<yourDefaultTabNameTab>/<yourDefaultTabNameTab>.tsx
    ```

1. <span data-ttu-id="8bbc9-179">Suchen Sie die Methode, und fügen Sie oben im `render()` Containercode das folgende Tag und den folgenden `<div>` Inhalt `<PanelBody>` hinzu:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-179">Locate the `render()` method and add the following `<div>` tag and content to the top of the `<PanelBody>` container code:</span></span>

    ```html
        <PanelBody>
            <div style={styles.section}>
                Hello World! Yo Teams rocks!
            </div>
        </PanelBody>
    ```

1. <span data-ttu-id="8bbc9-180">Stellen Sie sicher, dass Sie die aktualisierte Datei speichern.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-180">Make sure to save the updated file.</span></span>

### <a name="build-and-run-your-application"></a><span data-ttu-id="8bbc9-181">Erstellen und Ausführen der Anwendung</span><span class="sxs-lookup"><span data-stu-id="8bbc9-181">Build and run your application</span></span>

<span data-ttu-id="8bbc9-182">Öffnen Sie an einer Eingabeaufforderung Das Projektverzeichnis, um die nächsten Aufgaben auszuführen.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-182">At a command prompt, open your project directory to complete the next tasks.</span></span>

#### <a name="create-the-app-package"></a><span data-ttu-id="8bbc9-183">Erstellen des App-Pakets</span><span class="sxs-lookup"><span data-stu-id="8bbc9-183">Create the app package</span></span>

<span data-ttu-id="8bbc9-184">Sie benötigen ein App-Paket, um Ihre Registerkarte in Teams zu testen.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-184">You must have an app package to test your tab in Teams.</span></span> <span data-ttu-id="8bbc9-185">Es handelt sich um einen ZIP-Ordner, der die folgenden erforderlichen Dateien enthält:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-185">It is a zip folder that contains the following required files:</span></span>

- <span data-ttu-id="8bbc9-186">Ein **Vollfarbsymbol** mit einer Auflösung von 192 x 192 Pixeln.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-186">A **full color icon** measuring 192 x 192 pixels.</span></span>
- <span data-ttu-id="8bbc9-187">Ein **transparentes Gliederungssymbol** mit einer Auflösung von 32 x 32 Pixeln.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-187">A **transparent outline icon** measuring 32 x 32 pixels.</span></span>
- <span data-ttu-id="8bbc9-188">Ein **manifest.jsfür** die Datei, die die Attribute Ihrer App angibt.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-188">A **manifest.json** file that specifies the attributes of your app.</span></span>

<span data-ttu-id="8bbc9-189">Das Paket wird über eine gulp-Aufgabe erstellt, die die manifest.json-Datei überprüft und den ZIP-Ordner im **./package-Verzeichnis** generiert.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-189">The package is created through a gulp task that validates the manifest.json file and generates the zip folder in the **./package directory**.</span></span> <span data-ttu-id="8bbc9-190">Geben Sie an der Eingabeaufforderung den folgenden Befehl ein:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-190">In the command prompt, enter the following command:</span></span>

```bash
gulp manifest
```

#### <a name="build-your-application"></a><span data-ttu-id="8bbc9-191">Erstellen Der Anwendung</span><span class="sxs-lookup"><span data-stu-id="8bbc9-191">Build your application</span></span>

<span data-ttu-id="8bbc9-192">Der Buildbefehl transpiliert Ihre Lösung in den Ordner **./dist.**</span><span class="sxs-lookup"><span data-stu-id="8bbc9-192">The build command transpiles your solution into the **./dist** folder.</span></span> <span data-ttu-id="8bbc9-193">Geben Sie in der Eingabeaufforderung den folgenden Befehl ein:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-193">Enter the following command in the command prompt:</span></span>

```bash
gulp build
```

#### <a name="run-your-application-in-localhost"></a><span data-ttu-id="8bbc9-194">Ausführen der Anwendung in localhost</span><span class="sxs-lookup"><span data-stu-id="8bbc9-194">Run your application in localhost</span></span>

1. <span data-ttu-id="8bbc9-195">Starten Sie einen lokalen Webserver, indem Sie in der Eingabeaufforderung Folgendes eingeben:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-195">Start a local web server by entering the following in the command prompt:</span></span>

    ```bash
    gulp serve
    ```

1. <span data-ttu-id="8bbc9-196">Geben Sie `http://localhost:3007/<yourDefaultAppNameTab>/` in Ihren Browser ein, ersetzen Sie diesen **<yourDefaultAppNameTab>** durch ihren Registerkartennamen, und zeigen Sie die Startseite Ihrer Anwendung an, wie in der folgenden Abbildung dargestellt:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-196">Enter `http://localhost:3007/<yourDefaultAppNameTab>/` in your browser, replace **<yourDefaultAppNameTab>** with your tab name, and view your application's home page as shown in the following image:</span></span>

    ![Screenshot der Startseite](~/assets/images/tab-images/homePage.png)

1. <span data-ttu-id="8bbc9-198">Um die Registerkartenkonfigurationsseite anzuzeigen, wechseln Sie zu `https://localhost:3007/<yourDefaultAppNameTab>/config.html` .</span><span class="sxs-lookup"><span data-stu-id="8bbc9-198">To view your tab configuration page, go to `https://localhost:3007/<yourDefaultAppNameTab>/config.html`.</span></span> <span data-ttu-id="8bbc9-199">Es wird Folgendes gezeigt:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-199">The following is shown:</span></span>

    ![Screenshot der Konfigurationsseite](~/assets/images/tab-images/configurationPage.png)

### <a name="establish-a-secure-tunnel-to-your-tab"></a><span data-ttu-id="8bbc9-201">Einrichten eines sicheren Tunnels zu Ihrer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="8bbc9-201">Establish a secure tunnel to your tab</span></span>

<span data-ttu-id="8bbc9-202">Microsoft Teams ist ein cloudbasiertes Produkt und erfordert, dass Ihre Registerkarteninhalte über HTTPS-Endpunkte aus der Cloud verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-202">Microsoft Teams is a cloud-based product and requires that your tab content be available from the cloud using HTTPS endpoints.</span></span> <span data-ttu-id="8bbc9-203">Teams lässt kein lokales Hosting zu.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-203">Teams does not allow local hosting.</span></span> <span data-ttu-id="8bbc9-204">Sie müssen ihre Registerkarte entweder auf einer öffentlichen URL veröffentlichen oder einen Proxy verwenden, der Ihren lokalen Port für eine internetbasierte URL verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-204">You must either publish your tab to a public URL or use a proxy that exposes your local port to an internet-facing URL.</span></span>

<span data-ttu-id="8bbc9-205">Verwenden Sie zum Testen der [Registerkartenerweiterung ngrok,](https://ngrok.com/docs)das in diese Anwendung integriert ist.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-205">To test your tab extension, use [ngrok](https://ngrok.com/docs), which is built into this application.</span></span> <span data-ttu-id="8bbc9-206">Ngrok ist ein Reverseproxysoftwaretool, das einen Tunnel zu den öffentlich verfügbaren HTTPS-Endpunkten Ihres lokal ausgeführten Webservers erstellt.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-206">Ngrok is a reverse proxy software tool that creates a tunnel to your locally running web server's publicly-available HTTPS endpoints.</span></span> <span data-ttu-id="8bbc9-207">Die Webendpunkte Ihres Servers sind während der aktuellen Sitzung auf Ihrem Computer verfügbar.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-207">Your server's web endpoints are available during the current session on your computer.</span></span> <span data-ttu-id="8bbc9-208">Wenn der Computer heruntergefahren wird oder in den Ruhezustand wechselt, ist der Dienst nicht mehr verfügbar.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-208">When the computer is shut down or goes to sleep the service is no longer available.</span></span>

<span data-ttu-id="8bbc9-209">Beenden Sie an der Eingabeaufforderung "localhost", und geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-209">In your command prompt, exit localhost and enter the following:</span></span>

```bash
gulp ngrok-serve
```

> [!IMPORTANT]
> <span data-ttu-id="8bbc9-210">Nachdem Ihre Registerkarte in Microsoft Teams hochgeladen und erfolgreich gespeichert wurde, können Sie sie im Registerkartenkatalog anzeigen, der Registerkartenleiste hinzufügen und damit interagieren, bis Ihre ngrok-Tunnelsitzung endet.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-210">After your tab has been uploaded to Microsoft Teams and successfully saved, you can view it in the tabs gallery, add it to the tabs bar, and interact with it until your ngrok tunnel session ends.</span></span> <span data-ttu-id="8bbc9-211">Wenn Sie Ihre ngrok-Sitzung neu starten, müssen Sie Ihre App mit der neuen URL aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-211">If you restart your ngrok session, you must update your app with the new URL.</span></span>

### <a name="upload-your-application-to-teams"></a><span data-ttu-id="8bbc9-212">Hochladen Der Anwendung Teams</span><span class="sxs-lookup"><span data-stu-id="8bbc9-212">Upload your application to Teams</span></span>

<span data-ttu-id="8bbc9-213">**So laden Sie Ihre Anwendung in Teams hoch**</span><span class="sxs-lookup"><span data-stu-id="8bbc9-213">**To upload your application to Teams**</span></span>

1. <span data-ttu-id="8bbc9-214">Wechseln Sie zu Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-214">Go to Microsoft Teams.</span></span> <span data-ttu-id="8bbc9-215">Wenn Sie die [webbasierte Version](https://teams.microsoft.com) verwenden, können Sie Ihren Front-End-Code mithilfe der [Entwicklertools](~/tabs/how-to/developer-tools.md)Ihres Browsers überprüfen.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-215">If you use the [web-based version](https://teams.microsoft.com) you can inspect your front-end code using your browser's [developer tools](~/tabs/how-to/developer-tools.md).</span></span>
1. <span data-ttu-id="8bbc9-216">Wählen Sie in Ihren Teams im linken Bereich die Auslassungspunkte &#x25CF;&#x25CF;&#x25CF; neben dem Team aus, das Sie zum Testen Ihrer Registerkarte verwenden, und wählen Sie **"Team verwalten"** aus.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-216">From your teams on the left pane, select the ellipses &#x25CF;&#x25CF;&#x25CF; next to the team that you are using to test your tab and choose **Manage team**.</span></span>
1. <span data-ttu-id="8bbc9-217">Wählen Sie im Hauptbereich in der Registerkartenleiste **"Apps"** aus, und wählen Sie **Hochladen eine benutzerdefinierte App** in der unteren rechten Ecke der Seite aus.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-217">In the main pane, select **Apps** from the tab bar and choose **Upload a custom app** located in the lower right corner of the page.</span></span>
1. <span data-ttu-id="8bbc9-218">Wechseln Sie zum Projektverzeichnis, navigieren Sie zum **Ordner "./package",** wählen Sie den ZIP-Ordner des App-Pakets aus, und wählen Sie **"Öffnen"** aus.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-218">Go your project directory, browse to the **./package** folder, select the app package zip folder, and choose **Open**.</span></span>

    ![Kanalregisterkarte hinzugefügt](../../assets/images/tab-images/channeltabadded.png)

1. <span data-ttu-id="8bbc9-220">Wählen  Sie im Dialogfeld Hinzufügen die Option Hinzufügen aus.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-220">Select **Add** in the pop-up dialog box.</span></span> <span data-ttu-id="8bbc9-221">Ihre Registerkarte wird in Teams hochgeladen.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-221">Your tab uploads into Teams.</span></span>
1. <span data-ttu-id="8bbc9-222">Kehren Sie zu Ihrem Team zurück, wählen Sie den Kanal aus, in dem Sie die Registerkarte anzeigen möchten, wählen Sie ➕ aus der Registerkartenleiste aus, und wählen Sie Ihre Registerkarte im Katalog aus.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-222">Return to your team, choose the channel where you want to display the tab, select ➕ from the tab bar, and choose your tab from the gallery.</span></span>
1. <span data-ttu-id="8bbc9-223">Befolgen Sie die Anweisungen zum Hinzufügen einer Registerkarte. Es gibt ein benutzerdefiniertes Konfigurationsdialogfeld für Die Kanal- oder Gruppenregisterkarte.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-223">Follow the directions for adding a tab. There is a custom configuration dialog box for your channel or group tab.</span></span>
1. <span data-ttu-id="8bbc9-224">Wählen Sie **Speichern aus,** und Ihre Registerkarte wird der Registerkartenleiste des Kanals hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-224">Select **Save** and your tab is added to the channel's tab bar.</span></span>

    ![Registerkarte "Kanal" hochgeladen](../../assets/images/tab-images/channeltabuploaded.png)

# <a name="aspnet-core"></a>[<span data-ttu-id="8bbc9-226">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8bbc9-226">ASP.NET Core</span></span>](#tab/aspnetcore)

### <a name="create-a-custom-channel-or-group-tab-with-aspnet-core"></a><span data-ttu-id="8bbc9-227">Erstellen einer benutzerdefinierten Kanal- oder Gruppenregisterkarte mit ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8bbc9-227">Create a custom channel or group tab with ASP.NET Core</span></span>

<span data-ttu-id="8bbc9-228">Sie können eine benutzerdefinierte Kanal- oder Gruppenregisterkarte mit C# und ASP.Net Core Razor-Seite erstellen.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-228">You can create a custom channel or group tab using C# and ASP.Net Core Razor page.</span></span> <span data-ttu-id="8bbc9-229">[App Studio für Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) wird auch verwendet, um Das App-Manifest fertig zu stellen und die Registerkarte für Teams bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-229">[App Studio for Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) is also used to finalize your app manifest and deploy your tab to Teams.</span></span>

### <a name="prerequisites-for-teams-apps"></a><span data-ttu-id="8bbc9-230">Voraussetzungen für Teams-Apps</span><span class="sxs-lookup"><span data-stu-id="8bbc9-230">Prerequisites for Teams apps</span></span>

<span data-ttu-id="8bbc9-231">Sie müssen die folgenden Voraussetzungen verstehen:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-231">You must have an understanding of the following prerequisites:</span></span>

- <span data-ttu-id="8bbc9-232">Sie müssen einen Office 365 Mandanten und ein Team mit aktivierter **Option "Hochladen benutzerdefinierter Apps zulassen"** konfiguriert haben.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-232">You must have an Office 365 tenant and a team configured with **Allow uploading custom apps** enabled.</span></span> <span data-ttu-id="8bbc9-233">Weitere Informationen finden Sie unter [Vorbereiten Ihres Office 365 Mandanten.](~/concepts/build-and-test/prepare-your-o365-tenant.md)</span><span class="sxs-lookup"><span data-stu-id="8bbc9-233">For more information, see [prepare your Office 365 tenant](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="8bbc9-234">Wenn Sie derzeit kein Microsoft 365 Konto haben, können Sie sich über das [Microsoft-Entwicklerprogramm](https://developer.microsoft.com/en-us/microsoft-365/dev-program)für ein kostenloses Abonnement registrieren.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-234">If you do not currently have a Microsoft 365 account, you can sign up for a free subscription through the [Microsoft Developer Program](https://developer.microsoft.com/en-us/microsoft-365/dev-program).</span></span> <span data-ttu-id="8bbc9-235">Das Abonnement bleibt aktiv, solange Sie es für die fortlaufende Entwicklung verwenden.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-235">The subscription remains active as long as you are using it for ongoing development.</span></span>

- <span data-ttu-id="8bbc9-236">Verwenden Sie App Studio, um Ihre Anwendung in Teams zu importieren.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-236">Use App Studio to import your application to Teams.</span></span> <span data-ttu-id="8bbc9-237">Um App Studio zu installieren, wählen Sie **Apps** ![ Store App in der ](~/assets/images/tab-images/storeApp.png) unteren linken Ecke der Teams App aus, und suchen Sie nach **App Studio.**</span><span class="sxs-lookup"><span data-stu-id="8bbc9-237">To install App Studio, select **Apps** ![Store App](~/assets/images/tab-images/storeApp.png) at the lower left corner of the Teams app, and search for **App Studio**.</span></span> <span data-ttu-id="8bbc9-238">Nachdem Sie die Kachel gefunden haben, wählen Sie sie aus, und wählen Sie im Popupdialogfeld **"Hinzufügen"** aus, um sie zu installieren.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-238">After you find the tile, select it and choose **Add** in the pop-up dialog box to install it.</span></span>

<span data-ttu-id="8bbc9-239">Darüber hinaus muss für dieses Projekt Folgendes in Ihrer Entwicklungsumgebung installiert sein:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-239">In addition, this project requires that you have the following installed in your development environment:</span></span>

- <span data-ttu-id="8bbc9-240">Die aktuelle Version der Visual Studio IDE, in der **die plattformübergreifende .NET CORE-Entwicklungsworkload** installiert ist.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-240">The current version of the Visual Studio IDE with the **.NET CORE cross-platform development** workload installed.</span></span> <span data-ttu-id="8bbc9-241">Wenn Sie noch nicht über Visual Studio verfügen, können Sie die neueste [Microsoft Visual Studio Community Version](https://visualstudio.microsoft.com/downloads) kostenlos herunterladen und installieren.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-241">If you do not already have Visual Studio, you can download and install the latest [Microsoft Visual Studio Community](https://visualstudio.microsoft.com/downloads) version for free.</span></span>

- <span data-ttu-id="8bbc9-242">Das [ngrok-Reverseproxytool.](https://ngrok.com)</span><span class="sxs-lookup"><span data-stu-id="8bbc9-242">The [ngrok](https://ngrok.com) reverse proxy tool.</span></span> <span data-ttu-id="8bbc9-243">Verwenden Sie ngrok, um einen Tunnel zu den öffentlich verfügbaren HTTPS-Endpunkten Ihres lokal ausgeführten Webservers zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-243">Use ngrok to create a tunnel to your locally running web server's publicly-available HTTPS endpoints.</span></span> <span data-ttu-id="8bbc9-244">Sie können [ngrok herunterladen.](https://ngrok.com/download)</span><span class="sxs-lookup"><span data-stu-id="8bbc9-244">You can [download ngrok](https://ngrok.com/download).</span></span>

### <a name="get-the-source-code"></a><span data-ttu-id="8bbc9-245">Abrufen des Quellcodes</span><span class="sxs-lookup"><span data-stu-id="8bbc9-245">Get the source code</span></span>

<span data-ttu-id="8bbc9-246">Erstellen Sie an einer Eingabeaufforderung ein neues Verzeichnis für Ihr Registerkartenprojekt.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-246">At a command prompt, create a new directory for your tab project.</span></span> <span data-ttu-id="8bbc9-247">Ein einfaches Projekt wird bereitgestellt, um Ihnen den Einstieg zu erleichtern.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-247">A simple project is provided to get you started.</span></span> <span data-ttu-id="8bbc9-248">Klonen Sie das Beispiel-Repository mit dem folgenden Befehl in Ihr neues Verzeichnis:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-248">Clone the sample repository into your new directory using the following command:</span></span>

```bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

<span data-ttu-id="8bbc9-249">Alternativ können Sie den Quellcode abrufen, indem Sie den ZIP-Ordner herunterladen und die Dateien extrahieren.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-249">Alternately, you can retrieve the source code by downloading the zip folder and extracting the files.</span></span>

<span data-ttu-id="8bbc9-250">**So erstellen Sie das Registerkartenprojekt und führen es aus**</span><span class="sxs-lookup"><span data-stu-id="8bbc9-250">**To build and run the tab project**</span></span>

1. <span data-ttu-id="8bbc9-251">Nachdem Sie über den Quellcode verfügen, wechseln Sie zu Visual Studio, und wählen Sie **"Projekt oder Projektmappe öffnen"** aus.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-251">After you have the source code, go to Visual Studio and select **Open a project or solution**.</span></span>
1. <span data-ttu-id="8bbc9-252">Wechseln Sie zum Registerkartenanwendungsverzeichnis, und öffnen **Sie "ChannelGroupTab.sln".**</span><span class="sxs-lookup"><span data-stu-id="8bbc9-252">Go to the tab application directory and open **ChannelGroupTab.sln**.</span></span>
1. <span data-ttu-id="8bbc9-253">Drücken Sie **F5,** oder wählen Sie im Menü **"Debuggen"** die Option **"Debuggen starten"** aus, um die Anwendung zu erstellen und auszuführen.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-253">To build and run your application, press **F5** or choose **Start Debugging** from the **Debug** menu.</span></span>
1. <span data-ttu-id="8bbc9-254">Wechseln Sie in einem Browser zu den folgenden URLs, und überprüfen Sie, ob die Anwendung ordnungsgemäß geladen wurde:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-254">In a browser, go to the following URLs and verify the application loaded properly:</span></span>

    - `http://localhost:44355`
    - `http://localhost:44355/privacy`
    - `http://localhost:44355/tou`

### <a name="review-the-source-code"></a><span data-ttu-id="8bbc9-255">Überprüfen des Quellcodes</span><span class="sxs-lookup"><span data-stu-id="8bbc9-255">Review the source code</span></span>

#### <a name="startupcs"></a><span data-ttu-id="8bbc9-256">Startup.cs</span><span class="sxs-lookup"><span data-stu-id="8bbc9-256">Startup.cs</span></span>

<span data-ttu-id="8bbc9-257">Dieses Projekt wurde aus einer leeren Vorlage für ASP.NET Core 2.2-Webanwendung erstellt, wobei das Kontrollkästchen **"Erweitert – Für HTTPS konfigurieren"** beim Setup aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-257">This project was created from an ASP.NET Core 2.2 Web Application empty template with the **Advanced - Configure for HTTPS** check box selected at setup.</span></span> <span data-ttu-id="8bbc9-258">Die MVC-Dienste werden durch die Methode des Abhängigkeitsinjektionsframeworks `ConfigureServices()` registriert.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-258">The MVC services are registered by the dependency injection framework's `ConfigureServices()` method.</span></span> <span data-ttu-id="8bbc9-259">Darüber hinaus ermöglicht die leere Vorlage nicht standardmäßig die Bereitstellung statischer Inhalte, sodass die Middleware für statische Dateien der Methode mit dem folgenden Code hinzugefügt `Configure()` wird:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-259">Additionally, the empty template does not enable serving static content by default, so the static files middleware is added to the `Configure()` method using the following code:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
  {
    services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_2);
  }
public void Configure(IApplicationBuilder app)
  {
    app.UseStaticFiles();
    app.UseMvc();
  }
```

#### <a name="wwwroot-folder"></a><span data-ttu-id="8bbc9-260">Wwwroot-Ordner</span><span class="sxs-lookup"><span data-stu-id="8bbc9-260">wwwroot folder</span></span>

<span data-ttu-id="8bbc9-261">In ASP.NET Core sucht die Anwendung im Webstammordner nach statischen Dateien.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-261">In ASP.NET Core, the web root folder is where the application looks for static files.</span></span>

#### <a name="indexcshtml"></a><span data-ttu-id="8bbc9-262">Index.cshtml</span><span class="sxs-lookup"><span data-stu-id="8bbc9-262">Index.cshtml</span></span>

<span data-ttu-id="8bbc9-263">ASP.NET Core behandelt Dateien mit dem Namen **Index** als Standard- oder Startseite für die Website.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-263">ASP.NET Core treats files called **Index** as the default or home page for the site.</span></span> <span data-ttu-id="8bbc9-264">Wenn Ihre Browser-URL auf den Stamm der Website zeigt, wird **Index.cshtml** als Startseite für Ihre Anwendung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-264">When your browser URL points to the root of the site, **Index.cshtml** is displayed as the home page for your application.</span></span>

#### <a name="tabcs"></a><span data-ttu-id="8bbc9-265">Tab.cs</span><span class="sxs-lookup"><span data-stu-id="8bbc9-265">Tab.cs</span></span>

<span data-ttu-id="8bbc9-266">Diese C#-Datei enthält eine Methode, die während der Konfiguration von **Tab.cshtml** aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-266">This C# file contains a method that is called from **Tab.cshtml** during configuration.</span></span>

#### <a name="appmanifest-folder"></a><span data-ttu-id="8bbc9-267">AppManifest-Ordner</span><span class="sxs-lookup"><span data-stu-id="8bbc9-267">AppManifest folder</span></span>

<span data-ttu-id="8bbc9-268">Dieser Ordner enthält die folgenden erforderlichen App-Paketdateien:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-268">This folder contains the following required app package files:</span></span>

- <span data-ttu-id="8bbc9-269">Ein **Vollfarbsymbol** mit einer Auflösung von 192 x 192 Pixeln.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-269">A **full color icon** measuring 192 x 192 pixels.</span></span>
- <span data-ttu-id="8bbc9-270">Ein **transparentes Gliederungssymbol** mit einer Auflösung von 32 x 32 Pixeln.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-270">A **transparent outline icon** measuring 32 x 32 pixels.</span></span>
- <span data-ttu-id="8bbc9-271">Ein **manifest.jsfür** die Datei, die die Attribute Ihrer App angibt.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-271">A **manifest.json** file that specifies the attributes of your app.</span></span>

<span data-ttu-id="8bbc9-272">Diese Dateien müssen in einem App-Paket gezippt werden, um Ihre Registerkarte in Teams hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-272">These files need to be zipped in an app package for use in uploading your tab to Teams.</span></span> <span data-ttu-id="8bbc9-273">Wenn ein Benutzer die Registerkarte hinzufügt oder aktualisiert, lädt Microsoft Teams das `configurationUrl` angegebene Element in Ihrem Manifest, einbettet es in einen IFrame und rendert es auf der Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-273">When a user chooses to add or update your tab, Microsoft Teams loads the `configurationUrl` specified in your manifest, embeds it in an IFrame, and renders it in your tab.</span></span>

#### <a name="csproj"></a><span data-ttu-id="8bbc9-274">CSPROJ</span><span class="sxs-lookup"><span data-stu-id="8bbc9-274">.csproj</span></span>

<span data-ttu-id="8bbc9-275">Klicken Sie im Fenster Visual Studio Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie **"Bearbeiten Project Datei"** aus.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-275">In the Visual Studio Solution Explorer window, right-click on the project and select **Edit Project File**.</span></span> <span data-ttu-id="8bbc9-276">Am Ende der Datei wird der folgende Code angezeigt, der Ihren ZIP-Ordner erstellt und aktualisiert, wenn die Anwendung erstellt wird:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-276">At the end of the file, you see the following code that creates and updates your zip folder when the application builds:</span></span>

```xml
<PropertyGroup>
    <PostBuildEvent>powershell.exe Compress-Archive -Path \"$(ProjectDir)AppManifest\*\" -DestinationPath \"$(TargetDir)tab.zip\" -Force</PostBuildEvent>
  </PropertyGroup>

  <ItemGroup>
    <EmbeddedResource Include="AppManifest\icon-outline.png">
      <CopyToOutputDirectory>Always</CopyToOutputDirectory>
    </EmbeddedResource>
    <EmbeddedResource Include="AppManifest\icon-color.png">
      <CopyToOutputDirectory>Always</CopyToOutputDirectory>
    </EmbeddedResource>
    <EmbeddedResource Include="AppManifest\manifest.json">
      <CopyToOutputDirectory>Always</CopyToOutputDirectory>
    </EmbeddedResource>
  </ItemGroup>
```

### <a name="establish-a-secure-tunnel-to-your-tab-for-teams"></a><span data-ttu-id="8bbc9-277">Einrichten eines sicheren Tunnels zu Ihrer Registerkarte für Teams</span><span class="sxs-lookup"><span data-stu-id="8bbc9-277">Establish a secure tunnel to your tab for Teams</span></span>

<span data-ttu-id="8bbc9-278">Microsoft Teams ist ein cloudbasiertes Produkt und erfordert, dass Ihre Registerkarteninhalte über HTTPS-Endpunkte aus der Cloud verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-278">Microsoft Teams is a cloud-based product and requires that your tab content be available from the cloud using HTTPS endpoints.</span></span> <span data-ttu-id="8bbc9-279">Teams lässt kein lokales Hosting zu.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-279">Teams does not allow local hosting.</span></span> <span data-ttu-id="8bbc9-280">Sie müssen ihre Registerkarte entweder über eine öffentliche URL veröffentlichen oder einen Proxy verwenden, der Ihren lokalen Port für eine internetbasierte URL verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-280">You must either publish your tab to a public URL, or use a proxy that exposes your local port to an internet-facing URL.</span></span>

<span data-ttu-id="8bbc9-281">Verwenden Sie zum Testen Der Registerkarte [ngrok](https://ngrok.com/docs).</span><span class="sxs-lookup"><span data-stu-id="8bbc9-281">To test your tab, use [ngrok](https://ngrok.com/docs).</span></span> <span data-ttu-id="8bbc9-282">Die Webendpunkte Ihres Servers sind verfügbar, während ngrok auf Ihrem Computer ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-282">Your server's web endpoints are available while ngrok is running on your computer.</span></span> <span data-ttu-id="8bbc9-283">In der kostenlosen Version von ngrok unterscheiden sich die URLs beim nächsten Start von ngrok, wenn Sie ngrok schließen.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-283">In the free version of ngrok, if you close ngrok, the URLs are different the next time you start it.</span></span>

- <span data-ttu-id="8bbc9-284">Führen Sie an einer Eingabeaufforderung im Stammverzeichnis des Projekts den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-284">At a command prompt in the root of your project directory, run the following command:</span></span>

    ```bash
    ngrok http https://localhost:44355 -host-header="localhost:44355"
    ```

- <span data-ttu-id="8bbc9-285">Ngrok lauscht auf Anforderungen aus dem Internet und leitet sie an Ihre Anwendung weiter, wenn sie auf Port 44355 ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-285">Ngrok listens to requests from the internet and routes them to your application when it is running on port 44355.</span></span> <span data-ttu-id="8bbc9-286">Es sollte etwa so `https://y8rCgT2b.ngrok.io/` aussehen, wo **y8rCgT2b** durch Ihre alphangrok-numerische HTTPS-URL ersetzt wird.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-286">It should resemble `https://y8rCgT2b.ngrok.io/` where **y8rCgT2b** is replaced by your ngrok alpha-numeric HTTPS URL.</span></span>

- <span data-ttu-id="8bbc9-287">Stellen Sie sicher, dass die Eingabeaufforderung mit ngrok ausgeführt wird, und notieren Sie sich die URL.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-287">Ensure that you keep the command prompt with ngrok running and make a note of the URL.</span></span>

### <a name="update-your-application"></a><span data-ttu-id="8bbc9-288">Aktualisieren Der Anwendung</span><span class="sxs-lookup"><span data-stu-id="8bbc9-288">Update your application</span></span>

<span data-ttu-id="8bbc9-289">Innerhalb von **Tab.cshtml** zeigt die Anwendung dem Benutzer zwei Optionsschaltflächen zum Anzeigen der Registerkarte mit einem roten oder grauen Symbol an.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-289">Within **Tab.cshtml** the application presents the user with two option buttons for displaying the tab with either a red or gray icon.</span></span> <span data-ttu-id="8bbc9-290">Durch Auswählen der Schaltfläche **"Grau auswählen"** oder **"Rot auswählen"** wird die `saveGray()` Schaltfläche `saveRed()` `settings.setValidityState(true)` **"Speichern"** auf der Konfigurationsseite festgelegt bzw. aktiviert.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-290">Choosing the **Select Gray** or **Select Red** button triggers `saveGray()` or `saveRed()`, respectively, sets `settings.setValidityState(true)`, and enables the **Save** button on the configuration page.</span></span> <span data-ttu-id="8bbc9-291">Dieser Code teilt Teams mit, dass Sie die Konfigurationsanforderungen erfüllt haben und die Installation fortgesetzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-291">This code lets Teams know that you have completed the configuration requirements and the installation can proceed.</span></span> <span data-ttu-id="8bbc9-292">Die Parameter `settings.setSettings` von sind festgelegt.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-292">The parameters of `settings.setSettings` are set.</span></span> <span data-ttu-id="8bbc9-293">Schließlich `saveEvent.notifySuccess()` wird aufgerufen, um anzugeben, dass die Inhalts-URL erfolgreich aufgelöst wurde.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-293">Finally, `saveEvent.notifySuccess()` is called to indicate that the content URL has been successfully resolved.</span></span>

#### <a name="_layoutcshtml"></a><span data-ttu-id="8bbc9-294">_Layout.cshtml</span><span class="sxs-lookup"><span data-stu-id="8bbc9-294">_Layout.cshtml</span></span>

<span data-ttu-id="8bbc9-295">Damit Die Registerkarte in Teams angezeigt werden kann, müssen Sie das **Microsoft Teams JavaScript-Client-SDK** und einen Aufruf nach `microsoftTeams.initialize()` dem Laden der Seite einschließen.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-295">For your tab to display in Teams, you must include the **Microsoft Teams JavaScript client SDK** and include a call to `microsoftTeams.initialize()` after your page loads.</span></span> <span data-ttu-id="8bbc9-296">So kommunizieren Ihre Registerkarte und der Teams-Client:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-296">This is how your tab and the Teams client communicate:</span></span>

<span data-ttu-id="8bbc9-297">Wechseln Sie zum Ordner **"Freigegeben",** öffnen **Sie _Layout.cshtml,** und fügen Sie dem Tag Folgendes `<head>` hinzu:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-297">Go to the **Shared** folder, open **_Layout.cshtml**, and add the following to the `<head>` tag:</span></span>

```html
<script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
<script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>
```

> [!IMPORTANT]
> <span data-ttu-id="8bbc9-298">Kopieren Sie die URLs von dieser Seite nicht, und fügen Sie `<script src="...">` sie nicht ein, da sie nicht die neueste Version darstellen.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-298">Do not copy and paste the `<script src="...">` URLs from this page, as they do not represent the latest version.</span></span> <span data-ttu-id="8bbc9-299">Um die neueste Version des SDK zu erhalten, wechseln Sie immer zu [Microsoft Teams JavaScript-API.](https://www.npmjs.com/package/@microsoft/teams-js)</span><span class="sxs-lookup"><span data-stu-id="8bbc9-299">To get the latest version of the SDK, always go to [Microsoft Teams JavaScript API](https://www.npmjs.com/package/@microsoft/teams-js).</span></span>

#### <a name="tabcshtml"></a><span data-ttu-id="8bbc9-300">Tab.cshtml</span><span class="sxs-lookup"><span data-stu-id="8bbc9-300">Tab.cshtml</span></span>

<span data-ttu-id="8bbc9-301">**So aktualisieren Sie Tab.cshtml**</span><span class="sxs-lookup"><span data-stu-id="8bbc9-301">**To update Tab.cshtml**</span></span>

1. <span data-ttu-id="8bbc9-302">Öffnen **Sie Tab.cshtml** in Visual Studio, und aktualisieren Sie die eingebettete `<script>` .</span><span class="sxs-lookup"><span data-stu-id="8bbc9-302">Open **Tab.cshtml** in Visual Studio and update the embedded `<script>`.</span></span>

1. <span data-ttu-id="8bbc9-303">Rufen Sie oben im Skript `microsoftTeams.initialize()` .</span><span class="sxs-lookup"><span data-stu-id="8bbc9-303">At the top of the script, call `microsoftTeams.initialize()`.</span></span>

1. <span data-ttu-id="8bbc9-304">Aktualisieren Sie die `websiteUrl` Werte in jeder Funktion mit der `contentUrl` HTTPS-ngrok-URL auf Ihre Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-304">Update the `websiteUrl` and `contentUrl` values in each function with the HTTPS ngrok URL to your tab.</span></span>

    <span data-ttu-id="8bbc9-305">Ihr Code sollte nun Folgendes enthalten, wobei **y8rCgT2b** durch Ihre ngrok-URL ersetzt wird:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-305">Your code should now include the following with **y8rCgT2b** replaced with your ngrok URL:</span></span>

    ```javascript
        microsoftTeams.initialize();

        let saveGray = () => {
            microsoftTeams.settings.registerOnSaveHandler(function (saveEvent) {
                microsoftTeams.settings.setSettings({
                    websiteUrl: `https://y8rCgT2b.ngrok.io`,
                    contentUrl: `https://y8rCgT2b.ngrok.io/gray/`,
                    entityId: "grayIconTab",
                    suggestedDisplayName: "MyNewTab"
                });
                saveEvent.notifySuccess();
            });
        }

        let saveRed = () => {
            microsoftTeams.settings.registerOnSaveHandler(function (saveEvent) {
                microsoftTeams.settings.setSettings({
                    websiteUrl: `https://y8rCgT2b.ngrok.io`,
                    contentUrl: `https://y8rCgT2b.ngrok.io/red/`,
                    entityId: "redIconTab",
                    suggestedDisplayName: "MyNewTab"
                });
                saveEvent.notifySuccess();
        });
        }
    ```

1. <span data-ttu-id="8bbc9-306">Speichern Sie die aktualisierte **Registerkarte.cshtml**.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-306">Save the updated **Tab.cshtml**.</span></span>

### <a name="build-and-run-your-application-for-teams"></a><span data-ttu-id="8bbc9-307">Erstellen und Ausführen der Anwendung für Teams</span><span class="sxs-lookup"><span data-stu-id="8bbc9-307">Build and run your application for Teams</span></span>

<span data-ttu-id="8bbc9-308">**So erstellen Sie Ihre Anwendung und führen sie aus**</span><span class="sxs-lookup"><span data-stu-id="8bbc9-308">**To build and run your application**</span></span>

1. <span data-ttu-id="8bbc9-309">Drücken Sie in Visual Studio **F5,** oder wählen Sie im Menü **"Debuggen"** die Option **"Debuggen starten"** aus.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-309">In Visual Studio, press **F5** or choose **Start Debugging** from the **Debug** menu.</span></span>
1. <span data-ttu-id="8bbc9-310">Stellen Sie sicher, dass **ngrok** ausgeführt wird und ordnungsgemäß funktioniert, indem Sie Ihren Browser öffnen und über die ngrok-HTTPS-URL, die im Eingabeaufforderungsfenster bereitgestellt wurde, zur Inhaltsseite wechseln.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-310">Verify that **ngrok** is running and working properly by opening your browser and going to your content page via the ngrok HTTPS URL that was provided in your command prompt window.</span></span>

> [!TIP]
> <span data-ttu-id="8bbc9-311">Sie müssen ihre Anwendung sowohl in Visual Studio als auch in ngrok ausführen, um die in diesem Artikel beschriebenen Schritte auszuführen.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-311">You need to have both your application in Visual Studio and ngrok running to complete the steps provided in this article.</span></span> <span data-ttu-id="8bbc9-312">Wenn Sie die Ausführung der Anwendung in Visual Studio beenden müssen, um daran zu arbeiten, **führen Sie ngrok weiter** aus.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-312">If you need to stop running your application in Visual Studio to work on it, **keep ngrok running**.</span></span> <span data-ttu-id="8bbc9-313">Beim Neustart in Visual Studio wird die Weiterleitung der Anwendungsanforderung überwacht und fortgesetzt.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-313">It listens and resumes routing your application's request when it restarts in Visual Studio.</span></span> <span data-ttu-id="8bbc9-314">Wenn Sie den ngrok-Dienst neu starten müssen, wird eine neue URL zurückgegeben, und Sie müssen Ihre Anwendung mit der neuen URL aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-314">If you have to restart the ngrok service it returns a new URL and you have to update your application with the new URL.</span></span>

### <a name="upload-your-tab-for-teams"></a><span data-ttu-id="8bbc9-315">Hochladen Ihrer Registerkarte für Teams</span><span class="sxs-lookup"><span data-stu-id="8bbc9-315">Upload your tab for Teams</span></span>

> [!NOTE]
> <span data-ttu-id="8bbc9-316">App Studio kann verwendet werden, um Ihre **manifest.jszu** bearbeiten und das fertige Paket in Teams hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-316">App Studio can be used to edit your **manifest.json** file and upload the completed package to Teams.</span></span> <span data-ttu-id="8bbc9-317">Sie können die **manifest.js** auch manuell bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-317">You can also manually edit the **manifest.json** file.</span></span> <span data-ttu-id="8bbc9-318">Stellen Sie in diesem Fall sicher, dass Sie die Lösung erneut erstellen, um die hochzuladende **tab.zipdatei** zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-318">If you do, ensure that you build the solution again to create the **tab.zip** file to upload.</span></span>

<span data-ttu-id="8bbc9-319">**So laden Sie Ihre Registerkarte mit App Studio hoch**</span><span class="sxs-lookup"><span data-stu-id="8bbc9-319">**To upload your tab with App Studio**</span></span>

1. <span data-ttu-id="8bbc9-320">Wechseln Sie zu Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-320">Go to Microsoft Teams.</span></span> <span data-ttu-id="8bbc9-321">Wenn Sie die [webbasierte Version](https://teams.microsoft.com)verwenden, können Sie Ihren Front-End-Code mithilfe der [Entwicklertools](~/tabs/how-to/developer-tools.md)Ihres Browsers überprüfen.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-321">If you use the [web-based version](https://teams.microsoft.com), you can inspect your front-end code using your browser's [developer tools](~/tabs/how-to/developer-tools.md).</span></span>

1. <span data-ttu-id="8bbc9-322">Wechseln Sie zu **App Studio,** und wählen Sie die Registerkarte **"Manifest-Editor"** aus.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-322">Go to **App Studio** and select the **Manifest editor** tab.</span></span>

1. <span data-ttu-id="8bbc9-323">Wählen Sie im **Manifest-Editor** eine **vorhandene App importieren** aus, um mit dem Aktualisieren des App-Pakets für Ihre Registerkarte zu beginnen. Der Quellcode enthält ein eigenes teilweise vollständiges Manifest.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-323">Select **Import an existing app** in the **Manifest editor** to begin updating the app package for your tab. The source code comes with its own partially complete manifest.</span></span> <span data-ttu-id="8bbc9-324">Der Name Ihres App-Pakets ist **tab.zip.**</span><span class="sxs-lookup"><span data-stu-id="8bbc9-324">The name of your app package is **tab.zip**.</span></span> <span data-ttu-id="8bbc9-325">Es ist über den folgenden Pfad verfügbar:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-325">It is available from the following path:</span></span>

    ```bash
    /bin/Debug/netcoreapp2.2/tab.zip
    ```

1. <span data-ttu-id="8bbc9-326">Hochladen app Studio **tab.zip.**</span><span class="sxs-lookup"><span data-stu-id="8bbc9-326">Upload **tab.zip** to App Studio.</span></span>

#### <a name="update-your-app-package-with-manifest-editor"></a><span data-ttu-id="8bbc9-327">Aktualisieren des App-Pakets mit dem Manifest-Editor</span><span class="sxs-lookup"><span data-stu-id="8bbc9-327">Update your app package with Manifest editor</span></span>

<span data-ttu-id="8bbc9-328">Nachdem Sie Das App-Paket in App Studio hochgeladen haben, müssen Sie es konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-328">After you have uploaded your app package into App Studio, you must configure it.</span></span>

<span data-ttu-id="8bbc9-329">Wählen Sie die Kachel für Ihre neu importierte Registerkarte im rechten Bereich der Willkommensseite des Manifest-Editors aus.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-329">Select the tile for your newly imported tab in the right panel of the Manifest editor welcome page.</span></span>

<span data-ttu-id="8bbc9-330">Es gibt eine Liste der Schritte auf der linken Seite des Manifest-Editors und auf der rechten Seite eine Liste der Eigenschaften, die Werte für jeden dieser Schritte aufweisen müssen.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-330">There is a list of steps on the left side of the Manifest editor, and on the right, a list of properties that must have values for each of those steps.</span></span> <span data-ttu-id="8bbc9-331">Ein Großteil der Informationen wurde von Ihrem **manifest.js** bereitgestellt, es gibt jedoch Felder, die Sie aktualisieren müssen.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-331">Much of the information has been provided by your **manifest.json** but there are fields that you must update.</span></span>

##### <a name="details-app-details"></a><span data-ttu-id="8bbc9-332">Details: App-Details</span><span class="sxs-lookup"><span data-stu-id="8bbc9-332">Details: App details</span></span>

<span data-ttu-id="8bbc9-333">Im Abschnitt **"App-Details":**</span><span class="sxs-lookup"><span data-stu-id="8bbc9-333">In the **App details** section:</span></span>

1. <span data-ttu-id="8bbc9-334">Wählen Sie unter **"Identifikation"** die Option **"Generieren"** aus, um die Platzhalter-ID durch die erforderliche GUID für Ihre Registerkarte zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-334">Under **Identification**, select **Generate** to replace the placeholder ID with the required GUID for your tab.</span></span>

1. <span data-ttu-id="8bbc9-335">Aktualisieren Sie unter **"Entwicklerinformationen"** **die Website** mit Ihrer **ngrok** HTTPS-URL.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-335">Under **Developer information**, update **Website** with your **ngrok** HTTPS URL.</span></span>

1. <span data-ttu-id="8bbc9-336">Aktualisieren Sie unter **App-URLs** die **Datenschutzerklärung** `https://<yourngrokurl>/privacy` und die **Nutzungsbedingungen** auf `https://<yourngrokurl>/tou`>.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-336">Under **App URLs**, update the **Privacy statement** to `https://<yourngrokurl>/privacy` and **Terms of use** to `https://<yourngrokurl>/tou`>.</span></span>

##### <a name="capabilities-tabs"></a><span data-ttu-id="8bbc9-337">Funktionen: Registerkarten</span><span class="sxs-lookup"><span data-stu-id="8bbc9-337">Capabilities: Tabs</span></span>

<span data-ttu-id="8bbc9-338">Im Abschnitt **"Registerkarten":**</span><span class="sxs-lookup"><span data-stu-id="8bbc9-338">In the **Tabs** section:</span></span>

1. <span data-ttu-id="8bbc9-339">Wählen Sie **auf der Registerkarte "Team"** die Option **"Hinzufügen"** aus.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-339">Under **Team tab**, select **Add**.</span></span>

1. <span data-ttu-id="8bbc9-340">Aktualisieren Sie im Popupfenster der **Registerkarte "Team"** die **Konfigurations-URL** auf `https://<yourngrokurl>/tab` .</span><span class="sxs-lookup"><span data-stu-id="8bbc9-340">In the **Team tab** pop-up window, update the **Configuration URL** to `https://<yourngrokurl>/tab`.</span></span>

1. <span data-ttu-id="8bbc9-341">Stellen Sie sicher, dass die **Kontrollkästchen "Konfiguration aktualisieren können",** **"Team"** und **"Gruppenchat"** aktiviert sind, und wählen Sie **"Speichern"** aus.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-341">Ensure the **Can update configuration?**, **Team**, and **Group chat** checkboxes are selected and select **Save**.</span></span>

##### <a name="finish-domains-and-permissions"></a><span data-ttu-id="8bbc9-342">Fertig stellen: Domänen und Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="8bbc9-342">Finish: Domains and permissions</span></span>

<span data-ttu-id="8bbc9-343">Im Abschnitt **"Domänen und Berechtigungen"** müssen **Domänen von Ihren Registerkarten** Ihre ngrok-URL ohne das HTTPS-Präfix `<yourngrokurl>.ngrok.io/` enthalten.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-343">In the **Domains and permissions** section, **Domains from your tabs** must contain your ngrok URL without the HTTPS prefix `<yourngrokurl>.ngrok.io/`.</span></span>

##### <a name="finish-test-and-distribute"></a><span data-ttu-id="8bbc9-344">Fertig stellen: Testen und Verteilen</span><span class="sxs-lookup"><span data-stu-id="8bbc9-344">Finish: Test and distribute</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bbc9-345">Auf der rechten Seite wird in der **Beschreibung** die folgende Warnung angezeigt:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-345">On the right, in **Description**, you see the following warning:</span></span>
>
> <span data-ttu-id="8bbc9-346">&#9888; "**Das Array "validDomains" darf keine Tunnelwebsite enthalten...**"</span><span class="sxs-lookup"><span data-stu-id="8bbc9-346">&#9888; "**The 'validDomains' array cannot contain a tunneling site...**"</span></span>
>
> <span data-ttu-id="8bbc9-347">Diese Warnung kann beim Testen der Registerkarte ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-347">This warning can be ignored while testing your tab.</span></span>

1. <span data-ttu-id="8bbc9-348">Wählen Sie im Abschnitt **"Testen und Verteilen"** die Option **"Installieren"** aus.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-348">In the **Test and Distribute** section, select **Install**.</span></span>

1. <span data-ttu-id="8bbc9-349">Wählen Sie im Popupdialogfeld **"Zu einem Team hinzufügen"** oder aus der Dropdownliste die Option **"Zu einem Chat hinzufügen"** aus.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-349">In the pop-up dialog box, select **Add to a team** or from the drop-down, select **Add to a chat**.</span></span>

1. <span data-ttu-id="8bbc9-350">Wählen Sie das Team oder den Chat aus, in dem die Registerkarte angezeigt werden soll, und wählen Sie **"Registerkarte einrichten"** aus.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-350">Choose the team or chat where you want the tab to be displayed and select **Set up a tab**.</span></span>

1. <span data-ttu-id="8bbc9-351">Wählen Sie im nächsten Popupdialogfeld entweder **"Grau"** oder **"Rot"** aus, und wählen Sie **"Speichern"** aus.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-351">In the next pop-up dialog box, choose either **Select Gray** or **Select Red**, and select **Save**.</span></span>

1. <span data-ttu-id="8bbc9-352">Um Ihre Registerkarte anzuzeigen, wechseln Sie zu dem Team oder Chat, in dem Sie die Registerkarte installiert haben, und wählen Sie sie in der Registerkartenleiste aus.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-352">To view your tab, go to the team or chat where you installed the tab, and select it from the tab bar.</span></span> <span data-ttu-id="8bbc9-353">Die Seite, die Sie während der Konfiguration ausgewählt haben, wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-353">The page that you chose during configuration is displayed.</span></span>

    ![Kanalregisterkarte ASPNET hochgeladen](../../assets/images/tab-images/channeltabaspnetuploaded.png)

# <a name="aspnet-core-mvc"></a>[<span data-ttu-id="8bbc9-355">ASP.NET Core Mvc</span><span class="sxs-lookup"><span data-stu-id="8bbc9-355">ASP.NET Core MVC</span></span>](#tab/aspnetcoremvc)

### <a name="create-a-custom-channel-or-group-tab-with-aspnet-core-mvc"></a><span data-ttu-id="8bbc9-356">Erstellen einer benutzerdefinierten Kanal- oder Gruppenregisterkarte mit ASP.NET Core MVC</span><span class="sxs-lookup"><span data-stu-id="8bbc9-356">Create a custom channel or group tab with ASP.NET Core MVC</span></span>

<span data-ttu-id="8bbc9-357">Sie können eine benutzerdefinierte Kanal- oder Gruppenregisterkarte mit C# und ASP.Net Core MVC erstellen.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-357">You can create a custom channel or group tab using C# and ASP.Net Core MVC.</span></span> <span data-ttu-id="8bbc9-358">[App Studio für Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) wird auch verwendet, um Das App-Manifest fertig zu stellen und die Registerkarte für Teams bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-358">[App Studio for Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) is also used to finalize your app manifest and deploy your tab to Teams.</span></span>

### <a name="prerequisites-for-custom-channel-or-group-tab"></a><span data-ttu-id="8bbc9-359">Voraussetzungen für benutzerdefinierte Kanal- oder Gruppenregisterkarten</span><span class="sxs-lookup"><span data-stu-id="8bbc9-359">Prerequisites for custom channel or group tab</span></span>

- <span data-ttu-id="8bbc9-360">Sie benötigen einen Microsoft 365 Mandanten und ein Team, für das das **Hochladen benutzerdefinierter Apps** zugelassen ist.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-360">You must have a Microsoft 365 tenant and a team configured with **Allow uploading custom apps** enabled.</span></span> <span data-ttu-id="8bbc9-361">Weitere Informationen finden Sie unter [Vorbereiten Ihres Office 365 Mandanten.](~/concepts/build-and-test/prepare-your-o365-tenant.md)</span><span class="sxs-lookup"><span data-stu-id="8bbc9-361">For more information, see [prepare your Office 365 tenant](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="8bbc9-362">Wenn Sie derzeit kein Microsoft 365 Konto haben, können Sie sich über das [Microsoft-Entwicklerprogramm](https://developer.microsoft.com/en-us/microsoft-365/dev-program)für ein kostenloses Abonnement registrieren.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-362">If you do not currently have a Microsoft 365 account, you can sign up for a free subscription through the [Microsoft Developer Program](https://developer.microsoft.com/en-us/microsoft-365/dev-program).</span></span> <span data-ttu-id="8bbc9-363">Das Abonnement bleibt aktiv, solange Sie es für die fortlaufende Entwicklung verwenden.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-363">The subscription remains active as long as you are using it for ongoing development.</span></span>

- <span data-ttu-id="8bbc9-364">Verwenden Sie App Studio, um Ihre Anwendung in Teams zu importieren.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-364">Use App Studio to import your application to Teams.</span></span> <span data-ttu-id="8bbc9-365">Um App Studio zu installieren, wählen Sie **Apps** ![ Store App in der ](~/assets/images/tab-images/storeApp.png) unteren linken Ecke der Teams App aus, und suchen Sie nach **App Studio.**</span><span class="sxs-lookup"><span data-stu-id="8bbc9-365">To install App Studio, select **Apps** ![Store App](~/assets/images/tab-images/storeApp.png) at the lower left corner of the Teams app, and search for **App Studio**.</span></span> <span data-ttu-id="8bbc9-366">Nachdem Sie die Kachel gefunden haben, wählen Sie sie aus, und wählen Sie im Popupdialogfeld **"Hinzufügen"** aus, um sie zu installieren.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-366">After you find the tile, select it and choose **Add** in the pop-up dialog box to install it.</span></span>

<span data-ttu-id="8bbc9-367">Darüber hinaus muss für dieses Projekt Folgendes in Ihrer Entwicklungsumgebung installiert sein:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-367">In addition, this project requires that you have the following installed in your development environment:</span></span>

- <span data-ttu-id="8bbc9-368">Die aktuelle Version der Visual Studio IDE, in der **die plattformübergreifende .NET CORE-Entwicklungsworkload** installiert ist.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-368">The current version of the Visual Studio IDE with the **.NET CORE cross-platform development** workload installed.</span></span> <span data-ttu-id="8bbc9-369">Wenn Sie noch nicht über Visual Studio verfügen, können Sie die neueste [Microsoft Visual Studio Community Version](https://visualstudio.microsoft.com/downloads) kostenlos herunterladen und installieren.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-369">If you do not already have Visual Studio, you can download and install the latest [Microsoft Visual Studio Community](https://visualstudio.microsoft.com/downloads) version for free.</span></span>

- <span data-ttu-id="8bbc9-370">Das [ngrok-Reverseproxytool.](https://ngrok.com)</span><span class="sxs-lookup"><span data-stu-id="8bbc9-370">The [ngrok](https://ngrok.com) reverse proxy tool.</span></span> <span data-ttu-id="8bbc9-371">Verwenden Sie ngrok, um einen Tunnel zu den öffentlich verfügbaren HTTPS-Endpunkten Ihres lokal ausgeführten Webservers zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-371">Use ngrok to create a tunnel to your locally running web server's publicly-available HTTPS endpoints.</span></span> <span data-ttu-id="8bbc9-372">Sie können [ngrok herunterladen.](https://ngrok.com/download)</span><span class="sxs-lookup"><span data-stu-id="8bbc9-372">You can [download ngrok](https://ngrok.com/download).</span></span>

### <a name="get-the-source-code"></a><span data-ttu-id="8bbc9-373">Abrufen des Quellcodes</span><span class="sxs-lookup"><span data-stu-id="8bbc9-373">Get the source code</span></span>

<span data-ttu-id="8bbc9-374">Erstellen Sie an einer Eingabeaufforderung ein neues Verzeichnis für Ihr Registerkartenprojekt.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-374">At a command prompt, create a new directory for your tab project.</span></span> <span data-ttu-id="8bbc9-375">Ein einfaches [Kanalgruppen-Registerkartenprojekt](https://github.com/OfficeDev/microsoft-teams-sample-tabs/tree/master/ChannelGroupTabMVC) wird bereitgestellt, um Ihnen den Einstieg zu erleichtern.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-375">A simple [Channel Group Tab](https://github.com/OfficeDev/microsoft-teams-sample-tabs/tree/master/ChannelGroupTabMVC) project is provided to get you started.</span></span> <span data-ttu-id="8bbc9-376">Klonen Sie das Beispiel-Repository mit dem folgenden Befehl in Ihr neues Verzeichnis:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-376">Clone the sample repository into your new directory using the following command:</span></span>

```bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

<span data-ttu-id="8bbc9-377">Alternativ können Sie den Quellcode abrufen, indem Sie den ZIP-Ordner herunterladen und die Dateien extrahieren.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-377">Alternately, you can retrieve the source code by downloading the zip folder and extracting the files.</span></span>

<span data-ttu-id="8bbc9-378">**So erstellen Sie das Registerkartenprojekt und führen es aus**</span><span class="sxs-lookup"><span data-stu-id="8bbc9-378">**To build and run the tab project**</span></span>

1. <span data-ttu-id="8bbc9-379">Nachdem Sie über den Quellcode verfügen, wechseln Sie zu Visual Studio, und wählen Sie **"Projekt oder Projektmappe öffnen"** aus.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-379">After you have the source code, go to Visual Studio and select **Open a project or solution**.</span></span>
1. <span data-ttu-id="8bbc9-380">Wechseln Sie zum Registerkartenanwendungsverzeichnis, und öffnen **Sie ChannelGroupTabMVC.sln**.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-380">Go to the tab application directory and open **ChannelGroupTabMVC.sln**.</span></span>
1. <span data-ttu-id="8bbc9-381">Drücken Sie **F5,** oder wählen Sie im Menü **"Debuggen"** die Option **"Debuggen starten"** aus, um die Anwendung zu erstellen und auszuführen.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-381">To build and run your application, press **F5** or choose **Start Debugging** from the **Debug** menu.</span></span>
1. <span data-ttu-id="8bbc9-382">Navigieren Sie in einem Browser zu den folgenden URLs, und stellen Sie sicher, dass die Anwendung ordnungsgemäß geladen wurde:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-382">In a browser, navigate to the following URLs and verify that the application loaded properly:</span></span>

    - `http://localhost:44360`
    - `http://localhost:44360/privacy`
    - `http://localhost:44360/tou`

### <a name="review-the-source-code"></a><span data-ttu-id="8bbc9-383">Überprüfen des Quellcodes</span><span class="sxs-lookup"><span data-stu-id="8bbc9-383">Review the source code</span></span>

#### <a name="startupcs"></a><span data-ttu-id="8bbc9-384">Startup.cs</span><span class="sxs-lookup"><span data-stu-id="8bbc9-384">Startup.cs</span></span>

<span data-ttu-id="8bbc9-385">Dieses Projekt wurde aus einer leeren Vorlage für ASP.NET Core 2.2-Webanwendung erstellt, wobei das Kontrollkästchen **"Erweitert – Für HTTPS konfigurieren"** beim Setup aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-385">This project was created from an ASP.NET Core 2.2 Web Application empty template with the **Advanced - Configure for HTTPS** check box selected at setup.</span></span> <span data-ttu-id="8bbc9-386">Die MVC-Dienste werden durch die Methode des Abhängigkeitsinjektionsframeworks `ConfigureServices()` registriert.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-386">The MVC services are registered by the dependency injection framework's `ConfigureServices()` method.</span></span> <span data-ttu-id="8bbc9-387">Darüber hinaus ermöglicht die leere Vorlage nicht standardmäßig die Bereitstellung statischer Inhalte, sodass die Middleware für statische Dateien der Methode mit dem folgenden Code hinzugefügt `Configure()` wird:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-387">Additionally, the empty template does not enable serving static content by default, so the static files middleware is added to the `Configure()` method using the following code:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
  {
    services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_2);
  }
public void Configure(IApplicationBuilder app)
  {
    app.UseStaticFiles();
    app.UseMvc();
  }
```

#### <a name="wwwroot-folder"></a><span data-ttu-id="8bbc9-388">Wwwroot-Ordner</span><span class="sxs-lookup"><span data-stu-id="8bbc9-388">wwwroot folder</span></span>

<span data-ttu-id="8bbc9-389">In ASP.NET Core sucht die Anwendung im Webstammordner nach statischen Dateien.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-389">In ASP.NET Core, the web root folder is where the application looks for static files.</span></span>

#### <a name="appmanifest-folder"></a><span data-ttu-id="8bbc9-390">AppManifest-Ordner</span><span class="sxs-lookup"><span data-stu-id="8bbc9-390">AppManifest folder</span></span>

<span data-ttu-id="8bbc9-391">Dieser Ordner enthält die folgenden erforderlichen App-Paketdateien:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-391">This folder contains the following required app package files:</span></span>

- <span data-ttu-id="8bbc9-392">Ein **Vollfarbsymbol** mit einer Auflösung von 192 x 192 Pixeln.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-392">A **full color icon** measuring 192 x 192 pixels.</span></span>
- <span data-ttu-id="8bbc9-393">Ein **transparentes Gliederungssymbol** mit einer Auflösung von 32 x 32 Pixeln.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-393">A **transparent outline icon** measuring 32 x 32 pixels.</span></span>
- <span data-ttu-id="8bbc9-394">Ein **manifest.jsfür** die Datei, die die Attribute Ihrer App angibt.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-394">A **manifest.json** file that specifies the attributes of your app.</span></span>

<span data-ttu-id="8bbc9-395">Diese Dateien müssen in einem App-Paket gezippt werden, um Ihre Registerkarte in Teams hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-395">These files need to be zipped in an app package for use in uploading your tab to Teams.</span></span>

#### <a name="csproj"></a><span data-ttu-id="8bbc9-396">CSPROJ</span><span class="sxs-lookup"><span data-stu-id="8bbc9-396">.csproj</span></span>

<span data-ttu-id="8bbc9-397">Klicken Sie im Fenster Visual Studio Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie **"Bearbeiten Project Datei"** aus.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-397">In the Visual Studio Solution Explorer window, right-click on the project and select **Edit Project File**.</span></span> <span data-ttu-id="8bbc9-398">Am Ende der Datei wird der folgende Code angezeigt, der Ihren ZIP-Ordner erstellt und aktualisiert, wenn die Anwendung erstellt wird:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-398">At the end of the file you see the following code that creates and updates your zip folder when the application builds:</span></span>

```xml
<PropertyGroup>
    <PostBuildEvent>powershell.exe Compress-Archive -Path \"$(ProjectDir)AppManifest\*\" -DestinationPath \"$(TargetDir)tab.zip\" -Force</PostBuildEvent>
  </PropertyGroup>

  <ItemGroup>
    <EmbeddedResource Include="AppManifest\icon-outline.png">
      <CopyToOutputDirectory>Always</CopyToOutputDirectory>
    </EmbeddedResource>
    <EmbeddedResource Include="AppManifest\icon-color.png">
      <CopyToOutputDirectory>Always</CopyToOutputDirectory>
    </EmbeddedResource>
    <EmbeddedResource Include="AppManifest\manifest.json">
      <CopyToOutputDirectory>Always</CopyToOutputDirectory>
    </EmbeddedResource>
  </ItemGroup>
```

#### <a name="models"></a><span data-ttu-id="8bbc9-399">Modelle</span><span class="sxs-lookup"><span data-stu-id="8bbc9-399">Models</span></span>

<span data-ttu-id="8bbc9-400">**ChannelGroup.cs** stellt ein Message-Objekt und Methoden vor, die während der Konfiguration von den Controllern aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-400">**ChannelGroup.cs** presents a Message object and methods that will be called from the controllers during configuration.</span></span>

#### <a name="views"></a><span data-ttu-id="8bbc9-401">Ansichten</span><span class="sxs-lookup"><span data-stu-id="8bbc9-401">Views</span></span>

<span data-ttu-id="8bbc9-402">Dies sind die verschiedenen Ansichten in ASP.NET Core MVC:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-402">These are the different views in ASP.NET Core MVC:</span></span>

* <span data-ttu-id="8bbc9-403">Start: ASP.NET Core behandelt Dateien mit dem Namen **Index** als Standard- oder Startseite für die Website.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-403">Home: ASP.NET Core treats files called **Index** as the default or home page for the site.</span></span> <span data-ttu-id="8bbc9-404">Wenn Ihre Browser-URL auf den Stamm der Website zeigt, wird **Index.cshtml** als Startseite für Ihre Anwendung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-404">When your browser URL points to the root of the site, **Index.cshtml** will be displayed as the home page for your application.</span></span>

* <span data-ttu-id="8bbc9-405">Freigegeben: Das Partielle Ansichtsmarkup **_Layout.cshtml** enthält die allgemeine Seitenstruktur der Anwendung und freigegebene visuelle Elemente.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-405">Shared: The partial view markup **_Layout.cshtml** contains the application's overall page structure and shared visual elements.</span></span> <span data-ttu-id="8bbc9-406">Außerdem wird auf die Teams Bibliothek verwiesen.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-406">It will also reference the Teams Library.</span></span>

#### <a name="controllers"></a><span data-ttu-id="8bbc9-407">Controller</span><span class="sxs-lookup"><span data-stu-id="8bbc9-407">Controllers</span></span>

<span data-ttu-id="8bbc9-408">Die Controller verwenden die `ViewBag` Eigenschaft, um Werte dynamisch in die Ansichten zu übertragen.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-408">The controllers use the `ViewBag` property to transfer values dynamically to the views.</span></span>

[!INCLUDE [dotnet-ngrok-intro](~/includes/tabs/dotnet-ngrok-intro.md)]

* <span data-ttu-id="8bbc9-409">Öffnen Sie eine Eingabeaufforderung im Stammverzeichnis des Projekts, und führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="8bbc9-409">Open a command prompt in the root of your project directory and run the following command:</span></span>

    ```bash
    ngrok http https://localhost:443560 -host-header="localhost:44360"
    ```

* <span data-ttu-id="8bbc9-410">Ngrok lauscht auf Anforderungen aus dem Internet und leitet sie an Ihre Anwendung weiter, wenn sie auf Port 44355 ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-410">Ngrok will listen to requests from the internet and will route them to your application when it is running on port 44355.</span></span> <span data-ttu-id="8bbc9-411">Es sollte etwa so `https://y8rCgT2b.ngrok.io/` aussehen, wo **y8rCgT2b** durch Ihre alphangrok-numerische HTTPS-URL ersetzt wird.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-411">It should resemble `https://y8rCgT2b.ngrok.io/` where **y8rCgT2b** is replaced by your ngrok alpha-numeric HTTPS URL.</span></span>

* <span data-ttu-id="8bbc9-412">Stellen Sie sicher, dass die Eingabeaufforderung mit ngrok ausgeführt wird, und notieren Sie sich die URL.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-412">Ensure that you keep the command prompt with ngrok running and make a note of the URL.</span></span>

### <a name="update-your-application"></a><span data-ttu-id="8bbc9-413">Aktualisieren Der Anwendung</span><span class="sxs-lookup"><span data-stu-id="8bbc9-413">Update your application</span></span>

<span data-ttu-id="8bbc9-414">Innerhalb von **Tab.cshtml** zeigt die Anwendung dem Benutzer zwei Optionsschaltflächen zum Anzeigen der Registerkarte mit einem roten oder grauen Symbol an.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-414">Within **Tab.cshtml** the application presents the user with two option buttons for displaying the tab with either a red or gray icon.</span></span> <span data-ttu-id="8bbc9-415">Durch Auswählen der Schaltfläche **"Grau auswählen"** oder **"Rot auswählen"** wird die Schaltfläche "Speichern" auf der Konfigurationsseite ausgelöst `saveGray()` `saveRed()` `settings.setValidityState(true)` bzw. festgelegt. </span><span class="sxs-lookup"><span data-stu-id="8bbc9-415">Choosing the **Select Gray** or **Select Red** button, triggers `saveGray()` or `saveRed()`, respectively, sets `settings.setValidityState(true)`, and enables the **Save** button on the configuration page.</span></span> <span data-ttu-id="8bbc9-416">Dieser Code teilt Teams mit, dass Sie die Konfigurationsanforderungen erfüllt haben und die Installation fortgesetzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-416">This code lets Teams know that you have completed the configuration requirements and the installation can proceed.</span></span> <span data-ttu-id="8bbc9-417">Beim Speichern werden die Parameter `settings.setSettings` von festgelegt.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-417">On save, the parameters of `settings.setSettings` are set.</span></span> <span data-ttu-id="8bbc9-418">Schließlich `saveEvent.notifySuccess()` wird aufgerufen, um anzugeben, dass die Inhalts-URL erfolgreich aufgelöst wurde.</span><span class="sxs-lookup"><span data-stu-id="8bbc9-418">Finally, `saveEvent.notifySuccess()` is called to indicate that the content URL has been successfully resolved.</span></span>

[!INCLUDE [dotnet-update-app](~/includes/tabs/dotnet-update-chan-grp-app.md)]

---

## <a name="see-also"></a><span data-ttu-id="8bbc9-419">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="8bbc9-419">See also</span></span>

* [<span data-ttu-id="8bbc9-420">registerkarten Teams</span><span class="sxs-lookup"><span data-stu-id="8bbc9-420">Teams tabs</span></span>](~/tabs/what-are-tabs.md)
* [<span data-ttu-id="8bbc9-421">Erstellen einer persönlichen Registerkarte</span><span class="sxs-lookup"><span data-stu-id="8bbc9-421">Create a personal tab</span></span>](~/tabs/how-to/create-personal-tab.md)
* [<span data-ttu-id="8bbc9-422">Registerkarten auf mobilen Geräten</span><span class="sxs-lookup"><span data-stu-id="8bbc9-422">Tabs on mobile</span></span>](~/tabs/design/tabs-mobile.md)
* [<span data-ttu-id="8bbc9-423">Erstellen von Registerkarten mit adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="8bbc9-423">Build tabs with Adaptive Cards</span></span>](~/tabs/how-to/build-adaptive-card-tabs.md)

## <a name="next-step"></a><span data-ttu-id="8bbc9-424">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="8bbc9-424">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8bbc9-425">Erstellen einer Inhaltsseite</span><span class="sxs-lookup"><span data-stu-id="8bbc9-425">Create a content page</span></span>](~/tabs/how-to/create-tab-pages/content-page.md)
