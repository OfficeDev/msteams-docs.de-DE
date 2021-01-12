---
title: Erste Schritte – Erstellen und Ausführen Ihrer ersten App
author: heath-hamilton
description: Erstellen Sie schnell eine Microsoft Teams-App, die "Hello, World!" anzeigt. -Nachricht mithilfe des Microsoft Teams Toolkits.
ms.author: lajanuar
ms.date: 11/03/2020
ms.topic: quickstart
ms.openlocfilehash: bc5d18dd887cbdbf56b8d6d013f53c21d1540370
ms.sourcegitcommit: 5687a901d48bcf2f5a3a086e0f703f854e8b9c21
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2021
ms.locfileid: "49795468"
---
# <a name="build-and-run-your-first-microsoft-teams-app"></a><span data-ttu-id="c344a-104">Erstellen und Ausführen Ihrer ersten Microsoft Teams-App</span><span class="sxs-lookup"><span data-stu-id="c344a-104">Build and run your first Microsoft Teams app</span></span>

<span data-ttu-id="c344a-105">Sie können direkt in die Entwicklung von Microsoft Teams einspringen, indem Sie eine persönliche Registerkarte erstellen, auf der "Hello, World!" angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="c344a-105">You can jump right into Microsoft Teams development by building a personal tab that displays "Hello, World!"</span></span>

## <a name="1-create-your-app-project"></a><span data-ttu-id="c344a-106">1. Erstellen Ihres App-Projekts</span><span class="sxs-lookup"><span data-stu-id="c344a-106">1. Create your app project</span></span>

<span data-ttu-id="c344a-107">Verwenden Sie das Microsoft Teams Toolkit in Visual Studio Code, um Ihr erstes App-Projekt einrichten.</span><span class="sxs-lookup"><span data-stu-id="c344a-107">Use the Microsoft Teams Toolkit in Visual Studio Code to set up your first app project.</span></span>

1. In Visual Studio Code, select **Microsoft Teams** on the left Activity Bar and choose Create a new Teams :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: **app**.
1. <span data-ttu-id="c344a-109">Wenn Sie dazu aufgefordert werden, melden Sie sich mit Ihrem Microsoft 365-Entwicklungskonto an.</span><span class="sxs-lookup"><span data-stu-id="c344a-109">When prompted, sign in with your Microsoft 365 development account.</span></span>
1. <span data-ttu-id="c344a-110">Wählen Sie **auf dem Bildschirm** "Funktionen hinzufügen" die Option **"Tab"** und dann **"Weiter" aus.**</span><span class="sxs-lookup"><span data-stu-id="c344a-110">On the **Add capabilities** screen, select **Tab** then **Next**.</span></span>
:::image type="content" source="../assets/images/build-your-first-app/choose-tab.png" alt-text="Screenshot, der zeigt, wie Sie Ihr App-Projekt mit dem Visual Studio Code Teams Toolkit konfigurieren.":::
1. <span data-ttu-id="c344a-112">Geben Sie einen Namen für Ihre Teams-App ein.</span><span class="sxs-lookup"><span data-stu-id="c344a-112">Enter a name for your Teams app.</span></span> <span data-ttu-id="c344a-113">(Dies ist der Standardname für Ihre App und auch der Name des App-Projektverzeichnisses auf dem lokalen Computer.)</span><span class="sxs-lookup"><span data-stu-id="c344a-113">(This is the default name for your app and also the name of the app project directory on your local machine.)</span></span>
1. <span data-ttu-id="c344a-114">Aktivieren Sie nur die Registerkarte "Persönlich", und **wählen** Sie "Fertig stellen" am unteren Rand des Bildschirms aus, um Ihr Projekt zu konfigurieren. </span><span class="sxs-lookup"><span data-stu-id="c344a-114">Check only the **Personal tab** option and select **Finish** at the bottom of the screen to configure your project.</span></span>

## <a name="2-understand-important-app-project-components"></a><span data-ttu-id="c344a-115">2. Verstehen wichtiger Komponenten des App-Projekts</span><span class="sxs-lookup"><span data-stu-id="c344a-115">2. Understand important app project components</span></span>

<span data-ttu-id="c344a-116">Nachdem Das Toolkit Ihr Projekt konfiguriert hat, verfügen Sie über die Komponenten zum Erstellen einer einfachen persönlichen Registerkarte für Teams.</span><span class="sxs-lookup"><span data-stu-id="c344a-116">Once the toolkit configures your project, you have the components to build a basic personal tab for Teams.</span></span> <span data-ttu-id="c344a-117">Die Projektverzeichnissen und Dateien werden im Explorerbereich von Visual Studio Code angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c344a-117">The project directories and files display in the Explorer area of Visual Studio Code.</span></span>

