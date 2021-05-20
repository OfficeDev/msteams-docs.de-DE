---
title: Tutorial - Erstellen Sie Ihre erste App mit Node.js
description: Erfahren Sie, wie Sie mit dem Erstellen Microsoft Teams Apps mit Node.js beginnen.
keywords: Erste Schritte node.js nodejs App Studio
ms.topic: tutorial
localization_priority: Normal
ms.custom: scenarios:getting-started; languages:JavaScript,Node.js
ms.openlocfilehash: 46272671443e07432513b667af424b5c5be05f2e
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566540"
---
# <a name="create-your-first-microsoft-teams-app-using-nodejs"></a><span data-ttu-id="8b4de-104">Erstellen Sie Ihre erste Microsoft Teams-App mit Node.js</span><span class="sxs-lookup"><span data-stu-id="8b4de-104">Create your first Microsoft Teams app using Node.js</span></span>

<span data-ttu-id="8b4de-105">In diesem Tutorial können Sie mit dem Erstellen einer Microsoft Teams-App mit Node.js beginnen.</span><span class="sxs-lookup"><span data-stu-id="8b4de-105">This tutorial helps you get started creating a Microsoft Teams app using Node.js.</span></span>

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="DownloadAndHost"></a>

## <a name="download-and-host-your-app"></a><span data-ttu-id="8b4de-106">Herunterladen und Hosten Ihrer App</span><span class="sxs-lookup"><span data-stu-id="8b4de-106">Download and host your app</span></span>

<span data-ttu-id="8b4de-107">Führen Sie die folgenden Schritte aus, um eine einfache "Hallo-Welt"-App in Teams herunterzuladen und zu hosten.</span><span class="sxs-lookup"><span data-stu-id="8b4de-107">Follow these steps to download and host a simple "hello world" app in Teams.</span></span>

<a name="GetPrerequisites"></a>

### <a name="get-prerequisites"></a><span data-ttu-id="8b4de-108">Voraussetzungen abrufen</span><span class="sxs-lookup"><span data-stu-id="8b4de-108">Get prerequisites</span></span>

<span data-ttu-id="8b4de-109">Um dieses Tutorial abzuschließen, benötigen Sie die folgenden Tools.</span><span class="sxs-lookup"><span data-stu-id="8b4de-109">To complete this tutorial, you need the following tools.</span></span> <span data-ttu-id="8b4de-110">Wenn Sie sie noch nicht haben, können Sie sie über diese Links installieren.</span><span class="sxs-lookup"><span data-stu-id="8b4de-110">If you don't already have them you can install them from these links.</span></span>

