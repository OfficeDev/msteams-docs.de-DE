---
title: Erste Schritte mit App Studio und Node. js
description: Erste Schritte beim Erstellen von tollen apps in Microsoft Teams mit Node. js und App Studio
keywords: Erste Schritte Node. js nodejs App Studio
ms.date: 11/09/2018
ms.topic: tutorial
ms.custom: scenarios:getting-started; languages:JavaScript,Node.js
ms.openlocfilehash: 92fbbdd30e9cdaf54644b42bf642ca5825bcec51
ms.sourcegitcommit: b13b38a104946c32cd5245a7af706070e534927d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2020
ms.locfileid: "43034050"
---
# <a name="get-started-on-the-microsoft-teams-platform-with-nodejs-and-app-studio"></a><span data-ttu-id="28e55-104">Erste Schritte mit der Microsoft Teams-Plattform mit Node. js und App Studio</span><span class="sxs-lookup"><span data-stu-id="28e55-104">Get started on the Microsoft Teams platform with Node.js and App Studio</span></span>

<span data-ttu-id="28e55-105">Die [Microsoft Teams](/microsoftteams/) -Entwicklerplattform erleichtert Ihnen das Erweitern von Teams und die nahtlose Integration ihrer eigenen Anwendungen und Dienste in den Arbeitsbereich "Teams".</span><span class="sxs-lookup"><span data-stu-id="28e55-105">The [Microsoft Teams](/microsoftteams/) developer platform makes it easy for you to extend Teams and integrate your own applications and services seamlessly into the Teams workspace.</span></span> <span data-ttu-id="28e55-106">Diese Apps können dann an Ihr Unternehmen oder für Teams auf der ganzen Welt verteilt werden.</span><span class="sxs-lookup"><span data-stu-id="28e55-106">These apps can then be distributed to your enterprise or for teams around the world.</span></span>

<span data-ttu-id="28e55-107">Um Microsoft Teams zu erweitern, müssen Sie eine Microsoft Teams-app erstellen.</span><span class="sxs-lookup"><span data-stu-id="28e55-107">To extend Microsoft Teams, you need to create a Microsoft Teams app.</span></span> <span data-ttu-id="28e55-108">Eine Microsoft Teams-APP ist eine Webanwendung, die Sie hosten.</span><span class="sxs-lookup"><span data-stu-id="28e55-108">A Microsoft Teams app is a web application that you host.</span></span> <span data-ttu-id="28e55-109">Diese APP kann dann in Microsoft Teams in den Arbeitsbereich des Benutzers integriert werden.</span><span class="sxs-lookup"><span data-stu-id="28e55-109">This app can then be integrated into the user's workspace in Teams.</span></span>

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="DownloadAndHost"></a>

## <a name="download-and-host-your-app"></a><span data-ttu-id="28e55-110">Herunterladen und Hosten Ihrer APP</span><span class="sxs-lookup"><span data-stu-id="28e55-110">Download and host your app</span></span>

<span data-ttu-id="28e55-111">Führen Sie die folgenden Schritte aus, um eine einfache "Hello World"-app in Microsoft Teams herunterzuladen und zu hosten.</span><span class="sxs-lookup"><span data-stu-id="28e55-111">Follow these steps to download and host a simple "hello world" app in Teams.</span></span>

<a name="GetPrerequisites"></a>

### <a name="get-prerequisites"></a><span data-ttu-id="28e55-112">Abrufen von Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="28e55-112">Get prerequisites</span></span>

<span data-ttu-id="28e55-113">Um dieses Lernprogramm abzuschließen, benötigen Sie die folgenden Tools.</span><span class="sxs-lookup"><span data-stu-id="28e55-113">To complete this tutorial, you need the following tools.</span></span> <span data-ttu-id="28e55-114">Wenn Sie diese nicht bereits haben, können Sie Sie über diese Links installieren.</span><span class="sxs-lookup"><span data-stu-id="28e55-114">If you don't already have them you can install them from these links.</span></span>

