---
title: Bots für Anrufe und Online Besprechungen
description: Erfahren Sie, wie Ihre Microsoft Teams-apps mit Benutzern interagieren können, die Sprach-und Videofunktionen mithilfe von Microsoft Graph-APIs für Anrufe und Onlinebesprechungen verwenden.
keywords: Anrufe für Audio-Video-IVR-VoIP-Onlinebesprechungen
ms.openlocfilehash: fa31bc55221befab1ac1b6b77e116f3fc2e1a935
ms.sourcegitcommit: bfdcd122b6b4ffc52d92320d4741f870c07f0542
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "49552430"
---
# <a name="calls-and-online-meetings-bots"></a>Bots für Anrufe und Onlinebesprechungen

> [!NOTE]
> Die Unterstützung für Anrufe und Bots für Onlinebesprechungen wird derzeit auf der mobilen Microsoft Teams-Plattform nicht unterstützt. 

Mit [Microsoft Graph-APIs für Anrufe und Onlinebesprechungen](/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true)können Microsoft Teams-apps nun mithilfe von Sprach-und Videofunktionen auf vielfältige Weise mit Benutzern interagieren. Mit diesen APIs können Sie neue Funktionen wie interaktive Sprachantwort (Interactive Voice Response, IVR), Anrufsteuerung und Zugriff auf Echtzeit-Audio-und/oder-Videodatenströme für Anrufe und Besprechungen hinzufügen, einschließlich Desktop-und App-Freigabe.

Um diese Microsoft Graph-APIs in einer Microsoft Teams-APP zu verwenden, erstellen Sie einen bot und geben einige zusätzliche Informationen und Berechtigungen an, die wir an anderer Stelle beschreiben, aber zunächst ist es wichtig, einige Kernkonzepte, Terminologie und Konventionen zu verstehen:

* **Audio/Videoanrufe.** Anrufe in Microsoft Teams können rein Audio-oder Audio + Video sein. Um der Kürze willen, sagen wir nicht "Audio/Video-Anruf" überall; Wir sagen einfach "Anruf" aus.
* **Anruftypen.** Anrufe sind entweder Peer-to-Peer (zwischen einer Person und Ihrem bot) oder mehrteilig (Ihr bot und zwei oder mehr Personen in einem Gruppenanruf).
  ![CallingTypes ](~/assets/images/calls-and-meetings/call-types.png) :
  * Ein Benutzer kann einen Peer-zu-Peer-Anruf mit Ihrem bot initiieren oder Ihren bot in einen vorhandenen mehr Parteien Anruf einladen (obwohl dieser noch nicht in der Microsoft Teams-Benutzeroberfläche aktiviert ist).
  * Microsoft Graph-Berechtigungen sind nicht erforderlich, damit ein Benutzer einen Peer-to-Peer-Anruf mit Ihrem bot initiieren kann, aber zusätzliche Berechtigungen sind erforderlich, damit Ihr bot an einem mehrteiligen Anruf teilnimmt oder Ihr bot einen Peer-to-Peer-Anruf mit einem Benutzer initiieren kann.
  * Ein Anruf wird möglicherweise als Peer-to-Peer gestartet und eskaliert zu mehr Parteien. Ihr Bot kann diese Eskalation initiieren, indem er andere einlädt, vorausgesetzt, Ihr bot verfügt über die entsprechenden Berechtigungen. Wenn Ihr bot keine Berechtigungen zur Teilnahme an Gruppen anrufen hat und ein Teilnehmer eine andere Partei hinzufügt, wird Ihr bot aus dem Anruf gelöscht.
* **Signal.** Es gibt zwei Arten von Signalen – eingehenden Anruf und in-Call:
  * Um einen eingehenden Anruf zu erhalten, geben Sie einen Endpunkt in ihren bot-Einstellungen an; dieser Endpunkt erhält eine Benachrichtigung, wenn ein eingehender Anruf ankommt. Sie können den Anruf annehmen, ablehnen oder an einen anderen Ort oder eine andere Person weiterleiten.
  ![Anruftypen](~/assets/images/calls-and-meetings/call-handling.png)
  * Wenn sich ein bot in einem Anruf befindet, gibt es APIs zum stumm schalten und zum Aufheben der Stummschaltung selbst sowie zum Starten/Beenden der Freigabe von Video-/Desktopinhalten mit den anderen Teilnehmern.
  * Der Bot kann auch auf die Teilnehmerliste zugreifen, neue Teilnehmer einladen und Sie stumm schalten.
* **Anrufe und Onlinebesprechungen.** Aus der Perspektive eines Teams-Benutzers gibt es zwei Arten von Onlinebesprechungen – Ad hoc und geplant. Aus der Perspektive eines bot sind beide jedoch identisch. Für einen Bot ist eine Onlinebesprechung nur ein mehr Parteien Anruf (die Gruppe von Teilnehmern) plus "Besprechungs Koordinaten", die Sie als Metadaten für die Besprechung betrachten können: `botId` , `chatId` die der Besprechung zugeordnet ist, `joinUrl` `startTime` / `endTime` und mehr.
* **Echt Zeit Medien.** Wenn ein bot an einem Anruf oder einer Onlinebesprechung teilnimmt, muss er sich mit Audio-und Videodatenströmen beschäftigen. Wenn Benutzer über einen Anruf sprechen, sich selbst in einer Webcam anzeigen oder ihre Bildschirme in einer Besprechung präsentieren, sieht ein bot diesen als Audio-und/oder Videostreams. Wenn ein bot etwas sagen oder Bildschirminhalte präsentieren möchte, erfordert dies einen Audio-oder Videostream. Selbst so einfach wie der bot sagt: "drücken Sie 0, um den Operator zu erreichen" in einem IVR-Szenario (Interaktive Sprachantwort) ist das Abspielen einer. WAV-Datei. Gemeinsam bezeichnen wir dies als _Medien_ -oder _Echt Zeit Medien_ (bei Bezugnahme auf Szenarien, in denen Medien in Echtzeit verarbeitet werden müssen, im Gegensatz zur Wiedergabe zuvor aufgezeichneten Audios/Videos). Historisch gesehen war der Umgang mit Mediendatenströmen, insbesondere in Echtzeit-Mediendatenströmen, für Entwickler äußerst komplex. Microsoft hat die _Echtzeit-Medienplattform_ erstellt, um diese Anwendungsfälle zu verarbeiten und so viel wie möglich von der herkömmlichen "schweren Hebung" der Echt Zeit Medienverarbeitung zu entlasten.  Wenn der Bot auf einen eingehenden Anruf antwortet oder einem neuen oder bestehenden Anruf beitritt, muss er der Real-Time Media-Plattform mitteilen, wie Medien behandelt werden. Wenn Sie eine IVR-Anwendung erstellen, können Sie die teure Audioverarbeitung an Microsoft abwälzen. Wenn Ihr bot auch direkten Zugriff auf Mediendatenströme erfordert, unterstützen wir dieses Szenario ebenfalls. Es gibt zwei Arten von Medienverarbeitung:
  * **Vom Dienst gehostete Medien.** Bots konzentrieren sich auf die Verwaltung des Anwendungsworkflows (beispielsweise das Weiterleiten von Anrufen) und die Abladung der Audioverarbeitung an die Microsoft-echt Zeit Medienplattform. Bei Dienst gehosteten Medien stehen Ihnen mehrere Optionen zum Implementieren und Hosten Ihres bot zur Verfügung. Ein von einem Dienst gehosteter Medien bot kann als statusloser Dienst implementiert werden, da Medien nicht lokal verarbeitet werden. Vom Dienst gehostete Medien Bots können APIs verwenden, beispielsweise `PlayPrompt` zum Abspielen eines Audioclips, `Record` zum Aufzeichnen von Audioclips oder zum Abonnieren von DTMF- `SubscribeToTone` Tönen (beispielsweise zu wissen, wann ein Benutzer 0 gedrückt hat, um den Operator zu erreichen).
  * **Von der Anwendung gehostete Medien.** Damit ein bot einen direkten Zugriff auf die Medien erhält, benötigt er eine bestimmte Graph-Berechtigung, aber sobald der bot ihn hat, hilft die [Echt Zeit Medienbibliothek](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/) und das [Graph-Aufruf-SDK](https://microsoftgraph.github.io/microsoft-graph-comms-samples/docs/articles/index.html#graph-calling-sdk-and-stateful-client-builder) beim Erstellen reichhaltiger, Echt Zeit Medien und beim Aufrufen von Bots. Ein von der Anwendung gehosteter bot muss in einer Windows-Umgebung gehostet werden, wie [hier](./requirements-considerations-application-hosted-media-bots.md)ausführlicher beschrieben.

## <a name="further-reading"></a>Weiterführende Literatur

Hier finden Sie weitere Informationen zum Erstellen und Testen von Anrufen und Online-Besprechungs-Bots:

* [Diagramm-API-Referenz](/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true)
* [Beispielapps](https://github.com/microsoftgraph/microsoft-graph-comms-samples)
* [Registrieren eines bot, der Anrufe und Onlinebesprechungen](./registering-calling-bot.md) und [Microsoft Graph-Berechtigungen für Anrufe und Online-Besprechungs-Bots](./registering-calling-bot.md#add-microsoft-graph-permissions) unterstützt
* [So entwickeln Sie Anrufer-und Online-Besprechungs-Bots auf Ihrem lokalen PC](./debugging-local-testing-calling-meeting-bots.md)
* [Weitere Informationen zur Echt Zeit Medienverarbeitung](./real-time-media-concepts.md)und [was für die Unterstützung von von Anwendungen gehosteten Medien erforderlich ist](./requirements-considerations-application-hosted-media-bots.md)
* [Technische Informationen zum Verarbeiten von Benachrichtigungen über eingehende Anrufe](./call-notifications.md)
