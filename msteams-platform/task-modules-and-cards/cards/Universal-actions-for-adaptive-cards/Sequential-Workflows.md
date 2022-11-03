---
title: Sequenzielle Workflows
description: In diesem Modul erfahren Sie mehr über sequenzielle Workflows für adaptive Karten mithilfe von Universellen Aktionen mit Codebeispielen.
author: surbhigupta12
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: bd3fbf560099487ba45c2454460b82b852b675fa
ms.sourcegitcommit: c3601696cced9aadc764f1e734646ee7711f154c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2022
ms.locfileid: "68833191"
---
# <a name="sequential-workflows"></a>Sequenzielle Workflows

Adaptive Karten unterstützen jetzt sequenzielle Workflows, die bei Benutzeraktionen aktualisiert werden. Mithilfe von sequenziellen Workflows werden adaptive Karten bei Benutzeraktionen aktualisiert, und der Benutzer kann eine Reihe von Karten durchlaufen, die eine Benutzereingabe erfordern. `Action.Execute` unterstützt sequenzielle Workflows, mit denen Botentwickler adaptive Karten als Reaktion auf eine Benutzeraktion zurückgeben können.

Nehmen Sie beispielsweise ein Szenario, in dem die Cafeteria eine Bestellung für ein Team oder einen Kanal annehmen möchte. Mit `Action.Execute` der Auswahl des Benutzers für verschiedene Elemente, wie z. B. Speisen und Getränke, kann sequenziell aufgezeichnet werden. Der Benutzer kann auch die Karten gemäß der vom Botentwickler definierten Logik durchlaufen. <br/>

Die folgende Abbildung zeigt den sequenziellen Workflow:

<img src="~/assets/images/bots/sequentialWorkflow.gif" alt="Sequential Workflow" width="400"/>

Ein Benutzer kann seinen Workflow durchlaufen, ohne die Karte für andere Benutzer zu ändern. Der Workflow ist auch nützlich für die Durchführung von Quizzes mit sequenziellen adaptiven Karten. Die folgende Abbildung zeigt, dass sich unterschiedliche Benutzer in verschiedenen Phasen des Workflows und Zuständen der Karte befinden können:

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-catering-bot.png" alt-text="Zustände des Cateringbots" lightbox="../../../assets/images/adaptive-cards/universal-bots-catering-bot.png":::

> [!NOTE]
> Um den Fortschritt des Benutzers geräteübergreifend zu synchronisieren, verwenden Sie die `refresh` -Eigenschaft in JSON für adaptive Karten.

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

`Action.Execute` Durch aufrufen des Bots können adaptive Karten als Antwort zurückgegeben werden, wodurch die vorhandene Karte in Teams ersetzt wird.
Das folgende Beispiel zeigt, was der Bot bei der Auswahl von Speisen oder Getränken oder auf einer Bestellbestätigung zurückgibt:

* Auf der Essensauswahl von Karte 1 kann bot eine Karte für die Auswahl von Getränken zurückgeben, die Karte 2 ist.
* Bei der Getränkeauswahl aus Karte 2 kann der Bot eine Bestellbestätigungskarte zurückgeben, die Karte 3 ist.
* Bei der Auftragsbestätigung von Karte 3 kann der Bot eine bestellbestätigunge Karte zurückgeben, die Karte 4 ist.

## <a name="invoke-request-received-on-bot-side"></a>Auf botseitiger Seite empfangene Aufrufanforderung

Der folgende Code enthält ein Beispiel für eine Aufrufanforderung, die auf der Botseite empfangen wurde:

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
| Teams-Catering-Bot | Erstellen Sie einen Bot, der mit adaptiven Karten eine Bestellung annimmt. |[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-teams-catering/csharp)| – |
| Adaptive Karten für sequenzielle Workflows | Veranschaulichen, wie sequenzielle Workflows, benutzerspezifische Ansichten und aktuelle adaptive Karten in Bots implementiert werden. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-sequential-flow-adaptive-cards/csharp) | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-sequential-flow-adaptive-cards/nodejs) |

## <a name="see-also"></a>Siehe auch

* [Adaptive Kartenaktionen in Teams](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)
* [Wie Bots funktionieren](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true)
* [Mit Universal-Aktionen für adaptive Karten arbeiten](Work-with-universal-actions-for-adaptive-cards.md)
* [Feedback zum Ausfüllen des Formulars](~/bots/how-to/conversations/conversation-messages.md#form-completion-feedback)
