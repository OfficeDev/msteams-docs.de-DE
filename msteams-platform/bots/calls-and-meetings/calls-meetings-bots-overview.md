---
title: Bots für Anrufe und Onlinebesprechungen
description: Erfahren Sie, wie Ihre Microsoft Teams-Apps mit Benutzern per Sprach- und Videofunktion mithilfe von Microsoft Graph-APIs für Anrufe und Onlinebesprechungen interagieren können, und erfahren Sie mehr über Mediendatenströme in Echtzeit.
ms.topic: conceptual
ms.localizationpriority: medium
keywords: Anrufe Audio Video IVR Voice Online-Besprechungen Echtzeit Medienstreams Bot
ms.openlocfilehash: 19f101a35120e068dbdcf06fe12e5bf030f44822
ms.sourcegitcommit: 6906ba7e2a6e957889530b0a117a852c43bc86a6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2022
ms.locfileid: "63784002"
---
# <a name="calls-and-online-meetings-bots"></a>Bots für Anrufe und Onlinebesprechungen

Bots können mit Teams Anrufen und Besprechungen in Echtzeit mit Sprach-, Video- und Bildschirmfreigabe interagieren. Mit [Microsoft Graph-APIs für Anrufe und Onlinebesprechungen](/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true) können Teams Apps jetzt mit Benutzern interagieren, indem Sie Sprach- und Videofunktionen verwenden, um die Benutzererfahrung zu verbessern. Mit diesen APIs können Sie die folgenden neuen Features hinzufügen:

* Interaktive Sprachantwort (Interactive Voice Response, IVR).
* Anrufsteuerung.
* Zugriff auf Audio- und Videodatenströme in Echtzeit, einschließlich Desktop- und App-Freigabe.

Um diese Graph-APIs in einer Teams-App zu verwenden, erstellen Sie einen Bot und geben einige zusätzliche Informationen und Berechtigungen an.

Darüber hinaus ermöglicht die Echtzeit-Medienplattform Bots die Interaktion mit Teams Anrufen und Besprechungen mithilfe von Echtzeit-Sprach-, Video- und Bildschirmfreigabe. Ein Bot, der an Audio- oder Videoanrufen und Onlinebesprechungen teilnimmt, ist ein regulärer Microsoft Teams Bot mit einigen zusätzlichen Features, die zum Registrieren des Bots verwendet werden.

Mit dem Teams App-Manifest mit zwei zusätzlichen Einstellungen `supportsCalling` und `supportsVideo`Graph Berechtigungen für die Microsoft App-ID Ihres Bots und der Zustimmung des Mandantenadministrators können Sie den Bot registrieren. Bei der Registrierung eines Bots für Anrufe und Besprechungen für Teams wird die Webhook-URL erwähnt, die der Webhook-Endpunkt für alle eingehenden Anrufe an Ihren Bot ist. Für einen von der Anwendung gehosteten Medienbot ist Microsoft erforderlich. Graph. Communications.Calls.Media .NET library to access the audio and video media streams, and the bot must be deployed on a Windows Server machine or Windows Server guest Operating System (OS) in Azure. Bots auf Teams unterstützen nur eine bestimmte Gruppe von Medienformaten für Audio- und Videoinhalte.

Jetzt müssen Sie einige grundlegende Konzepte, Terminologie und Konventionen verstehen.

## <a name="terminologies"></a>Terminologien

Die folgenden Kernkonzepte, Terminologie und Konventionen führen Sie durch die Verwendung von Anrufen und Onlinebesprechungs-Bots:

* Audio- oder Videoanrufe
* Anruftypen
* Signale
* Anrufe und Onlinebesprechungen
* Echtzeitmedien

### <a name="audio-or-video-calls"></a>Audio- oder Videoanrufe

Anrufe in Teams können ausschließlich Audio- oder Audio- und Videoanrufe sein. Anstelle von Audio- oder Videoanrufen wird der Begriff "Anruf" verwendet.

### <a name="call-types"></a>Anruftypen

Anrufe sind peer-to-peer zwischen einer Person und Ihrem Bot oder Multiparty zwischen Ihrem Bot und zwei oder mehr Personen in einem Gruppenanruf.

![Anruftypen](~/assets/images/calls-and-meetings/call-types.png)

Nachfolgend sind die verschiedenen Anruftypen und Berechtigungen aufgeführt, die für den Anruf erforderlich sind:

* Ein Benutzer kann einen Peer-to-Peer-Anruf mit Ihrem Bot initiieren oder Ihren Bot zu einem vorhandenen Anruf mit mehreren Teilnehmern einladen. Der Anruf mit mehreren Teilnehmern ist in der Teams Benutzeroberfläche noch nicht aktiviert.

    > [!NOTE]
    > Benutzerinitiierte Aufrufe an einen Bot werden derzeit auf Microsoft Teams mobilen Plattform nicht unterstützt.

* Graph Berechtigungen sind nicht erforderlich, damit ein Benutzer einen Peer-to-Peer-Anruf mit Ihrem Bot initiiert. Zusätzliche Berechtigungen sind erforderlich, damit Ihr Bot an einem Anruf mit mehreren Teilnehmern teilnimmt, oder damit Ihr Bot einen Peer-to-Peer-Anruf mit einem Benutzer initiiert.
* Ein Anruf kann als Peer-to-Peer-Anruf beginnen und schließlich zu einem Anruf mit mehreren Teilnehmern werden. Ihr Bot kann Anrufe mit mehreren Teilnehmern initiieren, indem er andere Benutzer einlädt, vorausgesetzt, Ihr Bot verfügt über die richtigen Berechtigungen. Wenn Ihr Bot nicht über die Berechtigung zum Teilnehmen an Gruppenanrufen verfügt und ein Teilnehmer einen anderen Teilnehmer zum Anruf hinzufügt, wird Ihr Bot aus dem Anruf entfernt.

### <a name="signals"></a>Signale

Es gibt zwei Arten von Signalen: eingehende Anrufe und Eingehende Anrufe. Es folgen die verschiedenen Features von Signalen:

* Um einen eingehenden Anruf zu erhalten, geben Sie einen Endpunkt in Ihre Bot-Einstellungen ein. Dieser Endpunkt empfängt eine Benachrichtigung, wenn ein eingehender Anruf initiiert wird. Sie können den Anruf annehmen, ablehnen oder an eine andere Person weiterleiten.

    ![Anrufverarbeitung](~/assets/images/calls-and-meetings/call-handling.png)

* Wenn sich ein Bot in einem Anruf befindet, gibt es APIs zum Stummschalten und Aufheben der Stummschaltung des Bots und zum Starten oder Beenden der Freigabe von Video- oder Desktopinhalten für andere Teilnehmer.
* Der Bot kann auch auf die Liste der Teilnehmer zugreifen, neue Teilnehmer einladen und stummschalten.

### <a name="calls-and-online-meetings"></a>Anrufe und Onlinebesprechungen

Aus sicht eines Teams Benutzers gibt es zwei Arten von Onlinebesprechungen, Ad-hoc-Besprechungen und geplante. Aus Sicht eines Bots sind beide Onlinebesprechungen identisch. Für einen Bot ist eine Onlinebesprechung ein Anruf mit mehreren Teilnehmern zwischen einer Gruppe von Teilnehmern und enthält Besprechungskoordinaten. Besprechungskoordinaten sind die Metadaten für die Besprechung, einschließlich `botId`, der Besprechung `joinUrl``startTime` zugeordnet usw`endTime``chatId`.

### <a name="real-time-media"></a>Echtzeitmedien

Wenn ein Bot an einem Anruf oder einer Onlinebesprechung teilnimmt, muss er audio- und videostreams behandeln. Wenn Benutzer über einen Anruf sprechen, sich auf einer Webcam zeigen oder ihre Bildschirme in einer Besprechung präsentieren, wird sie einem Bot als Audio- und Videostreams angezeigt. Wenn ein Bot etwas so Einfaches sagen möchte wie, **drücken Sie 0, um den Operator** in einem IvR-Szenario (Interactive Voice Response) zu erreichen, muss ein . WAV-Datei. Zusammenfassend wird dies als Medien oder Echtzeitmedien bezeichnet.

