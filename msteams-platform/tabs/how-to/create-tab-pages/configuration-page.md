---
title: Erstellen einer Konfigurationsseite
author: laujan
description: Erstellen einer Konfigurationsseite
keywords: Teams Tabs Gruppenkanal konfigurierbar
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: aeab1cf96d1e875db79d9143fefd0e46348f585a
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566684"
---
# <a name="create-a-configuration-page"></a><span data-ttu-id="6be13-104">Erstellen einer Konfigurationsseite</span><span class="sxs-lookup"><span data-stu-id="6be13-104">Create a configuration page</span></span>

<span data-ttu-id="6be13-105">Eine Konfigurationsseite ist ein spezieller [Inhaltstyp](content-page.md).</span><span class="sxs-lookup"><span data-stu-id="6be13-105">A configuration page is a special type of [content page](content-page.md).</span></span> <span data-ttu-id="6be13-106">Die Benutzer konfigurieren einige Aspekte der Microsoft Teams-App mithilfe der Konfigurationsseite und verwenden diese Konfiguration als Teil der folgenden:</span><span class="sxs-lookup"><span data-stu-id="6be13-106">The users configure some aspects of the Microsoft Teams app using the configuration page and use that configuration as part of the following:</span></span>

* <span data-ttu-id="6be13-107">Eine Registerkarte für Kanal- oder Gruppenchats: Sammeln Sie Informationen von den Benutzern, und legen Sie fest, dass die `contentUrl` Inhaltsseite angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="6be13-107">A channel or group chat tab: Collect information from the users and set the `contentUrl` of the content page to display.</span></span>
* <span data-ttu-id="6be13-108">Eine [Messagingerweiterung](~/messaging-extensions/what-are-messaging-extensions.md).</span><span class="sxs-lookup"><span data-stu-id="6be13-108">A [messaging extension](~/messaging-extensions/what-are-messaging-extensions.md).</span></span>
* <span data-ttu-id="6be13-109">Ein [Office 365 Connector](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md).</span><span class="sxs-lookup"><span data-stu-id="6be13-109">An [Office 365 Connector](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md).</span></span>

## <a name="configuring-a-channel-or-group-chat-tab"></a><span data-ttu-id="6be13-110">Konfigurieren einer Kanal- oder Gruppenchat-Registerkarte</span><span class="sxs-lookup"><span data-stu-id="6be13-110">Configuring a channel or group chat tab</span></span>

<span data-ttu-id="6be13-111">Die Anwendung muss auf das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) verweisen und `microsoft.initialize()` aufrufen.</span><span class="sxs-lookup"><span data-stu-id="6be13-111">The application must reference the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) and call `microsoft.initialize()`.</span></span> <span data-ttu-id="6be13-112">Außerdem müssen die verwendeten URLs https-Endpunkte gesichert und in der Cloud verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="6be13-112">Also, the URLs used must be secured HTTPS endpoints and available from the cloud.</span></span> 

### <a name="example"></a><span data-ttu-id="6be13-113">Beispiel</span><span class="sxs-lookup"><span data-stu-id="6be13-113">Example</span></span>

<span data-ttu-id="6be13-114">Ein Beispiel für eine Konfigurationsseite wird in der folgenden Abbildung gezeigt:</span><span class="sxs-lookup"><span data-stu-id="6be13-114">An example of a configuration page is shown in the following image:</span></span> 

<img src="~/assets/images/tab-images/configuration-page.png" alt="Configuration page" width="400"/>

<span data-ttu-id="6be13-115">Der entsprechende Code für die Konfigurationsseite wird im folgenden Abschnitt gezeigt:</span><span class="sxs-lookup"><span data-stu-id="6be13-115">The corresponding code for configuration page is shown in the following section:</span></span>

