---
title: Entfernen von Registerkartenrändern in Microsoft Teams
author: surbhigupta
description: Beschreibt, wie das Entfernen von Registerkartenrändern die Erfahrung von Entwicklern verbessert.
keywords: Registerkarte zum Entfernen des Abstands von Rändern
ms.topic: reference
localization_priority: Normal
ms.author: lomeybur
ms.openlocfilehash: b4b3fbbe7ed2e8356fcc9c49346d423707a6a264
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069168"
---
# <a name="tab-margin-changes"></a><span data-ttu-id="6ba17-104">Änderungen am Registerkartenrand</span><span class="sxs-lookup"><span data-stu-id="6ba17-104">Tab margin changes</span></span>

<span data-ttu-id="6ba17-105">In diesem Dokument wird beschrieben, wie das Entfernen von Rändern um alle Registerkarten in Microsoft Teams die Erfahrung des Entwicklers beim Erstellen von Apps verbessert.</span><span class="sxs-lookup"><span data-stu-id="6ba17-105">This document describes how the removal of margins around all tabs in Microsoft Teams will enhance the developer's experience when building apps.</span></span> <span data-ttu-id="6ba17-106">Dies ist eine Erweiterung, die in Microsoft Teams 2021 eingeführt wurde.</span><span class="sxs-lookup"><span data-stu-id="6ba17-106">This is an enhancement introduced in Microsoft Teams in 2021.</span></span>
<span data-ttu-id="6ba17-107">Wenn Sie die Ränder um alle Registerkarten entfernen, können Entwickler Apps erstellen, die systemeigener für Teams aussehen.</span><span class="sxs-lookup"><span data-stu-id="6ba17-107">Removing the margins around all tabs will allow developers to build apps that look more native to Teams.</span></span> <span data-ttu-id="6ba17-108">Dies entspricht auch unseren [Ui-Kit-Designs.](~/tabs/design/tabs.md)</span><span class="sxs-lookup"><span data-stu-id="6ba17-108">This will also align with our [UI kit designs](~/tabs/design/tabs.md).</span></span> <span data-ttu-id="6ba17-109">Die meisten Apps sehen bereits besser aus, ohne dass die Ränder ihrer Umgebungen vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="6ba17-109">Most apps already look better without the margins surrounding their experiences.</span></span> <span data-ttu-id="6ba17-110">Einige Registerkarten sind jedoch visuell von dieser Änderung betroffen, und Entwickler müssen die erforderlichen Änderungen vornehmen.</span><span class="sxs-lookup"><span data-stu-id="6ba17-110">However, some tabs are visually affected by this change, and developers must make the necessary changes.</span></span>

:::image type="content" source="../assets/images/tabs/remove-margins-tabs.png" alt-text="Tabstopp und ohne Ränder" border="false":::

> [!NOTE]
> <span data-ttu-id="6ba17-112">Dieses Feature gilt nicht für mobile Clients, da die in den mobilen Clients angezeigten Registerkarten keine Ränder aufweisen.</span><span class="sxs-lookup"><span data-stu-id="6ba17-112">This feature is not applicable to mobile clients, as the tabs viewed in the mobile clients do not have margins.</span></span> 

## <a name="timelines"></a><span data-ttu-id="6ba17-113">Zeitpläne</span><span class="sxs-lookup"><span data-stu-id="6ba17-113">Timelines</span></span>

