---
title: Produktionsfertige Shifts-Connectors
description: Mitarbeiterverwaltung Verschiebt Connectors für Teams
ms.topic: reference
author: laujan
ms.date: 03/09/2020
localization_priority: Normal
keywords: Microsoft Teams Connectors kronos
ms.author: lajanuar
ms.openlocfilehash: 94e0b2b61998510ea9dd054d118e856eadc49b2d
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019617"
---
# <a name="production-ready-shifts-connectors"></a>Produktionsfertige Shifts-Connectors  

Teams Shifts Workforce Management (WFM)-Connectors sind produktionsbereite, Open-Source- und communitygesteuerte Integrationen, die für Mitarbeiter in erster Front nützlich sind. Sie bieten eine nahtlose Erfahrung und einen schnellen Prozess für die digitale Transformation von FirstLine-Mitarbeitern mit Teams Shifts. 

Jeder Connector bietet detaillierte Anleitungen für die Bereitstellung und Integration in Ihre Organisation. Der vollständige Quellcode ist im GitHub-Repository verfügbar. Sie können details oder fork untersuchen und anpassen, um Ihre spezifischen Anforderungen zu erfüllen.   

Dieses Dokument enthält eine Übersicht über die wichtigsten Vorteile von Teams Shifts WFM Connectors, Kronos-to-Teams Shifts Connector und JDA-to-Teams Shifts Connector.

## <a name="key-benefits-of-teams-shifts-wfm-connectors"></a>Wichtige Vorteile von Teams Shifts WFM Connectors

Nachfolgend finden Sie die wichtigsten Vorteile von Teams Shifts-WFM-Connectors:

* **Plug -and-Play-Erfahrung:** Alle Shifts-WFM-Connectors enthalten ARM Azure-Bereitstellungsskripts, mit denen Sie alle erforderlichen Dienste in Microsoft Azure hosten können. Für die Bereitstellung der Apps ist keine Codierung erforderlich.

* **Produktionsbereiter Code:** Alle Shifts-Connectors entsprechen den empfohlenen bewährten Methoden für Sicherheit und Infrastruktur, und alle von der Community übermittelten Änderungen werden überprüft, um eine kontinuierliche Konformität sicherzustellen.

* **Anpassbar und erweiterbar:**   Zwar sind alle Shifts-WFM-Connectors bereit für die sofortige Verwendung, wobei die gesamte Codebasis und Bereitstellungsskripts verfügbar sind. Sie können sie ganz einfach an Ihre individuellen Anforderungen anpassen oder erweitern.

* **Ausführliche Dokumentation & Support:**   Alle Shifts-WFM-Connectors werden von einer End-to-End-Dokumentation für Lösungsarchitektur, Bereitstellung und Konfigurationsschritte begleitet. Die Connectorrepositorys werden überwacht, sodass Sie alle Probleme, Herausforderungen oder Schwierigkeiten melden können, die sie über den GitHub Issues Tracker des Repositorys haben.

* **Nahtlose Integration:** Durch die Integration zwischen WFM-Lösungen und Teams Shifts können Mitarbeiter von Firstline die Teams Shifts-App verwenden, um ihre Zeitpläne und Schichtzeiten ein- oder zu verwalten, und alle anderen features für die umfassende Zusammenarbeit, die in Teams bereitgestellt werden, direkt vom mobilen Gerät oder Desktop aus nutzen, ohne den Kontext auf eine andere App umschalten zu müssen.  

**Ansicht "Offene Schichten" in Teams** 

Die Verschiebungsansicht in Teams wird in der folgenden Abbildung angezeigt: 

![Offene Schichten in Teams](../assets/images/teams-open-shifts-view.png)

## <a name="kronos-to-teams-shifts-connector"></a>Kronos-zu-Teams-Schichtconnector

Mit Open-Source-Code können Sie Kronos Workforce Central Version 8.1 und höher mit Teams Shifts wie Desktop- oder mobilen Teams-Apps für die folgenden Firstline-Worker- und Managerszenarien integrieren:

* Anzeigezeitplan.

* Veröffentlichen und Anfordern offener Schichten.

* Swapverschiebungen.

* Fordern Sie eine Auszeit an.

* Bieten Sie Schichten an.

Weitere Informationen zur Bereitstellung des Kronos-to-Teams Shifts-Connectors finden Sie unter [Abrufen auf GitHub](https://aka.ms/KronosShiftsConnector).

## <a name="jda-to-teams-shifts-connector"></a>JDA-zu-Teams-Schichtconnector

Mit Open-Source-Code können Sie JDA, z. B. BlueYonder, Version 17.2 und höher, mit Teams Shifts wie Desktop- oder mobilen Teams-Apps für die folgenden FirstLine-Worker- und Managerszenarien integrieren:

* Veröffentlichen Sie Schichten und Planen von Gruppen in JDA, und zeigen Sie sie in Teams an.

* Aktivieren Sie umfangreiche Zeitplanungsszenarien, einschließlich anfordern von Schichtswaps und Auszeit.

* Festlegen der Benutzerverfügbarkeit mithilfe der [Microsoft Graph-API für Schichten](/graph/api/resources/shift?view=graph-rest-beta&preserve-view=true).

Weitere Informationen zu Beitrag und Vorschlag finden Sie unter [Get it on GitHub](https://aka.ms/JDAShiftsConnector).</br></br>

## <a name="see-also"></a>Siehe auch

> [!div class="nextstepaction"]
> [Integrieren von Web-Apps](~/samples/integrate-web-apps-overview.md)
