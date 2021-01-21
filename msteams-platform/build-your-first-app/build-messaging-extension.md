---
title: Erste Schritte – Erstellen einer Messagingerweiterung
author: heath-hamilton
description: Erstellen Sie mithilfe des Microsoft Teams Toolkits schnell eine Microsoft Teams-Messaging-Erweiterung.
ms.author: lajanuar
ms.date: 11/04/2020
ms.topic: tutorial
ms.openlocfilehash: 86d44740feaa2cd33aff0e1dde14d757420d90d6
ms.sourcegitcommit: 00c657e3bf57d3b92aca7da941cde47a2eeff4d0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "49911919"
---
# <a name="build-a-messaging-extension-for-microsoft-teams"></a><span data-ttu-id="ea6e8-103">Erstellen einer Messagingerweiterung für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="ea6e8-103">Build a messaging extension for Microsoft Teams</span></span>

<span data-ttu-id="ea6e8-104">Es gibt zwei Arten von Messagingerweiterungen für *Teams-Apps:* [Suchbefehle](../messaging-extensions/how-to/search-commands/define-search-command.md) und [Aktionsbefehle.](../messaging-extensions/how-to/action-commands/define-action-command.md)</span><span class="sxs-lookup"><span data-stu-id="ea6e8-104">There are two types of Teams app *messaging extensions*: [Search commands](../messaging-extensions/how-to/search-commands/define-search-command.md) and [action commands](../messaging-extensions/how-to/action-commands/define-action-command.md).</span></span>

<span data-ttu-id="ea6e8-105">In dieser Lektion erstellen Sie einen Suchbefehl *(auch* als suchbasierte *Messagingerweiterung* bezeichnet), der eine Verknüpfung zum Suchen externer Inhalte und zum Freigeben in Teams ist.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-105">In this lesson, you'll create a *search command* (also known as a *search-based messaging extension*), which is a shortcut for finding external content and sharing it in Teams.</span></span> <span data-ttu-id="ea6e8-106">Benutzer können über das Feld "Teams verfassen" oder ["Befehl" auf Suchbefehle zugreifen.](../messaging-extensions/what-are-messaging-extensions.md)</span><span class="sxs-lookup"><span data-stu-id="ea6e8-106">Users can access search commands from the [Teams compose or command box](../messaging-extensions/what-are-messaging-extensions.md).</span></span>

## <a name="your-assignment"></a><span data-ttu-id="ea6e8-107">Ihre Zuordnung</span><span class="sxs-lookup"><span data-stu-id="ea6e8-107">Your assignment</span></span>

<span data-ttu-id="ea6e8-108">Das Helpdesk Ihrer Organisation kommuniziert über Teams mit Benutzern, die Tickets befinden sich jedoch in einem separaten System.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-108">Your organization's help desk communicates with users through Teams, but the tickets reside in a separate system.</span></span> <span data-ttu-id="ea6e8-109">Das bedeutet, dass Supportmitarbeiter ständig zwischen Apps hin und her wechseln müssen.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-109">This means support staff must constantly go back and forth between apps.</span></span> <span data-ttu-id="ea6e8-110">Sie untersuchen, wie Sie diesen Kontextwechsel reduzieren können, indem Sie eine einfache suchbasierte Messagingerweiterung für Teams erstellen.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-110">You'll investigate how you might reduce this much context switching by creating a simple search-based messaging extension for Teams.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="ea6e8-111">Was Sie lernen werden</span><span class="sxs-lookup"><span data-stu-id="ea6e8-111">What you'll learn</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="ea6e8-112">Erstellen eines App-Projekts und eines Messaging-Erweiterungs-Bots mithilfe des Microsoft Teams Toolkit for Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="ea6e8-112">Create an app project and messaging extension bot using the Microsoft Teams Toolkit for Visual Studio Code</span></span>
> * <span data-ttu-id="ea6e8-113">Identifizieren der App-Konfigurationen und einiger der für Messagingerweiterungen relevanten Gerüste</span><span class="sxs-lookup"><span data-stu-id="ea6e8-113">Identify the app configurations and some of the scaffolding relevant to messaging extensions</span></span>
> * <span data-ttu-id="ea6e8-114">Lokales Hosten einer App</span><span class="sxs-lookup"><span data-stu-id="ea6e8-114">Host an app locally</span></span>
> * <span data-ttu-id="ea6e8-115">Konfigurieren des Bots für Ihre Messagingerweiterung</span><span class="sxs-lookup"><span data-stu-id="ea6e8-115">Configure the bot for your messaging extension</span></span>
> * <span data-ttu-id="ea6e8-116">Querladen und Testen einer Messagingerweiterung in Teams</span><span class="sxs-lookup"><span data-stu-id="ea6e8-116">Sideload and test a messaging extension in Teams</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="ea6e8-117">Vorabinformationen</span><span class="sxs-lookup"><span data-stu-id="ea6e8-117">Before you begin</span></span>

<span data-ttu-id="ea6e8-118">Falls noch nicht, stellen Sie sicher, dass Sie die Voraussetzungen für die Entwicklung von Teams verstehen und [installieren.](build-first-app-overview.md#get-prerequisites)</span><span class="sxs-lookup"><span data-stu-id="ea6e8-118">If you haven't yet, make sure you [understand and install the Teams development prerequisites](build-first-app-overview.md#get-prerequisites).</span></span>

## <a name="1-create-your-app-project"></a><span data-ttu-id="ea6e8-119">1. Erstellen Ihres App-Projekts</span><span class="sxs-lookup"><span data-stu-id="ea6e8-119">1. Create your app project</span></span>

<span data-ttu-id="ea6e8-120">Mit dem Microsoft Teams Toolkit können Sie die folgenden Komponenten für Ihre Messagingerweiterung einrichten:</span><span class="sxs-lookup"><span data-stu-id="ea6e8-120">The Microsoft Teams Toolkit helps you set up the following components for your messaging extension:</span></span>

* <span data-ttu-id="ea6e8-121">**Für Messagingerweiterungen relevante App-Konfigurationen** und Gerüste</span><span class="sxs-lookup"><span data-stu-id="ea6e8-121">**App configurations and scaffolding** relevant to messaging extensions</span></span>
* <span data-ttu-id="ea6e8-122">**Bot** für Ihre Messaging-Erweiterung, die automatisch beim Microsoft Azure Bot Service registriert wird</span><span class="sxs-lookup"><span data-stu-id="ea6e8-122">**Bot** for your messaging extension that's automatically registered with the Microsoft Azure Bot Service</span></span>

> [!TIP]
> <span data-ttu-id="ea6e8-123">Wenn Sie noch kein Teams-App-Projekt erstellt haben, ist [](../build-your-first-app/build-and-run.md) es möglicherweise hilfreich, diesen Anweisungen zu folgen, die Projekte ausführlicher erläutern.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-123">If you haven't created a Teams app project before, you might find it helpful to follow [these instructions](../build-your-first-app/build-and-run.md) that explain projects in more detail.</span></span>

1. In Visual Studio Code, select **Microsoft Teams** on the left Activity Bar and choose Create a new Teams :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: **app**.
1. <span data-ttu-id="ea6e8-125">Wenn Sie dazu aufgefordert werden, melden Sie sich mit Ihrem Microsoft 365-Entwicklungskonto an.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-125">When prompted, sign in with your Microsoft 365 development account.</span></span>
1. <span data-ttu-id="ea6e8-126">Wählen Sie **auf dem Bildschirm "Funktionen** hinzufügen" die Option **"Messagingerweiterung" und** dann **"Weiter" aus.**</span><span class="sxs-lookup"><span data-stu-id="ea6e8-126">On the **Add capabilities** screen, select **Messaging Extension** then **Next**.</span></span>
1. <span data-ttu-id="ea6e8-127">Geben Sie einen Namen für Ihre Teams-App ein.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-127">Enter a name for your Teams app.</span></span> <span data-ttu-id="ea6e8-128">(Dies ist der Standardname für Ihre App und auch der Name des App-Projektverzeichnisses auf dem lokalen Computer.)</span><span class="sxs-lookup"><span data-stu-id="ea6e8-128">(This is the default name for your app and also the name of the app project directory on your local machine.)</span></span>
1. <span data-ttu-id="ea6e8-129">Gehen Sie **auf dem Bildschirm "Messagingerweiterung konfigurieren"** wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="ea6e8-129">On the **Configure messaging extension** screen, do the following:</span></span>
    1. <span data-ttu-id="ea6e8-130">Wählen Sie nur **die suchbasierte Option** für den Typ der Messagingerweiterung aus.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-130">Choose only the **Search-based** option for the type of messaging extension.</span></span>
    1. <span data-ttu-id="ea6e8-131">Wählen **Sie "Neuen Bot erstellen"** und dann **"Botregistrierung erstellen" aus.**</span><span class="sxs-lookup"><span data-stu-id="ea6e8-131">Select **Create a new Bot** then **Create Bot Registration**.</span></span> <span data-ttu-id="ea6e8-132">Wenn dies erfolgreich ist, hat Ihr neuer Bot den **Status "Registriert".**</span><span class="sxs-lookup"><span data-stu-id="ea6e8-132">If successful, your new bot will have a **Registered** status.</span></span>
    1. <span data-ttu-id="ea6e8-133">Wählen Sie derzeit **"Nein"** für die Option zum Deaktivieren des Links aus.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-133">For now, select **No** for the link unfurling option.</span></span>
1. <span data-ttu-id="ea6e8-134">Wählen **Sie "Fertig** stellen" am unteren Rand des Bildschirms aus, um das Projekt zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-134">Select **Finish** at the bottom of the screen to configure your project.</span></span>

## <a name="2-identify-relevant-app-project-components"></a><span data-ttu-id="ea6e8-135">2. Identifizieren relevanter Komponenten des App-Projekts</span><span class="sxs-lookup"><span data-stu-id="ea6e8-135">2. Identify relevant app project components</span></span>

<span data-ttu-id="ea6e8-136">Ein Teil der App-Konfigurationen und -Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Teams Toolkit erstellen.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-136">Much of the app configurations and scaffolding are set up automatically when you create your project with the Teams Toolkit.</span></span>

### <a name="app-configurations"></a><span data-ttu-id="ea6e8-137">App-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="ea6e8-137">App configurations</span></span>

<span data-ttu-id="ea6e8-138">Wenn Sie die Konfigurationen Ihrer Messagingerweiterung anzeigen oder aktualisieren möchten, wählen **Sie App Studio** im Toolkit aus, und wechseln Sie zu **Messaging-Erweiterungen.**</span><span class="sxs-lookup"><span data-stu-id="ea6e8-138">To view or update your messaging extension's configurations, select **App Studio** in the toolkit and go to **Messaging extensions**.</span></span>

### <a name="app-scaffolding"></a><span data-ttu-id="ea6e8-139">App-Gerüst</span><span class="sxs-lookup"><span data-stu-id="ea6e8-139">App scaffolding</span></span>

<span data-ttu-id="ea6e8-140">Das App-Gerüst stellt eine Datei im Stammverzeichnis Ihres Projekts zur Verfügung, um zu behandeln, wie Ihre Messagingerweiterung (oder technisch der Bot der Messagingerweiterung) auf Suchabfragen `botActivityHandler.js` in Teams reagiert. [](#4-configure-the-bot-for-your-messaging-extension)</span><span class="sxs-lookup"><span data-stu-id="ea6e8-140">The app scaffolding provides a `botActivityHandler.js` file, located in the root directory of your project, for handling how your messaging extension (or technically, the [messaging extension's bot](#4-configure-the-bot-for-your-messaging-extension)) responds to search queries in Teams.</span></span>

## <a name="3-set-up-a-secure-tunnel-to-your-app"></a><span data-ttu-id="ea6e8-141">3. Einrichten eines sicheren Tunnels für Ihre App</span><span class="sxs-lookup"><span data-stu-id="ea6e8-141">3. Set up a secure tunnel to your app</span></span>

<span data-ttu-id="ea6e8-142">Zu Testzwecken hosten wir Ihre Messagingerweiterung auf einem lokalen Webserver (Port 3978).</span><span class="sxs-lookup"><span data-stu-id="ea6e8-142">For testing purposes, let's host your messaging extension on a local web server (port 3978).</span></span>

1. <span data-ttu-id="ea6e8-143">Falls noch nicht, installieren Sie [ngrok](https://ngrok.com/download).</span><span class="sxs-lookup"><span data-stu-id="ea6e8-143">If you haven't already, install [ngrok](https://ngrok.com/download).</span></span>
1. <span data-ttu-id="ea6e8-144">Führen Sie in einem Terminal `ngrok http -host-header=rewrite 3978` .</span><span class="sxs-lookup"><span data-stu-id="ea6e8-144">In a terminal, run `ngrok http -host-header=rewrite 3978`.</span></span>
1. <span data-ttu-id="ea6e8-145">Kopieren Sie die HTTPS-URL in der Ausgabe (z. B. `https://468b9ab725e9.ngrok.io` ), da Teams https-Verbindungen benötigt.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-145">Copy the HTTPS URL in the output (for example, `https://468b9ab725e9.ngrok.io`) since Teams requires HTTPS connections.</span></span>

<span data-ttu-id="ea6e8-146">Mit dieser URL kann Teams (für das HTTPS-Verbindungen erforderlich sind) an den Ort tunneln, an dem Sie Ihre App hosten (an `localhost` Port 3978).</span><span class="sxs-lookup"><span data-stu-id="ea6e8-146">With this URL, Teams (which requires HTTPS connections) will be able tunnel to where you're hosting your app (`localhost` on port 3978).</span></span>

## <a name="4-configure-the-bot-for-your-messaging-extension"></a><span data-ttu-id="ea6e8-147">4. Konfigurieren des Bots für Ihre Messagingerweiterung</span><span class="sxs-lookup"><span data-stu-id="ea6e8-147">4. Configure the bot for your messaging extension</span></span>

<span data-ttu-id="ea6e8-148">Messagingerweiterungen verlassen sich auf Bots, um Benutzeranforderungen von Teams an Ihren gehosteten Dienst zu senden und zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-148">Messaging extensions rely on bots to send and process user requests from Teams to your hosted service.</span></span> <span data-ttu-id="ea6e8-149">Der Bot muss beim Azure Bot Service registriert sein, was beim Einrichten Ihrer App mithilfe des Teams Toolkits erfolgt ist.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-149">The bot must be registered with the Azure Bot Service, which was done when you set up your app using the Teams Toolkit.</span></span>

<span data-ttu-id="ea6e8-150">Sie müssen dennoch eine Botendpunkt-URL angeben, um Suchabfragen in Ihrer Messagingerweiterung zu empfangen und zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-150">You still must specify a bot endpoint URL to receive and process search queries in your messaging extension.</span></span> <span data-ttu-id="ea6e8-151">In der Regel sieht die URL wie `https://HOST_URL/api/messages` aus.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-151">Typically, the URL looks like `https://HOST_URL/api/messages`.</span></span> <span data-ttu-id="ea6e8-152">Sie können dies im Toolkit schnell konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-152">You can configure this quickly in the toolkit.</span></span>

1. In Visual Studio Code, select **Microsoft Teams** on the left Activity Bar and choose Open Microsoft Teams :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: **Toolkit**.
1. <span data-ttu-id="ea6e8-154">Wechseln Sie **zu Bots > vorhandenen Botregistrierungen,** und wählen Sie den Bot aus, den Sie während des Setups erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-154">Go to **Bots > Existing bot registrations** and select the bot you created during setup.</span></span>
1. <span data-ttu-id="ea6e8-155">Geben Sie **im Adressfeld des** Bot-Endpunkts die ngrok-URL ein (z. B. ), in der Sie den Bot hosten, `https://468b9ab725e9.ngrok.io` und fügen Sie ihn `/api/messages` an.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-155">In the **Bot endpoint address** field, enter the ngrok URL (for example, `https://468b9ab725e9.ngrok.io`) where you're hosting the bot and append `/api/messages` to it.</span></span>

<span data-ttu-id="ea6e8-156">Ihr Bot kann Abfragen in Ihrer Messagingerweiterung verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-156">Your bot will be able to handle queries in your messaging extension.</span></span>

## <a name="5-build-and-run-your-app"></a><span data-ttu-id="ea6e8-157">5. Erstellen und Ausführen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="ea6e8-157">5. Build and run your app</span></span>

<span data-ttu-id="ea6e8-158">Sie haben eine URL zum Hosten Ihrer Messagingerweiterung eingerichtet und für die Verarbeitung von Suchen konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-158">You've set up a URL to host your messaging extension and configured it to handle searches.</span></span> <span data-ttu-id="ea6e8-159">Es ist an der Zeit, Ihre App zu starten und zu starten.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-159">It's time to get your app up and running.</span></span>

1. <span data-ttu-id="ea6e8-160">Wechseln Sie in einem Terminal zum Stammverzeichnis Ihres App-Projekts, und führen Sie es `npm install` aus.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-160">In a terminal, go to the root directory of your app project and run `npm install`.</span></span>
1. <span data-ttu-id="ea6e8-161">Führen Sie `npm start` .</span><span class="sxs-lookup"><span data-stu-id="ea6e8-161">Run `npm start`.</span></span>

<span data-ttu-id="ea6e8-162">Wenn dies erfolgreich ist, wird die folgende Meldung angezeigt, die angibt, dass ihr Messagingerweiterungsdienst Aktivitäten an Ihrem Gerät `localhost` abhört:</span><span class="sxs-lookup"><span data-stu-id="ea6e8-162">If successful, you see the following message indicating your messaging extension service is listening for activity at your `localhost`:</span></span>

`Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-messaging-extension-in-teams"></a><span data-ttu-id="ea6e8-163">6. Querladen Ihrer Messagingerweiterung in Teams</span><span class="sxs-lookup"><span data-stu-id="ea6e8-163">6. Sideload your messaging extension in Teams</span></span>

<span data-ttu-id="ea6e8-164">Wenn Ihre Messagingerweiterung ausgeführt wird, können Sie sie in Teams installieren.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-164">With your messaging extension running, you can install it in Teams.</span></span>

> [!TIP]
> <span data-ttu-id="ea6e8-165">Wenn Sie zuvor noch keine Teams-App sideloaded haben und Probleme auftreten, führen Sie die folgenden [Anweisungen aus.](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams)</span><span class="sxs-lookup"><span data-stu-id="ea6e8-165">If you haven't sideloaded a Teams app before and run into issues, follow these [instructions](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams).</span></span>

1. <span data-ttu-id="ea6e8-166">Drücken Visual Studio Code die **F5-TASTE,** um einen Teams-Webclient zu starten.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-166">In Visual Studio Code, press the **F5** key to launch a Teams web client.</span></span>
1. <span data-ttu-id="ea6e8-167">Wählen Sie im Dialogfeld "App-Installation" die Option **"Für mich hinzufügen" aus.**</span><span class="sxs-lookup"><span data-stu-id="ea6e8-167">In the app install dialog, select **Add for me**.</span></span>

## <a name="7-test-your-messaging-extension"></a><span data-ttu-id="ea6e8-168">7. Testen der Messagingerweiterung</span><span class="sxs-lookup"><span data-stu-id="ea6e8-168">7. Test your messaging extension</span></span>

<span data-ttu-id="ea6e8-169">Erfahren Sie, wie Messagingerweiterungen in einem Teams-Chat funktionieren.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-169">Learn how messaging extensions work in a Teams chat.</span></span>

1. <span data-ttu-id="ea6e8-170">Starten Sie einen neuen Chat.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-170">Start a new chat.</span></span> Wählen Sie im Feld zum Verfassen **mehr** aus, und wählen Sie :::image type="icon" source="../assets/icons/teams-client-more.png"::: die Messaging-Erweiterungs-App aus, die Sie gerade geladen haben.
1. <span data-ttu-id="ea6e8-172">Suchen Sie nach etwas (z. B. **Tickets).**</span><span class="sxs-lookup"><span data-stu-id="ea6e8-172">Try searching for something (for example, **Tickets**).</span></span> <span data-ttu-id="ea6e8-173">Wenn Ihre App funktioniert, werden Beispielsuchergebnisse angezeigt (Sie können später eigene hinzufügen).</span><span class="sxs-lookup"><span data-stu-id="ea6e8-173">If your app is working, you'll see sample search results (you can add your own later).</span></span><br/>
   :::image type="content" source="../assets/images/build-your-first-app/me-teams-test.png" alt-text="Ein Screenshot, der zeigt, wie eine suchbasierte Messagingerweiterung im Feld zum Verfassen von Teams verwendet wird.":::

## <a name="well-done"></a><span data-ttu-id="ea6e8-175">Gut gemacht</span><span class="sxs-lookup"><span data-stu-id="ea6e8-175">Well done</span></span>

<span data-ttu-id="ea6e8-176">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="ea6e8-176">Congratulations!</span></span> <span data-ttu-id="ea6e8-177">Sie verfügen über eine grundlegende Teams-Messaging-Erweiterung, die für die Suche nach externen Inhalten im Feld zum Verfassen oder Befehl eingerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-177">You have a basic Teams messaging extension that's set up to search for external content in the compose or command box.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ea6e8-178">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="ea6e8-178">Next steps</span></span>

<span data-ttu-id="ea6e8-179">Auf den folgenden Seiten können Sie fortfahren und eine voll funktionsfähige Messagingerweiterung erstellen:</span><span class="sxs-lookup"><span data-stu-id="ea6e8-179">See the following pages to continue and build a fully featured messaging extension:</span></span>

1. <span data-ttu-id="ea6e8-180">[Definieren Sie Suchbefehle,](../messaging-extensions/how-to/search-commands/define-search-command.md) die für Ihren Dienst relevant sind.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-180">[Define search commands](../messaging-extensions/how-to/search-commands/define-search-command.md) that are relevant to your service.</span></span>
1. <span data-ttu-id="ea6e8-181">Konfigurieren Sie Ihren Dienst [so, dass er auf Benutzersuchen reagiert.](../messaging-extensions/how-to/search-commands/respond-to-search.md)</span><span class="sxs-lookup"><span data-stu-id="ea6e8-181">Configure your service to [respond to users' searches](../messaging-extensions/how-to/search-commands/respond-to-search.md).</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="ea6e8-182">Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="ea6e8-182">Troubleshooting</span></span>

<span data-ttu-id="ea6e8-183">Die folgenden Informationen können hilfreich sein, wenn beim Abschließen dieses Lernprogramms Probleme auftreten.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-183">The following information may help if you had issues completing this tutorial.</span></span>

### <a name="bot-isnt-connected-to-teams"></a><span data-ttu-id="ea6e8-184">Bot ist nicht mit Teams verbunden</span><span class="sxs-lookup"><span data-stu-id="ea6e8-184">Bot isn't connected to Teams</span></span>

<span data-ttu-id="ea6e8-185">Wenn Sie Ihre App installiert haben, aber nicht funktioniert, stellen Sie sicher, dass der Bot der Messagingerweiterung mit dem Teams-Kanal des [Azure Bot Service verbunden *ist.*](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="ea6e8-185">If you installed your app but it isn't working, make sure the messaging extension's bot is [connected to the Azure Bot Service's Teams *channel*](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true).</span></span>

<span data-ttu-id="ea6e8-186">Es ist wichtig zu wissen, dass dies nicht mit einem Kanal in Teams identisch ist.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-186">It's important to understand that this isn't the same as a channel in Teams.</span></span> <span data-ttu-id="ea6e8-187">In diesem Fall verbindet der Azure Bot Service Ihren Bot mit Teams oder einer anderen unterstützten Microsoft- oder [Drittanbieter-Kommunikations-App.](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="ea6e8-187">In this case, a channel is how the Azure Bot Service connects your bot to Teams or another [supported Microsoft or third-party communications app](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span>

## <a name="learn-more"></a><span data-ttu-id="ea6e8-188">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="ea6e8-188">Learn more</span></span>

* [<span data-ttu-id="ea6e8-189">Fügen Sie ein Feature zum Entfing von Links ein.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-189">Include a link unfurling feature</span></span>](../messaging-extensions/how-to/link-unfurling.md)
* <span data-ttu-id="ea6e8-190">Folgen Sie [unseren Entwurfsrichtlinien,](../messaging-extensions/design/messaging-extension-design.md) und erstellen Sie mit [produktionsbereiten](../concepts/design/design-teams-app-ui-templates.md) Benutzeroberflächenvorlagen, um eine nahtlose Benutzeroberfläche zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-190">Follow our [design guidelines](../messaging-extensions/design/messaging-extension-design.md) and build with [production-ready UI templates](../concepts/design/design-teams-app-ui-templates.md) to create a seamless experience.</span></span>
* [<span data-ttu-id="ea6e8-191">Authentifizierung hinzufügen</span><span class="sxs-lookup"><span data-stu-id="ea6e8-191">Add authentication</span></span>](../messaging-extensions/how-to/add-authentication.md)
* [<span data-ttu-id="ea6e8-192">Erstellen einer aktionsbasierten Messagingerweiterung</span><span class="sxs-lookup"><span data-stu-id="ea6e8-192">Create an action-based messaging extension</span></span>](../messaging-extensions/how-to/action-commands/define-action-command.md)
* [<span data-ttu-id="ea6e8-193">Microsoft Bot Framework</span><span class="sxs-lookup"><span data-stu-id="ea6e8-193">Microsoft Bot Framework</span></span>](https://dev.botframework.com/)
