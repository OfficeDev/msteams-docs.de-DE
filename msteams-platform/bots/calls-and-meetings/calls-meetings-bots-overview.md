---
title: Bots für Anrufe und Onlinebesprechungen
description: In diesem Modul erfahren Sie, wie Ihre Microsoft Teams-Apps mit Benutzern per Sprach- und Videofunktion mithilfe von Microsoft Graph-APIs für Anrufe und Onlinebesprechungen interagieren können, und erfahren Sie mehr über Echtzeitmedienströme.
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: bbeca082a561386d6c64d08e1d303975f9746f0a
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66143851"
---
# <a name="calls-and-online-meetings-bots"></a>Bots für Anrufe und Onlinebesprechungen

Bots können per Sprach-, Video- und Bildschirmfreigabe in Echtzeit mit Teams-Anrufen und Besprechungen interagieren. Mit [Microsoft Graph-APIs für Anrufe und Onlinebesprechungen](/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true) können Teams-Apps jetzt per Sprache und Video mit Benutzern interagieren und so die Erfahrung verbessern. Mit diesen APIs können Sie die folgenden neuen Features hinzufügen:

* Interactive Voice Response (IVR).
* Anrufsteuerung.
* Zugriff auf Audio- und Videostreams in Echtzeit, einschließlich Desktop- und App-Freigabe.

Wenn Sie diese Graph-APIs in einer Teams-App verwenden möchten, erstellen Sie einen Bot und geben Sie einige zusätzliche Informationen und Berechtigungen an.

Darüber hinaus können Bots über die Echtzeitmedienplattform per Sprach-, Video- und Bildschirmfreigabe mit Teams-Anrufen und Besprechungen interagieren. Ein Bot, der an Audio- oder Videoanrufen und Onlinebesprechungen teilnimmt, ist ein regulärer Microsoft Teams-Bot mit wenigen zusätzlichen Funktionen, die zum Registrieren des Bots verwendet werden.

Mit dem Teams-App-Manifest mit zwei zusätzlichen Einstellungen `supportsCalling` und `supportsVideo`Graph-Berechtigungen für die Microsoft App-ID Ihres Bots und der Zustimmung des Mandantenadministrators können Sie den Bot registrieren. Bei der Registrierung eines Bots für Anrufe und Besprechungen für Teams wird die Webhook-URL erwähnt, die der Webhook-Endpunkt für alle eingehenden Anrufe an Ihren Bot ist. Für einen in der Anwendung gehosteten Medienbot ist die .NET-Bibliothek Microsoft.Graph.Communications.Calls.Media erforderlich, um auf die Audio- und Videomedienstreams zuzugreifen. Zudem muss der Bot auf einem Windows Server-Computer oder Windows Server-Gastbetriebssystem in Azure bereitgestellt werden. Bots in Teams unterstützen nur eine bestimmte Gruppe von Medienformaten für Audio- und Videoinhalte.

Nun müssen Sie einige Kernkonzepte, Terminologien und Konventionen verstehen.

## <a name="terminologies"></a>Terminologien

Die folgenden Kernkonzepte, Terminologien und Konventionen dienen Ihnen als Orientierungshilfe bei der Verwendung von Bots für Anrufe und Onlinebesprechungen:

* Audio- oder Videoanrufe
* Anruftypen
* Signale
* Anrufe und Onlinebesprechungen
* Echtzeitmedien

### <a name="audio-or-video-calls"></a>Audio- oder Videoanrufe

Anrufe in Teams können reine Audio- oder Audio- und Videoanrufe sein. Anstelle von Audio- oder Videoanrufen wird der Begriff „Anruf“ verwendet.

### <a name="call-types"></a>Anruftypen

Anrufe erfolgen entweder zwischen einer Person und Ihrem Bot (Peer-to-Peer) oder zwischen Ihrem Bot und mindestens zwei Personen in einem Gruppenanruf (mehrere Teilnehmer).

:::image type="content" source="~/assets/images/calls-and-meetings/call-types.png" alt-text="Anruftypen"border="true":::

Im Folgenden sind die verschiedenen Anruftypen und -berechtigungen aufgeführt, die für den Anruf erforderlich sind:

