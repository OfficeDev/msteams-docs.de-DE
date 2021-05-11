---
title: Aktualisieren und Löschen von Nachrichten, die von Ihrem Bot gesendet werden
author: WashingtonKayaker
description: Aktualisieren und Löschen von Nachrichten, die von Ihrem Microsoft Teams werden
ms.topic: overview
localization_priority: Normal
ms.author: anclear
ms.openlocfilehash: 90dc50fd2ec153813457f199ac029e17a0157502
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101534"
---
# <a name="update-and-delete-messages-sent-from-your-bot"></a><span data-ttu-id="cfca6-103">Aktualisieren und Löschen von Nachrichten, die von Ihrem Bot gesendet werden</span><span class="sxs-lookup"><span data-stu-id="cfca6-103">Update and delete messages sent from your bot</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="cfca6-104">Ihr Bot kann Nachrichten nach dem Senden dynamisch aktualisieren, anstatt sie als statische Momentaufnahmen von Daten zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="cfca6-104">Your bot can dynamically update messages after sending them instead of having them as static snapshots of data.</span></span> <span data-ttu-id="cfca6-105">Nachrichten können auch mit der Bot Framework-Methode gelöscht `DeleteActivity` werden.</span><span class="sxs-lookup"><span data-stu-id="cfca6-105">Messages can also be deleted using the Bot Framework's `DeleteActivity` method.</span></span>

## <a name="update-messages"></a><span data-ttu-id="cfca6-106">Nachricht aktualisieren</span><span class="sxs-lookup"><span data-stu-id="cfca6-106">Update messages</span></span>

<span data-ttu-id="cfca6-107">Sie können dynamische Nachrichtenupdates für Szenarien verwenden, z. B. Abrufupdates, Ändern verfügbarer Aktionen nach dem Drücken einer Schaltfläche oder andere asynchrone Statusänderung.</span><span class="sxs-lookup"><span data-stu-id="cfca6-107">You can use dynamic message updates for scenarios, such as poll updates, modifying available actions after a button press, or any other asynchronous state change.</span></span>

<span data-ttu-id="cfca6-108">Es ist nicht erforderlich, dass die neue Nachricht mit dem originalen Typ übereinstimmen muss.</span><span class="sxs-lookup"><span data-stu-id="cfca6-108">It is not necessary for the new message to match the original in type.</span></span> <span data-ttu-id="cfca6-109">Wenn die ursprüngliche Nachricht beispielsweise eine Anlage enthält, kann die neue Nachricht eine einfache Textnachricht sein.</span><span class="sxs-lookup"><span data-stu-id="cfca6-109">For example, if the original message contains an attachment, the new message can be a simple text message.</span></span>

# <a name="c"></a>[<span data-ttu-id="cfca6-110">C#</span><span class="sxs-lookup"><span data-stu-id="cfca6-110">C#</span></span>](#tab/dotnet)

