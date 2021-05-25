---
title: Entwerfen Ihrer App – Verstehen des Entwurfssystems
description: Erfahren Sie mehr über die Grundlagen des Entwerfens Microsoft Teams App, einschließlich Layout, Farbschema und mehr.
author: heath-hamilton
localization_priority: Normal
ms.author: lajanuar
ms.topic: overview
ms.openlocfilehash: 0af2a22200e62be9289f167b0306c9769366e46a
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "52630841"
---
# <a name="microsoft-teams-app-design-system"></a><span data-ttu-id="021bb-103">Microsoft Teams-App-Designsystem</span><span class="sxs-lookup"><span data-stu-id="021bb-103">Microsoft Teams app design system</span></span>

<span data-ttu-id="021bb-104">Erlernen Sie schnell die Grundlagen des App-Designs von Teams.</span><span class="sxs-lookup"><span data-stu-id="021bb-104">Quickly learn about the fundamentals of Teams app design.</span></span> <span data-ttu-id="021bb-105">Umfassende Anleitungen und Beispiele finden Sie im <a href="https://www.figma.com/community/file/916836509871353159" target="_blank">Microsoft Teams UI Kit (Figma).</a></span><span class="sxs-lookup"><span data-stu-id="021bb-105">You can find comprehensive guidance and examples in the <a href="https://www.figma.com/community/file/916836509871353159" target="_blank">Microsoft Teams UI Kit (Figma)</a>.</span></span>

## <a name="layout"></a><span data-ttu-id="021bb-106">Layout</span><span class="sxs-lookup"><span data-stu-id="021bb-106">Layout</span></span>

