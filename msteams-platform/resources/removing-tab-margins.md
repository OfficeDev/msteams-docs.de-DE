---
title: Entfernen von Registerkartenrändern in Microsoft Teams
author: laujan
description: Beschreibt, wie das Entfernen von Registerkartenrändern die Erfahrung von Entwicklern verbessert.
keywords: Tabulatoren entfernen Ränderabstand
ms.topic: reference
localization_priority: Normal
ms.author: lomeybur
ms.openlocfilehash: 78d97dca73e7fce2bf4b911f5ea4588525667378
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019713"
---
# <a name="tab-margin-changes"></a><span data-ttu-id="5c8a2-104">Änderungen am Registerkartenrand</span><span class="sxs-lookup"><span data-stu-id="5c8a2-104">Tab margin changes</span></span>

<span data-ttu-id="5c8a2-105">In diesem Dokument wird beschrieben, wie das Entfernen von Rändern um alle Registerkarten in Microsoft Teams die Erfahrung des Entwicklers beim Erstellen von Apps verbessert.</span><span class="sxs-lookup"><span data-stu-id="5c8a2-105">This document describes how the removal of margins around all tabs in Microsoft Teams will enhance the developer's experience when building apps.</span></span> <span data-ttu-id="5c8a2-106">Dies ist eine Verbesserung, die in Microsoft Teams 2021 eingeführt wurde.</span><span class="sxs-lookup"><span data-stu-id="5c8a2-106">This is an enhancement introduced in Microsoft Teams in 2021.</span></span>
<span data-ttu-id="5c8a2-107">Wenn Sie die Ränder um alle Registerkarten entfernen, können Entwickler Apps erstellen, die nativ für Teams.</span><span class="sxs-lookup"><span data-stu-id="5c8a2-107">Removing the margins around all tabs will allow developers to build apps that look more native to Teams.</span></span> <span data-ttu-id="5c8a2-108">Dies entspricht auch unseren [Ui Kit-Designs.](~/tabs/design/tabs.md)</span><span class="sxs-lookup"><span data-stu-id="5c8a2-108">This will also align with our [UI kit designs](~/tabs/design/tabs.md).</span></span> <span data-ttu-id="5c8a2-109">Die meisten Apps sehen ohne die Ränder, die ihre Erfahrungen umgeben, bereits besser aus.</span><span class="sxs-lookup"><span data-stu-id="5c8a2-109">Most apps already look better without the margins surrounding their experiences.</span></span> <span data-ttu-id="5c8a2-110">Einige Registerkarten sind jedoch visuell von dieser Änderung betroffen, und Entwickler müssen die erforderlichen Änderungen vornehmen.</span><span class="sxs-lookup"><span data-stu-id="5c8a2-110">However, some tabs are visually affected by this change, and developers must make the necessary changes.</span></span>

:::image type="content" source="../assets/images/tabs/remove-margins-tabs.png" alt-text="Tabstopp-Witz und ohne Ränder" border="false":::

> [!NOTE]
> <span data-ttu-id="5c8a2-112">Dieses Feature gilt nicht für mobile Clients, da die in den mobilen Clients angezeigten Registerkarten keine Ränder haben.</span><span class="sxs-lookup"><span data-stu-id="5c8a2-112">This feature is not applicable to mobile clients, as the tabs viewed in the mobile clients do not have margins.</span></span> 

## <a name="timelines"></a><span data-ttu-id="5c8a2-113">Zeitpläne</span><span class="sxs-lookup"><span data-stu-id="5c8a2-113">Timelines</span></span>

