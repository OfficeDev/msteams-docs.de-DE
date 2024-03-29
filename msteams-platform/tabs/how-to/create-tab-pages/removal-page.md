---
title: Erstellen einer Seite zum Entfernen von Registerkarten
author: surbhigupta
description: Erfahren Sie, wie Sie die Neukonfiguration Ihrer Registerkarte nach der Installation aktivieren. Erweitern Sie die Benutzererfahrung durch Unterstützung von Entfernungs- und Änderungsoptionen in der Microsoft Teams-App.
ms.localizationpriority: high
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 423cc386ca416fe116eb0bcb62c1238cae5547ff
ms.sourcegitcommit: 9ea9a70d2591bce6b8c980d22014e160f7b45f91
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2022
ms.locfileid: "68819940"
---
# <a name="create-a-removal-page"></a>Erstellen einer Seite zum Entfernen

Sie können die Benutzererfahrung erweitern und verbessern, indem Sie Die Entfernungs- und Änderungsoptionen in Ihrer App unterstützen. Teams ermöglicht Benutzern das Umbenennen oder Entfernen eines Kanals oder einer Gruppenregisterkarte, und Sie können Benutzern erlauben, Ihre Registerkarte nach der Installation neu zu konfigurieren. Darüber hinaus bietet die Registerkartenentfernung den Benutzern Optionen zum Löschen oder Archivieren von Inhalten nach dem Entfernen.

[!INCLUDE [sdk-include](~/includes/sdk-include.md)]

## <a name="enable-your-tab-to-be-reconfigured-after-installation"></a>Aktivieren der Neukonfiguration Ihrer Registerkarte nach der Installation

Ihre `manifest.json` definiert die Features und Funktionen Ihrer Registerkarte. Die Eigenschaft der Registerkarteninstanz `canUpdateConfiguration` akzeptiert einen booleschen Wert, der angibt, ob ein Benutzer die Registerkarte ändern oder neu konfigurieren kann, nachdem sie erstellt wurde. Die folgende Tabelle enthält die Eigenschaftendetails:

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`canUpdateConfiguration`|Boolescher Wert|||Der Wert, der angibt, ob eine Instanz der Registerkartenkonfiguration nach der Erstellung vom Benutzer aktualisiert werden kann. Der Standardwert ist `true`. |

Wenn Ihre Registerkarte in einen Kanal oder Gruppenchat hochgeladen wird, fügt Teams ein Rechtsklick-Dropdownmenü für Ihre Registerkarte hinzu. Die verfügbaren Optionen werden durch die `canUpdateConfiguration` Einstellung bestimmt. Die folgende Tabelle enthält die Einstellungsdetails:

| `canUpdateConfiguration`| true   | false | description |
| ----------------------- | :----: | ----- | ----------- |
|     Einstellungen            |   √    |       |Die `configurationUrl` Seite wird in einem iFrame neu geladen, sodass der Benutzer die Registerkarte neu konfigurieren kann. |
|     Umbenennen              |   √    |   √   | Der Benutzer kann den Namen der Registerkarte so ändern, wie er in der Registerkartenleiste angezeigt wird.          |
|     Entfernen              |   √    |   √   |  Wenn die Eigenschaft und der  `removeURL` Wert auf der **Konfigurationsseite** enthalten sind, wird die **Seite zum Entfernen** in einen iFrame geladen und dem Benutzer angezeigt. Wenn keine Seite zum Entfernen enthalten ist, wird dem Benutzer ein Bestätigungsdialogfeld angezeigt.          |

## <a name="create-a-tab-removal-page-for-your-application"></a>Erstellen einer Registerkartenentfernungsseite für Ihre Anwendung

Die optionale Seite zum Entfernen ist eine HTML-Seite, die Sie hosten und angezeigt wird, wenn die Registerkarte entfernt wird. Die URL der Entfernungsseite wird von der `setConfig()` -Methode (oder `setSettings()` vor TeamsJS v.2.0.0) auf Ihrer Konfigurationsseite angegeben. Wie bei allen Seiten in Ihrer App muss die Seite zum Entfernen die [Voraussetzungen für die Registerkarte "Teams"](../../../tabs/how-to/tab-requirements.md) erfüllen.

### <a name="register-a-remove-handler"></a>Registrieren eines Remove-Handlers

Optional können Sie innerhalb der Logik der Entfernungsseite den `registerOnRemoveHandler((RemoveEvent) => {}` Ereignishandler aufrufen, wenn der Benutzer eine vorhandene Registerkartenkonfiguration entfernt. Die -Methode akzeptiert die [`RemoveEvent`](/javascript/api/@microsoft/teams-js/pages.config.removeevent?view=msteams-client-js-latest&preserve-view=true) -Schnittstelle und führt den Code im Handler aus, wenn ein Benutzer versucht, Inhalte zu entfernen. Die -Methode wird verwendet, um Bereinigungsvorgänge auszuführen, z. B. das Entfernen der zugrunde liegenden Ressource, die den Registerkarteninhalt mit Energie versorgt. Es kann jeweils nur ein Handler zum Entfernen registriert werden.

Die `RemoveEvent` -Schnittstelle beschreibt ein -Objekt mit zwei Methoden:

* Die `notifySuccess()` Funktion ist erforderlich. Es gibt an, dass die entfernung der zugrunde liegenden Ressource erfolgreich war und ihr Inhalt entfernt werden kann.

* Die `notifyFailure(string)` Funktion ist optional. Es weist darauf hin, dass das Entfernen der zugrunde liegenden Ressource fehlgeschlagen ist und deren Inhalt nicht entfernt werden kann. Der optionale Zeichenfolgenparameter gibt einen Grund für den Fehler an. Falls angegeben, wird diese Zeichenfolge dem Benutzer angezeigt. andernfalls wird ein generischer Fehler angezeigt.

#### <a name="use-the-getconfig-function"></a>Verwenden der `getConfig()` Funktion

Sie können (früher `getSettings()`) verwenden `getConfig()` , um den zu entfernenden Registerkarteninhalt zuzuweisen. Die `getConfig()` Funktion gibt eine Zusage zurück, die mit dem Config-Objekt aufgelöst wird, und stellt die gültigen Einstellungseigenschaftswerte bereit, die abgerufen werden können.

#### <a name="use-the-getcontext-function"></a>Verwenden der `getContext()` Funktion

Sie können verwenden `getContext()` , um den aktuellen Kontext abzurufen, in dem der Frame ausgeführt wird. Die `getContext()` Funktion gibt eine Zusage zurück, die mit dem Context-Objekt aufgelöst wird. Das Context-Objekt stellt gültige `Context` Eigenschaftswerte bereit, die Sie in der Logik der Entfernungsseite verwenden können, um den Inhalt zu bestimmen, der auf der Entfernungsseite angezeigt werden soll.

#### <a name="include-authentication"></a>Einschließen der Authentifizierung

Eine Authentifizierung ist erforderlich, bevor ein Benutzer den Inhalt der Registerkarte löschen kann. Kontextinformationen können zum Erstellen von Authentifizierungsanforderungen und Autorisierungsseiten-URLs verwendet werden. [Registerkarten finden Sie unter Microsoft Teams-Authentifizierungsflow](~/tabs/how-to/authentication/auth-flow-tab.md). Stellen Sie sicher, dass alle Domänen, die `validDomains` auf Ihren Registerkartenseiten verwendet werden, im Array Ihres App-Manifests aufgeführt sind.

Es folgt ein Beispiel für den Codeblock zum Entfernen von Registerkarten:

# <a name="teamsjs-v2"></a>[TeamsJS v2](#tab/teamsjs-v2)

```html
<body>
  <button onclick="onClick()">Delete this tab and all underlying data?</button>
  <script>
    await microsoftTeams.app.initialize();
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

Wenn ein Benutzer im Dropdownmenü der Registerkarte **Entfernen** auswählt, lädt Teams die auf Ihrer **Konfigurationsseite** zugewiesene optionale `removeUrl` Seite in einen iFrame. Dem Benutzer wird eine Schaltfläche angezeigt, die mit der `onClick()` Funktion geladen ist, die die Schaltfläche **Entfernen** aufruft `pages.config.setValidityState(true)` und aktiviert, die unten auf der Entfernungsseite iFrame angezeigt wird.

Nachdem der Entfernungshandler ausgeführt wurde, `removeEvent.notifySuccess()` oder `removeEvent.notifyFailure()` benachrichtigt Teams über das Ergebnis der Inhaltsentfernung.

>[!NOTE]
>
> * Um sicherzustellen, dass die Kontrolle eines autorisierten Benutzers über eine Registerkarte nicht behindert wird, entfernt Teams die Registerkarte sowohl in Erfolgs- als auch in Fehlerfällen.
> * Nachdem Sie den `registerOnRemoveHandler` Ereignishandler aufgerufen haben, haben Sie 15 Sekunden Zeit, um auf die -Methode zu antworten. Standardmäßig aktiviert Teams die Schaltfläche **Entfernen** nach fünf Sekunden, auch wenn Sie nicht aufrufen `setValidityState(true)`.
> * Wenn der Benutzer **Entfernen** auswählt, entfernt Teams die Registerkarte nach 30 Sekunden, unabhängig davon, ob die Aktionen abgeschlossen wurden oder nicht.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md)

## <a name="see-also"></a>Siehe auch

* [Erstellen von Registerkarten für Teams](../../what-are-tabs.md)
* [App-Manifestschema für Teams](../../../resources/schema/manifest-schema.md)
* [RemoveEvent-Schnittstelle](/javascript/api/@microsoft/teams-js/pages.config.removeevent)
* [Kontext für Ihre Registerkarte erhalten](../access-teams-context.md)
* [Erstellen einer persönlichen Registerkarte](../create-personal-tab.md)
* [Erstellen einer Kanalregisterkarte oder Gruppenregisterkarte](../create-channel-group-tab.md)
