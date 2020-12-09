---
title: Entwerfen von adaptiven Karten für Ihre APP
description: Hier erfahren Sie, wie Sie Adaptive Karten für Teams entwerfen und das Microsoft Teams UI Kit erhalten.
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: bd48846284620415cc8cadabc59f2ab7b61d5189
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "49604522"
---
# <a name="designing-adaptive-cards-for-your-microsoft-teams-app"></a><span data-ttu-id="6d9ff-103">Entwerfen von adaptiven Karten für Ihre Microsoft Teams-App</span><span class="sxs-lookup"><span data-stu-id="6d9ff-103">Designing Adaptive Cards for your Microsoft Teams app</span></span>

<span data-ttu-id="6d9ff-104">Eine Adaptive Karte enthält einen Freihandform Körper mit Kartenelementen und optionalen Aktionen.</span><span class="sxs-lookup"><span data-stu-id="6d9ff-104">An Adaptive Card contains a freeform body of card elements and optional set of actions.</span></span> <span data-ttu-id="6d9ff-105">Adaptive Karten sind Aktions fähige Snippets von Inhalten, die Sie einer Unterhaltung über eine bot-oder Messaging-Erweiterung hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="6d9ff-105">Adaptive Cards are actionable snippets of content that you can add to a conversation through a bot or messaging extension.</span></span> <span data-ttu-id="6d9ff-106">Mithilfe von Text, Grafiken und Schaltflächen bieten diese Karten eine umfassende Kommunikation mit Ihrem Publikum.</span><span class="sxs-lookup"><span data-stu-id="6d9ff-106">Using text, graphics, and buttons, these cards provide rich communication to your audience.</span></span>

<span data-ttu-id="6d9ff-107">Das Adaptive Karten Framework wird in vielen Microsoft-Produkten, einschließlich Teams, verwendet.</span><span class="sxs-lookup"><span data-stu-id="6d9ff-107">The Adaptive Card framework is used across many Microsoft products, including Teams.</span></span> <span data-ttu-id="6d9ff-108">Sie können Karten innerhalb von Nachrichten an Benutzer über Bots oder Messaging-Erweiterungen senden.</span><span class="sxs-lookup"><span data-stu-id="6d9ff-108">You can send cards inside messages to users via bots or messaging extensions.</span></span> <span data-ttu-id="6d9ff-109">Benutzer können Aktionen auf Karten durchführen, wenn diese vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="6d9ff-109">Users can take actions on cards when present.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/adaptive-card-overview.png" alt-text="Beispiel zeigt eine Adaptive Karte." border="false":::

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="6d9ff-111">Microsoft Teams-UI-Kit</span><span class="sxs-lookup"><span data-stu-id="6d9ff-111">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="6d9ff-112">Ausführlichere Entwurfsrichtlinien für Adaptive Karten in Microsoft Teams, einschließlich der Elemente, die Sie nach Bedarf abrufen und ändern können, finden Sie im Microsoft Teams UI Kit.</span><span class="sxs-lookup"><span data-stu-id="6d9ff-112">You can find more comprehensive design guidelines for Adaptive Cards in Teams, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span> <span data-ttu-id="6d9ff-113">Das UI-Kit umfasst auch wichtige Themen wie Design, Barrierefreiheit und reaktionsschnelle Größenanpassung.</span><span class="sxs-lookup"><span data-stu-id="6d9ff-113">The UI kit also covers essential topics such as theming, accessibility, and responsive sizing.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6d9ff-114">Abrufen des Microsoft Teams UI Kit (Figma)</span><span class="sxs-lookup"><span data-stu-id="6d9ff-114">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="adaptive-cards-designer"></a><span data-ttu-id="6d9ff-115">Adaptive Cards-Designer</span><span class="sxs-lookup"><span data-stu-id="6d9ff-115">Adaptive Cards designer</span></span>

<span data-ttu-id="6d9ff-116">Sie können auch mit dem Entwerfen Ihrer adaptiven Karten direkt im Browser beginnen.</span><span class="sxs-lookup"><span data-stu-id="6d9ff-116">You also can start designing your Adaptive Cards directly in the browser.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6d9ff-117">Testen des Adaptive Cards-Designers</span><span class="sxs-lookup"><span data-stu-id="6d9ff-117">Try the Adaptive Cards designer</span></span>](https://adaptivecards.io/designer/)

## <a name="types-of-adaptive-cards"></a><span data-ttu-id="6d9ff-118">Arten von adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="6d9ff-118">Types of Adaptive Cards</span></span>

### <a name="hero"></a><span data-ttu-id="6d9ff-119">Hero</span><span class="sxs-lookup"><span data-stu-id="6d9ff-119">Hero</span></span>

<span data-ttu-id="6d9ff-120">Unsere größte Karte.</span><span class="sxs-lookup"><span data-stu-id="6d9ff-120">Our largest card.</span></span> <span data-ttu-id="6d9ff-121">Verwenden Sie für die Freigabe von Artikeln oder Szenarien, in denen ein Bild die meiste Geschichte erzählt.</span><span class="sxs-lookup"><span data-stu-id="6d9ff-121">Use for sharing articles or scenarios where an image tells most of the story.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/hero-card.png" alt-text="Beispiel zeigt eine Adaptive Karte." border="false":::

### <a name="thumbnail"></a><span data-ttu-id="6d9ff-123">Minaturansicht</span><span class="sxs-lookup"><span data-stu-id="6d9ff-123">Thumbnail</span></span>

<span data-ttu-id="6d9ff-124">Verwenden Sie zum Senden einer einfachen Aktion-Nachricht.</span><span class="sxs-lookup"><span data-stu-id="6d9ff-124">Use for sending a simple actionable message.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/thumbnail-card.png" alt-text="Beispiel zeigt eine Adaptive Karte." border="false":::

### <a name="list"></a><span data-ttu-id="6d9ff-126">List</span><span class="sxs-lookup"><span data-stu-id="6d9ff-126">List</span></span>

<span data-ttu-id="6d9ff-127">Verwenden Sie in Szenarien, in denen der Benutzer ein Element aus einer Liste auswählen soll, aber für die Elemente keine große Erklärung erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="6d9ff-127">Use in scenarios where you want the user to pick an item from a list, but the items don’t need a lot of explanation.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/list-card.png" alt-text="Beispiel zeigt eine Adaptive Karte." border="false":::

### <a name="digest"></a><span data-ttu-id="6d9ff-129">Digest</span><span class="sxs-lookup"><span data-stu-id="6d9ff-129">Digest</span></span>

<span data-ttu-id="6d9ff-130">Verwenden Sie für Nachrichtenübersichten und Round-up-Beiträge.</span><span class="sxs-lookup"><span data-stu-id="6d9ff-130">Use for news digests and round-up posts.</span></span> <span data-ttu-id="6d9ff-131">Hinweis: Wir empfehlen die thumbnailkarte für ein einzelnes Update oder ein neues Element.</span><span class="sxs-lookup"><span data-stu-id="6d9ff-131">Note: We recommend the thumbnail card for a single update or news item.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/digest-card.png" alt-text="Beispiel zeigt eine Adaptive Karte." border="false":::

### <a name="media"></a><span data-ttu-id="6d9ff-133">Medien</span><span class="sxs-lookup"><span data-stu-id="6d9ff-133">Media</span></span>

<span data-ttu-id="6d9ff-134">Verwenden Sie diese Funktion, wenn Sie Text und Medien wie Audio oder Video kombinieren möchten.</span><span class="sxs-lookup"><span data-stu-id="6d9ff-134">Use when you want to combine text and media, like audio or video.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/media-card.png" alt-text="Beispiel zeigt eine Adaptive Karte." border="false":::

### <a name="people"></a><span data-ttu-id="6d9ff-136">Personen</span><span class="sxs-lookup"><span data-stu-id="6d9ff-136">People</span></span>

<span data-ttu-id="6d9ff-137">Am besten geeignet, wenn Sie effizient vermitteln möchten, wer eine Aufgabe eingeht.</span><span class="sxs-lookup"><span data-stu-id="6d9ff-137">Best used when you to efficiently convey who's involved with a task.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/people-card.png" alt-text="Beispiel zeigt eine Adaptive Karte." border="false":::

### <a name="request-ticket"></a><span data-ttu-id="6d9ff-139">Ticket anfordern</span><span class="sxs-lookup"><span data-stu-id="6d9ff-139">Request ticket</span></span>

