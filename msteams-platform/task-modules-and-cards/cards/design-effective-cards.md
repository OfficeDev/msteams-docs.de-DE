---
title: Entwerfen adaptiver Karten für Ihre App
description: Erfahren Sie, wie Sie adaptive Karten für Teams entwerfen und das Microsoft Teams UI Kit erhalten.
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: b4d5f43268c7bd5afecb56d26eb0d49ed6c9002b
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "52630282"
---
# <a name="designing-adaptive-cards-for-your-microsoft-teams-app"></a><span data-ttu-id="df66d-103">Entwerfen adaptiver Karten für Ihre Microsoft Teams App</span><span class="sxs-lookup"><span data-stu-id="df66d-103">Designing Adaptive Cards for your Microsoft Teams app</span></span>

<span data-ttu-id="df66d-104">Eine adaptive Karte enthält einen Freihandformtext mit Kartenelementen und optionalen Aktionen.</span><span class="sxs-lookup"><span data-stu-id="df66d-104">An Adaptive Card contains a freeform body of card elements and optional set of actions.</span></span> <span data-ttu-id="df66d-105">Adaptive Karten sind aktionenfähige Codeausschnitte von Inhalten, die Sie einer Unterhaltung über einen Bot oder eine Messagingerweiterung hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="df66d-105">Adaptive Cards are actionable snippets of content that you can add to a conversation through a bot or messaging extension.</span></span> <span data-ttu-id="df66d-106">Mithilfe von Text, Grafiken und Schaltflächen bieten diese Karten eine umfassende Kommunikation für Ihre Zielgruppe.</span><span class="sxs-lookup"><span data-stu-id="df66d-106">Using text, graphics, and buttons, these cards provide rich communication to your audience.</span></span>

<span data-ttu-id="df66d-107">Das Adaptive Card-Framework wird in vielen Microsoft-Produkten verwendet, einschließlich Teams.</span><span class="sxs-lookup"><span data-stu-id="df66d-107">The Adaptive Card framework is used across many Microsoft products, including Teams.</span></span> <span data-ttu-id="df66d-108">Sie können Karten innerhalb von Nachrichten über Bots oder Messagingerweiterungen an Benutzer senden.</span><span class="sxs-lookup"><span data-stu-id="df66d-108">You can send cards inside messages to users via bots or messaging extensions.</span></span> <span data-ttu-id="df66d-109">Benutzer können auch Aktionen auf Karten ausführen, wenn vorhanden.</span><span class="sxs-lookup"><span data-stu-id="df66d-109">Users can also take actions on cards when present.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/adaptive-card-overview.png" alt-text="Übersichtsbeispiel einer adaptiven Karte." border="false":::

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="df66d-111">Microsoft Teams-UI-Kit</span><span class="sxs-lookup"><span data-stu-id="df66d-111">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="df66d-112">Umfassendere Entwurfsrichtlinien für adaptive Karten finden Sie in Teams, einschließlich Elementen, die Sie bei Bedarf packen und ändern können, im Microsoft Teams UI Kit.</span><span class="sxs-lookup"><span data-stu-id="df66d-112">You can find more comprehensive design guidelines for Adaptive Cards in Teams, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span> <span data-ttu-id="df66d-113">Das Benutzeroberflächenkit behandelt auch wichtige Themen wie Design, Barrierefreiheit und reaktionsschnelle Größenanpassung.</span><span class="sxs-lookup"><span data-stu-id="df66d-113">The UI kit also covers essential topics such as theming, accessibility, and responsive sizing.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="df66d-114">Holen Sie sich das Microsoft Teams-UI-Kit (Figma)</span><span class="sxs-lookup"><span data-stu-id="df66d-114">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="adaptive-cards-designer"></a><span data-ttu-id="df66d-115">Designer für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="df66d-115">Adaptive Cards designer</span></span>

