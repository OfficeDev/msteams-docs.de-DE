---
title: Erstellen einer Seite zum Entfernen von Registerkarten
author: surbhigupta
description: So erstellen Sie eine Seite zum Entfernen von Registerkarten
keywords: Teams-Registerkarten Gruppenkanal konfigurierbare Löschung entfernen
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 9f4e10bd8fd5b5c4caf8f5349e0952732821dd85
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069055"
---
# <a name="modify-or-remove-a-channel-group-tab"></a>Ändern oder Entfernen einer Kanalgruppenregisterkarte

Sie können die Benutzererfahrung erweitern und verbessern, indem Sie Entfernungs- und Änderungsoptionen in Ihrer App unterstützen. Teams ermöglicht Benutzern das Umbenennen oder Entfernen einer Kanal-/Gruppenregisterkarte, und Sie können Benutzern erlauben, Ihre Registerkarte nach der Installation neu zu konfigurieren. Darüber hinaus kann die Registerkartenentfernungsoberfläche angeben, was mit dem Inhalt geschieht, wenn die Registerkarte entfernt wird, oder Benutzern Optionen wie das Löschen oder Archivieren des Inhalts nach dem Entfernen geben.

## <a name="enable-your-tab-to-be-reconfigured-after-installation"></a>Aktivieren der Neukonfiguration Ihrer Registerkarte nach der Installation

Ihr **manifest.jsdefiniert** die Features und Funktionen Ihrer Registerkarte. Die `canUpdateConfiguration` Registerkarteninstanzeigenschaft verwendet einen booleschen Wert, der angibt, ob ein Benutzer die Registerkarte ändern oder neu konfigurieren kann, nachdem sie erstellt wurde:

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`canUpdateConfiguration`|Boolescher Wert|||Ein Wert, der angibt, ob eine Instanz der Konfiguration der Registerkarte vom Benutzer nach der Erstellung aktualisiert werden kann. Standard: `true`|

Wenn Ihre Registerkarte in einen Kanal- oder Gruppenchat hochgeladen wird, fügt Teams ein Dropdownmenü mit der rechten Maustaste für Ihre Registerkarte hinzu. Die verfügbaren Optionen werden durch die `canUpdateConfiguration` Einstellung bestimmt:

| `canUpdateConfiguration`| true   | false | description |
| ----------------------- | :----: | ----- | ----------- |
|     Einstellungen            |   √    |       |Die `configurationUrl` Seite wird in einem IFrame neu geladen, sodass der Benutzer die Registerkarte neu konfigurieren kann.  |
|     Umbenennen              |   √    |   √   | Der Benutzer kann den Namen der Registerkarte so ändern, wie er in der Registerkartenleiste angezeigt wird.          |
|     Entfernen              |   √    |   √   |  Wenn die  `removeURL` Eigenschaft und der Wert auf der **Konfigurationsseite** enthalten sind, wird die Seite zum **Entfernen** in einen IFrame geladen und dem Benutzer angezeigt. Wenn keine Entfernungsseite enthalten ist, wird dem Benutzer ein Bestätigungsdialogfeld angezeigt.          |
|||||

## <a name="create-a-tab-removal-page-for-your-application"></a>Erstellen einer Seite zum Entfernen von Registerkarten für Ihre Anwendung

Die optionale Seite zum Entfernen ist eine HTML-Seite, die Sie hosten, und wird angezeigt, wenn die Registerkarte entfernt wird. Die URL der Entfernungsseite wird von der `setSettings()` Methode innerhalb der Konfigurationsseite festgelegt. Wie bei allen Seiten in Ihrer App muss die Entfernungsseite [Teams Registerkartenanforderungen](../../../tabs/how-to/tab-requirements.md)entsprechen.

### <a name="register-a-remove-handler"></a>Registrieren eines Remove-Handlers

Optional können Sie innerhalb der Logik für die Entfernungsseite den Ereignishandler aufrufen, `registerOnRemoveHandler((RemoveEvent) => {}` wenn der Benutzer eine vorhandene Registerkartenkonfiguration entfernt. Die Methode übernimmt die [`RemoveEvent`](/javascript/api/@microsoft/teams-js/microsoftteams.settings.removeevent?view=msteams-client-js-latest&preserve-view=true) Schnittstelle und führt den Code im Handler aus, wenn ein Benutzer versucht, Inhalte zu entfernen. Es wird verwendet, um Bereinigungsvorgänge auszuführen, z. B. das Entfernen der zugrunde liegenden Ressource, die den Registerkarteninhalt angibt. Es kann jeweils nur ein Remove-Handler registriert werden.

Die `RemoveEvent` Schnittstelle beschreibt ein Objekt mit zwei Methoden:

* Die `notifySuccess()` Funktion ist erforderlich. Es gibt an, dass das Entfernen der zugrunde liegenden Ressource erfolgreich war und der Inhalt entfernt werden kann.

* Die `notifyFailure(string)` Funktion ist optional. Es gibt an, dass das Entfernen der zugrunde liegenden Ressource fehlgeschlagen ist und der Inhalt nicht entfernt werden kann. Der optionale Zeichenfolgenparameter gibt einen Grund für den Fehler an. Wenn angegeben, wird diese Zeichenfolge dem Benutzer angezeigt. andernfalls wird ein allgemeiner Fehler angezeigt.

#### <a name="use-the-getsettings-function"></a>Verwenden der `getSettings()` Funktion

Sie können den `getSettings()` zu entfernenden Registerkarteninhalt festlegen. Die `getSettings((Settings) =>{})` Funktion übernimmt die gültigen Werte der Einstellungseigenschaft und stellt sie [`Settings interface`](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true) bereit, die abgerufen werden können.

#### <a name="use-the-getcontext-function"></a>Verwenden der `getContext()` Funktion

Sie können `getContext()` den aktuellen Kontext abrufen, in dem der Frame ausgeführt wird. Die Funktion übernimmt die gültigen Eigenschaftswerte und stellt sie `getContext((Context) =>{})` [`Context interface`](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true) `Context` bereit, die Sie in der Logik für die Entfernungsseite verwenden können, um den Inhalt zu bestimmen, der auf der Entfernungsseite angezeigt werden soll.

#### <a name="include-authentication"></a>Einschließen der Authentifizierung

Möglicherweise ist eine Authentifizierung erforderlich, bevor ein Benutzer den Registerkarteninhalt löschen kann. Kontextinformationen können verwendet werden, um Authentifizierungsanforderungen und Autorisierungsseiten-URLs zu erstellen. Siehe [Microsoft Teams Authentifizierungsfluss für Registerkarten.](~/tabs/how-to/authentication/auth-flow-tab.md) Stellen Sie sicher, dass alle Domänen, die auf Ihren Registerkartenseiten verwendet werden, im Array aufgeführt `manifest.json` `validDomains` sind.

Unten sehen Sie einen Codeblock zum Entfernen von Registerkarten:

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

Wenn ein Benutzer im Dropdownmenü der Registerkarte **"Entfernen"** auswählt, lädt Teams die optionale `removeUrl` Seite (die auf der **Konfigurationsseite** angegeben ist) in einen IFrame. Hier wird dem Benutzer eine Schaltfläche angezeigt, die mit der Funktion geladen `onClick()` ist, `microsoftTeams.settings.setValidityState(true)` die die Schaltfläche **"Entfernen"** aufruft, die sich unten auf dem IFrame der Entfernungsseite befindet.

Nach der Ausführung des Remove-Handlers oder benachrichtigt `removeEvent.notifySuccess()` Teams über das Ergebnis der `removeEvent.notifyFailure()` Inhaltsentfernung.

>[!NOTE]
> * Um sicherzustellen, dass die Kontrolle eines autorisierten Benutzers über eine Registerkarte nicht gehemmt wird, entfernt Teams die Registerkarte sowohl in Erfolgs- als auch in Fehlerfällen.\
> * Teams aktiviert die Schaltfläche **"Entfernen"** nach 5 Sekunden, auch wenn die Registerkarte nicht aufgerufen `setValidityState()` wurde.
> * Wenn der Benutzer **"Entfernen"** auswählt, Teams wird die Registerkarte nach 30 Sekunden entfernt, unabhängig davon, ob Die Aktionen abgeschlossen wurden.
