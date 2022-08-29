---
title: Live Share Übersicht
author: surbhigupta
description: In diesem Modul erfahren Sie, was das Microsoft Live Share SDK und seine Benutzerszenarien sind.
ms.topic: overview
ms.localizationpriority: high
ms.author: v-ypalikila
ms.date: 04/07/2022
ms.openlocfilehash: 3738ee1037c87f283fd31ebdaba53b57f1784bb2
ms.sourcegitcommit: 134ce9381891e51e6327f1f611fdfd60c90cca18
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2022
ms.locfileid: "67425624"
---
---

# <a name="live-share-sdk"></a>Live Share SDK

> [!NOTE]
> Das Live Share SDK ist derzeit in [der öffentlichen Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) verfügbar. Sie müssen Teil der öffentlichen Entwicklervorschau sein, damit Microsoft Teams Live Share verwenden kann.

Live Share ist ein SDK, das entwickelt wurde, um Teams-Apps in kollaborative Mehrbenutzererlebnisse umzuwandeln, ohne einen dedizierten Back-End-Code schreiben zu müssen. Live Share integriert Besprechungen nahtlos in [Fluid Framework](https://fluidframework.com/). Fluid Framework ist eine Sammlung von Client-Bibliotheken zum Verteilen und Synchronisieren von freigegeben Status. Live Share bietet ein kostenloses, vollständig verwaltetes und einsatzbereites [Azure Fluid Relay](/azure/azure-fluid-relay/), das durch die Sicherheit und globale Reichweite von Teams unterstützt wird.

> [!div class="nextstepaction"]
> [Erste Schritte](teams-live-share-quick-start.md)

Live Share enthält eine `TeamsFluidClient` Klasse zum Herstellen einer Verbindung mit einem speziellen Fluid-Container, der jeder Besprechung in einigen Codezeilen zugeordnet ist. Zusätzlich zu den von Fluid Framework bereitgestellten Datenstrukturen unterstützt Live Share auch einen neuen Satz von DDS-Klassen (Distributed Data Structure), um das Erstellen von Anwendungen für gängige Besprechungsszenarien, wie z. B. die Wiedergabe gemeinsam genutzter Medien, zu vereinfachen.

:::image type="content" source="../assets/images/teams-live-share/teams-live-share-contoso-video.gif" alt-text="Live Share Video-Sharing-Erfahrung":::

## <a name="why-build-apps-with-live-share"></a>Warum Apps mit Live Share erstellen?

Das Erstellen von kollaborativen Apps kann schwierig, zeitaufwändig und kostspielig sein und umfasst komplexe Compliance-Anforderungen in großem Maßstab. Benutzer von Teams verbringen viel Zeit damit, die Arbeit mit Teamkollegen zu überprüfen, gemeinsam Videos anzusehen und neue Ideen durch Bildschirmfreigabe zu sammeln. Mit dem Live Share SDK können Sie Ihre App mit minimalen Investitionen in etwas kollaborativeres verwandeln.

Hier sind einige der wichtigsten Vorteile des Live Share SDK:

- Problemloses Sitzungsmanagement und Sicherheit
- Zustandsbehaftete und zustandslose verteilte Datenstrukturen
- Medienerweiterungen zum einfachen Synchronisieren von Video und Audio
- Besprechungsberechtigungen mithilfe der Rollenüberprüfung respektieren
- Kostenloser und vollständig verwalteter Dienst mit geringer Latenz
- Intelligentes Audio-Ducking

:::image type="content" source="../assets/images/teams-live-share/Teams-live-share-schematics.png" alt-text="Teams Live Share":::

Um zu verstehen, ob Live Share für Ihr Szenario für die Zusammenarbeit geeignet ist, ist es hilfreich, die Unterschiede zwischen Live Share und anderen Frameworks für die Zusammenarbeit zu verstehen, einschließlich:

- [Websockets](#web-sockets)
- [Azure Fluid Relay](#azure-fluid-relay)
- [Live-Freigabe](#live-share-hosted-service)

### <a name="web-sockets"></a>Websockets

Websockets sind eine allgegenwärtige Technologie für die Kommunikation in Echtzeit im Web, und einige Apps bevorzugen möglicherweise ein eigenes benutzerdefiniertes Websocket-Back-End. Im Gegensatz zu REST-APIs behalten Websockets eine offene Verbindung zwischen einem Server und Clients in einer Sitzung bei.

Wie andere benutzerdefinierte API-Dienste umfassen die Anforderungen in der Regel Authentifizierungssitzungen, regionale Zuordnung, Wartung und Skalierung. Viele Szenarien für die Zusammenarbeit erfordern auch die Aufrechterhaltung des Sitzungszustands auf dem Server, was Speicherinfrastruktur, Konfliktauflösungen und vieles mehr erfordert.

### <a name="azure-fluid-relay"></a>Azure Fluid Relay

[Azure Fluid Relay](/azure/azure-fluid-relay/) ist ein verwaltetes Angebot für das Fluid Framework, das Entwicklern hilft, Zusammenarbeitserfahrungen in Echtzeit zu erstellen und den Zustand über verbundene JavaScript-Clients hinweg zu replizieren. Microsoft Whiteboard, Loop und OneNote sind beispiele für Apps, die heute mit Fluid Framework erstellt wurden.

Wie andere Azure-Dienste ist Azure Fluid Relay so konzipiert, dass es auf Ihre individuellen Projektanforderungen mit minimaler Komplexität zugeschnitten ist. Die Anforderungen umfassen die Entwicklung einer Authentifizierungsgeschichte für Ihre Fluid-Container und die regionale Compliance. Nach der Konfiguration können sich Entwickler auf die Bereitstellung qualitativ hochwertiger Erfahrungen für die Zusammenarbeit konzentrieren.

### <a name="live-share-hosted-service"></a>Gehosteter Live-Freigabedienst

Live Share bietet einen schlüsselfertigen Azure Fluid Relay-Dienst, der von der Sicherheit von Microsoft Teams-Besprechungen unterstützt wird. Live-Freigabecontainer sind auf Besprechungsteilnehmer beschränkt, behalten die Anforderungen an die Mandantenresidenz bei und können in einigen Zeilen Clientcode aufgerufen werden.

# <a name="javascript"></a>[JavaScript](#tab/javascript)

```javascript
import { TeamsFluidClient, EphemeralPresence } from "@microsoft/live-share";

// Join the Fluid container
const client = new TeamsFluidClient();
const schema = {
  initialObjects: { presence: EphemeralPresence },
};
const { container } = await client.joinContainer(schema);

// ... ready to start app sync logic
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```TypeScript
import { TeamsFluidClient, EphemeralPresence } from "@microsoft/live-share";
import { ContainerSchema } from "fluid-framework";

// Join the Fluid container
const client = new TeamsFluidClient();
const schema: ContainerSchema = {
  initialObjects: { presence: EphemeralPresence },
};
const { container } = await client.joinContainer(schema);

// ... ready to start app sync logic
```

---

> [!IMPORTANT]
> Auf alle Daten, die über den gehosteten Azure Fluid Relay-Dienst des Live Share SDK gesendet oder gespeichert werden, kann bis zu 24 Stunden zugegriffen werden. Weitere Informationen finden Sie unter [Häufig gestellte Fragen zu Live Share](teams-live-share-faq.md).

#### <a name="using-a-custom-azure-fluid-relay-service"></a>Verwenden eines benutzerdefinierten Azure Fluid Relay-Diensts

Während es den meisten von Ihnen vorzuziehen ist, unseren kostenlosen gehosteten Dienst zu verwenden, gibt es immer noch Situationen, in denen es von Vorteil ist, Ihren eigenen Azure Fluid Relay-Dienst für Ihre Live Share-App zu verwenden.

Erwägen Sie die Verwendung eines benutzerdefinierten Diensts, wenn Sie:

- Speicherung von Daten in Fluid-Containern über die Lebensdauer einer Besprechung hinaus erforderlich.
- Übertragen vertraulicher Daten über den Dienst, der eine benutzerdefinierte Sicherheitsrichtlinie erfordert.
- Entwickeln Sie Features beispielsweise `SharedMap`über Fluid Framework für Ihre Anwendung außerhalb von Teams.

Weitere Informationen finden Sie im benutzerdefinierten Leitfaden zum Azure Fluid [Relay-Dienst](./teams-live-share-how-to/how-to-custom-azure-fluid-relay.md).

## <a name="user-scenarios"></a>Benutzerszenarien

| Szenario                                                                                | Beispiel                                                                                                                                                                                            |
| :-------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Während einer Marketingbewertung möchte ein Benutzer Feedback zu seiner neuesten Videobearbeitung sammeln. | Der Benutzer teilt das Video in der Besprechungsphase und startet das Video. Bei Bedarf hält der Benutzer das Video an, um die Szene zu besprechen, und die Teilnehmer zeichnen über Teile des Bildschirms, um wichtige Punkte hervorzuheben. |
| Ein Projektmanager spielt agiles Poker mit ihrem Team während der Planung.                    | Der Manager teilt eine Agile Poker-App für die Besprechungsphase, die es ermöglicht, das Planungsspiel zu spielen, bis das Team konsensfähig ist.                                                                        |
| Ein Finanzberater überprüft PDF-Dokumente mit Kunden vor der Unterzeichnung.                  | Der Finanzberater teilt den PDF-Vertrag mit der Besprechungsphase. Alle Teilnehmer können sich gegenseitig Cursor und hervorgehobenen Text in der PDF-Datei sehen, nach dem beide Parteien die Vereinbarung unterzeichnen.        |

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erste Schritte](teams-live-share-quick-start.md)

## <a name="see-also"></a>Siehe auch

- [GitHub-Repository](https://github.com/microsoft/live-share-sdk)
- [Live Share SDK-Referenzdokumente](/javascript/api/@microsoft/live-share/)
- [Referenzdokumentation zum Live Share Media SDK](/javascript/api/@microsoft/live-share-media/)
- [Live Share-Funktionen](teams-live-share-capabilities.md)
- [Live Share-Medienfunktionen](teams-live-share-media-capabilities.md)
- [Live Share – FAQ](teams-live-share-faq.md)
- [Teams-Apps in Besprechungen](teams-apps-in-meetings.md)
