---
title: Erstellen von Apps mit dem Microsoft Teams-Toolkit und Visual Studio Code
description: Erste Schritte beim Erstellen von großartigen benutzerdefinierten Apps direkt in Visual Studio Code mit dem Microsoft Teams-Toolkit
keywords: Teams Visual Studio Code Toolkit
localization_priority: Normal
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: b2cfab5cb2ea2d727608b6ea3bbfec3271b2b039
ms.sourcegitcommit: 14409950307b135265c8582408be5277b35131dd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2021
ms.locfileid: "52994140"
---
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio-code"></a><span data-ttu-id="df8cf-104">Erstellen von Apps mit dem Teams-Toolkit und Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="df8cf-104">Build apps with the Teams Toolkit and Visual Studio Code</span></span>

<span data-ttu-id="df8cf-105">Das Teams-Toolkit für Visual Studio Code unterstützt Entwickler beim Erstellen und Bereitstellen von Teams-Apps mit integrierter Identität, Zugriff auf Cloudspeicher, Daten aus Microsoft Graph und anderen Diensten in Azure und M365 mit einem Nullkonfigurationsansatz für die Entwicklerumgebung.</span><span class="sxs-lookup"><span data-stu-id="df8cf-105">The Teams Toolkit for Visual Studio Code helps developers create and deploy Teams apps with integrated identity, access to cloud storage, data from Microsoft Graph, and other services in Azure and M365 with a “zero-configuration” approach to the developer experience.</span></span>  

<span data-ttu-id="df8cf-106">Sie können das Toolkit auch mit Visual Studio oder als CLI (genannt `teamsfx` ) verwenden.</span><span class="sxs-lookup"><span data-stu-id="df8cf-106">You also can use the toolkit with Visual Studio or as a CLI (called `teamsfx`).</span></span>

## <a name="install-the-teams-toolkit-for-visual-studio-code"></a><span data-ttu-id="df8cf-107">Installieren des Teams-Toolkits für Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="df8cf-107">Install the Teams Toolkit for Visual Studio Code</span></span>

1. <span data-ttu-id="df8cf-108">Öffnen Sie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="df8cf-108">Open Visual Studio Code.</span></span>
1. <span data-ttu-id="df8cf-109">Wählen Sie die Erweiterungsansicht (**STRG+UMSCHALT+X**  /  **⌘⇧-X** oder **Ansicht > Erweiterungen) aus.**</span><span class="sxs-lookup"><span data-stu-id="df8cf-109">Select the Extensions view (**Ctrl+Shift+X** / **⌘⇧-X** or **View > Extensions**).</span></span>
1. <span data-ttu-id="df8cf-110">Geben Sie im Suchfeld das _Teams-Toolkit_ ein.</span><span class="sxs-lookup"><span data-stu-id="df8cf-110">In the search box, enter _Teams Toolkit_.</span></span>
1. <span data-ttu-id="df8cf-111">Klicken Sie auf die grüne Installationsschaltfläche neben dem Teams-Toolkit.</span><span class="sxs-lookup"><span data-stu-id="df8cf-111">Select on the green install button next to the Teams Toolkit.</span></span>

<span data-ttu-id="df8cf-112">Sie finden das Teams-Toolkit auch im [Visual Studio Code Marketplace.](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension)</span><span class="sxs-lookup"><span data-stu-id="df8cf-112">You also can find the Teams Toolkit on the [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension).</span></span>

<span data-ttu-id="df8cf-113">Die folgenden Tools werden bei Bedarf von der Visual Studio Code-Erweiterung installiert.</span><span class="sxs-lookup"><span data-stu-id="df8cf-113">The following tools are installed by the Visual Studio Code extension when they are needed.</span></span> <span data-ttu-id="df8cf-114">Wenn sie bereits installiert ist, wird stattdessen die installierte Version verwendet.</span><span class="sxs-lookup"><span data-stu-id="df8cf-114">If already installed, the installed version is used instead.</span></span> <span data-ttu-id="df8cf-115">Wenn Sie Linux (einschließlich WSL) verwenden, müssen Sie diese Tools vor der Verwendung installieren:</span><span class="sxs-lookup"><span data-stu-id="df8cf-115">If using Linux (including WSL), you must install these tools before use:</span></span>

