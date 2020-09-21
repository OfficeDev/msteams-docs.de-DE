---
title: Erstellen eines Bots für Teams
author: heath-hamilton
description: Hier erfahren Sie, wie Sie einen bot in ihrer ersten Microsoft Teams-app erstellen.
ms.author: lajanuar
ms.date: 08/31/2020
ms.topic: tutorial
ms.openlocfilehash: f1307bcc7bb864ddfa97b9297f34fa4f7d5fcb0d
ms.sourcegitcommit: d3bb4bbcdff9545c9869647dcdbe563a2db868be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/18/2020
ms.locfileid: "47964722"
---
# <a name="create-a-bot-for-teams"></a><span data-ttu-id="e7f37-103">Erstellen eines Bots für Teams</span><span class="sxs-lookup"><span data-stu-id="e7f37-103">Create a bot for Teams</span></span>

<span data-ttu-id="e7f37-104">In diesem Lernprogramm erstellen Sie eine einfache *bot* -app.</span><span class="sxs-lookup"><span data-stu-id="e7f37-104">You'll build a basic *bot* app in this tutorial.</span></span> <span data-ttu-id="e7f37-105">Ein bot fungiert als Vermittler zwischen Microsoft Teams-Benutzern und Ihrem Webdienst.</span><span class="sxs-lookup"><span data-stu-id="e7f37-105">A bot acts as an intermediary between Teams users and your web service.</span></span> <span data-ttu-id="e7f37-106">Personen können mit einem bot chatten, um schnell Informationen zu erhalten oder Workflows und Aufgaben zu initiieren, die von Ihrem Dienst ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="e7f37-106">People can chat with a bot to quickly get information or initiate workflows and tasks performed by your service.</span></span>

## <a name="your-assignment"></a><span data-ttu-id="e7f37-107">Ihre Zuordnung</span><span class="sxs-lookup"><span data-stu-id="e7f37-107">Your assignment</span></span>

<span data-ttu-id="e7f37-108">Ihr Arbeitsplatz verwendet [Registerkarten](../build-your-first-app/add-personal-tab.md) , um wichtige Kontaktinformationen in Microsoft Teams zu Surface.</span><span class="sxs-lookup"><span data-stu-id="e7f37-108">Your workplace has been using [tabs](../build-your-first-app/add-personal-tab.md) to surface important contact information in Teams.</span></span> <span data-ttu-id="e7f37-109">Kollegen haben beispielsweise schnellen Zugriff auf die Telefonnummer des Helpdesks.</span><span class="sxs-lookup"><span data-stu-id="e7f37-109">For example, colleagues have quick access to the help desk phone number.</span></span> <span data-ttu-id="e7f37-110">Aber statt aufzurufen, was wäre, wenn Personen mit einem Chatbot Kontakt zum Helpdesk aufnehmen könnten?</span><span class="sxs-lookup"><span data-stu-id="e7f37-110">But instead of calling, what if people could contact the help desk using a chatbot?</span></span> <span data-ttu-id="e7f37-111">Ihr Chef bittet Sie, sich anzusehen, wie schnell Sie einen einfachen Unterhaltungs bot in Microsoft Teams in Betrieb nehmen können.</span><span class="sxs-lookup"><span data-stu-id="e7f37-111">Your boss asks you to look at how quickly you can get a basic conversational bot up and running in Teams.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="e7f37-112">Was Sie lernen</span><span class="sxs-lookup"><span data-stu-id="e7f37-112">What you'll learn</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="e7f37-113">Erstellen eines App-Projekts und bot mithilfe des Microsoft Teams-Toolkits für Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="e7f37-113">Create an app project and bot using the Microsoft Teams Toolkit for Visual Studio Code</span></span>
> * <span data-ttu-id="e7f37-114">Identifizieren der Eigenschaften des App-Manifests und einiger für Bots relevanter Gerüste</span><span class="sxs-lookup"><span data-stu-id="e7f37-114">Identify the app manifest properties and some of the scaffolding relevant to bots</span></span>
> * <span data-ttu-id="e7f37-115">Hosten eines bot lokal</span><span class="sxs-lookup"><span data-stu-id="e7f37-115">Host a bot locally</span></span>
> * <span data-ttu-id="e7f37-116">Konfigurieren eines bot für Teams</span><span class="sxs-lookup"><span data-stu-id="e7f37-116">Configure a bot for Teams</span></span>
> * <span data-ttu-id="e7f37-117">Querladen und Testen eines bot in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="e7f37-117">Sideload and test a bot in Teams</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="e7f37-118">Bevor Sie beginnen:</span><span class="sxs-lookup"><span data-stu-id="e7f37-118">Before you begin</span></span>

<span data-ttu-id="e7f37-119">Wenn Sie noch nicht eingerichtet haben, richten Sie Ihr Microsoft 365-Entwicklungs [Konto](building-real-world-app.md#set-up-your-development-account) und die [Teams-App-Tools](building-real-world-app.md#install-your-development-tools)ein.</span><span class="sxs-lookup"><span data-stu-id="e7f37-119">If you haven't yet, set up your Microsoft 365 development [account](building-real-world-app.md#set-up-your-development-account) and [Teams app tools](building-real-world-app.md#install-your-development-tools).</span></span>

## <a name="create-your-app-project-and-bot"></a><span data-ttu-id="e7f37-120">Erstellen Ihres App-Projekts und bot</span><span class="sxs-lookup"><span data-stu-id="e7f37-120">Create your app project and bot</span></span>

<span data-ttu-id="e7f37-121">Das Microsoft Teams-Toolkit hilft Ihnen, die folgenden Komponenten für Ihre APP einzurichten:</span><span class="sxs-lookup"><span data-stu-id="e7f37-121">The Microsoft Teams Toolkit helps you set up the following components for your app:</span></span>

* <span data-ttu-id="e7f37-122">**App-Projekt**: enthält das App-Manifest und für Bots relevante Gerüste</span><span class="sxs-lookup"><span data-stu-id="e7f37-122">**App project**: Includes the app manifest and scaffolding relevant to bots</span></span>
* <span data-ttu-id="e7f37-123">**Bot**: konfiguriert einen neuen bot und registriert ihn mit dem Microsoft Azure bot-Dienst</span><span class="sxs-lookup"><span data-stu-id="e7f37-123">**Bot**: Configures a new bot and registers it with the Microsoft Azure Bot Service</span></span>

> [!TIP]
> <span data-ttu-id="e7f37-124">Wenn Sie noch kein Teams-App-Projekt erstellt haben, ist es möglicherweise hilfreich, [diese Anweisungen](../build-your-first-app/build-and-run.md) zu befolgen, mit denen Projekte detaillierter erläutert werden.</span><span class="sxs-lookup"><span data-stu-id="e7f37-124">If you haven't created a Teams app project before, you might find it helpful to follow [these instructions](../build-your-first-app/build-and-run.md) that explain projects in more detail.</span></span>

1. Wählen Sie in Visual Studio Code **Microsoft Teams** in :::image type="icon" source="../doc-links/images/vsc-toolkit.png"::: der linken Aktivitäts Leiste aus, und wählen Sie **neue Teams-app erstellen**aus.
1. <span data-ttu-id="e7f37-126">Geben Sie einen Namen für Ihre Teams-App ein.</span><span class="sxs-lookup"><span data-stu-id="e7f37-126">Enter a name for your Teams app.</span></span> <span data-ttu-id="e7f37-127">(Dies ist der Standardname für Ihre APP und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.)</span><span class="sxs-lookup"><span data-stu-id="e7f37-127">(This is the default name for your app and also the name of the app project directory on your local machine.)</span></span>
1. <span data-ttu-id="e7f37-128">Wählen Sie auf dem Bildschirm **Funktionen hinzufügen** die Option **bot** und dann **weiter**aus.</span><span class="sxs-lookup"><span data-stu-id="e7f37-128">On the **Add capabilities** screen, select **Bot** then **Next**.</span></span>
1. <span data-ttu-id="e7f37-129">Wählen Sie **Create a New bot** and **Login** aus, um sich mit Ihrem Microsoft 365-entwicklungskonto anzumelden.</span><span class="sxs-lookup"><span data-stu-id="e7f37-129">Select **Create a new Bot** and **Login** to sign in with your Microsoft 365 development account.</span></span><br/>
:::image type="content" source="../doc-links/images/vsc-create-bot.png" alt-text="Abbildung, die zeigt, wie Sie sich im Teams-Toolkit bei Ihrem Microsoft 365-Konto anmelden können, um einen neuen bot zu erstellen.":::
1. <span data-ttu-id="e7f37-131">Optional Geben Sie einen benutzerdefinierten Namen für Ihren bot ein, und wählen Sie **Erstellen**aus.</span><span class="sxs-lookup"><span data-stu-id="e7f37-131">(Optional) Enter a custom name for your bot and select **Create**.</span></span> <span data-ttu-id="e7f37-132">(Denken Sie daran, dies ist der Name für Ihren bot und nicht der Name der Microsoft Teams-APP, die Sie bereits angegeben haben.)</span><span class="sxs-lookup"><span data-stu-id="e7f37-132">(Remember, this is the name for your bot and not the name of the Teams app you already specified.)</span></span>
1. <span data-ttu-id="e7f37-133">Klicken Sie unten auf dem Bildschirm auf **Fertig stellen** , um Ihr Projekt zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="e7f37-133">Select **Finish** at the bottom of the screen to configure your project.</span></span>

## <a name="identify-relevant-app-project-components"></a><span data-ttu-id="e7f37-134">Identifizieren relevanter App-Projektkomponenten</span><span class="sxs-lookup"><span data-stu-id="e7f37-134">Identify relevant app project components</span></span>

<span data-ttu-id="e7f37-135">Ein Großteil des App-Manifests und Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Teams-Toolkit erstellen.</span><span class="sxs-lookup"><span data-stu-id="e7f37-135">Much of the app manifest and scaffolding are set up automatically when you create your project with the Teams Toolkit.</span></span> <span data-ttu-id="e7f37-136">Lassen Sie uns die Hauptkomponenten zum Erstellen eines bot betrachten.</span><span class="sxs-lookup"><span data-stu-id="e7f37-136">Let's look at the main components for building a bot.</span></span>

### <a name="app-manifest"></a><span data-ttu-id="e7f37-137">App-Manifest</span><span class="sxs-lookup"><span data-stu-id="e7f37-137">App manifest</span></span>

<span data-ttu-id="e7f37-138">Im folgenden Codeausschnitt aus dem App-Manifest (die `manifest.json` Datei im Verzeichnis des Projekts `.publish` ) werden die Eigenschaften und Standardwerte für Bots angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e7f37-138">The following snippet from the app manifest (the `manifest.json` file in your project's `.publish` directory) shows the properties and default values relevant to bots.</span></span>

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

<span data-ttu-id="e7f37-139">Lassen Sie uns im Moment nur auf die folgenden erforderlichen Eigenschaften konzentrieren.</span><span class="sxs-lookup"><span data-stu-id="e7f37-139">For now, let's just focus on the following required properties.</span></span> <span data-ttu-id="e7f37-140">(Weitere Informationen finden Sie in der vollständigen Liste unterstützter [`bots`](../../resources/schema/manifest-schema.md#bots) Eigenschaften.)</span><span class="sxs-lookup"><span data-stu-id="e7f37-140">(See the full list of supported [`bots`](../../resources/schema/manifest-schema.md#bots) properties.)</span></span>

* <span data-ttu-id="e7f37-141">`botId`: Die ID des bot, den Sie zum Einrichten Ihres Projekts erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="e7f37-141">`botId`: The ID of the bot you created setting up your project.</span></span> <span data-ttu-id="e7f37-142">(In gespeichert `{botId0}` , können Sie die tatsächliche ID in suchen `Development.env` .)</span><span class="sxs-lookup"><span data-stu-id="e7f37-142">(Stored in `{botId0}`, you can find the actual ID in `Development.env`.)</span></span>
* <span data-ttu-id="e7f37-143">`scopes`: Gibt an, ob Ihr bot in `personal` -, `groupchat` -oder- `team` (also Kanal-) Kontexten verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="e7f37-143">`scopes`: Specifies if your bot is available in `personal`, `groupchat`, or `team` (i.e., channel) contexts.</span></span>
* <span data-ttu-id="e7f37-144">`commands`: Verfügbare Befehle, die Benutzer an Ihren bot senden können.</span><span class="sxs-lookup"><span data-stu-id="e7f37-144">`commands`: Available commands users can send to your bot.</span></span>
* <span data-ttu-id="e7f37-145">`title`: Ein bot-Befehlsname, den Benutzer im Teams-Client sehen.</span><span class="sxs-lookup"><span data-stu-id="e7f37-145">`title`: A bot command name users see in the Teams client.</span></span>
* <span data-ttu-id="e7f37-146">`description`: Eine kurze Beschreibung oder ein Beispiel für die Syntax und die Argumente, mit denen Benutzer verstehen, was ein bot-Befehl bewirkt.</span><span class="sxs-lookup"><span data-stu-id="e7f37-146">`description`: A short description or example of the syntax and arguments to help users understand what a bot command does.</span></span>

### <a name="app-scaffolding"></a><span data-ttu-id="e7f37-147">App-Gerüste</span><span class="sxs-lookup"><span data-stu-id="e7f37-147">App scaffolding</span></span>

<span data-ttu-id="e7f37-148">Das App-Gerüst enthält eine `botActivityHandler.js` Datei, die sich im Stammverzeichnis des Projekts befindet, um zu behandeln, wie Ihr Bot Aktivitäten in Microsoft Teams verarbeitet (beispielsweise, wie der bot auf bestimmte Nachrichten wie "Hello" reagiert).</span><span class="sxs-lookup"><span data-stu-id="e7f37-148">The app scaffolding provides a `botActivityHandler.js` file, located in the root directory of your project, for handling how your bot processes activities in Teams (for example, how the bot responds to specific messages such as "Hello").</span></span>

## <a name="set-up-a-secure-tunnel-to-your-app"></a><span data-ttu-id="e7f37-149">Einrichten eines sicheren Tunnels für Ihre APP</span><span class="sxs-lookup"><span data-stu-id="e7f37-149">Set up a secure tunnel to your app</span></span>

<span data-ttu-id="e7f37-150">Zu Testzwecken hosten wir Ihren bot auf einem lokalen Webserver (Port 3978).</span><span class="sxs-lookup"><span data-stu-id="e7f37-150">For testing purposes, let's host your bot on a local web server (port 3978).</span></span>

1. <span data-ttu-id="e7f37-151">Führen Sie in einem Terminal aus `ngrok http -host-header=rewrite 3978` .</span><span class="sxs-lookup"><span data-stu-id="e7f37-151">In a terminal, run `ngrok http -host-header=rewrite 3978`.</span></span>
1. <span data-ttu-id="e7f37-152">Kopieren Sie die HTTPS-URL in der Ausgabe, da für Teams HTTPS-Verbindungen erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="e7f37-152">Copy the HTTPS URL in the output since Teams requires HTTPS connections.</span></span>
1. <span data-ttu-id="e7f37-153">Öffnen Sie in Ihrem `.publish` Verzeichnis `Development.env` .</span><span class="sxs-lookup"><span data-stu-id="e7f37-153">In your `.publish` directory, open `Development.env`.</span></span>
1. <span data-ttu-id="e7f37-154">Ersetzen Sie den `baseUrl0` Wert durch die kopierte URL.</span><span class="sxs-lookup"><span data-stu-id="e7f37-154">Replace the `baseUrl0` value with the copied URL.</span></span> <span data-ttu-id="e7f37-155">(Ändern Sie beispielsweise `baseUrl0=http://localhost:3000` in `baseUrl0=https://85528b2b3ca5.ngrok.io` .)</span><span class="sxs-lookup"><span data-stu-id="e7f37-155">(For example, change `baseUrl0=http://localhost:3000` to `baseUrl0=https://85528b2b3ca5.ngrok.io`.)</span></span>

<span data-ttu-id="e7f37-156">Ihr App-Manifest zeigt auf die Stelle, an der Sie den bot hosten.</span><span class="sxs-lookup"><span data-stu-id="e7f37-156">Your app manifest is pointing to where you're hosting the bot.</span></span>

## <a name="configuring-your-bot"></a><span data-ttu-id="e7f37-157">Konfigurieren Ihres bot</span><span class="sxs-lookup"><span data-stu-id="e7f37-157">Configuring your bot</span></span>

<span data-ttu-id="e7f37-158">Um einen bot in Microsoft Teams zu verwenden, müssen Sie ihn bei dem Azure bot-Dienst registrieren.</span><span class="sxs-lookup"><span data-stu-id="e7f37-158">To use a bot in Teams, you must register it with the Azure Bot Service.</span></span> <span data-ttu-id="e7f37-159">Glücklicherweise wird dies automatisch durchgeführt, wenn Sie Ihre APP mit dem Teams-Toolkit einrichten.</span><span class="sxs-lookup"><span data-stu-id="e7f37-159">Lucky for you, this is done automatically when you set up your app using the Teams Toolkit.</span></span>

### <a name="add-the-bot-endpoint-address"></a><span data-ttu-id="e7f37-160">Hinzufügen der bot-Endpunktadresse</span><span class="sxs-lookup"><span data-stu-id="e7f37-160">Add the bot endpoint address</span></span>

<span data-ttu-id="e7f37-161">Sie müssen eine Endpunkt-URL angeben, um Benutzer Nachrichten (d. h., Anforderungen) zu empfangen und zu verarbeiten, die an den bot gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="e7f37-161">You must specify an endpoint URL to receive and process user messages (i.e., requests) sent to the bot.</span></span> <span data-ttu-id="e7f37-162">Normalerweise sieht die URL wie aus `https://HOST_URL/api/messages` .</span><span class="sxs-lookup"><span data-stu-id="e7f37-162">Typically, the URL looks like `https://HOST_URL/api/messages`.</span></span> <span data-ttu-id="e7f37-163">Sie können dies schnell im Teams-Toolkit konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="e7f37-163">You can configure this quickly in the Teams Toolkit.</span></span>

1. Wählen Sie in Visual Studio Code **Microsoft Teams** in :::image type="icon" source="../doc-links/images/vsc-toolkit.png"::: der linken Aktivitäts Leiste aus, und wählen Sie **Microsoft Teams Toolkit öffnen**aus.
1. <span data-ttu-id="e7f37-165">Wechseln Sie zu **bot Management > vorhandene bot-Registrierungen** , und wählen Sie den bot aus, den Sie während des Setups erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="e7f37-165">Go to **Bot management > Existing bot registrations** and select the bot you created during setup.</span></span>
1. <span data-ttu-id="e7f37-166">Geben Sie in das Feld **bot-Endpunktadresse** den lokalen Webserver ein, auf dem Sie den bot hosten, und fügen Sie `/api/messages` ihn an.</span><span class="sxs-lookup"><span data-stu-id="e7f37-166">In the **Bot endpoint address** field, enter the local web server where you're hosting the bot and append `/api/messages` to it.</span></span>

    :::image type="content" source="../doc-links/images/bot-config-endpoint-url.png" alt-text="Abbildung zeigt, wo Sie die bot-Endpunkt-URL im Teams-Toolkit konfigurieren können.":::

<span data-ttu-id="e7f37-168">Ihr bot wird in der Lage sein, auf Nachrichten in Microsoft Teams zu antworten.</span><span class="sxs-lookup"><span data-stu-id="e7f37-168">Your bot will be able to respond to messages in Teams.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="e7f37-169">Ausführen der APP</span><span class="sxs-lookup"><span data-stu-id="e7f37-169">Run your app</span></span>

<span data-ttu-id="e7f37-170">Sie haben eine URL zum Hosten Ihres bot eingerichtet und für die Verarbeitung von Nachrichten konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="e7f37-170">You've set up a URL to host your bot and configured it to handle messages.</span></span> <span data-ttu-id="e7f37-171">Es ist an der Zeit, dass Ihr bot in Betrieb geht.</span><span class="sxs-lookup"><span data-stu-id="e7f37-171">It's time to get your bot up and running.</span></span>

1. <span data-ttu-id="e7f37-172">Wechseln Sie in einem Terminal zum Stammverzeichnis des App-Projekts, und führen Sie es aus `npm install` .</span><span class="sxs-lookup"><span data-stu-id="e7f37-172">In a terminal, go to the root directory of your app project and run `npm install`.</span></span>
1. <span data-ttu-id="e7f37-173">Ausführen `npm start` .</span><span class="sxs-lookup"><span data-stu-id="e7f37-173">Run `npm start`.</span></span>

<span data-ttu-id="e7f37-174">Wenn die Meldung erfolgreich verläuft, wird die folgende Meldung angezeigt, die darauf hinweist, dass Ihr bot ihre Aktivität überwacht `localhost` :</span><span class="sxs-lookup"><span data-stu-id="e7f37-174">If successful, you see something like the following message indicating your bot is listening for activity at your `localhost`:</span></span>

`Bot/ME service listening at http://localhost:3978`

## <a name="sideload-your-bot-in-teams"></a><span data-ttu-id="e7f37-175">Querladen Ihres bot in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="e7f37-175">Sideload your bot in Teams</span></span>

<span data-ttu-id="e7f37-176">Wenn Ihr bot läuft, können Sie ihn in Microsoft Teams installieren.</span><span class="sxs-lookup"><span data-stu-id="e7f37-176">With your bot running, you can install it in Teams.</span></span>

> [!TIP]
> <span data-ttu-id="e7f37-177">Wenn Sie noch keine Teams-App quer geladene haben und Probleme haben, führen Sie die folgenden [Schritte](../build-your-first-app/build-and-run.md#sideload-your-app-in-teams)aus.</span><span class="sxs-lookup"><span data-stu-id="e7f37-177">If you haven't sideloaded a Teams app before and run into issues, follow these [instructions](../build-your-first-app/build-and-run.md#sideload-your-app-in-teams).</span></span>

1. <span data-ttu-id="e7f37-178">Melden Sie sich mit Ihrem Konto beim Microsoft Teams-Client an, das App-Sideloading zulässt.</span><span class="sxs-lookup"><span data-stu-id="e7f37-178">Log in to the Teams client with your account that allows app sideloading.</span></span>
1. <span data-ttu-id="e7f37-179">Wählen Sie **apps**aus, und wählen Sie dann **benutzerdefinierte App hochladen**aus.</span><span class="sxs-lookup"><span data-stu-id="e7f37-179">Select **Apps**, then choose **Upload a custom app**.</span></span>
1. <span data-ttu-id="e7f37-180">Wechseln Sie zu Ihrem APP `.publish` -Projektordner, und wählen Sie aus `Development.zip` .</span><span class="sxs-lookup"><span data-stu-id="e7f37-180">Go to your app project `.publish` folder and select `Development.zip`.</span></span>
1. <span data-ttu-id="e7f37-181">Wählen Sie im modalen Installationsmodus die Option **Hinzufügen** aus, um Ihre APP zu installieren.</span><span class="sxs-lookup"><span data-stu-id="e7f37-181">In the install modal, select **Add** to install your app.</span></span>

## <a name="test-your-bot"></a><span data-ttu-id="e7f37-182">Testen des bot</span><span class="sxs-lookup"><span data-stu-id="e7f37-182">Test your bot</span></span>

<span data-ttu-id="e7f37-183">Nun zum spaßigen Teil: sagen wir "Hallo" zu Ihrem bot in einem Einzelchat.</span><span class="sxs-lookup"><span data-stu-id="e7f37-183">Now for the fun part: Let's say "Hello" to your bot in a one-on-one chat.</span></span>

1. Wählen Sie in Microsoft **More** Teams :::image type="icon" source="../doc-links/images/teams-client-more.png"::: auf der linken Seite Weitere aus.
1. <span data-ttu-id="e7f37-185">Suchen und wählen Sie den bot aus, den Sie gerade quer geladene haben.</span><span class="sxs-lookup"><span data-stu-id="e7f37-185">Locate and select the bot you just sideloaded.</span></span><br/>
   :::image type="content" source="../doc-links/images/bot-teams-access.png" alt-text="Illustration, die zeigt, wo Sie in Microsoft Teams auf Ihren bot zugreifen.":::
1. <span data-ttu-id="e7f37-187">Senden Sie im Feld Verfassen eine `Hello` Nachricht.</span><span class="sxs-lookup"><span data-stu-id="e7f37-187">In the compose box, send a `Hello` message.</span></span>

<span data-ttu-id="e7f37-188">Ihr bot antwortet mit so etwas wie der folgenden Nachricht.</span><span class="sxs-lookup"><span data-stu-id="e7f37-188">Your bot replies with something like the following message.</span></span>

:::image type="content" source="../doc-links/images/contoso-chatbot.png" alt-text="Ein Screenshot mit einem Benutzer, der "Hello" zu einem Team-bot und einer Antwort zurückgibt.":::

> [!NOTE]
> <span data-ttu-id="e7f37-190">Wenn Sie nach dem Testen Ihres bot Codeänderungen vornehmen, beispielsweise aktualisieren, `botActivityHandler.js` müssen Sie Ihre APP erneut ausführen, um diese Änderungen in Microsoft Teams wiedergegeben anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="e7f37-190">If you make code changes after testing your bot—for example, you update `botActivityHandler.js`—you must run your app again to see those changes reflected in Teams.</span></span>

## <a name="well-done"></a><span data-ttu-id="e7f37-191">Gut gemacht</span><span class="sxs-lookup"><span data-stu-id="e7f37-191">Well done</span></span>

<span data-ttu-id="e7f37-192">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="e7f37-192">Congratulations!</span></span> <span data-ttu-id="e7f37-193">Sie haben einen einfachen Teams-bot, der mit Benutzern einzeln oder in Gruppeneinstellungen (Kanäle und Chats) kommunizieren kann.</span><span class="sxs-lookup"><span data-stu-id="e7f37-193">You have a basic Teams bot that can communicate with users one-on-one or in group settings (channels and chats).</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="e7f37-194">Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="e7f37-194">Troubleshooting</span></span>

<span data-ttu-id="e7f37-195">Die folgenden Informationen können hilfreich sein, wenn beim Abschluss dieses Lernprogramms Probleme aufgetreten sind.</span><span class="sxs-lookup"><span data-stu-id="e7f37-195">The following information may help if you had issues completing this tutorial.</span></span>

### <a name="toolkit-setup-fails"></a><span data-ttu-id="e7f37-196">Toolkit-Setup schlägt fehl</span><span class="sxs-lookup"><span data-stu-id="e7f37-196">Toolkit setup fails</span></span>

<span data-ttu-id="e7f37-197">Beim Einrichten Ihres App-Projekts mit dem Teams-Toolkit erhalten Sie eine Fehlermeldung, nachdem Sie die Option **neue bot erstellen** ausgewählt und sich mit Ihrem Microsoft 365-entwicklungskonto angemeldet haben.</span><span class="sxs-lookup"><span data-stu-id="e7f37-197">While setting up your app project with the Teams Toolkit, you get an error after selecting the **Create a new Bot** option and logging in with your Microsoft 365 development account.</span></span>

<span data-ttu-id="e7f37-198">Hierbei kann es sich um ein Authentifizierungsproblem handeln.</span><span class="sxs-lookup"><span data-stu-id="e7f37-198">This could be an authentication issue.</span></span> <span data-ttu-id="e7f37-199">Führen Sie die folgenden Schritte aus, um das Einrichten Ihres Projekts abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="e7f37-199">Follow these steps to finish setting up your project.</span></span>

1. Wählen Sie in Visual Studio Code **Microsoft Teams** in :::image type="icon" source="../doc-links/images/vsc-toolkit.png"::: der linken Aktivitäts Leiste aus, und wählen Sie **Abmelden aus**.
1. <span data-ttu-id="e7f37-201">Durchlaufen Sie den Setupvorgang erneut, indem Sie sich mit demselben Konto anmelden und einen neuen bot erstellen.</span><span class="sxs-lookup"><span data-stu-id="e7f37-201">Go through the setup process again by logging in with the same account and creating a new bot.</span></span>

### <a name="bot-isnt-connected-to-teams"></a><span data-ttu-id="e7f37-202">Bot ist nicht mit Microsoft Teams verbunden</span><span class="sxs-lookup"><span data-stu-id="e7f37-202">Bot isn't connected to Teams</span></span>

<span data-ttu-id="e7f37-203">Wenn Sie Ihre APP installiert haben, aber der bot nicht funktioniert, stellen Sie sicher, dass der bot [mit dem Microsoft Teams- *Kanal*des Azure bot-Diensts verbunden](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true)ist.</span><span class="sxs-lookup"><span data-stu-id="e7f37-203">If you installed your app but the bot isn't working, make sure the bot is [connected to the Azure Bot Service's Teams *channel*](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true).</span></span>

<span data-ttu-id="e7f37-204">Es ist wichtig zu verstehen, dass dies nicht mit einem Kanal in Microsoft Teams identisch ist.</span><span class="sxs-lookup"><span data-stu-id="e7f37-204">It's important to understand that this isn't the same as a channel in Teams.</span></span> <span data-ttu-id="e7f37-205">In diesem Fall stellt ein Kanal dar, wie der Azure bot-Dienst Ihren bot mit Teams oder einer anderen [unterstützten Microsoft-oder Drittanbieter-Kommunikations-App](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)verbindet.</span><span class="sxs-lookup"><span data-stu-id="e7f37-205">In this case, a channel is how the Azure Bot Service connects your bot to Teams or another [supported Microsoft or third-party communications app](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span>

## <a name="learn-more"></a><span data-ttu-id="e7f37-206">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e7f37-206">Learn more</span></span>

* [<span data-ttu-id="e7f37-207">Sehen Sie sich an, was andere Teams-Bots mit einem unserer Beispiele tun können (GitHub)</span><span class="sxs-lookup"><span data-stu-id="e7f37-207">See what else Teams bots can do with one of our samples (GitHub)</span></span>](https://github.com/microsoft/BotBuilder-Samples#teams-samples)
* [<span data-ttu-id="e7f37-208">Grundlegende Informationen zu Bot-Unterhaltungen</span><span class="sxs-lookup"><span data-stu-id="e7f37-208">Bot conversation basics</span></span>](../../bots/how-to/conversations/conversation-basics.md)
* [<span data-ttu-id="e7f37-209">Bot-Authentifizierung in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="e7f37-209">Bot authentication in Teams</span></span>](../../bots/how-to/authentication/auth-flow-bot.md)
* [<span data-ttu-id="e7f37-210">Microsoft bot-Framework</span><span class="sxs-lookup"><span data-stu-id="e7f37-210">Microsoft Bot Framework</span></span>](https://dev.botframework.com/)
