---
title: Hochladen Ihrer benutzerdefinierten app in Microsoft Teams
description: Beschreibt, wie Sie Ihre APP in Microsoft Teams hochladen
keywords: Upload von Teams-apps
ms.openlocfilehash: 256a9bea48ed816f2e9912006dd2fe7301743919
ms.sourcegitcommit: 61c93b22490526b1de87c0b14a3c7eb6e046caf6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2020
ms.locfileid: "44453882"
---
# <a name="upload-an-app-package-to-microsoft-teams"></a><span data-ttu-id="0201d-104">Hochladen eines App-Pakets in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="0201d-104">Upload an app package to Microsoft Teams</span></span>

<span data-ttu-id="0201d-105">Um Ihre APP-Erfahrung in Microsoft Teams zu testen, müssen Sie Ihre APP in Teams hochladen.</span><span class="sxs-lookup"><span data-stu-id="0201d-105">To test your app experience within Microsoft Teams, you need to upload your app to Teams.</span></span> <span data-ttu-id="0201d-106">Durch Hochladen wird die APP dem ausgewählten Team hinzugefügt, und Sie und Ihre Teammitglieder können wie Endbenutzer mit ihr interagieren.</span><span class="sxs-lookup"><span data-stu-id="0201d-106">Uploading adds the app to the team you select, and you and your team members can interact with it like end users.</span></span>

> [!NOTE]
> <span data-ttu-id="0201d-107">Beim Hochladen eines aktualisierten Pakets für eine vorhandene App mit einem bot werden im Fenster Unterhaltungen möglicherweise keine Registerkarten Änderungen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0201d-107">Uploading an updated package for an existing app with a bot might not show tab changes when viewed through the Conversations window.</span></span> <span data-ttu-id="0201d-108">Es ist besser, über das Apps-Fly-Out darauf zuzugreifen oder auf eine saubere Testumgebung zu testen.</span><span class="sxs-lookup"><span data-stu-id="0201d-108">It's better to access it via the Apps fly-out, or test on a clean test environment.</span></span>

## <a name="create-your-upload-package"></a><span data-ttu-id="0201d-109">Erstellen des Upload-Pakets</span><span class="sxs-lookup"><span data-stu-id="0201d-109">Create your upload package</span></span>

<span data-ttu-id="0201d-110">Für die Entwicklung als auch für AppSource (ehemals Office Store)-Übermittlung müssen Sie ein uploadable-Paket erstellen, das die Informationen zum Beschreiben Ihrer Benutzeroberfläche enthält.</span><span class="sxs-lookup"><span data-stu-id="0201d-110">For development as well as AppSource (formerly Office Store) submission you must create an uploadable package that contains the information to describe your experience.</span></span> <span data-ttu-id="0201d-111">Das Paket, eine ZIP-Datei, enthält das Anwendungsmanifest und die Symbole, die Ihre Benutzeroberfläche eindeutig definieren.</span><span class="sxs-lookup"><span data-stu-id="0201d-111">The package, a .zip file, contains the application manifest and icons that uniquely define your experience.</span></span>

<span data-ttu-id="0201d-112">Informationen zum Erstellen eines Upload-Pakets finden Sie unter [Erstellen des Pakets für Ihre Microsoft Teams-App](../build-and-test/apps-package.md).</span><span class="sxs-lookup"><span data-stu-id="0201d-112">To create an upload package, see [Create the package for your Microsoft Teams app](../build-and-test/apps-package.md).</span></span>

<span data-ttu-id="0201d-113">Wenn Ihr Paket erstellt wurde, können Sie es jetzt in ein Team hochladen.</span><span class="sxs-lookup"><span data-stu-id="0201d-113">With your package created, you can now upload it into a team.</span></span> <span data-ttu-id="0201d-114">Sobald hochgeladen, steht sie für alle Benutzer im ausgewählten Team und nur für die Benutzer dieses Teams zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="0201d-114">Once uploaded it will be available for all users in the selected team, and only the users of that team.</span></span>

## <a name="load-your-package-into-teams"></a><span data-ttu-id="0201d-115">Laden Ihres Pakets in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="0201d-115">Load your package into Teams</span></span>

