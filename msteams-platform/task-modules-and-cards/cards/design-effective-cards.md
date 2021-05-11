---
title: Entwerfen adaptiver Karten für Ihre App
description: Erfahren Sie, wie Sie adaptive Karten für Teams entwerfen und das Microsoft Teams UI Kit erhalten.
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 14ffff1264e716e04a1ffb5549b71a8b7ec5fc14
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101737"
---
# <a name="designing-adaptive-cards-for-your-microsoft-teams-app"></a><span data-ttu-id="5e91d-103">Entwerfen adaptiver Karten für Ihre Microsoft Teams App</span><span class="sxs-lookup"><span data-stu-id="5e91d-103">Designing Adaptive Cards for your Microsoft Teams app</span></span>

<span data-ttu-id="5e91d-104">Eine adaptive Karte enthält einen Freihandformtext mit Kartenelementen und optionalen Aktionen.</span><span class="sxs-lookup"><span data-stu-id="5e91d-104">An Adaptive Card contains a freeform body of card elements and optional set of actions.</span></span> <span data-ttu-id="5e91d-105">Adaptive Karten sind aktionenfähige Codeausschnitte von Inhalten, die Sie einer Unterhaltung über einen Bot oder eine Messagingerweiterung hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="5e91d-105">Adaptive Cards are actionable snippets of content that you can add to a conversation through a bot or messaging extension.</span></span> <span data-ttu-id="5e91d-106">Mithilfe von Text, Grafiken und Schaltflächen bieten diese Karten eine umfassende Kommunikation für Ihre Zielgruppe.</span><span class="sxs-lookup"><span data-stu-id="5e91d-106">Using text, graphics, and buttons, these cards provide rich communication to your audience.</span></span>

<span data-ttu-id="5e91d-107">Das Adaptive Card-Framework wird in vielen Microsoft-Produkten verwendet, einschließlich Teams.</span><span class="sxs-lookup"><span data-stu-id="5e91d-107">The Adaptive Card framework is used across many Microsoft products, including Teams.</span></span> <span data-ttu-id="5e91d-108">Sie können Karten innerhalb von Nachrichten über Bots oder Messagingerweiterungen an Benutzer senden.</span><span class="sxs-lookup"><span data-stu-id="5e91d-108">You can send cards inside messages to users via bots or messaging extensions.</span></span> <span data-ttu-id="5e91d-109">Benutzer können aktionen auf Karten ausführen, wenn vorhanden.</span><span class="sxs-lookup"><span data-stu-id="5e91d-109">Users can take actions on cards when present.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/adaptive-card-overview.png" alt-text="Übersichtsbeispiel einer adaptiven Karte." border="false":::

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="5e91d-111">Microsoft Teams-UI-Kit</span><span class="sxs-lookup"><span data-stu-id="5e91d-111">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="5e91d-112">Umfassendere Entwurfsrichtlinien für adaptive Karten finden Sie in Teams, einschließlich Elementen, die Sie bei Bedarf packen und ändern können, im Microsoft Teams UI Kit.</span><span class="sxs-lookup"><span data-stu-id="5e91d-112">You can find more comprehensive design guidelines for Adaptive Cards in Teams, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span> <span data-ttu-id="5e91d-113">Das Benutzeroberflächenkit behandelt auch wichtige Themen wie Design, Barrierefreiheit und reaktionsschnelle Größenanpassung.</span><span class="sxs-lookup"><span data-stu-id="5e91d-113">The UI kit also covers essential topics such as theming, accessibility, and responsive sizing.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5e91d-114">Holen Sie sich das Microsoft Teams-UI-Kit (Figma)</span><span class="sxs-lookup"><span data-stu-id="5e91d-114">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="adaptive-cards-designer"></a><span data-ttu-id="5e91d-115">Designer für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="5e91d-115">Adaptive Cards designer</span></span>

<span data-ttu-id="5e91d-116">Sie können ihre adaptiven Karten auch direkt im Browser entwerfen.</span><span class="sxs-lookup"><span data-stu-id="5e91d-116">You also can start designing your Adaptive Cards directly in the browser.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5e91d-117">Testen des Designers für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="5e91d-117">Try the Adaptive Cards designer</span></span>](https://adaptivecards.io/designer/)

