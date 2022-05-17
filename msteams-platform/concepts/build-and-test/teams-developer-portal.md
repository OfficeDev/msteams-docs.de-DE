---
title: Verwalten Ihrer Apps mit dem Entwicklerportal
description: Erfahren Sie, wie Sie Ihre Apps mithilfe des Entwicklerportals für Microsoft Teams konfigurieren, verteilen und verwalten.
keywords: Erste Schritte für Entwicklerportalteams
ms.localizationpriority: medium
ms.topic: overview
ms.author: surbhigupta
ms.openlocfilehash: c7ca898cd411028dffa6c8a197c78cd796f823e5
ms.sourcegitcommit: a3567e3e1a52b8e3cb2072b037f0e75bd0f12e58
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2022
ms.locfileid: "65439325"
---
# <a name="manage-your-teams-apps-using-developer-portal"></a>Verwalten Ihrer Teams-Apps mithilfe des Entwicklerportals

Das <a href="https://dev.teams.microsoft.com" target="_blank">Entwicklerportal für Teams</a> ist das primäre Tool zum Konfigurieren, Verteilen und Verwalten Ihrer Microsoft Teams-Apps. Mit dem Entwicklerportal können Sie mit Kollegen an Ihrer App zusammenarbeiten, Laufzeitumgebungen einrichten und vieles mehr.

:::image type="content" source="../../assets/images/tdp/tdp_home_1.png" alt-text="Screenshot der Startseite des Entwicklerportals für Teams.":::

> [!NOTE]
>
> * Derzeit ist das Entwicklerportal nicht für Mandanten Government Community Cloud (GCC), GCC-High oder Department of Defense (DOD) verfügbar.
> * Sie können jedoch einen regulären Mandanten verwenden, um eine App im Entwicklerportal zu erstellen, die App herunterzuladen und die App [mithilfe von Microsoft Graph](/graph/api/teamsapp-publish?view=graph-rest-1.0&tabs=http&preserve-view=true) in eine nationale Cloud hochzuladen. Weitere Informationen finden Sie unter ["Nationale Cloudbereitstellungen"](/graph/deployments).

## <a name="register-an-app"></a>Registrieren einer App

Das Entwicklerportal bietet mehrere Möglichkeiten zum Registrieren einer Teams-App:

* Registrieren einer brandneuen App
* Importieren eines vorhandenen App-Pakets

> [!NOTE]
> Wenn Sie eine App mit dem [Microsoft Teams Toolkit für Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) erstellen, können Sie diese App im Entwicklerportal verwalten.

## <a name="set-up-an-environment"></a>Einrichten einer Umgebung

Sie können Umgebungen und globale Variablen konfigurieren, um den Übergang Ihrer App von der lokalen Laufzeit zur Produktion zu erleichtern. Globale Variablen werden in allen Umgebungen verwendet.

So richten Sie eine Umgebung ein:

1. Wählen Sie im Entwicklerportal die App aus, an der Sie gerade arbeiten.
2. Wechseln Sie zur Seite **"Umgebungen",** und wählen Sie **+Umgebung hinzufügen** aus.
3. Wählen Sie **aus, und fügen Sie eine Variable hinzu** , um Konfigurationsvariablen für Ihre Umgebung zu erstellen.

So verwenden Sie Variablen:

Verwenden Sie die Variablennamen anstelle hartcodierter Werte, um Ihre App-Konfigurationen festzulegen.

1. Geben Sie `{{` in ein beliebiges Feld im Entwicklerportal ein. Es wird eine Dropdownliste mit allen Variablen angezeigt, die Sie für die ausgewählte Umgebung zusammen mit den globalen Variablen erstellt haben.  
1. Wählen Sie vor dem Herunterladen des App-Pakets (z. B. beim Vorbereiten der Veröffentlichung im Teams Store) die Umgebung aus, die Sie verwenden möchten. Ihre App-Konfigurationen werden automatisch basierend auf der Umgebung aktualisiert.

