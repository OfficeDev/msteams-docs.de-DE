---
title: Erste Schritte – Erstellen einer Messagingerweiterung
author: heath-hamilton
description: Erstellen Sie schnell eine Microsoft Teams-Messagingerweiterung mithilfe des Microsoft Teams Toolkits.
ms.author: lajanuar
localization_priority: Normal
ms.date: 11/04/2020
ms.topic: tutorial
ms.openlocfilehash: f3b5bc9c749d5e5276c0c7af7ff92f4ff5a00d0b
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020870"
---
# <a name="build-a-messaging-extension-for-microsoft-teams"></a><span data-ttu-id="a5fec-103">Erstellen einer Messagingerweiterung für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="a5fec-103">Build a messaging extension for Microsoft Teams</span></span>

<span data-ttu-id="a5fec-104">Es gibt zwei Arten von *Teams-Messagingerweiterungen:* [Suchbefehle](../messaging-extensions/how-to/search-commands/define-search-command.md) und [Aktionsbefehle.](../messaging-extensions/how-to/action-commands/define-action-command.md)</span><span class="sxs-lookup"><span data-stu-id="a5fec-104">There are two types of Teams *messaging extensions*: [Search commands](../messaging-extensions/how-to/search-commands/define-search-command.md) and [action commands](../messaging-extensions/how-to/action-commands/define-action-command.md).</span></span>

<span data-ttu-id="a5fec-105">In dieser Lektion erstellen Sie einen Suchbefehl *(auch* als suchbasierte Messagingerweiterung *bezeichnet),* der eine Verknüpfung zum Suchen externer Inhalte und deren Freigabe in Teams ist.</span><span class="sxs-lookup"><span data-stu-id="a5fec-105">In this lesson, you'll create a *search command* (also known as a *search-based messaging extension*), which is a shortcut for finding external content and sharing it in Teams.</span></span> <span data-ttu-id="a5fec-106">Benutzer können über das Verfassen- oder [Befehlsfeld Teams auf Suchbefehle zugreifen.](../messaging-extensions/what-are-messaging-extensions.md)</span><span class="sxs-lookup"><span data-stu-id="a5fec-106">Users can access search commands from the [Teams compose or command box](../messaging-extensions/what-are-messaging-extensions.md).</span></span>

## <a name="your-assignment"></a><span data-ttu-id="a5fec-107">Ihre Zuordnung</span><span class="sxs-lookup"><span data-stu-id="a5fec-107">Your assignment</span></span>

<span data-ttu-id="a5fec-108">Der Helpdesk Ihrer Organisation kommuniziert mit Benutzern über Teams, die Tickets befinden sich jedoch in einem separaten System.</span><span class="sxs-lookup"><span data-stu-id="a5fec-108">Your organization's help desk communicates with users through Teams, but the tickets reside in a separate system.</span></span> <span data-ttu-id="a5fec-109">Dies bedeutet, dass Supportmitarbeiter ständig zwischen Apps hin- und hergehen müssen.</span><span class="sxs-lookup"><span data-stu-id="a5fec-109">This means support staff must constantly go back and forth between apps.</span></span> <span data-ttu-id="a5fec-110">Sie untersuchen, wie Sie diesen Kontextwechsel reduzieren können, indem Sie eine einfache suchbasierte Messagingerweiterung für Teams erstellen.</span><span class="sxs-lookup"><span data-stu-id="a5fec-110">You'll investigate how you might reduce this much context switching by creating a simple search-based messaging extension for Teams.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="a5fec-111">Was Sie lernen werden</span><span class="sxs-lookup"><span data-stu-id="a5fec-111">What you'll learn</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="a5fec-112">Erstellen eines App-Projekts und eines Messagingerweiterungsbots mithilfe des Microsoft Teams Toolkits für Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="a5fec-112">Create an app project and messaging extension bot using the Microsoft Teams Toolkit for Visual Studio Code</span></span>
> * <span data-ttu-id="a5fec-113">Identifizieren der App-Konfigurationen und einiger Gerüste, die für Messagingerweiterungen relevant sind</span><span class="sxs-lookup"><span data-stu-id="a5fec-113">Identify the app configurations and some of the scaffolding relevant to messaging extensions</span></span>
> * <span data-ttu-id="a5fec-114">Lokal hosten einer App</span><span class="sxs-lookup"><span data-stu-id="a5fec-114">Host an app locally</span></span>
> * <span data-ttu-id="a5fec-115">Konfigurieren des Bots für Ihre Messagingerweiterung</span><span class="sxs-lookup"><span data-stu-id="a5fec-115">Configure the bot for your messaging extension</span></span>
> * <span data-ttu-id="a5fec-116">Querladen und Testen einer Messagingerweiterung in Teams</span><span class="sxs-lookup"><span data-stu-id="a5fec-116">Sideload and test a messaging extension in Teams</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="a5fec-117">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="a5fec-117">Before you begin</span></span>

<span data-ttu-id="a5fec-118">Falls noch nicht, stellen Sie sicher, dass Sie die Voraussetzungen für die [Teams-Entwicklung verstehen und installieren.](build-first-app-overview.md#get-prerequisites)</span><span class="sxs-lookup"><span data-stu-id="a5fec-118">If you haven't yet, make sure you [understand and install the Teams development prerequisites](build-first-app-overview.md#get-prerequisites).</span></span>

## <a name="1-create-your-app-project"></a><span data-ttu-id="a5fec-119">1. Erstellen Ihres App-Projekts</span><span class="sxs-lookup"><span data-stu-id="a5fec-119">1. Create your app project</span></span>

<span data-ttu-id="a5fec-120">Das Microsoft Teams Toolkit hilft Ihnen beim Einrichten der folgenden Komponenten für Ihre Messagingerweiterung:</span><span class="sxs-lookup"><span data-stu-id="a5fec-120">The Microsoft Teams Toolkit helps you set up the following components for your messaging extension:</span></span>

* <span data-ttu-id="a5fec-121">**Für Messagingerweiterungen** relevante App-Konfigurationen und Gerüste</span><span class="sxs-lookup"><span data-stu-id="a5fec-121">**App configurations and scaffolding** relevant to messaging extensions</span></span>
* <span data-ttu-id="a5fec-122">**Bot** für Ihre Messagingerweiterung, die automatisch beim Microsoft Azure Bot Service registriert ist</span><span class="sxs-lookup"><span data-stu-id="a5fec-122">**Bot** for your messaging extension that's automatically registered with the Microsoft Azure Bot Service</span></span>

> [!TIP]
> <span data-ttu-id="a5fec-123">Wenn Sie noch kein Teams-App-Projekt erstellt haben, ist [](../build-your-first-app/build-and-run.md) es möglicherweise hilfreich, diese Anweisungen zu befolgen, die Projekte ausführlicher erläutern.</span><span class="sxs-lookup"><span data-stu-id="a5fec-123">If you haven't created a Teams app project before, you might find it helpful to follow [these instructions](../build-your-first-app/build-and-run.md) that explain projects in more detail.</span></span>

1. Wählen Visual Studio Code auf der linken Aktivitätsleiste **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: aus, und wählen Sie Erstellen einer neuen **Teams-App aus.**
1. <span data-ttu-id="a5fec-125">Melden Sie sich bei Aufforderung mit Ihrem Microsoft 365-Entwicklungskonto an.</span><span class="sxs-lookup"><span data-stu-id="a5fec-125">When prompted, sign in with your Microsoft 365 development account.</span></span>
1. <span data-ttu-id="a5fec-126">Wählen Sie **auf dem Bildschirm** Funktionen hinzufügen die Option **Messagingerweiterung** und dann **Weiter aus.**</span><span class="sxs-lookup"><span data-stu-id="a5fec-126">On the **Add capabilities** screen, select **Messaging Extension** then **Next**.</span></span>
1. <span data-ttu-id="a5fec-127">Geben Sie einen Namen für Ihre Teams-App ein.</span><span class="sxs-lookup"><span data-stu-id="a5fec-127">Enter a name for your Teams app.</span></span> <span data-ttu-id="a5fec-128">(Dies ist der Standardname für Ihre App und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.)</span><span class="sxs-lookup"><span data-stu-id="a5fec-128">(This is the default name for your app and also the name of the app project directory on your local machine.)</span></span>
1. <span data-ttu-id="a5fec-129">Gehen Sie auf dem Bildschirm **Messagingerweiterung** konfigurieren wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="a5fec-129">On the **Configure messaging extension** screen, do the following:</span></span>
    1. <span data-ttu-id="a5fec-130">Wählen Sie nur **die suchbasierte** Option für den Typ der Messagingerweiterung aus.</span><span class="sxs-lookup"><span data-stu-id="a5fec-130">Choose only the **Search-based** option for the type of messaging extension.</span></span>
    1. <span data-ttu-id="a5fec-131">Wählen **Sie Erstellen eines neuen Bots** und dann **Botregistrierung erstellen aus.**</span><span class="sxs-lookup"><span data-stu-id="a5fec-131">Select **Create a new Bot** then **Create Bot Registration**.</span></span> <span data-ttu-id="a5fec-132">Wenn der neue Bot erfolgreich ist, hat er den **Status "Registriert".**</span><span class="sxs-lookup"><span data-stu-id="a5fec-132">If successful, your new bot will have a **Registered** status.</span></span>
    1. <span data-ttu-id="a5fec-133">Wählen Sie im Ersten **Nein** für die Option zum Entf?nden des Links aus.</span><span class="sxs-lookup"><span data-stu-id="a5fec-133">For now, select **No** for the link unfurling option.</span></span>
1. <span data-ttu-id="a5fec-134">Wählen **Sie unten** auf dem Bildschirm Fertig stellen aus, um Ihr Projekt zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="a5fec-134">Select **Finish** at the bottom of the screen to configure your project.</span></span>

## <a name="2-identify-relevant-app-project-components"></a><span data-ttu-id="a5fec-135">2. Identifizieren relevanter App-Projektkomponenten</span><span class="sxs-lookup"><span data-stu-id="a5fec-135">2. Identify relevant app project components</span></span>

<span data-ttu-id="a5fec-136">Viele der App-Konfigurationen und Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Teams Toolkit erstellen.</span><span class="sxs-lookup"><span data-stu-id="a5fec-136">Much of the app configurations and scaffolding are set up automatically when you create your project with the Teams Toolkit.</span></span>

### <a name="app-configurations"></a><span data-ttu-id="a5fec-137">App-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="a5fec-137">App configurations</span></span>

<span data-ttu-id="a5fec-138">Wenn Sie die Konfigurationen Ihrer Messagingerweiterung anzeigen oder aktualisieren möchten, wählen Sie im Toolkit **App Studio aus,** und wechseln Sie zu **Messagingerweiterungen**.</span><span class="sxs-lookup"><span data-stu-id="a5fec-138">To view or update your messaging extension's configurations, select **App Studio** in the toolkit and go to **Messaging extensions**.</span></span>

### <a name="app-scaffolding"></a><span data-ttu-id="a5fec-139">App-Gerüst</span><span class="sxs-lookup"><span data-stu-id="a5fec-139">App scaffolding</span></span>

<span data-ttu-id="a5fec-140">Das App-Gerüst stellt eine Datei im Stammverzeichnis Ihres Projekts zur Verfügung, um zu behandeln, wie Ihre Messagingerweiterung (oder technisch der Bot der Messagingerweiterung) auf Suchabfragen `botActivityHandler.js` in Teams reagiert. [](#4-configure-the-bot-for-your-messaging-extension)</span><span class="sxs-lookup"><span data-stu-id="a5fec-140">The app scaffolding provides a `botActivityHandler.js` file, located in the root directory of your project, for handling how your messaging extension (or technically, the [messaging extension's bot](#4-configure-the-bot-for-your-messaging-extension)) responds to search queries in Teams.</span></span>

## <a name="3-set-up-a-secure-tunnel-to-your-app"></a><span data-ttu-id="a5fec-141">3. Einrichten eines sicheren Tunnels für Ihre App</span><span class="sxs-lookup"><span data-stu-id="a5fec-141">3. Set up a secure tunnel to your app</span></span>

<span data-ttu-id="a5fec-142">Zu Testzwecken hosten wir Ihre Messagingerweiterung auf einem lokalen Webserver (Port 3978).</span><span class="sxs-lookup"><span data-stu-id="a5fec-142">For testing purposes, let's host your messaging extension on a local web server (port 3978).</span></span>

1. <span data-ttu-id="a5fec-143">Falls noch nicht, installieren Sie [ngrok](https://ngrok.com/download).</span><span class="sxs-lookup"><span data-stu-id="a5fec-143">If you haven't already, install [ngrok](https://ngrok.com/download).</span></span>
1. <span data-ttu-id="a5fec-144">Führen Sie in einem Terminal `ngrok http -host-header=rewrite 3978` aus.</span><span class="sxs-lookup"><span data-stu-id="a5fec-144">In a terminal, run `ngrok http -host-header=rewrite 3978`.</span></span>
1. <span data-ttu-id="a5fec-145">Kopieren Sie die HTTPS-URL in der Ausgabe (z. B. `https://468b9ab725e9.ngrok.io` ), da Teams HTTPS-Verbindungen erfordert.</span><span class="sxs-lookup"><span data-stu-id="a5fec-145">Copy the HTTPS URL in the output (for example, `https://468b9ab725e9.ngrok.io`) since Teams requires HTTPS connections.</span></span>

<span data-ttu-id="a5fec-146">Mit dieser URL kann Teams (für die HTTPS-Verbindungen erforderlich sind) zu dem Ort tunneln, an dem Sie Ihre App hosten ( `localhost` an Port 3978).</span><span class="sxs-lookup"><span data-stu-id="a5fec-146">With this URL, Teams (which requires HTTPS connections) will be able tunnel to where you're hosting your app (`localhost` on port 3978).</span></span>

## <a name="4-configure-the-bot-for-your-messaging-extension"></a><span data-ttu-id="a5fec-147">4. Konfigurieren des Bots für Ihre Messagingerweiterung</span><span class="sxs-lookup"><span data-stu-id="a5fec-147">4. Configure the bot for your messaging extension</span></span>

<span data-ttu-id="a5fec-148">Messagingerweiterungen verwenden Bots, um Benutzeranforderungen von Teams an Ihren gehosteten Dienst zu senden und zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="a5fec-148">Messaging extensions rely on bots to send and process user requests from Teams to your hosted service.</span></span> <span data-ttu-id="a5fec-149">Der Bot muss beim Azure Bot Service registriert sein, was beim Einrichten Ihrer App mithilfe des Teams Toolkits erfolgt ist.</span><span class="sxs-lookup"><span data-stu-id="a5fec-149">The bot must be registered with the Azure Bot Service, which was done when you set up your app using the Teams Toolkit.</span></span>

<span data-ttu-id="a5fec-150">Sie müssen weiterhin eine Botendpunkt-URL angeben, um Suchabfragen in Ihrer Messagingerweiterung zu empfangen und zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="a5fec-150">You still must specify a bot endpoint URL to receive and process search queries in your messaging extension.</span></span> <span data-ttu-id="a5fec-151">In der Regel sieht die URL wie `https://HOST_URL/api/messages` aus.</span><span class="sxs-lookup"><span data-stu-id="a5fec-151">Typically, the URL looks like `https://HOST_URL/api/messages`.</span></span> <span data-ttu-id="a5fec-152">Sie können dies schnell im Toolkit konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="a5fec-152">You can configure this quickly in the toolkit.</span></span>

1. Wählen Visual Studio Code auf der linken Aktivitätsleiste **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: aus, und wählen Sie Microsoft Teams Toolkit **öffnen aus.**
1. <span data-ttu-id="a5fec-154">Wechseln Sie **zu Bots > vorhandenen Botregistrierungen,** und wählen Sie den Bot aus, den Sie während des Setups erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="a5fec-154">Go to **Bots > Existing bot registrations** and select the bot you created during setup.</span></span>
1. <span data-ttu-id="a5fec-155">Geben Sie im Feld **Bot-Endpunktadresse** die ngrok-URL (z. B. ) ein, in der Sie den Bot hosten, und `https://468b9ab725e9.ngrok.io` fügen Sie ihn `/api/messages` an.</span><span class="sxs-lookup"><span data-stu-id="a5fec-155">In the **Bot endpoint address** field, enter the ngrok URL (for example, `https://468b9ab725e9.ngrok.io`) where you're hosting the bot and append `/api/messages` to it.</span></span>

<span data-ttu-id="a5fec-156">Ihr Bot kann Abfragen in Ihrer Messagingerweiterung verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="a5fec-156">Your bot will be able to handle queries in your messaging extension.</span></span>

## <a name="5-build-and-run-your-app"></a><span data-ttu-id="a5fec-157">5. Erstellen und Ausführen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="a5fec-157">5. Build and run your app</span></span>

<span data-ttu-id="a5fec-158">Sie haben eine URL zum Hosten Ihrer Messagingerweiterung eingerichtet und für die Verarbeitung von Suchen konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="a5fec-158">You've set up a URL to host your messaging extension and configured it to handle searches.</span></span> <span data-ttu-id="a5fec-159">Es ist an der Zeit, Ihre App in Betrieb zu halten.</span><span class="sxs-lookup"><span data-stu-id="a5fec-159">It's time to get your app up and running.</span></span>

1. <span data-ttu-id="a5fec-160">Wechseln Sie in einem Terminal zum Stammverzeichnis Ihres App-Projekts, und führen Sie `npm install` aus.</span><span class="sxs-lookup"><span data-stu-id="a5fec-160">In a terminal, go to the root directory of your app project and run `npm install`.</span></span>
1. <span data-ttu-id="a5fec-161">Führen Sie `npm start` aus.</span><span class="sxs-lookup"><span data-stu-id="a5fec-161">Run `npm start`.</span></span>

<span data-ttu-id="a5fec-162">Wenn dies erfolgreich ist, wird die folgende Meldung angezeigt, die angibt, dass Ihr Messagingerweiterungsdienst aktivitäten bei Ihrer `localhost` abhört:</span><span class="sxs-lookup"><span data-stu-id="a5fec-162">If successful, you see the following message indicating your messaging extension service is listening for activity at your `localhost`:</span></span>

`Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-messaging-extension-in-teams"></a><span data-ttu-id="a5fec-163">6. Querladen Ihrer Messagingerweiterung in Teams</span><span class="sxs-lookup"><span data-stu-id="a5fec-163">6. Sideload your messaging extension in Teams</span></span>

<span data-ttu-id="a5fec-164">Wenn Ihre Messagingerweiterung ausgeführt wird, können Sie sie in Teams installieren.</span><span class="sxs-lookup"><span data-stu-id="a5fec-164">With your messaging extension running, you can install it in Teams.</span></span>

> [!TIP]
> <span data-ttu-id="a5fec-165">Wenn Sie eine Teams-App noch nicht nebeneinander geladen haben und Probleme auftreten, führen Sie diese [Anweisungen aus.](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams)</span><span class="sxs-lookup"><span data-stu-id="a5fec-165">If you haven't sideloaded a Teams app before and run into issues, follow these [instructions](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams).</span></span>

1. <span data-ttu-id="a5fec-166">Drücken Visual Studio Code die **F5-TASTE,** um einen Teams-Webclient zu starten.</span><span class="sxs-lookup"><span data-stu-id="a5fec-166">In Visual Studio Code, press the **F5** key to launch a Teams web client.</span></span>
1. <span data-ttu-id="a5fec-167">Wählen Sie im Dialogfeld App-Installation die Option **Für mich hinzufügen aus.**</span><span class="sxs-lookup"><span data-stu-id="a5fec-167">In the app install dialog, select **Add for me**.</span></span>

## <a name="7-test-your-messaging-extension"></a><span data-ttu-id="a5fec-168">7. Testen Der Messagingerweiterung</span><span class="sxs-lookup"><span data-stu-id="a5fec-168">7. Test your messaging extension</span></span>

<span data-ttu-id="a5fec-169">Erfahren Sie, wie Messagingerweiterungen in einem Teams-Chat funktionieren.</span><span class="sxs-lookup"><span data-stu-id="a5fec-169">Learn how messaging extensions work in a Teams chat.</span></span>

1. <span data-ttu-id="a5fec-170">Starten Sie einen neuen Chat.</span><span class="sxs-lookup"><span data-stu-id="a5fec-170">Start a new chat.</span></span> Wählen Sie im Feld Verfassen die Option **Mehr** :::image type="icon" source="../assets/icons/teams-client-more.png"::: aus, und wählen Sie die Messagingerweiterungs-App aus, die Sie gerade seitengeladen haben.
1. <span data-ttu-id="a5fec-172">Versuchen Sie, nach etwas zu suchen (z. B. **Tickets**).</span><span class="sxs-lookup"><span data-stu-id="a5fec-172">Try searching for something (for example, **Tickets**).</span></span> <span data-ttu-id="a5fec-173">Wenn Ihre App funktioniert, werden Beispielsuchergebnisse angezeigt (Sie können ihre eigenen später hinzufügen).</span><span class="sxs-lookup"><span data-stu-id="a5fec-173">If your app is working, you'll see sample search results (you can add your own later).</span></span><br/>
   :::image type="content" source="../assets/images/build-your-first-app/me-teams-test.png" alt-text="Ein Screenshot, der zeigt, wie eine suchbasierte Messagingerweiterung im Feld Teams verfassen verwendet wird.":::

## <a name="well-done"></a><span data-ttu-id="a5fec-175">Gut gemacht</span><span class="sxs-lookup"><span data-stu-id="a5fec-175">Well done</span></span>

<span data-ttu-id="a5fec-176">Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="a5fec-176">Congratulations!</span></span> <span data-ttu-id="a5fec-177">Sie verfügen über eine grundlegende Teams-Messagingerweiterung, die für die Suche nach externen Inhalten im Verfassen- oder Befehlsfeld eingerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="a5fec-177">You have a basic Teams messaging extension that's set up to search for external content in the compose or command box.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a5fec-178">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="a5fec-178">Next steps</span></span>

<span data-ttu-id="a5fec-179">Weitere Informationen zum Erstellen einer voll funktionsfähigen Messagingerweiterung finden Sie auf den folgenden Seiten:</span><span class="sxs-lookup"><span data-stu-id="a5fec-179">See the following pages to continue and build a fully featured messaging extension:</span></span>

1. <span data-ttu-id="a5fec-180">[Definieren Sie Suchbefehle,](../messaging-extensions/how-to/search-commands/define-search-command.md) die für Ihren Dienst relevant sind.</span><span class="sxs-lookup"><span data-stu-id="a5fec-180">[Define search commands](../messaging-extensions/how-to/search-commands/define-search-command.md) that are relevant to your service.</span></span>
1. <span data-ttu-id="a5fec-181">Konfigurieren Sie Ihren Dienst [so, dass er auf benutzersuchen reagiert.](../messaging-extensions/how-to/search-commands/respond-to-search.md)</span><span class="sxs-lookup"><span data-stu-id="a5fec-181">Configure your service to [respond to users' searches](../messaging-extensions/how-to/search-commands/respond-to-search.md).</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="a5fec-182">Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="a5fec-182">Troubleshooting</span></span>

<span data-ttu-id="a5fec-183">Die folgenden Informationen können hilfreich sein, wenn Beim Abschließen dieses Lernprogramms Probleme auftreten.</span><span class="sxs-lookup"><span data-stu-id="a5fec-183">The following information may help if you had issues completing this tutorial.</span></span>

### <a name="bot-isnt-connected-to-teams"></a><span data-ttu-id="a5fec-184">Bot ist nicht mit Teams verbunden</span><span class="sxs-lookup"><span data-stu-id="a5fec-184">Bot isn't connected to Teams</span></span>

<span data-ttu-id="a5fec-185">Wenn Sie Ihre App installiert haben, aber nicht funktioniert, stellen Sie sicher, dass der Bot der Messagingerweiterung mit dem Teams-Kanal des [Azure Bot Service verbunden *ist.*](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="a5fec-185">If you installed your app but it isn't working, make sure the messaging extension's bot is [connected to the Azure Bot Service's Teams *channel*](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true).</span></span>

<span data-ttu-id="a5fec-186">Es ist wichtig zu wissen, dass dies nicht mit einem Kanal in Teams identisch ist.</span><span class="sxs-lookup"><span data-stu-id="a5fec-186">It's important to understand that this isn't the same as a channel in Teams.</span></span> <span data-ttu-id="a5fec-187">In diesem Fall verbindet der Azure Bot Service Ihren Bot mit Teams oder einer anderen unterstützten Microsoft- oder [Drittanbieter-Kommunikations-App.](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="a5fec-187">In this case, a channel is how the Azure Bot Service connects your bot to Teams or another [supported Microsoft or third-party communications app](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span>

## <a name="learn-more"></a><span data-ttu-id="a5fec-188">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="a5fec-188">Learn more</span></span>

* [<span data-ttu-id="a5fec-189">Schließen Sie ein Feature zum Entfingen eines Links ein.</span><span class="sxs-lookup"><span data-stu-id="a5fec-189">Include a link unfurling feature</span></span>](../messaging-extensions/how-to/link-unfurling.md)
* <span data-ttu-id="a5fec-190">Befolgen Sie [unsere Entwurfsrichtlinien,](../messaging-extensions/design/messaging-extension-design.md) und erstellen Sie mit [produktionsbereiten](../concepts/design/design-teams-app-ui-templates.md) Benutzeroberflächenvorlagen, um eine nahtlose Oberfläche zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="a5fec-190">Follow our [design guidelines](../messaging-extensions/design/messaging-extension-design.md) and build with [production-ready UI templates](../concepts/design/design-teams-app-ui-templates.md) to create a seamless experience.</span></span>
* [<span data-ttu-id="a5fec-191">Authentifizierung hinzufügen</span><span class="sxs-lookup"><span data-stu-id="a5fec-191">Add authentication</span></span>](../messaging-extensions/how-to/add-authentication.md)
* [<span data-ttu-id="a5fec-192">Erstellen einer aktionsbasierten Messagingerweiterung</span><span class="sxs-lookup"><span data-stu-id="a5fec-192">Create an action-based messaging extension</span></span>](../messaging-extensions/how-to/action-commands/define-action-command.md)
* [<span data-ttu-id="a5fec-193">Microsoft Bot Framework</span><span class="sxs-lookup"><span data-stu-id="a5fec-193">Microsoft Bot Framework</span></span>](https://dev.botframework.com/)

