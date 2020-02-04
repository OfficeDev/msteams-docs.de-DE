---
title: Aktualisieren und Löschen von Nachrichten, die von Ihrem bot gesendet wurden
author: WashingtonKayaker
description: Aktualisieren und Löschen von Nachrichten, die von Ihrem Microsoft Teams-bot gesendet wurden
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 012a6edb77f75c43cff01c58fb94e03fd4f61a85
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674466"
---
# <a name="update-and-delete-messages-sent-from-your-bot"></a><span data-ttu-id="99ac9-103">Aktualisieren und Löschen von Nachrichten, die von Ihrem bot gesendet wurden</span><span class="sxs-lookup"><span data-stu-id="99ac9-103">Update and delete messages sent from your bot</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

## <a name="updating-messages"></a><span data-ttu-id="99ac9-104">Aktualisieren von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="99ac9-104">Updating messages</span></span>

<span data-ttu-id="99ac9-105">Anstatt Ihre Nachrichten als statische Momentaufnahmen von Daten zu haben, kann Ihr bot Nachrichten nach dem Senden dynamisch aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="99ac9-105">Rather than have your messages be static snapshots of data, your bot can dynamically update messages after sending them.</span></span> <span data-ttu-id="99ac9-106">Sie können dynamische Nachrichten Aktualisierungen für Szenarien wie Abruf Aktualisierungen, das Ändern von verfügbaren Aktionen nach einer Tastendruck oder andere asynchrone Statusänderungen verwenden.</span><span class="sxs-lookup"><span data-stu-id="99ac9-106">You can use dynamic message updates for scenarios such as poll updates, modifying available actions after a button press, or any other asynchronous state change.</span></span>

<span data-ttu-id="99ac9-107">Die neue Nachricht muss nicht mit dem Original in Type übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="99ac9-107">The new message need not match the original in type.</span></span> <span data-ttu-id="99ac9-108">Wenn die ursprüngliche Nachricht beispielsweise eine Anlage enthielt, kann es sich bei der neuen Nachricht um eine einfache Textnachricht handeln.</span><span class="sxs-lookup"><span data-stu-id="99ac9-108">For instance, if the original message contained an attachment, the new message can be a simple text message.</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="99ac9-109">C#-/.net</span><span class="sxs-lookup"><span data-stu-id="99ac9-109">C#/.NET</span></span>](#tab/dotnet)

<span data-ttu-id="99ac9-110">Um eine vorhandene Nachricht zu aktualisieren, übergeben Sie `Activity` ein neues Objekt mit der vorhandenen Aktivitäts- `UpdateActivityAsync` ID an die `TurnContext` Methode der Klasse.</span><span class="sxs-lookup"><span data-stu-id="99ac9-110">To update an existing message, pass a new `Activity` object with the existing activity ID to the `UpdateActivityAsync` method of the `TurnContext` class.</span></span> <span data-ttu-id="99ac9-111">*Siehe* [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable)</span><span class="sxs-lookup"><span data-stu-id="99ac9-111">*See* [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable)</span></span>

```csharp
var newActivity = MessageFactory.Text("The new text for the activity");
newActivity.Id = activityId;
await turnContext.UpdateActivityAsync(newActivity, cancellationToken);
```

# <a name="typescriptnodejstabtypescript"></a>[<span data-ttu-id="99ac9-112">Manuskript/Node. js</span><span class="sxs-lookup"><span data-stu-id="99ac9-112">TypeScript/Node.js</span></span>](#tab/typescript)

<span data-ttu-id="99ac9-113">Um eine vorhandene Nachricht zu aktualisieren, übergeben Sie `Activity` ein neues Objekt mit der vorhandenen Aktivitäts- `updateActivity` ID an die `TurnContext` Methode des Objekts.</span><span class="sxs-lookup"><span data-stu-id="99ac9-113">To update an existing message, pass a new `Activity` object with the existing activity ID to the `updateActivity` method of the `TurnContext` object.</span></span> <span data-ttu-id="99ac9-114">*Siehe* [Update Subversion](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--)</span><span class="sxs-lookup"><span data-stu-id="99ac9-114">*See* [updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--)</span></span>

```typescript
const newActivity = MessageFactory.text('The new text for the activity');
newActivity.id = activityId;
await turnContext.updateActivity(newActivity);
```

# <a name="pythontabpython"></a>[<span data-ttu-id="99ac9-115">Python</span><span class="sxs-lookup"><span data-stu-id="99ac9-115">Python</span></span>](#tab/python)

<span data-ttu-id="99ac9-116">Um eine vorhandene Nachricht zu aktualisieren, übergeben Sie `Activity` ein neues Objekt mit der vorhandenen Aktivitäts- `update_activity` ID an die `TurnContext` Methode der Klasse.</span><span class="sxs-lookup"><span data-stu-id="99ac9-116">To update an existing message, pass a new `Activity` object with the existing activity ID to the `update_activity` method of the `TurnContext` class.</span></span> <span data-ttu-id="99ac9-117">Siehe [TurnContextClass](link to Python API ref docs).</span><span class="sxs-lookup"><span data-stu-id="99ac9-117">See [TurnContextClass](link to Python API ref docs).</span></span>

```python

new_activity = MessageFactory.text("The new text for the activity")
new_activity.id = activity_id
update_result = await context.update_activity(new_activity)

```

---

## <a name="deleting-messages"></a><span data-ttu-id="99ac9-118">Löschen von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="99ac9-118">Deleting messages</span></span>

<span data-ttu-id="99ac9-119">Im bot-Framework hat jede Nachricht eine eigene eindeutige Aktivitäts-ID.</span><span class="sxs-lookup"><span data-stu-id="99ac9-119">In the Bot Framework, every message has its own unique activity identifier.</span></span>
<span data-ttu-id="99ac9-120">Nachrichten können mithilfe der `DeleteActivity` Methode des bot-Frameworks wie hier gezeigt gelöscht werden.</span><span class="sxs-lookup"><span data-stu-id="99ac9-120">Messages can be deleted using the Bot Framework's `DeleteActivity` method as shown here.</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="99ac9-121">C#-/.net</span><span class="sxs-lookup"><span data-stu-id="99ac9-121">C#/.NET</span></span>](#tab/dotnet)

<span data-ttu-id="99ac9-122">Um diese Nachricht zu löschen, übergeben Sie die ID der Aktivität `DeleteActivityAsync` an die Methode `TurnContext` der Klasse.</span><span class="sxs-lookup"><span data-stu-id="99ac9-122">To delete that message, pass that activity's ID to the `DeleteActivityAsync` method of the `TurnContext` class.</span></span> <span data-ttu-id="99ac9-123">*Siehe* [turncontext. DeleteActivityAsync-Methode](/dotnet/api/microsoft.bot.builder.turncontext.deleteactivityasync?view=botbuilder-dotnet-stable)</span><span class="sxs-lookup"><span data-stu-id="99ac9-123">*See* [TurnContext.DeleteActivityAsync Method](/dotnet/api/microsoft.bot.builder.turncontext.deleteactivityasync?view=botbuilder-dotnet-stable)</span></span>

```csharp
foreach (var activityId in _list)
{
    await turnContext.DeleteActivityAsync(activityId, cancellationToken);
}
```

# <a name="typescriptnodejstabtypescript"></a>[<span data-ttu-id="99ac9-124">Manuskript/Node. js</span><span class="sxs-lookup"><span data-stu-id="99ac9-124">TypeScript/Node.js</span></span>](#tab/typescript)

<span data-ttu-id="99ac9-125">Um diese Nachricht zu löschen, übergeben Sie die ID der Aktivität `deleteActivity` an die Methode `TurnContext` des Objekts.</span><span class="sxs-lookup"><span data-stu-id="99ac9-125">To delete that message, pass that activity's ID to the `deleteActivity` method of the `TurnContext` object.</span></span> <span data-ttu-id="99ac9-126">*Siehe* [Delete](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#deleteactivity-string---partial-conversationreference--) -Aktion</span><span class="sxs-lookup"><span data-stu-id="99ac9-126">*See* [deleteActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#deleteactivity-string---partial-conversationreference--)</span></span>

```typescript
for (let i = 0; i < activityIds.length; i++) {
    await turnContext.deleteActivity(activityIds[i]);
}
```

# <a name="pythontabpython"></a>[<span data-ttu-id="99ac9-127">Python</span><span class="sxs-lookup"><span data-stu-id="99ac9-127">Python</span></span>](#tab/python)

<span data-ttu-id="99ac9-128">Um diese Nachricht zu löschen, übergeben Sie die ID der Aktivität `delete_activity` an die Methode `TurnContext` des Objekts.</span><span class="sxs-lookup"><span data-stu-id="99ac9-128">To delete that message, pass that activity's ID to the `delete_activity` method of the `TurnContext` object.</span></span> <span data-ttu-id="99ac9-129">Siehe [delete_activity](link to Python API ref docs).</span><span class="sxs-lookup"><span data-stu-id="99ac9-129">See [delete_activity](link to Python API ref docs).</span></span>

```python
for each activity_id in _list:
    await TurnContext.delete_activity(activity_id)
```

---

