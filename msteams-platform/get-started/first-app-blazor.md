---
title: Erste Schritte – Erstellen Ihrer ersten Teams app mit Blazor
author: adrianhall
description: Erstellen Sie schnell Microsoft Teams App, die ein "Hello, World!" anzeigt. mit dem Microsoft Teams Toolkit und .NET Blazor.
ms.author: adhal
ms.date: 04/27/2021
ms.topic: quickstart
ms.openlocfilehash: 861b6921d7a2092a746ea7dc1399f8aaa523e207
ms.sourcegitcommit: 9cabeaed9baf96c8caeb1497f0bc37abdb787d22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2021
ms.locfileid: "52646782"
---
# <a name="build-and-run-your-first-microsoft-teams-app-with-blazor"></a><span data-ttu-id="ded09-104">Erstellen und Ausführen der ersten Microsoft Teams app mit Blazor</span><span class="sxs-lookup"><span data-stu-id="ded09-104">Build and run your first Microsoft Teams app with Blazor</span></span>

<span data-ttu-id="ded09-105">In diesem Lernprogramm erstellen Sie eine neue Microsoft Teams-App in .NET/Blazor, die eine einfache persönliche App implementiert, um Informationen aus dem Microsoft-Graph.</span><span class="sxs-lookup"><span data-stu-id="ded09-105">In this tutorial, you will create a new Microsoft Teams app in .NET/Blazor that implements a simple personal app to pull information from the Microsoft Graph.</span></span> <span data-ttu-id="ded09-106">(Eine *persönliche App* enthält eine Reihe von Registerkarten, die für die individuelle Verwendung festgelegt sind.)  Im Lernprogramm erfahren Sie mehr über die Struktur einer Teams-App, das lokale Ausführen einer App und die Bereitstellung der App in Azure.</span><span class="sxs-lookup"><span data-stu-id="ded09-106">(A *personal app* includes a set of tabs scoped for individual use.)  During the tutorial, you will learn about the structure of a Teams app, how to run an app locally, and how to deploy the app to Azure.</span></span>

<span data-ttu-id="ded09-107">Die app, die erstellt wird, zeigt grundlegende Benutzerinformationen für den aktuellen Benutzer an.</span><span class="sxs-lookup"><span data-stu-id="ded09-107">The app that is built displays basic user information for the current user.</span></span>  <span data-ttu-id="ded09-108">Wenn die Berechtigung erteilt wird, stellt die App eine Verbindung mit dem Microsoft Graph als aktueller Benutzer, um das vollständige Profil zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="ded09-108">When permission is granted, the app will connect to the Microsoft Graph as the current user to get the complete profile.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="ded09-109">Bevor Sie beginnen:</span><span class="sxs-lookup"><span data-stu-id="ded09-109">Before you begin</span></span>

<span data-ttu-id="ded09-110">Stellen Sie sicher, dass Ihre Entwicklungsumgebung eingerichtet ist, indem Sie die [erforderlichen Komponenten installieren.](prerequisites.md)</span><span class="sxs-lookup"><span data-stu-id="ded09-110">Make sure your development environment is set up by installing the [prerequisites](prerequisites.md)</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ded09-111">Installieren der erforderlichen Komponenten</span><span class="sxs-lookup"><span data-stu-id="ded09-111">Install prerequisites</span></span>](prerequisites.md)

## <a name="create-your-project"></a><span data-ttu-id="ded09-112">Erstellen Ihres Projekts</span><span class="sxs-lookup"><span data-stu-id="ded09-112">Create your project</span></span>

<span data-ttu-id="ded09-113">Verwenden Sie das Teams Toolkit, um Ihr erstes Projekt zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="ded09-113">Use the Teams Toolkit to create your first project:</span></span>

# <a name="visual-studio-2019"></a>[<span data-ttu-id="ded09-114">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="ded09-114">Visual Studio 2019</span></span>](#tab/vs)

1. <span data-ttu-id="ded09-115">Öffnen Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="ded09-115">Open Visual Studio 2019.</span></span>

1. <span data-ttu-id="ded09-116">Wählen **Sie Neues Projekt erstellen aus.**</span><span class="sxs-lookup"><span data-stu-id="ded09-116">Select **Create a new project**.</span></span>

1. <span data-ttu-id="ded09-117">Wählen **Microsoft Teams App** aus, und drücken Sie dann **weiter**.</span><span class="sxs-lookup"><span data-stu-id="ded09-117">Select **Microsoft Teams App**, then press **Next**.</span></span>  <span data-ttu-id="ded09-118">Um die Vorlage zu finden, verwenden Sie den Projekttyp **Microsoft Teams**.</span><span class="sxs-lookup"><span data-stu-id="ded09-118">To help you find the template, use the project type **Microsoft Teams**.</span></span>

1. <span data-ttu-id="ded09-119">Geben Sie dem Projekt und der Projektmappe einen guten Namen, und drücken Sie dann **weiter**.</span><span class="sxs-lookup"><span data-stu-id="ded09-119">Give the project and solution a good name, then press **Next**.</span></span>

1. <span data-ttu-id="ded09-120">Geben Sie den Anwendungsnamen und den Firmennamen an, und drücken Sie dann **erstellen**.</span><span class="sxs-lookup"><span data-stu-id="ded09-120">Provide the application name and company name, then press **Create**.</span></span>  <span data-ttu-id="ded09-121">Der Anwendungsname und der Firmenname werden ihren Endbenutzern angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ded09-121">The application name and company name are displayed to your end users.</span></span>

1. <span data-ttu-id="ded09-122">Ihre Teams-App wird innerhalb weniger Sekunden erstellt.</span><span class="sxs-lookup"><span data-stu-id="ded09-122">Your Teams app will be created within a few seconds.</span></span>  <span data-ttu-id="ded09-123">Nachdem das Projekt erstellt wurde, richten Sie einmaliges Anmelden mit M365 ein:</span><span class="sxs-lookup"><span data-stu-id="ded09-123">Once the project is created, set up single sign-on with M365:</span></span>

   - <span data-ttu-id="ded09-124">Wählen **Project**  >  **TeamsFx**  >  **Configure for SSO...** aus.</span><span class="sxs-lookup"><span data-stu-id="ded09-124">Select **Project** > **TeamsFx** > **Configure for SSO...**.</span></span>
   - <span data-ttu-id="ded09-125">Wenn Sie dazu aufgefordert werden, melden Sie sich bei Ihrem M365-Administratorkonto an.</span><span class="sxs-lookup"><span data-stu-id="ded09-125">When prompted, sign in to your M365 administrator account.</span></span>

# <a name="command-line"></a>[<span data-ttu-id="ded09-126">Befehlszeile</span><span class="sxs-lookup"><span data-stu-id="ded09-126">Command line</span></span>](#tab/cli)

1. <span data-ttu-id="ded09-127">Öffnen Sie ein Terminal, und wählen Sie das Verzeichnis aus, in dem Sie das Projekt erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="ded09-127">Open a Terminal and select the directory where you wish to create the project.</span></span>

1. <span data-ttu-id="ded09-128">Führen `dotnet new -i` Sie aus, um die Vorlage von NuGet:</span><span class="sxs-lookup"><span data-stu-id="ded09-128">Run `dotnet new -i` to install the template from NuGet:</span></span>

   ``` bash
   dotnet new -i Microsoft.TeamsApp.Blazor
   ```

   <span data-ttu-id="ded09-129">Sie müssen dies nur beim ersten Mal oder beim Aktualisieren der Vorlage tun.</span><span class="sxs-lookup"><span data-stu-id="ded09-129">You only need to do this the first time or when updating the template.</span></span>

1. <span data-ttu-id="ded09-130">Erstellen eines Verzeichnisses:</span><span class="sxs-lookup"><span data-stu-id="ded09-130">Create a directory:</span></span>

   ``` bash
   mkdir helloworld
   ```

1. <span data-ttu-id="ded09-131">Führen `dotnet new` Sie aus, um ein neues Projekt zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="ded09-131">Run `dotnet new` to create a new project:</span></span>

   ``` bash
   dotnet new teamsapp --shortName my-teams-app --companyName "My Company"
   ```

1. <span data-ttu-id="ded09-132">Konfigurieren Sie nach dem Gerüst das Projekt für Teams Bereitstellung:</span><span class="sxs-lookup"><span data-stu-id="ded09-132">Once scaffolded, configure the project for Teams deployment:</span></span>

   ``` bash
   teamsfx init
   ```

<span data-ttu-id="ded09-133">Sie können die Lösung nun in einem Visual Studio Debuggen öffnen.</span><span class="sxs-lookup"><span data-stu-id="ded09-133">You can now open the solution in Visual Studio for debugging.</span></span>

---

## <a name="take-a-tour-of-the-source-code"></a><span data-ttu-id="ded09-134">Machen Sie einen Rundgang durch den Quellcode</span><span class="sxs-lookup"><span data-stu-id="ded09-134">Take a tour of the source code</span></span>

