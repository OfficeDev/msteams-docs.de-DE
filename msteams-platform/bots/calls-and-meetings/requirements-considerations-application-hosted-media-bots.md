---
title: Anforderungen und Überlegungen für von der Anwendung gehostete Medienbots
description: Informationen zu wichtigen Anforderungen und Überlegungen im Zusammenhang mit der Erstellung von von Anwendungen gehosteten Medienbots für Microsoft Teams.
ms.topic: conceptual
keywords: Von der Anwendung gehostete Medien windows server azure vm
ms.date: 11/16/2018
ms.openlocfilehash: bf75b7f689713f16cb3ff9ff4313ab829b5cc2d6
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014488"
---
# <a name="requirements-and-considerations-for-application-hosted-media-bots"></a>Anforderungen und Überlegungen für von der Anwendung gehostete Medienbots

Nicht alle Anleitungen für die Entwicklung von Messaging- und Interactive Voice Response (IVR)-Bots gelten gleichermaßen für das Erstellen von von Anwendungen gehosteten Medienbots. In diesem Artikel werden einige der wichtigen Anforderungen und Überlegungen für die Entwicklung und Ausführung eines in einer Anwendung gehosteten Medienbots beschrieben.

> [!NOTE]
> Da sich die Microsoft Real-time Media Platform für Bots in der Entwicklervorschau befindet, kann die Anleitung in diesem Artikel geändert werden.

## <a name="application-hosted-media-bot-development-requires-cnet-and-windows-server"></a>Für die Entwicklung von von der Anwendung gehosteten Medienbots sind C#/.NET und Windows Server erforderlich.

