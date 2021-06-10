---
title: Benutzerspezifische Ansichten
description: Beispiel für benutzerspezifische Ansichten mit universellen Aktionen
author: surbhigupta12
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: c24697b300d07ed53a172df162d0d3851361f579
ms.sourcegitcommit: 37325179a532897fafbe827dcf9a7ca5fa5e7d0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2021
ms.locfileid: "52853515"
---
# <a name="user-specific-views"></a><span data-ttu-id="c09e9-103">Benutzerspezifische Ansichten</span><span class="sxs-lookup"><span data-stu-id="c09e9-103">User Specific Views</span></span>

<span data-ttu-id="c09e9-104">Wenn adaptive Karten zuvor in einer Teams Unterhaltung gesendet wurden, sehen alle Benutzer genau den gleichen Karteninhalt.</span><span class="sxs-lookup"><span data-stu-id="c09e9-104">Earlier if Adaptive Cards was sent in a Teams conversation, all users see the exact same card content.</span></span> <span data-ttu-id="c09e9-105">Mit der Einführung des Modells für universelle Aktionen und `refresh` für adaptive Karten können Botentwickler Benutzern jetzt benutzerspezifische Ansichten adaptiver Karten bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="c09e9-105">With the introduction of the Universal Actions model and `refresh` for Adaptive Cards, bot developers can now provide User Specific Views of Adaptive Cards to users.</span></span> <span data-ttu-id="c09e9-106">Dieselbe adaptive Karte kann jetzt auf eine benutzerspezifische adaptive Karte aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="c09e9-106">The same Adaptive Card can now refresh to a User Specific Adaptive Card.</span></span> <span data-ttu-id="c09e9-107">Maximal 60 verschiedene Benutzer können eine andere Version der Karte mit zusätzlichen Informationen oder Aktionen sehen.</span><span class="sxs-lookup"><span data-stu-id="c09e9-107">Maximum 60 different users can see a different version of the card with additional information or actions.</span></span> <span data-ttu-id="c09e9-108">Dies bietet leistungsstarke Szenarien wie Genehmigungen, Steuerelemente für Umfrageersteller, Ticketing, Vorfallverwaltung und Projektverwaltungskarten.</span><span class="sxs-lookup"><span data-stu-id="c09e9-108">This provides powerful scenarios like approvals, poll creator controls, ticketing, incident management, and project management cards.</span></span>

<span data-ttu-id="c09e9-109">Megan, ein Sicherheitsinspektor bei Contoso, möchte beispielsweise einen Vorfall erstellen und Alex zuweisen.</span><span class="sxs-lookup"><span data-stu-id="c09e9-109">For example, Megan, a safety inspector at Contoso, wants to create an incident and assign it to Alex.</span></span> <span data-ttu-id="c09e9-110">Außerdem möchte sie, dass jeder im Team über den Vorfall informiert wird.</span><span class="sxs-lookup"><span data-stu-id="c09e9-110">She also wants everyone in the team to be aware about the incident.</span></span> <span data-ttu-id="c09e9-111">Megan verwendet die Nachrichtenerweiterung "Contoso Incident Reporting", die von universellen Aktionen für adaptive Karten unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="c09e9-111">Megan uses Contoso incident reporting message extension powered by Universal Actions for Adaptive Cards.</span></span>

# <a name="mobile"></a>[<span data-ttu-id="c09e9-112">Mobil</span><span class="sxs-lookup"><span data-stu-id="c09e9-112">Mobile</span></span>](#tab/mobile)

:::image type="content" source="~/assets/images/adaptive-cards/mobile-universal-bots-incident-management.jpg" alt-text="Benutzerspezifische Ansichten mobiler Benutzer":::

# <a name="desktop"></a>[<span data-ttu-id="c09e9-114">Desktop</span><span class="sxs-lookup"><span data-stu-id="c09e9-114">Desktop</span></span>](#tab/desktop)

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-incident-management.png" alt-text="Benutzerspezifische Ansichten":::

* * *

## <a name="user-specific-views-for-adaptive-cards"></a><span data-ttu-id="c09e9-116">Benutzerspezifische Ansichten für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="c09e9-116">User Specific Views for Adaptive Cards</span></span>

<span data-ttu-id="c09e9-117">Der folgende Code enthält ein Beispiel für adaptive Karten:</span><span class="sxs-lookup"><span data-stu-id="c09e9-117">The following code provides an example of Adaptive Cards:</span></span>

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

<span data-ttu-id="c09e9-118">**Um adaptive Karten zu senden, aktualisieren Sie benutzerspezifische Ansichten, und rufen Sie Anforderungen an den Bot auf.**</span><span class="sxs-lookup"><span data-stu-id="c09e9-118">**To send Adaptive Cards, refresh User Specific Views, and invoke requests to the bot**</span></span>

