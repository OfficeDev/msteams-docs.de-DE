---
title: Tutorial - Erstellen Sie Ihre erste App mit dem Yeoman Generator
description: Erfahren Sie, wie Sie mit dem Erstellen Microsoft Teams Apps mit dem Yeoman-Generator beginnen.
keywords: erste Schritte node.js nodejs yeoman
localization_priority: Normal
ms.topic: tutorial
ms.custom: scenarios:getting-started
ms.openlocfilehash: 96a4f64d487e1d16bf25abd978759fedeac1061c
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566824"
---
# <a name="create-your-first-microsoft-teams-app-using-the-yeoman-generator"></a><span data-ttu-id="8a022-104">Erstellen Sie Ihre erste Microsoft Teams-App mit dem Yeoman-Generator</span><span class="sxs-lookup"><span data-stu-id="8a022-104">Create your first Microsoft Teams app using the Yeoman generator</span></span>

> [!Note]
> <span data-ttu-id="8a022-105">Dieses Tutorial kommt vom [Yeoman Generator für Teams Wiki](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App).</span><span class="sxs-lookup"><span data-stu-id="8a022-105">This tutorial comes from the [Yeoman generator for Teams wiki](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App).</span></span>

<span data-ttu-id="8a022-106">In diesem Tutorial werden wir durch die Erstellung Ihrer allerersten Microsoft Teams App mit dem Microsoft Teams Yeoman Generator gehen.</span><span class="sxs-lookup"><span data-stu-id="8a022-106">In this tutorial, we will walk through creating your very first Microsoft Teams app using the Microsoft Teams Yeoman generator.</span></span> <span data-ttu-id="8a022-107">Es führt Sie auch durch den Prozess der Aktualisierung Ihrer Teams mit dem Yeoman-Generator.</span><span class="sxs-lookup"><span data-stu-id="8a022-107">It also walks you through the process of upgrading your Teams using the Yeoman generator.</span></span> <span data-ttu-id="8a022-108">Voraussetzung für den Einstieg in dieses Tutorial ist, dass Sie über ein Teams Konto verfügen, das das [Sideloading](~/concepts/build-and-test/prepare-your-o365-tenant.md)von Apps ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="8a022-108">The prerequisite to start with this tutorial is that you have a Teams account that allows [app sideloading](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>

![yeoman generator git](~/assets/yeoman-demo.gif)

## <a name="setup-and-prepare-your-machine"></a><span data-ttu-id="8a022-110">Einrichten und Vorbereiten Ihrer Maschine</span><span class="sxs-lookup"><span data-stu-id="8a022-110">Setup and prepare your machine</span></span>

<span data-ttu-id="8a022-111">Sie müssen Folgendes auf Ihrem Computer installieren, bevor Sie mit der Verwendung des Yeoman-Generators beginnen.</span><span class="sxs-lookup"><span data-stu-id="8a022-111">You need to install the following on your machine before starting to use the Yeoman generator.</span></span>

### <a name="install-nodejs"></a><span data-ttu-id="8a022-112">Installieren von Node.js</span><span class="sxs-lookup"><span data-stu-id="8a022-112">Install Node.js</span></span>

<span data-ttu-id="8a022-113">Sie müssen Node.js auf Ihrem Computer installiert haben.</span><span class="sxs-lookup"><span data-stu-id="8a022-113">You need to have Node.js installed on your machine.</span></span> <span data-ttu-id="8a022-114">Sie sollten die neueste [LTS-Version](https://nodejs.org)verwenden.</span><span class="sxs-lookup"><span data-stu-id="8a022-114">You should use the latest [LTS version](https://nodejs.org).</span></span>

### <a name="install-a-code-editor"></a><span data-ttu-id="8a022-115">Installieren eines Code-Editors</span><span class="sxs-lookup"><span data-stu-id="8a022-115">Install a code editor</span></span>

<span data-ttu-id="8a022-116">Sie benötigen einen Code-Editor.</span><span class="sxs-lookup"><span data-stu-id="8a022-116">You need a code editor.</span></span> <span data-ttu-id="8a022-117">Die meisten dieser Dokumentationen und Bilder beziehen sich auf die Verwendung [von Visual Studio Code](https://code.visualstudio.com).</span><span class="sxs-lookup"><span data-stu-id="8a022-117">Most of this documentation and images refer to using [Visual Studio Code](https://code.visualstudio.com).</span></span> <span data-ttu-id="8a022-118">Sie können jedoch den gewünschten Texteditor verwenden.</span><span class="sxs-lookup"><span data-stu-id="8a022-118">However, feel free to use whatever text editor you prefer.</span></span>

### <a name="install-yeoman-and-gulp-cli"></a><span data-ttu-id="8a022-119">Installieren von Yeoman und Gulp CLI</span><span class="sxs-lookup"><span data-stu-id="8a022-119">Install Yeoman and Gulp CLI</span></span>

<span data-ttu-id="8a022-120">Um Gerüstprojekte mit dem Generator zu erstellen, müssen Sie das Yeoman-Tool und den Gulp CLI-Task-Manager installieren.</span><span class="sxs-lookup"><span data-stu-id="8a022-120">To scaffold projects using the generator, you must install the Yeoman tool and Gulp CLI task manager.</span></span>

<span data-ttu-id="8a022-121">Öffnen Sie eine Eingabeaufforderung, und geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="8a022-121">Open up a command prompt and type the following:</span></span>

```bash
npm install yo gulp-cli --global
```

## <a name="install-the-generator"></a><span data-ttu-id="8a022-122">Installieren des Generators</span><span class="sxs-lookup"><span data-stu-id="8a022-122">Install the generator</span></span>

<span data-ttu-id="8a022-123">Installieren Sie den Teams Yeoman-Generator mit dem folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="8a022-123">Install the Teams Yeoman generator with the following command:</span></span>

```bash
npm install generator-teams --global
```

<span data-ttu-id="8a022-124">Installieren Sie die Vorschauversion des Generators mit dem folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="8a022-124">Install the preview version of the generator with the following command:</span></span>

```bash
npm install generator-teams@preview --global
```

## <a name="generate-your-project"></a><span data-ttu-id="8a022-125">Generieren Sie Ihr Projekt</span><span class="sxs-lookup"><span data-stu-id="8a022-125">Generate your project</span></span>

<span data-ttu-id="8a022-126">In diesem Abschnitt werden die Schritte zum Generieren des Projekts erläutert.</span><span class="sxs-lookup"><span data-stu-id="8a022-126">This section walks you through the steps for generating your project.</span></span>

<span data-ttu-id="8a022-127">**So generieren Sie Ihr Projekt**</span><span class="sxs-lookup"><span data-stu-id="8a022-127">**To generate your project**</span></span>

1. <span data-ttu-id="8a022-128">Öffnen Sie eine Eingabeaufforderung, und erstellen Sie ein neues Verzeichnis, in dem Sie Ihr Projekt erstellen möchten, und führen Sie in diesem Verzeichnis den Befehl `yo teams` aus.</span><span class="sxs-lookup"><span data-stu-id="8a022-128">Open up a command prompt and create a new directory where you want to create your project, and in that directory run the command `yo teams`.</span></span> <span data-ttu-id="8a022-129">Der Generator startet.</span><span class="sxs-lookup"><span data-stu-id="8a022-129">The generator starts.</span></span>
1. <span data-ttu-id="8a022-130">Beantworten Sie den Satz von Fragen, die vom Generator gestellt werden:</span><span class="sxs-lookup"><span data-stu-id="8a022-130">Respond to the set of questions prompted by the generator:</span></span>

   ![yo-Teams](~/assets/yeoman-images/teams-first-app-1.png)

   1. <span data-ttu-id="8a022-132">Die erste Frage betrifft Ihren Projektnamen, Sie können ihn wie folgt belassen, indem Sie die Eingabetaste drücken.</span><span class="sxs-lookup"><span data-stu-id="8a022-132">The first question is about your project name, you can leave it as is by pressing enter.</span></span>
   1. <span data-ttu-id="8a022-133">Die nächste Frage fragt Sie, ob Sie ein neues Verzeichnis erstellen oder das aktuelle verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="8a022-133">Next question asks you if you want to create a new directory or use the current one.</span></span> <span data-ttu-id="8a022-134">Da Sie sich bereits in dem gewünschten Verzeichnis befinden, drücken Sie einfach die Eingabetaste.</span><span class="sxs-lookup"><span data-stu-id="8a022-134">As you are already in the directory you want, just press enter.</span></span>
   1. <span data-ttu-id="8a022-135">Geben Sie in der nächsten Frage den Titel Ihres Projekts ein.</span><span class="sxs-lookup"><span data-stu-id="8a022-135">In the next question, type the title of your project.</span></span> <span data-ttu-id="8a022-136">Dieser Titel wird im Manifest und in der Beschreibung Ihrer App verwendet.</span><span class="sxs-lookup"><span data-stu-id="8a022-136">This title will be used in the manifest and description of your app.</span></span> 
   1. <span data-ttu-id="8a022-137">Als Nächstes werden Sie nach einem Firmennamen gefragt, der auch im Manifest verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="8a022-137">Next, you will be asked for a company name, which also will be used in the manifest.</span></span>
   1. <span data-ttu-id="8a022-138">In der fünften Frage werden Sie gefragt, welche Version des Manifests Sie verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="8a022-138">The fifth question asks you about what version of the manifest you want to use.</span></span> <span data-ttu-id="8a022-139">Wählen Sie für dieses Tutorial `v1.5` aus, welches das aktuelle allgemeine verfügbare Schema ist.</span><span class="sxs-lookup"><span data-stu-id="8a022-139">For this tutorial select `v1.5`, which is the current general available schema.</span></span>
   1. <span data-ttu-id="8a022-140">Als Nächstes fragt der Generator Sie nach den Elementen, die Sie Ihrem Projekt hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="8a022-140">Next, the generator will ask you for what items you want to add to your project.</span></span> <span data-ttu-id="8a022-141">Sie können eine einzelne oder eine beliebige Kombination von Elementen auswählen.</span><span class="sxs-lookup"><span data-stu-id="8a022-141">You can select a single one or any combination of items.</span></span> <span data-ttu-id="8a022-142">Wählen Sie für diese Tutorials einfach *eine Registerkarte* aus:</span><span class="sxs-lookup"><span data-stu-id="8a022-142">For this tutorials, just select *a Tab*:</span></span>

    ![Artikelauswahl](~/assets/yeoman-images/teams-first-app-2.png)

1. <span data-ttu-id="8a022-144">Antworten Sie auf den nächsten Satz von Folgefragen, die basierend auf den in Schritt 2 ausgewählten Elementen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="8a022-144">Respond to the next set of follow-up questions that appear based on the items you selected in step 2.</span></span>
1. <span data-ttu-id="8a022-145">Geben Sie eine URL ein, unter der Sie Ihre Lösung hosten möchten.</span><span class="sxs-lookup"><span data-stu-id="8a022-145">Enter a URL of where you will host your solution.</span></span> 

   > [!NOTE]
   > <span data-ttu-id="8a022-146">Die URL kann eine beliebige URL sein, aber standardmäßig schlägt der Generator eine Azure-Website-URL vor.</span><span class="sxs-lookup"><span data-stu-id="8a022-146">The URL can be any URL, but by default the generator suggests an Azure web site URL.</span></span>

1. <span data-ttu-id="8a022-147">Bestätigen Sie in der nächsten Frage, ob Sie Komponententests für Ihre Lösung einschließen möchten.</span><span class="sxs-lookup"><span data-stu-id="8a022-147">In the next question, confirm if you want to include unit-testing for your solution.</span></span> <span data-ttu-id="8a022-148">Die Standardantwort lautet *yes*.</span><span class="sxs-lookup"><span data-stu-id="8a022-148">The default response is *yes*.</span></span> <span data-ttu-id="8a022-149">Wenn Sie Komponententests einschließen, verfügt das generierte Projekt über ein Komponententestframework und einige Standardkomponententests für die verschiedenen Elemente, die auf Gerüsten erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="8a022-149">If you choose to include unit-testing, the generated project will have a unit testing framework and some default unit tests for the different items being scaffolded.</span></span> 
   > [!NOTE]
   > * <span data-ttu-id="8a022-150">Für dieses Tutorial sollten Sie kein Testframework enthalten.</span><span class="sxs-lookup"><span data-stu-id="8a022-150">For this tutorial choose not to include a test framework.</span></span>
   > * <span data-ttu-id="8a022-151">Der Generator hat viele integrierte erweiterte Funktionen, die Sie opt-in oder Opt-out können.</span><span class="sxs-lookup"><span data-stu-id="8a022-151">The generator has a lot of built-in advanced features that you can opt-in or opt-out of.</span></span>

1. <span data-ttu-id="8a022-152">Um die Anmeldung für Sie zu vereinfachen, werden Sie auch gefragt, ob Sie Azure Application Insights für die Anmeldung verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="8a022-152">In order to make signing-in easy for you, you will also be asked if you want to use Azure Application Insights for signing-in.</span></span> <span data-ttu-id="8a022-153">Wenn Sie *Ja* wählen, müssen Sie einen Azure Application Insights-Schlüssel angeben.</span><span class="sxs-lookup"><span data-stu-id="8a022-153">If you choose *Yes*, you will need to provide an Azure Application Insights key.</span></span> 

   > [!NOTE]
   > <span data-ttu-id="8a022-154">Für dieses Tutorial Opt-out der Verwendung von Application Insights.</span><span class="sxs-lookup"><span data-stu-id="8a022-154">For this tutorial opt-out of using Application Insights.</span></span>

<span data-ttu-id="8a022-155">Der nächste Fragensatz basiert auf den zuvor ausgewählten Elementen.</span><span class="sxs-lookup"><span data-stu-id="8a022-155">The next set of questions will be based on the previously selected items.</span></span> <span data-ttu-id="8a022-156">Für eine Registerkarte müssen Sie nur einen Namen angeben und optional auswählen, ob Sie diese App als SharePoint Online-Webpart verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="8a022-156">For a tab you only need to provide a name and optionally choose if you want to be able to use this app as a SharePoint Online web part.</span></span> <span data-ttu-id="8a022-157">Nachdem Sie den Namen angeben, generiert der Generator das Projekt und installiert alle Abhängigkeiten.</span><span class="sxs-lookup"><span data-stu-id="8a022-157">After you provide the name the generator will generate the project and install all dependencies.</span></span> <span data-ttu-id="8a022-158">Dies dauert ein oder zwei Minuten.</span><span class="sxs-lookup"><span data-stu-id="8a022-158">This will take a minute or two.</span></span>

## <a name="add-some-code-to-your-tab"></a><span data-ttu-id="8a022-159">Hinzufügen von Code zu Ihrer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="8a022-159">Add some code to your tab</span></span>

<span data-ttu-id="8a022-160">Nachdem der Generator fertig ist, können Sie die Lösung in Ihrem Lieblings-Code-Editor öffnen.</span><span class="sxs-lookup"><span data-stu-id="8a022-160">After the generator is done you can open up the solution in your favorite code editor.</span></span> <span data-ttu-id="8a022-161">Nehmen Sie sich ein oder zwei Minuten Zeit und machen Sie sich mit der Organisation des Codes vertraut.</span><span class="sxs-lookup"><span data-stu-id="8a022-161">Take a minute or two and familiarize yourself with how the code is organized.</span></span> <span data-ttu-id="8a022-162">Weitere Informationen finden Sie in [Project Strukturdokumentation.](https://github.com/OfficeDev/generator-teams/wiki/Project-Structure)</span><span class="sxs-lookup"><span data-stu-id="8a022-162">For more information, see [Project Structure](https://github.com/OfficeDev/generator-teams/wiki/Project-Structure) documentation.</span></span>

<span data-ttu-id="8a022-163">Ihre Registerkarte befindet sich in der `./src/app/scripts/myFirstAppTab/MyFirstAppTab.tsx` Datei.</span><span class="sxs-lookup"><span data-stu-id="8a022-163">Your tab is in the `./src/app/scripts/myFirstAppTab/MyFirstAppTab.tsx` file.</span></span> <span data-ttu-id="8a022-164">Dies ist die TypeScript React-basierte Klasse für Ihre Registerkarte. Suchen Sie die `render()` Methode, und fügen Sie eine Codezeile innerhalb des Steuerelements hinzu, `<PanelBody>` damit sie wie folgt aussieht:</span><span class="sxs-lookup"><span data-stu-id="8a022-164">This is the TypeScript React-based class for your tab. Locate the `render()` method and add a line of code inside the `<PanelBody>` control so it looks like this:</span></span>

``` TypeScript
<PanelBody>
    <div style={styles.section}>
    Hello World! Yo Teams rocks!
    </div>
</PanelBody>
```

<span data-ttu-id="8a022-165">Speichern Sie die Datei, und kehren Sie zur Eingabeaufforderung zurück.</span><span class="sxs-lookup"><span data-stu-id="8a022-165">Save the file and return to the command prompt.</span></span>

## <a name="build-your-app"></a><span data-ttu-id="8a022-166">Erstellen Sie Ihre Anwendung</span><span class="sxs-lookup"><span data-stu-id="8a022-166">Build your app</span></span>

<span data-ttu-id="8a022-167">Sie können nun Ihr Projekt erstellen.</span><span class="sxs-lookup"><span data-stu-id="8a022-167">You can now build your project.</span></span> <span data-ttu-id="8a022-168">Dies geschieht in zwei Schritten (oder in einem Schritt, siehe unten).</span><span class="sxs-lookup"><span data-stu-id="8a022-168">This is done in two steps (or one step, see below).</span></span>

<span data-ttu-id="8a022-169">Zuerst müssen Sie die Teams App-Manifestdatei erstellen, die Sie in Microsoft Teams hochladen/sideloaden.</span><span class="sxs-lookup"><span data-stu-id="8a022-169">First you need to create the Teams App manifest file, that you upload/sideload into Microsoft Teams.</span></span> <span data-ttu-id="8a022-170">Dies geschieht durch die Gulp-Aufgabe `gulp manifest` .</span><span class="sxs-lookup"><span data-stu-id="8a022-170">This is done by the Gulp task `gulp manifest`.</span></span> <span data-ttu-id="8a022-171">Dadurch wird das Manifest überprüft und eine ZIP-Datei im `./package` Verzeichnis erstellt.</span><span class="sxs-lookup"><span data-stu-id="8a022-171">This will validate the manifest and create a zip file in the `./package` directory.</span></span>

<span data-ttu-id="8a022-172">Zum Erstellen der Lösung verwenden Sie den `gulp build` Befehl.</span><span class="sxs-lookup"><span data-stu-id="8a022-172">To build your solution you use the `gulp build` command.</span></span> <span data-ttu-id="8a022-173">Dadurch wird Ihre Lösung in den `./dist` Ordner übertragen.</span><span class="sxs-lookup"><span data-stu-id="8a022-173">This will transpile your solution into the `./dist` folder.</span></span> 

## <a name="run-your-app"></a><span data-ttu-id="8a022-174">Ausführen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="8a022-174">Run your app</span></span>

<span data-ttu-id="8a022-175">Zum Ausführen Ihrer App verwenden Sie den `gulp serve` Befehl.</span><span class="sxs-lookup"><span data-stu-id="8a022-175">To run your app you use the `gulp serve` command.</span></span> <span data-ttu-id="8a022-176">Dadurch wird ein lokaler Webserver erstellt und gestartet, auf dem Sie Ihre App testen können.</span><span class="sxs-lookup"><span data-stu-id="8a022-176">This will build and start a local web server for you to test your app.</span></span> <span data-ttu-id="8a022-177">Der Befehl erstellt die Anwendung auch neu, wenn Sie eine Datei in Ihrem Projekt speichern.</span><span class="sxs-lookup"><span data-stu-id="8a022-177">The command will also rebuild the application whenever you save a file in your project.</span></span> 

<span data-ttu-id="8a022-178">Sie sollten nun in der Lage `http://localhost:3007/myFirstAppTab/` sein, zu navigieren, um sicherzustellen, dass Ihre Registerkarte gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="8a022-178">You should now be able to browse to `http://localhost:3007/myFirstAppTab/` to ensure that your tab is rendering.</span></span> <span data-ttu-id="8a022-179">Allerdings noch nicht in Microsoft Teams:</span><span class="sxs-lookup"><span data-stu-id="8a022-179">However, not in Microsoft Teams yet:</span></span>

![Anzeigen Ihrer Website in einem Browser](~/assets/yeoman-images/teams-first-app-3.png)

## <a name="run-your-app-in-microsoft-teams"></a><span data-ttu-id="8a022-181">Führen Sie Ihre App in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="8a022-181">Run your app in Microsoft Teams</span></span>

<span data-ttu-id="8a022-182">Microsoft Teams ermöglicht es Ihnen nicht, Ihre App auf localhost gehostet zu haben, daher müssen Sie sie entweder auf einer öffentlichen URL veröffentlichen oder einen Proxy wie ngrok verwenden.</span><span class="sxs-lookup"><span data-stu-id="8a022-182">Microsoft Teams does not allow you to have your app hosted on localhost, so you need to either publish it to a public URL or use a proxy such as ngrok.</span></span>

<span data-ttu-id="8a022-183">Eine gute Nachricht ist, dass das Gerüstprojekt diese eingebaute hat.</span><span class="sxs-lookup"><span data-stu-id="8a022-183">Good news is that the scaffolded project has this built-in.</span></span> <span data-ttu-id="8a022-184">Wenn Sie `gulp ngrok-serve` den ngrok-Dienst ausführen, wird er im Hintergrund mit einem eindeutigen und öffentlichen DNS-Eintrag gestartet, und er wird auch das Manifest mit dieser eindeutigen URL verpacken und dann genau dasselbe wie `gulp serve` ausführen.</span><span class="sxs-lookup"><span data-stu-id="8a022-184">When you run `gulp ngrok-serve` the ngrok service will be started in the background, with a unique and public DNS entry and it will also package the manifest with that unique URL and then do the exact same thing as `gulp serve`.</span></span>

<span data-ttu-id="8a022-185">Erstellen Sie nach dem Ausführen ein neues Microsoft Teams Team, und klicken Sie `gulp ngrok-serve` bei der Erstellung auf den Teamnamen, um zu den Teameinstellungen zu wechseln, und wählen Sie dann *Apps* aus.</span><span class="sxs-lookup"><span data-stu-id="8a022-185">After running `gulp ngrok-serve`, create a new Microsoft Teams team and when it is created click on the Team name, to go to the teams settings and then select *Apps*.</span></span> <span data-ttu-id="8a022-186">In der unteren rechten Ecke sollten Sie einen Link *Hochladen einer benutzerdefinierten App* sehen, wählen Sie sie aus, und navigieren Sie dann zu Ihrem Projektordner und dem Unterordner mit dem Namen `package` .</span><span class="sxs-lookup"><span data-stu-id="8a022-186">In the lower right corner you should see a link *Upload a custom app*, select it and then browse to your project folder and the subfolder called `package`.</span></span> <span data-ttu-id="8a022-187">Wählen Sie die ZIP-Datei in diesem Ordner aus, und wählen Sie Öffnen aus.</span><span class="sxs-lookup"><span data-stu-id="8a022-187">Select the zip file in that folder and choose open.</span></span> <span data-ttu-id="8a022-188">Ihre App wird jetzt in Microsoft Teams:</span><span class="sxs-lookup"><span data-stu-id="8a022-188">Your App is now sideloaded into Microsoft Teams:</span></span>

![Sideloaded-App](~/assets/yeoman-images/teams-first-app-4.png)

<span data-ttu-id="8a022-190">Kehren Sie zum *Allgemeinen* Kanal zurück und wählen Sie *+* eine neue Registerkarte hinzu. Sie sollten Ihre Registerkarte in der Liste der Registerkarten sehen:</span><span class="sxs-lookup"><span data-stu-id="8a022-190">Go back to the *General* channel and select *+* to add a new Tab. You should see your tab in the list of tabs:</span></span>

![Registerkarte konfigurieren](~/assets/yeoman-images/teams-first-app-5.png)

<span data-ttu-id="8a022-192">Wählen Sie Ihre Registerkarte und folgen Sie den Anweisungen, um sie hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="8a022-192">Choose your tab and follow the instructions to add it.</span></span> <span data-ttu-id="8a022-193">Beachten Sie, dass Sie über ein benutzerdefiniertes Konfigurationsdialogfeld verfügen, für das Sie die Quelle bearbeiten können.</span><span class="sxs-lookup"><span data-stu-id="8a022-193">Notice that you have a custom configuration dialog, for which you can edit the source.</span></span> <span data-ttu-id="8a022-194">Wählen Sie *Speichern* aus, um die Registerkarte zum Kanal hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="8a022-194">Select *Save* to add your tab to the channel.</span></span> <span data-ttu-id="8a022-195">Sobald Sie fertig sind, sollte Ihre Registerkarte in Microsoft Teams geladen werden!</span><span class="sxs-lookup"><span data-stu-id="8a022-195">Once done your tab should be loaded inside Microsoft Teams!</span></span>

![Ausführen der Registerkarte in Teams](~/assets/yeoman-images/teams-first-app-6.png)

## <a name="upgrade-microsoft-teams"></a><span data-ttu-id="8a022-197">Upgrade-Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="8a022-197">Upgrade Microsoft Teams</span></span>

<span data-ttu-id="8a022-198">Sie können Auch Ihre aktuelle Microsoft Teams Version auf die neueste Version aktualisieren, indem Sie den Microsoft Teams Yeoman-Generator verwenden.</span><span class="sxs-lookup"><span data-stu-id="8a022-198">You can also upgrade your current Microsoft Teams version to the latest version using the Microsoft Teams Yeoman generator.</span></span>

<span data-ttu-id="8a022-199">**So aktualisieren Sie Microsoft Teams**</span><span class="sxs-lookup"><span data-stu-id="8a022-199">**To upgrade Microsoft Teams**</span></span>

1. <span data-ttu-id="8a022-200">Aktuelle Version von Teams mit dem folgenden Befehl abrufen:</span><span class="sxs-lookup"><span data-stu-id="8a022-200">Get current version of Teams with the following command:</span></span>

   ```PowerShell
    yo teams --version
   ```
2. <span data-ttu-id="8a022-201">Verwenden Sie den folgenden Befehl, um Ihren Generator aktualisieren auszuwählen:</span><span class="sxs-lookup"><span data-stu-id="8a022-201">Use the following command to select update your generator:</span></span>

   ```PowerShell
    yo
   ```
3. <span data-ttu-id="8a022-202">Verwenden Sie die Pfeiltasten, um **Aktualisieren Sie Ihre Generatoren**:</span><span class="sxs-lookup"><span data-stu-id="8a022-202">Use the  arrow keys to choose **Update your Generators**:</span></span>

   ![Bild von YoSelectUpdatGen](~/assets/images/Update-Teams/YoSelectUpdateGen.png)

4. <span data-ttu-id="8a022-204">Wählen Sie den gewünschten Generator aus der Liste der Generatoren aus:</span><span class="sxs-lookup"><span data-stu-id="8a022-204">Select the generator you want from the list of generators:</span></span>
   > [!NOTE]
   > <span data-ttu-id="8a022-205">Verwenden Sie die Leertaste, um eine ausgewählte Teams Version aus den verfügbaren Optionen auszuwählen oder zu löschen.</span><span class="sxs-lookup"><span data-stu-id="8a022-205">Use the space bar to select or clear a selected Teams version from the available options.</span></span>

    ![Bild von UseSpaceToSelectGenerators](~/assets/images/Update-Teams/UseSpaceToSelectGenerators.png)
    

   > [!NOTE]
   > <span data-ttu-id="8a022-207">Es dauert einige Sekunden bis Minuten, bis Teams Installation abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="8a022-207">It takes few seconds to minutes for Teams installation to complete.</span></span>

5. <span data-ttu-id="8a022-208">Nachdem die Installation abgeschlossen ist, verwenden Sie den folgenden Befehl, um die installierte Version zu überprüfen:</span><span class="sxs-lookup"><span data-stu-id="8a022-208">After the installation is complete, use the following command to check the installed version:</span></span>

   ```PowerShell
    yo teams --version
   ```
   
<span data-ttu-id="8a022-209">**Congrats! Sie haben Ihre erste Microsoft Teams-App erstellt und bereitgestellt. Sie haben auch Microsoft Teams aktualisiert.**</span><span class="sxs-lookup"><span data-stu-id="8a022-209">**Congrats! You built and deployed your first Microsoft Teams app. You also upgraded Microsoft Teams.**</span></span>
