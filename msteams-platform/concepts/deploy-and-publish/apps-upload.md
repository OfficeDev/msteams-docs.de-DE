---
title: Hochladen Ihrer benutzerdefinierten App
description: Beschreibt, wie Sie Ihre App in Microsoft Teams hochladen
ms.topic: how-to
keywords: Hochladen von Teams-Apps
ms.openlocfilehash: 2e7a21dc27fdfe824ecacebabbb61a3b99ae8e79
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014341"
---
# <a name="upload-an-app-package-to-microsoft-teams"></a><span data-ttu-id="c2a18-104">Hochladen eines App-Pakets in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="c2a18-104">Upload an app package to Microsoft Teams</span></span>

<span data-ttu-id="c2a18-105">Um Ihre App in Microsoft Teams zu testen, müssen Sie Ihre App in Teams hochladen.</span><span class="sxs-lookup"><span data-stu-id="c2a18-105">To test your app experience within Microsoft Teams, you need to upload your app to Teams.</span></span> <span data-ttu-id="c2a18-106">Durch das Hochladen wird die App zu dem ausgewählten Team addiert, und Sie und Ihre Teammitglieder können wie Endbenutzer damit interagieren.</span><span class="sxs-lookup"><span data-stu-id="c2a18-106">Uploading adds the app to the team you select, and you and your team members can interact with it like end users.</span></span>

> [!NOTE]
> <span data-ttu-id="c2a18-107">Beim Hochladen eines aktualisierten Pakets für eine vorhandene App mit einem Bot werden beim Anzeigen über das Fenster "Unterhaltungen" möglicherweise keine Registerkartenänderungen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c2a18-107">Uploading an updated package for an existing app with a bot might not show tab changes when viewed through the Conversations window.</span></span> <span data-ttu-id="c2a18-108">Es ist besser, über das Flyout "Apps" darauf zu zugreifen oder in einer sauberen Testumgebung zu testen.</span><span class="sxs-lookup"><span data-stu-id="c2a18-108">It's better to access it via the Apps fly-out, or test on a clean test environment.</span></span>

## <a name="create-your-upload-package"></a><span data-ttu-id="c2a18-109">Erstellen des Uploadpakets</span><span class="sxs-lookup"><span data-stu-id="c2a18-109">Create your upload package</span></span>

<span data-ttu-id="c2a18-110">Für die Entwicklung sowie die AppSource-Übermittlung (früher Office Store) müssen Sie ein hochladebares Paket erstellen, das die Informationen enthält, um Ihre Erfahrung zu beschreiben.</span><span class="sxs-lookup"><span data-stu-id="c2a18-110">For development as well as AppSource (formerly Office Store) submission you must create an uploadable package that contains the information to describe your experience.</span></span> <span data-ttu-id="c2a18-111">Das Paket, eine ZIP-Datei, enthält das Anwendungsmanifest und Symbole, die Ihre Erfahrung eindeutig definieren.</span><span class="sxs-lookup"><span data-stu-id="c2a18-111">The package, a .zip file, contains the application manifest and icons that uniquely define your experience.</span></span>

<span data-ttu-id="c2a18-112">Informationen zum Erstellen eines Uploadpakets finden Sie unter [Erstellen des Pakets für Ihre Microsoft Teams-App.](../build-and-test/apps-package.md)</span><span class="sxs-lookup"><span data-stu-id="c2a18-112">To create an upload package, see [Create the package for your Microsoft Teams app](../build-and-test/apps-package.md).</span></span>

<span data-ttu-id="c2a18-113">Nachdem Das Paket erstellt wurde, können Sie es nun in ein Team hochladen.</span><span class="sxs-lookup"><span data-stu-id="c2a18-113">With your package created, you can now upload it into a team.</span></span> <span data-ttu-id="c2a18-114">Nach dem Hochladen ist es für alle Benutzer im ausgewählten Team und nur für die Benutzer dieses Teams verfügbar.</span><span class="sxs-lookup"><span data-stu-id="c2a18-114">Once uploaded it will be available for all users in the selected team, and only the users of that team.</span></span>

## <a name="load-your-package-into-teams"></a><span data-ttu-id="c2a18-115">Laden Des Pakets in Teams</span><span class="sxs-lookup"><span data-stu-id="c2a18-115">Load your package into Teams</span></span>

