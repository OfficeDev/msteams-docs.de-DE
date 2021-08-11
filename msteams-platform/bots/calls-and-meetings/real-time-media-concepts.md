---
title: Echtzeit-Medienanrufe und Onlinebesprechungen mit Microsoft Teams
description: Grundlegendes zu den wichtigsten Konzepten beim Erstellen eines Bots, der Audio- und Videoanrufe in Echtzeit und Onlinebesprechungen durchführen kann.
ms.topic: conceptual
localization_priority: Normal
keywords: 'Audiostream-Videostream: Audio-/Videoanrufe bei Besprechungen in Echtzeit, medienanwendungsgehostete Medien, die vom Mediendienst gehostet werden'
ms.openlocfilehash: 23a4573c39968f3b5c53badc32fd80ecc4dc889087dd8d98253be9d46555919c
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2021
ms.locfileid: "57709545"
---
# <a name="real-time-media-calls-and-meetings-with-microsoft-teams"></a>Echtzeit-Medienanrufe und Besprechungen mit Microsoft Teams

Die Echtzeit-Medienplattform ermöglicht Bots die Interaktion mit Microsoft Teams Anrufen und Besprechungen mithilfe von Sprach-, Video- und Bildschirmfreigabe in Echtzeit. Die Echtzeit-Medienplattform ist eine erweiterte Funktion, mit der der Bot Sprach- und Videoinhaltsframes nach Frame senden und empfangen kann. Der Bot hat unformatierten Zugriff auf die Mediendatenströme Sprach-, Video- und Bildschirmfreigabe. Es gibt einfachere vom Dienst gehostete Medienbots, die für die gesamte Medienverarbeitung auf der Echtzeit-Medienplattform basieren. Bots, die Medien selbst verarbeiten, werden als von der Anwendung gehostete Medienbots bezeichnet.

Beispielsweise erhält der Bot bei einem 1:1-Anruf mit einem Bot, während der Benutzer spricht, 50 Audioframes pro Sekunde. Der Bot empfängt Audioframes mit jeweils 20 Millisekunden (ms) Audio. Ein von der Anwendung gehosteter Medienbot kann die Spracherkennung in Echtzeit durchführen, wenn die Audioframes empfangen werden. Es ist nicht erforderlich, auf eine Aufzeichnung zu warten, nachdem der Benutzer aufgehört hat zu sprechen. Der Bot kann auch Video mit hoher Auflösung senden und empfangen, einschließlich videobasierter Bildschirmfreigabeinhalte.

Die Plattform bietet eine einfache socketähnliche API für den Bot zum Senden und Empfangen von Medien. Es verarbeitet die Codierung und Decodierung von Audio- oder Videopaketen in Echtzeit. Für Audio und H.264 für Video werden Codecs wie BEISPIELSWEISE CODEC und G.722 verwendet. Die Plattform verarbeitet auch die gesamte Medienpaketverschlüsselung oder -entschlüsselung sowie die Paketnetzwerkübertragung. Der Bot befasst sich nur mit den tatsächlichen Audio- oder Videoinhalten. Ein Echtzeit-Medienbot nimmt an 1:1-Anrufen und Besprechungen mit mehreren Teilnehmern teil.

## <a name="media-session"></a>Mediensitzung

Ein Echtzeitmedienbot muss deklarieren, welche Modalitäten er unterstützen muss. Der Echtzeitmedienbot muss Unterstützung deklarieren, wenn er einen eingehenden Anruf entgegennimmt oder an einer Teams Besprechung teilnimmt. Für jede unterstützte Modalität deklariert der Bot, ob er Medien senden und empfangen, nur empfangen oder nur senden kann. Beispielsweise muss ein Bot, der für die Verarbeitung von 1:1-Teams-Anrufen entwickelt wurde, Audio senden und empfangen. Der Bot muss jedoch nur Videos senden, da er das Video des Anrufers nicht empfangen muss. Der Satz von Audio- und Videomodalitäten, der zwischen dem Bot und dem Teams Anrufer oder der Besprechung eingerichtet wurde, wird als Mediensitzung bezeichnet.

Es werden zwei Arten von Videomodalitäten unterstützt: Hauptvideo und videobasierte Bildschirmfreigabe. Das Hauptvideo wird verwendet, um das Video von der Webcam eines Benutzers zu übertragen. Mit der videobasierten Bildschirmfreigabe kann ein Benutzer den Bildschirm freigeben. Die Plattform ermöglicht es einem Bot, beide Videotypen zu senden und zu empfangen.

Wenn ein Bot an einer Teams Besprechung teil nimmt, kann er mehrere Hauptvideostreams gleichzeitig bis zu 10 pro Mediensitzung empfangen. Der Bot kann mehr als einen Teilnehmer an der Besprechung sehen.

Der nächste Abschnitt enthält Details über den Bot, der Medien als Folge von Frames sendet und empfängt.

## <a name="frames-and-frame-rate"></a>Frames und Framerate

