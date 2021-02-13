---
title: 'Lernprogramm – Erstellen Ihrer ersten App mit C #'
description: 'Erfahren Sie, wie Sie mit dem Erstellen von Microsoft #A0 mit C# oder .NET beginnen.'
keywords: Erste Schritte .net c# csharp
ms.custom: scenarios:getting-started; languages:ASP.NET,C#
ms.topic: tutorial
ms.date: 11/09/2018
ms.openlocfilehash: b37a8d555117e38383504dc99d82d564439a3ebf
ms.sourcegitcommit: e3b6bc31059ec77de5fbef9b15c17d358abbca0f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/12/2021
ms.locfileid: "50231525"
---
# <a name="create-your-first-teams-app-using-c-or-net"></a><span data-ttu-id="e4cf5-104">Erstellen Ihrer ersten #A0 mit C# oder .NET</span><span class="sxs-lookup"><span data-stu-id="e4cf5-104">Create your first Teams app using C# or .NET</span></span>

<span data-ttu-id="e4cf5-105">Dieses Lernprogramm hilft Ihnen beim Erstellen einer Microsoft #A0 mit C# oder .NET.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-105">This tutorial helps you to create a Microsoft Teams app using C# or .NET.</span></span>

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="GetPrerequisites"></a>

## <a name="get-prerequisites"></a><span data-ttu-id="e4cf5-106">Voraussetzungen erhalten</span><span class="sxs-lookup"><span data-stu-id="e4cf5-106">Get prerequisites</span></span>

<span data-ttu-id="e4cf5-107">Um dieses Lernprogramm abschließen zu können, benötigen Sie die folgenden Tools:</span><span class="sxs-lookup"><span data-stu-id="e4cf5-107">To complete this tutorial, you need to get the following tools:</span></span>

