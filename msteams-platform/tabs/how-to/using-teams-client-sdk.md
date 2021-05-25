---
title: Erstellen von Registerkarten und anderen gehosteten Erfahrungen mit dem JavaScript-Client-SDK
author: heath-hamilton
ms.author: surbhigupta
description: Übersicht über das Microsoft Teams JavaScript-Client-SDK, das Ihnen beim Erstellen Teams app-Erfahrungen helfen kann, die in einem gehosteten <iframe>.
localization_priority: Normal
keywords: teams tabs group channel configurable static SDK JavaScript personal
ms.topic: conceptual
ms.openlocfilehash: 04c6bb9d7687a068375bce548588e6713fd57747
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "52630341"
---
# <a name="building-tabs-and-other-hosted-experiences-with-the-microsoft-teams-javascript-client-sdk"></a>Erstellen von Registerkarten und anderen gehosteten Erfahrungen mit dem Microsoft Teams JavaScript-Client-SDK

Das Microsoft Teams JavaScript-Client-SDK kann Ihnen dabei helfen, gehostete Erfahrungen in Teams zu erstellen, was bedeutet, Dass Ihre App-Inhalte in einem iframe angezeigt werden.

Das SDK ist für die Entwicklung von Apps mit einer der folgenden Funktionen Teams hilfreich:

* [Registerkarten](../../tabs/what-are-tabs.md)
* [Aufgabenmodule](../../task-modules-and-cards/what-are-task-modules.md)

