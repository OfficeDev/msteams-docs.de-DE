---
title: Kartentypen
description: Beschreibt alle Karten und Kartenaktionen, die Bots in Teams
localization_priority: Normal
keywords: Referenz zu Bots-Karten
ms.topic: reference
ms.openlocfilehash: be38454daac519530d0fdf10b5170e128219f6fc
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140488"
---
# <a name="types-of-cards"></a><span data-ttu-id="9fc12-104">Kartentypen</span><span class="sxs-lookup"><span data-stu-id="9fc12-104">Types of cards</span></span>

<span data-ttu-id="9fc12-105">Adaptive, Hero-, Listen-, Office 365 Connector-, Beleg-, Anmelde- und Miniaturansichtskarten und Kartensammlungen werden in Bots für Microsoft Teams unterstützt.</span><span class="sxs-lookup"><span data-stu-id="9fc12-105">Adaptive, hero, list, Office 365 Connector, receipt, signin, and thumbnail cards and card collections are supported in bots for Microsoft Teams.</span></span> <span data-ttu-id="9fc12-106">Sie basieren auf Vom Bot Framework definierten Karten, aber Teams unterstützt nicht alle Bot Framework-Karten und hat einige eigene hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="9fc12-106">They are based on cards defined by the Bot Framework, but Teams does not support all Bot Framework cards and has added some of its own.</span></span>

<span data-ttu-id="9fc12-107">Bevor Sie die verschiedenen Kartentypen identifizieren, sollten Sie wissen, wie Sie eine Favoritenkarte, Miniaturansichtskarte oder adaptive Karte erstellen.</span><span class="sxs-lookup"><span data-stu-id="9fc12-107">Before you identify the different card types, understand how to create a a hero card, thumbnail card, or Adaptive Card.</span></span>

## <a name="create-a-hero-card-thumbnail-card-or-adaptive-card"></a><span data-ttu-id="9fc12-108">Erstellen einer Favoritenkarte, Miniaturansichtskarte oder adaptiven Karte</span><span class="sxs-lookup"><span data-stu-id="9fc12-108">Create a hero card, thumbnail card, or Adaptive Card</span></span>

<span data-ttu-id="9fc12-109">**So erstellen Sie eine Favoritenkarte, Miniaturansichtskarte oder adaptive Karte aus App Studio**</span><span class="sxs-lookup"><span data-stu-id="9fc12-109">**To create a hero card, thumbnail card, or Adaptive Card from App Studio**</span></span>

1. <span data-ttu-id="9fc12-110">Wechseln Sie von Teams zu **App Studio.**</span><span class="sxs-lookup"><span data-stu-id="9fc12-110">Go to **App Studio** from Teams.</span></span>
1. <span data-ttu-id="9fc12-111">Wählen Sie **den Karten-Editor** aus.</span><span class="sxs-lookup"><span data-stu-id="9fc12-111">Select **Card editor**.</span></span>
1. <span data-ttu-id="9fc12-112">Wählen Sie **"Neue Karte erstellen"** aus.</span><span class="sxs-lookup"><span data-stu-id="9fc12-112">Select **Create a new card**.</span></span>
1. <span data-ttu-id="9fc12-113">Wählen Sie **"Erstellen"** für eine der Karten aus **Hero-Karte,** **Miniaturansichtskarte** oder **adaptiver Karte** aus.</span><span class="sxs-lookup"><span data-stu-id="9fc12-113">Select **Create** for one of the cards from **Hero Card**, **Thumbnail Card**, or **Adaptive Card**.</span></span> <span data-ttu-id="9fc12-114">Die Metadatendetails, Schaltflächen und JSON-, Csharp- und Knotencodebeispiele werden für diese Karte gezeigt.</span><span class="sxs-lookup"><span data-stu-id="9fc12-114">The metadata details, buttons, and json, csharp, and node code examples are shown for that card.</span></span>

    ![Favoritenkartendetails](~/assets/images/Cards/Herocarddetails.png)

1. <span data-ttu-id="9fc12-116">Wählen Sie **"Diese Karte senden" aus.**</span><span class="sxs-lookup"><span data-stu-id="9fc12-116">Select **Send me this card**.</span></span> <span data-ttu-id="9fc12-117">Die Karte wird als Chatnachricht an Sie gesendet.</span><span class="sxs-lookup"><span data-stu-id="9fc12-117">The card is sent to you as a chat message.</span></span>

## <a name="card-examples"></a><span data-ttu-id="9fc12-118">Kartenbeispiele</span><span class="sxs-lookup"><span data-stu-id="9fc12-118">Card examples</span></span>

<span data-ttu-id="9fc12-119">Weitere Informationen zur Verwendung von Karten finden Sie in der Dokumentation für das Bot Builder SDK v3.</span><span class="sxs-lookup"><span data-stu-id="9fc12-119">You can find additional information on how to use cards in the documentation for the Bot Builder SDK v3.</span></span> <span data-ttu-id="9fc12-120">Codebeispiele sind auch im **Microsoft/BotBuilder-Samples-Repository** auf GitHub verfügbar.</span><span class="sxs-lookup"><span data-stu-id="9fc12-120">Code samples are also available in the **Microsoft/BotBuilder-Samples** repository on GitHub.</span></span> <span data-ttu-id="9fc12-121">Es folgen einige Kartenbeispiele:</span><span class="sxs-lookup"><span data-stu-id="9fc12-121">Following are a few card examples:</span></span>