## <a name="types-of-adaptive-cards"></a><span data-ttu-id="5e91d-118">Typen adaptiver Karten</span><span class="sxs-lookup"><span data-stu-id="5e91d-118">Types of Adaptive Cards</span></span>

### <a name="hero"></a><span data-ttu-id="5e91d-119">Hero</span><span class="sxs-lookup"><span data-stu-id="5e91d-119">Hero</span></span>

<span data-ttu-id="5e91d-120">Unsere größte Karte.</span><span class="sxs-lookup"><span data-stu-id="5e91d-120">Our largest card.</span></span> <span data-ttu-id="5e91d-121">Wird für die Freigabe von Artikeln oder Szenarien verwendet, in denen ein Bild den größten Teil der Geschichte beschreibt.</span><span class="sxs-lookup"><span data-stu-id="5e91d-121">Use for sharing articles or scenarios where an image tells most of the story.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/hero-card.png" alt-text="Beispiel zeigt eine Adaptive Card Hero Card." border="false":::

### <a name="thumbnail"></a><span data-ttu-id="5e91d-123">Miniaturansicht</span><span class="sxs-lookup"><span data-stu-id="5e91d-123">Thumbnail</span></span>

<span data-ttu-id="5e91d-124">Verwenden Sie diese Methode zum Senden einer einfachen Nachricht mit Aktionen.</span><span class="sxs-lookup"><span data-stu-id="5e91d-124">Use for sending a simple actionable message.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/thumbnail-card.png" alt-text="Beispiel zeigt eine Miniaturansichtskarte für adaptive Karten." border="false":::

### <a name="list"></a><span data-ttu-id="5e91d-126">Liste</span><span class="sxs-lookup"><span data-stu-id="5e91d-126">List</span></span>

<span data-ttu-id="5e91d-127">Wird in Szenarien verwendet, in denen der Benutzer ein Element aus einer Liste auswählen soll, die Elemente jedoch nicht viel Erläuterung benötigen.</span><span class="sxs-lookup"><span data-stu-id="5e91d-127">Use in scenarios where you want the user to pick an item from a list, but the items don’t need a lot of explanation.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/list-card.png" alt-text="Beispiel zeigt eine Listenkarte für adaptive Karten." border="false":::

### <a name="digest"></a><span data-ttu-id="5e91d-129">Digest</span><span class="sxs-lookup"><span data-stu-id="5e91d-129">Digest</span></span>

<span data-ttu-id="5e91d-130">Wird für News digests und Round-up-Beiträge verwendet.</span><span class="sxs-lookup"><span data-stu-id="5e91d-130">Use for news digests and round-up posts.</span></span> <span data-ttu-id="5e91d-131">Hinweis: Wir empfehlen die Miniaturansichtskarte für ein einzelnes Update oder Newselement.</span><span class="sxs-lookup"><span data-stu-id="5e91d-131">Note: We recommend the thumbnail card for a single update or news item.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/digest-card.png" alt-text="Beispiel zeigt eine Digestkarte für adaptive Karten." border="false":::

### <a name="media"></a><span data-ttu-id="5e91d-133">Medien</span><span class="sxs-lookup"><span data-stu-id="5e91d-133">Media</span></span>

<span data-ttu-id="5e91d-134">Verwenden Sie, wenn Sie Text und Medien, z. B. Audio oder Video, kombinieren möchten.</span><span class="sxs-lookup"><span data-stu-id="5e91d-134">Use when you want to combine text and media, like audio or video.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/media-card.png" alt-text="Beispiel zeigt eine Medienkarte für adaptive Karten." border="false":::

### <a name="people"></a><span data-ttu-id="5e91d-136">Personen</span><span class="sxs-lookup"><span data-stu-id="5e91d-136">People</span></span>

<span data-ttu-id="5e91d-137">Am besten, wenn Sie effizient vermitteln, wer an einer Aufgabe beteiligt ist.</span><span class="sxs-lookup"><span data-stu-id="5e91d-137">Best used when you to efficiently convey who's involved with a task.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/people-card.png" alt-text="Beispiel zeigt eine Adaptive Card-Personenkarte." border="false":::

### <a name="request-ticket"></a><span data-ttu-id="5e91d-139">Ticket anfordern</span><span class="sxs-lookup"><span data-stu-id="5e91d-139">Request ticket</span></span>

