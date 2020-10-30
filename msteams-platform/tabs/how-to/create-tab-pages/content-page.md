---
title: Erstellen einer Inhaltsseite
author: laujan
description: Vorgehensweise Erstellen einer Inhaltsseite
keywords: Teams-Registerkartengruppe Kanal konfigurierbar statisch
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 62a398c87b681013c89e540d2bdc463c97877307
ms.sourcegitcommit: 3fc7ad33e2693f07170c3cb1a0d396261fc5c619
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "48796316"
---
# <a name="create-a-content-page-for-your-tab"></a>Erstellen einer Inhaltsseite für die Registerkarte

Eine Inhaltsseite ist eine Webseite, die im Microsoft Teams-Client gerendert wird. Diese sind in der Regel Bestandteil von:

* Eine benutzerdefinierte Registerkarte auf persönlicher Ebene – in dieser Instanz ist die Inhaltsseite die erste Seite, auf die der Benutzer stößt.
* Eine benutzerdefinierte Kanal/Gruppe-Registerkarte – nachdem der Benutzer die Registerkarte im entsprechenden Kontext fixiert und konfiguriert hat, wird die Inhaltsseite angezeigt.
* Ein [Aufgabenmodul](~/task-modules-and-cards/what-are-task-modules.md) -Sie können eine Inhaltsseite erstellen und als WebView in ein Aufgabenmodul einbetten. Die Seite wird innerhalb des modalen Popups gerendert.

Dieser Artikel ist spezifisch für die Verwendung von Inhaltsseiten als Registerkarten; Allerdings würde der Großteil der Anleitung hier angewendet, unabhängig davon, wie die Inhaltsseite dem Endbenutzer angezeigt wird.

## <a name="tab-content-and-style-guidelines"></a>Inhalts-und Stilrichtlinien für Registerkarten

Das allgemeine Ziel ihrer Registerkarte sollte es sein, den Zugriff auf aussagekräftige und ansprechende Inhalte zu ermöglichen, die einen praktischen Nutzen und einen offensichtlichen Zweck haben. Das bedeutet nicht, dass Sie auf eine erfreuliche Art verzichten sollten, aber Sie sollten sich darauf konzentrieren, die Übersichtlichkeit zu minimieren, indem Sie das Design Ihrer Registerkarte sauber, die Navigation intuitiv und die Inhalte immersive machen. Informationen [zu Inhalten und Unterhaltungen auf einmal mithilfe von Tabs](~/tabs/design/tabs.md) und [Microsoft Teams-App-Genehmigungsprozess Anleitungen](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md)

## <a name="integrate-your-code-with-teams"></a>Integrieren von Code in Microsoft Teams

Damit Ihre Seite in Teams angezeigt wird, müssen Sie das [Microsoft Teams-JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latestadd &preserve-view=true) einschließen und nach dem Laden einer Seite einen Anruf hinzufügen `microsoftTeams.initialize()` . So kommunizieren Ihre Seite und der Microsoft Teams-Client:

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

## <a name="accessing-additional-content"></a>Zugreifen auf zusätzlichen Inhalt

### <a name="using-the-sdk-to-interact-with-teams"></a>Verwenden des SDK für die Interaktion mit Microsoft Teams

Das Microsoft [Teams-Client-JavaScript-SDK](~/tabs/how-to/using-teams-client-sdk.md) bietet viele zusätzliche Funktionen, die Sie beim Entwickeln Ihrer Inhaltsseite nützlich finden können.

### <a name="deep-links"></a>Deep-Links

Sie können tiefe Links zu Entitäten in Microsoft Teams erstellen. Diese werden normalerweise verwendet, um Links zu erstellen, die zu Inhalten und Informationen in ihrer Registerkarte navigieren. Weitere Informationen finden Sie unter [Erstellen von tiefen Links zu Inhalten und Features in Microsoft Teams](~/concepts/build-and-test/deep-links.md).

### <a name="task-modules"></a>Aufgaben Module

Ein Aufgabenmodul ist eine modale Popup-ähnliche Erfahrung, die Sie auf der Registerkarte auslösen können. Normalerweise möchten Sie auf einer Inhaltsseite nicht durch mehrere Seiten navigieren. Stattdessen verwenden Sie Aufgaben Module zum Darstellen von Formularen zum Sammeln zusätzlicher Informationen, zum Anzeigen der Details eines Elements in einer Liste oder zu einem anderen Zeitpunkt, zu dem Sie dem Benutzer zusätzliche Informationen zur Verfügung stellen müssen. Die Aufgaben Module selbst können zusätzliche Inhaltsseiten sein oder vollständig mit adaptiven Karten erstellt werden. Vollständige Informationen finden Sie unter [Verwenden von Aufgaben Modulen in Registerkarten](~/task-modules-and-cards/task-modules/task-modules-tabs.md) .

### <a name="valid-domains"></a>Gültige Domänen

Stellen Sie sicher, dass die in ihren Registerkarten verwendeten URL-Domänen in dem `validDomains` Array in Ihrem [Manifest](~/concepts/build-and-test/apps-package.md)enthalten sind. Weitere Informationen finden Sie unter [validDomains](~/resources/schema/manifest-schema.md#validdomains) in der Manifest-Schemareferenz. Beachten Sie jedoch, dass die Kernfunktionen Ihrer Registerkarte in Microsoft Teams und nicht außerhalb von Teams vorhanden sind.

## <a name="show-a-native-loading-indicator"></a>Anzeigen eines systemeigenen Lade Indikators

Beginnend mit dem [Manifest-Schema v 1.7](../../../resources/schema/manifest-schema.md)können Sie einen [systemeigenen Lade Indikator](../../../resources/schema/manifest-schema.md#showloadingindicator) bereitstellen, unabhängig davon, wo Ihre Webinhalte in Microsoft Teams geladen werden, beispielsweise [Registerkarteninhalts Seite](#integrate-your-code-with-teams), [Konfigurationsseite](configuration-page.md), [Entfernungs Seite](removal-page.md) und [Aufgaben Module in Registerkarten](../../../task-modules-and-cards/task-modules/task-modules-tabs.md).

> [!NOTE]
> Wenn Sie  `"showLoadingIndicator : true`  in Ihrem App-Manifest angeben, müssen alle Seiten für Registerkartenkonfiguration, Inhalt und Entfernung sowie alle IFRAME-basierten Aufgaben Module dem obligatorischen Protokoll unten entsprechen:

1. Um den Lade Indikator anzuzeigen, fügen Sie `"showLoadingIndicator": true` zu ihrem Manifest hinzu. 
2. Denken Sie daran, anzurufen `microsoftTeams.initialize();` .
3. **Optional** . Wenn Sie zum Drucken auf dem Bildschirm und zum verzögerten Laden des restlichen Inhalts Ihrer Anwendung fähig sind, können Sie den Lade Indikator manuell ausblenden, indem Sie `microsoftTeams.appInitialization.notifyAppLoaded();`
4. **Obligatorisch** . Schließlich rufen Sie die Teams darauf hin `microsoftTeams.appInitialization.notifySuccess()` , dass Ihre APP erfolgreich geladen wurde. Teams werden dann den Lade Indikator ausblenden, falls zutreffend. Wenn  `notifySuccess`  nicht innerhalb von 30 Sekunden aufgerufen wird, wird davon ausgegangen, dass Ihre APP abgelaufen ist und ein Fehlerbildschirm mit einer Wiederholungsoption angezeigt wird.
5. Wenn Ihre Anwendung nicht laden kann, können Sie aufrufen `microsoftTeams.appInitialization.notifyFailure(reason);` , um Microsoft Teams mitzuteilen, dass ein Fehler aufgetreten ist. Dem Benutzer wird dann ein Fehlerbildschirm angezeigt:

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
