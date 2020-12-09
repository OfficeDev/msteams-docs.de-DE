---
title: Verpacken Ihrer APP
description: Hier erfahren Sie, wie Sie Ihre Microsoft Teams-App zum Testen, hochladen und Speichern von Veröffentlichungen verpacken.
ms.topic: conceptual
ms.openlocfilehash: 6929375c8d6a1602f01d83d15bfa0dab7f02a664
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "49605274"
---
# <a name="create-an-app-package-for-your-microsoft-teams-app"></a><span data-ttu-id="11f70-103">Erstellen eines App-Pakets für Ihre Microsoft Teams-App</span><span class="sxs-lookup"><span data-stu-id="11f70-103">Create an app package for your Microsoft Teams app</span></span>

<span data-ttu-id="11f70-104">Apps in Microsoft Teams werden durch eine JSON-Datei für App-Manifeste definiert und in einem App-Paket mit ihren Symbolen gebündelt.</span><span class="sxs-lookup"><span data-stu-id="11f70-104">Apps in Teams are defined by an app manifest JSON file, and bundled in an app package with their icons.</span></span> <span data-ttu-id="11f70-105">Sie benötigen ein App-Paket, um Ihre APP in Microsoft Teams hochzuladen und zu installieren und entweder in Ihrem Branchen-App-Katalog oder in AppSource zu veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="11f70-105">You'll need an app package to upload and install your app in Teams and publish to either your Line of Business app catalog or to AppSource.</span></span>

<span data-ttu-id="11f70-106">Ein Teams-App-Paket ist eine ZIP-Datei, die Folgendes enthält:</span><span class="sxs-lookup"><span data-stu-id="11f70-106">A Teams app package is a .zip file containing the following:</span></span>

* <span data-ttu-id="11f70-107">Eine Manifestdatei mit dem Namen `manifest.json` , die Attribute Ihrer APP angibt und auf erforderliche Ressourcen für Ihre Benutzeroberfläche verweist, beispielsweise den Speicherort der Registerkarten-Konfigurationsseite oder die Microsoft App-ID für den bot.</span><span class="sxs-lookup"><span data-stu-id="11f70-107">A manifest file named `manifest.json`, which specifies attributes of your app and points to required resources for your experience, such the location of its tab configuration page or the Microsoft app ID for its bot.</span></span>
* <span data-ttu-id="11f70-108">[Symbole für Farben und Gliederungen für Ihre APP](#app-icons).</span><span class="sxs-lookup"><span data-stu-id="11f70-108">[Color and outline icons for your app](#app-icons).</span></span>

## <a name="creating-a-manifest"></a><span data-ttu-id="11f70-109">Erstellen einer Manifestdatei</span><span class="sxs-lookup"><span data-stu-id="11f70-109">Creating a manifest</span></span>

<span data-ttu-id="11f70-110">*Teams App Studio* kann bei der Konfiguration ihres Manifests behilflich sein.</span><span class="sxs-lookup"><span data-stu-id="11f70-110">*Teams App Studio* can help configure your manifest.</span></span> <span data-ttu-id="11f70-111">App Studio enthält außerdem eine React-Steuerelementbibliothek sowie konfigurierbare Beispiele für Karten.</span><span class="sxs-lookup"><span data-stu-id="11f70-111">It also contains a React control library and configurable samples for cards.</span></span> <span data-ttu-id="11f70-112">Siehe [Übersicht über das App-Studio](~/concepts/build-and-test/app-studio-overview.md).</span><span class="sxs-lookup"><span data-stu-id="11f70-112">See [App Studio Overview](~/concepts/build-and-test/app-studio-overview.md).</span></span>

<span data-ttu-id="11f70-113">Ihre Manifestdatei muss den Namen "manifest.json" tragen und sich auf der obersten Ebene des Upload-Pakets befinden.</span><span class="sxs-lookup"><span data-stu-id="11f70-113">Your manifest file must be named "manifest.json" and be at the top level of the upload package.</span></span> <span data-ttu-id="11f70-114">Beachten Sie, dass zuvor erstellte Manifeste und Pakete möglicherweise eine ältere Version des Schemas unterstützen.</span><span class="sxs-lookup"><span data-stu-id="11f70-114">Note that manifests and packages built previously might support an older version of the schema.</span></span> <span data-ttu-id="11f70-115">Für Microsoft Teams-apps und insbesondere AppSource (ehemals Office Store)-Übermittlung müssen Sie das aktuelle [Manifest-Schema](~/resources/schema/manifest-schema.md)verwenden.</span><span class="sxs-lookup"><span data-stu-id="11f70-115">For Teams apps and especially AppSource (formerly Office Store) submission, you must use the current [manifest schema](~/resources/schema/manifest-schema.md).</span></span>

> [!TIP]
> <span data-ttu-id="11f70-116">Geben Sie das Schema am Anfang des Manifests an, um IntelliSense oder ähnliche Unterstützung aus Ihrem Code-Editor zu aktivieren:</span><span class="sxs-lookup"><span data-stu-id="11f70-116">Specify the schema at the beginning of your manifest to enable IntelliSense or similar support from your code editor:</span></span>
>
> `"$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",`

## <a name="app-icons"></a><span data-ttu-id="11f70-117">App-Symbole</span><span class="sxs-lookup"><span data-stu-id="11f70-117">App icons</span></span>

<span data-ttu-id="11f70-118">Ihr App-Paket muss zwei PNG-Versionen Ihres App-Symbols enthalten: ein Farbsymbol und ein Gliederungssymbol.</span><span class="sxs-lookup"><span data-stu-id="11f70-118">Your app package must include two PNG versions of your app icon—a color icon and an outline icon.</span></span> <span data-ttu-id="11f70-119">Damit Ihre APP die AppSource-Überprüfung übergibt, müssen diese Symbole die folgenden Größenanforderungen erfüllen.</span><span class="sxs-lookup"><span data-stu-id="11f70-119">For your app to pass the AppSource review, these icons must meet the following size requirements.</span></span>

> [!Note]
> <span data-ttu-id="11f70-120">Wenn Ihre APP über eine bot-oder Messaging-Erweiterung verfügt, werden Ihre Symbole auch in Ihrer Microsoft Azure bot-Dienstregistrierung enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="11f70-120">If your app has a bot or messaging extension, your icons also will be included in your Microsoft Azure Bot Service registration.</span></span>

### <a name="color-icon"></a><span data-ttu-id="11f70-121">Farbsymbol</span><span class="sxs-lookup"><span data-stu-id="11f70-121">Color icon</span></span>

<span data-ttu-id="11f70-122">Die Farbversion Ihres Symbols wird in den meisten Microsoft Teams-Szenarien angezeigt und muss 192x192 Pixel sein.</span><span class="sxs-lookup"><span data-stu-id="11f70-122">The color version of your icon displays in most Teams scenarios and must be 192x192 pixels.</span></span> <span data-ttu-id="11f70-123">Das Symbol Symbol (96x96 Pixel) kann eine beliebige Farbe oder Farbe sein, es muss jedoch auf einem soliden oder vollständig transparenten Quadrat Hintergrund sitzen.</span><span class="sxs-lookup"><span data-stu-id="11f70-123">Your icon symbol (96x96 pixels) can be any color or colors, but it must sit on a solid or fully transparent square background.</span></span>

<span data-ttu-id="11f70-124">Teams schneidet ihr Symbol automatisch so ab, dass in bot-Szenarien ein Quadrat mit abgerundeten Ecken in mehreren Szenarien und einer hexagonalen Form angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="11f70-124">Teams automatically crops your icon to display a square with rounded corners in multiple scenarios and a hexagonal shape in bot scenarios.</span></span> <span data-ttu-id="11f70-125">Fügen Sie 48 Pixelabstand um Ihr Symbol ein, damit diese Kulturen ohne jegliche Details gemacht werden können.</span><span class="sxs-lookup"><span data-stu-id="11f70-125">Include 48 pixels of padding around your symbol so these crops can be made without losing any detail.</span></span>

:::image type="content" source="../../assets/images/icons/design-color-icon.png" alt-text="Microsoft Teams Color Icon Design Guidance." border="false":::

### <a name="outline-icon"></a><span data-ttu-id="11f70-127">Gliederungssymbol</span><span class="sxs-lookup"><span data-stu-id="11f70-127">Outline icon</span></span>

<span data-ttu-id="11f70-128">Ein Gliederungssymbol wird in zwei Szenarien angezeigt:</span><span class="sxs-lookup"><span data-stu-id="11f70-128">An outline icon displays in two scenarios:</span></span>

* <span data-ttu-id="11f70-129">Wenn Ihre APP in der APP-Leiste auf der linken Seite von Microsoft Teams verwendet und "gehisst" wird.</span><span class="sxs-lookup"><span data-stu-id="11f70-129">When your app is in use and “hoisted” on the app bar on the left of Teams.</span></span>
* <span data-ttu-id="11f70-130">Wenn ein Benutzer die Messaging Erweiterung der APP anstiftet.</span><span class="sxs-lookup"><span data-stu-id="11f70-130">when a user pins your app's messaging extension.</span></span>

<span data-ttu-id="11f70-131">Das Symbol muss 32x32 Pixel sein.</span><span class="sxs-lookup"><span data-stu-id="11f70-131">The icon must be 32x32 pixels.</span></span> <span data-ttu-id="11f70-132">Er kann weiß mit einem transparenten Hintergrund oder transparent mit weißem Hintergrund sein (es sind keine anderen Farben zulässig).</span><span class="sxs-lookup"><span data-stu-id="11f70-132">It can be white with a transparent background or transparent with a white background (no other colors are permitted).</span></span> <span data-ttu-id="11f70-133">Das Symbol "Gliederung" sollte keinen zusätzlichen Abstand um das Symbol haben.</span><span class="sxs-lookup"><span data-stu-id="11f70-133">The outline icon should not have any extra padding around the symbol.</span></span>

:::image type="content" source="../../assets/images/icons/design-outline-icon.png" alt-text="Microsoft Teams Color Icon Design Guidance." border="false":::

### <a name="best-practices"></a><span data-ttu-id="11f70-135">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="11f70-135">Best practices</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/icons/design-icon-do.png" alt-text="Illustration, die zeigt, wie Sie Ihre APP-Symbole entwerfen." border="false":::

#### <a name="do-follow-the-precise-outline-icon-guidelines"></a><span data-ttu-id="11f70-137">Ausführen: Folgen Sie den genauen Gliederungssymbol-Richtlinien</span><span class="sxs-lookup"><span data-stu-id="11f70-137">Do: Follow the precise outline icon guidelines</span></span>

<span data-ttu-id="11f70-138">Die in Ihrem Symbol verwendeten RGB-Werte von weiß müssen rot sein: 255, grün: 255, blau: 255.</span><span class="sxs-lookup"><span data-stu-id="11f70-138">The RGB values of white used in your icon must be Red: 255, Green: 255, Blue: 255.</span></span> <span data-ttu-id="11f70-139">Alle anderen Teile des Gliederungs Symbols müssen vollständig transparent sein, wobei der Alphakanal auf 0 festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="11f70-139">All other parts of the outline icon must be fully transparent, with the alpha channel set to 0.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/icons/design-icon-dont.png" alt-text="Illustration, die zeigt, wie Sie Ihre APP-Symbole nicht entwerfen." border="false":::

#### <a name="dont-crop-in-a-circular-or-rounded-square-shape"></a><span data-ttu-id="11f70-141">Nicht: Zuschneiden in einer kreisförmigen oder runden quadratischen Form</span><span class="sxs-lookup"><span data-stu-id="11f70-141">Don't: Crop in a circular or rounded square shape</span></span>

<span data-ttu-id="11f70-142">Das in Ihrem App-Paket übermittelte Farbsymbol muss quadratisch sein.</span><span class="sxs-lookup"><span data-stu-id="11f70-142">The color icon submitted in your app package must be square.</span></span> <span data-ttu-id="11f70-143">Runden Sie die Ecken Ihres Symbols nicht ab.</span><span class="sxs-lookup"><span data-stu-id="11f70-143">Don’t round the corners of your icon.</span></span> <span data-ttu-id="11f70-144">Teams passt den Eckenradius automatisch an.</span><span class="sxs-lookup"><span data-stu-id="11f70-144">Teams automatically adjusts the corner radius.</span></span>

   :::column-end:::
:::row-end:::

### <a name="examples"></a><span data-ttu-id="11f70-145">Beispiele</span><span class="sxs-lookup"><span data-stu-id="11f70-145">Examples</span></span>

<span data-ttu-id="11f70-146">Hier erfahren Sie, wie App-Symbole in verschiedenen Teams-Funktionen und Kontexten angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="11f70-146">Here's how app icons appear in different Teams capabilities and contexts.</span></span>

#### <a name="personal-app"></a><span data-ttu-id="11f70-147">Persönliche App</span><span class="sxs-lookup"><span data-stu-id="11f70-147">Personal app</span></span>

:::image type="content" source="../../assets/images/icons/personal-app-icon-example.png" alt-text="Beispiel, das zeigt, wie ein App-Symbol in einer persönlichen App aussieht." border="false":::

#### <a name="bot-channel"></a><span data-ttu-id="11f70-149">Bot (Kanal)</span><span class="sxs-lookup"><span data-stu-id="11f70-149">Bot (channel)</span></span>

:::image type="content" source="../../assets/images/icons/bot-icon-example.png" alt-text="Beispiel, das zeigt, wie ein App-Symbol auf einem bot-Inside-Kanal aussieht." border="false":::

#### <a name="messaging-extension"></a><span data-ttu-id="11f70-151">Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="11f70-151">Messaging extension</span></span>

:::image type="content" source="../../assets/images/icons/messaging-extension-icon-example.png" alt-text="<alt-Text>" border="false":::
