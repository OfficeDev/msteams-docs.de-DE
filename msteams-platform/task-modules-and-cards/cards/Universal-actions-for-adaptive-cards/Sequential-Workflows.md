---
title: Sequenzielle Workflows
description: Informationen zu sequenziellen Workflows für adaptive Karten mit universellen Aktionen mit Codebeispielen
author: surbhigupta12
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: 32200fc7a4df12567ba4000aad34e5a229dbc466
ms.sourcegitcommit: 3bfd0d2c4d83f306023adb45c8a3f829f7150b1d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2022
ms.locfileid: "65073781"
---
# <a name="sequential-workflows"></a>Sequenzielle Workflows

Adaptive Karten unterstützen jetzt sequenzielle Workflows, die bei der Benutzeraktion aktualisiert werden. Mit sequenziellen Workflows werden adaptive Karten für die Benutzeraktion aktualisiert, und Benutzer können eine Reihe von Karten durchlaufen, für die Benutzereingaben erforderlich sind. `Action.Execute` unterstützt sequenzielle Workflows, wodurch Botentwickler adaptive Karten als Reaktion auf eine Benutzeraktion zurückgeben können.

Nehmen Sie beispielsweise ein Szenario, in dem die Cafeteria eine Bestellung für ein Team oder einen Kanal annehmen möchte. Mit `Action.Execute` der Auswahl des Benutzers für verschiedene Elemente, wie Speisen und Getränke, können nacheinander aufgezeichnet werden. Benutzer können die Karten auch nach der vom Bot-Entwickler definierten Logik hin und her durchlaufen. <br/>

Die folgende Abbildung zeigt den sequenziellen Workflow:

<img src="~/assets/images/bots/sequentialWorkflow.gif" alt="Sequential Workflow" width="400"/>

Ein Benutzer kann den Workflow durchlaufen, ohne die Karte für andere Benutzer zu ändern. Der Workflow ist auch für die Durchführung von Quizfragen mit sequenziellen adaptiven Karten hilfreich. Die folgende Abbildung zeigt, dass sich verschiedene Benutzer in verschiedenen Phasen des Workflows und in den Status der Karte befinden können:

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-catering-bot.png" alt-text="Catering-Bot-Staaten" lightbox="../../../assets/images/adaptive-cards/universal-bots-catering-bot.png":::

> [!NOTE]
> Um den Fortschritt des Benutzers geräteübergreifend zu synchronisieren, verwenden Sie die `refresh` Eigenschaft in JSON für adaptive Karten.

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
Im folgenden Beispiel wird angegeben, was der Bot bei der Auswahl von Lebensmitteln oder Getränken oder der Auftragsbestätigung zurückgibt:

* Bei der Auswahl von Speisen von Karte 1 kann bot eine Karte für die Auswahl von Getränken zurückgeben, die Karte 2 ist.
* Bei Auswahl von Getränken von Karte 2 kann der Bot eine Auftragsbestätigungskarte zurückgeben, die Karte 3 ist.
* Bei Auftragsbestätigung von Karte 3 kann der Bot eine bestätigte Karte der Bestellung zurückgeben, die Karte 4 ist.

## <a name="invoke-request-received-on-bot-side"></a>Aufrufanforderung, die auf Botseite empfangen wurde

Der folgende Code enthält ein Beispiel für eine Aufrufanforderung, die auf Botseite empfangen wird:

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

Der folgende Code enthält ein Beispiel für eine Aufrufantwort zur Rückgabe adaptiver Karten:

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
| Teams-Catering-Bot | Erstellen Sie mit adaptiven Karten einen Bot, der Lebensmittelbestellungen akzeptiert. |[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-teams-catering/csharp)| Noch nicht verfügbar |
| Adaptive Karten für sequenzielle Workflows | Veranschaulichen, wie sequenzielle Workflows, benutzerspezifische Ansichten und aktuelle adaptive Karten in Bots implementiert werden. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-sequential-flow-adaptive-cards/csharp) | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-sequential-flow-adaptive-cards/nodejs) |

## <a name="see-also"></a>Siehe auch

* [Adaptive Kartenaktionen in Teams](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)
* [Wie Bots funktionieren](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true)
* [Mit Universal-Aktionen für adaptive Karten arbeiten](Work-with-universal-actions-for-adaptive-cards.md)
* [Feedback zum Ausfüllen des Formulars](~/bots/how-to/conversations/conversation-messages.md#form-completion-feedback)
