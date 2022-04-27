---
title: Bots für Anrufe und Onlinebesprechungen
description: Erfahren Sie, wie Ihre Microsoft Teams-Apps mitHilfe von Sprach- und Videofunktion mithilfe von Microsoft Graph-APIs für Anrufe und Onlinebesprechungen interagieren können, und erfahren Sie mehr über Echtzeitmedienströme.
ms.topic: conceptual
ms.localizationpriority: medium
keywords: Anrufe Audio Video IVR Voice Online-Besprechungen Echtzeit-Mediendatenströme Bot
ms.openlocfilehash: e17d0c18bfb3f751a11e43780dba9f0f85441a96
ms.sourcegitcommit: 3bfd0d2c4d83f306023adb45c8a3f829f7150b1d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2022
ms.locfileid: "65073823"
---
# <a name="calls-and-online-meetings-bots"></a>Bots für Anrufe und Onlinebesprechungen

Bots können mit Teams Anrufen und Besprechungen über Echtzeit-Sprach-, Video- und Bildschirmfreigabe interagieren. Mit [Microsoft Graph-APIs für Anrufe und Onlinebesprechungen](/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true) können Teams-Apps jetzt mit Benutzern per Sprach- und Videofunktion interagieren, um die Benutzerfreundlichkeit zu verbessern. Mit diesen APIs können Sie die folgenden neuen Features hinzufügen:

* Interaktive Sprachantwort (IVR).
* Anrufsteuerung.
* Zugriff auf Echtzeit-Audio- und Videostreams, einschließlich Desktop- und App-Freigabe.

Um diese Graph-APIs in einer Teams-App zu verwenden, erstellen Sie einen Bot und geben einige zusätzliche Informationen und Berechtigungen an.

Darüber hinaus ermöglicht die Echtzeitmedienplattform Bots die Interaktion mit Teams Anrufen und Besprechungen mithilfe von Echtzeit-Sprach-, Video- und Bildschirmfreigabe. Ein Bot, der an Audio- oder Videoanrufen und Onlinebesprechungen teilnimmt, ist ein regelmäßiger Microsoft Teams Bot mit wenigen zusätzlichen Funktionen, die zum Registrieren des Bots verwendet werden.

Mit dem Teams App-Manifest mit zwei zusätzlichen Einstellungen `supportsCalling` und `supportsVideo`Graph Berechtigungen für die Microsoft App-ID Ihres Bots und der Zustimmung des Mandantenadministrators können Sie den Bot registrieren. Bei der Registrierung eines Bots für Anrufe und Besprechungen für Teams wird die Webhook-URL erwähnt, die der Webhook-Endpunkt für alle eingehenden Anrufe an Ihren Bot ist. Für einen in der Anwendung gehosteten Medienbot ist Microsoft erforderlich. Graph. Communications.Calls.Media .NET library to access the audio and video media streams, and the bot must be deployed on a Windows Server machine or Windows Server guest Operating System (OS) in Azure. Bots auf Teams unterstützen nur eine bestimmte Gruppe von Medienformaten für Audio- und Videoinhalte.

Nun müssen Sie einige Kernkonzepte, Terminologie und Konventionen verstehen.

## <a name="terminologies"></a>Terminologien

Die folgenden Kernkonzepte, Terminologie und Konventionen führen Sie durch die Verwendung von Anrufen und Bots für Onlinebesprechungen:

* Audio- oder Videoanrufe
* Anruftypen
* Signale
* Anrufe und Onlinebesprechungen
* Echtzeitmedien

### <a name="audio-or-video-calls"></a>Audio- oder Videoanrufe

Anrufe in Teams können reine Audio- oder Audio- und Videodaten sein. Anstelle von Audio- oder Videoanrufen wird der Begriff "Anruf" verwendet.

### <a name="call-types"></a>Anruftypen

Anrufe sind peer-to-peer zwischen einer Person und Ihrem Bot oder multiparty zwischen Ihrem Bot und zwei oder mehr Personen in einem Gruppenanruf.

![Anruftypen](~/assets/images/calls-and-meetings/call-types.png)

Im Folgenden sind die verschiedenen Anruftypen und -berechtigungen aufgeführt, die für den Anruf erforderlich sind:

* Ein Benutzer kann einen Peer-to-Peer-Anruf mit Ihrem Bot initiieren oder Ihren Bot zu einem vorhandenen Anruf mit mehreren Teilnehmern einladen. Der Anruf mit mehreren Teilnehmern ist in der Benutzeroberfläche Teams noch nicht aktiviert.

    > [!NOTE]
    > Vom Benutzer initiierte Aufrufe an einen Bot werden derzeit auf Microsoft Teams mobilen Plattform nicht unterstützt.

* Graph Berechtigungen sind für einen Benutzer nicht erforderlich, um einen Peer-to-Peer-Anruf mit Ihrem Bot zu initiieren. Zusätzliche Berechtigungen sind erforderlich, damit Ihr Bot an einem Anruf mit mehreren Teilnehmern teilnimmt oder dass Ihr Bot einen Peer-to-Peer-Anruf mit einem Benutzer initiiert.
* Ein Anruf kann als Peer-to-Peer beginnen und schließlich zu einem Anruf mit mehreren Teilnehmern werden. Ihr Bot kann Anrufe mit mehreren Teilnehmern initiieren, indem er andere einlädt, vorausgesetzt, Ihr Bot verfügt über die entsprechenden Berechtigungen. Wenn Ihr Bot nicht berechtigt ist, an Gruppenanrufen teilzunehmen, und wenn ein Teilnehmer einen anderen Teilnehmer zu dem Anruf hinzufügt, wird der Bot aus dem Anruf gelöscht.

### <a name="signals"></a>Signale

Es gibt zwei Arten von Signalen, eingehenden Anruf und In-Call. Im Folgenden sind die verschiedenen Merkmale von Signalen aufgeführt:

* Um einen eingehenden Anruf zu erhalten, geben Sie einen Endpunkt in Ihre Bot-Einstellungen ein. Dieser Endpunkt erhält eine Benachrichtigung, wenn ein eingehender Anruf initiiert wird. Sie können den Anruf annehmen, ablehnen oder an eine andere Person umleiten.

    ![Anrufbehandlung](~/assets/images/calls-and-meetings/call-handling.png)

* Wenn sich ein Bot in einem Anruf befindet, gibt es APIs zum Stummschalten und Aufheben der Stummschaltung des Bots und zum Starten oder Beenden der Freigabe von Video- oder Desktopinhalten für andere Teilnehmer.
* Der Bot kann auch auf die Liste der Teilnehmer zugreifen, neue Teilnehmer einladen und sie stummschalten.

### <a name="calls-and-online-meetings"></a>Anrufe und Onlinebesprechungen

Aus sicht Teams Benutzers gibt es zwei Arten von Onlinebesprechungen, ad hoc und geplant. Aus Sicht eines Bots sind beide Onlinebesprechungen identisch. Für einen Bot ist eine Onlinebesprechung ein Anruf mit mehreren Teilnehmern und umfasst Besprechungskoordinaten. Besprechungskoordinaten sind die Metadaten für die Besprechung, einschließlich `botId`, `chatId` der Besprechung zugeordnet, `joinUrl``startTime` oder `endTime`usw.

### <a name="real-time-media"></a>Echtzeitmedien

Wenn ein Bot an einem Anruf oder einer Onlinebesprechung teilnimmt, muss er sich mit Audio- und Videostreams befassen. Wenn Benutzer bei einem Anruf sprechen, sich auf einer Webcam zeigen oder ihre Bildschirme in einer Besprechung präsentieren, wird sie einem Bot als Audio- und Videostreams angezeigt. Wenn ein Bot etwas so Einfaches sagen möchte, **drücken Sie 0, um den Operator** in einem IVR-Szenario (Interactive Voice Response) zu erreichen, muss ein . WAV-Datei. Zusammenfassend wird dies als Medien oder Echtzeitmedien bezeichnet.

