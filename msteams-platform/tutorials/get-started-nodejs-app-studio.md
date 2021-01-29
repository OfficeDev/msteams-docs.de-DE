---
title: Lernprogramm – Erstellen Sie Ihre erste App mithilfe Node.js
description: Erfahren Sie, wie Sie mit dem Erstellen von Microsoft Teams-Apps mit Node.js.
keywords: Erste Schritte node.js nodejs App Studio
ms.topic: tutorial
ms.custom: scenarios:getting-started; languages:JavaScript,Node.js
ms.openlocfilehash: 03dcf79a46266321e54c7e99bf01cdd2a87075fa
ms.sourcegitcommit: fa64b83c0b534bf7a89f256880d5b5ca193e4b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/28/2021
ms.locfileid: "50037046"
---
# <a name="create-your-first-microsoft-teams-app-using-nodejs"></a><span data-ttu-id="a018f-104">Erstellen Sie Ihre erste Microsoft Teams-App mithilfe Node.js</span><span class="sxs-lookup"><span data-stu-id="a018f-104">Create your first Microsoft Teams app using Node.js</span></span>

<span data-ttu-id="a018f-105">Dieses Lernprogramm hilft Ihnen bei den ersten Schritte beim Erstellen einer Microsoft Teams-App Node.js.</span><span class="sxs-lookup"><span data-stu-id="a018f-105">This tutorial helps you get started creating a Microsoft Teams app using Node.js.</span></span>

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="DownloadAndHost"></a>

## <a name="download-and-host-your-app"></a><span data-ttu-id="a018f-106">Herunterladen und Hosten Ihrer App</span><span class="sxs-lookup"><span data-stu-id="a018f-106">Download and host your app</span></span>

<span data-ttu-id="a018f-107">Führen Sie die folgenden Schritte aus, um eine einfache "Hello World"-App in Teams herunterzuladen und zu hosten.</span><span class="sxs-lookup"><span data-stu-id="a018f-107">Follow these steps to download and host a simple "hello world" app in Teams.</span></span>

<a name="GetPrerequisites"></a>

### <a name="get-prerequisites"></a><span data-ttu-id="a018f-108">Voraussetzungen erhalten</span><span class="sxs-lookup"><span data-stu-id="a018f-108">Get prerequisites</span></span>

<span data-ttu-id="a018f-109">Zum Abschließen dieses Lernprogramms benötigen Sie die folgenden Tools.</span><span class="sxs-lookup"><span data-stu-id="a018f-109">To complete this tutorial, you need the following tools.</span></span> <span data-ttu-id="a018f-110">Wenn sie noch nicht vorhanden sind, können Sie sie über diese Links installieren.</span><span class="sxs-lookup"><span data-stu-id="a018f-110">If you don't already have them you can install them from these links.</span></span>

- [<span data-ttu-id="a018f-111">Git</span><span class="sxs-lookup"><span data-stu-id="a018f-111">Git</span></span>](https://git-scm.com/downloads)
- [<span data-ttu-id="a018f-112">Node.js und NPM</span><span class="sxs-lookup"><span data-stu-id="a018f-112">Node.js and NPM</span></span>](https://nodejs.org/)
- <span data-ttu-id="a018f-113">Erhalten Sie einen beliebigen Texteditor oder eine IDE.</span><span class="sxs-lookup"><span data-stu-id="a018f-113">Get any text editor or IDE.</span></span> <span data-ttu-id="a018f-114">Sie können Visual Studio [Code kostenlos](https://code.visualstudio.com/download) installieren und verwenden.</span><span class="sxs-lookup"><span data-stu-id="a018f-114">You can install and use [Visual Studio Code](https://code.visualstudio.com/download) for free.</span></span>

<span data-ttu-id="a018f-115">Wenn während der Installation Optionen zum Hinzufügen , , und zum PFAD angezeigt werden, wählen Sie `git` `node` `npm` `code` dies aus.</span><span class="sxs-lookup"><span data-stu-id="a018f-115">If you see options to add `git`, `node`, `npm`, and `code` to the PATH during installation, choose to do so.</span></span> <span data-ttu-id="a018f-116">Es ist praktisch.</span><span class="sxs-lookup"><span data-stu-id="a018f-116">It will be handy.</span></span>

<span data-ttu-id="a018f-117">Stellen Sie sicher, dass die Tools verfügbar sind, indem Sie folgendes in einem Terminalfenster ausführen:</span><span class="sxs-lookup"><span data-stu-id="a018f-117">Verify that the tools are available by running the following in a terminal window:</span></span>

> [!NOTE]
> <span data-ttu-id="a018f-118">Verwenden Sie das Terminalfenster, mit dem Sie sich auf Ihrer Plattform am besten aus sind.</span><span class="sxs-lookup"><span data-stu-id="a018f-118">Use the terminal window that you are most comfortable with on your platform.</span></span> <span data-ttu-id="a018f-119">In diesen Beispielen wird Bash (in Git enthalten) verwendet, aber diese Skripts werden auf den meisten Plattformen ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="a018f-119">These examples use Bash (which is included in Git), but these scripts will run on most platforms.</span></span>

```bash
$ git --version
git version 2.19.0.windows.1

$ node -v
v8.9.3

$ npm -v
5.5.1

$ gulp -v
CLI version 2.3.0
Local version 4.0.2
```

<span data-ttu-id="a018f-120">Möglicherweise haben Sie eine andere Version dieser Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="a018f-120">You may have a different version of these applications.</span></span> <span data-ttu-id="a018f-121">Dies sollte kein Problem sein, mit Ausnahme von gulp.</span><span class="sxs-lookup"><span data-stu-id="a018f-121">This should not be a problem, except for gulp.</span></span> <span data-ttu-id="a018f-122">Für gulp müssen Sie Version 4.0.0 oder höher verwenden.</span><span class="sxs-lookup"><span data-stu-id="a018f-122">For gulp you'll need to use version 4.0.0 or later.</span></span>

<span data-ttu-id="a018f-123">Wenn Sie gulp nicht installiert haben (oder die falsche Version installiert haben), tun Sie dies jetzt, indem Sie `npm install gulp` in Ihrem Terminalfenster ausführen.</span><span class="sxs-lookup"><span data-stu-id="a018f-123">If you don't have gulp installed (or have the wrong version installed), do so now by running `npm install gulp` in your terminal window.</span></span>

<span data-ttu-id="a018f-124">Wenn Sie Visual Studio Code installiert haben, können Sie die Installation überprüfen, indem Sie dies ausführen:</span><span class="sxs-lookup"><span data-stu-id="a018f-124">If you have installed Visual Studio Code, you can verify the installation by running:</span></span>

```bash
code --version
1.28.2
929bacba01ef658b873545e26034d1a8067445e9
```

<span data-ttu-id="a018f-125">Sie können weiterhin dieses Terminalfenster verwenden, um die Befehle auszuführen, die in diesem Lernprogramm folgen.</span><span class="sxs-lookup"><span data-stu-id="a018f-125">You can continue to use this terminal window to run the commands that follow in this tutorial.</span></span>

<a name="DownloadSample"></a>

### <a name="download-the-sample"></a><span data-ttu-id="a018f-126">Herunterladen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="a018f-126">Download the sample</span></span>

<span data-ttu-id="a018f-127">Wir haben ein einfaches [Hello, World! bereitgestellt.](https://github.com/OfficeDev/msteams-samples-hello-world-nodejs)</span><span class="sxs-lookup"><span data-stu-id="a018f-127">We have provided a simple [Hello, World!](https://github.com/OfficeDev/msteams-samples-hello-world-nodejs)</span></span> <span data-ttu-id="a018f-128">Beispiel für die ersten Schritte.</span><span class="sxs-lookup"><span data-stu-id="a018f-128">sample to get you started.</span></span> <span data-ttu-id="a018f-129">Führen Sie in einem Terminalfenster den folgenden Befehl aus, um das Beispielrepository auf Ihrem lokalen Computer zu klonen:</span><span class="sxs-lookup"><span data-stu-id="a018f-129">In a terminal window, run the following command to clone the sample repository to your local machine:</span></span>

```bash
git clone https://github.com/OfficeDev/msteams-samples-hello-world-nodejs.git
```

> [!TIP]
> <span data-ttu-id="a018f-130">Sie können [dieses Repository ver forken,](https://help.github.com/articles/fork-a-repo/) [](https://github.com/OfficeDev/msteams-samples-hello-world-nodejs) wenn Sie Ihre Änderungen an Ihrem GitHub-Repository ändern und einchecken möchten, um eine zukünftige Referenz zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="a018f-130">You can [fork](https://help.github.com/articles/fork-a-repo/) this [repo](https://github.com/OfficeDev/msteams-samples-hello-world-nodejs) if you want to modify and check in your changes to your GitHub repo for future reference.</span></span>

<a name="BuildRun"></a>

### <a name="build-and-run-the-sample"></a><span data-ttu-id="a018f-131">Erstellen und Ausführen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="a018f-131">Build and run the sample</span></span>

<span data-ttu-id="a018f-132">Nachdem das Repository geklont wurde, wechseln Sie zu dem Verzeichnis, in dem sich das Beispiel befindet:</span><span class="sxs-lookup"><span data-stu-id="a018f-132">Once the repo is cloned, change to the directory that holds the sample:</span></span>

```bash
cd msteams-samples-hello-world-nodejs
```

<span data-ttu-id="a018f-133">Zum Erstellen des Beispiels müssen Sie alle Abhängigkeiten installieren.</span><span class="sxs-lookup"><span data-stu-id="a018f-133">In order to build the sample, you need to install all its dependencies.</span></span> <span data-ttu-id="a018f-134">Führen Sie dazu den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="a018f-134">Run the following command to do this:</span></span>

```bash
npm install
```

<span data-ttu-id="a018f-135">Es sollte eine Reihe von Abhängigkeiten angezeigt werden, die installiert werden.</span><span class="sxs-lookup"><span data-stu-id="a018f-135">You should see a bunch of dependencies getting installed.</span></span> <span data-ttu-id="a018f-136">Sobald sie fertig sind, können Sie die App ausführen:</span><span class="sxs-lookup"><span data-stu-id="a018f-136">Once they are finished, you can run the app:</span></span>

```bash
npm start
```

<span data-ttu-id="a018f-137">Wenn die Hello-World-App gestartet wird, wird sie `App started listening on port 3333` im Terminalfenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a018f-137">When the hello-world app starts, it displays `App started listening on port 3333` in the terminal window.</span></span>

> [!NOTE]
> <span data-ttu-id="a018f-138">Wenn in der obigen Meldung eine andere Portnummer angezeigt wird, ist eine Portumgebungsvariable festgelegt.</span><span class="sxs-lookup"><span data-stu-id="a018f-138">If you see a different port number displayed in the message above, it is because you have a PORT environment variable set.</span></span> <span data-ttu-id="a018f-139">Sie können diesen Port weiterhin verwenden oder die Umgebungsvariable in 3333 ändern.</span><span class="sxs-lookup"><span data-stu-id="a018f-139">You can continue to use that port or change your environment variable to 3333.</span></span>

<span data-ttu-id="a018f-140">An diesem Punkt können Sie ein Browserfenster öffnen und zu den folgenden URLs navigieren, um zu überprüfen, ob alle URLs geladen werden:</span><span class="sxs-lookup"><span data-stu-id="a018f-140">At this point, you can open a browser window and navigate to the following URLs to verify that all the app URLs are loading:</span></span>

- [http://localhost:3333](http://localhost:3333)
- [http://localhost:3333/hello](http://localhost:3333/hello)
- [http://localhost:3333/first](http://localhost:3333/first)
- [http://localhost:3333/second](http://localhost:3333/second)

<a name="HostSample"></a>

### <a name="host-the-sample-app"></a><span data-ttu-id="a018f-141">Hosten der Beispiel-App</span><span class="sxs-lookup"><span data-stu-id="a018f-141">Host the sample app</span></span>

<span data-ttu-id="a018f-142">Denken Sie daran, dass Apps in Microsoft Teams Webanwendungen sind, die eine oder mehrere Funktionen verfügbar machen.</span><span class="sxs-lookup"><span data-stu-id="a018f-142">Remember that apps in Microsoft Teams are web applications exposing one or more capabilities.</span></span> <span data-ttu-id="a018f-143">Damit die Plattform Teams Ihre App laden kann, muss Ihre App über das Internet erreichbar sein.</span><span class="sxs-lookup"><span data-stu-id="a018f-143">For the Teams platform to load your app, your app must be reachable from the internet.</span></span> <span data-ttu-id="a018f-144">Damit Ihre App über das Internet erreichbar ist, müssen Sie *Ihre App* hosten.</span><span class="sxs-lookup"><span data-stu-id="a018f-144">To make your app reachable from the internet, you need to *host* your app.</span></span>

<span data-ttu-id="a018f-145">Für lokale Tests können Sie die App auf Ihrem lokalen Computer ausführen und einen Tunnel mit einem Webendpunkt erstellen.</span><span class="sxs-lookup"><span data-stu-id="a018f-145">For local testing you can run the app on your local machine and create a tunnel to it with a web endpoint.</span></span> <span data-ttu-id="a018f-146">[ngrok](https://ngrok.com) ist ein kostenloses Tool, mit dem Sie genau das tun können.</span><span class="sxs-lookup"><span data-stu-id="a018f-146">[ngrok](https://ngrok.com) is a free tool that lets you do just that.</span></span> <span data-ttu-id="a018f-147">Mit *ngrok* können Sie eine Webadresse wie z. B. `https://d0ac14a5.ngrok.io` (diese URL ist nur ein Beispiel) erhalten.</span><span class="sxs-lookup"><span data-stu-id="a018f-147">With *ngrok* you can get a web address such as `https://d0ac14a5.ngrok.io` (this URL is just an example).</span></span> <span data-ttu-id="a018f-148">Sie können *ngrok für* Ihre Umgebung herunterladen und installieren. [](https://ngrok.com/download)</span><span class="sxs-lookup"><span data-stu-id="a018f-148">You can [download and install](https://ngrok.com/download) *ngrok* for your environment.</span></span> <span data-ttu-id="a018f-149">Stellen Sie sicher, dass Sie es einem Speicherort in Ihrer `PATH` hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="a018f-149">Make sure you add it to a location in your `PATH`.</span></span>

<span data-ttu-id="a018f-150">Nach der Installation können Sie ein neues Terminalfenster öffnen und den folgenden Befehl ausführen, um einen Tunnel zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="a018f-150">Once you install it, you can open a new terminal window and run the following command to create a tunnel.</span></span> <span data-ttu-id="a018f-151">Im Beispiel wird Port 3333 verwendet. Geben Sie ihn daher hier an.</span><span class="sxs-lookup"><span data-stu-id="a018f-151">The sample uses port 3333, so be sure to specify it here.</span></span>

```bash
ngrok http 3333 -host-header=localhost:3333
```

<span data-ttu-id="a018f-152">*Ngrok* hört Anforderungen aus dem Internet ab und führt sie an Ihre App weiter, die an Port 3333 ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="a018f-152">*Ngrok* will listen to requests from the internet and will route them to your app running on port 3333.</span></span> <span data-ttu-id="a018f-153">Sie können dies überprüfen, indem Sie Ihren Browser öffnen und die `https://d0ac14a5.ngrok.io/hello` Hello-Seite Ihrer App laden.</span><span class="sxs-lookup"><span data-stu-id="a018f-153">You can verify by opening your browser and going to `https://d0ac14a5.ngrok.io/hello` to load your app's hello page.</span></span> <span data-ttu-id="a018f-154">Verwenden Sie anstatt dieser URL unbedingt die Weiterleitungsadresse, die *ngrok* in Ihrer Konsolensitzung angezeigt hat.</span><span class="sxs-lookup"><span data-stu-id="a018f-154">Please be sure to use the forwarding address displayed by *ngrok* in your console session instead of this URL.</span></span>

> [!NOTE]
> <span data-ttu-id="a018f-155">Wenn Sie im Build einen [](#build-and-run-the-sample) anderen Port verwendet haben und den obigen Schritt ausführen, stellen Sie sicher, dass Sie zum Einrichten des *ngrok-Tunnels* dieselbe Portnummer verwenden.</span><span class="sxs-lookup"><span data-stu-id="a018f-155">If you have used a different port in the [build and run](#build-and-run-the-sample) step above, make sure you use the same port number to setup the *ngrok* tunnel.</span></span>
> [!TIP]
> <span data-ttu-id="a018f-156">Es ist eine gute Idee, *ngrok* in einem anderen Terminalfenster ausführen, damit es ausgeführt wird, ohne die Knoten-App zu stören, die Sie später möglicherweise beenden, neu erstellen und erneut ausführen müssen.</span><span class="sxs-lookup"><span data-stu-id="a018f-156">It is a good idea to run *ngrok* in a different terminal window to keep it running without interfering with the node app which you might later have to stop, rebuild and rerun.</span></span> <span data-ttu-id="a018f-157">Die *ngrok-Sitzung* gibt nützliche Debuginformationen in diesem Fenster zurück.</span><span class="sxs-lookup"><span data-stu-id="a018f-157">The *ngrok* session will return useful debugging information in this window.</span></span>

<span data-ttu-id="a018f-158">Es gibt eine kostenpflichtige Version von *ngrok,* die beständige Namen zulässt.</span><span class="sxs-lookup"><span data-stu-id="a018f-158">There is a paid version of *ngrok* that allows persistent names.</span></span> <span data-ttu-id="a018f-159">Wenn Sie die kostenlose Version verwenden, ist Ihre App nur während der aktuellen Sitzung auf Ihrem Entwicklungscomputer verfügbar.</span><span class="sxs-lookup"><span data-stu-id="a018f-159">If you use the free version your app will only be available during the current session on your development machine.</span></span> <span data-ttu-id="a018f-160">Wenn der Computer heruntergefahren wird oder in den Ruhezustand geht, ist der Dienst nicht mehr verfügbar.</span><span class="sxs-lookup"><span data-stu-id="a018f-160">If the machine is shut down or goes to sleep the service will no longer be available.</span></span> <span data-ttu-id="a018f-161">Denken Sie daran, wenn Sie die App für Tests durch andere Benutzer freigeben.</span><span class="sxs-lookup"><span data-stu-id="a018f-161">Remember this when sharing the app for testing by other users.</span></span> <span data-ttu-id="a018f-162">Wenn Sie den Dienst neu starten müssen, wird eine neue Adresse zurückgeben, und Sie müssen jeden Ort aktualisieren, der diese Adresse verwendet.</span><span class="sxs-lookup"><span data-stu-id="a018f-162">If you have to restart the service it will return a new address and you will have to update every place that uses that address.</span></span>

<span data-ttu-id="a018f-163">Notieren Sie sich die URL Ihrer App, da Sie diese später benötigen, wenn Sie die App mit App Studio bei Teams registrieren.</span><span class="sxs-lookup"><span data-stu-id="a018f-163">Remember, make a note of the URL of your app because you will need this later when you register the app with Teams using App studio.</span></span> <span data-ttu-id="a018f-164">Editor funktioniert zu diesem Zweck gut.</span><span class="sxs-lookup"><span data-stu-id="a018f-164">Notepad works fine for this purpose.</span></span>

<a name="DeployToTeams"></a>

## <a name="deploy-your-app-to-microsoft-teams"></a><span data-ttu-id="a018f-165">Bereitstellen Ihrer App in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="a018f-165">Deploy your app to Microsoft Teams</span></span>

<span data-ttu-id="a018f-166">An diesem Punkt haben Sie eine App, die im Internet gehostet wird, Aber Sie haben noch keine Möglichkeit, Teams mitzuteilen, wo sie suchen soll oder auch nicht, wie Ihre App heißt.</span><span class="sxs-lookup"><span data-stu-id="a018f-166">At this point you have an app hosted on the internet, but you have no way yet of telling Teams where to look for it, or even what your app is called.</span></span> <span data-ttu-id="a018f-167">Dazu müssen Sie nun ein App-Paket erstellen.</span><span class="sxs-lookup"><span data-stu-id="a018f-167">To do this you now have to create an app package.</span></span> <span data-ttu-id="a018f-168">Dies ist wenig mehr als eine Textdatei, die das App-Manifest und einige Symbole enthält, die der Teams-Client verwendet, um Ihre App ordnungsgemäß zu anzeigen und zu brandmarken.</span><span class="sxs-lookup"><span data-stu-id="a018f-168">This is little more than a text file that contains the app manifest and some icons that the Teams client will use to properly display and brand your app.</span></span> <span data-ttu-id="a018f-169">Sie können dieses App-Paket manuell erstellen oder App Studio verwenden, ein Tool, das in Teams ausgeführt wird und das Registrieren der App vereinfacht.</span><span class="sxs-lookup"><span data-stu-id="a018f-169">You can manually create this app package, or you can use App Studio, a tool that runs in Teams that will simplify the process of registering the app.</span></span> <span data-ttu-id="a018f-170">App Studio ist die empfohlene Methode zum Erstellen und Aktualisieren des App-Pakets.</span><span class="sxs-lookup"><span data-stu-id="a018f-170">App Studio is the recommended way of creating and updating the app package.</span></span>

<span data-ttu-id="a018f-171">Für beide Methoden benötigen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="a018f-171">For either method you will need the following:</span></span>

- <span data-ttu-id="a018f-172">Die URL, unter der Ihre App im Internet zu finden ist.</span><span class="sxs-lookup"><span data-stu-id="a018f-172">The URL where your app can be found on the internet.</span></span>
- <span data-ttu-id="a018f-173">Symbole, die Teams zum Branden Ihrer App verwendet.</span><span class="sxs-lookup"><span data-stu-id="a018f-173">Icons that Teams will use to brand your app.</span></span> <span data-ttu-id="a018f-174">Das Beispiel enthält Platzhaltersymbole in "src\static\images".</span><span class="sxs-lookup"><span data-stu-id="a018f-174">The sample comes with placeholder icons located in "src\static\images.</span></span> <span data-ttu-id="a018f-175">App Studio stellt bei Bedarf auch Standardsymbole zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="a018f-175">App Studio also will provide default icons if needed.</span></span>

[!include[Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

## <a name="update-your-hosted-app"></a><span data-ttu-id="a018f-176">Aktualisieren Ihrer gehosteten App</span><span class="sxs-lookup"><span data-stu-id="a018f-176">Update your hosted app</span></span>

<span data-ttu-id="a018f-177">Die Beispiel-App erfordert, dass die folgenden Umgebungsvariablen auf die Werte festgelegt werden, die Sie zuvor notieren.</span><span class="sxs-lookup"><span data-stu-id="a018f-177">The sample app requires the following environment variables to be set to the values you made a note of earlier.</span></span>

```
MICROSOFT_APP_ID=<YOUR BOT'S APP ID>
MICROSOFT_APP_PASSWORD=<YOUR BOT'S PASSWORD>
WEBSITE_NODE_DEFAULT_VERSION=8.9.4
```

<span data-ttu-id="a018f-178">Wie Sie dies tun, hängt davon ab, wie Sie Ihre App gehostet haben.</span><span class="sxs-lookup"><span data-stu-id="a018f-178">How you do that differs depending on how you hosted your app.</span></span> <span data-ttu-id="a018f-179">Der wichtige Punkt bei der Verwendung von Umgebungsvariablen ist, dass diese Werte Teil Ihrer Umgebung sind. Sie können über den Code für Ihre App darauf zugreifen, werden jedoch nicht für Dritte verfügbar gemacht, die die Dateien untersuchen, aus denen Ihre Website besteht.</span><span class="sxs-lookup"><span data-stu-id="a018f-179">The important thing about using environment variables is that these values are part of your environment - they can be accessed by the code for your app, but they are not exposed to third parties who might examine the files that make up your site.</span></span>

<span data-ttu-id="a018f-180">Wenn Sie die App mit ngrok ausführen, müssen Sie einige lokale Umgebungsvariablen einrichten.</span><span class="sxs-lookup"><span data-stu-id="a018f-180">If you are running the app using ngrok you'll need to set up some local environment variables.</span></span> <span data-ttu-id="a018f-181">Es gibt viele Möglichkeiten, dies zu tun, aber die einfachste Möglichkeit, wenn Sie Visual Studio Code verwenden, ist das Hinzufügen einer [Startkonfiguration:](https://code.visualstudio.com/Docs/editor/debugging#_launch-configurations)</span><span class="sxs-lookup"><span data-stu-id="a018f-181">There are many ways to do this, but the easiest, if you are using Visual Studio Code, is to add a [launch configuration](https://code.visualstudio.com/Docs/editor/debugging#_launch-configurations):</span></span>

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

<span data-ttu-id="a018f-182">Dabei gilt Folgendes:</span><span class="sxs-lookup"><span data-stu-id="a018f-182">Where:</span></span>

<span data-ttu-id="a018f-183">MICROSOFT_APP_ID und MICROSOFT_APP_PASSWORD ist die ID bzw. das Kennwort für Ihren Bot.</span><span class="sxs-lookup"><span data-stu-id="a018f-183">MICROSOFT_APP_ID and MICROSOFT_APP_PASSWORD is the ID and password, respectively, for your bot.</span></span>
<span data-ttu-id="a018f-184">NODE_DEBUG zeigt Ihnen, was in Ihrem Bot geschieht, in der Visual Studio Code-Debugkonsole.</span><span class="sxs-lookup"><span data-stu-id="a018f-184">NODE_DEBUG will show you what's happening in your bot in the Visual Studio Code debug console.</span></span>
<span data-ttu-id="a018f-185">NODE_CONFIG_DIR verweist auf das Verzeichnis im Stammverzeichnis des Repositorys (wenn die App lokal ausgeführt wird, sucht sie standardmäßig im Ordner "src").</span><span class="sxs-lookup"><span data-stu-id="a018f-185">NODE_CONFIG_DIR points to the directory at the root of the repository (by default, when the app is run locally, it looks for it in the src folder).</span></span>

> [!Note]
> <span data-ttu-id="a018f-186">Wenn Sie npm weiter oben im Lernprogramm nicht beendet haben, müssen Sie die Ausführung ausführen, damit Visual Studio Code ihre Startkonfigurationsvariablen `npm stop` richtig anfordert.</span><span class="sxs-lookup"><span data-stu-id="a018f-186">If you have not stopped npm from earlier in the tutorial, you'll need to run `npm stop` in order for Visual Studio Code to pickup your launch configuration variables correctly.</span></span>

<a name="ConfigureTheAppTab"></a>

## <a name="configure-the-app-tab"></a><span data-ttu-id="a018f-187">Konfigurieren der Registerkarte "App"</span><span class="sxs-lookup"><span data-stu-id="a018f-187">Configure the app tab</span></span>

<span data-ttu-id="a018f-188">Nachdem Sie die App in einem Team installiert haben, müssen Sie sie so konfigurieren, dass Inhalte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="a018f-188">Once you install the app into a team, you will need to configure it to show content.</span></span> <span data-ttu-id="a018f-189">Wechseln Sie zu einem Kanal im Team, und klicken Sie auf die Schaltfläche **"+",** um eine neue Registerkarte hinzuzufügen. Sie können dann aus der `Hello World` Registerkartenliste **"Hinzufügen"** auswählen.</span><span class="sxs-lookup"><span data-stu-id="a018f-189">Go to a channel in the team and click on the **'+'** button to add a new tab. You can then choose `Hello World` from the **Add a tab** list.</span></span> <span data-ttu-id="a018f-190">Anschließend wird ein Konfigurationsdialogfeld angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a018f-190">You will then be presented with a configuration dialog.</span></span> <span data-ttu-id="a018f-191">In diesem Dialogfeld können Sie auswählen, welche Registerkarte in diesem Kanal angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="a018f-191">This dialog will let you choose which tab to display in this channel.</span></span> <span data-ttu-id="a018f-192">Nachdem Sie die Registerkarte ausgewählt und darauf geklickt haben, wird die Registerkarte mit der ausgewählten `Save` `Hello World` Registerkarte geladen.</span><span class="sxs-lookup"><span data-stu-id="a018f-192">Once you select the tab and click on `Save` you can see the `Hello World` tab loaded with the tab you chose.</span></span>

<img width="430px" src="~/assets/images/samples-hello-world-tab-configure.png" alt-text="Screenshot of configure" />

### <a name="test-your-bot-in-teams"></a><span data-ttu-id="a018f-193">Testen Ihres Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="a018f-193">Test your bot in Teams</span></span>

<span data-ttu-id="a018f-194">Sie können jetzt mit dem Bot in Teams interagieren.</span><span class="sxs-lookup"><span data-stu-id="a018f-194">You can now interact with the bot in Teams.</span></span> <span data-ttu-id="a018f-195">Wählen Sie einen Kanal im Team aus, in dem Sie Ihre App registriert haben, und geben Sie `@your-bot-name` , gefolgt von Ihrer Nachricht, ein.</span><span class="sxs-lookup"><span data-stu-id="a018f-195">Choose a channel in the team where you registered your app, and type `@your-bot-name`, followed by your message.</span></span> <span data-ttu-id="a018f-196">Dies wird als Erwähnung **\@ bezeichnet.**</span><span class="sxs-lookup"><span data-stu-id="a018f-196">This is called an **\@mention**.</span></span> <span data-ttu-id="a018f-197">Welche Nachricht Sie an den Bot senden, wird als Antwort an Sie zurückgeschickt.</span><span class="sxs-lookup"><span data-stu-id="a018f-197">Whatever message you send to the bot will be sent back to you as a reply.</span></span>

<img width="450px" alt-text="Bot responses" src="~/assets/images/samples-hello-world-bot.png" />

<a name="ComposeRichMessages"></a>

### <a name="test-your-messaging-extension"></a><span data-ttu-id="a018f-198">Testen der Messagingerweiterung</span><span class="sxs-lookup"><span data-stu-id="a018f-198">Test your messaging extension</span></span>

<span data-ttu-id="a018f-199">Zum Testen Ihrer Messagingerweiterung können Sie auf die drei Punkte unter dem Eingabefeld in der Unterhaltungsansicht klicken.</span><span class="sxs-lookup"><span data-stu-id="a018f-199">To test your messaging extension, you can click on the three dots below the input box in your conversation view.</span></span> <span data-ttu-id="a018f-200">Ein Menü mit der **"Hello World"-App** wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a018f-200">A menu will pop up with the **'Hello World'** app in it.</span></span> <span data-ttu-id="a018f-201">Wenn Sie darauf klicken, wird eine Reihe zufälliger Texte zu sehen sein.</span><span class="sxs-lookup"><span data-stu-id="a018f-201">When you click it, you will see a number of random texts.</span></span> <span data-ttu-id="a018f-202">Sie können eine davon auswählen und in Ihre Unterhaltung einfügen.</span><span class="sxs-lookup"><span data-stu-id="a018f-202">You can choose any one of them and it will be inserted it into your conversation.</span></span>

<img width="430px" alt-text="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu.png" />

<img width="430px" alt-text="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result.png" />

<span data-ttu-id="a018f-203">Wählen Sie einen der zufälligen Texte aus, und unten wird eine Karte formatiert und bereit zum Senden mit Ihrer eigenen Nachricht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a018f-203">Choose one of the random texts, and you will see a card formatted and ready to send with your own message at the bottom.</span></span>

<img width="430px" alt-text="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />
