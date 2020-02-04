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
# <a name="incoming-call-notifications-technical-details"></a>Benachrichtigungen über eingehende Anrufe: Technische Details

Bei der [Registrierung eines bot für Anrufe und Besprechungen für Microsoft Teams](./registering-calling-bot.md#creating-a-new-bot-or-adding-calling-capabilities-to-an-existing-bot)erwähnten wir die **webhook-URL (für den Aufruf)** – den webhook-Endpunkt für alle eingehenden Anrufe an Ihren bot. In diesem Thema werden die technischen Details erläutert, die Sie für die Reaktion auf diese Benachrichtigungen benötigen.

## <a name="protocol-determination"></a>Protokoll Findung

Die eingehende Benachrichtigung wird im Legacyformat zur Kompatibilität mit dem vorherigen [Skype-Protokoll](/azure/bot-service/dotnet/bot-builder-dotnet-real-time-media-concepts?view=azure-bot-service-3.0)bereitgestellt. Um den Anruf in das Microsoft Graph-Protokoll zu konvertieren, muss Ihr bot ermitteln, ob die Benachrichtigung im Legacyformat vorliegt und mit folgendem Antworten:

```http
HTTP/1.1 204 No Content
```

Ihr bot erhält die Benachrichtigung erneut, diesmal aber im Microsoft Graph-Protokoll.

In einer zukünftigen Version der Echt Zeit Medienplattform können Sie das Protokoll konfigurieren, das Ihre Anwendung unterstützt, um zu vermeiden, dass der anfängliche Rückruf im Legacyformat empfangen wird.

## <a name="redirects-for-region-affinity"></a>Umleitungen für die Regions Affinität

Sie rufen ihren webhook aus dem Rechenzentrum an, das den Anruf hostet. Der Anruf wird möglicherweise in einem beliebigen Rechenzentrum gestartet und berücksichtigt keine Regionen-Affinitäten. Die Benachrichtigung wird in Abhängigkeit von der GeoDNS-Auflösung an Ihre Bereitstellung gesendet. Wenn Ihre Anwendung durch Untersuchen der anfänglichen Benachrichtigungs Nutzlast oder anderweitig feststellt, dass Sie in einer anderen Bereitstellung ausgeführt werden muss, antwortet die Anwendung möglicherweise mit:

```http
HTTP/1.1 302 Found
Location: your-new-location
```

Aktivieren Sie Ihren bot, um einen eingehenden Anruf mit der [Antwort](https://developer.microsoft.com/graph/docs/api-reference/beta/api/call_answer) -API zu beantworten. Sie können den `callbackUri` für diesen bestimmten Aufruf zu behandelnden angeben. Dies ist für _Stateful_ -Instanzen hilfreich, bei denen der Anruf von einer bestimmten Partition verarbeitet wird und Sie diese Informationen in das `callbackUri` für das Routing an die richtige Instanz einbetten möchten.

## <a name="authenticating-the-callback"></a>Authentifizieren des Rückrufs

Ihr bot sollte das auf Ihrem webhook gepostete Token überprüfen, um die Anforderung zu überprüfen. Wenn die API an den webhook gesendet wird, enthält die HTTP Post-Nachricht ein OAuth-Token im Autorisierungsheader als Träger Token, wobei die Benutzergruppe als APP-ID Ihrer Anwendung angezeigt wird.

Ihre Anwendung sollte dieses Token überprüfen, bevor Sie die Rückrufanforderung akzeptieren.

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

Das OAuth-Token enthält Werte wie die folgenden und wird von Skype signiert. Die OpenID-Konfiguration, <https://api.aps.skype.com/v1/.well-known/OpenIdConfiguration> die veröffentlicht wird, kann verwendet werden, um das Token zu überprüfen.

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

* **AUD** Zielgruppe ist der für die Anwendung angegebene APP-ID-URI.
* **TID** ist die Mandanten-ID für contoso.com.
* **ISS** ist der Token-Aussteller, `https://api.botframework.com`.

Ihr Code, der den webhook verarbeitet, sollte das Token validieren, sicherstellen, dass es nicht abgelaufen ist, und überprüfen, ob es von unserer veröffentlichten OpenID-Konfiguration signiert wurde. Sie sollten auch überprüfen, ob **AUD** mit Ihrer APP-ID übereinstimmt, bevor Sie die Rückrufanforderung annehmen.

[Beispiel](https://github.com/microsoftgraph/microsoft-graph-comms-samples/blob/master/Samples/Common/Sample.Common/Authentication/AuthenticationProvider.cs) zeigt, wie eingehende Anforderungen überprüft werden.
