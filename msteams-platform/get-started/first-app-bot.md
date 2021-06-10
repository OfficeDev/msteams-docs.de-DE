---
title: Erste Schritte – Erstellen Sie Ihren ersten Unterhaltungs-Bot
author: adrianhall
description: Erstellen Sie mithilfe des Teams-Toolkits einen Unterhaltungs-Bot für Microsoft Teams.
ms.author: adhal
ms.date: 05/27/2021
ms.topic: quickstart
ms.openlocfilehash: a2f1ccfa6cc708d655f3b9a54062ee39e8be14bd
ms.sourcegitcommit: 33a43c61f27ae750776616b2cf90159455d8ba6c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2021
ms.locfileid: "52721850"
---
# <a name="build-your-first-conversational-bot-for-microsoft-teams"></a><span data-ttu-id="73c6a-103">Erstellen Sie Ihren ersten Unterhaltungs-Bot für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="73c6a-103">Build your first conversational bot for Microsoft Teams</span></span>

<span data-ttu-id="73c6a-104">Ein Bot agiert als Vermittler zwischen einem Teams-Benutzer und einem Webdienst.</span><span class="sxs-lookup"><span data-stu-id="73c6a-104">A bot acts as an intermediary between a Teams user and a web service.</span></span>  <span data-ttu-id="73c6a-105">Benutzer können mit einem Bot chatten, um schnell Informationen zu erhalten, Workflows zu initiieren, oder für alles andere, was Ihr Webservice tun kann.</span><span class="sxs-lookup"><span data-stu-id="73c6a-105">Users can chat with a bot to quickly get information, initiate workflows, or anything else your web service can do.</span></span>  <span data-ttu-id="73c6a-106">In diesem Lernprogramm erfahren Sie, wie Sie eine Teams-Bot-App erstellen, ausführen und bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="73c6a-106">In this tutorial, you will learn how to build, run, and deploy a Teams bot app.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="73c6a-107">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="73c6a-107">Before you begin</span></span>

<span data-ttu-id="73c6a-108">Stellen Sie sicher, dass Ihre Entwicklungsumgebung eingerichtet ist, indem Sie [Installieren erforderlicher Komponenten](prerequisites.md)</span><span class="sxs-lookup"><span data-stu-id="73c6a-108">Make sure your development environment is set up by installing the [Prerequisites](prerequisites.md)</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="73c6a-109">Installieren erforderlicher Komponenten</span><span class="sxs-lookup"><span data-stu-id="73c6a-109">Install Prerequisites</span></span>](prerequisites.md)

## <a name="create-your-project"></a><span data-ttu-id="73c6a-110">Erstellen Ihres Projekts</span><span class="sxs-lookup"><span data-stu-id="73c6a-110">Create your project</span></span>

<span data-ttu-id="73c6a-111">Verwenden Sie zum Erstellen Ihres ersten Projekts das Microsoft Teams-Toolkit:</span><span class="sxs-lookup"><span data-stu-id="73c6a-111">Use the Teams Toolkit to create your first project:</span></span>

# <a name="visual-studio-code"></a>[<span data-ttu-id="73c6a-112">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="73c6a-112">Visual Studio Code</span></span>](#tab/vscode)

1. <span data-ttu-id="73c6a-113">Öffnen Sie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="73c6a-113">Open Visual Studio code.</span></span>
1. <span data-ttu-id="73c6a-114">Öffnen Sie das Microsoft Teams-Toolkit, indem Sie auf das Microsoft Teams-Symbol in der Randleiste klicken:</span><span class="sxs-lookup"><span data-stu-id="73c6a-114">Open the Teams Toolkit by selecting the Teams icon in the sidebar:</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="Das Microsoft Teams-Symbol in der Visual Studio Code-Randleiste.":::

1. <span data-ttu-id="73c6a-116">Klicken Sie auf **Neues Projekt erstellen**.</span><span class="sxs-lookup"><span data-stu-id="73c6a-116">Select **Create New Project**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project.png" alt-text="Ort des Links „Neues Projekt erstellen“ in der Randleiste des Microsoft Teams-Toolkits.":::

