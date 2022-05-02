---
title: Aktualisieren und Löschen von Nachrichten, die von Ihrem Bot gesendet wurden
author: WashingtonKayaker
description: Erfahren Sie anhand von Codebeispielen, wie Sie Nachrichten, die von Ihrem Microsoft Teams-Bot gesendet wurden, in verschiedenen Umgebungen und mit REST-APIs aktualisieren und löschen.
ms.topic: overview
ms.localizationpriority: high
ms.author: anclear
ms.openlocfilehash: 76befe46bab8d6cc0aa3d5c0c1e2c8c0f15bf579
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111409"
---
# <a name="update-and-delete-messages-sent-from-your-bot"></a>Aktualisieren und Löschen von Nachrichten, die von Ihrem Bot gesendet wurden

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Ihr Bot kann Nachrichten nach dem Senden dynamisch aktualisieren, anstatt sie als statische Momentaufnahmen von Daten zu behalten. Nachrichten können auch mithilfe der Bot Framework-Methode `DeleteActivity` gelöscht werden.

## <a name="update-messages"></a>Nachricht aktualisieren

Sie können dynamische Nachrichtenaktualisierungen für Szenarien wie Umfrageaktualisierungen, das Ändern verfügbarer Aktionen nach einem Tastendruck oder jede andere asynchrone Zustandsänderung verwenden.

Es ist nicht erforderlich, dass die neue Nachricht mit dem ursprünglichen Typ übereinstimmt. Wenn die ursprüngliche Nachricht beispielsweise einen Anhang enthielt, kann die neue Nachricht eine einfache Textnachricht sein.

# <a name="c"></a>[C#](#tab/dotnet)

Um eine vorhandene Nachricht zu aktualisieren, übergeben Sie ein neues `Activity`-Objekt mit der vorhandenen Aktivitäts-ID an die `UpdateActivityAsync`-Methode der `TurnContext`-Klasse. Siehe [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable&preserve-view=true) für weitere Informationen.

```csharp
var newActivity = MessageFactory.Text("The new text for the activity");
newActivity.Id = activityId;
await turnContext.UpdateActivityAsync(newActivity, cancellationToken);
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

Um eine vorhandene Nachricht zu aktualisieren, übergeben Sie ein neues `Activity`-Objekt mit der vorhandenen Aktivitäts-ID an die `updateActivity`-Methode des `TurnContext`-Objekts. Siehe [updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--&preserve-view=true) für weitere Informationen.

```typescript
const newActivity = MessageFactory.text('The new text for the activity');
newActivity.id = activityId;
await turnContext.updateActivity(newActivity);
```

# <a name="python"></a>[Python](#tab/python)

Um eine vorhandene Nachricht zu aktualisieren, übergeben Sie ein neues `Activity`-Objekt mit der vorhandenen Aktivitäts-ID an die `update_activity`-Methode der `TurnContext`-Klasse. Siehe [TurnContextClass](/python/api/botbuilder-core/botbuilder.core.turncontext?view=botbuilder-py-latest&preserve-view=true).

```python
new_activity = MessageFactory.text("The new text for the activity")
new_activity.id = activity_id
update_result = await context.update_activity(new_activity)
```

# <a name="rest-api"></a>[REST API](#tab/rest)

> [!NOTE]
> Sie können Microsoft Teams-Apps in jeder beliebigen Webprogrammiertechnologie entwickeln und die [Bot Connector-Dienst-REST-APIs](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true) direkt aufrufen. Dazu müssen Sie mit Ihren API-Anforderungen [Authentifizierungssicherheitsverfahren](/azure/bot-service/rest-api/bot-framework-rest-connector-authentication?view=azure-bot-service-4.0&preserve-view=true) implementieren.

Um eine vorhandene Aktivität innerhalb einer Unterhaltung zu aktualisieren, schließen Sie `conversationId` und `activityId` in den Anforderungsendpunkt ein. Um dieses Szenario abzuschließen, müssen Sie die vom ursprünglichen POST-Aufruf zurückgegebene Aktivitäts-ID zwischenspeichern.

```http
PUT /v3/conversations/{conversationId}/activities/{activityId}
```

|Anforderung |Antwort |
|----|----|
| Ein [Activity](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#activity-object&preserve-view=true)-Objekt | Ein [ResourceResponse](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#resourceresponse-object&preserve-view=true)-Objekt |

---
---

Nachdem Sie Nachrichten aktualisiert haben, aktualisieren Sie die vorhandene Karte bei der Schaltflächenauswahl für eingehende Aktivitäten.

## <a name="update-cards"></a>Karten aktualisieren

Um die vorhandene Karte bei der Schaltflächenauswahl zu aktualisieren, können Sie `ReplyToId` von eingehenden Aktivitäten verwenden.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

Um eine vorhandene Karte bei der Schaltflächenauswahl zu aktualisieren, übergeben Sie ein neues `Activity`-Objekt mit aktualisierter Karte und `ReplyToId` als Aktivitäts-ID an die `UpdateActivityAsync`-Methode der `TurnContext`-Klasse. Siehe [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable&preserve-view=true).

```csharp
var activity = MessageFactory.Attachment(card.ToAttachment());
activity.Id = turnContext.Activity.ReplyToId;
await turnContext.UpdateActivityAsync(activity, cancellationToken);
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

Um eine vorhandene Karte bei der Schaltflächenauswahl zu aktualisieren, übergeben Sie ein neues `Activity`-Objekt mit aktualisierter Karte und `replyToId` als Aktivitäts-ID an die `updateActivity`-Methode des `TurnContext`-Objekts. Siehe [updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--&preserve-view=true).

```typescript
const message = MessageFactory.attachment(card);
message.id = context.activity.replyToId;
await context.updateActivity(message);
```

# <a name="python"></a>[Python](#tab/python)

Um eine vorhandene Karte beim Klick auf eine Schaltfläche zu aktualisieren, übergeben Sie ein neues `Activity`-Objekt mit aktualisierter Karte und `reply_to_id` als Aktivitäts-ID an die `update_activity`-Methode der `TurnContext`-Klasse. Siehe [TurnContextClass](/python/api/botbuilder-core/botbuilder.core.turncontext?view=botbuilder-py-latest&preserve-view=true).

```python
updated_activity = MessageFactory.attachment(CardFactory.hero_card(card))
updated_activity.id = turn_context.activity.reply_to_id
await turn_context.update_activity(updated_activity)
```

# <a name="rest-api"></a>[REST API](#tab/rest)

> [!NOTE]
> Sie können Microsoft Teams-Apps in jeder beliebigen Webprogrammiertechnologie entwickeln und die [Bot Connector-Dienst-REST-APIs](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true) direkt aufrufen. Dazu müssen Sie mit Ihren API-Anforderungen [Authentifizierungssicherheitsverfahren](/azure/bot-service/rest-api/bot-framework-rest-connector-authentication?view=azure-bot-service-4.0&preserve-view=true) implementieren.

Um eine vorhandene Aktivität innerhalb einer Unterhaltung zu aktualisieren, schließen Sie `conversationId` und `activityId` in den Anforderungsendpunkt ein. Um dieses Szenario abzuschließen, müssen Sie die vom ursprünglichen POST-Aufruf zurückgegebene Aktivitäts-ID zwischenspeichern.

```http
PUT /v3/conversations/{conversationId}/activities/{activityId}
```

|Anforderung |Antwort |
|----|----|
| Ein [activity](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#activity-object&preserve-view=true)-Objekt | Ein [ResourceResponse](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#resourceresponse-object&preserve-view=true)-Objekt |

---

Nachdem Sie Karten aktualisiert haben, können Sie Nachrichten mithilfe des Bot Framework löschen.

## <a name="delete-messages"></a>Löschen von Nachrichten

Im Bot Framework hat jede Nachricht ihren eindeutigen Aktivitätsbezeichner. Nachrichten können mithilfe der Bot Framework-Methode `DeleteActivity` gelöscht werden.

# <a name="c"></a>[C#](#tab/dotnet)

Um eine Nachricht zu löschen, übergeben Sie die ID dieser Aktivität an die `DeleteActivityAsync`-Methode der `TurnContext`-Klasse. Siehe [TurnContext.DeleteActivityAsync-Methode](/dotnet/api/microsoft.bot.builder.turncontext.deleteactivityasync?view=botbuilder-dotnet-stable&preserve-view=true) für weitere Informationen.

```csharp
foreach (var activityId in _list)
{
    await turnContext.DeleteActivityAsync(activityId, cancellationToken);
}
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

Um eine Nachricht zu löschen, übergeben Sie die ID dieser Aktivität an die `deleteActivity`-Methode des `TurnContext`-Objekts. Siehe [deleteActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#deleteactivity-string---partial-conversationreference--&preserve-view=true) für weitere Informationen.

```typescript
for (let i = 0; i < activityIds.length; i++) {
    await turnContext.deleteActivity(activityIds[i]);
}
```

# <a name="python"></a>[Python](#tab/python)

Um die Nachricht zu löschen, übergeben Sie die ID dieser Aktivität an die `delete_activity`-Methode des `TurnContext`-Objekts. Siehe [activity-update-and-delete](https://github.com/microsoft/botbuilder-python/blob/c04ecacb22c1f4b43a671fe2f1e4782218391975/tests/teams/scenarios/activity-update-and-delete/bots/activity_update_and_delete_bot.py) für weitere Informationen.

```python
for each activity_id in _list:
    await TurnContext.delete_activity(activity_id)
```

# <a name="rest-api"></a>[REST API](#tab/rest)

Um eine vorhandene Aktivität innerhalb einer Unterhaltung zu löschen, schließen Sie `conversationId` und `activityId` in den Anforderungsendpunkt ein.

```http
DELETE /v3/conversations/{conversationId}/activities/{activityId}
```

| **Anforderung und Antwort** | **Beschreibung** |
|----|----|
| Nicht zutreffend | Ein HTTP-Statuscode, der das Ergebnis des Vorgangs angibt. Im Textkörper der Antwort ist nichts angegeben. |

---

## <a name="code-sample"></a>Codebeispiel

Im folgenden Codebeispiel werden die Grundaspekte von Unterhaltungen veranschaulicht:

| **Beispielname** | **Beschreibung** | **.NET** | **Node.js** | **Python** |
|----------------------|-----------------|--------|-------------|--------|
| Grundlagen zu Teams-Unterhaltungen  | Veranschaulicht die Grundaspekte von Unterhaltungen in Microsoft Teams einschließlich Nachrichtenaktualisierung und -löschung. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/57.teams-conversation-bot) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/57.teams-conversation-bot) |

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Microsoft Teams-Kontext abrufen](~/bots/how-to/get-teams-context.md)
