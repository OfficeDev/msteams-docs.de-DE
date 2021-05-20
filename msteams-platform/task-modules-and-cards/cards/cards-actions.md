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
# <a name="card-actions"></a><span data-ttu-id="91d78-104">Kartenaktionen</span><span class="sxs-lookup"><span data-stu-id="91d78-104">Card actions</span></span>

<span data-ttu-id="91d78-105">Karten, die von Bots und Messaging-Erweiterungen in Teams verwendet werden, unterstützen die folgenden Aktivitätstypen ( [`CardAction`](/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments#process-events-within-rich-cards) ).</span><span class="sxs-lookup"><span data-stu-id="91d78-105">Cards used by bots and messaging extensions in Teams support the following activity ([`CardAction`](/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments#process-events-within-rich-cards)) types.</span></span> <span data-ttu-id="91d78-106">Beachten Sie, dass sich diese Aktionen von `potentialActions` Office 365 Connectorkarten unterscheiden, wenn sie von Connectors verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="91d78-106">Note that these actions differ from `potentialActions` for Office 365 Connector cards when used from Connectors.</span></span>

| <span data-ttu-id="91d78-107">Typ</span><span class="sxs-lookup"><span data-stu-id="91d78-107">Type</span></span> | <span data-ttu-id="91d78-108">Aktion</span><span class="sxs-lookup"><span data-stu-id="91d78-108">Action</span></span> |
| --- | --- |
| `openUrl` | <span data-ttu-id="91d78-109">Öffnet eine URL im Standardbrowser.</span><span class="sxs-lookup"><span data-stu-id="91d78-109">Opens a URL in the default browser.</span></span> |
| `messageBack` | <span data-ttu-id="91d78-110">Sendet eine Nachricht und Nutzlast an den Bot von dem Benutzer, der auf die Schaltfläche geklickt oder auf die Karte getippt hat und eine separate Nachricht an den Chat-Stream sendet.</span><span class="sxs-lookup"><span data-stu-id="91d78-110">Sends a message and payload to the bot from the user who clicked the button or tapped the card and sends a separate message to the chat stream.</span></span> |
| `imBack`| <span data-ttu-id="91d78-111">Sendet eine Nachricht an den Bot von dem Benutzer, der auf die Schaltfläche geklickt oder auf die Karte getippt hat.</span><span class="sxs-lookup"><span data-stu-id="91d78-111">Sends a message to the bot from the user who clicked the button or tapped the card.</span></span> <span data-ttu-id="91d78-112">Diese Nachricht (vom Benutzer zum Bot) ist für alle Gesprächsteilnehmer sichtbar.</span><span class="sxs-lookup"><span data-stu-id="91d78-112">This message (from user to bot) is visible to all conversation participants.</span></span> |
| `invoke` | <span data-ttu-id="91d78-113">Sendet eine Nachricht und Nutzlast an den Bot von dem Benutzer, der auf die Schaltfläche geklickt oder auf die Karte getippt hat.</span><span class="sxs-lookup"><span data-stu-id="91d78-113">Sends a message and payload to the bot from the user who clicked the button or tapped the card.</span></span> <span data-ttu-id="91d78-114">Diese Meldung ist nicht sichtbar.</span><span class="sxs-lookup"><span data-stu-id="91d78-114">This message is not visible.</span></span> |
| `signin` | <span data-ttu-id="91d78-115">Initiiert den OAuth-Fluss, sodass Bots eine Verbindung mit sicheren Diensten herstellen können.</span><span class="sxs-lookup"><span data-stu-id="91d78-115">Initiates OAuth flow, allowing bots to connect with secure services.</span></span> |

> [!NOTE]
>* <span data-ttu-id="91d78-116">Teams unterstützt keine `CardAction` Typen, die in der obigen Tabelle nicht aufgeführt sind.</span><span class="sxs-lookup"><span data-stu-id="91d78-116">Teams does not support `CardAction` types not listed in the preceding table.</span></span>
>* <span data-ttu-id="91d78-117">Teams unterstützt die `potentialActions` Unterkunft nicht.</span><span class="sxs-lookup"><span data-stu-id="91d78-117">Teams does not support the `potentialActions` property.</span></span>
>* <span data-ttu-id="91d78-118">Kartenaktionen unterscheiden sich von [den vorgeschlagenen Aktionen](/azure/bot-service/bot-builder-howto-add-suggested-actions?view=azure-bot-service-4.0&tabs=javascript#suggest-action-using-button&preserve-view=true) in Bot Framework/Azure Bot Service.</span><span class="sxs-lookup"><span data-stu-id="91d78-118">Card actions are different than [suggested actions](/azure/bot-service/bot-builder-howto-add-suggested-actions?view=azure-bot-service-4.0&tabs=javascript#suggest-action-using-button&preserve-view=true) in Bot Framework/Azure Bot Service.</span></span> <span data-ttu-id="91d78-119">Vorgeschlagene Aktionen werden in Microsoft Teams nicht unterstützt: Wenn Schaltflächen auf einer Teams-Bot-Nachricht angezeigt werden sollen, verwenden Sie eine Karte.</span><span class="sxs-lookup"><span data-stu-id="91d78-119">Suggested actions are not supported in Microsoft Teams: if you want buttons to appear on a Teams bot message, use a card.</span></span>
>* <span data-ttu-id="91d78-120">Wenn Sie eine Kartenaktion als Teil einer Messagingerweiterung verwenden, funktionieren die Aktionen erst, wenn die Karte an den Kanal gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="91d78-120">If you are using a card action as part of a messaging extension, the actions do not work until the card is submitted to the channel.</span></span> <span data-ttu-id="91d78-121">Sie funktionieren nicht, während sich die Karte im Meldungsfeld verfassen befindet.</span><span class="sxs-lookup"><span data-stu-id="91d78-121">They do not work while the card is in the compose message box.</span></span>

<span data-ttu-id="91d78-122">Teams unterstützt auch [Adaptive Cards-Aktionen](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions), die nur von Adaptive Cards verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="91d78-122">Teams also supports [Adaptive Cards actions](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions), which are only used by Adaptive Cards.</span></span> <span data-ttu-id="91d78-123">Diese Aktionen werden in ihrem eigenen Abschnitt am Ende dieses Verweises aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="91d78-123">These actions are listed in their own section at the end of this reference.</span></span>

## <a name="openurl"></a><span data-ttu-id="91d78-124">OpenURL</span><span class="sxs-lookup"><span data-stu-id="91d78-124">openUrl</span></span>

<span data-ttu-id="91d78-125">Dieser Aktionstyp gibt eine URL an, die im Standardbrowser gestartet werden soll.</span><span class="sxs-lookup"><span data-stu-id="91d78-125">This action type specifies a URL to launch in the default browser.</span></span> <span data-ttu-id="91d78-126">Beachten Sie, dass Ihr Bot keine Benachrichtigung darüber erhält, auf welche Schaltfläche geklickt wurde.</span><span class="sxs-lookup"><span data-stu-id="91d78-126">Note that your bot does not receive any notice on which button was clicked.</span></span>

<span data-ttu-id="91d78-127">Das `value` Feld muss eine vollständige und ordnungsgemäß formatierte URL enthalten.</span><span class="sxs-lookup"><span data-stu-id="91d78-127">The `value` field must contain a full and properly formed URL.</span></span>

```json
{
    "type": "openUrl",
    "title": "Tabs in Teams",
    "value": "https://msdn.microsoft.com/microsoft-teams/tabs"
}
```

## <a name="messageback"></a><span data-ttu-id="91d78-128">MessageBack</span><span class="sxs-lookup"><span data-stu-id="91d78-128">messageBack</span></span>

<span data-ttu-id="91d78-129">Mit `messageBack` können Sie eine vollständig angepasste Aktion mit den folgenden Eigenschaften erstellen:</span><span class="sxs-lookup"><span data-stu-id="91d78-129">With `messageBack`, you can create a fully customized action with the following properties:</span></span>

| <span data-ttu-id="91d78-130">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="91d78-130">Property</span></span> | <span data-ttu-id="91d78-131">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="91d78-131">Description</span></span> |
| --- | --- |
| `title` | <span data-ttu-id="91d78-132">Wird als Schaltflächenbeschriftung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="91d78-132">Appears as the button label.</span></span> |
| `displayText` | <span data-ttu-id="91d78-133">Optional.</span><span class="sxs-lookup"><span data-stu-id="91d78-133">Optional.</span></span> <span data-ttu-id="91d78-134">Wird vom Benutzer in den Chat-Stream eingefügt, wenn die Aktion ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="91d78-134">Echoed by the user into the chat stream when the action is performed.</span></span> <span data-ttu-id="91d78-135">Dieser Text wird *nicht* an Ihren Bot gesendet.</span><span class="sxs-lookup"><span data-stu-id="91d78-135">This text is *not* sent to your bot.</span></span> |
| `value` | <span data-ttu-id="91d78-136">Wird an Ihren Bot gesendet, wenn die Aktion ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="91d78-136">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="91d78-137">Sie können den Kontext für die Aktion kodieren, z. B. eindeutige Bezeichner oder ein JSON-Objekt.</span><span class="sxs-lookup"><span data-stu-id="91d78-137">You can encode context for the action, such as unique identifiers or a JSON object.</span></span> |
| `text` | <span data-ttu-id="91d78-138">Wird an Ihren Bot gesendet, wenn die Aktion ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="91d78-138">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="91d78-139">Verwenden Sie diese Eigenschaft, um die Bot-Entwicklung zu vereinfachen: Ihr Code kann eine einzelne Eigenschaft der obersten Ebene überprüfen, um Botlogik zu versenden.</span><span class="sxs-lookup"><span data-stu-id="91d78-139">Use this property to simplify bot development: Your code can check a single top-level property to dispatch bot logic.</span></span> |

<span data-ttu-id="91d78-140">Die Flexibilität der `messageBack` Mittel, dass Ihr Code nicht eine sichtbare Benutzernachricht im Verlauf verlassen kann, indem Sie einfach nicht `displayText` .</span><span class="sxs-lookup"><span data-stu-id="91d78-140">The flexibility of `messageBack` means that your code can choose not to leave a visible user message in the history simply by not using `displayText`.</span></span>

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

<span data-ttu-id="91d78-141">Die `value` Eigenschaft kann entweder eine serialisierte JSON-Zeichenfolge oder ein JSON-Objekt sein.</span><span class="sxs-lookup"><span data-stu-id="91d78-141">The `value` property can be either a serialized JSON string or a JSON object.</span></span>

### <a name="inbound-message-example"></a><span data-ttu-id="91d78-142">Beispiel für eingehende Nachrichten</span><span class="sxs-lookup"><span data-stu-id="91d78-142">Inbound message example</span></span>

<span data-ttu-id="91d78-143">`replyToId` enthält die ID der Nachricht, aus der die Kartenaktion stammt.</span><span class="sxs-lookup"><span data-stu-id="91d78-143">`replyToId` contains the ID of the message that the card action came from.</span></span> <span data-ttu-id="91d78-144">Verwenden Sie sie, wenn Sie die Nachricht aktualisieren möchten.</span><span class="sxs-lookup"><span data-stu-id="91d78-144">Use it if you want to update the message.</span></span>

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

## <a name="imback"></a><span data-ttu-id="91d78-145">imBack</span><span class="sxs-lookup"><span data-stu-id="91d78-145">imBack</span></span>

<span data-ttu-id="91d78-146">Diese Aktion löst eine Rückgabemeldung an Ihren Bot aus, als ob der Benutzer sie in einer normalen Chatnachricht eingegeben hätte.</span><span class="sxs-lookup"><span data-stu-id="91d78-146">This action triggers a return message to your bot, as if the user typed it in a normal chat message.</span></span> <span data-ttu-id="91d78-147">Ihr Benutzer und alle anderen Benutzer, wenn sie sich in einem Kanal aufhalten, sehen diese Schaltflächenantwort.</span><span class="sxs-lookup"><span data-stu-id="91d78-147">Your user, and all other users if in a channel, will see that button response.</span></span>

<span data-ttu-id="91d78-148">Das `value` Feld sollte die Textzeichenfolge enthalten, die im Chat widerhallt und daher an den Bot zurückgesendet wird.</span><span class="sxs-lookup"><span data-stu-id="91d78-148">The `value` field should contain the text string echoed in the chat and therefore sent back to the bot.</span></span> <span data-ttu-id="91d78-149">Dies ist der Nachrichtentext, den Sie in Ihrem Bot verarbeiten werden, um die gewünschte Logik auszuführen.</span><span class="sxs-lookup"><span data-stu-id="91d78-149">This is the message text you will process in your bot to perform the desired logic.</span></span> <span data-ttu-id="91d78-150">Hinweis: Dieses Feld ist eine einfache Zeichenfolge - es gibt keine Unterstützung für Formatierung oder ausgeblendete Zeichen.</span><span class="sxs-lookup"><span data-stu-id="91d78-150">Note: this field is a simple string - there is no support for formatting or hidden characters.</span></span>

```json
{
    "type": "imBack",
    "title": "More",
    "value": "Show me more"
}
```

## <a name="invoke"></a><span data-ttu-id="91d78-151">Aufrufen</span><span class="sxs-lookup"><span data-stu-id="91d78-151">invoke</span></span>

<span data-ttu-id="91d78-152">Die `invoke` Aktion wird zum Aufrufen von [Aufgabenmodulen](~/task-modules-and-cards/task-modules/task-modules-bots.md)verwendet.</span><span class="sxs-lookup"><span data-stu-id="91d78-152">The `invoke` action is used for invoking [task modules](~/task-modules-and-cards/task-modules/task-modules-bots.md).</span></span>

<span data-ttu-id="91d78-153">Die `invoke` Aktion enthält drei Eigenschaften: , und `type` `title` `value` .</span><span class="sxs-lookup"><span data-stu-id="91d78-153">The `invoke` action contains three properties: `type`, `title`, and `value`.</span></span> <span data-ttu-id="91d78-154">Die `value` Eigenschaft kann eine Zeichenfolge, ein zeichenfolgeifiziertes JSON-Objekt oder ein JSON-Objekt enthalten.</span><span class="sxs-lookup"><span data-stu-id="91d78-154">The `value` property can contain a string, a stringified JSON object, or a JSON object.</span></span>

```json
{
    "type": "invoke",
    "title": "Option 1",
    "value": {
        "option": "opt1"
    }
}
```

<span data-ttu-id="91d78-155">Wenn ein Benutzer auf die Schaltfläche klickt, erhält Ihr Bot das `value` Objekt mit einigen zusätzlichen Informationen.</span><span class="sxs-lookup"><span data-stu-id="91d78-155">When a user clicks the button, your bot will receive the `value` object with some additional info.</span></span> <span data-ttu-id="91d78-156">Bitte beachten Sie, dass der Aktivitätstyp `invoke` anstelle von `message` ( `activity.Type == "invoke"` ) angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="91d78-156">Please note that the activity type will be `invoke` instead of `message` (`activity.Type == "invoke"`).</span></span>

### <a name="example-invoke-button-definition-net"></a><span data-ttu-id="91d78-157">Beispiel: Schaltflächendefinition aufrufen (.NET)</span><span class="sxs-lookup"><span data-stu-id="91d78-157">Example: Invoke button definition (.NET)</span></span>

```csharp
var button = new CardAction()
{
    Title = "Option 1",
    Type = "invoke",
    Value = "{\"option\": \"opt1\"}"
};
```

### <a name="example-incoming-invoke-message"></a><span data-ttu-id="91d78-158">Beispiel: Eingehende Aufrufnachricht</span><span class="sxs-lookup"><span data-stu-id="91d78-158">Example: Incoming invoke message</span></span>

<span data-ttu-id="91d78-159">Die Eigenschaft der obersten Ebene `replyToId` enthält die ID der Nachricht, aus der die Kartenaktion stammt.</span><span class="sxs-lookup"><span data-stu-id="91d78-159">The top-level `replyToId` property contains the ID of the message that the card action came from.</span></span> <span data-ttu-id="91d78-160">Verwenden Sie sie, wenn Sie die Nachricht aktualisieren möchten.</span><span class="sxs-lookup"><span data-stu-id="91d78-160">Use it if you want to update the message.</span></span>

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

## <a name="signin"></a><span data-ttu-id="91d78-161">Signin</span><span class="sxs-lookup"><span data-stu-id="91d78-161">signin</span></span>

<span data-ttu-id="91d78-162">Initiiert einen OAuth-Fluss, der es Bots ermöglicht, sich mit sicheren Diensten zu verbinden, wie hier ausführlicher beschrieben: [Authentifizierungsfluss in Bots](~/bots/how-to/authentication/auth-flow-bot.md).</span><span class="sxs-lookup"><span data-stu-id="91d78-162">Initiates an OAuth flow, allowing bots to connect with secure services, as described in more detail here: [Authentication flow in bots](~/bots/how-to/authentication/auth-flow-bot.md).</span></span>

## <a name="adaptive-cards-actions"></a><span data-ttu-id="91d78-163">Adaptive Kartenaktionen</span><span class="sxs-lookup"><span data-stu-id="91d78-163">Adaptive Cards actions</span></span>

<span data-ttu-id="91d78-164">Adaptive Karten unterstützen vier Aktionstypen:</span><span class="sxs-lookup"><span data-stu-id="91d78-164">Adaptive Cards support four action types:</span></span>

* [<span data-ttu-id="91d78-165">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="91d78-165">Action.OpenUrl</span></span>](http://adaptivecards.io/explorer/Action.OpenUrl.html)
* [<span data-ttu-id="91d78-166">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="91d78-166">Action.Submit</span></span>](http://adaptivecards.io/explorer/Action.Submit.html)
* [<span data-ttu-id="91d78-167">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="91d78-167">Action.ShowCard</span></span>](http://adaptivecards.io/explorer/Action.ShowCard.html)
* [<span data-ttu-id="91d78-168">Action.Exeniedlich</span><span class="sxs-lookup"><span data-stu-id="91d78-168">Action.Execute</span></span>](/adaptive-cards/authoring-cards/universal-action-model#actionexecute)

<span data-ttu-id="91d78-169">Zusätzlich zu den oben genannten Aktionen können Sie die `Action.Submit` Adaptive Card-Nutzlast ändern, um vorhandene Bot Framework-Aktionen mithilfe einer Eigenschaft im Objekt von zu `msteams` `data` `Action.Submit` unterstützen.</span><span class="sxs-lookup"><span data-stu-id="91d78-169">In addition to the actions mentioned above, you can modify the Adaptive Card `Action.Submit` payload to support existing Bot Framework actions using a `msteams` property in the `data` object of `Action.Submit`.</span></span> <span data-ttu-id="91d78-170">In den folgenden Abschnitten wird erläutert, wie vorhandene Bot Framework-Aktionen mit Adaptive Cards verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="91d78-170">The below sections detail how to use existing Bot Framework actions with Adaptive Cards.</span></span>

> [!NOTE]
> <span data-ttu-id="91d78-171">Das Hinzufügen `msteams` zu Daten mit einer Bot Framework-Aktion funktioniert nicht mit einem Taskmodul für adaptive Karten.</span><span class="sxs-lookup"><span data-stu-id="91d78-171">Adding `msteams` to data, with a Bot Framework action, does not work with an Adaptive Card task module.</span></span>

### <a name="adaptive-cards-with-messageback-action"></a><span data-ttu-id="91d78-172">Adaptive Karten mit messageBack-Aktion</span><span class="sxs-lookup"><span data-stu-id="91d78-172">Adaptive Cards with messageBack action</span></span>

<span data-ttu-id="91d78-173">Um eine Aktion mit einer adaptiven Karte einzuschließen, `messageBack` schließen Sie die folgenden Details in das Objekt `msteams` ein.</span><span class="sxs-lookup"><span data-stu-id="91d78-173">To include a `messageBack` action with an Adaptive Card include the following details in the `msteams` object.</span></span> <span data-ttu-id="91d78-174">Beachten Sie, dass Sie bei Bedarf zusätzliche ausgeblendete Eigenschaften in das Objekt einschließen `data` können.</span><span class="sxs-lookup"><span data-stu-id="91d78-174">Note that you can include additional hidden properties in the `data` object if needed.</span></span>

| <span data-ttu-id="91d78-175">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="91d78-175">Property</span></span> | <span data-ttu-id="91d78-176">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="91d78-176">Description</span></span> |
| --- | --- |
| `type` | <span data-ttu-id="91d78-177">Eingestellt auf `messageBack`</span><span class="sxs-lookup"><span data-stu-id="91d78-177">Set to `messageBack`</span></span> |
| `displayText` | <span data-ttu-id="91d78-178">Optional.</span><span class="sxs-lookup"><span data-stu-id="91d78-178">Optional.</span></span> <span data-ttu-id="91d78-179">Wird vom Benutzer in den Chat-Stream eingefügt, wenn die Aktion ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="91d78-179">Echoed by the user into the chat stream when the action is performed.</span></span> <span data-ttu-id="91d78-180">Dieser Text wird *nicht* an Ihren Bot gesendet.</span><span class="sxs-lookup"><span data-stu-id="91d78-180">This text is *not* sent to your bot.</span></span> |
| `value` | <span data-ttu-id="91d78-181">Wird an Ihren Bot gesendet, wenn die Aktion ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="91d78-181">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="91d78-182">Sie können den Kontext für die Aktion kodieren, z. B. eindeutige Bezeichner oder ein JSON-Objekt.</span><span class="sxs-lookup"><span data-stu-id="91d78-182">You can encode context for the action, such as unique identifiers or a JSON object.</span></span> |
| `text` | <span data-ttu-id="91d78-183">Wird an Ihren Bot gesendet, wenn die Aktion ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="91d78-183">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="91d78-184">Verwenden Sie diese Eigenschaft, um die Bot-Entwicklung zu vereinfachen: Ihr Code kann eine einzelne Eigenschaft der obersten Ebene überprüfen, um Botlogik zu versenden.</span><span class="sxs-lookup"><span data-stu-id="91d78-184">Use this property to simplify bot development: Your code can check a single top-level property to dispatch bot logic.</span></span> |

#### <a name="example"></a><span data-ttu-id="91d78-185">Beispiel</span><span class="sxs-lookup"><span data-stu-id="91d78-185">Example</span></span>

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

### <a name="adaptive-cards-with-imback-action"></a><span data-ttu-id="91d78-186">Adaptive Karten mit imBack-Aktion</span><span class="sxs-lookup"><span data-stu-id="91d78-186">Adaptive Cards with imBack action</span></span>

<span data-ttu-id="91d78-187">Um eine Aktion mit einer adaptiven Karte einzuschließen, `imBack` schließen Sie die folgenden Details in das Objekt `msteams` ein.</span><span class="sxs-lookup"><span data-stu-id="91d78-187">To include a `imBack` action with an Adaptive Card include the following details in the `msteams` object.</span></span> <span data-ttu-id="91d78-188">Beachten Sie, dass Sie bei Bedarf zusätzliche ausgeblendete Eigenschaften in das Objekt einschließen `data` können.</span><span class="sxs-lookup"><span data-stu-id="91d78-188">Note that you can include additional hidden properties in the `data` object if needed.</span></span>

| <span data-ttu-id="91d78-189">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="91d78-189">Property</span></span> | <span data-ttu-id="91d78-190">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="91d78-190">Description</span></span> |
| --- | --- |
| `type` | <span data-ttu-id="91d78-191">Eingestellt auf `imBack`</span><span class="sxs-lookup"><span data-stu-id="91d78-191">Set to `imBack`</span></span> |
| `value` | <span data-ttu-id="91d78-192">String, der im Chat wieder wiederholt werden muss</span><span class="sxs-lookup"><span data-stu-id="91d78-192">String that needs to be echoed back in the chat</span></span> |

#### <a name="example"></a><span data-ttu-id="91d78-193">Beispiel</span><span class="sxs-lookup"><span data-stu-id="91d78-193">Example</span></span>

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

### <a name="adaptive-cards-with-signin-action"></a><span data-ttu-id="91d78-194">Adaptive Karten mit Signin-Aktion</span><span class="sxs-lookup"><span data-stu-id="91d78-194">Adaptive Cards with signin action</span></span>

<span data-ttu-id="91d78-195">Um eine Aktion mit einer adaptiven Karte einzuschließen, `signin` schließen Sie die folgenden Details in das Objekt `msteams` ein.</span><span class="sxs-lookup"><span data-stu-id="91d78-195">To include a `signin` action with an Adaptive Card include the following details in the `msteams` object.</span></span> <span data-ttu-id="91d78-196">Beachten Sie, dass Sie bei Bedarf zusätzliche ausgeblendete Eigenschaften in das Objekt einschließen `data` können.</span><span class="sxs-lookup"><span data-stu-id="91d78-196">Note that you can include additional hidden properties in the `data` object if needed.</span></span>

| <span data-ttu-id="91d78-197">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="91d78-197">Property</span></span> | <span data-ttu-id="91d78-198">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="91d78-198">Description</span></span> |
| --- | --- |
| `type` | <span data-ttu-id="91d78-199">Auf `signin` .</span><span class="sxs-lookup"><span data-stu-id="91d78-199">Set to `signin`.</span></span> |
| `value` | <span data-ttu-id="91d78-200">Wird auf die URL festgelegt, zu der Sie umleiten möchten.</span><span class="sxs-lookup"><span data-stu-id="91d78-200">Set to the URL that you want to redirect to.</span></span>  |

#### <a name="example"></a><span data-ttu-id="91d78-201">Beispiel</span><span class="sxs-lookup"><span data-stu-id="91d78-201">Example</span></span>

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

### <a name="adaptive-cards-with-invoke-action"></a><span data-ttu-id="91d78-202">Adaptive Karten mit Aufrufaktion</span><span class="sxs-lookup"><span data-stu-id="91d78-202">Adaptive Cards with invoke action</span></span>
 
<span data-ttu-id="91d78-203">Um eine Aktion mit einer adaptiven Karte einzuschließen, `invoke` schließen Sie die folgenden Details in das Objekt `msteams` ein.</span><span class="sxs-lookup"><span data-stu-id="91d78-203">To include a `invoke` action with an Adaptive Card include the following details in the `msteams` object.</span></span> <span data-ttu-id="91d78-204">Beachten Sie, dass Sie bei Bedarf zusätzliche ausgeblendete Eigenschaften in das Objekt einschließen `data` können.</span><span class="sxs-lookup"><span data-stu-id="91d78-204">Note that you can include additional hidden properties in the `data` object if needed.</span></span>

| <span data-ttu-id="91d78-205">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="91d78-205">Property</span></span> | <span data-ttu-id="91d78-206">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="91d78-206">Description</span></span> |
| --- | --- |
| `type` | <span data-ttu-id="91d78-207">Eingestellt auf `task/fetch`</span><span class="sxs-lookup"><span data-stu-id="91d78-207">Set to `task/fetch`</span></span> |
| `data` | <span data-ttu-id="91d78-208">Legen Sie den Wert fest</span><span class="sxs-lookup"><span data-stu-id="91d78-208">Set the value</span></span>  |

#### <a name="example"></a><span data-ttu-id="91d78-209">Beispiel</span><span class="sxs-lookup"><span data-stu-id="91d78-209">Example</span></span>

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

#### <a name="example-2-with-additional-payload-data"></a><span data-ttu-id="91d78-210">Beispiel 2 (mit zusätzlichen Nutzlastdaten)</span><span class="sxs-lookup"><span data-stu-id="91d78-210">Example 2 (with additional payload data)</span></span>

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
