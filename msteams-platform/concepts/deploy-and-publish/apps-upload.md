---
title: Hochladen Ihrer benutzerdefinierten App
description: Beschreibt, wie Sie Ihre App in Microsoft Teams hochladen
ms.topic: how-to
ms.author: lajanuar
keywords: Hochladen von Teams-Apps
ms.openlocfilehash: 3ca086cf8dbb992de84b22b7499f739d7c80b9d6
ms.sourcegitcommit: 9cfbc44912980a33d2d7c7c85739aeea6ccb41de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "50479882"
---
# <a name="upload-an-app-package-to-microsoft-teams"></a><span data-ttu-id="94b86-104">Hochladen eines App-Pakets in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="94b86-104">Upload an app package to Microsoft Teams</span></span>

<span data-ttu-id="94b86-105">Um Ihre App-Erfahrung in Microsoft Teams zu testen, müssen Sie Ihre App in Teams hochladen.</span><span class="sxs-lookup"><span data-stu-id="94b86-105">To test your app experience within Microsoft Teams, you need to upload your app to Teams.</span></span> <span data-ttu-id="94b86-106">Beim Hochladen wird die App zum ausgewählten Team hinzufügt, und alle Teammitglieder können wie Endbenutzer damit interagieren.</span><span class="sxs-lookup"><span data-stu-id="94b86-106">Uploading adds the app to the selected team and all the team members can interact with it like end users.</span></span>

> [!NOTE]
> <span data-ttu-id="94b86-107">Beim Hochladen eines aktualisierten Pakets für eine vorhandene App mit einem Bot werden möglicherweise keine Registerkartenänderungen angezeigt, wenn sie über das Unterhaltungsfenster angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="94b86-107">Uploading an updated package for an existing app with a bot might not show tab changes when viewed through the conversations window.</span></span> <span data-ttu-id="94b86-108">Sie können über das Fly-Out oder testen in einer sauberen Umgebung auf die App zugreifen.</span><span class="sxs-lookup"><span data-stu-id="94b86-108">You can access the app through the apps fly-out or test in a clean environment.</span></span>

## <a name="create-your-upload-package"></a><span data-ttu-id="94b86-109">Erstellen des Uploadpakets</span><span class="sxs-lookup"><span data-stu-id="94b86-109">Create your upload package</span></span>

<span data-ttu-id="94b86-110">Für die Entwicklung und AppSource-Übermittlung müssen Sie ein Paket erstellen, das Sie hochladen können.</span><span class="sxs-lookup"><span data-stu-id="94b86-110">For development and AppSource submission, you must create a package that you can upload.</span></span> <span data-ttu-id="94b86-111">Das Paket muss die Informationen enthalten, um Ihre Erfahrung zu beschreiben.</span><span class="sxs-lookup"><span data-stu-id="94b86-111">The package must contain the information to describe your experience.</span></span> <span data-ttu-id="94b86-112">Das Paket ist eine ZIP-Datei, die das Anwendungsmanifest und Symbole enthält, die Ihre Erfahrung eindeutig definieren.</span><span class="sxs-lookup"><span data-stu-id="94b86-112">The package is a .zip file that contains the application manifest and icons that uniquely define your experience.</span></span>

<span data-ttu-id="94b86-113">Informationen zum Erstellen eines Uploadpakets finden Sie unter [Erstellen des Pakets für Ihre Microsoft Teams-App.](../build-and-test/apps-package.md)</span><span class="sxs-lookup"><span data-stu-id="94b86-113">To create an upload package, see [Create the package for your Microsoft Teams app](../build-and-test/apps-package.md).</span></span>

<span data-ttu-id="94b86-114">Nachdem Sie das Paket erstellt haben, laden Sie es in ein Team hoch.</span><span class="sxs-lookup"><span data-stu-id="94b86-114">After you create the package, upload it into a team.</span></span> <span data-ttu-id="94b86-115">Das hochgeladene Paket steht nur den Benutzern des ausgewählten Teams zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="94b86-115">The uploaded package is only available to the users of the selected team.</span></span>

## <a name="load-your-package-into-teams"></a><span data-ttu-id="94b86-116">Laden Des Pakets in Teams</span><span class="sxs-lookup"><span data-stu-id="94b86-116">Load your package into Teams</span></span>

<span data-ttu-id="94b86-117">Sie können Ihr Paket testen, indem Sie es in Teams hochladen.</span><span class="sxs-lookup"><span data-stu-id="94b86-117">You can test your package by uploading it into Teams.</span></span>

> [!NOTE]
> <span data-ttu-id="94b86-118">Damit das Hochladen funktioniert, muss Ihr Mandantenadministrator zuerst [das Hochladen von Apps aktivieren.](/microsoftteams/admin-settings)</span><span class="sxs-lookup"><span data-stu-id="94b86-118">For uploading to work, your tenant admin must first [enable uploading of apps](/microsoftteams/admin-settings).</span></span>

<span data-ttu-id="94b86-119">Es gibt zwei Möglichkeiten, Ihre App in Teams hochzuladen:</span><span class="sxs-lookup"><span data-stu-id="94b86-119">There are two ways to upload your app to Teams:</span></span>

* <span data-ttu-id="94b86-120">Verwenden des Store</span><span class="sxs-lookup"><span data-stu-id="94b86-120">Using the Store</span></span>
* <span data-ttu-id="94b86-121">Verwenden der Registerkarte Apps</span><span class="sxs-lookup"><span data-stu-id="94b86-121">Using the Apps tab</span></span>

## <a name="upload-your-package-into-a-team-or-conversation-using-the-store"></a><span data-ttu-id="94b86-122">Hochladen Ihres Pakets in ein Team oder eine Unterhaltung mithilfe des Store</span><span class="sxs-lookup"><span data-stu-id="94b86-122">Upload your package into a team or conversation using the Store</span></span>

1. <span data-ttu-id="94b86-123">Wählen Sie in der unteren linken Ecke von Teams das **Symbol Store** aus.</span><span class="sxs-lookup"><span data-stu-id="94b86-123">In the lower left corner of Teams, choose the **Store** icon.</span></span> <span data-ttu-id="94b86-124">Wählen Sie auf der Seite Store die Option **Benutzerdefinierte App hochladen aus.**</span><span class="sxs-lookup"><span data-stu-id="94b86-124">On the Store page, choose **Upload a custom app**.</span></span>

  ![Team anzeigen](../../assets/images/store-upload-a-custom-app2.png)

2. <span data-ttu-id="94b86-126">Navigieren Sie **im** Dialogfeld Öffnen zu dem Paket, das Sie hochladen möchten, und wählen Sie Öffnen aus.</span><span class="sxs-lookup"><span data-stu-id="94b86-126">In the **Open** dialog, navigate to the package you want to upload and choose Open.</span></span>

   ![Menü hinzufügen](../../assets/images/NewappAddmenudropdown.png)

<span data-ttu-id="94b86-128">Das hochgeladene Paket muss für die Verwendung im Team oder der Im Zustimmungsdialogfeld angegebenen Unterhaltung verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="94b86-128">The uploaded package must be available for use in the team or conversation specified in the consent dialog.</span></span> <span data-ttu-id="94b86-129">Wenn Ihre App nicht angezeigt wird, ist der häufigste Grund ein Fehler im Manifest, insbesondere IDs für die App- und Bot- und Messagingerweiterungen.</span><span class="sxs-lookup"><span data-stu-id="94b86-129">If your app does not appear, the most common reason is an error in the manifest, particularly IDs for the app, bot, and messaging extensions.</span></span> <span data-ttu-id="94b86-130">Wenn die App nicht für Unterhaltungen begrenzt ist, wird diese Option nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="94b86-130">If the app is not scoped for conversations that option does not appear.</span></span>

>[!NOTE]
> <span data-ttu-id="94b86-131">Apps in Unterhaltungen befinden sich derzeit in [Developer Preview](../../resources/dev-preview/developer-preview-intro.md), und die Option wird nicht angezeigt, wenn Teams nicht in diesem Modus ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="94b86-131">Apps in conversations is currently in [Developer Preview](../../resources/dev-preview/developer-preview-intro.md), and the option does not appear if Teams is not running in that mode.</span></span>

![Beispiel für bot in der Liste der hochgeladenen Bots](../../assets/images/botinlist.jpg)

## <a name="upload-your-package-into-a-team-using-the-apps-tab"></a><span data-ttu-id="94b86-133">Hochladen Ihres Pakets in ein Team mithilfe der Registerkarte Apps</span><span class="sxs-lookup"><span data-stu-id="94b86-133">Upload your package into a team using the Apps tab</span></span>

1. <span data-ttu-id="94b86-134">Wählen Sie im Zielteam **weitere Optionen** (**&#8943;**) aus, und wählen Sie Team **verwalten aus.**</span><span class="sxs-lookup"><span data-stu-id="94b86-134">In the target team, choose **More options** (**&#8943;**) and select **Manage team**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="94b86-135">Sie müssen der Teambesitzer sein, oder der Besitzer muss Benutzern Zugriff geben, um die entsprechenden App-Typen hinzuzufügen, damit diese Funktionalität angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="94b86-135">You must be the team owner or the owner must give access to users to add the appropriate app types for this functionality to appear.</span></span>

2. <span data-ttu-id="94b86-136">Wählen Sie die **Registerkarte Apps** aus, und wählen Sie unten rechts **Hochladen** einer benutzerdefinierten App aus.</span><span class="sxs-lookup"><span data-stu-id="94b86-136">Select the **Apps** tab and choose **Upload a custom app** on the lower right.</span></span>

   ![Einstiegspunkt hochladen](../../assets/images/UploadACustomApp.png)

3. <span data-ttu-id="94b86-138">Wählen Sie ihr .zip-Paket vom Computer aus.</span><span class="sxs-lookup"><span data-stu-id="94b86-138">Select your .zip package from the computer.</span></span>

4. <span data-ttu-id="94b86-139">Die hochgeladene App wird in der Liste angezeigt.</span><span class="sxs-lookup"><span data-stu-id="94b86-139">You can see your uploaded app in the list.</span></span>

   ![Beispiel für bot in der Liste der hochgeladenen Bots](../../assets/images/botinlist.jpg)

<span data-ttu-id="94b86-141">Wenn Ihre App nicht geladen wird, ist der häufigste Grund ein Fehler im Manifest, insbesondere IDs für die App- und Bot- und Messagingerweiterungen.</span><span class="sxs-lookup"><span data-stu-id="94b86-141">If your app does not load, the most common reason is an error in the manifest, particularly IDs for the app, bot, and messaging extensions.</span></span>

## <a name="access-your-uploaded-configurable-tab"></a><span data-ttu-id="94b86-142">Zugreifen auf ihre hochgeladene konfigurierbare Registerkarte</span><span class="sxs-lookup"><span data-stu-id="94b86-142">Access your uploaded configurable tab</span></span>

<span data-ttu-id="94b86-143">Wenn die App Registerkarten enthält, können Benutzer sie mithilfe des standardmäßigen Registerkartenkatalogflusses an alle Unterhaltungen oder Teamkanäle anheften:</span><span class="sxs-lookup"><span data-stu-id="94b86-143">If the app contains tabs, users can pin them to any conversation or team channel using the standard tab gallery flow:</span></span>

1. <span data-ttu-id="94b86-144">Wechseln Sie zu einem Kanal im Team.</span><span class="sxs-lookup"><span data-stu-id="94b86-144">Go to a channel in the team.</span></span> <span data-ttu-id="94b86-145">Wählen Sie aus, um rechts neben den vorhandenen Registerkarten eine **+** Registerkarte hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="94b86-145">Choose **+** to add a tab to the right of the existing tabs.</span></span>

2. <span data-ttu-id="94b86-146">Wählen Sie ihre Registerkarte aus dem angezeigten Katalog aus.</span><span class="sxs-lookup"><span data-stu-id="94b86-146">Select your tab from the gallery that appears.</span></span>

3. <span data-ttu-id="94b86-147">Akzeptieren Sie die Zustimmungsaufforderung.</span><span class="sxs-lookup"><span data-stu-id="94b86-147">Accept the consent prompt.</span></span>

4. <span data-ttu-id="94b86-148">Konfigurieren Sie Ihre Registerkarte über die [Konfigurationsseite,](../../tabs/how-to/create-tab-pages/configuration-page.md) und wählen Sie **Speichern aus.**</span><span class="sxs-lookup"><span data-stu-id="94b86-148">Configure your tab through its [configuration page](../../tabs/how-to/create-tab-pages/configuration-page.md) and select **Save**.</span></span>

  ![Das Dialogfeld Registerkarte hinzufügen mit einem Katalog verfügbarer Registerkarten](../../assets/images/tab_gallery.png)

## <a name="access-your-uploaded-bot"></a><span data-ttu-id="94b86-150">Zugreifen auf ihren hochgeladenen Bot</span><span class="sxs-lookup"><span data-stu-id="94b86-150">Access your uploaded bot</span></span>

<span data-ttu-id="94b86-151">Nach dem Hinzufügen des Bots zu einem Team muss er je nach Definition des Botbereichs von jedem Benutzer in diesem Team innerhalb und außerhalb der Teamkanäle verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="94b86-151">After adding the bot to a team, it must be usable by anyone on that team, inside and outside the team channels, depending on bot scope definition.</span></span> <span data-ttu-id="94b86-152">Allen Teammitgliedern wird ein Beitrag im Kanal **Allgemein** angezeigt, der angibt, dass der Bot dem Team hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="94b86-152">All team members can see a post in the **General** channel indicating that the bot has been added to the team.</span></span>

<span data-ttu-id="94b86-153">Für einen Teams-Bot können Sie ihren Bot zunächst aufrufen, indem @mentioning Namen des Bots eingeben.</span><span class="sxs-lookup"><span data-stu-id="94b86-153">For a Teams bot, you can start by invoking your bot by @mentioning the name of the bot.</span></span>

<span data-ttu-id="94b86-154">Um direkte Chats mit Ihrem Bot zu testen, können Sie entweder über die App-Startseite darauf zugreifen, @mention in einem Kanal darauf zugreifen oder im Fenster Neuer **Chat** nach ihm suchen.</span><span class="sxs-lookup"><span data-stu-id="94b86-154">To test direct chats with your bot, you can either access it through the App home, @mention it in a channel, or search for it in the **New Chat** window.</span></span>

<span data-ttu-id="94b86-155">Sie können @mention bot in einer Unterhaltung anzeigen oder im Fenster Neuer **Chat** suchen, um direkte Chats mit Ihrem Bot zu testen.</span><span class="sxs-lookup"><span data-stu-id="94b86-155">You can @mention the bot in a conversation or search for it in the **New Chat** window to test direct chats with your bot.</span></span>

## <a name="access-your-uploaded-connector"></a><span data-ttu-id="94b86-156">Zugreifen auf ihren hochgeladenen Connector</span><span class="sxs-lookup"><span data-stu-id="94b86-156">Access your uploaded Connector</span></span>

<span data-ttu-id="94b86-157">Wenn die App in das Team oder die Unterhaltung geladen ist, können Benutzer einen Connector mithilfe des standardmäßigen Connectors-Katalogflusses einrichten:</span><span class="sxs-lookup"><span data-stu-id="94b86-157">With the app loaded in the team or conversation, users can set up a Connector using the standard Connectors gallery flow:</span></span>

1. <span data-ttu-id="94b86-158">Wechseln Sie zu einem Kanal im Team.</span><span class="sxs-lookup"><span data-stu-id="94b86-158">Go to a channel in the team.</span></span> <span data-ttu-id="94b86-159">Wählen **Sie Weitere Optionen** (*&#8943;*) aus, und wählen Sie **Connectors aus.**</span><span class="sxs-lookup"><span data-stu-id="94b86-159">Choose **More options** (*&#8943;*) and choose **Connectors**.</span></span>

2. <span data-ttu-id="94b86-160">Wählen Sie den Connector im **Abschnitt Sideloaded** unten aus.</span><span class="sxs-lookup"><span data-stu-id="94b86-160">Select your Connector from the **Sideloaded** section at the bottom.</span></span>

3. <span data-ttu-id="94b86-161">Konfigurieren Sie den Connector über die [Konfigurationsseite,](../../webhooks-and-connectors/how-to/connectors-creating.md) und wählen Sie **Speichern aus.**</span><span class="sxs-lookup"><span data-stu-id="94b86-161">Configure your connector through its [configuration page](../../webhooks-and-connectors/how-to/connectors-creating.md) and select **Save**.</span></span>

  ![Das Dialogfeld Registerkarte hinzufügen mit einem Katalog verfügbarer Registerkarten.](../../assets/images/connector_gallery.png)

## <a name="access-your-uploaded-messaging-extension"></a><span data-ttu-id="94b86-163">Zugreifen auf ihre hochgeladene Messagingerweiterung</span><span class="sxs-lookup"><span data-stu-id="94b86-163">Access your uploaded messaging extension</span></span>

<span data-ttu-id="94b86-164">Eine hochgeladene App mit einer Messagingerweiterung wird automatisch im Menü Weitere Optionen **(** *&#8943;*) im Verfassenfeld angezeigt.</span><span class="sxs-lookup"><span data-stu-id="94b86-164">An uploaded app with a messaging extension automatically appears in the **More options** (*&#8943;*) menu in the compose box.</span></span>

![Messaging-Erweiterungen](../../assets/images/compose-extensions/cesampleapp.png)

## <a name="add-a-default-install-scope-and-group-capability"></a><span data-ttu-id="94b86-166">Hinzufügen eines Standardinstallationsbereichs und einer Gruppenfunktion</span><span class="sxs-lookup"><span data-stu-id="94b86-166">Add a default install scope and group capability</span></span>

> [!NOTE]
> <span data-ttu-id="94b86-167">Der Standardinstallationsbereich und die Gruppenfunktion sind derzeit nur in der Entwicklervorschau verfügbar.</span><span class="sxs-lookup"><span data-stu-id="94b86-167">The default install scope and group capability is currently available in developer preview only.</span></span>

<span data-ttu-id="94b86-168">Obwohl das Installieren einer App im persönlichen Bereich für die meisten Apps funktioniert, unterstützen einige Apps im Teams Store sowohl persönliche als auch Teambereiche.</span><span class="sxs-lookup"><span data-stu-id="94b86-168">Although installing an app in the personal scope works for most apps, some of the apps in Teams Store support both personal and team scopes.</span></span>
<span data-ttu-id="94b86-169">Einige dieser Apps sind für die Arbeit in einem Team, in Besprechungen oder in einem Groupchat vorgesehen, bei dem die persönliche App-Erfahrung sekundär ist.</span><span class="sxs-lookup"><span data-stu-id="94b86-169">Some of these apps are intended to work in a team, meetings, or a groupchat, with personal app experience being secondary.</span></span>
<span data-ttu-id="94b86-170">Mit der Standardauswahl für den Installationsbereich können Sie die für die von Ihnen `defaultInstallScope` veröffentlichten Apps angeben.</span><span class="sxs-lookup"><span data-stu-id="94b86-170">The default install scope selection helps you to specify the `defaultInstallScope` for the apps that you publish.</span></span> <span data-ttu-id="94b86-171">Die App-Installationserfahrung stellt dem Benutzer die Standardoptionen zur Verfügung, während der Rest wie im Bild hervorgehoben unter das Chevron verschoben wird.</span><span class="sxs-lookup"><span data-stu-id="94b86-171">The app installation experience makes the default options available to the user, while the rest is moved under the chevron as highlighted in the image.</span></span>

![Eine App hinzufügen](../../assets/images/compose-extensions/addanapp.png)

<span data-ttu-id="94b86-173">Die `defaultInstallScope` Eigenschaft unterstützt Werte wie persönliche, Team-, Gruppenchat- oder Besprechungsgespräche.</span><span class="sxs-lookup"><span data-stu-id="94b86-173">The `defaultInstallScope` property supports values, such as personal, team, groupchat, or meetings.</span></span>

> [!NOTE]
><span data-ttu-id="94b86-174">`defaultGroupCapability` stellt die Standardfunktion zur Verfügung, die dem Team, dem Gruppenchat oder besprechungen hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="94b86-174">`defaultGroupCapability` provides the default capability that is added to the team, groupchat or meetings.</span></span> <span data-ttu-id="94b86-175">Wählen Sie eine Registerkarte, einen Bot oder einen Connector als Standardfunktion für Ihre App aus, Sie müssen jedoch sicherstellen, dass Sie die ausgewählte Funktion in Ihrer App-Definition bereitgestellt haben.</span><span class="sxs-lookup"><span data-stu-id="94b86-175">Choose a tab, bot, or connector as the default capability for your app, but you must ensure that you have provided the selected capability in your app definition.</span></span>

## <a name="remove-or-update-your-app"></a><span data-ttu-id="94b86-176">Entfernen oder Aktualisieren Ihrer App</span><span class="sxs-lookup"><span data-stu-id="94b86-176">Remove or update your app</span></span>

<span data-ttu-id="94b86-177">Um Ihre App zu entfernen, wählen Sie das Löschsymbol neben dem App-Namen in der **Liste Teams-Bots** anzeigen aus.</span><span class="sxs-lookup"><span data-stu-id="94b86-177">To remove your app, select the delete icon next to the app name in the **View Teams** bots list.</span></span> <span data-ttu-id="94b86-178">Wenn Sie Manifestinformationen ändern, entfernen Sie zuerst die App, und fügen Sie dann das aktualisierte Paket hinzu. Weitere Informationen finden Sie unter [Load your package into a team](#load-your-package-into-teams).</span><span class="sxs-lookup"><span data-stu-id="94b86-178">If you change manifest information, first remove the app and then add the updated package, see [Load your package into a team](#load-your-package-into-teams).</span></span> <span data-ttu-id="94b86-179">Codeänderungen an Ihrem Dienst erfordern nicht, dass Sie Ihr Manifest erneut hochladen.</span><span class="sxs-lookup"><span data-stu-id="94b86-179">Code changes on your service do not require you to upload your manifest again.</span></span> <span data-ttu-id="94b86-180">Wenn die Codeänderungen jedoch Manifestupdates erfordern, z. B. Änderungen an der URL oder der Microsoft-App-ID für den Bot, müssen Sie das Manifest erneut hochladen.</span><span class="sxs-lookup"><span data-stu-id="94b86-180">However, if the code changes require manifest updates, such as changes to the URL or the Microsoft app ID for its bot, you must upload the manifest again.</span></span>

> [!NOTE]
> <span data-ttu-id="94b86-181">Sie können einen Bot nicht vollständig aus einem persönlichen Kontext entfernen.</span><span class="sxs-lookup"><span data-stu-id="94b86-181">You cannot remove a bot from a personal context entirely.</span></span> <span data-ttu-id="94b86-182">Wenn der Bot entfernt und erneut hinzugefügt wird, wird der vorherigen Unterhaltung zusätzliche Kommunikation mit dem Bot hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="94b86-182">If the bot is removed and added again, additional communication with the bot appends to the previous conversation.</span></span>

## <a name="troubleshooting-notes"></a><span data-ttu-id="94b86-183">Hinweise zur Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="94b86-183">Troubleshooting notes</span></span>

<span data-ttu-id="94b86-184">Wenn das Manifest nicht geladen werden kann, überprüfen Sie, ob Sie alle Anweisungen in [Erstellen](../../concepts/build-and-test/apps-package.md) des Pakets befolgt und Ihr Manifest anhand des Schemas [überprüft haben.](../../resources/schema/manifest-schema.md)</span><span class="sxs-lookup"><span data-stu-id="94b86-184">If the manifest fails to load, check if you have followed all the instructions in [Create the package](../../concepts/build-and-test/apps-package.md) and validated your manifest against the [schema](../../resources/schema/manifest-schema.md).</span></span>
