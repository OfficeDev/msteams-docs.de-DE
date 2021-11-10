---
title: Aktualisieren und Löschen von Nachrichten, die von Ihrem Bot gesendet wurden
author: WashingtonKayaker
description: Erfahren Sie, wie Sie Nachrichten, die von Ihrem Microsoft Teams Bot gesendet werden, in verschiedenen Umgebungen und mit REST-APIs mithilfe von Codebeispielen aktualisieren und löschen.
ms.topic: overview
ms.localizationpriority: medium
ms.author: anclear
ms.openlocfilehash: b92eb5c566df1d23b0228a218afa546160a3bb91
ms.sourcegitcommit: af1d0a4041ce215e7863ac12c71b6f1fa3e3ba81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2021
ms.locfileid: "60889342"
---
# <a name="update-and-delete-messages-sent-from-your-bot"></a>Aktualisieren und Löschen von Nachrichten, die von Ihrem Bot gesendet wurden

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Ihr Bot kann Nachrichten nach dem Senden dynamisch aktualisieren, anstatt sie als statische Momentaufnahmen von Daten zu verwenden. Nachrichten können auch mithilfe der Bot Framework-Methode gelöscht `DeleteActivity` werden.

## <a name="update-messages"></a>Nachricht aktualisieren

Sie können dynamische Nachrichtenupdates für Szenarien verwenden, z. B. Abfragen von Updates, Ändern verfügbarer Aktionen nach einem Tastendruck oder andere asynchrone Zustandsänderungen.

Es ist nicht erforderlich, dass die neue Nachricht mit dem ursprünglichen Typ übereinstimmt. Wenn die ursprüngliche Nachricht beispielsweise eine Anlage enthält, kann es sich bei der neuen Nachricht um eine einfache Textnachricht handeln.

# <a name="c"></a>[C#](#tab/dotnet)

Um eine vorhandene Nachricht zu aktualisieren, übergeben Sie ein neues `Activity` Objekt mit der vorhandenen Aktivitäts-ID an die Methode der `UpdateActivityAsync` `TurnContext` Klasse. Weitere Informationen finden Sie unter [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable&preserve-view=true).

```csharp
var newActivity = MessageFactory.Text("The new text for the activity");
newActivity.Id = activityId;
await turnContext.UpdateActivityAsync(newActivity, cancellationToken);
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

Um eine vorhandene Nachricht zu aktualisieren, übergeben Sie ein neues `Activity` Objekt mit der vorhandenen Aktivitäts-ID an die Methode des `updateActivity` `TurnContext` Objekts. Weitere Informationen finden Sie unter [updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--&preserve-view=true).

```typescript
const newActivity = MessageFactory.text('The new text for the activity');
newActivity.id = activityId;
await turnContext.updateActivity(newActivity);
```

# <a name="python"></a>[Python](#tab/python)

Um eine vorhandene Nachricht zu aktualisieren, übergeben Sie ein neues `Activity` Objekt mit der vorhandenen Aktivitäts-ID an die Methode der `update_activity` `TurnContext` Klasse. Siehe [TurnContextClass](/python/api/botbuilder-core/botbuilder.core.turncontext?view=botbuilder-py-latest&preserve-view=true).

```python
new_activity = MessageFactory.text("The new text for the activity")
new_activity.id = activity_id
update_result = await context.update_activity(new_activity)
```

# <a name="rest-api"></a>[REST API](#tab/rest)

> [!NOTE]

> Sie können Teams Apps in jeder Webprogrammiertechnologie entwickeln und direkt die [REST-APIs des Bot Connector-Diensts](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true)aufrufen. Dazu müssen Sie [Authentifizierungssicherheitsverfahren](/azure/bot-service/rest-api/bot-framework-rest-connector-authentication?view=azure-bot-service-4.0&preserve-view=true) mit Ihren API-Anforderungen implementieren.

Um eine vorhandene Aktivität in einer Unterhaltung zu aktualisieren, schließen Sie den `conversationId` und `activityId` in den Anforderungsendpunkt ein. Um dieses Szenario abzuschließen, müssen Sie die Aktivitäts-ID zwischenspeichern, die vom ursprünglichen Post-Aufruf zurückgegeben wird.

```http
PUT /v3/conversations/{conversationId}/activities/{activityId}
```

|Anforderung |Antwort |
|----|----|
| Ein [Activity-Objekt.](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#activity-object&preserve-view=true) | Ein [ResourceResponse-Objekt.](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#resourceresponse-object&preserve-view=true) |

---
* * *

Nachdem Sie nun Nachrichten aktualisiert haben, aktualisieren Sie die vorhandene Auswahl der Schaltfläche "Karte" für eingehende Aktivitäten.

## <a name="update-cards"></a>Karten aktualisieren

Um die vorhandene Karte auf der Schaltflächenauswahl zu aktualisieren, können Sie `ReplyToId` eingehende Aktivitäten verwenden.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

Um vorhandene Karten in einer Schaltflächenauswahl zu aktualisieren, übergeben Sie ein neues `Activity` Objekt mit aktualisierter Karte und `ReplyToId` als Aktivitäts-ID an die `UpdateActivityAsync` Methode der `TurnContext` Klasse. Siehe [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable&preserve-view=true).

```csharp
var activity = MessageFactory.Attachment(card.ToAttachment());
activity.Id = turnContext.Activity.ReplyToId;
await turnContext.UpdateActivityAsync(activity, cancellationToken);
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

