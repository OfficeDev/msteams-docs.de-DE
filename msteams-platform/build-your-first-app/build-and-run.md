---
title: Erstellen und Ausführen eines "Hello, World!" Teams-App
author: heath-hamilton
description: Erstellen Sie die erste Microsoft Teams-APP, und führen Sie Sie aus, eine persönliche Registerkarte, auf der "Hello, World!" angezeigt wird.
ms.author: lajanuar
ms.date: 09/22/2020
ms.topic: quickstart
ms.openlocfilehash: 244a899670f71b9446c8c3d3e404c9fd7c7b510c
ms.sourcegitcommit: f9a2f5cedc9d30ef7a9cf78a47d01cfd277e150d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "48237832"
---
# <a name="build-a-hello-world-teams-app"></a><span data-ttu-id="63d30-104">Erstellen Sie ein "Hello, World!"</span><span class="sxs-lookup"><span data-stu-id="63d30-104">Build a "Hello, World!"</span></span> <span data-ttu-id="63d30-105">Teams-App</span><span class="sxs-lookup"><span data-stu-id="63d30-105">Teams app</span></span>

<span data-ttu-id="63d30-106">Sie können direkt in die Microsoft Teams-Plattformentwicklung wechseln, indem Sie eine persönliche RegisterkarteErstellen, in der "Hello, World!" angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="63d30-106">You can jump right into Microsoft Teams platform development by building a personal tab that displays "Hello, World!"</span></span>

## <a name="1-create-your-app-project"></a><span data-ttu-id="63d30-107">1. Erstellen des App-Projekts</span><span class="sxs-lookup"><span data-stu-id="63d30-107">1. Create your app project</span></span>

<span data-ttu-id="63d30-108">Verwenden Sie das Microsoft Teams-Toolkit in Visual Studio Code, um Ihr erstes App-Projekt einzurichten.</span><span class="sxs-lookup"><span data-stu-id="63d30-108">Use the Microsoft Teams Toolkit in Visual Studio Code to set up your first app project.</span></span>

1. Wählen Sie in Visual Studio Code **Microsoft Teams** in :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: der linken Aktivitäts Leiste aus, und wählen Sie **neue Teams-app erstellen**aus.
:::image type="content" source="../assets/images/build-your-first-app/create-teams-app.png" alt-text="Screenshot, der zeigt, wie Sie eine neue APP mit dem Visual Studio Code Teams-Toolkit erstellen.":::
1. <span data-ttu-id="63d30-111">Geben Sie einen Namen für Ihre Teams-App ein.</span><span class="sxs-lookup"><span data-stu-id="63d30-111">Enter a name for your Teams app.</span></span> <span data-ttu-id="63d30-112">(Dies ist der Standardname für Ihre APP und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.)</span><span class="sxs-lookup"><span data-stu-id="63d30-112">(This is the default name for your app and also the name of the app project directory on your local machine.)</span></span>
1. <span data-ttu-id="63d30-113">Wählen Sie auf dem Bildschirm **Funktionen hinzufügen** die Option **Tab** und dann dann **weiter**aus.</span><span class="sxs-lookup"><span data-stu-id="63d30-113">On the **Add capabilities** screen, select **Tab** then **Next**.</span></span>
:::image type="content" source="../assets/images/build-your-first-app/choose-tab.png" alt-text="Screenshot, in dem gezeigt wird, wie Ihr App-Projekt mit dem Visual Studio Code Teams-Toolkit konfiguriert wird.":::
1. <span data-ttu-id="63d30-115">Aktivieren Sie die Option **persönliche Registerkarte** , und klicken Sie unten auf dem Bildschirm auf **Fertig stellen** , um Ihr Projekt zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="63d30-115">Check the **Personal tab** option and select **Finish** at the bottom of the screen to configure your project.</span></span>

## <a name="2-understand-important-app-project-components"></a><span data-ttu-id="63d30-116">2. Grundlegendes zu wichtigen App-Projektkomponenten</span><span class="sxs-lookup"><span data-stu-id="63d30-116">2. Understand important app project components</span></span>

<span data-ttu-id="63d30-117">Nachdem das Toolkit Ihr Projekt konfiguriert hat, müssen Sie die Komponenten zum Erstellen einer einfachen persönlichen Registerkarte für Teams.</span><span class="sxs-lookup"><span data-stu-id="63d30-117">Once the toolkit configures your project, you have the components to build a basic personal tab for Teams.</span></span> <span data-ttu-id="63d30-118">Die Projektverzeichnisse und-Dateien werden im Bereich "Explorer" von Visual Studio Code angezeigt.</span><span class="sxs-lookup"><span data-stu-id="63d30-118">The project directories and files display in the Explorer area of Visual Studio Code.</span></span>

:::image type="content" source="../assets/images/build-your-first-app/app-project-files.png" alt-text="Screenshot, in dem App-Projektdateien für eine persönliche Registerkarte in Visual Studio Code angezeigt werden.":::

<span data-ttu-id="63d30-120">Lassen Sie uns einen Moment Zeit nehmen, um einige der wichtigsten Dateien zu verstehen, mit denen Microsoft Teams-App-Entwickler arbeiten.</span><span class="sxs-lookup"><span data-stu-id="63d30-120">Let's take a moment to understand some of the key files Teams app developers work with.</span></span>

### <a name="app-manifest-manifestjson"></a><span data-ttu-id="63d30-121">App-Manifest ( `manifest.json` )</span><span class="sxs-lookup"><span data-stu-id="63d30-121">App manifest (`manifest.json`)</span></span>

<span data-ttu-id="63d30-122">Im Verzeichnis befindet `.publish` sich das App-Manifest als Ausgangspunkt für ein beliebiges App-Projekt.</span><span class="sxs-lookup"><span data-stu-id="63d30-122">Located in the `.publish` directory, the app manifest is the starting point for any app project.</span></span> <span data-ttu-id="63d30-123">Das Manifest definiert die grundlegenden Attribute Ihrer APP und verweist auf erforderliche Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="63d30-123">The manifest defines your app's fundamental attributes and points to required resources.</span></span> <span data-ttu-id="63d30-124">Wenn Sie eine App installieren, analysiert Microsoft Teams das Manifest, um zu verstehen, wie Ihre APP auf dem Client gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="63d30-124">When you install an app, Teams parses the manifest to understand how to render your app in the client.</span></span>

### <a name="app-scaffolding"></a><span data-ttu-id="63d30-125">App-Gerüste</span><span class="sxs-lookup"><span data-stu-id="63d30-125">App scaffolding</span></span>

<span data-ttu-id="63d30-126">Das Toolkit erstellt automatisch ein Gerüst für Sie im `src` Verzeichnis basierend auf den Funktionen, die Sie während der Installation hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="63d30-126">The toolkit automatically creates scaffolding for you in the `src` directory based on the capabilities you added during setup.</span></span>

<span data-ttu-id="63d30-127">Wenn Sie beispielsweise während des Setups eine RegisterkarteErstellen, `App.js` ist die Datei im `src/components` Verzeichnis wichtig, da Sie die Initialisierung und das Routing Ihrer APP übernimmt.</span><span class="sxs-lookup"><span data-stu-id="63d30-127">If you create a tab during setup, for example, the `App.js` file in the `src/components` directory is important because it handles the initialization and routing of your app.</span></span> <span data-ttu-id="63d30-128">Das [Microsoft Teams SDK](../tabs/how-to/using-teams-client-sdk.md) wird aufgerufen, um die Kommunikation zwischen Ihrer APP und ihren Teams herzustellen.</span><span class="sxs-lookup"><span data-stu-id="63d30-128">It calls the [Microsoft Teams SDK](../tabs/how-to/using-teams-client-sdk.md) to establish communication between your app and Teams.</span></span>

### <a name="app-package-developmentzip"></a><span data-ttu-id="63d30-129">App-Paket ( `Development.zip` )</span><span class="sxs-lookup"><span data-stu-id="63d30-129">App package (`Development.zip`)</span></span>

<span data-ttu-id="63d30-130">Im Verzeichnis befindet `.publish` , benötigen Sie das App-Paket, um [Ihre APP](../concepts/deploy-and-publish/overview.md#upload-your-app-directly) in Microsoft Teams querladen.</span><span class="sxs-lookup"><span data-stu-id="63d30-130">Located in the `.publish` directory, you need the app package to [sideload your app](../concepts/deploy-and-publish/overview.md#upload-your-app-directly) in Teams.</span></span> <span data-ttu-id="63d30-131">Das Paket wird auch verwendet, wenn im [App-Katalog oder AppSource Ihrer Organisation veröffentlicht](../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) wird. [AppSource](../concepts/deploy-and-publish/appsource/publish.md)</span><span class="sxs-lookup"><span data-stu-id="63d30-131">The package is also used when [publishing to your organization's app catalog](../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) or [AppSource](../concepts/deploy-and-publish/appsource/publish.md).</span></span>

<span data-ttu-id="63d30-132">Hier finden Sie einige Details zu den App-Paketdateien:</span><span class="sxs-lookup"><span data-stu-id="63d30-132">Here are some details about the app package files:</span></span>

|<span data-ttu-id="63d30-133">Name</span><span class="sxs-lookup"><span data-stu-id="63d30-133">Name</span></span>|<span data-ttu-id="63d30-134">Typ</span><span class="sxs-lookup"><span data-stu-id="63d30-134">Type</span></span>|<span data-ttu-id="63d30-135">Größe</span><span class="sxs-lookup"><span data-stu-id="63d30-135">Size</span></span>|<span data-ttu-id="63d30-136">Speicherort des Manifests</span><span class="sxs-lookup"><span data-stu-id="63d30-136">Manifest location</span></span>|<span data-ttu-id="63d30-137">Toolkit-Dateiname</span><span class="sxs-lookup"><span data-stu-id="63d30-137">Toolkit filename</span></span>|
|---|---|:---:|:---:|-----|
|<span data-ttu-id="63d30-138">**App-Manifest**</span><span class="sxs-lookup"><span data-stu-id="63d30-138">**App manifest**</span></span>|`.json`| <span data-ttu-id="63d30-139">—</span><span class="sxs-lookup"><span data-stu-id="63d30-139">—</span></span> | <span data-ttu-id="63d30-140">—</span><span class="sxs-lookup"><span data-stu-id="63d30-140">—</span></span> |`.publish/manifest.json`|
|<span data-ttu-id="63d30-141">**Farb Logo**</span><span class="sxs-lookup"><span data-stu-id="63d30-141">**Color logo**</span></span>|`.png`|<span data-ttu-id="63d30-142">192 &times; 192 Pixel</span><span class="sxs-lookup"><span data-stu-id="63d30-142">192&times;192 pixels</span></span>|`icon.color`|`.publish/color.png`|
|<span data-ttu-id="63d30-143">**Gliederungs Logo**</span><span class="sxs-lookup"><span data-stu-id="63d30-143">**Outline logo**</span></span>|`.png`|<span data-ttu-id="63d30-144">32 &times; 32 Pixel</span><span class="sxs-lookup"><span data-stu-id="63d30-144">32&times;32 pixels</span></span>|`icon.outline`|`.publish/outline.png`|

## <a name="3-run-your-app"></a><span data-ttu-id="63d30-145">3. führen Sie Ihre APP aus.</span><span class="sxs-lookup"><span data-stu-id="63d30-145">3. Run your app</span></span>

<span data-ttu-id="63d30-146">Im Interesse der Zeit erstellen und führen Sie Ihre APP lokal aus.</span><span class="sxs-lookup"><span data-stu-id="63d30-146">In the interest of time, you'll build and run your app locally.</span></span>

<span data-ttu-id="63d30-147">(Diese Informationen sind auch im Toolkit verfügbar `README` .)</span><span class="sxs-lookup"><span data-stu-id="63d30-147">(This information is also available in the toolkit `README`.)</span></span>

1. <span data-ttu-id="63d30-148">Wechseln Sie in einem Terminal zum Stammverzeichnis des App-Projekts, und führen Sie es aus `npm install` .</span><span class="sxs-lookup"><span data-stu-id="63d30-148">In a terminal, go to the root directory of your app project and run `npm install`.</span></span>
1. <span data-ttu-id="63d30-149">Ausführen `npm start` .</span><span class="sxs-lookup"><span data-stu-id="63d30-149">Run `npm start`.</span></span> <span data-ttu-id="63d30-150">Nach Abschluss des Vorgangs wird ein **erfolgreiches kompiliert!**</span><span class="sxs-lookup"><span data-stu-id="63d30-150">Once complete, there's a **Compiled successfully!**</span></span> <span data-ttu-id="63d30-151">Nachricht im Terminal.</span><span class="sxs-lookup"><span data-stu-id="63d30-151">message in the terminal.</span></span>
1. <span data-ttu-id="63d30-152">Öffnen Sie einen Browser, und wechseln Sie zu `https://localhost:3000` , um eine leere Webseite mit dem Namen **Microsoft Teams-Registerkarte**anzuzeigen. (Keine Sorge, dass auf der Seite kein Inhalt angezeigt wird.)</span><span class="sxs-lookup"><span data-stu-id="63d30-152">Open a browser and go to `https://localhost:3000` to view a blank webpage called **Microsoft Teams Tab**. (Don't worry that you can't see any content on the page.)</span></span><br/>
   :::image type="content" source="../assets/images/build-your-first-app/local-host-tab.png" alt-text="Screenshot, der zeigt, wie die laufende app in einem Browser angezeigt wird.":::

## <a name="4-set-up-a-secure-tunnel-to-your-app"></a><span data-ttu-id="63d30-154">4. Einrichten eines sicheren Tunnels für Ihre APP</span><span class="sxs-lookup"><span data-stu-id="63d30-154">4. Set up a secure tunnel to your app</span></span>

<span data-ttu-id="63d30-155">Ihre APP ist auf Ihrem lokalen Webserver aktiv.</span><span class="sxs-lookup"><span data-stu-id="63d30-155">Your app is up and running on your local web server.</span></span> <span data-ttu-id="63d30-156">Wenn Sie Ihre APP in Microsoft Teams ausführen möchten, müssen Sie den `localhost` Zugriff über HTTPS vornehmen.</span><span class="sxs-lookup"><span data-stu-id="63d30-156">To run your app in Teams, you must make your `localhost` accessible through HTTPS.</span></span>

<span data-ttu-id="63d30-157">Installieren Sie [ngrok](https://ngrok.com/download) , falls noch nicht geschehen.</span><span class="sxs-lookup"><span data-stu-id="63d30-157">Install [ngrok](https://ngrok.com/download) if you haven't already.</span></span> <span data-ttu-id="63d30-158">Wenn Sie dieses Tool ausführen, erstellen Sie zwei global verfügbare URLs, die auf Ihren lokalen Webserver ( `http://localhost:3000` ) deuten.</span><span class="sxs-lookup"><span data-stu-id="63d30-158">When you run this tool, you create two globally available URLs that point to your local web server (`http://localhost:3000`).</span></span> <span data-ttu-id="63d30-159">Sie benötigen die Weiterleitungs-URL, die mit beginnt `HTTPS` .</span><span class="sxs-lookup"><span data-stu-id="63d30-159">You need the forwarding URL that begins with `HTTPS`.</span></span>

1. <span data-ttu-id="63d30-160">Öffnen Sie ein neues Terminal, und führen Sie es aus `ngrok http 3000` .</span><span class="sxs-lookup"><span data-stu-id="63d30-160">Open a new terminal and run `ngrok http 3000`.</span></span>
1. <span data-ttu-id="63d30-161">Kopieren Sie die von Ihnen angegebene HTTPS-URL (siehe das folgende Beispiel).</span><span class="sxs-lookup"><span data-stu-id="63d30-161">Copy the HTTPS URL you're provided (see the following example).</span></span>
:::image type="content" source="../assets/images/build-your-first-app/ngrok-running.png" alt-text="Screenshot, in dem ein Terminal mit ngrok-Ausführung angezeigt wird.":::
1. <span data-ttu-id="63d30-163">Öffnen Sie in Ihrem `.publish` Verzeichnis `Development.env` .</span><span class="sxs-lookup"><span data-stu-id="63d30-163">In your `.publish` directory, open `Development.env`.</span></span>
1. <span data-ttu-id="63d30-164">Ersetzen Sie den `baseUrl0` Wert durch die kopierte URL.</span><span class="sxs-lookup"><span data-stu-id="63d30-164">Replace the `baseUrl0` value with the copied URL.</span></span> <span data-ttu-id="63d30-165">(Ändern Sie beispielsweise `baseUrl0=http://localhost:3000` in `baseUrl0=https://85528b2b3ba5.ngrok.io` .)</span><span class="sxs-lookup"><span data-stu-id="63d30-165">(For example, change `baseUrl0=http://localhost:3000` to `baseUrl0=https://85528b2b3ba5.ngrok.io`.)</span></span>

<span data-ttu-id="63d30-166">Das App-Manifest zeigt jetzt auf die Stelle, an der Sie die APP hosten.</span><span class="sxs-lookup"><span data-stu-id="63d30-166">Your app manifest now points to where you're hosting the app.</span></span>

## <a name="5-sideload-your-app-in-teams"></a><span data-ttu-id="63d30-167">5. querladen ihrer app in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="63d30-167">5. Sideload your app in Teams</span></span>

<span data-ttu-id="63d30-168">Wenn Ihre APP über HTTPS läuft und darauf zugegriffen werden kann, sind Sie bereit, Sie in Microsoft Teams hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="63d30-168">With your app running and accessible via HTTPS, you're ready to upload it to Teams.</span></span>

> [!TIP]
> <span data-ttu-id="63d30-169">Überprüfen Sie vor dem Sideloading Ihrer APP auf Probleme, die die [Validierungsfunktion des Toolkits](../concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#teams-app-validation-tool)verwenden.</span><span class="sxs-lookup"><span data-stu-id="63d30-169">Before sideloading your app, check for issues using the [toolkit's validation feature](../concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#teams-app-validation-tool).</span></span> <span data-ttu-id="63d30-170">Fehler müssen behoben sein, damit die APP erfolgreich querladen.</span><span class="sxs-lookup"><span data-stu-id="63d30-170">Errors must be fixed to successfully sideload the app.</span></span>

1. <span data-ttu-id="63d30-171">Melden Sie sich mit Ihrem Konto beim Microsoft Teams-Client an, das App-Sideloading zulässt.</span><span class="sxs-lookup"><span data-stu-id="63d30-171">Log in to the Teams client with your account that allows app sideloading.</span></span> <span data-ttu-id="63d30-172">(Wenn Sie nicht sicher sind, dass dies der Fall ist, erfahren Sie mehr über das [Einrichten eines Teams-entwicklungskontos](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account).)</span><span class="sxs-lookup"><span data-stu-id="63d30-172">(If you aren't sure you have that, learn about getting a [Teams development account](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account).)</span></span>
1. <span data-ttu-id="63d30-173">Wählen Sie **apps**aus, und wählen Sie dann **benutzerdefinierte App hochladen**aus.</span><span class="sxs-lookup"><span data-stu-id="63d30-173">Select **Apps**, then choose **Upload a custom app**.</span></span>
1. <span data-ttu-id="63d30-174">Wechseln Sie zu Ihrem APP `.publish` -Projektordner, und wählen Sie aus `Development.zip` .</span><span class="sxs-lookup"><span data-stu-id="63d30-174">Go to your app project `.publish` folder and select `Development.zip`.</span></span> <span data-ttu-id="63d30-175">Eine modale Installation wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="63d30-175">An installation modal displays.</span></span>
:::image type="content" source="../assets/images/build-your-first-app/add-teams-app.png" alt-text="Screenshot mit einem Beispiel für eine Microsoft Teams-App-Installation modal.":::
1. <span data-ttu-id="63d30-177">Wählen Sie **Hinzufügen** aus, um Ihre APP zu installieren.</span><span class="sxs-lookup"><span data-stu-id="63d30-177">Select **Add** to install your app.</span></span>
:::image type="content" source="../assets/images/build-your-first-app/tab-running.png" alt-text="Screenshot mit einem Beispiel für die persönliche Tab-app "Hello, World!", die in Microsoft Teams läuft.":::

<span data-ttu-id="63d30-179">🎉 Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="63d30-179">🎉 Congratulations!</span></span> <span data-ttu-id="63d30-180">Ihre APP wird in Microsoft Teams gestartet.</span><span class="sxs-lookup"><span data-stu-id="63d30-180">Your app is running in Teams.</span></span>

## <a name="next-step"></a><span data-ttu-id="63d30-181">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="63d30-181">Next step</span></span>

<span data-ttu-id="63d30-182">Erweitern Sie auf der persönlichen Registerkarte, die Sie gerade erstellt haben, oder erstellen Sie eine andere Art von Teams-app.</span><span class="sxs-lookup"><span data-stu-id="63d30-182">Expand on the personal tab you just created or build another type of Teams app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="63d30-183">Zu Ihrer persönlichen Registerkarte hinzufügen</span><span class="sxs-lookup"><span data-stu-id="63d30-183">Add to your personal tab</span></span>](../build-your-first-app/build-personal-tab.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="63d30-184">Erstellen einer Kanal Registerkarte</span><span class="sxs-lookup"><span data-stu-id="63d30-184">Build a channel tab</span></span>](../build-your-first-app/build-channel-tab.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="63d30-185">Erstellen eines bot</span><span class="sxs-lookup"><span data-stu-id="63d30-185">Build a bot</span></span>](../build-your-first-app/build-bot.md)
