---
title: 'Lernprogramm – Erstellen Ihrer ersten App mithilfe von C #'
description: Erfahren Sie, wie Sie mit dem Erstellen Microsoft Teams apps mit C# oder .NET beginnen.
keywords: Erste Schritte .net c# csharp
ms.custom: scenarios:getting-started; languages:ASP.NET,C#
localization_priority: Normal
ms.topic: tutorial
ms.date: 11/09/2018
ms.openlocfilehash: be6c5865da04125b159792364bbd80ac219d9fd9
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101856"
---
# <a name="create-your-first-teams-app-using-c"></a><span data-ttu-id="87e1b-104">Erstellen Ihrer ersten Teams-App mit C #</span><span class="sxs-lookup"><span data-stu-id="87e1b-104">Create your first Teams app using C#</span></span>

<span data-ttu-id="87e1b-105">Dieses Lernprogramm hilft Ihnen beim Erstellen einer Microsoft Teams App mithilfe C#.</span><span class="sxs-lookup"><span data-stu-id="87e1b-105">This tutorial helps you to create a Microsoft Teams app using C#.</span></span> <span data-ttu-id="87e1b-106">Dazu müssen Sie Folgendes tun:</span><span class="sxs-lookup"><span data-stu-id="87e1b-106">To do this, you must:</span></span>

* <span data-ttu-id="87e1b-107">Vorbereiten der Umgebung</span><span class="sxs-lookup"><span data-stu-id="87e1b-107">Prepare your environment</span></span>
* <span data-ttu-id="87e1b-108">Erforderliche Komponenten erhalten</span><span class="sxs-lookup"><span data-stu-id="87e1b-108">Get prerequisites</span></span>
* <span data-ttu-id="87e1b-109">Herunterladen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="87e1b-109">Download the sample</span></span>
* <span data-ttu-id="87e1b-110">Erstellen und Ausführen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="87e1b-110">Build and run the sample</span></span>
* <span data-ttu-id="87e1b-111">Hosten der Beispiel-App</span><span class="sxs-lookup"><span data-stu-id="87e1b-111">Host the sample app</span></span>
* <span data-ttu-id="87e1b-112">Aktualisieren der Anmeldeinformationen für Ihre gehostete App</span><span class="sxs-lookup"><span data-stu-id="87e1b-112">Update the credentials for your hosted app</span></span>
* <span data-ttu-id="87e1b-113">Konfigurieren der Registerkarte "App"</span><span class="sxs-lookup"><span data-stu-id="87e1b-113">Configure the app tab</span></span>

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="GetPrerequisites"></a>

## <a name="get-prerequisites"></a><span data-ttu-id="87e1b-114">Erforderliche Komponenten erhalten</span><span class="sxs-lookup"><span data-stu-id="87e1b-114">Get prerequisites</span></span>

<span data-ttu-id="87e1b-115">Zum Abschließen dieses Lernprogramms müssen Sie die folgenden Tools installieren:</span><span class="sxs-lookup"><span data-stu-id="87e1b-115">To complete this tutorial, you need to install the following tools:</span></span>

