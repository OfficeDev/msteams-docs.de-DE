---
title: Erstellen einer Inhaltsseite
author: laujan
description: Erstellen einer Inhaltsseite
keywords: Teams Registerkarten Gruppenkanal konfigurierbar statisch
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 136160cb9154d62be40d8e29075ac1fc86135a6b
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566677"
---
# <a name="create-a-content-page-for-your-tab"></a>Erstellen einer Inhaltsseite für Ihre Registerkarte

Eine Inhaltsseite ist eine Webseite, die innerhalb des Teams-Clients gerendert wird. In der Regel sind diese Teil von:

* Eine benutzerdefinierte Registerkarte mit persönlichem Umfang: In diesem Fall ist die Inhaltsseite die erste Seite, auf die der Benutzer trifft.
* Eine benutzerdefinierte Registerkarte "Kanal/Gruppe": Nachdem der Benutzer die Registerkarte im entsprechenden Kontext fixiert und konfiguriert hat, wird die Inhaltsseite angezeigt.
* Ein [Aufgabenmodul](~/task-modules-and-cards/what-are-task-modules.md): Sie können eine Inhaltsseite erstellen und als Webansicht in ein Aufgabenmodul einbetten. Die Seite wird im modalen Popup gerendert.

Dieser Artikel ist spezifisch für die Verwendung von Inhaltsseiten als Registerkarten; Der Großteil der Anleitungen würde hier jedoch unabhängig davon gelten, wie die Inhaltsseite dem Endbenutzer präsentiert wird.

## <a name="tab-content-and-design-guidelines"></a>Tab-Inhalt und Designrichtlinien

Das übergeordnete Ziel Ihrer Registerkarte sollte darin bestehen, den Zugriff auf aussagekräftige und ansprechende Inhalte zu ermöglichen, die einen praktischen Wert und einen offensichtlichen Zweck haben. Das bedeutet nicht, dass Sie auf einen ansprechenden Stil verzichten sollten, aber Sie sollten sich auf die Minimierung von Unordnung konzentrieren, indem Sie Ihr Tab-Design sauber, Navigation intuitiv und Inhalt immersive.

Weitere Informationen finden Sie in den Richtlinien für den [Tab-Design](~/tabs/design/tabs.md) und [Microsoft Teams-Richtlinien für](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md) die Speichervalidierung

## <a name="integrate-your-code-with-teams"></a>Integrieren Sie Ihren Code in Teams

Damit Ihre Seite in Teams angezeigt wird, müssen Sie das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) und einen Aufruf an die Seite nach dem `microsoftTeams.initialize()` Laden der Seite einfügen. So kommunizieren Ihre Seite und der Teams Client:

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

## <a name="accessing-additional-content"></a>Zugriff auf zusätzliche Inhalte

### <a name="using-the-sdk-to-interact-with-teams"></a>Verwenden des SDK zur Interaktion mit Teams

Das [Teams Client JavaScript SDK](~/tabs/how-to/using-teams-client-sdk.md) bietet viele zusätzliche Funktionen, die Sie beim Entwickeln Ihrer Inhaltsseite nützlich finden können.

### <a name="deep-links"></a>Deep-Links

Sie können tiefe Verknüpfungen zu Entitäten in Teams erstellen. In der Regel werden diese verwendet, um Links zu erstellen, die zu Inhalten und Informationen auf Ihrer Registerkarte navigieren. Weitere Informationen finden Sie unter [Erstellen von Deep Links zu Inhalten und Features in Microsoft Teams](~/concepts/build-and-test/deep-links.md).

### <a name="task-modules"></a>Aufgabenmodule

Ein Taskmodul ist eine modale Popup-ähnliche Erfahrung, die Sie von Ihrer Registerkarte aus auslösen können. In der Regel möchten Sie auf einer Inhaltsseite nicht durch mehrere Seiten navigieren. Stattdessen verwenden Sie Aufgabenmodule, um Formulare zum Sammeln zusätzlicher Informationen, Anzeigen der Details eines Elements in einer Liste oder zu jeder anderen Zeit, die Sie benötigen, um dem Benutzer zusätzliche Informationen zu präsentieren. Die Aufgabenmodule selbst können zusätzliche Inhaltsseiten sein oder vollständig mit Adaptive Cards erstellt werden. Weitere Informationen finden Sie unter [Verwenden von Aufgabenmodulen in Registerkarten.](~/task-modules-and-cards/task-modules/task-modules-tabs.md)

### <a name="valid-domains"></a>Gültige Domänen

Stellen Sie sicher, dass alle URL-Domänen, die auf Ihren Registerkarten verwendet werden, im Array in Ihrem Manifest enthalten `validDomains` sind. [](~/concepts/build-and-test/apps-package.md) Weitere Informationen finden Sie unter [validDomains](~/resources/schema/manifest-schema.md#validdomains) im Manifestschemaverweis. Beachten Sie jedoch, dass die Kernfunktionalität Ihrer Registerkarte innerhalb Teams und nicht außerhalb von Teams vorhanden ist.

## <a name="reorder-static-personal-tabs"></a>Neuanordnen statischer persönlicher Registerkarten

Ab Manifestversion 1.7 können Entwickler alle Registerkarten in ihrer persönlichen App neu anordnen. Insbesondere kann ein Entwickler die *Bot-Chat-Registerkarte* verschieben, die immer standardmäßig an die erste Position, an einer beliebigen Stelle im Header der persönlichen App-Registerkarte ist. Wir haben zwei reservierte Tab-EntitätId-Schlüsselwörter, *Unterhaltungen* und *über* deklariert.

Wenn Sie einen Bot mit einem *persönlichen* Bereich erstellen, wird er standardmäßig an der ersten Tabstoppposition in einer persönlichen App angezeigt. Wenn Sie es an eine andere Position verschieben möchten, müssen Sie Ihrem Manifest ein statisches Tabstoppobjekt mit dem reservierten Schlüsselwort *Unterhaltungen* hinzufügen. Die *Registerkarte Unterhaltung* wird im Web oder Desktop angezeigt, je nach dem Ort, an dem Sie die *Unterhaltungsregisterkarte* im `staticTabs` Array hinzufügen. 

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

## <a name="show-a-native-loading-indicator"></a>Anzeigen einer nativen Ladeanzeige

Ab [dem Manifestschema v1.7](../../../resources/schema/manifest-schema.md)können Sie überall dort, wo Ihre Webinhalte in Teams geladen werden, eine [systemeigene Ladeanzeige](../../../resources/schema/manifest-schema.md#showloadingindicator) bereitstellen. Beispiel: [Registerkarteninhaltsseite](#integrate-your-code-with-teams), [Konfigurationsseite](configuration-page.md), [Entfernungsseite](removal-page.md)und [Aufgabenmodule in Registerkarten](../../../task-modules-and-cards/task-modules/task-modules-tabs.md).

> [!NOTE]
> * Das Verhalten auf mobilen Clients kann über diese Manifesteigenschaft nicht konfiguriert werden. Mobile Clients zeigen standardmäßig eine systemeigene Ladeanzeige über Inhaltsseiten und iframe-basierte Aufgabenmodule hinweg an. Dieser Indikator auf Mobilgeräten wird angezeigt, wenn eine Anforderung zum Abrufen von Inhalten gestellt wird, und wird abgelehnt, sobald die Anforderung abgeschlossen wird.
> * Wenn Sie  `"showLoadingIndicator : true`  in Ihrem App-Manifest angeben, müssen alle Registerkartenkonfigurations-, Inhalts- und Entfernungsseiten sowie alle iframe-basierten Aufgabenmodule dem obligatorischen Protokoll folgen:

**So zeigen Sie die Ladeanzeige an**

* Fügen Sie `"showLoadingIndicator": true` Ihrem Manifest hinzu. 
* Denken Sie daran, `microsoftTeams.initialize();` anzurufen.
* **Optional**: Wenn Sie bereit sind, auf dem Bildschirm zu drucken und den Rest des Anwendungsinhalts nicht mehr laden möchten, können Sie die Ladeanzeige manuell ausblenden, indem Sie `microsoftTeams.appInitialization.notifyAppLoaded();`
* **Obligatorisch**: Rufen Sie schließlich `microsoftTeams.appInitialization.notifySuccess()` an, um Teams zu benachrichtigen, dass Ihre App erfolgreich geladen wurde. Teams blenden dann ggf. die Ladeanzeige aus. Wenn  `notifySuccess`  nicht innerhalb von 30 Sekunden aufgerufen wird, wird davon ausgegangen, dass eine Zeitlupe ihrer App auftritt und ein Fehlerbildschirm mit einer Wiederholungsoption angezeigt wird.
* Wenn Ihre Anwendung nicht geladen werden kann, können Sie `microsoftTeams.appInitialization.notifyFailure(reason);` aufrufen, um Teams zu informieren, dass ein Fehler aufgetreten ist. Anschließend wird dem Benutzer ein Fehlerbildschirm angezeigt:

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
