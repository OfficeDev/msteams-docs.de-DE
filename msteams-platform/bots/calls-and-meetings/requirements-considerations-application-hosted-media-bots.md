---
title: Anforderungen und Überlegungen für von der Anwendung gehostete Medien Bots
description: Grundlegendes zu wichtigen Anforderungen und Überlegungen im Zusammenhang mit der Erstellung von von der Anwendung gehosteten Medien Bots für Microsoft Teams.
keywords: von der Anwendung gehostete Medien Windows Server Azure VM
ms.date: 11/16/2018
ms.openlocfilehash: f5b721edacb11e867d05c8213b74036cb51f419c
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674243"
---
# <a name="requirements-and-considerations-for-application-hosted-media-bots"></a>Anforderungen und Überlegungen für von der Anwendung gehostete Medien Bots

Nicht alle Anleitungen für die Entwicklung von Messaging-und IVR-Bots (Interactive Voice Response) gelten gleichermaßen für die Erstellung von von der Anwendung gehosteten Medien Bots. In diesem Artikel werden einige wichtige Anforderungen und Überlegungen für die Entwicklung und Ausführung eines von der Anwendung gehosteten Medien-bot beschrieben.

> [!NOTE]
> Da sich die Microsoft-echt Zeit Medienplattform für Bots in der Entwicklervorschau befindet, kann die Anleitung in diesem Artikel geändert werden.

## <a name="application-hosted-media-bot-development-requires-cnet-and-windows-server"></a>Die von der Anwendung gehostete Medien bot-Entwicklung erfordert C#-/.net und Windows Server

- Für einen von der Anwendung gehosteten Medien `Microsoft.Graph.Communications.Calls.Media` -bot ist die .NET-Bibliothek ([verfügbar](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/) für den Zugriff auf die Audio-und Video Mediendatenströme) erforderlich, und der bot muss auf einem Windows Server-Computer (oder Windows Server-Gastbetriebssystem in Azure) bereitgestellt werden. Daher muss der bot in C# entwickelt werden und die Standard .NET Framework und in Microsoft Azure bereitgestellt werden. Sie können nicht C++-oder Node. js-APIs verwenden, um auf Echt Zeit Medien zuzugreifen, und .net Core wird für einen von der Anwendung gehosteten Medien-bot nicht unterstützt.

- Ein von der Anwendung gehosteter Medien-bot kann in einer der folgenden Azure-Dienstumgebungen gehostet werden:
  - Cloud-Dienst.
  - Service Fabric mit Skalierungs Sätzen virtueller Computer (VMSS).
  - Infrastructure as a Service (IaaS) Virtual Machine (VM).  
  
- Ein von der Anwendung gehosteter Medien-bot kann nicht als Azure-Webanwendung bereitgestellt werden.

- Ein von der `Microsoft.Graph.Communications.Calls.Media` Anwendung gehosteter Medien-bot muss unter einer aktuellen Version der .NET-Bibliothek ausgeführt werden. Der bot sollte entweder die neueste verfügbare Version des [NuGet-Pakets](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/)oder eine Version verwenden, die nicht älter als drei Monate ist. Ältere Versionen der Bibliothek sind veraltet und funktionieren nach ein paar Monaten möglicherweise nicht mehr. Wenn Sie `Microsoft.Graph.Communications.Calls.Media` die Bibliothek auf dem neuesten Stand halten, wird die beste Interoperabilität zwischen bot und Microsoft Teams gewährleistet.

## <a name="real-time-media-calls-stay-on-the-machine-where-they-were-created"></a>Echt Zeit Medien Anrufe bleiben auf dem Computer, auf dem Sie erstellt wurden.

- Ein echt Zeit Medien Anruf wird an die VM-Instanz (Virtual Machine) angeheftet, die den Anruf angenommen oder gestartet hat. Medien von einem Microsoft Teams-Anruf oder einer Besprechung fließen in diese VM-Instanz ein, und Medien, die der bot zurück an Microsoft Teams sendet, müssen auch von dieser VM stammen.
- Wenn während der Beendigung des VM-Vorgangs in Echtzeit Medien Aufrufe ausgeführt werden, werden diese Aufrufe abrupt beendet. Wenn der bot über das ausstehende VM-Herunterfahren informiert ist, kann er versuchen, die Anrufe "ordnungsgemäß" zu beenden.