- [<span data-ttu-id="df8cf-116">Azure Functions Core Tools</span><span class="sxs-lookup"><span data-stu-id="df8cf-116">Azure Functions Core Tools</span></span>](/azure/azure-functions/functions-run-local)

    <span data-ttu-id="df8cf-117">Azure Functions Core Tools wird verwendet, um alle Back-End-Komponenten während einer lokalen Debugausführung lokal auszuführen, einschließlich der Authentifizierungshilfsprogramme, die beim Ausführen Ihrer Dienste in Azure erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="df8cf-117">Azure Functions Core Tools is used to run any backend components locally during a local debug run, including the authentication helpers required when running your services in Azure.</span></span> <span data-ttu-id="df8cf-118">Sie wird mithilfe des npm im Projektverzeichnis `devDependencies` installiert.</span><span class="sxs-lookup"><span data-stu-id="df8cf-118">It is installed within the project directory using the npm `devDependencies`.</span></span>

- [<span data-ttu-id="df8cf-119">.NET SDK</span><span class="sxs-lookup"><span data-stu-id="df8cf-119">.NET SDK</span></span>](/dotnet/core/install/)

    <span data-ttu-id="df8cf-120">Das .NET SDK wird verwendet, um angepasste Bindungen für lokales Debuggen und Azure Functions-App-Bereitstellungen zu installieren.</span><span class="sxs-lookup"><span data-stu-id="df8cf-120">The .NET SDK is used to install customized bindings for local debugging and Azure Functions app deployments.</span></span> <span data-ttu-id="df8cf-121">Wenn Sie das .NET 3.1- oder höher-SDK nicht global installiert haben, wird die portierbare Version installiert.</span><span class="sxs-lookup"><span data-stu-id="df8cf-121">If you have not installed the .NET 3.1 or later SDK globally, the portable version is installed.</span></span>