* <span data-ttu-id="9fc12-122">.NET</span><span class="sxs-lookup"><span data-stu-id="9fc12-122">.NET</span></span>
  * <span data-ttu-id="9fc12-123">[Fügen Sie Nachrichten Karten als Anlagen hinzu.](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="9fc12-123">[Add cards as attachments to messages](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true).</span></span>
  * <span data-ttu-id="9fc12-124">[Karten-Beispielcode Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/06.using-cards).</span><span class="sxs-lookup"><span data-stu-id="9fc12-124">[Cards sample code Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/06.using-cards).</span></span>

* <span data-ttu-id="9fc12-125">Node.js</span><span class="sxs-lookup"><span data-stu-id="9fc12-125">Node.js</span></span>
  * <span data-ttu-id="9fc12-126">[Fügen Sie Nachrichten Karten als Anlagen hinzu.](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="9fc12-126">[Add cards as attachments to messages](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true).</span></span>
  * <span data-ttu-id="9fc12-127">[Karten-Beispielcode Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/06.using-cards).</span><span class="sxs-lookup"><span data-stu-id="9fc12-127">[Cards sample code Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/06.using-cards).</span></span>

## <a name="card-types"></a><span data-ttu-id="9fc12-128">Kartentypen</span><span class="sxs-lookup"><span data-stu-id="9fc12-128">Card types</span></span>

<span data-ttu-id="9fc12-129">Sie können unterschiedliche Kartentypen basierend auf Ihren Anwendungsanforderungen identifizieren und verwenden.</span><span class="sxs-lookup"><span data-stu-id="9fc12-129">You can identify and use different types of cards based on your application requirements.</span></span> <span data-ttu-id="9fc12-130">In der folgenden Tabelle sind die Kartentypen aufgeführt, die Ihnen zur Verfügung stehen:</span><span class="sxs-lookup"><span data-stu-id="9fc12-130">The following table shows the types of cards available to you:</span></span>

| <span data-ttu-id="9fc12-131">Kartentyp</span><span class="sxs-lookup"><span data-stu-id="9fc12-131">Card type</span></span> | <span data-ttu-id="9fc12-132">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9fc12-132">Description</span></span> |
| --- | --- |
| [<span data-ttu-id="9fc12-133">Adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="9fc12-133">Adaptive Card</span></span>](#adaptive-card) | <span data-ttu-id="9fc12-134">Diese Karte ist in hohem Maße anpassbar und kann eine beliebige Kombination aus Text, Sprache, Bildern, Schaltflächen und Eingabefeldern enthalten.</span><span class="sxs-lookup"><span data-stu-id="9fc12-134">This card is highly customizable and can contain any combination of text, speech, images, buttons, and input fields.</span></span> |
| [<span data-ttu-id="9fc12-135">Hero-Karte</span><span class="sxs-lookup"><span data-stu-id="9fc12-135">Hero card</span></span>](#hero-card) | <span data-ttu-id="9fc12-136">Diese Karte enthält in der Regel ein einzelnes großes Bild, eine oder mehrere Schaltflächen und eine kleine Textmenge.</span><span class="sxs-lookup"><span data-stu-id="9fc12-136">This card typically contains a single large image, one or more buttons, and a small amount of text.</span></span> |
| [<span data-ttu-id="9fc12-137">Karte auflisten</span><span class="sxs-lookup"><span data-stu-id="9fc12-137">List card</span></span>](#list-card) | <span data-ttu-id="9fc12-138">Diese Karte enthält eine Bildlaufliste von Elementen.</span><span class="sxs-lookup"><span data-stu-id="9fc12-138">This card contains a scrolling list of items.</span></span> |
| [<span data-ttu-id="9fc12-139">Office 365 Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="9fc12-139">Office 365 Connector card</span></span>](#office-365-connector-card) | <span data-ttu-id="9fc12-140">Diese Karte verfügt über ein flexibles Layout mit mehreren Abschnitten, Feldern, Bildern und Aktionen.</span><span class="sxs-lookup"><span data-stu-id="9fc12-140">This card has a flexible layout with multiple sections, fields, images, and actions.</span></span> |
| [<span data-ttu-id="9fc12-141">Belegkarte</span><span class="sxs-lookup"><span data-stu-id="9fc12-141">Receipt card</span></span>](#receipt-card) | <span data-ttu-id="9fc12-142">Diese Karte stellt dem Benutzer einen Beleg bereit.</span><span class="sxs-lookup"><span data-stu-id="9fc12-142">This card provides a receipt to the user.</span></span> |
| [<span data-ttu-id="9fc12-143">Anmeldekarte</span><span class="sxs-lookup"><span data-stu-id="9fc12-143">Signin card</span></span>](#signin-card) | <span data-ttu-id="9fc12-144">Mit dieser Karte kann ein Bot anfordern, dass sich ein Benutzer anmeldet.</span><span class="sxs-lookup"><span data-stu-id="9fc12-144">This card enables a bot to request that a user signs in.</span></span> |
| [<span data-ttu-id="9fc12-145">Miniaturansichtskarte</span><span class="sxs-lookup"><span data-stu-id="9fc12-145">Thumbnail card</span></span>](#thumbnail-card) | <span data-ttu-id="9fc12-146">Diese Karte enthält in der Regel ein einzelnes Miniaturbild, kurzen Text und eine oder mehrere Schaltflächen.</span><span class="sxs-lookup"><span data-stu-id="9fc12-146">This card typically contains a single thumbnail image, some short text, and one or more buttons.</span></span> |
| [<span data-ttu-id="9fc12-147">Kartensammlungen</span><span class="sxs-lookup"><span data-stu-id="9fc12-147">Card collections</span></span>](#card-collections) | <span data-ttu-id="9fc12-148">Diese Kartensammlung wird verwendet, um mehrere Elemente in einer einzigen Antwort zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="9fc12-148">This card collection is used to return multiple items in a single response.</span></span> |

## <a name="common-properties-for-all-cards"></a><span data-ttu-id="9fc12-149">Allgemeine Eigenschaften für alle Karten</span><span class="sxs-lookup"><span data-stu-id="9fc12-149">Common properties for all cards</span></span>

<span data-ttu-id="9fc12-150">Sie können einige allgemeine Eigenschaften durchgehen, die für alle Karten gelten.</span><span class="sxs-lookup"><span data-stu-id="9fc12-150">You can go through some common properties that are applicable to all cards.</span></span>

### <a name="inline-card-images"></a><span data-ttu-id="9fc12-151">Inlinekartenbilder</span><span class="sxs-lookup"><span data-stu-id="9fc12-151">Inline card images</span></span>

<span data-ttu-id="9fc12-152">Die Karte kann ein Inlinebild enthalten, indem ein Link zum öffentlich verfügbaren Bild eingeschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="9fc12-152">The card can contain an inline image by including a link to the publicly available image.</span></span> <span data-ttu-id="9fc12-153">Aus Leistungsgründen wird dringend empfohlen, das Image auf einem öffentlichen Content Delivery Network (CDN) zu hosten.</span><span class="sxs-lookup"><span data-stu-id="9fc12-153">For performance purposes, it is highly recommended you host the image on a public Content Delivery Network (CDN).</span></span>

<span data-ttu-id="9fc12-154">Bilder werden in der Größe nach oben oder unten skaliert, um das Seitenverhältnis für die Abdeckung des Bildbereichs beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="9fc12-154">Images are scaled up or down in size to maintain the aspect ratio for covering the image area.</span></span> <span data-ttu-id="9fc12-155">Bilder werden dann von der Mitte zugeschnitten, um das entsprechende Seitenverhältnis für die Karte zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="9fc12-155">Images are then cropped from center to achieve the appropriate aspect ratio for the card.</span></span>

<span data-ttu-id="9fc12-156">Bilder müssen höchstens 1024×1024 und im PNG-, JPEG- oder GIF-Format vorliegen.</span><span class="sxs-lookup"><span data-stu-id="9fc12-156">Images must be at most 1024×1024 and in PNG, JPEG, or GIF format.</span></span> <span data-ttu-id="9fc12-157">Animierte GIF-Dateien werden nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="9fc12-157">Animated GIF is not supported.</span></span>

<span data-ttu-id="9fc12-158">Die folgende Tabelle enthält die Eigenschaften von Inlinekartenbildern:</span><span class="sxs-lookup"><span data-stu-id="9fc12-158">The following table provides the properties of inline card images:</span></span>

| <span data-ttu-id="9fc12-159">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="9fc12-159">Property</span></span> | <span data-ttu-id="9fc12-160">Typ</span><span class="sxs-lookup"><span data-stu-id="9fc12-160">Type</span></span>  | <span data-ttu-id="9fc12-161">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9fc12-161">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="9fc12-162">url</span><span class="sxs-lookup"><span data-stu-id="9fc12-162">url</span></span> | <span data-ttu-id="9fc12-163">URL</span><span class="sxs-lookup"><span data-stu-id="9fc12-163">URL</span></span> | <span data-ttu-id="9fc12-164">HTTPS-URL zum Bild.</span><span class="sxs-lookup"><span data-stu-id="9fc12-164">HTTPS URL to the image.</span></span> |
| <span data-ttu-id="9fc12-165">alt</span><span class="sxs-lookup"><span data-stu-id="9fc12-165">alt</span></span> | <span data-ttu-id="9fc12-166">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="9fc12-166">String</span></span> | <span data-ttu-id="9fc12-167">Beschreibung des Bilds, auf das zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="9fc12-167">Accessible description of the image.</span></span> |

> [!NOTE]
> <span data-ttu-id="9fc12-168">Wenn eine Karte eine Bild-URL enthält, die vor dem endgültigen Bild umgeleitet wird, wird die Umleitung in der Bild-URL nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="9fc12-168">If a card includes an image URL that is redirected before the final image, the redirect in image URL is not supported.</span></span> <span data-ttu-id="9fc12-169">Dies geschieht für Bilder, die in der öffentlichen Cloud freigegeben sind.</span><span class="sxs-lookup"><span data-stu-id="9fc12-169">This occurs for images shared on the public cloud.</span></span>

### <a name="buttons"></a><span data-ttu-id="9fc12-170">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="9fc12-170">Buttons</span></span>

<span data-ttu-id="9fc12-171">Schaltflächen werden am unteren Rand der Karte gestapelt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="9fc12-171">Buttons are shown stacked at the bottom of the card.</span></span> <span data-ttu-id="9fc12-172">Schaltflächentext befindet sich immer in einer zeile und wird abgeschnitten, wenn der Text die Breite der Schaltfläche überschreitet.</span><span class="sxs-lookup"><span data-stu-id="9fc12-172">Button text is always on a single line and is truncated if the text exceeds the button width.</span></span> <span data-ttu-id="9fc12-173">Zusätzliche Schaltflächen, die über die von der Karte maximal unterstützte Anzahl hinausgehen, werden nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="9fc12-173">Any additional buttons beyond the maximum number supported by the card are not shown.</span></span>

<span data-ttu-id="9fc12-174">Weitere Informationen finden Sie unter [Kartenaktionen.](~/task-modules-and-cards/cards/cards-actions.md)</span><span class="sxs-lookup"><span data-stu-id="9fc12-174">For more information, see [card actions](~/task-modules-and-cards/cards/cards-actions.md).</span></span>

### <a name="card-formatting"></a><span data-ttu-id="9fc12-175">Kartenformatierung</span><span class="sxs-lookup"><span data-stu-id="9fc12-175">Card formatting</span></span>

<span data-ttu-id="9fc12-176">Weitere Informationen zur Textformatierung in Karten finden Sie unter [Kartenformatierung.](~/task-modules-and-cards/cards/cards-format.md)</span><span class="sxs-lookup"><span data-stu-id="9fc12-176">For more information on text formatting in cards, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span>

<span data-ttu-id="9fc12-177">Nachdem Sie die allgemeinen Eigenschaften für alle Karten identifiziert haben, können Sie jetzt mit adaptiven Karten arbeiten, die Ihnen helfen, das Engagement und die Effizienz zu steigern, indem Sie Ihre Aktionen erfordernden Inhalte direkt zu den von Ihnen verwendeten Apps hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="9fc12-177">After identifying the common properties for all cards, you can now work with Adaptive Cards, which help you increase engagement and efficiency by adding your actionable content directly into the apps you use.</span></span>

## <a name="adaptive-card"></a><span data-ttu-id="9fc12-178">Adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="9fc12-178">Adaptive Card</span></span>

> [!VIDEO https://www.youtube-nocookie.com/embed/J12lKt717Ws]

<span data-ttu-id="9fc12-179">Eine adaptive Karte ist eine anpassbare Karte, die eine beliebige Kombination aus Text, Sprache, Bildern, Schaltflächen und Eingabefeldern enthalten kann.</span><span class="sxs-lookup"><span data-stu-id="9fc12-179">An Adaptive Card is a customizable card that can contain any combination of text, speech, images, buttons, and input fields.</span></span> <span data-ttu-id="9fc12-180">Weitere Informationen finden Sie unter [Adaptive Karten v1.2.0.](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0)</span><span class="sxs-lookup"><span data-stu-id="9fc12-180">For more information, see [Adaptive Cards v1.2.0](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0).</span></span>

### <a name="support-for-adaptive-cards"></a><span data-ttu-id="9fc12-181">Unterstützung für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="9fc12-181">Support for Adaptive Cards</span></span>

<span data-ttu-id="9fc12-182">Die folgende Tabelle enthält die Features, die adaptive Karten unterstützen:</span><span class="sxs-lookup"><span data-stu-id="9fc12-182">The following table provides the features that support Adaptive Cards:</span></span>

| <span data-ttu-id="9fc12-183">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="9fc12-183">Bots in Teams</span></span> | <span data-ttu-id="9fc12-184">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="9fc12-184">Messaging extensions</span></span>  | <span data-ttu-id="9fc12-185">Connectors</span><span class="sxs-lookup"><span data-stu-id="9fc12-185">Connectors</span></span> | <span data-ttu-id="9fc12-186">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="9fc12-186">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="9fc12-187">✔</span><span class="sxs-lookup"><span data-stu-id="9fc12-187">✔</span></span> | <span data-ttu-id="9fc12-188">✔</span><span class="sxs-lookup"><span data-stu-id="9fc12-188">✔</span></span> | <span data-ttu-id="9fc12-189">✖</span><span class="sxs-lookup"><span data-stu-id="9fc12-189">✖</span></span> | <span data-ttu-id="9fc12-190">✔</span><span class="sxs-lookup"><span data-stu-id="9fc12-190">✔</span></span> |

> [!NOTE]
> * <span data-ttu-id="9fc12-191">Teams Plattform unterstützt v1.2 oder frühere Features für adaptive Karten.</span><span class="sxs-lookup"><span data-stu-id="9fc12-191">Teams platform supports v1.2 or earlier of Adaptive Card features.</span></span>
> * <span data-ttu-id="9fc12-192">Das Formatieren positiver oder destruktiver Aktionen wird in adaptiven Karten auf der Teams Plattform nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="9fc12-192">Positive or destructive action styling is not supported in Adaptive Cards on the Teams platform.</span></span>
> * <span data-ttu-id="9fc12-193">Medienelemente werden derzeit in adaptiver Karte auf der Teams Plattform nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="9fc12-193">Media elements are currently not supported in Adaptive Card on the Teams platform.</span></span>

### <a name="example-of-adaptive-card"></a><span data-ttu-id="9fc12-194">Beispiel für adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="9fc12-194">Example of Adaptive Card</span></span>

![Beispiel für eine adaptive Karte](~/assets/images/cards/adaptivecard.png)

<span data-ttu-id="9fc12-196">Der folgende Code zeigt ein Beispiel für eine adaptive Karte:</span><span class="sxs-lookup"><span data-stu-id="9fc12-196">The following code shows an example of an Adaptive Card:</span></span>

```json
{
  "contentType": "application/vnd.microsoft.card.adaptive",
  "content": {
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
      {
        "type": "Container",
        "items": [
          {
            "type": "TextBlock",
            "text": "Publish Adaptive Card schema",
            "weight": "bolder",
            "size": "medium"
          },
          {
            "type": "ColumnSet",
            "columns": [
              {
                "type": "Column",
                "width": "auto",
                "items": [
                  {
                    "type": "Image",
                    "url": "https://pbs.twimg.com/profile_images/3647943215/d7f12830b3c17a5a9e4afcc370e3a37e_400x400.jpeg",
                    "size": "small",
                    "style": "person"
                  }
                ]
              },
              {
                "type": "Column",
                "width": "stretch",
                "items": [
                  {
                    "type": "TextBlock",
                    "text": "Matt Hidinger",
                    "weight": "bolder",
                    "wrap": true
                  },
                  {
                    "type": "TextBlock",
                    "spacing": "none",
                    "text": "Created {{DATE(2017-02-14T06:08:39Z, SHORT)}}",
                    "isSubtle": true,
                    "wrap": true
                  }
                ]
              }
            ]
          }
        ]
      },
      {
        "type": "Container",
        "items": [
          {
            "type": "TextBlock",
            "text": "Now that we have defined the main rules and features of the format, we need to produce a schema and publish it to GitHub. The schema will be the starting point of our reference documentation.",
            "wrap": true
          },
          {
            "type": "FactSet",
            "facts": [
              {
                "title": "Board:",
                "value": "Adaptive Card"
              },
              {
                "title": "List:",
                "value": "Backlog"
              },
              {
                "title": "Assigned to:",
                "value": "Matt Hidinger"
              },
              {
                "title": "Due date:",
                "value": "Not set"
              }
            ]
          }
        ]
      }
    ],
    "actions": [
      {
        "type": "Action.ShowCard",
        "title": "Set due date",
        "card": {
          "type": "AdaptiveCard",
          "body": [
            {
              "type": "Input.Date",
              "id": "dueDate"
            }
          ],
          "actions": [
            {
              "type": "Action.Submit",
              "title": "OK"
            }
          ]
        }
      },
      {
        "type": "Action.ShowCard",
        "title": "Comment",
        "card": {
          "type": "AdaptiveCard",
          "body": [
            {
              "type": "Input.Text",
              "id": "comment",
              "isMultiline": true,
              "placeholder": "Enter your comment"
            }
          ],
          "actions": [
            {
              "type": "Action.Submit",
              "title": "OK"
            }
          ]
        }
      }
    ]
  }  
}
```

#### <a name="additional-information-on-adaptive-cards"></a><span data-ttu-id="9fc12-197">Zusätzliche Informationen zu adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="9fc12-197">Additional information on Adaptive Cards</span></span>

<span data-ttu-id="9fc12-198">Bot Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="9fc12-198">Bot Framework reference:</span></span>

* [<span data-ttu-id="9fc12-199">Knoten "Adaptive Karten"</span><span class="sxs-lookup"><span data-stu-id="9fc12-199">Adaptive Cards Node</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true)
* [<span data-ttu-id="9fc12-200">Adaptive Karte C #</span><span class="sxs-lookup"><span data-stu-id="9fc12-200">Adaptive Card C#</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true)

<span data-ttu-id="9fc12-201">Sie können jetzt mit einer Hero-Karte arbeiten, bei der es sich um eine Mehrzweckkarte handelt, die verwendet wird, um eine potenzielle Benutzerauswahl visuell hervorzuheben.</span><span class="sxs-lookup"><span data-stu-id="9fc12-201">You can now work with a hero card, which is a multipurpose card used to visually highlight a potential user selection.</span></span>

## <a name="hero-card"></a><span data-ttu-id="9fc12-202">Hero-Karte</span><span class="sxs-lookup"><span data-stu-id="9fc12-202">Hero card</span></span>

<span data-ttu-id="9fc12-203">Eine Karte, die in der Regel ein einzelnes großes Bild, eine oder mehrere Schaltflächen und Text enthält.</span><span class="sxs-lookup"><span data-stu-id="9fc12-203">A card that typically contains a single large image, one or more buttons, and text.</span></span>

### <a name="support-for-hero-cards"></a><span data-ttu-id="9fc12-204">Unterstützung für Favoritenkarten</span><span class="sxs-lookup"><span data-stu-id="9fc12-204">Support for hero cards</span></span>

<span data-ttu-id="9fc12-205">Die folgende Tabelle enthält die Features, die Hero-Karten unterstützen:</span><span class="sxs-lookup"><span data-stu-id="9fc12-205">The following table provides the features that support hero cards:</span></span>

| <span data-ttu-id="9fc12-206">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="9fc12-206">Bots in Teams</span></span> | <span data-ttu-id="9fc12-207">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="9fc12-207">Messaging extensions</span></span>  | <span data-ttu-id="9fc12-208">Connectors</span><span class="sxs-lookup"><span data-stu-id="9fc12-208">Connectors</span></span> | <span data-ttu-id="9fc12-209">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="9fc12-209">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="9fc12-210">✔</span><span class="sxs-lookup"><span data-stu-id="9fc12-210">✔</span></span> | <span data-ttu-id="9fc12-211">✔</span><span class="sxs-lookup"><span data-stu-id="9fc12-211">✔</span></span> | <span data-ttu-id="9fc12-212">✖</span><span class="sxs-lookup"><span data-stu-id="9fc12-212">✖</span></span> | <span data-ttu-id="9fc12-213">✔</span><span class="sxs-lookup"><span data-stu-id="9fc12-213">✔</span></span> |

### <a name="properties-of-a-hero-card"></a><span data-ttu-id="9fc12-214">Eigenschaften einer Favoritenkarte</span><span class="sxs-lookup"><span data-stu-id="9fc12-214">Properties of a hero card</span></span>

<span data-ttu-id="9fc12-215">Die folgende Tabelle enthält die Eigenschaften einer Hero-Karte:</span><span class="sxs-lookup"><span data-stu-id="9fc12-215">The following table provides the properties of a hero card:</span></span>

| <span data-ttu-id="9fc12-216">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="9fc12-216">Property</span></span> | <span data-ttu-id="9fc12-217">Typ</span><span class="sxs-lookup"><span data-stu-id="9fc12-217">Type</span></span>  | <span data-ttu-id="9fc12-218">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9fc12-218">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="9fc12-219">title</span><span class="sxs-lookup"><span data-stu-id="9fc12-219">title</span></span> | <span data-ttu-id="9fc12-220">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="9fc12-220">Rich text</span></span> | <span data-ttu-id="9fc12-221">Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="9fc12-221">Title of the card.</span></span> <span data-ttu-id="9fc12-222">Maximal zwei Zeilen.</span><span class="sxs-lookup"><span data-stu-id="9fc12-222">Maximum two lines.</span></span> |
| <span data-ttu-id="9fc12-223">Untertitel</span><span class="sxs-lookup"><span data-stu-id="9fc12-223">subtitle</span></span> | <span data-ttu-id="9fc12-224">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="9fc12-224">Rich text</span></span> | <span data-ttu-id="9fc12-225">Untertitel der Karte.</span><span class="sxs-lookup"><span data-stu-id="9fc12-225">Subtitle of the card.</span></span> <span data-ttu-id="9fc12-226">Maximal zwei Zeilen.</span><span class="sxs-lookup"><span data-stu-id="9fc12-226">Maximum two lines.</span></span>|
| <span data-ttu-id="9fc12-227">text</span><span class="sxs-lookup"><span data-stu-id="9fc12-227">text</span></span> | <span data-ttu-id="9fc12-228">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="9fc12-228">Rich text</span></span> | <span data-ttu-id="9fc12-229">Text wird unter dem Untertitel angezeigt.</span><span class="sxs-lookup"><span data-stu-id="9fc12-229">Text appears under the subtitle.</span></span> <span data-ttu-id="9fc12-230">Formatierungsoptionen finden Sie unter [Kartenformatierung.](~/task-modules-and-cards/cards/cards-format.md)</span><span class="sxs-lookup"><span data-stu-id="9fc12-230">For formatting options, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span> |
| <span data-ttu-id="9fc12-231">Bilder</span><span class="sxs-lookup"><span data-stu-id="9fc12-231">images</span></span> | <span data-ttu-id="9fc12-232">Array von Bildern</span><span class="sxs-lookup"><span data-stu-id="9fc12-232">Array of images</span></span> | <span data-ttu-id="9fc12-233">Bild, das oben auf der Karte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="9fc12-233">Image displayed at the top of the card.</span></span> <span data-ttu-id="9fc12-234">Seitenverhältnis 16:9.</span><span class="sxs-lookup"><span data-stu-id="9fc12-234">Aspect ratio 16:9.</span></span> |
| <span data-ttu-id="9fc12-235">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="9fc12-235">buttons</span></span> | <span data-ttu-id="9fc12-236">Array von Aktionsobjekten</span><span class="sxs-lookup"><span data-stu-id="9fc12-236">Array of action objects</span></span> | <span data-ttu-id="9fc12-237">Aktionssatz, der für die aktuelle Karte gilt.</span><span class="sxs-lookup"><span data-stu-id="9fc12-237">Set of actions applicable to the current card.</span></span> <span data-ttu-id="9fc12-238">Maximal sechs.</span><span class="sxs-lookup"><span data-stu-id="9fc12-238">Maximum six.</span></span> |
| <span data-ttu-id="9fc12-239">Tippen</span><span class="sxs-lookup"><span data-stu-id="9fc12-239">tap</span></span> | <span data-ttu-id="9fc12-240">Action-Objekt</span><span class="sxs-lookup"><span data-stu-id="9fc12-240">Action object</span></span> | <span data-ttu-id="9fc12-241">Wird aktiviert, wenn der Benutzer auf die Karte selbst tippt.</span><span class="sxs-lookup"><span data-stu-id="9fc12-241">Activated when the user taps on the card itself.</span></span> |

### <a name="example-of-a-hero-card"></a><span data-ttu-id="9fc12-242">Beispiel für eine Hero-Karte</span><span class="sxs-lookup"><span data-stu-id="9fc12-242">Example of a hero card</span></span>

![Beispiel für eine Hero-Karte](~/assets/images/cards/hero.png)

<span data-ttu-id="9fc12-244">Der folgende Code zeigt ein Beispiel für eine Hero-Karte:</span><span class="sxs-lookup"><span data-stu-id="9fc12-244">The following code shows an example of a hero card:</span></span>

```json
{
   "contentType": "application/vnd.microsoft.card.hero",
   "content": {
     "title": "Seattle Center Monorail",
     "subtitle": "Seattle Center Monorail",
     "text": "The Seattle Center Monorail is an elevated train line between Seattle Center (near the Space Needle) and downtown Seattle. It was built for the 1962 World's Fair. Its original two trains, completed in 1961, are still in service.",
     "images": [
       {
         "url":"https://upload.wikimedia.org/wikipedia/commons/thumb/4/49/Seattle_monorail01_2008-02-25.jpg/1024px-Seattle_monorail01_2008-02-25.jpg"
       }
     ],
    "buttons": [
      {
         "type": "openUrl",
         "title": "Official website",
         "value": "https://www.seattlemonorail.com"
       },
      {
        "type": "openUrl",
        "title": "Wikipeda page",
        "value": "https://en.wikipedia.org/wiki/Seattle_Center_Monorail"
       }
     ]
   }
}

```

### <a name="additional-information-on-hero-cards"></a><span data-ttu-id="9fc12-245">Zusätzliche Informationen zu Favoritenkarten</span><span class="sxs-lookup"><span data-stu-id="9fc12-245">Additional information on hero cards</span></span>

<span data-ttu-id="9fc12-246">Bot Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="9fc12-246">Bot Framework reference:</span></span>

* [<span data-ttu-id="9fc12-247">Hero card Node.js</span><span class="sxs-lookup"><span data-stu-id="9fc12-247">Hero card Node.js</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-a-hero-card&preserve-view=true)
* [<span data-ttu-id="9fc12-248">Hero-Karte C #</span><span class="sxs-lookup"><span data-stu-id="9fc12-248">Hero card C#</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-hero-card&preserve-view=true)

## <a name="list-card"></a><span data-ttu-id="9fc12-249">Karte auflisten</span><span class="sxs-lookup"><span data-stu-id="9fc12-249">List card</span></span>

<span data-ttu-id="9fc12-250">Die Listenkarte wurde von Teams hinzugefügt, um Funktionen bereitzustellen, die über das hinausgeht, was die Listensammlung bereitstellen kann.</span><span class="sxs-lookup"><span data-stu-id="9fc12-250">The list card has been added by Teams to provide functions beyond what the list collection can provide.</span></span> <span data-ttu-id="9fc12-251">Die Listenkarte enthält eine Bildlaufliste mit Elementen.</span><span class="sxs-lookup"><span data-stu-id="9fc12-251">The list card provides a scrolling list of items.</span></span>

### <a name="support-for-list-cards"></a><span data-ttu-id="9fc12-252">Unterstützung für Listenkarten</span><span class="sxs-lookup"><span data-stu-id="9fc12-252">Support for list cards</span></span>

<span data-ttu-id="9fc12-253">Die folgende Tabelle enthält die Features, die Listenkarten unterstützen:</span><span class="sxs-lookup"><span data-stu-id="9fc12-253">The following table provides the features that support list cards:</span></span>

| <span data-ttu-id="9fc12-254">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="9fc12-254">Bots in Teams</span></span> | <span data-ttu-id="9fc12-255">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="9fc12-255">Messaging extensions</span></span>  | <span data-ttu-id="9fc12-256">Connectors</span><span class="sxs-lookup"><span data-stu-id="9fc12-256">Connectors</span></span> | <span data-ttu-id="9fc12-257">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="9fc12-257">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="9fc12-258">✔</span><span class="sxs-lookup"><span data-stu-id="9fc12-258">✔</span></span> | <span data-ttu-id="9fc12-259">✖</span><span class="sxs-lookup"><span data-stu-id="9fc12-259">✖</span></span> | <span data-ttu-id="9fc12-260">✖</span><span class="sxs-lookup"><span data-stu-id="9fc12-260">✖</span></span> |<span data-ttu-id="9fc12-261">✔</span><span class="sxs-lookup"><span data-stu-id="9fc12-261">✔</span></span> |

### <a name="properties-of-a-list-card"></a><span data-ttu-id="9fc12-262">Eigenschaften einer Listenkarte</span><span class="sxs-lookup"><span data-stu-id="9fc12-262">Properties of a list card</span></span>

<span data-ttu-id="9fc12-263">Die folgende Tabelle enthält die Eigenschaften einer Listenkarte:</span><span class="sxs-lookup"><span data-stu-id="9fc12-263">The following table provides the properties of a list card:</span></span>

| <span data-ttu-id="9fc12-264">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="9fc12-264">Property</span></span> | <span data-ttu-id="9fc12-265">Typ</span><span class="sxs-lookup"><span data-stu-id="9fc12-265">Type</span></span>  | <span data-ttu-id="9fc12-266">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9fc12-266">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="9fc12-267">title</span><span class="sxs-lookup"><span data-stu-id="9fc12-267">title</span></span> | <span data-ttu-id="9fc12-268">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="9fc12-268">Rich text</span></span> | <span data-ttu-id="9fc12-269">Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="9fc12-269">Title of the card.</span></span> <span data-ttu-id="9fc12-270">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="9fc12-270">Maximum 2 lines.</span></span>|
| <span data-ttu-id="9fc12-271">Elemente</span><span class="sxs-lookup"><span data-stu-id="9fc12-271">items</span></span> | <span data-ttu-id="9fc12-272">Array von Listenelementen</span><span class="sxs-lookup"><span data-stu-id="9fc12-272">Array of list items</span></span> | <span data-ttu-id="9fc12-273">Satz von Elementen, die auf die Karte anwendbar sind.</span><span class="sxs-lookup"><span data-stu-id="9fc12-273">Set of items applicable to the card.</span></span>|
| <span data-ttu-id="9fc12-274">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="9fc12-274">buttons</span></span> | <span data-ttu-id="9fc12-275">Array von Aktionsobjekten</span><span class="sxs-lookup"><span data-stu-id="9fc12-275">Array of action objects</span></span> | <span data-ttu-id="9fc12-276">Aktionssatz, der für die aktuelle Karte gilt.</span><span class="sxs-lookup"><span data-stu-id="9fc12-276">Set of actions applicable to the current card.</span></span> <span data-ttu-id="9fc12-277">Maximal 6.</span><span class="sxs-lookup"><span data-stu-id="9fc12-277">Maximum 6.</span></span> |

### <a name="example-of-a-list-card"></a><span data-ttu-id="9fc12-278">Beispiel für eine Listenkarte</span><span class="sxs-lookup"><span data-stu-id="9fc12-278">Example of a list card</span></span>

<span data-ttu-id="9fc12-279">Der folgende Code zeigt ein Beispiel für eine Listenkarte:</span><span class="sxs-lookup"><span data-stu-id="9fc12-279">The following code shows an example of a list card:</span></span>

```json
{
  "contentType": "application/vnd.microsoft.teams.card.list",
  "content": {
    "title": "Card title",
    "items": [
      {
        "type": "file",
        "id": "https://contoso.sharepoint.com/teams/new/Shared%20Documents/Report.xlsx",
        "title": "Report",
        "subtitle": "teams > new > design",
        "tap": {
          "type": "imBack",
          "value": "editOnline https://contoso.sharepoint.com/teams/new/Shared%20Documents/Report.xlsx"
        }
      },
      {
        "type": "resultItem",
        "icon": "https://cdn2.iconfinder.com/data/icons/social-icons-33/128/Trello-128.png",
        "title": "Trello title",
        "subtitle": "A Trello subtitle",
        "tap": {
          "type": "openUrl",
          "value": "http://trello.com"
        }
      },
      {
        "type": "section",
        "title": "Manager"
      },
      {
        "type": "person",
        "id": "JohnDoe@contoso.com",
        "title": "John Doe",
        "subtitle": "Manager",
        "tap": {
          "type": "imBack",
          "value": "whois JohnDoe@contoso.com"
        }
      }
    ],
    "buttons": [
      {
        "type": "imBack",
        "title": "Select",
        "value": "whois"
      }
    ]
  }
}
```

## <a name="office-365-connector-card"></a><span data-ttu-id="9fc12-280">Office 365-Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="9fc12-280">Office 365 connector card</span></span>

<span data-ttu-id="9fc12-281">Sie können mit einer Office 365 Connectorkarte arbeiten, die ein flexibles Layout bietet und eine hervorragende Möglichkeit darstellt, nützliche Informationen zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="9fc12-281">You can work with an Office 365 Connector card that provides a flexible layout and is a great way to get useful information.</span></span> <span data-ttu-id="9fc12-282">Die Office 365 Connectorkarte wird in Teams und nicht in Bot Framework unterstützt.</span><span class="sxs-lookup"><span data-stu-id="9fc12-282">The Office 365 connector card is supported in Teams, not in Bot Framework.</span></span> <span data-ttu-id="9fc12-283">Diese Karte bietet ein flexibles Layout mit mehreren Abschnitten, Feldern, Bildern und Aktionen.</span><span class="sxs-lookup"><span data-stu-id="9fc12-283">This card provides a flexible layout with multiple sections, fields, images, and actions.</span></span> <span data-ttu-id="9fc12-284">Diese Karte enthält eine Connectorkarte, sodass sie von Bots verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="9fc12-284">This card contains a connector card so that it can be used by bots.</span></span> <span data-ttu-id="9fc12-285">Informationen zu Den Unterschieden zwischen Connectorkarten und der Office 365 Connectorkarte finden Sie unter [zusätzliche Informationen auf der Office 365 Connector-Karte.](#additional-information-on-the-office-365-connector-card)</span><span class="sxs-lookup"><span data-stu-id="9fc12-285">For differences between connector cards and the Office 365 Connector card, see [Additional information on the Office 365 Connector card](#additional-information-on-the-office-365-connector-card).</span></span>

### <a name="support-for-office-365-connector-cards"></a><span data-ttu-id="9fc12-286">Unterstützung für Office 365 Connectorkarten</span><span class="sxs-lookup"><span data-stu-id="9fc12-286">Support for Office 365 Connector cards</span></span>

<span data-ttu-id="9fc12-287">Die folgende Tabelle enthält die Features, die Office 365 Connectorkarten unterstützen:</span><span class="sxs-lookup"><span data-stu-id="9fc12-287">The following table provides the features that support Office 365 Connector cards:</span></span>

| <span data-ttu-id="9fc12-288">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="9fc12-288">Bots in Teams</span></span> | <span data-ttu-id="9fc12-289">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="9fc12-289">Messaging extensions</span></span>  | <span data-ttu-id="9fc12-290">Connectors</span><span class="sxs-lookup"><span data-stu-id="9fc12-290">Connectors</span></span> | <span data-ttu-id="9fc12-291">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="9fc12-291">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="9fc12-292">✔</span><span class="sxs-lookup"><span data-stu-id="9fc12-292">✔</span></span> | <span data-ttu-id="9fc12-293">✔</span><span class="sxs-lookup"><span data-stu-id="9fc12-293">✔</span></span> | <span data-ttu-id="9fc12-294">✔</span><span class="sxs-lookup"><span data-stu-id="9fc12-294">✔</span></span> | <span data-ttu-id="9fc12-295">✖</span><span class="sxs-lookup"><span data-stu-id="9fc12-295">✖</span></span> |

### <a name="properties-of-the-office-365-connector-card"></a><span data-ttu-id="9fc12-296">Eigenschaften der Office 365-Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="9fc12-296">Properties of the Office 365 Connector card</span></span>

<span data-ttu-id="9fc12-297">Die folgende Tabelle enthält die Eigenschaften der Office 365 Connectorkarte:</span><span class="sxs-lookup"><span data-stu-id="9fc12-297">The following table provides the properties of the Office 365 connector card:</span></span>

| <span data-ttu-id="9fc12-298">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="9fc12-298">Property</span></span> | <span data-ttu-id="9fc12-299">Typ</span><span class="sxs-lookup"><span data-stu-id="9fc12-299">Type</span></span>  | <span data-ttu-id="9fc12-300">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9fc12-300">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="9fc12-301">title</span><span class="sxs-lookup"><span data-stu-id="9fc12-301">title</span></span> | <span data-ttu-id="9fc12-302">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="9fc12-302">Rich text</span></span> | <span data-ttu-id="9fc12-303">Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="9fc12-303">Title of the card.</span></span> <span data-ttu-id="9fc12-304">Maximal zwei Zeilen.</span><span class="sxs-lookup"><span data-stu-id="9fc12-304">Maximum two lines.</span></span> |
| <span data-ttu-id="9fc12-305">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="9fc12-305">summary</span></span> | <span data-ttu-id="9fc12-306">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="9fc12-306">Rich text</span></span> | <span data-ttu-id="9fc12-307">Zusammenfassung der Karte.</span><span class="sxs-lookup"><span data-stu-id="9fc12-307">Summary of the card.</span></span> <span data-ttu-id="9fc12-308">Maximal zwei Zeilen.</span><span class="sxs-lookup"><span data-stu-id="9fc12-308">Maximum two lines.</span></span> |
| <span data-ttu-id="9fc12-309">text</span><span class="sxs-lookup"><span data-stu-id="9fc12-309">text</span></span> | <span data-ttu-id="9fc12-310">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="9fc12-310">Rich text</span></span> | <span data-ttu-id="9fc12-311">Text wird unter dem Untertitel angezeigt.</span><span class="sxs-lookup"><span data-stu-id="9fc12-311">Text appears under the subtitle.</span></span> <span data-ttu-id="9fc12-312">Formatierungsoptionen finden Sie unter [Kartenformatierung.](~/task-modules-and-cards/cards/cards-format.md)</span><span class="sxs-lookup"><span data-stu-id="9fc12-312">For formatting options, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span> |
| <span data-ttu-id="9fc12-313">themeColor</span><span class="sxs-lookup"><span data-stu-id="9fc12-313">themeColor</span></span> | <span data-ttu-id="9fc12-314">HEX-Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="9fc12-314">HEX string</span></span> | <span data-ttu-id="9fc12-315">Farbe, die die `accentColor` aus dem Anwendungsmanifest bereitgestellte Überschreibung überschreibt.</span><span class="sxs-lookup"><span data-stu-id="9fc12-315">Color that overrides the `accentColor` provided from the application manifest.</span></span> |

### <a name="additional-information-on-the-office-365-connector-card"></a><span data-ttu-id="9fc12-316">Zusätzliche Informationen auf der Office 365 Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="9fc12-316">Additional information on the Office 365 Connector card</span></span>

<span data-ttu-id="9fc12-317">Office 365 Connectorkarten funktionieren ordnungsgemäß in Microsoft Teams, einschließlich [ `ActionCard` Aktionen.](/outlook/actionable-messages/card-reference#actioncard-action)</span><span class="sxs-lookup"><span data-stu-id="9fc12-317">Office 365 Connector cards function properly in Microsoft Teams, including [`ActionCard` actions](/outlook/actionable-messages/card-reference#actioncard-action).</span></span>

<span data-ttu-id="9fc12-318">Der wichtige Unterschied zwischen der Verwendung von Connectorkarten aus einem Connector und der Verwendung von Connectorkarten in Ihrem Bot besteht in der Behandlung von Kartenaktionen.</span><span class="sxs-lookup"><span data-stu-id="9fc12-318">The important difference between using connector cards from a connector and using connector cards in your bot is the handling of card actions.</span></span> <span data-ttu-id="9fc12-319">In der folgenden Tabelle sind die Unterschiede aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="9fc12-319">The following table lists the difference:</span></span>

| <span data-ttu-id="9fc12-320">Connector</span><span class="sxs-lookup"><span data-stu-id="9fc12-320">Connector</span></span> | <span data-ttu-id="9fc12-321">Bot</span><span class="sxs-lookup"><span data-stu-id="9fc12-321">Bot</span></span> |
| --- | --- |
| <span data-ttu-id="9fc12-322">Der Endpunkt empfängt die Kartennutzlast über HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="9fc12-322">The endpoint receives the card payload through HTTP POST.</span></span> | <span data-ttu-id="9fc12-323">Die `HttpPOST` Aktion löst eine Aktivität `invoke` aus, die nur die Aktions-ID und den Textkörper an den Bot sendet.</span><span class="sxs-lookup"><span data-stu-id="9fc12-323">The `HttpPOST` action triggers an `invoke` activity that sends only the action ID and body to the bot.</span></span>|

<span data-ttu-id="9fc12-324">Jede Connectorkarte kann maximal zehn Abschnitte anzeigen, und jeder Abschnitt kann maximal fünf Bilder und fünf Aktionen enthalten.</span><span class="sxs-lookup"><span data-stu-id="9fc12-324">Each connector card can display a maximum of ten sections, and each section can contain a maximum of five images and five actions.</span></span>

> [!NOTE]
> <span data-ttu-id="9fc12-325">Alle zusätzlichen Abschnitte, Bilder oder Aktionen in einer Nachricht werden nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="9fc12-325">Any additional sections, images, or actions in a message do not appear.</span></span>

<span data-ttu-id="9fc12-326">Alle Textfelder unterstützen Markdown und HTML.</span><span class="sxs-lookup"><span data-stu-id="9fc12-326">All text fields support Markdown and HTML.</span></span> <span data-ttu-id="9fc12-327">Sie können steuern, welche Abschnitte Markdown oder HTML verwenden, indem Sie die `markdown` Eigenschaft in einer Nachricht festlegen.</span><span class="sxs-lookup"><span data-stu-id="9fc12-327">You can control which sections use Markdown or HTML by setting the `markdown` property in a message.</span></span> <span data-ttu-id="9fc12-328">Standardmäßig `markdown` ist auf `true` .</span><span class="sxs-lookup"><span data-stu-id="9fc12-328">By default, `markdown` is set to `true`.</span></span> <span data-ttu-id="9fc12-329">Wenn Sie stattdessen HTML verwenden möchten, legen Sie `markdown` dies auf `false` fest.</span><span class="sxs-lookup"><span data-stu-id="9fc12-329">If you want to use HTML instead, set `markdown` to `false`.</span></span>

<span data-ttu-id="9fc12-330">Wenn Sie die `themeColor` Eigenschaft angeben, überschreibt sie die `accentColor` Eigenschaft im App-Manifest.</span><span class="sxs-lookup"><span data-stu-id="9fc12-330">If you specify the `themeColor` property, it overrides the `accentColor` property in the app manifest.</span></span>

<span data-ttu-id="9fc12-331">Um den Renderingstil für `activityImage` anzugeben, können Sie `activityImageType` wie in der folgenden Tabelle dargestellt festlegen:</span><span class="sxs-lookup"><span data-stu-id="9fc12-331">To specify the rendering style for `activityImage`, you can set `activityImageType` as shown in the following table:</span></span>

| <span data-ttu-id="9fc12-332">Wert</span><span class="sxs-lookup"><span data-stu-id="9fc12-332">Value</span></span> | <span data-ttu-id="9fc12-333">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9fc12-333">Description</span></span> |
| --- | --- |
| `avatar` | <span data-ttu-id="9fc12-334">Standard, `activityImage` wird als Kreis zugeschnitten.</span><span class="sxs-lookup"><span data-stu-id="9fc12-334">Default, `activityImage` is cropped as a circle.</span></span> |
| `article` | <span data-ttu-id="9fc12-335">`activityImage` wird als Rechteck angezeigt und behält das Seitenverhältnis bei.</span><span class="sxs-lookup"><span data-stu-id="9fc12-335">`activityImage` is displayed as a rectangle and retains its aspect ratio.</span></span> |

<span data-ttu-id="9fc12-336">Weitere Informationen zu den Eigenschaften der Connectorkarte finden Sie unter [Referenz zu Nachrichtenkarten](/outlook/actionable-messages/card-reference)mit Aktionen.</span><span class="sxs-lookup"><span data-stu-id="9fc12-336">For all other details about connector card properties, see [actionable message card reference](/outlook/actionable-messages/card-reference).</span></span> <span data-ttu-id="9fc12-337">Die einzigen Connectorkarteneigenschaften, die Teams derzeit nicht unterstützt, sind:</span><span class="sxs-lookup"><span data-stu-id="9fc12-337">The only connector card properties that Teams does not currently support are as follows:</span></span>

* `heroImage`
* `hideOriginalBody`
* <span data-ttu-id="9fc12-338">`startGroup`immer wie in Teams behandelt `true`</span><span class="sxs-lookup"><span data-stu-id="9fc12-338">`startGroup` always treated as `true` in Teams</span></span>
* `originator`
* `correlationId`

### <a name="example-of-an-office-365-connector-card"></a><span data-ttu-id="9fc12-339">Beispiel für eine Office 365-Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="9fc12-339">Example of an Office 365 Connector card</span></span>

<span data-ttu-id="9fc12-340">Der folgende Code zeigt ein Beispiel für eine Office 365 Connectorkarte:</span><span class="sxs-lookup"><span data-stu-id="9fc12-340">The following code shows an example of an Office 365 Connector card:</span></span>

```json
{
  "contentType": "application/vnd.microsoft.teams.card.o365connector",
  "content": {
    "@type": "MessageCard",
    "@context": "http://schema.org/extensions",
    "summary": "John Doe commented on Trello",
    "title": "Project Tango",
    "sections": [
        {
            "activityTitle": "John Doe commented",
            "activitySubtitle": "On Project Tango",
            "activityText": "\"Here are the designs\"",
            "activityImage": "http://connectorsdemo.azurewebsites.net/images/MSC12_Oscar_002.jpg"
        },
        {
            "title": "Details",
            "facts": [
                {
                    "name": "Labels",
                    "value": "Designs, redlines"
                },
                {
                    "name": "Due date",
                    "value": "Dec 7, 2016"
                },
                {
                    "name": "Attachments",
                    "value": "[final.jpg](http://connectorsdemo.azurewebsites.net/images/WIN14_Jan_04.jpg)"
                }
            ]
        },
        {
            "title": "Images",
            "images": [
                {
                    "image":"http://connectorsdemo.azurewebsites.net/images/MicrosoftSurface_024_Cafe_OH-06315_VS_R1c.jpg"
                },
                {
                    "image":"http://connectorsdemo.azurewebsites.net/images/WIN12_Scene_01.jpg"
                },
                {
                    "image":"http://connectorsdemo.azurewebsites.net/images/WIN12_Anthony_02.jpg"
                }
            ]
        }
    ],
    "potentialAction": [
        {
            "@context": "http://schema.org",
            "@type": "ViewAction",
            "name": "View in Trello",
            "target": [
                "https://trello.com/c/1101/"
            ]
        }
    ]
  }
}
```

## <a name="receipt-card"></a><span data-ttu-id="9fc12-341">Belegkarte</span><span class="sxs-lookup"><span data-stu-id="9fc12-341">Receipt card</span></span>

<span data-ttu-id="9fc12-342">Teams unterstützt die Belegkarte.</span><span class="sxs-lookup"><span data-stu-id="9fc12-342">Teams supports receipt card.</span></span> <span data-ttu-id="9fc12-343">Es handelt sich um eine Karte, die es einem Bot ermöglicht, dem Benutzer einen Beleg bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="9fc12-343">It is a card that enables a bot to provide a receipt to the user.</span></span> <span data-ttu-id="9fc12-344">Es enthält in der Regel die Liste der Elemente, die in den Beleg aufgenommen werden sollen, z. B. Steuer- und Gesamtinformationen.</span><span class="sxs-lookup"><span data-stu-id="9fc12-344">It typically contains the list of items to include on the receipt, such as tax and total information.</span></span>

### <a name="support-for-receipt-cards"></a><span data-ttu-id="9fc12-345">Unterstützung für Belegkarten</span><span class="sxs-lookup"><span data-stu-id="9fc12-345">Support for receipt cards</span></span>

<span data-ttu-id="9fc12-346">Die folgende Tabelle enthält die Features, die Belegkarten unterstützen:</span><span class="sxs-lookup"><span data-stu-id="9fc12-346">The following table provides the features that support receipt cards:</span></span>

| <span data-ttu-id="9fc12-347">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="9fc12-347">Bots in Teams</span></span> | <span data-ttu-id="9fc12-348">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="9fc12-348">Messaging extensions</span></span>  | <span data-ttu-id="9fc12-349">Connectors</span><span class="sxs-lookup"><span data-stu-id="9fc12-349">Connectors</span></span> | <span data-ttu-id="9fc12-350">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="9fc12-350">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="9fc12-351">✔</span><span class="sxs-lookup"><span data-stu-id="9fc12-351">✔</span></span> | <span data-ttu-id="9fc12-352">✔</span><span class="sxs-lookup"><span data-stu-id="9fc12-352">✔</span></span> | <span data-ttu-id="9fc12-353">✖</span><span class="sxs-lookup"><span data-stu-id="9fc12-353">✖</span></span> | <span data-ttu-id="9fc12-354">✔</span><span class="sxs-lookup"><span data-stu-id="9fc12-354">✔</span></span> |

### <a name="example-of-a-receipt-card"></a><span data-ttu-id="9fc12-355">Beispiel für eine Belegkarte</span><span class="sxs-lookup"><span data-stu-id="9fc12-355">Example of a receipt card</span></span>

![Beispiel für eine Belegkarte](~/assets/images/cards/receipt.png)

<span data-ttu-id="9fc12-357">Der folgende Code zeigt ein Beispiel für eine Belegkarte:</span><span class="sxs-lookup"><span data-stu-id="9fc12-357">The following code shows an example of a receipt card:</span></span>

```json
{
  "contentType": "application/vnd.microsoft.card.receipt",
  "content": {
    "title": "John Doe",
    "facts": [
      {
        "key": "Order Number",
        "value": "1234"
      },
      {
        "key": "Payment Method",
        "value": "VISA 5555-****"
      }
    ],
    "items": [
      {
        "title": "Data Transfer",
        "image": {
          "url": "https://github.com/amido/azure-vector-icons/raw/master/renders/traffic-manager.png"
        },
        "price": "$ 38.45",
        "quantity": "368"
      },
      {
        "title": "App Service",
        "image": {
          "url": "https://github.com/amido/azure-vector-icons/raw/master/renders/cloud-service.png"
        },
        "price": "$ 45.00",
        "quantity": "720"
      }
    ],
    "total": "$ 90.95",
    "tax": "$ 7.50",
    "buttons": [
      {
        "type": "openUrl",
        "title": "More information",
        "image": "https://account.windowsazure.com/content/6.10.1.38-.8225.160809-1618/aux-pre/images/offer-icon-freetrial.png",
        "value": "https://azure.microsoft.com/en-us/pricing/"
      }
    ]
  }
}
```

### <a name="additional-information-on-receipt-cards"></a><span data-ttu-id="9fc12-358">Zusätzliche Informationen zu Belegkarten</span><span class="sxs-lookup"><span data-stu-id="9fc12-358">Additional information on receipt cards</span></span>

<span data-ttu-id="9fc12-359">Bot Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="9fc12-359">Bot Framework reference:</span></span>

* [<span data-ttu-id="9fc12-360">Belegkarte Node.js</span><span class="sxs-lookup"><span data-stu-id="9fc12-360">Receipt card Node.js</span></span>](/javascript/api/botframework-schema/receiptcard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="9fc12-361">Belegkarte C #</span><span class="sxs-lookup"><span data-stu-id="9fc12-361">Receipt card C#</span></span>](/dotnet/api/microsoft.bot.schema.receiptcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="signin-card"></a><span data-ttu-id="9fc12-362">Anmeldekarte</span><span class="sxs-lookup"><span data-stu-id="9fc12-362">Signin card</span></span>

<span data-ttu-id="9fc12-363">Die Anmeldekarte in Teams ähnelt der Anmeldekarte im Bot Framework, mit der Ausnahme, dass die Anmeldekarte in Teams nur zwei Aktionen `signin` und `openUrl` unterstützt.</span><span class="sxs-lookup"><span data-stu-id="9fc12-363">The signin card in Teams is similar to the signin card in the Bot Framework except that the signin card in Teams only supports two actions `signin` and `openUrl`.</span></span>

<span data-ttu-id="9fc12-364">Die Anmeldeaktion kann von jeder Karte in Teams verwendet werden, nicht nur von der Anmeldekarte.</span><span class="sxs-lookup"><span data-stu-id="9fc12-364">The signin action can be used from any card in Teams, not just the signin card.</span></span> <span data-ttu-id="9fc12-365">Weitere Informationen finden Sie unter [Teams Authentifizierungsfluss für Bots.](~/bots/how-to/authentication/auth-flow-bot.md)</span><span class="sxs-lookup"><span data-stu-id="9fc12-365">For more information, see [Teams authentication flow for bots](~/bots/how-to/authentication/auth-flow-bot.md).</span></span>

### <a name="support-for-signin-cards"></a><span data-ttu-id="9fc12-366">Unterstützung für Anmeldekarten</span><span class="sxs-lookup"><span data-stu-id="9fc12-366">Support for signin cards</span></span>

<span data-ttu-id="9fc12-367">Die folgende Tabelle enthält die Features, die Anmeldekarten unterstützen:</span><span class="sxs-lookup"><span data-stu-id="9fc12-367">The following table provides the features that support signin cards:</span></span>

| <span data-ttu-id="9fc12-368">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="9fc12-368">Bots in Teams</span></span> | <span data-ttu-id="9fc12-369">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="9fc12-369">Messaging extensions</span></span>  | <span data-ttu-id="9fc12-370">Connectors</span><span class="sxs-lookup"><span data-stu-id="9fc12-370">Connectors</span></span> | <span data-ttu-id="9fc12-371">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="9fc12-371">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="9fc12-372">✔</span><span class="sxs-lookup"><span data-stu-id="9fc12-372">✔</span></span> | <span data-ttu-id="9fc12-373">✖</span><span class="sxs-lookup"><span data-stu-id="9fc12-373">✖</span></span> | <span data-ttu-id="9fc12-374">✖</span><span class="sxs-lookup"><span data-stu-id="9fc12-374">✖</span></span> | <span data-ttu-id="9fc12-375">✔</span><span class="sxs-lookup"><span data-stu-id="9fc12-375">✔</span></span> |

### <a name="additional-information-on-signin-cards"></a><span data-ttu-id="9fc12-376">Zusätzliche Informationen zu Anmeldekarten</span><span class="sxs-lookup"><span data-stu-id="9fc12-376">Additional information on signin cards</span></span>

<span data-ttu-id="9fc12-377">Bot Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="9fc12-377">Bot Framework reference:</span></span>

* [<span data-ttu-id="9fc12-378">Anmeldekarten-Node.js</span><span class="sxs-lookup"><span data-stu-id="9fc12-378">Signin card Node.js</span></span>](/javascript/api/botframework-schema/signincard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="9fc12-379">Anmeldekarte C #</span><span class="sxs-lookup"><span data-stu-id="9fc12-379">Signin card C#</span></span>](/dotnet/api/microsoft.bot.schema.signincard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="thumbnail-card"></a><span data-ttu-id="9fc12-380">Miniaturansichtskarte</span><span class="sxs-lookup"><span data-stu-id="9fc12-380">Thumbnail card</span></span>

<span data-ttu-id="9fc12-381">Sie können mit einer Miniaturansichtskarte arbeiten, die zum Senden einer einfachen Nachricht mit Aktionen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="9fc12-381">You can work with a thumbnail card that is used for sending a simple actionable message.</span></span> <span data-ttu-id="9fc12-382">Eine Karte, die in der Regel ein einzelnes Miniaturbild, eine oder mehrere Schaltflächen und Text enthält.</span><span class="sxs-lookup"><span data-stu-id="9fc12-382">A card that typically contains a single thumbnail image, one or more buttons, and text.</span></span>

### <a name="support-for-thumbnail-cards"></a><span data-ttu-id="9fc12-383">Unterstützung für Miniaturansichtskarten</span><span class="sxs-lookup"><span data-stu-id="9fc12-383">Support for thumbnail cards</span></span>

<span data-ttu-id="9fc12-384">Die folgende Tabelle enthält die Features, die Miniaturansichtskarten unterstützen:</span><span class="sxs-lookup"><span data-stu-id="9fc12-384">The following table provides the features that support thumbnail cards:</span></span>

| <span data-ttu-id="9fc12-385">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="9fc12-385">Bots in Teams</span></span> | <span data-ttu-id="9fc12-386">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="9fc12-386">Messaging extensions</span></span>  | <span data-ttu-id="9fc12-387">Connectors</span><span class="sxs-lookup"><span data-stu-id="9fc12-387">Connectors</span></span> | <span data-ttu-id="9fc12-388">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="9fc12-388">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="9fc12-389">✔</span><span class="sxs-lookup"><span data-stu-id="9fc12-389">✔</span></span> | <span data-ttu-id="9fc12-390">✔</span><span class="sxs-lookup"><span data-stu-id="9fc12-390">✔</span></span> | <span data-ttu-id="9fc12-391">✖</span><span class="sxs-lookup"><span data-stu-id="9fc12-391">✖</span></span> | <span data-ttu-id="9fc12-392">✔</span><span class="sxs-lookup"><span data-stu-id="9fc12-392">✔</span></span> |

![Beispiel für eine Miniaturansichtskarte](~/assets/images/cards/thumbnail.png)

### <a name="properties-of-a-thumbnail-card"></a><span data-ttu-id="9fc12-394">Eigenschaften einer Miniaturansichtskarte</span><span class="sxs-lookup"><span data-stu-id="9fc12-394">Properties of a thumbnail card</span></span>

<span data-ttu-id="9fc12-395">Die folgende Tabelle enthält die Eigenschaften einer Miniaturansichtskarte:</span><span class="sxs-lookup"><span data-stu-id="9fc12-395">The following table provides the properties of a thumbnail card:</span></span>

| <span data-ttu-id="9fc12-396">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="9fc12-396">Property</span></span> | <span data-ttu-id="9fc12-397">Typ</span><span class="sxs-lookup"><span data-stu-id="9fc12-397">Type</span></span>  | <span data-ttu-id="9fc12-398">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9fc12-398">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="9fc12-399">title</span><span class="sxs-lookup"><span data-stu-id="9fc12-399">title</span></span> | <span data-ttu-id="9fc12-400">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="9fc12-400">Rich text</span></span> | <span data-ttu-id="9fc12-401">Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="9fc12-401">Title of the card.</span></span> <span data-ttu-id="9fc12-402">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="9fc12-402">Maximum 2 lines.</span></span>|
| <span data-ttu-id="9fc12-403">Untertitel</span><span class="sxs-lookup"><span data-stu-id="9fc12-403">subtitle</span></span> | <span data-ttu-id="9fc12-404">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="9fc12-404">Rich text</span></span> | <span data-ttu-id="9fc12-405">Untertitel der Karte.</span><span class="sxs-lookup"><span data-stu-id="9fc12-405">Subtitle of the card.</span></span> <span data-ttu-id="9fc12-406">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="9fc12-406">Maximum 2 lines.</span></span>|
| <span data-ttu-id="9fc12-407">text</span><span class="sxs-lookup"><span data-stu-id="9fc12-407">text</span></span> | <span data-ttu-id="9fc12-408">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="9fc12-408">Rich text</span></span> | <span data-ttu-id="9fc12-409">Text wird unter dem Untertitel angezeigt.</span><span class="sxs-lookup"><span data-stu-id="9fc12-409">Text appears under the subtitle.</span></span> <span data-ttu-id="9fc12-410">Formatierungsoptionen finden Sie unter [Kartenformatierung.](~/task-modules-and-cards/cards/cards-format.md)</span><span class="sxs-lookup"><span data-stu-id="9fc12-410">For formatting options, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span> |
| <span data-ttu-id="9fc12-411">Bilder</span><span class="sxs-lookup"><span data-stu-id="9fc12-411">images</span></span> | <span data-ttu-id="9fc12-412">Array von Bildern</span><span class="sxs-lookup"><span data-stu-id="9fc12-412">Array of images</span></span> | <span data-ttu-id="9fc12-413">Bild, das oben auf der Karte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="9fc12-413">Image displayed at the top of the card.</span></span> <span data-ttu-id="9fc12-414">Seitenverhältnis 1:1 Quadrat.</span><span class="sxs-lookup"><span data-stu-id="9fc12-414">Aspect ratio 1:1 square.</span></span> |
| <span data-ttu-id="9fc12-415">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="9fc12-415">buttons</span></span> | <span data-ttu-id="9fc12-416">Array von Aktionsobjekten</span><span class="sxs-lookup"><span data-stu-id="9fc12-416">Array of action objects</span></span> | <span data-ttu-id="9fc12-417">Aktionssatz, der für die aktuelle Karte gilt.</span><span class="sxs-lookup"><span data-stu-id="9fc12-417">Set of actions applicable to the current card.</span></span> <span data-ttu-id="9fc12-418">Maximal 6.</span><span class="sxs-lookup"><span data-stu-id="9fc12-418">Maximum 6.</span></span> |
| <span data-ttu-id="9fc12-419">Tippen</span><span class="sxs-lookup"><span data-stu-id="9fc12-419">tap</span></span> | <span data-ttu-id="9fc12-420">Action-Objekt</span><span class="sxs-lookup"><span data-stu-id="9fc12-420">Action object</span></span> | <span data-ttu-id="9fc12-421">Wird aktiviert, wenn der Benutzer auf die Karte selbst tippt.</span><span class="sxs-lookup"><span data-stu-id="9fc12-421">Activated when the user taps on the card itself.</span></span> |

### <a name="example-of-a-thumbnail-card"></a><span data-ttu-id="9fc12-422">Beispiel für eine Miniaturansichtskarte</span><span class="sxs-lookup"><span data-stu-id="9fc12-422">Example of a thumbnail card</span></span>

<span data-ttu-id="9fc12-423">Der folgende Code zeigt ein Beispiel für eine Miniaturansichtskarte:</span><span class="sxs-lookup"><span data-stu-id="9fc12-423">The following code shows an example of a thumbnail card:</span></span>

```json
{
  "contentType": "application/vnd.microsoft.card.thumbnail",
  "content": {
    "title": "Bender",
    "subtitle": "tale of a robot who dared to love",
    "text": "Bender Bending Rodríguez is a main character in the animated television series Futurama. He was created by series creators Matt Groening and David X. Cohen, and is voiced by John DiMaggio",
    "images": [
      {
        "url": "https://upload.wikimedia.org/wikipedia/en/a/a6/Bender_Rodriguez.png",
        "alt": "Bender Rodríguez"
      }
    ],
    "buttons": [
      {
        "type": "imBack",
        "title": "Thumbs Up",
        "image": "http://moopz.com/assets_c/2012/06/emoji-thumbs-up-150-thumb-autox125-140616.jpg",
        "value": "I like it"
      },
      {
        "type": "imBack",
        "title": "Thumbs Down",
        "image": "http://yourfaceisstupid.com/wp-content/uploads/2014/08/thumbs-down.png",
        "value": "I don't like it"
      },
      {
        "type": "openUrl",
        "title": "I feel lucky",
        "image": "http://thumb9.shutterstock.com/photos/thumb_large/683806/148441982.jpg",
        "value": "https://www.bing.com/images/search?q=bender&qpvt=bender&qpvt=bender&qpvt=bender&FORM=IGRE"
      }
    ],
    "tap": {
      "type": "imBack",
      "value": "Tapped it!"
    }
  }
}
```

### <a name="additional-information"></a><span data-ttu-id="9fc12-424">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="9fc12-424">Additional information</span></span>

<span data-ttu-id="9fc12-425">Bot Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="9fc12-425">Bot Framework reference:</span></span>

* [<span data-ttu-id="9fc12-426">Miniaturansichtskarte Node.js</span><span class="sxs-lookup"><span data-stu-id="9fc12-426">Thumbnail card Node.js</span></span>](/javascript/api/botframework-schema/thumbnailcard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="9fc12-427">Miniaturansichtskarte C #</span><span class="sxs-lookup"><span data-stu-id="9fc12-427">Thumbnail card C#</span></span>](/dotnet/api/microsoft.bot.schema.thumbnailcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="card-collections"></a><span data-ttu-id="9fc12-428">Kartensammlungen</span><span class="sxs-lookup"><span data-stu-id="9fc12-428">Card collections</span></span>

<span data-ttu-id="9fc12-429">Sie können mit Kartensammlungen arbeiten, die Karussell- und Listensammlungen enthalten.</span><span class="sxs-lookup"><span data-stu-id="9fc12-429">You can work with card collections that include carousel and list collections.</span></span> <span data-ttu-id="9fc12-430">Teams unterstützt Kartensammlungen.</span><span class="sxs-lookup"><span data-stu-id="9fc12-430">Teams supports card collections.</span></span> <span data-ttu-id="9fc12-431">Kartensammlungen enthalten `builder.AttachmentLayout.carousel` und `builder.AttachmentLayout.list` .</span><span class="sxs-lookup"><span data-stu-id="9fc12-431">Card collections include `builder.AttachmentLayout.carousel` and `builder.AttachmentLayout.list`.</span></span> <span data-ttu-id="9fc12-432">Diese Sammlungen enthalten adaptive, Hero- oder Miniaturansichtskarten.</span><span class="sxs-lookup"><span data-stu-id="9fc12-432">These collections contain Adaptive, hero, or thumbnail cards.</span></span>

### <a name="carousel-collection"></a><span data-ttu-id="9fc12-433">Karussellsammlung</span><span class="sxs-lookup"><span data-stu-id="9fc12-433">Carousel collection</span></span>

<span data-ttu-id="9fc12-434">Das [Karusselllayout](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-carousel-of-cards&preserve-view=true) zeigt ein Karussell mit Karten, optional mit zugehörigen Aktionsschaltflächen.</span><span class="sxs-lookup"><span data-stu-id="9fc12-434">The [carousel layout](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-carousel-of-cards&preserve-view=true) shows a carousel of cards, optionally with associated action buttons.</span></span>

#### <a name="support-for-carousel-collections"></a><span data-ttu-id="9fc12-435">Unterstützung für Karussellsammlungen</span><span class="sxs-lookup"><span data-stu-id="9fc12-435">Support for carousel collections</span></span>

<span data-ttu-id="9fc12-436">Die folgende Tabelle enthält die Features, die Karussellsammlungen unterstützen:</span><span class="sxs-lookup"><span data-stu-id="9fc12-436">The following table provides the features that support carousel collections:</span></span>

| <span data-ttu-id="9fc12-437">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="9fc12-437">Bots in Teams</span></span> | <span data-ttu-id="9fc12-438">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="9fc12-438">Messaging extensions</span></span>  | <span data-ttu-id="9fc12-439">Connectors</span><span class="sxs-lookup"><span data-stu-id="9fc12-439">Connectors</span></span> | <span data-ttu-id="9fc12-440">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="9fc12-440">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="9fc12-441">✔</span><span class="sxs-lookup"><span data-stu-id="9fc12-441">✔</span></span> | <span data-ttu-id="9fc12-442">✖</span><span class="sxs-lookup"><span data-stu-id="9fc12-442">✖</span></span> | <span data-ttu-id="9fc12-443">✖</span><span class="sxs-lookup"><span data-stu-id="9fc12-443">✖</span></span> | <span data-ttu-id="9fc12-444">✔</span><span class="sxs-lookup"><span data-stu-id="9fc12-444">✔</span></span> |

> [!NOTE]
> <span data-ttu-id="9fc12-445">Ein Karussell kann maximal zehn Karten pro Nachricht anzeigen.</span><span class="sxs-lookup"><span data-stu-id="9fc12-445">A carousel can display a maximum of ten cards per message.</span></span>

#### <a name="properties-of-a-carousel-card"></a><span data-ttu-id="9fc12-446">Eigenschaften einer Karussellkarte</span><span class="sxs-lookup"><span data-stu-id="9fc12-446">Properties of a carousel card</span></span>

<span data-ttu-id="9fc12-447">Die Eigenschaften einer Karussellkarte sind identisch mit den Favoriten- und Miniaturansichtskarten.</span><span class="sxs-lookup"><span data-stu-id="9fc12-447">Properties of a carousel card are same as the hero and thumbnail cards.</span></span>

#### <a name="example-of-a-carousel-collection"></a><span data-ttu-id="9fc12-448">Beispiel für eine Karussellsammlung</span><span class="sxs-lookup"><span data-stu-id="9fc12-448">Example of a carousel collection</span></span>

![Beispiel für ein Karussell von Karten](~/assets/images/cards/carousel.png)

<span data-ttu-id="9fc12-450">Der folgende Code zeigt ein Beispiel für eine Karussellsammlung:</span><span class="sxs-lookup"><span data-stu-id="9fc12-450">The following code shows an example of a carousel collection:</span></span>

```json
{
 "attachmentLayout": "carousel",
 "attachments":[
    {
      "contentType": "application/vnd.microsoft.card.adaptive",
      "content": {
        "type": "AdaptiveCard",
        "version": "1.0",
        "body": [
          {
            "type": "Container",
            "items": [
              {
                "type": "TextBlock",
                "size": "extraLarge",
                "weight": "bolder",
                "text": "Welcome to Employee Connect",
                "height": "stretch"
              },
              {
                "type": "TextBlock",
                "size": "medium",
                "weight": "bolder",
                "text": "Add events to your calendar",
                "height": "stretch"
              },
              {
                "type": "TextBlock",
                "weight": "bolder",
                "text": "The bot can send \r\rnotification to remind \r\ryou about the latest \r\revents and trainings.",
                "wrap": true,
                "height": "stretch"
              },
              {
                "type": "ColumnSet",
                "columns": [
                  {
                    "type": "Column",
                    "items": [],
                    "height": "stretch"
                  }
                ]
              },
              {
                "type": "ColumnSet",
                "columns": [
                  {
                    "type": "Column",
                    "items": [],
                    "height": "stretch"
                  }
                ]
              }
            ]
          }
        ],
        "actions": [
          {
            "type": "Action.Submit",
            "title": "Let's get started"
          }
        ]
      }
    },
    {
      "contentType": "application/vnd.microsoft.card.adaptive",
      "content": {
        "type": "AdaptiveCard",
        "version": "1.2",
        "body": [
          {
            "type": "Container",
            "items": [
              {
                "type": "TextBlock",
                "size": "large",
                "weight": "bolder",
                "text": "Employee connect"
              },
              {
                "type": "TextBlock",
                "text": "The bot can send notifications \r\rto remind you about the latest \r\r events and trainings",
                "wrap": true,
                "maxWidth": 2
              },
              {
                "type": "ColumnSet",
                "columns": [
                  {
                    "type": "Column",
                    "items": [],
                    "height": "stretch"
                  }
                ]
              },
              {
                "type": "ColumnSet",
                "columns": [
                  {
                    "type": "Column",
                    "items": [],
                    "height": "stretch"
                  }
                ]
              }
            ]
          }
        ],
        "actions": [
          {
            "type": "Action.Submit",
            "title": "Let's get started"
          }
        ]
      }
    },
    {
      "contentType": "application/vnd.microsoft.card.adaptive",
      "content": {
        "type": "AdaptiveCard",
        "version": "1.0",
        "body": [
          {
            "type": "Container",
            "items": [
              {
                "type": "TextBlock",
                "size": "large",
                "weight": "bolder",
                "text": "Employee Connect final"
              },
              {
                "type": "TextBlock",
                "weight": "bolder",
                "text": "Create and manage your tasks",
                "wrap": true
              },
              {
                "type": "TextBlock",
                "text": "The app identifies all your pending tasks \r\r and helps you manage everything at \r\r one place.",
                "wrap": true
              },
              {
                "type": "TextBlock",
                "weight": "bolder",
                "text": "Try these commands \r\r- Pending Submissions \r\r- Pending Approvals- My Tools",
                "wrap": true,
                "height": "stretch"
              }
            ]
          }
        ],
        "actions": [
          {
            "type": "Action.Submit",
            "title": "Let's get started"
          }
        ]
      }
    }
  ]
}
```

#### <a name="syntax-for-carousel-collections"></a><span data-ttu-id="9fc12-451">Syntax für Karussellsammlungen</span><span class="sxs-lookup"><span data-stu-id="9fc12-451">Syntax for carousel collections</span></span>

<span data-ttu-id="9fc12-452">`builder.AttachmentLayoutTypes.Carousel` ist die Syntax für Karussellsammlungen.</span><span class="sxs-lookup"><span data-stu-id="9fc12-452">`builder.AttachmentLayoutTypes.Carousel` is the syntax for carousel collections.</span></span>

### <a name="list-collection"></a><span data-ttu-id="9fc12-453">Sammlung auflisten</span><span class="sxs-lookup"><span data-stu-id="9fc12-453">List collection</span></span>

<span data-ttu-id="9fc12-454">Das Listenlayout zeigt eine vertikal gestapelte Liste von Karten, optional mit zugehörigen Aktionsschaltflächen.</span><span class="sxs-lookup"><span data-stu-id="9fc12-454">The list layout shows a vertically stacked list of cards, optionally with associated action buttons.</span></span>

#### <a name="support-for-list-collections"></a><span data-ttu-id="9fc12-455">Unterstützung für Listensammlungen</span><span class="sxs-lookup"><span data-stu-id="9fc12-455">Support for list collections</span></span>

<span data-ttu-id="9fc12-456">Die folgende Tabelle enthält die Features, die Listensammlungen unterstützen:</span><span class="sxs-lookup"><span data-stu-id="9fc12-456">The following table provides the features that support list collections:</span></span>

| <span data-ttu-id="9fc12-457">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="9fc12-457">Bots in Teams</span></span> | <span data-ttu-id="9fc12-458">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="9fc12-458">Messaging extensions</span></span>  | <span data-ttu-id="9fc12-459">Connectors</span><span class="sxs-lookup"><span data-stu-id="9fc12-459">Connectors</span></span> | <span data-ttu-id="9fc12-460">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="9fc12-460">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="9fc12-461">✔</span><span class="sxs-lookup"><span data-stu-id="9fc12-461">✔</span></span> | <span data-ttu-id="9fc12-462">✔</span><span class="sxs-lookup"><span data-stu-id="9fc12-462">✔</span></span> | <span data-ttu-id="9fc12-463">✖</span><span class="sxs-lookup"><span data-stu-id="9fc12-463">✖</span></span> | <span data-ttu-id="9fc12-464">✔</span><span class="sxs-lookup"><span data-stu-id="9fc12-464">✔</span></span> |

#### <a name="example-of-a-list-collection"></a><span data-ttu-id="9fc12-465">Beispiel für eine Listensammlung</span><span class="sxs-lookup"><span data-stu-id="9fc12-465">Example of a list collection</span></span>

![Beispiel für eine Liste von Karten](~/assets/images/cards/list.png)

<span data-ttu-id="9fc12-467">Die Eigenschaften von Listensammlungen sind identisch mit den Favoriten- oder Miniaturansichtskarten.</span><span class="sxs-lookup"><span data-stu-id="9fc12-467">Properties of list collections are same as the hero or thumbnail cards.</span></span>

<span data-ttu-id="9fc12-468">Eine Liste kann maximal zehn Karten pro Nachricht anzeigen.</span><span class="sxs-lookup"><span data-stu-id="9fc12-468">A list can display a maximum of ten cards per message.</span></span>

> [!NOTE]
> <span data-ttu-id="9fc12-469">Einige Kombinationen von Listenkarten werden unter iOS und Android noch nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="9fc12-469">Some combinations of list cards are not yet supported on iOS and Android.</span></span>

#### <a name="syntax-for-list-collections"></a><span data-ttu-id="9fc12-470">Syntax für Listensammlungen</span><span class="sxs-lookup"><span data-stu-id="9fc12-470">Syntax for list collections</span></span>

<span data-ttu-id="9fc12-471">`builder.AttachmentLayout.list` ist die Syntax für Listensammlungen.</span><span class="sxs-lookup"><span data-stu-id="9fc12-471">`builder.AttachmentLayout.list` is the syntax for list collections.</span></span>

## <a name="cards-not-supported-in-teams"></a><span data-ttu-id="9fc12-472">Karten werden in Teams nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="9fc12-472">Cards not supported in Teams</span></span>

<span data-ttu-id="9fc12-473">Die folgenden Karten werden vom Bot Framework implementiert, aber nicht von Teams unterstützt:</span><span class="sxs-lookup"><span data-stu-id="9fc12-473">The following cards are implemented by the Bot Framework, but are not supported by Teams:</span></span>

* <span data-ttu-id="9fc12-474">Animationskarten</span><span class="sxs-lookup"><span data-stu-id="9fc12-474">Animation cards</span></span>
* <span data-ttu-id="9fc12-475">Audiokarten</span><span class="sxs-lookup"><span data-stu-id="9fc12-475">Audio cards</span></span>
* <span data-ttu-id="9fc12-476">Grafikkarten</span><span class="sxs-lookup"><span data-stu-id="9fc12-476">Video cards</span></span>

## <a name="see-also"></a><span data-ttu-id="9fc12-477">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="9fc12-477">See also</span></span>

* [<span data-ttu-id="9fc12-478">Aufgabenmodule</span><span class="sxs-lookup"><span data-stu-id="9fc12-478">Task modules</span></span>](~/task-modules-and-cards/what-are-task-modules.md)
* [<span data-ttu-id="9fc12-479">Formatieren von Karten</span><span class="sxs-lookup"><span data-stu-id="9fc12-479">Format cards</span></span>](~/task-modules-and-cards/cards/cards-format.md)
