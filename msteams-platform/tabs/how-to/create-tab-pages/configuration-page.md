---
title: Erstellen einer Konfigurationsseite
author: laujan
description: Erstellen einer Konfigurationsseite
keywords: Gruppenkanal für Registerkarten von Teams konfigurierbar
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 2544454fd06348fa41269f3a8fd57cc71a07d140
ms.sourcegitcommit: 84f408aa2854aa7a5cefaa66ce9a373b19e0864a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/18/2021
ms.locfileid: "49886737"
---
# <a name="create-a-configuration-page"></a><span data-ttu-id="63b6e-104">Erstellen einer Konfigurationsseite</span><span class="sxs-lookup"><span data-stu-id="63b6e-104">Create a configuration page</span></span>

<span data-ttu-id="63b6e-105">Eine Konfigurationsseite ist ein spezieller Typ von [Inhaltsseite.](content-page.md)</span><span class="sxs-lookup"><span data-stu-id="63b6e-105">A configuration page is a special type of [content page](content-page.md).</span></span> <span data-ttu-id="63b6e-106">Die Benutzer konfigurieren einige Aspekte der Microsoft Teams-App mithilfe der Konfigurationsseite und verwenden diese Konfiguration im Rahmen der folgenden Schritte:</span><span class="sxs-lookup"><span data-stu-id="63b6e-106">The users configure some aspects of the Microsoft Teams app using the configuration page and use that configuration as part of the following:</span></span>

* <span data-ttu-id="63b6e-107">Registerkarte "Kanal" oder "Gruppenchat" – Sammeln von Informationen von den Benutzern und Festlegen der anzuzeigende `contentUrl` Inhaltsseite.</span><span class="sxs-lookup"><span data-stu-id="63b6e-107">A channel or group chat tab - Collect information from the users and set the `contentUrl` of the content page to display.</span></span>
* <span data-ttu-id="63b6e-108">Eine [Messagingerweiterung](~/messaging-extensions/what-are-messaging-extensions.md)</span><span class="sxs-lookup"><span data-stu-id="63b6e-108">A [messaging extension](~/messaging-extensions/what-are-messaging-extensions.md)</span></span>
* <span data-ttu-id="63b6e-109">Ein [Office 365-Connector](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md)</span><span class="sxs-lookup"><span data-stu-id="63b6e-109">An [Office 365 Connector](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md)</span></span>

## <a name="configuring-a-channel-or-group-chat-tab"></a><span data-ttu-id="63b6e-110">Konfigurieren einer Kanal- oder Gruppenchatregisterkarte</span><span class="sxs-lookup"><span data-stu-id="63b6e-110">Configuring a channel or group chat tab</span></span>

<span data-ttu-id="63b6e-111">Die Anwendung muss auf das [Microsoft Teams JavaScript-Client-SDK verweisen und](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) `microsoft.initialize()` aufrufen.</span><span class="sxs-lookup"><span data-stu-id="63b6e-111">The application must reference the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) and call `microsoft.initialize()`.</span></span> <span data-ttu-id="63b6e-112">Außerdem müssen die verwendeten URLs gesicherte HTTPS-Endpunkte sein und über die Cloud verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="63b6e-112">Also, the URLs used must be secured HTTPS endpoints and available from the cloud.</span></span> <span data-ttu-id="63b6e-113">Der folgende Code ist ein Beispiel für eine Konfigurationsseite:</span><span class="sxs-lookup"><span data-stu-id="63b6e-113">The following code is an example of a configuration page:</span></span>

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

<span data-ttu-id="63b6e-114">Wählen Sie **auf der Konfigurationsseite** die **Schaltfläche** "Grau auswählen" oder "Rot auswählen" aus, um den Registerkarteninhalt mit einem grauen oder roten Symbol anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="63b6e-114">Choose either **Select Gray** or **Select Red** button in the configuration page, to display the tab content with a gray or red icon.</span></span> <span data-ttu-id="63b6e-115">Wenn Sie die relative Schaltfläche auswählen, wird entweder eine oder eine oder mehrere der `saveGray()` `saveRed()` folgenden Schaltflächen aufgerufen:</span><span class="sxs-lookup"><span data-stu-id="63b6e-115">Choosing the relative button fires either `saveGray()` or `saveRed()`, and invokes the following:</span></span>

