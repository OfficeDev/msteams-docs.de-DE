---
title: Erste Schritte – erstellen und Ausführen ihrer ersten App
author: heath-hamilton
description: Erstellen Sie schnell eine Microsoft Teams-APP, die ein "Hello, World!" anzeigt. Nachricht mit dem Microsoft Teams-Toolkit.
ms.author: lajanuar
ms.date: 11/03/2020
ms.topic: quickstart
ms.openlocfilehash: 62c4bd950183ceb64fb30b528661cf84e9210d89
ms.sourcegitcommit: 99c35de7e2c604bd8bce392242c2c2fa709cd50b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2020
ms.locfileid: "48931777"
---
# <a name="build-and-run-your-first-microsoft-teams-app"></a><span data-ttu-id="e9510-104">Erstellen und Ausführen ihrer ersten Microsoft Teams-App</span><span class="sxs-lookup"><span data-stu-id="e9510-104">Build and run your first Microsoft Teams app</span></span>

<span data-ttu-id="e9510-105">Sie können direkt in die Microsoft Teams-Entwicklung wechseln, indem Sie eine persönliche RegisterkarteErstellen, die "Hello, World!" anzeigt.</span><span class="sxs-lookup"><span data-stu-id="e9510-105">You can jump right into Microsoft Teams development by building a personal tab that displays "Hello, World!"</span></span>

## <a name="1-create-your-app-project"></a><span data-ttu-id="e9510-106">1. Erstellen des App-Projekts</span><span class="sxs-lookup"><span data-stu-id="e9510-106">1. Create your app project</span></span>

<span data-ttu-id="e9510-107">Verwenden Sie das Microsoft Teams-Toolkit in Visual Studio Code, um Ihr erstes App-Projekt einzurichten.</span><span class="sxs-lookup"><span data-stu-id="e9510-107">Use the Microsoft Teams Toolkit in Visual Studio Code to set up your first app project.</span></span>

1. Wählen Sie in Visual Studio Code **Microsoft Teams** in :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: der linken Aktivitäts Leiste aus, und wählen Sie **neue Teams-app erstellen** aus.
1. <span data-ttu-id="e9510-109">Wenn Sie dazu aufgefordert werden, melden Sie sich mit Ihrem Microsoft 365-entwicklungskonto an.</span><span class="sxs-lookup"><span data-stu-id="e9510-109">When prompted, sign in with your Microsoft 365 development account.</span></span>
1. <span data-ttu-id="e9510-110">Wählen Sie auf dem Bildschirm **Funktionen hinzufügen** die Option **Tab** und dann dann **weiter** aus.</span><span class="sxs-lookup"><span data-stu-id="e9510-110">On the **Add capabilities** screen, select **Tab** then **Next**.</span></span>
:::image type="content" source="../assets/images/build-your-first-app/choose-tab.png" alt-text="Screenshot, in dem gezeigt wird, wie Ihr App-Projekt mit dem Visual Studio Code Teams-Toolkit konfiguriert wird.":::
1. <span data-ttu-id="e9510-112">Geben Sie einen Namen für Ihre Teams-App ein.</span><span class="sxs-lookup"><span data-stu-id="e9510-112">Enter a name for your Teams app.</span></span> <span data-ttu-id="e9510-113">(Dies ist der Standardname für Ihre APP und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.)</span><span class="sxs-lookup"><span data-stu-id="e9510-113">(This is the default name for your app and also the name of the app project directory on your local machine.)</span></span>
1. <span data-ttu-id="e9510-114">Aktivieren Sie nur die Option **persönliche Registerkarte** , und klicken Sie unten auf dem Bildschirm auf **Fertig stellen** , um Ihr Projekt zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="e9510-114">Check only the **Personal tab** option and select **Finish** at the bottom of the screen to configure your project.</span></span>

## <a name="2-understand-important-app-project-components"></a><span data-ttu-id="e9510-115">2. Grundlegendes zu wichtigen App-Projektkomponenten</span><span class="sxs-lookup"><span data-stu-id="e9510-115">2. Understand important app project components</span></span>

<span data-ttu-id="e9510-116">Nachdem das Toolkit Ihr Projekt konfiguriert hat, müssen Sie die Komponenten zum Erstellen einer einfachen persönlichen Registerkarte für Teams.</span><span class="sxs-lookup"><span data-stu-id="e9510-116">Once the toolkit configures your project, you have the components to build a basic personal tab for Teams.</span></span> <span data-ttu-id="e9510-117">Die Projektverzeichnisse und-Dateien werden im Bereich "Explorer" von Visual Studio Code angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e9510-117">The project directories and files display in the Explorer area of Visual Studio Code.</span></span>

:::image type="content" source="../assets/images/build-your-first-app/app-project-files.png" alt-text="Screenshot, in dem App-Projektdateien für eine persönliche Registerkarte in Visual Studio Code angezeigt werden.":::

### <a name="app-scaffolding"></a><span data-ttu-id="e9510-119">App-Gerüste</span><span class="sxs-lookup"><span data-stu-id="e9510-119">App scaffolding</span></span>

<span data-ttu-id="e9510-120">Das Toolkit erstellt automatisch ein Gerüst für Sie im `src` Verzeichnis basierend auf den Funktionen, die Sie während der Installation hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="e9510-120">The toolkit automatically creates scaffolding for you in the `src` directory based on the capabilities you added during setup.</span></span>

<span data-ttu-id="e9510-121">Wenn Sie beispielsweise während des Setups eine RegisterkarteErstellen, `App.js` ist die Datei im `src/components` Verzeichnis wichtig, da Sie die Initialisierung und das Routing Ihrer APP übernimmt.</span><span class="sxs-lookup"><span data-stu-id="e9510-121">If you create a tab during setup, for example, the `App.js` file in the `src/components` directory is important because it handles the initialization and routing of your app.</span></span> <span data-ttu-id="e9510-122">Das [Microsoft Teams SDK](../tabs/how-to/using-teams-client-sdk.md) wird aufgerufen, um die Kommunikation zwischen Ihrer APP und ihren Teams herzustellen.</span><span class="sxs-lookup"><span data-stu-id="e9510-122">It calls the [Microsoft Teams SDK](../tabs/how-to/using-teams-client-sdk.md) to establish communication between your app and Teams.</span></span>

### <a name="app-id"></a><span data-ttu-id="e9510-123">App-ID</span><span class="sxs-lookup"><span data-stu-id="e9510-123">App ID</span></span>

<span data-ttu-id="e9510-124">Ihre Teams-APP-ID wird benötigt, um Ihre APP mit App Studio zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="e9510-124">Your Teams app ID is needed to configure your app with App Studio.</span></span> <span data-ttu-id="e9510-125">Sie finden die ID im `teamsAppId` Objekt, das sich in der Datei des Projekts befindet `package.json` .</span><span class="sxs-lookup"><span data-stu-id="e9510-125">You can find the ID in the `teamsAppId` object, which is located in your project's `package.json` file.</span></span>

## <a name="3-build-and-run-your-app"></a><span data-ttu-id="e9510-126">3. erstellen und Ausführen der APP</span><span class="sxs-lookup"><span data-stu-id="e9510-126">3. Build and run your app</span></span>

<span data-ttu-id="e9510-127">Im Interesse der Zeit erstellen und führen Sie Ihre APP lokal aus.</span><span class="sxs-lookup"><span data-stu-id="e9510-127">In the interest of time, you'll build and run your app locally.</span></span>

<span data-ttu-id="e9510-128">(Diese Informationen sind auch im Toolkit verfügbar `README` .)</span><span class="sxs-lookup"><span data-stu-id="e9510-128">(This information is also available in the toolkit `README`.)</span></span>

1. <span data-ttu-id="e9510-129">Wechseln Sie in einem Terminal zum Stammverzeichnis des App-Projekts, und führen Sie es aus `npm install` .</span><span class="sxs-lookup"><span data-stu-id="e9510-129">In a terminal, go to the root directory of your app project and run `npm install`.</span></span>
1. <span data-ttu-id="e9510-130">Ausführen `npm start` .</span><span class="sxs-lookup"><span data-stu-id="e9510-130">Run `npm start`.</span></span>

<span data-ttu-id="e9510-131">Nach Abschluss des Vorgangs wird ein **erfolgreiches kompiliert!**</span><span class="sxs-lookup"><span data-stu-id="e9510-131">Once complete, there's a **Compiled successfully!**</span></span> <span data-ttu-id="e9510-132">Nachricht im Terminal.</span><span class="sxs-lookup"><span data-stu-id="e9510-132">message in the terminal.</span></span> <span data-ttu-id="e9510-133">Ihre APP wird gestartet `https://localhost:3000` .</span><span class="sxs-lookup"><span data-stu-id="e9510-133">Your app is running on `https://localhost:3000`.</span></span>

## <a name="4-sideload-your-app-in-teams"></a><span data-ttu-id="e9510-134">4. querladen ihrer app in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="e9510-134">4. Sideload your app in Teams</span></span>

