---
title: Erstellen einer Registerkarten-Entfernungs Seite
author: laujan
description: Erstellen einer Registerkarten-Entfernungs Seite
keywords: Teams-Registerkartengruppe Kanal konfigurierbar entfernen löschen
ms.topic: conceptual
ms.author: ''
ms.openlocfilehash: 576a3bc88d8776a193b48868d37df204c3112fd8
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674085"
---
# <a name="modify-or-remove-a-channel-group-tab"></a>Ändern oder Entfernen einer Kanalgruppen Registerkarte

Sie können die Benutzerfreundlichkeit erweitern und verbessern, indem Sie Entfernungs-und Änderungsoptionen in Ihrer APP unterstützen. Microsoft Teams ermöglicht Benutzern das Umbenennen oder Entfernen einer Kanal/Gruppen-Registerkarte, und Sie können Benutzern das erneute Konfigurieren ihrer Registerkarte nach der Installation gestatten. Darüber hinaus können Sie mit der Registerkarten Entfernung festlegen, was mit dem Inhalt geschieht, wenn die Registerkarte entfernt wird, oder Benutzern nach dem Entfernen Optionen wie löschen oder Archivieren des Inhalts zuweisen.

## <a name="enable-your-tab-to-be-reconfigured-after-installation"></a>Aktivieren der erneuten Konfiguration der Registerkarte nach der Installation

Ihre **Manifest. JSON** definiert die Funktionen und Funktionen Ihrer Registerkarte. Die Eigenschaft der `canUpdateConfiguration` Tab-Instanz akzeptiert einen booleschen Wert, der angibt, ob ein Benutzer die Registerkarte nach der Erstellung ändern oder neu konfigurieren kann:

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`canUpdateConfiguration`|Boolean|||Ein Wert, der angibt, ob eine Instanz der Konfiguration der Registerkarte nach der Erstellung vom Benutzer aktualisiert werden kann. Standard`true`|

Wenn Ihre Registerkarte in einen Kanal-oder Gruppenchat hochgeladen wird, fügt Microsoft Teams ein Rechtsklick-Dropdownmenü für die Registerkarte hinzu. Die verfügbaren Optionen werden durch `canUpdateConfiguration` die Einstellung bestimmt:

| `canUpdateConfiguration`| true   | false | description |
| ----------------------- | :----: | ----- | ----------- |
|     Einstellungen            |   √    |       |Die `configurationUrl` Seite wird in einem IFRAME neu geladen, sodass der Benutzer die Registerkarte neu konfigurieren kann.  |
|     Umbenennen              |   √    |   √   | Der Benutzer kann den Registerkartennamen so ändern, wie er in der Registerkartenleiste angezeigt wird.          |
|     Entfernen              |   √    |   √   |  Wenn die `removeURL` Eigenschaft und der Wert auf der **Konfigurationsseite**enthalten sind, wird die **Entfernungs Seite** in einen IFRAME geladen und dem Benutzer zur Verfügung gestellt. Wenn keine Entfernungs Seite enthalten ist, wird dem Benutzer ein Bestätigungsdialogfeld angezeigt.          |
|||||

## <a name="create-a-tab-removal-page-for-your-application"></a>Erstellen einer Registerkarten-Entfernungs Seite für Ihre Anwendung

Die optionale Entfernungs Seite ist eine HTML-Seite, die Sie hosten und angezeigt wird, wenn die Registerkarte entfernt wird. Die URL der Entfernungs Seite wird von `setSettings()` der-Methode auf Ihrer Konfigurationsseite festgelegt. Wie bei allen Seiten in Ihrer APP muss die Entfernungs Seite den [Registerkarten Anforderungen für Teams](~/tabs/how-to/add-tab.md)entsprechen.

### <a name="register-a-remove-handler"></a>Registrieren eines Remove-Handlers

Optional können Sie in der Logik ihrer Entfernungs Seite den `registerOnRemoveHandler((RemoveEvent) => {}` Ereignishandler aufrufen, wenn der Benutzer eine vorhandene Registerkartenkonfiguration entfernt. Die-Methode nimmt die [`RemoveEvent`](/javascript/api/@microsoft/teams-js/microsoftteams.settings.removeevent?view=msteams-client-js-latest) Schnittstelle an und führt den Code im Handler aus, wenn ein Benutzer versucht, Inhalte zu entfernen. Es wird verwendet, um Bereinigungsvorgänge wie das Entfernen der zugrunde liegenden Ressource, die die Registerkarteninhalte macht, auszuführen. Nur ein Remove-Handler kann gleichzeitig registriert werden.

Die `RemoveEvent` Schnittstelle beschreibt ein Objekt mit zwei Methoden:

* Die `notifySuccess()` Funktion ist erforderlich. Er gibt an, dass das Entfernen der zugrunde liegenden Ressource erfolgreich war und dass der Inhalt entfernt werden kann.

* Die `notifyFailure(string)` Funktion ist optional. Er gibt an, dass das Entfernen der zugrunde liegenden Ressource fehlgeschlagen ist und dass der Inhalt nicht entfernt werden kann. Der optionale String-Parameter gibt einen Grund für den Fehler an. Wenn angegeben, wird diese Zeichenfolge dem Benutzer angezeigt; Andernfalls wird ein generischer Fehler angezeigt.

#### <a name="use-the-getsettings-function"></a>Verwenden Sie `getSettings()` die Funktion

Sie können zum `getSettings()`Festlegen des zu entfernenden Registerkarteninhalts verwenden. Die `getSettings((Settings) =>{})` -Funktion übernimmt die [`Settings interface`](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest) und stellt die gültigen Einstellungen-Eigenschaftswerte bereit, die abgerufen werden können.

#### <a name="use-the-getcontext-function"></a>Verwenden Sie `getContext()` die Funktion

Sie können zum `getContext()` Abrufen des aktuellen Kontexts verwenden, in dem der Frame gestartet wird. Die `getContext((Context) =>{})` -Funktion übernimmt die [`Context interface`](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest) und stellt gültige `Context` Eigenschaftswerte bereit, die Sie in ihrer Entfernungs Seitenlogik verwenden können, um den Inhalt zu bestimmen, der auf der Entfernungs Seite angezeigt werden soll.

#### <a name="include-authentication"></a>Einschließen der Authentifizierung

Möglicherweise müssen Sie eine Authentifizierung benötigen, bevor Sie einem Benutzer das Löschen der Registerkarteninhalte ermöglichen. Kontextinformationen können verwendet werden, um die Erstellung von Authentifizierungsanforderungen und Autorisierungs Seiten-URLs zu erleichtern. Weitere Informationen finden Sie unter [Microsoft Teams-Authentifizierungs Fluss für Registerkarten](~/tabs/how-to/authentication/auth-flow-tab.md). Stellen Sie sicher, dass alle auf den Registerkartenseiten verwendeten Domänen im `manifest.json` `validDomains` Array aufgelistet sind.

Unten finden Sie einen Codebaustein zum Entfernen von Beispiel Registerkarten:

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

Wenn ein Benutzer aus dem Dropdownmenü der Registerkarte **Entfernen** auswählt, lädt Microsoft Teams die optionale `removeUrl` Seite (in Ihrer **Konfigurationsseite**festgelegt) in einen iframe. Hier wird dem Benutzer eine Schaltfläche mit der `onClick()` Funktion zur Verfügung gestellt, `microsoftTeams.settings.setValidityState(true)` die die Schaltfläche **Entfernen** im unteren Bereich der Entfernungs Seite IFRAME aufruft und aktiviert.

Nach der Ausführung des Remove- `removeEvent.notifySuccess()` Handlers oder `removeEvent.notifyFailure()` benachrichtigt Teams über das Ergebnis der Inhalts Entfernung.

>[!NOTE]
>Um sicherzustellen, dass die Steuerung eines autorisierten Benutzers über eine Registerkarte nicht gehemmt wird, wird die Registerkarte in Microsoft Teams sowohl in Success als auch in Fehlerfällen entfernt. \
>Teams aktiviert die Schaltfläche **Entfernen** nach 5 Sekunden, auch wenn die Registerkarte `setValidityState()`nicht aufgerufen wird. \
>Wenn der Benutzer **Remove** Teams auswählt, wird die Registerkarte nach 30 Sekunden entfernt, unabhängig davon, ob Ihre Aktionen abgeschlossen wurden.
