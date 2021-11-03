---
title: Erstellen einer Inhaltsseite
author: surbhigupta
description: Erstellen einer Inhaltsseite
keywords: teams tabs group channel configurable static
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: e85e643179bf3c1c8b9aa3951f560e1f85dad0bc
ms.sourcegitcommit: 22c9e44437720d30c992a4a3626a2a9f745983c1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2021
ms.locfileid: "60720313"
---
# <a name="create-a-content-page-for-your-tab"></a>Erstellen einer Inhaltsseite für Ihre Registerkarte

Eine Inhaltsseite ist eine Webseite, die im Teams-Client gerendert wird. Diese sind Teil von:

* Eine benutzerdefinierte Registerkarte mit persönlichem Bereich: In diesem Fall ist die Inhaltsseite die erste Seite, auf die der Benutzer trifft.
* Eine benutzerdefinierte Kanal- oder Gruppenregisterkarte: Die Inhaltsseite wird angezeigt, nachdem der Benutzer die Registerkarte im entsprechenden Kontext angeheftet und konfiguriert hat.
* Ein [Aufgabenmodul:](~/task-modules-and-cards/what-are-task-modules.md)Sie können eine Inhaltsseite erstellen und als Webansicht in ein Aufgabenmodul einbetten. Die Seite wird innerhalb des modalen Popups gerendert.

Dieser Artikel ist spezifisch für die Verwendung von Inhaltsseiten als Registerkarten. Der Großteil der hier aufgeführten Anleitungen gilt jedoch unabhängig davon, wie die Inhaltsseite für den Benutzer angezeigt wird.

## <a name="tab-content-and-design-guidelines"></a>Registerkarteninhalte und Entwurfsrichtlinien

Das übergeordnete Ziel Ihrer Registerkarte besteht darin, den Zugriff auf aussagekräftige und ansprechende Inhalte zu ermöglichen, die einen praktischen Nutzen und einen offensichtlichen Zweck haben. Sie müssen sich darauf konzentrieren, das Registerkartendesign übersichtlich, navigations intuitiv und inhaltssiv zu gestalten.

Weitere Informationen finden Sie unter [Registerkartenentwurfsrichtlinien](~/tabs/design/tabs.md) und [Microsoft Teams Richtlinien für die Speichervalidierung.](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md)

## <a name="integrate-your-code-with-teams"></a>Integrieren von Code in Teams

Damit Ihre Seite in Teams angezeigt werden kann, müssen Sie das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) und einen Aufruf nach dem `microsoftTeams.initialize()` Laden der Seite einschließen. 

Der folgende Code enthält ein Beispiel dafür, wie Ihre Seite und der Teams-Client kommunizieren:

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

## <a name="access-additional-content"></a>Zugreifen auf zusätzliche Inhalte

Sie können auf zusätzliche Inhalte zugreifen, indem Sie das SDK verwenden, um mit Teams zu interagieren, Deep-Links zu erstellen, Aufgabenmodule zu verwenden und zu überprüfen, ob URL-Domänen im Array enthalten `validDomains` sind.

### <a name="use-the-sdk-to-interact-with-teams"></a>Verwenden des SDK für die Interaktion mit Teams

Das [Teams-Client-JavaScript-SDK](~/tabs/how-to/using-teams-client-sdk.md) bietet viele zusätzliche Funktionen, die Sie beim Entwickeln Ihrer Inhaltsseite hilfreich finden können.

### <a name="deep-links"></a>Deep-Links

Sie können Deep-Links zu Entitäten in Teams erstellen. Diese werden verwendet, um Links zu erstellen, die zu Inhalten und Informationen auf Ihrer Registerkarte navigieren. Weitere Informationen finden Sie unter [Erstellen von Deep-Links zu Inhalten und Features in Teams.](~/concepts/build-and-test/deep-links.md)

### <a name="task-modules"></a>Aufgabenmodule

Ein Aufgabenmodul ist eine modale Popupoberfläche, die Sie von Ihrer Registerkarte aus auslösen können. Auf einer Inhaltsseite können Sie Aufgabenmodule verwenden, um Formulare zum Sammeln zusätzlicher Informationen, zum Anzeigen der Details eines Elements in einer Liste oder zum Darstellen zusätzlicher Informationen für den Benutzer anzuzeigen. Die Aufgabenmodule selbst können zusätzliche Inhaltsseiten sein oder vollständig mit adaptiven Karten erstellt werden. Weitere Informationen finden Sie unter [Verwenden von Aufgabenmodulen in Registerkarten.](~/task-modules-and-cards/task-modules/task-modules-tabs.md)

### <a name="valid-domains"></a>Gültige Domänen

Stellen Sie sicher, dass alle URL-Domänen, die in Ihren Registerkarten verwendet werden, im `validDomains` Array ihres [Manifests](~/concepts/build-and-test/apps-package.md)enthalten sind. Weitere Informationen finden Sie unter ["validDomains"](~/resources/schema/manifest-schema.md#validdomains) in der Manifestschemareferenz.

> [!NOTE]
> Die Kernfunktionalität Ihrer Registerkarte befindet sich innerhalb Teams und nicht außerhalb von Teams.

## <a name="show-a-native-loading-indicator"></a>Anzeigen einer systemeigenen Ladeanzeige

Ab [Manifestschema v1.7](../../../resources/schema/manifest-schema.md)können Sie eine [systemeigene Ladeanzeige](../../../resources/schema/manifest-schema.md#showloadingindicator)bereitstellen. Beispiel: [Registerkarteninhaltsseite,](#integrate-your-code-with-teams) [Konfigurationsseite,](configuration-page.md) [Entfernungsseite](removal-page.md)und [Aufgabenmodule in Registerkarten.](../../../task-modules-and-cards/task-modules/task-modules-tabs.md)

> [!NOTE]
> * Das Verhalten auf mobilen Clients kann nicht über die systemeigene Ladeindikatoreigenschaft konfiguriert werden. Mobile Clients zeigen diesen Indikator standardmäßig auf Inhaltsseiten und iframebasierten Aufgabenmodulen an. Dieser Indikator wird auf mobilen Geräten angezeigt, wenn eine Anforderung zum Abrufen von Inhalten gestellt wird, und wird geschlossen, sobald die Anforderung abgeschlossen ist.

Wenn Sie `showLoadingIndicator : true`  in Ihrem App-Manifest angeben, müssen alle Registerkartenkonfigurationen, Inhalte, Entfernungsseiten und alle iframebasierten Aufgabenmodule die folgenden Schritte ausführen:

**So zeigen Sie die Ladeanzeige an**

1. Zu `"showLoadingIndicator": true` Ihrem Manifest hinzufügen.
1. Aufrufen von `microsoftTeams.initialize();`
1. Rufen Sie als **obligatorischen** Schritt `microsoftTeams.appInitialization.notifySuccess()` Teams auf, dass Ihre App erfolgreich geladen wurde. Teams blendet dann ggf. die Ladeanzeige aus. Wenn `notifySuccess`  die App nicht innerhalb von 30 Sekunden aufgerufen wird, wird davon ausgegangen, dass ein Timeout für Ihre App aufgetreten ist und ein Fehlerbildschirm mit einer Wiederholungsoption angezeigt wird.
1. **Optional** können Sie, wenn Sie bereit sind, auf dem Bildschirm zu drucken und den restlichen Inhalt Der Anwendung zu laden, die Ladeanzeige manuell ausblenden, indem Sie `microsoftTeams.appInitialization.notifyAppLoaded();` aufrufen.
1. Wenn ihre Anwendung nicht geladen werden kann, können Sie `microsoftTeams.appInitialization.notifyFailure(reason);` Teams mitteilen, dass ein Fehler aufgetreten ist. Dem Benutzer wird ein Fehlerbildschirm angezeigt. Der folgende Code enthält ein Beispiel für Anwendungsfehlerursachen:

    ```typescript
    /* List of failure reasons */
    export const enum FailedReason {
        AuthFailed = "AuthFailed",
        Timeout = "Timeout",
        Other = "Other"
    }
    ```

## <a name="see-also"></a>Siehe auch

* [registerkarten Teams](~/tabs/what-are-tabs.md)
* [Erstellen einer persönlichen Registerkarte](~/tabs/how-to/create-personal-tab.md)
* [Erstellen einer Kanal- oder Gruppenregisterkarte](~/tabs/how-to/create-channel-group-tab.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen einer Konfigurationsseite](~/tabs/how-to/create-tab-pages/configuration-page.md)