1. <span data-ttu-id="c09e9-119">Wenn Megan einen neuen Vorfall erstellt, sendet der Bot die adaptive Karte oder allgemeine Karte mit Vorfalldetails in der Teams Unterhaltung.</span><span class="sxs-lookup"><span data-stu-id="c09e9-119">When Megan creates a new incident, the bot sends the Adaptive Card or common card with incident details in the Teams conversation.</span></span>
2. <span data-ttu-id="c09e9-120">Jetzt wird diese Karte automatisch auf die benutzerspezifische Ansicht für Megan und Alex aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="c09e9-120">Now this card automatically refreshes to User Specific View for Megan and Alex.</span></span> <span data-ttu-id="c09e9-121">Alex und Megans Benutzer-MRIs werden als `userIds` Eigenschaft der Adaptive Card JSON `refresh` hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="c09e9-121">Alex's and Megan's user MRIs are added in `userIds` property of `refresh` property of the Adaptive Card JSON.</span></span> <span data-ttu-id="c09e9-122">Die Karte bleibt für andere Benutzer in der Unterhaltung gleich.</span><span class="sxs-lookup"><span data-stu-id="c09e9-122">The card remains the same for other users in the conversation.</span></span>
3. <span data-ttu-id="c09e9-123">Bei Megan löst die automatische Aktualisierung eine `adaptiveCard/action` Aufrufanforderung an den Bot aus.</span><span class="sxs-lookup"><span data-stu-id="c09e9-123">For Megan, automatic refresh triggers an `adaptiveCard/action` invoke request to the bot.</span></span> <span data-ttu-id="c09e9-124">Der Bot kann eine Vorfallerstellerkarte mit `Edit` schaltfläche als Antwort auf diese Aufrufanforderung zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="c09e9-124">The bot can return an incident creator card with `Edit` button as a response to this invoke request.</span></span>
4. <span data-ttu-id="c09e9-125">Auf ähnliche Weise löst die automatische Aktualisierung für Alex eine weitere `adaptiveCard/action` Aufrufanforderung an den Bot aus.</span><span class="sxs-lookup"><span data-stu-id="c09e9-125">Similarly for Alex, automatic refresh triggers another `adaptiveCard/action` invoke request to the bot.</span></span> <span data-ttu-id="c09e9-126">Der Bot kann eine `Resolve` Vorfallbesitzer-Kartenschaltfläche als Antwort auf diese Aufrufanforderung zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="c09e9-126">The bot can return an incident owner card `Resolve` button as a response to this invoke request.</span></span>

## <a name="invoke-request-sent-from-teams-client-to-the-bot"></a><span data-ttu-id="c09e9-127">Aufrufen einer Anforderung, die vom Teams-Client an den Bot gesendet wurde</span><span class="sxs-lookup"><span data-stu-id="c09e9-127">Invoke request sent from Teams client to the bot</span></span>

<span data-ttu-id="c09e9-128">Der folgende Code enthält ein Beispiel für eine Aufrufanforderung, die vom Teams-Client von Alex und Megan an den Bot gesendet wird:</span><span class="sxs-lookup"><span data-stu-id="c09e9-128">The following code provides an example of an invoke request sent from Alex's and Megan's Teams client to the bot:</span></span>

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

## <a name="adaptivecardaction-invoke-response-card"></a><span data-ttu-id="c09e9-129">adaptiveCard/Aktionsaufrufantwortkarte</span><span class="sxs-lookup"><span data-stu-id="c09e9-129">adaptiveCard/action invoke response card</span></span>

<span data-ttu-id="c09e9-130">Der folgende Code enthält ein Beispiel für eine AdaptiveCard/Aktionsaufforderungsantwortkarte für Megan:</span><span class="sxs-lookup"><span data-stu-id="c09e9-130">The following code provides an example of an adaptiveCard/action invoke response card for Megan:</span></span>

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

## <a name="adaptivecardaction-invoke-response-card-for-alex"></a><span data-ttu-id="c09e9-131">adaptiveCard/Aktion ruft Antwortkarte für Alex auf</span><span class="sxs-lookup"><span data-stu-id="c09e9-131">adaptiveCard/action invoke response card for Alex</span></span>

<span data-ttu-id="c09e9-132">Der folgende Code enthält ein Beispiel für eine AdaptiveCard/Aktionsaufforderungsantwortkarte für Alex:</span><span class="sxs-lookup"><span data-stu-id="c09e9-132">The following code provides an example of an adaptiveCard/action invoke response card for Alex:</span></span>

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

## <a name="invoke-response-to-return-adaptive-cards"></a><span data-ttu-id="c09e9-133">Aufrufen der Antwort zum Zurückgeben adaptiver Karten</span><span class="sxs-lookup"><span data-stu-id="c09e9-133">Invoke response to return Adaptive Cards</span></span>

<span data-ttu-id="c09e9-134">Der folgende Code enthält ein Beispiel für eine Aufrufantwort, um adaptive Karten zurückzugeben:</span><span class="sxs-lookup"><span data-stu-id="c09e9-134">The following code provides an example of an invoke response to return Adaptive Cards:</span></span>

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

<span data-ttu-id="c09e9-135">Richtlinien für den Kartenentwurf, die Sie beim Entwerfen benutzerspezifischer Ansichten beachten sollten:</span><span class="sxs-lookup"><span data-stu-id="c09e9-135">Card design guidelines to keep in mind while designing User Specific Views:</span></span>

* <span data-ttu-id="c09e9-136">Sie können maximal **60 benutzerspezifische Ansichten** für eine bestimmte Karte erstellen, die an einen Chat oder Kanal gesendet wird, indem Sie diese `userIds` im Abschnitt `refresh` angeben.</span><span class="sxs-lookup"><span data-stu-id="c09e9-136">You can create a maximum of **60 User Specific Views** for a particular card sent to a chat or channel by specifying their `userIds` in the `refresh` section.</span></span>
* <span data-ttu-id="c09e9-137">**Basiskarte:** Die Basisversion der Karte, die der Bot-Entwickler an den Chat sendet.</span><span class="sxs-lookup"><span data-stu-id="c09e9-137">**Base Card:** The base version of the card that the bot developer sends to the chat.</span></span> <span data-ttu-id="c09e9-138">Dies ist die Version der adaptiven Karte für alle Benutzer, die nicht im Abschnitt angegeben `userIds` sind.</span><span class="sxs-lookup"><span data-stu-id="c09e9-138">This is the version of the Adaptive Card for all users who are not specified in the `userIds` section.</span></span>
* <span data-ttu-id="c09e9-139">Eine Nachrichtenaktualisierung kann verwendet werden, um die Basiskarte zu aktualisieren und gleichzeitig die benutzerspezifische Karte zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="c09e9-139">A message update can be used to update the base card and simultaneously refresh the User Specific Card.</span></span> <span data-ttu-id="c09e9-140">Beim Öffnen des Chats oder Kanals wird auch die Karte für Benutzer mit aktivierter Aktualisierung aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="c09e9-140">Opening the chat or channel also refreshes the card for users with refresh enabled.</span></span>
* <span data-ttu-id="c09e9-141">Für Szenarien mit größeren Gruppen, in denen Benutzer zu einer Aktionsansicht wechseln, die dynamische Updates für Antwortende benötigt, können Sie bis zu 60 Benutzer zur `userIds` Liste hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="c09e9-141">For scenarios with larger groups where users switch to a view on action, which needs dynamic updates for responders, you can keep adding up to 60 users to the `userIds` list.</span></span> <span data-ttu-id="c09e9-142">Sie können den Ersten Antwortenden aus der Liste entfernen, wenn der 61. Benutzer antwortet.</span><span class="sxs-lookup"><span data-stu-id="c09e9-142">You can remove the first responder from the list when the 61st user responds.</span></span> <span data-ttu-id="c09e9-143">Für die Benutzer, die aus der Liste entfernt `userIds` werden, können Sie eine manuelle Aktualisierungsschaltfläche bereitstellen oder die Schaltfläche "Aktualisieren" im Menü "Nachrichtenoptionen" verwenden, um das neueste Ergebnis zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="c09e9-143">For the users who get removed from the `userIds` list, you can provide a manual refresh button or use the refresh button in the message options menu to get the latest result.</span></span>
* <span data-ttu-id="c09e9-144">Geben Sie Benutzern eine Eingabeaufforderung, um eine benutzerspezifische Ansicht zu erhalten, in der nur eine bestimmte Ansicht der Karte oder einige Aktionen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c09e9-144">Give a prompt to users to get a User Specific View, where they see only a particular view of the card or some actions.</span></span>

## <a name="see-also"></a><span data-ttu-id="c09e9-145">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="c09e9-145">See also</span></span>

* [<span data-ttu-id="c09e9-146">Mit Universal-Aktionen für adaptive Karten arbeiten</span><span class="sxs-lookup"><span data-stu-id="c09e9-146">Work with Universal Actions for Adaptive Cards</span></span>](Work-with-universal-actions-for-adaptive-cards.md)
* [<span data-ttu-id="c09e9-147">Aktuelle Ansichten</span><span class="sxs-lookup"><span data-stu-id="c09e9-147">Up to date views</span></span>](Up-To-Date-Views.md)
