---
title: Erstellen einer Seite zum Entfernen von Registerkarten
author: laujan
description: So erstellen Sie eine Registerkarte zum Entfernen von Registerkarten
keywords: Teams Registerkarten Gruppenkanal konfigurierbar entfernen löschen
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

Sie können die Benutzerfreundlichkeit erweitern und verbessern, indem Sie Entfernungs- und Änderungsoptionen in Ihrer App unterstützen. Teams ermöglicht benutzern das Umbenennen oder Entfernen einer Kanal-/Gruppenregisterkarte, und Sie können Benutzern erlauben, die Registerkarte nach der Installation neu zu konfigurieren. Darüber hinaus kann Ihre Registerkartenentfernungserfahrung die Angabe dessen umfassen, was mit dem Inhalt geschieht, wenn Ihre Registerkarte entfernt wird, oder Benutzern Optionen für das Nachentfernen nach dem Entfernen wie Löschen oder Archivieren des Inhalts zu geben.

## <a name="enable-your-tab-to-be-reconfigured-after-installation"></a>Aktivieren Sie die Neukonfiguration der Registerkarte nach der Installation

Ihre **manifest.jsauf** definiert die Funktionen und Funktionen Ihrer Registerkarte. Die Tabstoppinstanzeigenschaft `canUpdateConfiguration` nimmt einen booleschen Wert an, der angibt, ob ein Benutzer die Registerkarte ändern oder neu konfigurieren kann, nachdem sie erstellt wurde:

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`canUpdateConfiguration`|Boolescher Wert|||Ein Wert, der angibt, ob eine Instanz der Registerkartenkonfiguration vom Benutzer nach der Erstellung aktualisiert werden kann. Standard: `true`|

Wenn Ihre Registerkarte in einen Kanal- oder Gruppenchat hochgeladen wird, wird Teams ein Dropdown-Menü mit rechts klicken. Die verfügbaren Optionen werden durch die `canUpdateConfiguration` Einstellung bestimmt:

| `canUpdateConfiguration`| true   | false | description |
| ----------------------- | :----: | ----- | ----------- |
|     Einstellungen            |   √    |       |Die `configurationUrl` Seite wird in einem IFrame neu geladen, sodass der Benutzer die Registerkarte neu konfigurieren kann.  |
|     Umbenennen              |   √    |   √   | Der Benutzer kann den Tabnamen so ändern, wie er in der Registerkartenleiste angezeigt wird.          |
|     Entfernen              |   √    |   √   |  Wenn die Eigenschaft und der  `removeURL` Wert auf der **Konfigurationsseite** enthalten sind, wird die **Entfernungsseite** in einen IFrame geladen und dem Benutzer angezeigt. Wenn eine Entfernungsseite nicht enthalten ist, wird dem Benutzer ein Dialogfeld bestätigen angezeigt.          |
|||||

## <a name="create-a-tab-removal-page-for-your-application"></a>Erstellen einer Registerkarte zum Entfernen ihrer Anwendung

Die optionale Entfernungsseite ist eine HTML-Seite, die Sie hosten und beim Entfernen der Registerkarte angezeigt wird. Die URL der Entfernungsseite wird von der `setSettings()` Methode auf der Konfigurationsseite festgelegt. Wie bei allen Seiten in Ihrer App muss die Entfernungsseite [Teams Tabstoppanforderungen](../../../tabs/how-to/tab-requirements.md)entsprechen.

### <a name="register-a-remove-handler"></a>Registrieren eines Remove-Handlers

Optional können Sie in der Entfernerlogik den Ereignishandler aufrufen, `registerOnRemoveHandler((RemoveEvent) => {}` wenn der Benutzer eine vorhandene Registerkartenkonfiguration entfernt. Die Methode nimmt die [`RemoveEvent`](/javascript/api/@microsoft/teams-js/microsoftteams.settings.removeevent?view=msteams-client-js-latest&preserve-view=true) Schnittstelle auf und führt den Code im Handler aus, wenn ein Benutzer versucht, Inhalte zu entfernen. Es wird verwendet, um Bereinigungsvorgänge durchzuführen, z. B. das Entfernen der zugrunde liegenden Ressource, die den Tabstoppinhalt anmacht. Es kann jeweils nur ein Remove-Handler registriert werden.

Die `RemoveEvent` Schnittstelle beschreibt ein Objekt mit zwei Methoden:

* Die `notifySuccess()` Funktion ist erforderlich. Es zeigt an, dass das Entfernen der zugrunde liegenden Ressource erfolgreich war und ihr Inhalt entfernt werden kann.

* Die `notifyFailure(string)` Funktion ist optional. Es weist darauf hin, dass das Entfernen der zugrunde liegenden Ressource fehlgeschlagen ist und ihr Inhalt nicht entfernt werden kann. Der optionale Zeichenfolgenparameter gibt einen Grund für den Fehler an. Falls angegeben, wird diese Zeichenfolge dem Benutzer angezeigt. Andernfalls wird ein generischer Fehler angezeigt.

#### <a name="use-the-getsettings-function"></a>Verwenden Sie die `getSettings()` Funktion

Sie können `getSettings()` den zu entfernenden Tabstoppinhalt festlegen. Die Funktion nimmt die ein `getSettings((Settings) =>{})` und stellt die gültigen [`Settings interface`](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true) Einstellungseigenschaftswerte bereit, die abgerufen werden können.

#### <a name="use-the-getcontext-function"></a>Verwenden Sie die `getContext()` Funktion

Sie können `getContext()` verwenden, um den aktuellen Kontext abzurufen, in dem der Frame ausgeführt wird. Die Funktion nimmt die ein `getContext((Context) =>{})` [`Context interface`](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true) und stellt gültige `Context` Eigenschaftswerte bereit, die Sie in der Seitenlogik zum Entfernen verwenden können, um den Inhalt zu bestimmen, der auf der Entfernungsseite angezeigt werden soll.

#### <a name="include-authentication"></a>Authentifizierung einschließen

Möglicherweise benötigen Sie eine Authentifizierung, bevor Sie einem Benutzer das Löschen des Registerkarteninhalts gestatten. Kontextinformationen können verwendet werden, um Authentifizierungsanforderungen und Autorisierungsseiten-URLs zu erstellen. Weitere Informationen [finden Sie unter Microsoft Teams Authentifizierungsablauf für Registerkarten](~/tabs/how-to/authentication/auth-flow-tab.md). Stellen Sie sicher, dass alle Domänen, die auf den Registerkarten verwendet werden, im Array aufgeführt `manifest.json` `validDomains` sind.

Unten ist ein Beispiel Tab-Entfernung Code-Block:

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

Wenn ein Benutzer aus dem Dropdown-Menü der Registerkarte **Entfernen** auswählt, lädt Teams die optionale `removeUrl` Seite (die auf der **Konfigurationsseite** angegeben ist) in einen IFrame. Hier wird dem Benutzer eine Schaltfläche angezeigt, die mit der Funktion geladen ist, die `onClick()` aufruft `microsoftTeams.settings.setValidityState(true)` und die Schaltfläche **Entfernen** am unteren Rand der Entfernungsseite IFrame aktiviert.

Nach der Ausführung des Remove-Handlers `removeEvent.notifySuccess()` oder benachrichtigt Teams des `removeEvent.notifyFailure()` Inhaltsentfernungsergebnisses.

>[!NOTE]
> * Um sicherzustellen, dass die Kontrolle eines autorisierten Benutzers über eine Registerkarte nicht gehemmt wird, entfernt Teams die Registerkarte sowohl in Erfolgs- als auch in Fehlerfällen.
> * Teams aktiviert die **Schaltfläche Entfernen** nach 5 Sekunden, auch wenn Ihre Registerkarte nicht aufgerufen `setValidityState()` hat.
> * Wenn der Benutzer **Teams** entfernen auswählt, wird die Registerkarte nach 30 Sekunden entfernt, unabhängig davon, ob Ihre Aktionen abgeschlossen wurden.
