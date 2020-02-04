---
title: Referenz zu Entwurfsrichtlinien
description: Beschreibt die Richtlinien für die Verwendung von Feldern und Flyouts in ihren apps.
keywords: Teams-Entwurfsrichtlinien Referenzkomponenten Felder und Flyouts
ms.openlocfilehash: 0f62d38bf961ae79b05c599638cefb3c76f46ed4
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674511"
---
# <a name="fields-and-flyouts"></a><span data-ttu-id="4509c-104">Felder und Flyouts</span><span class="sxs-lookup"><span data-stu-id="4509c-104">Fields and flyouts</span></span>

---

## <a name="fields"></a><span data-ttu-id="4509c-105">Felder</span><span class="sxs-lookup"><span data-stu-id="4509c-105">Fields</span></span>

<span data-ttu-id="4509c-106">Felder sind Bereiche, in denen Benutzer Text eingeben können.</span><span class="sxs-lookup"><span data-stu-id="4509c-106">Fields are areas where users can input text.</span></span>

### <a name="padding-and-size"></a><span data-ttu-id="4509c-107">Textabstand und Größe</span><span class="sxs-lookup"><span data-stu-id="4509c-107">Padding and size</span></span>

<span data-ttu-id="4509c-108">Einzeilige Textfelder sind eine feste Höhe von Bund, die der Höhe anderer Komponenten entspricht.</span><span class="sxs-lookup"><span data-stu-id="4509c-108">Single-line text fields are a fixed height of 32px to match the height of other components.</span></span> <span data-ttu-id="4509c-109">Einige Textfelder wie Beschreibungsfelder sind möglicherweise vertikal höher, sodass mehr Text zulässig ist.</span><span class="sxs-lookup"><span data-stu-id="4509c-109">Some text fields such as description fields may be taller vertically to allow more text.</span></span>
[!include[Padding and size](~/includes/design/fields-image-padding.html)]

### <a name="states"></a><span data-ttu-id="4509c-110">Staaten</span><span class="sxs-lookup"><span data-stu-id="4509c-110">States</span></span>

<span data-ttu-id="4509c-111">Dies sind die Zustände unserer Textfelder.</span><span class="sxs-lookup"><span data-stu-id="4509c-111">These are the states of our text fields.</span></span> <span data-ttu-id="4509c-112">Text Felder sind in unterschiedlichen Zuständen vorhanden.</span><span class="sxs-lookup"><span data-stu-id="4509c-112">Text fields exist in different states.</span></span> <span data-ttu-id="4509c-113">Wir haben spezielle Designs für neun mögliche Szenarien, einschließlich (von oben nach unten): resting-Textfeld, Tastatur im Fokus und Cursor innerhalb des Felds, Tastatur im Fokus mit eingegebenem Text, Fehlerbehandlung erfolgreich, Fehlerbehandlung ist fehlgeschlagen, Klartext Feld (einschließlich eines X-Symbols), Suchfeld (einschließlich eines suchsymbols), eines Lade Felds und eines deaktivierten Felds.</span><span class="sxs-lookup"><span data-stu-id="4509c-113">We have specific designs dedicated to nine possible scenarios, including (top to bottom): Resting text field, Keyboard in focus and cursor inside the field, Keyboard in focus with text entered, Error handling has succeeded, Error handling has failed, Clear text field (including an X icon), Search field (including a Search icon), Loading field, and a Disabled field.</span></span>
[!include[Field states](~/includes/design/fields-image-states.html)]

### <a name="formatting-help-text-and-labels"></a><span data-ttu-id="4509c-114">Formatieren von Hilfe Text und Beschriftungen</span><span class="sxs-lookup"><span data-stu-id="4509c-114">Formatting help text and labels</span></span>

<span data-ttu-id="4509c-115">Felder können Platzhaltertext enthalten, um ein Beispiel für die Art der erforderlichen Informationen anzugeben.</span><span class="sxs-lookup"><span data-stu-id="4509c-115">Fields can contain placeholder text to give an example of the kind of information that is required.</span></span> <span data-ttu-id="4509c-116">Sie können auch Bezeichnungen enthalten, die dem Benutzer mehr Kontext geben.</span><span class="sxs-lookup"><span data-stu-id="4509c-116">They can also hold labels that give the user more context.</span></span> <span data-ttu-id="4509c-117">Innerhalb eines Felds sollte Ihr Text immer linksbündig ausgerichtet sein.</span><span class="sxs-lookup"><span data-stu-id="4509c-117">Within a field, your text should always be justified left.</span></span> <span data-ttu-id="4509c-118">Wir verwenden auch hier in der Satz Verkleidung.</span><span class="sxs-lookup"><span data-stu-id="4509c-118">We use sentence casing throughout here, as well.</span></span>

