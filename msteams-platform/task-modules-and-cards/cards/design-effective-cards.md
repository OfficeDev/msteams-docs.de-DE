---
title: Entwerfen adaptiver Karten für Ihre App
description: Erfahren Sie, wie Sie adaptive Karten für Teams entwerfen und das Microsoft Teams UI Kit erhalten.
localization_priority: Priority
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 8e56928da44e22006feb59715c8bdbf821ec4c42
ms.sourcegitcommit: 99b1f151e4e36a86c6a5d2ccbde01bf45b61f526
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2021
ms.locfileid: "53037656"
---
# <a name="designing-adaptive-cards-for-your-microsoft-teams-app"></a><span data-ttu-id="49f40-103">Entwerfen adaptiver Karten für Ihre Microsoft Teams-App</span><span class="sxs-lookup"><span data-stu-id="49f40-103">Designing Adaptive Cards for your Microsoft Teams app</span></span>

<span data-ttu-id="49f40-104">Eine adaptive Karte enthält einen Freihandform-Textkörper mit Kartenelementen und optionalen Aktionen.</span><span class="sxs-lookup"><span data-stu-id="49f40-104">An Adaptive Card contains a freeform body of card elements and optional set of actions.</span></span> <span data-ttu-id="49f40-105">Adaptive Karten sind Aktionen erfordernde Inhaltsausschnitte, die Sie einer Unterhaltung über einen Bot oder eine Messagingerweiterung hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="49f40-105">Adaptive Cards are actionable snippets of content that you can add to a conversation through a bot or messaging extension.</span></span> <span data-ttu-id="49f40-106">Mithilfe von Text, Grafiken und Schaltflächen ermöglichen diese Karten eine umfassende Kommunikation mit Ihrer Zielgruppe.</span><span class="sxs-lookup"><span data-stu-id="49f40-106">Using text, graphics, and buttons, these cards provide rich communication to your audience.</span></span>

<span data-ttu-id="49f40-107">Das Framework für adaptive Karten wird in vielen Microsoft-Produkten verwendet, einschließlich Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="49f40-107">The Adaptive Card framework is used across many Microsoft products, including Teams.</span></span> <span data-ttu-id="49f40-108">Sie können Karten in Nachrichten über Bots oder Messagingerweiterungen an Benutzer senden.</span><span class="sxs-lookup"><span data-stu-id="49f40-108">You can send cards inside messages to users via bots or messaging extensions.</span></span> <span data-ttu-id="49f40-109">Benutzer können auch Aktionen auf Karten durchführen, wenn diese bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="49f40-109">Users can also take actions on cards when present.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/adaptive-card-overview.png" alt-text="Übersichtsbeispiel für eine adaptive Karte." border="false":::

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="49f40-111">Microsoft Teams-UI-Kit</span><span class="sxs-lookup"><span data-stu-id="49f40-111">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="49f40-112">Umfassendere Entwurfsrichtlinien für adaptive Karten, einschließlich Elemente, die Sie nach Bedarf abrufen und ändern können, finden Sie im Microsoft Teams-UI-Kit.</span><span class="sxs-lookup"><span data-stu-id="49f40-112">You can find more comprehensive design guidelines for Adaptive Cards in Teams, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span> <span data-ttu-id="49f40-113">Das UI-Kit deckt auch wesentliche Themen wie Designs, Barrierefreiheit und dynamische Größenanpassung ab.</span><span class="sxs-lookup"><span data-stu-id="49f40-113">The UI kit also covers essential topics such as theming, accessibility, and responsive sizing.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="49f40-114">Holen Sie sich das Microsoft Teams-UI-Kit (Figma)</span><span class="sxs-lookup"><span data-stu-id="49f40-114">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="adaptive-cards-designer"></a><span data-ttu-id="49f40-115">Designer für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="49f40-115">Adaptive Cards designer</span></span>

