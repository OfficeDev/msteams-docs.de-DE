---
title: Erstellen von Registerkarten und anderen gehosteten Erfahrungen mit dem JavaScript-Client-SDK
author: heath-hamilton
ms.author: surbhigupta
description: Übersicht über das Microsoft Teams JavaScript-Client-SDK, das Sie beim Erstellen von Teams-App-Erfahrungen unterstützt, die in einem <iframe>.
keywords: Gruppenkanal für Teamregisterkarten, konfigurierbares statisches SDK JavaScript Personal
ms.topic: conceptual
ms.openlocfilehash: 7ba900990507e2d32992d6d2c26fff07d7c84bd8
ms.sourcegitcommit: fa64b83c0b534bf7a89f256880d5b5ca193e4b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/28/2021
ms.locfileid: "50036997"
---
# <a name="building-tabs-and-other-hosted-experiences-with-the-microsoft-teams-javascript-client-sdk"></a>Erstellen von Registerkarten und anderen gehosteten Erfahrungen mit dem Microsoft Teams JavaScript-Client-SDK

Das JavaScript-Client-SDK von Microsoft Teams kann Ihnen dabei helfen, gehostete Erfahrungen in Teams zu erstellen, was bedeutet, Dass Ihre App-Inhalte in einem iframe angezeigt werden.

Das SDK ist hilfreich für die Entwicklung von Apps mit einer der folgenden Teams-Funktionen:

* [Registerkarten](../../tabs/what-are-tabs.md)
* [Aufgabenmodule](../../task-modules-and-cards/what-are-task-modules.md)

