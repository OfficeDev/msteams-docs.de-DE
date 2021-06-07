---
title: Übersicht über universelle Aktionen für adaptive Karten
description: Eine kurze Übersicht über universelle Aktionen für adaptive Karten.
ms.topic: overview
localization_priority: Normal
ms.openlocfilehash: f8980743954c4dff2ced464bc599439c7519cefe
ms.sourcegitcommit: d1d1143e285cac5f23590ccba5389616d08f94b3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2021
ms.locfileid: "52781618"
---
# <a name="universal-actions-for-adaptive-cards"></a><span data-ttu-id="e6304-103">Universal-Aktionen für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="e6304-103">Universal Actions for Adaptive Cards</span></span>

<span data-ttu-id="e6304-104">Universelle Aktionen für adaptive Karten haben sich aus dem Feedback von Entwicklern entwickelt, dass das Layout und Rendering für adaptive Karten zwar universell war, die Aktionsbehandlung jedoch nicht war.</span><span class="sxs-lookup"><span data-stu-id="e6304-104">Universal Actions for Adaptive Cards evolved from developer feedback that even though layout and rendering for Adaptive Cards was universal, action handling was not.</span></span> <span data-ttu-id="e6304-105">Auch wenn ein Entwickler dieselbe Karte an verschiedene Orte senden möchte, müssen aktionen unterschiedlich behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="e6304-105">Even if a developer wanted to send the same card to different places, they have to handle actions differently.</span></span>

<span data-ttu-id="e6304-106">Universelle Aktionen für adaptive Karten stellt den Bot als allgemeines Back-End für die Behandlung von Aktionen bereit und führt einen neuen Aktionstyp ein, `Action.Execute` der appsübergreifend funktioniert, z. B. Teams und Outlook.</span><span class="sxs-lookup"><span data-stu-id="e6304-106">Universal Actions for Adaptive Cards brings the bot as the common backend for handling actions and introduces a new action type, `Action.Execute`, which works across apps, such as Teams and Outlook.</span></span>

<span data-ttu-id="e6304-107">Dieses Dokument hilft Ihnen zu verstehen, wie Sie das Modell für universelle Aktionen verwenden können, um die Benutzerfreundlichkeit der Interaktion mit adaptiven Karten plattform- und anwendungsübergreifend zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="e6304-107">This document helps you to understand how you can use Universal Actions model to enhance user experience of interacting with Adaptive Cards across platforms and applications.</span></span>

> [!NOTE]
> <span data-ttu-id="e6304-108">Unterstützung für universelle Aktionen für adaptive Karten ist nur für Vom Bot gesendete Karten verfügbar.</span><span class="sxs-lookup"><span data-stu-id="e6304-108">Support for Universal Actions for Adaptive Cards is only available for cards sent by bot.</span></span> <span data-ttu-id="e6304-109">Unterstützung für Karten, die über das Feld zum Verfassen gesendet werden, und die Verbreitung von Karten für Links wird in Kürze verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="e6304-109">Support for cards sent through compose box and link unfurling cards is coming soon.</span></span>

## <a name="enhance-user-experiences-with-universal-actions-for-adaptive-cards"></a><span data-ttu-id="e6304-110">Verbessern der Benutzererfahrung mit universellen Aktionen für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="e6304-110">Enhance user experiences with Universal Actions for Adaptive Cards</span></span>

<span data-ttu-id="e6304-111">Universelle Aktionen für adaptive Karten verbessern die Benutzererfahrung, indem die folgenden Szenarien aktiviert werden:</span><span class="sxs-lookup"><span data-stu-id="e6304-111">Universal Actions for Adaptive Cards enhances user experience by enabling the following scenarios:</span></span>

* [<span data-ttu-id="e6304-112">Universelle Aktionen</span><span class="sxs-lookup"><span data-stu-id="e6304-112">Universal Actions</span></span>](#universal-actions)
* [<span data-ttu-id="e6304-113">Benutzerspezifische Ansichten</span><span class="sxs-lookup"><span data-stu-id="e6304-113">User Specific Views</span></span>](#user-specific-views)
* [<span data-ttu-id="e6304-114">Sequenzielle Workflowunterstützung</span><span class="sxs-lookup"><span data-stu-id="e6304-114">Sequential Workflow support</span></span>](#sequential-workflow-support)
* [<span data-ttu-id="e6304-115">Aktuelle Ansichten</span><span class="sxs-lookup"><span data-stu-id="e6304-115">Up to date views</span></span>](#up-to-date-views)

### <a name="universal-actions"></a><span data-ttu-id="e6304-116">Universelle Aktionen</span><span class="sxs-lookup"><span data-stu-id="e6304-116">Universal Actions</span></span>

<span data-ttu-id="e6304-117">Vor den universellen Aktionen für adaptive Karten haben verschiedene Hosts wie folgt unterschiedliche Aktionsmodelle bereitgestellt:</span><span class="sxs-lookup"><span data-stu-id="e6304-117">Before the Universal Actions for Adaptive Cards, different hosts provided different action models as follows:</span></span>

* <span data-ttu-id="e6304-118">Teams oder bots verwendet `Action.Submit` , ein Ansatz, der das tatsächliche Kommunikationsmodell auf den zugrunde liegenden Kanal zurücksetzt.</span><span class="sxs-lookup"><span data-stu-id="e6304-118">Teams or bots used `Action.Submit`, an approach which defers the actual communication model to the underlying channel.</span></span>
* <span data-ttu-id="e6304-119">Outlook `Action.Http` für die Kommunikation mit dem Back-End-Dienst verwendet, der explizit in der Nutzlast der adaptiven Karte angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="e6304-119">Outlook used `Action.Http` to communicate with the backend service explicitly specified in the Adaptive Card payload.</span></span>

<span data-ttu-id="e6304-120">Die folgende Abbildung zeigt das aktuelle inkonsistente Aktionsmodell:</span><span class="sxs-lookup"><span data-stu-id="e6304-120">The following image shows the current inconsistent action model:</span></span>

:::image type="content" source="~/assets/images/adaptive-cards/current-teams-outlook-action-model.png" alt-text="Inkonsistentes Aktionsmodell":::

<span data-ttu-id="e6304-122">Mit den universellen Aktionen für adaptive Karten können Sie `Action.Execute` die Aktionsbehandlung auf verschiedenen Plattformen verwenden.</span><span class="sxs-lookup"><span data-stu-id="e6304-122">With the Universal Actions for Adaptive Cards, you can use `Action.Execute` for action handling across different platforms.</span></span> <span data-ttu-id="e6304-123">`Action.Execute`funktioniert über Hubs hinweg, einschließlich Teams und Outlook.</span><span class="sxs-lookup"><span data-stu-id="e6304-123">`Action.Execute` works across hubs including Teams and Outlook.</span></span> <span data-ttu-id="e6304-124">Darüber hinaus kann eine adaptive Karte als Antwort auf eine `Action.Execute` ausgelöste Aufrufanforderung zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="e6304-124">In addition, an Adaptive Card can be returned as response for an `Action.Execute` triggered invoke request.</span></span>

<span data-ttu-id="e6304-125">Die folgende Abbildung zeigt das neue Modell für universelle Aktionen:</span><span class="sxs-lookup"><span data-stu-id="e6304-125">The following image shows the new Universal Action model:</span></span>

:::image type="content" source="~/assets/images/adaptive-cards/universal-action-model.png" alt-text="Neue universelle Aktionen für adaptive Karten":::

<span data-ttu-id="e6304-127">Sie können jetzt die gleiche Karte an beide senden, Teams und Outlook, und sie mithilfe des zugrunde liegenden Bots miteinander synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="e6304-127">You can now send the same card to both, Teams and Outlook, and keep them in sync with each other using the underlying bot.</span></span> <span data-ttu-id="e6304-128">Alle Aktionen, die auf beiden Plattformen ausgeführt werden, werden mit diesem Build einmal auf die andere Plattform übernommen *und stellen ein beliebiges* Modell (Universelle Aktionen für adaptive Karten) bereit.</span><span class="sxs-lookup"><span data-stu-id="e6304-128">Any action taken on either platform is reflected to the other with this *build once, deploy anywhere* (Universal Actions for Adaptive Cards) model.</span></span>

<span data-ttu-id="e6304-129">Die folgende Abbildung zeigt die universellen Aktionen für adaptive Karten für Teams und Outlook:</span><span class="sxs-lookup"><span data-stu-id="e6304-129">The following image depicts the Universal Actions for Adaptive Cards for both Teams and Outlook:</span></span>

# <a name="mobile"></a>[<span data-ttu-id="e6304-130">Mobil</span><span class="sxs-lookup"><span data-stu-id="e6304-130">Mobile</span></span>](#tab/mobile)

:::image type="content" source="~/assets/images/adaptive-cards/mobile-universal-bots-teams-outlook.jpg" alt-text="Mobile Karte für Teams und Outlook":::

# <a name="desktop"></a>[<span data-ttu-id="e6304-132">Desktop</span><span class="sxs-lookup"><span data-stu-id="e6304-132">Desktop</span></span>](#tab/desktop)

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-teams-outlook.png" alt-text="Dieselbe Karte wie Teams und Outlook":::

* * *

### <a name="user-specific-views"></a><span data-ttu-id="e6304-134">Benutzerspezifische Ansichten</span><span class="sxs-lookup"><span data-stu-id="e6304-134">User Specific Views</span></span>

<span data-ttu-id="e6304-135">Heute sieht jeder Benutzer im Teams Chat oder Kanal genau die gleichen Ansichts- und Schaltflächenaktionen auf der adaptiven Karte.</span><span class="sxs-lookup"><span data-stu-id="e6304-135">Today every user in the Teams chat or channel sees the exact same view and button actions on the Adaptive Card.</span></span> <span data-ttu-id="e6304-136">In bestimmten Szenarien ist es jedoch erforderlich, dass bestimmte Benutzer unterschiedlich handeln und Zugriff auf unterschiedliche Informationen innerhalb desselben Chats oder Kanals haben.</span><span class="sxs-lookup"><span data-stu-id="e6304-136">However, in certain scenarios there is a requirement for certain users to act differently and have access to different information within the same chat or channel.</span></span>

<span data-ttu-id="e6304-137">Wenn Sie beispielsweise eine Karte für die Schadensberichterstattung in einem Chat oder Kanal senden, muss nur dem Benutzer, dem der Vorfall zugewiesen ist, eine Schaltfläche **"Auflösen"** angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="e6304-137">For example, if you send an incident reporting card in a chat or channel, only the user who is assigned the incident must see a **Resolve** button.</span></span> <span data-ttu-id="e6304-138">Andererseits muss dem Ersteller des Vorfalls eine Schaltfläche **"Bearbeiten"** angezeigt werden, und alle anderen Benutzer dürfen nur Details des Vorfalls anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="e6304-138">On the other hand, the incident creator must see an **Edit** button and all other users must only be able to view details of the incident.</span></span> <span data-ttu-id="e6304-139">Dies wird durch benutzerspezifische Ansichten ermöglicht, die von der Eigenschaft aktiviert `refresh` werden.</span><span class="sxs-lookup"><span data-stu-id="e6304-139">This is made possible by User Specific Views that is enabled by the `refresh` property.</span></span>

<span data-ttu-id="e6304-140">Die folgende Abbildung zeigt ein Beispiel für eine Ticketing Messaging Extension (ME), bei der verschiedene Benutzer im Chat basierend auf der Anforderung unterschiedliche Aktionen angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="e6304-140">The following image shows an example of a ticketing messaging extension (ME) where different users in the chat are shown different actions based on the requirement:</span></span>

# <a name="mobile"></a>[<span data-ttu-id="e6304-141">Mobil</span><span class="sxs-lookup"><span data-stu-id="e6304-141">Mobile</span></span>](#tab/mobile)

:::image type="content" source="~/assets/images/adaptive-cards/mobile-universal-bots-incident-management.jpg" alt-text="Benutzerspezifische Ansichten mobiler Benutzer":::

# <a name="desktop"></a>[<span data-ttu-id="e6304-143">Desktop</span><span class="sxs-lookup"><span data-stu-id="e6304-143">Desktop</span></span>](#tab/desktop)

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-incident-management.png" alt-text="Benutzerspezifische Ansichten":::

* * *

<span data-ttu-id="e6304-145">Weitere Informationen finden Sie im [Beispiel für benutzerspezifische Ansichten.](User-Specific-Views.md)</span><span class="sxs-lookup"><span data-stu-id="e6304-145">For more information, see [sample for User Specific Views](User-Specific-Views.md).</span></span>

### <a name="sequential-workflow-support"></a><span data-ttu-id="e6304-146">Sequenzielle Workflowunterstützung</span><span class="sxs-lookup"><span data-stu-id="e6304-146">Sequential Workflow support</span></span>

<span data-ttu-id="e6304-147">Mit sequenzieller Workflowunterstützung können Benutzer eine Reihe von Workflows durchlaufen, ohne separate Karten zu senden.</span><span class="sxs-lookup"><span data-stu-id="e6304-147">With Sequential Workflow support, users can progress through a series of workflows without sending different cards separately.</span></span> <span data-ttu-id="e6304-148">Dies wird durch die Möglichkeit `Action.Execute` ermöglicht, eine adaptive Karte als Reaktion auf eine Aktion zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="e6304-148">This is made possible by the ability of `Action.Execute` to return an Adaptive Card in response to an action.</span></span> <span data-ttu-id="e6304-149">Außerdem kann jeder Benutzer im Chat oder Kanal den Workflow durchlaufen, ohne die Karte für andere Benutzer im Chat zu ändern.</span><span class="sxs-lookup"><span data-stu-id="e6304-149">Also, any user in the chat or channel can progress through their workflow without modifying the card for other users in the chat.</span></span>

<span data-ttu-id="e6304-150">Die folgende Abbildung zeigt ein Beispiel für einen Bot zur Sortierung von Essen:</span><span class="sxs-lookup"><span data-stu-id="e6304-150">The following image illustrates a food ordering bot example:</span></span> <br/>

<img src="~/assets/images/bots/sequentialWorkflow.gif" alt="Sequential Workflow" width="400"/>

<span data-ttu-id="e6304-151">Die folgende Abbildung zeigt die verschiedenen Zustände für verschiedene Benutzer im Chat oder Kanal:</span><span class="sxs-lookup"><span data-stu-id="e6304-151">The following image shows the various states for different users in the chat or channel:</span></span>

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-catering-bot.png" alt-text="Zustände des Bots &quot;Auffüllen&quot;":::

<span data-ttu-id="e6304-153">Weitere Informationen finden Sie im [Beispiel für sequenziellen Workflow.](Sequential-Workflows.md)</span><span class="sxs-lookup"><span data-stu-id="e6304-153">For more information, see [sample for Sequential Workflow](Sequential-Workflows.md).</span></span>

### <a name="up-to-date-views"></a><span data-ttu-id="e6304-154">Aktuelle Ansichten</span><span class="sxs-lookup"><span data-stu-id="e6304-154">Up to date views</span></span>

<span data-ttu-id="e6304-155">Sie können adaptive Karten erstellen, die automatisch aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="e6304-155">You can create Adaptive Cards that update automatically.</span></span> <span data-ttu-id="e6304-156">Dies kann z. B. eine Genehmigungsanforderung sein, die von einem Benutzer gesendet wurde.</span><span class="sxs-lookup"><span data-stu-id="e6304-156">For example, it can be an approval request sent by a user.</span></span> <span data-ttu-id="e6304-157">Nach der Genehmigung muss die Karte automatisch Details zur Genehmigungszeit der Anforderung und zur Person anzeigen, die die Anforderung genehmigt hat.</span><span class="sxs-lookup"><span data-stu-id="e6304-157">After approval, the card must automatically display details about the request approval time and who approved the request.</span></span> <span data-ttu-id="e6304-158">Mit dem Aktualisierungsmodell können Sie so aktuelle Ansichten bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="e6304-158">The refresh model enables you to provide such up to date views.</span></span> <span data-ttu-id="e6304-159">Die folgende Abbildung zeigt einen mehrstufigen Genehmigungsfluss und wie die Ansichten für verschiedene Benutzer angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="e6304-159">The following image shows a multi-step approval flow and how the views for different users is shown.</span></span>

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-up-to-date-views.png" alt-text="Aktuelle benutzerspezifische Ansichten":::

<span data-ttu-id="e6304-161">Weitere Informationen finden Sie im [Beispiel für aktuelle Ansichten.](Up-To-Date-Views.md)</span><span class="sxs-lookup"><span data-stu-id="e6304-161">For more information, see [sample for up to date views](Up-To-Date-Views.md).</span></span>

<span data-ttu-id="e6304-162">Jetzt können Sie verstehen, wie adaptive Karten mit dem neuen Modell für universelle Aktionen transformiert werden können, um eine einzigartige und verbesserte Benutzererfahrung bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="e6304-162">Now, you can understand how Adaptive Cards can be transformed with the new Universal Actions model to provide a unique and enhanced user experience.</span></span>

## <a name="adaptive-cards-and-the-new-universal-actions-model"></a><span data-ttu-id="e6304-163">Adaptive Karten und das neue Modell für universelle Aktionen</span><span class="sxs-lookup"><span data-stu-id="e6304-163">Adaptive Cards and the new Universal Actions model</span></span>

<span data-ttu-id="e6304-164">Adaptive Karten sind eine Kombination aus Inhalten, z. B. Text und Grafiken, und Aktionen, die von einem Benutzer ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="e6304-164">Adaptive Cards are a combination of content, such as text and graphics, and actions that can be performed by a user.</span></span> <span data-ttu-id="e6304-165">Weitere Informationen finden Sie unter [Adaptive Karten.](http://adaptivecards.io/)</span><span class="sxs-lookup"><span data-stu-id="e6304-165">For more information, see [Adaptive Cards](http://adaptivecards.io/).</span></span> <span data-ttu-id="e6304-166">Die neuen universellen Aktionen für adaptive Karten ermöglichen eine allgemeine Behandlung der Aktionen adaptiver Karten über Plattformen und Anwendungen hinweg.</span><span class="sxs-lookup"><span data-stu-id="e6304-166">The new Universal Actions for Adaptive Cards enables a common handling of the Adaptive Card actions across platforms and applications.</span></span> <span data-ttu-id="e6304-167">Weitere Informationen finden Sie unter ["Universelles Aktionsmodell".](/adaptive-cards/authoring-cards/universal-action-model)</span><span class="sxs-lookup"><span data-stu-id="e6304-167">For more information, see [Universal Action Model](/adaptive-cards/authoring-cards/universal-action-model).</span></span>

<span data-ttu-id="e6304-168">Sie können loslegen, indem Sie Szenarien mithilfe der [Schnellstartanleitung](Work-with-universal-actions-for-adaptive-cards.md) aktualisieren und universelle Aktionen nutzen.</span><span class="sxs-lookup"><span data-stu-id="e6304-168">You can get started by updating scenarios using the [quick start guide](Work-with-universal-actions-for-adaptive-cards.md) and leverage Universal Actions.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6304-169">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e6304-169">See also</span></span>

* [<span data-ttu-id="e6304-170">Was sind Bots?</span><span class="sxs-lookup"><span data-stu-id="e6304-170">What are bots</span></span>](~/bots/what-are-bots.md)
* [<span data-ttu-id="e6304-171">Übersicht über adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="e6304-171">Adaptive Cards overview</span></span>](~/task-modules-and-cards/what-are-cards.md)
* [<span data-ttu-id="e6304-172">Adaptive Karten @ Microsoft Build 2020</span><span class="sxs-lookup"><span data-stu-id="e6304-172">Adaptive Cards @ Microsoft Build 2020</span></span>](https://youtu.be/hEBhwB72Qn4?t=1393)
* [<span data-ttu-id="e6304-173">Adaptive Karten @ Ignite 2020</span><span class="sxs-lookup"><span data-stu-id="e6304-173">Adaptive Cards @ Ignite 2020</span></span>](https://techcommunity.microsoft.com/t5/video-hub/elevate-user-experiences-with-teams-and-adaptive-cards/m-p/1689460)

## <a name="next-step"></a><span data-ttu-id="e6304-174">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="e6304-174">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e6304-175">Mit Universal-Aktionen für adaptive Karten arbeiten</span><span class="sxs-lookup"><span data-stu-id="e6304-175">Work with Universal Actions for Adaptive Cards</span></span>](Work-with-universal-actions-for-adaptive-cards.md)
