---
title: Entwerfen Ihrer App mit erweiterten UI-Komponenten
author: heath-hamilton
description: Erfahren Sie mehr über die Teams-UI-Komponenten, z. B. Breadcrumbs, Benachrichtigungsleiste, Phasenansicht sowie relevante Anwendungsfälle.
ms.author: surbhigupta
ms.localizationpriority: medium
ms.topic: reference
ms.openlocfilehash: 055ee4440982add222b76454f1ff4382f129ff21
ms.sourcegitcommit: c398dfdae9ed96f12e1401ac7c8d0228ff9c0a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2022
ms.locfileid: "66558842"
---
# <a name="designing-your-microsoft-teams-app-with-advanced-ui-components"></a>Entwerfen Ihrer Microsoft Teams-App mit erweiterten UI-Komponenten

Die folgenden Komponenten sind eine Kombination aus [grundlegenden UI-Komponenten](~/concepts/design/design-teams-app-basic-ui-components.md) , die Sie für allgemeine Teams-Entwurfssituationen wie navigation verwenden können.

## <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-UI-Kit

Basierend auf der <a href="https://fluentsite.z22.web.core.windows.net/" target="_blank">Fluent-Benutzeroberfläche</a> enthält das Microsoft Teams UI Kit Komponenten und Muster, die speziell für die Erstellung von Teams-Apps entwickelt wurden. Im UI-Kit können Sie die hier aufgeführten Komponenten direkt in Ihr Design aufnehmen und einfügen und weitere Beispiele für die Verwendung der einzelnen Komponenten anzeigen.

> [!div class="nextstepaction"]
> [Holen Sie sich das Microsoft Teams-UI-Kit (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="breadcrumb"></a>Breadcrumb

Breadcrumbs sind eine Navigationshilfe, die die Hierarchie Ihrer App vermittelt. Sie helfen Benutzern zu verstehen, wie die angezeigte Seite in die Gesamtoberfläche passt, und ermöglichen den Zugriff mit einem Klick auf höhere Ebenen in dieser Hierarchie.

### <a name="top-use-cases"></a>Die häufigsten Anwendungsfälle

* Kommunikationshierarchie
* Navigation

### <a name="mobile"></a>Mobilgerät

:::image type="content" source="../../assets/images/ui-templates/mobile-breadcrumb.png" alt-text="Das Beispiel zeigt eine Breadcrumb-Vorlage auf Mobilgeräten.":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/ui-templates/breadcrumb.png" alt-text="Das Beispiel zeigt eine Breadcrumbvorlage auf dem Desktop.":::

## <a name="left-nav"></a>Linker Navigationsbereich

Verwenden Sie die linke Navigationsleiste, um mehrere Seiten auf Ihrer Teams-Registerkarte zu durchsuchen. Im folgenden Beispiel befindet sich die linke Navigationsleiste zwischen der Kanalliste und dem Registerkarteninhalt.

### <a name="top-use-cases"></a>Die häufigsten Anwendungsfälle

* Durchsuchen Sie mehrere Seiten auf einer Teams-Registerkarte.
* Unterteilen Sie komplexe Apps in mehrere Seiten.

### <a name="mobile"></a>Mobilgerät

:::image type="content" source="../../assets/images/ui-templates/mobile-left-nav.png" alt-text="Das Beispiel zeigt eine linke Navigationsvorlage auf mobilgeräten.":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/ui-templates/left-nav.png" alt-text="Das Beispiel zeigt eine Linksnavigationsvorlage auf dem Desktop.":::

## <a name="notification-bar"></a>Benachrichtigungsleiste

Eine Benachrichtigungsleiste ist ein dedizierter Bereich zum Anzeigen einer kurzen, wichtigen Nachricht, in der der Benutzer keine sofortigen Maßnahmen ergreifen muss. Bestimmte Hintergrundfarben und Symbole sind bestimmten Nachrichtentypen zugeordnet (siehe unten).

Sie können eine Benachrichtigungsleiste mithilfe der Fluent [UI-Warnungskomponente](https://fluentsite.z22.web.core.windows.net/0.59.0/components/alert/definition) implementieren.

### <a name="top-use-cases"></a>Die häufigsten Anwendungsfälle

* Kritische Meldungen, Fehler und Warnungen
* Erfolgsmeldungen
* Informations- oder Werbenachrichten

### <a name="mobile"></a>Mobilgerät

:::image type="content" source="../../assets/images/ui-templates/mobile-notification-bar.png" alt-text="Beispiel zeigt die Benutzeroberflächenvorlage der Benachrichtigungsleiste auf mobilgeräten.":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/ui-templates/notification-bar.png" alt-text="Das Beispiel zeigt Ui-Vorlagen für die Benachrichtigungsleiste auf dem Desktop.":::

## <a name="stage-view"></a>Phasenansicht

Mit der Phasenansicht können Benutzer Inhalte wie ein Bild, eine Datei oder eine Website auf einer großen Oberfläche in Teams sehen, ohne den Kontext zu wechseln. Diese Komponente dient in erster Linie zum Anzeigen von Inhalten. Verwenden Sie es nicht für komplexe Interaktionen.

Erfahren Sie, wie Sie die [Phasenansicht](~/tabs/tabs-link-unfurling.md) implementieren.

### <a name="top-use-cases"></a>Die häufigsten Anwendungsfälle

* Anzeigen von Inhalten auf einer großen Oberfläche in Teams anstelle einer anderen App oder eines anderen Browsers
* Spotlight-Medien oder andere umfangreiche Inhalte

### <a name="mobile"></a>Mobilgerät

Ihre App kann eine Phase über eine adaptive Karte, einen freigegebenen Link oder visuelle Komponenten (z. B. ein Diagramm) starten.

:::image type="content" source="../../assets/images/ui-templates/mobile-stage.png" alt-text="Das Beispiel zeigt eine Phasenvorlage auf mobilen Geräten.":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/ui-templates/stage.png" alt-text="Das Beispiel zeigt eine Phasenvorlage auf dem Desktop.":::

## <a name="toolbar"></a>Symbolleiste

Eine Symbolleiste ist ein Container zum Gruppieren einer Gruppe von Steuerelementen.

### <a name="top-use-cases"></a>Die häufigsten Anwendungsfälle

* Kontextbezogene Aktionen für App-Inhalte.
* Kontextbezogener Filter und Suche.
* Navigation und Breadcrumbs.

### <a name="mobile"></a>Mobilgerät

:::image type="content" source="../../assets/images/ui-templates/mobile-toolbar.png" alt-text="Das Beispiel zeigt eine Symbolleistenvorlage auf mobilgeräten.":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/ui-templates/toolbar.png" alt-text="Das Beispiel zeigt eine Symbolleistenvorlage auf dem Desktop.":::
