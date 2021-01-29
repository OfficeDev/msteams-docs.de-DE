---
title: Lernprogramm – Erstellen Ihrer ersten App mithilfe des Yeoman-Generators
description: Erfahren Sie, wie Sie mit dem Erstellen von Microsoft Teams-Apps mit dem Yeoman-Generator beginnen.
keywords: Erste Schritte node.js nodejs yeoman
ms.topic: tutorial
ms.custom: scenarios:getting-started
ms.openlocfilehash: f7f0fb3ba1be28dfa7d343be3af9d122b4ad090d
ms.sourcegitcommit: fa64b83c0b534bf7a89f256880d5b5ca193e4b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/28/2021
ms.locfileid: "50037004"
---
# <a name="create-your-first-microsoft-teams-app-using-the-yeoman-generator"></a><span data-ttu-id="df5cc-104">Erstellen Ihrer ersten Microsoft Teams-App mithilfe des Yeoman-Generators</span><span class="sxs-lookup"><span data-stu-id="df5cc-104">Create your first Microsoft Teams app using the Yeoman generator</span></span>

>[!Note]
><span data-ttu-id="df5cc-105">Dieses Lernprogramm stammt aus dem [Yeoman-Generator für Teams-Wiki.](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App)</span><span class="sxs-lookup"><span data-stu-id="df5cc-105">This tutorial comes from the [Yeoman generator for Teams wiki](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App).</span></span>

