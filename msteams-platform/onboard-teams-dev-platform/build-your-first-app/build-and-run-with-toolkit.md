---
title: Erstellen und Ausführen ihrer ersten Teams-App
author: heath-hamilton
description: Führen Sie Ihre erste Microsoft Teams-App aus.
ms.openlocfilehash: 98af8d8d6d89007e36c24bd34661ec21b33cbdf1
ms.sourcegitcommit: 9fbc701a9a039ecdc360aefbe86df52b9c3593f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/12/2020
ms.locfileid: "46652045"
---
# <a name="build-and-run-your-first-microsoft-teams-app"></a><span data-ttu-id="94e61-103">Erstellen und Ausführen ihrer ersten Microsoft Teams-App</span><span class="sxs-lookup"><span data-stu-id="94e61-103">Build and run your first Microsoft Teams app</span></span>

<span data-ttu-id="94e61-104">Sie können direkt in die Entwicklung auf der Microsoft Teams-Plattform wechseln, indem Sie schnell eine einfache APP erstellen und durchführen.</span><span class="sxs-lookup"><span data-stu-id="94e61-104">You can jump right into developing on the Microsoft Teams platform by quickly building and running a basic app.</span></span>

> [!NOTE]
> <span data-ttu-id="94e61-105">Bei der Befolgen dieser Lernprogramme ist es hilfreich, über funktionsfähige JavaScript-Kenntnisse (konkret reagieren) zu verfügen.</span><span class="sxs-lookup"><span data-stu-id="94e61-105">It's helpful to have working knowledge of JavaScript (specifically React) when following these tutorials.</span></span>

## <a name="set-up-your-development-account"></a><span data-ttu-id="94e61-106">Einrichten Ihres entwicklungskontos</span><span class="sxs-lookup"><span data-stu-id="94e61-106">Set up your development account</span></span>

<span data-ttu-id="94e61-107">Um Apps für Teams zu erstellen, benötigen Sie ein Teams-Konto, das Sideloading zulässt (Ihr Konto kann dies möglicherweise bereits bereitstellen).</span><span class="sxs-lookup"><span data-stu-id="94e61-107">To build apps for Teams, you need a Teams account that allows sideloading (your account may already provide this).</span></span> <span data-ttu-id="94e61-108">Wenn dies nicht der Fall ist, registrieren Sie sich für ein Microsoft 365-Entwickler Abonnement, damit Sie einen Testmandanten erhalten können.</span><span class="sxs-lookup"><span data-stu-id="94e61-108">If it doesn't, register for a Microsoft 365 developer subscription so you can get a test tenant.</span></span>

1. <span data-ttu-id="94e61-109">Überprüfen Sie, ob Sie apps in Microsoft Teams querladen können:</span><span class="sxs-lookup"><span data-stu-id="94e61-109">Verify if you can sideload apps in Teams:</span></span>
    1. <span data-ttu-id="94e61-110">Wählen Sie im Microsoft Teams-Client **apps**aus.</span><span class="sxs-lookup"><span data-stu-id="94e61-110">In the Teams client, select **Apps**.</span></span>
    1. <span data-ttu-id="94e61-111">Suchen Sie nach einer Option zum **Hochladen einer benutzerdefinierten App**.</span><span class="sxs-lookup"><span data-stu-id="94e61-111">Look for an option to **Upload a custom app**.</span></span>
1. <span data-ttu-id="94e61-112">Wenn Sie diese Option verwenden, können Sie mit dem Erstellen beginnen.</span><span class="sxs-lookup"><span data-stu-id="94e61-112">If you have this option, you can start building.</span></span> <span data-ttu-id="94e61-113">Wenn dies nicht der Fall ist, führen Sie die folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="94e61-113">If not, do the following:</span></span>
    1. <span data-ttu-id="94e61-114">Registrieren Sie sich für ein [Microsoft 365-Entwickler Abonnement](../doc-links/prepare-your-o365-tenant.md).</span><span class="sxs-lookup"><span data-stu-id="94e61-114">Register for a [Microsoft 365 developer subscription](../doc-links/prepare-your-o365-tenant.md).</span></span>
    1. <span data-ttu-id="94e61-115">[Aktivieren Sie benutzerdefinierte App-Sideloading](../doc-links/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading) für Ihr Test Konto.</span><span class="sxs-lookup"><span data-stu-id="94e61-115">[Enable custom app sideloading](../doc-links/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading) for your test account.</span></span>

