---
title: Erstellen einer Konfigurationsseite
author: laujan
description: ''
keywords: Teams-Registerkartengruppe Kanal konfigurierbar
ms.topic: conceptualF
ms.author: laujan
ms.openlocfilehash: c7b6b636a342c650667a1131e7899908744beedf
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674086"
---
# <a name="create-a-configuration-page"></a><span data-ttu-id="4ef60-103">Erstellen einer Konfigurationsseite</span><span class="sxs-lookup"><span data-stu-id="4ef60-103">Create a configuration page</span></span>

<span data-ttu-id="4ef60-104">Bei einer Konfigurationsseite handelt es sich um einen speziellen Inhaltstyp der [Inhaltsseite](content-page.md) , mit dem Ihre Benutzer einen Aspekt Ihrer Teams-App konfigurieren können.</span><span class="sxs-lookup"><span data-stu-id="4ef60-104">A configuration page is a special type of [content page](content-page.md) that allows your users to configure some aspect of your Teams app.</span></span> <span data-ttu-id="4ef60-105">Diese werden normalerweise als Bestandteil von verwendet:</span><span class="sxs-lookup"><span data-stu-id="4ef60-105">Typically these are used as part of:</span></span>

* <span data-ttu-id="4ef60-106">Eine Kanal-oder Gruppenchat-Registerkarte – auf der Konfigurationsseite können Sie Informationen von Ihren Benutzern sammeln `contentUrl` und die anzuzeigende Inhaltsseite festlegen.</span><span class="sxs-lookup"><span data-stu-id="4ef60-106">A channel or group chat tab - The configuration page allows you to collect information from your users and set the `contentUrl` of the content page to display.</span></span>
* <span data-ttu-id="4ef60-107">Eine [Messaging Erweiterung](~/messaging-extensions/what-are-messaging-extensions.md)</span><span class="sxs-lookup"><span data-stu-id="4ef60-107">A [messaging extension](~/messaging-extensions/what-are-messaging-extensions.md)</span></span>
* <span data-ttu-id="4ef60-108">Ein [Office 365 Verbinder](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md)</span><span class="sxs-lookup"><span data-stu-id="4ef60-108">A [Office 365 Connector](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md)</span></span>

## <a name="configuring-a-channel-or-group-chat-tab"></a><span data-ttu-id="4ef60-109">Konfigurieren einer Kanal-oder Gruppenchat-Registerkarte</span><span class="sxs-lookup"><span data-stu-id="4ef60-109">Configuring a channel or group chat tab</span></span>

<span data-ttu-id="4ef60-110">Auf einer Konfigurationsseite wird die Inhaltsseite darüber informiert, wie Sie gerendert werden soll.</span><span class="sxs-lookup"><span data-stu-id="4ef60-110">A configuration page informs the content page how it should render.</span></span> <span data-ttu-id="4ef60-111">Ihre Anwendung muss auf das [Microsoft Teams JavaScript Client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest) verweisen und `microsoft.initialize()`den Anruf tätigen.</span><span class="sxs-lookup"><span data-stu-id="4ef60-111">Your application must reference the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest) and call `microsoft.initialize()`.</span></span> <span data-ttu-id="4ef60-112">Außerdem müssen Ihre URLs sichere HTTPS-Endpunkte und in der Cloud verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="4ef60-112">Additionally, your URLs must be secure HTTPS endpoints and available from the cloud.</span></span> <span data-ttu-id="4ef60-113">Unten sehen Sie ein Beispiel für eine Konfigurationsseite.</span><span class="sxs-lookup"><span data-stu-id="4ef60-113">Below is a configuration page example.</span></span>

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

<span data-ttu-id="4ef60-114">Hier werden dem Benutzer zwei Optionsschaltflächen angezeigt, **Wählen Sie grau** aus, oder **Wählen Sie Rot aus** , um den Registerkarteninhalt mit einem roten oder grauen Symbol anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="4ef60-114">Here, the user is presented with two option buttons, **Select Gray** or **Select Red** to display the tab content with either a red or gray icon.</span></span> <span data-ttu-id="4ef60-115">Die Auswahl der relativen Schalt `saveGray()` Fläche `saveRed()` wird ausgelöst oder ruft Folgendes auf:</span><span class="sxs-lookup"><span data-stu-id="4ef60-115">Choosing the relative button fires `saveGray()` or `saveRed()` and invokes the following:</span></span>

