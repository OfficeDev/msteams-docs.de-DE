---
title: Aktualisieren und Löschen von Nachrichten, die von Ihrem bot gesendet wurden
author: WashingtonKayaker
description: Aktualisieren und Löschen von Nachrichten, die von Ihrem Microsoft Teams-bot gesendet wurden
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 222409fa0d02a571b7295dedb0c60b1ca3f90cca
ms.sourcegitcommit: 61edf47c9dd1dbc1df03d0d9fb83bfedca4c423b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2020
ms.locfileid: "43914609"
---
# <a name="update-and-delete-messages-sent-from-your-bot"></a><span data-ttu-id="7ee9b-103">Aktualisieren und Löschen von Nachrichten, die von Ihrem bot gesendet wurden</span><span class="sxs-lookup"><span data-stu-id="7ee9b-103">Update and delete messages sent from your bot</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

## <a name="updating-messages"></a><span data-ttu-id="7ee9b-104">Aktualisieren von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="7ee9b-104">Updating messages</span></span>

<span data-ttu-id="7ee9b-105">Anstatt Ihre Nachrichten als statische Momentaufnahmen von Daten zu haben, kann Ihr bot Nachrichten nach dem Senden dynamisch aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="7ee9b-105">Rather than have your messages be static snapshots of data, your bot can dynamically update messages after sending them.</span></span> <span data-ttu-id="7ee9b-106">Sie können dynamische Nachrichten Aktualisierungen für Szenarien wie Abruf Aktualisierungen, das Ändern von verfügbaren Aktionen nach einer Tastendruck oder andere asynchrone Statusänderungen verwenden.</span><span class="sxs-lookup"><span data-stu-id="7ee9b-106">You can use dynamic message updates for scenarios such as poll updates, modifying available actions after a button press, or any other asynchronous state change.</span></span>

<span data-ttu-id="7ee9b-107">Die neue Nachricht muss nicht mit dem Original in Type übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="7ee9b-107">The new message need not match the original in type.</span></span> <span data-ttu-id="7ee9b-108">Wenn die ursprüngliche Nachricht beispielsweise eine Anlage enthielt, kann es sich bei der neuen Nachricht um eine einfache Textnachricht handeln.</span><span class="sxs-lookup"><span data-stu-id="7ee9b-108">For instance, if the original message contained an attachment, the new message can be a simple text message.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="7ee9b-109">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="7ee9b-109">C#/.NET</span></span>](#tab/dotnet)

<span data-ttu-id="7ee9b-110">Um eine vorhandene Nachricht zu aktualisieren, übergeben Sie `Activity` ein neues Objekt mit der vorhandenen Aktivitäts- `UpdateActivityAsync` ID an die `TurnContext` Methode der Klasse.</span><span class="sxs-lookup"><span data-stu-id="7ee9b-110">To update an existing message, pass a new `Activity` object with the existing activity ID to the `UpdateActivityAsync` method of the `TurnContext` class.</span></span> <span data-ttu-id="7ee9b-111">*Siehe* [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable)</span><span class="sxs-lookup"><span data-stu-id="7ee9b-111">*See* [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable)</span></span>

```csharp
var newActivity = MessageFactory.Text("The new text for the activity");
newActivity.Id = activityId;
await turnContext.UpdateActivityAsync(newActivity, cancellationToken);
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="7ee9b-112">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="7ee9b-112">TypeScript/Node.js</span></span>](#tab/typescript)

<span data-ttu-id="7ee9b-113">Um eine vorhandene Nachricht zu aktualisieren, übergeben Sie `Activity` ein neues Objekt mit der vorhandenen Aktivitäts- `updateActivity` ID an die `TurnContext` Methode des Objekts.</span><span class="sxs-lookup"><span data-stu-id="7ee9b-113">To update an existing message, pass a new `Activity` object with the existing activity ID to the `updateActivity` method of the `TurnContext` object.</span></span> <span data-ttu-id="7ee9b-114">*Siehe* [Update Subversion](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--)</span><span class="sxs-lookup"><span data-stu-id="7ee9b-114">*See* [updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--)</span></span>

```typescript
const newActivity = MessageFactory.text('The new text for the activity');
newActivity.id = activityId;
await turnContext.updateActivity(newActivity);
```

# <a name="python"></a>[<span data-ttu-id="7ee9b-115">Python</span><span class="sxs-lookup"><span data-stu-id="7ee9b-115">Python</span></span>](#tab/python)

<span data-ttu-id="7ee9b-116">Um eine vorhandene Nachricht zu aktualisieren, übergeben Sie `Activity` ein neues Objekt mit der vorhandenen Aktivitäts- `update_activity` ID an die `TurnContext` Methode der Klasse.</span><span class="sxs-lookup"><span data-stu-id="7ee9b-116">To update an existing message, pass a new `Activity` object with the existing activity ID to the `update_activity` method of the `TurnContext` class.</span></span> <span data-ttu-id="7ee9b-117">Siehe [TurnContextClass](link to Python API ref docs).</span><span class="sxs-lookup"><span data-stu-id="7ee9b-117">See [TurnContextClass](link to Python API ref docs).</span></span>

```python

