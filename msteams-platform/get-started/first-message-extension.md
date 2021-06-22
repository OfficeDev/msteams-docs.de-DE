---
title: Erste Schritte – Erstellen Sie Ihre erste Messaging-Erweiterung
author: adrianhall
description: Erstellen Sie mithilfe des Teams Toolkits eine Messaging-Erweiterung für Microsoft Teams.
ms.author: adhal
ms.date: 05/20/2021
ms.topic: quickstart
ms.openlocfilehash: cb37bc97c3b9de8ce469728e4c1b0e09ba1c2942
ms.sourcegitcommit: 99b1f151e4e36a86c6a5d2ccbde01bf45b61f526
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2021
ms.locfileid: "53037635"
---
# <a name="build-and-run-your-first-messaging-extension-for-microsoft-teams"></a><span data-ttu-id="6993f-103">Erstellen Sie Ihre erste Messaging-Erweiterung für Microsoft Teams, und führen Sie sie aus.</span><span class="sxs-lookup"><span data-stu-id="6993f-103">Build and run your first messaging extension for Microsoft Teams</span></span>

<span data-ttu-id="6993f-104">Es gibt zwei Arten von Teams-**Messaging-Erweiterungen**:</span><span class="sxs-lookup"><span data-stu-id="6993f-104">There are two types of Teams **messaging extensions**:</span></span>

- <span data-ttu-id="6993f-105">Mit [Suchbefehlen](../messaging-extensions/how-to/search-commands/define-search-command.md) können Sie externe Systeme durchsuchen und die Ergebnisse dieser Suche in Form einer Karte in eine Nachricht einfügen.</span><span class="sxs-lookup"><span data-stu-id="6993f-105">[Search commands](../messaging-extensions/how-to/search-commands/define-search-command.md) allow you to search external systems and insert the results of that search into a message in the form of a card.</span></span>
- <span data-ttu-id="6993f-106">[Aktionsbefehle](../messaging-extensions/how-to/action-commands/define-action-command.md) ermöglichen Ihnen, Ihren Benutzern ein modales Popupfenster zum Sammeln oder Anzeigen von Informationen vorzuführen, ihre Interaktion zu verarbeiten und Informationen an Teams zurückzusenden.</span><span class="sxs-lookup"><span data-stu-id="6993f-106">[Action commands](../messaging-extensions/how-to/action-commands/define-action-command.md) allow you present your users with a modal popup to collect or display information, then process their interaction and send information back to Teams.</span></span>

<span data-ttu-id="6993f-107">In diesem Tutorial erstellen Sie einen *Suchbefehl*, um nach externen Daten zu suchen und die Ergebnisse in eine Nachricht einzufügen.</span><span class="sxs-lookup"><span data-stu-id="6993f-107">In this tutorial, you will create a *search command* to search for external data and insert the results into a message.</span></span>  

## <a name="before-you-begin"></a><span data-ttu-id="6993f-108">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="6993f-108">Before you begin</span></span>

<span data-ttu-id="6993f-109">Stellen Sie sicher, dass Ihre Entwicklungsumgebung eingerichtet ist, indem Sie [Installieren erforderlicher Komponenten](prerequisites.md)</span><span class="sxs-lookup"><span data-stu-id="6993f-109">Make sure your development environment is set up by installing the [Prerequisites](prerequisites.md)</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6993f-110">Installieren erforderlicher Komponenten</span><span class="sxs-lookup"><span data-stu-id="6993f-110">Install Prerequisites</span></span>](prerequisites.md)

## <a name="create-your-project"></a><span data-ttu-id="6993f-111">Erstellen Ihres Projekts</span><span class="sxs-lookup"><span data-stu-id="6993f-111">Create your project</span></span>

<span data-ttu-id="6993f-112">Verwenden Sie zum Erstellen Ihres ersten Projekts das Microsoft Teams-Toolkit:</span><span class="sxs-lookup"><span data-stu-id="6993f-112">Use the Teams Toolkit to create your first project:</span></span>

# <a name="visual-studio-code"></a>[<span data-ttu-id="6993f-113">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="6993f-113">Visual Studio Code</span></span>](#tab/vscode)

