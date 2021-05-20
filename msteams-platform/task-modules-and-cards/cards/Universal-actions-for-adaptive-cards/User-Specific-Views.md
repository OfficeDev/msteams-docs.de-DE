---
title: Benutzerspezifische Ansichten
description: Beispiel für benutzerspezifische Ansichten mithilfe universeller Aktionen
author: surbhigupta12
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: 696fc5ce25c79d749b301309bfe0c737e39ad294
ms.sourcegitcommit: 9ef3b415cbba484c2201abe9c6927e08d974388e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52555444"
---
# <a name="user-specific-views"></a><span data-ttu-id="2586d-103">Benutzerspezifische Ansichten</span><span class="sxs-lookup"><span data-stu-id="2586d-103">User Specific Views</span></span>

<span data-ttu-id="2586d-104">Früher, wenn Adaptive Cards in einer Teams Unterhaltung gesendet wurden, sehen alle Benutzer genau den gleichen Karteninhalt.</span><span class="sxs-lookup"><span data-stu-id="2586d-104">Earlier if Adaptive Cards was sent in a Teams conversation, all users see the exact same card content.</span></span> <span data-ttu-id="2586d-105">Mit der Einführung des Universal Actions-Modells und `refresh` für Adaptive Cards können Bot-Entwickler Benutzern nun benutzerspezifische Ansichten von Adaptive Cards zur Verfügung stellen.</span><span class="sxs-lookup"><span data-stu-id="2586d-105">With the introduction of the Universal Actions model and `refresh` for Adaptive Cards, bot developers can now provide User Specific Views of Adaptive Cards to users.</span></span> <span data-ttu-id="2586d-106">Dieselbe Adaptive Karte kann jetzt auf einer benutzerspezifischen adaptiven Karte aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="2586d-106">The same Adaptive Card can now refresh to a User Specific Adaptive Card.</span></span>

<span data-ttu-id="2586d-107">Beispielsweise möchte Megan, ein Sicherheitsinspektor bei Contoso, einen Vorfall erstellen und Alex zuweisen.</span><span class="sxs-lookup"><span data-stu-id="2586d-107">For example, Megan, a safety inspector at Contoso, wants to create an incident and assign it to Alex.</span></span> <span data-ttu-id="2586d-108">Sie möchte auch, dass alle im Team über den Vorfall informiert werden.</span><span class="sxs-lookup"><span data-stu-id="2586d-108">She also wants everyone in the team to be aware about the incident.</span></span> <span data-ttu-id="2586d-109">Megan verwendet Contoso Incident Reporting Message Extension powered by Universal Actions for Adaptive Cards.</span><span class="sxs-lookup"><span data-stu-id="2586d-109">Megan uses Contoso incident reporting message extension powered by Universal Actions for Adaptive Cards.</span></span>

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-incident-management.png" alt-text="Benutzerspezifische Ansichten":::

## <a name="user-specific-views-for-adaptive-cards"></a><span data-ttu-id="2586d-111">Benutzerspezifische Ansichten für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="2586d-111">User Specific Views for Adaptive Cards</span></span>

<span data-ttu-id="2586d-112">Der folgende Code enthält ein Beispiel für Adaptive Cards:</span><span class="sxs-lookup"><span data-stu-id="2586d-112">The following code provides an example of Adaptive Cards:</span></span>

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

<span data-ttu-id="2586d-113">**Um Adaptive Cards zu senden, benutzerspezifische Ansichten zu aktualisieren und Anforderungen an den Bot aufzurufen**</span><span class="sxs-lookup"><span data-stu-id="2586d-113">**To send Adaptive Cards, refresh User Specific Views, and invoke requests to the bot**</span></span>

1. <span data-ttu-id="2586d-114">Wenn Megan einen neuen Vorfall erstellt, sendet der Bot die Adaptive Card oder die gemeinsame Karte mit Ereignisdetails im Teams Gespräch.</span><span class="sxs-lookup"><span data-stu-id="2586d-114">When Megan creates a new incident, the bot sends the Adaptive Card or common card with incident details in the Teams conversation.</span></span>
2. <span data-ttu-id="2586d-115">Diese Karte wird jetzt automatisch in der benutzerspezifischen Ansicht für Megan und Alex aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="2586d-115">Now this card automatically refreshes to User Specific View for Megan and Alex.</span></span> <span data-ttu-id="2586d-116">Die Benutzer-MRTs von Alex und Megan werden in `userIds` der Eigenschaft der Adaptive Card `refresh` JSON hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="2586d-116">Alex's and Megan's user MRIs are added in `userIds` property of `refresh` property of the Adaptive Card JSON.</span></span> <span data-ttu-id="2586d-117">Die Karte bleibt für andere Benutzer in der Unterhaltung gleich.</span><span class="sxs-lookup"><span data-stu-id="2586d-117">The card remains the same for other users in the conversation.</span></span>
3. <span data-ttu-id="2586d-118">Für Megan löst die automatische Aktualisierung eine `adaptiveCard/action` Aufrufanforderung an den Bot aus.</span><span class="sxs-lookup"><span data-stu-id="2586d-118">For Megan, automatic refresh triggers an `adaptiveCard/action` invoke request to the bot.</span></span> <span data-ttu-id="2586d-119">Der Bot kann eine Vorfall-Ersteller-Karte mit `Edit` Schaltfläche als Antwort auf diese Aufrufanforderung zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="2586d-119">The bot can return an incident creator card with `Edit` button as a response to this invoke request.</span></span>
4. <span data-ttu-id="2586d-120">Ebenso löst die automatische Aktualisierung für Alex eine weitere `adaptiveCard/action` Aufrufanforderung an den Bot aus.</span><span class="sxs-lookup"><span data-stu-id="2586d-120">Similarly for Alex, automatic refresh triggers another `adaptiveCard/action` invoke request to the bot.</span></span> <span data-ttu-id="2586d-121">Der Bot kann eine Schaltfläche für den Vorfallbesitzer als `Resolve` Antwort auf diese Aufrufanforderung zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="2586d-121">The bot can return an incident owner card `Resolve` button as a response to this invoke request.</span></span>

## <a name="invoke-request-sent-from-teams-client-to-the-bot"></a><span data-ttu-id="2586d-122">Aufrufen von Anforderung, die von Teams Client an den Bot gesendet wurde</span><span class="sxs-lookup"><span data-stu-id="2586d-122">Invoke request sent from Teams client to the bot</span></span>

<span data-ttu-id="2586d-123">Der folgende Code enthält ein Beispiel für eine Aufrufanforderung, die von Alex und Megans Teams-Client an den Bot gesendet wurde:</span><span class="sxs-lookup"><span data-stu-id="2586d-123">The following code provides an example of an invoke request sent from Alex's and Megan's Teams client to the bot:</span></span>

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

## <a name="adaptivecardaction-invoke-response-card"></a><span data-ttu-id="2586d-124">adaptiveCard/Action-Aufrufantwortkarte</span><span class="sxs-lookup"><span data-stu-id="2586d-124">adaptiveCard/action invoke response card</span></span>

<span data-ttu-id="2586d-125">Der folgende Code enthält ein Beispiel für eine adaptiveCard/Aktionsaufrufantwortkarte für Megan:</span><span class="sxs-lookup"><span data-stu-id="2586d-125">The following code provides an example of an adaptiveCard/action invoke response card for Megan:</span></span>

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

## <a name="adaptivecardaction-invoke-response-card-for-alex"></a><span data-ttu-id="2586d-126">adaptiveCard/Action-Aufrufantwortkarte für Alex</span><span class="sxs-lookup"><span data-stu-id="2586d-126">adaptiveCard/action invoke response card for Alex</span></span>

<span data-ttu-id="2586d-127">Der folgende Code enthält ein Beispiel für eine adaptiveCard/Aktionsaufrufantwortkarte für Alex:</span><span class="sxs-lookup"><span data-stu-id="2586d-127">The following code provides an example of an adaptiveCard/action invoke response card for Alex:</span></span>

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

## <a name="invoke-response-to-return-adaptive-cards"></a><span data-ttu-id="2586d-128">Aufrufen der Antwort auf die Rückgabe von Adaptive Cards</span><span class="sxs-lookup"><span data-stu-id="2586d-128">Invoke response to return Adaptive Cards</span></span>

<span data-ttu-id="2586d-129">Der folgende Code enthält ein Beispiel für eine Aufrufantwort zum Zurückgeben von Adaptive Cards:</span><span class="sxs-lookup"><span data-stu-id="2586d-129">The following code provides an example of an invoke response to return Adaptive Cards:</span></span>

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

<span data-ttu-id="2586d-130">Richtlinien für das Kartendesign, die Beim Entwerfen von benutzerspezifischen Ansichten zu beachten sind:</span><span class="sxs-lookup"><span data-stu-id="2586d-130">Card design guidelines to keep in mind while designing User Specific Views:</span></span>

* <span data-ttu-id="2586d-131">Sie können maximal **60 benutzerspezifische Ansichten** für eine bestimmte Karte erstellen, die an einen Chat oder Kanal gesendet wird, indem Sie deren `userIds` im Abschnitt `refresh` angeben.</span><span class="sxs-lookup"><span data-stu-id="2586d-131">You can create a maximum of **60 User Specific Views** for a particular card being sent to a chat or channel by specifying their `userIds` in the `refresh` section.</span></span>
* <span data-ttu-id="2586d-132">**Basiskarte:** Die Basisversion der Karte, die der Bot-Entwickler an den Chat sendet.</span><span class="sxs-lookup"><span data-stu-id="2586d-132">**Base Card:** The base version of the card that the bot developer sends to the chat.</span></span> <span data-ttu-id="2586d-133">Dies ist die Version der Adaptive Card für alle Benutzer, die nicht im Abschnitt angegeben `userIds` sind.</span><span class="sxs-lookup"><span data-stu-id="2586d-133">This is the version of the Adaptive Card for all users who are not specified in the `userIds` section.</span></span>
* <span data-ttu-id="2586d-134">Eine Nachrichtenaktualisierung oder -bearbeitung kann verwendet werden, um die Basiskarte zu aktualisieren und gleichzeitig die benutzerspezifische Karte zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="2586d-134">A message update or edit can be used to update the base card and simultaneously refresh the User Specific Card.</span></span>

## <a name="see-also"></a><span data-ttu-id="2586d-135">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="2586d-135">See also</span></span>

* [<span data-ttu-id="2586d-136">Mit Universal-Aktionen für adaptive Karten arbeiten</span><span class="sxs-lookup"><span data-stu-id="2586d-136">Work with Universal Actions for Adaptive Cards</span></span>](Work-with-universal-actions-for-adaptive-cards.md)
* [<span data-ttu-id="2586d-137">Aktuelle Ansichten</span><span class="sxs-lookup"><span data-stu-id="2586d-137">Up to date views</span></span>](Up-To-Date-Views.md)
