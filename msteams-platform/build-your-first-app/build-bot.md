---
title: Erste Schritte – Erstellen eines Bots
author: heath-hamilton
description: Erstellen Sie mithilfe des Microsoft Teams Toolkits schnell einen Microsoft Teams-Bot.
ms.author: lajanuar
ms.date: 11/04/2020
ms.topic: tutorial
ms.openlocfilehash: fbabd5130f0b7eb648a980f5f143792cc4c17933
ms.sourcegitcommit: 00c657e3bf57d3b92aca7da941cde47a2eeff4d0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "49911947"
---
# <a name="build-a-bot-for-microsoft-teams"></a><span data-ttu-id="93988-103">Erstellen eines Bots für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="93988-103">Build a bot for Microsoft Teams</span></span>

<span data-ttu-id="93988-104">In diesem Lernprogramm  erstellen Sie eine einfache Bot-App.</span><span class="sxs-lookup"><span data-stu-id="93988-104">You'll build a basic *bot* app in this tutorial.</span></span> <span data-ttu-id="93988-105">Ein Bot fungiert als Vermittler zwischen Den Benutzern von Teams und Ihrem Webdienst.</span><span class="sxs-lookup"><span data-stu-id="93988-105">A bot acts as an intermediary between Teams users and your web service.</span></span> <span data-ttu-id="93988-106">Benutzer können mit einem Bot chatten, um schnell Informationen zu erhalten oder Workflows und Aufgaben zu initiieren, die von Ihrem Dienst ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="93988-106">People can chat with a bot to quickly get information or initiate workflows and tasks performed by your service.</span></span>

## <a name="your-assignment"></a><span data-ttu-id="93988-107">Ihre Zuordnung</span><span class="sxs-lookup"><span data-stu-id="93988-107">Your assignment</span></span>

<span data-ttu-id="93988-108">Ihr Arbeitsplatz hat eine Teams-App erstellt, die [Registerkarten](../build-your-first-app/build-personal-tab.md) zum Anzeigen wichtiger Kontaktinformationen verwendet.</span><span class="sxs-lookup"><span data-stu-id="93988-108">Your workplace created a Teams app that uses [tabs](../build-your-first-app/build-personal-tab.md) to surface important contact information.</span></span> <span data-ttu-id="93988-109">Kollegen haben beispielsweise schnellen Zugriff auf die Telefonnummer des Helpdesks.</span><span class="sxs-lookup"><span data-stu-id="93988-109">For example, colleagues have quick access to the help desk phone number.</span></span> <span data-ttu-id="93988-110">Aber was passiert, wenn sich Personen über einen Chatbot an den Helpdesk wenden können, anstatt zu anrufen?</span><span class="sxs-lookup"><span data-stu-id="93988-110">But instead of calling, what if people could contact the help desk using a chatbot?</span></span> <span data-ttu-id="93988-111">Ihr Chef bittet Sie, zu sehen, wie schnell Sie einen einfachen Unterhaltungsbot in Teams einrichten können.</span><span class="sxs-lookup"><span data-stu-id="93988-111">Your boss asks you to look at how quickly you can get a basic conversational bot up and running in Teams.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="93988-112">Was Sie lernen werden</span><span class="sxs-lookup"><span data-stu-id="93988-112">What you'll learn</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="93988-113">Erstellen eines App-Projekts und -Bots mithilfe des Microsoft Teams Toolkit for Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="93988-113">Create an app project and bot using the Microsoft Teams Toolkit for Visual Studio Code</span></span>
> * <span data-ttu-id="93988-114">Identifizieren einiger der für Bots relevanten App-Konfigurationen und Gerüste</span><span class="sxs-lookup"><span data-stu-id="93988-114">Identify some of the app configurations and scaffolding relevant to bots</span></span>
> * <span data-ttu-id="93988-115">Lokales Hosten einer App</span><span class="sxs-lookup"><span data-stu-id="93988-115">Host an app locally</span></span>
> * <span data-ttu-id="93988-116">Konfigurieren eines Bots für Teams</span><span class="sxs-lookup"><span data-stu-id="93988-116">Configure a bot for Teams</span></span>
> * <span data-ttu-id="93988-117">Querladen und Testen eines Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="93988-117">Sideload and test a bot in Teams</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="93988-118">Vorabinformationen</span><span class="sxs-lookup"><span data-stu-id="93988-118">Before you begin</span></span>

<span data-ttu-id="93988-119">Falls noch nicht, stellen Sie sicher, dass Sie die Voraussetzungen für die Entwicklung von Teams verstehen und [installieren.](build-first-app-overview.md#get-prerequisites)</span><span class="sxs-lookup"><span data-stu-id="93988-119">If you haven't yet, make sure you [understand and install the Teams development prerequisites](build-first-app-overview.md#get-prerequisites).</span></span>

## <a name="1-create-your-app-project"></a><span data-ttu-id="93988-120">1. Erstellen Ihres App-Projekts</span><span class="sxs-lookup"><span data-stu-id="93988-120">1. Create your app project</span></span>

<span data-ttu-id="93988-121">Das Microsoft Teams Toolkit hilft Ihnen beim Einrichten der folgenden Komponenten für Ihre App:</span><span class="sxs-lookup"><span data-stu-id="93988-121">The Microsoft Teams Toolkit helps you set up the following components for your app:</span></span>

* <span data-ttu-id="93988-122">**Für Bots relevante App-Konfigurationen** und Gerüste</span><span class="sxs-lookup"><span data-stu-id="93988-122">**App configurations and scaffolding** relevant to bots</span></span>
* <span data-ttu-id="93988-123">**Bot,** der automatisch beim Microsoft Azure Bot Service registriert wird</span><span class="sxs-lookup"><span data-stu-id="93988-123">**Bot** that's automatically registered with the Microsoft Azure Bot Service</span></span>

> [!TIP]
> <span data-ttu-id="93988-124">Wenn Sie noch kein Teams-App-Projekt erstellt haben, ist [](../build-your-first-app/build-and-run.md) es möglicherweise hilfreich, diese Anweisungen zu befolgen, in der Projekte ausführlicher erläutert werden.</span><span class="sxs-lookup"><span data-stu-id="93988-124">If you haven't created a Teams app project before, you might find it helpful to follow [these instructions](../build-your-first-app/build-and-run.md) that explain projects in more detail.</span></span>

1. Wählen Visual Studio Code auf der linken Aktivitätsleiste **Microsoft Teams** aus, und wählen :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: Sie **"Neue Teams-App erstellen" aus.**
1. <span data-ttu-id="93988-126">Wenn Sie dazu aufgefordert werden, melden Sie sich mit Ihrem Microsoft 365-Entwicklungskonto an.</span><span class="sxs-lookup"><span data-stu-id="93988-126">When prompted, sign in with your Microsoft 365 development account.</span></span>
1. <span data-ttu-id="93988-127">Wählen Sie **auf dem Bildschirm** "Funktionen hinzufügen" **"Bot"** und dann **"Weiter" aus.**</span><span class="sxs-lookup"><span data-stu-id="93988-127">On the **Add capabilities** screen, select **Bot** then **Next**.</span></span>
1. <span data-ttu-id="93988-128">Geben Sie einen Namen für Ihre Teams-App ein.</span><span class="sxs-lookup"><span data-stu-id="93988-128">Enter a name for your Teams app.</span></span> <span data-ttu-id="93988-129">(Dies ist der Standardname für Ihre App und auch der Name des App-Projektverzeichnisses auf dem lokalen Computer.)</span><span class="sxs-lookup"><span data-stu-id="93988-129">(This is the default name for your app and also the name of the app project directory on your local machine.)</span></span>
1. <span data-ttu-id="93988-130">Wechseln Sie zu **"Bot konfigurieren",** und wählen **Sie "Neuen Bot erstellen"** und dann **"Botregistrierung erstellen" aus.**</span><span class="sxs-lookup"><span data-stu-id="93988-130">Go to **Configure bot** and select **Create a new Bot** then **Create Bot Registration**.</span></span> <span data-ttu-id="93988-131">Wenn dies erfolgreich ist, hat Ihr neuer Bot den **Status "Registriert".**</span><span class="sxs-lookup"><span data-stu-id="93988-131">If successful, your new bot will have a **Registered** status.</span></span>
1. <span data-ttu-id="93988-132">Wählen **Sie "Fertig** stellen" am unteren Rand des Bildschirms aus, und wählen Sie einen Speicherort zum Erstellen des Projekts aus.</span><span class="sxs-lookup"><span data-stu-id="93988-132">Select **Finish** at the bottom of the screen and choose a location to create your project.</span></span>

## <a name="2-identify-relevant-app-project-components"></a><span data-ttu-id="93988-133">2. Identifizieren relevanter Komponenten des App-Projekts</span><span class="sxs-lookup"><span data-stu-id="93988-133">2. Identify relevant app project components</span></span>

<span data-ttu-id="93988-134">Ein Teil der App-Konfigurationen und -Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Teams Toolkit erstellen.</span><span class="sxs-lookup"><span data-stu-id="93988-134">Much of the app configurations and scaffolding are set up automatically when you create your project with the Teams Toolkit.</span></span> <span data-ttu-id="93988-135">Sehen wir uns die Hauptkomponenten zum Erstellen eines Bots an.</span><span class="sxs-lookup"><span data-stu-id="93988-135">Let's look at the main components for building a bot.</span></span>

### <a name="app-configurations"></a><span data-ttu-id="93988-136">App-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="93988-136">App configurations</span></span>

<span data-ttu-id="93988-137">Wenn Sie die Konfigurationen Ihres Bots anzeigen oder aktualisieren möchten, wählen **Sie App Studio** im Toolkit aus, und wechseln Sie zu **Bots.**</span><span class="sxs-lookup"><span data-stu-id="93988-137">To view or update your bot's configurations, select **App Studio** in the toolkit and go to **Bots**.</span></span>

### <a name="app-scaffolding"></a><span data-ttu-id="93988-138">App-Gerüst</span><span class="sxs-lookup"><span data-stu-id="93988-138">App scaffolding</span></span>

<span data-ttu-id="93988-139">Das Gerüst der App stellt eine Datei im Stammverzeichnis Ihres Projekts zur Verarbeitung der Aktivitäten ihres Bots in Teams (z. B. wie der Bot auf bestimmte Nachrichten wie `botActivityHandler.js` "Hello") reagiert.</span><span class="sxs-lookup"><span data-stu-id="93988-139">The app scaffolding provides a `botActivityHandler.js` file, located in the root directory of your project, for handling how your bot processes activities in Teams (for example, how the bot responds to specific messages such as "Hello").</span></span>

## <a name="3-set-up-a-secure-tunnel-to-your-app"></a><span data-ttu-id="93988-140">3. Einrichten eines sicheren Tunnels für Ihre App</span><span class="sxs-lookup"><span data-stu-id="93988-140">3. Set up a secure tunnel to your app</span></span>

<span data-ttu-id="93988-141">Zu Testzwecken hosten wir Ihre App auf einem lokalen Webserver (Port 3978).</span><span class="sxs-lookup"><span data-stu-id="93988-141">For testing purposes, let's host your app on a local web server (port 3978).</span></span>

1. <span data-ttu-id="93988-142">Falls noch nicht, installieren Sie [ngrok](https://ngrok.com/download).</span><span class="sxs-lookup"><span data-stu-id="93988-142">If you haven't already, install [ngrok](https://ngrok.com/download).</span></span>
1. <span data-ttu-id="93988-143">Führen Sie in einem Terminal die Ausführung `ngrok http -host-header=rewrite 3978` aus.</span><span class="sxs-lookup"><span data-stu-id="93988-143">In a terminal, run `ngrok http -host-header=rewrite 3978`.</span></span>
1. <span data-ttu-id="93988-144">Kopieren Sie die HTTPS-URL in der Ausgabe (z. B. `https://468b9ab725e9.ngrok.io` ), da Teams https-Verbindungen benötigt.</span><span class="sxs-lookup"><span data-stu-id="93988-144">Copy the HTTPS URL in the output (for example, `https://468b9ab725e9.ngrok.io`) since Teams requires HTTPS connections.</span></span>

<span data-ttu-id="93988-145">Mit dieser URL kann Teams (für das HTTPS-Verbindungen erforderlich sind) an den Ort tunneln, an dem Sie Ihre App hosten (an `localhost` Port 3978).</span><span class="sxs-lookup"><span data-stu-id="93988-145">With this URL, Teams (which requires HTTPS connections) will be able tunnel to where you're hosting your app (`localhost` on port 3978).</span></span>

## <a name="4-configure-your-bot"></a><span data-ttu-id="93988-146">4. Konfigurieren Des Bots</span><span class="sxs-lookup"><span data-stu-id="93988-146">4. Configure your bot</span></span>

<span data-ttu-id="93988-147">Um einen Bot in Teams zu verwenden, müssen Sie ihn beim Azure Bot Service registrieren.</span><span class="sxs-lookup"><span data-stu-id="93988-147">To use a bot in Teams, you must register it with the Azure Bot Service.</span></span> <span data-ttu-id="93988-148">Dies erfolgt automatisch, wenn Sie Ihre App mit dem Teams Toolkit einrichten.</span><span class="sxs-lookup"><span data-stu-id="93988-148">Lucky for you, this is done automatically when you set up your app using the Teams Toolkit.</span></span>

<span data-ttu-id="93988-149">Sie müssen dennoch eine Endpunktadresse angeben, um Benutzernachrichten (d. h. Anforderungen) zu empfangen und zu verarbeiten, die an den Bot gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="93988-149">You still must specify an endpoint address to receive and process user messages (i.e., requests) sent to the bot.</span></span> <span data-ttu-id="93988-150">In der Regel sieht die URL wie `https://HOST_URL/api/messages` .</span><span class="sxs-lookup"><span data-stu-id="93988-150">Typically, the URL looks like `https://HOST_URL/api/messages`.</span></span> <span data-ttu-id="93988-151">Sie können dies im Toolkit schnell konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="93988-151">You can configure this quickly in the toolkit.</span></span>

1. In Visual Studio Code, select **Microsoft Teams** on the left Activity Bar and choose Open Microsoft Teams :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: **Toolkit**.
1. <span data-ttu-id="93988-153">Wechseln Sie **zu Bots > vorhandenen Botregistrierungen,** und wählen Sie den Bot aus, den Sie während des Setups erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="93988-153">Go to **Bots > Existing bot registrations** and select the bot you created during setup.</span></span>
1. <span data-ttu-id="93988-154">Geben Sie **im Adressfeld des** Bot-Endpunkts die ngrok-URL ein (z. B. ), in der Sie den Bot hosten, `https://468b9ab725e9.ngrok.io` und fügen Sie ihn `/api/messages` an.</span><span class="sxs-lookup"><span data-stu-id="93988-154">In the **Bot endpoint address** field, enter the ngrok URL (for example, `https://468b9ab725e9.ngrok.io`) where you're hosting the bot and append `/api/messages` to it.</span></span><br/>
    :::image type="content" source="../assets/images/build-your-first-app/bot-config-endpoint-url.png" alt-text="Illustration showing where you can configure the bot endpoint URL in the Teams Toolkit.":::

<span data-ttu-id="93988-156">Ihr Bot kann auf Nachrichten in Teams reagieren.</span><span class="sxs-lookup"><span data-stu-id="93988-156">Your bot will be able to respond to messages in Teams.</span></span>

## <a name="5-build-and-run-your-app"></a><span data-ttu-id="93988-157">5. Erstellen und Ausführen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="93988-157">5. Build and run your app</span></span>

<span data-ttu-id="93988-158">Sie haben eine URL zum Hosten Ihres Bots eingerichtet und für die Verarbeitung von Nachrichten konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="93988-158">You've set up a URL to host your bot and configured it to handle messages.</span></span> <span data-ttu-id="93988-159">Es ist an der Zeit, Ihre App zu starten und zu starten.</span><span class="sxs-lookup"><span data-stu-id="93988-159">It's time to get your app up and running.</span></span>

1. <span data-ttu-id="93988-160">Wechseln Sie in einem Terminal zum Stammverzeichnis Ihres App-Projekts, und führen Sie es `npm install` aus.</span><span class="sxs-lookup"><span data-stu-id="93988-160">In a terminal, go to the root directory of your app project and run `npm install`.</span></span>
1. <span data-ttu-id="93988-161">Führen Sie `npm start` .</span><span class="sxs-lookup"><span data-stu-id="93988-161">Run `npm start`.</span></span>

<span data-ttu-id="93988-162">Wenn dies erfolgreich ist, wird die folgende Meldung angezeigt, die angibt, dass Ihr Bot auf Aktivitäten bei Ihnen `localhost` lauscht:</span><span class="sxs-lookup"><span data-stu-id="93988-162">If successful, you see the following message indicating your bot is listening for activity at your `localhost`:</span></span>

`Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-bot-in-teams"></a><span data-ttu-id="93988-163">6. Querladen Ihres Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="93988-163">6. Sideload your bot in Teams</span></span>

<span data-ttu-id="93988-164">Wenn Ihr Bot ausgeführt wird, können Sie ihn in Teams installieren.</span><span class="sxs-lookup"><span data-stu-id="93988-164">With your bot running, you can install it in Teams.</span></span>

> [!TIP]
> <span data-ttu-id="93988-165">Wenn Sie zuvor noch keine Teams-App sideloaded haben und Probleme auftreten, führen Sie die folgenden [Anweisungen aus.](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams)</span><span class="sxs-lookup"><span data-stu-id="93988-165">If you haven't sideloaded a Teams app before and run into issues, follow these [instructions](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams).</span></span>

1. <span data-ttu-id="93988-166">Drücken Visual Studio Code die **F5-TASTE,** um einen Teams-Webclient zu starten.</span><span class="sxs-lookup"><span data-stu-id="93988-166">In Visual Studio Code, press the **F5** key to launch a Teams web client.</span></span>
1. <span data-ttu-id="93988-167">Wählen Sie im Dialogfeld "App-Installation" die Option **"Für mich hinzufügen" aus.**</span><span class="sxs-lookup"><span data-stu-id="93988-167">In the app install dialog, select **Add for me**.</span></span> <span data-ttu-id="93988-168">(Sie können den Bot einem Kanal oder Chat hinzufügen, aber es ist weniger aufdringlich für andere, einen Bot in einem 1:1-Chat zu testen.)</span><span class="sxs-lookup"><span data-stu-id="93988-168">(You could add the bot to a channel or chat, but it's less intrusive to others to test a bot in a one-on-one chat.)</span></span>

## <a name="7-test-your-bot"></a><span data-ttu-id="93988-169">7. Testen Des Bots</span><span class="sxs-lookup"><span data-stu-id="93988-169">7. Test your bot</span></span>

<span data-ttu-id="93988-170">Jetzt zum spaßig-Teil: Lassen Sie uns "Hello" zu Ihrem Bot sagen.</span><span class="sxs-lookup"><span data-stu-id="93988-170">Now for the fun part: Let's say "Hello" to your bot.</span></span>

1. <span data-ttu-id="93988-171">Senden Sie im Feld zum Verfassen eine `Hello` Nachricht.</span><span class="sxs-lookup"><span data-stu-id="93988-171">In the compose box, send a `Hello` message.</span></span>

<span data-ttu-id="93988-172">Ihr Bot antwortet mit einer Nachricht wie der folgenden.</span><span class="sxs-lookup"><span data-stu-id="93988-172">Your bot replies with something like the following message.</span></span>

:::image type="content" source="../assets/images/build-your-first-app/contoso-chatbot.png" alt-text="Ein Screenshot, der zeigt, wie ein Benutzer &quot;Hello&quot; zu einem Teams-Bot sagt und eine Antwort erhalten.":::

## <a name="well-done"></a><span data-ttu-id="93988-174">Gut gemacht</span><span class="sxs-lookup"><span data-stu-id="93988-174">Well done</span></span>

<span data-ttu-id="93988-175">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="93988-175">Congratulations!</span></span> <span data-ttu-id="93988-176">Sie verfügen über einen einfachen Teams-Bot, der mit Benutzern 1:1 oder in Gruppeneinstellungen (Kanäle und Chats) kommunizieren kann.</span><span class="sxs-lookup"><span data-stu-id="93988-176">You have a basic Teams bot that can communicate with users one-on-one or in group settings (channels and chats).</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="93988-177">Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="93988-177">Troubleshooting</span></span>

<span data-ttu-id="93988-178">Die folgenden Informationen können hilfreich sein, wenn beim Abschließen dieses Lernprogramms Probleme auftreten.</span><span class="sxs-lookup"><span data-stu-id="93988-178">The following information may help if you had issues completing this tutorial.</span></span>

### <a name="bot-isnt-connected-to-teams"></a><span data-ttu-id="93988-179">Bot ist nicht mit Teams verbunden</span><span class="sxs-lookup"><span data-stu-id="93988-179">Bot isn't connected to Teams</span></span>

<span data-ttu-id="93988-180">Wenn Sie Ihre App installiert haben, der Bot aber nicht funktioniert, stellen Sie sicher, dass der Bot mit dem Teams-Kanal des [Azure Bot Service verbunden *ist.*](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="93988-180">If you installed your app but the bot isn't working, make sure the bot is [connected to the Azure Bot Service's Teams *channel*](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true).</span></span>

<span data-ttu-id="93988-181">Es ist wichtig zu wissen, dass dies nicht mit einem Kanal in Teams identisch ist.</span><span class="sxs-lookup"><span data-stu-id="93988-181">It's important to understand that this isn't the same as a channel in Teams.</span></span> <span data-ttu-id="93988-182">In diesem Fall verbindet der Azure Bot Service Ihren Bot mit Teams oder einer anderen unterstützten Microsoft- oder [Drittanbieter-Kommunikations-App.](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="93988-182">In this case, a channel is how the Azure Bot Service connects your bot to Teams or another [supported Microsoft or third-party communications app](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span>

## <a name="learn-more"></a><span data-ttu-id="93988-183">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="93988-183">Learn more</span></span>

* [<span data-ttu-id="93988-184">Erfahren Sie, was Teams Bots sonst noch mit einem unserer Beispiele tun können.</span><span class="sxs-lookup"><span data-stu-id="93988-184">See what else Teams bots can do with one of our samples</span></span>](https://github.com/microsoft/BotBuilder-Samples#teams-samples)
* [<span data-ttu-id="93988-185">Grundlegende Informationen zu Bot-Unterhaltungen</span><span class="sxs-lookup"><span data-stu-id="93988-185">Bot conversation basics</span></span>](../bots/how-to/conversations/conversation-basics.md)
* <span data-ttu-id="93988-186">Folgen Sie [unseren Entwurfsrichtlinien,](../bots/design/bots.md) und erstellen Sie mit [produktionsbereiten](../concepts/design/design-teams-app-ui-templates.md) Benutzeroberflächenvorlagen, um eine nahtlose Benutzeroberfläche zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="93988-186">Follow our [design guidelines](../bots/design/bots.md) and build with [production-ready UI templates](../concepts/design/design-teams-app-ui-templates.md) to create a seamless experience.</span></span>
* [<span data-ttu-id="93988-187">Botauthentifizierung in Teams</span><span class="sxs-lookup"><span data-stu-id="93988-187">Bot authentication in Teams</span></span>](../bots/how-to/authentication/auth-flow-bot.md)
* [<span data-ttu-id="93988-188">Microsoft Bot Framework</span><span class="sxs-lookup"><span data-stu-id="93988-188">Microsoft Bot Framework</span></span>](https://dev.botframework.com/)
* [<span data-ttu-id="93988-189">Erstellen eines Bots ohne das Toolkit</span><span class="sxs-lookup"><span data-stu-id="93988-189">Create a bot without the toolkit</span></span>](../bots/how-to/create-a-bot-for-teams.md)
