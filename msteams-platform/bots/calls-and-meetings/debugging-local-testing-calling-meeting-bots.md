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
# <a name="how-to-develop-calling-and-online-meeting-bots-on-your-local-pc"></a><span data-ttu-id="673d4-104">So entwickeln Sie Anrufer-und Online-Besprechungs-Bots auf Ihrem lokalen PC</span><span class="sxs-lookup"><span data-stu-id="673d4-104">How to develop calling and online meeting bots on your local PC</span></span>

<span data-ttu-id="673d4-105">In [ausführen und Debuggen Ihrer APP](../../concepts/build-and-test/debug.md) wird erklärt, wie Sie [ngrok](https://ngrok.com) verwenden, um einen Tunnel zwischen Ihrem lokalen Computer und dem Internet zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="673d4-105">In [Run and debug your app](../../concepts/build-and-test/debug.md) we explain how to use [ngrok](https://ngrok.com) to create a tunnel between your local computer and the internet.</span></span> <span data-ttu-id="673d4-106">In diesem Thema erfahren Sie, wie Sie auch ngrok und Ihren lokalen PC verwenden können, um Bots zu entwickeln, die Anrufe und Onlinebesprechungen unterstützen.</span><span class="sxs-lookup"><span data-stu-id="673d4-106">In this topic, learn how you can also use ngrok and your local PC to develop bots that support calls and online meetings.</span></span>

<span data-ttu-id="673d4-107">Messaging-Bots verwenden http, aber Anrufe und Online-Besprechungs-Bots verwenden die unterere Ebene TCP.</span><span class="sxs-lookup"><span data-stu-id="673d4-107">Messaging bots use HTTP, but calls and online meeting bots use the lower-level TCP.</span></span> <span data-ttu-id="673d4-108">Ngrok unterstützt TCP-Tunnel zusätzlich zu http-Tunneln; Hier erfahren Sie, wie es weiter unten geht.</span><span class="sxs-lookup"><span data-stu-id="673d4-108">Ngrok supports TCP tunnels in addition to HTTP tunnels; you'll learn how, below.</span></span>

## <a name="configuring-ngrokyml"></a><span data-ttu-id="673d4-109">Konfigurieren von ngrok. yml</span><span class="sxs-lookup"><span data-stu-id="673d4-109">Configuring ngrok.yml</span></span>

<span data-ttu-id="673d4-110">Wechseln Sie zu [ngrok](https://ngrok.com) , und registrieren Sie sich für ein kostenloses Konto, oder melden Sie sich bei Ihrem vorhandenen Konto an.</span><span class="sxs-lookup"><span data-stu-id="673d4-110">Go to [ngrok](https://ngrok.com) and sign up for a free account or log into your existing account.</span></span> <span data-ttu-id="673d4-111">Nachdem Sie sich angemeldet haben, wechseln Sie zum [Dashboard](https://dashboard.ngrok.com) , und rufen Sie Ihre AuthToken ab.</span><span class="sxs-lookup"><span data-stu-id="673d4-111">Once you've logged in, go to the [dashboard](https://dashboard.ngrok.com) and get your authtoken.</span></span>

<span data-ttu-id="673d4-112">Erstellen Sie eine ngrok- `ngrok.yml` Konfigurationsdatei (Weitere Informationen dazu, wo sich diese Datei befinden kann), und [fügen Sie die](https://ngrok.com/docs#config) folgende Position hinzu:</span><span class="sxs-lookup"><span data-stu-id="673d4-112">Create an ngrok configuration file `ngrok.yml` (see [here](https://ngrok.com/docs#config) for more information on where this file can be located) and add this line:</span></span>

  `authtoken: <Your-AuthToken>`

## <a name="setting-up-signaling"></a><span data-ttu-id="673d4-113">Einrichten der Signalisierung</span><span class="sxs-lookup"><span data-stu-id="673d4-113">Setting up signaling</span></span>

<span data-ttu-id="673d4-114">In [Anrufern und Online-Besprechungs-Bots](./calls-meetings-bots-overview.md)wurde Gesprächs Signalierung erörtert, wie Bots während eines Anrufs neue Anrufe und Ereignisse erkennen und darauf reagieren.</span><span class="sxs-lookup"><span data-stu-id="673d4-114">In [Calls and online meetings bots](./calls-meetings-bots-overview.md), we discussed call signaling — how bots detect and respond to new calls and events during a call.</span></span> <span data-ttu-id="673d4-115">Anruf Signalisierungs Ereignisse werden über HTTP-Post an den aufrufenden Endpunkt des bot gesendet.</span><span class="sxs-lookup"><span data-stu-id="673d4-115">Call signaling events are sent via HTTP POST to the bot's calling endpoint.</span></span>

<span data-ttu-id="673d4-116">Wie bei der Messaging-API des bot muss Ihr bot über das Internet erreichbar sein, damit die Echt Zeit Medienplattform mit Ihrem bot kommunizieren kann.</span><span class="sxs-lookup"><span data-stu-id="673d4-116">As with the bot's messaging API, in order for the Real-time Media Platform to talk to your bot, your bot must be reachable over the internet.</span></span> <span data-ttu-id="673d4-117">Ngrok vereinfacht dies, indem Sie die folgenden Zeilen zu ihrer Ngrok. yml hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="673d4-117">Ngrok makes this simple — add the following lines to your ngrok.yml:</span></span>

```yaml
tunnels:
    signaling:
        addr: 12345
        proto: http
```

## <a name="setting-up-local-media"></a><span data-ttu-id="673d4-118">Einrichten von lokalen Medien</span><span class="sxs-lookup"><span data-stu-id="673d4-118">Setting up local media</span></span>

> [!NOTE]
> <span data-ttu-id="673d4-119">Dieser Abschnitt ist nur für von der Anwendung gehostete Medien Bots erforderlich und kann übersprungen werden, wenn Sie keine Medien selbst hosten.</span><span class="sxs-lookup"><span data-stu-id="673d4-119">This section is only required for application-hosted media bots and can be skipped if you don't host media yourself.</span></span>

<span data-ttu-id="673d4-120">Von der Anwendung gehostete Medien verwenden Zertifikate und TCP-Tunnel.</span><span class="sxs-lookup"><span data-stu-id="673d4-120">Application-hosted media uses certificates and TCP tunnels.</span></span> <span data-ttu-id="673d4-121">Die folgenden Schritte sind erforderlich:</span><span class="sxs-lookup"><span data-stu-id="673d4-121">The following steps are required:</span></span>

- <span data-ttu-id="673d4-122">Öffentliche TCP-Endpunkte von Ngrok haben feste URLs.</span><span class="sxs-lookup"><span data-stu-id="673d4-122">Ngrok's public TCP endpoints have fixed URLs.</span></span> <span data-ttu-id="673d4-123">Sie sind `0.tcp.ngrok.io`, `1.tcp.ngrok.io`usw.</span><span class="sxs-lookup"><span data-stu-id="673d4-123">They are `0.tcp.ngrok.io`, `1.tcp.ngrok.io`, and so on.</span></span> <span data-ttu-id="673d4-124">Sie sollten über einen DNS-CNAME-Eintrag für den Dienst verfügen, der auf diese URLs verweist.</span><span class="sxs-lookup"><span data-stu-id="673d4-124">You should have a DNS CNAME entry for your service that points to these URLs.</span></span> <span data-ttu-id="673d4-125">In `0.bot.contoso.com` diesem Beispiel `0.tcp.ngrok.io` `1.bot.contoso.com` `1.tcp.ngrok.io`wird angenommen, bezieht sich auf, und so weiter.</span><span class="sxs-lookup"><span data-stu-id="673d4-125">In this example, let's say `0.bot.contoso.com` refers to `0.tcp.ngrok.io`, `1.bot.contoso.com` refers to `1.tcp.ngrok.io`, and so on.</span></span>
- <span data-ttu-id="673d4-126">Für Ihre URLs ist ein SSL-Zertifikat erforderlich.</span><span class="sxs-lookup"><span data-stu-id="673d4-126">A SSL certificate is required for your URLs.</span></span> <span data-ttu-id="673d4-127">Verwenden Sie ein SSL-Zertifikat, das für eine Platzhalterdomäne ausgestellt wurde, um es einfach zu machen.</span><span class="sxs-lookup"><span data-stu-id="673d4-127">To make it easy, use a SSL certificate issued to a wild card domain.</span></span> <span data-ttu-id="673d4-128">In diesem Fall wäre es `*.bot.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="673d4-128">In this case, it would be `*.bot.contoso.com`.</span></span> <span data-ttu-id="673d4-129">Dieses SSL-Zertifikat wird vom Media SDK überprüft und sollte daher mit der öffentlichen URL Ihres bot übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="673d4-129">This SSL certificate is validated by the media SDK, so it should match your bot's public URL.</span></span> <span data-ttu-id="673d4-130">Notieren Sie sich den Fingerabdruck und installieren Sie ihn in ihren Computerzertifikaten.</span><span class="sxs-lookup"><span data-stu-id="673d4-130">Note the thumbprint and install it in your machine certificates.</span></span>
- <span data-ttu-id="673d4-131">Richten Sie nun einen TCP-Tunnel für die Weiterleitung des Datenverkehrs an localhost ein.</span><span class="sxs-lookup"><span data-stu-id="673d4-131">Now, setup a TCP tunnel to forward the traffic to localhost.</span></span> <span data-ttu-id="673d4-132">Schreiben Sie die folgenden Zeilen in Ihre ngrok. yml:</span><span class="sxs-lookup"><span data-stu-id="673d4-132">Write the following lines into your ngrok.yml:</span></span>

    ```yaml
    media:
        addr: 8445
        proto: tcp
    ```

## <a name="start-ngrok"></a><span data-ttu-id="673d4-133">Ngrok starten</span><span class="sxs-lookup"><span data-stu-id="673d4-133">Start ngrok</span></span>

<span data-ttu-id="673d4-134">Nachdem die ngrok-Konfiguration nun bereit ist, starten Sie Sie:</span><span class="sxs-lookup"><span data-stu-id="673d4-134">Now that the ngrok configuration is ready, launch it:</span></span>

  `ngrok.exe start -all -config <Path to your ngrok.yml>`

<span data-ttu-id="673d4-135">Damit wird ngrok gestartet und die öffentlichen URLs definiert, die die Tunnel für Ihren localhost bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="673d4-135">This starts ngrok and defines the public URLs which provide the tunnels to your localhost.</span></span> <span data-ttu-id="673d4-136">Die Ausgabe sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="673d4-136">The output looks like the following:</span></span>

```cmd
Forwarding  http://signal.ngrok.io -> localhost:12345
Forwarding  https://signal.ngrok.io -> localhost:12345
Forwarding  tcp://1.tcp.ngrok.io:12332 -> localhost:8445
```

<span data-ttu-id="673d4-137">Hier `12345` ist der Signalisierungs Port, `8445` der von der Anwendung gehostete Port und `12332` der Remotemedien Port, der von ngrok verfügbar gemacht wird.</span><span class="sxs-lookup"><span data-stu-id="673d4-137">Here, `12345` is the signaling port, `8445` is the application-hosted port, and `12332` is the remote media port exposed by ngrok.</span></span> <span data-ttu-id="673d4-138">Beachten Sie, dass wir eine weiter `1.bot.contoso.com` Leitung `1.tcp.ngrok.io`von an haben.</span><span class="sxs-lookup"><span data-stu-id="673d4-138">Note that we have a forwarding from `1.bot.contoso.com` to `1.tcp.ngrok.io`.</span></span> <span data-ttu-id="673d4-139">Dieser wird als Medien-URL für den bot verwendet.</span><span class="sxs-lookup"><span data-stu-id="673d4-139">This will be used as the media URL for the bot.</span></span> <span data-ttu-id="673d4-140">Selbstverständlich sind diese Portnummern nur Beispiele, und Sie können einen beliebigen verfügbaren Port verwenden.</span><span class="sxs-lookup"><span data-stu-id="673d4-140">Of course, these port numbers are just examples and you can use any available port.</span></span>

### <a name="update-code"></a><span data-ttu-id="673d4-141">Aktualisieren des Codes</span><span class="sxs-lookup"><span data-stu-id="673d4-141">Update code</span></span>

<span data-ttu-id="673d4-142">Nachdem ngrok gestartet wurde, aktualisieren Sie den Code, um die Konfiguration zu verwenden, die Sie soeben eingerichtet haben.</span><span class="sxs-lookup"><span data-stu-id="673d4-142">Once ngrok is up and running, update the code to use the config you just set up.</span></span>

#### <a name="update-signaling"></a><span data-ttu-id="673d4-143">Aktualisieren der Signalisierung</span><span class="sxs-lookup"><span data-stu-id="673d4-143">Update signaling</span></span>

- <span data-ttu-id="673d4-144">Ändern Sie im BotBuilder-Aufruf die `NotificationUrl` in die Signalisierungs-URL, die von ngrok bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="673d4-144">In the BotBuilder call, change the `NotificationUrl` to the signaling URL provided by ngrok.</span></span>

```csharp
statefulClientBuilder.SetNotificationUrl(
    new Uri("https://signal.ngrok.io/notificationEndpoint"))
```

> [!NOTE]
> <span data-ttu-id="673d4-145">Ersetzen Sie das Signal durch das von ngrok bereitgestellte `NotificationEndpoint` und mit dem Controller Pfad, der eine Benachrichtigung erhält.</span><span class="sxs-lookup"><span data-stu-id="673d4-145">Replace signal with the one provided by ngrok and the `NotificationEndpoint` with the controller path that receives notification.</span></span>

> <span data-ttu-id="673d4-146">**Wichtig**: die URL in `SetNotificationUrl` muss https sein.</span><span class="sxs-lookup"><span data-stu-id="673d4-146">**IMPORTANT**: The URL in `SetNotificationUrl` must be HTTPS.</span></span>

> <span data-ttu-id="673d4-147">**Wichtig**: Ihre lokale Instanz muss den HTTP-Datenverkehr am Signal Port überwachen.</span><span class="sxs-lookup"><span data-stu-id="673d4-147">**IMPORTANT**: Your local instance must be listening to HTTP traffic on the signaling port.</span></span> <span data-ttu-id="673d4-148">Die Anforderungen, die von der Plattform für Anrufe und Onlinebesprechungen vorgenommen werden, erreichen den bot als localhost-HTTP-Datenverkehr, es sei denn, die End-to-End-Verschlüsselung ist eingerichtet.</span><span class="sxs-lookup"><span data-stu-id="673d4-148">The requests made by the calls and online meetings platform will reach the bot as localhost HTTP traffic unless end-to-end encryption is set up.</span></span>

#### <a name="update-media"></a><span data-ttu-id="673d4-149">Aktualisieren von Medien</span><span class="sxs-lookup"><span data-stu-id="673d4-149">Update media</span></span>

<span data-ttu-id="673d4-150">Aktualisieren Sie `MediaPlatformSettings` Folgendes:</span><span class="sxs-lookup"><span data-stu-id="673d4-150">Update your `MediaPlatformSettings` to the following.</span></span>

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
> <span data-ttu-id="673d4-151">Der oben angegebene Zertifikat Fingerabdruck sollte mit dem Dienst-FQDN übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="673d4-151">The certificate thumbprint provided above should match the Service FQDN.</span></span> <span data-ttu-id="673d4-152">Aus diesem Grund sind die DNS-Einträge erforderlich.</span><span class="sxs-lookup"><span data-stu-id="673d4-152">That is why the DNS entries are required.</span></span>

## <a name="next-steps"></a><span data-ttu-id="673d4-153">Weitere Schritte</span><span class="sxs-lookup"><span data-stu-id="673d4-153">Next steps</span></span>

<span data-ttu-id="673d4-154">Ihr Bot kann nun lokal ausgeführt werden, und alle Abläufe funktionieren von Ihrem localhost aus.</span><span class="sxs-lookup"><span data-stu-id="673d4-154">Your bot can now run locally and all the flows work from your localhost.</span></span>

## <a name="caveats"></a><span data-ttu-id="673d4-155">Warnhinweise</span><span class="sxs-lookup"><span data-stu-id="673d4-155">Caveats</span></span>

- <span data-ttu-id="673d4-156">Ngrok-freie Konten bieten **keine** End-to-End-Verschlüsselung.</span><span class="sxs-lookup"><span data-stu-id="673d4-156">Ngrok free accounts **don't** provide end-to-end encryption.</span></span> <span data-ttu-id="673d4-157">Die HTTPS-Daten enden an der ngrok-URL, und die Daten fließen unverschlüsselt `localhost`von ngrok in.</span><span class="sxs-lookup"><span data-stu-id="673d4-157">The HTTPS data ends at the ngrok URL and the data flows unencrypted from ngrok to `localhost`.</span></span> <span data-ttu-id="673d4-158">Wenn Sie eine End-to-End-Verschlüsselung benötigen, sollten Sie ein kostenpflichtiges ngrok-Konto verwenden.</span><span class="sxs-lookup"><span data-stu-id="673d4-158">If you require end-to-end encryption, consider a paid ngrok account.</span></span> <span data-ttu-id="673d4-159">Schritte zum Einrichten sicherer End-to-End-Tunnel finden Sie unter [TLS-Tunnel](https://ngrok.com/docs#tls) .</span><span class="sxs-lookup"><span data-stu-id="673d4-159">See [TLS tunnels](https://ngrok.com/docs#tls) for steps on setting up secure end-to-end tunnels.</span></span>
- <span data-ttu-id="673d4-160">Da die bot-Rückruf-URL dynamisch ist, müssen bei eingehenden Anrufszenarien häufig die ngrok-Endpunkte aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="673d4-160">Because the bot callback URL is dynamic, incoming call scenarios require you to frequently update your ngrok endpoints.</span></span> <span data-ttu-id="673d4-161">Eine Möglichkeit, dies zu beheben, ist die Verwendung eines kostenpflichtigen ngrok-Kontos, das feste Unterdomänen zur Verfügung stellt, auf die Sie Ihren bot und die Plattform hinweisen können.</span><span class="sxs-lookup"><span data-stu-id="673d4-161">One way to fix this is to use a paid ngrok account which provides fixed subdomains to which you can point your bot and the platform.</span></span>
- <span data-ttu-id="673d4-162">Ngrok-Tunnel können auch mit [Azure Service Fabric](/azure/service-fabric/service-fabric-overview)verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="673d4-162">Ngrok tunnels can also be used with [Azure Service Fabric](/azure/service-fabric/service-fabric-overview).</span></span> <span data-ttu-id="673d4-163">Ein Beispiel für die Vorgehensweise finden Sie in der [HueBot-Beispiel-App](/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/LocalMediaSamples/HueBot/HueBot).</span><span class="sxs-lookup"><span data-stu-id="673d4-163">For an example of how to do this, see the [HueBot sample app](/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/LocalMediaSamples/HueBot/HueBot).</span></span>
