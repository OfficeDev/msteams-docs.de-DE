---
title: Erstellen einer Inhaltsseite
author: surbhigupta
description: Erfahren Sie mehr über die Webseite innerhalb des Teams-Clients und ist Teil der benutzerdefinierten Registerkarte "Persönlich", "Kanal" oder "Gruppe". Erstellen Sie eine Inhaltsseite, und betten Sie sie als Webansicht innerhalb des Aufgabenmoduls ein.
ms.localizationpriority: high
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: dad5451c4255ad97cb14a13983f1701a52f39bb9
ms.sourcegitcommit: 0e4fcbc5efff4bfa1dbfba1e5467bbfaa6638705
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2022
ms.locfileid: "68773443"
---
# <a name="create-a-content-page"></a>Erstellen einer Inhaltsseite

Eine Inhaltsseite ist eine Webseite, die im Teams-Client gerendert wird, der Teil von:

* Eine benutzerdefinierte Registerkarte mit persönlichem Bereich: In diesem Fall ist die Inhaltsseite die erste Seite, auf die der Benutzer stößt.
* Eine benutzerdefinierte Kanal- oder Gruppenregisterkarte: Die Inhaltsseite wird angezeigt, nachdem der Benutzer die Registerkarte angeheftet und im entsprechenden Kontext konfiguriert hat.
* Ein [Aufgabenmodul](~/task-modules-and-cards/what-are-task-modules.md): Sie können eine Inhaltsseite erstellen und als Webansicht in ein Aufgabenmodul einbetten. Die Seite wird innerhalb des modale Popupfensters gerendert.

Dieser Artikel bezieht sich speziell auf die Verwendung von Inhaltsseiten als Registerkarten. Die meisten der hier aufgeführten Anleitungen gelten jedoch unabhängig davon, wie die Inhaltsseite dem Benutzer präsentiert wird.

[!INCLUDE [sdk-include](~/includes/sdk-include.md)]

## <a name="tab-content-and-design-guidelines"></a>Registerkarteninhalt und Entwurfsrichtlinien

Das allgemeine Ziel Ihrer Registerkarte besteht darin, Den Zugriff auf die sinnvollen und ansprechenden Inhalte zu ermöglichen, die einen praktischen Wert und einen offensichtlichen Zweck haben.

Sie müssen sich darauf konzentrieren, Ihr Registerkartendesign sauber, die Navigation intuitiv und den Inhalt immersiver zu gestalten. Weitere Informationen finden Sie unter [Richtlinien zum Entwerfen von Registerkarten](~/tabs/design/tabs.md) und [Richtlinien zur Überprüfung des Microsoft Teams-Stores](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md).

## <a name="integrate-your-code-with-teams"></a>Integrieren Ihres Codes in Teams

Damit Ihre Seite in Teams angezeigt werden kann, müssen Sie das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) einschließen und einen Aufruf von einschließen, `app.initialize()` nachdem Ihre Seite geladen wurde.

> [!NOTE]
> Es dauert fast 24 bis 48 Stunden, bis alle Inhalts- oder UI-Änderungen aufgrund des Caches in der Registerkarten-App widergespiegelt werden.

Der folgende Code enthält ein Beispiel dafür, wie Ihre Seite und der Teams-Client kommunizieren:

# <a name="teamsjs-v2"></a>[TeamsJS v2](#tab/teamsjs-v2)

```html
<!DOCTYPE html>
<html>
<head>
...
    <script src="https://res.cdn.office.net/teams-js/2.2.0/js/MicrosoftTeams.min.js" 
      integrity="sha384yBjE++eHeBPzIg+IKl9OHFqMbSdrzY2S/LW3qeitc5vqXewEYRWegByWzBN/chRh" 
      crossorigin="anonymous" >
    </script>
...
</head>
<body>
...
    <script>
    microsoftTeams.app.initialize();
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

Sie können auf zusätzliche Inhalte zugreifen, indem Sie das SDK verwenden, um mit Teams zu interagieren, DeepLinks zu erstellen, Aufgabenmodule zu verwenden und zu überprüfen, ob URL-Domänen im `validDomains` Array enthalten sind.

### <a name="use-the-sdk-to-interact-with-teams"></a>Verwenden des SDK für die Interaktion mit Teams

Das [Teams-Client-JavaScript SDK](~/tabs/how-to/using-teams-client-sdk.md) bietet viele weitere Funktionen, die Sie beim Entwickeln Ihrer Inhaltsseite nützlich finden können.

### <a name="deep-links"></a>Deep-Links

Sie können Deeplinks zu Entitäten in Teams erstellen. Sie werden verwendet, um Links zu erstellen, die zu Inhalten und Informationen auf Ihrer Registerkarte navigieren. Weitere Informationen finden Sie unter [Erstellen von Deep-Links zu Inhalten und Features in Teams](~/concepts/build-and-test/deep-links.md).

### <a name="task-modules"></a>Aufgabenmodule

Ein Aufgabenmodul ist eine modale Popupfunktion, die Sie über Ihre Registerkarte auslösen können. Verwenden Sie auf einer Inhaltsseite Aufgabenmodule, um Formulare zum Sammeln zusätzlicher Informationen, zum Anzeigen der Details eines Elements in einer Liste oder zum Präsentieren zusätzlicher Informationen für den Benutzer darzustellen. Die Aufgabenmodule selbst können zusätzliche Inhaltsseiten sein oder vollständig mit adaptiven Karten erstellt werden. Weitere Informationen finden Sie unter [Verwenden von Aufgabenmodulen in Registerkarten](~/task-modules-and-cards/task-modules/task-modules-tabs.md).

### <a name="valid-domains"></a>Gültige Domänen

Stellen Sie sicher, dass alle URL-Domänen, die `validDomains` in Ihren Registerkarten verwendet werden, im Array in Ihrem [Manifest](~/concepts/build-and-test/apps-package.md) enthalten sind. Weitere Informationen finden Sie unter [validDomains](~/resources/schema/manifest-schema.md#validdomains) in der Manifestschemareferenz.

> [!NOTE]
> Die Kernfunktionalität Ihrer Registerkarte ist innerhalb von Teams und nicht außerhalb von Teams vorhanden.

## <a name="show-a-native-loading-indicator"></a>Anzeigen eines nativen Ladeindikators

Ab [Manifestschema v1.7](../../../resources/schema/manifest-schema.md) können Sie einen [nativen Ladeindikator](../../../resources/schema/manifest-schema.md#showloadingindicator) bereitstellen. Beispielsweise [Registerkarteninhaltsseite](#integrate-your-code-with-teams), [Konfigurationsseite](configuration-page.md), [Entfernungsseite](removal-page.md) und [Aufgabenmodule in Registerkarten](../../../task-modules-and-cards/task-modules/task-modules-tabs.md).

> [!NOTE]
>
> * Das Verhalten auf mobilen Clients kann nicht über die Eigenschaft des nativen Ladeindikators konfiguriert werden. Mobile Clients zeigen diesen Indikator standardmäßig auf Inhaltsseiten und iFrame-basierten Aufgabenmodulen an. Dieser Indikator wird auf Mobilgeräten angezeigt, wenn eine Anforderung zum Abrufen von Inhalten gestellt wird und verworfen wird, sobald die Anforderung abgeschlossen ist.

Wenn Sie in Ihrem App-Manifest angeben `showLoadingIndicator : true`  , müssen alle Registerkartenkonfigurationen, Inhalte, Entfernungsseiten und alle iframe-basierten Aufgabenmodule die folgenden Schritte ausführen:

So zeigen Sie den Ladeindikator an:

1. Fügen Sie `"showLoadingIndicator": true` Ihrem Manifest hinzu.
1. Aufrufen von `app.initialize();`
1. Rufen Sie `app.notifySuccess()` als **obligatorischen** Schritt auf, um Teams zu benachrichtigen, dass Ihre App erfolgreich geladen wurde. Anschließend blendet Teams ggf. den Ladeindikator aus. Wenn `notifySuccess`  nicht innerhalb von 30 Sekunden aufgerufen wird, geht Teams davon aus, dass für Ihre App ein Timeout aufgetreten ist, und es wird ein Fehlerbildschirm mit einer Wiederholungsoption angezeigt.
1. **Wenn** Sie zum Drucken auf dem Bildschirm bereit sind und den restlichen Inhalt Ihrer Anwendung verzögert laden möchten, können Sie den Ladeindikator manuell ausblenden, indem Sie aufrufen `app.notifyAppLoaded();`.
1. Wenn Ihre Anwendung nicht geladen wird, können Sie aufrufen `app.notifyFailure({reason: app.FailedReason.Timeout, message: "failure message"});` , um Teams über den Fehler zu informieren und optional eine Fehlermeldung bereitzustellen. `notifyFailure` zeigt keine benutzerdefinierte Nachricht an. Dem Benutzer wird ein Fehlerbildschirm angezeigt. Der folgende Code zeigt die -Enumeration, die die möglichen Gründe definiert, die Sie für den Fehler beim Laden der Anwendung angeben können:

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
