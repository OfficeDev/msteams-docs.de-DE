---
title: Erste Schritte - Erstellen Eines Bots
author: girliemac
description: Erstellen Sie schnell einen Microsoft Teams-Bot mit dem Microsoft Teams Toolkit.
ms.author: timura
ms.date: 04/14/2020
ms.topic: tutorial
ms.openlocfilehash: 2cbd90b293e8ac8343febc7b3d23278d5bb5bf82
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565886"
---
# <a name="create-your-first-bot-for-teams"></a><span data-ttu-id="58ca3-103">Erstellen Sie Ihren ersten Bot für Teams</span><span class="sxs-lookup"><span data-stu-id="58ca3-103">Create your first bot for Teams</span></span>

<span data-ttu-id="58ca3-104">Dieses Tutorial lehrt Sie, eine grundlegende Bot-App zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="58ca3-104">This tutorial teaches you to build a basic bot app.</span></span> <span data-ttu-id="58ca3-105">Ein Bot fungiert als Vermittler zwischen Teams Benutzern und Ihrer Web-App oder Ihrem Dienst mit einer Konversationsschnittstelle.</span><span class="sxs-lookup"><span data-stu-id="58ca3-105">A bot acts as an intermediary between Teams users and your web app or service with a conversational interface.</span></span> <span data-ttu-id="58ca3-106">Personen können mit einem Bot chatten, um schnell Informationen zu erhalten oder Workflows und Aufgaben zu initiieren, die von Ihrem Dienst ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="58ca3-106">People can chat with a bot to quickly get information or initiate workflows and tasks performed by your service.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="58ca3-107">Was Sie lernen werden</span><span class="sxs-lookup"><span data-stu-id="58ca3-107">What you'll learn</span></span>

* <span data-ttu-id="58ca3-108">Erstellen Sie ein App-Projekt und einen Bot mit dem Microsoft Teams Toolkit für Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="58ca3-108">Create an app project and bot using the Microsoft Teams Toolkit for Visual Studio Code.</span></span>
* <span data-ttu-id="58ca3-109">Verstehen Sie die Teams App-Konfigurationen, die für Bots relevant sind.</span><span class="sxs-lookup"><span data-stu-id="58ca3-109">Understand the Teams app configurations relevant to bots.</span></span>
* <span data-ttu-id="58ca3-110">Hosten und führen Sie eine App lokal mit einer lokalen Host-Tunnellösung aus.</span><span class="sxs-lookup"><span data-stu-id="58ca3-110">Host and run an app locally using a localhost tunneling solution.</span></span>
* <span data-ttu-id="58ca3-111">Sideload und testen Sie einen Bot in Teams.</span><span class="sxs-lookup"><span data-stu-id="58ca3-111">Sideload and test a bot in Teams.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="58ca3-112">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="58ca3-112">Prerequisites</span></span>

<span data-ttu-id="58ca3-113">Stellen Sie sicher, dass Sie verstehen, wie Sie eine einfache Teams-App einrichten und erstellen.</span><span class="sxs-lookup"><span data-stu-id="58ca3-113">Ensure that you understand how to set up and build a simple Teams app.</span></span> <span data-ttu-id="58ca3-114">Weitere Informationen finden Sie [unter Erstellen Ihrer ersten Microsoft Teams "Hello, World!"-App](../build-your-first-app/build-and-run.md).</span><span class="sxs-lookup"><span data-stu-id="58ca3-114">For more information, see [create your first Microsoft Teams "Hello, World!" app](../build-your-first-app/build-and-run.md).</span></span> 

## <a name="1-create-your-app-project"></a><span data-ttu-id="58ca3-115">1. Erstellen Sie Ihr App-Projekt</span><span class="sxs-lookup"><span data-stu-id="58ca3-115">1. Create your app project</span></span>

<span data-ttu-id="58ca3-116">Mit dem Microsoft Teams Toolkit können Sie die folgenden Komponenten für Ihre App einrichten:</span><span class="sxs-lookup"><span data-stu-id="58ca3-116">The Microsoft Teams Toolkit helps you set up the following components for your app:</span></span> 

* <span data-ttu-id="58ca3-117">**App-Konfigurationen und Gerüste** relevant für Bots.</span><span class="sxs-lookup"><span data-stu-id="58ca3-117">**App configurations and scaffolding** relevant to bots.</span></span>
* <span data-ttu-id="58ca3-118">**Bot,** der automatisch beim Microsoft Azure Bot Service registriert ist.</span><span class="sxs-lookup"><span data-stu-id="58ca3-118">**Bot** that's automatically registered with the Microsoft Azure Bot Service.</span></span>

<span data-ttu-id="58ca3-119">**So erstellen Sie Ihr App-Projekt**</span><span class="sxs-lookup"><span data-stu-id="58ca3-119">**To create your app project**</span></span>

1. Wählen Sie in Visual Studio Code **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: auf der linken Aktivitätsleiste aus, und wählen Sie **eine neue Teams-App erstellen** aus.

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-01.png" alt-text="Screenshot, der zeigt, wie sie eine App im Teams Toolkit erstellen.":::

1. <span data-ttu-id="58ca3-122">Wenn Sie dazu aufgefordert werden, melden Sie sich mit Ihrem Microsoft 365-Entwicklungskonto an.</span><span class="sxs-lookup"><span data-stu-id="58ca3-122">When prompted, sign in with your Microsoft 365 development account.</span></span> 
1. <span data-ttu-id="58ca3-123">Wählen Sie auf dem Bildschirm Projekt auswählen Unterhaltung-Bots aus:</span><span class="sxs-lookup"><span data-stu-id="58ca3-123">On the Select project screen, select Conversation bots:</span></span> 

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-02.png" alt-text="Screenshot, der zeigt, wie Sie einen neuen Bot im Teams Toolkit erstellen.":::

1. <span data-ttu-id="58ca3-125">Geben Sie auf dem **Bildschirm Projekt konfigurieren** einen Namen für Ihren Bot ein.</span><span class="sxs-lookup"><span data-stu-id="58ca3-125">On the **Configure project** screen, enter a name for your bot.</span></span> <span data-ttu-id="58ca3-126">Dies ist der Standardname für Ihre App und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.</span><span class="sxs-lookup"><span data-stu-id="58ca3-126">This is the default name for your app and also the name of the app project directory on your local machine.</span></span>
1. <span data-ttu-id="58ca3-127">Wählen Sie **Erstellen einer neuen**  >  **Bot-Registrierung erstellen** aus, wie in der folgenden Abbildung gezeigt:</span><span class="sxs-lookup"><span data-stu-id="58ca3-127">Select **Create a new Bot** > **Create Bot Registration** as shown in the following image:</span></span>

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-03.png" alt-text="Screenshot mit dem Benennen eines neuen Bots im Teams Toolkit.":::

    <span data-ttu-id="58ca3-129">Wenn der Erfolg gelingt, hat Ihr neuer Bot einen **registrierten** Status.</span><span class="sxs-lookup"><span data-stu-id="58ca3-129">If successful, your new bot will have a **Registered** status.</span></span> <span data-ttu-id="58ca3-130">Jetzt wird Ihr Bot automatisch beim Microsoft Azure-Bot-Service registriert.</span><span class="sxs-lookup"><span data-stu-id="58ca3-130">Now your bot is automatically registered with the Microsoft Azure Bot Service.</span></span> 

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-04.png" alt-text="Screenshot mit der Registrierung eines neuen Bots im Teams Toolkit.":::

1. <span data-ttu-id="58ca3-132">Wählen Sie am unteren Bildschirmrand **fertig** und speichern Sie Das Projekt auf dem Computer.</span><span class="sxs-lookup"><span data-stu-id="58ca3-132">Select **Finish** at the bottom of the screen and save your project on your machine.</span></span>  

## <a name="2-understand-your-app-project-components"></a><span data-ttu-id="58ca3-133">2. Verstehen Ihrer App-Projektkomponenten</span><span class="sxs-lookup"><span data-stu-id="58ca3-133">2. Understand your app project components</span></span>

<span data-ttu-id="58ca3-134">Ein Großteil der App-Konfigurationen und Gerüste wird automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Teams Toolkit erstellen.</span><span class="sxs-lookup"><span data-stu-id="58ca3-134">Much of the app configurations and scaffolding are set up automatically when you create your project with the Teams Toolkit.</span></span> <span data-ttu-id="58ca3-135">Sehen wir uns die Hauptkomponenten für den Aufbau eines Bots an:</span><span class="sxs-lookup"><span data-stu-id="58ca3-135">Let's look at the main components for building a bot:</span></span>

:::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-05.png" alt-text="Screenshot mit einem Projektgerüst im Teams Toolkit.":::

<span data-ttu-id="58ca3-137">Wenn Sie eine Registerkarte in einem anderen Tutorial erstellt haben, ist das App-Gerüst für den Bot anders.</span><span class="sxs-lookup"><span data-stu-id="58ca3-137">If you created a tab in another tutorial, the app scaffolding for the bot is different.</span></span> <span data-ttu-id="58ca3-138">Im Gegensatz zu Registerkarten erfordert die Bot-Entwicklung keine Front-End-Webkomponenten oder die Verwendung des Teams JavaScript-Client-SDK.</span><span class="sxs-lookup"><span data-stu-id="58ca3-138">Unlike tabs, bot development doesn't require you to build any front-end web components or use the Teams JavaScript client SDK.</span></span>  <span data-ttu-id="58ca3-139">Stattdessen verwendet das Gerüst die [Microsoft Bot Framework](https://dev.botframework.com/), die ein Open-Source-SDK für den Aufbau intelligenter Bots auf Enterprise-Qualität ist, die im Web, mobil und natürlich Teams funktionieren können!</span><span class="sxs-lookup"><span data-stu-id="58ca3-139">Instead, the scaffolding uses the [Microsoft Bot Framework](https://dev.botframework.com/), which is an open-source SDK for building intelligent, enterprise-grade bots that can work on the web, mobile, and of course Teams!</span></span> 

<span data-ttu-id="58ca3-140">Die `botActivityHandler.js` Datei, die sich im Stammverzeichnis Ihres Projekts befindet, ist der Teams-spezifische Handler, der Bot-Aktivitäten verarbeitet, z. B. wie der Bot auf bestimmte Nachrichten reagiert.</span><span class="sxs-lookup"><span data-stu-id="58ca3-140">The `botActivityHandler.js` file, located in the root directory of your project, is the Teams-specific handler that handles bot activities, such as how the bot responds to specific messages.</span></span> <span data-ttu-id="58ca3-141">Das App-Gerüst stellt eine `botActivityHandler.js` Datei im Stammverzeichnis Ihres Projekts bereit, ist die Teams bestimmten Handlers, der Bot-Aktivitäten verarbeitet, z. B. wie der Bot auf bestimmte Nachrichten reagiert.</span><span class="sxs-lookup"><span data-stu-id="58ca3-141">The app scaffolding provides a `botActivityHandler.js` file located in the root directory of your project, is the Teams specific handler that handles bot activities such as how the bot responds to specific messages.</span></span>

## <a name="3-securely-expose-your-localhost-to-the-internet"></a><span data-ttu-id="58ca3-142">3. Setzen Sie Ihren lokalen Host sicher dem Internet aus</span><span class="sxs-lookup"><span data-stu-id="58ca3-142">3. Securely expose your localhost to the internet</span></span>

<span data-ttu-id="58ca3-143">Werfen Sie einen Blick auf die `index.js` Datei, die einen HTTP-Server erstellt und Routing verarbeitet, um eingehende Anforderungen an Ihren Bot zu hören.</span><span class="sxs-lookup"><span data-stu-id="58ca3-143">Take a look at the `index.js` file, which creates an HTTP server and handles routing to listen for incoming requests to your bot.</span></span> <span data-ttu-id="58ca3-144">Die `/api/messages` ist die Endpunkt-URL Ihrer App, um auf Clientanforderungen zu reagieren:</span><span class="sxs-lookup"><span data-stu-id="58ca3-144">The `/api/messages` is your app's endpoint URL to respond to client requests:</span></span> 

```JavaScript
server.post('/api/messages', (req, res) => { 
  adapter.processActivity(req, res, async (context) => { 
    await botActivityHandler.run(context); 
  }); 
}); 
```

<span data-ttu-id="58ca3-145">Um die Anforderungen an die Logik Ihres Bots weiterzuleiten, müssen Sie eine öffentlich zugängliche URL einrichten, z. `https://example.com/api/messages` B. . `https://localhost`</span><span class="sxs-lookup"><span data-stu-id="58ca3-145">To forward the requests to your bot's logic, you must set up a publicly accessible URL, such as `https://example.com/api/messages`, instead of `https://localhost`.</span></span> <span data-ttu-id="58ca3-146">Da Ihre App derzeit von Ihrem lokalen Host aus ausgeführt wird, müssen Sie das Netzwerk *tunneln.*</span><span class="sxs-lookup"><span data-stu-id="58ca3-146">Because your app is running from your localhost currently, you must *tunnel* the network.</span></span>

<span data-ttu-id="58ca3-147">Tunneling ist ein Protokoll, mit dem Sie Daten über ein Netzwerk transportieren können.</span><span class="sxs-lookup"><span data-stu-id="58ca3-147">Tunneling is a protocol that allows you to transport data across a network.</span></span> <span data-ttu-id="58ca3-148">Und localhost Tunneling bietet Ihnen eine Verbindung zwischen Ihrem lokalen Computer und einer Remote-Verbindung.</span><span class="sxs-lookup"><span data-stu-id="58ca3-148">And localhost tunneling gives you a connection between your local machine and a remote connection.</span></span> <span data-ttu-id="58ca3-149">Um Ihren lokalen Host sicher dem Internet auszusetzen, empfehlen wir Ihnen, das Drittanbieter-Tool **namens ngrok** zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="58ca3-149">To securely expose your localhost to the internet, we recommend you to use the 3rd party tool called, **ngrok**.</span></span> <span data-ttu-id="58ca3-150">Dadurch erhalten Sie eine sichere URL.</span><span class="sxs-lookup"><span data-stu-id="58ca3-150">This will give you a secure URL.</span></span> 

1. <span data-ttu-id="58ca3-151">Rufen Sie die [ngrok.com-Website](https://ngrok.com/download) auf, und befolgen Sie die Anweisungen zum Installieren und Einrichten von ngrok in Ihrer Umgebung.</span><span class="sxs-lookup"><span data-stu-id="58ca3-151">Go to the [ngrok.com](https://ngrok.com/download) site and follow the instruction to install and set up ngrok in your environment.</span></span> 
    
    <span data-ttu-id="58ca3-152">Fügen Sie den vollständigen Pfad zur ngrok.exe Datei hinzu, die Sie der Systemumgebungsvariablen PATH installiert haben.</span><span class="sxs-lookup"><span data-stu-id="58ca3-152">Add the full path to the ngrok.exe file that you installed to the system PATH environment variable.</span></span> <span data-ttu-id="58ca3-153">Die genauen Schritte sind spezifisch für die Shell, die Sie verwenden.</span><span class="sxs-lookup"><span data-stu-id="58ca3-153">The exact steps are specific to the shell that you are using.</span></span>

1.  <span data-ttu-id="58ca3-154">Nachdem Sie die Einrichtung abgeschlossen haben, öffnen Sie ein Terminal, und führen Sie `ngrok http -host-header=rewrite 3978` aus.</span><span class="sxs-lookup"><span data-stu-id="58ca3-154">After you have finished setting it up, open a terminal and run `ngrok http -host-header=rewrite 3978`.</span></span> 

    <span data-ttu-id="58ca3-155">Jetzt stellt ngrok Ihnen eine öffentliche, sichere URL bereit, die an Ihren lokalen Host an Port 3978 weitergeleitet wird, also kopieren Sie die HTTPS-URL, z. B., `https://287a4f4223bc.ngrok.io` wie im Screenshot unten gezeigt, da Teams HTTPS-Verbindungen erfordert:</span><span class="sxs-lookup"><span data-stu-id="58ca3-155">Now ngrok provides you a public, secure URL that forwards to your localhost at port 3978, so copy the HTTPS URL, for example, `https://287a4f4223bc.ngrok.io` as shown in the screenshot below, since Teams requires HTTPS connections:</span></span> 

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-ngrok-06.png" alt-text="Screenshot mit Tunnelbau von localhost mit ngrok.":::

1. <span data-ttu-id="58ca3-157">Registrieren Sie die URL in Ihrem App-Manifest.</span><span class="sxs-lookup"><span data-stu-id="58ca3-157">Register the URL in your app manifest.</span></span> 

## <a name="4-register-your-bot-endpoint"></a><span data-ttu-id="58ca3-158">4. Registrieren Sie Ihren Bot-Endpunkt</span><span class="sxs-lookup"><span data-stu-id="58ca3-158">4. Register your bot endpoint</span></span>

<span data-ttu-id="58ca3-159">Um einen Bot in Teams verwenden zu können, müssen Sie ihn beim Azure Bot Service registrieren.</span><span class="sxs-lookup"><span data-stu-id="58ca3-159">To use a bot in Teams, you must register it with the Azure Bot Service.</span></span> <span data-ttu-id="58ca3-160">Dies geschieht automatisch, wenn Sie Ihre App mit dem Teams Toolkit einrichten.</span><span class="sxs-lookup"><span data-stu-id="58ca3-160">This is done automatically when you set up your app using the Teams Toolkit.</span></span>

<span data-ttu-id="58ca3-161">Sie müssen weiterhin eine Endpunktadresse angeben, um Benutzernachrichten oder an den Bot gesendete Anforderungen zu empfangen und zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="58ca3-161">You must still specify an endpoint address to receive and process user messages, or requests sent to the bot.</span></span> <span data-ttu-id="58ca3-162">In der Regel sieht die URL wie `https://HOST_URL/api/messages` aus.</span><span class="sxs-lookup"><span data-stu-id="58ca3-162">Typically, the URL looks like `https://HOST_URL/api/messages`.</span></span> <span data-ttu-id="58ca3-163">Sie können dies im Toolkit konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="58ca3-163">You can configure this in the toolkit.</span></span>

1. <span data-ttu-id="58ca3-164">Öffnen Sie **Visual Studio Code Microsoft Teams Toolkit**.</span><span class="sxs-lookup"><span data-stu-id="58ca3-164">In Visual Studio Code, open **Microsoft Teams Toolkit**.</span></span>
1. <span data-ttu-id="58ca3-165">Wählen Sie **Bots**  >  **Vorhandene Bot-Registrierungen** und wählen Sie den Bot, den Sie während des Setups erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="58ca3-165">Select **Bots** > **Existing bot registrations** and select the bot you created during setup.</span></span> 
1. <span data-ttu-id="58ca3-166">Geben Sie im Feld **Bot-Endpunktadresse** die ngrok-URL ein, z. B. , in der Sie den Bot hosten und an ihn `https://287a4f4223bc.ngrok.io` `/api/messages` anhängen:</span><span class="sxs-lookup"><span data-stu-id="58ca3-166">In the **Bot endpoint address** field, enter the ngrok URL, for example, `https://287a4f4223bc.ngrok.io`, where you're hosting the bot and append `/api/messages` to it:</span></span>

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-07.png" alt-text="Screenshot, der zeigt, wie localhost mit ngrok getunnelt wird.":::

    <span data-ttu-id="58ca3-168">Ihr Bot kann auf Nachrichten in Teams antworten, nachdem Sie den Endpunkt richtig eingerichtet haben.</span><span class="sxs-lookup"><span data-stu-id="58ca3-168">Your bot will be able to respond to messages in Teams, after you set up the endpoint correctly.</span></span> 

## <a name="5-build-and-run-your-app"></a><span data-ttu-id="58ca3-169">5. Erstellen und Ausführen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="58ca3-169">5. Build and run your app</span></span>

<span data-ttu-id="58ca3-170">Sie haben eine URL zum Hosten Ihres Bots eingerichtet und für die Verarbeitung von Nachrichten konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="58ca3-170">You've set up a URL to host your bot and configured it to handle messages.</span></span> <span data-ttu-id="58ca3-171">Es ist an der Zeit, Ihre App in Betrieb zu nehmen.</span><span class="sxs-lookup"><span data-stu-id="58ca3-171">It's time to get your app up and running.</span></span>

1. <span data-ttu-id="58ca3-172">Wechseln Sie in einem Terminal zum Stammverzeichnis Ihres App-Projekts, und führen Sie `npm install` aus.</span><span class="sxs-lookup"><span data-stu-id="58ca3-172">In a terminal, go to the root directory of your app project and run `npm install`.</span></span>
1. <span data-ttu-id="58ca3-173">Führen Sie `npm start` aus.</span><span class="sxs-lookup"><span data-stu-id="58ca3-173">Run `npm start`.</span></span>

   <span data-ttu-id="58ca3-174">Wenn dies erfolgreich ist, wird die folgende Meldung angezeigt, die darauf hinweist, dass Ihr Bot auf Aktivitäten in Ihrem `localhost` feldt:</span><span class="sxs-lookup"><span data-stu-id="58ca3-174">If successful, you see the following message indicating your bot is listening for activity at your `localhost`:</span></span>

   `Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-bot-in-teams"></a><span data-ttu-id="58ca3-175">6. Sideload Ihren Bot in Teams</span><span class="sxs-lookup"><span data-stu-id="58ca3-175">6. Sideload your bot in Teams</span></span>

<span data-ttu-id="58ca3-176">Wenn Ihr Bot läuft, können Sie ihn in Teams installieren.</span><span class="sxs-lookup"><span data-stu-id="58ca3-176">With your bot running, you can install it in Teams.</span></span>

> [!TIP]
> <span data-ttu-id="58ca3-177">Wenn Sie noch keine Teams App geladen haben und Probleme auftreten, befolgen Sie diese [Anweisungen](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams).</span><span class="sxs-lookup"><span data-stu-id="58ca3-177">If you haven't sideloaded a Teams app before and run into issues, follow these [instructions](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams).</span></span>

1. <span data-ttu-id="58ca3-178">Wählen Sie Visual Studio Code die **Taste F5** aus, um einen Teams Webclient zu starten.</span><span class="sxs-lookup"><span data-stu-id="58ca3-178">In Visual Studio Code, select the **F5** key to launch a Teams web client.</span></span>
1. <span data-ttu-id="58ca3-179">Wählen Sie im Dialogfeld App-Installation die Option **Für mich hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="58ca3-179">In the app install dialog, select **Add for me**.</span></span> 

   > [!Note]
   > <span data-ttu-id="58ca3-180">Standardmäßig wird die App zu Ihrer 1:1-Direktchatnachricht hinzugefügt, Sie können sie jedoch in einem Team installieren oder chatten, indem Sie auf den kleinen Pfeil neben **Add for me** klicken.</span><span class="sxs-lookup"><span data-stu-id="58ca3-180">By default, the app is added to your 1:1 direct chat message, however you can choose to install it to a team or chat by clicking the little arrow beside **Add for me**.</span></span> <span data-ttu-id="58ca3-181">In diesem Tutorial klicken wir einfach auf Hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="58ca3-181">In this tutorial, let’s just click Add.</span></span>

   :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-install-08.png" alt-text="Screenshot mit Tunneling localhost mit ngrok.":::

## <a name="7-test-your-bot"></a><span data-ttu-id="58ca3-183">7. Testen Sie Ihren Bot</span><span class="sxs-lookup"><span data-stu-id="58ca3-183">7. Test your bot</span></span>

<span data-ttu-id="58ca3-184">Sagen wir "Hallo" zu Ihrem Bot.</span><span class="sxs-lookup"><span data-stu-id="58ca3-184">Let's say "Hello" to your bot.</span></span>

* <span data-ttu-id="58ca3-185">Senden Sie im Feld Verfassen eine `Hello` Nachricht.</span><span class="sxs-lookup"><span data-stu-id="58ca3-185">In the compose box, send a `Hello` message.</span></span>
    <span data-ttu-id="58ca3-186">Ihr Bot antwortet mit der folgenden Nachricht:</span><span class="sxs-lookup"><span data-stu-id="58ca3-186">Your bot replies with something like the following message:</span></span>

    :::image type="content" source="../assets/images/build-your-first-app/teams-client-bot.png" alt-text="Ein Screenshot, der einen Benutzer zeigt, der einem Teams Bot &quot;Hallo&quot; sagt und eine Antwort erhält.":::

    <span data-ttu-id="58ca3-188">Sie haben jetzt eine grundlegende Teams-Bots erstellt, die mit Benutzern eins zu eins oder in Gruppeneinstellungen (Kanäle und Chats) 🎉 kommunizieren können.</span><span class="sxs-lookup"><span data-stu-id="58ca3-188">You have now created a basic Teams bot that can communicate with users one-on-one or in group settings (channels and chats) 🎉.</span></span>

## <a name="troubleshoot-your-bot"></a><span data-ttu-id="58ca3-189">Beheben Sie Ihren Bot</span><span class="sxs-lookup"><span data-stu-id="58ca3-189">Troubleshoot your bot</span></span>

<span data-ttu-id="58ca3-190">Die folgenden Informationen können hilfreich sein, wenn Sie Probleme beim Abschließen dieses Tutorials hatten.</span><span class="sxs-lookup"><span data-stu-id="58ca3-190">The following information may help if you had issues completing this tutorial.</span></span>

### <a name="bot-isnt-connected-to-teams"></a><span data-ttu-id="58ca3-191">Bot ist nicht mit Teams verbunden</span><span class="sxs-lookup"><span data-stu-id="58ca3-191">Bot isn't connected to Teams</span></span>


<span data-ttu-id="58ca3-192">Wenn Sie Ihre App installiert haben, der Bot jedoch nicht funktioniert, stellen Sie sicher, dass der Bot [mit dem Teams *Kanal* des Azure Bot Service verbunden](/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true)ist.</span><span class="sxs-lookup"><span data-stu-id="58ca3-192">If you installed your app but the bot isn't working, make sure the bot is [connected to the Azure Bot Service's Teams *channel*](/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true).</span></span>

<span data-ttu-id="58ca3-193">Es ist wichtig zu verstehen, dass dies nicht dasselbe ist wie ein Kanal in Teams.</span><span class="sxs-lookup"><span data-stu-id="58ca3-193">It's important to understand that this isn't the same as a channel in Teams.</span></span> <span data-ttu-id="58ca3-194">In diesem Fall ist ein Kanal, wie der Azure Bot Service Ihren Bot mit Teams oder einer anderen [unterstützten Microsoft- oder Drittanbieter-Kommunikations-App](/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)verbindet.</span><span class="sxs-lookup"><span data-stu-id="58ca3-194">In this case, a channel is how the Azure Bot Service connects your bot to Teams or another [supported Microsoft or third-party communications app](/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span>

## <a name="see-also"></a><span data-ttu-id="58ca3-195">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="58ca3-195">See also</span></span>

* [<span data-ttu-id="58ca3-196">Bot-Grundlagen</span><span class="sxs-lookup"><span data-stu-id="58ca3-196">Bot basics</span></span>](../bots/bot-basics.md)
* [<span data-ttu-id="58ca3-197">Erstellen einer persönlichen Registerkarte für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="58ca3-197">Build a personal tab for Microsoft Teams</span></span>](../build-your-first-app/build-personal-tab.md)
* [<span data-ttu-id="58ca3-198">Sehen Sie, was Teams Bots noch mit einem unserer Samples tun können</span><span class="sxs-lookup"><span data-stu-id="58ca3-198">See what else Teams bots can do with one of our samples</span></span>](https://github.com/microsoft/BotBuilder-Samples#teams-samples)
* [<span data-ttu-id="58ca3-199">Grundlegende Informationen zu Bot-Unterhaltungen</span><span class="sxs-lookup"><span data-stu-id="58ca3-199">Bot conversation basics</span></span>](../bots/how-to/conversations/conversation-basics.md)
* [<span data-ttu-id="58ca3-200">Richtlinien für den Entwurf</span><span class="sxs-lookup"><span data-stu-id="58ca3-200">Design guidelines</span></span>](../bots/design/bots.md) 
* [<span data-ttu-id="58ca3-201">Produktionsfähige UI-Vorlagen</span><span class="sxs-lookup"><span data-stu-id="58ca3-201">Production-ready UI templates</span></span>](../concepts/design/design-teams-app-ui-templates.md)
* [<span data-ttu-id="58ca3-202">Bot-Authentifizierung in Teams</span><span class="sxs-lookup"><span data-stu-id="58ca3-202">Bot authentication in Teams</span></span>](../bots/how-to/authentication/auth-flow-bot.md)
* [<span data-ttu-id="58ca3-203">Microsoft Bot Framework</span><span class="sxs-lookup"><span data-stu-id="58ca3-203">Microsoft Bot Framework</span></span>](https://dev.botframework.com/)
* [<span data-ttu-id="58ca3-204">Erstellen eines Bots ohne Toolkit</span><span class="sxs-lookup"><span data-stu-id="58ca3-204">Create a bot without the toolkit</span></span>](../resources/bot-v3/bots-create.md)

## <a name="next-step"></a><span data-ttu-id="58ca3-205">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="58ca3-205">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="58ca3-206">Erstellen einer Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="58ca3-206">Build a messaging extension</span></span>](../build-your-first-app/build-messaging-extension.md)
