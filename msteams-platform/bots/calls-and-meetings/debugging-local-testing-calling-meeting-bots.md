---
title: So entwickeln Sie Anrufer-und Online-Besprechungs-Bots auf Ihrem lokalen PC
description: Erfahren Sie, wie Sie mit ngrok auch Anrufe und Online-Besprechungs-Bots auf Ihrem lokalen PC entwickeln können.
keywords: lokale Entwicklung ngrok Tunnel
ms.date: 11/18/2018
ms.openlocfilehash: b6cd2ba5a3866da8085b3da42377ab9e21f12f5f
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674499"
---
# <a name="how-to-develop-calling-and-online-meeting-bots-on-your-local-pc"></a>So entwickeln Sie Anrufer-und Online-Besprechungs-Bots auf Ihrem lokalen PC

In [ausführen und Debuggen Ihrer APP](../../concepts/build-and-test/debug.md) wird erklärt, wie Sie [ngrok](https://ngrok.com) verwenden, um einen Tunnel zwischen Ihrem lokalen Computer und dem Internet zu erstellen. In diesem Thema erfahren Sie, wie Sie auch ngrok und Ihren lokalen PC verwenden können, um Bots zu entwickeln, die Anrufe und Onlinebesprechungen unterstützen.

Messaging-Bots verwenden http, aber Anrufe und Online-Besprechungs-Bots verwenden die unterere Ebene TCP. Ngrok unterstützt TCP-Tunnel zusätzlich zu http-Tunneln; Hier erfahren Sie, wie es weiter unten geht.

## <a name="configuring-ngrokyml"></a>Konfigurieren von ngrok. yml

Wechseln Sie zu [ngrok](https://ngrok.com) , und registrieren Sie sich für ein kostenloses Konto, oder melden Sie sich bei Ihrem vorhandenen Konto an. Nachdem Sie sich angemeldet haben, wechseln Sie zum [Dashboard](https://dashboard.ngrok.com) , und rufen Sie Ihre AuthToken ab.

Erstellen Sie eine ngrok- `ngrok.yml` Konfigurationsdatei (Weitere Informationen dazu, wo sich diese Datei befinden kann), und [fügen Sie die](https://ngrok.com/docs#config) folgende Position hinzu:

  `authtoken: <Your-AuthToken>`

## <a name="setting-up-signaling"></a>Einrichten der Signalisierung

In [Anrufern und Online-Besprechungs-Bots](./calls-meetings-bots-overview.md)wurde Gesprächs Signalierung erörtert, wie Bots während eines Anrufs neue Anrufe und Ereignisse erkennen und darauf reagieren. Anruf Signalisierungs Ereignisse werden über HTTP-Post an den aufrufenden Endpunkt des bot gesendet.

Wie bei der Messaging-API des bot muss Ihr bot über das Internet erreichbar sein, damit die Echt Zeit Medienplattform mit Ihrem bot kommunizieren kann. Ngrok vereinfacht dies, indem Sie die folgenden Zeilen zu ihrer Ngrok. yml hinzufügen:

```yaml
tunnels:
    signaling:
        addr: 12345
        proto: http
```

## <a name="setting-up-local-media"></a>Einrichten von lokalen Medien

> [!NOTE]
> Dieser Abschnitt ist nur für von der Anwendung gehostete Medien Bots erforderlich und kann übersprungen werden, wenn Sie keine Medien selbst hosten.

Von der Anwendung gehostete Medien verwenden Zertifikate und TCP-Tunnel. Die folgenden Schritte sind erforderlich:

- Öffentliche TCP-Endpunkte von Ngrok haben feste URLs. Sie sind `0.tcp.ngrok.io`, `1.tcp.ngrok.io`usw. Sie sollten über einen DNS-CNAME-Eintrag für den Dienst verfügen, der auf diese URLs verweist. In `0.bot.contoso.com` diesem Beispiel `0.tcp.ngrok.io` `1.bot.contoso.com` `1.tcp.ngrok.io`wird angenommen, bezieht sich auf, und so weiter.
- Für Ihre URLs ist ein SSL-Zertifikat erforderlich. Verwenden Sie ein SSL-Zertifikat, das für eine Platzhalterdomäne ausgestellt wurde, um es einfach zu machen. In diesem Fall wäre es `*.bot.contoso.com`. Dieses SSL-Zertifikat wird vom Media SDK überprüft und sollte daher mit der öffentlichen URL Ihres bot übereinstimmen. Notieren Sie sich den Fingerabdruck und installieren Sie ihn in ihren Computerzertifikaten.
- Richten Sie nun einen TCP-Tunnel für die Weiterleitung des Datenverkehrs an localhost ein. Schreiben Sie die folgenden Zeilen in Ihre ngrok. yml:

    ```yaml
    media:
        addr: 8445
        proto: tcp
    ```

## <a name="start-ngrok"></a>Ngrok starten

Nachdem die ngrok-Konfiguration nun bereit ist, starten Sie Sie:

  `ngrok.exe start -all -config <Path to your ngrok.yml>`

Damit wird ngrok gestartet und die öffentlichen URLs definiert, die die Tunnel für Ihren localhost bereitstellen. Die Ausgabe sieht wie folgt aus:

```cmd
Forwarding  http://signal.ngrok.io -> localhost:12345
Forwarding  https://signal.ngrok.io -> localhost:12345
Forwarding  tcp://1.tcp.ngrok.io:12332 -> localhost:8445
```

Hier `12345` ist der Signalisierungs Port, `8445` der von der Anwendung gehostete Port und `12332` der Remotemedien Port, der von ngrok verfügbar gemacht wird. Beachten Sie, dass wir eine weiter `1.bot.contoso.com` Leitung `1.tcp.ngrok.io`von an haben. Dieser wird als Medien-URL für den bot verwendet. Selbstverständlich sind diese Portnummern nur Beispiele, und Sie können einen beliebigen verfügbaren Port verwenden.

### <a name="update-code"></a>Aktualisieren des Codes

Nachdem ngrok gestartet wurde, aktualisieren Sie den Code, um die Konfiguration zu verwenden, die Sie soeben eingerichtet haben.

#### <a name="update-signaling"></a>Aktualisieren der Signalisierung

- Ändern Sie im BotBuilder-Aufruf die `NotificationUrl` in die Signalisierungs-URL, die von ngrok bereitgestellt wird.

```csharp
statefulClientBuilder.SetNotificationUrl(
    new Uri("https://signal.ngrok.io/notificationEndpoint"))
```

> [!NOTE]
> Ersetzen Sie das Signal durch das von ngrok bereitgestellte `NotificationEndpoint` und mit dem Controller Pfad, der eine Benachrichtigung erhält.

> **Wichtig**: die URL in `SetNotificationUrl` muss https sein.

> **Wichtig**: Ihre lokale Instanz muss den HTTP-Datenverkehr am Signal Port überwachen. Die Anforderungen, die von der Plattform für Anrufe und Onlinebesprechungen vorgenommen werden, erreichen den bot als localhost-HTTP-Datenverkehr, es sei denn, die End-to-End-Verschlüsselung ist eingerichtet.

#### <a name="update-media"></a>Aktualisieren von Medien

Aktualisieren Sie `MediaPlatformSettings` Folgendes:

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
> Der oben angegebene Zertifikat Fingerabdruck sollte mit dem Dienst-FQDN übereinstimmen. Aus diesem Grund sind die DNS-Einträge erforderlich.

## <a name="next-steps"></a>Weitere Schritte

Ihr Bot kann nun lokal ausgeführt werden, und alle Abläufe funktionieren von Ihrem localhost aus.

## <a name="caveats"></a>Warnhinweise

- Ngrok-freie Konten bieten **keine** End-to-End-Verschlüsselung. Die HTTPS-Daten enden an der ngrok-URL, und die Daten fließen unverschlüsselt `localhost`von ngrok in. Wenn Sie eine End-to-End-Verschlüsselung benötigen, sollten Sie ein kostenpflichtiges ngrok-Konto verwenden. Schritte zum Einrichten sicherer End-to-End-Tunnel finden Sie unter [TLS-Tunnel](https://ngrok.com/docs#tls) .
- Da die bot-Rückruf-URL dynamisch ist, müssen bei eingehenden Anrufszenarien häufig die ngrok-Endpunkte aktualisiert werden. Eine Möglichkeit, dies zu beheben, ist die Verwendung eines kostenpflichtigen ngrok-Kontos, das feste Unterdomänen zur Verfügung stellt, auf die Sie Ihren bot und die Plattform hinweisen können.
- Ngrok-Tunnel können auch mit [Azure Service Fabric](/azure/service-fabric/service-fabric-overview)verwendet werden. Ein Beispiel für die Vorgehensweise finden Sie in der [HueBot-Beispiel-App](/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/LocalMediaSamples/HueBot/HueBot).
