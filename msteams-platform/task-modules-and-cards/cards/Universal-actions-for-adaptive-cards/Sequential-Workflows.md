---
title: Sequenzielle Workflows
description: Beispiel für sequenzielle Workflows mit universellen Aktionen
author: surbhigupta12
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: f36e65133572569cd01de1053044336c810656f3
ms.sourcegitcommit: 999f5c607671e088ea8a461fa7dbb63f8d61c39b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2021
ms.locfileid: "52649646"
---
# <a name="sequential-workflows"></a><span data-ttu-id="775eb-103">Sequenzielle Workflows</span><span class="sxs-lookup"><span data-stu-id="775eb-103">Sequential Workflows</span></span>

<span data-ttu-id="775eb-104">Adaptive Karten unterstützen jetzt sequenzielle Workflows, bei denen adaptive Karten auf Benutzeraktion aktualisiert werden und benutzer durch eine Reihe von Karten, die Benutzereingaben erfordern, fortschreitet.</span><span class="sxs-lookup"><span data-stu-id="775eb-104">Adaptive Cards now support Sequential Workflows that is when Adaptive Cards are updated on user action and user can progress through a series of cards that require user input.</span></span> <span data-ttu-id="775eb-105">Dies wird über unterstützt, wodurch Botentwickler adaptive Karten als Reaktion auf eine `Action.Execute` Benutzeraktion zurückgeben können.</span><span class="sxs-lookup"><span data-stu-id="775eb-105">This is supported through `Action.Execute`, which allows bot developers to return Adaptive Cards in response to a user action.</span></span>

<span data-ttu-id="775eb-106">Nehmen Sie beispielsweise ein Szenario, in dem die Cafeteria eine Bestellung für ein Team oder einen Kanal übernehmen möchte.</span><span class="sxs-lookup"><span data-stu-id="775eb-106">For example, take a scenario where the cafeteria wants to take an order for a team or channel.</span></span> <span data-ttu-id="775eb-107">Mit der Auswahl des Benutzers für verschiedene Elemente, z. B. Essen, Getränke und so weiter, kann sequenziell `Action.Execute` aufgezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="775eb-107">With `Action.Execute` the user's choice for various items, such as food, drinks, and so on can be recorded sequentially.</span></span> <span data-ttu-id="775eb-108">Der Benutzer kann auch gemäß der vom Botentwickler definierten Logik durch die Karten hin- und hergehen.</span><span class="sxs-lookup"><span data-stu-id="775eb-108">User can also go back and forth through the cards as per the logic defined by the bot developer.</span></span> <br/>

<span data-ttu-id="775eb-109">Die folgende Abbildung zeigt den sequenziellen Workflow:</span><span class="sxs-lookup"><span data-stu-id="775eb-109">The following image shows the Sequential Workflow:</span></span>

<img src="~/assets/images/bots/sequentialWorkflow.gif" alt="Sequential Workflow" width="400"/>

<span data-ttu-id="775eb-110">Ein Benutzer kann seinen Workflow durchkommen, ohne die Karte für andere Benutzer zu ändern.</span><span class="sxs-lookup"><span data-stu-id="775eb-110">A user can progress through their workflow without modifying the card for other users.</span></span> <span data-ttu-id="775eb-111">Dies ist auch hilfreich, wenn Sie Quiz mit sequenziellen adaptiven Karten durchführen.</span><span class="sxs-lookup"><span data-stu-id="775eb-111">This is also useful for conducting quizzes using sequential Adaptive Cards.</span></span> <span data-ttu-id="775eb-112">Wie in der folgenden Abbildung gezeigt, können sich unterschiedliche Benutzer in unterschiedlichen Phasen des Workflows begnnen und unterschiedliche Zustände der Karte sehen:</span><span class="sxs-lookup"><span data-stu-id="775eb-112">As shown in the following image, different users can be at different stages of the workflow and they see different states of the card:</span></span>

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-catering-bot.png" alt-text="Zustände des Cateringbots":::

> [!NOTE]
> <span data-ttu-id="775eb-114">Um den Fortschritt des Benutzers geräteübergreifend zu synchronisieren, verwenden Sie die `refresh` Eigenschaft in Adaptive Card JSON.</span><span class="sxs-lookup"><span data-stu-id="775eb-114">In order to sync the user's progress across devices, use the `refresh` property in Adaptive Card JSON.</span></span>

## <a name="sequential-workflow-for-adaptive-cards"></a><span data-ttu-id="775eb-115">Sequenzieller Workflow für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="775eb-115">Sequential Workflow for Adaptive Cards</span></span>

<span data-ttu-id="775eb-116">Der folgende Code enthält ein Beispiel für adaptive Karten:</span><span class="sxs-lookup"><span data-stu-id="775eb-116">The following code provides an example of Adaptive Cards:</span></span>

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

<span data-ttu-id="775eb-117">`Action.Execute`Das Aufrufen des Bots kann adaptive Karten als Antwort zurückgeben, wodurch die vorhandene Karte in der Teams.</span><span class="sxs-lookup"><span data-stu-id="775eb-117">`Action.Execute` invoking the bot can return Adaptive Cards as a response, which replaces the existing card in Teams.</span></span>
<span data-ttu-id="775eb-118">Das folgende Beispiel enthält, was der Bot bei der Auswahl von Essen oder Getränken oder der Auftragsbestätigung zurückgibt:</span><span class="sxs-lookup"><span data-stu-id="775eb-118">The following example provides what the bot returns on food or drink selection or order confirmation:</span></span>

* <span data-ttu-id="775eb-119">Bei der Auswahl von Essen von Karte 1 kann bot eine Karte für die Auswahl von Getränken zurückgeben, die Karte 2 ist.</span><span class="sxs-lookup"><span data-stu-id="775eb-119">On food selection from Card 1, bot can return a card for selection of drinks that is Card 2.</span></span>
* <span data-ttu-id="775eb-120">Bei der Auswahl von Getränken aus Karte 2 kann der Bot eine Auftragsbestätigungskarte mit Karte 3 zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="775eb-120">On drink selection from Card 2, bot can return an order confirmation card that is Card 3.</span></span>
* <span data-ttu-id="775eb-121">Bei der Auftragsbestätigung von Karte 3 kann der Bot eine bestätigte Karte mit der Karte 4 zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="775eb-121">On order confirmation from Card 3, bot can return an order confirmed card that is Card 4.</span></span>

## <a name="invoke-request-received-on-bot-side"></a><span data-ttu-id="775eb-122">Aufrufen der auf Botseite empfangenen Anforderung</span><span class="sxs-lookup"><span data-stu-id="775eb-122">Invoke request received on bot side</span></span>

<span data-ttu-id="775eb-123">Der folgende Code enthält ein Beispiel für eine botseitige Aufrufanforderung:</span><span class="sxs-lookup"><span data-stu-id="775eb-123">The following code provides an example of an invoke request received on bot side:</span></span>

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

## <a name="invoke-response-to-return-adaptive-cards"></a><span data-ttu-id="775eb-124">Aufrufen der Antwort zum Zurückgeben adaptiver Karten</span><span class="sxs-lookup"><span data-stu-id="775eb-124">Invoke response to return Adaptive Cards</span></span>

<span data-ttu-id="775eb-125">Der folgende Code enthält ein Beispiel für eine Aufrufantwort zum Zurückgeben adaptiver Karten:</span><span class="sxs-lookup"><span data-stu-id="775eb-125">The following code provides an example of an invoke response to return Adaptive Cards:</span></span>

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

## <a name="code-sample"></a><span data-ttu-id="775eb-126">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="775eb-126">Code sample</span></span>

|<span data-ttu-id="775eb-127">Beispielname</span><span class="sxs-lookup"><span data-stu-id="775eb-127">Sample name</span></span> | <span data-ttu-id="775eb-128">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="775eb-128">Description</span></span> | <span data-ttu-id="775eb-129">. NETCore</span><span class="sxs-lookup"><span data-stu-id="775eb-129">.NETCore</span></span> |
|----------------|-----------------|--------------|
| <span data-ttu-id="775eb-130">Teams-Catering-Bot</span><span class="sxs-lookup"><span data-stu-id="775eb-130">Teams catering bot</span></span> | <span data-ttu-id="775eb-131">Erstellen Sie einen einfachen Bot, der die Essensbestellung mit adaptiven Karten akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="775eb-131">Create a simple bot that accepts food order using Adaptive Cards.</span></span> |[<span data-ttu-id="775eb-132">View</span><span class="sxs-lookup"><span data-stu-id="775eb-132">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-teams-catering/csharp)|

## <a name="see-also"></a><span data-ttu-id="775eb-133">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="775eb-133">See also</span></span>

* [<span data-ttu-id="775eb-134">Adaptive Kartenaktionen in Teams</span><span class="sxs-lookup"><span data-stu-id="775eb-134">Adaptive Card actions in Teams</span></span>](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)
* [<span data-ttu-id="775eb-135">Wie Bots funktionieren</span><span class="sxs-lookup"><span data-stu-id="775eb-135">How bots work</span></span>](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true)
* [<span data-ttu-id="775eb-136">Mit Universal-Aktionen für adaptive Karten arbeiten</span><span class="sxs-lookup"><span data-stu-id="775eb-136">Work with Universal Actions for Adaptive Cards</span></span>](Work-with-universal-actions-for-adaptive-cards.md)
