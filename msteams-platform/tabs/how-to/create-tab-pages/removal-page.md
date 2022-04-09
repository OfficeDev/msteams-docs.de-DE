---
title: Erstellen einer Seite zum Entfernen von Registerkarten
author: surbhigupta
description: So erstellen Sie eine Seite zum Entfernen von Registerkarten
keywords: Teams-Registerkarten Gruppenkanal konfigurierbar entfernen Löschen
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: ea29959bf79b5e46e876f75570dcb437fa56888f
ms.sourcegitcommit: 61003a14e8a179e1268bbdbd9cf5e904c5259566
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2022
ms.locfileid: "64736862"
---
# <a name="create-a-removal-page"></a>Erstellen einer Seite zum Entfernen

Sie können die Benutzererfahrung erweitern und verbessern, indem Sie Die Entfernungs- und Änderungsoptionen in Ihrer App unterstützen. Teams ermöglicht Es Benutzern, eine Kanal- oder Gruppenregisterkarte umzubenennen oder zu entfernen, und Sie können Benutzern erlauben, Ihre Registerkarte nach der Installation neu zu konfigurieren. Darüber hinaus bietet die Registerkartenentfernung den Benutzern nach dem Entfernen Optionen zum Löschen oder Archivieren von Inhalten.

## <a name="enable-your-tab-to-be-reconfigured-after-installation"></a>Aktivieren der Neukonfiguration Ihrer Registerkarte nach der Installation

Sie `manifest.json` definieren die Features und Funktionen Ihrer Registerkarte. Die Registerkarteninstanzeigenschaft `canUpdateConfiguration` verwendet einen booleschen Wert, der angibt, ob ein Benutzer die Registerkarte nach der Erstellung ändern oder neu konfigurieren kann. Die folgende Tabelle enthält die Eigenschaftendetails:

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`canUpdateConfiguration`|Boolean|||Der Wert, der angibt, ob eine Instanz der Registerkartenkonfiguration nach der Erstellung vom Benutzer aktualisiert werden kann. Der Standardwert ist `true`. |

Wenn Ihre Registerkarte in einen Kanal- oder Gruppenchat hochgeladen wird, fügt Teams ein Dropdownmenü mit der rechten Maustaste für Ihre Registerkarte hinzu. Die verfügbaren Optionen werden durch die `canUpdateConfiguration` Einstellung bestimmt. Die folgende Tabelle enthält die Einstellungsdetails:

| `canUpdateConfiguration`| true   | false | description |
| ----------------------- | :----: | ----- | ----------- |
|     Einstellungen            |   √    |       |Die `configurationUrl` Seite wird in einem IFrame neu geladen, sodass der Benutzer die Registerkarte neu konfigurieren kann. |
|     Umbenennen              |   √    |   √   | Der Benutzer kann den Namen der Registerkarte ändern, wie er in der Registerkartenleiste angezeigt wird.          |
|     Entfernen              |   √    |   √   |  Wenn die Eigenschaft und der  `removeURL` Wert auf der **Konfigurationsseite** enthalten sind, wird die **Seite zum Entfernen** in einen IFrame geladen und dem Benutzer angezeigt. Wenn keine Seite zum Entfernen enthalten ist, wird dem Benutzer ein Bestätigungsdialogfeld angezeigt.          |

## <a name="create-a-tab-removal-page-for-your-application"></a>Erstellen einer Seite zum Entfernen von Registerkarten für Ihre Anwendung

Die optionale Seite zum Entfernen ist eine HTML-Seite, die Sie hosten, und wird angezeigt, wenn die Registerkarte entfernt wird. Die URL der Entfernungsseite wird von der `setSettings()` Methode auf der Konfigurationsseite festgelegt. Wie bei allen Seiten in Ihrer App muss die Seite zum Entfernen [Teams Registerkartenvoraussetzungen](../../../tabs/how-to/tab-requirements.md) entsprechen.

### <a name="register-a-remove-handler"></a>Registrieren eines Remove-Handlers

Optional können Sie in der Logik der Entfernungsseite den `registerOnRemoveHandler((RemoveEvent) => {}` Ereignishandler aufrufen, wenn der Benutzer eine vorhandene Registerkartenkonfiguration entfernt. Die Methode übernimmt die [`RemoveEvent`](/javascript/api/@microsoft/teams-js/microsoftteams.settings.removeevent?view=msteams-client-js-latest&preserve-view=true) Schnittstelle und führt den Code im Handler aus, wenn ein Benutzer versucht, Inhalte zu entfernen. Die Methode wird verwendet, um Bereinigungsvorgänge auszuführen, z. B. das Entfernen der zugrunde liegenden Ressource, die den Registerkarteninhalt läuft. Gleichzeitig kann nur ein Remove-Handler registriert werden.

Die `RemoveEvent` Schnittstelle beschreibt ein Objekt mit zwei Methoden:

* Die `notifySuccess()` Funktion ist erforderlich. Es gibt an, dass das Entfernen der zugrunde liegenden Ressource erfolgreich war und der Inhalt entfernt werden kann.

* Die `notifyFailure(string)` Funktion ist optional. Es gibt an, dass das Entfernen der zugrunde liegenden Ressource fehlgeschlagen ist und der Inhalt nicht entfernt werden kann. Der optionale Zeichenfolgenparameter gibt einen Grund für den Fehler an. Falls angegeben, wird diese Zeichenfolge dem Benutzer angezeigt. andernfalls wird ein allgemeiner Fehler angezeigt.

#### <a name="use-the-getsettings-function"></a>Verwenden der `getSettings()` Funktion

Sie können `getSettings()`den zu entfernenden Registerkarteninhalt zuweisen. Die `getSettings((Settings) =>{})` Funktion übernimmt die [`Settings interface`](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true) und stellt die gültigen Einstellungseigenschaftenwerte bereit, die abgerufen werden können.

#### <a name="use-the-getcontext-function"></a>Verwenden der `getContext()` Funktion

Sie können `getContext()` den aktuellen Kontext abrufen, in dem der Frame ausgeführt wird. Die `getContext((Context) =>{})` Funktion übernimmt die [`Context interface`](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true). Die Funktion stellt gültige `Context` Eigenschaftswerte bereit, die Sie in ihrer Logik zum Entfernen von Seiten verwenden können, um den Inhalt zu bestimmen, der auf der Entfernungsseite angezeigt werden soll.

#### <a name="include-authentication"></a>Authentifizierung einschließen

Die Authentifizierung ist erforderlich, bevor ein Benutzer den Registerkarteninhalt löschen kann. Kontextinformationen können zum Erstellen von Authentifizierungsanforderungen und Autorisierungsseiten-URLs verwendet werden. Siehe [Microsoft Teams Authentifizierungsfluss für Registerkarten](~/tabs/how-to/authentication/auth-flow-tab.md). Stellen Sie sicher, dass alle Domänen, die auf Ihren Registerkartenseiten verwendet werden, im `manifest.json` `validDomains` Array aufgeführt sind.

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

Wenn ein Benutzer "Aus dem Dropdownmenü der Registerkarte **entfernen**" auswählt, lädt Teams die optionale `removeUrl` Seite, die auf ihrer **Konfigurationsseite** zugewiesen ist, in einen IFrame. Dem Benutzer wird eine Schaltfläche angezeigt, die mit der Funktion geladen wird, die `onClick()` die Schaltfläche "**Entfernen**" am unteren Rand der IFrame-Seite zum Entfernen aufruft `microsoftTeams.settings.setValidityState(true)` und aktiviert.

Nachdem der Remove-Handler ausgeführt wurde, `removeEvent.notifySuccess()` oder `removeEvent.notifyFailure()` benachrichtigt Teams des Inhaltsentfernungsergebnisses.

>[!NOTE]
>
> * Um sicherzustellen, dass die Kontrolle eines autorisierten Benutzers über eine Registerkarte nicht gehemmt wird, entfernt Teams die Registerkarte sowohl in Erfolgs- als auch in Fehlerfällen.
> * Nachdem Sie den `registerOnRemoveHandler` Ereignishandler aufgerufen haben, haben Sie 15 Sekunden Zeit, um auf die Methode zu reagieren. Standardmäßig aktiviert Teams die Schaltfläche "**Entfernen**" nach fünf Sekunden, auch wenn Sie nicht aufrufen`setValidityState(true)`.
> * Wenn der Benutzer "**Entfernen**" auswählt, entfernt Teams die Registerkarte nach 30 Sekunden, unabhängig davon, ob die Aktionen abgeschlossen wurden oder nicht.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md)

## <a name="see-also"></a>Siehe auch

* [Teams Registerkarten](~/tabs/what-are-tabs.md)
* [Erstellen einer persönlichen Registerkarte](~/tabs/how-to/create-personal-tab.md)
* [Erstellen einer Kanal- oder Gruppenregisterkarte](~/tabs/how-to/create-channel-group-tab.md)
* [Erstellen einer Konfigurationsseite](~/tabs/how-to/create-tab-pages/configuration-page.md)