<span data-ttu-id="df66d-116">Sie können ihre adaptiven Karten auch direkt im Browser entwerfen.</span><span class="sxs-lookup"><span data-stu-id="df66d-116">You also can start designing your Adaptive Cards directly in the browser.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="df66d-117">Testen des Designers für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="df66d-117">Try the Adaptive Cards designer</span></span>](https://adaptivecards.io/designer/)

## <a name="types-of-adaptive-cards"></a><span data-ttu-id="df66d-118">Typen adaptiver Karten</span><span class="sxs-lookup"><span data-stu-id="df66d-118">Types of Adaptive Cards</span></span>

### <a name="hero"></a><span data-ttu-id="df66d-119">Hero</span><span class="sxs-lookup"><span data-stu-id="df66d-119">Hero</span></span>

<span data-ttu-id="df66d-120">Unsere größte Karte.</span><span class="sxs-lookup"><span data-stu-id="df66d-120">Our largest card.</span></span> <span data-ttu-id="df66d-121">Wird für die Freigabe von Artikeln oder Szenarien verwendet, in denen ein Bild den größten Teil der Geschichte beschreibt.</span><span class="sxs-lookup"><span data-stu-id="df66d-121">Use for sharing articles or scenarios where an image tells most of the story.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="df66d-122">Desktop</span><span class="sxs-lookup"><span data-stu-id="df66d-122">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/hero-card.png" alt-text="Beispiel zeigt eine Adaptive Card Hero Card." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="df66d-124">Mobil</span><span class="sxs-lookup"><span data-stu-id="df66d-124">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-hero-card.png" alt-text="Beispiel zeigt eine Adaptive Card Hero Card auf Mobilgeräten." border="false":::

---

### <a name="thumbnail"></a><span data-ttu-id="df66d-126">Miniaturansicht</span><span class="sxs-lookup"><span data-stu-id="df66d-126">Thumbnail</span></span>

<span data-ttu-id="df66d-127">Verwenden Sie diese Methode zum Senden einer einfachen Nachricht mit Aktionen.</span><span class="sxs-lookup"><span data-stu-id="df66d-127">Use for sending a simple actionable message.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="df66d-128">Desktop</span><span class="sxs-lookup"><span data-stu-id="df66d-128">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/thumbnail-card.png" alt-text="Beispiel zeigt eine Miniaturansichtskarte für adaptive Karten." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="df66d-130">Mobil</span><span class="sxs-lookup"><span data-stu-id="df66d-130">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-thumbnail-card.png" alt-text="Beispiel zeigt eine Miniaturansichtskarte für adaptive Karten auf Mobilgeräten." border="false":::

---

### <a name="list"></a><span data-ttu-id="df66d-132">Liste</span><span class="sxs-lookup"><span data-stu-id="df66d-132">List</span></span>

<span data-ttu-id="df66d-133">Wird in Szenarien verwendet, in denen der Benutzer ein Element aus einer Liste auswählen soll, die Elemente jedoch nicht viel Erläuterung benötigen.</span><span class="sxs-lookup"><span data-stu-id="df66d-133">Use in scenarios where you want the user to pick an item from a list, but the items don’t need a lot of explanation.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="df66d-134">Desktop</span><span class="sxs-lookup"><span data-stu-id="df66d-134">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/list-card.png" alt-text="Beispiel zeigt eine Listenkarte für adaptive Karten." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="df66d-136">Mobil</span><span class="sxs-lookup"><span data-stu-id="df66d-136">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-list-card.png" alt-text="Beispiel zeigt eine Listenkarte für adaptive Karten auf Mobilgeräten." border="false":::

---

### Digest

Use for news digests and round-up posts. Note: We recommend the thumbnail card for a single update or news item.

# [Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/digest-card.png" alt-text="Example shows an Adaptive Card digest card." border="false":::

# [Mobile](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-digest-card.png" alt-text="Example shows an Adaptive Card digest card on mobile." border="false":::

---

### <a name="media"></a><span data-ttu-id="df66d-138">Medien</span><span class="sxs-lookup"><span data-stu-id="df66d-138">Media</span></span>

<span data-ttu-id="df66d-139">Verwenden Sie, wenn Sie Text und Medien, z. B. Audio oder Video, kombinieren möchten.</span><span class="sxs-lookup"><span data-stu-id="df66d-139">Use when you want to combine text and media, like audio or video.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="df66d-140">Desktop</span><span class="sxs-lookup"><span data-stu-id="df66d-140">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/media-card.png" alt-text="Beispiel zeigt eine Medienkarte für adaptive Karten." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="df66d-142">Mobil</span><span class="sxs-lookup"><span data-stu-id="df66d-142">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-media-card.png" alt-text="Beispiel zeigt eine Medienkarte für adaptive Karten auf Mobilgeräten." border="false":::

---

### <a name="people"></a><span data-ttu-id="df66d-144">Personen</span><span class="sxs-lookup"><span data-stu-id="df66d-144">People</span></span>

<span data-ttu-id="df66d-145">Am besten, wenn Sie effizient vermitteln, wer an einer Aufgabe beteiligt ist.</span><span class="sxs-lookup"><span data-stu-id="df66d-145">Best used when you to efficiently convey who's involved with a task.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="df66d-146">Desktop</span><span class="sxs-lookup"><span data-stu-id="df66d-146">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/people-card.png" alt-text="Beispiel zeigt eine Adaptive Card-Personenkarte." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="df66d-148">Mobil</span><span class="sxs-lookup"><span data-stu-id="df66d-148">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-people-card.png" alt-text="Beispiel zeigt eine Adaptive Card-Personenkarte auf Mobilgeräten." border="false":::

---

### <a name="request-ticket"></a><span data-ttu-id="df66d-150">Ticket anfordern</span><span class="sxs-lookup"><span data-stu-id="df66d-150">Request ticket</span></span>

<span data-ttu-id="df66d-151">Verwenden Sie, um schnelle Eingaben von einem Benutzer zu erhalten, um automatisch eine Aufgabe oder ein Ticket zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="df66d-151">Use to get quick inputs from a user to automatically create a task or ticket.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="df66d-152">Desktop</span><span class="sxs-lookup"><span data-stu-id="df66d-152">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/request-ticket-card.png" alt-text="Beispiel zeigt eine Ticketkarte für adaptive Kartenanforderung." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="df66d-154">Mobil</span><span class="sxs-lookup"><span data-stu-id="df66d-154">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-request-ticket-card.png" alt-text="Beispiel zeigt eine Adaptive Card-Anforderungsticketkarte auf Mobilgeräten." border="false":::

---

### <a name="image-set"></a><span data-ttu-id="df66d-156">Bildsatz</span><span class="sxs-lookup"><span data-stu-id="df66d-156">Image set</span></span>

<span data-ttu-id="df66d-157">Verwenden Sie zum Senden mehrerer Bildminiaturansichten.</span><span class="sxs-lookup"><span data-stu-id="df66d-157">Use to send multiple image thumbnails.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="df66d-158">Desktop</span><span class="sxs-lookup"><span data-stu-id="df66d-158">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/image-set-card.png" alt-text="Beispiel zeigt eine Adaptive Card-Bildsatzkarte." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="df66d-160">Mobil</span><span class="sxs-lookup"><span data-stu-id="df66d-160">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-image-set-card.png" alt-text="Beispiel zeigt eine Adaptive Card-Bildsatzkarte auf Mobilgeräten." border="false":::

---

### <a name="action-set"></a><span data-ttu-id="df66d-162">Aktionssatz</span><span class="sxs-lookup"><span data-stu-id="df66d-162">Action set</span></span>

<span data-ttu-id="df66d-163">Verwenden Sie diese Option, wenn der Benutzer eine Schaltfläche auswählen und dann die Benutzereingaben von derselben Karte erfassen soll.</span><span class="sxs-lookup"><span data-stu-id="df66d-163">Use when you want to the user to select a button, then gather addition user input from the same card.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="df66d-164">Desktop</span><span class="sxs-lookup"><span data-stu-id="df66d-164">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/action-set-card.png" alt-text="Beispiel zeigt eine Aktionssatzkarte für adaptive Karten." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="df66d-166">Mobil</span><span class="sxs-lookup"><span data-stu-id="df66d-166">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-action-set-card.png" alt-text="Beispiel zeigt eine Aktionssatzkarte für adaptive Karten auf Mobilgeräten." border="false":::

---

### <a name="choice-set"></a><span data-ttu-id="df66d-168">Auswahlsatz</span><span class="sxs-lookup"><span data-stu-id="df66d-168">Choice set</span></span>

<span data-ttu-id="df66d-169">Verwenden Sie, um mehrere Eingaben vom Benutzer zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="df66d-169">Use to gather multiple inputs from the user.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="df66d-170">Desktop</span><span class="sxs-lookup"><span data-stu-id="df66d-170">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/choice-set-card.png" alt-text="Beispiel zeigt eine Auswahlkarte für adaptive Karten." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="df66d-172">Mobil</span><span class="sxs-lookup"><span data-stu-id="df66d-172">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-choice-set-card.png" alt-text="Beispiel zeigt eine Auswahlkarte für adaptive Karten auf Mobilgeräten." border="false":::

---

## <a name="anatomy"></a><span data-ttu-id="df66d-174">Anatomie</span><span class="sxs-lookup"><span data-stu-id="df66d-174">Anatomy</span></span>

<span data-ttu-id="df66d-175">Adaptive Karten haben eine menge Flexibilität.</span><span class="sxs-lookup"><span data-stu-id="df66d-175">Adaptive Cards have a lot of flexibility.</span></span> <span data-ttu-id="df66d-176">Es wird jedoch dringend empfohlen, die folgenden Komponenten auf jeder Karte zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="df66d-176">But at minimum, we strongly suggest including the following components in every card.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="df66d-177">Desktop</span><span class="sxs-lookup"><span data-stu-id="df66d-177">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/anatomy.png" alt-text="EExample zeigt adaptive Kartenanatomie." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="df66d-179">Mobil</span><span class="sxs-lookup"><span data-stu-id="df66d-179">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-anatomy.png" alt-text="Beispiel zeigt adaptive Kartenanatomie auf Mobilgeräten." border="false":::

---

|<span data-ttu-id="df66d-181">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="df66d-181">Counter</span></span>|<span data-ttu-id="df66d-182">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="df66d-182">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="df66d-183">A</span><span class="sxs-lookup"><span data-stu-id="df66d-183">A</span></span>|<span data-ttu-id="df66d-184">**Header**: Machen Sie Ihre Kopfzeilen klar und präzise.</span><span class="sxs-lookup"><span data-stu-id="df66d-184">**Header**: Make your headers clear and concise.</span></span>|
|<span data-ttu-id="df66d-185">B</span><span class="sxs-lookup"><span data-stu-id="df66d-185">B</span></span>|<span data-ttu-id="df66d-186">**Textkörperkopie:** Übermitteln Sie Details, die entweder zu lang oder nicht wichtig genug sind, um in die Kopfzeile zu enthalten.</span><span class="sxs-lookup"><span data-stu-id="df66d-186">**Body copy**: Convey details that are either too long or not important enough to include in the header.</span></span>|
|<span data-ttu-id="df66d-187">C</span><span class="sxs-lookup"><span data-stu-id="df66d-187">C</span></span>|<span data-ttu-id="df66d-188">**Primäre Aktionen:** Als bewährte Methode werden 1-3 primäre Aktionen bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="df66d-188">**Primary actions**: As a best practice, include 1-3 primary actions.</span></span> <span data-ttu-id="df66d-189">Sie können bis zu sechs Personen haben.</span><span class="sxs-lookup"><span data-stu-id="df66d-189">You can have up to six.</span></span>|

## <a name="best-practices"></a><span data-ttu-id="df66d-190">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="df66d-190">Best practices</span></span>

<span data-ttu-id="df66d-191">Verwenden Sie diese Empfehlungen, um eine hochwertige App-Erfahrung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="df66d-191">Use these recommendations to create a quality app experience.</span></span>

### <a name="primary-and-secondary-actions"></a><span data-ttu-id="df66d-192">Primäre und sekundäre Aktionen</span><span class="sxs-lookup"><span data-stu-id="df66d-192">Primary and secondary actions</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/adaptive-cards/actions-do.png" alt-text="Bewährte Methode, wie Sie nur einen kleinen Satz von Aktionen auf einer adaptiven Karte verwenden sollten." border="false":::

#### <a name="do-use-up-to-six-primary-actions"></a><span data-ttu-id="df66d-194">Do: Verwenden von bis zu sechs primären Aktionen</span><span class="sxs-lookup"><span data-stu-id="df66d-194">Do: Use up to six primary actions</span></span>

<span data-ttu-id="df66d-195">Adaptive Karten können zwar sechs primäre Aktionen unterstützen, die meisten Karten benötigen dies jedoch nicht.</span><span class="sxs-lookup"><span data-stu-id="df66d-195">While Adaptive Cards can support six primary actions, most cards don’t need that.</span></span> <span data-ttu-id="df66d-196">Die Aktionen sollten klar, präzise und direkt sein.</span><span class="sxs-lookup"><span data-stu-id="df66d-196">Actions should be clear, concise, and straight forward.</span></span> <span data-ttu-id="df66d-197">Weniger ist mehr.</span><span class="sxs-lookup"><span data-stu-id="df66d-197">Less is more.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/adaptive-cards/actions-dont.png" alt-text="Bewährte Methode, um Benutzer nicht mit zu vielen Aktionen auf einer adaptiven Karte zu überfordern." border="false":::

#### <a name="dont-use-more-than-six-primary-actions"></a><span data-ttu-id="df66d-199">Don't: Verwenden von mehr als sechs primären Aktionen</span><span class="sxs-lookup"><span data-stu-id="df66d-199">Don't: Use more than six primary actions</span></span>

<span data-ttu-id="df66d-200">Adaptive Karten sollten schnell aktionenfähige Inhalte enthalten.</span><span class="sxs-lookup"><span data-stu-id="df66d-200">Adaptive Cards should present quick, actionable content.</span></span> <span data-ttu-id="df66d-201">Zu viele Aktionen können einen Benutzer überfordern.</span><span class="sxs-lookup"><span data-stu-id="df66d-201">Too many actions can overwhelm a user.</span></span>

   :::column-end:::
:::row-end:::

### <a name="frequency"></a><span data-ttu-id="df66d-202">Häufigkeit</span><span class="sxs-lookup"><span data-stu-id="df66d-202">Frequency</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/frequency-do.png" alt-text="Bewährte Methode zur Häufigkeit adaptiver Karten." border="false":::

#### <a name="do-be-concise"></a><span data-ttu-id="df66d-204">Do: Kurz sein</span><span class="sxs-lookup"><span data-stu-id="df66d-204">Do: Be concise</span></span>

<span data-ttu-id="df66d-205">Es ist einfach, mehrere Karten in eine Unterhaltung zu senden, aber sobald Karten nicht mehr angezeigt werden, werden sie weniger nützlich.</span><span class="sxs-lookup"><span data-stu-id="df66d-205">It's easy to send multiple cards into a conversation, but once cards scroll out of view, they become less useful.</span></span> <span data-ttu-id="df66d-206">Versuchen Sie, sich auf das Wesentliche zu beschränken.</span><span class="sxs-lookup"><span data-stu-id="df66d-206">Try to limit yourself to the essentials.</span></span> <span data-ttu-id="df66d-207">Dies gilt insbesondere in einem Kanal, in dem Benutzer weniger Toleranz für das haben, was sie als "Rauschen" wahrnehmen.</span><span class="sxs-lookup"><span data-stu-id="df66d-207">This is especially true in a channel where users have less tolerance for what they perceive as "noise".</span></span>
