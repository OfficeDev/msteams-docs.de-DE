---
title: Packen Ihrer App
description: Erfahren Sie, wie Sie Microsoft Teams App zum Testen, Hochladen und Speichern von Veröffentlichungen packen.
localization_priority: Normal
ms.topic: conceptual
ms.openlocfilehash: 219e2d5341707ed51b7e0a3a8077f93df9eac640
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565214"
---
# <a name="create-a-microsoft-teams-app-package"></a><span data-ttu-id="b8b16-103">Erstellen eines Microsoft Teams-App-Pakets</span><span class="sxs-lookup"><span data-stu-id="b8b16-103">Create a Microsoft Teams app package</span></span>

<span data-ttu-id="b8b16-104">Sie benötigen ein App-Paket, planen jedoch, Ihre app Microsoft Teams verteilen.</span><span class="sxs-lookup"><span data-stu-id="b8b16-104">You need an app package however you plan to distribute your Microsoft Teams app.</span></span> <span data-ttu-id="b8b16-105">Ein gültiges Paket ist eine ZIP-Datei, die Folgendes enthält:</span><span class="sxs-lookup"><span data-stu-id="b8b16-105">A valid package is a ZIP file that contains the following:</span></span>

* <span data-ttu-id="b8b16-106">**App-Manifest:** Beschreibt, wie Ihre App konfiguriert ist, einschließlich ihrer Funktionen, erforderlichen Ressourcen und anderer wichtiger Attribute.</span><span class="sxs-lookup"><span data-stu-id="b8b16-106">**App manifest**: Describes how your app is configured, including its capabilities, required resources, and other important attributes.</span></span>
* <span data-ttu-id="b8b16-107">**App-Symbole:** Jedes Paket erfordert ein Farb- und Gliederungssymbol für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="b8b16-107">**App icons**: Each package requires a color and outline icon for your app.</span></span>

## <a name="app-manifest"></a><span data-ttu-id="b8b16-108">App-Manifest</span><span class="sxs-lookup"><span data-stu-id="b8b16-108">App manifest</span></span>

<span data-ttu-id="b8b16-109">Ihre App-Manifestdatei muss auf der obersten Ebene des Pakets mit dem Namen `manifest.json` sein.</span><span class="sxs-lookup"><span data-stu-id="b8b16-109">Your app manifest file must be at the top level of the package with the name `manifest.json`.</span></span> 

<span data-ttu-id="b8b16-110">Stellen Sie beim Veröffentlichen im Teams sicher, dass das Manifest auf das neueste Schema [verweist.](~/resources/schema/manifest-schema.md)</span><span class="sxs-lookup"><span data-stu-id="b8b16-110">When publishing to the Teams store, make sure your manifest references the latest [schema](~/resources/schema/manifest-schema.md).</span></span>

## <a name="app-icons"></a><span data-ttu-id="b8b16-111">App-Symbole</span><span class="sxs-lookup"><span data-stu-id="b8b16-111">App icons</span></span>

<span data-ttu-id="b8b16-112">Ihr App-Paket muss zwei PNG-Versionen Ihres App-Symbols enthalten: eine Farb- und Gliederungsversion.</span><span class="sxs-lookup"><span data-stu-id="b8b16-112">Your app package must include two PNG versions of your app icon: A color and outline version.</span></span>

> [!Note]
> <span data-ttu-id="b8b16-113">Wenn Ihre App über einen Bot oder eine Messagingerweiterung verfügt, werden Ihre Symbole auch in Ihrer Microsoft Azure Bot Service-Registrierung enthalten.</span><span class="sxs-lookup"><span data-stu-id="b8b16-113">If your app has a bot or messaging extension, your icons also will be included in your Microsoft Azure Bot Service registration.</span></span>

<span data-ttu-id="b8b16-114">Damit Ihre App die Teams bestehen kann, müssen diese Symbole die folgenden Größenanforderungen erfüllen.</span><span class="sxs-lookup"><span data-stu-id="b8b16-114">For your app to pass Teams store review, these icons must meet the following size requirements.</span></span>

### <a name="color-icon"></a><span data-ttu-id="b8b16-115">Farbsymbol</span><span class="sxs-lookup"><span data-stu-id="b8b16-115">Color icon</span></span>

