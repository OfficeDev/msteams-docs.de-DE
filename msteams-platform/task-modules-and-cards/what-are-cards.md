---
title: Einführung in Karten
description: Beschreibt Karten und deren Verwendung in Bots, Connectors und Messagingerweiterungen
localization_priority: Normal
ms.topic: conceptual
keywords: Connectors bots karten messaging
ms.openlocfilehash: acf5dc95b742a433c092be9e293d589b5919bb4d
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020268"
---
# <a name="cards"></a><span data-ttu-id="70296-104">Karten</span><span class="sxs-lookup"><span data-stu-id="70296-104">Cards</span></span>

<span data-ttu-id="70296-105">Eine *Karte* ist ein Benutzeroberflächencontainer für kurze oder verwandte Informationen.</span><span class="sxs-lookup"><span data-stu-id="70296-105">A *card* is a user-interface (UI) container for short or related pieces of information.</span></span> <span data-ttu-id="70296-106">Karten können mehrere Eigenschaften und Anlagen aufweisen.</span><span class="sxs-lookup"><span data-stu-id="70296-106">Cards can have multiple properties and attachments.</span></span> <span data-ttu-id="70296-107">Karten können Schaltflächen enthalten, die [Kartenaktionen auslösen können.](~/task-modules-and-cards/cards/cards-actions.md)</span><span class="sxs-lookup"><span data-stu-id="70296-107">Cards can include buttons which can trigger [Card actions](~/task-modules-and-cards/cards/cards-actions.md).</span></span>

## <a name="adaptive-cards"></a><span data-ttu-id="70296-108">Adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="70296-108">Adaptive cards</span></span>

<span data-ttu-id="70296-109">[Adaptive Karten](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card) sind eine neue produktübergreifende Spezifikation für Karten in Microsoft-Produkten, einschließlich Bots, Cortana, Outlook und Windows.</span><span class="sxs-lookup"><span data-stu-id="70296-109">[Adaptive cards](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card) are a new cross product specification for cards in Microsoft products including Bots, Cortana, Outlook, and Windows.</span></span> <span data-ttu-id="70296-110">Sie sind der empfohlene Kartentyp für die neue Teams-Entwicklung.</span><span class="sxs-lookup"><span data-stu-id="70296-110">They are the recommended card type for new Teams development.</span></span> <span data-ttu-id="70296-111">Allgemeine Informationen vom Team für adaptive Karten finden Sie unter [Adaptive Cards Overview](/adaptive-cards).</span><span class="sxs-lookup"><span data-stu-id="70296-111">For general information from the Adaptive cards team see [Adaptive Cards Overview](/adaptive-cards).</span></span> <span data-ttu-id="70296-112">Sie können adaptive Karten überall verwenden, an der Sie vorhandene Hero-Karten, Office365-Karten und Miniaturansichtskarten verwenden können.</span><span class="sxs-lookup"><span data-stu-id="70296-112">You can use adaptive cards anywhere you can use existing Hero cards, Office365 cards, and Thumbnail cards.</span></span>

<span data-ttu-id="70296-113">Zusätzlich zu adaptiven Karten unterstützt Teams zwei weitere Kartentypen:</span><span class="sxs-lookup"><span data-stu-id="70296-113">In addition to Adaptive Cards, Teams supports two other types of cards:</span></span>

* <span data-ttu-id="70296-114">Connectorkarten, die als Teil von Office 365-Connectors verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="70296-114">Connector Cards, used as part of Office 365 connectors.</span></span>
* <span data-ttu-id="70296-115">Einfache Karten aus dem Botframework, z. B. Miniaturansichten und Heldenkarten.</span><span class="sxs-lookup"><span data-stu-id="70296-115">Simple cards from the bot framework, such as the thumbnail and hero cards.</span></span>