1. <span data-ttu-id="4ef60-116">Der `settings.setValidityState(true)` ist auf true festgelegt.</span><span class="sxs-lookup"><span data-stu-id="4ef60-116">The `settings.setValidityState(true)` is set to true.</span></span>
1. <span data-ttu-id="4ef60-117">Der `microsoftTeams.settings.registerOnSaveHandler()` Ereignishandler wird ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="4ef60-117">The `microsoftTeams.settings.registerOnSaveHandler()` event handler is triggered.</span></span>
1. <span data-ttu-id="4ef60-118">Die Schaltfläche **Speichern** auf der Konfigurationsseite der APP, die in Teams hochgeladen wurde, ist aktiviert.</span><span class="sxs-lookup"><span data-stu-id="4ef60-118">The **Save** button on the app's configuration page, uploaded in Teams, is enabled.</span></span>

<span data-ttu-id="4ef60-119">Mit diesem Code können Teams wissen, dass die Konfigurationsanforderungen erfüllt wurden und die Installation fortgesetzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="4ef60-119">This code lets Teams know that the configuration requirements have been satisfied and the installation can proceed.</span></span> <span data-ttu-id="4ef60-120">Bei **Save**werden die Parameter von `settings.setSettings()` festgelegt, wie durch die `Settings` Schnittstelle für die aktuelle Instanz definiert (siehe [Einstellungen-Schnittstelle](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest) ).</span><span class="sxs-lookup"><span data-stu-id="4ef60-120">On **Save**, the parameters of `settings.setSettings()` are set, as defined by the `Settings` interface, for the current instance (See [Settings interface](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest) ).</span></span> <span data-ttu-id="4ef60-121">Schließlich `saveEvent.notifySuccess()` wird aufgerufen, um anzugeben, dass die Inhalts-URL erfolgreich aufgelöst wurde.</span><span class="sxs-lookup"><span data-stu-id="4ef60-121">Finally, `saveEvent.notifySuccess()` is called to indicate that the content URL has successfully resolved.</span></span>

>[!NOTE]
>
>* <span data-ttu-id="4ef60-122">Wenn ein Speicher Handler mit `microsoftTeams.settings.registerOnSaveHandler()`registriert wurde, muss der Rückruf aufrufen `saveEvent.notifySuccess()` oder `saveEvent.notifyFailure()` das Ergebnis der Konfiguration angeben.</span><span class="sxs-lookup"><span data-stu-id="4ef60-122">If a save handler was registered using `microsoftTeams.settings.registerOnSaveHandler()`, the callback must invoke `saveEvent.notifySuccess()` or `saveEvent.notifyFailure()` to indicate the outcome of the configuration.</span></span>
>* <span data-ttu-id="4ef60-123">Wenn kein Speicher Handler registriert wurde, wird `saveEvent.notifySuccess()` der Anruf automatisch sofort ausgeführt, sobald der Benutzer die Schaltfläche **Speichern** auswählt.</span><span class="sxs-lookup"><span data-stu-id="4ef60-123">If no save handler was registered, the `saveEvent.notifySuccess()` call is automatically made immediately upon the user selecting the **Save** button.</span></span>

### <a name="get-context-data-for-your-tab-settings"></a><span data-ttu-id="4ef60-124">Abrufen von Kontextdaten für die Registerkarteneinstellungen</span><span class="sxs-lookup"><span data-stu-id="4ef60-124">Get context data for your tab settings</span></span>

<span data-ttu-id="4ef60-125">Für Ihre Registerkarte sind möglicherweise Kontextinformationen erforderlich, um relevante Inhalte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="4ef60-125">Your tab might require contextual information to display relevant content.</span></span> <span data-ttu-id="4ef60-126">Kontextinformationen können die Attraktivität Ihrer Registerkarte weiter verbessern, indem Sie eine Benutzerfreundlichkeit bieten, die Ihnen angepasst ist.</span><span class="sxs-lookup"><span data-stu-id="4ef60-126">Contextual information can further enhance your tab's appeal by providing a more customized user experience.</span></span>

<span data-ttu-id="4ef60-127">Die [Kontext Schnittstelle](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest) für Teams definiert die Eigenschaften, die für Ihre Registerkartenkonfiguration verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="4ef60-127">The Teams [Context interface](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest) defines the properties that can be used for your tab configuration.</span></span> <span data-ttu-id="4ef60-128">Sie können die Werte von Kontextdaten Variablen auf zwei Arten erfassen:</span><span class="sxs-lookup"><span data-stu-id="4ef60-128">You can collect the values of context data variables in two ways:</span></span>

1. <span data-ttu-id="4ef60-129">Fügen Sie Platzhalter für URL- `configurationURL`Abfragezeichenfolgen in das Manifest ein.</span><span class="sxs-lookup"><span data-stu-id="4ef60-129">Insert URL query string placeholders in your manifest's `configurationURL`.</span></span>