:::image type="content" source="../assets/images/build-your-first-app/app-project-files.png" alt-text="Screenshot showing app project files for a personal tab in Visual Studio Code.":::

### <a name="app-scaffolding"></a><span data-ttu-id="c344a-119">App-Gerüst</span><span class="sxs-lookup"><span data-stu-id="c344a-119">App scaffolding</span></span>

<span data-ttu-id="c344a-120">Das Toolkit erstellt automatisch ein Gerüst für Sie im Verzeichnis basierend auf den `src` Funktionen, die Sie während des Setups hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="c344a-120">The toolkit automatically creates scaffolding for you in the `src` directory based on the capabilities you added during setup.</span></span>

<span data-ttu-id="c344a-121">Wenn Sie beispielsweise während des Setups eine Registerkarte erstellen, ist die Datei im Verzeichnis wichtig, da sie die Initialisierung und das Routing `App.js` `src/components` Ihrer App behandelt.</span><span class="sxs-lookup"><span data-stu-id="c344a-121">If you create a tab during setup, for example, the `App.js` file in the `src/components` directory is important because it handles the initialization and routing of your app.</span></span> <span data-ttu-id="c344a-122">Es ruft das [Microsoft Teams JavaScript-Client-SDK auf,](../tabs/how-to/using-teams-client-sdk.md) um die Kommunikation zwischen Ihrer App und Teams zu herstellen.</span><span class="sxs-lookup"><span data-stu-id="c344a-122">It calls the [Microsoft Teams JavaScript client SDK](../tabs/how-to/using-teams-client-sdk.md) to establish communication between your app and Teams.</span></span>

### <a name="app-id"></a><span data-ttu-id="c344a-123">App-ID</span><span class="sxs-lookup"><span data-stu-id="c344a-123">App ID</span></span>

<span data-ttu-id="c344a-124">Ihre Teams-App-ID wird benötigt, um Ihre App mit App Studio zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="c344a-124">Your Teams app ID is needed to configure your app with App Studio.</span></span> <span data-ttu-id="c344a-125">Sie finden die ID im `teamsAppId` Objekt, das sich in der Projektdatei `package.json` befindet.</span><span class="sxs-lookup"><span data-stu-id="c344a-125">You can find the ID in the `teamsAppId` object, which is located in your project's `package.json` file.</span></span>

## <a name="3-build-and-run-your-app"></a><span data-ttu-id="c344a-126">3. Erstellen und Ausführen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="c344a-126">3. Build and run your app</span></span>

<span data-ttu-id="c344a-127">Im Interesse der Zeit erstellen und führen Sie Ihre App lokal aus.</span><span class="sxs-lookup"><span data-stu-id="c344a-127">In the interest of time, you'll build and run your app locally.</span></span>

<span data-ttu-id="c344a-128">(Diese Informationen sind auch im Toolkit `README` verfügbar.)</span><span class="sxs-lookup"><span data-stu-id="c344a-128">(This information is also available in the toolkit `README`.)</span></span>

1. <span data-ttu-id="c344a-129">Wechseln Sie in einem Terminal zum Stammverzeichnis Ihres App-Projekts, und führen Sie es `npm install` aus.</span><span class="sxs-lookup"><span data-stu-id="c344a-129">In a terminal, go to the root directory of your app project and run `npm install`.</span></span>
1. <span data-ttu-id="c344a-130">Ausführen `npm start` .</span><span class="sxs-lookup"><span data-stu-id="c344a-130">Run `npm start`.</span></span>

<span data-ttu-id="c344a-131">Nach Abschluss des Vorgangs wird ein **kompiliertes Programm erfolgreich erstellt.**</span><span class="sxs-lookup"><span data-stu-id="c344a-131">Once complete, there's a **Compiled successfully!**</span></span> <span data-ttu-id="c344a-132">im Terminal zu senden.</span><span class="sxs-lookup"><span data-stu-id="c344a-132">message in the terminal.</span></span> <span data-ttu-id="c344a-133">Ihre App wird unter `https://localhost:3000` ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="c344a-133">Your app is running on `https://localhost:3000`.</span></span>

## <a name="4-sideload-your-app-in-teams"></a><span data-ttu-id="c344a-134">4. Querladen Ihrer App in Teams</span><span class="sxs-lookup"><span data-stu-id="c344a-134">4. Sideload your app in Teams</span></span>

<span data-ttu-id="c344a-135">Ihre App kann in Teams testbereit sein.</span><span class="sxs-lookup"><span data-stu-id="c344a-135">Your app is ready to test in Teams.</span></span> <span data-ttu-id="c344a-136">Dazu müssen Sie über ein Konto verfügen, das das Querladen von Apps ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="c344a-136">To do this, you must have an account that allows app sideloading.</span></span> <span data-ttu-id="c344a-137">(Wenn Sie nicht sicher sind, ob Sie dies haben, erfahren Sie mehr über das Abrufen eines [Teams-Entwicklungskontos.)](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account)</span><span class="sxs-lookup"><span data-stu-id="c344a-137">(If you aren't sure you have that, learn about getting a [Teams development account](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account).)</span></span>

> [!TIP]
> <span data-ttu-id="c344a-138">Überprüfen Sie vor dem Querladen Ihrer App, ob Probleme mit dem Validierungsfeature [in App Studio](../concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#teams-app-validation-tool)auftreten, das im Toolkit enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="c344a-138">Before sideloading your app, check for issues using the [validation feature in App Studio](../concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#teams-app-validation-tool), which is included in the toolkit.</span></span> <span data-ttu-id="c344a-139">Fehler müssen behoben werden, um die App erfolgreich querladen zu können.</span><span class="sxs-lookup"><span data-stu-id="c344a-139">Errors must be fixed to successfully sideload the app.</span></span>

1. <span data-ttu-id="c344a-140">Drücken Visual Studio Code die **F5-TASTE,** um einen Teams-Webclient zu starten.</span><span class="sxs-lookup"><span data-stu-id="c344a-140">In Visual Studio Code, press the **F5** key to launch a Teams web client.</span></span>
1. <span data-ttu-id="c344a-141">Um Ihre App-Inhalte in Teams anzuzeigen, geben Sie an, dass der Ort, an dem Ihre App ausgeführt wird ( `localhost` ) vertrauenswürdig ist:</span><span class="sxs-lookup"><span data-stu-id="c344a-141">To display your app content in Teams, specify that where your app is running (`localhost`) is trustworthy:</span></span>
   1. <span data-ttu-id="c344a-142">Öffnen Sie eine neue Registerkarte im selben Browserfenster (standardmäßig Google Chrome), das nach drücken von **F5 geöffnet wurde.**</span><span class="sxs-lookup"><span data-stu-id="c344a-142">Open a new tab in the same browser window (Google Chrome by default) which opened after pressing **F5**.</span></span>
   1. <span data-ttu-id="c344a-143">Wechseln Sie `https://localhost:3000/tab` zu der Seite, und fahren Sie mit der Seite fort.</span><span class="sxs-lookup"><span data-stu-id="c344a-143">Go to `https://localhost:3000/tab` and proceed to the page.</span></span>
1. <span data-ttu-id="c344a-144">Wechseln Sie zurück zu Teams.</span><span class="sxs-lookup"><span data-stu-id="c344a-144">Go back to Teams.</span></span> <span data-ttu-id="c344a-145">Wählen Sie im Dialogfeld **"Hinzufügen" aus, um** Ihre App zu installieren.</span><span class="sxs-lookup"><span data-stu-id="c344a-145">In the dialog, select **Add for me** to install your app.</span></span>
:::image type="content" source="../assets/images/build-your-first-app/tab-running.png" alt-text="Screenshot mit einem Beispiel für eine persönliche Registerkarten-App &quot;Hello, World!&quot;, die in Teams ausgeführt wird.":::

<span data-ttu-id="c344a-147">🎉 Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="c344a-147">🎉 Congratulations!</span></span> <span data-ttu-id="c344a-148">Ihre App wird in Teams ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="c344a-148">Your app is running in Teams.</span></span>

## <a name="next-step"></a><span data-ttu-id="c344a-149">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="c344a-149">Next step</span></span>

<span data-ttu-id="c344a-150">Erweitern Sie die persönliche Registerkarte, die Sie gerade erstellt haben, oder erstellen Sie einen anderen Typ von Teams-App.</span><span class="sxs-lookup"><span data-stu-id="c344a-150">Expand on the personal tab you just created or build another type of Teams app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c344a-151">Zu Ihrer persönlichen Registerkarte hinzufügen</span><span class="sxs-lookup"><span data-stu-id="c344a-151">Add to your personal tab</span></span>](../build-your-first-app/build-personal-tab.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="c344a-152">Erstellen einer Kanalregisterkarte</span><span class="sxs-lookup"><span data-stu-id="c344a-152">Build a channel tab</span></span>](../build-your-first-app/build-channel-tab.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="c344a-153">Erstellen eines Bots</span><span class="sxs-lookup"><span data-stu-id="c344a-153">Build a bot</span></span>](../build-your-first-app/build-bot.md)