- [<span data-ttu-id="87e1b-116">Installieren von Git</span><span class="sxs-lookup"><span data-stu-id="87e1b-116">Install Git</span></span>](https://git-scm.com/downloads)
- [<span data-ttu-id="87e1b-117">Installieren von Visual Studio</span><span class="sxs-lookup"><span data-stu-id="87e1b-117">Install Visual Studio</span></span>](https://www.visualstudio.com/downloads/)

<span data-ttu-id="87e1b-118">Sie können die kostenlose Community edition von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="87e1b-118">You can install the free community edition of Visual Studio.</span></span> <span data-ttu-id="87e1b-119">Wenn es während der Installation eine Option gibt, die dem Pfad `git` hinzugefügt werden kann, wählen Sie ihn aus.</span><span class="sxs-lookup"><span data-stu-id="87e1b-119">During installation, if there is an option to add `git` to the path, select it.</span></span> <span data-ttu-id="87e1b-120">Führen Sie in einem Terminalfenster den folgenden Befehl aus, um die Installation zu `git` überprüfen:</span><span class="sxs-lookup"><span data-stu-id="87e1b-120">In a terminal window, run the following command to verify your `git` installation:</span></span>

```bash
$ git --version
git version 2.17.1.windows.2

```

> [!NOTE]
> <span data-ttu-id="87e1b-121">Verwenden Sie ein geeignetes Terminalfenster auf Ihrer Plattform.</span><span class="sxs-lookup"><span data-stu-id="87e1b-121">Use a suitable terminal window on your platform.</span></span> <span data-ttu-id="87e1b-122">Diese Beispiele verwenden Git Bash, können jedoch auf den meisten Plattformen ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="87e1b-122">These examples use Git Bash but can be run on most platforms.</span></span>

<span data-ttu-id="87e1b-123">Öffnen Sie die neueste Version von Visual Studio, und installieren Sie alle Updates.</span><span class="sxs-lookup"><span data-stu-id="87e1b-123">Open the latest version of Visual Studio and install any updates.</span></span>

<span data-ttu-id="87e1b-124">Sie können dasselbe Terminalfenster verwenden, um die Befehle in diesem Lernprogramm auszuführen.</span><span class="sxs-lookup"><span data-stu-id="87e1b-124">You can use the same terminal window to run the commands in this tutorial.</span></span>

<a name="DownloadSample"></a>

## <a name="download-the-sample"></a><span data-ttu-id="87e1b-125">Herunterladen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="87e1b-125">Download the sample</span></span>

<span data-ttu-id="87e1b-126">Sie können mit einem einfachen [Hello, World! beginnen.](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-hello-world/csharp)</span><span class="sxs-lookup"><span data-stu-id="87e1b-126">You can get started with a simple [Hello, World!](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-hello-world/csharp)</span></span> <span data-ttu-id="87e1b-127">Beispiel in C#.</span><span class="sxs-lookup"><span data-stu-id="87e1b-127">sample in C#.</span></span> <span data-ttu-id="87e1b-128">Führen Sie in einem Terminalfenster den folgenden Befehl aus, um das Beispielrepository auf Ihren Computer zu klonen:</span><span class="sxs-lookup"><span data-stu-id="87e1b-128">In a terminal window, run the following command to clone the sample repository to your computer:</span></span>

```bash
git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
```

> [!TIP]
> <span data-ttu-id="87e1b-129">Sie können [dieses Repository forken,](https://help.github.com/articles/fork-a-repo/) [um](https://github.com/OfficeDev/Microsoft-Teams-Samples) Ihre Änderungen zu ändern und zu speichern, GitHub.</span><span class="sxs-lookup"><span data-stu-id="87e1b-129">You can [fork](https://help.github.com/articles/fork-a-repo/) this [repo](https://github.com/OfficeDev/Microsoft-Teams-Samples) to modify and save your changes to GitHub.</span></span>

<a name="BuildRun"></a>

## <a name="build-and-run-the-sample"></a><span data-ttu-id="87e1b-130">Erstellen und Ausführen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="87e1b-130">Build and run the sample</span></span>

<span data-ttu-id="87e1b-131">Nachdem das Repository geklont wurde, Visual Studio Sie die Lösungsdatei **Microsoft.Teams. Samples.HelloWorld.sln** aus dem **Microsoft-Teams-Samples/samples/app-hello-world/csharp-Verzeichnis** des Beispiels.</span><span class="sxs-lookup"><span data-stu-id="87e1b-131">After the repo is cloned, use Visual Studio to open the solution file **Microsoft.Teams.Samples.HelloWorld.sln** from the **Microsoft-Teams-Samples/samples/app-hello-world/csharp** directory of the sample.</span></span> <span data-ttu-id="87e1b-132">Wählen Sie dann **im Menü Build** die Option Lösung erstellen aus. </span><span class="sxs-lookup"><span data-stu-id="87e1b-132">Then, select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="87e1b-133">Drücken Sie zum Ausführen des Beispiels **F5,** oder wählen Sie **Debuggen starten** im Menü **Debuggen** aus.</span><span class="sxs-lookup"><span data-stu-id="87e1b-133">To run the sample, press **F5** or select **Start Debugging** from the **Debug** menu.</span></span>

<span data-ttu-id="87e1b-134">Wenn die App gestartet wird, wird ein Browserfenster geöffnet, in dem der Stamm der App gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="87e1b-134">When the app starts, a browser window opens with the root of the app launched.</span></span> <span data-ttu-id="87e1b-135">Sie können zu den folgenden URLs wechseln, um zu überprüfen, ob alle App-URLs geladen werden:</span><span class="sxs-lookup"><span data-stu-id="87e1b-135">You can go to the following URLs to verify that all the app URLs are loading:</span></span>

- [https://localhost:44327/](https://localhost:44327/)
- [https://localhost:44327/hello](https://localhost:44327/hello)
- [https://localhost:44327/first](https://localhost:44327/first)
- [https://localhost:44327/second](https://localhost:44327/second)

<a name="HostSample"></a>

> [!Note]
> <span data-ttu-id="87e1b-136">Wenn sie einen Fehler `Could not find a part of the path … bin\roslyn\csc.exe` erhalten, aktualisieren Sie das Paket mit dem Befehl `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r` .</span><span class="sxs-lookup"><span data-stu-id="87e1b-136">If you receive an error `Could not find a part of the path … bin\roslyn\csc.exe`, update the package with the command `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r`.</span></span> <span data-ttu-id="87e1b-137">Weitere Informationen finden Sie in [dieser Frage unter Stack Overflow](https://stackoverflow.com/questions/32780315).</span><span class="sxs-lookup"><span data-stu-id="87e1b-137">For more information, see [this question on Stack Overflow](https://stackoverflow.com/questions/32780315).</span></span>

## <a name="host-the-sample-app"></a><span data-ttu-id="87e1b-138">Hosten der Beispiel-App</span><span class="sxs-lookup"><span data-stu-id="87e1b-138">Host the sample app</span></span>

<span data-ttu-id="87e1b-139">Apps in Microsoft Teams sind Webanwendungen, die eine oder mehrere Funktionen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="87e1b-139">Apps in Microsoft Teams are web applications that provide one or more capabilities.</span></span> <span data-ttu-id="87e1b-140">Damit die Teams Ihre App laden kann, muss Ihre App im Internet verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="87e1b-140">For the Teams platform to load your app, your app must be available on the internet.</span></span> <span data-ttu-id="87e1b-141">Dazu müssen Sie Ihre App hosten.</span><span class="sxs-lookup"><span data-stu-id="87e1b-141">To do this, you need to host your app.</span></span> <span data-ttu-id="87e1b-142">Sie können sie entweder kostenlos in Microsoft Azure hosten oder einen Tunnel für den lokalen Prozess auf Ihrem Computer mit `ngrok` erstellen.</span><span class="sxs-lookup"><span data-stu-id="87e1b-142">You can either host it in Microsoft Azure for free or create a tunnel to the local process on your computer using `ngrok`.</span></span> <span data-ttu-id="87e1b-143">Notieren Sie sich nach dem Hosten Ihrer App die Stamm-URL, z. B. `https://yourteamsapp.ngrok.io` oder `https://yourteamsapp.azurewebsites.net` .</span><span class="sxs-lookup"><span data-stu-id="87e1b-143">After you host your app, note its root URL, such as `https://yourteamsapp.ngrok.io` or `https://yourteamsapp.azurewebsites.net`.</span></span>

### <a name="tunnel-using-ngrok"></a><span data-ttu-id="87e1b-144">Tunnel verwenden von ngrok</span><span class="sxs-lookup"><span data-stu-id="87e1b-144">Tunnel using ngrok</span></span>

<span data-ttu-id="87e1b-145">Für schnelle Tests können Sie die App auf Ihrem Computer ausführen und über einen Webendpunkt einen Tunnel dafür erstellen.</span><span class="sxs-lookup"><span data-stu-id="87e1b-145">For quick testing, you can run the app on your computer and create a tunnel to it through a web endpoint.</span></span> <span data-ttu-id="87e1b-146">[`ngrok`](https://ngrok.com) ist ein kostenloses Tool, mit dem Sie eine Webadresse erhalten können, z. B. `https://d0ac14a5.ngrok.io` .</span><span class="sxs-lookup"><span data-stu-id="87e1b-146">[`ngrok`](https://ngrok.com) is a free tool with which you can get a web address, such as `https://d0ac14a5.ngrok.io`.</span></span> <span data-ttu-id="87e1b-147">Sie können [ngrok herunterladen und](https://ngrok.com/download) installieren und an einem Speicherort in Ihrer `PATH` hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="87e1b-147">You can [download and install](https://ngrok.com/download) ngrok and add it to a location in your `PATH`.</span></span>

<span data-ttu-id="87e1b-148">Öffnen Sie nach `ngrok` der Installation ein neues Terminalfenster, und führen Sie den folgenden Befehl aus, um einen Tunnel zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="87e1b-148">After you install `ngrok`, open a new terminal window and run the following command to create a tunnel:</span></span>

```bash
ngrok http 44327 -host-header=localhost:44327
```

<span data-ttu-id="87e1b-149">`Ngrok` lauscht Anfragen aus dem Internet und leitet sie an Ihre App weiter, die an Port 44327 ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="87e1b-149">`Ngrok` listens to requests from the internet and routes them to your app running on port 44327.</span></span> <span data-ttu-id="87e1b-150">Um dies zu überprüfen, öffnen Sie Ihren Browser, und `https://d0ac14a5.ngrok.io/hello` wechseln Sie zu, um die Hello-Seite Ihrer App zu laden.</span><span class="sxs-lookup"><span data-stu-id="87e1b-150">To verify, open your browser and go to `https://d0ac14a5.ngrok.io/hello` to load your app's hello page.</span></span> <span data-ttu-id="87e1b-151">Verwenden Sie anstelle dieser URL die Weiterleitungsadresse, die `ngrok` in Der Konsolensitzung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="87e1b-151">Instead of this URL, use the forwarding address displayed by `ngrok` in your console session.</span></span>

> [!NOTE]
> <span data-ttu-id="87e1b-152">Wenn Sie im Build- [](#build-and-run-the-sample) und Ausführungsschritt einen anderen Port verwendet haben, stellen Sie sicher, dass Sie zum Einrichten des Tunnels dieselbe Portnummer `ngrok` verwenden.</span><span class="sxs-lookup"><span data-stu-id="87e1b-152">If you have used a different port in the [build and run](#build-and-run-the-sample) step, ensure you use the same port number to setup the `ngrok` tunnel.</span></span>

> [!TIP]
> <span data-ttu-id="87e1b-153">Es ist eine gute Idee, in einem `ngrok` anderen Terminalfenster ausgeführt zu werden.</span><span class="sxs-lookup"><span data-stu-id="87e1b-153">It is a good idea to run `ngrok` in a different terminal window.</span></span> <span data-ttu-id="87e1b-154">Dies geschieht, um `ngrok` die Ausführung zu unterlaufen, ohne die App zu stören.</span><span class="sxs-lookup"><span data-stu-id="87e1b-154">This is done to keep `ngrok` from running without interfering with the app.</span></span> <span data-ttu-id="87e1b-155">Sie müssen die App beenden, neu erstellen und erneut ausführen.</span><span class="sxs-lookup"><span data-stu-id="87e1b-155">You have to stop, rebuild, and rerun the app.</span></span> <span data-ttu-id="87e1b-156">Die `ngrok` Sitzung enthält nützliche Debugginginformationen in diesem Fenster.</span><span class="sxs-lookup"><span data-stu-id="87e1b-156">The `ngrok` session provides useful debugging information in this window.</span></span>

<span data-ttu-id="87e1b-157">Die App ist nur während der aktuellen Sitzung auf Ihrem Computer verfügbar.</span><span class="sxs-lookup"><span data-stu-id="87e1b-157">The app is only available during the current session on your computer.</span></span> <span data-ttu-id="87e1b-158">Wenn der Computer heruntergefahren wird oder in den Ruhezustand geht, ist der Dienst nicht mehr verfügbar.</span><span class="sxs-lookup"><span data-stu-id="87e1b-158">If the machine is shut down or goes to sleep, the service is no longer available.</span></span> <span data-ttu-id="87e1b-159">Denken Sie daran, wenn Sie die App für Tests für andere Benutzer freigeben.</span><span class="sxs-lookup"><span data-stu-id="87e1b-159">Remember this when you share the app for testing to other users.</span></span> <span data-ttu-id="87e1b-160">Wenn Sie den Dienst neu starten müssen, gibt die App eine neue Adresse zurück, und Sie müssen jeden Speicherort aktualisieren, der diese Adresse verwendet.</span><span class="sxs-lookup"><span data-stu-id="87e1b-160">If you have to restart the service, the app returns a new address and you must update every location that uses that address.</span></span> <span data-ttu-id="87e1b-161">Die kostenpflichtige Version von `ngrok` hat diese Einschränkung nicht.</span><span class="sxs-lookup"><span data-stu-id="87e1b-161">The paid version of `ngrok` does not have this limitation.</span></span>

### <a name="host-in-azure"></a><span data-ttu-id="87e1b-162">Host in Azure</span><span class="sxs-lookup"><span data-stu-id="87e1b-162">Host in Azure</span></span>

<span data-ttu-id="87e1b-163">Microsoft Azure hostet Ihre .NET-Anwendung auf einer kostenlosen Ebene mithilfe der freigegebenen Infrastruktur.</span><span class="sxs-lookup"><span data-stu-id="87e1b-163">Microsoft Azure hosts your .NET application on a free tier using shared infrastructure.</span></span> <span data-ttu-id="87e1b-164">Dies ist ausreichend, um das Beispiel ausführen zu `Hello World` können.</span><span class="sxs-lookup"><span data-stu-id="87e1b-164">This is sufficient to run the `Hello World` sample.</span></span> <span data-ttu-id="87e1b-165">Weitere Informationen finden Sie unter [Erstellen eines neuen kostenlosen Azure-Kontos](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="87e1b-165">For more information, see [creating a new free Azure account](https://azure.microsoft.com/free/).</span></span>

<span data-ttu-id="87e1b-166">Visual Studio bietet integrierte Unterstützung für die App-Bereitstellung für verschiedene Anbieter, einschließlich Azure.</span><span class="sxs-lookup"><span data-stu-id="87e1b-166">Visual Studio has built-in support for app deployment to different providers, including Azure.</span></span>

<img width="530px" alt="Visual Studio" src="~/assets/images/get-started/publishtoazure1.png"/>

[!include [Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

## <a name="update-the-credentials-for-your-hosted-app"></a><span data-ttu-id="87e1b-167">Aktualisieren der Anmeldeinformationen für Ihre gehostete App</span><span class="sxs-lookup"><span data-stu-id="87e1b-167">Update the credentials for your hosted app</span></span>

<span data-ttu-id="87e1b-168">Für die Beispiel-App müssen die Umgebungsvariablen auf die Werte festgelegt werden, die Sie in der Textdatei gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="87e1b-168">The sample app requires the environment variables to be set to the values that you saved in the text file.</span></span>

<span data-ttu-id="87e1b-169">die Datei `appsettings.json` öffnen.</span><span class="sxs-lookup"><span data-stu-id="87e1b-169">Open the `appsettings.json` file.</span></span> <span data-ttu-id="87e1b-170">Aktualisieren Sie **den MicrosoftAppId-Wert** mit Ihrer Bot-ID, die Sie in der Textdatei gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="87e1b-170">Update the **MicrosoftAppId** value with your bot ID that you saved in the text file.</span></span> <span data-ttu-id="87e1b-171">Aktualisieren Sie **microsoftAppPassword** mit dem von Ihnen gespeicherten Botkennwort.</span><span class="sxs-lookup"><span data-stu-id="87e1b-171">Update the **MicrosoftAppPassword** with the bot password you saved.</span></span>

<img width="560px" alt="Setting the keys" src="~/assets/images/get-started/get-started-net-azure-add-keys.png"/>

<span data-ttu-id="87e1b-172">Nachdem diese Änderungen vorgenommen wurden, erstellen Sie die App neu.</span><span class="sxs-lookup"><span data-stu-id="87e1b-172">After these changes are made, rebuild the app.</span></span> <span data-ttu-id="87e1b-173">Wenn Sie ngrok verwenden, führen Sie die App lokal aus, und wenn Sie in Azure hosten, stellen Sie die App erneut bereit.</span><span class="sxs-lookup"><span data-stu-id="87e1b-173">If you are using ngrok, run the app locally, and if you are hosting in Azure, redeploy the app.</span></span>

## <a name="configure-the-app-tab"></a><span data-ttu-id="87e1b-174">Konfigurieren der Registerkarte "App"</span><span class="sxs-lookup"><span data-stu-id="87e1b-174">Configure the app tab</span></span>

<span data-ttu-id="87e1b-175">Nachdem Sie die App in einem Team installiert haben, müssen Sie sie so konfigurieren, dass Inhalte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="87e1b-175">Once you install the app into a team, you must configure it to show content.</span></span> <span data-ttu-id="87e1b-176">Wechseln Sie zu einem Kanal im Team, in dem Sie die Beispiel-App installiert haben, und wählen Sie die Schaltfläche **"+"** aus, um eine neue Registerkarte hinzuzufügen. Wählen **Sie Hello World** in der **Registerkartenliste** Hinzufügen aus.</span><span class="sxs-lookup"><span data-stu-id="87e1b-176">Go to a channel in the team where you installed the sample app and select the **'+'** button to add a new tab. Choose **Hello World** from the **Add a tab** list.</span></span> <span data-ttu-id="87e1b-177">Es wird ein Konfigurationsdialogfeld angezeigt, mit dem Sie die Registerkarte auswählen können, die in diesem Kanal angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="87e1b-177">A configuration dialog box is displayed that enables you to choose the tab to display in this channel.</span></span> <span data-ttu-id="87e1b-178">Nachdem Sie die Registerkarte ausgewählt und die Option **Speichern** ausgewählt haben, wird die Registerkarte `Hello World` mit der Registerkarte geladen.</span><span class="sxs-lookup"><span data-stu-id="87e1b-178">After you select the tab and select **Save** the `Hello World` tab is loaded with the tab.</span></span>

<img width="530px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png" />

### <a name="test-your-bot-in-teams"></a><span data-ttu-id="87e1b-179">Testen Des Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="87e1b-179">Test your bot in Teams</span></span>

<span data-ttu-id="87e1b-180">Jetzt können Sie den Bot in der Teams.</span><span class="sxs-lookup"><span data-stu-id="87e1b-180">Now you can test the bot in Teams.</span></span> <span data-ttu-id="87e1b-181">Wählen Sie einen Kanal im Team aus, in dem Sie Ihre App registriert haben, und geben Sie `@your-bot-name` ein.</span><span class="sxs-lookup"><span data-stu-id="87e1b-181">Select a channel in the team where you registered your app and type `@your-bot-name`.</span></span> <span data-ttu-id="87e1b-182">Dies wird als Erwähnung **\@ bezeichnet.**</span><span class="sxs-lookup"><span data-stu-id="87e1b-182">This is called an **\@mention**.</span></span> <span data-ttu-id="87e1b-183">Der Bot antwortet auf jede nachricht, die Sie senden.</span><span class="sxs-lookup"><span data-stu-id="87e1b-183">The bot replies to any message that you send.</span></span>

<img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png" />

### <a name="test-your-messaging-extension"></a><span data-ttu-id="87e1b-184">Testen Der Messagingerweiterung</span><span class="sxs-lookup"><span data-stu-id="87e1b-184">Test your messaging extension</span></span>

<span data-ttu-id="87e1b-185">Zum Testen Ihrer Messagingerweiterung können Sie **... unter** dem Eingabefeld in der Unterhaltungsansicht auswählen.</span><span class="sxs-lookup"><span data-stu-id="87e1b-185">To test your messaging extension, you can select **...** below the input box in your conversation view.</span></span> <span data-ttu-id="87e1b-186">Ein Menü mit der **App "Hello World"** wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="87e1b-186">A menu with the **'Hello World'** app is displayed.</span></span> <span data-ttu-id="87e1b-187">Wenn Sie sie auswählen, wird eine Reihe zufälliger Texte angezeigt.</span><span class="sxs-lookup"><span data-stu-id="87e1b-187">When you select it, a set of random texts is displayed.</span></span> <span data-ttu-id="87e1b-188">Sie können einen zufälligen Text auswählen, der in Ihre Unterhaltung eingefügt wird.</span><span class="sxs-lookup"><span data-stu-id="87e1b-188">You can select one of the random text and that is inserted into your conversation.</span></span>

<img width="530px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu.png" />

<img width="530px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result.png" />

<span data-ttu-id="87e1b-189">Wählen Sie einen der zufälligen Text aus.</span><span class="sxs-lookup"><span data-stu-id="87e1b-189">Select one of the random text.</span></span> <span data-ttu-id="87e1b-190">Es wird eine Karte angezeigt, die mit Ihrer eigenen Nachricht formatiert und zum Senden bereit ist.</span><span class="sxs-lookup"><span data-stu-id="87e1b-190">A card formatted and ready to send with your own message is shown.</span></span>

<img width="530px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />
