---
title: Verpacken Sie Ihre App
description: Erfahren Sie, wie Sie Ihre Microsoft Teams-App zum Testen, Hochladen und Store-Publishing verpacken.
localization_priority: Normal
ms.topic: conceptual
ms.openlocfilehash: 219e2d5341707ed51b7e0a3a8077f93df9eac640
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565214"
---
# <a name="create-a-microsoft-teams-app-package"></a><span data-ttu-id="3bec4-103">Erstellen eines Microsoft Teams-App-Pakets</span><span class="sxs-lookup"><span data-stu-id="3bec4-103">Create a Microsoft Teams app package</span></span>

<span data-ttu-id="3bec4-104">Sie benötigen ein App-Paket, wie auch immer Sie Ihre Microsoft Teams-App verteilen möchten.</span><span class="sxs-lookup"><span data-stu-id="3bec4-104">You need an app package however you plan to distribute your Microsoft Teams app.</span></span> <span data-ttu-id="3bec4-105">Ein gültiges Paket ist eine ZIP-Datei, die Folgendes enthält:</span><span class="sxs-lookup"><span data-stu-id="3bec4-105">A valid package is a ZIP file that contains the following:</span></span>

* <span data-ttu-id="3bec4-106">**App-Manifest**: Beschreibt, wie Ihre App konfiguriert ist, einschließlich ihrer Funktionen, erforderlichen Ressourcen und anderer wichtiger Attribute.</span><span class="sxs-lookup"><span data-stu-id="3bec4-106">**App manifest**: Describes how your app is configured, including its capabilities, required resources, and other important attributes.</span></span>
* <span data-ttu-id="3bec4-107">**App-Symbole**: Jedes Paket erfordert ein Farb- und Umrisssymbol für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="3bec4-107">**App icons**: Each package requires a color and outline icon for your app.</span></span>

## <a name="app-manifest"></a><span data-ttu-id="3bec4-108">App-Manifest</span><span class="sxs-lookup"><span data-stu-id="3bec4-108">App manifest</span></span>

<span data-ttu-id="3bec4-109">Ihre App-Manifestdatei muss sich auf der obersten Ebene des Pakets mit dem Namen `manifest.json` befinden.</span><span class="sxs-lookup"><span data-stu-id="3bec4-109">Your app manifest file must be at the top level of the package with the name `manifest.json`.</span></span> 

<span data-ttu-id="3bec4-110">Stellen Sie beim Veröffentlichen im Teams-Speicher sicher, dass das Manifest auf das neueste [Schema](~/resources/schema/manifest-schema.md)verweist.</span><span class="sxs-lookup"><span data-stu-id="3bec4-110">When publishing to the Teams store, make sure your manifest references the latest [schema](~/resources/schema/manifest-schema.md).</span></span>

## <a name="app-icons"></a><span data-ttu-id="3bec4-111">App-Symbole</span><span class="sxs-lookup"><span data-stu-id="3bec4-111">App icons</span></span>

<span data-ttu-id="3bec4-112">Ihr App-Paket muss zwei PNG-Versionen Ihres App-Symbols enthalten: eine Farb- und Gliederungsversion.</span><span class="sxs-lookup"><span data-stu-id="3bec4-112">Your app package must include two PNG versions of your app icon: A color and outline version.</span></span>

> [!Note]
> <span data-ttu-id="3bec4-113">Wenn Ihre App über einen Bot oder eine Messaging-Erweiterung verfügt, werden Ihre Symbole auch in Ihre Microsoft Azure Bot Service-Registrierung einbezogen.</span><span class="sxs-lookup"><span data-stu-id="3bec4-113">If your app has a bot or messaging extension, your icons also will be included in your Microsoft Azure Bot Service registration.</span></span>

<span data-ttu-id="3bec4-114">Damit Ihre App Teams Store-Überprüfung bestehen kann, müssen diese Symbole die folgenden Größenanforderungen erfüllen.</span><span class="sxs-lookup"><span data-stu-id="3bec4-114">For your app to pass Teams store review, these icons must meet the following size requirements.</span></span>

### <a name="color-icon"></a><span data-ttu-id="3bec4-115">Farbsymbol</span><span class="sxs-lookup"><span data-stu-id="3bec4-115">Color icon</span></span>

<span data-ttu-id="3bec4-116">Die Farbversion ihres Symbols wird in den meisten Teams Szenarien angezeigt und muss 192x192 Pixel betragen.</span><span class="sxs-lookup"><span data-stu-id="3bec4-116">The color version of your icon displays in most Teams scenarios and must be 192x192 pixels.</span></span> <span data-ttu-id="3bec4-117">Ihr Symbolsymbol (96x96 Pixel) kann eine beliebige Farbe haben, muss jedoch auf einem durchgezogenen oder vollständig transparenten quadratischen Hintergrund sitzen.</span><span class="sxs-lookup"><span data-stu-id="3bec4-117">Your icon symbol (96x96 pixels) can be any color, but it must sit on a solid or fully transparent square background.</span></span>

<span data-ttu-id="3bec4-118">Teams schneidet Ihr Symbol automatisch zu, um ein Quadrat mit abgerundeten Ecken in mehreren Szenarien und einer sechseckigen Form in Bot-Szenarien anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="3bec4-118">Teams automatically crops your icon to display a square with rounded corners in multiple scenarios and a hexagonal shape in bot scenarios.</span></span> <span data-ttu-id="3bec4-119">Um das Symbol zuzuschneiden, ohne Details zu verlieren, schließen Sie 48 Pixel Auffüllung um Ihr Symbol ein.</span><span class="sxs-lookup"><span data-stu-id="3bec4-119">To crop the symbol without losing any detail, include 48 pixels of padding around your symbol.</span></span>

:::image type="content" source="../../assets/images/icons/design-color-icon.png" alt-text="Teams Farbsymbol und Designanleitung." border="false":::

### <a name="outline-icon"></a><span data-ttu-id="3bec4-121">Gliederungssymbol</span><span class="sxs-lookup"><span data-stu-id="3bec4-121">Outline icon</span></span>

<span data-ttu-id="3bec4-122">In zwei Szenarien wird ein Gliederungssymbol angezeigt:</span><span class="sxs-lookup"><span data-stu-id="3bec4-122">An outline icon displays in two scenarios:</span></span>

* <span data-ttu-id="3bec4-123">Wenn Ihre App verwendet und in der App-Leiste auf der linken Seite von Teams "gehisst" wird.</span><span class="sxs-lookup"><span data-stu-id="3bec4-123">When your app is in use and “hoisted” on the app bar on the left side of Teams.</span></span>
* <span data-ttu-id="3bec4-124">Wenn ein Benutzer die Messagingerweiterung Ihrer App anheftet.</span><span class="sxs-lookup"><span data-stu-id="3bec4-124">When a user pins your app's messaging extension.</span></span>

<span data-ttu-id="3bec4-125">Das Symbol muss 32x32 Pixel groß sein.</span><span class="sxs-lookup"><span data-stu-id="3bec4-125">The icon must be 32x32 pixels.</span></span> <span data-ttu-id="3bec4-126">Es kann weiß mit einem transparenten Hintergrund oder transparent mit einem weißen Hintergrund sein (keine anderen Farben sind erlaubt).</span><span class="sxs-lookup"><span data-stu-id="3bec4-126">It can be white with a transparent background or transparent with a white background (no other colors are permitted).</span></span> <span data-ttu-id="3bec4-127">Das Umrisssymbol sollte keine zusätzliche Auffüllung um das Symbol herum haben.</span><span class="sxs-lookup"><span data-stu-id="3bec4-127">The outline icon should not have any extra padding around the symbol.</span></span>

:::image type="content" source="../../assets/images/icons/design-outline-icon.png" alt-text="Teams Anleitung zum Entwurf des Umrisssymbols." border="false":::

### <a name="best-practices"></a><span data-ttu-id="3bec4-129">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="3bec4-129">Best practices</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/icons/design-icon-do.png" alt-text="Abbildung zum Entwerfen Ihrer App-Symbole." border="false":::

#### <a name="do-follow-the-precise-outline-icon-guidelines"></a><span data-ttu-id="3bec4-131">Tun: Befolgen Sie die genauen Richtlinien für das Gliederungssymbol</span><span class="sxs-lookup"><span data-stu-id="3bec4-131">Do: Follow the precise outline icon guidelines</span></span>

<span data-ttu-id="3bec4-132">Die RGB-Werte von Weiß, die in Ihrem Symbol verwendet werden, müssen Rot sein: 255, Grün: 255, Blau: 255.</span><span class="sxs-lookup"><span data-stu-id="3bec4-132">The RGB values of white used in your icon must be Red: 255, Green: 255, Blue: 255.</span></span> <span data-ttu-id="3bec4-133">Alle anderen Teile des Gliederungssymbols müssen vollständig transparent sein, wobei der Alphakanal auf 0 gesetzt ist.</span><span class="sxs-lookup"><span data-stu-id="3bec4-133">All other parts of the outline icon must be fully transparent, with the alpha channel set to 0.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/icons/design-icon-dont.png" alt-text="Abbildung zeigt, wie Sie Ihre App-Symbole nicht entwerfen." border="false":::

#### <a name="dont-crop-in-a-circular-or-rounded-square-shape"></a><span data-ttu-id="3bec4-135">Nicht: Zuschneiden in kreisförmiger oder abgerundeter quadratischer Form</span><span class="sxs-lookup"><span data-stu-id="3bec4-135">Don't: Crop in a circular or rounded square shape</span></span>

<span data-ttu-id="3bec4-136">Das in Ihrem App-Paket übermittelte Farbsymbol muss quadratisch sein.</span><span class="sxs-lookup"><span data-stu-id="3bec4-136">The color icon submitted in your app package must be square.</span></span> <span data-ttu-id="3bec4-137">Umrunden Sie nicht die Ecken Ihres Symbols.</span><span class="sxs-lookup"><span data-stu-id="3bec4-137">Don’t round the corners of your icon.</span></span> <span data-ttu-id="3bec4-138">Teams passt den Eckenradius automatisch an.</span><span class="sxs-lookup"><span data-stu-id="3bec4-138">Teams automatically adjusts the corner radius.</span></span>

   :::column-end:::
:::row-end:::

#### <a name="dont-copy-other-brands"></a><span data-ttu-id="3bec4-139">Nicht: Andere Marken kopieren</span><span class="sxs-lookup"><span data-stu-id="3bec4-139">Don't: Copy other brands</span></span>

<span data-ttu-id="3bec4-140">Ihre Symbole dürfen keine urheberrechtlich geschützten Produkte imitieren, die Sie nicht besitzen.</span><span class="sxs-lookup"><span data-stu-id="3bec4-140">Your icons must not mimic any copyrighted products that you don't own.</span></span> <span data-ttu-id="3bec4-141">Beispielsweise ein Design, das einem Microsoft-Produkt oder einer Microsoft-Marke ähnelt.</span><span class="sxs-lookup"><span data-stu-id="3bec4-141">For example, a design similar to a Microsoft product or brand.</span></span>

### <a name="examples"></a><span data-ttu-id="3bec4-142">Beispiele</span><span class="sxs-lookup"><span data-stu-id="3bec4-142">Examples</span></span>

<span data-ttu-id="3bec4-143">So werden App-Symbole in verschiedenen Teams Funktionen und Kontexten angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3bec4-143">Here's how app icons appear in different Teams capabilities and contexts.</span></span>

#### <a name="personal-app"></a><span data-ttu-id="3bec4-144">Persönliche App</span><span class="sxs-lookup"><span data-stu-id="3bec4-144">Personal app</span></span>

:::image type="content" source="../../assets/images/icons/personal-app-icon-example.png" alt-text="Beispiel, das zeigt, wie ein App-Symbol in einer persönlichen App aussieht." border="false":::

#### <a name="bot-channel"></a><span data-ttu-id="3bec4-146">Bot (Kanal)</span><span class="sxs-lookup"><span data-stu-id="3bec4-146">Bot (channel)</span></span>

:::image type="content" source="../../assets/images/icons/bot-icon-example.png" alt-text="Beispiel, das zeigt, wie ein App-Symbol auf einem Bot innerhalb des Kanals aussieht." border="false":::

#### <a name="messaging-extension"></a><span data-ttu-id="3bec4-148">Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="3bec4-148">Messaging extension</span></span>

:::image type="content" source="../../assets/images/icons/messaging-extension-icon-example.png" alt-text="<Alt-Text>" border="false":::

## <a name="next-step"></a><span data-ttu-id="3bec4-150">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="3bec4-150">Next step</span></span>

<span data-ttu-id="3bec4-151">Wählen Sie aus, wie Sie Ihre App verteilen möchten:</span><span class="sxs-lookup"><span data-stu-id="3bec4-151">Choose how you plan to distribute your app:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3bec4-152">Sideload Ihre App in Teams</span><span class="sxs-lookup"><span data-stu-id="3bec4-152">Sideload your app in Teams</span></span>](~/concepts/deploy-and-publish/apps-upload.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="3bec4-153">Veröffentlichen Sie Ihre App in Ihrer Organisation</span><span class="sxs-lookup"><span data-stu-id="3bec4-153">Publish your app to your org</span></span>](/MicrosoftTeams/tenant-apps-catalog-teams?toc=/microsoftteams/platform/toc.json&bc=/MicrosoftTeams/breadcrumb/toc.json)
> [!div class="nextstepaction"]
> [<span data-ttu-id="3bec4-154">Veröffentlichen Ihrer App im Store</span><span class="sxs-lookup"><span data-stu-id="3bec4-154">Publish your app to the store</span></span>](~/concepts/deploy-and-publish/appsource/publish.md)
