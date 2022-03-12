---
title: Eingehende Anrufbenachrichtigungen
description: Erfahren Sie mehr über detaillierte technische Informationen zum Umgang mit Benachrichtigungen bei eingehenden Anrufen, zum Umleiten und Authentifizieren von Anrufen mithilfe von Codebeispielen.
ms.topic: conceptual
ms.localizationpriority: medium
keywords: Anrufbenachrichtigungen Rückrufregion Affinität aufrufen
ms.date: 04/02/2019
ms.openlocfilehash: a1d2362347643badc06a23d967120c8f14a17200
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2022
ms.locfileid: "63453054"
---
# <a name="incoming-call-notifications"></a>Eingehende Anrufbenachrichtigungen

Bei [der Registrierung eines Anruf- und Besprechungsbots für Microsoft Teams](./registering-calling-bot.md#create-new-bot-or-add-calling-capabilities) wird der Webhook für die Anruf-URL erwähnt. Diese URL ist der Webhook-Endpunkt für alle eingehenden Anrufe an Ihren Bot.

## <a name="protocol-determination"></a>Protokollermittlung

Die eingehende Benachrichtigung wird aus Gründen der Kompatibilität mit dem vorherigen [Skype-Protokoll](/azure/bot-service/dotnet/bot-builder-dotnet-real-time-media-concepts?view=azure-bot-service-3.0&preserve-view=true) in einem älteren Format bereitgestellt. Um den Aufruf in das Microsoft Graph-Protokoll zu konvertieren, muss Ihr Bot bestimmen, ob die Benachrichtigung ein Legacyformat aufweist, und die folgende Antwort bereitstellen:

```http
HTTP/1.1 204 No Content
```

Ihr Bot empfängt die Benachrichtigung erneut, aber dieses Mal im Microsoft Graph-Protokoll.

In einer zukünftigen Version der Real-Time Media Platform können Sie das Protokoll konfigurieren, das Ihre Anwendung unterstützt, um zu vermeiden, dass der anfängliche Rückruf im Legacyformat empfangen wird.

Der nächste Abschnitt enthält Details zu eingehenden Anrufbenachrichtigungen, die für die Regionsaffinität zu Ihrer Bereitstellung umgeleitet werden.

## <a name="redirects-for-region-affinity"></a>Umleitungen für Regionsaffinität

Sie rufen Ihren Webhook aus dem Rechenzentrum an, in dem der Anruf gehostet wird. Der Anruf beginnt in einem beliebigen Rechenzentrum und berücksichtigt keine Regionsaffinitäten. Die Benachrichtigung wird abhängig von der GeoDNS-Auflösung an Ihre Bereitstellung gesendet. Wenn Ihre Anwendung feststellt, dass sie in einer anderen Bereitstellung ausgeführt werden muss, indem sie die anfängliche Benachrichtigungsnutzlast überprüft oder anderweitig überprüft, gibt die Anwendung die folgende Antwort aus:

```http
HTTP/1.1 302 Found
Location: your-new-location
```

Ermöglichen Sie Ihrem Bot, einen eingehenden Anruf mithilfe der [Antwort-API](/graph/api/call-answer?view=graph-rest-1.0&tabs=http&preserve-view=true) zu beantworten. Sie können den `callbackUri` für diesen bestimmten Aufruf zu verwendenden Wert angeben. Dies ist nützlich für zustandsbehaftete Instanzen, in denen Ihr Anruf von einer bestimmten Partition verarbeitet wird, und Sie möchten diese Informationen für das `callbackUri` Routing an die richtige Instanz einbetten.

Der nächste Abschnitt enthält Details zum Authentifizieren des Rückrufs, indem das Token überprüft wird, das in Ihrem Webhook veröffentlicht wurde.

## <a name="authenticate-the-callback"></a>Authentifizieren des Rückrufs

Ihr Bot muss das in Ihrem Webhook gepostete Token überprüfen, um die Anforderung zu überprüfen. Jedes Mal, wenn die API im Webhook postet, enthält die HTTP POST-Nachricht ein OAuth-Token im Autorisierungsheader als Bearertoken, wobei die Zielgruppe die App-ID Ihrer Anwendung ist.

Ihre Anwendung muss dieses Token überprüfen, bevor die Rückrufanforderung akzeptiert wird.

Der folgende Beispielcode wird verwendet, um den Rückruf zu authentifizieren:

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

Die openID-Konfiguration, die unter <https://api.aps.skype.com/v1/.well-known/OpenIdConfiguration> veröffentlicht wurde, kann verwendet werden, um das Token zu überprüfen. Jeder OAuth-Tokenwert wird wie folgt verwendet:

* `aud` dabei ist "audience" der app-ID-URI, der für die Anwendung angegeben ist.
* `tid` ist die Mandanten-ID für Contoso.com.
* `iss`ist der Tokenaussteller. `https://api.botframework.com`

Für die Codeverarbeitung muss der Webhook das Token überprüfen, sicherstellen, dass es nicht abgelaufen ist, und überprüfen, ob es von der veröffentlichten OpenID-Konfiguration signiert wurde. Sie müssen auch überprüfen, ob "aud" ihrer App-ID entspricht, bevor Sie die Rückrufanforderung annehmen.

Weitere Informationen finden Sie unter [Überprüfen eingehender Anforderungen](https://github.com/microsoftgraph/microsoft-graph-comms-samples/blob/master/Samples/Common/Sample.Common/Authentication/AuthenticationProvider.cs).

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Anforderungen und Überlegungen für von der Anwendung gehostete Medienbots](~/bots/calls-and-meetings/requirements-considerations-application-hosted-media-bots.md)
