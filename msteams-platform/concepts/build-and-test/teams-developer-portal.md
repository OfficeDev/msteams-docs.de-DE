---
title: Verwalten Ihrer Apps mit dem Entwicklerportal
description: Erfahren Sie, wie Sie Ihre Apps mithilfe des Entwicklerportals für Microsoft Teams verwalten.
keywords: Erste Schritte für Entwicklerportal-Teams
ms.localizationpriority: medium
ms.topic: overview
ms.author: surbhigupta
ms.openlocfilehash: 84f3e5724adf3256fff3086158345fc3777513bb
ms.sourcegitcommit: 6573881f7e69d8e5ec8861f54df84e7d519f0511
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2021
ms.locfileid: "60096574"
---
# <a name="manage-your-apps-with-the-developer-portal-for-microsoft-teams"></a>Verwalten Ihrer Apps mit dem Entwicklerportal für Microsoft Teams

Das <a href="https://dev.teams.microsoft.com" target="_blank">Entwicklerportal für Teams</a> ist das primäre Tool zum Konfigurieren, Verteilen und Verwalten Ihrer Microsoft Teams-Apps. Mit dem Entwicklerportal können Sie mit Kollegen an Ihrer App zusammenarbeiten, Laufzeitumgebungen einrichten und vieles mehr.

:::image type="content" source="../../assets/images/tdp/tdp_home_1.png" alt-text="Screenshot der Startseite des Entwicklerportals für Teams.":::

## <a name="register-an-app"></a>Registrieren einer App

Sie können Ihre Teams-App im Entwicklerportal auf folgende Weise registrieren:

* Registrieren einer neuen App
* Importieren eines vorhandenen App-Pakets

> [!NOTE]
> Wenn Sie eine App mit dem [Microsoft Teams Toolkit für Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension)erstellen, können Sie diese App im Entwicklerportal verwalten.

## <a name="set-up-an-environment"></a>Einrichten einer Umgebung

Sie können Umgebungen und globale Variablen konfigurieren, um den Übergang Ihrer App von der lokalen Laufzeit zur Produktion zu unterstützen. Globale Variablen werden in allen Umgebungen verwendet.

**So konfigurieren Sie eine Umgebung**

1. Wählen Sie im Entwicklerportal die App aus, an der Sie arbeiten.
2. Wechseln Sie zu **"Umgebungen",** und wählen Sie **"+ Umgebung hinzufügen"** aus.
3. Wählen Sie **+ Hinzufügen einer Variablen,** um Konfigurationsvariablen für Ihre Umgebung zu erstellen.

**So verwenden Sie Variablen**

Verwenden Sie die Variablennamen anstelle von hartcodierten Werten, um Ihre App-Konfigurationen festzulegen.

1. Geben Sie `{{` in ein beliebiges Feld im Entwicklerportal ein. Es wird eine Dropdownliste mit allen Variablen angezeigt, die Sie für die ausgewählte Umgebung zusammen mit den globalen Variablen erstellt haben.  
1. Wählen Sie vor dem Herunterladen des App-Pakets (z. B. wenn Sie sich auf die Veröffentlichung im Teams Store vorbereiten) die Umgebung aus, die Sie verwenden möchten. Ihre App-Konfigurationen werden basierend auf der Umgebung automatisch aktualisiert. 

## <a name="identify-app-owners"></a>Identifizieren von App-Besitzern

Jede App enthält **Besitzer,** in denen Sie Ihre App-Registrierung für Kollegen in Ihrer Organisation freigeben können. Die **Rolle "Mitwirkender"** verfügt über die gleichen Berechtigungen wie die **Besitzerrolle,** mit Ausnahme der Möglichkeit, eine App zu löschen.

## <a name="configure-your-apps-capabilities-and-other-important-metadata"></a>Konfigurieren der Funktionen Ihrer App und anderer wichtiger Metadaten

Eine Teams-App ist eine Web-App. Wie alle Web-Apps wird der Quellcode in der Regel in einer IDE oder einem Code-Editor entwickelt und an einer beliebigen Stelle in der Cloud (z. B. Azure) gehostet.

Um Ihre App in Teams zu installieren und zu rendern, müssen Sie eine Reihe von Konfigurationen einschließen, die Teams erkennt. Dies geschieht traditionell durch das Erstellen eines App-Manifests, einer JSON-Datei, die alle Metadaten enthält, die Teams benötigen, um Ihre App-Inhalte anzuzeigen. Das Entwicklerportal abstrahiert diesen Prozess und enthält neue Features und Tools, die Ihnen helfen, erfolgreicher zu sein.

### <a name="basic-app-configuration"></a>Grundlegende App-Konfiguration 

**Grundlegende App-Informationen:** Die Benutzer werden auf der App-Detailseite in Teams angezeigt, z. B. App-ID, App-Namen, Beschreibungen, Entwicklerinformationen, Version, App-URLs und Microsoft Partner Network-ID.

**Branding:** Apps erfordern ein Farb- und Gliederungssymbol im PNG-Format. Um Ihre App im Teams Store zu veröffentlichen, müssen die Symbole bestimmte Größenanforderungen erfüllen.

**Features:** Teams Features, die Sie in Ihre App einschließen können. Je nach Den Anwendungsfällen Ihrer App können Sie ein oder mehrere Features hinzufügen.

**Berechtigungen:** Geben Sie an, welchen Benutzern sie zustimmen müssen, wenn Sie Ihre App verwenden.

**Einmaliges Anmelden:** Konfigurieren Sie Ihre App so, dass Benutzer mit einmaligem Anmelden (Single Sign-On, SSO) authentifiziert werden.

**Domänen:** Listet alle Domänen auf, zu denen Ihre App navigieren muss. Verwenden Sie Platzhalter, um mehrere Unterdomänen einzuschließen. Beispiel: `*.example.com`.

### <a name="advanced-app-configuration"></a>Erweiterte App-Konfiguration

**App-Inhalt:** Konfigurieren Sie die optionalen Features wie Ladeanzeige und Vollbildmodus für Ihre App.

**App-Anpassung:** Wählen Sie die Eigenschaften aus, die Teams Administratoren über Ihre App anpassen können.

**Erstanbietereinstellungen:** Features für Erstanbieteranwendungen, die über die öffentliche Funktionalität hinausgehen.

### <a name="distribute-your-app"></a>Verteilen Ihrer App

**App-Paket:** Das App-Paket beschreibt Ihre App-Konfiguration, Funktionen, erforderlichen Ressourcen und andere wichtige Attribute. Beispielsweise das Manifestschema.

**Flights:** Steuern, wer App-Updates erhält. Sie können beispielsweise ein Update an Microsoft-Mitarbeiter freigeben, um Fehler zu identifizieren und zu beheben, bevor Sie es für die Öffentlichkeit freigeben.

**Veröffentlichen in Ihrer Organisation (Microsoft):** Stellen Sie Ihre App für Personen in Ihrer Organisation zur Verfügung. Nachdem Sie von Ihrem IT-Administrator genehmigt wurden, wird Ihre App in Teams unter "Apps > Für Ihre Organisation erstellt" angezeigt.

**Im Teams Store veröffentlichen:** Das App-Überprüfungstool überprüft Ihr App-Paket anhand der Testfälle, die Microsoft bei der Überprüfung Ihrer App verwendet. Beheben Sie Fehler oder Warnungen, und lesen Sie die Prüfliste vor der Übermittlung.

## <a name="test-your-app-directly-in-teams"></a>Testen Sie Ihre App direkt in Teams

Das Entwicklerportal bietet Optionen zum Testen und Debuggen Ihrer App:

* In **overview**, you can see a snapshot of whether your app's configurations validate against Teams store test cases.
* Mit **der Vorschau in Teams** können Sie Ihre App schnell im Teams-Client zum Debuggen starten.

## <a name="distribute-your-app"></a>Verteilen Ihrer App

Verwenden Sie im Entwicklerportal **"Verteilen",** um ein App-Paket herunterzuladen, es in Ihrer Organisation zu veröffentlichen oder im Teams Store zu veröffentlichen.

Weitere Informationen finden Sie unter [Verteilen Ihrer Teams-App.](~/concepts/deploy-and-publish/apps-publish-overview.md)

## <a name="analyze-your-apps-usage"></a>Analysieren der Nutzung Ihrer App

In **overview**, you can see the total number of active users for your app. Diese Metriken sind für Apps verfügbar, die im Teams Store oder im App-Katalog einer Organisation über das Entwicklerportal veröffentlicht und auf die App-ID beschränkt sind.

| Metrik | Definition |
| :-----------------------| :------------------------------------------------------------------------------------------------------|
| *Monatlich R30* | Die Standardverwendungsmetrik. Es zeigt die Anzahl der eindeutigen aktiven Benutzer an, die Ihre App innerhalb dieses rollenden 30-Tage-Fensters in UTC verwendet haben. |
| *Täglich* | Zeigt die Anzahl der eindeutigen aktiven Benutzer an, die Ihre App an einem bestimmten Tag in UTC verwendet haben. |

Die monatliche und tägliche Nutzung wird für die letzten sieben Tage, 30 Tage und 60 Tage angezeigt. Die Nutzung sollte für einen bestimmten Tag innerhalb von 24 bis 48 Stunden widergespiegelt werden. Die Anzeige neuer Apps kann bis zu 3 bis 5 Tage dauern.

## <a name="use-tools-to-create-app-features"></a>Verwenden von Tools zum Erstellen von App-Features

Das Entwicklerportal enthält auch Tools, mit denen Sie einige wichtige Features von Teams-Apps erstellen können. Einige dieser Tools umfassen:

* **Szenenstudio:** Entwerfen [sie benutzerdefinierte Szenen im Zusammen-Modus](~/apps-in-teams-meetings/teams-together-mode.md) für Teams Besprechungen.
* **Editor für adaptive Karten:** Erstellen und Anzeigen einer Vorschau adaptiver Karten, die in Ihre Apps aufgenommen werden sollen.
* **Microsoft Identity Platform Verwaltung:** Registrieren Sie Ihre Apps bei Azure Active Directory (Azure AD), um Benutzern zu helfen, sich anzumelden und Zugriff auf APIs bereitzustellen.
