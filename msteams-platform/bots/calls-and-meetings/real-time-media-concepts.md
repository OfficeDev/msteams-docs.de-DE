---
title: Echtzeitmedienanrufe und Onlinebesprechungen mit Microsoft Teams
description: Grundlegendes zu den wichtigsten Konzepten beim Erstellen von Bots, die Audio- und Videoanrufe und Onlinebesprechungen in Echtzeit durchführen können.
ms.topic: conceptual
localization_priority: Normal
keywords: Audiostream video stream audio/video calling meeting real-time media application-hosted media service-hosted media media
ms.openlocfilehash: deedc47f67fe6848cf7f84457247d2271257e3f0
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020155"
---
# <a name="real-time-media-calls-and-meetings-with-microsoft-teams"></a>Echtzeitmedienanrufe und Besprechungen mit Microsoft Teams

Die Echtzeitmedienplattform ermöglicht Bots die Interaktion mit Microsoft Teams Anrufen und Besprechungen mithilfe von Echtzeit-Sprach-, Video- und Bildschirmfreigabe. Dies ist eine erweiterte Funktion, mit der der Bot Sprach- und Videoinhalte frame für Frame senden und empfangen kann. Der Bot hat unformatierte Zugriff auf die Medienstreams für Sprach-, Video- und Bildschirmfreigabe. Es gibt einfachere vom Dienst gehostete Medienbots, die für alle Medienverarbeitungen auf der Echtzeitmedienplattform beruhen. Bots, die Medien selbst verarbeiten, werden als anwendungsgehostte Medienbots bezeichnet.

Beispielsweise empfängt der Bot bei einem 1:1-Anruf mit einem Bot, wie der Benutzer spricht, 50 Audioframes pro Sekunde, bei denen jeder Frame 20 Millisekunden Audio enthält. Ein von der Anwendung gehosteter Medienbot kann die Spracherkennung in Echtzeit ausführen, wenn die Audioframes empfangen werden, anstatt auf eine Aufzeichnung warten zu müssen, nachdem der Benutzer nicht mehr gesprochen hat. Der Bot kann auch Videos mit hoher Auflösung senden und empfangen, einschließlich videobasierter Bildschirmfreigabeinhalte.

Die Plattform bietet eine einfache socket- like-API für den Bot zum Senden und Empfangen von Medien. Es verarbeitet die Echtzeitcodierung und -decodierung von Audio- oder Videopaketen mithilfe von Codecs wie SILK und G.722 für Audio und H.264 für Video. Die Plattform übernimmt auch die verschlüsselungs- oder entschlüsselte Medienpaket- und Paketnetzwerkübertragung automatisch. Der Bot betrifft nur die tatsächlichen Audio- oder Videoinhalte. Ein Echtzeitmedienbot nimmt an 1:1-Anrufen sowie Besprechungen mit mehreren Teilnehmern teil.

## <a name="media-session"></a>Mediensitzung

Wenn ein Medienbot in Echtzeit einen eingehenden Anruf beantwortet oder an einer Teams teiln, muss er deklarieren, welche Modalitäten er unterstützen muss. Für jede unterstützte Modalität gibt der Bot an, ob er Medien senden und empfangen, nur empfangen oder nur senden kann. Beispielsweise muss ein Bot, der 1:1-Teams-Anrufe verarbeiten soll, Audio senden und empfangen, aber nur Video senden, da das Video des Anrufers nicht empfangen werden muss. Der Satz von Audio- und Videomodalitäten, die zwischen dem Bot und dem Teams oder Besprechung eingerichtet werden, wird als Mediensitzung bezeichnet.

Es werden zwei Arten von Videomodalitäten unterstützt, hauptvideo- und videobasierte Bildschirmfreigabe. Das Hauptvideo wird verwendet, um das Video von der Webcam eines Benutzers zu transportieren. Die videobasierte Bildschirmfreigabe ermöglicht es einem Benutzer, seinen Bildschirm als Videostream zu teilen. Die Plattform ermöglicht es einem Bot, beide Videotypen zu senden und zu empfangen.

Wenn ein Bot einer Teams beigetreten ist, kann er mehrere Hauptvideostreams gleichzeitig bis zu zehn pro Mediensitzung empfangen. Dadurch kann der Bot mehr als einen Teilnehmer an der Besprechung sehen.

Der nächste Abschnitt enthält Details zum Senden und Empfangen von Medien als Sequenz von Frames.

## <a name="frames-and-frame-rate"></a>Frames und Framerate

Ein Echtzeitmedienbot interagiert direkt mit den Audio- und Videomodalitäten einer Mediensitzung. Dies bedeutet, dass der Bot Medien als Sequenz von Frames sendet und empfängt, wobei jeder Frame eine Inhaltseinheit darstellt. Eine Sekunde Audio wird als Sequenz von 50 Frames übertragen, jeder Frame enthält 20 ms, d. h. 1/50 einer Sekunde Sprachinhalt. Eine Sekunde des Videos wird als Sequenz von 30 Bildern übertragen, die jeweils nur für 33,3 ms angezeigt werden sollen, d. h. 1/30 sekunden, bevor der nächste Videoframe angezeigt wird. Die Anzahl der pro Sekunde übertragenen oder gerenderten Frames wird als Framerate bezeichnet.