Echtzeitmedien beziehen sich auf Szenarien, in denen Medien in Echtzeit verarbeitet werden müssen, im Gegensatz zur Wiedergabe zuvor aufgezeichneter Audio- oder Videodaten. Der Umgang mit Mediendatenströmen, insbesondere Echtzeitmedienstreams, ist äußerst komplex. Microsoft hat die Echtzeitmedienplattform erstellt, um diese Szenarien zu behandeln und so viel wie möglich von der herkömmlichen umfangreichen Verarbeitung von Echtzeitmedien abzuheben. Wenn der Bot einen eingehenden Anruf annimmt oder einem neuen oder vorhandenen Anruf beitritt, muss er der Echtzeitmedienplattform mitteilen, wie Medien verarbeitet werden. Wenn Sie eine IVR-Anwendung erstellen, können Sie die teure Audioverarbeitung an Microsoft auslagern. Wenn Ihr Bot auch direkten Zugriff auf Mediendatenströme benötigt, wird dieses Szenario ebenfalls unterstützt. Es gibt zwei Arten der Medienverarbeitung:

* **Vom Dienst gehostete Medien**: Bots konzentrieren sich auf die Verwaltung von Anwendungsworkflows, z. B. das Routing von Anrufen und das Auslagern der Audioverarbeitung an die Microsoft Real-Time Media Platform. Mit vom Dienst gehosteten Medien haben Sie mehrere Optionen zum Implementieren und Hosten Ihres Bots. Ein vom Dienst gehosteter Medienbot kann als statusfreier Dienst implementiert werden, da er keine Medien lokal verarbeitet. Vom Dienst gehostete Medienbots können die folgenden APIs verwenden:

  * `PlayPrompt` zum Wiedergeben eines Audioclips.
  * `Record` für die Aufzeichnung von Audioclips.
  * `SubscribeToTone` zum Abonnieren von DTMF-Tönen (Dual Tone Multiple Frequency).

    Beispielsweise zu wissen, wann ein Benutzer **0** gedrückt hat, um den Operator zu erreichen.

* **Von der Anwendung gehostete Medien**: Damit ein Bot direkten Zugriff auf die Medien erhält, benötigt er eine bestimmte Graph Berechtigung. Nachdem Ihr Bot über die Berechtigung verfügt, hilft Ihnen die [Echtzeit-Medienbibliothek](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/) und das [Graph aufrufende SDK](https://microsoftgraph.github.io/microsoft-graph-comms-samples/docs/articles/index.html#graph-calling-sdk-and-stateful-client-builder) beim Erstellen umfangreicher Medien in Echtzeit und beim Aufrufen von Bots. Ein in der Anwendung gehosteter Bot muss in einer Windows-Umgebung gehostet werden. Weitere Informationen finden Sie unter [von der Anwendung gehosteten Medienbots](./requirements-considerations-application-hosted-media-bots.md).

## <a name="code-sample"></a>Codebeispiel

| **Beispielname** | **Beschreibung** | **Graph** |
|---------------|----------|--------|
| Graph Kommunikation | Graph Kommunikation für die Interaktion mit der Kommunikationsplattform von Microsoft. | [View](https://github.com/microsoftgraph/microsoft-graph-comms-samples) |

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Medienanrufe und Besprechungen in Echtzeit](~/bots/calls-and-meetings/real-time-media-concepts.md)

## <a name="see-also"></a>Siehe auch

* [Graph-API Referenz](/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true)
* [Beispielapps](https://github.com/microsoftgraph/microsoft-graph-comms-samples)
* [Registrieren eines Bots, der Anrufe und Onlinebesprechungen unterstützt](./registering-calling-bot.md)
* [Graph von Berechtigungen für Anrufe und Onlinebesprechungs-Bots](./registering-calling-bot.md#add-graph-permissions)
* [Entwickeln von Anruf- und Onlinebesprechungs-Bots auf Ihrem Computer](./debugging-local-testing-calling-meeting-bots.md)
* [Anforderungen und Überlegungen für in der Anwendung gehostete Medienbots](./requirements-considerations-application-hosted-media-bots.md)
* [Technische Informationen zur Behandlung eingehender Anrufbenachrichtigungen](./call-notifications.md)
* [Einrichten einer automatischen Telefonzentrale](/microsoftteams/create-a-phone-system-auto-attendant)
* [Einrichten der automatischen Antwort für Microsoft Teams-Räume auf Android- und Teams Videotelefongeräten](/microsoftteams/set-up-auto-answer-on-teams-android)
* [Teams Aufzeichnungsrichtlinie](/MicrosoftTeams/teams-recording-policy)