<span data-ttu-id="b8b16-116">Die Farbversion Des Symbols wird in den meisten Teams angezeigt und muss 192 x 192 Pixel groß sein.</span><span class="sxs-lookup"><span data-stu-id="b8b16-116">The color version of your icon displays in most Teams scenarios and must be 192x192 pixels.</span></span> <span data-ttu-id="b8b16-117">Ihr Symbol (96 x 96 Pixel) kann eine beliebige Farbe sein, muss jedoch auf einem einfarbigen oder vollständig transparenten quadratischen Hintergrund stehen.</span><span class="sxs-lookup"><span data-stu-id="b8b16-117">Your icon symbol (96x96 pixels) can be any color, but it must sit on a solid or fully transparent square background.</span></span>

<span data-ttu-id="b8b16-118">Teams Symbol automatisch zu, um ein Quadrat mit abgerundeten Ecken in mehreren Szenarien und eine hexagonale Form in Botszenarien angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b8b16-118">Teams automatically crops your icon to display a square with rounded corners in multiple scenarios and a hexagonal shape in bot scenarios.</span></span> <span data-ttu-id="b8b16-119">Um das Symbol zuschneiden, ohne Details zu verlieren, schließen Sie 48 Pixel Abstand um das Symbol ein.</span><span class="sxs-lookup"><span data-stu-id="b8b16-119">To crop the symbol without losing any detail, include 48 pixels of padding around your symbol.</span></span>

:::image type="content" source="../../assets/images/icons/design-color-icon.png" alt-text="Teams Farbsymbol und Entwurfsanleitung." border="false":::

### <a name="outline-icon"></a><span data-ttu-id="b8b16-121">Gliederungssymbol</span><span class="sxs-lookup"><span data-stu-id="b8b16-121">Outline icon</span></span>

<span data-ttu-id="b8b16-122">Ein Gliederungssymbol wird in zwei Szenarien angezeigt:</span><span class="sxs-lookup"><span data-stu-id="b8b16-122">An outline icon displays in two scenarios:</span></span>

* <span data-ttu-id="b8b16-123">Wenn Ihre App verwendet wird und auf der App-Leiste auf der linken Seite des Teams.</span><span class="sxs-lookup"><span data-stu-id="b8b16-123">When your app is in use and “hoisted” on the app bar on the left side of Teams.</span></span>
* <span data-ttu-id="b8b16-124">Wenn ein Benutzer die Messagingerweiterung Ihrer App anheften.</span><span class="sxs-lookup"><span data-stu-id="b8b16-124">When a user pins your app's messaging extension.</span></span>

<span data-ttu-id="b8b16-125">Das Symbol muss 32 x 32 Pixel groß sein.</span><span class="sxs-lookup"><span data-stu-id="b8b16-125">The icon must be 32x32 pixels.</span></span> <span data-ttu-id="b8b16-126">Es kann weiß mit einem transparenten Hintergrund oder transparent mit weißem Hintergrund sein (keine anderen Farben sind zulässig).</span><span class="sxs-lookup"><span data-stu-id="b8b16-126">It can be white with a transparent background or transparent with a white background (no other colors are permitted).</span></span> <span data-ttu-id="b8b16-127">Das Gliederungssymbol sollte keinen zusätzlichen Abstand um das Symbol haben.</span><span class="sxs-lookup"><span data-stu-id="b8b16-127">The outline icon should not have any extra padding around the symbol.</span></span>

:::image type="content" source="../../assets/images/icons/design-outline-icon.png" alt-text="Teams Gliederungssymbolentwurfsanleitung." border="false":::

### <a name="best-practices"></a><span data-ttu-id="b8b16-129">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="b8b16-129">Best practices</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/icons/design-icon-do.png" alt-text="Abbildung, die zeigt, wie Sie Ihre App-Symbole entwerfen." border="false":::

#### <a name="do-follow-the-precise-outline-icon-guidelines"></a><span data-ttu-id="b8b16-131">Do: Befolgen Sie die Richtlinien für genaue Gliederungssymbole.</span><span class="sxs-lookup"><span data-stu-id="b8b16-131">Do: Follow the precise outline icon guidelines</span></span>

<span data-ttu-id="b8b16-132">Die RGB-Werte von Weiß, die in Ihrem Symbol verwendet werden, müssen Rot sein: 255, Grün: 255, Blau: 255.</span><span class="sxs-lookup"><span data-stu-id="b8b16-132">The RGB values of white used in your icon must be Red: 255, Green: 255, Blue: 255.</span></span> <span data-ttu-id="b8b16-133">Alle anderen Teile des Gliederungssymbols müssen vollständig transparent sein, und der Alphakanal ist auf 0 festgelegt.</span><span class="sxs-lookup"><span data-stu-id="b8b16-133">All other parts of the outline icon must be fully transparent, with the alpha channel set to 0.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/icons/design-icon-dont.png" alt-text="Abbildung, die zeigt, wie Sie Ihre App-Symbole nicht entwerfen." border="false":::

#### <a name="dont-crop-in-a-circular-or-rounded-square-shape"></a><span data-ttu-id="b8b16-135">Don't: Crop in a circular or rounded square shape</span><span class="sxs-lookup"><span data-stu-id="b8b16-135">Don't: Crop in a circular or rounded square shape</span></span>

<span data-ttu-id="b8b16-136">Das in Ihrem App-Paket übermittelte Farbsymbol muss quadratisch sein.</span><span class="sxs-lookup"><span data-stu-id="b8b16-136">The color icon submitted in your app package must be square.</span></span> <span data-ttu-id="b8b16-137">Runden Sie nicht die Ecken Ihres Symbols.</span><span class="sxs-lookup"><span data-stu-id="b8b16-137">Don’t round the corners of your icon.</span></span> <span data-ttu-id="b8b16-138">Teams automatisch den Eckenradius an.</span><span class="sxs-lookup"><span data-stu-id="b8b16-138">Teams automatically adjusts the corner radius.</span></span>

   :::column-end:::
:::row-end:::

#### <a name="dont-copy-other-brands"></a><span data-ttu-id="b8b16-139">Don't: Copy other brands</span><span class="sxs-lookup"><span data-stu-id="b8b16-139">Don't: Copy other brands</span></span>

<span data-ttu-id="b8b16-140">Ihre Symbole dürfen keine urheberrechtlich geschützten Produkte imitieren, die Sie nicht besitzen.</span><span class="sxs-lookup"><span data-stu-id="b8b16-140">Your icons must not mimic any copyrighted products that you don't own.</span></span> <span data-ttu-id="b8b16-141">Beispiel: ein Design, das einem Microsoft-Produkt oder einer Marke ähnelt.</span><span class="sxs-lookup"><span data-stu-id="b8b16-141">For example, a design similar to a Microsoft product or brand.</span></span>

### <a name="examples"></a><span data-ttu-id="b8b16-142">Beispiele</span><span class="sxs-lookup"><span data-stu-id="b8b16-142">Examples</span></span>

<span data-ttu-id="b8b16-143">Hier sehen Sie, wie App-Symbole in verschiedenen Teams und Kontexten angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="b8b16-143">Here's how app icons appear in different Teams capabilities and contexts.</span></span>

#### <a name="personal-app"></a><span data-ttu-id="b8b16-144">Persönliche App</span><span class="sxs-lookup"><span data-stu-id="b8b16-144">Personal app</span></span>

:::image type="content" source="../../assets/images/icons/personal-app-icon-example.png" alt-text="Beispiel, das zeigt, wie ein App-Symbol in einer persönlichen App aussieht." border="false":::

#### <a name="bot-channel"></a><span data-ttu-id="b8b16-146">Bot (Kanal)</span><span class="sxs-lookup"><span data-stu-id="b8b16-146">Bot (channel)</span></span>

:::image type="content" source="../../assets/images/icons/bot-icon-example.png" alt-text="Beispiel, das zeigt, wie ein App-Symbol auf einem Bot innerhalb eines Kanals aussieht." border="false":::

#### <a name="messaging-extension"></a><span data-ttu-id="b8b16-148">Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="b8b16-148">Messaging extension</span></span>

:::image type="content" source="../../assets/images/icons/messaging-extension-icon-example.png" alt-text="<text>" border="false":::

## <a name="next-step"></a><span data-ttu-id="b8b16-150">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="b8b16-150">Next step</span></span>

<span data-ttu-id="b8b16-151">Wählen Sie aus, wie Sie Ihre App verteilen möchten:</span><span class="sxs-lookup"><span data-stu-id="b8b16-151">Choose how you plan to distribute your app:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b8b16-152">Querladen Ihrer App in Teams</span><span class="sxs-lookup"><span data-stu-id="b8b16-152">Sideload your app in Teams</span></span>](~/concepts/deploy-and-publish/apps-upload.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="b8b16-153">Veröffentlichen Ihrer App in Ihrer Organisation</span><span class="sxs-lookup"><span data-stu-id="b8b16-153">Publish your app to your org</span></span>](/MicrosoftTeams/tenant-apps-catalog-teams?toc=/microsoftteams/platform/toc.json&bc=/MicrosoftTeams/breadcrumb/toc.json)
> [!div class="nextstepaction"]
> [<span data-ttu-id="b8b16-154">Veröffentlichen Ihrer App im Store</span><span class="sxs-lookup"><span data-stu-id="b8b16-154">Publish your app to the store</span></span>](~/concepts/deploy-and-publish/appsource/publish.md)
