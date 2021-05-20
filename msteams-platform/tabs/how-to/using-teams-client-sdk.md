---
title: Erstellen von Registerkarten und anderen gehosteten Erlebnissen mit dem JavaScript-Client-SDK
author: heath-hamilton
ms.author: surbhigupta
description: Überblick über das Microsoft Teams JavaScript-Client-SDK, mit dem Sie Teams App-Erlebnisse erstellen können, die in einem <iframe>.
localization_priority: Normal
keywords: Teams Registerkarten Gruppenkanal konfigurierbar statische SDK JavaScript personal
ms.topic: conceptual
ms.openlocfilehash: d3dfadda7f2a56e32ecf8e5b67df3b9831c52739
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566656"
---
# <a name="building-tabs-and-other-hosted-experiences-with-the-microsoft-teams-javascript-client-sdk"></a>Erstellen von Registerkarten und anderen gehosteten Erlebnissen mit dem Microsoft Teams JavaScript-Client-SDK

Das Microsoft Teams JavaScript-Client-SDK kann Ihnen beim Erstellen gehosteter Erlebnisse in Teams helfen, d. h. Ihre App-Inhalte in einem iframe anzeigen.

Das SDK ist hilfreich für die Entwicklung von Apps mit einer der folgenden Teams Funktionen:

* [Registerkarten](../../tabs/what-are-tabs.md)
* [Aufgabenmodule](../../task-modules-and-cards/what-are-task-modules.md)

Das SDK kann z. B. dazu führen, dass Ihre [Registerkarte auf Designänderungen reagiert,](../../build-your-first-app/build-personal-tab.md) die Ihre Benutzer im Teams-Client vornehmen.

## <a name="getting-started"></a>Erste Schritte

Führen Sie je nach Ihren Entwicklungseinstellungen eine der folgenden Schritte aus:

* [Installieren Sie das SDK mit npm oder Yarn](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)

## <a name="common-sdk-functions"></a>Gemeinsame SDK-Funktionen

In den folgenden Tabellen finden Sie informationen zu häufig verwendeten SDK-Funktionen. Die [SDK-Referenzdokumentation](/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true) bietet umfassendere Informationen:


### <a name="basic-functions"></a>Grundfunktionen

| Funktion  | Beschreibung          | Dokumentation|
| -----     | -----     | -----    |
| `microsoftTeams.initialize()` | Initialisiert das SDK. Diese Funktion muss vor anderen SDK-Aufrufen aufgerufen werden.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#initialize-any-&preserve-view=true)|
|`microsoftTeams.getContext(callback: (context: Context)`| Ruft den aktuellen Status ab, in dem die Seite ausgeführt wird. Der Rückruf ruft das **Context-Objekt** ab.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#getcontext--context--context-----void-&preserve-view=true)<br/>[Kontext obj](/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true)|
| `microsoftTeams.initializeWithContext({contentUrl: string, websiteUrl: string})` | Initialisiert die Teams Bibliothek und legt den [Framekontext](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true) der Registerkarte in Abhängigkeit von contentUrl und websiteUrl fest. Dadurch wird sichergestellt, dass die Go-to-Website- oder Reload-Funktionalität mit der richtigen URL funktioniert.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#initializewithframecontext-framecontext--------void--string---&preserve-view=true)|
| `microsoftTeams.setFrameContext({contentUrl: string, websiteUrl: string})` | Legt den [Framekontext](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true) der Registerkarte in Abhängigkeit von contentUrl und websiteUrl fest. Dadurch wird sichergestellt, dass die Go-to-Website- oder Reload-Funktionalität mit der richtigen URL funktioniert.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#setframecontext-framecontext-&preserve-view=true)|
| `microsoftTeams.registerFullScreenHandler(handler: (isFullScreen: boolean)` |Der Handler, der registriert wird, wenn der Benutzer die Vollbild- oder Fensteransicht einer Registerkarte umschaltet.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#registerfullscreenhandler--isfullscreen--boolean-----void-&preserve-view=true)<br/>[boolean](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#registerFullScreenHandler__isFullScreen__boolean_____void_&preserve-view=true)|
|`microsoftTeams.registerChangeSettingsHandler()` |Der Handler, der registriert wird, wenn der Benutzer die aktivierte **Einstellungen-Schaltfläche** zum Neukonfigurieren einer Registerkarte auswählt.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#registerchangesettingshandler-------void-&preserve-view=true)|
| `microsoftTeams.getTabInstances(callback: (tabInfo: TabInformation),tabInstanceParameters?: TabInstanceParameters,)` |Ruft die Registerkarten ab, die im Besitz der App sind. Der Rückruf ruft das **TabInformation-Objekt** ab. Das **TabInstanceParameters-Objekt** ist ein optionaler Parameter.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#gettabinstances--tabinfo--tabinformation-----void--tabinstanceparameters-&preserve-view=true)<br/>[tabInfo obj](/javascript/api/@microsoft/teams-js/tabinformation?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.getMruTabInstances(callback: (tabInfo: TabInformation),tabInstanceParameters?: TabInstanceParameters)`|Ruft die zuletzt verwendeten Registerkarten für den Benutzer ab. Der Rückruf ruft das **TabInformation-Objekt** ab. Das **TabInstanceParameters-Objekt** ist ein optionaler Parameter.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#getmrutabinstances--tabinfo--tabinformation-----void--tabinstanceparameters-&preserve-view=true)<br/>[tabInfo obj](/javascript/api/@microsoft/teams-js/tabinformation?view=msteams-client-js-latest&preserve-view=true)<br/>[tabInstance obj](/javascript/api/@microsoft/teams-js/tabinstanceparameters?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.shareDeepLink(deepLinkParameters: DeepLinkParameters)`|Nimmt das **DeepLinkParameters-Objekt** als Eingabe und gibt ein Dialogfeld für tiefen Verknüpfungen an, mit dem ein Benutzer zu Inhalten *innerhalb der Registerkarte* navigieren kann.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#sharedeeplink-deeplinkparameters-&preserve-view=true)<br/>[deepLink obj](/javascript/api/@microsoft/teams-js/deeplinkparameters?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.executeDeepLink(deepLink: string, onComplete?: (status: boolean, reason?: string))`|Nimmt einen erforderlichen **deepLink** als Eingabe und navigiert Benutzer zu einer URL oder löst eine Clientaktion aus, z. B. das Öffnen oder Installieren einer App *innerhalb Teams*.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#executedeeplink-string---status--boolean--reason---string-----void-&preserve-view=true)|
|`microsoftTeams.navigateToTab(tabInstance: TabInstance, onComplete?: (status: boolean, reason?: string))`|Nimmt das **TabInstance-Objekt** als Eingabe und navigiert zu einer angegebenen Registerkarteninstanz.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#navigatetotab-tabinstance-&preserve-view=true)<br/>[tabInstance obj](/javascript/api/@microsoft/teams-js/tabinstance?view=msteams-client-js-latest&preserve-view=true)|