1. <span data-ttu-id="73c6a-118">Wählen Sie **Neue Microsoft Teams-App erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="73c6a-118">Select **Create a new Teams app**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-new-project-intro.png" alt-text="Start des Assistenten für „Neues Projekt erstellen“":::

1. <span data-ttu-id="73c6a-120">Wählen Sie im Schritt **Funktionen auswählen** die Option **Bot** aus, und heben Sie die Auswahl **Registerkarte** auf. Drücken Sie **OK**.</span><span class="sxs-lookup"><span data-stu-id="73c6a-120">On the **Select capabilities** step, select **Bot** and deselect **Tab**.  Press **OK**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-capabilities-bot.png" alt-text="Screenshot, der zeigt, wie Ihrer neuen App Funktionen hinzufügt werden.":::

1. <span data-ttu-id="73c6a-122">Wählen Sie im Schritt **Registrierung eines Bots** die Option **Eine neue Registrierung eines Bots erstellen**.</span><span class="sxs-lookup"><span data-stu-id="73c6a-122">On the **Bot registration** step, select **Create a new bot registration**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-bot-registration.png" alt-text="Wählen Sie „Eine neue Bot-Registrierung erstellen“ aus":::

1. <span data-ttu-id="73c6a-124">Wählen Sie im Schritt **Programmiersprache** die Option **JavaScript** aus.</span><span class="sxs-lookup"><span data-stu-id="73c6a-124">On the **Programming Language** step, select **JavaScript**.</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-programming-languages.png" alt-text="Screenshot, der zeigt, wie die Programmiersprache ausgewählt wird.":::

1. <span data-ttu-id="73c6a-126">Wählen Sie einen Arbeitsbereichsordner aus.</span><span class="sxs-lookup"><span data-stu-id="73c6a-126">Select a workspace folder.</span></span>  <span data-ttu-id="73c6a-127">Innerhalb Ihres Arbeitsbereichsordners wird für das von Ihnen erstellte Projekt ein Ordner erstellt.</span><span class="sxs-lookup"><span data-stu-id="73c6a-127">A folder will be created within your workspace folder for the project you are creating.</span></span>

1. <span data-ttu-id="73c6a-128">Geben Sie einen passenden Namen für Ihre App ein, wie z. B. `helloworld`.</span><span class="sxs-lookup"><span data-stu-id="73c6a-128">Enter a suitable name for your app, like `helloworld`.</span></span>  <span data-ttu-id="73c6a-129">Der Name der App darf nur aus alphanumerischen Zeichen bestehen.</span><span class="sxs-lookup"><span data-stu-id="73c6a-129">The name of the app must consist only of alphanumeric characters.</span></span>  <span data-ttu-id="73c6a-130">Drücken Sie die **EINGABETASTE**, um fortzufahren.</span><span class="sxs-lookup"><span data-stu-id="73c6a-130">Press **Enter** to continue.</span></span>

<span data-ttu-id="73c6a-131">Ihre Microsoft Teams-App wird innerhalb weniger Sekunden erstellt.</span><span class="sxs-lookup"><span data-stu-id="73c6a-131">Your Teams app will be created within a few seconds.</span></span>

# <a name="command-line"></a>[<span data-ttu-id="73c6a-132">Befehlszeile</span><span class="sxs-lookup"><span data-stu-id="73c6a-132">Command line</span></span>](#tab/cli)

<span data-ttu-id="73c6a-133">Verwenden Sie die `teamsfx`-CLI zum Erstellen Ihres ersten Projekts.</span><span class="sxs-lookup"><span data-stu-id="73c6a-133">Use the `teamsfx` CLI to create your first project.</span></span>  <span data-ttu-id="73c6a-134">Beginnen Sie in dem Ordner, in dem Sie den Projektordner erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="73c6a-134">Start from the folder where you want to create the project folder.</span></span>

