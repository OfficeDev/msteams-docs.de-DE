---
title: Anforderungen und Überlegungen für anwendungsgehostete Medienbots
description: Verstehen Sie wichtige Anforderungen und Überlegungen sowie Skalierbarkeits- und Leistungsüberlegungen im Zusammenhang mit der Erstellung von anwendungsgehosteten Medienbots für Microsoft Teams anhand von Codebeispielen und Beispielen.
ms.topic: conceptual
ms.localizationpriority: high
keywords: Anwendungsgehostete Medien Windows-Server Azure-VM
ms.date: 11/16/2018
ms.openlocfilehash: 35ad133d898b53538f51c2ae4c699cd19368f9af
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111983"
---
# <a name="requirements-and-considerations-for-application-hosted-media-bots"></a>Anforderungen und Überlegungen für anwendungsgehostete Medienbots

Ein von einer Anwendung gehosteter Medienbot benötigt die [`Microsoft.Graph.Communications.Calls.Media` .NET-Bibliothek](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/), um auf die Audio- und Videomedienströme zuzugreifen. Der Bot muss auf einem lokalen Windows Server-Computer oder einem Windows Server-Gastbetriebssystem (OS) in Azure bereitgestellt werden.

> [!NOTE]
>
> * Die Anleitung zum Entwickeln von Messaging- und Interactive Voice Response (IVR)-Bots gilt nicht vollständig für das Erstellen von anwendungsgehosteten Medien-Bots.
> * Da sich die Microsoft Real-time Media Platform für Bots in der Entwicklervorschau befindet, können sich die Anleitungen in diesem Dokument ändern.

## <a name="c-or-net-and-windows-server-for-development"></a>C# oder .NET und Windows Server für die Entwicklung

Ein von der Anwendung gehosteter Medienbot erfordert Folgendes:

* Der Bot muss in C# und dem standardmäßigen .NET Framework entwickelt und in Microsoft Azure bereitgestellt werden. Sie können C++- oder Node.js-APIs nicht verwenden, um auf Echtzeitmedien zuzugreifen, und .NET Core wird für einen von einer Anwendung gehosteten Medienbot nicht unterstützt.

* Der Bot kann in einer der folgenden Azure-Dienstumgebungen gehostet werden:
  * Cloud-Dienst.
  * Service Fabric mit Virtual Machine Scale Sets (VMSS).
  * Infrastructure as a Service (IaaS) Virtuelle Maschine (VM).  
  
* Der Bot kann nicht als Azure-Web-App bereitgestellt werden.

* Der Bot muss auf einer aktuellen Version der `Microsoft.Graph.Communications.Calls.Media`.NET-Bibliothek ausgeführt werden. Der Bot muss entweder die neueste verfügbare Version des [NuGet-Pakets oder eine Version verwenden](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/), die nicht älter als drei Monate ist. Ältere Versionen der Bibliothek sind veraltet und funktionieren nach einigen Monaten nicht mehr. Die Aktualisierung der `Microsoft.Graph.Communications.Calls.Media` Bibliothek stellt die beste Interoperabilität zwischen dem Bot und Microsoft Teams sicher.

Der nächste Abschnitt enthält Einzelheiten darüber, wo sich Echtzeit-Medienaufrufe befinden.

## <a name="real-time-media-calls-stay-where-they-are-created"></a>Echtzeit-Medienanrufe bleiben dort, wo sie erstellt wurden

Echtzeit-Medienanrufe bleiben auf dem Computer, auf dem sie erstellt wurden. Ein Echtzeit-Medienanruf wird an die Instanz der virtuellen Maschine (VM) angeheftet, die den Anruf angenommen oder gestartet hat. Medien von einem Microsoft Teams-Anruf oder -Meeting fließen zu dieser VM-Instanz, und Medien, die der Bot an Microsoft Teams zurücksendet, müssen ebenfalls von dieser VM stammen. Wenn beim Stoppen der VM Echtzeit-Medienaufrufe ausgeführt werden, werden diese Aufrufe abrupt beendet. Wenn der Bot Vorkenntnisse über das bevorstehende Herunterfahren der VM hat, kann er die Anrufe beenden.

Der nächste Abschnitt enthält Details zur Zugänglichkeit von anwendungsgehosteten Medien-Bots.

## <a name="application-hosted-media-bots-accessible-on-the-internet"></a>Anwendungsgehostete Medien-Bots, auf die über das Internet zugegriffen werden kann

Von der Anwendung gehostete Medien-Bots müssen direkt im Internet zugänglich sein. Diese Bots müssen die folgenden Funktionen enthalten:

* Auf jede VM-Instanz, die einen von der Anwendung gehosteten Medienbot in Azure hostet, muss direkt über das Internet mit einer öffentlichen IP-Adresse (ILPIP) auf Instanzebene zugegriffen werden können.
  * Informationen zum Abrufen und Konfigurieren eines ILPIP für einen Azure Cloud-Dienst finden Sie unter Klassische [Übersicht über öffentliche IP-Adressen auf Instanzebene](/azure/virtual-network/virtual-networks-instance-level-public-ip).
  * Informationen zum Konfigurieren eines ILPIP für eine VM-Skalierungsgruppe finden Sie unter [öffentliches IPv4 pro virtuellem Computer](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-networking#public-ipv4-per-virtual-machine).
* Der Dienst, der einen von der Anwendung gehosteten Medienbot hostet, muss außerdem jede VM-Instanz mit einem öffentlich zugänglichen Port konfigurieren, der der jeweiligen Instanz zugeordnet ist.
  * Für einen Azure Cloud Service erfordert dies einen Instanzeingabeendpunkt. Weitere Informationen [finden Sie unter Aktivieren der Kommunikation für Rolleninstanzen in Azure](/azure/cloud-services/cloud-services-enable-communication-role-instances).
  * Für eine VM-Skalierungsgruppe muss eine NAT-Regel auf dem Load Balancer konfiguriert werden. Weitere Informationen finden Sie unter [virtuelle Netzwerke und virtuelle Computer in Azure](/azure/virtual-machines/windows/network-overview).

* Anwendungsgehostete Medien-Bots werden vom Bot Framework-Emulator nicht unterstützt.

Der nächste Abschnitt enthält Details zu Skalierbarkeits- und Leistungsüberlegungen von anwendungsgehosteten Medien-Bots.

## <a name="scalability-and-performance-considerations"></a>Überlegungen zu Skalierbarkeit und Leistung

Die von der Anwendung gehosteten Medien-Bots erfordern die folgenden Skalierbarkeits- und Leistungsüberlegungen:

* Von Anwendungen gehostete Medien-Bots erfordern mehr Rechen- und Netzwerkkapazität (Bandbreite) als Messaging-Bots und können erheblich höhere Betriebskosten verursachen. Ein Echtzeit-Media-Bot-Entwickler muss die Skalierbarkeit des Bots sorgfältig messen und sicherstellen, dass der Bot nicht mehr gleichzeitige Anrufe akzeptiert, als er bewältigen kann. Ein videofähiger Bot kann möglicherweise nur eine oder zwei gleichzeitige Mediensitzungen pro CPU-Kern aufrechterhalten (bei Verwendung der „rohen“ RGB24- oder NV12-Videoformate).
* Die Real-Time Media Platform nutzt derzeit keine auf der VM verfügbaren Graphics Processing Units (GPU), um H.264-Videokodierung/-dekodierung auszulagern. Stattdessen werden Videocodierung und -decodierung in Software auf der CPU durchgeführt. Wenn eine GPU verfügbar ist, kann der Bot diese zum Beispiel für sein eigenes Grafik-Rendering nutzen, wenn der Bot eine 3D-Grafik-Engine verwendet.
* Die VM-Instanz, die den Echtzeit-Medienbot hostet, muss mindestens 2 CPU-Kerne haben. Für Azure wird ein virtueller Computer der Dv2-Serie empfohlen. Für andere Azure-VM-Typen ist ein System mit vier virtuellen CPUs (vCPU) die erforderliche Mindestgröße. Ausführliche Informationen zu Azure-VM-Typen finden Sie in der [Azure-Dokumentation](/azure/virtual-machines/windows/sizes-general).

## <a name="code-sample"></a>Codebeispiel

Beispiele für von der Anwendung gehostete Medien-Bots lauten wie folgt:

| **Beispielname** | **Beschreibung** | **Graph** |
|------------|-------------|-----------|
| Lokale Medienprobe | Beispiele, die verschiedene lokale Medienszenarien veranschaulichen. | [Anzeigen](https://github.com/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/V1.0Samples/LocalMediaSamples) |
| Remote-Medienbeispiel | Beispiele, die verschiedene Remote-Medien-Szenarien veranschaulichen. | [View](https://github.com/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/V1.0Samples/RemoteMediaSamples) |

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Unterstützte Medienformate](~/resources/media-formats.md)

## <a name="see-also"></a>Siehe auch

* [Graph Calling SDK-Dokumentation](https://microsoftgraph.github.io/microsoft-graph-comms-samples/docs/)
* Die Bots benötigen mehr Rechen- und Netzwerkbandbreitenkapazität als Messaging-Bots und verursachen deutlich höhere Betriebskosten. Ein Echtzeit-Media-Bot-Entwickler muss die Skalierbarkeit des Bots sorgfältig messen und sicherstellen, dass der Bot nicht mehr gleichzeitige Anrufe akzeptiert, als er bewältigen kann. Ein videofähiger Bot kann nur eine oder zwei gleichzeitige Mediensitzungen pro CPU-Kern aufrechterhalten, wenn er die rohen RGB24- oder NV12-Videoformate verwendet.
* Die Echtzeit-Medienplattform nutzt derzeit keine auf der VM verfügbaren Grafikprozessoreinheiten (GPU), um die H.264-Videokodierung oder -dekodierung auszulagern. Stattdessen werden Videocodierung und -decodierung in Software auf der CPU durchgeführt. Wenn eine GPU verfügbar ist, nutzt der Bot diese für sein eigenes Grafik-Rendering, beispielsweise wenn der Bot eine 3D-Grafik-Engine verwendet.
* Die VM-Instanz, die den Echtzeit-Medienbot hostet, muss mindestens 2 CPU-Kerne haben. Für Azure wird ein virtueller Computer der Dv2-Serie empfohlen. Für andere Azure-VM-Typen ist ein System mit 4 virtuellen CPUs (vCPU) die erforderliche Mindestgröße. Weitere Informationen zu Azure-VM-Typen finden Sie in der [Azure-Dokumentation](/azure/virtual-machines/windows/sizes-general).

Der nächste Abschnitt enthält Beispiele, die verschiedene lokale Medienszenarien veranschaulichen.

## <a name="samples-and-additional-resources"></a>Beispiele und zusätzliche Ressourcen

* [Anwendungsbeispiele](https://github.com/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/V1.0Samples/LocalMediaSamples)
* [Graph Calling SDK-dokumentation](https://microsoftgraph.github.io/microsoft-graph-comms-samples/docs/)