- Ein von einer Anwendung gehosteter Medienbot erfordert die .NET-Bibliothek (hier verfügbar für den Zugriff auf die Audio- und Videomedienstreams, und der Bot muss auf einem Windows Server-Computer (oder Windows Server-Gastbetriebssystem in Azure) bereitgestellt `Microsoft.Graph.Communications.Calls.Media` werden.[](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/) Daher muss der Bot in C# und dem standardmäßigen .NET Framework entwickelt und in Microsoft Azure bereitgestellt werden. Sie können C++ oder Node.js-APIs nicht für den Zugriff auf Echtzeitmedien verwenden, und .NET Core wird für einen in der Anwendung gehosteten Medienbot nicht unterstützt.

- Ein von einer Anwendung gehosteter Medienbot kann in einer der folgenden Azure-Dienstumgebungen gehostet werden:
  - Clouddienst.
  - Service Fabric mit VmSS (Virtual Machine Scale Sets).
  - Infrastructure as a Service (IaaS) Virtual Machine (VM).  
  
- Ein in der Anwendung gehosteter Medienbot kann nicht als Azure Web App bereitgestellt werden.

- Ein in der Anwendung gehosteter Medienbot muss auf einer aktuellen Version der `Microsoft.Graph.Communications.Calls.Media` .NET-Bibliothek ausgeführt werden. Der Bot sollte entweder die neueste verfügbare Version des [NuGet-Pakets](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/)oder eine Version verwenden, die nicht mehr als drei Monate alt ist. Ältere Versionen der Bibliothek sind veraltet und funktionieren nach einigen Monaten möglicherweise nicht mehr. Wenn Sie die Bibliothek auf dem neuesten Stand halten, wird `Microsoft.Graph.Communications.Calls.Media` die beste Interoperabilität zwischen dem Bot und Microsoft Teams sichergestellt.

## <a name="real-time-media-calls-stay-on-the-machine-where-they-were-created"></a>Echtzeitmedienanrufe bleiben auf dem Computer, auf dem sie erstellt wurden

- Ein Echtzeitmedienanruf wird an die Instanz des virtuellen Computers (VM) angeheftet, die den Anruf angenommen oder gestartet hat. Medien aus einem Microsoft Teams-Anruf oder einer Besprechung fließen zu dieser VM-Instanz, und Medien, die der Bot an Microsoft Teams zurücksendet, müssen ebenfalls von diesem virtuellen Computer stammen.
- Wenn beim Beenden des virtuellen Computers Echtzeitmedienanrufe ausgeführt werden, werden diese Anrufe abrupt beendet. Wenn der Bot bereits über Kenntnisse des ausstehenden Herunterfahrens von virtuellen Computer verfügt, kann er versuchen, die Anrufe "anständig" zu beenden.

## <a name="application-hosted-media-bots-must-be-directly-accessible-on-the-internet"></a>Auf von der Anwendung gehostete Medienbots muss direkt über das Internet zugegriffen werden können.

- Jede VM-Instanz, die einen in der Anwendung gehosteten Medienbot in Azure hosten, muss direkt über das Internet über eine öffentliche ILPIP (Instance-Level Public IP Address) auf Instanzebene zugänglich sein.
  - Informationen zum Abrufen und Konfigurieren eines ILPIP für einen Azure Cloud Service finden Sie in der Übersicht über öffentliche [IP (Classic) auf Instanzebene.](/azure/virtual-network/virtual-networks-instance-level-public-ip)
  - Informationen zum Konfigurieren eines ILPIP für einen Skalierungssatz für virtuelle Computer finden Sie unter [Öffentliches IPv4 pro virtuellem Computer.](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-networking#public-ipv4-per-virtual-machine)
- Der Dienst, der einen in der Anwendung gehosteten Medienbot hosten soll, muss außerdem jede VM-Instanz mit einem öffentlich zugänglichen Port konfigurieren, der der jeweiligen Instanz zugeordnet ist.
  - Für einen Azure Cloud Service ist dafür ein Instanzeingabeendpunkt erforderlich. Siehe ["Kommunikation für Rolleninstanzen in Azure aktivieren".](/azure/cloud-services/cloud-services-enable-communication-role-instances)
  - Für einen #A0 muss eine #A1 im Lastenausgleich konfiguriert werden. siehe [Virtuelle Netzwerke und virtuelle Computer in Azure](/azure/virtual-machines/windows/network-overview).
- Von der Anwendung gehostete Medienbots werden vom Bot -Framework-Emulator nicht unterstützt.

## <a name="scalability-and-performance-considerations"></a>Überlegungen zu Skalierbarkeit und Leistung

- In der Anwendung gehostete Medienbots erfordern eine höhere Rechen- und Netzwerkkapazität (Bandbreite) als Messaging-Bots und können deutlich höhere Betriebskosten verursachen. Ein Entwickler eines Medienbots in Echtzeit muss die Skalierbarkeit des Bots sorgfältig messen und sicherstellen, dass der Bot nicht mehr gleichzeitige Anrufe akzeptiert, als er verwalten kann. Ein videofähiger Bot kann möglicherweise nur eine oder zwei gleichzeitige Mediensitzungen pro PROZESSORkern unterstützen (bei Verwendung der "rohen" RGB24- oder NV12-Videoformate).
- Die Echtzeitmedienplattform nutzt derzeit keine auf dem virtuellen Computer verfügbaren Grafikprozessoren (Gpu), um die H.264-Videocodierung/-decodierung zu deaktivieren. Stattdessen erfolgt die Videocodierung und -decodierung in der Software auf der CPU. Wenn eine GPU verfügbar ist, kann der Bot sie für das eigene Grafikrendering nutzen (z. B. wenn der Bot ein 3D-Grafikmodul verwendet).
- Die VM-Instanz, die den Echtzeitmedienbot hosten, muss mindestens 2 Prozessorkerne haben. Für Azure wird ein virtueller Computer der Dv2-Serie empfohlen. Für andere Azure -VM-Typen ist ein System mit 4 virtuellen CPUs (vCPU) die erforderliche Mindestgröße. Ausführliche Informationen zu Azure -VM-Typen finden Sie in der [Azure-Dokumentation.](/azure/virtual-machines/windows/sizes-general)

## <a name="samples-and-additional-resources"></a>Beispiele und zusätzliche Ressourcen

- [Beispielanwendungen](https://github.com/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/V1.0Samples/LocalMediaSamples)
- [Dokumentation zum Graph Calling SDK](https://microsoftgraph.github.io/microsoft-graph-comms-samples/docs/)
