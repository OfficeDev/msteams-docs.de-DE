---
title: Erste Schritte – Erstellen Sie Ihren ersten Unterhaltungs-Bot
author: adrianhall
description: Erstellen Sie mithilfe des Teams-Toolkits einen Unterhaltungs-Bot für Microsoft Teams.
ms.author: adhal
ms.date: 05/27/2021
ms.topic: quickstart
ms.openlocfilehash: 96bbddd99b6901a4b92e1e2f2dc98482c755dc66
ms.sourcegitcommit: 9d63611974ba8a7e7f19ceea35e50189a2e90434
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2021
ms.locfileid: "53254251"
---
# <a name="build-your-first-conversational-bot-for-microsoft-teams"></a><span data-ttu-id="8c3fe-103">Erstellen Sie Ihren ersten Unterhaltungs-Bot für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="8c3fe-103">Build your first conversational bot for Microsoft Teams</span></span>

<span data-ttu-id="8c3fe-104">In diesem Lernprogramm erfahren Sie, wie Sie eine Teams-Bot-App erstellen, ausführen und bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-104">In this tutorial, you will learn how to build, run, and deploy a Teams bot app.</span></span> <span data-ttu-id="8c3fe-105">Ein Bot agiert als Vermittler zwischen einem Teams-Benutzer und einem Webdienst.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-105">A bot acts as an intermediary between a Teams user and a web service.</span></span>  <span data-ttu-id="8c3fe-106">Benutzer können mit einem Bot chatten, um schnell Informationen zu erhalten, Workflows zu initiieren, oder für alles andere, was Ihr Webservice tun kann.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-106">Users can chat with a bot to quickly get information, initiate workflows, or anything else your web service can do.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="8c3fe-107">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="8c3fe-107">Before you begin</span></span>

<span data-ttu-id="8c3fe-108">Stellen Sie sicher, dass Ihre Entwicklungsumgebung eingerichtet ist, indem Sie die erforderlichen Komponenten installieren.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-108">Make sure your development environment is set up by installing the Prerequisites.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8c3fe-109">Installieren erforderlicher Komponenten</span><span class="sxs-lookup"><span data-stu-id="8c3fe-109">Install Prerequisites</span></span>](prerequisites.md)

## <a name="create-your-project"></a><span data-ttu-id="8c3fe-110">Erstellen Ihres Projekts</span><span class="sxs-lookup"><span data-stu-id="8c3fe-110">Create your project</span></span>

<span data-ttu-id="8c3fe-111">Verwenden Sie zum Erstellen Ihres ersten Projekts das Microsoft Teams-Toolkit:</span><span class="sxs-lookup"><span data-stu-id="8c3fe-111">Use the Teams Toolkit to create your first project:</span></span>

# <a name="visual-studio-code"></a>[<span data-ttu-id="8c3fe-112">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="8c3fe-112">Visual Studio Code</span></span>](#tab/vscode)

1. <span data-ttu-id="8c3fe-113">Öffnen Sie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-113">Open Visual Studio code.</span></span>
1. <span data-ttu-id="8c3fe-114">Wählen Sie das Symbol Teams in der Seitenleiste aus, um das Teams Toolkit zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-114">Select the Teams icon in the sidebar to open the Teams Toolkit.</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="Das Microsoft Teams-Symbol in der Visual Studio Code-Randleiste.":::

1. <span data-ttu-id="8c3fe-116">Klicken Sie auf **Neues Projekt erstellen**.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-116">Select **Create New Project**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project.png" alt-text="Ort des Links „Neues Projekt erstellen“ in der Randleiste des Microsoft Teams-Toolkits.":::

1. <span data-ttu-id="8c3fe-118">Wählen Sie **Neue Microsoft Teams-App erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-118">Select **Create a new Teams app**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-new-project-intro.png" alt-text="Starten des Assistenten für „Neues Projekt erstellen“":::

1. <span data-ttu-id="8c3fe-120">Wählen Sie im Abschnitt **"Funktionen auswählen"** die Option **"Bot"** aus, deaktivieren **Sie die Registerkarte,** und wählen Sie **"OK"** aus.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-120">In the **Select capabilities** section, select **Bot**, deselect **Tab** and select **OK**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-capabilities-bot.png" alt-text="Screenshot, der zeigt, wie Ihrer neuen App Funktionen hinzufügt werden können.":::

1. <span data-ttu-id="8c3fe-122">Wählen Sie im Abschnitt **"Bot-Registrierung"** die Option **"Neue Bot-Registrierung erstellen"** aus.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-122">In the **Bot registration** section, select **Create a new bot registration**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-bot-registration.png" alt-text="Wählen Sie „Eine neue Registrierung eines Bots erstellen“ aus":::

1. <span data-ttu-id="8c3fe-124">Wählen Sie im Abschnitt **"Programmiersprache"** **JavaScript** aus.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-124">In the **Programming Language** section, select **JavaScript**.</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-programming-languages.png" alt-text="Screenshot, der zeigt, wie die Programmiersprache ausgewählt wird.":::

1. <span data-ttu-id="8c3fe-126">Wählen Sie einen Arbeitsbereichsordner aus.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-126">Select a workspace folder.</span></span>  <span data-ttu-id="8c3fe-127">Innerhalb Ihres Arbeitsbereichsordners wird für das von Ihnen erstellte Projekt ein Ordner erstellt.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-127">A folder will be created within your workspace folder for the project you are creating.</span></span>

1. <span data-ttu-id="8c3fe-128">Geben Sie einen passenden Namen für Ihre App ein, wie z. B. `helloworld`.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-128">Enter a suitable name for your app, like `helloworld`.</span></span>  <span data-ttu-id="8c3fe-129">Der Name der App darf nur alphanumerische Zeichen enthalten.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-129">The name of the app must contain only alphanumeric characters.</span></span>  <span data-ttu-id="8c3fe-130">Drücken Sie die **EINGABETASTE**, um fortzufahren.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-130">Press **Enter** to continue.</span></span>

<span data-ttu-id="8c3fe-131">Ihre Microsoft Teams-App wird innerhalb weniger Sekunden erstellt.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-131">Your Teams app will be created within a few seconds.</span></span>

# <a name="command-line"></a>[<span data-ttu-id="8c3fe-132">Befehlszeile</span><span class="sxs-lookup"><span data-stu-id="8c3fe-132">Command line</span></span>](#tab/cli)

<span data-ttu-id="8c3fe-133">Verwenden Sie die `teamsfx`-CLI zum Erstellen Ihres ersten Projekts.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-133">Use the `teamsfx` CLI to create your first project.</span></span>  <span data-ttu-id="8c3fe-134">Beginnen Sie in dem Ordner, in dem Sie den Projektordner erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-134">Start from the folder where you want to create the project folder.</span></span>

``` bash
teamsfx new
```

<span data-ttu-id="8c3fe-135">Die CLI führt durch einige Fragen zum Erstellen des Projekts.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-135">The CLI walks through some questions to create the project.</span></span>  <span data-ttu-id="8c3fe-136">Bei jeder Frage wird angegeben, wie Sie sie beantworten können (z. B. mithilfe von Pfeiltasten, um eine Option auszuwählen).</span><span class="sxs-lookup"><span data-stu-id="8c3fe-136">Each question will tell you how to answer it (for example, to use arrow keys to select an option).</span></span>  <span data-ttu-id="8c3fe-137">Wenn Sie eine Frage beantwortet haben, bestätigen Sie Ihre Auswahl, indem Sie die **EINGABETASTE** drücken.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-137">When you have answered the question, confirm your choice by pressing **Enter**.</span></span>

