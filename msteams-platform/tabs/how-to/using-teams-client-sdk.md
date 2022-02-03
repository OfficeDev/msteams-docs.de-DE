---
title: Erstellen von Registerkarten und anderen gehosteten Erfahrungen mit dem JavaScript-Client-SDK
author: heath-hamilton
ms.author: surbhigupta
description: Übersicht über das Microsoft Teams JavaScript-Client-SDK, mit dem Sie Teams App-Umgebungen erstellen können, die in einem <iframe>. Es enthält grundlegende Funktionen, Authentifizierungsnamespace und Einstellungsnamespace.
ms.localizationpriority: medium
keywords: teams tabs group channel configurable static SDK JavaScript personal
ms.topic: conceptual
ms.openlocfilehash: 1c8f36348a5227726e466e3d3a8ffb3e6eadd19d
ms.sourcegitcommit: 58a24422bb04a529b6629a56803ed2efabc17cb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2022
ms.locfileid: "62323190"
---
# <a name="building-tabs-and-other-hosted-experiences-with-the-microsoft-teams-javascript-client-sdk"></a>Erstellen von Registerkarten und anderen gehosteten Umgebungen mit dem Microsoft Teams JavaScript-Client-SDK

Das Microsoft Teams JavaScript-Client-SDK kann Ihnen helfen, gehostete Erfahrungen in Teams zu erstellen, was bedeutet, dass Ihre App-Inhalte in einem iframe angezeigt werden.

Das SDK ist hilfreich für die Entwicklung von Apps mit einer der folgenden Teams Funktionen:

* [Registerkarten](../../tabs/what-are-tabs.md)
* [Aufgabenmodule](../../task-modules-and-cards/what-are-task-modules.md)

