---
title: 'Lernprogramm – Erstellen Ihrer ersten App mithilfe von C #'
description: 'Erfahren Sie, wie Sie mit dem Erstellen von Microsoft #A0 mit C# oder .NET beginnen.'
keywords: Erste Schritte .net c# csharp
ms.custom: scenarios:getting-started; languages:ASP.NET,C#
ms.topic: tutorial
ms.date: 11/09/2018
ms.openlocfilehash: 29cc4e0f434bf9ece9c6073af84627acc048b628
ms.sourcegitcommit: 6ff8d1244ac386641ebf9401804b8df3854b02dc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/18/2021
ms.locfileid: "50294754"
---
# <a name="create-your-first-teams-app-using-c-or-net"></a><span data-ttu-id="8a00a-104">Erstellen Ihrer ersten #A0 mithilfe von C# oder .NET</span><span class="sxs-lookup"><span data-stu-id="8a00a-104">Create your first Teams app using C# or .NET</span></span>

<span data-ttu-id="8a00a-105">Dieses Lernprogramm hilft Ihnen beim Erstellen einer Microsoft #A0 mit C# oder .NET.</span><span class="sxs-lookup"><span data-stu-id="8a00a-105">This tutorial helps you to create a Microsoft Teams app using C# or .NET.</span></span>

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="GetPrerequisites"></a>

## <a name="get-prerequisites"></a><span data-ttu-id="8a00a-106">Erforderliche Komponenten erhalten</span><span class="sxs-lookup"><span data-stu-id="8a00a-106">Get prerequisites</span></span>

<span data-ttu-id="8a00a-107">Zum Abschließen dieses Lernprogramms müssen Sie die folgenden Tools erhalten:</span><span class="sxs-lookup"><span data-stu-id="8a00a-107">To complete this tutorial, you need to get the following tools:</span></span>

