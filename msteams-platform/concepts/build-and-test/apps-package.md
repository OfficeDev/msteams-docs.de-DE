---
title: Packen Ihrer App
description: Erfahren Sie, wie Sie Ihre Microsoft Teams-App zum Testen, Hochladen und Speichern der Veröffentlichung packen.
ms.topic: conceptual
ms.openlocfilehash: 222ea5459b3496c00b1186f15a68c3288ce419f7
ms.sourcegitcommit: 35bc2a31b92f3f7c6524373108f095a870d9ad09
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2021
ms.locfileid: "51922510"
---
# <a name="create-an-app-package-for-your-microsoft-teams-app"></a><span data-ttu-id="16211-103">Erstellen eines App-Pakets für Ihre Microsoft Teams-App</span><span class="sxs-lookup"><span data-stu-id="16211-103">Create an app package for your Microsoft Teams app</span></span>

<span data-ttu-id="16211-104">Apps in Teams werden durch eine App-Manifest-JSON-Datei definiert und in einem App-Paket mit ihren Symbolen gebündelt.</span><span class="sxs-lookup"><span data-stu-id="16211-104">Apps in Teams are defined by an app manifest JSON file, and bundled in an app package with their icons.</span></span> <span data-ttu-id="16211-105">Sie benötigen ein App-Paket, um Ihre App in Teams hochzuladen und zu installieren und entweder in Ihrem Line of Business-App-Katalog oder in AppSource zu veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="16211-105">You'll need an app package to upload and install your app in Teams and publish to either your Line of Business app catalog or to AppSource.</span></span>

<span data-ttu-id="16211-106">Ein Teams-App-Paket ist eine ZIP-Datei, die Folgendes enthält:</span><span class="sxs-lookup"><span data-stu-id="16211-106">A Teams app package is a .zip file containing the following:</span></span>