- [<span data-ttu-id="df8cf-122">ngrok</span><span class="sxs-lookup"><span data-stu-id="df8cf-122">ngrok</span></span>](https://ngrok.com/download)

    <span data-ttu-id="df8cf-123">Einige Teams-App-Features (Unterhaltungsbots, Messaging-Erweiterungen und eingehende Webhooks) erfordern eingehende Verbindungen.</span><span class="sxs-lookup"><span data-stu-id="df8cf-123">Some Teams app features (conversational bots, messaging extensions, and incoming webhooks) require inbound connections.</span></span>  <span data-ttu-id="df8cf-124">Sie müssen Ihr Entwicklungssystem über einen Tunnel für Teams verfügbar machen.</span><span class="sxs-lookup"><span data-stu-id="df8cf-124">You need to expose your development system to Teams through a tunnel.</span></span> <span data-ttu-id="df8cf-125">Für Apps, die nur Registerkarten enthalten, ist kein Tunnel erforderlich.</span><span class="sxs-lookup"><span data-stu-id="df8cf-125">A tunnel is not required for apps that only include tabs.</span></span>  <span data-ttu-id="df8cf-126">Dieses Paket wird im Projektverzeichnis installiert (mit `devDependencies` npm).</span><span class="sxs-lookup"><span data-stu-id="df8cf-126">This package is installed within the project directory (using npm `devDependencies`).</span></span>

## <a name="use-the-teams-toolkit-for-visual-studio-code"></a><span data-ttu-id="df8cf-127">Verwenden des Teams-Toolkits für Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="df8cf-127">Use the Teams Toolkit for Visual Studio Code</span></span>

- [<span data-ttu-id="df8cf-128">Einrichten eines neuen Projekts</span><span class="sxs-lookup"><span data-stu-id="df8cf-128">Set up a new project</span></span>](#set-up-a-new-teams-project)
- [<span data-ttu-id="df8cf-129">Konfigurieren Sie die App</span><span class="sxs-lookup"><span data-stu-id="df8cf-129">Configure your app</span></span>](#configure-your-app)
- [<span data-ttu-id="df8cf-130">Lokales Ausführen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="df8cf-130">Run your app locally</span></span>](#install-and-run-your-app-locally)
- [<span data-ttu-id="df8cf-131">Veröffentlichen eigener Apps</span><span class="sxs-lookup"><span data-stu-id="df8cf-131">Publish your app</span></span>](#publish-your-app-to-teams)

## <a name="set-up-a-new-teams-project"></a><span data-ttu-id="df8cf-132">Einrichten eines neuen Teams-Projekts</span><span class="sxs-lookup"><span data-stu-id="df8cf-132">Set up a new Teams project</span></span>

<span data-ttu-id="df8cf-133">Das Teams-Toolkit kann React-Apps erstellen, die in Azure- oder SPFx-Webparts gehostet werden, die in Ihrer M365 SharePoint-Umgebung gehostet werden.</span><span class="sxs-lookup"><span data-stu-id="df8cf-133">The Teams Toolkit can create React apps that are hosted in Azure or SPFx web parts that are hosted on your M365 SharePoint environment.</span></span> <span data-ttu-id="df8cf-134">So erstellen Sie eine neue React-App, die in Azure gehostet werden soll:</span><span class="sxs-lookup"><span data-stu-id="df8cf-134">To create a new React app to be hosted on Azure:</span></span>

1. <span data-ttu-id="df8cf-135">Öffnen Sie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="df8cf-135">Open Visual Studio code.</span></span>
1. <span data-ttu-id="df8cf-136">Öffnen Sie das Microsoft Teams-Toolkit, indem Sie auf das Microsoft Teams-Symbol in der Randleiste klicken:</span><span class="sxs-lookup"><span data-stu-id="df8cf-136">Open the Teams Toolkit by selecting the Teams icon in the sidebar:</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="Das Microsoft Teams-Symbol in der Visual Studio Code-Randleiste.":::

1. <span data-ttu-id="df8cf-138">Klicken Sie auf **Neues Projekt erstellen**.</span><span class="sxs-lookup"><span data-stu-id="df8cf-138">Select **Create New Project**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project.png" alt-text="Ort des Links „Neues Projekt erstellen“ in der Randleiste des Microsoft Teams-Toolkits.":::

1. <span data-ttu-id="df8cf-140">Wählen Sie **Neue Microsoft Teams-App erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="df8cf-140">Select **Create a new Teams app**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-new-project-intro.png" alt-text="Starten des Assistenten für „Neues Projekt erstellen“":::

1. <span data-ttu-id="df8cf-142">Im Schritt **"Funktionen auswählen"** ist die **Registerkartenfunktion** bereits ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="df8cf-142">On the **Select capabilities** step, the **Tab** capability is already selected.</span></span> <span data-ttu-id="df8cf-143">Sie können optional auch **Bot-** und **Messaging-Erweiterung** auswählen.</span><span class="sxs-lookup"><span data-stu-id="df8cf-143">You can also optionally select **Bot** and **Messaging Extension**.</span></span>  <span data-ttu-id="df8cf-144">Drücken Sie **OK**.</span><span class="sxs-lookup"><span data-stu-id="df8cf-144">Press **OK**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-capabilities.png" alt-text="Screenshot, der zeigt, wie Ihrer neuen App Funktionen hinzufügt werden können.":::

1. <span data-ttu-id="df8cf-146">Wählen Sie im Schritt **Frontend-Hostingtyp** die Option **Azure** aus.</span><span class="sxs-lookup"><span data-stu-id="df8cf-146">On the **Frontend hosting type** step, select **Azure**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-hosting.png" alt-text="Screenshot, der zeigt, wie das Hosting für Ihre neue App ausgewählt wird.":::

1. <span data-ttu-id="df8cf-148">Wählen Sie optional im Schritt **"Cloudressourcen"** Cloudressourcen aus, die Ihre Anwendung verwendet.</span><span class="sxs-lookup"><span data-stu-id="df8cf-148">Optionally, on the **Cloud resources** step, select cloud resources that your application uses.</span></span> <span data-ttu-id="df8cf-149">Sie können den CRUD-Zugriff (Erstellen, Lesen, Aktualisieren und Löschen) auf eine SQL-Tabelle oder eine API auswählen:</span><span class="sxs-lookup"><span data-stu-id="df8cf-149">You can select CRUD (create, read, update, and delete) access to a SQL table or an API:</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-cloud-resources.png" alt-text="Screenshot, der zeigt, wie Cloudressourcen für Ihre neue App hinzugefügt werden.":::

1. <span data-ttu-id="df8cf-151">Im Schritt **"Programmiersprache"** können Sie **JavaScript** oder **TypeScript** auswählen:</span><span class="sxs-lookup"><span data-stu-id="df8cf-151">On the **Programming Language** step, you can choose **JavaScript** or **TypeScript**:</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-programming-languages.png" alt-text="Screenshot, der zeigt, wie die Programmiersprache ausgewählt wird.":::

1. <span data-ttu-id="df8cf-153">Wählen Sie einen Arbeitsbereichsordner aus.</span><span class="sxs-lookup"><span data-stu-id="df8cf-153">Select a workspace folder.</span></span> <span data-ttu-id="df8cf-154">Ein Ordner wird in Ihrem Arbeitsbereichsordner für das Projekt erstellt, das Sie erstellen.</span><span class="sxs-lookup"><span data-stu-id="df8cf-154">A folder is created within your workspace folder for the project you are creating.</span></span>

1. <span data-ttu-id="df8cf-155">Geben Sie einen passenden Namen für Ihre App ein, wie z. B. `helloworld`.</span><span class="sxs-lookup"><span data-stu-id="df8cf-155">Enter a suitable name for your app, like `helloworld`.</span></span> <span data-ttu-id="df8cf-156">Der Name der App darf nur aus alphanumerischen Zeichen bestehen.</span><span class="sxs-lookup"><span data-stu-id="df8cf-156">The name of the app must consist only of alphanumeric characters.</span></span>  <span data-ttu-id="df8cf-157">Drücken Sie die **EINGABETASTE**, um fortzufahren.</span><span class="sxs-lookup"><span data-stu-id="df8cf-157">Press **Enter** to continue.</span></span>

<span data-ttu-id="df8cf-158">Ihre Teams-App wird innerhalb weniger Sekunden erstellt.</span><span class="sxs-lookup"><span data-stu-id="df8cf-158">Your Teams app is created within a few seconds.</span></span> <span data-ttu-id="df8cf-159">Die Gerüst-App enthält Code für die Behandlung des einmaligen Anmeldens mit Azure Active Directory und den Zugriff auf Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="df8cf-159">The scaffolded app contains code to handle single sign-on with Azure Active Directory and access to the Microsoft Graph.</span></span>  <span data-ttu-id="df8cf-160">Wenn Sie Azure-Ressourcen ausgewählt haben, ist auch der Code für diese Ressourcen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="df8cf-160">If you selected Azure resources, then the code for those resources is also available.</span></span>

<span data-ttu-id="df8cf-161">Eine exemplarische Vorgehensweise zum SPFx-Erstellungs- und -Veröffentlichungsprozess finden Sie im [SPFx-Lernprogramm.](../get-started/first-app-spfx.md)</span><span class="sxs-lookup"><span data-stu-id="df8cf-161">For a walk-through of the SPFx creation and publication process, see the [SPFx tutorial](../get-started/first-app-spfx.md).</span></span>

## <a name="configure-your-app"></a><span data-ttu-id="df8cf-162">Konfigurieren Sie die App</span><span class="sxs-lookup"><span data-stu-id="df8cf-162">Configure your app</span></span>

<span data-ttu-id="df8cf-163">Im Kern umfasst die Teams-App drei Komponenten:</span><span class="sxs-lookup"><span data-stu-id="df8cf-163">At its core, the Teams app embraces three components:</span></span>

  1. <span data-ttu-id="df8cf-164">Der Microsoft Teams-Client (Web, Desktop oder Mobil), auf dem Benutzer mit Ihrer App interagieren.</span><span class="sxs-lookup"><span data-stu-id="df8cf-164">The Microsoft Teams client (web, desktop or mobile) where users interact with your app.</span></span>
  1. <span data-ttu-id="df8cf-165">Ein Server, der auf Anforderungen für Inhalte reagiert, die in Teams angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="df8cf-165">A server that responds to requests for content that is displayed in Teams.</span></span> <span data-ttu-id="df8cf-166">Beispiel: HTML-Registerkarteninhalt oder eine adaptive Bot-Karte.</span><span class="sxs-lookup"><span data-stu-id="df8cf-166">For example, HTML tab content or a bot Adaptive Card.</span></span>
  1. <span data-ttu-id="df8cf-167">Ein Teams-App-Paket besteht aus drei Dateien:</span><span class="sxs-lookup"><span data-stu-id="df8cf-167">A Teams app package consists of three files:</span></span>

      > [!div class="checklist"]
      >
      > - <span data-ttu-id="df8cf-168">Die manifest.jsaktiviert.</span><span class="sxs-lookup"><span data-stu-id="df8cf-168">The manifest.json.</span></span>
      > - <span data-ttu-id="df8cf-169">Ein [Farbsymbol](../resources/schema/manifest-schema.md#icons) für Ihre App, das im öffentlichen App- oder Organisations-App-Katalog angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="df8cf-169">A [color icon](../resources/schema/manifest-schema.md#icons) for your app to display in the public or organization app catalog.</span></span>
      > - <span data-ttu-id="df8cf-170">Ein [Gliederungssymbol](../resources/schema/manifest-schema.md#icons) für die Anzeige auf der Teams-Aktivitätsleiste.</span><span class="sxs-lookup"><span data-stu-id="df8cf-170">An [outline icon](../resources/schema/manifest-schema.md#icons) for display on the Teams activity bar.</span></span>

<span data-ttu-id="df8cf-171">Das Manifest und die Symbole werden im `.fx` Ordner Ihres Projekts gespeichert, bevor sie in Teams hochgeladen werden.</span><span class="sxs-lookup"><span data-stu-id="df8cf-171">The manifest and icons are stored in the `.fx` folder of your project prior to being uploaded to Teams.</span></span> <span data-ttu-id="df8cf-172">Wenn eine App installiert ist, analysiert der Teams-Client die Manifestdatei, um die erforderlichen Informationen wie den Namen Ihrer App und die URL zu ermitteln, unter der sich die Dienste befinden.</span><span class="sxs-lookup"><span data-stu-id="df8cf-172">When an app is installed, the Teams client parses the manifest file to determine needed information like the name of your app and the URL where the services are located.</span></span>

1. <span data-ttu-id="df8cf-173">Navigieren Sie zum Konfigurieren Ihrer App zur Registerkarte **"Teams-Toolkit"** in Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="df8cf-173">To configure your app, navigate to the **Teams Toolkit** tab in Visual Studio Code.</span></span>
1. <span data-ttu-id="df8cf-174">Wählen Sie im Abschnitt **"Projekt"** den **Manifest-Editor** aus.</span><span class="sxs-lookup"><span data-stu-id="df8cf-174">Select **Manifest Editor** in the **Project** section.</span></span>

<span data-ttu-id="df8cf-175">Durch das Bearbeiten der Felder auf der Seite "App-Details" wird der Inhalt der manifest.jsauf der Datei aktualisiert, die letztendlich als Teil des App-Pakets ausgeliefert wird.</span><span class="sxs-lookup"><span data-stu-id="df8cf-175">Editing the fields in the App details page updates the contents of the manifest.json file that is ultimately shipped as part of the app package.</span></span>

## <a name="install-and-run-your-app-locally"></a><span data-ttu-id="df8cf-176">Lokales Installieren und Ausführen der App</span><span class="sxs-lookup"><span data-stu-id="df8cf-176">Install and run your app locally</span></span>

<span data-ttu-id="df8cf-177">So erstellen Sie Ihre App und führen sie lokal aus:</span><span class="sxs-lookup"><span data-stu-id="df8cf-177">To build and run your app locally:</span></span>

1. <span data-ttu-id="df8cf-178">Drücken Sie in Visual Studio Code **F5**, um die Anwendung im Debugmodus auszuführen.</span><span class="sxs-lookup"><span data-stu-id="df8cf-178">From Visual Studio Code, press **F5** to run your application in debug mode.</span></span>

   > <span data-ttu-id="df8cf-179">Wenn Sie die App zum ersten Mal ausführen, werden alle Abhängigkeiten heruntergeladen und die App wird erstellt.</span><span class="sxs-lookup"><span data-stu-id="df8cf-179">When you run the app for the first time, all dependencies are downloaded and the app is built.</span></span>  <span data-ttu-id="df8cf-180">Wenn die Erstellung abgeschlossen ist, wird automatisch ein Browserfenster geöffnet.</span><span class="sxs-lookup"><span data-stu-id="df8cf-180">A browser window automatically opens when the build is complete.</span></span>  <span data-ttu-id="df8cf-181">Dies kann 3 bis 5 Minuten dauern.</span><span class="sxs-lookup"><span data-stu-id="df8cf-181">This can take 3-5 minutes to complete.</span></span>

   <span data-ttu-id="df8cf-182">Das Toolkit fordert Sie auf, bei Bedarf ein lokales Zertifikat zu installieren.</span><span class="sxs-lookup"><span data-stu-id="df8cf-182">The toolkit prompts you to install a local certificate if required.</span></span> <span data-ttu-id="df8cf-183">Mit diesem Zertifikat kann Microsoft Teams Ihre Anwendung von `https://localhost` laden.</span><span class="sxs-lookup"><span data-stu-id="df8cf-183">This certificate allows Teams to load your application from `https://localhost`.</span></span> <span data-ttu-id="df8cf-184">Wählen Sie "Ja" aus, wenn das folgende Dialogfenster angezeigt wird:</span><span class="sxs-lookup"><span data-stu-id="df8cf-184">Select yes when the following dialog appears:</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/ssl-prompt.png" alt-text="Screenshot mit Dialogfenster zum Installieren eines SSL-Zertifikats, damit Microsoft Teams Ihre Anwendung von localhost laden kann.":::

1. <span data-ttu-id="df8cf-186">Ihr Webbrowser wird gestartet, um die Anwendung auszuführen.</span><span class="sxs-lookup"><span data-stu-id="df8cf-186">Your web browser is started to run the application.</span></span> <span data-ttu-id="df8cf-187">Wenn Sie zum Öffnen von Microsoft Teams aufgefordert werden, wählen Sie „Abbrechen“ aus, um im Browser zu verbleiben.</span><span class="sxs-lookup"><span data-stu-id="df8cf-187">If prompted to open Microsoft Teams, select Cancel to remain within the browser.</span></span> <span data-ttu-id="df8cf-188">Möglicherweise werden Sie auch zu anderen Zeiten aufgefordert, zur Teams-Anwendung zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="df8cf-188">You may also be prompted to switch to the Teams application at other times.</span></span> <span data-ttu-id="df8cf-189">Wählen Sie in diesem Fall die Web-App aus.</span><span class="sxs-lookup"><span data-stu-id="df8cf-189">Select the web app when this happens.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/launch-web-browser-and-pick-webapp.png" alt-text="Screenshot, der zeigt, wie die Web-Version von Microsoft Teams beim Start ausgewählt wird.":::

1. <span data-ttu-id="df8cf-191">Möglicherweise werden Sie aufgefordert, sich anzumelden.</span><span class="sxs-lookup"><span data-stu-id="df8cf-191">You may be prompted to sign in.</span></span> <span data-ttu-id="df8cf-192">Melden Sie sich in diesem Fall mit Ihrem M365-Konto an.</span><span class="sxs-lookup"><span data-stu-id="df8cf-192">If so, sign in with your M365 account.</span></span>
1. <span data-ttu-id="df8cf-193">Wenn Sie aufgefordert werden, die App in Microsoft Teams zu installieren, drücken Sie **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="df8cf-193">When prompted to install the app onto Teams, press **Add**.</span></span>

<span data-ttu-id="df8cf-194">Sowohl das Back-End als auch der Frontend sind in den Visual Studio Code-Debugger eingebunden.</span><span class="sxs-lookup"><span data-stu-id="df8cf-194">Both the backend and frontend are hooked into the Visual Studio Code debugger.</span></span>  <span data-ttu-id="df8cf-195">Auf diese Weise können Sie haltepunkte an einer beliebigen Stelle im Code festlegen und den Status überprüfen.</span><span class="sxs-lookup"><span data-stu-id="df8cf-195">This allows you to set breakpoints anywhere in your code and inspect state.</span></span>  <span data-ttu-id="df8cf-196">Sie können auch alle Front-End-Debugtools (z. B. die React Developer Tools) im Browser verwenden.</span><span class="sxs-lookup"><span data-stu-id="df8cf-196">You can also use any frontend debugging tools (such as the React Developer Tools) within the browser.</span></span>  <span data-ttu-id="df8cf-197">Weitere Informationen zum Debuggen in Visual Studio Code können Sie [in der Dokumentation nachlesen.](https://code.visualstudio.com/Docs/editor/debugging)</span><span class="sxs-lookup"><span data-stu-id="df8cf-197">For more information about debugging in Visual Studio Code, review [the documentation](https://code.visualstudio.com/Docs/editor/debugging).</span></span>

## <a name="publish-your-app-to-teams"></a><span data-ttu-id="df8cf-198">Veröffentlichen Ihrer App in Teams</span><span class="sxs-lookup"><span data-stu-id="df8cf-198">Publish your app to Teams</span></span>

<span data-ttu-id="df8cf-199">Bevor sie von anderen Personen verwendet werden kann, müssen Sie Ihre App im Entwicklerportal für Teams veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="df8cf-199">Before it can be used by other people, you must publish your app to the Developer Portal for Teams.</span></span>

1. <span data-ttu-id="df8cf-200">Navigieren Sie zum Veröffentlichen Ihrer App zur Registerkarte **"Teams-Toolkit"** in Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="df8cf-200">To publish your app, navigate to the **Teams Toolkit** tab in Visual Studio Code.</span></span>
1. <span data-ttu-id="df8cf-201">Wählen Sie im **Abschnitt Project** in Teams **veröffentlichen** aus.</span><span class="sxs-lookup"><span data-stu-id="df8cf-201">Select **Publish to Teams** in the **Project** section.</span></span>

<span data-ttu-id="df8cf-202">Wenn Sie Azure-Hosting verwenden, müssen Sie die Cloud bereitgestellt und bereitgestellt haben.</span><span class="sxs-lookup"><span data-stu-id="df8cf-202">If using Azure hosting, you must have provisioned and deployed to the cloud.</span></span> <span data-ttu-id="df8cf-203">Eine exemplarische Vorgehensweise zum SPFx Veröffentlichungsprozess finden Sie im [SPFx Lernprogramm.](../get-started/first-app-spfx.md)</span><span class="sxs-lookup"><span data-stu-id="df8cf-203">For a walk-through of the SPFx publication process, see the [SPFx tutorial](../get-started/first-app-spfx.md).</span></span>

## <a name="next-step"></a><span data-ttu-id="df8cf-204">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="df8cf-204">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="df8cf-205">Verwalten und Unterstützen Ihrer veröffentlichten App</span><span class="sxs-lookup"><span data-stu-id="df8cf-205">Maintaining and supporting your published app</span></span>](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
