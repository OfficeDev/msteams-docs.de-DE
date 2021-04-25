---
title: Aktualisieren und Löschen von Nachrichten, die von Ihrem Bot gesendet werden
author: WashingtonKayaker
description: Aktualisieren und Löschen von Nachrichten, die von Ihrem Microsoft Teams-Bot gesendet werden
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: a2836d59c22b9784f1f1a0c84306072bb6a97d3e
ms.sourcegitcommit: dd2220f691029d043aaddfc7c229e332735acb1d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2021
ms.locfileid: "51996002"
---
# <a name="update-and-delete-messages-sent-from-your-bot"></a><span data-ttu-id="a0ec7-103">Aktualisieren und Löschen von Nachrichten, die von Ihrem Bot gesendet werden</span><span class="sxs-lookup"><span data-stu-id="a0ec7-103">Update and delete messages sent from your bot</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="a0ec7-104">Ihr Bot kann Nachrichten nach dem Senden dynamisch aktualisieren, anstatt sie als statische Momentaufnahmen von Daten zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="a0ec7-104">Your bot can dynamically update messages after sending them instead of having them as static snapshots of data.</span></span> <span data-ttu-id="a0ec7-105">Nachrichten können auch mit der Bot Framework-Methode gelöscht `DeleteActivity` werden.</span><span class="sxs-lookup"><span data-stu-id="a0ec7-105">Messages can also be deleted using the Bot Framework's `DeleteActivity` method.</span></span>

## <a name="update-messages"></a><span data-ttu-id="a0ec7-106">Nachricht aktualisieren</span><span class="sxs-lookup"><span data-stu-id="a0ec7-106">Update messages</span></span>

<span data-ttu-id="a0ec7-107">Sie können dynamische Nachrichtenupdates für Szenarien verwenden, z. B. Abrufupdates, Ändern verfügbarer Aktionen nach dem Drücken einer Schaltfläche oder andere asynchrone Statusänderung.</span><span class="sxs-lookup"><span data-stu-id="a0ec7-107">You can use dynamic message updates for scenarios, such as poll updates, modifying available actions after a button press, or any other asynchronous state change.</span></span>

<span data-ttu-id="a0ec7-108">Es ist nicht erforderlich, dass die neue Nachricht mit dem originalen Typ übereinstimmen muss.</span><span class="sxs-lookup"><span data-stu-id="a0ec7-108">It is not necessary for the new message to match the original in type.</span></span> <span data-ttu-id="a0ec7-109">Wenn die ursprüngliche Nachricht beispielsweise eine Anlage enthält, kann die neue Nachricht eine einfache Textnachricht sein.</span><span class="sxs-lookup"><span data-stu-id="a0ec7-109">For example, if the original message contains an attachment, the new message can be a simple text message.</span></span>

# <a name="c"></a>[<span data-ttu-id="a0ec7-110">C#</span><span class="sxs-lookup"><span data-stu-id="a0ec7-110">C#</span></span>](#tab/dotnet)

