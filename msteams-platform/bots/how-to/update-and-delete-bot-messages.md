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
# <a name="update-and-delete-messages-sent-from-your-bot"></a>Aktualisieren und Löschen von Nachrichten, die von Ihrem bot gesendet wurden

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

## <a name="updating-messages"></a>Aktualisieren von Nachrichten

Anstatt Ihre Nachrichten als statische Momentaufnahmen von Daten zu haben, kann Ihr bot Nachrichten nach dem Senden dynamisch aktualisieren. Sie können dynamische Nachrichten Aktualisierungen für Szenarien wie Abruf Aktualisierungen, das Ändern von verfügbaren Aktionen nach einer Tastendruck oder andere asynchrone Statusänderungen verwenden.

Die neue Nachricht muss nicht mit dem Original in Type übereinstimmen. Wenn die ursprüngliche Nachricht beispielsweise eine Anlage enthielt, kann es sich bei der neuen Nachricht um eine einfache Textnachricht handeln.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

Um eine vorhandene Nachricht zu aktualisieren, übergeben Sie `Activity` ein neues Objekt mit der vorhandenen Aktivitäts- `UpdateActivityAsync` ID an die `TurnContext` Methode der Klasse. *Siehe* [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable)

```csharp
var newActivity = MessageFactory.Text("The new text for the activity");
newActivity.Id = activityId;
await turnContext.UpdateActivityAsync(newActivity, cancellationToken);
```

# <a name="typescriptnodejs"></a>[TypeScript/Node.js](#tab/typescript)

Um eine vorhandene Nachricht zu aktualisieren, übergeben Sie `Activity` ein neues Objekt mit der vorhandenen Aktivitäts- `updateActivity` ID an die `TurnContext` Methode des Objekts. *Siehe* [Update Subversion](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--)

```typescript
const newActivity = MessageFactory.text('The new text for the activity');
newActivity.id = activityId;
await turnContext.updateActivity(newActivity);
```

# <a name="python"></a>[Python](#tab/python)

Um eine vorhandene Nachricht zu aktualisieren, übergeben Sie `Activity` ein neues Objekt mit der vorhandenen Aktivitäts- `update_activity` ID an die `TurnContext` Methode der Klasse. Siehe [TurnContextClass](link to Python API ref docs).

```python

new_activity = MessageFactory.text("The new text for the activity")
new_activity.id = activity_id
update_result = await context.update_activity(new_activity)

```

# <a name="rest-api"></a>[REST API](#tab/rest)

>[!NOTE]
>Sie können Microsoft Teams-apps in jeder beliebigen webprogrammier Technologie entwickeln und direkt die [Rest-APIs des bot Connector-Diensts](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0)aufrufen. Dazu müssen Sie [Authentifizierungs](/azure/bot-service/rest-api/bot-framework-rest-connector-authentication?view=azure-bot-service-4.0) Sicherheitsverfahren mit ihren API-Anforderungen implementieren.

Um eine vorhandene Aktivität in einer Unterhaltung zu aktualisieren, `conversationId` schließen `activityId` Sie die und in den Anforderungs Endpunkt ein. Um dieses Szenario abzuschließen, sollten Sie die vom ursprünglichen Post-Aufruf zurückgegebene Aktivitäts-ID Zwischenspeichern.

```http
PUT /v3/conversations/{conversationId}/activities/{activityId}
```

| | |
|----|----|
| **Anforderungstext** | Ein [Activity](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#activity-object) -Objekt |
| **gibt zurück** | Ein [ResourceResponse](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#resourceresponse-object) -Objekt |

---

## <a name="deleting-messages"></a>Löschen von Nachrichten

Im bot-Framework hat jede Nachricht eine eigene eindeutige Aktivitäts-ID.
Nachrichten können mithilfe der `DeleteActivity` Methode des bot-Frameworks wie hier gezeigt gelöscht werden.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

Um diese Nachricht zu löschen, übergeben Sie die ID der Aktivität `DeleteActivityAsync` an die Methode `TurnContext` der Klasse. *Siehe* [turncontext. DeleteActivityAsync-Methode](/dotnet/api/microsoft.bot.builder.turncontext.deleteactivityasync?view=botbuilder-dotnet-stable)

```csharp
foreach (var activityId in _list)
{
    await turnContext.DeleteActivityAsync(activityId, cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[TypeScript/Node.js](#tab/typescript)

Um diese Nachricht zu löschen, übergeben Sie die ID der Aktivität `deleteActivity` an die Methode `TurnContext` des Objekts. *Siehe* [Delete](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#deleteactivity-string---partial-conversationreference--) -Aktion

```typescript
for (let i = 0; i < activityIds.length; i++) {
    await turnContext.deleteActivity(activityIds[i]);
}
```

# <a name="python"></a>[Python](#tab/python)

Um diese Nachricht zu löschen, übergeben Sie die ID der Aktivität `delete_activity` an die Methode `TurnContext` des Objekts. Siehe [Activity-Update-and-Delete](https://github.com/microsoft/botbuilder-python/blob/c04ecacb22c1f4b43a671fe2f1e4782218391975/tests/teams/scenarios/activity-update-and-delete/bots/activity_update_and_delete_bot.py).

```python
for each activity_id in _list:
    await TurnContext.delete_activity(activity_id)
```

# <a name="rest-api"></a>[REST API](#tab/rest)

 Wenn Sie eine vorhandene Aktivität in einer Unterhaltung löschen möchten `conversationId` , `activityId` schließen Sie die und in den Anforderungs Endpunkt ein.

```http
DELETE /v3/conversations/{conversationId}/activities/{activityId}
```

| | |
|----|----|
| **Anforderungstext** | n/v |
| **gibt zurück** | Ein HTTP-Status Code, der das Ergebnis des Vorgangs angibt. Im Text der Antwort wird nichts angegeben. |

---