- [<span data-ttu-id="e4cf5-108">Installieren von Git</span><span class="sxs-lookup"><span data-stu-id="e4cf5-108">Install Git</span></span>](https://git-scm.com/downloads)
- <span data-ttu-id="e4cf5-109">[Installieren Visual Studio](https://www.visualstudio.com/downloads/).</span><span class="sxs-lookup"><span data-stu-id="e4cf5-109">[Install Visual Studio](https://www.visualstudio.com/downloads/).</span></span> <span data-ttu-id="e4cf5-110">Sie können die kostenlose Community Edition installieren.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-110">You can install the free community edition.</span></span>

<span data-ttu-id="e4cf5-111">Wenn es während der Installation eine Option zum Hinzufügen zum `git` PFAD gibt, wählen Sie ihn aus.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-111">During installation, if there is an option to add `git` to the PATH, choose it.</span></span>

<span data-ttu-id="e4cf5-112">Führen Sie in einem Terminalfenster den folgenden Befehl aus, um die Installation zu `git` überprüfen:</span><span class="sxs-lookup"><span data-stu-id="e4cf5-112">In a terminal window, run the following command to verify your `git` installation:</span></span>

```bash
$ git --version
git version 2.17.1.windows.2

```

> [!NOTE]
> <span data-ttu-id="e4cf5-113">Verwenden Sie ein geeignetes Terminalfenster auf Ihrer Plattform.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-113">Use a suitable terminal window on your platform.</span></span> <span data-ttu-id="e4cf5-114">In diesen Beispielen wird Bash verwendet, aber auf den meisten Plattformen ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-114">These examples use Bash but run on most platforms.</span></span>

<span data-ttu-id="e4cf5-115">Stellen Sie sicher, dass Sie die neueste Version von Visual Studio und alle Updates installieren.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-115">Make sure to launch the latest version of Visual Studio and install any updates.</span></span>

<span data-ttu-id="e4cf5-116">Sie können dasselbe Terminalfenster verwenden, um die Befehle in diesem Lernprogramm auszuführen.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-116">You can use the same terminal window to run the commands in this tutorial.</span></span>

<a name="DownloadSample"></a>

## <a name="download-the-sample"></a><span data-ttu-id="e4cf5-117">Herunterladen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="e4cf5-117">Download the sample</span></span>

<span data-ttu-id="e4cf5-118">Sie können mit einer einfachen ["Hello, World" beginnen!](https://github.com/OfficeDev/msteams-samples-hello-world-csharp)</span><span class="sxs-lookup"><span data-stu-id="e4cf5-118">You can get started with a simple [Hello, World!](https://github.com/OfficeDev/msteams-samples-hello-world-csharp)</span></span> <span data-ttu-id="e4cf5-119">Beispiel in C#.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-119">sample in C#.</span></span> <span data-ttu-id="e4cf5-120">Führen Sie in einem Terminalfenster den folgenden Befehl aus, um das Beispielrepository auf Ihrem lokalen Computer zu klonen:</span><span class="sxs-lookup"><span data-stu-id="e4cf5-120">In a terminal window, run the following command to clone the sample repository to your local machine:</span></span>

```bash
git clone https://github.com/OfficeDev/msteams-samples-hello-world-csharp.git
```

> [!TIP]
> <span data-ttu-id="e4cf5-121">Sie können dieses [](https://github.com/OfficeDev/msteams-samples-hello-world-csharp) [Repository ver forken,](https://help.github.com/articles/fork-a-repo/) um Ihre Änderungen an GitHub zu ändern und zu speichern.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-121">You can [fork](https://help.github.com/articles/fork-a-repo/) this [repo](https://github.com/OfficeDev/msteams-samples-hello-world-csharp) to modify and save your changes to GitHub for reference.</span></span>

<a name="BuildRun"></a>

## <a name="build-and-run-the-sample"></a><span data-ttu-id="e4cf5-122">Erstellen und Ausführen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="e4cf5-122">Build and run the sample</span></span>

<span data-ttu-id="e4cf5-123">Nachdem das Repository geklont wurde, Visual Studio Sie die Lösungsdatei aus dem Stammverzeichnis des Beispiels öffnen und aus dem `Microsoft.Teams.Samples.HelloWorld.sln` `Build Solution` Menü `Build` auswählen.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-123">After the repo is cloned, use Visual Studio to open the solution file `Microsoft.Teams.Samples.HelloWorld.sln` from the root directory of the sample and select `Build Solution` from the `Build` menu.</span></span> <span data-ttu-id="e4cf5-124">Um das Beispiel zu drücken oder `F5` aus dem Menü zu `Start Debugging` `Debug` wählen.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-124">To run the sample press `F5` or choose `Start Debugging` from the `Debug` menu.</span></span>

<span data-ttu-id="e4cf5-125">Wenn die App gestartet wird, wird ein Browserfenster geöffnet, in dem der Stamm der App gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-125">When the app starts, a browser window opens with the root of the app launched.</span></span> <span data-ttu-id="e4cf5-126">Sie können zu den folgenden URLs navigieren, um zu überprüfen, ob alle URLs geladen werden:</span><span class="sxs-lookup"><span data-stu-id="e4cf5-126">You can navigate to the following URLs to verify that all the app URLs are loading:</span></span>

- [https://localhost:44327/](https://localhost:44327/)
- [https://localhost:44327/hello](https://localhost:44327/hello)
- [https://localhost:44327/first](https://localhost:44327/first)
- <span data-ttu-id="e4cf5-127">[https://localhost:44327/second]https://localhost:44327/second)</span><span class="sxs-lookup"><span data-stu-id="e4cf5-127">[https://localhost:44327/second]https://localhost:44327/second)</span></span>

<a name="HostSample"></a>

> [!Note]
> <span data-ttu-id="e4cf5-128">Wenn sie eine Fehlermeldung `Could not find a part of the path … bin\roslyn\csc.exe` erhalten, aktualisieren Sie das Paket mit dem `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r` Befehl.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-128">If you receive an error `Could not find a part of the path … bin\roslyn\csc.exe`, update the package with the command `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r`.</span></span> <span data-ttu-id="e4cf5-129">Weitere Informationen finden Sie in [dieser Frage auf StackOverflow](https://stackoverflow.com/questions/32780315).</span><span class="sxs-lookup"><span data-stu-id="e4cf5-129">For more information, see [this question on StackOverflow](https://stackoverflow.com/questions/32780315).</span></span>

## <a name="host-the-sample-app"></a><span data-ttu-id="e4cf5-130">Hosten der Beispiel-App</span><span class="sxs-lookup"><span data-stu-id="e4cf5-130">Host the sample app</span></span>

<span data-ttu-id="e4cf5-131">Apps in Microsoft Teams sind Webanwendungen, die eine oder mehrere Funktionen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-131">Apps in Microsoft Teams are web applications that provide one or more capabilities.</span></span> <span data-ttu-id="e4cf5-132">Damit die Plattform Teams Ihre App laden kann, muss Ihre App über das Internet erreichbar sein.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-132">For the Teams platform to load your app, your app must be reachable from the internet.</span></span> <span data-ttu-id="e4cf5-133">Damit Ihre App über das Internet erreichbar ist, müssen Sie Ihre App hosten.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-133">To make your app reachable from the internet, you need to host your app.</span></span> <span data-ttu-id="e4cf5-134">Sie können sie entweder kostenlos in Microsoft Azure hosten oder einen Tunnel für den lokalen Prozess auf Ihrem Entwicklungscomputer `ngrok` erstellen.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-134">You can either host it in Microsoft Azure for free or create a tunnel to the local process on your development machine using `ngrok`.</span></span> <span data-ttu-id="e4cf5-135">Wenn Sie mit dem Hosten Ihrer App fertig sind, notieren Sie sich die Stamm-URL.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-135">When you finish hosting your app, note its root URL.</span></span> <span data-ttu-id="e4cf5-136">Beispielsweise oder `https://yourteamsapp.ngrok.io` `https://yourteamsapp.azurewebsites.net` .</span><span class="sxs-lookup"><span data-stu-id="e4cf5-136">For example, `https://yourteamsapp.ngrok.io` or `https://yourteamsapp.azurewebsites.net`.</span></span>

### <a name="tunnel-using-ngrok"></a><span data-ttu-id="e4cf5-137">Tunnel mit ngrok</span><span class="sxs-lookup"><span data-stu-id="e4cf5-137">Tunnel using ngrok</span></span>

<span data-ttu-id="e4cf5-138">Für schnelle Tests können Sie die App auf Ihrem lokalen Computer ausführen und einen Tunnel zu ihr über einen Webendpunkt erstellen.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-138">For quick testing, you can run the app on your local machine and create a tunnel to it through a web endpoint.</span></span> <span data-ttu-id="e4cf5-139">[ngrok](https://ngrok.com) ist ein kostenloses Tool, mit dem Sie eine Webadresse wie z. B. erhalten `https://d0ac14a5.ngrok.io` können.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-139">[ngrok](https://ngrok.com) is a free tool with which you can get a web address such as `https://d0ac14a5.ngrok.io`.</span></span> <span data-ttu-id="e4cf5-140">Sie können [ngrok](https://ngrok.com/download) herunterladen und installieren.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-140">You can [download and install](https://ngrok.com/download) ngrok.</span></span> <span data-ttu-id="e4cf5-141">Stellen Sie sicher, dass Sie es einem Speicherort in Ihrer `PATH` hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-141">Make sure you add it to a location in your `PATH`.</span></span>

<span data-ttu-id="e4cf5-142">Öffnen Sie nach der Installation von ngrok ein neues Terminalfenster, und führen Sie den folgenden Befehl aus, um einen Tunnel zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="e4cf5-142">After you install ngrok, open a new terminal window and run the following command to create a tunnel:</span></span>

```bash
ngrok http 44327 -host-header=localhost:44327
```

<span data-ttu-id="e4cf5-143">Im Beispiel wird Port 44327 verwendet, um ihn anzugeben.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-143">The sample uses port 44327 be sure to specify it.</span></span>

<span data-ttu-id="e4cf5-144">Ngrok lauscht an Anforderungen aus dem Internet und leitet sie an Ihre App weiter, die an Port 44327 ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-144">Ngrok listens to requests from the internet and routes them to your app running on port 44327.</span></span> <span data-ttu-id="e4cf5-145">Um dies zu überprüfen, öffnen Sie Ihren Browser, und wechseln Sie zum Laden der `https://d0ac14a5.ngrok.io/hello` Hello-Seite Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-145">To verify, open your browser and go to `https://d0ac14a5.ngrok.io/hello` to load your app's hello page.</span></span> <span data-ttu-id="e4cf5-146">Verwenden Sie anstelle dieser URL die Weiterleitungsadresse, die von ngrok in Ihrer Konsolensitzung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-146">Instead of this URL, use the forwarding address displayed by ngrok in your console session.</span></span>

> [!NOTE]
> <span data-ttu-id="e4cf5-147">Wenn Sie im Build- [](#build-and-run-the-sample) und Ausführungsschritt einen anderen Port verwendet haben, stellen Sie sicher, dass Sie zum Einrichten des Tunnels dieselbe `ngrok` Portnummer verwenden.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-147">If you have used a different port in the [build and run](#build-and-run-the-sample) step, make sure you use the same port number to setup the `ngrok` tunnel.</span></span>

> [!TIP]
> <span data-ttu-id="e4cf5-148">Es ist eine gute Idee, in einem `ngrok` anderen Terminalfenster ausgeführt zu werden.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-148">It is a good idea to run `ngrok` in a different terminal window.</span></span> <span data-ttu-id="e4cf5-149">Dies geschieht, um zu verhindern, dass ngrok ausgeführt wird, ohne die App zu stören, die Sie beenden, neu erstellen und erneut ausführen müssen.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-149">This is done to keep ngrok from running without interfering with the app, which you have to stop, rebuild, and rerun.</span></span> <span data-ttu-id="e4cf5-150">Die `ngrok` Sitzung enthält nützliche Debuginformationen in diesem Fenster.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-150">The `ngrok` session provides useful debugging information in this window.</span></span>

<span data-ttu-id="e4cf5-151">Die App ist nur während der aktuellen Sitzung auf Ihrem Entwicklungscomputer verfügbar.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-151">The app is only available during the current session on your development machine.</span></span> <span data-ttu-id="e4cf5-152">Wenn der Computer heruntergefahren wird oder in den Ruhezustand geht, ist der Dienst nicht mehr verfügbar.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-152">If the machine is shut down or goes to sleep, the service is no longer available.</span></span> <span data-ttu-id="e4cf5-153">Denken Sie daran, wenn Sie die App zu Testzwecken für andere Benutzer freigeben.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-153">Remember this when you share the app for testing to other users.</span></span> <span data-ttu-id="e4cf5-154">Wenn Sie den Dienst neu starten müssen, gibt die App eine neue Adresse zurück, und Sie müssen jeden Speicherort aktualisieren, der diese Adresse verwendet.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-154">If you have to restart the service, the app returns a new address and you must update every location that uses that address.</span></span> <span data-ttu-id="e4cf5-155">Für die kostenpflichtige Version von ngrok gilt diese Einschränkung nicht.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-155">The paid version of ngrok does not have this limitation.</span></span>

### <a name="host-in-azure"></a><span data-ttu-id="e4cf5-156">Host in Azure</span><span class="sxs-lookup"><span data-stu-id="e4cf5-156">Host in Azure</span></span>

<span data-ttu-id="e4cf5-157">Microsoft Azure hostet Ihre .NET-Anwendung auf einer kostenlosen Ebene mit freigegebener Infrastruktur.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-157">Microsoft Azure hosts your .NET application on a free tier using shared infrastructure.</span></span> <span data-ttu-id="e4cf5-158">Dies reicht aus, um das Beispiel ausführen zu `Hello World` können.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-158">This is sufficient to run the `Hello World` sample.</span></span> <span data-ttu-id="e4cf5-159">Weitere Informationen finden Sie unter [Erstellen eines neuen kostenlosen Kontos.](https://azure.microsoft.com/free/)</span><span class="sxs-lookup"><span data-stu-id="e4cf5-159">For more information, see [creating a new free account](https://azure.microsoft.com/free/).</span></span>

<span data-ttu-id="e4cf5-160">Visual Studio bietet integrierte Unterstützung für die Bereitstellung von Apps für verschiedene Anbieter, einschließlich Azure.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-160">Visual Studio has built-in support for app deployment to different providers, including Azure.</span></span>

<img width="530px" alt="Visual Studio" src="~/assets/images/get-started/publishtoazure1.png"/>

[!include [Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

## <a name="update-the-credentials-for-your-hosted-app"></a><span data-ttu-id="e4cf5-161">Aktualisieren der Anmeldeinformationen für Ihre gehostete App</span><span class="sxs-lookup"><span data-stu-id="e4cf5-161">Update the credentials for your hosted app</span></span>

<span data-ttu-id="e4cf5-162">Für die Beispiel-App müssen die folgenden Umgebungsvariablen auf die Werte festgelegt werden, die Sie zuvor notieren.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-162">The sample app requires the following environment variables to be set to the values you made a note of earlier.</span></span>

<span data-ttu-id="e4cf5-163">Öffnen Sie die appsettings.jsOn-Datei.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-163">Open up the appsettings.json file.</span></span> <span data-ttu-id="e4cf5-164">Aktualisieren Sie *den Wert "MicrosoftAppId"* mit Ihrer Bot-ID, die Sie zuvor gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-164">Update the *MicrosoftAppId* value with your Bot ID that you saved earlier.</span></span> <span data-ttu-id="e4cf5-165">Aktualisieren Sie *MicrosoftAppPassword* mit dem Bot-Kennwort, das Sie zuvor gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-165">Update the *MicrosoftAppPassword* with the Bot password you saved earlier.</span></span>

<img width="560px" alt="Setting the keys" src="~/assets/images/get-started/get-started-net-azure-add-keys.png"/>

<span data-ttu-id="e4cf5-166">Nachdem diese Änderungen vorgenommen wurden, erstellen Sie die App neu.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-166">Once these changes are made, rebuild the app.</span></span> <span data-ttu-id="e4cf5-167">Wenn Sie ngrok verwenden, führen Sie die App lokal aus, und wenn Sie die App in Azure hosten, stellen Sie sie erneut bereit.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-167">If you are using ngrok, run the app locally, and if you are hosting in Azure redeploy the app.</span></span>

## <a name="configure-the-app-tab"></a><span data-ttu-id="e4cf5-168">Konfigurieren der Registerkarte "App"</span><span class="sxs-lookup"><span data-stu-id="e4cf5-168">Configure the app tab</span></span>

<span data-ttu-id="e4cf5-169">Nachdem Sie die App in einem Team installiert haben, müssen Sie sie so konfigurieren, dass Inhalte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-169">Once you install the app into a team, you will need to configure it to show content.</span></span> <span data-ttu-id="e4cf5-170">Wechseln Sie zu einem Kanal im Team, in dem Sie die Beispiel-App installiert haben, und klicken Sie auf die Schaltfläche **"+",** um eine neue Registerkarte hinzuzufügen. Sie können dann aus der `Hello World` Registerkartenliste **"Hinzufügen"** auswählen.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-170">Go to a channel in the team where you installed the sample app and click on the **'+'** button to add a new tab. You can then choose `Hello World` from the **Add a tab** list.</span></span> <span data-ttu-id="e4cf5-171">Anschließend wird ein Konfigurationsdialogfeld angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-171">You will then be presented with a configuration dialog.</span></span> <span data-ttu-id="e4cf5-172">In diesem Dialogfeld können Sie auswählen, welche Registerkarte in diesem Kanal angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-172">This dialog will let you choose which tab to display in this channel.</span></span> <span data-ttu-id="e4cf5-173">Sobald Sie die Registerkarte ausgewählt und auf diese geklickt haben, wird die Registerkarte mit der ausgewählten `Save` `Hello World` Registerkarte geladen.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-173">Once you select the tab and click on `Save` then you can see the `Hello World` tab loaded with the tab you chose.</span></span>

<img width="530px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png" />

### <a name="test-your-bot-in-teams"></a><span data-ttu-id="e4cf5-174">Testen Ihres Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="e4cf5-174">Test your bot in Teams</span></span>

<span data-ttu-id="e4cf5-175">Sie können jetzt mit dem Bot in Teams interagieren.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-175">You can now interact with the bot in Teams.</span></span> <span data-ttu-id="e4cf5-176">Wählen Sie einen Kanal im Team aus, in dem Sie Ihre App registriert haben und geben Sie `@your-bot-name` ein.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-176">Choose a channel in the team where you registered your app and type `@your-bot-name`.</span></span> <span data-ttu-id="e4cf5-177">Dies wird als Erwähnung **\@ bezeichnet.**</span><span class="sxs-lookup"><span data-stu-id="e4cf5-177">This is called an **\@mention**.</span></span> <span data-ttu-id="e4cf5-178">Welche Nachricht Sie an den Bot senden, wird als Antwort an Sie zurückgeschickt.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-178">Whatever message you send to the bot will be sent back to you as a reply.</span></span>

<img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png" />

### <a name="test-your-messaging-extension"></a><span data-ttu-id="e4cf5-179">Testen der Messagingerweiterung</span><span class="sxs-lookup"><span data-stu-id="e4cf5-179">Test your messaging extension</span></span>

<span data-ttu-id="e4cf5-180">Zum Testen Ihrer Messagingerweiterung können Sie auf die drei Punkte unter dem Eingabefeld in der Unterhaltungsansicht klicken.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-180">To test your messaging extension, you can click on the three dots below the input box in your conversation view.</span></span> <span data-ttu-id="e4cf5-181">Ein Menü mit der **"Hello World"-App** wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-181">A menu will pop up with the **'Hello World'** app in it.</span></span> <span data-ttu-id="e4cf5-182">Wenn Sie darauf klicken, wird eine Reihe zufälliger Texte angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-182">When you click it, you will see a bunch of random texts showing up.</span></span> <span data-ttu-id="e4cf5-183">Sie können eine der beiden Auswählen, und es wird in Ihre Unterhaltung eingefügt.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-183">You can choose any one of them and it is inserted into your conversation.</span></span>

<img width="530px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu.png" />

<img width="530px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result.png" />

<span data-ttu-id="e4cf5-184">Wählen Sie einen der zufälligen Texte aus, und unten wird eine Karte formatiert und kann mit Ihrer eigenen Nachricht gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="e4cf5-184">Choose one of the random texts, and you will see a card formatted and ready to send with your own message at the bottom.</span></span>

<img width="530px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />
