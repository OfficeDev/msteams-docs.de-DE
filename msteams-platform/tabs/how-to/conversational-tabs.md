---
title: Registerkarten für Unterhaltungen erstellen
author: surbhigupta
description: Erstellen eines Unterhaltungsunterentitätschats für Ihre Kanalregisterkarten
keywords: Kanal "Teams-Registerkarten" konfigurierbar
ms.topic: conceptual
ms.author: lomeybur
ms.openlocfilehash: fbc5e90842c892cfb7e14f845563d7d2ffb397bb
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140264"
---
# <a name="create-conversational-tabs"></a><span data-ttu-id="b4134-104">Registerkarten für Unterhaltungen erstellen</span><span class="sxs-lookup"><span data-stu-id="b4134-104">Create conversational tabs</span></span>

<span data-ttu-id="b4134-105">Unterhaltungsunterentitäten bieten eine Möglichkeit, Benutzern zu ermöglichen, Unterhaltungen über Unterentitäten auf Ihrer Registerkarte zu führen, z. B. bestimmte Aufgaben, Patienten und Verkaufschancen, anstatt die gesamte Registerkarte zu besprechen, die auch als Entität bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="b4134-105">Conversational sub-entities provides a way to allow users to have conversations about sub-entities in your tab, such as specific task, patient, and sales opportunity, instead of discussing the entire tab, also known as entity.</span></span> <span data-ttu-id="b4134-106">Ein herkömmlicher Kanal oder eine konfigurierbare Registerkarte ermöglicht dem Benutzer eine Unterhaltung über eine Registerkarte, aber der Benutzer erfordert eine gezielte unterhaltung.</span><span class="sxs-lookup"><span data-stu-id="b4134-106">A traditional channel or configurable tab allows the user to have a conversation about a tab, but the user requires a more focused conversation.</span></span> <span data-ttu-id="b4134-107">Die Anforderung einer fokussierteren Unterhaltung kann entweder auftreten, wenn zu viele Inhalte vorhanden sind, um eine zentrale Diskussion zu führen, oder weil sich der Inhalt im Laufe der Zeit geändert hat, wodurch die Unterhaltung für die angezeigten Inhalte irrelevant wird.</span><span class="sxs-lookup"><span data-stu-id="b4134-107">The requirement for a more focused conversation can arise either, if there is too much content to have a centralized discussion or because the content changed over time, making the conversation irrelevant to the content being shown.</span></span> <span data-ttu-id="b4134-108">Unterhaltungsunterentitäten bieten eine viel fokussiertere Unterhaltungserfahrung für dynamische Registerkarten.</span><span class="sxs-lookup"><span data-stu-id="b4134-108">Conversational sub-entities provides a much more focused conversation experience for dynamic tabs.</span></span>

<span data-ttu-id="b4134-109">Unterhaltungsunterentitäten werden nur in Kanälen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b4134-109">Conversational sub-entities are only supported in channels.</span></span> <span data-ttu-id="b4134-110">Sie können von einer persönlichen oder statischen Registerkarte verwendet werden, um Unterhaltungen in Registerkarten zu erstellen oder fortzusetzen, die bereits an einen Kanal angeheftet sind.</span><span class="sxs-lookup"><span data-stu-id="b4134-110">They can be used from a personal or static tab to create or continue conversations in tabs that are already pinned to a channel.</span></span> <span data-ttu-id="b4134-111">Die statische Registerkarte ist nützlich, wenn Sie einen Ort für einen Benutzer bereitstellen möchten, an dem Unterhaltungen über mehrere Kanäle hinweg angezeigt und darauf zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="b4134-111">The static tab is useful if you want to provide one location for a user to view and access conversations happening across multiple channels.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b4134-112">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="b4134-112">Prerequisites</span></span>

<span data-ttu-id="b4134-113">Um Unterhaltungsunterentitäten zu unterstützen, muss Ihre Registerkartenwebanwendung in der Lage sein, eine Zuordnung zwischen Unterentitäten ↔ Unterhaltungen in einer Back-End-Datenbank zu speichern.</span><span class="sxs-lookup"><span data-stu-id="b4134-113">In order to support conversational sub-entities, your tab web application must have the ability to store a mapping between sub-entities ↔ conversations in a backend database.</span></span> <span data-ttu-id="b4134-114">Dies `conversationId` wird bereitgestellt, Sie müssen dies jedoch speichern `conversationId` und an Teams zurückgeben, damit Benutzer die Unterhaltung fortsetzen können.</span><span class="sxs-lookup"><span data-stu-id="b4134-114">The `conversationId` is provided, but you must store that `conversationId` and return it to Teams in order for users to continue the conversation.</span></span>

## <a name="start-a-new-conversation"></a><span data-ttu-id="b4134-115">Starten einer neuen Unterhaltung</span><span class="sxs-lookup"><span data-stu-id="b4134-115">Start a new conversation</span></span>

<span data-ttu-id="b4134-116">Verwenden Sie die Funktion, um eine neue Unterhaltung zu `openConversation()` starten.</span><span class="sxs-lookup"><span data-stu-id="b4134-116">To start a new conversation, use the `openConversation()` function.</span></span> <span data-ttu-id="b4134-117">Das Starten und Fortsetzen einer Unterhaltung wird von dieser Methode verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="b4134-117">Starting and continuing a conversation are all handled by this method.</span></span> <span data-ttu-id="b4134-118">Die Eingaben für die Funktion ändern sich je nachdem, welche Aktion Sie ausführen möchten.</span><span class="sxs-lookup"><span data-stu-id="b4134-118">The inputs to the function change depending on which action you want to take.</span></span> <span data-ttu-id="b4134-119">Aus Sicht der Benutzer wird dadurch der Unterhaltungsbereich rechts vom Bildschirm geöffnet, um entweder eine Unterhaltung zu initiieren oder eine Unterhaltung fortzusetzen.</span><span class="sxs-lookup"><span data-stu-id="b4134-119">From the users perspective, this opens the conversation panel to the right of the screen, either to initiate a conversation or continue a conversation.</span></span>

``` javascript
microsoftTeams.conversations.openConversation(openConversationRequest);
```

<span data-ttu-id="b4134-120">**openConversation** verwendet die folgenden Eingaben, um eine Unterhaltung in einem Kanal zu starten:</span><span class="sxs-lookup"><span data-stu-id="b4134-120">**openConversation** takes the following inputs to start a conversation in a channel:</span></span>

* <span data-ttu-id="b4134-121">**subEntityId:** Dies ist die ID Ihrer spezifischen Unterentität.</span><span class="sxs-lookup"><span data-stu-id="b4134-121">**subEntityId**: This is the ID of your specific sub-entity.</span></span> <span data-ttu-id="b4134-122">Beispiel: Task-123.</span><span class="sxs-lookup"><span data-stu-id="b4134-122">For example, task-123.</span></span>
* <span data-ttu-id="b4134-123">**entityId:** Dies ist die ID der Registerkarteninstanz, als sie erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="b4134-123">**entityId**: This is the ID of the tab instance when it was created.</span></span> <span data-ttu-id="b4134-124">Die ID ist wichtig, um auf dieselbe Registerkarteninstanz zurück zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="b4134-124">The ID is important to refer back to the same tab instance.</span></span>
* <span data-ttu-id="b4134-125">**channelId:** Dies ist der Kanal, in dem sich die Registerkarteninstanz befindet.</span><span class="sxs-lookup"><span data-stu-id="b4134-125">**channelId**: This is the channel in which the tab instance resides.</span></span>
   > [!NOTE]
   > <span data-ttu-id="b4134-126">Die **channelId** ist optional für Kanalregisterkarten.</span><span class="sxs-lookup"><span data-stu-id="b4134-126">The **channelId** is optional for channel tabs.</span></span> <span data-ttu-id="b4134-127">Es wird jedoch empfohlen, die Implementierung kanalübergreifend und auf statischen Registerkarten gleich zu halten.</span><span class="sxs-lookup"><span data-stu-id="b4134-127">However, it is recommended if you want to keep your implementation across channel and static tabs the same.</span></span>
* <span data-ttu-id="b4134-128">**title:** Dies ist der Titel, der dem Benutzer im Chatbereich angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b4134-128">**title**: This is the title that is shown to the user in the chat panel.</span></span>

<span data-ttu-id="b4134-129">Die meisten dieser Werte können auch aus der API abgerufen `getContext` werden.</span><span class="sxs-lookup"><span data-stu-id="b4134-129">Most of these values can also be retrieved from the `getContext` API.</span></span>

```javascript
microsoftTeams.conversations.openConversation({“subEntityId”:”task-1”, “entityId”: “tabInstanceId-1”, “channelId”: ”19:baa6e71f65b948d189bf5c892baa8e5a@thread.skype”, “title”: "Task Title”});
```

<span data-ttu-id="b4134-130">Die folgende Abbildung zeigt den Unterhaltungsbereich:</span><span class="sxs-lookup"><span data-stu-id="b4134-130">The following image shows the conversation panel:</span></span>

![Unterhaltungsunterentitäten – Unterhaltung starten](~/assets/images/tabs/conversational-subentities/start-conversation.png)

<span data-ttu-id="b4134-132">Wenn der Benutzer eine Unterhaltung startet, ist es wichtig, auf den Rückruf dieses Ereignisses zu lauschen, um die **conversationId** abzurufen und zu speichern:</span><span class="sxs-lookup"><span data-stu-id="b4134-132">If the user starts a conversation, it is important to listen for the callback of that event in order to retrieve and save the **conversationId**:</span></span>

```javascript
microsoftTeams.conversations.onStartConversation = (conversationResponse) => {
    // console.log(conversationReponse.conversationId)
};
```

<span data-ttu-id="b4134-133">Das `conversationResponse` Objekt enthält Informationen zu der unterhaltung, die gestartet wurde.</span><span class="sxs-lookup"><span data-stu-id="b4134-133">The `conversationResponse` object contains information related to the conversation that was started.</span></span> <span data-ttu-id="b4134-134">Es wird empfohlen, alle Eigenschaften dieses Antwortobjekts zur späteren Verwendung zu speichern.</span><span class="sxs-lookup"><span data-stu-id="b4134-134">It is recommended that you save all the properties of this response object for later use.</span></span>

## <a name="continue-a-conversation"></a><span data-ttu-id="b4134-135">Unterhaltung fortsetzen</span><span class="sxs-lookup"><span data-stu-id="b4134-135">Continue a conversation</span></span>

<span data-ttu-id="b4134-136">Nach dem Starten einer Unterhaltung müssen Sie bei nachfolgenden Aufrufen `openConversation()` auch die gleichen Eingaben wie beim Starten [einer neuen Unterhaltung](#start-a-new-conversation)angeben, aber auch die **conversationId** einschließen.</span><span class="sxs-lookup"><span data-stu-id="b4134-136">After a conversation starts, subsequent calls to `openConversation()` requires that you also provide the same inputs as in [start a new conversation](#start-a-new-conversation), but also include the **conversationId**.</span></span> <span data-ttu-id="b4134-137">Der Unterhaltungsbereich wird für den Benutzer geöffnet, in dem die entsprechende Unterhaltung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b4134-137">The conversation panel opens for the user with the appropriate conversation in view.</span></span> <span data-ttu-id="b4134-138">Benutzer können neue oder eingehende Nachrichten in Echtzeit sehen.</span><span class="sxs-lookup"><span data-stu-id="b4134-138">Users are able to see new or incoming messages in real-time.</span></span>

<span data-ttu-id="b4134-139">Die folgende Abbildung zeigt den Unterhaltungsbereich mit der entsprechenden Unterhaltung:</span><span class="sxs-lookup"><span data-stu-id="b4134-139">The following image shows the conversation panel with the appropriate conversation:</span></span>

![Unterhaltungsunterentitäten – Unterhaltung fortsetzen](~/assets/images/tabs/conversational-subentities/continue-conversation.png)

## <a name="enhance-a-conversation"></a><span data-ttu-id="b4134-141">Verbessern einer Unterhaltung</span><span class="sxs-lookup"><span data-stu-id="b4134-141">Enhance a conversation</span></span>

<span data-ttu-id="b4134-142">Es ist wichtig, dass Ihre Registerkarte [Deeplinks zu Ihrer Unterentität](~/concepts/build-and-test/deep-links.md)enthält.</span><span class="sxs-lookup"><span data-stu-id="b4134-142">It is important that your tab includes [deeplinks to your sub-entity](~/concepts/build-and-test/deep-links.md).</span></span> <span data-ttu-id="b4134-143">Der Benutzer wählt z. B. den Tabstopp-Deeplink aus der Kanalunterhaltung aus.</span><span class="sxs-lookup"><span data-stu-id="b4134-143">For example, user selecting the tab chiclet deeplink from the channel conversation.</span></span> <span data-ttu-id="b4134-144">Das erwartete Verhalten besteht darin, den Deeplink zu erhalten, diese Unterentität zu öffnen und dann den Unterhaltungsbereich für diese Unterentität zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="b4134-144">The expected behavior is to receive the deeplink, open that sub-entity, and then open the conversation panel for that sub-entity.</span></span>

<span data-ttu-id="b4134-145">Um Unterhaltungsunterentitäten von Ihrer persönlichen oder statischen Registerkarte aus zu unterstützen, müssen Sie nichts in Ihrer Implementierung ändern.</span><span class="sxs-lookup"><span data-stu-id="b4134-145">To support conversational sub-entities from your personal or static tab, you do not have to change anything in your implementation.</span></span> <span data-ttu-id="b4134-146">Wir unterstützen nur das Starten oder Fortsetzen von Unterhaltungen über Kanalregisterkarten, die bereits angeheftet sind.</span><span class="sxs-lookup"><span data-stu-id="b4134-146">We only support starting or continuing conversations from channel tabs that are already pinned.</span></span> <span data-ttu-id="b4134-147">Die Unterstützung statischer Registerkarten ermöglicht es Ihnen, einen einzelnen Speicherort für Ihre Benutzer bereitzustellen, um mit allen Ihren Unterentitäten zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="b4134-147">Supporting static tabs allows you to provide a single location for your users to interact with all your sub-entities.</span></span> <span data-ttu-id="b4134-148">Es ist wichtig, dass Sie die Registerkarte speichern `subEntityId` und wenn die Registerkarte ursprünglich in einem Kanal erstellt `entityId` `channelId` wurde, um die richtigen Eigenschaften zu haben, wenn Sie die Unterhaltungsansicht in einer statischen Registerkarte öffnen.</span><span class="sxs-lookup"><span data-stu-id="b4134-148">It is important that you save the `subEntityId`, `entityId`, and `channelId` when your tab is originally created in a channel to have the right properties when opening the conversation view in a static tab.</span></span>

## <a name="close-a-conversation"></a><span data-ttu-id="b4134-149">Beenden einer Unterhaltung</span><span class="sxs-lookup"><span data-stu-id="b4134-149">Close a conversation</span></span>

<span data-ttu-id="b4134-150">Sie können die Unterhaltungsansicht manuell schließen, indem Sie die `closeConversation()` Funktion aufrufen.</span><span class="sxs-lookup"><span data-stu-id="b4134-150">You can manually close the conversation view by calling the `closeConversation()` function.</span></span>

```javascript
microsoftTeams.conversations.closeConversation();
```

<span data-ttu-id="b4134-151">Sie können auch auf ein Ereignis lauschen, wenn die Unterhaltungsansicht von einem Benutzer geschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="b4134-151">You can also listen for an event when the conversation view is closed by a user.</span></span>

```javascript
microsoftTeams.conversations.onCloseConversation = (conversationResponse) => {
    // console.log(conversationResponse)
};
```

## <a name="see-also"></a><span data-ttu-id="b4134-152">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b4134-152">See also</span></span>

* [<span data-ttu-id="b4134-153">registerkarten Teams</span><span class="sxs-lookup"><span data-stu-id="b4134-153">Teams tabs</span></span>](~/tabs/what-are-tabs.md)
* [<span data-ttu-id="b4134-154">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="b4134-154">Prerequisites</span></span>](~/tabs/how-to/tab-requirements.md)
* [<span data-ttu-id="b4134-155">Erstellen einer persönlichen Registerkarte</span><span class="sxs-lookup"><span data-stu-id="b4134-155">Create a personal tab</span></span>](~/tabs/how-to/create-personal-tab.md)
* [<span data-ttu-id="b4134-156">Erstellen einer Kanal- oder Gruppenregisterkarte</span><span class="sxs-lookup"><span data-stu-id="b4134-156">Create a channel or group tab</span></span>](~/tabs/how-to/create-channel-group-tab.md)
* [<span data-ttu-id="b4134-157">Erstellen einer Inhaltsseite</span><span class="sxs-lookup"><span data-stu-id="b4134-157">Create a content page</span></span>](~/tabs/how-to/create-tab-pages/content-page.md)
* [<span data-ttu-id="b4134-158">Erstellen einer Konfigurationsseite</span><span class="sxs-lookup"><span data-stu-id="b4134-158">Create a configuration page</span></span>](~/tabs/how-to/create-tab-pages/configuration-page.md)
* [<span data-ttu-id="b4134-159">Erstellen einer Seite zum Entfernen ihrer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="b4134-159">Create a removal page for your tab</span></span>](~/tabs/how-to/create-tab-pages/removal-page.md)
* [<span data-ttu-id="b4134-160">Registerkarten auf mobilen Geräten</span><span class="sxs-lookup"><span data-stu-id="b4134-160">Tabs on mobile</span></span>](~/tabs/design/tabs-mobile.md)
* [<span data-ttu-id="b4134-161">Kontext für Ihre Registerkarte erhalten</span><span class="sxs-lookup"><span data-stu-id="b4134-161">Get context for your tab</span></span>](~/tabs/how-to/access-teams-context.md)
* [<span data-ttu-id="b4134-162">Erstellen von Registerkarten mit adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="b4134-162">Build tabs with Adaptive Cards</span></span>](~/tabs/how-to/build-adaptive-card-tabs.md)
* [<span data-ttu-id="b4134-163">Aufgeklappte Registerkartenverknüpfung und Phasenansicht</span><span class="sxs-lookup"><span data-stu-id="b4134-163">Tabs link unfurling and Stage View</span></span>](~/tabs/tabs-link-unfurling.md)

## <a name="next-step"></a><span data-ttu-id="b4134-164">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="b4134-164">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b4134-165">Änderungen am Registerkartenrand</span><span class="sxs-lookup"><span data-stu-id="b4134-165">Tab margin changes</span></span>](~/resources/removing-tab-margins.md)