<span data-ttu-id="70296-116">Diese Kartentypen werden in der Teams-Kartenreferenz [genauer beschrieben.](~/task-modules-and-cards/cards/cards-reference.md)</span><span class="sxs-lookup"><span data-stu-id="70296-116">These card types are described more fully in the [Teams Card Reference](~/task-modules-and-cards/cards/cards-reference.md).</span></span>

<span data-ttu-id="70296-117">Teams verwendet Karten an drei verschiedenen Orten:</span><span class="sxs-lookup"><span data-stu-id="70296-117">Teams uses cards in three different places:</span></span>

* <span data-ttu-id="70296-118">Connectors</span><span class="sxs-lookup"><span data-stu-id="70296-118">Connectors</span></span>
* <span data-ttu-id="70296-119">Bots</span><span class="sxs-lookup"><span data-stu-id="70296-119">Bots</span></span>
* <span data-ttu-id="70296-120">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="70296-120">Messaging extensions</span></span>

## <a name="adaptive-cards-and-incoming-webhooks"></a><span data-ttu-id="70296-121">Adaptive Karten und eingehende Webhooks</span><span class="sxs-lookup"><span data-stu-id="70296-121">Adaptive cards and incoming webhooks</span></span>

> [!NOTE]
>
> <span data-ttu-id="70296-122">✔ Alle systemeigenen adaptiven Kartenschemaelemente, mit Ausnahme von `Action.Submit`, werden vollständig unterstützt.</span><span class="sxs-lookup"><span data-stu-id="70296-122">✔ All native adaptive card schema elements, except `Action.Submit`, are fully supported.</span></span>
>
> <span data-ttu-id="70296-123">✔ Die unterstützten Aktionen sind [**Action.OpenURL**](https://adaptivecards.io/explorer/Action.OpenUrl.html), [**Action.ShowCard**](https://adaptivecards.io/explorer/Action.ShowCard.html)und [**Action.ToggleVisibility**](https://adaptivecards.io/explorer/Action.ToggleVisibility.html).</span><span class="sxs-lookup"><span data-stu-id="70296-123">✔ The supported actions are [**Action.OpenURL**](https://adaptivecards.io/explorer/Action.OpenUrl.html), [**Action.ShowCard**](https://adaptivecards.io/explorer/Action.ShowCard.html), and [**Action.ToggleVisibility**](https://adaptivecards.io/explorer/Action.ToggleVisibility.html).</span></span>

## <a name="cards-in-connectors"></a><span data-ttu-id="70296-124">Karten in Connectors</span><span class="sxs-lookup"><span data-stu-id="70296-124">Cards in Connectors</span></span>

<span data-ttu-id="70296-125">Karten wurden zunächst als Teil von Outlook und Office 365 definiert und als Teil von Office 365 Connectors verwendet.</span><span class="sxs-lookup"><span data-stu-id="70296-125">Cards were first defined as part of Outlook and Office 365, and are used as part of Office 365 Connectors.</span></span> <span data-ttu-id="70296-126">Wie viele office 365-Anwendungen unterstützt Teams Connectors.</span><span class="sxs-lookup"><span data-stu-id="70296-126">Like many Office 365 applications, Teams supports Connectors.</span></span> <span data-ttu-id="70296-127">Weitere Informationen zu Connectors in [Office 365 Connectors für Microsoft Teams](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md)und die Spezifikation für Karten in Connectors finden Sie unter [Actionable message card reference](/outlook/actionable-messages/card-reference).</span><span class="sxs-lookup"><span data-stu-id="70296-127">You can learn more about Connectors in [Office 365 Connectors for Microsoft Teams](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md), and find the specification for cards in connectors in [Actionable message card reference](/outlook/actionable-messages/card-reference).</span></span>

## <a name="cards-in-bots"></a><span data-ttu-id="70296-128">Karten in Bots</span><span class="sxs-lookup"><span data-stu-id="70296-128">Cards in Bots</span></span>

<span data-ttu-id="70296-129">Das Microsoft Bot Framework hat die Kartenspezifikation erweitert, indem eine Reihe vordefinierter Karten hinzugefügt wurde, die Bots als Teil von Botnachrichten verwenden können.</span><span class="sxs-lookup"><span data-stu-id="70296-129">The Microsoft Bot Framework extended the cards specification by adding a set of predefined cards that bots could use as part of bot messages.</span></span> <span data-ttu-id="70296-130">Teams unterstützt Bots, die das Bot Framework verwenden, unterstützt jedoch einen etwas anderen Satz dieser Karten.</span><span class="sxs-lookup"><span data-stu-id="70296-130">Teams supports bots using the Bot Framework but it supports a slightly different set of these cards.</span></span> <span data-ttu-id="70296-131">Allgemeine Informationen zu Karten in Bot Framework finden Sie unter Hinzufügen von [Rich-Card-Anlagen zu Nachrichten.](/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards)</span><span class="sxs-lookup"><span data-stu-id="70296-131">General information on cards in Bot Framework can be found in [Add rich card attachments to messages](/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards).</span></span> <span data-ttu-id="70296-132">Diese Karten werden in *Teams als einfache Karten* bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="70296-132">These cards are called *simple cards* in Teams.</span></span>

<span data-ttu-id="70296-133">Bots in Teams können jede Art von Karte verwenden: einfach, connector oder adaptive.</span><span class="sxs-lookup"><span data-stu-id="70296-133">Bots in Teams can use any type of card: simple, connector or adaptive.</span></span> <span data-ttu-id="70296-134">Karten, die von Bots in Teams unterstützt werden, finden Sie unter [Teams Card Reference](~/task-modules-and-cards/cards/cards-reference.md).</span><span class="sxs-lookup"><span data-stu-id="70296-134">Cards that are supported by bots in Teams are detailed in [Teams Card Reference](~/task-modules-and-cards/cards/cards-reference.md).</span></span>  

## <a name="cards-in-messaging-extensions"></a><span data-ttu-id="70296-135">Karten in Messagingerweiterungen</span><span class="sxs-lookup"><span data-stu-id="70296-135">Cards in Messaging Extensions</span></span>

<span data-ttu-id="70296-136">[Messaging-Erweiterungen](~/messaging-extensions/what-are-messaging-extensions.md) können auch eine Karte zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="70296-136">[Messaging Extensions](~/messaging-extensions/what-are-messaging-extensions.md) can also return a card.</span></span> <span data-ttu-id="70296-137">Messagingerweiterungen können jede Art von Karte verwenden: einfach, connector oder adaptive.</span><span class="sxs-lookup"><span data-stu-id="70296-137">Messaging extensions can use any type of card: simple, connector or adaptive.</span></span> <span data-ttu-id="70296-138">Diese Karten finden Sie in der [Teams-Kartenreferenz](~/task-modules-and-cards/cards/cards-reference.md).</span><span class="sxs-lookup"><span data-stu-id="70296-138">These cards are found in the [Teams Card Reference](~/task-modules-and-cards/cards/cards-reference.md).</span></span>

## <a name="card-reference"></a><span data-ttu-id="70296-139">Kartenreferenz</span><span class="sxs-lookup"><span data-stu-id="70296-139">Card reference</span></span>

<span data-ttu-id="70296-140">Alle von Teams verwendeten Karten sind in der [Teams-Kartenreferenz aufgeführt.](~/task-modules-and-cards/cards/cards-reference.md)</span><span class="sxs-lookup"><span data-stu-id="70296-140">All cards used by Teams are listed in the [Teams Card Reference](~/task-modules-and-cards/cards/cards-reference.md).</span></span> <span data-ttu-id="70296-141">In diesem Verweis werden auch die Unterschiede zwischen Bot Framework-Karten und -Karten in Teams beschrieben.</span><span class="sxs-lookup"><span data-stu-id="70296-141">This reference also describes differences between Bot Framework cards and cards in Teams.</span></span>
