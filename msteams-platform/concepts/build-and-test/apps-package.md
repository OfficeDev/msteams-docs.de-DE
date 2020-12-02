---
title: Verpacken Ihrer APP
description: Erfahren Sie, wie Sie Ihre APP zum Testen, hochladen und veröffentlichen in Microsoft Teams verpacken.
keywords: Apps für Teams-Verpackungen
ms.topic: conceptual
ms.openlocfilehash: 4c20e2c1b3c8d7ef13d16b354449887b3c0f1147
ms.sourcegitcommit: bfdcd122b6b4ffc52d92320d4741f870c07f0542
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "49552570"
---
# <a name="create-an-app-package-for-your-microsoft-teams-app"></a><span data-ttu-id="728bf-104">Erstellen eines App-Pakets für Ihre Microsoft Teams-App</span><span class="sxs-lookup"><span data-stu-id="728bf-104">Create an app package for your Microsoft Teams app</span></span>

<span data-ttu-id="728bf-105">Apps in Microsoft Teams werden durch eine JSON-Datei für App-Manifeste definiert und in einem App-Paket mit ihren Symbolen gebündelt.</span><span class="sxs-lookup"><span data-stu-id="728bf-105">Apps in Teams are defined by an app manifest JSON file, and bundled in an app package with their icons.</span></span> <span data-ttu-id="728bf-106">Sie benötigen ein App-Paket, um Ihre APP in Microsoft Teams hochzuladen und zu installieren und entweder im App-Katalog ihrer Branche oder in AppSource zu veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="728bf-106">You'll need an app package to upload and install your app in Teams, and to publish to either your Line of Business app catalog or to AppSource.</span></span>

<span data-ttu-id="728bf-107">Ein Teams-App-Paket ist eine ZIP-Datei, die Folgendes enthält:</span><span class="sxs-lookup"><span data-stu-id="728bf-107">A Teams app package is a .zip file containing the following:</span></span>

* <span data-ttu-id="728bf-108">Eine Manifestdatei mit dem Namen "manifest.json", die Attribute Ihrer APP angibt und auf erforderliche Ressourcen für Ihre Benutzeroberfläche verweist, beispielsweise den Speicherort der Registerkarten-Konfigurationsseite oder die Microsoft App-ID für den bot.</span><span class="sxs-lookup"><span data-stu-id="728bf-108">A manifest file named "manifest.json", which specifies attributes of your app and points to required resources for your experience, such the location of its tab configuration page or the Microsoft app ID for its bot.</span></span>
* <span data-ttu-id="728bf-109">Ein transparentes "Outline"-Symbol und ein vollständiges "Color"-Symbol.</span><span class="sxs-lookup"><span data-stu-id="728bf-109">A transparent "outline" icon and a full "color" icon.</span></span> <span data-ttu-id="728bf-110">Weitere Informationen finden Sie unter [Icons](#icons) weiter unten in diesem Thema.</span><span class="sxs-lookup"><span data-stu-id="728bf-110">See [Icons](#icons) later in this topic for more information.</span></span>

## <a name="creating-a-manifest"></a><span data-ttu-id="728bf-111">Erstellen einer Manifestdatei</span><span class="sxs-lookup"><span data-stu-id="728bf-111">Creating a manifest</span></span>

<span data-ttu-id="728bf-112">*Teams App Studio* kann bei der Konfiguration ihres Manifests behilflich sein.</span><span class="sxs-lookup"><span data-stu-id="728bf-112">*Teams App Studio* can help configure your manifest.</span></span> <span data-ttu-id="728bf-113">App Studio enthält außerdem eine React-Steuerelementbibliothek sowie konfigurierbare Beispiele für Karten.</span><span class="sxs-lookup"><span data-stu-id="728bf-113">It also contains a React control library and configurable samples for cards.</span></span> <span data-ttu-id="728bf-114">Siehe [Übersicht über das App-Studio](~/concepts/build-and-test/app-studio-overview.md).</span><span class="sxs-lookup"><span data-stu-id="728bf-114">See [App Studio Overview](~/concepts/build-and-test/app-studio-overview.md).</span></span>

<span data-ttu-id="728bf-115">Ihre Manifestdatei muss den Namen "manifest.json" tragen und sich auf der obersten Ebene des Upload-Pakets befinden.</span><span class="sxs-lookup"><span data-stu-id="728bf-115">Your manifest file must be named "manifest.json" and be at the top level of the upload package.</span></span> <span data-ttu-id="728bf-116">Beachten Sie, dass zuvor erstellte Manifeste und Pakete möglicherweise eine ältere Version des Schemas unterstützen.</span><span class="sxs-lookup"><span data-stu-id="728bf-116">Note that manifests and packages built previously might support an older version of the schema.</span></span> <span data-ttu-id="728bf-117">Für Microsoft Teams-apps und insbesondere AppSource (ehemals Office Store)-Übermittlung müssen Sie das aktuelle [Manifest-Schema](~/resources/schema/manifest-schema.md)verwenden.</span><span class="sxs-lookup"><span data-stu-id="728bf-117">For Teams apps and especially AppSource (formerly Office Store) submission, you must use the current [manifest schema](~/resources/schema/manifest-schema.md).</span></span>

> [!TIP]
> <span data-ttu-id="728bf-118">Geben Sie das Schema am Anfang des Manifests an, um IntelliSense oder ähnliche Unterstützung aus Ihrem Code-Editor zu aktivieren:</span><span class="sxs-lookup"><span data-stu-id="728bf-118">Specify the schema at the beginning of your manifest to enable IntelliSense or similar support from your code editor:</span></span>
>
> `"$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",`

## <a name="icons"></a><span data-ttu-id="728bf-119">Symbole</span><span class="sxs-lookup"><span data-stu-id="728bf-119">Icons</span></span>

> [!Note]
> <span data-ttu-id="728bf-120">Wenn Ihre APP eine bot-oder Messaging-Erweiterung enthält, werden die Symbole verwendet, die in Ihre bot-Registrierung im bot-Framework hochgeladen werden.</span><span class="sxs-lookup"><span data-stu-id="728bf-120">If your app contains a bot or messaging extension, the icons used will be the icons uploaded to your bot registration in the Bot Framework.</span></span>

<span data-ttu-id="728bf-121">Microsoft Teams benötigt zwei Symbole für Ihre APP-Erfahrung, die innerhalb des Produkts verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="728bf-121">Microsoft Teams requires two icons for your app experience, to be used within the product.</span></span> <span data-ttu-id="728bf-122">Symbole müssen im Paket enthalten sein und über relative Pfade im Manifest referenziert werden.</span><span class="sxs-lookup"><span data-stu-id="728bf-122">Icons must be included in the package and referenced via relative paths in the manifest.</span></span> <span data-ttu-id="728bf-123">Die maximale Länge jedes Pfads beträgt 2048 Bytes, und das Format des Symbols ist. png.</span><span class="sxs-lookup"><span data-stu-id="728bf-123">The maximum length of each path is 2048 bytes, and the format of the icon is .png.</span></span>

### <a name="color"></a><span data-ttu-id="728bf-124">color</span><span class="sxs-lookup"><span data-stu-id="728bf-124">color</span></span>

<span data-ttu-id="728bf-125">Das `color` Symbol wird in Microsoft Teams verwendet (in App-und Tab-Galerien, Bots, Flyouts usw.).</span><span class="sxs-lookup"><span data-stu-id="728bf-125">The `color` icon is used throughout Microsoft Teams (in app and tab galleries, bots, flyouts, and so on).</span></span> <span data-ttu-id="728bf-126">Dieses Symbol sollte 192x192 Pixel sein.</span><span class="sxs-lookup"><span data-stu-id="728bf-126">This icon should be 192x192 pixels.</span></span> <span data-ttu-id="728bf-127">Bei Ihrem Symbol kann es sich um eine beliebige Farbe (oder Farben) handeln, der Hintergrund sollte jedoch ihre Branding-Akzentfarbe sein.</span><span class="sxs-lookup"><span data-stu-id="728bf-127">Your icon can be any color (or colors), but the background should be your branded accent color.</span></span> <span data-ttu-id="728bf-128">Es sollte auch eine kleine Menge von Textabstand um das Symbol verfügen, um das hexagonale Zuschneiden für die bot-Version des Symbols unterzubringen.</span><span class="sxs-lookup"><span data-stu-id="728bf-128">It should also have a small amount of padding surrounding the icon to accommodate the hexagonal cropping for the bot version of the icon.</span></span>

### <a name="outline"></a><span data-ttu-id="728bf-129">outline</span><span class="sxs-lookup"><span data-stu-id="728bf-129">outline</span></span>

<span data-ttu-id="728bf-130">Das `outline` Symbol wird an diesen Stellen verwendet: die APP-Leiste und die Messaging Erweiterungen, die der Benutzer als Favorit markiert hat.</span><span class="sxs-lookup"><span data-stu-id="728bf-130">The `outline` icon is used in these places: the app bar and messaging extensions the user has marked as a "favorite."</span></span> <span data-ttu-id="728bf-131">Dieses Symbol muss 32x32 Pixel sein.</span><span class="sxs-lookup"><span data-stu-id="728bf-131">This icon must be 32x32 pixels.</span></span> <span data-ttu-id="728bf-132">Das Gliederungssymbol muss nur weiß und Transparenz enthalten (keine anderen Farben).</span><span class="sxs-lookup"><span data-stu-id="728bf-132">Your outline icon must contain only white and transparency (no other colors).</span></span> <span data-ttu-id="728bf-133">Das Symbol kann weiß mit transparentem Hintergrund oder transparent mit weißem Hintergrund sein.</span><span class="sxs-lookup"><span data-stu-id="728bf-133">The icon can be white with transparent background or transparent with a white background.</span></span> <span data-ttu-id="728bf-134">Das Symbol für die Gliederung sollte nicht über einen zusätzlichen Textabstand verfügen, der das Symbol umgibt, und sollte so dicht wie möglich abgeschnitten sein, während die 32x32-Bemaßungen weiterhin beibehalten werden.</span><span class="sxs-lookup"><span data-stu-id="728bf-134">The outline icon should not have extra padding surrounding the icon and should be as tightly cropped as possible while still maintaining the 32x32 dimensions.</span></span> <span data-ttu-id="728bf-135">Hier sind einige gute Beispiele:</span><span class="sxs-lookup"><span data-stu-id="728bf-135">Here are a few good examples:</span></span>

![Beispiel-Gliederungssymbole](~/assets/images/icons/sample20x20s.png)

<span data-ttu-id="728bf-137">[! Tipp zum Erstellen eines transparenten Symbols]</span><span class="sxs-lookup"><span data-stu-id="728bf-137">[!TIP to create transparent icon]</span></span>

* <span data-ttu-id="728bf-138">Die Farbe muss in RGB "weiß" sein (rot: 255, grün: 255, blau: 255).</span><span class="sxs-lookup"><span data-stu-id="728bf-138">Color must be "White" in RGB, (Red: 255, Green: 255, Blue: 255).</span></span>
* <span data-ttu-id="728bf-139">Der gesamte andere Teil des Symbols sollte transparent sein.</span><span class="sxs-lookup"><span data-stu-id="728bf-139">All other part of icon should be transparent.</span></span>
* <span data-ttu-id="728bf-140">Für die Übergabe muss das kleine Symbol vollständig transparent sein, mit einem Alphakanalwert von 0 – ein beliebiger anderer Wert ist ein Fehler.</span><span class="sxs-lookup"><span data-stu-id="728bf-140">For passing, small icon must be full transparent with an alpha channel value of 0 — any other value is a fail.</span></span>

<span data-ttu-id="728bf-141">Angenommen, Ihr Unternehmen ist contoso.</span><span class="sxs-lookup"><span data-stu-id="728bf-141">For example, say your company is Contoso.</span></span> <span data-ttu-id="728bf-142">Sie möchten zwei Symbole übermitteln:</span><span class="sxs-lookup"><span data-stu-id="728bf-142">You'd submit two icons:</span></span>

![Symbol Showcase](~/assets/images/framework/framework_submit_icon.png)

<span data-ttu-id="728bf-144">Hier erfahren Sie, wie die Symbole auf der Benutzeroberfläche angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="728bf-144">Here's how the icons would appear in the UI:</span></span>

#### <a name="bot-and-chiclet-in-channel-view"></a><span data-ttu-id="728bf-145">Bot-und chiclet in der Kanalansicht</span><span class="sxs-lookup"><span data-stu-id="728bf-145">Bot and chiclet in Channel view</span></span>

![Bot-und chiclet-UX](~/assets/images/icons/botandchiclet.png)

#### <a name="flyout"></a><span data-ttu-id="728bf-147">Flyout</span><span class="sxs-lookup"><span data-stu-id="728bf-147">Flyout</span></span>

![Beispiel für Contoso-Flyout](~/assets/images/icons/flyout.png)

#### <a name="app-bar-and-home-screen"></a><span data-ttu-id="728bf-149">App-Leiste und Startbildschirm</span><span class="sxs-lookup"><span data-stu-id="728bf-149">App bar and home screen</span></span>

![Beispiel für Contoso-App-Leiste Homescreen](~/assets/images/icons/appbarhomescreen.png)