<span data-ttu-id="a0ec7-111">Um eine vorhandene Nachricht zu aktualisieren, übergeben Sie ein neues Objekt mit der vorhandenen `Activity` Aktivitäts-ID an die `UpdateActivityAsync` -Methode der `TurnContext` Klasse.</span><span class="sxs-lookup"><span data-stu-id="a0ec7-111">To update an existing message, pass a new `Activity` object with the existing activity ID to the `UpdateActivityAsync` method of the `TurnContext` class.</span></span> <span data-ttu-id="a0ec7-112">Weitere Informationen finden Sie unter [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="a0ec7-112">For more information, see [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable&preserve-view=true).</span></span>

```csharp
var newActivity = MessageFactory.Text("The new text for the activity");
newActivity.Id = activityId;
await turnContext.UpdateActivityAsync(newActivity, cancellationToken);
```

# <a name="typescript"></a>[<span data-ttu-id="a0ec7-113">TypeScript</span><span class="sxs-lookup"><span data-stu-id="a0ec7-113">TypeScript</span></span>](#tab/typescript)

<span data-ttu-id="a0ec7-114">Um eine vorhandene Nachricht zu aktualisieren, übergeben Sie ein neues Objekt mit der vorhandenen Aktivitäts-ID `Activity` an die `updateActivity` -Methode des `TurnContext` Objekts.</span><span class="sxs-lookup"><span data-stu-id="a0ec7-114">To update an existing message, pass a new `Activity` object with the existing activity ID to the `updateActivity` method of the `TurnContext` object.</span></span> <span data-ttu-id="a0ec7-115">Weitere Informationen finden Sie unter [updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="a0ec7-115">For more information, see [updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--&preserve-view=true).</span></span>

```typescript
const newActivity = MessageFactory.text('The new text for the activity');
newActivity.id = activityId;
await turnContext.updateActivity(newActivity);
```

# <a name="python"></a>[<span data-ttu-id="a0ec7-116">Python</span><span class="sxs-lookup"><span data-stu-id="a0ec7-116">Python</span></span>](#tab/python)

<span data-ttu-id="a0ec7-117">Um eine vorhandene Nachricht zu aktualisieren, übergeben Sie ein neues Objekt mit der vorhandenen `Activity` Aktivitäts-ID an die `update_activity` -Methode der `TurnContext` Klasse.</span><span class="sxs-lookup"><span data-stu-id="a0ec7-117">To update an existing message, pass a new `Activity` object with the existing activity ID to the `update_activity` method of the `TurnContext` class.</span></span> <span data-ttu-id="a0ec7-118">Weitere [Informationen finden Sie unter TurnContextClass](/python/api/botbuilder-core/botbuilder.core.turncontext?view=botbuilder-py-latest&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="a0ec7-118">See [TurnContextClass](/python/api/botbuilder-core/botbuilder.core.turncontext?view=botbuilder-py-latest&preserve-view=true).</span></span>

```python
new_activity = MessageFactory.text("The new text for the activity")
new_activity.id = activity_id
update_result = await context.update_activity(new_activity)
```

# <a name="rest-api"></a>[<span data-ttu-id="a0ec7-119">REST API</span><span class="sxs-lookup"><span data-stu-id="a0ec7-119">REST API</span></span>](#tab/rest)

> [!NOTE]

> <span data-ttu-id="a0ec7-120">Sie können Teams-Apps in jeder beliebigen Webprogrammiertechnologie entwickeln und direkt die [Bot Connector-Dienst-REST-APIs aufrufen.](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="a0ec7-120">You can develop Teams apps in any web-programming technology and directly call the [Bot Connector service REST APIs](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span> <span data-ttu-id="a0ec7-121">Dazu müssen Sie Authentifizierungssicherheitsverfahren mit Ihren API-Anforderungen implementieren. [](/azure/bot-service/rest-api/bot-framework-rest-connector-authentication?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="a0ec7-121">To do so, you need to implement [Authentication](/azure/bot-service/rest-api/bot-framework-rest-connector-authentication?view=azure-bot-service-4.0&preserve-view=true) security procedures with your API requests.</span></span>

<span data-ttu-id="a0ec7-122">Um eine vorhandene Aktivität in einer Unterhaltung zu aktualisieren, schließen Sie `conversationId` das und in den `activityId` Anforderungsendpunkt ein.</span><span class="sxs-lookup"><span data-stu-id="a0ec7-122">To update an existing activity within a conversation, include the `conversationId` and `activityId` in the request endpoint.</span></span> <span data-ttu-id="a0ec7-123">Zum Abschließen dieses Szenarios müssen Sie die vom ursprünglichen Postanruf zurückgegebene Aktivitäts-ID zwischenspeichern.</span><span class="sxs-lookup"><span data-stu-id="a0ec7-123">To complete this scenario, you must cache the activity ID returned by the original post call.</span></span>

```http
PUT /v3/conversations/{conversationId}/activities/{activityId}
```

| <span data-ttu-id="a0ec7-124">**Anforderung und Responce**</span><span class="sxs-lookup"><span data-stu-id="a0ec7-124">**Request and Responce**</span></span> | <span data-ttu-id="a0ec7-125">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="a0ec7-125">**Description**</span></span> |
|----|----|
| <span data-ttu-id="a0ec7-126">Ein [Aktivitätsobjekt](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#activity-object&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="a0ec7-126">An [activity](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#activity-object&preserve-view=true) object</span></span> | <span data-ttu-id="a0ec7-127">Ein [ResourceResponse-Objekt](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#resourceresponse-object&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="a0ec7-127">A [ResourceResponse](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#resourceresponse-object&preserve-view=true) object</span></span> |

---
* * *

<span data-ttu-id="a0ec7-128">Nachdem Sie Nachrichten aktualisiert haben, aktualisieren Sie die vorhandene Karte auf Schaltflächenauswahl für eingehende Aktivitäten.</span><span class="sxs-lookup"><span data-stu-id="a0ec7-128">Now that you have updated messages, update the existing card on button selection for incoming activities.</span></span>

## <a name="update-cards"></a><span data-ttu-id="a0ec7-129">Aktualisieren von Karten</span><span class="sxs-lookup"><span data-stu-id="a0ec7-129">Update cards</span></span>

<span data-ttu-id="a0ec7-130">Zum Aktualisieren der vorhandenen Kartenauswahl für Schaltflächen können Sie eingehende `ReplyToId` Aktivitäten verwenden.</span><span class="sxs-lookup"><span data-stu-id="a0ec7-130">To update the existing card on button selection, you can use `ReplyToId` of incoming activity.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="a0ec7-131">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="a0ec7-131">C#/.NET</span></span>](#tab/dotnet)

<span data-ttu-id="a0ec7-132">Um vorhandene Karten für eine Schaltflächenauswahl zu aktualisieren, übergeben Sie ein neues Objekt mit aktualisierter Karte und als Aktivitäts-ID an die `Activity` `ReplyToId` `UpdateActivityAsync` -Methode der `TurnContext` Klasse.</span><span class="sxs-lookup"><span data-stu-id="a0ec7-132">To update existing card on a button selection, pass a new `Activity` object with updated card and `ReplyToId` as activity ID to the `UpdateActivityAsync` method of the `TurnContext` class.</span></span> <span data-ttu-id="a0ec7-133">Weitere [Informationen finden Sie unter TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="a0ec7-133">See [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable&preserve-view=true).</span></span>

```csharp
var activity = MessageFactory.Attachment(card.ToAttachment());
activity.Id = turnContext.Activity.ReplyToId;
await turnContext.UpdateActivityAsync(activity, cancellationToken);
```

# <a name="typescript"></a>[<span data-ttu-id="a0ec7-134">TypeScript</span><span class="sxs-lookup"><span data-stu-id="a0ec7-134">TypeScript</span></span>](#tab/typescript)

<span data-ttu-id="a0ec7-135">Um vorhandene Karten für eine Schaltflächenauswahl zu aktualisieren, übergeben Sie ein neues Objekt mit aktualisierter Karte und als Aktivitäts-ID an die `Activity` `replyToId` `updateActivity` -Methode des `TurnContext` Objekts.</span><span class="sxs-lookup"><span data-stu-id="a0ec7-135">To update existing card on a button selection, pass a new `Activity` object with updated card and `replyToId` as activity ID to the `updateActivity` method of the `TurnContext` object.</span></span> <span data-ttu-id="a0ec7-136">Weitere [Informationen finden Sie unter updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="a0ec7-136">See [updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--&preserve-view=true).</span></span>

```typescript
const message = MessageFactory.attachment(card);
message.id = context.activity.replyToId;
await context.updateActivity(message);
```

# <a name="python"></a>[<span data-ttu-id="a0ec7-137">Python</span><span class="sxs-lookup"><span data-stu-id="a0ec7-137">Python</span></span>](#tab/python)

<span data-ttu-id="a0ec7-138">Um vorhandene Karten auf einer Schaltfläche zu aktualisieren, übergeben Sie ein neues Objekt mit aktualisierter Karte und als Aktivitäts-ID an die `Activity` `reply_to_id` Methode der `update_activity` `TurnContext` Klasse.</span><span class="sxs-lookup"><span data-stu-id="a0ec7-138">To update existing card on a button click, pass a new `Activity` object with updated card and `reply_to_id` as activity ID to the `update_activity` method of the `TurnContext` class.</span></span> <span data-ttu-id="a0ec7-139">Weitere [Informationen finden Sie unter TurnContextClass](/python/api/botbuilder-core/botbuilder.core.turncontext?view=botbuilder-py-latest&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="a0ec7-139">See [TurnContextClass](/python/api/botbuilder-core/botbuilder.core.turncontext?view=botbuilder-py-latest&preserve-view=true).</span></span>

```python
updated_activity = MessageFactory.attachment(CardFactory.hero_card(card))
updated_activity.id = turn_context.activity.reply_to_id
await turn_context.update_activity(updated_activity)
```

# <a name="rest-api"></a>[<span data-ttu-id="a0ec7-140">REST API</span><span class="sxs-lookup"><span data-stu-id="a0ec7-140">REST API</span></span>](#tab/rest)

> [!NOTE]
> <span data-ttu-id="a0ec7-141">Sie können Teams-Apps in jeder beliebigen Webprogrammiertechnologie entwickeln und direkt den [Botconnectordienst REST-APIs aufrufen.](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="a0ec7-141">You can develop Teams apps in any web programming technology and directly call the [bot connector service REST APIs](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span> <span data-ttu-id="a0ec7-142">Dazu müssen Sie Authentifizierungssicherheitsverfahren mit Ihren API-Anforderungen implementieren. [](/azure/bot-service/rest-api/bot-framework-rest-connector-authentication?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="a0ec7-142">To do this, you must implement [authentication](/azure/bot-service/rest-api/bot-framework-rest-connector-authentication?view=azure-bot-service-4.0&preserve-view=true) security procedures with your API requests.</span></span>

<span data-ttu-id="a0ec7-143">Um eine vorhandene Aktivität in einer Unterhaltung zu aktualisieren, schließen Sie `conversationId` das und in den `activityId` Anforderungsendpunkt ein.</span><span class="sxs-lookup"><span data-stu-id="a0ec7-143">To update an existing activity within a conversation, include the `conversationId` and `activityId` in the request endpoint.</span></span> <span data-ttu-id="a0ec7-144">Zum Abschließen dieses Szenarios müssen Sie die vom ursprünglichen Postanruf zurückgegebene Aktivitäts-ID zwischenspeichern.</span><span class="sxs-lookup"><span data-stu-id="a0ec7-144">To complete this scenario, you must cache the activity ID returned by the original post call.</span></span>

```http
PUT /v3/conversations/{conversationId}/activities/{activityId}
```

|<span data-ttu-id="a0ec7-145">Anforderung</span><span class="sxs-lookup"><span data-stu-id="a0ec7-145">Request</span></span> |<span data-ttu-id="a0ec7-146">Antwort</span><span class="sxs-lookup"><span data-stu-id="a0ec7-146">Response</span></span> |
|----|----|
| <span data-ttu-id="a0ec7-147">Ein [Aktivitätsobjekt.](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#activity-object&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="a0ec7-147">An [activity](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#activity-object&preserve-view=true) object.</span></span> | <span data-ttu-id="a0ec7-148">Ein [ResourceResponse-Objekt.](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#resourceresponse-object&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="a0ec7-148">A [ResourceResponse](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#resourceresponse-object&preserve-view=true) object.</span></span> |

* * *

<span data-ttu-id="a0ec7-149">Nachdem Sie karten aktualisiert haben, können Sie Nachrichten mit dem Bot Framework löschen.</span><span class="sxs-lookup"><span data-stu-id="a0ec7-149">Now that you have updated cards, you can delete messages using the Bot Framework.</span></span>

## <a name="delete-messages"></a><span data-ttu-id="a0ec7-150">Löschen von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="a0ec7-150">Delete messages</span></span>

<span data-ttu-id="a0ec7-151">Im Bot Framework hat jede Nachricht ihren eindeutigen Aktivitätsbezeichner.</span><span class="sxs-lookup"><span data-stu-id="a0ec7-151">In the Bot Framework, every message has its unique activity identifier.</span></span> <span data-ttu-id="a0ec7-152">Nachrichten können mit der Bot Framework-Methode gelöscht `DeleteActivity` werden.</span><span class="sxs-lookup"><span data-stu-id="a0ec7-152">Messages can be deleted using the Bot Framework's `DeleteActivity` method.</span></span>

# <a name="c"></a>[<span data-ttu-id="a0ec7-153">C#</span><span class="sxs-lookup"><span data-stu-id="a0ec7-153">C#</span></span>](#tab/dotnet)

<span data-ttu-id="a0ec7-154">Um eine Nachricht zu löschen, übergeben Sie die ID dieser Aktivität an die `DeleteActivityAsync` -Methode der `TurnContext` Klasse.</span><span class="sxs-lookup"><span data-stu-id="a0ec7-154">To delete a message, pass that activity's ID to the `DeleteActivityAsync` method of the `TurnContext` class.</span></span> <span data-ttu-id="a0ec7-155">Weitere Informationen finden Sie unter [TurnContext.DeleteActivityAsync-Methode](/dotnet/api/microsoft.bot.builder.turncontext.deleteactivityasync?view=botbuilder-dotnet-stable&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="a0ec7-155">For more information, see [TurnContext.DeleteActivityAsync Method](/dotnet/api/microsoft.bot.builder.turncontext.deleteactivityasync?view=botbuilder-dotnet-stable&preserve-view=true).</span></span>

```csharp
foreach (var activityId in _list)
{
    await turnContext.DeleteActivityAsync(activityId, cancellationToken);
}
```

# <a name="typescript"></a>[<span data-ttu-id="a0ec7-156">TypeScript</span><span class="sxs-lookup"><span data-stu-id="a0ec7-156">TypeScript</span></span>](#tab/typescript)

<span data-ttu-id="a0ec7-157">Um eine Nachricht zu löschen, übergeben Sie die ID dieser Aktivität an die `deleteActivity` -Methode des `TurnContext` Objekts.</span><span class="sxs-lookup"><span data-stu-id="a0ec7-157">To delete a message, pass that activity's ID to the `deleteActivity` method of the `TurnContext` object.</span></span> <span data-ttu-id="a0ec7-158">Weitere Informationen finden Sie unter [deleteActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#deleteactivity-string---partial-conversationreference--&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="a0ec7-158">For more information, see [deleteActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#deleteactivity-string---partial-conversationreference--&preserve-view=true).</span></span>

```typescript
for (let i = 0; i < activityIds.length; i++) {
    await turnContext.deleteActivity(activityIds[i]);
}
```

# <a name="python"></a>[<span data-ttu-id="a0ec7-159">Python</span><span class="sxs-lookup"><span data-stu-id="a0ec7-159">Python</span></span>](#tab/python)

<span data-ttu-id="a0ec7-160">Um diese Nachricht zu löschen, übergeben Sie die ID dieser Aktivität an die `delete_activity` -Methode des `TurnContext` Objekts.</span><span class="sxs-lookup"><span data-stu-id="a0ec7-160">To delete that message, pass that activity's ID to the `delete_activity` method of the `TurnContext` object.</span></span> <span data-ttu-id="a0ec7-161">Weitere Informationen finden Sie unter [activity-update-and-delete](https://github.com/microsoft/botbuilder-python/blob/c04ecacb22c1f4b43a671fe2f1e4782218391975/tests/teams/scenarios/activity-update-and-delete/bots/activity_update_and_delete_bot.py).</span><span class="sxs-lookup"><span data-stu-id="a0ec7-161">For more information, see [activity-update-and-delete](https://github.com/microsoft/botbuilder-python/blob/c04ecacb22c1f4b43a671fe2f1e4782218391975/tests/teams/scenarios/activity-update-and-delete/bots/activity_update_and_delete_bot.py).</span></span>

```python
for each activity_id in _list:
    await TurnContext.delete_activity(activity_id)
```

# <a name="rest-api"></a>[<span data-ttu-id="a0ec7-162">REST API</span><span class="sxs-lookup"><span data-stu-id="a0ec7-162">REST API</span></span>](#tab/rest)

<span data-ttu-id="a0ec7-163">Um eine vorhandene Aktivität in einer Unterhaltung zu löschen, schließen Sie `conversationId` das und in den `activityId` Anforderungsendpunkt ein.</span><span class="sxs-lookup"><span data-stu-id="a0ec7-163">To delete an existing activity within a conversation, include the `conversationId` and `activityId` in the request endpoint.</span></span>

```http
DELETE /v3/conversations/{conversationId}/activities/{activityId}
```

| <span data-ttu-id="a0ec7-164">**Anforderung und Responce**</span><span class="sxs-lookup"><span data-stu-id="a0ec7-164">**Request and Responce**</span></span> | <span data-ttu-id="a0ec7-165">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="a0ec7-165">**Description**</span></span> |
|----|----|
| <span data-ttu-id="a0ec7-166">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="a0ec7-166">N/A</span></span> | <span data-ttu-id="a0ec7-167">Ein HTTP-Statuscode, der das Ergebnis des Vorgangs angibt.</span><span class="sxs-lookup"><span data-stu-id="a0ec7-167">An HTTP status code that indicates the outcome of the operation.</span></span> <span data-ttu-id="a0ec7-168">Im Textkörper der Antwort ist nichts angegeben.</span><span class="sxs-lookup"><span data-stu-id="a0ec7-168">Nothing is specified in the body of the response.</span></span> |

---

## <a name="code-sample"></a><span data-ttu-id="a0ec7-169">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="a0ec7-169">Code sample</span></span>

<span data-ttu-id="a0ec7-170">Im folgenden Codebeispiel werden die Grundlagen von Unterhaltungen veranschaulicht:</span><span class="sxs-lookup"><span data-stu-id="a0ec7-170">The following code sample demonstrates basics of conversations:</span></span>

| <span data-ttu-id="a0ec7-171">**Beispielname**</span><span class="sxs-lookup"><span data-stu-id="a0ec7-171">**Sample Name**</span></span> | <span data-ttu-id="a0ec7-172">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="a0ec7-172">**Description**</span></span> | <span data-ttu-id="a0ec7-173">**.NET**</span><span class="sxs-lookup"><span data-stu-id="a0ec7-173">**.NET**</span></span> | <span data-ttu-id="a0ec7-174">**Node.js**</span><span class="sxs-lookup"><span data-stu-id="a0ec7-174">**Node.js**</span></span> | <span data-ttu-id="a0ec7-175">**Python**</span><span class="sxs-lookup"><span data-stu-id="a0ec7-175">**Python**</span></span> |
|----------------------|-----------------|--------|-------------|--------|
| <span data-ttu-id="a0ec7-176">Grundlagen für Teams-Unterhaltungen</span><span class="sxs-lookup"><span data-stu-id="a0ec7-176">Teams Conversation Basics</span></span>  | <span data-ttu-id="a0ec7-177">Veranschaulicht grundlagen von Unterhaltungen in Teams, einschließlich Nachrichtenaktualisierung und -löschen.</span><span class="sxs-lookup"><span data-stu-id="a0ec7-177">Demonstrates basics of conversations in Teams including message update and delete.</span></span> | [<span data-ttu-id="a0ec7-178">View</span><span class="sxs-lookup"><span data-stu-id="a0ec7-178">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot) | [<span data-ttu-id="a0ec7-179">View</span><span class="sxs-lookup"><span data-stu-id="a0ec7-179">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/57.teams-conversation-bot) | [<span data-ttu-id="a0ec7-180">View</span><span class="sxs-lookup"><span data-stu-id="a0ec7-180">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/57.teams-conversation-bot) |

## <a name="next-step"></a><span data-ttu-id="a0ec7-181">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="a0ec7-181">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a0ec7-182">Get Teams context</span><span class="sxs-lookup"><span data-stu-id="a0ec7-182">Get Teams context</span></span>](~/bots/how-to/get-teams-context.md)