Ein Echtzeit-Medienbot interagiert direkt mit den Audio- und Videomodalitäten einer Mediensitzung. Der Bot sendet und empfängt Medien als Folge von Frames, und jeder Frame ist eine Inhaltseinheit. Eine Sekunde Audiodaten werden als eine Abfolge von 50 Frames übertragen. Jeder Frame enthält 20 ms, d. h. 1/50 Sekunden des Sprachinhalts. Eine Sekunde des Videos wird als Sequenz von 30 Standbildern übertragen. Jedes Bild ist für nur 33,3 ms vorgesehen, also 1/30 Sekunden vor dem nächsten Videoframe. Die Anzahl der pro Sekunde übertragenen oder gerenderten Frames wird als Framerate bezeichnet.

Der nächste Abschnitt enthält Details zum Audio- und Videoformat, das in Echtzeit-Medienanrufen und Besprechungen verwendet wird.

## <a name="audio-and-video-format"></a>Audio- und Videoformat

Im Audioformat wird jede Audiosekunde als 16.000 Beispiele dargestellt, wobei jedes Beispiel 16 Bit Daten enthält. Ein 20 Ms großer Audioframe enthält 320 Beispiele mit 640 Byte Daten.

Im Videoformat werden mehrere Formate unterstützt. Zwei wichtige Eigenschaften eines Videoformats sind die Framegröße und das Farbformat. Unterstützte Framegrößen umfassen 640 x 360 Pixel, 1280 x 720 Pixel und 1920 x 1080 pixel. Unterstützte Farbformate sind NV12 mit 12 Bit pro Pixel und RGB24 mit 24 Bit pro Pixel.

Ein Videoframe mit 720 p enthält 921.600 Pixel, was 1280 Mal 720 Pixeln entspricht. Im RGB24-Farbformat wird jedes Pixel als 3 Byte dargestellt, das 24 Bit groß ist, einschließlich jeweils 1 Byte der Farbkomponenten Rot, Grün und Blau. Ein einzelner RGB24-Videoframe mit 720p erfordert 2.764.800 Bytes an Daten, was 921.600 Pixel mal 3 Bytes pro Pixel entspricht. Bei einer variablen Framerate bedeutet das Senden von RGB24-Videoframes mit 720p etwa 80 Megabyte pro Sekunde Inhalt. 80 Megabyte werden durch den H.264-Videocodec vor der Netzwerkübertragung erheblich komprimiert.

Eine erweiterte Funktion der Plattform ermöglicht es einem Bot, Videos als codierte H.264-Frames zu senden oder zu empfangen. Bots, die einen eigenen H.264-Encoder oder Decoder bereitstellen, werden unterstützt, oder der in rgb24- oder NV12-Bitmaps decodierte Videodatenstrom ist nicht erforderlich.

Der nächste Abschnitt enthält Details darüber, welche Besprechungsteilnehmer sprechen, welche aktive und dominante Referenten sind.

## <a name="active-and-dominant-speakers"></a>Aktive und dominante Lautsprecher

Wenn er einer Teams Besprechung beigetreten ist, die aus mehreren Teilnehmern besteht, kann ein Bot ermitteln, welche Besprechungsteilnehmer gerade sprechen. Aktive Lautsprecher identifizieren, welche Teilnehmer in jedem empfangenen Audioframe gehört werden. Dominante Sprecher identifizieren, welche Teilnehmer derzeit aktiv oder dominant in der Gruppenunterhaltung sind, obwohl ihre Stimme nicht in jedem Audioframe gehört wird. Die Gruppe der dominanten Sprecher kann sich ändern, wenn unterschiedliche Teilnehmer abwechselnd sprechen.

Der nächste Abschnitt enthält Details zu Videoabonnementanforderungen, die von einem Bot gestellt werden.

## <a name="video-subscription"></a>Videoabonnement

Bei einem 1:1-Anruf empfängt der Bot automatisch das Video des Anrufers, wenn der Bot für den Empfang des Videos aktiviert ist. In einer Teams Besprechung muss der Bot der Plattform angeben, welche Teilnehmer er sehen möchte. Ein Videoabonnement ist eine Anforderung des Bots, den Hauptinhalt des Videos oder der Bildschirmfreigabe eines Teilnehmers zu erhalten. Während die Teilnehmer an der Besprechung ihre Unterhaltungen führen, ändert der Bot die erforderlichen Videoabonnements. Der Bot ändert Videoabonnements basierend auf Updates des dominanten Sprechersatzes oder Benachrichtigungen, die angeben, welcher Teilnehmer derzeit bildschirmfreigabet.

Der nächste Abschnitt enthält Details dazu, was Sie installieren müssen, und die Anforderungen zum Entwickeln eines von der Anwendung gehosteten Medienbots.

## <a name="developer-resources"></a>Entwicklerressourcen

Um einen von der Anwendung gehosteten Medienbot zu entwickeln, müssen Sie die [Microsoft.Graph installieren. Calls.Media .NET library](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/) NuGet package within your Visual Studio project.

In der Anwendung gehostete Medienbots erfordern .NET oder C# und Windows Server. Weitere Informationen finden Sie unter [Anforderungen und Überlegungen für von der Anwendung gehostete Medienbots.](requirements-considerations-application-hosted-media-bots.md#c-or-net-and-windows-server-for-development)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Registrieren eines anrufenden Bots](~/bots/calls-and-meetings/registering-calling-bot.md)
