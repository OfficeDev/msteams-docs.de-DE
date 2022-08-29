---
title: Erstellen einer Seite zum Entfernen von Registerkarten
author: surbhigupta
description: Erfahren Sie, wie Sie ihre Registerkarte nach der Installation neu konfigurieren können. Erweitern Sie die Benutzerfreundlichkeit, indem Sie Die Entfernungs- und Änderungsoptionen in der Microsoft Teams-App unterstützen.
ms.localizationpriority: high
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 6aa06cae222ad89b89b2eddc0ba224db0ff4225f
ms.sourcegitcommit: 87bba925d005eb331d876a0b9b75154f8100e911
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2022
ms.locfileid: "67450408"
---
# <a name="create-a-removal-page"></a>Erstellen einer Seite zum Entfernen

Sie können die Benutzererfahrung erweitern und verbessern, indem Sie Die Entfernungs- und Änderungsoptionen in Ihrer App unterstützen. Teams ermöglicht Benutzern das Umbenennen oder Entfernen einer Kanal- oder Gruppenregisterkarte, und Sie können Benutzern erlauben, Ihre Registerkarte nach der Installation neu zu konfigurieren. Darüber hinaus bietet die Registerkartenentfernung den Benutzern nach dem Entfernen Optionen zum Löschen oder Archivieren von Inhalten.

[!INCLUDE [sdk-include](~/includes/sdk-include.md)]

## <a name="enable-your-tab-to-be-reconfigured-after-installation"></a>Aktivieren der Neukonfiguration Ihrer Registerkarte nach der Installation

Sie `manifest.json` definieren die Features und Funktionen Ihrer Registerkarte. Die Registerkarteninstanzeigenschaft `canUpdateConfiguration` verwendet einen booleschen Wert, der angibt, ob ein Benutzer die Registerkarte nach der Erstellung ändern oder neu konfigurieren kann. Die folgende Tabelle enthält die Eigenschaftendetails:

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`canUpdateConfiguration`|Boolescher Wert|||Der Wert, der angibt, ob eine Instanz der Registerkartenkonfiguration nach der Erstellung vom Benutzer aktualisiert werden kann. Der Standardwert ist `true`. |

Wenn Ihre Registerkarte in einen Kanal- oder Gruppenchat hochgeladen wird, fügt Teams ein Dropdownmenü mit der rechten Maustaste für Ihre Registerkarte hinzu. Die verfügbaren Optionen werden durch die `canUpdateConfiguration` Einstellung bestimmt. Die folgende Tabelle enthält die Einstellungsdetails:

| `canUpdateConfiguration`| true   | false | description |
| ----------------------- | :----: | ----- | ----------- |
|     Einstellungen            |   √    |       |Die `configurationUrl` Seite wird in einem IFrame neu geladen, sodass der Benutzer die Registerkarte neu konfigurieren kann. |
|     Umbenennen              |   √    |   √   | Der Benutzer kann den Namen der Registerkarte ändern, wie er in der Registerkartenleiste angezeigt wird.          |
|     Entfernen              |   √    |   √   |  Wenn die Eigenschaft und der  `removeURL` Wert auf der **Konfigurationsseite** enthalten sind, wird die **Seite zum Entfernen** in einen IFrame geladen und dem Benutzer angezeigt. Wenn keine Seite zum Entfernen enthalten ist, wird dem Benutzer ein Bestätigungsdialogfeld angezeigt.          |

## <a name="create-a-tab-removal-page-for-your-application"></a>Erstellen einer Seite zum Entfernen von Registerkarten für Ihre Anwendung

Die optionale Seite zum Entfernen ist eine HTML-Seite, die Sie hosten, und wird angezeigt, wenn die Registerkarte entfernt wird. Die URL der Entfernungsseite wird von der `setConfig()` Methode (oder `setSettings()` vor TeamsJS v.2.0.0) auf Ihrer Konfigurationsseite festgelegt. Wie bei allen Seiten in Ihrer App muss die Seite zum Entfernen den [Voraussetzungen der Teams-Registerkarte](../../../tabs/how-to/tab-requirements.md) entsprechen.

### <a name="register-a-remove-handler"></a>Registrieren eines Remove-Handlers

Optional können Sie in der Logik der Entfernungsseite den `registerOnRemoveHandler((RemoveEvent) => {}` Ereignishandler aufrufen, wenn der Benutzer eine vorhandene Registerkartenkonfiguration entfernt. Die Methode übernimmt die [`RemoveEvent`](/javascript/api/@microsoft/teams-js/pages.config.removeevent?view=msteams-client-js-latest&preserve-view=true) Schnittstelle und führt den Code im Handler aus, wenn ein Benutzer versucht, Inhalte zu entfernen. Die Methode wird verwendet, um Bereinigungsvorgänge auszuführen, z. B. das Entfernen der zugrunde liegenden Ressource, die den Registerkarteninhalt läuft. Gleichzeitig kann nur ein Remove-Handler registriert werden.

Die `RemoveEvent` Schnittstelle beschreibt ein Objekt mit zwei Methoden:

* Die `notifySuccess()` Funktion ist erforderlich. Es gibt an, dass das Entfernen der zugrunde liegenden Ressource erfolgreich war und der Inhalt entfernt werden kann.

* Die `notifyFailure(string)` Funktion ist optional. Es weist darauf hin, dass das Entfernen der zugrunde liegenden Ressource fehlgeschlagen ist und der Inhalt nicht entfernt werden kann. Der optionale Zeichenfolgenparameter gibt einen Grund für den Fehler an. Falls angegeben, wird diese Zeichenfolge dem Benutzer angezeigt. andernfalls wird ein allgemeiner Fehler angezeigt.

#### <a name="use-the-getconfig-function"></a>Verwenden der `getConfig()` Funktion

Sie können `getConfig()` den zu entfernenden Registerkarteninhalt (früher `getSettings()`) zuweisen. Die `getConfig()` Funktion gibt eine Zusage zurück, die mit dem Config-Objekt aufgelöst wird, und stellt die gültigen Einstellungseigenschaftenwerte bereit, die abgerufen werden können.

#### <a name="use-the-getcontext-function"></a>Verwenden der `getContext()` Funktion

Sie können `getContext()` den aktuellen Kontext abrufen, in dem der Frame ausgeführt wird. Die `getContext()` Funktion gibt eine Zusage zurück, die mit dem Context-Objekt aufgelöst wird. Das Context-Objekt stellt gültige `Context` Eigenschaftswerte bereit, die Sie in der Logik der Entfernungsseite verwenden können, um den Inhalt zu bestimmen, der auf der Entfernungsseite angezeigt werden soll.

#### <a name="include-authentication"></a>Authentifizierung einschließen

Die Authentifizierung ist erforderlich, bevor ein Benutzer den Registerkarteninhalt löschen kann. Kontextinformationen können zum Erstellen von Authentifizierungsanforderungen und Autorisierungsseiten-URLs verwendet werden. Siehe [Microsoft Teams-Authentifizierungsfluss für Registerkarten](~/tabs/how-to/authentication/auth-flow-tab.md). Stellen Sie sicher, dass alle Domänen, die auf Ihren Registerkartenseiten verwendet werden, im `validDomains` Array Ihres App-Manifests aufgeführt sind.

Es folgt ein Beispielcodeblock zum Entfernen von Registerkarten:

# <a name="teamsjs-v2"></a>[TeamsJS v2](#tab/teamsjs-v2)

```html
<body>
  <button onclick="onClick()">Delete this tab and all underlying data?</button>
  <script type="module">
        import {app, pages} from 'https://res.cdn.office.net/teams-js/2.0.0/js/MicrosoftTeams.min.js';
    await app.initialize();
    pages.config.registerOnRemoveHandler((removeEvent) => {
      // Here you can designate the tab content to be removed and/or archived.
        const configPromise = pages.getConfig();
        configPromise.
            then((configuration) => {
                configuration.contentUrl = "...";
                removeEvent.notifySuccess()}).
            catch((error) => {removeEvent.notifyFailure("failure message")});
    });

    const onClick() => {
        pages.config.setValidityState(true);
    }
  </script>
</body>
```

# <a name="teamsjs-v1"></a>[TeamsJS v1](#tab/teamsjs-v1)

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

***

Wenn ein Benutzer "Aus dem Dropdownmenü der Registerkarte **entfernen** " auswählt, lädt Teams die optionale `removeUrl` Seite, die auf Ihrer **Konfigurationsseite** zugewiesen ist, in einen IFrame. Dem Benutzer wird eine Schaltfläche angezeigt, die mit der Funktion geladen wird, die `onClick()` die Schaltfläche "**Entfernen**" am unteren Rand der IFrame-Seite zum Entfernen aufruft `pages.config.setValidityState(true)` und aktiviert.

Nachdem der Remove-Handler ausgeführt wurde, `removeEvent.notifySuccess()` oder `removeEvent.notifyFailure()` benachrichtigt Teams über das Ergebnis der Inhaltsentfernung.

>[!NOTE]
>
> * Um sicherzustellen, dass die Kontrolle eines autorisierten Benutzers über eine Registerkarte nicht gehemmt wird, entfernt Teams die Registerkarte sowohl in Erfolgs- als auch in Fehlerfällen.
> * Nachdem Sie den `registerOnRemoveHandler` Ereignishandler aufgerufen haben, haben Sie 15 Sekunden Zeit, um auf die Methode zu reagieren. Standardmäßig aktiviert Teams die Schaltfläche " **Entfernen** " nach fünf Sekunden, auch wenn Sie nicht anrufen `setValidityState(true)`.
> * Wenn der Benutzer " **Entfernen**" auswählt, entfernt Teams die Registerkarte nach 30 Sekunden, unabhängig davon, ob die Aktionen abgeschlossen wurden oder nicht.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md)

## <a name="see-also"></a>Siehe auch

* [Microsoft Teams-Registerkarten](~/tabs/what-are-tabs.md)
* [Erstellen einer persönlichen Registerkarte](~/tabs/how-to/create-personal-tab.md)
* [Erstellen einer Kanal- oder Gruppenregisterkarte](~/tabs/how-to/create-channel-group-tab.md)
* [Erstellen einer Konfigurationsseite](~/tabs/how-to/create-tab-pages/configuration-page.md)
