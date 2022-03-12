---
title: Anruf- und Besprechungsbot lokal debuggen
description: Erfahren Sie, wie Sie ngrok auch verwenden können, um Anrufe und Onlinebesprechungs-Bots auf Ihrem lokalen PC zu entwickeln.
ms.topic: how-to
ms.localizationpriority: medium
keywords: ngrok-Tunnel für lokale Entwicklung
ms.date: 11/18/2018
ms.openlocfilehash: c55ec6e5d7296f4ee04ae3ad3de0f9bb82cfd276
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2022
ms.locfileid: "63453362"
---
# <a name="develop-calling-and-online-meeting-bots-on-your-local-pc"></a>Entwickeln von Anruf- und Onlinebesprechungs-Bots auf Ihrem lokalen PC

In [Run and debug your app](../../concepts/build-and-test/debug.md) we explain how to use [ngrok](https://ngrok.com) to create a tunnel between your local computer and the internet. In diesem Thema erfahren Sie, wie Sie auch ngrok und Ihren lokalen PC verwenden können, um Bots zu entwickeln, die Anrufe und Onlinebesprechungen unterstützen.

Messaging-Bots verwenden HTTP, aber Anrufe und Onlinebesprechungs-Bots verwenden tcp auf niedrigerer Ebene. Ngrok unterstützt zusätzlich zu HTTP-Tunneln TCP-Tunnel.

## <a name="configure-ngrokyml"></a>Konfigurieren von ngrok.yml

Wechseln Sie zu [ngrok](https://ngrok.com) , und registrieren Sie sich für ein kostenloses Konto, oder melden Sie sich bei Ihrem vorhandenen Konto an. Nachdem Sie sich angemeldet haben, wechseln Sie zum [Dashboard](https://dashboard.ngrok.com) , und rufen Sie Ihr Authentifizierungstoken ab.

Erstellen Sie eine ngrok-Konfigurationsdatei `ngrok.yml` , und fügen Sie die folgende Zeile hinzu. Weitere Informationen dazu, wo sich die Datei befinden kann, finden Sie unter [ngrok](https://ngrok.com/docs#config):

  `authtoken: <Your-AuthToken>`

## <a name="set-up-signaling"></a>Einrichten der Signalisierung

In [Bots für Anrufe und Onlinebesprechungen](./calls-meetings-bots-overview.md) haben wir die Signalisierung von Anrufen darüber besprochen, wie Bots neue Anrufe und Ereignisse während eines Anrufs erkennen und darauf reagieren. Anrufsignalereignisse werden über HTTP POST an den aufrufenden Endpunkt des Bots gesendet.

Wie bei der Messaging-API des Bots muss Ihr Bot über das Internet erreichbar sein, damit die Echtzeitmedienplattform mit Ihrem Bot kommunizieren kann. Ngrok vereinfacht dies. Fügen Sie die folgenden Zeilen zu Ihrem ngrok.yml hinzu:

```yaml
tunnels:
    signaling:
        addr: 12345
        proto: http
```

## <a name="set-up-local-media"></a>Einrichten lokaler Medien

> [!NOTE]
> Dieser Abschnitt ist nur für in der Anwendung gehostete Medienbots erforderlich und kann übersprungen werden, wenn Sie keine Medien selbst hosten.

Von der Anwendung gehostete Medien verwenden Zertifikate und TCP-Tunnel. Die folgenden Schritte sind erforderlich:

1. Die öffentlichen TCP-Endpunkte von Ngrok verfügen über feste URLs. Sie sind `0.tcp.ngrok.io`usw `1.tcp.ngrok.io`. Sie benötigen einen DNS-CNAME-Eintrag für Ihren Dienst, der auf diese URLs verweist. Nehmen wir `0.bot.contoso.com` beispielsweise an, bezieht sich auf `0.tcp.ngrok.io`, `1.bot.contoso.com` bezieht sich `1.tcp.ngrok.io`auf usw.
2. Für Ihre URLs ist ein SSL-Zertifikat erforderlich. Um dies zu vereinfachen, verwenden Sie ein SSL-Zertifikat, das für eine Platzhalterdomäne ausgestellt wurde. In diesem Fall wäre `*.bot.contoso.com`dies . Dieses SSL-Zertifikat wird vom Media SDK überprüft, sodass es mit der öffentlichen URL Ihres Bots übereinstimmen muss. Notieren Sie sich den Fingerabdruck, und installieren Sie ihn in Ihren Computerzertifikaten.
3. Richten Sie nun einen TCP-Tunnel ein, um den Datenverkehr an localhost weiterzuleiten. Schreiben Sie die folgenden Zeilen in ngrok.yml:

    ```yaml
    media:
        addr: 8445
        proto: tcp
    ```

## <a name="start-ngrok"></a>Start ngrok

Nachdem die ngrok-Konfiguration fertig ist, starten Sie sie:

  `ngrok.exe start -all -config <Path to your ngrok.yml>`

Dadurch wird ngrok gestartet und die öffentlichen URLs definiert, die die Tunnel für Ihren localhost bereitstellen. Es folgt ein Beispiel für die Ausgabe:

```cmd
Forwarding  http://signal.ngrok.io -> localhost:12345
Forwarding  https://signal.ngrok.io -> localhost:12345
Forwarding  tcp://1.tcp.ngrok.io:12332 -> localhost:8445
```

`12345` Hier sehen Sie den Signalport, `8445` den von der Anwendung gehosteten Port und `12332` den Remotemedienport, der von ngrok verfügbar gemacht wird. Beachten Sie, dass wir eine Weiterleitung von `1.bot.contoso.com` zu `1.tcp.ngrok.io`haben. Dies wird als Medien-URL für den Bot verwendet. Natürlich sind diese Portnummern nur Beispiele, und Sie können jeden verfügbaren Port verwenden.

### <a name="update-code"></a>Aktualisieren des Codes

Nachdem ngrok eingerichtet und ausgeführt wurde, aktualisieren Sie den Code so, dass er die soeben eingerichtete Konfiguration verwendet.

#### <a name="update-signaling"></a>Signalisierung aktualisieren

Ändern Sie im BotBuilder-Aufruf die `NotificationUrl` von ngrok bereitgestellte Signal-URL.

```csharp
statefulClientBuilder.SetNotificationUrl(
    new Uri("https://signal.ngrok.io/notificationEndpoint"))
```

> [!NOTE]
> Ersetzen Sie das Signal durch das von ngrok bereitgestellte Signal und das `NotificationEndpoint` Signal durch den Controllerpfad, der die Benachrichtigung empfängt.

> [!IMPORTANT]
>
> * Die URL in `SetNotificationUrl` muss HTTPS sein.
>
> Ihre lokale Instanz muss auf HTTP-Datenverkehr am Signalport lauschen. Die Anforderungen der Plattform für Anrufe und Onlinebesprechungen erreichen den Bot als localhost HTTP-Datenverkehr, es sei denn, die End-to-End-Verschlüsselung ist eingerichtet.

#### <a name="update-media"></a>Medien aktualisieren

Aktualisieren Sie Folgendes `MediaPlatformSettings` :

```csharp
var mediaPlatform = new MediaPlatformSettings
{
    ApplicationId = <Your application id>
    MediaPlatformInstanceSettings = new MediaPlatformInstanceSettings
    {
        CertificateThumbprint = <Your SSL Cert thumbprint>,
        InstanceInternalPort = <Localhost media port>,
        InstancePublicPort = <Ngrok exposed remote media port>,
        InstancePublicIPAddress = new IPAddress(0x0),
        ServiceFqdn = <Media url for bot (eg: 1.bot.contoso.com)>,
    },
}
```

> [!NOTE]
> Der im FQDN des `MediaPlatformSettings` Diensts angegebene Zertifikatfingerabdruck muss mit dem Dienst-FQDN übereinstimmen. Aus diesem Grund sind die DNS-Einträge erforderlich.

## <a name="caveats"></a>Vorbehalte

* Kostenlose Ngrok-Konten bieten **keine** End-to-End-Verschlüsselung. Die HTTPS-Daten enden bei der ngrok-URL, und die Daten werden unverschlüsselt von ngrok zu `localhost`. Wenn Sie eine End-to-End-Verschlüsselung benötigen, erwägen Sie ein kostenpflichtiges ngrok-Konto. Weitere Informationen zum Einrichten sicherer End-to-End-Tunnel finden Sie unter [TLS-Tunnel](https://ngrok.com/docs#tls) .
* Da die Bot-Rückruf-URL dynamisch ist, müssen Sie in Szenarien mit eingehenden Anrufen häufig Ihre ngrok-Endpunkte aktualisieren. Eine Möglichkeit, dies zu beheben, ist die Verwendung eines kostenpflichtigen ngrok-Kontos, das feste Unterdomänen bereitstellt, auf die Sie Ihren Bot und die Plattform verweisen können.
* Ngrok-Tunnel können auch mit [Azure Service Fabric](/azure/service-fabric/service-fabric-overview) verwendet werden. Ein Beispiel dafür finden Sie in der [HueBot-Beispiel-App](https://github.com/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/V1.0Samples/LocalMediaSamples/HueBot/HueBot).