<span data-ttu-id="4509c-119">Wir verwenden Segoe UI Regular bei 12 pt (Caption) und $App-Gray-02 für Bezeichnungen.</span><span class="sxs-lookup"><span data-stu-id="4509c-119">We use Segoe UI Regular at 12 pt (caption) and $app-gray-02 for labels.</span></span> <span data-ttu-id="4509c-120">Für Hilfetext verwenden wir Segoe UI Regular bei 14 pt (Base) und $App-Gray-02.</span><span class="sxs-lookup"><span data-stu-id="4509c-120">For help text, we use Segoe UI Regular at 14 pt (base) and $app-gray-02.</span></span>
[!include[Fields typography](~/includes/design/fields-image-typography.html)]

---

## <a name="flyouts"></a><span data-ttu-id="4509c-121">Flyouts</span><span class="sxs-lookup"><span data-stu-id="4509c-121">Flyouts</span></span>

<span data-ttu-id="4509c-122">Flyouts sind leichter als Dialogfelder und können schnell abgewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="4509c-122">Flyouts are more lightweight than dialogs and can be dismissed quickly.</span></span> <span data-ttu-id="4509c-123">Sie können Schaltflächen, Felder und andere Komponenten enthalten.</span><span class="sxs-lookup"><span data-stu-id="4509c-123">They can contain buttons, fields, and other components.</span></span>
[!include[Flyouts](~/includes/design/flyouts-image.html)]

### <a name="sizing-and-padding"></a><span data-ttu-id="4509c-124">Größenanpassung und Auffüllung</span><span class="sxs-lookup"><span data-stu-id="4509c-124">Sizing and padding</span></span>

<span data-ttu-id="4509c-125">Links und rechts neben dem Inhalt wird ein 16px-Abstand empfohlen.</span><span class="sxs-lookup"><span data-stu-id="4509c-125">We recommend a 16px padding to the left and right of the content.</span></span>
[!include[Flyouts size and padding](~/includes/design/flyouts-image-sizepadding.html)]

### <a name="placement"></a><span data-ttu-id="4509c-126">Platzierung</span><span class="sxs-lookup"><span data-stu-id="4509c-126">Placement</span></span>

<span data-ttu-id="4509c-127">Flyouts sind kontextbezogen und sollten oberhalb, unterhalb oder neben dem Element platziert werden, das es ausgelöst hat.</span><span class="sxs-lookup"><span data-stu-id="4509c-127">Flyouts are contextual and should be placed above, below, or beside the element that triggered it.</span></span>

### <a name="scrolling"></a><span data-ttu-id="4509c-128">Scrollen</span><span class="sxs-lookup"><span data-stu-id="4509c-128">Scrolling</span></span>

<span data-ttu-id="4509c-129">Der Header bleibt an der richtigen Stelle, um dem Inhalt, in dem ein Bildlauf durchgeführt wird, Kontext zu geben.</span><span class="sxs-lookup"><span data-stu-id="4509c-129">The header remains in place to give context to the content being scrolled.</span></span>
[!include[Flyouts scrolling](~/includes/design/flyouts-image-scrolling.html)]

## <a name="mobile"></a><span data-ttu-id="4509c-130">Mobil</span><span class="sxs-lookup"><span data-stu-id="4509c-130">Mobile</span></span>

<span data-ttu-id="4509c-131">Felder sind Texteingabefelder, die Eingaben von Benutzern annehmen.</span><span class="sxs-lookup"><span data-stu-id="4509c-131">Fields are text-entry boxes that accept input from users.</span></span> <span data-ttu-id="4509c-132">Flyout-Menüs sind horizontale Popupfenster, die im oberen Bereich angezeigt werden und zum Anzeigen detaillierter Informationen zu einem Element verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="4509c-132">Flyout menus are horizontal pop-up windows that appear from the top pane and can be used to show more detail about an item.</span></span>

### <a name="field-controls"></a><span data-ttu-id="4509c-133">Feldsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="4509c-133">Field Controls</span></span>

[!include[Mobile fields](~/includes/design/fields-mobile-image.html)]

### <a name="flyout-menu-list-controls"></a><span data-ttu-id="4509c-134">Flyout-Menü Listensteuerelemente</span><span class="sxs-lookup"><span data-stu-id="4509c-134">Flyout menu list controls</span></span>

[!include[Mobile flyout menu controls](~/includes/design/flyout-menu-mobile-image.html)]
