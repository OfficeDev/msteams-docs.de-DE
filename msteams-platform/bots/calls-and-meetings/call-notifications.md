---
title: Technische Details zur Behandlung von Benachrichtigungen über eingehende Anrufe
description: Ausführliche technische Informationen zum Behandeln von Benachrichtigungen über eingehende Anrufe
keywords: Calling Calls Notifications Callback Region Affinity
ms.date: 04/02/2019
ms.openlocfilehash: be8860ff70cd7dff4fd9599079ea7aab4f454174
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674501"
---
# <a name="incoming-call-notifications-technical-details"></a><span data-ttu-id="f80b2-104">Benachrichtigungen über eingehende Anrufe: Technische Details</span><span class="sxs-lookup"><span data-stu-id="f80b2-104">Incoming call notifications: technical details</span></span>

<span data-ttu-id="f80b2-105">Bei der [Registrierung eines bot für Anrufe und Besprechungen für Microsoft Teams](./registering-calling-bot.md#creating-a-new-bot-or-adding-calling-capabilities-to-an-existing-bot)erwähnten wir die **webhook-URL (für den Aufruf)** – den webhook-Endpunkt für alle eingehenden Anrufe an Ihren bot.</span><span class="sxs-lookup"><span data-stu-id="f80b2-105">In [Registering a calling and meeting bot for Microsoft Teams](./registering-calling-bot.md#creating-a-new-bot-or-adding-calling-capabilities-to-an-existing-bot), we mentioned the **Webhook (for calling)** URL — the webhook endpoint for all incoming calls to your bot.</span></span> <span data-ttu-id="f80b2-106">In diesem Thema werden die technischen Details erläutert, die Sie für die Reaktion auf diese Benachrichtigungen benötigen.</span><span class="sxs-lookup"><span data-stu-id="f80b2-106">This topic discusses the technical details you'll need to respond to these notifications.</span></span>

## <a name="protocol-determination"></a><span data-ttu-id="f80b2-107">Protokoll Findung</span><span class="sxs-lookup"><span data-stu-id="f80b2-107">Protocol determination</span></span>

<span data-ttu-id="f80b2-108">Die eingehende Benachrichtigung wird im Legacyformat zur Kompatibilität mit dem vorherigen [Skype-Protokoll](/azure/bot-service/dotnet/bot-builder-dotnet-real-time-media-concepts?view=azure-bot-service-3.0)bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="f80b2-108">The incoming notification is provided in legacy format for compatibility with the previous [Skype protocol](/azure/bot-service/dotnet/bot-builder-dotnet-real-time-media-concepts?view=azure-bot-service-3.0).</span></span> <span data-ttu-id="f80b2-109">Um den Anruf in das Microsoft Graph-Protokoll zu konvertieren, muss Ihr bot ermitteln, ob die Benachrichtigung im Legacyformat vorliegt und mit folgendem Antworten:</span><span class="sxs-lookup"><span data-stu-id="f80b2-109">In order to convert the call to the Microsoft Graph protocol, your bot must determine whether the notification is in legacy format and reply with:</span></span>

```http
HTTP/1.1 204 No Content
```

<span data-ttu-id="f80b2-110">Ihr bot erhält die Benachrichtigung erneut, diesmal aber im Microsoft Graph-Protokoll.</span><span class="sxs-lookup"><span data-stu-id="f80b2-110">Your bot will receive the notification again, but this time in the Microsoft Graph protocol.</span></span>

<span data-ttu-id="f80b2-111">In einer zukünftigen Version der Echt Zeit Medienplattform können Sie das Protokoll konfigurieren, das Ihre Anwendung unterstützt, um zu vermeiden, dass der anfängliche Rückruf im Legacyformat empfangen wird.</span><span class="sxs-lookup"><span data-stu-id="f80b2-111">In a future release of the Real-time Media Platform, we'll allow you to configure the protocol your application supports to avoid receiving the initial callback in the legacy format.</span></span>

## <a name="redirects-for-region-affinity"></a><span data-ttu-id="f80b2-112">Umleitungen für die Regions Affinität</span><span class="sxs-lookup"><span data-stu-id="f80b2-112">Redirects for region affinity</span></span>

<span data-ttu-id="f80b2-113">Sie rufen ihren webhook aus dem Rechenzentrum an, das den Anruf hostet.</span><span class="sxs-lookup"><span data-stu-id="f80b2-113">You'll call your webhook from the data-center hosting the call.</span></span> <span data-ttu-id="f80b2-114">Der Anruf wird möglicherweise in einem beliebigen Rechenzentrum gestartet und berücksichtigt keine Regionen-Affinitäten.</span><span class="sxs-lookup"><span data-stu-id="f80b2-114">The call may start in any data center and doesn't take into account region affinities.</span></span> <span data-ttu-id="f80b2-115">Die Benachrichtigung wird in Abhängigkeit von der GeoDNS-Auflösung an Ihre Bereitstellung gesendet.</span><span class="sxs-lookup"><span data-stu-id="f80b2-115">The notification will be sent to your deployment depending on the GeoDNS resolution.</span></span> <span data-ttu-id="f80b2-116">Wenn Ihre Anwendung durch Untersuchen der anfänglichen Benachrichtigungs Nutzlast oder anderweitig feststellt, dass Sie in einer anderen Bereitstellung ausgeführt werden muss, antwortet die Anwendung möglicherweise mit:</span><span class="sxs-lookup"><span data-stu-id="f80b2-116">If your application determines, by inspecting the initial notification payload or otherwise, that it needs to run in a different deployment, the application may reply with:</span></span>

```http
HTTP/1.1 302 Found
Location: your-new-location
```

<span data-ttu-id="f80b2-117">Aktivieren Sie Ihren bot, um einen eingehenden Anruf mit der [Antwort](https://developer.microsoft.com/graph/docs/api-reference/beta/api/call_answer) -API zu beantworten.</span><span class="sxs-lookup"><span data-stu-id="f80b2-117">Enable your bot to answer an incoming call using the [answer](https://developer.microsoft.com/graph/docs/api-reference/beta/api/call_answer) API.</span></span> <span data-ttu-id="f80b2-118">Sie können den `callbackUri` für diesen bestimmten Aufruf zu behandelnden angeben.</span><span class="sxs-lookup"><span data-stu-id="f80b2-118">You can specify the `callbackUri` to handle this particular call.</span></span> <span data-ttu-id="f80b2-119">Dies ist für _Stateful_ -Instanzen hilfreich, bei denen der Anruf von einer bestimmten Partition verarbeitet wird und Sie diese Informationen in das `callbackUri` für das Routing an die richtige Instanz einbetten möchten.</span><span class="sxs-lookup"><span data-stu-id="f80b2-119">This is useful for _stateful_ instances where your call is handled by a particular partition and you want to embed this information in the `callbackUri` for routing to the right instance.</span></span>

## <a name="authenticating-the-callback"></a><span data-ttu-id="f80b2-120">Authentifizieren des Rückrufs</span><span class="sxs-lookup"><span data-stu-id="f80b2-120">Authenticating the callback</span></span>

<span data-ttu-id="f80b2-121">Ihr bot sollte das auf Ihrem webhook gepostete Token überprüfen, um die Anforderung zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="f80b2-121">Your bot should inspect the token posted to your webhook to validate the request.</span></span> <span data-ttu-id="f80b2-122">Wenn die API an den webhook gesendet wird, enthält die HTTP Post-Nachricht ein OAuth-Token im Autorisierungsheader als Träger Token, wobei die Benutzergruppe als APP-ID Ihrer Anwendung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="f80b2-122">Whenever the API posts to the webhook, the HTTP POST message contains an OAuth token in the Authorization header as a Bearer token, with audience as your application's App ID.</span></span>

<span data-ttu-id="f80b2-123">Ihre Anwendung sollte dieses Token überprüfen, bevor Sie die Rückrufanforderung akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="f80b2-123">Your application should validate this token before accepting the callback request.</span></span>

```http
POST https://bot.contoso.com/api/calls
Content-Type: application/json
Authentication: Bearer <TOKEN>

"value": [
    "subscriptionId": "2887CEE8344B47C291F1AF628599A93C",
    "subscriptionExpirationDateTime": "2016-11-20T18:23:45.9356913Z",
    "changeType": "updated",
    "resource": "/app/calls/8A934F51F25B4EE19613D4049491857B",
    "resourceData": {
        "@odata.type": "#microsoft.graph.call",
        "state": "Established"
    }
]
```

<span data-ttu-id="f80b2-124">Das OAuth-Token enthält Werte wie die folgenden und wird von Skype signiert.</span><span class="sxs-lookup"><span data-stu-id="f80b2-124">The OAuth token will have values like the following, and will be signed by Skype.</span></span> <span data-ttu-id="f80b2-125">Die OpenID-Konfiguration, <https://api.aps.skype.com/v1/.well-known/OpenIdConfiguration> die veröffentlicht wird, kann verwendet werden, um das Token zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="f80b2-125">The OpenID configuration published at <https://api.aps.skype.com/v1/.well-known/OpenIdConfiguration> can be used to verify the token.</span></span>

```json
{
    "aud": "0efc74f7-41c3-47a4-8775-7259bfef4241",
    "iss": "https://api.botframework.com",
    "iat": 1466741440,
    "nbf": 1466741440,
    "exp": 1466745340,
    "tid": "1fdd12d0-4620-44ed-baec-459b611f84b2"
}
```

* <span data-ttu-id="f80b2-126">**AUD** Zielgruppe ist der für die Anwendung angegebene APP-ID-URI.</span><span class="sxs-lookup"><span data-stu-id="f80b2-126">**aud** audience is the App ID URI specified for the application.</span></span>
* <span data-ttu-id="f80b2-127">**TID** ist die Mandanten-ID für contoso.com.</span><span class="sxs-lookup"><span data-stu-id="f80b2-127">**tid** is the tenant id for Contoso.com.</span></span>
* <span data-ttu-id="f80b2-128">**ISS** ist der Token-Aussteller, `https://api.botframework.com`.</span><span class="sxs-lookup"><span data-stu-id="f80b2-128">**iss** is the token issuer, `https://api.botframework.com`.</span></span>

<span data-ttu-id="f80b2-129">Ihr Code, der den webhook verarbeitet, sollte das Token validieren, sicherstellen, dass es nicht abgelaufen ist, und überprüfen, ob es von unserer veröffentlichten OpenID-Konfiguration signiert wurde.</span><span class="sxs-lookup"><span data-stu-id="f80b2-129">Your code handling the webhook should validate the token, ensure it hasn't expired, and check whether it has been signed by our published OpenID configuration.</span></span> <span data-ttu-id="f80b2-130">Sie sollten auch überprüfen, ob **AUD** mit Ihrer APP-ID übereinstimmt, bevor Sie die Rückrufanforderung annehmen.</span><span class="sxs-lookup"><span data-stu-id="f80b2-130">You should also check whether **aud** matches your App ID before accepting the callback request.</span></span>

<span data-ttu-id="f80b2-131">[Beispiel](https://github.com/microsoftgraph/microsoft-graph-comms-samples/blob/master/Samples/Common/Sample.Common/Authentication/AuthenticationProvider.cs) zeigt, wie eingehende Anforderungen überprüft werden.</span><span class="sxs-lookup"><span data-stu-id="f80b2-131">[Sample](https://github.com/microsoftgraph/microsoft-graph-comms-samples/blob/master/Samples/Common/Sample.Common/Authentication/AuthenticationProvider.cs) shows how to validate inbound requests.</span></span>
