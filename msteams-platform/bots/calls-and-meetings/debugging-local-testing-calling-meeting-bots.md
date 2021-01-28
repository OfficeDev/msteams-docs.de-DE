---
title: Anruf- und Besprechungsbot lokal debuggen
description: Erfahren Sie, wie Sie ngrok auch zum Entwickeln von Anrufen und Online-Besprechungsbots auf Ihrem lokalen PC verwenden können.
ms.topic: how-to
keywords: Ngrok-Tunnel für lokale Entwicklung
ms.date: 11/18/2018
ms.openlocfilehash: e9b77df18c8d80f02134dc7912b5796023082039
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014306"
---
# <a name="how-to-develop-calling-and-online-meeting-bots-on-your-local-pc"></a>So entwickeln Sie Anruf- und Online-Besprechungsbots auf Ihrem lokalen PC

In [Run and debug your app](../../concepts/build-and-test/debug.md) we explain how to use [ngrok](https://ngrok.com) to create a tunnel between your local computer and the internet. In diesem Thema erfahren Sie, wie Sie ngrok und Ihren lokalen PC auch zum Entwickeln von Bots verwenden können, die Anrufe und Onlinebesprechungen unterstützen.

Messaging bots use HTTP, but calls and online meeting bots use the lower-level TCP. Ngrok unterstützt #A0 zusätzlich zu HTTP-Tunneln. Wie das geht, erfahren Sie weiter unten.

## <a name="configuring-ngrokyml"></a>Konfigurieren von ngrok.yml

Wechseln Sie [zu ngrok,](https://ngrok.com) und registrieren Sie sich für ein kostenloses Konto, oder melden Sie sich bei Ihrem vorhandenen Konto an. Nachdem Sie sich angemeldet haben, wechseln Sie zum [Dashboard,](https://dashboard.ngrok.com) und erhalten Sie Ihr Authentifizierungstoken.

Erstellen Sie eine ngrok-Konfigurationsdatei (hier finden Sie weitere Informationen dazu, wo sich diese Datei befinden kann), und fügen Sie `ngrok.yml` diese Zeile hinzu: [](https://ngrok.com/docs#config)

  `authtoken: <Your-AuthToken>`

## <a name="setting-up-signaling"></a>Einrichten der Signalisierung

In ["Anrufe" und "Onlinebesprechungsbots"](./calls-meetings-bots-overview.md)haben wir die Anrufsignalisierung besprochen– wie Bots neue Anrufe und Ereignisse während eines Anrufs erkennen und darauf reagieren. Anrufsignalereignisse werden über HTTP POST an den aufrufenden Endpunkt des Bots gesendet.

Wie bei der Messaging-API des Bots muss Ihr Bot über das Internet erreichbar sein, damit die Medienplattform in Echtzeit mit Ihrem Bot sprechen kann. Ngrok macht dies einfach – fügen Sie ihrer ngrok.yml die folgenden Zeilen hinzu:

```yaml
tunnels:
    signaling:
        addr: 12345
        proto: http
```

## <a name="setting-up-local-media"></a>Einrichten lokaler Medien

> [!NOTE]
> Dieser Abschnitt ist nur für in der Anwendung gehostete Medienbots erforderlich und kann übersprungen werden, wenn Sie medien nicht selbst hosten.

In der Anwendung gehostete Medien verwenden Zertifikate und TCP-Tunnel. Die folgenden Schritte sind erforderlich:

- Die öffentlichen TCP-Endpunkte von Ngrok verfügen über feste URLs. Sie sind `0.tcp.ngrok.io` , `1.tcp.ngrok.io` und so weiter. Sie sollten über einen DNS-CNAME-Eintrag für Ihren Dienst verfügen, der auf diese URLs verweist. In diesem Beispiel bezieht sich dies beispielsweise `0.bot.contoso.com` auf , bezieht sich auf und so `0.tcp.ngrok.io` `1.bot.contoso.com` `1.tcp.ngrok.io` weiter.
- Für Ihre URLs ist ein SSL-Zertifikat erforderlich. Um dies einfach zu machen, verwenden Sie ein SSL-Zertifikat, das für eine Platzhalterdomäne ausgestellt wurde. In diesem Fall wäre dies `*.bot.contoso.com` . Dieses SSL-Zertifikat wird vom Medien-SDK überprüft und sollte daher mit der öffentlichen URL Ihres Bots übereinstimmen. Notieren Sie sich den Fingerabdruck, und installieren Sie ihn in Ihren Computerzertifikaten.
- Richten Sie nun einen TCP-Tunnel ein, um den Datenverkehr an "localhost" weiter zu weiterleiten. Schreiben Sie die folgenden Zeilen in ngrok.yml:

    ```yaml
    media:
        addr: 8445
        proto: tcp
    ```

## <a name="start-ngrok"></a>ngrok starten

Nachdem die ngrok-Konfiguration nun bereit ist, starten Sie sie:

  `ngrok.exe start -all -config <Path to your ngrok.yml>`

Dadurch wird ngrok gestartet und die öffentlichen URLs definiert, die die Tunnel für Ihren localhost bereitstellen. Die Ausgabe sieht wie folgt aus:

```cmd
Forwarding  http://signal.ngrok.io -> localhost:12345
Forwarding  https://signal.ngrok.io -> localhost:12345
Forwarding  tcp://1.tcp.ngrok.io:12332 -> localhost:8445
```

Hier ist der Signalport, der von der Anwendung gehostete Port und der von ngrok verfügbar gemachte `12345` `8445` `12332` Remotemedienport. Beachten Sie, dass wir eine Weiterleitung von `1.bot.contoso.com` zu `1.tcp.ngrok.io` haben. Diese wird als Medien-URL für den Bot verwendet. Natürlich sind diese Portnummern nur Beispiele, und Sie können einen beliebigen verfügbaren Port verwenden.

### <a name="update-code"></a>Aktualisieren des Codes

Sobald ngrok ausgeführt wird, aktualisieren Sie den Code so, dass er die konfiguration verwendet, die Sie gerade eingerichtet haben.

#### <a name="update-signaling"></a>Updatesignal

- Ändern Sie im BotBuilder-Aufruf die `NotificationUrl` Signal-URL, die von ngrok bereitgestellt wird.

```csharp
statefulClientBuilder.SetNotificationUrl(
    new Uri("https://signal.ngrok.io/notificationEndpoint"))
```

> [!NOTE]
> Ersetzen Sie das Signal durch das von ngrok bereitgestellte Signal und durch den Controllerpfad, `NotificationEndpoint` der eine Benachrichtigung empfängt.

> **WICHTIG:** Die URL muss `SetNotificationUrl` HTTPS sein.

> **WICHTIG:** Ihre lokale Instanz muss den HTTP-Datenverkehr auf dem Signalport abhören. Die Anforderungen der Anruf- und Onlinebesprechungsplattform erreichen den Bot als Localhost-HTTP-Datenverkehr, es sei denn, die End-to-End-Verschlüsselung ist eingerichtet.

#### <a name="update-media"></a>Medien aktualisieren

Aktualisieren Sie `MediaPlatformSettings` Sie auf Folgendes.

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
> Der oben bereitgestellte Zertifikatfingerabdruck sollte mit dem Dienst-FQDN übereinstimmen. Aus diesem Grund sind die DNS-Einträge erforderlich.

## <a name="next-steps"></a>Nächste Schritte

Ihr Bot kann jetzt lokal ausgeführt werden, und alle Flüsse funktionieren von Ihrem localhost.

## <a name="caveats"></a>Warnen

- Kostenlose Ngrok-Konten **bieten keine** End-to-End-Verschlüsselung. Die HTTPS-Daten enden an der ngrok-URL, und die Datenflüsse werden unverschlüsselt von ngrok zu `localhost` . Wenn Sie eine End-to-End-Verschlüsselung benötigen, sollten Sie ein kostenpflichtiges ngrok-Konto in Betracht ziehen. Schritte [zum Einrichten sicherer](https://ngrok.com/docs#tls) End-to-End-Tunnel finden Sie unter TLS-Tunneln.
- Da die Botrückruf-URL dynamisch ist, müssen Sie in Szenarien mit eingehenden Anrufen häufig Ihre ngrok-Endpunkte aktualisieren. Eine Möglichkeit, dies zu beheben, ist die Verwendung eines kostenpflichtigen ngrok-Kontos, das feste Unterdomänen bietet, auf die Sie Ihren Bot und die Plattform verweisen können.
- Ngrok-Tunnel können auch mit [Azure Service Fabric verwendet werden.](/azure/service-fabric/service-fabric-overview) Ein Beispiel dafür finden Sie in der [HueBot-Beispiel-App.](/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/LocalMediaSamples/HueBot/HueBot)
