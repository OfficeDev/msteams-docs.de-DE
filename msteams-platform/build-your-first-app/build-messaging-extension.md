---
title: Erste Schritte - Erstellen einer Messagingerweiterung
author: girliemac
description: Erstellen Sie schnell eine Microsoft Teams Messaging-Erweiterung mit dem Microsoft Teams Toolkit.
ms.author: timura
ms.date: 03/25/2021
ms.topic: tutorial
ms.openlocfilehash: c120a5b5d878c549cde008c3e1ccc71743a4e24f
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566061"
---
# <a name="build-your-first-messaging-extension-for-microsoft-teams"></a><span data-ttu-id="59caf-103">Erstellen Sie Ihre erste Messagingerweiterung für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="59caf-103">Build your first messaging extension for Microsoft Teams</span></span>

<span data-ttu-id="59caf-104">Es gibt zwei Arten von Teams *Messaging-Erweiterungen:* [Suchbefehle](../messaging-extensions/how-to/search-commands/define-search-command.md) und [Aktionsbefehle](../messaging-extensions/how-to/action-commands/define-action-command.md).</span><span class="sxs-lookup"><span data-stu-id="59caf-104">There are two types of Teams *messaging extensions*: [Search commands](../messaging-extensions/how-to/search-commands/define-search-command.md) and [action commands](../messaging-extensions/how-to/action-commands/define-action-command.md).</span></span>

<span data-ttu-id="59caf-105">In diesem Tutorial lernen Sie an, einen *Suchbefehl* (auch als *suchbasierte Messagingerweiterung* bezeichnet) zu erstellen, der eine Verknüpfung zum Suchen externer Inhalte und zum Freigeben von externen Inhalten und deren Freigabe in Teams darstellt.</span><span class="sxs-lookup"><span data-stu-id="59caf-105">This tutorial teaches you to create a *search command* (also known as a *search-based messaging extension*), which is a shortcut for finding external content and sharing it in Teams.</span></span> <span data-ttu-id="59caf-106">Benutzer können über das Teams verfassen oder Befehlsfeld auf Suchbefehle zugreifen.</span><span class="sxs-lookup"><span data-stu-id="59caf-106">Users can access search commands from the Teams compose or command box.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="59caf-107">Was Sie lernen werden</span><span class="sxs-lookup"><span data-stu-id="59caf-107">What you'll learn</span></span>

* <span data-ttu-id="59caf-108">Erstellen Sie einen App-Projekt- und Messagingerweiterungsbot mit dem Microsoft Teams Toolkit für Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="59caf-108">Create an app project and messaging extension bot using the Microsoft Teams Toolkit for Visual Studio Code.</span></span>
* <span data-ttu-id="59caf-109">Verstehen Sie die App-Konfigurationen und das Gerüst, das für Messaging-Erweiterungen relevant ist.</span><span class="sxs-lookup"><span data-stu-id="59caf-109">Understand the app configurations and the scaffolding relevant to messaging extensions.</span></span>
* <span data-ttu-id="59caf-110">Hosten Sie eine App lokal.</span><span class="sxs-lookup"><span data-stu-id="59caf-110">Host an app locally.</span></span>
* <span data-ttu-id="59caf-111">Konfigurieren Sie den Bot für Ihre Messaging-Erweiterung.</span><span class="sxs-lookup"><span data-stu-id="59caf-111">Configure the bot for your messaging extension.</span></span>
* <span data-ttu-id="59caf-112">Sideload und testen Sie eine Messagingerweiterung in Teams.</span><span class="sxs-lookup"><span data-stu-id="59caf-112">Sideload and test a messaging extension in Teams.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="59caf-113">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="59caf-113">Prerequisites</span></span>

<span data-ttu-id="59caf-114">Stellen Sie sicher, dass Sie verstehen, wie Sie eine einfache Teams-App einrichten und erstellen.</span><span class="sxs-lookup"><span data-stu-id="59caf-114">Make sure that you understand how to set up and build a simple Teams app.</span></span> <span data-ttu-id="59caf-115">Weitere Informationen finden Sie [unter Erstellen Ihrer ersten Microsoft Teams "Hello, World!"-App](../build-your-first-app/build-and-run.md).</span><span class="sxs-lookup"><span data-stu-id="59caf-115">For more information, see [create your first Microsoft Teams "Hello, World!" app](../build-your-first-app/build-and-run.md).</span></span>

## <a name="1-create-your-app-project"></a><span data-ttu-id="59caf-116">1. Erstellen Sie Ihr App-Projekt</span><span class="sxs-lookup"><span data-stu-id="59caf-116">1. Create your app project</span></span>

<span data-ttu-id="59caf-117">Das Microsoft Teams Toolkit unterstützt Sie beim Einrichten der folgenden Komponenten für Ihre Messagingerweiterung:</span><span class="sxs-lookup"><span data-stu-id="59caf-117">The Microsoft Teams Toolkit helps you set up the following components for your messaging extension:</span></span>

* <span data-ttu-id="59caf-118">**App-Konfigurationen und Gerüste,** die für Messaging-Erweiterungen relevant sind.</span><span class="sxs-lookup"><span data-stu-id="59caf-118">**App configurations and scaffolding** relevant to messaging extensions.</span></span>
* <span data-ttu-id="59caf-119">**Bot** für Ihre Messaging-Erweiterung, die automatisch beim Microsoft Azure Bot Service registriert ist.</span><span class="sxs-lookup"><span data-stu-id="59caf-119">**Bot** for your messaging extension that's automatically registered with the Microsoft Azure Bot Service.</span></span>

<span data-ttu-id="59caf-120">**So erstellen Sie Ihr App-Projekt**</span><span class="sxs-lookup"><span data-stu-id="59caf-120">**To create your app project**</span></span>

1. Wählen Sie in Visual Studio Code **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: auf der linken Aktivitätsleiste aus, und wählen Sie **eine neue Teams-App erstellen** aus.
1. <span data-ttu-id="59caf-122">Wenn Sie dazu aufgefordert werden, melden Sie sich mit Ihrem Microsoft 365-Entwicklungskonto an.</span><span class="sxs-lookup"><span data-stu-id="59caf-122">When prompted, sign in with your Microsoft 365 development account.</span></span>
1. <span data-ttu-id="59caf-123">Klicken **Sie** auf dem Bildschirm Projekt auswählen auf **Messaging Extensions**  >  **Search** auf **JS (JavaScript)**.</span><span class="sxs-lookup"><span data-stu-id="59caf-123">On the **Select project** screen, at **Messaging Extensions** > **Search**, click **JS (JavaScript)**.</span></span> 
1. <span data-ttu-id="59caf-124">Geben Sie einen Namen für Ihre Teams App ein.</span><span class="sxs-lookup"><span data-stu-id="59caf-124">Enter a name for your Teams app.</span></span> <span data-ttu-id="59caf-125">Dies ist der Standardname für Ihre App und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.</span><span class="sxs-lookup"><span data-stu-id="59caf-125">This is the default name for your app and also the name of the app project directory on your local machine.</span></span>
1. <span data-ttu-id="59caf-126">Wählen Sie **Einen neuen Bot** erstellen und klicken Sie dann auf Die Schaltfläche **Bot-Registrierung erstellen.**</span><span class="sxs-lookup"><span data-stu-id="59caf-126">Select **Create a new Bot** then click **Create Bot Registration** button.</span></span> <span data-ttu-id="59caf-127">Wenn der Erfolg gelingt, hat Ihr neuer Bot einen *registrierten* Status.</span><span class="sxs-lookup"><span data-stu-id="59caf-127">If successful, your new bot will have a *Registered* status.</span></span> <span data-ttu-id="59caf-128">Jetzt wird Ihr Bot automatisch beim Microsoft Azure-Bot-Service registriert.</span><span class="sxs-lookup"><span data-stu-id="59caf-128">Now your bot is automatically registered with the Microsoft Azure Bot Service.</span></span> 
1. <span data-ttu-id="59caf-129">Wählen Sie am unteren Bildschirmrand **fertig** aus, um das Projekt zu konfigurieren und das Projekt auf dem lokalen Computer zu speichern.</span><span class="sxs-lookup"><span data-stu-id="59caf-129">Select **Finish** at the bottom of the screen to configure your project and save your project on your local machine.</span></span>

## <a name="2-understand-your-app-project-components"></a><span data-ttu-id="59caf-130">2. Verstehen Ihrer App-Projektkomponenten</span><span class="sxs-lookup"><span data-stu-id="59caf-130">2. Understand your app project components</span></span>

<span data-ttu-id="59caf-131">Ein Großteil der App-Konfigurationen und Gerüste wird automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Teams Toolkit erstellen.</span><span class="sxs-lookup"><span data-stu-id="59caf-131">Much of the app configurations and scaffolding are set up automatically when you create your project with the Teams Toolkit.</span></span>

* <span data-ttu-id="59caf-132">App-Konfigurationen: Um die Konfigurationen Ihrer Messagingerweiterung anzuzeigen oder zu aktualisieren, wählen Sie **App Studio** im Toolkit aus, und wechseln Sie zu **Messagingerweiterungen**.</span><span class="sxs-lookup"><span data-stu-id="59caf-132">App configurations: To view or update your messaging extension's configurations, select **App Studio** in the toolkit and go to **Messaging extensions**.</span></span>
* <span data-ttu-id="59caf-133">App-Gerüst: Das App-Gerüst stellt eine `botActivityHandler.js` Datei bereit, die sich im Stammverzeichnis Ihres Projekts befindet, um zu verarbeiten, wie Ihre Messaging-Erweiterung (oder technisch gesehen der Bot der [Messaging-Erweiterung)](#4-configure-the-bot-for-your-messaging-extension)auf Suchanfragen in Teams reagiert.</span><span class="sxs-lookup"><span data-stu-id="59caf-133">App scaffolding: The app scaffolding provides a `botActivityHandler.js` file, located in the root directory of your project, for handling how your messaging extension (or technically, the [messaging extension's bot](#4-configure-the-bot-for-your-messaging-extension)) responds to search queries in Teams.</span></span>

## <a name="3-set-up-a-secure-tunnel-to-your-app"></a><span data-ttu-id="59caf-134">3. Richten Sie einen sicheren Tunnel zu Ihrer App ein</span><span class="sxs-lookup"><span data-stu-id="59caf-134">3. Set up a secure tunnel to your app</span></span>

<span data-ttu-id="59caf-135">Zu Testzwecken hosten wir Ihre Messagingerweiterung auf einem lokalen Webserver (Port 3978).</span><span class="sxs-lookup"><span data-stu-id="59caf-135">For testing purposes, let's host your messaging extension on a local web server (port 3978).</span></span> <span data-ttu-id="59caf-136">Sie werden [ngrok](https://ngrok.com/download) verwenden, um einen sicheren Tunnel zum localhost einzurichten.</span><span class="sxs-lookup"><span data-stu-id="59caf-136">You are going to use [ngrok](https://ngrok.com/download) to set up a secure tunnel to localhost.</span></span> <span data-ttu-id="59caf-137">Weitere Informationen finden Sie in [Build your first bot for Microsoft Teams.](../build-your-first-app/build-bot.md#3-securely-expose-your-localhost-to-the-internet)</span><span class="sxs-lookup"><span data-stu-id="59caf-137">See [build your first bot for Microsoft Teams](../build-your-first-app/build-bot.md#3-securely-expose-your-localhost-to-the-internet) for details.</span></span> 

1. <span data-ttu-id="59caf-138">Wenn Sie dies noch nicht getan haben, installieren Sie [ngrok](https://ngrok.com/download).</span><span class="sxs-lookup"><span data-stu-id="59caf-138">If you haven't already, install [ngrok](https://ngrok.com/download).</span></span>
1. <span data-ttu-id="59caf-139">Führen Sie in einem Terminal `ngrok http -host-header=rewrite 3978` aus.</span><span class="sxs-lookup"><span data-stu-id="59caf-139">In a terminal, run `ngrok http -host-header=rewrite 3978`.</span></span>
1. <span data-ttu-id="59caf-140">Kopieren Sie die HTTPS-URL in der Ausgabe (z. B. `https://468b9ab725e9.ngrok.io` ), da Teams HTTPS-Verbindungen erfordert.</span><span class="sxs-lookup"><span data-stu-id="59caf-140">Copy the HTTPS URL in the output (for example, `https://468b9ab725e9.ngrok.io`) since Teams requires HTTPS connections.</span></span>

   <span data-ttu-id="59caf-141">Mit dieser URL können Teams (die HTTPS-Verbindungen erfordert) tunneln, wo Sie Ihre App hosten `localhost` (auf Port 3978).</span><span class="sxs-lookup"><span data-stu-id="59caf-141">With this URL, Teams (which requires HTTPS connections) will be able tunnel to where you're hosting your app (`localhost` on port 3978).</span></span>

## <a name="4-configure-the-bot-for-your-messaging-extension"></a><span data-ttu-id="59caf-142">4. Konfigurieren Sie den Bot für Ihre Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="59caf-142">4. Configure the bot for your messaging extension</span></span>

<span data-ttu-id="59caf-143">Messagingerweiterungen sind auf Bots angewiesen, um Benutzeranfragen von Teams an Ihren gehosteten Dienst zu senden und zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="59caf-143">Messaging extensions rely on bots to send and process user requests from Teams to your hosted service.</span></span> <span data-ttu-id="59caf-144">Der Bot muss beim Azure Bot Service registriert sein, was beim Einrichten Ihrer App mit dem Teams Toolkit durchgeführt wurde.</span><span class="sxs-lookup"><span data-stu-id="59caf-144">The bot must be registered with the Azure Bot Service, which was done when you set up your app using the Teams Toolkit.</span></span>

<span data-ttu-id="59caf-145">Sie müssen weiterhin eine Bot-Endpunkt-URL angeben, um Suchabfragen in Ihrer Messagingerweiterung zu empfangen und zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="59caf-145">You still must specify a bot endpoint URL to receive and process search queries in your messaging extension.</span></span> <span data-ttu-id="59caf-146">In der Regel sieht die URL wie `https://HOST_URL/api/messages` aus.</span><span class="sxs-lookup"><span data-stu-id="59caf-146">Typically, the URL looks like `https://HOST_URL/api/messages`.</span></span> <span data-ttu-id="59caf-147">Sie können dies schnell im Toolkit konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="59caf-147">You can configure this quickly in the toolkit.</span></span>

1. Wählen Sie in Visual Studio Code **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: auf der linken Aktivitätsleiste aus, und wählen Sie **Microsoft Teams Toolkit öffnen**.
1. <span data-ttu-id="59caf-149">Gehen Sie zu **Bots > Vorhandene Bot-Registrierungen** und wählen Sie den Bot aus, den Sie während des Setups erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="59caf-149">Go to **Bots > Existing bot registrations** and select the bot you created during setup.</span></span>
1. <span data-ttu-id="59caf-150">Geben Sie im Feld **Bot-Endpunktadresse** die ngrok-URL (z. B. ) ein, in der Sie den Bot hosten und an ihn `https://468b9ab725e9.ngrok.io` `/api/messages` anhängen.</span><span class="sxs-lookup"><span data-stu-id="59caf-150">In the **Bot endpoint address** field, enter the ngrok URL (for example, `https://468b9ab725e9.ngrok.io`) where you're hosting the bot and append `/api/messages` to it.</span></span>

   <span data-ttu-id="59caf-151">Ihr Bot wird in der Lage sein, Abfragen in Ihrer Messaging-Erweiterung zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="59caf-151">Your bot will be able to handle queries in your messaging extension.</span></span>

## <a name="5-build-and-run-your-app"></a><span data-ttu-id="59caf-152">5. Erstellen und Ausführen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="59caf-152">5. Build and run your app</span></span>

<span data-ttu-id="59caf-153">Sie haben eine URL zum Hosten Ihrer Messagingerweiterung eingerichtet und für die Verarbeitung von Suchvorgängen konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="59caf-153">You've set up a URL to host your messaging extension and configured it to handle searches.</span></span> <span data-ttu-id="59caf-154">Es ist an der Zeit, Ihre App in Betrieb zu nehmen.</span><span class="sxs-lookup"><span data-stu-id="59caf-154">It's time to get your app up and running.</span></span>

1. <span data-ttu-id="59caf-155">Öffnen Sie das Terminal, und wechseln Sie zum Stammverzeichnis Ihres App-Projekts.</span><span class="sxs-lookup"><span data-stu-id="59caf-155">Open terminal and go to the root directory of your app project.</span></span>
1. <span data-ttu-id="59caf-156">Führen Sie `npm install` aus.</span><span class="sxs-lookup"><span data-stu-id="59caf-156">Run `npm install`.</span></span>
1. <span data-ttu-id="59caf-157">Führen Sie `npm start` aus.</span><span class="sxs-lookup"><span data-stu-id="59caf-157">Run `npm start`.</span></span>

   <span data-ttu-id="59caf-158">Wenn dies erfolgreich ist, wird die folgende Meldung angezeigt, die darauf hinweist, dass Ihr Messagingerweiterungsdienst auf Aktivitäten in Ihrem folgenden Dienst `localhost` wartet:</span><span class="sxs-lookup"><span data-stu-id="59caf-158">If successful, you see the following message indicating your messaging extension service is listening for activity at your `localhost`:</span></span>

   `Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-messaging-extension-in-teams"></a><span data-ttu-id="59caf-159">6. Sideload Ihre Messaging-Erweiterung in Teams</span><span class="sxs-lookup"><span data-stu-id="59caf-159">6. Sideload your messaging extension in Teams</span></span>

<span data-ttu-id="59caf-160">Wenn Ihre Messagingerweiterung ausgeführt wird, können Sie sie in Teams installieren.</span><span class="sxs-lookup"><span data-stu-id="59caf-160">With your messaging extension running, you can install it in Teams.</span></span>

> [!TIP]
> <span data-ttu-id="59caf-161">Wenn Sie noch keine Teams App geladen haben und Probleme auftreten, befolgen Sie diese [Anweisungen](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams).</span><span class="sxs-lookup"><span data-stu-id="59caf-161">If you haven't sideloaded a Teams app before and run into issues, follow these [instructions](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams).</span></span>

1. <span data-ttu-id="59caf-162">Wählen Sie Visual Studio Code die **Taste F5** aus, um einen Teams Webclient zu starten.</span><span class="sxs-lookup"><span data-stu-id="59caf-162">In Visual Studio Code, select the **F5** key to launch a Teams web client.</span></span>
1. <span data-ttu-id="59caf-163">Wählen Sie im Dialogfeld App-Installation die Option **Für mich hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="59caf-163">In the app install dialog, select **Add for me**.</span></span>

## <a name="7-test-your-messaging-extension"></a><span data-ttu-id="59caf-164">7. Testen Sie Ihre Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="59caf-164">7. Test your messaging extension</span></span>

<span data-ttu-id="59caf-165">Erfahren Sie, wie Messagingerweiterungen in einem Teams Chat funktionieren.</span><span class="sxs-lookup"><span data-stu-id="59caf-165">Learn how messaging extensions work in a Teams chat.</span></span>

1. <span data-ttu-id="59caf-166">Starten Sie einen neuen Chat.</span><span class="sxs-lookup"><span data-stu-id="59caf-166">Start a new chat.</span></span> Wählen Sie im Feld Verfassen **Mehr** :::image type="icon" source="../assets/icons/teams-client-more.png"::: aus, und wählen Sie die Messagingerweiterungs-App aus, die Sie gerade seitlich geladen haben.
1. <span data-ttu-id="59caf-168">Versuchen Sie, nach etwas zu suchen (z. B. **Tickets**).</span><span class="sxs-lookup"><span data-stu-id="59caf-168">Try searching for something (for example, **Tickets**).</span></span> <span data-ttu-id="59caf-169">Wenn Ihre App funktioniert, sehen Sie Beispielsuchergebnisse (Sie können später eigene hinzufügen).</span><span class="sxs-lookup"><span data-stu-id="59caf-169">If your app is working, you'll see sample search results (you can add your own later).</span></span>

   :::image type="content" source="../assets/images/build-your-first-app/me-teams-test.png" alt-text="Ein Screenshot, der zeigt, wie eine suchbasierte Messagingerweiterung im Teams Verfassen verwendet wird.":::

## <a name="troubleshooting"></a><span data-ttu-id="59caf-171">Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="59caf-171">Troubleshooting</span></span>

<span data-ttu-id="59caf-172">Die folgenden Informationen können hilfreich sein, wenn Sie Probleme beim Abschließen dieses Tutorials hatten.</span><span class="sxs-lookup"><span data-stu-id="59caf-172">The following information may help if you had issues completing this tutorial.</span></span>

<span data-ttu-id="59caf-173">**Bot ist nicht mit Teams verbunden**</span><span class="sxs-lookup"><span data-stu-id="59caf-173">**Bot isn't connected to Teams**</span></span>

<span data-ttu-id="59caf-174">Wenn Sie Ihre App installiert haben, diese jedoch nicht funktioniert, stellen Sie sicher, dass der Bot der Messagingerweiterung [mit dem Teams *Kanal*](/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true)des Azure Bot Service verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="59caf-174">If you installed your app but it isn't working, make sure the messaging extension's bot is [connected to the Azure Bot Service's Teams *channel*](/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true).</span></span>

<span data-ttu-id="59caf-175">Es ist wichtig zu verstehen, dass dies nicht dasselbe ist wie ein Kanal in Teams.</span><span class="sxs-lookup"><span data-stu-id="59caf-175">It's important to understand that this isn't the same as a channel in Teams.</span></span> <span data-ttu-id="59caf-176">In diesem Fall ist ein Kanal, wie der Azure Bot Service Ihren Bot mit Teams oder einer anderen [unterstützten Microsoft- oder Drittanbieter-Kommunikations-App](/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)verbindet.</span><span class="sxs-lookup"><span data-stu-id="59caf-176">In this case, a channel is how the Azure Bot Service connects your bot to Teams or another [supported Microsoft or third-party communications app](/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span>

## <a name="see-also"></a><span data-ttu-id="59caf-177">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="59caf-177">See also</span></span>

* [<span data-ttu-id="59caf-178">Teams Verfassen oder Befehlsfeld</span><span class="sxs-lookup"><span data-stu-id="59caf-178">Teams compose or command box</span></span>](../messaging-extensions/what-are-messaging-extensions.md) 
* [<span data-ttu-id="59caf-179">Einschließen einer Link-Entfurlingsfunktion</span><span class="sxs-lookup"><span data-stu-id="59caf-179">Include a link unfurling feature</span></span>](../messaging-extensions/how-to/link-unfurling.md)
* [<span data-ttu-id="59caf-180">Richtlinien für den Entwurf</span><span class="sxs-lookup"><span data-stu-id="59caf-180">Design guidelines</span></span>](../messaging-extensions/design/messaging-extension-design.md) 
* [<span data-ttu-id="59caf-181">Produktionsfähige UI-Vorlagen</span><span class="sxs-lookup"><span data-stu-id="59caf-181">Production-ready UI templates</span></span>](../concepts/design/design-teams-app-ui-templates.md) 
* [<span data-ttu-id="59caf-182">Authentifizierung hinzufügen</span><span class="sxs-lookup"><span data-stu-id="59caf-182">Add authentication</span></span>](../messaging-extensions/how-to/add-authentication.md)
* [<span data-ttu-id="59caf-183">Erstellen einer aktionsbasierten Messagingerweiterung</span><span class="sxs-lookup"><span data-stu-id="59caf-183">Create an action-based messaging extension</span></span>](../messaging-extensions/how-to/action-commands/define-action-command.md)
* [<span data-ttu-id="59caf-184">Microsoft Bot Framework</span><span class="sxs-lookup"><span data-stu-id="59caf-184">Microsoft Bot Framework</span></span>](https://dev.botframework.com/)

## <a name="next-steps"></a><span data-ttu-id="59caf-185">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="59caf-185">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="59caf-186">Definition von Suchbefehlen</span><span class="sxs-lookup"><span data-stu-id="59caf-186">Define search commands</span></span>](../messaging-extensions/how-to/search-commands/define-search-command.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="59caf-187">Reagieren auf die Suchanfragen der Benutzer</span><span class="sxs-lookup"><span data-stu-id="59caf-187">Respond to users' searches</span></span>](../messaging-extensions/how-to/search-commands/respond-to-search.md)
