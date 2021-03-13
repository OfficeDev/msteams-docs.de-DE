---
title: Entfernen von Registerkartenrändern in Microsoft Teams
author: laujan
description: Beschreibt, wie das Entfernen von Registerkartenrändern die Erfahrung von Entwicklern verbessert.
keywords: Tabulatoren entfernen Ränderabstand
ms.topic: reference
ms.author: lomeybur
ms.openlocfilehash: 57e6b15999ffc41c0a3e09897ba565f9b3bf3705
ms.sourcegitcommit: 23ed7edf145df10dcfba15c43978eae9e0d451a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2021
ms.locfileid: "50753518"
---
# <a name="tab-margin-changes"></a><span data-ttu-id="babc8-104">Änderungen am Registerkartenrand</span><span class="sxs-lookup"><span data-stu-id="babc8-104">Tab margin changes</span></span>

<span data-ttu-id="babc8-105">In diesem Dokument wird beschrieben, wie das Entfernen von Rändern um alle Registerkarten in Microsoft Teams die Erfahrung des Entwicklers beim Erstellen von Apps verbessert.</span><span class="sxs-lookup"><span data-stu-id="babc8-105">This document describes how the removal of margins around all tabs in Microsoft Teams will enhance the developer's experience when building apps.</span></span> <span data-ttu-id="babc8-106">Dies ist eine Verbesserung, die in Microsoft Teams in 2021 eingeführt wurde.</span><span class="sxs-lookup"><span data-stu-id="babc8-106">This is an enhancement introduced in Microsoft Teams in 2021.</span></span>
<span data-ttu-id="babc8-107">Wenn Sie die Ränder um alle Registerkarten entfernen, können Entwickler Apps erstellen, die für Teams systemeigener aussehen.</span><span class="sxs-lookup"><span data-stu-id="babc8-107">Removing the margins around all tabs will allow developers to build apps that look more native to Teams.</span></span> <span data-ttu-id="babc8-108">Dies entspricht auch unseren [Ui Kit-Designs.](~/tabs/design/tabs.md)</span><span class="sxs-lookup"><span data-stu-id="babc8-108">This will also align with our [UI kit designs](~/tabs/design/tabs.md).</span></span> <span data-ttu-id="babc8-109">Die meisten Apps sehen ohne die Ränder, die ihre Erfahrungen umgeben, bereits besser aus.</span><span class="sxs-lookup"><span data-stu-id="babc8-109">Most apps already look better without the margins surrounding their experiences.</span></span> <span data-ttu-id="babc8-110">Einige Registerkarten sind jedoch visuell von dieser Änderung betroffen, und Entwickler müssen die erforderlichen Änderungen vornehmen.</span><span class="sxs-lookup"><span data-stu-id="babc8-110">However, some tabs are visually affected by this change, and developers must make the necessary changes.</span></span>

:::image type="content" source="../assets/images/tabs/remove-margins-tabs.png" alt-text="Tabstopp-Witz und ohne Ränder" border="false":::

## <a name="timelines"></a><span data-ttu-id="babc8-112">Zeitpläne</span><span class="sxs-lookup"><span data-stu-id="babc8-112">Timelines</span></span>

