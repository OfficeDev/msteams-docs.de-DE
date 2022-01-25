---
title: Verwalten Ihrer Apps mit dem Entwicklerportal
description: Erfahren Sie, wie Sie Ihre Apps mithilfe des Entwicklerportals für Microsoft Teams konfigurieren, verteilen und verwalten.
keywords: Erste Schritte für Entwicklerportal-Teams
ms.localizationpriority: medium
ms.topic: overview
ms.author: surbhigupta
ms.openlocfilehash: 246ea41b30fe920562989b32c3643813238fb083
ms.sourcegitcommit: 7209e5af27e1ebe34f7e26ca1e6b17cb7290bc06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2022
ms.locfileid: "62212538"
---
# <a name="manage-your-apps-with-the-developer-portal-for-microsoft-teams"></a>Verwalten Ihrer Apps mit dem Entwicklerportal für Microsoft Teams

Das <a href="https://dev.teams.microsoft.com" target="_blank">Entwicklerportal für Teams</a> ist das primäre Tool zum Konfigurieren, Verteilen und Verwalten Ihrer Microsoft Teams-Apps. Mit dem Entwicklerportal können Sie mit Kollegen an Ihrer App zusammenarbeiten, Laufzeitumgebungen einrichten und vieles mehr.

:::image type="content" source="../../assets/images/tdp/tdp_home_1.png" alt-text="Screenshot der Startseite des Entwicklerportals für Teams.":::

## <a name="register-an-app"></a>Registrieren einer App

Das Entwicklerportal bietet verschiedene Möglichkeiten zum Registrieren einer Teams-App:

* Registrieren einer völlig neuen App
* Importieren eines vorhandenen App-Pakets

> [!NOTE]
> Wenn Sie eine App mit dem [Microsoft Teams Toolkit für Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension)erstellen, können Sie diese App im Entwicklerportal verwalten.

## <a name="set-up-an-environment"></a>Einrichten einer Umgebung

Sie können Umgebungen und globale Variablen konfigurieren, um den Übergang Ihrer App von Ihrer lokalen Laufzeit zur Produktion zu unterstützen. Globale Variablen werden in allen Umgebungen verwendet.

**So richten Sie eine Umgebung ein**

1. Wählen Sie im Entwicklerportal die App aus, an der Sie arbeiten.
2. Wechseln Sie zur Seite **"Umgebungen",** und wählen Sie **+Umgebung hinzufügen** aus.
3. Wählen Sie **+ Hinzufügen einer Variablen,** um Konfigurationsvariablen für Ihre Umgebung zu erstellen.

**So verwenden Sie Variablen**

Verwenden Sie die Variablennamen anstelle von hartcodierten Werten, um Ihre App-Konfigurationen festzulegen.

1. Geben Sie `{{` in ein beliebiges Feld im Entwicklerportal ein. Es wird eine Dropdownliste mit allen Variablen angezeigt, die Sie für die ausgewählte Umgebung zusammen mit den globalen Variablen erstellt haben.  
1. Wählen Sie vor dem Herunterladen Ihres App-Pakets (z. B. wenn Sie sich auf die Veröffentlichung im Teams Store vorbereiten) die Umgebung aus, die Sie verwenden möchten. Ihre App-Konfigurationen werden basierend auf der Umgebung automatisch aktualisiert. 

## <a name="identify-app-owners"></a>Identifizieren von App-Besitzern

Jede App enthält eine **Besitzerseite,** auf der Sie Ihre App-Registrierung für Kollegen in Ihrer Organisation freigeben können. Die **Rolle "Mitwirkender"** verfügt über die gleichen Berechtigungen wie die **Besitzerrolle,** mit Ausnahme der Möglichkeit, eine App zu löschen.

## <a name="configure-your-apps-capabilities-and-other-important-metadata"></a>Konfigurieren der Funktionen Ihrer App und anderer wichtiger Metadaten

Eine Teams-App ist eine Web-App. Wie alle Web-Apps wird der Quellcode in der Regel in einer IDE oder einem Code-Editor entwickelt und an einer beliebigen Stelle in der Cloud (z. B. Azure) gehostet.

Um Ihre App in Teams zu installieren und zu rendern, müssen Sie eine Reihe von Konfigurationen einschließen, die Teams erkennt. Dies geschieht traditionell durch das Erstellen eines App-Manifests, einer JSON-Datei, die alle Metadaten enthält, die Teams zum Anzeigen ihrer App-Inhalte benötigt. Das Entwicklerportal abstrahiert diesen Prozess und enthält neue Features und Tools, die Ihnen helfen, erfolgreicher zu sein.

## <a name="test-your-app-directly-in-teams"></a>Testen Sie Ihre App direkt in Teams

Das Entwicklerportal bietet Optionen zum Testen und Debuggen Ihrer App:

* Auf der **Übersichtsseite** sehen Sie eine Momentaufnahme, ob die Konfigurationen Ihrer App anhand Teams Store-Testfälle überprüft werden.
* Mit der Schaltfläche **"Vorschau in Teams"** können Sie Ihre App schnell im Teams-Client zum Debuggen starten.

## <a name="distribute-your-app"></a>Verteilen Ihrer App

Verwenden Sie im Entwicklerportal die Schaltfläche **"Verteilen",** um ein App-Paket herunterzuladen, in Ihrer Organisation zu veröffentlichen oder im Teams Store zu veröffentlichen.

Weitere Informationen finden Sie unter [Verteilen Ihrer Teams-App.](~/concepts/deploy-and-publish/apps-publish-overview.md)

## <a name="analyze-your-apps-usage"></a>Analysieren der Nutzung Ihrer App

Auf der **Übersichtsseite** sehen Sie die Gesamtzahl der aktiven Benutzer für Ihre App. Diese Metriken sind für Apps verfügbar, die im Teams Store oder im App-Katalog einer Organisation über das Entwicklerportal veröffentlicht und auf die App-ID beschränkt sind.

| Metrik | Definition |
| :-----------------------| :------------------------------------------------------------------------------------------------------|
| *Monatlich R30* | Die Standardverwendungsmetrik. Sie zeigt die Anzahl der eindeutigen aktiven Benutzer an, die Ihre App innerhalb dieses rollenden 30-Tage-Fensters in UTC verwendet haben. |
| *Täglich* | Zeigt die Anzahl der eindeutigen aktiven Benutzer an, die Ihre App an einem bestimmten Tag in UTC verwendet haben. |

Die monatliche und tägliche Nutzung wird für die letzten sieben, 30 und 60 Tage angezeigt. Die Nutzung sollte für einen bestimmten Tag innerhalb von 24 bis 48 Stunden widergespiegelt werden. Die Anzeige neuer Apps kann bis zu 3 bis 5 Tage dauern.

## <a name="use-tools-to-create-app-features"></a>Verwenden von Tools zum Erstellen von App-Features

Das Entwicklerportal enthält auch Tools, mit denen Sie einige wichtige Features von Teams-Apps erstellen können. Einige dieser Tools umfassen:

* **Szenenstudio:** Entwerfen [Sie benutzerdefinierte Szenen im Zusammen-Modus](~/apps-in-teams-meetings/teams-together-mode.md) für Teams Besprechungen.
* **Editor für adaptive Karten:** Erstellen und Anzeigen einer Vorschau adaptiver Karten, die in Ihre Apps aufgenommen werden sollen.
* **Microsoft Identity Platform Verwaltung:** Registrieren Sie Ihre Apps bei Azure Active Directory, um Benutzern zu helfen, sich anzumelden und Zugriff auf APIs zu gewähren.

## <a name="see-also"></a>Siehe auch

[Einschließen eines SaaS-Angebots in Ihre Microsoft Teams-App](~/concepts/deploy-and-publish/appsource/prepare/include-saas-offer.md)
