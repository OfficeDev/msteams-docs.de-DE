---
title: Medienanrufe und Besprechungen in Echtzeit mit Microsoft Teams
description: Erfahren Sie, wie Bots über die Echtzeitmedienplattform mit Microsoft Teams-Anrufen und -Besprechungen interagieren können. Erkunden, Mediensitzungen, Frames und Framerate, Audio- und Videoformat, aktive Lautsprecher, Videoabonnement.
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: 8eeb30d63c982ead3e990c0dea2a2bb04a820b97
ms.sourcegitcommit: 75d0072c021609af33ce584d671f610d78b3aaef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2022
ms.locfileid: "68100917"
---
# <a name="real-time-media-calls-and-meetings-with-microsoft-teams"></a>Medienanrufe und Besprechungen in Echtzeit mit Microsoft Teams

Die Echtzeitmedienplattform ermöglicht Bots die Interaktion mit Microsoft Teams-Anrufen und -Besprechungen mithilfe von Sprach-, Videofunktionen und Bildschirmfreigabe in Echtzeit. Die Echtzeitmedienplattform ist eine erweiterte Funktion, mit der der Bot Sprach- und Videoinhalte frameweise senden und empfangen kann. Der Bot hat unformatierten Zugriff auf die Medienstreams „Sprache“, „Video“ und „Bildschirmfreigabe“. Es gibt einfachere von dienstgehostete Medienbots, die für die gesamte Medienverarbeitung auf die Echtzeitmedienplattform angewiesen sind. Bots, die Medien selbst verarbeiten, werden als anwendungsgehostete Medienbots bezeichnet.

Beispielsweise empfängt der Bot in einem 1:1-Anruf mit einem Bot, während der Benutzer spricht, 50 Audioframes pro Sekunde. Der Bot empfängt pro einzelnem Audioframe 20 Millisekunden (ms) Audio. Ein anwendungsgehosteter Medienbot kann während des Empfangs der Audioframes Spracherkennung in Echtzeit durchführen. Es ist nicht erforderlich, auf eine Aufnahme zu warten, nachdem der Benutzer aufgehört hat zu sprechen. Der Bot kann auch HD-Videos senden und empfangen, einschließlich videobasierter Bildschirmfreigabeinhalte.

Die Plattform bietet für den Bot zum Senden und Empfangen von Medien eine einfache Socket-ähnliche API. Sie behandelt die Codierung und Decodierung von Audio- oder Videopaketen in Echtzeit. Sie verwendet Codecs wie SILK und G.722 für Audio und H.264 für Video. Die Plattform übernimmt auch die gesamte Medienpaketverschlüsselung oder -entschlüsselung sowie die Paketnetzwerkübertragung. Der Bot befasst sich nur mit den tatsächlichen Audio- oder Videoinhalten. Ein Medienbot in Echtzeit nimmt an 1:1-Anrufen und Besprechungen mit mehreren Teilnehmern teil.

## <a name="media-session"></a>Mediensitzung

Ein Echtzeit-Medienbot muss deklarieren, welche Modalitäten er unterstützen muss. Der Medienbot in Echtzeit muss Unterstützung deklarieren, wenn er einen eingehenden Anruf annimmt oder an einer Teams-Besprechung teilnimmt. Für jede unterstützte Modalität deklariert der Bot, ob er Medien senden und empfangen, nur empfangen oder nur senden kann. Beispielsweise muss ein Bot, der 1:1-Teams-Anrufe verarbeitet, Sowohl Audio senden als auch empfangen. Der Bot muss jedoch nur Video senden, da er das Video des Anrufers nicht empfangen muss. Der Satz von Audio- und Videomodalitäten, die zwischen dem Bot und dem Teams-Anrufer oder der Besprechung eingerichtet wurden, wird als Mediensitzung bezeichnet.

Es werden zwei Arten von Videomodalitäten unterstützt, die Hauptvideo- und die videobasierte Bildschirmfreigabe. Das Hauptvideo wird verwendet, um das Video von der Webcam eines Benutzers zu transportieren. Die videobasierte Bildschirmfreigabe ermöglicht es einem Benutzer, den Bildschirm freizugeben. Die Plattform ermöglicht es einem Bot, beide Videotypen zu senden und zu empfangen.

Wenn ein Bot einer Teams-Besprechung beigetreten ist, kann er mehrere Hauptvideostreams gleichzeitig empfangen, bis zu 10 pro Mediensitzung. Der Bot kann mehr als einen Teilnehmer an der Besprechung sehen.

Der nächste Abschnitt enthält Details zum Senden und Empfangen von Medien als eine Sequenz von Frames durch den Bot.

## <a name="frames-and-frame-rate"></a>Frames und Bildfrequenz

Ein Echtzeit-Medienbot interagiert direkt mit den Audio- und Videomodalitäten einer Mediensitzung. Der Bot sendet und empfängt Medien als Sequenz von Frames, und jeder Frame ist eine Inhaltseinheit. Eine Sekunde Audio wird als Sequenz von 50 Frames übertragen. Jeder Frame enthält 20 ms, was 1/50 einer Sekunde Sprachinhalt entspricht. Eine Sekunde Video wird als Sequenz von 30 Standbildern übertragen. Jedes Bild soll nur für 33,3 ms angezeigt werden, d. h. 1/30 Sekunden vor dem nächsten Videoframe. Die Anzahl der pro Sekunde übertragenen oder gerenderten Frames wird als Bildfrequenz bezeichnet.

