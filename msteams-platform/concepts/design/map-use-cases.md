---
title: Zuordnen von Anwendungsfällen zu Microsoft TeamsApp-Features und -Funktionen
author: surbhigupta
description: Ermitteln Sie, wie die Anwendungsfälle für Ihre App innerhalb der Microsoft Teams-Oberfläche, in App-Features und -Funktionen funktionieren können. Ordnen Sie allgemeine Anwendungsfälle Funktionen zu.
ms.topic: conceptual
ms.localizationpriority: high
ms.author: anclear
ms.openlocfilehash: 50298ec41a6f5f6a4ca0ecfcf3b0570762d2720c
ms.sourcegitcommit: c398dfdae9ed96f12e1401ac7c8d0228ff9c0a2b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2022
ms.locfileid: "66557855"
---
# <a name="map-your-use-cases-to-teams-app-features"></a>Zuordnen von Anwendungsfällen zu Microsoft Teams-App-Features

Ein gut definierter Anwendungsfall hilft Ihnen, das Framework von Features zu ermitteln, die Sie in der Microsoft Teams-App benötigen. Nachdem Sie die Benutzeranforderungen ermittelt haben, definieren Sie den Bereich und die Microsoft Teams-Funktion, die für Ihre App am besten geeignet sind.

Sie können Ihren Anwendungsfall basierend auf folgenden Elementen zuordnen:

* Freigeben von und Zusammenarbeit an Elementen in einem externen System
* Starten von Workflows und Senden von Benachrichtigungen an Benutzer
* Verwenden von Social Media-Plattformen, Unterhaltungs-Bots und Kombinieren mehrerer Features

## <a name="common-use-cases-mapped-to-teams-capabilities"></a>Häufige Anwendungsfälle, die Microsoft Teams-Funktionen zugeordnet sind

Der nächste Schritt besteht darin, Anwendungsfälle App-Funktionen zuzuordnen.

Im Folgenden finden Sie eine Liste allgemeiner Benutzerszenarien, die Microsoft Teams-Funktionen zugeordnet sind. Es handelt sich nicht um eine vollständige Liste, sondern hilft Ihnen dabei, einige der Möglichkeiten zu durchdenken, die Ihnen zur Verfügung stehen.
</br>
</br>
<details>
<summary>Erstellen, Freigeben von und Zusammenarbeit an Elementen in einem externen System</summary>

Apps für die Interaktion mit Ihren Daten

| **Sie möchten...** | **Probieren Sie Folgendes aus...** |
| --- | --- |
| Externe Systeme durchsuchen und die Ergebnisse als interaktive Karte mit anderen teilen | Nachrichtenerweiterungen mit Suchbefehlen |
| Informationen sammeln, um sie in einen Datenspeicher einzufügen oder erweiterte Suchvorgänge auszuführen. | Nachrichtenerweiterungen mit Aktionsbefehlen |
| Eingebettete Weblösungen erstellen zum Anzeigen, Arbeiten mit und Freigeben von Daten | Registerkarten |
| Daten aus dem Microsoft Teams-Client per Push übertragen und senden | Connectors und Webhooks|
| Interaktive modale Formulare, von wo immer Sie diese benötigen, um Informationen zu sammeln oder anzuzeigen | Aufgabenmodule |

</details>
</br>
<details>
<summary>Initiieren von Workflows und Prozessen</summary>

Eine schnelle Möglichkeit, einen Prozess oder Workflow in einem externen System zu starten.

| **Sie möchten...** | **Probieren Sie Folgendes aus...** |
| --- | --- |
| Nachrichten auslösen, sodass Ihre Benutzer die Inhalte einer Nachricht schnell an Ihre Webdienste senden können | Aktionsbefehle für Nachrichtenerweiterungen |
| Öffnen Sie Nachrichten von einer Registerkarte, einem Bot oder einer Nachrichtenerweiterung, um Informationen zu sammeln, bevor Sie einen Workflow starten. | Aufgabenmodule |
| Mit Ihren Benutzern über Text und funktionsreiche Karten interagieren | Unterhaltungs-Bots |
| Eine gute Wahl für einfache Hin- und Her-Interaktionen, wenn Sie keinen vollständigen Unterhaltungs-Bot erstellen müssen. |  Ausgehende Webhooks |

</details>
</br>
<details>
<summary>Senden von Benachrichtigungen und Warnungen</summary>

Senden Sie asynchrone Benachrichtigungen und Warnungen an Ihre Benutzer in Microsoft Teams.

| **Sie möchten...** | **Probieren Sie Folgendes aus...** |
| --- | --- |
| Proaktiv Nachrichten an Gruppen, Kanäle oder einzelne Benutzer senden | Unterhaltungs-Bots |
| Zulassen, dass ein Kanal Nachrichten abonniert. Mithilfe eines Connectors können Benutzer das Abonnement über eine Konfigurationsseite anpassen. | Connectors und eingehende Webhooks |

</details>
</br>
<details>
<summary>Fragen stellen und Antworten erhalten</summary>

Kommunizieren mit Ihren Benutzern und Lösen ihrer Fragen

| **Sie möchten...** | **Probieren Sie Folgendes aus...** |
| --- | --- |
| Verarbeitung natürlicher Sprache, KI, maschinelles Lernen u. Ä. Verwenden Sie einen Bot, der von der intelligenten Cloud unterstützt wird, um Ihren Benutzern die benötigten Antworten bereitzustellen. | Unterhaltungs-Bots |
| Ihr vorhandenes Webportal in Microsoft Teams einbetten oder eine Microsoft Teams-spezifische Version für zusätzliche Funktionen erstellen | Registerkarten |

</details>

## <a name="app-capabilities-mapped-to-features"></a>Features zugeordnete App-Funktionen

Die Microsoft Teams-Plattform bietet eine Vielzahl von Features. Jedes Feature bietet eine Möglichkeit der Interaktion mit Ihren Benutzern, die die Microsoft Teams App-Funktion für die Benutzeranforderungen relevant macht.

Sehen wir uns an, wie Microsoft Teams-Funktionen verschiedene Features für Ihre App ermöglichen.

:::image type="content" source="../../assets/images/overview/teams-apps-capabilities.png" alt-text="Abbildung von Microsoft Teams-Funktionen":::

Beispiel:

* Verwenden Sie die **Registerkartenfunktion**, um Aufgabenmodule anzuzeigen, Geräteberechtigungen anzufordern, <`iframe`> Inhalte anzuzeigen oder Deep-Links zu verwenden.
* Nutzen Sie die Möglichkeit der **Nachrichtenerweiterung**, um Karten zu versenden, Links freizugeben oder Aktionen für Nachrichten durchzuführen.

## <a name="see-also"></a>Siehe auch

* [Planungscheckliste](../design/planning-checklist.md)
* [Erstellen Ihrer ersten Microsoft Teams-App](../../get-started/get-started-overview.md)