<span data-ttu-id="49f40-116">Sie können ihre adaptiven Karten auch direkt im Browser entwerfen.</span><span class="sxs-lookup"><span data-stu-id="49f40-116">You also can start designing your Adaptive Cards directly in the browser.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="49f40-117">Designer für adaptive Karten testen</span><span class="sxs-lookup"><span data-stu-id="49f40-117">Try the Adaptive Cards designer</span></span>](https://adaptivecards.io/designer/)

## <a name="types-of-adaptive-cards"></a><span data-ttu-id="49f40-118">Typen von adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="49f40-118">Types of Adaptive Cards</span></span>

### <a name="hero"></a><span data-ttu-id="49f40-119">Hero</span><span class="sxs-lookup"><span data-stu-id="49f40-119">Hero</span></span>

<span data-ttu-id="49f40-120">Unsere größte Karte.</span><span class="sxs-lookup"><span data-stu-id="49f40-120">Our largest card.</span></span> <span data-ttu-id="49f40-121">Wird für die Freigabe von Artikeln oder Szenarien verwendet, in denen Bilder den größten Teil der Geschichte erzählen.</span><span class="sxs-lookup"><span data-stu-id="49f40-121">Use for sharing articles or scenarios where an image tells most of the story.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="49f40-122">Desktop</span><span class="sxs-lookup"><span data-stu-id="49f40-122">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/hero-card.png" alt-text="Beispiel einer adaptiven Hero-Karte." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="49f40-124">Mobilgerät</span><span class="sxs-lookup"><span data-stu-id="49f40-124">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-hero-card.png" alt-text="Beispiel einer adaptiven Hero-Karte auf einem Mobilgerät." border="false":::

---

### <a name="thumbnail"></a><span data-ttu-id="49f40-126">Miniaturansicht</span><span class="sxs-lookup"><span data-stu-id="49f40-126">Thumbnail</span></span>

<span data-ttu-id="49f40-127">Wird zum Senden einer einfachen, Aktionen erfordernden Nachricht verwendet.</span><span class="sxs-lookup"><span data-stu-id="49f40-127">Use for sending a simple actionable message.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="49f40-128">Desktop</span><span class="sxs-lookup"><span data-stu-id="49f40-128">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/thumbnail-card.png" alt-text="Beispiel einer adaptiven Miniaturansichtskarte." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="49f40-130">Mobilgerät</span><span class="sxs-lookup"><span data-stu-id="49f40-130">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-thumbnail-card.png" alt-text="Beispiel einer adaptiven Miniaturansichtskarte auf einem Mobilgerät." border="false":::

---

### <a name="list"></a><span data-ttu-id="49f40-132">Liste</span><span class="sxs-lookup"><span data-stu-id="49f40-132">List</span></span>

<span data-ttu-id="49f40-133">Wird in Szenarien verwendet, in denen der Benutzer ein Element aus einer Liste auswählen soll, die Elemente jedoch nicht viel Erklärung benötigen.</span><span class="sxs-lookup"><span data-stu-id="49f40-133">Use in scenarios where you want the user to pick an item from a list, but the items don’t need a lot of explanation.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="49f40-134">Desktop</span><span class="sxs-lookup"><span data-stu-id="49f40-134">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/list-card.png" alt-text="Beispiel einer adaptiven Listenkarte." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="49f40-136">Mobilgerät</span><span class="sxs-lookup"><span data-stu-id="49f40-136">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-list-card.png" alt-text="Beispiel einer adaptiven Listenkarte auf einem Mobilgerät." border="false":::

---
Use for news digests and round-up posts. Note: We recommend the thumbnail card for a single update or news item.
':::image type="content" source="../../assets/images/adaptive-cards/digest-card.png" alt-text="Example shows an Adaptive Card digest card." border="false"::': null
':::image type="content" source="../../assets/images/adaptive-cards/mobile-digest-card.png" alt-text="Example shows an Adaptive Card digest card on mobile." border="false"::': null
---

### <a name="media"></a><span data-ttu-id="49f40-138">Medien</span><span class="sxs-lookup"><span data-stu-id="49f40-138">Media</span></span>

<span data-ttu-id="49f40-139">Wird verwendet, wenn Sie Text und Medien kombinieren möchten, z. B. Audio oder Video.</span><span class="sxs-lookup"><span data-stu-id="49f40-139">Use when you want to combine text and media, like audio or video.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="49f40-140">Desktop</span><span class="sxs-lookup"><span data-stu-id="49f40-140">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/media-card.png" alt-text="Beispiel einer adaptiven Medienkarte." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="49f40-142">Mobilgerät</span><span class="sxs-lookup"><span data-stu-id="49f40-142">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-media-card.png" alt-text="Beispiel einer adaptiven Medienkarte auf einem Mobilgerät." border="false":::

---

### <a name="people"></a><span data-ttu-id="49f40-144">Personen</span><span class="sxs-lookup"><span data-stu-id="49f40-144">People</span></span>

<span data-ttu-id="49f40-145">Am besten geeignet, wenn Sie effizient vermitteln möchten, wer an einer Aufgabe beteiligt ist.</span><span class="sxs-lookup"><span data-stu-id="49f40-145">Best used when you to efficiently convey who's involved with a task.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="49f40-146">Desktop</span><span class="sxs-lookup"><span data-stu-id="49f40-146">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/people-card.png" alt-text="Beispiel einer adaptiven Personenkarte." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="49f40-148">Mobilgerät</span><span class="sxs-lookup"><span data-stu-id="49f40-148">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-people-card.png" alt-text="Beispiel einer adaptiven Personenkarte auf einem Mobilgerät." border="false":::

---

### <a name="request-ticket"></a><span data-ttu-id="49f40-150">Anforderungsticket</span><span class="sxs-lookup"><span data-stu-id="49f40-150">Request ticket</span></span>

<span data-ttu-id="49f40-151">Wird verwendet, um von einem Benutzer schnelle Eingaben zum automatischen Erstellen einer Aufgabe oder eines Tickets zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="49f40-151">Use to get quick inputs from a user to automatically create a task or ticket.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="49f40-152">Desktop</span><span class="sxs-lookup"><span data-stu-id="49f40-152">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/request-ticket-card.png" alt-text="Beispiel einer adaptiven Anforderungsticketkarte." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="49f40-154">Mobilgerät</span><span class="sxs-lookup"><span data-stu-id="49f40-154">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-request-ticket-card.png" alt-text="Beispiel einer adaptiven Anforderungsticketkarte auf einem Mobilgerät." border="false":::

---

### <a name="image-set"></a><span data-ttu-id="49f40-156">Bildergruppe</span><span class="sxs-lookup"><span data-stu-id="49f40-156">Image set</span></span>

<span data-ttu-id="49f40-157">Wird verwendet, um mehrere Miniaturansichten von Bildern zu senden.</span><span class="sxs-lookup"><span data-stu-id="49f40-157">Use to send multiple image thumbnails.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="49f40-158">Desktop</span><span class="sxs-lookup"><span data-stu-id="49f40-158">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/image-set-card.png" alt-text="Beispiel einer adaptiven Bildergruppenkarte." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="49f40-160">Mobilgerät</span><span class="sxs-lookup"><span data-stu-id="49f40-160">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-image-set-card.png" alt-text="Beispiel einer adaptiven Bildergruppenkarte auf einem Mobilgerät." border="false":::

---

### <a name="action-set"></a><span data-ttu-id="49f40-162">Aktionsgruppe</span><span class="sxs-lookup"><span data-stu-id="49f40-162">Action set</span></span>

<span data-ttu-id="49f40-163">Wird verwendet, wenn der Benutzer eine Schaltfläche auswählen soll, und Sie dann zusätzliche Benutzereingaben über dieselbe Karte erfassen möchten.</span><span class="sxs-lookup"><span data-stu-id="49f40-163">Use when you want to the user to select a button, then gather addition user input from the same card.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="49f40-164">Desktop</span><span class="sxs-lookup"><span data-stu-id="49f40-164">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/action-set-card.png" alt-text="Beispiel einer adaptiven Aktionsgruppenkarte." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="49f40-166">Mobilgerät</span><span class="sxs-lookup"><span data-stu-id="49f40-166">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-action-set-card.png" alt-text="Beispiel einer adaptiven Aktionsgruppenkarte auf einem Mobilgerät." border="false":::

---

### <a name="choice-set"></a><span data-ttu-id="49f40-168">Auswahlgruppe</span><span class="sxs-lookup"><span data-stu-id="49f40-168">Choice set</span></span>

<span data-ttu-id="49f40-169">Wird verwendet, um mehrere Eingaben vom Benutzer zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="49f40-169">Use to gather multiple inputs from the user.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="49f40-170">Desktop</span><span class="sxs-lookup"><span data-stu-id="49f40-170">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/choice-set-card.png" alt-text="Beispiel einer adaptiven Auswahlgruppenkarte." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="49f40-172">Mobilgerät</span><span class="sxs-lookup"><span data-stu-id="49f40-172">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-choice-set-card.png" alt-text="Beispiel einer adaptiven Auswahlgruppenkarte auf einem Mobilgerät." border="false":::

---

## <a name="anatomy"></a><span data-ttu-id="49f40-174">Anatomie</span><span class="sxs-lookup"><span data-stu-id="49f40-174">Anatomy</span></span>

<span data-ttu-id="49f40-175">Adaptive Karten sind sehr flexibel.</span><span class="sxs-lookup"><span data-stu-id="49f40-175">Adaptive Cards have a lot of flexibility.</span></span> <span data-ttu-id="49f40-176">Es wird jedoch dringend empfohlen, mindestens die folgenden Komponenten auf jeder Karte zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="49f40-176">But at minimum, we strongly suggest including the following components in every card.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="49f40-177">Desktop</span><span class="sxs-lookup"><span data-stu-id="49f40-177">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/anatomy.png" alt-text="Beispiel der Anatomie adaptiver Karten." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="49f40-179">Mobilgerät</span><span class="sxs-lookup"><span data-stu-id="49f40-179">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-anatomy.png" alt-text="Beispiel der Anatomie adaptiver Karten auf einem Mobilgerät." border="false":::

---

|<span data-ttu-id="49f40-181">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="49f40-181">Counter</span></span>|<span data-ttu-id="49f40-182">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="49f40-182">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="49f40-183">A</span><span class="sxs-lookup"><span data-stu-id="49f40-183">A</span></span>|<span data-ttu-id="49f40-184">**Kopfzeile**: Sorgen Sie dafür, dass Ihre Kopfzeilen klar und präzise sind.</span><span class="sxs-lookup"><span data-stu-id="49f40-184">**Header**: Make your headers clear and concise.</span></span>|
|<span data-ttu-id="49f40-185">B</span><span class="sxs-lookup"><span data-stu-id="49f40-185">B</span></span>|<span data-ttu-id="49f40-186">**Textkörper**: Übermitteln Sie hier Details, die entweder zu lang oder nicht wichtig genug sind, um sie in die Kopfzeile aufzunehmen.</span><span class="sxs-lookup"><span data-stu-id="49f40-186">**Body copy**: Convey details that are either too long or not important enough to include in the header.</span></span>|
|<span data-ttu-id="49f40-187">C</span><span class="sxs-lookup"><span data-stu-id="49f40-187">C</span></span>|<span data-ttu-id="49f40-188">**Primäre Aktionen**: Schließen Sie als bewährte Methode 1 bis 3 primäre Aktionen ein.</span><span class="sxs-lookup"><span data-stu-id="49f40-188">**Primary actions**: As a best practice, include 1-3 primary actions.</span></span> <span data-ttu-id="49f40-189">Es können bis zu sechs eingefügt werden.</span><span class="sxs-lookup"><span data-stu-id="49f40-189">You can have up to six.</span></span>|

## <a name="best-practices"></a><span data-ttu-id="49f40-190">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="49f40-190">Best practices</span></span>

<span data-ttu-id="49f40-191">Verwenden Sie diese Empfehlungen, um eine hochwertige App-Erfahrung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="49f40-191">Use these recommendations to create a quality app experience.</span></span>

### <a name="primary-and-secondary-actions"></a><span data-ttu-id="49f40-192">Primäre und sekundäre Aktionen</span><span class="sxs-lookup"><span data-stu-id="49f40-192">Primary and secondary actions</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/adaptive-cards/actions-do.png" alt-text="Bewährte Methode: Eine adaptive Karte sollte nur eine kleine Gruppe von Aktionen enthalten." border="false":::

#### <a name="do-use-up-to-six-primary-actions"></a><span data-ttu-id="49f40-194">Was Sie tun sollten: bis zu sechs primäre Aktionen verwenden</span><span class="sxs-lookup"><span data-stu-id="49f40-194">Do: Use up to six primary actions</span></span>

<span data-ttu-id="49f40-195">Adaptive Karten unterstützen zwar bis zu sechs primäre Aktionen, auf den meisten Karten werden diese jedoch nicht benötigt.</span><span class="sxs-lookup"><span data-stu-id="49f40-195">While Adaptive Cards can support six primary actions, most cards don’t need that.</span></span> <span data-ttu-id="49f40-196">Aktionen sollten klar, präzise und unkompliziert sein.</span><span class="sxs-lookup"><span data-stu-id="49f40-196">Actions should be clear, concise, and straight forward.</span></span> <span data-ttu-id="49f40-197">Weniger ist mehr.</span><span class="sxs-lookup"><span data-stu-id="49f40-197">Less is more.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/adaptive-cards/actions-dont.png" alt-text="Bewährte Methode: Benutzer sollten nicht mit zu vielen Aktionen auf einer adaptiven Karte überfordert werden." border="false":::

#### <a name="dont-use-more-than-six-primary-actions"></a><span data-ttu-id="49f40-199">Was Sie nicht tun sollten: mehr als sechs primäre Aktionen verwenden</span><span class="sxs-lookup"><span data-stu-id="49f40-199">Don't: Use more than six primary actions</span></span>

<span data-ttu-id="49f40-200">Adaptive Karten sollten schnelle, handlungsrelevante Inhalte präsentieren.</span><span class="sxs-lookup"><span data-stu-id="49f40-200">Adaptive Cards should present quick, actionable content.</span></span> <span data-ttu-id="49f40-201">Zu viele Aktionen können einen Benutzer überfordern.</span><span class="sxs-lookup"><span data-stu-id="49f40-201">Too many actions can overwhelm a user.</span></span>

   :::column-end:::
:::row-end:::

### <a name="frequency"></a><span data-ttu-id="49f40-202">Häufigkeit</span><span class="sxs-lookup"><span data-stu-id="49f40-202">Frequency</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/frequency-do.png" alt-text="Bewährte Methode bezüglich der Häufigkeit adaptiver Karten." border="false":::

#### <a name="do-be-concise"></a><span data-ttu-id="49f40-204">Was Sie tun sollten: Präzise sein</span><span class="sxs-lookup"><span data-stu-id="49f40-204">Do: Be concise</span></span>

<span data-ttu-id="49f40-205">Es ist einfach, mehrere Karten in eine Unterhaltung zu senden, aber sobald Karten aus der Ansicht scrollen, werden sie weniger nützlich.</span><span class="sxs-lookup"><span data-stu-id="49f40-205">It's easy to send multiple cards into a conversation, but once cards scroll out of view, they become less useful.</span></span> <span data-ttu-id="49f40-206">Versuchen Sie, sich auf das Wesentliche zu beschränken.</span><span class="sxs-lookup"><span data-stu-id="49f40-206">Try to limit yourself to the essentials.</span></span> <span data-ttu-id="49f40-207">Dies gilt insbesondere in einem Kanal, in dem Benutzer weniger Toleranz für das haben, was sie als „Rauschen“ wahrnehmen.</span><span class="sxs-lookup"><span data-stu-id="49f40-207">This is especially true in a channel where users have less tolerance for what they perceive as "noise".</span></span>
