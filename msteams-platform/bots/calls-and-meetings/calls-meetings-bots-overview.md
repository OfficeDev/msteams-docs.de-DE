---
title: Bots für Anrufe und Onlinebesprechungen
description: Erfahren Sie, wie Ihre Microsoft Teams-Apps mithilfe von Sprach- und Videonachrichten mithilfe von Microsoft Graph-APIs für Anrufe und Onlinebesprechungen mit Benutzern interagieren können.
keywords: Anrufanrufe Audiovideo-IVR-Sprach-Onlinebesprechungen
ms.openlocfilehash: 0fcf420ba8d698404d00bb2cab3d61cab2245f40
ms.sourcegitcommit: 49d1ecda14042bf3f368b14c1971618fe979b914
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/23/2021
ms.locfileid: "51034642"
---
# <a name="calls-and-online-meetings-bots"></a>Bots für Anrufe und Onlinebesprechungen

Durch das Hinzufügen von [Microsoft Graph-APIs](/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true)für Anrufe und Onlinebesprechungen können Microsoft Teams-Apps jetzt auf vielfältige Weise mithilfe von Sprach- und Videonachrichten mit Benutzern interagieren. Mit diesen APIs können Sie neue Features wie interaktive Sprachantwort (Interactive Voice Response, IVR), Anrufsteuerung und Zugriff auf Audio- und/oder Videodatenströme in Echtzeit für Anrufe und Besprechungen hinzufügen, einschließlich Desktop- und App-Freigabe.

Um diese Microsoft Graph-APIs in einer Microsoft Teams-App zu verwenden, erstellen Sie einen Bot und geben einige zusätzliche Informationen und Berechtigungen an, die wir an anderer Stelle beschreiben. Zunächst ist es jedoch wichtig, einige kernige Konzepte, Terminologie und Konventionen zu verstehen:

* **Audio-/Videoanrufe.** Anrufe in Teams können rein audio- oder audio+video sein. Aus Gründen der Kürze sagen wir nicht überall "Audio-/Videoanruf". wir sagen nur "Anruf".
* **Anruftypen.** Anrufe sind peer-to-peer (zwischen einer Person und Ihrem Bot) oder mehrteilig (Ihr Bot und zwei oder mehr Personen in einem Gruppenanruf).
  ![CallingTypes ](~/assets/images/calls-and-meetings/call-types.png) :
  * Ein Benutzer kann einen Peer-to-Peer-Anruf mit Ihrem Bot initiieren oder Ihren Bot zu einem vorhandenen Mehrparteienanruf einladen (obwohl letzterer noch nicht in der Microsoft Teams-Benutzeroberfläche aktiviert ist).
  
  > [!NOTE]
  > Vom Benutzer initiierte Aufrufe an einen Bot werden derzeit auf der mobilen Microsoft Teams-Plattform nicht unterstützt. 
  
  * Microsoft Graph-Berechtigungen sind für einen Benutzer nicht erforderlich, um einen Peer-zu-Peer-Anruf mit Ihrem Bot zu initiieren, es sind jedoch zusätzliche Berechtigungen erforderlich, damit Ihr Bot an einem Mehrparteienanruf teilnehmen kann oder dass Ihr Bot einen Peer-zu-Peer-Anruf mit einem Benutzer initiieren kann.
  * Ein Anruf kann als Peer-to-Peer gestartet und auf mehrteilige Anrufe eskaliert werden. Ihr Bot kann diese Eskalation initiieren, indem er andere einlä bittet, vorausgesetzt, ihr Bot verfügt über die entsprechenden Berechtigungen. Wenn Ihr Bot nicht über berechtigungen für die Teilnahme an Gruppenanrufen verfügt und ein Teilnehmer eine andere Partei hinzufügt, wird Ihr Bot aus dem Anruf gelöscht.
* **Signalisierung.** Es gibt zwei Arten von Signalen: eingehender Anruf und In-Call-Anruf:
  * Um einen eingehenden Anruf zu empfangen, geben Sie einen Endpunkt in den Boteinstellungen an. Dieser Endpunkt empfängt eine Benachrichtigung, wenn ein eingehender Anruf eintrifft. Sie können den Anruf beantworten, ablehnen oder an einen anderen Ort oder eine andere Person umleiten.
  ![Anruftypen](~/assets/images/calls-and-meetings/call-handling.png)
  * Wenn sich ein Bot in einem Anruf befindet, gibt es APIs zum Stummschalten und Änderen der Änderung selbst und zum Starten/Beenden der Freigabe von Video-/Desktopinhalten für die anderen Teilnehmer.
  * Der Bot kann auch auf die Liste der Teilnehmer zugreifen, neue Teilnehmer einladen und stummschalten.
* **Anrufe und Onlinebesprechungen.** Aus Der Sicht eines Teams-Benutzers gibt es zwei Arten von Onlinebesprechungen – ad hoc und geplant. Aus Sicht eines Bots sind beide jedoch identisch. Für einen Bot ist eine Onlinekonferenz nur ein Mehrparteienanruf (der Teilnehmersatz) plus "Besprechungskoordinaten", die Sie als Metadaten für die Besprechung bezeichnen können: , der Besprechung zugeordnet, , und vieles `botId` `chatId` `joinUrl` `startTime` / `endTime` mehr.
* **Echtzeitmedien.** Wenn ein Bot an einem Anruf oder einer Onlinebe besprechung teilnimmt, muss er sich mit Audio- und Videostreams beschäftigen. Wenn Benutzer bei einem Anruf sprechen, sich auf einer Webcam anzeigen oder ihre Bildschirme in einer Besprechung präsentieren, wird dies von einem Bot als Audio- und/oder Videostreams "angezeigt". Wenn ein Bot etwas sagen oder Bildschirminhalte präsentieren möchte, erfordert dies einen Audio- oder Videostream. Selbst etwas so einfaches wie der Bot mit dem Satz "Drücken Sie 0, um den Operator zu erreichen" in einem IVR-Szenario (interaktive Sprachantwort) bedeutet die Wiedergabe eines . WAV-Datei. Insgesamt bezeichnen wir dies  als Medien oder Echtzeitmedien _(wenn_ wir uns auf Szenarien beziehen, in denen Medien in Echtzeit verarbeitet werden müssen, an stelle der Wiedergabe zuvor aufgezeichneter Audio-/Videodaten). In der Vergangenheit war der Umgang mit Medienstreams, insbesondere mit Echtzeitmedienstreams, für Entwickler äußerst komplex. Microsoft hat die _Echtzeitmedienplattform_ erstellt, um diese Verwendungsfälle zu verarbeiten und den herkömmlichen "Heavy Lifting" der Echtzeitmedienverarbeitung so weit wie möglich zu entlasten.  Wenn der Bot auf einen eingehenden Anruf antwortet oder einem neuen oder bestehenden Anruf beitritt, muss er der Real-Time Media-Plattform mitteilen, wie Medien behandelt werden. Wenn Sie eine IVR-Anwendung erstellen, können Sie die teure Audioverarbeitung an Microsoft ausladen. Alternativ unterstützen wir dieses Szenario auch, wenn Ihr Bot direkten Zugriff auf Medienstreams benötigt. Es gibt die beiden Arten der Medienverarbeitung:
  * **Vom Dienst gehostete Medien.** Bots konzentrieren sich auf die Verwaltung des Anwendungsworkflows (z. B. Routinganrufe) und das Ausladen der Audioverarbeitung an die Microsoft Real-time Media Platform. Mit vom Dienst gehosteten Medien haben Sie mehrere Optionen zum Implementieren und Hosten Ihres Bots. Ein vom Dienst gehosteter Medienbot kann als zustandsloser Dienst implementiert werden, da er keine Medien lokal verarbeiten kann. Vom Dienst gehostete Medienbots können APIs verwenden, z. B. zum Wiedergeben eines Audioclips, zum Aufzeichnen von Audioclips oder zum Abonnieren von `PlayPrompt` `Record` DTMF-Tönen (z. B. wissen, wann ein Benutzer 0 gedrückt hat, um den Operator zu `SubscribeToTone` erreichen).
  * **Von der Anwendung gehostete Medien.** Damit ein Bot direkten Zugriff auf die Medien erhalten kann, benötigt er eine [](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/) bestimmte Graph-Berechtigung, aber sobald ihr Bot vorhanden ist, können Sie mit der Echtzeitmedienbibliothek und dem [Graph Calling SDK](https://microsoftgraph.github.io/microsoft-graph-comms-samples/docs/articles/index.html#graph-calling-sdk-and-stateful-client-builder) umfangreiche Echtzeitmedien erstellen und Bots aufrufen. Ein vom Anwendungshosting gehosteter Bot muss in einer Windows-Umgebung gehostet werden, wie hier ausführlicher [beschrieben.](./requirements-considerations-application-hosted-media-bots.md)

## <a name="further-reading"></a>Weitere Informationen

Hier finden Sie weitere Informationen zum Erstellen und Testen von Anrufen und Onlinebesprechungsbots:

* [Graph-API-Referenz](/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true)
* [Beispielapps](https://github.com/microsoftgraph/microsoft-graph-comms-samples)
* [Registrieren eines Bots, der Anrufe und Onlinebesprechungen](./registering-calling-bot.md) sowie Microsoft Graph-Berechtigungen für Anrufe und [Onlinebesprechungen unterstützt](./registering-calling-bot.md#add-microsoft-graph-permissions)
* [Entwickeln von Anruf- und Online-Besprechungsbots auf Ihrem lokalen PC](./debugging-local-testing-calling-meeting-bots.md)
* [Weitere Informationen zur Medienverarbeitung in](./real-time-media-concepts.md)Echtzeit und zur Unterstützung von von Anwendungen [gehosteten Medien](./requirements-considerations-application-hosted-media-bots.md)
* [Technische Informationen zum Behandeln eingehender Anrufbenachrichtigungen](./call-notifications.md)
