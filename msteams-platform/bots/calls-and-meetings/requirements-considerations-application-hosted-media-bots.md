---
title: Anforderungen und Überlegungen für von der Anwendung gehostete Medienbots
description: Grundlegendes zu wichtigen Anforderungen und Überlegungen sowie Überlegungen zur Skalierbarkeit und Leistung im Zusammenhang mit dem Erstellen von in der Anwendung gehosteten Medienbots für Microsoft Teams mithilfe von Codebeispielen und Beispielen.
ms.topic: conceptual
ms.localizationpriority: medium
keywords: Von der Anwendung gehostete Medien-Windows Server-Azure-VM
ms.date: 11/16/2018
ms.openlocfilehash: 0597e99b1933270ee4ee85d1adc18378da3c3114
ms.sourcegitcommit: af1d0a4041ce215e7863ac12c71b6f1fa3e3ba81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2021
ms.locfileid: "60887413"
---
# <a name="requirements-and-considerations-for-application-hosted-media-bots"></a>Anforderungen und Überlegungen für von der Anwendung gehostete Medienbots

Ein von der Anwendung gehosteter Medienbot benötigt die [ `Microsoft.Graph.Communications.Calls.Media` .NET-Bibliothek,](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/) um auf die Audio- und Videomediendatenströme zuzugreifen. Der Bot muss auf einem Windows Servercomputer oder Windows Gastbetriebssystem (BS) in Azure bereitgestellt werden.

> [!NOTE]
> * Die Anleitungen für die Entwicklung von Messaging- und Interactive Voice Response (IVR)-Bots gelten nicht vollständig für das Erstellen von in der Anwendung gehosteten Medienbots.
> * Da sich die Microsoft Real-Time Media Platform für Bots in der Entwicklervorschau befindet, können sich die Anleitungen in diesem Dokument ändern.

## <a name="c-or-net-and-windows-server-for-development"></a>C# oder .NET und Windows Server für die Entwicklung

Ein von der Anwendung gehosteter Medienbot erfordert Folgendes:

- Der Bot muss in C# und dem Standard-.NET Framework entwickelt und in Microsoft Azure bereitgestellt werden. Sie können C++ oder Node.js-APIs nicht für den Zugriff auf Echtzeitmedien verwenden, und .NET Core wird für einen von der Anwendung gehosteten Medienbot nicht unterstützt.

- Der Bot kann in einer der folgenden Azure-Dienstumgebungen gehostet werden:
    - Cloud-Dienst.
    - Service Fabric mit VMSS (Virtual Machine Scale Sets).
    - Virtueller Computer (Infrastructure as a Service, IaaS)  
  
- Der Bot kann nicht als Azure-Web-App bereitgestellt werden.

- Der Bot muss in einer aktuellen Version der `Microsoft.Graph.Communications.Calls.Media` .NET-Bibliothek ausgeführt werden. Der Bot muss entweder die neueste verfügbare Version des [NuGet-Pakets](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/)oder eine Version verwenden, die nicht mehr als drei Monate alt ist. Ältere Versionen der Bibliothek sind veraltet und funktionieren nach einigen Monaten nicht mehr. Wenn Sie die `Microsoft.Graph.Communications.Calls.Media` Bibliothek auf dem neuesten Stand halten, wird die beste Interoperabilität zwischen dem Bot und Microsoft Teams sichergestellt.

Der nächste Abschnitt enthält Details dazu, wo sich Medienanrufe in Echtzeit befinden.

## <a name="real-time-media-calls-stay-where-they-are-created"></a>Medienanrufe in Echtzeit bleiben dort, wo sie erstellt werden

Echtzeit-Medienanrufe bleiben auf dem Computer, auf dem sie erstellt wurden. Ein Echtzeit-Medienanruf wird an die VM-Instanz (Virtual Machine) angeheftet, die den Anruf angenommen oder gestartet hat. Medien aus einem Microsoft Teams Anruf oder einer Besprechung fließen zu dieser VM-Instanz, und Medien, die der Bot zurück an Microsoft Teams muss auch von diesem virtuellen Computer stammen. Wenn beim Beenden des virtuellen Computers Medienanrufe in Echtzeit ausgeführt werden, werden diese Aufrufe abrupt beendet. Wenn der Bot über vor dem Herunterfahren des virtuellen Computers verfügt, kann er die Aufrufe beenden.

Der nächste Abschnitt enthält Details zur Barrierefreiheit von in der Anwendung gehosteten Medienbots.

## <a name="application-hosted-media-bots-accessible-on-the-internet"></a>Anwendungsgehostete Medienbots, auf die im Internet zugegriffen werden kann

Von der Anwendung gehostete Medienbots müssen direkt im Internet zugänglich sein. Diese Bots müssen die folgenden Features enthalten:

