---
title: Entwerfen Ihrer App mit Benutzeroberflächenvorlagen
author: heath-hamilton
description: Entwerfen Sie Ihre App schneller mit standardisierten Benutzeroberflächenkomponenten, Layouts und Mustern, die häufig in verschiedenen Microsoft Teams.
ms.author: lajanuar
localization_priority: Normal
ms.topic: reference
ms.openlocfilehash: 5026554070396dcc55390496b6754961e8e037bc
ms.sourcegitcommit: 4224c44d169b1a289cbf1d3353de6bc6de7c7ea8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2021
ms.locfileid: "52644859"
---
# <a name="designing-your-microsoft-teams-app-with-ui-templates"></a>Entwerfen Ihrer Microsoft Teams-App mit Benutzeroberflächenvorlagen

Entwerfen Sie Microsoft Teams App schneller mit Benutzeroberflächenvorlagen. Bei den Vorlagen handelt es sich um eine Sammlung von Benutzeroberflächenbasierten Fluent-Komponenten, die Teams gängigen Verwendungsfällen funktionieren und Ihnen mehr Zeit zum Herausfinden der besten Benutzererfahrung bieten.

## <a name="getting-started-with-tools-and-samples"></a>Erste Schritte mit Tools und Beispielen

Mit den folgenden Ressourcen können Sie Ihre App mithilfe von Benutzeroberflächenvorlagen entwerfen und entwickeln.

### <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-UI-Kit

Greifen Sie ui templates for your app design from the Microsoft Teams UI Kit, which also includes extensive information about usage, anatomy, accessibility, and best practices.