Echtzeitmedien beziehen sich auf Szenarien, in denen Medien in Echtzeit verarbeitet werden müssen, im Gegensatz zur Wiedergabe von zuvor aufgezeichneten Audio- oder Videodaten. Der Umgang mit Mediendatenströmen, insbesondere Echtzeit-Medienstreams, ist äußerst komplex. Microsoft hat die Echtzeitmedienplattform erstellt, um diese Szenarien zu verarbeiten und so viel wie möglich von den herkömmlichen Aufgaben der Echtzeitmedienverarbeitung zu entladen. Wenn der Bot einen eingehenden Anruf entgegennimmt oder einem neuen oder vorhandenen Anruf beitritt, muss er der Echtzeit-Medienplattform mitteilen, wie Medien behandelt werden. Wenn Sie eine IVR-Anwendung erstellen, können Sie die kostspielige Audioverarbeitung an Microsoft auslagern. Alternativ wird auch dieses Szenario unterstützt, wenn Ihr Bot direkten Zugriff auf Medienstreams benötigt. Es gibt zwei Arten der Medienverarbeitung:

* **Vom Dienst gehostete Medien**: Bots konzentrieren sich auf die Verwaltung des Anwendungsworkflows, z. B. das Weiterleiten von Anrufen und das Auslagern der Audioverarbeitung an die Microsoft Real-Time Media Platform. Bei vom Dienst gehosteten Medien stehen Ihnen mehrere Optionen zum Implementieren und Hosten Ihres Bots zur Verfügung. Ein vom Dienst gehosteter Medienbot kann als statusfreier Dienst implementiert werden, da er keine Medien lokal verarbeitet. Vom Dienst gehostete Medienbots können die folgenden APIs verwenden:

  * `PlayPrompt` zum Wiedergeben eines Audioclips.
  * `Record` für die Aufzeichnung von Audioclips.
  * `SubscribeToTone` zum Abonnieren von DTMF-Tönen (Dual Tone Multiple Frequency).

    Beispielsweise wissen, wann ein Benutzer **0** gedrückt hat, um den Operator zu erreichen.

* **In der Anwendung gehostete Medien**: Damit ein Bot direkten Zugriff auf die Medien erhält, benötigt er eine bestimmte Graph Berechtigung. Nachdem Ihr Bot über die Berechtigung verfügt, hilft Ihnen die [Echtzeit-Medienbibliothek](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/) und das [Graph aufrufenden SDK](https://microsoftgraph.github.io/microsoft-graph-comms-samples/docs/articles/index.html#graph-calling-sdk-and-stateful-client-builder) beim Erstellen umfangreicher Echtzeitmedien und aufrufenden Bots. Ein in der Anwendung gehosteter Bot muss in einer Windows-Umgebung gehostet werden. Weitere Informationen finden Sie unter [von der Anwendung gehostete Medienbots](./requirements-considerations-application-hosted-media-bots.md).

## <a name="code-sample"></a>Codebeispiel

| **Beispielname** | **Beschreibung** | **Graph** |
|---------------|----------|--------|
| Graph Kommunikation | Graph Kommunikation, um mit der Kommunikationsplattform von Microsoft zu interagieren. | [Anzeigen](https://github.com/microsoftgraph/microsoft-graph-comms-samples) |

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Medienanrufe und Besprechungen in Echtzeit](~/bots/calls-and-meetings/real-time-media-concepts.md)

## <a name="see-also"></a>Siehe auch

* [Graph API-Referenz](/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true)
* [Beispielapps](https://github.com/microsoftgraph/microsoft-graph-comms-samples)
* [Registrieren eines Bots, der Anrufe und Onlinebesprechungen unterstützt](./registering-calling-bot.md)
* [Graph Berechtigungen für Anruf- und Onlinebesprechungs-Bots](./registering-calling-bot.md#add-graph-permissions)
* [So entwickeln Sie Anruf- und Onlinebesprechungs-Bots auf Ihrem Computer](./debugging-local-testing-calling-meeting-bots.md)
* [Anforderungen und Überlegungen für von der Anwendung gehostete Medienbots](./requirements-considerations-application-hosted-media-bots.md)
* [Technische Informationen zur Behandlung eingehender Anrufbenachrichtigungen](./call-notifications.md)
* [Einrichten einer automatischen Telefonzentrale](/microsoftteams/create-a-phone-system-auto-attendant)
* [Einrichten der automatischen Antwort für Microsoft Teams-Räume auf Android- und Teams-Videotelefongeräten](/microsoftteams/set-up-auto-answer-on-teams-android)