* <span data-ttu-id="16211-107">Eine Manifestdatei mit dem Namen , die Attribute Ihrer App angibt und auf erforderliche Ressourcen für Ihre Erfahrung verweist, z. B. den Speicherort der Registerkartenkonfigurationsseite oder die `manifest.json` Microsoft-App-ID für den Bot.</span><span class="sxs-lookup"><span data-stu-id="16211-107">A manifest file named `manifest.json`, which specifies attributes of your app and points to required resources for your experience, such the location of its tab configuration page or the Microsoft app ID for its bot.</span></span>
* <span data-ttu-id="16211-108">[Farb- und Gliederungssymbole für Ihre App](#app-icons).</span><span class="sxs-lookup"><span data-stu-id="16211-108">[Color and outline icons for your app](#app-icons).</span></span>

## <a name="creating-a-manifest"></a><span data-ttu-id="16211-109">Erstellen einer Manifestdatei</span><span class="sxs-lookup"><span data-stu-id="16211-109">Creating a manifest</span></span>

<span data-ttu-id="16211-110">**Teams App Studio kann** Ihnen bei der Konfiguration Ihres Manifests helfen.</span><span class="sxs-lookup"><span data-stu-id="16211-110">**Teams App Studio** can help configure your manifest.</span></span> <span data-ttu-id="16211-111">App Studio enthält außerdem eine React-Steuerelementbibliothek sowie konfigurierbare Beispiele für Karten.</span><span class="sxs-lookup"><span data-stu-id="16211-111">It also contains a React control library and configurable samples for cards.</span></span> <span data-ttu-id="16211-112">Weitere Informationen finden Sie unter [App Studio Overview](~/concepts/build-and-test/app-studio-overview.md).</span><span class="sxs-lookup"><span data-stu-id="16211-112">For more information, see [App Studio Overview](~/concepts/build-and-test/app-studio-overview.md).</span></span>

<span data-ttu-id="16211-113">Ihre Manifestdatei muss den Namen "manifest.jsein" haben und sich auf der obersten Ebene des Uploadpakets begnaufen.</span><span class="sxs-lookup"><span data-stu-id="16211-113">Your manifest file must be named "manifest.json" and be at the top level of the upload package.</span></span> <span data-ttu-id="16211-114">Beachten Sie, dass zuvor erstellte Manifeste und Pakete möglicherweise eine ältere Version des Schemas unterstützen.</span><span class="sxs-lookup"><span data-stu-id="16211-114">Note that manifests and packages built previously might support an older version of the schema.</span></span> <span data-ttu-id="16211-115">Für Teams-Apps und insbesondere die AppSource-Übermittlung (früher Office Store) müssen Sie das aktuelle [Manifestschema verwenden.](~/resources/schema/manifest-schema.md)</span><span class="sxs-lookup"><span data-stu-id="16211-115">For Teams apps and especially AppSource (formerly Office Store) submission, you must use the current [manifest schema](~/resources/schema/manifest-schema.md).</span></span>

> [!TIP]
> <span data-ttu-id="16211-116">Geben Sie das Schema am Anfang des Manifests an, um IntelliSense oder ähnliche Unterstützung von Ihrem Code-Editor zu aktivieren:</span><span class="sxs-lookup"><span data-stu-id="16211-116">Specify the schema at the beginning of your manifest to enable IntelliSense or similar support from your code editor:</span></span>
>
> `"$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.9/MicrosoftTeams.schema.json",`
 
## <a name="app-icons"></a><span data-ttu-id="16211-117">App-Symbole</span><span class="sxs-lookup"><span data-stu-id="16211-117">App icons</span></span>

<span data-ttu-id="16211-118">Ihr App-Paket muss zwei PNG-Versionen ihres App-Symbols enthalten– ein Farbsymbol und ein Gliederungssymbol.</span><span class="sxs-lookup"><span data-stu-id="16211-118">Your app package must include two PNG versions of your app icon—a color icon and an outline icon.</span></span> <span data-ttu-id="16211-119">Damit Ihre App die AppSource-Überprüfung bestehen kann, müssen diese Symbole die folgenden Größenanforderungen erfüllen.</span><span class="sxs-lookup"><span data-stu-id="16211-119">For your app to pass the AppSource review, these icons must meet the following size requirements.</span></span>

> [!Note]
> <span data-ttu-id="16211-120">Wenn Ihre App über einen Bot oder eine Messagingerweiterung verfügt, werden Ihre Symbole auch in Ihre Microsoft Azure Bot Service-Registrierung einbezogen.</span><span class="sxs-lookup"><span data-stu-id="16211-120">If your app has a bot or messaging extension, your icons also will be included in your Microsoft Azure Bot Service registration.</span></span>

### <a name="color-icon"></a><span data-ttu-id="16211-121">Farbsymbol</span><span class="sxs-lookup"><span data-stu-id="16211-121">Color icon</span></span>

<span data-ttu-id="16211-122">Die Farbversion Ihres Symbols wird in den meisten Teams-Szenarien angezeigt und muss 192 x 192 Pixel groß sein.</span><span class="sxs-lookup"><span data-stu-id="16211-122">The color version of your icon displays in most Teams scenarios and must be 192x192 pixels.</span></span> <span data-ttu-id="16211-123">Ihr Symbol (96 x 96 Pixel) kann eine beliebige Farbe oder Farbe sein, muss jedoch auf einem einfarbigen oder vollständig transparenten quadratischen Hintergrund stehen.</span><span class="sxs-lookup"><span data-stu-id="16211-123">Your icon symbol (96x96 pixels) can be any color or colors, but it must sit on a solid or fully transparent square background.</span></span>

<span data-ttu-id="16211-124">Teams ackert Ihr Symbol automatisch, um ein Quadrat mit abgerundeten Ecken in mehreren Szenarien und eine hexagonale Form in Botszenarien zu zeigen.</span><span class="sxs-lookup"><span data-stu-id="16211-124">Teams automatically crops your icon to display a square with rounded corners in multiple scenarios and a hexagonal shape in bot scenarios.</span></span> <span data-ttu-id="16211-125">Schließen Sie 48 Pixel Abstand um das Symbol ein, damit diese Kulturen ohne Detailverlust hergestellt werden können.</span><span class="sxs-lookup"><span data-stu-id="16211-125">Include 48 pixels of padding around your symbol so these crops can be made without losing any detail.</span></span>

:::image type="content" source="../../assets/images/icons/design-color-icon.png" alt-text="Designanleitungen für Teams-Farbsymbole." border="false":::

### <a name="outline-icon"></a><span data-ttu-id="16211-127">Gliederungssymbol</span><span class="sxs-lookup"><span data-stu-id="16211-127">Outline icon</span></span>

<span data-ttu-id="16211-128">Ein Gliederungssymbol wird in zwei Szenarien angezeigt:</span><span class="sxs-lookup"><span data-stu-id="16211-128">An outline icon displays in two scenarios:</span></span>

* <span data-ttu-id="16211-129">Wenn Ihre App verwendet wird und auf der App-Leiste links von Teams "gehissen" wird.</span><span class="sxs-lookup"><span data-stu-id="16211-129">When your app is in use and “hoisted” on the app bar on the left of Teams.</span></span>
* <span data-ttu-id="16211-130">wenn ein Benutzer die Messagingerweiterung Ihrer App anheften.</span><span class="sxs-lookup"><span data-stu-id="16211-130">when a user pins your app's messaging extension.</span></span>

<span data-ttu-id="16211-131">Das Symbol muss 32 x 32 Pixel groß sein.</span><span class="sxs-lookup"><span data-stu-id="16211-131">The icon must be 32x32 pixels.</span></span> <span data-ttu-id="16211-132">Es kann weiß mit einem transparenten Hintergrund oder transparent mit weißem Hintergrund sein (keine anderen Farben sind zulässig).</span><span class="sxs-lookup"><span data-stu-id="16211-132">It can be white with a transparent background or transparent with a white background (no other colors are permitted).</span></span> <span data-ttu-id="16211-133">Das Gliederungssymbol sollte keinen zusätzlichen Abstand um das Symbol haben.</span><span class="sxs-lookup"><span data-stu-id="16211-133">The outline icon should not have any extra padding around the symbol.</span></span>

:::image type="content" source="../../assets/images/icons/design-outline-icon.png" alt-text="Richtlinien zum Entwerfen von Symbolen in Teams." border="false":::

### <a name="best-practices"></a><span data-ttu-id="16211-135">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="16211-135">Best practices</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/icons/design-icon-do.png" alt-text="Abbildung, die zeigt, wie Sie Ihre App-Symbole entwerfen." border="false":::

#### <a name="do-follow-the-precise-outline-icon-guidelines"></a><span data-ttu-id="16211-137">Do: Befolgen Sie die Richtlinien für genaue Gliederungssymbole.</span><span class="sxs-lookup"><span data-stu-id="16211-137">Do: Follow the precise outline icon guidelines</span></span>

<span data-ttu-id="16211-138">Die RGB-Werte von Weiß, die in Ihrem Symbol verwendet werden, müssen Rot sein: 255, Grün: 255, Blau: 255.</span><span class="sxs-lookup"><span data-stu-id="16211-138">The RGB values of white used in your icon must be Red: 255, Green: 255, Blue: 255.</span></span> <span data-ttu-id="16211-139">Alle anderen Teile des Gliederungssymbols müssen vollständig transparent sein, und der Alphakanal ist auf 0 festgelegt.</span><span class="sxs-lookup"><span data-stu-id="16211-139">All other parts of the outline icon must be fully transparent, with the alpha channel set to 0.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/icons/design-icon-dont.png" alt-text="Abbildung, die zeigt, wie Sie Ihre App-Symbole nicht entwerfen." border="false":::

#### <a name="dont-crop-in-a-circular-or-rounded-square-shape"></a><span data-ttu-id="16211-141">Don't: Crop in a circular or rounded square shape</span><span class="sxs-lookup"><span data-stu-id="16211-141">Don't: Crop in a circular or rounded square shape</span></span>

<span data-ttu-id="16211-142">Das in Ihrem App-Paket übermittelte Farbsymbol muss quadratisch sein.</span><span class="sxs-lookup"><span data-stu-id="16211-142">The color icon submitted in your app package must be square.</span></span> <span data-ttu-id="16211-143">Runden Sie nicht die Ecken Ihres Symbols.</span><span class="sxs-lookup"><span data-stu-id="16211-143">Don’t round the corners of your icon.</span></span> <span data-ttu-id="16211-144">Teams passt den Eckenradius automatisch an.</span><span class="sxs-lookup"><span data-stu-id="16211-144">Teams automatically adjusts the corner radius.</span></span>

   :::column-end:::
:::row-end:::

### <a name="examples"></a><span data-ttu-id="16211-145">Beispiele</span><span class="sxs-lookup"><span data-stu-id="16211-145">Examples</span></span>

<span data-ttu-id="16211-146">Hier sehen Sie, wie App-Symbole in verschiedenen Teams-Funktionen und Kontexten angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="16211-146">Here's how app icons appear in different Teams capabilities and contexts.</span></span>

#### <a name="personal-app"></a><span data-ttu-id="16211-147">Persönliche App</span><span class="sxs-lookup"><span data-stu-id="16211-147">Personal app</span></span>

:::image type="content" source="../../assets/images/icons/personal-app-icon-example.png" alt-text="Beispiel, das zeigt, wie ein App-Symbol in einer persönlichen App aussieht." border="false":::

#### <a name="bot-channel"></a><span data-ttu-id="16211-149">Bot (Kanal)</span><span class="sxs-lookup"><span data-stu-id="16211-149">Bot (channel)</span></span>

:::image type="content" source="../../assets/images/icons/bot-icon-example.png" alt-text="Beispiel, das zeigt, wie ein App-Symbol auf einem Bot innerhalb eines Kanals aussieht." border="false":::

#### <a name="messaging-extension"></a><span data-ttu-id="16211-151">Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="16211-151">Messaging extension</span></span>

:::image type="content" source="../../assets/images/icons/messaging-extension-icon-example.png" alt-text="<text>" border="false":::
