---
title: Aktuelle Ansichten
description: Beispiel für aktuelle Ansichten mithilfe von Universal Bot
author: surbhigupta12
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: 2027d07961929fb40e7afc3ee268e1267b235a02
ms.sourcegitcommit: 1256639fa424e3833b44207ce847a245824d48e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2021
ms.locfileid: "52088888"
---
# <a name="up-to-date-cards"></a><span data-ttu-id="4d622-103">Aktuelle Karten</span><span class="sxs-lookup"><span data-stu-id="4d622-103">Up to date cards</span></span>

<span data-ttu-id="4d622-104">Sie können Ihren Benutzern jetzt aktuelle Informationen zu adaptiven Karten mit einer Kombination aus Aktualisierungs- und Nachrichtenbearbeitungen in Teams.</span><span class="sxs-lookup"><span data-stu-id="4d622-104">You can now provide latest information to your users on Adaptive Cards with a combination of refresh and message edits in Teams.</span></span> <span data-ttu-id="4d622-105">Dadurch können Sie die benutzerspezifischen Ansichten dynamisch auf den neuesten Status aktualisieren, wenn eine Änderung an Ihrem Dienst vor sich geht.</span><span class="sxs-lookup"><span data-stu-id="4d622-105">With this you are able to update the User Specific Views dynamically to its latest state as and when there is a change on your service.</span></span> <span data-ttu-id="4d622-106">Bei Projektverwaltungs- oder Ticketkarten können Sie beispielsweise Kommentare und den Status der Aufgabe aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="4d622-106">For example, in the case of project management or ticketing cards, you can update comments and the status of the task.</span></span> <span data-ttu-id="4d622-107">Bei Genehmigungen wird der neueste Zustand widersspiegelt und gleichzeitig differenzierte Informationen und Aktionen zur Verfügung stellt.</span><span class="sxs-lookup"><span data-stu-id="4d622-107">In case of approvals the latest state is reflected while also providing differentiated information and actions.</span></span>

<span data-ttu-id="4d622-108">Beispielsweise kann ein Benutzer eine Anforderung zur Anlagengenehmigung in einer Teams erstellen.</span><span class="sxs-lookup"><span data-stu-id="4d622-108">For example, a user can create an asset approval request in a Teams conversation.</span></span> <span data-ttu-id="4d622-109">Alex erstellt eine Genehmigungsanforderung und weist sie Megan und Nestor zu.</span><span class="sxs-lookup"><span data-stu-id="4d622-109">Alex creates an approval request and assigns it to Megan and Nestor.</span></span> <span data-ttu-id="4d622-110">Es folgen die beiden Teile zum Erstellen der Genehmigungsanforderung:</span><span class="sxs-lookup"><span data-stu-id="4d622-110">The following are the two parts to create the approval request:</span></span>

* <span data-ttu-id="4d622-111">Benutzerspezifische Ansichten können mithilfe der Eigenschaft der `refresh` adaptiven Karten genutzt werden.</span><span class="sxs-lookup"><span data-stu-id="4d622-111">User Specific Views can be leveraged using the `refresh` property of the Adaptive Cards.</span></span>
<span data-ttu-id="4d622-112">Mithilfe benutzerspezifischer Ansichten kann  eine  Karte mit Den Schaltflächen Genehmigen oder Ablehnen für eine Gruppe von Benutzern und eine Karte ohne diese Schaltflächen für andere Benutzer angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="4d622-112">Using User Specific Views one can show a card with **Approve** or **Reject** buttons to a set of users, and show a card without these buttons to other users.</span></span>

* <span data-ttu-id="4d622-113">Um den Kartenstatus immer auf dem neuesten Stand zu halten, Teams Nachrichtenbearbeitungsmechanismus genutzt werden.</span><span class="sxs-lookup"><span data-stu-id="4d622-113">To keep the card state updated at all times, Teams message edit mechanism can be leveraged.</span></span> <span data-ttu-id="4d622-114">Jedes Mal, wenn eine Genehmigung vor liegt, kann der Bot beispielsweise eine Nachrichtenbearbeitung für alle Benutzer auslösen.</span><span class="sxs-lookup"><span data-stu-id="4d622-114">For example, each time there is an approval, bot can trigger a message edit to all users.</span></span> <span data-ttu-id="4d622-115">Diese Botnachrichtenbearbeitung löst eine Aufrufanforderung für alle Benutzer der automatischen Aktualisierung aus, auf die der Bot mit der aktualisierten `adaptiveCard/action` benutzerspezifischen Karte antworten kann.</span><span class="sxs-lookup"><span data-stu-id="4d622-115">This bot message edit triggers an `adaptiveCard/action` invoke request for all automatic refresh users, to which the bot can respond with the updated user specific card.</span></span>

<span data-ttu-id="4d622-116">Weitere Informationen finden Sie unter [How to do a bot message edit](https://docs.microsoft.com/microsoftteams/platform/bots/how-to/update-and-delete-bot-messages?tabs=dotnet#update-cards).</span><span class="sxs-lookup"><span data-stu-id="4d622-116">For more information, see [how to do a bot message edit](https://docs.microsoft.com/microsoftteams/platform/bots/how-to/update-and-delete-bot-messages?tabs=dotnet#update-cards).</span></span>

## <a name="approval-base-card"></a><span data-ttu-id="4d622-117">Genehmigungsbasiskarte</span><span class="sxs-lookup"><span data-stu-id="4d622-117">Approval base card</span></span>

<span data-ttu-id="4d622-118">Der folgende Code enthält ein Beispiel für eine Genehmigungsbasiskarte:</span><span class="sxs-lookup"><span data-stu-id="4d622-118">The following code provides an example of an approval base card:</span></span>

```JSON
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "version": "1.4",
  "refresh": {
    "action": {
      "type": "Action.Execute",
      "title": "Refresh",
      "verb": "acceptRejectView"
    },
    "userIds": ["<Megan's user MRI>", "<Nestor's user MRI>"]
  },
  "body": [
    {
      "type": "TextBlock",
      "text": "Asset Request B12"
    },
    {
      "type": "TextBlock",
      "text": "Submitted by **Alex**"
    },
    {
      "type": "TextBlock",
      "text": "Approval pending from **Megan and Nestor**"
    }
  ]
}
```

## <a name="approval-card-with-approve-and-reject-buttons"></a><span data-ttu-id="4d622-119">Genehmigungskarte mit Schaltflächen Genehmigen und Ablehnen</span><span class="sxs-lookup"><span data-stu-id="4d622-119">Approval card with Approve and Reject buttons</span></span>

<span data-ttu-id="4d622-120">Der folgende Code enthält ein Beispiel für eine Genehmigungskarte mit den Schaltflächen **Genehmigen** **und Ablehnen:**</span><span class="sxs-lookup"><span data-stu-id="4d622-120">The following code provides an example of an approval card with **Approve** and **Reject** buttons:</span></span>

```JSON
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "version": "1.4",
  "refresh": {
    "action": {
      "type": "Action.Execute",
      "title": "Refresh",
      "verb": "acceptRejectView"
    },
    "userIds": ["<Nestor's user MRI>", "<Megan's user MRI>"]
  },
  "body": [
    {
      "type": "TextBlock",
      "text": "Approval Request B12"
    },
    {
      "type": "TextBlock",
      "text": "Submitted by **Alex**"
    },
    {
      "type": "TextBlock",
      "text": "Approval pending from **Megan and Nestor**"
    }
  ],
  "actions": [
    {
      "type": "Action.Execute",
      "title": "Approve",
      "verb": "approve",
      "data": {
            "more info": "<more info>"
      }
    },
    {
      "type": "Action.Execute",
      "title": "Reject",
      "verb": "reject",
      "data": {
            "more info": "<more info>"
      }
    }
  ]
}
```

<span data-ttu-id="4d622-121">Es folgen die beiden Rollen, die Benutzern in Abhängigkeit von ihrer Beteiligung an der Genehmigungsanforderung angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="4d622-121">Following are the two roles that are shown to users depending on their involvement in the approval request:</span></span>

* <span data-ttu-id="4d622-122">Genehmigungsbasiskarte: Wird Benutzern angezeigt, die nicht Teil der Liste genehmiger Personen sind und die Anforderung noch nicht genehmigt oder abgelehnt haben und nicht Teil der Liste in der Eigenschaft der `userIds` `refresh` adaptiven Karten-JSON sind.</span><span class="sxs-lookup"><span data-stu-id="4d622-122">Approval base card: Shown to users who are not part of approvers list and have not yet approved or rejected the request, and are not part of `userIds` list in `refresh` property of the Adaptive Card JSON.</span></span>
* <span data-ttu-id="4d622-123">Genehmigungskarte mit  **Den** Schaltflächen Genehmigen oder Ablehnen: Wird den Benutzern angezeigt, die Teil der Liste genehmiger Personen sind, und der Liste in der Eigenschaft des `userIds` `refresh` JSON für adaptive Karten.</span><span class="sxs-lookup"><span data-stu-id="4d622-123">Approval card with **Approve** or **Reject** buttons: Shown to the users who are part of the approvers list and the `userIds` list in the `refresh` property of the Adaptive Card JSON.</span></span>

<span data-ttu-id="4d622-124">**So senden Sie die Anforderung zur Anlagengenehmigung**</span><span class="sxs-lookup"><span data-stu-id="4d622-124">**To send the asset approval request**</span></span>

1. <span data-ttu-id="4d622-125">Alex löst eine Anforderung zur Anlagengenehmigung in einer Teams aus und weist sie Megan und Nestor zu.</span><span class="sxs-lookup"><span data-stu-id="4d622-125">Alex raises an asset approval request in a Teams conversation and assigns it to Megan and Nestor.</span></span>
2. <span data-ttu-id="4d622-126">Bot sendet die Genehmigungsbasiskarte in der Unterhaltung.</span><span class="sxs-lookup"><span data-stu-id="4d622-126">Bot sends the approval base card in the conversation.</span></span>
3. <span data-ttu-id="4d622-127">Alle anderen Benutzer in der Unterhaltung sehen die vom Bot gesendete Karte.</span><span class="sxs-lookup"><span data-stu-id="4d622-127">All other users in the conversation see the card sent by the bot.</span></span> <span data-ttu-id="4d622-128">Die automatische Aktualisierung wird für Megan und Nestor ausgelöst,  denen nun die benutzerspezifische Karte mit den Schaltflächen **Genehmigen** oder Ablehnen angezeigt wird, da ihre Benutzer-MRIs der Liste in der Eigenschaft der adaptiven Karte hinzugefügt `userIds` `refresh` werden.</span><span class="sxs-lookup"><span data-stu-id="4d622-128">Automatic refresh is triggered for Megan and Nestor, who now see the user specific card with **Approve** or **Reject** buttons as their user MRIs are added to the `userIds` list in the `refresh` property of the Adaptive Card.</span></span>

    :::image type="content" source="~/assets/images/adaptive-cards/universal-bots-up-to-date-views-1.png" alt-text="Benutzerspezifische Ansichten":::

4. <span data-ttu-id="4d622-130">Nestor wählt die Schaltfläche **Genehmigen** aus, die mit betrieben `Action.Execute` wird.</span><span class="sxs-lookup"><span data-stu-id="4d622-130">Nestor selects the **Approve** button which is powered with `Action.Execute`.</span></span> <span data-ttu-id="4d622-131">Der Bot ruft eine `adaptiveCard/action` Aufrufanforderung ab, an die er als Antwort eine adaptive Karte zurückgeben kann.</span><span class="sxs-lookup"><span data-stu-id="4d622-131">The bot gets an `adaptiveCard/action` invoke request to which it can return an Adaptive Card in response.</span></span>
5. <span data-ttu-id="4d622-132">Der Bot löst eine Nachrichtenbearbeitung mit einer aktualisierten Karte aus, auf der nestor die Anforderung genehmigt hat, während Megans Genehmigung aussteht.</span><span class="sxs-lookup"><span data-stu-id="4d622-132">The bot triggers a message edit with an updated card which says Nestor has approved the request while Megan's approval is pending.</span></span>
6. <span data-ttu-id="4d622-133">Die Bot-Nachrichtenbearbeitung löst eine automatische Aktualisierung für Megan aus, und ihr wird die aktualisierte  benutzerspezifische Karte angezeigt, auf der nestor die Anforderung genehmigt hat, aber auch die Schaltflächen Genehmigen oder Ablehnen **angezeigt** wird.</span><span class="sxs-lookup"><span data-stu-id="4d622-133">Bot message edit triggers an automatic refresh for Megan and she sees the updated user specific card, which says Nestor has approved the request, but also sees the **Approve** or **Reject** buttons.</span></span> <span data-ttu-id="4d622-134">Die Benutzer-MRT von Nestor wird in den Schritten 4 und 5 aus der Liste in der Eigenschaft dieses JSON für adaptive Karten `userIds` `refresh` entfernt.</span><span class="sxs-lookup"><span data-stu-id="4d622-134">Nestor's user MRI is removed from the `userIds` list in `refresh` property of this Adaptive Card JSON in steps 4 and 5.</span></span> <span data-ttu-id="4d622-135">Jetzt wird die automatische Aktualisierung nur für Megan ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="4d622-135">Now, automatic refresh is only triggered for Megan.</span></span>

    :::image type="content" source="~/assets/images/adaptive-cards/universal-bots-up-to-date-views-2.png" alt-text="Aktuelle benutzerspezifische Ansichten":::

7. <span data-ttu-id="4d622-137">Megan wählt nun die Schaltfläche **Genehmigen** aus, die mit betrieben `Action.Execute` wird.</span><span class="sxs-lookup"><span data-stu-id="4d622-137">Now, Megan selects the **Approve** button, which is powered with `Action.Execute`.</span></span> <span data-ttu-id="4d622-138">Der Bot ruft eine `adaptiveCard/action` Aufrufanforderung ab, an die er als Antwort eine adaptive Karte zurückgeben kann.</span><span class="sxs-lookup"><span data-stu-id="4d622-138">The bot gets an `adaptiveCard/action` invoke request to which it can return an Adaptive Card in response.</span></span>
8. <span data-ttu-id="4d622-139">Der Bot löst eine Nachrichtenbearbeitung mit einer aktualisierten Karte aus, die nestor und Megan die Anforderung genehmigt haben.</span><span class="sxs-lookup"><span data-stu-id="4d622-139">The bot triggers a message edit with an updated card, which says Nestor and Megan have approved the request.</span></span>
9. <span data-ttu-id="4d622-140">Die Botnachrichtenbearbeitung löst keine automatische Aktualisierung aus.</span><span class="sxs-lookup"><span data-stu-id="4d622-140">Bot message edit does not trigger any automatic refresh.</span></span> <span data-ttu-id="4d622-141">Megans Benutzer-MRI wird auch in der Eigenschaft dieser adaptiven Karten-JSON in den Schritten `userIds` `refresh` 7 und 8 aus der Liste entfernt.</span><span class="sxs-lookup"><span data-stu-id="4d622-141">Megan's user MRI is also removed from the `userIds` list in `refresh` property of this Adaptive Card JSON in steps 7 and 8.</span></span>

    :::image type="content" source="~/assets/images/adaptive-cards/universal-bots-up-to-date-views-3.png" alt-text="Aktuelle Ansichten":::

## <a name="adaptive-card-sent-as-response-of-adaptivecardaction-and-message-edit"></a><span data-ttu-id="4d622-143">Adaptive Karte, die als Antwort von und gesendet `adaptiveCard/action` wird `message edit`</span><span class="sxs-lookup"><span data-stu-id="4d622-143">Adaptive Card sent as response of `adaptiveCard/action` and `message edit`</span></span>

<span data-ttu-id="4d622-144">Der folgende Code enthält ein Beispiel für adaptive Karten, die als Antwort auf und für die `adaptiveCard/action` `message edit` Schritte 4 und 5 gesendet werden:</span><span class="sxs-lookup"><span data-stu-id="4d622-144">The following code provides an example of Adaptive Cards sent as response of `adaptiveCard/action` and `message edit` for steps 4 and 5:</span></span>

```JSON
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "version": "1.4",
  "refresh": {
    "action": {
      "type": "Action.Execute",
      "title": "Refresh",
      "verb": "acceptRejectView"
    },
    "userIds": ["<Megan's user MRI>"]
  },
  "body": [
    {
      "type": "TextBlock",
      "text": "Asset Request B12"
    },
    {
      "type": "TextBlock",
      "text": "Submitted by **Alex**"
    },
    {
      "type": "TextBlock",
      "text": "Approval pending from **Megan**"
    },
    {
      "type": "TextBlock",
      "text": "Approved by **Nestor**"
    }
  ]
}
```

<span data-ttu-id="4d622-145">Der folgende Code enthält ein Beispiel für adaptive Karten, die als Reaktion auf den Aufruf durch `adaptiveCard/action` automatische Aktualisierung für Schritt 6 gesendet werden:</span><span class="sxs-lookup"><span data-stu-id="4d622-145">The following code provides an example of Adaptive Cards sent as response of `adaptiveCard/action` invoke through automatic refresh for step 6:</span></span>

```JSON
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "version": "1.4",
  "refresh": {
    "action": {
      "type": "Action.Execute",
      "title": "Refresh",
      "verb": "acceptRejectView"
    },
    "userIds": ["<Megan's user MRI>"]
  },
  "body": [
    {
      "type": "TextBlock",
      "text": "Approval Request B12"
    },
    {
      "type": "TextBlock",
      "text": "Submitted by **Alex**"
    },
    {
      "type": "TextBlock",
      "text": "Approval pending from **Megan**"
    },
    {
      "type": "TextBlock",
      "text": "Approved by **Nestor**"
    }
  ],
  "actions": [
    {
      "type": "Action.Execute",
      "title": "Approve",
      "verb": "approve",
      "data": {
            "more info": "<more info>"
      }
    },
    {
      "type": "Action.Execute",
      "title": "Reject",
      "verb": "reject",
      "data": {
            "more info": "<more info>"
      }
    }
  ]
}
```

<span data-ttu-id="4d622-146">Der folgende Code enthält ein Beispiel für adaptive Karten, die als Antwort auf und für die Schritte `adaptiveCard/action` `message edit` 7 und 8 gesendet werden:</span><span class="sxs-lookup"><span data-stu-id="4d622-146">The following code provides an example of Adaptive Cards sent as response of `adaptiveCard/action` and `message edit` for steps 7 and 8:</span></span>

```JSON
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "version": "1.4",
  "refresh": {
    "action": {
      "type": "Action.Execute",
      "title": "Refresh",
      "verb": "acceptRejectView"
    },
    "userIds": []
  },
  "body": [
    {
      "type": "TextBlock",
      "text": "Asset Request B12"
    },
    {
      "type": "TextBlock",
      "text": "Submitted by **Alex**"
    },
    {
      "type": "TextBlock",
      "text": "Approved by **Nestor and Megan**"
    }
  ]
}
```

## <a name="see-also"></a><span data-ttu-id="4d622-147">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="4d622-147">See also</span></span>

* [<span data-ttu-id="4d622-148">Arbeiten mit universellen Aktionen für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="4d622-148">Work with Universal Actions for Adaptive Cards</span></span>](Work-with-universal-actions-for-adaptive-cards.md)
* [<span data-ttu-id="4d622-149">Benutzerspezifische Ansichten</span><span class="sxs-lookup"><span data-stu-id="4d622-149">User Specific Views</span></span>](User-Specific-Views.md)
