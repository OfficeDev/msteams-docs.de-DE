---
title: Benutzerspezifische Ansichten
description: Beispiel für benutzerspezifische Ansichten mithilfe universeller Aktionen
author: surbhigupta12
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: 984b32511dda544942df11f7c5d8a25cca8e9a8a
ms.sourcegitcommit: 1256639fa424e3833b44207ce847a245824d48e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2021
ms.locfileid: "52088837"
---
# <a name="user-specific-views"></a><span data-ttu-id="c1403-103">Benutzerspezifische Ansichten</span><span class="sxs-lookup"><span data-stu-id="c1403-103">User Specific Views</span></span>

<span data-ttu-id="c1403-104">Wenn adaptive Karten in einer Teams gesendet wurden, sehen alle Benutzer den exakt gleichen Karteninhalt.</span><span class="sxs-lookup"><span data-stu-id="c1403-104">Earlier if Adaptive Cards was sent in a Teams conversation, all users see the exact same card content.</span></span> <span data-ttu-id="c1403-105">Mit der Einführung des Universellen Aktionsmodells und für adaptive Karten können Botentwickler benutzern nun benutzerspezifische Ansichten `refresh` adaptiver Karten bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="c1403-105">With the introduction of the Universal Actions model and `refresh` for Adaptive Cards, bot developers can now provide User Specific Views of Adaptive Cards to users.</span></span> <span data-ttu-id="c1403-106">Dieselbe adaptive Karte kann jetzt auf eine benutzerspezifische adaptive Karte aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="c1403-106">The same Adaptive Card can now refresh to a User Specific Adaptive Card.</span></span>

<span data-ttu-id="c1403-107">Beispielsweise möchte Megan, ein Sicherheitsinspektor bei Contoso, einen Vorfall erstellen und alex zuweisen.</span><span class="sxs-lookup"><span data-stu-id="c1403-107">For example, Megan, a safety inspector at Contoso, wants to create an incident and assign it to Alex.</span></span> <span data-ttu-id="c1403-108">Außerdem möchte sie, dass jeder im Team über den Vorfall informiert ist.</span><span class="sxs-lookup"><span data-stu-id="c1403-108">She also wants everyone in the team to be aware about the incident.</span></span> <span data-ttu-id="c1403-109">Megan verwendet die Nachrichtenerweiterung contoso incident reporting powered by Universal Actions for Adaptive Cards.</span><span class="sxs-lookup"><span data-stu-id="c1403-109">Megan uses Contoso incident reporting message extension powered by Universal Actions for Adaptive Cards.</span></span>

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-incident-management.png" alt-text="Benutzerspezifische Ansichten":::

## <a name="user-specific-views-for-adaptive-cards"></a><span data-ttu-id="c1403-111">Benutzerspezifische Ansichten für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="c1403-111">User Specific Views for Adaptive Cards</span></span>

<span data-ttu-id="c1403-112">Der folgende Code enthält ein Beispiel für adaptive Karten:</span><span class="sxs-lookup"><span data-stu-id="c1403-112">The following code provides an example of Adaptive Cards:</span></span>

```JSON
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "originator":"c9b4352b-a76b-43b9-88ff-80edddaa243b",
  "version": "1.4",
  "refresh": {
    "action": {
      "type": "Action.Execute",
      "title": "Refresh",
      "verb": "editOrResolveView",
      "data": {
              "refresh info": "<refresh info>"
    },
    "userIds": ["<Megan's user MRI>", "<Alex's user MRI>"]
  },
  "body": [
    {
      "type": "TextBlock",
      "text": "Incident 1234"
    },
    {
      "type": "TextBlock",
      "text": "Incident details: <incident details>"
    }
  ]
}
```

<span data-ttu-id="c1403-113">**Aktualisieren Sie benutzerspezifische Ansichten, und rufen Sie Anforderungen an den Bot auf, um adaptive Karten zu senden**</span><span class="sxs-lookup"><span data-stu-id="c1403-113">**To send Adaptive Cards, refresh User Specific Views, and invoke requests to the bot**</span></span>

1. <span data-ttu-id="c1403-114">Wenn Megan einen neuen Vorfall erstellt, sendet der Bot die adaptive Karte oder eine gemeinsame Karte mit Vorfalldetails in der Teams Unterhaltung.</span><span class="sxs-lookup"><span data-stu-id="c1403-114">When Megan creates a new incident, the bot sends the Adaptive Card or common card with incident details in the Teams conversation.</span></span>
2. <span data-ttu-id="c1403-115">Jetzt wird diese Karte automatisch auf benutzerspezifische Ansicht für Megan und Alex aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="c1403-115">Now this card automatically refreshes to User Specific View for Megan and Alex.</span></span> <span data-ttu-id="c1403-116">Die Benutzer-MRIs von Alex und Megan werden in eigenschaft der Eigenschaft der `userIds` `refresh` adaptiven Karten-JSON hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="c1403-116">Alex's and Megan's user MRIs are added in `userIds` property of `refresh` property of the Adaptive Card JSON.</span></span> <span data-ttu-id="c1403-117">Die Karte bleibt für andere Benutzer in der Unterhaltung gleich.</span><span class="sxs-lookup"><span data-stu-id="c1403-117">The card remains the same for other users in the conversation.</span></span>
3. <span data-ttu-id="c1403-118">Für Megan löst die automatische Aktualisierung eine `adaptiveCard/action` Aufrufanforderung an den Bot aus.</span><span class="sxs-lookup"><span data-stu-id="c1403-118">For Megan, automatic refresh triggers an `adaptiveCard/action` invoke request to the bot.</span></span> <span data-ttu-id="c1403-119">Der Bot kann eine Vorfallerstellerkarte mit `Edit` Schaltfläche als Antwort auf diese Aufrufanforderung zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="c1403-119">The bot can return an incident creator card with `Edit` button as a response to this invoke request.</span></span>
4. <span data-ttu-id="c1403-120">Ähnlich wie bei Alex löst die automatische Aktualisierung eine weitere `adaptiveCard/action` Aufrufanforderung an den Bot aus.</span><span class="sxs-lookup"><span data-stu-id="c1403-120">Similarly for Alex, automatic refresh triggers another `adaptiveCard/action` invoke request to the bot.</span></span> <span data-ttu-id="c1403-121">Der Bot kann eine Karte des Vorfallsbesitzers als `Resolve` Antwort auf diese Aufrufanforderung zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="c1403-121">The bot can return an incident owner card `Resolve` button as a response to this invoke request.</span></span>

## <a name="invoke-request-sent-from-teams-client-to-the-bot"></a><span data-ttu-id="c1403-122">Aufrufen der Anforderung, die vom Teams an den Bot gesendet wird</span><span class="sxs-lookup"><span data-stu-id="c1403-122">Invoke request sent from Teams client to the bot</span></span>

<span data-ttu-id="c1403-123">Der folgende Code enthält ein Beispiel für eine Aufrufanforderung, die von Alex' und Megans Teams an den Bot gesendet wird:</span><span class="sxs-lookup"><span data-stu-id="c1403-123">The following code provides an example of an invoke request sent from Alex's and Megan's Teams client to the bot:</span></span>

```JSON
{ 
  "type": "invoke",
  "name": "adaptiveCard/action",

  // ... other properties omitted for brevity

  "value": { 
    "action": { 
      "type": "Action.Execute", 
      "id": "", 
      "verb": "editOrResolveView",
      "data": { 
            "refresh info": "<refresh info>"
      } 
    },
    "trigger": "automatic" 
  }
}
```

## <a name="adaptivecardaction-invoke-response-card"></a><span data-ttu-id="c1403-124">adaptiveCard/action invoke response card</span><span class="sxs-lookup"><span data-stu-id="c1403-124">adaptiveCard/action invoke response card</span></span>

<span data-ttu-id="c1403-125">Der folgende Code enthält ein Beispiel für eine adaptiveCard/Action-Aufrufantwortkarte für Megan:</span><span class="sxs-lookup"><span data-stu-id="c1403-125">The following code provides an example of an adaptiveCard/action invoke response card for Megan:</span></span>

```JSON
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "originator":"c9b4352b-a76b-43b9-88ff-80edddaa243b",
  "version": "1.4",
  "refresh": {
    "action": {
      "type": "Action.Execute",
      "title": "Refresh",
      "verb": "editOrResolveView"
    },
    "userIds": ["<Megan's user MRI>", "<Alex's user MRI>"]
  },
  "body": [
    {
      "type": "TextBlock",
      "text": "Incident 1234"
    },
    {
      "type": "TextBlock",
      "text": "Incident details: <incident details>"
    }
  ],
  "actions": [
    {
      "type": "Action.Execute",
      "title": "Edit",
      "verb": "edit",
      "data": {
            "additional info": "<additional info>",
            ...
      }
    }
  ]
}
```

## <a name="adaptivecardaction-invoke-response-card-for-alex"></a><span data-ttu-id="c1403-126">adaptiveCard/action invoke response card for Alex</span><span class="sxs-lookup"><span data-stu-id="c1403-126">adaptiveCard/action invoke response card for Alex</span></span>

<span data-ttu-id="c1403-127">Der folgende Code enthält ein Beispiel für eine adaptiveCard/Action-Aufrufantwortkarte für Alex:</span><span class="sxs-lookup"><span data-stu-id="c1403-127">The following code provides an example of an adaptiveCard/action invoke response card for Alex:</span></span>

```JSON
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "originator":"c9b4352b-a76b-43b9-88ff-80edddaa243b",
  "version": "1.4",
  "refresh": {
    "action": {
      "type": "Action.Execute",
      "title": "Refresh",
      "verb": "editOrResolveView"
    },
    "userIds": ["<Megan's user MRI>", "<Alex's user MRI>"]
  },
  "body": [
    {
      "type": "TextBlock",
      "text": "Incident 1234"
    },
    {
      "type": "TextBlock",
      "text": "Incident details: <incident details>"
    }
  ],
  "actions": [
    {
      "type": "Action.Execute",
      "title": "Resolve",
      "verb": "resolve",
      "data": {
            "additional info": "<additional info>",
            ...
      }
    }
  ]
}
```

## <a name="invoke-response-to-return-adaptive-cards"></a><span data-ttu-id="c1403-128">Aufrufen der Antwort zum Zurückgeben adaptiver Karten</span><span class="sxs-lookup"><span data-stu-id="c1403-128">Invoke response to return Adaptive Cards</span></span>

<span data-ttu-id="c1403-129">Der folgende Code enthält ein Beispiel für eine Aufrufantwort zum Zurückgeben adaptiver Karten:</span><span class="sxs-lookup"><span data-stu-id="c1403-129">The following code provides an example of an invoke response to return Adaptive Cards:</span></span>

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

<span data-ttu-id="c1403-130">Richtlinien für den Kartenentwurf, die beim Entwerfen benutzerspezifischer Ansichten zu berücksichtigen sind:</span><span class="sxs-lookup"><span data-stu-id="c1403-130">Card design guidelines to keep in mind while designing User Specific Views:</span></span>

* <span data-ttu-id="c1403-131">Sie können maximal **60 benutzerspezifische** Ansichten für eine bestimmte Karte erstellen, die an einen Chat oder Kanal gesendet werden, indem Sie sie `userIds` im Abschnitt `refresh` angeben.</span><span class="sxs-lookup"><span data-stu-id="c1403-131">You can create a maximum of **60 User Specific Views** for a particular card being sent to a chat or channel by specifying their `userIds` in the `refresh` section.</span></span>
* <span data-ttu-id="c1403-132">**Basiskarte:** Die Basisversion der Karte, die der Botentwickler an den Chat sendet.</span><span class="sxs-lookup"><span data-stu-id="c1403-132">**Base Card:** The base version of the card that the bot developer sends to the chat.</span></span> <span data-ttu-id="c1403-133">Dies ist die Version der adaptiven Karte für alle Benutzer, die nicht im Abschnitt angegeben `userIds` sind.</span><span class="sxs-lookup"><span data-stu-id="c1403-133">This is the version of the Adaptive Card for all users who are not specified in the `userIds` section.</span></span>
* <span data-ttu-id="c1403-134">Ein Nachrichtenupdate oder -bearbeiten kann verwendet werden, um die Basiskarte zu aktualisieren und gleichzeitig die benutzerspezifische Karte zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="c1403-134">A message update or edit can be used to update the base card and simultaneously refresh the User Specific Card.</span></span>

## <a name="see-also"></a><span data-ttu-id="c1403-135">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="c1403-135">See also</span></span>

* [<span data-ttu-id="c1403-136">Mit Universal-Aktionen für adaptive Karten arbeiten</span><span class="sxs-lookup"><span data-stu-id="c1403-136">Work with Universal Actions for Adaptive Cards</span></span>](Work-with-universal-actions-for-adaptive-cards.md)
* [<span data-ttu-id="c1403-137">Aktuelle Ansichten</span><span class="sxs-lookup"><span data-stu-id="c1403-137">Up to date views</span></span>](Up-To-Date-Views.md)