Der nächste Abschnitt enthält Details zum Audio- und Videoformat, das in Echtzeitmedienanrufen und Besprechungen verwendet wird.

## <a name="audio-and-video-format"></a>Audio- und Videoformat

Im Audioformat wird jede Sekunde des Audios als 16.000 Samples dargestellt, jedes Beispiel enthält 16-Bit-Daten. Ein 20 ms-Audioframe enthält 320 Samples, die 640 Byte Daten sind.

Im Videoformat werden mehrere Formate unterstützt. Zwei wichtige Eigenschaften eines Videoformats sind die Framegröße und das Farbformat. Unterstützte Framegrößen sind 640 x 360, d. h. 360 Pixel, 1280 x 720 Pixel und 1920 x 1080 Pixel. Unterstützte Farbformate sind NV12 mit 12 Bit pro Pixel und RGB24 mit 24 Bit pro Pixel.

Ein 720p-Videoframe enthält 921.600 Pixel, also 1280 mal 720 Pixel. Im RGB24-Farbformat wird jedes Pixel als 3 Byte dargestellt, d. h. 24 Bit, die jeweils ein Byte aus roten, grünen und blauen Farbkomponenten enthalten. Daher erfordert ein einzelner 720p RGB24-Videoframe 2.764.800 Byte Daten, also 921.600 Pixel mal 3 Byte pro Pixel. Bei einer Framerate von 30 fps bedeutet das Senden von 720p RGB24-Videoframes die Verarbeitung von ungefähr 80 Megabyte pro Sekunde des Inhalts, der vom H.264-Videocodec vor der Netzwerkübertragung erheblich komprimiert wird.

Eine erweiterte Funktion der Plattform ermöglicht es einem Bot, Video als codierte H.264-Frames zu senden oder zu empfangen. Dies unterstützt Bots, die einen eigenen H.264-Encoder oder Decoder bereitstellen oder den Videodatenstrom nicht in unformatierte RGB24- oder NV12-Bitmaps decodieren müssen.

Der nächste Abschnitt enthält Details dazu, welche Besprechungsteilnehmer sprechen, die aktive und dominante Referenten sind.

## <a name="active-and-dominant-speakers"></a>Aktive und dominante Lautsprecher

Wenn ein Bot an einer Teams, die aus mehreren Teilnehmern besteht, verbunden ist, kann er bestimmen, welche Besprechungsteilnehmer gerade sprechen. Aktive Lautsprecher identifizieren, welche Teilnehmer in jedem empfangenen Audioframe gehört werden. Dominante Lautsprecher identifizieren, welche Teilnehmer derzeit am aktivsten oder dominantesten in der Gruppenbesprechung sind, auch wenn ihre Stimme nicht in jedem Audioframe gehört wird. Die Gruppe dominanter Lautsprecher kann sich ändern, wenn unterschiedliche Teilnehmer abwechselnd sprechen.

Der nächste Abschnitt enthält Details zu Videoabonnementanforderungen, die von einem Bot vorgenommen wurden.

## <a name="video-subscription"></a>Videoabonnement

Bei einem 1:1-Anruf empfängt der Bot automatisch das Video des Anrufers, wenn der Bot für den Empfang des Videos aktiviert ist. In einer Teams muss der Bot der Plattform angeben, welche Teilnehmer er sehen möchte. Ein Videoabonnement ist eine Anforderung des Bots, die Hauptvideo- oder Bildschirmfreigabeinhalte eines Teilnehmers zu erhalten. Während die Teilnehmer der Besprechung ihre Unterhaltung führen, ändert der Bot seine gewünschten Videoabonnements basierend auf Updates des dominanten Lautsprechersets oder Benachrichtigungen, die angeben, welcher Teilnehmer gerade bildschirmfreigaben.

Der nächste Abschnitt enthält Details dazu, was Sie installieren müssen, und die Anforderungen für die Entwicklung eines vom Anwendungshosting gehosteten Medienbots.

## <a name="developer-resources"></a>Entwicklerressourcen

Zum Entwickeln eines von einer Anwendung gehosteten Medienbots müssen Sie [microsoft.Graph. Calls.Media .NET library](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/) NuGet paket innerhalb Visual Studio Projekt.

Anwendungsgehostte Medienbots erfordern .NET oder C# und Windows Server. Weitere Informationen finden Sie unter [Anforderungen und Überlegungen für anwendungsgehostte Medienbots](requirements-considerations-application-hosted-media-bots.md#c-or-net-and-windows-server-for-development).

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Registrieren eines anrufenden Bots](~/bots/calls-and-meetings/registering-calling-bot.md)
