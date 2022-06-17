---
title: Anruf- und Besprechungsbot lokal debuggen
description: In diesem Modul erfahren Sie, wie Sie mit ngrok auch Anrufe und Onlinebesprechungs-Bots auf Ihrem lokalen PC entwickeln können.
ms.topic: how-to
ms.localizationpriority: medium
ms.date: 11/18/2018
ms.openlocfilehash: 518d0b846737eca7f4c182dba032b2c85366cee6
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66143816"
---
# <a name="develop-calling-and-online-meeting-bots-on-your-local-pc"></a>Entwickeln Sie Anruf- und Online-Meeting-Bots auf Ihrem lokalen PC

In ["Ausführen und Debuggen Ihrer App](../../concepts/build-and-test/debug.md)" wird erläutert, wie Sie [mithilfe von ngrok](https://ngrok.com) einen Tunnel zwischen Ihrem lokalen Computer und dem Internet erstellen. In diesem Thema erfahren Sie, wie Sie ngrok und Ihren lokalen PC auch verwenden können, um Bots zu entwickeln, die Anrufe und Online-Meetings unterstützen.

Messaging-Bots verwenden HTTP, aber Anruf- und Online-Meeting-Bots verwenden das niedrigere TCP. Ngrok unterstützt TCP-Tunnel zusätzlich zu HTTP-Tunneln.

## <a name="configure-ngrokyml"></a>Konfigurieren Sie ngrok.yml

Gehen Sie zu [ngrok](https://ngrok.com) und registrieren Sie sich für ein kostenloses Konto oder melden Sie sich bei Ihrem bestehenden Konto an. Nachdem Sie sich angemeldet haben, gehen Sie zum [Dashboard](https://dashboard.ngrok.com) und rufen Sie Ihr Authentifizierungstoken ab.

Erstellen Sie eine ngrok-Konfigurationsdatei `ngrok.yml` , und fügen Sie die folgende Zeile hinzu. Weitere Informationen darüber, wo sich die Datei befinden kann, finden Sie unter [ngrok](https://ngrok.com/docs#config):

  `authtoken: <Your-AuthToken>`

## <a name="set-up-signaling"></a>Einrichten der Signalisierung

In [Anruf- und Online-Meeting-Bots haben wir die Anrufsignalisierung darüber besprochen](./calls-meetings-bots-overview.md), wie Bots neue Anrufe und Ereignisse während eines Anrufs erkennen und darauf reagieren. Anrufsignalisierungsereignisse werden über HTTP POST an den aufrufenden Endpunkt des Bots gesendet.

Wie bei der Messaging-API des Bots muss Ihr Bot über das Internet erreichbar sein, damit die Echtzeit-Medienplattform mit Ihrem Bot kommunizieren kann. Ngrok macht das einfach. Fügen Sie Ihrer ngrok.yml die folgenden Zeilen hinzu:

```yaml
tunnels:
    signaling:
        addr: 12345
        proto: http
```

## <a name="set-up-local-media"></a>Einrichten lokaler Medien

> [!NOTE]
> Dieser Abschnitt ist nur für von Anwendungen gehostete Medienbots erforderlich und kann übersprungen werden, wenn Sie keine Medien selbst hosten.

Anwendungsgehostete Medien verwenden Zertifikate und TCP-Tunnel. Die folgenden zwei Schritte sind dazu erforderlich:

1. Die öffentlichen TCP-Endpunkte von Ngrok haben feste URLs. Sie sind `0.tcp.ngrok.io`usw `1.tcp.ngrok.io`. Sie müssen über einen DNS-CNAME-Eintrag für Ihren Dienst verfügen, der auf diese URLs verweist. Sagen wir zum Beispiel `0.bot.contoso.com` bezieht sich auf `0.tcp.ngrok.io`, `1.bot.contoso.com` bezieht sich auf `1.tcp.ngrok.io` und so weiter.
2. Für Ihre URLs ist ein SSL-Zertifikat erforderlich. Verwenden Sie zur Vereinfachung ein SSL-Zertifikat, das für eine Wildcard-Domain ausgestellt wurde. In diesem Fall wäre es `*.bot.contoso.com`. Dieses SSL-Zertifikat wird vom Medien-SDK validiert, daher muss es mit der öffentlichen URL Ihres Bots übereinstimmen. Notieren Sie sich den Fingerabdruck und installieren Sie ihn in Ihren Maschinenzertifikaten.
3. Richten Sie nun einen TCP-Tunnel ein, um den Datenverkehr an localhost weiterzuleiten. Schreiben Sie die folgenden Zeilen in Ihre ngrok.yml:

    ```yaml
    media:
        addr: 8445
        proto: tcp
    ```

## <a name="start-ngrok"></a>Starten Sie ngrok

Nachdem die ngrok-Konfiguration fertig ist, starten Sie sie:

  `ngrok.exe start -all -config <Path to your ngrok.yml>`

Dies startet ngrok und definiert die öffentlichen URLs, die die Tunnel für Ihren localhost bereitstellen. Es folgt ein Beispiel für die Ausgabe:

```cmd
Forwarding  http://signal.ngrok.io -> localhost:12345
Forwarding  https://signal.ngrok.io -> localhost:12345
Forwarding  tcp://1.tcp.ngrok.io:12332 -> localhost:8445
```

Hier `12345` ist der Signalisierungsport, `8445` der von der Anwendung gehostete Port und `12332` der von ngrok bereitgestellte Remote-Medienport. Beachten Sie, dass wir eine Weiterleitung von bis `1.bot.contoso.com` haben `1.tcp.ngrok.io`. Dies wird als Medien-URL für den Bot verwendet. Natürlich sind diese Portnummern nur Beispiele und Sie können jeden verfügbaren Port verwenden.

### <a name="update-code"></a>Aktualisieren des Codes

Nachdem ngrok betriebsbereit ist, aktualisieren Sie den Code, um die gerade eingerichtete Konfiguration zu verwenden.

#### <a name="update-signaling"></a>Signalisierung aktualisieren

Ändern Sie im BotBuilder-Aufruf `NotificationUrl`die in die von ngrok bereitgestellte Signalisierungs-URL.

```csharp
statefulClientBuilder.SetNotificationUrl(
    new Uri("https://signal.ngrok.io/notificationEndpoint"))
```

> [!NOTE]
> Ersetzen Sie signal durch das von ngrok bereitgestellte und `NotificationEndpoint` durch den Controller-Pfad, der die Benachrichtigung erhält.

> [!IMPORTANT]
>
> * Die URL in `SetNotificationUrl` muss HTTPS sein.
>
> Ihre lokale Instanz muss HTTP-Datenverkehr am Signalisierungsport überwachen. Die von der Anruf- und Online-Meeting-Plattform gestellten Anforderungen erreichen den Bot als localhost-HTTP-Datenverkehr, sofern keine Ende-zu-Ende-Verschlüsselung eingerichtet ist.

#### <a name="update-media"></a>Medien aktualisieren

Aktualisieren Sie Ihre wie `MediaPlatformSettings` folgt:

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
> Der in bereitgestellte Fingerabdruck des Zertifikats muss mit `MediaPlatformSettings` dem Dienst-FQDN übereinstimmen. Deshalb werden die DNS-Einträge benötigt.

## <a name="caveats"></a>Vorbehalte

* Kostenlose Ngrok-Konten bieten **keine** Ende-zu-Ende-Verschlüsselung. Die HTTPS-Daten enden bei der ngrok-URL und die Daten fließen unverschlüsselt von ngrok nach`localhost`. Wenn Sie eine Ende-zu-Ende-Verschlüsselung benötigen, ziehen Sie ein kostenpflichtiges ngrok-Konto in Betracht. Siehe [TLS-Tunnel](https://ngrok.com/docs#tls) für Schritte zum Einrichten sicherer End-to-End-Tunnel.
* Da die Bot-Callback-URL dynamisch ist, erfordern eingehende Anrufszenarien, dass Sie Ihre ngrok-Endpunkte häufig aktualisieren. Eine Möglichkeit, dies zu beheben, ist die Verwendung eines kostenpflichtigen ngrok-Kontos, das feste Unterdomänen bereitstellt, auf die Sie Ihren Bot und die Plattform verweisen können.
* Ngrok-Tunnel können auch mit [Azure Service Fabric verwendet werden](/azure/service-fabric/service-fabric-overview). Ein Beispiel dafür finden Sie in der [HueBot-Beispiel-App](https://github.com/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/V1.0Samples/LocalMediaSamples/HueBot/HueBot).
