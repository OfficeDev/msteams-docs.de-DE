---
title: Echt Zeit Medien Anrufe und Onlinebesprechungen mit Microsoft Teams
description: Grundlegende Konzepte zum Erstellen von bot, die in Echtzeit Audio-und Videoanrufe und Onlinebesprechungen durchführen können.
keywords: Audio Stream Video Stream Audio/Videoanrufe Treffen in Echtzeit Medien Anwendung – gehosteter Mediendienst – gehostete Medien
ms.openlocfilehash: 0ec99d1caa8810d292170c7c70a1518de7301873
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674244"
---
# <a name="real-time-media-calls-and-meetings-with-microsoft-teams"></a>Echt Zeit Medien Anrufe und Besprechungen mit Microsoft Teams

Die Echtzeit-Medienplattform ermöglicht Bots die Interaktion mit Microsoft Teams-anrufen und Besprechungen mit Echt Zeit Sprache, Video und Bildschirmfreigabe. Dies ist eine erweiterte Funktion, mit der der bot den Sprach-und Videoinhalt *Frame für Frame*senden und empfangen kann. Der bot verfügt über einen "RAW"-Zugriff auf die Mediendatenströme Voice, Video und Screen Sharing. (Bots, die Medien selbst verarbeiten, werden als _Anwendungs gehostete Medien_ Bots bezeichnet, im Gegensatz zu einfacheren _Dienst gehosteten Medien_ Bots, die auf der Echt Zeit Medienplattform für die gesamte Medienverarbeitung basieren.)

Beispielsweise erhält der bot in einem 1:1-Aufruf mit einem bot, wie der Benutzer spricht, 50-Audioframes pro Sekunde, wobei jeder Frame 20 Millisekunden (MS) Audio enthält. Ein von der Anwendung gehosteter Medien-bot kann die Spracherkennung in Echtzeit durchführen, wenn die Audioframes empfangen werden, anstatt auf eine Aufzeichnung warten zu müssen, nachdem der Benutzer die Sprechzeit angehalten hat. Der Bot kann auch Video mit hoher Auflösung, einschließlich videobasierter Bildschirmfreigabe Inhalte, senden und empfangen.

Die Plattform bietet eine einfache Socket-ähnliche API für den bot zum Senden und empfangen von Medien und behandelt die Echtzeitcodierung und-Decodierung von Audio/Video-Paketen mithilfe von Codecs wie Silk und G. 722 für Audio und H. 264 für Video. Die Plattform verarbeitet auch die gesamte Medienpaket Verschlüsselung/-Entschlüsselung und die Paketnetzwerk Übertragung automatisch, sodass sich der bot nur mit dem tatsächlichen Audio/Video-Inhalt befassen muss. Ein Echtzeit-Medien-bot kann an 1:1 anrufen sowie Besprechungen mit mehreren Teilnehmern teilnehmen.

In diesem Artikel werden wichtige Konzepte im Zusammenhang mit dem Erstellen eines bot vorgestellt, der Audio-und Videoanrufe in Echtzeit mit Microsoft Teams durchführen kann.

## <a name="media-session"></a>Mediensitzung

Wenn ein Echtzeit-Medien-bot einen eingehenden Anruf beantwortet oder einer Microsoft Teams-Besprechung Beitritt, muss er deklarieren, welche Modalitäten er unterstützen möchte. Für jede unterstützte Modalität deklariert der bot, ob er Medien senden und empfangen, nur empfangen oder nur senden kann. Beispielsweise möchte ein bot, der 1:1-Teams-Anrufe verarbeiten soll, sowohl Audio Senden als auch empfangen, aber nur Video *senden* (da er das Video des Anrufers nicht erhalten muss). Die Audio-und Video Modalitäten, die zwischen dem bot und dem Anrufer oder der Besprechung der Teams hergestellt werden, werden als **Mediensitzung**bezeichnet.

Es werden zwei Arten von Video Modalitäten unterstützt: **Hauptvideo** und **videobasierte Bildschirmfreigabe**. Das Hauptvideo wird verwendet, um das Video von der Webcam eines Benutzers zu transportieren. Die videobasierte Bildschirmfreigabe ermöglicht einem Benutzer, seinen Bildschirm als Videostream freizugeben. Die Plattform ermöglicht es einem bot, *beide* Videotypen zu senden und/oder zu empfangen.

Wenn ein bot mit einer Microsoft Teams-Besprechung verbunden ist, kann er mehrere Haupt Videostreams gleichzeitig empfangen – bis zu 10 pro Mediensitzung. Dadurch kann der bot mehr als einen Teilnehmer an der Besprechung "anzeigen".

## <a name="frames-and-frame-rate"></a>Rahmen und Framerate

