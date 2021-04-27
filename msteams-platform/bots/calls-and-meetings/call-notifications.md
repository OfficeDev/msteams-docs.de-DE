---
title: Eingehende Anrufbenachrichtigungen
description: Detaillierte technische Informationen zum Behandeln von Benachrichtigungen von eingehenden Anrufen
ms.topic: conceptual
localization_priority: Normal
keywords: Aufrufen von Anrufbenachrichtigungen Rückrufregionsaffinität
ms.date: 04/02/2019
ms.openlocfilehash: 06068c13d27598b9a7b5e70181c69f9efb2c0afb
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020176"
---
# <a name="incoming-call-notifications"></a><span data-ttu-id="610e6-104">Eingehende Anrufbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="610e6-104">Incoming call notifications</span></span>

<span data-ttu-id="610e6-105">Bei [der Registrierung eines Anruf- und Besprechungsbots für Microsoft Teams](./registering-calling-bot.md#create-new-bot-or-add-calling-capabilities)wird der Webhook für das Aufrufen der URL erwähnt.</span><span class="sxs-lookup"><span data-stu-id="610e6-105">In [registering a calls and meetings bot for Microsoft Teams](./registering-calling-bot.md#create-new-bot-or-add-calling-capabilities), the Webhook for calling URL is mentioned.</span></span> <span data-ttu-id="610e6-106">Diese URL ist der Webhook-Endpunkt für alle eingehenden Anrufe an Ihren Bot.</span><span class="sxs-lookup"><span data-stu-id="610e6-106">This URL is the webhook endpoint for all incoming calls to your bot.</span></span>

## <a name="protocol-determination"></a><span data-ttu-id="610e6-107">Protokollermittlung</span><span class="sxs-lookup"><span data-stu-id="610e6-107">Protocol determination</span></span>

<span data-ttu-id="610e6-108">Die eingehende Benachrichtigung wird im Legacyformat bereitgestellt, um die Kompatibilität mit dem vorherigen [Skype-Protokoll zu gewährleisten.](/azure/bot-service/dotnet/bot-builder-dotnet-real-time-media-concepts?view=azure-bot-service-3.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="610e6-108">The incoming notification is provided in a legacy format for compatibility with the previous [Skype protocol](/azure/bot-service/dotnet/bot-builder-dotnet-real-time-media-concepts?view=azure-bot-service-3.0&preserve-view=true).</span></span> <span data-ttu-id="610e6-109">Um den Aufruf an das Microsoft Graph-Protokoll zu konvertieren, muss Ihr Bot ermitteln, ob die Benachrichtigung ein Älteres Format hat, und die folgende Antwort bereitstellen:</span><span class="sxs-lookup"><span data-stu-id="610e6-109">In order to convert the call to the Microsoft Graph protocol, your bot must determine whether the notification is in a legacy format and provide the following response:</span></span>

```http
HTTP/1.1 204 No Content
```

<span data-ttu-id="610e6-110">Ihr Bot empfängt die Benachrichtigung erneut, dieses Mal jedoch im Microsoft Graph-Protokoll.</span><span class="sxs-lookup"><span data-stu-id="610e6-110">Your bot receives the notification again, but this time in the Microsoft Graph protocol.</span></span>

<span data-ttu-id="610e6-111">In einer zukünftigen Version der Echtzeitmedienplattform können Sie das von Der Anwendung unterstützte Protokoll konfigurieren, um den anfänglichen Rückruf im Legacyformat zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="610e6-111">In a future release of the Real-time Media Platform, you can configure the protocol your application supports to avoid receiving the initial callback in the legacy format.</span></span>

<span data-ttu-id="610e6-112">Der nächste Abschnitt enthält Details zu eingehenden Anrufbenachrichtigungen, die für die Regionaffinität zu Ihrer Bereitstellung umgeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="610e6-112">The next section provides details on incoming call notifications redirected for region affinity to your deployment.</span></span>

## <a name="redirects-for-region-affinity"></a><span data-ttu-id="610e6-113">Umleitungen für die Regionaffinität</span><span class="sxs-lookup"><span data-stu-id="610e6-113">Redirects for region affinity</span></span>

<span data-ttu-id="610e6-114">Sie rufen Ihren Webhook aus dem Rechenzentrum auf, das den Anruf hosten.</span><span class="sxs-lookup"><span data-stu-id="610e6-114">You call your webhook from the data-center hosting the call.</span></span> <span data-ttu-id="610e6-115">Der Anruf beginnt in einem Beliebigen Rechenzentrum und berücksichtigt keine Regionalaffinitäten.</span><span class="sxs-lookup"><span data-stu-id="610e6-115">The call starts in any data center and does not take into account region affinities.</span></span> <span data-ttu-id="610e6-116">Die Benachrichtigung wird abhängig von der GeoDNS-Auflösung an Ihre Bereitstellung gesendet.</span><span class="sxs-lookup"><span data-stu-id="610e6-116">The notification is sent to your deployment depending on the GeoDNS resolution.</span></span> <span data-ttu-id="610e6-117">Wenn Ihre Anwendung durch Überprüfen der ursprünglichen Benachrichtigungsnutzlast oder anderweitig feststellt, dass sie in einer anderen Bereitstellung ausgeführt werden muss, gibt die Anwendung die folgende Antwort:</span><span class="sxs-lookup"><span data-stu-id="610e6-117">If your application determines, by inspecting the initial notification payload or otherwise, that it needs to run in a different deployment, the application provides the following response:</span></span>

```http
HTTP/1.1 302 Found
Location: your-new-location
```

<span data-ttu-id="610e6-118">Aktivieren Sie Ihren Bot, um einen eingehenden Anruf über die [Antwort-API zu](https://developer.microsoft.com/graph/docs/api-reference/beta/api/call_answer) beantworten.</span><span class="sxs-lookup"><span data-stu-id="610e6-118">Enable your bot to answer an incoming call using the [answer](https://developer.microsoft.com/graph/docs/api-reference/beta/api/call_answer) API.</span></span> <span data-ttu-id="610e6-119">Sie können die `callbackUri` angeben, um diesen bestimmten Anruf zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="610e6-119">You can specify the `callbackUri` to handle this particular call.</span></span> <span data-ttu-id="610e6-120">Dies ist nützlich für Zustandsinstanzen, in denen Ihr Anruf von einer bestimmten Partition verarbeitet wird, und Sie möchten diese Informationen in die für das Routing an die `callbackUri` richtige Instanz einbetten.</span><span class="sxs-lookup"><span data-stu-id="610e6-120">This is useful for stateful instances where your call is handled by a particular partition, and you want to embed this information in the `callbackUri` for routing to the right instance.</span></span>

<span data-ttu-id="610e6-121">Der nächste Abschnitt enthält Details zur Authentifizierung des Rückrufs durch Überprüfen des Tokens, das in Ihrem Webhook bereitgestellt wurde.</span><span class="sxs-lookup"><span data-stu-id="610e6-121">The next section provides details on authenticating the callback by inspecting the token posted to your webhook.</span></span>

## <a name="authenticate-the-callback"></a><span data-ttu-id="610e6-122">Authentifizieren des Rückrufs</span><span class="sxs-lookup"><span data-stu-id="610e6-122">Authenticate the callback</span></span>

<span data-ttu-id="610e6-123">Ihr Bot muss das token überprüfen, das in Ihrem Webhook bereitgestellt wurde, um die Anforderung zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="610e6-123">Your bot must inspect the token posted to your webhook to validate the request.</span></span> <span data-ttu-id="610e6-124">Jedes Mal, wenn die API an den Webhook beiträget, enthält die HTTP-POST-Nachricht ein OAuth-Token im Autorisierungsheader als Bearertoken, bei dem die Zielgruppe die App-ID Ihrer Anwendung ist.</span><span class="sxs-lookup"><span data-stu-id="610e6-124">Every time the API posts to the webhook, the HTTP POST message contains an OAuth token in the Authorization header as a bearer token, with the audience as your application's App ID.</span></span>

<span data-ttu-id="610e6-125">Ihre Anwendung muss dieses Token überprüfen, bevor sie die Rückrufanforderung akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="610e6-125">Your application must validate this token before accepting the callback request.</span></span>

<span data-ttu-id="610e6-126">Der folgende Beispielcode wird zum Authentifizieren des Rückrufs verwendet:</span><span class="sxs-lookup"><span data-stu-id="610e6-126">The following sample code is used to authenticate the callback:</span></span>

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

<span data-ttu-id="610e6-127">Das OAuth-Token hat die folgenden Werte und wird von Skype signiert:</span><span class="sxs-lookup"><span data-stu-id="610e6-127">The OAuth token has the following values, and is signed by Skype:</span></span>

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

<span data-ttu-id="610e6-128">Die unter veröffentlichte <https://api.aps.skype.com/v1/.well-known/OpenIdConfiguration> OpenID-Konfiguration kann zum Überprüfen des Tokens verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="610e6-128">The OpenID configuration published at <https://api.aps.skype.com/v1/.well-known/OpenIdConfiguration> can be used to verify the token.</span></span> <span data-ttu-id="610e6-129">Jeder OAuth-Tokenwert wird wie folgt verwendet:</span><span class="sxs-lookup"><span data-stu-id="610e6-129">Each OAuth token value is used as follows:</span></span>

* <span data-ttu-id="610e6-130">`aud` dabei ist Audience der für die Anwendung angegebene App-ID-URI.</span><span class="sxs-lookup"><span data-stu-id="610e6-130">`aud` where audience is the App ID URI specified for the application.</span></span>
* <span data-ttu-id="610e6-131">`tid` ist die Mandanten-ID für Contoso.com.</span><span class="sxs-lookup"><span data-stu-id="610e6-131">`tid` is the tenant id for Contoso.com.</span></span>
* <span data-ttu-id="610e6-132">`iss` ist der Tokenherausgeber, `https://api.botframework.com` .</span><span class="sxs-lookup"><span data-stu-id="610e6-132">`iss` is the token issuer, `https://api.botframework.com`.</span></span>

<span data-ttu-id="610e6-133">Für die Codeverarbeitung muss der Webhook das Token überprüfen, sicherstellen, dass es nicht abgelaufen ist, und überprüfen, ob es von der veröffentlichten OpenID-Konfiguration signiert wurde.</span><span class="sxs-lookup"><span data-stu-id="610e6-133">For your code handling, the webhook must validate the token, ensure it has not expired, and check whether it has been signed by the published OpenID configuration.</span></span> <span data-ttu-id="610e6-134">Sie müssen auch überprüfen, ob aud mit Ihrer App-ID entspricht, bevor Sie die Rückrufanforderung akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="610e6-134">You must also check whether aud matches your App ID before accepting the callback request.</span></span>

<span data-ttu-id="610e6-135">Weitere Informationen finden Sie unter [Überprüfen eingehender Anforderungen](https://github.com/microsoftgraph/microsoft-graph-comms-samples/blob/master/Samples/Common/Sample.Common/Authentication/AuthenticationProvider.cs).</span><span class="sxs-lookup"><span data-stu-id="610e6-135">For more information, see [validate inbound requests](https://github.com/microsoftgraph/microsoft-graph-comms-samples/blob/master/Samples/Common/Sample.Common/Authentication/AuthenticationProvider.cs).</span></span>

## <a name="next-step"></a><span data-ttu-id="610e6-136">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="610e6-136">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="610e6-137">Anforderungen und Überlegungen für von der Anwendung gehostete Medienbots</span><span class="sxs-lookup"><span data-stu-id="610e6-137">Requirements and considerations for application-hosted media bots</span></span>](~/bots/calls-and-meetings/requirements-considerations-application-hosted-media-bots.md)
