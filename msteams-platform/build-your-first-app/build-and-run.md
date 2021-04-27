---
title: Erste Schritte – Erstellen und Ausführen Ihrer ersten App
author: heath-hamilton
description: Erstellen Sie schnell eine Microsoft Teams-App, die ein "Hello, World!" anzeigt. mit dem Microsoft Teams Toolkit.
ms.author: lajanuar
localization_priority: Normal
ms.date: 11/03/2020
ms.topic: quickstart
ms.openlocfilehash: 1b34c3f3121e834abc8a8a92a8a0ac9a049c9e07
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020884"
---
# <a name="build-and-run-your-first-microsoft-teams-app"></a><span data-ttu-id="1cb48-104">Erstellen und Ausführen Ihrer ersten Microsoft Teams-App</span><span class="sxs-lookup"><span data-stu-id="1cb48-104">Build and run your first Microsoft Teams app</span></span>

<span data-ttu-id="1cb48-105">Starten Sie die Microsoft Teams-Entwicklung, indem Sie eine persönliche Registerkarte erstellen, auf der "Hello, World!" angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="1cb48-105">Start Microsoft Teams development by building a personal tab that displays "Hello, World!".</span></span>
<span data-ttu-id="1cb48-106">Erstellen und ausführen Sie Ihre erste Teams-App mithilfe der folgenden Schritte:</span><span class="sxs-lookup"><span data-stu-id="1cb48-106">Build and run your first Teams app using the following steps:</span></span>

## <a name="1-create-your-app-project"></a><span data-ttu-id="1cb48-107">1. Erstellen Ihres App-Projekts</span><span class="sxs-lookup"><span data-stu-id="1cb48-107">1. Create your app project</span></span>

<span data-ttu-id="1cb48-108">Verwenden Sie das Microsoft Teams Toolkit in Visual Studio Code, um Ihr erstes App-Projekt zu einrichten.</span><span class="sxs-lookup"><span data-stu-id="1cb48-108">Use the Microsoft Teams Toolkit in Visual Studio Code to set up your first app project.</span></span> <span data-ttu-id="1cb48-109">Erstellen Sie Ihr App-Projekt mithilfe der folgenden Schritte:</span><span class="sxs-lookup"><span data-stu-id="1cb48-109">Create your app project using the following steps:</span></span>

1. Wählen Visual Studio Code auf der linken Aktivitätsleiste **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: aus, und wählen Sie Erstellen einer neuen **Teams-App aus.**
1. <span data-ttu-id="1cb48-111">Melden Sie sich bei Aufforderung mit Ihrem Microsoft 365-Entwicklungskonto an.</span><span class="sxs-lookup"><span data-stu-id="1cb48-111">When prompted, sign in with your Microsoft 365 development account.</span></span>
1. <span data-ttu-id="1cb48-112">Wählen Sie **auf dem** Bildschirm Funktionen hinzufügen die Option **Tab** und dann **Weiter aus.**</span><span class="sxs-lookup"><span data-stu-id="1cb48-112">On the **Add capabilities** screen, select **Tab** then **Next**.</span></span>
:::image type="content" source="../assets/images/build-your-first-app/choose-tab.png" alt-text="Screenshot, der zeigt, wie Sie Ihr App-Projekt mit dem Visual Studio Code Teams Toolkit konfigurieren.":::
1. <span data-ttu-id="1cb48-114">Geben Sie einen Namen für Ihre Teams-App ein.</span><span class="sxs-lookup"><span data-stu-id="1cb48-114">Enter a name for your Teams app.</span></span> <span data-ttu-id="1cb48-115">(Dies ist der Standardname für Ihre App und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.)</span><span class="sxs-lookup"><span data-stu-id="1cb48-115">(This is the default name for your app and also the name of the app project directory on your local machine.)</span></span>
1. <span data-ttu-id="1cb48-116">Aktivieren Sie nur **die Option Persönliche Registerkarte,** und wählen Sie **am** unteren Bildschirmrand Fertig stellen aus, um Ihr Projekt zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="1cb48-116">Check only the **Personal tab** option and select **Finish** at the bottom of the screen to configure your project.</span></span>

## <a name="2-understand-important-app-project-components"></a><span data-ttu-id="1cb48-117">2. Verstehen wichtiger Komponenten des App-Projekts</span><span class="sxs-lookup"><span data-stu-id="1cb48-117">2. Understand important app project components</span></span>

<span data-ttu-id="1cb48-118">Nachdem Das Toolkit Ihr Projekt konfiguriert hat, verfügen Sie über die Komponenten zum Erstellen einer grundlegenden persönlichen Registerkarte für Teams.</span><span class="sxs-lookup"><span data-stu-id="1cb48-118">Once the toolkit configures your project, you have the components to build a basic personal tab for Teams.</span></span> <span data-ttu-id="1cb48-119">Die Projektverzeichnissen und -dateien werden im Explorer-Bereich von Visual Studio angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1cb48-119">The project directories and files display in the Explorer area of Visual Studio Code.</span></span>

:::image type="content" source="../assets/images/build-your-first-app/app-project-files.png" alt-text="Screenshot mit App-Projektdateien für eine persönliche Registerkarte in Visual Studio Code.":::

### <a name="app-scaffolding"></a><span data-ttu-id="1cb48-121">App-Gerüst</span><span class="sxs-lookup"><span data-stu-id="1cb48-121">App scaffolding</span></span>

<span data-ttu-id="1cb48-122">Das Toolkit erstellt automatisch ein Gerüst für Sie im Verzeichnis basierend auf den `src` Funktionen, die Sie während des Setups hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="1cb48-122">The toolkit automatically creates scaffolding for you in the `src` directory based on the capabilities you added during setup.</span></span>

<span data-ttu-id="1cb48-123">Wenn Sie beispielsweise während des Setups eine Registerkarte erstellen, ist die Datei im Verzeichnis wichtig, da sie die Initialisierung und das Routing `App.js` `src/components` Ihrer App behandelt.</span><span class="sxs-lookup"><span data-stu-id="1cb48-123">If you create a tab during setup, for example, the `App.js` file in the `src/components` directory is important because it handles the initialization and routing of your app.</span></span> <span data-ttu-id="1cb48-124">Es ruft das [Microsoft Teams JavaScript-Client-SDK auf,](../tabs/how-to/using-teams-client-sdk.md) um die Kommunikation zwischen Ihrer App und Teams zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="1cb48-124">It calls the [Microsoft Teams JavaScript client SDK](../tabs/how-to/using-teams-client-sdk.md) to establish communication between your app and Teams.</span></span>

### <a name="app-id"></a><span data-ttu-id="1cb48-125">App-ID</span><span class="sxs-lookup"><span data-stu-id="1cb48-125">App ID</span></span>

<span data-ttu-id="1cb48-126">Konfigurieren Sie Ihre App mit App Studio mithilfe der Teams-App-ID.</span><span class="sxs-lookup"><span data-stu-id="1cb48-126">Configure your app with App Studio using the Teams app ID.</span></span> <span data-ttu-id="1cb48-127">Suchen Sie die ID im `teamsAppId` Objekt, das sich in der Projektdatei `package.json` befindet.</span><span class="sxs-lookup"><span data-stu-id="1cb48-127">Find the ID in the `teamsAppId` object, which is located in your project's `package.json` file.</span></span>

## <a name="3-build-and-run-your-app"></a><span data-ttu-id="1cb48-128">3. Erstellen und Ausführen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="1cb48-128">3. Build and run your app</span></span>

<span data-ttu-id="1cb48-129">Erstellen und ausführen Sie Ihre App lokal, um Zeit zu sparen.</span><span class="sxs-lookup"><span data-stu-id="1cb48-129">Build and run your app locally to save time.</span></span> <span data-ttu-id="1cb48-130">Diese Informationen sind auch im Toolkit `README` verfügbar.</span><span class="sxs-lookup"><span data-stu-id="1cb48-130">This information is also available in the toolkit `README`.</span></span> <span data-ttu-id="1cb48-131">Erstellen und ausführen Sie Ihre App mithilfe der folgenden Schritte:</span><span class="sxs-lookup"><span data-stu-id="1cb48-131">Build and run your app using the following steps:</span></span>

1. <span data-ttu-id="1cb48-132">Wechseln Sie in einem Terminal zum Stammverzeichnis Ihres App-Projekts, und führen Sie `npm install` aus.</span><span class="sxs-lookup"><span data-stu-id="1cb48-132">In a terminal, go to the root directory of your app project and run `npm install`.</span></span>
1. <span data-ttu-id="1cb48-133">Führen Sie `npm start` aus.</span><span class="sxs-lookup"><span data-stu-id="1cb48-133">Run `npm start`.</span></span>

<span data-ttu-id="1cb48-134">Sobald sie abgeschlossen sind, wird ein **Kompiliert erfolgreich erstellt!**</span><span class="sxs-lookup"><span data-stu-id="1cb48-134">Once complete, there's a **Compiled successfully!**</span></span> <span data-ttu-id="1cb48-135">-Nachricht im Terminal.</span><span class="sxs-lookup"><span data-stu-id="1cb48-135">message in the terminal.</span></span> <span data-ttu-id="1cb48-136">Ihre App wird auf `https://localhost:3000` ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="1cb48-136">Your app is running on `https://localhost:3000`.</span></span>

## <a name="4-sideload-your-app-in-teams"></a><span data-ttu-id="1cb48-137">4. Querladen Ihrer App in Teams</span><span class="sxs-lookup"><span data-stu-id="1cb48-137">4. Sideload your app in Teams</span></span>

<span data-ttu-id="1cb48-138">Ihre App kann in Teams testen.</span><span class="sxs-lookup"><span data-stu-id="1cb48-138">Your app is ready to test in Teams.</span></span> <span data-ttu-id="1cb48-139">Dazu müssen Sie über ein Microsoft 365-Entwicklungskonto verfügen, das das Querladen von Apps zulässt.</span><span class="sxs-lookup"><span data-stu-id="1cb48-139">To do this, you must have a Microsoft 365 development account that allows app sideloading.</span></span> <span data-ttu-id="1cb48-140">Weitere Informationen zum Öffnen von Konten finden Sie unter [Teams-Entwicklungskonto](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account).</span><span class="sxs-lookup"><span data-stu-id="1cb48-140">For more information on account opening, see [Teams development account](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account).</span></span> 