:::row:::

   :::column span="3":::

      <span data-ttu-id="021bb-107">Teams basiert auf einem Rasterlayout, um konsistente und elegante Beziehungen zwischen Entwurfskomponenten sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="021bb-107">Teams relies on a grid layout to ensure consistent and elegant relationships between design components.</span></span> <span data-ttu-id="021bb-108">Die 4-Pixel-Basiseinheit des Rasters ermöglicht komponenten eine durchgängige Skalierung über alle Anzeigegrößen in Teams.</span><span class="sxs-lookup"><span data-stu-id="021bb-108">The grid’s 4-pixel base unit allows components to scale consistently across all display sizes in Teams.</span></span>

      * [<span data-ttu-id="021bb-109">Siehe vollständige Layoutrichtlinien (Figma)</span><span class="sxs-lookup"><span data-stu-id="021bb-109">See full layout guidelines (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)
      * [<span data-ttu-id="021bb-110">Implementieren des Layouts (Fluent UI)</span><span class="sxs-lookup"><span data-stu-id="021bb-110">Implement layout (Fluent UI)</span></span>](https://developer.microsoft.com/fluentui#/styles/web/layout)

   :::column-end:::
   :::column span="1":::
      :::image type="content" source="../../assets/images/design-guidelines/teams-layout.png" alt-text="Konzeptionelles Bild Teams Layout." border="false":::
   :::column-end:::

:::row-end:::

## <a name="avatars"></a><span data-ttu-id="021bb-112">Avatare</span><span class="sxs-lookup"><span data-stu-id="021bb-112">Avatars</span></span>

:::row:::

   :::column span="3":::

      <span data-ttu-id="021bb-113">Ein Avatar ist eine grafische Darstellung einer Person, eines Teams, bots oder einer Entität in Teams.</span><span class="sxs-lookup"><span data-stu-id="021bb-113">An avatar is a graphical representation of a person, team, bot, or entity in Teams.</span></span> <span data-ttu-id="021bb-114">Eine Avatargruppe wird häufig verwendet, um Liveaktivität zu vermitteln oder eine Liste so zu repräsentieren, dass der vertikale Raum erhalten bleibt.</span><span class="sxs-lookup"><span data-stu-id="021bb-114">An avatar group is often used to convey live activity or a represent a roster in a way that preserves vertical space.</span></span> 

      * <span data-ttu-id="021bb-115"><a href="https://www.figma.com/community/file/916836509871353159" target="_blank">Siehe vollständige Avatarrichtlinien (Figma)</a></span><span class="sxs-lookup"><span data-stu-id="021bb-115"><a href="https://www.figma.com/community/file/916836509871353159" target="_blank">See full avatar guidelines (Figma)</a></span></span>

   :::column-end:::
   :::column span="1":::

      :::image type="content" source="../../assets/images/design-guidelines/teams-avatars.png" alt-text="Konzeptionelles Bild Teams Avatare." border="false":::

   :::column-end:::
:::row-end:::

## <a name="icons"></a><span data-ttu-id="021bb-117">Symbole</span><span class="sxs-lookup"><span data-stu-id="021bb-117">Icons</span></span>

:::row:::

   :::column span="3":::

      <span data-ttu-id="021bb-118">Das primäre Symbol Ihrer App kann bei der Vermittlung Ihrer Marke an die Benutzer Teams werden.</span><span class="sxs-lookup"><span data-stu-id="021bb-118">Your app's primary icon can go a long way in conveying your brand to Teams users.</span></span> <span data-ttu-id="021bb-119">Das Richtige des Symbolentwurfs ist auch für die Veröffentlichung [Ihrer App](../../concepts/build-and-test/apps-package.md) im Teams wichtig.</span><span class="sxs-lookup"><span data-stu-id="021bb-119">Getting your icon design right is also important for [publishing your app](../../concepts/build-and-test/apps-package.md) to the Teams store.</span></span>

      <span data-ttu-id="021bb-120">Sie können auch In-App-Symbole für die Fluent-Benutzeroberfläche verwenden:</span><span class="sxs-lookup"><span data-stu-id="021bb-120">You also can use Fluent UI icons throughout your app:</span></span>

      * <span data-ttu-id="021bb-121"><a href="https://www.figma.com/community/file/836835755999342788" target="_blank">Aktuelles Fluent-Symbolsatz (Figma)</a></span><span class="sxs-lookup"><span data-stu-id="021bb-121"><a href="https://www.figma.com/community/file/836835755999342788" target="_blank">Get the latest Fluent icon set (Figma)</a></span></span>
      * [<span data-ttu-id="021bb-122">Implementieren der Symbole (Fluent UI)</span><span class="sxs-lookup"><span data-stu-id="021bb-122">Implement the icons (Fluent UI)</span></span>](https://developer.microsoft.com/fluentui#/styles/web/icons)

   :::column-end:::
   :::column span="1":::

      :::image type="content" source="../../assets/images/design-guidelines/teams-iconography.png" alt-text="Konzeptionelles Bild Teams Symbolen." border="false":::

   :::column-end:::
:::row-end:::

## <a name="type"></a><span data-ttu-id="021bb-124">Typ</span><span class="sxs-lookup"><span data-stu-id="021bb-124">Type</span></span>

:::row:::

   :::column span="3":::

      <span data-ttu-id="021bb-125">Teams verwendet die Segoe-Benutzeroberfläche für die Typauflauf und unterschiedliche Schriftgrößen und -gewichtungen, um eine Hierarchie zu erstellen und die Lesbarkeit sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="021bb-125">Teams uses Segoe UI for its type ramp and different font sizes and weights to help create hierarchy and ensure readability.</span></span>

      * <span data-ttu-id="021bb-126"><a href="https://www.figma.com/community/file/916836509871353159" target="_blank">Siehe Vollständige Typrichtlinien (Figma)</a></span><span class="sxs-lookup"><span data-stu-id="021bb-126"><a href="https://www.figma.com/community/file/916836509871353159" target="_blank">See full type guidelines (Figma)</a></span></span>
      * [<span data-ttu-id="021bb-127">Implementieren der Typografie (Fluent UI)</span><span class="sxs-lookup"><span data-stu-id="021bb-127">Implement typography (Fluent UI)</span></span>](https://developer.microsoft.com/fluentui#/styles/web/typography)

   :::column-end:::
   :::column span="1":::

      :::image type="content" source="../../assets/images/design-guidelines/teams-typography.png" alt-text="Konzeptionelles Bild Teams Typografie." border="false":::

   :::column-end:::
:::row-end:::

## <a name="colors"></a><span data-ttu-id="021bb-129">Farben</span><span class="sxs-lookup"><span data-stu-id="021bb-129">Colors</span></span>

:::row:::

   :::column span="3":::

      <span data-ttu-id="021bb-130">Teams Web und Desktop unterstützt Standardmäßige Designs (hell), dunkel und mit hohem Kontrast, während Teams Mobile helle und dunkle Designs unterstützt.</span><span class="sxs-lookup"><span data-stu-id="021bb-130">Teams web and desktop supports default (light), dark, and high-contrast themes, while Teams mobile supports light and dark themes.</span></span> <span data-ttu-id="021bb-131">Jedes Design verfügt über ein eigenes Farbschema.</span><span class="sxs-lookup"><span data-stu-id="021bb-131">Each theme has its own color scheme.</span></span>

      * <span data-ttu-id="021bb-132"><a href="https://www.figma.com/community/file/916836509871353159" target="_blank">Vollständige Farbrichtlinien und verfügbare Farbtoken (Figma)</a></span><span class="sxs-lookup"><span data-stu-id="021bb-132"><a href="https://www.figma.com/community/file/916836509871353159" target="_blank">See full color guidelines and available color tokens (Figma)</a></span></span>
      * [<span data-ttu-id="021bb-133">Implementieren von Farben (Fluent UI)</span><span class="sxs-lookup"><span data-stu-id="021bb-133">Implement colors (Fluent UI)</span></span>](https://fluentsite.z22.web.core.windows.net/0.51.7/colors)

   :::column-end:::
   :::column span="1":::
      :::image type="content" source="../../assets/images/design-guidelines/teams-color.png" alt-text="Konzeptbild der Teams Farben." border="false":::
   :::column-end:::

:::row-end:::

## <a name="shape-and-elevation"></a><span data-ttu-id="021bb-135">Form und Höhe</span><span class="sxs-lookup"><span data-stu-id="021bb-135">Shape and elevation</span></span>

:::row:::

   :::column span="3":::

      <span data-ttu-id="021bb-136">Sie können Form und Höhe verwenden, um zusätzliche Hierarchien in Ihrer App zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="021bb-136">You can use shape and elevation to create additional hierarchy in your app.</span></span> 

      * <span data-ttu-id="021bb-137"><a href="https://www.figma.com/community/file/916836509871353159" target="_blank">Siehe Vollständige Richtlinien für Form und Höhe (Figma)</a></span><span class="sxs-lookup"><span data-stu-id="021bb-137"><a href="https://www.figma.com/community/file/916836509871353159" target="_blank">See full shape and elevation guidelines (Figma)</a></span></span>
      * [<span data-ttu-id="021bb-138">Implementieren von Form und Höhe (Fluent UI)</span><span class="sxs-lookup"><span data-stu-id="021bb-138">Implement shape and elevation (Fluent UI)</span></span>](https://developer.microsoft.com/fluentui#/styles/web/elevation)

   :::column-end:::
   :::column span="1":::

      :::image type="content" source="../../assets/images/design-guidelines/shape-and-elevation.png" alt-text="Konzeptuell von Form und Höhe." border="false":::

   :::column-end:::
:::row-end:::

## <a name="copy-and-content"></a><span data-ttu-id="021bb-140">Kopieren und Inhalt</span><span class="sxs-lookup"><span data-stu-id="021bb-140">Copy and content</span></span>

:::row:::

   :::column span="3":::

      <span data-ttu-id="021bb-141">Um teil der Teams zu sein, sollte Ihre [](/style-guide/brand-voice-above-all-simple-human)App-Kopie im Allgemeinen die folgenden Microsoft-Sprachprinzipien befolgen: warm und entspannt, knackig und klar und bereit, Hand zu geben.</span><span class="sxs-lookup"><span data-stu-id="021bb-141">To feel part of Teams, your app copy in general should follow these [Microsoft voice principles](/style-guide/brand-voice-above-all-simple-human): warm and relaxed, crisp and clear, and ready to lend hand.</span></span>

      * <span data-ttu-id="021bb-142"><a href="https://www.figma.com/community/file/916836509871353159" target="_blank">Vollständige Kopier- und Inhaltsrichtlinien anzeigen– einschließlich schreiben für Bots (Figma)</a></span><span class="sxs-lookup"><span data-stu-id="021bb-142"><a href="https://www.figma.com/community/file/916836509871353159" target="_blank">See full copy and content guidelines—including writing for bots (Figma)</a></span></span>

   :::column-end:::
   :::column span="1":::

      :::image type="content" source="../../assets/images/design-guidelines/teams-copy-and-content.png" alt-text="Konzeptionelles Bild von Kopie und Inhalt." border="false":::

   :::column-end:::
:::row-end:::
