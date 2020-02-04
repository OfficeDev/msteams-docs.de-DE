---
title: Erste Schritte mit C#/.net
description: Erste Schritte beim Erstellen von tollen apps in Microsoft Teams mit C#-/.net
keywords: Erste Schritte mit .net c# CSharp
ms.date: 11/09/2018
ms.openlocfilehash: de133894042baaba897a9f046d613cd5dbb94eee
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674273"
---
# <a name="get-started-on-the-microsoft-teams-platform-with-cnet-and-app-studio"></a><span data-ttu-id="e1f70-104">Erste Schritte mit der Microsoft Teams-Plattform mit C#/.net und App Studio</span><span class="sxs-lookup"><span data-stu-id="e1f70-104">Get started on the Microsoft Teams platform with C#/.NET and App Studio</span></span>

<span data-ttu-id="e1f70-105">Die [Microsoft Teams](/microsoftteams/) -Entwicklerplattform erleichtert Ihnen das Erweitern von Teams und die nahtlose Integration ihrer eigenen Anwendungen und Dienste in den Arbeitsbereich "Teams".</span><span class="sxs-lookup"><span data-stu-id="e1f70-105">The [Microsoft Teams](/microsoftteams/) developer platform makes it easy for you to extend Teams and integrate your own applications and services seamlessly into the Teams workspace.</span></span> <span data-ttu-id="e1f70-106">Diese Apps können dann an Ihr Unternehmen oder für Teams auf der ganzen Welt verteilt werden.</span><span class="sxs-lookup"><span data-stu-id="e1f70-106">These apps can then be distributed to your enterprise or for teams around the world.</span></span>

<span data-ttu-id="e1f70-107">Um Microsoft Teams zu erweitern, müssen Sie eine Microsoft Teams-app erstellen.</span><span class="sxs-lookup"><span data-stu-id="e1f70-107">To extend Microsoft Teams, you will need to create a Microsoft Teams app.</span></span> <span data-ttu-id="e1f70-108">Eine Microsoft Teams-APP ist eine Webanwendung, die Sie hosten.</span><span class="sxs-lookup"><span data-stu-id="e1f70-108">A Microsoft Teams app is a web application that you host.</span></span> <span data-ttu-id="e1f70-109">Diese APP kann dann in Microsoft Teams in den Arbeitsbereich des Benutzers integriert werden.</span><span class="sxs-lookup"><span data-stu-id="e1f70-109">This app can then be integrated into the user's workspace in Teams.</span></span>

<span data-ttu-id="e1f70-110">In diesem Lernprogramm erfahren Sie, wie Sie mit dem Erstellen einer Microsoft Teams-App mithilfe von C# in .net beginnen können.</span><span class="sxs-lookup"><span data-stu-id="e1f70-110">This tutorial helps you get started creating a Microsoft Teams app using C# on .NET.</span></span> <span data-ttu-id="e1f70-111">Sie können die APP testen, indem Sie Sie in ein Team laden, für das Sie Berechtigungen haben, oder in einen Testmandanten, der mit dem Office-Entwicklerprogramm erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="e1f70-111">You can test the app by loading it into a Team that you have permissions for, or into a test tenant created using the Office Developer Program.</span></span>

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="GetPrerequisites"></a>

## <a name="get-prerequisites"></a><span data-ttu-id="e1f70-112">Abrufen von Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="e1f70-112">Get prerequisites</span></span>

<span data-ttu-id="e1f70-113">Um dieses Lernprogramm abzuschließen, müssen Sie die folgenden Tools abrufen:</span><span class="sxs-lookup"><span data-stu-id="e1f70-113">To complete this tutorial, you need to get the following tools:</span></span>