1. <span data-ttu-id="8c3fe-138">Wählen Sie **Neue Microsoft Teams-App erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-138">Select **Create a new Teams app**.</span></span>
1. <span data-ttu-id="8c3fe-139">Wählen Sie **Bot** aus, und heben Sie die **Auswahl auf der Registerkarte auf.**</span><span class="sxs-lookup"><span data-stu-id="8c3fe-139">Select **Bot** and deselect **Tab**.</span></span>
1. <span data-ttu-id="8c3fe-140">Wählen Sie **Eine neue Registrierung eines Bots erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-140">Select **Create a new bot registration**.</span></span>
1. <span data-ttu-id="8c3fe-141">Wählen Sie **JavaScript** als Programmiersprache aus.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-141">Select **JavaScript** as the programming language.</span></span>
1. <span data-ttu-id="8c3fe-142">Drücken Sie die **EINGABETASTE**, um den Standardordner des Arbeitsbereichs auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-142">Press **Enter** to select the default workspace folder.</span></span>
1. <span data-ttu-id="8c3fe-143">Geben Sie einen passenden Namen für Ihre App ein, wie z. B. `helloworld`.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-143">Enter a suitable name for your app, like `helloworld`.</span></span>  <span data-ttu-id="8c3fe-144">Der Name der App darf nur aus alphanumerischen Zeichen bestehen.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-144">The name of the app must consist only of alphanumeric characters.</span></span>

<span data-ttu-id="8c3fe-145">Nachdem alle Fragen beantwortet wurden, wird Ihr Projekt erstellt.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-145">After all the questions have been answered, your project is created.</span></span>

---

## <a name="take-a-tour-of-the-source-code"></a><span data-ttu-id="8c3fe-146">Machen Sie einen Rundgang durch den Quellcode</span><span class="sxs-lookup"><span data-stu-id="8c3fe-146">Take a tour of the source code</span></span>

<span data-ttu-id="8c3fe-147">Wenn Sie diesen Abschnitt vorerst überspringen möchten, können Sie [Ihre App lokal ausführen](#run-your-app-locally).</span><span class="sxs-lookup"><span data-stu-id="8c3fe-147">If you wish to skip this section for now, you can [run your app locally](#run-your-app-locally).</span></span>

<span data-ttu-id="8c3fe-148">Eine Messaging-Erweiterung verwendet das [Bot-Framework](https://docs.botframework.com), um dem Benutzer die Interaktion mit Ihrem Dienst über eine Unterhaltung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-148">A messaging extension uses the [Bot Framework](https://docs.botframework.com) to allow the user to interact with your service via a conversation.</span></span>  <span data-ttu-id="8c3fe-149">Nach der Gerüsterstellung wird Ihr Projekt folgend aussehen:</span><span class="sxs-lookup"><span data-stu-id="8c3fe-149">After scaffolding, your project will look like this:</span></span>

:::image type="content" source="../assets/images/teams-toolkit-v2/bot-file-layout.png" alt-text="Dateilayout eines Bot-Projekts.":::

<span data-ttu-id="8c3fe-151">Der Bot-Code wird im `bot`-Verzeichnis gespeichert.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-151">The bot code is stored in the `bot` directory.</span></span>  <span data-ttu-id="8c3fe-152">Das `bot/teamsBot.js` ist der Haupteinstiegspunkt für den Bot, und die Dialoge werden im `dialogs`-Verzeichnis gespeichert.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-152">The `bot/teamsBot.js` is the main entry point for the bot, and the dialogs are stored in the `dialogs` directory.</span></span>

> [!Tip]
> <span data-ttu-id="8c3fe-153">Machen Sie sich mit Bots außerhalb von Teams vertraut, bevor Sie Ihren ersten Bot in Teams integrieren.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-153">Familiarize yourself with bots outside of Teams before you integrate your first bot within Teams.</span></span>  <span data-ttu-id="8c3fe-154">Sie können weitere Informationen zu Bots im Lernprogramme von [Azure Bot Service](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true) finden.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-154">You can find more information about bots by reviewing the [Azure Bot Service](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true) tutorials.</span></span>

## <a name="run-your-app-locally"></a><span data-ttu-id="8c3fe-155">Lokales Ausführen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="8c3fe-155">Run your app locally</span></span>

<span data-ttu-id="8c3fe-156">Das Teams-Toolkit ermöglicht es Ihnen, Ihre App lokal zu hosten.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-156">Teams Toolkit allows you to host your app locally.</span></span>  <span data-ttu-id="8c3fe-157">Gehen Sie hierfür folgendermaßen vor:</span><span class="sxs-lookup"><span data-stu-id="8c3fe-157">To do this:</span></span>

- <span data-ttu-id="8c3fe-158">Eine Azure Active Directory-Anwendung ist im M365-Mandanten registriert.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-158">An Azure Active Directory Application is registered within the M365 tenant.</span></span>
- <span data-ttu-id="8c3fe-159">Ein App-Manifest wird dem Entwickler-Center für Teams übermittelt.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-159">An app manifest is submitted to the Developer Center for Teams.</span></span>
- <span data-ttu-id="8c3fe-160">Eine API wird mittels der Azure Functions Core Tools lokal ausgeführt, um Ihre App zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-160">An API is run locally using Azure Functions Core Tools to support your app.</span></span>
- <span data-ttu-id="8c3fe-161">[ngrok](https://ngrok.io) ist installiert und wird dazu verwendet, einen Tunnel zwischen Teams und Ihrem Bot-Code bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-161">[ngrok](https://ngrok.io) is installed and used to provide a tunnel between Teams and your bot code.</span></span>

<span data-ttu-id="8c3fe-162">So erstellen Sie Ihre App und führen sie lokal aus:</span><span class="sxs-lookup"><span data-stu-id="8c3fe-162">To build and run your app locally:</span></span>

1. <span data-ttu-id="8c3fe-163">Drücken Sie Visual Studio Code die **F5-Taste,** um die Anwendung im Debugmodus auszuführen.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-163">From Visual Studio Code, press the **F5** key to run your application in debug mode.</span></span>

   > <span data-ttu-id="8c3fe-164">Wenn Sie die App zum ersten Mal ausführen, werden alle Abhängigkeiten heruntergeladen und die App wird erstellt.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-164">When you run the app for the first time, all dependencies are downloaded and the app is built.</span></span>  <span data-ttu-id="8c3fe-165">Wenn die Erstellung abgeschlossen ist, wird automatisch ein Browserfenster geöffnet.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-165">A browser window automatically opens when the build is complete.</span></span>  <span data-ttu-id="8c3fe-166">Dies kann 3 bis 5 Minuten dauern.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-166">This can take 3-5 minutes to complete.</span></span>

1. <span data-ttu-id="8c3fe-167">Ihr Webbrowser beginnt mit der Ausführung der App.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-167">Your web browser starts to run the app.</span></span> <span data-ttu-id="8c3fe-168">Wenn Sie aufgefordert werden, Teams Desktop zu öffnen, wählen Sie **"Abbrechen"** aus, um im Browser zu verbleiben.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-168">If prompted to open Teams desktop, select **Cancel** to remain in the browser.</span></span> <span data-ttu-id="8c3fe-169">Möglicherweise werden Sie auch aufgefordert, zu anderen Zeiten zu Teams Desktop zu wechseln. wählen Sie in diesem Fall die Teams Web-App aus.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-169">You may also be prompted to switch to Teams desktop at other times; select the Teams web app when this happens.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/launch-web-browser-and-pick-webapp.png" alt-text="Screenshot, der zeigt, wie die Web-Version von Microsoft Teams beim Start ausgewählt wird.":::

1. <span data-ttu-id="8c3fe-171">Möglicherweise werden Sie aufgefordert, sich anzumelden.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-171">You may be prompted to sign in.</span></span>  <span data-ttu-id="8c3fe-172">Melden Sie sich in diesem Fall mit Ihrem M365-Konto an.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-172">If so, sign in with your M365 account.</span></span>
1. <span data-ttu-id="8c3fe-173">Wenn Sie aufgefordert werden, die App auf Teams zu installieren, wählen Sie **Hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-173">When prompted to install the app onto Teams, select **Add**.</span></span>

   <span data-ttu-id="8c3fe-174">Nachdem die App geladen wurde, werden Sie direkt zu einer Chatsitzung mit dem Bot weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-174">After the app is loaded, you will be taken directly to a chat session with the bot.</span></span>  <span data-ttu-id="8c3fe-175">Sie können `intro` eingeben, um einen Einführungskarte anzuzeigen, und `show`, um Ihre Details von Microsoft Graph anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-175">You can type `intro` to show an introduction card, and `show` to show your details from Microsoft Graph.</span></span>  <span data-ttu-id="8c3fe-176">(Dies benötigt eine zusätzliche Berechtigungsgenehmigung).</span><span class="sxs-lookup"><span data-stu-id="8c3fe-176">(This will require an additional permissions approval).</span></span>

   <span data-ttu-id="8c3fe-177">Das Debuggen funktioniert so, wie Sie es normalerweise erwarten – probieren Sie es selbst aus!</span><span class="sxs-lookup"><span data-stu-id="8c3fe-177">Debugging works as you normally would expect - try it yourself!</span></span> <span data-ttu-id="8c3fe-178">Öffnen Sie die Datei `bot/dialogs/rootDialog.js`, und suchen Sie die `triggerCommand(...)`-Methode.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-178">Open the `bot/dialogs/rootDialog.js` file and locate the `triggerCommand(...)` method.</span></span>  <span data-ttu-id="8c3fe-179">Setzen Sie einen Haltepunkt auf dem Standardvorgang.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-179">Set a breakpoint on the default case.</span></span>  <span data-ttu-id="8c3fe-180">Geben Sie dann einigen Text ein.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-180">Then type some text.</span></span>

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="8c3fe-181">Erfahren Sie, was geschieht, wenn Sie Ihre App lokal im Debugger ausführen.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-181">Learn what happens when you run your app locally in the debugger.</span></span></summary>

<span data-ttu-id="8c3fe-182">Wenn Sie **F5** drücken, hat das Teams Toolkit Folgendes:</span><span class="sxs-lookup"><span data-stu-id="8c3fe-182">When you press the **F5** key, the Teams Toolkit:</span></span>

1. <span data-ttu-id="8c3fe-183">Registriert Ihre Anwendung bei Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-183">Registers your application with Azure Active Directory.</span></span>
1. <span data-ttu-id="8c3fe-184">Registriert Ihre Anwendung für das "Querladen" in Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-184">Registers your application for "side loading" in Microsoft Teams.</span></span>
1. <span data-ttu-id="8c3fe-185">Startet ihr Anwendungs-Back-End, das lokal mithilfe von [Azure Function Core Tools](/azure/azure-functions/functions-run-local?#start)ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-185">Starts your application backend running locally using [Azure Function Core Tools](/azure/azure-functions/functions-run-local?#start).</span></span>
1. <span data-ttu-id="8c3fe-186">Startet einen ngrok-Tunnel, damit Teams mit Ihrer App kommunizieren können.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-186">Starts an ngrok tunnel so Teams can communicate with your app.</span></span>
1. <span data-ttu-id="8c3fe-187">Startet Microsoft Teams mit einem Befehl, um Teams anzuweisen, die Anwendung querzuladen.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-187">Starts Microsoft Teams with a command to instruct Teams to sideload the application.</span></span>

</details>

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="8c3fe-188">Erfahren Sie, wie Sie häufige Probleme bei dem lokalen Ausführen Ihrer App lösen können.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-188">Learn how to troubleshoot common issues when running your app locally.</span></span></summary>

<span data-ttu-id="8c3fe-189">Um Ihre App in Teams erfolgreich auszuführen, müssen Sie ein Microsoft 365-Entwicklungskonto haben, das das Querladen von Apps ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-189">To successfully run your app in Teams, you must have a Microsoft 365 development account that allows app sideloading.</span></span> <span data-ttu-id="8c3fe-190">Weitere Informationen zum Öffnen von Apps finden Sie unter [Erforderliche Komponenten](prerequisites.md#enable-sideloading).</span><span class="sxs-lookup"><span data-stu-id="8c3fe-190">For more information on account opening, see [Prerequisites](prerequisites.md#enable-sideloading).</span></span>

> [!TIP]
> <span data-ttu-id="8c3fe-191">Überprüfen Sie mithilfe des [Tools für die App-Überprüfung](https://dev.teams.microsoft.com/appvalidation.html), das im Toolkit enthalten ist, ob es Probleme gibt, bevor Sie ihre App querladen.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-191">Check for issues before sideloading your app, using the [app validation tool](https://dev.teams.microsoft.com/appvalidation.html), which is included in the toolkit.</span></span> <span data-ttu-id="8c3fe-192">Beheben Sie die Probleme, um die App erfolgreich querzuladen.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-192">Fix the errors to successfully sideload the app.</span></span>
</details>

[!INCLUDE [Provision and Deploy your app on Azure](~/includes/get-started/azure-provisioning-instructions.md)]

<!-- markdownlint-disable MD033 -->

<details>
<summary><span data-ttu-id="8c3fe-193">Erfahren Sie, was geschieht, wenn Sie Ihre App in Azure bereitstellen</span><span class="sxs-lookup"><span data-stu-id="8c3fe-193">Learn what happens when you deployed your app to Azure</span></span></summary>

<span data-ttu-id="8c3fe-194">Vor der Bereitstellung wurde die Anwendung lokal ausgeführt:</span><span class="sxs-lookup"><span data-stu-id="8c3fe-194">Before deployment, the application has been running locally:</span></span>

1. <span data-ttu-id="8c3fe-195">Das Back-End unter Verwendung von _Azure Functions Core Tools_ ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-195">The backend runs using _Azure Functions Core Tools_.</span></span>
1. <span data-ttu-id="8c3fe-196">Der HTTP-Endpunkt der Anwendung, an dem Microsoft Teams die Anwendung lädt, wird lokal ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-196">The application HTTP endpoint, where Microsoft Teams loads the application, runs locally.</span></span>

   <span data-ttu-id="8c3fe-197">Die Bereitstellung umfasst das Bereitstellen von Ressourcen für ein aktives Azure-Abonnement und das Bereitstellen (Hochladen) des Back-End- und des Frontend-Codes für die Anwendung in Azure.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-197">Deployment involves provisioning resources on an active Azure subscription and deploying (uploading) the backend and frontend code for the application to Azure.</span></span> <span data-ttu-id="8c3fe-198">Das Back-End verwendet eine Vielzahl von Azure-Diensten, einschließlich Azure App Service und Azure Bot Service.</span><span class="sxs-lookup"><span data-stu-id="8c3fe-198">The backend uses a variety of Azure services, including Azure App Service and Azure Bot Service.</span></span>

</details>

## <a name="see-also"></a><span data-ttu-id="8c3fe-199">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="8c3fe-199">See also</span></span>

* [<span data-ttu-id="8c3fe-200">Übersicht über Lernprogramme</span><span class="sxs-lookup"><span data-stu-id="8c3fe-200">Tutorials Overview</span></span>](code-samples.md) 
* [<span data-ttu-id="8c3fe-201">Erstellen einer App mit React</span><span class="sxs-lookup"><span data-stu-id="8c3fe-201">Create an app using React</span></span>](first-app-react.md)
* [<span data-ttu-id="8c3fe-202">Erstellen einer App mitHilfe von Blatter</span><span class="sxs-lookup"><span data-stu-id="8c3fe-202">Create an app using Blazor</span></span>](first-app-blazor.md)
* [<span data-ttu-id="8c3fe-203">Erstellen einer App mit SPFx</span><span class="sxs-lookup"><span data-stu-id="8c3fe-203">Create an app using SPFx</span></span>](first-app-spfx.md)
* [<span data-ttu-id="8c3fe-204">Erstellen einer App mithilfe von C# oder .NET</span><span class="sxs-lookup"><span data-stu-id="8c3fe-204">Create an app using C# or .NET</span></span>](get-started-dotnet-app-studio.md)
* [<span data-ttu-id="8c3fe-205">Erstellen einer App mithilfe von Node.js</span><span class="sxs-lookup"><span data-stu-id="8c3fe-205">Create an app using Node.js</span></span>](get-started-nodejs-app-studio.md)
* [<span data-ttu-id="8c3fe-206">Erstellen einer App mithilfe des Yeoman-Generators</span><span class="sxs-lookup"><span data-stu-id="8c3fe-206">Create an app using Yeoman generator</span></span>](get-started-yeoman.md)
* [<span data-ttu-id="8c3fe-207">Erstellen einer Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="8c3fe-207">Create a messaging extension</span></span>](first-message-extension.md)
* [<span data-ttu-id="8c3fe-208">Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="8c3fe-208">Code Samples</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples)