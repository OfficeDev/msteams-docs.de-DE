---
title: 'Tutorial - Erstellen Sie Ihre erste App mit C #'
description: Erfahren Sie, wie Sie mit dem Erstellen Microsoft Teams-Apps mit C- oder .NET beginnen.
keywords: Erste Schritte .net c' csharp
ms.custom: scenarios:getting-started; languages:ASP.NET,C#
localization_priority: Normal
ms.topic: tutorial
ms.date: 11/09/2018
ms.openlocfilehash: eaa37f1ccb7944ee18bb62ae47882dc4a715b165
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566887"
---
# <a name="create-your-first-teams-app-using-c"></a><span data-ttu-id="8ea1a-104">Erstellen Sie Ihre erste Teams-App mit C #</span><span class="sxs-lookup"><span data-stu-id="8ea1a-104">Create your first Teams app using C#</span></span>

<span data-ttu-id="8ea1a-105">In diesem Tutorial können Sie eine Microsoft Teams-App mit C-Code erstellen.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-105">This tutorial helps you to create a Microsoft Teams app using C#.</span></span> <span data-ttu-id="8ea1a-106">Dazu müssen Sie Folgendes tun:</span><span class="sxs-lookup"><span data-stu-id="8ea1a-106">To do this, you must:</span></span>

* <span data-ttu-id="8ea1a-107">Vorbereiten der Umgebung</span><span class="sxs-lookup"><span data-stu-id="8ea1a-107">Prepare your environment</span></span>
* <span data-ttu-id="8ea1a-108">Voraussetzungen abrufen</span><span class="sxs-lookup"><span data-stu-id="8ea1a-108">Get prerequisites</span></span>
* <span data-ttu-id="8ea1a-109">Laden Sie das Beispiel herunter</span><span class="sxs-lookup"><span data-stu-id="8ea1a-109">Download the sample</span></span>
* <span data-ttu-id="8ea1a-110">Erstellen und Ausführen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="8ea1a-110">Build and run the sample</span></span>
* <span data-ttu-id="8ea1a-111">Hosten der Beispiel-App</span><span class="sxs-lookup"><span data-stu-id="8ea1a-111">Host the sample app</span></span>
* <span data-ttu-id="8ea1a-112">Aktualisieren der Anmeldeinformationen für Ihre gehostete App</span><span class="sxs-lookup"><span data-stu-id="8ea1a-112">Update the credentials for your hosted app</span></span>
* <span data-ttu-id="8ea1a-113">Konfigurieren der App-Registerkarte</span><span class="sxs-lookup"><span data-stu-id="8ea1a-113">Configure the app tab</span></span>

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="GetPrerequisites"></a>

## <a name="get-prerequisites"></a><span data-ttu-id="8ea1a-114">Voraussetzungen abrufen</span><span class="sxs-lookup"><span data-stu-id="8ea1a-114">Get prerequisites</span></span>

<span data-ttu-id="8ea1a-115">Um dieses Tutorial abzuschließen, müssen Sie die folgenden Tools installieren:</span><span class="sxs-lookup"><span data-stu-id="8ea1a-115">To complete this tutorial, you need to install the following tools:</span></span>