* <span data-ttu-id="babc8-113">5. März 2021 – Ränder in [Public Developer Preview](~/resources/dev-preview/developer-preview-intro.md).</span><span class="sxs-lookup"><span data-stu-id="babc8-113">March 5, 2021 - Margins removed in [Public Developer Preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>
* <span data-ttu-id="babc8-114">1. Mai 2021 – Ränder werden in der Produktion entfernt.</span><span class="sxs-lookup"><span data-stu-id="babc8-114">May 1, 2021 - Margins will be removed in production.</span></span>

## <a name="guidelines"></a><span data-ttu-id="babc8-115">Anleitungen</span><span class="sxs-lookup"><span data-stu-id="babc8-115">Guidelines</span></span>

<span data-ttu-id="babc8-116">Microsoft Teams-Apps, die Registerkarten verwenden, sind von dieser Änderung betroffen.</span><span class="sxs-lookup"><span data-stu-id="babc8-116">Microsoft Teams apps that use tabs will be affected by this change.</span></span> <span data-ttu-id="babc8-117">Entwickler müssen zu [Public Developer Preview](~/resources/dev-preview/developer-preview-intro.md) wechseln, um zu bestimmen, wie ihre Registerkarten betroffen sind, und die erforderlichen Änderungen vornehmen.</span><span class="sxs-lookup"><span data-stu-id="babc8-117">Developers must switch to [Public Developer Preview](~/resources/dev-preview/developer-preview-intro.md) in order to determine how their tabs are affected and make the necessary changes.</span></span>

<span data-ttu-id="babc8-118">Registerkartenentwickler dürfen sich nicht darauf verlassen, dass Teams Ränder für ihre Registerkarten zur Verfügung stellt.</span><span class="sxs-lookup"><span data-stu-id="babc8-118">Tab developers must not rely on Teams to provide margins surrounding their tabs.</span></span> <span data-ttu-id="babc8-119">Entwickler werden ermutigt, Ränder um ihre Registerkartendesigns hinzuzufügen, wo dies erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="babc8-119">Developers are encouraged to add margins around their tab designs where it is required.</span></span> <span data-ttu-id="babc8-120">App-Designs in der Produktion können wie zusätzliche Abstände aussehen, d. h. Ränder, die von Teams bereitgestellt werden, und Ränder, die von der Registerkarte bereitgestellt werden. Der zusätzliche Abstand ist jedoch nur temporär und wird in ein paar Wochen weg sein, und nur der von der App bereitgestellte Abstand bleibt erhalten.</span><span class="sxs-lookup"><span data-stu-id="babc8-120">App designs in production can look like there is extra padding, that is, margins provided by Teams and margins provided by the tab. However, the extra padding is only temporary and will go away in a few weeks, leaving only the app's provided padding.</span></span>

## <a name="faq"></a><span data-ttu-id="babc8-121">Häufig gestellte Fragen</span><span class="sxs-lookup"><span data-stu-id="babc8-121">FAQ</span></span>

<span data-ttu-id="babc8-122">**Ist es für App Chrome, z. B. Kopf- oder Taskleiste, in Ordnung, die Ränder unserer Designs zu berühren?**</span><span class="sxs-lookup"><span data-stu-id="babc8-122">**Is it OK for app chrome, such as header bar or taskbar, to touch the edges of our designs?**</span></span>

<span data-ttu-id="babc8-123">Ja, dies ist in Ordnung und wird ermutigt.</span><span class="sxs-lookup"><span data-stu-id="babc8-123">Yes, this is fine and encouraged.</span></span> <span data-ttu-id="babc8-124">Dies hilft der App, sich systemeigener zu fühlen.</span><span class="sxs-lookup"><span data-stu-id="babc8-124">This helps the app feel native.</span></span>

<span data-ttu-id="babc8-125">**Ist es für App-Inhalte wie Text, Logos und Bilder in Ordnung, den linken und rechten Rand unserer Designs zu berühren?**</span><span class="sxs-lookup"><span data-stu-id="babc8-125">**Is it OK for app content, such as text, logos, and images, to touch the left and right edges of our designs?**</span></span>

<span data-ttu-id="babc8-126">Nein, Sie müssen links und rechts von allen App-Inhalten einen eigenen Abstand oder Ränder bereitstellen, um sicherzustellen, dass die Ränder der Benutzeroberfläche nicht berührt werden.</span><span class="sxs-lookup"><span data-stu-id="babc8-126">No, you must provide your own padding or margins to the left and right of all app content to ensure it does not touch the edges of your UI.</span></span> <span data-ttu-id="babc8-127">Sie können bei Bedarf auch Ränder oben auf Ihrer Registerkarte hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="babc8-127">You can also add margins at the top of your tab, if required.</span></span>

<span data-ttu-id="babc8-128">**Wie groß sind die Ränder, die Teams zuvor angewendet hat?**</span><span class="sxs-lookup"><span data-stu-id="babc8-128">**What's the size of the margins Teams previously applied?**</span></span>

* <span data-ttu-id="babc8-129">Links und rechts: 20px</span><span class="sxs-lookup"><span data-stu-id="babc8-129">Left and right: 20px</span></span>
* <span data-ttu-id="babc8-130">Top: 16px</span><span class="sxs-lookup"><span data-stu-id="babc8-130">Top: 16px</span></span>
* <span data-ttu-id="babc8-131">Unten: 0px</span><span class="sxs-lookup"><span data-stu-id="babc8-131">Bottom: 0px</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="babc8-132">Alle Registerkarten haben ihre Ränder entfernt: persönliche Registerkarten, (Gruppen-) Chatregisterkarten, Besprechungsregisterkarten und Kanalregisterkarten.</span><span class="sxs-lookup"><span data-stu-id="babc8-132">All tabs have their margins removed: personal tabs, (group) chat tabs, meeting tabs, and channel tabs.</span></span>
> * <span data-ttu-id="babc8-133">Es gibt keine Möglichkeit, sich für diese Änderung zu entscheiden oder abmelden.</span><span class="sxs-lookup"><span data-stu-id="babc8-133">There is no way to opt-in or opt-out of this change.</span></span> <span data-ttu-id="babc8-134">Sie gilt für alle Registerkarten.</span><span class="sxs-lookup"><span data-stu-id="babc8-134">It will apply to all tabs.</span></span>
> * <span data-ttu-id="babc8-135">Diese Änderung kann sich auf Registerkarten auswirken, die auf Microsoft Teams angewiesen sind, um Ränder für die Benutzeroberfläche zur Verfügung zu stellen.</span><span class="sxs-lookup"><span data-stu-id="babc8-135">This change can affect tabs that rely on Microsoft Teams to provide margins surrounding their UI.</span></span>
