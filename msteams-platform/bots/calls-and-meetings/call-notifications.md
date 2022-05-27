---
title: Eingehende Anrufbenachrichtigungen
description: Lernen Sie anhand von Codebeispielen detaillierte technische Informationen zur Behandlung von Benachrichtigungen bei eingehenden Anrufen und zur Umleitung und Authentifizierung von Anrufen kennen
ms.topic: conceptual
ms.localizationpriority: medium
keywords: Affinität zwischen Rückrufregion und Anrufbenachrichtigungen
ms.date: 04/02/2019
ms.openlocfilehash: e2844649764284f74e242967106adbfdc8edf8cf
ms.sourcegitcommit: eeaa8cbb10b9dfa97e9c8e169e9940ddfe683a7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2022
ms.locfileid: "65757143"
---
# <a name="incoming-call-notifications"></a>Eingehende Anrufbenachrichtigungen

In [Registrieren eines Anruf- und Besprechungsbots für Microsoft Teams](./registering-calling-bot.md#create-new-bot-or-add-calling-capabilities)wird der Webhook für die Anruf-URL erwähnt. Diese URL ist der Webhook-Endpunkt für alle eingehenden Anrufe an Ihren Bot.

## <a name="protocol-determination"></a>Protokollermittlung

Die eingehende Benachrichtigung wird aus Gründen der Kompatibilität mit dem früheren [Skype-Protokoll](/azure/bot-service/dotnet/bot-builder-dotnet-real-time-media-concepts?view=azure-bot-service-3.0&preserve-view=true) in einem Legacy-Format bereitgestellt. Um den Aufruf in das Microsoft Graph-Protokoll zu konvertieren, muss Ihr Bot ermitteln, ob die Benachrichtigung im Legacyformat vorliegt, und die folgende Antwort liefert:

```http
HTTP/1.1 204 No Content
```

Ihr Bot empfängt die Benachrichtigung erneut, dieses Mal jedoch im Microsoft Graph-Protokoll.

In einer zukünftigen Version der Echtzeitmedienplattform können Sie das Protokoll konfigurieren, das Ihre Anwendung unterstützt, um zu vermeiden, dass der erste Rückruf im Legacyformat empfangen wird.

Der nächste Abschnitt enthält Einzelheiten zu eingehenden Anrufbenachrichtigungen, die aufgrund der Regionszugehörigkeit zu Ihrer Einrichtung umgeleitet werden.

## <a name="redirects-for-region-affinity"></a>Umleitungen für Regionsaffinität

Sie rufen Ihren Webhook aus dem Rechenzentrum an, in dem der Anruf gehostet wird. Der Anruf beginnt in einem beliebigen Rechenzentrum und berücksichtigt keine Regionsaffinitäten. Die Benachrichtigung wird abhängig von der GeoDNS-Auflösung an Ihre Bereitstellung gesendet. Wenn Ihre Anwendung durch Untersuchen der ersten Benachrichtigungsnutzlast oder anderweitig feststellt, dass sie in einer anderen Bereitstellung ausgeführt werden muss, liefert die Anwendung die folgende Antwort:

```http
HTTP/1.1 302 Found
Location: your-new-location
```

Aktivieren Sie Ihren Bot, um einen eingehenden Anruf über die [Antwort](/graph/api/call-answer?view=graph-rest-1.0&tabs=http&preserve-view=true)-API zu beantworten. Sie können die `callbackUri` angeben, um diesen bestimmten Aufruf zu verarbeiten. Dies ist nützlich für zustandsbehaftete Instanzen, bei denen Ihr Aufruf von einer bestimmten Partition verarbeitet wird und Sie diese Informationen in den `callbackUri` einbetten möchten, um das Routing zur richtigen Instanz auszuführen.

Der nächste Abschnitt enthält Details zur Authentifizierung des Rückrufs durch Überprüfen des in Ihrem Webhook geposteten Tokens.

## <a name="authenticate-the-callback"></a>Authentifizieren des Rückrufs

Ihr Bot muss das an Ihren Webhook gesendete Token überprüfen, um die Anfrage zu validieren. Jedes Mal, wenn die API an den Webhook sendet, enthält die HTTP-POST-Nachricht ein OAuth-Token im Authorization-Header als Bearer-Token, wobei das Publikum die App-ID Ihrer Anwendung ist.

Ihre Anwendung muss dieses Token überprüfen, bevor sie die Rückrufanforderung akzeptiert.

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

Die auf <https://api.aps.skype.com/v1/.well-known/OpenIdConfiguration> veröffentlichte OpenID-Konfiguration kann zum Überprüfen des Tokens verwendet werden. Jeder OAuth-Tokenwert wird wie folgt verwendet:

* `aud` wobei die Zielgruppe die für die Anwendung angegebene App ID URI ist.
* `tid` ist die Mandanten-ID für Contoso.com.
* `iss` ist der Tokenherausgeber, `https://api.botframework.com`.

Für die Codebehandlung muss der Webhook das Token überprüfen, sicherstellen, dass es nicht abgelaufen ist, und überprüfen, ob es von der veröffentlichten OpenID-Konfiguration signiert wurde. Sie müssen auch überprüfen, ob aud Ihrer App-ID entspricht, bevor Sie die Rückrufanforderung annehmen.

Weitere Informationen finden Sie unter [Überprüfen eingehender Anforderungen](https://github.com/microsoftgraph/microsoft-graph-comms-samples/blob/master/Samples/Common/Sample.Common/Authentication/AuthenticationProvider.cs).

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Anforderungen und Überlegungen für anwendungsgehostete Medienbots](~/bots/calls-and-meetings/requirements-considerations-application-hosted-media-bots.md)

## <a name="see-also"></a>Siehe auch

* [Einrichten einer automatischen Telefonzentrale](/microsoftteams/create-a-phone-system-auto-attendant)
* [Einrichten der automatischen Antwort für Microsoft Teams-Räume auf Android- und Teams Videotelefongeräten](/microsoftteams/set-up-auto-answer-on-teams-android)