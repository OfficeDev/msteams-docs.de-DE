---
title: Erstellen einer Seite zum Entfernen von Registerkarten
author: laujan
description: Erstellen einer Seite zum Entfernen von Registerkarten
keywords: teams tabs group channel configurable remove delete
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: e1a1f38a2bcb3b5bc4bc54f469c8727e44d8695e
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566670"
---
# <a name="modify-or-remove-a-channel-group-tab"></a>Ändern oder Entfernen einer Kanalgruppenregisterkarte

Sie können die Benutzeroberfläche erweitern und verbessern, indem Sie Entfernungs- und Änderungsoptionen in Ihrer App unterstützen. Teams ermöglicht Benutzern das Umbenennen oder Entfernen einer Kanal-/Gruppenregisterkarte, und Sie können Benutzern erlauben, Ihre Registerkarte nach der Installation neu zu konfigurieren. Darüber hinaus kann ihre Registerkartenentfernungserfahrung das Festlegen der Inhalte beim Entfernen der Registerkarte oder das Festlegen von Optionen nach dem Entfernen von Inhalten wie löschen oder Archivieren des Inhalts umfassen.

## <a name="enable-your-tab-to-be-reconfigured-after-installation"></a>Aktivieren der Neukonfiguration ihrer Registerkarte nach der Installation

Ihre **manifest.jsdefiniert** die Features und Funktionen Ihrer Registerkarte. Die Tab-Instanz-Eigenschaft verwendet einen booleschen Wert, der angibt, ob ein Benutzer die Registerkarte ändern oder neu konfigurieren `canUpdateConfiguration` kann, nachdem sie erstellt wurde:

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`canUpdateConfiguration`|Boolescher Wert|||Ein Wert, der angibt, ob eine Instanz der Registerkartenkonfiguration vom Benutzer nach der Erstellung aktualisiert werden kann. Standard: `true`|

Wenn Ihre Registerkarte in einen Kanal- oder Gruppenchat hochgeladen wird, Teams sie ein Dropdownmenü mit der rechten Maustaste für Ihre Registerkarte hinzufügen. Die verfügbaren Optionen werden durch die Einstellung `canUpdateConfiguration` bestimmt:

| `canUpdateConfiguration`| true   | false | description |
| ----------------------- | :----: | ----- | ----------- |
|     Einstellungen            |   √    |       |Die Seite wird in einem IFrame neu `configurationUrl` geladen, sodass der Benutzer die Registerkarte neu konfigurieren kann.  |
|     Umbenennen              |   √    |   √   | Der Benutzer kann den Namen der Registerkarte ändern, wie er in der Registerkartenleiste angezeigt wird.          |
|     Entfernen              |   √    |   √   |  Wenn die Eigenschaft und der Wert auf der Konfigurationsseite enthalten sind, wird die Seite zum Entfernen in einen IFrame geladen und dem `removeURL` Benutzer angezeigt.   Wenn keine Entfernungsseite enthalten ist, wird dem Benutzer ein Bestätigungsdialogfeld angezeigt.          |
|||||

## <a name="create-a-tab-removal-page-for-your-application"></a>Erstellen einer Seite zum Entfernen von Registerkarten für Ihre Anwendung

Die optionale Seite zum Entfernen ist eine HTML-Seite, die Sie hosten und die angezeigt wird, wenn die Registerkarte entfernt wird. Die URL der Entfernungsseite wird von der `setSettings()` Methode auf der Konfigurationsseite festgelegt. Wie bei allen Seiten in Ihrer App muss die Seite zum Entfernen die Teams [erfüllen.](../../../tabs/how-to/tab-requirements.md)

### <a name="register-a-remove-handler"></a>Registrieren eines Remove-Handlers

Optional können Sie innerhalb der Logik der Entfernungsseite den Ereignishandler aufrufen, wenn der Benutzer `registerOnRemoveHandler((RemoveEvent) => {}` eine vorhandene Registerkartenkonfiguration entfernt. Die -Methode übernimmt die Schnittstelle und führt den Code im Handler aus, wenn ein Benutzer versucht, [`RemoveEvent`](/javascript/api/@microsoft/teams-js/microsoftteams.settings.removeevent?view=msteams-client-js-latest&preserve-view=true) Inhalte zu entfernen. Es wird verwendet, um Bereinigungsvorgänge durchzuführen, z. B. das Entfernen der zugrunde liegenden Ressource, die den Registerkarteninhalt nutzt. Es kann immer nur ein Remove-Handler registriert werden.

Die `RemoveEvent` Schnittstelle beschreibt ein Objekt mit zwei Methoden:

* Die `notifySuccess()` Funktion ist erforderlich. Es gibt an, dass das Entfernen der zugrunde liegenden Ressource erfolgreich war und deren Inhalt entfernt werden kann.

* Die `notifyFailure(string)` Funktion ist optional. Es gibt an, dass das Entfernen der zugrunde liegenden Ressource fehlgeschlagen ist und deren Inhalt nicht entfernt werden kann. Der optionale String-Parameter gibt einen Grund für den Fehler an. Wenn angegeben, wird diese Zeichenfolge dem Benutzer angezeigt. Andernfalls wird ein allgemeiner Fehler angezeigt.

#### <a name="use-the-getsettings-function"></a>Verwenden der `getSettings()` Funktion

Sie können den `getSettings()` zu entfernende Registerkarteninhalt festlegen. Die `getSettings((Settings) =>{})` Funktion übernimmt [`Settings interface`](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true) die und stellt die gültigen Einstellungseigenschaftswerte zur Verfügung, die abgerufen werden können.

#### <a name="use-the-getcontext-function"></a>Verwenden der `getContext()` Funktion

Sie können den `getContext()` aktuellen Kontext abrufen, in dem der Frame ausgeführt wird. Die Funktion übernimmt die und stellt gültige Eigenschaftswerte zur Verfügung, die Sie in der Logik der Entfernungsseite verwenden können, um den Inhalt zu bestimmen, der auf der `getContext((Context) =>{})` [`Context interface`](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true) Entfernungsseite angezeigt werden `Context` soll.

#### <a name="include-authentication"></a>Schließen Sie die Authentifizierung ein

Möglicherweise benötigen Sie eine Authentifizierung, bevor ein Benutzer den Registerkarteninhalt löschen kann. Kontextinformationen können zum Erstellen von Authentifizierungsanforderungen und Autorisierungsseiten-URLs verwendet werden. Weitere [Microsoft Teams finden Sie unter Authentifizierungsfluss für Registerkarten](~/tabs/how-to/authentication/auth-flow-tab.md). Stellen Sie sicher, dass alle auf Ihren Registerkartenseiten verwendeten Domänen im Array `manifest.json` `validDomains` aufgeführt sind.

Nachfolgend finden Sie einen Beispielcodeblock zum Entfernen von Registerkarten:

```html
<body>
  <button onclick="onClick()">Delete this tab and all underlying data?</button>
  <script>
    microsoftTeams.initialize();
    microsoftTeams.settings.registerOnRemoveHandler((removeEvent) => {
      // Here you can designate the tab content to be removed and/or archived.
        microsoftTeams.settings.getSettings((settings) => {
        settings.contentUrl = "..."
        });
        removeEvent.notifySuccess();
    });

    const onClick() => {
        microsoftTeams.settings.setValidityState(true);
    }
  </script>
</body>

```

Wenn ein Benutzer  aus dem Dropdownmenü der Registerkarte entfernen auswählt, wird Teams die optionale Seite (auf Ihrer Konfigurationsseite festgelegt) in einen `removeUrl` IFrame geladen.  Hier wird dem Benutzer eine Schaltfläche angezeigt, die mit der Funktion geladen ist, die die Schaltfläche Entfernen aufruft und aktiviert, die sich am unteren Rand der `onClick()` `microsoftTeams.settings.setValidityState(true)` Entfernungsseite IFrame befindet. 

Nach der Ausführung des Remove-Handlers oder benachrichtigt Teams das Ergebnis `removeEvent.notifySuccess()` `removeEvent.notifyFailure()` der Inhaltsentfernung.

>[!NOTE]
> * Um sicherzustellen, dass das Steuerelement eines autorisierten Benutzers über eine Registerkarte nicht gehemmt wird, Teams die Registerkarte sowohl in Erfolgs- als auch in Fehlerfällen entfernt.\
> * Teams aktiviert die **Schaltfläche Entfernen** nach 5 Sekunden, auch wenn Ihre Registerkarte nicht aufgerufen `setValidityState()` wurde.\
> * Wenn der Benutzer Remove **Teams** entfernt die Registerkarte nach 30 Sekunden, unabhängig davon, ob Ihre Aktionen abgeschlossen wurden.
