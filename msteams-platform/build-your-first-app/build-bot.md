---
title: Erste Schritte – Erstellen eines Bots
author: girliemac
description: Erstellen Sie schnell einen Microsoft Teams-Bot mithilfe des Microsoft Teams Toolkits.
ms.author: timura
ms.date: 04/14/2020
ms.topic: tutorial
ms.openlocfilehash: dbb6f0a2497a0914d8e14473f1dbd6b2b225fc96
ms.sourcegitcommit: 303fc214aa04757779a171337f31a6539f47fd03
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2021
ms.locfileid: "52068608"
---
# <a name="create-your-first-bot-for-teams"></a><span data-ttu-id="af8e4-103">Erstellen Des ersten Bots für Teams</span><span class="sxs-lookup"><span data-stu-id="af8e4-103">Create your first bot for Teams</span></span>

<span data-ttu-id="af8e4-104">In diesem Lernprogramm lernen Sie, eine einfache Bot-App zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="af8e4-104">This tutorial teaches you to build a basic bot app.</span></span> <span data-ttu-id="af8e4-105">Ein Bot fungiert als Vermittler zwischen Teams-Benutzern und Ihrer Web-App oder Ihrem Dienst mit einer Unterhaltungsschnittstelle.</span><span class="sxs-lookup"><span data-stu-id="af8e4-105">A bot acts as an intermediary between Teams users and your web app or service with a conversational interface.</span></span> <span data-ttu-id="af8e4-106">Benutzer können mit einem Bot chatten, um schnell Informationen zu erhalten oder Workflows und Aufgaben zu initiieren, die von Ihrem Dienst ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="af8e4-106">People can chat with a bot to quickly get information or initiate workflows and tasks performed by your service.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="af8e4-107">Was Sie lernen werden</span><span class="sxs-lookup"><span data-stu-id="af8e4-107">What you'll learn</span></span>

* <span data-ttu-id="af8e4-108">Erstellen Sie ein App-Projekt und einen Bot mit dem Microsoft Teams Toolkit für Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="af8e4-108">Create an app project and bot using the Microsoft Teams Toolkit for Visual Studio Code.</span></span>
* <span data-ttu-id="af8e4-109">Verstehen sie die für Bots relevanten Teams-App-Konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="af8e4-109">Understand the Teams app configurations relevant to bots.</span></span>
* <span data-ttu-id="af8e4-110">Hosten und ausführen Sie eine App lokal mit einer localhost-Tunnellösung.</span><span class="sxs-lookup"><span data-stu-id="af8e4-110">Host and run an app locally using a localhost tunneling solution.</span></span>
* <span data-ttu-id="af8e4-111">Querladen und Testen eines Bots in Teams.</span><span class="sxs-lookup"><span data-stu-id="af8e4-111">Sideload and test a bot in Teams.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="af8e4-112">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="af8e4-112">Prerequisites</span></span>

<span data-ttu-id="af8e4-113">Stellen Sie sicher, dass Sie verstehen, wie Sie eine einfache Teams-App einrichten und erstellen.</span><span class="sxs-lookup"><span data-stu-id="af8e4-113">Ensure that you understand how to set up and build a simple Teams app.</span></span> <span data-ttu-id="af8e4-114">Weitere Informationen finden Sie unter [Erstellen Ihrer ersten Microsoft Teams "Hello, World!"-App.](../build-your-first-app/build-and-run.md)</span><span class="sxs-lookup"><span data-stu-id="af8e4-114">For more information, see [create your first Microsoft Teams "Hello, World!" app](../build-your-first-app/build-and-run.md).</span></span> 

## <a name="1-create-your-app-project"></a><span data-ttu-id="af8e4-115">1. Erstellen Ihres App-Projekts</span><span class="sxs-lookup"><span data-stu-id="af8e4-115">1. Create your app project</span></span>

<span data-ttu-id="af8e4-116">Das Microsoft Teams Toolkit hilft Ihnen beim Einrichten der folgenden Komponenten für Ihre App:</span><span class="sxs-lookup"><span data-stu-id="af8e4-116">The Microsoft Teams Toolkit helps you set up the following components for your app:</span></span> 

* <span data-ttu-id="af8e4-117">**Für Bots relevante** App-Konfigurationen und Gerüste</span><span class="sxs-lookup"><span data-stu-id="af8e4-117">**App configurations and scaffolding** relevant to bots</span></span>
* <span data-ttu-id="af8e4-118">**Bot,** der automatisch beim Microsoft Azure Bot Service registriert ist</span><span class="sxs-lookup"><span data-stu-id="af8e4-118">**Bot** that's automatically registered with the Microsoft Azure Bot Service</span></span>

<span data-ttu-id="af8e4-119">**So erstellen Sie Ihr App-Projekt**</span><span class="sxs-lookup"><span data-stu-id="af8e4-119">**To create your app project**</span></span>

1. Wählen Visual Studio Code auf der linken Aktivitätsleiste **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: aus, und wählen Sie Erstellen einer neuen **Teams-App aus.**

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-01.png" alt-text="Screenshot, der zeigt, wie Sie eine App im Teams Toolkit erstellen.":::

1. <span data-ttu-id="af8e4-122">Melden Sie sich bei Aufforderung mit Ihrem Microsoft 365-Entwicklungskonto an.</span><span class="sxs-lookup"><span data-stu-id="af8e4-122">When prompted, sign in with your Microsoft 365 development account.</span></span> 
1. <span data-ttu-id="af8e4-123">Wählen Sie auf dem Bildschirm Projekt auswählen die Option Unterhaltungsbots aus:</span><span class="sxs-lookup"><span data-stu-id="af8e4-123">On the Select project screen, select Conversation bots:</span></span> 

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-02.png" alt-text="Screenshot, der zeigt, wie Sie einen neuen Bot im Teams Toolkit erstellen.":::

1. <span data-ttu-id="af8e4-125">Geben Sie **auf dem Bildschirm** Projekt konfigurieren einen Namen für Ihren Bot ein.</span><span class="sxs-lookup"><span data-stu-id="af8e4-125">On the **Configure project** screen, enter a name for your bot.</span></span> <span data-ttu-id="af8e4-126">Dies ist der Standardname für Ihre App und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.</span><span class="sxs-lookup"><span data-stu-id="af8e4-126">This is the default name for your app and also the name of the app project directory on your local machine.</span></span>
1. <span data-ttu-id="af8e4-127">Wählen **Sie Create a new Bot** Create Bot  >  **Registration** aus, wie in der folgenden Abbildung dargestellt:</span><span class="sxs-lookup"><span data-stu-id="af8e4-127">Select **Create a new Bot** > **Create Bot Registration** as shown in the following image:</span></span>

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-03.png" alt-text="Screenshot mit der Benennung eines neuen Bots im Teams Toolkit.":::

    <span data-ttu-id="af8e4-129">Wenn der neue Bot erfolgreich ist, hat er den **Status "Registriert".**</span><span class="sxs-lookup"><span data-stu-id="af8e4-129">If successful, your new bot will have a **Registered** status.</span></span> <span data-ttu-id="af8e4-130">Jetzt wird Ihr Bot automatisch beim Microsoft Azure Bot Service registriert.</span><span class="sxs-lookup"><span data-stu-id="af8e4-130">Now your bot is automatically registered with the Microsoft Azure Bot Service.</span></span> 

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-04.png" alt-text="Screenshot der Registrierung des neuen Bots im Teams Toolkit.":::

1. <span data-ttu-id="af8e4-132">Wählen **Sie unten** auf dem Bildschirm Fertig stellen aus, und speichern Sie Ihr Projekt auf Ihrem Computer.</span><span class="sxs-lookup"><span data-stu-id="af8e4-132">Select **Finish** at the bottom of the screen and save your project on your machine.</span></span>  

## <a name="2-understand-your-app-project-components"></a><span data-ttu-id="af8e4-133">2. Verstehen Ihrer App-Projektkomponenten</span><span class="sxs-lookup"><span data-stu-id="af8e4-133">2. Understand your app project components</span></span>

<span data-ttu-id="af8e4-134">Viele der App-Konfigurationen und Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Teams Toolkit erstellen.</span><span class="sxs-lookup"><span data-stu-id="af8e4-134">Much of the app configurations and scaffolding are set up automatically when you create your project with the Teams Toolkit.</span></span> <span data-ttu-id="af8e4-135">Sehen wir uns die Hauptkomponenten zum Erstellen eines Bots an:</span><span class="sxs-lookup"><span data-stu-id="af8e4-135">Let's look at the main components for building a bot:</span></span>

:::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-05.png" alt-text="Screenshot eines Projektgerüsts im Teams Toolkit.":::

<span data-ttu-id="af8e4-137">Wenn Sie in einem anderen Lernprogramm eine Registerkarte erstellt haben, ist das App-Gerüst für den Bot anders.</span><span class="sxs-lookup"><span data-stu-id="af8e4-137">If you created a tab in another tutorial, the app scaffolding for the bot is different.</span></span> <span data-ttu-id="af8e4-138">Im Gegensatz zu Registerkarten erfordert die Botentwicklung nicht, dass Sie Front-End-Webkomponenten erstellen oder das Teams JavaScript-Client-SDK verwenden.</span><span class="sxs-lookup"><span data-stu-id="af8e4-138">Unlike tabs, bot development doesn't require you to build any front-end web components or use the Teams JavaScript client SDK.</span></span>  <span data-ttu-id="af8e4-139">Stattdessen verwendet das Gerüst das [Microsoft Bot Framework](https://dev.botframework.com/), ein Open-Source-SDK zum Erstellen intelligenter Bots auf Enterprise-Qualität, die im Web, mobil und natürlich Teams funktionieren können!</span><span class="sxs-lookup"><span data-stu-id="af8e4-139">Instead, the scaffolding uses the [Microsoft Bot Framework](https://dev.botframework.com/), which is an open-source SDK for building intelligent, enterprise-grade bots that can work on the web, mobile, and of course Teams!</span></span> 

<span data-ttu-id="af8e4-140">Die Datei, die sich im Stammverzeichnis Ihres Projekts befindet, ist der teamsspezifische Handler, der Botaktivitäten verarbeitet, z. B. wie der `botActivityHandler.js` Bot auf bestimmte Nachrichten reagiert.</span><span class="sxs-lookup"><span data-stu-id="af8e4-140">The `botActivityHandler.js` file, located in the root directory of your project, is the Teams-specific handler that handles bot activities, such as how the bot responds to specific messages.</span></span> <span data-ttu-id="af8e4-141">Das App-Gerüst bietet eine Datei, die sich im Stammverzeichnis Ihres Projekts befindet, ist der spezifische Handler für Teams, der Botaktivitäten verarbeitet, z. B. wie der Bot auf `botActivityHandler.js` bestimmte Nachrichten reagiert.</span><span class="sxs-lookup"><span data-stu-id="af8e4-141">The app scaffolding provides a `botActivityHandler.js` file, located in the root directory of your project, is the Teams specific handler that handles bot activities such as how the bot responds to specific messages.</span></span>

## <a name="3-securely-expose-your-localhost-to-the-internet"></a><span data-ttu-id="af8e4-142">3. Stellen Sie Ihren localhost sicher für das Internet zur Verfügung</span><span class="sxs-lookup"><span data-stu-id="af8e4-142">3. Securely expose your localhost to the internet</span></span>

<span data-ttu-id="af8e4-143">Werfen Sie einen Blick auf die Datei, die einen HTTP-Server erstellt und routing behandelt, um eingehende `index.js` Anforderungen an Ihren Bot zu lauschen.</span><span class="sxs-lookup"><span data-stu-id="af8e4-143">Take a look at the `index.js` file, which creates an HTTP server and handles routing to listen for incoming requests to your bot.</span></span> <span data-ttu-id="af8e4-144">Die `/api/messages` ist die Endpunkt-URL Ihrer App, um auf Clientanforderungen zu reagieren:</span><span class="sxs-lookup"><span data-stu-id="af8e4-144">The `/api/messages` is your app's endpoint URL to respond to client requests:</span></span> 

```JavaScript
server.post('/api/messages', (req, res) => { 
  adapter.processActivity(req, res, async (context) => { 
    await botActivityHandler.run(context); 
  }); 
}); 
```

<span data-ttu-id="af8e4-145">Um die Anforderungen an die Logik Ihres Bots weiter zu weiterleiten, müssen Sie eine öffentlich zugängliche URL einrichten, z. B. `https://example.com/api/messages` , anstatt `https://localhost` .</span><span class="sxs-lookup"><span data-stu-id="af8e4-145">To forward the requests to your bot's logic, you must set up a publicly accessible URL, such as `https://example.com/api/messages`, instead of `https://localhost`.</span></span> <span data-ttu-id="af8e4-146">Da Ihre App derzeit von Ihrem localhost ausgeführt wird, müssen Sie *das* Netzwerk tunneln.</span><span class="sxs-lookup"><span data-stu-id="af8e4-146">Because your app is running from your localhost currently, you must *tunnel* the network.</span></span>

<span data-ttu-id="af8e4-147">Tunneling ist ein Protokoll, mit dem Sie Daten über ein Netzwerk übertragen können.</span><span class="sxs-lookup"><span data-stu-id="af8e4-147">Tunneling is a protocol that allows you to transport data across a network.</span></span> <span data-ttu-id="af8e4-148">Und mit dem localhost-Tunneling können Sie eine Verbindung zwischen Ihrem lokalen Computer und einer Remoteverbindung herstellen.</span><span class="sxs-lookup"><span data-stu-id="af8e4-148">And localhost tunneling gives you a connection between your local machine and a remote connection.</span></span> <span data-ttu-id="af8e4-149">Um Ihren localhost sicher für das Internet verfügbar zu machen, empfehlen wir Die Verwendung des Drittanbietertools **ngrok**.</span><span class="sxs-lookup"><span data-stu-id="af8e4-149">To securely expose your localhost to the internet, we recommend you to use the 3rd party tool called, **ngrok**.</span></span> <span data-ttu-id="af8e4-150">Dadurch erhalten Sie eine sichere URL.</span><span class="sxs-lookup"><span data-stu-id="af8e4-150">This will give you a secure URL.</span></span> 

1. <span data-ttu-id="af8e4-151">Wechseln Sie zur [ngrok.com,](https://ngrok.com/download) und befolgen Sie die Anweisungen zum Installieren und Einrichten von ngrok in Ihrer Umgebung.</span><span class="sxs-lookup"><span data-stu-id="af8e4-151">Go to the [ngrok.com](https://ngrok.com/download) site and follow the instruction to install and set up ngrok in your environment.</span></span> 
    
    <span data-ttu-id="af8e4-152">Fügen Sie den vollständigen Pfad zur ngrok.exe, die Sie zur Systempfadumgebungsvariablen installiert haben.</span><span class="sxs-lookup"><span data-stu-id="af8e4-152">Add the full path to the ngrok.exe file that you installed to the system PATH environment variable.</span></span> <span data-ttu-id="af8e4-153">Die genauen Schritte sind spezifisch für die shell, die Sie verwenden.</span><span class="sxs-lookup"><span data-stu-id="af8e4-153">The exact steps are specific to the shell that you are using.</span></span>

1.  <span data-ttu-id="af8e4-154">Nachdem Sie die Einrichtung abgeschlossen haben, öffnen Sie ein Terminal, und führen Sie `ngrok http -host-header=rewrite 3978` aus.</span><span class="sxs-lookup"><span data-stu-id="af8e4-154">After you have finished setting it up, open a terminal and run `ngrok http -host-header=rewrite 3978`.</span></span> 

    <span data-ttu-id="af8e4-155">Ngrok stellt Ihnen nun eine öffentliche, sichere URL zur Seite, die an Ihren localhost an Port 3978 weitergeleitet wird. Kopieren Sie daher beispielsweise die HTTPS-URL, wie im screenshot unten gezeigt, da Teams HTTPS-Verbindungen `https://287a4f4223bc.ngrok.io` erfordert:</span><span class="sxs-lookup"><span data-stu-id="af8e4-155">Now ngrok provides you a public, secure URL that forwards to your localhost at port 3978, so copy the HTTPS URL, for example, `https://287a4f4223bc.ngrok.io` as shown in the screenshot below, since Teams requires HTTPS connections:</span></span> 

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-ngrok-06.png" alt-text="Screenshot des Tunnelns von localhost mit ngrok.":::

1. <span data-ttu-id="af8e4-157">Registrieren Sie die URL im App-Manifest.</span><span class="sxs-lookup"><span data-stu-id="af8e4-157">Register the URL in your app manifest.</span></span> 

## <a name="4-register-your-bot-endpoint"></a><span data-ttu-id="af8e4-158">4. Registrieren Des Bot-Endpunkts</span><span class="sxs-lookup"><span data-stu-id="af8e4-158">4. Register your bot endpoint</span></span>

<span data-ttu-id="af8e4-159">Um einen Bot in Teams zu verwenden, müssen Sie ihn beim Azure Bot Service registrieren.</span><span class="sxs-lookup"><span data-stu-id="af8e4-159">To use a bot in Teams, you must register it with the Azure Bot Service.</span></span> <span data-ttu-id="af8e4-160">Dies erfolgt automatisch, wenn Sie Ihre App mithilfe des Teams Toolkits einrichten.</span><span class="sxs-lookup"><span data-stu-id="af8e4-160">This is done automatically when you set up your app using the Teams Toolkit.</span></span>

<span data-ttu-id="af8e4-161">Sie müssen weiterhin eine Endpunktadresse angeben, um Benutzernachrichten oder Anforderungen zu empfangen und zu verarbeiten, die an den Bot gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="af8e4-161">You must still specify an endpoint address to receive and process user messages, or requests, sent to the bot.</span></span> <span data-ttu-id="af8e4-162">In der Regel sieht die URL wie `https://HOST_URL/api/messages` aus.</span><span class="sxs-lookup"><span data-stu-id="af8e4-162">Typically, the URL looks like `https://HOST_URL/api/messages`.</span></span> <span data-ttu-id="af8e4-163">Sie können dies schnell im Toolkit konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="af8e4-163">You can configure this quickly in the toolkit.</span></span>

1. <span data-ttu-id="af8e4-164">Öffnen Visual Studio Microsoft Teams **Toolkit** in Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="af8e4-164">In Visual Studio Code, open **Microsoft Teams Toolkit**.</span></span>
1. <span data-ttu-id="af8e4-165">Wählen **Sie Bots**  >  **Vorhandene Botregistrierungen aus,** und wählen Sie den Bot aus, den Sie während des Setups erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="af8e4-165">Select **Bots** > **Existing bot registrations** and select the bot you created during setup.</span></span> 
1. <span data-ttu-id="af8e4-166">Geben Sie im Feld **Bot-Endpunktadresse** die ngrok-URL ein, z. B. , wo Sie den Bot hosten und `https://287a4f4223bc.ngrok.io` an ihn `/api/messages` anfügen:</span><span class="sxs-lookup"><span data-stu-id="af8e4-166">In the **Bot endpoint address** field, enter the ngrok URL, for example, `https://287a4f4223bc.ngrok.io`, where you're hosting the bot and append `/api/messages` to it:</span></span>

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-07.png" alt-text="Screenshot, der zeigt, wie Sie localhost mit ngrok tunneln.":::

    <span data-ttu-id="af8e4-168">Ihr Bot kann auf Nachrichten in Teams reagieren, nachdem Sie den Endpunkt ordnungsgemäß eingerichtet haben.</span><span class="sxs-lookup"><span data-stu-id="af8e4-168">Your bot will be able to respond to messages in Teams, after you set up the endpoint correctly.</span></span> 

## <a name="5-build-and-run-your-app"></a><span data-ttu-id="af8e4-169">5. Erstellen und Ausführen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="af8e4-169">5. Build and run your app</span></span>

<span data-ttu-id="af8e4-170">Sie haben eine URL zum Hosten Ihres Bots eingerichtet und für die Verarbeitung von Nachrichten konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="af8e4-170">You've set up a URL to host your bot and configured it to handle messages.</span></span> <span data-ttu-id="af8e4-171">Es ist an der Zeit, Ihre App in Betrieb zu halten.</span><span class="sxs-lookup"><span data-stu-id="af8e4-171">It's time to get your app up and running.</span></span>

1. <span data-ttu-id="af8e4-172">Wechseln Sie in einem Terminal zum Stammverzeichnis Ihres App-Projekts, und führen Sie `npm install` aus.</span><span class="sxs-lookup"><span data-stu-id="af8e4-172">In a terminal, go to the root directory of your app project and run `npm install`.</span></span>
1. <span data-ttu-id="af8e4-173">Führen Sie `npm start` aus.</span><span class="sxs-lookup"><span data-stu-id="af8e4-173">Run `npm start`.</span></span>

   <span data-ttu-id="af8e4-174">Wenn dies erfolgreich ist, wird die folgende Meldung angezeigt, die angibt, dass Ihr Bot aktivitäten bei Ihrer `localhost` abhört:</span><span class="sxs-lookup"><span data-stu-id="af8e4-174">If successful, you see the following message indicating your bot is listening for activity at your `localhost`:</span></span>

   `Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-bot-in-teams"></a><span data-ttu-id="af8e4-175">6. Querladen Des Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="af8e4-175">6. Sideload your bot in Teams</span></span>

<span data-ttu-id="af8e4-176">Wenn Ihr Bot ausgeführt wird, können Sie ihn in Teams installieren.</span><span class="sxs-lookup"><span data-stu-id="af8e4-176">With your bot running, you can install it in Teams.</span></span>

> [!TIP]
> <span data-ttu-id="af8e4-177">Wenn Sie eine Teams-App noch nicht nebeneinander geladen haben und Probleme auftreten, führen Sie diese [Anweisungen aus.](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams)</span><span class="sxs-lookup"><span data-stu-id="af8e4-177">If you haven't sideloaded a Teams app before and run into issues, follow these [instructions](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams).</span></span>

1. <span data-ttu-id="af8e4-178">Wählen Visual Studio Code die **F5-Taste** aus, um einen Teams-Webclient zu starten.</span><span class="sxs-lookup"><span data-stu-id="af8e4-178">In Visual Studio Code, select the **F5** key to launch a Teams web client.</span></span>
1. <span data-ttu-id="af8e4-179">Wählen Sie im Dialogfeld App-Installation die Option **Für mich hinzufügen aus.**</span><span class="sxs-lookup"><span data-stu-id="af8e4-179">In the app install dialog, select **Add for me**.</span></span> 

   > [!Note]
   > <span data-ttu-id="af8e4-180">Standardmäßig wird die App Ihrer 1:1-Chatnachricht hinzugefügt, Sie können sie jedoch in einem Team oder Chat installieren, indem Sie auf den kleinen Pfeil neben Hinzufügen für mich **klicken.**</span><span class="sxs-lookup"><span data-stu-id="af8e4-180">By default, the app is added to your 1:1 direct chat message, however you can choose to install it to a team or chat by clicking the little arrow beside **Add for me**.</span></span> <span data-ttu-id="af8e4-181">In diesem Lernprogramm klicken wir einfach auf Hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="af8e4-181">In this tutorial, let’s just click Add.</span></span>

   :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-install-08.png" alt-text="Screenshot, der das Tunneln von localhost mit ngrok zeigt.":::

## <a name="7-test-your-bot"></a><span data-ttu-id="af8e4-183">7. Testen Des Bots</span><span class="sxs-lookup"><span data-stu-id="af8e4-183">7. Test your bot</span></span>

<span data-ttu-id="af8e4-184">Sagen wir "Hello" zu Ihrem Bot.</span><span class="sxs-lookup"><span data-stu-id="af8e4-184">Let's say "Hello" to your bot.</span></span>

* <span data-ttu-id="af8e4-185">Senden Sie im Feld Verfassen eine `Hello` Nachricht.</span><span class="sxs-lookup"><span data-stu-id="af8e4-185">In the compose box, send a `Hello` message.</span></span>
    <span data-ttu-id="af8e4-186">Ihr Bot antwortet mit einer Nachricht wie der folgenden:</span><span class="sxs-lookup"><span data-stu-id="af8e4-186">Your bot replies with something like the following message:</span></span>

    :::image type="content" source="../assets/images/build-your-first-app/teams-client-bot.png" alt-text="Ein Screenshot, auf dem ein Benutzer &quot;Hello&quot; zu einem Teams-Bot sagt und eine Antwort erhalten.":::

    <span data-ttu-id="af8e4-188">Sie haben nun einen einfachen Teams-Bot erstellt, der mit Benutzern 1:1 oder in Gruppeneinstellungen (Kanäle und Chats) kommunizieren 🎉</span><span class="sxs-lookup"><span data-stu-id="af8e4-188">You have now created a basic Teams bot that can communicate with users one-on-one or in group settings (channels and chats) 🎉</span></span>

## <a name="troubleshoot-your-bot"></a><span data-ttu-id="af8e4-189">Problembehandlung für Ihren Bot</span><span class="sxs-lookup"><span data-stu-id="af8e4-189">Troubleshoot your bot</span></span>

<span data-ttu-id="af8e4-190">Die folgenden Informationen können hilfreich sein, wenn Beim Abschließen dieses Lernprogramms Probleme auftreten.</span><span class="sxs-lookup"><span data-stu-id="af8e4-190">The following information may help if you had issues completing this tutorial.</span></span>

### <a name="bot-isnt-connected-to-teams"></a><span data-ttu-id="af8e4-191">Bot ist nicht mit Teams verbunden</span><span class="sxs-lookup"><span data-stu-id="af8e4-191">Bot isn't connected to Teams</span></span>


<span data-ttu-id="af8e4-192">Wenn Sie Ihre App installiert haben, der Bot jedoch nicht funktioniert, stellen Sie sicher, dass der Bot mit dem Teams-Kanal des [Azure Bot Service verbunden *ist.*](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="af8e4-192">If you installed your app but the bot isn't working, make sure the bot is [connected to the Azure Bot Service's Teams *channel*](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true).</span></span>

<span data-ttu-id="af8e4-193">Es ist wichtig zu wissen, dass dies nicht mit einem Kanal in Teams identisch ist.</span><span class="sxs-lookup"><span data-stu-id="af8e4-193">It's important to understand that this isn't the same as a channel in Teams.</span></span> <span data-ttu-id="af8e4-194">In diesem Fall verbindet der Azure Bot Service Ihren Bot mit Teams oder einer anderen unterstützten Microsoft- oder [Drittanbieter-Kommunikations-App.](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="af8e4-194">In this case, a channel is how the Azure Bot Service connects your bot to Teams or another [supported Microsoft or third-party communications app](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span>

## <a name="see-also"></a><span data-ttu-id="af8e4-195">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="af8e4-195">See also</span></span>

* [<span data-ttu-id="af8e4-196">Bot-Grundlagen</span><span class="sxs-lookup"><span data-stu-id="af8e4-196">Bot basics</span></span>](../bots/bot-basics.md)
* [<span data-ttu-id="af8e4-197">Erstellen einer persönlichen Registerkarte für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="af8e4-197">Build a personal tab for Microsoft Teams</span></span>](../build-your-first-app/build-personal-tab.md)
* [<span data-ttu-id="af8e4-198">Sehen Sie sich an, welche anderen Teams Bots mit einem unserer Beispiele arbeiten können</span><span class="sxs-lookup"><span data-stu-id="af8e4-198">See what else Teams bots can do with one of our samples</span></span>](https://github.com/microsoft/BotBuilder-Samples#teams-samples)
* [<span data-ttu-id="af8e4-199">Grundlegende Informationen zu Bot-Unterhaltungen</span><span class="sxs-lookup"><span data-stu-id="af8e4-199">Bot conversation basics</span></span>](../bots/how-to/conversations/conversation-basics.md)
* [<span data-ttu-id="af8e4-200">Richtlinien für den Entwurf</span><span class="sxs-lookup"><span data-stu-id="af8e4-200">Design guidelines</span></span>](../bots/design/bots.md) 
* [<span data-ttu-id="af8e4-201">Produktionsbereite Benutzeroberflächenvorlagen</span><span class="sxs-lookup"><span data-stu-id="af8e4-201">Production-ready UI templates</span></span>](../concepts/design/design-teams-app-ui-templates.md)
* [<span data-ttu-id="af8e4-202">Bot-Authentifizierung in Teams</span><span class="sxs-lookup"><span data-stu-id="af8e4-202">Bot authentication in Teams</span></span>](../bots/how-to/authentication/auth-flow-bot.md)
* [<span data-ttu-id="af8e4-203">Microsoft Bot Framework</span><span class="sxs-lookup"><span data-stu-id="af8e4-203">Microsoft Bot Framework</span></span>](https://dev.botframework.com/)
* [<span data-ttu-id="af8e4-204">Erstellen eines Bots ohne Toolkit</span><span class="sxs-lookup"><span data-stu-id="af8e4-204">Create a bot without the toolkit</span></span>](../resources/bot-v3/bots-create.md)

## <a name="next-step"></a><span data-ttu-id="af8e4-205">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="af8e4-205">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="af8e4-206">Erstellen einer Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="af8e4-206">Build a messaging extension</span></span>](../build-your-first-app/build-messaging-extension.md)
