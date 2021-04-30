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
# <a name="card-actions"></a><span data-ttu-id="2f37f-104">Kartenaktionen</span><span class="sxs-lookup"><span data-stu-id="2f37f-104">Card actions</span></span>

<span data-ttu-id="2f37f-105">Karten, die von Bots und Messagingerweiterungen in Teams verwendet werden, unterstützen die folgenden Aktivitätstypen ( [`CardAction`](/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments#process-events-within-rich-cards) ).</span><span class="sxs-lookup"><span data-stu-id="2f37f-105">Cards used by bots and messaging extensions in Teams support the following activity ([`CardAction`](/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments#process-events-within-rich-cards)) types.</span></span> <span data-ttu-id="2f37f-106">Beachten Sie, dass sich diese Aktionen von Office 365 Connectorkarten unterscheiden, wenn `potentialActions` sie von Connectors verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="2f37f-106">Note that these actions differ from `potentialActions` for Office 365 Connector cards when used from Connectors.</span></span>

| <span data-ttu-id="2f37f-107">Typ</span><span class="sxs-lookup"><span data-stu-id="2f37f-107">Type</span></span> | <span data-ttu-id="2f37f-108">Aktion</span><span class="sxs-lookup"><span data-stu-id="2f37f-108">Action</span></span> |
| --- | --- |
| `openUrl` | <span data-ttu-id="2f37f-109">Öffnet eine URL im Standardbrowser.</span><span class="sxs-lookup"><span data-stu-id="2f37f-109">Opens a URL in the default browser.</span></span> |
| `messageBack` | <span data-ttu-id="2f37f-110">Sendet eine Nachricht und Nutzlast an den Bot (vom Benutzer, der auf die Schaltfläche geklickt oder auf die Karte getippt hat) und sendet eine separate Nachricht an den Chatstream.</span><span class="sxs-lookup"><span data-stu-id="2f37f-110">Sends a message and payload to the bot (from the user who clicked the button or tapped the card) and sends a separate message to the chat stream.</span></span> |
| `imBack`| <span data-ttu-id="2f37f-111">Sendet eine Nachricht an den Bot (vom Benutzer, der auf die Schaltfläche geklickt oder auf die Karte getippt hat).</span><span class="sxs-lookup"><span data-stu-id="2f37f-111">Sends a message to the bot (from the user who clicked the button or tapped the card).</span></span> <span data-ttu-id="2f37f-112">Diese Nachricht (von Benutzer zu Bot) ist für alle Unterhaltungsteilnehmer sichtbar.</span><span class="sxs-lookup"><span data-stu-id="2f37f-112">This message (from user to bot) is visible to all conversation participants.</span></span> |
| `invoke` | <span data-ttu-id="2f37f-113">Sendet eine Nachricht und Nutzlast an den Bot (vom Benutzer, der auf die Schaltfläche geklickt oder auf die Karte getippt hat).</span><span class="sxs-lookup"><span data-stu-id="2f37f-113">Sends a message and payload to the bot (from the user who clicked the button or tapped the card).</span></span> <span data-ttu-id="2f37f-114">Diese Meldung ist nicht sichtbar.</span><span class="sxs-lookup"><span data-stu-id="2f37f-114">This message is not visible.</span></span> |
| `signin` | <span data-ttu-id="2f37f-115">Initiiert den OAuth-Fluss, sodass Bots eine Verbindung mit sicheren Diensten herstellen können.</span><span class="sxs-lookup"><span data-stu-id="2f37f-115">Initiates OAuth flow, allowing bots to connect with secure services.</span></span> |

> [!NOTE]
>* <span data-ttu-id="2f37f-116">Teams unterstützt keine `CardAction` Typen, die in der vorherigen Tabelle nicht aufgeführt sind.</span><span class="sxs-lookup"><span data-stu-id="2f37f-116">Teams does not support `CardAction` types not listed in the preceding table.</span></span>
>* <span data-ttu-id="2f37f-117">Teams unterstützt die Eigenschaft `potentialActions` nicht.</span><span class="sxs-lookup"><span data-stu-id="2f37f-117">Teams does not support the `potentialActions` property.</span></span>
>* <span data-ttu-id="2f37f-118">Kartenaktionen unterscheiden sich von den [vorgeschlagenen Aktionen](/azure/bot-service/bot-builder-howto-add-suggested-actions?view=azure-bot-service-4.0&tabs=javascript#suggest-action-using-button&preserve-view=true) in Bot Framework/Azure Bot Service.</span><span class="sxs-lookup"><span data-stu-id="2f37f-118">Card actions are different than [suggested actions](/azure/bot-service/bot-builder-howto-add-suggested-actions?view=azure-bot-service-4.0&tabs=javascript#suggest-action-using-button&preserve-view=true) in Bot Framework/Azure Bot Service.</span></span> <span data-ttu-id="2f37f-119">Vorgeschlagene Aktionen werden in Microsoft Teams nicht unterstützt: Wenn Schaltflächen in einer Teams angezeigt werden sollen, verwenden Sie eine Karte.</span><span class="sxs-lookup"><span data-stu-id="2f37f-119">Suggested actions are not supported in Microsoft Teams: if you want buttons to appear on a Teams bot message, use a card.</span></span>
>* <span data-ttu-id="2f37f-120">Wenn Sie eine Kartenaktion als Teil einer Messagingerweiterung verwenden, funktionieren die Aktionen erst, wenn die Karte an den Kanal übermittelt wird (sie funktionieren nicht, während sich die Karte im Meldungsfeld Verfassen befindet).</span><span class="sxs-lookup"><span data-stu-id="2f37f-120">If you're using a card action as part of a messaging extension, the actions will be not work until the card is submitted to the channel (they will not work while the card is in the compose message box).</span></span>

<span data-ttu-id="2f37f-121">Teams unterstützt auch [adaptive Kartenaktionen,](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)die nur von adaptiven Karten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="2f37f-121">Teams also supports [Adaptive Cards actions](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions), which are only used by Adaptive Cards.</span></span> <span data-ttu-id="2f37f-122">Diese Aktionen werden in ihrem eigenen Abschnitt am Ende dieses Verweises aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="2f37f-122">These actions are listed in their own section at the end of this reference.</span></span>

## <a name="openurl"></a><span data-ttu-id="2f37f-123">OpenURL</span><span class="sxs-lookup"><span data-stu-id="2f37f-123">openUrl</span></span>

<span data-ttu-id="2f37f-124">Dieser Aktionstyp gibt eine URL an, die im Standardbrowser gestartet werden soll.</span><span class="sxs-lookup"><span data-stu-id="2f37f-124">This action type specifies a URL to launch in the default browser.</span></span> <span data-ttu-id="2f37f-125">Beachten Sie, dass Ihr Bot keine Benachrichtigung erhält, auf welche Schaltfläche geklickt wurde.</span><span class="sxs-lookup"><span data-stu-id="2f37f-125">Note that your bot does not receive any notice on which button was clicked.</span></span>

<span data-ttu-id="2f37f-126">Das `value` Feld muss eine vollständige und ordnungsgemäß gebildete URL enthalten.</span><span class="sxs-lookup"><span data-stu-id="2f37f-126">The `value` field must contain a full and properly formed URL.</span></span>

```json
{
    "type": "openUrl",
    "title": "Tabs in Teams",
    "value": "https://msdn.microsoft.com/microsoft-teams/tabs"
}
```

## <a name="messageback"></a><span data-ttu-id="2f37f-127">messageBack</span><span class="sxs-lookup"><span data-stu-id="2f37f-127">messageBack</span></span>

<span data-ttu-id="2f37f-128">Mit `messageBack` können Sie eine vollständig angepasste Aktion mit den folgenden Eigenschaften erstellen:</span><span class="sxs-lookup"><span data-stu-id="2f37f-128">With `messageBack`, you can create a fully customized action with the following properties:</span></span>

| <span data-ttu-id="2f37f-129">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="2f37f-129">Property</span></span> | <span data-ttu-id="2f37f-130">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2f37f-130">Description</span></span> |
| --- | --- |
| `title` | <span data-ttu-id="2f37f-131">Wird als Schaltflächenbeschriftung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="2f37f-131">Appears as the button label.</span></span> |
| `displayText` | <span data-ttu-id="2f37f-132">Optional.</span><span class="sxs-lookup"><span data-stu-id="2f37f-132">Optional.</span></span> <span data-ttu-id="2f37f-133">Echoed by the user into the chat stream when the action is performed.</span><span class="sxs-lookup"><span data-stu-id="2f37f-133">Echoed by the user into the chat stream when the action is performed.</span></span> <span data-ttu-id="2f37f-134">Dieser Text wird *nicht an* Ihren Bot gesendet.</span><span class="sxs-lookup"><span data-stu-id="2f37f-134">This text is *not* sent to your bot.</span></span> |
| `value` | <span data-ttu-id="2f37f-135">Wird an Ihren Bot gesendet, wenn die Aktion ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="2f37f-135">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="2f37f-136">Sie können den Kontext für die Aktion codieren, z. B. eindeutige Bezeichner oder ein JSON-Objekt.</span><span class="sxs-lookup"><span data-stu-id="2f37f-136">You can encode context for the action, such as unique identifiers or a JSON object.</span></span> |
| `text` | <span data-ttu-id="2f37f-137">Wird an Ihren Bot gesendet, wenn die Aktion ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="2f37f-137">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="2f37f-138">Verwenden Sie diese Eigenschaft, um die Botentwicklung zu vereinfachen: Ihr Code kann eine einzelne Eigenschaft auf oberster Ebene überprüfen, um Botlogik zu versenden.</span><span class="sxs-lookup"><span data-stu-id="2f37f-138">Use this property to simplify bot development: Your code can check a single top-level property to dispatch bot logic.</span></span> |

<span data-ttu-id="2f37f-139">Die Flexibilität von bedeutet, dass Ihr Code auswählen kann, keine sichtbare Benutzernachricht im Verlauf zu hinterlassen, indem `messageBack` einfach nicht verwendet `displayText` wird.</span><span class="sxs-lookup"><span data-stu-id="2f37f-139">The flexibility of `messageBack` means that your code can choose not to leave a visible user message in the history simply by not using `displayText`.</span></span>

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

<span data-ttu-id="2f37f-140">Die `value` Eigenschaft kann entweder eine serialisierte JSON-Zeichenfolge oder ein JSON-Objekt sein.</span><span class="sxs-lookup"><span data-stu-id="2f37f-140">The `value` property can be either a serialized JSON string or a JSON object.</span></span>

### <a name="inbound-message-example"></a><span data-ttu-id="2f37f-141">Beispiel für eingehende Nachrichten</span><span class="sxs-lookup"><span data-stu-id="2f37f-141">Inbound message example</span></span>

<span data-ttu-id="2f37f-142">`replyToId` enthält die ID der Nachricht, aus der die Kartenaktion stammt.</span><span class="sxs-lookup"><span data-stu-id="2f37f-142">`replyToId` contains the ID of the message that the card action came from.</span></span> <span data-ttu-id="2f37f-143">Verwenden Sie sie, wenn Sie die Nachricht aktualisieren möchten.</span><span class="sxs-lookup"><span data-stu-id="2f37f-143">Use it if you want to update the message.</span></span>

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

## <a name="imback"></a><span data-ttu-id="2f37f-144">imBack</span><span class="sxs-lookup"><span data-stu-id="2f37f-144">imBack</span></span>

<span data-ttu-id="2f37f-145">Diese Aktion löst eine Rückgabenachricht an Ihren Bot aus, als würde der Benutzer sie in eine normale Chatnachricht eingeben.</span><span class="sxs-lookup"><span data-stu-id="2f37f-145">This action triggers a return message to your bot, as if the user typed it in a normal chat message.</span></span> <span data-ttu-id="2f37f-146">Ihr Benutzer und alle anderen Benutzer in einem Kanal sehen diese Schaltflächenantwort.</span><span class="sxs-lookup"><span data-stu-id="2f37f-146">Your user, and all other users if in a channel, will see that button response.</span></span>

<span data-ttu-id="2f37f-147">Das `value` Feld sollte die Textzeichenfolge enthalten, die im Chat widerhallt und daher an den Bot gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="2f37f-147">The `value` field should contain the text string echoed in the chat and therefore sent back to the bot.</span></span> <span data-ttu-id="2f37f-148">Dies ist der Nachrichtentext, den Sie in Ihrem Bot verarbeiten, um die gewünschte Logik durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="2f37f-148">This is the message text you will process in your bot to perform the desired logic.</span></span> <span data-ttu-id="2f37f-149">Hinweis: Dieses Feld ist eine einfache Zeichenfolge – es gibt keine Unterstützung für Formatierungen oder ausgeblendete Zeichen.</span><span class="sxs-lookup"><span data-stu-id="2f37f-149">Note: this field is a simple string - there is no support for formatting or hidden characters.</span></span>

```json
{
    "type": "imBack",
    "title": "More",
    "value": "Show me more"
}
```

## <a name="invoke"></a><span data-ttu-id="2f37f-150">invoke</span><span class="sxs-lookup"><span data-stu-id="2f37f-150">invoke</span></span>

<span data-ttu-id="2f37f-151">Die `invoke` Aktion wird zum Aufrufen von [Aufgabenmodulen verwendet.](~/task-modules-and-cards/task-modules/task-modules-bots.md)</span><span class="sxs-lookup"><span data-stu-id="2f37f-151">The `invoke` action is used for invoking [task modules](~/task-modules-and-cards/task-modules/task-modules-bots.md).</span></span>

<span data-ttu-id="2f37f-152">Die `invoke` Aktion enthält drei Eigenschaften: , und `type` `title` `value` .</span><span class="sxs-lookup"><span data-stu-id="2f37f-152">The `invoke` action contains three properties: `type`, `title`, and `value`.</span></span> <span data-ttu-id="2f37f-153">Die `value` Eigenschaft kann eine Zeichenfolge, ein zeichenfolgenbesetztes JSON-Objekt oder ein JSON-Objekt enthalten.</span><span class="sxs-lookup"><span data-stu-id="2f37f-153">The `value` property can contain a string, a stringified JSON object, or a JSON object.</span></span>

```json
{
    "type": "invoke",
    "title": "Option 1",
    "value": {
        "option": "opt1"
    }
}
```

<span data-ttu-id="2f37f-154">Wenn ein Benutzer auf die Schaltfläche klickt, erhält ihr Bot das `value` Objekt mit einigen zusätzlichen Informationen.</span><span class="sxs-lookup"><span data-stu-id="2f37f-154">When a user clicks the button, your bot will receive the `value` object with some additional info.</span></span> <span data-ttu-id="2f37f-155">Beachten Sie, dass der Aktivitätstyp anstelle `invoke` von `message` ( `activity.Type == "invoke"` ist).</span><span class="sxs-lookup"><span data-stu-id="2f37f-155">Please note that the activity type will be `invoke` instead of `message` (`activity.Type == "invoke"`).</span></span>

### <a name="example-invoke-button-definition-net"></a><span data-ttu-id="2f37f-156">Beispiel: Aufrufen der Schaltflächendefinition (.NET)</span><span class="sxs-lookup"><span data-stu-id="2f37f-156">Example: Invoke button definition (.NET)</span></span>

```csharp
var button = new CardAction()
{
    Title = "Option 1",
    Type = "invoke",
    Value = "{\"option\": \"opt1\"}"
};
```

### <a name="example-incoming-invoke-message"></a><span data-ttu-id="2f37f-157">Beispiel: Eingehende Aufrufnachricht</span><span class="sxs-lookup"><span data-stu-id="2f37f-157">Example: Incoming invoke message</span></span>

<span data-ttu-id="2f37f-158">Die Eigenschaft auf `replyToId` oberster Ebene enthält die ID der Nachricht, aus der die Kartenaktion stammt.</span><span class="sxs-lookup"><span data-stu-id="2f37f-158">The top-level `replyToId` property contains the ID of the message that the card action came from.</span></span> <span data-ttu-id="2f37f-159">Verwenden Sie sie, wenn Sie die Nachricht aktualisieren möchten.</span><span class="sxs-lookup"><span data-stu-id="2f37f-159">Use it if you want to update the message.</span></span>

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

## <a name="signin"></a><span data-ttu-id="2f37f-160">signin</span><span class="sxs-lookup"><span data-stu-id="2f37f-160">signin</span></span>

<span data-ttu-id="2f37f-161">Initiiert einen OAuth-Fluss, sodass Bots eine Verbindung mit sicheren Diensten herstellen können, wie hier ausführlicher beschrieben: [Authentifizierungsfluss in Bots](~/bots/how-to/authentication/auth-flow-bot.md).</span><span class="sxs-lookup"><span data-stu-id="2f37f-161">Initiates an OAuth flow, allowing bots to connect with secure services, as described in more detail here: [Authentication flow in bots](~/bots/how-to/authentication/auth-flow-bot.md).</span></span>

## <a name="adaptive-cards-actions"></a><span data-ttu-id="2f37f-162">Aktionen mit adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="2f37f-162">Adaptive Cards actions</span></span>

<span data-ttu-id="2f37f-163">Adaptive Karten unterstützen vier Aktionstypen:</span><span class="sxs-lookup"><span data-stu-id="2f37f-163">Adaptive Cards support four action types:</span></span>

* [<span data-ttu-id="2f37f-164">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="2f37f-164">Action.OpenUrl</span></span>](http://adaptivecards.io/explorer/Action.OpenUrl.html)
* [<span data-ttu-id="2f37f-165">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="2f37f-165">Action.Submit</span></span>](http://adaptivecards.io/explorer/Action.Submit.html)
* [<span data-ttu-id="2f37f-166">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="2f37f-166">Action.ShowCard</span></span>](http://adaptivecards.io/explorer/Action.ShowCard.html)
* [<span data-ttu-id="2f37f-167">Action.Execute</span><span class="sxs-lookup"><span data-stu-id="2f37f-167">Action.Execute</span></span>](https://docs.microsoft.com/adaptive-cards/authoring-cards/universal-action-model#actionexecute)

<span data-ttu-id="2f37f-168">Zusätzlich zu den oben genannten Aktionen können Sie die Nutzlast der adaptiven Karte so ändern, dass vorhandene Bot Framework-Aktionen mithilfe einer Eigenschaft `Action.Submit` im Objekt von unterstützt `msteams` `data` `Action.Submit` werden.</span><span class="sxs-lookup"><span data-stu-id="2f37f-168">In addition to the actions mentioned above, you can modify the Adaptive Card `Action.Submit` payload to support existing Bot Framework actions using a `msteams` property in the `data` object of `Action.Submit`.</span></span> <span data-ttu-id="2f37f-169">In den folgenden Abschnitten erfahren Sie, wie Sie vorhandene Bot Framework-Aktionen mit adaptiven Karten verwenden.</span><span class="sxs-lookup"><span data-stu-id="2f37f-169">The below sections detail how to use existing Bot Framework actions with Adaptive Cards.</span></span>

> [!NOTE]
> <span data-ttu-id="2f37f-170">Das Hinzufügen zu Daten mit einer Bot Framework-Aktion funktioniert `msteams` nicht mit einem Aufgabenmodul für adaptive Karten.</span><span class="sxs-lookup"><span data-stu-id="2f37f-170">Adding `msteams` to data, with a Bot Framework action, does not work with an Adaptive Card task module.</span></span>

### <a name="adaptive-cards-with-messageback-action"></a><span data-ttu-id="2f37f-171">Adaptive Karten mit messageBack-Aktion</span><span class="sxs-lookup"><span data-stu-id="2f37f-171">Adaptive Cards with messageBack action</span></span>

<span data-ttu-id="2f37f-172">Um eine `messageBack` Aktion mit einer adaptiven Karte zu verwenden, fügen Sie die folgenden Details in das Objekt `msteams` ein.</span><span class="sxs-lookup"><span data-stu-id="2f37f-172">To include a `messageBack` action with an Adaptive Card include the following details in the `msteams` object.</span></span> <span data-ttu-id="2f37f-173">Beachten Sie, dass Sie bei Bedarf zusätzliche ausgeblendete Eigenschaften in das `data` Objekt verwenden können.</span><span class="sxs-lookup"><span data-stu-id="2f37f-173">Note that you can include additional hidden properties in the `data` object if needed.</span></span>

| <span data-ttu-id="2f37f-174">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="2f37f-174">Property</span></span> | <span data-ttu-id="2f37f-175">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2f37f-175">Description</span></span> |
| --- | --- |
| `type` | <span data-ttu-id="2f37f-176">Set to `messageBack`</span><span class="sxs-lookup"><span data-stu-id="2f37f-176">Set to `messageBack`</span></span> |
| `displayText` | <span data-ttu-id="2f37f-177">Optional.</span><span class="sxs-lookup"><span data-stu-id="2f37f-177">Optional.</span></span> <span data-ttu-id="2f37f-178">Echoed by the user into the chat stream when the action is performed.</span><span class="sxs-lookup"><span data-stu-id="2f37f-178">Echoed by the user into the chat stream when the action is performed.</span></span> <span data-ttu-id="2f37f-179">Dieser Text wird *nicht an* Ihren Bot gesendet.</span><span class="sxs-lookup"><span data-stu-id="2f37f-179">This text is *not* sent to your bot.</span></span> |
| `value` | <span data-ttu-id="2f37f-180">Wird an Ihren Bot gesendet, wenn die Aktion ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="2f37f-180">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="2f37f-181">Sie können den Kontext für die Aktion codieren, z. B. eindeutige Bezeichner oder ein JSON-Objekt.</span><span class="sxs-lookup"><span data-stu-id="2f37f-181">You can encode context for the action, such as unique identifiers or a JSON object.</span></span> |
| `text` | <span data-ttu-id="2f37f-182">Wird an Ihren Bot gesendet, wenn die Aktion ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="2f37f-182">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="2f37f-183">Verwenden Sie diese Eigenschaft, um die Botentwicklung zu vereinfachen: Ihr Code kann eine einzelne Eigenschaft auf oberster Ebene überprüfen, um Botlogik zu versenden.</span><span class="sxs-lookup"><span data-stu-id="2f37f-183">Use this property to simplify bot development: Your code can check a single top-level property to dispatch bot logic.</span></span> |

#### <a name="example"></a><span data-ttu-id="2f37f-184">Beispiel</span><span class="sxs-lookup"><span data-stu-id="2f37f-184">Example</span></span>

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

### <a name="adaptive-cards-with-imback-action"></a><span data-ttu-id="2f37f-185">Adaptive Karten mit imBack-Aktion</span><span class="sxs-lookup"><span data-stu-id="2f37f-185">Adaptive Cards with imBack action</span></span>

<span data-ttu-id="2f37f-186">Um eine `imBack` Aktion mit einer adaptiven Karte zu verwenden, fügen Sie die folgenden Details in das Objekt `msteams` ein.</span><span class="sxs-lookup"><span data-stu-id="2f37f-186">To include a `imBack` action with an Adaptive Card include the following details in the `msteams` object.</span></span> <span data-ttu-id="2f37f-187">Beachten Sie, dass Sie bei Bedarf zusätzliche ausgeblendete Eigenschaften in das `data` Objekt verwenden können.</span><span class="sxs-lookup"><span data-stu-id="2f37f-187">Note that you can include additional hidden properties in the `data` object if needed.</span></span>

| <span data-ttu-id="2f37f-188">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="2f37f-188">Property</span></span> | <span data-ttu-id="2f37f-189">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2f37f-189">Description</span></span> |
| --- | --- |
| `type` | <span data-ttu-id="2f37f-190">Set to `imBack`</span><span class="sxs-lookup"><span data-stu-id="2f37f-190">Set to `imBack`</span></span> |
| `value` | <span data-ttu-id="2f37f-191">Zeichenfolge, die im Chat wiederholt werden muss</span><span class="sxs-lookup"><span data-stu-id="2f37f-191">String that needs to be echoed back in the chat</span></span> |

#### <a name="example"></a><span data-ttu-id="2f37f-192">Beispiel</span><span class="sxs-lookup"><span data-stu-id="2f37f-192">Example</span></span>

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

### <a name="adaptive-cards-with-signin-action"></a><span data-ttu-id="2f37f-193">Adaptive Karten mit Anmeldeaktion</span><span class="sxs-lookup"><span data-stu-id="2f37f-193">Adaptive Cards with signin action</span></span>

<span data-ttu-id="2f37f-194">Um eine `signin` Aktion mit einer adaptiven Karte zu verwenden, fügen Sie die folgenden Details in das Objekt `msteams` ein.</span><span class="sxs-lookup"><span data-stu-id="2f37f-194">To include a `signin` action with an Adaptive Card include the following details in the `msteams` object.</span></span> <span data-ttu-id="2f37f-195">Beachten Sie, dass Sie bei Bedarf zusätzliche ausgeblendete Eigenschaften in das `data` Objekt verwenden können.</span><span class="sxs-lookup"><span data-stu-id="2f37f-195">Note that you can include additional hidden properties in the `data` object if needed.</span></span>

| <span data-ttu-id="2f37f-196">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="2f37f-196">Property</span></span> | <span data-ttu-id="2f37f-197">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2f37f-197">Description</span></span> |
| --- | --- |
| `type` | <span data-ttu-id="2f37f-198">Set to `signin`</span><span class="sxs-lookup"><span data-stu-id="2f37f-198">Set to `signin`</span></span> |
| `value` | <span data-ttu-id="2f37f-199">Festlegen auf die URL, an die Sie umleiten möchten</span><span class="sxs-lookup"><span data-stu-id="2f37f-199">Set to the URL that you want to redirect to</span></span>  |

#### <a name="example"></a><span data-ttu-id="2f37f-200">Beispiel</span><span class="sxs-lookup"><span data-stu-id="2f37f-200">Example</span></span>

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

### <a name="adaptive-cards-with-invoke-action"></a><span data-ttu-id="2f37f-201">Adaptive Karten mit Aufrufaktion</span><span class="sxs-lookup"><span data-stu-id="2f37f-201">Adaptive Cards with invoke action</span></span>
 
<span data-ttu-id="2f37f-202">Um eine `invoke` Aktion mit einer adaptiven Karte zu verwenden, fügen Sie die folgenden Details in das Objekt `msteams` ein.</span><span class="sxs-lookup"><span data-stu-id="2f37f-202">To include a `invoke` action with an Adaptive Card include the following details in the `msteams` object.</span></span> <span data-ttu-id="2f37f-203">Beachten Sie, dass Sie bei Bedarf zusätzliche ausgeblendete Eigenschaften in das `data` Objekt verwenden können.</span><span class="sxs-lookup"><span data-stu-id="2f37f-203">Note that you can include additional hidden properties in the `data` object if needed.</span></span>

| <span data-ttu-id="2f37f-204">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="2f37f-204">Property</span></span> | <span data-ttu-id="2f37f-205">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2f37f-205">Description</span></span> |
| --- | --- |
| `type` | <span data-ttu-id="2f37f-206">Set to `task/fetch`</span><span class="sxs-lookup"><span data-stu-id="2f37f-206">Set to `task/fetch`</span></span> |
| `data` | <span data-ttu-id="2f37f-207">Festlegen des Werts</span><span class="sxs-lookup"><span data-stu-id="2f37f-207">Set the value</span></span>  |

#### <a name="example"></a><span data-ttu-id="2f37f-208">Beispiel</span><span class="sxs-lookup"><span data-stu-id="2f37f-208">Example</span></span>

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

#### <a name="example-2-with-additional-payload-data"></a><span data-ttu-id="2f37f-209">Beispiel 2 (mit zusätzlichen Nutzlastdaten)</span><span class="sxs-lookup"><span data-stu-id="2f37f-209">Example 2 (with additional payload data)</span></span>

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
