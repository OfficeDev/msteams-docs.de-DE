---
title: Anruf- und Besprechungsbot lokal debuggen
description: Erfahren Sie, wie Sie ngrok auch zum Entwickeln von Anrufen und Online-Besprechungsbots auf Ihrem lokalen PC verwenden können.
ms.topic: how-to
keywords: ngrok-Tunnel für lokale Entwicklung
ms.date: 11/18/2018
ms.openlocfilehash: d61c380fda941618a769ad3fffa053b2a4800de9
ms.sourcegitcommit: 5b3ba227c2e5e6f7a2c629961993f168da6a504d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2021
ms.locfileid: "51634727"
---
# <a name="develop-calling-and-online-meeting-bots-on-your-local-pc"></a>Entwickeln von Anruf- und Online-Besprechungsbots auf Ihrem lokalen PC

In [Run and debug your app](../../concepts/build-and-test/debug.md) we explain how to use [ngrok](https://ngrok.com) to create a tunnel between your local computer and the internet. In diesem Thema erfahren Sie, wie Sie ngrok und Ihren lokalen PC auch verwenden können, um Bots zu entwickeln, die Anrufe und Onlinebesprechungen unterstützen.

Messaging bots use HTTP, but calls and online meeting bots use the lower-level TCP. Ngrok unterstützt zusätzlich zu HTTP-Tunneln TCP-Tunnel. 

## <a name="configure-ngrokyml"></a>Konfigurieren von ngrok.yml

Wechseln Sie [zu ngrok,](https://ngrok.com) und registrieren Sie sich für ein kostenloses Konto, oder melden Sie sich bei Ihrem vorhandenen Konto an. Nachdem Sie sich angemeldet haben, wechseln Sie zum [Dashboard,](https://dashboard.ngrok.com) und erhalten Sie Ihr Authentifizierungstoken.

Erstellen Sie eine ngrok-Konfigurationsdatei, `ngrok.yml` und fügen Sie die folgende Zeile hinzu. Weitere Informationen zum Ort der Datei finden Sie unter [ngrok](https://ngrok.com/docs#config):

  `authtoken: <Your-AuthToken>`

## <a name="set-up-signaling"></a>Einrichten der Signalisierung

In [Den Bots](./calls-meetings-bots-overview.md)für Anrufe und Onlinebesprechungen haben wir die Anrufsignalisierung darüber erörtert, wie Bots neue Anrufe und Ereignisse während eines Anrufs erkennen und darauf reagieren. Anrufsignalereignisse werden über HTTP POST an den aufrufenden Endpunkt des Bots gesendet.

Wie bei der Messaging-API des Bots muss Ihr Bot über das Internet erreichbar sein, damit die Echtzeitmedienplattform mit Ihrem Bot sprechen kann. Ngrok macht dies einfach. Fügen Sie ihrer ngrok.yml die folgenden Zeilen hinzu:

```yaml
tunnels:
    signaling:
        addr: 12345
        proto: http
```

## <a name="set-up-local-media"></a>Einrichten lokaler Medien

> [!NOTE]
> Dieser Abschnitt ist nur für von Anwendungen gehostete Medienbots erforderlich und kann übersprungen werden, wenn Sie medien nicht selbst hosten.

Von der Anwendung gehostete Medien verwenden Zertifikate und TCP-Tunnel. Die folgenden Schritte sind erforderlich:

1. Die öffentlichen TCP-Endpunkte von Ngrok verfügen über feste URLs. Sie sind `0.tcp.ngrok.io` `1.tcp.ngrok.io` , und so weiter. Sie müssen über einen DNS-CNAME-Eintrag für Ihren Dienst verfügen, der auf diese URLs verweist. Angenommen, bezieht sich `0.bot.contoso.com` auf `0.tcp.ngrok.io` , `1.bot.contoso.com` bezieht sich auf , und `1.tcp.ngrok.io` so weiter.
2. Für Ihre URLs ist ein SSL-Zertifikat erforderlich. Um dies zu einfach zu machen, verwenden Sie ein SSL-Zertifikat, das für eine Platzhalterdomäne ausgestellt wurde. In diesem Fall wäre es `*.bot.contoso.com` . Dieses SSL-Zertifikat wird vom media SDK überprüft, daher muss es mit der öffentlichen URL Ihres Bots übereinstimmen. Notieren Sie sich den Fingerabdruck, und installieren Sie ihn in Ihren Computerzertifikaten.
3. Richten Sie nun einen TCP-Tunnel ein, um den Datenverkehr an localhost weiter zu weiterleiten. Schreiben Sie die folgenden Zeilen in ngrok.yml:

    ```yaml
    media:
        addr: 8445
        proto: tcp
    ```

## <a name="start-ngrok"></a>ngrok starten

Nachdem die ngrok-Konfiguration nun bereit ist, starten Sie sie:

  `ngrok.exe start -all -config <Path to your ngrok.yml>`

Dadurch wird ngrok gestartet und die öffentlichen URLs definiert, die die Tunnel für Ihren localhost bereitstellen. Es folgt ein Beispiel für die Ausgabe:

```cmd
Forwarding  http://signal.ngrok.io -> localhost:12345
Forwarding  https://signal.ngrok.io -> localhost:12345
Forwarding  tcp://1.tcp.ngrok.io:12332 -> localhost:8445
```

Hier ist der Signalingport, der von der Anwendung gehostete Port und der von ngrok verfügbar gemachte `12345` `8445` `12332` Remotemedienport. Beachten Sie, dass wir eine Weiterleitung von `1.bot.contoso.com` zu `1.tcp.ngrok.io` haben. Dies wird als Medien-URL für den Bot verwendet. Natürlich sind diese Portnummern nur Beispiele, und Sie können jeden verfügbaren Port verwenden.

### <a name="update-code"></a>Aktualisieren des Codes

Nachdem ngrok ausgeführt wurde, aktualisieren Sie den Code so, dass er die konfiguration verwendet, die Sie gerade eingerichtet haben.

#### <a name="update-signaling"></a>Updatesignalisierung

Ändern Sie im BotBuilder-Aufruf die in die von ngrok bereitgestellte `NotificationUrl` Signal-URL.

```csharp
statefulClientBuilder.SetNotificationUrl(
    new Uri("https://signal.ngrok.io/notificationEndpoint"))
```

> [!NOTE]
> Ersetzen Sie das Signal durch das von ngrok bereitgestellte signal und das durch den `NotificationEndpoint` Controllerpfad, der eine Benachrichtigung empfängt.

> [!IMPORTANT]
> * Die URL in `SetNotificationUrl` muss HTTPS sein.
> 
> Ihre lokale Instanz muss den HTTP-Datenverkehr am Signalport abhören. Die Anforderungen der Anruf- und Onlinebesprechungsplattform erreichen den Bot als localhost-HTTP-Datenverkehr, es sei denn, die End-to-End-Verschlüsselung ist eingerichtet.

#### <a name="update-media"></a>Medien aktualisieren

Aktualisieren Sie `MediaPlatformSettings` Ihre wie folgt:

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
> Der in der bereitgestellte Zertifikatfingerabdruck `MediaPlatformSettings` muss mit dem Dienst-FQDN übereinstimmen. Deshalb sind die DNS-Einträge erforderlich.

## <a name="caveats"></a>Vorbehalte

- Kostenlose Ngrok-Konten **bieten keine** End-to-End-Verschlüsselung. Die HTTPS-Daten enden an der ngrok-URL, und die Daten werden unverschlüsselt von ngrok zu `localhost` übertragen. Wenn Sie eine End-to-End-Verschlüsselung benötigen, sollten Sie ein kostenpflichtiges ngrok-Konto in Betracht ziehen. Schritte zum Einrichten sicherer End-to-End-Tunnel finden Sie unter [TLS-Tunnel.](https://ngrok.com/docs#tls)
- Da die Bot-Rückruf-URL dynamisch ist, müssen Sie ihre ngrok-Endpunkte für eingehende Anrufe häufig aktualisieren. Eine Möglichkeit, dies zu beheben, ist die Verwendung eines kostenpflichtigen ngrok-Kontos, das feste Unterdomänen zur Verfügung stellt, auf die Sie Ihren Bot und die Plattform verweisen können.
- Ngrok-Tunnel können auch mit [Azure Service Fabric verwendet werden.](/azure/service-fabric/service-fabric-overview) Ein Beispiel dafür finden Sie in der [HueBot-Beispiel-App](/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/LocalMediaSamples/HueBot/HueBot).