### <a name="authentication-namespace"></a>Authentifizierungsnamespace

| Funktion  | Beschreibung          | Dokumentation|
| -----     | -----     | -----    |
|`microsoftTeams.authentication.authenticate(authenticateParameters?: AuthenticateParameters)`|Initiiert eine Authentifizierungsanforderung, die ein neues Fenster mit den vom Aufrufer bereitgestellten Parametern öffnet. Optionale Eingabewerte werden durch das **AuthenticateParameters-Objekt** definiert.|[function](/javascript/api/@microsoft/teams-js/authentication?view=msteams-client-js-latest&preserve-view=true)<br/>[auth obj](/javascript/api/@microsoft/teams-js/authenticateparameters?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.authentication.notifySuccess(result?: string, callbackUrl?: string)`|Benachrichtigt den Frame, der die Authentifizierungsanforderung initiiert hat, dass die Anforderung erfolgreich war, und schließt das Authentifizierungsfenster|[function](/javascript/api/@microsoft/teams-js/authentication?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.authentication.notifyFailure(reason?: string, callbackUrl?: string)`|Benachrichtigt den Frame, der die Authentifizierungsanforderung initiiert hat, dass die Anforderung fehlgeschlagen ist, und schließt das Authentifizierungsfenster.|[function](/javascript/api/@microsoft/teams-js/authentication?view=msteams-client-js-latest&preserve-view=true)|

### <a name="settings-namespace"></a>Einstellungen Namespace

| Funktion  | Beschreibung          | Dokumentation|
| -----     | -----     | -----    |
|`microsoftTeams.settings.setValidityState(validityState: boolean)`|Der Anfangswert ist false. Aktiviert die Schaltfläche **Speichern** oder **Entfernen,** wenn der Gültigkeitsstatus wahr ist.|[function](/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.settings.getSettings(callback: (instanceSettings: Settings)`|Ruft die Einstellungen für die aktuelle Instanz ab. Der Rückruf ruft das **Einstellungen-Objekt** ab.|[function](/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest&preserve-view=true)<br/>[Einstellungen obj](/javascript/api/@microsoft/teams-js/_settings?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.settings.setSettings(instanceSettings: Settings, onComplete?: (status: boolean, reason?: string)`|Konfiguriert die Einstellungen für die aktuelle Instanz. Gültige Einstellungen werden durch das **Einstellungen** Objekt definiert.|[function](/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest&preserve-view=true)<br/>[Einstellungen obj](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.settings.registerOnSaveHandler(handler: (evt: SaveEvent)`|Der Handler, der registriert wird, wenn der Benutzer die Schaltfläche **Speichern** auswählt. Dieser Handler sollte verwendet werden, um die zugrunde liegende Ressource zu erstellen oder zu aktualisieren, die den Inhalt anmacht.|[function](/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.settings.registerOnRemoveHandler(handler: (evt: RemoveEvent)`|Der Handler, der registriert wird, wenn der Benutzer die Schaltfläche **Entfernen** auswählt. Dieser Handler sollte verwendet werden, um die zugrunde liegende Ressource zu entfernen, die den Inhalt antreiben kann.|[function](/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest&preserve-view=true)|

### <a name="task-modules-namespace"></a>Taskmodule Namespace

| Funktion  | Beschreibung          | Dokumentation|
| -----     | -----     | -----    |
|`microsoftTeams.tasks.startTask(taskInfo: TaskInfo, submitHandler?: (err: string, result: string)`|Nimmt das **TaskInfo-Objekt** als Eingabe und ermöglicht es einer App, das Aufgabenmodul zu öffnen. Der optionale **submitHandler** wird registriert, wenn das Taskmodul abgeschlossen ist. |[function](/javascript/api/@microsoft/teams-js/tasks?view=msteams-client-js-latest&preserve-view=true)<br/>[taskInfo obj](/javascript/api/@microsoft/teams-js/taskinfo?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.tasks.submitTask(result?: string | object, appIds?: string | string[])`|Sendet das Aufgabenmodul. Der optionale **Result** String-Parameter ist das Ergebnis, das an den Bot oder die App gesendet wird, und ist in der Regel ein JSON-Objekt oder eine Serialisierung. Der **optionale appIds-Zeichenfolgen-** oder Zeichenfolgenarrayparameter hilft bei der Überprüfung, dass der Aufruf von derselben appId stammt wie die, die das Taskmodul aufgerufen hat.|[function](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true)|