* Ein Benutzer kann einen Peer-to-Peer-Anruf mit Ihrem Bot starten oder den Bot zu einem bestehenden Anruf mit mehreren Teilnehmern einladen. Der Anruf mit mehreren Teilnehmern ist in der Teams-Benutzeroberfläche noch nicht aktiviert.

    > [!NOTE]
    > Vom Benutzer initiierte Anrufe an einen Bot werden derzeit auf der mobilen Microsoft Teams-Plattform nicht unterstützt.

* Graph-Berechtigungen sind nicht erforderlich, damit ein Benutzer einen Peer-to-Peer-Anruf mit Ihrem Bot initiiert. Zusätzliche Berechtigungen sind erforderlich, damit Ihr Bot an einem Anruf mit mehreren Teilnehmern teilnimmt oder damit der Bot einen Peer-to-Peer-Anruf mit einem Benutzer initiiert.
* Ein Anruf kann als Peer-to-Peer-Anruf beginnen und schließlich zu einem Anruf mit mehreren Teilnehmern werden. Ihr Bot kann Anrufe mit mehreren Teilnehmern initiieren, indem er andere Teilnehmer einlädt, sofern der Bot die richtigen Berechtigungen besitzt. Wenn Ihr Bot nicht die Berechtigungen besitzt, um an Gruppenanrufen teilzunehmen, und wenn ein Teilnehmer einen anderen Teilnehmer zu dem Anruf hinzufügt, wird der Bot aus dem Anruf ausgeschlossen.

### <a name="signals"></a>Signale

Es gibt zwei Arten von Signalen, eingehender Anruf und im Gespräch. Im Folgenden sind die verschiedenen Merkmale der Signale aufgeführt:

* Um einen eingehenden Anruf zu erhalten, geben Sie einen Endpunkt in Ihren Boteinstellungen ein. Dieser Endpunkt erhält eine Benachrichtigung, wenn ein eingehender Anruf initiiert wird. Sie können den Anruf annehmen, ablehnen oder an eine andere Person umleiten.

     :::image type="content" source="~/assets/images/calls-and-meetings/call-handling.png" alt-text="Anrufverarbeitung"border="true":::

* Wenn sich ein Bot in einem Anruf befindet, gibt es APIs zum Stummschalten und Aufheben der Stummschaltung des Bots und zum Starten oder Beenden der Freigabe von Video- oder Desktopinhalten für andere Teilnehmer.
* Der Bot kann auch auf die Liste der Teilnehmer zugreifen, neue Teilnehmer einladen und sie stummschalten.

### <a name="calls-and-online-meetings"></a>Anrufe und Onlinebesprechungen

Aus Sicht eines Teams-Benutzers gibt es zwei Arten von Onlinebesprechungen: ad hoc und geplant. Aus Sicht eines Bots sind beide Arten von Onlinebesprechungen identisch. Für einen Bot ist eine Onlinebesprechung ein Anruf mit mehreren Teilnehmern und umfasst Besprechungskoordinaten. Besprechungskoordinaten sind die Metadaten für die Besprechung, einschließlich `botId`, `chatId`, die der Besprechung zugeordnet ist, `joinUrl`, `startTime` oder `endTime` usw.

### <a name="real-time-media"></a>Echtzeitmedien

Wenn ein Bot an einem Anruf oder einer Onlinebesprechung teilnimmt, muss er Audio- und Videostreams handhaben. Wenn Benutzer während eines Anrufs sprechen, sich vor einer Webcam zeigen oder ihre Bildschirme in einer Besprechung präsentieren, wird dies einem Bot als Audio- und Videostreams angezeigt. Wenn ein Bot etwas so Einfaches wie **Drücken Sie 0, um den Operator zu erreichen** in einem IVR-Szenario (Interactive Voice Response) sagen möchte, muss eine .WAV-Datei abgespielt werden. Zusammenfassend wird dies als Medien oder Echtzeitmedien bezeichnet.

Echtzeitmedien beziehen sich auf Szenarien, in denen Medien im Gegensatz zur Wiedergabe zuvor aufgezeichneter Audio- oder Videodaten in Echtzeit verarbeitet werden müssen. Der Umgang mit Medienstreams, insbesondere Echtzeitmedienstreams, ist äußerst komplex. Microsoft hat die Echtzeitmedienplattform erstellt, um diese Szenarien zu handhaben und so viel wie möglich von der herkömmlichen umfangreichen Verarbeitung von Echtzeitmedien auszulagern. Wenn der Bot auf einen eingehenden Anruf antwortet oder einem neuen oder bestehenden Anruf beitritt, muss er der Echtzeitmedienplattform mitteilen, wie Medien gehandhabt werden. Wenn Sie eine IVR-Anwendung (Interactive Voice Response) erstellen, können Sie die kostspielige Audioverarbeitung an Microsoft auslagern. Benötigt Ihr Bot direkten Zugriff auf Medienstreams, wird auch dieses Szenario unterstützt. Es gibt zwei Arten der Medienverarbeitung:

* **Vom Dienst gehostete Medien**: Bots konzentrieren sich auf die Verwaltung von Anwendungsworkflows, z. B. das Routing von Anrufen und das Auslagern der Audioverarbeitung an die Microsoft Echtzeitmedienplattform. Mit vom Dienst gehosteten Medien haben Sie mehrere Optionen zum Implementieren und Hosten Ihres Bots. Ein vom Dienst gehosteter Medienbot kann als statusfreier Dienst implementiert werden, da er keine Medien lokal verarbeitet. Vom Dienst gehostete Medienbots können die folgenden APIs verwenden:

  * `PlayPrompt` zum Wiedergeben eines Audioclips.
  * `Record` zum Aufzeichnen von Audioclips.
  * `SubscribeToTone` zum Abonnieren von DTMF-Tönen (Dual Tone Multiple Frequency).

    Beispielsweise um zu wissen, wann ein Benutzer **0** gedrückt hat, um den Operator zu erreichen.

* **Von der Anwendung gehostete Medien**: Damit ein Bot direkten Zugriff auf die Medien erhält, benötigt er eine bestimmte Graph-Berechtigung. Sobald Ihr Bot die Berechtigung besitzt, helfen Ihnen die [Echtzeitmedienbibliothek](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/) und das [Graph-aufrufende SDK](https://microsoftgraph.github.io/microsoft-graph-comms-samples/docs/articles/index.html#graph-calling-sdk-and-stateful-client-builder) beim Erstellen umfangreicher Echtzeitmedien und beim Anrufen von Bots. Ein in der Anwendung gehosteter Bot muss in einer Windows-Umgebung gehostet werden. Weitere Informationen finden Sie unter [Von der Anwendung gehostete Medienbots](./requirements-considerations-application-hosted-media-bots.md).

## <a name="code-sample"></a>Codebeispiel

| **Beispielname** | **Beschreibung** | **Graph** |
|---------------|----------|--------|
| Graph-Kommunikation | Graph-Kommunikation für die Interaktion mit der Kommunikationsplattform von Microsoft. | [Anzeigen](https://github.com/microsoftgraph/microsoft-graph-comms-samples) |

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Medienanrufe und Besprechungen in Echtzeit](~/bots/calls-and-meetings/real-time-media-concepts.md)

## <a name="see-also"></a>Siehe auch

* [Graph-API-Referenz](/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true)
* [Beispielapps](https://github.com/microsoftgraph/microsoft-graph-comms-samples)
* [Registrieren eines Bots, der Anrufe und Onlinebesprechungen unterstützt](./registering-calling-bot.md)
* [Graph-Berechtigungen für Bots für Anrufe und Onlinebesprechungen](./registering-calling-bot.md#add-graph-permissions)
* [Entwickeln von Bots für Anrufe und Onlinebesprechungen auf Ihrem Computer](./debugging-local-testing-calling-meeting-bots.md)
* [Anforderungen und Überlegungen für anwendungsgehostete Medienbots](./requirements-considerations-application-hosted-media-bots.md)
* [Technische Informationen zur Behandlung eingehender Anrufbenachrichtigungen](./call-notifications.md)
* [Einrichten einer automatischen Telefonzentrale](/microsoftteams/create-a-phone-system-auto-attendant)
* [Einrichten der automatischen Antwort für Microsoft Teams-Räume auf Android- und Teams Videotelefongeräten](/microsoftteams/set-up-auto-answer-on-teams-android)
* [Teams-Aufzeichnungsrichtlinie](/MicrosoftTeams/teams-recording-policy)
* [Arbeiten mit der Kommunikations-API in Microsoft Graph](/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true)
