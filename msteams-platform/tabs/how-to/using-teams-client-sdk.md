---
title: Verwenden des Teams-Client-SDK
author: laujan
description: Vorgehensweise verwenden des Teams-Client-SDK zum Hinzufügen von Teams-fähigen Funktionen zu Ihren benutzerdefinierten Registerkarten
keywords: Teams Tabs Gruppenkanal konfigurierbares statisches SDK JavaScript Personal
ms.topic: conceptual
ms.openlocfilehash: eac5a8ec03ba12d926346afb40ca9bc6e9dda8d6
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674561"
---
# <a name="using-the-teams-client-sdk"></a>Verwenden des Teams-Client-SDK

Das Microsoft Teams-JavaScript- **Client-SDK** und die JavaScript- **Bibliothek für Teams** sind Teil der [Microsoft Teams-Entwicklerplattform](https://msdn.microsoft.com/microsoft-teams) und stellen Tools und Prozesse zur Verfügung, um die Anwendungserstellung für Teams zu vereinfachen. Das Microsoft Teams-Client-SDK wird als NPM-Paket verteilt. Die neueste Version finden Sie hier: <https://www.npmjs.com/package/@microsoft/teams-js>. Die Microsoft Teams-Bibliothek befindet <https://github.com/OfficeDev/microsoft-teams-library-js>sich unter.

In der folgenden Tabelle werden die in der Entwicklung von Tabs üblicherweise verwendeten Teams-Bibliotheksfunktionen beschrieben:

## <a name="teams-sdk-public-api"></a>Öffentliche Microsoft Teams SDK-API 

| Funktion  | Beschreibung          | Dokumentation|
| -----     | -----     | -----    | -----        |
| `microsoftTeams.initialize()` | Initialisiert die Teams-Bibliothek. Diese Funktion muss vor anderen SDK-aufrufen aufgerufen werden.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#initialize-any-)|
|`microsoftTeams.getContext(callback: (context: Context)`| Ruft den aktuellen Zustand ab, in dem die Seite läuft. Der Rückruf Ruft das **context** -Objekt ab.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#getcontext--context--context-----void-)<br/>[Kontext-obj](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest)|
| `microsoftTeams.registerFullScreenHandler(handler: (isFullScreen: boolean)` |Der Handler, der registriert wird, wenn der Benutzer die Vollbildansicht/Fenster Ansicht eines Tabs umschalten kann.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#registerfullscreenhandler--isfullscreen--boolean-----void-)<br/>[boolean](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest#isfullscreen)|
|`microsoftTeams.registerChangeSettingsHandler()` |Der Handler, der registriert wird, wenn der Benutzer die Schaltfläche "aktivierte **Einstellungen** " auswählt, um eine Registerkarte neu zu konfigurieren.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#registerchangesettingshandler-------void-)|
| `microsoftTeams.getTabInstances(callback: (tabInfo: TabInformation),tabInstanceParameters?: TabInstanceParameters,)` |Ruft die Registerkarten im Besitz der App ab. Der Rückruf Ruft das **TabInformation** -Objekt ab. Das **TabInstanceParameters** -Objekt ist ein optionaler Parameter.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#gettabinstances--tabinfo--tabinformation-----void--tabinstanceparameters-)<br/>[TabInfo obj](/javascript/api/@microsoft/teams-js/microsoftteams.tabinformation?view=msteams-client-js-latest)|
|`microsoftTeams.getMruTabInstances(callback: (tabInfo: TabInformation),tabInstanceParameters?: TabInstanceParameters)`|Ruft die zuletzt verwendeten Registerkarten für den Benutzer ab. Der Rückruf Ruft das **TabInformation** -Objekt ab. Das **TabInstanceParameters** -Objekt ist ein optionaler Parameter.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#getmrutabinstances--tabinfo--tabinformation-----void--tabinstanceparameters-)<br/>[TabInfo obj](/javascript/api/@microsoft/teams-js/microsoftteams.teaminformation?view=msteams-client-js-latest)<br/>[tabInstance obj](/javascript/api/@microsoft/teams-js/microsoftteams.tabinstanceparameters?view=msteams-client-js-latest)|
|`microsoftTeams.shareDeepLink(deepLinkParameters: DeepLinkParameters)`|Das **DeepLinkParameters** -Objekt wird als Eingabe verwendet, und es wird ein Dialogfeld Deep Link gemeinsam verwendet, mit dem ein Benutzer zu Inhalten *innerhalb der Registerkarte*navigieren kann.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#sharedeeplink-deeplinkparameters-)<br/>[deepLink obj](/javascript/api/@microsoft/teams-js/microsoftteams.deeplinkparameters?view=msteams-client-js-latest)|
|`microsoftTeams.executeDeepLink(deepLink: string, onComplete?: (status: boolean, reason?: string))`|Akzeptiert eine erforderliche **deepLink** als Eingabe und navigiert Benutzer zu einer URL oder löst eine Clientaktion aus – beispielsweise öffnen oder installieren – eine APP *in Microsoft Teams*.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#executedeeplink-string---status--boolean--reason---string-----void-)|
|`microsoftTeams.navigateToTab(tabInstance: TabInstance, onComplete?: (status: boolean, reason?: string))`|Das **TabInstance** -Objekt wird als Eingabe verwendet und zu einer angegebenen Registerkarten Instanz navigiert.|[function](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#navigatetotab-tabinstance-)<br/>[tabInstance obj](/javascript/api/@microsoft/teams-js/microsoftteams.tabinstance?view=msteams-client-js-latest)|

## <a name="authentication-namespace"></a>Authentifizierungs Namespace

| Funktion  | Beschreibung          | Dokumentation|
| -----     | -----     | -----    | -----        |
|`microsoftTeams.authentication.authenticate(authenticateParameters?: AuthenticateParameters)`|Initiiert eine Authentifizierungsanforderung, die ein neues Fenster mit den vom Aufrufer bereitgestellten Parametern öffnet. Optionale Eingabewerte werden durch das **AuthenticateParameters** -Objekt definiert.|[function](/javascript/api/@microsoft/teams-js/microsoftteams.authentication?view=msteams-client-js-latest#authenticate-authenticateparameters-)<br/>[Authentifizierungs-obj](/javascript/api/@microsoft/teams-js/microsoftteams.authentication.authenticateparameters?view=msteams-client-js-latest)|
|`microsoftTeams.authentication.notifySuccess(result?: string, callbackUrl?: string)`|Benachrichtigt den Frame, der die Authentifizierungsanforderung initiiert hat, dass die Anforderung erfolgreich war, und schließt das Authentifizierungsfenster|[function](/javascript/api/@microsoft/teams-js/microsoftteams.authentication?view=msteams-client-js-latest#notifysuccess-string--string-)|
|`microsoftTeams.authentication.notifyFailure(reason?: string, callbackUrl?: string)`|Benachrichtigt den Frame, der die Authentifizierungsanforderung initiiert hat, dass die Anforderung fehlgeschlagen ist, und schließt das Authentifizierungsfenster.|[function](/javascript/api/@microsoft/teams-js/microsoftteams.authentication?view=msteams-client-js-latest#notifyfailure-string--string-)|

## <a name="settings-namespace"></a>Namespace "Settings"

| Funktion  | Beschreibung          | Dokumentation|
| -----     | -----     | -----    | -----        |
|`microsoftTeams.settings.setValidityState(validityState: boolean)`|Der Anfangswert ist false. Aktiviert die Schaltfläche **Speichern** oder **Entfernen** , wenn der Gültigkeitsstatus auf true festgelegt ist.|[function](/javascript/api/@microsoft/teams-js/microsoftteams.settings?view=msteams-client-js-latest#setvaliditystate-boolean-)|
|`microsoftTeams.settings.getSettings(callback: (instanceSettings: Settings)`|Ruft die Einstellungen für die aktuelle Instanz ab. Der Rückruf Ruft das **Settings** -Objekt ab.|[function](/javascript/api/@microsoft/teams-js/microsoftteams.settings?view=msteams-client-js-latest#getsettings--instancesettings--settings-----void-)<br/>[obj-Einstellungen](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest)|
|`microsoftTeams.settings.setSettings(instanceSettings: Settings, onComplete?: (status: boolean, reason?: string)`|Konfiguriert die Einstellungen für die aktuelle Instanz. Gültige Einstellungen werden durch das **Settings** -Objekt definiert.|[function](/javascript/api/@microsoft/teams-js/microsoftteams.settings?view=msteams-client-js-latest#setsettings-settings-)<br/>[obj-Einstellungen](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest)|
|`microsoftTeams.settings.registerOnSaveHandler(handler: (evt: SaveEvent)`|Der Handler, der registriert wird, wenn der Benutzer die Schaltfläche **Speichern** auswählt. Dieser Handler sollte verwendet werden, um die zugrunde liegende Ressource, die den Inhalt einmacht, zu erstellen oder zu aktualisieren.|[function](/javascript/api/@microsoft/teams-js/microsoftteams.settings?view=msteams-client-js-latest#registeronsavehandler--evt--saveevent-----void-)|
|`microsoftTeams.settings.registerOnRemoveHandler(handler: (evt: RemoveEvent)`|Der Handler, der registriert wird, wenn der Benutzer die Schaltfläche **Entfernen** auswählt. Dieser Handler sollte verwendet werden, um die zugrunde liegende Ressource zu entfernen, die den Inhalt einmacht.|[function](/javascript/api/@microsoft/teams-js/microsoftteams.settings?view=msteams-client-js-latest#registeronremovehandler--evt--removeevent-----void-)|

## <a name="tasks-namespace"></a>Aufgaben-Namespace

| Funktion  | Beschreibung          | Dokumentation|
| -----     | -----     | -----    | -----        |
|`microsoftTeams.tasks.startTask(taskInfo: TaskInfo, submitHandler?: (err: string, result: string)`|Das **taskinfo** -Objekt wird als Eingabe verwendet und ermöglicht einer APP das Öffnen des Aufgabenmoduls. Das optionale **submitHandler** wird registriert, wenn der Aufgabenmodul abgeschlossen ist. |[function](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#starttask-taskinfo---err--string--result--string-----void-)<br/>[taskInfo obj](/javascript/api/@microsoft/teams-js/microsoftteams.taskinfo?view=msteams-client-js-latest)|
|`microsoftTeams.tasks.submitTask(result?: string | object, appIds?: string | string[])`|Sendet das Aufgabenmodul. Der optionale **Ergebnis** Zeichenfolgen-Parameter ist das Ergebnis, das an den bot oder die APP gesendet wurde, und ist in der Regel ein JSON-Objekt oder eine Serialisierung; Die optionale Zeichenfolge oder der String-Arrayparameter für die **Zeichenfolgengruppe** hilft bei der Überprüfung, dass der Aufruf von der gleichen Webanwendung stammt wie diejenige, die den Aufgabenmodul aufgerufen hat.|[function](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---)|