Der nächste Abschnitt enthält Details zum Audio- und Videoformat, das in Echtzeit-Medienanrufen und -besprechungen verwendet wird.

## <a name="audio-and-video-format"></a>Audio- und Videoformat

Im Audioformat wird jede Sekunde des Audios als 16.000 Sample dargestellt, wobei jedes Sample 16 Bit Daten enthält. Ein 20-ms-Audioframe enthält 320 Samples, bei denen es sich um 640 Byte Daten handelt.

Im Videoformat werden mehrere Formate unterstützt. Zwei wichtige Eigenschaften eines Videoformats sind die Framegröße und das Farbformat. Unterstützte Framegrößen sind 640 x 360 mit 360 Pixeln 1280 x 720 mit 720 Pixeln und 1920 x 1080 mit 1080 Pixeln. Zu den unterstützten Farbformaten gehören NV12 mit 12 Bit pro Pixel und RGB24 mit 24 Bit pro Pixel.

Ein 720-p-Videoframe enthält 921.600 Pixel, also 1280 mal 720 Pixel. Im RGB24-Farbformat wird jedes Pixel als 3 Bytes dargestellt, das sind 24 Bit, einschließlich jeweils 1 Byte roter, grüner und blauer Farbkomponenten. Ein einzelner RGB24-Videoframe mit 720p erfordert 2.764.800 Byte Daten, d. h. 921.600 Pixel mal 3 Byte pro Pixel. Bei einer variablen Bildfrequenz bedeutet das Senden von 720p-RGB24-Videoframes die Verarbeitung von ca. 80 Megabyte pro Sekunde an Inhalt. Die 80 Megabyte werden durch den H.264-Videocodec vor der Netzwerkübertragung erheblich komprimiert.

Eine erweiterte Funktion der Plattform ermöglicht es einem Bot, Video als codierte H.264-Frames zu senden oder zu empfangen. Bots, die ihren eigenen H.264-Encoder oder -Decoder bereitstellen, werden unterstützt, oder der Videostream, der in unformatierte RGB24- oder NV12-Bitmaps decodiert wird, ist nicht erforderlich.

Der nächste Abschnitt enthält Details dazu, welche sprechenden Besprechungsteilnehmer aktive und dominante Redner sind.

## <a name="active-and-dominant-speakers"></a>Aktive und dominante Redner

Wenn ein Bot einer aus mehreren Teilnehmern bestehen Teams-Besprechung beigetreten ist, kann er ermitteln, welche Besprechungsteilnehmer gerade sprechen. Aktive Redner identifizieren, welche Teilnehmer in jedem empfangenen Audioframe gehört werden. Dominante Redner identifizieren, welche Teilnehmer derzeit am aktivsten oder dominantesten in der Gruppenunterhaltung sind, obwohl ihre Stimme nicht in jedem Audioframe zu hören ist. Die Gruppe dominanter Redner kann sich ändern, wenn verschiedene Teilnehmer abwechselnd sprechen.

Der nächste Abschnitt enthält Details zu Videoabonnementanforderungen eines Bots.

## <a name="video-subscription"></a>Videoabonnement

In einem 1:1-Anruf empfängt der Bot automatisch das Video des Anrufers, wenn der Bot für den Empfang des Videos aktiviert ist. In einer Teams-Besprechung muss der Bot der Plattform angeben, welche Teilnehmer er sehen möchte. Ein Videoabonnement ist eine Anforderung des Bots, die wichtigsten Video- oder Bildschirmfreigabeinhalte eines Teilnehmers zu erhalten. Während die Teilnehmer der Besprechung ihre Unterhaltung führen, ändert der Bot seine erforderlichen Videoabonnements. Der Bot ändert Videoabonnements auf Grundlage von Updates der Einstellung des dominanten Redners oder Benachrichtigungen, die angeben, welcher Teilnehmer gerade eine Bildschirmfreigabe durchführt.

Im nächsten Abschnitt finden Sie Details dazu was Sie installieren müssen und zu den Anforderungen an die Entwicklung eines anwendungsgehosteten Medienbots.

## <a name="developer-resources"></a>Developer-Ressourcen

Um einen anwendungsgehosteten Medienbot zu entwickeln, müssen Sie das NuGet-Paket [Microsoft.Graph Calls.Media .NET-Bibliothek](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/) in Ihrem Visual Studio-Projekt installieren.

Anwendungsgehostete Medienbots erfordern .NET oder C# und Windows Server. Weitere Informationen finden Sie unter [Anforderungen und Überlegungen für anwendungsgehostete Medienbots](requirements-considerations-application-hosted-media-bots.md#c-or-net-and-windows-server-for-development).

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Registrieren eines anrufenden Bots](~/bots/calls-and-meetings/registering-calling-bot.md)

## <a name="see-also"></a>Siehe auch

[Unterstützte Medienformate für Bots](~/resources/media-formats.md)
