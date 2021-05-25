---
title: Entwerfen Ihrer App mit erweiterten Benutzeroberflächenkomponenten
author: heath-hamilton
description: Erfahren Sie mehr über die benutzeroberflächenkomponenten, die in Teams.
ms.author: surbhigupta
localization_priority: Normal
ms.topic: reference
ms.openlocfilehash: ae1c2793586dc638d56051e105482aac92e01091
ms.sourcegitcommit: 4224c44d169b1a289cbf1d3353de6bc6de7c7ea8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2021
ms.locfileid: "52644929"
---
# <a name="designing-your-microsoft-teams-app-with-advanced-ui-components"></a>Entwerfen Ihrer Microsoft Teams-App mit erweiterten Benutzeroberflächenkomponenten

Die folgenden Komponenten sind eine Kombination aus einfachen [Benutzeroberflächenkomponenten,](~/concepts/design/design-teams-app-basic-ui-components.md) die Sie für allgemeine Teams verwenden können, z. B. Navigation.

## <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-UI-Kit

Basierend auf <a href="https://fluentsite.z22.web.core.windows.net/" target="_blank">der Fluent-Benutzeroberfläche</a>enthält das Microsoft Teams UI Kit Komponenten und Muster, die speziell für das Erstellen von apps Teams sind. Im UI Kit können Sie die hier aufgeführten Komponenten direkt in Ihren Entwurf packen und einfügen und weitere Beispiele für die Verwendung der einzelnen Komponenten anzeigen.

> [!div class="nextstepaction"]
> [Holen Sie sich das Microsoft Teams-UI-Kit (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="breadcrumb"></a>Breadcrumb

Breadcrumbs sind eine Navigationshilfe, die die Hierarchie Ihrer App vermittelt. Sie helfen Benutzern, zu verstehen, wie die angezeigte Seite in die Allgemeine Benutzererfahrung passt, und ermöglichen mit einem Klick Zugriff auf höhere Ebenen in dieser Hierarchie.

### <a name="top-use-cases"></a>Die am besten verwendeten Fälle

* Hierarchie kommunizieren
* Navigation

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/breadcrumb.png" alt-text="Beispiel zeigt eine Breadcrumbvorlage auf dem Desktop." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-breadcrumb.png" alt-text="Beispiel zeigt eine Breadcrumbvorlage auf mobilen Geräten." border="false":::

---

## <a name="left-nav"></a>Linkes Navigationsgerät

Verwenden Sie das linke Navigations navi, um mehrere Seiten innerhalb ihrer Registerkarte Teams durchsuchen. Im folgenden Beispiel befindet sich das linke Navigationsgerät zwischen der Kanalliste und dem Registerkarteninhalt.

### <a name="top-use-cases"></a>Die am besten verwendeten Fälle

* Durchsuchen Sie mehrere Seiten innerhalb Teams Registerkarte.
* Unterlegen Sie komplexe Apps in mehrere Seiten.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/left-nav.png" alt-text="Beispiel zeigt eine linke Navigationsvorlage auf dem Desktop." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-left-nav.png" alt-text="Beispiel zeigt eine linke Navigationsvorlage auf mobilen Geräten." border="false":::

---

## <a name="notification-bar"></a>Benachrichtigungsleiste

Eine Benachrichtigungsleiste ist ein dedizierter Bereich zum Anzeigen einer kurzen, wichtigen Nachricht, für die der Benutzer keine sofortigen Maßnahmen ergreifen muss. Bestimmte Hintergrundfarben und Symbole sind bestimmten Nachrichtentypen zugeordnet (siehe unten).

### <a name="top-use-cases"></a>Die am besten verwendeten Fälle

* Wichtige Meldungen, Fehler und Warnungen
* Erfolgsmeldungen
* Informations- oder Werbenachrichten

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/notification-bar.png" alt-text="Beispiel zeigt Benachrichtigungsleisten-UI-Vorlagen auf dem Desktop." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-notification-bar.png" alt-text="Beispiel zeigt die Benutzeroberflächenvorlage für die Benachrichtigungsleiste auf Mobilgeräten." border="false":::

---

## <a name="stage"></a>Stufe

Stage bietet Benutzern die Möglichkeit, eine Entität wie ein Bild, eine Datei oder eine Website in Teams zu öffnen, anstatt sie in einer anderen App oder einem anderen Browser zu öffnen. Der primäre Verwendungsfall der Phase ist die Anzeige. die Oberfläche sollte nicht für komplexe Interaktionen verwendet werden.

(Implementierungshinweis: Erstellen Sie Ihre Phase mithilfe eines großen [Aufgabenmoduls](../../task-modules-and-cards/task-modules/design-teams-task-modules.md).)

### <a name="top-use-cases"></a>Die am besten verwendeten Fälle

* Öffnen einer Entität in Teams anstelle einer anderen App oder eines anderen Browsers
* Spotlight-Medien oder andere Inhalte

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/stage.png" alt-text="Beispiel zeigt eine Stage-Vorlage auf dem Desktop." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

Ihre App kann eine Phase über eine adaptive Karte, einen freigegebenen Link oder visuelle Komponenten (z. B. ein Diagramm) starten.

:::image type="content" source="../../assets/images/ui-templates/mobile-stage.png" alt-text="Beispiel zeigt eine Stage-Vorlage auf mobilen Geräten." border="false":::

---

## <a name="toolbar"></a>Symbolleiste

Eine Symbolleiste ist ein Container zum Gruppieren einer Gruppe von Steuerelementen.

### <a name="top-use-cases"></a>Die am besten verwendeten Fälle

* Kontextbezogene Aktionen für App-Inhalte
* Kontextfilter und -suche
* Navigation und Breadcrumbs

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/toolbar.png" alt-text="Beispiel zeigt eine Symbolleistenvorlage auf dem Desktop." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-toolbar.png" alt-text="Beispiel zeigt eine Symbolleistenvorlage auf mobilen Geräten." border="false":::

---