- [<span data-ttu-id="28e55-115">Git</span><span class="sxs-lookup"><span data-stu-id="28e55-115">Git</span></span>](https://git-scm.com/downloads)
- [<span data-ttu-id="28e55-116">Node. js und NPM</span><span class="sxs-lookup"><span data-stu-id="28e55-116">Node.js and NPM</span></span>](https://nodejs.org/)
- <span data-ttu-id="28e55-117">Abrufen eines beliebigen Text-Editors oder einer IDE.</span><span class="sxs-lookup"><span data-stu-id="28e55-117">Get any text editor or IDE.</span></span> <span data-ttu-id="28e55-118">Sie können [Visual Studio-Code](https://code.visualstudio.com/download) kostenlos installieren und verwenden.</span><span class="sxs-lookup"><span data-stu-id="28e55-118">You can install and use [Visual Studio Code](https://code.visualstudio.com/download) for free.</span></span>

<span data-ttu-id="28e55-119">Wenn Sie Optionen zum Hinzufügen `git`, `node` `npm`, und `code` dem Pfad während der Installation sehen, wählen Sie, um dies zu tun.</span><span class="sxs-lookup"><span data-stu-id="28e55-119">If you see options to add `git`, `node`, `npm`, and `code` to the PATH during installation, choose to do so.</span></span> <span data-ttu-id="28e55-120">Das ist praktisch.</span><span class="sxs-lookup"><span data-stu-id="28e55-120">It will be handy.</span></span>

<span data-ttu-id="28e55-121">Stellen Sie sicher, dass die Tools verfügbar sind, indem Sie Folgendes in einem Terminalfenster ausführen:</span><span class="sxs-lookup"><span data-stu-id="28e55-121">Verify that the tools are available by running the following in a terminal window:</span></span>

> [!NOTE]
> <span data-ttu-id="28e55-122">Verwenden Sie das Terminal-Fenster, mit dem Sie sich am besten auf Ihrer Plattform vertraut machen.</span><span class="sxs-lookup"><span data-stu-id="28e55-122">Use the terminal window that you are most comfortable with on your platform.</span></span> <span data-ttu-id="28e55-123">In diesen Beispielen wird bash verwendet (in git enthalten), diese Skripts werden jedoch auf den meisten Plattformen ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="28e55-123">These examples use Bash (which is included in Git), but these scripts will run on most platforms.</span></span>

```bash
$ git --version
git version 2.19.0.windows.1

$ node -v
v8.9.3

$ npm -v
5.5.1

$ gulp -v
CLI version 4.0.2
```

<span data-ttu-id="28e55-124">Möglicherweise haben Sie eine andere Version dieser Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="28e55-124">You may have a different version of these applications.</span></span> <span data-ttu-id="28e55-125">Dies sollte kein Problem sein, außer für "schlucken".</span><span class="sxs-lookup"><span data-stu-id="28e55-125">This should not be a problem, except for gulp.</span></span> <span data-ttu-id="28e55-126">Für Schluck müssen Sie Version 4.0.0 oder höher verwenden.</span><span class="sxs-lookup"><span data-stu-id="28e55-126">For gulp you'll need to use version 4.0.0 or later.</span></span>

<span data-ttu-id="28e55-127">Wenn Sie keinen Schluck installiert haben (oder die falsche Version installiert haben), tun Sie dies jetzt, `npm install gulp` indem Sie in Ihrem Terminal-Fenster ausführen.</span><span class="sxs-lookup"><span data-stu-id="28e55-127">If you don't have gulp installed (or have the wrong version installed), do so now by running `npm install gulp` in your terminal window.</span></span>

<span data-ttu-id="28e55-128">Wenn Sie Visual Studio Code installiert haben, können Sie die Installation überprüfen, indem Sie Folgendes durchführen:</span><span class="sxs-lookup"><span data-stu-id="28e55-128">If you have installed Visual Studio Code, you can verify the installation by running:</span></span>

```bash
code --version
1.28.2
929bacba01ef658b873545e26034d1a8067445e9
```

<span data-ttu-id="28e55-129">Sie können weiterhin dieses Terminalfenster verwenden, um die Befehle auszuführen, die in diesem Lernprogramm folgen.</span><span class="sxs-lookup"><span data-stu-id="28e55-129">You can continue to use this terminal window to run the commands that follow in this tutorial.</span></span>

<a name="DownloadSample"></a>

### <a name="download-the-sample"></a><span data-ttu-id="28e55-130">Herunterladen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="28e55-130">Download the sample</span></span>

<span data-ttu-id="28e55-131">Wir haben ein einfaches [Hello, World](https://github.com/OfficeDev/msteams-samples-hello-world-nodejs) bereitgestellt!</span><span class="sxs-lookup"><span data-stu-id="28e55-131">We have provided a simple [Hello, World!](https://github.com/OfficeDev/msteams-samples-hello-world-nodejs)</span></span> <span data-ttu-id="28e55-132">Beispiel für die ersten Schritte.</span><span class="sxs-lookup"><span data-stu-id="28e55-132">sample to get you started.</span></span> <span data-ttu-id="28e55-133">Führen Sie in einem Terminalfenster den folgenden Befehl aus, um das Beispiel-Repository auf Ihren lokalen Computer zu klonen:</span><span class="sxs-lookup"><span data-stu-id="28e55-133">In a terminal window, run the following command to clone the sample repository to your local machine:</span></span>

```bash
git clone https://github.com/OfficeDev/msteams-samples-hello-world-nodejs.git
```

> [!TIP]
> <span data-ttu-id="28e55-134">Sie können dieses [Repo](https://github.com/OfficeDev/msteams-samples-hello-world-nodejs) [abzweigen](https://help.github.com/articles/fork-a-repo/) , wenn Sie Ihre Änderungen an Ihrem GitHub-Repo zum späteren Nachschlagen ändern und einchecken möchten.</span><span class="sxs-lookup"><span data-stu-id="28e55-134">You can [fork](https://help.github.com/articles/fork-a-repo/) this [repo](https://github.com/OfficeDev/msteams-samples-hello-world-nodejs) if you want to modify and check in your changes to your GitHub repo for future reference.</span></span>

<a name="BuildRun"></a>

### <a name="build-and-run-the-sample"></a><span data-ttu-id="28e55-135">Erstellen und Ausführen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="28e55-135">Build and run the sample</span></span>

<span data-ttu-id="28e55-136">Nachdem das Repository geklont wurde, wechseln Sie in das Verzeichnis, in dem sich das Beispiel befindet:</span><span class="sxs-lookup"><span data-stu-id="28e55-136">Once the repo is cloned, change to the directory that holds the sample:</span></span>

```bash
cd msteams-samples-hello-world-nodejs
```

<span data-ttu-id="28e55-137">Um das Beispiel zu erstellen, müssen Sie alle Abhängigkeiten installieren.</span><span class="sxs-lookup"><span data-stu-id="28e55-137">In order to build the sample, you need to install all its dependencies.</span></span> <span data-ttu-id="28e55-138">Führen Sie dazu den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="28e55-138">Run the following command to do this:</span></span>

```bash
npm install
```

<span data-ttu-id="28e55-139">Sie sollten eine Reihe von Abhängigkeiten erhalten, die installiert werden.</span><span class="sxs-lookup"><span data-stu-id="28e55-139">You should see a bunch of dependencies getting installed.</span></span> <span data-ttu-id="28e55-140">Nachdem Sie fertig sind, können Sie die app ausführen:</span><span class="sxs-lookup"><span data-stu-id="28e55-140">Once they are finished, you can run the app:</span></span>

```bash
npm start
```

<span data-ttu-id="28e55-141">Wenn die Hello-World-App gestartet wird, `App started listening on port 3333` wird Sie im Terminalfenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="28e55-141">When the hello-world app starts, it displays `App started listening on port 3333` in the terminal window.</span></span>

> [!NOTE]
> <span data-ttu-id="28e55-142">Wenn in der obigen Meldung eine andere Portnummer angezeigt wird, liegt dies daran, dass Sie eine Umgebungsvariable für die Port Umgebung festgelegt haben.</span><span class="sxs-lookup"><span data-stu-id="28e55-142">If you see a different port number displayed in the message above, it is because you have a PORT environment variable set.</span></span> <span data-ttu-id="28e55-143">Sie können diesen Port weiterhin verwenden oder Ihre Umgebungsvariable in 3333 ändern.</span><span class="sxs-lookup"><span data-stu-id="28e55-143">You can continue to use that port or change your environment variable to 3333.</span></span>

<span data-ttu-id="28e55-144">Nun können Sie ein Browserfenster öffnen und zu den folgenden URLs navigieren, um zu überprüfen, ob alle App-URLs geladen werden:</span><span class="sxs-lookup"><span data-stu-id="28e55-144">At this point, you can open a browser window and navigate to the following URLs to verify that all the app URLs are loading:</span></span>

- [http://localhost:3333](http://localhost:3333)
- [http://localhost:3333/hello](http://localhost:3333/hello)
- [http://localhost:3333/first](http://localhost:3333/first)
- [http://localhost:3333/second](http://localhost:3333/second)

<a name="HostSample"></a>

### <a name="host-the-sample-app"></a><span data-ttu-id="28e55-145">Hosten der Beispiel-App</span><span class="sxs-lookup"><span data-stu-id="28e55-145">Host the sample app</span></span>

<span data-ttu-id="28e55-146">Beachten Sie, dass apps in Microsoft Teams Webanwendungen sind, die eine oder mehrere Funktionen verfügbar machen.</span><span class="sxs-lookup"><span data-stu-id="28e55-146">Remember that apps in Microsoft Teams are web applications exposing one or more capabilities.</span></span> <span data-ttu-id="28e55-147">Damit die Microsoft Teams-Plattform Ihre APP lädt, muss Ihre APP über das Internet erreichbar sein.</span><span class="sxs-lookup"><span data-stu-id="28e55-147">For the Teams platform to load your app, your app must be reachable from the internet.</span></span> <span data-ttu-id="28e55-148">Damit Ihre APP über das Internet erreichbar ist, müssen Sie Ihre APP *hosten* .</span><span class="sxs-lookup"><span data-stu-id="28e55-148">To make your app reachable from the internet, you need to *host* your app.</span></span>

<span data-ttu-id="28e55-149">Für lokale Tests können Sie die APP auf Ihrem lokalen Computer ausführen und einen Tunnel mit einem Webendpunkt erstellen.</span><span class="sxs-lookup"><span data-stu-id="28e55-149">For local testing you can run the app on your local machine and create a tunnel to it with a web endpoint.</span></span> <span data-ttu-id="28e55-150">[ngrok](https://ngrok.com) ist ein kostenloses Tool, mit dem Sie genau dies tun können.</span><span class="sxs-lookup"><span data-stu-id="28e55-150">[ngrok](https://ngrok.com) is a free tool that lets you do just that.</span></span> <span data-ttu-id="28e55-151">Mit *ngrok* können Sie eine Webadresse wie `https://d0ac14a5.ngrok.io` (diese URL ist nur ein Beispiel) erhalten.</span><span class="sxs-lookup"><span data-stu-id="28e55-151">With *ngrok* you can get a web address such as `https://d0ac14a5.ngrok.io` (this URL is just an example).</span></span> <span data-ttu-id="28e55-152">Sie können *ngrok* für Ihre Umgebung [herunterladen und installieren](https://ngrok.com/download) .</span><span class="sxs-lookup"><span data-stu-id="28e55-152">You can [download and install](https://ngrok.com/download) *ngrok* for your environment.</span></span> <span data-ttu-id="28e55-153">Stellen Sie sicher, dass Sie Sie an einen Speicherort `PATH`in Ihrem hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="28e55-153">Make sure you add it to a location in your `PATH`.</span></span>

<span data-ttu-id="28e55-154">Nachdem Sie es installiert haben, können Sie ein neues Terminalfenster öffnen und den folgenden Befehl ausführen, um einen Tunnel zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="28e55-154">Once you install it, you can open a new terminal window and run the following command to create a tunnel.</span></span> <span data-ttu-id="28e55-155">Im Beispiel wird Port 3333 verwendet, stellen Sie daher sicher, dass Sie es hier angeben.</span><span class="sxs-lookup"><span data-stu-id="28e55-155">The sample uses port 3333, so be sure to specify it here.</span></span>

```bash
ngrok http 3333 -host-header=localhost:3333
```

<span data-ttu-id="28e55-156">*Ngrok* wird Anfragen aus dem Internet abhören und diese an Ihre APP weiterleiten, die auf Port 3333 läuft.</span><span class="sxs-lookup"><span data-stu-id="28e55-156">*Ngrok* will listen to requests from the internet and will route them to your app running on port 3333.</span></span> <span data-ttu-id="28e55-157">Sie können überprüfen, ob Sie Ihren Browser öffnen `https://d0ac14a5.ngrok.io/hello` und die Hello-Seite Ihrer App laden.</span><span class="sxs-lookup"><span data-stu-id="28e55-157">You can verify by opening your browser and going to `https://d0ac14a5.ngrok.io/hello` to load your app's hello page.</span></span> <span data-ttu-id="28e55-158">Achten Sie darauf, dass Sie die von *ngrok* in ihrer Konsolensitzung angezeigte Weiterleitungsadresse anstelle dieser URL verwenden.</span><span class="sxs-lookup"><span data-stu-id="28e55-158">Please be sure to use the forwarding address displayed by *ngrok* in your console session instead of this URL.</span></span>

> [!NOTE]
> <span data-ttu-id="28e55-159">Wenn Sie einen anderen Port im Schritt " [Build" und "ausführen](#build-and-run-the-sample) " verwendet haben, stellen Sie sicher, dass Sie die gleiche Portnummer zum Einrichten des *ngrok* -Tunnels verwenden.</span><span class="sxs-lookup"><span data-stu-id="28e55-159">If you have used a different port in the [build and run](#build-and-run-the-sample) step above, make sure you use the same port number to setup the *ngrok* tunnel.</span></span>
> [!TIP]
> <span data-ttu-id="28e55-160">Es empfiehlt sich, *ngrok* in einem anderen Terminalfenster auszuführen, damit es ausgeführt wird, ohne dass die Knoten-App gestört wird, die Sie später möglicherweise beenden, neu erstellen und erneut ausführen müssen.</span><span class="sxs-lookup"><span data-stu-id="28e55-160">It is a good idea to run *ngrok* in a different terminal window to keep it running without interfering with the node app which you might later have to stop, rebuild and rerun.</span></span> <span data-ttu-id="28e55-161">In diesem Fenster werden in der *ngrok* -Sitzung nützliche Debuginformationen zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="28e55-161">The *ngrok* session will return useful debugging information in this window.</span></span>

<span data-ttu-id="28e55-162">Es gibt eine kostenpflichtige Version von *ngrok* , die persistente Namen zulässt.</span><span class="sxs-lookup"><span data-stu-id="28e55-162">There is a paid version of *ngrok* that allows persistent names.</span></span> <span data-ttu-id="28e55-163">Wenn Sie die ﻿kostenlose Version verwenden, ist Ihre APP nur während der aktuellen Sitzung auf dem Entwicklungscomputer verfügbar.</span><span class="sxs-lookup"><span data-stu-id="28e55-163">If you use the free version your app will only be available during the current session on your development machine.</span></span> <span data-ttu-id="28e55-164">Wenn der Computer heruntergefahren wird oder in den Standbymodus wechselt, steht der Dienst nicht mehr zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="28e55-164">If the machine is shut down or goes to sleep the service will no longer be available.</span></span> <span data-ttu-id="28e55-165">Denken Sie daran, wenn Sie die APP für Tests von anderen Benutzern freigeben.</span><span class="sxs-lookup"><span data-stu-id="28e55-165">Remember this when sharing the app for testing by other users.</span></span> <span data-ttu-id="28e55-166">Wenn Sie den Dienst neu starten müssen, wird eine neue Adresse zurückgegeben, und Sie müssen jeden Ort aktualisieren, an dem diese Adresse verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="28e55-166">If you have to restart the service it will return a new address and you will have to update every place that uses that address.</span></span>

<span data-ttu-id="28e55-167">Notieren Sie sich die URL Ihrer APP, da Sie dies später benötigen, wenn Sie die app in Microsoft Teams mithilfe von App Studio registrieren.</span><span class="sxs-lookup"><span data-stu-id="28e55-167">Remember, make a note of the URL of your app because you will need this later when you register the app with Teams using App studio.</span></span> <span data-ttu-id="28e55-168">Der Editor funktioniert zu diesem Zweck einwandfrei.</span><span class="sxs-lookup"><span data-stu-id="28e55-168">Notepad works fine for this purpose.</span></span>

<a name="DeployToTeams"></a>

## <a name="deploy-your-app-to-microsoft-teams"></a><span data-ttu-id="28e55-169">Bereitstellen der APP für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="28e55-169">Deploy your app to Microsoft Teams</span></span>

<span data-ttu-id="28e55-170">An diesem Punkt haben Sie eine APP, die im Internet gehostet wird, aber Sie haben keine Möglichkeit, Microsoft Teams mitzuteilen, wo Sie suchen sollen oder sogar, was Ihre APP heißt.</span><span class="sxs-lookup"><span data-stu-id="28e55-170">At this point you have an app hosted on the internet, but you have no way yet of telling Teams where to look for it, or even what your app is called.</span></span> <span data-ttu-id="28e55-171">Dafür müssen Sie nun ein App-Paket erstellen.</span><span class="sxs-lookup"><span data-stu-id="28e55-171">To do this you now have to create an app package.</span></span> <span data-ttu-id="28e55-172">Dies ist kaum mehr als eine Textdatei, die das App-Manifest und einige Symbole enthält, die der Microsoft Teams-Client zum ordnungsgemäßen anzeigen und Branding Ihrer APP verwendet.</span><span class="sxs-lookup"><span data-stu-id="28e55-172">This is little more than a text file that contains the app manifest and some icons that the Teams client will use to properly display and brand your app.</span></span> <span data-ttu-id="28e55-173">Sie können dieses app-Paket manuell erstellen, oder Sie können APP Studio verwenden, ein Tool, das in Microsoft Teams ausgeführt wird, um den Registrierungsvorgang für die APP zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="28e55-173">You can manually create this app package, or you can use App Studio, a tool that runs in Teams that will simplify the process of registering the app.</span></span> <span data-ttu-id="28e55-174">App Studio ist die empfohlene Methode zum Erstellen und Aktualisieren des App-Pakets.</span><span class="sxs-lookup"><span data-stu-id="28e55-174">App Studio is the recommended way of creating and updating the app package.</span></span>

<span data-ttu-id="28e55-175">Für beide Methoden ist Folgendes erforderlich:</span><span class="sxs-lookup"><span data-stu-id="28e55-175">For either method you will need the following:</span></span>

- <span data-ttu-id="28e55-176">Die URL, über die Ihre APP im Internet gefunden werden kann.</span><span class="sxs-lookup"><span data-stu-id="28e55-176">The URL where your app can be found on the internet.</span></span>
- <span data-ttu-id="28e55-177">Symbole, mit denen Microsoft Teams Ihre APP brandingieren kann.</span><span class="sxs-lookup"><span data-stu-id="28e55-177">Icons that Teams will use to brand your app.</span></span> <span data-ttu-id="28e55-178">Das Beispiel enthält Platzhaltersymbole, die sich in "src\static\images.</span><span class="sxs-lookup"><span data-stu-id="28e55-178">The sample comes with placeholder icons located in "src\static\images.</span></span> <span data-ttu-id="28e55-179">Bei Bedarf stellt App Studio auch Standardsymbole bereit.</span><span class="sxs-lookup"><span data-stu-id="28e55-179">App Studio also will provide default icons if needed.</span></span>

[!include[Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

## <a name="update-your-hosted-app"></a><span data-ttu-id="28e55-180">Aktualisieren der gehosteten App</span><span class="sxs-lookup"><span data-stu-id="28e55-180">Update your hosted app</span></span>

<span data-ttu-id="28e55-181">Für die Beispiel-App müssen die folgenden Umgebungsvariablen auf die Werte festgelegt werden, auf die Sie zuvor hingewiesen haben.</span><span class="sxs-lookup"><span data-stu-id="28e55-181">The sample app requires the following environment variables to be set to the values you made a note of earlier.</span></span>

```
MICROSOFT_APP_ID=<YOUR BOT'S APP ID>
MICROSOFT_APP_PASSWORD=<YOUR BOT'S PASSWORD>
WEBSITE_NODE_DEFAULT_VERSION=8.9.4
```

<span data-ttu-id="28e55-182">Die Vorgehensweise unterscheidet sich je nachdem, wie Sie Ihre APP gehostet haben.</span><span class="sxs-lookup"><span data-stu-id="28e55-182">How you do that differs depending on how you hosted your app.</span></span> <span data-ttu-id="28e55-183">Wichtig bei der Verwendung von Umgebungsvariablen ist, dass diese Werte Teil Ihrer Umgebung sind – Sie können über den Code Ihrer APP auf Sie zugreifen, aber Sie werden nicht für Drittanbieter verfügbar gemacht, die die Dateien, aus denen Ihre Website besteht, möglicherweise untersuchen.</span><span class="sxs-lookup"><span data-stu-id="28e55-183">The important thing about using environment variables is that these values are part of your environment - they can be accessed by the code for your app, but they are not exposed to third parties who might examine the files that make up your site.</span></span>

<span data-ttu-id="28e55-184">Wenn Sie die APP mit ngrok durchführen, müssen Sie einige lokale Umgebungsvariablen einrichten.</span><span class="sxs-lookup"><span data-stu-id="28e55-184">If you are running the app using ngrok you'll need to set up some local environment variables.</span></span> <span data-ttu-id="28e55-185">Es gibt viele Möglichkeiten, dies zu tun, aber am einfachsten ist es, wenn Sie Visual Studio Code verwenden, eine [Startkonfiguration](https://code.visualstudio.com/Docs/editor/debugging#_launch-configurations)hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="28e55-185">There are many ways to do this, but the easiest, if you are using Visual Studio Code, is to add a [launch configuration](https://code.visualstudio.com/Docs/editor/debugging#_launch-configurations):</span></span>

``` 
{
    "type": "node",
    "request": "launch",
    "name": "Launch - Teams Debug",
    "program": "${workspaceRoot}/src/app.js",
    "cwd": "${workspaceFolder}/src",
    "env": {
        "BASE_URI": "https://yourNgrokURL.ngrok.io",
        "MICROSOFT_APP_ID": "00000000-0000-0000-0000-000000000000",
        "MICROSOFT_APP_PASSWORD": "yourBotAppPassword",
        "NODE_DEBUG": "botbuilder",
        "SUPPRESS_NO_CONFIG_WARNING": "y",
        "NODE_CONFIG_DIR": "../config"
    }
}
```

<span data-ttu-id="28e55-186">Dabei gilt:</span><span class="sxs-lookup"><span data-stu-id="28e55-186">Where:</span></span>

<span data-ttu-id="28e55-187">MICROSOFT_APP_ID und MICROSOFT_APP_PASSWORD ist jeweils die ID und das Kennwort für Ihren bot.</span><span class="sxs-lookup"><span data-stu-id="28e55-187">MICROSOFT_APP_ID and MICROSOFT_APP_PASSWORD is the ID and password, respectively, for your bot.</span></span>
<span data-ttu-id="28e55-188">In NODE_DEBUG erfahren Sie, was in Ihrem bot in der Visual Studio-Code-Debug-Konsole geschieht.</span><span class="sxs-lookup"><span data-stu-id="28e55-188">NODE_DEBUG will show you what's happening in your bot in the Visual Studio Code debug console.</span></span>
<span data-ttu-id="28e55-189">NODE_CONFIG_DIR verweist auf das Verzeichnis im Stammverzeichnis des Repositorys (Standardmäßig wird bei der lokalen Ausführung der APP im Ordner src nach dieser gesucht).</span><span class="sxs-lookup"><span data-stu-id="28e55-189">NODE_CONFIG_DIR points to the directory at the root of the repository (by default, when the app is run locally, it looks for it in the src folder).</span></span>

> [!Note]
> <span data-ttu-id="28e55-190">Wenn Sie NPM nicht von früher im Lernprogramm angehalten haben, müssen Sie in der `npm stop` Reihenfolge ausgeführt werden, dass Visual Studio Code Ihre Start Konfigurationsvariablen ordnungsgemäß Pickup.</span><span class="sxs-lookup"><span data-stu-id="28e55-190">If you have not stopped npm from earlier in the tutorial, you'll need to run `npm stop` in order for Visual Studio Code to pickup your launch configuration variables correctly.</span></span>

<a name="ConfigureTheAppTab"></a>

## <a name="configure-the-app-tab"></a><span data-ttu-id="28e55-191">Konfigurieren der Registerkarte "App"</span><span class="sxs-lookup"><span data-stu-id="28e55-191">Configure the app tab</span></span>

<span data-ttu-id="28e55-192">Nachdem Sie die app in einem Team installiert haben, müssen Sie Sie so konfigurieren, dass Inhalte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="28e55-192">Once you install the app into a team, you will need to configure it to show content.</span></span> <span data-ttu-id="28e55-193">Wechseln Sie zu einem Kanal im Team, und klicken Sie auf die Schaltfläche **"+"** , um eine neue Registerkarte hinzuzufügen. Sie können dann in `Hello World` der Liste **Registerkarte hinzufügen** auswählen.</span><span class="sxs-lookup"><span data-stu-id="28e55-193">Go to a channel in the team and click on the **'+'** button to add a new tab. You can then choose `Hello World` from the **Add a tab** list.</span></span> <span data-ttu-id="28e55-194">Anschließend wird ein Konfigurationsdialogfeld angezeigt.</span><span class="sxs-lookup"><span data-stu-id="28e55-194">You will then be presented with a configuration dialog.</span></span> <span data-ttu-id="28e55-195">In diesem Dialogfeld können Sie auswählen, welche Registerkarte in diesem Kanal angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="28e55-195">This dialog will let you choose which tab to display in this channel.</span></span> <span data-ttu-id="28e55-196">Sobald Sie die Registerkarte ausgewählt haben und `Save` auf klicken, können `Hello World` Sie die Registerkarte anzeigen, die mit der ausgewählten Registerkarte geladen wurde.</span><span class="sxs-lookup"><span data-stu-id="28e55-196">Once you select the tab and click on `Save` you can see the `Hello World` tab loaded with the tab you chose.</span></span>

<img width="430px" src="~/assets/images/samples-hello-world-tab-configure.png" title="Screenshot von configure" />

### <a name="test-your-bot-in-teams"></a><span data-ttu-id="28e55-198">Testen Sie Ihren bot in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="28e55-198">Test your bot in Teams</span></span>

<span data-ttu-id="28e55-199">Sie können nun mit dem bot in Microsoft Teams interagieren.</span><span class="sxs-lookup"><span data-stu-id="28e55-199">You can now interact with the bot in Teams.</span></span> <span data-ttu-id="28e55-200">Wählen Sie einen Kanal im Team aus, in dem Sie Ihre APP registriert `@your-bot-name`haben, und geben Sie gefolgt von Ihrer Nachricht ein.</span><span class="sxs-lookup"><span data-stu-id="28e55-200">Choose a channel in the team where you registered your app, and type `@your-bot-name`, followed by your message.</span></span> <span data-ttu-id="28e55-201">Dies wird als \*\* \@Erwähnung\*\*bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="28e55-201">This is called an **\@mention**.</span></span> <span data-ttu-id="28e55-202">Jede Nachricht, die Sie an den bot senden, wird als Antwort an Sie zurückgesendet.</span><span class="sxs-lookup"><span data-stu-id="28e55-202">Whatever message you send to the bot will be sent back to you as a reply.</span></span>

<img width="450px" title="Bot-Antworten" src="~/assets/images/samples-hello-world-bot.png" />

<a name="ComposeRichMessages"></a>

### <a name="test-your-messaging-extension"></a><span data-ttu-id="28e55-204">Testen der Messaging Erweiterung</span><span class="sxs-lookup"><span data-stu-id="28e55-204">Test your messaging extension</span></span>

<span data-ttu-id="28e55-205">Um Ihre Messaging Erweiterung zu testen, können Sie auf die drei Punkte unter dem Eingabefeld in ihrer Unterhaltungsansicht klicken.</span><span class="sxs-lookup"><span data-stu-id="28e55-205">To test your messaging extension, you can click on the three dots below the input box in your conversation view.</span></span> <span data-ttu-id="28e55-206">Ein Menü wird mit der **"Hello World"-** app in diesem Popup angezeigt.</span><span class="sxs-lookup"><span data-stu-id="28e55-206">A menu will pop up with the **'Hello World'** app in it.</span></span> <span data-ttu-id="28e55-207">Wenn Sie darauf klicken, wird eine Reihe von zufälligen Texten angezeigt.</span><span class="sxs-lookup"><span data-stu-id="28e55-207">When you click it, you will see a number of random texts.</span></span> <span data-ttu-id="28e55-208">Sie können eine von Ihnen auswählen, und Sie wird in Ihre Unterhaltung eingefügt.</span><span class="sxs-lookup"><span data-stu-id="28e55-208">You can choose any one of them and it will be inserted it into your conversation.</span></span>

<img width="430px" title="Menü "Messaging Erweiterung"" src="~/assets/images/samples-hello-world-messaging-extensions-menu.png" />

<img width="430px" title="Ergebnis der Messaging-Erweiterung" src="~/assets/images/samples-hello-world-messaging-extensions-result.png" />

<span data-ttu-id="28e55-211">Wählen Sie einen der zufälligen Texte aus, und Sie sehen eine Karte, die formatiert und mit ihrer eigenen Nachricht am unteren Rand gesendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="28e55-211">Choose one of the random texts, and you will see a card formatted and ready to send with your own message at the bottom.</span></span>

<img width="430px" title="Messaging-Durchwahl senden" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />
