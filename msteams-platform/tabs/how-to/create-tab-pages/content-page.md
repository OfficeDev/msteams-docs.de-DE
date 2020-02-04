---
title: Erstellen einer Inhaltsseite
author: laujan
description: ''
keywords: Teams-Registerkartengruppe Kanal konfigurierbar statisch
ms.topic: conceptual
ms.author: v-laujan
ms.openlocfilehash: ac85e000c9bdaebf28cb33143a7c82a348d3771e
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674332"
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

Damit Ihre Seite in Teams angezeigt wird, müssen Sie das [Microsoft Teams-JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest) einschließen und `microsoftTeams.initialize()` nach dem Laden einer Seite einen Anruf hinzufügen. So kommunizieren Ihre Seite und der Microsoft Teams-Client:

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

Das Microsoft [Teams-Client-JavaScript-SDK](~/tabs/how-to/using-teams-client-sdk.md) bietet viele zusätzliche Funktionen, die Sie beim Entwickler Ihrer Inhaltsseite möglicherweise nützlich finden.

### <a name="deep-links"></a>Deep links

Sie können tiefe Links zu Entitäten in Microsoft Teams erstellen. Diese werden normalerweise verwendet, um Links zu erstellen, die zu Inhalten und Informationen in ihrer Registerkarte navigieren. Weitere Informationen finden Sie unter [Erstellen von tiefen Links zu Inhalten und Features in Microsoft Teams](~/concepts/build-and-test/deep-links.md).

### <a name="task-modules"></a>Aufgaben Module

Ein Aufgabenmodul ist eine modale Popup-ähnliche Erfahrung, die Sie auf der Registerkarte auslösen können. in der Regel auf einer Inhaltsseite möchten Sie nicht über mehrere Seiten in den Benutzer navigieren. Stattdessen verwenden Sie Aufgaben Module zum Darstellen von Formularen zum Sammeln zusätzlicher Informationen, zum Anzeigen der Details eines Elements in einer Liste oder zu einem anderen Zeitpunkt, zu dem Sie dem Benutzer zusätzliche Informationen zur Verfügung stellen müssen. Die Aufgaben Module selbst können zusätzliche Inhaltsseiten sein oder vollständig mit adaptiven Karten erstellt werden. Vollständige Informationen finden Sie unter [Verwenden von Aufgaben Modulen in Registerkarten](~/task-modules-and-cards/task-modules/task-modules-tabs.md) .

### <a name="valid-domains"></a>Gültige Domänen

Stellen Sie sicher, dass die in ihren Registerkarten verwendeten URL-Domänen `validDomains` in dem Array in Ihrem [Manifest](~/concepts/build-and-test/apps-package.md)enthalten sind. Weitere Informationen finden Sie unter [validDomains](~/resources/schema/manifest-schema.md#validdomains) in der Manifest-Schemareferenz. Beachten Sie jedoch, dass die Kernfunktionen Ihrer Registerkarte in Microsoft Teams und nicht außerhalb von Teams vorhanden sind.