<span data-ttu-id="0201d-116">Sie können Ihr Paket testen, indem Sie es in Teams hochladen.</span><span class="sxs-lookup"><span data-stu-id="0201d-116">You can test your package by uploading it into Teams.</span></span>

> [!NOTE]
> <span data-ttu-id="0201d-117">Damit das Hochladen funktioniert, muss Ihr mandantenadministrator zunächst das [Hochladen von Apps aktivieren](/microsoftteams/admin-settings).</span><span class="sxs-lookup"><span data-stu-id="0201d-117">For uploading to work, your tenant admin must first [enable uploading of apps](/microsoftteams/admin-settings).</span></span>

<span data-ttu-id="0201d-118">Es gibt zwei Möglichkeiten, Ihre APP in Microsoft Teams hochzuladen:</span><span class="sxs-lookup"><span data-stu-id="0201d-118">There are two ways to upload your app to Teams:</span></span>

* <span data-ttu-id="0201d-119">Verwenden des Stores</span><span class="sxs-lookup"><span data-stu-id="0201d-119">Using the Store</span></span>
* <span data-ttu-id="0201d-120">Verwenden der Registerkarte "Apps"</span><span class="sxs-lookup"><span data-stu-id="0201d-120">Using the Apps tab</span></span>

## <a name="upload-your-package-into-a-team-or-conversation-using-the-store"></a><span data-ttu-id="0201d-121">Laden Sie Ihr Paket mit dem Store in ein Team oder eine Unterhaltung hoch.</span><span class="sxs-lookup"><span data-stu-id="0201d-121">Upload your package into a team or conversation using the Store</span></span>

1. <span data-ttu-id="0201d-122">Wählen Sie in der unteren linken Ecke von Microsoft Teams das Symbol Store aus.</span><span class="sxs-lookup"><span data-stu-id="0201d-122">In the lower left corner of Teams, choose the Store icon.</span></span> <span data-ttu-id="0201d-123">Wählen Sie auf der Seite Store die Option "benutzerdefinierte App hochladen" aus.</span><span class="sxs-lookup"><span data-stu-id="0201d-123">On the Store page, choose "Upload a custom app".</span></span>

   ![Team anzeigen](../../assets/images/store-upload-a-custom-app.png)

2. <span data-ttu-id="0201d-125">Navigieren Sie im Dialogfeld *Öffnen* zu dem Paket, das Sie hochladen möchten, und wählen Sie *Öffnen*aus.</span><span class="sxs-lookup"><span data-stu-id="0201d-125">In the *Open* dialog, navigate to the package you want to upload and choose *Open*.</span></span>

<span data-ttu-id="0201d-126">Das hochgeladene Paket sollte jetzt für die Verwendung in der im Zustimmungsdialogfeld angegebenen Gruppe oder Unterhaltung zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="0201d-126">The uploaded package should now be available for use in the team or conversation specified in the consent dialog.</span></span> <span data-ttu-id="0201d-127">Wenn Ihre APP nicht angezeigt wird, ist der häufigste Grund ein Fehler im Manifest, insbesondere IDs für die APP-, bot-und Messaging-Erweiterungen.</span><span class="sxs-lookup"><span data-stu-id="0201d-127">If your app does not appear, the most common reason is an error in the manifest, particularly ids for the app, bot and messaging extensions.</span></span> <span data-ttu-id="0201d-128">Wenn die APP nicht für Unterhaltungen ausgelegt ist, wird diese Option nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0201d-128">If the app is not scoped for conversations, that option will not appear.</span></span>

>[!NOTE]
> <span data-ttu-id="0201d-129">Apps in Unterhaltungen befinden sich derzeit in der [Entwicklervorschau](../../resources/dev-preview/developer-preview-intro.md), und die Option wird nicht angezeigt, wenn Teams nicht in diesem Modus ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="0201d-129">Apps in conversations is currently in [Developer Preview](../../resources/dev-preview/developer-preview-intro.md), and the option will not appear if Teams is not running in that mode.</span></span>

![Beispiel für bot in der Liste der hochgeladenen Bots](../../assets/images/botinlist.jpg)

## <a name="upload-your-package-into-a-team-using-the-apps-tab"></a><span data-ttu-id="0201d-131">Hochladen des Pakets mithilfe der Registerkarte "Apps" in ein Team</span><span class="sxs-lookup"><span data-stu-id="0201d-131">Upload your package into a team using the Apps tab</span></span>

1. <span data-ttu-id="0201d-132">Wählen Sie im Ziel Team *Weitere Optionen* (**&#8943;**) aus, und wählen Sie *Team verwalten*aus.</span><span class="sxs-lookup"><span data-stu-id="0201d-132">In the target team, choose *More options* (**&#8943;**) and choose *Manage team*.</span></span>

   > [!NOTE]
   > <span data-ttu-id="0201d-133">Sie müssen der Teambesitzer sein, oder der Besitzer muss zulassen, dass Benutzer die entsprechenden App-Typen hinzufügen, damit diese Funktion angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="0201d-133">You must be the team owner, or the owner must allow users to add the appropriate app types for this functionality to appear.</span></span>

2. <span data-ttu-id="0201d-134">Wählen Sie die Registerkarte Apps aus, und wählen Sie dann *eine benutzerdefinierte App* in der rechten oberen Ecke Hochladen aus.</span><span class="sxs-lookup"><span data-stu-id="0201d-134">Select the Apps tab, and then choose *Upload a custom app* on the lower right.</span></span>

   ![Einstiegspfad hochladen](../../assets/images/UploadACustomApp.png)

3. <span data-ttu-id="0201d-136">Navigieren Sie zu Ihrem ZIP-Paket auf Ihrem Computer, und wählen Sie es aus.</span><span class="sxs-lookup"><span data-stu-id="0201d-136">Browse to and select your .zip package from your computer.</span></span>

4. <span data-ttu-id="0201d-137">Nach einer kurzen Pause wird Ihre hochgeladene app in der Liste angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0201d-137">After a brief pause you will see your uploaded app in the list.</span></span>

   ![Beispiel für bot in der Liste der hochgeladenen Bots](../../assets/images/botinlist.jpg)

<span data-ttu-id="0201d-139">Wenn Ihre APP nicht lädt, ist der häufigste Grund ein Fehler im Manifest, insbesondere IDs für die APP-, bot-und Messaging-Erweiterungen.</span><span class="sxs-lookup"><span data-stu-id="0201d-139">If your app does not load, the most common reason is an error in the manifest, particularly ids for the app, bot and messaging extensions.</span></span>

## <a name="accessing-your-uploaded-configurable-tab"></a><span data-ttu-id="0201d-140">Zugreifen auf die konfigurierbare Registerkarte "hochgeladen"</span><span class="sxs-lookup"><span data-stu-id="0201d-140">Accessing your uploaded configurable tab</span></span>

<span data-ttu-id="0201d-141">Wenn die APP Registerkarten enthält, können Benutzer Sie an jede Unterhaltung oder einen Team Kanal mit dem standardmäßigen Tab Gallery Flow anheften:</span><span class="sxs-lookup"><span data-stu-id="0201d-141">If the app contains tabs, users can pin them to any conversation or team channel using the standard tab gallery flow:</span></span>

1. <span data-ttu-id="0201d-142">Wechseln Sie zu einem Kanal im Team.</span><span class="sxs-lookup"><span data-stu-id="0201d-142">Go to a channel in the team.</span></span> <span data-ttu-id="0201d-143">Klicken Sie *+* auf der rechten Seite der vorhandenen Registerkarten auf (*Registerkarte hinzufügen*).</span><span class="sxs-lookup"><span data-stu-id="0201d-143">Choose *+* (*Add a tab*) to the right of the existing tabs.</span></span>

2. <span data-ttu-id="0201d-144">Wählen Sie in der angezeigten Galerie die Registerkarte aus.</span><span class="sxs-lookup"><span data-stu-id="0201d-144">Select your tab from the gallery that appears.</span></span>

3. <span data-ttu-id="0201d-145">Akzeptieren Sie die Zustimmungsaufforderung.</span><span class="sxs-lookup"><span data-stu-id="0201d-145">Accept the consent prompt.</span></span>

4. <span data-ttu-id="0201d-146">Konfigurieren Sie die Registerkarte über die [Konfigurationsseite](../../tabs/how-to/create-tab-pages/configuration-page.md) , und wählen Sie *Speichern*aus.</span><span class="sxs-lookup"><span data-stu-id="0201d-146">Configure your tab via its [configuration page](../../tabs/how-to/create-tab-pages/configuration-page.md) and choose *Save*.</span></span>

  ![Das Dialogfeld "Register hinzufügen" mit einem Katalog verfügbarer Registerkarten](../../assets/images/tab_gallery.png)

## <a name="accessing-your-uploaded-bot"></a><span data-ttu-id="0201d-148">Zugriff auf Ihren hochgeladenen bot</span><span class="sxs-lookup"><span data-stu-id="0201d-148">Accessing your uploaded bot</span></span>

<span data-ttu-id="0201d-149">Wenn Sie einem Team einen bot hinzufügen, sollte er je nach der Bereichsdefinition des bot von jedem Benutzer in diesem Team innerhalb und außerhalb der Team Kanäle verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="0201d-149">When you add a bot to a team, it should be usable by anyone on that team, inside and outside the team channels, depending on bot scope definition.</span></span> <span data-ttu-id="0201d-150">Ihnen und anderen Teammitgliedern wird ein Beitrag im allgemeinen Kanal angezeigt, der angibt, dass der bot dem Team hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="0201d-150">You and other team members will see a post in the General channel indicating that the bot has been added to the team.</span></span>

<span data-ttu-id="0201d-151">Für einen Teams-fähigen bot können Sie zunächst Ihren bot aufrufen, indem Sie @mentioning den Namen des bot, der AutoVervollständigen sollte.</span><span class="sxs-lookup"><span data-stu-id="0201d-151">For a teams-enabled bot, you can start by invoking your bot by @mentioning the name of the bot, which should autocomplete.</span></span>

<span data-ttu-id="0201d-152">Um direkte Chats mit Ihrem bot zu testen, können Sie entweder über das App-Home darauf zugreifen, es in einem Kanal @Mention oder im **neuen Chat** Fenster danach suchen.</span><span class="sxs-lookup"><span data-stu-id="0201d-152">To test direct chats with your bot, you can either access it via the App home, @mention it in a channel, or search for it in the **New Chat** window.</span></span>

<span data-ttu-id="0201d-153">Wenn Sie Ihren bot zu einer Unterhaltung hinzufügen, um direkte Chats mit Ihrem bot zu testen, können Sie ihn in einer Unterhaltung @Mention oder im **neuen Chat** Fenster suchen.</span><span class="sxs-lookup"><span data-stu-id="0201d-153">When you add your bot to a conversation To test direct chats with your bot, you can @mention it in a conversation, or search for it in the **New Chat** window.</span></span>

## <a name="accessing-your-uploaded-connector"></a><span data-ttu-id="0201d-154">Zugreifen auf Ihren hochgeladenen Connector</span><span class="sxs-lookup"><span data-stu-id="0201d-154">Accessing your uploaded Connector</span></span>

<span data-ttu-id="0201d-155">Wenn die APP im Team oder in der Unterhaltung geladen ist, können Benutzer einen Connector mit dem standardmäßigen Konnektoren-Katalog Ablauf einrichten:</span><span class="sxs-lookup"><span data-stu-id="0201d-155">With the app loaded in the team or conversation, users can set up a Connector using the standard Connectors gallery flow:</span></span>

1. <span data-ttu-id="0201d-156">Wechseln Sie zu einem Kanal im Team.</span><span class="sxs-lookup"><span data-stu-id="0201d-156">Go to a channel in the team.</span></span> <span data-ttu-id="0201d-157">Wählen Sie *Weitere Optionen* (*&#8943;*) aus, und wählen Sie *Connectors*aus.</span><span class="sxs-lookup"><span data-stu-id="0201d-157">Choose *More options* (*&#8943;*) and choose *Connectors*.</span></span>

2. <span data-ttu-id="0201d-158">Wählen Sie Ihren Connector aus dem Abschnitt **hochgeladene** unten aus.</span><span class="sxs-lookup"><span data-stu-id="0201d-158">Select your Connector from the **Uploaded** section at the bottom.</span></span>

3. <span data-ttu-id="0201d-159">Konfigurieren Sie den Connector über die [Konfigurationsseite](../../webhooks-and-connectors/how-to/connectors-creating.md) , und wählen Sie *Speichern*aus.</span><span class="sxs-lookup"><span data-stu-id="0201d-159">Configure your Connector via its [configuration page](../../webhooks-and-connectors/how-to/connectors-creating.md) and choose *Save*.</span></span>

  ![Das DialogfeldRegister hinzufügen mit einem Katalog verfügbarer Registerkarten.](../../assets/images/connector_gallery.png)

## <a name="accessing-your-uploaded-messaging-extension"></a><span data-ttu-id="0201d-161">Zugriff auf Ihre hochgeladene Messaging Erweiterung</span><span class="sxs-lookup"><span data-stu-id="0201d-161">Accessing your uploaded messaging extension</span></span>

<span data-ttu-id="0201d-162">Eine hochgeladene App mit einer Messaging Erweiterung wird automatisch im Menü *Weitere Optionen* (*&#8943;*) im Feld Verfassen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0201d-162">An uploaded app with a messaging extension automatically appears in the *More options* (*&#8943;*) menu in the compose box.</span></span>

![Messaging-Erweiterungen](../../assets/images/compose-extensions/cesampleapp.png)

## <a name="removing-or-updating-your-app"></a><span data-ttu-id="0201d-164">Entfernen oder Aktualisieren Ihrer APP</span><span class="sxs-lookup"><span data-stu-id="0201d-164">Removing or updating your app</span></span>

<span data-ttu-id="0201d-165">Wenn Sie Ihre APP entfernen möchten, wählen Sie in der Liste Teams-Bots anzeigen neben dem APP-Namen das Papierkorbsymbol aus.</span><span class="sxs-lookup"><span data-stu-id="0201d-165">If you want to remove your app, select the trash-can icon next to the app name in the View Teams bots list.</span></span>

<span data-ttu-id="0201d-166">Wenn Sie Manifestinformationen ändern, müssen Sie zuerst die APP entfernen und dann das aktualisierte Paket hinzufügen (pro [Laden Ihres Pakets in ein Team](#load-your-package-into-teams)).</span><span class="sxs-lookup"><span data-stu-id="0201d-166">If you change manifest information, you must first remove the app and then add the updated package (per [Load your package into a team](#load-your-package-into-teams)).</span></span> <span data-ttu-id="0201d-167">Beachten Sie, dass für Codeänderungen in Ihrem Dienst im Allgemeinen keine erneute Hochladung des Manifests erforderlich ist, es sei denn, für diese Änderungen sind Manifeste Aktualisierungen erforderlich (beispielsweise Änderungen an der URL oder an der Microsoft App-ID für den bot).</span><span class="sxs-lookup"><span data-stu-id="0201d-167">Note that, in general, code changes on your service do not require you to re-upload your manifest, unless those changes require manifest updates (such as changes to the URL or the Microsoft app ID for its bot).</span></span>

> [!NOTE]
> <span data-ttu-id="0201d-168">Es gibt keine Möglichkeit, einen bot vollständig aus dem persönlichen Kontext zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="0201d-168">There is no way to completely remove a bot from personal context.</span></span> <span data-ttu-id="0201d-169">Wenn der bot entfernt und erneut hinzugefügt wird, wird die zusätzliche Kommunikation mit dem bot an die vorherige Unterhaltung angefügt.</span><span class="sxs-lookup"><span data-stu-id="0201d-169">If the bot is removed and re-added, additional communication with the bot will append to the previous conversation.</span></span>

## <a name="troubleshooting-notes"></a><span data-ttu-id="0201d-170">Problembehandlung bei Notizen</span><span class="sxs-lookup"><span data-stu-id="0201d-170">Troubleshooting notes</span></span>

* <span data-ttu-id="0201d-171">Wenn das Manifest nicht lädt, überprüfen Sie bitte, ob Sie alle Anweisungen unter [Erstellen des Pakets](../../concepts/build-and-test/apps-package.md) befolgt und Ihr Manifest anhand des [Schemas](../../resources/schema/manifest-schema.md)überprüft haben.</span><span class="sxs-lookup"><span data-stu-id="0201d-171">If the manifest doesn't load, please double-check that you followed all the instructions in [Create the package](../../concepts/build-and-test/apps-package.md) and validated your manifest against the [schema](../../resources/schema/manifest-schema.md).</span></span>

