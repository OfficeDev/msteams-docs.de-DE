---
title: Hinzufügen von Kartenaktionen in einem Bot
description: Beschreibt Kartenaktionen in Microsoft Teams und deren Verwendung in Ihren Bots
localization_priority: Normal
ms.topic: conceptual
keywords: Aktionen für Teams-Bots-Karten
ms.openlocfilehash: 1b20ca8003ab74c5dd2860e754024ae64ff94527
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140089"
---
# <a name="card-actions"></a>Kartenaktionen

Karten, die von Bots und Messaging-Erweiterungen in Teams verwendet werden, unterstützen die folgenden [`CardAction`](/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments#process-events-within-rich-cards) Aktivitätstypen:

> [!NOTE]
> Die `CardAction` Aktionen unterscheiden sich von Office 365 `potentialActions` Konnektorkarten, wenn sie von Connectors verwendet werden.

| Typ | Aktion |
| --- | --- |
| `openUrl` | Öffnet eine URL im Standardbrowser. |
| `messageBack` | Sendet eine Nachricht und Nutzlast vom Benutzer, der die Schaltfläche ausgewählt oder auf die Karte getippt hat, an den Bot. Sendet eine separate Nachricht an den Chatstream. |
| `imBack`| Sendet eine Nachricht vom Benutzer, der die Schaltfläche ausgewählt oder auf die Karte getippt hat, an den Bot. Diese Nachricht von Benutzer zu Bot ist für alle Unterhaltungsteilnehmer sichtbar. |
| `invoke` | Sendet eine Nachricht und Nutzlast vom Benutzer, der die Schaltfläche ausgewählt oder auf die Karte getippt hat, an den Bot. Diese Meldung ist nicht sichtbar. |
| `signin` | Initiiert den OAuth-Fluss, sodass Bots eine Verbindung mit sicheren Diensten herstellen können. |

> [!NOTE]
>* Teams unterstützt keine `CardAction` Typen, die in der vorherigen Tabelle nicht aufgeführt sind.
>* Teams unterstützt die Eigenschaft `potentialActions` nicht.
>* Kartenaktionen unterscheiden sich von [den vorgeschlagenen Aktionen](/azure/bot-service/bot-builder-howto-add-suggested-actions?view=azure-bot-service-4.0&tabs=javascript#suggest-action-using-button&preserve-view=true) in Bot Framework oder Azure Bot Service. Vorgeschlagene Aktionen werden in Microsoft Teams nicht unterstützt. Wenn Schaltflächen in einer Teams Bot-Nachricht angezeigt werden sollen, verwenden Sie eine Karte.
>* Wenn Sie eine Kartenaktion als Teil einer Messaging-Erweiterung verwenden, funktionieren die Aktionen erst, wenn die Karte an den Kanal übermittelt wird. Die Aktionen funktionieren nicht, während sich die Karte im Feld zum Verfassen von Nachrichten befindet.

## <a name="action-type-openurl"></a>Aktionstyp "openUrl"

`openUrl` der Aktionstyp gibt eine URL an, die im Standardbrowser gestartet werden soll.

> [!NOTE]
> Ihr Bot erhält keine Benachrichtigung darüber, welche Schaltfläche ausgewählt wurde.

Mit `openUrl` können Sie eine Aktion mit den folgenden Eigenschaften erstellen:

| Eigenschaft | Beschreibung |
| --- | --- |
| `title` | Wird als Schaltflächenbeschriftung angezeigt. |
| `value` | Dieses Feld muss eine vollständige und ordnungsgemäß gebildete URL enthalten. |

# <a name="json"></a>[Json](#tab/json)

Der folgende Code zeigt ein Beispiel für den `openUrl` Aktionstyp in JSON:

```json
{
    "type": "openUrl",
    "title": "Tabs in Teams",
    "value": "https://msdn.microsoft.com/microsoft-teams/tabs"
}
```

# <a name="c"></a>[C#](#tab/csharp)

Der folgende Code zeigt ein Beispiel für den `openUrl` Aktionstyp in C#:

```csharp
var button = new CardAction()
{
    Type = ActionTypes.OpenUrl,
    Title = "Tabs in Teams",
    Value = "https://docs.microsoft.com/en-us/microsoftteams/platform/"
};
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

Der folgende Code zeigt ein Beispiel für den `openUrl` Aktionstyp in JavaScript:

```javascript
CardFactory.actions([
{
    type: 'openUrl',
    title: 'Tabs in Teams',
    value: 'https://docs.microsoft.com/en-us/microsoftteams/platform/'
}])
```

---

## <a name="action-type-messageback"></a>MessageBack des Aktionstyps

Mit `messageBack` können Sie eine vollständig angepasste Aktion mit den folgenden Eigenschaften erstellen:

| Eigenschaft | Beschreibung |
| --- | --- |
| `title` | Wird als Schaltflächenbeschriftung angezeigt. |
| `displayText` | Optional. Wird vom Benutzer im Chatdatenstrom verwendet, wenn die Aktion ausgeführt wird. Dieser Text wird nicht an Ihren Bot gesendet. |
| `value` | Wird an Ihren Bot gesendet, wenn die Aktion ausgeführt wird. Sie können den Kontext für die Aktion codieren, z. B. eindeutige Bezeichner oder ein JSON-Objekt. |
| `text` | Wird an Ihren Bot gesendet, wenn die Aktion ausgeführt wird. Verwenden Sie diese Eigenschaft, um die Bot-Entwicklung zu vereinfachen. Ihr Code kann eine einzelne Eigenschaft der obersten Ebene überprüfen, um Botlogik zu verteilen. |

Die Flexibilität `messageBack` bedeutet, dass Ihr Code keine sichtbare Benutzernachricht im Verlauf belassen kann, indem er einfach nicht verwendet `displayText` wird.

# <a name="json"></a>[Json](#tab/json)

Der folgende Code zeigt ein Beispiel für den `messageBack` Aktionstyp in JSON:

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

Die `value` Eigenschaft kann eine serialisierte JSON-Zeichenfolge oder ein JSON-Objekt sein.

# <a name="c"></a>[C#](#tab/csharp)

Der folgende Code zeigt ein Beispiel für den `messageBack` Aktionstyp in C#:

```csharp
var button = new CardAction()
{
    Type = ActionTypes.MessageBack,
    Title = "My MessageBack button",
    DisplayText = "I clicked this button",
    Text = "User just clicked the MessageBack button",
    Value = "{\"property\": \"propertyValue\" }"
};
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

Der folgende Code zeigt ein Beispiel für den `messageBack` Aktionstyp in JavaScript:

```javascript
CardFactory.actions([
{
    type: 'messageBack',
    title: "My MessageBack button",
    displayText: "I clicked this button",
    text: "User just clicked the MessageBack button",
    value: {property: "propertyValue" }
}])
```

---

### <a name="inbound-message-example"></a>Beispiel für eingehende Nachrichten

`replyToId` enthält die ID der Nachricht, aus der die Kartenaktion stammt. Verwenden Sie sie, wenn Sie die Nachricht aktualisieren möchten.

Der folgende Code zeigt ein Beispiel für eingehende Nachrichten:

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

## <a name="action-type-imback"></a>Aktionstyp imBack

Die `imBack` Aktion löst eine Rückgabenachricht an Ihren Bot aus, als ob der Benutzer sie in eine normale Chatnachricht eingegeben hätte. Der Benutzer und alle anderen Benutzer in einem Kanal können die Schaltflächenantwort sehen.

Mit `imBack` können Sie eine Aktion mit den folgenden Eigenschaften erstellen:

| Eigenschaft | Beschreibung |
| --- | --- |
| `title` | Wird als Schaltflächenbeschriftung angezeigt. |
| `value` | Dieses Feld muss die im Chat verwendete Textzeichenfolge enthalten und daher an den Bot zurücksandt. Dies ist der Nachrichtentext, den Sie in Ihrem Bot verarbeiten, um die gewünschte Logik auszuführen. |

> [!NOTE]
> Das `value` Feld ist eine einfache Zeichenfolge. Formatierungen oder ausgeblendete Zeichen werden nicht unterstützt.

# <a name="json"></a>[Json](#tab/json)

Der folgende Code zeigt ein Beispiel für den `imBack` Aktionstyp in JSON:

```json
{
    "type": "imBack",
    "title": "More",
    "value": "Show me more"
}
```

# <a name="c"></a>[C#](#tab/csharp)

Der folgende Code zeigt ein Beispiel für den `imBack` Aktionstyp in C#:

```csharp
var button = new CardAction()
{
    Type = ActionTypes.ImBack,
    Title = "More",
    Value = "Show me more"
};
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

Der folgende Code zeigt ein Beispiel für den `imBack` Aktionstyp in JavaScript:

```javascript
CardFactory.actions([
{
    type: "imBack",
    title: "More",
    value: "Show me more"
}])
```

---

## <a name="action-type-invoke"></a>Aufrufen des Aktionstyps

Die `invoke` Aktion wird zum Aufrufen von [Aufgabenmodulen](~/task-modules-and-cards/task-modules/task-modules-bots.md)verwendet.

Die `invoke` Aktion enthält drei Eigenschaften, und `type` `title` `value` .

Mit `invoke` können Sie eine Aktion mit den folgenden Eigenschaften erstellen:

| Eigenschaft | Beschreibung |
| --- | --- |
| `title` | Wird als Schaltflächenbeschriftung angezeigt. |
| `value` | Diese Eigenschaft kann eine Zeichenfolge, ein JSON-Objekt mit Zeichenfolge oder ein JSON-Objekt enthalten. |

# <a name="json"></a>[Json](#tab/json)

Der folgende Code zeigt ein Beispiel für den `invoke` Aktionstyp in JSON:

```json
{
    "type": "invoke",
    "title": "Option 1",
    "value": {
        "option": "opt1"
    }
}
```

Wenn ein Benutzer die Schaltfläche auswählt, empfängt Ihr Bot das `value` Objekt mit einigen zusätzlichen Informationen.

> [!NOTE]
> Der `invoke` Aktivitätstyp ist `message` stattdessen `activity.Type == "invoke"` .

# <a name="c"></a>[C#](#tab/csharp)

Der folgende Code zeigt ein Beispiel für den `invoke` Aktionstyp in C#:

```csharp
var button = new CardAction()
{
    Title = "Option 1",
    Type = "invoke",
    Value = "{\"option\": \"opt1\"}"
};
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

Der folgende Code zeigt ein Beispiel für den `invoke` Aktionstyp in Node.js:

```javascript
CardFactory.actions([
{
    type: "invoke",
    title: "Option 1",
    value: {
        option: "opt1"
    }
}])
```

---

### <a name="example-of-incoming-invoke-message"></a>Beispiel für eingehende Aufrufnachricht

Die Eigenschaft der obersten Ebene `replyToId` enthält die ID der Nachricht, aus der die Kartenaktion stammt. Verwenden Sie sie, wenn Sie die Nachricht aktualisieren möchten.

Der folgende Code zeigt ein Beispiel für eine eingehende Aufrufnachricht:

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

## <a name="action-type-signin"></a>Signin des Aktionstyps

`signin` Der Aktionstyp initiiert einen OAuth-Fluss, der bots die Verbindung mit sicheren Diensten ermöglicht. Weitere Informationen finden Sie unter [Authentifizierungsfluss in Bots.](~/bots/how-to/authentication/auth-flow-bot.md)

Teams unterstützt auch [Adaptive Kartenaktionen,](#adaptive-cards-actions) die nur von adaptiven Karten verwendet werden.

# <a name="json"></a>[Json](#tab/json)

Der folgende Code zeigt ein Beispiel für den `signin` Aktionstyp in JSON:

```json
{
"type": "signin",
"title": "Click me for signin",
"value": "https://signin.com"
}
```

# <a name="c"></a>[C#](#tab/csharp)

Der folgende Code zeigt ein Beispiel für den `signin` Aktionstyp in C#:

```csharp
var button = new CardAction()
{
    Type = ActionTypes.Signin,
    Title = "Click me for signin",
    Value = "https://signin.com"
};
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

Der folgende Code zeigt ein Beispiel für den `signin` Aktionstyp in JavaScript:

```javascript
CardFactory.actions([
{
    type: "signin",
    title: "Click me for signin",
    value: "https://signin.com"
}])
```

---

## <a name="adaptive-cards-actions"></a>Aktionen für adaptive Karten

Adaptive Karten unterstützen vier Aktionstypen:

* [Action.OpenUrl](http://adaptivecards.io/explorer/Action.OpenUrl.html)
* [Action.Submit](http://adaptivecards.io/explorer/Action.Submit.html)
* [Action.ShowCard](http://adaptivecards.io/explorer/Action.ShowCard.html)
* [Action.Execute](/adaptive-cards/authoring-cards/universal-action-model#actionexecute)

Sie können auch die Nutzlast der adaptiven Karte `Action.Submit` ändern, um vorhandene Bot Framework-Aktionen mithilfe einer Eigenschaft im Objekt von zu `msteams` `data` `Action.Submit` unterstützen. Der nächste Abschnitt enthält Details zur Verwendung vorhandener Bot Framework-Aktionen mit adaptiven Karten.

> [!NOTE]
> Das Hinzufügen `msteams` zu Daten mit einer Bot Framework-Aktion funktioniert nicht mit einem Aufgabenmodul für adaptive Karten.

### <a name="adaptive-cards-with-messageback-action"></a>Adaptive Karten mit messageBack-Aktion

Um eine `messageBack` Aktion in eine adaptive Karte einzuschließen, fügen Sie die folgenden Details in das Objekt `msteams` ein:

> [!NOTE]
> Sie können zusätzliche ausgeblendete Eigenschaften in das `data` Objekt einschließen, falls erforderlich.

| Eigenschaft | Beschreibung |
| --- | --- |
| `type` | Festgelegt auf `messageBack` . |
| `displayText` | Optional. Wird vom Benutzer im Chatdatenstrom verwendet, wenn die Aktion ausgeführt wird. Dieser Text wird nicht an Ihren Bot gesendet. |
| `value` | Wird an Ihren Bot gesendet, wenn die Aktion ausgeführt wird. Sie können den Kontext für die Aktion codieren, z. B. eindeutige Bezeichner oder ein JSON-Objekt. |
| `text` | Wird an Ihren Bot gesendet, wenn die Aktion ausgeführt wird. Verwenden Sie diese Eigenschaft, um die Bot-Entwicklung zu vereinfachen. Ihr Code kann eine einzelne Eigenschaft der obersten Ebene überprüfen, um Botlogik zu verteilen. |

Der folgende Code zeigt ein Beispiel für adaptive Karten mit `messageBack` Aktion:

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

Um eine `imBack` Aktion in eine adaptive Karte einzuschließen, fügen Sie die folgenden Details in das Objekt `msteams` ein:

> [!NOTE]
> Sie können zusätzliche ausgeblendete Eigenschaften in das `data` Objekt einschließen, falls erforderlich.

| Eigenschaft | Beschreibung |
| --- | --- |
| `type` | Festgelegt auf `imBack` . |
| `value` | Zeichenfolge, die im Chat wiederholt werden muss. |

Der folgende Code zeigt ein Beispiel für adaptive Karten mit `imBack` Aktion:

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

Um eine `signin` Aktion in eine adaptive Karte einzuschließen, fügen Sie die folgenden Details in das Objekt `msteams` ein:

> [!NOTE]
> Sie können zusätzliche ausgeblendete Eigenschaften in das `data` Objekt einschließen, falls erforderlich.

| Eigenschaft | Beschreibung |
| --- | --- |
| `type` | Festgelegt auf `signin` . |
| `value` | Legen Sie die URL fest, an die Sie umleiten möchten.  |

Der folgende Code zeigt ein Beispiel für adaptive Karten mit `signin` Aktion:

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

Um eine `invoke` Aktion in eine adaptive Karte einzuschließen, fügen Sie die folgenden Details in das Objekt `msteams` ein:

> [!NOTE]
> Sie können zusätzliche ausgeblendete Eigenschaften in das `data` Objekt einschließen, falls erforderlich.

| Eigenschaft | Beschreibung |
| --- | --- |
| `type` | Festgelegt auf `task/fetch` . |
| `data` | Legen Sie den Wert fest.  |

Der folgende Code zeigt ein Beispiel für adaptive Karten mit `invoke` Aktion:

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

Der folgende Code zeigt ein Beispiel für adaptive Karten mit `invoke` Aktion mit zusätzlichen Nutzlastdaten:

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

## <a name="see-also"></a>Siehe auch

[Karten-Referenz](./cards-reference.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Universal-Aktionen für adaptive Karten](../cards/Universal-actions-for-adaptive-cards/Overview.md)
