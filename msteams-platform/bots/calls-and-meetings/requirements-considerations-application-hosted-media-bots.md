---
title: Anforderungen und Überlegungen für von der Anwendung gehostete Medienbots
description: Wichtige Anforderungen und Überlegungen im Zusammenhang mit dem Erstellen von von Anwendungen gehosteten Medienbots für Microsoft Teams.
ms.topic: conceptual
localization_priority: Normal
keywords: von der Anwendung gehostete Medien windows server azure vm
ms.date: 11/16/2018
ms.openlocfilehash: 731cc53573d5c2b65eaed36d75793901fde86e54
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020056"
---
# <a name="requirements-and-considerations-for-application-hosted-media-bots"></a>Anforderungen und Überlegungen für von der Anwendung gehostete Medienbots

Für einen anwendungsgehostten Medienbot muss [ `Microsoft.Graph.Communications.Calls.Media` die .NET-Bibliothek](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/) auf die Audio- und Videomedienstreams zugreifen. Der Bot muss auf einem Servercomputer oder Windows server oder Windows Server Guest Operating System (OS) in Azure bereitgestellt werden.

> [!NOTE]
> * Die Anleitungen für die Entwicklung von Messaging- und Interactive Voice Response (IVR)-Bots gelten nicht vollständig für das Erstellen von von Anwendungen gehosteten Medienbots.
> * Da sich die Microsoft Real-time Media Platform für Bots in der Entwicklervorschau befindet, können die Anleitungen in diesem Dokument geändert werden.

## <a name="c-or-net-and-windows-server-for-development"></a>C# oder .NET und Windows Server für die Entwicklung

Für einen in der Anwendung gehosteten Medienbot ist Folgendes erforderlich:

- Der Bot muss in der C# und der Standard-.NET Framework entwickelt und in Microsoft Azure. Sie können C++ oder Node.js-APIs nicht verwenden, um auf Echtzeitmedien zu zugreifen, und .NET Core wird für einen in der Anwendung gehosteten Medienbot nicht unterstützt.

- Der Bot kann in einer der folgenden Azure-Dienstumgebungen gehostet werden:
    - CloudDienst.
    - Service Fabric mit VmSS (Virtual Machine Scale Sets)
    - Infrastructure as a Service (IaaS) Virtual Machine (VM).  
  
- Der Bot kann nicht als Azure-Web-App bereitgestellt werden.

- Der Bot muss auf einer aktuellen Version der `Microsoft.Graph.Communications.Calls.Media` .NET-Bibliothek ausgeführt werden. Der Bot muss entweder die neueste verfügbare Version des NuGet-Pakets oder eine Version [verwenden,](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/)die nicht länger als drei Monate alt ist. Ältere Versionen der Bibliothek sind veraltet und funktionieren nach einigen Monaten nicht mehr. Die Bibliothek auf dem neuesten Stand zu halten, stellt die beste Interoperabilität zwischen bot und `Microsoft.Graph.Communications.Calls.Media` Microsoft Teams.

Der nächste Abschnitt enthält Details dazu, wo sich Medienanrufe in Echtzeit befinden.

## <a name="real-time-media-calls-stay-where-they-are-created"></a>Echtzeitmedienanrufe bleiben dort, wo sie erstellt werden

Echtzeitmedienanrufe bleiben auf dem Computer, auf dem sie erstellt wurden. Ein Echtzeitmedienanruf wird an die Vm-Instanz angeheftet, die den Anruf angenommen oder gestartet hat. Medien aus einem Microsoft Teams oder Besprechungsflüssen an diese VM-Instanz, und Medien, die der Bot an Microsoft Teams muss ebenfalls von diesem virtuellen Computer stammen. Wenn beim Beenden des virtuellen Computers Echtzeitmedienanrufe ausgeführt werden, werden diese Anrufe abrupt beendet. Wenn der Bot über Vorkenntnisse des ausstehenden Herunterfahrens von virtuellen Computer verfügt, kann er die Aufrufe beenden.

Der nächste Abschnitt enthält Details zur Barrierefreiheit von von Anwendungen gehosteten Medienbots.

## <a name="application-hosted-media-bots-accessible-on-the-internet"></a>Anwendungsgehostte Medienbots, auf die im Internet zugegriffen werden kann

Anwendungsgehostte Medienbots müssen direkt über das Internet zugänglich sein. Diese Bots müssen die folgenden Features enthalten:

- Jede VM-Instanz, die einen von einer Anwendung gehosteten Medienbot in Azure hosten, muss über eine öffentliche IP-Adresse (ILPIP) auf Instanzebene direkt über das Internet zugänglich sein.
    - Informationen zum Abrufen und Konfigurieren eines ILPIP für einen Azure Cloud Service finden Sie unter klassische Übersicht über öffentliche [IP-Adressen auf Instanzebene.](/azure/virtual-network/virtual-networks-instance-level-public-ip)
    - Informationen zum Konfigurieren eines ILPIP für einen VM-Skalierungssatz finden Sie unter [Public IPv4 per virtual machine](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-networking#public-ipv4-per-virtual-machine).
- Der Dienst, der einen von einer Anwendung gehosteten Medienbot hosten soll, muss auch jede VM-Instanz mit einem öffentlich zugänglichen Port konfigurieren, der der jeweiligen Instanz zugeordnet ist.
    - Für einen Azure Cloud Service erfordert dies einen Instanzeingabeendpunkt. Weitere Informationen finden Sie unter [Aktivieren der Kommunikation für Rolleninstanzen in Azure](/azure/cloud-services/cloud-services-enable-communication-role-instances).
    - Für einen VM-Skalierungssatz muss eine NAT-Regel für den Lastenausgleich konfiguriert werden. Weitere Informationen finden Sie unter [virtuelle Netzwerke und virtuelle Computer in Azure](/azure/virtual-machines/windows/network-overview).
- Vom Anwendungshosting gehostete Medienbots werden von der Bot Framework Emulator.

Der nächste Abschnitt enthält Details zu Skalierbarkeits- und Leistungsaspekten von anwendungsgehostten Medienbots.

## <a name="scalability-and-performance-considerations"></a>Überlegungen zu Skalierbarkeit und Leistung

Anwendungsgehostte Medienbots erfordern die folgenden Skalierbarkeits- und Leistungsüberlegungen:

## <a name="code-sample"></a>Codebeispiel

Anwendungsgehostte Medienbots-Beispiele lauten wie folgt:

| **Beispielname** | **Beschreibung** | **Graph** |
|------------|-------------|-----------|
| Beispiel für lokale Medien | Beispiele, die verschiedene lokale Medienszenarien veranschaulichen. | [View](https://github.com/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/V1.0Samples/LocalMediaSamples) |
| Remotemedienbeispiel | Beispiele, die verschiedene Remotemedienszenarien veranschaulichen. | [View](https://github.com/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/V1.0Samples/RemoteMediaSamples) |

## <a name="see-also"></a>Siehe auch

- [Graph Aufrufen der SDK-Dokumentation](https://microsoftgraph.github.io/microsoft-graph-comms-samples/docs/)
- Die Bots erfordern mehr Rechen- und Netzwerkbandbreite als Messagingbots und verursachen deutlich höhere Betriebskosten. Ein Entwickler eines Medienbots in Echtzeit muss die Skalierbarkeit des Bots sorgfältig messen und sicherstellen, dass der Bot nicht mehr gleichzeitige Anrufe akzeptiert, als er verwalten kann. Ein videofähiger Bot kann nur ein oder zwei gleichzeitige Mediensitzungen pro CPU-Kern unterstützen, wenn die rohen RGB24- oder NV12-Videoformate verwendet werden.
- Die Echtzeitmedienplattform nutzt derzeit keine auf dem virtuellen Computer verfügbaren Grafikverarbeitungseinheiten (Gpu), um die H.264-Videocodierung oder -decodierung zu deaktivieren. Stattdessen erfolgt die Videocodierung und -decodierung in der Software auf der CPU. Wenn eine GPU verfügbar ist, nutzt der Bot sie für ein eigenes Grafikrendering, z. B. wenn der Bot ein 3D-Grafikmodul verwendet.
- Die VM-Instanz, die den Echtzeitmedienbot hosten, muss über mindestens 2 CPU-Kerne verfügen. Für Azure wird ein virtueller Computer der Dv2-Reihe empfohlen. Für andere Azure VM-Typen ist ein System mit 4 virtuellen CPUs (vCPU) die erforderliche Mindestgröße. Weitere Informationen zu Azure VM-Typen finden Sie in [der Azure-Dokumentation](/azure/virtual-machines/windows/sizes-general).

Der nächste Abschnitt enthält Beispiele, die verschiedene lokale Medienszenarien veranschaulichen.

## <a name="samples-and-additional-resources"></a>Beispiele und zusätzliche Ressourcen

- [Beispielanwendungen](https://github.com/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/V1.0Samples/LocalMediaSamples)
- [Graph aufrufende SDK-Dokumentation](https://microsoftgraph.github.io/microsoft-graph-comms-samples/docs/)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Unterstützte Medienformate](~/resources/media-formats.md)
