---
title: Hinzufügen von Kartenaktionen in einem Bot
description: Beschreibt Kartenaktionen in Microsoft Teams und deren Verwendung in Ihren Bots
localization_priority: Normal
ms.topic: conceptual
keywords: Aktionen für Teams-Bots-Karten
ms.openlocfilehash: 4af152f6179785687d4fd7371d202c56e1aee170
ms.sourcegitcommit: 9d63611974ba8a7e7f19ceea35e50189a2e90434
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2021
ms.locfileid: "53254202"
---
# <a name="card-actions"></a><span data-ttu-id="c1be9-104">Kartenaktionen</span><span class="sxs-lookup"><span data-stu-id="c1be9-104">Card actions</span></span>

<span data-ttu-id="c1be9-105">Karten, die von Bots und Messaging-Erweiterungen in Teams verwendet werden, unterstützen die folgenden [`CardAction`](/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments#process-events-within-rich-cards) Aktivitätstypen:</span><span class="sxs-lookup"><span data-stu-id="c1be9-105">Cards used by bots and messaging extensions in Teams support the following activity [`CardAction`](/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments#process-events-within-rich-cards) types:</span></span>

> [!NOTE]
> <span data-ttu-id="c1be9-106">Die `CardAction` Aktionen unterscheiden sich von Office 365 `potentialActions` Konnektorkarten, wenn sie von Connectors verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c1be9-106">The `CardAction` actions differ from `potentialActions` for Office 365 Connector cards when used from connectors.</span></span>

| <span data-ttu-id="c1be9-107">Typ</span><span class="sxs-lookup"><span data-stu-id="c1be9-107">Type</span></span> | <span data-ttu-id="c1be9-108">Aktion</span><span class="sxs-lookup"><span data-stu-id="c1be9-108">Action</span></span> |
| --- | --- |
| `openUrl` | <span data-ttu-id="c1be9-109">Öffnet eine URL im Standardbrowser.</span><span class="sxs-lookup"><span data-stu-id="c1be9-109">Opens a URL in the default browser.</span></span> |
| `messageBack` | <span data-ttu-id="c1be9-110">Sendet eine Nachricht und Nutzlast vom Benutzer, der die Schaltfläche ausgewählt oder auf die Karte getippt hat, an den Bot.</span><span class="sxs-lookup"><span data-stu-id="c1be9-110">Sends a message and payload to the bot from the user who selected the button or tapped the card.</span></span> <span data-ttu-id="c1be9-111">Sendet eine separate Nachricht an den Chatstream.</span><span class="sxs-lookup"><span data-stu-id="c1be9-111">Sends a separate message to the chat stream.</span></span> |
| `imBack`| <span data-ttu-id="c1be9-112">Sendet eine Nachricht vom Benutzer, der die Schaltfläche ausgewählt oder auf die Karte getippt hat, an den Bot.</span><span class="sxs-lookup"><span data-stu-id="c1be9-112">Sends a message to the bot from the user who selected the button or tapped the card.</span></span> <span data-ttu-id="c1be9-113">Diese Nachricht von Benutzer zu Bot ist für alle Unterhaltungsteilnehmer sichtbar.</span><span class="sxs-lookup"><span data-stu-id="c1be9-113">This message from user to bot is visible to all conversation participants.</span></span> |
| `invoke` | <span data-ttu-id="c1be9-114">Sendet eine Nachricht und Nutzlast vom Benutzer, der die Schaltfläche ausgewählt oder auf die Karte getippt hat, an den Bot.</span><span class="sxs-lookup"><span data-stu-id="c1be9-114">Sends a message and payload to the bot from the user who selected the button or tapped the card.</span></span> <span data-ttu-id="c1be9-115">Diese Meldung ist nicht sichtbar.</span><span class="sxs-lookup"><span data-stu-id="c1be9-115">This message is not visible.</span></span> |
| `signin` | <span data-ttu-id="c1be9-116">Initiiert den OAuth-Fluss, sodass Bots eine Verbindung mit sicheren Diensten herstellen können.</span><span class="sxs-lookup"><span data-stu-id="c1be9-116">Initiates OAuth flow, allowing bots to connect with secure services.</span></span> |

> [!NOTE]
>* <span data-ttu-id="c1be9-117">Teams unterstützt keine `CardAction` Typen, die in der vorherigen Tabelle nicht aufgeführt sind.</span><span class="sxs-lookup"><span data-stu-id="c1be9-117">Teams does not support `CardAction` types not listed in the previous table.</span></span>
>* <span data-ttu-id="c1be9-118">Teams unterstützt die Eigenschaft `potentialActions` nicht.</span><span class="sxs-lookup"><span data-stu-id="c1be9-118">Teams does not support the `potentialActions` property.</span></span>
>* <span data-ttu-id="c1be9-119">Kartenaktionen unterscheiden sich von [den vorgeschlagenen Aktionen](/azure/bot-service/bot-builder-howto-add-suggested-actions?view=azure-bot-service-4.0&tabs=javascript#suggest-action-using-button&preserve-view=true) in Bot Framework oder Azure Bot Service.</span><span class="sxs-lookup"><span data-stu-id="c1be9-119">Card actions are different than [suggested actions](/azure/bot-service/bot-builder-howto-add-suggested-actions?view=azure-bot-service-4.0&tabs=javascript#suggest-action-using-button&preserve-view=true) in Bot Framework or Azure Bot Service.</span></span> <span data-ttu-id="c1be9-120">Vorgeschlagene Aktionen werden in Microsoft Teams nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c1be9-120">Suggested actions are not supported in Microsoft Teams.</span></span> <span data-ttu-id="c1be9-121">Wenn Schaltflächen in einer Teams Bot-Nachricht angezeigt werden sollen, verwenden Sie eine Karte.</span><span class="sxs-lookup"><span data-stu-id="c1be9-121">If you want buttons to appear on a Teams bot message, use a card.</span></span>
>* <span data-ttu-id="c1be9-122">Wenn Sie eine Kartenaktion als Teil einer Messaging-Erweiterung verwenden, funktionieren die Aktionen erst, wenn die Karte an den Kanal übermittelt wird.</span><span class="sxs-lookup"><span data-stu-id="c1be9-122">If you are using a card action as part of a messaging extension, the actions do not work until the card is submitted to the channel.</span></span> <span data-ttu-id="c1be9-123">Die Aktionen funktionieren nicht, während sich die Karte im Feld zum Verfassen von Nachrichten befindet.</span><span class="sxs-lookup"><span data-stu-id="c1be9-123">The actions do not work while the card is in the compose message box.</span></span>

## <a name="action-type-openurl"></a><span data-ttu-id="c1be9-124">Aktionstyp "openUrl"</span><span class="sxs-lookup"><span data-stu-id="c1be9-124">Action type openUrl</span></span>

<span data-ttu-id="c1be9-125">`openUrl` der Aktionstyp gibt eine URL an, die im Standardbrowser gestartet werden soll.</span><span class="sxs-lookup"><span data-stu-id="c1be9-125">`openUrl` action type specifies a URL to launch in the default browser.</span></span>

> [!NOTE]
> <span data-ttu-id="c1be9-126">Ihr Bot erhält keine Benachrichtigung darüber, welche Schaltfläche ausgewählt wurde.</span><span class="sxs-lookup"><span data-stu-id="c1be9-126">Your bot does not receive any notice on which button was selected.</span></span>

<span data-ttu-id="c1be9-127">Mit `openUrl` können Sie eine Aktion mit den folgenden Eigenschaften erstellen:</span><span class="sxs-lookup"><span data-stu-id="c1be9-127">With `openUrl`, you can create an action with the following properties:</span></span>

| <span data-ttu-id="c1be9-128">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="c1be9-128">Property</span></span> | <span data-ttu-id="c1be9-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c1be9-129">Description</span></span> |
| --- | --- |
| `title` | <span data-ttu-id="c1be9-130">Wird als Schaltflächenbeschriftung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c1be9-130">Appears as the button label.</span></span> |
| `value` | <span data-ttu-id="c1be9-131">Dieses Feld muss eine vollständige und ordnungsgemäß gebildete URL enthalten.</span><span class="sxs-lookup"><span data-stu-id="c1be9-131">This field must contain a full and properly formed URL.</span></span> |

# <a name="json"></a>[<span data-ttu-id="c1be9-132">Json</span><span class="sxs-lookup"><span data-stu-id="c1be9-132">JSON</span></span>](#tab/json)

<span data-ttu-id="c1be9-133">Der folgende Code zeigt ein Beispiel für den `openUrl` Aktionstyp in JSON:</span><span class="sxs-lookup"><span data-stu-id="c1be9-133">The following code shows an example of `openUrl` action type in JSON:</span></span>

```json
{
    "type": "openUrl",
    "title": "Tabs in Teams",
    "value": "https://msdn.microsoft.com/microsoft-teams/tabs"
}
```

# <a name="c"></a>[<span data-ttu-id="c1be9-134">C#</span><span class="sxs-lookup"><span data-stu-id="c1be9-134">C#</span></span>](#tab/csharp)

<span data-ttu-id="c1be9-135">Der folgende Code zeigt ein Beispiel für den `openUrl` Aktionstyp in C#:</span><span class="sxs-lookup"><span data-stu-id="c1be9-135">The following code shows an example of `openUrl` action type in C#:</span></span>

```csharp
var button = new CardAction()
{
    Type = ActionTypes.OpenUrl,
    Title = "Tabs in Teams",
    Value = "https://docs.microsoft.com/en-us/microsoftteams/platform/"
};
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="c1be9-136">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="c1be9-136">JavaScript/Node.js</span></span>](#tab/javascript)

<span data-ttu-id="c1be9-137">Der folgende Code zeigt ein Beispiel für den `openUrl` Aktionstyp in JavaScript:</span><span class="sxs-lookup"><span data-stu-id="c1be9-137">The following code shows an example of `openUrl` action type in JavaScript:</span></span>

```javascript
CardFactory.actions([
{
    type: 'openUrl',
    title: 'Tabs in Teams',
    value: 'https://docs.microsoft.com/en-us/microsoftteams/platform/'
}])
```

---

## <a name="action-type-messageback"></a><span data-ttu-id="c1be9-138">MessageBack des Aktionstyps</span><span class="sxs-lookup"><span data-stu-id="c1be9-138">Action type messageBack</span></span>

<span data-ttu-id="c1be9-139">Mit `messageBack` können Sie eine vollständig angepasste Aktion mit den folgenden Eigenschaften erstellen:</span><span class="sxs-lookup"><span data-stu-id="c1be9-139">With `messageBack`, you can create a fully customized action with the following properties:</span></span>

| <span data-ttu-id="c1be9-140">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="c1be9-140">Property</span></span> | <span data-ttu-id="c1be9-141">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c1be9-141">Description</span></span> |
| --- | --- |
| `title` | <span data-ttu-id="c1be9-142">Wird als Schaltflächenbeschriftung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c1be9-142">Appears as the button label.</span></span> |
| `displayText` | <span data-ttu-id="c1be9-143">Optional.</span><span class="sxs-lookup"><span data-stu-id="c1be9-143">Optional.</span></span> <span data-ttu-id="c1be9-144">Wird vom Benutzer im Chatdatenstrom verwendet, wenn die Aktion ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c1be9-144">Used by the user in the chat stream when the action is performed.</span></span> <span data-ttu-id="c1be9-145">Dieser Text wird nicht an Ihren Bot gesendet.</span><span class="sxs-lookup"><span data-stu-id="c1be9-145">This text is not sent to your bot.</span></span> |
| `value` | <span data-ttu-id="c1be9-146">Wird an Ihren Bot gesendet, wenn die Aktion ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c1be9-146">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="c1be9-147">Sie können den Kontext für die Aktion codieren, z. B. eindeutige Bezeichner oder ein JSON-Objekt.</span><span class="sxs-lookup"><span data-stu-id="c1be9-147">You can encode context for the action, such as unique identifiers or a JSON object.</span></span> |
| `text` | <span data-ttu-id="c1be9-148">Wird an Ihren Bot gesendet, wenn die Aktion ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c1be9-148">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="c1be9-149">Verwenden Sie diese Eigenschaft, um die Bot-Entwicklung zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="c1be9-149">Use this property to simplify bot development.</span></span> <span data-ttu-id="c1be9-150">Ihr Code kann eine einzelne Eigenschaft der obersten Ebene überprüfen, um Botlogik zu verteilen.</span><span class="sxs-lookup"><span data-stu-id="c1be9-150">Your code can check a single top-level property to dispatch bot logic.</span></span> |

<span data-ttu-id="c1be9-151">Die Flexibilität `messageBack` bedeutet, dass Ihr Code keine sichtbare Benutzernachricht im Verlauf belassen kann, indem er einfach nicht verwendet `displayText` wird.</span><span class="sxs-lookup"><span data-stu-id="c1be9-151">The flexibility of `messageBack` means that your code cannot leave a visible user message in the history simply by not using `displayText`.</span></span>

# <a name="json"></a>[<span data-ttu-id="c1be9-152">Json</span><span class="sxs-lookup"><span data-stu-id="c1be9-152">JSON</span></span>](#tab/json)

<span data-ttu-id="c1be9-153">Der folgende Code zeigt ein Beispiel für den `messageBack` Aktionstyp in JSON:</span><span class="sxs-lookup"><span data-stu-id="c1be9-153">The following code shows an example of `messageBack` action type in JSON:</span></span>

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

<span data-ttu-id="c1be9-154">Die `value` Eigenschaft kann eine serialisierte JSON-Zeichenfolge oder ein JSON-Objekt sein.</span><span class="sxs-lookup"><span data-stu-id="c1be9-154">The `value` property can be either a serialized JSON string or a JSON object.</span></span>

# <a name="c"></a>[<span data-ttu-id="c1be9-155">C#</span><span class="sxs-lookup"><span data-stu-id="c1be9-155">C#</span></span>](#tab/csharp)

<span data-ttu-id="c1be9-156">Der folgende Code zeigt ein Beispiel für den `messageBack` Aktionstyp in C#:</span><span class="sxs-lookup"><span data-stu-id="c1be9-156">The following code shows an example of `messageBack` action type in C#:</span></span>

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

# <a name="javascriptnodejs"></a>[<span data-ttu-id="c1be9-157">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="c1be9-157">JavaScript/Node.js</span></span>](#tab/javascript)

<span data-ttu-id="c1be9-158">Der folgende Code zeigt ein Beispiel für den `messageBack` Aktionstyp in JavaScript:</span><span class="sxs-lookup"><span data-stu-id="c1be9-158">The following code shows an example of `messageBack` action type in JavaScript:</span></span>

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

### <a name="inbound-message-example"></a><span data-ttu-id="c1be9-159">Beispiel für eingehende Nachrichten</span><span class="sxs-lookup"><span data-stu-id="c1be9-159">Inbound message example</span></span>

<span data-ttu-id="c1be9-160">`replyToId` enthält die ID der Nachricht, aus der die Kartenaktion stammt.</span><span class="sxs-lookup"><span data-stu-id="c1be9-160">`replyToId` contains the ID of the message that the card action came from.</span></span> <span data-ttu-id="c1be9-161">Verwenden Sie sie, wenn Sie die Nachricht aktualisieren möchten.</span><span class="sxs-lookup"><span data-stu-id="c1be9-161">Use it if you want to update the message.</span></span>

<span data-ttu-id="c1be9-162">Der folgende Code zeigt ein Beispiel für eingehende Nachrichten:</span><span class="sxs-lookup"><span data-stu-id="c1be9-162">The following code shows an example of inbound message:</span></span>

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

## <a name="action-type-imback"></a><span data-ttu-id="c1be9-163">Aktionstyp imBack</span><span class="sxs-lookup"><span data-stu-id="c1be9-163">Action type imBack</span></span>

<span data-ttu-id="c1be9-164">Die `imBack` Aktion löst eine Rückgabenachricht an Ihren Bot aus, als ob der Benutzer sie in eine normale Chatnachricht eingegeben hätte.</span><span class="sxs-lookup"><span data-stu-id="c1be9-164">The `imBack` action triggers a return message to your bot, as if the user typed it in a normal chat message.</span></span> <span data-ttu-id="c1be9-165">Der Benutzer und alle anderen Benutzer in einem Kanal können die Schaltflächenantwort sehen.</span><span class="sxs-lookup"><span data-stu-id="c1be9-165">Your user and all other users in a channel can see the button response.</span></span>

<span data-ttu-id="c1be9-166">Mit `imBack` können Sie eine Aktion mit den folgenden Eigenschaften erstellen:</span><span class="sxs-lookup"><span data-stu-id="c1be9-166">With `imBack`, you can create an action with the following properties:</span></span>

| <span data-ttu-id="c1be9-167">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="c1be9-167">Property</span></span> | <span data-ttu-id="c1be9-168">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c1be9-168">Description</span></span> |
| --- | --- |
| `title` | <span data-ttu-id="c1be9-169">Wird als Schaltflächenbeschriftung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c1be9-169">Appears as the button label.</span></span> |
| `value` | <span data-ttu-id="c1be9-170">Dieses Feld muss die im Chat verwendete Textzeichenfolge enthalten und daher an den Bot zurücksandt.</span><span class="sxs-lookup"><span data-stu-id="c1be9-170">This field must contain the text string used in the chat and therefore sent back to the bot.</span></span> <span data-ttu-id="c1be9-171">Dies ist der Nachrichtentext, den Sie in Ihrem Bot verarbeiten, um die gewünschte Logik auszuführen.</span><span class="sxs-lookup"><span data-stu-id="c1be9-171">This is the message text you process in your bot to perform the desired logic.</span></span> |

> [!NOTE]
> <span data-ttu-id="c1be9-172">Das `value` Feld ist eine einfache Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="c1be9-172">The `value` field is a simple string.</span></span> <span data-ttu-id="c1be9-173">Formatierungen oder ausgeblendete Zeichen werden nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c1be9-173">There is no support for formatting or hidden characters.</span></span>

# <a name="json"></a>[<span data-ttu-id="c1be9-174">Json</span><span class="sxs-lookup"><span data-stu-id="c1be9-174">JSON</span></span>](#tab/json)

<span data-ttu-id="c1be9-175">Der folgende Code zeigt ein Beispiel für den `imBack` Aktionstyp in JSON:</span><span class="sxs-lookup"><span data-stu-id="c1be9-175">The following code shows an example of `imBack` action type in JSON:</span></span>

```json
{
    "type": "imBack",
    "title": "More",
    "value": "Show me more"
}
```

# <a name="c"></a>[<span data-ttu-id="c1be9-176">C#</span><span class="sxs-lookup"><span data-stu-id="c1be9-176">C#</span></span>](#tab/csharp)

<span data-ttu-id="c1be9-177">Der folgende Code zeigt ein Beispiel für den `imBack` Aktionstyp in C#:</span><span class="sxs-lookup"><span data-stu-id="c1be9-177">The following code shows an example of `imBack` action type in C#:</span></span>

```csharp
var button = new CardAction()
{
    Type = ActionTypes.ImBack,
    Title = "More",
    Value = "Show me more"
};
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="c1be9-178">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="c1be9-178">JavaScript/Node.js</span></span>](#tab/javascript)

<span data-ttu-id="c1be9-179">Der folgende Code zeigt ein Beispiel für den `imBack` Aktionstyp in JavaScript:</span><span class="sxs-lookup"><span data-stu-id="c1be9-179">The following code shows an example of `imBack` action type in JavaScript:</span></span>

```javascript
CardFactory.actions([
{
    type: "imBack",
    title: "More",
    value: "Show me more"
}])
```

---

## <a name="action-type-invoke"></a><span data-ttu-id="c1be9-180">Aufrufen des Aktionstyps</span><span class="sxs-lookup"><span data-stu-id="c1be9-180">Action type invoke</span></span>

<span data-ttu-id="c1be9-181">Die `invoke` Aktion wird zum Aufrufen von [Aufgabenmodulen](~/task-modules-and-cards/task-modules/task-modules-bots.md)verwendet.</span><span class="sxs-lookup"><span data-stu-id="c1be9-181">The `invoke` action is used for invoking [task modules](~/task-modules-and-cards/task-modules/task-modules-bots.md).</span></span>

<span data-ttu-id="c1be9-182">Die `invoke` Aktion enthält drei Eigenschaften, und `type` `title` `value` .</span><span class="sxs-lookup"><span data-stu-id="c1be9-182">The `invoke` action contains three properties, `type`, `title`, and `value`.</span></span>

<span data-ttu-id="c1be9-183">Mit `invoke` können Sie eine Aktion mit den folgenden Eigenschaften erstellen:</span><span class="sxs-lookup"><span data-stu-id="c1be9-183">With `invoke`, you can create an action with the following properties:</span></span>

| <span data-ttu-id="c1be9-184">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="c1be9-184">Property</span></span> | <span data-ttu-id="c1be9-185">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c1be9-185">Description</span></span> |
| --- | --- |
| `title` | <span data-ttu-id="c1be9-186">Wird als Schaltflächenbeschriftung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c1be9-186">Appears as the button label.</span></span> |
| `value` | <span data-ttu-id="c1be9-187">Diese Eigenschaft kann eine Zeichenfolge, ein JSON-Objekt mit Zeichenfolge oder ein JSON-Objekt enthalten.</span><span class="sxs-lookup"><span data-stu-id="c1be9-187">This property can contain a string, a stringified JSON object, or a JSON object.</span></span> |

# <a name="json"></a>[<span data-ttu-id="c1be9-188">Json</span><span class="sxs-lookup"><span data-stu-id="c1be9-188">JSON</span></span>](#tab/json)

<span data-ttu-id="c1be9-189">Der folgende Code zeigt ein Beispiel für den `invoke` Aktionstyp in JSON:</span><span class="sxs-lookup"><span data-stu-id="c1be9-189">The following code shows an example of `invoke` action type in JSON:</span></span>

```json
{
    "type": "invoke",
    "title": "Option 1",
    "value": {
        "option": "opt1"
    }
}
```

<span data-ttu-id="c1be9-190">Wenn ein Benutzer die Schaltfläche auswählt, empfängt Ihr Bot das `value` Objekt mit einigen zusätzlichen Informationen.</span><span class="sxs-lookup"><span data-stu-id="c1be9-190">When a user selects the button, your bot receives the `value` object with some additional information.</span></span>

> [!NOTE]
> <span data-ttu-id="c1be9-191">Der `invoke` Aktivitätstyp ist `message` stattdessen `activity.Type == "invoke"` .</span><span class="sxs-lookup"><span data-stu-id="c1be9-191">The activity type is `invoke` instead of `message` that is `activity.Type == "invoke"`.</span></span>

# <a name="c"></a>[<span data-ttu-id="c1be9-192">C#</span><span class="sxs-lookup"><span data-stu-id="c1be9-192">C#</span></span>](#tab/csharp)

<span data-ttu-id="c1be9-193">Der folgende Code zeigt ein Beispiel für den `invoke` Aktionstyp in C#:</span><span class="sxs-lookup"><span data-stu-id="c1be9-193">The following code shows an example of `invoke` action type in C#:</span></span>

```csharp
var button = new CardAction()
{
    Title = "Option 1",
    Type = "invoke",
    Value = "{\"option\": \"opt1\"}"
};
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="c1be9-194">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="c1be9-194">JavaScript/Node.js</span></span>](#tab/javascript)

<span data-ttu-id="c1be9-195">Der folgende Code zeigt ein Beispiel für den `invoke` Aktionstyp in Node.js:</span><span class="sxs-lookup"><span data-stu-id="c1be9-195">The following code shows an example of `invoke` action type in Node.js:</span></span>

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

### <a name="example-of-incoming-invoke-message"></a><span data-ttu-id="c1be9-196">Beispiel für eingehende Aufrufnachricht</span><span class="sxs-lookup"><span data-stu-id="c1be9-196">Example of incoming invoke message</span></span>

<span data-ttu-id="c1be9-197">Die Eigenschaft der obersten Ebene `replyToId` enthält die ID der Nachricht, aus der die Kartenaktion stammt.</span><span class="sxs-lookup"><span data-stu-id="c1be9-197">The top-level `replyToId` property contains the ID of the message that the card action came from.</span></span> <span data-ttu-id="c1be9-198">Verwenden Sie sie, wenn Sie die Nachricht aktualisieren möchten.</span><span class="sxs-lookup"><span data-stu-id="c1be9-198">Use it if you want to update the message.</span></span>

<span data-ttu-id="c1be9-199">Der folgende Code zeigt ein Beispiel für eine eingehende Aufrufnachricht:</span><span class="sxs-lookup"><span data-stu-id="c1be9-199">The following code shows an example of incoming invoke message:</span></span>

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

## <a name="action-type-signin"></a><span data-ttu-id="c1be9-200">Signin des Aktionstyps</span><span class="sxs-lookup"><span data-stu-id="c1be9-200">Action type signin</span></span>

<span data-ttu-id="c1be9-201">`signin` Der Aktionstyp initiiert einen OAuth-Fluss, der bots die Verbindung mit sicheren Diensten ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="c1be9-201">`signin` action type initiates an OAuth flow that permits bots to connect with secure services.</span></span> <span data-ttu-id="c1be9-202">Weitere Informationen finden Sie unter [Authentifizierungsfluss in Bots.](~/bots/how-to/authentication/auth-flow-bot.md)</span><span class="sxs-lookup"><span data-stu-id="c1be9-202">For more information, see [authentication flow in bots](~/bots/how-to/authentication/auth-flow-bot.md).</span></span>

<span data-ttu-id="c1be9-203">Teams unterstützt auch [Adaptive Kartenaktionen,](#adaptive-cards-actions) die nur von adaptiven Karten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c1be9-203">Teams also supports [Adaptive Cards actions](#adaptive-cards-actions) that are only used by Adaptive Cards.</span></span>

# <a name="json"></a>[<span data-ttu-id="c1be9-204">Json</span><span class="sxs-lookup"><span data-stu-id="c1be9-204">JSON</span></span>](#tab/json)

<span data-ttu-id="c1be9-205">Der folgende Code zeigt ein Beispiel für den `signin` Aktionstyp in JSON:</span><span class="sxs-lookup"><span data-stu-id="c1be9-205">The following code shows an example of `signin` action type in JSON:</span></span>

```json
{
"type": "signin",
"title": "Click me for signin",
"value": "https://signin.com"
}
```

# <a name="c"></a>[<span data-ttu-id="c1be9-206">C#</span><span class="sxs-lookup"><span data-stu-id="c1be9-206">C#</span></span>](#tab/csharp)

<span data-ttu-id="c1be9-207">Der folgende Code zeigt ein Beispiel für den `signin` Aktionstyp in C#:</span><span class="sxs-lookup"><span data-stu-id="c1be9-207">The following code shows an example of `signin` action type in C#:</span></span>

```csharp
var button = new CardAction()
{
    Type = ActionTypes.Signin,
    Title = "Click me for signin",
    Value = "https://signin.com"
};
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="c1be9-208">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="c1be9-208">JavaScript/Node.js</span></span>](#tab/javascript)

<span data-ttu-id="c1be9-209">Der folgende Code zeigt ein Beispiel für den `signin` Aktionstyp in JavaScript:</span><span class="sxs-lookup"><span data-stu-id="c1be9-209">The following code shows an example of `signin` action type in JavaScript:</span></span>

```javascript
CardFactory.actions([
{
    type: "signin",
    title: "Click me for signin",
    value: "https://signin.com"
}])
```

---

## <a name="adaptive-cards-actions"></a><span data-ttu-id="c1be9-210">Aktionen für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="c1be9-210">Adaptive Cards actions</span></span>

<span data-ttu-id="c1be9-211">Adaptive Karten unterstützen vier Aktionstypen:</span><span class="sxs-lookup"><span data-stu-id="c1be9-211">Adaptive Cards support four action types:</span></span>

* [<span data-ttu-id="c1be9-212">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="c1be9-212">Action.OpenUrl</span></span>](http://adaptivecards.io/explorer/Action.OpenUrl.html)
* [<span data-ttu-id="c1be9-213">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="c1be9-213">Action.Submit</span></span>](http://adaptivecards.io/explorer/Action.Submit.html)
* [<span data-ttu-id="c1be9-214">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="c1be9-214">Action.ShowCard</span></span>](http://adaptivecards.io/explorer/Action.ShowCard.html)
* [<span data-ttu-id="c1be9-215">Action.Exeniedlich</span><span class="sxs-lookup"><span data-stu-id="c1be9-215">Action.Execute</span></span>](/adaptive-cards/authoring-cards/universal-action-model#actionexecute)

<span data-ttu-id="c1be9-216">Sie können auch die Nutzlast der adaptiven Karte `Action.Submit` ändern, um vorhandene Bot Framework-Aktionen mithilfe einer Eigenschaft im Objekt von zu `msteams` `data` `Action.Submit` unterstützen.</span><span class="sxs-lookup"><span data-stu-id="c1be9-216">You can also modify the Adaptive Card `Action.Submit` payload to support existing Bot Framework actions using an `msteams` property in the `data` object of `Action.Submit`.</span></span> <span data-ttu-id="c1be9-217">Der nächste Abschnitt enthält Details zur Verwendung vorhandener Bot Framework-Aktionen mit adaptiven Karten.</span><span class="sxs-lookup"><span data-stu-id="c1be9-217">The next section provide details on how to use existing Bot Framework actions with Adaptive Cards.</span></span>

> [!NOTE]
> <span data-ttu-id="c1be9-218">Das Hinzufügen `msteams` zu Daten mit einer Bot Framework-Aktion funktioniert nicht mit einem Aufgabenmodul für adaptive Karten.</span><span class="sxs-lookup"><span data-stu-id="c1be9-218">Adding `msteams` to data with a Bot Framework action does not work with an Adaptive Card task module.</span></span>

### <a name="adaptive-cards-with-messageback-action"></a><span data-ttu-id="c1be9-219">Adaptive Karten mit messageBack-Aktion</span><span class="sxs-lookup"><span data-stu-id="c1be9-219">Adaptive Cards with messageBack action</span></span>

<span data-ttu-id="c1be9-220">Um eine `messageBack` Aktion in eine adaptive Karte einzuschließen, fügen Sie die folgenden Details in das Objekt `msteams` ein:</span><span class="sxs-lookup"><span data-stu-id="c1be9-220">To include a `messageBack` action with an Adaptive Card include the following details in the `msteams` object:</span></span>

> [!NOTE]
> <span data-ttu-id="c1be9-221">Sie können zusätzliche ausgeblendete Eigenschaften in das `data` Objekt einschließen, falls erforderlich.</span><span class="sxs-lookup"><span data-stu-id="c1be9-221">You can include additional hidden properties in the `data` object, if required.</span></span>

| <span data-ttu-id="c1be9-222">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="c1be9-222">Property</span></span> | <span data-ttu-id="c1be9-223">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c1be9-223">Description</span></span> |
| --- | --- |
| `type` | <span data-ttu-id="c1be9-224">Festgelegt auf `messageBack` .</span><span class="sxs-lookup"><span data-stu-id="c1be9-224">Set to `messageBack`.</span></span> |
| `displayText` | <span data-ttu-id="c1be9-225">Optional.</span><span class="sxs-lookup"><span data-stu-id="c1be9-225">Optional.</span></span> <span data-ttu-id="c1be9-226">Wird vom Benutzer im Chatdatenstrom verwendet, wenn die Aktion ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c1be9-226">Used by the user in the chat stream when the action is performed.</span></span> <span data-ttu-id="c1be9-227">Dieser Text wird nicht an Ihren Bot gesendet.</span><span class="sxs-lookup"><span data-stu-id="c1be9-227">This text is not sent to your bot.</span></span> |
| `value` | <span data-ttu-id="c1be9-228">Wird an Ihren Bot gesendet, wenn die Aktion ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c1be9-228">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="c1be9-229">Sie können den Kontext für die Aktion codieren, z. B. eindeutige Bezeichner oder ein JSON-Objekt.</span><span class="sxs-lookup"><span data-stu-id="c1be9-229">You can encode context for the action, such as unique identifiers or a JSON object.</span></span> |
| `text` | <span data-ttu-id="c1be9-230">Wird an Ihren Bot gesendet, wenn die Aktion ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c1be9-230">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="c1be9-231">Verwenden Sie diese Eigenschaft, um die Bot-Entwicklung zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="c1be9-231">Use this property to simplify bot development.</span></span> <span data-ttu-id="c1be9-232">Ihr Code kann eine einzelne Eigenschaft der obersten Ebene überprüfen, um Botlogik zu verteilen.</span><span class="sxs-lookup"><span data-stu-id="c1be9-232">Your code can check a single top-level property to dispatch bot logic.</span></span> |

<span data-ttu-id="c1be9-233">Der folgende Code zeigt ein Beispiel für adaptive Karten mit `messageBack` Aktion:</span><span class="sxs-lookup"><span data-stu-id="c1be9-233">The following code shows an example of Adaptive Cards with `messageBack` action:</span></span>

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

### <a name="adaptive-cards-with-imback-action"></a><span data-ttu-id="c1be9-234">Adaptive Karten mit imBack-Aktion</span><span class="sxs-lookup"><span data-stu-id="c1be9-234">Adaptive Cards with imBack action</span></span>

<span data-ttu-id="c1be9-235">Um eine `imBack` Aktion in eine adaptive Karte einzuschließen, fügen Sie die folgenden Details in das Objekt `msteams` ein:</span><span class="sxs-lookup"><span data-stu-id="c1be9-235">To include an `imBack` action with an Adaptive Card include the following details in the `msteams` object:</span></span>

> [!NOTE]
> <span data-ttu-id="c1be9-236">Sie können zusätzliche ausgeblendete Eigenschaften in das `data` Objekt einschließen, falls erforderlich.</span><span class="sxs-lookup"><span data-stu-id="c1be9-236">You can include additional hidden properties in the `data` object, if required.</span></span>

| <span data-ttu-id="c1be9-237">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="c1be9-237">Property</span></span> | <span data-ttu-id="c1be9-238">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c1be9-238">Description</span></span> |
| --- | --- |
| `type` | <span data-ttu-id="c1be9-239">Festgelegt auf `imBack` .</span><span class="sxs-lookup"><span data-stu-id="c1be9-239">Set to `imBack`.</span></span> |
| `value` | <span data-ttu-id="c1be9-240">Zeichenfolge, die im Chat wiederholt werden muss.</span><span class="sxs-lookup"><span data-stu-id="c1be9-240">String that needs to be echoed back in the chat.</span></span> |

<span data-ttu-id="c1be9-241">Der folgende Code zeigt ein Beispiel für adaptive Karten mit `imBack` Aktion:</span><span class="sxs-lookup"><span data-stu-id="c1be9-241">The following code shows an example of Adaptive Cards with `imBack` action:</span></span>

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

### <a name="adaptive-cards-with-signin-action"></a><span data-ttu-id="c1be9-242">Adaptive Karten mit Anmeldeaktion</span><span class="sxs-lookup"><span data-stu-id="c1be9-242">Adaptive Cards with signin action</span></span>

<span data-ttu-id="c1be9-243">Um eine `signin` Aktion in eine adaptive Karte einzuschließen, fügen Sie die folgenden Details in das Objekt `msteams` ein:</span><span class="sxs-lookup"><span data-stu-id="c1be9-243">To include a `signin` action with an Adaptive Card include the following details in the `msteams` object:</span></span>

> [!NOTE]
> <span data-ttu-id="c1be9-244">Sie können zusätzliche ausgeblendete Eigenschaften in das `data` Objekt einschließen, falls erforderlich.</span><span class="sxs-lookup"><span data-stu-id="c1be9-244">You can include additional hidden properties in the `data` object, if required.</span></span>

| <span data-ttu-id="c1be9-245">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="c1be9-245">Property</span></span> | <span data-ttu-id="c1be9-246">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c1be9-246">Description</span></span> |
| --- | --- |
| `type` | <span data-ttu-id="c1be9-247">Festgelegt auf `signin` .</span><span class="sxs-lookup"><span data-stu-id="c1be9-247">Set to `signin`.</span></span> |
| `value` | <span data-ttu-id="c1be9-248">Legen Sie die URL fest, an die Sie umleiten möchten.</span><span class="sxs-lookup"><span data-stu-id="c1be9-248">Set to the URL where you want to redirect.</span></span>  |

<span data-ttu-id="c1be9-249">Der folgende Code zeigt ein Beispiel für adaptive Karten mit `signin` Aktion:</span><span class="sxs-lookup"><span data-stu-id="c1be9-249">The following code shows an example of Adaptive Cards with `signin` action:</span></span>

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

### <a name="adaptive-cards-with-invoke-action"></a><span data-ttu-id="c1be9-250">Adaptive Karten mit Aufrufaktion</span><span class="sxs-lookup"><span data-stu-id="c1be9-250">Adaptive Cards with invoke action</span></span>

<span data-ttu-id="c1be9-251">Um eine `invoke` Aktion in eine adaptive Karte einzuschließen, fügen Sie die folgenden Details in das Objekt `msteams` ein:</span><span class="sxs-lookup"><span data-stu-id="c1be9-251">To include an `invoke` action with an Adaptive Card include the following details in the `msteams` object:</span></span>

> [!NOTE]
> <span data-ttu-id="c1be9-252">Sie können zusätzliche ausgeblendete Eigenschaften in das `data` Objekt einschließen, falls erforderlich.</span><span class="sxs-lookup"><span data-stu-id="c1be9-252">You can include additional hidden properties in the `data` object, if required.</span></span>

| <span data-ttu-id="c1be9-253">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="c1be9-253">Property</span></span> | <span data-ttu-id="c1be9-254">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c1be9-254">Description</span></span> |
| --- | --- |
| `type` | <span data-ttu-id="c1be9-255">Festgelegt auf `task/fetch` .</span><span class="sxs-lookup"><span data-stu-id="c1be9-255">Set to `task/fetch`.</span></span> |
| `data` | <span data-ttu-id="c1be9-256">Legen Sie den Wert fest.</span><span class="sxs-lookup"><span data-stu-id="c1be9-256">Set the value.</span></span>  |

<span data-ttu-id="c1be9-257">Der folgende Code zeigt ein Beispiel für adaptive Karten mit `invoke` Aktion:</span><span class="sxs-lookup"><span data-stu-id="c1be9-257">The following code shows an example of Adaptive Cards with `invoke` action:</span></span>

```json
{
  "type": "Action.Submit",
  "title": "submit",
  "data": {
    "msteams": {
        "type": "task/fetch"
    }
  }
}
```

<span data-ttu-id="c1be9-258">Der folgende Code zeigt ein Beispiel für adaptive Karten mit `invoke` Aktion mit zusätzlichen Nutzlastdaten:</span><span class="sxs-lookup"><span data-stu-id="c1be9-258">The following code shows an example of Adaptive Cards with `invoke` action with additional payload data:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c1be9-259">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="c1be9-259">See also</span></span>

[<span data-ttu-id="c1be9-260">Karten-Referenz</span><span class="sxs-lookup"><span data-stu-id="c1be9-260">Cards reference</span></span>](./cards-reference.md)

## <a name="next-step"></a><span data-ttu-id="c1be9-261">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="c1be9-261">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c1be9-262">Universal-Aktionen für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="c1be9-262">Universal Actions for Adaptive Cards</span></span>](../cards/Universal-actions-for-adaptive-cards/Overview.md)
