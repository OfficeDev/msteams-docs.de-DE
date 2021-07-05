---
title: 'Lernprogramm – Erstellen Ihrer ersten App mit C #'
description: Erfahren Sie, wie Sie mit C# oder .NET mit dem Erstellen Microsoft Teams Apps beginnen.
keywords: Erste Schritte .net c# csharp
ms.custom: scenarios:getting-started; languages:ASP.NET,C#
localization_priority: Normal
ms.topic: tutorial
ms.date: 11/09/2018
ms.openlocfilehash: f63e729400fa74f1675faddbe0b5f8fa101c8824
ms.sourcegitcommit: 9d63611974ba8a7e7f19ceea35e50189a2e90434
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2021
ms.locfileid: "53254344"
---
# <a name="build-your-first-teams-app-using-c"></a><span data-ttu-id="21966-104">Erstellen Ihrer ersten Teams-App mit C #</span><span class="sxs-lookup"><span data-stu-id="21966-104">Build your first Teams app using C#</span></span>

<span data-ttu-id="21966-105">In diesem Lernprogramm erfahren Sie, wie Sie Ihre erste Microsoft Teams-App mit .NET oder C# erstellen.</span><span class="sxs-lookup"><span data-stu-id="21966-105">In this tutorial, you will learn how to build your very first Microsoft Teams app using .NET or C#.</span></span> <span data-ttu-id="21966-106">Außerdem werden Sie durch die folgenden Schritte geführt:</span><span class="sxs-lookup"><span data-stu-id="21966-106">It also walks you through the steps to:</span></span>

