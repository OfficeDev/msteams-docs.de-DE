---
title: Hinzufügen von Karten Aktionen in einem bot
description: Beschreibt Karten Aktionen in Microsoft Teams und deren Verwendung in ihren Bots
keywords: Teams Bots Cards Aktionen
ms.openlocfilehash: 2bee1072405d91cd29d1aa227884516a87d10bde
ms.sourcegitcommit: b9771f8f4be9ac1ff8c85c2d7bd8d5c5408bc653
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/06/2021
ms.locfileid: "49768074"
---
# <a name="card-actions"></a>Karten Aktionen

Von Bots und Messaging Erweiterungen in Microsoft Teams verwendete Karten unterstützen die folgenden Aktivitäts [`CardAction`](/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments#process-events-within-rich-cards) Typen. Beachten Sie, dass sich diese Aktionen von `potentialActions` für Office 365-connectorkarten unterscheiden, wenn Sie von Connectors verwendet werden.

| Typ | Aktion |
| --- | --- |
| `openUrl` | Öffnet eine URL im Standardbrowser. |
| `messageBack` | Sendet eine Nachricht und eine Nutzlast an den bot (von dem Benutzer, der auf die Schaltfläche geklickt oder die Karte angetippt hat) und sendet eine separate Nachricht an den Chat Datenstrom. |
| `imBack`| Sendet eine Nachricht an den bot (von dem Benutzer, der auf die Schaltfläche geklickt oder die Karte angetippt hat). Diese Nachricht (von Benutzer zu bot) ist für alle Gesprächsteilnehmer sichtbar. |
| `invoke` | Sendet eine Nachricht und eine Nutzlast an den bot (von dem Benutzer, der auf die Schaltfläche geklickt oder die Karte angetippt hat). Diese Nachricht ist nicht sichtbar. |
| `signin` | Initiiert den OAuth-Fluss, sodass Bots eine Verbindung mit sicheren Diensten herstellen können. |

> [!NOTE]
>* In Microsoft Teams werden keine Typen unterstützt `CardAction` , die nicht in der obigen Tabelle aufgeführt sind.
>* Die-Eigenschaft wird von Microsoft Teams nicht unterstützt `potentialActions` .
>* Karten Aktionen unterscheiden sich von [vorgeschlagenen Aktionen](/azure/bot-service/bot-builder-howto-add-suggested-actions?view=azure-bot-service-4.0&tabs=javascript#suggest-action-using-button&preserve-view=true) im bot-Framework/Azure-bot-Dienst. Vorgeschlagene Aktionen werden in Microsoft Teams nicht unterstützt: Wenn Sie möchten, dass Schaltflächen in einer Team-bot-Nachricht angezeigt werden, verwenden Sie eine Karte.
>* Wenn Sie eine Karten Aktion als Teil einer Messaging Erweiterung verwenden, werden die Aktionen erst ausgeführt, wenn die Karte an den Kanal gesendet wird (Sie funktionieren nicht, wenn sich die Karte im Meldungsfeld verfassen befindet).

Teams unterstützen auch [Aktionen für Adaptive Karten](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions), die nur von adaptiven Karten verwendet werden. Diese Aktionen werden am Ende dieser Referenz in einem eigenen Abschnitt aufgeführt.

## <a name="openurl"></a>OpenURL

Dieser Aktionstyp gibt eine URL an, die im Standardbrowser gestartet werden soll. Beachten Sie, dass Ihr bot keinen Hinweis auf die Schaltfläche erhält, auf die geklickt wurde.

Das `value` Feld muss eine vollständige und ordnungsgemäß formatierte URL enthalten.

```json
{
    "type": "openUrl",
    "title": "Tabs in Teams",
    "value": "https://msdn.microsoft.com/microsoft-teams/tabs"
}
```

## <a name="messageback"></a>messageBack

Mit `messageBack` können Sie eine vollständig angepasste Aktion mit den folgenden Eigenschaften erstellen:

| Eigenschaft | Beschreibung |
| --- | --- |
| `title` | Wird als Schaltflächenbeschriftung angezeigt. |
| `displayText` | Optional. Wird vom Benutzer im Chat-Stream wiedergegeben, wenn die Aktion ausgeführt wird. Dieser Text wird *nicht* an Ihren bot gesendet. |
| `value` | An Ihren bot gesendet, wenn die Aktion ausgeführt wird. Sie können den Kontext für die Aktion codieren, beispielsweise eindeutige Bezeichner oder ein JSON-Objekt. |
| `text` | An Ihren bot gesendet, wenn die Aktion ausgeführt wird. Verwenden Sie diese Eigenschaft, um die bot-Entwicklung zu vereinfachen: Ihr Code kann eine einzelne Eigenschaft auf oberster Ebene zum Senden der bot-Logik überprüfen. |

Die Flexibilität von `messageBack` bedeutet, dass Ihr Code wählen kann, keine sichtbare Benutzernachricht im Verlauf einfach zu hinterlassen, indem er nicht verwendet wird `displayText` .

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

Die `value` -Eigenschaft kann entweder eine serialisierte JSON-Zeichenfolge oder ein JSON-Objekt sein.

### <a name="inbound-message-example"></a>Beispiel für eingehende Nachrichten

`replyToId` enthält die ID der Nachricht, aus der die Karten Aktion stammt. Verwenden Sie es, wenn Sie die Nachricht aktualisieren möchten.

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

## <a name="imback"></a>zurück

Durch diese Aktion wird eine Rückgabemeldung an Ihren bot ausgelöst, als ob der Benutzer Sie in einer normalen Chatnachricht eingegeben hat. Der Benutzer und alle anderen Benutzer, die sich in einem Kanal befinden, sehen diese Schaltflächen Antwort.

Das `value` Feld sollte die Textzeichenfolge enthalten, die im Chat wiedergegeben wird und daher an den bot zurückgesendet wird. Dies ist der Nachrichtentext, den Sie in Ihrem bot verarbeiten werden, um die gewünschte Logik auszuführen. Hinweis: Dieses Feld ist eine einfache Zeichenfolge-es gibt keine Unterstützung für die Formatierung oder versteckte Zeichen.

```json
{
    "type": "imBack",
    "title": "More",
    "value": "Show me more"
}
```

## <a name="invoke"></a>Invoke

Die `invoke` Aktion wird zum Aufrufen von [Aufgaben Modulen](~/task-modules-and-cards/task-modules/task-modules-bots.md)verwendet.

Die `invoke` Aktion enthält drei Eigenschaften: `type` , `title` und `value` . Die `value` -Eigenschaft kann eine Zeichenfolge, ein stringified JSON-Objekt oder ein JSON-Objekt enthalten.

```json
{
    "type": "invoke",
    "title": "Option 1",
    "value": {
        "option": "opt1"
    }
}
```

Wenn ein Benutzer auf die Schaltfläche klickt, erhält der bot das `value` Objekt mit zusätzlichen Informationen. Beachten Sie, dass der Aktivitätstyp `invoke` statt `message` () ist `activity.Type == "invoke"` .

### <a name="example-invoke-button-definition-net"></a>Beispiel: Invoke-Schaltflächen Definition (.net)

```csharp
var button = new CardAction()
{
    Title = "Option 1",
    Type = "invoke",
    Value = "{\"option\": \"opt1\"}"
};
```

### <a name="example-incoming-invoke-message"></a>Beispiel: eingehende Invoke-Nachricht

Die Eigenschaft der obersten Ebene `replyToId` enthält die ID der Nachricht, von der die Karten Aktion stammt. Verwenden Sie es, wenn Sie die Nachricht aktualisieren möchten.

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

## <a name="signin"></a>SignIn

Initiiert einen OAuth-Fluss, wodurch Bots eine Verbindung mit sicheren Diensten herstellen können, wie hier ausführlicher beschrieben: [Authentifizierungs Fluss in Bots](~/bots/how-to/authentication/auth-flow-bot.md).

## <a name="adaptive-cards-actions"></a>Aktionen für Adaptive Karten

Adaptive Karten unterstützen drei Aktionstypen:

* [Action.OpenUrl](http://adaptivecards.io/explorer/Action.OpenUrl.html)
* [Action.Submit](http://adaptivecards.io/explorer/Action.Submit.html)
* [Action. ShowCard](http://adaptivecards.io/explorer/Action.ShowCard.html)

Zusätzlich zu den oben genannten Aktionen können Sie die Nutzlast der adaptiven Karte ändern, `Action.Submit` um vorhandene bot-Framework-Aktionen mithilfe einer `msteams` Eigenschaft im `data` Objekt von zu unterstützen `Action.Submit` . In den folgenden Abschnitten wird erläutert, wie vorhandene bot-Framework-Aktionen mit adaptiven Karten verwendet werden.

> [!NOTE]
> Das Hinzufügen `msteams` zu Daten mit einer bot-Framework-Aktion funktioniert nicht mit einem adaptiven Karten Aufgabenmodul.

### <a name="adaptive-cards-with-messageback-action"></a>Adaptive Karten mit messageBack-Aktion

Um eine `messageBack` Aktion mit einer adaptiven Karte einzubeziehen, schließen Sie die folgenden Details in das `msteams` Objekt ein. Beachten Sie, dass Sie bei Bedarf zusätzliche verborgene Eigenschaften in das Objekt einschließen können `data` .

| Eigenschaft | Beschreibung |
| --- | --- |
| `type` | Auf festlegen `messageBack` |
| `displayText` | Optional. Wird vom Benutzer im Chat-Stream wiedergegeben, wenn die Aktion ausgeführt wird. Dieser Text wird *nicht* an Ihren bot gesendet. |
| `value` | An Ihren bot gesendet, wenn die Aktion ausgeführt wird. Sie können den Kontext für die Aktion codieren, beispielsweise eindeutige Bezeichner oder ein JSON-Objekt. |
| `text` | An Ihren bot gesendet, wenn die Aktion ausgeführt wird. Verwenden Sie diese Eigenschaft, um die bot-Entwicklung zu vereinfachen: Ihr Code kann eine einzelne Eigenschaft auf oberster Ebene zum Senden der bot-Logik überprüfen. |

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

### <a name="adaptive-cards-with-imback-action"></a>Adaptive Karten mit Rück kehr Aktion

Um eine `imBack` Aktion mit einer adaptiven Karte einzubeziehen, schließen Sie die folgenden Details in das `msteams` Objekt ein. Beachten Sie, dass Sie bei Bedarf zusätzliche verborgene Eigenschaften in das Objekt einschließen können `data` .

| Eigenschaft | Beschreibung |
| --- | --- |
| `type` | Auf festlegen `imBack` |
| `value` | Zeichenfolge, die im Chat wiederholt werden muss |

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

### <a name="adaptive-cards-with-signin-action"></a>Adaptive Karten mit SignIn-Aktion

Um eine `signin` Aktion mit einer adaptiven Karte einzubeziehen, schließen Sie die folgenden Details in das `msteams` Objekt ein. Beachten Sie, dass Sie bei Bedarf zusätzliche verborgene Eigenschaften in das Objekt einschließen können `data` .

| Eigenschaft | Beschreibung |
| --- | --- |
| `type` | Auf festlegen `signin` |
| `value` | Legen Sie die URL fest, auf die umgeleitet werden soll.  |

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

### <a name="adaptive-cards-with-invoke-action"></a>Adaptive Karten mit Invoke-Aktion
 
Um eine `invoke` Aktion mit einer adaptiven Karte einzubeziehen, schließen Sie die folgenden Details in das `msteams` Objekt ein. Beachten Sie, dass Sie bei Bedarf zusätzliche verborgene Eigenschaften in das Objekt einschließen können `data` .

| Eigenschaft | Beschreibung |
| --- | --- |
| `type` | Auf festlegen `task/fetch` |
| `data` | Festlegen des Werts  |

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

#### <a name="example-2-with-additional-payload-data"></a>Beispiel 2 (mit zusätzlichen Nutzlast-Daten)

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
