---
title: Aktualisieren und Löschen von Nachrichten, die von Ihrem bot gesendet wurden
author: WashingtonKayaker
description: Aktualisieren und Löschen von Nachrichten, die von Ihrem Microsoft Teams-bot gesendet wurden
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 46994c6810197002ef1c108af4f725426395b37f
ms.sourcegitcommit: 2b1fd50466d807869fd173371ba7dfd82a0064ac
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2020
ms.locfileid: "43957187"
---
# <a name="update-and-delete-messages-sent-from-your-bot"></a><span data-ttu-id="f72b0-103">Aktualisieren und Löschen von Nachrichten, die von Ihrem bot gesendet wurden</span><span class="sxs-lookup"><span data-stu-id="f72b0-103">Update and delete messages sent from your bot</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

## <a name="updating-messages"></a><span data-ttu-id="f72b0-104">Aktualisieren von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="f72b0-104">Updating messages</span></span>

<span data-ttu-id="f72b0-105">Anstatt Ihre Nachrichten als statische Momentaufnahmen von Daten zu haben, kann Ihr bot Nachrichten nach dem Senden dynamisch aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="f72b0-105">Rather than have your messages be static snapshots of data, your bot can dynamically update messages after sending them.</span></span> <span data-ttu-id="f72b0-106">Sie können dynamische Nachrichten Aktualisierungen für Szenarien wie Abruf Aktualisierungen, das Ändern von verfügbaren Aktionen nach einer Tastendruck oder andere asynchrone Statusänderungen verwenden.</span><span class="sxs-lookup"><span data-stu-id="f72b0-106">You can use dynamic message updates for scenarios such as poll updates, modifying available actions after a button press, or any other asynchronous state change.</span></span>

<span data-ttu-id="f72b0-107">Die neue Nachricht muss nicht mit dem Original in Type übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="f72b0-107">The new message need not match the original in type.</span></span> <span data-ttu-id="f72b0-108">Wenn die ursprüngliche Nachricht beispielsweise eine Anlage enthielt, kann es sich bei der neuen Nachricht um eine einfache Textnachricht handeln.</span><span class="sxs-lookup"><span data-stu-id="f72b0-108">For instance, if the original message contained an attachment, the new message can be a simple text message.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="f72b0-109">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="f72b0-109">C#/.NET</span></span>](#tab/dotnet)

<span data-ttu-id="f72b0-110">Um eine vorhandene Nachricht zu aktualisieren, übergeben Sie `Activity` ein neues Objekt mit der vorhandenen Aktivitäts- `UpdateActivityAsync` ID an die `TurnContext` Methode der Klasse.</span><span class="sxs-lookup"><span data-stu-id="f72b0-110">To update an existing message, pass a new `Activity` object with the existing activity ID to the `UpdateActivityAsync` method of the `TurnContext` class.</span></span> <span data-ttu-id="f72b0-111">*Siehe* [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable)</span><span class="sxs-lookup"><span data-stu-id="f72b0-111">*See* [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable)</span></span>

```csharp
var newActivity = MessageFactory.Text("The new text for the activity");
newActivity.Id = activityId;
await turnContext.UpdateActivityAsync(newActivity, cancellationToken);
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="f72b0-112">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="f72b0-112">TypeScript/Node.js</span></span>](#tab/typescript)

<span data-ttu-id="f72b0-113">Um eine vorhandene Nachricht zu aktualisieren, übergeben Sie `Activity` ein neues Objekt mit der vorhandenen Aktivitäts- `updateActivity` ID an die `TurnContext` Methode des Objekts.</span><span class="sxs-lookup"><span data-stu-id="f72b0-113">To update an existing message, pass a new `Activity` object with the existing activity ID to the `updateActivity` method of the `TurnContext` object.</span></span> <span data-ttu-id="f72b0-114">*Siehe* [Update Subversion](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--)</span><span class="sxs-lookup"><span data-stu-id="f72b0-114">*See* [updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--)</span></span>

```typescript
const newActivity = MessageFactory.text('The new text for the activity');
newActivity.id = activityId;
await turnContext.updateActivity(newActivity);
```

# <a name="python"></a>[<span data-ttu-id="f72b0-115">Python</span><span class="sxs-lookup"><span data-stu-id="f72b0-115">Python</span></span>](#tab/python)

<span data-ttu-id="f72b0-116">Um eine vorhandene Nachricht zu aktualisieren, übergeben Sie `Activity` ein neues Objekt mit der vorhandenen Aktivitäts- `update_activity` ID an die `TurnContext` Methode der Klasse.</span><span class="sxs-lookup"><span data-stu-id="f72b0-116">To update an existing message, pass a new `Activity` object with the existing activity ID to the `update_activity` method of the `TurnContext` class.</span></span> <span data-ttu-id="f72b0-117">Siehe [TurnContextClass](link to Python API ref docs).</span><span class="sxs-lookup"><span data-stu-id="f72b0-117">See [TurnContextClass](link to Python API ref docs).</span></span>

```python

