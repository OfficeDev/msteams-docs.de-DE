---
title: Live Share Übersicht
author: surbhigupta
description: In diesem Modul erfahren Sie, was das Microsoft Live Share SDK und seine Benutzerszenarien sind.
ms.topic: overview
ms.localizationpriority: high
ms.author: v-ypalikila
ms.date: 04/07/2022
ms.openlocfilehash: c242faa57809bb967a29b7ab224e6cc0e859247b
ms.sourcegitcommit: 1248901a5e59db67bae091f60710aabe7562016a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2022
ms.locfileid: "68560554"
---
---

# <a name="live-share-sdk"></a>Live Share SDK

> [!VIDEO https://www.youtube.com/embed/971YIvosuUk]

Live Share ist ein SDK, das entwickelt wurde, um Teams-Apps in kollaborative Mehrbenutzererlebnisse umzuwandeln, ohne einen dedizierten Back-End-Code schreiben zu müssen. Mit Live Share können Ihre Benutzer während Besprechungen gemeinsam Besprechungen ansehen, gemeinsam erstellen und gemeinsam bearbeiten.

Manchmal reicht die Bildschirmfreigabe einfach nicht aus, weshalb Microsoft Tools wie PowerPoint Live und Whiteboard direkt in Teams erstellt hat. Indem Sie Ihre Webanwendung direkt in den Mittelpunkt der Besprechungsoberfläche stellen, können Ihre Benutzer während Besprechungen und Anrufen nahtlos zusammenarbeiten.

> [!div class="nextstepaction"]
> [Erste Schritte](teams-live-share-quick-start.md)

## <a name="feature-overview"></a>Featureübersicht

Live Share verfügt über drei Pakete, die unbegrenzte Szenarien für die Zusammenarbeit unterstützen. Diese Pakete machen eine Reihe verteilter Datenstrukturen (Distributed Data Structures, DDS) verfügbar, einschließlich primitiver Bausteine und schlüsselfertiger Szenarien.

Live Share integriert Besprechungen nahtlos in [Fluid Framework](https://fluidframework.com/). Fluid Framework ist eine Sammlung von Client-Bibliotheken zum Verteilen und Synchronisieren von freigegeben Status. Live Share bietet ein kostenloses, vollständig verwaltetes und einsatzbereites [Azure Fluid Relay](/azure/azure-fluid-relay/), das durch die Sicherheit und globale Reichweite von Teams unterstützt wird.

### <a name="live-share-core"></a>Live Share Core

Live Share ermöglicht die Verbindung mit einem speziellen FluidContainer, der jeder Besprechung in einigen Codezeilen zugeordnet ist. Zusätzlich zu den von Fluid Framework bereitgestellten Datenstrukturen unterstützt Live Share auch einen neuen Satz von DDS-Klassen, um die Synchronisierung des App-Zustands in Besprechungen zu vereinfachen.

Zu den vom Live Share-Kernpaket unterstützten Features gehören:

- Nehmen Sie an der Live-Freigabesitzung einer Besprechung mit teil `LiveShareClient`.
- Nachverfolgen der Anwesenheit von Besprechungen und Synchronisieren von Benutzermetadaten mit `LivePresence`.
- Senden Von Echtzeitereignissen an andere Clients in der Sitzung mit `LiveEvent`.
- Koordinieren Sie den App-Zustand, der verschwindet, wenn Benutzer die Sitzung mit `LiveState`verlassen.
- Synchronisieren eines Countdown-Timers mit `LiveTimer`.
- Nutzen Sie alle Funktionen von Fluid Framework, z `SharedMap` . B. und `SharedString`.

Weitere Informationen zu diesem Paket finden Sie auf der [Seite "Kernfunktionen"](./teams-live-share-capabilities.md).

### <a name="live-share-media"></a>Live Teilen von Medien

:::image type="content" source="../assets/images/teams-live-share/teams-live-share-contoso-video.gif" alt-text="Screenshot zeigt ein Beispiel für die Videofreigabe in Live Share.":::

Video und Audio sind wichtige Bestandteile der modernen Welt und des Arbeitsplatzes. Live Share Media ermöglicht **die Mediensynchronisierung** für jeden Media Player mit nur wenigen Codezeilen. Durch die Synchronisierung von Medien auf der Ebene der Zustands- und Transportsteuerelemente des Players können Sie Ansichten einzeln zuordnen und gleichzeitig die höchstmögliche Qualität bereitstellen, die über Ihre App verfügbar ist. Da Microsoft Ihre Medieninhalte nicht erneut aktualisiert, bleiben Ihre Lizenzierungs- und Zugriffsanforderungen erhalten.

Zu den von Live Share-Medien unterstützten Features gehören:

- Synchronisieren des Media Player-Zustands und Nachverfolgen mit `MediaPlayerSynchronizer`.
- Intelligente Anpassungen der Medienlautstärke, wenn Benutzer während der Besprechung sprechen.
- Begrenzen Sie, welche Benutzer den Spielerstatus ändern können.
- Anhalten und Fortsetzen der Mediensynchronisierung im Flug oder an geplanten Wartepunkten.

Weitere Informationen zu diesem Paket finden Sie auf der [Live Share-Medienseite](./teams-live-share-media-capabilities.md).

> [!NOTE]
> Live-Freigaben übertragen keine Medieninhalte erneut. Es wurde für die Verwendung mit eingebetteten Webplayern wie HTML5 `<video>` oder Azure Media Player entwickelt.

### <a name="live-share-canvas"></a>Live-Freigabe-Canvas

:::image type="content" source="../assets/images/teams-live-share/Teams-live-share-schematics.png" alt-text="Screenshots zeigen ein Beispiel für mehrere Benutzer, die während einer Besprechung auf einem Zeichenbereich zeichnen.":::

Bei der Zusammenarbeit in Besprechungen ist es wichtig, dass Benutzer auf Inhalte auf dem Bildschirm hinweisen und diese hervorheben können. Live Share Canvas erleichtert das Hinzufügen von Freihandeingaben, Laserpointern und Cursorn zu Ihrer App für eine nahtlose Zusammenarbeit.

Zu den von der Live-Freigabe-Canvas unterstützten Features gehören:

- Fügen Sie Ihrer App eine Zusammenarbeit `<canvas>` mit `LiveCanvas`hinzu.
- Vermitteln Sie Ideen mithilfe der Stift-, Textmarker-, Linien- und Pfeiltools.
- Präsentieren Sie effektiv mit dem Laserpointer.
- Folgen Sie den Mauscursorn in Echtzeit.
- Konfigurieren sie Einstellungen für variable Geräte und Ansichtszustände.
- Verwenden Sie vollständig unterstützte Maus-, Touch- und Eingabestifteingaben.

Weitere Informationen zu diesem Paket finden Sie auf der [Canvasseite "Live-Freigabe"](./teams-live-share-canvas.md).

## <a name="why-build-apps-with-live-share"></a>Warum Apps mit Live Share erstellen?

Das Erstellen von kollaborativen Apps kann schwierig, zeitaufwändig und kostspielig sein und umfasst komplexe Compliance-Anforderungen in großem Maßstab. Benutzer von Teams verbringen viel Zeit damit, die Arbeit mit Teamkollegen zu überprüfen, gemeinsam Videos anzusehen und neue Ideen durch Bildschirmfreigabe zu sammeln. Mit dem Live Share SDK können Sie Ihre App mit minimalen Investitionen in etwas kollaborativeres verwandeln.

Hier sind einige der wichtigsten Vorteile des Live Share SDK:

- Problemloses Sitzungsmanagement und Sicherheit
- Zustandsbehaftete und zustandslose verteilte Datenstrukturen
- Medienerweiterungen zum einfachen Synchronisieren von Video und Audio
- Freihandeingabe mit Drehtaste, Laserpointer und Cursor.
- Besprechungsberechtigungen mithilfe der Rollenüberprüfung respektieren
- Kostenloser und vollständig verwalteter Dienst mit geringer Latenz

Um zu verstehen, ob Live Share für Ihr Szenario für die Zusammenarbeit geeignet ist, ist es hilfreich, die Unterschiede zwischen Live Share und anderen Frameworks für die Zusammenarbeit zu verstehen, einschließlich:

- [Websockets](#web-sockets)
- [Azure Fluid Relay](#azure-fluid-relay)
- [Live-Freigabe](#live-share-hosted-service)

### <a name="web-sockets"></a>Websockets

Websockets sind eine allgegenwärtige Technologie für die Kommunikation in Echtzeit im Web, und einige Apps bevorzugen möglicherweise ein eigenes benutzerdefiniertes Websocket-Back-End. Im Gegensatz zu REST-APIs behalten Websockets eine offene Verbindung zwischen einem Server und Clients in einer Sitzung bei.

Wie andere benutzerdefinierte API-Dienste umfassen die Anforderungen in der Regel Authentifizierungssitzungen, regionale Zuordnung, Wartung und Skalierung. Viele Szenarien für die Zusammenarbeit erfordern auch die Aufrechterhaltung des Sitzungszustands auf dem Server, was Speicherinfrastruktur, Konfliktauflösungen und vieles mehr erfordert.

Durch die Verwendung von Live Share erhalten Sie die gesamte Leistungsfähigkeit von Websockets ohne den Aufwand.

### <a name="azure-fluid-relay"></a>Azure Fluid Relay

[Azure Fluid Relay](/azure/azure-fluid-relay/) ist ein verwaltetes Angebot für das Fluid Framework, das Entwicklern hilft, Zusammenarbeitserfahrungen in Echtzeit zu erstellen und den Zustand über verbundene JavaScript-Clients hinweg zu replizieren. Microsoft Whiteboard, Loop und OneNote sind beispiele für Apps, die heute mit Fluid Framework erstellt wurden.

Wie andere Azure-Dienste ist Azure Fluid Relay so konzipiert, dass es auf Ihre individuellen Projektanforderungen mit minimaler Komplexität zugeschnitten ist. Die Anforderungen umfassen die Entwicklung einer Authentifizierungsgeschichte für Ihre Fluid-Container und die regionale Compliance. Nach der Konfiguration können sich Entwickler auf die Bereitstellung qualitativ hochwertiger Erfahrungen für die Zusammenarbeit konzentrieren.

### <a name="live-share-hosted-service"></a>Gehosteter Live-Freigabedienst

Live Share bietet einen schlüsselfertigen Azure Fluid Relay-Dienst, der von der Sicherheit von Microsoft Teams-Besprechungen unterstützt wird. Live-Freigabecontainer sind auf Besprechungsteilnehmer beschränkt, behalten die Anforderungen an die Mandantenresidenz bei und können in einigen Zeilen Clientcode aufgerufen werden.

# <a name="javascript"></a>[JavaScript](#tab/javascript)

```javascript
import { LiveShareClient, LivePresence } from "@microsoft/live-share";

// Join the Fluid container
const liveShare = new LiveShareClient();
const schema = {
  initialObjects: { presence: LivePresence },
};
const { container } = await liveShare.joinContainer(schema);

// ... ready to start app sync logic
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```TypeScript
import { LiveShareClient, LivePresence } from "@microsoft/live-share";
import { ContainerSchema } from "fluid-framework";

// Join the Fluid container
const liveShare = new LiveShareClient();
const schema: ContainerSchema = {
  initialObjects: { presence: LivePresence },
};
const { container } = await liveShare.joinContainer(schema);

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
| Ein Finanzberater überprüft PDF-Dokumente mit Kunden vor der Unterzeichnung.                  | Der Finanzberater teilt den PDF-Vertrag mit der Besprechungsphase. Alle Teilnehmer können die Cursor und den hervorgehobenen Text in der PDF-Datei sehen, nachdem beide Parteien die Vereinbarung unterzeichnet haben.        |

> [!IMPORTANT]
> Live Share ist unter der [Microsoft Live Share SDK-Lizenz](https://github.com/microsoft/live-share-sdk/blob/main/LICENSE) lizenziert. Um diese Funktionen in Ihrer App nutzen zu können, müssen Sie diese Bedingungen zuerst lesen und akzeptieren.

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
