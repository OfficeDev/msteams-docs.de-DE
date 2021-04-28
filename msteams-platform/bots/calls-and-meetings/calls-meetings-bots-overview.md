---
title: Bots für Anrufe und Onlinebesprechungen
description: Erfahren Sie, wie Ihre Microsoft Teams-Apps mithilfe von Sprach- und Videonachrichten mithilfe von Microsoft Graph-APIs für Anrufe und Onlinebesprechungen mit Benutzern interagieren können.
ms.topic: conceptual
localization_priority: Normal
keywords: Anrufanrufe Audiovideo-IVR-Sprach-Onlinebesprechungen
ms.openlocfilehash: d4cec30e110eed5f73929305cc43b84eed4d7524
ms.sourcegitcommit: a732789190f59ec1f3699e8ad2f06387e8fe1458
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2021
ms.locfileid: "52058313"
---
# <a name="calls-and-online-meetings-bots"></a>Bots für Anrufe und Onlinebesprechungen

> [!NOTE]
> Die Unterstützung für Anrufe und Online-Besprechungsbots wird derzeit auf der mobilen Microsoft Teams-Plattform nicht unterstützt.

Bots können mit Teams-Anrufen und -Besprechungen mithilfe von Sprach-, Video- und Bildschirmfreigabe in Echtzeit interagieren. Mit [Microsoft Graph-APIs für Anrufe und](/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true)Onlinebesprechungen können Teams-Apps jetzt mit Benutzern interagieren, die Sprach- und Videonachrichten verwenden, um die Benutzererfahrung zu verbessern. Mit diesen APIs können Sie die folgenden neuen Features hinzufügen:

* Interaktive Sprachantwort (Interactive Voice Response, IVR).
* Anrufsteuerung.
* Zugriff auf Audio- und Videostreams in Echtzeit, einschließlich Desktop- und App-Freigabe.

Um diese Graph-APIs in einer Teams-App zu verwenden, erstellen Sie einen Bot und geben einige zusätzliche Informationen und Berechtigungen an.

Darüber hinaus ermöglicht die Echtzeitmedienplattform Bots die Interaktion mit Teams-Anrufen und Besprechungen mithilfe von Echtzeit-Sprach-, Video- und Bildschirmfreigabe. Ein Bot, der an Audio- oder Videoanrufen und Onlinebesprechungen teil nimmt, ist ein regulärer Microsoft Teams-Bot mit wenigen zusätzlichen Funktionen, die zum Registrieren des Bots verwendet werden.

Das Microsoft Teams-App-Manifest mit zwei zusätzlichen Einstellungen und , Graph-Berechtigungen für die Microsoft App-ID Ihres Bots und die Zustimmung des Mandantenadministrators ermöglichen ihnen die Registrierung `supportsCalling` `supportsVideo` des Bots. Bei der Registrierung eines Anruf- und Besprechungsbots für Teams wird die Webhook-URL erwähnt, die der Webhook-Endpunkt für alle eingehenden Anrufe an Ihren Bot ist. Für einen von einer Anwendung gehosteten Medienbot muss die Microsoft.Graph.Communications.Calls.Media .NET-Bibliothek auf Audio- und Videomedienstreams zugreifen, und der Bot muss auf einem Windows Server-Computer oder Windows Server-Gastbetriebssystem (Os) in Azure bereitgestellt werden. Bots in Teams unterstützen nur eine bestimmte Gruppe von Medienformaten für Audio- und Videoinhalte.

Jetzt müssen Sie einige kernige Konzepte, Terminologie und Konventionen verstehen.

## <a name="terminologies"></a>Terminologies

Die folgenden Kernkonzepte, Terminologie und Konventionen führen Sie durch die Verwendung von Anrufen und Onlinebesprechungsbots:

* Audio- oder Videoanrufe
* Anruftypen
* Signale
* Anrufe und Onlinebesprechungen
* Echtzeitmedien

### <a name="audio-or-video-calls"></a>Audio- oder Videoanrufe

Anrufe in Teams können reine Audio- oder Audio- und Videoanrufe sein. Anstelle von Audio- oder Videoanrufen wird der Begriff Anruf verwendet.

