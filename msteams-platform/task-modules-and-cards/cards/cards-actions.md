---
title: Hinzufügen von Kartenaktionen in einem Bot
description: Beschreibt Kartenaktionen in Microsoft Teams und deren Verwendung in Ihren Bots
localization_priority: Normal
ms.topic: conceptual
keywords: Aktionen für Teams-Bots-Karten
ms.openlocfilehash: 75dcd6e1de1968f021a1ebe66c6770c4f641c94d
ms.sourcegitcommit: 1256639fa424e3833b44207ce847a245824d48e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2021
ms.locfileid: "52088794"
---
# <a name="card-actions"></a>Kartenaktionen

Karten, die von Bots und Messagingerweiterungen in Teams verwendet werden, unterstützen die folgenden Aktivitätstypen ( [`CardAction`](/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments#process-events-within-rich-cards) ). Beachten Sie, dass sich diese Aktionen von Office 365 Connectorkarten unterscheiden, wenn `potentialActions` sie von Connectors verwendet werden.

| Typ | Aktion |
| --- | --- |
| `openUrl` | Öffnet eine URL im Standardbrowser. |
| `messageBack` | Sendet eine Nachricht und Nutzlast an den Bot (vom Benutzer, der auf die Schaltfläche geklickt oder auf die Karte getippt hat) und sendet eine separate Nachricht an den Chatstream. |
| `imBack`| Sendet eine Nachricht an den Bot (vom Benutzer, der auf die Schaltfläche geklickt oder auf die Karte getippt hat). Diese Nachricht (von Benutzer zu Bot) ist für alle Unterhaltungsteilnehmer sichtbar. |
| `invoke` | Sendet eine Nachricht und Nutzlast an den Bot (vom Benutzer, der auf die Schaltfläche geklickt oder auf die Karte getippt hat). Diese Meldung ist nicht sichtbar. |
| `signin` | Initiiert den OAuth-Fluss, sodass Bots eine Verbindung mit sicheren Diensten herstellen können. |

> [!NOTE]
>* Teams unterstützt keine `CardAction` Typen, die in der vorherigen Tabelle nicht aufgeführt sind.
>* Teams unterstützt die Eigenschaft `potentialActions` nicht.
>* Kartenaktionen unterscheiden sich von den [vorgeschlagenen Aktionen](/azure/bot-service/bot-builder-howto-add-suggested-actions?view=azure-bot-service-4.0&tabs=javascript#suggest-action-using-button&preserve-view=true) in Bot Framework/Azure Bot Service. Vorgeschlagene Aktionen werden in Microsoft Teams nicht unterstützt: Wenn Schaltflächen in einer Teams angezeigt werden sollen, verwenden Sie eine Karte.
>* Wenn Sie eine Kartenaktion als Teil einer Messagingerweiterung verwenden, funktionieren die Aktionen erst, wenn die Karte an den Kanal übermittelt wird (sie funktionieren nicht, während sich die Karte im Meldungsfeld Verfassen befindet).

Teams unterstützt auch [adaptive Kartenaktionen,](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)die nur von adaptiven Karten verwendet werden. Diese Aktionen werden in ihrem eigenen Abschnitt am Ende dieses Verweises aufgeführt.

## <a name="openurl"></a>OpenURL

Dieser Aktionstyp gibt eine URL an, die im Standardbrowser gestartet werden soll. Beachten Sie, dass Ihr Bot keine Benachrichtigung erhält, auf welche Schaltfläche geklickt wurde.

Das `value` Feld muss eine vollständige und ordnungsgemäß gebildete URL enthalten.

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
| `displayText` | Optional. Echoed by the user into the chat stream when the action is performed. Dieser Text wird *nicht an* Ihren Bot gesendet. |
| `value` | Wird an Ihren Bot gesendet, wenn die Aktion ausgeführt wird. Sie können den Kontext für die Aktion codieren, z. B. eindeutige Bezeichner oder ein JSON-Objekt. |
| `text` | Wird an Ihren Bot gesendet, wenn die Aktion ausgeführt wird. Verwenden Sie diese Eigenschaft, um die Botentwicklung zu vereinfachen: Ihr Code kann eine einzelne Eigenschaft auf oberster Ebene überprüfen, um Botlogik zu versenden. |

Die Flexibilität von bedeutet, dass Ihr Code auswählen kann, keine sichtbare Benutzernachricht im Verlauf zu hinterlassen, indem `messageBack` einfach nicht verwendet `displayText` wird.

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

Diese Aktion löst eine Rückgabenachricht an Ihren Bot aus, als würde der Benutzer sie in eine normale Chatnachricht eingeben. Ihr Benutzer und alle anderen Benutzer in einem Kanal sehen diese Schaltflächenantwort.

Das `value` Feld sollte die Textzeichenfolge enthalten, die im Chat widerhallt und daher an den Bot gesendet wird. Dies ist der Nachrichtentext, den Sie in Ihrem Bot verarbeiten, um die gewünschte Logik durchzuführen. Hinweis: Dieses Feld ist eine einfache Zeichenfolge – es gibt keine Unterstützung für Formatierungen oder ausgeblendete Zeichen.

```json
{
    "type": "imBack",
    "title": "More",
    "value": "Show me more"
}
```

## <a name="invoke"></a>invoke

Die `invoke` Aktion wird zum Aufrufen von [Aufgabenmodulen verwendet.](~/task-modules-and-cards/task-modules/task-modules-bots.md)

Die `invoke` Aktion enthält drei Eigenschaften: , und `type` `title` `value` . Die `value` Eigenschaft kann eine Zeichenfolge, ein zeichenfolgenbesetztes JSON-Objekt oder ein JSON-Objekt enthalten.

```json
{
    "type": "invoke",
    "title": "Option 1",
    "value": {
        "option": "opt1"
    }
}
```

Wenn ein Benutzer auf die Schaltfläche klickt, erhält ihr Bot das `value` Objekt mit einigen zusätzlichen Informationen. Beachten Sie, dass der Aktivitätstyp anstelle `invoke` von `message` ( `activity.Type == "invoke"` ist).

### <a name="example-invoke-button-definition-net"></a>Beispiel: Aufrufen der Schaltflächendefinition (.NET)

```csharp
var button = new CardAction()
{
    Title = "Option 1",
    Type = "invoke",
    Value = "{\"option\": \"opt1\"}"
};
```

### <a name="example-incoming-invoke-message"></a>Beispiel: Eingehende Aufrufnachricht

Die Eigenschaft auf `replyToId` oberster Ebene enthält die ID der Nachricht, aus der die Kartenaktion stammt. Verwenden Sie sie, wenn Sie die Nachricht aktualisieren möchten.

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

## <a name="signin"></a>signin

Initiiert einen OAuth-Fluss, sodass Bots eine Verbindung mit sicheren Diensten herstellen können, wie hier ausführlicher beschrieben: [Authentifizierungsfluss in Bots](~/bots/how-to/authentication/auth-flow-bot.md).

## <a name="adaptive-cards-actions"></a>Aktionen mit adaptiven Karten

Adaptive Karten unterstützen vier Aktionstypen:

* [Action.OpenUrl](http://adaptivecards.io/explorer/Action.OpenUrl.html)
* [Action.Submit](http://adaptivecards.io/explorer/Action.Submit.html)
* [Action.ShowCard](http://adaptivecards.io/explorer/Action.ShowCard.html)
* [Action.Execute](https://docs.microsoft.com/adaptive-cards/authoring-cards/universal-action-model#actionexecute)

Zusätzlich zu den oben genannten Aktionen können Sie die Nutzlast der adaptiven Karte so ändern, dass vorhandene Bot Framework-Aktionen mithilfe einer Eigenschaft `Action.Submit` im Objekt von unterstützt `msteams` `data` `Action.Submit` werden. In den folgenden Abschnitten erfahren Sie, wie Sie vorhandene Bot Framework-Aktionen mit adaptiven Karten verwenden.

> [!NOTE]
> Das Hinzufügen zu Daten mit einer Bot Framework-Aktion funktioniert `msteams` nicht mit einem Aufgabenmodul für adaptive Karten.

### <a name="adaptive-cards-with-messageback-action"></a>Adaptive Karten mit messageBack-Aktion

Um eine `messageBack` Aktion mit einer adaptiven Karte zu verwenden, fügen Sie die folgenden Details in das Objekt `msteams` ein. Beachten Sie, dass Sie bei Bedarf zusätzliche ausgeblendete Eigenschaften in das `data` Objekt verwenden können.

| Eigenschaft | Beschreibung |
| --- | --- |
| `type` | Set to `messageBack` |
| `displayText` | Optional. Echoed by the user into the chat stream when the action is performed. Dieser Text wird *nicht an* Ihren Bot gesendet. |
| `value` | Wird an Ihren Bot gesendet, wenn die Aktion ausgeführt wird. Sie können den Kontext für die Aktion codieren, z. B. eindeutige Bezeichner oder ein JSON-Objekt. |
| `text` | Wird an Ihren Bot gesendet, wenn die Aktion ausgeführt wird. Verwenden Sie diese Eigenschaft, um die Botentwicklung zu vereinfachen: Ihr Code kann eine einzelne Eigenschaft auf oberster Ebene überprüfen, um Botlogik zu versenden. |

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

Um eine `imBack` Aktion mit einer adaptiven Karte zu verwenden, fügen Sie die folgenden Details in das Objekt `msteams` ein. Beachten Sie, dass Sie bei Bedarf zusätzliche ausgeblendete Eigenschaften in das `data` Objekt verwenden können.

| Eigenschaft | Beschreibung |
| --- | --- |
| `type` | Set to `imBack` |
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

### <a name="adaptive-cards-with-signin-action"></a>Adaptive Karten mit Anmeldeaktion

Um eine `signin` Aktion mit einer adaptiven Karte zu verwenden, fügen Sie die folgenden Details in das Objekt `msteams` ein. Beachten Sie, dass Sie bei Bedarf zusätzliche ausgeblendete Eigenschaften in das `data` Objekt verwenden können.

| Eigenschaft | Beschreibung |
| --- | --- |
| `type` | Set to `signin` |
| `value` | Festlegen auf die URL, an die Sie umleiten möchten  |

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
 
Um eine `invoke` Aktion mit einer adaptiven Karte zu verwenden, fügen Sie die folgenden Details in das Objekt `msteams` ein. Beachten Sie, dass Sie bei Bedarf zusätzliche ausgeblendete Eigenschaften in das `data` Objekt verwenden können.

| Eigenschaft | Beschreibung |
| --- | --- |
| `type` | Set to `task/fetch` |
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
