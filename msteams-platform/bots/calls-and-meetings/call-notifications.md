---
title: Eingehende Anrufbenachrichtigungen
description: Detaillierte technische Informationen zum Behandeln von Benachrichtigungen von eingehenden Anrufen
ms.topic: conceptual
keywords: Aufrufen von Anrufbenachrichtigungen Rückrufregionsaffinität
ms.date: 04/02/2019
ms.openlocfilehash: 1ab28f898d2b51b4c1c643006ecac06ca79b2d14
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696402"
---
# <a name="incoming-call-notifications"></a>Eingehende Anrufbenachrichtigungen

Bei [der Registrierung eines Anruf- und Besprechungsbots für Microsoft Teams](./registering-calling-bot.md#create-new-bot-or-add-calling-capabilities)wird der Webhook für das Aufrufen der URL erwähnt. Diese URL ist der Webhook-Endpunkt für alle eingehenden Anrufe an Ihren Bot.

## <a name="protocol-determination"></a>Protokollermittlung

Die eingehende Benachrichtigung wird im Legacyformat bereitgestellt, um die Kompatibilität mit dem vorherigen [Skype-Protokoll zu gewährleisten.](/azure/bot-service/dotnet/bot-builder-dotnet-real-time-media-concepts?view=azure-bot-service-3.0&preserve-view=true) Um den Aufruf an das Microsoft Graph-Protokoll zu konvertieren, muss Ihr Bot ermitteln, ob die Benachrichtigung ein Älteres Format hat, und die folgende Antwort bereitstellen:

```http
HTTP/1.1 204 No Content
```

Ihr Bot empfängt die Benachrichtigung erneut, dieses Mal jedoch im Microsoft Graph-Protokoll.

In einer zukünftigen Version der Echtzeitmedienplattform können Sie das von Der Anwendung unterstützte Protokoll konfigurieren, um den anfänglichen Rückruf im Legacyformat zu vermeiden.

Der nächste Abschnitt enthält Details zu eingehenden Anrufbenachrichtigungen, die für die Regionaffinität zu Ihrer Bereitstellung umgeleitet werden.

## <a name="redirects-for-region-affinity"></a>Umleitungen für die Regionaffinität

Sie rufen Ihren Webhook aus dem Rechenzentrum auf, das den Anruf hosten. Der Anruf beginnt in einem Beliebigen Rechenzentrum und berücksichtigt keine Regionalaffinitäten. Die Benachrichtigung wird abhängig von der GeoDNS-Auflösung an Ihre Bereitstellung gesendet. Wenn Ihre Anwendung durch Überprüfen der ursprünglichen Benachrichtigungsnutzlast oder anderweitig feststellt, dass sie in einer anderen Bereitstellung ausgeführt werden muss, gibt die Anwendung die folgende Antwort:

```http
HTTP/1.1 302 Found
Location: your-new-location
```

Aktivieren Sie Ihren Bot, um einen eingehenden Anruf über die [Antwort-API zu](https://developer.microsoft.com/graph/docs/api-reference/beta/api/call_answer) beantworten. Sie können die `callbackUri` angeben, um diesen bestimmten Anruf zu verarbeiten. Dies ist nützlich für Zustandsinstanzen, in denen Ihr Anruf von einer bestimmten Partition verarbeitet wird, und Sie möchten diese Informationen in die für das Routing an die `callbackUri` richtige Instanz einbetten.

Der nächste Abschnitt enthält Details zur Authentifizierung des Rückrufs durch Überprüfen des Tokens, das in Ihrem Webhook bereitgestellt wurde.

## <a name="authenticate-the-callback"></a>Authentifizieren des Rückrufs

Ihr Bot muss das token überprüfen, das in Ihrem Webhook bereitgestellt wurde, um die Anforderung zu überprüfen. Jedes Mal, wenn die API an den Webhook beiträget, enthält die HTTP-POST-Nachricht ein OAuth-Token im Autorisierungsheader als Bearertoken, bei dem die Zielgruppe die App-ID Ihrer Anwendung ist.

Ihre Anwendung muss dieses Token überprüfen, bevor sie die Rückrufanforderung akzeptiert.

Der folgende Beispielcode wird zum Authentifizieren des Rückrufs verwendet:

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

Das OAuth-Token hat die folgenden Werte und wird von Skype signiert:

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

Die unter veröffentlichte <https://api.aps.skype.com/v1/.well-known/OpenIdConfiguration> OpenID-Konfiguration kann zum Überprüfen des Tokens verwendet werden. Jeder OAuth-Tokenwert wird wie folgt verwendet:

* `aud` dabei ist Audience der für die Anwendung angegebene App-ID-URI.
* `tid` ist die Mandanten-ID für Contoso.com.
* `iss` ist der Tokenherausgeber, `https://api.botframework.com` .

Für die Codeverarbeitung muss der Webhook das Token überprüfen, sicherstellen, dass es nicht abgelaufen ist, und überprüfen, ob es von der veröffentlichten OpenID-Konfiguration signiert wurde. Sie müssen auch überprüfen, ob aud mit Ihrer App-ID entspricht, bevor Sie die Rückrufanforderung akzeptieren.

Weitere Informationen finden Sie unter [Überprüfen eingehender Anforderungen](https://github.com/microsoftgraph/microsoft-graph-comms-samples/blob/master/Samples/Common/Sample.Common/Authentication/AuthenticationProvider.cs).

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Anforderungen und Überlegungen für von der Anwendung gehostete Medienbots](~/bots/calls-and-meetings/requirements-considerations-application-hosted-media-bots.md)