### <a name="call-types"></a>Anruftypen

Anrufe sind peer-to-peer zwischen einer Person und Ihrem Bot oder mehrteilig zwischen Ihrem Bot und zwei oder mehr Personen in einem Gruppenanruf.

![Aufrufende Typen](~/assets/images/calls-and-meetings/call-types.png)

Es folgen die verschiedenen Anruftypen und Berechtigungen, die für den Anruf erforderlich sind:

* Ein Benutzer kann einen Peer-zu-Peer-Anruf mit Ihrem Bot initiieren oder Ihren Bot zu einem vorhandenen Mehrparteienanruf einladen. Der Aufruf mit mehrerenPartys ist noch nicht auf der Benutzeroberfläche von Teams aktiviert.
* Graph-Berechtigungen sind für einen Benutzer nicht erforderlich, um einen Peer-to-Peer-Anruf mit Ihrem Bot zu initiieren. Zusätzliche Berechtigungen sind erforderlich, damit Ihr Bot an einem Mehrparteienanruf teilnehmen kann oder dass der Bot einen Peer-zu-Peer-Anruf mit einem Benutzer initiieren kann.
* Ein Anruf kann als Peer-to-Peer gestartet werden und schließlich zu einem Mehrparteienanruf werden. Ihr Bot kann Anrufe mit mehrerenPartys initiieren, indem er andere Aufrufe einläutet, sofern Ihr Bot über die entsprechenden Berechtigungen verfügt. Wenn Ihr Bot nicht über berechtigungen für die Teilnahme an Gruppenanrufen verfügt und ein Teilnehmer einen anderen Teilnehmer zum Anruf hinzufügt, wird Ihr Bot aus dem Anruf gelöscht.

### <a name="signals"></a>Signale

Es gibt zwei Arten von Signalen, eingehende Anrufe und In-Call-Anrufe. Es folgen die verschiedenen Features von Signalen:

* Um einen eingehenden Anruf zu erhalten, geben Sie einen Endpunkt in ihre Boteinstellungen ein. Dieser Endpunkt empfängt eine Benachrichtigung, wenn ein eingehender Anruf initiiert wird. Sie können den Anruf beantworten, ablehnen oder an eine andere Person umleiten.

    ![Anrufbehandlung](~/assets/images/calls-and-meetings/call-handling.png)

* Wenn sich ein Bot in einem Anruf befindet, gibt es APIs zum Stummschalten und Stummschalten des Bots sowie zum Starten oder Beenden der Freigabe von Video- oder Desktopinhalten für andere Teilnehmer.
* Der Bot kann auch auf die Liste der Teilnehmer zugreifen, neue Teilnehmer einladen und stummschalten.

### <a name="calls-and-online-meetings"></a>Anrufe und Onlinebesprechungen

Aus Der Sicht eines Teams-Benutzers gibt es zwei Arten von Onlinebesprechungen, ad hoc und geplant. Aus Der Sicht eines Bots sind beide Onlinebesprechungen identisch. Für einen Bot ist eine Onlinekonferenz ein Mehrparteienanruf zwischen einer Gruppe von Teilnehmern und umfasst Besprechungskoordinaten. Besprechungskoordinaten sind die Metadaten für die Besprechung, einschließlich , zugeordnet mit der `botId` `chatId` Besprechung, `joinUrl` oder , und `startTime` so `endTime` weiter.

### <a name="real-time-media"></a>Echtzeitmedien

Wenn ein Bot an einem Anruf oder einer Onlinebe besprechung teilnimmt, muss er sich mit Audio- und Videostreams beschäftigen. Wenn Benutzer in einem Anruf sprechen, sich selbst auf einer Webcam anzeigen oder ihre Bildschirme in einer Besprechung präsentieren, wird sie als Audio- und Videostreams angezeigt. Wenn ein Bot etwas so einfaches wie sagen möchte, drücken Sie **0,** um den Operator in einem Szenario mit interaktiver Sprachantwort (Interactive Voice Response, IVR) zu erreichen. WAV-Datei. Insgesamt wird dies als Medien- oder Echtzeitmedien bezeichnet.

