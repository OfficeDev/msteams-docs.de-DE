---
title: Erste Schritte mit dem Landarbeits Generator für Microsoft Teams
description: Erste Schritte beim Erstellen von tollen apps mit dem Landwirtschafts Generator für Microsoft Teams
keywords: Erste Schritte Node. js nodejs
ms.topic: tutorial
ms.custom: scenarios:getting-started
ms.openlocfilehash: 217c0900e067a61e083e7ffb0b121afdaa51c49f
ms.sourcegitcommit: b13b38a104946c32cd5245a7af706070e534927d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2020
ms.locfileid: "43034043"
---
# <a name="build-your-first-microsoft-teams-app"></a><span data-ttu-id="08236-104">Erstellen Ihrer ersten Microsoft Teams-App</span><span class="sxs-lookup"><span data-stu-id="08236-104">Build your First Microsoft Teams App</span></span>

>[!Note]
><span data-ttu-id="08236-105">Dieses Lernprogramm stammt aus dem wiki "landkraft- [Generator für Microsoft Teams](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) "</span><span class="sxs-lookup"><span data-stu-id="08236-105">This tutorial comes from the [yeoman generator for Teams wiki](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App)</span></span>

<span data-ttu-id="08236-106">In diesem Tutorial werden wir durch das Erstellen Ihrer ersten Microsoft Teams-App mithilfe des Microsoft Teams-Landarbeits-Generators gehen.</span><span class="sxs-lookup"><span data-stu-id="08236-106">In this tutorial we will walk through creating your very first Microsoft Teams app using the Microsoft Teams Yeoman generator.</span></span> <span data-ttu-id="08236-107">Es wird davon ausgegangen, dass Sie das [Laden von Microsoft Teams-apps aktiviert](~/concepts/build-and-test/prepare-your-o365-tenant.md)haben.</span><span class="sxs-lookup"><span data-stu-id="08236-107">It assumes that you have [enabled side-loading of Microsoft Teams apps](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>

![git-Generator](~/assets/yeoman-demo.gif)

## <a name="setup-and-prepare-your-machine"></a><span data-ttu-id="08236-109">Einrichten und Vorbereiten des Computers</span><span class="sxs-lookup"><span data-stu-id="08236-109">Setup and prepare your machine</span></span>

<span data-ttu-id="08236-110">Sie müssen Folgendes auf Ihrem Computer installieren, bevor Sie mit der Verwendung des Teams-Generators beginnen.</span><span class="sxs-lookup"><span data-stu-id="08236-110">You need to install the following on your machine before starting to use the Teams Generator.</span></span>

### <a name="install-node"></a><span data-ttu-id="08236-111">Installations Knoten</span><span class="sxs-lookup"><span data-stu-id="08236-111">Install Node</span></span>

<span data-ttu-id="08236-112">Sie müssen NodeJS auf Ihrem Computer installiert haben.</span><span class="sxs-lookup"><span data-stu-id="08236-112">You need to have NodeJS installed on your machine.</span></span> <span data-ttu-id="08236-113">Sie sollten die neueste [LTS-Version](https://nodejs.org/dist/latest-v8.x/)verwenden.</span><span class="sxs-lookup"><span data-stu-id="08236-113">You should use the latest [LTS version](https://nodejs.org/dist/latest-v8.x/).</span></span>

### <a name="install-a-code-editor"></a><span data-ttu-id="08236-114">Installieren eines Code-Editors</span><span class="sxs-lookup"><span data-stu-id="08236-114">Install a code editor</span></span>

<span data-ttu-id="08236-115">Sie benötigen auch einen Code-Editor, können jederzeit den von Ihnen bevorzugten Texteditor verwenden.</span><span class="sxs-lookup"><span data-stu-id="08236-115">You also need a code editor, feel free to use whatever text editor you prefer.</span></span> <span data-ttu-id="08236-116">Die meisten dieser Dokumentationen und Screenshots bezieht sich jedoch auf die Verwendung [Visual Studios Codes](https://code.visualstudio.com).</span><span class="sxs-lookup"><span data-stu-id="08236-116">However most of this documentation and screenshots refer to using [Visual Studio Code](https://code.visualstudio.com).</span></span>

### <a name="install-yeoman-and-gulp-cli"></a><span data-ttu-id="08236-117">Installieren von "Autobauer" und "Schluck" CLI</span><span class="sxs-lookup"><span data-stu-id="08236-117">Install Yeoman and Gulp CLI</span></span>

<span data-ttu-id="08236-118">Um ein Gerüst von Projekten mit dem Teams-Generator erstellen zu können, müssen Sie das Tool "Tools" sowie den "Schluck CLI-Task-Manager" installieren.</span><span class="sxs-lookup"><span data-stu-id="08236-118">To be able to scaffold projects using the Teams generator you need to install the Yeoman tool as well as the Gulp CLI task manager.</span></span>

<span data-ttu-id="08236-119">Öffnen Sie eine Eingabeaufforderung, und geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="08236-119">Open up a command prompt and type the following:</span></span>

```bash
npm install yo gulp-cli --global
```

## <a name="install-the-microsoft-teams-apps-generator---yo-teams"></a><span data-ttu-id="08236-120">Installieren der Microsoft Teams-apps-Generator-Yo-Teams</span><span class="sxs-lookup"><span data-stu-id="08236-120">Install the Microsoft Teams Apps generator - Yo Teams</span></span>

<span data-ttu-id="08236-121">Der Befehl "landkraft-Generator für Microsoft Teams-Apps" wird mit dem folgenden Befehl installiert:</span><span class="sxs-lookup"><span data-stu-id="08236-121">The Yeoman generator for Microsoft Teams apps are installed with the following command:</span></span>

```bash
npm install generator-teams --global
```

#### <a name="install-preview-versions"></a><span data-ttu-id="08236-122">Installieren von Vorschauversionen</span><span class="sxs-lookup"><span data-stu-id="08236-122">Install preview versions</span></span>

<span data-ttu-id="08236-123">Wenn Sie mit dem folgenden Befehl Vorschauversionen des Teams-Generators installieren möchten:</span><span class="sxs-lookup"><span data-stu-id="08236-123">If you want to install preview versions of the Teams generator with this command:</span></span>

```bash
npm install generator-teams@preview --global
```

## <a name="generate-your-project"></a><span data-ttu-id="08236-124">Erstellen des Projekts</span><span class="sxs-lookup"><span data-stu-id="08236-124">Generate your project</span></span>

<span data-ttu-id="08236-125">Öffnen Sie eine Eingabeaufforderung, und erstellen Sie ein neues Verzeichnis, in dem Sie Ihr Projekt erstellen möchten, und geben Sie `yo teams`in diesem Verzeichnis den Befehl ein.</span><span class="sxs-lookup"><span data-stu-id="08236-125">Open up a command prompt and create a new directory where you want to create your project and in that directory type the command `yo teams`.</span></span> <span data-ttu-id="08236-126">Dadurch wird der Microsoft Teams-apps-Generator gestartet, und Sie werden eine Reihe von Fragen gestellt.</span><span class="sxs-lookup"><span data-stu-id="08236-126">This will start the Teams Apps generator and you will be asked a set of questions.</span></span>

![Yo Teams](~/assets/yeoman-images/teams-first-app-1.png)

<span data-ttu-id="08236-128">Bei der ersten Frage geht es um Ihren Projektnamen, und Sie können ihn unverändert lassen, indem Sie die EINGABETASTE drücken.</span><span class="sxs-lookup"><span data-stu-id="08236-128">The first question is about your project name, you can leave it as is by pressing enter.</span></span> <span data-ttu-id="08236-129">In der nächsten Frage werden Sie gefragt, ob Sie ein neues Verzeichnis erstellen oder die aktuelle verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="08236-129">Next question asks you if you want to create a new directory or use the current one.</span></span> <span data-ttu-id="08236-130">Da wir uns bereits im gewünschten Verzeichnis befinden, drücken Sie einfach die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="08236-130">As we already are in the directory we want, we just press enter.</span></span>

<span data-ttu-id="08236-131">Im folgenden Schritt wird nach einem Titel Ihres Projekts gefragt, dieser Titel wird im Manifest und in der Beschreibung Ihrer APP verwendet.</span><span class="sxs-lookup"><span data-stu-id="08236-131">The following step asks for a title of your project, this title will be used in the manifest and description of your app.</span></span> <span data-ttu-id="08236-132">Anschließend werden Sie nach einem Firmennamen gefragt, der auch im Manifest verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="08236-132">And then you will be asked for a company name, which also will be used in the manifest.</span></span>

<span data-ttu-id="08236-133">In der fünften Frage werden Sie gefragt, welche Version des Manifests Sie verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="08236-133">The fifth question asks you about what version of the manifest you want to use.</span></span> <span data-ttu-id="08236-134">Wählen Sie `v1.5`für dieses Lernprogramm das aktuelle allgemein verfügbare Schema aus.</span><span class="sxs-lookup"><span data-stu-id="08236-134">For this tutorial select `v1.5`, which is the current general available schema.</span></span>

<span data-ttu-id="08236-135">Anschließend werden Sie vom Generator gefragt, welche Elemente dem Projekt hinzugefügt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="08236-135">After this the generator will ask you for what items you want to add to your project.</span></span> <span data-ttu-id="08236-136">Sie können eine einzelne oder eine beliebige Kombination von Elementen auswählen.</span><span class="sxs-lookup"><span data-stu-id="08236-136">You can select a single one or any combination of items.</span></span> <span data-ttu-id="08236-137">Wählen Sie im Moment einfach *eine Registerkarte*aus.</span><span class="sxs-lookup"><span data-stu-id="08236-137">For now, just select *a Tab*.</span></span>

![Elementauswahl](~/assets/yeoman-images/teams-first-app-2.png)

<span data-ttu-id="08236-139">Basierend auf den ausgewählten Elementen werden Sie aufgefordert, eine Reihe von weiteren Fragen zu beantworten.</span><span class="sxs-lookup"><span data-stu-id="08236-139">Based on what items you select, you will be asked a set of follow-up questions.</span></span>

<span data-ttu-id="08236-140">Jetzt müssen Sie eine URL eingeben, von der aus Sie Ihre Lösung hosten werden.</span><span class="sxs-lookup"><span data-stu-id="08236-140">Now you need to enter a URL of where you will host your solution.</span></span> <span data-ttu-id="08236-141">Hierbei kann es sich um eine beliebige URL handeln, standardmäßig schlägt der Generator jedoch eine Azure-Websites-URL vor.</span><span class="sxs-lookup"><span data-stu-id="08236-141">This can be any URL, but by default the generator suggests an Azure Web Sites URL.</span></span>

<span data-ttu-id="08236-142">Der Generator verfügt über eine Vielzahl integrierter erweiterter Funktionen, die Sie aktivieren oder deaktivieren können.</span><span class="sxs-lookup"><span data-stu-id="08236-142">The generator has a lot of built-in advanced features that you can opt-in or opt-out of.</span></span> <span data-ttu-id="08236-143">Nach der URL-Frage werden Sie gefragt, ob Sie Komponententests für Ihre Lösung einschließen möchten, Standard ist ja.</span><span class="sxs-lookup"><span data-stu-id="08236-143">Following the URL question you will be asked if you want to include unit-testing for your solution, default is yes.</span></span> <span data-ttu-id="08236-144">Wenn Sie dies auswählen, verfügt das generierte Projekt über ein Komponententestframework und einige Standardkomponenten Tests für die unterschiedlichen Elemente, die als Gerüstbau verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="08236-144">If you choose this the generated project will have a unit testing framework and some default unit tests for the different items being scaffolded.</span></span> <span data-ttu-id="08236-145">Wählen Sie für dieses Lernprogramm nicht ein Test Framework einschließen aus.</span><span class="sxs-lookup"><span data-stu-id="08236-145">For this tutorial choose not to include a test framework.</span></span>

<span data-ttu-id="08236-146">Um die Protokollierung für Sie zu vereinfachen, werden Sie auch gefragt, ob Sie Azure-Anwendungs Einblicke für die Protokollierung verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="08236-146">In order to make logging easy for you, you will also be asked if you want to use Azure Application Insights for logging.</span></span> <span data-ttu-id="08236-147">Wenn Sie Ja auswählen, müssen Sie einen Azure Application Insights-Schlüssel bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="08236-147">If you choose Yes, you will need to provide a Azure Application Insights key.</span></span> <span data-ttu-id="08236-148">Für dieses Lernprogramm Opt-out der Verwendung von Application Insights.</span><span class="sxs-lookup"><span data-stu-id="08236-148">For this tutorial opt-out of using Application Insights.</span></span>

<span data-ttu-id="08236-149">Die nächste Gruppe von Fragen basiert auf Ihrer Auswahl von Elementen, die zuvor verwendet wurden.</span><span class="sxs-lookup"><span data-stu-id="08236-149">The next set of questions will be based on your selection of items previously.</span></span> <span data-ttu-id="08236-150">Für eine Registerkarte müssen Sie nur einen Namen angeben und optional auswählen, ob Sie diese APP als SharePoint Online Webpart verwenden können möchten.</span><span class="sxs-lookup"><span data-stu-id="08236-150">For a tab you only need to provide a name and optionally choose if you want to be able to use this app as a SharePoint Online web part.</span></span> <span data-ttu-id="08236-151">Nachdem Sie diesen Namen angegeben haben, wird der Generator das Projekt generieren und alle Abhängigkeiten installieren.</span><span class="sxs-lookup"><span data-stu-id="08236-151">Once you have provided this name the generator will generate the project and install all dependencies.</span></span> <span data-ttu-id="08236-152">Dies dauert ein oder zwei Minuten.</span><span class="sxs-lookup"><span data-stu-id="08236-152">This will take a minute or two.</span></span>

## <a name="add-some-code-to-your-tab"></a><span data-ttu-id="08236-153">Hinzufügen von Code zu ihrer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="08236-153">Add some code to your tab</span></span>

<span data-ttu-id="08236-154">Sobald der Generator fertig ist, können Sie die Lösung in Ihrem bevorzugten Code-Editor öffnen.</span><span class="sxs-lookup"><span data-stu-id="08236-154">Once the generator is done you can open up the solution in your favorite code editor.</span></span> <span data-ttu-id="08236-155">Nehmen Sie sich ein oder zwei Minuten und machen Sie sich mit der Organisation des Codes vertraut – Sie können mehr darüber in der Dokumentation zur [Projektstruktur](https://github.com/OfficeDev/generator-teams/wiki/Project-Structure) lesen.</span><span class="sxs-lookup"><span data-stu-id="08236-155">Take a minute or two and familiarize yourself with how the code is organized - you can read more about that in the [Project Structure](https://github.com/OfficeDev/generator-teams/wiki/Project-Structure) documentation.</span></span>

<span data-ttu-id="08236-156">Die Registerkarte befindet sich in der `./src/app/scripts/myFirstAppTab/MyFirstAppTab.tsx` Datei.</span><span class="sxs-lookup"><span data-stu-id="08236-156">Your Tab will be located in the `./src/app/scripts/myFirstAppTab/MyFirstAppTab.tsx` file.</span></span> <span data-ttu-id="08236-157">Dies ist die auf der Registerkarte basierende Reaktions basierte Klasse. suchen `render()` Sie die-Methode, und fügen Sie eine `<PanelBody>` Codezeile innerhalb des Steuerelements, sodass es wie folgt aussieht:</span><span class="sxs-lookup"><span data-stu-id="08236-157">This is the TypeScript React based class for your Tab. Locate the `render()` method and add a line of code inside the `<PanelBody>` control so it looks like this:</span></span>

``` TypeScript
<PanelBody>
    <div style={styles.section}>
    Hello World! Yo Teams rocks!
    </div>
</PanelBody>
```

<span data-ttu-id="08236-158">Speichern Sie die Datei, und kehren Sie zur Eingabeaufforderung zurück.</span><span class="sxs-lookup"><span data-stu-id="08236-158">Save the file and return to the command prompt.</span></span>

## <a name="build-your-app"></a><span data-ttu-id="08236-159">Erstellen Sie Ihre Anwendung</span><span class="sxs-lookup"><span data-stu-id="08236-159">Build your app</span></span>

<span data-ttu-id="08236-160">Sie können nun Ihr Projekt erstellen.</span><span class="sxs-lookup"><span data-stu-id="08236-160">You can now build your project.</span></span> <span data-ttu-id="08236-161">Dies erfolgt in zwei Schritten (oder einem Schritt, siehe unten).</span><span class="sxs-lookup"><span data-stu-id="08236-161">This is done in two steps (or one step, see below).</span></span>

<span data-ttu-id="08236-162">Zunächst müssen Sie die Teams-App-Manifestdatei erstellen, die Sie in Microsoft Teams hochladen/querladen.</span><span class="sxs-lookup"><span data-stu-id="08236-162">First you need to create the Teams App manifest file, that you upload/sideload into Microsoft Teams.</span></span> <span data-ttu-id="08236-163">Dies erfolgt durch die Aufgabe `gulp manifest`"schlucken".</span><span class="sxs-lookup"><span data-stu-id="08236-163">This is done by the Gulp task `gulp manifest`.</span></span> <span data-ttu-id="08236-164">Dadurch wird das Manifest überprüft und eine ZIP-Datei im `./package` Verzeichnis erstellt.</span><span class="sxs-lookup"><span data-stu-id="08236-164">This will validate the manifest and create a zip file in the `./package` directory.</span></span>

<span data-ttu-id="08236-165">Verwenden Sie zum Erstellen der Lösung den `gulp build` Befehl.</span><span class="sxs-lookup"><span data-stu-id="08236-165">To build your solution you use the `gulp build` command.</span></span> <span data-ttu-id="08236-166">Dadurch wird die Lösung in den `./dist` Ordner transstapeln.</span><span class="sxs-lookup"><span data-stu-id="08236-166">This will transpile your solution into the `./dist` folder.</span></span> 

## <a name="run-your-app"></a><span data-ttu-id="08236-167">Ausführen der APP</span><span class="sxs-lookup"><span data-stu-id="08236-167">Run your app</span></span>

<span data-ttu-id="08236-168">Zum Ausführen der App verwenden Sie den `gulp serve` Befehl.</span><span class="sxs-lookup"><span data-stu-id="08236-168">To run your app you use the `gulp serve` command.</span></span> <span data-ttu-id="08236-169">Dadurch wird ein lokaler Webserver erstellt und gestartet, damit Sie Ihre APP testen können.</span><span class="sxs-lookup"><span data-stu-id="08236-169">This will build and start a local web server for you to test your app.</span></span> <span data-ttu-id="08236-170">Mit dem Befehl wird die Anwendung auch dann neu erstellt, wenn Sie eine Datei im Projekt speichern.</span><span class="sxs-lookup"><span data-stu-id="08236-170">The command will also rebuild the application whenever you save a file in your project.</span></span> 

<span data-ttu-id="08236-171">Sie sollten jetzt in der Lage sein, `http://localhost:3007/myFirstAppTab/` zu navigieren, um sicherzustellen, dass Ihre Registerkarte gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="08236-171">You should now be able to browse to `http://localhost:3007/myFirstAppTab/` to ensure that your tab is rendering.</span></span> <span data-ttu-id="08236-172">Jedoch noch nicht in Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="08236-172">However, not in Microsoft Teams yet.</span></span>

![Anzeigen Ihrer Website in einem Browser](~/assets/yeoman-images/teams-first-app-3.png)

## <a name="run-your-app-in-microsoft-teams"></a><span data-ttu-id="08236-174">Ausführen ihrer app in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="08236-174">Run your app in Microsoft Teams</span></span>

<span data-ttu-id="08236-175">Microsoft Teams lässt nicht zu, dass Ihre APP auf localhost gehostet wird, daher müssen Sie Sie entweder in einer öffentlichen URL veröffentlichen oder einen Proxy wie ngrok verwenden.</span><span class="sxs-lookup"><span data-stu-id="08236-175">Microsoft Teams does not allow you to have your app hosted on localhost, so you need to either publish it to a public URL or use a proxy such as ngrok.</span></span>

<span data-ttu-id="08236-176">Eine gute Nachricht ist, dass das Gerüst Projekt diese integrierte ist.</span><span class="sxs-lookup"><span data-stu-id="08236-176">Good news is that the scaffolded project has this built-in.</span></span> <span data-ttu-id="08236-177">Wenn Sie den `gulp ngrok-serve` ngrok-Dienst ausführen, wird im Hintergrund mit einem eindeutigen und öffentlichen DNS-Eintrag gestartet, und es wird auch das Manifest mit dieser eindeutigen URL Verpacken und dann genau dasselbe tun wie `gulp serve`.</span><span class="sxs-lookup"><span data-stu-id="08236-177">When you run `gulp ngrok-serve` the ngrok service will be started in the background, with a unique and public DNS entry and it will also package the manifest with that unique URL and then do the exact same thing as `gulp serve`.</span></span>

<span data-ttu-id="08236-178">Erstellen Sie `gulp ngrok-serve`nach dem Starten ein neues Microsoft Teams-Team, und klicken Sie bei der Erstellung auf den Namen des Teams, um zu den Teams-Einstellungen zu wechseln, und wählen Sie dann *apps*aus.</span><span class="sxs-lookup"><span data-stu-id="08236-178">After running `gulp ngrok-serve`, create a new Microsoft Teams team and when it is created click on the Team name, to go to the teams settings and then select *Apps*.</span></span> <span data-ttu-id="08236-179">In der unteren rechten Ecke sehen Sie einen Link zum *Hochladen einer benutzerdefinierten App*, wählen Sie Sie aus, und navigieren Sie dann zu Ihrem Projekt `package`Ordner und dem Unterordner mit dem Namen.</span><span class="sxs-lookup"><span data-stu-id="08236-179">In the lower right corner you should see a link *Upload a custom app*, select it and then browse to your project folder and the subfolder called `package`.</span></span> <span data-ttu-id="08236-180">Wählen Sie die ZIP-Datei in diesem Ordner aus, und wählen Sie öffnen aus.</span><span class="sxs-lookup"><span data-stu-id="08236-180">Select the zip file in that folder and choose open.</span></span> <span data-ttu-id="08236-181">Ihre APP wird nun in Microsoft Teams quer geladene.</span><span class="sxs-lookup"><span data-stu-id="08236-181">Your App is now sideloaded into Microsoft Teams.</span></span>

![quer geladene-App](~/assets/yeoman-images/teams-first-app-4.png)

<span data-ttu-id="08236-183">Wechseln Sie zurück zum Kanal *Allgemein* , und *+* wählen Sie aus, um eine neue Registerkarte hinzuzufügen. Die Registerkarte sollte in der Liste der Registerkarten angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="08236-183">Go back to the *General* channel and select *+* to add a new Tab. You should see your tab in the list of tabs.</span></span>

![Registerkarte "Konfigurieren"](~/assets/yeoman-images/teams-first-app-5.png)

<span data-ttu-id="08236-185">Klicken Sie auf die Registerkarte, und folgen Sie den Anweisungen zum Hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="08236-185">Choose your tab and follow the instructions to add it.</span></span> <span data-ttu-id="08236-186">Beachten Sie, dass Sie über ein benutzerdefiniertes Konfigurationsdialogfeld verfügen, in dem Sie die Quelle bearbeiten können.</span><span class="sxs-lookup"><span data-stu-id="08236-186">Notice that you have a custom configuration dialog, for which you can edit the source.</span></span> <span data-ttu-id="08236-187">Wählen Sie *Speichern* aus, um die Registerkarte dem Kanal hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="08236-187">Select *Save* to add your tab to the channel.</span></span> <span data-ttu-id="08236-188">Wenn die Registerkarte fertig ist, sollte Sie in Microsoft Teams geladen werden!</span><span class="sxs-lookup"><span data-stu-id="08236-188">Once done your tab should be loaded inside Microsoft Teams!</span></span>

![Registerkarte "Running" in Microsoft Teams](~/assets/yeoman-images/teams-first-app-6.png)

<span data-ttu-id="08236-190">**Congrats! Sie haben ihre erste Microsoft Teams-App erstellt und bereitgestellt.**</span><span class="sxs-lookup"><span data-stu-id="08236-190">**Congrats! You built and deployed your first Microsoft Teams App**</span></span>
