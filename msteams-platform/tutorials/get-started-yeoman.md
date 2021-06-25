---
title: Lernprogramm – Erstellen Ihrer ersten App mithilfe des Yeoman-Generators
description: Erfahren Sie, wie Sie mit dem Yeoman-Generator mit dem Erstellen Microsoft Teams Apps beginnen.
keywords: Erste Schritte node.js nodejs yeoman
localization_priority: Normal
ms.topic: tutorial
ms.custom: scenarios:getting-started
ms.openlocfilehash: ed9e9c15c1287bb6d26778161302e45833205a75
ms.sourcegitcommit: 6e4d2c8e99426125f7b72b9640ee4a4b4f374401
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/24/2021
ms.locfileid: "53114386"
---
# <a name="build-your-first-microsoft-teams-app-using-the-yeoman-generator"></a><span data-ttu-id="61f43-104">Erstellen Ihrer ersten Microsoft Teams-App mithilfe des Yeoman-Generators</span><span class="sxs-lookup"><span data-stu-id="61f43-104">Build your first Microsoft Teams app using the Yeoman generator</span></span>

> [!Note]
> <span data-ttu-id="61f43-105">Dieses Lernprogramm stammt aus dem [Yeoman-Generator für Teams Wiki.](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App)</span><span class="sxs-lookup"><span data-stu-id="61f43-105">This tutorial comes from the [Yeoman generator for Teams wiki](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App).</span></span>

<span data-ttu-id="61f43-106">In diesem Lernprogramm erfahren Sie, wie Sie Ihre erste Microsoft Teams-App mit dem Microsoft Teams Yeoman-Generator erstellen.</span><span class="sxs-lookup"><span data-stu-id="61f43-106">In this tutorial, you will learn how to build your very first Microsoft Teams app using the Microsoft Teams Yeoman generator.</span></span> <span data-ttu-id="61f43-107">Außerdem werden Sie durch den Prozess des Upgradens Ihrer Teams mithilfe des Yeoman-Generators führt.</span><span class="sxs-lookup"><span data-stu-id="61f43-107">It also walks you through the process of upgrading your Teams using the Yeoman generator.</span></span> <span data-ttu-id="61f43-108">Bevor Sie beginnen, benötigen Sie ein Teams Konto, das das [Querladen von Apps](~/concepts/build-and-test/prepare-your-o365-tenant.md)ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="61f43-108">Before you begin, you must have a Teams account that allows [app sideloading](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>

![Git des Yeoman-Generators](~/assets/yeoman-demo.gif)

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="GetPrerequisites"></a>

## <a name="get-prerequisites"></a><span data-ttu-id="61f43-110">Voraussetzungen abrufen</span><span class="sxs-lookup"><span data-stu-id="61f43-110">Get Prerequisites</span></span>

<span data-ttu-id="61f43-111">Sie müssen Folgendes auf Ihrem Computer installieren, bevor Sie mit der Verwendung des Yeoman-Generators beginnen:</span><span class="sxs-lookup"><span data-stu-id="61f43-111">You need to install the following on your machine before starting to use the Yeoman generator:</span></span>

* <span data-ttu-id="61f43-112">Node.js</span><span class="sxs-lookup"><span data-stu-id="61f43-112">Node.js</span></span>

   <span data-ttu-id="61f43-113">Sie müssen Node.js auf Ihrem Computer installiert haben.</span><span class="sxs-lookup"><span data-stu-id="61f43-113">You need to have Node.js installed on your machine.</span></span> <span data-ttu-id="61f43-114">Sie sollten die neueste [LTS-Version](https://nodejs.org)verwenden.</span><span class="sxs-lookup"><span data-stu-id="61f43-114">You should use the latest [LTS version](https://nodejs.org).</span></span>

* <span data-ttu-id="61f43-115">Ein Code-Editor</span><span class="sxs-lookup"><span data-stu-id="61f43-115">A code editor</span></span>

   <span data-ttu-id="61f43-116">Sie benötigen einen Code-Editor.</span><span class="sxs-lookup"><span data-stu-id="61f43-116">You need a code editor.</span></span> <span data-ttu-id="61f43-117">Die meisten dieser Dokumentationen und Bilder beziehen sich auf die Verwendung [Visual Studio Code](https://code.visualstudio.com).</span><span class="sxs-lookup"><span data-stu-id="61f43-117">Most of this documentation and images refer to using [Visual Studio Code](https://code.visualstudio.com).</span></span> <span data-ttu-id="61f43-118">Sie können jedoch den gewünschten Text-Editor verwenden.</span><span class="sxs-lookup"><span data-stu-id="61f43-118">However, feel free to use whatever text editor you prefer.</span></span>

* <span data-ttu-id="61f43-119">Yeoman und Gulp CLI</span><span class="sxs-lookup"><span data-stu-id="61f43-119">Yeoman and Gulp CLI</span></span>

   <span data-ttu-id="61f43-120">Zum Erstellen eines Gerüsts für Projekte mithilfe des Generators müssen Sie das Yeoman-Tool und den Gulp CLI-Task-Manager installieren.</span><span class="sxs-lookup"><span data-stu-id="61f43-120">To scaffold projects using the generator, you must install the Yeoman tool and Gulp CLI task manager.</span></span>

   <span data-ttu-id="61f43-121">Öffnen Sie eine Eingabeaufforderung, und geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="61f43-121">Open up a command prompt and type the following:</span></span>

   ```bash
   npm install yo gulp-cli --global
   ```

## <a name="install-the-generator"></a><span data-ttu-id="61f43-122">Installieren des Generators</span><span class="sxs-lookup"><span data-stu-id="61f43-122">Install the generator</span></span>

<span data-ttu-id="61f43-123">Installieren Sie den Teams Yeoman-Generator mit dem folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="61f43-123">Install the Teams Yeoman generator with the following command:</span></span>

```bash
npm init yo teams
```

<span data-ttu-id="61f43-124">Installieren Sie die Vorschauversion des Generators mit dem folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="61f43-124">Install the preview version of the generator with the following command:</span></span>

```bash
npm init yo teams@preview
```

## <a name="generate-your-project"></a><span data-ttu-id="61f43-125">Generieren Ihres Projekts</span><span class="sxs-lookup"><span data-stu-id="61f43-125">Generate your project</span></span>

<span data-ttu-id="61f43-126">In diesem Abschnitt werden Sie durch die Schritte zum Generieren Ihres Projekts geführt.</span><span class="sxs-lookup"><span data-stu-id="61f43-126">This section walks you through the steps to generate your project.</span></span>

<span data-ttu-id="61f43-127">**So generieren Sie Ihr Projekt**</span><span class="sxs-lookup"><span data-stu-id="61f43-127">**To generate your project**</span></span>

1. <span data-ttu-id="61f43-128">Öffnen Sie eine Eingabeaufforderung, und erstellen Sie ein neues Verzeichnis, in dem Sie Ihr Projekt erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="61f43-128">Open a command prompt and create a new directory where you want to create your project.</span></span>
1. <span data-ttu-id="61f43-129">Wechseln Sie zum Verzeichnis, und führen Sie den Befehl `yo teams` aus.</span><span class="sxs-lookup"><span data-stu-id="61f43-129">Go to the directory, and run the command `yo teams`.</span></span> <span data-ttu-id="61f43-130">Der Generator wird gestartet.</span><span class="sxs-lookup"><span data-stu-id="61f43-130">The generator starts.</span></span>
1. <span data-ttu-id="61f43-131">Antworten Sie auf die Fragen, die vom Generator gestellt werden:</span><span class="sxs-lookup"><span data-stu-id="61f43-131">Respond to the set of questions prompted by the generator:</span></span>

   ![Yo Teams](~/assets/yeoman-images/teams-first-app-1.png)

   1. <span data-ttu-id="61f43-133">Geben Sie einen Namen für Ihr Projekt ein.</span><span class="sxs-lookup"><span data-stu-id="61f43-133">Enter a name for your project.</span></span> <span data-ttu-id="61f43-134">Sie können es wie belassen, indem Sie die EINGABETASTE drücken.</span><span class="sxs-lookup"><span data-stu-id="61f43-134">You can leave it as is by pressing Enter.</span></span>
   1. <span data-ttu-id="61f43-135">Geben Sie einen Pfad für das neue Verzeichnis ein, wenn Sie ein neues Verzeichnis erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="61f43-135">Enter a path for the new directory if you want to create a new directory.</span></span> <span data-ttu-id="61f43-136">Da Sie sich bereits im gewünschten Verzeichnis befinden, drücken Sie einfach die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="61f43-136">As you are already in the directory you want, just press Enter.</span></span>
   1. <span data-ttu-id="61f43-137">Geben Sie den Titel Ihres Projekts ein.</span><span class="sxs-lookup"><span data-stu-id="61f43-137">Enter the title of your project.</span></span> <span data-ttu-id="61f43-138">Dieser Titel wird im Manifest und in der Beschreibung Ihrer App verwendet.</span><span class="sxs-lookup"><span data-stu-id="61f43-138">This title will be used in the manifest and description of your app.</span></span> 
   1. <span data-ttu-id="61f43-139">Geben Sie einen Firmennamen ein, der auch im Manifest verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="61f43-139">Enter a company name which also will be used in the manifest.</span></span>
   1. <span data-ttu-id="61f43-140">Geben Sie die Version des Manifests ein, das Sie verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="61f43-140">Enter the version of the manifest you want to use.</span></span> <span data-ttu-id="61f43-141">Wählen Sie für dieses Lernprogramm `v1.5` das aktuelle allgemein verfügbare Schema aus.</span><span class="sxs-lookup"><span data-stu-id="61f43-141">For this tutorial select `v1.5`, which is the current general available schema.</span></span>
   1. <span data-ttu-id="61f43-142">Wählen Sie die Elemente aus, die Sie Ihrem Projekt hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="61f43-142">Select the items you want to add to your project.</span></span> <span data-ttu-id="61f43-143">Sie können eine einzelne oder eine beliebige Kombination von Elementen auswählen.</span><span class="sxs-lookup"><span data-stu-id="61f43-143">You can select a single one or any combination of items.</span></span> <span data-ttu-id="61f43-144">Wählen Sie für diese Lernprogramme einfach *eine Registerkarte* aus:</span><span class="sxs-lookup"><span data-stu-id="61f43-144">For this tutorials, just select *a Tab*:</span></span>

    ![Elementauswahl](~/assets/yeoman-images/teams-first-app-2.png)

1. <span data-ttu-id="61f43-146">Antworten Sie auf die nächsten Folgefragen, die basierend auf den in Schritt 2 ausgewählten Elementen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="61f43-146">Respond to the next set of follow-up questions that appear based on the items you selected in Step 2.</span></span>
1. <span data-ttu-id="61f43-147">Geben Sie eine URL für den Speicherort ein, an dem Sie Ihre Lösung hosten möchten.</span><span class="sxs-lookup"><span data-stu-id="61f43-147">Enter a URL for the location where you will host your solution.</span></span> 

   > [!NOTE]
   > <span data-ttu-id="61f43-148">Die URL kann eine beliebige URL sein, aber standardmäßig schlägt der Generator eine Azure-Website-URL vor.</span><span class="sxs-lookup"><span data-stu-id="61f43-148">The URL can be any URL, but by default the generator suggests an Azure web site URL.</span></span>

1. <span data-ttu-id="61f43-149">Vergewissern Sie sich, dass Sie Komponententests für Ihre Lösung einschließen möchten.</span><span class="sxs-lookup"><span data-stu-id="61f43-149">Confirm if you want to include unit-testing for your solution.</span></span> <span data-ttu-id="61f43-150">Die Standardantwort lautet **Ja**.</span><span class="sxs-lookup"><span data-stu-id="61f43-150">The default response is **Yes**.</span></span> <span data-ttu-id="61f43-151">Wenn Sie sich dafür entscheiden, Komponententests einzubeziehen, verfügt das generierte Projekt über ein Komponententestframework und einige Standardeinheitstests für die verschiedenen Elemente, für die ein Gerüst erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="61f43-151">If you opt to include unit-testing, the generated project will have a unit testing framework and some default unit tests for the different items being scaffolded.</span></span> 
   > [!NOTE]
   > * <span data-ttu-id="61f43-152">Wählen Sie für dieses Lernprogramm, kein Testframework einzuschließen.</span><span class="sxs-lookup"><span data-stu-id="61f43-152">For this tutorial choose not to include a test framework.</span></span>
   > * <span data-ttu-id="61f43-153">Der Generator verfügt über viele integrierte erweiterte Features, von denen Sie sich anmelden oder abmelden können.</span><span class="sxs-lookup"><span data-stu-id="61f43-153">The generator has a lot of built-in advanced features that you can opt-in or opt-out of.</span></span>

1. <span data-ttu-id="61f43-154">Um Ihnen die Anmeldung zu erleichtern, werden Sie auch gefragt, ob Sie Azure Application Insights für die Anmeldung verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="61f43-154">In order to make signing-in easy for you, you will also be asked if you want to use Azure Application Insights for signing-in.</span></span> <span data-ttu-id="61f43-155">Wenn Sie **"Ja"** auswählen, müssen Sie einen Azure-Anwendungsschlüssel Insights bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="61f43-155">If you select **Yes**, you will need to provide an Azure Application Insights key.</span></span> 

   > [!NOTE]
   > <span data-ttu-id="61f43-156">In diesem Lernprogramm wird die Verwendung von Anwendungs-Insights abgemeldet.</span><span class="sxs-lookup"><span data-stu-id="61f43-156">For this tutorial opt-out of using Application Insights.</span></span>

   <span data-ttu-id="61f43-157">Die nächsten Fragen basieren auf den zuvor ausgewählten Elementen.</span><span class="sxs-lookup"><span data-stu-id="61f43-157">The next set of questions will be based on the previously selected items.</span></span> <span data-ttu-id="61f43-158">Für eine Registerkarte müssen Sie nur einen Namen angeben und optional auswählen, ob Sie diese App als SharePoint Online-Webpart verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="61f43-158">For a tab you only need to provide a name and optionally choose if you want to be able to use this app as a SharePoint Online web part.</span></span> <span data-ttu-id="61f43-159">Nachdem Sie den Namen angegeben haben, generiert der Generator das Projekt und installiert alle Abhängigkeiten.</span><span class="sxs-lookup"><span data-stu-id="61f43-159">After you provide the name the generator will generate the project and install all dependencies.</span></span> <span data-ttu-id="61f43-160">Dies dauert ein oder zwei Minuten.</span><span class="sxs-lookup"><span data-stu-id="61f43-160">This will take a minute or two.</span></span>

## <a name="add-code-to-your-tab"></a><span data-ttu-id="61f43-161">Hinzufügen von Code zu Ihrer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="61f43-161">Add code to your tab</span></span>

<span data-ttu-id="61f43-162">Nach Abschluss des Generators können Sie die Lösung in Ihrem bevorzugten Code-Editor öffnen.</span><span class="sxs-lookup"><span data-stu-id="61f43-162">After the generator is done you can open up the solution in your favorite code editor.</span></span> <span data-ttu-id="61f43-163">Nehmen Sie sich ein oder zwei Minuten Zeit, und machen Sie sich mit der Organisation des Codes vertraut.</span><span class="sxs-lookup"><span data-stu-id="61f43-163">Take a minute or two and familiarize yourself with how the code is organized.</span></span> <span data-ttu-id="61f43-164">Weitere Informationen finden Sie in [Project Strukturdokumentation.](https://github.com/OfficeDev/generator-teams/wiki/Project-Structure)</span><span class="sxs-lookup"><span data-stu-id="61f43-164">For more information, see [Project Structure](https://github.com/OfficeDev/generator-teams/wiki/Project-Structure) documentation.</span></span>

<span data-ttu-id="61f43-165">Ihre Registerkarte befindet sich in der `./src/app/scripts/myFirstAppTab/MyFirstAppTab.tsx` Datei.</span><span class="sxs-lookup"><span data-stu-id="61f43-165">Your tab is in the `./src/app/scripts/myFirstAppTab/MyFirstAppTab.tsx` file.</span></span> <span data-ttu-id="61f43-166">Dies ist die TypeScript-React-basierte Klasse für Ihre Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="61f43-166">This is the TypeScript React-based class for your tab.</span></span> 

1. <span data-ttu-id="61f43-167">Suchen Sie die `render()` Methode, und fügen Sie eine Codezeile innerhalb des `<PanelBody>` Steuerelements hinzu, damit sie wie folgt aussieht:</span><span class="sxs-lookup"><span data-stu-id="61f43-167">Locate the `render()` method and add a line of code inside the `<PanelBody>` control so it looks like this:</span></span>

   ``` TypeScript
   <PanelBody>
      <div style={styles.section}>
      Hello World! Yo Teams rocks!
      </div>
   </PanelBody>
   ```
1. <span data-ttu-id="61f43-168">Speichern Sie die Datei, und kehren Sie zur Eingabeaufforderung zurück.</span><span class="sxs-lookup"><span data-stu-id="61f43-168">Save the file and return to the command prompt.</span></span>

## <a name="build-your-app"></a><span data-ttu-id="61f43-169">Erstellen Sie Ihre Anwendung</span><span class="sxs-lookup"><span data-stu-id="61f43-169">Build your app</span></span>

<span data-ttu-id="61f43-170">Sie können nun Ihr Projekt erstellen.</span><span class="sxs-lookup"><span data-stu-id="61f43-170">You can now build your project.</span></span> <span data-ttu-id="61f43-171">Dies erfolgt in zwei Schritten.</span><span class="sxs-lookup"><span data-stu-id="61f43-171">This is done in two steps.</span></span>

1. <span data-ttu-id="61f43-172">Erstellen Sie die Teams App-Manifestdatei für die App, die Sie in Microsoft Teams hochgeladen haben.</span><span class="sxs-lookup"><span data-stu-id="61f43-172">Create the Teams App manifest file for the app that you uploaded into Microsoft Teams.</span></span> <span data-ttu-id="61f43-173">Dies geschieht durch die Gulp-Aufgabe. `gulp manifest`</span><span class="sxs-lookup"><span data-stu-id="61f43-173">This is done by the Gulp task `gulp manifest`.</span></span> <span data-ttu-id="61f43-174">Dadurch wird das Manifest überprüft und eine ZIP-Datei im `./package` Verzeichnis erstellt.</span><span class="sxs-lookup"><span data-stu-id="61f43-174">This will validate the manifest and create a zip file in the `./package` directory.</span></span>
1. <span data-ttu-id="61f43-175">Führen Sie den `gulp build` Befehl aus, um die Lösung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="61f43-175">Run the `gulp build` command to build the solution.</span></span> <span data-ttu-id="61f43-176">Dadurch wird Ihre Lösung in den `./dist` Ordner transpiliert.</span><span class="sxs-lookup"><span data-stu-id="61f43-176">This will transpile your solution into the `./dist` folder.</span></span> 

## <a name="run-your-app"></a><span data-ttu-id="61f43-177">Ausführen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="61f43-177">Run your app</span></span>

<span data-ttu-id="61f43-178">Verwenden Sie den Befehl, um Ihre App `gulp serve` auszuführen.</span><span class="sxs-lookup"><span data-stu-id="61f43-178">To run your app, use the `gulp serve` command.</span></span> <span data-ttu-id="61f43-179">Dadurch wird ein lokaler Webserver erstellt und gestartet, auf dem Sie Ihre App testen können.</span><span class="sxs-lookup"><span data-stu-id="61f43-179">This will build and start a local web server for you to test your app.</span></span> <span data-ttu-id="61f43-180">Der Befehl erstellt die Anwendung auch neu, wenn Sie eine Datei in Ihrem Projekt speichern.</span><span class="sxs-lookup"><span data-stu-id="61f43-180">The command will also rebuild the application whenever you save a file in your project.</span></span> 

<span data-ttu-id="61f43-181">Jetzt sollten Sie zu der Registerkarte wechseln `http://localhost:3007/myFirstAppTab/` und sicherstellen, dass sie gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="61f43-181">You should now be go to `http://localhost:3007/myFirstAppTab/` and ensure that your tab is rendering.</span></span> <span data-ttu-id="61f43-182">Es befindet sich jedoch noch nicht in Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="61f43-182">However, it is not in Microsoft Teams yet.</span></span> 

<span data-ttu-id="61f43-183">**So rendern Sie die Registerkarte in Microsoft Teams**</span><span class="sxs-lookup"><span data-stu-id="61f43-183">**To render your tab in Microsoft Teams**</span></span>

![Anzeigen Ihrer Website in einem Browser](~/assets/yeoman-images/teams-first-app-3.png)

### <a name="run-your-app-in-microsoft-teams"></a><span data-ttu-id="61f43-185">Ausführen Ihrer App in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="61f43-185">Run your app in Microsoft Teams</span></span>

<span data-ttu-id="61f43-186">Microsoft Teams nicht zulässt, dass Ihre App auf localhost gehostet wird. Daher müssen Sie sie entweder unter einer öffentlichen URL veröffentlichen oder einen Proxy wie ngrok verwenden.</span><span class="sxs-lookup"><span data-stu-id="61f43-186">Microsoft Teams does not allow you to have your app hosted on localhost, so you need to either publish it to a public URL or use a proxy such as ngrok.</span></span> <span data-ttu-id="61f43-187">Eine gute Nachricht ist, dass das Gerüstprojekt über dieses integrierte Projekt verfügt.</span><span class="sxs-lookup"><span data-stu-id="61f43-187">Good news is that the scaffolded project has this built-in.</span></span> 

<span data-ttu-id="61f43-188">**So führen Sie Ihre App in Teams**</span><span class="sxs-lookup"><span data-stu-id="61f43-188">**To run your app in Teams**</span></span>

1. <span data-ttu-id="61f43-189">Wird `gulp ngrok-serve` in Terminal ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="61f43-189">Run `gulp ngrok-serve` in Terminal.</span></span> <span data-ttu-id="61f43-190">Wenn Sie `gulp ngrok-serve` den ngrok-Dienst ausführen, wird er im Hintergrund mit einem eindeutigen und öffentlichen DNS-Eintrag gestartet. Außerdem wird das Manifest mit dieser eindeutigen URL verpackt und dann genau dasselbe ausgeführt wie `gulp serve` .</span><span class="sxs-lookup"><span data-stu-id="61f43-190">When you run `gulp ngrok-serve` the ngrok service will be started in the background, with a unique and public DNS entry and it will also package the manifest with that unique URL and then do the exact same thing as `gulp serve`.</span></span>
1. <span data-ttu-id="61f43-191">Erstellen Sie ein neues Microsoft Teams Team.</span><span class="sxs-lookup"><span data-stu-id="61f43-191">Create a new Microsoft Teams team.</span></span>
1. <span data-ttu-id="61f43-192">Wählen Sie den Teamnamen > Teams Einstellungen > Apps aus.</span><span class="sxs-lookup"><span data-stu-id="61f43-192">Select the Team name > Teams Settings > Apps.</span></span>
1. <span data-ttu-id="61f43-193">Wählen Sie in der unteren rechten Ecke **Hochladen einer benutzerdefinierten App** aus.</span><span class="sxs-lookup"><span data-stu-id="61f43-193">From the lower right corner, select **Upload a custom app**.</span></span>
1. <span data-ttu-id="61f43-194">Wechseln Sie zum `package` Ordner unter Ihrem Projektordner.</span><span class="sxs-lookup"><span data-stu-id="61f43-194">Go to the `package` folder under your project folder.</span></span> 
1. <span data-ttu-id="61f43-195">Wählen Sie die ZIP-Datei in diesem Ordner aus, und wählen Sie "Öffnen" aus.</span><span class="sxs-lookup"><span data-stu-id="61f43-195">Select the zip file in that folder and select open.</span></span> 
   <span data-ttu-id="61f43-196">Ihre App wird nun in Microsoft Teams quergeladen:</span><span class="sxs-lookup"><span data-stu-id="61f43-196">Your App is now sideloaded into Microsoft Teams:</span></span>

   ![Quergeladene App](~/assets/yeoman-images/teams-first-app-4.png)
1. <span data-ttu-id="61f43-198">Wechseln Sie zurück zum Kanal **"Allgemein",** und wählen Sie **+** aus, um eine neue Registerkarte hinzuzufügen. Die Registerkarte sollte in der Liste der Registerkarten angezeigt werden: ![ Registerkarte konfigurieren](~/assets/yeoman-images/teams-first-app-5.png)</span><span class="sxs-lookup"><span data-stu-id="61f43-198">Go back to the **General** channel and select **+** to add a new Tab. You should see your tab in the list of tabs: ![configure tab](~/assets/yeoman-images/teams-first-app-5.png)</span></span>
1. <span data-ttu-id="61f43-199">Wählen Sie Ihre Registerkarte aus, und folgen Sie den Anweisungen, um sie hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="61f43-199">Select your tab and follow the instructions to add it.</span></span> <span data-ttu-id="61f43-200">Beachten Sie, dass Sie über ein benutzerdefiniertes Konfigurationsdialogfeld verfügen, für das Sie die Quelle bearbeiten können.</span><span class="sxs-lookup"><span data-stu-id="61f43-200">Notice that you have a custom configuration dialog, for which you can edit the source.</span></span> <span data-ttu-id="61f43-201">Wählen Sie *"Speichern"* aus, um ihre Registerkarte zum Kanal hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="61f43-201">Select *Save* to add your tab to the channel.</span></span> <span data-ttu-id="61f43-202">Ihre Registerkarte wird jetzt in Microsoft Teams geladen!</span><span class="sxs-lookup"><span data-stu-id="61f43-202">Your tab is now loaded inside Microsoft Teams!</span></span>

   ![Registerkarte "Ausführen" in Teams](~/assets/yeoman-images/teams-first-app-6.png)

### <a name="upgrade-microsoft-teams"></a><span data-ttu-id="61f43-204">Upgrade Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="61f43-204">Upgrade Microsoft Teams</span></span>

<span data-ttu-id="61f43-205">Sie können ihre aktuelle Microsoft Teams Version auch mit dem Microsoft Teams Yeoman-Generator auf die neueste Version aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="61f43-205">You can also upgrade your current Microsoft Teams version to the latest version using the Microsoft Teams Yeoman generator.</span></span>

<span data-ttu-id="61f43-206">**So aktualisieren Sie Microsoft Teams**</span><span class="sxs-lookup"><span data-stu-id="61f43-206">**To upgrade Microsoft Teams**</span></span>

1. <span data-ttu-id="61f43-207">Rufen Sie die aktuelle Version von Teams mit dem folgenden Befehl ab:</span><span class="sxs-lookup"><span data-stu-id="61f43-207">Get current version of Teams with the following command:</span></span>

   ```PowerShell
    yo teams --version
   ```
2. <span data-ttu-id="61f43-208">Verwenden Sie den folgenden Befehl, um ihren Generator auszuwählen und zu aktualisieren:</span><span class="sxs-lookup"><span data-stu-id="61f43-208">Use the following command to select and update your generator:</span></span>

   ```PowerShell
    yo
   ```
3. <span data-ttu-id="61f43-209">Verwenden Sie die Pfeiltasten, um **"Generatoren aktualisieren"** auszuwählen:</span><span class="sxs-lookup"><span data-stu-id="61f43-209">Use the  arrow keys to select **Update your Generators**:</span></span>

   ![Abbildung von YoSelectUpdatGen](~/assets/images/Update-Teams/YoSelectUpdateGen.png)

4. <span data-ttu-id="61f43-211">Wählen Sie den gewünschten Generator aus der Liste der Generatoren aus:</span><span class="sxs-lookup"><span data-stu-id="61f43-211">Select the generator you want from the list of generators:</span></span>
   > [!NOTE]
   > <span data-ttu-id="61f43-212">Verwenden Sie die Leertaste, um eine ausgewählte Teams Version aus den verfügbaren Optionen auszuwählen oder zu löschen.</span><span class="sxs-lookup"><span data-stu-id="61f43-212">Use the space bar to select or clear a selected Teams version from the available options.</span></span>

    ![Abbildung von UseSpaceToSelectGenerators](~/assets/images/Update-Teams/UseSpaceToSelectGenerators.png)
    

   > [!NOTE]
   > <span data-ttu-id="61f43-214">Es dauert einige Sekunden bis Minuten, bis Teams Installation abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="61f43-214">It takes few seconds to minutes for Teams installation to complete.</span></span>

5. <span data-ttu-id="61f43-215">Verwenden Sie nach Abschluss der Installation den folgenden Befehl, um die installierte Version zu überprüfen:</span><span class="sxs-lookup"><span data-stu-id="61f43-215">After the installation is complete, use the following command to check the installed version:</span></span>

   ```PowerShell
    yo teams --version
   ```
 <span data-ttu-id="61f43-216">Congrats!</span><span class="sxs-lookup"><span data-stu-id="61f43-216">Congrats!</span></span> <span data-ttu-id="61f43-217">Sie haben Ihre erste Microsoft Teams App erstellt und bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="61f43-217">You built and deployed your first Microsoft Teams app.</span></span> <span data-ttu-id="61f43-218">Sie haben auch Microsoft Teams aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="61f43-218">You also upgraded Microsoft Teams.</span></span>

 ## <a name="see-also"></a><span data-ttu-id="61f43-219">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="61f43-219">See also</span></span>

* [<span data-ttu-id="61f43-220">Übersicht über Lernprogramme</span><span class="sxs-lookup"><span data-stu-id="61f43-220">Tutorials Overview</span></span>](code-samples.md)
* [<span data-ttu-id="61f43-221">Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="61f43-221">Code Samples</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples)