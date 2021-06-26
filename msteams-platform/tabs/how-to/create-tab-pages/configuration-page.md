---
title: Erstellen einer Konfigurationsseite
author: surbhigupta
description: So erstellen Sie eine Konfigurationsseite
keywords: Konfigurierbarer Gruppenkanal für Teams-Registerkarten
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 00aac64465dcc0c59a0146ea37f863f16c976a52
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140222"
---
# <a name="create-a-configuration-page"></a><span data-ttu-id="e1fc6-104">Erstellen einer Konfigurationsseite</span><span class="sxs-lookup"><span data-stu-id="e1fc6-104">Create a configuration page</span></span>

<span data-ttu-id="e1fc6-105">Eine Konfigurationsseite ist ein spezieller [Inhaltsseitentyp.](content-page.md)</span><span class="sxs-lookup"><span data-stu-id="e1fc6-105">A configuration page is a special type of [content page](content-page.md).</span></span> <span data-ttu-id="e1fc6-106">Die Benutzer konfigurieren einige Aspekte der Microsoft Teams App mithilfe der Konfigurationsseite und verwenden diese Konfiguration als Teil der folgenden Komponenten:</span><span class="sxs-lookup"><span data-stu-id="e1fc6-106">The users configure some aspects of the Microsoft Teams app using the configuration page and use that configuration as part of the following:</span></span>

* <span data-ttu-id="e1fc6-107">Registerkarte "Kanal- oder Gruppenchat": Sammeln sie Informationen von den Benutzern, und legen Sie `contentUrl` die anzuzeigende Inhaltsseite fest.</span><span class="sxs-lookup"><span data-stu-id="e1fc6-107">A channel or group chat tab: Collect information from the users and set the `contentUrl` of the content page to be displayed.</span></span>
* <span data-ttu-id="e1fc6-108">Eine [Messaging-Erweiterung](~/messaging-extensions/what-are-messaging-extensions.md).</span><span class="sxs-lookup"><span data-stu-id="e1fc6-108">A [messaging extension](~/messaging-extensions/what-are-messaging-extensions.md).</span></span>
* <span data-ttu-id="e1fc6-109">Ein [Office 365 Connector](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md).</span><span class="sxs-lookup"><span data-stu-id="e1fc6-109">An [Office 365 Connector](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md).</span></span>

## <a name="configure-a-channel-or-group-chat-tab"></a><span data-ttu-id="e1fc6-110">Konfigurieren einer Kanal- oder Gruppenchatregisterkarte</span><span class="sxs-lookup"><span data-stu-id="e1fc6-110">Configure a channel or group chat tab</span></span>

<span data-ttu-id="e1fc6-111">Die Anwendung muss auf das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) verweisen und `microsoft.initialize()` aufrufen.</span><span class="sxs-lookup"><span data-stu-id="e1fc6-111">The application must reference the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) and call `microsoft.initialize()`.</span></span> <span data-ttu-id="e1fc6-112">Die verwendeten URLs müssen https-Endpunkte gesichert und in der Cloud verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="e1fc6-112">The URLs used must be secured HTTPS endpoints and available from the cloud.</span></span>

### <a name="example"></a><span data-ttu-id="e1fc6-113">Beispiel</span><span class="sxs-lookup"><span data-stu-id="e1fc6-113">Example</span></span>

<span data-ttu-id="e1fc6-114">Ein Beispiel für eine Konfigurationsseite ist in der folgenden Abbildung dargestellt:</span><span class="sxs-lookup"><span data-stu-id="e1fc6-114">An example of a configuration page is shown in the following image:</span></span>

<img src="~/assets/images/tab-images/configuration-page.png" alt="Configuration page" width="400"/>

<span data-ttu-id="e1fc6-115">Der folgende Code ist ein Beispiel für den entsprechenden Code für die Konfigurationsseite:</span><span class="sxs-lookup"><span data-stu-id="e1fc6-115">The following code is an example of corresponding code for the configuration page:</span></span>

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

<span data-ttu-id="e1fc6-116">Wählen Sie auf der Konfigurationsseite entweder die Schaltfläche **"Grau"** oder **"Rot auswählen"** aus, um den Registerkarteninhalt mit einem grauen oder roten Symbol anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="e1fc6-116">Choose either **Select Gray** or **Select Red** button in the configuration page, to display the tab content with a gray or red icon.</span></span>

<span data-ttu-id="e1fc6-117">In der folgenden Abbildung wird der Registerkarteninhalt mit einem grauen Symbol angezeigt:</span><span class="sxs-lookup"><span data-stu-id="e1fc6-117">The following image displays the tab content with a gray icon:</span></span>

<img src="~/assets/images/tab-images/configure-tab-with-gray.png" alt="Configure tab with select gray" width="400"/>

<span data-ttu-id="e1fc6-118">In der folgenden Abbildung wird der Registerkarteninhalt mit einem roten Symbol angezeigt:</span><span class="sxs-lookup"><span data-stu-id="e1fc6-118">The following image displays the tab content with a red icon:</span></span>

<img src="~/assets/images/tab-images/configure-tab-with-red.png" alt="Configure tab with select red" width="400"/>

<span data-ttu-id="e1fc6-119">Wenn Sie die entsprechende Schaltfläche auswählen, wird entweder `saveGray()` oder `saveRed()` ausgelöst, und Folgendes wird aufgerufen:</span><span class="sxs-lookup"><span data-stu-id="e1fc6-119">Choosing the appropriate button triggers either `saveGray()` or `saveRed()`, and invokes the following:</span></span>

* <span data-ttu-id="e1fc6-120">Auf `settings.setValidityState(true)` "true" festgelegt.</span><span class="sxs-lookup"><span data-stu-id="e1fc6-120">Set `settings.setValidityState(true)` to true.</span></span> 
* <span data-ttu-id="e1fc6-121">Der `microsoftTeams.settings.registerOnSaveHandler()` Ereignishandler wird ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="e1fc6-121">The `microsoftTeams.settings.registerOnSaveHandler()` event handler is triggered.</span></span>
* <span data-ttu-id="e1fc6-122">**Das Speichern** auf der Konfigurationsseite der App ist aktiviert.</span><span class="sxs-lookup"><span data-stu-id="e1fc6-122">**Save** on the app's configuration page, is enabled.</span></span>

<span data-ttu-id="e1fc6-123">Der Code der Konfigurationsseite informiert Teams, dass die Konfigurationsanforderungen erfüllt sind und die Installation fortgesetzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="e1fc6-123">The configuration page code informs Teams that the configuration requirements are satisfied and the installation can proceed.</span></span> <span data-ttu-id="e1fc6-124">Wenn der Benutzer **"Speichern"** auswählt, werden die Parameter `settings.setSettings()` festgelegt, wie von der `Settings` Benutzeroberfläche definiert.</span><span class="sxs-lookup"><span data-stu-id="e1fc6-124">When the user selects **Save**, the parameters of `settings.setSettings()` are set, as defined by the `Settings` interface.</span></span> <span data-ttu-id="e1fc6-125">Weitere Informationen finden Sie unter ["Einstellungsschnittstelle".](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="e1fc6-125">For more information, see [settings interface](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true).</span></span> <span data-ttu-id="e1fc6-126">`saveEvent.notifySuccess()` wird aufgerufen, um anzugeben, dass die Inhalts-URL erfolgreich aufgelöst wurde.</span><span class="sxs-lookup"><span data-stu-id="e1fc6-126">`saveEvent.notifySuccess()` is called to indicate that the content URL has successfully resolved.</span></span>

>[!NOTE]
>
>* <span data-ttu-id="e1fc6-127">Wenn Sie einen Speicherhandler mithilfe `microsoftTeams.settings.registerOnSaveHandler()` registrieren, muss der Rückruf aufgerufen `saveEvent.notifySuccess()` werden oder das Ergebnis der Konfiguration `saveEvent.notifyFailure()` angeben.</span><span class="sxs-lookup"><span data-stu-id="e1fc6-127">If you register a save handler using `microsoftTeams.settings.registerOnSaveHandler()`, the callback must invoke `saveEvent.notifySuccess()` or `saveEvent.notifyFailure()` to indicate the outcome of the configuration.</span></span>
>* <span data-ttu-id="e1fc6-128">Wenn Sie keinen Speicherhandler registrieren, wird der `saveEvent.notifySuccess()` Aufruf automatisch ausgeführt, wenn der Benutzer **"Speichern"** auswählt.</span><span class="sxs-lookup"><span data-stu-id="e1fc6-128">If you do not register a save handler, the `saveEvent.notifySuccess()` call is made automatically when the user selects **Save**.</span></span>

### <a name="get-context-data-for-your-tab-settings"></a><span data-ttu-id="e1fc6-129">Abrufen von Kontextdaten für Ihre Registerkarteneinstellungen</span><span class="sxs-lookup"><span data-stu-id="e1fc6-129">Get context data for your tab settings</span></span>

<span data-ttu-id="e1fc6-130">Ihre Registerkarte erfordert Kontextinformationen, um relevante Inhalte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="e1fc6-130">Your tab requires contextual information to display relevant content.</span></span> <span data-ttu-id="e1fc6-131">Kontextbezogene Informationen verbessern die Darstellung Ihrer Registerkarte weiter, indem sie eine angepasstere Benutzeroberfläche bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="e1fc6-131">Contextual information further enhances your tab's appeal by providing a more customized user experience.</span></span>

<span data-ttu-id="e1fc6-132">Weitere Informationen zu den Eigenschaften, die für die Registerkartenkonfiguration verwendet werden, finden Sie unter [der Kontextschnittstelle.](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="e1fc6-132">For more information on the properties used for tab configuration, see [context interface](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true).</span></span> <span data-ttu-id="e1fc6-133">Erfassen Sie die Werte von Kontextdatenvariablen auf zwei Arten:</span><span class="sxs-lookup"><span data-stu-id="e1fc6-133">Collect the values of context data variables in the following two ways:</span></span>

* <span data-ttu-id="e1fc6-134">Fügen Sie PLATZHALTER FÜR URL-Abfragezeichenfolgen in das Manifest `configurationURL` ein.</span><span class="sxs-lookup"><span data-stu-id="e1fc6-134">Insert URL query string placeholders in your manifest's `configurationURL`.</span></span>

* <span data-ttu-id="e1fc6-135">Verwenden Sie die [Teams SDK-Methode.](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) `microsoftTeams.getContext((context) =>{})`</span><span class="sxs-lookup"><span data-stu-id="e1fc6-135">Use the [Teams SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) `microsoftTeams.getContext((context) =>{})` method.</span></span>

#### <a name="insert-placeholders-in-the-configurationurl"></a><span data-ttu-id="e1fc6-136">Einfügen von Platzhaltern in die `configurationUrl`</span><span class="sxs-lookup"><span data-stu-id="e1fc6-136">Insert placeholders in the `configurationUrl`</span></span>

<span data-ttu-id="e1fc6-137">Fügen Sie Ihrer Basis Platzhalter für die Kontextschnittstelle `configurationUrl` hinzu.</span><span class="sxs-lookup"><span data-stu-id="e1fc6-137">Add context interface placeholders to your base `configurationUrl`.</span></span> <span data-ttu-id="e1fc6-138">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="e1fc6-138">For example:</span></span>

##### <a name="base-url"></a><span data-ttu-id="e1fc6-139">Basis-URL</span><span class="sxs-lookup"><span data-stu-id="e1fc6-139">Base URL</span></span>

```json
...
"configurationUrl": "https://yourWebsite/config",
...
```

#### <a name="base-url-with-query-strings"></a><span data-ttu-id="e1fc6-140">Basis-URL mit Abfragezeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="e1fc6-140">Base URL with query strings</span></span>

```json
...
"configurationUrl": "https://yourWebsite/config?team={teamId}&channel={channelId}&{locale}"
...
```

<span data-ttu-id="e1fc6-141">Nachdem die Seite hochgeladen wurde, aktualisiert Teams die Platzhalter der Abfragezeichenfolge mit relevanten Werten.</span><span class="sxs-lookup"><span data-stu-id="e1fc6-141">After your page uploads, Teams updates the query string placeholders with relevant values.</span></span> <span data-ttu-id="e1fc6-142">Schließen Sie Logik in die Konfigurationsseite ein, um diese Werte abzurufen und zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="e1fc6-142">Include logic in the configuration page to retrieve and use those values.</span></span> <span data-ttu-id="e1fc6-143">Weitere Informationen zum Arbeiten mit URL-Abfragezeichenfolgen finden Sie unter [URLSearchParams](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) in MDN Web Docs. Das folgende Codebeispiel bietet die Möglichkeit, einen Wert aus der Eigenschaft zu `configurationUrl` extrahieren:</span><span class="sxs-lookup"><span data-stu-id="e1fc6-143">For more information on working with URL query strings, see [URLSearchParams](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) in MDN Web Docs. The following code example provides the way to extract a value from the `configurationUrl` property:</span></span>

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

### <a name="use-the-getcontext-function-to-retrieve-context"></a><span data-ttu-id="e1fc6-144">Verwenden der `getContext()` Funktion zum Abrufen des Kontexts</span><span class="sxs-lookup"><span data-stu-id="e1fc6-144">Use the `getContext()` function to retrieve context</span></span>

<span data-ttu-id="e1fc6-145">Die `microsoftTeams.getContext((context) => {})` Funktion ruft die [Kontextschnittstelle](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true) ab, wenn sie aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="e1fc6-145">The `microsoftTeams.getContext((context) => {})` function retrieves the [context interface](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true) when invoked.</span></span>

<span data-ttu-id="e1fc6-146">Der folgende Code enthält ein Beispiel für das Hinzufügen dieser Funktion zur Konfigurationsseite zum Abrufen von Kontextwerten:</span><span class="sxs-lookup"><span data-stu-id="e1fc6-146">The following code provides an example of adding this function to the configuration page to retrieve context values:</span></span>

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

## <a name="context-and-authentication"></a><span data-ttu-id="e1fc6-147">Kontext und Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="e1fc6-147">Context and authentication</span></span>

<span data-ttu-id="e1fc6-148">Authentifizieren Sie sich, bevor ein Benutzer Ihre App konfigurieren kann.</span><span class="sxs-lookup"><span data-stu-id="e1fc6-148">Authenticate before allowing a user to configure your app.</span></span> <span data-ttu-id="e1fc6-149">Andernfalls können Ihre Inhalte Quellen mit ihren Authentifizierungsprotokollen enthalten.</span><span class="sxs-lookup"><span data-stu-id="e1fc6-149">Otherwise, your content might include sources that have their authentication protocols.</span></span> <span data-ttu-id="e1fc6-150">Weitere Informationen finden Sie unter ["Authentifizieren eines Benutzers in einer Microsoft Teams Registerkarte".](~/tabs/how-to/authentication/auth-flow-tab.md) Verwenden Sie Kontextinformationen, um die URLs für Authentifizierungsanforderungen und Autorisierungsseiten zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="e1fc6-150">For more information, see [authenticate a user in a Microsoft Teams tab](~/tabs/how-to/authentication/auth-flow-tab.md). Use context information to construct the authentication requests and authorization page URLs.</span></span> <span data-ttu-id="e1fc6-151">Stellen Sie sicher, dass alle Domänen, die auf Ihren Registerkartenseiten verwendet werden, im `manifest.json` `validDomains` Und-Array aufgeführt sind.</span><span class="sxs-lookup"><span data-stu-id="e1fc6-151">Ensure that all domains used in your tab pages are listed in the `manifest.json` and `validDomains` array.</span></span>

## <a name="modify-or-remove-a-tab"></a><span data-ttu-id="e1fc6-152">Ändern oder Entfernen einer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="e1fc6-152">Modify or remove a tab</span></span>

<span data-ttu-id="e1fc6-153">Legen Sie die Eigenschaft Ihres Manifests `canUpdateConfiguration` auf , die es benutzern `true` ermöglicht, einen Kanal oder eine Gruppenregisterkarte zu ändern, neu zu konfigurieren oder umzubenennen. Geben Sie außerdem an, was mit dem Inhalt geschieht, wenn eine Registerkarte entfernt wird, indem Sie eine Seite mit Den entfernten Optionen in die App einschließen und einen Wert für die `removeUrl` Eigenschaft in der Konfiguration  `setSettings()` festlegen.</span><span class="sxs-lookup"><span data-stu-id="e1fc6-153">Set your manifest's `canUpdateConfiguration` property to `true`, that enables the users to modify, reconfigure, or rename a channel or group tab. Also, indicate what happens to the content when a tab is removed, by including a removal options page in the app and setting a value for the `removeUrl` property in the  `setSettings()` configuration.</span></span> <span data-ttu-id="e1fc6-154">Der Benutzer kann persönliche Registerkarten deinstallieren, aber nicht ändern.</span><span class="sxs-lookup"><span data-stu-id="e1fc6-154">The user can uninstall personal tabs but cannot modify them.</span></span> <span data-ttu-id="e1fc6-155">Weitere Informationen finden Sie unter [Erstellen einer Seite zum Entfernen ihrer Registerkarte.](~/tabs/how-to/create-tab-pages/removal-page.md)</span><span class="sxs-lookup"><span data-stu-id="e1fc6-155">For more information, see [create a removal page for your tab](~/tabs/how-to/create-tab-pages/removal-page.md).</span></span>

<span data-ttu-id="e1fc6-156">`setSettings()`Microsoft Teams Konfigurationsseite für die Entfernungsseite:</span><span class="sxs-lookup"><span data-stu-id="e1fc6-156">Microsoft Teams `setSettings()` configuration for removal page:</span></span>

```javascript
microsoftTeams.settings.setSettings({
    contentUrl: "add content page URL here",
    entityId: "add unique name here",
    suggestedDisplayName: "add name to display on tab here",
    websiteUrl: "add website URL here //Required field for configurable tabs on Mobile Clients",
    removeUrl: "add removal page URL here"
});
```

## <a name="mobile-clients"></a><span data-ttu-id="e1fc6-157">Mobile Clients</span><span class="sxs-lookup"><span data-stu-id="e1fc6-157">Mobile clients</span></span>

<span data-ttu-id="e1fc6-158">Wenn Ihre Kanal- oder Gruppenregisterkarte auf den Teams mobilen Clients angezeigt werden soll, muss die `setSettings()` Konfiguration einen Wert für `websiteUrl` aufweisen.</span><span class="sxs-lookup"><span data-stu-id="e1fc6-158">If you choose to have your channel or group tab appear on the Teams mobile clients, the `setSettings()` configuration must have a value for `websiteUrl`.</span></span> <span data-ttu-id="e1fc6-159">Weitere Informationen finden Sie unter [Anleitungen für Registerkarten auf mobilen Geräten.](~/tabs/design/tabs-mobile.md)</span><span class="sxs-lookup"><span data-stu-id="e1fc6-159">For more information, see [guidance for tabs on mobile](~/tabs/design/tabs-mobile.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e1fc6-160">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e1fc6-160">See also</span></span>

* [<span data-ttu-id="e1fc6-161">registerkarten Teams</span><span class="sxs-lookup"><span data-stu-id="e1fc6-161">Teams tabs</span></span>](~/tabs/what-are-tabs.md)
* [<span data-ttu-id="e1fc6-162">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="e1fc6-162">Prerequisites</span></span>](~/tabs/how-to/tab-requirements.md)
* [<span data-ttu-id="e1fc6-163">Erstellen einer persönlichen Registerkarte</span><span class="sxs-lookup"><span data-stu-id="e1fc6-163">Create a personal tab</span></span>](~/tabs/how-to/create-personal-tab.md)
* [<span data-ttu-id="e1fc6-164">Erstellen einer Kanal- oder Gruppenregisterkarte</span><span class="sxs-lookup"><span data-stu-id="e1fc6-164">Create a channel or group tab</span></span>](~/tabs/how-to/create-channel-group-tab.md)
* [<span data-ttu-id="e1fc6-165">Erstellen einer Inhaltsseite</span><span class="sxs-lookup"><span data-stu-id="e1fc6-165">Create a content page</span></span>](~/tabs/how-to/create-tab-pages/content-page.md)
* [<span data-ttu-id="e1fc6-166">Registerkarten auf mobilen Geräten</span><span class="sxs-lookup"><span data-stu-id="e1fc6-166">Tabs on mobile</span></span>](~/tabs/design/tabs-mobile.md)
* [<span data-ttu-id="e1fc6-167">Kontext für Ihre Registerkarte erhalten</span><span class="sxs-lookup"><span data-stu-id="e1fc6-167">Get context for your tab</span></span>](~/tabs/how-to/access-teams-context.md)
* [<span data-ttu-id="e1fc6-168">Erstellen von Registerkarten mit adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="e1fc6-168">Build tabs with Adaptive Cards</span></span>](~/tabs/how-to/build-adaptive-card-tabs.md)
* [<span data-ttu-id="e1fc6-169">Aufgeklappte Registerkartenverknüpfung und Phasenansicht</span><span class="sxs-lookup"><span data-stu-id="e1fc6-169">Tabs link unfurling and Stage View</span></span>](~/tabs/tabs-link-unfurling.md)
* [<span data-ttu-id="e1fc6-170">Registerkarten für Unterhaltungen erstellen</span><span class="sxs-lookup"><span data-stu-id="e1fc6-170">Create conversational tabs</span></span>](~/tabs/how-to/conversational-tabs.md)
* [<span data-ttu-id="e1fc6-171">Änderungen am Registerkartenrand</span><span class="sxs-lookup"><span data-stu-id="e1fc6-171">Tab margin changes</span></span>](~/resources/removing-tab-margins.md)

## <a name="next-step"></a><span data-ttu-id="e1fc6-172">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="e1fc6-172">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e1fc6-173">Erstellen einer Seite zum Entfernen ihrer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="e1fc6-173">Create a removal page for your tab</span></span>](~/tabs/how-to/create-tab-pages/removal-page.md)
