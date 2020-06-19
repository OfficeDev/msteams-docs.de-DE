---
title: Hinzufügen von Karten Aktionen in einem bot
description: Beschreibt Karten Aktionen in Microsoft Teams und deren Verwendung in ihren Bots
keywords: Teams Bots Cards Aktionen
ms.openlocfilehash: e0b050cde9adf5bd811d5d95ce1c6f1bf60546a1
ms.sourcegitcommit: fdcd91b270d4c2e98ab2b2c1029c76c49bb807fa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "44801267"
---
# <a name="card-actions"></a><span data-ttu-id="c202d-104">Karten Aktionen</span><span class="sxs-lookup"><span data-stu-id="c202d-104">Card actions</span></span>

<span data-ttu-id="c202d-105">Von Bots und Messaging Erweiterungen in Microsoft Teams verwendete Karten unterstützen die folgenden Aktivitäts [`CardAction`](https://docs.microsoft.com/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments#process-events-within-rich-cards) Typen.</span><span class="sxs-lookup"><span data-stu-id="c202d-105">Cards used by bots and messaging extensions in Teams support the following activity ([`CardAction`](https://docs.microsoft.com/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments#process-events-within-rich-cards)) types.</span></span> <span data-ttu-id="c202d-106">Beachten Sie, dass sich diese Aktionen von `potentialActions` für Office 365-connectorkarten unterscheiden, wenn Sie von Connectors verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c202d-106">Note that these actions differ from `potentialActions` for Office 365 Connector cards when used from Connectors.</span></span>

| <span data-ttu-id="c202d-107">Typ</span><span class="sxs-lookup"><span data-stu-id="c202d-107">Type</span></span> | <span data-ttu-id="c202d-108">Aktion</span><span class="sxs-lookup"><span data-stu-id="c202d-108">Action</span></span> |
| --- | --- |
| `openUrl` | <span data-ttu-id="c202d-109">Öffnet eine URL im Standardbrowser.</span><span class="sxs-lookup"><span data-stu-id="c202d-109">Opens a URL in the default browser.</span></span> |
| `messageBack` | <span data-ttu-id="c202d-110">Sendet eine Nachricht und eine Nutzlast an den bot (von dem Benutzer, der auf die Schaltfläche geklickt oder die Karte angetippt hat) und sendet eine separate Nachricht an den Chat Datenstrom.</span><span class="sxs-lookup"><span data-stu-id="c202d-110">Sends a message and payload to the bot (from the user who clicked the button or tapped the card) and sends a separate message to the chat stream.</span></span> |
| `imBack`| <span data-ttu-id="c202d-111">Sendet eine Nachricht an den bot (von dem Benutzer, der auf die Schaltfläche geklickt oder die Karte angetippt hat).</span><span class="sxs-lookup"><span data-stu-id="c202d-111">Sends a message to the bot (from the user who clicked the button or tapped the card).</span></span> <span data-ttu-id="c202d-112">Diese Nachricht (von Benutzer zu bot) ist für alle Gesprächsteilnehmer sichtbar.</span><span class="sxs-lookup"><span data-stu-id="c202d-112">This message (from user to bot) is visible to all conversation participants.</span></span> |
| `invoke` | <span data-ttu-id="c202d-113">Sendet eine Nachricht und eine Nutzlast an den bot (von dem Benutzer, der auf die Schaltfläche geklickt oder die Karte angetippt hat).</span><span class="sxs-lookup"><span data-stu-id="c202d-113">Sends a message and payload to the bot (from the user who clicked the button or tapped the card).</span></span> <span data-ttu-id="c202d-114">Diese Nachricht ist nicht sichtbar.</span><span class="sxs-lookup"><span data-stu-id="c202d-114">This message is not visible.</span></span> |
| `signin` | <span data-ttu-id="c202d-115">Initiiert den OAuth-Fluss, sodass Bots eine Verbindung mit sicheren Diensten herstellen können.</span><span class="sxs-lookup"><span data-stu-id="c202d-115">Initiates OAuth flow, allowing bots to connect with secure services.</span></span> |

> [!NOTE]
>* <span data-ttu-id="c202d-116">In Microsoft Teams werden keine Typen unterstützt `CardAction` , die nicht in der obigen Tabelle aufgeführt sind.</span><span class="sxs-lookup"><span data-stu-id="c202d-116">Teams does not support `CardAction` types not listed in the preceding table.</span></span>
>* <span data-ttu-id="c202d-117">Die-Eigenschaft wird von Microsoft Teams nicht unterstützt `potentialActions` .</span><span class="sxs-lookup"><span data-stu-id="c202d-117">Teams does not support the `potentialActions` property.</span></span>
>* <span data-ttu-id="c202d-118">Karten Aktionen unterscheiden sich von [vorgeschlagenen Aktionen](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-add-suggested-actions?view=azure-bot-service-4.0&tabs=javascript#suggest-action-using-button) im bot-Framework/Azure-bot-Dienst.</span><span class="sxs-lookup"><span data-stu-id="c202d-118">Card actions are different than [suggested actions](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-add-suggested-actions?view=azure-bot-service-4.0&tabs=javascript#suggest-action-using-button) in Bot Framework/Azure Bot Service.</span></span> <span data-ttu-id="c202d-119">Vorgeschlagene Aktionen werden in Microsoft Teams nicht unterstützt: Wenn Sie möchten, dass Schaltflächen in einer Team-bot-Nachricht angezeigt werden, verwenden Sie eine Karte.</span><span class="sxs-lookup"><span data-stu-id="c202d-119">Suggested actions are not supported in Microsoft Teams: if you want buttons to appear on a Teams bot message, use a card.</span></span>
>* <span data-ttu-id="c202d-120">Wenn Sie eine Karten Aktion als Teil einer Messaging Erweiterung verwenden, werden die Aktionen erst ausgeführt, wenn die Karte an den Kanal gesendet wird (Sie funktionieren nicht, wenn sich die Karte im Meldungsfeld verfassen befindet).</span><span class="sxs-lookup"><span data-stu-id="c202d-120">If you're using a card action as part of a messaging extension, the actions will be not work until the card is submitted to the channel (they will not work while the card is in the compose message box).</span></span>

<span data-ttu-id="c202d-121">Teams unterstützen auch [Aktionen für Adaptive Karten](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions), die nur von adaptiven Karten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c202d-121">Teams also supports [Adaptive Cards actions](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions), which are only used by Adaptive Cards.</span></span> <span data-ttu-id="c202d-122">Diese Aktionen werden am Ende dieser Referenz in einem eigenen Abschnitt aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="c202d-122">These actions are listed in their own section at the end of this reference.</span></span>

## <a name="openurl"></a><span data-ttu-id="c202d-123">OpenURL</span><span class="sxs-lookup"><span data-stu-id="c202d-123">openUrl</span></span>

<span data-ttu-id="c202d-124">Dieser Aktionstyp gibt eine URL an, die im Standardbrowser gestartet werden soll.</span><span class="sxs-lookup"><span data-stu-id="c202d-124">This action type specifies a URL to launch in the default browser.</span></span> <span data-ttu-id="c202d-125">Beachten Sie, dass Ihr bot keinen Hinweis auf die Schaltfläche erhält, auf die geklickt wurde.</span><span class="sxs-lookup"><span data-stu-id="c202d-125">Note that your bot does not receive any notice on which button was clicked.</span></span>

<span data-ttu-id="c202d-126">Das `value` Feld muss eine vollständige und ordnungsgemäß formatierte URL enthalten.</span><span class="sxs-lookup"><span data-stu-id="c202d-126">The `value` field must contain a full and properly formed URL.</span></span>

```json
{
    "type": "openUrl",
    "title": "Tabs in Teams",
    "value": "https://msdn.microsoft.com/microsoft-teams/tabs"
}
```

## <a name="messageback"></a><span data-ttu-id="c202d-127">messageBack</span><span class="sxs-lookup"><span data-stu-id="c202d-127">messageBack</span></span>

<span data-ttu-id="c202d-128">Mit `messageBack` können Sie eine vollständig angepasste Aktion mit den folgenden Eigenschaften erstellen:</span><span class="sxs-lookup"><span data-stu-id="c202d-128">With `messageBack`, you can create a fully customized action with the following properties:</span></span>

| <span data-ttu-id="c202d-129">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="c202d-129">Property</span></span> | <span data-ttu-id="c202d-130">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c202d-130">Description</span></span> |
| --- | --- |
| `title` | <span data-ttu-id="c202d-131">Wird als Schaltflächenbeschriftung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c202d-131">Appears as the button label.</span></span> |
| `displayText` | <span data-ttu-id="c202d-132">Optional.</span><span class="sxs-lookup"><span data-stu-id="c202d-132">Optional.</span></span> <span data-ttu-id="c202d-133">Wird vom Benutzer im Chat-Stream wiedergegeben, wenn die Aktion ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c202d-133">Echoed by the user into the chat stream when the action is performed.</span></span> <span data-ttu-id="c202d-134">Dieser Text wird *nicht* an Ihren bot gesendet.</span><span class="sxs-lookup"><span data-stu-id="c202d-134">This text is *not* sent to your bot.</span></span> |
| `value` | <span data-ttu-id="c202d-135">An Ihren bot gesendet, wenn die Aktion ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c202d-135">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="c202d-136">Sie können den Kontext für die Aktion codieren, beispielsweise eindeutige Bezeichner oder ein JSON-Objekt.</span><span class="sxs-lookup"><span data-stu-id="c202d-136">You can encode context for the action, such as unique identifiers or a JSON object.</span></span> |
| `text` | <span data-ttu-id="c202d-137">An Ihren bot gesendet, wenn die Aktion ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c202d-137">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="c202d-138">Verwenden Sie diese Eigenschaft, um die bot-Entwicklung zu vereinfachen: Ihr Code kann eine einzelne Eigenschaft auf oberster Ebene zum Senden der bot-Logik überprüfen.</span><span class="sxs-lookup"><span data-stu-id="c202d-138">Use this property to simplify bot development: Your code can check a single top-level property to dispatch bot logic.</span></span> |

<span data-ttu-id="c202d-139">Die Flexibilität von `messageBack` bedeutet, dass Ihr Code wählen kann, keine sichtbare Benutzernachricht im Verlauf einfach zu hinterlassen, indem er nicht verwendet wird `displayText` .</span><span class="sxs-lookup"><span data-stu-id="c202d-139">The flexibility of `messageBack` means that your code can choose not to leave a visible user message in the history simply by not using `displayText`.</span></span>

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

<span data-ttu-id="c202d-140">Die `value` -Eigenschaft kann entweder eine serialisierte JSON-Zeichenfolge oder ein JSON-Objekt sein.</span><span class="sxs-lookup"><span data-stu-id="c202d-140">The `value` property can be either a serialized JSON string or a JSON object.</span></span>

### <a name="inbound-message-example"></a><span data-ttu-id="c202d-141">Beispiel für eingehende Nachrichten</span><span class="sxs-lookup"><span data-stu-id="c202d-141">Inbound message example</span></span>

<span data-ttu-id="c202d-142">`replyToId`enthält die ID der Nachricht, aus der die Karten Aktion stammt.</span><span class="sxs-lookup"><span data-stu-id="c202d-142">`replyToId` contains the ID of the message that the card action came from.</span></span> <span data-ttu-id="c202d-143">Verwenden Sie es, wenn Sie die Nachricht aktualisieren möchten.</span><span class="sxs-lookup"><span data-stu-id="c202d-143">Use it if you want to update the message.</span></span>

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

## <a name="imback"></a><span data-ttu-id="c202d-144">zurück</span><span class="sxs-lookup"><span data-stu-id="c202d-144">imBack</span></span>

<span data-ttu-id="c202d-145">Durch diese Aktion wird eine Rückgabemeldung an Ihren bot ausgelöst, als ob der Benutzer Sie in einer normalen Chatnachricht eingegeben hat.</span><span class="sxs-lookup"><span data-stu-id="c202d-145">This action triggers a return message to your bot, as if the user typed it in a normal chat message.</span></span> <span data-ttu-id="c202d-146">Der Benutzer und alle anderen Benutzer, die sich in einem Kanal befinden, sehen diese Schaltflächen Antwort.</span><span class="sxs-lookup"><span data-stu-id="c202d-146">Your user, and all other users if in a channel, will see that button response.</span></span>

<span data-ttu-id="c202d-147">Das `value` Feld sollte die Textzeichenfolge enthalten, die im Chat wiedergegeben wird und daher an den bot zurückgesendet wird.</span><span class="sxs-lookup"><span data-stu-id="c202d-147">The `value` field should contain the text string echoed in the chat and therefore sent back to the bot.</span></span> <span data-ttu-id="c202d-148">Dies ist der Nachrichtentext, den Sie in Ihrem bot verarbeiten werden, um die gewünschte Logik auszuführen.</span><span class="sxs-lookup"><span data-stu-id="c202d-148">This is the message text you will process in your bot to perform the desired logic.</span></span> <span data-ttu-id="c202d-149">Hinweis: Dieses Feld ist eine einfache Zeichenfolge-es gibt keine Unterstützung für die Formatierung oder versteckte Zeichen.</span><span class="sxs-lookup"><span data-stu-id="c202d-149">Note: this field is a simple string - there is no support for formatting or hidden characters.</span></span>

```json
{
    "type": "imBack",
    "title": "More",
    "value": "Show me more"
}
```

## <a name="invoke"></a><span data-ttu-id="c202d-150">Invoke</span><span class="sxs-lookup"><span data-stu-id="c202d-150">invoke</span></span>

<span data-ttu-id="c202d-151">Die `invoke` Aktion wird zum Aufrufen von [Aufgaben Modulen](~/task-modules-and-cards/task-modules/task-modules-bots.md)verwendet.</span><span class="sxs-lookup"><span data-stu-id="c202d-151">The `invoke` action is used for invoking [task modules](~/task-modules-and-cards/task-modules/task-modules-bots.md).</span></span>

<span data-ttu-id="c202d-152">Die `invoke` Aktion enthält drei Eigenschaften: `type` , `title` und `value` .</span><span class="sxs-lookup"><span data-stu-id="c202d-152">The `invoke` action contains three properties: `type`, `title`, and `value`.</span></span> <span data-ttu-id="c202d-153">Die `value` -Eigenschaft kann eine Zeichenfolge, ein stringified JSON-Objekt oder ein JSON-Objekt enthalten.</span><span class="sxs-lookup"><span data-stu-id="c202d-153">The `value` property can contain a string, a stringified JSON object, or a JSON object.</span></span>

```json
{
    "type": "invoke",
    "title": "Option 1",
    "value": {
        "option": "opt1"
    }
}
```

<span data-ttu-id="c202d-154">Wenn ein Benutzer auf die Schaltfläche klickt, erhält der bot das `value` Objekt mit zusätzlichen Informationen.</span><span class="sxs-lookup"><span data-stu-id="c202d-154">When a user clicks the button, your bot will receive the `value` object with some additional info.</span></span> <span data-ttu-id="c202d-155">Beachten Sie, dass der Aktivitätstyp `invoke` statt `message` () ist `activity.Type == "invoke"` .</span><span class="sxs-lookup"><span data-stu-id="c202d-155">Please note that the activity type will be `invoke` instead of `message` (`activity.Type == "invoke"`).</span></span>

### <a name="example-invoke-button-definition-net"></a><span data-ttu-id="c202d-156">Beispiel: Invoke-Schaltflächen Definition (.net)</span><span class="sxs-lookup"><span data-stu-id="c202d-156">Example: Invoke button definition (.NET)</span></span>

```csharp
var button = new CardAction()
{
    Title = "Option 1",
    Type = "invoke",
    Value = "{\"option\": \"opt1\"}"
};
```

### <a name="example-incoming-invoke-message"></a><span data-ttu-id="c202d-157">Beispiel: eingehende Invoke-Nachricht</span><span class="sxs-lookup"><span data-stu-id="c202d-157">Example: Incoming invoke message</span></span>

<span data-ttu-id="c202d-158">Die Eigenschaft der obersten Ebene `replyToId` enthält die ID der Nachricht, von der die Karten Aktion stammt.</span><span class="sxs-lookup"><span data-stu-id="c202d-158">The top-level `replyToId` property contains the ID of the message that the card action came from.</span></span> <span data-ttu-id="c202d-159">Verwenden Sie es, wenn Sie die Nachricht aktualisieren möchten.</span><span class="sxs-lookup"><span data-stu-id="c202d-159">Use it if you want to update the message.</span></span>

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

## <a name="signin"></a><span data-ttu-id="c202d-160">SignIn</span><span class="sxs-lookup"><span data-stu-id="c202d-160">signin</span></span>

<span data-ttu-id="c202d-161">Initiiert einen OAuth-Fluss, wodurch Bots eine Verbindung mit sicheren Diensten herstellen können, wie hier ausführlicher beschrieben: [Authentifizierungs Fluss in Bots](~/bots/how-to/authentication/auth-flow-bot.md).</span><span class="sxs-lookup"><span data-stu-id="c202d-161">Initiates an OAuth flow, allowing bots to connect with secure services, as described in more detail here: [Authentication flow in bots](~/bots/how-to/authentication/auth-flow-bot.md).</span></span>

## <a name="adaptive-cards-actions"></a><span data-ttu-id="c202d-162">Aktionen für Adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="c202d-162">Adaptive Cards actions</span></span>

<span data-ttu-id="c202d-163">Adaptive Karten unterstützen drei Aktionstypen:</span><span class="sxs-lookup"><span data-stu-id="c202d-163">Adaptive Cards support three action types:</span></span>

* [<span data-ttu-id="c202d-164">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="c202d-164">Action.OpenUrl</span></span>](http://adaptivecards.io/explorer/Action.OpenUrl.html)
* [<span data-ttu-id="c202d-165">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="c202d-165">Action.Submit</span></span>](http://adaptivecards.io/explorer/Action.Submit.html)
* [<span data-ttu-id="c202d-166">Action. ShowCard</span><span class="sxs-lookup"><span data-stu-id="c202d-166">Action.ShowCard</span></span>](http://adaptivecards.io/explorer/Action.ShowCard.html)

<span data-ttu-id="c202d-167">Zusätzlich zu den oben genannten Aktionen können Sie die Nutzlast der adaptiven Karte ändern, `Action.Submit` um vorhandene bot-Framework-Aktionen mithilfe einer `msteams` Eigenschaft im `data` Objekt von zu unterstützen `Action.Submit` .</span><span class="sxs-lookup"><span data-stu-id="c202d-167">In addition to the actions mentioned above, you can modify the Adaptive Card `Action.Submit` payload to support existing Bot Framework actions using a `msteams` property in the `data` object of `Action.Submit`.</span></span> <span data-ttu-id="c202d-168">In den folgenden Abschnitten wird erläutert, wie vorhandene bot-Framework-Aktionen mit adaptiven Karten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c202d-168">The below sections detail how to use existing Bot Framework actions with Adaptive Cards.</span></span>

### <a name="adaptive-cards-with-messageback-action"></a><span data-ttu-id="c202d-169">Adaptive Karten mit messageBack-Aktion</span><span class="sxs-lookup"><span data-stu-id="c202d-169">Adaptive Cards with messageBack action</span></span>

<span data-ttu-id="c202d-170">Um eine `messageBack` Aktion mit einer adaptiven Karte einzubeziehen, schließen Sie die folgenden Details in das `msteams` Objekt ein.</span><span class="sxs-lookup"><span data-stu-id="c202d-170">To include a `messageBack` action with an Adaptive Card include the following details in the `msteams` object.</span></span> <span data-ttu-id="c202d-171">Beachten Sie, dass Sie bei Bedarf zusätzliche verborgene Eigenschaften in das Objekt einschließen können `data` .</span><span class="sxs-lookup"><span data-stu-id="c202d-171">Note that you can include additional hidden properties in the `data` object if needed.</span></span>

| <span data-ttu-id="c202d-172">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="c202d-172">Property</span></span> | <span data-ttu-id="c202d-173">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c202d-173">Description</span></span> |
| --- | --- |
| `type` | <span data-ttu-id="c202d-174">Auf festlegen`messageBack`</span><span class="sxs-lookup"><span data-stu-id="c202d-174">Set to `messageBack`</span></span> |
| `displayText` | <span data-ttu-id="c202d-175">Optional.</span><span class="sxs-lookup"><span data-stu-id="c202d-175">Optional.</span></span> <span data-ttu-id="c202d-176">Wird vom Benutzer im Chat-Stream wiedergegeben, wenn die Aktion ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c202d-176">Echoed by the user into the chat stream when the action is performed.</span></span> <span data-ttu-id="c202d-177">Dieser Text wird *nicht* an Ihren bot gesendet.</span><span class="sxs-lookup"><span data-stu-id="c202d-177">This text is *not* sent to your bot.</span></span> |
| `value` | <span data-ttu-id="c202d-178">An Ihren bot gesendet, wenn die Aktion ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c202d-178">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="c202d-179">Sie können den Kontext für die Aktion codieren, beispielsweise eindeutige Bezeichner oder ein JSON-Objekt.</span><span class="sxs-lookup"><span data-stu-id="c202d-179">You can encode context for the action, such as unique identifiers or a JSON object.</span></span> |
| `text` | <span data-ttu-id="c202d-180">An Ihren bot gesendet, wenn die Aktion ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c202d-180">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="c202d-181">Verwenden Sie diese Eigenschaft, um die bot-Entwicklung zu vereinfachen: Ihr Code kann eine einzelne Eigenschaft auf oberster Ebene zum Senden der bot-Logik überprüfen.</span><span class="sxs-lookup"><span data-stu-id="c202d-181">Use this property to simplify bot development: Your code can check a single top-level property to dispatch bot logic.</span></span> |

#### <a name="example"></a><span data-ttu-id="c202d-182">Beispiel</span><span class="sxs-lookup"><span data-stu-id="c202d-182">Example</span></span>

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

### <a name="adaptive-cards-with-imback-action"></a><span data-ttu-id="c202d-183">Adaptive Karten mit Rück kehr Aktion</span><span class="sxs-lookup"><span data-stu-id="c202d-183">Adaptive Cards with imBack action</span></span>

<span data-ttu-id="c202d-184">Um eine `imBack` Aktion mit einer adaptiven Karte einzubeziehen, schließen Sie die folgenden Details in das `msteams` Objekt ein.</span><span class="sxs-lookup"><span data-stu-id="c202d-184">To include a `imBack` action with an Adaptive Card include the following details in the `msteams` object.</span></span> <span data-ttu-id="c202d-185">Beachten Sie, dass Sie bei Bedarf zusätzliche verborgene Eigenschaften in das Objekt einschließen können `data` .</span><span class="sxs-lookup"><span data-stu-id="c202d-185">Note that you can include additional hidden properties in the `data` object if needed.</span></span>

| <span data-ttu-id="c202d-186">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="c202d-186">Property</span></span> | <span data-ttu-id="c202d-187">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c202d-187">Description</span></span> |
| --- | --- |
| `type` | <span data-ttu-id="c202d-188">Auf festlegen`imBack`</span><span class="sxs-lookup"><span data-stu-id="c202d-188">Set to `imBack`</span></span> |
| `value` | <span data-ttu-id="c202d-189">Zeichenfolge, die im Chat wiederholt werden muss</span><span class="sxs-lookup"><span data-stu-id="c202d-189">String that needs to be echoed back in the chat</span></span> |

#### <a name="example"></a><span data-ttu-id="c202d-190">Beispiel</span><span class="sxs-lookup"><span data-stu-id="c202d-190">Example</span></span>

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

### <a name="adaptive-cards-with-signin-action"></a><span data-ttu-id="c202d-191">Adaptive Karten mit SignIn-Aktion</span><span class="sxs-lookup"><span data-stu-id="c202d-191">Adaptive Cards with signin action</span></span>

<span data-ttu-id="c202d-192">Um eine `signin` Aktion mit einer adaptiven Karte einzubeziehen, schließen Sie die folgenden Details in das `msteams` Objekt ein.</span><span class="sxs-lookup"><span data-stu-id="c202d-192">To include a `signin` action with an Adaptive Card include the following details in the `msteams` object.</span></span> <span data-ttu-id="c202d-193">Beachten Sie, dass Sie bei Bedarf zusätzliche verborgene Eigenschaften in das Objekt einschließen können `data` .</span><span class="sxs-lookup"><span data-stu-id="c202d-193">Note that you can include additional hidden properties in the `data` object if needed.</span></span>

| <span data-ttu-id="c202d-194">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="c202d-194">Property</span></span> | <span data-ttu-id="c202d-195">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c202d-195">Description</span></span> |
| --- | --- |
| `type` | <span data-ttu-id="c202d-196">Auf festlegen`signin`</span><span class="sxs-lookup"><span data-stu-id="c202d-196">Set to `signin`</span></span> |
| `value` | <span data-ttu-id="c202d-197">Legen Sie die URL fest, auf die umgeleitet werden soll.</span><span class="sxs-lookup"><span data-stu-id="c202d-197">Set to the URL that you want to redirect to</span></span>  |

#### <a name="example"></a><span data-ttu-id="c202d-198">Beispiel</span><span class="sxs-lookup"><span data-stu-id="c202d-198">Example</span></span>

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