<span data-ttu-id="ded09-135">Wenn Sie diesen Abschnitt vorerst überspringen möchten, können Sie [Ihre App lokal ausführen.](#run-your-app-locally)</span><span class="sxs-lookup"><span data-stu-id="ded09-135">If you wish to skip this section for now, you can [run your app locally](#run-your-app-locally).</span></span>

<span data-ttu-id="ded09-136">Sobald Teams Toolkit Ihr Projekt konfiguriert hat, verfügen Sie über die Komponenten zum Erstellen einer einfachen persönlichen App für Teams.</span><span class="sxs-lookup"><span data-stu-id="ded09-136">Once the Teams Toolkit configures your project, you have the components to build a basic personal app for Teams.</span></span> <span data-ttu-id="ded09-137">Die Projektverzeichnissen und -dateien werden im Bereich Projektmappen-Explorer von Visual Studio 2019 angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ded09-137">The project directories and files display in the Solution Explorer area of Visual Studio 2019.</span></span>

:::image type="content" source="../assets/images/teams-toolkit-v2/blazor-file-layout.png" alt-text="Screenshot mit App-Projektdateien für eine persönliche App in Visual Studio 2019.":::

- <span data-ttu-id="ded09-139">Die App-Symbole werden als PNG-Dateien in `color.png` und `outline.png` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="ded09-139">The app icons are stored as PNG files in `color.png` and `outline.png`.</span></span>
- <span data-ttu-id="ded09-140">Das App-Manifest für die Veröffentlichung über das Entwicklerportal für Teams wird in `Properties/manifest.json` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="ded09-140">The app manifest for publishing through the Developer Portal for Teams is stored in `Properties/manifest.json`.</span></span>
- <span data-ttu-id="ded09-141">Zur Unterstützung der Authentifizierung wird ein `Controllers/BackendController.cs` Back-End-Controller bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="ded09-141">A backend controller is provided in `Controllers/BackendController.cs` for assisting with authentication.</span></span>

<span data-ttu-id="ded09-142">Da Sie während des Setups eine Tab-App erstellt haben, erstellt das Teams Toolkit einen Gerüst für den erforderlichen Code für eine einfache Registerkarte als [Blazor Server](/aspnet/core/blazor).</span><span class="sxs-lookup"><span data-stu-id="ded09-142">Since you created a tab app during setup, the Teams Toolkit scaffolds all the necessary code for a basic tab as a [Blazor Server](/aspnet/core/blazor).</span></span>

- <span data-ttu-id="ded09-143">`Pages/Tab.razor` ist der Einstiegspunkt der Front-End-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="ded09-143">`Pages/Tab.razor` is the front-end application's entry point.</span></span>
- <span data-ttu-id="ded09-144">`TeamsFx.cs`und `JS/src/index.js` wird zum Initialisieren der Kommunikation mit dem Teams verwendet.</span><span class="sxs-lookup"><span data-stu-id="ded09-144">`TeamsFx.cs` and `JS/src/index.js` is used for initializing communications with the Teams host.</span></span>

<span data-ttu-id="ded09-145">Sie können Back-End-Funktionen hinzufügen, indem Sie ASP.NET Core Ihrer Anwendung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ded09-145">You can add backend functionality by adding additional ASP.NET Core controllers to your application.</span></span>

## <a name="run-your-app-locally"></a><span data-ttu-id="ded09-146">Lokales Ausführen der App</span><span class="sxs-lookup"><span data-stu-id="ded09-146">Run your app locally</span></span>

<span data-ttu-id="ded09-147">Teams Mit toolkit können Sie Ihre App lokal ausführen.</span><span class="sxs-lookup"><span data-stu-id="ded09-147">Teams Toolkit allows you to run your app locally.</span></span>  <span data-ttu-id="ded09-148">Dies besteht aus mehreren Teilen, die erforderlich sind, um die richtige Infrastruktur zur Verfügung zu stellen, die Teams erwartet:</span><span class="sxs-lookup"><span data-stu-id="ded09-148">This consists of several parts that are necessary to provide the correct infrastructure that Teams expects:</span></span>

- <span data-ttu-id="ded09-149">Eine Anwendung wird mit Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="ded09-149">An application is registered with Azure Active Directory.</span></span>  <span data-ttu-id="ded09-150">Diese Anwendung verfügt über Berechtigungen, die dem Speicherort zugeordnet sind, von dem die App geladen wird, und allen Back-End-Ressourcen, auf die sie zu zugegriffen hat.</span><span class="sxs-lookup"><span data-stu-id="ded09-150">This application has permissions associated with the location that the app is loaded from and any backend resources it accesses.</span></span>
- <span data-ttu-id="ded09-151">Eine Web-API wird (über IIS Express) gehostet, um Authentifizierungsaufgaben zu unterstützen und als Proxy zwischen der App und Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="ded09-151">A web API is hosted (via IIS Express) to assist with authentication tasks, acting as a proxy between the app and Azure Active Directory.</span></span>  
- <span data-ttu-id="ded09-152">Ein App-Manifest wird generiert und ist im Entwicklerportal für Teams.</span><span class="sxs-lookup"><span data-stu-id="ded09-152">An app manifest is generated and exists in the Developer Portal for Teams.</span></span>  <span data-ttu-id="ded09-153">Teams verwendet das App-Manifest, um verbundene Clients zu informieren, von wo aus die App geladen werden soll.</span><span class="sxs-lookup"><span data-stu-id="ded09-153">Teams uses the app manifest to tell connected clients where to load the app from.</span></span>

<span data-ttu-id="ded09-154">Sobald dies geschehen ist, kann die App innerhalb des Teams geladen werden.</span><span class="sxs-lookup"><span data-stu-id="ded09-154">Once this is done, the app can be loaded within the Teams client.</span></span>  <span data-ttu-id="ded09-155">Wir verwenden den Teams-Webclient, damit der HTML-, CSS- und JavaScript-Code in einer standardmäßigen Webentwicklungsumgebung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ded09-155">We use the Teams web client so that we can see the HTML, CSS, and JavaScript code within a standard web development environment.</span></span>

<span data-ttu-id="ded09-156">So erstellen und führen Sie Ihre App lokal aus:</span><span class="sxs-lookup"><span data-stu-id="ded09-156">To build and run your app locally:</span></span>

1. <span data-ttu-id="ded09-157">Drücken Visual Studio Code **F5,** um die Anwendung im Debugmodus ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="ded09-157">From Visual Studio Code, press **F5** to run your application in debug mode.</span></span>

1. <span data-ttu-id="ded09-158">Installieren Sie auf Wunsch das selbst signierte SSL-Zertifikat für das lokale Debuggen.</span><span class="sxs-lookup"><span data-stu-id="ded09-158">If requested, install the self-signed SSL certificate for local debugging.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/ssl-prompt.png" alt-text="Screenshot, der zeigt, wie die Aufforderung zum Installieren eines SSL-Zertifikats angezeigt wird, Teams die Anwendung von localhost laden zu können.":::

1. <span data-ttu-id="ded09-160">Teams werden in einem Webbrowser geladen, und Sie werden zur Anmeldung aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="ded09-160">Teams will be loaded in a web browser, and you will be prompted to sign in.</span></span> <span data-ttu-id="ded09-161">Wenn Sie aufgefordert werden, Microsoft Teams öffnen, wählen Sie Abbrechen aus, um im Browser zu verbleiben.</span><span class="sxs-lookup"><span data-stu-id="ded09-161">If prompted to open Microsoft Teams, select Cancel to remain within the browser.</span></span> <span data-ttu-id="ded09-162">Melden Sie sich mit Ihrem M365-Konto an.</span><span class="sxs-lookup"><span data-stu-id="ded09-162">Sign in with your M365 account.</span></span>
1. <span data-ttu-id="ded09-163">Wenn Sie aufgefordert werden, die App auf Teams, drücken Sie **hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="ded09-163">When prompted to install the app onto Teams, press **Add**.</span></span>

<span data-ttu-id="ded09-164">Ihre App wird nun angezeigt:</span><span class="sxs-lookup"><span data-stu-id="ded09-164">Your app will now be displayed:</span></span>

:::image type="content" source="../assets/images/teams-toolkit-v2/blazor-completed-app.png" alt-text="Screenshot der abgeschlossenen App":::

<span data-ttu-id="ded09-166">Sie können normale Debugaktivitäten so tun, als wäre dies eine andere Webanwendung (z. B. festlegen von Haltepunkten).</span><span class="sxs-lookup"><span data-stu-id="ded09-166">You can do normal debugging activities as if this were any other web application (such as setting breakpoints).</span></span> <span data-ttu-id="ded09-167">Die App unterstützt das Laden von Hot Reloads.</span><span class="sxs-lookup"><span data-stu-id="ded09-167">The app supports hot reloading.</span></span>  <span data-ttu-id="ded09-168">Wenn Sie eine Datei innerhalb des Projekts ändern, wird die Seite erneut geladen.</span><span class="sxs-lookup"><span data-stu-id="ded09-168">If you change any file within the project, the page will be reloaded.</span></span>

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="ded09-169">Erfahren Sie, was geschieht, wenn Sie Ihre App lokal im Debugger ausführen.</span><span class="sxs-lookup"><span data-stu-id="ded09-169">Learn what happens when you run your app locally in the debugger.</span></span></summary>

<span data-ttu-id="ded09-170">Wenn Sie F5 gedrückt haben, Teams Toolkit:</span><span class="sxs-lookup"><span data-stu-id="ded09-170">When you pressed F5, the Teams Toolkit:</span></span>

1. <span data-ttu-id="ded09-171">Registriert Ihre Anwendung bei Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="ded09-171">Registered your application with Azure Active Directory.</span></span>
1. <span data-ttu-id="ded09-172">Registriert Ihre Anwendung für das "Seitenladen" in Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="ded09-172">Registered your application for "side loading" in Microsoft Teams.</span></span>
1. <span data-ttu-id="ded09-173">Das Anwendungs-Back-End wurde lokal ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="ded09-173">Started your application backend running locally.</span></span>
1. <span data-ttu-id="ded09-174">Das Front-End der Anwendung wurde lokal gestartet.</span><span class="sxs-lookup"><span data-stu-id="ded09-174">Started your application front-end hosted locally.</span></span>
1. <span data-ttu-id="ded09-175">Die Microsoft Teams in einem Webbrowser mit einem Befehl gestartet, um Teams anweisen, die Anwendung seitlich zu laden (die URL wird im Anwendungsmanifest registriert).</span><span class="sxs-lookup"><span data-stu-id="ded09-175">Started Microsoft Teams in a web browser with a command to instruct Teams to side load the application (the URL is registered inside the application manifest).</span></span>

</details>

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="ded09-176">Erfahren Sie, wie Sie häufige Probleme beim lokalen Ausführen Ihrer App beheben.</span><span class="sxs-lookup"><span data-stu-id="ded09-176">Learn how to troubleshoot common issues when running your app locally.</span></span></summary>

<span data-ttu-id="ded09-177">Um Ihre App erfolgreich in Teams ausführen zu können, müssen Sie über ein Microsoft 365-Entwicklungskonto verfügen, das das appseitige Laden zulässt.</span><span class="sxs-lookup"><span data-stu-id="ded09-177">To successfully run your app in Teams, you must have a Microsoft 365 development account that allows app side loading.</span></span> <span data-ttu-id="ded09-178">Weitere Informationen zum Öffnen von Konten finden Sie unter [Voraussetzungen](prerequisites.md#enable-sideloading).</span><span class="sxs-lookup"><span data-stu-id="ded09-178">For more information on account opening, see [Prerequisites](prerequisites.md#enable-sideloading).</span></span>

</details>

## <a name="deploy-your-app-to-azure"></a><span data-ttu-id="ded09-179">Bereitstellen Ihrer App in Azure</span><span class="sxs-lookup"><span data-stu-id="ded09-179">Deploy your app to Azure</span></span>

<span data-ttu-id="ded09-180">Die Bereitstellung besteht aus zwei Schritten.</span><span class="sxs-lookup"><span data-stu-id="ded09-180">Deployment consists of two steps.</span></span>  <span data-ttu-id="ded09-181">Zuerst werden erforderliche Cloudressourcen erstellt (auch als Bereitstellung bezeichnet), dann wird der Code, aus dem Ihre App besteht, in die erstellten Cloudressourcen kopiert.</span><span class="sxs-lookup"><span data-stu-id="ded09-181">First, necessary cloud resources are created (also known as provisioning), then the code that makes up your app is copied into the created cloud resources.</span></span>

> <span data-ttu-id="ded09-182">**Vorschau**</span><span class="sxs-lookup"><span data-stu-id="ded09-182">**PREVIEW**</span></span>
>
> <span data-ttu-id="ded09-183">Die Unterstützung für Blazor-Apps ist neu in Teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="ded09-183">Support for Blazor apps is new in Teams Toolkit.</span></span>  <span data-ttu-id="ded09-184">Bereitstellung und Bereitstellung erfolgt mit einer Kombination aus Visual Studio 2019 und dem Entwicklerportal für Teams.</span><span class="sxs-lookup"><span data-stu-id="ded09-184">Provisioning and deployment are done with a combination of Visual Studio 2019 and the Developer Portal for Teams.</span></span>

## <a name="provision-and-deploy-your-app-to-azure-app-service"></a><span data-ttu-id="ded09-185">Bereitstellen und Bereitstellen Ihrer App im Azure App Service</span><span class="sxs-lookup"><span data-stu-id="ded09-185">Provision and deploy your app to Azure App Service</span></span>

1. <span data-ttu-id="ded09-186">Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Veröffentlichen** aus (oder verwenden Sie das **Menüelement Veröffentlichen**  >   erstellen).</span><span class="sxs-lookup"><span data-stu-id="ded09-186">In Solution Explorer, right-click the project node and choose **Publish** (or use the **Build** > **Publish** menu item).</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish1.png" alt-text="Auswählen des Veröffentlichungsvorgangs für das Projekt":::

1. <span data-ttu-id="ded09-188">Wählen Sie **im Fenster** Veröffentlichen die Option **Azure aus.**</span><span class="sxs-lookup"><span data-stu-id="ded09-188">In the **Publish** window, select **Azure**.</span></span>  <span data-ttu-id="ded09-189">Drücken Sie **weiter**.</span><span class="sxs-lookup"><span data-stu-id="ded09-189">Press **Next**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish2.png" alt-text="Auswählen von Azure als Veröffentlichungsziel":::

1. <span data-ttu-id="ded09-191">Wählen **Sie Azure App Service (Windows) aus.**</span><span class="sxs-lookup"><span data-stu-id="ded09-191">Select **Azure App Service (Windows)**.</span></span>  <span data-ttu-id="ded09-192">Drücken Sie **weiter**.</span><span class="sxs-lookup"><span data-stu-id="ded09-192">Press **Next**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish3.png" alt-text="Auswählen von Azure App Service als Veröffentlichungsziel":::

1. <span data-ttu-id="ded09-194">Wählen **+** Sie diese Option aus, um eine neue App -Dienstinstanz zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="ded09-194">Select **+** to create a new App Service instance.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish4.png" alt-text="Erstellen Sie eine neue Instanz.":::

1. <span data-ttu-id="ded09-196">Im Dialogfeld **App-Dienst erstellen (Windows)** werden die Eingabefelder **Name,** **Abonnementname,** **Ressourcengruppe** und **Hostingplan** aufgefüllt.</span><span class="sxs-lookup"><span data-stu-id="ded09-196">In the **Create App Service (Windows)** dialog, the **Name**, **Subscription name**, **Resource Group**, and **Hosting Plan** entry fields are populated.</span></span> <span data-ttu-id="ded09-197">Wenn Sie bereits einen App-Dienst ausgeführt haben, werden vorhandene Einstellungen ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="ded09-197">If you have already got an App Service running, existing settings will be selected.</span></span>  <span data-ttu-id="ded09-198">Sie können eine neue Ressourcengruppe und einen neuen Hostingplan erstellen (empfohlen).</span><span class="sxs-lookup"><span data-stu-id="ded09-198">You can opt to create a new resource group and hosting plan (Recommended).</span></span>  <span data-ttu-id="ded09-199">Wenn Sie bereit sind, wählen Sie **Erstellen aus.**</span><span class="sxs-lookup"><span data-stu-id="ded09-199">When ready, select **Create**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish5.png" alt-text="Auswählen von Hostingplan und Abonnement":::

1. <span data-ttu-id="ded09-201">Im Dialogfeld **Veröffentlichen** wurde die neu erstellte Instanz automatisch ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="ded09-201">In the **Publish** dialog, the newly created instance has been automatically selected.</span></span>  <span data-ttu-id="ded09-202">Wenn Sie bereit sind, wählen Sie **Fertig stellen aus.**</span><span class="sxs-lookup"><span data-stu-id="ded09-202">When ready, select **Finish**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish6.png" alt-text="Wählen Sie die neue Instanz aus.":::

1. <span data-ttu-id="ded09-204">Drücken Sie **das Symbol Bearbeiten** (Bleistift) neben Bereitstellungsmodus, und wählen Sie dann **Eigenständiges aus.** </span><span class="sxs-lookup"><span data-stu-id="ded09-204">Press the **Edit** (pencil) icon next to **Deployment Mode**, then select **Self-contained**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish8.png" alt-text="Wählen Sie den eigenständigen Bereitstellungsmodus aus.":::

1. <span data-ttu-id="ded09-206">Wählen Sie **Veröffentlichen** aus.</span><span class="sxs-lookup"><span data-stu-id="ded09-206">Select **Publish**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish7.png" alt-text="Veröffentlichen Ihrer App im App-Dienst":::

<span data-ttu-id="ded09-208">Visual Studio stellt die App in Ihrem Azure App Service bereit, und die Web-App wird in Ihrem Browser geladen.</span><span class="sxs-lookup"><span data-stu-id="ded09-208">Visual Studio deploys the app to your Azure App Service, and the web app loads in your browser.</span></span>  <span data-ttu-id="ded09-209">Fügen `/tab` Sie am Ende der URL hinzu, um Ihre Seite zu sehen.</span><span class="sxs-lookup"><span data-stu-id="ded09-209">Add `/tab` to the end of the URL to see your page.</span></span>

<span data-ttu-id="ded09-210">Der Bereich **"Projekteigenschaften veröffentlichen"** zeigt die Website-URL und andere Details an.</span><span class="sxs-lookup"><span data-stu-id="ded09-210">The project properties **Publish** pane shows the site URL and other details.</span></span> <span data-ttu-id="ded09-211">Notieren Sie sich die Website-URL.</span><span class="sxs-lookup"><span data-stu-id="ded09-211">Make a note of the site URL.</span></span>

## <a name="create-an-environment-for-your-app"></a><span data-ttu-id="ded09-212">Erstellen einer Umgebung für Ihre App</span><span class="sxs-lookup"><span data-stu-id="ded09-212">Create an environment for your app</span></span>

<span data-ttu-id="ded09-213">Das Entwicklerportal für Teams verwaltet, wo die Registerkarten für Ihre App mit einer Umgebung geladen **werden.**</span><span class="sxs-lookup"><span data-stu-id="ded09-213">The Developer Portal for Teams manages where the tabs for your app are loaded from with an **Environment**.</span></span>  <span data-ttu-id="ded09-214">So erstellen Sie eine Umgebung:</span><span class="sxs-lookup"><span data-stu-id="ded09-214">To create an environment:</span></span>

1. <span data-ttu-id="ded09-215">Öffnen Sie [das Entwicklerportal für Teams](https://dev.teams.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="ded09-215">Open the [Developer Portal for Teams](https://dev.teams.microsoft.com).</span></span>  <span data-ttu-id="ded09-216">Melden Sie sich mit Ihrem M365-Administratorkonto an.</span><span class="sxs-lookup"><span data-stu-id="ded09-216">Sign in with your M365 administrative account.</span></span>

1. <span data-ttu-id="ded09-217">Wählen Sie in der Seitenleiste **Apps aus.**</span><span class="sxs-lookup"><span data-stu-id="ded09-217">From the sidebar, select **Apps**.</span></span>

1. <span data-ttu-id="ded09-218">Wenn Sie nur über eine App verfügen, wird sie automatisch ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="ded09-218">If you only have one app, it will be automatically selected.</span></span>  <span data-ttu-id="ded09-219">Wenn nicht, wählen Sie Ihre App aus der Liste aus.</span><span class="sxs-lookup"><span data-stu-id="ded09-219">If not, select your app from the list.</span></span>

1. <span data-ttu-id="ded09-220">Wählen Sie **Umgebungen aus.**</span><span class="sxs-lookup"><span data-stu-id="ded09-220">Select **Environments**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments1.png" alt-text="Auswählen von Umgebungen":::

1. <span data-ttu-id="ded09-222">Wählen **Sie Erstellen Ihrer ersten Umgebung aus.**</span><span class="sxs-lookup"><span data-stu-id="ded09-222">Select **Create your first environment**.</span></span>

1. <span data-ttu-id="ded09-223">Geben Sie einen Namen für Ihre Umgebung ein, und drücken Sie dann **hinzufügen**; z. B. _Production_.</span><span class="sxs-lookup"><span data-stu-id="ded09-223">Enter a name for your environment, then press **Add**; for example _Production_.</span></span>

1. <span data-ttu-id="ded09-224">Drücken Sie bei Auswahl der neu erstellten Umgebung die **Erste Umgebungsvariable erstellen.**</span><span class="sxs-lookup"><span data-stu-id="ded09-224">With the newly created environment selected, press **Create your first environment variable**.</span></span>

1. <span data-ttu-id="ded09-225">Geben `azure_app_url` Sie für den Namen **ein.**</span><span class="sxs-lookup"><span data-stu-id="ded09-225">Enter `azure_app_url` for the **Name**.</span></span>  <span data-ttu-id="ded09-226">Geben Sie Ihre Azure-Website-URL (ohne `https://` ) als **Wert ein.**</span><span class="sxs-lookup"><span data-stu-id="ded09-226">Enter your Azure site URL (without the `https://`) as the **Value**.</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments2.png" alt-text="Erstellen einer Umgebungsvariablen":::

   <span data-ttu-id="ded09-228">Drücken Sie **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="ded09-228">Press **Add**.</span></span>

## <a name="update-the-app-manifest"></a><span data-ttu-id="ded09-229">Aktualisieren des App-Manifests</span><span class="sxs-lookup"><span data-stu-id="ded09-229">Update the app manifest</span></span>

<span data-ttu-id="ded09-230">Das App-Manifest lädt die Registerkarte über eine `localhost` URL.</span><span class="sxs-lookup"><span data-stu-id="ded09-230">The app manifest is loading the tab from a `localhost` URL.</span></span>  <span data-ttu-id="ded09-231">In diesem Abschnitt passen Sie das App-Manifest an, um die Registerkarte aus der URL zu laden, die in der Umgebung aufgeführt ist, die Sie gerade erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="ded09-231">In this section, you will adjust the app manifest to load the tab from the URL listed within the environment you just created.</span></span>

1. <span data-ttu-id="ded09-232">Wählen Sie auf der Seitenleiste **Grundlegende Informationen aus.**</span><span class="sxs-lookup"><span data-stu-id="ded09-232">From the sidebar, select **Basic information**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments3.png" alt-text="Auswählen grundlegender Informationen":::

1. <span data-ttu-id="ded09-234">Es gibt mehrere Orte im Manifest, die eine `locahost:XXXXX` als Teil einer URL auflisten.</span><span class="sxs-lookup"><span data-stu-id="ded09-234">There are several places within the manifest that list a `locahost:XXXXX` as part of a URL.</span></span>  <span data-ttu-id="ded09-235">Ersetzen Sie alle Vorkommen durch `{{azure_app_url}}` (einschließlich der geschweiften Klammern).</span><span class="sxs-lookup"><span data-stu-id="ded09-235">Replace all occurrences with `{{azure_app_url}}` (including the curly braces).</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments4.png" alt-text="Anpassen grundlegender Informationen für die Umgebung":::

1. <span data-ttu-id="ded09-237">Drücken Sie nach Abschluss des Vorgangs **speichern**.</span><span class="sxs-lookup"><span data-stu-id="ded09-237">When complete, press **Save**.</span></span>

1. <span data-ttu-id="ded09-238">Wählen Sie auf der Seitenleiste Funktionen **aus.**</span><span class="sxs-lookup"><span data-stu-id="ded09-238">From the sidebar, select **Capabilities**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments5.png" alt-text="Auswählen von Funktionen":::

1. <span data-ttu-id="ded09-240">Wählen **Sie Persönliche Registerkarte aus.**</span><span class="sxs-lookup"><span data-stu-id="ded09-240">Select **Personal Tab**.</span></span>
1. <span data-ttu-id="ded09-241">Wählen Sie neben **der Registerkarte Personal** die dreifachen Punkte aus, und wählen Sie dann Bearbeiten **aus.**</span><span class="sxs-lookup"><span data-stu-id="ded09-241">Next to the **Personal Tab**, select the triple dots, then select **Edit**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments6.png" alt-text="Bearbeiten persönlicher Registerkarteneinstellungen":::

1. <span data-ttu-id="ded09-243">Ersetzen Sie die URL durch die Umgebungsvariable in den Feldern **Inhalts-URL** und **Website-URL.**</span><span class="sxs-lookup"><span data-stu-id="ded09-243">Replace the URL with the environment variable within the **Content Url** and **Website Url** fields.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments7.png" alt-text="Bearbeiten von URLs für persönliche Registerkarten":::

1. <span data-ttu-id="ded09-245">Drücken **Sie Update**.</span><span class="sxs-lookup"><span data-stu-id="ded09-245">Press **Update**.</span></span>

1. <span data-ttu-id="ded09-246">Klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="ded09-246">Press **Save**.</span></span>

1. <span data-ttu-id="ded09-247">Wählen Sie auf der Seitenleiste **einmaliges Anmelden aus.**</span><span class="sxs-lookup"><span data-stu-id="ded09-247">From the sidebar, select **Single Sign-On**.</span></span>

1. <span data-ttu-id="ded09-248">Ersetzen Sie `localhost` den innerhalb des **Anwendungs-ID-URI** durch `{{azure_app_url}}` .</span><span class="sxs-lookup"><span data-stu-id="ded09-248">Replace the `localhost` within the **Application ID URI** with `{{azure_app_url}}`.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments8.png" alt-text="Bearbeiten des Anwendungs-ID-URI für einmaliges Anmelden":::

1. <span data-ttu-id="ded09-250">Klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="ded09-250">Press **Save**.</span></span>

1. <span data-ttu-id="ded09-251">Drücken Sie an der Seitenleiste **domänen**.</span><span class="sxs-lookup"><span data-stu-id="ded09-251">From the sidebar, press **Domains**.</span></span>

1. <span data-ttu-id="ded09-252">Drücken **Sie die Taste Domäne hinzufügen.**</span><span class="sxs-lookup"><span data-stu-id="ded09-252">Press **Add a domain**.</span></span>

1. <span data-ttu-id="ded09-253">Wenn sie nicht als gültige Domäne aufgeführt ist, fügen Sie sie als gültige Domäne hinzu, und drücken `{{azure_app_url}}` Sie dann die Taste **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="ded09-253">If `{{azure_app_url}}` is not listed as a valid domain, add it as a valid domain, then press **Add**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments9.png" alt-text="Hinzufügen einer Domäne":::

<span data-ttu-id="ded09-255">Sie können nun die Schaltfläche **Vorschau im Teams** oben auf der Seite verwenden, um Ihre App innerhalb eines Teams.</span><span class="sxs-lookup"><span data-stu-id="ded09-255">You can now use the **Preview in Teams** button at the top of the page to launch your app within Teams.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ded09-256">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="ded09-256">Next steps</span></span>

<span data-ttu-id="ded09-257">Erfahren Sie mehr über andere Methoden zum Erstellen Teams Apps:</span><span class="sxs-lookup"><span data-stu-id="ded09-257">Learn about other methods for creating Teams apps:</span></span>

- [<span data-ttu-id="ded09-258">Erstellen einer Teams App mit React</span><span class="sxs-lookup"><span data-stu-id="ded09-258">Create a Teams app with React</span></span>](first-app-react.md)
- <span data-ttu-id="ded09-259">[Erstellen einer Teams-App](first-app-spfx.md) als SharePoint Web part (Azure nicht erforderlich)</span><span class="sxs-lookup"><span data-stu-id="ded09-259">[Create a Teams app as a SharePoint Web Part](first-app-spfx.md) (Azure not required)</span></span>
- [<span data-ttu-id="ded09-260">Erstellen einer Unterhaltungsbot-App</span><span class="sxs-lookup"><span data-stu-id="ded09-260">Create a conversational bot app</span></span>](first-app-bot.md)
- [<span data-ttu-id="ded09-261">Erstellen einer Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="ded09-261">Create a messaging extension</span></span>](first-message-extension.md)
