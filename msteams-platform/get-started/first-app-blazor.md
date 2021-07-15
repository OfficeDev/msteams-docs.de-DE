---
title: Erste Schritte – Erstellen Sie Ihre erste Teams-App mitHilfe von Doppelklicken
author: adrianhall
description: Erstellen Sie mithilfe von Microsoft Teams-Toolkit und React schnell eine Microsoft Teams-App, mithilfe des Microsoft Teams Toolkits und .NET Mofzor.
ms.author: adhal
ms.date: 04/27/2021
ms.topic: quickstart
ms.openlocfilehash: a749d70875948d606f42688fea74c1e0bf79817e
ms.sourcegitcommit: e327c9766dfa05abb468cdc71319e3cba7c6c79f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/14/2021
ms.locfileid: "53428737"
---
# <a name="build-and-run-your-first-microsoft-teams-app-with-blazor"></a><span data-ttu-id="994ee-104">Erstellen und Ausführen Ihrer ersten Microsoft Teams-App mit Demerz</span><span class="sxs-lookup"><span data-stu-id="994ee-104">Build and run your first Microsoft Teams app with Blazor</span></span>

<span data-ttu-id="994ee-105">In diesem Lernprogramm erfahren Sie, wie Sie eine neue Microsoft Teams-App in .NET/Doppelklickmicron erstellen, die eine einfache persönliche App implementiert, um Informationen aus der Microsoft-Graph abzurufen.</span><span class="sxs-lookup"><span data-stu-id="994ee-105">In this tutorial, you will learn how to create a new Microsoft Teams app in .NET/Blazor that implements a simple personal app to pull information from the Microsoft Graph.</span></span> <span data-ttu-id="994ee-106">Beispielsweise enthält eine *persönliche App* eine Reihe von Registerkarten für die individuelle Verwendung.</span><span class="sxs-lookup"><span data-stu-id="994ee-106">For example, a *personal app* includes a set of tabs for individual use.</span></span> <span data-ttu-id="994ee-107">Während des Lernprogramms erfahren Sie mehr über die Struktur einer Teams-App, wie Sie eine App lokal ausführen und wie Sie die App in Azure bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="994ee-107">During the tutorial, you will learn about the structure of a Teams app, how to run an app locally, and how to deploy the app to Azure.</span></span>

<span data-ttu-id="994ee-108">In der erstellten App werden grundlegende Benutzerinformationen für den aktuellen Benutzer angezeigt.</span><span class="sxs-lookup"><span data-stu-id="994ee-108">The app that is built displays basic user information for the current user.</span></span>  <span data-ttu-id="994ee-109">Wenn die Berechtigung dazu erteilt wurde, stellt die App eine Verbindung mit Microsoft Graph als aktueller Benutzer her, um das vollständige Profil zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="994ee-109">When permission is granted, the app will connect to the Microsoft Graph as the current user to get the complete profile.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="994ee-110">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="994ee-110">Before you begin</span></span>

<span data-ttu-id="994ee-111">Stellen Sie sicher, dass Ihre Entwicklungsumgebung eingerichtet ist, indem Sie die erforderlichen Komponenten installieren.</span><span class="sxs-lookup"><span data-stu-id="994ee-111">Make sure your development environment is set up by installing the prerequisites.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="994ee-112">Erforderliche Komponenten installieren</span><span class="sxs-lookup"><span data-stu-id="994ee-112">Install prerequisites</span></span>](prerequisites.md)

## <a name="create-your-project"></a><span data-ttu-id="994ee-113">Erstellen Ihres Projekts</span><span class="sxs-lookup"><span data-stu-id="994ee-113">Create your project</span></span>

<span data-ttu-id="994ee-114">Verwenden Sie zum Erstellen Ihres ersten Projekts das Microsoft Teams-Toolkit:</span><span class="sxs-lookup"><span data-stu-id="994ee-114">Use the Teams Toolkit to create your first project:</span></span>

# <a name="visual-studio-2019"></a>[<span data-ttu-id="994ee-115">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="994ee-115">Visual Studio 2019</span></span>](#tab/vs)

1. <span data-ttu-id="994ee-116">Öffnen Sie Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="994ee-116">Open Visual Studio 2019.</span></span>

1. <span data-ttu-id="994ee-117">Wählen Sie **"Neues Projekt erstellen"** aus.</span><span class="sxs-lookup"><span data-stu-id="994ee-117">Select **Create a new project**.</span></span>

1. <span data-ttu-id="994ee-118">Wählen Sie **Microsoft Teams App** aus, und klicken Sie dann auf **"Weiter".**</span><span class="sxs-lookup"><span data-stu-id="994ee-118">Select **Microsoft Teams App**, then select **Next**.</span></span>  <span data-ttu-id="994ee-119">Um die Vorlage zu finden, verwenden Sie den Projekttyp **Microsoft Teams**.</span><span class="sxs-lookup"><span data-stu-id="994ee-119">To help you find the template, use the project type **Microsoft Teams**.</span></span>

1. <span data-ttu-id="994ee-120">Geben Sie einen Namen ein, und wählen Sie **"Weiter"** aus.</span><span class="sxs-lookup"><span data-stu-id="994ee-120">Enter a name and select **Next**.</span></span>

1. <span data-ttu-id="994ee-121">Geben Sie den Anwendungs- und Firmennamen ein.</span><span class="sxs-lookup"><span data-stu-id="994ee-121">Enter the application name and company name.</span></span>

1. <span data-ttu-id="994ee-122">Wählen Sie **Erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="994ee-122">Select **Create**.</span></span>  <span data-ttu-id="994ee-123">Der Anwendungsname und der Firmenname werden Ihren Endbenutzern angezeigt.</span><span class="sxs-lookup"><span data-stu-id="994ee-123">The application name and company name are displayed to your end users.</span></span> <span data-ttu-id="994ee-124">Ihre Microsoft Teams-App wird innerhalb weniger Sekunden erstellt.</span><span class="sxs-lookup"><span data-stu-id="994ee-124">Your Teams app will be created within a few seconds.</span></span>  <span data-ttu-id="994ee-125">Nachdem das Projekt erstellt wurde, richten Sie einmaliges Anmelden mit M365 ein:</span><span class="sxs-lookup"><span data-stu-id="994ee-125">After the project is created, set up single sign-on with M365:</span></span>

   1. <span data-ttu-id="994ee-126">Wählen Sie **Project**  >  **TeamsFx**  >  **Konfigurieren für SSO... aus.**</span><span class="sxs-lookup"><span data-stu-id="994ee-126">Select **Project** > **TeamsFx** > **Configure for SSO...**.</span></span>
   1. <span data-ttu-id="994ee-127">Melden Sie sich bei Ihrem M365-Administratorkonto an, wenn Sie dazu aufgefordert werden.</span><span class="sxs-lookup"><span data-stu-id="994ee-127">When prompted, sign in to your M365 administrator account.</span></span>

# <a name="command-line"></a>[<span data-ttu-id="994ee-128">Befehlszeile</span><span class="sxs-lookup"><span data-stu-id="994ee-128">Command line</span></span>](#tab/cli)

1. <span data-ttu-id="994ee-129">Öffnen Sie ein Terminal, und wählen Sie das Verzeichnis aus, in dem Sie das Projekt erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="994ee-129">Open a Terminal and select the directory where you wish to create the project.</span></span>

1. <span data-ttu-id="994ee-130">Ausführen, `dotnet new -i` um die Vorlage aus NuGet zu installieren:</span><span class="sxs-lookup"><span data-stu-id="994ee-130">Run `dotnet new -i` to install the template from NuGet:</span></span>

   ``` bash
   dotnet new --install Microsoft.TeamsFx.VisualStudio.ProjectTemplates::0.1.43-beta
   ```

   <span data-ttu-id="994ee-131">Dies ist nur beim ersten Mal oder beim Aktualisieren der Vorlage erforderlich.</span><span class="sxs-lookup"><span data-stu-id="994ee-131">You only need to do this the first time or when updating the template.</span></span> <span data-ttu-id="994ee-132">Überprüfen Sie [NuGet](https://www.nuget.org/packages/Microsoft.TeamsFx.VisualStudio.ProjectTemplates/) nach der neuesten Version dieses Pakets.</span><span class="sxs-lookup"><span data-stu-id="994ee-132">Check [NuGet](https://www.nuget.org/packages/Microsoft.TeamsFx.VisualStudio.ProjectTemplates/) for the latest version of this package.</span></span>

1. <span data-ttu-id="994ee-133">Erstellen eines Verzeichnisses:</span><span class="sxs-lookup"><span data-stu-id="994ee-133">Create a directory:</span></span>

   ``` bash
   mkdir helloworld
   ```

1. <span data-ttu-id="994ee-134">Ausführen, `dotnet new` um ein neues Projekt zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="994ee-134">Run `dotnet new` to create a new project:</span></span>

   ``` bash
   dotnet new teamsapp --shortName my-teams-app --companyName "My Company"
   ```

1. <span data-ttu-id="994ee-135">Konfigurieren Sie nach dem Gerüst das Projekt für Teams Bereitstellung:</span><span class="sxs-lookup"><span data-stu-id="994ee-135">After scaffolding, configure the project for Teams deployment:</span></span>

   ``` bash
   teamsfx init
   ```

   <span data-ttu-id="994ee-136">Sie können die Lösung jetzt in Visual Studio zum Debuggen öffnen.</span><span class="sxs-lookup"><span data-stu-id="994ee-136">You can now open the solution in Visual Studio for debugging.</span></span>

---

## <a name="take-a-tour-of-the-source-code"></a><span data-ttu-id="994ee-137">Machen Sie einen Rundgang durch den Quellcode</span><span class="sxs-lookup"><span data-stu-id="994ee-137">Take a tour of the source code</span></span>

<span data-ttu-id="994ee-138">Wenn Sie diesen Abschnitt vorerst überspringen möchten, können Sie [Ihre App lokal ausführen](#run-your-app-locally).</span><span class="sxs-lookup"><span data-stu-id="994ee-138">If you wish to skip this section for now, you can [run your app locally](#run-your-app-locally).</span></span>

<span data-ttu-id="994ee-139">Nachdem das Teams Toolkit Ihr Projekt konfiguriert hat, verfügen Sie über die Komponenten zum Erstellen einer einfachen persönlichen App für Teams.</span><span class="sxs-lookup"><span data-stu-id="994ee-139">After the Teams Toolkit configures your project, you have the components to build a basic personal app for Teams.</span></span> <span data-ttu-id="994ee-140">Die Projektverzeichnisse und Dateien werden im Projektmappen-Explorer-Bereich von Visual Studio 2019 angezeigt.</span><span class="sxs-lookup"><span data-stu-id="994ee-140">The project directories and files display in the Solution Explorer area of Visual Studio 2019.</span></span>

:::image type="content" source="../assets/images/teams-toolkit-v2/blazor-file-layout.png" alt-text="Screenshot der App-Projektdateien für eine persönliche App in Visual Studio 2019.":::

- <span data-ttu-id="994ee-142">Die App-Symbole werden als PNG-Dateien in `color.png` und `outline.png` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="994ee-142">The app icons are stored as PNG files in `color.png` and `outline.png`.</span></span>
- <span data-ttu-id="994ee-143">Das App-Manifest für die Veröffentlichung über das Entwicklerportal für Teams wird in `Properties/manifest.json` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="994ee-143">The app manifest for publishing through the Developer Portal for Teams is stored in `Properties/manifest.json`.</span></span>
- <span data-ttu-id="994ee-144">Zur Unterstützung der Authentifizierung wird ein Back-End-Controller `Controllers/BackendController.cs` bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="994ee-144">A backend controller is provided in `Controllers/BackendController.cs` for assisting with authentication.</span></span>

<span data-ttu-id="994ee-145">Da Sie während des Setups eine Registerkarten-App erstellt haben, erstellt das Teams-Toolkit das Gerüst für den gesamten erforderlichen Code für eine einfache Registerkarte als [Einenzockserver.](/aspnet/core/blazor)</span><span class="sxs-lookup"><span data-stu-id="994ee-145">Since you created a tab app during setup, the Teams Toolkit scaffolds all the necessary code for a basic tab as a [Blazor Server](/aspnet/core/blazor).</span></span>

- <span data-ttu-id="994ee-146">`Pages/Tab.razor` ist der Einstiegspunkt der Front-End-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="994ee-146">`Pages/Tab.razor` is the front-end application's entry point.</span></span>
- <span data-ttu-id="994ee-147">`TeamsFx.cs``JS/src/index.js`und wird für die Initialisierung der Kommunikation mit dem Teams Host verwendet.</span><span class="sxs-lookup"><span data-stu-id="994ee-147">`TeamsFx.cs` and `JS/src/index.js` is used for initializing communications with the Teams host.</span></span>

<span data-ttu-id="994ee-148">Sie können Back-End-Funktionen hinzufügen, indem Sie Ihrer Anwendung zusätzliche ASP.NET Core-Controller hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="994ee-148">You can add backend functionality by adding additional ASP.NET Core controllers to your application.</span></span>

## <a name="run-your-app-locally"></a><span data-ttu-id="994ee-149">Lokales Ausführen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="994ee-149">Run your app locally</span></span>

<span data-ttu-id="994ee-150">Das Microsoft Teams-Toolkit ermöglicht es Ihnen, Ihre App lokal auszuführen.</span><span class="sxs-lookup"><span data-stu-id="994ee-150">Teams Toolkit allows you to run your app locally.</span></span>  <span data-ttu-id="994ee-151">Dies besteht aus mehreren Teilen, die für die Bereitstellung der richtigen, von Microsoft Teams erwarteten Infrastruktur erforderlich sind:</span><span class="sxs-lookup"><span data-stu-id="994ee-151">This consists of several parts that are necessary to provide the correct infrastructure that Teams expects:</span></span>

- <span data-ttu-id="994ee-152">Es wird eine Anwendung bei Azure Active Directory registriert.</span><span class="sxs-lookup"><span data-stu-id="994ee-152">An application is registered with Azure Active Directory.</span></span>  <span data-ttu-id="994ee-153">Diese Anwendung verfügt über Berechtigungen, die mit dem Speicherort, von dem die App geladen wird, und allen Back-End-Ressourcen verknüpft sind, auf die sie zugreift.</span><span class="sxs-lookup"><span data-stu-id="994ee-153">This application has permissions associated with the location that the app is loaded from and any backend resources it accesses.</span></span>
- <span data-ttu-id="994ee-154">Eine Web-API wird (über IIS Express) gehostet, um Authentifizierungsaufgaben zu unterstützen, die als Proxy zwischen der App und Azure Active Directory fungieren.</span><span class="sxs-lookup"><span data-stu-id="994ee-154">A web API is hosted (via IIS Express) to assist with authentication tasks, acting as a proxy between the app and Azure Active Directory.</span></span>  
- <span data-ttu-id="994ee-155">Es wird ein App-Manifest generiert und im Entwicklerportal für Microsoft Teams verfügbar gemacht.</span><span class="sxs-lookup"><span data-stu-id="994ee-155">An app manifest is generated and exists in the Developer Portal for Teams.</span></span>  <span data-ttu-id="994ee-156">Microsoft Teams verwendet das App-Manifest, um die verbundenen Clients darüber zu informieren, von wo die App geladen werden soll.</span><span class="sxs-lookup"><span data-stu-id="994ee-156">Teams uses the app manifest to tell connected clients where to load the app from.</span></span>

<span data-ttu-id="994ee-157">Danach kann die App innerhalb des Teams-Clients geladen werden.</span><span class="sxs-lookup"><span data-stu-id="994ee-157">After this is done, the app can be loaded within the Teams client.</span></span>  <span data-ttu-id="994ee-158">Wir verwenden den Microsoft Teams-Webclient, um den HTML-, CSS- und JavaScript-Code in einer standardmäßigen Webentwicklungsumgebung anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="994ee-158">We use the Teams web client so that we can see the HTML, CSS, and JavaScript code within a standard web development environment.</span></span>

<span data-ttu-id="994ee-159">So erstellen Sie Ihre App und führen sie lokal aus:</span><span class="sxs-lookup"><span data-stu-id="994ee-159">To build and run your app locally:</span></span>


1. <span data-ttu-id="994ee-160">Drücken Sie Visual Studio Code die **F5-Taste,** um die Anwendung im Debugmodus auszuführen.</span><span class="sxs-lookup"><span data-stu-id="994ee-160">From Visual Studio Code, press the **F5** key to run your application in debug mode.</span></span>


1. <span data-ttu-id="994ee-161">Installieren Sie auf Anforderung das selbstsignierungsbasierte SSL-Zertifikat für das lokale Debuggen.</span><span class="sxs-lookup"><span data-stu-id="994ee-161">If requested, install the self-signed SSL certificate for local debugging.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/ssl-prompt.png" alt-text="Screenshot mit Dialogfenster zum Installieren eines SSL-Zertifikats, damit Microsoft Teams Ihre Anwendung von localhost laden kann.":::

1. <span data-ttu-id="994ee-163">Teams wird in einem Webbrowser geladen, und Sie werden dazu aufgefordert, sich anzumelden.</span><span class="sxs-lookup"><span data-stu-id="994ee-163">Teams will be loaded in a web browser, and you will be prompted to sign in.</span></span> <span data-ttu-id="994ee-164">Wenn Sie zum Öffnen von Microsoft Teams aufgefordert werden, wählen Sie „Abbrechen“ aus, um im Browser zu verbleiben.</span><span class="sxs-lookup"><span data-stu-id="994ee-164">If prompted to open Microsoft Teams, select Cancel to remain within the browser.</span></span> <span data-ttu-id="994ee-165">Melden Sie sich mit Ihrem M365-Konto an.</span><span class="sxs-lookup"><span data-stu-id="994ee-165">Sign in with your M365 account.</span></span>

1. <span data-ttu-id="994ee-166">Wenn Sie aufgefordert werden, die App auf Teams zu installieren, wählen Sie **Hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="994ee-166">When prompted to install the app onto Teams, select **Add**.</span></span>

   <span data-ttu-id="994ee-167">Ihre App wird nun angezeigt:</span><span class="sxs-lookup"><span data-stu-id="994ee-167">Your app will now be displayed:</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-completed-app.png" alt-text="Screenshot der fertiggestellten App":::

   <span data-ttu-id="994ee-169">Sie können die Debugaktivitäten so ausführen, als wäre dies eine andere Webanwendung wie das Festlegen von Haltepunkten.</span><span class="sxs-lookup"><span data-stu-id="994ee-169">You can perform the debugging activities as if this were any other web application like setting breakpoints.</span></span> <span data-ttu-id="994ee-170">Die App unterstützt Hot Reloading.</span><span class="sxs-lookup"><span data-stu-id="994ee-170">The app supports hot reloading.</span></span>  <span data-ttu-id="994ee-171">Wenn Sie eine Datei innerhalb des Projekts ändern, wird die Seite neu geladen.</span><span class="sxs-lookup"><span data-stu-id="994ee-171">If you change any file within the project, the page will be reloaded.</span></span>

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="994ee-172">Erfahren Sie, was geschieht, wenn Sie Ihre App lokal im Debugger ausführen.</span><span class="sxs-lookup"><span data-stu-id="994ee-172">Learn what happens when you run your app locally in the debugger.</span></span></summary>

<span data-ttu-id="994ee-173">Wenn Sie die **F5-Taste** drücken, wird das Teams Toolkit:</span><span class="sxs-lookup"><span data-stu-id="994ee-173">When you press the **F5** key, the Teams Toolkit:</span></span>

1. <span data-ttu-id="994ee-174">Registriert Ihre Anwendung bei Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="994ee-174">Registers your application with Azure Active Directory.</span></span>
1. <span data-ttu-id="994ee-175">Registriert Ihre Anwendung für das "Querladen" in Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="994ee-175">Registers your application for "side loading" in Microsoft Teams.</span></span>
1. <span data-ttu-id="994ee-176">Startet das Anwendungs-Back-End, das lokal ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="994ee-176">Starts your application backend running locally.</span></span>
1. <span data-ttu-id="994ee-177">Startet das lokal gehostete Anwendungs-Front-End.</span><span class="sxs-lookup"><span data-stu-id="994ee-177">Starts your application front-end hosted locally.</span></span>
1. <span data-ttu-id="994ee-178">Startet Microsoft Teams in einem Webbrowser mit einem Befehl, um Teams anzuweisen, die Anwendung querzuladen (die URL wird im Anwendungsmanifest registriert).</span><span class="sxs-lookup"><span data-stu-id="994ee-178">Starts Microsoft Teams in a web browser with a command to instruct Teams to side load the application (the URL is registered inside the application manifest).</span></span>

</details>

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="994ee-179">Erfahren Sie, wie Sie häufige Probleme bei dem lokalen Ausführen Ihrer App lösen können.</span><span class="sxs-lookup"><span data-stu-id="994ee-179">Learn how to troubleshoot common issues when running your app locally.</span></span></summary>

<span data-ttu-id="994ee-180">Um Ihre App erfolgreich in Teams ausführen zu können, benötigen Sie ein Microsoft 365 Entwicklungskonto, das das Laden der App-Seite ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="994ee-180">To successfully run your app in Teams, you must have a Microsoft 365 development account that allows app side loading.</span></span> <span data-ttu-id="994ee-181">Weitere Informationen zum Öffnen von Apps finden Sie unter [Erforderliche Komponenten](prerequisites.md#enable-sideloading).</span><span class="sxs-lookup"><span data-stu-id="994ee-181">For more information on account opening, see [Prerequisites](prerequisites.md#enable-sideloading).</span></span>

</details>

## <a name="deploy-your-app-to-azure"></a><span data-ttu-id="994ee-182">Bereitstellen Ihrer App in Azure</span><span class="sxs-lookup"><span data-stu-id="994ee-182">Deploy your app to Azure</span></span>

<span data-ttu-id="994ee-183">Die Bereitstellung besteht aus zwei Schritten:</span><span class="sxs-lookup"><span data-stu-id="994ee-183">Deployment consists of two steps:</span></span> 

1. <span data-ttu-id="994ee-184">Erforderliche Cloudressourcen werden erstellt.</span><span class="sxs-lookup"><span data-stu-id="994ee-184">Necessary cloud resources are created.</span></span> <span data-ttu-id="994ee-185">Dies wird auch als Bereitstellung bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="994ee-185">This is also known as provisioning.</span></span>
1. <span data-ttu-id="994ee-186">Beginnen Sie mit dem Codieren, und kopieren Sie Ihre App in die erstellten Cloudressourcen.</span><span class="sxs-lookup"><span data-stu-id="994ee-186">Start coding and copy your app into the created cloud resources.</span></span>

> <span data-ttu-id="994ee-187">**Vorschau**</span><span class="sxs-lookup"><span data-stu-id="994ee-187">**PREVIEW**</span></span>
>
> <span data-ttu-id="994ee-188">Die Unterstützung für Doppelklick-Apps ist neu in Teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="994ee-188">Support for Blazor apps is new in Teams Toolkit.</span></span>  <span data-ttu-id="994ee-189">Bereitstellung und Bereitstellung erfolgen mit einer Kombination aus Visual Studio 2019 und dem Entwicklerportal für Teams.</span><span class="sxs-lookup"><span data-stu-id="994ee-189">Provisioning and deployment are done with a combination of Visual Studio 2019 and the Developer Portal for Teams.</span></span>

## <a name="provision-and-deploy-your-app-to-azure-app-service"></a><span data-ttu-id="994ee-190">Bereitstellen und Bereitstellen Ihrer App im Azure App Service</span><span class="sxs-lookup"><span data-stu-id="994ee-190">Provision and deploy your app to Azure App Service</span></span>

1. <span data-ttu-id="994ee-191">Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Projektknoten, und wählen Sie **"Veröffentlichen"** aus.</span><span class="sxs-lookup"><span data-stu-id="994ee-191">In Solution Explorer, right-click the project node and select **Publish**.</span></span> <span data-ttu-id="994ee-192">Sie können auch das  >  Menüelement **"Veröffentlichen erstellen"** verwenden.</span><span class="sxs-lookup"><span data-stu-id="994ee-192">You can also use the **Build** > **Publish** menu item.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish1.png" alt-text="Auswählen des Veröffentlichungsvorgangs für das Projekt":::

1. <span data-ttu-id="994ee-194">Wählen Sie im **Veröffentlichungsfenster** **Azure** aus, und wählen Sie **"Weiter"** aus.</span><span class="sxs-lookup"><span data-stu-id="994ee-194">In the **Publish** window, select **Azure** and selct **Next**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish2.png" alt-text="Auswählen von Azure als Veröffentlichungsziel":::

1. <span data-ttu-id="994ee-196">Wählen Sie **Azure App Service (Windows)** und dann **Weiter** aus.</span><span class="sxs-lookup"><span data-stu-id="994ee-196">Select **Azure App Service (Windows)** and select **Next**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish3.png" alt-text="Auswählen von Azure App Service als Veröffentlichungsziel":::

1. <span data-ttu-id="994ee-198">Wählen Sie **+** diese Option aus, um eine neue App Service-Instanz zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="994ee-198">Select **+** to create a new App Service instance.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish4.png" alt-text="Erstellen Sie eine neue Instanz.":::

1. <span data-ttu-id="994ee-200">Im Dialogfeld **App-Dienst erstellen (Windows)** werden die Eintragsfelder **"Name",** **"Abonnementname",** **"Ressourcengruppe"** und **"Hostingplan"** ausgefüllt.</span><span class="sxs-lookup"><span data-stu-id="994ee-200">In the **Create App Service (Windows)** dialog, the **Name**, **Subscription name**, **Resource Group**, and **Hosting Plan** entry fields are populated.</span></span> <span data-ttu-id="994ee-201">Wenn Sie bereits einen App-Dienst ausgeführt haben, werden vorhandene Einstellungen ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="994ee-201">If you have already got an App Service running, existing settings are selected.</span></span>  <span data-ttu-id="994ee-202">Sie können eine neue Ressourcengruppe und einen neuen Hostingplan erstellen.</span><span class="sxs-lookup"><span data-stu-id="994ee-202">You can opt to create a new resource group and hosting plan.</span></span>  <span data-ttu-id="994ee-203">Wenn Sie fertig sind, wählen Sie **Erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="994ee-203">When ready, select **Create**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish5.png" alt-text="Auswählen von Hostingplan und Abonnement":::

1. <span data-ttu-id="994ee-205">Im Dialogfeld **"Veröffentlichen"** wurde die neu erstellte Instanz automatisch ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="994ee-205">In the **Publish** dialog, the newly created instance has been automatically selected.</span></span>  <span data-ttu-id="994ee-206">Wenn Sie fertig sind, wählen Sie **Fertig stellen** aus.</span><span class="sxs-lookup"><span data-stu-id="994ee-206">When ready, select **Finish**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish6.png" alt-text="Wählen Sie die neue Instanz aus.":::

1. <span data-ttu-id="994ee-208">Wählen Sie neben dem **Bereitstellungsmodus** das Symbol Bearbeiten (Bleistift) und dann Eigenständig aus.  </span><span class="sxs-lookup"><span data-stu-id="994ee-208">Select the **Edit** (pencil) icon next to **Deployment Mode**, and select **Self-contained**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish8.png" alt-text="Wählen Sie den eigenständigen Bereitstellungsmodus aus.":::

1. <span data-ttu-id="994ee-210">Wählen Sie **Veröffentlichen** aus.</span><span class="sxs-lookup"><span data-stu-id="994ee-210">Select **Publish**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish7.png" alt-text="Veröffentlichen Ihrer App im App-Dienst":::

   <span data-ttu-id="994ee-212">Visual Studio stellt die App in Ihrem Azure App Service bereit, und die Web-App wird in Ihrem Browser geladen.</span><span class="sxs-lookup"><span data-stu-id="994ee-212">Visual Studio deploys the app to your Azure App Service, and the web app loads in your browser.</span></span>  <span data-ttu-id="994ee-213">Fügen Sie `/tab` am Ende der URL hinzu, um Ihre Seite anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="994ee-213">Add `/tab` to the end of the URL to see your page.</span></span>

   <span data-ttu-id="994ee-214">Im Bereich **"Veröffentlichen"** der Projekteigenschaften werden die Website-URL und andere Details angezeigt.</span><span class="sxs-lookup"><span data-stu-id="994ee-214">The project properties **Publish** pane shows the site URL and other details.</span></span> <span data-ttu-id="994ee-215">Notieren Sie sich die Website-URL.</span><span class="sxs-lookup"><span data-stu-id="994ee-215">Make a note of the site URL.</span></span>

## <a name="create-an-environment-for-your-app"></a><span data-ttu-id="994ee-216">Erstellen einer Umgebung für Ihre App</span><span class="sxs-lookup"><span data-stu-id="994ee-216">Create an environment for your app</span></span>

<span data-ttu-id="994ee-217">Das Entwicklerportal für Teams verwaltet, wo die Registerkarten für Ihre App mit einer **Umgebung** geladen werden.</span><span class="sxs-lookup"><span data-stu-id="994ee-217">The Developer Portal for Teams manages where the tabs for your app are loaded from with an **Environment**.</span></span>  

<span data-ttu-id="994ee-218">**So erstellen Sie eine Umgebung:**</span><span class="sxs-lookup"><span data-stu-id="994ee-218">**To create an environment:**</span></span>

1. <span data-ttu-id="994ee-219">Öffnen Sie das [Entwicklerportal für Teams](https://dev.teams.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="994ee-219">Open the [Developer Portal for Teams](https://dev.teams.microsoft.com).</span></span>  <span data-ttu-id="994ee-220">Melden Sie sich mit Ihrem M365-Administratorkonto an.</span><span class="sxs-lookup"><span data-stu-id="994ee-220">Sign in with your M365 administrative account.</span></span>

1. <span data-ttu-id="994ee-221">Wählen Sie in der Seitenleiste **Apps** aus.</span><span class="sxs-lookup"><span data-stu-id="994ee-221">From the sidebar, select **Apps**.</span></span>

1. <span data-ttu-id="994ee-222">Wenn Sie nur eine App haben, wird sie automatisch ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="994ee-222">If you only have one app, it will be automatically selected.</span></span>  <span data-ttu-id="994ee-223">Wenn nicht, wählen Sie Ihre App aus der Liste aus.</span><span class="sxs-lookup"><span data-stu-id="994ee-223">If not, select your app from the list.</span></span>

1. <span data-ttu-id="994ee-224">Wählen Sie **Umgebungen** aus.</span><span class="sxs-lookup"><span data-stu-id="994ee-224">Select **Environments**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments1.png" alt-text="Auswählen von Umgebungen":::

1. <span data-ttu-id="994ee-226">Wählen Sie **Ihre erste Umgebung erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="994ee-226">Select **Create your first environment**.</span></span>

1. <span data-ttu-id="994ee-227">Geben Sie einen Namen für Ihre Umgebung ein, und wählen Sie **"Hinzufügen"** aus.</span><span class="sxs-lookup"><span data-stu-id="994ee-227">Enter a name for your environment and select **Add**.</span></span> <span data-ttu-id="994ee-228">Beispiel: `_Production_`.</span><span class="sxs-lookup"><span data-stu-id="994ee-228">For example, `_Production_`.</span></span>

1. <span data-ttu-id="994ee-229">Wählen Sie **Ihre erste Umgebungsvariable** erstellen aus.</span><span class="sxs-lookup"><span data-stu-id="994ee-229">Select **Create your first environment variable**.</span></span>

1. <span data-ttu-id="994ee-230">Geben Sie `azure_app_url` den **Namen** ein.</span><span class="sxs-lookup"><span data-stu-id="994ee-230">Enter `azure_app_url` for the **Name**.</span></span>  <span data-ttu-id="994ee-231">Geben Sie Ihre Azure-Website-URL ohne `https://` den **Wert** ein.</span><span class="sxs-lookup"><span data-stu-id="994ee-231">Enter your Azure site URL without the `https://` as the **Value**.</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments2.png" alt-text="Erstellen einer Umgebungsvariablen":::

   <span data-ttu-id="994ee-233">Klicken **Sie auf "Hinzufügen".**</span><span class="sxs-lookup"><span data-stu-id="994ee-233">Press **Add**.</span></span>

## <a name="update-the-app-manifest"></a><span data-ttu-id="994ee-234">Aktualisieren des App-Manifests</span><span class="sxs-lookup"><span data-stu-id="994ee-234">Update the app manifest</span></span>

<span data-ttu-id="994ee-235">Das App-Manifest lädt die Registerkarte von einer `localhost` URL.</span><span class="sxs-lookup"><span data-stu-id="994ee-235">The app manifest loads the tab from a `localhost` URL.</span></span>  <span data-ttu-id="994ee-236">In diesem Abschnitt konfigurieren Sie das App-Manifest so, dass die Registerkarte von der URL geladen wird, die in der soeben erstellten Umgebung aufgeführt ist.</span><span class="sxs-lookup"><span data-stu-id="994ee-236">In this section, you will configure the app manifest to load the tab from the URL listed within the environment you just created.</span></span>

1. <span data-ttu-id="994ee-237">Wählen Sie in der Seitenleiste die Option **"Grundlegende Informationen"** aus.</span><span class="sxs-lookup"><span data-stu-id="994ee-237">From the sidebar, select **Basic information**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments3.png" alt-text="Auswählen grundlegender Informationen":::

1. <span data-ttu-id="994ee-239">Es gibt mehrere Stellen innerhalb des Manifests, an denen ein Element als Teil einer URL aufgeführt `localhost:XXXXX` wird.</span><span class="sxs-lookup"><span data-stu-id="994ee-239">There are several places within the manifest that list a `localhost:XXXXX` as part of a URL.</span></span>  <span data-ttu-id="994ee-240">Ersetzen Sie alle Vorkommen durch `{{azure_app_url}}` , einschließlich der geschweiften Klammern.</span><span class="sxs-lookup"><span data-stu-id="994ee-240">Replace all occurrences with `{{azure_app_url}}`, including the curly braces.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments4.png" alt-text="Anpassen der grundlegenden Informationen für die Umgebung":::

1. <span data-ttu-id="994ee-242">Wenn Sie fertig sind, wählen Sie **Speichern** aus.</span><span class="sxs-lookup"><span data-stu-id="994ee-242">When complete, select **Save**.</span></span>

1. <span data-ttu-id="994ee-243">Wählen Sie in der Seitenleiste **"Funktionen"** aus.</span><span class="sxs-lookup"><span data-stu-id="994ee-243">From the sidebar, select **Capabilities**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments5.png" alt-text="Auswählen von Funktionen":::

1. <span data-ttu-id="994ee-245">Wählen Sie **"Persönliche Registerkarte" aus.**</span><span class="sxs-lookup"><span data-stu-id="994ee-245">Select **Personal Tab**.</span></span>
1. <span data-ttu-id="994ee-246">Wählen Sie neben der **Registerkarte "Persönlich"** die drei Punkte aus, und wählen Sie dann **"Bearbeiten"** aus.</span><span class="sxs-lookup"><span data-stu-id="994ee-246">Next to the **Personal Tab**, select the triple dots, then select **Edit**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments6.png" alt-text="Bearbeiten persönlicher Registerkarteneinstellungen":::

1. <span data-ttu-id="994ee-248">Ersetzen Sie die URL durch die Umgebungsvariable in den Feldern **"Inhalts-URL"** und **"Website-URL".**</span><span class="sxs-lookup"><span data-stu-id="994ee-248">Replace the URL with the environment variable within the **Content Url** and **Website Url** fields.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments7.png" alt-text="Bearbeiten von URLs für persönliche Registerkarten":::

1. <span data-ttu-id="994ee-250">Wählen Sie **Aktualisieren** aus.</span><span class="sxs-lookup"><span data-stu-id="994ee-250">Select **Update**.</span></span>

1. <span data-ttu-id="994ee-251">Klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="994ee-251">Select **Save**.</span></span>

1. <span data-ttu-id="994ee-252">Wählen Sie in der Seitenleiste **single Sign-On** aus.</span><span class="sxs-lookup"><span data-stu-id="994ee-252">From the sidebar, select **Single Sign-On**.</span></span>

1. <span data-ttu-id="994ee-253">Ersetzen Sie den `localhost` innerhalb des **Anwendungs-ID-URI** durch `{{azure_app_url}}` .</span><span class="sxs-lookup"><span data-stu-id="994ee-253">Replace the `localhost` within the **Application ID URI** with `{{azure_app_url}}`.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments8.png" alt-text="Bearbeiten des Anwendungs-ID-URI für einmaliges Anmelden":::

1. <span data-ttu-id="994ee-255">Klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="994ee-255">Select **Save**.</span></span>

1. <span data-ttu-id="994ee-256">Wählen Sie in der Seitenleiste **Domänen** aus.</span><span class="sxs-lookup"><span data-stu-id="994ee-256">From the sidebar, select **Domains**.</span></span>

1. <span data-ttu-id="994ee-257">Wählen Sie **Domäne hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="994ee-257">Select **Add a domain**.</span></span>

1. <span data-ttu-id="994ee-258">Wenn `{{azure_app_url}}` sie nicht als gültige Domäne aufgeführt ist, fügen Sie sie als gültige Domäne hinzu, und wählen Sie dann **Hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="994ee-258">If `{{azure_app_url}}` is not listed as a valid domain, add it as a valid domain, then select **Add**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments9.png" alt-text="Hinzufügen einer Domäne":::

   <span data-ttu-id="994ee-260">Sie können jetzt die Option **"Vorschau in Teams"** oben auf der Seite verwenden, um Ihre App in Teams zu starten.</span><span class="sxs-lookup"><span data-stu-id="994ee-260">You can now use the **Preview in Teams** option at the top of the page to launch your app within Teams.</span></span>

## <a name="see-also"></a><span data-ttu-id="994ee-261">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="994ee-261">See also</span></span>

* [<span data-ttu-id="994ee-262">Übersicht über Lernprogramme</span><span class="sxs-lookup"><span data-stu-id="994ee-262">Tutorials Overview</span></span>](code-samples.md)
* [<span data-ttu-id="994ee-263">Erstellen einer Unterhaltungs-Bot-App</span><span class="sxs-lookup"><span data-stu-id="994ee-263">Create a conversational bot app</span></span>](first-app-bot.md)
* [<span data-ttu-id="994ee-264">Erstellen einer Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="994ee-264">Create a messaging extension</span></span>](first-message-extension.md)
* [<span data-ttu-id="994ee-265">Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="994ee-265">Code Samples</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples)