- [<span data-ttu-id="e1f70-114">Installieren von git</span><span class="sxs-lookup"><span data-stu-id="e1f70-114">Install Git</span></span>](https://git-scm.com/downloads)
- <span data-ttu-id="e1f70-115">[Installieren Sie Visual Studio 2017](https://www.visualstudio.com/downloads/).</span><span class="sxs-lookup"><span data-stu-id="e1f70-115">[Install Visual Studio 2017](https://www.visualstudio.com/downloads/).</span></span> <span data-ttu-id="e1f70-116">Sie können die ﻿kostenlose Community Edition installieren.</span><span class="sxs-lookup"><span data-stu-id="e1f70-116">You can install the free community edition.</span></span>

<span data-ttu-id="e1f70-117">Wenn Sie während der Installation eine Option `git` zum Hinzufügen des Pfads sehen, wählen Sie aus.</span><span class="sxs-lookup"><span data-stu-id="e1f70-117">If you see an option to add `git` to the PATH during installation, choose to do so.</span></span> <span data-ttu-id="e1f70-118">Das ist praktisch.</span><span class="sxs-lookup"><span data-stu-id="e1f70-118">It will be handy.</span></span>

<span data-ttu-id="e1f70-119">Überprüfen `git` Sie Ihre Installation, indem Sie Folgendes in einem Terminalfenster ausführen:</span><span class="sxs-lookup"><span data-stu-id="e1f70-119">Verify your `git` installation by running the following in a terminal window:</span></span>
> [!NOTE]
> <span data-ttu-id="e1f70-120">Verwenden Sie das Terminal-Fenster, mit dem Sie sich am besten auf Ihrer Plattform vertraut machen.</span><span class="sxs-lookup"><span data-stu-id="e1f70-120">Use the terminal window that you are most comfortable with on your platform.</span></span> <span data-ttu-id="e1f70-121">In diesen Beispielen wird bash verwendet, wird jedoch auf den meisten Plattformen ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="e1f70-121">These examples use Bash, but will run on most platforms.</span></span>

```bash
$ git --version
git version 2.17.1.windows.2

```

<span data-ttu-id="e1f70-122">Stellen Sie sicher, dass Sie Visual Studio 2017 starten und alle Updates installieren, falls dies angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="e1f70-122">Make sure to launch Visual Studio 2017 and install any updates if shown.</span></span>

<span data-ttu-id="e1f70-123">Sie können weiterhin dieses Terminalfenster verwenden, um die Befehle auszuführen, die in diesem Lernprogramm folgen.</span><span class="sxs-lookup"><span data-stu-id="e1f70-123">You can continue to use this terminal window to run the commands that follow in this tutorial.</span></span>

<a name="DownloadSample"></a>

## <a name="download-the-sample"></a><span data-ttu-id="e1f70-124">Herunterladen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="e1f70-124">Download the sample</span></span>

<span data-ttu-id="e1f70-125">Wir haben ein einfaches [Hello, World](https://github.com/OfficeDev/msteams-samples-hello-world-csharp) bereitgestellt!</span><span class="sxs-lookup"><span data-stu-id="e1f70-125">We have provided a simple [Hello, World!](https://github.com/OfficeDev/msteams-samples-hello-world-csharp)</span></span> <span data-ttu-id="e1f70-126">Beispiel in C#, um den Einstieg zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="e1f70-126">sample in C# to get you started.</span></span> <span data-ttu-id="e1f70-127">Führen Sie in einem Terminalfenster den folgenden Befehl aus, um das Beispiel-Repository auf Ihren lokalen Computer zu klonen:</span><span class="sxs-lookup"><span data-stu-id="e1f70-127">In a terminal window, run the following command to clone the sample repository to your local machine:</span></span>

```bash
git clone https://github.com/OfficeDev/msteams-samples-hello-world-csharp.git
```

> [!TIP]
> <span data-ttu-id="e1f70-128">Sie können dieses [Repo](https://github.com/OfficeDev/msteams-samples-hello-world-csharp) [abzweigen](https://help.github.com/articles/fork-a-repo/) , wenn Sie die Änderungen an GitHub zur späteren Referenz ändern und einchecken möchten.</span><span class="sxs-lookup"><span data-stu-id="e1f70-128">You can [fork](https://help.github.com/articles/fork-a-repo/) this [repo](https://github.com/OfficeDev/msteams-samples-hello-world-csharp) if you want to modify and check in your changes to GitHub for future reference.</span></span>

<a name="BuildRun"></a>

## <a name="build-and-run-the-sample"></a><span data-ttu-id="e1f70-129">Erstellen und Ausführen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="e1f70-129">Build and run the sample</span></span>

<span data-ttu-id="e1f70-130">Nachdem das Repository geklont wurde, verwenden Sie Visual Studio, um die Lösungsdatei `Microsoft.Teams.Samples.HelloWorld.sln` aus dem Stammverzeichnis des Beispiels zu öffnen und `Build Solution` im `Build` Menü zu klicken.</span><span class="sxs-lookup"><span data-stu-id="e1f70-130">Once the repo is cloned, use Visual Studio to open the solution file `Microsoft.Teams.Samples.HelloWorld.sln` from the root directory of the sample and click `Build Solution` from the `Build` menu.</span></span> <span data-ttu-id="e1f70-131">Sie können das Beispiel durch Drücken `F5` oder auswählen `Start Debugging` im `Debug` Menü ausführen.</span><span class="sxs-lookup"><span data-stu-id="e1f70-131">You can run the sample by pressing `F5` or choosing `Start Debugging` from the `Debug` menu.</span></span>

<span data-ttu-id="e1f70-132">Wenn die APP gestartet wird, wird ein Browserfenster geöffnet, in dem der Stamm der APP gestartet ist.</span><span class="sxs-lookup"><span data-stu-id="e1f70-132">When the app starts, you will see a browser window open with the root of the app launched.</span></span> <span data-ttu-id="e1f70-133">Sie können zu den folgenden URLs navigieren, um sicherzustellen, dass alle App-URLs geladen werden:</span><span class="sxs-lookup"><span data-stu-id="e1f70-133">You can navigate to the following URLs to verify that all the app URLs are loading:</span></span>

- [http://localhost:3333](http://localhost:3333)
- [http://localhost:3333/hello](http://localhost:3333/hello)
- [http://localhost:3333/first](http://localhost:3333/first)
- [http://localhost:3333/second](http://localhost:3333/second)

<a name="HostSample"></a>

> [!Note]
> <span data-ttu-id="e1f70-134">Wenn Sie eine Fehlermeldung wie `Could not find a part of the path … bin\roslyn\csc.exe`erhalten, versuchen Sie, das Paket mit `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r`dem Befehl zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="e1f70-134">If you receive an error like `Could not find a part of the path … bin\roslyn\csc.exe`, try updating the package with the command `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r`.</span></span> <span data-ttu-id="e1f70-135">Weitere Informationen finden Sie [in dieser Frage auf StackOverflow](https://stackoverflow.com/questions/32780315) .</span><span class="sxs-lookup"><span data-stu-id="e1f70-135">See [this question on StackOverflow](https://stackoverflow.com/questions/32780315) for additional details.</span></span>

## <a name="host-the-sample-app"></a><span data-ttu-id="e1f70-136">Hosten der Beispiel-App</span><span class="sxs-lookup"><span data-stu-id="e1f70-136">Host the sample app</span></span>

<span data-ttu-id="e1f70-137">Beachten Sie, dass apps in Microsoft Teams Webanwendungen sind, die eine oder mehrere Funktionen verfügbar machen.</span><span class="sxs-lookup"><span data-stu-id="e1f70-137">Remember that apps in Microsoft Teams are web applications exposing one or more capabilities.</span></span> <span data-ttu-id="e1f70-138">Damit die Microsoft Teams-Plattform Ihre APP lädt, muss Ihre APP über das Internet erreichbar sein.</span><span class="sxs-lookup"><span data-stu-id="e1f70-138">For the Teams platform to load your app, your app must be reachable from the internet.</span></span> <span data-ttu-id="e1f70-139">Damit Ihre APP über das Internet erreichbar ist, müssen Sie Ihre APP hosten.</span><span class="sxs-lookup"><span data-stu-id="e1f70-139">To make your app reachable from the internet, you need to host your app.</span></span> <span data-ttu-id="e1f70-140">Sie können es entweder in Microsoft Azure kostenlos hosten oder einen Tunnel für den lokalen Prozess auf dem Entwicklungscomputer mit `ngrok`erstellen.</span><span class="sxs-lookup"><span data-stu-id="e1f70-140">You can either host it in Microsoft Azure for free or create a tunnel to the local process on your development machine using `ngrok`.</span></span> <span data-ttu-id="e1f70-141">Wenn Sie das Hosten Ihrer APP abgeschlossen haben, notieren Sie sich die Stamm-URL.</span><span class="sxs-lookup"><span data-stu-id="e1f70-141">When you finish hosting your app make a note of its root URL.</span></span> <span data-ttu-id="e1f70-142">Es sieht etwa wie folgt aus `https://yourteamsapp.ngrok.io` : `https://yourteamsapp.azurewebsites.net`oder.</span><span class="sxs-lookup"><span data-stu-id="e1f70-142">It will look something like: `https://yourteamsapp.ngrok.io` or `https://yourteamsapp.azurewebsites.net`.</span></span>

### <a name="tunnel-using-ngrok"></a><span data-ttu-id="e1f70-143">Tunnel mit ngrok</span><span class="sxs-lookup"><span data-stu-id="e1f70-143">Tunnel using ngrok</span></span>

<span data-ttu-id="e1f70-144">Für schnelle Tests können Sie die APP auf Ihrem lokalen Computer ausführen und einen Tunnel über einen Webendpunkt erstellen.</span><span class="sxs-lookup"><span data-stu-id="e1f70-144">For quick testing you can run the app on your local machine and create a tunnel to it through a web endpoint.</span></span> <span data-ttu-id="e1f70-145">[ngrok](https://ngrok.com) ist ein kostenloses Tool, mit dem Sie genau dies tun können.</span><span class="sxs-lookup"><span data-stu-id="e1f70-145">[ngrok](https://ngrok.com) is a free tool that lets you do just that.</span></span> <span data-ttu-id="e1f70-146">Mit ngrok können Sie eine Webadresse wie `https://d0ac14a5.ngrok.io` (diese URL ist nur ein Beispiel) erhalten.</span><span class="sxs-lookup"><span data-stu-id="e1f70-146">With ngrok you can get a web address such as `https://d0ac14a5.ngrok.io` (this URL is just an example).</span></span> <span data-ttu-id="e1f70-147">Sie können ngrok für Ihre Umgebung [herunterladen und installieren](https://ngrok.com/download) .</span><span class="sxs-lookup"><span data-stu-id="e1f70-147">You can [download and install](https://ngrok.com/download) ngrok for your environment.</span></span> <span data-ttu-id="e1f70-148">Stellen Sie sicher, dass Sie Sie an einen Speicherort `PATH`in Ihrem hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="e1f70-148">Make sure you add it to a location in your `PATH`.</span></span>

<span data-ttu-id="e1f70-149">Nachdem Sie es installiert haben, können Sie ein neues Terminalfenster öffnen und den folgenden Befehl ausführen, um einen Tunnel zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="e1f70-149">Once you install it, you can open a new terminal window and run the following command to create a tunnel.</span></span> <span data-ttu-id="e1f70-150">Im Beispiel wird Port 3333 verwendet, stellen Sie daher sicher, dass Sie es hier angeben.</span><span class="sxs-lookup"><span data-stu-id="e1f70-150">The sample uses port 3333, so be sure to specify it here.</span></span>

```bash
ngrok http 3333 -host-header=localhost:3333
```

<span data-ttu-id="e1f70-151">Ngrok wird Anfragen aus dem Internet abhören und diese an Ihre APP weiterleiten, die auf Port 3333 läuft.</span><span class="sxs-lookup"><span data-stu-id="e1f70-151">Ngrok will listen to requests from the internet and will route them to your app running on port 3333.</span></span> <span data-ttu-id="e1f70-152">Sie können überprüfen, ob Sie Ihren Browser öffnen `https://d0ac14a5.ngrok.io/hello` und die Hello-Seite Ihrer App laden.</span><span class="sxs-lookup"><span data-stu-id="e1f70-152">You can verify by opening your browser and going to `https://d0ac14a5.ngrok.io/hello` to load your app's hello page.</span></span> <span data-ttu-id="e1f70-153">Achten Sie darauf, dass Sie die von ngrok in ihrer Konsolensitzung angezeigte Weiterleitungsadresse anstelle dieser URL verwenden.</span><span class="sxs-lookup"><span data-stu-id="e1f70-153">Please be sure to use the forwarding address displayed by ngrok in your console session instead of this URL.</span></span>

> [!NOTE]
> <span data-ttu-id="e1f70-154">Wenn Sie einen anderen Port im Schritt " [Build" und "ausführen](#build-and-run-the-sample) " verwendet haben, stellen Sie sicher, dass Sie die gleiche Port `ngrok` Nummer zum Einrichten des Tunnels verwenden.</span><span class="sxs-lookup"><span data-stu-id="e1f70-154">If you have used a different port in the [build and run](#build-and-run-the-sample) step above, make sure you use the same port number to setup the `ngrok` tunnel.</span></span>
> [!TIP]
> <span data-ttu-id="e1f70-155">Es empfiehlt sich, `ngrok` in einem anderen Terminalfenster ausgeführt zu werden, damit es ausgeführt wird, ohne dass die APP beeinträchtigt wird, die Sie später möglicherweise beenden, neu erstellen und erneut ausführen müssen.</span><span class="sxs-lookup"><span data-stu-id="e1f70-155">It is a good idea to run `ngrok` in a different terminal window to keep it running without interfering with the app which you might later have to stop, rebuild and rerun.</span></span> <span data-ttu-id="e1f70-156">Die `ngrok` Sitzung gibt nützliche Debuginformationen in diesem Fenster zurück.</span><span class="sxs-lookup"><span data-stu-id="e1f70-156">The `ngrok` session will return useful debugging information in this window.</span></span>

<span data-ttu-id="e1f70-157">Die APP ist nur während der aktuellen Sitzung auf dem Entwicklungscomputer verfügbar.</span><span class="sxs-lookup"><span data-stu-id="e1f70-157">The app will only be available during the current session on your development machine.</span></span> <span data-ttu-id="e1f70-158">Wenn der Computer heruntergefahren wird oder in den Standbymodus wechselt, steht der Dienst nicht mehr zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="e1f70-158">If the machine is shut down or goes to sleep the service will no longer be available.</span></span> <span data-ttu-id="e1f70-159">Denken Sie daran, wenn Sie die APP für Tests von anderen Benutzern freigeben.</span><span class="sxs-lookup"><span data-stu-id="e1f70-159">Remember this when sharing the app for testing by other users.</span></span> <span data-ttu-id="e1f70-160">Wenn Sie den Dienst neu starten müssen, wird eine neue Adresse zurückgegeben, und Sie müssen jeden Ort aktualisieren, an dem diese Adresse verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="e1f70-160">If you have to restart the service it will return a new address and you will have to update every place that uses that address.</span></span> <span data-ttu-id="e1f70-161">Die kostenpflichtige Version von Ngrok hat diese Einschränkung nicht.</span><span class="sxs-lookup"><span data-stu-id="e1f70-161">The paid version of Ngrok does not have this limitation.</span></span>

### <a name="host-in-azure"></a><span data-ttu-id="e1f70-162">Host in Azure</span><span class="sxs-lookup"><span data-stu-id="e1f70-162">Host in Azure</span></span>

<span data-ttu-id="e1f70-163">Microsoft Azure können Sie Ihre .NET-Anwendung auf einer freien Ebene mit der freigegebenen Infrastruktur hosten.</span><span class="sxs-lookup"><span data-stu-id="e1f70-163">Microsoft Azure lets you host your .NET application on a free tier using shared infrastructure.</span></span> <span data-ttu-id="e1f70-164">Dies reicht aus, um dieses `Hello World` Beispiel ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="e1f70-164">This will be sufficient to run this `Hello World` sample.</span></span> <span data-ttu-id="e1f70-165">Weitere Informationen finden Sie unter [Erstellen eines neuen kostenlosen Kontos](https://azure.microsoft.com/free/) .</span><span class="sxs-lookup"><span data-stu-id="e1f70-165">See [creating a new free account](https://azure.microsoft.com/free/) for more information.</span></span>

<span data-ttu-id="e1f70-166">Visual Studio bietet integrierte Unterstützung für die APP-Bereitstellung für unterschiedliche Anbieter, einschließlich Azure.</span><span class="sxs-lookup"><span data-stu-id="e1f70-166">Visual Studio has built-in support for app deployment to different providers, including Azure.</span></span>

<img width="530px" src="~/assets/images/get-started/publishtoazure1.png" title="Visual Studio"/>

[!include[Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

## <a name="update-the-credentials-for-your-hosted-app"></a><span data-ttu-id="e1f70-168">Aktualisieren der Anmeldeinformationen für die gehostete App</span><span class="sxs-lookup"><span data-stu-id="e1f70-168">Update the credentials for your hosted app</span></span>

<span data-ttu-id="e1f70-169">Für die Beispiel-App müssen die folgenden Umgebungsvariablen auf die Werte festgelegt werden, auf die Sie zuvor hingewiesen haben.</span><span class="sxs-lookup"><span data-stu-id="e1f70-169">The sample app requires the following environment variables to be set to the values you made a note of earlier.</span></span>

<span data-ttu-id="e1f70-170">Öffnen Sie die Datei "Internet. config", und suchen Sie nach dem Abschnitt *appSettings* .</span><span class="sxs-lookup"><span data-stu-id="e1f70-170">Open up the web.config file and find the *appSettings* section.</span></span> <span data-ttu-id="e1f70-171">Aktualisieren Sie den *MicrosoftAppId* -Wert mit ihrer bot-ID, die Sie zuvor gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="e1f70-171">Update the *MicrosoftAppId* value with your Bot ID that you saved earlier.</span></span> <span data-ttu-id="e1f70-172">Aktualisieren Sie das *MicrosoftAppPassword* mit dem zuvor gespeicherten bot-Kennwort.</span><span class="sxs-lookup"><span data-stu-id="e1f70-172">Update the *MicrosoftAppPassword* with the Bot password you saved earlier.</span></span>

<img width="560px" src="~/assets/images/get-started/get-started-net-azure-add-keys.png" title="Festlegen der Schlüssel"/>

<span data-ttu-id="e1f70-174">Nachdem diese Änderungen vorgenommen wurden, erstellen Sie die APP neu.</span><span class="sxs-lookup"><span data-stu-id="e1f70-174">Once these changes are made, rebuild the app.</span></span> <span data-ttu-id="e1f70-175">Wenn Sie ngrok verwenden, führen Sie die APP lokal aus, und wenn Sie in Azure hosten, müssen Sie die APP erneut bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="e1f70-175">If you are using ngrok, run the app locally, and if you are hosting in Azure redeploy the app.</span></span>

## <a name="configure-the-app-tab"></a><span data-ttu-id="e1f70-176">Konfigurieren der Registerkarte "App"</span><span class="sxs-lookup"><span data-stu-id="e1f70-176">Configure the app tab</span></span>

<span data-ttu-id="e1f70-177">Nachdem Sie die app in einem Team installiert haben, müssen Sie Sie so konfigurieren, dass Inhalte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="e1f70-177">Once you install the app into a team, you will need to configure it to show content.</span></span> <span data-ttu-id="e1f70-178">Wechseln Sie zu einem Kanal im Team, in dem Sie die Beispiel-App installiert haben, und klicken Sie auf die Schaltfläche **"+"** , um eine neue Registerkarte hinzuzufügen. Sie können dann in `Hello World` der Liste **Registerkarte hinzufügen** auswählen.</span><span class="sxs-lookup"><span data-stu-id="e1f70-178">Go to a channel in the team where you installed the sample app and click on the **'+'** button to add a new tab. You can then choose `Hello World` from the **Add a tab** list.</span></span> <span data-ttu-id="e1f70-179">Anschließend wird ein Konfigurationsdialogfeld angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e1f70-179">You will then be presented with a configuration dialog.</span></span> <span data-ttu-id="e1f70-180">In diesem Dialogfeld können Sie auswählen, welche Registerkarte in diesem Kanal angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="e1f70-180">This dialog will let you choose which tab to display in this channel.</span></span> <span data-ttu-id="e1f70-181">Nachdem Sie die Registerkarte ausgewählt haben und `Save` klicken Sie auf dann können `Hello World` Sie die Registerkarte mit der ausgewählten Registerkarte geladen sehen.</span><span class="sxs-lookup"><span data-stu-id="e1f70-181">Once you select the tab and click on `Save` then you can see the `Hello World` tab loaded with the tab you chose.</span></span>

<img width="530px" src="~/assets/images/samples-hello-world-tab-configure.png" title="Screenshot von configure" />

### <a name="test-your-bot-in-teams"></a><span data-ttu-id="e1f70-183">Testen Sie Ihren bot in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="e1f70-183">Test your bot in Teams</span></span>

<span data-ttu-id="e1f70-184">Sie können nun mit dem bot in Microsoft Teams interagieren.</span><span class="sxs-lookup"><span data-stu-id="e1f70-184">You can now interact with the bot in Teams.</span></span> <span data-ttu-id="e1f70-185">Wählen Sie einen Kanal in dem Team aus, in dem Sie Ihre APP `@your-bot-name`registriert haben, und geben Sie ein.</span><span class="sxs-lookup"><span data-stu-id="e1f70-185">Choose a channel in the team where you registered your app, and type `@your-bot-name`.</span></span> <span data-ttu-id="e1f70-186">Dies wird als \*\* \@Erwähnung\*\*bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="e1f70-186">This is called an **\@mention**.</span></span> <span data-ttu-id="e1f70-187">Jede Nachricht, die Sie an den bot senden, wird als Antwort an Sie zurückgesendet.</span><span class="sxs-lookup"><span data-stu-id="e1f70-187">Whatever message you send to the bot will be sent back to you as a reply.</span></span>

<img width="450px" title="Bot-Antworten" src="~/assets/images/samples-hello-world-bot.png" />

### <a name="test-your-messaging-extension"></a><span data-ttu-id="e1f70-189">Testen der Messaging Erweiterung</span><span class="sxs-lookup"><span data-stu-id="e1f70-189">Test your messaging extension</span></span>

<span data-ttu-id="e1f70-190">Um Ihre Messaging Erweiterung zu testen, können Sie auf die drei Punkte unter dem Eingabefeld in ihrer Unterhaltungsansicht klicken.</span><span class="sxs-lookup"><span data-stu-id="e1f70-190">To test your messaging extension, you can click on the three dots below the input box in your conversation view.</span></span> <span data-ttu-id="e1f70-191">Ein Menü wird mit der **"Hello World"-** app in diesem Popup angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e1f70-191">A menu will pop up with the **'Hello World'** app in it.</span></span> <span data-ttu-id="e1f70-192">Wenn Sie darauf klicken, sehen Sie eine Reihe von zufälligen Texten, die angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="e1f70-192">When you click it, you will see a bunch of random texts showing up.</span></span> <span data-ttu-id="e1f70-193">Sie können eine von Ihnen auswählen, und Sie wird in Ihre Unterhaltung eingefügt.</span><span class="sxs-lookup"><span data-stu-id="e1f70-193">You can choose any one of them and it will be inserted it into your conversation.</span></span>

<img width="530px" title="Menü "Messaging Erweiterung"" src="~/assets/images/samples-hello-world-messaging-extensions-menu.png" />

<img width="530px" title="Ergebnis der Messaging-Erweiterung" src="~/assets/images/samples-hello-world-messaging-extensions-result.png" />

<span data-ttu-id="e1f70-196">Wählen Sie einen der zufälligen Texte aus, und Sie sehen eine Karte, die formatiert und mit ihrer eigenen Nachricht am unteren Rand gesendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="e1f70-196">Choose one of the random texts, and you will see a card formatted and ready to send with your own message at the bottom.</span></span>

<img width="530px" title="Messaging-Durchwahl senden" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />
