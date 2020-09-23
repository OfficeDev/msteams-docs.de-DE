---
title: Erstellen einer Microsoft Teams-Messaging Erweiterung
author: heath-hamilton
description: Hier erfahren Sie, wie Sie eine Messaging Erweiterung für Ihre erste Microsoft Teams-app erstellen.
ms.author: lajanuar
ms.date: 09/22/2020
ms.topic: tutorial
ms.openlocfilehash: 0475fcea7d865849fa60c5b3b23788bf90ee5e25
ms.sourcegitcommit: 1aa0b172931d0f81db346452788c41dc4a6717b9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "48210227"
---
# <a name="build-a-teams-messaging-extension"></a><span data-ttu-id="16d2d-103">Erstellen einer Microsoft Teams-Messaging Erweiterung</span><span class="sxs-lookup"><span data-stu-id="16d2d-103">Build a Teams messaging extension</span></span>

<span data-ttu-id="16d2d-104">Es gibt zwei Typen von Microsoft Teams- *Messaging Erweiterungen*: [Suchbefehle](../messaging-extensions/how-to/search-commands/define-search-command.md) und [Aktionsbefehle](../messaging-extensions/how-to/action-commands/define-action-command.md).</span><span class="sxs-lookup"><span data-stu-id="16d2d-104">There are two types of Teams *messaging extensions*: [Search commands](../messaging-extensions/how-to/search-commands/define-search-command.md) and [action commands](../messaging-extensions/how-to/action-commands/define-action-command.md).</span></span>

<span data-ttu-id="16d2d-105">In dieser Lektion erstellen Sie einen *Suchbefehl* (auch als *Suchbasierte Messaging Erweiterung*bezeichnet), bei dem es sich um eine Verknüpfung zum Suchen externer Inhalte und deren Freigabe in Microsoft Teams handelt.</span><span class="sxs-lookup"><span data-stu-id="16d2d-105">In this lesson, you'll create a *search command* (also known as a *search-based messaging extension*), which is a shortcut for finding external content and sharing it in Teams.</span></span> <span data-ttu-id="16d2d-106">Benutzer können über das [Feld Verfassen oder Ausführen des Teams](../messaging-extensions/what-are-messaging-extensions.md)auf Suchbefehle zugreifen.</span><span class="sxs-lookup"><span data-stu-id="16d2d-106">Users can access search commands from the [Teams compose or command box](../messaging-extensions/what-are-messaging-extensions.md).</span></span>

## <a name="your-assignment"></a><span data-ttu-id="16d2d-107">Ihre Zuordnung</span><span class="sxs-lookup"><span data-stu-id="16d2d-107">Your assignment</span></span>

<span data-ttu-id="16d2d-108">Das Helpdesk Ihrer Organisation kommuniziert mit Benutzern über Teams, die Tickets befinden sich jedoch in einem separaten System.</span><span class="sxs-lookup"><span data-stu-id="16d2d-108">Your organization's help desk communicates with users through Teams, but the tickets reside in a separate system.</span></span> <span data-ttu-id="16d2d-109">Dies bedeutet, dass Supportmitarbeiter ständig zwischen apps hin und her wechseln müssen.</span><span class="sxs-lookup"><span data-stu-id="16d2d-109">This means support staff must constantly go back and forth between apps.</span></span> <span data-ttu-id="16d2d-110">Sie werden untersuchen, wie Sie diese vielseitige Kontext Umstellung reduzieren können, indem Sie eine einfache suchbasierte Messaging Erweiterung für Teams erstellen.</span><span class="sxs-lookup"><span data-stu-id="16d2d-110">You'll investigate how you might reduce this much context switching by creating a simple search-based messaging extension for Teams.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="16d2d-111">Was Sie lernen</span><span class="sxs-lookup"><span data-stu-id="16d2d-111">What you'll learn</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="16d2d-112">Erstellen eines App-Projekts und eines bot für die Messaging Erweiterung mithilfe des Microsoft Teams-Toolkits für Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="16d2d-112">Create an app project and messaging extension bot using the Microsoft Teams Toolkit for Visual Studio Code</span></span>
> * <span data-ttu-id="16d2d-113">Identifizieren der Eigenschaften des App-Manifests und einiger für Messaging-Erweiterungen relevanter Gerüste</span><span class="sxs-lookup"><span data-stu-id="16d2d-113">Identify the app manifest properties and some of the scaffolding relevant to messaging extensions</span></span>
> * <span data-ttu-id="16d2d-114">Lokal Hosten einer APP</span><span class="sxs-lookup"><span data-stu-id="16d2d-114">Host an app locally</span></span>
> * <span data-ttu-id="16d2d-115">Konfigurieren des bot für Ihre Messaging Erweiterung</span><span class="sxs-lookup"><span data-stu-id="16d2d-115">Configure the bot for your messaging extension</span></span>
> * <span data-ttu-id="16d2d-116">Querladen und Testen einer Messaging Erweiterung in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="16d2d-116">Sideload and test a messaging extension in Teams</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="16d2d-117">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="16d2d-117">Before you begin</span></span>

<span data-ttu-id="16d2d-118">Wenn Sie noch nicht vorhanden sind, stellen Sie sicher, dass Sie [die Entwicklungsvoraussetzungen für Teams kennen und installieren](build-first-app-overview.md#get-prerequisites).</span><span class="sxs-lookup"><span data-stu-id="16d2d-118">If you haven't yet, make sure you [understand and install the Teams development prerequisites](build-first-app-overview.md#get-prerequisites).</span></span>

## <a name="create-your-app-project"></a><span data-ttu-id="16d2d-119">Erstellen eines App-Projekts</span><span class="sxs-lookup"><span data-stu-id="16d2d-119">Create your app project</span></span>

<span data-ttu-id="16d2d-120">Das Microsoft Teams-Toolkit hilft Ihnen beim Einrichten der folgenden Komponenten für Ihre Messaging-Erweiterung:</span><span class="sxs-lookup"><span data-stu-id="16d2d-120">The Microsoft Teams Toolkit helps you set up the following components for your messaging extension:</span></span>

* <span data-ttu-id="16d2d-121">Für Messaging-Erweiterungen relevantes **App-Manifest und Gerüste**</span><span class="sxs-lookup"><span data-stu-id="16d2d-121">**App manifest and scaffolding** relevant to messaging extensions</span></span>
* <span data-ttu-id="16d2d-122">**Bot** für Ihre Messaging-Erweiterung, die automatisch beim Microsoft Azure bot-Dienst registriert wird</span><span class="sxs-lookup"><span data-stu-id="16d2d-122">**Bot** for your messaging extension that's automatically registered with the Microsoft Azure Bot Service</span></span>

> [!TIP]
> <span data-ttu-id="16d2d-123">Wenn Sie noch kein Teams-App-Projekt erstellt haben, ist es möglicherweise hilfreich, [diese Anweisungen](../build-your-first-app/build-and-run.md) zu befolgen, mit denen Projekte detaillierter erläutert werden.</span><span class="sxs-lookup"><span data-stu-id="16d2d-123">If you haven't created a Teams app project before, you might find it helpful to follow [these instructions](../build-your-first-app/build-and-run.md) that explain projects in more detail.</span></span>

1. Wählen Sie in Visual Studio Code **Microsoft Teams** in :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: der linken Aktivitäts Leiste aus, und wählen Sie **neue Teams-app erstellen**aus.
1. <span data-ttu-id="16d2d-125">Geben Sie einen Namen für Ihre Teams-App ein.</span><span class="sxs-lookup"><span data-stu-id="16d2d-125">Enter a name for your Teams app.</span></span> <span data-ttu-id="16d2d-126">(Dies ist der Standardname für Ihre APP und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.)</span><span class="sxs-lookup"><span data-stu-id="16d2d-126">(This is the default name for your app and also the name of the app project directory on your local machine.)</span></span>
1. <span data-ttu-id="16d2d-127">Wählen Sie auf dem Bildschirm **Funktionen hinzufügen** die Option **Messaging Erweiterung** und dann dann **weiter**aus.</span><span class="sxs-lookup"><span data-stu-id="16d2d-127">On the **Add capabilities** screen, select **Messaging Extension** then **Next**.</span></span>
1. <span data-ttu-id="16d2d-128">Führen Sie auf dem Bildschirm **Messaging-Erweiterung konfigurieren** die folgenden Aktionen aus:</span><span class="sxs-lookup"><span data-stu-id="16d2d-128">On the **Configure messaging extension** screen, do the following:</span></span>
    1. <span data-ttu-id="16d2d-129">Wählen Sie nur die **Suchbasierte** Option für den Typ der Messaging Erweiterung aus.</span><span class="sxs-lookup"><span data-stu-id="16d2d-129">Choose only the **Search-based** option for the type of messaging extension.</span></span>
    1. <span data-ttu-id="16d2d-130">Wählen Sie **Create a New bot** and **Login** aus, um sich mit Ihrem Microsoft 365-entwicklungskonto anzumelden.</span><span class="sxs-lookup"><span data-stu-id="16d2d-130">Select **Create a new Bot** and **Login** to sign in with your Microsoft 365 development account.</span></span>
    1. <span data-ttu-id="16d2d-131">Speichern Sie Ihre bot-ID und Ihr Kennwort (Sie benötigen dies ein wenig später).</span><span class="sxs-lookup"><span data-stu-id="16d2d-131">Store your bot ID and password (you need this a little later).</span></span>
    1. <span data-ttu-id="16d2d-132">Optional Geben Sie einen benutzerdefinierten Namen für Ihren bot ein, und wählen Sie **Erstellen**aus.</span><span class="sxs-lookup"><span data-stu-id="16d2d-132">(Optional) Enter a custom name for your bot and select **Create**.</span></span> <span data-ttu-id="16d2d-133">(Dies ist nicht der Name der Microsoft Teams-APP, die Sie bereits angegeben haben.)</span><span class="sxs-lookup"><span data-stu-id="16d2d-133">(This is not the name of the Teams app you already specified.)</span></span>
    1. <span data-ttu-id="16d2d-134">Wählen Sie im Moment **Nein** für die Option zum Aufheben der Verknüpfung aus.</span><span class="sxs-lookup"><span data-stu-id="16d2d-134">For now, select **No** for the link unfurling option.</span></span></br>
:::image type="content" source="../assets/images/build-your-first-app/choose-me-search.png" alt-text="Abbildung, die zeigt, wie Sie sich im Teams-Toolkit bei Ihrem Microsoft 365-Konto anmelden können, um einen neuen bot für Ihre Messaging Erweiterung zu erstellen.":::
1. <span data-ttu-id="16d2d-136">Klicken Sie unten auf dem Bildschirm auf **Fertig stellen** , um Ihr Projekt zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="16d2d-136">Select **Finish** at the bottom of the screen to configure your project.</span></span>

## <a name="identify-relevant-app-project-components"></a><span data-ttu-id="16d2d-137">Identifizieren relevanter App-Projektkomponenten</span><span class="sxs-lookup"><span data-stu-id="16d2d-137">Identify relevant app project components</span></span>

<span data-ttu-id="16d2d-138">Ein Großteil des App-Manifests und Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Teams-Toolkit erstellen.</span><span class="sxs-lookup"><span data-stu-id="16d2d-138">Much of the app manifest and scaffolding are set up automatically when you create your project with the Teams Toolkit.</span></span>

### <a name="app-manifest"></a><span data-ttu-id="16d2d-139">App-Manifest</span><span class="sxs-lookup"><span data-stu-id="16d2d-139">App manifest</span></span>

<span data-ttu-id="16d2d-140">Im folgenden Codeausschnitt aus dem App-Manifest (die `manifest.json` Datei im Verzeichnis des Projekts `.publish` ) werden die Eigenschaften und Standardwerte für Messaging Erweiterungen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="16d2d-140">The following snippet from the app manifest (the `manifest.json` file in your project's `.publish` directory) shows the properties and default values relevant to messaging extensions.</span></span>

```JSON
"composeExtensions": [
    {
        "botId": "{botId0}",
        "canUpdateConfiguration": true,
        "commands": [
            {
                "id": "searchQuery",
                "context": [
                    "compose",
                    "commandBox"
                ],
                "description": "Test command to run query",
                "title": "Search",
                "type": "query",
                "parameters": [
                    {
                        "name": "searchQuery",
                        "title": "Search Query",
                        "description": "Your search query",
                        "inputType": "text"
                    }
                ]
            }
        ]
    }
],
```

<span data-ttu-id="16d2d-141">Lassen Sie uns einige der Eigenschaften verstehen, die das Toolkit für Sie erstellt hat.</span><span class="sxs-lookup"><span data-stu-id="16d2d-141">Let's understand some of the properties the toolkit created for you.</span></span> <span data-ttu-id="16d2d-142">(Weitere Informationen finden Sie in der vollständigen Liste unterstützter [`composeExtensions`](../resources/schema/manifest-schema.md#composeextensions) Eigenschaften.)</span><span class="sxs-lookup"><span data-stu-id="16d2d-142">(See the full list of supported [`composeExtensions`](../resources/schema/manifest-schema.md#composeextensions) properties.)</span></span>

* <span data-ttu-id="16d2d-143">`botId`: Die ID des bot, den Sie zum Einrichten Ihres Projekts erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="16d2d-143">`botId`: The ID of the bot you created setting up your project.</span></span> <span data-ttu-id="16d2d-144">(In gespeichert `{botId0}` , können Sie die tatsächliche ID in suchen `Development.env` .)</span><span class="sxs-lookup"><span data-stu-id="16d2d-144">(Stored in `{botId0}`, you can find the actual ID in `Development.env`.)</span></span>
* <span data-ttu-id="16d2d-145">`commands`: Verfügbare Befehle für die Messaging Erweiterung.</span><span class="sxs-lookup"><span data-stu-id="16d2d-145">`commands`: Available commands for the messaging extension.</span></span> <span data-ttu-id="16d2d-146">Das Toolkit bietet Ihnen ein Gerüst für einen Suchbefehl.</span><span class="sxs-lookup"><span data-stu-id="16d2d-146">The toolkit provided you scaffolding for a search command.</span></span>
* <span data-ttu-id="16d2d-147">`context`: Wo Benutzer die Messaging Erweiterung aufrufen können.</span><span class="sxs-lookup"><span data-stu-id="16d2d-147">`context`: Where users can invoke the messaging extension.</span></span> <span data-ttu-id="16d2d-148">In diesem Fall können Sie die Messaging Erweiterung im Verfassen-oder Befehlsfeld Teams starten.</span><span class="sxs-lookup"><span data-stu-id="16d2d-148">In this case, you can launch the messaging extension from the Teams compose or command box.</span></span>
* <span data-ttu-id="16d2d-149">`description`: Hilfetext zur Benutzeroberfläche, der angibt, was der Befehl ausführt oder wie er verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="16d2d-149">`description`: UI help text indicating what the command does or how to use it.</span></span>
* <span data-ttu-id="16d2d-150">`parameters`: Enthält alle Parameter, die ein Befehl akzeptiert (Sie müssen mindestens einen haben und kann bis zu fünf).</span><span class="sxs-lookup"><span data-stu-id="16d2d-150">`parameters`: Includes all parameters a command accepts (you must have at least one and can have up to five).</span></span>
* <span data-ttu-id="16d2d-151">`parameters.description`: Hilfetext zur Benutzeroberfläche, der den Zweck oder die Beispiel Eingabe des Parameters beschreibt.</span><span class="sxs-lookup"><span data-stu-id="16d2d-151">`parameters.description`: UI help text describing the parameter's purpose or example input.</span></span>

### <a name="app-scaffolding"></a><span data-ttu-id="16d2d-152">App-Gerüste</span><span class="sxs-lookup"><span data-stu-id="16d2d-152">App scaffolding</span></span>

<span data-ttu-id="16d2d-153">Das App-Gerüst enthält eine `.env` Datei, die sich im Stammverzeichnis des Projekts befindet und die ID und das Kennwort für den bot Ihrer Messaging Erweiterung speichert.</span><span class="sxs-lookup"><span data-stu-id="16d2d-153">The app scaffolding includes a `.env` file, located in the root directory of your project, which stores the ID and password of your messaging extension's bot.</span></span>

<span data-ttu-id="16d2d-154">Auch im Stammverzeichnis gibt es eine Datei, in der `botActivityHandler.js` Sie behandeln können, wie Ihre Messaging Erweiterung (oder der [bot der Messaging Erweiterung](#configuring-the-bot-for-your-messaging-extension)) auf Suchabfragen in Microsoft Teams reagiert.</span><span class="sxs-lookup"><span data-stu-id="16d2d-154">Also in the root directory, there's a `botActivityHandler.js` file for handling how your messaging extension (or technically, the [messaging extension's bot](#configuring-the-bot-for-your-messaging-extension)) responds to search queries in Teams.</span></span>

## <a name="set-up-a-secure-tunnel-to-your-app"></a><span data-ttu-id="16d2d-155">Einrichten eines sicheren Tunnels für Ihre APP</span><span class="sxs-lookup"><span data-stu-id="16d2d-155">Set up a secure tunnel to your app</span></span>

<span data-ttu-id="16d2d-156">Zu Testzwecken hosten wir Ihre Messaging-Erweiterung auf einem lokalen Webserver (Port 3978).</span><span class="sxs-lookup"><span data-stu-id="16d2d-156">For testing purposes, let's host your messaging extension on a local web server (port 3978).</span></span>

1. <span data-ttu-id="16d2d-157">Führen Sie in einem Terminal aus `ngrok http -host-header=rewrite 3978` .</span><span class="sxs-lookup"><span data-stu-id="16d2d-157">In a terminal, run `ngrok http -host-header=rewrite 3978`.</span></span>
1. <span data-ttu-id="16d2d-158">Kopieren Sie die HTTPS-URL in der Ausgabe, da für Teams HTTPS-Verbindungen erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="16d2d-158">Copy the HTTPS URL in the output since Teams requires HTTPS connections.</span></span>
1. <span data-ttu-id="16d2d-159">Öffnen Sie in Ihrem `.publish` Verzeichnis `Development.env` .</span><span class="sxs-lookup"><span data-stu-id="16d2d-159">In your `.publish` directory, open `Development.env`.</span></span>
1. <span data-ttu-id="16d2d-160">Ersetzen Sie den `baseUrl0` Wert durch die kopierte URL.</span><span class="sxs-lookup"><span data-stu-id="16d2d-160">Replace the `baseUrl0` value with the copied URL.</span></span> <span data-ttu-id="16d2d-161">(Ändern Sie beispielsweise `baseUrl0=http://localhost:3000` in `baseUrl0=https://85528b2b3ca5.ngrok.io` .)</span><span class="sxs-lookup"><span data-stu-id="16d2d-161">(For example, change `baseUrl0=http://localhost:3000` to `baseUrl0=https://85528b2b3ca5.ngrok.io`.)</span></span>

<span data-ttu-id="16d2d-162">Ihr App-Manifest zeigt auf die Stelle, an der Sie den von der Messaging Erweiterung verwendeten bot hosten.</span><span class="sxs-lookup"><span data-stu-id="16d2d-162">Your app manifest is pointing to where you're hosting the bot used by the messaging extension.</span></span>

## <a name="configuring-the-bot-for-your-messaging-extension"></a><span data-ttu-id="16d2d-163">Konfigurieren des bot für Ihre Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="16d2d-163">Configuring the bot for your messaging extension</span></span>

<span data-ttu-id="16d2d-164">Messaging-Erweiterungen beruhen darauf, dass Bots Benutzeranforderungen von Teams an den gehosteten Dienst senden und verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="16d2d-164">Messaging extensions rely on bots to send and process user requests from Teams to your hosted service.</span></span>

<span data-ttu-id="16d2d-165">Der bot muss mit dem Azure bot-Dienst registriert werden, der beim Einrichten Ihrer APP mit dem Teams-Toolkit ausgeführt wurde.</span><span class="sxs-lookup"><span data-stu-id="16d2d-165">The bot must be registered with the Azure Bot Service, which was done when you set up your app using the Teams Toolkit.</span></span>

### <a name="specify-your-bot-id-and-password"></a><span data-ttu-id="16d2d-166">Geben Sie Ihre bot-ID und Ihr Kennwort ein.</span><span class="sxs-lookup"><span data-stu-id="16d2d-166">Specify your bot ID and password</span></span>

<span data-ttu-id="16d2d-167">Wenn Ihr bot mit dem Azure bot-Dienst registriert ist, erhält er eine ID und ein Kennwort, über die ihre Teams-App Bescheid wissen muss.</span><span class="sxs-lookup"><span data-stu-id="16d2d-167">When your bot is registered with the Azure Bot Service, it's assigned an ID and password that your Teams app must know about.</span></span>

1. <span data-ttu-id="16d2d-168">Suchen Sie die bot-ID und das Kennwort, die Sie während des Toolkit-Setups gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="16d2d-168">Locate the bot ID and password you stored during toolkit setup.</span></span>
1. <span data-ttu-id="16d2d-169">Öffnen Sie in Ihrem Stammverzeichnis die `.env` Datei.</span><span class="sxs-lookup"><span data-stu-id="16d2d-169">In your root directory, open the `.env` file.</span></span>
1. <span data-ttu-id="16d2d-170">Legen Sie Ihre bot-ID und Ihr Kennwort auf die `BotId` Eigenschaften und fest `BotPassword` .</span><span class="sxs-lookup"><span data-stu-id="16d2d-170">Set your bot ID and password to the `BotId` and `BotPassword` properties, respectively.</span></span>

### <a name="add-the-bot-endpoint-address"></a><span data-ttu-id="16d2d-171">Hinzufügen der bot-Endpunktadresse</span><span class="sxs-lookup"><span data-stu-id="16d2d-171">Add the bot endpoint address</span></span>

<span data-ttu-id="16d2d-172">Sie müssen eine bot-Endpunkt-URL angeben, um Suchabfragen in Ihrer Messaging-Erweiterung zu empfangen und zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="16d2d-172">You must specify a bot endpoint URL to receive and process search queries in your messaging extension.</span></span> <span data-ttu-id="16d2d-173">Normalerweise sieht die URL wie aus `https://HOST_URL/api/messages` .</span><span class="sxs-lookup"><span data-stu-id="16d2d-173">Typically, the URL looks like `https://HOST_URL/api/messages`.</span></span> <span data-ttu-id="16d2d-174">Sie können dies schnell im Teams-Toolkit konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="16d2d-174">You can configure this quickly in the Teams Toolkit.</span></span>

1. Wählen Sie in Visual Studio Code **Microsoft Teams** in :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: der linken Aktivitäts Leiste aus, und wählen Sie **Microsoft Teams Toolkit öffnen**aus.
1. <span data-ttu-id="16d2d-176">Wechseln Sie zu **bot Management > vorhandene bot-Registrierungen** , und wählen Sie den bot aus, den Sie während des Setups erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="16d2d-176">Go to **Bot management > Existing bot registrations** and select the bot you created during setup.</span></span>
1. <span data-ttu-id="16d2d-177">Geben Sie in das Feld **bot-Endpunktadresse** den lokalen Webserver ein, auf dem Sie den bot hosten ( `baseUrl10` Wert), und fügen Sie `/api/messages` ihn hinzu.</span><span class="sxs-lookup"><span data-stu-id="16d2d-177">In the **Bot endpoint address** field, enter the local web server where you're hosting the bot (`baseUrl10` value) and append `/api/messages` to it.</span></span>

<span data-ttu-id="16d2d-178">Ihr bot ist in der Lage, Abfragen in Ihrer Messaging-Erweiterung zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="16d2d-178">Your bot will be able to handle queries in your messaging extension.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="16d2d-179">Ausführen der APP</span><span class="sxs-lookup"><span data-stu-id="16d2d-179">Run your app</span></span>

<span data-ttu-id="16d2d-180">Sie haben eine URL eingerichtet, die Ihre Messaging-Erweiterung hostet und für die Verarbeitung von Suchvorgängen konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="16d2d-180">You've set up a URL to host your messaging extension and configured it to handle searches.</span></span> <span data-ttu-id="16d2d-181">Es ist an der Zeit, Ihre APP in Betrieb zu nehmen.</span><span class="sxs-lookup"><span data-stu-id="16d2d-181">It's time to get your app up and running.</span></span>

1. <span data-ttu-id="16d2d-182">Wechseln Sie in einem Terminal zum Stammverzeichnis des App-Projekts, und führen Sie es aus `npm install` .</span><span class="sxs-lookup"><span data-stu-id="16d2d-182">In a terminal, go to the root directory of your app project and run `npm install`.</span></span>
1. <span data-ttu-id="16d2d-183">Ausführen `npm start` .</span><span class="sxs-lookup"><span data-stu-id="16d2d-183">Run `npm start`.</span></span>

<span data-ttu-id="16d2d-184">Wenn die Meldung erfolgreich verläuft, wird die folgende Meldung angezeigt, die darauf hinweist, dass Ihr Messaging-Erweiterungsdienst bei Ihrem `localhost` Folgendes überwacht:</span><span class="sxs-lookup"><span data-stu-id="16d2d-184">If successful, you see something like the following message indicating your messaging extension service is listening for activity at your `localhost`:</span></span>

`Bot/ME service listening at http://localhost:3978`

## <a name="sideload-your-messaging-extension-in-teams"></a><span data-ttu-id="16d2d-185">Querladen Ihrer Messaging Erweiterung in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="16d2d-185">Sideload your messaging extension in Teams</span></span>

<span data-ttu-id="16d2d-186">Wenn Ihre Messaging-Erweiterung aktiv ist, können Sie Sie in Microsoft Teams installieren.</span><span class="sxs-lookup"><span data-stu-id="16d2d-186">With your messaging extension running, you can install it in Teams.</span></span>

> [!TIP]
> <span data-ttu-id="16d2d-187">Wenn Sie noch keine Teams-App quer geladene haben und Probleme haben, führen Sie die folgenden [Schritte](../build-your-first-app/build-and-run.md#sideload-your-app-in-teams)aus.</span><span class="sxs-lookup"><span data-stu-id="16d2d-187">If you haven't sideloaded a Teams app before and run into issues, follow these [instructions](../build-your-first-app/build-and-run.md#sideload-your-app-in-teams).</span></span>

1. <span data-ttu-id="16d2d-188">Melden Sie sich mit Ihrem Konto beim Microsoft Teams-Client an, das App-Sideloading zulässt.</span><span class="sxs-lookup"><span data-stu-id="16d2d-188">Log in to the Teams client with your account that allows app sideloading.</span></span>
1. <span data-ttu-id="16d2d-189">Wählen Sie **apps**aus, und wählen Sie dann **benutzerdefinierte App hochladen**aus.</span><span class="sxs-lookup"><span data-stu-id="16d2d-189">Select **Apps**, then choose **Upload a custom app**.</span></span>
1. <span data-ttu-id="16d2d-190">Wechseln Sie zu Ihrem APP `.publish` -Projektordner, und wählen Sie aus `Development.zip` .</span><span class="sxs-lookup"><span data-stu-id="16d2d-190">Go to your app project `.publish` folder and select `Development.zip`.</span></span>
1. <span data-ttu-id="16d2d-191">Wählen Sie im modalen Installationsmodus die Option **Hinzufügen** aus, um Ihre APP zu installieren.</span><span class="sxs-lookup"><span data-stu-id="16d2d-191">In the install modal, select **Add** to install your app.</span></span>

## <a name="test-your-messaging-extension"></a><span data-ttu-id="16d2d-192">Testen der Messaging Erweiterung</span><span class="sxs-lookup"><span data-stu-id="16d2d-192">Test your messaging extension</span></span>

<span data-ttu-id="16d2d-193">Erfahren Sie, wie Messaging-Erweiterungen in einem Microsoft Teams-Chat funktionieren.</span><span class="sxs-lookup"><span data-stu-id="16d2d-193">Learn how messaging extensions work in a Teams chat.</span></span>

1. <span data-ttu-id="16d2d-194">Starten Sie einen neuen Chat.</span><span class="sxs-lookup"><span data-stu-id="16d2d-194">Start a new chat.</span></span> Wählen Sie im Feld Verfassen die Option **Weitere** aus, :::image type="icon" source="../assets/icons/teams-client-more.png"::: und wählen Sie die soeben quer geladene Messaging-Erweiterungs-App aus.<br/>
   :::image type="content" source="../assets/images/build-your-first-app/me-teams-access.png" alt-text="Abbildung zeigt, wie Sie im Feld Teams erstellen auf eine suchbasierte Messaging Erweiterung zugreifen können.":::
1. <span data-ttu-id="16d2d-197">Versuchen Sie, nach etwas zu suchen (beispielsweise "Tickets").</span><span class="sxs-lookup"><span data-stu-id="16d2d-197">Try searching for something (for example, "Tickets").</span></span> <span data-ttu-id="16d2d-198">Wenn Ihre APP funktioniert, werden Beispiel Suchergebnisse angezeigt (Sie können Sie später hinzufügen).</span><span class="sxs-lookup"><span data-stu-id="16d2d-198">If your app is working, you'll see sample search results (you can add your own later).</span></span><br/>
   :::image type="content" source="../assets/images/build-your-first-app/me-teams-test.png" alt-text="Ein Screenshot, der zeigt, wie eine suchbasierte Messaging Erweiterung im Feld "Teams erstellen" verwendet wird.":::

## <a name="well-done"></a><span data-ttu-id="16d2d-200">Gut gemacht</span><span class="sxs-lookup"><span data-stu-id="16d2d-200">Well done</span></span>

<span data-ttu-id="16d2d-201">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="16d2d-201">Congratulations!</span></span> <span data-ttu-id="16d2d-202">Sie verfügen über eine Standard-Microsoft Teams-Messaging Erweiterung, die für die Suche nach externem Inhalt im Feld Verfassen oder Befehl eingerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="16d2d-202">You have a basic Teams messaging extension that's set up to search for external content in the compose or command box.</span></span>

## <a name="next-steps"></a><span data-ttu-id="16d2d-203">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="16d2d-203">Next steps</span></span>

<span data-ttu-id="16d2d-204">Auf den folgenden Seiten können Sie fortfahren und eine vollständig ausgestattete Messaging Erweiterung erstellen:</span><span class="sxs-lookup"><span data-stu-id="16d2d-204">See the following pages to continue and build a fully featured messaging extension:</span></span>

1. <span data-ttu-id="16d2d-205">[Definieren Sie Suchbefehle](../messaging-extensions/how-to/search-commands/define-search-command.md) , die für Ihren Dienst relevant sind.</span><span class="sxs-lookup"><span data-stu-id="16d2d-205">[Define search commands](../messaging-extensions/how-to/search-commands/define-search-command.md) that are relevant to your service.</span></span>
1. <span data-ttu-id="16d2d-206">Konfigurieren Sie den Dienst so, dass er [auf die Suchvorgänge von Benutzern reagiert](../messaging-extensions/how-to/search-commands/respond-to-search.md).</span><span class="sxs-lookup"><span data-stu-id="16d2d-206">Configure your service to [respond to users' searches](../messaging-extensions/how-to/search-commands/respond-to-search.md).</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="16d2d-207">Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="16d2d-207">Troubleshooting</span></span>

<span data-ttu-id="16d2d-208">Die folgenden Informationen können hilfreich sein, wenn beim Abschluss dieses Lernprogramms Probleme aufgetreten sind.</span><span class="sxs-lookup"><span data-stu-id="16d2d-208">The following information may help if you had issues completing this tutorial.</span></span>

### <a name="toolkit-setup-fails"></a><span data-ttu-id="16d2d-209">Toolkit-Setup schlägt fehl</span><span class="sxs-lookup"><span data-stu-id="16d2d-209">Toolkit setup fails</span></span>

<span data-ttu-id="16d2d-210">Beim Einrichten Ihres App-Projekts mit dem Teams-Toolkit erhalten Sie eine Fehlermeldung, nachdem Sie die Option **neue bot erstellen** ausgewählt und sich mit Ihrem Microsoft 365-entwicklungskonto angemeldet haben.</span><span class="sxs-lookup"><span data-stu-id="16d2d-210">While setting up your app project with the Teams Toolkit, you get an error after selecting the **Create a new Bot** option and logging in with your Microsoft 365 development account.</span></span>

<span data-ttu-id="16d2d-211">Hierbei kann es sich um ein Authentifizierungsproblem handeln.</span><span class="sxs-lookup"><span data-stu-id="16d2d-211">This could be an authentication issue.</span></span> <span data-ttu-id="16d2d-212">Führen Sie die folgenden Schritte aus, um das Einrichten Ihres Projekts abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="16d2d-212">Follow these steps to finish setting up your project.</span></span>

1. Wählen Sie in Visual Studio Code **Microsoft Teams** in :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: der linken Aktivitäts Leiste aus, und wählen Sie **Abmelden aus**.
1. <span data-ttu-id="16d2d-214">Durchlaufen Sie den Setupvorgang erneut, indem Sie sich mit demselben Konto anmelden und einen neuen bot erstellen.</span><span class="sxs-lookup"><span data-stu-id="16d2d-214">Go through the setup process again by logging in with the same account and creating a new bot.</span></span>

### <a name="bot-isnt-connected-to-teams"></a><span data-ttu-id="16d2d-215">Bot ist nicht mit Microsoft Teams verbunden</span><span class="sxs-lookup"><span data-stu-id="16d2d-215">Bot isn't connected to Teams</span></span>

<span data-ttu-id="16d2d-216">Wenn Sie Ihre APP installiert haben, aber nicht funktioniert, stellen Sie sicher, dass der bot der Messaging Erweiterung [mit dem Microsoft Teams- *Kanal*des Azure bot-Diensts verbunden](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true)ist.</span><span class="sxs-lookup"><span data-stu-id="16d2d-216">If you installed your app but it isn't working, make sure the messaging extension's bot is [connected to the Azure Bot Service's Teams *channel*](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true).</span></span>

<span data-ttu-id="16d2d-217">Es ist wichtig zu verstehen, dass dies nicht mit einem Kanal in Microsoft Teams identisch ist.</span><span class="sxs-lookup"><span data-stu-id="16d2d-217">It's important to understand that this isn't the same as a channel in Teams.</span></span> <span data-ttu-id="16d2d-218">In diesem Fall stellt ein Kanal dar, wie der Azure bot-Dienst Ihren bot mit Teams oder einer anderen [unterstützten Microsoft-oder Drittanbieter-Kommunikations-App](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)verbindet.</span><span class="sxs-lookup"><span data-stu-id="16d2d-218">In this case, a channel is how the Azure Bot Service connects your bot to Teams or another [supported Microsoft or third-party communications app](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span>

## <a name="learn-more"></a><span data-ttu-id="16d2d-219">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="16d2d-219">Learn more</span></span>

* [<span data-ttu-id="16d2d-220">Einschließen einer Link-Entfaltungs Funktion</span><span class="sxs-lookup"><span data-stu-id="16d2d-220">Include a link unfurling feature</span></span>](../messaging-extensions/how-to/link-unfurling.md)
* [<span data-ttu-id="16d2d-221">Authentifizierung hinzufügen</span><span class="sxs-lookup"><span data-stu-id="16d2d-221">Add authentication</span></span>](../messaging-extensions/how-to/add-authentication.md)
* [<span data-ttu-id="16d2d-222">Erstellen einer Aktions basierten Messaging Erweiterung</span><span class="sxs-lookup"><span data-stu-id="16d2d-222">Create an action-based messaging extension</span></span>](../messaging-extensions/how-to/action-commands/define-action-command.md)
* [<span data-ttu-id="16d2d-223">Microsoft bot-Framework</span><span class="sxs-lookup"><span data-stu-id="16d2d-223">Microsoft Bot Framework</span></span>](https://dev.botframework.com/)