Das SDK kann ihre Registerkarte beispielsweise dazu bringen, [auf Designänderungen zu reagieren](../../build-your-first-app/build-personal-tab.md#3-update-your-tab-theme), die Ihre Benutzer im Teams-Client vornehmen.

## <a name="getting-started"></a>Erste Schritte

Führen Sie je nach Ihren Entwicklungseinstellungen eine der folgenden Aktionen aus:

* [Installieren des SDK mit npm oder Yarn](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)
* [Klonen des SDK (GitHub)](https://github.com/OfficeDev/microsoft-teams-library-js)

## <a name="common-sdk-functions"></a>Allgemeine SDK-Funktionen

In den folgenden Tabellen finden Sie Informationen zu häufig verwendeten SDK-Funktionen. Die [SDK-Referenzdokumentation](/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true) enthält umfassendere Informationen.

### <a name="basic-functions"></a>Grundlegende Funktionen

| Funktion  | Beschreibung          | Dokumentation|
| -----     | -----     | -----    |
| `microsoftTeams.initialize()` | Initialisiert das SDK. Diese Funktion muss vor allen anderen SDK-Aufrufen aufgerufen werden.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#@microsoft-teams-js-microsoftteams-initialize&preserve-view=true)|
|`microsoftTeams.getContext(callback: (context: Context)`| Ruft den aktuellen Status ab, in dem die Seite ausgeführt wird. Der Rückruf ruft das **Context-Objekt** ab.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest&preserve-view=true)<br/>[Kontext-Obj](/javascript/api/@microsoft/teams-js/@microsoft.teams-js?view=msteams-client-js-latest&preserve-view=true)|
| `microsoftTeams.initializeWithContext({contentUrl: string, websiteUrl: string})` | Initialisiert die Teams Bibliothek und legt den [Framekontext](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true) der Registerkarte abhängig von contentUrl und websiteUrl fest. Dadurch wird sichergestellt, dass die Go-to-Website/Reload-Funktion unter der richtigen URL ausgeführt wird.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#@microsoft-teams-js-microsoftteams-initializewithframecontext&preserve-view=true)|
| `microsoftTeams.setFrameContext({contentUrl: string, websiteUrl: string})` | Legt den [Framekontext](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true) der Registerkarte abhängig von contentUrl und websiteUrl fest. Dadurch wird sichergestellt, dass die Go-to-Website/Reload-Funktion unter der richtigen URL ausgeführt wird.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#@microsoft-teams-js-microsoftteams-setframecontext&preserve-view=true)|
| `microsoftTeams.registerFullScreenHandler(handler: (isFullScreen: boolean)` |Der Handler, der registriert wird, wenn der Benutzer die Vollbild-/Fensteransicht einer Registerkarte umschaltet.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#@microsoft-teams-js-microsoftteams-registerfullscreenhandler&preserve-view=true)<br/>[boolean](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#@microsoft-teams-js-microsoftteams-registerfullscreenhandler&preserve-view=true)|
|`microsoftTeams.registerChangeSettingsHandler()` |Der Handler, der registriert wird, wenn der Benutzer die aktivierte **Einstellungen-Schaltfläche** auswählt, um eine Registerkarte neu zu konfigurieren.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest&preserve-view=true)|
| `microsoftTeams.getTabInstances(callback: (tabInfo: TabInformation),tabInstanceParameters?: TabInstanceParameters,)` |Ruft die Registerkarten ab, die der App gehören. Der Rückruf ruft das **TabInformation** -Objekt ab. Das **TabInstanceParameters -** Objekt ist ein optionaler Parameter.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#@microsoft-teams-js-microsoftteams-gettabinstances&preserve-view=true)<br/>[tabInfo obj](/javascript/api/@microsoft/teams-js/microsoftteams.tabinformation?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.getMruTabInstances(callback: (tabInfo: TabInformation),tabInstanceParameters?: TabInstanceParameters)`|Ruft die zuletzt verwendeten Registerkarten für den Benutzer ab. Der Rückruf ruft das **TabInformation** -Objekt ab. Das **TabInstanceParameters -** Objekt ist ein optionaler Parameter.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#@microsoft-teams-js-microsoftteams-getmrutabinstances&preserve-view=true)<br/>[tabInfo obj](/javascript/api/@microsoft/teams-js/microsoftteams.tabinformation?view=msteams-client-js-latest&preserve-view=true)<br/>[tabInstance obj](/javascript/api/@microsoft/teams-js/microsoftteams.tabinstanceparameters?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.shareDeepLink(deepLinkParameters: DeepLinkParameters)`|Verwendet das **DeepLinkParameters-Objekt** als Eingabe und teilt ein Deep-Link-Dialogfeld, das ein Benutzer verwenden kann, um zu *Inhalten auf der Registerkarte* zu navigieren.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#@microsoft-teams-js-microsoftteams-sharedeeplink&preserve-view=true)<br/>[deepLink-Obj](/javascript/api/@microsoft/teams-js/microsoftteams.deeplinkparameters?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.executeDeepLink(deepLink: string, onComplete?: (status: boolean, reason?: string))`|Verwendet einen erforderlichen **DeepLink** als Eingabe und navigiert den Benutzer zu einer URL oder löst eine Clientaktion (z. B. öffnen oder installieren) einer App *innerhalb Teams* aus.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#@microsoft-teams-js-microsoftteams-executedeeplink&preserve-view=true)|
|`microsoftTeams.navigateToTab(tabInstance: TabInstance, onComplete?: (status: boolean, reason?: string))`|Verwendet das **TabInstance-Objekt** als Eingabe und navigiert zu einer angegebenen Registerkarteninstanz.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#@microsoft-teams-js-microsoftteams-navigatetotab&preserve-view=true)<br/>[tabInstance obj](/javascript/api/@microsoft/teams-js/microsoftteams.tabinstance?view=msteams-client-js-latest&preserve-view=true)|

### <a name="authentication-namespace"></a>Authentifizierungsnamespace

| Funktion  | Beschreibung          | Dokumentation|
| -----     | -----     | -----    |
|`microsoftTeams.authentication.authenticate(authenticateParameters?: AuthenticateParameters)`|Initiiert eine Authentifizierungsanforderung, die ein neues Fenster mit den vom Aufrufer bereitgestellten Parametern öffnet. Optionale Eingabewerte werden vom **AuthenticateParameters-Objekt** definiert.|[function](/javascript/api/@microsoft/teams-js/microsoftteams.authentication?view=msteams-client-js-latest&preserve-view=true)<br/>[Authentifizierungs-Obj](/javascript/api/@microsoft/teams-js/microsoftteams.authentication.authenticateparameters?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.authentication.notifySuccess(result?: string, callbackUrl?: string)`|Benachrichtigt den Frame, der die Authentifizierungsanforderung initiiert hat, dass die Anforderung erfolgreich war, und schließt das Authentifizierungsfenster.|[function](/javascript/api/@microsoft/teams-js/microsoftteams.authentication?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.authentication.notifyFailure(reason?: string, callbackUrl?: string)`|Benachrichtigt den Frame, der die Authentifizierungsanforderung initiiert hat, darüber, dass die Anforderung fehlgeschlagen ist, und schließt das Authentifizierungsfenster.|[function](/javascript/api/@microsoft/teams-js/microsoftteams.authentication?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.authentication.getAuthToken(authTokenRequest: AuthTokenRequest)`|Senden Sie eine Anforderung, um Azure AD Token im Auftrag der App auszustellen. Das Token kann aus dem Cache abgerufen werden, wenn es nicht abgelaufen ist. Andernfalls wird eine Anforderung an Azure AD gesendet, um ein neues Token abzurufen.|[function](/javascript/api/@microsoft/teams-js/microsoftteams.authentication?view=msteams-client-js-latest#@microsoft-teams-js-microsoftteams-authentication-getauthtoken&preserve-view=true)|

### <a name="settings-namespace"></a>Einstellungen-Namespace

| Funktion  | Beschreibung          | Dokumentation|
| -----     | -----     | -----    |
|`microsoftTeams.settings.setValidityState(validityState: boolean)`|Der Anfangswert ist "false". Aktiviert die Schaltfläche **"Speichern** " oder **"Entfernen** ", wenn der Gültigkeitsstatus "true" ist.|[function](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.settings.getSettings(callback: (instanceSettings: Settings)`|Ruft die Einstellungen für die aktuelle Instanz ab. Der Rückruf ruft das **Einstellungen-Objekt** ab.|[function](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true)<br/>[Einstellungs-Obj](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.settings.setSettings(instanceSettings: Settings, onComplete?: (status: boolean, reason?: string)`|Konfiguriert die Einstellungen für die aktuelle Instanz. Gültige Einstellungen werden vom **Einstellungen-Objekt** definiert.|[function](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true)<br/>[Einstellungs-Obj](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.settings.registerOnSaveHandler(handler: (evt: SaveEvent)`|Der Handler, der registriert wird, wenn der Benutzer die Schaltfläche " **Speichern** " auswählt. Dieser Handler sollte verwendet werden, um die zugrunde liegende Ressource zu erstellen oder zu aktualisieren, die den Inhalt unterstützt.|[function](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.settings.registerOnRemoveHandler(handler: (evt: RemoveEvent)`|Der Handler, der registriert wird, wenn der Benutzer die Schaltfläche **"Entfernen"** auswählt. Dieser Handler sollte verwendet werden, um die zugrunde liegende Ressource zu entfernen, die den Inhalt angibt.|[function](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true)|

### <a name="task-modules-namespace"></a>Aufgabenmodulnamespace

| Funktion  | Beschreibung          | Dokumentation|
| -----     | -----     | -----    |
|`microsoftTeams.tasks.startTask(taskInfo: TaskInfo, submitHandler?: (err: string, result: string)`|Verwendet das **TaskInfo-Objekt** als Eingabe und ermöglicht es einer App, das Aufgabenmodul zu öffnen. Der optionale **submitHandler** wird registriert, wenn das Aufgabenmodul abgeschlossen ist. |[function](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest&preserve-view=true)<br/>[taskInfo obj](/javascript/api/@microsoft/teams-js/microsoftteams.taskinfo?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.tasks.submitTask(result?: string | object, appIds?: string | string[])`|Sendet das Aufgabenmodul. Der optionale **Ergebniszeichenfolgenparameter** ist das Ergebnis, das an den Bot oder die App gesendet wird und in der Regel ein JSON-Objekt oder eine Serialisierung ist. Der optionale **parameter "appIds string"** oder "string array" hilft dabei, zu überprüfen, ob der Aufruf von derselben appId stammt wie der Aufruf, der das Aufgabenmodul aufgerufen hat.|[function](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#@microsoft-teams-js-microsoftteams-tasks-submittask&preserve-view=true)|