- [<span data-ttu-id="8b4de-111">Git</span><span class="sxs-lookup"><span data-stu-id="8b4de-111">Git</span></span>](https://git-scm.com/downloads)
- [<span data-ttu-id="8b4de-112">Node.js und NPM</span><span class="sxs-lookup"><span data-stu-id="8b4de-112">Node.js and NPM</span></span>](https://nodejs.org/)
- <span data-ttu-id="8b4de-113">Holen Sie sich einen beliebigen Texteditor oder eine IDE.</span><span class="sxs-lookup"><span data-stu-id="8b4de-113">Get any text editor or IDE.</span></span> <span data-ttu-id="8b4de-114">Sie können [Visual Studio Code](https://code.visualstudio.com/download) kostenlos installieren und verwenden.</span><span class="sxs-lookup"><span data-stu-id="8b4de-114">You can install and use [Visual Studio Code](https://code.visualstudio.com/download) for free.</span></span>

<span data-ttu-id="8b4de-115">Wenn Während der Installation Optionen zum Hinzufügen von , , und zum PATH angezeigt werden, wählen Sie dies `git` `node` `npm` `code` aus.</span><span class="sxs-lookup"><span data-stu-id="8b4de-115">If you see options to add `git`, `node`, `npm`, and `code` to the PATH during installation, choose to do so.</span></span> <span data-ttu-id="8b4de-116">Es wird praktisch sein.</span><span class="sxs-lookup"><span data-stu-id="8b4de-116">It will be handy.</span></span>

<span data-ttu-id="8b4de-117">Stellen Sie sicher, dass die Tools verfügbar sind, indem Sie folgendes in einem Terminalfenster ausführen:</span><span class="sxs-lookup"><span data-stu-id="8b4de-117">Verify that the tools are available by running the following in a terminal window:</span></span>

> [!NOTE]
> <span data-ttu-id="8b4de-118">Verwenden Sie das Terminalfenster, mit dem Sie sich auf Ihrer Plattform am wohlsten fühlen.</span><span class="sxs-lookup"><span data-stu-id="8b4de-118">Use the terminal window that you are most comfortable with on your platform.</span></span> <span data-ttu-id="8b4de-119">Diese Beispiele verwenden Bash (das in Git enthalten ist), aber diese Skripte werden auf den meisten Plattformen ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="8b4de-119">These examples use Bash (which is included in Git), but these scripts will run on most platforms.</span></span>

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

<span data-ttu-id="8b4de-120">Möglicherweise verfügen Sie über eine andere Version dieser Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="8b4de-120">You may have a different version of these applications.</span></span> <span data-ttu-id="8b4de-121">Dies sollte kein Problem sein, außer gulp.</span><span class="sxs-lookup"><span data-stu-id="8b4de-121">This should not be a problem, except for gulp.</span></span> <span data-ttu-id="8b4de-122">Für gulp müssen Sie Version 4.0.0 oder höher verwenden.</span><span class="sxs-lookup"><span data-stu-id="8b4de-122">For gulp you'll need to use version 4.0.0 or later.</span></span>

<span data-ttu-id="8b4de-123">Wenn Sie gulp nicht installiert haben (oder die falsche Version installiert haben), führen Sie dies jetzt `npm install gulp` in Ihrem Terminalfenster aus.</span><span class="sxs-lookup"><span data-stu-id="8b4de-123">If you don't have gulp installed (or have the wrong version installed), do so now by running `npm install gulp` in your terminal window.</span></span>

<span data-ttu-id="8b4de-124">Wenn Sie Visual Studio Code installiert haben, können Sie die Installation überprüfen, indem Sie:</span><span class="sxs-lookup"><span data-stu-id="8b4de-124">If you have installed Visual Studio Code, you can verify the installation by running:</span></span>

```bash
code --version
1.28.2
929bacba01ef658b873545e26034d1a8067445e9
```

<span data-ttu-id="8b4de-125">Sie können dieses Terminalfenster weiterhin verwenden, um die folgenden Befehle in diesem Tutorial auszuführen.</span><span class="sxs-lookup"><span data-stu-id="8b4de-125">You can continue to use this terminal window to run the commands that follow in this tutorial.</span></span>

<a name="DownloadSample"></a>

### <a name="download-the-sample"></a><span data-ttu-id="8b4de-126">Laden Sie das Beispiel herunter</span><span class="sxs-lookup"><span data-stu-id="8b4de-126">Download the sample</span></span>

<span data-ttu-id="8b4de-127">Wir haben ein einfaches [Hallo, Welt](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-hello-world/nodejs) zur Verfügung gestellt!</span><span class="sxs-lookup"><span data-stu-id="8b4de-127">We have provided a simple [Hello, World!](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-hello-world/nodejs)</span></span> <span data-ttu-id="8b4de-128">Beispiel, um Ihnen den Einstieg zu erleichtern.</span><span class="sxs-lookup"><span data-stu-id="8b4de-128">sample to get you started.</span></span> <span data-ttu-id="8b4de-129">Führen Sie in einem Terminalfenster den folgenden Befehl aus, um das Beispiel-Repository auf Ihren lokalen Computer zu klonen:</span><span class="sxs-lookup"><span data-stu-id="8b4de-129">In a terminal window, run the following command to clone the sample repository to your local machine:</span></span>

```bash
git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
```

> [!TIP]
> <span data-ttu-id="8b4de-130">Sie können dieses [Repository](https://github.com/OfficeDev/Microsoft-Teams-Samples) [verkleben,](https://help.github.com/articles/fork-a-repo/) wenn Sie Ihre Änderungen an Ihrem GitHub Repository für zukünftige Referenzen ändern und einchecken möchten.</span><span class="sxs-lookup"><span data-stu-id="8b4de-130">You can [fork](https://help.github.com/articles/fork-a-repo/) this [repo](https://github.com/OfficeDev/Microsoft-Teams-Samples) if you want to modify and check in your changes to your GitHub repo for future reference.</span></span>

<a name="BuildRun"></a>

### <a name="build-and-run-the-sample"></a><span data-ttu-id="8b4de-131">Erstellen und Ausführen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="8b4de-131">Build and run the sample</span></span>

<span data-ttu-id="8b4de-132">Nachdem das Repository geklont wurde, wechseln Sie in das Verzeichnis, in dem sich das Beispiel befindet:</span><span class="sxs-lookup"><span data-stu-id="8b4de-132">Once the repo is cloned, change to the directory that holds the sample:</span></span>

```bash
cd Microsoft-Teams-Samples/samples/app-hello-world/nodejs/
```

<span data-ttu-id="8b4de-133">Um das Beispiel zu erstellen, müssen Sie alle abhängigkeiten installieren.</span><span class="sxs-lookup"><span data-stu-id="8b4de-133">In order to build the sample, you need to install all its dependencies.</span></span> <span data-ttu-id="8b4de-134">Führen Sie dazu den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="8b4de-134">Run the following command to do this:</span></span>

```bash
npm install
```

<span data-ttu-id="8b4de-135">Es sollte angezeigt werden, dass eine Reihe von Abhängigkeiten installiert werden.</span><span class="sxs-lookup"><span data-stu-id="8b4de-135">You should see a bunch of dependencies getting installed.</span></span> <span data-ttu-id="8b4de-136">Sobald sie fertig sind, können Sie die App ausführen:</span><span class="sxs-lookup"><span data-stu-id="8b4de-136">Once they are finished, you can run the app:</span></span>

```bash
npm start
```

<span data-ttu-id="8b4de-137">Wenn die hello-world-App gestartet wird, wird sie `App started listening on port 3333` im Terminalfenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8b4de-137">When the hello-world app starts, it displays `App started listening on port 3333` in the terminal window.</span></span>

> [!NOTE]
> <span data-ttu-id="8b4de-138">Wenn in der obigen Meldung eine andere Portnummer angezeigt wird, liegt dies daran, dass sie eine PORT-Umgebungsvariable festgelegt haben.</span><span class="sxs-lookup"><span data-stu-id="8b4de-138">If you see a different port number displayed in the message above, it is because you have a PORT environment variable set.</span></span> <span data-ttu-id="8b4de-139">Sie können diesen Port weiterhin verwenden oder Ihre Umgebungsvariable in 3333 ändern.</span><span class="sxs-lookup"><span data-stu-id="8b4de-139">You can continue to use that port or change your environment variable to 3333.</span></span>

<span data-ttu-id="8b4de-140">An dieser Stelle können Sie ein Browserfenster öffnen und zu den folgenden URLs navigieren, um zu überprüfen, ob alle App-URLs geladen werden:</span><span class="sxs-lookup"><span data-stu-id="8b4de-140">At this point, you can open a browser window and navigate to the following URLs to verify that all the app URLs are loading:</span></span>

- `http://localhost:3333`
- `http://localhost:3333/hello`
- `http://localhost:3333/first`
- `http://localhost:3333/second`

<a name="HostSample"></a>

### <a name="host-the-sample-app"></a><span data-ttu-id="8b4de-141">Hosten der Beispiel-App</span><span class="sxs-lookup"><span data-stu-id="8b4de-141">Host the sample app</span></span>

<span data-ttu-id="8b4de-142">Denken Sie daran, dass Apps in Microsoft Teams Webanwendungen sind, die eine oder mehrere Funktionen verfügbar machen.</span><span class="sxs-lookup"><span data-stu-id="8b4de-142">Remember that apps in Microsoft Teams are web applications exposing one or more capabilities.</span></span> <span data-ttu-id="8b4de-143">Damit die Teams Plattform Ihre App lädt, muss Ihre App über das Internet erreichbar sein.</span><span class="sxs-lookup"><span data-stu-id="8b4de-143">For the Teams platform to load your app, your app must be reachable from the internet.</span></span> <span data-ttu-id="8b4de-144">Damit Ihre App über das Internet erreichbar ist, müssen Sie Ihre App *hosten.*</span><span class="sxs-lookup"><span data-stu-id="8b4de-144">To make your app reachable from the internet, you need to *host* your app.</span></span>

<span data-ttu-id="8b4de-145">Für lokale Tests können Sie die App auf Ihrem lokalen Computer ausführen und einen Tunnel zu diesem Mitmachen mit einem Webendpunkt erstellen.</span><span class="sxs-lookup"><span data-stu-id="8b4de-145">For local testing you can run the app on your local machine and create a tunnel to it with a web endpoint.</span></span> <span data-ttu-id="8b4de-146">[ngrok](https://ngrok.com) ist ein kostenloses Tool, mit dem Sie genau das tun können.</span><span class="sxs-lookup"><span data-stu-id="8b4de-146">[ngrok](https://ngrok.com) is a free tool that lets you do just that.</span></span> <span data-ttu-id="8b4de-147">Mit *ngrok* können Sie eine Webadresse wie `https://d0ac14a5.ngrok.io` (diese URL ist nur ein Beispiel) erhalten.</span><span class="sxs-lookup"><span data-stu-id="8b4de-147">With *ngrok* you can get a web address such as `https://d0ac14a5.ngrok.io` (this URL is just an example).</span></span> <span data-ttu-id="8b4de-148">Sie können *ngrok* für Ihre Umgebung [herunterladen und installieren.](https://ngrok.com/download)</span><span class="sxs-lookup"><span data-stu-id="8b4de-148">You can [download and install](https://ngrok.com/download) *ngrok* for your environment.</span></span> <span data-ttu-id="8b4de-149">Stellen Sie sicher, dass Sie es an einem Speicherort in Ihrem `PATH` hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="8b4de-149">Make sure you add it to a location in your `PATH`.</span></span>

<span data-ttu-id="8b4de-150">Nachdem Sie es installiert haben, können Sie ein neues Terminalfenster öffnen und den folgenden Befehl ausführen, um einen Tunnel zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="8b4de-150">Once you install it, you can open a new terminal window and run the following command to create a tunnel.</span></span> <span data-ttu-id="8b4de-151">Das Beispiel verwendet Port 3333, also stellen Sie sicher, dass Sie ihn hier angeben:</span><span class="sxs-lookup"><span data-stu-id="8b4de-151">The sample uses port 3333, so be sure to specify it here:</span></span>

```bash
ngrok http 3333 -host-header=localhost:3333
```

<span data-ttu-id="8b4de-152">*Ngrok* hört Anfragen aus dem Internet ab und leitet sie an Ihre App weiter, die auf Port 3333 ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="8b4de-152">*Ngrok* will listen to requests from the internet and will route them to your app running on port 3333.</span></span> <span data-ttu-id="8b4de-153">Sie können dies überprüfen, indem Sie Ihren Browser öffnen und die `https://d0ac14a5.ngrok.io/hello` Hallo-Seite Ihrer App laden.</span><span class="sxs-lookup"><span data-stu-id="8b4de-153">You can verify by opening your browser and going to `https://d0ac14a5.ngrok.io/hello` to load your app's hello page.</span></span> <span data-ttu-id="8b4de-154">Bitte verwenden Sie die Weiterleitungsadresse, die von *ngrok* in Ihrer Konsolensitzung anstelle dieser URL angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8b4de-154">Please be sure to use the forwarding address displayed by *ngrok* in your console session instead of this URL.</span></span>

> [!NOTE]
> <span data-ttu-id="8b4de-155">Wenn Sie einen anderen Port im Build verwendet haben und schritt oben [ausgeführt](#build-and-run-the-sample) werden, stellen Sie sicher, dass Sie dieselbe Portnummer verwenden, um den *ngrok-Tunnel* einzurichten.</span><span class="sxs-lookup"><span data-stu-id="8b4de-155">If you have used a different port in the [build and run](#build-and-run-the-sample) step above, make sure you use the same port number to setup the *ngrok* tunnel.</span></span>
> [!TIP]
> <span data-ttu-id="8b4de-156">Es ist eine gute Idee, *ngrok* in einem anderen Terminalfenster auszuführen, um es laufen zu lassen, ohne die Knoten-App zu stören, die Sie später möglicherweise anhalten, neu erstellen und erneut ausführen müssen.</span><span class="sxs-lookup"><span data-stu-id="8b4de-156">It is a good idea to run *ngrok* in a different terminal window to keep it running without interfering with the node app which you might later have to stop, rebuild and rerun.</span></span> <span data-ttu-id="8b4de-157">Die *ngrok-Sitzung* gibt in diesem Fenster nützliche Debuginformationen zurück.</span><span class="sxs-lookup"><span data-stu-id="8b4de-157">The *ngrok* session will return useful debugging information in this window.</span></span>

<span data-ttu-id="8b4de-158">Es gibt eine kostenpflichtige Version von *ngrok,* die persistente Namen zulässt.</span><span class="sxs-lookup"><span data-stu-id="8b4de-158">There is a paid version of *ngrok* that allows persistent names.</span></span> <span data-ttu-id="8b4de-159">Wenn Sie die kostenlose Version verwenden, ist Ihre App nur während der aktuellen Sitzung auf Ihrem Entwicklungscomputer verfügbar.</span><span class="sxs-lookup"><span data-stu-id="8b4de-159">If you use the free version your app will only be available during the current session on your development machine.</span></span> <span data-ttu-id="8b4de-160">Wenn die Maschine heruntergefahren wird oder in den Ruhezustand geht, ist der Dienst nicht mehr verfügbar.</span><span class="sxs-lookup"><span data-stu-id="8b4de-160">If the machine is shut down or goes to sleep the service will no longer be available.</span></span> <span data-ttu-id="8b4de-161">Denken Sie daran, wenn Sie die App zum Testen durch andere Benutzer freigeben.</span><span class="sxs-lookup"><span data-stu-id="8b4de-161">Remember this when sharing the app for testing by other users.</span></span> <span data-ttu-id="8b4de-162">Wenn Sie den Dienst neu starten müssen, wird eine neue Adresse zurückgegeben, und Sie müssen jeden Ort aktualisieren, der diese Adresse verwendet.</span><span class="sxs-lookup"><span data-stu-id="8b4de-162">If you have to restart the service it will return a new address and you will have to update every place that uses that address.</span></span>

<span data-ttu-id="8b4de-163">Denken Sie daran, notieren Sie sich die URL Ihrer App, da Sie dies später benötigen, wenn Sie die App mit Teams app studio registrieren.</span><span class="sxs-lookup"><span data-stu-id="8b4de-163">Remember, make a note of the URL of your app because you will need this later when you register the app with Teams using App studio.</span></span> <span data-ttu-id="8b4de-164">Editor funktioniert dafür gut.</span><span class="sxs-lookup"><span data-stu-id="8b4de-164">Notepad works fine for this purpose.</span></span>

<a name="DeployToTeams"></a>

## <a name="deploy-your-app-to-microsoft-teams"></a><span data-ttu-id="8b4de-165">Stellen Sie Ihre App zum Microsoft Teams bereit</span><span class="sxs-lookup"><span data-stu-id="8b4de-165">Deploy your app to Microsoft Teams</span></span>

<span data-ttu-id="8b4de-166">Zu diesem Zeitpunkt haben Sie eine App im Internet gehostet, aber Sie haben noch keine Möglichkeit, Teams zu sagen, wo sie zu suchen, oder sogar, was Ihre App genannt wird.</span><span class="sxs-lookup"><span data-stu-id="8b4de-166">At this point you have an app hosted on the internet, but you have no way yet of telling Teams where to look for it, or even what your app is called.</span></span> <span data-ttu-id="8b4de-167">Dazu müssen Sie nun ein App-Paket erstellen.</span><span class="sxs-lookup"><span data-stu-id="8b4de-167">To do this you now have to create an app package.</span></span> <span data-ttu-id="8b4de-168">Dies ist nicht viel mehr als eine Textdatei, die das App-Manifest und einige Symbole enthält, die der Teams-Client verwendet, um Ihre App ordnungsgemäß anzuzeigen und zu brandmarken.</span><span class="sxs-lookup"><span data-stu-id="8b4de-168">This is little more than a text file that contains the app manifest and some icons that the Teams client will use to properly display and brand your app.</span></span> <span data-ttu-id="8b4de-169">Sie können dieses App-Paket manuell erstellen oder App Studio verwenden, ein Tool, das in Teams ausgeführt wird, das den Prozess der Registrierung der App vereinfacht.</span><span class="sxs-lookup"><span data-stu-id="8b4de-169">You can manually create this app package, or you can use App Studio, a tool that runs in Teams that will simplify the process of registering the app.</span></span> <span data-ttu-id="8b4de-170">App Studio ist die empfohlene Methode zum Erstellen und Aktualisieren des App-Pakets.</span><span class="sxs-lookup"><span data-stu-id="8b4de-170">App Studio is the recommended way of creating and updating the app package.</span></span>

<span data-ttu-id="8b4de-171">Für eine der beiden Methoden benötigen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="8b4de-171">For either method you will need the following:</span></span>

- <span data-ttu-id="8b4de-172">Die URL, unter der Sich Ihre App im Internet befindet.</span><span class="sxs-lookup"><span data-stu-id="8b4de-172">The URL where your app can be found on the internet.</span></span>
- <span data-ttu-id="8b4de-173">Symbole, die Teams verwenden, um Ihre App zu brandmarken.</span><span class="sxs-lookup"><span data-stu-id="8b4de-173">Icons that Teams will use to brand your app.</span></span> <span data-ttu-id="8b4de-174">Das Beispiel enthält Platzhaltersymbole, die sich in "src-static-images" befinden.</span><span class="sxs-lookup"><span data-stu-id="8b4de-174">The sample comes with placeholder icons located in "src\static\images.</span></span> <span data-ttu-id="8b4de-175">App Studio stellt bei Bedarf auch Standardsymbole bereit.</span><span class="sxs-lookup"><span data-stu-id="8b4de-175">App Studio also will provide default icons if needed.</span></span>

[!include[Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

## <a name="update-your-hosted-app"></a><span data-ttu-id="8b4de-176">Aktualisieren Ihrer gehosteten App</span><span class="sxs-lookup"><span data-stu-id="8b4de-176">Update your hosted app</span></span>

<span data-ttu-id="8b4de-177">Für die Beispiel-App müssen die folgenden Umgebungsvariablen auf die Werte festgelegt werden, die Sie zuvor notieren:</span><span class="sxs-lookup"><span data-stu-id="8b4de-177">The sample app requires the following environment variables to be set to the values you made a note of earlier:</span></span>

```
MICROSOFT_APP_ID=<YOUR BOT'S APP ID>
MICROSOFT_APP_PASSWORD=<YOUR BOT'S PASSWORD>
WEBSITE_NODE_DEFAULT_VERSION=8.9.4
```

<span data-ttu-id="8b4de-178">Wie Sie dies tun, hängt davon ab, wie Sie Ihre App gehostet haben.</span><span class="sxs-lookup"><span data-stu-id="8b4de-178">How you do that differs depending on how you hosted your app.</span></span> <span data-ttu-id="8b4de-179">Das Wichtige an der Verwendung von Umgebungsvariablen ist, dass diese Werte Teil Ihrer Umgebung sind - sie können durch den Code für Ihre App zugegriffen werden, aber sie sind nicht für Dritte verfügbar, die die Dateien untersuchen könnten, aus denen Ihre Website besteht.</span><span class="sxs-lookup"><span data-stu-id="8b4de-179">The important thing about using environment variables is that these values are part of your environment - they can be accessed by the code for your app, but they are not exposed to third parties who might examine the files that make up your site.</span></span>

<span data-ttu-id="8b4de-180">Wenn Sie die App mit ngrok ausführen, müssen Sie einige lokale Umgebungsvariablen einrichten.</span><span class="sxs-lookup"><span data-stu-id="8b4de-180">If you are running the app using ngrok you'll need to set up some local environment variables.</span></span> <span data-ttu-id="8b4de-181">Es gibt viele Möglichkeiten, dies zu tun, aber die einfachste, wenn Sie Visual Studio Code verwenden, ist es, eine [Startkonfiguration](https://code.visualstudio.com/Docs/editor/debugging#_launch-configurations)hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="8b4de-181">There are many ways to do this, but the easiest, if you are using Visual Studio Code, is to add a [launch configuration](https://code.visualstudio.com/Docs/editor/debugging#_launch-configurations):</span></span>

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

<span data-ttu-id="8b4de-182">Dabei gilt:</span><span class="sxs-lookup"><span data-stu-id="8b4de-182">Where:</span></span>

<span data-ttu-id="8b4de-183">MICROSOFT_APP_ID und MICROSOFT_APP_PASSWORD ist die ID bzw. das Passwort für Ihren Bot.</span><span class="sxs-lookup"><span data-stu-id="8b4de-183">MICROSOFT_APP_ID and MICROSOFT_APP_PASSWORD is the ID and password, respectively, for your bot.</span></span>
<span data-ttu-id="8b4de-184">NODE_DEBUG zeigt Ihnen, was in Ihrem Bot in der Visual Studio Code-Debug-Konsole passiert.</span><span class="sxs-lookup"><span data-stu-id="8b4de-184">NODE_DEBUG will show you what's happening in your bot in the Visual Studio Code debug console.</span></span>
<span data-ttu-id="8b4de-185">NODE_CONFIG_DIR zeigt auf das Verzeichnis im Stammverzeichnis des Repositorys (standardmäßig sucht die App, wenn sie lokal ausgeführt wird, im Ordner src nach).</span><span class="sxs-lookup"><span data-stu-id="8b4de-185">NODE_CONFIG_DIR points to the directory at the root of the repository (by default, when the app is run locally, it looks for it in the src folder).</span></span>

> [!Note]
> <span data-ttu-id="8b4de-186">Wenn Sie npm nicht von früher im Tutorial gestoppt haben, müssen Sie ausführen, `npm stop` damit Visual Studio Code Ihre Startkonfigurationsvariablen korrekt abrufen können.</span><span class="sxs-lookup"><span data-stu-id="8b4de-186">If you have not stopped npm from earlier in the tutorial, you'll need to run `npm stop` in order for Visual Studio Code to pickup your launch configuration variables correctly.</span></span>

<a name="ConfigureTheAppTab"></a>

## <a name="configure-the-app-tab"></a><span data-ttu-id="8b4de-187">Konfigurieren der App-Registerkarte</span><span class="sxs-lookup"><span data-stu-id="8b4de-187">Configure the app tab</span></span>

<span data-ttu-id="8b4de-188">Nachdem Sie die App in einem Team installiert haben, müssen Sie sie so konfigurieren, dass Inhalte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="8b4de-188">Once you install the app into a team, you will need to configure it to show content.</span></span> <span data-ttu-id="8b4de-189">Gehen Sie zu einem Kanal im Team und klicken Sie auf die Schaltfläche **"+",** um eine neue Registerkarte hinzuzufügen. Sie können dann `Hello World` aus der Liste Registerkarte **hinzufügen** auswählen.</span><span class="sxs-lookup"><span data-stu-id="8b4de-189">Go to a channel in the team and click on the **'+'** button to add a new tab. You can then choose `Hello World` from the **Add a tab** list.</span></span> <span data-ttu-id="8b4de-190">Anschließend wird Ihnen ein Konfigurationsdialog angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8b4de-190">You will then be presented with a configuration dialog.</span></span> <span data-ttu-id="8b4de-191">In diesem Dialogfeld können Sie auswählen, welche Registerkarte in diesem Kanal angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="8b4de-191">This dialog will let you choose which tab to display in this channel.</span></span> <span data-ttu-id="8b4de-192">Sobald Sie die Registerkarte ausgewählt und klicken Sie auf `Save` Sie können die Registerkarte mit der Registerkarte geladen sehen Sie `Hello World` gewählt:</span><span class="sxs-lookup"><span data-stu-id="8b4de-192">Once you select the tab and click on `Save` you can see the `Hello World` tab loaded with the tab you chose:</span></span>

<img width="430px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png"/>

### <a name="test-your-bot-in-teams"></a><span data-ttu-id="8b4de-193">Testen Sie Ihren Bot in Teams</span><span class="sxs-lookup"><span data-stu-id="8b4de-193">Test your bot in Teams</span></span>

<span data-ttu-id="8b4de-194">Sie können jetzt mit dem Bot in Teams interagieren.</span><span class="sxs-lookup"><span data-stu-id="8b4de-194">You can now interact with the bot in Teams.</span></span> <span data-ttu-id="8b4de-195">Wählen Sie einen Kanal im Team aus, in dem Sie Ihre App registriert haben, und geben Sie `@your-bot-name` ein, gefolgt von Ihrer Nachricht.</span><span class="sxs-lookup"><span data-stu-id="8b4de-195">Choose a channel in the team where you registered your app, and type `@your-bot-name`, followed by your message.</span></span> <span data-ttu-id="8b4de-196">Dies wird als **\@ Erwähnung** bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="8b4de-196">This is called an **\@mention**.</span></span> <span data-ttu-id="8b4de-197">Welche Nachricht Sie an den Bot senden, wird Ihnen als Antwort zurückgesendet:</span><span class="sxs-lookup"><span data-stu-id="8b4de-197">Whatever message you send to the bot will be sent back to you as a reply:</span></span>

<img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png"/>

<a name="ComposeRichMessages"></a>

### <a name="test-your-messaging-extension"></a><span data-ttu-id="8b4de-198">Testen Sie Ihre Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="8b4de-198">Test your messaging extension</span></span>

<span data-ttu-id="8b4de-199">Um Ihre Messaging-Erweiterung zu testen, können Sie auf die drei Punkte unter dem Eingabefeld in Ihrer Unterhaltungsansicht klicken.</span><span class="sxs-lookup"><span data-stu-id="8b4de-199">To test your messaging extension, you can click on the three dots below the input box in your conversation view.</span></span> <span data-ttu-id="8b4de-200">Ein Menü erscheint mit der **"Hello World"-App.**</span><span class="sxs-lookup"><span data-stu-id="8b4de-200">A menu will pop up with the **'Hello World'** app in it.</span></span> <span data-ttu-id="8b4de-201">Wenn Sie darauf klicken, sehen Sie eine Reihe von zufälligen Texten.</span><span class="sxs-lookup"><span data-stu-id="8b4de-201">When you click it, you will see a number of random texts.</span></span> <span data-ttu-id="8b4de-202">Sie können einen von ihnen auswählen und es wird in Ihre Unterhaltung eingefügt:</span><span class="sxs-lookup"><span data-stu-id="8b4de-202">You can choose any one of them and it will be inserted it into your conversation:</span></span>

<img width="430px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu.png" />

<img width="430px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result.png" />

<span data-ttu-id="8b4de-203">Wählen Sie einen der zufälligen Texte, und Sie sehen eine Karte formatiert und bereit, mit Ihrer eigenen Nachricht am unteren Rand zu senden:</span><span class="sxs-lookup"><span data-stu-id="8b4de-203">Choose one of the random texts, and you will see a card formatted and ready to send with your own message at the bottom:</span></span>

<img width="430px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />
