---
title: Aktualisieren und Löschen von Nachrichten, die von Ihrem Bot gesendet werden
author: WashingtonKayaker
description: Aktualisieren und Löschen von Nachrichten, die von Ihrem Microsoft Teams-Bot gesendet werden
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 3b94c3f0851c62adb905121afb47389144bccffd
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696315"
---
# <a name="update-and-delete-messages-sent-from-your-bot"></a>Aktualisieren und Löschen von Nachrichten, die von Ihrem Bot gesendet werden

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Ihr Bot kann Nachrichten nach dem Senden dynamisch aktualisieren, anstatt sie als statische Momentaufnahmen von Daten zu verwenden. Nachrichten können auch mit der Bot Framework-Methode gelöscht `DeleteActivity` werden.

## <a name="update-messages"></a>Nachricht aktualisieren

Sie können dynamische Nachrichtenupdates für Szenarien verwenden, z. B. Abrufupdates, Ändern verfügbarer Aktionen nach dem Drücken einer Schaltfläche oder andere asynchrone Statusänderung.

Es ist nicht erforderlich, dass die neue Nachricht mit dem originalen Typ übereinstimmen muss. Wenn die ursprüngliche Nachricht beispielsweise eine Anlage enthält, kann die neue Nachricht eine einfache Textnachricht sein.

# <a name="c"></a>[C#](#tab/dotnet)

Um eine vorhandene Nachricht zu aktualisieren, übergeben Sie ein neues Objekt mit der vorhandenen `Activity` Aktivitäts-ID an die `UpdateActivityAsync` -Methode der `TurnContext` Klasse. Weitere Informationen finden Sie unter [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable&preserve-view=true).

```csharp
var newActivity = MessageFactory.Text("The new text for the activity");
newActivity.Id = activityId;
await turnContext.UpdateActivityAsync(newActivity, cancellationToken);
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

Um eine vorhandene Nachricht zu aktualisieren, übergeben Sie ein neues Objekt mit der vorhandenen Aktivitäts-ID `Activity` an die `updateActivity` -Methode des `TurnContext` Objekts. Weitere Informationen finden Sie unter [updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--&preserve-view=true).

```typescript
const newActivity = MessageFactory.text('The new text for the activity');
newActivity.id = activityId;
await turnContext.updateActivity(newActivity);
```

# <a name="python"></a>[Python](#tab/python)

Um eine vorhandene Nachricht zu aktualisieren, übergeben Sie ein neues Objekt mit der vorhandenen `Activity` Aktivitäts-ID an die `update_activity` -Methode der `TurnContext` Klasse. Weitere Informationen finden Sie unter [TurnContextClass](/python/api/botbuilder-core/botbuilder.core.turncontext?view=botbuilder-py-latest&preserve-view=true).

```python

new_activity = MessageFactory.text("The new text for the activity")
new_activity.id = activity_id
update_result = await context.update_activity(new_activity)

```

# <a name="rest-api"></a>[REST API](#tab/rest)

> [!NOTE]
> Sie können Teams-Apps in jeder beliebigen Webprogrammiertechnologie entwickeln und direkt den [Botconnectordienst REST-APIs aufrufen.](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true) Dazu müssen Sie Authentifizierungssicherheitsverfahren mit Ihren API-Anforderungen implementieren. [](/azure/bot-service/rest-api/bot-framework-rest-connector-authentication?view=azure-bot-service-4.0&preserve-view=true)

Um eine vorhandene Aktivität in einer Unterhaltung zu aktualisieren, schließen Sie `conversationId` das und in den `activityId` Anforderungsendpunkt ein. Zum Abschließen dieses Szenarios müssen Sie die vom ursprünglichen Postanruf zurückgegebene Aktivitäts-ID zwischenspeichern.

```http
PUT /v3/conversations/{conversationId}/activities/{activityId}
```

|Anforderungstext | Rückgabewerte |
|----|----|
| Ein [Aktivitätsobjekt](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#activity-object&preserve-view=true) | Ein [ResourceResponse-Objekt](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#resourceresponse-object&preserve-view=true) |

---
* * *

Nachdem Sie Nachrichten aktualisiert haben, aktualisieren Sie die vorhandene Karte auf Schaltflächenauswahl für eingehende Aktivitäten.

## <a name="update-cards"></a>Aktualisieren von Karten

Zum Aktualisieren der vorhandenen Kartenauswahl für Schaltflächen können Sie eingehende `ReplyToId` Aktivitäten verwenden.

# <a name="c"></a>[C#](#tab/dotnet)

Um vorhandene Karten für eine Schaltflächenauswahl zu aktualisieren, übergeben Sie ein neues Objekt mit aktualisierter Karte und als Aktivitäts-ID an die `Activity` `ReplyToId` `UpdateActivityAsync` -Methode der `TurnContext` Klasse. Weitere [Informationen finden Sie unter TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable&preserve-view=true).

```csharp
var activity = MessageFactory.Attachment(card.ToAttachment());
activity.Id = turnContext.Activity.ReplyToId;
await turnContext.UpdateActivityAsync(activity, cancellationToken);
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

Um vorhandene Karten für eine Schaltflächenauswahl zu aktualisieren, übergeben Sie ein neues Objekt mit aktualisierter Karte und als Aktivitäts-ID an die `Activity` `replyToId` `updateActivity` -Methode des `TurnContext` Objekts. Weitere [Informationen finden Sie unter updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--&preserve-view=true).

```typescript
const message = MessageFactory.attachment(card);
message.id = context.activity.replyToId;
await context.updateActivity(message);
```

# <a name="python"></a>[Python](#tab/python)

Um vorhandene Karten für eine Schaltflächenauswahl zu aktualisieren, übergeben Sie ein neues Objekt mit aktualisierter Karte und als Aktivitäts-ID an die `Activity` `reply_to_id` `update_activity` -Methode der `TurnContext` Klasse. Weitere [Informationen finden Sie unter TurnContextClass](/python/api/botbuilder-core/botbuilder.core.turncontext?view=botbuilder-py-latest&preserve-view=true).

```python
updated_activity = MessageFactory.attachment(CardFactory.hero_card(card))
updated_activity.id = turn_context.activity.reply_to_id
await turn_context.update_activity(updated_activity)

```

# <a name="rest-api"></a>[REST API](#tab/rest)

> [!NOTE]
> Sie können Teams-Apps in jeder beliebigen Webprogrammiertechnologie entwickeln und direkt den [Botconnectordienst REST-APIs aufrufen.](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true) Dazu müssen Sie Authentifizierungssicherheitsverfahren mit Ihren API-Anforderungen implementieren. [](/azure/bot-service/rest-api/bot-framework-rest-connector-authentication?view=azure-bot-service-4.0&preserve-view=true)

Um eine vorhandene Aktivität in einer Unterhaltung zu aktualisieren, schließen Sie `conversationId` das und in den `activityId` Anforderungsendpunkt ein. Zum Abschließen dieses Szenarios müssen Sie die vom ursprünglichen Postanruf zurückgegebene Aktivitäts-ID zwischenspeichern.

```http
PUT /v3/conversations/{conversationId}/activities/{activityId}
```

|Anforderung |Antwort |
|----|----|
| Ein [Aktivitätsobjekt.](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#activity-object&preserve-view=true) | Ein [ResourceResponse-Objekt.](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#resourceresponse-object&preserve-view=true) |

* * *

Nachdem Sie karten aktualisiert haben, können Sie Nachrichten mit dem Bot Framework löschen.

## <a name="delete-messages"></a>Löschen von Nachrichten

Im Bot Framework hat jede Nachricht ihren eindeutigen Aktivitätsbezeichner. Nachrichten können mit der Bot Framework-Methode gelöscht `DeleteActivity` werden.

# <a name="c"></a>[C#](#tab/dotnet)

Um eine Nachricht zu löschen, übergeben Sie die ID dieser Aktivität an die `DeleteActivityAsync` -Methode der `TurnContext` Klasse. Weitere Informationen finden Sie unter [TurnContext.DeleteActivityAsync-Methode](/dotnet/api/microsoft.bot.builder.turncontext.deleteactivityasync?view=botbuilder-dotnet-stable&preserve-view=true).

```csharp
foreach (var activityId in _list)
{
    await turnContext.DeleteActivityAsync(activityId, cancellationToken);
}
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

Um eine Nachricht zu löschen, übergeben Sie die ID dieser Aktivität an die `deleteActivity` -Methode des `TurnContext` Objekts. Weitere Informationen finden Sie unter [deleteActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#deleteactivity-string---partial-conversationreference--&preserve-view=true).

```typescript
for (let i = 0; i < activityIds.length; i++) {
    await turnContext.deleteActivity(activityIds[i]);
}
```

# <a name="python"></a>[Python](#tab/python)

Um diese Nachricht zu löschen, übergeben Sie die ID dieser Aktivität an die `delete_activity` -Methode des `TurnContext` Objekts. Weitere Informationen finden Sie unter [activity-update-and-delete](https://github.com/microsoft/botbuilder-python/blob/c04ecacb22c1f4b43a671fe2f1e4782218391975/tests/teams/scenarios/activity-update-and-delete/bots/activity_update_and_delete_bot.py).

```python
for each activity_id in _list:
    await TurnContext.delete_activity(activity_id)
```

# <a name="rest-api"></a>[REST API](#tab/rest)

Um eine vorhandene Aktivität in einer Unterhaltung zu löschen, schließen Sie `conversationId` das und in den `activityId` Anforderungsendpunkt ein.

```http
DELETE /v3/conversations/{conversationId}/activities/{activityId}
```

|Anforderung |Antwort |
|----|----|
| Nicht zutreffend | Ein HTTP-Statuscode, der das Ergebnis des Vorgangs angibt. Im Textkörper der Antwort ist nichts angegeben. |

---

## <a name="code-sample"></a>Codebeispiel

Im folgenden Codebeispiel werden die Grundlagen von Unterhaltungen veranschaulicht:

| Beispielname           | Beschreibung                                                                      | .NET    | Node.js   | Python  |
|:----------------------|:---------------------------------------------------------------------------------|:--------|:-------------|:--------|
|Grundlagen der Teams-Unterhaltung  | Veranschaulicht grundlagen von Unterhaltungen in Teams, einschließlich Nachrichtenaktualisierung und -löschen.|[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/57.teams-conversation-bot) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/57.teams-conversation-bot)|

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Get Teams context](~/bots/how-to/get-teams-context.md)

