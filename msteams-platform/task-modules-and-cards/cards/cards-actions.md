---
title: Hinzufügen von Kartenaktionen in einem Bot
description: Beschreibt Kartenaktionen in Microsoft Teams und wie Sie sie in Ihren Bots verwenden
localization_priority: Normal
ms.topic: conceptual
keywords: Teams Bots Karten Aktionen
ms.openlocfilehash: b9276c7197070df43ba447707e6fa4d3d4098591
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566852"
---
# <a name="card-actions"></a>Kartenaktionen

Karten, die von Bots und Messaging-Erweiterungen in Teams verwendet werden, unterstützen die folgenden Aktivitätstypen ( [`CardAction`](/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments#process-events-within-rich-cards) ). Beachten Sie, dass sich diese Aktionen von `potentialActions` Office 365 Connectorkarten unterscheiden, wenn sie von Connectors verwendet werden.

| Typ | Aktion |
| --- | --- |
| `openUrl` | Öffnet eine URL im Standardbrowser. |
| `messageBack` | Sendet eine Nachricht und Nutzlast an den Bot von dem Benutzer, der auf die Schaltfläche geklickt oder auf die Karte getippt hat und eine separate Nachricht an den Chat-Stream sendet. |
| `imBack`| Sendet eine Nachricht an den Bot von dem Benutzer, der auf die Schaltfläche geklickt oder auf die Karte getippt hat. Diese Nachricht (vom Benutzer zum Bot) ist für alle Gesprächsteilnehmer sichtbar. |
| `invoke` | Sendet eine Nachricht und Nutzlast an den Bot von dem Benutzer, der auf die Schaltfläche geklickt oder auf die Karte getippt hat. Diese Meldung ist nicht sichtbar. |
| `signin` | Initiiert den OAuth-Fluss, sodass Bots eine Verbindung mit sicheren Diensten herstellen können. |

> [!NOTE]
>* Teams unterstützt keine `CardAction` Typen, die in der obigen Tabelle nicht aufgeführt sind.
>* Teams unterstützt die `potentialActions` Unterkunft nicht.
>* Kartenaktionen unterscheiden sich von [den vorgeschlagenen Aktionen](/azure/bot-service/bot-builder-howto-add-suggested-actions?view=azure-bot-service-4.0&tabs=javascript#suggest-action-using-button&preserve-view=true) in Bot Framework/Azure Bot Service. Vorgeschlagene Aktionen werden in Microsoft Teams nicht unterstützt: Wenn Schaltflächen auf einer Teams-Bot-Nachricht angezeigt werden sollen, verwenden Sie eine Karte.
>* Wenn Sie eine Kartenaktion als Teil einer Messagingerweiterung verwenden, funktionieren die Aktionen erst, wenn die Karte an den Kanal gesendet wird. Sie funktionieren nicht, während sich die Karte im Meldungsfeld verfassen befindet.

Teams unterstützt auch [Adaptive Cards-Aktionen](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions), die nur von Adaptive Cards verwendet werden. Diese Aktionen werden in ihrem eigenen Abschnitt am Ende dieses Verweises aufgeführt.

## <a name="openurl"></a>OpenURL

Dieser Aktionstyp gibt eine URL an, die im Standardbrowser gestartet werden soll. Beachten Sie, dass Ihr Bot keine Benachrichtigung darüber erhält, auf welche Schaltfläche geklickt wurde.

Das `value` Feld muss eine vollständige und ordnungsgemäß formatierte URL enthalten.

```json
{
    "type": "openUrl",
    "title": "Tabs in Teams",
    "value": "https://msdn.microsoft.com/microsoft-teams/tabs"
}
```

## <a name="messageback"></a>MessageBack

Mit `messageBack` können Sie eine vollständig angepasste Aktion mit den folgenden Eigenschaften erstellen:

| Eigenschaft | Beschreibung |
| --- | --- |
| `title` | Wird als Schaltflächenbeschriftung angezeigt. |
| `displayText` | Optional. Wird vom Benutzer in den Chat-Stream eingefügt, wenn die Aktion ausgeführt wird. Dieser Text wird *nicht* an Ihren Bot gesendet. |
| `value` | Wird an Ihren Bot gesendet, wenn die Aktion ausgeführt wird. Sie können den Kontext für die Aktion kodieren, z. B. eindeutige Bezeichner oder ein JSON-Objekt. |
| `text` | Wird an Ihren Bot gesendet, wenn die Aktion ausgeführt wird. Verwenden Sie diese Eigenschaft, um die Bot-Entwicklung zu vereinfachen: Ihr Code kann eine einzelne Eigenschaft der obersten Ebene überprüfen, um Botlogik zu versenden. |

Die Flexibilität der `messageBack` Mittel, dass Ihr Code nicht eine sichtbare Benutzernachricht im Verlauf verlassen kann, indem Sie einfach nicht `displayText` .

```json
{
  "buttons": [
    {
    "type": "messageBack",
    "title": "My MessageBack button",
    "displayText": "I clicked this button",
    "text": "User just clicked the MessageBack button",
    "value": "{\"property\": \"propertyValue\" }"
    }
  ]
}
```

Die `value` Eigenschaft kann entweder eine serialisierte JSON-Zeichenfolge oder ein JSON-Objekt sein.

### <a name="inbound-message-example"></a>Beispiel für eingehende Nachrichten

`replyToId` enthält die ID der Nachricht, aus der die Kartenaktion stammt. Verwenden Sie sie, wenn Sie die Nachricht aktualisieren möchten.

```json
{
   "text":"User just clicked the MessageBack button",
   "value":{
      "property":"propertyValue"
   },
   "type":"message",
   "timestamp":"2017-06-22T22:38:47.407Z",
   "id":"f:5261769396935243054",
   "channelId":"msteams",
   "serviceUrl":"https://smba.trafficmanager.net/amer-client-ss.msg/",
   "from":{
      "id":"29:102jd210jd010icsoaeclaejcoa9ue09u",
      "name":"John Smith"
   },
   "conversation":{
      "id":"19:malejcou081i20ojmlcau0@thread.skype;messageid=1498171086622"
   },
   "recipient":{
      "id":"28:76096e45-119f-4736-859c-6dfff54395f7",
      "name":"MyBot"
   },
   "entities":[
      {
        "locale": "en-US",
        "country": "US",
        "platform": "Windows",
        "timezone": "America/Los_Angeles",
        "type": "clientInfo" 
      }
   ],
   "channelData":{
      "channel":{
         "id":"19:malejcou081i20ojmlcau0@thread.skype"
      },
      "team":{
         "id":"19:12d021jdoijsaeoaue0u@thread.skype"
      },
      "tenant":{
         "id":"bec8e231-67ad-484e-87f4-3e5438390a77"
      }
   },
        "replyToId": "1575667808184",
}
```

## <a name="imback"></a>imBack

Diese Aktion löst eine Rückgabemeldung an Ihren Bot aus, als ob der Benutzer sie in einer normalen Chatnachricht eingegeben hätte. Ihr Benutzer und alle anderen Benutzer, wenn sie sich in einem Kanal aufhalten, sehen diese Schaltflächenantwort.

Das `value` Feld sollte die Textzeichenfolge enthalten, die im Chat widerhallt und daher an den Bot zurückgesendet wird. Dies ist der Nachrichtentext, den Sie in Ihrem Bot verarbeiten werden, um die gewünschte Logik auszuführen. Hinweis: Dieses Feld ist eine einfache Zeichenfolge - es gibt keine Unterstützung für Formatierung oder ausgeblendete Zeichen.

```json
{
    "type": "imBack",
    "title": "More",
    "value": "Show me more"
}
```

## <a name="invoke"></a>Aufrufen

Die `invoke` Aktion wird zum Aufrufen von [Aufgabenmodulen](~/task-modules-and-cards/task-modules/task-modules-bots.md)verwendet.

Die `invoke` Aktion enthält drei Eigenschaften: , und `type` `title` `value` . Die `value` Eigenschaft kann eine Zeichenfolge, ein zeichenfolgeifiziertes JSON-Objekt oder ein JSON-Objekt enthalten.

```json
{
    "type": "invoke",
    "title": "Option 1",
    "value": {
        "option": "opt1"
    }
}
```

Wenn ein Benutzer auf die Schaltfläche klickt, erhält Ihr Bot das `value` Objekt mit einigen zusätzlichen Informationen. Bitte beachten Sie, dass der Aktivitätstyp `invoke` anstelle von `message` ( `activity.Type == "invoke"` ) angezeigt wird.

### <a name="example-invoke-button-definition-net"></a>Beispiel: Schaltflächendefinition aufrufen (.NET)

```csharp
var button = new CardAction()
{
    Title = "Option 1",
    Type = "invoke",
    Value = "{\"option\": \"opt1\"}"
};
```

### <a name="example-incoming-invoke-message"></a>Beispiel: Eingehende Aufrufnachricht

Die Eigenschaft der obersten Ebene `replyToId` enthält die ID der Nachricht, aus der die Kartenaktion stammt. Verwenden Sie sie, wenn Sie die Nachricht aktualisieren möchten.

```json
{
    "type": "invoke",
    "value": {
        "option": "opt1"
    },
    "timestamp": "2017-02-10T04:11:19.614Z",
    "localTimestamp": "2017-02-09T21:11:19.614-07:00",
    "id": "f:6894910862892785420",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
    "from": {
        "id": "29:1Eniglq0-uVL83xNB9GU6w_G5a4SZF0gcJLprZzhtEbel21G_5h-
    NgoprRw45mP0AXUIZVeqrsIHSYV4ntgfVJQ",
        "name": "John Doe"
    },
    "conversation": {
        "id": "19:97b1ec61-45bf-453c-9059-6e8984e0cef4_8d88f59b-ae61-4300-bec0-caace7d28446@unq.gbl.spaces"
    },
    "recipient": {
        "id": "28:8d88f59b-ae61-4300-bec0-caace7d28446",
        "name": "MyBot"
    },
    "entities": [
        {
            "locale": "en-US",
            "country": "US",
            "platform": "Web",
            "type": "clientInfo"
        }
    ],
    "channelData": {
        "channel": {
            "id": "19:dc5ba12695be4eb7bf457cad6b4709eb@thread.skype"
        },
        "team": {
            "id": "19:712c61d0ef384e5fa681ba90ca943398@thread.skype"
        },
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    },
    "replyToId": "1575667808184"
}
```

## <a name="signin"></a>Signin

Initiiert einen OAuth-Fluss, der es Bots ermöglicht, sich mit sicheren Diensten zu verbinden, wie hier ausführlicher beschrieben: [Authentifizierungsfluss in Bots](~/bots/how-to/authentication/auth-flow-bot.md).

## <a name="adaptive-cards-actions"></a>Adaptive Kartenaktionen

Adaptive Karten unterstützen vier Aktionstypen:

* [Action.OpenUrl](http://adaptivecards.io/explorer/Action.OpenUrl.html)
* [Action.Submit](http://adaptivecards.io/explorer/Action.Submit.html)
* [Action.ShowCard](http://adaptivecards.io/explorer/Action.ShowCard.html)
* [Action.Exeniedlich](/adaptive-cards/authoring-cards/universal-action-model#actionexecute)

Zusätzlich zu den oben genannten Aktionen können Sie die `Action.Submit` Adaptive Card-Nutzlast ändern, um vorhandene Bot Framework-Aktionen mithilfe einer Eigenschaft im Objekt von zu `msteams` `data` `Action.Submit` unterstützen. In den folgenden Abschnitten wird erläutert, wie vorhandene Bot Framework-Aktionen mit Adaptive Cards verwendet werden.

> [!NOTE]
> Das Hinzufügen `msteams` zu Daten mit einer Bot Framework-Aktion funktioniert nicht mit einem Taskmodul für adaptive Karten.

### <a name="adaptive-cards-with-messageback-action"></a>Adaptive Karten mit messageBack-Aktion

Um eine Aktion mit einer adaptiven Karte einzuschließen, `messageBack` schließen Sie die folgenden Details in das Objekt `msteams` ein. Beachten Sie, dass Sie bei Bedarf zusätzliche ausgeblendete Eigenschaften in das Objekt einschließen `data` können.

| Eigenschaft | Beschreibung |
| --- | --- |
| `type` | Eingestellt auf `messageBack` |
| `displayText` | Optional. Wird vom Benutzer in den Chat-Stream eingefügt, wenn die Aktion ausgeführt wird. Dieser Text wird *nicht* an Ihren Bot gesendet. |
| `value` | Wird an Ihren Bot gesendet, wenn die Aktion ausgeführt wird. Sie können den Kontext für die Aktion kodieren, z. B. eindeutige Bezeichner oder ein JSON-Objekt. |
| `text` | Wird an Ihren Bot gesendet, wenn die Aktion ausgeführt wird. Verwenden Sie diese Eigenschaft, um die Bot-Entwicklung zu vereinfachen: Ihr Code kann eine einzelne Eigenschaft der obersten Ebene überprüfen, um Botlogik zu versenden. |

#### <a name="example"></a>Beispiel

```json
{
  "type": "Action.Submit",
  "title": "Click me for messageBack",
  "data": {
    "msteams": {
        "type": "messageBack",
        "displayText": "I clicked this button",
        "text": "text to bots",
        "value": "{\"bfKey\": \"bfVal\", \"conflictKey\": \"from value\"}"
    }
  }
}
```

### <a name="adaptive-cards-with-imback-action"></a>Adaptive Karten mit imBack-Aktion

Um eine Aktion mit einer adaptiven Karte einzuschließen, `imBack` schließen Sie die folgenden Details in das Objekt `msteams` ein. Beachten Sie, dass Sie bei Bedarf zusätzliche ausgeblendete Eigenschaften in das Objekt einschließen `data` können.

| Eigenschaft | Beschreibung |
| --- | --- |
| `type` | Eingestellt auf `imBack` |
| `value` | String, der im Chat wieder wiederholt werden muss |

#### <a name="example"></a>Beispiel

```json
{
  "type": "Action.Submit",
  "title": "Click me for imBack",
  "data": {
    "msteams": {
        "type": "imBack",
        "value": "Text to reply in chat"
    }
  }
}
```

### <a name="adaptive-cards-with-signin-action"></a>Adaptive Karten mit Signin-Aktion

Um eine Aktion mit einer adaptiven Karte einzuschließen, `signin` schließen Sie die folgenden Details in das Objekt `msteams` ein. Beachten Sie, dass Sie bei Bedarf zusätzliche ausgeblendete Eigenschaften in das Objekt einschließen `data` können.

| Eigenschaft | Beschreibung |
| --- | --- |
| `type` | Auf `signin` . |
| `value` | Wird auf die URL festgelegt, zu der Sie umleiten möchten.  |

#### <a name="example"></a>Beispiel

```json
{
  "type": "Action.Submit",
  "title": "Click me for signin",
  "data": {
    "msteams": {
        "type": "signin",
        "value": "https://signin.com"
    }
  }
}
```

### <a name="adaptive-cards-with-invoke-action"></a>Adaptive Karten mit Aufrufaktion
 
Um eine Aktion mit einer adaptiven Karte einzuschließen, `invoke` schließen Sie die folgenden Details in das Objekt `msteams` ein. Beachten Sie, dass Sie bei Bedarf zusätzliche ausgeblendete Eigenschaften in das Objekt einschließen `data` können.

| Eigenschaft | Beschreibung |
| --- | --- |
| `type` | Eingestellt auf `task/fetch` |
| `data` | Legen Sie den Wert fest  |

#### <a name="example"></a>Beispiel

```json
{
  "type": "Action.Submit",
  "title": "submit"
  "data": {
    "msteams": {
        "type": "task/fetch"
    }
  }
}
```

#### <a name="example-2-with-additional-payload-data"></a>Beispiel 2 (mit zusätzlichen Nutzlastdaten)

```json
{
  "type": "Action.Submit",
  "title": "submit"
  "data": {
    "msteams": {
        "type": "task/fetch"
    },
    "Value1": "some value"
  }
}
```