- [<span data-ttu-id="8a00a-108">Installieren von Git</span><span class="sxs-lookup"><span data-stu-id="8a00a-108">Install Git</span></span>](https://git-scm.com/downloads)
- <span data-ttu-id="8a00a-109">[Installieren Visual Studio](https://www.visualstudio.com/downloads/).</span><span class="sxs-lookup"><span data-stu-id="8a00a-109">[Install Visual Studio](https://www.visualstudio.com/downloads/).</span></span> <span data-ttu-id="8a00a-110">Sie können die kostenlose Community edition installieren.</span><span class="sxs-lookup"><span data-stu-id="8a00a-110">You can install the free community edition.</span></span>

<span data-ttu-id="8a00a-111">Wenn während der Installation eine Option zum PATH hinzugefügt werden `git` kann, wählen Sie sie aus.</span><span class="sxs-lookup"><span data-stu-id="8a00a-111">During installation, if there is an option to add `git` to the PATH, choose it.</span></span>

<span data-ttu-id="8a00a-112">Führen Sie in einem Terminalfenster den folgenden Befehl aus, um die Installation zu `git` überprüfen:</span><span class="sxs-lookup"><span data-stu-id="8a00a-112">In a terminal window, run the following command to verify your `git` installation:</span></span>

```bash
$ git --version
git version 2.17.1.windows.2

```

> [!NOTE]
> <span data-ttu-id="8a00a-113">Verwenden Sie ein geeignetes Terminalfenster auf Ihrer Plattform.</span><span class="sxs-lookup"><span data-stu-id="8a00a-113">Use a suitable terminal window on your platform.</span></span> <span data-ttu-id="8a00a-114">In diesen Beispielen wird Bash verwendet, aber auf den meisten Plattformen ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="8a00a-114">These examples use Bash but run on most platforms.</span></span>

<span data-ttu-id="8a00a-115">Stellen Sie sicher, dass Sie die neueste Version von Visual Studio starten und Updates installieren.</span><span class="sxs-lookup"><span data-stu-id="8a00a-115">Make sure to launch the latest version of Visual Studio and install any updates.</span></span>

<span data-ttu-id="8a00a-116">Sie können dasselbe Terminalfenster verwenden, um die Befehle in diesem Lernprogramm auszuführen.</span><span class="sxs-lookup"><span data-stu-id="8a00a-116">You can use the same terminal window to run the commands in this tutorial.</span></span>

<a name="DownloadSample"></a>

## <a name="download-the-sample"></a><span data-ttu-id="8a00a-117">Herunterladen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="8a00a-117">Download the sample</span></span>

<span data-ttu-id="8a00a-118">Sie können mit einem einfachen [Hello, World! beginnen.](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-hello-world/csharp)</span><span class="sxs-lookup"><span data-stu-id="8a00a-118">You can get started with a simple [Hello, World!](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-hello-world/csharp)</span></span> <span data-ttu-id="8a00a-119">Beispiel in C#.</span><span class="sxs-lookup"><span data-stu-id="8a00a-119">sample in C#.</span></span> <span data-ttu-id="8a00a-120">Führen Sie in einem Terminalfenster den folgenden Befehl aus, um das Beispielrepository auf ihren lokalen Computer zu klonen:</span><span class="sxs-lookup"><span data-stu-id="8a00a-120">In a terminal window, run the following command to clone the sample repository to your local machine:</span></span>

```bash
git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
```

> [!TIP]
> <span data-ttu-id="8a00a-121">Sie können [dieses Repository forken,](https://help.github.com/articles/fork-a-repo/) [um](https://github.com/OfficeDev/Microsoft-Teams-Samples) Ihre Änderungen an GitHub zu ändern und zu speichern.</span><span class="sxs-lookup"><span data-stu-id="8a00a-121">You can [fork](https://help.github.com/articles/fork-a-repo/) this [repo](https://github.com/OfficeDev/Microsoft-Teams-Samples) to modify and save your changes to GitHub for reference.</span></span>

<a name="BuildRun"></a>

## <a name="build-and-run-the-sample"></a><span data-ttu-id="8a00a-122">Erstellen und Ausführen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="8a00a-122">Build and run the sample</span></span>

<span data-ttu-id="8a00a-123">Nachdem das Repository geklont wurde, öffnen Sie mithilfe Visual Studio die Lösungsdatei aus dem `Microsoft.Teams.Samples.HelloWorld.sln` **Verzeichnis Microsoft-Teams-Samples/samples/app-hello-world/csharp** des Beispiels, und wählen Sie aus dem Menü `Build Solution` `Build` aus.</span><span class="sxs-lookup"><span data-stu-id="8a00a-123">After the repo is cloned, use Visual Studio to open the solution file `Microsoft.Teams.Samples.HelloWorld.sln` from the **Microsoft-Teams-Samples/samples/app-hello-world/csharp** directory of the sample and select `Build Solution` from the `Build` menu.</span></span> <span data-ttu-id="8a00a-124">Zum Ausführen des Beispiels drücken `F5` Oder wählen Sie aus dem Menü `Start Debugging` `Debug` aus.</span><span class="sxs-lookup"><span data-stu-id="8a00a-124">To run the sample press `F5` or choose `Start Debugging` from the `Debug` menu.</span></span>

<span data-ttu-id="8a00a-125">Wenn die App gestartet wird, wird ein Browserfenster geöffnet, in dem der Stamm der App gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="8a00a-125">When the app starts, a browser window opens with the root of the app launched.</span></span> <span data-ttu-id="8a00a-126">Sie können zu den folgenden URLs navigieren, um zu überprüfen, ob alle App-URLs geladen werden:</span><span class="sxs-lookup"><span data-stu-id="8a00a-126">You can navigate to the following URLs to verify that all the app URLs are loading:</span></span>

- [https://localhost:44327/](https://localhost:44327/)
- [https://localhost:44327/hello](https://localhost:44327/hello)
- [https://localhost:44327/first](https://localhost:44327/first)
- <span data-ttu-id="8a00a-127">[https://localhost:44327/second]https://localhost:44327/second)</span><span class="sxs-lookup"><span data-stu-id="8a00a-127">[https://localhost:44327/second]https://localhost:44327/second)</span></span>

<a name="HostSample"></a>

> [!Note]
> <span data-ttu-id="8a00a-128">Wenn sie einen Fehler `Could not find a part of the path … bin\roslyn\csc.exe` erhalten, aktualisieren Sie das Paket mit dem Befehl `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r` .</span><span class="sxs-lookup"><span data-stu-id="8a00a-128">If you receive an error `Could not find a part of the path … bin\roslyn\csc.exe`, update the package with the command `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r`.</span></span> <span data-ttu-id="8a00a-129">Weitere Informationen finden Sie in [dieser Frage unter StackOverflow](https://stackoverflow.com/questions/32780315).</span><span class="sxs-lookup"><span data-stu-id="8a00a-129">For more information, see [this question on StackOverflow](https://stackoverflow.com/questions/32780315).</span></span>

## <a name="host-the-sample-app"></a><span data-ttu-id="8a00a-130">Hosten der Beispiel-App</span><span class="sxs-lookup"><span data-stu-id="8a00a-130">Host the sample app</span></span>

<span data-ttu-id="8a00a-131">Apps in Microsoft Teams sind Webanwendungen, die eine oder mehrere Funktionen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="8a00a-131">Apps in Microsoft Teams are web applications that provide one or more capabilities.</span></span> <span data-ttu-id="8a00a-132">Damit die Teams-Plattform Ihre App laden kann, muss Ihre App über das Internet erreichbar sein.</span><span class="sxs-lookup"><span data-stu-id="8a00a-132">For the Teams platform to load your app, your app must be reachable from the internet.</span></span> <span data-ttu-id="8a00a-133">Damit Ihre App über das Internet erreichbar ist, müssen Sie Ihre App hosten.</span><span class="sxs-lookup"><span data-stu-id="8a00a-133">To make your app reachable from the internet, you need to host your app.</span></span> <span data-ttu-id="8a00a-134">Sie können sie entweder kostenlos in Microsoft Azure hosten oder einen Tunnel für den lokalen Prozess auf Ihrem Entwicklungscomputer mit `ngrok` erstellen.</span><span class="sxs-lookup"><span data-stu-id="8a00a-134">You can either host it in Microsoft Azure for free or create a tunnel to the local process on your development machine using `ngrok`.</span></span> <span data-ttu-id="8a00a-135">Wenn Sie mit dem Hosten Ihrer App fertig sind, notieren Sie sich die Stamm-URL.</span><span class="sxs-lookup"><span data-stu-id="8a00a-135">When you finish hosting your app, note its root URL.</span></span> <span data-ttu-id="8a00a-136">Beispiel: `https://yourteamsapp.ngrok.io` oder `https://yourteamsapp.azurewebsites.net` .</span><span class="sxs-lookup"><span data-stu-id="8a00a-136">For example, `https://yourteamsapp.ngrok.io` or `https://yourteamsapp.azurewebsites.net`.</span></span>

### <a name="tunnel-using-ngrok"></a><span data-ttu-id="8a00a-137">Tunnel mit ngrok</span><span class="sxs-lookup"><span data-stu-id="8a00a-137">Tunnel using ngrok</span></span>

<span data-ttu-id="8a00a-138">Für schnelle Tests können Sie die App auf Ihrem lokalen Computer ausführen und über einen Webendpunkt einen Tunnel dafür erstellen.</span><span class="sxs-lookup"><span data-stu-id="8a00a-138">For quick testing, you can run the app on your local machine and create a tunnel to it through a web endpoint.</span></span> <span data-ttu-id="8a00a-139">[ngrok](https://ngrok.com) ist ein kostenloses Tool, mit dem Sie eine Webadresse wie erhalten `https://d0ac14a5.ngrok.io` können.</span><span class="sxs-lookup"><span data-stu-id="8a00a-139">[ngrok](https://ngrok.com) is a free tool with which you can get a web address such as `https://d0ac14a5.ngrok.io`.</span></span> <span data-ttu-id="8a00a-140">Sie können [ngrok](https://ngrok.com/download) herunterladen und installieren.</span><span class="sxs-lookup"><span data-stu-id="8a00a-140">You can [download and install](https://ngrok.com/download) ngrok.</span></span> <span data-ttu-id="8a00a-141">Stellen Sie sicher, dass Sie es einem Speicherort in Ihrer `PATH` hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="8a00a-141">Make sure you add it to a location in your `PATH`.</span></span>

<span data-ttu-id="8a00a-142">Öffnen Sie nach der Installation von ngrok ein neues Terminalfenster, und führen Sie den folgenden Befehl aus, um einen Tunnel zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="8a00a-142">After you install ngrok, open a new terminal window and run the following command to create a tunnel:</span></span>

```bash
ngrok http 44327 -host-header=localhost:44327
```

<span data-ttu-id="8a00a-143">Im Beispiel wird Port 44327 verwendet, um ihn anzugeben.</span><span class="sxs-lookup"><span data-stu-id="8a00a-143">The sample uses port 44327 be sure to specify it.</span></span>

<span data-ttu-id="8a00a-144">Ngrok lauscht Anforderungen aus dem Internet und leitet sie an Ihre App weiter, die unter Port 44327 ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="8a00a-144">Ngrok listens to requests from the internet and routes them to your app running on port 44327.</span></span> <span data-ttu-id="8a00a-145">Um dies zu überprüfen, öffnen Sie Ihren Browser, und `https://d0ac14a5.ngrok.io/hello` wechseln Sie zu, um die Hello-Seite Ihrer App zu laden.</span><span class="sxs-lookup"><span data-stu-id="8a00a-145">To verify, open your browser and go to `https://d0ac14a5.ngrok.io/hello` to load your app's hello page.</span></span> <span data-ttu-id="8a00a-146">Verwenden Sie anstelle dieser URL die Weiterleitungsadresse, die von ngrok in Ihrer Konsolensitzung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8a00a-146">Instead of this URL, use the forwarding address displayed by ngrok in your console session.</span></span>

> [!NOTE]
> <span data-ttu-id="8a00a-147">Wenn Sie im Build- [](#build-and-run-the-sample) und Ausführungsschritt einen anderen Port verwendet haben, stellen Sie sicher, dass Sie zum Einrichten des Tunnels dieselbe Portnummer `ngrok` verwenden.</span><span class="sxs-lookup"><span data-stu-id="8a00a-147">If you have used a different port in the [build and run](#build-and-run-the-sample) step, make sure you use the same port number to setup the `ngrok` tunnel.</span></span>

> [!TIP]
> <span data-ttu-id="8a00a-148">Es ist eine gute Idee, in einem `ngrok` anderen Terminalfenster ausgeführt zu werden.</span><span class="sxs-lookup"><span data-stu-id="8a00a-148">It is a good idea to run `ngrok` in a different terminal window.</span></span> <span data-ttu-id="8a00a-149">Dies geschieht, um zu verhindern, dass ngrok ausgeführt wird, ohne die App zu stören, die Sie beenden, neu erstellen und erneut ausführen müssen.</span><span class="sxs-lookup"><span data-stu-id="8a00a-149">This is done to keep ngrok from running without interfering with the app, which you have to stop, rebuild, and rerun.</span></span> <span data-ttu-id="8a00a-150">Die `ngrok` Sitzung enthält nützliche Debugginginformationen in diesem Fenster.</span><span class="sxs-lookup"><span data-stu-id="8a00a-150">The `ngrok` session provides useful debugging information in this window.</span></span>

<span data-ttu-id="8a00a-151">Die App ist nur während der aktuellen Sitzung auf Ihrem Entwicklungscomputer verfügbar.</span><span class="sxs-lookup"><span data-stu-id="8a00a-151">The app is only available during the current session on your development machine.</span></span> <span data-ttu-id="8a00a-152">Wenn der Computer heruntergefahren wird oder in den Ruhezustand geht, ist der Dienst nicht mehr verfügbar.</span><span class="sxs-lookup"><span data-stu-id="8a00a-152">If the machine is shut down or goes to sleep, the service is no longer available.</span></span> <span data-ttu-id="8a00a-153">Denken Sie daran, wenn Sie die App für Tests für andere Benutzer freigeben.</span><span class="sxs-lookup"><span data-stu-id="8a00a-153">Remember this when you share the app for testing to other users.</span></span> <span data-ttu-id="8a00a-154">Wenn Sie den Dienst neu starten müssen, gibt die App eine neue Adresse zurück, und Sie müssen jeden Speicherort aktualisieren, der diese Adresse verwendet.</span><span class="sxs-lookup"><span data-stu-id="8a00a-154">If you have to restart the service, the app returns a new address and you must update every location that uses that address.</span></span> <span data-ttu-id="8a00a-155">Die kostenpflichtige Version von ngrok hat diese Einschränkung nicht.</span><span class="sxs-lookup"><span data-stu-id="8a00a-155">The paid version of ngrok does not have this limitation.</span></span>

### <a name="host-in-azure"></a><span data-ttu-id="8a00a-156">Host in Azure</span><span class="sxs-lookup"><span data-stu-id="8a00a-156">Host in Azure</span></span>

<span data-ttu-id="8a00a-157">Microsoft Azure hostet Ihre .NET-Anwendung auf einer kostenlosen Ebene mithilfe der freigegebenen Infrastruktur.</span><span class="sxs-lookup"><span data-stu-id="8a00a-157">Microsoft Azure hosts your .NET application on a free tier using shared infrastructure.</span></span> <span data-ttu-id="8a00a-158">Dies ist ausreichend, um das Beispiel ausführen zu `Hello World` können.</span><span class="sxs-lookup"><span data-stu-id="8a00a-158">This is sufficient to run the `Hello World` sample.</span></span> <span data-ttu-id="8a00a-159">Weitere Informationen finden Sie unter [Erstellen eines neuen kostenlosen Kontos](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="8a00a-159">For more information, see [creating a new free account](https://azure.microsoft.com/free/).</span></span>

<span data-ttu-id="8a00a-160">Visual Studio bietet integrierte Unterstützung für die App-Bereitstellung für verschiedene Anbieter, einschließlich Azure.</span><span class="sxs-lookup"><span data-stu-id="8a00a-160">Visual Studio has built-in support for app deployment to different providers, including Azure.</span></span>

<img width="530px" alt="Visual Studio" src="~/assets/images/get-started/publishtoazure1.png"/>

[!include [Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

## <a name="update-the-credentials-for-your-hosted-app"></a><span data-ttu-id="8a00a-161">Aktualisieren der Anmeldeinformationen für Ihre gehostete App</span><span class="sxs-lookup"><span data-stu-id="8a00a-161">Update the credentials for your hosted app</span></span>

<span data-ttu-id="8a00a-162">Die Beispiel-App erfordert, dass die folgenden Umgebungsvariablen auf die Werte festgelegt werden, die Sie zuvor notieren.</span><span class="sxs-lookup"><span data-stu-id="8a00a-162">The sample app requires the following environment variables to be set to the values you made a note of earlier.</span></span>

<span data-ttu-id="8a00a-163">Öffnen Sie die appsettings.json-Datei.</span><span class="sxs-lookup"><span data-stu-id="8a00a-163">Open up the appsettings.json file.</span></span> <span data-ttu-id="8a00a-164">Aktualisieren Sie *den MicrosoftAppId-Wert* mit Ihrer Bot-ID, die Sie zuvor gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="8a00a-164">Update the *MicrosoftAppId* value with your Bot ID that you saved earlier.</span></span> <span data-ttu-id="8a00a-165">Aktualisieren Sie *microsoftAppPassword* mit dem bot-Kennwort, das Sie zuvor gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="8a00a-165">Update the *MicrosoftAppPassword* with the Bot password you saved earlier.</span></span>

<img width="560px" alt="Setting the keys" src="~/assets/images/get-started/get-started-net-azure-add-keys.png"/>

<span data-ttu-id="8a00a-166">Nachdem diese Änderungen vorgenommen wurden, erstellen Sie die App neu.</span><span class="sxs-lookup"><span data-stu-id="8a00a-166">Once these changes are made, rebuild the app.</span></span> <span data-ttu-id="8a00a-167">Wenn Sie ngrok verwenden, führen Sie die App lokal aus, und wenn Sie in Azure hosten, stellen Sie die App erneut bereit.</span><span class="sxs-lookup"><span data-stu-id="8a00a-167">If you are using ngrok, run the app locally, and if you are hosting in Azure redeploy the app.</span></span>

## <a name="configure-the-app-tab"></a><span data-ttu-id="8a00a-168">Konfigurieren der Registerkarte "App"</span><span class="sxs-lookup"><span data-stu-id="8a00a-168">Configure the app tab</span></span>

<span data-ttu-id="8a00a-169">Nachdem Sie die App in einem Team installiert haben, müssen Sie sie so konfigurieren, dass Inhalte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="8a00a-169">Once you install the app into a team, you will need to configure it to show content.</span></span> <span data-ttu-id="8a00a-170">Wechseln Sie zu einem Kanal im Team, in dem Sie die Beispiel-App installiert haben, und klicken Sie auf die Schaltfläche **"+",** um eine neue Registerkarte hinzuzufügen. Sie können dann aus `Hello World` der Registerkartenliste **Hinzufügen** auswählen.</span><span class="sxs-lookup"><span data-stu-id="8a00a-170">Go to a channel in the team where you installed the sample app and click on the **'+'** button to add a new tab. You can then choose `Hello World` from the **Add a tab** list.</span></span> <span data-ttu-id="8a00a-171">Anschließend wird ihnen ein Konfigurationsdialogfeld angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8a00a-171">You will then be presented with a configuration dialog.</span></span> <span data-ttu-id="8a00a-172">In diesem Dialogfeld können Sie auswählen, welche Registerkarte in diesem Kanal angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="8a00a-172">This dialog will let you choose which tab to display in this channel.</span></span> <span data-ttu-id="8a00a-173">Sobald Sie die Registerkarte ausgewählt haben und auf klicken, wird die Registerkarte mit der von Ihnen ausgewählten `Save` `Hello World` Registerkarte geladen.</span><span class="sxs-lookup"><span data-stu-id="8a00a-173">Once you select the tab and click on `Save` then you can see the `Hello World` tab loaded with the tab you chose.</span></span>

<img width="530px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png" />

### <a name="test-your-bot-in-teams"></a><span data-ttu-id="8a00a-174">Testen Des Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="8a00a-174">Test your bot in Teams</span></span>

<span data-ttu-id="8a00a-175">Sie können jetzt mit dem Bot in Teams interagieren.</span><span class="sxs-lookup"><span data-stu-id="8a00a-175">You can now interact with the bot in Teams.</span></span> <span data-ttu-id="8a00a-176">Wählen Sie einen Kanal im Team aus, in dem Sie Ihre App registriert haben, und geben Sie `@your-bot-name` ein.</span><span class="sxs-lookup"><span data-stu-id="8a00a-176">Choose a channel in the team where you registered your app and type `@your-bot-name`.</span></span> <span data-ttu-id="8a00a-177">Dies wird als Erwähnung **\@ bezeichnet.**</span><span class="sxs-lookup"><span data-stu-id="8a00a-177">This is called an **\@mention**.</span></span> <span data-ttu-id="8a00a-178">Alle Nachrichten, die Sie an den Bot senden, werden als Antwort an Sie zurückgeschickt.</span><span class="sxs-lookup"><span data-stu-id="8a00a-178">Whatever message you send to the bot will be sent back to you as a reply.</span></span>

<img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png" />

### <a name="test-your-messaging-extension"></a><span data-ttu-id="8a00a-179">Testen Der Messagingerweiterung</span><span class="sxs-lookup"><span data-stu-id="8a00a-179">Test your messaging extension</span></span>

<span data-ttu-id="8a00a-180">Um Ihre Messagingerweiterung zu testen, können Sie auf die drei Punkte unter dem Eingabefeld in der Unterhaltungsansicht klicken.</span><span class="sxs-lookup"><span data-stu-id="8a00a-180">To test your messaging extension, you can click on the three dots below the input box in your conversation view.</span></span> <span data-ttu-id="8a00a-181">Ein Menü wird mit der **"Hello World"-App** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8a00a-181">A menu will pop up with the **'Hello World'** app in it.</span></span> <span data-ttu-id="8a00a-182">Wenn Sie darauf klicken, wird eine Reihe zufälliger Texte angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8a00a-182">When you click it, you will see a bunch of random texts showing up.</span></span> <span data-ttu-id="8a00a-183">Sie können einen beliebigen auswählen, und er wird in Ihre Unterhaltung eingefügt.</span><span class="sxs-lookup"><span data-stu-id="8a00a-183">You can choose any one of them and it is inserted into your conversation.</span></span>

<img width="530px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu.png" />

<img width="530px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result.png" />

<span data-ttu-id="8a00a-184">Wählen Sie einen der zufälligen Texte aus, und unten wird eine Karte formatiert und kann mit Ihrer eigenen Nachricht gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="8a00a-184">Choose one of the random texts, and you will see a card formatted and ready to send with your own message at the bottom.</span></span>

<img width="530px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />
