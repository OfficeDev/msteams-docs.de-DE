---
title: Erste Schritte – Erstellen einer Messaging Erweiterung
author: heath-hamilton
description: Erstellen Sie mit dem Microsoft Teams-Toolkit schnell eine Microsoft Teams-Messaging Erweiterung.
ms.author: lajanuar
ms.date: 11/04/2020
ms.topic: tutorial
ms.openlocfilehash: 160878d92969d57680e6fa25eb6fc13e82bf2a82
ms.sourcegitcommit: 99c35de7e2c604bd8bce392242c2c2fa709cd50b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2020
ms.locfileid: "48931750"
---
# <a name="build-a-messaging-extension-for-microsoft-teams"></a><span data-ttu-id="405e5-103">Erstellen einer Messaging Erweiterung für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="405e5-103">Build a messaging extension for Microsoft Teams</span></span>

<span data-ttu-id="405e5-104">Es gibt zwei Typen von Teams-APP- *Messaging-Erweiterungen* : [Suchbefehle](../messaging-extensions/how-to/search-commands/define-search-command.md) und [Aktionsbefehle](../messaging-extensions/how-to/action-commands/define-action-command.md).</span><span class="sxs-lookup"><span data-stu-id="405e5-104">There are two types of Teams app *messaging extensions* : [Search commands](../messaging-extensions/how-to/search-commands/define-search-command.md) and [action commands](../messaging-extensions/how-to/action-commands/define-action-command.md).</span></span>

<span data-ttu-id="405e5-105">In dieser Lektion erstellen Sie einen *Suchbefehl* (auch als *Suchbasierte Messaging Erweiterung* bezeichnet), bei dem es sich um eine Verknüpfung zum Suchen externer Inhalte und deren Freigabe in Microsoft Teams handelt.</span><span class="sxs-lookup"><span data-stu-id="405e5-105">In this lesson, you'll create a *search command* (also known as a *search-based messaging extension* ), which is a shortcut for finding external content and sharing it in Teams.</span></span> <span data-ttu-id="405e5-106">Benutzer können über das [Feld Verfassen oder Ausführen des Teams](../messaging-extensions/what-are-messaging-extensions.md)auf Suchbefehle zugreifen.</span><span class="sxs-lookup"><span data-stu-id="405e5-106">Users can access search commands from the [Teams compose or command box](../messaging-extensions/what-are-messaging-extensions.md).</span></span>

## <a name="your-assignment"></a><span data-ttu-id="405e5-107">Ihre Zuordnung</span><span class="sxs-lookup"><span data-stu-id="405e5-107">Your assignment</span></span>

<span data-ttu-id="405e5-108">Das Helpdesk Ihrer Organisation kommuniziert mit Benutzern über Teams, die Tickets befinden sich jedoch in einem separaten System.</span><span class="sxs-lookup"><span data-stu-id="405e5-108">Your organization's help desk communicates with users through Teams, but the tickets reside in a separate system.</span></span> <span data-ttu-id="405e5-109">Dies bedeutet, dass Supportmitarbeiter ständig zwischen apps hin und her wechseln müssen.</span><span class="sxs-lookup"><span data-stu-id="405e5-109">This means support staff must constantly go back and forth between apps.</span></span> <span data-ttu-id="405e5-110">Sie werden untersuchen, wie Sie diese vielseitige Kontext Umstellung reduzieren können, indem Sie eine einfache suchbasierte Messaging Erweiterung für Teams erstellen.</span><span class="sxs-lookup"><span data-stu-id="405e5-110">You'll investigate how you might reduce this much context switching by creating a simple search-based messaging extension for Teams.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="405e5-111">Was Sie lernen</span><span class="sxs-lookup"><span data-stu-id="405e5-111">What you'll learn</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="405e5-112">Erstellen eines App-Projekts und eines bot für die Messaging Erweiterung mithilfe des Microsoft Teams-Toolkits für Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="405e5-112">Create an app project and messaging extension bot using the Microsoft Teams Toolkit for Visual Studio Code</span></span>
> * <span data-ttu-id="405e5-113">Identifizieren der APP-Konfigurationen und einiger der für Messaging-Erweiterungen relevanten Gerüste</span><span class="sxs-lookup"><span data-stu-id="405e5-113">Identify the app configurations and some of the scaffolding relevant to messaging extensions</span></span>
> * <span data-ttu-id="405e5-114">Lokal Hosten einer APP</span><span class="sxs-lookup"><span data-stu-id="405e5-114">Host an app locally</span></span>
> * <span data-ttu-id="405e5-115">Konfigurieren des bot für Ihre Messaging Erweiterung</span><span class="sxs-lookup"><span data-stu-id="405e5-115">Configure the bot for your messaging extension</span></span>
> * <span data-ttu-id="405e5-116">Querladen und Testen einer Messaging Erweiterung in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="405e5-116">Sideload and test a messaging extension in Teams</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="405e5-117">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="405e5-117">Before you begin</span></span>

<span data-ttu-id="405e5-118">Wenn Sie noch nicht vorhanden sind, stellen Sie sicher, dass Sie [die Entwicklungsvoraussetzungen für Teams kennen und installieren](build-first-app-overview.md#get-prerequisites).</span><span class="sxs-lookup"><span data-stu-id="405e5-118">If you haven't yet, make sure you [understand and install the Teams development prerequisites](build-first-app-overview.md#get-prerequisites).</span></span>

## <a name="1-create-your-app-project"></a><span data-ttu-id="405e5-119">1. Erstellen des App-Projekts</span><span class="sxs-lookup"><span data-stu-id="405e5-119">1. Create your app project</span></span>

<span data-ttu-id="405e5-120">Das Microsoft Teams-Toolkit hilft Ihnen beim Einrichten der folgenden Komponenten für Ihre Messaging-Erweiterung:</span><span class="sxs-lookup"><span data-stu-id="405e5-120">The Microsoft Teams Toolkit helps you set up the following components for your messaging extension:</span></span>

* <span data-ttu-id="405e5-121">Für Messaging-Erweiterungen relevantes **App-Konfigurationen und Gerüste**</span><span class="sxs-lookup"><span data-stu-id="405e5-121">**App configurations and scaffolding** relevant to messaging extensions</span></span>
* <span data-ttu-id="405e5-122">**Bot** für Ihre Messaging-Erweiterung, die automatisch beim Microsoft Azure bot-Dienst registriert wird</span><span class="sxs-lookup"><span data-stu-id="405e5-122">**Bot** for your messaging extension that's automatically registered with the Microsoft Azure Bot Service</span></span>

> [!TIP]
> <span data-ttu-id="405e5-123">Wenn Sie noch kein Teams-App-Projekt erstellt haben, ist es möglicherweise hilfreich, [diese Anweisungen](../build-your-first-app/build-and-run.md) zu befolgen, mit denen Projekte detaillierter erläutert werden.</span><span class="sxs-lookup"><span data-stu-id="405e5-123">If you haven't created a Teams app project before, you might find it helpful to follow [these instructions](../build-your-first-app/build-and-run.md) that explain projects in more detail.</span></span>

1. Wählen Sie in Visual Studio Code **Microsoft Teams** in :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: der linken Aktivitäts Leiste aus, und wählen Sie **neue Teams-app erstellen** aus.
1. <span data-ttu-id="405e5-125">Wenn Sie dazu aufgefordert werden, melden Sie sich mit Ihrem Microsoft 365-entwicklungskonto an.</span><span class="sxs-lookup"><span data-stu-id="405e5-125">When prompted, sign in with your Microsoft 365 development account.</span></span>
1. <span data-ttu-id="405e5-126">Wählen Sie auf dem Bildschirm **Funktionen hinzufügen** die Option **Messaging Erweiterung** und dann dann **weiter** aus.</span><span class="sxs-lookup"><span data-stu-id="405e5-126">On the **Add capabilities** screen, select **Messaging Extension** then **Next**.</span></span>
1. <span data-ttu-id="405e5-127">Geben Sie einen Namen für Ihre Teams-App ein.</span><span class="sxs-lookup"><span data-stu-id="405e5-127">Enter a name for your Teams app.</span></span> <span data-ttu-id="405e5-128">(Dies ist der Standardname für Ihre APP und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.)</span><span class="sxs-lookup"><span data-stu-id="405e5-128">(This is the default name for your app and also the name of the app project directory on your local machine.)</span></span>
1. <span data-ttu-id="405e5-129">Führen Sie auf dem Bildschirm **Messaging-Erweiterung konfigurieren** die folgenden Aktionen aus:</span><span class="sxs-lookup"><span data-stu-id="405e5-129">On the **Configure messaging extension** screen, do the following:</span></span>
    1. <span data-ttu-id="405e5-130">Wählen Sie nur die **Suchbasierte** Option für den Typ der Messaging Erweiterung aus.</span><span class="sxs-lookup"><span data-stu-id="405e5-130">Choose only the **Search-based** option for the type of messaging extension.</span></span>
    1. <span data-ttu-id="405e5-131">Wählen Sie **Create a New bot** aus, und erstellen Sie dann die **bot-Registrierung**.</span><span class="sxs-lookup"><span data-stu-id="405e5-131">Select **Create a new Bot** then **Create Bot Registration**.</span></span> <span data-ttu-id="405e5-132">Wenn die Methode erfolgreich verläuft, wird Ihr neuer bot einen **registrierten** Status haben.</span><span class="sxs-lookup"><span data-stu-id="405e5-132">If successful, your new bot will have a **Registered** status.</span></span>
    1. <span data-ttu-id="405e5-133">Wählen Sie im Moment **Nein** für die Option zum Aufheben der Verknüpfung aus.</span><span class="sxs-lookup"><span data-stu-id="405e5-133">For now, select **No** for the link unfurling option.</span></span>
1. <span data-ttu-id="405e5-134">Klicken Sie unten auf dem Bildschirm auf **Fertig stellen** , um Ihr Projekt zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="405e5-134">Select **Finish** at the bottom of the screen to configure your project.</span></span>

## <a name="2-identify-relevant-app-project-components"></a><span data-ttu-id="405e5-135">2. Identifizieren der relevanten App-Projektkomponenten</span><span class="sxs-lookup"><span data-stu-id="405e5-135">2. Identify relevant app project components</span></span>

<span data-ttu-id="405e5-136">Viele der APP-Konfigurationen und Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Teams-Toolkit erstellen.</span><span class="sxs-lookup"><span data-stu-id="405e5-136">Much of the app configurations and scaffolding are set up automatically when you create your project with the Teams Toolkit.</span></span>

### <a name="app-configurations"></a><span data-ttu-id="405e5-137">App-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="405e5-137">App configurations</span></span>

<span data-ttu-id="405e5-138">Um die Konfigurationen Ihrer Messaging Erweiterung anzuzeigen oder zu aktualisieren, wählen Sie **App Studio** im Toolkit aus, und wechseln Sie zu **Messaging Erweiterungen**.</span><span class="sxs-lookup"><span data-stu-id="405e5-138">To view or update your messaging extension's configurations, select **App Studio** in the toolkit and go to **Messaging extensions**.</span></span>

### <a name="app-scaffolding"></a><span data-ttu-id="405e5-139">App-Gerüste</span><span class="sxs-lookup"><span data-stu-id="405e5-139">App scaffolding</span></span>

<span data-ttu-id="405e5-140">Das App-Gerüst stellt eine `botActivityHandler.js` Datei bereit, die sich im Stammverzeichnis des Projekts befindet, um zu behandeln, wie Ihre Messaging-Erweiterung (oder technisch gesehen, der [bot der Messaging Erweiterung](#4-configure-the-bot-for-your-messaging-extension)) auf Suchabfragen in Microsoft Teams reagiert.</span><span class="sxs-lookup"><span data-stu-id="405e5-140">The app scaffolding provides a `botActivityHandler.js` file, located in the root directory of your project, for handling how your messaging extension (or technically, the [messaging extension's bot](#4-configure-the-bot-for-your-messaging-extension)) responds to search queries in Teams.</span></span>

## <a name="3-set-up-a-secure-tunnel-to-your-app"></a><span data-ttu-id="405e5-141">3. Einrichten eines sicheren Tunnels für Ihre APP</span><span class="sxs-lookup"><span data-stu-id="405e5-141">3. Set up a secure tunnel to your app</span></span>

<span data-ttu-id="405e5-142">Zu Testzwecken hosten wir Ihre Messaging-Erweiterung auf einem lokalen Webserver (Port 3978).</span><span class="sxs-lookup"><span data-stu-id="405e5-142">For testing purposes, let's host your messaging extension on a local web server (port 3978).</span></span>

1. <span data-ttu-id="405e5-143">Wenn Sie noch nicht vorhanden sind, installieren Sie [ngrok](https://ngrok.com/download).</span><span class="sxs-lookup"><span data-stu-id="405e5-143">If you haven't already, install [ngrok](https://ngrok.com/download).</span></span>
1. <span data-ttu-id="405e5-144">Führen Sie in einem Terminal aus `ngrok http -host-header=rewrite 3978` .</span><span class="sxs-lookup"><span data-stu-id="405e5-144">In a terminal, run `ngrok http -host-header=rewrite 3978`.</span></span>
1. <span data-ttu-id="405e5-145">Kopieren Sie die HTTPS-URL in der Ausgabe (beispielsweise `https://468b9ab725e9.ngrok.io` ), da für Teams HTTPS-Verbindungen erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="405e5-145">Copy the HTTPS URL in the output (for example, `https://468b9ab725e9.ngrok.io`) since Teams requires HTTPS connections.</span></span>

<span data-ttu-id="405e5-146">Mit dieser URL können Teams (für die HTTPS-Verbindungen erforderlich sind) in der Lage sein, zu dem Ort zu gelangen, an dem Sie Ihre APP hosten ( `localhost` auf Port 3978).</span><span class="sxs-lookup"><span data-stu-id="405e5-146">With this URL, Teams (which requires HTTPS connections) will be able tunnel to where you're hosting your app (`localhost` on port 3978).</span></span>

## <a name="4-configure-the-bot-for-your-messaging-extension"></a><span data-ttu-id="405e5-147">4. Konfigurieren des bot für Ihre Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="405e5-147">4. Configure the bot for your messaging extension</span></span>

<span data-ttu-id="405e5-148">Messaging-Erweiterungen beruhen darauf, dass Bots Benutzeranforderungen von Teams an den gehosteten Dienst senden und verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="405e5-148">Messaging extensions rely on bots to send and process user requests from Teams to your hosted service.</span></span> <span data-ttu-id="405e5-149">Der bot muss mit dem Azure bot-Dienst registriert werden, der beim Einrichten Ihrer APP mit dem Teams-Toolkit ausgeführt wurde.</span><span class="sxs-lookup"><span data-stu-id="405e5-149">The bot must be registered with the Azure Bot Service, which was done when you set up your app using the Teams Toolkit.</span></span>

<span data-ttu-id="405e5-150">Sie müssen immer noch eine bot-Endpunkt-URL angeben, um Suchabfragen in Ihrer Messaging-Erweiterung zu empfangen und zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="405e5-150">You still must specify a bot endpoint URL to receive and process search queries in your messaging extension.</span></span> <span data-ttu-id="405e5-151">Normalerweise sieht die URL wie aus `https://HOST_URL/api/messages` .</span><span class="sxs-lookup"><span data-stu-id="405e5-151">Typically, the URL looks like `https://HOST_URL/api/messages`.</span></span> <span data-ttu-id="405e5-152">Sie können diese schnell im Toolkit konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="405e5-152">You can configure this quickly in the toolkit.</span></span>

1. Wählen Sie in Visual Studio Code **Microsoft Teams** in :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: der linken Aktivitäts Leiste aus, und wählen Sie **Microsoft Teams Toolkit öffnen** aus.
1. <span data-ttu-id="405e5-154">Wechseln Sie zu **Bots > vorhandene bot-Registrierungen** , und wählen Sie den bot aus, den Sie während des Setups erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="405e5-154">Go to **Bots > Existing bot registrations** and select the bot you created during setup.</span></span>
1. <span data-ttu-id="405e5-155">Geben Sie im Feld **bot-Endpunktadresse** die ngrok-URL (beispielsweise) ein, in der `https://468b9ab725e9.ngrok.io` Sie den bot hosten und `/api/messages` an ihn anfügen.</span><span class="sxs-lookup"><span data-stu-id="405e5-155">In the **Bot endpoint address** field, enter the ngrok URL (for example, `https://468b9ab725e9.ngrok.io`) where you're hosting the bot and append `/api/messages` to it.</span></span>

<span data-ttu-id="405e5-156">Ihr bot ist in der Lage, Abfragen in Ihrer Messaging-Erweiterung zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="405e5-156">Your bot will be able to handle queries in your messaging extension.</span></span>

## <a name="5-build-and-run-your-app"></a><span data-ttu-id="405e5-157">5. erstellen und Ausführen der APP</span><span class="sxs-lookup"><span data-stu-id="405e5-157">5. Build and run your app</span></span>

<span data-ttu-id="405e5-158">Sie haben eine URL eingerichtet, die Ihre Messaging-Erweiterung hostet und für die Verarbeitung von Suchvorgängen konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="405e5-158">You've set up a URL to host your messaging extension and configured it to handle searches.</span></span> <span data-ttu-id="405e5-159">Es ist an der Zeit, Ihre APP in Betrieb zu nehmen.</span><span class="sxs-lookup"><span data-stu-id="405e5-159">It's time to get your app up and running.</span></span>

1. <span data-ttu-id="405e5-160">Wechseln Sie in einem Terminal zum Stammverzeichnis des App-Projekts, und führen Sie es aus `npm install` .</span><span class="sxs-lookup"><span data-stu-id="405e5-160">In a terminal, go to the root directory of your app project and run `npm install`.</span></span>
1. <span data-ttu-id="405e5-161">Ausführen `npm start` .</span><span class="sxs-lookup"><span data-stu-id="405e5-161">Run `npm start`.</span></span>

<span data-ttu-id="405e5-162">Wenn die Funktion erfolgreich verläuft, wird die folgende Meldung angezeigt, die besagt, dass Ihr Messaging-Erweiterungsdienst bei Ihrem `localhost` Folgendes überwacht:</span><span class="sxs-lookup"><span data-stu-id="405e5-162">If successful, you see the following message indicating your messaging extension service is listening for activity at your `localhost`:</span></span>

`Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-messaging-extension-in-teams"></a><span data-ttu-id="405e5-163">6. querladen Ihrer Messaging Erweiterung in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="405e5-163">6. Sideload your messaging extension in Teams</span></span>

<span data-ttu-id="405e5-164">Wenn Ihre Messaging-Erweiterung aktiv ist, können Sie Sie in Microsoft Teams installieren.</span><span class="sxs-lookup"><span data-stu-id="405e5-164">With your messaging extension running, you can install it in Teams.</span></span>

> [!TIP]
> <span data-ttu-id="405e5-165">Wenn Sie noch keine Teams-App quer geladene haben und Probleme haben, führen Sie die folgenden [Schritte](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams)aus.</span><span class="sxs-lookup"><span data-stu-id="405e5-165">If you haven't sideloaded a Teams app before and run into issues, follow these [instructions](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams).</span></span>

1. <span data-ttu-id="405e5-166">Drücken Sie in Visual Studio Code die **F5** -Taste, um einen Microsoft Teams-WebClient zu starten.</span><span class="sxs-lookup"><span data-stu-id="405e5-166">In Visual Studio Code, press the **F5** key to launch a Teams web client.</span></span>
1. <span data-ttu-id="405e5-167">Wählen Sie im Dialogfeld App-Installation die Option **für mich hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="405e5-167">In the app install dialog, select **Add for me**.</span></span>

## <a name="7-test-your-messaging-extension"></a><span data-ttu-id="405e5-168">7. Testen der Messaging Erweiterung</span><span class="sxs-lookup"><span data-stu-id="405e5-168">7. Test your messaging extension</span></span>

<span data-ttu-id="405e5-169">Erfahren Sie, wie Messaging-Erweiterungen in einem Microsoft Teams-Chat funktionieren.</span><span class="sxs-lookup"><span data-stu-id="405e5-169">Learn how messaging extensions work in a Teams chat.</span></span>

1. <span data-ttu-id="405e5-170">Starten Sie einen neuen Chat.</span><span class="sxs-lookup"><span data-stu-id="405e5-170">Start a new chat.</span></span> Wählen Sie im Feld Verfassen die Option **Weitere** aus, :::image type="icon" source="../assets/icons/teams-client-more.png"::: und wählen Sie die soeben quer geladene Messaging-Erweiterungs-App aus.
1. <span data-ttu-id="405e5-172">Suchen Sie nach etwas (beispielsweise **Tickets** ).</span><span class="sxs-lookup"><span data-stu-id="405e5-172">Try searching for something (for example, **Tickets** ).</span></span> <span data-ttu-id="405e5-173">Wenn Ihre APP funktioniert, werden Beispiel Suchergebnisse angezeigt (Sie können Sie später hinzufügen).</span><span class="sxs-lookup"><span data-stu-id="405e5-173">If your app is working, you'll see sample search results (you can add your own later).</span></span><br/>
   :::image type="content" source="../assets/images/build-your-first-app/me-teams-test.png" alt-text="Ein Screenshot, der zeigt, wie eine suchbasierte Messaging Erweiterung im Feld _OL_QUOTE_PLACEHOLDER_Teams erstellen_OL_QUOTE_PLACEHOLDER_ verwendet wird.":::

## <a name="well-done"></a><span data-ttu-id="405e5-175">Gut gemacht</span><span class="sxs-lookup"><span data-stu-id="405e5-175">Well done</span></span>

<span data-ttu-id="405e5-176">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="405e5-176">Congratulations!</span></span> <span data-ttu-id="405e5-177">Sie verfügen über eine Standard-Microsoft Teams-Messaging Erweiterung, die für die Suche nach externem Inhalt im Feld Verfassen oder Befehl eingerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="405e5-177">You have a basic Teams messaging extension that's set up to search for external content in the compose or command box.</span></span>

## <a name="next-steps"></a><span data-ttu-id="405e5-178">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="405e5-178">Next steps</span></span>

<span data-ttu-id="405e5-179">Auf den folgenden Seiten können Sie fortfahren und eine vollständig ausgestattete Messaging Erweiterung erstellen:</span><span class="sxs-lookup"><span data-stu-id="405e5-179">See the following pages to continue and build a fully featured messaging extension:</span></span>

1. <span data-ttu-id="405e5-180">[Definieren Sie Suchbefehle](../messaging-extensions/how-to/search-commands/define-search-command.md) , die für Ihren Dienst relevant sind.</span><span class="sxs-lookup"><span data-stu-id="405e5-180">[Define search commands](../messaging-extensions/how-to/search-commands/define-search-command.md) that are relevant to your service.</span></span>
1. <span data-ttu-id="405e5-181">Konfigurieren Sie den Dienst so, dass er [auf die Suchvorgänge von Benutzern reagiert](../messaging-extensions/how-to/search-commands/respond-to-search.md).</span><span class="sxs-lookup"><span data-stu-id="405e5-181">Configure your service to [respond to users' searches](../messaging-extensions/how-to/search-commands/respond-to-search.md).</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="405e5-182">Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="405e5-182">Troubleshooting</span></span>

<span data-ttu-id="405e5-183">Die folgenden Informationen können hilfreich sein, wenn beim Abschluss dieses Lernprogramms Probleme aufgetreten sind.</span><span class="sxs-lookup"><span data-stu-id="405e5-183">The following information may help if you had issues completing this tutorial.</span></span>

### <a name="bot-isnt-connected-to-teams"></a><span data-ttu-id="405e5-184">Bot ist nicht mit Microsoft Teams verbunden</span><span class="sxs-lookup"><span data-stu-id="405e5-184">Bot isn't connected to Teams</span></span>

<span data-ttu-id="405e5-185">Wenn Sie Ihre APP installiert haben, aber nicht funktioniert, stellen Sie sicher, dass der bot der Messaging Erweiterung [mit dem Microsoft Teams- *Kanal* des Azure bot-Diensts verbunden](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true)ist.</span><span class="sxs-lookup"><span data-stu-id="405e5-185">If you installed your app but it isn't working, make sure the messaging extension's bot is [connected to the Azure Bot Service's Teams *channel*](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true).</span></span>

<span data-ttu-id="405e5-186">Es ist wichtig zu verstehen, dass dies nicht mit einem Kanal in Microsoft Teams identisch ist.</span><span class="sxs-lookup"><span data-stu-id="405e5-186">It's important to understand that this isn't the same as a channel in Teams.</span></span> <span data-ttu-id="405e5-187">In diesem Fall stellt ein Kanal dar, wie der Azure bot-Dienst Ihren bot mit Teams oder einer anderen [unterstützten Microsoft-oder Drittanbieter-Kommunikations-App](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)verbindet.</span><span class="sxs-lookup"><span data-stu-id="405e5-187">In this case, a channel is how the Azure Bot Service connects your bot to Teams or another [supported Microsoft or third-party communications app](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span>

## <a name="learn-more"></a><span data-ttu-id="405e5-188">Mehr erfahren</span><span class="sxs-lookup"><span data-stu-id="405e5-188">Learn more</span></span>

* [<span data-ttu-id="405e5-189">Einschließen einer Link-Entfaltungs Funktion</span><span class="sxs-lookup"><span data-stu-id="405e5-189">Include a link unfurling feature</span></span>](../messaging-extensions/how-to/link-unfurling.md)
* [<span data-ttu-id="405e5-190">Authentifizierung hinzufügen</span><span class="sxs-lookup"><span data-stu-id="405e5-190">Add authentication</span></span>](../messaging-extensions/how-to/add-authentication.md)
* [<span data-ttu-id="405e5-191">Erstellen einer Aktions basierten Messaging Erweiterung</span><span class="sxs-lookup"><span data-stu-id="405e5-191">Create an action-based messaging extension</span></span>](../messaging-extensions/how-to/action-commands/define-action-command.md)
* [<span data-ttu-id="405e5-192">Microsoft bot-Framework</span><span class="sxs-lookup"><span data-stu-id="405e5-192">Microsoft Bot Framework</span></span>](https://dev.botframework.com/)
