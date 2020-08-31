---
title: Verwenden des Teams-Client-SDKs
author: laujan
description: Vorgehensweise verwenden des Teams-Client-SDK zum Hinzufügen von Teams-fähigen Funktionen zu Ihren benutzerdefinierten Registerkarten
keywords: Teams Tabs Gruppenkanal konfigurierbares statisches SDK JavaScript Personal
ms.topic: conceptual
ms.openlocfilehash: 66d44617b897e44268ae2cee53f7ea64743ad821
ms.sourcegitcommit: 9fbc701a9a039ecdc360aefbe86df52b9c3593f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/12/2020
ms.locfileid: "46652015"
---
# <a name="using-the-teams-client-sdk"></a><span data-ttu-id="0d342-104">Verwenden des Teams-Client-SDKs</span><span class="sxs-lookup"><span data-stu-id="0d342-104">Using the Teams client SDK</span></span>

<span data-ttu-id="0d342-105">Das Microsoft Teams-JavaScript- **Client-SDK**  und die JavaScript- **Bibliothek für Teams** sind Teil der [Microsoft Teams-Entwicklerplattform](https://msdn.microsoft.com/microsoft-teams) und stellen Tools und Prozesse zur Verfügung, um die Anwendungserstellung für Teams zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="0d342-105">The **Teams JavaScript client SDK**  and **Teams JavaScript Library** are part of the [Microsoft Teams developer platform](https://msdn.microsoft.com/microsoft-teams) and provide tools and processes to facilitate Teams application creation.</span></span> <span data-ttu-id="0d342-106">Das Microsoft Teams-Client-SDK wird als NPM-Paket verteilt.</span><span class="sxs-lookup"><span data-stu-id="0d342-106">The Teams client SDK is distributed as an npm package.</span></span> <span data-ttu-id="0d342-107">Die neueste Version finden Sie hier: <https://www.npmjs.com/package/@microsoft/teams-js> .</span><span class="sxs-lookup"><span data-stu-id="0d342-107">The latest version can be found here: <https://www.npmjs.com/package/@microsoft/teams-js>.</span></span> <span data-ttu-id="0d342-108">Die Microsoft Teams-Bibliothek befindet sich unter <https://github.com/OfficeDev/microsoft-teams-library-js> .</span><span class="sxs-lookup"><span data-stu-id="0d342-108">The Teams Library is located at <https://github.com/OfficeDev/microsoft-teams-library-js>.</span></span>

<span data-ttu-id="0d342-109">In der folgenden Tabelle werden die in der Entwicklung von Tabs üblicherweise verwendeten Teams-Bibliotheksfunktionen beschrieben:</span><span class="sxs-lookup"><span data-stu-id="0d342-109">The following table outlines the Teams Library functions typically used in tabs development:</span></span>

## <a name="teams-sdk-public-api"></a><span data-ttu-id="0d342-110">Öffentliche Microsoft Teams SDK-API</span><span class="sxs-lookup"><span data-stu-id="0d342-110">Teams SDK public API</span></span> 

| <span data-ttu-id="0d342-111">Funktion</span><span class="sxs-lookup"><span data-stu-id="0d342-111">Function</span></span>  | <span data-ttu-id="0d342-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0d342-112">Description</span></span>          | <span data-ttu-id="0d342-113">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="0d342-113">Documentation</span></span>|
| -----     | -----     | -----    | -----        |
| `microsoftTeams.initialize()` | <span data-ttu-id="0d342-114">Initialisiert die Teams-Bibliothek.</span><span class="sxs-lookup"><span data-stu-id="0d342-114">Initializes the Teams library.</span></span> <span data-ttu-id="0d342-115">Diese Funktion muss vor anderen SDK-aufrufen aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="0d342-115">This function must be called before any other SDK calls.</span></span>|[<span data-ttu-id="0d342-116">function</span><span class="sxs-lookup"><span data-stu-id="0d342-116">function</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#initialize-any-)|
|`microsoftTeams.getContext(callback: (context: Context)`| <span data-ttu-id="0d342-117">Ruft den aktuellen Zustand ab, in dem die Seite läuft.</span><span class="sxs-lookup"><span data-stu-id="0d342-117">Gets the current state in which the page is running.</span></span> <span data-ttu-id="0d342-118">Der Rückruf Ruft das **context** -Objekt ab.</span><span class="sxs-lookup"><span data-stu-id="0d342-118">The callback retrieves the **Context** object.</span></span>|[<span data-ttu-id="0d342-119">function</span><span class="sxs-lookup"><span data-stu-id="0d342-119">function</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#getcontext--context--context-----void-)<br/>[<span data-ttu-id="0d342-120">Kontext-obj</span><span class="sxs-lookup"><span data-stu-id="0d342-120">context obj</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest)|
| `microsoftTeams.initializeWithContext({contentUrl: string, websiteUrl: string})` | <span data-ttu-id="0d342-121">Initialisiert die Teams-Bibliothek und legt den [Rahmen Kontext](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest) der Registerkarte abhängig von der contentUrl und websiteUrl.</span><span class="sxs-lookup"><span data-stu-id="0d342-121">Initializes the Teams library and sets the tab's [frame context](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest) depending on the contentUrl and websiteUrl.</span></span> <span data-ttu-id="0d342-122">Dadurch wird sichergestellt, dass die Funktion "Gehe zu Website/Reload" mit der korrekten URL arbeitet.</span><span class="sxs-lookup"><span data-stu-id="0d342-122">This ensures the go-to-website/reload functionality operates on the correct URL.</span></span>|[<span data-ttu-id="0d342-123">function</span><span class="sxs-lookup"><span data-stu-id="0d342-123">function</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#initializewithframecontext-framecontext--------void--string---)|
| `microsoftTeams.setFrameContext({contentUrl: string, websiteUrl: string})` | <span data-ttu-id="0d342-124">Legt den [Rahmen Kontext](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest) der Registerkarte je nach contentUrl und websiteUrl.</span><span class="sxs-lookup"><span data-stu-id="0d342-124">Sets the tab's [frame context](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest) depending on the contentUrl and websiteUrl.</span></span> <span data-ttu-id="0d342-125">Dadurch wird sichergestellt, dass die Funktion "Gehe zu Website/Reload" mit der korrekten URL arbeitet.</span><span class="sxs-lookup"><span data-stu-id="0d342-125">This ensures the go-to-website/reload functionality operates on the correct URL.</span></span>|[<span data-ttu-id="0d342-126">function</span><span class="sxs-lookup"><span data-stu-id="0d342-126">function</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#setframecontext-framecontext-)|
| `microsoftTeams.registerFullScreenHandler(handler: (isFullScreen: boolean)` |<span data-ttu-id="0d342-127">Der Handler, der registriert wird, wenn der Benutzer die Vollbildansicht/Fenster Ansicht eines Tabs umschalten kann.</span><span class="sxs-lookup"><span data-stu-id="0d342-127">The handler that is registered when the user toggles a tab's full-screen/windowed view.</span></span>|[<span data-ttu-id="0d342-128">function</span><span class="sxs-lookup"><span data-stu-id="0d342-128">function</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#registerfullscreenhandler--isfullscreen--boolean-----void-)<br/>[<span data-ttu-id="0d342-129">boolean</span><span class="sxs-lookup"><span data-stu-id="0d342-129">boolean</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest#isfullscreen)|
|`microsoftTeams.registerChangeSettingsHandler()` |<span data-ttu-id="0d342-130">Der Handler, der registriert wird, wenn der Benutzer die Schaltfläche "aktivierte **Einstellungen** " auswählt, um eine Registerkarte neu zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="0d342-130">The handler that is registered when the user selects the enabled **Settings** button to reconfigure a tab.</span></span>|[<span data-ttu-id="0d342-131">function</span><span class="sxs-lookup"><span data-stu-id="0d342-131">function</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#registerchangesettingshandler-------void-)|
| `microsoftTeams.getTabInstances(callback: (tabInfo: TabInformation),tabInstanceParameters?: TabInstanceParameters,)` |<span data-ttu-id="0d342-132">Ruft die Registerkarten im Besitz der App ab.</span><span class="sxs-lookup"><span data-stu-id="0d342-132">Gets the tabs owned by the app.</span></span> <span data-ttu-id="0d342-133">Der Rückruf Ruft das **TabInformation** -Objekt ab.</span><span class="sxs-lookup"><span data-stu-id="0d342-133">The callback retrieves the **TabInformation** object.</span></span> <span data-ttu-id="0d342-134">Das **TabInstanceParameters** -Objekt ist ein optionaler Parameter.</span><span class="sxs-lookup"><span data-stu-id="0d342-134">The **TabInstanceParameters** object is an optional parameter.</span></span>|[<span data-ttu-id="0d342-135">function</span><span class="sxs-lookup"><span data-stu-id="0d342-135">function</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#gettabinstances--tabinfo--tabinformation-----void--tabinstanceparameters-)<br/>[<span data-ttu-id="0d342-136">TabInfo obj</span><span class="sxs-lookup"><span data-stu-id="0d342-136">tabInfo obj</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams.tabinformation?view=msteams-client-js-latest)|
|`microsoftTeams.getMruTabInstances(callback: (tabInfo: TabInformation),tabInstanceParameters?: TabInstanceParameters)`|<span data-ttu-id="0d342-137">Ruft die zuletzt verwendeten Registerkarten für den Benutzer ab.</span><span class="sxs-lookup"><span data-stu-id="0d342-137">Gets the most recently used tabs for the user.</span></span> <span data-ttu-id="0d342-138">Der Rückruf Ruft das **TabInformation** -Objekt ab.</span><span class="sxs-lookup"><span data-stu-id="0d342-138">The callback retrieves the **TabInformation** object.</span></span> <span data-ttu-id="0d342-139">Das **TabInstanceParameters** -Objekt ist ein optionaler Parameter.</span><span class="sxs-lookup"><span data-stu-id="0d342-139">The **TabInstanceParameters** object is an optional parameter.</span></span>|[<span data-ttu-id="0d342-140">function</span><span class="sxs-lookup"><span data-stu-id="0d342-140">function</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#getmrutabinstances--tabinfo--tabinformation-----void--tabinstanceparameters-)<br/>[<span data-ttu-id="0d342-141">TabInfo obj</span><span class="sxs-lookup"><span data-stu-id="0d342-141">tabInfo obj</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams.teaminformation?view=msteams-client-js-latest)<br/>[<span data-ttu-id="0d342-142">tabInstance obj</span><span class="sxs-lookup"><span data-stu-id="0d342-142">tabInstance obj</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams.tabinstanceparameters?view=msteams-client-js-latest)|
|`microsoftTeams.shareDeepLink(deepLinkParameters: DeepLinkParameters)`|<span data-ttu-id="0d342-143">Das **DeepLinkParameters** -Objekt wird als Eingabe verwendet, und es wird ein Dialogfeld Deep Link gemeinsam verwendet, mit dem ein Benutzer zu Inhalten *innerhalb der Registerkarte*navigieren kann.</span><span class="sxs-lookup"><span data-stu-id="0d342-143">Takes the **DeepLinkParameters** object as input and shares a deep link dialog box that a user can use to navigate to content *within the tab*.</span></span>|[<span data-ttu-id="0d342-144">function</span><span class="sxs-lookup"><span data-stu-id="0d342-144">function</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#sharedeeplink-deeplinkparameters-)<br/>[<span data-ttu-id="0d342-145">deepLink obj</span><span class="sxs-lookup"><span data-stu-id="0d342-145">deepLink obj</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams.deeplinkparameters?view=msteams-client-js-latest)|
|`microsoftTeams.executeDeepLink(deepLink: string, onComplete?: (status: boolean, reason?: string))`|<span data-ttu-id="0d342-146">Akzeptiert eine erforderliche **deepLink** als Eingabe und navigiert Benutzer zu einer URL oder löst eine Clientaktion aus – beispielsweise öffnen oder installieren – eine APP *in Microsoft Teams*.</span><span class="sxs-lookup"><span data-stu-id="0d342-146">Takes a required **deepLink** as input and navigates user to a URL or triggers a client action—such as opening or installing—an app *within Teams*.</span></span>|[<span data-ttu-id="0d342-147">function</span><span class="sxs-lookup"><span data-stu-id="0d342-147">function</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#executedeeplink-string---status--boolean--reason---string-----void-)|
|`microsoftTeams.navigateToTab(tabInstance: TabInstance, onComplete?: (status: boolean, reason?: string))`|<span data-ttu-id="0d342-148">Das **TabInstance** -Objekt wird als Eingabe verwendet und zu einer angegebenen Registerkarten Instanz navigiert.</span><span class="sxs-lookup"><span data-stu-id="0d342-148">Takes the **TabInstance** object as input and navigates to a specified tab instance.</span></span>|[<span data-ttu-id="0d342-149">function</span><span class="sxs-lookup"><span data-stu-id="0d342-149">function</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#navigatetotab-tabinstance-)<br/>[<span data-ttu-id="0d342-150">tabInstance obj</span><span class="sxs-lookup"><span data-stu-id="0d342-150">tabInstance obj</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams.tabinstance?view=msteams-client-js-latest)|

## <a name="authentication-namespace"></a><span data-ttu-id="0d342-151">Authentifizierungs Namespace</span><span class="sxs-lookup"><span data-stu-id="0d342-151">Authentication namespace</span></span>

| <span data-ttu-id="0d342-152">Funktion</span><span class="sxs-lookup"><span data-stu-id="0d342-152">Function</span></span>  | <span data-ttu-id="0d342-153">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0d342-153">Description</span></span>          | <span data-ttu-id="0d342-154">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="0d342-154">Documentation</span></span>|
| -----     | -----     | -----    | -----        |
|`microsoftTeams.authentication.authenticate(authenticateParameters?: AuthenticateParameters)`|<span data-ttu-id="0d342-155">Initiiert eine Authentifizierungsanforderung, die ein neues Fenster mit den vom Aufrufer bereitgestellten Parametern öffnet.</span><span class="sxs-lookup"><span data-stu-id="0d342-155">Initiates an authentication request that opens a new window with the parameters provided by the caller.</span></span> <span data-ttu-id="0d342-156">Optionale Eingabewerte werden durch das **AuthenticateParameters** -Objekt definiert.</span><span class="sxs-lookup"><span data-stu-id="0d342-156">Optional input values are defined by the **AuthenticateParameters** object.</span></span>|[<span data-ttu-id="0d342-157">function</span><span class="sxs-lookup"><span data-stu-id="0d342-157">function</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams.authentication?view=msteams-client-js-latest#authenticate-authenticateparameters-)<br/>[<span data-ttu-id="0d342-158">Authentifizierungs-obj</span><span class="sxs-lookup"><span data-stu-id="0d342-158">auth obj</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams.authentication.authenticateparameters?view=msteams-client-js-latest)|
|`microsoftTeams.authentication.notifySuccess(result?: string, callbackUrl?: string)`|<span data-ttu-id="0d342-159">Benachrichtigt den Frame, der die Authentifizierungsanforderung initiiert hat, dass die Anforderung erfolgreich war, und schließt das Authentifizierungsfenster</span><span class="sxs-lookup"><span data-stu-id="0d342-159">Notifies the frame that initiated the authentication request that the request was successful and closes the authentication window</span></span>|[<span data-ttu-id="0d342-160">function</span><span class="sxs-lookup"><span data-stu-id="0d342-160">function</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams.authentication?view=msteams-client-js-latest#notifysuccess-string--string-)|
|`microsoftTeams.authentication.notifyFailure(reason?: string, callbackUrl?: string)`|<span data-ttu-id="0d342-161">Benachrichtigt den Frame, der die Authentifizierungsanforderung initiiert hat, dass die Anforderung fehlgeschlagen ist, und schließt das Authentifizierungsfenster.</span><span class="sxs-lookup"><span data-stu-id="0d342-161">Notifies the frame that initiated the authentication request that the request failed and closes the authentication window.</span></span>|[<span data-ttu-id="0d342-162">function</span><span class="sxs-lookup"><span data-stu-id="0d342-162">function</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams.authentication?view=msteams-client-js-latest#notifyfailure-string--string-)|

## <a name="settings-namespace"></a><span data-ttu-id="0d342-163">Namespace "Settings"</span><span class="sxs-lookup"><span data-stu-id="0d342-163">Settings namespace</span></span>

| <span data-ttu-id="0d342-164">Funktion</span><span class="sxs-lookup"><span data-stu-id="0d342-164">Function</span></span>  | <span data-ttu-id="0d342-165">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0d342-165">Description</span></span>          | <span data-ttu-id="0d342-166">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="0d342-166">Documentation</span></span>|
| -----     | -----     | -----    | -----        |
|`microsoftTeams.settings.setValidityState(validityState: boolean)`|<span data-ttu-id="0d342-167">Der Anfangswert ist false.</span><span class="sxs-lookup"><span data-stu-id="0d342-167">The initial value is false.</span></span> <span data-ttu-id="0d342-168">Aktiviert die Schaltfläche **Speichern** oder **Entfernen** , wenn der Gültigkeitsstatus auf true festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="0d342-168">Activates the **Save** or **Remove** button when the validity state is true.</span></span>|[<span data-ttu-id="0d342-169">function</span><span class="sxs-lookup"><span data-stu-id="0d342-169">function</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams.settings?view=msteams-client-js-latest#setvaliditystate-boolean-)|
|`microsoftTeams.settings.getSettings(callback: (instanceSettings: Settings)`|<span data-ttu-id="0d342-170">Ruft die Einstellungen für die aktuelle Instanz ab.</span><span class="sxs-lookup"><span data-stu-id="0d342-170">Gets the settings for the current instance.</span></span> <span data-ttu-id="0d342-171">Der Rückruf Ruft das **Settings** -Objekt ab.</span><span class="sxs-lookup"><span data-stu-id="0d342-171">The callback retrieves the **Settings** object.</span></span>|[<span data-ttu-id="0d342-172">function</span><span class="sxs-lookup"><span data-stu-id="0d342-172">function</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams.settings?view=msteams-client-js-latest#getsettings--instancesettings--settings-----void-)<br/>[<span data-ttu-id="0d342-173">obj-Einstellungen</span><span class="sxs-lookup"><span data-stu-id="0d342-173">settings obj</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest)|
|`microsoftTeams.settings.setSettings(instanceSettings: Settings, onComplete?: (status: boolean, reason?: string)`|<span data-ttu-id="0d342-174">Konfiguriert die Einstellungen für die aktuelle Instanz.</span><span class="sxs-lookup"><span data-stu-id="0d342-174">Configures the settings for the current instance.</span></span> <span data-ttu-id="0d342-175">Gültige Einstellungen werden durch das **Settings** -Objekt definiert.</span><span class="sxs-lookup"><span data-stu-id="0d342-175">Valid settings are defined by the **Settings** object.</span></span>|[<span data-ttu-id="0d342-176">function</span><span class="sxs-lookup"><span data-stu-id="0d342-176">function</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams.settings?view=msteams-client-js-latest#setsettings-settings-)<br/>[<span data-ttu-id="0d342-177">obj-Einstellungen</span><span class="sxs-lookup"><span data-stu-id="0d342-177">settings obj</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest)|
|`microsoftTeams.settings.registerOnSaveHandler(handler: (evt: SaveEvent)`|<span data-ttu-id="0d342-178">Der Handler, der registriert wird, wenn der Benutzer die Schaltfläche **Speichern** auswählt.</span><span class="sxs-lookup"><span data-stu-id="0d342-178">The handler that is registered when the user selects the **Save** button.</span></span> <span data-ttu-id="0d342-179">Dieser Handler sollte verwendet werden, um die zugrunde liegende Ressource, die den Inhalt einmacht, zu erstellen oder zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="0d342-179">This handler should be used to create or update the underlying resource powering the content.</span></span>|[<span data-ttu-id="0d342-180">function</span><span class="sxs-lookup"><span data-stu-id="0d342-180">function</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams.settings?view=msteams-client-js-latest#registeronsavehandler--evt--saveevent-----void-)|
|`microsoftTeams.settings.registerOnRemoveHandler(handler: (evt: RemoveEvent)`|<span data-ttu-id="0d342-181">Der Handler, der registriert wird, wenn der Benutzer die Schaltfläche **Entfernen** auswählt.</span><span class="sxs-lookup"><span data-stu-id="0d342-181">The handler that is registered when the user selects the **Remove** button.</span></span> <span data-ttu-id="0d342-182">Dieser Handler sollte verwendet werden, um die zugrunde liegende Ressource zu entfernen, die den Inhalt einmacht.</span><span class="sxs-lookup"><span data-stu-id="0d342-182">This handler should be used to remove the underlying resource powering the content.</span></span>|[<span data-ttu-id="0d342-183">function</span><span class="sxs-lookup"><span data-stu-id="0d342-183">function</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams.settings?view=msteams-client-js-latest#registeronremovehandler--evt--removeevent-----void-)|

## <a name="tasks-namespace"></a><span data-ttu-id="0d342-184">Aufgaben-Namespace</span><span class="sxs-lookup"><span data-stu-id="0d342-184">Tasks namespace</span></span>

| <span data-ttu-id="0d342-185">Funktion</span><span class="sxs-lookup"><span data-stu-id="0d342-185">Function</span></span>  | <span data-ttu-id="0d342-186">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0d342-186">Description</span></span>          | <span data-ttu-id="0d342-187">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="0d342-187">Documentation</span></span>|
| -----     | -----     | -----    | -----        |
|`microsoftTeams.tasks.startTask(taskInfo: TaskInfo, submitHandler?: (err: string, result: string)`|<span data-ttu-id="0d342-188">Das **taskinfo** -Objekt wird als Eingabe verwendet und ermöglicht einer APP das Öffnen des Aufgabenmoduls.</span><span class="sxs-lookup"><span data-stu-id="0d342-188">Takes the **TaskInfo** object as input and allows an app to open the task module.</span></span> <span data-ttu-id="0d342-189">Das optionale **submitHandler** wird registriert, wenn der Aufgabenmodul abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="0d342-189">The optional **submitHandler** is registered when the task module is completed.</span></span> |[<span data-ttu-id="0d342-190">function</span><span class="sxs-lookup"><span data-stu-id="0d342-190">function</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#starttask-taskinfo---err--string--result--string-----void-)<br/>[<span data-ttu-id="0d342-191">taskInfo obj</span><span class="sxs-lookup"><span data-stu-id="0d342-191">taskInfo obj</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams.taskinfo?view=msteams-client-js-latest)|
|`microsoftTeams.tasks.submitTask(result?: string | object, appIds?: string | string[])`|<span data-ttu-id="0d342-192">Sendet das Aufgabenmodul.</span><span class="sxs-lookup"><span data-stu-id="0d342-192">Submits the task module.</span></span> <span data-ttu-id="0d342-193">Der optionale **Ergebnis** Zeichenfolgen-Parameter ist das Ergebnis, das an den bot oder die APP gesendet wurde, und ist in der Regel ein JSON-Objekt oder eine Serialisierung; Die optionale Zeichenfolge oder der String-Arrayparameter für die **Zeichenfolgengruppe** hilft bei der Überprüfung, dass der Aufruf von der gleichen Webanwendung stammt wie diejenige, die den Aufgabenmodul aufgerufen hat.</span><span class="sxs-lookup"><span data-stu-id="0d342-193">The optional **result** string parameter is the result sent to the bot or the app and is typically a JSON object or serialization; The optional **appIds** string or string array parameter aids in validating that the call originated from the same appId as the one that invoked the task module.</span></span>|[<span data-ttu-id="0d342-194">function</span><span class="sxs-lookup"><span data-stu-id="0d342-194">function</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---)|