<span data-ttu-id="cfca6-111">Um eine vorhandene Nachricht zu aktualisieren, übergeben Sie ein neues Objekt mit der vorhandenen `Activity` Aktivitäts-ID an die `UpdateActivityAsync` -Methode der `TurnContext` Klasse.</span><span class="sxs-lookup"><span data-stu-id="cfca6-111">To update an existing message, pass a new `Activity` object with the existing activity ID to the `UpdateActivityAsync` method of the `TurnContext` class.</span></span> <span data-ttu-id="cfca6-112">Weitere Informationen finden Sie unter [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="cfca6-112">For more information, see [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable&preserve-view=true).</span></span>

```csharp
var newActivity = MessageFactory.Text("The new text for the activity");
newActivity.Id = activityId;
await turnContext.UpdateActivityAsync(newActivity, cancellationToken);
```

# <a name="typescript"></a>[<span data-ttu-id="cfca6-113">TypeScript</span><span class="sxs-lookup"><span data-stu-id="cfca6-113">TypeScript</span></span>](#tab/typescript)

<span data-ttu-id="cfca6-114">Um eine vorhandene Nachricht zu aktualisieren, übergeben Sie ein neues Objekt mit der vorhandenen Aktivitäts-ID `Activity` an die `updateActivity` -Methode des `TurnContext` Objekts.</span><span class="sxs-lookup"><span data-stu-id="cfca6-114">To update an existing message, pass a new `Activity` object with the existing activity ID to the `updateActivity` method of the `TurnContext` object.</span></span> <span data-ttu-id="cfca6-115">Weitere Informationen finden Sie unter [updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="cfca6-115">For more information, see [updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--&preserve-view=true).</span></span>

```typescript
const newActivity = MessageFactory.text('The new text for the activity');
newActivity.id = activityId;
await turnContext.updateActivity(newActivity);
```

# <a name="python"></a>[<span data-ttu-id="cfca6-116">Python</span><span class="sxs-lookup"><span data-stu-id="cfca6-116">Python</span></span>](#tab/python)

<span data-ttu-id="cfca6-117">Um eine vorhandene Nachricht zu aktualisieren, übergeben Sie ein neues Objekt mit der vorhandenen `Activity` Aktivitäts-ID an die `update_activity` -Methode der `TurnContext` Klasse.</span><span class="sxs-lookup"><span data-stu-id="cfca6-117">To update an existing message, pass a new `Activity` object with the existing activity ID to the `update_activity` method of the `TurnContext` class.</span></span> <span data-ttu-id="cfca6-118">Weitere [Informationen finden Sie unter TurnContextClass](/python/api/botbuilder-core/botbuilder.core.turncontext?view=botbuilder-py-latest&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="cfca6-118">See [TurnContextClass](/python/api/botbuilder-core/botbuilder.core.turncontext?view=botbuilder-py-latest&preserve-view=true).</span></span>

```python
new_activity = MessageFactory.text("The new text for the activity")
new_activity.id = activity_id
update_result = await context.update_activity(new_activity)
```

# <a name="rest-api"></a>[<span data-ttu-id="cfca6-119">REST API</span><span class="sxs-lookup"><span data-stu-id="cfca6-119">REST API</span></span>](#tab/rest)

> [!NOTE]

> <span data-ttu-id="cfca6-120">Sie können Teams in jeder Webprogrammiertechnologie entwickeln und die [Bot Connector-Dienst-REST-APIs direkt aufrufen.](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="cfca6-120">You can develop Teams apps in any web-programming technology and directly call the [Bot Connector service REST APIs](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span> <span data-ttu-id="cfca6-121">Dazu müssen Sie Authentifizierungssicherheitsverfahren mit Ihren API-Anforderungen implementieren. [](/azure/bot-service/rest-api/bot-framework-rest-connector-authentication?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="cfca6-121">To do so, you need to implement [Authentication](/azure/bot-service/rest-api/bot-framework-rest-connector-authentication?view=azure-bot-service-4.0&preserve-view=true) security procedures with your API requests.</span></span>

<span data-ttu-id="cfca6-122">Um eine vorhandene Aktivität in einer Unterhaltung zu aktualisieren, schließen Sie `conversationId` das und in den `activityId` Anforderungsendpunkt ein.</span><span class="sxs-lookup"><span data-stu-id="cfca6-122">To update an existing activity within a conversation, include the `conversationId` and `activityId` in the request endpoint.</span></span> <span data-ttu-id="cfca6-123">Zum Abschließen dieses Szenarios müssen Sie die vom ursprünglichen Postanruf zurückgegebene Aktivitäts-ID zwischenspeichern.</span><span class="sxs-lookup"><span data-stu-id="cfca6-123">To complete this scenario, you must cache the activity ID returned by the original post call.</span></span>

```http
PUT /v3/conversations/{conversationId}/activities/{activityId}
```

|<span data-ttu-id="cfca6-124">Anforderung</span><span class="sxs-lookup"><span data-stu-id="cfca6-124">Request</span></span> |<span data-ttu-id="cfca6-125">Antwort</span><span class="sxs-lookup"><span data-stu-id="cfca6-125">Response</span></span> |
|----|----|
| <span data-ttu-id="cfca6-126">Ein [Activity-Objekt.](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#activity-object&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="cfca6-126">An [Activity](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#activity-object&preserve-view=true) object.</span></span> | <span data-ttu-id="cfca6-127">Ein [ResourceResponse-Objekt.](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#resourceresponse-object&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="cfca6-127">A [ResourceResponse](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#resourceresponse-object&preserve-view=true) object.</span></span> |

---
* * *

<span data-ttu-id="cfca6-128">Nachdem Sie Nachrichten aktualisiert haben, aktualisieren Sie die vorhandene Karte auf Schaltflächenauswahl für eingehende Aktivitäten.</span><span class="sxs-lookup"><span data-stu-id="cfca6-128">Now that you have updated messages, update the existing card on button selection for incoming activities.</span></span>

## <a name="update-cards"></a><span data-ttu-id="cfca6-129">Aktualisieren von Karten</span><span class="sxs-lookup"><span data-stu-id="cfca6-129">Update cards</span></span>

<span data-ttu-id="cfca6-130">Zum Aktualisieren der vorhandenen Kartenauswahl für Schaltflächen können Sie eingehende `ReplyToId` Aktivitäten verwenden.</span><span class="sxs-lookup"><span data-stu-id="cfca6-130">To update the existing card on button selection, you can use `ReplyToId` of incoming activity.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="cfca6-131">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="cfca6-131">C#/.NET</span></span>](#tab/dotnet)

<span data-ttu-id="cfca6-132">Um vorhandene Karten für eine Schaltflächenauswahl zu aktualisieren, übergeben Sie ein neues Objekt mit aktualisierter Karte und als Aktivitäts-ID an die `Activity` `ReplyToId` `UpdateActivityAsync` -Methode der `TurnContext` Klasse.</span><span class="sxs-lookup"><span data-stu-id="cfca6-132">To update existing card on a button selection, pass a new `Activity` object with updated card and `ReplyToId` as activity ID to the `UpdateActivityAsync` method of the `TurnContext` class.</span></span> <span data-ttu-id="cfca6-133">Weitere [Informationen finden Sie unter TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="cfca6-133">See [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable&preserve-view=true).</span></span>

```csharp
var activity = MessageFactory.Attachment(card.ToAttachment());
activity.Id = turnContext.Activity.ReplyToId;
await turnContext.UpdateActivityAsync(activity, cancellationToken);
```

# <a name="typescript"></a>[<span data-ttu-id="cfca6-134">TypeScript</span><span class="sxs-lookup"><span data-stu-id="cfca6-134">TypeScript</span></span>](#tab/typescript)

<span data-ttu-id="cfca6-135">Um vorhandene Karten für eine Schaltflächenauswahl zu aktualisieren, übergeben Sie ein neues Objekt mit aktualisierter Karte und als Aktivitäts-ID an die `Activity` `replyToId` `updateActivity` -Methode des `TurnContext` Objekts.</span><span class="sxs-lookup"><span data-stu-id="cfca6-135">To update existing card on a button selection, pass a new `Activity` object with updated card and `replyToId` as activity ID to the `updateActivity` method of the `TurnContext` object.</span></span> <span data-ttu-id="cfca6-136">Weitere [Informationen finden Sie unter updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="cfca6-136">See [updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--&preserve-view=true).</span></span>

```typescript
const message = MessageFactory.attachment(card);
message.id = context.activity.replyToId;
await context.updateActivity(message);
```

# <a name="python"></a>[<span data-ttu-id="cfca6-137">Python</span><span class="sxs-lookup"><span data-stu-id="cfca6-137">Python</span></span>](#tab/python)

<span data-ttu-id="cfca6-138">Um vorhandene Karten auf einer Schaltfläche zu aktualisieren, übergeben Sie ein neues Objekt mit aktualisierter Karte und als Aktivitäts-ID an die `Activity` `reply_to_id` Methode der `update_activity` `TurnContext` Klasse.</span><span class="sxs-lookup"><span data-stu-id="cfca6-138">To update existing card on a button click, pass a new `Activity` object with updated card and `reply_to_id` as activity ID to the `update_activity` method of the `TurnContext` class.</span></span> <span data-ttu-id="cfca6-139">Weitere [Informationen finden Sie unter TurnContextClass](/python/api/botbuilder-core/botbuilder.core.turncontext?view=botbuilder-py-latest&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="cfca6-139">See [TurnContextClass](/python/api/botbuilder-core/botbuilder.core.turncontext?view=botbuilder-py-latest&preserve-view=true).</span></span>

```python
updated_activity = MessageFactory.attachment(CardFactory.hero_card(card))
updated_activity.id = turn_context.activity.reply_to_id
await turn_context.update_activity(updated_activity)
```

# <a name="rest-api"></a>[<span data-ttu-id="cfca6-140">REST API</span><span class="sxs-lookup"><span data-stu-id="cfca6-140">REST API</span></span>](#tab/rest)

> [!NOTE]
> <span data-ttu-id="cfca6-141">Sie können Teams apps in jeder Webprogrammiertechnologie entwickeln und direkt den [Botconnectordienst REST-APIs aufrufen.](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="cfca6-141">You can develop Teams apps in any web programming technology and directly call the [bot connector service REST APIs](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span> <span data-ttu-id="cfca6-142">Dazu müssen Sie Authentifizierungssicherheitsverfahren mit Ihren API-Anforderungen implementieren. [](/azure/bot-service/rest-api/bot-framework-rest-connector-authentication?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="cfca6-142">To do this, you must implement [authentication](/azure/bot-service/rest-api/bot-framework-rest-connector-authentication?view=azure-bot-service-4.0&preserve-view=true) security procedures with your API requests.</span></span>

<span data-ttu-id="cfca6-143">Um eine vorhandene Aktivität in einer Unterhaltung zu aktualisieren, schließen Sie `conversationId` das und in den `activityId` Anforderungsendpunkt ein.</span><span class="sxs-lookup"><span data-stu-id="cfca6-143">To update an existing activity within a conversation, include the `conversationId` and `activityId` in the request endpoint.</span></span> <span data-ttu-id="cfca6-144">Zum Abschließen dieses Szenarios müssen Sie die vom ursprünglichen Postanruf zurückgegebene Aktivitäts-ID zwischenspeichern.</span><span class="sxs-lookup"><span data-stu-id="cfca6-144">To complete this scenario, you must cache the activity ID returned by the original post call.</span></span>

```http
PUT /v3/conversations/{conversationId}/activities/{activityId}
```

|<span data-ttu-id="cfca6-145">Anforderung</span><span class="sxs-lookup"><span data-stu-id="cfca6-145">Request</span></span> |<span data-ttu-id="cfca6-146">Antwort</span><span class="sxs-lookup"><span data-stu-id="cfca6-146">Response</span></span> |
|----|----|
| <span data-ttu-id="cfca6-147">Ein [Aktivitätsobjekt.](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#activity-object&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="cfca6-147">An [activity](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#activity-object&preserve-view=true) object.</span></span> | <span data-ttu-id="cfca6-148">Ein [ResourceResponse-Objekt.](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#resourceresponse-object&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="cfca6-148">A [ResourceResponse](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#resourceresponse-object&preserve-view=true) object.</span></span> |

* * *

<span data-ttu-id="cfca6-149">Nachdem Sie karten aktualisiert haben, können Sie Nachrichten mit dem Bot Framework löschen.</span><span class="sxs-lookup"><span data-stu-id="cfca6-149">Now that you have updated cards, you can delete messages using the Bot Framework.</span></span>

## <a name="delete-messages"></a><span data-ttu-id="cfca6-150">Löschen von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="cfca6-150">Delete messages</span></span>

<span data-ttu-id="cfca6-151">Im Bot Framework hat jede Nachricht ihren eindeutigen Aktivitätsbezeichner.</span><span class="sxs-lookup"><span data-stu-id="cfca6-151">In the Bot Framework, every message has its unique activity identifier.</span></span> <span data-ttu-id="cfca6-152">Nachrichten können mit der Bot Framework-Methode gelöscht `DeleteActivity` werden.</span><span class="sxs-lookup"><span data-stu-id="cfca6-152">Messages can be deleted using the Bot Framework's `DeleteActivity` method.</span></span>

# <a name="c"></a>[<span data-ttu-id="cfca6-153">C#</span><span class="sxs-lookup"><span data-stu-id="cfca6-153">C#</span></span>](#tab/dotnet)

<span data-ttu-id="cfca6-154">Um eine Nachricht zu löschen, übergeben Sie die ID dieser Aktivität an die `DeleteActivityAsync` -Methode der `TurnContext` Klasse.</span><span class="sxs-lookup"><span data-stu-id="cfca6-154">To delete a message, pass that activity's ID to the `DeleteActivityAsync` method of the `TurnContext` class.</span></span> <span data-ttu-id="cfca6-155">Weitere Informationen finden Sie unter [TurnContext.DeleteActivityAsync-Methode](/dotnet/api/microsoft.bot.builder.turncontext.deleteactivityasync?view=botbuilder-dotnet-stable&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="cfca6-155">For more information, see [TurnContext.DeleteActivityAsync Method](/dotnet/api/microsoft.bot.builder.turncontext.deleteactivityasync?view=botbuilder-dotnet-stable&preserve-view=true).</span></span>

```csharp
foreach (var activityId in _list)
{
    await turnContext.DeleteActivityAsync(activityId, cancellationToken);
}
```

# <a name="typescript"></a>[<span data-ttu-id="cfca6-156">TypeScript</span><span class="sxs-lookup"><span data-stu-id="cfca6-156">TypeScript</span></span>](#tab/typescript)

<span data-ttu-id="cfca6-157">Um eine Nachricht zu löschen, übergeben Sie die ID dieser Aktivität an die `deleteActivity` -Methode des `TurnContext` Objekts.</span><span class="sxs-lookup"><span data-stu-id="cfca6-157">To delete a message, pass that activity's ID to the `deleteActivity` method of the `TurnContext` object.</span></span> <span data-ttu-id="cfca6-158">Weitere Informationen finden Sie unter [deleteActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#deleteactivity-string---partial-conversationreference--&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="cfca6-158">For more information, see [deleteActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#deleteactivity-string---partial-conversationreference--&preserve-view=true).</span></span>

```typescript
for (let i = 0; i < activityIds.length; i++) {
    await turnContext.deleteActivity(activityIds[i]);
}
```

# <a name="python"></a>[<span data-ttu-id="cfca6-159">Python</span><span class="sxs-lookup"><span data-stu-id="cfca6-159">Python</span></span>](#tab/python)

<span data-ttu-id="cfca6-160">Um diese Nachricht zu löschen, übergeben Sie die ID dieser Aktivität an die `delete_activity` -Methode des `TurnContext` Objekts.</span><span class="sxs-lookup"><span data-stu-id="cfca6-160">To delete that message, pass that activity's ID to the `delete_activity` method of the `TurnContext` object.</span></span> <span data-ttu-id="cfca6-161">Weitere Informationen finden Sie unter [activity-update-and-delete](https://github.com/microsoft/botbuilder-python/blob/c04ecacb22c1f4b43a671fe2f1e4782218391975/tests/teams/scenarios/activity-update-and-delete/bots/activity_update_and_delete_bot.py).</span><span class="sxs-lookup"><span data-stu-id="cfca6-161">For more information, see [activity-update-and-delete](https://github.com/microsoft/botbuilder-python/blob/c04ecacb22c1f4b43a671fe2f1e4782218391975/tests/teams/scenarios/activity-update-and-delete/bots/activity_update_and_delete_bot.py).</span></span>

```python
for each activity_id in _list:
    await TurnContext.delete_activity(activity_id)
```

# <a name="rest-api"></a>[<span data-ttu-id="cfca6-162">REST API</span><span class="sxs-lookup"><span data-stu-id="cfca6-162">REST API</span></span>](#tab/rest)

<span data-ttu-id="cfca6-163">Um eine vorhandene Aktivität in einer Unterhaltung zu löschen, schließen Sie `conversationId` das und in den `activityId` Anforderungsendpunkt ein.</span><span class="sxs-lookup"><span data-stu-id="cfca6-163">To delete an existing activity within a conversation, include the `conversationId` and `activityId` in the request endpoint.</span></span>

```http
DELETE /v3/conversations/{conversationId}/activities/{activityId}
```

| <span data-ttu-id="cfca6-164">**Anforderung und Antwort**</span><span class="sxs-lookup"><span data-stu-id="cfca6-164">**Request and response**</span></span> | <span data-ttu-id="cfca6-165">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="cfca6-165">**Description**</span></span> |
|----|----|
| <span data-ttu-id="cfca6-166">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="cfca6-166">N/A</span></span> | <span data-ttu-id="cfca6-167">Ein HTTP-Statuscode, der das Ergebnis des Vorgangs angibt.</span><span class="sxs-lookup"><span data-stu-id="cfca6-167">An HTTP status code indicating the outcome of the operation.</span></span> <span data-ttu-id="cfca6-168">Im Textkörper der Antwort ist nichts angegeben.</span><span class="sxs-lookup"><span data-stu-id="cfca6-168">Nothing is specified in the body of the response.</span></span> |

---

## <a name="code-sample"></a><span data-ttu-id="cfca6-169">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="cfca6-169">Code sample</span></span>

<span data-ttu-id="cfca6-170">Im folgenden Codebeispiel werden die Grundlagen von Unterhaltungen veranschaulicht:</span><span class="sxs-lookup"><span data-stu-id="cfca6-170">The following code sample demonstrates basics of conversations:</span></span>

| <span data-ttu-id="cfca6-171">**Beispielname**</span><span class="sxs-lookup"><span data-stu-id="cfca6-171">**Sample name**</span></span> | <span data-ttu-id="cfca6-172">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="cfca6-172">**Description**</span></span> | <span data-ttu-id="cfca6-173">**.NET**</span><span class="sxs-lookup"><span data-stu-id="cfca6-173">**.NET**</span></span> | <span data-ttu-id="cfca6-174">**Node.js**</span><span class="sxs-lookup"><span data-stu-id="cfca6-174">**Node.js**</span></span> | <span data-ttu-id="cfca6-175">**Python**</span><span class="sxs-lookup"><span data-stu-id="cfca6-175">**Python**</span></span> |
|----------------------|-----------------|--------|-------------|--------|
| <span data-ttu-id="cfca6-176">Teams Conversation Basics</span><span class="sxs-lookup"><span data-stu-id="cfca6-176">Teams Conversation Basics</span></span>  | <span data-ttu-id="cfca6-177">Veranschaulicht grundlagen von Unterhaltungen in Teams nachrichtenaktualisierung und -löschen.</span><span class="sxs-lookup"><span data-stu-id="cfca6-177">Demonstrates basics of conversations in Teams including message update and delete.</span></span> | [<span data-ttu-id="cfca6-178">View</span><span class="sxs-lookup"><span data-stu-id="cfca6-178">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot) | [<span data-ttu-id="cfca6-179">View</span><span class="sxs-lookup"><span data-stu-id="cfca6-179">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/57.teams-conversation-bot) | [<span data-ttu-id="cfca6-180">View</span><span class="sxs-lookup"><span data-stu-id="cfca6-180">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/57.teams-conversation-bot) |

## <a name="next-step"></a><span data-ttu-id="cfca6-181">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="cfca6-181">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cfca6-182">Get Teams context</span><span class="sxs-lookup"><span data-stu-id="cfca6-182">Get Teams context</span></span>](~/bots/how-to/get-teams-context.md)
