---
title: Entwerfen Ihrer App mit UI-Vorlagen
author: heath-hamilton
description: Entwerfen Sie Ihre App schneller mit standardisierten UI-Komponenten, Layouts und Mustern, die häufig in Microsoft Teams zu sehen sind.
ms.author: lajanuar
localization_priority: Normal
ms.topic: reference
ms.openlocfilehash: 7d46829be50e6c88dc7629376437878a4b5fecf93d82e805a12093c96b3677ba
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2021
ms.locfileid: "57702890"
---
# <a name="designing-your-microsoft-teams-app-with-ui-templates"></a>Entwerfen Ihrer Microsoft Teams-App mit Ui-Vorlagen

Entwerfen Sie Ihre Microsoft Teams-App schneller mit UI-Vorlagen. Die Vorlagen sind eine Sammlung von Fluent UI-basierten Komponenten, die in allgemeinen Teams Anwendungsfällen funktionieren, sodass Sie mehr Zeit haben, um die beste Benutzererfahrung zu ermitteln.

## <a name="getting-started-with-tools-and-samples"></a>Erste Schritte mit Tools und Beispielen

Die folgenden Ressourcen können Ihnen beim Entwerfen und Entwickeln Ihrer App mithilfe von Benutzeroberflächenvorlagen helfen.

### <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-UI-Kit

Nutzen Sie UI-Vorlagen für Ihr App-Design aus dem Microsoft Teams UI Kit, das auch umfassende Informationen zur Nutzung, Anatomie, Barrierefreiheit und bewährten Methoden enthält.

> [!div class="nextstepaction"]
> [Abrufen des UI-Kits (Numma)](https://www.figma.com/community/file/916836509871353159)

### <a name="microsoft-teams-ui-library"></a>Microsoft Teams UI-Bibliothek

Anzeigen und Testen einzelner Teams UI-Vorlagen und zugehöriger Komponenten in Ihrem Browser.

> [!div class="nextstepaction"]
> [Probieren Sie die Benutzeroberflächenbibliothek (Playground) aus.](https://dev-int.teams.microsoft.com/storybook/main/index.html)

Importieren Sie diese Vorlagen und zugehörigen Komponenten direkt in Ihr Teams App-Projekt.

> [!div class="nextstepaction"]
> [Abrufen der Benutzeroberflächenbibliothek (GitHub)](https://github.com/OfficeDev/microsoft-teams-ui-component-library)

### <a name="sample-app"></a>Beispiel-App

Installieren Sie eine Beispiel-App, um zu sehen, wie UI-Vorlagen in Teams Kontexten aussehen und sich verhalten.

> [!div class="nextstepaction"]
> [Abrufen der Beispiel-App (GitHub)](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-ui-templates/ts)

## <a name="dashboard"></a>Dashboard

Ein Dashboard zeigt unterschiedliche Inhaltstypen an einem zentralen Ort an (Teams persönliche App oder Registerkarte). Benutzer sollten in der Lage sein, zumindest einige der Elemente anzupassen, die sie auf einem Dashboard sehen.

### <a name="top-use-cases"></a>Häufigste Anwendungsfälle

* Analysieren von Daten
* Berichtsmetriken
* Organisieren unterschiedlicher Informationen an einem Ort

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/dashboard.png" alt-text="Beispiel zeigt eine Dashboard-UI-Vorlage auf dem Desktop." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-dashboard.png" alt-text="Beispiel zeigt eine Dashboard-UI-Vorlage auf mobilgeräten." border="false":::

---

## <a name="data-visualization"></a>Datenvisualisierung

Sie können unterschiedliche Kartengrößen (einzel, doppelt und vollständig) verwenden, um Datenvisualisierungen auf derselben Seite zu stapeln und zu organisieren. Die Karten werden so skaliert, dass sie in das Spaltenlayout passen und leere Leerzeichen ausfüllen.

### <a name="top-use-cases"></a>Häufigste Anwendungsfälle

* Anzeigen komplexer Informationen
* Erstellen eines Dashboards

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/data-viz.png" alt-text="Beispiel zeigt eine Datenvisualisierungs-UI-Vorlage auf dem Desktop." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-data-viz.png" alt-text="Beispiel zeigt eine Vorlage für die Datenvisualisierung auf mobilen Geräten." border="false":::

---

## <a name="empty-state"></a>Leerer Zustand

Die leere Statusvorlage kann für viele Szenarien verwendet werden, einschließlich Anmeldung, Erste Ausführung, Fehlermeldungen und vieles mehr. Es ist äußerst flexibel– passen Sie es an die Verwendung einer, einiger oder aller Komponenten im folgenden Design an.

### <a name="top-use-cases"></a>Häufigste Anwendungsfälle

* Anmelden
* Willkommensnachrichten und Erfahrungen bei der ersten Ausführung
* Erfolgsmeldungen
* Fehlermeldungen

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/empty-state.png" alt-text="Beispiel zeigt eine leere Status-UI-Vorlage auf dem Desktop." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-empty-state.png" alt-text="Beispiel zeigt eine leere Status-UI-Vorlage auf mobilgeräten." border="false":::

---

## <a name="filter"></a>Filter

Mit einem Filter können Sie die angezeigten Informationen basierend auf den ausgewählten Kriterien reduzieren. Sie können Filter in Tabellen, Listen, Karten und andere Komponenten einschließen, die Inhalte organisieren.

### <a name="top-use-cases"></a>Häufigste Anwendungsfälle

Organisieren von Inhalten in:

* Listen
* Tabellen
* Dashboards
* Datenvisualisierung

:::image type="content" source="../../assets/images/ui-templates/filter.png" alt-text="Beispiel zeigt eine Filtervorlage." border="false":::

## <a name="form"></a>Formular

Formulare werden verwendet, um Benutzereingaben strukturiert zu erfassen, zu überprüfen und zu übermitteln. Klare Beschriftungen und logische Gruppierungen von Eingabefeldern sind entscheidend für eine gute Benutzererfahrung.

### <a name="top-use-cases"></a>Häufigste Anwendungsfälle

* Anmelden
* Benutzerprofile
* Einstellungen
* Benutzereingabesammlung

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/form.png" alt-text="Beispiel zeigt eine Formular-UI-Vorlage auf dem Desktop." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-form.png" alt-text="Beispiel zeigt eine Formular-UI-Vorlage auf mobilgeräten." border="false":::

---

## <a name="list"></a>Liste

Sie können eine Liste verwenden, um verwandte Elemente in einem scannbaren Format anzuzeigen und Benutzern das Ausführen von Aktionen für eine gesamte Liste oder einzelne Elemente zu ermöglichen.

### <a name="top-use-cases"></a>Häufigste Anwendungsfälle

* Anzeigen von Daten
* Kontextbezogene Aktionen für App-Inhalte

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/list.png" alt-text="Beispiel zeigt eine Listen-UI-Vorlage auf dem Desktop." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-list.png" alt-text="Beispiel zeigt eine Listen-UI-Vorlage auf mobilgeräten." border="false":::

---

## <a name="sign-in"></a>Anmelden

Sie können App-Anmeldeabläufe für unterschiedliche Teams Kontexte und Identitätsanbieter entwerfen. Das folgende Beispiel enthält einmaliges Anmelden (Single Sign-On, SSO), das wir für die einfachste Authentifizierung empfehlen.

### <a name="top-use-case"></a>Häufigster Anwendungsfall

* Authentifizieren von Benutzern

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/sign-in.png" alt-text="Beispiel zeigt eine Vorlage für die Anmeldung auf der Benutzeroberfläche auf dem Desktop." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-sign-in.png" alt-text="Beispiel zeigt eine Benutzeroberflächenvorlage für die Anmeldung auf mobilgeräten." border="false":::

---

## <a name="settings"></a>Einstellungen

Einstellungen Bildschirme können Benutzer ihre Einstellungen mit Ihrer App konfigurieren. (Hinweis: Einstellungen ist ein Container für [grundlegende UI-Komponenten.)](~/concepts/design/design-teams-app-basic-ui-components.md)

### <a name="top-use-case"></a>Häufigster Anwendungsfall

* Verwalten von App-Features

:::image type="content" source="../../assets/images/ui-templates/settings.png" alt-text="Beispiel zeigt eine Einstellungsvorlage." border="false":::

## <a name="task-board"></a>Task Board

Ein Task Board, manchmal auch als "Tickets Board" oder "Boot" bezeichnet, ist eine Sammlung von Karten, die häufig verwendet werden, um den Status von Arbeitselementen oder Tickets nachzuverfolgen. Es kann auch verwendet werden, um alle Arten von Inhalten in Kategorien zu sortieren. Sie können die Karten bearbeiten und zwischen Spalten verschieben.

### <a name="top-use-cases"></a>Häufigste Anwendungsfälle

* Projektmanagement Zuweisen von Aufgaben und Nachverfolgungsstatus
* Brainstorming. Hinzufügen von Ideen in verschiedenen Kategorien
* Sortierübungen. Organisieren beliebiger Informationen in Buckets

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/task-board.png" alt-text="Beispiel zeigt eine Task Board-UI-Vorlage auf dem Desktop." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-task-board.png" alt-text="Beispiel zeigt eine Task Board-UI-Vorlage auf mobilgeräten." border="false":::

---

## <a name="wizard"></a>Assistent

Ein Assistent führt einen Benutzer durch mehrere Bildschirme, um eine Aufgabe abzuschließen (z. B. einen Setupprozess).

### <a name="top-use-cases"></a>Häufigste Anwendungsfälle

* Setup
* Onboarding
* Erfahrungen bei der ersten Ausführung

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/wizard.png" alt-text="Beispiel zeigt eine Assistenten-UI-Vorlage auf dem Desktop." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-wizard.png" alt-text="Beispiel zeigt eine Assistenten-UI-Vorlage auf mobilgeräten." border="false":::

---