1. <span data-ttu-id="6993f-114">Öffnen Sie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="6993f-114">Open Visual Studio Code.</span></span>
1. <span data-ttu-id="6993f-115">Öffnen Sie das Teams-Toolkit, indem Sie das Teams-Symbol in der Randleiste auswählen:</span><span class="sxs-lookup"><span data-stu-id="6993f-115">Open the Teams Toolkit by selecting the Teams icon in the sidebar:</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="Das Microsoft Teams-Symbol in der Visual Studio Code-Randleiste.":::

1. <span data-ttu-id="6993f-117">Klicken Sie auf **Neues Projekt erstellen**.</span><span class="sxs-lookup"><span data-stu-id="6993f-117">Select **Create New Project**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project.png" alt-text="Ort des Links „Neues Projekt erstellen“ in der Randleiste des Microsoft Teams-Toolkits.":::

1. <span data-ttu-id="6993f-119">Wählen Sie **Neue Microsoft Teams-App erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="6993f-119">Select **Create a new Teams app**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-new-project-intro.png" alt-text="Assistenten für „Neues Projekt erstellen“ starten":::

1. <span data-ttu-id="6993f-121">Wählen Sie im Schritt **Funktionen auswählen** die Option **Nachrichtenerweiterung** aus und heben Sie die Auswahl **Registerkarte** auf. Drücken Sie **OK**.</span><span class="sxs-lookup"><span data-stu-id="6993f-121">On the **Select capabilities** step, select **Message Extension** and deselect **Tab**.  Press **OK**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/msgextn-create-project-capabilities.png" alt-text="Screenshot, der zeigt, wie Funktionen Ihrer neuen App hinzufügt werden können.":::

1. <span data-ttu-id="6993f-123">Wählen Sie im Schritt **Registrierung eines Bots** die Option **Eine neue Registrierung eines Bots erstellen**.</span><span class="sxs-lookup"><span data-stu-id="6993f-123">On the **Bot registration** step, select **Create a new bot registration**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-bot-registration.png" alt-text="Wählen Sie „Eine neue Registrierung eines Bots erstellen“ aus":::

   > [!NOTE]
   > <span data-ttu-id="6993f-125">Messaging-Erweiterungen sind auf Bots angewiesen, um ein Dialogfeld zwischen Benutzer und Code zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="6993f-125">Messaging extensions rely on bots to provide a dialog between the user and your code.</span></span>

1. <span data-ttu-id="6993f-126">Wählen Sie im Schritt **Programmiersprache** die Option **JavaScript** aus.</span><span class="sxs-lookup"><span data-stu-id="6993f-126">On the **Programming Language** step, select **JavaScript**.</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-programming-languages.png" alt-text="Screenshot, der zeigt, wie die Programmiersprache ausgewählt wird.":::

1. <span data-ttu-id="6993f-128">Wählen Sie einen Arbeitsbereichsordner aus.</span><span class="sxs-lookup"><span data-stu-id="6993f-128">Select a workspace folder.</span></span>  <span data-ttu-id="6993f-129">Innerhalb Ihres Arbeitsbereichsordners wird für das von Ihnen erstellte Projekt ein Ordner erstellt.</span><span class="sxs-lookup"><span data-stu-id="6993f-129">A folder will be created within your workspace folder for the project you are creating.</span></span>

1. <span data-ttu-id="6993f-130">Geben Sie einen passenden Namen für Ihre App ein, wie z. B. `helloworld`.</span><span class="sxs-lookup"><span data-stu-id="6993f-130">Enter a suitable name for your app, like `helloworld`.</span></span>  <span data-ttu-id="6993f-131">Der Name der App darf nur aus alphanumerischen Zeichen bestehen.</span><span class="sxs-lookup"><span data-stu-id="6993f-131">The name of the app must consist only of alphanumeric characters.</span></span>  <span data-ttu-id="6993f-132">Drücken Sie die **EINGABETASTE**, um fortzufahren.</span><span class="sxs-lookup"><span data-stu-id="6993f-132">Press **Enter** to continue.</span></span>

<span data-ttu-id="6993f-133">Ihre Microsoft Teams-App wird innerhalb weniger Sekunden erstellt.</span><span class="sxs-lookup"><span data-stu-id="6993f-133">Your Teams app will be created within a few seconds.</span></span>

# <a name="command-line"></a>[<span data-ttu-id="6993f-134">Befehlszeile</span><span class="sxs-lookup"><span data-stu-id="6993f-134">Command line</span></span>](#tab/cli)

<span data-ttu-id="6993f-135">Verwenden Sie die `teamsfx`-CLI zum Erstellen Ihres ersten Projekts.</span><span class="sxs-lookup"><span data-stu-id="6993f-135">Use the `teamsfx` CLI to create your first project.</span></span>  <span data-ttu-id="6993f-136">Beginnen Sie in dem Ordner, in dem Sie den Projektordner erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="6993f-136">Start from the folder where you want to create the project folder.</span></span>

``` bash
teamsfx new
```

<span data-ttu-id="6993f-137">Die CLI führt durch einige Fragen zum Erstellen des Projekts.</span><span class="sxs-lookup"><span data-stu-id="6993f-137">The CLI walks through some questions to create the project.</span></span>  <span data-ttu-id="6993f-138">Bei jeder Frage wird angegeben, wie Sie sie beantworten können (z. B. mithilfe von Pfeiltasten, um eine Option auszuwählen).</span><span class="sxs-lookup"><span data-stu-id="6993f-138">Each question will tell you how to answer it (for example, to use arrow keys to select an option).</span></span>  <span data-ttu-id="6993f-139">Wenn Sie eine Frage beantwortet haben, bestätigen Sie Ihre Auswahl, indem Sie die **EINGABETASTE** drücken.</span><span class="sxs-lookup"><span data-stu-id="6993f-139">When you have answered the question, confirm your choice by pressing **Enter**.</span></span>

1. <span data-ttu-id="6993f-140">Wählen Sie **Eine neue Teams-App erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="6993f-140">Select **Create a new Teams app**.</span></span>
1. <span data-ttu-id="6993f-141">Wählen Sie die Funktion **Nachrichtenerweiterung** aus und heben Sie die Auswahl der Funktion **Registerkarte** auf.</span><span class="sxs-lookup"><span data-stu-id="6993f-141">Select the **Message Extension** capability and deselect the **Tab** capability.</span></span>
1. <span data-ttu-id="6993f-142">Wählen Sie **Eine neue Registrierung eines Bots erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="6993f-142">Select **Create a new bot registration**.</span></span>
1. <span data-ttu-id="6993f-143">Wählen Sie **JavaScript** als Programmiersprache aus.</span><span class="sxs-lookup"><span data-stu-id="6993f-143">Select **JavaScript** as the programming language.</span></span>
1. <span data-ttu-id="6993f-144">Drücken Sie die **EINGABETASTE**, um den Standardordner des Arbeitsbereichs auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="6993f-144">Press **Enter** to select the default workspace folder.</span></span>
1. <span data-ttu-id="6993f-145">Geben Sie einen passenden Namen für Ihre App ein, wie z. B. `helloworld`.</span><span class="sxs-lookup"><span data-stu-id="6993f-145">Enter a suitable name for your app, like `helloworld`.</span></span>  <span data-ttu-id="6993f-146">Der Name der App darf nur aus alphanumerischen Zeichen bestehen.</span><span class="sxs-lookup"><span data-stu-id="6993f-146">The name of the app must consist only of alphanumeric characters.</span></span>

<span data-ttu-id="6993f-147">Sobald alle Fragen beantwortet wurden, wird Ihr Projekt erstellt.</span><span class="sxs-lookup"><span data-stu-id="6993f-147">Once all the questions have been answered, your project will be created.</span></span>

---

## <a name="take-a-tour-of-the-source-code"></a><span data-ttu-id="6993f-148">Machen Sie einen Rundgang durch den Quellcode</span><span class="sxs-lookup"><span data-stu-id="6993f-148">Take a tour of the source code</span></span>

<span data-ttu-id="6993f-149">Wenn Sie diesen Abschnitt vorerst überspringen möchten, können Sie [Ihre App lokal ausführen](#run-your-app-locally).</span><span class="sxs-lookup"><span data-stu-id="6993f-149">If you wish to skip this section for now, you can [run your app locally](#run-your-app-locally).</span></span>

<span data-ttu-id="6993f-150">Eine Messaging-Erweiterung verwendet das [Bot-Framework](https://docs.botframework.com), um dem Benutzer die Interaktion mit Ihrem Dienst über eine Unterhaltung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="6993f-150">A messaging extension uses the [Bot Framework](https://docs.botframework.com) to allow the user to interact with your service via a conversation.</span></span>  <span data-ttu-id="6993f-151">Nach der Gerüsterstellung wird Ihr Projekt folgend aussehen:</span><span class="sxs-lookup"><span data-stu-id="6993f-151">After scaffolding, your project will look like this:</span></span>

:::image type="content" source="../assets/images/teams-toolkit-v2/msgextn-file-layout.png" alt-text="Dateilayout eines Bot-Projekts.":::

<span data-ttu-id="6993f-153">Der Bot-Code wird im `bot` Verzeichnis gespeichert.</span><span class="sxs-lookup"><span data-stu-id="6993f-153">The bot code is stored in the `bot` directory.</span></span>  <span data-ttu-id="6993f-154">Das `bot/messageExtensionBot.js` ist der Haupteinsteigerpunkt der Messaging-Erweiterung.</span><span class="sxs-lookup"><span data-stu-id="6993f-154">The `bot/messageExtensionBot.js` is the main entry point for the messaging extension.</span></span>

> [!Tip]
> <span data-ttu-id="6993f-155">Machen Sie sich mit Bots außerhalb von Teams vertraut, bevor Sie Ihren ersten Bot in Teams integrieren.</span><span class="sxs-lookup"><span data-stu-id="6993f-155">Familiarize yourself with bots outside of Teams before you integrate your first bot within Teams.</span></span>  <span data-ttu-id="6993f-156">Sie können weitere Informationen zu Bots im Lernprogramme von [Azure Bot Service](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true) finden.</span><span class="sxs-lookup"><span data-stu-id="6993f-156">You can find more information about bots by reviewing the [Azure Bot Service](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true) tutorials.</span></span>

## <a name="run-your-app-locally"></a><span data-ttu-id="6993f-157">Lokales Ausführen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="6993f-157">Run your app locally</span></span>

<span data-ttu-id="6993f-158">Das Teams-Toolkit ermöglicht es Ihnen, Ihre App lokal zu hosten.</span><span class="sxs-lookup"><span data-stu-id="6993f-158">Teams Toolkit allows you to host your app locally.</span></span>  <span data-ttu-id="6993f-159">Gehen Sie hierfür folgendermaßen vor:</span><span class="sxs-lookup"><span data-stu-id="6993f-159">To do this:</span></span>

- <span data-ttu-id="6993f-160">Eine Azure Active Directory-Anwendung ist im M365-Mandanten registriert.</span><span class="sxs-lookup"><span data-stu-id="6993f-160">An Azure Active Directory Application is registered within the M365 tenant.</span></span>
- <span data-ttu-id="6993f-161">Ein App-Manifest wurde dem Entwicklerportal für Teams übermittelt.</span><span class="sxs-lookup"><span data-stu-id="6993f-161">An app manifest is submitted to the Developer Portal for Teams.</span></span>
- <span data-ttu-id="6993f-162">Eine API wird mittels des Azure Functions Core Tools ausgeführt, um Ihre App zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="6993f-162">An API is run locally using Azure Functions Core Tools to support your app.</span></span>
- <span data-ttu-id="6993f-163">[ngrok](https://ngrok.io) ist installiert und dazu verwendet, eine Tunnel zwischen Teams und Ihrer Messaging-Erweiterung bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="6993f-163">[ngrok](https://ngrok.io) is installed and used to provide a tunnel between Teams and your messaging extension.</span></span>

<span data-ttu-id="6993f-164">So erstellen Sie Ihre App und führen sie lokal aus:</span><span class="sxs-lookup"><span data-stu-id="6993f-164">To build and run your app locally:</span></span>

1. <span data-ttu-id="6993f-165">Drücken Sie in Visual Studio Code **F5**, um die Anwendung im Debugmodus auszuführen.</span><span class="sxs-lookup"><span data-stu-id="6993f-165">From Visual Studio Code, press **F5** to run your application in debug mode.</span></span>

   > <span data-ttu-id="6993f-166">Wenn Sie die App zum ersten Mal ausführen, werden alle Abhängigkeiten heruntergeladen und die App wird erstellt.</span><span class="sxs-lookup"><span data-stu-id="6993f-166">When you run the app for the first time, all dependencies are downloaded and the app is built.</span></span>  <span data-ttu-id="6993f-167">Wenn die Erstellung abgeschlossen ist, wird automatisch ein Browserfenster geöffnet.</span><span class="sxs-lookup"><span data-stu-id="6993f-167">A browser window automatically opens when the build is complete.</span></span>  <span data-ttu-id="6993f-168">Diese Änderung kann 3-5 Minuten dauern.</span><span class="sxs-lookup"><span data-stu-id="6993f-168">This can take 3-5 minutes to complete.</span></span>

1. <span data-ttu-id="6993f-169">Teams wird in einem Webbrowser geladen, und Sie werden dazu aufgefordert, sich anzumelden.</span><span class="sxs-lookup"><span data-stu-id="6993f-169">Teams will be loaded in a web browser, and you will be prompted to sign in.</span></span> <span data-ttu-id="6993f-170">Wenn Sie zum Öffnen von Microsoft Teams aufgefordert werden, wählen Sie „Abbrechen“ aus, um im Browser zu verbleiben.</span><span class="sxs-lookup"><span data-stu-id="6993f-170">If prompted to open Microsoft Teams, select Cancel to remain within the browser.</span></span> <span data-ttu-id="6993f-171">Melden Sie sich mit Ihrem M365-Konto an.</span><span class="sxs-lookup"><span data-stu-id="6993f-171">Sign in with your M365 account.</span></span>

1. <span data-ttu-id="6993f-172">Drücken Sie **Hinzufügen**, um die App zu Ihrem Konto hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="6993f-172">Press **Add** to add the app to your account.</span></span>

<span data-ttu-id="6993f-173">Sobald die App geladen ist, wird Ihnen direkt ein Suchdialogfeld angezeigt:</span><span class="sxs-lookup"><span data-stu-id="6993f-173">Once the app is loaded, you will be taken directly to a search dialog:</span></span>

:::image type="content" source="../assets/images/teams-toolkit-v2/msgextn-completed-app.png" alt-text="Suchbasierte Messaging-Erweiterung in Aktion":::

<span data-ttu-id="6993f-175">Geben Sie einen Text in das Suchfeld ein, und wählen Sie dann eine der Optionen aus.</span><span class="sxs-lookup"><span data-stu-id="6993f-175">Type some text in the search box, then select one of the options.</span></span>  <span data-ttu-id="6993f-176">Ihrem Eingabefeld wird eine adaptive Karte hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="6993f-176">An adaptive card will be added to your input box.</span></span>

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="6993f-177">Erfahren Sie, was passiert, wenn Sie Ihre App lokal im Debugger ausführen.</span><span class="sxs-lookup"><span data-stu-id="6993f-177">Learn what happens when you run your app locally in the debugger.</span></span></summary>

<span data-ttu-id="6993f-178">Wenn Sie F5 gedrückt haben, hat das Microsoft Teams-Toolkit Folgendes getan:</span><span class="sxs-lookup"><span data-stu-id="6993f-178">When you pressed F5, the Teams Toolkit:</span></span>

1. <span data-ttu-id="6993f-179">Ihre Anwendung bei Azure Active Directory registriert.</span><span class="sxs-lookup"><span data-stu-id="6993f-179">Registered your application with Azure Active Directory.</span></span>
1. <span data-ttu-id="6993f-180">Ihre Anwendung bei Microsoft Teams für das „Querladen“ registriert.</span><span class="sxs-lookup"><span data-stu-id="6993f-180">Registered your application for "side loading" in Microsoft Teams.</span></span>
1. <span data-ttu-id="6993f-181">Ihr Anwendungs-Back-End mithilfe von [Azure Function Core Tools](/azure/azure-functions/functions-run-local?#start) lokal gestartet.</span><span class="sxs-lookup"><span data-stu-id="6993f-181">Started your application backend running locally using [Azure Function Core Tools](/azure/azure-functions/functions-run-local?#start).</span></span>
1. <span data-ttu-id="6993f-182">Ein ngrok-Tunnel gestartet, sodass Teams mit Ihrer App kommunizieren kann.</span><span class="sxs-lookup"><span data-stu-id="6993f-182">Started an ngrok tunnel so Teams can communicate with your app.</span></span>
1. <span data-ttu-id="6993f-183">Microsoft Teams mit einem Befehl gestartet, mit dem Teams angewiesen wird, die Anwendung querzuladen.</span><span class="sxs-lookup"><span data-stu-id="6993f-183">Started Microsoft Teams with a command to instruct Teams to sideload the application.</span></span>

</details>

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="6993f-184">Erfahren Sie, wie Sie häufige Probleme bei dem lokalen Ausführen Ihrer App lösen können.</span><span class="sxs-lookup"><span data-stu-id="6993f-184">Learn how to troubleshoot common issues when running your app locally.</span></span></summary>

<span data-ttu-id="6993f-185">Um Ihre App in Teams erfolgreich auszuführen, müssen Sie ein Microsoft 365-Entwicklungskonto haben, das das Querladen von Apps ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="6993f-185">To successfully run your app in Teams, you must have a Microsoft 365 development account that allows app sideloading.</span></span> <span data-ttu-id="6993f-186">Weitere Informationen zum Öffnen von Apps finden Sie unter [Erforderliche Komponenten](prerequisites.md#enable-sideloading).</span><span class="sxs-lookup"><span data-stu-id="6993f-186">For more information on account opening, see [Prerequisites](prerequisites.md#enable-sideloading).</span></span>

> [!TIP]
> <span data-ttu-id="6993f-187">Überprüfen Sie mithilfe des [Tools für die App-Überprüfung](https://dev.teams.microsoft.com/appvalidation.html), das im Toolkit enthalten ist, ob es Probleme gibt, bevor Sie ihre App querladen.</span><span class="sxs-lookup"><span data-stu-id="6993f-187">Check for issues before sideloading your app, using the [app validation tool](https://dev.teams.microsoft.com/appvalidation.html), which is included in the toolkit.</span></span> <span data-ttu-id="6993f-188">Beheben Sie die Probleme, um die App erfolgreich querzuladen.</span><span class="sxs-lookup"><span data-stu-id="6993f-188">Fix the errors to successfully sideload the app.</span></span>
</details>

[!INCLUDE [Provision and Deploy your app on Azure](~/includes/get-started/azure-provisioning-instructions.md)]

<!-- markdownlint-disable MD033 -->

<details>
<summary><span data-ttu-id="6993f-189">Erfahren Sie, was geschieht, wenn Sie Ihre App in Azure bereitstellen</span><span class="sxs-lookup"><span data-stu-id="6993f-189">Learn what happens when you deployed your app to Azure</span></span></summary>

<span data-ttu-id="6993f-190">Vor der Bereitstellung wurde die Anwendung lokal ausgeführt:</span><span class="sxs-lookup"><span data-stu-id="6993f-190">Before deployment, the application has been running locally:</span></span>

1. <span data-ttu-id="6993f-191">Das Back-End unter Verwendung von _Azure Functions Core Tools_ ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="6993f-191">The backend runs using _Azure Functions Core Tools_.</span></span>
1. <span data-ttu-id="6993f-192">Der HTTP-Endpunkt der Anwendung, an dem Microsoft Teams die Anwendung lädt, wird lokal ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="6993f-192">The application HTTP endpoint, where Microsoft Teams loads the application, runs locally.</span></span>

<span data-ttu-id="6993f-193">Die Bereitstellung umfasst das Bereitstellen von Ressourcen für ein aktives Azure-Abonnement und das Bereitstellen (Hochladen) des Back-End- und des Frontend-Codes für die Anwendung in Azure.</span><span class="sxs-lookup"><span data-stu-id="6993f-193">Deployment involves provisioning resources on an active Azure subscription and deploying (uploading) the backend and frontend code for the application to Azure.</span></span> <span data-ttu-id="6993f-194">Das Back-End verwendet eine Vielzahl von Azure-Diensten, einschließlich Azure App Service und Azure Bot Service.</span><span class="sxs-lookup"><span data-stu-id="6993f-194">The backend uses a variety of Azure services, including Azure App Service and Azure Bot Service.</span></span>

</details>

## <a name="add-a-configuration-page-to-your-messaging-extension"></a><span data-ttu-id="6993f-195">Hinzufügen einer Konfigurationsseite zu Ihrer Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="6993f-195">Add a configuration page to your messaging extension</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

## <a name="code-sample"></a><span data-ttu-id="6993f-196">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="6993f-196">Code sample</span></span>

<span data-ttu-id="6993f-197">Die Teams Search Auth Config for sample projects on GitHub, demonstrate how to create messaging extensions that include a configuration page and [Bot Service authentication.](https://github.com/microsoft/BotBuilder-Samples#teams-samples)</span><span class="sxs-lookup"><span data-stu-id="6993f-197">The Teams Search Auth Config for sample projects on GitHub, demonstrate how to create messaging extensions that include a configuration page and [Bot Service authentication](https://github.com/microsoft/BotBuilder-Samples#teams-samples).</span></span> <span data-ttu-id="6993f-198">Die Beispiele zeigen auch, wie Sie Nachrichtenerweiterungen erstellen, die Suchanforderungen akzeptieren und die Ergebnisse zurückgeben, nachdem sich der Benutzer angemeldet hat.</span><span class="sxs-lookup"><span data-stu-id="6993f-198">The samples also demonstrate how to create message extensions that accept search requests and return the results after the user has signed in.</span></span>

| <span data-ttu-id="6993f-199">**Beispielname**</span><span class="sxs-lookup"><span data-stu-id="6993f-199">**Sample name**</span></span> | <span data-ttu-id="6993f-200">**Description**</span><span class="sxs-lookup"><span data-stu-id="6993f-200">**Description**</span></span> | <span data-ttu-id="6993f-201">**.NET**</span><span class="sxs-lookup"><span data-stu-id="6993f-201">**.NET**</span></span> | <span data-ttu-id="6993f-202">**Node.js**</span><span class="sxs-lookup"><span data-stu-id="6993f-202">**Node.js**</span></span> | <span data-ttu-id="6993f-203">**Python**</span><span class="sxs-lookup"><span data-stu-id="6993f-203">**Python**</span></span> |
|-----------------|-----------------|-------------|--------------|--------|
| <span data-ttu-id="6993f-204">Bot-Generator</span><span class="sxs-lookup"><span data-stu-id="6993f-204">Bot builder</span></span> | <span data-ttu-id="6993f-205">So erstellen Sie Messaging-Erweiterungen.</span><span class="sxs-lookup"><span data-stu-id="6993f-205">To create messaging extensions.</span></span> | [<span data-ttu-id="6993f-206">View</span><span class="sxs-lookup"><span data-stu-id="6993f-206">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config) | [<span data-ttu-id="6993f-207">View</span><span class="sxs-lookup"><span data-stu-id="6993f-207">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/52.teams-messaging-extensions-search-auth-config) | [<span data-ttu-id="6993f-208">View</span><span class="sxs-lookup"><span data-stu-id="6993f-208">View</span></span>]( https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/50.teams-messaging-extension-search) |

## <a name="additional-code-sample"></a><span data-ttu-id="6993f-209">Zusätzliches Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="6993f-209">Additional code sample</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6993f-210">Weitere Bot Framework-Beispiele auf GitHub anzeigen</span><span class="sxs-lookup"><span data-stu-id="6993f-210">View more Bot Framework Samples on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-samples#messaging-extensions-samples-using-the-v4-sdk)

## <a name="see-also"></a><span data-ttu-id="6993f-211">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="6993f-211">See also</span></span>

- [<span data-ttu-id="6993f-212">Erstellen einer Teams-App mit React</span><span class="sxs-lookup"><span data-stu-id="6993f-212">Create a Teams app with React</span></span>](first-app-react.md)
- [<span data-ttu-id="6993f-213">Erstellen einer Teams-App mit Blazor</span><span class="sxs-lookup"><span data-stu-id="6993f-213">Create a Teams app with Blazor</span></span>](first-app-blazor.md)
- <span data-ttu-id="6993f-214">[Erstellen einer Teams-App als SharePoint-Webpart](first-app-spfx.md) (Azure nicht erforderlich)</span><span class="sxs-lookup"><span data-stu-id="6993f-214">[Create a Teams app as a SharePoint Web Part](first-app-spfx.md) (Azure not required)</span></span>
- [<span data-ttu-id="6993f-215">Erstellen eines Unterhaltungs-Bots</span><span class="sxs-lookup"><span data-stu-id="6993f-215">Create a conversation bot</span></span>](first-app-bot.md)