> [!TIP]
> <span data-ttu-id="1cb48-141">Überprüfen Sie vor dem Querladen Ihrer App mithilfe der [Überprüfungsfunktion in App Studio,](../concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#teams-app-validation-tool)die im Toolkit enthalten ist, nach Problemen.</span><span class="sxs-lookup"><span data-stu-id="1cb48-141">Check for issues before sideloading your app, using the [validation feature in App Studio](../concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#teams-app-validation-tool), which is included in the toolkit.</span></span> <span data-ttu-id="1cb48-142">Beheben Sie die Fehler, um die App erfolgreich querladen zu können.</span><span class="sxs-lookup"><span data-stu-id="1cb48-142">Fix the errors to successfully sideload the app.</span></span>

<span data-ttu-id="1cb48-143">Querladen Ihrer App in Teams mithilfe der folgenden Schritte:</span><span class="sxs-lookup"><span data-stu-id="1cb48-143">Sideload your app in Teams using the following steps:</span></span>

> [!NOTE]
> <span data-ttu-id="1cb48-144">Um das Querladen zu aktivieren, bevor Sie Ihre App in Teams querladen, führen Sie die Schritte unter [Turn on app sideloading aus.](../concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading)</span><span class="sxs-lookup"><span data-stu-id="1cb48-144">To enable sideloading before you sideload your app in Teams, follow the steps in [Turn on app sideloading](../concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading).</span></span>

1. <span data-ttu-id="1cb48-145">Wählen Sie **die F5-Taste** aus, um einen Teams-Webclient in Visual Studio starten.</span><span class="sxs-lookup"><span data-stu-id="1cb48-145">Select the **F5** key to launch a Teams web client in Visual Studio Code.</span></span>
1. <span data-ttu-id="1cb48-146">Um Ihre App-Inhalte in Teams anzuzeigen, geben Sie an, wo Ihre App ausgeführt wird ( `localhost` ) vertrauenswürdig ist:</span><span class="sxs-lookup"><span data-stu-id="1cb48-146">To display your app content in Teams, specify that where your app is running (`localhost`) is trustworthy:</span></span>
   1. <span data-ttu-id="1cb48-147">Öffnen Sie eine neue Registerkarte im gleichen Browserfenster (Standardmäßig Google Chrome), das nach dem Drücken von **F5 geöffnet wurde.**</span><span class="sxs-lookup"><span data-stu-id="1cb48-147">Open a new tab in the same browser window (Google Chrome by default) which opened after pressing **F5**.</span></span>
   1. <span data-ttu-id="1cb48-148">Wechseln Sie `https://localhost:3000/tab` zu und fahren Sie mit der Seite fort.</span><span class="sxs-lookup"><span data-stu-id="1cb48-148">Go to `https://localhost:3000/tab` and proceed to the page.</span></span>
1. <span data-ttu-id="1cb48-149">Wechseln Sie zurück zu Teams.</span><span class="sxs-lookup"><span data-stu-id="1cb48-149">Go back to Teams.</span></span> <span data-ttu-id="1cb48-150">Wählen Sie im Dialogfeld **Hinzufügen aus, um Ihre** App zu installieren.</span><span class="sxs-lookup"><span data-stu-id="1cb48-150">In the dialog, select **Add for me** to install your app.</span></span>
:::image type="content" source="../assets/images/build-your-first-app/tab-running.png" alt-text="Screenshot mit einem Beispiel für die persönliche Tab-App &quot;Hello, World!&quot;, die in Teams ausgeführt wird.":::

<span data-ttu-id="1cb48-152">🎉 Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="1cb48-152">🎉 Congratulations!</span></span> <span data-ttu-id="1cb48-153">Ihre App wird in Teams ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="1cb48-153">Your app is running in Teams.</span></span>

## <a name="next-step"></a><span data-ttu-id="1cb48-154">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="1cb48-154">Next step</span></span>

<span data-ttu-id="1cb48-155">Erweitern Sie auf der persönlichen Registerkarte, die Sie gerade erstellt haben, oder erstellen Sie eine andere Art von Teams-App.</span><span class="sxs-lookup"><span data-stu-id="1cb48-155">Expand on the personal tab you just created or build another type of Teams app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1cb48-156">Hinzufügen zu Ihrer persönlichen Registerkarte</span><span class="sxs-lookup"><span data-stu-id="1cb48-156">Add to your personal tab</span></span>](../build-your-first-app/build-personal-tab.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="1cb48-157">Erstellen einer Kanalregisterkarte</span><span class="sxs-lookup"><span data-stu-id="1cb48-157">Build a channel tab</span></span>](../build-your-first-app/build-channel-tab.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="1cb48-158">Erstellen eines Bots</span><span class="sxs-lookup"><span data-stu-id="1cb48-158">Build a bot</span></span>](../build-your-first-app/build-bot.md)