- [<span data-ttu-id="8ea1a-116">Installieren von Git</span><span class="sxs-lookup"><span data-stu-id="8ea1a-116">Install Git</span></span>](https://git-scm.com/downloads)
- [<span data-ttu-id="8ea1a-117">Installieren von Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8ea1a-117">Install Visual Studio</span></span>](https://www.visualstudio.com/downloads/)

<span data-ttu-id="8ea1a-118">Sie können die kostenlose Community-Edition von Visual Studio installieren.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-118">You can install the free community edition of Visual Studio.</span></span> <span data-ttu-id="8ea1a-119">Wenn es während der Installation eine Option zum Hinzufügen `git` zum Pfad gibt, wählen Sie ihn aus.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-119">During installation, if there is an option to add `git` to the path, select it.</span></span> <span data-ttu-id="8ea1a-120">Führen Sie in einem Terminalfenster den folgenden Befehl aus, um Ihre Installation zu `git` überprüfen:</span><span class="sxs-lookup"><span data-stu-id="8ea1a-120">In a terminal window, run the following command to verify your `git` installation:</span></span>

```bash
$ git --version
git version 2.17.1.windows.2

```

> [!NOTE]
> <span data-ttu-id="8ea1a-121">Verwenden Sie ein geeignetes Terminalfenster auf Ihrer Plattform.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-121">Use a suitable terminal window on your platform.</span></span> <span data-ttu-id="8ea1a-122">Diese Beispiele verwenden Git Bash, können aber auf den meisten Plattformen ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-122">These examples use Git Bash but can be run on most platforms.</span></span>

<span data-ttu-id="8ea1a-123">Öffnen Sie die neueste Version von Visual Studio und installieren Sie alle Updates.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-123">Open the latest version of Visual Studio and install any updates.</span></span>

<span data-ttu-id="8ea1a-124">Sie können dasselbe Terminalfenster verwenden, um die Befehle in diesem Tutorial auszuführen.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-124">You can use the same terminal window to run the commands in this tutorial.</span></span>

<a name="DownloadSample"></a>

## <a name="download-the-sample"></a><span data-ttu-id="8ea1a-125">Laden Sie das Beispiel herunter</span><span class="sxs-lookup"><span data-stu-id="8ea1a-125">Download the sample</span></span>

<span data-ttu-id="8ea1a-126">Sie können mit einem einfachen [Hallo, Welt beginnen!](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-hello-world/csharp)</span><span class="sxs-lookup"><span data-stu-id="8ea1a-126">You can get started with a simple [Hello, World!](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-hello-world/csharp)</span></span> <span data-ttu-id="8ea1a-127">Beispiel in C..</span><span class="sxs-lookup"><span data-stu-id="8ea1a-127">sample in C#.</span></span> <span data-ttu-id="8ea1a-128">Führen Sie in einem Terminalfenster den folgenden Befehl aus, um das Beispiel-Repository auf Ihren Computer zu klonen:</span><span class="sxs-lookup"><span data-stu-id="8ea1a-128">In a terminal window, run the following command to clone the sample repository to your computer:</span></span>

```bash
git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
```

> [!TIP]
> <span data-ttu-id="8ea1a-129">Sie können dieses [Repository](https://github.com/OfficeDev/Microsoft-Teams-Samples) [verkleben,](https://help.github.com/articles/fork-a-repo/) um Ihre Änderungen zu ändern und in GitHub zu speichern.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-129">You can [fork](https://help.github.com/articles/fork-a-repo/) this [repo](https://github.com/OfficeDev/Microsoft-Teams-Samples) to modify and save your changes to GitHub.</span></span>

<a name="BuildRun"></a>

## <a name="build-and-run-the-sample"></a><span data-ttu-id="8ea1a-130">Erstellen und Ausführen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="8ea1a-130">Build and run the sample</span></span>

<span data-ttu-id="8ea1a-131">Nachdem das Repository geklont wurde, verwenden Sie Visual Studio, um die Lösungsdatei **Microsoft.Teams zu öffnen. Samples.HelloWorld.sln** aus dem **Microsoft-Teams-Samples/samples/app-hello-world/csharp-Verzeichnis** des Beispiels.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-131">After the repo is cloned, use Visual Studio to open the solution file **Microsoft.Teams.Samples.HelloWorld.sln** from the **Microsoft-Teams-Samples/samples/app-hello-world/csharp** directory of the sample.</span></span> <span data-ttu-id="8ea1a-132">Wählen Sie dann im Menü **Erstellen** die Option **Lösung erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-132">Then, select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="8ea1a-133">Um das Beispiel auszuführen, drücken Sie **F5** oder wählen Sie **Debuggen** starten im **Debugmenü** aus.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-133">To run the sample, press **F5** or select **Start Debugging** from the **Debug** menu.</span></span>

<span data-ttu-id="8ea1a-134">Wenn die App gestartet wird, wird ein Browserfenster geöffnet, in dem der Stamm der App gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-134">When the app starts, a browser window opens with the root of the app launched.</span></span> <span data-ttu-id="8ea1a-135">Sie können zu den folgenden URLs wechseln, um zu überprüfen, ob alle App-URLs geladen werden:</span><span class="sxs-lookup"><span data-stu-id="8ea1a-135">You can go to the following URLs to verify that all the app URLs are loading:</span></span>

- `https://localhost:44327/`
- `https://localhost:44327/hello`
- `https://localhost:44327/first`
- `https://localhost:44327/second`

<a name="HostSample"></a>

> [!Note]
> <span data-ttu-id="8ea1a-136">Wenn sie eine Fehlermeldung `Could not find a part of the path … bin\roslyn\csc.exe` erhalten, aktualisieren Sie das Paket mit dem Befehl `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r` .</span><span class="sxs-lookup"><span data-stu-id="8ea1a-136">If you receive an error `Could not find a part of the path … bin\roslyn\csc.exe`, update the package with the command `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r`.</span></span> <span data-ttu-id="8ea1a-137">Weitere Informationen finden Sie unter [diese Frage unter Stack Overflow](https://stackoverflow.com/questions/32780315).</span><span class="sxs-lookup"><span data-stu-id="8ea1a-137">For more information, see [this question on Stack Overflow](https://stackoverflow.com/questions/32780315).</span></span>

## <a name="host-the-sample-app"></a><span data-ttu-id="8ea1a-138">Hosten der Beispiel-App</span><span class="sxs-lookup"><span data-stu-id="8ea1a-138">Host the sample app</span></span>

<span data-ttu-id="8ea1a-139">Apps in Microsoft Teams sind Webanwendungen, die eine oder mehrere Funktionen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-139">Apps in Microsoft Teams are web applications that provide one or more capabilities.</span></span> <span data-ttu-id="8ea1a-140">Damit die Teams Plattform Ihre App laden kann, muss Ihre App im Internet verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-140">For the Teams platform to load your app, your app must be available on the internet.</span></span> <span data-ttu-id="8ea1a-141">Dazu müssen Sie Ihre App hosten.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-141">To do this, you need to host your app.</span></span> <span data-ttu-id="8ea1a-142">Sie können es entweder kostenlos in Microsoft Azure hosten oder einen Tunnel zum lokalen Prozess auf Ihrem Computer erstellen, indem Sie `ngrok` verwenden.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-142">You can either host it in Microsoft Azure for free or create a tunnel to the local process on your computer using `ngrok`.</span></span> <span data-ttu-id="8ea1a-143">Nachdem Sie Ihre App hosten, notieren Sie sich deren Stamm-URL, z. `https://yourteamsapp.ngrok.io` B. oder `https://yourteamsapp.azurewebsites.net` .</span><span class="sxs-lookup"><span data-stu-id="8ea1a-143">After you host your app, note its root URL, such as `https://yourteamsapp.ngrok.io` or `https://yourteamsapp.azurewebsites.net`.</span></span>

### <a name="tunnel-using-ngrok"></a><span data-ttu-id="8ea1a-144">Tunnel mit ngrok</span><span class="sxs-lookup"><span data-stu-id="8ea1a-144">Tunnel using ngrok</span></span>

<span data-ttu-id="8ea1a-145">Zum schnellen Testen können Sie die App auf Ihrem Computer ausführen und einen Tunnel zu diesem Überstand über einen Webendpunkt erstellen.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-145">For quick testing, you can run the app on your computer and create a tunnel to it through a web endpoint.</span></span> <span data-ttu-id="8ea1a-146">[`ngrok`](https://ngrok.com) ist ein kostenloses Tool, mit dem Sie eine Webadresse erhalten können, z. `https://d0ac14a5.ngrok.io` B. .</span><span class="sxs-lookup"><span data-stu-id="8ea1a-146">[`ngrok`](https://ngrok.com) is a free tool with which you can get a web address, such as `https://d0ac14a5.ngrok.io`.</span></span> <span data-ttu-id="8ea1a-147">Sie können ngrok [herunterladen und installieren](https://ngrok.com/download) und es an einem Speicherort in Ihrem `PATH` hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-147">You can [download and install](https://ngrok.com/download) ngrok and add it to a location in your `PATH`.</span></span>

<span data-ttu-id="8ea1a-148">Öffnen Sie nach der Installation `ngrok` ein neues Terminalfenster, und führen Sie den folgenden Befehl aus, um einen Tunnel zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="8ea1a-148">After you install `ngrok`, open a new terminal window and run the following command to create a tunnel:</span></span>

```bash
ngrok http 44327 -host-header=localhost:44327
```

<span data-ttu-id="8ea1a-149">`Ngrok` überwacht Anfragen aus dem Internet und leitet sie an Ihre App weiter, die unter Port 44327 ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-149">`Ngrok` listens to requests from the internet and routes them to your app running on port 44327.</span></span> <span data-ttu-id="8ea1a-150">Um dies zu überprüfen, öffnen Sie Ihren Browser, und gehen Sie `https://d0ac14a5.ngrok.io/hello` zu , um die Hallo-Seite Ihrer App zu laden.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-150">To verify, open your browser and go to `https://d0ac14a5.ngrok.io/hello` to load your app's hello page.</span></span> <span data-ttu-id="8ea1a-151">Verwenden Sie anstelle dieser URL die Weiterleitungsadresse, die in der Konsolensitzung angezeigt `ngrok` wird.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-151">Instead of this URL, use the forwarding address displayed by `ngrok` in your console session.</span></span>

> [!NOTE]
> <span data-ttu-id="8ea1a-152">Wenn Sie im [Build- und Ausführungsschritt](#build-and-run-the-sample) einen anderen Port verwendet haben, stellen Sie sicher, dass Sie dieselbe Portnummer verwenden, um den `ngrok` Tunnel einzurichten.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-152">If you have used a different port in the [build and run](#build-and-run-the-sample) step, ensure you use the same port number to setup the `ngrok` tunnel.</span></span>

> [!TIP]
> <span data-ttu-id="8ea1a-153">Es ist eine gute Idee, in einem anderen Terminalfenster zu `ngrok` laufen.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-153">It is a good idea to run `ngrok` in a different terminal window.</span></span> <span data-ttu-id="8ea1a-154">Dies geschieht, um zu verhindern, `ngrok` dass die App ausgeführt wird, ohne die App zu stören.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-154">This is done to keep `ngrok` from running without interfering with the app.</span></span> <span data-ttu-id="8ea1a-155">Sie müssen die App anhalten, neu erstellen und erneut ausführen.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-155">You have to stop, rebuild, and rerun the app.</span></span> <span data-ttu-id="8ea1a-156">Die `ngrok` Sitzung enthält nützliche Debuginformationen in diesem Fenster.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-156">The `ngrok` session provides useful debugging information in this window.</span></span>

<span data-ttu-id="8ea1a-157">Die App ist nur während der aktuellen Sitzung auf Ihrem Computer verfügbar.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-157">The app is only available during the current session on your computer.</span></span> <span data-ttu-id="8ea1a-158">Wenn die Maschine heruntergefahren wird oder in den Ruhezustand geht, ist der Dienst nicht mehr verfügbar.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-158">If the machine is shut down or goes to sleep, the service is no longer available.</span></span> <span data-ttu-id="8ea1a-159">Denken Sie daran, wenn Sie die App zum Testen für andere Benutzer freigeben.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-159">Remember this when you share the app for testing to other users.</span></span> <span data-ttu-id="8ea1a-160">Wenn Sie den Dienst neu starten müssen, gibt die App eine neue Adresse zurück, und Sie müssen jeden Speicherort aktualisieren, der diese Adresse verwendet.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-160">If you have to restart the service, the app returns a new address and you must update every location that uses that address.</span></span> <span data-ttu-id="8ea1a-161">Die kostenpflichtige Version von `ngrok` hat diese Einschränkung nicht.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-161">The paid version of `ngrok` does not have this limitation.</span></span>

### <a name="host-in-azure"></a><span data-ttu-id="8ea1a-162">Host in Azure</span><span class="sxs-lookup"><span data-stu-id="8ea1a-162">Host in Azure</span></span>

<span data-ttu-id="8ea1a-163">Microsoft Azure Hosthosten Ihrer .NET-Anwendung auf einem freien Kontingent mithilfe einer freigegebenen Infrastruktur.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-163">Microsoft Azure hosts your .NET application on a free tier using shared infrastructure.</span></span> <span data-ttu-id="8ea1a-164">Dies reicht aus, um das `Hello World` Beispiel auszuführen.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-164">This is sufficient to run the `Hello World` sample.</span></span> <span data-ttu-id="8ea1a-165">Weitere Informationen finden Sie unter [Erstellen eines neuen kostenlosen Azure-Kontos](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="8ea1a-165">For more information, see [creating a new free Azure account](https://azure.microsoft.com/free/).</span></span>

<span data-ttu-id="8ea1a-166">Visual Studio bietet integrierte Unterstützung für die App-Bereitstellung für verschiedene Anbieter, einschließlich Azure:</span><span class="sxs-lookup"><span data-stu-id="8ea1a-166">Visual Studio has built-in support for app deployment to different providers, including Azure:</span></span>

<img width="530px" alt="Visual Studio" src="~/assets/images/get-started/publishtoazure1.png"/>

[!include [Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

## <a name="update-the-credentials-for-your-hosted-app"></a><span data-ttu-id="8ea1a-167">Aktualisieren der Anmeldeinformationen für Ihre gehostete App</span><span class="sxs-lookup"><span data-stu-id="8ea1a-167">Update the credentials for your hosted app</span></span>

<span data-ttu-id="8ea1a-168">Die Beispiel-App erfordert, dass die Umgebungsvariablen auf die Werte festgelegt werden, die Sie in der Textdatei gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-168">The sample app requires the environment variables to be set to the values that you saved in the text file.</span></span>

<span data-ttu-id="8ea1a-169">die Datei `appsettings.json` öffnen.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-169">Open the `appsettings.json` file.</span></span> <span data-ttu-id="8ea1a-170">Aktualisieren Sie den **MicrosoftAppId-Wert** mit Ihrer Bot-ID, die Sie in der Textdatei gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-170">Update the **MicrosoftAppId** value with your bot ID that you saved in the text file.</span></span> <span data-ttu-id="8ea1a-171">Aktualisieren Sie das **MicrosoftAppPassword** mit dem von Ihnen gespeicherten Bot-Passwort.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-171">Update the **MicrosoftAppPassword** with the bot password you saved.</span></span>

<img width="560px" alt="Setting the keys" src="~/assets/images/get-started/get-started-net-azure-add-keys.png"/>

<span data-ttu-id="8ea1a-172">Nachdem diese Änderungen vorgenommen wurden, erstellen Sie die App neu.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-172">After these changes are made, rebuild the app.</span></span> <span data-ttu-id="8ea1a-173">Wenn Sie ngrok verwenden, führen Sie die App lokal aus, und stellen Sie die App erneut bereit, und wenn Sie in Azure hosten, stellen Sie die App erneut bereit.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-173">If you are using ngrok, run the app locally, and if you are hosting in Azure, redeploy the app.</span></span>

## <a name="configure-the-app-tab"></a><span data-ttu-id="8ea1a-174">Konfigurieren der App-Registerkarte</span><span class="sxs-lookup"><span data-stu-id="8ea1a-174">Configure the app tab</span></span>

<span data-ttu-id="8ea1a-175">Nachdem Sie die App in einem Team installiert haben, müssen Sie sie so konfigurieren, dass Inhalte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-175">Once you install the app into a team, you must configure it to show content.</span></span> <span data-ttu-id="8ea1a-176">Wechseln Sie zu einem Kanal im Team, in dem Sie die Beispiel-App installiert haben, und wählen Sie die Schaltfläche **"+",** um eine neue Registerkarte hinzuzufügen. Wählen Sie **Hello World** aus der **RegisterkarteNliste Hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-176">Go to a channel in the team where you installed the sample app and select the **'+'** button to add a new tab. Choose **Hello World** from the **Add a tab** list.</span></span> <span data-ttu-id="8ea1a-177">Es wird ein Konfigurationsdialogfeld angezeigt, in dem Sie die Registerkarte auswählen können, die in diesem Kanal angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-177">A configuration dialog box is displayed that enables you to choose the tab to display in this channel.</span></span> <span data-ttu-id="8ea1a-178">Nachdem Sie die Registerkarte ausgewählt und die Option **Speichern** auswählen, wird die `Hello World` Registerkarte mit der Registerkarte geladen.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-178">After you select the tab and select **Save** the `Hello World` tab is loaded with the tab.</span></span>

<img width="530px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png" />

### <a name="test-your-bot-in-teams"></a><span data-ttu-id="8ea1a-179">Testen Sie Ihren Bot in Teams</span><span class="sxs-lookup"><span data-stu-id="8ea1a-179">Test your bot in Teams</span></span>

<span data-ttu-id="8ea1a-180">Jetzt können Sie den Bot in Teams testen.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-180">Now you can test the bot in Teams.</span></span> <span data-ttu-id="8ea1a-181">Wählen Sie einen Kanal im Team aus, in dem Sie Ihre App registriert haben, und geben Sie `@your-bot-name` ein.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-181">Select a channel in the team where you registered your app and type `@your-bot-name`.</span></span> <span data-ttu-id="8ea1a-182">Dies wird als **\@ Erwähnung** bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-182">This is called an **\@mention**.</span></span> <span data-ttu-id="8ea1a-183">Der Bot antwortet auf jede Nachricht, die Sie senden.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-183">The bot replies to any message that you send.</span></span>

<img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png" />

### <a name="test-your-messaging-extension"></a><span data-ttu-id="8ea1a-184">Testen Sie Ihre Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="8ea1a-184">Test your messaging extension</span></span>

<span data-ttu-id="8ea1a-185">Um Ihre Messaging-Erweiterung zu testen, können Sie **...** unter dem Eingabefeld in Ihrer Unterhaltungsansicht auswählen.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-185">To test your messaging extension, you can select **...** below the input box in your conversation view.</span></span> <span data-ttu-id="8ea1a-186">Ein Menü mit der **App "Hello World"** wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-186">A menu with the **'Hello World'** app is displayed.</span></span> <span data-ttu-id="8ea1a-187">Wenn Sie es auswählen, wird eine Reihe zufälliger Texte angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-187">When you select it, a set of random texts is displayed.</span></span> <span data-ttu-id="8ea1a-188">Sie können einen der zufälligen Texte auswählen, der in Ihre Unterhaltung eingefügt wird.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-188">You can select one of the random text and that is inserted into your conversation.</span></span>

<img width="530px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu.png" />

<img width="530px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result.png" />

<span data-ttu-id="8ea1a-189">Wählen Sie einen der zufälligen Texte aus.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-189">Select one of the random text.</span></span> <span data-ttu-id="8ea1a-190">Eine Karte, die mit Ihrer eigenen Nachricht formatiert und zum Senden bereit ist, wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8ea1a-190">A card formatted and ready to send with your own message is shown.</span></span>

<img width="530px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />
