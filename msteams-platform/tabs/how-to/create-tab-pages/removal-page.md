---
title: Erstellen einer Seite zum Entfernen von Registerkarten
author: laujan
description: So erstellen Sie eine Seite zum Entfernen von Registerkarten
keywords: Teams-Registerkarten-Gruppenkanal konfigurierbare Löschung entfernen
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 49e2df47095999e9f9eea76ea341a44215bfacb3
ms.sourcegitcommit: 4539479289b43812eaae07a1c0f878bed815d2d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/12/2021
ms.locfileid: "49797883"
---
# <a name="modify-or-remove-a-channel-group-tab"></a>Ändern oder Entfernen einer Kanalgruppenregisterkarte

Sie können die Benutzererfahrung erweitern und verbessern, indem Sie Entfernungs- und Änderungsoptionen in Ihrer App unterstützen. Teams ermöglicht Benutzern das Umbenennen oder Entfernen einer Kanal-/Gruppenregisterkarte, und Sie können Benutzern erlauben, ihre Registerkarte nach der Installation neu zu konfigurieren. Darüber hinaus können Sie beim Entfernen von Registerkarten festlegen, was mit dem Inhalt geschieht, wenn die Registerkarte entfernt wird, oder benutzern Optionen nach dem Entfernen zur Verfügung stellen, z. B. löschen oder archivieren.

## <a name="enable-your-tab-to-be-reconfigured-after-installation"></a>Aktivieren der Neukonfiguration der Registerkarte nach der Installation

Ihr **manifest.jsdefiniert** die Features und Funktionen Ihrer Registerkarte. Die Eigenschaft der Registerkarteninstanz verwendet einen booleschen Wert, der angibt, ob ein Benutzer die Registerkarte ändern oder neu konfigurieren kann, nachdem `canUpdateConfiguration` sie erstellt wurde:

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`canUpdateConfiguration`|Boolean|||Ein Wert, der angibt, ob eine Instanz der Konfiguration der Registerkarte vom Benutzer nach der Erstellung aktualisiert werden kann. Standard: `true`|

Wenn Ihre Registerkarte in einen Kanal- oder Gruppenchat hochgeladen wird, fügt Teams ein Dropdownmenü mit der rechten Maustaste für Ihre Registerkarte hinzu. Die verfügbaren Optionen werden durch die Einstellung `canUpdateConfiguration` bestimmt:

| `canUpdateConfiguration`| true   | False | description |
| ----------------------- | :----: | ----- | ----------- |
|     Einstellungen            |   √    |       |Die Seite wird in einem IFrame neu geladen, sodass der Benutzer die `configurationUrl` Registerkarte neu konfigurieren kann.  |
|     Umbenennen              |   √    |   √   | Der Benutzer kann den Namen der Registerkarte ändern, wie er in der Registerkartenleiste angezeigt wird.          |
|     Entfernen              |   √    |   √   |  Wenn die Eigenschaft und der Wert in der Konfigurationsseite enthalten sind, wird die Seite zum Entfernen in einen IFrame geladen und `removeURL` dem Benutzer angezeigt.   Wenn keine Seite zum Entfernen enthalten ist, wird dem Benutzer ein Bestätigungsdialogfeld angezeigt.          |
|||||

## <a name="create-a-tab-removal-page-for-your-application"></a>Erstellen einer Seite zum Entfernen von Registerkarten für Ihre Anwendung

Die optionale Seite zum Entfernen ist eine HTML-Seite, die Sie hosten und die angezeigt wird, wenn die Registerkarte entfernt wird. Die URL der Entfernungsseite wird durch die `setSettings()` Methode auf der Konfigurationsseite festgelegt. Wie bei allen Seiten in Ihrer App muss die Seite zum Entfernen den [Registerkartenanforderungen](../../../tabs/how-to/tab-requirements.md)für Teams entsprechen.

### <a name="register-a-remove-handler"></a>Registrieren eines Removehandlers

