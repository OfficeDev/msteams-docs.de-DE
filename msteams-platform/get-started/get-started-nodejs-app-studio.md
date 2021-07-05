---
title: Lernprogramm – Erstellen Ihrer ersten App mit Node.js
description: Erfahren Sie, wie Sie mit Microsoft Teams-Apps mit Node.js beginnen.
keywords: Erste Schritte node.js nodejs App Studio
ms.topic: tutorial
localization_priority: Normal
ms.custom: scenarios:getting-started; languages:JavaScript,Node.js
ms.openlocfilehash: 84c3452c739f67c2908d698b627b5651ff9d5d7a
ms.sourcegitcommit: 9d63611974ba8a7e7f19ceea35e50189a2e90434
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2021
ms.locfileid: "53254376"
---
# <a name="build-your-first-microsoft-teams-app-using-nodejs"></a><span data-ttu-id="e51cd-104">Erstellen Ihrer ersten Microsoft Teams-App mit Node.js</span><span class="sxs-lookup"><span data-stu-id="e51cd-104">Build your first Microsoft Teams app using Node.js</span></span>

<span data-ttu-id="e51cd-105">In diesem Lernprogramm erfahren Sie, wie Sie Ihre erste Microsoft Teams-App mit Node.js erstellen.</span><span class="sxs-lookup"><span data-stu-id="e51cd-105">In this tutorial, you will learn how to build your very first Microsoft Teams app using Node.js.</span></span> <span data-ttu-id="e51cd-106">Außerdem werden Sie durch die folgenden Schritte geführt:</span><span class="sxs-lookup"><span data-stu-id="e51cd-106">It also walks you through the steps to:</span></span> 