* <span data-ttu-id="6ba17-114">5. März 2021 – In [public Developer Preview](~/resources/dev-preview/developer-preview-intro.md)entfernte Ränder.</span><span class="sxs-lookup"><span data-stu-id="6ba17-114">March 5, 2021 - Margins removed in [Public Developer Preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>
* <span data-ttu-id="6ba17-115">15. Juni 2021 – Ränder werden in der Produktion entfernt.</span><span class="sxs-lookup"><span data-stu-id="6ba17-115">June 15, 2021 - Margins will be removed in production.</span></span>

## <a name="guidelines"></a><span data-ttu-id="6ba17-116">Anleitungen</span><span class="sxs-lookup"><span data-stu-id="6ba17-116">Guidelines</span></span>

<span data-ttu-id="6ba17-117">Microsoft Teams Apps, die Registerkarten verwenden, sind von dieser Änderung betroffen.</span><span class="sxs-lookup"><span data-stu-id="6ba17-117">Microsoft Teams apps that use tabs will be affected by this change.</span></span> <span data-ttu-id="6ba17-118">Entwickler müssen zur [Öffentlichen Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md) wechseln, um zu bestimmen, wie ihre Registerkarten betroffen sind, und die erforderlichen Änderungen vornehmen.</span><span class="sxs-lookup"><span data-stu-id="6ba17-118">Developers must switch to [Public Developer Preview](~/resources/dev-preview/developer-preview-intro.md) in order to determine how their tabs are affected and make the necessary changes.</span></span>

<span data-ttu-id="6ba17-119">Registerkartenentwickler dürfen sich nicht auf Teams verlassen, um Ränder um ihre Registerkarten herum bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="6ba17-119">Tab developers must not rely on Teams to provide margins surrounding their tabs.</span></span> <span data-ttu-id="6ba17-120">Entwickler sollten Ränder um ihre Registerkartendesigns herum hinzufügen, wo dies erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="6ba17-120">Developers are encouraged to add margins around their tab designs where it is required.</span></span> <span data-ttu-id="6ba17-121">App-Designs in der Produktion können so aussehen, als ob zusätzliche Abstände vorhanden sind, d. h. Ränder, die von Teams bereitgestellt werden, und Ränder, die von der Registerkarte bereitgestellt werden. Der zusätzliche Abstand ist jedoch nur temporär und wird in ein paar Wochen entfernt, sodass nur der von der App bereitgestellte Abstand übrig bleibt.</span><span class="sxs-lookup"><span data-stu-id="6ba17-121">App designs in production can look like there is extra padding, that is, margins provided by Teams and margins provided by the tab. However, the extra padding is only temporary and will go away in a few weeks, leaving only the app's provided padding.</span></span>

## <a name="faq"></a><span data-ttu-id="6ba17-122">Häufig gestellte Fragen (FAQ)</span><span class="sxs-lookup"><span data-stu-id="6ba17-122">FAQ</span></span>

<span data-ttu-id="6ba17-123">**Ist es für App-Chrome, z. B. Kopfzeile oder Taskleiste, in Ordnung, die Ränder unserer Designs zu berühren?**</span><span class="sxs-lookup"><span data-stu-id="6ba17-123">**Is it OK for app chrome, such as header bar or taskbar, to touch the edges of our designs?**</span></span>

<span data-ttu-id="6ba17-124">Ja, dies ist in Ordnung und wird unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6ba17-124">Yes, this is fine and encouraged.</span></span> <span data-ttu-id="6ba17-125">Dies hilft der App, sich systemintern anfühlen zu können.</span><span class="sxs-lookup"><span data-stu-id="6ba17-125">This helps the app feel native.</span></span>

<span data-ttu-id="6ba17-126">**Ist es für App-Inhalte wie Text, Logos und Bilder in Ordnung, die linken und rechten Ränder unserer Designs zu berühren?**</span><span class="sxs-lookup"><span data-stu-id="6ba17-126">**Is it OK for app content, such as text, logos, and images, to touch the left and right edges of our designs?**</span></span>

<span data-ttu-id="6ba17-127">Nein, Sie müssen ihren eigenen Abstand oder Ränder links und rechts von allen App-Inhalten bereitstellen, um sicherzustellen, dass sie nicht die Ränder Der Benutzeroberfläche berühren.</span><span class="sxs-lookup"><span data-stu-id="6ba17-127">No, you must provide your own padding or margins to the left and right of all app content to ensure it does not touch the edges of your UI.</span></span> <span data-ttu-id="6ba17-128">Sie können bei Bedarf auch Ränder oben auf der Registerkarte hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="6ba17-128">You can also add margins at the top of your tab, if required.</span></span>

<span data-ttu-id="6ba17-129">**Wie groß sind die Ränder, die zuvor angewendet Teams?**</span><span class="sxs-lookup"><span data-stu-id="6ba17-129">**What's the size of the margins Teams previously applied?**</span></span>

* <span data-ttu-id="6ba17-130">Links und rechts: 20 Pixel</span><span class="sxs-lookup"><span data-stu-id="6ba17-130">Left and right: 20px</span></span>
* <span data-ttu-id="6ba17-131">Top: 16px</span><span class="sxs-lookup"><span data-stu-id="6ba17-131">Top: 16px</span></span>
* <span data-ttu-id="6ba17-132">Unten: 0px</span><span class="sxs-lookup"><span data-stu-id="6ba17-132">Bottom: 0px</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="6ba17-133">Alle Registerkarten haben ihre Ränder entfernt: persönliche Registerkarten, (Gruppen-)Chat-Registerkarten, Besprechungsregisterkarten und Kanalregisterkarten.</span><span class="sxs-lookup"><span data-stu-id="6ba17-133">All tabs have their margins removed: personal tabs, (group) chat tabs, meeting tabs, and channel tabs.</span></span>
> * <span data-ttu-id="6ba17-134">Es gibt keine Möglichkeit, diese Änderung abzumelden oder abzuwählen.</span><span class="sxs-lookup"><span data-stu-id="6ba17-134">There is no way to opt-in or opt-out of this change.</span></span> <span data-ttu-id="6ba17-135">Sie gilt für alle Registerkarten.</span><span class="sxs-lookup"><span data-stu-id="6ba17-135">It will apply to all tabs.</span></span>
> * <span data-ttu-id="6ba17-136">Diese Änderung kann sich auf Registerkarten auswirken, die auf Microsoft Teams angewiesen sind, um Ränder zu ihrer Benutzeroberfläche bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="6ba17-136">This change can affect tabs that rely on Microsoft Teams to provide margins surrounding their UI.</span></span>