> [!div class="nextstepaction"]
> [Benutzeroberflächenkit (Figma)](https://www.figma.com/community/file/916836509871353159)

### <a name="microsoft-teams-ui-library"></a>Microsoft Teams Benutzeroberflächenbibliothek

Anzeigen und Testen einzelner Teams benutzeroberflächenvorlagen und zugehörigen Komponenten in Ihrem Browser.

> [!div class="nextstepaction"]
> [Probieren Sie die Benutzeroberflächenbibliothek (Playground) aus.](https://dev-int.teams.microsoft.com/storybook/main/index.html)

Importieren Sie diese Vorlagen und zugehörigen Komponenten direkt in Teams App-Projekt.

> [!div class="nextstepaction"]
> [Benutzeroberflächenbibliothek (GitHub)](https://github.com/OfficeDev/microsoft-teams-ui-component-library)

### <a name="sample-app"></a>Beispiel-App

Installieren Sie eine Beispiel-App, um zu sehen, wie Benutzeroberflächenvorlagen in Teams aussehen und verhalten.

> [!div class="nextstepaction"]
> [Die Beispiel-App (GitHub)](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-ui-templates/ts)

## <a name="dashboard"></a>Dashboard

Ein Dashboard zeigt unterschiedliche Inhaltstypen an einem zentralen Speicherort an (Teams persönliche App oder Registerkarte). Benutzer sollten in der Lage sein, zumindest einige der auf einem Dashboard angezeigten Informationen anzupassen.

### <a name="top-use-cases"></a>Die am besten verwendeten Fälle

* Analysieren von Daten
* Berichtsmetriken
* Organisieren verschiedener Informationen an einem Ort

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/dashboard.png" alt-text="Beispiel zeigt eine Dashboard-UI-Vorlage auf dem Desktop." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-dashboard.png" alt-text="Beispiel zeigt eine Dashboardbenutzeroberflächenvorlage auf Mobilgeräten." border="false":::

---

## <a name="data-visualization"></a>Datenvisualisierung

Sie können verschiedene Kartengrößen (einzeln, doppelt und vollständig) verwenden, um Datenvisualisierungen auf derselben Seite zu stapeln und zu organisieren. Die Karten werden so skaliert, dass sie an das Spaltenlayout passen und leere Leerzeichen ausfüllen.

### <a name="top-use-cases"></a>Die am besten verwendeten Fälle

* Anzeigen komplexer Informationen
* Erstellen eines Dashboards

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/data-viz.png" alt-text="Beispiel zeigt eine Benutzeroberflächenvorlage für die Datenvisualisierung auf dem Desktop." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-data-viz.png" alt-text="Beispiel zeigt eine Benutzeroberflächenvorlage für die Datenvisualisierung auf Mobilgeräten." border="false":::

---

## <a name="empty-state"></a>Leerer Status

Die leere Zustandsvorlage kann für viele Szenarien verwendet werden, z. B. für die Anmeldung, die Erstlauferfahrung, Fehlermeldungen und vieles mehr. Es ist äußerst flexibel– passen Sie es an, um eine, einige oder alle Komponenten im folgenden Entwurf zu verwenden.

### <a name="top-use-cases"></a>Die am besten verwendeten Fälle

* Anmelden
* Willkommensnachrichten und Erstlauferfahrungen
* Erfolgsmeldungen
* Fehlermeldungen

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/empty-state.png" alt-text="Beispiel zeigt eine leere Zustands-UI-Vorlage auf dem Desktop." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-empty-state.png" alt-text="Beispiel zeigt eine leere Zustands-UI-Vorlage auf mobilen Geräten." border="false":::

---

## <a name="filter"></a>Filter

Mit einem Filter können Sie die angezeigten Informationen basierend auf den ausgewählten Kriterien reduzieren. Sie können Filter mit Tabellen, Listen, Karten und anderen Komponenten hinzufügen, die Inhalte organisieren.

### <a name="top-use-cases"></a>Die am besten verwendeten Fälle

Organisieren von Inhalten in:

* Listen
* Tabellen
* Dashboards
* Datenvisualisierung

:::image type="content" source="../../assets/images/ui-templates/filter.png" alt-text="Beispiel zeigt eine Filtervorlage." border="false":::

## <a name="form"></a>Formular

Formulare werden verwendet, um Benutzereingaben strukturiert zu erfassen, zu überprüfen und zu übermitteln. Klare Bezeichnungen und logische Gruppierungen von Eingabefeldern sind für eine gute Benutzeroberfläche entscheidend.

### <a name="top-use-cases"></a>Die am besten verwendeten Fälle

* Anmelden
* Benutzerprofile
* Einstellungen
* Benutzereingabesammlung

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/form.png" alt-text="Beispiel zeigt eine Formularbenutzeroberflächenvorlage auf dem Desktop." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-form.png" alt-text="Beispiel zeigt eine Formularbenutzeroberflächenvorlage auf mobilen Geräten." border="false":::

---

## <a name="list"></a>Liste

Sie können eine Liste verwenden, um verwandte Elemente in einem scannierbaren Format anzeigen und Benutzern das Ausführen von Aktionen für eine gesamte Liste oder einzelne Elemente zu ermöglichen.

### <a name="top-use-cases"></a>Die am besten verwendeten Fälle

* Anzeigen von Daten
* Kontextbezogene Aktionen für App-Inhalte

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/list.png" alt-text="Beispiel zeigt eine Listenbenutzeroberflächenvorlage auf dem Desktop." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-list.png" alt-text="Beispiel zeigt eine Listenbenutzeroberflächenvorlage auf mobilen Geräten." border="false":::

---

## <a name="sign-in"></a>Anmelden

Sie können App-Anmeldeflüsse für unterschiedliche Teams und Identitätsanbieter entwerfen. Das folgende Beispiel enthält einmaliges Anmelden (Single Sign-On, SSO), das für die einfachste Authentifizierung empfohlen wird.

### <a name="top-use-case"></a>Top Use Case

* Authentifizieren von Benutzern

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/sign-in.png" alt-text="Beispiel zeigt eine Benutzeroberflächenvorlage für die Anmeldung auf dem Desktop." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-sign-in.png" alt-text="Beispiel zeigt eine Benutzeroberflächenvorlage für die Anmeldung auf mobilen Geräten." border="false":::

---

## <a name="settings"></a>Einstellungen

Einstellungen bildschirmen können Benutzer ihre Einstellungen mit Ihrer App konfigurieren. (Hinweis: Einstellungen ist ein Container für [grundlegende Benutzeroberflächenkomponenten](~/concepts/design/design-teams-app-basic-ui-components.md).)

### <a name="top-use-case"></a>Top Use Case

* Verwalten von App-Features

:::image type="content" source="../../assets/images/ui-templates/settings.png" alt-text="Beispiel zeigt eine Einstellungsvorlage." border="false":::

## <a name="task-board"></a>Task Board

Ein Aufgabenboard, manchmal auch als Kanbanboard oder Schwimmstreifen bezeichnet, ist eine Sammlung von Karten, die häufig zum Nachverfolgen des Status von Arbeitselementen oder Tickets verwendet werden. Es kann auch verwendet werden, um alle Arten von Inhalten in Kategorien zu sortieren. Sie können die Karten zwischen Spalten bearbeiten und verschieben.

### <a name="top-use-cases"></a>Die am besten verwendeten Fälle

* Projektmanagement Zuweisen von Aufgaben und Nachverfolgungsstatus
* Brainstorming. Hinzufügen von Ideen in verschiedenen Kategorien
* Sortierübungen. Organisieren aller Arten von Informationen in Buckets

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/task-board.png" alt-text="Beispiel zeigt eine Benutzeroberflächenvorlage für Taskboards auf dem Desktop." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-task-board.png" alt-text="Beispiel zeigt eine Benutzeroberflächenvorlage für task board auf mobilen Geräten." border="false":::

---

## <a name="wizard"></a>Assistent

Ein Assistent führt einen Benutzer durch mehrere Bildschirme, um eine Aufgabe auszuführen (z. B. einen Einrichtungsprozess).

### <a name="top-use-cases"></a>Die am besten verwendeten Fälle

* Setup
* Onboarding
* First-Run-Erfahrungen

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/wizard.png" alt-text="Beispiel zeigt eine Benutzeroberflächenvorlage des Assistenten auf dem Desktop." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-wizard.png" alt-text="Beispiel zeigt eine Benutzeroberflächenvorlage des Assistenten auf Mobilgeräten." border="false":::

---