Beispielsweise kann das SDK [](../../build-your-first-app/build-personal-tab.md#3-update-the-tab-theme) Ihre Registerkarte auf Designänderungen reagieren lassen, die Ihre Benutzer im Teams-Client vornehmen.

## <a name="getting-started"></a>Erste Schritte

Gehen Sie abhängig von Ihren Entwicklungseinstellungen wie folgt vor:

* [Installieren des SDK mit npm oder Einem](https://docs.microsoft.com/javascript/api/overview/msteams-client?view=msteams-client-js-latest)
* [Klonen des SDK (GitHub)](https://github.com/OfficeDev/microsoft-teams-library-js)

## <a name="common-sdk-functions"></a>Allgemeine SDK-Funktionen

In den folgenden Tabellen finden Sie Informationen zu häufig verwendeten SDK-Funktionen. Die [SDK-Referenzdokumentation](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest) bietet umfassendere Informationen.

### <a name="basic-functions"></a>Grundlegende Funktionen

| Funktion  | Beschreibung          | Dokumentation|
| -----     | -----     | -----    |
| `microsoftTeams.initialize()` | Initialisiert das SDK. Diese Funktion muss vor anderen SDK-Aufrufen aufgerufen werden.|[function](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#initialize-any-&preserve-view=true)|
|`microsoftTeams.getContext(callback: (context: Context)`| Ruft den aktuellen Status ab, in dem die Seite ausgeführt wird. Der Rückruf ruft das **Context -Objekt** ab.|[function](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#getcontext--context--context-----void-&preserve-view=true)<br/>[context obj](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true)|
| `microsoftTeams.initializeWithContext({contentUrl: string, websiteUrl: string})` | Initialisiert die Teams-Bibliothek und legt [](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true) den Framekontext der Registerkarte abhängig von "contentUrl" und "websiteUrl" fest. Dadurch wird sichergestellt, dass die Go-to-Website-/Neuladefunktionalität auf der richtigen URL funktioniert.|[function](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#initializewithframecontext-framecontext--------void--string---&preserve-view=true)|
| `microsoftTeams.setFrameContext({contentUrl: string, websiteUrl: string})` | Legt den Framekontext der Registerkarte [abhängig](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true) von "contentUrl" und "websiteUrl" fest. Dadurch wird sichergestellt, dass die Go-to-Website-/Neuladefunktionalität auf der richtigen URL funktioniert.|[function](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#setframecontext-framecontext-&preserve-view=true)|
| `microsoftTeams.registerFullScreenHandler(handler: (isFullScreen: boolean)` |Der Handler, der registriert wird, wenn der Benutzer die Vollbild-/Fensteransicht einer Registerkarte einschaltet.|[function](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#registerfullscreenhandler--isfullscreen--boolean-----void-&preserve-view=true)<br/>[boolean](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#registerFullScreenHandler__isFullScreen__boolean_____void_&preserve-view=true)|
|`microsoftTeams.registerChangeSettingsHandler()` |Der Handler, der registriert wird,  wenn der Benutzer die Schaltfläche "Einstellungen" auswählt, um eine Registerkarte neu zu konfigurieren.|[function](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#registerchangesettingshandler-------void-&preserve-view=true)|
| `microsoftTeams.getTabInstances(callback: (tabInfo: TabInformation),tabInstanceParameters?: TabInstanceParameters,)` |Ruft die Registerkarten ab, die der App gehören. Der Rückruf ruft das **TabInformation -Objekt** ab. Das **TabInstanceParameters -Objekt** ist ein optionaler Parameter.|[function](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#gettabinstances--tabinfo--tabinformation-----void--tabinstanceparameters-&preserve-view=true)<br/>[tabInfo obj](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/tabinformation?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.getMruTabInstances(callback: (tabInfo: TabInformation),tabInstanceParameters?: TabInstanceParameters)`|Ruft die zuletzt verwendeten Registerkarten für den Benutzer ab. Der Rückruf ruft das **TabInformation -Objekt** ab. Das **TabInstanceParameters -Objekt** ist ein optionaler Parameter.|[function](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#getmrutabinstances--tabinfo--tabinformation-----void--tabinstanceparameters-&preserve-view=true)<br/>[tabInfo obj](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/tabinformation?view=msteams-client-js-latest&preserve-view=true)<br/>[tabInstance obj](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/tabinstanceparameters?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.shareDeepLink(deepLinkParameters: DeepLinkParameters)`|Übernimmt **das DeepLinkParameters -Objekt** als Eingabe und gibt ein Dialogfeld für einen Deep Link weiter, das ein Benutzer verwenden kann, um zu Inhalten auf der *Registerkarte zu navigieren.*|[function](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#sharedeeplink-deeplinkparameters-&preserve-view=true)<br/>[deepLink obj](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/deeplinkparameters?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.executeDeepLink(deepLink: string, onComplete?: (status: boolean, reason?: string))`|Verwendet einen erforderlichen **deepLink** als Eingabe und navigiert den Benutzer zu einer URL oder löst eine Clientaktion aus, z. B. das Öffnen oder Installieren einer *App in Teams.*|[function](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#executedeeplink-string---status--boolean--reason---string-----void-&preserve-view=true)|
|`microsoftTeams.navigateToTab(tabInstance: TabInstance, onComplete?: (status: boolean, reason?: string))`|Übernimmt **das TabInstance -Objekt** als Eingabe und navigiert zu einer angegebenen Registerkarteninstanz.|[function](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#navigatetotab-tabinstance-&preserve-view=true)<br/>[tabInstance obj](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/tabinstance?view=msteams-client-js-latest&preserve-view=true)|

### <a name="authentication-namespace"></a>Authentifizierungsnamespace

| Funktion  | Beschreibung          | Dokumentation|
| -----     | -----     | -----    |
|`microsoftTeams.authentication.authenticate(authenticateParameters?: AuthenticateParameters)`|Initiiert eine Authentifizierungsanforderung, die ein neues Fenster mit den vom Aufrufer bereitgestellten Parametern öffnet. Optionale Eingabewerte werden durch das **AuthenticateParameters -Objekt** definiert.|[function](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/authentication?view=msteams-client-js-latest&preserve-view=true)<br/>[auth obj](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/authenticateparameters?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.authentication.notifySuccess(result?: string, callbackUrl?: string)`|Benachrichtigt den Frame, der die Authentifizierungsanforderung initiiert hat, darüber, dass die Anforderung erfolgreich war, und schließt das Authentifizierungsfenster.|[function](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/authentication?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.authentication.notifyFailure(reason?: string, callbackUrl?: string)`|Benachrichtigt den Frame, der die Authentifizierungsanforderung initiiert hat, über einen Fehler bei der Anforderung und schließt das Authentifizierungsfenster.|[function](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/authentication?view=msteams-client-js-latest&preserve-view=true)|

### <a name="settings-namespace"></a>Einstellungsnamespace

| Funktion  | Beschreibung          | Dokumentation|
| -----     | -----     | -----    |
|`microsoftTeams.settings.setValidityState(validityState: boolean)`|Der Anfangswert ist "false". Aktiviert die Schaltfläche **"Speichern"** oder **"Entfernen",** wenn der Gültigkeitsstatus "true" ist.|[function](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.settings.getSettings(callback: (instanceSettings: Settings)`|Ruft die Einstellungen für die aktuelle Instanz ab. Der Rückruf ruft das Settings **-Objekt** ab.|[function](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest&preserve-view=true)<br/>[settings obj](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/_settings?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.settings.setSettings(instanceSettings: Settings, onComplete?: (status: boolean, reason?: string)`|Konfiguriert die Einstellungen für die aktuelle Instanz. Gültige Einstellungen werden durch das **Settings -Objekt** definiert.|[function](/https://docs.microsoft.com/en-us/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest)<br/>[settings obj](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.settings.registerOnSaveHandler(handler: (evt: SaveEvent)`|Der Handler, der registriert wird, wenn der Benutzer die Schaltfläche **"Speichern"** auswählt. Dieser Handler sollte verwendet werden, um die zugrunde liegende Ressource zu erstellen oder zu aktualisieren, die den Inhalt an die Macht macht.|[function](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.settings.registerOnRemoveHandler(handler: (evt: RemoveEvent)`|Der Handler, der registriert wird, wenn der Benutzer die Schaltfläche **"Entfernen"** auswählt. Dieser Handler sollte verwendet werden, um die zugrunde liegende Ressource zu entfernen, die den Inhalt an die Macht macht.|[function](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest&preserve-view=true)|

### <a name="task-modules-namespace"></a>Namespace für Aufgabenmodule

| Funktion  | Beschreibung          | Dokumentation|
| -----     | -----     | -----    |
|`microsoftTeams.tasks.startTask(taskInfo: TaskInfo, submitHandler?: (err: string, result: string)`|Übernimmt **das TaskInfo -Objekt** als Eingabe und ermöglicht einer App, das Aufgabenmodul zu öffnen. Der optionale **submitHandler** wird registriert, wenn das Aufgabenmodul abgeschlossen ist. |[function](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/tasks?view=msteams-client-js-latest&preserve-view=true)<br/>[taskInfo obj](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/taskinfo?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.tasks.submitTask(result?: string | object, appIds?: string | string[])`|Sendet das Aufgabenmodul. Der optionale **Ergebniszeichenfolgenparameter** ist das an den Bot oder die App gesendete Ergebnis und ist in der Regel ein #A0 oder eine Serialisierung. Der optionale **appIds-Zeichenfolgen-** oder Zeichenfolgenarrayparameter unterstützt bei der Validierung, ob der Aufruf von derselben appId stammt wie die appId, die das Aufgabenmodul aufgerufen hat.|[function](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true)|