``` bash
teamsfx new
```

<span data-ttu-id="73c6a-135">Die CLI führt durch einige Fragen zum Erstellen des Projekts.</span><span class="sxs-lookup"><span data-stu-id="73c6a-135">The CLI walks through some questions to create the project.</span></span>  <span data-ttu-id="73c6a-136">Bei jeder Frage wird angegeben, wie Sie sie beantworten können (z. B. mithilfe von Pfeiltasten, um eine Option auszuwählen).</span><span class="sxs-lookup"><span data-stu-id="73c6a-136">Each question will tell you how to answer it (for example, to use arrow keys to select an option).</span></span>  <span data-ttu-id="73c6a-137">Wenn Sie eine Frage beantwortet haben, bestätigen Sie Ihre Auswahl, indem Sie die **EINGABETASTE** drücken.</span><span class="sxs-lookup"><span data-stu-id="73c6a-137">When you have answered the question, confirm your choice by pressing **Enter**.</span></span>

1. <span data-ttu-id="73c6a-138">Wählen Sie **Eine neue Teams-App erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="73c6a-138">Select **Create a new Teams app**.</span></span>
1. <span data-ttu-id="73c6a-139">Wählen Sie die Funktion **Bot** aus, und heben Sie die Auswahl der Funktion **Registerkarte** auf.</span><span class="sxs-lookup"><span data-stu-id="73c6a-139">Select the **Bot** capability and deselect the **Tab** capability.</span></span>
1. <span data-ttu-id="73c6a-140">Wählen Sie **Eine neue Bot-Registrierung erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="73c6a-140">Select **Create a new bot registration**.</span></span>
1. <span data-ttu-id="73c6a-141">Wählen Sie **JavaScript** als Programmiersprache aus.</span><span class="sxs-lookup"><span data-stu-id="73c6a-141">Select **JavaScript** as the programming language.</span></span>
1. <span data-ttu-id="73c6a-142">Drücken Sie die **EINGABETASTE**, um den Standardordner des Arbeitsbereichs auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="73c6a-142">Press **Enter** to select the default workspace folder.</span></span>
1. <span data-ttu-id="73c6a-143">Geben Sie einen passenden Namen für Ihre App ein, wie z. B. `helloworld`.</span><span class="sxs-lookup"><span data-stu-id="73c6a-143">Enter a suitable name for your app, like `helloworld`.</span></span>  <span data-ttu-id="73c6a-144">Der Name der App darf nur aus alphanumerischen Zeichen bestehen.</span><span class="sxs-lookup"><span data-stu-id="73c6a-144">The name of the app must consist only of alphanumeric characters.</span></span>

<span data-ttu-id="73c6a-145">Sobald alle Fragen beantwortet wurden, wird Ihr Projekt erstellt.</span><span class="sxs-lookup"><span data-stu-id="73c6a-145">Once all the questions have been answered, your project will be created.</span></span>

---

## <a name="take-a-tour-of-the-source-code"></a><span data-ttu-id="73c6a-146">Machen Sie einen Rundgang durch den Quellcode</span><span class="sxs-lookup"><span data-stu-id="73c6a-146">Take a tour of the source code</span></span>

<span data-ttu-id="73c6a-147">Wenn Sie diesen Abschnitt vorerst überspringen möchten, können Sie [Ihre App lokal ausführen](#run-your-app-locally).</span><span class="sxs-lookup"><span data-stu-id="73c6a-147">If you wish to skip this section for now, you can [run your app locally](#run-your-app-locally).</span></span>

<span data-ttu-id="73c6a-148">Eine Messaging-Erweiterung verwendet das [Bot-Framework](https://docs.botframework.com), um dem Benutzer die Interaktion mit Ihrem Dienst über eine Unterhaltung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="73c6a-148">A messaging extension uses the [Bot Framework](https://docs.botframework.com) to allow the user to interact with your service via a conversation.</span></span>  <span data-ttu-id="73c6a-149">Nach der Gerüsterstellung wird Ihr Projekt folgend aussehen:</span><span class="sxs-lookup"><span data-stu-id="73c6a-149">After scaffolding, your project will look like this:</span></span>

:::image type="content" source="../assets/images/teams-toolkit-v2/bot-file-layout.png" alt-text="Dateilayout eines Bot-Projekts.":::

<span data-ttu-id="73c6a-151">Der Bot-Code wird im `bot`-Verzeichnis gespeichert.</span><span class="sxs-lookup"><span data-stu-id="73c6a-151">The bot code is stored in the `bot` directory.</span></span>  <span data-ttu-id="73c6a-152">Das `bots/teamsBot.js` ist der Haupteinstiegspunkt für den Bot, und die Dialoge werden im `dialogs`-Verzeichnis gespeichert.</span><span class="sxs-lookup"><span data-stu-id="73c6a-152">The `bots/teamsBot.js` is the main entry point for the bot, and the dialogs are stored in the `dialogs` directory.</span></span>

> [!Tip]
> <span data-ttu-id="73c6a-153">Machen Sie sich mit Bots außerhalb von Teams vertraut, bevor Sie Ihren ersten Bot in Teams integrieren.</span><span class="sxs-lookup"><span data-stu-id="73c6a-153">Familiarize yourself with bots outside of Teams before you integrate your first bot within Teams.</span></span>  <span data-ttu-id="73c6a-154">Sie können weitere Informationen zu Bots im Lernprogramme von [Azure Bot Service](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true) finden.</span><span class="sxs-lookup"><span data-stu-id="73c6a-154">You can find more information about bots by reviewing the [Azure Bot Service](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true) tutorials.</span></span>

## <a name="run-your-app-locally"></a><span data-ttu-id="73c6a-155">Lokales Ausführen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="73c6a-155">Run your app locally</span></span>

<span data-ttu-id="73c6a-156">Das Teams-Toolkit ermöglicht es Ihnen, Ihre App lokal zu hosten.</span><span class="sxs-lookup"><span data-stu-id="73c6a-156">Teams Toolkit allows you to host your app locally.</span></span>  <span data-ttu-id="73c6a-157">Gehen Sie hierfür folgendermaßen vor:</span><span class="sxs-lookup"><span data-stu-id="73c6a-157">To do this:</span></span>

- <span data-ttu-id="73c6a-158">Eine Azure Active Directory-Anwendung ist im M365-Mandanten registriert.</span><span class="sxs-lookup"><span data-stu-id="73c6a-158">An Azure Active Directory Application is registered within the M365 tenant.</span></span>
- <span data-ttu-id="73c6a-159">Ein App-Manifest wird dem Entwickler-Center für Teams übermittelt.</span><span class="sxs-lookup"><span data-stu-id="73c6a-159">An app manifest is submitted to the Developer Center for Teams.</span></span>
- <span data-ttu-id="73c6a-160">Eine API wird mittels der Azure Functions Core Tools lokal ausgeführt, um Ihre App zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="73c6a-160">An API is run locally using Azure Functions Core Tools to support your app.</span></span>
- <span data-ttu-id="73c6a-161">[ngrok](https://ngrok.io) ist installiert und wird dazu verwendet, einen Tunnel zwischen Teams und Ihrem Bot-Code bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="73c6a-161">[ngrok](https://ngrok.io) is installed and used to provide a tunnel between Teams and your bot code.</span></span>

<span data-ttu-id="73c6a-162">So erstellen Sie Ihre App und führen sie lokal aus:</span><span class="sxs-lookup"><span data-stu-id="73c6a-162">To build and run your app locally:</span></span>

1. <span data-ttu-id="73c6a-163">Drücken Sie in Visual Studio Code **F5**, um die Anwendung im Debugmodus auszuführen.</span><span class="sxs-lookup"><span data-stu-id="73c6a-163">From Visual Studio Code, press **F5** to run your application in debug mode.</span></span>

   > <span data-ttu-id="73c6a-164">Wenn Sie die App zum ersten Mal ausführen, werden alle Abhängigkeiten heruntergeladen und die App wird erstellt.</span><span class="sxs-lookup"><span data-stu-id="73c6a-164">When you run the app for the first time, all dependencies are downloaded and the app is built.</span></span>  <span data-ttu-id="73c6a-165">Wenn die Erstellung abgeschlossen ist, wird automatisch ein Browserfenster geöffnet.</span><span class="sxs-lookup"><span data-stu-id="73c6a-165">A browser window automatically opens when the build is complete.</span></span>  <span data-ttu-id="73c6a-166">Dies kann 3 bis 5 Minuten dauern.</span><span class="sxs-lookup"><span data-stu-id="73c6a-166">This can take 3-5 minutes to complete.</span></span>

1. <span data-ttu-id="73c6a-167">Ihr Webbrowser startet mit der Ausführung der App.</span><span class="sxs-lookup"><span data-stu-id="73c6a-167">Your web browser starts to run the app.</span></span> <span data-ttu-id="73c6a-168">Wenn Sie aufgefordert werden, Teams desktop zu öffnen, wählen **Sie Abbrechen** aus, um im Browser zu verbleiben.</span><span class="sxs-lookup"><span data-stu-id="73c6a-168">If prompted to open Teams desktop, select **Cancel** to remain in the browser.</span></span> <span data-ttu-id="73c6a-169">Sie werden möglicherweise auch aufgefordert, zu anderen Teams zu wechseln. wählen Sie Teams Web-App aus, wenn dies geschieht.</span><span class="sxs-lookup"><span data-stu-id="73c6a-169">You may also be prompted to switch to Teams desktop at other times; select the Teams web app when this happens.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/launch-web-browser-and-pick-webapp.png" alt-text="Screenshot, der zeigt, wie die Web-Version von Microsoft Teams beim Start ausgewählt wird.":::

1. <span data-ttu-id="73c6a-171">Möglicherweise werden Sie aufgefordert, sich anzumelden.</span><span class="sxs-lookup"><span data-stu-id="73c6a-171">You may be prompted to sign in.</span></span>  <span data-ttu-id="73c6a-172">Melden Sie sich in diesem Fall mit Ihrem M365-Konto an.</span><span class="sxs-lookup"><span data-stu-id="73c6a-172">If so, sign in with your M365 account.</span></span>
1. <span data-ttu-id="73c6a-173">Wenn Sie aufgefordert werden, die App in Teams zu installieren, drücken Sie **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="73c6a-173">When prompted to install the app onto Teams, press **Add**.</span></span>

<span data-ttu-id="73c6a-174">Sobald die App geladen ist, werden Sie direkt zu einer Chat-Sitzung mit dem Bot geführt.</span><span class="sxs-lookup"><span data-stu-id="73c6a-174">Once the app is loaded, you will be taken directly to a chat session with the bot.</span></span>  <span data-ttu-id="73c6a-175">Sie können `intro` eingeben, um einen Einführungskarte anzuzeigen, und `show`, um Ihre Details von Microsoft Graph anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="73c6a-175">You can type `intro` to show an introduction card, and `show` to show your details from Microsoft Graph.</span></span>  <span data-ttu-id="73c6a-176">(Dies benötigt eine zusätzliche Berechtigungsgenehmigung).</span><span class="sxs-lookup"><span data-stu-id="73c6a-176">(This will require an additional permissions approval).</span></span>

<span data-ttu-id="73c6a-177">Das Debuggen funktioniert so, wie Sie es normalerweise erwarten – probieren Sie es selbst aus!</span><span class="sxs-lookup"><span data-stu-id="73c6a-177">Debugging works as you normally would expect - try it yourself!</span></span> <span data-ttu-id="73c6a-178">Öffnen Sie die Datei `bot/dialogs/rootDialog.js`, und suchen Sie die `triggerCommand(...)`-Methode.</span><span class="sxs-lookup"><span data-stu-id="73c6a-178">Open the `bot/dialogs/rootDialog.js` file and locate the `triggerCommand(...)` method.</span></span>  <span data-ttu-id="73c6a-179">Setzen Sie einen Haltepunkt auf dem Standardvorgang.</span><span class="sxs-lookup"><span data-stu-id="73c6a-179">Set a breakpoint on the default case.</span></span>  <span data-ttu-id="73c6a-180">Geben Sie dann einigen Text ein.</span><span class="sxs-lookup"><span data-stu-id="73c6a-180">Then type some text.</span></span>

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="73c6a-181">Erfahren Sie, was geschieht, wenn Sie Ihre App lokal im Debugger ausführen.</span><span class="sxs-lookup"><span data-stu-id="73c6a-181">Learn what happens when you run your app locally in the debugger.</span></span></summary>

<span data-ttu-id="73c6a-182">Wenn Sie F5 gedrückt haben, hat das Microsoft Teams-Toolkit Folgendes getan:</span><span class="sxs-lookup"><span data-stu-id="73c6a-182">When you pressed F5, the Teams Toolkit:</span></span>

1. <span data-ttu-id="73c6a-183">Ihre Anwendung bei Azure Active Directory registriert.</span><span class="sxs-lookup"><span data-stu-id="73c6a-183">Registered your application with Azure Active Directory.</span></span>
1. <span data-ttu-id="73c6a-184">Ihre Anwendung bei Microsoft Teams für das „Querladen“ registriert.</span><span class="sxs-lookup"><span data-stu-id="73c6a-184">Registered your application for "side loading" in Microsoft Teams.</span></span>
1. <span data-ttu-id="73c6a-185">Ihr Anwendungs-Back-End mithilfe von [Azure Function Core Tools](/azure/azure-functions/functions-run-local?#start) lokal gestartet.</span><span class="sxs-lookup"><span data-stu-id="73c6a-185">Started your application backend running locally using [Azure Function Core Tools](/azure/azure-functions/functions-run-local?#start).</span></span>
1. <span data-ttu-id="73c6a-186">Ein ngrok-Tunnel gestartet, sodass Teams mit Ihrer App kommunizieren kann.</span><span class="sxs-lookup"><span data-stu-id="73c6a-186">Started an ngrok tunnel so Teams can communicate with your app.</span></span>
1. <span data-ttu-id="73c6a-187">Microsoft Teams mit einem Befehl gestartet, mit dem Teams angewiesen wird, die Anwendung querzuladen.</span><span class="sxs-lookup"><span data-stu-id="73c6a-187">Started Microsoft Teams with a command to instruct Teams to sideload the application.</span></span>

</details>

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="73c6a-188">Erfahren Sie, wie Sie häufige Probleme bei dem lokalen Ausführen Ihrer App lösen können.</span><span class="sxs-lookup"><span data-stu-id="73c6a-188">Learn how to troubleshoot common issues when running your app locally.</span></span></summary>

<span data-ttu-id="73c6a-189">Um Ihre App in Teams erfolgreich auszuführen, müssen Sie ein Microsoft 365-Entwicklungskonto haben, das das Querladen von Apps ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="73c6a-189">To successfully run your app in Teams, you must have a Microsoft 365 development account that allows app sideloading.</span></span> <span data-ttu-id="73c6a-190">Weitere Informationen zum Öffnen von Apps finden Sie unter [Erforderliche Komponenten](prerequisites.md#enable-sideloading).</span><span class="sxs-lookup"><span data-stu-id="73c6a-190">For more information on account opening, see [Prerequisites](prerequisites.md#enable-sideloading).</span></span>

> [!TIP]
> <span data-ttu-id="73c6a-191">Überprüfen Sie mithilfe des [Tools für die App-Überprüfung](https://dev.teams.microsoft.com/appvalidation.html), das im Toolkit enthalten ist, ob es Probleme gibt, bevor Sie ihre App querladen.</span><span class="sxs-lookup"><span data-stu-id="73c6a-191">Check for issues before sideloading your app, using the [app validation tool](https://dev.teams.microsoft.com/appvalidation.html), which is included in the toolkit.</span></span> <span data-ttu-id="73c6a-192">Beheben Sie die Probleme, um die App erfolgreich querzuladen.</span><span class="sxs-lookup"><span data-stu-id="73c6a-192">Fix the errors to successfully sideload the app.</span></span>
</details>

[!INCLUDE [Provision and Deploy your app on Azure](~/includes/get-started/azure-provisioning-instructions.md)]

<!-- markdownlint-disable MD033 -->

<details>
<summary><span data-ttu-id="73c6a-193">Erfahren Sie, was geschieht, wenn Sie Ihre App in Azure bereitstellen</span><span class="sxs-lookup"><span data-stu-id="73c6a-193">Learn what happens when you deployed your app to Azure</span></span></summary>

<span data-ttu-id="73c6a-194">Vor der Bereitstellung wurde die Anwendung lokal ausgeführt:</span><span class="sxs-lookup"><span data-stu-id="73c6a-194">Before deployment, the application has been running locally:</span></span>

1. <span data-ttu-id="73c6a-195">Das Back-End unter Verwendung von _Azure Functions Core Tools_ ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="73c6a-195">The backend runs using _Azure Functions Core Tools_.</span></span>
1. <span data-ttu-id="73c6a-196">Der HTTP-Endpunkt der Anwendung, an dem Microsoft Teams die Anwendung lädt, wird lokal ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="73c6a-196">The application HTTP endpoint, where Microsoft Teams loads the application, runs locally.</span></span>

<span data-ttu-id="73c6a-197">Die Bereitstellung umfasst das Bereitstellen von Ressourcen für ein aktives Azure-Abonnement und das Bereitstellen (Hochladen) des Back-End- und des Frontend-Codes für die Anwendung in Azure.</span><span class="sxs-lookup"><span data-stu-id="73c6a-197">Deployment involves provisioning resources on an active Azure subscription and deploying (uploading) the backend and frontend code for the application to Azure.</span></span> <span data-ttu-id="73c6a-198">Das Back-End verwendet eine Vielzahl von Azure-Diensten, einschließlich Azure App Service und Azure Bot Service.</span><span class="sxs-lookup"><span data-stu-id="73c6a-198">The backend uses a variety of Azure services, including Azure App Service and Azure Bot Service.</span></span>

</details>

## <a name="next-steps"></a><span data-ttu-id="73c6a-199">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="73c6a-199">Next steps</span></span>

<span data-ttu-id="73c6a-200">Weitere Informationen zu anderen Methoden zum Erstellen von Teams-Apps:</span><span class="sxs-lookup"><span data-stu-id="73c6a-200">Learn about other methods for creating Teams apps:</span></span>

- [<span data-ttu-id="73c6a-201">Erstellen einer Teams-App mit React</span><span class="sxs-lookup"><span data-stu-id="73c6a-201">Create a Teams app with React</span></span>](first-app-react.md)
- [<span data-ttu-id="73c6a-202">Erstellen einer Teams-App mit Blazor</span><span class="sxs-lookup"><span data-stu-id="73c6a-202">Create a Teams app with Blazor</span></span>](first-app-blazor.md)
- <span data-ttu-id="73c6a-203">[Erstellen einer Teams-App als ein SharePoint-Webpart](first-app-spfx.md) (Azure nicht erforderlich)</span><span class="sxs-lookup"><span data-stu-id="73c6a-203">[Create a Teams app as a SharePoint Web Part](first-app-spfx.md) (Azure not required)</span></span>
- [<span data-ttu-id="73c6a-204">Erstellen einer Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="73c6a-204">Create a messaging extension</span></span>](first-message-extension.md)