- Jede VM-Instanz, die einen von der Anwendung gehosteten Medienbot in Azure hostet, muss über eine öffentliche IP-Adresse (ILPIP) auf Instanzebene direkt über das Internet zugänglich sein.
    - Informationen zum Abrufen und Konfigurieren eines ILPIP für einen Azure Cloud Service finden Sie in der [klassischen Übersicht über öffentliche IP-Adressen auf Instanzebene.](/azure/virtual-network/virtual-networks-instance-level-public-ip)
    - Informationen zum Konfigurieren eines ILPIP für eine VM-Skalierungsgruppe finden Sie unter [öffentliches IPv4 pro virtuellem Computer.](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-networking#public-ipv4-per-virtual-machine)
- Der Dienst, der einen von der Anwendung gehosteten Medienbot hostet, muss auch jede VM-Instanz mit einem öffentlich zugänglichen Port konfigurieren, der der jeweiligen Instanz zugeordnet ist.
    - Für einen Azure Cloud Service erfordert dies einen Instanzeingabeendpunkt. Weitere Informationen finden Sie unter Aktivieren der [Kommunikation für Rolleninstanzen in Azure.](/azure/cloud-services/cloud-services-enable-communication-role-instances)
    - Für einen VM-Skalierungssatz muss eine NAT-Regel für den Lastenausgleich konfiguriert werden. Weitere Informationen finden Sie unter [virtuelle Netzwerke und virtuelle Computer in Azure.](/azure/virtual-machines/windows/network-overview)
- Von der Anwendung gehostete Medienbots werden vom Bot Framework Emulator nicht unterstützt.

Der nächste Abschnitt enthält Details zu Skalierbarkeits- und Leistungsaspekten von von der Anwendung gehosteten Medienbots.

## <a name="scalability-and-performance-considerations"></a>Überlegungen zu Skalierbarkeit und Leistung

Die von der Anwendung gehosteten Medienbots erfordern die folgenden Skalierbarkeits- und Leistungsaspekte:
- Anwendungsgehostete Medienbots erfordern mehr Rechen- und Netzwerkkapazität (Bandbreite) als Messaging-Bots und können deutlich höhere Betriebskosten verursachen. Ein Echtzeit-Medienbot-Entwickler muss die Skalierbarkeit des Bots sorgfältig messen und sicherstellen, dass der Bot nicht mehr gleichzeitige Anrufe akzeptiert, als er verwalten kann. Ein videoaktivierter Bot kann möglicherweise nur eine oder zwei gleichzeitige Mediensitzungen pro CPU-Kern unterstützen (bei Verwendung der "unformatierten" RGB24- oder NV12-Videoformate).
- Die Echtzeitmedienplattform nutzt derzeit keine Grafikverarbeitungseinheiten (GPU), die auf dem virtuellen Computer verfügbar sind, um die H.264-Videocodierung/-decodierung zu deaktivieren. Stattdessen erfolgt die Videocodierung und -decodierung in der Software auf der CPU. Wenn eine GPU verfügbar ist, kann der Bot sie für sein eigenes Grafikrendering nutzen, z. B. wenn der Bot ein 3D-Grafikmodul verwendet.
- Die VM-Instanz, die den Echtzeitmedienbot hostet, muss mindestens 2 CPU-Kerne aufweisen. Für Azure wird ein virtueller Computer der Dv2-Serie empfohlen. Bei anderen Azure-VM-Typen ist ein System mit vier virtuellen CPUs (vCPU) die mindest erforderliche Größe. Ausführliche Informationen zu Azure VM-Typen finden Sie in der [Azure-Dokumentation.](/azure/virtual-machines/windows/sizes-general) 

## <a name="code-sample"></a>Codebeispiel

Beispiele für von der Anwendung gehostete Medienbots sind:

| **Beispielname** | **Beschreibung** | **Graph** |
|------------|-------------|-----------|
| Beispiel für lokale Medien | Beispiele, die unterschiedliche lokale Medienszenarien veranschaulichen. | [View](https://github.com/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/V1.0Samples/LocalMediaSamples) |
| Beispiel für Remotemedien | Beispiele, die verschiedene Remotemedienszenarien veranschaulichen. | [View](https://github.com/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/V1.0Samples/RemoteMediaSamples) |

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Unterstützte Medienformate](~/resources/media-formats.md)

## <a name="see-also"></a>Siehe auch

- [Graph Dokumentation zum Aufrufen des SDK](https://microsoftgraph.github.io/microsoft-graph-comms-samples/docs/)
- Die Bots benötigen mehr Rechen- und Netzwerkbandbreitenkapazität als Messaging-Bots und verursachen deutlich höhere Betriebskosten. Ein Echtzeit-Medienbot-Entwickler muss die Skalierbarkeit des Bots sorgfältig messen und sicherstellen, dass der Bot nicht mehr gleichzeitige Anrufe akzeptiert, als er verwalten kann. Ein videoaktivierter Bot kann nur eine oder zwei gleichzeitige Mediensitzungen pro CPU-Kern unterstützen, wenn die rohen RGB24- oder NV12-Videoformate verwendet werden.
- Die Echtzeitmedienplattform nutzt derzeit keine Grafikverarbeitungseinheiten (GPU), die auf dem virtuellen Computer verfügbar sind, um die H.264-Videocodierung oder -Decodierung zu deaktivieren. Stattdessen erfolgt die Videocodierung und -decodierung in der Software auf der CPU. Wenn eine GPU verfügbar ist, nutzt der Bot diese für das eigene Grafikrendering, z. B. wenn der Bot ein 3D-Grafikmodul verwendet.
- Die VM-Instanz, die den Echtzeitmedienbot hostet, muss mindestens 2 CPU-Kerne aufweisen. Für Azure wird ein virtueller Computer der Dv2-Serie empfohlen. Für andere Azure-VM-Typen ist ein System mit 4 virtuellen CPUs (vCPU) die mindest erforderliche Größe. Weitere Informationen zu Azure VM-Typen finden Sie in der [Azure-Dokumentation.](/azure/virtual-machines/windows/sizes-general)

Der nächste Abschnitt enthält Beispiele, die unterschiedliche lokale Medienszenarien veranschaulichen.

## <a name="samples-and-additional-resources"></a>Beispiele und zusätzliche Ressourcen

- [Beispielanwendungen](https://github.com/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/V1.0Samples/LocalMediaSamples)
- [Graph aufrufende SDK-Dokumentation](https://microsoftgraph.github.io/microsoft-graph-comms-samples/docs/)