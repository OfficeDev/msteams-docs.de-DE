---
title: Sequenzielle Workflows
description: Beispiel für sequenzielle Workflows mit universellen Aktionen
author: surbhigupta12
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: 4b37e8603d34c070bdef3003c2f8ccb0bb41550b
ms.sourcegitcommit: 1256639fa424e3833b44207ce847a245824d48e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2021
ms.locfileid: "52088875"
---
# <a name="sequential-workflows"></a>Sequenzielle Workflows

Adaptive Karten unterstützen jetzt sequenzielle Workflows, bei denen adaptive Karten auf Benutzeraktion aktualisiert werden und benutzer durch eine Reihe von Karten, die Benutzereingaben erfordern, fortschreitet. Dies wird über unterstützt, wodurch Botentwickler adaptive Karten als Reaktion auf eine `Action.Execute` Benutzeraktion zurückgeben können.

Nehmen Sie beispielsweise ein Szenario, in dem die Cafeteria eine Bestellung für ein Team oder einen Kanal übernehmen möchte. Mit der Auswahl des Benutzers für verschiedene Elemente, z. B. Essen, Getränke und so weiter, kann sequenziell `Action.Execute` aufgezeichnet werden. Der Benutzer kann auch gemäß der vom Botentwickler definierten Logik durch die Karten hin- und hergehen. <br/>

Die folgende Abbildung zeigt den sequenziellen Workflow:

<img src="~/assets/images/bots/sequentialWorkflow.gif" alt="Sequential Workflow" width="400"/>

Ein Benutzer kann seinen Workflow durchkommen, ohne die Karte für andere Benutzer zu ändern. Dies ist auch hilfreich, wenn Sie Quiz mit sequenziellen adaptiven Karten durchführen. Wie in der folgenden Abbildung gezeigt, können sich unterschiedliche Benutzer in unterschiedlichen Phasen des Workflows begnnen und unterschiedliche Zustände der Karte sehen:

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-catering-bot.png" alt-text="Zustände des Cateringbots":::

> [!NOTE]
> Um den Fortschritt des Benutzers geräteübergreifend zu synchronisieren, verwenden Sie die `refresh` Eigenschaft in Adaptive Card JSON.

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

`Action.Execute`Das Aufrufen des Bots kann adaptive Karten als Antwort zurückgeben, wodurch die vorhandene Karte in der Teams.
Das folgende Beispiel enthält, was der Bot bei der Auswahl von Essen oder Getränken oder der Auftragsbestätigung zurückgibt:

* Bei der Auswahl von Essen von Karte 1 kann bot eine Karte für die Auswahl von Getränken zurückgeben, die Karte 2 ist.
* Bei der Auswahl von Getränken aus Karte 2 kann der Bot eine Auftragsbestätigungskarte mit Karte 3 zurückgeben.
* Bei der Auftragsbestätigung von Karte 3 kann der Bot eine bestätigte Karte mit der Karte 4 zurückgeben.

## <a name="invoke-request-received-on-bot-side"></a>Aufrufen der auf Botseite empfangenen Anforderung

Der folgende Code enthält ein Beispiel für eine botseitige Aufrufanforderung:

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

Der folgende Code enthält ein Beispiel für eine Aufrufantwort zum Zurückgeben adaptiver Karten:

```C#
string cardJson = "<adaptive card json>";
var card = JsonConvert.DeserializeObject(cardJson);

var adaptiveCardResponse = JObject.FromObject(new
 {
    statusCode = 200,
    type = "application/vnd.microsoft.card.adaptive",
    value = card
 });
```

## <a name="see-also"></a>Siehe auch

* [Adaptive Kartenaktionen in Teams](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)
* [Wie Bots funktionieren](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true)
* [Arbeiten mit universellen Aktionen für adaptive Karten](Work-with-universal-actions-for-adaptive-cards.md)