<span data-ttu-id="c2a18-116">Sie können Ihr Paket testen, indem Sie es in Teams hochladen.</span><span class="sxs-lookup"><span data-stu-id="c2a18-116">You can test your package by uploading it into Teams.</span></span>

> [!NOTE]
> <span data-ttu-id="c2a18-117">Damit das Hochladen funktioniert, muss Ihr Mandantenadministrator zuerst [das Hochladen von Apps aktivieren.](/microsoftteams/admin-settings)</span><span class="sxs-lookup"><span data-stu-id="c2a18-117">For uploading to work, your tenant admin must first [enable uploading of apps](/microsoftteams/admin-settings).</span></span>

<span data-ttu-id="c2a18-118">Es gibt zwei Möglichkeiten, Ihre App in Teams hochzuladen:</span><span class="sxs-lookup"><span data-stu-id="c2a18-118">There are two ways to upload your app to Teams:</span></span>

* <span data-ttu-id="c2a18-119">Verwenden des Store</span><span class="sxs-lookup"><span data-stu-id="c2a18-119">Using the Store</span></span>
* <span data-ttu-id="c2a18-120">Verwenden der Registerkarte "Apps"</span><span class="sxs-lookup"><span data-stu-id="c2a18-120">Using the Apps tab</span></span>

## <a name="upload-your-package-into-a-team-or-conversation-using-the-store"></a><span data-ttu-id="c2a18-121">Hochladen Ihres Pakets in ein Team oder eine Unterhaltung mithilfe des Store</span><span class="sxs-lookup"><span data-stu-id="c2a18-121">Upload your package into a team or conversation using the Store</span></span>

1. <span data-ttu-id="c2a18-122">Wählen Sie in der unteren linken Ecke von Teams das Symbol "Store" aus.</span><span class="sxs-lookup"><span data-stu-id="c2a18-122">In the lower left corner of Teams, choose the Store icon.</span></span> <span data-ttu-id="c2a18-123">Wählen Sie auf der Seite "Store" die Option "Benutzerdefinierte App hochladen" aus.</span><span class="sxs-lookup"><span data-stu-id="c2a18-123">On the Store page, choose "Upload a custom app".</span></span>

  ![Team anzeigen](../../assets/images/store-upload-a-custom-app2.png)

2. <span data-ttu-id="c2a18-125">Navigieren Sie *im Dialogfeld* "Öffnen" zu dem Paket, das Sie hochladen möchten, und wählen Sie *"Öffnen" aus.*</span><span class="sxs-lookup"><span data-stu-id="c2a18-125">In the *Open* dialog, navigate to the package you want to upload and choose *Open*.</span></span>

   ![Menü "Hinzufügen"](../../assets/images/NewappAddmenudropdown.png)

<span data-ttu-id="c2a18-127">Das hochgeladene Paket sollte jetzt für die Verwendung in dem im Zustimmungsdialogfeld angegebenen Team oder der Unterhaltung verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="c2a18-127">The uploaded package should now be available for use in the team or conversation specified in the consent dialog.</span></span> <span data-ttu-id="c2a18-128">Wenn Ihre App nicht angezeigt wird, ist der häufigste Grund ein Fehler im Manifest, insbesondere IDs für die App, Bot- und Messagingerweiterungen.</span><span class="sxs-lookup"><span data-stu-id="c2a18-128">If your app does not appear, the most common reason is an error in the manifest, particularly ids for the app, bot and messaging extensions.</span></span> <span data-ttu-id="c2a18-129">Wenn die App nicht für Unterhaltungen gilt, wird diese Option nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c2a18-129">If the app is not scoped for conversations, that option will not appear.</span></span>

>[!NOTE]
> <span data-ttu-id="c2a18-130">Apps in Unterhaltungen befinden sich derzeit in [Developer Preview](../../resources/dev-preview/developer-preview-intro.md), und die Option wird nicht angezeigt, wenn Teams nicht in diesem Modus ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c2a18-130">Apps in conversations is currently in [Developer Preview](../../resources/dev-preview/developer-preview-intro.md), and the option will not appear if Teams is not running in that mode.</span></span>

![Beispiel für einen Bot in der Liste der hochgeladenen Bots](../../assets/images/botinlist.jpg)

## <a name="upload-your-package-into-a-team-using-the-apps-tab"></a><span data-ttu-id="c2a18-132">Hochladen Ihres Pakets in ein Team über die Registerkarte "Apps"</span><span class="sxs-lookup"><span data-stu-id="c2a18-132">Upload your package into a team using the Apps tab</span></span>

1. <span data-ttu-id="c2a18-133">Wählen Sie im Zielteam *"Weitere Optionen"* (**&#8943;**) und *"Team verwalten" aus.*</span><span class="sxs-lookup"><span data-stu-id="c2a18-133">In the target team, choose *More options* (**&#8943;**) and choose *Manage team*.</span></span>

   > [!NOTE]
   > <span data-ttu-id="c2a18-134">Sie müssen der Teambesitzer sein, oder der Besitzer muss zulassen, dass Benutzer die entsprechenden App-Typen hinzufügen, damit diese Funktion angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="c2a18-134">You must be the team owner, or the owner must allow users to add the appropriate app types for this functionality to appear.</span></span>

2. <span data-ttu-id="c2a18-135">Wählen Sie die Registerkarte "Apps" und dann unten rechts *"Benutzerdefinierte* App hochladen" aus.</span><span class="sxs-lookup"><span data-stu-id="c2a18-135">Select the Apps tab, and then choose *Upload a custom app* on the lower right.</span></span>

   ![Einstiegspunkt hochladen](../../assets/images/UploadACustomApp.png)

3. <span data-ttu-id="c2a18-137">Navigieren Sie auf Ihrem Computer zu Ihrem ZIP-Paket, und wählen Sie es aus.</span><span class="sxs-lookup"><span data-stu-id="c2a18-137">Browse to and select your .zip package from your computer.</span></span>

4. <span data-ttu-id="c2a18-138">Nach einer kurzen Pause wird Die hochgeladene App in der Liste angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c2a18-138">After a brief pause you will see your uploaded app in the list.</span></span>

   ![Beispiel für einen Bot in der Liste der hochgeladenen Bots](../../assets/images/botinlist.jpg)

<span data-ttu-id="c2a18-140">Wenn Ihre App nicht geladen wird, ist der häufigste Grund ein Fehler im Manifest, insbesondere IDs für die App, Bot- und Messagingerweiterungen.</span><span class="sxs-lookup"><span data-stu-id="c2a18-140">If your app does not load, the most common reason is an error in the manifest, particularly ids for the app, bot and messaging extensions.</span></span>

## <a name="accessing-your-uploaded-configurable-tab"></a><span data-ttu-id="c2a18-141">Zugreifen auf die hochgeladene konfigurierbare Registerkarte</span><span class="sxs-lookup"><span data-stu-id="c2a18-141">Accessing your uploaded configurable tab</span></span>

<span data-ttu-id="c2a18-142">Wenn die App Registerkarten enthält, können Benutzer sie mithilfe des standardmäßigen Registerkartenkatalogflusses an eine beliebige Unterhaltung oder einen beliebigen Teamkanal anheften:</span><span class="sxs-lookup"><span data-stu-id="c2a18-142">If the app contains tabs, users can pin them to any conversation or team channel using the standard tab gallery flow:</span></span>

1. <span data-ttu-id="c2a18-143">Wechseln Sie zu einem Kanal im Team.</span><span class="sxs-lookup"><span data-stu-id="c2a18-143">Go to a channel in the team.</span></span> <span data-ttu-id="c2a18-144">Wählen Sie rechts neben den vorhandenen Registerkarten die Option ( Registerkarte *+* hinzufügen) aus.</span><span class="sxs-lookup"><span data-stu-id="c2a18-144">Choose *+* (*Add a tab*) to the right of the existing tabs.</span></span>

2. <span data-ttu-id="c2a18-145">Wählen Sie die Registerkarte aus dem angezeigten Katalog aus.</span><span class="sxs-lookup"><span data-stu-id="c2a18-145">Select your tab from the gallery that appears.</span></span>

3. <span data-ttu-id="c2a18-146">Akzeptieren Sie die Zustimmungsaufforderung.</span><span class="sxs-lookup"><span data-stu-id="c2a18-146">Accept the consent prompt.</span></span>

4. <span data-ttu-id="c2a18-147">Konfigurieren Sie die Registerkarte über die [Konfigurationsseite,](../../tabs/how-to/create-tab-pages/configuration-page.md) und wählen Sie *"Speichern" aus.*</span><span class="sxs-lookup"><span data-stu-id="c2a18-147">Configure your tab via its [configuration page](../../tabs/how-to/create-tab-pages/configuration-page.md) and choose *Save*.</span></span>

  ![Das Dialogfeld "Registerkarte hinzufügen" mit einem Katalog verfügbarer Registerkarten](../../assets/images/tab_gallery.png)

## <a name="accessing-your-uploaded-bot"></a><span data-ttu-id="c2a18-149">Zugreifen auf Ihren hochgeladenen Bot</span><span class="sxs-lookup"><span data-stu-id="c2a18-149">Accessing your uploaded bot</span></span>

<span data-ttu-id="c2a18-150">Wenn Sie einen Bot zu einem Team hinzufügen, sollte er je nach Definition des Botbereichs von allen Personen in diesem Team innerhalb und außerhalb der Teamkanäle verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="c2a18-150">When you add a bot to a team, it should be usable by anyone on that team, inside and outside the team channels, depending on bot scope definition.</span></span> <span data-ttu-id="c2a18-151">You and other team members will see a post in the General channel indicating that the bot has been added to the team.</span><span class="sxs-lookup"><span data-stu-id="c2a18-151">You and other team members will see a post in the General channel indicating that the bot has been added to the team.</span></span>

<span data-ttu-id="c2a18-152">Für einen teamsfähigen Bot können Sie beginnen, indem Sie Ihren Bot aufrufen, indem @mentioning Namen des Bots eingeben, der automatisch kompletiert werden sollte.</span><span class="sxs-lookup"><span data-stu-id="c2a18-152">For a teams-enabled bot, you can start by invoking your bot by @mentioning the name of the bot, which should autocomplete.</span></span>

<span data-ttu-id="c2a18-153">Um direkte Chats mit Ihrem Bot zu testen, können Sie entweder über die App-Startseite darauf zugreifen, @mention in einem Kanal darauf zugreifen oder im Fenster "Neuer **Chat"** suchen.</span><span class="sxs-lookup"><span data-stu-id="c2a18-153">To test direct chats with your bot, you can either access it via the App home, @mention it in a channel, or search for it in the **New Chat** window.</span></span>

<span data-ttu-id="c2a18-154">Wenn Sie Ihren Bot zu einer Unterhaltung hinzufügen, um direkte Chats mit Ihrem Bot zu testen, können Sie @mention in einer Unterhaltung anzeigen oder im Fenster "Neuer **Chat"** nach ihm suchen.</span><span class="sxs-lookup"><span data-stu-id="c2a18-154">When you add your bot to a conversation To test direct chats with your bot, you can @mention it in a conversation, or search for it in the **New Chat** window.</span></span>

## <a name="accessing-your-uploaded-connector"></a><span data-ttu-id="c2a18-155">Zugreifen auf den hochgeladenen Connector</span><span class="sxs-lookup"><span data-stu-id="c2a18-155">Accessing your uploaded Connector</span></span>

<span data-ttu-id="c2a18-156">Wenn die App im Team oder in der Unterhaltung geladen ist, können Benutzer einen Connector mithilfe des standardmäßigen Connectorskatalogflusses einrichten:</span><span class="sxs-lookup"><span data-stu-id="c2a18-156">With the app loaded in the team or conversation, users can set up a Connector using the standard Connectors gallery flow:</span></span>

1. <span data-ttu-id="c2a18-157">Wechseln Sie zu einem Kanal im Team.</span><span class="sxs-lookup"><span data-stu-id="c2a18-157">Go to a channel in the team.</span></span> <span data-ttu-id="c2a18-158">Choose *More options* (*&#8943;*) and choose *Connectors*.</span><span class="sxs-lookup"><span data-stu-id="c2a18-158">Choose *More options* (*&#8943;*) and choose *Connectors*.</span></span>

2. <span data-ttu-id="c2a18-159">Wählen Sie den Connector im **Abschnitt "Sideloaded"** unten aus.</span><span class="sxs-lookup"><span data-stu-id="c2a18-159">Select your Connector from the **Sideloaded** section at the bottom.</span></span>

3. <span data-ttu-id="c2a18-160">Konfigurieren Sie den Connector über die [Konfigurationsseite, und](../../webhooks-and-connectors/how-to/connectors-creating.md) wählen Sie *"Speichern" aus.*</span><span class="sxs-lookup"><span data-stu-id="c2a18-160">Configure your Connector via its [configuration page](../../webhooks-and-connectors/how-to/connectors-creating.md) and choose *Save*.</span></span>

  ![Das Dialogfeld "Registerkarte hinzufügen" mit einem Katalog verfügbarer Registerkarten.](../../assets/images/connector_gallery.png)

## <a name="accessing-your-uploaded-messaging-extension"></a><span data-ttu-id="c2a18-162">Zugreifen auf Ihre hochgeladene Messagingerweiterung</span><span class="sxs-lookup"><span data-stu-id="c2a18-162">Accessing your uploaded messaging extension</span></span>

<span data-ttu-id="c2a18-163">Eine hochgeladene App mit einer Messagingerweiterung wird automatisch im Menü "Weitere *Optionen"* (*&#8943;*) im Feld zum Verfassen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c2a18-163">An uploaded app with a messaging extension automatically appears in the *More options* (*&#8943;*) menu in the compose box.</span></span>

![Messaging-Erweiterungen](../../assets/images/compose-extensions/cesampleapp.png)

## <a name="removing-or-updating-your-app"></a><span data-ttu-id="c2a18-165">Entfernen oder Aktualisieren Ihrer App</span><span class="sxs-lookup"><span data-stu-id="c2a18-165">Removing or updating your app</span></span>

<span data-ttu-id="c2a18-166">Wenn Sie Ihre App entfernen möchten, wählen Sie das Papierkorbsymbol neben dem Namen der App in der Liste "Teams-Bots anzeigen" aus.</span><span class="sxs-lookup"><span data-stu-id="c2a18-166">If you want to remove your app, select the trash-can icon next to the app name in the View Teams bots list.</span></span>

<span data-ttu-id="c2a18-167">Wenn Sie Manifestinformationen ändern, müssen Sie zuerst die App entfernen und dann das aktualisierte Paket hinzufügen (pro Paket in [ein Team laden).](#load-your-package-into-teams)</span><span class="sxs-lookup"><span data-stu-id="c2a18-167">If you change manifest information, you must first remove the app and then add the updated package (per [Load your package into a team](#load-your-package-into-teams)).</span></span> <span data-ttu-id="c2a18-168">Beachten Sie, dass Codeänderungen an Ihrem Dienst im Allgemeinen kein erneutes Hochladen Ihres Manifests erfordern, es sei denn, diese Änderungen erfordern Manifestupdates (z. B. Änderungen an der URL oder der Microsoft-App-ID für den Bot).</span><span class="sxs-lookup"><span data-stu-id="c2a18-168">Note that, in general, code changes on your service do not require you to re-upload your manifest, unless those changes require manifest updates (such as changes to the URL or the Microsoft app ID for its bot).</span></span>

> [!NOTE]
> <span data-ttu-id="c2a18-169">Es gibt keine Möglichkeit, einen Bot vollständig aus dem persönlichen Kontext zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="c2a18-169">There is no way to completely remove a bot from personal context.</span></span> <span data-ttu-id="c2a18-170">Wenn der Bot entfernt und erneut hinzugefügt wird, wird die zusätzliche Kommunikation mit dem Bot an die vorherige Unterhaltung angehängt.</span><span class="sxs-lookup"><span data-stu-id="c2a18-170">If the bot is removed and re-added, additional communication with the bot will append to the previous conversation.</span></span>

## <a name="troubleshooting-notes"></a><span data-ttu-id="c2a18-171">Hinweise zur Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="c2a18-171">Troubleshooting notes</span></span>

* <span data-ttu-id="c2a18-172">If the manifest doesn't load, please double-check that you followed all the instructions in [Create the package](../../concepts/build-and-test/apps-package.md) and validated your manifest against the [schema](../../resources/schema/manifest-schema.md).</span><span class="sxs-lookup"><span data-stu-id="c2a18-172">If the manifest doesn't load, please double-check that you followed all the instructions in [Create the package](../../concepts/build-and-test/apps-package.md) and validated your manifest against the [schema](../../resources/schema/manifest-schema.md).</span></span>