## <a name="identify-app-owners"></a>Identifizieren von App-Besitzern

Jede App enthält eine Seite **"Besitzer"** , auf der Sie Ihre App-Registrierung für Kollegen in Ihrer Organisation freigeben können. Die **Rolle "Mitwirkender"** verfügt über die gleichen Berechtigungen wie die **Rolle "Besitzer"** , mit Ausnahme der Möglichkeit, eine App zu löschen.

## <a name="configure-your-apps-capabilities-and-other-important-metadata"></a>Konfigurieren der Funktionen Ihrer App und anderer wichtiger Metadaten

Eine Teams-App ist eine Web-App. Wie alle Web-Apps wird der Quellcode in der Regel in einem IDE- oder Code-Editor entwickelt und irgendwo in der Cloud (z. B. Azure) gehostet.

Um Ihre App in Teams zu installieren und zu rendern, müssen Sie eine Reihe von Konfigurationen einschließen, die Teams erkennt. Dies geschieht traditionell durch Erstellen eines App-Manifests, einer JSON-Datei, die alle Metadaten enthält, Teams ihre App-Inhalte anzeigen müssen. Das Entwicklerportal abstrahiert diesen Prozess und enthält neue Features und Tools, die Ihnen helfen, erfolgreicher zu sein.

## <a name="test-your-app-directly-in-teams"></a>Testen Sie Ihre App direkt in Teams

Das Entwicklerportal bietet Optionen zum Testen und Debuggen Ihrer App:

* Auf der Seite **"Übersicht**" sehen Sie eine Momentaufnahme, ob die Konfigurationen Ihrer App anhand Teams Store-Testfälle überprüft werden.
* Mit der Schaltfläche "**Vorschau in Teams**" können Sie Ihre App schnell im Teams-Client zum Debuggen starten.

## <a name="distribute-your-app"></a>Verteilen Ihrer App

Verwenden Sie im Entwicklerportal die Schaltfläche "**Verteilen**", um ein App-Paket herunterzuladen, in Ihrer Organisation zu veröffentlichen oder im Teams Store zu veröffentlichen.

Weitere Informationen finden Sie unter [Verteilen Ihrer Teams-App](~/concepts/deploy-and-publish/apps-publish-overview.md).

## <a name="analyze-your-apps-usage"></a>Analysieren der App-Nutzung

Im Entwicklerportal für Teams können Sie auf der Seite **"Übersicht**" die Gesamtzahl der aktiven Benutzer für Ihre App anzeigen.

> [!NOTE]
> Nutzungsanalysen sind derzeit nur für neue benutzerdefinierte Apps verfügbar, die in Ihrer Organisation über das **Entwicklerportal** für Teams (vormals App Studio) veröffentlicht oder nach April 2022 für Teams in das **Entwicklerportal** importiert wurden. Nutzungsanalysen für alle im Teams Store veröffentlichten Apps finden Sie im **Partner Center**, um weitere Informationen [Teams App-Nutzungsbericht zu erhalten](/office/dev/store/teams-apps-usage).

| Metrik | Definition |
| :-----------------------| :------------------------------------------------------------------------------------------------------|
| *Monatlich R30* | Die Standardnutzungsmetrik. Es zeigt die Anzahl der eindeutigen aktiven Benutzer, die Ihre App in diesem rollierenden 30-Tage-Fenster in UTC verwendet haben. |
| *Täglich* | Es zeigt Die Anzahl der eindeutigen aktiven Benutzer, die Ihre App an einem bestimmten Tag in UTC verwendet haben. |

Die App-Nutzung für einen bestimmten Tag wird innerhalb von 24 bis 48 Stunden widergespiegelt, und die Nutzungsdaten für neue Apps können bis zu drei bis fünf Tage dauern, bis sie in den Diagrammen widergespiegelt werden.

Sie können die Nutzung Ihrer App und andere Einblicke auf der **Analyseseite** anzeigen. So greifen Sie auf die Seite zu:

1. Wechseln Sie zum **[Entwicklerportal für Teams](https://dev.teams.microsoft.com)**.
1. Wählen Sie im linken Bereich **Teams** aus.
1. Wählen Sie die erforderliche App auf der Seite **"Apps** " aus.
1. Wählen Sie unter "**Übersicht**" die Option "**Analyse**" oder unter der Karte "**Aktive Benutzer (Vorschau)"** die Option "**Details anzeigen**" aus.

 :::image type="content" source="../../assets/images/tdp/dev-app-portal.PNG" alt-text="dev-Portal-analytics"lightbox="../../assets/images/tdp/dev-app-portal.PNG":::

Während Sie einzelne Metriken auf dieser Seite erkunden, können Sie die Schaltfläche " **Filtern** " verwenden, um die Nutzung Ihrer App anhand der folgenden Filteroptionen zu analysieren:

* Aggregationstyp: Mit diesem Filter können Sie die folgenden Metriken nach einer Anzahl unterschiedlicher Benutzer oder einer Anzahl unterschiedlicher Mandanten oder Kunden gruppieren.
* Plattform
* Betriebssystem
* Bereich

 :::image type="content" source="../../assets/images/tdp/dev-analytics-filter.PNG" alt-text="Filter":::

Nachdem Sie Ihre gewünschten Filter ausgewählt haben, können Sie die folgenden einzelnen Widgets erkunden:

* [Nutzung nach Zeitraum](#usage-by-time-period)
* [Verwendung nach Plattform und Betriebssystem](#usage-by-platform-and-os)
* [Verwendung nach Aufbewahrungsstatus](#usage-by-retention-state)
* [Nutzungsintensität](#usage-intensity)

### <a name="usage-by-time-period"></a>Nutzung nach Zeitraum

Das Diagramm **"Nutzung nach Zeitraum** " zeigt die Anzahl der aktiven Benutzer oder Mandanten, die Ihre App über verschiedene Zeiträume hinweg geöffnet und verwendet haben.

 :::image type="content" source="../../assets/images/tdp/usage-by-time-period.png" alt-text="Period":::

| Metrik | Definition |
| :-----------------------| :------------------------------------------------------------------------------------------------------|
| Monatlich R30 | Jeder Datenpunkt stellt einen bestimmten R30-Zeitraum (rollierender 30-Tage-Zeitraum) dar. |
| Monatlich R28 | Jeder Datenpunkt stellt einen bestimmten R28-Zeitraum (rollierender 28-Tag) dar. |
| Wöchentlich R7| Jeder Datenpunkt stellt einen bestimmten R7-Zeitraum (Rolling 7 Day) dar. |
| Täglich | Jeder Datenpunkt stellt einen bestimmten R1-Zeitraum (Rolling 1 Day) dar. |

### <a name="usage-by-platform-and-os"></a>Verwendung nach Plattform und Betriebssystem

Das Diagramm **"Nutzung nach Plattform und Betriebssystem**" zeigt die aktive Nutzung Ihrer App über verschiedene Endpunkte hinweg an, z. B. **Windows**, **Mac**, **iOS**, **Android** und **Web**. Derselbe Benutzer oder Mandant kann eine App auf mehreren Endpunkten verwenden. Jeder Datenpunkt stellt einen bestimmten R30-Zeitraum (rollierender 30-Tage-Zeitraum) dar.

 :::image type="content" source="../../assets/images/tdp/usage-by-platform-OS.png" alt-text="Plattform":::

### <a name="usage-by-retention-state"></a>Verwendung nach Aufbewahrungsstatus

Mithilfe des Diagramms " **Verwendung nach Aufbewahrungsstatus** " können Sie vier wichtige Aufbewahrungs- oder Änderungsmetriken für Ihre App im Laufe der Zeit nachverfolgen.

:::image type="content" source="../../assets/images/tdp/usage-by-retention-state.png" alt-text="Retention":::

| Metrik | Definition |
| :-----------------------| :------------------------------------------------------------------------------------------------------|
| Neue Benutzer oder Mandanten | Aktive Benutzer oder Mandanten, die neu sind und Ihre App nicht verwendet haben. |
| Zurückgeben von Benutzern oder Mandanten | Aktive Benutzer oder Mandanten, die Ihre App während eines bestimmten Zeitraums von R30 (Rolling 30 Day) und dem unmittelbar vorhergehenden R30-Zeitraum verwendet haben. |
| Wiedererstandene Benutzer oder Mandanten | Aktive Benutzer oder Mandanten, die Ihre App ein oder mehrere Male zuvor, aber nicht im unmittelbar vorhergehenden R30-Zeitraum verwendet haben. |
| Abgelaufene Benutzer oder Mandanten | Aktive Benutzer oder Mandanten, die während eines bestimmten R30-Zeitraums nicht angezeigt wurden, aber während des unmittelbar vorhergehenden R30-Zeitraums angezeigt wurden. |

### <a name="usage-intensity"></a>Nutzungsintensität

Im Diagramm **"Nutzungsintensität** " werden die wichtigsten Nutzungsintensitätsmetriken für Ihre App angezeigt.

 :::image type="content" source="../../assets/images/tdp/usage-intensity.png" alt-text="Intensität":::

| Metrik | Definition |
| :-----------------------| :------------------------------------------------------------------------------------------------------|
| Pro Monat verwendete Mediantage | Die medianen Anzahl von Tagen, in denen Ihre App im letzten Zeitraum von R30 (Rolling 30 Day) geöffnet wurde. |
| % der Nutzung von mehr als 5 Tagen | Die % der aktiven Benutzer, die die App im letzten R30-Zeitraum mehr als fünf Tage geöffnet oder verwendet haben. |
| DAU/MAU | Das Verhältnis der durchschnittlichen Anzahl eindeutiger Benutzer oder Mandanten, die Ihre App an jedem Tag verwendet haben, dividiert durch die monatlich aktiven Benutzer für den ausgewählten R30-Zeitraum. |

### <a name="app-dashboard"></a>App-Dashboard

In der **Dashboardtabelle "Meine App** " werden die neuesten R30-Daten (Rolling 30 Day) für jede der Metriken unter den vorherigen vier Kategorien sowie die Monatsänderung angezeigt. Verwenden Sie die Zeitauswahl oben links, und wählen Sie das gewünschte Datum aus. Sie können täglich R30-Daten für die letzten 75 Tage und die Daten zum Ende des Monats R30 für bis zu 12 Monate anzeigen.

Sie können jeden dieser **Metriknamen** auswählen, um Trends im Laufe der Zeit anzuzeigen.

 :::image type="content" source="../../assets/images/tdp/app-dashboard.png" alt-text="App":::

## <a name="use-tools-to-create-app-features"></a>Verwenden von Tools zum Erstellen von App-Features

Das Entwicklerportal enthält auch Tools, mit denen Sie einige wichtige Features von Teams-Apps erstellen können. Einige dieser Tools umfassen:

* **Szenenstudio**: Entwerfen [von benutzerdefinierten Zusammen-Modus-Szenen](~/apps-in-teams-meetings/teams-together-mode.md) für Teams Besprechungen.
* **Editor für adaptive Karten**: Erstellen Sie adaptive Karten, und zeigen Sie eine Vorschau an, die in Ihre Apps aufgenommen werden sollen.
* **Microsoft Identity Platform-Verwaltung**: Registrieren Sie Ihre Apps bei Azure Active Directory, um Benutzern bei der Anmeldung und dem Zugriff auf APIs zu helfen.

## <a name="see-also"></a>Siehe auch

[Einschließen eines SaaS-Angebots in Ihre Microsoft Teams-App](~/concepts/deploy-and-publish/appsource/prepare/include-saas-offer.md)
