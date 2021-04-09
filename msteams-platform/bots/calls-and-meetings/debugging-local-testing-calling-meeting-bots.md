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
# <a name="develop-calling-and-online-meeting-bots-on-your-local-pc"></a><span data-ttu-id="01394-104">Entwickeln von Anruf- und Online-Besprechungsbots auf Ihrem lokalen PC</span><span class="sxs-lookup"><span data-stu-id="01394-104">Develop calling and online meeting bots on your local PC</span></span>

<span data-ttu-id="01394-105">In [Run and debug your app](../../concepts/build-and-test/debug.md) we explain how to use [ngrok](https://ngrok.com) to create a tunnel between your local computer and the internet.</span><span class="sxs-lookup"><span data-stu-id="01394-105">In [Run and debug your app](../../concepts/build-and-test/debug.md) we explain how to use [ngrok](https://ngrok.com) to create a tunnel between your local computer and the internet.</span></span> <span data-ttu-id="01394-106">In diesem Thema erfahren Sie, wie Sie ngrok und Ihren lokalen PC auch verwenden können, um Bots zu entwickeln, die Anrufe und Onlinebesprechungen unterstützen.</span><span class="sxs-lookup"><span data-stu-id="01394-106">In this topic, learn how you can also use ngrok and your local PC to develop bots that support calls and online meetings.</span></span>

<span data-ttu-id="01394-107">Messaging bots use HTTP, but calls and online meeting bots use the lower-level TCP.</span><span class="sxs-lookup"><span data-stu-id="01394-107">Messaging bots use HTTP, but calls and online meeting bots use the lower-level TCP.</span></span> <span data-ttu-id="01394-108">Ngrok unterstützt zusätzlich zu HTTP-Tunneln TCP-Tunnel.</span><span class="sxs-lookup"><span data-stu-id="01394-108">Ngrok supports TCP tunnels in addition to HTTP tunnels.</span></span> 

## <a name="configure-ngrokyml"></a><span data-ttu-id="01394-109">Konfigurieren von ngrok.yml</span><span class="sxs-lookup"><span data-stu-id="01394-109">Configure ngrok.yml</span></span>

<span data-ttu-id="01394-110">Wechseln Sie [zu ngrok,](https://ngrok.com) und registrieren Sie sich für ein kostenloses Konto, oder melden Sie sich bei Ihrem vorhandenen Konto an.</span><span class="sxs-lookup"><span data-stu-id="01394-110">Go to [ngrok](https://ngrok.com) and sign up for a free account or log into your existing account.</span></span> <span data-ttu-id="01394-111">Nachdem Sie sich angemeldet haben, wechseln Sie zum [Dashboard,](https://dashboard.ngrok.com) und erhalten Sie Ihr Authentifizierungstoken.</span><span class="sxs-lookup"><span data-stu-id="01394-111">After you've signed in, go to the [dashboard](https://dashboard.ngrok.com) and get your authtoken.</span></span>

<span data-ttu-id="01394-112">Erstellen Sie eine ngrok-Konfigurationsdatei, `ngrok.yml` und fügen Sie die folgende Zeile hinzu.</span><span class="sxs-lookup"><span data-stu-id="01394-112">Create an ngrok configuration file `ngrok.yml` and add the following line.</span></span> <span data-ttu-id="01394-113">Weitere Informationen zum Ort der Datei finden Sie unter [ngrok](https://ngrok.com/docs#config):</span><span class="sxs-lookup"><span data-stu-id="01394-113">For more information on where the file can be located, see [ngrok](https://ngrok.com/docs#config):</span></span>

  `authtoken: <Your-AuthToken>`

## <a name="set-up-signaling"></a><span data-ttu-id="01394-114">Einrichten der Signalisierung</span><span class="sxs-lookup"><span data-stu-id="01394-114">Set up signaling</span></span>

<span data-ttu-id="01394-115">In [Den Bots](./calls-meetings-bots-overview.md)für Anrufe und Onlinebesprechungen haben wir die Anrufsignalisierung darüber erörtert, wie Bots neue Anrufe und Ereignisse während eines Anrufs erkennen und darauf reagieren.</span><span class="sxs-lookup"><span data-stu-id="01394-115">In [Calls and online meetings bots](./calls-meetings-bots-overview.md), we discussed call signaling on how bots detect and respond to new calls and events during a call.</span></span> <span data-ttu-id="01394-116">Anrufsignalereignisse werden über HTTP POST an den aufrufenden Endpunkt des Bots gesendet.</span><span class="sxs-lookup"><span data-stu-id="01394-116">Call signaling events are sent through HTTP POST to the bot's calling endpoint.</span></span>

<span data-ttu-id="01394-117">Wie bei der Messaging-API des Bots muss Ihr Bot über das Internet erreichbar sein, damit die Echtzeitmedienplattform mit Ihrem Bot sprechen kann.</span><span class="sxs-lookup"><span data-stu-id="01394-117">As with the bot's messaging API, in order for the Real-time Media Platform to talk to your bot, your bot must be reachable over the internet.</span></span> <span data-ttu-id="01394-118">Ngrok macht dies einfach.</span><span class="sxs-lookup"><span data-stu-id="01394-118">Ngrok makes this simple.</span></span> <span data-ttu-id="01394-119">Fügen Sie ihrer ngrok.yml die folgenden Zeilen hinzu:</span><span class="sxs-lookup"><span data-stu-id="01394-119">Add the following lines to your ngrok.yml:</span></span>

```yaml
tunnels:
    signaling:
        addr: 12345
        proto: http
```

## <a name="set-up-local-media"></a><span data-ttu-id="01394-120">Einrichten lokaler Medien</span><span class="sxs-lookup"><span data-stu-id="01394-120">Set up local media</span></span>

> [!NOTE]
> <span data-ttu-id="01394-121">Dieser Abschnitt ist nur für von Anwendungen gehostete Medienbots erforderlich und kann übersprungen werden, wenn Sie medien nicht selbst hosten.</span><span class="sxs-lookup"><span data-stu-id="01394-121">This section is only required for application-hosted media bots and can be skipped if you don't host media yourself.</span></span>

<span data-ttu-id="01394-122">Von der Anwendung gehostete Medien verwenden Zertifikate und TCP-Tunnel.</span><span class="sxs-lookup"><span data-stu-id="01394-122">Application-hosted media uses certificates and TCP tunnels.</span></span> <span data-ttu-id="01394-123">Die folgenden Schritte sind erforderlich:</span><span class="sxs-lookup"><span data-stu-id="01394-123">The following steps are required:</span></span>

1. <span data-ttu-id="01394-124">Die öffentlichen TCP-Endpunkte von Ngrok verfügen über feste URLs.</span><span class="sxs-lookup"><span data-stu-id="01394-124">Ngrok's public TCP endpoints have fixed URLs.</span></span> <span data-ttu-id="01394-125">Sie sind `0.tcp.ngrok.io` `1.tcp.ngrok.io` , und so weiter.</span><span class="sxs-lookup"><span data-stu-id="01394-125">They are `0.tcp.ngrok.io`, `1.tcp.ngrok.io`, and so on.</span></span> <span data-ttu-id="01394-126">Sie müssen über einen DNS-CNAME-Eintrag für Ihren Dienst verfügen, der auf diese URLs verweist.</span><span class="sxs-lookup"><span data-stu-id="01394-126">You must have a DNS CNAME entry for your service that points to these URLs.</span></span> <span data-ttu-id="01394-127">Angenommen, bezieht sich `0.bot.contoso.com` auf `0.tcp.ngrok.io` , `1.bot.contoso.com` bezieht sich auf , und `1.tcp.ngrok.io` so weiter.</span><span class="sxs-lookup"><span data-stu-id="01394-127">For example, let's say `0.bot.contoso.com` refers to `0.tcp.ngrok.io`, `1.bot.contoso.com` refers to `1.tcp.ngrok.io`, and so on.</span></span>
2. <span data-ttu-id="01394-128">Für Ihre URLs ist ein SSL-Zertifikat erforderlich.</span><span class="sxs-lookup"><span data-stu-id="01394-128">A SSL certificate is required for your URLs.</span></span> <span data-ttu-id="01394-129">Um dies zu einfach zu machen, verwenden Sie ein SSL-Zertifikat, das für eine Platzhalterdomäne ausgestellt wurde.</span><span class="sxs-lookup"><span data-stu-id="01394-129">To make it easy, use a SSL certificate issued to a wild card domain.</span></span> <span data-ttu-id="01394-130">In diesem Fall wäre es `*.bot.contoso.com` .</span><span class="sxs-lookup"><span data-stu-id="01394-130">In this case, it would be `*.bot.contoso.com`.</span></span> <span data-ttu-id="01394-131">Dieses SSL-Zertifikat wird vom media SDK überprüft, daher muss es mit der öffentlichen URL Ihres Bots übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="01394-131">This SSL certificate is validated by the media SDK, so it must match your bot's public URL.</span></span> <span data-ttu-id="01394-132">Notieren Sie sich den Fingerabdruck, und installieren Sie ihn in Ihren Computerzertifikaten.</span><span class="sxs-lookup"><span data-stu-id="01394-132">Note the thumbprint and install it in your machine certificates.</span></span>
3. <span data-ttu-id="01394-133">Richten Sie nun einen TCP-Tunnel ein, um den Datenverkehr an localhost weiter zu weiterleiten.</span><span class="sxs-lookup"><span data-stu-id="01394-133">Now, setup a TCP tunnel to forward the traffic to localhost.</span></span> <span data-ttu-id="01394-134">Schreiben Sie die folgenden Zeilen in ngrok.yml:</span><span class="sxs-lookup"><span data-stu-id="01394-134">Write the following lines into your ngrok.yml:</span></span>

    ```yaml
    media:
        addr: 8445
        proto: tcp
    ```

## <a name="start-ngrok"></a><span data-ttu-id="01394-135">ngrok starten</span><span class="sxs-lookup"><span data-stu-id="01394-135">Start ngrok</span></span>

<span data-ttu-id="01394-136">Nachdem die ngrok-Konfiguration nun bereit ist, starten Sie sie:</span><span class="sxs-lookup"><span data-stu-id="01394-136">Now that the ngrok configuration is ready, launch it:</span></span>

  `ngrok.exe start -all -config <Path to your ngrok.yml>`

<span data-ttu-id="01394-137">Dadurch wird ngrok gestartet und die öffentlichen URLs definiert, die die Tunnel für Ihren localhost bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="01394-137">This starts ngrok and defines the public URLs which provide the tunnels to your localhost.</span></span> <span data-ttu-id="01394-138">Es folgt ein Beispiel für die Ausgabe:</span><span class="sxs-lookup"><span data-stu-id="01394-138">Following is an example of the output:</span></span>

```cmd
Forwarding  http://signal.ngrok.io -> localhost:12345
Forwarding  https://signal.ngrok.io -> localhost:12345
Forwarding  tcp://1.tcp.ngrok.io:12332 -> localhost:8445
```

<span data-ttu-id="01394-139">Hier ist der Signalingport, der von der Anwendung gehostete Port und der von ngrok verfügbar gemachte `12345` `8445` `12332` Remotemedienport.</span><span class="sxs-lookup"><span data-stu-id="01394-139">Here, `12345` is the signaling port, `8445` is the application-hosted port, and `12332` is the remote media port exposed by ngrok.</span></span> <span data-ttu-id="01394-140">Beachten Sie, dass wir eine Weiterleitung von `1.bot.contoso.com` zu `1.tcp.ngrok.io` haben.</span><span class="sxs-lookup"><span data-stu-id="01394-140">Note that we have a forwarding from `1.bot.contoso.com` to `1.tcp.ngrok.io`.</span></span> <span data-ttu-id="01394-141">Dies wird als Medien-URL für den Bot verwendet.</span><span class="sxs-lookup"><span data-stu-id="01394-141">This will be used as the media URL for the bot.</span></span> <span data-ttu-id="01394-142">Natürlich sind diese Portnummern nur Beispiele, und Sie können jeden verfügbaren Port verwenden.</span><span class="sxs-lookup"><span data-stu-id="01394-142">Of course, these port numbers are just examples and you can use any available port.</span></span>

### <a name="update-code"></a><span data-ttu-id="01394-143">Aktualisieren des Codes</span><span class="sxs-lookup"><span data-stu-id="01394-143">Update code</span></span>

<span data-ttu-id="01394-144">Nachdem ngrok ausgeführt wurde, aktualisieren Sie den Code so, dass er die konfiguration verwendet, die Sie gerade eingerichtet haben.</span><span class="sxs-lookup"><span data-stu-id="01394-144">After ngrok is up and running, update the code to use the config you just set up.</span></span>

#### <a name="update-signaling"></a><span data-ttu-id="01394-145">Updatesignalisierung</span><span class="sxs-lookup"><span data-stu-id="01394-145">Update signaling</span></span>

<span data-ttu-id="01394-146">Ändern Sie im BotBuilder-Aufruf die in die von ngrok bereitgestellte `NotificationUrl` Signal-URL.</span><span class="sxs-lookup"><span data-stu-id="01394-146">In the BotBuilder call, change the `NotificationUrl` to the signaling URL provided by ngrok.</span></span>

```csharp
statefulClientBuilder.SetNotificationUrl(
    new Uri("https://signal.ngrok.io/notificationEndpoint"))
```

> [!NOTE]
> <span data-ttu-id="01394-147">Ersetzen Sie das Signal durch das von ngrok bereitgestellte signal und das durch den `NotificationEndpoint` Controllerpfad, der eine Benachrichtigung empfängt.</span><span class="sxs-lookup"><span data-stu-id="01394-147">Replace signal with the one provided by ngrok and the `NotificationEndpoint` with the controller path that receives notification.</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="01394-148">Die URL in `SetNotificationUrl` muss HTTPS sein.</span><span class="sxs-lookup"><span data-stu-id="01394-148">The URL in `SetNotificationUrl` must be HTTPS.</span></span>
> 
> <span data-ttu-id="01394-149">Ihre lokale Instanz muss den HTTP-Datenverkehr am Signalport abhören.</span><span class="sxs-lookup"><span data-stu-id="01394-149">Your local instance must be listening to HTTP traffic on the signaling port.</span></span> <span data-ttu-id="01394-150">Die Anforderungen der Anruf- und Onlinebesprechungsplattform erreichen den Bot als localhost-HTTP-Datenverkehr, es sei denn, die End-to-End-Verschlüsselung ist eingerichtet.</span><span class="sxs-lookup"><span data-stu-id="01394-150">The requests made by the calls and online meetings platform will reach the bot as localhost HTTP traffic unless end-to-end encryption is set up.</span></span>

#### <a name="update-media"></a><span data-ttu-id="01394-151">Medien aktualisieren</span><span class="sxs-lookup"><span data-stu-id="01394-151">Update media</span></span>

<span data-ttu-id="01394-152">Aktualisieren Sie `MediaPlatformSettings` Ihre wie folgt:</span><span class="sxs-lookup"><span data-stu-id="01394-152">Update your `MediaPlatformSettings` as following:</span></span>

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
> <span data-ttu-id="01394-153">Der in der bereitgestellte Zertifikatfingerabdruck `MediaPlatformSettings` muss mit dem Dienst-FQDN übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="01394-153">The certificate thumbprint provided in the `MediaPlatformSettings` must match the Service FQDN.</span></span> <span data-ttu-id="01394-154">Deshalb sind die DNS-Einträge erforderlich.</span><span class="sxs-lookup"><span data-stu-id="01394-154">That is why the DNS entries are required.</span></span>

## <a name="caveats"></a><span data-ttu-id="01394-155">Vorbehalte</span><span class="sxs-lookup"><span data-stu-id="01394-155">Caveats</span></span>

- <span data-ttu-id="01394-156">Kostenlose Ngrok-Konten **bieten keine** End-to-End-Verschlüsselung.</span><span class="sxs-lookup"><span data-stu-id="01394-156">Ngrok free accounts **don't** provide end-to-end encryption.</span></span> <span data-ttu-id="01394-157">Die HTTPS-Daten enden an der ngrok-URL, und die Daten werden unverschlüsselt von ngrok zu `localhost` übertragen.</span><span class="sxs-lookup"><span data-stu-id="01394-157">The HTTPS data ends at the ngrok URL and the data flows unencrypted from ngrok to `localhost`.</span></span> <span data-ttu-id="01394-158">Wenn Sie eine End-to-End-Verschlüsselung benötigen, sollten Sie ein kostenpflichtiges ngrok-Konto in Betracht ziehen.</span><span class="sxs-lookup"><span data-stu-id="01394-158">If you require end-to-end encryption, consider a paid ngrok account.</span></span> <span data-ttu-id="01394-159">Schritte zum Einrichten sicherer End-to-End-Tunnel finden Sie unter [TLS-Tunnel.](https://ngrok.com/docs#tls)</span><span class="sxs-lookup"><span data-stu-id="01394-159">See [TLS tunnels](https://ngrok.com/docs#tls) for steps on setting up secure end-to-end tunnels.</span></span>
- <span data-ttu-id="01394-160">Da die Bot-Rückruf-URL dynamisch ist, müssen Sie ihre ngrok-Endpunkte für eingehende Anrufe häufig aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="01394-160">Because the bot callback URL is dynamic, incoming call scenarios require you to frequently update your ngrok endpoints.</span></span> <span data-ttu-id="01394-161">Eine Möglichkeit, dies zu beheben, ist die Verwendung eines kostenpflichtigen ngrok-Kontos, das feste Unterdomänen zur Verfügung stellt, auf die Sie Ihren Bot und die Plattform verweisen können.</span><span class="sxs-lookup"><span data-stu-id="01394-161">One way to fix this is to use a paid ngrok account which provides fixed subdomains to which you can point your bot and the platform.</span></span>
- <span data-ttu-id="01394-162">Ngrok-Tunnel können auch mit [Azure Service Fabric verwendet werden.](/azure/service-fabric/service-fabric-overview)</span><span class="sxs-lookup"><span data-stu-id="01394-162">Ngrok tunnels can also be used with [Azure Service Fabric](/azure/service-fabric/service-fabric-overview).</span></span> <span data-ttu-id="01394-163">Ein Beispiel dafür finden Sie in der [HueBot-Beispiel-App](/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/LocalMediaSamples/HueBot/HueBot).</span><span class="sxs-lookup"><span data-stu-id="01394-163">For an example of how to do this, see the [HueBot sample app](/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/LocalMediaSamples/HueBot/HueBot).</span></span>
