---
title: Sequenzielle Workflows
description: Beispiel für sequenzielle Workflows mit universellen Aktionen
author: surbhigupta12
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: 7f285bf76aac4f0ca276321aee2ce4b4e5c3e7e4
ms.sourcegitcommit: 9ef3b415cbba484c2201abe9c6927e08d974388e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52555402"
---
# <a name="sequential-workflows"></a>Sequenzielle Workflows

Adaptive Karten unterstützen jetzt sequenzielle Workflows, wenn Adaptive Karten auf Benutzeraktionen aktualisiert werden und der Benutzer eine Reihe von Karten durchlaufen kann, die Benutzereingaben erfordern. Dies wird durch `Action.Execute` unterstützt, wodurch Bot-Entwickler Adaptive Cards als Reaktion auf eine Benutzeraktion zurückgeben können.

Nehmen Sie beispielsweise ein Szenario, in dem die Cafeteria eine Bestellung für ein Team oder einen Kanal annehmen möchte. Mit `Action.Execute` der Wahl des Benutzers für verschiedene Artikel, wie Essen, Getränke, und so weiter kann nacheinander aufgezeichnet werden. Der Benutzer kann auch durch die Karten hin und her gehen, wie es die vom Bot-Entwickler definierte Logik betrifft. <br/>

Die folgende Abbildung zeigt den Sequenziellen Workflow:

<img src="~/assets/images/bots/sequentialWorkflow.gif" alt="Sequential Workflow" width="400"/>

Ein Benutzer kann seinen Workflow durchlaufen, ohne die Karte für andere Benutzer zu ändern. Dies ist auch nützlich für die Durchführung von Quizfragen mit sequenziellen Adaptive Cards. Wie in der folgenden Abbildung gezeigt, können sich verschiedene Benutzer in verschiedenen Phasen des Workflows befinden und sehen unterschiedliche Zustände der Karte:

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-catering-bot.png" alt-text="Catering-Bot-Staaten":::

> [!NOTE]
> Um den Fortschritt des Benutzers geräteübergreifend zu synchronisieren, verwenden Sie die `refresh` Eigenschaft in Adaptive Card JSON.

## <a name="sequential-workflow-for-adaptive-cards"></a>Sequenzieller Workflow für adaptive Karten

Der folgende Code enthält ein Beispiel für Adaptive Cards:

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

`Action.Execute`Aufrufen des Bots kann Adaptive Cards als Antwort zurückgegeben werden, die die vorhandene Karte in Teams ersetzt.
Das folgende Beispiel enthält, was der Bot bei der Auswahl von Speisen oder Getränken oder der Auftragsbestätigung zurückgibt:

* Bei der Speisenauswahl aus Karte 1 kann der Bot eine Karte für die Auswahl der Getränke zurückgeben, die Karte 2 ist.
* Bei der Getränkeauswahl aus Karte 2 kann der Bot eine Auftragsbestätigungskarte mit Karte 3 zurückgeben.
* Auf Auftragsbestätigung von Karte 3 kann Bot eine auftragsbestätigte Karte mit Karte 4 zurückgeben.

## <a name="invoke-request-received-on-bot-side"></a>Aufrufanforderung, die auf Bot-Seite empfangen wurde

Der folgende Code enthält ein Beispiel für eine Aufrufanforderung, die auf Bot-Seite empfangen wurde:

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

## <a name="invoke-response-to-return-adaptive-cards"></a>Aufrufen der Antwort auf die Rückgabe von Adaptive Cards

Der folgende Code enthält ein Beispiel für eine Aufrufantwort zum Zurückgeben von Adaptive Cards:

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

## <a name="see-also"></a>Siehe auch

* [Adaptive Kartenaktionen in Teams](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)
* [Wie Bots funktionieren](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true)
* [Mit Universal-Aktionen für adaptive Karten arbeiten](Work-with-universal-actions-for-adaptive-cards.md)
