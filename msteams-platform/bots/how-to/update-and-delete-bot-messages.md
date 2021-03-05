---
title: Aktualisieren und Löschen von Nachrichten, die von Ihrem Bot gesendet werden
author: WashingtonKayaker
description: Aktualisieren und Löschen von Nachrichten, die von Ihrem Microsoft Teams-Bot gesendet werden
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 664bd531bdee0093c6766bc23e35d2bf10307eb4
ms.sourcegitcommit: 5cb3453e918bec1173899e7591b48a48113cf8f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2021
ms.locfileid: "50449500"
---
# <a name="update-and-delete-messages-sent-from-your-bot"></a><span data-ttu-id="4c8d3-103">Aktualisieren und Löschen von Nachrichten, die von Ihrem Bot gesendet werden</span><span class="sxs-lookup"><span data-stu-id="4c8d3-103">Update and delete messages sent from your bot</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

## <a name="update-messages"></a><span data-ttu-id="4c8d3-104">Nachricht aktualisieren</span><span class="sxs-lookup"><span data-stu-id="4c8d3-104">Update messages</span></span>

<span data-ttu-id="4c8d3-105">Ihr Bot kann Nachrichten nach dem Senden dynamisch aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="4c8d3-105">Your bot can dynamically update messages after sending them.</span></span> <span data-ttu-id="4c8d3-106">Sie können dynamische Nachrichtenupdates für Szenarien wie Abrufupdates, Ändern verfügbarer Aktionen nach dem Drücken einer Schaltfläche oder andere asynchrone Zustandsänderung verwenden.</span><span class="sxs-lookup"><span data-stu-id="4c8d3-106">You can use dynamic message updates for scenarios such as poll updates, modifying available actions after a button press, or any other asynchronous state change.</span></span>

<span data-ttu-id="4c8d3-107">Die neue Nachricht muss nicht mit dem ursprünglichen Typ übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="4c8d3-107">The new message need not match the original in type.</span></span> <span data-ttu-id="4c8d3-108">Wenn die ursprüngliche Nachricht beispielsweise eine Anlage enthielt, kann die neue Nachricht eine einfache Textnachricht sein.</span><span class="sxs-lookup"><span data-stu-id="4c8d3-108">For example, if the original message contained an attachment, the new message can be a simple text message.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="4c8d3-109">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="4c8d3-109">C#/.NET</span></span>](#tab/dotnet)

