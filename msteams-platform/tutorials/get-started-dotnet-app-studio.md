---
title: 'Lernprogramm – Erstellen Ihrer ersten App mit C #'
description: 'Erfahren Sie, wie Sie mit dem Erstellen von Microsoft #A0 mit C#/.NET beginnen.'
keywords: Erste Schritte .net c# csharp
ms.custom: scenarios:getting-started; languages:ASP.NET,C#
ms.topic: tutorial
ms.date: 11/09/2018
ms.openlocfilehash: c28c4d00c375b8e37f82c343eec2c5405ae0c1c8
ms.sourcegitcommit: fa64b83c0b534bf7a89f256880d5b5ca193e4b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/28/2021
ms.locfileid: "50037039"
---
# <a name="create-your-first-microsoft-teams-app-using-c"></a><span data-ttu-id="1eac7-104">Erstellen Ihrer ersten Microsoft #A0 mit C #</span><span class="sxs-lookup"><span data-stu-id="1eac7-104">Create your first Microsoft Teams app using C#</span></span>

<span data-ttu-id="1eac7-105">Dieses Lernprogramm hilft Ihnen, mit dem Erstellen einer Microsoft #A0 mit C# auf .NET zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="1eac7-105">This tutorial helps you get started creating a Microsoft Teams app using C# on .NET.</span></span>

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="GetPrerequisites"></a>

## <a name="get-prerequisites"></a><span data-ttu-id="1eac7-106">Voraussetzungen erhalten</span><span class="sxs-lookup"><span data-stu-id="1eac7-106">Get prerequisites</span></span>

<span data-ttu-id="1eac7-107">Um dieses Lernprogramm abschließen zu können, benötigen Sie die folgenden Tools:</span><span class="sxs-lookup"><span data-stu-id="1eac7-107">To complete this tutorial, you need to get the following tools:</span></span>