1. <span data-ttu-id="63b6e-116">Der `settings.setValidityState(true)` Wert ist auf "true" festgelegt.</span><span class="sxs-lookup"><span data-stu-id="63b6e-116">The `settings.setValidityState(true)` is set to true.</span></span>
1. <span data-ttu-id="63b6e-117">Der `microsoftTeams.settings.registerOnSaveHandler()` Ereignishandler wird ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="63b6e-117">The `microsoftTeams.settings.registerOnSaveHandler()` event handler is triggered.</span></span>
1. <span data-ttu-id="63b6e-118">Die **Schaltfläche** "Speichern" auf der Konfigurationsseite der App, die in Teams hochgeladen wurde, ist aktiviert.</span><span class="sxs-lookup"><span data-stu-id="63b6e-118">The **Save** button on the app's configuration page, uploaded in Teams, is enabled.</span></span>

<span data-ttu-id="63b6e-119">Der Konfigurationsseitencode informiert Teams darüber, dass die Konfigurationsanforderungen erfüllt sind und die Installation fortgesetzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="63b6e-119">The configuration page code informs the Teams that the configuration requirements are satisfied and the installation can proceed.</span></span> <span data-ttu-id="63b6e-120">Wenn der Benutzer **"Speichern"** auswählt, werden die Parameter `settings.setSettings()` festgelegt, wie von der Benutzeroberfläche `Settings` definiert.</span><span class="sxs-lookup"><span data-stu-id="63b6e-120">When the user selects **Save**, the parameters of `settings.setSettings()` are set, as defined by the `Settings` interface.</span></span> <span data-ttu-id="63b6e-121">Weitere Informationen finden Sie unter ["Einstellungsschnittstelle".](/javascript/api/@microsoft/teams-js/_settings?view=msteams-client-js-latest&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="63b6e-121">For more information, see [Settings interface](/javascript/api/@microsoft/teams-js/_settings?view=msteams-client-js-latest&preserve-view=true).</span></span> <span data-ttu-id="63b6e-122">Im letzten Schritt wird aufgerufen, um anzugeben, `saveEvent.notifySuccess()` dass die Inhalts-URL erfolgreich aufgelöst wurde.</span><span class="sxs-lookup"><span data-stu-id="63b6e-122">In the last step, `saveEvent.notifySuccess()` is called to indicate that the content URL has successfully resolved.</span></span>

>[!NOTE]
>
>* <span data-ttu-id="63b6e-123">Wenn Sie einen Speicherhandler mithilfe registrieren, muss der Rückruf das Ergebnis der Konfiguration aufrufen `microsoftTeams.settings.registerOnSaveHandler()` `saveEvent.notifySuccess()` oder `saveEvent.notifyFailure()` angeben.</span><span class="sxs-lookup"><span data-stu-id="63b6e-123">If you register a save handler using `microsoftTeams.settings.registerOnSaveHandler()`, the callback must invoke `saveEvent.notifySuccess()` or `saveEvent.notifyFailure()` to indicate the outcome of the configuration.</span></span>
>* <span data-ttu-id="63b6e-124">Wenn Sie keinen Speicherhandler registrieren, wird der Aufruf automatisch ausgeführt, wenn `saveEvent.notifySuccess()` der Benutzer "Speichern" **auswählt.**</span><span class="sxs-lookup"><span data-stu-id="63b6e-124">If you don't register a save handler, the `saveEvent.notifySuccess()` call is made automatically when the user selects **Save**.</span></span>

### <a name="get-context-data-for-your-tab-settings"></a><span data-ttu-id="63b6e-125">Kontextdaten für Ihre Registerkarteneinstellungen erhalten</span><span class="sxs-lookup"><span data-stu-id="63b6e-125">Get context data for your tab settings</span></span>

<span data-ttu-id="63b6e-126">Ihre Registerkarte erfordert möglicherweise kontextbezogene Informationen, um relevante Inhalte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="63b6e-126">Your tab might require contextual information to display relevant content.</span></span> <span data-ttu-id="63b6e-127">Kontextbezogene Informationen verbessern die Aufrufe Ihrer Registerkarte weiter, indem sie eine angepasste Benutzeroberfläche bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="63b6e-127">Contextual information further enhances your tab's appeal by providing a more customized user experience.</span></span>

<span data-ttu-id="63b6e-128">Weitere Informationen zu den Eigenschaften, die für die Registerkartenkonfiguration verwendet werden, finden Sie unter [Kontextschnittstelle](/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="63b6e-128">For more information on the properties used for tab configuration, see [Context interface](/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true).</span></span> <span data-ttu-id="63b6e-129">Sammeln Sie die Werte von Kontextdatenvariablen auf zwei Arten:</span><span class="sxs-lookup"><span data-stu-id="63b6e-129">Collect the values of context data variables in the following two ways:</span></span>

1. <span data-ttu-id="63b6e-130">Einfügen von Platzhaltern für die URL-Abfragezeichenfolge im `configurationURL` Manifest.</span><span class="sxs-lookup"><span data-stu-id="63b6e-130">Insert URL query string placeholders in your manifest's `configurationURL`.</span></span>

1. <span data-ttu-id="63b6e-131">Verwenden Sie die [Teams](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) `microsoftTeams.getContext((context) =>{})` SDK-Methode.</span><span class="sxs-lookup"><span data-stu-id="63b6e-131">Use the [Teams SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) `microsoftTeams.getContext((context) =>{})` method.</span></span>

#### <a name="insert-placeholders-in-the-configurationurl"></a><span data-ttu-id="63b6e-132">Einfügen von Platzhaltern in das `configurationUrl`</span><span class="sxs-lookup"><span data-stu-id="63b6e-132">Insert placeholders in the `configurationUrl`</span></span>

<span data-ttu-id="63b6e-133">Fügen Sie Ihrer Basis Platzhalter für die Kontextschnittstelle `configurationUrl` hinzu.</span><span class="sxs-lookup"><span data-stu-id="63b6e-133">Add context interface placeholders to your base `configurationUrl`.</span></span> <span data-ttu-id="63b6e-134">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="63b6e-134">For example:</span></span>

##### <a name="base-url"></a><span data-ttu-id="63b6e-135">Basis-URL</span><span class="sxs-lookup"><span data-stu-id="63b6e-135">Base URL</span></span>

```json
...
"configurationUrl": "https://yourWebsite/config",
...
```

#### <a name="base-url-with-query-strings"></a><span data-ttu-id="63b6e-136">Basis-URL mit Abfragezeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="63b6e-136">Base URL with query strings</span></span>

```json
...
"configurationUrl": "https://yourWebsite/config?team={teamId}&channel={channelId}&{locale}"
...
```

<span data-ttu-id="63b6e-137">Nach dem Hochladen der Seite aktualisiert Teams die Platzhalter der Abfragezeichenfolge mit relevanten Werten.</span><span class="sxs-lookup"><span data-stu-id="63b6e-137">After your page uploads, the Teams updates the query string placeholders with relevant values.</span></span> <span data-ttu-id="63b6e-138">Schließen Sie logik in die Konfigurationsseite ein, um diese Werte abzurufen und zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="63b6e-138">Include logic in the configuration page to retrieve and use those values.</span></span> <span data-ttu-id="63b6e-139">Weitere Informationen zum Arbeiten mit URL-Abfragezeichenfolgen finden Sie unter ["URLSearchParams"](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) in MDN Web Docs. Im folgenden Beispiel wird die Methode zum Extrahieren eines Werts aus der Eigenschaft `configurationUrl` beschrieben:</span><span class="sxs-lookup"><span data-stu-id="63b6e-139">For more information on working with URL query strings, see [URLSearchParams](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) in MDN Web Docs. The following example describes the way to extract a value from the `configurationUrl` property:</span></span>

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

### <a name="use-the-getcontext-function-to-retrieve-context"></a><span data-ttu-id="63b6e-140">Verwenden der `getContext()` Funktion zum Abrufen von Kontext</span><span class="sxs-lookup"><span data-stu-id="63b6e-140">Use the `getContext()` function to retrieve context</span></span>

<span data-ttu-id="63b6e-141">Die `microsoftTeams.getContext((context) => {})` Funktion ruft die [Kontextschnittstelle ab,](/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true) wenn sie aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="63b6e-141">The `microsoftTeams.getContext((context) => {})` function retrieves the [Context interface](/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true) when invoked.</span></span> <span data-ttu-id="63b6e-142">Fügen Sie diese Funktion zur Konfigurationsseite hinzu, um Kontextwerte abzurufen:</span><span class="sxs-lookup"><span data-stu-id="63b6e-142">Add this function to the configuration page to retrieve context values:</span></span>

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

## <a name="context-and-authentication"></a><span data-ttu-id="63b6e-143">Kontext und Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="63b6e-143">Context and authentication</span></span>

 <span data-ttu-id="63b6e-144">Authentifizieren Sie sich, bevor Ein Benutzer Ihre App konfigurieren können.</span><span class="sxs-lookup"><span data-stu-id="63b6e-144">Authenticate before allowing a user to configure your app.</span></span> <span data-ttu-id="63b6e-145">Andernfalls können Ihre Inhalte Quellen enthalten, die über ihre Authentifizierungsprotokolle verfügen.</span><span class="sxs-lookup"><span data-stu-id="63b6e-145">Otherwise, your content might include sources that have their authentication protocols.</span></span> <span data-ttu-id="63b6e-146">Weitere Informationen finden Sie unter [Authentifizieren eines Benutzers auf einer Microsoft Teams-Registerkarte.](~/tabs/how-to/authentication/auth-flow-tab.md) Verwenden Sie Kontextinformationen, um die URLs für Authentifizierungsanforderungen und Autorisierungsseiten zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="63b6e-146">For more information, see [Authenticate a user in a Microsoft Teams tab](~/tabs/how-to/authentication/auth-flow-tab.md). Use context information to construct the authentication requests and authorization page URLs.</span></span>
<span data-ttu-id="63b6e-147">Stellen Sie sicher, dass alle auf Ihren Registerkartenseiten verwendeten Domänen im `manifest.json` Und-Array aufgeführt `validDomains` sind.</span><span class="sxs-lookup"><span data-stu-id="63b6e-147">Ensure that all domains used in your tab pages are listed in the `manifest.json` and `validDomains` array.</span></span>

## <a name="modify-or-remove-a-tab"></a><span data-ttu-id="63b6e-148">Ändern oder Entfernen einer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="63b6e-148">Modify or remove a tab</span></span>

<span data-ttu-id="63b6e-149">Unterstützte Entfernungsoptionen optimieren die Benutzeroberfläche weiter.</span><span class="sxs-lookup"><span data-stu-id="63b6e-149">Supported removal options further refine the user experience.</span></span> <span data-ttu-id="63b6e-150">Legen Sie die Eigenschaft Des Manifests auf , die es den Benutzern ermöglicht, eine Gruppe oder Kanalregisterkarte zu ändern, neu zu konfigurieren oder `canUpdateConfiguration` `true` umzubenennen. Geben Sie außerdem an, was mit dem Inhalt geschieht, wenn eine Registerkarte entfernt wird, indem Sie eine Seite mit Optionen zum Entfernen in die App hinzufügen und einen Wert für die Eigenschaft `removeUrl` in der Konfiguration  `setSettings()` festlegen.</span><span class="sxs-lookup"><span data-stu-id="63b6e-150">Set your manifest's `canUpdateConfiguration` property to `true`, that enables the users to modify, reconfigure, or rename a group or channel tab. Also, indicate what happens to the content when a tab is removed, by including a removal options page in the app and setting a value for the `removeUrl` property in the  `setSettings()` configuration.</span></span> <span data-ttu-id="63b6e-151">Weitere Informationen finden Sie unter [Mobile Clients](#mobile-clients).</span><span class="sxs-lookup"><span data-stu-id="63b6e-151">For more information, see [Mobile clients](#mobile-clients).</span></span> <span data-ttu-id="63b6e-152">Der Benutzer kann die persönlichen Registerkarten deinstallieren, aber nicht ändern.</span><span class="sxs-lookup"><span data-stu-id="63b6e-152">The user can uninstall the Personal tabs but cannot modify them.</span></span> <span data-ttu-id="63b6e-153">Weitere Informationen finden Sie unter ["Erstellen einer Seite zum Entfernen" für Ihre Registerkarte.](~/tabs/how-to/create-tab-pages/removal-page.md)</span><span class="sxs-lookup"><span data-stu-id="63b6e-153">For more information, see [Create a removal page for your tab](~/tabs/how-to/create-tab-pages/removal-page.md).</span></span>

## <a name="mobile-clients"></a><span data-ttu-id="63b6e-154">Mobile Clients</span><span class="sxs-lookup"><span data-stu-id="63b6e-154">Mobile clients</span></span>

<span data-ttu-id="63b6e-155">Wenn Sie ihre Kanal- oder Gruppenregisterkarte auf den mobilen Clients von Teams anzeigen möchten, muss die Konfiguration `setSettings()` einen Wert für die Eigenschaft `websiteUrl` haben.</span><span class="sxs-lookup"><span data-stu-id="63b6e-155">If you choose to have your channel or group tab appear on the Teams mobile clients, the `setSettings()` configuration must have a value for the `websiteUrl` property.</span></span> <span data-ttu-id="63b6e-156">Weitere Informationen finden Sie unter [Anleitungen für Registerkarten auf mobilen Geräten.](~/tabs/design/tabs-mobile.md)</span><span class="sxs-lookup"><span data-stu-id="63b6e-156">For more information, see [guidance for tabs on mobile](~/tabs/design/tabs-mobile.md).</span></span>

<span data-ttu-id="63b6e-157">Microsoft Teams setSettings()-Konfiguration zum Entfernen von Seiten oder mobilen Clients:</span><span class="sxs-lookup"><span data-stu-id="63b6e-157">Microsoft Teams setSettings() configuration for removal page or mobile clients:</span></span>

```javascript
microsoftTeams.settings.setSettings({
    contentUrl: "add content page URL here",
    entityId: "add unique name here",
    suggestedDisplayName: "add name to display on tab here",
    websiteUrl: "URL REQUIRED FOR MOBILE CLIENTS",
    removeUrl: "ADD REMOVAL PAGE URL HERE"
});
```
