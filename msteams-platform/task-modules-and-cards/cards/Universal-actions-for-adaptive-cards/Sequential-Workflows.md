---
title: Sequenzielle Workflows
description: Informationen zu sequenziellen Workflows für adaptive Karten mit universellen Aktionen mit Codebeispielen
author: surbhigupta12
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: 468fd5168c58e7bc99b4f269e10f76484fc16b1d
ms.sourcegitcommit: c65a868744e4108b5d786de2350981e3f1f05718
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/19/2022
ms.locfileid: "62081051"
---
# <a name="sequential-workflows"></a>Sequenzielle Workflows

Adaptive Karten unterstützen jetzt sequenzielle Workflows, die bei Benutzeraktionen aktualisiert werden. Mit sequenziellen Workflows werden adaptive Karten bei Benutzeraktionen aktualisiert, und der Benutzer kann eine Reihe von Karten durchlaufen, die Benutzereingaben erfordern. `Action.Execute` unterstützt sequenzielle Workflows, mit denen Botentwickler adaptive Karten als Reaktion auf eine Benutzeraktion zurückgeben können.

Nehmen wir beispielsweise ein Szenario, in dem die Kantinen eine Bestellung für ein Team oder einen Kanal annehmen möchten. Mit `Action.Execute` der Wahl des Benutzers für verschiedene Elemente, wie z. B. Essen und Wein, kann nacheinander aufgezeichnet werden. Der Benutzer kann auch gemäß der vom Bot-Entwickler definierten Logik hin- und herblättern. <br/>

Die folgende Abbildung zeigt den sequenziellen Workflow:

<img src="~/assets/images/bots/sequentialWorkflow.gif" alt="Sequential Workflow" width="400"/>

Ein Benutzer kann den Workflow durchlaufen, ohne die Karte für andere Benutzer zu ändern. Der Workflow ist auch hilfreich für die Durchführung von Quizfragen mit sequenziellen adaptiven Karten. Die folgende Abbildung zeigt, dass sich unterschiedliche Benutzer in verschiedenen Phasen des Workflows und status der Karte befinden können:

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-catering-bot.png" alt-text="Zustände des Bots &quot;Auffüllen&quot;":::

> [!NOTE]
> Um den Fortschritt des Benutzers geräteübergreifend zu synchronisieren, verwenden Sie die `refresh` Eigenschaft in adaptiver Karten-JSON.

## <a name="sequential-workflow-for-adaptive-cards"></a>Sequenzieller Workflow für adaptive Karten

Der folgende Code enthält ein Beispiel für adaptive Karten:

```JSON
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "version": "1.4",
  "body": [
    {
      "type": "TextBlock",
      "text": "Select from food options"
    },
    { 
      "type": "ActionSet",
      "actions": [
        {
          "type": "Action.Execute",
          "title": "Chicken",
          "verb": "food",
          "data": {
              "item": "chicken"
          }
        },
        {
          "type": "Action.Execute",
          "title": "Beef",
          "verb": "food",
          "data": {
              "item": "beef"
          }
        },
        {
          "type": "Action.Execute",
          "title": "Vegan",
          "verb": "food",
          "data": {
              "item": "vegan"
          }
        }
      ]
    }
  ]
}
```

`Action.Execute`Das Aufrufen des Bots kann adaptive Karten als Antwort zurückgeben, wodurch die vorhandene Karte in Teams ersetzt wird.
Das folgende Beispiel gibt an, was der Bot bei der Auswahl oder Bestätigung der Bestellung von Menüs oder Deren Auswahl zurückgibt:

* Bei der Auswahl des Essens aus Karte 1 kann der Bot eine Karte für die Auswahl der Karte 2 zurückgeben.
* Bei der Auswahl von Karte 2 kann der Bot eine Bestätigungskarte für die Bestellung zurückgeben, die Karte 3 ist.
* Bei der Bestellbestätigung von Karte 3 kann der Bot eine bestätigte Karte zurückgeben, die Karte 4 ist.

## <a name="invoke-request-received-on-bot-side"></a>Aufrufanforderung, die auf Botseite empfangen wurde

Der folgende Code enthält ein Beispiel für eine Aufrufanforderung, die auf Botseite empfangen wurde:

```JSON
{ 
  "type": "invoke",
  "name": "adaptiveCard/action",

  // ... other properties omitted for brevity

  "value": { 
    "action": { 
      "type": "Action.Execute", 
      "id": "", 
      "verb": "food",
      "data": { 
            "item": "vegan"
      } 
    },
    "trigger": "manual" 
  }
}
```

## <a name="invoke-response-to-return-adaptive-cards"></a>Aufrufen der Antwort zum Zurückgeben adaptiver Karten

Der folgende Code enthält ein Beispiel für eine Aufrufantwort, um adaptive Karten zurückzugeben:

```C#
string cardJson = "<adaptive card json>";
var card = JsonConvert.DeserializeObject(cardJson);

var adaptiveCardResponse = JObject.FromObject(new
 {
    statusCode = 200,
    type = "application/vnd.microsoft.adaptive.card",
    value = card
 });
```

## <a name="code-samples"></a>Codebeispiele

|Beispielname | Beschreibung | .NETCore | Node.js |
|----------------|-----------------|--------------|--------------|
| Teams-Catering-Bot | Erstellen Sie einen Bot, der die Bestellung von Essen mithilfe adaptiver Karten akzeptiert. |[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-teams-catering/csharp)| Noch nicht verfügbar |
| Sequenzielle Workflows adaptive Karten | Vorführen, wie sequenzielle Workflows, benutzerspezifische Ansichten und aktuelle adaptive Karten in Bots implementiert werden. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-sequential-flow-adaptive-cards/csharp) | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-sequential-flow-adaptive-cards/nodejs) |


## <a name="see-also"></a>Siehe auch

* [Adaptive Kartenaktionen in Teams](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)
* [Wie Bots funktionieren](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true)
* [Mit Universal-Aktionen für adaptive Karten arbeiten](Work-with-universal-actions-for-adaptive-cards.md)
* [Feedback zum Ausfüllen des Formulars](~/bots/how-to/conversations/conversation-messages.md#form-completion-feedback)