<span data-ttu-id="6d9ff-140">Wird verwendet, um schnelle Eingaben eines Benutzers zu erhalten, um automatisch eine Aufgabe oder ein Ticket zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="6d9ff-140">Use to get quick inputs from a user to automatically create a task or ticket.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/request-ticket-card.png" alt-text="Beispiel zeigt eine Adaptive Karte." border="false":::

### <a name="imageset"></a><span data-ttu-id="6d9ff-142">ImageSet</span><span class="sxs-lookup"><span data-stu-id="6d9ff-142">ImageSet</span></span>

<span data-ttu-id="6d9ff-143">Verwenden Sie, um mehrere Bildminiaturansichten zu senden.</span><span class="sxs-lookup"><span data-stu-id="6d9ff-143">Use to send multiple image thumbnails.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/image-set-card.png" alt-text="Beispiel zeigt eine Adaptive Karte." border="false":::

### <a name="actionset"></a><span data-ttu-id="6d9ff-145">Für actionset</span><span class="sxs-lookup"><span data-stu-id="6d9ff-145">ActionSet</span></span>

<span data-ttu-id="6d9ff-146">Verwenden Sie diese Option, wenn Sie möchten, dass der Benutzer eine Schaltfläche wählt und dann zusätzlich Benutzereingaben von derselben Karte sammelt.</span><span class="sxs-lookup"><span data-stu-id="6d9ff-146">Use when you want to the user to select a button, then gather addition user input from the same card.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/action-set-card.png" alt-text="Beispiel zeigt eine Adaptive Karte." border="false":::

### <a name="choiceset"></a><span data-ttu-id="6d9ff-148">Choiceset</span><span class="sxs-lookup"><span data-stu-id="6d9ff-148">ChoiceSet</span></span>

<span data-ttu-id="6d9ff-149">Verwenden Sie, um mehrere Eingaben des Benutzers zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="6d9ff-149">Use to gather multiple inputs from the user.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/choice-set-card.png" alt-text="Beispiel zeigt eine Adaptive Karte." border="false":::

## <a name="anatomy"></a><span data-ttu-id="6d9ff-151">Anatomie</span><span class="sxs-lookup"><span data-stu-id="6d9ff-151">Anatomy</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/anatomy.png" alt-text="Illustration mit der UI-Anatomie einer adaptiven Karte." border="false":::

<span data-ttu-id="6d9ff-153">Adaptive Karten haben eine große Flexibilität.</span><span class="sxs-lookup"><span data-stu-id="6d9ff-153">Adaptive Cards have a lot of flexibility.</span></span> <span data-ttu-id="6d9ff-154">Es wird jedoch dringend empfohlen, die folgenden Komponenten auf jeder Karte einzubinden:</span><span class="sxs-lookup"><span data-stu-id="6d9ff-154">But at a minimum, we strongly suggest including the following components in every card:</span></span>

|<span data-ttu-id="6d9ff-155">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="6d9ff-155">Counter</span></span>|<span data-ttu-id="6d9ff-156">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6d9ff-156">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="6d9ff-157">A</span><span class="sxs-lookup"><span data-stu-id="6d9ff-157">A</span></span>|<span data-ttu-id="6d9ff-158">**Kopfzeile**: transparente und prägnante Kopfzeilen, aber dennoch aussagekräftig.</span><span class="sxs-lookup"><span data-stu-id="6d9ff-158">**Header**: Make headers clear and concise, yet descriptive.</span></span>|
|<span data-ttu-id="6d9ff-159">B</span><span class="sxs-lookup"><span data-stu-id="6d9ff-159">B</span></span>|<span data-ttu-id="6d9ff-160">**Body Copy**: Verwenden Sie, um Details zu übermitteln, die entweder zu lang oder nicht wichtig genug sind, um in die Kopfzeile einzubeziehen.</span><span class="sxs-lookup"><span data-stu-id="6d9ff-160">**Body copy**: Use to convey detail that is either too long or not important enough to include in the header.</span></span>|
|<span data-ttu-id="6d9ff-161">C</span><span class="sxs-lookup"><span data-stu-id="6d9ff-161">C</span></span>|<span data-ttu-id="6d9ff-162">**Primäre Aktionen**: Fügen Sie als bewährte Methode 1-3 primäre Aktionen hinzu.</span><span class="sxs-lookup"><span data-stu-id="6d9ff-162">**Primary actions**: As a best practice, include 1-3 primary actions.</span></span> <span data-ttu-id="6d9ff-163">Es sind maximal sechs zulässig.</span><span class="sxs-lookup"><span data-stu-id="6d9ff-163">A maximum of six are allowed.</span></span>|

## <a name="best-practices"></a><span data-ttu-id="6d9ff-164">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="6d9ff-164">Best practices</span></span>

### <a name="primary-and-secondary-actions"></a><span data-ttu-id="6d9ff-165">Primäre und sekundäre Aktionen</span><span class="sxs-lookup"><span data-stu-id="6d9ff-165">Primary and secondary actions</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/adaptive-cards/actions-do.png" alt-text="Beispiel mit einer bewährten Methode für Adaptive Karten." border="false":::

#### <a name="do-use-up-to-six-primary-actions"></a><span data-ttu-id="6d9ff-167">Do: Verwenden Sie bis zu sechs primäre Aktionen.</span><span class="sxs-lookup"><span data-stu-id="6d9ff-167">Do: Use up to six primary actions</span></span>

<span data-ttu-id="6d9ff-168">Während Adaptive Karten sechs primäre Aktionen unterstützen können, benötigen die meisten Karten dies nicht.</span><span class="sxs-lookup"><span data-stu-id="6d9ff-168">While Adaptive Cards can support six primary actions, most cards don’t need that.</span></span> <span data-ttu-id="6d9ff-169">Aktionen sollten klar, prägnant und geradlinig sein.</span><span class="sxs-lookup"><span data-stu-id="6d9ff-169">Actions should be clear, concise, and straight forward.</span></span> <span data-ttu-id="6d9ff-170">Weniger ist mehr.</span><span class="sxs-lookup"><span data-stu-id="6d9ff-170">Less is more.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/adaptive-cards/actions-dont.png" alt-text="Beispiel mit einer bewährten Methode für Adaptive Karten." border="false":::

#### <a name="dont-use-more-than-six-primary-actions"></a><span data-ttu-id="6d9ff-172">Nicht: mehr als sechs primäre Aktionen verwenden</span><span class="sxs-lookup"><span data-stu-id="6d9ff-172">Don't: Use more than six primary actions</span></span>

<span data-ttu-id="6d9ff-173">Adaptive Karten sollten schnelle, umsetzbare Inhalte darstellen.</span><span class="sxs-lookup"><span data-stu-id="6d9ff-173">Adaptive Cards should present quick, actionable content.</span></span> <span data-ttu-id="6d9ff-174">Zu viele Aktionen können einen Benutzer überwältigen.</span><span class="sxs-lookup"><span data-stu-id="6d9ff-174">Too many actions can overwhelm a user.</span></span>

   :::column-end:::
:::row-end:::

### <a name="frequency"></a><span data-ttu-id="6d9ff-175">Häufigkeit</span><span class="sxs-lookup"><span data-stu-id="6d9ff-175">Frequency</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/frequency-do.png" alt-text="Beispiel mit einer bewährten Methode für Adaptive Karten." border="false":::

#### <a name="do-be-concise"></a><span data-ttu-id="6d9ff-177">Do: prägnant sein</span><span class="sxs-lookup"><span data-stu-id="6d9ff-177">Do: Be concise</span></span>

<span data-ttu-id="6d9ff-178">Es ist ganz einfach, mehrere Karten in eine Unterhaltung zu senden, aber sobald die Karten aus dem Blickfeld geraten, werden Sie nicht mehr so nützlich.</span><span class="sxs-lookup"><span data-stu-id="6d9ff-178">It's easy to send multiple cards into a conversation, but once cards scroll out of view, they become less useful.</span></span> <span data-ttu-id="6d9ff-179">Versuchen Sie, sich auf das Wesentliche zu beschränken.</span><span class="sxs-lookup"><span data-stu-id="6d9ff-179">Try to limit yourself to the essentials.</span></span> <span data-ttu-id="6d9ff-180">Dies gilt insbesondere für einen Kanal, in dem Benutzer eine geringere Toleranz für das als "Rauschen" wahrgenommene haben.</span><span class="sxs-lookup"><span data-stu-id="6d9ff-180">This is especially true in a channel where users have less tolerance for what they perceive as "noise".</span></span>