## <a name="get-your-development-tools"></a><span data-ttu-id="94e61-116">Abrufen Ihrer Entwicklungstools</span><span class="sxs-lookup"><span data-stu-id="94e61-116">Get your development tools</span></span>

<span data-ttu-id="94e61-117">Sie können Microsoft Teams-apps mit Ihren bevorzugten Tools erstellen, aber hier erfahren Sie, wie Sie mit Visual Studio-Code und dem Microsoft Teams-Toolkit schnell loslegen müssen.</span><span class="sxs-lookup"><span data-stu-id="94e61-117">You can build Teams apps with your preferred tools, but here's what you need to get started quickly with Visual Studio Code and the Microsoft Teams Toolkit.</span></span>

1. <span data-ttu-id="94e61-118">Installieren Sie die neueste Version von [Visual Studio-Code](https://code.visualstudio.com/download).</span><span class="sxs-lookup"><span data-stu-id="94e61-118">Install the latest version of [Visual Studio Code](https://code.visualstudio.com/download).</span></span>
1. <span data-ttu-id="94e61-119">Wählen Sie in Visual Studio Code die Option **Extensions** ![ Visual Studio Toolkit View in ](../doc-links/images/vs-code-extensions.png) der linken Aktivitäts Leiste aus, und installieren Sie das **Microsoft Teams-Toolkit**.</span><span class="sxs-lookup"><span data-stu-id="94e61-119">In Visual Studio Code, select **Extensions** ![visual studio toolkit view](../doc-links/images/vs-code-extensions.png) on the left Activity Bar and install the **Microsoft Teams Toolkit**.</span></span>
1. <span data-ttu-id="94e61-120">Installieren Sie [Node.js](https://nodejs.org/en/).</span><span class="sxs-lookup"><span data-stu-id="94e61-120">Install [Node.js](https://nodejs.org/en/).</span></span>

## <a name="create-an-app-project"></a><span data-ttu-id="94e61-121">Erstellen eines App-Projekts</span><span class="sxs-lookup"><span data-stu-id="94e61-121">Create an app project</span></span>

<span data-ttu-id="94e61-122">Das Microsoft Teams-Toolkit kann Ihnen helfen, ihr erstes App-Projekt einzurichten.</span><span class="sxs-lookup"><span data-stu-id="94e61-122">The Microsoft Teams Toolkit can help you set up your first app project.</span></span>

1. <span data-ttu-id="94e61-123">Öffnen Sie in Visual Studio Code das Toolkit, indem Sie das Symbol Teams auswählen.</span><span class="sxs-lookup"><span data-stu-id="94e61-123">In Visual Studio Code, open the toolkit by selecting the Teams icon</span></span> ![Teams-Symbol](../doc-links/images/favicon-16x16.png) <span data-ttu-id="94e61-125">in der linken Aktivitäts Leiste.</span><span class="sxs-lookup"><span data-stu-id="94e61-125">on the left Activity Bar.</span></span>
1. <span data-ttu-id="94e61-126">Wählen Sie **neue Teams-app erstellen**aus.</span><span class="sxs-lookup"><span data-stu-id="94e61-126">Select **Create a new Teams app**.</span></span>
1. <span data-ttu-id="94e61-127">Wenn Sie dazu aufgefordert werden, geben Sie einen Namen für Ihre APP ein.</span><span class="sxs-lookup"><span data-stu-id="94e61-127">When prompted, enter a name for your app.</span></span> <span data-ttu-id="94e61-128">Dies ist der Standardname für Ihre APP und auch der Name des Projektverzeichnisses auf Ihrem lokalen Computer.</span><span class="sxs-lookup"><span data-stu-id="94e61-128">This is the default name for your app and also the name of the project directory on your local machine.</span></span>
1. <span data-ttu-id="94e61-129">Wählen Sie auf dem Bildschirm **Funktionen hinzufügen** die Option **Tab** und dann dann **weiter**aus.</span><span class="sxs-lookup"><span data-stu-id="94e61-129">On the **Add capabilities** screen, select **Tab** then **Next**.</span></span>
1. <span data-ttu-id="94e61-130">Aktivieren Sie die Option **persönliche Registerkarte** , und wählen Sie **Fertig stellen** aus, um Ihr Projekt zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="94e61-130">Check the **Personal tab** option and select **Finish** to configure your project.</span></span>

![Registerkartenansicht "Toolkit hinzufügen"](../doc-links/images/toolkit-add-tabs.PNG)

<span data-ttu-id="94e61-132">Nachdem Sie abgeschlossen haben, haben Sie die APP-Gerüst Komponenten zum Erstellen einer persönlichen Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="94e61-132">Once complete, you have the app scaffolding components for building a personal tab.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="94e61-133">Ausführen der APP</span><span class="sxs-lookup"><span data-stu-id="94e61-133">Run your app</span></span>

<span data-ttu-id="94e61-134">Führen Sie die `README.md` in Ihrem Projekt beschriebenen Schritte aus, um Ihre APP in Microsoft Teams zu erstellen, auszuführen und bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="94e61-134">Follow the `README.md` in your project to build, run, and deploy your app to Teams.</span></span> <span data-ttu-id="94e61-135">Im allgemeinen helfen Ihnen diese Anweisungen dabei, Folgendes zu tun:</span><span class="sxs-lookup"><span data-stu-id="94e61-135">In general, these instructions help you do the following:</span></span>

* <span data-ttu-id="94e61-136">Hosten Ihrer APP auf `localhost` .</span><span class="sxs-lookup"><span data-stu-id="94e61-136">Host your app on `localhost`.</span></span>
* <span data-ttu-id="94e61-137">[Richten Sie einen sicheren Tunnel mit ngrok ein](../doc-links/debug.md#locally-hosted) , damit Teams auf Ihre App zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="94e61-137">[Set up a secure tunnel with ngrok](../doc-links/debug.md#locally-hosted) so that Teams can access your app.</span></span> <span data-ttu-id="94e61-138">(Installieren Sie [ngrok](https://ngrok.com/download).)</span><span class="sxs-lookup"><span data-stu-id="94e61-138">(Install [ngrok](https://ngrok.com/download).)</span></span>
* <span data-ttu-id="94e61-139">[Querladen Ihre APP](../doc-links/apps-upload.md) im Microsoft Teams-Client mithilfe der `Development.zip` im `.publish` -Ordner.</span><span class="sxs-lookup"><span data-stu-id="94e61-139">[Sideload your app](../doc-links/apps-upload.md) in the Teams client using the `Development.zip` in the `.publish` folder.</span></span>

<span data-ttu-id="94e61-140">Nachdem Sie Ihre APP querladen haben, sollte Sie im Microsoft Teams-Client wie folgt aussehen.</span><span class="sxs-lookup"><span data-stu-id="94e61-140">Once you sideload your app, it should look like this in the Teams client.</span></span>

![Beispielregisterkarte "Hello World"](../doc-links/images/tab-running.png)

## <a name="important-app-project-files"></a><span data-ttu-id="94e61-142">Wichtige Dateien für das App-Projekt</span><span class="sxs-lookup"><span data-stu-id="94e61-142">Important app project files</span></span>

<span data-ttu-id="94e61-143">Wenn Ihr App-Projekt und das Gerüstbau eingerichtet sind, nehmen Sie sich einige Zeit, um einige der wichtigsten Dateien zu verstehen, mit denen die Teams-App-Entwickler arbeiten.</span><span class="sxs-lookup"><span data-stu-id="94e61-143">With your app project and scaffolding set up, take some time to understand some of the key files Teams app developers work with.</span></span>

### <a name="app-manifest-manifestjson"></a><span data-ttu-id="94e61-144">App-Manifest ( `manifest.json` )</span><span class="sxs-lookup"><span data-stu-id="94e61-144">App manifest (`manifest.json`)</span></span>

<span data-ttu-id="94e61-145">Im Verzeichnis befindet `.publish` sich das App-Manifest als Ausgangspunkt für ein beliebiges App-Projekt.</span><span class="sxs-lookup"><span data-stu-id="94e61-145">Located in the `.publish` directory, the app manifest is the starting point for any app project.</span></span> <span data-ttu-id="94e61-146">Das Manifest definiert die grundlegenden Attribute Ihrer APP und verweist auf erforderliche Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="94e61-146">The manifest defines your app's fundamental attributes and points to required resources.</span></span> <span data-ttu-id="94e61-147">Wenn Sie eine App installieren, analysiert Microsoft Teams das Manifest, um zu verstehen, wie Ihre APP auf dem Client gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="94e61-147">When you install an app, Teams parses the manifest to understand how to render your app in the client.</span></span>

<span data-ttu-id="94e61-148">In den folgenden Lernprogrammen konzentrieren Sie sich auf die Abschnitte des App-Manifests zum Erstellen von persönlichen und Kanal Registerkarten.</span><span class="sxs-lookup"><span data-stu-id="94e61-148">In the following tutorials, you'll focus on the sections of the app manifest for building personal and channel tabs.</span></span>

### <a name="package-developmentzip"></a><span data-ttu-id="94e61-149">Paket ( `Development.zip` )</span><span class="sxs-lookup"><span data-stu-id="94e61-149">Package (`Development.zip`)</span></span>

<span data-ttu-id="94e61-150">Auch im Verzeichnis befindet `.publish` , benötigen Sie das App-Paket, um [Ihre APP](../../overview.md#how-can-you-share-your-teams-app) in Microsoft Teams querladen.</span><span class="sxs-lookup"><span data-stu-id="94e61-150">Also located in the `.publish` directory, you need the app package to [sideload your app](../../overview.md#how-can-you-share-your-teams-app) in Teams.</span></span> <span data-ttu-id="94e61-151">Es wird auch verwendet, wenn im [App-Katalog Ihrer Organisation oder in](../../overview.md#how-can-you-share-your-teams-app) [AppSource](../../concepts/deploy-and-publish/appsource/publish.md)veröffentlicht wird.</span><span class="sxs-lookup"><span data-stu-id="94e61-151">It's also used when [publishing to your organization's app catalog](../../overview.md#how-can-you-share-your-teams-app) or [AppSource](../../concepts/deploy-and-publish/appsource/publish.md).</span></span>

<span data-ttu-id="94e61-152">Hier finden Sie einige Details zu den App-Paketdateien:</span><span class="sxs-lookup"><span data-stu-id="94e61-152">Here are some details about the app package files:</span></span>

|<span data-ttu-id="94e61-153">Name</span><span class="sxs-lookup"><span data-stu-id="94e61-153">Name</span></span>|<span data-ttu-id="94e61-154">Typ</span><span class="sxs-lookup"><span data-stu-id="94e61-154">Type</span></span>|<span data-ttu-id="94e61-155">Größe</span><span class="sxs-lookup"><span data-stu-id="94e61-155">Size</span></span>|<span data-ttu-id="94e61-156">Speicherort des Manifests</span><span class="sxs-lookup"><span data-stu-id="94e61-156">Manifest location</span></span>|<span data-ttu-id="94e61-157">Toolkit-Dateiname</span><span class="sxs-lookup"><span data-stu-id="94e61-157">Toolkit filename</span></span>|
|---|---|:---:|:---:|-----|
|<span data-ttu-id="94e61-158">**App-Manifest**</span><span class="sxs-lookup"><span data-stu-id="94e61-158">**App manifest**</span></span>|`.json`| <span data-ttu-id="94e61-159">—</span><span class="sxs-lookup"><span data-stu-id="94e61-159">—</span></span> | <span data-ttu-id="94e61-160">—</span><span class="sxs-lookup"><span data-stu-id="94e61-160">—</span></span> |`.publish/manifest.json`|
|<span data-ttu-id="94e61-161">**Farb Logo**</span><span class="sxs-lookup"><span data-stu-id="94e61-161">**Color logo**</span></span>|`.png`|<span data-ttu-id="94e61-162">192 &times; 192 Pixel</span><span class="sxs-lookup"><span data-stu-id="94e61-162">192&times;192 pixels</span></span>|`icon.color`|`.publish/color.png`|
|<span data-ttu-id="94e61-163">**Gliederungs Logo**</span><span class="sxs-lookup"><span data-stu-id="94e61-163">**Outline logo**</span></span>|`.png`|<span data-ttu-id="94e61-164">32 &times; 32 Pixel</span><span class="sxs-lookup"><span data-stu-id="94e61-164">32&times;32 pixels</span></span>|`icon.outline`|`.publish/outline.png`|

### <a name="scaffolding-src"></a><span data-ttu-id="94e61-165">Gerüstbau ( `src` )</span><span class="sxs-lookup"><span data-stu-id="94e61-165">Scaffolding (`src`)</span></span>

<span data-ttu-id="94e61-166">Das Toolkit erstellt automatisch ein Gerüst für Sie im `src` Verzeichnis basierend auf den Funktionen, die Sie während der Installation hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="94e61-166">The toolkit automatically creates scaffolding for you in the `src` directory based on the capabilities you added during setup.</span></span>

<span data-ttu-id="94e61-167">Einige Dateien werden erstellt, unabhängig davon, welche Art von APP Sie haben, though.</span><span class="sxs-lookup"><span data-stu-id="94e61-167">Some files are created no matter what kind of app you have, though.</span></span> <span data-ttu-id="94e61-168">Beispielsweise ist die `App.js` Datei im `src/components` Verzeichnis wichtig, da Sie die Initialisierung und das Routing Ihrer APP übernimmt.</span><span class="sxs-lookup"><span data-stu-id="94e61-168">For example, the `App.js` file in the `src/components` directory is important because it handles the initialization and routing of your app.</span></span> <span data-ttu-id="94e61-169">Am wichtigsten ist, dass das [Microsoft Teams SDK](../doc-links/using-teams-client-sdk.md) aufgerufen wird, um die Kommunikation zwischen Ihrer APP und ihren Teams herzustellen.</span><span class="sxs-lookup"><span data-stu-id="94e61-169">Most importantly, it calls the [Microsoft Teams SDK](../doc-links/using-teams-client-sdk.md) to establish communication between your app and Teams.</span></span>

<span data-ttu-id="94e61-170">Weitere Informationen zu Gerüsten finden Sie in den Lernprogrammen zum Erstellen von persönlichen und Kanal Registerkarten.</span><span class="sxs-lookup"><span data-stu-id="94e61-170">You can learn more about scaffolding in the tutorials for creating personal and channel tabs.</span></span>

## <a name="next-step"></a><span data-ttu-id="94e61-171">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="94e61-171">Next step</span></span>

<span data-ttu-id="94e61-172">🎉 Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="94e61-172">🎉 Congratulations!</span></span> <span data-ttu-id="94e61-173">Sie verfügen über eine laufende Teams-app.</span><span class="sxs-lookup"><span data-stu-id="94e61-173">You have a running Teams app.</span></span> <span data-ttu-id="94e61-174">Wählen Sie die folgende Schaltfläche aus, um zu erfahren, wie Sie eine reale Funktion hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="94e61-174">Select the following button to learn how to add a real-world feature to it.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="94e61-175">Erstellen einer persönlichen Registerkarte</span><span class="sxs-lookup"><span data-stu-id="94e61-175">Build a personal tab</span></span>](add-personal-tab.md)