new_activity = MessageFactory.text("The new text for the activity")
new_activity.id = activity_id
update_result = await context.update_activity(new_activity)

```

---

## <a name="deleting-messages"></a><span data-ttu-id="7ee9b-118">Löschen von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="7ee9b-118">Deleting messages</span></span>

<span data-ttu-id="7ee9b-119">Im bot-Framework hat jede Nachricht eine eigene eindeutige Aktivitäts-ID.</span><span class="sxs-lookup"><span data-stu-id="7ee9b-119">In the Bot Framework, every message has its own unique activity identifier.</span></span>
<span data-ttu-id="7ee9b-120">Nachrichten können mithilfe der `DeleteActivity` Methode des bot-Frameworks wie hier gezeigt gelöscht werden.</span><span class="sxs-lookup"><span data-stu-id="7ee9b-120">Messages can be deleted using the Bot Framework's `DeleteActivity` method as shown here.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="7ee9b-121">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="7ee9b-121">C#/.NET</span></span>](#tab/dotnet)

<span data-ttu-id="7ee9b-122">Um diese Nachricht zu löschen, übergeben Sie die ID der Aktivität `DeleteActivityAsync` an die Methode `TurnContext` der Klasse.</span><span class="sxs-lookup"><span data-stu-id="7ee9b-122">To delete that message, pass that activity's ID to the `DeleteActivityAsync` method of the `TurnContext` class.</span></span> <span data-ttu-id="7ee9b-123">*Siehe* [turncontext. DeleteActivityAsync-Methode](/dotnet/api/microsoft.bot.builder.turncontext.deleteactivityasync?view=botbuilder-dotnet-stable)</span><span class="sxs-lookup"><span data-stu-id="7ee9b-123">*See* [TurnContext.DeleteActivityAsync Method](/dotnet/api/microsoft.bot.builder.turncontext.deleteactivityasync?view=botbuilder-dotnet-stable)</span></span>

```csharp
foreach (var activityId in _list)
{
    await turnContext.DeleteActivityAsync(activityId, cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="7ee9b-124">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="7ee9b-124">TypeScript/Node.js</span></span>](#tab/typescript)

<span data-ttu-id="7ee9b-125">Um diese Nachricht zu löschen, übergeben Sie die ID der Aktivität `deleteActivity` an die Methode `TurnContext` des Objekts.</span><span class="sxs-lookup"><span data-stu-id="7ee9b-125">To delete that message, pass that activity's ID to the `deleteActivity` method of the `TurnContext` object.</span></span> <span data-ttu-id="7ee9b-126">*Siehe* [Delete](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#deleteactivity-string---partial-conversationreference--) -Aktion</span><span class="sxs-lookup"><span data-stu-id="7ee9b-126">*See* [deleteActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#deleteactivity-string---partial-conversationreference--)</span></span>

```typescript
for (let i = 0; i < activityIds.length; i++) {
    await turnContext.deleteActivity(activityIds[i]);
}
```

# <a name="python"></a>[<span data-ttu-id="7ee9b-127">Python</span><span class="sxs-lookup"><span data-stu-id="7ee9b-127">Python</span></span>](#tab/python)

<span data-ttu-id="7ee9b-128">Um diese Nachricht zu löschen, übergeben Sie die ID der Aktivität `delete_activity` an die Methode `TurnContext` des Objekts.</span><span class="sxs-lookup"><span data-stu-id="7ee9b-128">To delete that message, pass that activity's ID to the `delete_activity` method of the `TurnContext` object.</span></span> <span data-ttu-id="7ee9b-129">Siehe [Activity-Update-and-Delete](https://github.com/microsoft/botbuilder-python/blob/c04ecacb22c1f4b43a671fe2f1e4782218391975/tests/teams/scenarios/activity-update-and-delete/bots/activity_update_and_delete_bot.py).</span><span class="sxs-lookup"><span data-stu-id="7ee9b-129">See [activity-update-and-delete](https://github.com/microsoft/botbuilder-python/blob/c04ecacb22c1f4b43a671fe2f1e4782218391975/tests/teams/scenarios/activity-update-and-delete/bots/activity_update_and_delete_bot.py).</span></span>

```python
for each activity_id in _list:
    await TurnContext.delete_activity(activity_id)
```

---