```html
<head>
<script src='https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js'></script>
</head>
    <body>
        <button onclick="(document.getElementById('icon').src = '/images/iconGray.png'); colorClickGray()">Select Gray</button>
        <img id="icon" src="/images/teamsIcon.png" alt="icon" style="width:100px" />
        <button onclick="(document.getElementById('icon').src = '/images/iconRed.png'); colorClickRed()">Select Red</button>

        <script>
            microsoftTeams.initialize();
            let saveGray = () => {
                microsoftTeams.settings.registerOnSaveHandler((saveEvent) => {
                    microsoftTeams.settings.setSettings({
                        websiteUrl: "https://yourWebsite.com",
                        contentUrl: "https://yourWebsite.com/gray",
                        entityId: "grayIconTab",
                        suggestedDisplayName: "MyNewTab"
                    });
                    saveEvent.notifySuccess();
                });
            }
            let saveRed = () => {
                microsoftTeams.settings.registerOnSaveHandler((saveEvent) => {
                    microsoftTeams.settings.setSettings({
                        websiteUrl: "https://yourWebsite.com",
                        contentUrl: "https://yourWebsite.com/red",
                        entityId: "redIconTab",
                        suggestedDisplayName: "MyNewTab"
                    });
                    saveEvent.notifySuccess();
                });
            }

            let gr = document.getElementById("gray").style;
            let rd = document.getElementById("red").style;

            const colorClickGray = () => {
                gr.display = "block";
                rd.display = "none";
                microsoftTeams.settings.setValidityState(true);
                saveGray()
            }

            const colorClickRed = () => {
                rd.display = "block";
                gr.display = "none";
                microsoftTeams.settings.setValidityState(true);
                saveRed();
            }
        </script>
    </body>
...
```

<span data-ttu-id="6be13-116">Wählen Sie entweder **Grau auswählen** **oder** Rote Schaltfläche auf der Konfigurationsseite, um den Tab-Inhalt mit einem grauen oder roten Symbol anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="6be13-116">Choose either **Select Gray** or **Select Red** button in the configuration page, to display the tab content with a gray or red icon.</span></span> 

<span data-ttu-id="6be13-117">In der folgenden Abbildung wird der Tabstoppinhalt mit einem grauen Symbol angezeigt:</span><span class="sxs-lookup"><span data-stu-id="6be13-117">The following image displays the tab content with gray icon:</span></span>

<img src="~/assets/images/tab-images/configure-tab-with-gray.png" alt="Configure tab with select gray" width="400"/>

<span data-ttu-id="6be13-118">In der folgenden Abbildung wird der Tabstoppinhalt mit einem roten Symbol angezeigt:</span><span class="sxs-lookup"><span data-stu-id="6be13-118">The following image displays the tab content with red icon:</span></span>

<img src="~/assets/images/tab-images/configure-tab-with-red.png" alt="Configure tab with select red" width="400"/>

<span data-ttu-id="6be13-119">Die Auswahl der relativen Schaltfläche löst entweder `saveGray()` oder aus und ruft Folgendes `saveRed()` auf:</span><span class="sxs-lookup"><span data-stu-id="6be13-119">Choosing the relative button triggers either `saveGray()` or `saveRed()`, and invokes the following:</span></span>

1. <span data-ttu-id="6be13-120">Der `settings.setValidityState(true)` ist auf wahr eingestellt.</span><span class="sxs-lookup"><span data-stu-id="6be13-120">The `settings.setValidityState(true)` is set to true.</span></span>
1. <span data-ttu-id="6be13-121">Der `microsoftTeams.settings.registerOnSaveHandler()` Ereignishandler wird ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="6be13-121">The `microsoftTeams.settings.registerOnSaveHandler()` event handler is triggered.</span></span>
1. <span data-ttu-id="6be13-122">Die Schaltfläche **Speichern** auf der Konfigurationsseite der App, die in Teams hochgeladen wurde, ist aktiviert.</span><span class="sxs-lookup"><span data-stu-id="6be13-122">The **Save** button on the app's configuration page, uploaded in Teams, is enabled.</span></span>

<span data-ttu-id="6be13-123">Der Konfigurationsseitencode informiert die Teams, dass die Konfigurationsanforderungen erfüllt sind und die Installation fortgesetzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="6be13-123">The configuration page code informs the Teams that the configuration requirements are satisfied and the installation can proceed.</span></span> <span data-ttu-id="6be13-124">Wenn der Benutzer **Speichern** auswählt, werden die Parameter von `settings.setSettings()` festgelegt, wie durch die Schnittstelle `Settings` definiert.</span><span class="sxs-lookup"><span data-stu-id="6be13-124">When the user selects **Save**, the parameters of `settings.setSettings()` are set, as defined by the `Settings` interface.</span></span> <span data-ttu-id="6be13-125">Weitere Informationen finden Sie [unter Einstellungen Schnittstelle](/javascript/api/@microsoft/teams-js/_settings?view=msteams-client-js-latest&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="6be13-125">For more information, see [Settings interface](/javascript/api/@microsoft/teams-js/_settings?view=msteams-client-js-latest&preserve-view=true).</span></span> <span data-ttu-id="6be13-126">Im letzten Schritt `saveEvent.notifySuccess()` wird aufgerufen, um anzugeben, dass die Inhalts-URL erfolgreich aufgelöst wurde.</span><span class="sxs-lookup"><span data-stu-id="6be13-126">In the last step, `saveEvent.notifySuccess()` is called to indicate that the content URL has successfully resolved.</span></span>

>[!NOTE]
>
>* <span data-ttu-id="6be13-127">Wenn Sie einen Speicherhandler mithilfe von `microsoftTeams.settings.registerOnSaveHandler()` registrieren, muss der Rückruf `saveEvent.notifySuccess()` aufgerufen werden oder das Ergebnis der Konfiguration `saveEvent.notifyFailure()` angeben.</span><span class="sxs-lookup"><span data-stu-id="6be13-127">If you register a save handler using `microsoftTeams.settings.registerOnSaveHandler()`, the callback must invoke `saveEvent.notifySuccess()` or `saveEvent.notifyFailure()` to indicate the outcome of the configuration.</span></span>
>* <span data-ttu-id="6be13-128">Wenn Sie keinen Speicherhandler registrieren, wird der `saveEvent.notifySuccess()` Aufruf automatisch durchgeführt, wenn der Benutzer **Speichern** auswählt.</span><span class="sxs-lookup"><span data-stu-id="6be13-128">If you don't register a save handler, the `saveEvent.notifySuccess()` call is made automatically when the user selects **Save**.</span></span>

### <a name="get-context-data-for-your-tab-settings"></a><span data-ttu-id="6be13-129">Abrufen von Kontextdaten für Ihre Registerkarteneinstellungen</span><span class="sxs-lookup"><span data-stu-id="6be13-129">Get context data for your tab settings</span></span>

<span data-ttu-id="6be13-130">Auf der Registerkarte sind möglicherweise Kontextinformationen zum Anzeigen relevanter Inhalte erforderlich.</span><span class="sxs-lookup"><span data-stu-id="6be13-130">Your tab might require contextual information to display relevant content.</span></span> <span data-ttu-id="6be13-131">Kontextbezogene Informationen erhöhen die Attraktivität Ihres Tabs weiter, indem sie eine individuellere Benutzererfahrung bieten.</span><span class="sxs-lookup"><span data-stu-id="6be13-131">Contextual information further enhances your tab's appeal by providing a more customized user experience.</span></span>

<span data-ttu-id="6be13-132">Weitere Informationen zu den Eigenschaften, die für die Registerkartenkonfiguration verwendet werden, finden Sie unter [Kontextschnittstelle](/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="6be13-132">For more information on the properties used for tab configuration, see [Context interface](/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true).</span></span> <span data-ttu-id="6be13-133">Sammeln Sie die Werte von Kontextdatenvariablen auf zwei Arten:</span><span class="sxs-lookup"><span data-stu-id="6be13-133">Collect the values of context data variables in the following two ways:</span></span>

1. <span data-ttu-id="6be13-134">Fügen Sie URL-Abfragezeichenfolgenplatzhalter in die `configurationURL` .</span><span class="sxs-lookup"><span data-stu-id="6be13-134">Insert URL query string placeholders in your manifest's `configurationURL`.</span></span>

1. <span data-ttu-id="6be13-135">Verwenden Sie die [Teams SDK-Methode.](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) `microsoftTeams.getContext((context) =>{})`</span><span class="sxs-lookup"><span data-stu-id="6be13-135">Use the [Teams SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) `microsoftTeams.getContext((context) =>{})` method.</span></span>

#### <a name="insert-placeholders-in-the-configurationurl"></a><span data-ttu-id="6be13-136">Platzhalter in die `configurationUrl`</span><span class="sxs-lookup"><span data-stu-id="6be13-136">Insert placeholders in the `configurationUrl`</span></span>

<span data-ttu-id="6be13-137">Fügen Sie Ihrer Basis Kontextschnittstellenplatzhalter `configurationUrl` hinzu.</span><span class="sxs-lookup"><span data-stu-id="6be13-137">Add context interface placeholders to your base `configurationUrl`.</span></span> <span data-ttu-id="6be13-138">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="6be13-138">For example:</span></span>

##### <a name="base-url"></a><span data-ttu-id="6be13-139">Basis-URL</span><span class="sxs-lookup"><span data-stu-id="6be13-139">Base URL</span></span>

```json
...
"configurationUrl": "https://yourWebsite/config",
...
```

#### <a name="base-url-with-query-strings"></a><span data-ttu-id="6be13-140">Basis-URL mit Abfragezeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="6be13-140">Base URL with query strings</span></span>

```json
...
"configurationUrl": "https://yourWebsite/config?team={teamId}&channel={channelId}&{locale}"
...
```

<span data-ttu-id="6be13-141">Nach dem Hochladen der Seite aktualisiert die Teams die Platzhalter der Abfragezeichenfolge mit relevanten Werten.</span><span class="sxs-lookup"><span data-stu-id="6be13-141">After your page uploads, the Teams updates the query string placeholders with relevant values.</span></span> <span data-ttu-id="6be13-142">Schließen Sie Logik in die Konfigurationsseite ein, um diese Werte abzurufen und zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="6be13-142">Include logic in the configuration page to retrieve and use those values.</span></span> <span data-ttu-id="6be13-143">Weitere Informationen zum Arbeiten mit URL-Abfragezeichenfolgen finden Sie unter [URLSearchParams](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) in MDN Web Docs. Im folgenden Beispiel wird beschrieben, wie ein Wert aus der Eigenschaft extrahiert werden `configurationUrl` kann:</span><span class="sxs-lookup"><span data-stu-id="6be13-143">For more information on working with URL query strings, see [URLSearchParams](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) in MDN Web Docs. The following example describes the way to extract a value from the `configurationUrl` property:</span></span>

```html
<script>
   microsoftTeams.initialize();
   const getId = () => {
        let urlParams = new URLSearchParams(document.location.search.substring(1));
        let blueTeamId = urlParams.get('team');
        return blueTeamId
    }
//For testing, you can invoke the following to view the pertinent value:
document.write(getId());
</script>
```

### <a name="use-the-getcontext-function-to-retrieve-context"></a><span data-ttu-id="6be13-144">Verwenden der `getContext()` Funktion zum Abrufen des Kontexts</span><span class="sxs-lookup"><span data-stu-id="6be13-144">Use the `getContext()` function to retrieve context</span></span>

<span data-ttu-id="6be13-145">Die `microsoftTeams.getContext((context) => {})` Funktion ruft die [Context-Schnittstelle](/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true) ab, wenn sie aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="6be13-145">The `microsoftTeams.getContext((context) => {})` function retrieves the [Context interface](/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true) when invoked.</span></span> <span data-ttu-id="6be13-146">Fügen Sie diese Funktion der Konfigurationsseite hinzu, um Kontextwerte abzurufen:</span><span class="sxs-lookup"><span data-stu-id="6be13-146">Add this function to the configuration page to retrieve context values:</span></span>

```html
<!-- `userPrincipalName` will render in the span with the id "user". -->

<span id="user"></span>
...
<script>
    microsoftTeams.getContext((context) =>{
        let userId = document.getElementById('user');
        userId.innerHTML = context.userPrincipalName;
    });
</script>
...
```

## <a name="context-and-authentication"></a><span data-ttu-id="6be13-147">Kontext und Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="6be13-147">Context and authentication</span></span>

 <span data-ttu-id="6be13-148">Authentifizieren, bevor sie einem Benutzer erlauben, Ihre App zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="6be13-148">Authenticate before allowing a user to configure your app.</span></span> <span data-ttu-id="6be13-149">Andernfalls können Ihre Inhalte Quellen enthalten, die über ihre Authentifizierungsprotokolle verfügen.</span><span class="sxs-lookup"><span data-stu-id="6be13-149">Otherwise, your content might include sources that have their authentication protocols.</span></span> <span data-ttu-id="6be13-150">Weitere Informationen finden Sie unter [Authentifizieren eines Benutzers auf einer Registerkarte Microsoft Teams](~/tabs/how-to/authentication/auth-flow-tab.md). Verwenden Sie Kontextinformationen, um die Authentifizierungsanforderungen und Autorisierungsseiten-URLs zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="6be13-150">For more information, see [Authenticate a user in a Microsoft Teams tab](~/tabs/how-to/authentication/auth-flow-tab.md). Use context information to construct the authentication requests and authorization page URLs.</span></span>
<span data-ttu-id="6be13-151">Stellen Sie sicher, dass alle Domänen, die auf den Registerkarten verwendet werden, im und im Array aufgeführt `manifest.json` `validDomains` sind.</span><span class="sxs-lookup"><span data-stu-id="6be13-151">Ensure that all domains used in your tab pages are listed in the `manifest.json` and `validDomains` array.</span></span>

## <a name="modify-or-remove-a-tab"></a><span data-ttu-id="6be13-152">Ändern oder Entfernen einer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="6be13-152">Modify or remove a tab</span></span>

<span data-ttu-id="6be13-153">Unterstützte Entfernungsoptionen verfeinern die Benutzerfreundlichkeit weiter.</span><span class="sxs-lookup"><span data-stu-id="6be13-153">Supported removal options further refine the user experience.</span></span> <span data-ttu-id="6be13-154">Legen Sie die Eigenschaft des Manifests `canUpdateConfiguration` auf , die es den Benutzern `true` ermöglicht, eine Gruppen- oder Kanalregisterkarte zu ändern, neu zu konfigurieren oder umzubenennen. Geben Sie außerdem an, was mit dem Inhalt geschieht, wenn eine Registerkarte entfernt wird, indem Sie eine Seite mit den Entfernungsoptionen in die App einschließen und einen Wert für die `removeUrl` Eigenschaft in der Konfiguration  `setSettings()` festlegen.</span><span class="sxs-lookup"><span data-stu-id="6be13-154">Set your manifest's `canUpdateConfiguration` property to `true`, that enables the users to modify, reconfigure, or rename a group or channel tab. Also, indicate what happens to the content when a tab is removed, by including a removal options page in the app and setting a value for the `removeUrl` property in the  `setSettings()` configuration.</span></span> <span data-ttu-id="6be13-155">Der Benutzer kann die Registerkarten "Personal" deinstallieren, sie jedoch nicht ändern.</span><span class="sxs-lookup"><span data-stu-id="6be13-155">The user can uninstall the Personal tabs but cannot modify them.</span></span> <span data-ttu-id="6be13-156">Weitere Informationen finden Sie unter [Erstellen einer Entfernungsseite für Ihre Registerkarte](~/tabs/how-to/create-tab-pages/removal-page.md).</span><span class="sxs-lookup"><span data-stu-id="6be13-156">For more information, see [Create a removal page for your tab](~/tabs/how-to/create-tab-pages/removal-page.md).</span></span>

<span data-ttu-id="6be13-157">Microsoft Teams setSettings()-Konfiguration zum Entfernen:</span><span class="sxs-lookup"><span data-stu-id="6be13-157">Microsoft Teams setSettings() configuration for removal page:</span></span>

```javascript
microsoftTeams.settings.setSettings({
    contentUrl: "add content page URL here",
    entityId: "add unique name here",
    suggestedDisplayName: "add name to display on tab here",
    websiteUrl: "add website URL here //Required field for configurable tabs on Mobile Clients",
    removeUrl: "add removal page URL here"
});
```

## <a name="mobile-clients"></a><span data-ttu-id="6be13-158">Mobile Clients</span><span class="sxs-lookup"><span data-stu-id="6be13-158">Mobile clients</span></span>

<span data-ttu-id="6be13-159">Wenn Sie den Kanal oder die Gruppenregisterkarte auf der Teams mobilen Clients anzeigen möchten, muss die `setSettings()` Konfiguration einen Wert für die Eigenschaft `websiteUrl` haben.</span><span class="sxs-lookup"><span data-stu-id="6be13-159">If you choose to have your channel or group tab appear on the Teams mobile clients, the `setSettings()` configuration must have a value for the `websiteUrl` property.</span></span> <span data-ttu-id="6be13-160">Weitere Informationen finden Sie unter [Anleitung zu Registerkarten auf mobilen](~/tabs/design/tabs-mobile.md).</span><span class="sxs-lookup"><span data-stu-id="6be13-160">For more information, see [guidance for tabs on mobile](~/tabs/design/tabs-mobile.md).</span></span>
