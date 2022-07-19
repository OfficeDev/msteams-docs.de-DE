---
title: Erstellen einer Inhaltsseite
author: surbhigupta
description: In diesem Modul erfahren Sie, wie Sie eine Inhaltsseite für Ihre Registerkarten- und Registerkarteninhalte und Designrichtlinien erstellen.
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 4fd9c301ba48f346b9e721f5d6b3baa13ca50c04
ms.sourcegitcommit: 79d525c0be309200e930cdd942bc2c753d0b718c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2022
ms.locfileid: "66841969"
---
# <a name="create-a-content-page"></a>Erstellen einer Inhaltsseite

Eine Inhaltsseite ist eine Webseite, die im Teams-Client gerendert wird, die Teil von:

* Eine benutzerdefinierte Registerkarte mit persönlichem Bereich: In diesem Fall ist die Inhaltsseite die erste Seite, auf die der Benutzer trifft.
* Eine benutzerdefinierte Kanal- oder Gruppenregisterkarte: Die Inhaltsseite wird angezeigt, nachdem der Benutzer die Registerkarte im entsprechenden Kontext angehefteten und konfiguriert hat.
* Ein [Aufgabenmodul](~/task-modules-and-cards/what-are-task-modules.md): Sie können eine Inhaltsseite erstellen und als Webview in ein Aufgabenmodul einbetten. Die Seite wird innerhalb des modalen Popups gerendert.

Dieser Artikel betrifft die Verwendung von Inhaltsseiten als Registerkarten. der großteil der hier aufgeführten Anleitungen gilt jedoch unabhängig davon, wie die Inhaltsseite dem Benutzer präsentiert wird.

[!INCLUDE [sdk-include](~/includes/sdk-include.md)]

## <a name="tab-content-and-design-guidelines"></a>Registerkarteninhalte und Designrichtlinien

Das übergeordnete Ziel Ihrer Registerkarte ist es, Zugriff auf die aussagekräftigen und ansprechenden Inhalte zu ermöglichen, die einen praktischen Wert und einen offensichtlichen Zweck haben.

Sie müssen sich darauf konzentrieren, Das Registerkartendesign übersichtlich, die Navigation intuitiv und den Inhalt immersiv zu gestalten. Weitere Informationen finden Sie in den [Richtlinien für den Registerkartenentwurf](~/tabs/design/tabs.md) und [den Validierungsrichtlinien für den Microsoft Teams-Store](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md).

## <a name="integrate-your-code-with-teams"></a>Integrieren Ihres Codes in Teams

Damit Ihre Seite in Teams angezeigt werden kann, müssen Sie das [JavaScript-Client-SDK von Microsoft Teams](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) einschließen und einen Aufruf einschließen, nachdem `app.initialize()` Die Seite geladen wurde.

Der folgende Code enthält ein Beispiel für die Kommunikation Ihrer Seite und des Teams-Clients:

# <a name="teamsjs-v2"></a>[TeamsJS v2](#tab/teamsjs-v2)

```html
<!DOCTYPE html>
<html>
<head>
...
    <script src= 'https://res.cdn.office.net/teams-js/2.0.0/js/MicrosoftTeams.min.js'></script>
...
<body>
...
    <script type="module">
        import {app} from 'https://res.cdn.office.net/teams-js/2.0.0/js/MicrosoftTeams.min.js';
        await app.initialize();
    </script>
...
</body>
```

# <a name="teamsjs-v1"></a>[TeamsJS v1](#tab/teamsjs-v1)

```html
<!DOCTYPE html>
<html>
<head>
...
    <script src= 'https://statics.teams.cdn.office.net/sdk/v1.10.0/js/MicrosoftTeams.min.js'></script>
...
</head>

<body>
...
    <script>
    microsoftTeams.initialize();
    </script>
...
</body>
```

***

## <a name="access-additional-content"></a>Zugriff auf zusätzliche Inhalte

Sie können auf zusätzliche Inhalte zugreifen, indem Sie das SDK für die Interaktion mit Teams verwenden, Deep-Links erstellen, Aufgabenmodule verwenden und überprüfen, ob URL-Domänen im `validDomains` Array enthalten sind.

### <a name="use-the-sdk-to-interact-with-teams"></a>Verwenden des SDK für die Interaktion mit Teams

Das [Teams-Client-JavaScript-SDK](~/tabs/how-to/using-teams-client-sdk.md) bietet viele zusätzliche Funktionen, die Sie beim Entwickeln Ihrer Inhaltsseite hilfreich finden können.

### <a name="deep-links"></a>Deep-Links

Sie können Deeplinks zu Entitäten in Teams erstellen. Sie werden verwendet, um Links zu erstellen, die zu Inhalten und Informationen auf Ihrer Registerkarte navigieren. Weitere Informationen finden Sie unter [Erstellen von Deep-Links zu Inhalten und Features in Teams](~/concepts/build-and-test/deep-links.md).

### <a name="task-modules"></a>Aufgabenmodule

Ein Aufgabenmodul ist eine modale Popuperfahrung, die Sie über Ihre Registerkarte auslösen können. Verwenden Sie auf einer Inhaltsseite Aufgabenmodule, um Formulare zum Sammeln zusätzlicher Informationen, zum Anzeigen der Details eines Elements in einer Liste oder zum Präsentieren des Benutzers mit zusätzlichen Informationen darzustellen. Die Aufgabenmodule selbst können zusätzliche Inhaltsseiten sein oder vollständig mit adaptiven Karten erstellt werden. Weitere Informationen finden Sie [unter Verwenden von Aufgabenmodulen auf Registerkarten](~/task-modules-and-cards/task-modules/task-modules-tabs.md).

### <a name="valid-domains"></a>Gültige Domänen

Stellen Sie sicher, dass alle URL-Domänen, die auf Ihren Registerkarten verwendet werden, im `validDomains` Array in Ihrem [Manifest](~/concepts/build-and-test/apps-package.md) enthalten sind. Weitere Informationen finden Sie unter ["validDomains](~/resources/schema/manifest-schema.md#validdomains) " in der Manifestschemareferenz.

> [!NOTE]
> Die Kernfunktionalität Ihrer Registerkarte ist in Teams und nicht außerhalb von Teams vorhanden.

## <a name="show-a-native-loading-indicator"></a>Anzeigen eines systemeigenen Ladeindikators

Ab [Manifestschema v1.7](../../../resources/schema/manifest-schema.md) können Sie einen [systemeigenen Ladeindikator](../../../resources/schema/manifest-schema.md#showloadingindicator) bereitstellen. Beispiel: [Registerkarteninhaltsseite](#integrate-your-code-with-teams), [Konfigurationsseite](configuration-page.md), [Entfernungsseite](removal-page.md) und [Aufgabenmodule in Registerkarten](../../../task-modules-and-cards/task-modules/task-modules-tabs.md).

> [!NOTE]
>
> * Das Verhalten auf mobilen Clients kann nicht über die eigenschaft des nativen Ladeindikators konfiguriert werden. Mobile Clients zeigen diesen Indikator standardmäßig auf Inhaltsseiten und iframe-basierten Aufgabenmodulen an. Dieser Indikator auf mobilen Geräten wird angezeigt, wenn eine Anforderung zum Abrufen von Inhalten gestellt wird, und wird geschlossen, sobald die Anforderung abgeschlossen ist.

Wenn Sie in Ihrem App-Manifest angeben `showLoadingIndicator : true`  , müssen alle Registerkartenkonfigurationen, Inhalte, Entfernungsseiten und alle iframebasierten Aufgabenmodule die folgenden Schritte ausführen:

So zeigen Sie die Ladeanzeige an:

1. Fügen Sie Ihrem Manifest hinzu `"showLoadingIndicator": true` .
1. Aufrufen von `app.initialize();`
1. Rufen Sie `app.notifySuccess()` als **obligatorischen** Schritt Teams auf, um zu benachrichtigen, dass Ihre App erfolgreich geladen wurde. Anschließend blendet Teams ggf. den Ladeindikator aus. Wenn `notifySuccess`  Teams nicht innerhalb von 30 Sekunden aufgerufen wird, wird davon ausgegangen, dass die App ein Timeout hat, und es wird ein Fehlerbildschirm mit einer Wiederholungsoption angezeigt.
1. **Wenn Sie zum** Drucken auf dem Bildschirm bereit sind und den Rest des Anwendungsinhalts verzögert laden möchten, können Sie die Ladeanzeige manuell ausblenden, indem Sie aufrufen `app.notifyAppLoaded();`.
1. Wenn Ihre Anwendung nicht geladen wird, können Sie Teams über `app.notifyFailure({reason: app.FailedReason.Timeout, message: "failure message"});` den Fehler informieren und optional eine Fehlermeldung bereitstellen. Dem Benutzer wird ein Fehlerbildschirm angezeigt. Der folgende Code zeigt die Enumeration, die die möglichen Gründe definiert, die Sie für das Nichtladen der Anwendung angeben können:

    ```typescript
    /* List of failure reasons */
    export const enum FailedReason {
        AuthFailed = "AuthFailed",
        Timeout = "Timeout",
        Other = "Other"
    }
    ```

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen einer Konfigurationsseite](~/tabs/how-to/create-tab-pages/configuration-page.md)

## <a name="see-also"></a>Siehe auch

* [Microsoft Teams-Registerkarten](~/tabs/what-are-tabs.md)
* [Erstellen einer persönlichen Registerkarte](~/tabs/how-to/create-personal-tab.md)
* [Registerkartenlink entfalten und Bühnenansicht](~/tabs/tabs-link-unfurling.md)
* [Erstellen einer Konfigurationsseite](~/tabs/how-to/create-tab-pages/configuration-page.md)
* [Entwicklertools für Microsoft Teams-Registerkarten](~/tabs/how-to/developer-tools.md)