* <span data-ttu-id="5c8a2-114">5. März 2021 – Ränder in [Public Developer Preview](~/resources/dev-preview/developer-preview-intro.md).</span><span class="sxs-lookup"><span data-stu-id="5c8a2-114">March 5, 2021 - Margins removed in [Public Developer Preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>
* <span data-ttu-id="5c8a2-115">15. Juni 2021 – Ränder werden in der Produktion entfernt.</span><span class="sxs-lookup"><span data-stu-id="5c8a2-115">June 15, 2021 - Margins will be removed in production.</span></span>

## <a name="guidelines"></a><span data-ttu-id="5c8a2-116">Richtlinien</span><span class="sxs-lookup"><span data-stu-id="5c8a2-116">Guidelines</span></span>

<span data-ttu-id="5c8a2-117">Microsoft Teams Apps, die Registerkarten verwenden, sind von dieser Änderung betroffen.</span><span class="sxs-lookup"><span data-stu-id="5c8a2-117">Microsoft Teams apps that use tabs will be affected by this change.</span></span> <span data-ttu-id="5c8a2-118">Entwickler müssen zu [Public Developer Preview](~/resources/dev-preview/developer-preview-intro.md) wechseln, um zu bestimmen, wie ihre Registerkarten betroffen sind, und die erforderlichen Änderungen vornehmen.</span><span class="sxs-lookup"><span data-stu-id="5c8a2-118">Developers must switch to [Public Developer Preview](~/resources/dev-preview/developer-preview-intro.md) in order to determine how their tabs are affected and make the necessary changes.</span></span>

<span data-ttu-id="5c8a2-119">Registerkartenentwickler dürfen sich nicht auf Teams verlassen, um Ränder für ihre Registerkarten zur Verfügung zu stellen.</span><span class="sxs-lookup"><span data-stu-id="5c8a2-119">Tab developers must not rely on Teams to provide margins surrounding their tabs.</span></span> <span data-ttu-id="5c8a2-120">Entwickler werden ermutigt, Ränder um ihre Registerkartendesigns hinzuzufügen, wo dies erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="5c8a2-120">Developers are encouraged to add margins around their tab designs where it is required.</span></span> <span data-ttu-id="5c8a2-121">App-Designs in der Produktion können so aussehen, als ob zusätzliche Abstände vorhanden sind, d. h. Ränder, die von Teams und Rändern bereitgestellt werden, die von der Registerkarte bereitgestellt werden. Der zusätzliche Abstand ist jedoch nur temporär und wird in ein paar Wochen weg sein, und nur der von der App bereitgestellte Abstand bleibt erhalten.</span><span class="sxs-lookup"><span data-stu-id="5c8a2-121">App designs in production can look like there is extra padding, that is, margins provided by Teams and margins provided by the tab. However, the extra padding is only temporary and will go away in a few weeks, leaving only the app's provided padding.</span></span>

## <a name="faq"></a><span data-ttu-id="5c8a2-122">Häufig gestellte Fragen</span><span class="sxs-lookup"><span data-stu-id="5c8a2-122">FAQ</span></span>

<span data-ttu-id="5c8a2-123">**Ist es für App Chrome, z. B. Kopf- oder Taskleiste, in Ordnung, die Ränder unserer Designs zu berühren?**</span><span class="sxs-lookup"><span data-stu-id="5c8a2-123">**Is it OK for app chrome, such as header bar or taskbar, to touch the edges of our designs?**</span></span>

<span data-ttu-id="5c8a2-124">Ja, dies ist in Ordnung und wird ermutigt.</span><span class="sxs-lookup"><span data-stu-id="5c8a2-124">Yes, this is fine and encouraged.</span></span> <span data-ttu-id="5c8a2-125">Dies hilft der App, sich systemeigener zu fühlen.</span><span class="sxs-lookup"><span data-stu-id="5c8a2-125">This helps the app feel native.</span></span>

<span data-ttu-id="5c8a2-126">**Ist es für App-Inhalte wie Text, Logos und Bilder in Ordnung, den linken und rechten Rand unserer Designs zu berühren?**</span><span class="sxs-lookup"><span data-stu-id="5c8a2-126">**Is it OK for app content, such as text, logos, and images, to touch the left and right edges of our designs?**</span></span>

<span data-ttu-id="5c8a2-127">Nein, Sie müssen links und rechts von allen App-Inhalten einen eigenen Abstand oder Ränder bereitstellen, um sicherzustellen, dass die Ränder der Benutzeroberfläche nicht berührt werden.</span><span class="sxs-lookup"><span data-stu-id="5c8a2-127">No, you must provide your own padding or margins to the left and right of all app content to ensure it does not touch the edges of your UI.</span></span> <span data-ttu-id="5c8a2-128">Sie können bei Bedarf auch Ränder oben auf Ihrer Registerkarte hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="5c8a2-128">You can also add margins at the top of your tab, if required.</span></span>

<span data-ttu-id="5c8a2-129">**Wie groß sind die Ränder, die Teams angewendet wurden?**</span><span class="sxs-lookup"><span data-stu-id="5c8a2-129">**What's the size of the margins Teams previously applied?**</span></span>

* <span data-ttu-id="5c8a2-130">Links und rechts: 20px</span><span class="sxs-lookup"><span data-stu-id="5c8a2-130">Left and right: 20px</span></span>
* <span data-ttu-id="5c8a2-131">Top: 16px</span><span class="sxs-lookup"><span data-stu-id="5c8a2-131">Top: 16px</span></span>
* <span data-ttu-id="5c8a2-132">Unten: 0px</span><span class="sxs-lookup"><span data-stu-id="5c8a2-132">Bottom: 0px</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="5c8a2-133">Alle Registerkarten haben ihre Ränder entfernt: persönliche Registerkarten, (Gruppen-) Chatregisterkarten, Besprechungsregisterkarten und Kanalregisterkarten.</span><span class="sxs-lookup"><span data-stu-id="5c8a2-133">All tabs have their margins removed: personal tabs, (group) chat tabs, meeting tabs, and channel tabs.</span></span>
> * <span data-ttu-id="5c8a2-134">Es gibt keine Möglichkeit, sich für diese Änderung zu entscheiden oder abmelden.</span><span class="sxs-lookup"><span data-stu-id="5c8a2-134">There is no way to opt-in or opt-out of this change.</span></span> <span data-ttu-id="5c8a2-135">Sie gilt für alle Registerkarten.</span><span class="sxs-lookup"><span data-stu-id="5c8a2-135">It will apply to all tabs.</span></span>
> * <span data-ttu-id="5c8a2-136">Diese Änderung kann sich auf Registerkarten auswirken, die Microsoft Teams, um Ränder für ihre Benutzeroberfläche zur Verfügung zu stellen.</span><span class="sxs-lookup"><span data-stu-id="5c8a2-136">This change can affect tabs that rely on Microsoft Teams to provide margins surrounding their UI.</span></span>
