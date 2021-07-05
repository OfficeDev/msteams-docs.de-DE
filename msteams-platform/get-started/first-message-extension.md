---
title: Erste Schritte – Erstellen Sie Ihre erste Messaging-Erweiterung
author: adrianhall
description: Erstellen Sie mithilfe des Teams Toolkits eine Messaging-Erweiterung für Microsoft Teams.
ms.author: adhal
ms.date: 05/20/2021
ms.topic: quickstart
ms.openlocfilehash: 3566bc55c9995a8407b1344fbdb7d1548e210046
ms.sourcegitcommit: 9d63611974ba8a7e7f19ceea35e50189a2e90434
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2021
ms.locfileid: "53254288"
---
# <a name="build-and-run-your-first-messaging-extension-for-microsoft-teams"></a><span data-ttu-id="ecaf5-103">Erstellen Sie Ihre erste Messaging-Erweiterung für Microsoft Teams, und führen Sie sie aus.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-103">Build and run your first messaging extension for Microsoft Teams</span></span>

<span data-ttu-id="ecaf5-104">In diesem Lernprogramm erfahren Sie, wie Sie einen *Suchbefehl* erstellen, um nach externen Daten zu suchen und die Ergebnisse in eine Nachricht einzufügen.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-104">In this tutorial, you will learn how to create a *search command* to search for external data and insert the results into a message.</span></span> 

<span data-ttu-id="ecaf5-105">Es gibt zwei Arten von Teams-**Messaging-Erweiterungen**:</span><span class="sxs-lookup"><span data-stu-id="ecaf5-105">There are two types of Teams **messaging extensions**:</span></span>

- <span data-ttu-id="ecaf5-106">Mit [Suchbefehlen](../messaging-extensions/how-to/search-commands/define-search-command.md) können Sie externe Systeme durchsuchen und die Ergebnisse dieser Suche in Form einer Karte in eine Nachricht einfügen.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-106">[Search commands](../messaging-extensions/how-to/search-commands/define-search-command.md) allow you to search external systems and insert the results of that search into a message in the form of a card.</span></span>
- <span data-ttu-id="ecaf5-107">[Aktionsbefehle](../messaging-extensions/how-to/action-commands/define-action-command.md) ermöglichen Ihnen, Ihren Benutzern ein modales Popupfenster zum Sammeln oder Anzeigen von Informationen vorzuführen, ihre Interaktion zu verarbeiten und Informationen an Teams zurückzusenden.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-107">[Action commands](../messaging-extensions/how-to/action-commands/define-action-command.md) allow you present your users with a modal popup to collect or display information, then process their interaction and send information back to Teams.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="ecaf5-108">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="ecaf5-108">Before you begin</span></span>

<span data-ttu-id="ecaf5-109">Stellen Sie sicher, dass Ihre Entwicklungsumgebung eingerichtet ist, indem Sie die erforderlichen Komponenten installieren.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-109">Make sure your development environment is set up by installing the Prerequisites.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ecaf5-110">Installieren erforderlicher Komponenten</span><span class="sxs-lookup"><span data-stu-id="ecaf5-110">Install Prerequisites</span></span>](prerequisites.md)

## <a name="create-your-project"></a><span data-ttu-id="ecaf5-111">Erstellen Ihres Projekts</span><span class="sxs-lookup"><span data-stu-id="ecaf5-111">Create your project</span></span>

<span data-ttu-id="ecaf5-112">Verwenden Sie zum Erstellen Ihres ersten Projekts das Microsoft Teams-Toolkit:</span><span class="sxs-lookup"><span data-stu-id="ecaf5-112">Use the Teams Toolkit to create your first project:</span></span>

# <a name="visual-studio-code"></a>[<span data-ttu-id="ecaf5-113">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="ecaf5-113">Visual Studio Code</span></span>](#tab/vscode)

1. <span data-ttu-id="ecaf5-114">Öffnen Sie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-114">Open Visual Studio Code.</span></span>
1. <span data-ttu-id="ecaf5-115">Wählen Sie das Symbol Teams in der Seitenleiste aus, um das Teams Toolkit zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-115">Select the Teams icon in the sidebar to open the Teams Toolkit.</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="Das Microsoft Teams-Symbol in der Visual Studio Code-Randleiste.":::

1. <span data-ttu-id="ecaf5-117">Klicken Sie auf **Neues Projekt erstellen**.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-117">Select **Create New Project**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project.png" alt-text="Ort des Links „Neues Projekt erstellen“ in der Randleiste des Microsoft Teams-Toolkits.":::

1. <span data-ttu-id="ecaf5-119">Wählen Sie **Neue Microsoft Teams-App erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-119">Select **Create a new Teams app**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-new-project-intro.png" alt-text="Starten des Assistenten für „Neues Projekt erstellen“":::

1. <span data-ttu-id="ecaf5-121">Wählen Sie im Abschnitt **"Funktionen auswählen"** die Option **"Nachrichtenerweiterung"** aus, deaktivieren Sie **die Option "Registerkarte",** und wählen Sie **"OK"** aus.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-121">In the **Select capabilities** section, select **Message Extension**, deselect **Tab** and select **OK**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/msgextn-create-project-capabilities.png" alt-text="Screenshot, der zeigt, wie Ihrer neuen App Funktionen hinzufügt werden können.":::

1. <span data-ttu-id="ecaf5-123">Wählen Sie im Abschnitt **"Bot-Registrierung"** die Option **"Neue Bot-Registrierung erstellen"** aus.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-123">In the **Bot registration** section, select **Create a new bot registration**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-bot-registration.png" alt-text="Wählen Sie „Eine neue Registrierung eines Bots erstellen“ aus":::

   > [!NOTE]
   > <span data-ttu-id="ecaf5-125">Messaging-Erweiterungen sind auf Bots angewiesen, um ein Dialogfeld zwischen Benutzer und Code zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-125">Messaging extensions rely on bots to provide a dialog between the user and your code.</span></span>

1. <span data-ttu-id="ecaf5-126">Wählen Sie im Abschnitt **"Programmiersprache"** **JavaScript** aus.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-126">In the **Programming Language** section, select **JavaScript**.</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-programming-languages.png" alt-text="Screenshot, der zeigt, wie die Programmiersprache ausgewählt wird.":::

1. <span data-ttu-id="ecaf5-128">Wählen Sie einen Arbeitsbereichsordner aus.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-128">Select a workspace folder.</span></span>  <span data-ttu-id="ecaf5-129">Innerhalb Ihres Arbeitsbereichsordners wird für das von Ihnen erstellte Projekt ein Ordner erstellt.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-129">A folder will be created within your workspace folder for the project you are creating.</span></span>

1. <span data-ttu-id="ecaf5-130">Geben Sie einen passenden Namen für Ihre App ein, wie z. B. `helloworld`.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-130">Enter a suitable name for your app, like `helloworld`.</span></span>  <span data-ttu-id="ecaf5-131">Der Name der App darf nur aus alphanumerischen Zeichen bestehen.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-131">The name of the app must consist only of alphanumeric characters.</span></span>  <span data-ttu-id="ecaf5-132">Drücken Sie die **EINGABETASTE**, um fortzufahren.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-132">Press **Enter** to continue.</span></span>

   <span data-ttu-id="ecaf5-133">Ihre Microsoft Teams-App wird innerhalb weniger Sekunden erstellt.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-133">Your Teams app will be created within a few seconds.</span></span>

# <a name="command-line"></a>[<span data-ttu-id="ecaf5-134">Befehlszeile</span><span class="sxs-lookup"><span data-stu-id="ecaf5-134">Command line</span></span>](#tab/cli)

<span data-ttu-id="ecaf5-135">Verwenden Sie die `teamsfx`-CLI zum Erstellen Ihres ersten Projekts.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-135">Use the `teamsfx` CLI to create your first project.</span></span>  <span data-ttu-id="ecaf5-136">Beginnen Sie in dem Ordner, in dem Sie den Projektordner erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-136">Start from the folder where you want to create the project folder.</span></span>

``` bash
teamsfx new
```

<span data-ttu-id="ecaf5-137">Die CLI führt durch einige Fragen zum Erstellen des Projekts.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-137">The CLI walks through some questions to create the project.</span></span>  <span data-ttu-id="ecaf5-138">Bei jeder Frage wird angegeben, wie Sie sie beantworten können (z. B. mithilfe von Pfeiltasten, um eine Option auszuwählen).</span><span class="sxs-lookup"><span data-stu-id="ecaf5-138">Each question will tell you how to answer it (for example, to use arrow keys to select an option).</span></span>  <span data-ttu-id="ecaf5-139">Wenn Sie eine Frage beantwortet haben, bestätigen Sie Ihre Auswahl, indem Sie die **EINGABETASTE** drücken.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-139">When you have answered the question, confirm your choice by pressing **Enter**.</span></span>

1. <span data-ttu-id="ecaf5-140">Wählen Sie **Neue Microsoft Teams-App erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-140">Select **Create a new Teams app**.</span></span>
1. <span data-ttu-id="ecaf5-141">Wählen Sie die **Nachrichtenerweiterung aus,** und deaktivieren Sie **die Registerkarte**.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-141">Select the **Message Extension** and deselect **Tab**.</span></span>
1. <span data-ttu-id="ecaf5-142">Wählen Sie **Eine neue Registrierung eines Bots erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-142">Select **Create a new bot registration**.</span></span>
1. <span data-ttu-id="ecaf5-143">Wählen Sie **JavaScript** als Programmiersprache aus.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-143">Select **JavaScript** as the programming language.</span></span>
1. <span data-ttu-id="ecaf5-144">Drücken Sie die **EINGABETASTE**, um den Standardordner des Arbeitsbereichs auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-144">Press **Enter** to select the default workspace folder.</span></span>
1. <span data-ttu-id="ecaf5-145">Geben Sie einen passenden Namen für Ihre App ein, wie z. B. `helloworld`.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-145">Enter a suitable name for your app, like `helloworld`.</span></span>  <span data-ttu-id="ecaf5-146">Der Name der App darf nur aus alphanumerischen Zeichen bestehen.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-146">The name of the app must consist only of alphanumeric characters.</span></span>

   <span data-ttu-id="ecaf5-147">Nachdem alle Fragen beantwortet wurden, wird Ihr Projekt erstellt.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-147">After all the questions have been answered, your project is created.</span></span>

---

## <a name="take-a-tour-of-the-source-code"></a><span data-ttu-id="ecaf5-148">Machen Sie einen Rundgang durch den Quellcode</span><span class="sxs-lookup"><span data-stu-id="ecaf5-148">Take a tour of the source code</span></span>

<span data-ttu-id="ecaf5-149">Wenn Sie diesen Abschnitt vorerst überspringen möchten, können Sie [Ihre App lokal ausführen](#run-your-app-locally).</span><span class="sxs-lookup"><span data-stu-id="ecaf5-149">If you wish to skip this section for now, you can [run your app locally](#run-your-app-locally).</span></span>

<span data-ttu-id="ecaf5-150">Eine Messaging-Erweiterung verwendet das [Bot-Framework](https://docs.botframework.com), um dem Benutzer die Interaktion mit Ihrem Dienst über eine Unterhaltung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-150">A messaging extension uses the [Bot Framework](https://docs.botframework.com) to allow the user to interact with your service via a conversation.</span></span>  <span data-ttu-id="ecaf5-151">Nach der Gerüsterstellung wird Ihr Projekt folgend aussehen:</span><span class="sxs-lookup"><span data-stu-id="ecaf5-151">After scaffolding, your project will look like this:</span></span>

:::image type="content" source="../assets/images/teams-toolkit-v2/msgextn-file-layout.png" alt-text="Dateilayout eines Bot-Projekts.":::

<span data-ttu-id="ecaf5-153">Der Bot-Code wird im `bot` Verzeichnis gespeichert.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-153">The bot code is stored in the `bot` directory.</span></span>  <span data-ttu-id="ecaf5-154">Das `bot/messageExtensionBot.js` ist der Haupteinsteigerpunkt der Messaging-Erweiterung.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-154">The `bot/messageExtensionBot.js` is the main entry point for the messaging extension.</span></span>

> [!Tip]
> <span data-ttu-id="ecaf5-155">Machen Sie sich mit Bots außerhalb von Teams vertraut, bevor Sie Ihren ersten Bot in Teams integrieren.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-155">Familiarize yourself with bots outside of Teams before you integrate your first bot within Teams.</span></span>  <span data-ttu-id="ecaf5-156">Sie können weitere Informationen zu Bots im Lernprogramme von [Azure Bot Service](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true) finden.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-156">You can find more information about bots by reviewing the [Azure Bot Service](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true) tutorials.</span></span>

## <a name="run-your-app-locally"></a><span data-ttu-id="ecaf5-157">Lokales Ausführen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="ecaf5-157">Run your app locally</span></span>

<span data-ttu-id="ecaf5-158">Das Teams-Toolkit ermöglicht es Ihnen, Ihre App lokal zu hosten.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-158">Teams Toolkit allows you to host your app locally.</span></span>  <span data-ttu-id="ecaf5-159">Gehen Sie hierfür folgendermaßen vor:</span><span class="sxs-lookup"><span data-stu-id="ecaf5-159">To do this:</span></span>

- <span data-ttu-id="ecaf5-160">Eine Azure Active Directory-Anwendung ist im M365-Mandanten registriert.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-160">An Azure Active Directory Application is registered within the M365 tenant.</span></span>
- <span data-ttu-id="ecaf5-161">Ein App-Manifest wurde dem Entwicklerportal für Teams übermittelt.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-161">An app manifest is submitted to the Developer Portal for Teams.</span></span>
- <span data-ttu-id="ecaf5-162">Eine API wird mittels des Azure Functions Core Tools ausgeführt, um Ihre App zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-162">An API is run locally using Azure Functions Core Tools to support your app.</span></span>
- <span data-ttu-id="ecaf5-163">[ngrok](https://ngrok.io) ist installiert und dazu verwendet, eine Tunnel zwischen Teams und Ihrer Messaging-Erweiterung bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-163">[ngrok](https://ngrok.io) is installed and used to provide a tunnel between Teams and your messaging extension.</span></span>

<span data-ttu-id="ecaf5-164">So erstellen Sie Ihre App und führen sie lokal aus:</span><span class="sxs-lookup"><span data-stu-id="ecaf5-164">To build and run your app locally:</span></span>

1. <span data-ttu-id="ecaf5-165">Drücken Sie Visual Studio Code die **F5-Taste,** um die Anwendung im Debugmodus auszuführen.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-165">From Visual Studio Code, press the **F5** key to run your application in debug mode.</span></span>

   > <span data-ttu-id="ecaf5-166">Wenn Sie die App zum ersten Mal ausführen, werden alle Abhängigkeiten heruntergeladen und die App wird erstellt.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-166">When you run the app for the first time, all dependencies are downloaded and the app is built.</span></span>  <span data-ttu-id="ecaf5-167">Wenn die Erstellung abgeschlossen ist, wird automatisch ein Browserfenster geöffnet.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-167">A browser window automatically opens when the build is complete.</span></span>  <span data-ttu-id="ecaf5-168">Diese Änderung kann 3-5 Minuten dauern.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-168">This can take 3-5 minutes to complete.</span></span>

1. <span data-ttu-id="ecaf5-169">Teams wird in einem Webbrowser geladen, und Sie werden dazu aufgefordert, sich anzumelden.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-169">Teams will be loaded in a web browser, and you will be prompted to sign in.</span></span> <span data-ttu-id="ecaf5-170">Wenn Sie zum Öffnen von Microsoft Teams aufgefordert werden, wählen Sie „Abbrechen“ aus, um im Browser zu verbleiben.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-170">If prompted to open Microsoft Teams, select Cancel to remain within the browser.</span></span> <span data-ttu-id="ecaf5-171">Melden Sie sich mit Ihrem M365-Konto an.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-171">Sign in with your M365 account.</span></span>

1. <span data-ttu-id="ecaf5-172">Wählen Sie **"Hinzufügen"** aus, um die App Ihrem Konto hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-172">Select **Add** to add the app to your account.</span></span>

   <span data-ttu-id="ecaf5-173">Nachdem die App geladen wurde, werden Sie direkt in ein Suchdialogfeld geleitet:</span><span class="sxs-lookup"><span data-stu-id="ecaf5-173">After the app is loaded, you will be taken directly to a search dialog:</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/msgextn-completed-app.png" alt-text="Suchbasierte Messaging-Erweiterung in Aktion":::

   <span data-ttu-id="ecaf5-175">Geben Sie einen Text in das Suchfeld ein, und wählen Sie dann eine der Optionen aus.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-175">Type some text in the search box, then select one of the options.</span></span>  <span data-ttu-id="ecaf5-176">Ihrem Eingabefeld wird eine adaptive Karte hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-176">An adaptive card will be added to your input box.</span></span>

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="ecaf5-177">Erfahren Sie, was passiert, wenn Sie Ihre App lokal im Debugger ausführen.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-177">Learn what happens when you run your app locally in the debugger.</span></span></summary>

<span data-ttu-id="ecaf5-178">Wenn Sie **F5** drücken, hat das Teams Toolkit Folgendes:</span><span class="sxs-lookup"><span data-stu-id="ecaf5-178">When you press the **F5** key, the Teams Toolkit:</span></span>

1. <span data-ttu-id="ecaf5-179">Registriert Ihre Anwendung bei Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-179">Registers your application with Azure Active Directory.</span></span>
1. <span data-ttu-id="ecaf5-180">Registriert Ihre Anwendung für das "Querladen" in Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-180">Registers your application for "side loading" in Microsoft Teams.</span></span>
1. <span data-ttu-id="ecaf5-181">Startet ihr Anwendungs-Back-End, das lokal mithilfe von [Azure Function Core Tools](/azure/azure-functions/functions-run-local?#start)ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-181">Starts your application backend running locally using [Azure Function Core Tools](/azure/azure-functions/functions-run-local?#start).</span></span>
1. <span data-ttu-id="ecaf5-182">Startet einen ngrok-Tunnel, damit Teams mit Ihrer App kommunizieren können.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-182">Starts an ngrok tunnel so Teams can communicate with your app.</span></span>
1. <span data-ttu-id="ecaf5-183">Startet Microsoft Teams mit einem Befehl, um Teams anzuweisen, die Anwendung querzuladen.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-183">Starts Microsoft Teams with a command to instruct Teams to sideload the application.</span></span>

</details>

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="ecaf5-184">Erfahren Sie, wie Sie häufige Probleme bei dem lokalen Ausführen Ihrer App lösen können.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-184">Learn how to troubleshoot common issues when running your app locally.</span></span></summary>

<span data-ttu-id="ecaf5-185">Um Ihre App in Teams erfolgreich auszuführen, müssen Sie ein Microsoft 365-Entwicklungskonto haben, das das Querladen von Apps ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-185">To successfully run your app in Teams, you must have a Microsoft 365 development account that allows app sideloading.</span></span> <span data-ttu-id="ecaf5-186">Weitere Informationen zum Öffnen von Apps finden Sie unter [Erforderliche Komponenten](prerequisites.md#enable-sideloading).</span><span class="sxs-lookup"><span data-stu-id="ecaf5-186">For more information on account opening, see [Prerequisites](prerequisites.md#enable-sideloading).</span></span>

> [!TIP]
> <span data-ttu-id="ecaf5-187">Überprüfen Sie mithilfe des [Tools für die App-Überprüfung](https://dev.teams.microsoft.com/appvalidation.html), das im Toolkit enthalten ist, ob es Probleme gibt, bevor Sie ihre App querladen.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-187">Check for issues before sideloading your app, using the [app validation tool](https://dev.teams.microsoft.com/appvalidation.html), which is included in the toolkit.</span></span> <span data-ttu-id="ecaf5-188">Beheben Sie die Probleme, um die App erfolgreich querzuladen.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-188">Fix the errors to successfully sideload the app.</span></span>
</details>

[!INCLUDE [Provision and Deploy your app on Azure](~/includes/get-started/azure-provisioning-instructions.md)]

<!-- markdownlint-disable MD033 -->

<details>
<summary><span data-ttu-id="ecaf5-189">Erfahren Sie, was geschieht, wenn Sie Ihre App in Azure bereitstellen</span><span class="sxs-lookup"><span data-stu-id="ecaf5-189">Learn what happens when you deployed your app to Azure</span></span></summary>

<span data-ttu-id="ecaf5-190">Vor der Bereitstellung wurde die Anwendung lokal ausgeführt:</span><span class="sxs-lookup"><span data-stu-id="ecaf5-190">Before deployment, the application has been running locally:</span></span>

1. <span data-ttu-id="ecaf5-191">Das Back-End unter Verwendung von _Azure Functions Core Tools_ ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-191">The backend runs using _Azure Functions Core Tools_.</span></span>
1. <span data-ttu-id="ecaf5-192">Der HTTP-Endpunkt der Anwendung, an dem Microsoft Teams die Anwendung lädt, wird lokal ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-192">The application HTTP endpoint, where Microsoft Teams loads the application, runs locally.</span></span>

<span data-ttu-id="ecaf5-193">Die Bereitstellung umfasst das Bereitstellen von Ressourcen für ein aktives Azure-Abonnement und das Bereitstellen (Hochladen) des Back-End- und des Frontend-Codes für die Anwendung in Azure.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-193">Deployment involves provisioning resources on an active Azure subscription and deploying (uploading) the backend and frontend code for the application to Azure.</span></span> <span data-ttu-id="ecaf5-194">Das Back-End verwendet eine Vielzahl von Azure-Diensten, einschließlich Azure App Service und Azure Bot Service.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-194">The backend uses a variety of Azure services, including Azure App Service and Azure Bot Service.</span></span>

</details>

## <a name="add-a-configuration-page-to-your-messaging-extension"></a><span data-ttu-id="ecaf5-195">Hinzufügen einer Konfigurationsseite zu Ihrer Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="ecaf5-195">Add a configuration page to your messaging extension</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

## <a name="code-sample"></a><span data-ttu-id="ecaf5-196">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="ecaf5-196">Code sample</span></span>

<span data-ttu-id="ecaf5-197">Die Teams Search Auth Config for sample projects on GitHub, demonstrate how to create messaging extensions that include a configuration page and [Bot Service authentication.](https://github.com/microsoft/BotBuilder-Samples#teams-samples)</span><span class="sxs-lookup"><span data-stu-id="ecaf5-197">The Teams Search Auth Config for sample projects on GitHub, demonstrate how to create messaging extensions that include a configuration page and [Bot Service authentication](https://github.com/microsoft/BotBuilder-Samples#teams-samples).</span></span> <span data-ttu-id="ecaf5-198">Die Beispiele zeigen auch, wie Sie Nachrichtenerweiterungen erstellen, die Suchanforderungen akzeptieren und die Ergebnisse zurückgeben, nachdem sich der Benutzer angemeldet hat.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-198">The samples also demonstrate how to create message extensions that accept search requests and return the results after the user has signed in.</span></span>

| <span data-ttu-id="ecaf5-199">**Beispielname**</span><span class="sxs-lookup"><span data-stu-id="ecaf5-199">**Sample name**</span></span> | <span data-ttu-id="ecaf5-200">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="ecaf5-200">**Description**</span></span> | <span data-ttu-id="ecaf5-201">**.NET**</span><span class="sxs-lookup"><span data-stu-id="ecaf5-201">**.NET**</span></span> | <span data-ttu-id="ecaf5-202">**Node.js**</span><span class="sxs-lookup"><span data-stu-id="ecaf5-202">**Node.js**</span></span> | <span data-ttu-id="ecaf5-203">**Python**</span><span class="sxs-lookup"><span data-stu-id="ecaf5-203">**Python**</span></span> |
|-----------------|-----------------|-------------|--------------|--------|
| <span data-ttu-id="ecaf5-204">Bot-Generator</span><span class="sxs-lookup"><span data-stu-id="ecaf5-204">Bot builder</span></span> | <span data-ttu-id="ecaf5-205">So erstellen Sie Messaging-Erweiterungen.</span><span class="sxs-lookup"><span data-stu-id="ecaf5-205">To create messaging extensions.</span></span> | [<span data-ttu-id="ecaf5-206">View</span><span class="sxs-lookup"><span data-stu-id="ecaf5-206">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config) | [<span data-ttu-id="ecaf5-207">View</span><span class="sxs-lookup"><span data-stu-id="ecaf5-207">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/52.teams-messaging-extensions-search-auth-config) | [<span data-ttu-id="ecaf5-208">View</span><span class="sxs-lookup"><span data-stu-id="ecaf5-208">View</span></span>]( https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/50.teams-messaging-extension-search) |

## <a name="additional-code-sample"></a><span data-ttu-id="ecaf5-209">Zusätzliches Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="ecaf5-209">Additional code sample</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ecaf5-210">Weitere Bot Framework-Beispiele auf GitHub anzeigen</span><span class="sxs-lookup"><span data-stu-id="ecaf5-210">View more Bot Framework Samples on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-samples#messaging-extensions-samples-using-the-v4-sdk)

## <a name="see-also"></a><span data-ttu-id="ecaf5-211">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="ecaf5-211">See also</span></span>

* [<span data-ttu-id="ecaf5-212">Übersicht über Lernprogramme</span><span class="sxs-lookup"><span data-stu-id="ecaf5-212">Tutorials Overview</span></span>](code-samples.md) 
* [<span data-ttu-id="ecaf5-213">Erstellen einer App mit React</span><span class="sxs-lookup"><span data-stu-id="ecaf5-213">Create an app using React</span></span>](first-app-react.md)
* [<span data-ttu-id="ecaf5-214">Erstellen einer App mitHilfe von Blatter</span><span class="sxs-lookup"><span data-stu-id="ecaf5-214">Create an app using Blazor</span></span>](first-app-blazor.md)
* [<span data-ttu-id="ecaf5-215">Erstellen einer App mit SPFx</span><span class="sxs-lookup"><span data-stu-id="ecaf5-215">Create an app using SPFx</span></span>](first-app-spfx.md)
* [<span data-ttu-id="ecaf5-216">Erstellen einer App mithilfe von C# oder .NET</span><span class="sxs-lookup"><span data-stu-id="ecaf5-216">Create an app using C# or .NET</span></span>](get-started-dotnet-app-studio.md)
* [<span data-ttu-id="ecaf5-217">Erstellen einer App mithilfe von Node.js</span><span class="sxs-lookup"><span data-stu-id="ecaf5-217">Create an app using Node.js</span></span>](get-started-nodejs-app-studio.md)
* [<span data-ttu-id="ecaf5-218">Erstellen einer App mithilfe des Yeoman-Generators</span><span class="sxs-lookup"><span data-stu-id="ecaf5-218">Create an app using Yeoman generator</span></span>](get-started-yeoman.md)
* [<span data-ttu-id="ecaf5-219">Erstellen einer Unterhaltungs-Bot-App</span><span class="sxs-lookup"><span data-stu-id="ecaf5-219">Create a conversational bot app</span></span>](first-app-bot.md)
* [<span data-ttu-id="ecaf5-220">Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="ecaf5-220">Code Samples</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples)