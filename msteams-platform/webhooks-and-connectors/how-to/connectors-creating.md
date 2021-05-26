---
title: Office 365-Connectors
description: Beschreibt, wie Sie mit Office 365 Connectors in Microsoft Teams
keywords: Teams O365-Connector
localization_priority: Normal
ms.topic: conceptual
ms.date: 04/19/2019
ms.openlocfilehash: 1598b84fc1c36547aa4c814cdf03404a3833779e
ms.sourcegitcommit: c55b0d2a4c1f8945e49b0b7c0b08c0eb3da3d2be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2021
ms.locfileid: "52646323"
---
# <a name="creating-office-365-connectors-for-microsoft-teams"></a><span data-ttu-id="deb19-104">Erstellen Office 365 Connectors für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="deb19-104">Creating Office 365 Connectors for Microsoft Teams</span></span>

<span data-ttu-id="deb19-105">Mit Microsoft Teams apps können Sie Ihren vorhandenen Office 365 Connector hinzufügen oder einen neuen erstellen, der in das Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="deb19-105">With Microsoft Teams apps, you can add your existing Office 365 Connector or build a new one to include in Microsoft Teams.</span></span> <span data-ttu-id="deb19-106">Weitere [Informationen finden Sie unter Build your own Connector.](/outlook/actionable-messages/connectors-dev-dashboard#build-your-own-connector)</span><span class="sxs-lookup"><span data-stu-id="deb19-106">See [Build your own Connector](/outlook/actionable-messages/connectors-dev-dashboard#build-your-own-connector) for more information.</span></span>

## <a name="adding-a-connector-to-your-teams-app"></a><span data-ttu-id="deb19-107">Hinzufügen eines Connectors zu Ihrer Teams App</span><span class="sxs-lookup"><span data-stu-id="deb19-107">Adding a Connector to your Teams App</span></span>

<span data-ttu-id="deb19-108">Sie können Ihren registrierten Connector als Teil Ihres Teams-App-Pakets verteilen.</span><span class="sxs-lookup"><span data-stu-id="deb19-108">You can distribute your registered Connector as part of your Teams app package.</span></span> <span data-ttu-id="deb19-109">Ob als eigenständige Lösung oder als eine von mehreren Funktionen, [](~/concepts/build-and-test/apps-package.md) die [](~/concepts/deploy-and-publish/apps-publish.md) Ihre Erfahrung in Teams ermöglicht: Sie können Ihren Connector als Teil Ihrer AppSource-Übermittlung packen und veröffentlichen, oder Sie können ihn Benutzern direkt zum Hochladen innerhalb von Teams. [](~/concepts/extensibility-points.md)</span><span class="sxs-lookup"><span data-stu-id="deb19-109">Whether as a standalone solution, or one of several [capabilities](~/concepts/extensibility-points.md) that your experience enables in Teams, you can [package](~/concepts/build-and-test/apps-package.md) and [publish](~/concepts/deploy-and-publish/apps-publish.md) your Connector as part of your AppSource submission, or you can provide it to users directly for uploading within Teams.</span></span>

<span data-ttu-id="deb19-110">Zum Verteilen ihres Connectors müssen Sie sich über das [Connectors Developer Dashboard registrieren.](https://outlook.office.com/connectors/home/login/#/publish)</span><span class="sxs-lookup"><span data-stu-id="deb19-110">To distribute your Connector, you need to register by using the [Connectors Developer Dashboard](https://outlook.office.com/connectors/home/login/#/publish).</span></span> <span data-ttu-id="deb19-111">Sobald ein Connector registriert ist, wird standardmäßig davon ausgegangen, dass Ihr Connector in allen Office 365-Produkten funktioniert, die sie unterstützen, einschließlich Outlook und Teams.</span><span class="sxs-lookup"><span data-stu-id="deb19-111">By default, once a Connector is registered, it's assumed that your Connector will work in all Office 365 products that support them, including Outlook and Teams.</span></span> <span data-ttu-id="deb19-112">Wenn dies _nicht_ der Fall ist und Sie einen Connector erstellen müssen, der nur in Microsoft Teams funktioniert, kontaktieren Sie uns direkt unter [Microsoft Teams App Submissions](mailto:teamsubm@microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="deb19-112">If that is _not_ the case and you need to create a Connector that only works in Microsoft Teams, contact us directly at [Microsoft Teams App Submissions](mailto:teamsubm@microsoft.com).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="deb19-113">Nachdem Sie **im Connectors** Developer Dashboard speichern auswählen, wird Ihr Connector registriert.</span><span class="sxs-lookup"><span data-stu-id="deb19-113">After you choose **Save** in the Connectors Developer Dashboard, your Connector is registered.</span></span> <span data-ttu-id="deb19-114">Wenn Sie Ihren Connector in AppSource veröffentlichen möchten, befolgen Sie die Anweisungen unter [Publish your Microsoft Teams app to AppSource](~/concepts/deploy-and-publish/apps-publish.md).</span><span class="sxs-lookup"><span data-stu-id="deb19-114">If you want to publish your Connector in AppSource, follow the instructions in [Publish your Microsoft Teams app to AppSource](~/concepts/deploy-and-publish/apps-publish.md).</span></span> <span data-ttu-id="deb19-115">Wenn Sie Ihre App nicht in AppSource veröffentlichen und stattdessen einfach nur direkt an Ihre Organisation verteilen möchten, können Sie dies tun, indem Sie sie in [Ihrer Organisation veröffentlichen.](#publish-connectors-for-your-organization)</span><span class="sxs-lookup"><span data-stu-id="deb19-115">If you do not wish to publish your app in AppSource, and rather simply distribute it directly to your organization only, you can do so by [publishing to your organization](#publish-connectors-for-your-organization).</span></span> <span data-ttu-id="deb19-116">Wenn Sie nur in Ihrer Organisation veröffentlichen möchten, sind keine weiteren Aktionen im Connectordashboard erforderlich.</span><span class="sxs-lookup"><span data-stu-id="deb19-116">If you only want to publish to your organization, no further action is necessary on the Connector dashboard.</span></span>

### <a name="integrating-the-configuration-experience"></a><span data-ttu-id="deb19-117">Integrieren der Konfigurationserfahrung</span><span class="sxs-lookup"><span data-stu-id="deb19-117">Integrating the configuration experience</span></span>

<span data-ttu-id="deb19-118">Ihre Benutzer führen die gesamte Connectorkonfiguration aus, ohne den Client Teams verlassen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="deb19-118">Your users will complete the entire Connector configuration experience without having to leave the Teams client.</span></span> <span data-ttu-id="deb19-119">Um diese Erfahrung zu erzielen, Teams Die Konfigurationsseite direkt in einen iframe einbetten.</span><span class="sxs-lookup"><span data-stu-id="deb19-119">To achieve this experience, Teams will embed your configuration page directly within an iframe.</span></span> <span data-ttu-id="deb19-120">Die Reihenfolge der Vorgänge lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="deb19-120">The sequence of operations is as follows:</span></span>

1. <span data-ttu-id="deb19-121">Der Benutzer klickt auf den Connector, um mit dem Konfigurationsprozess zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="deb19-121">The user clicks on your connector to begin the configuration process.</span></span>
2. <span data-ttu-id="deb19-122">Teams wird Ihre Konfigurationserfahrung in der Zeile geladen.</span><span class="sxs-lookup"><span data-stu-id="deb19-122">Teams will load your configuration experience in line.</span></span>
3. <span data-ttu-id="deb19-123">Der Benutzer interagiert mit Ihrer Weberfahrung, um die Konfiguration zu vervollständigen.</span><span class="sxs-lookup"><span data-stu-id="deb19-123">The user interacts with your web experience to complete the configuration.</span></span>
4. <span data-ttu-id="deb19-124">Der Benutzer drückt auf "Speichern", wodurch ein Rückruf in Ihrem Code ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="deb19-124">The user presses "Save", which triggers a callback in your code.</span></span>
5. <span data-ttu-id="deb19-125">Ihr Code wird das Speicherereignis verarbeiten, indem die Webhookeinstellungen abgerufen werden (siehe unten).</span><span class="sxs-lookup"><span data-stu-id="deb19-125">Your code will process the save event by retrieving the webhook settings (documented below).</span></span> <span data-ttu-id="deb19-126">Ihr Code sollte dann den Webhook speichern, um Ereignisse später zu veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="deb19-126">Your code should then store the webhook to post events later.</span></span>

<span data-ttu-id="deb19-127">Sie können Ihre vorhandene Webkonfigurationserfahrung wiederverwenden oder eine separate Version erstellen, die speziell in diesem Teams.</span><span class="sxs-lookup"><span data-stu-id="deb19-127">You can reuse your existing web configuration experience or create a separate version to be hosted specifically in Teams.</span></span> <span data-ttu-id="deb19-128">Ihr Code sollte:</span><span class="sxs-lookup"><span data-stu-id="deb19-128">Your code should:</span></span>

1. <span data-ttu-id="deb19-129">Schließen Sie das Microsoft Teams JavaScript SDK ein.</span><span class="sxs-lookup"><span data-stu-id="deb19-129">Include the Microsoft Teams JavaScript SDK.</span></span> <span data-ttu-id="deb19-130">Dadurch erhalten Sie Zugriff auf APIs, um allgemeine Vorgänge wie das Abrufen des aktuellen Benutzer-/Kanal-/Teamkontexts und das Initiieren von Authentifizierungsflüssen durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="deb19-130">This gives your code access to APIs to perform common operations like getting the current user/channel/team context and initiating authentication flows.</span></span> <span data-ttu-id="deb19-131">Initialisieren Sie das SDK durch Aufrufen von `microsoftTeams.initialize()`.</span><span class="sxs-lookup"><span data-stu-id="deb19-131">Initialize the SDK by calling `microsoftTeams.initialize()`.</span></span>
2. <span data-ttu-id="deb19-132">Rufen `microsoftTeams.settings.setValidityState(true)` Sie auf, wenn Sie die Schaltfläche Speichern aktivieren möchten.</span><span class="sxs-lookup"><span data-stu-id="deb19-132">Call `microsoftTeams.settings.setValidityState(true)` when you want to enable the Save button.</span></span> <span data-ttu-id="deb19-133">Sie sollten dies als Antwort auf gültige Benutzereingaben, z. B. eine Auswahl oder Feldaktualisierung, tun.</span><span class="sxs-lookup"><span data-stu-id="deb19-133">You should do this as a response to valid user input, such as a selection or field update.</span></span>
3. <span data-ttu-id="deb19-134">Registrieren Sie `microsoftTeams.settings.registerOnSaveHandler()` einen Ereignishandler, der aufgerufen wird, wenn der Benutzer auf Speichern klickt.</span><span class="sxs-lookup"><span data-stu-id="deb19-134">Register a `microsoftTeams.settings.registerOnSaveHandler()` event handler, which gets called when the user clicks Save.</span></span>
4. <span data-ttu-id="deb19-135">Rufen `microsoftTeams.settings.setSettings()` Sie zum Speichern der Connectoreinstellungen auf.</span><span class="sxs-lookup"><span data-stu-id="deb19-135">Call `microsoftTeams.settings.setSettings()` to save the connector settings.</span></span> <span data-ttu-id="deb19-136">Was hier gespeichert wird, ist auch das, was im Konfigurationsdialogfeld angezeigt wird, wenn der Benutzer versucht, eine vorhandene Konfiguration für Ihren Connector zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="deb19-136">What's saved here is also what will be shown in the configuration dialog if the user tries to update an existing configuration for your connector.</span></span>
5. <span data-ttu-id="deb19-137">Aufruf `microsoftTeams.settings.getSettings()` zum Abrufen von Webhookeigenschaften, einschließlich der URL selbst.</span><span class="sxs-lookup"><span data-stu-id="deb19-137">Call `microsoftTeams.settings.getSettings()` to fetch webhook properties, including the URL itself.</span></span> <span data-ttu-id="deb19-138">Sie sollten dies auch während des Save-Ereignisses aufrufen, wenn Ihre Seite im Falle einer Neukonfiguration zum ersten Mal geladen wird.</span><span class="sxs-lookup"><span data-stu-id="deb19-138">You should call this  In addition to during the save event, you should also call this when your page is first loaded in the case of a re-configuration.</span></span>
6. <span data-ttu-id="deb19-139">(Optional) Registrieren Sie `microsoftTeams.settings.registerOnRemoveHandler()` einen Ereignishandler, der aufgerufen wird, wenn der Benutzer den Connector entfernt.</span><span class="sxs-lookup"><span data-stu-id="deb19-139">(Optional) Register a `microsoftTeams.settings.registerOnRemoveHandler()` event handler, which gets called when the user removes your connector.</span></span> <span data-ttu-id="deb19-140">Dieses Ereignis bietet Ihrem Dienst die Möglichkeit, bereinigende Aktionen durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="deb19-140">This event gives your service an opportunity to perform any cleanup actions.</span></span>

<span data-ttu-id="deb19-141">Hier ist ein Beispiel-HTML zum Erstellen einer Connectorkonfigurationsseite ohne CSS:</span><span class="sxs-lookup"><span data-stu-id="deb19-141">Here's a sample HTML to create a Connector configuration page without the CSS:</span></span>

```html
<h2>Send notifications when tasks are:</h2>
<div class="col-md-8">
    <section id="configSection">
        <form id="configForm">
            <input type="radio" name="notificationType" value="Create" onclick="onClick()"> Created
            <br>
            <br>
            <input type="radio" name="notificationType" value="Update" onclick="onClick()"> Updated
        </form>
    </section>
</div>

<script src="https://statics.teams.microsoft.com/sdk/v1.5.2/js/MicrosoftTeams.min.js" crossorigin="anonymous"></script>
<script src="/Scripts/jquery-1.10.2.js"></script>

<script type="text/javascript">

        function onClick() {
            microsoftTeams.settings.setValidityState(true);
        }

        microsoftTeams.initialize();
        microsoftTeams.settings.registerOnSaveHandler(function (saveEvent) {
            var radios = document.getElementsByName('notificationType');

            var eventType = '';
            if (radios[0].checked) {
                eventType = radios[0].value;
            } else {
                eventType = radios[1].value;
            }

            microsoftTeams.settings.setSettings({
                 entityId: eventType,
                contentUrl: "https://YourSite/Connector/Setup",
                removeUrl:"https://YourSite/Connector/Setup",
                 configName: eventType
                });

            microsoftTeams.settings.getSettings(function (settings) {
                // We get the Webhook URL in settings.webhookUrl which needs to be saved. 
                // This can be used later to send notification.
            });

            saveEvent.notifySuccess();
        });

        microsoftTeams.settings.registerOnRemoveHandler(function (removeEvent) {
            alert("Removed" + JSON.stringify(removeEvent));
        });

</script>
```

#### <a name="getsettings-response-properties"></a><span data-ttu-id="deb19-142">`GetSettings()` Antworteigenschaften</span><span class="sxs-lookup"><span data-stu-id="deb19-142">`GetSettings()` response properties</span></span>

>[!Note]
><span data-ttu-id="deb19-143">Die vom Aufruf hier zurückgegebenen Parameter unterscheiden sich von denen, wenn Sie diese Methode über eine Registerkarte aufrufen würden, und unterscheiden sich von denen, die `getSettings` hier [dokumentiert sind.](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="deb19-143">The parameters returned by the `getSettings` call here are different than if you were to invoke this method from a tab, and differ from those documented [here](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true).</span></span>

| <span data-ttu-id="deb19-144">Parameter</span><span class="sxs-lookup"><span data-stu-id="deb19-144">Parameter</span></span>   | <span data-ttu-id="deb19-145">Details</span><span class="sxs-lookup"><span data-stu-id="deb19-145">Details</span></span> |
|-------------|---------|
| `entityId`       | <span data-ttu-id="deb19-146">Die Entitäts-ID, die vom Code beim Aufruf festgelegt `setSettings()` wird.</span><span class="sxs-lookup"><span data-stu-id="deb19-146">The entity ID, as set by your code when calling `setSettings()`.</span></span> |
| `configName`  | <span data-ttu-id="deb19-147">Der Konfigurationsname, der vom Code beim Aufrufen festgelegt `setSettings()` wird.</span><span class="sxs-lookup"><span data-stu-id="deb19-147">The configuration name, as set by your code when calling `setSettings()`.</span></span> |
| `contentUrl` | <span data-ttu-id="deb19-148">Die URL der Konfigurationsseite, die vom Code beim Aufrufen festgelegt `setSettings()` wird.</span><span class="sxs-lookup"><span data-stu-id="deb19-148">The URL of the configuration page, as set by your code when calling `setSettings()`.</span></span> |
| `webhookUrl` | <span data-ttu-id="deb19-149">Die webhook-URL, die für diesen Connector erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="deb19-149">The webhook URL created for this connector.</span></span> <span data-ttu-id="deb19-150">Persist the webhook URL and use it to POST structured JSON to send cards to the channel.</span><span class="sxs-lookup"><span data-stu-id="deb19-150">Persist the webhook URL and use it to POST structured JSON to send cards to the channel.</span></span> <span data-ttu-id="deb19-151">`webhookUrl` wird nur zurückgegeben, wenn Anwendung erfolgreich zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="deb19-151">The `webhookUrl` is returned only when application returns successfully.</span></span> |
| `appType` | <span data-ttu-id="deb19-152">Die zurückgegebenen Werte werden können `mail`, `groups` bzw. `teams` entsprechend Office 365-Mail, Office 365-Gruppen oder Microsoft Teams sein.</span><span class="sxs-lookup"><span data-stu-id="deb19-152">The values returned can be `mail`, `groups` or `teams` corresponding to the Office 365 Mail, Office 365 Groups or Microsoft Teams respectively.</span></span> |
| `userObjectId` | <span data-ttu-id="deb19-153">Dies ist die eindeutige ID, die dem Office 365 entspricht, der das Setup des Connectors initiiert hat.</span><span class="sxs-lookup"><span data-stu-id="deb19-153">This is the unique id corresponding to the Office 365 user who initiated setup of the connector.</span></span> <span data-ttu-id="deb19-154">Sie sollte gesichert werden.</span><span class="sxs-lookup"><span data-stu-id="deb19-154">It should be secured.</span></span> <span data-ttu-id="deb19-155">Dieser Wert kann verwendet werden, um den Benutzer in Office 365 zuzuweisen, der die Konfiguration für den Benutzer in Ihrem Dienst eingerichtet hat.</span><span class="sxs-lookup"><span data-stu-id="deb19-155">This value can be used to associate the user in Office 365 who set up the configuration to the user in your service.</span></span> |

<span data-ttu-id="deb19-156">Wenn Sie den Benutzer im Rahmen des Ladens Ihrer Seite [](~/tabs/how-to/authentication/auth-flow-tab.md) in Schritt 2 oben authentifizieren müssen, finden Sie unter diesem Link Weitere Informationen dazu, wie Sie die Anmeldung integrieren können, wenn Ihre Seite eingebettet ist.</span><span class="sxs-lookup"><span data-stu-id="deb19-156">If you need to authenticate the user as part of loading your page in step 2 above, refer to [this link](~/tabs/how-to/authentication/auth-flow-tab.md) for details on how you can integrate login when your page is embedded.</span></span>

> [!NOTE]
> <span data-ttu-id="deb19-157">Aus clientübergreifenden Kompatibilitätsgründen muss Ihr Code vor dem Aufrufen die URL und `microsoftTeams.authentication.registerAuthenticationHandlers()` die Methoden zum Erfolgreich-/Fehlerrückruf `authenticate()` aufrufen.</span><span class="sxs-lookup"><span data-stu-id="deb19-157">Due to cross-client compatibility reasons, your code will need to call `microsoftTeams.authentication.registerAuthenticationHandlers()` with the URL and success/failure callback methods before calling `authenticate()`.</span></span>

#### <a name="handling-edits"></a><span data-ttu-id="deb19-158">Behandeln von Bearbeitungen</span><span class="sxs-lookup"><span data-stu-id="deb19-158">Handling edits</span></span>

<span data-ttu-id="deb19-159">Der Code sollte wiederkehrenden Benutzern ermöglichen, eine vorhandene Connector-Konfiguration zu bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="deb19-159">Your code should handle users returning to edit an existing connector configuration.</span></span> <span data-ttu-id="deb19-160">Rufen Sie dazu während `microsoftTeams.settings.setSettings()` der Erstkonfiguration mit den folgenden Parametern auf:</span><span class="sxs-lookup"><span data-stu-id="deb19-160">To do this, call `microsoftTeams.settings.setSettings()` during the initial configuration with the following parameters:</span></span>

- <span data-ttu-id="deb19-161">`entityId` ist die benutzerdefinierte ID, die von Ihrem Dienst verstanden wird und das darstellt, was der Benutzer konfiguriert hat.</span><span class="sxs-lookup"><span data-stu-id="deb19-161">`entityId` is the custom ID that is understood by your service and represents what the user has configured.</span></span>
- <span data-ttu-id="deb19-162">`configName` ist ein Anzeigename, den Der Konfigurationscode abrufen kann</span><span class="sxs-lookup"><span data-stu-id="deb19-162">`configName` is a friendly name that your configuration code can retrieve</span></span>
- <span data-ttu-id="deb19-163">`contentUrl` ist eine benutzerdefinierte URL, die geladen wird, wenn ein Benutzer eine vorhandene Connectorkonfiguration bearbeitet.</span><span class="sxs-lookup"><span data-stu-id="deb19-163">`contentUrl` is a custom URL that gets loaded when a user edits an existing connector configuration.</span></span> <span data-ttu-id="deb19-164">Sie können diese URL verwenden, um es Ihrem Code zu erleichtern, den Bearbeitungsfall zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="deb19-164">You can use this URL to make it easier for your code to handle the edit case.</span></span>

<span data-ttu-id="deb19-165">In der Regel wird dieser Aufruf als Teil des Speicherereignishandlers vorgenommen.</span><span class="sxs-lookup"><span data-stu-id="deb19-165">Typically, this call is made as part of your save event handler.</span></span> <span data-ttu-id="deb19-166">Wenn das oben beschriebene Element geladen wird, sollte ihr Code dann aufrufen, um alle Einstellungen oder Formulare in der Konfigurationsbenutzeroberfläche `contentUrl` `getSettings()` vorab aufgefüllt zu haben.</span><span class="sxs-lookup"><span data-stu-id="deb19-166">Then, when the `contentUrl` above is loaded, your code should call `getSettings()` to prepopulate any settings or forms in your configuration UI.</span></span>

#### <a name="handling-removals"></a><span data-ttu-id="deb19-167">Behandeln von Entfernungen</span><span class="sxs-lookup"><span data-stu-id="deb19-167">Handling removals</span></span>

<span data-ttu-id="deb19-168">Sie können optional einen Ereignishandler ausführen, wenn der Benutzer eine vorhandene Connectorkonfiguration entfernt.</span><span class="sxs-lookup"><span data-stu-id="deb19-168">You can optionally execute an event handler when the user removes an existing connector configuration.</span></span> <span data-ttu-id="deb19-169">Sie registrieren diesen Handler durch Aufrufen `microsoftTeams.settings.registerOnRemoveHandler()` von .</span><span class="sxs-lookup"><span data-stu-id="deb19-169">You register this handler by calling `microsoftTeams.settings.registerOnRemoveHandler()`.</span></span> <span data-ttu-id="deb19-170">Dieser Handler kann zum Ausführen von Bereinigungsvorgängen verwendet werden, z. B. zum Entfernen von Einträgen aus einer Datenbank.</span><span class="sxs-lookup"><span data-stu-id="deb19-170">This handler can be used to perform cleanup operations such as removing entries from a database.</span></span>

### <a name="including-the-connector-in-your-manifest"></a><span data-ttu-id="deb19-171">Einschließlich des Connectors in Ihr Manifest</span><span class="sxs-lookup"><span data-stu-id="deb19-171">Including the Connector in your Manifest</span></span>

<span data-ttu-id="deb19-172">Sie können das automatisch generierte Teams-App-Manifest aus dem Portal herunterladen.</span><span class="sxs-lookup"><span data-stu-id="deb19-172">You can download the auto-generated Teams app manifest from the portal.</span></span> <span data-ttu-id="deb19-173">Bevor Sie sie jedoch zum Testen oder Veröffentlichen Ihrer App verwenden können, müssen Sie folgendes tun:</span><span class="sxs-lookup"><span data-stu-id="deb19-173">Before you can use it to test or publish your app, though, you must do the following:</span></span>

- <span data-ttu-id="deb19-174">[Zwei Symbole einschließen](../../concepts/build-and-test/apps-package.md#app-icons).</span><span class="sxs-lookup"><span data-stu-id="deb19-174">[Include two icons](../../concepts/build-and-test/apps-package.md#app-icons).</span></span>
- <span data-ttu-id="deb19-175">Ändern Sie den `icons`-Teil des Manifests so, dass er auf die Dateinamen der Symbole anstelle von URLs verweist.</span><span class="sxs-lookup"><span data-stu-id="deb19-175">Modify the `icons` portion of the manifest to refer to the file names of the icons instead of URLs.</span></span>

<span data-ttu-id="deb19-176">Die folgende manifest.JSON-Datei enthält die grundlegenden Elemente, die zum Testen und Übermitteln Ihrer APP erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="deb19-176">The following manifest.json file contains the basic elements needed to test and submit your app.</span></span>

> [!NOTE]
> <span data-ttu-id="deb19-177">Ersetzen Sie im folgenden Beispiel `id` und `connectorId` mit der GUID des Connectors.</span><span class="sxs-lookup"><span data-stu-id="deb19-177">Replace `id` and `connectorId` in the following example with the GUID of your Connector.</span></span>

#### <a name="example-manifestjson-with-connector"></a><span data-ttu-id="deb19-178">Beispiel-manifest.JSON mit Connector</span><span class="sxs-lookup"><span data-stu-id="deb19-178">Example manifest.json with Connector</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",
  "manifestVersion": "1.5",
  "id": "e9343a03-0a5e-4c1f-95a8-263a565505a5",
  "version": "1.0",
  "packageName": "com.sampleapp",
  "developer": {
    "name": "Publisher",
    "websiteUrl": "https://www.microsoft.com",
    "privacyUrl": "https://www.microsoft.com",
    "termsOfUseUrl": "https://www.microsoft.com"
  },
  "description": {
    "full": "This is a sample manifest for an app with a connector with an inline configuration experience.",
    "short": "This is a sample manifest for an app with a connector."
  },
  "icons": {
    "outline": "sampleapp-outline.png",
    "color": "sampleapp-color.png"
  },
  "connectors": [
    {
      "connectorId": "e9343a03-0a5e-4c1f-95a8-263a565505a5",
      "configurationUrl": "https://teamstodoappconnectorwithinlineconfig.azurewebsites.net/Connector/Setup",
      "scopes": [
        "team"
      ]
    }
  ],
  "name": {
    "short": "Sample App",
    "full": "Sample App Long Name"
  },
  "accentColor": "#FFFFFF"
}
```

## <a name="disable-or-enable-connectors-in-teams"></a><span data-ttu-id="deb19-179">Deaktivieren oder Aktivieren von Connectors in Teams</span><span class="sxs-lookup"><span data-stu-id="deb19-179">Disable or enable connectors in Teams</span></span>

<span data-ttu-id="deb19-180">Das Exchange Online PowerShell V2-Modul verwendet moderne Authentifizierung und arbeitet mit mehrstufiger Authentifizierung (Multi-Factor Authentication, MFA) für die Verbindung mit allen Exchange-bezogenen PowerShell-Umgebungen in Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="deb19-180">The Exchange Online PowerShell V2 module uses modern authentication and works with multi-factor authentication (MFA) for connecting to all Exchange-related PowerShell environments in Microsoft 365.</span></span> <span data-ttu-id="deb19-181">Administratoren können Exchange Online PowerShell verwenden, um Connectors für einen gesamten Mandanten oder ein bestimmtes Gruppenpostfach zu deaktivieren, was alle Benutzer in diesem Mandanten oder Postfach betrifft.</span><span class="sxs-lookup"><span data-stu-id="deb19-181">Admins can use Exchange Online PowerShell to disable connectors for an entire tenant or a specific group mailbox, affecting all users in that tenant or mailbox.</span></span> <span data-ttu-id="deb19-182">Es ist nicht möglich, für einige und nicht für andere zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="deb19-182">It is not possible to disable for some and not others.</span></span> <span data-ttu-id="deb19-183">Außerdem sind Connectors standardmäßig für GCC deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="deb19-183">Also, connectors are disabled by default for GCC tenants.</span></span>

<span data-ttu-id="deb19-184">Die Einstellung auf Mandantenebene überschreibt die Einstellung auf Gruppenebene.</span><span class="sxs-lookup"><span data-stu-id="deb19-184">The tenant-level setting overrides the group-level setting.</span></span> <span data-ttu-id="deb19-185">Wenn ein Administrator beispielsweise Connectors für die Gruppe aktiviert und für den Mandanten deaktiviert, werden Connectors für die Gruppe deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="deb19-185">For example, if an admin enables connectors for the group and disables them on the tenant, connectors for the group will be disabled.</span></span> <span data-ttu-id="deb19-186">Um einen Connector in Teams zu aktivieren, stellen Sie eine Verbindung mit [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell?view=exchange-ps#connect-to-exchange-online-powershell-using-modern-authentication-with-or-without-mfa&preserve-view=true) mithilfe der modernen Authentifizierung mit oder ohne MFA sicher.</span><span class="sxs-lookup"><span data-stu-id="deb19-186">To enable a connector in Teams, [connect to Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell?view=exchange-ps#connect-to-exchange-online-powershell-using-modern-authentication-with-or-without-mfa&preserve-view=true) using modern authentication with or without MFA.</span></span>

### <a name="commands-to-disable-or-enable-connectors"></a><span data-ttu-id="deb19-187">Befehle zum Deaktivieren oder Aktivieren von Connectors</span><span class="sxs-lookup"><span data-stu-id="deb19-187">Commands to disable or enable connectors</span></span>

<span data-ttu-id="deb19-188">**Ausführen des Befehls in Exchange Online PowerShell**</span><span class="sxs-lookup"><span data-stu-id="deb19-188">**Run the command in Exchange Online PowerShell**</span></span>

* <span data-ttu-id="deb19-189">So deaktivieren Sie Connectors für den Mandanten: `Set-OrganizationConfig -ConnectorsEnabled:$false` .</span><span class="sxs-lookup"><span data-stu-id="deb19-189">To disable connectors for the tenant: `Set-OrganizationConfig -ConnectorsEnabled:$false`.</span></span>
* <span data-ttu-id="deb19-190">So deaktivieren Sie Nachrichten mit Aktionen für den Mandanten: `Set-OrganizationConfig -ConnectorsActionableMessagesEnabled:$false` .</span><span class="sxs-lookup"><span data-stu-id="deb19-190">To disable actionable messages for the tenant: `Set-OrganizationConfig -ConnectorsActionableMessagesEnabled:$false`.</span></span>
* <span data-ttu-id="deb19-191">Führen Sie die folgenden Befehle aus, um Connectors für Teams zu aktivieren:</span><span class="sxs-lookup"><span data-stu-id="deb19-191">To enable connectors for Teams, run the following commands:</span></span>
    * `Set-OrganizationConfig -ConnectorsEnabled:$true `
    * `Set-OrganizationConfig -ConnectorsEnabledForTeams:$true`
    * `Set-OrganizationConfig -ConnectorsActionableMessagesEnabled:$true`

<span data-ttu-id="deb19-192">Weitere Informationen zum Austausch von PowerShell-Modulen finden Sie unter [Set-OrganizationConfig](/powershell/module/exchange/Set-OrganizationConfig?view=exchange-ps&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="deb19-192">For more information on PowerShell module exchange, see [Set-OrganizationConfig](/powershell/module/exchange/Set-OrganizationConfig?view=exchange-ps&preserve-view=true).</span></span> <span data-ttu-id="deb19-193">Zum Aktivieren oder Deaktivieren Outlook Sie [Apps mit Ihren Gruppen in Outlook.](https://support.microsoft.com/topic/connect-apps-to-your-groups-in-outlook-ed0ce547-038f-4902-b9b3-9e518ae6fbab?ui=en-us&rs=en-us&ad=us)</span><span class="sxs-lookup"><span data-stu-id="deb19-193">To enable or disable Outlook connectors, [connect apps to your groups in Outlook](https://support.microsoft.com/topic/connect-apps-to-your-groups-in-outlook-ed0ce547-038f-4902-b9b3-9e518ae6fbab?ui=en-us&rs=en-us&ad=us).</span></span>

## <a name="testing-your-connector"></a><span data-ttu-id="deb19-194">Testen des Connectors</span><span class="sxs-lookup"><span data-stu-id="deb19-194">Testing your Connector</span></span>

<span data-ttu-id="deb19-195">Um den Connector zu testen, laden Sie ihn wie jede andere App in ein Team hoch.</span><span class="sxs-lookup"><span data-stu-id="deb19-195">To test your Connector, upload it to a team as you would with any other app.</span></span> <span data-ttu-id="deb19-196">Sie können ein ZIP-Paket erstellen und dafür die (wie im vorherigen Abschnitt beschrieben modifizierte) Manifestdatei aus dem Entwicklerdashboard für Connectors sowie die beiden Symboldateien verwenden.</span><span class="sxs-lookup"><span data-stu-id="deb19-196">You can create a .zip package using the manifest file from the Connectors Developer Dashboard (modified as directed in the preceding section) and the two icon files.</span></span>

<span data-ttu-id="deb19-197">Nachdem Sie die App hochgeladen haben, öffnen Sie die Liste der Connectors von einem beliebigen Kanal aus.</span><span class="sxs-lookup"><span data-stu-id="deb19-197">After you upload the app, open the Connectors list from any channel.</span></span> <span data-ttu-id="deb19-198">Scrollen Sie ganz nach unten bis zu Ihrer App im Abschnitt **Hochgeladenen**.</span><span class="sxs-lookup"><span data-stu-id="deb19-198">Scroll to the bottom to see your app in the **Uploaded** section.</span></span>

![Screenshot des Abschnitts "Hochgeladen" im Connector-Dialogfeld](~/assets/images/connectors/connector_dialog_uploaded.png)

<span data-ttu-id="deb19-200">Sie können nun die Konfigurationsfunktion starten.</span><span class="sxs-lookup"><span data-stu-id="deb19-200">You can now launch the configuration experience.</span></span> <span data-ttu-id="deb19-201">Beachten Sie, dass dieser Fluss vollständig innerhalb der Microsoft Teams als gehostete Erfahrung erfolgt.</span><span class="sxs-lookup"><span data-stu-id="deb19-201">Be aware that this flow occurs entirely within Microsoft Teams as a hosted experience.</span></span>

<span data-ttu-id="deb19-202">Um zu überprüfen, `HttpPOST` ob eine Aktion ordnungsgemäß funktioniert, senden Sie Nachrichten an Den [Connector](~/webhooks-and-connectors/how-to/connectors-using.md).</span><span class="sxs-lookup"><span data-stu-id="deb19-202">To verify that an `HttpPOST` action is working correctly, [send messages to your connector](~/webhooks-and-connectors/how-to/connectors-using.md).</span></span>

## <a name="publish-connectors-for-your-organization"></a><span data-ttu-id="deb19-203">Veröffentlichen von Connectors für Ihre Organisation</span><span class="sxs-lookup"><span data-stu-id="deb19-203">Publish Connectors for your organization</span></span>

<span data-ttu-id="deb19-204">Manchmal möchten Sie Ihre Connector-App möglicherweise nicht in der öffentlichen AppSource/Store sondern nur für die Benutzer in Ihrer Organisation verfügbar machen.</span><span class="sxs-lookup"><span data-stu-id="deb19-204">Sometimes, you may not want to publish your connector app to the public AppSource/Store but would like it to be available only to the users in your organization.</span></span> <span data-ttu-id="deb19-205">In solchen Fällen können Sie Ihre benutzerdefinierte Connector-App in [den App-Katalog Ihrer Organisation hochladen.](~/concepts/deploy-and-publish/apps-publish.md)</span><span class="sxs-lookup"><span data-stu-id="deb19-205">In such cases, you can upload your custom connector app to your [organization's App Catalog](~/concepts/deploy-and-publish/apps-publish.md).</span></span> <span data-ttu-id="deb19-206">Auf diese Weise ist Ihre Connector-App nur für diese Organisation verfügbar, und Sie müssen Den Connector nicht im öffentlichen Store veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="deb19-206">This way, your connector app will be available only to that organization, and you will not need to publish your connector to the public store.</span></span>

<span data-ttu-id="deb19-207">Nachdem Sie Ihr App-Paket hochgeladen haben, kann der Connector zum Konfigurieren und Verwenden des Connectors in einem Team aus dem App-Katalog der Organisation installiert werden, indem Sie die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="deb19-207">Once you've uploaded your app package, to configure and use the connector in a Team it can be installed from the organization's app catalog by following these steps:</span></span>

1. <span data-ttu-id="deb19-208">Wählen Sie das Apps-Symbol in der vertikalen Navigationsleiste ganz links aus.</span><span class="sxs-lookup"><span data-stu-id="deb19-208">Select the apps icon from the far left vertical navigation bar.</span></span>
1. <span data-ttu-id="deb19-209">Wählen Sie **im Fenster Apps** Connectors **aus.**</span><span class="sxs-lookup"><span data-stu-id="deb19-209">In the **Apps** window select **Connectors**.</span></span>
1. <span data-ttu-id="deb19-210">Wählen Sie den Connector aus, den Sie hinzufügen möchten, und ein Popupdialogfenster wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="deb19-210">Select the connector that you want to add and a pop-up dialog window will display.</span></span>
1. <span data-ttu-id="deb19-211">Wählen Sie **die Leiste Zu einer Teamleiste hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="deb19-211">Select the **Add to a team** bar.</span></span>
1. <span data-ttu-id="deb19-212">Geben Sie im nächsten Dialogfeld einen Team- oder Kanalnamen ein.</span><span class="sxs-lookup"><span data-stu-id="deb19-212">In the next dialog window type a team or channel name.</span></span>
1. <span data-ttu-id="deb19-213">Wählen Sie **in der unteren rechten** Ecke des Dialogfelds die Option Connectorleiste einrichten aus.</span><span class="sxs-lookup"><span data-stu-id="deb19-213">Select the **Set up a connector** bar from the bottom right corner of dialog window.</span></span>
1. <span data-ttu-id="deb19-214">Der Connector steht im Abschnitt &#9679;&#9679;&#9679; => Weitere *Optionen* Connectors Alle Connectors für Ihr Team  =>    =>    =>   für dieses Team zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="deb19-214">The connector will be available in the  section &#9679;&#9679;&#9679; => *More options* => *Connectors* => *All* => *Connectors for you team* for that team.</span></span> <span data-ttu-id="deb19-215">Sie können navigieren, indem Sie zu diesem Abschnitt scrollen oder nach der Connector-App suchen.</span><span class="sxs-lookup"><span data-stu-id="deb19-215">You can navigate by scrolling to this section or search for the connector app.</span></span>
1. <span data-ttu-id="deb19-216">Wählen Sie zum Konfigurieren oder Ändern des Connectors die **Leiste Konfigurieren** aus.</span><span class="sxs-lookup"><span data-stu-id="deb19-216">To configure or modify the connector select the **Configure** bar.</span></span>

## <a name="code-sample"></a><span data-ttu-id="deb19-217">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="deb19-217">Code sample</span></span>
|<span data-ttu-id="deb19-218">**Beispielname**</span><span class="sxs-lookup"><span data-stu-id="deb19-218">**Sample name**</span></span> | <span data-ttu-id="deb19-219">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="deb19-219">**Description**</span></span> | <span data-ttu-id="deb19-220">**.NET**</span><span class="sxs-lookup"><span data-stu-id="deb19-220">**.NET**</span></span> | <span data-ttu-id="deb19-221">**Node.js**</span><span class="sxs-lookup"><span data-stu-id="deb19-221">**Node.js**</span></span> |
|----------------|------------------|--------|----------------|
| <span data-ttu-id="deb19-222">Connectors</span><span class="sxs-lookup"><span data-stu-id="deb19-222">Connectors</span></span>    | <span data-ttu-id="deb19-223">Beispiel für Office 365 Connector, der Benachrichtigungen an den Teams-Kanal generiert.</span><span class="sxs-lookup"><span data-stu-id="deb19-223">Sample Office 365 Connector generating notifications to teams channel.</span></span>|   [<span data-ttu-id="deb19-224">View</span><span class="sxs-lookup"><span data-stu-id="deb19-224">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-todo-notification/csharp) | [<span data-ttu-id="deb19-225">View</span><span class="sxs-lookup"><span data-stu-id="deb19-225">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-github-notification/nodejs)|
| <span data-ttu-id="deb19-226">Beispiel für generische Connectors</span><span class="sxs-lookup"><span data-stu-id="deb19-226">Generic connectors sample</span></span> |<span data-ttu-id="deb19-227">Beispielcode für einen generischen Connector, der einfach für jedes System angepasst werden kann, das Webhooks unterstützt.</span><span class="sxs-lookup"><span data-stu-id="deb19-227">Sample code for a generic connector that's easy to customize for any system which supports webhooks.</span></span>|  | [<span data-ttu-id="deb19-228">View</span><span class="sxs-lookup"><span data-stu-id="deb19-228">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-generic/nodejs)|