Optional können Sie innerhalb der Logik für die Entfernungsseite den Ereignishandler aufrufen, wenn der Benutzer `registerOnRemoveHandler((RemoveEvent) => {}` eine vorhandene Registerkartenkonfiguration entfernt. Die Methode übernimmt die Schnittstelle und führt den Code im Handler aus, wenn ein Benutzer [`RemoveEvent`](/javascript/api/@microsoft/teams-js/microsoftteams.settings.removeevent?view=msteams-client-js-latest&preserve-view=true) versucht, Inhalte zu entfernen. Es wird zum Ausführen von Bereinigungsvorgängen verwendet, z. B. zum Entfernen der zugrunde liegenden Ressource, die den Registerkarteninhalt an die Macht macht. Es kann immer nur ein Removehandler registriert werden.

Die `RemoveEvent` Schnittstelle beschreibt ein Objekt mit zwei Methoden:

* Die `notifySuccess()` Funktion ist erforderlich. Es gibt an, dass das Entfernen der zugrunde liegenden Ressource erfolgreich war und der inhalt entfernt werden kann.

* Die `notifyFailure(string)` Funktion ist optional. Es weist darauf hin, dass beim Entfernen der zugrunde liegenden Ressource ein Fehler aufting, und der Inhalt kann nicht entfernt werden. Der optionale Zeichenfolgenparameter gibt einen Grund für den Fehler an. Wenn angegeben, wird diese Zeichenfolge dem Benutzer angezeigt. andernfalls wird ein allgemeiner Fehler angezeigt.

#### <a name="use-the-getsettings-function"></a>Verwenden der `getSettings()` Funktion

Sie können den `getSettings()` zu entfernende Registerkarteninhalt festlegen. Die `getSettings((Settings) =>{})` Funktion übernimmt die [`Settings interface`](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true) gültigen Einstellungseigenschaftswerte, die abgerufen werden können.

#### <a name="use-the-getcontext-function"></a>Verwenden der `getContext()` Funktion

Sie können den `getContext()` aktuellen Kontext abrufen, in dem der Frame ausgeführt wird. Die Funktion übernimmt die gültigen Eigenschaftswerte, die Sie in Der Entfernungsseitenlogik verwenden können, um den Inhalt zu bestimmen, der auf der Seite zum Entfernen `getContext((Context) =>{})` [`Context interface`](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true) angezeigt werden `Context` soll.

#### <a name="include-authentication"></a>Authentifizierung mit ein- und ein-

Möglicherweise benötigen Sie eine Authentifizierung, bevor Sie einem Benutzer das Löschen des Registerkarteninhalts erlauben. Kontextinformationen können zum Erstellen von URLs für Authentifizierungsanforderungen und Autorisierungsseiten verwendet werden. Weitere [Informationen finden Sie unter Microsoft Teams-Authentifizierungsfluss für Registerkarten.](~/tabs/how-to/authentication/auth-flow-tab.md) Stellen Sie sicher, dass alle auf Ihren Registerkartenseiten verwendeten Domänen im Array aufgeführt `manifest.json` `validDomains` sind.

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

Wenn ein Benutzer  aus dem Dropdownmenü der Registerkarte "Entfernen" auswählt, wird die optionale Seite (auf Der Konfigurationsseite festgelegt) von Teams in einen `removeUrl` IFrame geladen.  Hier wird dem Benutzer eine Schaltfläche angezeigt, die mit der Funktion geladen ist, die die Schaltfläche "Entfernen" aufruft und aktiviert, die sich am unteren Rand des IFrames zum Entfernen `onClick()` `microsoftTeams.settings.setValidityState(true)` befindet. 

Nach der Ausführung des Removehandlers oder benachrichtigen Sie Teams über das Ergebnis `removeEvent.notifySuccess()` `removeEvent.notifyFailure()` des Entfernens von Inhalten.

>[!NOTE]
>Um sicherzustellen, dass die Kontrolle eines autorisierten Benutzers über eine Registerkarte nicht behindert wird, entfernt Teams die Registerkarte sowohl in Erfolgs- als auch in Fehlerfällen.\
>Teams aktiviert die **Schaltfläche "Entfernen"** nach 5 Sekunden, auch wenn Ihre Registerkarte ".\ " nicht aufgerufen `setValidityState()` hat.
>Wenn der Benutzer **"Teams** entfernen" auswählt, wird die Registerkarte nach 30 Sekunden entfernt, unabhängig davon, ob Ihre Aktionen abgeschlossen wurden.
