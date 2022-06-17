---
title: Entwerfen Ihrer App mit UI-Vorlagen
author: heath-hamilton
description: Erfahren Sie, wie Sie Ihre App schneller mit standardisierten UI-Komponenten, Layouts und Mustern entwerfen, die häufig in Microsoft Teams zu sehen sind.
ms.author: lajanuar
ms.localizationpriority: medium
ms.topic: reference
ms.openlocfilehash: d6323baf20c733eaddc1e8797a56d63effc45eab
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66142899"
---
# <a name="designing-your-microsoft-teams-app-with-ui-templates"></a>Entwerfen Ihrer Microsoft Teams-App mit UI-Vorlagen

Entwerfen Sie Ihre Microsoft Teams-App schneller mit UI-Vorlagen. Bei den Vorlagen handelt es sich um eine Sammlung von Fluent UI-basierten Komponenten, die in gängigen Teams Anwendungsfällen funktionieren, sodass Sie mehr Zeit haben, die beste Benutzererfahrung zu ermitteln.

## <a name="getting-started-with-tools-and-samples"></a>Erste Schritte mit Tools und Beispielen

Die folgenden Ressourcen können Ihnen beim Entwerfen und Entwickeln Ihrer App mithilfe von UI-Vorlagen helfen.

### <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-Benutzeroberflächenbausatz

Holen Sie sich UI-Vorlagen für Ihr App-Design aus dem Microsoft Teams UI Kit, das auch umfassende Informationen zur Verwendung, Anatomie, Barrierefreiheit und bewährten Methoden enthält.

> [!div class="nextstepaction"]
> [Abrufen des UI-Kits (Figma)](https://www.figma.com/community/file/916836509871353159)

### <a name="microsoft-teams-ui-library"></a>Microsoft Teams-Benutzeroberflächenbibliothek

Betrachten und testen Sie einzelne Teams-Benutzeroberflächenvorlagen und zugehörige Komponenten in Ihrem Browser.

> [!div class="nextstepaction"]
> [Probieren Sie die Benutzeroberflächenbibliothek (Playground) aus.](https://dev-int.teams.microsoft.com/storybook/main/index.html)

Importieren Sie diese Vorlagen und zugehörigen Komponenten direkt in Ihr Teams-App-Projekt.

> [!div class="nextstepaction"]
> [Abrufen der Benutzeroberflächenbibliothek (GitHub)](https://github.com/OfficeDev/microsoft-teams-ui-component-library)

### <a name="sample-app"></a>Beispiel-App

Installieren Sie eine Beispiel-App, um zu sehen, wie UI-Vorlagen in Teams Kontexten aussehen und sich verhalten.

> [!div class="nextstepaction"]
> [Abrufen der Beispiel-App (GitHub)](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-ui-templates/ts)

## <a name="calendar"></a>Kalender

In Teams ist ein Kalender der Ort, an dem ein Benutzer bevorstehende und vergangene Ereignisse für sich selbst oder eine Gruppe anzeigt, plant und verwaltet.

### <a name="top-use-cases"></a>Die häufigsten Anwendungsfälle

* Planen von Besprechungen und Ereignissen
* Abrufen von Erinnerungen an bevorstehende Besprechungen und Ereignisse
* Anzeigen von Zeitplänen

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/ui-templates/desktop-calendar.png" alt-text="Das Beispiel zeigt eine Kalender-UI-Vorlage auf dem Desktop." border="false":::

## <a name="dashboard"></a>Dashboard

Ein Dashboard zeigt verschiedene Arten von Inhalten an einem zentralen Ort an (z. B. eine Teams persönliche App oder Registerkarte). Benutzer sollten in der Lage sein, zumindest einige der Elemente anzupassen, die auf einem Dashboard angezeigt werden.

### <a name="top-use-cases"></a>Die häufigsten Anwendungsfälle

* Analysieren von Daten
* Berichtsmetriken
* Organisieren verschiedener Informationen an einem Ort

### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/ui-templates/mobile-dashboard.png" alt-text="Beispiel zeigt eine Dashboard-UI-Vorlage auf mobilgeräten." border="false":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/ui-templates/dashboard.png" alt-text="Beispiel zeigt eine Dashboard-UI-Vorlage auf dem Desktop." border="false":::

## <a name="data-visualization"></a>Datenvisualisierung

Sie können verschiedene Kartengrößen (single, double und full) verwenden, um Datenvisualisierungen auf derselben Seite zu stapeln und zu organisieren. Die Karten werden so skaliert, dass sie an das Spaltenlayout angepasst werden und leere Leerzeichen ausfüllen.

### <a name="top-use-cases"></a>Die häufigsten Anwendungsfälle

* Anzeigen komplexer Informationen
* Erstellen eines Dashboards

### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/ui-templates/mobile-data-viz.png" alt-text="Das Beispiel zeigt eine Datenvisualisierungs-UI-Vorlage auf mobilgeräten." border="false":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/ui-templates/data-viz.png" alt-text="Das Beispiel zeigt eine Datenvisualisierungs-UI-Vorlage auf dem Desktop." border="false":::

## <a name="empty-state"></a>Leerer Zustand

Die leere Statusvorlage kann für viele Szenarien verwendet werden, einschließlich Anmeldung, Erfahrungen bei der ersten Ausführung, Fehlermeldungen und mehr. Es ist sehr flexibel – passen Sie es an die Verwendung einer, einiger oder aller Komponenten im folgenden Design an.

### <a name="top-use-cases"></a>Die häufigsten Anwendungsfälle

* Anmelden
* Willkommensnachrichten und Erste-Ausführung-Erfahrungen
* Erfolgsmeldungen
* Fehlermeldungen

### <a name="mobile"></a>Mobil

:::image type="content" source="../../assets/images/ui-templates/mobile-empty-state.png" alt-text="Das Beispiel zeigt eine Leere Zustands-UI-Vorlage auf mobilgeräten." border="false":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/ui-templates/empty-state.png" alt-text="Das Beispiel zeigt eine Leere Zustands-UI-Vorlage auf dem Desktop." border="false":::

## <a name="filter"></a>Filter

Mit einem Filter können Sie die angezeigten Informationen basierend auf den ausgewählten Kriterien reduzieren. Sie können Filter in Tabellen, Listen, Karten und andere Komponenten einschließen, die Inhalte organisieren.

### <a name="top-use-cases"></a>Die häufigsten Anwendungsfälle

Organisieren von Inhalten in:

* Listen
* Tabellen
* Dashboards
* Datenvisualisierung

:::image type="content" source="../../assets/images/ui-templates/filter.png" alt-text="Beispiel zeigt eine Filtervorlage." border="false":::

## <a name="form"></a>Formular

Formulare werden verwendet, um Benutzereingaben auf strukturierte Weise zu sammeln, zu überprüfen und zu übermitteln. Klare Bezeichnungen und logische Gruppierungen von Eingabefeldern sind wichtig für eine gute Benutzererfahrung.

### <a name="top-use-cases"></a>Die häufigsten Anwendungsfälle

* Anmelden
* Benutzerprofile
* Einstellungen
* Benutzereingabesammlung

### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/ui-templates/mobile-form.png" alt-text="Das Beispiel zeigt eine Formular-UI-Vorlage auf mobilen Geräten." border="false":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/form.png" alt-text="Das Beispiel zeigt eine Formular-UI-Vorlage auf dem Desktop." border="false":::

## <a name="list"></a>Liste

Sie können eine Liste verwenden, um verwandte Elemente in einem scannbaren Format anzuzeigen und Benutzern das Ausführen von Aktionen für eine gesamte Liste oder einzelne Elemente zu ermöglichen.

### <a name="top-use-cases"></a>Die häufigsten Anwendungsfälle

* Anzeigen von Daten
* Kontextbezogene Aktionen für App-Inhalte

### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/ui-templates/mobile-list.png" alt-text="Beispiel zeigt eine Listen-UI-Vorlage auf mobilgeräten." border="false":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/ui-templates/list.png" alt-text="Das Beispiel zeigt eine Listen-UI-Vorlage auf dem Desktop." border="false":::

## <a name="sign-in"></a>Anmelden

Sie können App-Anmeldeflüsse für verschiedene Teams Kontexte und Identitätsanbieter entwerfen. Das folgende Beispiel enthält einmaliges Anmelden (Single Sign-On, SSO), das wir für die einfachste Authentifizierung empfehlen.

### <a name="top-use-case"></a>Top-Anwendungsfall

* Authentifizieren von Benutzern

### <a name="mobile"></a>Mobil

:::image type="content" source="../../assets/images/ui-templates/mobile-sign-in.png" alt-text="Das Beispiel zeigt eine Anmelde-UI-Vorlage auf mobilgeräten." border="false":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/ui-templates/sign-in.png" alt-text="Das Beispiel zeigt eine Anmelde-UI-Vorlage auf dem Desktop." border="false":::

## <a name="settings"></a>Einstellungen

Einstellungen Bildschirme können Benutzer ihre Einstellungen mit Ihrer App konfigurieren. (Hinweis: Einstellungen ist ein Container für [grundlegende UI-Komponenten](~/concepts/design/design-teams-app-basic-ui-components.md).)

### <a name="top-use-case"></a>Top-Anwendungsfall

* Verwalten von App-Features

:::image type="content" source="../../assets/images/ui-templates/settings.png" alt-text="Das Beispiel zeigt eine Einstellungsvorlage." border="false":::

## <a name="task-board"></a>Task Board

Ein Task Board, manchmal auch als Kanban Board oder Swim Lanes bezeichnet, ist eine Sammlung von Karten, die häufig verwendet werden, um den Status von Arbeitsgegenständen oder Tickets nachzuverfolgen. Es kann auch verwendet werden, um jede Art von Inhalt in Kategorien zu sortieren. Sie können die Karten zwischen Spalten bearbeiten und verschieben.

### <a name="top-use-cases"></a>Die häufigsten Anwendungsfälle

* Projektmanagement Zuweisen von Aufgaben und Nachverfolgen des Status.
* Brainstorming. Hinzufügen von Ideen in verschiedenen Kategorien.
* Sortierübungen. Organisieren aller Arten von Informationen in Buckets.

### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/ui-templates/mobile-task-board.png" alt-text="Das Beispiel zeigt eine Vorlage für die Task board-UI auf mobilgeräten." border="false":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/ui-templates/task-board.png" alt-text="Das Beispiel zeigt eine Vorlage für die Task board-UI auf dem Desktop." border="false":::

## <a name="wizard"></a>Assistent

Ein Assistent führt einen Benutzer durch mehrere Bildschirme, um eine Aufgabe auszuführen (z. B. einen Einrichtungsprozess).

### <a name="top-use-cases"></a>Die häufigsten Anwendungsfälle

* Einrichtung
* Onboarding
* Erste Ausführungserfahrungen

### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/ui-templates/mobile-wizard.png" alt-text="Das Beispiel zeigt eine Benutzeroberflächenvorlage des Assistenten auf mobilgeräten." border="false":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/ui-templates/wizard.png" alt-text="Das Beispiel zeigt eine Benutzeroberflächenvorlage des Assistenten auf dem Desktop." border="false":::

## <a name="see-also"></a>Siehe auch

* [Entwerfen Ihrer App mit grundlegenden Fluent UI-Komponenten](~/concepts/design/design-teams-app-basic-ui-components.md)
* [Entwerfen Ihrer Microsoft Teams-App mit erweiterten UI-Komponenten](~/concepts/design/design-teams-app-advanced-ui-components.md)
* [Formatieren von Bot-Nachrichten](~/bots/how-to/format-your-bot-messages.md)
