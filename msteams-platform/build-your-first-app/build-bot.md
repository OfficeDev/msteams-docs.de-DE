---
title: Erstellen eines Teams-bot
author: heath-hamilton
description: Hier erfahren Sie, wie Sie einen bot für Ihre erste Microsoft Teams-app erstellen.
ms.author: lajanuar
ms.date: 09/22/2020
ms.topic: tutorial
ms.openlocfilehash: 7d3d1b63aace7fda971fb6ccaddddf631b4b2ad9
ms.sourcegitcommit: 1aa0b172931d0f81db346452788c41dc4a6717b9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "48210197"
---
# <a name="build-a-teams-bot"></a><span data-ttu-id="575e8-103">Erstellen eines Teams-bot</span><span class="sxs-lookup"><span data-stu-id="575e8-103">Build a Teams bot</span></span>

<span data-ttu-id="575e8-104">In diesem Lernprogramm erstellen Sie eine einfache *bot* -app.</span><span class="sxs-lookup"><span data-stu-id="575e8-104">You'll build a basic *bot* app in this tutorial.</span></span> <span data-ttu-id="575e8-105">Ein bot fungiert als Vermittler zwischen Microsoft Teams-Benutzern und Ihrem Webdienst.</span><span class="sxs-lookup"><span data-stu-id="575e8-105">A bot acts as an intermediary between Teams users and your web service.</span></span> <span data-ttu-id="575e8-106">Personen können mit einem bot chatten, um schnell Informationen zu erhalten oder Workflows und Aufgaben zu initiieren, die von Ihrem Dienst ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="575e8-106">People can chat with a bot to quickly get information or initiate workflows and tasks performed by your service.</span></span>

## <a name="your-assignment"></a><span data-ttu-id="575e8-107">Ihre Zuordnung</span><span class="sxs-lookup"><span data-stu-id="575e8-107">Your assignment</span></span>

<span data-ttu-id="575e8-108">Ihr Arbeitsplatz verwendet [Registerkarten](../build-your-first-app/build-personal-tab.md) , um wichtige Kontaktinformationen in Microsoft Teams zu Surface.</span><span class="sxs-lookup"><span data-stu-id="575e8-108">Your workplace has been using [tabs](../build-your-first-app/build-personal-tab.md) to surface important contact information in Teams.</span></span> <span data-ttu-id="575e8-109">Kollegen haben beispielsweise schnellen Zugriff auf die Telefonnummer des Helpdesks.</span><span class="sxs-lookup"><span data-stu-id="575e8-109">For example, colleagues have quick access to the help desk phone number.</span></span> <span data-ttu-id="575e8-110">Aber statt aufzurufen, was wäre, wenn Personen mit einem Chatbot Kontakt zum Helpdesk aufnehmen könnten?</span><span class="sxs-lookup"><span data-stu-id="575e8-110">But instead of calling, what if people could contact the help desk using a chatbot?</span></span> <span data-ttu-id="575e8-111">Ihr Chef bittet Sie, sich anzusehen, wie schnell Sie einen einfachen Unterhaltungs bot in Microsoft Teams in Betrieb nehmen können.</span><span class="sxs-lookup"><span data-stu-id="575e8-111">Your boss asks you to look at how quickly you can get a basic conversational bot up and running in Teams.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="575e8-112">Was Sie lernen</span><span class="sxs-lookup"><span data-stu-id="575e8-112">What you'll learn</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="575e8-113">Erstellen eines App-Projekts und bot mithilfe des Microsoft Teams-Toolkits für Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="575e8-113">Create an app project and bot using the Microsoft Teams Toolkit for Visual Studio Code</span></span>
> * <span data-ttu-id="575e8-114">Identifizieren der Eigenschaften und Gerüste für App-Manifeste, die für Bots relevant sind</span><span class="sxs-lookup"><span data-stu-id="575e8-114">Identify some of the app manifest properties and scaffolding relevant to bots</span></span>
> * <span data-ttu-id="575e8-115">Lokal Hosten einer APP</span><span class="sxs-lookup"><span data-stu-id="575e8-115">Host an app locally</span></span>
> * <span data-ttu-id="575e8-116">Konfigurieren eines bot für Teams</span><span class="sxs-lookup"><span data-stu-id="575e8-116">Configure a bot for Teams</span></span>
> * <span data-ttu-id="575e8-117">Querladen und Testen eines bot in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="575e8-117">Sideload and test a bot in Teams</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="575e8-118">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="575e8-118">Before you begin</span></span>

<span data-ttu-id="575e8-119">Wenn Sie noch nicht vorhanden sind, stellen Sie sicher, dass Sie [die Entwicklungsvoraussetzungen für Teams kennen und installieren](build-first-app-overview.md#get-prerequisites).</span><span class="sxs-lookup"><span data-stu-id="575e8-119">If you haven't yet, make sure you [understand and install the Teams development prerequisites](build-first-app-overview.md#get-prerequisites).</span></span>

## <a name="create-your-app-project"></a><span data-ttu-id="575e8-120">Erstellen eines App-Projekts</span><span class="sxs-lookup"><span data-stu-id="575e8-120">Create your app project</span></span>

<span data-ttu-id="575e8-121">Das Microsoft Teams-Toolkit hilft Ihnen, die folgenden Komponenten für Ihre APP einzurichten:</span><span class="sxs-lookup"><span data-stu-id="575e8-121">The Microsoft Teams Toolkit helps you set up the following components for your app:</span></span>

* <span data-ttu-id="575e8-122">**App-Manifest und** für Bots relevante Gerüste</span><span class="sxs-lookup"><span data-stu-id="575e8-122">**App manifest and scaffolding** relevant to bots</span></span>
* <span data-ttu-id="575e8-123">**Bot** , der automatisch beim Microsoft Azure bot-Dienst registriert wird</span><span class="sxs-lookup"><span data-stu-id="575e8-123">**Bot** that's automatically registered with the Microsoft Azure Bot Service</span></span>

> [!TIP]
> <span data-ttu-id="575e8-124">Wenn Sie noch kein Teams-App-Projekt erstellt haben, ist es möglicherweise hilfreich, [diese Anweisungen](../build-your-first-app/build-and-run.md) zu befolgen, mit denen Projekte detaillierter erläutert werden.</span><span class="sxs-lookup"><span data-stu-id="575e8-124">If you haven't created a Teams app project before, you might find it helpful to follow [these instructions](../build-your-first-app/build-and-run.md) that explain projects in more detail.</span></span>

1. Wählen Sie in Visual Studio Code **Microsoft Teams** in :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: der linken Aktivitäts Leiste aus, und wählen Sie **neue Teams-app erstellen**aus.
1. <span data-ttu-id="575e8-126">Geben Sie einen Namen für Ihre Teams-App ein.</span><span class="sxs-lookup"><span data-stu-id="575e8-126">Enter a name for your Teams app.</span></span> <span data-ttu-id="575e8-127">(Dies ist der Standardname für Ihre APP und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.)</span><span class="sxs-lookup"><span data-stu-id="575e8-127">(This is the default name for your app and also the name of the app project directory on your local machine.)</span></span>
1. <span data-ttu-id="575e8-128">Wählen Sie auf dem Bildschirm **Funktionen hinzufügen** die Option **bot** und dann **weiter**aus.</span><span class="sxs-lookup"><span data-stu-id="575e8-128">On the **Add capabilities** screen, select **Bot** then **Next**.</span></span>
1. <span data-ttu-id="575e8-129">Wählen Sie **Create a New bot** and **Login** aus, um sich mit Ihrem Microsoft 365-entwicklungskonto anzumelden.</span><span class="sxs-lookup"><span data-stu-id="575e8-129">Select **Create a new Bot** and **Login** to sign in with your Microsoft 365 development account.</span></span><br/>
:::image type="content" source="../assets/images/build-your-first-app/vsc-create-bot.png" alt-text="Abbildung, die zeigt, wie Sie sich im Teams-Toolkit bei Ihrem Microsoft 365-Konto anmelden können, um einen neuen bot zu erstellen.":::
1. <span data-ttu-id="575e8-131">Speichern Sie Ihre bot-ID und Ihr Kennwort (Sie benötigen dies ein wenig später).</span><span class="sxs-lookup"><span data-stu-id="575e8-131">Store your bot ID and password (you need this a little later).</span></span>
1. <span data-ttu-id="575e8-132">Optional Geben Sie einen benutzerdefinierten Namen für Ihren bot ein, und wählen Sie **Erstellen**aus.</span><span class="sxs-lookup"><span data-stu-id="575e8-132">(Optional) Enter a custom name for your bot and select **Create**.</span></span> <span data-ttu-id="575e8-133">(Denken Sie daran, dies ist der Name für Ihren bot und nicht der Name der Microsoft Teams-APP, die Sie bereits angegeben haben.)</span><span class="sxs-lookup"><span data-stu-id="575e8-133">(Remember, this is the name for your bot and not the name of the Teams app you already specified.)</span></span>
1. <span data-ttu-id="575e8-134">Klicken Sie unten auf dem Bildschirm auf **Fertig stellen** , um Ihr Projekt zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="575e8-134">Select **Finish** at the bottom of the screen to configure your project.</span></span>

## <a name="identify-relevant-app-project-components"></a><span data-ttu-id="575e8-135">Identifizieren relevanter App-Projektkomponenten</span><span class="sxs-lookup"><span data-stu-id="575e8-135">Identify relevant app project components</span></span>

<span data-ttu-id="575e8-136">Ein Großteil des App-Manifests und Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Teams-Toolkit erstellen.</span><span class="sxs-lookup"><span data-stu-id="575e8-136">Much of the app manifest and scaffolding are set up automatically when you create your project with the Teams Toolkit.</span></span> <span data-ttu-id="575e8-137">Lassen Sie uns die Hauptkomponenten zum Erstellen eines bot betrachten.</span><span class="sxs-lookup"><span data-stu-id="575e8-137">Let's look at the main components for building a bot.</span></span>

### <a name="app-manifest"></a><span data-ttu-id="575e8-138">App-Manifest</span><span class="sxs-lookup"><span data-stu-id="575e8-138">App manifest</span></span>

<span data-ttu-id="575e8-139">Im folgenden Codeausschnitt aus dem App-Manifest (die `manifest.json` Datei im Verzeichnis des Projekts `.publish` ) werden die Eigenschaften und Standardwerte für Bots angezeigt.</span><span class="sxs-lookup"><span data-stu-id="575e8-139">The following snippet from the app manifest (the `manifest.json` file in your project's `.publish` directory) shows the properties and default values relevant to bots.</span></span>

```JSON
"bots": [
    {
        "botId": "{botId0}",
        "scopes": [
            "personal",
            "groupchat",
            "team"
        ],
        "supportsFiles": false,
        "isNotificationOnly": false,
        "commandLists": [
            {
                "scopes": [
                    "personal",
                    "groupchat",
                    "team"
                ],
                "commands": [
                    {
                        "title": "Hello",
                        "description": "Sends a hello message and @mention the sender"
                    }
                ]
            }
        ]
    }
],
```

<span data-ttu-id="575e8-140">Lassen Sie uns im Moment nur auf die folgenden erforderlichen Eigenschaften konzentrieren.</span><span class="sxs-lookup"><span data-stu-id="575e8-140">For now, let's just focus on the following required properties.</span></span> <span data-ttu-id="575e8-141">(Weitere Informationen finden Sie in der vollständigen Liste unterstützter [`bots`](../resources/schema/manifest-schema.md#bots) Eigenschaften.)</span><span class="sxs-lookup"><span data-stu-id="575e8-141">(See the full list of supported [`bots`](../resources/schema/manifest-schema.md#bots) properties.)</span></span>

* <span data-ttu-id="575e8-142">`botId`: Die ID des bot, den Sie zum Einrichten Ihres Projekts erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="575e8-142">`botId`: The ID of the bot you created setting up your project.</span></span> <span data-ttu-id="575e8-143">(In gespeichert `{botId0}` , können Sie die tatsächliche ID in suchen `Development.env` .)</span><span class="sxs-lookup"><span data-stu-id="575e8-143">(Stored in `{botId0}`, you can find the actual ID in `Development.env`.)</span></span>
* <span data-ttu-id="575e8-144">`scopes`: Gibt an, ob Ihr bot in `personal` -, `groupchat` -oder- `team` (also Kanal-) Kontexten verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="575e8-144">`scopes`: Specifies if your bot is available in `personal`, `groupchat`, or `team` (i.e., channel) contexts.</span></span>
* <span data-ttu-id="575e8-145">`commands`: Verfügbare Befehle, die Benutzer an Ihren bot senden können.</span><span class="sxs-lookup"><span data-stu-id="575e8-145">`commands`: Available commands users can send to your bot.</span></span>
* <span data-ttu-id="575e8-146">`title`: Bot-Befehlsname, der im Teams-Client angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="575e8-146">`title`: Bot command name that displays in the Teams client.</span></span>
* <span data-ttu-id="575e8-147">`description`: Eine kurze Beschreibung oder ein Beispiel für die Syntax und die Argumente, mit denen Benutzer verstehen, was ein bot-Befehl bewirkt.</span><span class="sxs-lookup"><span data-stu-id="575e8-147">`description`: A short description or example of the syntax and arguments to help users understand what a bot command does.</span></span>

### <a name="app-scaffolding"></a><span data-ttu-id="575e8-148">App-Gerüste</span><span class="sxs-lookup"><span data-stu-id="575e8-148">App scaffolding</span></span>

<span data-ttu-id="575e8-149">Das App-Gerüst enthält eine `botActivityHandler.js` Datei, die sich im Stammverzeichnis des Projekts befindet, um zu behandeln, wie Ihr Bot Aktivitäten in Microsoft Teams verarbeitet (beispielsweise, wie der bot auf bestimmte Nachrichten wie "Hello" reagiert).</span><span class="sxs-lookup"><span data-stu-id="575e8-149">The app scaffolding provides a `botActivityHandler.js` file, located in the root directory of your project, for handling how your bot processes activities in Teams (for example, how the bot responds to specific messages such as "Hello").</span></span>

<span data-ttu-id="575e8-150">Die `.env` Datei, auch im Stammverzeichnis, speichert Ihre bot-ID und Ihr Kennwort.</span><span class="sxs-lookup"><span data-stu-id="575e8-150">The `.env` file, also in the root directory, stores your bot ID and password.</span></span>

## <a name="set-up-a-secure-tunnel-to-your-app"></a><span data-ttu-id="575e8-151">Einrichten eines sicheren Tunnels für Ihre APP</span><span class="sxs-lookup"><span data-stu-id="575e8-151">Set up a secure tunnel to your app</span></span>

<span data-ttu-id="575e8-152">Zu Testzwecken hosten wir Ihren bot auf einem lokalen Webserver (Port 3978).</span><span class="sxs-lookup"><span data-stu-id="575e8-152">For testing purposes, let's host your bot on a local web server (port 3978).</span></span>

1. <span data-ttu-id="575e8-153">Führen Sie in einem Terminal aus `ngrok http -host-header=rewrite 3978` .</span><span class="sxs-lookup"><span data-stu-id="575e8-153">In a terminal, run `ngrok http -host-header=rewrite 3978`.</span></span>
1. <span data-ttu-id="575e8-154">Kopieren Sie die HTTPS-URL in der Ausgabe, da für Teams HTTPS-Verbindungen erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="575e8-154">Copy the HTTPS URL in the output since Teams requires HTTPS connections.</span></span>
1. <span data-ttu-id="575e8-155">Öffnen Sie in Ihrem `.publish` Verzeichnis `Development.env` .</span><span class="sxs-lookup"><span data-stu-id="575e8-155">In your `.publish` directory, open `Development.env`.</span></span>
1. <span data-ttu-id="575e8-156">Ersetzen Sie den `baseUrl0` Wert durch die kopierte URL.</span><span class="sxs-lookup"><span data-stu-id="575e8-156">Replace the `baseUrl0` value with the copied URL.</span></span> <span data-ttu-id="575e8-157">(Ändern Sie beispielsweise `baseUrl0=http://localhost:3000` in `baseUrl0=https://85528b2b3ca5.ngrok.io` .)</span><span class="sxs-lookup"><span data-stu-id="575e8-157">(For example, change `baseUrl0=http://localhost:3000` to `baseUrl0=https://85528b2b3ca5.ngrok.io`.)</span></span>

<span data-ttu-id="575e8-158">Ihr App-Manifest zeigt auf die Stelle, an der Sie den bot hosten.</span><span class="sxs-lookup"><span data-stu-id="575e8-158">Your app manifest is pointing to where you're hosting the bot.</span></span>

## <a name="configuring-your-bot"></a><span data-ttu-id="575e8-159">Konfigurieren Ihres bot</span><span class="sxs-lookup"><span data-stu-id="575e8-159">Configuring your bot</span></span>

<span data-ttu-id="575e8-160">Um einen bot in Microsoft Teams zu verwenden, müssen Sie ihn bei dem Azure bot-Dienst registrieren.</span><span class="sxs-lookup"><span data-stu-id="575e8-160">To use a bot in Teams, you must register it with the Azure Bot Service.</span></span> <span data-ttu-id="575e8-161">Glücklicherweise wird dies automatisch durchgeführt, wenn Sie Ihre APP mit dem Teams-Toolkit einrichten.</span><span class="sxs-lookup"><span data-stu-id="575e8-161">Lucky for you, this is done automatically when you set up your app using the Teams Toolkit.</span></span>

### <a name="specify-your-bot-id-and-password"></a><span data-ttu-id="575e8-162">Geben Sie Ihre bot-ID und Ihr Kennwort ein.</span><span class="sxs-lookup"><span data-stu-id="575e8-162">Specify your bot ID and password</span></span>

<span data-ttu-id="575e8-163">Wenn Ihr bot mit dem Azure bot-Dienst registriert ist, erhält er eine ID und ein Kennwort, über die ihre Teams-App Bescheid wissen muss.</span><span class="sxs-lookup"><span data-stu-id="575e8-163">When your bot is registered with the Azure Bot Service, it's assigned an ID and password that your Teams app must know about.</span></span>

1. <span data-ttu-id="575e8-164">Suchen Sie die bot-ID und das Kennwort, die Sie während des Toolkit-Setups gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="575e8-164">Locate the bot ID and password you stored during toolkit setup.</span></span>
1. <span data-ttu-id="575e8-165">Öffnen Sie in Ihrem Stammverzeichnis die `.env` Datei.</span><span class="sxs-lookup"><span data-stu-id="575e8-165">In your root directory, open the `.env` file.</span></span>
1. <span data-ttu-id="575e8-166">Fügen Sie Ihre bot-ID und Ihr Kennwort zu `BotId` bzw `BotPassword` . hinzu.</span><span class="sxs-lookup"><span data-stu-id="575e8-166">Add your bot ID and password to `BotId` and `BotPassword`, respectively.</span></span>

### <a name="add-the-bot-endpoint-address"></a><span data-ttu-id="575e8-167">Hinzufügen der bot-Endpunktadresse</span><span class="sxs-lookup"><span data-stu-id="575e8-167">Add the bot endpoint address</span></span>

<span data-ttu-id="575e8-168">Sie müssen eine Endpunkt-URL angeben, um Benutzer Nachrichten (d. h., Anforderungen) zu empfangen und zu verarbeiten, die an den bot gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="575e8-168">You must specify an endpoint URL to receive and process user messages (i.e., requests) sent to the bot.</span></span> <span data-ttu-id="575e8-169">Normalerweise sieht die URL wie aus `https://HOST_URL/api/messages` .</span><span class="sxs-lookup"><span data-stu-id="575e8-169">Typically, the URL looks like `https://HOST_URL/api/messages`.</span></span> <span data-ttu-id="575e8-170">Sie können dies schnell im Teams-Toolkit konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="575e8-170">You can configure this quickly in the Teams Toolkit.</span></span>

1. Wählen Sie in Visual Studio Code **Microsoft Teams** in :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: der linken Aktivitäts Leiste aus, und wählen Sie **Microsoft Teams Toolkit öffnen**aus.
1. <span data-ttu-id="575e8-172">Wechseln Sie zu **bot Management > vorhandene bot-Registrierungen** , und wählen Sie den bot aus, den Sie während des Setups erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="575e8-172">Go to **Bot management > Existing bot registrations** and select the bot you created during setup.</span></span>
1. <span data-ttu-id="575e8-173">Geben Sie in das Feld **bot-Endpunktadresse** den lokalen Webserver ein, auf dem Sie den bot hosten ( `baseUrl10` Wert), und fügen Sie `/api/messages` ihn hinzu.</span><span class="sxs-lookup"><span data-stu-id="575e8-173">In the **Bot endpoint address** field, enter the local web server where you're hosting the bot (`baseUrl10` value) and append `/api/messages` to it.</span></span>

    :::image type="content" source="../assets/images/build-your-first-app/bot-config-endpoint-url.png" alt-text="Abbildung zeigt, wo Sie die bot-Endpunkt-URL im Teams-Toolkit konfigurieren können.":::

<span data-ttu-id="575e8-175">Ihr bot wird in der Lage sein, auf Nachrichten in Microsoft Teams zu antworten.</span><span class="sxs-lookup"><span data-stu-id="575e8-175">Your bot will be able to respond to messages in Teams.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="575e8-176">Ausführen der APP</span><span class="sxs-lookup"><span data-stu-id="575e8-176">Run your app</span></span>

<span data-ttu-id="575e8-177">Sie haben eine URL zum Hosten Ihres bot eingerichtet und für die Verarbeitung von Nachrichten konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="575e8-177">You've set up a URL to host your bot and configured it to handle messages.</span></span> <span data-ttu-id="575e8-178">Es ist an der Zeit, dass Ihr bot in Betrieb geht.</span><span class="sxs-lookup"><span data-stu-id="575e8-178">It's time to get your bot up and running.</span></span>

1. <span data-ttu-id="575e8-179">Wechseln Sie in einem Terminal zum Stammverzeichnis des App-Projekts, und führen Sie es aus `npm install` .</span><span class="sxs-lookup"><span data-stu-id="575e8-179">In a terminal, go to the root directory of your app project and run `npm install`.</span></span>
1. <span data-ttu-id="575e8-180">Ausführen `npm start` .</span><span class="sxs-lookup"><span data-stu-id="575e8-180">Run `npm start`.</span></span>

<span data-ttu-id="575e8-181">Wenn die Meldung erfolgreich verläuft, wird die folgende Meldung angezeigt, die darauf hinweist, dass Ihr bot ihre Aktivität überwacht `localhost` :</span><span class="sxs-lookup"><span data-stu-id="575e8-181">If successful, you see something like the following message indicating your bot is listening for activity at your `localhost`:</span></span>

`Bot/ME service listening at http://localhost:3978`

## <a name="sideload-your-bot-in-teams"></a><span data-ttu-id="575e8-182">Querladen Ihres bot in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="575e8-182">Sideload your bot in Teams</span></span>

<span data-ttu-id="575e8-183">Wenn Ihr bot läuft, können Sie ihn in Microsoft Teams installieren.</span><span class="sxs-lookup"><span data-stu-id="575e8-183">With your bot running, you can install it in Teams.</span></span>

> [!TIP]
> <span data-ttu-id="575e8-184">Wenn Sie noch keine Teams-App quer geladene haben und Probleme haben, führen Sie die folgenden [Schritte](../build-your-first-app/build-and-run.md#sideload-your-app-in-teams)aus.</span><span class="sxs-lookup"><span data-stu-id="575e8-184">If you haven't sideloaded a Teams app before and run into issues, follow these [instructions](../build-your-first-app/build-and-run.md#sideload-your-app-in-teams).</span></span>

1. <span data-ttu-id="575e8-185">Melden Sie sich mit Ihrem Konto beim Microsoft Teams-Client an, das App-Sideloading zulässt.</span><span class="sxs-lookup"><span data-stu-id="575e8-185">Log in to the Teams client with your account that allows app sideloading.</span></span>
1. <span data-ttu-id="575e8-186">Wählen Sie **apps**aus, und wählen Sie dann **benutzerdefinierte App hochladen**aus.</span><span class="sxs-lookup"><span data-stu-id="575e8-186">Select **Apps**, then choose **Upload a custom app**.</span></span>
1. <span data-ttu-id="575e8-187">Wechseln Sie zu Ihrem APP `.publish` -Projektordner, und wählen Sie aus `Development.zip` .</span><span class="sxs-lookup"><span data-stu-id="575e8-187">Go to your app project `.publish` folder and select `Development.zip`.</span></span>
1. <span data-ttu-id="575e8-188">Wählen Sie im modalen Installationsmodus die Option **Hinzufügen** aus, um Ihre APP zu installieren.</span><span class="sxs-lookup"><span data-stu-id="575e8-188">In the install modal, select **Add** to install your app.</span></span>

## <a name="test-your-bot"></a><span data-ttu-id="575e8-189">Testen des bot</span><span class="sxs-lookup"><span data-stu-id="575e8-189">Test your bot</span></span>

<span data-ttu-id="575e8-190">Nun zum spaßigen Teil: sagen wir "Hallo" zu Ihrem bot in einem Einzelchat.</span><span class="sxs-lookup"><span data-stu-id="575e8-190">Now for the fun part: Let's say "Hello" to your bot in a one-on-one chat.</span></span>

1. Wählen Sie in Microsoft **More** Teams :::image type="icon" source="../assets/icons/teams-client-more.png"::: auf der linken Seite Weitere aus.
1. <span data-ttu-id="575e8-192">Suchen und wählen Sie den bot, den Sie gerade quer geladene.</span><span class="sxs-lookup"><span data-stu-id="575e8-192">Locate and choose the bot you just sideloaded.</span></span><br/>
   :::image type="content" source="../assets/images/build-your-first-app/bot-teams-access.png" alt-text="Illustration, die zeigt, wo Sie in Microsoft Teams auf Ihren bot zugreifen.":::
1. <span data-ttu-id="575e8-194">Senden Sie im Feld Verfassen eine `Hello` Nachricht.</span><span class="sxs-lookup"><span data-stu-id="575e8-194">In the compose box, send a `Hello` message.</span></span>

<span data-ttu-id="575e8-195">Ihr bot antwortet mit so etwas wie der folgenden Nachricht.</span><span class="sxs-lookup"><span data-stu-id="575e8-195">Your bot replies with something like the following message.</span></span>

:::image type="content" source="../assets/images/build-your-first-app/contoso-chatbot.png" alt-text="Ein Screenshot mit einem Benutzer, der "Hello" zu einem Team-bot und einer Antwort ruft.":::

## <a name="well-done"></a><span data-ttu-id="575e8-197">Gut gemacht</span><span class="sxs-lookup"><span data-stu-id="575e8-197">Well done</span></span>

<span data-ttu-id="575e8-198">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="575e8-198">Congratulations!</span></span> <span data-ttu-id="575e8-199">Sie haben einen einfachen Teams-bot, der mit Benutzern einzeln oder in Gruppeneinstellungen (Kanäle und Chats) kommunizieren kann.</span><span class="sxs-lookup"><span data-stu-id="575e8-199">You have a basic Teams bot that can communicate with users one-on-one or in group settings (channels and chats).</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="575e8-200">Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="575e8-200">Troubleshooting</span></span>

<span data-ttu-id="575e8-201">Die folgenden Informationen können hilfreich sein, wenn beim Abschluss dieses Lernprogramms Probleme aufgetreten sind.</span><span class="sxs-lookup"><span data-stu-id="575e8-201">The following information may help if you had issues completing this tutorial.</span></span>

### <a name="toolkit-setup-fails"></a><span data-ttu-id="575e8-202">Toolkit-Setup schlägt fehl</span><span class="sxs-lookup"><span data-stu-id="575e8-202">Toolkit setup fails</span></span>

<span data-ttu-id="575e8-203">Beim Einrichten Ihres App-Projekts mit dem Teams-Toolkit erhalten Sie eine Fehlermeldung, nachdem Sie die Option **neue bot erstellen** ausgewählt und sich mit Ihrem Microsoft 365-entwicklungskonto angemeldet haben.</span><span class="sxs-lookup"><span data-stu-id="575e8-203">While setting up your app project with the Teams Toolkit, you get an error after selecting the **Create a new Bot** option and logging in with your Microsoft 365 development account.</span></span>

<span data-ttu-id="575e8-204">Hierbei kann es sich um ein Authentifizierungsproblem handeln.</span><span class="sxs-lookup"><span data-stu-id="575e8-204">This could be an authentication issue.</span></span> <span data-ttu-id="575e8-205">Führen Sie die folgenden Schritte aus, um das Einrichten Ihres Projekts abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="575e8-205">Follow these steps to finish setting up your project.</span></span>

1. Wählen Sie in Visual Studio Code **Microsoft Teams** in :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: der linken Aktivitäts Leiste aus, und wählen Sie **Abmelden aus**.
1. <span data-ttu-id="575e8-207">Durchlaufen Sie den Setupvorgang erneut, indem Sie sich mit demselben Konto anmelden und einen neuen bot erstellen.</span><span class="sxs-lookup"><span data-stu-id="575e8-207">Go through the setup process again by logging in with the same account and creating a new bot.</span></span>

### <a name="bot-isnt-connected-to-teams"></a><span data-ttu-id="575e8-208">Bot ist nicht mit Microsoft Teams verbunden</span><span class="sxs-lookup"><span data-stu-id="575e8-208">Bot isn't connected to Teams</span></span>

<span data-ttu-id="575e8-209">Wenn Sie Ihre APP installiert haben, aber der bot nicht funktioniert, stellen Sie sicher, dass der bot [mit dem Microsoft Teams- *Kanal*des Azure bot-Diensts verbunden](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true)ist.</span><span class="sxs-lookup"><span data-stu-id="575e8-209">If you installed your app but the bot isn't working, make sure the bot is [connected to the Azure Bot Service's Teams *channel*](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true).</span></span>

<span data-ttu-id="575e8-210">Es ist wichtig zu verstehen, dass dies nicht mit einem Kanal in Microsoft Teams identisch ist.</span><span class="sxs-lookup"><span data-stu-id="575e8-210">It's important to understand that this isn't the same as a channel in Teams.</span></span> <span data-ttu-id="575e8-211">In diesem Fall stellt ein Kanal dar, wie der Azure bot-Dienst Ihren bot mit Teams oder einer anderen [unterstützten Microsoft-oder Drittanbieter-Kommunikations-App](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)verbindet.</span><span class="sxs-lookup"><span data-stu-id="575e8-211">In this case, a channel is how the Azure Bot Service connects your bot to Teams or another [supported Microsoft or third-party communications app](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span>

## <a name="learn-more"></a><span data-ttu-id="575e8-212">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="575e8-212">Learn more</span></span>

* [<span data-ttu-id="575e8-213">Sehen Sie sich an, was andere Teams-Bots mit einem unserer Beispiele tun können</span><span class="sxs-lookup"><span data-stu-id="575e8-213">See what else Teams bots can do with one of our samples</span></span>](https://github.com/microsoft/BotBuilder-Samples#teams-samples)
* [<span data-ttu-id="575e8-214">Grundlegende Informationen zu Bot-Unterhaltungen</span><span class="sxs-lookup"><span data-stu-id="575e8-214">Bot conversation basics</span></span>](../bots/how-to/conversations/conversation-basics.md)
* [<span data-ttu-id="575e8-215">Bot-Authentifizierung in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="575e8-215">Bot authentication in Teams</span></span>](../bots/how-to/authentication/auth-flow-bot.md)
* [<span data-ttu-id="575e8-216">Microsoft bot-Framework</span><span class="sxs-lookup"><span data-stu-id="575e8-216">Microsoft Bot Framework</span></span>](https://dev.botframework.com/)
* [<span data-ttu-id="575e8-217">Erstellen eines bot ohne Toolkit</span><span class="sxs-lookup"><span data-stu-id="575e8-217">Create a bot without the toolkit</span></span>](../bots/how-to/create-a-bot-for-teams.md)