1. [<span data-ttu-id="e51cd-107">Vorbereiten der Umgebung</span><span class="sxs-lookup"><span data-stu-id="e51cd-107">Prepare your environment</span></span>](#prepare-environment)
1. [<span data-ttu-id="e51cd-108">Voraussetzungen abrufen</span><span class="sxs-lookup"><span data-stu-id="e51cd-108">Get prerequisites</span></span>](#GetPrerequisites)
1. [<span data-ttu-id="e51cd-109">Beispiel herunterladen</span><span class="sxs-lookup"><span data-stu-id="e51cd-109">Download the sample</span></span>](#DownloadSample)
1. [<span data-ttu-id="e51cd-110">Erstellen und Ausführen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="e51cd-110">Build and run the sample</span></span>](#BuildRun)
1. [<span data-ttu-id="e51cd-111">Hosten der Beispiel-App</span><span class="sxs-lookup"><span data-stu-id="e51cd-111">Host the sample app</span></span>](#HostSample)
1. [<span data-ttu-id="e51cd-112">Aktualisieren der Anmeldeinformationen für Ihre gehostete App</span><span class="sxs-lookup"><span data-stu-id="e51cd-112">Update the credentials for your hosted app</span></span>](#updatecredentials)
1. [<span data-ttu-id="e51cd-113">Konfigurieren der Registerkarte "App"</span><span class="sxs-lookup"><span data-stu-id="e51cd-113">Configure the app tab</span></span>](#ConfigureTheAppTab)

<a name="prepare-environment"></a>

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="GetPrerequisites"></a>

### <a name="download-and-host-your-app"></a><span data-ttu-id="e51cd-114">Herunterladen und Hosten Ihrer App</span><span class="sxs-lookup"><span data-stu-id="e51cd-114">Download and host your app</span></span>

<span data-ttu-id="e51cd-115">Führen Sie die folgenden Schritte aus, um eine einfache "Hello World"-App in Teams herunterzuladen und zu hosten.</span><span class="sxs-lookup"><span data-stu-id="e51cd-115">Follow these steps to download and host a simple "hello world" app in Teams.</span></span>

<a name="GetPrerequisites"></a>

## <a name="get-prerequisites"></a><span data-ttu-id="e51cd-116">Voraussetzungen abrufen</span><span class="sxs-lookup"><span data-stu-id="e51cd-116">Get prerequisites</span></span>

<span data-ttu-id="e51cd-117">Zum Abschließen dieses Lernprogramms benötigen Sie die folgenden Tools.</span><span class="sxs-lookup"><span data-stu-id="e51cd-117">To complete this tutorial, you need the following tools.</span></span> <span data-ttu-id="e51cd-118">Wenn sie noch nicht vorhanden sind, können Sie sie über diese Links installieren.</span><span class="sxs-lookup"><span data-stu-id="e51cd-118">If you don't already have them you can install them from these links.</span></span>

- [<span data-ttu-id="e51cd-119">Git</span><span class="sxs-lookup"><span data-stu-id="e51cd-119">Git</span></span>](https://git-scm.com/downloads)
- [<span data-ttu-id="e51cd-120">Node.js und NPM</span><span class="sxs-lookup"><span data-stu-id="e51cd-120">Node.js and NPM</span></span>](https://nodejs.org/)
- <span data-ttu-id="e51cd-121">Rufen Sie einen beliebigen Text-Editor oder eine beliebige IDE ab.</span><span class="sxs-lookup"><span data-stu-id="e51cd-121">Get any text editor or IDE.</span></span> <span data-ttu-id="e51cd-122">Sie können [Visual Studio Code](https://code.visualstudio.com/download) kostenlos installieren und verwenden.</span><span class="sxs-lookup"><span data-stu-id="e51cd-122">You can install and use [Visual Studio Code](https://code.visualstudio.com/download) for free.</span></span>

<span data-ttu-id="e51cd-123">Wenn während der Installation Optionen zum Hinzufügen , und zum PFAD angezeigt `git` `node` `npm` `code` werden, wählen Sie die Optionen aus.</span><span class="sxs-lookup"><span data-stu-id="e51cd-123">If you see options to add `git`, `node`, `npm`, and `code` to the PATH during installation, select the options.</span></span> 

<span data-ttu-id="e51cd-124">Stellen Sie sicher, dass die Tools verfügbar sind, indem Sie Folgendes in einem Terminalfenster ausführen:</span><span class="sxs-lookup"><span data-stu-id="e51cd-124">Verify that the tools are available by running the following in a terminal window:</span></span>

> [!NOTE]
> <span data-ttu-id="e51cd-125">Verwenden Sie das Terminalfenster, mit dem Sie auf Ihrer Plattform am besten vertraut sind.</span><span class="sxs-lookup"><span data-stu-id="e51cd-125">Use the terminal window that you are most comfortable with on your platform.</span></span> <span data-ttu-id="e51cd-126">Diese Beispiele verwenden Bash (das in Git enthalten ist), aber diese Skripts werden auf den meisten Plattformen ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="e51cd-126">These examples use Bash (which is included in Git), but these scripts will run on most platforms.</span></span>

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

<span data-ttu-id="e51cd-127">Möglicherweise haben Sie eine andere Version dieser Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="e51cd-127">You may have a different version of these applications.</span></span> <span data-ttu-id="e51cd-128">Dies sollte kein Problem sein, mit Ausnahme von gulp.</span><span class="sxs-lookup"><span data-stu-id="e51cd-128">This should not be a problem, except for gulp.</span></span> <span data-ttu-id="e51cd-129">Für gulp müssen Sie Version 4.0.0 oder höher verwenden.</span><span class="sxs-lookup"><span data-stu-id="e51cd-129">For gulp you'll need to use version 4.0.0 or later.</span></span>

<span data-ttu-id="e51cd-130">Wenn Sie gulp nicht installiert haben (oder die falsche Version installiert haben), führen Sie dies jetzt `npm install gulp` in Ihrem Terminalfenster aus.</span><span class="sxs-lookup"><span data-stu-id="e51cd-130">If you don't have gulp installed (or have the wrong version installed), do so now by running `npm install gulp` in your terminal window.</span></span>

<span data-ttu-id="e51cd-131">Wenn Sie Visual Studio Code installiert haben, können Sie die Installation überprüfen, indem Sie Folgendes ausführen:</span><span class="sxs-lookup"><span data-stu-id="e51cd-131">If you have installed Visual Studio Code, you can verify the installation by running:</span></span>

```bash
code --version
1.28.2
929bacba01ef658b873545e26034d1a8067445e9
```

<span data-ttu-id="e51cd-132">Sie können dieses Terminalfenster weiterhin verwenden, um die befehle auszuführen, die in diesem Lernprogramm folgen.</span><span class="sxs-lookup"><span data-stu-id="e51cd-132">You can continue to use this terminal window to run the commands that follow in this tutorial.</span></span>

<a name="DownloadSample"></a>

## <a name="download-the-sample"></a><span data-ttu-id="e51cd-133">Beispiel herunterladen</span><span class="sxs-lookup"><span data-stu-id="e51cd-133">Download the sample</span></span>

<span data-ttu-id="e51cd-134">Wir haben ein einfaches [Hello, World bereitgestellt!](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-hello-world/nodejs)</span><span class="sxs-lookup"><span data-stu-id="e51cd-134">We have provided a simple [Hello, World!](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-hello-world/nodejs)</span></span> <span data-ttu-id="e51cd-135">Beispiel für die ersten Schritte.</span><span class="sxs-lookup"><span data-stu-id="e51cd-135">sample to get you started.</span></span> <span data-ttu-id="e51cd-136">Führen Sie in einem Terminalfenster den folgenden Befehl aus, um das Beispiel-Repository auf Ihrem lokalen Computer zu klonen:</span><span class="sxs-lookup"><span data-stu-id="e51cd-136">In a terminal window, run the following command to clone the sample repository to your local machine:</span></span>

```bash
git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
```

> [!TIP]
> <span data-ttu-id="e51cd-137">Sie können dieses [Repository verzweigen,](https://github.com/OfficeDev/Microsoft-Teams-Samples) wenn Sie Ihre Änderungen an Ihrem GitHub-Repository für zukünftige Verweise ändern und einchecken möchten. [](https://help.github.com/articles/fork-a-repo/)</span><span class="sxs-lookup"><span data-stu-id="e51cd-137">You can [fork](https://help.github.com/articles/fork-a-repo/) this [repo](https://github.com/OfficeDev/Microsoft-Teams-Samples) if you want to modify and check in your changes to your GitHub repo for future reference.</span></span>

<a name="BuildRun"></a>

## <a name="build-and-run-the-sample"></a><span data-ttu-id="e51cd-138">Erstellen und Ausführen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="e51cd-138">Build and run the sample</span></span>

<span data-ttu-id="e51cd-139">Führen Sie nach dem Klonen des Repositorys den Befehl "Verzeichnis ändern" im Terminal aus, um das Verzeichnis in das Beispiel zu ändern:</span><span class="sxs-lookup"><span data-stu-id="e51cd-139">After the repository is cloned, run the change directory command in terminal to change the directory to the sample:</span></span>

```bash
cd Microsoft-Teams-Samples/samples/app-hello-world/nodejs/
```

<span data-ttu-id="e51cd-140">Zum Erstellen des Beispiels müssen Sie alle Abhängigkeiten installieren.</span><span class="sxs-lookup"><span data-stu-id="e51cd-140">In order to build the sample, you need to install all its dependencies.</span></span> <span data-ttu-id="e51cd-141">Führen Sie dazu den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="e51cd-141">Run the following command to do this:</span></span>

```bash
npm install
```

<span data-ttu-id="e51cd-142">Es sollte eine Reihe von Abhängigkeiten angezeigt werden, die installiert werden.</span><span class="sxs-lookup"><span data-stu-id="e51cd-142">You should see a bunch of dependencies getting installed.</span></span> <span data-ttu-id="e51cd-143">Nach der Installation können Sie die App mit dem folgenden Befehl ausführen:</span><span class="sxs-lookup"><span data-stu-id="e51cd-143">After installation you can run the app with the following command:</span></span>

```bash
npm start
```

<span data-ttu-id="e51cd-144">Wenn die Hello-World-App gestartet wird, wird sie `App started listening on port 3333` im Terminalfenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e51cd-144">When the hello-world app starts, it displays `App started listening on port 3333` in the terminal window.</span></span>

> [!NOTE]
> <span data-ttu-id="e51cd-145">Wenn in der obigen Meldung eine andere Portnummer angezeigt wird, liegt dies daran, dass Sie eine PORT-Umgebungsvariable festgelegt haben.</span><span class="sxs-lookup"><span data-stu-id="e51cd-145">If you see a different port number displayed in the message above, it is because you have a PORT environment variable set.</span></span> <span data-ttu-id="e51cd-146">Sie können diesen Port weiterhin verwenden oder Ihre Umgebungsvariable auf 3333 ändern.</span><span class="sxs-lookup"><span data-stu-id="e51cd-146">You can continue to use that port or change your environment variable to 3333.</span></span>

<span data-ttu-id="e51cd-147">An diesem Punkt können Sie ein Browserfenster öffnen und zu den folgenden URLs navigieren, um zu überprüfen, ob alle App-URLs geladen werden:</span><span class="sxs-lookup"><span data-stu-id="e51cd-147">At this point, you can open a browser window and navigate to the following URLs to verify that all the app URLs are loading:</span></span>

- `http://localhost:3333`
- `http://localhost:3333/hello`
- `http://localhost:3333/first`
- `http://localhost:3333/second`

<a name="HostSample"></a>

## <a name="deploy-your-sample-app"></a><span data-ttu-id="e51cd-148">Bereitstellen Ihrer Beispiel-App</span><span class="sxs-lookup"><span data-stu-id="e51cd-148">Deploy your sample app</span></span>

<span data-ttu-id="e51cd-149">Denken Sie daran, dass Apps in Microsoft Teams Webanwendungen sind, die eine oder mehrere Funktionen verfügbar machen.</span><span class="sxs-lookup"><span data-stu-id="e51cd-149">Remember that apps in Microsoft Teams are web applications exposing one or more capabilities.</span></span> <span data-ttu-id="e51cd-150">Damit die Teams Plattform Ihre App laden kann, muss Ihre App über das Internet erreichbar sein.</span><span class="sxs-lookup"><span data-stu-id="e51cd-150">For the Teams platform to load your app, your app must be reachable from the internet.</span></span> <span data-ttu-id="e51cd-151">Damit Ihre App über das Internet erreichbar ist, müssen Sie ihre App *hosten.*</span><span class="sxs-lookup"><span data-stu-id="e51cd-151">To make your app reachable from the internet, you need to *host* your app.</span></span>

<span data-ttu-id="e51cd-152">Für lokale Tests können Sie die App auf Ihrem lokalen Computer ausführen und einen Tunnel mit einem Webendpunkt erstellen.</span><span class="sxs-lookup"><span data-stu-id="e51cd-152">For local testing you can run the app on your local machine and create a tunnel to it with a web endpoint.</span></span> <span data-ttu-id="e51cd-153">[ngrok](https://ngrok.com) ist ein kostenloses Tool, mit dem Sie genau das tun können.</span><span class="sxs-lookup"><span data-stu-id="e51cd-153">[ngrok](https://ngrok.com) is a free tool that lets you do just that.</span></span> <span data-ttu-id="e51cd-154">Mit *ngrok* können Sie eine Webadresse wie `https://d0ac14a5.ngrok.io` (diese URL ist nur ein Beispiel) abrufen.</span><span class="sxs-lookup"><span data-stu-id="e51cd-154">With *ngrok* you can get a web address such as `https://d0ac14a5.ngrok.io` (this URL is just an example).</span></span> <span data-ttu-id="e51cd-155">Sie können *ngrok* für Ihre Umgebung [herunterladen und installieren.](https://ngrok.com/download)</span><span class="sxs-lookup"><span data-stu-id="e51cd-155">You can [download and install](https://ngrok.com/download) *ngrok* for your environment.</span></span> <span data-ttu-id="e51cd-156">Stellen Sie sicher, dass Sie es einem Speicherort in Ihrer `PATH` hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="e51cd-156">Make sure you add it to a location in your `PATH`.</span></span>

<span data-ttu-id="e51cd-157">Nach der Installation können Sie ein neues Terminalfenster öffnen und den folgenden Befehl ausführen, um einen Tunnel zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="e51cd-157">After you install it, you can open a new terminal window and run the following command to create a tunnel.</span></span> <span data-ttu-id="e51cd-158">Im Beispiel wird Port 3333 verwendet. Achten Sie daher darauf, ihn hier anzugeben:</span><span class="sxs-lookup"><span data-stu-id="e51cd-158">The sample uses port 3333, so be sure to specify it here:</span></span>

```bash
ngrok http 3333 -host-header=localhost:3333
```

<span data-ttu-id="e51cd-159">*Ngrok* lauscht auf Anforderungen aus dem Internet und leitet sie an Ihre App weiter, die an Port 3333 ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="e51cd-159">*Ngrok* will listen to requests from the internet and will route them to your app running on port 3333.</span></span> <span data-ttu-id="e51cd-160">Sie können dies überprüfen, indem Sie Ihren Browser öffnen und `https://d0ac14a5.ngrok.io/hello` die Hello-Seite Ihrer App laden.</span><span class="sxs-lookup"><span data-stu-id="e51cd-160">You can verify by opening your browser and going to `https://d0ac14a5.ngrok.io/hello` to load your app's hello page.</span></span> <span data-ttu-id="e51cd-161">Verwenden Sie unbedingt die Von *ngrok* in Ihrer Konsolensitzung angezeigte Weiterleitungsadresse anstelle dieser URL.</span><span class="sxs-lookup"><span data-stu-id="e51cd-161">Please be sure to use the forwarding address displayed by *ngrok* in your console session instead of this URL.</span></span>

> [!NOTE]
> <span data-ttu-id="e51cd-162">Wenn Sie im [obigen Build](#build-and-run-the-sample) einen anderen Port verwendet und ausgeführt haben, stellen Sie sicher, dass Sie die gleiche Portnummer verwenden, um den *ngrok-Tunnel* einzurichten.</span><span class="sxs-lookup"><span data-stu-id="e51cd-162">If you have used a different port in the [build and run](#build-and-run-the-sample) step above, make sure you use the same port number to setup the *ngrok* tunnel.</span></span>
> [!TIP]
> <span data-ttu-id="e51cd-163">Es empfiehlt sich, *ngrok* in einem anderen Terminalfenster auszuführen, damit es ohne Beeinträchtigung der Knoten-App ausgeführt wird, die Sie später möglicherweise beenden, neu erstellen und erneut ausführen müssen.</span><span class="sxs-lookup"><span data-stu-id="e51cd-163">It is a good idea to run *ngrok* in a different terminal window to keep it running without interfering with the node app which you might later have to stop, rebuild and rerun.</span></span> <span data-ttu-id="e51cd-164">Die *ngrok-Sitzung* gibt nützliche Debuginformationen in diesem Fenster zurück.</span><span class="sxs-lookup"><span data-stu-id="e51cd-164">The *ngrok* session will return useful debugging information in this window.</span></span>

<span data-ttu-id="e51cd-165">Es gibt eine kostenpflichtige Version von *ngrok,* die persistente Namen zulässt.</span><span class="sxs-lookup"><span data-stu-id="e51cd-165">There is a paid version of *ngrok* that allows persistent names.</span></span> <span data-ttu-id="e51cd-166">Wenn Sie die kostenlose Version verwenden, ist Ihre App nur während der aktuellen Sitzung auf Ihrem Entwicklungscomputer verfügbar.</span><span class="sxs-lookup"><span data-stu-id="e51cd-166">If you use the free version your app will only be available during the current session on your development machine.</span></span> <span data-ttu-id="e51cd-167">Wenn der Computer heruntergefahren wird oder in den Ruhezustand wechselt, ist der Dienst nicht mehr verfügbar.</span><span class="sxs-lookup"><span data-stu-id="e51cd-167">If the machine is shut down or goes to sleep the service will no longer be available.</span></span> <span data-ttu-id="e51cd-168">Denken Sie daran, wenn Sie die App für Tests durch andere Benutzer freigeben.</span><span class="sxs-lookup"><span data-stu-id="e51cd-168">Remember this when sharing the app for testing by other users.</span></span> <span data-ttu-id="e51cd-169">Wenn Sie den Dienst neu starten müssen, wird eine neue Adresse zurückgegeben, und Sie müssen jeden Ort aktualisieren, der diese Adresse verwendet.</span><span class="sxs-lookup"><span data-stu-id="e51cd-169">If you have to restart the service it will return a new address and you will have to update every place that uses that address.</span></span>

<span data-ttu-id="e51cd-170">Notieren Sie sich die URL Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="e51cd-170">Make a note of the URL of your app.</span></span> <span data-ttu-id="e51cd-171">Sie benötigen dies später, wenn Sie die App bei Teams über App Studio oder das Entwicklerportal registrieren.</span><span class="sxs-lookup"><span data-stu-id="e51cd-171">You will need this later when you register the app with Teams using App studio or Developer Portal.</span></span>

<a name="DeployToTeams"></a>

## <a name="deploy-your-app-to-microsoft-teams"></a><span data-ttu-id="e51cd-172">Bereitstellen Ihrer App für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="e51cd-172">Deploy your app to Microsoft Teams</span></span>

<span data-ttu-id="e51cd-173">An diesem Punkt wird eine App im Internet gehostet, aber Sie können noch nicht sagen, Teams, wo sie gesucht werden soll oder sogar wie Ihre App heißt.</span><span class="sxs-lookup"><span data-stu-id="e51cd-173">At this point you have an app hosted on the internet, but you have no way yet of telling Teams where to look for it, or even what your app is called.</span></span> <span data-ttu-id="e51cd-174">Dazu müssen Sie jetzt ein App-Paket erstellen.</span><span class="sxs-lookup"><span data-stu-id="e51cd-174">To do this you now have to create an app package.</span></span> <span data-ttu-id="e51cd-175">Dies ist nur eine Textdatei, die das App-Manifest und einige Symbole enthält, die der Teams-Client verwendet, um Ihre App ordnungsgemäß anzuzeigen und zu brandingen.</span><span class="sxs-lookup"><span data-stu-id="e51cd-175">This is little more than a text file that contains the app manifest and some icons that the Teams client will use to properly display and brand your app.</span></span> <span data-ttu-id="e51cd-176">Sie können dieses App-Paket manuell erstellen oder App Studio oder das Entwicklerportal verwenden, Tools, die in Teams ausgeführt werden, wodurch die Registrierung der App vereinfacht wird.</span><span class="sxs-lookup"><span data-stu-id="e51cd-176">You can manually create this app package, or you can use App Studio or Developer Portal, tools that run in Teams, that will simplify the process of registering the app.</span></span> <span data-ttu-id="e51cd-177">App Studio und das Entwicklerportal sind die empfohlenen Methoden zum Erstellen und Aktualisieren des App-Pakets.</span><span class="sxs-lookup"><span data-stu-id="e51cd-177">App Studio and Developer Portal are the recommended ways of creating and updating the app package.</span></span>

<span data-ttu-id="e51cd-178">Für beide Methoden benötigen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="e51cd-178">For either method you will need the following:</span></span>

- <span data-ttu-id="e51cd-179">Die URL, unter der Ihre App im Internet zu finden ist.</span><span class="sxs-lookup"><span data-stu-id="e51cd-179">The URL where your app can be found on the internet.</span></span>
- <span data-ttu-id="e51cd-180">Symbole, die Teams zum Branding Ihrer App verwenden.</span><span class="sxs-lookup"><span data-stu-id="e51cd-180">Icons that Teams will use to brand your app.</span></span> <span data-ttu-id="e51cd-181">Das Beispiel enthält Platzhaltersymbole in "src\static\images".</span><span class="sxs-lookup"><span data-stu-id="e51cd-181">The sample comes with placeholder icons located in "src\static\images.</span></span> <span data-ttu-id="e51cd-182">App Studio stellt bei Bedarf auch Standardsymbole bereit.</span><span class="sxs-lookup"><span data-stu-id="e51cd-182">App Studio also will provide default icons if needed.</span></span>

<span data-ttu-id="e51cd-183">**Aktualisieren des App-Pakets**</span><span class="sxs-lookup"><span data-stu-id="e51cd-183">**Update the app package**</span></span>

# <a name="app-studio"></a>[<span data-ttu-id="e51cd-184">App-Studio</span><span class="sxs-lookup"><span data-stu-id="e51cd-184">App Studio</span></span>](#tab/AS)

[!include [Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

# <a name="developer-portal"></a>[<span data-ttu-id="e51cd-185">Entwicklerportal</span><span class="sxs-lookup"><span data-stu-id="e51cd-185">Developer Portal</span></span>](#tab/DP)

<span data-ttu-id="e51cd-186">**So installieren Sie das Entwicklerportal (Vorschau) in Teams**</span><span class="sxs-lookup"><span data-stu-id="e51cd-186">**To install Developer Portal (preview) in Teams**</span></span>

1. <span data-ttu-id="e51cd-187">Wählen Sie unten in der linken Leiste das Symbol **"Apps"** aus, und suchen Sie nach **dem Entwicklerportal.**</span><span class="sxs-lookup"><span data-stu-id="e51cd-187">Select the **Apps** icon at the bottom of the left-hand bar, and search for **Developer Portal**.</span></span>

    <img width="430px" alt="Screenshot of TDP" src="~/assets/images/Screen1.png"/>

1. <span data-ttu-id="e51cd-188">Wählen Sie **"Entwicklerportal"** aus, und wählen Sie **"Öffnen"** aus.</span><span class="sxs-lookup"><span data-stu-id="e51cd-188">Select **Developer Portal** and select **Open**.</span></span>

    <img width="430px" alt="Screenshot of TDP Open" src="~/assets/images/screen2.png"/>

1. <span data-ttu-id="e51cd-189">Wählen Sie die Registerkarte "Apps" aus, und wählen Sie **"Vorhandene App importieren"** aus.</span><span class="sxs-lookup"><span data-stu-id="e51cd-189">Select the Apps tab and select **Import an existing app**.</span></span>

    <img width="430px" alt="Screenshot of import app in tdp" src="~/assets/images/screen3.png"/>

1. <span data-ttu-id="e51cd-190">Wählen Sie **"Hello World"** aus, und wählen Sie **"Importieren"** aus.</span><span class="sxs-lookup"><span data-stu-id="e51cd-190">Select **Hello World** and select **Import**.</span></span> <span data-ttu-id="e51cd-191">Die **Hello World-App** wird im Entwicklerportal importiert.</span><span class="sxs-lookup"><span data-stu-id="e51cd-191">The **Hello World** app is imported in Developer Portal.</span></span> 

    <span data-ttu-id="e51cd-192">Sie können Ihre App über das Teams Entwicklerportal konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="e51cd-192">You can configure your app using the Teams Developer Portal.</span></span> <span data-ttu-id="e51cd-193">Das Manifest befindet sich unter "Verteilen".</span><span class="sxs-lookup"><span data-stu-id="e51cd-193">The Manifest is found under Distribute.</span></span> <span data-ttu-id="e51cd-194">Sie können das Manifest verwenden, um Funktionen, erforderliche Ressourcen und andere wichtige Attribute für Ihre App zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="e51cd-194">You can use the Manifest to configure capabilities, required resources, and other important attributes for your app.</span></span> <span data-ttu-id="e51cd-195">Weitere Informationen zum Konfigurieren Ihrer App mithilfe des Entwicklerportals finden Sie unter [Teams Developer Portal.](../concepts/build-and-test/teams-developer-portal.md)</span><span class="sxs-lookup"><span data-stu-id="e51cd-195">For more details on how to configure your app using Developer Portal, see [Teams Developer Portal](../concepts/build-and-test/teams-developer-portal.md).</span></span>

    <img width="430px" alt="Screenshot of configure tdp" src="~/assets/images/Screen4.png"/>

---
<a name="updatecredentials"></a>

## <a name="update-the-credentials-for-your-hosted-app"></a><span data-ttu-id="e51cd-196">Aktualisieren der Anmeldeinformationen für Ihre gehostete App</span><span class="sxs-lookup"><span data-stu-id="e51cd-196">Update the credentials for your hosted app</span></span>

<span data-ttu-id="e51cd-197">Für die Beispiel-App müssen die folgenden Umgebungsvariablen auf die Werte festgelegt werden, die Sie zuvor notieren:</span><span class="sxs-lookup"><span data-stu-id="e51cd-197">The sample app requires the following environment variables to be set to the values you made a note of earlier:</span></span>

```
MICROSOFT_APP_ID=<YOUR BOT'S APP ID>
MICROSOFT_APP_PASSWORD=<YOUR BOT'S PASSWORD>
WEBSITE_NODE_DEFAULT_VERSION=8.9.4
```

<span data-ttu-id="e51cd-198">Wie Sie dies tun, hängt davon ab, wie Sie Ihre App gehostet haben.</span><span class="sxs-lookup"><span data-stu-id="e51cd-198">How you do that differs depending on how you hosted your app.</span></span> <span data-ttu-id="e51cd-199">Wichtig bei der Verwendung von Umgebungsvariablen ist, dass diese Werte Teil Ihrer Umgebung sind. Sie können über den Code für Ihre App aufgerufen werden, werden jedoch nicht für Dritte verfügbar gemacht, die möglicherweise die Dateien untersuchen, aus denen Ihre Website besteht.</span><span class="sxs-lookup"><span data-stu-id="e51cd-199">The important thing about using environment variables is that these values are part of your environment - they can be accessed by the code for your app, but they are not exposed to third parties who might examine the files that make up your site.</span></span>

<span data-ttu-id="e51cd-200">Wenn Sie die App mit ngrok ausführen, müssen Sie einige lokale Umgebungsvariablen einrichten.</span><span class="sxs-lookup"><span data-stu-id="e51cd-200">If you are running the app using ngrok you'll need to set up some local environment variables.</span></span> <span data-ttu-id="e51cd-201">Es gibt viele Möglichkeiten, dies zu tun. Wenn Sie jedoch Visual Studio Code verwenden, besteht die einfachste Möglichkeit darin, eine [Startkonfiguration](https://code.visualstudio.com/Docs/editor/debugging#_launch-configurations)hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="e51cd-201">There are many ways to do this, but the easiest, if you are using Visual Studio Code, is to add a [launch configuration](https://code.visualstudio.com/Docs/editor/debugging#_launch-configurations):</span></span>

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

<span data-ttu-id="e51cd-202">Dabei gilt Folgendes:</span><span class="sxs-lookup"><span data-stu-id="e51cd-202">Where:</span></span>

<span data-ttu-id="e51cd-203">MICROSOFT_APP_ID und MICROSOFT_APP_PASSWORD ist die ID bzw. das Kennwort für Ihren Bot.</span><span class="sxs-lookup"><span data-stu-id="e51cd-203">MICROSOFT_APP_ID and MICROSOFT_APP_PASSWORD is the ID and password, respectively, for your bot.</span></span>
<span data-ttu-id="e51cd-204">NODE_DEBUG zeigen Ihnen, was in Ihrem Bot in der Visual Studio Code Debugkonsole passiert.</span><span class="sxs-lookup"><span data-stu-id="e51cd-204">NODE_DEBUG will show you what's happening in your bot in the Visual Studio Code debug console.</span></span>
<span data-ttu-id="e51cd-205">NODE_CONFIG_DIR verweist auf das Verzeichnis im Stammverzeichnis des Repositorys (wenn die App lokal ausgeführt wird, wird sie standardmäßig im Ordner "src" gesucht).</span><span class="sxs-lookup"><span data-stu-id="e51cd-205">NODE_CONFIG_DIR points to the directory at the root of the repository (by default, when the app is run locally, it looks for it in the src folder).</span></span>

> [!Note]
> <span data-ttu-id="e51cd-206">Wenn Sie npm noch nicht von früheren Versionen des Lernprogramms beendet haben, müssen Sie diese ausführen, `npm stop` damit Visual Studio Code die Startkonfigurationsvariablen korrekt abrufen können.</span><span class="sxs-lookup"><span data-stu-id="e51cd-206">If you have not stopped npm from earlier in the tutorial, you'll need to run `npm stop` in order for Visual Studio Code to pickup your launch configuration variables correctly.</span></span>

<a name="ConfigureTheAppTab"></a>

## <a name="configure-the-app-tab"></a><span data-ttu-id="e51cd-207">Konfigurieren der Registerkarte "App"</span><span class="sxs-lookup"><span data-stu-id="e51cd-207">Configure the app tab</span></span>

<span data-ttu-id="e51cd-208">Nachdem Sie die App in einem Team installiert haben, müssen Sie sie so konfigurieren, dass Inhalte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="e51cd-208">After you install the app into a team, you will need to configure it to show content.</span></span> <span data-ttu-id="e51cd-209">Wechseln Sie zu einem Kanal im Team, und klicken Sie auf die Schaltfläche **"+",** um eine neue Registerkarte hinzuzufügen. Sie können dann `Hello World` aus der **Registerkartenliste hinzufügen** auswählen.</span><span class="sxs-lookup"><span data-stu-id="e51cd-209">Go to a channel in the team and click on the **'+'** button to add a new tab. You can then choose `Hello World` from the **Add a tab** list.</span></span> <span data-ttu-id="e51cd-210">Anschließend wird ihnen ein Konfigurationsdialogfeld angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e51cd-210">You will then be presented with a configuration dialog.</span></span> <span data-ttu-id="e51cd-211">In diesem Dialogfeld können Sie auswählen, welche Registerkarte in diesem Kanal angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="e51cd-211">This dialog will let you choose which tab to display in this channel.</span></span> <span data-ttu-id="e51cd-212">Nachdem Sie die Registerkarte ausgewählt und auf **"Speichern"** geklickt haben, wird die `Hello World` Registerkarte angezeigt, die mit der ausgewählten Registerkarte geladen wurde:</span><span class="sxs-lookup"><span data-stu-id="e51cd-212">After you select the tab and click **Save** you can see the `Hello World` tab loaded with the tab you chose:</span></span>

<img width="430px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png"/>

### <a name="test-your-bot-in-teams"></a><span data-ttu-id="e51cd-213">Testen Ihres Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="e51cd-213">Test your bot in Teams</span></span>

<span data-ttu-id="e51cd-214">Sie können jetzt mit dem Bot in Teams interagieren.</span><span class="sxs-lookup"><span data-stu-id="e51cd-214">You can now interact with the bot in Teams.</span></span> <span data-ttu-id="e51cd-215">Wählen Sie einen Kanal im Team aus, in dem Sie Ihre App registriert haben, und geben Sie `@your-bot-name` dann Ihre Nachricht ein.</span><span class="sxs-lookup"><span data-stu-id="e51cd-215">Choose a channel in the team where you registered your app, and type `@your-bot-name`, followed by your message.</span></span> <span data-ttu-id="e51cd-216">Dies wird als **\@ Erwähnung bezeichnet.**</span><span class="sxs-lookup"><span data-stu-id="e51cd-216">This is called an **\@mention**.</span></span> <span data-ttu-id="e51cd-217">Jede Nachricht, die Sie an den Bot senden, wird als Antwort an Sie gesendet:</span><span class="sxs-lookup"><span data-stu-id="e51cd-217">Whatever message you send to the bot will be sent back to you as a reply:</span></span>

<img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png"/>

<a name="ComposeRichMessages"></a>

### <a name="test-your-messaging-extension"></a><span data-ttu-id="e51cd-218">Testen Der Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="e51cd-218">Test your messaging extension</span></span>

<span data-ttu-id="e51cd-219">**So testen Sie Ihre Messaging-Erweiterung**</span><span class="sxs-lookup"><span data-stu-id="e51cd-219">**To test your messaging extension**</span></span>
1. <span data-ttu-id="e51cd-220">Wählen Sie die drei Punkte unterhalb des Eingabefelds in der Unterhaltungsansicht aus.</span><span class="sxs-lookup"><span data-stu-id="e51cd-220">Select the three dots below the input box in your conversation view.</span></span> <span data-ttu-id="e51cd-221">Ein Menü mit der **App "Hello World"** wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e51cd-221">A menu with the **'Hello World'** app is displayed.</span></span>
1. <span data-ttu-id="e51cd-222">Wählen Sie das Menü aus.</span><span class="sxs-lookup"><span data-stu-id="e51cd-222">Select the menu.</span></span> <span data-ttu-id="e51cd-223">Es wird eine Reihe zufälliger Texte angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e51cd-223">A set of random texts is displayed.</span></span> <span data-ttu-id="e51cd-224">Sie können einen beliebigen Text auswählen, der in Ihre Unterhaltung eingefügt wird.</span><span class="sxs-lookup"><span data-stu-id="e51cd-224">You can select one of the random text and that is inserted into your conversation.</span></span>

    <img width="430px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu1.png" />

    <img width="430px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result1.png" />

1. <span data-ttu-id="e51cd-225">Wählen Sie einen der zufälligen Texte aus, und unten sehen Sie eine Karte, die formatiert und zum Senden mit Ihrer eigenen Nachricht bereit ist:</span><span class="sxs-lookup"><span data-stu-id="e51cd-225">Select one of the random texts, and you will see a card formatted and ready to send with your own message at the bottom:</span></span>

    <img width="430px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />

 ## <a name="see-also"></a><span data-ttu-id="e51cd-226">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="e51cd-226">See also</span></span>

* [<span data-ttu-id="e51cd-227">Übersicht über Lernprogramme</span><span class="sxs-lookup"><span data-stu-id="e51cd-227">Tutorials Overview</span></span>](code-samples.md)
* [<span data-ttu-id="e51cd-228">Erstellen einer Unterhaltungs-Bot-App</span><span class="sxs-lookup"><span data-stu-id="e51cd-228">Create a conversational bot app</span></span>](first-app-bot.md)
* [<span data-ttu-id="e51cd-229">Erstellen einer Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="e51cd-229">Create a messaging extension</span></span>](first-message-extension.md)
* [<span data-ttu-id="e51cd-230">Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="e51cd-230">Code Samples</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples)