---
title: Erste Schritte – Erstellen Sie Ihre erste Teams-App mit Demerz
author: adrianhall
description: Erstellen Sie mithilfe von Microsoft Teams-Toolkit und React schnell eine Microsoft Teams-App, mithilfe des Microsoft Teams Toolkits und .NET Mofzor.
ms.author: adhal
ms.date: 04/27/2021
ms.topic: quickstart
ms.openlocfilehash: f40331ed06a401d60092e884add2cfa747c3ebdc
ms.sourcegitcommit: 85a52119df6c4cb4536572e6d2e7407f0e5e8a23
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2021
ms.locfileid: "53179951"
---
# <a name="build-and-run-your-first-microsoft-teams-app-with-blazor"></a><span data-ttu-id="582a1-104">Erstellen und Ausführen Ihrer ersten Microsoft Teams-App mit Demerz</span><span class="sxs-lookup"><span data-stu-id="582a1-104">Build and run your first Microsoft Teams app with Blazor</span></span>

<span data-ttu-id="582a1-105">In diesem Lernprogramm erstellen Sie eine neue Microsoft Teams-App in .NET/Doppelklick, die eine einfache persönliche App zum Abrufen von Informationen aus dem Microsoft Graph implementiert.</span><span class="sxs-lookup"><span data-stu-id="582a1-105">In this tutorial, you will create a new Microsoft Teams app in .NET/Blazor that implements a simple personal app to pull information from the Microsoft Graph.</span></span> <span data-ttu-id="582a1-106">(Eine *persönliche App* enthält eine Reihe von Registerkarten, die für die individuelle Verwendung vorgesehen sind.)  Während des Lernprogramms erfahren Sie mehr über die Struktur einer Teams-App, wie Sie eine App lokal ausführen und wie Sie die App in Azure bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="582a1-106">(A *personal app* includes a set of tabs scoped for individual use.)  During the tutorial, you will learn about the structure of a Teams app, how to run an app locally, and how to deploy the app to Azure.</span></span>

<span data-ttu-id="582a1-107">In der erstellten App werden grundlegende Benutzerinformationen für den aktuellen Benutzer angezeigt.</span><span class="sxs-lookup"><span data-stu-id="582a1-107">The app that is built displays basic user information for the current user.</span></span>  <span data-ttu-id="582a1-108">Wenn die Berechtigung dazu erteilt wurde, stellt die App eine Verbindung mit Microsoft Graph als aktueller Benutzer her, um das vollständige Profil zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="582a1-108">When permission is granted, the app will connect to the Microsoft Graph as the current user to get the complete profile.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="582a1-109">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="582a1-109">Before you begin</span></span>

<span data-ttu-id="582a1-110">Stellen Sie sicher, dass Ihre Entwicklungsumgebung eingerichtet ist, indem Sie die [erforderlichen Komponenten](prerequisites.md) installieren.</span><span class="sxs-lookup"><span data-stu-id="582a1-110">Make sure your development environment is set up by installing the [prerequisites](prerequisites.md)</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="582a1-111">Erforderliche Komponenten installieren</span><span class="sxs-lookup"><span data-stu-id="582a1-111">Install prerequisites</span></span>](prerequisites.md)

## <a name="create-your-project"></a><span data-ttu-id="582a1-112">Erstellen Ihres Projekts</span><span class="sxs-lookup"><span data-stu-id="582a1-112">Create your project</span></span>

<span data-ttu-id="582a1-113">Verwenden Sie zum Erstellen Ihres ersten Projekts das Microsoft Teams-Toolkit:</span><span class="sxs-lookup"><span data-stu-id="582a1-113">Use the Teams Toolkit to create your first project:</span></span>

# <a name="visual-studio-2019"></a>[<span data-ttu-id="582a1-114">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="582a1-114">Visual Studio 2019</span></span>](#tab/vs)

1. <span data-ttu-id="582a1-115">Öffnen Sie Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="582a1-115">Open Visual Studio 2019.</span></span>

1. <span data-ttu-id="582a1-116">Wählen Sie **"Neues Projekt erstellen"** aus.</span><span class="sxs-lookup"><span data-stu-id="582a1-116">Select **Create a new project**.</span></span>

1. <span data-ttu-id="582a1-117">Wählen Sie **Microsoft Teams App** aus, und drücken Sie dann **"Weiter".**</span><span class="sxs-lookup"><span data-stu-id="582a1-117">Select **Microsoft Teams App**, then press **Next**.</span></span>  <span data-ttu-id="582a1-118">Um die Vorlage zu finden, verwenden Sie den Projekttyp **Microsoft Teams**.</span><span class="sxs-lookup"><span data-stu-id="582a1-118">To help you find the template, use the project type **Microsoft Teams**.</span></span>

1. <span data-ttu-id="582a1-119">Geben Sie dem Projekt und der Projektmappe einen guten Namen, und drücken Sie dann **"Weiter".**</span><span class="sxs-lookup"><span data-stu-id="582a1-119">Give the project and solution a good name, then press **Next**.</span></span>

1. <span data-ttu-id="582a1-120">Geben Sie den Anwendungsnamen und den Firmennamen ein, und drücken Sie dann die Schaltfläche **"Erstellen".**</span><span class="sxs-lookup"><span data-stu-id="582a1-120">Provide the application name and company name, then press **Create**.</span></span>  <span data-ttu-id="582a1-121">Der Anwendungsname und der Firmenname werden Ihren Endbenutzern angezeigt.</span><span class="sxs-lookup"><span data-stu-id="582a1-121">The application name and company name are displayed to your end users.</span></span>

1. <span data-ttu-id="582a1-122">Ihre Microsoft Teams-App wird innerhalb weniger Sekunden erstellt.</span><span class="sxs-lookup"><span data-stu-id="582a1-122">Your Teams app will be created within a few seconds.</span></span>  <span data-ttu-id="582a1-123">Nachdem das Projekt erstellt wurde, richten Sie einmaliges Anmelden mit M365 ein:</span><span class="sxs-lookup"><span data-stu-id="582a1-123">Once the project is created, set up single sign-on with M365:</span></span>

   - <span data-ttu-id="582a1-124">Wählen Sie **Project**  >  **TeamsFx**  >  **Konfigurieren für SSO... aus.**</span><span class="sxs-lookup"><span data-stu-id="582a1-124">Select **Project** > **TeamsFx** > **Configure for SSO...**.</span></span>
   - <span data-ttu-id="582a1-125">Melden Sie sich bei Ihrem M365-Administratorkonto an, wenn Sie dazu aufgefordert werden.</span><span class="sxs-lookup"><span data-stu-id="582a1-125">When prompted, sign in to your M365 administrator account.</span></span>

# <a name="command-line"></a>[<span data-ttu-id="582a1-126">Befehlszeile</span><span class="sxs-lookup"><span data-stu-id="582a1-126">Command line</span></span>](#tab/cli)

1. <span data-ttu-id="582a1-127">Öffnen Sie ein Terminal, und wählen Sie das Verzeichnis aus, in dem Sie das Projekt erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="582a1-127">Open a Terminal and select the directory where you wish to create the project.</span></span>

1. <span data-ttu-id="582a1-128">Ausführen, `dotnet new -i` um die Vorlage aus NuGet zu installieren:</span><span class="sxs-lookup"><span data-stu-id="582a1-128">Run `dotnet new -i` to install the template from NuGet:</span></span>

   ``` bash
   dotnet new --install Microsoft.TeamsFx.VisualStudio.ProjectTemplates::0.1.43-beta
   ```

   <span data-ttu-id="582a1-129">Dies ist nur beim ersten Mal oder beim Aktualisieren der Vorlage erforderlich.</span><span class="sxs-lookup"><span data-stu-id="582a1-129">You only need to do this the first time or when updating the template.</span></span> <span data-ttu-id="582a1-130">Überprüfen Sie [NuGet](https://www.nuget.org/packages/Microsoft.TeamsFx.VisualStudio.ProjectTemplates/) nach der neuesten Version dieses Pakets.</span><span class="sxs-lookup"><span data-stu-id="582a1-130">Check [NuGet](https://www.nuget.org/packages/Microsoft.TeamsFx.VisualStudio.ProjectTemplates/) for the latest version of this package.</span></span>

1. <span data-ttu-id="582a1-131">Erstellen eines Verzeichnisses:</span><span class="sxs-lookup"><span data-stu-id="582a1-131">Create a directory:</span></span>

   ``` bash
   mkdir helloworld
   ```

1. <span data-ttu-id="582a1-132">Ausführen, `dotnet new` um ein neues Projekt zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="582a1-132">Run `dotnet new` to create a new project:</span></span>

   ``` bash
   dotnet new teamsapp --shortName my-teams-app --companyName "My Company"
   ```

1. <span data-ttu-id="582a1-133">Nachdem Sie ein Gerüst erstellt haben, konfigurieren Sie das Projekt für Teams Bereitstellung:</span><span class="sxs-lookup"><span data-stu-id="582a1-133">Once scaffolded, configure the project for Teams deployment:</span></span>

   ``` bash
   teamsfx init
   ```

<span data-ttu-id="582a1-134">Sie können die Lösung nun in Visual Studio zum Debuggen öffnen.</span><span class="sxs-lookup"><span data-stu-id="582a1-134">You can now open the solution in Visual Studio for debugging.</span></span>

---

## <a name="take-a-tour-of-the-source-code"></a><span data-ttu-id="582a1-135">Machen Sie einen Rundgang durch den Quellcode</span><span class="sxs-lookup"><span data-stu-id="582a1-135">Take a tour of the source code</span></span>

<span data-ttu-id="582a1-136">Wenn Sie diesen Abschnitt vorerst überspringen möchten, können Sie [Ihre App lokal ausführen](#run-your-app-locally).</span><span class="sxs-lookup"><span data-stu-id="582a1-136">If you wish to skip this section for now, you can [run your app locally](#run-your-app-locally).</span></span>

<span data-ttu-id="582a1-137">Nachdem das Microsoft Teams Toolkit Ihr Projekt konfiguriert hat, verfügen Sie über die Komponenten zum Erstellen einer einfachen persönlichen App für Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="582a1-137">Once the Teams Toolkit configures your project, you have the components to build a basic personal app for Teams.</span></span> <span data-ttu-id="582a1-138">Die Projektverzeichnisse und Dateien werden im Projektmappen-Explorer-Bereich von Visual Studio 2019 angezeigt.</span><span class="sxs-lookup"><span data-stu-id="582a1-138">The project directories and files display in the Solution Explorer area of Visual Studio 2019.</span></span>

:::image type="content" source="../assets/images/teams-toolkit-v2/blazor-file-layout.png" alt-text="Screenshot der App-Projektdateien für eine persönliche App in Visual Studio 2019.":::

- <span data-ttu-id="582a1-140">Die App-Symbole werden als PNG-Dateien in `color.png` und `outline.png` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="582a1-140">The app icons are stored as PNG files in `color.png` and `outline.png`.</span></span>
- <span data-ttu-id="582a1-141">Das App-Manifest für die Veröffentlichung über das Entwicklerportal für Teams wird in `Properties/manifest.json` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="582a1-141">The app manifest for publishing through the Developer Portal for Teams is stored in `Properties/manifest.json`.</span></span>
- <span data-ttu-id="582a1-142">Zur Unterstützung der Authentifizierung wird ein Back-End-Controller `Controllers/BackendController.cs` bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="582a1-142">A backend controller is provided in `Controllers/BackendController.cs` for assisting with authentication.</span></span>

<span data-ttu-id="582a1-143">Da Sie während des Setups eine Registerkarten-App erstellt haben, erstellt das Teams-Toolkit das Gerüst für den gesamten erforderlichen Code für eine einfache Registerkarte als [Einenzockserver.](/aspnet/core/blazor)</span><span class="sxs-lookup"><span data-stu-id="582a1-143">Since you created a tab app during setup, the Teams Toolkit scaffolds all the necessary code for a basic tab as a [Blazor Server](/aspnet/core/blazor).</span></span>

- <span data-ttu-id="582a1-144">`Pages/Tab.razor` ist der Einstiegspunkt der Front-End-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="582a1-144">`Pages/Tab.razor` is the front-end application's entry point.</span></span>
- <span data-ttu-id="582a1-145">`TeamsFx.cs``JS/src/index.js`wird für die Initialisierung der Kommunikation mit dem Teams Host verwendet.</span><span class="sxs-lookup"><span data-stu-id="582a1-145">`TeamsFx.cs` and `JS/src/index.js` is used for initializing communications with the Teams host.</span></span>

<span data-ttu-id="582a1-146">Sie können Back-End-Funktionen hinzufügen, indem Sie Ihrer Anwendung zusätzliche ASP.NET Core-Controller hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="582a1-146">You can add backend functionality by adding additional ASP.NET Core controllers to your application.</span></span>

## <a name="run-your-app-locally"></a><span data-ttu-id="582a1-147">Lokales Ausführen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="582a1-147">Run your app locally</span></span>

<span data-ttu-id="582a1-148">Das Microsoft Teams-Toolkit ermöglicht es Ihnen, Ihre App lokal auszuführen.</span><span class="sxs-lookup"><span data-stu-id="582a1-148">Teams Toolkit allows you to run your app locally.</span></span>  <span data-ttu-id="582a1-149">Dies besteht aus mehreren Teilen, die für die Bereitstellung der richtigen, von Microsoft Teams erwarteten Infrastruktur erforderlich sind:</span><span class="sxs-lookup"><span data-stu-id="582a1-149">This consists of several parts that are necessary to provide the correct infrastructure that Teams expects:</span></span>

- <span data-ttu-id="582a1-150">Es wird eine Anwendung bei Azure Active Directory registriert.</span><span class="sxs-lookup"><span data-stu-id="582a1-150">An application is registered with Azure Active Directory.</span></span>  <span data-ttu-id="582a1-151">Diese Anwendung verfügt über Berechtigungen, die mit dem Speicherort, von dem die App geladen wird, und allen Back-End-Ressourcen verknüpft sind, auf die sie zugreift.</span><span class="sxs-lookup"><span data-stu-id="582a1-151">This application has permissions associated with the location that the app is loaded from and any backend resources it accesses.</span></span>
- <span data-ttu-id="582a1-152">Eine Web-API wird (über IIS Express) gehostet, um Authentifizierungsaufgaben zu unterstützen und als Proxy zwischen der App und Azure Active Directory zu fungieren.</span><span class="sxs-lookup"><span data-stu-id="582a1-152">A web API is hosted (via IIS Express) to assist with authentication tasks, acting as a proxy between the app and Azure Active Directory.</span></span>  
- <span data-ttu-id="582a1-153">Es wird ein App-Manifest generiert und im Entwicklerportal für Microsoft Teams verfügbar gemacht.</span><span class="sxs-lookup"><span data-stu-id="582a1-153">An app manifest is generated and exists in the Developer Portal for Teams.</span></span>  <span data-ttu-id="582a1-154">Microsoft Teams verwendet das App-Manifest, um die verbundenen Clients darüber zu informieren, von wo die App geladen werden soll.</span><span class="sxs-lookup"><span data-stu-id="582a1-154">Teams uses the app manifest to tell connected clients where to load the app from.</span></span>

<span data-ttu-id="582a1-155">Sobald dies erfolgt ist, kann die App im Microsoft Teams-Client geladen werden.</span><span class="sxs-lookup"><span data-stu-id="582a1-155">Once this is done, the app can be loaded within the Teams client.</span></span>  <span data-ttu-id="582a1-156">Wir verwenden den Microsoft Teams-Webclient, um den HTML-, CSS- und JavaScript-Code in einer standardmäßigen Webentwicklungsumgebung anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="582a1-156">We use the Teams web client so that we can see the HTML, CSS, and JavaScript code within a standard web development environment.</span></span>

<span data-ttu-id="582a1-157">So erstellen Sie Ihre App und führen sie lokal aus:</span><span class="sxs-lookup"><span data-stu-id="582a1-157">To build and run your app locally:</span></span>

1. <span data-ttu-id="582a1-158">Drücken Sie von Visual Studio **F5,** um die Anwendung im Debugmodus auszuführen.</span><span class="sxs-lookup"><span data-stu-id="582a1-158">From Visual Studio, press **F5** to run your application in debug mode.</span></span>

1. <span data-ttu-id="582a1-159">Installieren Sie auf Anforderung das selbstsignierungsbasierte SSL-Zertifikat für das lokale Debuggen.</span><span class="sxs-lookup"><span data-stu-id="582a1-159">If requested, install the self-signed SSL certificate for local debugging.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/ssl-prompt.png" alt-text="Screenshot mit Dialogfenster zum Installieren eines SSL-Zertifikats, damit Microsoft Teams Ihre Anwendung von localhost laden kann.":::

1. <span data-ttu-id="582a1-161">Teams wird in einem Webbrowser geladen, und Sie werden dazu aufgefordert, sich anzumelden.</span><span class="sxs-lookup"><span data-stu-id="582a1-161">Teams will be loaded in a web browser, and you will be prompted to sign in.</span></span> <span data-ttu-id="582a1-162">Wenn Sie zum Öffnen von Microsoft Teams aufgefordert werden, wählen Sie „Abbrechen“ aus, um im Browser zu verbleiben.</span><span class="sxs-lookup"><span data-stu-id="582a1-162">If prompted to open Microsoft Teams, select Cancel to remain within the browser.</span></span> <span data-ttu-id="582a1-163">Melden Sie sich mit Ihrem M365-Konto an.</span><span class="sxs-lookup"><span data-stu-id="582a1-163">Sign in with your M365 account.</span></span>
1. <span data-ttu-id="582a1-164">Wenn Sie aufgefordert werden, die App in Microsoft Teams zu installieren, drücken Sie **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="582a1-164">When prompted to install the app onto Teams, press **Add**.</span></span>

<span data-ttu-id="582a1-165">Ihre App wird nun angezeigt:</span><span class="sxs-lookup"><span data-stu-id="582a1-165">Your app will now be displayed:</span></span>

:::image type="content" source="../assets/images/teams-toolkit-v2/blazor-completed-app.png" alt-text="Screenshot der fertiggestellten App":::

<span data-ttu-id="582a1-167">Sie können normale Debugaktivitäten wie bei jeder anderen Webanwendung ausführen (z. B. Haltepunkte festlegen).</span><span class="sxs-lookup"><span data-stu-id="582a1-167">You can do normal debugging activities as if this were any other web application (such as setting breakpoints).</span></span> <span data-ttu-id="582a1-168">Die App unterstützt Hot Reloading.</span><span class="sxs-lookup"><span data-stu-id="582a1-168">The app supports hot reloading.</span></span>  <span data-ttu-id="582a1-169">Wenn Sie eine Datei innerhalb des Projekts ändern, wird die Seite neu geladen.</span><span class="sxs-lookup"><span data-stu-id="582a1-169">If you change any file within the project, the page will be reloaded.</span></span>

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="582a1-170">Erfahren Sie, was geschieht, wenn Sie Ihre App lokal im Debugger ausführen.</span><span class="sxs-lookup"><span data-stu-id="582a1-170">Learn what happens when you run your app locally in the debugger.</span></span></summary>

<span data-ttu-id="582a1-171">Wenn Sie F5 gedrückt haben, hat das Microsoft Teams-Toolkit Folgendes getan:</span><span class="sxs-lookup"><span data-stu-id="582a1-171">When you pressed F5, the Teams Toolkit:</span></span>

1. <span data-ttu-id="582a1-172">Ihre Anwendung bei Azure Active Directory registriert.</span><span class="sxs-lookup"><span data-stu-id="582a1-172">Registered your application with Azure Active Directory.</span></span>
1. <span data-ttu-id="582a1-173">Ihre Anwendung bei Microsoft Teams für das „Querladen“ registriert.</span><span class="sxs-lookup"><span data-stu-id="582a1-173">Registered your application for "side loading" in Microsoft Teams.</span></span>
1. <span data-ttu-id="582a1-174">Das Anwendungs-Back-End wurde lokal ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="582a1-174">Started your application backend running locally.</span></span>
1. <span data-ttu-id="582a1-175">Das lokal gehostete Anwendungs-Front-End gestartet</span><span class="sxs-lookup"><span data-stu-id="582a1-175">Started your application front-end hosted locally.</span></span>
1. <span data-ttu-id="582a1-176">Gestartet Microsoft Teams in einem Webbrowser mit einem Befehl, um Teams anzuweisen, die Anwendung querzuladen (die URL wird im Anwendungsmanifest registriert).</span><span class="sxs-lookup"><span data-stu-id="582a1-176">Started Microsoft Teams in a web browser with a command to instruct Teams to side load the application (the URL is registered inside the application manifest).</span></span>

</details>

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="582a1-177">Erfahren Sie, wie Sie häufige Probleme bei dem lokalen Ausführen Ihrer App lösen können.</span><span class="sxs-lookup"><span data-stu-id="582a1-177">Learn how to troubleshoot common issues when running your app locally.</span></span></summary>

<span data-ttu-id="582a1-178">Um Ihre App erfolgreich in Teams ausführen zu können, benötigen Sie ein Microsoft 365 Entwicklungskonto, das das Laden der App-Seite ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="582a1-178">To successfully run your app in Teams, you must have a Microsoft 365 development account that allows app side loading.</span></span> <span data-ttu-id="582a1-179">Weitere Informationen zum Öffnen von Apps finden Sie unter [Erforderliche Komponenten](prerequisites.md#enable-sideloading).</span><span class="sxs-lookup"><span data-stu-id="582a1-179">For more information on account opening, see [Prerequisites](prerequisites.md#enable-sideloading).</span></span>

</details>

## <a name="deploy-your-app-to-azure"></a><span data-ttu-id="582a1-180">Bereitstellen Ihrer App in Azure</span><span class="sxs-lookup"><span data-stu-id="582a1-180">Deploy your app to Azure</span></span>

<span data-ttu-id="582a1-181">Die Bereitstellung besteht aus zwei Schritten.</span><span class="sxs-lookup"><span data-stu-id="582a1-181">Deployment consists of two steps.</span></span>  <span data-ttu-id="582a1-182">Zuerst werden erforderliche Cloudressourcen erstellt (auch als Bereitstellung bezeichnet), dann wird der Code, aus dem Ihre App besteht, in die erstellten Cloudressourcen kopiert.</span><span class="sxs-lookup"><span data-stu-id="582a1-182">First, necessary cloud resources are created (also known as provisioning), then the code that makes up your app is copied into the created cloud resources.</span></span>

> <span data-ttu-id="582a1-183">**Vorschau**</span><span class="sxs-lookup"><span data-stu-id="582a1-183">**PREVIEW**</span></span>
>
> <span data-ttu-id="582a1-184">Die Unterstützung für Doppelklick-Apps ist neu in Teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="582a1-184">Support for Blazor apps is new in Teams Toolkit.</span></span>  <span data-ttu-id="582a1-185">Bereitstellung und Bereitstellung erfolgen mit einer Kombination aus Visual Studio 2019 und dem Entwicklerportal für Teams.</span><span class="sxs-lookup"><span data-stu-id="582a1-185">Provisioning and deployment are done with a combination of Visual Studio 2019 and the Developer Portal for Teams.</span></span>

## <a name="provision-and-deploy-your-app-to-azure-app-service"></a><span data-ttu-id="582a1-186">Bereitstellen und Bereitstellen Ihrer App im Azure App Service</span><span class="sxs-lookup"><span data-stu-id="582a1-186">Provision and deploy your app to Azure App Service</span></span>

1. <span data-ttu-id="582a1-187">Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Projektknoten, und wählen Sie **"Veröffentlichen"** aus (oder verwenden Sie das Menüelement   >  **"Veröffentlichen** erstellen").</span><span class="sxs-lookup"><span data-stu-id="582a1-187">In Solution Explorer, right-click the project node and choose **Publish** (or use the **Build** > **Publish** menu item).</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish1.png" alt-text="Auswählen des Veröffentlichungsvorgangs für das Projekt":::

1. <span data-ttu-id="582a1-189">Wählen Sie im **Veröffentlichungsfenster** **Azure** aus.</span><span class="sxs-lookup"><span data-stu-id="582a1-189">In the **Publish** window, select **Azure**.</span></span>  <span data-ttu-id="582a1-190">Klicken Sie **auf "Weiter".**</span><span class="sxs-lookup"><span data-stu-id="582a1-190">Press **Next**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish2.png" alt-text="Auswählen von Azure als Veröffentlichungsziel":::

1. <span data-ttu-id="582a1-192">Wählen Sie **Azure App Service (Windows)** aus.</span><span class="sxs-lookup"><span data-stu-id="582a1-192">Select **Azure App Service (Windows)**.</span></span>  <span data-ttu-id="582a1-193">Klicken Sie **auf "Weiter".**</span><span class="sxs-lookup"><span data-stu-id="582a1-193">Press **Next**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish3.png" alt-text="Auswählen von Azure App Service als Veröffentlichungsziel":::

1. <span data-ttu-id="582a1-195">Wählen Sie **+** diese Option aus, um eine neue App Service-Instanz zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="582a1-195">Select **+** to create a new App Service instance.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish4.png" alt-text="Erstellen Sie eine neue Instanz.":::

1. <span data-ttu-id="582a1-197">Im Dialogfeld **"App-Dienst erstellen" (Windows)** werden die Eintragsfelder **"Name",** **"Abonnementname",** **"Ressourcengruppe"** und **"Hostingplan"** ausgefüllt.</span><span class="sxs-lookup"><span data-stu-id="582a1-197">In the **Create App Service (Windows)** dialog, the **Name**, **Subscription name**, **Resource Group**, and **Hosting Plan** entry fields are populated.</span></span> <span data-ttu-id="582a1-198">Wenn Sie bereits einen App-Dienst ausgeführt haben, werden vorhandene Einstellungen ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="582a1-198">If you have already got an App Service running, existing settings will be selected.</span></span>  <span data-ttu-id="582a1-199">Sie können eine neue Ressourcengruppe und einen Hostingplan erstellen (empfohlen).</span><span class="sxs-lookup"><span data-stu-id="582a1-199">You can opt to create a new resource group and hosting plan (Recommended).</span></span>  <span data-ttu-id="582a1-200">Wenn Sie fertig sind, wählen Sie **Erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="582a1-200">When ready, select **Create**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish5.png" alt-text="Auswählen von Hostingplan und Abonnement":::

1. <span data-ttu-id="582a1-202">Im Dialogfeld **"Veröffentlichen"** wurde die neu erstellte Instanz automatisch ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="582a1-202">In the **Publish** dialog, the newly created instance has been automatically selected.</span></span>  <span data-ttu-id="582a1-203">Wenn Sie fertig sind, wählen Sie **Fertig stellen** aus.</span><span class="sxs-lookup"><span data-stu-id="582a1-203">When ready, select **Finish**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish6.png" alt-text="Wählen Sie die neue Instanz aus.":::

1. <span data-ttu-id="582a1-205">Klicken Sie auf das Symbol **"Bearbeiten"** (Bleistift) neben dem **Bereitstellungsmodus,** und wählen Sie dann **"Eigenständig"** aus.</span><span class="sxs-lookup"><span data-stu-id="582a1-205">Press the **Edit** (pencil) icon next to **Deployment Mode**, then select **Self-contained**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish8.png" alt-text="Wählen Sie den eigenständigen Bereitstellungsmodus aus.":::

1. <span data-ttu-id="582a1-207">Wählen Sie **Veröffentlichen** aus.</span><span class="sxs-lookup"><span data-stu-id="582a1-207">Select **Publish**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish7.png" alt-text="Veröffentlichen Ihrer App im App-Dienst":::

<span data-ttu-id="582a1-209">Visual Studio stellt die App in Ihrem Azure App Service bereit, und die Web-App wird in Ihrem Browser geladen.</span><span class="sxs-lookup"><span data-stu-id="582a1-209">Visual Studio deploys the app to your Azure App Service, and the web app loads in your browser.</span></span>  <span data-ttu-id="582a1-210">Fügen Sie `/tab` am Ende der URL hinzu, um Ihre Seite anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="582a1-210">Add `/tab` to the end of the URL to see your page.</span></span>

<span data-ttu-id="582a1-211">Im Bereich **"Veröffentlichen"** der Projekteigenschaften werden die Website-URL und andere Details angezeigt.</span><span class="sxs-lookup"><span data-stu-id="582a1-211">The project properties **Publish** pane shows the site URL and other details.</span></span> <span data-ttu-id="582a1-212">Notieren Sie sich die Website-URL.</span><span class="sxs-lookup"><span data-stu-id="582a1-212">Make a note of the site URL.</span></span>

## <a name="create-an-environment-for-your-app"></a><span data-ttu-id="582a1-213">Erstellen einer Umgebung für Ihre App</span><span class="sxs-lookup"><span data-stu-id="582a1-213">Create an environment for your app</span></span>

<span data-ttu-id="582a1-214">Das Entwicklerportal für Teams verwaltet, wo die Registerkarten für Ihre App mit einer **Umgebung** geladen werden.</span><span class="sxs-lookup"><span data-stu-id="582a1-214">The Developer Portal for Teams manages where the tabs for your app are loaded from with an **Environment**.</span></span>  <span data-ttu-id="582a1-215">So erstellen Sie eine Umgebung:</span><span class="sxs-lookup"><span data-stu-id="582a1-215">To create an environment:</span></span>

1. <span data-ttu-id="582a1-216">Öffnen Sie das [Entwicklerportal für Teams](https://dev.teams.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="582a1-216">Open the [Developer Portal for Teams](https://dev.teams.microsoft.com).</span></span>  <span data-ttu-id="582a1-217">Melden Sie sich mit Ihrem M365-Administratorkonto an.</span><span class="sxs-lookup"><span data-stu-id="582a1-217">Sign in with your M365 administrative account.</span></span>

1. <span data-ttu-id="582a1-218">Wählen Sie in der Seitenleiste **Apps** aus.</span><span class="sxs-lookup"><span data-stu-id="582a1-218">From the sidebar, select **Apps**.</span></span>

1. <span data-ttu-id="582a1-219">Wenn Sie nur eine App haben, wird sie automatisch ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="582a1-219">If you only have one app, it will be automatically selected.</span></span>  <span data-ttu-id="582a1-220">Wenn nicht, wählen Sie Ihre App aus der Liste aus.</span><span class="sxs-lookup"><span data-stu-id="582a1-220">If not, select your app from the list.</span></span>

1. <span data-ttu-id="582a1-221">Wählen Sie **Umgebungen** aus.</span><span class="sxs-lookup"><span data-stu-id="582a1-221">Select **Environments**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments1.png" alt-text="Auswählen von Umgebungen":::

1. <span data-ttu-id="582a1-223">Wählen Sie **Ihre erste Umgebung erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="582a1-223">Select **Create your first environment**.</span></span>

1. <span data-ttu-id="582a1-224">Geben Sie einen Namen für Ihre Umgebung ein, und drücken Sie dann **"Hinzufügen".** z. _B. Production_.</span><span class="sxs-lookup"><span data-stu-id="582a1-224">Enter a name for your environment, then press **Add**; for example _Production_.</span></span>

1. <span data-ttu-id="582a1-225">Wenn die neu erstellte Umgebung ausgewählt ist, drücken **Sie Die erste Umgebungsvariable** erstellen.</span><span class="sxs-lookup"><span data-stu-id="582a1-225">With the newly created environment selected, press **Create your first environment variable**.</span></span>

1. <span data-ttu-id="582a1-226">Geben Sie `azure_app_url` den **Namen** ein.</span><span class="sxs-lookup"><span data-stu-id="582a1-226">Enter `azure_app_url` for the **Name**.</span></span>  <span data-ttu-id="582a1-227">Geben Sie Ihre Azure-Website-URL (ohne die `https://` ) als **Wert** ein.</span><span class="sxs-lookup"><span data-stu-id="582a1-227">Enter your Azure site URL (without the `https://`) as the **Value**.</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments2.png" alt-text="Erstellen einer Umgebungsvariablen":::

   <span data-ttu-id="582a1-229">Klicken **Sie auf "Hinzufügen".**</span><span class="sxs-lookup"><span data-stu-id="582a1-229">Press **Add**.</span></span>

## <a name="update-the-app-manifest"></a><span data-ttu-id="582a1-230">Aktualisieren des App-Manifests</span><span class="sxs-lookup"><span data-stu-id="582a1-230">Update the app manifest</span></span>

<span data-ttu-id="582a1-231">Das App-Manifest lädt die Registerkarte von einer `localhost` URL.</span><span class="sxs-lookup"><span data-stu-id="582a1-231">The app manifest is loading the tab from a `localhost` URL.</span></span>  <span data-ttu-id="582a1-232">In diesem Abschnitt passen Sie das App-Manifest so an, dass die Registerkarte von der URL geladen wird, die in der soeben erstellten Umgebung aufgeführt ist.</span><span class="sxs-lookup"><span data-stu-id="582a1-232">In this section, you will adjust the app manifest to load the tab from the URL listed within the environment you just created.</span></span>

1. <span data-ttu-id="582a1-233">Wählen Sie in der Seitenleiste die Option **"Grundlegende Informationen"** aus.</span><span class="sxs-lookup"><span data-stu-id="582a1-233">From the sidebar, select **Basic information**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments3.png" alt-text="Auswählen grundlegender Informationen":::

1. <span data-ttu-id="582a1-235">Es gibt mehrere Stellen innerhalb des Manifests, an denen ein Element als Teil einer URL aufgeführt `localhost:XXXXX` wird.</span><span class="sxs-lookup"><span data-stu-id="582a1-235">There are several places within the manifest that list a `localhost:XXXXX` as part of a URL.</span></span>  <span data-ttu-id="582a1-236">Ersetzen Sie alle Vorkommen `{{azure_app_url}}` durch (einschließlich der geschweiften Klammern).</span><span class="sxs-lookup"><span data-stu-id="582a1-236">Replace all occurrences with `{{azure_app_url}}` (including the curly braces).</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments4.png" alt-text="Anpassen der grundlegenden Informationen für die Umgebung":::

1. <span data-ttu-id="582a1-238">Wenn Sie fertig sind, klicken Sie auf **"Speichern".**</span><span class="sxs-lookup"><span data-stu-id="582a1-238">When complete, press **Save**.</span></span>

1. <span data-ttu-id="582a1-239">Wählen Sie in der Seitenleiste **"Funktionen"** aus.</span><span class="sxs-lookup"><span data-stu-id="582a1-239">From the sidebar, select **Capabilities**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments5.png" alt-text="Auswählen von Funktionen":::

1. <span data-ttu-id="582a1-241">Wählen Sie **"Persönliche Registerkarte" aus.**</span><span class="sxs-lookup"><span data-stu-id="582a1-241">Select **Personal Tab**.</span></span>
1. <span data-ttu-id="582a1-242">Wählen Sie neben der **Registerkarte "Persönlich"** die drei Punkte aus, und wählen Sie dann **"Bearbeiten"** aus.</span><span class="sxs-lookup"><span data-stu-id="582a1-242">Next to the **Personal Tab**, select the triple dots, then select **Edit**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments6.png" alt-text="Bearbeiten persönlicher Registerkarteneinstellungen":::

1. <span data-ttu-id="582a1-244">Ersetzen Sie die URL durch die Umgebungsvariable in den Feldern **"Inhalts-URL"** und **"Website-URL".**</span><span class="sxs-lookup"><span data-stu-id="582a1-244">Replace the URL with the environment variable within the **Content Url** and **Website Url** fields.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments7.png" alt-text="Bearbeiten von URLs für persönliche Registerkarten":::

1. <span data-ttu-id="582a1-246">Drücken Sie **update**.</span><span class="sxs-lookup"><span data-stu-id="582a1-246">Press **Update**.</span></span>

1. <span data-ttu-id="582a1-247">Klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="582a1-247">Press **Save**.</span></span>

1. <span data-ttu-id="582a1-248">Wählen Sie in der Seitenleiste **single Sign-On** aus.</span><span class="sxs-lookup"><span data-stu-id="582a1-248">From the sidebar, select **Single Sign-On**.</span></span>

1. <span data-ttu-id="582a1-249">Ersetzen Sie den `localhost` innerhalb des **Anwendungs-ID-URI** durch `{{azure_app_url}}` .</span><span class="sxs-lookup"><span data-stu-id="582a1-249">Replace the `localhost` within the **Application ID URI** with `{{azure_app_url}}`.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments8.png" alt-text="Bearbeiten des Anwendungs-ID-URI für einmaliges Anmelden":::

1. <span data-ttu-id="582a1-251">Klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="582a1-251">Press **Save**.</span></span>

1. <span data-ttu-id="582a1-252">Drücken Sie in der Seitenleiste **Domänen**.</span><span class="sxs-lookup"><span data-stu-id="582a1-252">From the sidebar, press **Domains**.</span></span>

1. <span data-ttu-id="582a1-253">Drücken **Sie "Domäne hinzufügen".**</span><span class="sxs-lookup"><span data-stu-id="582a1-253">Press **Add a domain**.</span></span>

1. <span data-ttu-id="582a1-254">Wenn `{{azure_app_url}}` sie nicht als gültige Domäne aufgeführt ist, fügen Sie sie als gültige Domäne hinzu, und klicken Sie dann auf **"Hinzufügen".**</span><span class="sxs-lookup"><span data-stu-id="582a1-254">If `{{azure_app_url}}` is not listed as a valid domain, add it as a valid domain, then press **Add**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments9.png" alt-text="Hinzufügen einer Domäne":::

<span data-ttu-id="582a1-256">Sie können jetzt die Schaltfläche **"Vorschau in Teams"** oben auf der Seite verwenden, um Ihre App innerhalb Teams zu starten.</span><span class="sxs-lookup"><span data-stu-id="582a1-256">You can now use the **Preview in Teams** button at the top of the page to launch your app within Teams.</span></span>

## <a name="see-also"></a><span data-ttu-id="582a1-257">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="582a1-257">See also</span></span>

- [<span data-ttu-id="582a1-258">Erstellen einer Teams-App mit React</span><span class="sxs-lookup"><span data-stu-id="582a1-258">Create a Teams app with React</span></span>](first-app-react.md)
- [<span data-ttu-id="582a1-259">Erstellen einer Teams-App als SharePoint-Webpart</span><span class="sxs-lookup"><span data-stu-id="582a1-259">Create a Teams app as a SharePoint Web Part</span></span>](first-app-spfx.md)
- [<span data-ttu-id="582a1-260">Erstellen einer Unterhaltungs-Bot-App</span><span class="sxs-lookup"><span data-stu-id="582a1-260">Create a conversational bot app</span></span>](first-app-bot.md)
- [<span data-ttu-id="582a1-261">Erstellen einer Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="582a1-261">Create a messaging extension</span></span>](first-message-extension.md)

## <a name="next-step"></a><span data-ttu-id="582a1-262">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="582a1-262">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="582a1-263">Erstellen einer Teams-App als SharePoint-Webpart</span><span class="sxs-lookup"><span data-stu-id="582a1-263">Create a Teams app as a SharePoint Web Part</span></span>](first-app-spfx.md)