Beispielsweise kann das SDK [](../../build-your-first-app/build-personal-tab.md#3-update-your-tab-theme) Ihre Registerkarte auf Designänderungen reagieren lassen, die Ihre Benutzer im Teams vornehmen.

## <a name="getting-started"></a>Erste Schritte

Gehen Sie je nach Ihren Entwicklungseinstellungen wie folgt vor:

* [Installieren des SDK mit npm oder Yarn](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)
* [Klonen des SDK (GitHub)](https://github.com/OfficeDev/microsoft-teams-library-js)

## <a name="common-sdk-functions"></a>Allgemeine SDK-Funktionen

In den folgenden Tabellen finden Sie Informationen zu häufig verwendeten SDK-Funktionen. Die [SDK-Referenzdokumentation](/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true) enthält umfassendere Informationen.

### <a name="basic-functions"></a>Grundlegende Funktionen

| Funktion  | Beschreibung          | Dokumentation|
| -----     | -----     | -----    |
| `microsoftTeams.initialize()` | Initialisiert das SDK. Diese Funktion muss vor anderen SDK-Aufrufen aufgerufen werden.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#initialize-any-&preserve-view=true)|
|`microsoftTeams.getContext(callback: (context: Context)`| Ruft den aktuellen Status ab, in dem die Seite ausgeführt wird. Der Rückruf ruft das **Context-Objekt** ab.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#getcontext--context--context-----void-&preserve-view=true)<br/>[context obj](/javascript/api/@microsoft/teams-js/@microsoft.teams-js?view=msteams-client-js-latest&preserve-view=true)|
| `microsoftTeams.initializeWithContext({contentUrl: string, websiteUrl: string})` | Initialisiert die Teams und legt den Rahmenkontext [](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true) der Registerkarte abhängig von contentUrl und websiteUrl fest. Dadurch wird sichergestellt, dass die Go-to-Website/Reload-Funktion auf der richtigen URL funktioniert.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#initializewithframecontext-framecontext--------void--string---&preserve-view=true)|
| `microsoftTeams.setFrameContext({contentUrl: string, websiteUrl: string})` | Legt den [Rahmenkontext](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true) der Registerkarte in Abhängigkeit von contentUrl und websiteUrl fest. Dadurch wird sichergestellt, dass die Go-to-Website/Reload-Funktion auf der richtigen URL funktioniert.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#setframecontext-framecontext-&preserve-view=true)|
| `microsoftTeams.registerFullScreenHandler(handler: (isFullScreen: boolean)` |Der Handler, der registriert wird, wenn der Benutzer die Vollbild-/Fensteransicht einer Registerkarte umschaltet.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#registerfullscreenhandler--isfullscreen--boolean-----void-&preserve-view=true)<br/>[boolean](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#registerFullScreenHandler__isFullScreen__boolean_____void_&preserve-view=true)|
|`microsoftTeams.registerChangeSettingsHandler()` |Der Handler, der registriert wird,  wenn der Benutzer die Einstellungen auswählt, um eine Registerkarte neu zu konfigurieren.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#registerchangesettingshandler-------void-&preserve-view=true)|
| `microsoftTeams.getTabInstances(callback: (tabInfo: TabInformation),tabInstanceParameters?: TabInstanceParameters,)` |Ruft die Registerkarten ab, die der App gehören. Der Rückruf ruft das **TabInformation-Objekt** ab. Das **TabInstanceParameters-Objekt** ist ein optionaler Parameter.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#gettabinstances--tabinfo--tabinformation-----void--tabinstanceparameters-&preserve-view=true)<br/>[tabInfo obj](/javascript/api/@microsoft/teams-js/microsoftteams.tabinformation?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.getMruTabInstances(callback: (tabInfo: TabInformation),tabInstanceParameters?: TabInstanceParameters)`|Ruft die zuletzt verwendeten Registerkarten für den Benutzer ab. Der Rückruf ruft das **TabInformation-Objekt** ab. Das **TabInstanceParameters-Objekt** ist ein optionaler Parameter.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#getmrutabinstances--tabinfo--tabinformation-----void--tabinstanceparameters-&preserve-view=true)<br/>[tabInfo obj](/javascript/api/@microsoft/teams-js/microsoftteams.tabinformation?view=msteams-client-js-latest&preserve-view=true)<br/>[tabInstance obj](/javascript/api/@microsoft/teams-js/microsoftteams.tabinstanceparameters?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.shareDeepLink(deepLinkParameters: DeepLinkParameters)`|Nimmt das **DeepLinkParameters-Objekt** als Eingabe an und teilt ein Dialogfeld mit tiefen Verknüpfungen, das ein Benutzer verwenden kann, um zu *Inhalten innerhalb der Registerkarte zu navigieren.*|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#sharedeeplink-deeplinkparameters-&preserve-view=true)<br/>[deepLink obj](/javascript/api/@microsoft/teams-js/microsoftteams.deeplinkparameters?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.executeDeepLink(deepLink: string, onComplete?: (status: boolean, reason?: string))`|Nimmt einen erforderlichen **deepLink** als Eingabe an und navigiert den Benutzer zu einer URL oder löst eine Clientaktion aus , z. B. das Öffnen oder Installieren einer *App innerhalb Teams*.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#executedeeplink-string---status--boolean--reason---string-----void-&preserve-view=true)|
|`microsoftTeams.navigateToTab(tabInstance: TabInstance, onComplete?: (status: boolean, reason?: string))`|Übernimmt **das TabInstance-Objekt** als Eingabe und navigiert zu einer angegebenen Registerkarteninstanz.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#navigatetotab-tabinstance-&preserve-view=true)<br/>[tabInstance obj](/javascript/api/@microsoft/teams-js/microsoftteams.tabinstance?view=msteams-client-js-latest&preserve-view=true)|

### <a name="authentication-namespace"></a>Authentifizierungsnamespace

| Funktion  | Beschreibung          | Dokumentation|
| -----     | -----     | -----    |
|`microsoftTeams.authentication.authenticate(authenticateParameters?: AuthenticateParameters)`|Initiiert eine Authentifizierungsanforderung, die ein neues Fenster mit den vom Aufrufer bereitgestellten Parametern öffnet. Optionale Eingabewerte werden vom **AuthenticateParameters-Objekt** definiert.|[function](/javascript/api/@microsoft/teams-js/microsoftteams.authentication?view=msteams-client-js-latest&preserve-view=true)<br/>[auth obj](/javascript/api/@microsoft/teams-js/microsoftteams.authentication.authenticateparameters?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.authentication.notifySuccess(result?: string, callbackUrl?: string)`|Benachrichtigt den Frame, der die Authentifizierungsanforderung initiiert hat, dass die Anforderung erfolgreich war, und schließt das Authentifizierungsfenster.|[function](/javascript/api/@microsoft/teams-js/microsoftteams.authentication?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.authentication.notifyFailure(reason?: string, callbackUrl?: string)`|Benachrichtigt den Frame, der die Authentifizierungsanforderung initiiert hat, dass die Anforderung fehlgeschlagen ist, und schließt das Authentifizierungsfenster.|[function](/javascript/api/@microsoft/teams-js/microsoftteams.authentication?view=msteams-client-js-latest&preserve-view=true)|

### <a name="settings-namespace"></a>Einstellungen Namespace

| Funktion  | Beschreibung          | Dokumentation|
| -----     | -----     | -----    |
|`microsoftTeams.settings.setValidityState(validityState: boolean)`|Der Anfangswert ist false. Aktiviert die Schaltfläche **Speichern** oder **Entfernen,** wenn der Gültigkeitsstatus true ist.|[function](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.settings.getSettings(callback: (instanceSettings: Settings)`|Ruft die Einstellungen für die aktuelle Instanz ab. Der Rückruf ruft das **Einstellungen** ab.|[function](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true)<br/>[settings obj](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.settings.setSettings(instanceSettings: Settings, onComplete?: (status: boolean, reason?: string)`|Konfiguriert die Einstellungen für die aktuelle Instanz. Gültige Einstellungen werden durch das **Einstellungen** definiert.|[function](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true)<br/>[settings obj](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.settings.registerOnSaveHandler(handler: (evt: SaveEvent)`|Der Handler, der registriert wird, wenn der Benutzer die Schaltfläche **Speichern** auswählt. Dieser Handler sollte zum Erstellen oder Aktualisieren der zugrunde liegenden Ressource verwendet werden, die den Inhalt nutzt.|[function](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.settings.registerOnRemoveHandler(handler: (evt: RemoveEvent)`|Der Handler, der registriert wird, wenn der Benutzer die Schaltfläche **Entfernen** auswählt. Dieser Handler sollte verwendet werden, um die zugrunde liegende Ressource zu entfernen, die den Inhalt nutzt.|[function](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true)|

### <a name="task-modules-namespace"></a>Namespace für Aufgabenmodule

| Funktion  | Beschreibung          | Dokumentation|
| -----     | -----     | -----    |
|`microsoftTeams.tasks.startTask(taskInfo: TaskInfo, submitHandler?: (err: string, result: string)`|Nimmt das **TaskInfo-Objekt** als Eingabe an und ermöglicht einer App das Öffnen des Aufgabenmoduls. Der optionale **submitHandler** wird registriert, wenn das Aufgabenmodul abgeschlossen ist. |[function](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest&preserve-view=true)<br/>[taskInfo obj](/javascript/api/@microsoft/teams-js/microsoftteams.taskinfo?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.tasks.submitTask(result?: string | object, appIds?: string | string[])`|Sendet das Aufgabenmodul. Der optionale **Ergebniszeichenfolgenparameter** ist das an den Bot oder die App gesendete Ergebnis und ist in der Regel ein #A0 oder eine Serialisierung. Der optionale **parameter appIds** string or string array hilft beim Überprüfen, ob der Aufruf von derselben appId stammt wie der, der das Aufgabenmodul aufgerufen hat.|[function](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true)|
