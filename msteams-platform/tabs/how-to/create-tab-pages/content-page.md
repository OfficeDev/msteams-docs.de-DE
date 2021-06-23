---
title: Erstellen einer Inhaltsseite
author: surbhigupta
description: Erstellen einer Inhaltsseite
keywords: teams tabs group channel configurable static
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: abb073cee4a9417ee4a9f095acdbe18c5e6d7713
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53068520"
---
# <a name="create-a-content-page-for-your-tab"></a>Erstellen einer Inhaltsseite für Ihre Registerkarte

Eine Inhaltsseite ist eine Webseite, die im Teams-Client gerendert wird. Diese sind in der Regel Teil von:

* Eine benutzerdefinierte Registerkarte mit persönlichem Bereich: In dieser Instanz ist die Inhaltsseite die erste Seite, auf die der Benutzer trifft.
* Eine benutzerdefinierte Kanal-/Gruppenregisterkarte: Nachdem der Benutzer die Registerkarte im entsprechenden Kontext angeheftet und konfiguriert hat, wird die Inhaltsseite angezeigt.
* Ein [Aufgabenmodul:](~/task-modules-and-cards/what-are-task-modules.md)Sie können eine Inhaltsseite erstellen und als Webansicht in ein Aufgabenmodul einbetten. Die Seite wird innerhalb des modalen Popups gerendert.

Dieser Artikel ist spezifisch für die Verwendung von Inhaltsseiten als Registerkarten. Der Großteil der hier aufgeführten Anleitungen würde jedoch unabhängig davon gelten, wie die Inhaltsseite dem Endbenutzer angezeigt wird.

## <a name="tab-content-and-design-guidelines"></a>Registerkarteninhalte und Entwurfsrichtlinien

Das übergeordnete Ziel Ihrer Registerkarte sollte es sein, den Zugriff auf aussagekräftige und ansprechende Inhalte zu ermöglichen, die einen praktischen Nutzen und einen offensichtlichen Zweck haben. Das bedeutet nicht, dass Sie auf einen ansprechenden Stil verzichten sollten, sondern sich auf die Minimierung von Unübersichtlichkeit konzentrieren sollten, indem Sie das Registerkartendesign übersichtlich, die Navigation intuitiv und den Inhalt immersiver gestalten.

Weitere Informationen finden Sie in den Richtlinien für das [Registerkartendesign](~/tabs/design/tabs.md) und [Microsoft Teams Richtlinien für die Store-Validierung](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md)

## <a name="integrate-your-code-with-teams"></a>Integrieren von Code in Teams

Damit Ihre Seite in Teams angezeigt werden kann, müssen Sie das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) und einen Aufruf nach `microsoftTeams.initialize()` dem Laden der Seite einschließen. So kommunizieren Ihre Seite und der Teams-Client:

```html
<!DOCTYPE html>
<html>
<head>
...
    <script src= 'https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js'></script>
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

## <a name="accessing-additional-content"></a>Zugreifen auf zusätzliche Inhalte

### <a name="using-the-sdk-to-interact-with-teams"></a>Verwenden des SDK für die Interaktion mit Teams

Das [Teams-Client-JavaScript-SDK](~/tabs/how-to/using-teams-client-sdk.md) bietet viele zusätzliche Funktionen, die Sie beim Entwickeln Ihrer Inhaltsseite möglicherweise hilfreich finden.

### <a name="deep-links"></a>Deep-Links

Sie können Deep-Links zu Entitäten in Teams erstellen. In der Regel werden diese zum Erstellen von Links verwendet, die zu Inhalten und Informationen auf Ihrer Registerkarte navigieren. Weitere Informationen finden Sie unter [Erstellen von Deep-Links zu Inhalten und Features in Microsoft Teams.](~/concepts/build-and-test/deep-links.md)

### <a name="task-modules"></a>Aufgabenmodule

Ein Aufgabenmodul ist eine modale Popup-ähnliche Oberfläche, die Sie von Ihrer Registerkarte aus auslösen können. In der Regel möchten Sie ihren Benutzer auf einer Inhaltsseite nicht durch mehrere Seiten navigieren. Stattdessen verwenden Sie Aufgabenmodule, um Formulare zum Sammeln zusätzlicher Informationen, zum Anzeigen der Details eines Elements in einer Liste oder zu jedem anderen Zeitpunkt, in dem Sie dem Benutzer zusätzliche Informationen präsentieren müssen, darzustellen. Die Aufgabenmodule selbst können zusätzliche Inhaltsseiten sein oder vollständig mit adaptiven Karten erstellt werden. Vollständige Informationen finden Sie [unter "Verwenden von Aufgabenmodulen in Registerkarten".](~/task-modules-and-cards/task-modules/task-modules-tabs.md)

### <a name="valid-domains"></a>Gültige Domänen

Stellen Sie sicher, dass alle URL-Domänen, die in Ihren Registerkarten verwendet werden, im `validDomains` Array ihres [Manifests](~/concepts/build-and-test/apps-package.md)enthalten sind. Weitere Informationen finden Sie unter ["validDomains"](~/resources/schema/manifest-schema.md#validdomains) in der Manifestschemareferenz. Beachten Sie jedoch, dass die Kernfunktionalität Ihrer Registerkarte innerhalb Teams und nicht außerhalb von Teams vorhanden ist.

## <a name="reorder-static-personal-tabs"></a>Neu anordnen statischer persönlicher Registerkarten

Ab Manifestversion 1.7 können Entwickler alle Registerkarten in ihrer persönlichen App neu anordnen. Insbesondere kann ein Entwickler die *Registerkarte "Bot-Chat",* die standardmäßig immer an die erste Position festgelegt ist, an eine beliebige Stelle in der Kopfzeile der persönlichen App-Registerkarte verschieben. Wir haben zwei reservierte Registerkartenentitäts-ID-Schlüsselwörter, *Unterhaltungen* und *Informationen* deklariert.

Wenn Sie einen Bot mit einem *persönlichen* Bereich erstellen, wird er standardmäßig an der ersten Registerkartenposition in einer persönlichen App angezeigt. Wenn Sie es an eine andere Position verschieben möchten, müssen Sie Ihrem Manifest ein statisches Registerkartenobjekt mit dem reservierten Schlüsselwort *Unterhaltungen* hinzufügen. Die  Unterhaltungsregisterkarte wird im Web oder Desktop angezeigt, je nach dem, wo Sie die *Unterhaltungsregisterkarte* im Array `staticTabs` hinzufügen. 

```json
{
   "staticTabs":[
      {
         
      },
      {
         "entityId":"conversations",
         "scopes":[
            "personal"
         ]
      }
   ]
}
```

## <a name="show-a-native-loading-indicator"></a>Anzeigen einer systemeigenen Ladeanzeige

Ab [Manifestschema v1.7](../../../resources/schema/manifest-schema.md)können Sie eine [systemeigene Ladeanzeige](../../../resources/schema/manifest-schema.md#showloadingindicator) unabhängig davon bereitstellen, wo Ihre Webinhalte in Teams geladen werden. Beispiel: [Registerkarteninhaltsseite,](#integrate-your-code-with-teams) [Konfigurationsseite,](configuration-page.md) [Entfernungsseite](removal-page.md)und [Aufgabenmodule in Registerkarten.](../../../task-modules-and-cards/task-modules/task-modules-tabs.md)

> [!NOTE]
> * Das Verhalten auf mobilen Clients kann über diese Manifesteigenschaft nicht konfiguriert werden. Mobile Clients zeigen standardmäßig eine systemeigene Ladeanzeige auf Inhaltsseiten und iframebasierten Aufgabenmodulen an. Dieser Indikator wird auf mobilen Geräten angezeigt, wenn eine Anforderung zum Abrufen von Inhalten gestellt wird, und wird geschlossen, sobald die Anforderung abgeschlossen ist.
> * Wenn Sie  `"showLoadingIndicator : true`  in Ihrem App-Manifest angeben, müssen alle Registerkartenkonfigurations-, Inhalts- und Entfernungsseiten und alle iframebasierten Aufgabenmodule dem obligatorischen Protokoll folgen:

**So zeigen Sie die Ladeanzeige an**

* Zu `"showLoadingIndicator": true` Ihrem Manifest hinzufügen. 
* Denken Sie daran, `microsoftTeams.initialize();` aufzurufen.
* **Optional:** Wenn Sie bereit sind, auf dem Bildschirm zu drucken und den Rest des Inhalts Ihrer Anwendung verzögert laden möchten, können Sie die Ladeanzeige manuell ausblenden, indem Sie `microsoftTeams.appInitialization.notifyAppLoaded();`
* **Obligatorisch:** Rufen Sie schließlich `microsoftTeams.appInitialization.notifySuccess()` auf, Teams zu benachrichtigen, dass Ihre App erfolgreich geladen wurde. Teams blendet dann ggf. die Ladeanzeige aus. Wenn  `notifySuccess`  die App nicht innerhalb von 30 Sekunden aufgerufen wird, wird davon ausgegangen, dass ein Timeout für Ihre App aufgetreten ist und ein Fehlerbildschirm mit einer Wiederholungsoption angezeigt wird.
* Wenn die Anwendung nicht geladen werden kann, können Sie Teams mitteilen, `microsoftTeams.appInitialization.notifyFailure(reason);` dass ein Fehler aufgetreten ist. Dem Benutzer wird dann ein Fehlerbildschirm angezeigt:

    ```typescript
    ``
    /* List of failure reasons */
    export const enum FailedReason {
        AuthFailed = "AuthFailed",
        Timeout = "Timeout",
        Other = "Other"
    }
    ```
    >