Echtzeitmedien beziehen sich auf Szenarien, in denen Medien in Echtzeit verarbeitet werden müssen, im Gegensatz zur Wiedergabe zuvor aufgezeichneter Audio- oder Videodaten. Der Umgang mit Medienstreams, insbesondere mit Echtzeitmedienstreams, ist äußerst komplex. Microsoft hat die Echtzeitmedienplattform erstellt, um diese Szenarien zu verarbeiten und einen möglichst großen Teil der herkömmlichen hohen Belastung der Medienverarbeitung in Echtzeit zu verdingen. Wenn der Bot einen eingehenden Anruf entgegennimmt oder einem neuen oder vorhandenen Anruf beitritt, muss er der Echtzeitmedienplattform mitteilen, wie Medien behandelt werden. Wenn Sie eine IVR-Anwendung erstellen, können Sie die teure Audioverarbeitung an Microsoft ausladen. Wenn Ihr Bot den direkten Zugriff auf Medienstreams erfordert, wird dieses Szenario auch unterstützt. Es gibt zwei Arten von Medienverarbeitung:

* **Vom Dienst gehostete Medien:** Bots konzentrieren sich auf die Verwaltung von Anwendungsworkflows, z. B. Routing von Anrufen und Offload audio processing to the Microsoft Real-time Media Platform. Mit vom Dienst gehosteten Medien haben Sie mehrere Optionen zum Implementieren und Hosten Ihres Bots. Ein vom Dienst gehosteter Medienbot kann als statusfreier Dienst implementiert werden, da er keine Medien lokal verarbeitet. Vom Dienst gehostete Medienbots können die folgenden APIs verwenden:

    * `PlayPrompt` zum Wiedergeben eines Audioclips.
    * `Record` für die Aufzeichnung von Audioclips.
    * `SubscribeToTone` zum Abonnieren von DtmF-Tönen (Dual Tone Multiple Frequency).

    Beispiel: Wissen, wann ein Benutzer **0** gedrückt hat, um den Operator zu erreichen.

* **Von der Anwendung gehostete Medien:** Damit ein Bot direkten Zugriff auf die Medien erhalten kann, benötigt er eine bestimmte Graph-Berechtigung. Nachdem Ihr Bot über die Berechtigung verfügt, können Sie mit der [Echtzeitmedienbibliothek](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/)und dem [Graph calling SDK](https://microsoftgraph.github.io/microsoft-graph-comms-samples/docs/articles/index.html#graph-calling-sdk-and-stateful-client-builder) umfangreiche Echtzeitmedien und aufrufende Bots erstellen. Ein in der Anwendung gehosteter Bot muss in einer Windows-Umgebung gehostet werden. Weitere Informationen finden Sie unter [application-hosted media bots](./requirements-considerations-application-hosted-media-bots.md).

## <a name="code-sample"></a>Codebeispiel

| **Beispielname** | **Beschreibung** | **Graph** |
|---------------|----------|--------|
| Graph-Kommunikation | Graph communications to interact with Microsoft's communications platform. | [View](https://github.com/microsoftgraph/microsoft-graph-comms-samples) |

## <a name="see-also"></a>Siehe auch

- [Graph-API-Referenz](/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true)

- [Beispielapps](https://github.com/microsoftgraph/microsoft-graph-comms-samples)

- [Registrieren eines Bots, der Anrufe und Onlinebesprechungen unterstützt](./registering-calling-bot.md)

- [Diagrammberechtigungen für Anrufe und Onlinebesprechungsbots](./registering-calling-bot.md#add-graph-permissions)

- [Entwickeln von Anruf- und Online-Besprechungsbots auf Ihrem Computer](./debugging-local-testing-calling-meeting-bots.md)

- [Anforderungen und Überlegungen für von der Anwendung gehostete Medienbots](./requirements-considerations-application-hosted-media-bots.md)

- [Technische Informationen zum Behandeln eingehender Anrufbenachrichtigungen](./call-notifications.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Medienanrufe und Besprechungen in Echtzeit](~/bots/calls-and-meetings/real-time-media-concepts.md)
