---
title: Erstellen einer Seite zum Entfernen von Registerkarten
author: surbhigupta
description: So erstellen Sie eine Seite zum Entfernen von Registerkarten
keywords: Teams-Registerkarten Gruppenkanal konfigurierbare Löschung entfernen
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: fbff927687fd19de273ef801ef34e77dda7a83a5
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2022
ms.locfileid: "63452725"
---
# <a name="create-a-removal-page"></a>Erstellen einer Seite zum Entfernen

Sie können die Benutzererfahrung erweitern und verbessern, indem Sie Entfernungs- und Änderungsoptionen in Ihrer App unterstützen. Teams ermöglicht Benutzern das Umbenennen oder Entfernen einer Kanal- oder Gruppenregisterkarte, und Sie können Benutzern gestatten, ihre Registerkarte nach der Installation neu zu konfigurieren. Darüber hinaus bietet die Registerkartenentfernung den Benutzern Optionen zum Löschen oder Archivieren von Inhalten nach dem Entfernen.

## <a name="enable-your-tab-to-be-reconfigured-after-installation"></a>Aktivieren der Neukonfiguration Ihrer Registerkarte nach der Installation

Your **manifest.json** defines your tab's features and capabilities. Die Registerkarteninstanzeigenschaft `canUpdateConfiguration` verwendet einen booleschen Wert, der angibt, ob ein Benutzer die Registerkarte ändern oder neu konfigurieren kann, nachdem sie erstellt wurde. Die folgende Tabelle enthält die Eigenschaftendetails:

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`canUpdateConfiguration`|Boolean|||Der Wert, der angibt, ob eine Instanz der Registerkartenkonfiguration nach der Erstellung vom Benutzer aktualisiert werden kann. Der Standardwert ist `true`. |

Wenn Ihre Registerkarte in einen Kanal- oder Gruppenchat hochgeladen wird, fügt Teams ein Dropdownmenü mit der rechten Maustaste für Ihre Registerkarte hinzu. Die verfügbaren Optionen werden durch die `canUpdateConfiguration` Einstellung bestimmt. Die folgende Tabelle enthält die Einstellungsdetails:

| `canUpdateConfiguration`| true   | false | description |
| ----------------------- | :----: | ----- | ----------- |
|     Einstellungen            |   √    |       |Die `configurationUrl` Seite wird in einem IFrame neu geladen, sodass der Benutzer die Registerkarte neu konfigurieren kann. |
|     Umbenennen              |   √    |   √   | Der Benutzer kann den Namen der Registerkarte so ändern, wie er in der Registerkartenleiste angezeigt wird.          |
|     Entfernen              |   √    |   √   |  Wenn die  `removeURL` Eigenschaft und der Wert auf der **Konfigurationsseite** enthalten sind, wird die **Seite zum Entfernen** in einen IFrame geladen und dem Benutzer angezeigt. Wenn keine Seite zum Entfernen enthalten ist, wird dem Benutzer ein Bestätigungsdialogfeld angezeigt.          |

## <a name="create-a-tab-removal-page-for-your-application"></a>Erstellen einer Seite zum Entfernen von Registerkarten für Ihre Anwendung

Die optionale Seite zum Entfernen ist eine HTML-Seite, die Sie hosten, und wird angezeigt, wenn die Registerkarte entfernt wird. Die URL der Entfernungsseite wird von der `setSettings()` Methode innerhalb der Konfigurationsseite festgelegt. Wie bei allen Seiten in Ihrer App muss die Entfernungsseite [Teams Registerkartenvoraussetzungen](../../../tabs/how-to/tab-requirements.md) erfüllen.

### <a name="register-a-remove-handler"></a>Registrieren eines Remove-Handlers

Optional können Sie innerhalb der Logik für die Entfernungsseite den `registerOnRemoveHandler((RemoveEvent) => {}` Ereignishandler aufrufen, wenn der Benutzer eine vorhandene Registerkartenkonfiguration entfernt. Die Methode übernimmt die [`RemoveEvent`](/javascript/api/@microsoft/teams-js/microsoftteams.settings.removeevent?view=msteams-client-js-latest&preserve-view=true) Schnittstelle und führt den Code im Handler aus, wenn ein Benutzer versucht, Inhalte zu entfernen. Die Methode wird verwendet, um Bereinigungsvorgänge auszuführen, z. B. das Entfernen der zugrunde liegenden Ressource, die den Registerkarteninhalt ansteuert. Gleichzeitig kann nur ein Remove-Handler registriert werden.

Die `RemoveEvent` Schnittstelle beschreibt ein Objekt mit zwei Methoden:

* Die `notifySuccess()` Funktion ist erforderlich. Es gibt an, dass das Entfernen der zugrunde liegenden Ressource erfolgreich war und der Inhalt entfernt werden kann.

* Die `notifyFailure(string)` Funktion ist optional. Es gibt an, dass das Entfernen der zugrunde liegenden Ressource fehlgeschlagen ist und der Inhalt nicht entfernt werden kann. Der optionale Zeichenfolgenparameter gibt einen Grund für den Fehler an. Wenn angegeben, wird diese Zeichenfolge dem Benutzer angezeigt. andernfalls wird ein allgemeiner Fehler angezeigt.

#### <a name="use-the-getsettings-function"></a>Verwenden der `getSettings()` Funktion

Sie können den `getSettings()`zu entfernenden Registerkarteninhalt zuweisen. Die `getSettings((Settings) =>{})` Funktion übernimmt die gültigen Werte der [`Settings interface`](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true) Einstellungseigenschaft und stellt sie bereit, die abgerufen werden können.

#### <a name="use-the-getcontext-function"></a>Verwenden der `getContext()` Funktion

Sie können den `getContext()` aktuellen Kontext abrufen, in dem der Frame ausgeführt wird. Die `getContext((Context) =>{})` Funktion übernimmt die [`Context interface`](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true). Die Funktion stellt gültige `Context` Eigenschaftswerte bereit, die Sie in der Logik für die Entfernungsseite verwenden können, um den Inhalt zu bestimmen, der auf der Entfernungsseite angezeigt werden soll.

#### <a name="include-authentication"></a>Einschließen der Authentifizierung

Eine Authentifizierung ist erforderlich, bevor ein Benutzer den Registerkarteninhalt löschen kann. Kontextinformationen können verwendet werden, um Authentifizierungsanforderungen und Autorisierungsseiten-URLs zu erstellen. Weitere Informationen finden Sie [unter Microsoft Teams Authentifizierungsfluss für Registerkarten](~/tabs/how-to/authentication/auth-flow-tab.md). Stellen Sie sicher, dass alle Domänen, die auf Ihren Registerkartenseiten verwendet werden, im `manifest.json` `validDomains` Array aufgeführt sind.

Es folgt ein Beispielcodeblock zum Entfernen von Registerkarten:

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

Wenn ein Benutzer im Dropdownmenü der Registerkarte "**Entfernen**" auswählt, lädt Teams die auf der **Konfigurationsseite** zugewiesene optionale `removeUrl` Seite in einen IFrame. Dem Benutzer wird eine Schaltfläche angezeigt, die mit der `onClick()` Funktion geladen ist, die die Schaltfläche **"Entfernen"** am unteren Rand der IFrame-Entfernungsseite aufruft `microsoftTeams.settings.setValidityState(true)` und aktiviert.

Nachdem der Remove-Handler ausgeführt wurde, `removeEvent.notifySuccess()` oder `removeEvent.notifyFailure()` benachrichtigt Teams über das Ergebnis der Inhaltsentfernung.

>[!NOTE]
>
> * Um sicherzustellen, dass die Kontrolle eines autorisierten Benutzers über eine Registerkarte nicht gehemmt wird, entfernt Teams die Registerkarte sowohl in Erfolgs- als auch in Fehlerfällen.
> * Nachdem Sie den `registerOnRemoveHandler` Ereignishandler aufgerufen haben, haben Sie 15 Sekunden Zeit, um auf die Methode zu reagieren. Standardmäßig aktiviert Teams die Schaltfläche **"Entfernen"** nach fünf Sekunden, auch wenn Sie nicht aufrufen`setValidityState(true)`.
> * Wenn der Benutzer "**Entfernen**" auswählt, entfernt Teams die Registerkarte nach 30 Sekunden, unabhängig davon, ob die Aktionen abgeschlossen wurden oder nicht.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md)

## <a name="see-also"></a>Siehe auch

* [registerkarten Teams](~/tabs/what-are-tabs.md)
* [Erstellen einer persönlichen Registerkarte](~/tabs/how-to/create-personal-tab.md)
* [Erstellen einer Kanal- oder Gruppenregisterkarte](~/tabs/how-to/create-channel-group-tab.md)
* [Erstellen einer Konfigurationsseite](~/tabs/how-to/create-tab-pages/configuration-page.md)