## <a name="application-hosted-media-bots-must-be-directly-accessible-on-the-internet"></a>Von der Anwendung gehostete Medien-Bots müssen im Internet direkt zugänglich sein.

- Jede VM-Instanz, die einen von der Anwendung gehosteten Medien bot in Azure hostet, muss direkt über das Internet mit einer öffentlichen IP-Adresse auf Instanzebene (ILPIP) zugänglich sein.
  - Informationen zum Abrufen und Konfigurieren eines ILPIP für einen Azure Cloud-Dienst finden Sie unter [instance Level Public IP (Classic) Overview](/azure/virtual-network/virtual-networks-instance-level-public-ip).
  - Informationen zum Konfigurieren eines ILPIP für eine VM-Skalierungs Gruppe finden Sie unter [Public IPv4 pro virtueller Computer](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-networking#public-ipv4-per-virtual-machine).
- Der Dienst, der einen von der Anwendung gehosteten Medien-bot hostet, muss auch jede VM-Instanz mit einem öffentlichen Port konfigurieren, der der jeweiligen Instanz zugeordnet ist.
  - Für einen Azure Cloud-Dienst erfordert dies einen Instanz-eingabeendpunkt; Weitere Informationen finden Sie unter [Aktivieren der Kommunikation für Rolleninstanzen in Azure](/azure/cloud-services/cloud-services-enable-communication-role-instances).
  - Für eine VM-Skalierungs Gruppe muss eine NAT-Regel auf dem Lastenausgleichsmodul konfiguriert werden; siehe [virtuelle Netzwerke und virtuelle Computer in Azure](/azure/virtual-machines/windows/network-overview).
- Von der Anwendung gehostete Medien-Bots werden vom bot Framework-Emulator nicht unterstützt.

## <a name="scalability-and-performance-considerations"></a>Überlegungen zu Skalierbarkeit und Leistung

- Von der Anwendung gehostete Medien-Bots benötigen mehr Rechen-und Netzwerkkapazität (Bandbreite) als Messaging-Bots und können erheblich höhere Betriebskosten verursachen. Ein Echtzeit-Medien bot-Entwickler muss die Skalierbarkeit des bot sorgfältig messen und sicherstellen, dass der bot nicht mehr gleichzeitige Anrufe akzeptiert, als er verwalten kann. Ein Video aktivierter bot kann möglicherweise nur eine oder zwei gleichzeitige Mediensitzungen pro CPU-Kern (bei Verwendung des "RAW"-RGB24-oder NV12-Video Formats) aufrecht erhalten.
- Die Echt Zeit Medienplattform nutzt derzeit keine GPU (Graphics Processing Units), die auf der VM zur Verfügung steht, um die H. 264-Videocodierung/-Dekodierung zu laden. Stattdessen werden Videocodierung und-Dekodierung in Software auf der CPU ausgeführt. Wenn eine GPU verfügbar ist, kann der bot diese für das eigene Grafikrendering nutzen (beispielsweise, wenn der bot einen 3D-Grafikmodul verwendet).
- Die VM-Instanz, die den Echt Zeit Medien-bot hostet, muss mindestens 2 CPU-Kerne aufweisen. Für Azure wird ein virtueller Computer der Dv2-Reihe empfohlen. Für andere Azure VM-Typen ist ein System mit 4 virtuellen CPUs (vCPU) die erforderliche Mindestgröße. Ausführliche Informationen zu Azure VM-Typen finden Sie in der [Azure-Dokumentation](/azure/virtual-machines/windows/sizes-general).

## <a name="samples-and-additional-resources"></a>Beispiele und zusätzliche Ressourcen

- [Beispielanwendungen](https://github.com/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/V1.0Samples/LocalMediaSamples)
- [Dokumentation zum Graph Calling SDK](https://microsoftgraph.github.io/microsoft-graph-comms-samples/docs/)