Um eine vorhandene Karte in einer Schaltflächenauswahl zu aktualisieren, übergeben Sie ein neues `Activity` Objekt mit aktualisierter Karte und `replyToId` als Aktivitäts-ID an die `updateActivity` Methode des `TurnContext` Objekts. Siehe [updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--&preserve-view=true).

```typescript
const message = MessageFactory.attachment(card);
message.id = context.activity.replyToId;
await context.updateActivity(message);
```

# <a name="python"></a>[Python](#tab/python)

Um die vorhandene Karte auf einer Schaltfläche zu aktualisieren, übergeben Sie ein neues `Activity` Objekt mit aktualisierter Karte und `reply_to_id` als Aktivitäts-ID an die `update_activity` Methode der `TurnContext` Klasse. Siehe [TurnContextClass](/python/api/botbuilder-core/botbuilder.core.turncontext?view=botbuilder-py-latest&preserve-view=true).

```python
updated_activity = MessageFactory.attachment(CardFactory.hero_card(card))
updated_activity.id = turn_context.activity.reply_to_id
await turn_context.update_activity(updated_activity)
```

# <a name="rest-api"></a>[REST API](#tab/rest)

> [!NOTE]
> Sie können Teams-Apps in jeder Webprogrammiertechnologie entwickeln und direkt die [REST-APIs des Bot-Konnektordiensts](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true)aufrufen. Dazu müssen Sie [Authentifizierungssicherheitsverfahren](/azure/bot-service/rest-api/bot-framework-rest-connector-authentication?view=azure-bot-service-4.0&preserve-view=true) mit Ihren API-Anforderungen implementieren.

Um eine vorhandene Aktivität in einer Unterhaltung zu aktualisieren, schließen Sie den `conversationId` und `activityId` in den Anforderungsendpunkt ein. Um dieses Szenario abzuschließen, müssen Sie die Aktivitäts-ID zwischenspeichern, die vom ursprünglichen Post-Aufruf zurückgegeben wird.

```http
PUT /v3/conversations/{conversationId}/activities/{activityId}
```

|Anforderung |Antwort |
|----|----|
| Ein [Aktivitätsobjekt.](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#activity-object&preserve-view=true) | Ein [ResourceResponse-Objekt.](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#resourceresponse-object&preserve-view=true) |

* * *

Nachdem Sie nun Karten aktualisiert haben, können Sie Nachrichten mithilfe des Bot Frameworks löschen.

## <a name="delete-messages"></a>Löschen von Nachrichten

Im Bot Framework verfügt jede Nachricht über einen eindeutigen Aktivitätsbezeichner. Nachrichten können mithilfe der Bot Framework-Methode gelöscht `DeleteActivity` werden.

# <a name="c"></a>[C#](#tab/dotnet)

Um eine Nachricht zu löschen, übergeben Sie die ID dieser Aktivität an die `DeleteActivityAsync` Methode der `TurnContext` Klasse. Weitere Informationen finden Sie unter [TurnContext.DeleteActivityAsync-Methode.](/dotnet/api/microsoft.bot.builder.turncontext.deleteactivityasync?view=botbuilder-dotnet-stable&preserve-view=true)

```csharp
foreach (var activityId in _list)
{
    await turnContext.DeleteActivityAsync(activityId, cancellationToken);
}
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

Um eine Nachricht zu löschen, übergeben Sie die ID dieser Aktivität an die `deleteActivity` Methode des `TurnContext` Objekts. Weitere Informationen finden Sie unter [deleteActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#deleteactivity-string---partial-conversationreference--&preserve-view=true).

```typescript
for (let i = 0; i < activityIds.length; i++) {
    await turnContext.deleteActivity(activityIds[i]);
}
```

# <a name="python"></a>[Python](#tab/python)

Um diese Nachricht zu löschen, übergeben Sie die ID dieser Aktivität an die `delete_activity` Methode des `TurnContext` Objekts. Weitere Informationen finden Sie unter [Aktivitätsupdates und -löschungen.](https://github.com/microsoft/botbuilder-python/blob/c04ecacb22c1f4b43a671fe2f1e4782218391975/tests/teams/scenarios/activity-update-and-delete/bots/activity_update_and_delete_bot.py)

```python
for each activity_id in _list:
    await TurnContext.delete_activity(activity_id)
```

# <a name="rest-api"></a>[REST API](#tab/rest)

Um eine vorhandene Aktivität in einer Unterhaltung zu löschen, schließen Sie den `conversationId` und `activityId` in den Anforderungsendpunkt ein.

```http
DELETE /v3/conversations/{conversationId}/activities/{activityId}
```

| **Anforderung und Antwort** | **Beschreibung** |
|----|----|
| Nicht zutreffend | Ein HTTP-Statuscode, der das Ergebnis des Vorgangs angibt. Im Textkörper der Antwort wird nichts angegeben. |

---

## <a name="code-sample"></a>Codebeispiel

Im folgenden Codebeispiel werden die Grundlagen von Unterhaltungen veranschaulicht:

| **Beispielname** | **Beschreibung** | **.NET** | **Node.js** | **Python** |
|----------------------|-----------------|--------|-------------|--------|
| Teams Grundlagen zu Unterhaltungen  | Veranschaulicht die Grundlagen von Unterhaltungen in Teams einschließlich Nachrichtenaktualisierung und -löschung. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/57.teams-conversation-bot) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/57.teams-conversation-bot) |

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Abrufen Teams Kontexts](~/bots/how-to/get-teams-context.md)
