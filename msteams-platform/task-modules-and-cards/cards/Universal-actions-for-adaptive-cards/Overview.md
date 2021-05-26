---
title: Übersicht über universelle Aktionen für adaptive Karten
description: Eine kurze Übersicht über universelle Aktionen für adaptive Karten.
ms.topic: overview
localization_priority: Normal
ms.openlocfilehash: 8bdbc488c68bf9bef79363f1a22d66e63ec32e08
ms.sourcegitcommit: 999f5c607671e088ea8a461fa7dbb63f8d61c39b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2021
ms.locfileid: "52649717"
---
# <a name="universal-actions-for-adaptive-cards"></a><span data-ttu-id="7f8b5-103">Universal-Aktionen für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="7f8b5-103">Universal Actions for Adaptive Cards</span></span>

<span data-ttu-id="7f8b5-104">Universelle Aktionen für adaptive Karten entwickelten sich aus entwicklerfeedback, dass das Layout und Rendering für adaptive Karten zwar universell war, die Aktionsbehandlung jedoch nicht war.</span><span class="sxs-lookup"><span data-stu-id="7f8b5-104">Universal Actions for Adaptive Cards evolved from developer feedback that even though layout and rendering for Adaptive Cards was universal, action handling was not.</span></span> <span data-ttu-id="7f8b5-105">Auch wenn ein Entwickler dieselbe Karte an verschiedene Orte senden wollte, muss er die Aktionen anders behandeln.</span><span class="sxs-lookup"><span data-stu-id="7f8b5-105">Even if a developer wanted to send the same card to different places, they have to handle actions differently.</span></span>

<span data-ttu-id="7f8b5-106">Universelle Aktionen für adaptive Karten bietet den Bot als allgemeines Back-End für die Behandlung von Aktionen und führt einen neuen Aktionstyp ein, der appsübergreifend funktioniert, z. B. `Action.Execute` Teams und Outlook.</span><span class="sxs-lookup"><span data-stu-id="7f8b5-106">Universal Actions for Adaptive Cards brings the bot as the common backend for handling actions and introduces a new action type, `Action.Execute`, which works across apps, such as Teams and Outlook.</span></span>

<span data-ttu-id="7f8b5-107">Dieses Dokument hilft Ihnen zu verstehen, wie Sie das Modell für universelle Aktionen verwenden können, um die Benutzererfahrung bei der Interaktion mit adaptiven Karten über Plattformen und Anwendungen hinweg zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="7f8b5-107">This document helps you to understand how you can use Universal Actions model to enhance user experience of interacting with Adaptive Cards across platforms and applications.</span></span>

> [!NOTE]
> <span data-ttu-id="7f8b5-108">Unterstützung für universelle Aktionen für adaptive Karten ist nur für Karten verfügbar, die vom Bot gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="7f8b5-108">Support for Universal Actions for Adaptive Cards is only available for cards sent by bot.</span></span> <span data-ttu-id="7f8b5-109">Unterstützung für Karten, die über das Verfassenfeld gesendet werden, und link-Entf?ndungskarten werden in Kürze verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="7f8b5-109">Support for cards sent through compose box and link unfurling cards is coming soon.</span></span>

## <a name="enhance-user-experiences-with-universal-actions-for-adaptive-cards"></a><span data-ttu-id="7f8b5-110">Verbessern der Benutzererfahrung mit universellen Aktionen für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="7f8b5-110">Enhance user experiences with Universal Actions for Adaptive Cards</span></span>

<span data-ttu-id="7f8b5-111">Universelle Aktionen für adaptive Karten verbessern die Benutzerfreundlichkeit, indem die folgenden Szenarien aktiviert werden:</span><span class="sxs-lookup"><span data-stu-id="7f8b5-111">Universal Actions for Adaptive Cards enhances user experience by enabling the following scenarios:</span></span>

* [<span data-ttu-id="7f8b5-112">Universelle Aktionen</span><span class="sxs-lookup"><span data-stu-id="7f8b5-112">Universal Actions</span></span>](#universal-actions)
* [<span data-ttu-id="7f8b5-113">Benutzerspezifische Ansichten</span><span class="sxs-lookup"><span data-stu-id="7f8b5-113">User Specific Views</span></span>](#user-specific-views)
* [<span data-ttu-id="7f8b5-114">Sequenzielle Workflowunterstützung</span><span class="sxs-lookup"><span data-stu-id="7f8b5-114">Sequential Workflow support</span></span>](#sequential-workflow-support)
* [<span data-ttu-id="7f8b5-115">Aktuelle Ansichten</span><span class="sxs-lookup"><span data-stu-id="7f8b5-115">Up to date views</span></span>](#up-to-date-views)

### <a name="universal-actions"></a><span data-ttu-id="7f8b5-116">Universelle Aktionen</span><span class="sxs-lookup"><span data-stu-id="7f8b5-116">Universal Actions</span></span>

<span data-ttu-id="7f8b5-117">Vor den universellen Aktionen für adaptive Karten haben verschiedene Hosts unterschiedliche Aktionsmodelle bereitgestellt:</span><span class="sxs-lookup"><span data-stu-id="7f8b5-117">Before the Universal Actions for Adaptive Cards, different hosts provided different action models as follows:</span></span>

* <span data-ttu-id="7f8b5-118">Teams oder Bots verwendet , ein Ansatz, der das tatsächliche Kommunikationsmodell auf `Action.Submit` den zugrunde liegenden Kanal ausdebt.</span><span class="sxs-lookup"><span data-stu-id="7f8b5-118">Teams or bots used `Action.Submit`, an approach which defers the actual communication model to the underlying channel.</span></span>
* <span data-ttu-id="7f8b5-119">Outlook `Action.Http` verwendet, um mit dem Back-End-Dienst zu kommunizieren, der explizit in der Nutzlast der adaptiven Karte angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="7f8b5-119">Outlook used `Action.Http` to communicate with the backend service explicitly specified in the Adaptive Card payload.</span></span>

<span data-ttu-id="7f8b5-120">Die folgende Abbildung zeigt das aktuelle inkonsistente Aktionsmodell:</span><span class="sxs-lookup"><span data-stu-id="7f8b5-120">The following image shows the current inconsistent action model:</span></span>

:::image type="content" source="~/assets/images/adaptive-cards/current-teams-outlook-action-model.png" alt-text="Inkonsistentes Aktionsmodell":::

<span data-ttu-id="7f8b5-122">Mit den universellen Aktionen für adaptive Karten können Sie aktionen für `Action.Execute` verschiedene Plattformen verwenden.</span><span class="sxs-lookup"><span data-stu-id="7f8b5-122">With the Universal Actions for Adaptive Cards, you can use `Action.Execute` for action handling across different platforms.</span></span> <span data-ttu-id="7f8b5-123">`Action.Execute`funktioniert über Hubs hinweg, Teams und Outlook.</span><span class="sxs-lookup"><span data-stu-id="7f8b5-123">`Action.Execute` works across hubs including Teams and Outlook.</span></span> <span data-ttu-id="7f8b5-124">Darüber hinaus kann eine adaptive Karte als Antwort für eine `Action.Execute` ausgelöste Aufrufanforderung zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="7f8b5-124">In addition, an Adaptive Card can be returned as response for an `Action.Execute` triggered invoke request.</span></span>

<span data-ttu-id="7f8b5-125">Die folgende Abbildung zeigt das neue Universelle Aktionsmodell:</span><span class="sxs-lookup"><span data-stu-id="7f8b5-125">The following image shows the new Universal Action model:</span></span>

:::image type="content" source="~/assets/images/adaptive-cards/universal-action-model.png" alt-text="Neue universelle Aktionen für adaptive Karten":::

<span data-ttu-id="7f8b5-127">Sie können nun dieselbe Karte sowohl an Teams als auch Outlook senden und sie mithilfe des zugrunde liegenden Bots synchron halten.</span><span class="sxs-lookup"><span data-stu-id="7f8b5-127">You can now send the same card to both, Teams and Outlook, and keep them in sync with each other using the underlying bot.</span></span> <span data-ttu-id="7f8b5-128">Jede Aktion, die auf beiden Plattformen ergriffen wird, wird mit diesem Build einmal für die andere *übernommen,* und das Modell wird an beliebiger Stelle (Universelle Aktionen für adaptive Karten) bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="7f8b5-128">Any action taken on either platform is reflected to the other with this *build once, deploy anywhere* (Universal Actions for Adaptive Cards) model.</span></span>

<span data-ttu-id="7f8b5-129">Die folgende Abbildung zeigt die universellen Aktionen für adaptive Karten für Teams und Outlook:</span><span class="sxs-lookup"><span data-stu-id="7f8b5-129">The following image depicts the Universal Actions for Adaptive Cards for both Teams and Outlook:</span></span>

# <a name="mobile"></a>[<span data-ttu-id="7f8b5-130">Mobil</span><span class="sxs-lookup"><span data-stu-id="7f8b5-130">Mobile</span></span>](#tab/mobile)

:::image type="content" source="~/assets/images/adaptive-cards/mobile-universal-bots-teams-outlook.jpg" alt-text="Mobile gleiche Karte für Teams und Outlook":::

# <a name="desktop"></a>[<span data-ttu-id="7f8b5-132">Desktop</span><span class="sxs-lookup"><span data-stu-id="7f8b5-132">Desktop</span></span>](#tab/desktop)

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-teams-outlook.png" alt-text="Gleiche Karte für Teams und Outlook":::

* * *

### <a name="user-specific-views"></a><span data-ttu-id="7f8b5-134">Benutzerspezifische Ansichten</span><span class="sxs-lookup"><span data-stu-id="7f8b5-134">User Specific Views</span></span>

<span data-ttu-id="7f8b5-135">Heute sieht jeder Benutzer im Teams oder Kanal genau die gleichen Ansichts- und Schaltflächenaktionen auf der adaptiven Karte.</span><span class="sxs-lookup"><span data-stu-id="7f8b5-135">Today every user in the Teams chat or channel sees the exact same view and button actions on the Adaptive Card.</span></span> <span data-ttu-id="7f8b5-136">In bestimmten Szenarien ist es jedoch erforderlich, dass bestimmte Benutzer unterschiedlich handeln und zugriff auf unterschiedliche Informationen innerhalb desselben Chats oder Kanals haben.</span><span class="sxs-lookup"><span data-stu-id="7f8b5-136">However, in certain scenarios there is a requirement for certain users to act differently and have access to different information within the same chat or channel.</span></span>

<span data-ttu-id="7f8b5-137">Wenn Sie beispielsweise eine Vorfallberichtskarte in einem Chat oder Kanal senden, muss nur dem Benutzer, dem der Vorfall zugewiesen ist, eine **Schaltfläche Auflösen angezeigt** werden.</span><span class="sxs-lookup"><span data-stu-id="7f8b5-137">For example, if you send an incident reporting card in a chat or channel, only the user who is assigned the incident must see a **Resolve** button.</span></span> <span data-ttu-id="7f8b5-138">Andererseits muss dem Ersteller des  Vorfalls eine Schaltfläche Bearbeiten angezeigt werden, und alle anderen Benutzer dürfen nur Details des Vorfalls anzeigen.</span><span class="sxs-lookup"><span data-stu-id="7f8b5-138">On the other hand, the incident creator must see an **Edit** button and all other users must only be able to view details of the incident.</span></span> <span data-ttu-id="7f8b5-139">Dies wird durch benutzerspezifische Ansichten ermöglicht, die von der Eigenschaft aktiviert `refresh` werden.</span><span class="sxs-lookup"><span data-stu-id="7f8b5-139">This is made possible by User Specific Views that is enabled by the `refresh` property.</span></span>

<span data-ttu-id="7f8b5-140">Die folgende Abbildung zeigt ein Beispiel für eine Ticketing Messaging Extension (ME), bei der verschiedenen Benutzern im Chat basierend auf der Anforderung unterschiedliche Aktionen angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="7f8b5-140">The following image shows an example of a ticketing messaging extension (ME) where different users in the chat are shown different actions based on the requirement:</span></span>

# <a name="mobile"></a>[<span data-ttu-id="7f8b5-141">Mobil</span><span class="sxs-lookup"><span data-stu-id="7f8b5-141">Mobile</span></span>](#tab/mobile)

:::image type="content" source="~/assets/images/adaptive-cards/mobile-universal-bots-incident-management.jpg" alt-text="Benutzerspezifische Ansichten für mobile Benutzer":::

# <a name="desktop"></a>[<span data-ttu-id="7f8b5-143">Desktop</span><span class="sxs-lookup"><span data-stu-id="7f8b5-143">Desktop</span></span>](#tab/desktop)

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-incident-management.png" alt-text="Benutzerspezifische Ansichten":::

* * *

<span data-ttu-id="7f8b5-145">Weitere Informationen finden Sie [unter Beispiel für benutzerspezifische Ansichten](User-Specific-Views.md).</span><span class="sxs-lookup"><span data-stu-id="7f8b5-145">For more information, see [sample for User Specific Views](User-Specific-Views.md).</span></span>

### <a name="sequential-workflow-support"></a><span data-ttu-id="7f8b5-146">Sequenzielle Workflowunterstützung</span><span class="sxs-lookup"><span data-stu-id="7f8b5-146">Sequential Workflow support</span></span>

<span data-ttu-id="7f8b5-147">Mithilfe der Sequenziellen Workflowunterstützung können Benutzer eine Reihe von Workflows ohne separates Senden unterschiedlicher Karten nutzen.</span><span class="sxs-lookup"><span data-stu-id="7f8b5-147">With Sequential Workflow support, users can progress through a series of workflows without sending different cards separately.</span></span> <span data-ttu-id="7f8b5-148">Dies wird durch die Möglichkeit `Action.Execute` ermöglicht, eine adaptive Karte als Reaktion auf eine Aktion zurück zu geben.</span><span class="sxs-lookup"><span data-stu-id="7f8b5-148">This is made possible by the ability of `Action.Execute` to return an Adaptive Card in response to an action.</span></span> <span data-ttu-id="7f8b5-149">Darüber hinaus kann jeder Benutzer im Chat oder Kanal über seinen Workflow weiterkommen, ohne die Karte für andere Benutzer im Chat zu ändern.</span><span class="sxs-lookup"><span data-stu-id="7f8b5-149">Also, any user in the chat or channel can progress through their workflow without modifying the card for other users in the chat.</span></span>

<span data-ttu-id="7f8b5-150">Die folgende Abbildung zeigt ein Beispiel für einen Bot für die Essensbestellung:</span><span class="sxs-lookup"><span data-stu-id="7f8b5-150">The following image illustrates a food ordering bot example:</span></span> <br/>

<img src="~/assets/images/bots/sequentialWorkflow.gif" alt="Sequential Workflow" width="400"/>

<span data-ttu-id="7f8b5-151">Die folgende Abbildung zeigt die verschiedenen Zustände für verschiedene Benutzer im Chat oder Kanal:</span><span class="sxs-lookup"><span data-stu-id="7f8b5-151">The following image shows the various states for different users in the chat or channel:</span></span>

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-catering-bot.png" alt-text="Zustände des Cateringbots":::

<span data-ttu-id="7f8b5-153">Weitere Informationen finden Sie unter [Beispiel für Sequenzieller Workflow](Sequential-Workflows.md).</span><span class="sxs-lookup"><span data-stu-id="7f8b5-153">For more information, see [sample for Sequential Workflow](Sequential-Workflows.md).</span></span>

### <a name="up-to-date-views"></a><span data-ttu-id="7f8b5-154">Aktuelle Ansichten</span><span class="sxs-lookup"><span data-stu-id="7f8b5-154">Up to date views</span></span>

<span data-ttu-id="7f8b5-155">Sie können adaptive Karten erstellen, die automatisch aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="7f8b5-155">You can create Adaptive Cards that update automatically.</span></span> <span data-ttu-id="7f8b5-156">Dies kann z. B. eine Genehmigungsanforderung sein, die von einem Benutzer gesendet wurde.</span><span class="sxs-lookup"><span data-stu-id="7f8b5-156">For example, it can be an approval request sent by a user.</span></span> <span data-ttu-id="7f8b5-157">Nach der Genehmigung muss die Karte automatisch Details zur Genehmigungszeit der Anforderung und zur Genehmigung der Anforderung anzeigen.</span><span class="sxs-lookup"><span data-stu-id="7f8b5-157">After approval, the card must automatically display details about the request approval time and who approved the request.</span></span> <span data-ttu-id="7f8b5-158">Mit dem Aktualisierungsmodell können Sie solche aktuellen Ansichten bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="7f8b5-158">The refresh model enables you to provide such up to date views.</span></span> <span data-ttu-id="7f8b5-159">Die folgende Abbildung zeigt einen mehrstufigen Genehmigungsfluss und wie die Ansichten für verschiedene Benutzer angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="7f8b5-159">The following image shows a multi-step approval flow and how the views for different users is shown.</span></span>

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-up-to-date-views.png" alt-text="Aktuelle benutzerspezifische Ansichten":::

<span data-ttu-id="7f8b5-161">Weitere Informationen finden Sie [unter Beispiel für aktuelle Ansichten](Up-To-Date-Views.md).</span><span class="sxs-lookup"><span data-stu-id="7f8b5-161">For more information, see [sample for up to date views](Up-To-Date-Views.md).</span></span>

<span data-ttu-id="7f8b5-162">Jetzt können Sie verstehen, wie adaptive Karten mit dem neuen Modell für universelle Aktionen transformiert werden können, um eine eindeutige und verbesserte Benutzeroberfläche zu bieten.</span><span class="sxs-lookup"><span data-stu-id="7f8b5-162">Now, you can understand how Adaptive Cards can be transformed with the new Universal Actions model to provide a unique and enhanced user experience.</span></span>

## <a name="adaptive-cards-and-the-new-universal-actions-model"></a><span data-ttu-id="7f8b5-163">Adaptive Karten und das neue Modell für universelle Aktionen</span><span class="sxs-lookup"><span data-stu-id="7f8b5-163">Adaptive Cards and the new Universal Actions model</span></span>

<span data-ttu-id="7f8b5-164">Adaptive Karten sind eine Kombination aus Inhalten, z. B. Text und Grafiken, und Aktionen, die von einem Benutzer ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="7f8b5-164">Adaptive Cards are a combination of content, such as text and graphics, and actions that can be performed by a user.</span></span> <span data-ttu-id="7f8b5-165">Weitere Informationen finden Sie unter [Adaptive Karten](http://adaptivecards.io/).</span><span class="sxs-lookup"><span data-stu-id="7f8b5-165">For more information, see [Adaptive Cards](http://adaptivecards.io/).</span></span> <span data-ttu-id="7f8b5-166">Die neuen universellen Aktionen für adaptive Karten ermöglichen eine allgemeine Behandlung der adaptiven Kartenaktionen über Plattformen und Anwendungen hinweg.</span><span class="sxs-lookup"><span data-stu-id="7f8b5-166">The new Universal Actions for Adaptive Cards enables a common handling of the Adaptive Card actions across platforms and applications.</span></span> <span data-ttu-id="7f8b5-167">Weitere Informationen finden Sie unter [Universelles Aktionsmodell](/adaptive-cards/authoring-cards/universal-action-model).</span><span class="sxs-lookup"><span data-stu-id="7f8b5-167">For more information, see [Universal Action Model](/adaptive-cards/authoring-cards/universal-action-model).</span></span>

<span data-ttu-id="7f8b5-168">[Das Dokument "Arbeiten mit universellen](Work-with-universal-actions-for-adaptive-cards.md) Aktionen für adaptive Karten" führt Sie durch die Schritte, um die Funktionen von Universelle Aktionen für adaptive Karten für Ihre Lösung zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="7f8b5-168">[Work with Universal Actions for Adaptive Cards](Work-with-universal-actions-for-adaptive-cards.md) document takes you through the steps to use the capabilities of Universal Actions for Adaptive Cards for your solution.</span></span>

## <a name="see-also"></a><span data-ttu-id="7f8b5-169">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="7f8b5-169">See also</span></span>

* [<span data-ttu-id="7f8b5-170">Was sind Bots?</span><span class="sxs-lookup"><span data-stu-id="7f8b5-170">What are bots</span></span>](~/bots/what-are-bots.md)
* [<span data-ttu-id="7f8b5-171">Übersicht über adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="7f8b5-171">Adaptive Cards overview</span></span>](~/task-modules-and-cards/what-are-cards.md)
* [<span data-ttu-id="7f8b5-172">Adaptive Karten @ Microsoft Build 2020</span><span class="sxs-lookup"><span data-stu-id="7f8b5-172">Adaptive Cards @ Microsoft Build 2020</span></span>](https://youtu.be/hEBhwB72Qn4?t=1393)
* [<span data-ttu-id="7f8b5-173">Adaptive Karten @ Ignite 2020</span><span class="sxs-lookup"><span data-stu-id="7f8b5-173">Adaptive Cards @ Ignite 2020</span></span>](https://techcommunity.microsoft.com/t5/video-hub/elevate-user-experiences-with-teams-and-adaptive-cards/m-p/1689460)

## <a name="next-step"></a><span data-ttu-id="7f8b5-174">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="7f8b5-174">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7f8b5-175">Mit Universal-Aktionen für adaptive Karten arbeiten</span><span class="sxs-lookup"><span data-stu-id="7f8b5-175">Work with Universal Actions for Adaptive Cards</span></span>](Work-with-universal-actions-for-adaptive-cards.md)
