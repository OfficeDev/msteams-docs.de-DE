---
title: Erstellen von Office 365-Connectors
author: laujan
description: Beschreibt die ersten Schritte mit Office 365 Connectors in Microsoft Teams
keywords: Teams O365-Connector
localization_priority: Normal
ms.topic: conceptual
ms.date: 06/16/2021
ms.openlocfilehash: 28a2b35e868baf34e35a11a00e10b30b0f09c236
ms.sourcegitcommit: 85a52119df6c4cb4536572e6d2e7407f0e5e8a23
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2021
ms.locfileid: "53179755"
---
# <a name="create-office-365-connectors"></a><span data-ttu-id="06d18-104">Erstellen von Office 365-Connectors</span><span class="sxs-lookup"><span data-stu-id="06d18-104">Create Office 365 Connectors</span></span>

<span data-ttu-id="06d18-105">Mit Microsoft Teams Apps können Sie Ihren vorhandenen Office 365 Connector hinzufügen oder einen neuen connector in Teams erstellen.</span><span class="sxs-lookup"><span data-stu-id="06d18-105">With Microsoft Teams apps, you can add your existing Office 365 Connector or build a new one within Teams.</span></span> <span data-ttu-id="06d18-106">Weitere Informationen finden Sie unter [Erstellen Eines eigenen Connectors.](/outlook/actionable-messages/connectors-dev-dashboard#build-your-own-connector)</span><span class="sxs-lookup"><span data-stu-id="06d18-106">For more information, see [build your own connector](/outlook/actionable-messages/connectors-dev-dashboard#build-your-own-connector).</span></span>

## <a name="add-a-connector-to-teams-app"></a><span data-ttu-id="06d18-107">Hinzufügen eines Connectors zu Teams App</span><span class="sxs-lookup"><span data-stu-id="06d18-107">Add a connector to Teams app</span></span>

<span data-ttu-id="06d18-108">Sie können Ihren Connector im Rahmen Ihrer AppSource-Übermittlung [verpacken](~/concepts/build-and-test/apps-package.md) und [veröffentlichen.](~/concepts/deploy-and-publish/apps-publish.md)</span><span class="sxs-lookup"><span data-stu-id="06d18-108">You can [package](~/concepts/build-and-test/apps-package.md) and [publish](~/concepts/deploy-and-publish/apps-publish.md) your connector as part of your AppSource submission.</span></span> <span data-ttu-id="06d18-109">Sie können Ihren registrierten Connector als Teil Ihres Teams-App-Pakets verteilen.</span><span class="sxs-lookup"><span data-stu-id="06d18-109">You can distribute your registered connector as part of your Teams app package.</span></span> <span data-ttu-id="06d18-110">Informationen zu Einstiegspunkten für Teams App finden Sie unter ["Funktionen".](~/concepts/extensibility-points.md)</span><span class="sxs-lookup"><span data-stu-id="06d18-110">For information on entry points for Teams app, see [capabilities](~/concepts/extensibility-points.md).</span></span> <span data-ttu-id="06d18-111">Sie können das Paket benutzern auch direkt zum Hochladen in Teams bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="06d18-111">You can also provide the package to users directly for uploading within Teams.</span></span>

<span data-ttu-id="06d18-112">Um Den Connector zu verteilen, müssen Sie sich über [das Connectors Developer Dashboard](https://outlook.office.com/connectors/home/login/#/publish)registrieren.</span><span class="sxs-lookup"><span data-stu-id="06d18-112">To distribute your connector, you must register through [Connectors Developer Dashboard](https://outlook.office.com/connectors/home/login/#/publish).</span></span> <span data-ttu-id="06d18-113">Wenn ein Connector registriert ist, wird davon ausgegangen, dass er in allen Office 365 Produkten funktioniert, die Anwendungen unterstützen, einschließlich Outlook und Teams.</span><span class="sxs-lookup"><span data-stu-id="06d18-113">When a connector is registered, it is assumed that it works in all Office 365 products that support applications, including Outlook and Teams.</span></span> <span data-ttu-id="06d18-114">Wenn dies nicht der Fall ist und Sie einen Connector erstellen müssen, der nur in Microsoft Teams funktioniert, wenden Sie sich an: [Microsoft Teams E-Mail-Adresse für App-Übermittlungen.](mailto:teamsubm@microsoft.com)</span><span class="sxs-lookup"><span data-stu-id="06d18-114">If that is not the case and you must create a connector that only works in Microsoft Teams, contact: [Microsoft Teams App Submissions email](mailto:teamsubm@microsoft.com).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="06d18-115">Ihr Connector wird registriert, nachdem Sie im Connectors Developer Dashboard die Option **"Speichern"** ausgewählt haben.</span><span class="sxs-lookup"><span data-stu-id="06d18-115">Your connector is registered after you select **Save** in the Connectors Developer Dashboard.</span></span> <span data-ttu-id="06d18-116">Wenn Sie Ihren Connector in AppSource veröffentlichen möchten, folgen Sie den Anweisungen in der [Veröffentlichung Ihrer Microsoft Teams-App in AppSource.](~/concepts/deploy-and-publish/apps-publish.md)</span><span class="sxs-lookup"><span data-stu-id="06d18-116">If you want to publish your connector in AppSource, follow the instructions in [publish your Microsoft Teams app to AppSource](~/concepts/deploy-and-publish/apps-publish.md).</span></span> <span data-ttu-id="06d18-117">Wenn Sie Ihre App nicht in AppSource veröffentlichen möchten, verteilen Sie sie direkt an die Organisation.</span><span class="sxs-lookup"><span data-stu-id="06d18-117">If you do not want to publish your app in AppSource, distribute it directly to the organization.</span></span> <span data-ttu-id="06d18-118">Nach der [Veröffentlichung von Connectors für Ihre Organisation](#publish-connectors-for-the-organization)sind keine weiteren Aktionen im Connector-Dashboard erforderlich.</span><span class="sxs-lookup"><span data-stu-id="06d18-118">After [publishing connectors for your organization](#publish-connectors-for-the-organization), no further action is required on the Connector Dashboard.</span></span>

### <a name="integrate-the-configuration-experience"></a><span data-ttu-id="06d18-119">Integrieren der Konfigurationsumgebung</span><span class="sxs-lookup"><span data-stu-id="06d18-119">Integrate the configuration experience</span></span>

<span data-ttu-id="06d18-120">Benutzer können die gesamte Connectorkonfiguration abschließen, ohne den Teams-Client verlassen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="06d18-120">Users can complete the entire connector configuration experience without having to leave the Teams client.</span></span> <span data-ttu-id="06d18-121">Um die Erfahrung zu erhalten, können Teams Ihre Konfigurationsseite direkt in einen iframe einbetten.</span><span class="sxs-lookup"><span data-stu-id="06d18-121">To get the experience, Teams can embed your configuration page directly within an iframe.</span></span> <span data-ttu-id="06d18-122">Die Reihenfolge der Vorgänge lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="06d18-122">The sequence of operations is as follows:</span></span>

1. <span data-ttu-id="06d18-123">Der Benutzer wählt den Connector aus, um mit dem Konfigurationsprozess zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="06d18-123">The user selects the connector to begin the configuration process.</span></span>
1. <span data-ttu-id="06d18-124">Der Benutzer interagiert mit der Weboberfläche, um die Konfiguration abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="06d18-124">The user interacts with the web experience to complete the configuration.</span></span>
1. <span data-ttu-id="06d18-125">Der Benutzer wählt **Speichern** aus, wodurch ein Rückruf im Code ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="06d18-125">The user selects **Save**, which triggers a callback in code.</span></span>

    > [!NOTE]
    > * <span data-ttu-id="06d18-126">Der Code kann das Speicherereignis verarbeiten, indem die Webhook-Einstellungen abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="06d18-126">The code can process the save event by retrieving the webhook settings.</span></span> <span data-ttu-id="06d18-127">Ihr Code speichert den Webhook, um Ereignisse später zu posten.</span><span class="sxs-lookup"><span data-stu-id="06d18-127">Your code stores the webhook to post events later.</span></span>
    > * <span data-ttu-id="06d18-128">Die Konfigurationsoberfläche wird inline in Teams geladen.</span><span class="sxs-lookup"><span data-stu-id="06d18-128">The configuration experience is loaded inline within Teams.</span></span>

<span data-ttu-id="06d18-129">Sie können Ihre vorhandene Webkonfigurationsoberfläche wiederverwenden oder eine separate Version erstellen, die speziell in Teams gehostet werden soll.</span><span class="sxs-lookup"><span data-stu-id="06d18-129">You can reuse your existing web configuration experience or create a separate version to be hosted specifically in Teams.</span></span> <span data-ttu-id="06d18-130">Ihr Code muss das Microsoft Teams JavaScript SDK enthalten.</span><span class="sxs-lookup"><span data-stu-id="06d18-130">Your code must include the Microsoft Teams JavaScript SDK.</span></span> <span data-ttu-id="06d18-131">Dadurch erhält Ihr Code Zugriff auf APIs, um allgemeine Vorgänge auszuführen, z. B. den aktuellen Benutzer-, Kanal- oder Teamkontext abzurufen und Authentifizierungsflüsse zu initiieren.</span><span class="sxs-lookup"><span data-stu-id="06d18-131">This gives your code access to APIs to perform common operations, such as getting the current user, channel, or team context and initiate authentication flows.</span></span>

<span data-ttu-id="06d18-132">**So integrieren Sie die Konfigurationsumgebung**</span><span class="sxs-lookup"><span data-stu-id="06d18-132">**To integrate the configuration experience**</span></span>

1. <span data-ttu-id="06d18-133">Initialisieren Sie das SDK durch Aufrufen von `microsoftTeams.initialize()`.</span><span class="sxs-lookup"><span data-stu-id="06d18-133">Initialize the SDK by calling `microsoftTeams.initialize()`.</span></span>
1. <span data-ttu-id="06d18-134">Aufruf `microsoftTeams.settings.setValidityState(true)` zum Aktivieren von **Save**.</span><span class="sxs-lookup"><span data-stu-id="06d18-134">Call `microsoftTeams.settings.setValidityState(true)` to enable **Save**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="06d18-135">Sie müssen `microsoftTeams.settings.setValidityState(true)` als Antwort auf eine Aktualisierung der Benutzerauswahl oder des Felds aufrufen.</span><span class="sxs-lookup"><span data-stu-id="06d18-135">You must call `microsoftTeams.settings.setValidityState(true)` as a response to user selection or field update.</span></span>

1. <span data-ttu-id="06d18-136">Registrieren Sie  `microsoftTeams.settings.registerOnSaveHandler()` den Ereignishandler, der aufgerufen wird, wenn der Benutzer **"Speichern"** auswählt.</span><span class="sxs-lookup"><span data-stu-id="06d18-136">Register  `microsoftTeams.settings.registerOnSaveHandler()` event handler, which is called when the user selects **Save**.</span></span>
1. <span data-ttu-id="06d18-137">Aufruf `microsoftTeams.settings.setSettings()` zum Speichern der Connectoreinstellungen.</span><span class="sxs-lookup"><span data-stu-id="06d18-137">Call `microsoftTeams.settings.setSettings()` to save the connector settings.</span></span> <span data-ttu-id="06d18-138">Die gespeicherten Einstellungen werden auch im Konfigurationsdialogfeld angezeigt, wenn der Benutzer versucht, eine vorhandene Konfiguration für Ihren Connector zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="06d18-138">The saved settings are also shown in the configuration dialog if the user tries to update an existing configuration for your connector.</span></span>
1. <span data-ttu-id="06d18-139">Aufrufen zum Abrufen von `microsoftTeams.settings.getSettings()` Webhook-Eigenschaften, einschließlich der URL.</span><span class="sxs-lookup"><span data-stu-id="06d18-139">Call `microsoftTeams.settings.getSettings()` to fetch webhook properties, including the URL.</span></span>

    > [!NOTE]
    > <span data-ttu-id="06d18-140">Sie müssen bei `microsoftTeams.settings.getSettings()` der Neukonfiguration aufrufen, wann die Seite zum ersten Mal geladen wird.</span><span class="sxs-lookup"><span data-stu-id="06d18-140">You must call `microsoftTeams.settings.getSettings()` when your page is first loaded in case of reconfiguration.</span></span>

1. <span data-ttu-id="06d18-141">Registrieren Sie `microsoftTeams.settings.registerOnRemoveHandler()` den Ereignishandler, der aufgerufen wird, wenn der Benutzer den Connector entfernt.</span><span class="sxs-lookup"><span data-stu-id="06d18-141">Register `microsoftTeams.settings.registerOnRemoveHandler()` event handler, which is called when the user removes connector.</span></span>

<span data-ttu-id="06d18-142">Dieses Ereignis bietet Ihrem Dienst die Möglichkeit, alle Bereinigungsaktionen auszuführen.</span><span class="sxs-lookup"><span data-stu-id="06d18-142">This event gives your service an opportunity to perform any cleanup actions.</span></span>

<span data-ttu-id="06d18-143">Der folgende Code enthält ein HTML-Beispiel zum Erstellen einer Connectorkonfigurationsseite ohne den Kundendienst und Support:</span><span class="sxs-lookup"><span data-stu-id="06d18-143">The following code provides a sample HTML to create a connector configuration page without the customer service and support:</span></span>

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

<span data-ttu-id="06d18-144">Informationen zum Authentifizieren des Benutzers als Teil des Ladens ihrer Seite finden Sie im [Authentifizierungsfluss für Registerkarten,](~/tabs/how-to/authentication/auth-flow-tab.md) um die Anmeldung zu integrieren, wenn Ihre Seite eingebettet ist.</span><span class="sxs-lookup"><span data-stu-id="06d18-144">To authenticate the user as part of loading your page, see [authentication flow for tabs](~/tabs/how-to/authentication/auth-flow-tab.md) to integrate sign in when your page is embedded.</span></span>

> [!NOTE]
> <span data-ttu-id="06d18-145">Aus Gründen der clientübergreifenden Kompatibilität muss Ihr Code `microsoftTeams.authentication.registerAuthenticationHandlers()` vor dem Aufrufen mit der URL und den Rückrufmethoden für Erfolg oder Fehler `authenticate()` aufrufen.</span><span class="sxs-lookup"><span data-stu-id="06d18-145">Due to cross client compatibility reasons, your code must call `microsoftTeams.authentication.registerAuthenticationHandlers()` with the URL and success or failure callback methods before calling `authenticate()`.</span></span>

#### <a name="getsettings-response-properties"></a><span data-ttu-id="06d18-146">`GetSettings` Antworteigenschaften</span><span class="sxs-lookup"><span data-stu-id="06d18-146">`GetSettings` response properties</span></span>

>[!NOTE]
><span data-ttu-id="06d18-147">Die vom Aufruf zurückgegebenen Parameter `getSettings` unterscheiden sich, wenn Sie diese Methode über eine Registerkarte aufrufen, und unterscheiden sich von den parametern, die in den [JS-Einstellungen](/javascript/api/%40microsoft/teams-js/settings.settings?view=msteams-client-js-latest&preserve-view=true)dokumentiert sind.</span><span class="sxs-lookup"><span data-stu-id="06d18-147">The parameters returned by the `getSettings` call are different when you invoke this method from a tab and differ from those documented in [js settings](/javascript/api/%40microsoft/teams-js/settings.settings?view=msteams-client-js-latest&preserve-view=true).</span></span>

<span data-ttu-id="06d18-148">Die folgende Tabelle enthält die Parameter und die Details der `GetSetting` Antworteigenschaften:</span><span class="sxs-lookup"><span data-stu-id="06d18-148">The following table provides the parameters and the details of `GetSetting` response properties:</span></span>

| <span data-ttu-id="06d18-149">Parameter</span><span class="sxs-lookup"><span data-stu-id="06d18-149">Parameters</span></span>   | <span data-ttu-id="06d18-150">Details</span><span class="sxs-lookup"><span data-stu-id="06d18-150">Details</span></span> |
|-------------|---------|
| `entityId`       | <span data-ttu-id="06d18-151">Die Entitäts-ID, die vom Code beim Aufrufen festgelegt `setSettings()` wird.</span><span class="sxs-lookup"><span data-stu-id="06d18-151">The entity ID, as set by your code when calling `setSettings()`.</span></span> |
| `configName`  | <span data-ttu-id="06d18-152">Der Konfigurationsname, wie er vom Code beim Aufrufen festgelegt `setSettings()` wird.</span><span class="sxs-lookup"><span data-stu-id="06d18-152">The configuration name, as set by your code when calling `setSettings()`.</span></span> |
| `contentUrl` | <span data-ttu-id="06d18-153">Die URL der Konfigurationsseite, die vom Code beim Aufrufen festgelegt `setSettings()` wird.</span><span class="sxs-lookup"><span data-stu-id="06d18-153">The URL of the configuration page, as set by your code when calling `setSettings()`.</span></span> |
| `webhookUrl` | <span data-ttu-id="06d18-154">Die für den Connector erstellte Webhook-URL.</span><span class="sxs-lookup"><span data-stu-id="06d18-154">The webhook URL created for the connector.</span></span> <span data-ttu-id="06d18-155">Verwenden Sie die Webhook-URL, um strukturierten JSON-Code zu POSTEN, um Karten an den Kanal zu senden.</span><span class="sxs-lookup"><span data-stu-id="06d18-155">Use the webhook URL to POST structured JSON to send cards to the channel.</span></span> <span data-ttu-id="06d18-156">Wird `webhookUrl` nur zurückgegeben, wenn die Anwendung Daten erfolgreich zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="06d18-156">The `webhookUrl` is returned only when the application returns data successfully.</span></span> |
| `appType` | <span data-ttu-id="06d18-157">Die zurückgegebenen Werte können den `mail` `groups` Office 365 `teams` E-Mail-, Office 365- oder Microsoft Teams entsprechen.</span><span class="sxs-lookup"><span data-stu-id="06d18-157">The values returned can be `mail`, `groups`, or `teams` corresponding to the Office 365 Mail, Office 365 Groups, or Microsoft Teams respectively.</span></span> |
| `userObjectId` | <span data-ttu-id="06d18-158">Die eindeutige ID, die dem Office 365 Benutzer entspricht, der die Einrichtung des Connectors initiiert hat.</span><span class="sxs-lookup"><span data-stu-id="06d18-158">The unique ID corresponding to the Office 365 user who initiated the set up of the connector.</span></span> <span data-ttu-id="06d18-159">Sie muss gesichert werden.</span><span class="sxs-lookup"><span data-stu-id="06d18-159">It must be secured.</span></span> <span data-ttu-id="06d18-160">Dieser Wert kann verwendet werden, um den Benutzer in Office 365 zuzuordnen, der die Konfiguration in Ihrem Dienst eingerichtet hat.</span><span class="sxs-lookup"><span data-stu-id="06d18-160">This value can be used to associate the user in Office 365, who has set up the configuration in your service.</span></span> |

#### <a name="handle-edits"></a><span data-ttu-id="06d18-161">Bearbeiten behandeln</span><span class="sxs-lookup"><span data-stu-id="06d18-161">Handle edits</span></span>

<span data-ttu-id="06d18-162">Ihr Code muss Benutzer verarbeiten, die zurückkehren, um eine vorhandene Connectorkonfiguration zu bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="06d18-162">Your code must handle users who return to edit an existing connector configuration.</span></span> <span data-ttu-id="06d18-163">Rufen Sie dazu `microsoftTeams.settings.setSettings()` während der Anfänglichen Konfiguration die folgenden Parameter auf:</span><span class="sxs-lookup"><span data-stu-id="06d18-163">To do this, call `microsoftTeams.settings.setSettings()` during the initial configuration with the following parameters:</span></span>

- <span data-ttu-id="06d18-164">`entityId` ist die benutzerdefinierte ID, die darstellt, was der Benutzer von Ihrem Dienst konfiguriert und verstanden hat.</span><span class="sxs-lookup"><span data-stu-id="06d18-164">`entityId` is the custom ID that represents what the user has configured and understood by your service.</span></span>
- <span data-ttu-id="06d18-165">`configName` ist ein Name, den Konfigurationscode abrufen kann.</span><span class="sxs-lookup"><span data-stu-id="06d18-165">`configName` is a name that configuration code can retrieve.</span></span>
- <span data-ttu-id="06d18-166">`contentUrl` ist eine benutzerdefinierte URL, die geladen wird, wenn ein Benutzer eine vorhandene Connectorkonfiguration bearbeitet.</span><span class="sxs-lookup"><span data-stu-id="06d18-166">`contentUrl` is a custom URL that gets loaded when a user edits an existing connector configuration.</span></span>

<span data-ttu-id="06d18-167">Dieser Aufruf erfolgt als Teil des Speicherereignishandlers.</span><span class="sxs-lookup"><span data-stu-id="06d18-167">This call is made as part of your save event handler.</span></span> <span data-ttu-id="06d18-168">Wenn der Code geladen wird, muss er dann `contentUrl` aufgerufen werden, um alle Einstellungen oder Formulare `getSettings()` in der Konfigurationsbenutzeroberfläche vorab auszufüllen.</span><span class="sxs-lookup"><span data-stu-id="06d18-168">Then, when the `contentUrl` is loaded, your code must call `getSettings()` to pre populate any settings or forms in your configuration user interface.</span></span>

#### <a name="handle-removals"></a><span data-ttu-id="06d18-169">Behandeln von Entfernungen</span><span class="sxs-lookup"><span data-stu-id="06d18-169">Handle removals</span></span>

<span data-ttu-id="06d18-170">Sie können einen Ereignishandler ausführen, wenn der Benutzer eine vorhandene Connectorkonfiguration entfernt.</span><span class="sxs-lookup"><span data-stu-id="06d18-170">You can execute an event handler when the user removes an existing connector configuration.</span></span> <span data-ttu-id="06d18-171">Sie registrieren diesen Handler durch Aufrufen `microsoftTeams.settings.registerOnRemoveHandler()` von .</span><span class="sxs-lookup"><span data-stu-id="06d18-171">You register this handler by calling `microsoftTeams.settings.registerOnRemoveHandler()`.</span></span> <span data-ttu-id="06d18-172">Dieser Handler wird zum Ausführen von Bereinigungsvorgängen verwendet, z. B. zum Entfernen von Einträgen aus einer Datenbank.</span><span class="sxs-lookup"><span data-stu-id="06d18-172">This handler is used to perform cleanup operations, such as removing entries from a database.</span></span>

### <a name="include-the-connector-in-your-manifest"></a><span data-ttu-id="06d18-173">Einschließen des Connectors in Das Manifest</span><span class="sxs-lookup"><span data-stu-id="06d18-173">Include the connector in your Manifest</span></span>

<span data-ttu-id="06d18-174">Laden Sie das automatisch generierte `Teams app manifest` Aus dem Portal herunter.</span><span class="sxs-lookup"><span data-stu-id="06d18-174">Download the auto generated `Teams app manifest` from the portal.</span></span> <span data-ttu-id="06d18-175">Führen Sie die folgenden Schritte aus, bevor Sie die App testen oder veröffentlichen:</span><span class="sxs-lookup"><span data-stu-id="06d18-175">Perform the following steps, before testing or publishing the app:</span></span>

1. <span data-ttu-id="06d18-176">[Zwei Symbole einschließen](../../concepts/build-and-test/apps-package.md#app-icons).</span><span class="sxs-lookup"><span data-stu-id="06d18-176">[Include two icons](../../concepts/build-and-test/apps-package.md#app-icons).</span></span>
1. <span data-ttu-id="06d18-177">Ändern Sie den `icons` Teil des Manifests so, dass er die Dateinamen der Symbole anstelle von URLs enthält.</span><span class="sxs-lookup"><span data-stu-id="06d18-177">Modify the `icons` portion of the manifest to include the file names of the icons instead of URLs.</span></span>

<span data-ttu-id="06d18-178">Die folgende manifest.jszur Datei enthält die Elemente, die zum Testen und Übermitteln der App erforderlich sind:</span><span class="sxs-lookup"><span data-stu-id="06d18-178">The following manifest.json file contains the elements needed to test and submit the app:</span></span>

> [!NOTE]
> <span data-ttu-id="06d18-179">Ersetzen Sie `id` im folgenden Beispiel die `connectorId` GUID des Connectors.</span><span class="sxs-lookup"><span data-stu-id="06d18-179">Replace `id` and `connectorId` in the following example with the GUID of the connector.</span></span>

#### <a name="example-of-manifestjson-with-connector"></a><span data-ttu-id="06d18-180">Beispiel für manifest.jsmit Connector</span><span class="sxs-lookup"><span data-stu-id="06d18-180">Example of manifest.json with connector</span></span>

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
    "full": "This is a small sample app we made for you! This app has samples of all capabilities Microsoft Teams supports.",
    "short": "This is a small sample app we made for you!"
  },
  "icons": {
    "outline": "sampleapp-outline.png",
    "color": "sampleapp-color.png"
  },
  "connectors": [
    {
      "connectorId": "e9343a03-0a5e-4c1f-95a8-263a565505a5",
      "scopes": [
        "team"
      ]
    }
  ],
  "name": {
    "short": "Sample App",
    "full": "Sample App"
  },
  "accentColor": "#FFFFFF",
  "needsIdentity": "true"
}
```

## <a name="enable-or-disable-connectors-in-teams"></a><span data-ttu-id="06d18-181">Aktivieren oder Deaktivieren von Connectors in Teams</span><span class="sxs-lookup"><span data-stu-id="06d18-181">Enable or disable connectors in Teams</span></span>

<span data-ttu-id="06d18-182">Das Exchange Online PowerShell V2-Modul verwendet moderne Authentifizierung und arbeitet mit mehrstufiger Authentifizierung, die als MFA bezeichnet wird, um eine Verbindung mit allen Exchange zugehörigen PowerShell-Umgebungen in Microsoft 365 herzustellen.</span><span class="sxs-lookup"><span data-stu-id="06d18-182">The Exchange Online PowerShell V2 module uses modern authentication and works with multi factor authentication, called MFA for connecting to all Exchange related PowerShell environments in Microsoft 365.</span></span> <span data-ttu-id="06d18-183">Administratoren können Exchange Online PowerShell verwenden, um Connectors für einen ganzen Mandanten oder ein bestimmtes Gruppenpostfach zu deaktivieren, was sich auf alle Benutzer in diesem Mandanten oder Postfach auswirkt.</span><span class="sxs-lookup"><span data-stu-id="06d18-183">Admins can use Exchange Online PowerShell to disable connectors for an entire tenant or a specific group mailbox, affecting all users in that tenant or mailbox.</span></span> <span data-ttu-id="06d18-184">Es ist nicht möglich, für einige und nicht für andere zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="06d18-184">It is not possible to disable for some and not others.</span></span> <span data-ttu-id="06d18-185">Außerdem sind Connectors standardmäßig für Government Community Cloud deaktiviert, die als GCC Mandanten bezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="06d18-185">Also, connectors are disabled by default for Government Community Cloud, called GCC tenants.</span></span>

<span data-ttu-id="06d18-186">Die Einstellung auf Mandantenebene setzt die Einstellung auf Gruppenebene außer Kraft.</span><span class="sxs-lookup"><span data-stu-id="06d18-186">The tenant level setting overrides the group level setting.</span></span> <span data-ttu-id="06d18-187">Wenn ein Administrator beispielsweise Connectors für die Gruppe aktiviert und auf dem Mandanten deaktiviert, sind Connectors für die Gruppe deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="06d18-187">For example, if an admin enables connectors for the group and disables them on the tenant, connectors for the group is disabled.</span></span> <span data-ttu-id="06d18-188">Um einen Connector in Teams zu aktivieren, stellen Sie mithilfe der modernen Authentifizierung mit oder ohne MFA eine Verbindung mit [Exchange Online PowerShell her.](/powershell/exchange/connect-to-exchange-online-powershell?view=exchange-ps#connect-to-exchange-online-powershell-using-modern-authentication-with-or-without-mfa&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="06d18-188">To enable a connector in Teams, [connect to Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell?view=exchange-ps#connect-to-exchange-online-powershell-using-modern-authentication-with-or-without-mfa&preserve-view=true) using modern authentication with or without MFA.</span></span>

### <a name="commands-to-enable-or-disable-connectors"></a><span data-ttu-id="06d18-189">Befehle zum Aktivieren oder Deaktivieren von Connectors</span><span class="sxs-lookup"><span data-stu-id="06d18-189">Commands to enable or disable connectors</span></span>

<span data-ttu-id="06d18-190">Führen Sie die folgenden Befehle in Exchange Online PowerShell aus:</span><span class="sxs-lookup"><span data-stu-id="06d18-190">Run the following commands in Exchange Online PowerShell:</span></span>

* <span data-ttu-id="06d18-191">So deaktivieren Sie Connectors für den Mandanten: `Set-OrganizationConfig -ConnectorsEnabled:$false` .</span><span class="sxs-lookup"><span data-stu-id="06d18-191">To disable connectors for the tenant: `Set-OrganizationConfig -ConnectorsEnabled:$false`.</span></span>
* <span data-ttu-id="06d18-192">So deaktivieren Sie Nachrichten mit Aktionen für den Mandanten: `Set-OrganizationConfig -ConnectorsActionableMessagesEnabled:$false` .</span><span class="sxs-lookup"><span data-stu-id="06d18-192">To disable actionable messages for the tenant: `Set-OrganizationConfig -ConnectorsActionableMessagesEnabled:$false`.</span></span>
* <span data-ttu-id="06d18-193">Führen Sie die folgenden Befehle aus, um Connectors für Teams zu aktivieren:</span><span class="sxs-lookup"><span data-stu-id="06d18-193">To enable connectors for Teams, run the following commands:</span></span>
  * `Set-OrganizationConfig -ConnectorsEnabled:$true `
  * `Set-OrganizationConfig -ConnectorsEnabledForTeams:$true`
  * `Set-OrganizationConfig -ConnectorsActionableMessagesEnabled:$true`

<span data-ttu-id="06d18-194">Weitere Informationen zum Austausch von PowerShell-Modulen finden Sie unter ["Set-OrganizationConfig".](/powershell/module/exchange/Set-OrganizationConfig?view=exchange-ps&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="06d18-194">For more information on PowerShell module exchange, see [Set-OrganizationConfig](/powershell/module/exchange/Set-OrganizationConfig?view=exchange-ps&preserve-view=true).</span></span> <span data-ttu-id="06d18-195">Um Outlook Connectors zu aktivieren oder zu deaktivieren, [verbinden Sie Apps mit Ihren Gruppen in Outlook.](https://support.microsoft.com/topic/connect-apps-to-your-groups-in-outlook-ed0ce547-038f-4902-b9b3-9e518ae6fbab?ui=en-us&rs=en-us&ad=us)</span><span class="sxs-lookup"><span data-stu-id="06d18-195">To enable or disable Outlook connectors, [connect apps to your groups in Outlook](https://support.microsoft.com/topic/connect-apps-to-your-groups-in-outlook-ed0ce547-038f-4902-b9b3-9e518ae6fbab?ui=en-us&rs=en-us&ad=us).</span></span>

## <a name="test-your-connector"></a><span data-ttu-id="06d18-196">Testen des Connectors</span><span class="sxs-lookup"><span data-stu-id="06d18-196">Test your connector</span></span>

<span data-ttu-id="06d18-197">Laden Sie den Connector mit einer anderen App in ein Team hoch, um den Connector zu testen.</span><span class="sxs-lookup"><span data-stu-id="06d18-197">To test your connector, upload it to a team with any other app.</span></span> <span data-ttu-id="06d18-198">Sie können ein .zip-Paket mithilfe der Manifestdatei aus den beiden Symboldateien und Connectors Erstellen Entwicklerdashboard, geändert wie unter ["Einschließen des Connectors in Ihr Manifest"](#include-the-connector-in-your-manifest)angegeben.</span><span class="sxs-lookup"><span data-stu-id="06d18-198">You can create a .zip package using the manifest file from the two icon files and connectors Developer Dashboard, modified as directed in [Include the connector in your Manifest](#include-the-connector-in-your-manifest).</span></span>

<span data-ttu-id="06d18-199">Nachdem Sie die App hochgeladen haben, öffnen Sie die Liste der Connectors aus einem beliebigen Kanal.</span><span class="sxs-lookup"><span data-stu-id="06d18-199">After you upload the app, open the connectors list from any channel.</span></span> <span data-ttu-id="06d18-200">Scrollen Sie nach unten, um Ihre App im Abschnitt **"Hochgeladen"** anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="06d18-200">Scroll to the bottom to see your app in the **Uploaded** section:</span></span>

![Screenshot eines hochgeladenen Abschnitts im Dialogfeld "Connector"](~/assets/images/connectors/connector_dialog_uploaded.png)

> [!NOTE]
> <span data-ttu-id="06d18-202">Der Fluss erfolgt vollständig innerhalb Microsoft Teams als gehostete Oberfläche.</span><span class="sxs-lookup"><span data-stu-id="06d18-202">The flow occurs entirely within Microsoft Teams as a hosted experience.</span></span>

<span data-ttu-id="06d18-203">Um zu überprüfen, ob die `HttpPOST` Aktion ordnungsgemäß funktioniert, [senden Sie Nachrichten an den Connector.](~/webhooks-and-connectors/how-to/connectors-using.md)</span><span class="sxs-lookup"><span data-stu-id="06d18-203">To verify that `HttpPOST` action is working correctly, [send messages to your connector](~/webhooks-and-connectors/how-to/connectors-using.md).</span></span>

## <a name="publish-connectors-for-the-organization"></a><span data-ttu-id="06d18-204">Veröffentlichen von Connectors für die Organisation</span><span class="sxs-lookup"><span data-stu-id="06d18-204">Publish connectors for the organization</span></span>

<span data-ttu-id="06d18-205">Wenn der Connector nur für die Benutzer in Ihrer Organisation verfügbar sein soll, können Sie Ihre benutzerdefinierte Connector-App in den [App-Katalog](~/concepts/deploy-and-publish/apps-publish.md)Ihrer Organisation hochladen.</span><span class="sxs-lookup"><span data-stu-id="06d18-205">If you want the connector to be available only to the users in your organization, you can upload your custom connector app to your [organization's app catalog](~/concepts/deploy-and-publish/apps-publish.md).</span></span>

<span data-ttu-id="06d18-206">Nachdem Sie das App-Paket hochgeladen haben, um den Connector in einem Team zu konfigurieren und zu verwenden, installieren Sie den Connector aus dem App-Katalog der Organisation.</span><span class="sxs-lookup"><span data-stu-id="06d18-206">After uploading the app package to configure and use the connector in a team, install the connector from the organization's app catalog.</span></span>

<span data-ttu-id="06d18-207">**So richten Sie einen Connector ein**</span><span class="sxs-lookup"><span data-stu-id="06d18-207">**To set up a connector**</span></span>

1. <span data-ttu-id="06d18-208">Wählen Sie in der linken Navigationsleiste **Apps** aus.</span><span class="sxs-lookup"><span data-stu-id="06d18-208">Select **Apps** from the left navigation bar.</span></span>
1. <span data-ttu-id="06d18-209">Wählen Sie im Abschnitt **"Apps"** **Connectors** aus.</span><span class="sxs-lookup"><span data-stu-id="06d18-209">In the **Apps** section, select **Connectors**.</span></span>
1. <span data-ttu-id="06d18-210">Wählen Sie den Connector aus, den Sie hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="06d18-210">Select the connector that you want to add.</span></span> <span data-ttu-id="06d18-211">Ein Popup-Dialogfeld wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="06d18-211">A pop up dialog window appears.</span></span>
1. <span data-ttu-id="06d18-212">Wählen Sie im Dropdownmenü die Option **"Zu einem Team hinzufügen"** aus.</span><span class="sxs-lookup"><span data-stu-id="06d18-212">From the dropdown menu, select **Add to a team**.</span></span>
1. <span data-ttu-id="06d18-213">Geben Sie im Suchfeld einen Team- oder Kanalnamen ein.</span><span class="sxs-lookup"><span data-stu-id="06d18-213">In the search box, type a team or channel name.</span></span>
1. <span data-ttu-id="06d18-214">Wählen Sie im Dropdownmenü in der unteren rechten Ecke des Dialogfelds die Option **"Connector einrichten"** aus.</span><span class="sxs-lookup"><span data-stu-id="06d18-214">Select **Set up a Connector** from the dropdown menu in the bottom right corner of the dialog window.</span></span>

<span data-ttu-id="06d18-215">Der Connector ist im Abschnitt &#9679;&#9679;&#9679; > **Weitere Optionen** Connectors  >    >  **alle** Connectors für Ihr  >  **Team** für dieses Team verfügbar.</span><span class="sxs-lookup"><span data-stu-id="06d18-215">The connector is available in the section &#9679;&#9679;&#9679; > **More options** > **Connectors** > **All** > **Connectors for your team** for that team.</span></span> <span data-ttu-id="06d18-216">Sie können navigieren, indem Sie zu diesem Abschnitt scrollen oder nach der Connector-App suchen.</span><span class="sxs-lookup"><span data-stu-id="06d18-216">You can navigate by scrolling to this section or search for the connector app.</span></span> <span data-ttu-id="06d18-217">Um den Connector zu konfigurieren oder zu ändern, wählen Sie **Konfigurieren** aus.</span><span class="sxs-lookup"><span data-stu-id="06d18-217">To configure or modify the connector, select **Configure**.</span></span>

## <a name="distribute-webhook-and-connector"></a><span data-ttu-id="06d18-218">Verteilen von Webhook und Connector</span><span class="sxs-lookup"><span data-stu-id="06d18-218">Distribute webhook and connector</span></span>

1. <span data-ttu-id="06d18-219">[Richten Sie einen eingehenden Webhook](~/webhooks-and-connectors/how-to/add-incoming-webhook.md?branch=pr-en-us-3076#create-incoming-webhook) direkt für Ihr Team ein.</span><span class="sxs-lookup"><span data-stu-id="06d18-219">[Set up an Incoming Webhook](~/webhooks-and-connectors/how-to/add-incoming-webhook.md?branch=pr-en-us-3076#create-incoming-webhook) directly for your team.</span></span>
1. <span data-ttu-id="06d18-220">Fügen Sie eine [Konfigurationsseite](~/webhooks-and-connectors/how-to/connectors-creating.md?branch=pr-en-us-3076#integrate-the-configuration-experience) hinzu, und [veröffentlichen Sie Ihren eingehenden Webhook](~/webhooks-and-connectors/how-to/connectors-creating.md?branch=pr-en-us-3076#publish-connectors-for-the-organization) in einem O365-Connector.</span><span class="sxs-lookup"><span data-stu-id="06d18-220">Add a [configuration page](~/webhooks-and-connectors/how-to/connectors-creating.md?branch=pr-en-us-3076#integrate-the-configuration-experience) and [publish your Incoming Webhook](~/webhooks-and-connectors/how-to/connectors-creating.md?branch=pr-en-us-3076#publish-connectors-for-the-organization) in a O365 Connector.</span></span>
1. <span data-ttu-id="06d18-221">Verpacken und veröffentlichen Sie Ihren Connector als Teil Ihrer [AppSource-Übermittlung.](~/concepts/deploy-and-publish/office-store-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="06d18-221">Package and publish your connector as part of your [AppSource](~/concepts/deploy-and-publish/office-store-guidance.md) submission.</span></span>

## <a name="code-sample"></a><span data-ttu-id="06d18-222">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="06d18-222">Code sample</span></span>

<span data-ttu-id="06d18-223">Die folgende Tabelle enthält den Beispielnamen und dessen Beschreibung:</span><span class="sxs-lookup"><span data-stu-id="06d18-223">The following table provides the sample name and its description:</span></span>

|<span data-ttu-id="06d18-224">**Beispielname**</span><span class="sxs-lookup"><span data-stu-id="06d18-224">**Sample name**</span></span> | <span data-ttu-id="06d18-225">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="06d18-225">**Description**</span></span> | <span data-ttu-id="06d18-226">**.NET**</span><span class="sxs-lookup"><span data-stu-id="06d18-226">**.NET**</span></span> | <span data-ttu-id="06d18-227">**Node.js**</span><span class="sxs-lookup"><span data-stu-id="06d18-227">**Node.js**</span></span> |
|----------------|------------------|--------|----------------|
| <span data-ttu-id="06d18-228">Connectors</span><span class="sxs-lookup"><span data-stu-id="06d18-228">Connectors</span></span>    | <span data-ttu-id="06d18-229">Beispiel Office 365 Connector, der Benachrichtigungen an Teams Kanal generiert.</span><span class="sxs-lookup"><span data-stu-id="06d18-229">Sample Office 365 Connector generating notifications to Teams channel.</span></span>|   [<span data-ttu-id="06d18-230">View</span><span class="sxs-lookup"><span data-stu-id="06d18-230">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-todo-notification/csharp) | [<span data-ttu-id="06d18-231">View</span><span class="sxs-lookup"><span data-stu-id="06d18-231">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-github-notification/nodejs)|
| <span data-ttu-id="06d18-232">Beispiel für generische Connectors</span><span class="sxs-lookup"><span data-stu-id="06d18-232">Generic connectors sample</span></span> |<span data-ttu-id="06d18-233">Beispielcode für einen generischen Connector, der für jedes System, das Webhooks unterstützt, einfach angepasst werden kann.</span><span class="sxs-lookup"><span data-stu-id="06d18-233">Sample code for a generic connector that is easy to customize for any system that supports webhooks.</span></span>|  | [<span data-ttu-id="06d18-234">View</span><span class="sxs-lookup"><span data-stu-id="06d18-234">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-generic/nodejs)|

## <a name="see-also"></a><span data-ttu-id="06d18-235">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="06d18-235">See also</span></span>

* [<span data-ttu-id="06d18-236">Nachrichten erstellen und senden</span><span class="sxs-lookup"><span data-stu-id="06d18-236">Create and send messages</span></span>](~/webhooks-and-connectors/how-to/connectors-using.md)
* [<span data-ttu-id="06d18-237">Erstellen eines eingehenden Webhooks</span><span class="sxs-lookup"><span data-stu-id="06d18-237">Create an Incoming Webhook</span></span>](~/webhooks-and-connectors/how-to/add-incoming-webhook.md)
* [<span data-ttu-id="06d18-238">Erstellen eines Office 365-Connectors</span><span class="sxs-lookup"><span data-stu-id="06d18-238">Create an Office 365 Connector</span></span>](~/webhooks-and-connectors/how-to/connectors-creating.md)