<span data-ttu-id="e9510-135">Ihre APP ist zum Testen in Microsoft Teams verfügbar.</span><span class="sxs-lookup"><span data-stu-id="e9510-135">Your app is ready to test in Teams.</span></span> <span data-ttu-id="e9510-136">Hierzu benötigen Sie ein Konto, das App-Sideloading zulässt.</span><span class="sxs-lookup"><span data-stu-id="e9510-136">To do this, you must have an account that allows app sideloading.</span></span> <span data-ttu-id="e9510-137">(Wenn Sie nicht sicher sind, dass dies der Fall ist, erfahren Sie mehr über das [Einrichten eines Teams-entwicklungskontos](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account).)</span><span class="sxs-lookup"><span data-stu-id="e9510-137">(If you aren't sure you have that, learn about getting a [Teams development account](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account).)</span></span>

> [!TIP]
> <span data-ttu-id="e9510-138">Überprüfen Sie vor dem Sideloading Ihrer APP auf Probleme mit der [Überprüfungsfunktion in App Studio](../concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#teams-app-validation-tool), die im Toolkit enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="e9510-138">Before sideloading your app, check for issues using the [validation feature in App Studio](../concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#teams-app-validation-tool), which is included in the toolkit.</span></span> <span data-ttu-id="e9510-139">Fehler müssen behoben sein, damit die APP erfolgreich querladen.</span><span class="sxs-lookup"><span data-stu-id="e9510-139">Errors must be fixed to successfully sideload the app.</span></span>

1. <span data-ttu-id="e9510-140">Drücken Sie in Visual Studio Code die **F5** -Taste, um einen Microsoft Teams-WebClient zu starten.</span><span class="sxs-lookup"><span data-stu-id="e9510-140">In Visual Studio Code, press the **F5** key to launch a Teams web client.</span></span>
1. <span data-ttu-id="e9510-141">Um Ihre APP-Inhalte in Microsoft Teams anzuzeigen, geben Sie an, wo Ihre APP aktiv ist ( `localhost` ) vertrauenswürdig ist:</span><span class="sxs-lookup"><span data-stu-id="e9510-141">To display your app content in Teams, specify that where your app is running (`localhost`) is trustworthy:</span></span>
   1. <span data-ttu-id="e9510-142">Öffnen Sie eine neue Registerkarte in demselben Browserfenster (standardmäßig Google Chrome), die nach Drücken von **F5** geöffnet wurde.</span><span class="sxs-lookup"><span data-stu-id="e9510-142">Open a new tab in the same browser window (Google Chrome by default) which opened after pressing **F5**.</span></span>
   1. <span data-ttu-id="e9510-143">Wechseln Sie zu `https://localhost:3000/tab` der Seite, und fahren Sie fort.</span><span class="sxs-lookup"><span data-stu-id="e9510-143">Go to `https://localhost:3000/tab` and proceed to the page.</span></span>
1. <span data-ttu-id="e9510-144">Wechseln Sie zurück zu Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="e9510-144">Go back to Teams.</span></span> <span data-ttu-id="e9510-145">Wählen Sie im Dialogfeld **hinzufügen aus** , um Ihre APP zu installieren.</span><span class="sxs-lookup"><span data-stu-id="e9510-145">In the dialog, select **Add for me** to install your app.</span></span>
:::image type="content" source="../assets/images/build-your-first-app/tab-running.png" alt-text="Screenshot mit einem Beispiel für die persönliche Tab-app _OL_QUOTE_PLACEHOLDER_Hello, World!_OL_QUOTE_PLACEHOLDER_, die in Microsoft Teams läuft.":::

<span data-ttu-id="e9510-147">🎉 Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="e9510-147">🎉 Congratulations!</span></span> <span data-ttu-id="e9510-148">Ihre APP wird in Microsoft Teams gestartet.</span><span class="sxs-lookup"><span data-stu-id="e9510-148">Your app is running in Teams.</span></span>

## <a name="next-step"></a><span data-ttu-id="e9510-149">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="e9510-149">Next step</span></span>

<span data-ttu-id="e9510-150">Erweitern Sie auf der persönlichen Registerkarte, die Sie gerade erstellt haben, oder erstellen Sie eine andere Art von Teams-app.</span><span class="sxs-lookup"><span data-stu-id="e9510-150">Expand on the personal tab you just created or build another type of Teams app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e9510-151">Zu Ihrer persönlichen Registerkarte hinzufügen</span><span class="sxs-lookup"><span data-stu-id="e9510-151">Add to your personal tab</span></span>](../build-your-first-app/build-personal-tab.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="e9510-152">Erstellen einer Kanalregisterkarte</span><span class="sxs-lookup"><span data-stu-id="e9510-152">Build a channel tab</span></span>](../build-your-first-app/build-channel-tab.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="e9510-153">Erstellen eines Bots</span><span class="sxs-lookup"><span data-stu-id="e9510-153">Build a bot</span></span>](../build-your-first-app/build-bot.md)
