---
title: Analysieren der App-Nutzung im Entwicklerportal
description: In diesem Modul erfahren Sie, wie Sie die Nutzung Ihrer App im Entwicklerportal analysieren.
ms.localizationpriority: medium
ms.topic: overview
ms.author: surbhigupta
ms.openlocfilehash: 43758fdebd1f2e76318880a51d9173469b0ed604
ms.sourcegitcommit: 990a36fb774e614146444d4adaa2c9bcdb835998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2022
ms.locfileid: "67232395"
---
# <a name="analyze-your-apps-usage-in-developer-portal"></a>Analysieren der App-Nutzung im Entwicklerportal

Im Entwicklerportal für Teams können Sie auf der Seite **"Übersicht** " die Gesamtzahl der aktiven Benutzer für Ihre App anzeigen.

> [!NOTE]
> Nutzungsanalysen sind derzeit nur für neue benutzerdefinierte Apps verfügbar, die in Ihrer Organisation über **das Entwicklerportal** für Teams veröffentlicht oder nach April 2022 in **das Entwicklerportal** für Teams importiert wurden. Nutzungsanalysen für alle im Teams-Store veröffentlichten Apps sind im **Partner Center** verfügbar, um weitere Informationen zum [Nutzungsbericht für Teams-Apps zu erhalten](/office/dev/store/teams-apps-usage).

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

 :::image type="content" source="../../assets/images/tdp/dev-app-portal.png" alt-text="Die Screenshots zeigen Ihnen die Analyseseite Ihrer App im Entwicklerportal."lightbox="../../assets/images/tdp/dev-app-portal.png":::

Während Sie einzelne Metriken auf dieser Seite erkunden, können Sie die Schaltfläche " **Filtern** " verwenden, um die Nutzung Ihrer App anhand der folgenden Filteroptionen zu analysieren:

* Aggregationstyp: Mit diesem Filter können Sie die folgenden Metriken nach einer Anzahl unterschiedlicher Benutzer oder einer Anzahl unterschiedlicher Mandanten oder Kunden gruppieren.
* Plattform
* Betriebssystem
* Bereich

 :::image type="content" source="../../assets/images/tdp/dev-analytics-filter.png" alt-text="Die Screenshots zeigen den Filter der Analyseseite im Entwicklerportal.":::

Nachdem Sie Ihre gewünschten Filter ausgewählt haben, können Sie die folgenden einzelnen Widgets erkunden:

* [Nutzung nach Zeitraum](#usage-by-time-period)
* [Verwendung nach Plattform und Betriebssystem](#usage-by-platform-and-os)
* [Verwendung nach Aufbewahrungsstatus](#usage-by-retention-state)
* [Nutzungsintensität](#usage-intensity)

## <a name="usage-by-time-period"></a>Nutzung nach Zeitraum

Das Diagramm **"Nutzung nach Zeitraum** " zeigt die Anzahl der aktiven Benutzer oder Mandanten, die Ihre App über verschiedene Zeiträume hinweg geöffnet und verwendet haben.

 :::image type="content" source="../../assets/images/tdp/usage-by-time-period.png" alt-text="Die Screenshots zeigen die Verwendung nach Zeitraumdiagramm für Ihre veröffentlichte App.":::

| Metrik | Definition |
| :-----------------------| :------------------------------------------------------------------------------------------------------|
| Monatlich R30 | Jeder Datenpunkt stellt einen bestimmten R30-Zeitraum (rollierender 30-Tage-Zeitraum) dar. |
| Monatlich R28 | Jeder Datenpunkt stellt einen bestimmten R28-Zeitraum (rollierender 28-Tag) dar. |
| Wöchentlich R7| Jeder Datenpunkt stellt einen bestimmten R7-Zeitraum (Rolling 7 Day) dar. |
| Täglich | Jeder Datenpunkt stellt einen bestimmten R1-Zeitraum (Rolling 1 Day) dar. |

## <a name="usage-by-platform-and-os"></a>Verwendung nach Plattform und Betriebssystem

Das Diagramm **"Nutzung nach Plattform und Betriebssystem** " zeigt die aktive Nutzung Ihrer App über verschiedene Endpunkte hinweg, z. B. **Windows**, **Mac**, **iOS**, **Android** und **Web**. Derselbe Benutzer oder Mandant kann eine App auf mehreren Endpunkten verwenden. Jeder Datenpunkt stellt einen bestimmten R30-Zeitraum (rollierender 30-Tage-Zeitraum) dar.

 :::image type="content" source="../../assets/images/tdp/usage-by-platform-OS.png" alt-text="Die Screenshots zeigen die Verwendung nach Plattform und Betriebssystemdiagramm für Ihre veröffentlichte App.":::

## <a name="usage-by-retention-state"></a>Verwendung nach Aufbewahrungsstatus

Mithilfe des Diagramms " **Verwendung nach Aufbewahrungsstatus** " können Sie vier wichtige Aufbewahrungs- oder Änderungsmetriken für Ihre App im Laufe der Zeit nachverfolgen.

:::image type="content" source="../../assets/images/tdp/usage-by-retention-state.png" alt-text="Die Screenshots zeigen Die Verwendung nach Aufbewahrungszustandsdiagramm für Ihre veröffentlichte App.":::

| Metrik | Definition |
| :-----------------------| :------------------------------------------------------------------------------------------------------|
| Neue Benutzer oder Mandanten | Aktive Benutzer oder Mandanten, die neu sind und Ihre App nicht verwendet haben. |
| Zurückgeben von Benutzern oder Mandanten | Aktive Benutzer oder Mandanten, die Ihre App während eines bestimmten Zeitraums von R30 (Rolling 30 Day) und dem unmittelbar vorhergehenden R30-Zeitraum verwendet haben. |
| Wiedererstandene Benutzer oder Mandanten | Aktive Benutzer oder Mandanten, die Ihre App ein oder mehrere Male zuvor, aber nicht im unmittelbar vorhergehenden R30-Zeitraum verwendet haben. |
| Abgelaufene Benutzer oder Mandanten | Aktive Benutzer oder Mandanten, die während eines bestimmten R30-Zeitraums nicht angezeigt wurden, aber während des unmittelbar vorhergehenden R30-Zeitraums angezeigt wurden. |

## <a name="usage-intensity"></a>Nutzungsintensität

Im Diagramm **"Nutzungsintensität** " werden die wichtigsten Nutzungsintensitätsmetriken für Ihre App angezeigt.

 :::image type="content" source="../../assets/images/tdp/usage-intensity.png" alt-text="Die Screenshots zeigen Ihnen das Nutzungsintensitätsdiagramm für Ihre veröffentlichte App.":::

| Metrik | Definition |
| :-----------------------| :------------------------------------------------------------------------------------------------------|
| Pro Monat verwendete Mediantage | Die medianen Anzahl von Tagen, in denen Ihre App im letzten Zeitraum von R30 (Rolling 30 Day) geöffnet wurde. |
| % der Nutzung von mehr als 5 Tagen | Die % der aktiven Benutzer, die die App im letzten R30-Zeitraum mehr als fünf Tage geöffnet oder verwendet haben. |
| DAU/MAU | Das Verhältnis der durchschnittlichen Anzahl eindeutiger Benutzer oder Mandanten, die Ihre App an jedem Tag verwendet haben, dividiert durch die monatlich aktiven Benutzer für den ausgewählten R30-Zeitraum. |

## <a name="app-dashboard"></a>App-Dashboard

In der **Dashboardtabelle "Meine App** " werden die neuesten R30-Daten (Rolling 30 Day) für jede der Metriken unter den vorherigen vier Kategorien sowie die Monatsänderung angezeigt. Verwenden Sie die Zeitauswahl oben links, und wählen Sie das gewünschte Datum aus. Sie können täglich R30-Daten für die letzten 75 Tage und die Daten zum Ende des Monats R30 für bis zu 12 Monate anzeigen.

Sie können jeden dieser **Metriknamen** auswählen, um Trends im Laufe der Zeit anzuzeigen.

 :::image type="content" source="../../assets/images/tdp/app-dashboard.png" alt-text="Die Screenshots zeigen Das App-Dashboarddiagramm für Ihre veröffentlichte App.":::

## <a name="see-also"></a>Siehe auch

[Einschließen eines SaaS-Angebots mit Ihrer Microsoft Teams-App](~/concepts/deploy-and-publish/appsource/prepare/include-saas-offer.md)