<span data-ttu-id="4c8d3-110">Um eine vorhandene Nachricht zu aktualisieren, übergeben Sie ein neues Objekt mit der vorhandenen `Activity` Aktivitäts-ID an die `UpdateActivityAsync` -Methode der `TurnContext` Klasse.</span><span class="sxs-lookup"><span data-stu-id="4c8d3-110">To update an existing message, pass a new `Activity` object with the existing activity ID to the `UpdateActivityAsync` method of the `TurnContext` class.</span></span> <span data-ttu-id="4c8d3-111">Weitere [Informationen finden Sie unter TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="4c8d3-111">See [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable&preserve-view=true).</span></span>

```csharp
var newActivity = MessageFactory.Text("The new text for the activity");
newActivity.Id = activityId;
await turnContext.UpdateActivityAsync(newActivity, cancellationToken);
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="4c8d3-112">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="4c8d3-112">TypeScript/Node.js</span></span>](#tab/typescript)

<span data-ttu-id="4c8d3-113">Um eine vorhandene Nachricht zu aktualisieren, übergeben Sie ein neues Objekt mit der vorhandenen Aktivitäts-ID `Activity` an die `updateActivity` -Methode des `TurnContext` Objekts.</span><span class="sxs-lookup"><span data-stu-id="4c8d3-113">To update an existing message, pass a new `Activity` object with the existing activity ID to the `updateActivity` method of the `TurnContext` object.</span></span> <span data-ttu-id="4c8d3-114">Weitere [Informationen finden Sie unter updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="4c8d3-114">See [updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--&preserve-view=true).</span></span>

```typescript
const newActivity = MessageFactory.text('The new text for the activity');
newActivity.id = activityId;
await turnContext.updateActivity(newActivity);
```

# <a name="python"></a>[<span data-ttu-id="4c8d3-115">Python</span><span class="sxs-lookup"><span data-stu-id="4c8d3-115">Python</span></span>](#tab/python)

<span data-ttu-id="4c8d3-116">Um eine vorhandene Nachricht zu aktualisieren, übergeben Sie ein neues Objekt mit der vorhandenen `Activity` Aktivitäts-ID an die `update_activity` -Methode der `TurnContext` Klasse.</span><span class="sxs-lookup"><span data-stu-id="4c8d3-116">To update an existing message, pass a new `Activity` object with the existing activity ID to the `update_activity` method of the `TurnContext` class.</span></span> <span data-ttu-id="4c8d3-117">Weitere [Informationen finden Sie unter TurnContextClass](/python/api/botbuilder-core/botbuilder.core.turncontext?view=botbuilder-py-latest).</span><span class="sxs-lookup"><span data-stu-id="4c8d3-117">See [TurnContextClass](/python/api/botbuilder-core/botbuilder.core.turncontext?view=botbuilder-py-latest).</span></span>

```python

new_activity = MessageFactory.text("The new text for the activity")
new_activity.id = activity_id
update_result = await context.update_activity(new_activity)

```

# <a name="rest-api"></a>[<span data-ttu-id="4c8d3-118">REST API</span><span class="sxs-lookup"><span data-stu-id="4c8d3-118">REST API</span></span>](#tab/rest)

>[!NOTE]
><span data-ttu-id="4c8d3-119">Sie können Teams-Apps in jeder beliebigen Webprogrammiertechnologie entwickeln und direkt die [Bot Connector-Dienst-REST-APIs aufrufen.](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="4c8d3-119">You can develop Teams apps in any web-programming technology and directly call the [Bot Connector service REST APIs](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span> <span data-ttu-id="4c8d3-120">Dazu müssen Sie Authentifizierungssicherheitsverfahren mit Ihren API-Anforderungen implementieren. [](/azure/bot-service/rest-api/bot-framework-rest-connector-authentication?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="4c8d3-120">To do so, you need to implement [Authentication](/azure/bot-service/rest-api/bot-framework-rest-connector-authentication?view=azure-bot-service-4.0&preserve-view=true) security procedures with your API requests.</span></span>

<span data-ttu-id="4c8d3-121">Um eine vorhandene Aktivität in einer Unterhaltung zu aktualisieren, schließen Sie `conversationId` das und in den `activityId` Anforderungsendpunkt ein.</span><span class="sxs-lookup"><span data-stu-id="4c8d3-121">To update an existing activity within a conversation, include the `conversationId` and `activityId` in the request endpoint.</span></span> <span data-ttu-id="4c8d3-122">Zum Abschließen dieses Szenarios müssen Sie die vom ursprünglichen POST-Aufruf zurückgegebene Aktivitäts-ID zwischenspeichern.</span><span class="sxs-lookup"><span data-stu-id="4c8d3-122">To complete this scenario, you must cache the activity ID returned by the original POST call.</span></span>

```http
PUT /v3/conversations/{conversationId}/activities/{activityId}
```

| | |
|----|----|
| <span data-ttu-id="4c8d3-123">**Anforderungstext**</span><span class="sxs-lookup"><span data-stu-id="4c8d3-123">**Request body**</span></span> | <span data-ttu-id="4c8d3-124">Ein [Activity-Objekt](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#activity-object&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="4c8d3-124">An [Activity](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#activity-object&preserve-view=true) object</span></span> |
| <span data-ttu-id="4c8d3-125">**gibt zurück**</span><span class="sxs-lookup"><span data-stu-id="4c8d3-125">**Returns**</span></span> | <span data-ttu-id="4c8d3-126">Ein [ResourceResponse-Objekt](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#resourceresponse-object&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="4c8d3-126">A [ResourceResponse](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#resourceresponse-object&preserve-view=true) object</span></span> |

---

## <a name="update-cards"></a><span data-ttu-id="4c8d3-127">Aktualisieren von Karten</span><span class="sxs-lookup"><span data-stu-id="4c8d3-127">Update cards</span></span>

<span data-ttu-id="4c8d3-128">Zum Aktualisieren der vorhandenen Kartenauswahl für Schaltflächen können Sie eingehende `ReplyToId` Aktivitäten verwenden.</span><span class="sxs-lookup"><span data-stu-id="4c8d3-128">To update the existing card on button selection, you can use `ReplyToId` of incoming activity.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="4c8d3-129">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="4c8d3-129">C#/.NET</span></span>](#tab/dotnet)

<span data-ttu-id="4c8d3-130">Um vorhandene Karten auf einer Schaltfläche zu aktualisieren, übergeben Sie ein neues Objekt mit aktualisierter Karte und als Aktivitäts-ID an die `Activity` `ReplyToId` Methode der `UpdateActivityAsync` `TurnContext` Klasse.</span><span class="sxs-lookup"><span data-stu-id="4c8d3-130">To update existing card on a button click, pass a new `Activity` object with updated card and `ReplyToId` as activity ID to the `UpdateActivityAsync` method of the `TurnContext` class.</span></span> <span data-ttu-id="4c8d3-131">Weitere [Informationen finden Sie unter TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="4c8d3-131">See [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable&preserve-view=true).</span></span>
```csharp
var activity = MessageFactory.Attachment(card.ToAttachment());
activity.Id = turnContext.Activity.ReplyToId;
await turnContext.UpdateActivityAsync(activity, cancellationToken);
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="4c8d3-132">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="4c8d3-132">TypeScript/Node.js</span></span>](#tab/typescript)

<span data-ttu-id="4c8d3-133">Um vorhandene Karten auf einer Schaltfläche zu aktualisieren, übergeben Sie ein neues Objekt mit aktualisierter Karte und als Aktivitäts-ID an die `Activity` `replyToId` `updateActivity` -Methode des `TurnContext` Objekts.</span><span class="sxs-lookup"><span data-stu-id="4c8d3-133">To update existing card on a button click, pass a new `Activity` object with updated card and `replyToId` as activity ID to the `updateActivity` method of the `TurnContext` object.</span></span> <span data-ttu-id="4c8d3-134">Weitere [Informationen finden Sie unter updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="4c8d3-134">See [updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--&preserve-view=true).</span></span>
```typescript
const message = MessageFactory.attachment(card);
message.id = context.activity.replyToId;
await context.updateActivity(message);
```

# <a name="python"></a>[<span data-ttu-id="4c8d3-135">Python</span><span class="sxs-lookup"><span data-stu-id="4c8d3-135">Python</span></span>](#tab/python)

<span data-ttu-id="4c8d3-136">Um vorhandene Karten auf einer Schaltfläche zu aktualisieren, übergeben Sie ein neues Objekt mit aktualisierter Karte und als Aktivitäts-ID an die `Activity` `reply_to_id` Methode der `update_activity` `TurnContext` Klasse.</span><span class="sxs-lookup"><span data-stu-id="4c8d3-136">To update existing card on a button click, pass a new `Activity` object with updated card and `reply_to_id` as activity ID to the `update_activity` method of the `TurnContext` class.</span></span> <span data-ttu-id="4c8d3-137">Weitere [Informationen finden Sie unter TurnContextClass](/python/api/botbuilder-core/botbuilder.core.turncontext?view=botbuilder-py-latest).</span><span class="sxs-lookup"><span data-stu-id="4c8d3-137">See [TurnContextClass](/python/api/botbuilder-core/botbuilder.core.turncontext?view=botbuilder-py-latest).</span></span>

```python
updated_activity = MessageFactory.attachment(CardFactory.hero_card(card))
updated_activity.id = turn_context.activity.reply_to_id
await turn_context.update_activity(updated_activity)

```

## <a name="delete-messages"></a><span data-ttu-id="4c8d3-138">Löschen von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="4c8d3-138">Delete messages</span></span>

<span data-ttu-id="4c8d3-139">Im Bot Framework verfügt jede Nachricht über einen eigenen eindeutigen Aktivitätsbezeichner.</span><span class="sxs-lookup"><span data-stu-id="4c8d3-139">In the Bot Framework, every message has its own unique activity identifier.</span></span>
<span data-ttu-id="4c8d3-140">Nachrichten können mit der Bot Framework-Methode gelöscht `DeleteActivity` werden, wie hier gezeigt.</span><span class="sxs-lookup"><span data-stu-id="4c8d3-140">Messages can be deleted using the Bot Framework's `DeleteActivity` method as shown here.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="4c8d3-141">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="4c8d3-141">C#/.NET</span></span>](#tab/dotnet)

<span data-ttu-id="4c8d3-142">Um diese Nachricht zu löschen, übergeben Sie die ID dieser Aktivität an die `DeleteActivityAsync` -Methode der `TurnContext` Klasse.</span><span class="sxs-lookup"><span data-stu-id="4c8d3-142">To delete that message, pass that activity's ID to the `DeleteActivityAsync` method of the `TurnContext` class.</span></span> <span data-ttu-id="4c8d3-143">Weitere [Informationen finden Sie unter TurnContext.DeleteActivityAsync Method](/dotnet/api/microsoft.bot.builder.turncontext.deleteactivityasync?view=botbuilder-dotnet-stable&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="4c8d3-143">See [TurnContext.DeleteActivityAsync Method](/dotnet/api/microsoft.bot.builder.turncontext.deleteactivityasync?view=botbuilder-dotnet-stable&preserve-view=true).</span></span>

```csharp
foreach (var activityId in _list)
{
    await turnContext.DeleteActivityAsync(activityId, cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="4c8d3-144">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="4c8d3-144">TypeScript/Node.js</span></span>](#tab/typescript)

<span data-ttu-id="4c8d3-145">Um diese Nachricht zu löschen, übergeben Sie die ID dieser Aktivität an die `deleteActivity` -Methode des `TurnContext` Objekts.</span><span class="sxs-lookup"><span data-stu-id="4c8d3-145">To delete that message, pass that activity's ID to the `deleteActivity` method of the `TurnContext` object.</span></span> <span data-ttu-id="4c8d3-146">Siehe [deleteActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#deleteactivity-string---partial-conversationreference--&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="4c8d3-146">See [deleteActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#deleteactivity-string---partial-conversationreference--&preserve-view=true).</span></span>

```typescript
for (let i = 0; i < activityIds.length; i++) {
    await turnContext.deleteActivity(activityIds[i]);
}
```

# <a name="python"></a>[<span data-ttu-id="4c8d3-147">Python</span><span class="sxs-lookup"><span data-stu-id="4c8d3-147">Python</span></span>](#tab/python)

<span data-ttu-id="4c8d3-148">Um diese Nachricht zu löschen, übergeben Sie die ID dieser Aktivität an die `delete_activity` -Methode des `TurnContext` Objekts.</span><span class="sxs-lookup"><span data-stu-id="4c8d3-148">To delete that message, pass that activity's ID to the `delete_activity` method of the `TurnContext` object.</span></span> <span data-ttu-id="4c8d3-149">Weitere Informationen finden Sie [unter activity-update-and-delete](https://github.com/microsoft/botbuilder-python/blob/c04ecacb22c1f4b43a671fe2f1e4782218391975/tests/teams/scenarios/activity-update-and-delete/bots/activity_update_and_delete_bot.py).</span><span class="sxs-lookup"><span data-stu-id="4c8d3-149">See [activity-update-and-delete](https://github.com/microsoft/botbuilder-python/blob/c04ecacb22c1f4b43a671fe2f1e4782218391975/tests/teams/scenarios/activity-update-and-delete/bots/activity_update_and_delete_bot.py).</span></span>

```python
for each activity_id in _list:
    await TurnContext.delete_activity(activity_id)
```

# <a name="rest-api"></a>[<span data-ttu-id="4c8d3-150">REST API</span><span class="sxs-lookup"><span data-stu-id="4c8d3-150">REST API</span></span>](#tab/rest)

 <span data-ttu-id="4c8d3-151">Um eine vorhandene Aktivität in einer Unterhaltung zu löschen, schließen Sie `conversationId` das und in den `activityId` Anforderungsendpunkt ein.</span><span class="sxs-lookup"><span data-stu-id="4c8d3-151">To delete an existing activity within a conversation, include the `conversationId` and `activityId` in the request endpoint.</span></span>

```http
DELETE /v3/conversations/{conversationId}/activities/{activityId}
```

| | |
|----|----|
| <span data-ttu-id="4c8d3-152">**Anforderungstext**</span><span class="sxs-lookup"><span data-stu-id="4c8d3-152">**Request body**</span></span> | <span data-ttu-id="4c8d3-153">n/v</span><span class="sxs-lookup"><span data-stu-id="4c8d3-153">n/a</span></span> |
| <span data-ttu-id="4c8d3-154">**gibt zurück**</span><span class="sxs-lookup"><span data-stu-id="4c8d3-154">**Returns**</span></span> | <span data-ttu-id="4c8d3-155">Ein HTTP-Statuscode, der das Ergebnis des Vorgangs angibt.</span><span class="sxs-lookup"><span data-stu-id="4c8d3-155">An HTTP Status code that indicates the outcome of the operation.</span></span> <span data-ttu-id="4c8d3-156">Im Textkörper der Antwort ist nichts angegeben.</span><span class="sxs-lookup"><span data-stu-id="4c8d3-156">Nothing is specified in the body of the response.</span></span> |

---

## <a name="code-samples"></a><span data-ttu-id="4c8d3-157">Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="4c8d3-157">Code samples</span></span>

<span data-ttu-id="4c8d3-158">Die offiziellen Unterhaltungsgrunddaten sind wie folgt:</span><span class="sxs-lookup"><span data-stu-id="4c8d3-158">The official conversation basics are as follows:</span></span>

| <span data-ttu-id="4c8d3-159">Beispielname</span><span class="sxs-lookup"><span data-stu-id="4c8d3-159">Sample Name</span></span>           | <span data-ttu-id="4c8d3-160">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="4c8d3-160">Description</span></span>                                                                      | <span data-ttu-id="4c8d3-161">.NET</span><span class="sxs-lookup"><span data-stu-id="4c8d3-161">.NET</span></span>    | <span data-ttu-id="4c8d3-162">JavaScript</span><span class="sxs-lookup"><span data-stu-id="4c8d3-162">JavaScript</span></span>   | <span data-ttu-id="4c8d3-163">Python</span><span class="sxs-lookup"><span data-stu-id="4c8d3-163">Python</span></span>  |
|:----------------------|:---------------------------------------------------------------------------------|:--------|:-------------|:--------|
|<span data-ttu-id="4c8d3-164">Grundlagen für Teams-Unterhaltungen</span><span class="sxs-lookup"><span data-stu-id="4c8d3-164">Teams Conversation Basics</span></span>  | <span data-ttu-id="4c8d3-165">Veranschaulicht grundlagen von Unterhaltungen in Teams, einschließlich Nachrichtenaktualisierung und -löschen.</span><span class="sxs-lookup"><span data-stu-id="4c8d3-165">Demonstrates basics of conversations in Teams, including message update and delete.</span></span>|[<span data-ttu-id="4c8d3-166">.NET &nbsp; Core</span><span class="sxs-lookup"><span data-stu-id="4c8d3-166">.NET&nbsp;Core</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot)|[<span data-ttu-id="4c8d3-167">JavaScript</span><span class="sxs-lookup"><span data-stu-id="4c8d3-167">JavaScript</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/57.teams-conversation-bot) | [<span data-ttu-id="4c8d3-168">Python</span><span class="sxs-lookup"><span data-stu-id="4c8d3-168">Python</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/57.teams-conversation-bot)|
