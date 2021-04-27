---
title: Erste Schritte – Erstellen eines Bots
author: heath-hamilton
description: Erstellen Sie schnell einen Microsoft Teams-Bot mithilfe des Microsoft Teams Toolkits.
ms.author: lajanuar
localization_priority: Normal
ms.date: 11/04/2020
ms.topic: tutorial
ms.openlocfilehash: 5dfbfa05d2f1e36bbc14bd929cb2592303081522
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020000"
---
# <a name="build-a-bot-for-microsoft-teams"></a><span data-ttu-id="4a859-103">Erstellen eines Bots für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="4a859-103">Build a bot for Microsoft Teams</span></span>

<span data-ttu-id="4a859-104">In diesem Lernprogramm  erstellen Sie eine einfache Bot-App.</span><span class="sxs-lookup"><span data-stu-id="4a859-104">You'll build a basic *bot* app in this tutorial.</span></span> <span data-ttu-id="4a859-105">Ein Bot fungiert als Vermittler zwischen Teams-Benutzern und Ihrem Webdienst.</span><span class="sxs-lookup"><span data-stu-id="4a859-105">A bot acts as an intermediary between Teams users and your web service.</span></span> <span data-ttu-id="4a859-106">Benutzer können mit einem Bot chatten, um schnell Informationen zu erhalten oder Workflows und Aufgaben zu initiieren, die von Ihrem Dienst ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="4a859-106">People can chat with a bot to quickly get information or initiate workflows and tasks performed by your service.</span></span>

## <a name="your-assignment"></a><span data-ttu-id="4a859-107">Ihre Zuordnung</span><span class="sxs-lookup"><span data-stu-id="4a859-107">Your assignment</span></span>

<span data-ttu-id="4a859-108">Ihr Arbeitsplatz hat eine Teams-App erstellt, die [Registerkarten zum](../build-your-first-app/build-personal-tab.md) Anzeigen wichtiger Kontaktinformationen verwendet.</span><span class="sxs-lookup"><span data-stu-id="4a859-108">Your workplace created a Teams app that uses [tabs](../build-your-first-app/build-personal-tab.md) to surface important contact information.</span></span> <span data-ttu-id="4a859-109">Kollegen haben beispielsweise schnellen Zugriff auf die Telefonnummer des Helpdesks.</span><span class="sxs-lookup"><span data-stu-id="4a859-109">For example, colleagues have quick access to the help desk phone number.</span></span> <span data-ttu-id="4a859-110">Doch was wäre, wenn sich die Personen über einen Chatbot an den Helpdesk wenden könnten, anstatt zu anrufen?</span><span class="sxs-lookup"><span data-stu-id="4a859-110">But instead of calling, what if people could contact the help desk using a chatbot?</span></span> <span data-ttu-id="4a859-111">Ihr Vorgesetzter bittet Sie, zu sehen, wie schnell Sie einen einfachen Unterhaltungsbot in Teams einrichten und ausführen können.</span><span class="sxs-lookup"><span data-stu-id="4a859-111">Your boss asks you to look at how quickly you can get a basic conversational bot up and running in Teams.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="4a859-112">Was Sie lernen werden</span><span class="sxs-lookup"><span data-stu-id="4a859-112">What you'll learn</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="4a859-113">Erstellen eines App-Projekts und eines Bots mithilfe des Microsoft Teams Toolkits für Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4a859-113">Create an app project and bot using the Microsoft Teams Toolkit for Visual Studio Code</span></span>
> * <span data-ttu-id="4a859-114">Identifizieren einiger der für Bots relevanten App-Konfigurationen und Gerüste</span><span class="sxs-lookup"><span data-stu-id="4a859-114">Identify some of the app configurations and scaffolding relevant to bots</span></span>
> * <span data-ttu-id="4a859-115">Lokal hosten einer App</span><span class="sxs-lookup"><span data-stu-id="4a859-115">Host an app locally</span></span>
> * <span data-ttu-id="4a859-116">Konfigurieren eines Bots für Teams</span><span class="sxs-lookup"><span data-stu-id="4a859-116">Configure a bot for Teams</span></span>
> * <span data-ttu-id="4a859-117">Querladen und Testen eines Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="4a859-117">Sideload and test a bot in Teams</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="4a859-118">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="4a859-118">Before you begin</span></span>

<span data-ttu-id="4a859-119">Falls noch nicht, stellen Sie sicher, dass Sie die Voraussetzungen für die [Teams-Entwicklung verstehen und installieren.](build-first-app-overview.md#get-prerequisites)</span><span class="sxs-lookup"><span data-stu-id="4a859-119">If you haven't yet, make sure you [understand and install the Teams development prerequisites](build-first-app-overview.md#get-prerequisites).</span></span>

## <a name="1-create-your-app-project"></a><span data-ttu-id="4a859-120">1. Erstellen Ihres App-Projekts</span><span class="sxs-lookup"><span data-stu-id="4a859-120">1. Create your app project</span></span>

<span data-ttu-id="4a859-121">Das Microsoft Teams Toolkit hilft Ihnen beim Einrichten der folgenden Komponenten für Ihre App:</span><span class="sxs-lookup"><span data-stu-id="4a859-121">The Microsoft Teams Toolkit helps you set up the following components for your app:</span></span>

* <span data-ttu-id="4a859-122">**Für Bots relevante** App-Konfigurationen und Gerüste</span><span class="sxs-lookup"><span data-stu-id="4a859-122">**App configurations and scaffolding** relevant to bots</span></span>
* <span data-ttu-id="4a859-123">**Bot,** der automatisch beim Microsoft Azure Bot Service registriert ist</span><span class="sxs-lookup"><span data-stu-id="4a859-123">**Bot** that's automatically registered with the Microsoft Azure Bot Service</span></span>

> [!TIP]
> <span data-ttu-id="4a859-124">Wenn Sie noch kein Teams-App-Projekt erstellt haben, ist [](../build-your-first-app/build-and-run.md) es möglicherweise hilfreich, diese Anweisungen zu befolgen, die Projekte ausführlicher erläutern.</span><span class="sxs-lookup"><span data-stu-id="4a859-124">If you haven't created a Teams app project before, you might find it helpful to follow [these instructions](../build-your-first-app/build-and-run.md) that explain projects in more detail.</span></span>

1. Wählen Visual Studio Code auf der linken Aktivitätsleiste **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: aus, und wählen Sie Erstellen einer neuen **Teams-App aus.**
1. <span data-ttu-id="4a859-126">Melden Sie sich bei Aufforderung mit Ihrem Microsoft 365-Entwicklungskonto an.</span><span class="sxs-lookup"><span data-stu-id="4a859-126">When prompted, sign in with your Microsoft 365 development account.</span></span>
1. <span data-ttu-id="4a859-127">Wählen Sie **auf dem** Bildschirm Funktionen hinzufügen die Option **Bot** und dann **Weiter aus.**</span><span class="sxs-lookup"><span data-stu-id="4a859-127">On the **Add capabilities** screen, select **Bot** then **Next**.</span></span>
1. <span data-ttu-id="4a859-128">Geben Sie einen Namen für Ihre Teams-App ein.</span><span class="sxs-lookup"><span data-stu-id="4a859-128">Enter a name for your Teams app.</span></span> <span data-ttu-id="4a859-129">(Dies ist der Standardname für Ihre App und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.)</span><span class="sxs-lookup"><span data-stu-id="4a859-129">(This is the default name for your app and also the name of the app project directory on your local machine.)</span></span>
1. <span data-ttu-id="4a859-130">Wechseln Sie **zu Bot konfigurieren,** und wählen **Sie Erstellen eines neuen Bots** und **dann Botregistrierung erstellen aus.**</span><span class="sxs-lookup"><span data-stu-id="4a859-130">Go to **Configure bot** and select **Create a new Bot** then **Create Bot Registration**.</span></span> <span data-ttu-id="4a859-131">Wenn der neue Bot erfolgreich ist, hat er den **Status "Registriert".**</span><span class="sxs-lookup"><span data-stu-id="4a859-131">If successful, your new bot will have a **Registered** status.</span></span>
1. <span data-ttu-id="4a859-132">Wählen **Sie unten** auf dem Bildschirm Fertig stellen aus, und wählen Sie einen Speicherort aus, an dem Sie Ihr Projekt erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="4a859-132">Select **Finish** at the bottom of the screen and choose a location to create your project.</span></span>

## <a name="2-identify-relevant-app-project-components"></a><span data-ttu-id="4a859-133">2. Identifizieren relevanter App-Projektkomponenten</span><span class="sxs-lookup"><span data-stu-id="4a859-133">2. Identify relevant app project components</span></span>

<span data-ttu-id="4a859-134">Viele der App-Konfigurationen und Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Teams Toolkit erstellen.</span><span class="sxs-lookup"><span data-stu-id="4a859-134">Much of the app configurations and scaffolding are set up automatically when you create your project with the Teams Toolkit.</span></span> <span data-ttu-id="4a859-135">Sehen wir uns die Hauptkomponenten zum Erstellen eines Bots an.</span><span class="sxs-lookup"><span data-stu-id="4a859-135">Let's look at the main components for building a bot.</span></span>

### <a name="app-configurations"></a><span data-ttu-id="4a859-136">App-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="4a859-136">App configurations</span></span>

<span data-ttu-id="4a859-137">Wenn Sie die Konfigurationen Ihres Bots anzeigen oder aktualisieren möchten, wählen Sie im Toolkit **App Studio aus,** und wechseln Sie zu **Bots**.</span><span class="sxs-lookup"><span data-stu-id="4a859-137">To view or update your bot's configurations, select **App Studio** in the toolkit and go to **Bots**.</span></span>

### <a name="app-scaffolding"></a><span data-ttu-id="4a859-138">App-Gerüst</span><span class="sxs-lookup"><span data-stu-id="4a859-138">App scaffolding</span></span>

<span data-ttu-id="4a859-139">Das App-Gerüst stellt eine Datei im Stammverzeichnis Ihres Projekts zur Verarbeitung der Aktivitäten ihres Bots in Teams (z. B. wie der Bot auf bestimmte Nachrichten wie `botActivityHandler.js` "Hello") reagiert.</span><span class="sxs-lookup"><span data-stu-id="4a859-139">The app scaffolding provides a `botActivityHandler.js` file, located in the root directory of your project, for handling how your bot processes activities in Teams (for example, how the bot responds to specific messages such as "Hello").</span></span>

## <a name="3-set-up-a-secure-tunnel-to-your-app"></a><span data-ttu-id="4a859-140">3. Einrichten eines sicheren Tunnels für Ihre App</span><span class="sxs-lookup"><span data-stu-id="4a859-140">3. Set up a secure tunnel to your app</span></span>

<span data-ttu-id="4a859-141">Zu Testzwecken hosten wir Ihre App auf einem lokalen Webserver (Port 3978).</span><span class="sxs-lookup"><span data-stu-id="4a859-141">For testing purposes, let's host your app on a local web server (port 3978).</span></span>

1. <span data-ttu-id="4a859-142">Falls noch nicht, installieren Sie [ngrok](https://ngrok.com/download).</span><span class="sxs-lookup"><span data-stu-id="4a859-142">If you haven't already, install [ngrok](https://ngrok.com/download).</span></span>
1. <span data-ttu-id="4a859-143">Führen Sie in einem Terminal `ngrok http -host-header=rewrite 3978` aus.</span><span class="sxs-lookup"><span data-stu-id="4a859-143">In a terminal, run `ngrok http -host-header=rewrite 3978`.</span></span>
1. <span data-ttu-id="4a859-144">Kopieren Sie die HTTPS-URL in der Ausgabe (z. B. `https://468b9ab725e9.ngrok.io` ), da Teams HTTPS-Verbindungen erfordert.</span><span class="sxs-lookup"><span data-stu-id="4a859-144">Copy the HTTPS URL in the output (for example, `https://468b9ab725e9.ngrok.io`) since Teams requires HTTPS connections.</span></span>

<span data-ttu-id="4a859-145">Mit dieser URL kann Teams (für die HTTPS-Verbindungen erforderlich sind) zu dem Ort tunneln, an dem Sie Ihre App hosten ( `localhost` an Port 3978).</span><span class="sxs-lookup"><span data-stu-id="4a859-145">With this URL, Teams (which requires HTTPS connections) will be able tunnel to where you're hosting your app (`localhost` on port 3978).</span></span>

## <a name="4-configure-your-bot"></a><span data-ttu-id="4a859-146">4. Konfigurieren des Bots</span><span class="sxs-lookup"><span data-stu-id="4a859-146">4. Configure your bot</span></span>

<span data-ttu-id="4a859-147">Um einen Bot in Teams zu verwenden, müssen Sie ihn beim Azure Bot Service registrieren.</span><span class="sxs-lookup"><span data-stu-id="4a859-147">To use a bot in Teams, you must register it with the Azure Bot Service.</span></span> <span data-ttu-id="4a859-148">Zum Glück geschieht dies automatisch, wenn Sie Ihre App mithilfe des Teams Toolkits einrichten.</span><span class="sxs-lookup"><span data-stu-id="4a859-148">Lucky for you, this is done automatically when you set up your app using the Teams Toolkit.</span></span>

<span data-ttu-id="4a859-149">Sie müssen weiterhin eine Endpunktadresse angeben, um Benutzernachrichten (d. h. Anforderungen) zu empfangen und zu verarbeiten, die an den Bot gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="4a859-149">You still must specify an endpoint address to receive and process user messages (i.e., requests) sent to the bot.</span></span> <span data-ttu-id="4a859-150">In der Regel sieht die URL wie `https://HOST_URL/api/messages` aus.</span><span class="sxs-lookup"><span data-stu-id="4a859-150">Typically, the URL looks like `https://HOST_URL/api/messages`.</span></span> <span data-ttu-id="4a859-151">Sie können dies schnell im Toolkit konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="4a859-151">You can configure this quickly in the toolkit.</span></span>

1. Wählen Visual Studio Code auf der linken Aktivitätsleiste **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: aus, und wählen Sie Microsoft Teams Toolkit **öffnen aus.**
1. <span data-ttu-id="4a859-153">Wechseln Sie **zu Bots > vorhandenen Botregistrierungen,** und wählen Sie den Bot aus, den Sie während des Setups erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="4a859-153">Go to **Bots > Existing bot registrations** and select the bot you created during setup.</span></span>
1. <span data-ttu-id="4a859-154">Geben Sie im Feld **Bot-Endpunktadresse** die ngrok-URL (z. B. ) ein, in der Sie den Bot hosten, und `https://468b9ab725e9.ngrok.io` fügen Sie ihn `/api/messages` an.</span><span class="sxs-lookup"><span data-stu-id="4a859-154">In the **Bot endpoint address** field, enter the ngrok URL (for example, `https://468b9ab725e9.ngrok.io`) where you're hosting the bot and append `/api/messages` to it.</span></span><br/>
    :::image type="content" source="../assets/images/build-your-first-app/bot-config-endpoint-url.png" alt-text="Abbildung, in der Sie die URL des Botendpunkts im Teams Toolkit konfigurieren können.":::

<span data-ttu-id="4a859-156">Ihr Bot kann auf Nachrichten in Teams reagieren.</span><span class="sxs-lookup"><span data-stu-id="4a859-156">Your bot will be able to respond to messages in Teams.</span></span>

## <a name="5-build-and-run-your-app"></a><span data-ttu-id="4a859-157">5. Erstellen und Ausführen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="4a859-157">5. Build and run your app</span></span>

<span data-ttu-id="4a859-158">Sie haben eine URL zum Hosten Ihres Bots eingerichtet und für die Verarbeitung von Nachrichten konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="4a859-158">You've set up a URL to host your bot and configured it to handle messages.</span></span> <span data-ttu-id="4a859-159">Es ist an der Zeit, Ihre App in Betrieb zu halten.</span><span class="sxs-lookup"><span data-stu-id="4a859-159">It's time to get your app up and running.</span></span>

1. <span data-ttu-id="4a859-160">Wechseln Sie in einem Terminal zum Stammverzeichnis Ihres App-Projekts, und führen Sie `npm install` aus.</span><span class="sxs-lookup"><span data-stu-id="4a859-160">In a terminal, go to the root directory of your app project and run `npm install`.</span></span>
1. <span data-ttu-id="4a859-161">Führen Sie `npm start` aus.</span><span class="sxs-lookup"><span data-stu-id="4a859-161">Run `npm start`.</span></span>

<span data-ttu-id="4a859-162">Wenn dies erfolgreich ist, wird die folgende Meldung angezeigt, die angibt, dass Ihr Bot aktivitäten bei Ihrer `localhost` abhört:</span><span class="sxs-lookup"><span data-stu-id="4a859-162">If successful, you see the following message indicating your bot is listening for activity at your `localhost`:</span></span>

`Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-bot-in-teams"></a><span data-ttu-id="4a859-163">6. Querladen Des Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="4a859-163">6. Sideload your bot in Teams</span></span>

<span data-ttu-id="4a859-164">Wenn Ihr Bot ausgeführt wird, können Sie ihn in Teams installieren.</span><span class="sxs-lookup"><span data-stu-id="4a859-164">With your bot running, you can install it in Teams.</span></span>

> [!TIP]
> <span data-ttu-id="4a859-165">Wenn Sie eine Teams-App noch nicht nebeneinander geladen haben und Probleme auftreten, führen Sie diese [Anweisungen aus.](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams)</span><span class="sxs-lookup"><span data-stu-id="4a859-165">If you haven't sideloaded a Teams app before and run into issues, follow these [instructions](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams).</span></span>

1. <span data-ttu-id="4a859-166">Drücken Visual Studio Code die **F5-TASTE,** um einen Teams-Webclient zu starten.</span><span class="sxs-lookup"><span data-stu-id="4a859-166">In Visual Studio Code, press the **F5** key to launch a Teams web client.</span></span>
1. <span data-ttu-id="4a859-167">Wählen Sie im Dialogfeld App-Installation die Option **Für mich hinzufügen aus.**</span><span class="sxs-lookup"><span data-stu-id="4a859-167">In the app install dialog, select **Add for me**.</span></span> <span data-ttu-id="4a859-168">(Sie könnten den Bot zu einem Kanal oder Chat hinzufügen, aber es ist für andere weniger aufdringlich, einen Bot in einem 1:1-Chat zu testen.)</span><span class="sxs-lookup"><span data-stu-id="4a859-168">(You could add the bot to a channel or chat, but it's less intrusive to others to test a bot in a one-on-one chat.)</span></span>

## <a name="7-test-your-bot"></a><span data-ttu-id="4a859-169">7. Testen Des Bots</span><span class="sxs-lookup"><span data-stu-id="4a859-169">7. Test your bot</span></span>

<span data-ttu-id="4a859-170">Jetzt für den lustigen Teil: Sagen wir "Hello" zu Ihrem Bot.</span><span class="sxs-lookup"><span data-stu-id="4a859-170">Now for the fun part: Let's say "Hello" to your bot.</span></span>

1. <span data-ttu-id="4a859-171">Senden Sie im Feld Verfassen eine `Hello` Nachricht.</span><span class="sxs-lookup"><span data-stu-id="4a859-171">In the compose box, send a `Hello` message.</span></span>

<span data-ttu-id="4a859-172">Ihr Bot antwortet mit einer Nachricht wie der folgenden.</span><span class="sxs-lookup"><span data-stu-id="4a859-172">Your bot replies with something like the following message.</span></span>

:::image type="content" source="../assets/images/build-your-first-app/contoso-chatbot.png" alt-text="Ein Screenshot, auf dem ein Benutzer &quot;Hello&quot; zu einem Teams-Bot sagt und eine Antwort erhalten.":::

## <a name="well-done"></a><span data-ttu-id="4a859-174">Gut gemacht</span><span class="sxs-lookup"><span data-stu-id="4a859-174">Well done</span></span>

<span data-ttu-id="4a859-175">Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="4a859-175">Congratulations!</span></span> <span data-ttu-id="4a859-176">Sie verfügen über einen einfachen Teams-Bot, der mit Benutzern 1:1 oder in Gruppeneinstellungen (Kanäle und Chats) kommunizieren kann.</span><span class="sxs-lookup"><span data-stu-id="4a859-176">You have a basic Teams bot that can communicate with users one-on-one or in group settings (channels and chats).</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="4a859-177">Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="4a859-177">Troubleshooting</span></span>

<span data-ttu-id="4a859-178">Die folgenden Informationen können hilfreich sein, wenn Beim Abschließen dieses Lernprogramms Probleme auftreten.</span><span class="sxs-lookup"><span data-stu-id="4a859-178">The following information may help if you had issues completing this tutorial.</span></span>

### <a name="bot-isnt-connected-to-teams"></a><span data-ttu-id="4a859-179">Bot ist nicht mit Teams verbunden</span><span class="sxs-lookup"><span data-stu-id="4a859-179">Bot isn't connected to Teams</span></span>

<span data-ttu-id="4a859-180">Wenn Sie Ihre App installiert haben, der Bot jedoch nicht funktioniert, stellen Sie sicher, dass der Bot mit dem Teams-Kanal des [Azure Bot Service verbunden *ist.*](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="4a859-180">If you installed your app but the bot isn't working, make sure the bot is [connected to the Azure Bot Service's Teams *channel*](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true).</span></span>

<span data-ttu-id="4a859-181">Es ist wichtig zu wissen, dass dies nicht mit einem Kanal in Teams identisch ist.</span><span class="sxs-lookup"><span data-stu-id="4a859-181">It's important to understand that this isn't the same as a channel in Teams.</span></span> <span data-ttu-id="4a859-182">In diesem Fall verbindet der Azure Bot Service Ihren Bot mit Teams oder einer anderen unterstützten Microsoft- oder [Drittanbieter-Kommunikations-App.](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="4a859-182">In this case, a channel is how the Azure Bot Service connects your bot to Teams or another [supported Microsoft or third-party communications app](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span>

## <a name="learn-more"></a><span data-ttu-id="4a859-183">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="4a859-183">Learn more</span></span>

* [<span data-ttu-id="4a859-184">Sehen Sie sich an, welche anderen Teams Bots mit einem unserer Beispiele arbeiten können</span><span class="sxs-lookup"><span data-stu-id="4a859-184">See what else Teams bots can do with one of our samples</span></span>](https://github.com/microsoft/BotBuilder-Samples#teams-samples)
* [<span data-ttu-id="4a859-185">Grundlegende Informationen zu Bot-Unterhaltungen</span><span class="sxs-lookup"><span data-stu-id="4a859-185">Bot conversation basics</span></span>](../bots/how-to/conversations/conversation-basics.md)
* <span data-ttu-id="4a859-186">Befolgen Sie [unsere Entwurfsrichtlinien,](../bots/design/bots.md) und erstellen Sie mit [produktionsbereiten](../concepts/design/design-teams-app-ui-templates.md) Benutzeroberflächenvorlagen, um eine nahtlose Oberfläche zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="4a859-186">Follow our [design guidelines](../bots/design/bots.md) and build with [production-ready UI templates](../concepts/design/design-teams-app-ui-templates.md) to create a seamless experience.</span></span>
* [<span data-ttu-id="4a859-187">Bot-Authentifizierung in Teams</span><span class="sxs-lookup"><span data-stu-id="4a859-187">Bot authentication in Teams</span></span>](../bots/how-to/authentication/auth-flow-bot.md)
* [<span data-ttu-id="4a859-188">Microsoft Bot Framework</span><span class="sxs-lookup"><span data-stu-id="4a859-188">Microsoft Bot Framework</span></span>](https://dev.botframework.com/)
* [<span data-ttu-id="4a859-189">Erstellen eines Bots ohne Toolkit</span><span class="sxs-lookup"><span data-stu-id="4a859-189">Create a bot without the toolkit</span></span>](../resources/bot-v3/bots-create.md)
