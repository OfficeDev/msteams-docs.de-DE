---
title: Anforderungen und Überlegungen für anwendungsgehostete Medienbots
description: Lernen Sie wichtige Anforderungen und Überlegungen sowie Skalierbarkeits- und Leistungsaspekte im Zusammenhang mit der Erstellung von in der Anwendung gehosteten Medienbots für Teams
ms.topic: conceptual
ms.localizationpriority: medium
ms.date: 11/16/2018
ms.openlocfilehash: 87cdbce71189f64c0d34fc0cddb5211355017007
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66142486"
---
# <a name="requirements-and-considerations-for-application-hosted-media-bots"></a>Anforderungen und Überlegungen für anwendungsgehostete Medienbots

Für einen in der Anwendung gehosteten Medienbot ist die [`Microsoft.Graph.Communications.Calls.Media` .NET-Bibliothek](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/) erforderlich, um auf die Audio- und Videomedienstreams zuzugreifen. Der Bot muss auf einem Windows Server auf einem lokalen Computer oder einem Windows Server-Gastbetriebssystem in Azure bereitgestellt werden.

> [!NOTE]
>
> * Die Anleitung zum Entwickeln von Bots für Nachrichten und interaktive Sprachantworten (Interactive Voice Response, IVR) gilt nicht vollumfänglich für das Erstellen von durch Anwendungen gehosteten Medienbots.
> * Da sich die Microsoft Real-time Media Platform für Bots in der Entwicklervorschau befindet, können sich die Anleitungen in diesem Dokument ändern.

## <a name="c-or-net-and-windows-server-for-development"></a>C# oder .NET und Windows Server für die Entwicklung

Ein von der Anwendung gehosteter Medienbot erfordert Folgendes:

* Der Bot muss in C# und dem standardmäßigen .NET Framework entwickelt und in Microsoft Azure bereitgestellt werden. Sie können C++- oder Node.js-APIs nicht verwenden, um auf Echtzeitmedien zuzugreifen, und .NET Core wird für einen von einer Anwendung gehosteten Medienbot nicht unterstützt.

* Der Bot kann in einer der folgenden Azure-Dienstumgebungen gehostet werden:
  * Cloud-Dienst.
  * Service Fabric mit Virtual Machine Scale Sets (VMSS).
  * Infrastructure as a Service (IaaS) Virtuelle Maschine (VM).  
  
* Der Bot kann nicht als Azure-Webapp bereitgestellt werden.

* Der Bot muss auf einer aktuellen Version der `Microsoft.Graph.Communications.Calls.Media`.NET-Bibliothek ausgeführt werden. Der Bot muss entweder die neueste verfügbare Version des [NuGet-Pakets](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/) verwenden, oder eine Version, die nicht älter als drei Monate ist. Ältere Versionen der Bibliothek sind veraltet und funktionieren nach einigen Monaten nicht mehr. Die Aktualisierung der `Microsoft.Graph.Communications.Calls.Media` Bibliothek stellt die beste Interoperabilität zwischen dem Bot und Microsoft Teams sicher.

Der nächste Abschnitt enthält Einzelheiten darüber, wo sich Echtzeit-Medienaufrufe befinden.

## <a name="real-time-media-calls-stay-where-theyre-created"></a>Medienanrufe in Echtzeit bleiben dort, wo sie erstellt werden

Echtzeit-Medienanrufe bleiben auf dem Computer, auf dem sie erstellt wurden. Ein Echtzeit-Medienanruf wird an die Instanz der virtuellen Maschine (VM) angeheftet, die den Anruf angenommen oder gestartet hat. Medien von einem Microsoft Teams-Anruf oder -Meeting fließen zu dieser VM-Instanz, und Medien, die der Bot an Microsoft Teams zurücksendet, müssen ebenfalls von dieser VM stammen. Wenn beim Stoppen der VM Echtzeit-Medienaufrufe ausgeführt werden, werden diese Aufrufe abrupt beendet. Wenn der Bot Vorkenntnisse über das bevorstehende Herunterfahren der VM hat, kann er die Anrufe beenden.

Der nächste Abschnitt enthält Details zur Zugänglichkeit von anwendungsgehosteten Medien-Bots.

## <a name="application-hosted-media-bots-accessible-on-the-internet"></a>Anwendungsgehostete Medien-Bots, auf die über das Internet zugegriffen werden kann

Von der Anwendung gehostete Medien-Bots müssen direkt im Internet zugänglich sein. Diese Bots müssen die folgenden Funktionen enthalten:

* Auf jede VM-Instanz, die einen von der Anwendung gehosteten Medienbot in Azure hostet, muss direkt über das Internet mit einer öffentlichen IP-Adresse (ILPIP) auf Instanzebene zugegriffen werden können.
  * Informationen zum Abrufen und Konfigurieren eines ILPIP für einen Azure Cloud-Dienst finden Sie unter Klassische [Übersicht über öffentliche IP-Adressen auf Instanzebene](/azure/virtual-network/virtual-networks-instance-level-public-ip).
  * Informationen zum Konfigurieren eines ILPIP für eine VM-Skalierungsgruppe finden Sie unter [öffentliches IPv4 pro virtuellem Computer](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-networking#public-ipv4-per-virtual-machine).
* Der Dienst, der einen von einer Anwendung gehosteten Medienbot hostet, muss außerdem jede VM-Instanz mit einem öffentlich zugänglichen Port konfigurieren, welcher der jeweiligen Instanz zugeordnet ist.
  * Für einen Azure Cloud Service erfordert dies einen Instanzeingabeendpunkt. Weitere Informationen [finden Sie unter Aktivieren der Kommunikation für Rolleninstanzen in Azure](/azure/cloud-services/cloud-services-enable-communication-role-instances).
  * Für eine VM-Skalierungsgruppe muss eine NAT-Regel auf dem Load Balancer konfiguriert werden. Weitere Informationen finden Sie unter [virtuelle Netzwerke und virtuelle Computer in Azure](/azure/virtual-machines/windows/network-overview).

* Von einer Anwendung gehostete Medienbots werden vom Botframework-Emulator nicht unterstützt.

Der nächste Abschnitt enthält Details zu Skalierbarkeits- und Leistungsüberlegungen von anwendungsgehosteten Medien-Bots.

## <a name="scalability-and-performance-considerations"></a>Überlegungen zu Skalierbarkeit und Leistung

Die von der Anwendung gehosteten Medien-Bots erfordern die folgenden Skalierbarkeits- und Leistungsüberlegungen:

* Anwendungsgehostete Medienbots erfordern mehr Rechen- und Netzwerkkapazität (Bandbreite) als Messaging-Bots und können höhere Betriebskosten verursachen. Ein Echtzeit-Media-Bot-Entwickler muss die Skalierbarkeit des Bots sorgfältig messen und sicherstellen, dass der Bot nicht mehr gleichzeitige Anrufe akzeptiert, als er bewältigen kann. Ein videofähiger Bot kann möglicherweise nur eine oder zwei gleichzeitige Mediensitzungen pro CPU-Kern aufrechterhalten (bei Verwendung der „rohen“ RGB24- oder NV12-Videoformate).
* Die Real-Time Media Platform nutzt derzeit keine auf der VM verfügbaren Graphics Processing Units (GPU), um H.264-Videokodierung/-dekodierung auszulagern. Stattdessen werden Videocodierung und -decodierung in Software auf der CPU durchgeführt. Wenn eine GPU verfügbar ist, kann der Bot diese zum Beispiel für sein eigenes Grafik-Rendering nutzen, wenn der Bot eine 3D-Grafik-Engine verwendet.
* Die VM-Instanz, die den Echtzeit-Medienbot hostet, muss mindestens 2 CPU-Kerne haben. Für Azure wird ein virtueller Computer der Dv2-Serie empfohlen. Für andere Azure-VM-Typen ist ein System mit vier virtuellen CPUs (vCPU) die erforderliche Mindestgröße. Ausführliche Informationen zu Azure-VM-Typen finden Sie in der [Azure-Dokumentation](/azure/virtual-machines/windows/sizes-general).

## <a name="code-sample"></a>Codebeispiel

Beispiele für von der Anwendung gehostete Medien-Bots lauten wie folgt:

| **Beispielname** | **Beschreibung** | **Graph** |
|------------|-------------|-----------|
| Lokale Medienprobe | Beispiel, das verschiedene lokale Medienszenarien veranschaulicht. | [Anzeigen](https://github.com/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/V1.0Samples/LocalMediaSamples) |
| Remote-Medienbeispiel | Beispiel, das verschiedene Remotemedienszenarien veranschaulicht. | [Anzeigen](https://github.com/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/V1.0Samples/RemoteMediaSamples) |

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Unterstützte Medienformate](~/resources/media-formats.md)

## <a name="see-also"></a>Siehe auch

* [Graph Calling SDK-Dokumentation](https://microsoftgraph.github.io/microsoft-graph-comms-samples/docs/)
* Die Bots benötigen mehr Rechen- und Netzwerkbandbreitenkapazität als Messaging-Bots und verursachen höhere Betriebskosten. Ein Echtzeit-Media-Bot-Entwickler muss die Skalierbarkeit des Bots sorgfältig messen und sicherstellen, dass der Bot nicht mehr gleichzeitige Anrufe akzeptiert, als er bewältigen kann. Ein videofähiger Bot kann nur eine oder zwei gleichzeitige Mediensitzungen pro CPU-Kern aufrechterhalten, wenn er die rohen RGB24- oder NV12-Videoformate verwendet.
* Die Echtzeitmedienplattform nutzt derzeit keine Grafikverarbeitungseinheiten (GRAPHICS Processing Units, GPU), die auf dem virtuellen Computer verfügbar sind, um die H.264-Videocodierung oder Decodierung zu deaktivieren. Stattdessen werden Videocodierung und -decodierung in Software auf der CPU durchgeführt. Wenn eine GPU verfügbar ist, nutzt der Bot diese für sein eigenes Grafik-Rendering, beispielsweise wenn der Bot eine 3D-Grafik-Engine verwendet.
* Die VM-Instanz, die den Echtzeit-Medienbot hostet, muss mindestens 2 CPU-Kerne haben. Für Azure wird ein virtueller Computer der Dv2-Serie empfohlen. Für andere Azure-VM-Typen ist ein System mit 4 virtuellen CPUs (vCPU) die erforderliche Mindestgröße. Weitere Informationen zu Azure-VM-Typen finden Sie in der [Azure-Dokumentation](/azure/virtual-machines/windows/sizes-general).

Der nächste Abschnitt enthält Beispiele, die verschiedene lokale Medienszenarien veranschaulichen.

## <a name="samples-and-additional-resources"></a>Beispiele und zusätzliche Ressourcen

* [Anwendungsbeispiele](https://github.com/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/V1.0Samples/LocalMediaSamples)
* [Graph Calling SDK-dokumentation](https://microsoftgraph.github.io/microsoft-graph-comms-samples/docs/)
