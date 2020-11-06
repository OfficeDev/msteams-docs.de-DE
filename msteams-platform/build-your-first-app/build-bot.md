---
title: Erste Schritte – Erstellen eines bot
author: heath-hamilton
description: Erstellen Sie schnell einen Microsoft Teams-bot mithilfe des Microsoft Teams-Toolkits.
ms.author: lajanuar
ms.date: 11/04/2020
ms.topic: tutorial
ms.openlocfilehash: 1229064ac6b7aab73c50048f0764c6a2353ab54a
ms.sourcegitcommit: 99c35de7e2c604bd8bce392242c2c2fa709cd50b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2020
ms.locfileid: "48931739"
---
# <a name="build-a-bot-for-microsoft-teams"></a><span data-ttu-id="9eb06-103">Erstellen eines bot für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="9eb06-103">Build a bot for Microsoft Teams</span></span>

<span data-ttu-id="9eb06-104">In diesem Lernprogramm erstellen Sie eine einfache *bot* -app.</span><span class="sxs-lookup"><span data-stu-id="9eb06-104">You'll build a basic *bot* app in this tutorial.</span></span> <span data-ttu-id="9eb06-105">Ein bot fungiert als Vermittler zwischen Microsoft Teams-Benutzern und Ihrem Webdienst.</span><span class="sxs-lookup"><span data-stu-id="9eb06-105">A bot acts as an intermediary between Teams users and your web service.</span></span> <span data-ttu-id="9eb06-106">Personen können mit einem bot chatten, um schnell Informationen zu erhalten oder Workflows und Aufgaben zu initiieren, die von Ihrem Dienst ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="9eb06-106">People can chat with a bot to quickly get information or initiate workflows and tasks performed by your service.</span></span>

## <a name="your-assignment"></a><span data-ttu-id="9eb06-107">Ihre Zuordnung</span><span class="sxs-lookup"><span data-stu-id="9eb06-107">Your assignment</span></span>

<span data-ttu-id="9eb06-108">Ihr Arbeitsplatz hat eine Teams-App erstellt, die [Registerkarten](../build-your-first-app/build-personal-tab.md) verwendet, um wichtige Kontaktinformationen zu Surface.</span><span class="sxs-lookup"><span data-stu-id="9eb06-108">Your workplace created a Teams app that uses [tabs](../build-your-first-app/build-personal-tab.md) to surface important contact information.</span></span> <span data-ttu-id="9eb06-109">Kollegen haben beispielsweise schnellen Zugriff auf die Telefonnummer des Helpdesks.</span><span class="sxs-lookup"><span data-stu-id="9eb06-109">For example, colleagues have quick access to the help desk phone number.</span></span> <span data-ttu-id="9eb06-110">Aber statt aufzurufen, was wäre, wenn Personen mit einem Chatbot Kontakt zum Helpdesk aufnehmen könnten?</span><span class="sxs-lookup"><span data-stu-id="9eb06-110">But instead of calling, what if people could contact the help desk using a chatbot?</span></span> <span data-ttu-id="9eb06-111">Ihr Chef bittet Sie, sich anzusehen, wie schnell Sie einen einfachen Unterhaltungs bot in Microsoft Teams in Betrieb nehmen können.</span><span class="sxs-lookup"><span data-stu-id="9eb06-111">Your boss asks you to look at how quickly you can get a basic conversational bot up and running in Teams.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="9eb06-112">Was Sie lernen</span><span class="sxs-lookup"><span data-stu-id="9eb06-112">What you'll learn</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="9eb06-113">Erstellen eines App-Projekts und bot mithilfe des Microsoft Teams-Toolkits für Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="9eb06-113">Create an app project and bot using the Microsoft Teams Toolkit for Visual Studio Code</span></span>
> * <span data-ttu-id="9eb06-114">Identifizieren der für Bots relevanten App-Konfigurationen und Gerüste</span><span class="sxs-lookup"><span data-stu-id="9eb06-114">Identify some of the app configurations and scaffolding relevant to bots</span></span>
> * <span data-ttu-id="9eb06-115">Lokal Hosten einer APP</span><span class="sxs-lookup"><span data-stu-id="9eb06-115">Host an app locally</span></span>
> * <span data-ttu-id="9eb06-116">Konfigurieren eines bot für Teams</span><span class="sxs-lookup"><span data-stu-id="9eb06-116">Configure a bot for Teams</span></span>
> * <span data-ttu-id="9eb06-117">Querladen und Testen eines bot in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="9eb06-117">Sideload and test a bot in Teams</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="9eb06-118">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="9eb06-118">Before you begin</span></span>

<span data-ttu-id="9eb06-119">Wenn Sie noch nicht vorhanden sind, stellen Sie sicher, dass Sie [die Entwicklungsvoraussetzungen für Teams kennen und installieren](build-first-app-overview.md#get-prerequisites).</span><span class="sxs-lookup"><span data-stu-id="9eb06-119">If you haven't yet, make sure you [understand and install the Teams development prerequisites](build-first-app-overview.md#get-prerequisites).</span></span>

## <a name="1-create-your-app-project"></a><span data-ttu-id="9eb06-120">1. Erstellen des App-Projekts</span><span class="sxs-lookup"><span data-stu-id="9eb06-120">1. Create your app project</span></span>

<span data-ttu-id="9eb06-121">Das Microsoft Teams-Toolkit hilft Ihnen, die folgenden Komponenten für Ihre APP einzurichten:</span><span class="sxs-lookup"><span data-stu-id="9eb06-121">The Microsoft Teams Toolkit helps you set up the following components for your app:</span></span>

* <span data-ttu-id="9eb06-122">**App-Konfigurationen und** für Bots relevante Gerüste</span><span class="sxs-lookup"><span data-stu-id="9eb06-122">**App configurations and scaffolding** relevant to bots</span></span>
* <span data-ttu-id="9eb06-123">**Bot** , der automatisch beim Microsoft Azure bot-Dienst registriert wird</span><span class="sxs-lookup"><span data-stu-id="9eb06-123">**Bot** that's automatically registered with the Microsoft Azure Bot Service</span></span>

> [!TIP]
> <span data-ttu-id="9eb06-124">Wenn Sie noch kein Teams-App-Projekt erstellt haben, ist es möglicherweise hilfreich, [diese Anweisungen](../build-your-first-app/build-and-run.md) zu befolgen, mit denen Projekte detaillierter erläutert werden.</span><span class="sxs-lookup"><span data-stu-id="9eb06-124">If you haven't created a Teams app project before, you might find it helpful to follow [these instructions](../build-your-first-app/build-and-run.md) that explain projects in more detail.</span></span>

1. Wählen Sie in Visual Studio Code **Microsoft Teams** in :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: der linken Aktivitäts Leiste aus, und wählen Sie **neue Teams-app erstellen** aus.
1. <span data-ttu-id="9eb06-126">Wenn Sie dazu aufgefordert werden, melden Sie sich mit Ihrem Microsoft 365-entwicklungskonto an.</span><span class="sxs-lookup"><span data-stu-id="9eb06-126">When prompted, sign in with your Microsoft 365 development account.</span></span>
1. <span data-ttu-id="9eb06-127">Wählen Sie auf dem Bildschirm **Funktionen hinzufügen** die Option **bot** und dann **weiter** aus.</span><span class="sxs-lookup"><span data-stu-id="9eb06-127">On the **Add capabilities** screen, select **Bot** then **Next**.</span></span>
1. <span data-ttu-id="9eb06-128">Geben Sie einen Namen für Ihre Teams-App ein.</span><span class="sxs-lookup"><span data-stu-id="9eb06-128">Enter a name for your Teams app.</span></span> <span data-ttu-id="9eb06-129">(Dies ist der Standardname für Ihre APP und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.)</span><span class="sxs-lookup"><span data-stu-id="9eb06-129">(This is the default name for your app and also the name of the app project directory on your local machine.)</span></span>
1. <span data-ttu-id="9eb06-130">Wechseln Sie zu **configure bot** , und wählen Sie **Create a New bot** und dann **Create bot Registration** aus.</span><span class="sxs-lookup"><span data-stu-id="9eb06-130">Go to **Configure bot** and select **Create a new Bot** then **Create Bot Registration**.</span></span> <span data-ttu-id="9eb06-131">Wenn die Methode erfolgreich verläuft, wird Ihr neuer bot einen **registrierten** Status haben.</span><span class="sxs-lookup"><span data-stu-id="9eb06-131">If successful, your new bot will have a **Registered** status.</span></span>
1. <span data-ttu-id="9eb06-132">Klicken Sie unten auf dem Bildschirm auf **Fertig stellen** , und wählen Sie einen Speicherort aus, um das Projekt zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="9eb06-132">Select **Finish** at the bottom of the screen and choose a location to create your project.</span></span>

## <a name="2-identify-relevant-app-project-components"></a><span data-ttu-id="9eb06-133">2. Identifizieren der relevanten App-Projektkomponenten</span><span class="sxs-lookup"><span data-stu-id="9eb06-133">2. Identify relevant app project components</span></span>

<span data-ttu-id="9eb06-134">Viele der APP-Konfigurationen und Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Teams-Toolkit erstellen.</span><span class="sxs-lookup"><span data-stu-id="9eb06-134">Much of the app configurations and scaffolding are set up automatically when you create your project with the Teams Toolkit.</span></span> <span data-ttu-id="9eb06-135">Lassen Sie uns die Hauptkomponenten zum Erstellen eines bot betrachten.</span><span class="sxs-lookup"><span data-stu-id="9eb06-135">Let's look at the main components for building a bot.</span></span>

### <a name="app-configurations"></a><span data-ttu-id="9eb06-136">App-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="9eb06-136">App configurations</span></span>

<span data-ttu-id="9eb06-137">Um Ihre bot-Konfigurationen anzuzeigen oder zu aktualisieren, wählen Sie **App Studio** im Toolkit aus, und wechseln Sie zu **Bots**.</span><span class="sxs-lookup"><span data-stu-id="9eb06-137">To view or update your bot's configurations, select **App Studio** in the toolkit and go to **Bots**.</span></span>

### <a name="app-scaffolding"></a><span data-ttu-id="9eb06-138">App-Gerüste</span><span class="sxs-lookup"><span data-stu-id="9eb06-138">App scaffolding</span></span>

<span data-ttu-id="9eb06-139">Das App-Gerüst enthält eine `botActivityHandler.js` Datei, die sich im Stammverzeichnis des Projekts befindet, um zu behandeln, wie Ihr Bot Aktivitäten in Microsoft Teams verarbeitet (beispielsweise, wie der bot auf bestimmte Nachrichten wie "Hello" reagiert).</span><span class="sxs-lookup"><span data-stu-id="9eb06-139">The app scaffolding provides a `botActivityHandler.js` file, located in the root directory of your project, for handling how your bot processes activities in Teams (for example, how the bot responds to specific messages such as "Hello").</span></span>

## <a name="3-set-up-a-secure-tunnel-to-your-app"></a><span data-ttu-id="9eb06-140">3. Einrichten eines sicheren Tunnels für Ihre APP</span><span class="sxs-lookup"><span data-stu-id="9eb06-140">3. Set up a secure tunnel to your app</span></span>

<span data-ttu-id="9eb06-141">Zu Testzwecken hosten wir Ihre APP auf einem lokalen Webserver (Port 3978).</span><span class="sxs-lookup"><span data-stu-id="9eb06-141">For testing purposes, let's host your app on a local web server (port 3978).</span></span>

1. <span data-ttu-id="9eb06-142">Wenn Sie noch nicht vorhanden sind, installieren Sie [ngrok](https://ngrok.com/download).</span><span class="sxs-lookup"><span data-stu-id="9eb06-142">If you haven't already, install [ngrok](https://ngrok.com/download).</span></span>
1. <span data-ttu-id="9eb06-143">Führen Sie in einem Terminal aus `ngrok http -host-header=rewrite 3978` .</span><span class="sxs-lookup"><span data-stu-id="9eb06-143">In a terminal, run `ngrok http -host-header=rewrite 3978`.</span></span>
1. <span data-ttu-id="9eb06-144">Kopieren Sie die HTTPS-URL in der Ausgabe (beispielsweise `https://468b9ab725e9.ngrok.io` ), da für Teams HTTPS-Verbindungen erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="9eb06-144">Copy the HTTPS URL in the output (for example, `https://468b9ab725e9.ngrok.io`) since Teams requires HTTPS connections.</span></span>

<span data-ttu-id="9eb06-145">Mit dieser URL können Teams (für die HTTPS-Verbindungen erforderlich sind) in der Lage sein, zu dem Ort zu gelangen, an dem Sie Ihre APP hosten ( `localhost` auf Port 3978).</span><span class="sxs-lookup"><span data-stu-id="9eb06-145">With this URL, Teams (which requires HTTPS connections) will be able tunnel to where you're hosting your app (`localhost` on port 3978).</span></span>

## <a name="4-configure-your-bot"></a><span data-ttu-id="9eb06-146">4. Konfigurieren Ihres bot</span><span class="sxs-lookup"><span data-stu-id="9eb06-146">4. Configure your bot</span></span>

<span data-ttu-id="9eb06-147">Um einen bot in Microsoft Teams zu verwenden, müssen Sie ihn bei dem Azure bot-Dienst registrieren.</span><span class="sxs-lookup"><span data-stu-id="9eb06-147">To use a bot in Teams, you must register it with the Azure Bot Service.</span></span> <span data-ttu-id="9eb06-148">Glücklicherweise wird dies automatisch durchgeführt, wenn Sie Ihre APP mit dem Teams-Toolkit einrichten.</span><span class="sxs-lookup"><span data-stu-id="9eb06-148">Lucky for you, this is done automatically when you set up your app using the Teams Toolkit.</span></span>

<span data-ttu-id="9eb06-149">Sie müssen immer noch eine Endpunktadresse angeben, um Benutzer Nachrichten (d. h., Anforderungen) zu empfangen und zu verarbeiten, die an den bot gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="9eb06-149">You still must specify an endpoint address to receive and process user messages (i.e., requests) sent to the bot.</span></span> <span data-ttu-id="9eb06-150">Normalerweise sieht die URL wie aus `https://HOST_URL/api/messages` .</span><span class="sxs-lookup"><span data-stu-id="9eb06-150">Typically, the URL looks like `https://HOST_URL/api/messages`.</span></span> <span data-ttu-id="9eb06-151">Sie können diese schnell im Toolkit konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="9eb06-151">You can configure this quickly in the toolkit.</span></span>

1. Wählen Sie in Visual Studio Code **Microsoft Teams** in :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: der linken Aktivitäts Leiste aus, und wählen Sie **Microsoft Teams Toolkit öffnen** aus.
1. <span data-ttu-id="9eb06-153">Wechseln Sie zu **Bots > vorhandene bot-Registrierungen** , und wählen Sie den bot aus, den Sie während des Setups erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="9eb06-153">Go to **Bots > Existing bot registrations** and select the bot you created during setup.</span></span>
1. <span data-ttu-id="9eb06-154">Geben Sie im Feld **bot-Endpunktadresse** die ngrok-URL (beispielsweise) ein, in der `https://468b9ab725e9.ngrok.io` Sie den bot hosten und `/api/messages` an ihn anfügen.</span><span class="sxs-lookup"><span data-stu-id="9eb06-154">In the **Bot endpoint address** field, enter the ngrok URL (for example, `https://468b9ab725e9.ngrok.io`) where you're hosting the bot and append `/api/messages` to it.</span></span><br/>
    :::image type="content" source="../assets/images/build-your-first-app/bot-config-endpoint-url.png" alt-text="Abbildung zeigt, wo Sie die bot-Endpunkt-URL im Teams-Toolkit konfigurieren können.":::

<span data-ttu-id="9eb06-156">Ihr bot wird in der Lage sein, auf Nachrichten in Microsoft Teams zu antworten.</span><span class="sxs-lookup"><span data-stu-id="9eb06-156">Your bot will be able to respond to messages in Teams.</span></span>

## <a name="5-build-and-run-your-app"></a><span data-ttu-id="9eb06-157">5. erstellen und Ausführen der APP</span><span class="sxs-lookup"><span data-stu-id="9eb06-157">5. Build and run your app</span></span>

<span data-ttu-id="9eb06-158">Sie haben eine URL zum Hosten Ihres bot eingerichtet und für die Verarbeitung von Nachrichten konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="9eb06-158">You've set up a URL to host your bot and configured it to handle messages.</span></span> <span data-ttu-id="9eb06-159">Es ist an der Zeit, Ihre APP in Betrieb zu nehmen.</span><span class="sxs-lookup"><span data-stu-id="9eb06-159">It's time to get your app up and running.</span></span>

1. <span data-ttu-id="9eb06-160">Wechseln Sie in einem Terminal zum Stammverzeichnis des App-Projekts, und führen Sie es aus `npm install` .</span><span class="sxs-lookup"><span data-stu-id="9eb06-160">In a terminal, go to the root directory of your app project and run `npm install`.</span></span>
1. <span data-ttu-id="9eb06-161">Ausführen `npm start` .</span><span class="sxs-lookup"><span data-stu-id="9eb06-161">Run `npm start`.</span></span>

<span data-ttu-id="9eb06-162">Wenn die Aktion erfolgreich verläuft, wird die folgende Meldung angezeigt, die besagt, dass Ihr bot ihre Aktivität überwacht `localhost` :</span><span class="sxs-lookup"><span data-stu-id="9eb06-162">If successful, you see the following message indicating your bot is listening for activity at your `localhost`:</span></span>

`Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-bot-in-teams"></a><span data-ttu-id="9eb06-163">6. querladen Ihres bot in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="9eb06-163">6. Sideload your bot in Teams</span></span>

<span data-ttu-id="9eb06-164">Wenn Ihr bot läuft, können Sie ihn in Microsoft Teams installieren.</span><span class="sxs-lookup"><span data-stu-id="9eb06-164">With your bot running, you can install it in Teams.</span></span>

> [!TIP]
> <span data-ttu-id="9eb06-165">Wenn Sie noch keine Teams-App quer geladene haben und Probleme haben, führen Sie die folgenden [Schritte](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams)aus.</span><span class="sxs-lookup"><span data-stu-id="9eb06-165">If you haven't sideloaded a Teams app before and run into issues, follow these [instructions](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams).</span></span>

1. <span data-ttu-id="9eb06-166">Drücken Sie in Visual Studio Code die **F5** -Taste, um einen Microsoft Teams-WebClient zu starten.</span><span class="sxs-lookup"><span data-stu-id="9eb06-166">In Visual Studio Code, press the **F5** key to launch a Teams web client.</span></span>
1. <span data-ttu-id="9eb06-167">Wählen Sie im Dialogfeld App-Installation die Option **für mich hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="9eb06-167">In the app install dialog, select **Add for me**.</span></span> <span data-ttu-id="9eb06-168">(Sie können den bot einem Kanal oder Chat hinzufügen, aber er ist für andere nicht störend, um einen bot in einem Einzelchat zu testen.)</span><span class="sxs-lookup"><span data-stu-id="9eb06-168">(You could add the bot to a channel or chat, but it's less intrusive to others to test a bot in a one-on-one chat.)</span></span>

## <a name="7-test-your-bot"></a><span data-ttu-id="9eb06-169">7. Testen Sie Ihren bot</span><span class="sxs-lookup"><span data-stu-id="9eb06-169">7. Test your bot</span></span>

<span data-ttu-id="9eb06-170">Nun zum spaßigen Teil: sagen wir "Hallo" zu Ihrem bot.</span><span class="sxs-lookup"><span data-stu-id="9eb06-170">Now for the fun part: Let's say "Hello" to your bot.</span></span>

1. <span data-ttu-id="9eb06-171">Senden Sie im Feld Verfassen eine `Hello` Nachricht.</span><span class="sxs-lookup"><span data-stu-id="9eb06-171">In the compose box, send a `Hello` message.</span></span>

<span data-ttu-id="9eb06-172">Ihr bot antwortet mit so etwas wie der folgenden Nachricht.</span><span class="sxs-lookup"><span data-stu-id="9eb06-172">Your bot replies with something like the following message.</span></span>

:::image type="content" source="../assets/images/build-your-first-app/contoso-chatbot.png" alt-text="Ein Screenshot mit einem Benutzer, der _OL_QUOTE_PLACEHOLDER_Hello_OL_QUOTE_PLACEHOLDER_ zu einem Team-bot und einer Antwort ruft.":::

## <a name="well-done"></a><span data-ttu-id="9eb06-174">Gut gemacht</span><span class="sxs-lookup"><span data-stu-id="9eb06-174">Well done</span></span>

<span data-ttu-id="9eb06-175">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="9eb06-175">Congratulations!</span></span> <span data-ttu-id="9eb06-176">Sie haben einen einfachen Teams-bot, der mit Benutzern einzeln oder in Gruppeneinstellungen (Kanäle und Chats) kommunizieren kann.</span><span class="sxs-lookup"><span data-stu-id="9eb06-176">You have a basic Teams bot that can communicate with users one-on-one or in group settings (channels and chats).</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="9eb06-177">Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="9eb06-177">Troubleshooting</span></span>

<span data-ttu-id="9eb06-178">Die folgenden Informationen können hilfreich sein, wenn beim Abschluss dieses Lernprogramms Probleme aufgetreten sind.</span><span class="sxs-lookup"><span data-stu-id="9eb06-178">The following information may help if you had issues completing this tutorial.</span></span>

### <a name="bot-isnt-connected-to-teams"></a><span data-ttu-id="9eb06-179">Bot ist nicht mit Microsoft Teams verbunden</span><span class="sxs-lookup"><span data-stu-id="9eb06-179">Bot isn't connected to Teams</span></span>

<span data-ttu-id="9eb06-180">Wenn Sie Ihre APP installiert haben, aber der bot nicht funktioniert, stellen Sie sicher, dass der bot [mit dem Microsoft Teams- *Kanal* des Azure bot-Diensts verbunden](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true)ist.</span><span class="sxs-lookup"><span data-stu-id="9eb06-180">If you installed your app but the bot isn't working, make sure the bot is [connected to the Azure Bot Service's Teams *channel*](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true).</span></span>

<span data-ttu-id="9eb06-181">Es ist wichtig zu verstehen, dass dies nicht mit einem Kanal in Microsoft Teams identisch ist.</span><span class="sxs-lookup"><span data-stu-id="9eb06-181">It's important to understand that this isn't the same as a channel in Teams.</span></span> <span data-ttu-id="9eb06-182">In diesem Fall stellt ein Kanal dar, wie der Azure bot-Dienst Ihren bot mit Teams oder einer anderen [unterstützten Microsoft-oder Drittanbieter-Kommunikations-App](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)verbindet.</span><span class="sxs-lookup"><span data-stu-id="9eb06-182">In this case, a channel is how the Azure Bot Service connects your bot to Teams or another [supported Microsoft or third-party communications app](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span>

## <a name="learn-more"></a><span data-ttu-id="9eb06-183">Mehr erfahren</span><span class="sxs-lookup"><span data-stu-id="9eb06-183">Learn more</span></span>

* [<span data-ttu-id="9eb06-184">Sehen Sie sich an, was andere Teams-Bots mit einem unserer Beispiele tun können</span><span class="sxs-lookup"><span data-stu-id="9eb06-184">See what else Teams bots can do with one of our samples</span></span>](https://github.com/microsoft/BotBuilder-Samples#teams-samples)
* [<span data-ttu-id="9eb06-185">Grundlegende Informationen zu Bot-Unterhaltungen</span><span class="sxs-lookup"><span data-stu-id="9eb06-185">Bot conversation basics</span></span>](../bots/how-to/conversations/conversation-basics.md)
* [<span data-ttu-id="9eb06-186">Bot-Authentifizierung in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="9eb06-186">Bot authentication in Teams</span></span>](../bots/how-to/authentication/auth-flow-bot.md)
* [<span data-ttu-id="9eb06-187">Microsoft bot-Framework</span><span class="sxs-lookup"><span data-stu-id="9eb06-187">Microsoft Bot Framework</span></span>](https://dev.botframework.com/)
* [<span data-ttu-id="9eb06-188">Erstellen eines bot ohne Toolkit</span><span class="sxs-lookup"><span data-stu-id="9eb06-188">Create a bot without the toolkit</span></span>](../bots/how-to/create-a-bot-for-teams.md)