1. [<span data-ttu-id="21966-107">Vorbereiten der Umgebung</span><span class="sxs-lookup"><span data-stu-id="21966-107">Prepare your environment</span></span>](#prepare-your-environment)
1. [<span data-ttu-id="21966-108">Voraussetzungen abrufen</span><span class="sxs-lookup"><span data-stu-id="21966-108">Get prerequisites</span></span>](#GetPrerequisites)
1. [<span data-ttu-id="21966-109">Beispiel herunterladen</span><span class="sxs-lookup"><span data-stu-id="21966-109">Download the sample</span></span>](#DownloadSample)
1. [<span data-ttu-id="21966-110">Erstellen und Ausführen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="21966-110">Build and run the sample</span></span>](#BuildRun)
1. [<span data-ttu-id="21966-111">Hosten der Beispiel-App</span><span class="sxs-lookup"><span data-stu-id="21966-111">Host the sample app</span></span>](#hostsample)
1. [<span data-ttu-id="21966-112">Aktualisieren der Anmeldeinformationen für Ihre gehostete App</span><span class="sxs-lookup"><span data-stu-id="21966-112">Update the credentials for your hosted app</span></span>](#updatecredentials)
1. [<span data-ttu-id="21966-113">Konfigurieren der Registerkarte "App"</span><span class="sxs-lookup"><span data-stu-id="21966-113">Configure the app tab</span></span>](#configureapptab)

<a name="prepare-your-environment"></a>
[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="GetPrerequisites"></a>

## <a name="get-prerequisites"></a><span data-ttu-id="21966-114">Voraussetzungen abrufen</span><span class="sxs-lookup"><span data-stu-id="21966-114">Get prerequisites</span></span>

<span data-ttu-id="21966-115">Um dieses Lernprogramm abzuschließen, müssen Sie die folgenden Tools installieren:</span><span class="sxs-lookup"><span data-stu-id="21966-115">To complete this tutorial, you need to install the following tools:</span></span>

- [<span data-ttu-id="21966-116">Installieren von Git</span><span class="sxs-lookup"><span data-stu-id="21966-116">Install Git</span></span>](https://git-scm.com/downloads)
- [<span data-ttu-id="21966-117">Installieren von Visual Studio</span><span class="sxs-lookup"><span data-stu-id="21966-117">Install Visual Studio</span></span>](https://www.visualstudio.com/downloads/)

<span data-ttu-id="21966-118">Sie können die kostenlose Community-Edition von Visual Studio installieren.</span><span class="sxs-lookup"><span data-stu-id="21966-118">You can install the free community edition of Visual Studio.</span></span> <span data-ttu-id="21966-119">Wenn es während der Installation eine Option zum Hinzufügen `git` zum Pfad gibt, wählen Sie ihn aus.</span><span class="sxs-lookup"><span data-stu-id="21966-119">During installation, if there is an option to add `git` to the path, select it.</span></span> <span data-ttu-id="21966-120">Führen Sie in einem Terminalfenster den folgenden Befehl aus, um die Installation zu `git` überprüfen:</span><span class="sxs-lookup"><span data-stu-id="21966-120">In a terminal window, run the following command to verify your `git` installation:</span></span>

```bash
$ git --version
git version 2.17.1.windows.2

```

> [!NOTE]
> <span data-ttu-id="21966-121">Verwenden Sie ein geeignetes Terminalfenster auf Ihrer Plattform.</span><span class="sxs-lookup"><span data-stu-id="21966-121">Use a suitable terminal window on your platform.</span></span> <span data-ttu-id="21966-122">Diese Beispiele verwenden Git Bash, können aber auf den meisten Plattformen ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="21966-122">These examples use Git Bash but can be run on most platforms.</span></span>

<span data-ttu-id="21966-123">Öffnen Sie die neueste Version von Visual Studio, und installieren Sie alle Updates.</span><span class="sxs-lookup"><span data-stu-id="21966-123">Open the latest version of Visual Studio and install any updates.</span></span>

<span data-ttu-id="21966-124">Sie können dasselbe Terminalfenster verwenden, um die Befehle in diesem Lernprogramm auszuführen.</span><span class="sxs-lookup"><span data-stu-id="21966-124">You can use the same terminal window to run the commands in this tutorial.</span></span>

<a name="DownloadSample"></a>

## <a name="download-the-sample"></a><span data-ttu-id="21966-125">Beispiel herunterladen</span><span class="sxs-lookup"><span data-stu-id="21966-125">Download the sample</span></span>

<span data-ttu-id="21966-126">Sie können mit einem einfachen [Hello, World beginnen!](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-hello-world/csharp)</span><span class="sxs-lookup"><span data-stu-id="21966-126">You can get started with a simple [Hello, World!](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-hello-world/csharp)</span></span> <span data-ttu-id="21966-127">Beispiel in C#.</span><span class="sxs-lookup"><span data-stu-id="21966-127">sample in C#.</span></span> <span data-ttu-id="21966-128">Führen Sie in einem Terminalfenster den folgenden Befehl aus, um das Beispiel-Repository auf Ihrem Computer zu klonen:</span><span class="sxs-lookup"><span data-stu-id="21966-128">In a terminal window, run the following command to clone the sample repository to your computer:</span></span>

```bash
git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
```

> [!TIP]
> <span data-ttu-id="21966-129">Sie können dieses [Repository verzweigen,](https://github.com/OfficeDev/Microsoft-Teams-Samples) um Ihre Änderungen zu ändern und in GitHub zu speichern. [](https://help.github.com/articles/fork-a-repo/)</span><span class="sxs-lookup"><span data-stu-id="21966-129">You can [fork](https://help.github.com/articles/fork-a-repo/) this [repo](https://github.com/OfficeDev/Microsoft-Teams-Samples) to modify and save your changes to GitHub.</span></span>

<a name="BuildRun"></a>

## <a name="build-and-run-the-sample"></a><span data-ttu-id="21966-130">Erstellen und Ausführen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="21966-130">Build and run the sample</span></span>

<span data-ttu-id="21966-131">Sie können das Geklonte erstellen und ausführen.</span><span class="sxs-lookup"><span data-stu-id="21966-131">You can build and run the smaple after it is cloned.</span></span> 

<span data-ttu-id="21966-132">**So erstellen Sie das geklonte Beispiel und führen es aus**</span><span class="sxs-lookup"><span data-stu-id="21966-132">**To build and run the cloned sample**</span></span>

1. <span data-ttu-id="21966-133">Öffnen Sie die Projektmappendatei **"Microsoft.Teams". Samples.HelloWorld.sln** aus dem **Microsoft-Teams-Samples/samples/app-hello-world/csharp-Verzeichnis** des Beispiels.</span><span class="sxs-lookup"><span data-stu-id="21966-133">Open the solution file **Microsoft.Teams.Samples.HelloWorld.sln** from the **Microsoft-Teams-Samples/samples/app-hello-world/csharp** directory of the sample.</span></span>
1. <span data-ttu-id="21966-134">Wählen Sie im Menü "Erstellen" die Option **"Projektmappe** **erstellen"** aus.</span><span class="sxs-lookup"><span data-stu-id="21966-134">Select **Build Solution** from the **Build** menu.</span></span>
1. <span data-ttu-id="21966-135">Wählen Sie **F5** aus, oder wählen Sie im Menü **"Debuggen"** die Option **"Debuggen starten"** aus, um das Beispiel auszuführen.</span><span class="sxs-lookup"><span data-stu-id="21966-135">Select the **F5** key, or select **Start Debugging** from the **Debug** menu to run the sample.</span></span>

    <span data-ttu-id="21966-136">Wenn die App gestartet wird, wird ein Browserfenster geöffnet, in dem der Stamm der App gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="21966-136">When the app starts, a browser window opens with the root of the app launched.</span></span> <span data-ttu-id="21966-137">Sie können die folgenden URLs aufrufen, um zu überprüfen, ob alle App-URLs geladen werden:</span><span class="sxs-lookup"><span data-stu-id="21966-137">You can go to the following URLs to verify that all the app URLs are loading:</span></span>

    - `https://localhost:44327/`
    - `https://localhost:44327/hello`
    - `https://localhost:44327/first`
    - `https://localhost:44327/second`

    > [!Note]
    > <span data-ttu-id="21966-138">Wenn ein Fehler angezeigt wird, aktualisieren Sie `Could not find a part of the path … bin\roslyn\csc.exe` das Paket mit dem Befehl `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r` .</span><span class="sxs-lookup"><span data-stu-id="21966-138">If you receive an error `Could not find a part of the path … bin\roslyn\csc.exe`, update the package with the command `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r`.</span></span> <span data-ttu-id="21966-139">Weitere Informationen finden Sie in [dieser Frage auf Stack Overflow](https://stackoverflow.com/questions/32780315).</span><span class="sxs-lookup"><span data-stu-id="21966-139">For more information, see [this question on Stack Overflow](https://stackoverflow.com/questions/32780315).</span></span>

    <a name="hostsample"></a>
    ## <a name="deploy-your-sample-app"></a><span data-ttu-id="21966-140">Bereitstellen Ihrer Beispiel-App</span><span class="sxs-lookup"><span data-stu-id="21966-140">Deploy your sample app</span></span>

    <span data-ttu-id="21966-141">Apps in Microsoft Teams sind Webanwendungen, die eine oder mehrere Funktionen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="21966-141">Apps in Microsoft Teams are web applications that provide one or more capabilities.</span></span> <span data-ttu-id="21966-142">Damit die Teams Plattform Ihre App laden kann, muss Ihre App im Internet verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="21966-142">For the Teams platform to load your app, your app must be available on the internet.</span></span> <span data-ttu-id="21966-143">Dazu müssen Sie Ihre App hosten.</span><span class="sxs-lookup"><span data-stu-id="21966-143">To do this, you need to host your app.</span></span> <span data-ttu-id="21966-144">Sie können es entweder kostenlos in Microsoft Azure hosten oder mithilfe von `ngrok` .</span><span class="sxs-lookup"><span data-stu-id="21966-144">You can either host it in Microsoft Azure for free or create a tunnel to the local process on your computer using `ngrok`.</span></span> <span data-ttu-id="21966-145">Notieren Sie sich nach dem Hosten der App die Stamm-URL, z. `https://yourteamsapp.ngrok.io` B. oder `https://yourteamsapp.azurewebsites.net` .</span><span class="sxs-lookup"><span data-stu-id="21966-145">After you host your app, make a note of its root URL, such as `https://yourteamsapp.ngrok.io` or `https://yourteamsapp.azurewebsites.net`.</span></span>

### <a name="tunnel-using-ngrok"></a><span data-ttu-id="21966-146">Tunnel mit ngrok</span><span class="sxs-lookup"><span data-stu-id="21966-146">Tunnel using ngrok</span></span>

<span data-ttu-id="21966-147">Für schnelle Tests können Sie die App auf Ihrem Computer ausführen und einen Tunnel über einen Webendpunkt erstellen.</span><span class="sxs-lookup"><span data-stu-id="21966-147">For quick testing, you can run the app on your computer and create a tunnel to it through a web endpoint.</span></span> <span data-ttu-id="21966-148">[`ngrok`](https://ngrok.com) ist ein kostenloses Tool, mit dem Sie eine Webadresse abrufen können, `https://d0ac14a5.ngrok.io` z. B. .</span><span class="sxs-lookup"><span data-stu-id="21966-148">[`ngrok`](https://ngrok.com) is a free tool with which you can get a web address, such as `https://d0ac14a5.ngrok.io`.</span></span> <span data-ttu-id="21966-149">Sie können ngrok [herunterladen und installieren](https://ngrok.com/download) und zu einem Speicherort in Ihrer `PATH` hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="21966-149">You can [download and install](https://ngrok.com/download) ngrok and add it to a location in your `PATH`.</span></span>

<span data-ttu-id="21966-150">Öffnen Sie nach der Installation `ngrok` ein neues Terminalfenster, und führen Sie den folgenden Befehl aus, um einen Tunnel zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="21966-150">After you install `ngrok`, open a new terminal window and run the following command to create a tunnel:</span></span>

```bash
ngrok http 44327 -host-header=localhost:44327
```

<span data-ttu-id="21966-151">`Ngrok` antwortet auf Anforderungen aus dem Internet und leitet sie an Ihre App weiter, die an Port 44327 ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="21966-151">`Ngrok` responds to requests from the internet and routes them to your app running on port 44327.</span></span> 

<span data-ttu-id="21966-152">**So überprüfen Sie die Antwort**</span><span class="sxs-lookup"><span data-stu-id="21966-152">**To verify the response**</span></span>

1. <span data-ttu-id="21966-153">Öffnen Sie Ihren Browser, und navigieren Sie zu `https://d0ac14a5.ngrok.io/hello`.</span><span class="sxs-lookup"><span data-stu-id="21966-153">Open your browser and go to `https://d0ac14a5.ngrok.io/hello`.</span></span> <span data-ttu-id="21966-154">Dadurch wird die Hello-Seite Ihrer App geladen.</span><span class="sxs-lookup"><span data-stu-id="21966-154">This will load your app's Hello page.</span></span>
1. <span data-ttu-id="21966-155">Verwenden Sie anstelle der in Schritt 1 erwähnten URL die Weiterleitungsadresse, die `ngrok` in Ihrer Konsolensitzung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="21966-155">Instead of the URL mentioned in Step 1, use the forwarding address displayed by `ngrok` in your console session.</span></span>
    > [!NOTE]
    > <span data-ttu-id="21966-156">Wenn Sie im [Build- und Ausführungsschritt](#build-and-run-the-sample) einen anderen Port verwendet haben, stellen Sie sicher, dass Sie die gleiche Portnummer zum Einrichten des `ngrok` Tunnels verwenden.</span><span class="sxs-lookup"><span data-stu-id="21966-156">If you have used a different port in the [build and run](#build-and-run-the-sample) step, ensure you use the same port number to setup the `ngrok` tunnel.</span></span>
    > [!TIP]
    > <span data-ttu-id="21966-157">Es empfiehlt sich, in einem anderen Terminalfenster ausgeführt zu `ngrok` werden.</span><span class="sxs-lookup"><span data-stu-id="21966-157">It is a good idea to run `ngrok` in a different terminal window.</span></span> <span data-ttu-id="21966-158">Dies geschieht, um die `ngrok` Ausführung ohne Beeinträchtigung der App aufzuhalten.</span><span class="sxs-lookup"><span data-stu-id="21966-158">This is done to keep `ngrok` from running without interfering with the app.</span></span> <span data-ttu-id="21966-159">Sie müssen die App beenden, neu erstellen und erneut ausführen.</span><span class="sxs-lookup"><span data-stu-id="21966-159">You have to stop, rebuild, and rerun the app.</span></span> <span data-ttu-id="21966-160">Die `ngrok` Sitzung enthält nützliche Debuginformationen in diesem Fenster.</span><span class="sxs-lookup"><span data-stu-id="21966-160">The `ngrok` session provides useful debugging information in this window.</span></span>

    <span data-ttu-id="21966-161">Die App ist nur während der aktuellen Sitzung auf Ihrem Computer verfügbar.</span><span class="sxs-lookup"><span data-stu-id="21966-161">The app is only available during the current session on your computer.</span></span> <span data-ttu-id="21966-162">Wenn der Computer heruntergefahren wird oder in den Ruhezustand wechselt, ist der Dienst nicht mehr verfügbar.</span><span class="sxs-lookup"><span data-stu-id="21966-162">If the machine is shut down or goes to sleep, the service is no longer available.</span></span> <span data-ttu-id="21966-163">Denken Sie daran, wenn Sie die App zu Testzwecken für andere Benutzer freigeben.</span><span class="sxs-lookup"><span data-stu-id="21966-163">Remember this when you share the app for testing to other users.</span></span> <span data-ttu-id="21966-164">Wenn Sie den Dienst neu starten müssen, gibt die App eine neue Adresse zurück, und Sie müssen jeden Speicherort aktualisieren, der diese Adresse verwendet.</span><span class="sxs-lookup"><span data-stu-id="21966-164">If you have to restart the service, the app returns a new address and you must update every location that uses that address.</span></span> <span data-ttu-id="21966-165">Für die kostenpflichtige Version von `ngrok` gilt diese Einschränkung nicht.</span><span class="sxs-lookup"><span data-stu-id="21966-165">The paid version of `ngrok` does not have this limitation.</span></span>

### <a name="host-in-azure"></a><span data-ttu-id="21966-166">Hosten in Azure</span><span class="sxs-lookup"><span data-stu-id="21966-166">Host in Azure</span></span>

<span data-ttu-id="21966-167">Microsoft Azure hostet Ihre .NET-Anwendung auf einer kostenlosen Ebene mithilfe der freigegebenen Infrastruktur.</span><span class="sxs-lookup"><span data-stu-id="21966-167">Microsoft Azure hosts your .NET application on a free tier using shared infrastructure.</span></span> <span data-ttu-id="21966-168">Dies reicht aus, um das `Hello World` Beispiel auszuführen.</span><span class="sxs-lookup"><span data-stu-id="21966-168">This is sufficient to run the `Hello World` sample.</span></span> <span data-ttu-id="21966-169">Weitere Informationen finden Sie unter [Erstellen eines neuen kostenlosen Azure-Kontos.](https://azure.microsoft.com/free/)</span><span class="sxs-lookup"><span data-stu-id="21966-169">For more information, see [creating a new free Azure account](https://azure.microsoft.com/free/).</span></span>

<span data-ttu-id="21966-170">Visual Studio bietet integrierte Unterstützung für die App-Bereitstellung für verschiedene Anbieter, einschließlich Azure:</span><span class="sxs-lookup"><span data-stu-id="21966-170">Visual Studio has built-in support for app deployment to different providers, including Azure:</span></span>

<img width="530px" alt="Visual Studio" src="~/assets/images/get-started/publishtoazure1.png"/>

<span data-ttu-id="21966-171">**Aktualisieren des App-Pakets**</span><span class="sxs-lookup"><span data-stu-id="21966-171">**Update the app package**</span></span>

# <a name="app-studio"></a>[<span data-ttu-id="21966-172">App-Studio</span><span class="sxs-lookup"><span data-stu-id="21966-172">App Studio</span></span>](#tab/AS)

[!include [Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

# <a name="developer-portal"></a>[<span data-ttu-id="21966-173">Entwicklerportal</span><span class="sxs-lookup"><span data-stu-id="21966-173">Developer Portal</span></span>](#tab/DP)

<span data-ttu-id="21966-174">**So installieren Sie das Entwicklerportal (Vorschau) in Teams**</span><span class="sxs-lookup"><span data-stu-id="21966-174">**To install Developer Portal (preview) in Teams**</span></span>


1. <span data-ttu-id="21966-175">Wählen Sie unten in der linken Leiste das Symbol **"Apps"** aus, und suchen Sie nach **dem Entwicklerportal.**</span><span class="sxs-lookup"><span data-stu-id="21966-175">Select the **Apps** icon at the bottom of the left-hand bar, and search for **Developer Portal**.</span></span>

    <img width="430px" alt="Screenshot of TDP" src="~/assets/images/Screen1.png"/>

1. <span data-ttu-id="21966-176">Wählen Sie **"Entwicklerportal"** aus, und wählen Sie **"Öffnen"** aus.</span><span class="sxs-lookup"><span data-stu-id="21966-176">Select **Developer Portal** and select **Open**.</span></span>

    <img width="430px" alt="Screenshot of TDP Open" src="~/assets/images/screen2.png"/>

1. <span data-ttu-id="21966-177">Wählen Sie die Registerkarte "Apps" aus, und wählen Sie **"Vorhandene App importieren"** aus.</span><span class="sxs-lookup"><span data-stu-id="21966-177">Select the Apps tab and select **Import an existing app**.</span></span>

    <img width="430px" alt="Screenshot of import app in tdp" src="~/assets/images/screen3.png"/>

1. <span data-ttu-id="21966-178">Wählen Sie **"Hello World"** aus, und wählen Sie **"Importieren"** aus.</span><span class="sxs-lookup"><span data-stu-id="21966-178">Select **Hello World** and select **Import**.</span></span> <span data-ttu-id="21966-179">Die **Hello World-App** wird im Entwicklerportal importiert.</span><span class="sxs-lookup"><span data-stu-id="21966-179">The **Hello World** app is imported in Developer Portal.</span></span> 

    <span data-ttu-id="21966-180">Sie können Ihre App über das Teams Entwicklerportal konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="21966-180">You can configure your app using the Teams Developer Portal.</span></span> <span data-ttu-id="21966-181">Das Manifest befindet sich unter "Verteilen".</span><span class="sxs-lookup"><span data-stu-id="21966-181">The Manifest is found under Distribute.</span></span> <span data-ttu-id="21966-182">Sie können das Manifest verwenden, um Funktionen, erforderliche Ressourcen und andere wichtige Attribute für Ihre App zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="21966-182">You can use the Manifest to configure capabilities, required resources, and other important attributes for your app.</span></span> <span data-ttu-id="21966-183">Weitere Informationen zum Konfigurieren Ihrer App mithilfe des Entwicklerportals finden Sie unter [Teams Developer Portal.](../concepts/build-and-test/teams-developer-portal.md)</span><span class="sxs-lookup"><span data-stu-id="21966-183">For more details on how to configure your app using Developer Portal, see [Teams Developer Portal](../concepts/build-and-test/teams-developer-portal.md).</span></span>

    <img width="430px" alt="Screenshot of configure tdp" src="~/assets/images/Screen4.png"/>
---

<a name="updatecredentials"></a>
## <a name="update-the-credentials-for-your-hosted-app"></a><span data-ttu-id="21966-184">Aktualisieren der Anmeldeinformationen für Ihre gehostete App</span><span class="sxs-lookup"><span data-stu-id="21966-184">Update the credentials for your hosted app</span></span>

<span data-ttu-id="21966-185">Die Beispiel-App erfordert, dass die Umgebungsvariablen auf die Werte festgelegt werden, die Sie in der Textdatei gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="21966-185">The sample app requires the environment variables to be set to the values that you saved in the text file.</span></span>

<span data-ttu-id="21966-186">**So aktualisieren Sie die Anmeldeinformationen für Ihre gehostete App**</span><span class="sxs-lookup"><span data-stu-id="21966-186">**To update the credentials for your hosted app**</span></span>

1. <span data-ttu-id="21966-187">die Datei `appsettings.json` öffnen.</span><span class="sxs-lookup"><span data-stu-id="21966-187">Open the `appsettings.json` file.</span></span> 
1. <span data-ttu-id="21966-188">Aktualisieren Sie den **MicrosoftAppId-Wert** mit Ihrer Bot-ID, die Sie in der Textdatei gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="21966-188">Update the **MicrosoftAppId** value with your bot ID that you saved in the text file.</span></span> 
1. <span data-ttu-id="21966-189">Aktualisieren Sie das **MicrosoftAppPassword** mit dem Bot-Kennwort, das Sie gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="21966-189">Update the **MicrosoftAppPassword** with the bot password that you saved.</span></span>

    <img width="560px" alt="Setting the keys" src="~/assets/images/get-started/get-started-net-azure-add-keys.png"/>

    <span data-ttu-id="21966-190">Nachdem diese Änderungen vorgenommen wurden, erstellen Sie die App neu.</span><span class="sxs-lookup"><span data-stu-id="21966-190">After these changes are made, rebuild the app.</span></span> <span data-ttu-id="21966-191">Wenn Sie ngrok verwenden, führen Sie die App lokal aus, und wenn Sie in Azure hosten, stellen Sie die App erneut bereit.</span><span class="sxs-lookup"><span data-stu-id="21966-191">If you are using ngrok, run the app locally, and if you are hosting in Azure, redeploy the app.</span></span>

<a name="configureapptab"></a>
## <a name="configure-the-app-tab"></a><span data-ttu-id="21966-192">Konfigurieren der Registerkarte "App"</span><span class="sxs-lookup"><span data-stu-id="21966-192">Configure the app tab</span></span>

<span data-ttu-id="21966-193">Nachdem Sie die App in Teams installiert haben, müssen Sie sie so konfigurieren, dass der Inhalt angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="21966-193">After you have installed the app into teams, you must configure it to display the content.</span></span> 

<span data-ttu-id="21966-194">**So konfigurieren Sie die Registerkarte "App"**</span><span class="sxs-lookup"><span data-stu-id="21966-194">**To configure the app tab**</span></span>

1. <span data-ttu-id="21966-195">Wechseln Sie zu einem Kanal im Team, in dem Sie die Beispiel-App installiert haben, und wählen Sie die Schaltfläche **"+"** aus, um eine neue Registerkarte hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="21966-195">Go to a channel in the team where you installed the sample app and select the **'+'** button to add a new tab.</span></span>
1. <span data-ttu-id="21966-196">Wählen Sie **"Hello World"** aus der **Registerkartenliste hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="21966-196">Select **Hello World** from the **Add a tab** list.</span></span> <span data-ttu-id="21966-197">Es wird ein Konfigurationsdialogfeld angezeigt, in dem Sie die Registerkarte auswählen können, die in diesem Kanal angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="21966-197">A configuration dialog box is displayed that enables you to select the tab to display in this channel.</span></span> 
1. <span data-ttu-id="21966-198">Wählen Sie **Speichern** aus.</span><span class="sxs-lookup"><span data-stu-id="21966-198">Select **Save**.</span></span> <span data-ttu-id="21966-199">Die `Hello World` Registerkarte wird mit der Registerkarte geladen.</span><span class="sxs-lookup"><span data-stu-id="21966-199">The `Hello World` tab is loaded with the tab.</span></span>

    <img width="530px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png" />

### <a name="test-your-bot-in-teams"></a><span data-ttu-id="21966-200">Testen Ihres Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="21966-200">Test your bot in Teams</span></span>

<span data-ttu-id="21966-201">Sie können den Bot jetzt in Teams testen.</span><span class="sxs-lookup"><span data-stu-id="21966-201">You can now test the bot in Teams.</span></span> 

<span data-ttu-id="21966-202">**So testen Sie Ihren Bot**</span><span class="sxs-lookup"><span data-stu-id="21966-202">**To test your bot**</span></span>

* <span data-ttu-id="21966-203">Wählen Sie einen Kanal im Team aus, in dem Sie Ihre App registriert haben, und geben Sie `@your-bot-name` diesen ein.</span><span class="sxs-lookup"><span data-stu-id="21966-203">Select a channel in the team where you registered your app and type `@your-bot-name`.</span></span> <span data-ttu-id="21966-204">Dies wird als **\@ Erwähnung bezeichnet.**</span><span class="sxs-lookup"><span data-stu-id="21966-204">This is called an **\@mention**.</span></span> <span data-ttu-id="21966-205">Der Bot antwortet auf eine beliebige Nachricht, die Sie senden.</span><span class="sxs-lookup"><span data-stu-id="21966-205">The bot replies to any message that you send.</span></span>

    <img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png" />

### <a name="test-your-messaging-extension"></a><span data-ttu-id="21966-206">Testen Der Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="21966-206">Test your messaging extension</span></span>

<span data-ttu-id="21966-207">**So testen Sie Ihre Messaging-Erweiterung**</span><span class="sxs-lookup"><span data-stu-id="21966-207">**To test your messaging extension**</span></span>
1. <span data-ttu-id="21966-208">Wählen Sie **...** unterhalb des Eingabefelds in der Unterhaltungsansicht aus.</span><span class="sxs-lookup"><span data-stu-id="21966-208">Select **...** below the input box in your conversation view.</span></span> <span data-ttu-id="21966-209">Ein Menü mit der **App "Hello World"** wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="21966-209">A menu with the **'Hello World'** app is displayed.</span></span> 
1. <span data-ttu-id="21966-210">Wählen Sie das Menü aus, es wird eine Reihe zufälliger Texte angezeigt.</span><span class="sxs-lookup"><span data-stu-id="21966-210">Select the menu, a set of random texts is displayed.</span></span> <span data-ttu-id="21966-211">Sie können einen beliebigen Text auswählen, der in Ihre Unterhaltung eingefügt wird.</span><span class="sxs-lookup"><span data-stu-id="21966-211">You can select one of the random text and that is inserted into your conversation.</span></span>

    <img width="530px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu1.png" />

    <img width="530px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result1.png" />

1. <span data-ttu-id="21966-212">Wählen Sie einen beliebigen Text aus.</span><span class="sxs-lookup"><span data-stu-id="21966-212">Select one of the random text.</span></span> <span data-ttu-id="21966-213">Eine Karte, die mit Ihrer eigenen Nachricht formatiert und zum Senden bereit ist, wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="21966-213">A card formatted and ready to send with your own message is shown.</span></span>

    <img width="530px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />

## <a name="see-also"></a><span data-ttu-id="21966-214">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="21966-214">See also</span></span>

* [<span data-ttu-id="21966-215">Übersicht über Lernprogramme</span><span class="sxs-lookup"><span data-stu-id="21966-215">Tutorials Overview</span></span>](code-samples.md)
* [<span data-ttu-id="21966-216">Erstellen einer Unterhaltungs-Bot-App</span><span class="sxs-lookup"><span data-stu-id="21966-216">Create a conversational bot app</span></span>](first-app-bot.md)
* [<span data-ttu-id="21966-217">Erstellen einer Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="21966-217">Create a messaging extension</span></span>](first-message-extension.md)
* [<span data-ttu-id="21966-218">Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="21966-218">Code Samples</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples)