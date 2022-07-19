---
title: Live Share Übersicht
author: surbhigupta
description: In diesem Modul erfahren Sie, was das Microsoft Live Share SDK und seine Benutzerszenarien sind.
ms.topic: overview
ms.localizationpriority: high
ms.author: v-ypalikila
ms.date: 04/07/2022
ms.openlocfilehash: 80d28acd5616fea371f3cd84354412504815ff87
ms.sourcegitcommit: 79d525c0be309200e930cdd942bc2c753d0b718c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2022
ms.locfileid: "66841862"
---
---

# <a name="live-share-sdk"></a>Live Share SDK

> [!Note]
> Das Live Share SDK ist derzeit nur in der [Public Developer Preview](../resources/dev-preview/developer-preview-intro.md) verfügbar. Sie müssen Teil der öffentlichen Developer-Vorschau für Microsoft Teams sein, um das Live Share SDK verwenden zu können.

Live Share ist ein SDK, das entwickelt wurde, um Teams-Apps in kollaborative Mehrbenutzererlebnisse umzuwandeln, ohne einen dedizierten Back-End-Code schreiben zu müssen. Das Live Share SDK integriert Meetings nahtlos in [Fluid Framework](https://fluidframework.com/). Fluid Framework ist eine Sammlung von Client-Bibliotheken zum Verteilen und Synchronisieren von freigegeben Status. Live Share bietet ein kostenloses, vollständig verwaltetes und einsatzbereites [Azure Fluid Relay](/azure/azure-fluid-relay/), das durch die Sicherheit und globale Reichweite von Teams unterstützt wird.

> [!div class="nextstepaction"]
> [Erste Schritte](teams-live-share-quick-start.md)

Das Live Share SDK bietet eine `TeamsFluidClient` Klasse zum Verbinden mit einem speziellen Fluid Container, der jedem Meeting in wenigen Codezeilen zugeordnet ist. Zusätzlich zu den von Fluid Framework bereitgestellten Datenstrukturen unterstützt Live Share auch einen neuen Satz von DDS-Klassen (Distributed Data Structure), um das Erstellen von Anwendungen für gängige Besprechungsszenarien, wie z. B. die Wiedergabe gemeinsam genutzter Medien, zu vereinfachen.

:::image type="content" source="../assets/images/teams-live-share/teams-live-share-contoso-video.gif" alt-text="Live Share Video-Sharing-Erfahrung":::

## <a name="why-build-apps-using-the-live-share-sdk"></a>Warum Apps mit dem Live Share SDK erstellen?

Das Erstellen von kollaborativen Apps kann schwierig, zeitaufwändig und kostspielig sein und umfasst komplexe Compliance-Anforderungen in großem Maßstab. Benutzer von Teams verbringen viel Zeit damit, die Arbeit mit Teamkollegen zu überprüfen, gemeinsam Videos anzusehen und neue Ideen durch Bildschirmfreigabe zu sammeln. Mit dem Live Share SDK können Sie Ihre App mit minimalen Investitionen in etwas kollaborativeres verwandeln.

Hier sind einige der wichtigsten Vorteile des Live Share SDK:

* Problemloses Sitzungsmanagement und Sicherheit
* Zustandsbehaftete und zustandslose verteilte Datenstrukturen
* Medienerweiterungen zum einfachen Synchronisieren von Video und Audio
* Besprechungsberechtigungen mithilfe der Rollenüberprüfung respektieren
* Kostenloser und vollständig verwalteter Dienst mit geringer Latenz
* Intelligentes Audio-Ducking

:::image type="content" source="../assets/images/teams-live-share/Teams-live-share-schematics.png" alt-text="Teams Live Share":::

## <a name="user-scenarios"></a>Benutzerszenarien

|Szenario|Beispiel|
| :------- | :--------------------- |
| Benutzer und ihre Kollegen haben ein Meeting angesetzt, um eine frühe Bearbeitung eines Marketingvideos bei einer bevorstehenden Führungsüberprüfung vorzustellen, und möchten bestimmte Abschnitte für Feedback hervorheben. | Benutzer teilen das Video auf der Meeting-Bühne und starten das Video. Bei Bedarf hält der Benutzer das Video an, um die Szene zu besprechen. Benutzer können abwechselnd Teile des Bildschirms übermalen, um wichtige Punkte hervorzuheben.|
| Sie sind Projektmanager für ein agiles Team und spielen mit Ihrem Team Agile Poker, um den Arbeitsaufwand für einen bevorstehenden Sprint abzuschätzen.| Sie teilen eine Agile Poker-Planungs-App mit der Besprechungsbühne, die das Live Share SDK verwendet, und spielen das Planungsspiel, bis das Team einen Konsens trifft.|

> [!IMPORTANT]
> Alle Daten, die über den gehosteten Azure Fluid Relay-Dienst des Live Share SDK gesendet oder gespeichert werden, sind 24 Stunden lang zugänglich. Weitere Informationen finden Sie unter [Häufig gestellte Fragen zu Live Share](teams-live-share-faq.md).

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erste Schritte](teams-live-share-quick-start.md)

## <a name="see-also"></a>Siehe auch

* [GitHub-Repository](https://github.com/microsoft/live-share-sdk)
* [Live Share SDK-Referenzdokumente](/javascript/api/@microsoft/live-share/)
* [Referenzdokumentation zum Live Share Media SDK](/javascript/api/@microsoft/live-share-media/)
* [Live Share-Funktionen](teams-live-share-capabilities.md)
* [Live Share-Medienfunktionen](teams-live-share-media-capabilities.md)
* [Live Share – FAQ](teams-live-share-faq.md)
* [Teams-Apps in Besprechungen](teams-apps-in-meetings.md)
