---
title: Erstellen von Unterhaltungsregisterkarten
author: laujan
description: Erstellen von Unterhaltungsunterentitätschats für Ihre Kanalregisterkarten
keywords: Teams-Registerkartenkanal konfigurierbar
ms.topic: conceptual
ms.author: lomeybur
ms.openlocfilehash: 4171265a3ef4ad917661e258dd7305f82411c5ef
ms.sourcegitcommit: 118f7261d313feeac5b398fef56a44bd90104b2f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2021
ms.locfileid: "52709646"
---
# <a name="create-conversational-tabs"></a><span data-ttu-id="fbb17-104">Erstellen von Unterhaltungsregisterkarten</span><span class="sxs-lookup"><span data-stu-id="fbb17-104">Create conversational tabs</span></span>

<span data-ttu-id="fbb17-105">Unterhaltungsunterentitäten bieten eine Möglichkeit, Benutzern zu ermöglichen, Unterhaltungen über Unterentitäten auf Ihrer Registerkarte zu führen, z. B. bestimmte Aufgaben, Patienten und Verkaufschancen, anstatt die gesamte Registerkarte zu besprechen, die auch als Entität bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="fbb17-105">Conversational sub-entities provides a way to allow users to have conversations about sub-entities in your tab, such as specific task, patient, and sales opportunity, instead of discussing the entire tab, also known as entity.</span></span> <span data-ttu-id="fbb17-106">Ein herkömmlicher Kanal oder eine konfigurierbare Registerkarte ermöglicht es dem Benutzer, eine Unterhaltung über eine Registerkarte zu führen, aber der Benutzer möchte möglicherweise eine fokussierte Unterhaltung.</span><span class="sxs-lookup"><span data-stu-id="fbb17-106">A traditional channel or configurable tab allows the user to have a conversation about a tab, but the user may want a more focused conversation.</span></span> <span data-ttu-id="fbb17-107">Die Anforderung einer fokussierteren Unterhaltung kann entweder auftreten, wenn zu viel Inhalt für eine zentrale Diskussion vor sich geht oder der Inhalt im Laufe der Zeit geändert wird, was die Unterhaltung für den angezeigten Inhalt irrelevant macht.</span><span class="sxs-lookup"><span data-stu-id="fbb17-107">The requirement for a more focused conversation can arise either, if there is too much content to have a centralized discussion or the content changed over time, making the conversation irrelevant to the content being shown.</span></span> <span data-ttu-id="fbb17-108">Unterhaltungsunterentitäten bieten eine viel fokussiertere Unterhaltungserfahrung für dynamische Registerkarten.</span><span class="sxs-lookup"><span data-stu-id="fbb17-108">Conversational sub-entities provides a much more focused conversation experience for dynamic tabs.</span></span>

<span data-ttu-id="fbb17-109">Unterhaltungsunterentitäten werden nur in Kanälen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="fbb17-109">Conversational sub-entities are only supported in channels.</span></span> <span data-ttu-id="fbb17-110">Sie können jedoch auf einer persönlichen oder statischen Registerkarte zum  Erstellen oder Fortsetzen von Unterhaltungen in Registerkarten verwendet werden, die bereits an einen Kanal angeheftet sind.</span><span class="sxs-lookup"><span data-stu-id="fbb17-110">However, they can be used from a personal or static tab to create or continue conversations in tabs that are *already* pinned to a channel.</span></span> <span data-ttu-id="fbb17-111">Die statische Registerkarte ist hilfreich, wenn Sie einem Benutzer einen Ort zum Anzeigen und Zugreifen auf Unterhaltungen über mehrere Kanäle bereitstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="fbb17-111">The static tab is useful if you wish to provide one location for a user to view and access conversations happening across multiple channels.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fbb17-112">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="fbb17-112">Prerequisites</span></span>

<span data-ttu-id="fbb17-113">Um Unterhaltungsunterentitäten zu unterstützen, muss Ihre Registerkartenwebanwendung die Möglichkeit haben, eine Zuordnung zwischen Unterentitäten ↔ Unterhaltungen in einer Back-End-Datenbank zu speichern.</span><span class="sxs-lookup"><span data-stu-id="fbb17-113">In order to support conversational sub-entities, your tab web application must have the ability to store a mapping between sub-entities ↔ conversations in a backend database.</span></span> <span data-ttu-id="fbb17-114">Wir stellen Ihnen die zur Verfügung, aber es liegt in Ihrer Verantwortung, dies zu speichern und an Teams zurück, damit Benutzer `conversationId` `conversationId` die Unterhaltung fortsetzen können.</span><span class="sxs-lookup"><span data-stu-id="fbb17-114">We will provide you with the `conversationId`, but it will be your responsibility to store that `conversationId` and return it to Teams in order for users to continue the conversation.</span></span>

## <a name="start-a-new-conversation"></a><span data-ttu-id="fbb17-115">Starten einer neuen Unterhaltung</span><span class="sxs-lookup"><span data-stu-id="fbb17-115">Start a new conversation</span></span>

<span data-ttu-id="fbb17-116">Verwenden Sie die Funktion, um eine neue Unterhaltung zu `openConversation()` starten.</span><span class="sxs-lookup"><span data-stu-id="fbb17-116">To start a new conversation, you use the `openConversation()` function.</span></span> <span data-ttu-id="fbb17-117">Das Starten und Fortsetzen einer Unterhaltung wird von dieser Methode behandelt, die Eingaben für die Funktion ändern sich jedoch je nach der Aktion, die Sie ergreifen möchten.</span><span class="sxs-lookup"><span data-stu-id="fbb17-117">Starting and continuing a conversation are all handled by this method, however, the inputs to the function change depending on which action you want to take.</span></span> <span data-ttu-id="fbb17-118">Aus Benutzersicht wird dadurch der Unterhaltungsbereich rechts neben dem Bildschirm geöffnet, um eine Unterhaltung zu initiieren oder eine Unterhaltung weiter zu führen.</span><span class="sxs-lookup"><span data-stu-id="fbb17-118">From the users perspective, this opens the conversation panel to the right of the screen, either to initiate a conversation or continue a conversation.</span></span>

``` javascript
microsoftTeams.conversations.openConversation(openConversationRequest);
```

<span data-ttu-id="fbb17-119">**openConversation** verwendet die folgenden Eingaben, um eine Unterhaltung in einem Kanal zu starten:</span><span class="sxs-lookup"><span data-stu-id="fbb17-119">**openConversation** takes the following inputs to start a conversation in a channel:</span></span>

* <span data-ttu-id="fbb17-120">**subEntityId**: Dies ist die ID Ihrer bestimmten Unterentität.</span><span class="sxs-lookup"><span data-stu-id="fbb17-120">**subEntityId**: This is the ID of your specific sub-entity.</span></span> <span data-ttu-id="fbb17-121">Beispiel: task-123.</span><span class="sxs-lookup"><span data-stu-id="fbb17-121">For example, task-123.</span></span>
* <span data-ttu-id="fbb17-122">**entityId**: Dies ist die ID der Registerkarteninstanz, als sie erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="fbb17-122">**entityId**: This is the ID of the tab instance when it was created.</span></span> <span data-ttu-id="fbb17-123">Die ID ist wichtig, um auf dieselbe Registerkarteninstanz zurück verweisen.</span><span class="sxs-lookup"><span data-stu-id="fbb17-123">The ID is important to refer back to the same tab instance.</span></span>
* <span data-ttu-id="fbb17-124">**channelId**: Dies ist der Kanal, in dem sich die Registerkarteninstanz befindet.</span><span class="sxs-lookup"><span data-stu-id="fbb17-124">**channelId**: This is the channel in which the tab instance resides.</span></span>
   > [!NOTE]
   > <span data-ttu-id="fbb17-125">Die **channelId** ist optional für Kanalregisterkarten.</span><span class="sxs-lookup"><span data-stu-id="fbb17-125">The **channelId** is optional for channel tabs.</span></span> <span data-ttu-id="fbb17-126">Es wird jedoch empfohlen, die Implementierung kanal- und statisch gleich zu halten.</span><span class="sxs-lookup"><span data-stu-id="fbb17-126">However, it is recommended if you wish to keep your implementation across channel and static tabs the same.</span></span>
* <span data-ttu-id="fbb17-127">**title**: Dies ist der Titel, der dem Benutzer im Chatbereich angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="fbb17-127">**title**: This is the title that is shown to the user in the chat panel.</span></span>

<span data-ttu-id="fbb17-128">Die meisten dieser Werte können auch aus der API abgerufen `getContext` werden.</span><span class="sxs-lookup"><span data-stu-id="fbb17-128">Most of these values can also be retrieved from the `getContext` API.</span></span>

```javascript
microsoftTeams.conversations.openConversation({“subEntityId”:”task-1”, “entityId”: “tabInstanceId-1”, “channelId”: ”19:baa6e71f65b948d189bf5c892baa8e5a@thread.skype”, “title”: "Task Title”});
```

<span data-ttu-id="fbb17-129">Dadurch wird der Unterhaltungsbereich geöffnet.</span><span class="sxs-lookup"><span data-stu-id="fbb17-129">This will open the conversation panel.</span></span>

![Conversationl Sub Entities – Unterhaltung starten](~/assets/images/tabs/conversational-subentities/start-conversation.png)

<span data-ttu-id="fbb17-131">Wenn der Benutzer eine Unterhaltung startet, ist es wichtig, auf den Rückruf dieses Ereignisses zu lauschen, um die conversationId abzurufen und **zu speichern:**</span><span class="sxs-lookup"><span data-stu-id="fbb17-131">If the user starts a conversation, it’s important to listen for the callback of that event in order to retrieve and save the **conversationId**:</span></span>

```javascript
microsoftTeams.conversations.onStartConversation = (conversationResponse) => {
    // console.log(conversationReponse.conversationId)
};
```

<span data-ttu-id="fbb17-132">Das `conversationReponse` Objekt enthält Informationen im Zusammenhang mit der Unterhaltung, die gerade gestartet wurde.</span><span class="sxs-lookup"><span data-stu-id="fbb17-132">The `conversationReponse` object contains information related to the conversation that was just started.</span></span> <span data-ttu-id="fbb17-133">Es wird empfohlen, alle Eigenschaften dieses Antwortobjekts zur späteren Wiederverwendung zu speichern.</span><span class="sxs-lookup"><span data-stu-id="fbb17-133">We recommend you save all the properties of this response object for reuse later.</span></span>

## <a name="continue-a-conversation"></a><span data-ttu-id="fbb17-134">Fortsetzen einer Unterhaltung</span><span class="sxs-lookup"><span data-stu-id="fbb17-134">Continue a conversation</span></span>

<span data-ttu-id="fbb17-135">Nachdem eine Unterhaltung gestartet wurde, müssen Sie für nachfolgende Aufrufe auch die gleichen Eingaben wie unter Starten einer neuen Kanalregisterkarten-Unterhaltung bereitstellen, aber auch `openConversation()` **die conversationId enthalten.** [](#Starting a new channel tab conversation)</span><span class="sxs-lookup"><span data-stu-id="fbb17-135">After a conversation starts, subsequent calls to `openConversation()` requires that you also provide the same inputs as in [Starting a new channel tab conversation](#Starting a new channel tab conversation), but also include the **conversationId**.</span></span> <span data-ttu-id="fbb17-136">Der Unterhaltungsbereich wird für den Benutzer geöffnet, in dem die entsprechende Unterhaltung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="fbb17-136">The conversation panel opens for the user with the appropriate conversation in view.</span></span> <span data-ttu-id="fbb17-137">Benutzer können neue oder eingehende Nachrichten in Echtzeit anzeigen.</span><span class="sxs-lookup"><span data-stu-id="fbb17-137">Users are able to see new or incoming messages in real-time.</span></span>

![Conversationl Sub Entities – Unterhaltung fortsetzen](~/assets/images/tabs/conversational-subentities/continue-conversation.png)

## <a name="enhance-a-conversation"></a><span data-ttu-id="fbb17-139">Verbessern einer Unterhaltung</span><span class="sxs-lookup"><span data-stu-id="fbb17-139">Enhance a conversation</span></span>

<span data-ttu-id="fbb17-140">Schließlich ist es wichtig, dass Ihre Registerkarte [Deeplinks zu Ihrer Unterentität verwendet.](~/concepts/build-and-test/deep-links.md)</span><span class="sxs-lookup"><span data-stu-id="fbb17-140">Finally, it’s important that your tab consumes [deeplinks to your sub-entity](~/concepts/build-and-test/deep-links.md).</span></span> <span data-ttu-id="fbb17-141">Beispielsweise klickt der Benutzer in der Kanal-Unterhaltung auf die Registerkartenschickslet-Deeplink.</span><span class="sxs-lookup"><span data-stu-id="fbb17-141">For example, user clicking the tab chiclet deeplink from the channel conversation.</span></span> <span data-ttu-id="fbb17-142">Das erwartete Verhalten ist, dass Sie den Deeplink erhalten, diese Unterentität öffnen und dann den Unterhaltungsbereich für diese bestimmte Unterentität öffnen.</span><span class="sxs-lookup"><span data-stu-id="fbb17-142">The expected behavior is for you to receive the deeplink, open that sub-entity, and then open the conversation panel for that specific sub-entity.</span></span>

<span data-ttu-id="fbb17-143">Um Unterhaltungsunterentitäten von Ihrer persönlichen oder statischen Registerkarte zu unterstützen, müssen Sie nichts an Ihrer Implementierung ändern.</span><span class="sxs-lookup"><span data-stu-id="fbb17-143">To support conversational sub-entities from your personal or static tab, you do not have to change anything about your implementation.</span></span> <span data-ttu-id="fbb17-144">Wir unterstützen nur das Starten oder Fortsetzen von Unterhaltungen auf Kanalregisterkarten, die bereits angeheftet sind.</span><span class="sxs-lookup"><span data-stu-id="fbb17-144">We only support starting or continuing conversations from channel tabs that are already pinned.</span></span> <span data-ttu-id="fbb17-145">Durch die Unterstützung statischer Registerkarten können Sie ihren Benutzern einen einzigen Speicherort für die Interaktion mit allen Unterentitäten bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="fbb17-145">Supporting static tabs allow you to provide a single location for your users to interact with all your sub-entities.</span></span> <span data-ttu-id="fbb17-146">Es ist jedoch wichtig, dass Sie die , speichern und wenn Ihre Registerkarte ursprünglich in einem Kanal erstellt wurde, damit Sie beim Öffnen der Unterhaltungsansicht auf einer statischen Registerkarte die richtigen Eigenschaften `subEntityId` `entityId` `channelId` haben.</span><span class="sxs-lookup"><span data-stu-id="fbb17-146">It is, however, important that you save the `subEntityId`, `entityId`, and `channelId` when your tab is originally created in a channel in order for you to have the right properties when opening the conversation view in a static tab.</span></span>

## <a name="close-a-conversation"></a><span data-ttu-id="fbb17-147">Schließen einer Unterhaltung</span><span class="sxs-lookup"><span data-stu-id="fbb17-147">Close a conversation</span></span>

<span data-ttu-id="fbb17-148">Sie können die Unterhaltungsansicht manuell schließen, indem Sie die Funktion `closeConversation()` aufrufen.</span><span class="sxs-lookup"><span data-stu-id="fbb17-148">You can manually close the conversation view by calling the `closeConversation()` function.</span></span>

```javascript
microsoftTeams.conversations.closeConversation();
```

<span data-ttu-id="fbb17-149">Sie können auch auf ein Ereignis lauschen, wenn die Unterhaltungsansicht von einem Benutzer geschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="fbb17-149">You can also listen for an event when the conversation view is closed by a user.</span></span>

```javascript
microsoftTeams.conversations.onCloseConversation = (conversationResponse) => {
    // console.log(conversationResponse)
};
```