1. <span data-ttu-id="4ef60-130">Verwenden Sie die [Teams-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest) `microsoftTeams.getContext((context) =>{}` -Methode.</span><span class="sxs-lookup"><span data-stu-id="4ef60-130">Use the [Teams SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest) `microsoftTeams.getContext((context) =>{}` method.</span></span>

#### <a name="insert-placeholders-in-the-configurationurl"></a><span data-ttu-id="4ef60-131">Einfügen von Platzhaltern im`configurationURL`</span><span class="sxs-lookup"><span data-stu-id="4ef60-131">Insert placeholders in the `configurationURL`</span></span>

<span data-ttu-id="4ef60-132">Platzhalter für die Kontext Schnittstelle können ihrer Basis `configurationUrl`hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="4ef60-132">Context interface placeholders can be added to your base `configurationUrl`.</span></span> <span data-ttu-id="4ef60-133">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="4ef60-133">For example:</span></span>

##### <a name="base-url"></a><span data-ttu-id="4ef60-134">Basis-URL</span><span class="sxs-lookup"><span data-stu-id="4ef60-134">Base Url</span></span>

```json
...
"configurationUrl": "https://yourWebsite/config",
...
```

#### <a name="base-url-with-query-strings"></a><span data-ttu-id="4ef60-135">Basis-URL mit Abfragezeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="4ef60-135">Base URL with query strings</span></span>

```json
...
"configurationUrl": "https://yourWebsite/config?team={teamId}&channel={channelId}&{locale}"
...
```

<span data-ttu-id="4ef60-136">Nachdem die Seite hochgeladen wurde, werden die Platzhalter für die Abfragezeichenfolge von Microsoft Teams mit den entsprechenden Werten aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="4ef60-136">After your page has uploaded, the query string placeholders will be updated by Teams with the relevant values.</span></span> <span data-ttu-id="4ef60-137">Sie können Logik in Ihre Konfigurationsseite einbeziehen, um diese Werte abzurufen und zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="4ef60-137">You can include logic in your configuration page to retrieve and use those values.</span></span> <span data-ttu-id="4ef60-138">Weitere Informationen zum Arbeiten mit URL-Abfragezeichenfolgen finden Sie unter [URLSearchParams](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) in MDN-Webdocs. Nachfolgend finden Sie ein Beispiel zum Extrahieren eines Werts aus der obigen `configurationURL` Eigenschaft:</span><span class="sxs-lookup"><span data-stu-id="4ef60-138">For more information on working with URL query strings see [URLSearchParams](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) in MDN web docs. Here is an example of how to extract a value from the above `configurationURL` property:</span></span>

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

### <a name="use-the-getcontext-function-to-retrieve-context"></a><span data-ttu-id="4ef60-139">Verwenden der `getContext()` -Funktion zum Abrufen des Kontexts</span><span class="sxs-lookup"><span data-stu-id="4ef60-139">Use the `getContext()` function to retrieve context</span></span>

<span data-ttu-id="4ef60-140">Wenn die `microsoftTeams.getContext((context) => {})` Funktion aufgerufen wird, ruft Sie die [Kontext Schnittstelle](/javascript/api/@microsoft/teams-js//microsoftteams.context?view=msteams-client-js-latest)ab.</span><span class="sxs-lookup"><span data-stu-id="4ef60-140">When invoked, the `microsoftTeams.getContext((context) => {})` function retrieves the [Context interface](/javascript/api/@microsoft/teams-js//microsoftteams.context?view=msteams-client-js-latest).</span></span> <span data-ttu-id="4ef60-141">Sie können diese Funktion zur Konfigurationsseite hinzufügen, um Kontext Werte abzurufen:</span><span class="sxs-lookup"><span data-stu-id="4ef60-141">You can add this function to your configuration page to retrieve context values:</span></span>

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

## <a name="context-and-authentication"></a><span data-ttu-id="4ef60-142">Kontext und Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="4ef60-142">Context and Authentication</span></span>

<span data-ttu-id="4ef60-143">Möglicherweise benötigen Sie eine Authentifizierung, bevor Sie einem Benutzer die Konfiguration Ihrer APP erlauben, oder Ihre Inhalte können Quellen enthalten, die über eigene Authentifizierungsprotokolle verfügen.</span><span class="sxs-lookup"><span data-stu-id="4ef60-143">You might require authentication before allowing a user to configure your app or your content might include sources that have their own authentication protocols.</span></span> <span data-ttu-id="4ef60-144">Informationen zum Erstellen von Authentifizierungsanforderungen und Autorisierungs Seiten-URLs finden Sie unter [Authentifizieren eines Benutzers in einer Microsoft Teams-Registerkarte](~/tabs/how-to/authentication/auth-flow-tab.md) Kontextinformationen können verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="4ef60-144">See [Authenticate a user in a Microsoft Teams tab](~/tabs/how-to/authentication/auth-flow-tab.md) Context information can be used to help construct authentication requests and authorization page URLs.</span></span>
<span data-ttu-id="4ef60-145">Stellen Sie sicher, dass alle auf den Registerkartenseiten verwendeten Domänen im `manifest.json` `validDomains` Array aufgelistet sind.</span><span class="sxs-lookup"><span data-stu-id="4ef60-145">Make sure that all domains used in your tab pages are listed in the `manifest.json` `validDomains` array.</span></span>

## <a name="modify-or-remove-a-tab"></a><span data-ttu-id="4ef60-146">Ändern oder Entfernen einer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="4ef60-146">Modify or remove a tab</span></span>

<span data-ttu-id="4ef60-147">Unterstützte Entfernungsoptionen können die Benutzerfreundlichkeit weiter verfeinern.</span><span class="sxs-lookup"><span data-stu-id="4ef60-147">Supported removal options can further refine the user experience.</span></span> <span data-ttu-id="4ef60-148">Sie können Benutzern das ändern, konfigurieren oder Umbenennen einer Gruppe/Kanal-Registerkarte ermöglichen, indem Sie die `canUpdateConfiguration` Eigenschaft des Manifests auf `true`festlegen.</span><span class="sxs-lookup"><span data-stu-id="4ef60-148">You can enable users to modify, reconfigure, or rename a group/channel tab by setting your manifest's `canUpdateConfiguration` property to `true`.</span></span>  <span data-ttu-id="4ef60-149">Darüber hinaus können Sie festlegen, was mit dem Inhalt geschieht, wenn eine Registerkarte entfernt wird, indem Sie eine Seite mit den Entfernungsoptionen in Ihrer APP `removeUrl` hinzufügen und `setSettings()` einen Wert für die Eigenschaft in der Konfiguration festlegen (siehe unten).</span><span class="sxs-lookup"><span data-stu-id="4ef60-149">In addition, you can designate what happens to the content when a tab is removed by including a removal options page in your app and setting a value for the `removeUrl` property in the  `setSettings()` configuration (see below).</span></span> <span data-ttu-id="4ef60-150">Persönliche Registerkarten können nicht geändert, aber vom Benutzer deinstalliert werden.</span><span class="sxs-lookup"><span data-stu-id="4ef60-150">Personal tabs can't be modified but can be uninstalled by the user.</span></span> <span data-ttu-id="4ef60-151">Weitere Informationen finden Sie unter [Erstellen einer Entfernungs Seite für die Registerkarte](~/tabs/how-to/create-tab-pages/removal-page.md).</span><span class="sxs-lookup"><span data-stu-id="4ef60-151">For more information, see [Create a removal page for your tab](~/tabs/how-to/create-tab-pages/removal-page.md).</span></span>

## <a name="mobile-clients"></a><span data-ttu-id="4ef60-152">Mobile Clients</span><span class="sxs-lookup"><span data-stu-id="4ef60-152">Mobile clients</span></span>

<span data-ttu-id="4ef60-153">Wenn die Registerkarte Kanal/Gruppe auf mobilen Teams-Clients angezeigt werden soll, muss `setSettings()` die Konfiguration über einen Wert für die `websiteUrl` Eigenschaft verfügen (siehe unten).</span><span class="sxs-lookup"><span data-stu-id="4ef60-153">If you choose to have your channel/group tab appear on Teams mobile clients, the `setSettings()` configuration must have a value for the `websiteUrl` property (see below).</span></span> <span data-ttu-id="4ef60-154">Die vollständige Unterstützung für Registerkarten auf mobilen Clients wird in Kürze veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="4ef60-154">Full support for tabs on mobile clients will be released soon.</span></span> <span data-ttu-id="4ef60-155">Zur Vorbereitung des Updates sollten Sie die [Anleitungen für Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md) beim Erstellen Ihrer Registerkarten befolgten.</span><span class="sxs-lookup"><span data-stu-id="4ef60-155">To prepare for the update, you should follow the [guidance for tabs on mobile](~/tabs/design/tabs-mobile.md) when creating your tabs.</span></span>

<span data-ttu-id="4ef60-156">Microsoft Teams SetSettings ()-Konfiguration für die Entfernungs Seite und/oder Mobile Clients:</span><span class="sxs-lookup"><span data-stu-id="4ef60-156">Microsoft Teams setSettings() configuration for removal page and/or mobile clients:</span></span>

```javascript
microsoftTeams.settings.setSettings({
    contentUrl: "add content page URL here",
    entityId: "add unique name here",
    suggestedDisplayName: "add name to display on tab here",
    websiteUrl: "URL REQUIRED FOR MOBILE CLIENTS",
    removeUrl: "ADD REMOVAL PAGE URL HERE"
});
```