- [<span data-ttu-id="1eac7-108">Installieren von Git</span><span class="sxs-lookup"><span data-stu-id="1eac7-108">Install Git</span></span>](https://git-scm.com/downloads)
- <span data-ttu-id="1eac7-109">[Installieren Visual Studio](https://www.visualstudio.com/downloads/).</span><span class="sxs-lookup"><span data-stu-id="1eac7-109">[Install Visual Studio](https://www.visualstudio.com/downloads/).</span></span> <span data-ttu-id="1eac7-110">Sie können die kostenlose Community Edition installieren.</span><span class="sxs-lookup"><span data-stu-id="1eac7-110">You can install the free community edition.</span></span>

<span data-ttu-id="1eac7-111">Wenn während der Installation eine Option zum Hinzufügen zum PFAD angezeigt wird, wählen Sie `git` dies aus.</span><span class="sxs-lookup"><span data-stu-id="1eac7-111">If you see an option to add `git` to the PATH during installation, choose to do so.</span></span> <span data-ttu-id="1eac7-112">Es ist praktisch.</span><span class="sxs-lookup"><span data-stu-id="1eac7-112">It will be handy.</span></span>

<span data-ttu-id="1eac7-113">Überprüfen Sie `git` die Installation, indem Sie folgendes in einem Terminalfenster ausführen:</span><span class="sxs-lookup"><span data-stu-id="1eac7-113">Verify your `git` installation by running the following in a terminal window:</span></span>
> [!NOTE]
> <span data-ttu-id="1eac7-114">Verwenden Sie das Terminalfenster, mit dem Sie sich auf Ihrer Plattform am besten aus sind.</span><span class="sxs-lookup"><span data-stu-id="1eac7-114">Use the terminal window that you are most comfortable with on your platform.</span></span> <span data-ttu-id="1eac7-115">Diese Beispiele verwenden Bash, werden aber auf den meisten Plattformen ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="1eac7-115">These examples use Bash, but will run on most platforms.</span></span>

```bash
$ git --version
git version 2.17.1.windows.2

```

<span data-ttu-id="1eac7-116">Stellen Sie sicher, dass Sie die neueste Version von Visual Studio installieren und alle Updates installieren, wenn sie angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="1eac7-116">Make sure to launch the latest version of Visual Studio and install any updates if shown.</span></span>

<span data-ttu-id="1eac7-117">Sie können weiterhin dieses Terminalfenster verwenden, um die Befehle auszuführen, die in diesem Lernprogramm folgen.</span><span class="sxs-lookup"><span data-stu-id="1eac7-117">You can continue to use this terminal window to run the commands that follow in this tutorial.</span></span>

<a name="DownloadSample"></a>

## <a name="download-the-sample"></a><span data-ttu-id="1eac7-118">Herunterladen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="1eac7-118">Download the sample</span></span>

<span data-ttu-id="1eac7-119">Wir haben ein einfaches [Hello, World! bereitgestellt.](https://github.com/OfficeDev/msteams-samples-hello-world-csharp)</span><span class="sxs-lookup"><span data-stu-id="1eac7-119">We have provided a simple [Hello, World!](https://github.com/OfficeDev/msteams-samples-hello-world-csharp)</span></span> <span data-ttu-id="1eac7-120">Beispiel in C#, um Sie zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="1eac7-120">sample in C# to get you started.</span></span> <span data-ttu-id="1eac7-121">Führen Sie in einem Terminalfenster den folgenden Befehl aus, um das Beispielrepository auf Ihrem lokalen Computer zu klonen:</span><span class="sxs-lookup"><span data-stu-id="1eac7-121">In a terminal window, run the following command to clone the sample repository to your local machine:</span></span>

```bash
git clone https://github.com/OfficeDev/msteams-samples-hello-world-csharp.git
```

> [!TIP]
> <span data-ttu-id="1eac7-122">Sie können [dieses Repository ver forken,](https://help.github.com/articles/fork-a-repo/) [](https://github.com/OfficeDev/msteams-samples-hello-world-csharp) wenn Sie Ihre Änderungen an GitHub ändern und zur zukünftigen Referenz einchecken möchten.</span><span class="sxs-lookup"><span data-stu-id="1eac7-122">You can [fork](https://help.github.com/articles/fork-a-repo/) this [repo](https://github.com/OfficeDev/msteams-samples-hello-world-csharp) if you want to modify and check in your changes to GitHub for future reference.</span></span>

<a name="BuildRun"></a>

## <a name="build-and-run-the-sample"></a><span data-ttu-id="1eac7-123">Erstellen und Ausführen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="1eac7-123">Build and run the sample</span></span>

<span data-ttu-id="1eac7-124">Nachdem das Repository geklont wurde, Visual Studio Sie die Lösungsdatei aus dem Stammverzeichnis des Beispiels öffnen und im `Microsoft.Teams.Samples.HelloWorld.sln` `Build Solution` Menü `Build` klicken.</span><span class="sxs-lookup"><span data-stu-id="1eac7-124">Once the repo is cloned, use Visual Studio to open the solution file `Microsoft.Teams.Samples.HelloWorld.sln` from the root directory of the sample and click `Build Solution` from the `Build` menu.</span></span> <span data-ttu-id="1eac7-125">Sie können das Beispiel ausführen, indem Sie das Menü drücken `F5` `Start Debugging` oder `Debug` auswählen.</span><span class="sxs-lookup"><span data-stu-id="1eac7-125">You can run the sample by pressing `F5` or choosing `Start Debugging` from the `Debug` menu.</span></span>

<span data-ttu-id="1eac7-126">Wenn die App gestartet wird, wird ein Browserfenster mit dem Stamm der gestarteten App geöffnet.</span><span class="sxs-lookup"><span data-stu-id="1eac7-126">When the app starts, you will see a browser window open with the root of the app launched.</span></span> <span data-ttu-id="1eac7-127">Sie können zu den folgenden URLs navigieren, um zu überprüfen, ob alle URLs geladen werden:</span><span class="sxs-lookup"><span data-stu-id="1eac7-127">You can navigate to the following URLs to verify that all the app URLs are loading:</span></span>

- [http://localhost:3333](http://localhost:3333)
- [http://localhost:3333/hello](http://localhost:3333/hello)
- [http://localhost:3333/first](http://localhost:3333/first)
- [http://localhost:3333/second](http://localhost:3333/second)

<a name="HostSample"></a>

> [!Note]
> <span data-ttu-id="1eac7-128">Wenn sie eine Fehlermeldung wie `Could not find a part of the path … bin\roslyn\csc.exe` erhalten, versuchen Sie, das Paket mit dem Befehl zu `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r` aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="1eac7-128">If you receive an error like `Could not find a part of the path … bin\roslyn\csc.exe`, try updating the package with the command `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r`.</span></span> <span data-ttu-id="1eac7-129">Weitere Informationen finden Sie in dieser Frage auf [StackOverflow.](https://stackoverflow.com/questions/32780315)</span><span class="sxs-lookup"><span data-stu-id="1eac7-129">See [this question on StackOverflow](https://stackoverflow.com/questions/32780315) for additional details.</span></span>

## <a name="host-the-sample-app"></a><span data-ttu-id="1eac7-130">Hosten der Beispiel-App</span><span class="sxs-lookup"><span data-stu-id="1eac7-130">Host the sample app</span></span>

<span data-ttu-id="1eac7-131">Denken Sie daran, dass Apps in Microsoft Teams Webanwendungen sind, die eine oder mehrere Funktionen verfügbar machen.</span><span class="sxs-lookup"><span data-stu-id="1eac7-131">Remember that apps in Microsoft Teams are web applications exposing one or more capabilities.</span></span> <span data-ttu-id="1eac7-132">Damit die Plattform Teams Ihre App laden kann, muss Ihre App über das Internet erreichbar sein.</span><span class="sxs-lookup"><span data-stu-id="1eac7-132">For the Teams platform to load your app, your app must be reachable from the internet.</span></span> <span data-ttu-id="1eac7-133">Damit Ihre App über das Internet erreichbar ist, müssen Sie Ihre App hosten.</span><span class="sxs-lookup"><span data-stu-id="1eac7-133">To make your app reachable from the internet, you need to host your app.</span></span> <span data-ttu-id="1eac7-134">Sie können sie entweder kostenlos in Microsoft Azure hosten oder einen Tunnel für den lokalen Prozess auf Ihrem Entwicklungscomputer `ngrok` erstellen.</span><span class="sxs-lookup"><span data-stu-id="1eac7-134">You can either host it in Microsoft Azure for free or create a tunnel to the local process on your development machine using `ngrok`.</span></span> <span data-ttu-id="1eac7-135">Wenn Sie mit dem Hosten Ihrer App fertig sind, notieren Sie sich die Stamm-URL.</span><span class="sxs-lookup"><span data-stu-id="1eac7-135">When you finish hosting your app make a note of its root URL.</span></span> <span data-ttu-id="1eac7-136">Sie sieht in etwa wie: `https://yourteamsapp.ngrok.io` oder `https://yourteamsapp.azurewebsites.net` aus.</span><span class="sxs-lookup"><span data-stu-id="1eac7-136">It will look something like: `https://yourteamsapp.ngrok.io` or `https://yourteamsapp.azurewebsites.net`.</span></span>

### <a name="tunnel-using-ngrok"></a><span data-ttu-id="1eac7-137">Tunnel mit ngrok</span><span class="sxs-lookup"><span data-stu-id="1eac7-137">Tunnel using ngrok</span></span>

<span data-ttu-id="1eac7-138">Für schnelle Tests können Sie die App auf Ihrem lokalen Computer ausführen und einen Tunnel über einen Webendpunkt erstellen.</span><span class="sxs-lookup"><span data-stu-id="1eac7-138">For quick testing you can run the app on your local machine and create a tunnel to it through a web endpoint.</span></span> <span data-ttu-id="1eac7-139">[ngrok](https://ngrok.com) ist ein kostenloses Tool, mit dem Sie genau das tun können.</span><span class="sxs-lookup"><span data-stu-id="1eac7-139">[ngrok](https://ngrok.com) is a free tool that lets you do just that.</span></span> <span data-ttu-id="1eac7-140">Mit ngrok können Sie eine Webadresse wie z. B. `https://d0ac14a5.ngrok.io` (diese URL ist nur ein Beispiel) erhalten.</span><span class="sxs-lookup"><span data-stu-id="1eac7-140">With ngrok you can get a web address such as `https://d0ac14a5.ngrok.io` (this URL is just an example).</span></span> <span data-ttu-id="1eac7-141">Sie können [ngrok](https://ngrok.com/download) für Ihre Umgebung herunterladen und installieren.</span><span class="sxs-lookup"><span data-stu-id="1eac7-141">You can [download and install](https://ngrok.com/download) ngrok for your environment.</span></span> <span data-ttu-id="1eac7-142">Stellen Sie sicher, dass Sie es einem Speicherort in Ihrer `PATH` hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="1eac7-142">Make sure you add it to a location in your `PATH`.</span></span>

<span data-ttu-id="1eac7-143">Nach der Installation können Sie ein neues Terminalfenster öffnen und den folgenden Befehl ausführen, um einen Tunnel zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="1eac7-143">Once you install it, you can open a new terminal window and run the following command to create a tunnel.</span></span> <span data-ttu-id="1eac7-144">Im Beispiel wird Port 3333 verwendet. Geben Sie ihn daher unbedingt hier an.</span><span class="sxs-lookup"><span data-stu-id="1eac7-144">The sample uses port 3333, so be sure to specify it here.</span></span>

```bash
ngrok http 3333 -host-header=localhost:3333
```

<span data-ttu-id="1eac7-145">Ngrok hört Anforderungen aus dem Internet ab und führt sie an Ihre App weiter, die an Port 3333 ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="1eac7-145">Ngrok will listen to requests from the internet and will route them to your app running on port 3333.</span></span> <span data-ttu-id="1eac7-146">Sie können dies überprüfen, indem Sie Ihren Browser öffnen und die `https://d0ac14a5.ngrok.io/hello` Hello-Seite Ihrer App laden.</span><span class="sxs-lookup"><span data-stu-id="1eac7-146">You can verify by opening your browser and going to `https://d0ac14a5.ngrok.io/hello` to load your app's hello page.</span></span> <span data-ttu-id="1eac7-147">Verwenden Sie anstatt dieser URL unbedingt die Weiterleitungsadresse, die ngrok in Ihrer Konsolensitzung angezeigt hat.</span><span class="sxs-lookup"><span data-stu-id="1eac7-147">Please be sure to use the forwarding address displayed by ngrok in your console session instead of this URL.</span></span>

> [!NOTE]
> <span data-ttu-id="1eac7-148">Wenn Sie im Build einen [](#build-and-run-the-sample) anderen Port verwendet haben, und führen Sie den obigen Schritt aus, stellen Sie sicher, dass Sie zum Einrichten des Tunnels dieselbe Portnummer `ngrok` verwenden.</span><span class="sxs-lookup"><span data-stu-id="1eac7-148">If you have used a different port in the [build and run](#build-and-run-the-sample) step above, make sure you use the same port number to setup the `ngrok` tunnel.</span></span>
> [!TIP]
> <span data-ttu-id="1eac7-149">Es ist eine gute Idee, in einem anderen Terminalfenster ausgeführt zu werden, damit sie ausgeführt wird, ohne die App zu stören, die Sie später möglicherweise beenden, neu erstellen und `ngrok` erneut ausführen müssen.</span><span class="sxs-lookup"><span data-stu-id="1eac7-149">It is a good idea to run `ngrok` in a different terminal window to keep it running without interfering with the app which you might later have to stop, rebuild and rerun.</span></span> <span data-ttu-id="1eac7-150">Die `ngrok` Sitzung gibt nützliche Debuginformationen in diesem Fenster zurück.</span><span class="sxs-lookup"><span data-stu-id="1eac7-150">The `ngrok` session will return useful debugging information in this window.</span></span>

<span data-ttu-id="1eac7-151">Die App ist nur während der aktuellen Sitzung auf Ihrem Entwicklungscomputer verfügbar.</span><span class="sxs-lookup"><span data-stu-id="1eac7-151">The app will only be available during the current session on your development machine.</span></span> <span data-ttu-id="1eac7-152">Wenn der Computer heruntergefahren wird oder in den Ruhezustand geht, ist der Dienst nicht mehr verfügbar.</span><span class="sxs-lookup"><span data-stu-id="1eac7-152">If the machine is shut down or goes to sleep the service will no longer be available.</span></span> <span data-ttu-id="1eac7-153">Denken Sie daran, wenn Sie die App für Tests durch andere Benutzer freigeben.</span><span class="sxs-lookup"><span data-stu-id="1eac7-153">Remember this when sharing the app for testing by other users.</span></span> <span data-ttu-id="1eac7-154">Wenn Sie den Dienst neu starten müssen, wird eine neue Adresse zurückgeben, und Sie müssen jeden Ort aktualisieren, der diese Adresse verwendet.</span><span class="sxs-lookup"><span data-stu-id="1eac7-154">If you have to restart the service it will return a new address and you will have to update every place that uses that address.</span></span> <span data-ttu-id="1eac7-155">Für die kostenpflichtige Version von Ngrok gilt diese Einschränkung nicht.</span><span class="sxs-lookup"><span data-stu-id="1eac7-155">The paid version of Ngrok does not have this limitation.</span></span>

### <a name="host-in-azure"></a><span data-ttu-id="1eac7-156">Host in Azure</span><span class="sxs-lookup"><span data-stu-id="1eac7-156">Host in Azure</span></span>

<span data-ttu-id="1eac7-157">Mit Microsoft Azure können Sie Ihre .NET-Anwendung mithilfe einer gemeinsam genutzten Infrastruktur auf einer kostenlosen Ebene hosten.</span><span class="sxs-lookup"><span data-stu-id="1eac7-157">Microsoft Azure lets you host your .NET application on a free tier using shared infrastructure.</span></span> <span data-ttu-id="1eac7-158">Dies reicht aus, um dieses Beispiel ausführen zu `Hello World` können.</span><span class="sxs-lookup"><span data-stu-id="1eac7-158">This will be sufficient to run this `Hello World` sample.</span></span> <span data-ttu-id="1eac7-159">Weitere [Informationen finden Sie unter Erstellen eines neuen kostenlosen](https://azure.microsoft.com/free/) Kontos.</span><span class="sxs-lookup"><span data-stu-id="1eac7-159">See [creating a new free account](https://azure.microsoft.com/free/) for more information.</span></span>

<span data-ttu-id="1eac7-160">Visual Studio bietet integrierte Unterstützung für die Bereitstellung von Apps für verschiedene Anbieter, einschließlich Azure.</span><span class="sxs-lookup"><span data-stu-id="1eac7-160">Visual Studio has built-in support for app deployment to different providers, including Azure.</span></span>

<img width="530px" alt="Visual Studio" src="~/assets/images/get-started/publishtoazure1.png"/>

[!include [Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

## <a name="update-the-credentials-for-your-hosted-app"></a><span data-ttu-id="1eac7-161">Aktualisieren der Anmeldeinformationen für Ihre gehostete App</span><span class="sxs-lookup"><span data-stu-id="1eac7-161">Update the credentials for your hosted app</span></span>

<span data-ttu-id="1eac7-162">Die Beispiel-App erfordert, dass die folgenden Umgebungsvariablen auf die Werte festgelegt werden, die Sie zuvor notieren.</span><span class="sxs-lookup"><span data-stu-id="1eac7-162">The sample app requires the following environment variables to be set to the values you made a note of earlier.</span></span>

<span data-ttu-id="1eac7-163">Öffnen Sie die appsettings.jsOn-Datei.</span><span class="sxs-lookup"><span data-stu-id="1eac7-163">Open up the appsettings.json file.</span></span> <span data-ttu-id="1eac7-164">Aktualisieren Sie *den Wert "MicrosoftAppId"* mit Ihrer Bot-ID, die Sie zuvor gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="1eac7-164">Update the *MicrosoftAppId* value with your Bot ID that you saved earlier.</span></span> <span data-ttu-id="1eac7-165">Aktualisieren Sie *MicrosoftAppPassword* mit dem Bot-Kennwort, das Sie zuvor gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="1eac7-165">Update the *MicrosoftAppPassword* with the Bot password you saved earlier.</span></span>

<img width="560px" alt="Setting the keys" src="~/assets/images/get-started/get-started-net-azure-add-keys.png"/>

<span data-ttu-id="1eac7-166">Nachdem diese Änderungen vorgenommen wurden, erstellen Sie die App neu.</span><span class="sxs-lookup"><span data-stu-id="1eac7-166">Once these changes are made, rebuild the app.</span></span> <span data-ttu-id="1eac7-167">Wenn Sie ngrok verwenden, führen Sie die App lokal aus, und wenn Sie die App in Azure hosten, stellen Sie sie erneut bereit.</span><span class="sxs-lookup"><span data-stu-id="1eac7-167">If you are using ngrok, run the app locally, and if you are hosting in Azure redeploy the app.</span></span>

## <a name="configure-the-app-tab"></a><span data-ttu-id="1eac7-168">Konfigurieren der Registerkarte "App"</span><span class="sxs-lookup"><span data-stu-id="1eac7-168">Configure the app tab</span></span>

<span data-ttu-id="1eac7-169">Nachdem Sie die App in einem Team installiert haben, müssen Sie sie so konfigurieren, dass Inhalte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="1eac7-169">Once you install the app into a team, you will need to configure it to show content.</span></span> <span data-ttu-id="1eac7-170">Wechseln Sie zu einem Kanal im Team, in dem Sie die Beispiel-App installiert haben, und klicken Sie auf die Schaltfläche **"+",** um eine neue Registerkarte hinzuzufügen. Sie können dann aus der `Hello World` Registerkartenliste **"Hinzufügen"** auswählen.</span><span class="sxs-lookup"><span data-stu-id="1eac7-170">Go to a channel in the team where you installed the sample app and click on the **'+'** button to add a new tab. You can then choose `Hello World` from the **Add a tab** list.</span></span> <span data-ttu-id="1eac7-171">Anschließend wird ein Konfigurationsdialogfeld angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1eac7-171">You will then be presented with a configuration dialog.</span></span> <span data-ttu-id="1eac7-172">In diesem Dialogfeld können Sie auswählen, welche Registerkarte in diesem Kanal angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="1eac7-172">This dialog will let you choose which tab to display in this channel.</span></span> <span data-ttu-id="1eac7-173">Nachdem Sie die Registerkarte ausgewählt und auf diese geklickt haben, wird die Registerkarte mit der ausgewählten `Save` `Hello World` Registerkarte geladen.</span><span class="sxs-lookup"><span data-stu-id="1eac7-173">Once you select the tab and click on `Save` then you can see the `Hello World` tab loaded with the tab you chose.</span></span>

<img width="530px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png" />

### <a name="test-your-bot-in-teams"></a><span data-ttu-id="1eac7-174">Testen Ihres Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="1eac7-174">Test your bot in Teams</span></span>

<span data-ttu-id="1eac7-175">Sie können jetzt mit dem Bot in Teams interagieren.</span><span class="sxs-lookup"><span data-stu-id="1eac7-175">You can now interact with the bot in Teams.</span></span> <span data-ttu-id="1eac7-176">Wählen Sie einen Kanal im Team aus, in dem Sie Ihre App registriert haben, und geben Sie `@your-bot-name` ein.</span><span class="sxs-lookup"><span data-stu-id="1eac7-176">Choose a channel in the team where you registered your app, and type `@your-bot-name`.</span></span> <span data-ttu-id="1eac7-177">Dies wird als Erwähnung **\@ bezeichnet.**</span><span class="sxs-lookup"><span data-stu-id="1eac7-177">This is called an **\@mention**.</span></span> <span data-ttu-id="1eac7-178">Welche Nachricht Sie an den Bot senden, wird als Antwort an Sie zurückgeschickt.</span><span class="sxs-lookup"><span data-stu-id="1eac7-178">Whatever message you send to the bot will be sent back to you as a reply.</span></span>

<img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png" />

### <a name="test-your-messaging-extension"></a><span data-ttu-id="1eac7-179">Testen der Messagingerweiterung</span><span class="sxs-lookup"><span data-stu-id="1eac7-179">Test your messaging extension</span></span>

<span data-ttu-id="1eac7-180">Zum Testen Ihrer Messagingerweiterung können Sie auf die drei Punkte unter dem Eingabefeld in der Unterhaltungsansicht klicken.</span><span class="sxs-lookup"><span data-stu-id="1eac7-180">To test your messaging extension, you can click on the three dots below the input box in your conversation view.</span></span> <span data-ttu-id="1eac7-181">Ein Menü wird mit der **"Hello World"-App** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1eac7-181">A menu will pop up with the **'Hello World'** app in it.</span></span> <span data-ttu-id="1eac7-182">Wenn Sie darauf klicken, wird eine Reihe zufälliger Texte angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1eac7-182">When you click it, you will see a bunch of random texts showing up.</span></span> <span data-ttu-id="1eac7-183">Sie können eine davon auswählen und in Ihre Unterhaltung einfügen.</span><span class="sxs-lookup"><span data-stu-id="1eac7-183">You can choose any one of them and it will be inserted it into your conversation.</span></span>

<img width="530px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu.png" />

<img width="530px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result.png" />

<span data-ttu-id="1eac7-184">Wählen Sie einen der zufälligen Texte aus, und unten wird eine Karte formatiert und bereit zum Senden mit Ihrer eigenen Nachricht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1eac7-184">Choose one of the random texts, and you will see a card formatted and ready to send with your own message at the bottom.</span></span>

<img width="530px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />
