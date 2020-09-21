---
title: Erstellen und Ausführen der App "First Teams"
author: heath-hamilton
ms.author: lajanuar
description: Führen Sie Ihre erste Microsoft Teams-App aus.
ms.date: 08/31/2020
ms.topic: quickstart
ms.openlocfilehash: 441b70480d9c177e9c6140342df8c9ea29494a29
ms.sourcegitcommit: d3bb4bbcdff9545c9869647dcdbe563a2db868be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/18/2020
ms.locfileid: "47964692"
---
# <a name="build-and-run-your-first-microsoft-teams-app"></a><span data-ttu-id="a1e83-103">Erstellen und Ausführen ihrer ersten Microsoft Teams-App</span><span class="sxs-lookup"><span data-stu-id="a1e83-103">Build and run your first Microsoft Teams app</span></span>

<span data-ttu-id="a1e83-104">Sie können direkt in die Entwicklung auf der Microsoft Teams-Plattform wechseln, indem Sie schnell eine einfache persönliche RegisterkarteErstellen und durchführen.</span><span class="sxs-lookup"><span data-stu-id="a1e83-104">You can jump right into developing on the Microsoft Teams platform by quickly building and running a basic personal tab.</span></span>

## <a name="create-your-app-project"></a><span data-ttu-id="a1e83-105">Erstellen eines App-Projekts</span><span class="sxs-lookup"><span data-stu-id="a1e83-105">Create your app project</span></span>

<span data-ttu-id="a1e83-106">Verwenden Sie das Microsoft Teams-Toolkit in Visual Studio Code, um Ihr erstes App-Projekt einzurichten.</span><span class="sxs-lookup"><span data-stu-id="a1e83-106">Use the Microsoft Teams Toolkit in Visual Studio Code to set up your first app project.</span></span>

1. Wählen Sie in Visual Studio Code **Microsoft Teams** in :::image type="icon" source="../doc-links/images/vsc-toolkit.png"::: der linken Aktivitäts Leiste aus, und wählen Sie **neue Teams-app erstellen**aus.
:::image type="content" source="../doc-links/images/create-teams-app.png" alt-text="Erstellen eines Teams-App-Images":::
1. <span data-ttu-id="a1e83-109">Geben Sie einen Namen für Ihre Teams-App ein.</span><span class="sxs-lookup"><span data-stu-id="a1e83-109">Enter a name for your Teams app.</span></span> <span data-ttu-id="a1e83-110">(Dies ist der Standardname für Ihre APP und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.)</span><span class="sxs-lookup"><span data-stu-id="a1e83-110">(This is the default name for your app and also the name of the app project directory on your local machine.)</span></span>
1. <span data-ttu-id="a1e83-111">Wählen Sie auf dem Bildschirm **Funktionen hinzufügen** die Option **Tab** und dann dann **weiter**aus.</span><span class="sxs-lookup"><span data-stu-id="a1e83-111">On the **Add capabilities** screen, select **Tab** then **Next**.</span></span>
:::image type="content" source="../doc-links/images/choose-tab.png" alt-text="Ansicht "Teams-App-Bild erstellen"":::
1. <span data-ttu-id="a1e83-113">Aktivieren Sie die Option **persönliche Registerkarte** , und klicken Sie unten auf dem Bildschirm auf **Fertig stellen** , um Ihr Projekt zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="a1e83-113">Check the **Personal tab** option and select **Finish** at the bottom of the screen to configure your project.</span></span>

## <a name="understand-important-app-project-components"></a><span data-ttu-id="a1e83-114">Grundlegendes zu wichtigen App-Projektkomponenten</span><span class="sxs-lookup"><span data-stu-id="a1e83-114">Understand important app project components</span></span>

<span data-ttu-id="a1e83-115">Nachdem das Toolkit Ihr Projekt konfiguriert hat, müssen Sie die Komponenten zum Erstellen einer einfachen persönlichen Registerkarte für Teams.</span><span class="sxs-lookup"><span data-stu-id="a1e83-115">Once the toolkit configures your project, you have the components to build a basic personal tab for Teams.</span></span> <span data-ttu-id="a1e83-116">Die Projektverzeichnisse und-Dateien werden im Bereich "Explorer" von Visual Studio Code angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a1e83-116">The project directories and files display in the Explorer area of Visual Studio Code.</span></span>

:::image type="content" source="../doc-links/images/app-project-files.png" alt-text="App-Projektdateien in Visual Studio Code.":::

<span data-ttu-id="a1e83-118">Lassen Sie uns einige der wichtigsten Dateien kennen, mit denen Microsoft Teams-App-Entwickler arbeiten.</span><span class="sxs-lookup"><span data-stu-id="a1e83-118">Let's take time to understand some of the key files Teams app developers work with.</span></span>

### <a name="app-manifest-manifestjson"></a><span data-ttu-id="a1e83-119">App-Manifest ( `manifest.json` )</span><span class="sxs-lookup"><span data-stu-id="a1e83-119">App manifest (`manifest.json`)</span></span>

<span data-ttu-id="a1e83-120">Im Verzeichnis befindet `.publish` sich das App-Manifest als Ausgangspunkt für ein beliebiges App-Projekt.</span><span class="sxs-lookup"><span data-stu-id="a1e83-120">Located in the `.publish` directory, the app manifest is the starting point for any app project.</span></span> <span data-ttu-id="a1e83-121">Das Manifest definiert die grundlegenden Attribute Ihrer APP und verweist auf erforderliche Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="a1e83-121">The manifest defines your app's fundamental attributes and points to required resources.</span></span> <span data-ttu-id="a1e83-122">Wenn Sie eine App installieren, analysiert Microsoft Teams das Manifest, um zu verstehen, wie Ihre APP auf dem Client gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="a1e83-122">When you install an app, Teams parses the manifest to understand how to render your app in the client.</span></span>

### <a name="app-scaffolding"></a><span data-ttu-id="a1e83-123">App-Gerüste</span><span class="sxs-lookup"><span data-stu-id="a1e83-123">App scaffolding</span></span>

<span data-ttu-id="a1e83-124">Das Toolkit erstellt automatisch ein Gerüst für Sie im `src` Verzeichnis basierend auf den Funktionen, die Sie während der Installation hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="a1e83-124">The toolkit automatically creates scaffolding for you in the `src` directory based on the capabilities you added during setup.</span></span>

<span data-ttu-id="a1e83-125">Wenn Sie beispielsweise während des Setups eine RegisterkarteErstellen, `App.js` ist die Datei im `src/components` Verzeichnis wichtig, da Sie die Initialisierung und das Routing Ihrer APP übernimmt.</span><span class="sxs-lookup"><span data-stu-id="a1e83-125">If you create a tab during setup, for example, the `App.js` file in the `src/components` directory is important because it handles the initialization and routing of your app.</span></span> <span data-ttu-id="a1e83-126">Das [Microsoft Teams SDK](../../tabs/how-to/using-teams-client-sdk.md) wird aufgerufen, um die Kommunikation zwischen Ihrer APP und ihren Teams herzustellen.</span><span class="sxs-lookup"><span data-stu-id="a1e83-126">It calls the [Microsoft Teams SDK](../../tabs/how-to/using-teams-client-sdk.md) to establish communication between your app and Teams.</span></span>

### <a name="app-package-developmentzip"></a><span data-ttu-id="a1e83-127">App-Paket ( `Development.zip` )</span><span class="sxs-lookup"><span data-stu-id="a1e83-127">App package (`Development.zip`)</span></span>

<span data-ttu-id="a1e83-128">Im Verzeichnis befindet `.publish` , benötigen Sie das App-Paket, um [Ihre APP](../../concepts/deploy-and-publish/overview.md#upload-your-app-directly) in Microsoft Teams querladen.</span><span class="sxs-lookup"><span data-stu-id="a1e83-128">Located in the `.publish` directory, you need the app package to [sideload your app](../../concepts/deploy-and-publish/overview.md#upload-your-app-directly) in Teams.</span></span> <span data-ttu-id="a1e83-129">Das Paket wird auch verwendet, wenn im [App-Katalog oder AppSource Ihrer Organisation veröffentlicht](../../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) wird. [AppSource](../../concepts/deploy-and-publish/appsource/publish.md)</span><span class="sxs-lookup"><span data-stu-id="a1e83-129">The package is also used when [publishing to your organization's app catalog](../../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) or [AppSource](../../concepts/deploy-and-publish/appsource/publish.md).</span></span>

<span data-ttu-id="a1e83-130">Hier finden Sie einige Details zu den App-Paketdateien:</span><span class="sxs-lookup"><span data-stu-id="a1e83-130">Here are some details about the app package files:</span></span>

|<span data-ttu-id="a1e83-131">Name</span><span class="sxs-lookup"><span data-stu-id="a1e83-131">Name</span></span>|<span data-ttu-id="a1e83-132">Typ</span><span class="sxs-lookup"><span data-stu-id="a1e83-132">Type</span></span>|<span data-ttu-id="a1e83-133">Größe</span><span class="sxs-lookup"><span data-stu-id="a1e83-133">Size</span></span>|<span data-ttu-id="a1e83-134">Speicherort des Manifests</span><span class="sxs-lookup"><span data-stu-id="a1e83-134">Manifest location</span></span>|<span data-ttu-id="a1e83-135">Toolkit-Dateiname</span><span class="sxs-lookup"><span data-stu-id="a1e83-135">Toolkit filename</span></span>|
|---|---|:---:|:---:|-----|
|<span data-ttu-id="a1e83-136">**App-Manifest**</span><span class="sxs-lookup"><span data-stu-id="a1e83-136">**App manifest**</span></span>|`.json`| <span data-ttu-id="a1e83-137">—</span><span class="sxs-lookup"><span data-stu-id="a1e83-137">—</span></span> | <span data-ttu-id="a1e83-138">—</span><span class="sxs-lookup"><span data-stu-id="a1e83-138">—</span></span> |`.publish/manifest.json`|
|<span data-ttu-id="a1e83-139">**Farb Logo**</span><span class="sxs-lookup"><span data-stu-id="a1e83-139">**Color logo**</span></span>|`.png`|<span data-ttu-id="a1e83-140">192 &times; 192 Pixel</span><span class="sxs-lookup"><span data-stu-id="a1e83-140">192&times;192 pixels</span></span>|`icon.color`|`.publish/color.png`|
|<span data-ttu-id="a1e83-141">**Gliederungs Logo**</span><span class="sxs-lookup"><span data-stu-id="a1e83-141">**Outline logo**</span></span>|`.png`|<span data-ttu-id="a1e83-142">32 &times; 32 Pixel</span><span class="sxs-lookup"><span data-stu-id="a1e83-142">32&times;32 pixels</span></span>|`icon.outline`|`.publish/outline.png`|

## <a name="run-your-app"></a><span data-ttu-id="a1e83-143">Ausführen der APP</span><span class="sxs-lookup"><span data-stu-id="a1e83-143">Run your app</span></span>

<span data-ttu-id="a1e83-144">Im Interesse der Zeit erstellen und führen Sie Ihre APP lokal aus.</span><span class="sxs-lookup"><span data-stu-id="a1e83-144">In the interest of time, you'll build and run your app locally.</span></span> <span data-ttu-id="a1e83-145">Teams auf Produktionsebene – apps werden in der Cloud gehostet.</span><span class="sxs-lookup"><span data-stu-id="a1e83-145">Production-level Teams apps are hosted in the cloud.</span></span>

<span data-ttu-id="a1e83-146">(Diese Informationen sind auch im Toolkit verfügbar `README` .)</span><span class="sxs-lookup"><span data-stu-id="a1e83-146">(This information is also available in the toolkit `README`.)</span></span>

1. <span data-ttu-id="a1e83-147">Wechseln Sie in einem Terminal zum Stammverzeichnis des App-Projekts, und führen Sie es aus `npm install` .</span><span class="sxs-lookup"><span data-stu-id="a1e83-147">In a terminal, go to the root directory of your app project and run `npm install`.</span></span>
1. <span data-ttu-id="a1e83-148">Ausführen `npm start` .</span><span class="sxs-lookup"><span data-stu-id="a1e83-148">Run `npm start`.</span></span> <span data-ttu-id="a1e83-149">Nach Abschluss des Vorgangs wird ein **erfolgreiches kompiliert!**</span><span class="sxs-lookup"><span data-stu-id="a1e83-149">Once complete, there's a **Compiled successfully!**</span></span> <span data-ttu-id="a1e83-150">Nachricht im Terminal.</span><span class="sxs-lookup"><span data-stu-id="a1e83-150">message in the terminal.</span></span>
1. <span data-ttu-id="a1e83-151">Öffnen Sie einen Browser, und wechseln Sie zu `https://localhost:3000` , um eine leere Webseite mit dem Namen **Microsoft Teams-Registerkarte**anzuzeigen. (Keine Sorge, dass auf der Seite kein Inhalt angezeigt wird.)</span><span class="sxs-lookup"><span data-stu-id="a1e83-151">Open a browser and go to `https://localhost:3000` to view a blank webpage called **Microsoft Teams Tab**. (Don't worry that you can't see any content on the page.)</span></span><br/>
   :::image type="content" source="../doc-links/images/local-host-tab.png" alt-text="Anzeigen der app in einem Browser.":::

## <a name="set-up-a-secure-tunnel-to-your-app"></a><span data-ttu-id="a1e83-153">Einrichten eines sicheren Tunnels für Ihre APP</span><span class="sxs-lookup"><span data-stu-id="a1e83-153">Set up a secure tunnel to your app</span></span>

<span data-ttu-id="a1e83-154">Ihre APP ist auf Ihrem lokalen Webserver aktiv.</span><span class="sxs-lookup"><span data-stu-id="a1e83-154">Your app is up and running on your local web server.</span></span> <span data-ttu-id="a1e83-155">Wenn Sie Ihre APP in Microsoft Teams ausführen möchten, müssen Sie den `localhost` Zugriff über HTTPS vornehmen.</span><span class="sxs-lookup"><span data-stu-id="a1e83-155">To run your app in Teams, you must make your `localhost` accessible through HTTPS.</span></span>

<span data-ttu-id="a1e83-156">Installieren Sie [ngrok](https://ngrok.com/download) , falls noch nicht geschehen.</span><span class="sxs-lookup"><span data-stu-id="a1e83-156">Install [ngrok](https://ngrok.com/download) if you haven't already.</span></span> <span data-ttu-id="a1e83-157">Wenn Sie dieses Tool ausführen, erstellen Sie zwei global verfügbare URLs, die auf Ihren lokalen Webserver ( `http://localhost:3000` ) deuten.</span><span class="sxs-lookup"><span data-stu-id="a1e83-157">When you run this tool, you create two globally available URLs that point to your local web server (`http://localhost:3000`).</span></span> <span data-ttu-id="a1e83-158">Sie benötigen die Weiterleitungs-URL, die mit beginnt `HTTPS` .</span><span class="sxs-lookup"><span data-stu-id="a1e83-158">You need the forwarding URL that begins with `HTTPS`.</span></span>

1. <span data-ttu-id="a1e83-159">Öffnen Sie ein neues Terminal, und führen Sie es aus `ngrok http 3000` .</span><span class="sxs-lookup"><span data-stu-id="a1e83-159">Open a new terminal and run `ngrok http 3000`.</span></span>
1. <span data-ttu-id="a1e83-160">Kopieren Sie die von Ihnen angegebene HTTPS-URL (siehe das folgende Beispiel).</span><span class="sxs-lookup"><span data-stu-id="a1e83-160">Copy the HTTPS URL you're provided (see the following example).</span></span>
:::image type="content" source="../doc-links/images/ngrok-running.png" alt-text="ngrok-laufendes Bild":::
1. <span data-ttu-id="a1e83-162">Öffnen Sie in Ihrem `.publish` Verzeichnis `Development.env` .</span><span class="sxs-lookup"><span data-stu-id="a1e83-162">In your `.publish` directory, open `Development.env`.</span></span>
1. <span data-ttu-id="a1e83-163">Ersetzen Sie den `baseUrl0` Wert durch die kopierte URL.</span><span class="sxs-lookup"><span data-stu-id="a1e83-163">Replace the `baseUrl0` value with the copied URL.</span></span> <span data-ttu-id="a1e83-164">(Ändern Sie beispielsweise `baseUrl0=http://localhost:3000` in `baseUrl0=https://85528b2b3ba5.ngrok.io` .)</span><span class="sxs-lookup"><span data-stu-id="a1e83-164">(For example, change `baseUrl0=http://localhost:3000` to `baseUrl0=https://85528b2b3ba5.ngrok.io`.)</span></span>

<span data-ttu-id="a1e83-165">Das App-Manifest zeigt jetzt auf die Stelle, an der Sie die APP hosten.</span><span class="sxs-lookup"><span data-stu-id="a1e83-165">Your app manifest now points to where you're hosting the app.</span></span>

## <a name="sideload-your-app-in-teams"></a><span data-ttu-id="a1e83-166">Querladen ihrer app in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="a1e83-166">Sideload your app in Teams</span></span>

<span data-ttu-id="a1e83-167">Wenn Ihre APP über HTTPS läuft und darauf zugegriffen werden kann, sind Sie bereit, Sie in Microsoft Teams hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="a1e83-167">With your app running and accessible via HTTPS, you're ready to upload it to Teams.</span></span>

> [!TIP]
> <span data-ttu-id="a1e83-168">Überprüfen Sie vor dem Sideloading Ihrer APP auf Probleme, die die [Validierungsfunktion des Toolkits](../../concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#teams-app-validation-tool)verwenden.</span><span class="sxs-lookup"><span data-stu-id="a1e83-168">Before sideloading your app, check for issues using the [toolkit's validation feature](../../concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#teams-app-validation-tool).</span></span> <span data-ttu-id="a1e83-169">Fehler müssen behoben sein, damit die APP erfolgreich querladen.</span><span class="sxs-lookup"><span data-stu-id="a1e83-169">Errors must be fixed to successfully sideload the app.</span></span>

1. <span data-ttu-id="a1e83-170">Melden Sie sich mit Ihrem Konto beim Microsoft Teams-Client an, das App-Sideloading zulässt.</span><span class="sxs-lookup"><span data-stu-id="a1e83-170">Log in to the Teams client with your account that allows app sideloading.</span></span> <span data-ttu-id="a1e83-171">(Wenn Sie nicht sicher sind, dass dies der Fall ist, erfahren Sie mehr über das [Einrichten eines Teams-entwicklungskontos](../build-your-first-app/building-real-world-app.md#set-up-your-development-account).)</span><span class="sxs-lookup"><span data-stu-id="a1e83-171">(If you aren't sure you have that, learn about getting a [Teams development account](../build-your-first-app/building-real-world-app.md#set-up-your-development-account).)</span></span>
1. <span data-ttu-id="a1e83-172">Wählen Sie **apps**aus, und wählen Sie dann **benutzerdefinierte App hochladen**aus.</span><span class="sxs-lookup"><span data-stu-id="a1e83-172">Select **Apps**, then choose **Upload a custom app**.</span></span>
1. <span data-ttu-id="a1e83-173">Wechseln Sie zu Ihrem APP `.publish` -Projektordner, und wählen Sie aus `Development.zip` .</span><span class="sxs-lookup"><span data-stu-id="a1e83-173">Go to your app project `.publish` folder and select `Development.zip`.</span></span> <span data-ttu-id="a1e83-174">Eine modale Installation wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a1e83-174">An install modal displays.</span></span>
:::image type="content" source="../doc-links/images/add-teams-app.png" alt-text="Hinzufügen von Teams-App":::
1. <span data-ttu-id="a1e83-176">Wählen Sie **Hinzufügen** aus, um Ihre APP zu installieren.</span><span class="sxs-lookup"><span data-stu-id="a1e83-176">Select **Add** to install your app.</span></span>
:::image type="content" source="../doc-links/images/tab-running.png" alt-text="Screenshot mit einem Beispiel Hello, World! app in Microsoft Teams.":::

<span data-ttu-id="a1e83-178">🎉 Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="a1e83-178">🎉 Congratulations!</span></span> <span data-ttu-id="a1e83-179">Ihre APP wird in Microsoft Teams gestartet.</span><span class="sxs-lookup"><span data-stu-id="a1e83-179">Your app is running in Teams.</span></span>

## <a name="next-step"></a><span data-ttu-id="a1e83-180">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="a1e83-180">Next step</span></span>

<span data-ttu-id="a1e83-181">Erweitern Sie auf der persönlichen Registerkarte, die Sie gerade erstellt haben, oder erstellen Sie eine andere Art von Teams-app.</span><span class="sxs-lookup"><span data-stu-id="a1e83-181">Expand on the personal tab you just created or build another type of Teams app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a1e83-182">Zu Ihrer persönlichen Registerkarte hinzufügen</span><span class="sxs-lookup"><span data-stu-id="a1e83-182">Add to your personal tab</span></span>](../build-your-first-app/add-personal-tab.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="a1e83-183">Erstellen einer Kanal Registerkarte</span><span class="sxs-lookup"><span data-stu-id="a1e83-183">Build a channel tab</span></span>](../build-your-first-app/add-channel-tab.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="a1e83-184">Erstellen eines bot</span><span class="sxs-lookup"><span data-stu-id="a1e83-184">Build a bot</span></span>](../build-your-first-app/add-bot.md)
