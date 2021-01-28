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
# <a name="how-to-develop-calling-and-online-meeting-bots-on-your-local-pc"></a><span data-ttu-id="92de8-104">So entwickeln Sie Anruf- und Online-Besprechungsbots auf Ihrem lokalen PC</span><span class="sxs-lookup"><span data-stu-id="92de8-104">How to develop calling and online meeting bots on your local PC</span></span>

<span data-ttu-id="92de8-105">In [Run and debug your app](../../concepts/build-and-test/debug.md) we explain how to use [ngrok](https://ngrok.com) to create a tunnel between your local computer and the internet.</span><span class="sxs-lookup"><span data-stu-id="92de8-105">In [Run and debug your app](../../concepts/build-and-test/debug.md) we explain how to use [ngrok](https://ngrok.com) to create a tunnel between your local computer and the internet.</span></span> <span data-ttu-id="92de8-106">In diesem Thema erfahren Sie, wie Sie ngrok und Ihren lokalen PC auch zum Entwickeln von Bots verwenden können, die Anrufe und Onlinebesprechungen unterstützen.</span><span class="sxs-lookup"><span data-stu-id="92de8-106">In this topic, learn how you can also use ngrok and your local PC to develop bots that support calls and online meetings.</span></span>

<span data-ttu-id="92de8-107">Messaging bots use HTTP, but calls and online meeting bots use the lower-level TCP.</span><span class="sxs-lookup"><span data-stu-id="92de8-107">Messaging bots use HTTP, but calls and online meeting bots use the lower-level TCP.</span></span> <span data-ttu-id="92de8-108">Ngrok unterstützt #A0 zusätzlich zu HTTP-Tunneln. Wie das geht, erfahren Sie weiter unten.</span><span class="sxs-lookup"><span data-stu-id="92de8-108">Ngrok supports TCP tunnels in addition to HTTP tunnels; you'll learn how, below.</span></span>

## <a name="configuring-ngrokyml"></a><span data-ttu-id="92de8-109">Konfigurieren von ngrok.yml</span><span class="sxs-lookup"><span data-stu-id="92de8-109">Configuring ngrok.yml</span></span>

<span data-ttu-id="92de8-110">Wechseln Sie [zu ngrok,](https://ngrok.com) und registrieren Sie sich für ein kostenloses Konto, oder melden Sie sich bei Ihrem vorhandenen Konto an.</span><span class="sxs-lookup"><span data-stu-id="92de8-110">Go to [ngrok](https://ngrok.com) and sign up for a free account or log into your existing account.</span></span> <span data-ttu-id="92de8-111">Nachdem Sie sich angemeldet haben, wechseln Sie zum [Dashboard,](https://dashboard.ngrok.com) und erhalten Sie Ihr Authentifizierungstoken.</span><span class="sxs-lookup"><span data-stu-id="92de8-111">Once you've logged in, go to the [dashboard](https://dashboard.ngrok.com) and get your authtoken.</span></span>

<span data-ttu-id="92de8-112">Erstellen Sie eine ngrok-Konfigurationsdatei (hier finden Sie weitere Informationen dazu, wo sich diese Datei befinden kann), und fügen Sie `ngrok.yml` diese Zeile hinzu: [](https://ngrok.com/docs#config)</span><span class="sxs-lookup"><span data-stu-id="92de8-112">Create an ngrok configuration file `ngrok.yml` (see [here](https://ngrok.com/docs#config) for more information on where this file can be located) and add this line:</span></span>

  `authtoken: <Your-AuthToken>`

## <a name="setting-up-signaling"></a><span data-ttu-id="92de8-113">Einrichten der Signalisierung</span><span class="sxs-lookup"><span data-stu-id="92de8-113">Setting up signaling</span></span>

<span data-ttu-id="92de8-114">In ["Anrufe" und "Onlinebesprechungsbots"](./calls-meetings-bots-overview.md)haben wir die Anrufsignalisierung besprochen– wie Bots neue Anrufe und Ereignisse während eines Anrufs erkennen und darauf reagieren.</span><span class="sxs-lookup"><span data-stu-id="92de8-114">In [Calls and online meetings bots](./calls-meetings-bots-overview.md), we discussed call signaling — how bots detect and respond to new calls and events during a call.</span></span> <span data-ttu-id="92de8-115">Anrufsignalereignisse werden über HTTP POST an den aufrufenden Endpunkt des Bots gesendet.</span><span class="sxs-lookup"><span data-stu-id="92de8-115">Call signaling events are sent via HTTP POST to the bot's calling endpoint.</span></span>

<span data-ttu-id="92de8-116">Wie bei der Messaging-API des Bots muss Ihr Bot über das Internet erreichbar sein, damit die Medienplattform in Echtzeit mit Ihrem Bot sprechen kann.</span><span class="sxs-lookup"><span data-stu-id="92de8-116">As with the bot's messaging API, in order for the Real-time Media Platform to talk to your bot, your bot must be reachable over the internet.</span></span> <span data-ttu-id="92de8-117">Ngrok macht dies einfach – fügen Sie ihrer ngrok.yml die folgenden Zeilen hinzu:</span><span class="sxs-lookup"><span data-stu-id="92de8-117">Ngrok makes this simple — add the following lines to your ngrok.yml:</span></span>

```yaml
tunnels:
    signaling:
        addr: 12345
        proto: http
```

## <a name="setting-up-local-media"></a><span data-ttu-id="92de8-118">Einrichten lokaler Medien</span><span class="sxs-lookup"><span data-stu-id="92de8-118">Setting up local media</span></span>

> [!NOTE]
> <span data-ttu-id="92de8-119">Dieser Abschnitt ist nur für in der Anwendung gehostete Medienbots erforderlich und kann übersprungen werden, wenn Sie medien nicht selbst hosten.</span><span class="sxs-lookup"><span data-stu-id="92de8-119">This section is only required for application-hosted media bots and can be skipped if you don't host media yourself.</span></span>

<span data-ttu-id="92de8-120">In der Anwendung gehostete Medien verwenden Zertifikate und TCP-Tunnel.</span><span class="sxs-lookup"><span data-stu-id="92de8-120">Application-hosted media uses certificates and TCP tunnels.</span></span> <span data-ttu-id="92de8-121">Die folgenden Schritte sind erforderlich:</span><span class="sxs-lookup"><span data-stu-id="92de8-121">The following steps are required:</span></span>

- <span data-ttu-id="92de8-122">Die öffentlichen TCP-Endpunkte von Ngrok verfügen über feste URLs.</span><span class="sxs-lookup"><span data-stu-id="92de8-122">Ngrok's public TCP endpoints have fixed URLs.</span></span> <span data-ttu-id="92de8-123">Sie sind `0.tcp.ngrok.io` , `1.tcp.ngrok.io` und so weiter.</span><span class="sxs-lookup"><span data-stu-id="92de8-123">They are `0.tcp.ngrok.io`, `1.tcp.ngrok.io`, and so on.</span></span> <span data-ttu-id="92de8-124">Sie sollten über einen DNS-CNAME-Eintrag für Ihren Dienst verfügen, der auf diese URLs verweist.</span><span class="sxs-lookup"><span data-stu-id="92de8-124">You should have a DNS CNAME entry for your service that points to these URLs.</span></span> <span data-ttu-id="92de8-125">In diesem Beispiel bezieht sich dies beispielsweise `0.bot.contoso.com` auf , bezieht sich auf und so `0.tcp.ngrok.io` `1.bot.contoso.com` `1.tcp.ngrok.io` weiter.</span><span class="sxs-lookup"><span data-stu-id="92de8-125">In this example, let's say `0.bot.contoso.com` refers to `0.tcp.ngrok.io`, `1.bot.contoso.com` refers to `1.tcp.ngrok.io`, and so on.</span></span>
- <span data-ttu-id="92de8-126">Für Ihre URLs ist ein SSL-Zertifikat erforderlich.</span><span class="sxs-lookup"><span data-stu-id="92de8-126">A SSL certificate is required for your URLs.</span></span> <span data-ttu-id="92de8-127">Um dies einfach zu machen, verwenden Sie ein SSL-Zertifikat, das für eine Platzhalterdomäne ausgestellt wurde.</span><span class="sxs-lookup"><span data-stu-id="92de8-127">To make it easy, use a SSL certificate issued to a wild card domain.</span></span> <span data-ttu-id="92de8-128">In diesem Fall wäre dies `*.bot.contoso.com` .</span><span class="sxs-lookup"><span data-stu-id="92de8-128">In this case, it would be `*.bot.contoso.com`.</span></span> <span data-ttu-id="92de8-129">Dieses SSL-Zertifikat wird vom Medien-SDK überprüft und sollte daher mit der öffentlichen URL Ihres Bots übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="92de8-129">This SSL certificate is validated by the media SDK, so it should match your bot's public URL.</span></span> <span data-ttu-id="92de8-130">Notieren Sie sich den Fingerabdruck, und installieren Sie ihn in Ihren Computerzertifikaten.</span><span class="sxs-lookup"><span data-stu-id="92de8-130">Note the thumbprint and install it in your machine certificates.</span></span>
- <span data-ttu-id="92de8-131">Richten Sie nun einen TCP-Tunnel ein, um den Datenverkehr an "localhost" weiter zu weiterleiten.</span><span class="sxs-lookup"><span data-stu-id="92de8-131">Now, setup a TCP tunnel to forward the traffic to localhost.</span></span> <span data-ttu-id="92de8-132">Schreiben Sie die folgenden Zeilen in ngrok.yml:</span><span class="sxs-lookup"><span data-stu-id="92de8-132">Write the following lines into your ngrok.yml:</span></span>

    ```yaml
    media:
        addr: 8445
        proto: tcp
    ```

## <a name="start-ngrok"></a><span data-ttu-id="92de8-133">ngrok starten</span><span class="sxs-lookup"><span data-stu-id="92de8-133">Start ngrok</span></span>

<span data-ttu-id="92de8-134">Nachdem die ngrok-Konfiguration nun bereit ist, starten Sie sie:</span><span class="sxs-lookup"><span data-stu-id="92de8-134">Now that the ngrok configuration is ready, launch it:</span></span>

  `ngrok.exe start -all -config <Path to your ngrok.yml>`

<span data-ttu-id="92de8-135">Dadurch wird ngrok gestartet und die öffentlichen URLs definiert, die die Tunnel für Ihren localhost bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="92de8-135">This starts ngrok and defines the public URLs which provide the tunnels to your localhost.</span></span> <span data-ttu-id="92de8-136">Die Ausgabe sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="92de8-136">The output looks like the following:</span></span>

```cmd
Forwarding  http://signal.ngrok.io -> localhost:12345
Forwarding  https://signal.ngrok.io -> localhost:12345
Forwarding  tcp://1.tcp.ngrok.io:12332 -> localhost:8445
```

<span data-ttu-id="92de8-137">Hier ist der Signalport, der von der Anwendung gehostete Port und der von ngrok verfügbar gemachte `12345` `8445` `12332` Remotemedienport.</span><span class="sxs-lookup"><span data-stu-id="92de8-137">Here, `12345` is the signaling port, `8445` is the application-hosted port, and `12332` is the remote media port exposed by ngrok.</span></span> <span data-ttu-id="92de8-138">Beachten Sie, dass wir eine Weiterleitung von `1.bot.contoso.com` zu `1.tcp.ngrok.io` haben.</span><span class="sxs-lookup"><span data-stu-id="92de8-138">Note that we have a forwarding from `1.bot.contoso.com` to `1.tcp.ngrok.io`.</span></span> <span data-ttu-id="92de8-139">Diese wird als Medien-URL für den Bot verwendet.</span><span class="sxs-lookup"><span data-stu-id="92de8-139">This will be used as the media URL for the bot.</span></span> <span data-ttu-id="92de8-140">Natürlich sind diese Portnummern nur Beispiele, und Sie können einen beliebigen verfügbaren Port verwenden.</span><span class="sxs-lookup"><span data-stu-id="92de8-140">Of course, these port numbers are just examples and you can use any available port.</span></span>

### <a name="update-code"></a><span data-ttu-id="92de8-141">Aktualisieren des Codes</span><span class="sxs-lookup"><span data-stu-id="92de8-141">Update code</span></span>

<span data-ttu-id="92de8-142">Sobald ngrok ausgeführt wird, aktualisieren Sie den Code so, dass er die konfiguration verwendet, die Sie gerade eingerichtet haben.</span><span class="sxs-lookup"><span data-stu-id="92de8-142">Once ngrok is up and running, update the code to use the config you just set up.</span></span>

#### <a name="update-signaling"></a><span data-ttu-id="92de8-143">Updatesignal</span><span class="sxs-lookup"><span data-stu-id="92de8-143">Update signaling</span></span>

- <span data-ttu-id="92de8-144">Ändern Sie im BotBuilder-Aufruf die `NotificationUrl` Signal-URL, die von ngrok bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="92de8-144">In the BotBuilder call, change the `NotificationUrl` to the signaling URL provided by ngrok.</span></span>

```csharp
statefulClientBuilder.SetNotificationUrl(
    new Uri("https://signal.ngrok.io/notificationEndpoint"))
```

> [!NOTE]
> <span data-ttu-id="92de8-145">Ersetzen Sie das Signal durch das von ngrok bereitgestellte Signal und durch den Controllerpfad, `NotificationEndpoint` der eine Benachrichtigung empfängt.</span><span class="sxs-lookup"><span data-stu-id="92de8-145">Replace signal with the one provided by ngrok and the `NotificationEndpoint` with the controller path that receives notification.</span></span>

> <span data-ttu-id="92de8-146">**WICHTIG:** Die URL muss `SetNotificationUrl` HTTPS sein.</span><span class="sxs-lookup"><span data-stu-id="92de8-146">**IMPORTANT**: The URL in `SetNotificationUrl` must be HTTPS.</span></span>

> <span data-ttu-id="92de8-147">**WICHTIG:** Ihre lokale Instanz muss den HTTP-Datenverkehr auf dem Signalport abhören.</span><span class="sxs-lookup"><span data-stu-id="92de8-147">**IMPORTANT**: Your local instance must be listening to HTTP traffic on the signaling port.</span></span> <span data-ttu-id="92de8-148">Die Anforderungen der Anruf- und Onlinebesprechungsplattform erreichen den Bot als Localhost-HTTP-Datenverkehr, es sei denn, die End-to-End-Verschlüsselung ist eingerichtet.</span><span class="sxs-lookup"><span data-stu-id="92de8-148">The requests made by the calls and online meetings platform will reach the bot as localhost HTTP traffic unless end-to-end encryption is set up.</span></span>

#### <a name="update-media"></a><span data-ttu-id="92de8-149">Medien aktualisieren</span><span class="sxs-lookup"><span data-stu-id="92de8-149">Update media</span></span>

<span data-ttu-id="92de8-150">Aktualisieren Sie `MediaPlatformSettings` Sie auf Folgendes.</span><span class="sxs-lookup"><span data-stu-id="92de8-150">Update your `MediaPlatformSettings` to the following.</span></span>

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
> <span data-ttu-id="92de8-151">Der oben bereitgestellte Zertifikatfingerabdruck sollte mit dem Dienst-FQDN übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="92de8-151">The certificate thumbprint provided above should match the Service FQDN.</span></span> <span data-ttu-id="92de8-152">Aus diesem Grund sind die DNS-Einträge erforderlich.</span><span class="sxs-lookup"><span data-stu-id="92de8-152">That is why the DNS entries are required.</span></span>

## <a name="next-steps"></a><span data-ttu-id="92de8-153">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="92de8-153">Next steps</span></span>

<span data-ttu-id="92de8-154">Ihr Bot kann jetzt lokal ausgeführt werden, und alle Flüsse funktionieren von Ihrem localhost.</span><span class="sxs-lookup"><span data-stu-id="92de8-154">Your bot can now run locally and all the flows work from your localhost.</span></span>

## <a name="caveats"></a><span data-ttu-id="92de8-155">Warnen</span><span class="sxs-lookup"><span data-stu-id="92de8-155">Caveats</span></span>

- <span data-ttu-id="92de8-156">Kostenlose Ngrok-Konten **bieten keine** End-to-End-Verschlüsselung.</span><span class="sxs-lookup"><span data-stu-id="92de8-156">Ngrok free accounts **don't** provide end-to-end encryption.</span></span> <span data-ttu-id="92de8-157">Die HTTPS-Daten enden an der ngrok-URL, und die Datenflüsse werden unverschlüsselt von ngrok zu `localhost` .</span><span class="sxs-lookup"><span data-stu-id="92de8-157">The HTTPS data ends at the ngrok URL and the data flows unencrypted from ngrok to `localhost`.</span></span> <span data-ttu-id="92de8-158">Wenn Sie eine End-to-End-Verschlüsselung benötigen, sollten Sie ein kostenpflichtiges ngrok-Konto in Betracht ziehen.</span><span class="sxs-lookup"><span data-stu-id="92de8-158">If you require end-to-end encryption, consider a paid ngrok account.</span></span> <span data-ttu-id="92de8-159">Schritte [zum Einrichten sicherer](https://ngrok.com/docs#tls) End-to-End-Tunnel finden Sie unter TLS-Tunneln.</span><span class="sxs-lookup"><span data-stu-id="92de8-159">See [TLS tunnels](https://ngrok.com/docs#tls) for steps on setting up secure end-to-end tunnels.</span></span>
- <span data-ttu-id="92de8-160">Da die Botrückruf-URL dynamisch ist, müssen Sie in Szenarien mit eingehenden Anrufen häufig Ihre ngrok-Endpunkte aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="92de8-160">Because the bot callback URL is dynamic, incoming call scenarios require you to frequently update your ngrok endpoints.</span></span> <span data-ttu-id="92de8-161">Eine Möglichkeit, dies zu beheben, ist die Verwendung eines kostenpflichtigen ngrok-Kontos, das feste Unterdomänen bietet, auf die Sie Ihren Bot und die Plattform verweisen können.</span><span class="sxs-lookup"><span data-stu-id="92de8-161">One way to fix this is to use a paid ngrok account which provides fixed subdomains to which you can point your bot and the platform.</span></span>
- <span data-ttu-id="92de8-162">Ngrok-Tunnel können auch mit [Azure Service Fabric verwendet werden.](/azure/service-fabric/service-fabric-overview)</span><span class="sxs-lookup"><span data-stu-id="92de8-162">Ngrok tunnels can also be used with [Azure Service Fabric](/azure/service-fabric/service-fabric-overview).</span></span> <span data-ttu-id="92de8-163">Ein Beispiel dafür finden Sie in der [HueBot-Beispiel-App.](/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/LocalMediaSamples/HueBot/HueBot)</span><span class="sxs-lookup"><span data-stu-id="92de8-163">For an example of how to do this, see the [HueBot sample app](/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/LocalMediaSamples/HueBot/HueBot).</span></span>