<span data-ttu-id="df5cc-106">In diesem Lernprogramm werden wir durch die Erstellung Ihrer ersten Microsoft Teams-App mithilfe des Microsoft Teams-Yeoman-Generators gehen.</span><span class="sxs-lookup"><span data-stu-id="df5cc-106">In this tutorial we will walk through creating your very first Microsoft Teams app using the Microsoft Teams Yeoman generator.</span></span> <span data-ttu-id="df5cc-107">Es wird davon ausgegangen, dass Sie über ein Teams-Konto verfügen, das das [Querladen von](~/concepts/build-and-test/prepare-your-o365-tenant.md)Apps ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="df5cc-107">It assumes that you have a Teams account that allows [app sideloading](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>

![Yeoman-Generator-Git](~/assets/yeoman-demo.gif)

## <a name="setup-and-prepare-your-machine"></a><span data-ttu-id="df5cc-109">Einrichten und Vorbereiten des Computers</span><span class="sxs-lookup"><span data-stu-id="df5cc-109">Setup and prepare your machine</span></span>

<span data-ttu-id="df5cc-110">Sie müssen Folgendes auf Ihrem Computer installieren, bevor Sie mit der Verwendung des Yeoman-Generators beginnen.</span><span class="sxs-lookup"><span data-stu-id="df5cc-110">You need to install the following on your machine before starting to use the Yeoman generator.</span></span>

### <a name="install-nodejs"></a><span data-ttu-id="df5cc-111">Installieren von Node.js</span><span class="sxs-lookup"><span data-stu-id="df5cc-111">Install Node.js</span></span>

<span data-ttu-id="df5cc-112">Sie müssen die Node.js auf Ihrem Computer installiert haben.</span><span class="sxs-lookup"><span data-stu-id="df5cc-112">You need to have Node.js installed on your machine.</span></span> <span data-ttu-id="df5cc-113">Sie sollten die neueste [LTS-Version verwenden.](https://nodejs.org)</span><span class="sxs-lookup"><span data-stu-id="df5cc-113">You should use the latest [LTS version](https://nodejs.org).</span></span>

### <a name="install-a-code-editor"></a><span data-ttu-id="df5cc-114">Installieren eines Code-Editors</span><span class="sxs-lookup"><span data-stu-id="df5cc-114">Install a code editor</span></span>

<span data-ttu-id="df5cc-115">Sie benötigen auch einen Code-Editor, und sie können den von Ihnen bevorzugten Texteditor verwenden.</span><span class="sxs-lookup"><span data-stu-id="df5cc-115">You also need a code editor, feel free to use whatever text editor you prefer.</span></span> <span data-ttu-id="df5cc-116">Die meisten dieser Dokumentationen und Screenshots beziehen sich jedoch auf die Verwendung [Visual Studio Code .](https://code.visualstudio.com)</span><span class="sxs-lookup"><span data-stu-id="df5cc-116">However most of this documentation and screenshots refer to using [Visual Studio Code](https://code.visualstudio.com).</span></span>

### <a name="install-yeoman-and-gulp-cli"></a><span data-ttu-id="df5cc-117">Installieren von Yeoman und Gulp CLI</span><span class="sxs-lookup"><span data-stu-id="df5cc-117">Install Yeoman and Gulp CLI</span></span>

<span data-ttu-id="df5cc-118">Um mithilfe des Teams-Generators ein Gerüst für Projekte erstellen zu können, müssen Sie das Tool Yeoman sowie den Gulp CLI-Task-Manager installieren.</span><span class="sxs-lookup"><span data-stu-id="df5cc-118">To be able to scaffold projects using the Teams generator you need to install the Yeoman tool as well as the Gulp CLI task manager.</span></span>

<span data-ttu-id="df5cc-119">Öffnen Sie eine Eingabeaufforderung, und geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="df5cc-119">Open up a command prompt and type the following:</span></span>

```bash
npm install yo gulp-cli --global
```

## <a name="install-the-generator"></a><span data-ttu-id="df5cc-120">Installieren des Generators</span><span class="sxs-lookup"><span data-stu-id="df5cc-120">Install the generator</span></span>

<span data-ttu-id="df5cc-121">Installieren Sie den Teams-Yeoman-Generator mit dem folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="df5cc-121">Install the Teams Yeoman generator with the following command:</span></span>

```bash
npm install generator-teams --global
```

<span data-ttu-id="df5cc-122">Führen Sie den folgenden Befehl aus, um Vorschauversionen des Generators zu installieren:</span><span class="sxs-lookup"><span data-stu-id="df5cc-122">To install preview versions of the generator, run this command:</span></span>

```bash
npm install generator-teams@preview --global
```

## <a name="generate-your-project"></a><span data-ttu-id="df5cc-123">Generieren Des Projekts</span><span class="sxs-lookup"><span data-stu-id="df5cc-123">Generate your project</span></span>

<span data-ttu-id="df5cc-124">Öffnen Sie eine Eingabeaufforderung, und erstellen Sie ein neues Verzeichnis, in dem Sie Ihr Projekt erstellen möchten, und führen Sie in diesem Verzeichnis den Befehl `yo teams` aus.</span><span class="sxs-lookup"><span data-stu-id="df5cc-124">Open up a command prompt and create a new directory where you want to create your project and in that directory run the command `yo teams`.</span></span>

<span data-ttu-id="df5cc-125">Dadurch wird der Generator gestartet, der Sie mit einer Reihe von Fragen anfordert.</span><span class="sxs-lookup"><span data-stu-id="df5cc-125">This starts the generator, which prompts you with a set of questions.</span></span>

![yo teams](~/assets/yeoman-images/teams-first-app-1.png)

<span data-ttu-id="df5cc-127">Die erste Frage ist der Projektname. Sie können ihn durch Drücken der EINGABETASTE so be lassen, wie er ist.</span><span class="sxs-lookup"><span data-stu-id="df5cc-127">The first question is about your project name, you can leave it as is by pressing enter.</span></span> <span data-ttu-id="df5cc-128">Die nächste Frage stellt Ihnen die Frage, ob Sie ein neues Verzeichnis erstellen oder das aktuelle Verzeichnis verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="df5cc-128">Next question asks you if you want to create a new directory or use the current one.</span></span> <span data-ttu-id="df5cc-129">Da wir uns bereits in dem Verzeichnis befinden, das wir verwenden möchten, drücken wir einfach die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="df5cc-129">As we already are in the directory we want, we just press enter.</span></span>

<span data-ttu-id="df5cc-130">Im folgenden Schritt wird nach einem Titel Ihres Projekts gefragt. Dieser Titel wird im Manifest und in der Beschreibung Ihrer App verwendet.</span><span class="sxs-lookup"><span data-stu-id="df5cc-130">The following step asks for a title of your project, this title will be used in the manifest and description of your app.</span></span> <span data-ttu-id="df5cc-131">Anschließend werden Sie nach einem Firmennamen gefragt, der auch im Manifest verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="df5cc-131">And then you will be asked for a company name, which also will be used in the manifest.</span></span>

<span data-ttu-id="df5cc-132">In der fünften Frage werden Sie gefragt, welche Version des Manifests Sie verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="df5cc-132">The fifth question asks you about what version of the manifest you want to use.</span></span> <span data-ttu-id="df5cc-133">Wählen Sie für dieses `v1.5` Lernprogramm das aktuelle allgemein verfügbare Schema aus.</span><span class="sxs-lookup"><span data-stu-id="df5cc-133">For this tutorial select `v1.5`, which is the current general available schema.</span></span>

<span data-ttu-id="df5cc-134">Danach fragt der Generator Sie nach den Elementen, die Sie Ihrem Projekt hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="df5cc-134">After this the generator will ask you for what items you want to add to your project.</span></span> <span data-ttu-id="df5cc-135">Sie können ein einzelnes oder eine beliebige Kombination von Elementen auswählen.</span><span class="sxs-lookup"><span data-stu-id="df5cc-135">You can select a single one or any combination of items.</span></span> <span data-ttu-id="df5cc-136">For now, just select *a Tab*.</span><span class="sxs-lookup"><span data-stu-id="df5cc-136">For now, just select *a Tab*.</span></span>

![Elementauswahl](~/assets/yeoman-images/teams-first-app-2.png)

<span data-ttu-id="df5cc-138">Basierend auf den ausgewählten Elementen werden Ihnen eine Reihe von Nachschlagefragen gestellt.</span><span class="sxs-lookup"><span data-stu-id="df5cc-138">Based on what items you select, you will be asked a set of follow-up questions.</span></span>

<span data-ttu-id="df5cc-139">Jetzt müssen Sie eine URL eingeben, unter der Sie Ihre Lösung hosten.</span><span class="sxs-lookup"><span data-stu-id="df5cc-139">Now you need to enter a URL of where you will host your solution.</span></span> <span data-ttu-id="df5cc-140">Dies kann eine beliebige URL sein, der Generator schlägt jedoch standardmäßig eine Azure-Website-URL vor.</span><span class="sxs-lookup"><span data-stu-id="df5cc-140">This can be any URL, but by default the generator suggests an Azure Web Sites URL.</span></span>

<span data-ttu-id="df5cc-141">Der Generator verfügt über viele integrierte erweiterte Features, für die Sie sich entscheiden oder abmelden können.</span><span class="sxs-lookup"><span data-stu-id="df5cc-141">The generator has a lot of built-in advanced features that you can opt-in or opt-out of.</span></span> <span data-ttu-id="df5cc-142">Nach der URL-Frage, die Sie fragen, ob Sie Komponententests für Ihre Lösung hinzufügen möchten, ist der Standardwert "Ja".</span><span class="sxs-lookup"><span data-stu-id="df5cc-142">Following the URL question you will be asked if you want to include unit-testing for your solution, default is yes.</span></span> <span data-ttu-id="df5cc-143">Wenn Sie dies auswählen, verfügt das generierte Projekt über ein Komponententestframework und einige Standardeinheitstests für die verschiedenen Elemente, die Gerüste erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="df5cc-143">If you choose this the generated project will have a unit testing framework and some default unit tests for the different items being scaffolded.</span></span> <span data-ttu-id="df5cc-144">In diesem Lernprogramm wird kein Testframework verwendet.</span><span class="sxs-lookup"><span data-stu-id="df5cc-144">For this tutorial choose not to include a test framework.</span></span>

<span data-ttu-id="df5cc-145">Um Die Protokollierung für Sie einfach zu machen, werden Sie auch gefragt, ob Sie Azure Application Insights für die Protokollierung verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="df5cc-145">In order to make logging easy for you, you will also be asked if you want to use Azure Application Insights for logging.</span></span> <span data-ttu-id="df5cc-146">Wenn Sie "Ja" auswählen, müssen Sie einen Azure Application Insights-Schlüssel bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="df5cc-146">If you choose Yes, you will need to provide a Azure Application Insights key.</span></span> <span data-ttu-id="df5cc-147">In diesem Lernprogramm können Sie die Verwendung von Application Insights abmelden.</span><span class="sxs-lookup"><span data-stu-id="df5cc-147">For this tutorial opt-out of using Application Insights.</span></span>

<span data-ttu-id="df5cc-148">Die nächsten Fragen basieren auf der zuvor von Ihnen getroffenen Auswahl von Elementen.</span><span class="sxs-lookup"><span data-stu-id="df5cc-148">The next set of questions will be based on your selection of items previously.</span></span> <span data-ttu-id="df5cc-149">Für eine Registerkarte müssen Sie nur einen Namen eingeben und optional auswählen, ob Sie diese App als SharePoint Online-Web part verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="df5cc-149">For a tab you only need to provide a name and optionally choose if you want to be able to use this app as a SharePoint Online web part.</span></span> <span data-ttu-id="df5cc-150">Nachdem Sie diesen Namen angegeben haben, generiert der Generator das Projekt und installiert alle Abhängigkeiten.</span><span class="sxs-lookup"><span data-stu-id="df5cc-150">Once you have provided this name the generator will generate the project and install all dependencies.</span></span> <span data-ttu-id="df5cc-151">Dies dauert ein oder zwei Minuten.</span><span class="sxs-lookup"><span data-stu-id="df5cc-151">This will take a minute or two.</span></span>

## <a name="add-some-code-to-your-tab"></a><span data-ttu-id="df5cc-152">Hinzufügen von Code zu Ihrer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="df5cc-152">Add some code to your tab</span></span>

<span data-ttu-id="df5cc-153">Sobald der Generator fertig ist, können Sie die Lösung in Ihrem bevorzugten Codeeditor öffnen.</span><span class="sxs-lookup"><span data-stu-id="df5cc-153">Once the generator is done you can open up the solution in your favorite code editor.</span></span> <span data-ttu-id="df5cc-154">Nehmen Sie sich ein oder zwei Minuten Zeit und machen Sie sich mit der Struktur des Codes vertraut . Weitere Informationen dazu finden Sie in der [Dokumentation zur Projektstruktur.](https://github.com/OfficeDev/generator-teams/wiki/Project-Structure)</span><span class="sxs-lookup"><span data-stu-id="df5cc-154">Take a minute or two and familiarize yourself with how the code is organized - you can read more about that in the [Project Structure](https://github.com/OfficeDev/generator-teams/wiki/Project-Structure) documentation.</span></span>

<span data-ttu-id="df5cc-155">Die Registerkarte befindet sich in der `./src/app/scripts/myFirstAppTab/MyFirstAppTab.tsx` Datei.</span><span class="sxs-lookup"><span data-stu-id="df5cc-155">Your Tab will be located in the `./src/app/scripts/myFirstAppTab/MyFirstAppTab.tsx` file.</span></span> <span data-ttu-id="df5cc-156">Dies ist die TypeScript React-basierte Klasse für Ihre Registerkarte. Suchen Sie die Methode, und fügen Sie eine Codezeile innerhalb des Steuerelements hinzu, `render()` damit sie wie hier `<PanelBody>` aussieht:</span><span class="sxs-lookup"><span data-stu-id="df5cc-156">This is the TypeScript React based class for your Tab. Locate the `render()` method and add a line of code inside the `<PanelBody>` control so it looks like this:</span></span>

``` TypeScript
<PanelBody>
    <div style={styles.section}>
    Hello World! Yo Teams rocks!
    </div>
</PanelBody>
```

<span data-ttu-id="df5cc-157">Speichern Sie die Datei, und kehren Sie zur Eingabeaufforderung zurück.</span><span class="sxs-lookup"><span data-stu-id="df5cc-157">Save the file and return to the command prompt.</span></span>

## <a name="build-your-app"></a><span data-ttu-id="df5cc-158">Erstellen Sie Ihre Anwendung</span><span class="sxs-lookup"><span data-stu-id="df5cc-158">Build your app</span></span>

<span data-ttu-id="df5cc-159">Sie können nun Ihr Projekt erstellen.</span><span class="sxs-lookup"><span data-stu-id="df5cc-159">You can now build your project.</span></span> <span data-ttu-id="df5cc-160">Dies erfolgt in zwei Schritten (oder in einem Schritt, siehe unten).</span><span class="sxs-lookup"><span data-stu-id="df5cc-160">This is done in two steps (or one step, see below).</span></span>

<span data-ttu-id="df5cc-161">Zuerst müssen Sie die Teams-App-Manifestdatei erstellen, die Sie in Microsoft Teams hochladen/querladen.</span><span class="sxs-lookup"><span data-stu-id="df5cc-161">First you need to create the Teams App manifest file, that you upload/sideload into Microsoft Teams.</span></span> <span data-ttu-id="df5cc-162">Dies erfolgt durch die Gulp-Aufgabe. `gulp manifest`</span><span class="sxs-lookup"><span data-stu-id="df5cc-162">This is done by the Gulp task `gulp manifest`.</span></span> <span data-ttu-id="df5cc-163">Dadurch wird das Manifest überprüft und eine ZIP-Datei im Verzeichnis `./package` erstellt.</span><span class="sxs-lookup"><span data-stu-id="df5cc-163">This will validate the manifest and create a zip file in the `./package` directory.</span></span>

<span data-ttu-id="df5cc-164">Um Ihre Lösung zu erstellen, verwenden Sie den `gulp build` Befehl.</span><span class="sxs-lookup"><span data-stu-id="df5cc-164">To build your solution you use the `gulp build` command.</span></span> <span data-ttu-id="df5cc-165">Dadurch wird Ihre Lösung in den Ordner `./dist` transpiliert.</span><span class="sxs-lookup"><span data-stu-id="df5cc-165">This will transpile your solution into the `./dist` folder.</span></span> 

## <a name="run-your-app"></a><span data-ttu-id="df5cc-166">Ausführen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="df5cc-166">Run your app</span></span>

<span data-ttu-id="df5cc-167">Um Ihre App auszuführen, verwenden Sie den `gulp serve` Befehl.</span><span class="sxs-lookup"><span data-stu-id="df5cc-167">To run your app you use the `gulp serve` command.</span></span> <span data-ttu-id="df5cc-168">Dadurch erstellen und starten Sie einen lokalen Webserver, auf dem Sie Ihre App testen können.</span><span class="sxs-lookup"><span data-stu-id="df5cc-168">This will build and start a local web server for you to test your app.</span></span> <span data-ttu-id="df5cc-169">Der Befehl erstellt die Anwendung auch neu, wenn Sie eine Datei in Ihrem Projekt speichern.</span><span class="sxs-lookup"><span data-stu-id="df5cc-169">The command will also rebuild the application whenever you save a file in your project.</span></span> 

<span data-ttu-id="df5cc-170">Sie sollten nun in der Lage sein, zu navigieren, `http://localhost:3007/myFirstAppTab/` um sicherzustellen, dass die Registerkarte gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="df5cc-170">You should now be able to browse to `http://localhost:3007/myFirstAppTab/` to ensure that your tab is rendering.</span></span> <span data-ttu-id="df5cc-171">Allerdings noch nicht in Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="df5cc-171">However, not in Microsoft Teams yet.</span></span>

![Anzeigen Ihrer Website in einem Browser](~/assets/yeoman-images/teams-first-app-3.png)

## <a name="run-your-app-in-microsoft-teams"></a><span data-ttu-id="df5cc-173">Ausführen Ihrer App in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="df5cc-173">Run your app in Microsoft Teams</span></span>

<span data-ttu-id="df5cc-174">Microsoft Teams lässt nicht zu, dass Ihre App auf localhost gehostet wird. Daher müssen Sie sie entweder unter einer öffentlichen URL veröffentlichen oder einen Proxy wie ngrok verwenden.</span><span class="sxs-lookup"><span data-stu-id="df5cc-174">Microsoft Teams does not allow you to have your app hosted on localhost, so you need to either publish it to a public URL or use a proxy such as ngrok.</span></span>

<span data-ttu-id="df5cc-175">Eine gute Nachricht ist, dass das Gerüstprojekt über dieses integrierte Projekt verfügt.</span><span class="sxs-lookup"><span data-stu-id="df5cc-175">Good news is that the scaffolded project has this built-in.</span></span> <span data-ttu-id="df5cc-176">Wenn Sie den ngrok-Dienst ausführen, wird er im Hintergrund mit einem eindeutigen und öffentlichen DNS-Eintrag gestartet. Außerdem wird das Manifest mit dieser eindeutigen URL gepackt und dann genau dasselbe wie `gulp ngrok-serve` `gulp serve` ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="df5cc-176">When you run `gulp ngrok-serve` the ngrok service will be started in the background, with a unique and public DNS entry and it will also package the manifest with that unique URL and then do the exact same thing as `gulp serve`.</span></span>

<span data-ttu-id="df5cc-177">Erstellen Sie nach der Ausführung ein neues Microsoft Teams-Team, und klicken Sie bei seiner Erstellung auf den Teamnamen, um zu den Teameinstellungen zu wechseln und dann `gulp ngrok-serve` *Apps auszuwählen.*</span><span class="sxs-lookup"><span data-stu-id="df5cc-177">After running `gulp ngrok-serve`, create a new Microsoft Teams team and when it is created click on the Team name, to go to the teams settings and then select *Apps*.</span></span> <span data-ttu-id="df5cc-178">In der unteren rechten Ecke sollte ein Link zum *Hochladen* einer benutzerdefinierten App angezeigt werden. Wählen Sie ihn aus, und navigieren Sie dann zu Ihrem Projektordner und dem aufgerufenen `package` Unterordner.</span><span class="sxs-lookup"><span data-stu-id="df5cc-178">In the lower right corner you should see a link *Upload a custom app*, select it and then browse to your project folder and the subfolder called `package`.</span></span> <span data-ttu-id="df5cc-179">Wählen Sie die ZIP-Datei in diesem Ordner aus, und wählen Sie "Öffnen" aus.</span><span class="sxs-lookup"><span data-stu-id="df5cc-179">Select the zip file in that folder and choose open.</span></span> <span data-ttu-id="df5cc-180">Ihre App wird nun in Microsoft Teams sideloaded.</span><span class="sxs-lookup"><span data-stu-id="df5cc-180">Your App is now sideloaded into Microsoft Teams.</span></span>

![Sideloaded app](~/assets/yeoman-images/teams-first-app-4.png)

<span data-ttu-id="df5cc-182">Wechseln Sie zurück zum Kanal *"Allgemein",* und wählen *+* Sie aus, um eine neue Registerkarte hinzuzufügen. Ihre Registerkarte sollte in der Liste der Registerkarten angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="df5cc-182">Go back to the *General* channel and select *+* to add a new Tab. You should see your tab in the list of tabs.</span></span>

![Registerkarte konfigurieren](~/assets/yeoman-images/teams-first-app-5.png)

<span data-ttu-id="df5cc-184">Wählen Sie Ihre Registerkarte aus, und folgen Sie den Anweisungen, um sie hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="df5cc-184">Choose your tab and follow the instructions to add it.</span></span> <span data-ttu-id="df5cc-185">Beachten Sie, dass Sie über ein benutzerdefiniertes Konfigurationsdialogfeld verfügen, für das Sie die Quelle bearbeiten können.</span><span class="sxs-lookup"><span data-stu-id="df5cc-185">Notice that you have a custom configuration dialog, for which you can edit the source.</span></span> <span data-ttu-id="df5cc-186">Wählen *Sie "Speichern"* aus, um ihre Registerkarte zum Kanal hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="df5cc-186">Select *Save* to add your tab to the channel.</span></span> <span data-ttu-id="df5cc-187">Sobald Sie fertig sind, sollte Ihre Registerkarte in Microsoft Teams geladen werden!</span><span class="sxs-lookup"><span data-stu-id="df5cc-187">Once done your tab should be loaded inside Microsoft Teams!</span></span>

![Ausführen der Registerkarte in Teams](~/assets/yeoman-images/teams-first-app-6.png)

<span data-ttu-id="df5cc-189">**Cong kongenial! Sie haben Ihre erste Microsoft Teams-App erstellt und bereitgestellt.**</span><span class="sxs-lookup"><span data-stu-id="df5cc-189">**Congrats! You built and deployed your first Microsoft Teams app**</span></span>