new_activity = MessageFactory.text("The new text for the activity")
new_activity.id = activity_id
update_result = await context.update_activity(new_activity)

```

# <a name="rest-api"></a>[<span data-ttu-id="f72b0-118">REST API</span><span class="sxs-lookup"><span data-stu-id="f72b0-118">REST API</span></span>](#tab/rest)

>[!NOTE]
><span data-ttu-id="f72b0-119">Sie können Microsoft Teams-apps in jeder beliebigen webprogrammier Technologie entwickeln und direkt die [Rest-APIs des bot Connector-Diensts](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0)aufrufen.</span><span class="sxs-lookup"><span data-stu-id="f72b0-119">You can develop Teams apps in any web-programming technology and directly call the [Bot Connector service REST APIs](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0).</span></span> <span data-ttu-id="f72b0-120">Dazu müssen Sie [Authentifizierungs](/azure/bot-service/rest-api/bot-framework-rest-connector-authentication?view=azure-bot-service-4.0) Sicherheitsverfahren mit ihren API-Anforderungen implementieren.</span><span class="sxs-lookup"><span data-stu-id="f72b0-120">To do so, you'll need to implement [Authentication](/azure/bot-service/rest-api/bot-framework-rest-connector-authentication?view=azure-bot-service-4.0) security procedures with your API requests.</span></span>

<span data-ttu-id="f72b0-121">Um eine vorhandene Aktivität in einer Unterhaltung zu aktualisieren, `conversationId` schließen `activityId` Sie die und in den Anforderungs Endpunkt ein.</span><span class="sxs-lookup"><span data-stu-id="f72b0-121">To update an existing activity within a conversation, include the `conversationId` and `activityId` in the request endpoint.</span></span> <span data-ttu-id="f72b0-122">Um dieses Szenario abzuschließen, sollten Sie die vom ursprünglichen Post-Aufruf zurückgegebene Aktivitäts-ID Zwischenspeichern.</span><span class="sxs-lookup"><span data-stu-id="f72b0-122">To complete this scenario, you should cache the activity ID returned by the original POST call.</span></span>

```http
PUT /v3/conversations/{conversationId}/activities/{activityId}
```

| | |
|----|----|
| <span data-ttu-id="f72b0-123">**Anforderungstext**</span><span class="sxs-lookup"><span data-stu-id="f72b0-123">**Request body**</span></span> | <span data-ttu-id="f72b0-124">Ein [Activity](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#activity-object) -Objekt</span><span class="sxs-lookup"><span data-stu-id="f72b0-124">An [Activity](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#activity-object) object</span></span> |
| <span data-ttu-id="f72b0-125">**gibt zurück**</span><span class="sxs-lookup"><span data-stu-id="f72b0-125">**Returns**</span></span> | <span data-ttu-id="f72b0-126">Ein [ResourceResponse](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#resourceresponse-object) -Objekt</span><span class="sxs-lookup"><span data-stu-id="f72b0-126">A [ResourceResponse](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#resourceresponse-object) object</span></span> |

---

## <a name="deleting-messages"></a><span data-ttu-id="f72b0-127">Löschen von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="f72b0-127">Deleting messages</span></span>

<span data-ttu-id="f72b0-128">Im bot-Framework hat jede Nachricht eine eigene eindeutige Aktivitäts-ID.</span><span class="sxs-lookup"><span data-stu-id="f72b0-128">In the Bot Framework, every message has its own unique activity identifier.</span></span>
<span data-ttu-id="f72b0-129">Nachrichten können mithilfe der `DeleteActivity` Methode des bot-Frameworks wie hier gezeigt gelöscht werden.</span><span class="sxs-lookup"><span data-stu-id="f72b0-129">Messages can be deleted using the Bot Framework's `DeleteActivity` method as shown here.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="f72b0-130">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="f72b0-130">C#/.NET</span></span>](#tab/dotnet)

<span data-ttu-id="f72b0-131">Um diese Nachricht zu löschen, übergeben Sie die ID der Aktivität `DeleteActivityAsync` an die Methode `TurnContext` der Klasse.</span><span class="sxs-lookup"><span data-stu-id="f72b0-131">To delete that message, pass that activity's ID to the `DeleteActivityAsync` method of the `TurnContext` class.</span></span> <span data-ttu-id="f72b0-132">*Siehe* [turncontext. DeleteActivityAsync-Methode](/dotnet/api/microsoft.bot.builder.turncontext.deleteactivityasync?view=botbuilder-dotnet-stable)</span><span class="sxs-lookup"><span data-stu-id="f72b0-132">*See* [TurnContext.DeleteActivityAsync Method](/dotnet/api/microsoft.bot.builder.turncontext.deleteactivityasync?view=botbuilder-dotnet-stable)</span></span>

```csharp
foreach (var activityId in _list)
{
    await turnContext.DeleteActivityAsync(activityId, cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="f72b0-133">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="f72b0-133">TypeScript/Node.js</span></span>](#tab/typescript)

<span data-ttu-id="f72b0-134">Um diese Nachricht zu löschen, übergeben Sie die ID der Aktivität `deleteActivity` an die Methode `TurnContext` des Objekts.</span><span class="sxs-lookup"><span data-stu-id="f72b0-134">To delete that message, pass that activity's ID to the `deleteActivity` method of the `TurnContext` object.</span></span> <span data-ttu-id="f72b0-135">*Siehe* [Delete](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#deleteactivity-string---partial-conversationreference--) -Aktion</span><span class="sxs-lookup"><span data-stu-id="f72b0-135">*See* [deleteActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#deleteactivity-string---partial-conversationreference--)</span></span>

```typescript
for (let i = 0; i < activityIds.length; i++) {
    await turnContext.deleteActivity(activityIds[i]);
}
```

# <a name="python"></a>[<span data-ttu-id="f72b0-136">Python</span><span class="sxs-lookup"><span data-stu-id="f72b0-136">Python</span></span>](#tab/python)

<span data-ttu-id="f72b0-137">Um diese Nachricht zu löschen, übergeben Sie die ID der Aktivität `delete_activity` an die Methode `TurnContext` des Objekts.</span><span class="sxs-lookup"><span data-stu-id="f72b0-137">To delete that message, pass that activity's ID to the `delete_activity` method of the `TurnContext` object.</span></span> <span data-ttu-id="f72b0-138">Siehe [Activity-Update-and-Delete](https://github.com/microsoft/botbuilder-python/blob/c04ecacb22c1f4b43a671fe2f1e4782218391975/tests/teams/scenarios/activity-update-and-delete/bots/activity_update_and_delete_bot.py).</span><span class="sxs-lookup"><span data-stu-id="f72b0-138">See [activity-update-and-delete](https://github.com/microsoft/botbuilder-python/blob/c04ecacb22c1f4b43a671fe2f1e4782218391975/tests/teams/scenarios/activity-update-and-delete/bots/activity_update_and_delete_bot.py).</span></span>

```python
for each activity_id in _list:
    await TurnContext.delete_activity(activity_id)
```

# <a name="rest-api"></a>[<span data-ttu-id="f72b0-139">REST API</span><span class="sxs-lookup"><span data-stu-id="f72b0-139">REST API</span></span>](#tab/rest)

 <span data-ttu-id="f72b0-140">Wenn Sie eine vorhandene Aktivität in einer Unterhaltung löschen möchten `conversationId` , `activityId` schließen Sie die und in den Anforderungs Endpunkt ein.</span><span class="sxs-lookup"><span data-stu-id="f72b0-140">To delete an existing activity within a conversation, include the `conversationId` and `activityId` in the request endpoint.</span></span>

```http
DELETE /v3/conversations/{conversationId}/activities/{activityId}
```

| | |
|----|----|
| <span data-ttu-id="f72b0-141">**Anforderungstext**</span><span class="sxs-lookup"><span data-stu-id="f72b0-141">**Request body**</span></span> | <span data-ttu-id="f72b0-142">n/v</span><span class="sxs-lookup"><span data-stu-id="f72b0-142">n/a</span></span> |
| <span data-ttu-id="f72b0-143">**gibt zurück**</span><span class="sxs-lookup"><span data-stu-id="f72b0-143">**Returns**</span></span> | <span data-ttu-id="f72b0-144">Ein HTTP-Status Code, der das Ergebnis des Vorgangs angibt.</span><span class="sxs-lookup"><span data-stu-id="f72b0-144">An HTTP Status code that indicates the outcome of the operation.</span></span> <span data-ttu-id="f72b0-145">Im Text der Antwort wird nichts angegeben.</span><span class="sxs-lookup"><span data-stu-id="f72b0-145">Nothing is specified in the body of the response.</span></span> |

---