<span data-ttu-id="5e91d-140">Verwenden Sie, um schnelle Eingaben von einem Benutzer zu erhalten, um automatisch eine Aufgabe oder ein Ticket zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="5e91d-140">Use to get quick inputs from a user to automatically create a task or ticket.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/request-ticket-card.png" alt-text="Beispiel zeigt eine Ticketkarte für adaptive Kartenanforderung." border="false":::

### <a name="imageset"></a><span data-ttu-id="5e91d-142">ImageSet</span><span class="sxs-lookup"><span data-stu-id="5e91d-142">ImageSet</span></span>

<span data-ttu-id="5e91d-143">Verwenden Sie zum Senden mehrerer Bildminiaturansichten.</span><span class="sxs-lookup"><span data-stu-id="5e91d-143">Use to send multiple image thumbnails.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/image-set-card.png" alt-text="Beispiel zeigt eine Adaptive Card-Bildsatzkarte." border="false":::

### <a name="actionset"></a><span data-ttu-id="5e91d-145">ActionSet</span><span class="sxs-lookup"><span data-stu-id="5e91d-145">ActionSet</span></span>

<span data-ttu-id="5e91d-146">Verwenden Sie diese Option, wenn der Benutzer eine Schaltfläche auswählen und dann die Benutzereingaben von derselben Karte erfassen soll.</span><span class="sxs-lookup"><span data-stu-id="5e91d-146">Use when you want to the user to select a button, then gather addition user input from the same card.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/action-set-card.png" alt-text="Beispiel zeigt eine Aktionssatzkarte für adaptive Karten." border="false":::

### <a name="choiceset"></a><span data-ttu-id="5e91d-148">ChoiceSet</span><span class="sxs-lookup"><span data-stu-id="5e91d-148">ChoiceSet</span></span>

<span data-ttu-id="5e91d-149">Verwenden Sie, um mehrere Eingaben vom Benutzer zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="5e91d-149">Use to gather multiple inputs from the user.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/choice-set-card.png" alt-text="Beispiel zeigt eine Auswahlkarte für adaptive Karten." border="false":::

## <a name="anatomy"></a><span data-ttu-id="5e91d-151">Anatomie</span><span class="sxs-lookup"><span data-stu-id="5e91d-151">Anatomy</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/anatomy.png" alt-text="Beispiel zeigt eine Adaptive Card-Anatomiekarte." border="false":::

<span data-ttu-id="5e91d-153">Adaptive Karten haben eine menge Flexibilität.</span><span class="sxs-lookup"><span data-stu-id="5e91d-153">Adaptive Cards have a lot of flexibility.</span></span> <span data-ttu-id="5e91d-154">Es wird jedoch dringend empfohlen, die folgenden Komponenten auf jeder Karte zu verwenden:</span><span class="sxs-lookup"><span data-stu-id="5e91d-154">But at minimum, we strongly suggest including the following components in every card:</span></span>

|<span data-ttu-id="5e91d-155">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="5e91d-155">Counter</span></span>|<span data-ttu-id="5e91d-156">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5e91d-156">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="5e91d-157">A</span><span class="sxs-lookup"><span data-stu-id="5e91d-157">A</span></span>|<span data-ttu-id="5e91d-158">**Header**: Machen Sie Kopfzeilen klar und prägnant, aber beschreibend.</span><span class="sxs-lookup"><span data-stu-id="5e91d-158">**Header**: Make headers clear and concise, yet descriptive.</span></span>|
|<span data-ttu-id="5e91d-159">B</span><span class="sxs-lookup"><span data-stu-id="5e91d-159">B</span></span>|<span data-ttu-id="5e91d-160">**Textkörperkopie:** Verwenden Sie, um Details zu vermitteln, die entweder zu lang oder nicht wichtig genug sind, um sie in die Kopfzeile zu einfügen.</span><span class="sxs-lookup"><span data-stu-id="5e91d-160">**Body copy**: Use to convey detail that is either too long or not important enough to include in the header.</span></span>|
|<span data-ttu-id="5e91d-161">C</span><span class="sxs-lookup"><span data-stu-id="5e91d-161">C</span></span>|<span data-ttu-id="5e91d-162">**Primäre Aktionen:** Als bewährte Methode werden 1-3 primäre Aktionen bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="5e91d-162">**Primary actions**: As a best practice, include 1-3 primary actions.</span></span> <span data-ttu-id="5e91d-163">Maximal sechs sind zulässig.</span><span class="sxs-lookup"><span data-stu-id="5e91d-163">A maximum of six are allowed.</span></span>|

## <a name="best-practices"></a><span data-ttu-id="5e91d-164">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="5e91d-164">Best practices</span></span>

<span data-ttu-id="5e91d-165">Verwenden Sie diese Empfehlungen, um eine hochwertige App-Erfahrung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="5e91d-165">Use these recommendations to create a quality app experience.</span></span>

### <a name="primary-and-secondary-actions"></a><span data-ttu-id="5e91d-166">Primäre und sekundäre Aktionen</span><span class="sxs-lookup"><span data-stu-id="5e91d-166">Primary and secondary actions</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/adaptive-cards/actions-do.png" alt-text="Bewährte Methode, wie Sie nur einen kleinen Satz von Aktionen auf einer adaptiven Karte verwenden sollten." border="false":::

#### <a name="do-use-up-to-six-primary-actions"></a><span data-ttu-id="5e91d-168">Do: Verwenden von bis zu sechs primären Aktionen</span><span class="sxs-lookup"><span data-stu-id="5e91d-168">Do: Use up to six primary actions</span></span>

<span data-ttu-id="5e91d-169">Adaptive Karten können zwar sechs primäre Aktionen unterstützen, die meisten Karten benötigen dies jedoch nicht.</span><span class="sxs-lookup"><span data-stu-id="5e91d-169">While Adaptive Cards can support six primary actions, most cards don’t need that.</span></span> <span data-ttu-id="5e91d-170">Die Aktionen sollten klar, präzise und direkt sein.</span><span class="sxs-lookup"><span data-stu-id="5e91d-170">Actions should be clear, concise, and straight forward.</span></span> <span data-ttu-id="5e91d-171">Weniger ist mehr.</span><span class="sxs-lookup"><span data-stu-id="5e91d-171">Less is more.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/adaptive-cards/actions-dont.png" alt-text="Bewährte Methode, um Benutzer nicht mit zu vielen Aktionen auf einer adaptiven Karte zu überfordern." border="false":::

#### <a name="dont-use-more-than-six-primary-actions"></a><span data-ttu-id="5e91d-173">Don't: Verwenden von mehr als sechs primären Aktionen</span><span class="sxs-lookup"><span data-stu-id="5e91d-173">Don't: Use more than six primary actions</span></span>

<span data-ttu-id="5e91d-174">Adaptive Karten sollten schnell aktionenfähige Inhalte enthalten.</span><span class="sxs-lookup"><span data-stu-id="5e91d-174">Adaptive Cards should present quick, actionable content.</span></span> <span data-ttu-id="5e91d-175">Zu viele Aktionen können einen Benutzer überfordern.</span><span class="sxs-lookup"><span data-stu-id="5e91d-175">Too many actions can overwhelm a user.</span></span>

   :::column-end:::
:::row-end:::

### <a name="frequency"></a><span data-ttu-id="5e91d-176">Häufigkeit</span><span class="sxs-lookup"><span data-stu-id="5e91d-176">Frequency</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/frequency-do.png" alt-text="Bewährte Methode zur Häufigkeit adaptiver Karten." border="false":::

#### <a name="do-be-concise"></a><span data-ttu-id="5e91d-178">Do: Kurz sein</span><span class="sxs-lookup"><span data-stu-id="5e91d-178">Do: Be concise</span></span>

<span data-ttu-id="5e91d-179">Es ist einfach, mehrere Karten in eine Unterhaltung zu senden, aber sobald Karten nicht mehr angezeigt werden, werden sie weniger nützlich.</span><span class="sxs-lookup"><span data-stu-id="5e91d-179">It's easy to send multiple cards into a conversation, but once cards scroll out of view, they become less useful.</span></span> <span data-ttu-id="5e91d-180">Versuchen Sie, sich auf das Wesentliche zu beschränken.</span><span class="sxs-lookup"><span data-stu-id="5e91d-180">Try to limit yourself to the essentials.</span></span> <span data-ttu-id="5e91d-181">Dies gilt insbesondere in einem Kanal, in dem Benutzer weniger Toleranz für das haben, was sie als "Rauschen" wahrnehmen.</span><span class="sxs-lookup"><span data-stu-id="5e91d-181">This is especially true in a channel where users have less tolerance for what they perceive as "noise".</span></span>