Ein Echtzeit-Medien-bot interagiert direkt mit den Audio-und Video Modalitäten einer Mediensitzung. Dies bedeutet, dass der bot das Senden und/oder empfangen von Medien als Sequenz von **Frames**sendet, wobei jedes Frame eine Inhaltseinheit darstellt. Eine Sekunde der Audiodaten kann als Sequenz von 50-Frames übertragen werden, wobei jeder Frame 20 Millisekunden (MS) – 1/50 Sekunden – des sprach Inhalts enthält. Ein zweiter Video Wert kann als Sequenz von 30 Standbildern in Scheiben geschnitten werden, die jeweils für nur 33,3 ms – 1/30th einer Sekunde – angezeigt werden sollen, bevor der nächste Videorahmen angezeigt wird. Die Anzahl der Frames, die pro Sekunde übermittelt oder gerendert werden, wird als **Frame Rate**bezeichnet. "30 bps" gibt 30 Frames pro Sekunde an.

## <a name="audio-format"></a>Audio-Format

Jede Sekunde von Audio wird als 16.000- **Beispiele**dargestellt, wobei jedes Beispiel 16 Bit Daten enthält. Ein 20ms-audioframe enthält 320-Beispiele (640 Byte Daten).

## <a name="video-format"></a>Video Format

Für Video werden verschiedene Formate unterstützt. Zwei wichtige Eigenschaften eines Video Formats sind die **Framegröße** und das **Farbformat**. Unterstützte Framegrößen sind 640 x 360 ("360p"), 1280X720 ("720p") und 1920x1080 ("1080p"). Unterstützte Farbformate sind NV12 (12 Bit pro Pixel) und RGB24 (24 Bits pro Pixel).

Ein "720p"-Videorahmen enthält 921.600 Pixel (1280 Mal 720). Im RGB24-Farbformat wird jedes Pixel als 3 Byte (24-Bit) dargestellt, das jeweils ein Byte mit jeweils roten, grünen und blauen Farbkomponenten umfasst. Daher erfordert ein einzelnes 720p RGB24-Videoframe 2.764.800 Bytes Daten (921.600 Pixel mal 3 Byte/Pixel). Bei einer Bildrate von 30 bps bedeutet das Senden von 720p RGB24-Videoframes das Verarbeiten von ungefähr 80 MB/s Inhalt (was durch den H. 264-Videocodec vor der Netzwerkübertragung wesentlich komprimiert wird).

Eine erweiterte Funktionalität der Plattform ermöglicht es einem bot, Video als **codierte** H. 264-Frames zu senden/empfangen. Dadurch werden Bots unterstützt, die ihren eigenen H. 264-Encoder/-Decoder bereitstellen, oder der Videostream muss nicht in RAW-RGB24-oder NV12-Bitmaps decodiert werden.

## <a name="active-and-dominant-speakers"></a>Aktive und dominante Lautsprecher

Wenn Sie einer Teambesprechung mit mehreren Teilnehmern beigetreten sind, kann ein bot erkennen, welche Besprechungsteilnehmer derzeit sprechen. **Aktive Lautsprecher** bestimmen, welche Teilnehmer in jedem empfangenen Audioframes gehört werden. **Dominierende Lautsprecher** bestimmen, welche Teilnehmer derzeit am aktivsten (oder "dominanten") in der Gruppenunterhaltung sind, obwohl ihre Stimme in keinem Audioframes möglicherweise nicht gehört wird. Die Gruppe der dominanten Lautsprecher kann sich ändern, wenn sich verschiedene Teilnehmer im Gespräch befinden.

## <a name="video-subscription"></a>Video Abonnement

In einem 1:1-Aufruf erhält der bot automatisch das Video des Anrufers, wenn der bot für den Empfang von Video aktiviert ist. In einer Teams-Besprechung muss der bot der Plattform anzeigen, welche Teilnehmer er sehen möchte. Bei einem **Video Abonnement** handelt es sich um eine Anforderung des bot, den Hauptvideo-oder Bildschirmfreigabe Inhalt eines Teilnehmers zu erhalten. Während die Teilnehmer an der Besprechung Ihre Unterhaltungen durchführen, kann der bot seine gewünschten Video Abonnements basierend auf Aktualisierungen des dominanten Lautsprechersatzes oder Benachrichtigungen ändern, die angeben, welcher Teilnehmer derzeit Bildschirmfreigabe ist.

## <a name="developer-resources"></a>Entwicklerressourcen

Um einen von der Anwendung gehosteten Medien-bot zu entwickeln, müssen Sie das folgende NuGet-Paket in Ihrem Visual Studio-Projekt installieren:

- [Microsoft. Graph. Calls. Media .NET-Bibliothek](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/)

Von der Anwendung gehostete Medien-Bots benötigen .NET/C# und Windows Server, wie in [Anforderungen und Überlegungen für von Anwendungen gehostete Medien Bots](requirements-considerations-application-hosted-media-bots.md#application-hosted-media-bot-development-requires-cnet-and-windows-server)ausführlich beschrieben.
