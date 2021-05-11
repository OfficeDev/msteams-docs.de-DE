---
title: Karten-Referenz
description: Beschreibt alle Karten und Kartenaktionen, die Bots in der Teams
localization_priority: Normal
keywords: Bots-Kartenreferenz
ms.topic: reference
ms.openlocfilehash: 1e8cf2e474b8a74f6cab1cd6ef3439924b91892d
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019531"
---
# <a name="cards-reference"></a><span data-ttu-id="f77fa-104">Karten-Referenz</span><span class="sxs-lookup"><span data-stu-id="f77fa-104">Cards reference</span></span>

<span data-ttu-id="f77fa-105">Die in diesem Dokument aufgeführten Karten werden in Bots für Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="f77fa-105">The cards listed in this document are supported in bots for Microsoft Teams.</span></span> <span data-ttu-id="f77fa-106">Sie basieren auf Karten, die vom Bot Framework definiert wurden, aber Teams unterstützt nicht alle Bot Framework-Karten, sondern einige Teams hinzugefügt wurden.</span><span class="sxs-lookup"><span data-stu-id="f77fa-106">They are based on cards defined by the Bot Framework, but Teams does not support all Bot Framework cards and instead some Teams cards have been added.</span></span> <span data-ttu-id="f77fa-107">Unterschiede werden in den Verweisen in diesem Dokument aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="f77fa-107">Differences are called out in the references in this document.</span></span>

## <a name="card-examples"></a><span data-ttu-id="f77fa-108">Kartenbeispiele</span><span class="sxs-lookup"><span data-stu-id="f77fa-108">Card examples</span></span>

<span data-ttu-id="f77fa-109">Weitere Informationen zur Verwendung von Karten finden Sie in der Dokumentation für das Bot Builder SDK v3.</span><span class="sxs-lookup"><span data-stu-id="f77fa-109">You can find additional information on how to use cards in the documentation for the Bot Builder SDK v3.</span></span> <span data-ttu-id="f77fa-110">Codebeispiele sind auch im Microsoft/BotBuilder-Samples-Repository auf GitHub.</span><span class="sxs-lookup"><span data-stu-id="f77fa-110">Code samples are also available in the Microsoft/BotBuilder-Samples repository on GitHub.</span></span>

* <span data-ttu-id="f77fa-111">.NET</span><span class="sxs-lookup"><span data-stu-id="f77fa-111">.NET</span></span>
  * [<span data-ttu-id="f77fa-112">Hinzufügen von Karten als Anlagen zu Nachrichten</span><span class="sxs-lookup"><span data-stu-id="f77fa-112">Add cards as attachments to messages</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true)
  * [<span data-ttu-id="f77fa-113">Kartenbeispielcode Bot Builder v4</span><span class="sxs-lookup"><span data-stu-id="f77fa-113">Cards sample code Bot Builder v4</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/06.using-cards)

* <span data-ttu-id="f77fa-114">Node.js</span><span class="sxs-lookup"><span data-stu-id="f77fa-114">Node.js</span></span>
  * [<span data-ttu-id="f77fa-115">Hinzufügen von Karten als Anlagen zu Nachrichten</span><span class="sxs-lookup"><span data-stu-id="f77fa-115">Add cards as attachments to messages</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true)
  * [<span data-ttu-id="f77fa-116">Kartenbeispielcode Bot Builder v4</span><span class="sxs-lookup"><span data-stu-id="f77fa-116">Cards sample code Bot Builder v4</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/06.using-cards)

## <a name="types-of-cards"></a><span data-ttu-id="f77fa-117">Kartentypen</span><span class="sxs-lookup"><span data-stu-id="f77fa-117">Types of cards</span></span>

<span data-ttu-id="f77fa-118">In dieser Tabelle sind die verfügbaren Kartentypen aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="f77fa-118">This table shows the types of cards available to you:</span></span>

| <span data-ttu-id="f77fa-119">Kartentyp</span><span class="sxs-lookup"><span data-stu-id="f77fa-119">Card type</span></span> | <span data-ttu-id="f77fa-120">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f77fa-120">Description</span></span> |
| --- | --- |
| [<span data-ttu-id="f77fa-121">Adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="f77fa-121">Adaptive card</span></span>](#adaptive-card) | <span data-ttu-id="f77fa-122">Diese Karte ist eine hochgradig anpassbare Karte, die eine beliebige Kombination aus Text, Sprache, Bildern, Schaltflächen und Eingabefeldern enthalten kann.</span><span class="sxs-lookup"><span data-stu-id="f77fa-122">This card is highly customizable card that can contain any combination of text, speech, images, buttons, and input fields.</span></span> |
| [<span data-ttu-id="f77fa-123">Heldenkarte</span><span class="sxs-lookup"><span data-stu-id="f77fa-123">Hero card</span></span>](#hero-card) | <span data-ttu-id="f77fa-124">Diese Karte enthält in der Regel ein einzelnes großes Bild, eine oder mehrere Schaltflächen und eine kleine Textmenge.</span><span class="sxs-lookup"><span data-stu-id="f77fa-124">This card typically contains a single large image, one or more buttons, and a small amount of text.</span></span> |
| [<span data-ttu-id="f77fa-125">Listenkarte</span><span class="sxs-lookup"><span data-stu-id="f77fa-125">List card</span></span>](#list-card) | <span data-ttu-id="f77fa-126">Diese Karte ist eine Bildlaufliste mit Elementen.</span><span class="sxs-lookup"><span data-stu-id="f77fa-126">This card is a scrolling list of items.</span></span> |
| [<span data-ttu-id="f77fa-127">Office 365 Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="f77fa-127">Office 365 connector card</span></span>](#office-365-connector-card) | <span data-ttu-id="f77fa-128">Diese Karte verfügt über ein flexibles Layout mit mehreren Abschnitten, Feldern, Bildern und Aktionen.</span><span class="sxs-lookup"><span data-stu-id="f77fa-128">This card has a flexible layout with multiple sections, fields, images, and actions.</span></span> |
| [<span data-ttu-id="f77fa-129">Belegkarte</span><span class="sxs-lookup"><span data-stu-id="f77fa-129">Receipt card</span></span>](#receipt-card) | <span data-ttu-id="f77fa-130">Diese Karte bietet dem Benutzer eine Quittung.</span><span class="sxs-lookup"><span data-stu-id="f77fa-130">This card provides a receipt to the user.</span></span> |
| [<span data-ttu-id="f77fa-131">Signin-Karte</span><span class="sxs-lookup"><span data-stu-id="f77fa-131">Signin card</span></span>](#signin-card) | <span data-ttu-id="f77fa-132">Mit dieser Karte kann ein Bot anfordern, dass sich ein Benutzer meldet.</span><span class="sxs-lookup"><span data-stu-id="f77fa-132">This card enables a bot to request that a user signs in.</span></span> |
| [<span data-ttu-id="f77fa-133">Miniaturansichtskarte</span><span class="sxs-lookup"><span data-stu-id="f77fa-133">Thumbnail card</span></span>](#thumbnail-card) | <span data-ttu-id="f77fa-134">Diese Karte enthält in der Regel ein einzelnes Miniaturbild, einen kurzen Text und eine oder mehrere Schaltflächen.</span><span class="sxs-lookup"><span data-stu-id="f77fa-134">This card typically contains a single thumbnail image, some short text, and one or more buttons.</span></span> |
| [<span data-ttu-id="f77fa-135">Kartensammlungen</span><span class="sxs-lookup"><span data-stu-id="f77fa-135">Card collections</span></span>](#card-collections) | <span data-ttu-id="f77fa-136">Diese Karten werden verwendet, um mehrere Elemente in einer einzigen Antwort zurück zu geben.</span><span class="sxs-lookup"><span data-stu-id="f77fa-136">This cards is used to return multiple items in a single response.</span></span> |

## <a name="common-properties-for-all-cards"></a><span data-ttu-id="f77fa-137">Allgemeine Eigenschaften für alle Karten</span><span class="sxs-lookup"><span data-stu-id="f77fa-137">Common properties for all cards</span></span>

### <a name="inline-card-images"></a><span data-ttu-id="f77fa-138">Inlinekartenbilder</span><span class="sxs-lookup"><span data-stu-id="f77fa-138">Inline card images</span></span>

<span data-ttu-id="f77fa-139">Die Karte kann ein Inlinebild enthalten, indem sie einen Link zum öffentlich verfügbaren Bild enthält.</span><span class="sxs-lookup"><span data-stu-id="f77fa-139">The card can contain an inline image by including a link to the publicly available image.</span></span> <span data-ttu-id="f77fa-140">Aus Leistungsgründen wird dringend empfohlen, das Bild in einem öffentlichen Netzwerk für die Inhaltszustellung (CDN).</span><span class="sxs-lookup"><span data-stu-id="f77fa-140">For performance purposes, it is highly recommended you host the image on a public content-delivery network (CDN).</span></span>

<span data-ttu-id="f77fa-141">Bilder werden in der Größe nach oben oder unten skaliert, wobei das Seitenverhältnis beibehalten wird, um den Bildbereich zu abdecken.</span><span class="sxs-lookup"><span data-stu-id="f77fa-141">Images are scaled up or down in size while maintaining the aspect ratio to cover the image area.</span></span> <span data-ttu-id="f77fa-142">Bilder werden dann aus der Mitte zugeschnitten, um das entsprechende Seitenverhältnis für die Karte zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="f77fa-142">Images are then cropped from center to achieve the appropriate aspect ratio for the card.</span></span>

<span data-ttu-id="f77fa-143">Bilder müssen mindestens 1024×1024 im PNG-, JPEG- oder GIF-Format vorliegen und keine animierte GIF unterstützen.</span><span class="sxs-lookup"><span data-stu-id="f77fa-143">Images must be at most 1024×1024, in PNG, JPEG, or GIF format, and do not support animated GIF.</span></span>

| <span data-ttu-id="f77fa-144">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="f77fa-144">Property</span></span> | <span data-ttu-id="f77fa-145">Typ</span><span class="sxs-lookup"><span data-stu-id="f77fa-145">Type</span></span>  | <span data-ttu-id="f77fa-146">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f77fa-146">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="f77fa-147">url</span><span class="sxs-lookup"><span data-stu-id="f77fa-147">url</span></span> | <span data-ttu-id="f77fa-148">URL</span><span class="sxs-lookup"><span data-stu-id="f77fa-148">URL</span></span> | <span data-ttu-id="f77fa-149">HTTPS-URL zum Bild.</span><span class="sxs-lookup"><span data-stu-id="f77fa-149">HTTPS URL to the image.</span></span> |
| <span data-ttu-id="f77fa-150">alt</span><span class="sxs-lookup"><span data-stu-id="f77fa-150">alt</span></span> | <span data-ttu-id="f77fa-151">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="f77fa-151">String</span></span> | <span data-ttu-id="f77fa-152">Barrierefreie Beschreibung des Bilds.</span><span class="sxs-lookup"><span data-stu-id="f77fa-152">Accessible description of the image.</span></span> |

> [!NOTE]
> <span data-ttu-id="f77fa-153">Wenn eine Karte eine Bild-URL enthält, die eine Umleitung vor dem endgültigen Bild durchgeht, wird die Umleitung in der Bild-URL nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f77fa-153">If a card includes an image URL that goes through a redirect before the final image, the redirect in image URL is not supported.</span></span> <span data-ttu-id="f77fa-154">Dies tritt für Bilder auf, die in der öffentlichen Cloud freigegeben werden.</span><span class="sxs-lookup"><span data-stu-id="f77fa-154">This occurs for images shared on the public cloud.</span></span>

### <a name="buttons"></a><span data-ttu-id="f77fa-155">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="f77fa-155">Buttons</span></span>

<span data-ttu-id="f77fa-156">Schaltflächen werden am unteren Rand der Karte gestapelt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f77fa-156">Buttons are shown stacked at the bottom of the card.</span></span> <span data-ttu-id="f77fa-157">Der Text der Schaltfläche befindet sich immer in einer einzigen Zeile und wird abgeschnitten, wenn der Text die Breite der Schaltfläche überschreitet.</span><span class="sxs-lookup"><span data-stu-id="f77fa-157">Button text is always on a single line and is truncated if the text exceeds the button width.</span></span> <span data-ttu-id="f77fa-158">Alle zusätzlichen Schaltflächen, die über die maximale Anzahl hinausgehen, die von der Karte unterstützt wird, werden nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f77fa-158">Any additional buttons beyond the maximum number supported by the card are not shown.</span></span>

<span data-ttu-id="f77fa-159">Weitere Informationen finden Sie unter [Kartenaktionen](~/task-modules-and-cards/cards/cards-actions.md).</span><span class="sxs-lookup"><span data-stu-id="f77fa-159">For more information, see [card actions](~/task-modules-and-cards/cards/cards-actions.md).</span></span>

### <a name="card-formatting"></a><span data-ttu-id="f77fa-160">Kartenformatierung</span><span class="sxs-lookup"><span data-stu-id="f77fa-160">Card formatting</span></span>

<span data-ttu-id="f77fa-161">Weitere Informationen zur Textformatierung in Karten finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md).</span><span class="sxs-lookup"><span data-stu-id="f77fa-161">For more information on text formatting in cards, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span>

## <a name="adaptive-card"></a><span data-ttu-id="f77fa-162">Adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="f77fa-162">Adaptive card</span></span>

<span data-ttu-id="f77fa-163">Eine adaptive Karte ist eine anpassbare Karte, die eine beliebige Kombination aus Text, Sprache, Bildern, Schaltflächen und Eingabefeldern enthalten kann.</span><span class="sxs-lookup"><span data-stu-id="f77fa-163">An adaptive card is a customizable card that can contain any combination of text, speech, images, buttons, and input fields.</span></span> <span data-ttu-id="f77fa-164">Siehe [adaptive Karten v1.2.0](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0).</span><span class="sxs-lookup"><span data-stu-id="f77fa-164">See [adaptive cards v1.2.0](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0).</span></span>

### <a name="support-for-adaptive-cards"></a><span data-ttu-id="f77fa-165">Unterstützung für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="f77fa-165">Support for adaptive cards</span></span>

| <span data-ttu-id="f77fa-166">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="f77fa-166">Bots in Teams</span></span> | <span data-ttu-id="f77fa-167">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="f77fa-167">Messaging extensions</span></span>  | <span data-ttu-id="f77fa-168">Connectors</span><span class="sxs-lookup"><span data-stu-id="f77fa-168">Connectors</span></span> | <span data-ttu-id="f77fa-169">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="f77fa-169">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="f77fa-170">✔</span><span class="sxs-lookup"><span data-stu-id="f77fa-170">✔</span></span> | <span data-ttu-id="f77fa-171">✔</span><span class="sxs-lookup"><span data-stu-id="f77fa-171">✔</span></span> | <span data-ttu-id="f77fa-172">✖</span><span class="sxs-lookup"><span data-stu-id="f77fa-172">✖</span></span> | <span data-ttu-id="f77fa-173">✔</span><span class="sxs-lookup"><span data-stu-id="f77fa-173">✔</span></span> |

> [!NOTE]
> * <span data-ttu-id="f77fa-174">Teams Plattform unterstützt v1.2 oder früher adaptive Kartenfeatures.</span><span class="sxs-lookup"><span data-stu-id="f77fa-174">Teams platform supports v1.2 or earlier of adaptive card features.</span></span>
> * <span data-ttu-id="f77fa-175">Medienelemente werden derzeit in der adaptiven Karte v1.2 auf der Teams unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f77fa-175">Media elements are currently not supported in adaptive card v1.2 on the Teams platform.</span></span>

### <a name="example-of-an-adaptive-card"></a><span data-ttu-id="f77fa-176">Beispiel für eine adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="f77fa-176">Example of an adaptive card</span></span>

![Beispiel für eine adaptive Karte](~/assets/images/cards/adaptivecard.png)

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

#### <a name="additional-information-on-adaptive-cards"></a><span data-ttu-id="f77fa-178">Zusätzliche Informationen zu adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="f77fa-178">Additional information on adaptive cards</span></span>

<span data-ttu-id="f77fa-179">Bot Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="f77fa-179">Bot Framework reference:</span></span>

* [<span data-ttu-id="f77fa-180">Adaptive Karten Node.js</span><span class="sxs-lookup"><span data-stu-id="f77fa-180">Adaptive cards Node.js</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true)
* [<span data-ttu-id="f77fa-181">Adaptive Karte C #</span><span class="sxs-lookup"><span data-stu-id="f77fa-181">Adaptive card C#</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true)

## <a name="hero-card"></a><span data-ttu-id="f77fa-182">Heldenkarte</span><span class="sxs-lookup"><span data-stu-id="f77fa-182">Hero card</span></span>

<span data-ttu-id="f77fa-183">Eine Karte, die in der Regel ein einzelnes großes Bild, eine oder mehrere Schaltflächen und Text enthält.</span><span class="sxs-lookup"><span data-stu-id="f77fa-183">A card that typically contains a single large image, one or more buttons, and text.</span></span>

### <a name="support-for-hero-cards"></a><span data-ttu-id="f77fa-184">Unterstützung für Heldenkarten</span><span class="sxs-lookup"><span data-stu-id="f77fa-184">Support for hero cards</span></span>

| <span data-ttu-id="f77fa-185">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="f77fa-185">Bots in Teams</span></span> | <span data-ttu-id="f77fa-186">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="f77fa-186">Messaging extensions</span></span>  | <span data-ttu-id="f77fa-187">Connectors</span><span class="sxs-lookup"><span data-stu-id="f77fa-187">Connectors</span></span> | <span data-ttu-id="f77fa-188">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="f77fa-188">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="f77fa-189">✔</span><span class="sxs-lookup"><span data-stu-id="f77fa-189">✔</span></span> | <span data-ttu-id="f77fa-190">✔</span><span class="sxs-lookup"><span data-stu-id="f77fa-190">✔</span></span> | <span data-ttu-id="f77fa-191">✖</span><span class="sxs-lookup"><span data-stu-id="f77fa-191">✖</span></span> | <span data-ttu-id="f77fa-192">✔</span><span class="sxs-lookup"><span data-stu-id="f77fa-192">✔</span></span> |

### <a name="properties-of-a-hero-card"></a><span data-ttu-id="f77fa-193">Eigenschaften einer Heldenkarte</span><span class="sxs-lookup"><span data-stu-id="f77fa-193">Properties of a hero card</span></span>

| <span data-ttu-id="f77fa-194">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="f77fa-194">Property</span></span> | <span data-ttu-id="f77fa-195">Typ</span><span class="sxs-lookup"><span data-stu-id="f77fa-195">Type</span></span>  | <span data-ttu-id="f77fa-196">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f77fa-196">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="f77fa-197">title</span><span class="sxs-lookup"><span data-stu-id="f77fa-197">title</span></span> | <span data-ttu-id="f77fa-198">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="f77fa-198">Rich text</span></span> | <span data-ttu-id="f77fa-199">Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="f77fa-199">Title of the card.</span></span> <span data-ttu-id="f77fa-200">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="f77fa-200">Maximum 2 lines.</span></span> |
| <span data-ttu-id="f77fa-201">subtitle</span><span class="sxs-lookup"><span data-stu-id="f77fa-201">subtitle</span></span> | <span data-ttu-id="f77fa-202">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="f77fa-202">Rich text</span></span> | <span data-ttu-id="f77fa-203">Untertitel der Karte.</span><span class="sxs-lookup"><span data-stu-id="f77fa-203">Subtitle of the card.</span></span> <span data-ttu-id="f77fa-204">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="f77fa-204">Maximum 2 lines.</span></span>|
| <span data-ttu-id="f77fa-205">text</span><span class="sxs-lookup"><span data-stu-id="f77fa-205">text</span></span> | <span data-ttu-id="f77fa-206">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="f77fa-206">Rich text</span></span> | <span data-ttu-id="f77fa-207">Text wird unter dem Untertitel angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f77fa-207">Text appears under the subtitle.</span></span> <span data-ttu-id="f77fa-208">Formatierungsoptionen finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md).</span><span class="sxs-lookup"><span data-stu-id="f77fa-208">For formatting options, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span> |
| <span data-ttu-id="f77fa-209">Bilder</span><span class="sxs-lookup"><span data-stu-id="f77fa-209">images</span></span> | <span data-ttu-id="f77fa-210">Array von Bildern</span><span class="sxs-lookup"><span data-stu-id="f77fa-210">Array of images</span></span> | <span data-ttu-id="f77fa-211">Bild, das oben auf der Karte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="f77fa-211">Image displayed at the top of the card.</span></span> <span data-ttu-id="f77fa-212">Seitenverhältnis 16:9.</span><span class="sxs-lookup"><span data-stu-id="f77fa-212">Aspect ratio 16:9.</span></span> |
| <span data-ttu-id="f77fa-213">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="f77fa-213">buttons</span></span> | <span data-ttu-id="f77fa-214">Array von Aktionsobjekten</span><span class="sxs-lookup"><span data-stu-id="f77fa-214">Array of action objects</span></span> | <span data-ttu-id="f77fa-215">Aktionssatz, der auf die aktuelle Karte anwendbar ist.</span><span class="sxs-lookup"><span data-stu-id="f77fa-215">Set of actions applicable to the current card.</span></span> <span data-ttu-id="f77fa-216">Maximal 6.</span><span class="sxs-lookup"><span data-stu-id="f77fa-216">Maximum 6.</span></span> |
| <span data-ttu-id="f77fa-217">tippen</span><span class="sxs-lookup"><span data-stu-id="f77fa-217">tap</span></span> | <span data-ttu-id="f77fa-218">Action-Objekt</span><span class="sxs-lookup"><span data-stu-id="f77fa-218">Action object</span></span> | <span data-ttu-id="f77fa-219">Wird aktiviert, wenn der Benutzer auf die Karte selbst tippt.</span><span class="sxs-lookup"><span data-stu-id="f77fa-219">Activated when the user taps on the card itself.</span></span> |

### <a name="example-of-a-hero-card"></a><span data-ttu-id="f77fa-220">Beispiel für eine Heldenkarte</span><span class="sxs-lookup"><span data-stu-id="f77fa-220">Example of a hero card</span></span>

![Beispiel für eine Heldenkarte](~/assets/images/cards/hero.png)

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

### <a name="additional-information-on-hero-cards"></a><span data-ttu-id="f77fa-222">Zusätzliche Informationen zu Heldenkarten</span><span class="sxs-lookup"><span data-stu-id="f77fa-222">Additional information on hero cards</span></span>

<span data-ttu-id="f77fa-223">Bot Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="f77fa-223">Bot Framework reference:</span></span>

* [<span data-ttu-id="f77fa-224">Hero card Node.js</span><span class="sxs-lookup"><span data-stu-id="f77fa-224">Hero card Node.js</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-a-hero-card&preserve-view=true)
* [<span data-ttu-id="f77fa-225">Heldenkarte C #</span><span class="sxs-lookup"><span data-stu-id="f77fa-225">Hero card C#</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-hero-card&preserve-view=true)

## <a name="list-card"></a><span data-ttu-id="f77fa-226">Listenkarte</span><span class="sxs-lookup"><span data-stu-id="f77fa-226">List card</span></span>

<span data-ttu-id="f77fa-227">Die Listenkarte wurde von Teams hinzugefügt, um Funktionen zu bieten, die über das hinaus gehen, was die Listensammlung bereitstellen kann.</span><span class="sxs-lookup"><span data-stu-id="f77fa-227">The list card has been added by Teams to provide functions beyond what the list collection can provide.</span></span> <span data-ttu-id="f77fa-228">Die Listenkarte enthält eine Bildlaufliste mit Elementen.</span><span class="sxs-lookup"><span data-stu-id="f77fa-228">The list card provides a scrolling list of items.</span></span>

### <a name="support-for-list-cards"></a><span data-ttu-id="f77fa-229">Unterstützung für Listenkarten</span><span class="sxs-lookup"><span data-stu-id="f77fa-229">Support for list cards</span></span>

| <span data-ttu-id="f77fa-230">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="f77fa-230">Bots in Teams</span></span> | <span data-ttu-id="f77fa-231">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="f77fa-231">Messaging extensions</span></span>  | <span data-ttu-id="f77fa-232">Connectors</span><span class="sxs-lookup"><span data-stu-id="f77fa-232">Connectors</span></span> | <span data-ttu-id="f77fa-233">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="f77fa-233">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="f77fa-234">✔</span><span class="sxs-lookup"><span data-stu-id="f77fa-234">✔</span></span> | <span data-ttu-id="f77fa-235">✖</span><span class="sxs-lookup"><span data-stu-id="f77fa-235">✖</span></span> | <span data-ttu-id="f77fa-236">✖</span><span class="sxs-lookup"><span data-stu-id="f77fa-236">✖</span></span> |<span data-ttu-id="f77fa-237">✔</span><span class="sxs-lookup"><span data-stu-id="f77fa-237">✔</span></span> |

### <a name="properties-of-a-list-card"></a><span data-ttu-id="f77fa-238">Eigenschaften einer Listenkarte</span><span class="sxs-lookup"><span data-stu-id="f77fa-238">Properties of a list card</span></span>

| <span data-ttu-id="f77fa-239">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="f77fa-239">Property</span></span> | <span data-ttu-id="f77fa-240">Typ</span><span class="sxs-lookup"><span data-stu-id="f77fa-240">Type</span></span>  | <span data-ttu-id="f77fa-241">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f77fa-241">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="f77fa-242">title</span><span class="sxs-lookup"><span data-stu-id="f77fa-242">title</span></span> | <span data-ttu-id="f77fa-243">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="f77fa-243">Rich text</span></span> | <span data-ttu-id="f77fa-244">Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="f77fa-244">Title of the card.</span></span> <span data-ttu-id="f77fa-245">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="f77fa-245">Maximum 2 lines.</span></span>|
| <span data-ttu-id="f77fa-246">Elemente</span><span class="sxs-lookup"><span data-stu-id="f77fa-246">items</span></span> | <span data-ttu-id="f77fa-247">Array von Listenelementen</span><span class="sxs-lookup"><span data-stu-id="f77fa-247">Array of list items</span></span> ||
| <span data-ttu-id="f77fa-248">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="f77fa-248">buttons</span></span> | <span data-ttu-id="f77fa-249">Array von Aktionsobjekten</span><span class="sxs-lookup"><span data-stu-id="f77fa-249">Array of action objects</span></span> | <span data-ttu-id="f77fa-250">Aktionssatz, der auf die aktuelle Karte anwendbar ist.</span><span class="sxs-lookup"><span data-stu-id="f77fa-250">Set of actions applicable to the current card.</span></span> <span data-ttu-id="f77fa-251">Maximal 6.</span><span class="sxs-lookup"><span data-stu-id="f77fa-251">Maximum 6.</span></span> |

### <a name="example-of-a-list-card"></a><span data-ttu-id="f77fa-252">Beispiel für eine Listenkarte</span><span class="sxs-lookup"><span data-stu-id="f77fa-252">Example of a list card</span></span>

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

## <a name="office-365-connector-card"></a><span data-ttu-id="f77fa-253">Office 365 Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="f77fa-253">Office 365 connector card</span></span>

<span data-ttu-id="f77fa-254">Die Office 365 connector card wird in Teams, nicht in Bot Framework unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f77fa-254">The Office 365 connector card is supported in Teams, not in Bot Framework.</span></span> <span data-ttu-id="f77fa-255">Diese Karte bietet ein flexibles Layout mit mehreren Abschnitten, Feldern, Bildern und Aktionen.</span><span class="sxs-lookup"><span data-stu-id="f77fa-255">This card provides a flexible layout with multiple sections, fields, images, and actions.</span></span> <span data-ttu-id="f77fa-256">Diese Karte kapselt eine Connectorkarte, sodass sie von Bots verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="f77fa-256">This card encapsulates a connector card so that it can be used by bots.</span></span> <span data-ttu-id="f77fa-257">Unterschiede zwischen Connectorkarten und der O365-Karte finden Sie unter [Hinweise auf der Office 365 Connectorkarte](#notes-on-the-office-365-connector-card).</span><span class="sxs-lookup"><span data-stu-id="f77fa-257">For differences between connector cards and the O365 card, see [Notes on the Office 365 connector card](#notes-on-the-office-365-connector-card).</span></span>

### <a name="support-for-office-365-connector-cards"></a><span data-ttu-id="f77fa-258">Unterstützung für Office 365 Connectorkarten</span><span class="sxs-lookup"><span data-stu-id="f77fa-258">Support for Office 365 connector cards</span></span>

| <span data-ttu-id="f77fa-259">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="f77fa-259">Bots in Teams</span></span> | <span data-ttu-id="f77fa-260">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="f77fa-260">Messaging extensions</span></span>  | <span data-ttu-id="f77fa-261">Connectors</span><span class="sxs-lookup"><span data-stu-id="f77fa-261">Connectors</span></span> | <span data-ttu-id="f77fa-262">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="f77fa-262">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="f77fa-263">✔</span><span class="sxs-lookup"><span data-stu-id="f77fa-263">✔</span></span> | <span data-ttu-id="f77fa-264">✔</span><span class="sxs-lookup"><span data-stu-id="f77fa-264">✔</span></span> | <span data-ttu-id="f77fa-265">✔</span><span class="sxs-lookup"><span data-stu-id="f77fa-265">✔</span></span> | <span data-ttu-id="f77fa-266">✖</span><span class="sxs-lookup"><span data-stu-id="f77fa-266">✖</span></span> |

### <a name="properties-of-the-office-365-connector-card"></a><span data-ttu-id="f77fa-267">Eigenschaften der Office 365 Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="f77fa-267">Properties of the Office 365 connector card</span></span>

| <span data-ttu-id="f77fa-268">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="f77fa-268">Property</span></span> | <span data-ttu-id="f77fa-269">Typ</span><span class="sxs-lookup"><span data-stu-id="f77fa-269">Type</span></span>  | <span data-ttu-id="f77fa-270">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f77fa-270">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="f77fa-271">title</span><span class="sxs-lookup"><span data-stu-id="f77fa-271">title</span></span> | <span data-ttu-id="f77fa-272">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="f77fa-272">Rich text</span></span> | <span data-ttu-id="f77fa-273">Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="f77fa-273">Title of the card.</span></span> <span data-ttu-id="f77fa-274">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="f77fa-274">Maximum 2 lines.</span></span> |
| <span data-ttu-id="f77fa-275">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="f77fa-275">summary</span></span> | <span data-ttu-id="f77fa-276">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="f77fa-276">Rich text</span></span> | <span data-ttu-id="f77fa-277">Zusammenfassung der Karte.</span><span class="sxs-lookup"><span data-stu-id="f77fa-277">Summary of the card.</span></span> <span data-ttu-id="f77fa-278">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="f77fa-278">Maximum 2 lines.</span></span> |
| <span data-ttu-id="f77fa-279">text</span><span class="sxs-lookup"><span data-stu-id="f77fa-279">text</span></span> | <span data-ttu-id="f77fa-280">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="f77fa-280">Rich text</span></span> | <span data-ttu-id="f77fa-281">Text wird unter dem Untertitel angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f77fa-281">Text appears under the subtitle.</span></span> <span data-ttu-id="f77fa-282">Formatierungsoptionen finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md).</span><span class="sxs-lookup"><span data-stu-id="f77fa-282">For formatting options, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span> |
| <span data-ttu-id="f77fa-283">themeColor</span><span class="sxs-lookup"><span data-stu-id="f77fa-283">themeColor</span></span> | <span data-ttu-id="f77fa-284">HEX-Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="f77fa-284">HEX string</span></span> | <span data-ttu-id="f77fa-285">Farbe, die die im Anwendungsmanifest bereitgestellte accentColor überschreibt.</span><span class="sxs-lookup"><span data-stu-id="f77fa-285">Color that overrides the accentColor provided from the application manifest.</span></span> |

### <a name="notes-on-the-office-365-connector-card"></a><span data-ttu-id="f77fa-286">Hinweise auf der Office 365 Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="f77fa-286">Notes on the Office 365 connector card</span></span>

<span data-ttu-id="f77fa-287">Office 365 Connectorkarten funktionieren ordnungsgemäß in Microsoft Teams, einschließlich [ActionCard-Aktionen](/outlook/actionable-messages/card-reference#actioncard-action).</span><span class="sxs-lookup"><span data-stu-id="f77fa-287">Office 365 connector cards function properly in Microsoft Teams, including [ActionCard actions](/outlook/actionable-messages/card-reference#actioncard-action).</span></span>

<span data-ttu-id="f77fa-288">Ein wichtiger Unterschied zwischen der Verwendung von Connectorkarten von einem Connector und der Verwendung von Connectorkarten in Ihrem Bot ist die Behandlung von Kartenaktionen.</span><span class="sxs-lookup"><span data-stu-id="f77fa-288">One important difference between using connector cards from a connector and using connector cards in your bot is the handling of card actions.</span></span>

* <span data-ttu-id="f77fa-289">Für einen Connector empfängt der Endpunkt die Kartennutzlast über HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="f77fa-289">For a connector, the endpoint receives the card payload through HTTP POST.</span></span>
* <span data-ttu-id="f77fa-290">Bei einem Bot löst die Aktion eine Aktivität aus, die nur die `HttpPOST` `invoke` Aktions-ID und den Textkörper an den Bot sendet.</span><span class="sxs-lookup"><span data-stu-id="f77fa-290">For a bot, the `HttpPOST` action triggers an `invoke` activity that sends only the action ID and body to the bot.</span></span>

<span data-ttu-id="f77fa-291">Jede Connectorkarte kann maximal zehn Abschnitte anzeigen, und jeder Abschnitt kann maximal fünf Bilder und fünf Aktionen enthalten.</span><span class="sxs-lookup"><span data-stu-id="f77fa-291">Each connector card can display a maximum of ten sections, and each section can contain a maximum of five images and five actions.</span></span>

> [!NOTE]
> <span data-ttu-id="f77fa-292">Alle zusätzlichen Abschnitte, Bilder oder Aktionen in einer Nachricht werden nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f77fa-292">Any additional sections, images, or actions in a message do not appear.</span></span>

<span data-ttu-id="f77fa-293">Alle Textfelder unterstützen Markdown und HTML.</span><span class="sxs-lookup"><span data-stu-id="f77fa-293">All text fields support markdown and HTML.</span></span> <span data-ttu-id="f77fa-294">Sie können steuern, welche Abschnitte Markdown oder HTML verwenden, indem Sie `markdown` die Eigenschaft in einer Nachricht festlegen.</span><span class="sxs-lookup"><span data-stu-id="f77fa-294">You can control which sections use markdown or HTML by setting the `markdown` property in a message.</span></span> <span data-ttu-id="f77fa-295">Standardmäßig ist `markdown` auf `true` festgelegt.</span><span class="sxs-lookup"><span data-stu-id="f77fa-295">By default, `markdown` is set to `true`.</span></span> <span data-ttu-id="f77fa-296">Wenn Sie stattdessen HTML verwenden möchten, legen Sie auf `markdown` . `false`</span><span class="sxs-lookup"><span data-stu-id="f77fa-296">If you want to use HTML instead, set `markdown` to `false`.</span></span>

<span data-ttu-id="f77fa-297">Wenn Sie die Eigenschaft `themeColor` angeben, überschreibt sie die `accentColor` Eigenschaft im App-Manifest.</span><span class="sxs-lookup"><span data-stu-id="f77fa-297">If you specify the `themeColor` property, it overrides the `accentColor` property in the app manifest.</span></span>

<span data-ttu-id="f77fa-298">Zum Angeben des Renderingstils für `activityImage` können Sie `activityImageType` folgendes festlegen:</span><span class="sxs-lookup"><span data-stu-id="f77fa-298">To specify the rendering style for `activityImage`, you can set `activityImageType` as follows:</span></span>

| <span data-ttu-id="f77fa-299">Wert</span><span class="sxs-lookup"><span data-stu-id="f77fa-299">Value</span></span> | <span data-ttu-id="f77fa-300">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f77fa-300">Description</span></span> |
| --- | --- |
| `avatar` | <span data-ttu-id="f77fa-301">Standard; `activityImage` wird als Kreis zugeschnitten.</span><span class="sxs-lookup"><span data-stu-id="f77fa-301">Default; `activityImage` is cropped as a circle.</span></span> |
| `article` | <span data-ttu-id="f77fa-302">`activityImage` wird als Rechteck angezeigt und behält das Seitenverhältnis bei.</span><span class="sxs-lookup"><span data-stu-id="f77fa-302">`activityImage` is displayed as a rectangle and retains its aspect ratio.</span></span> |

<span data-ttu-id="f77fa-303">Weitere Informationen zu den Eigenschaften von Connectorkarten finden Sie unter [Referenz zu Nachrichtenkarten mit Aktionen.](/outlook/actionable-messages/card-reference)</span><span class="sxs-lookup"><span data-stu-id="f77fa-303">For all other details about connector card properties, see [actionable message card reference](/outlook/actionable-messages/card-reference).</span></span> <span data-ttu-id="f77fa-304">Die einzigen Connectorkarteneigenschaften, die Microsoft Teams derzeit nicht unterstützen, sind:</span><span class="sxs-lookup"><span data-stu-id="f77fa-304">The only connector card properties that Microsoft Teams does not currently support are as follows:</span></span>

* `heroImage`
* `hideOriginalBody`
* <span data-ttu-id="f77fa-305">`startGroup`immer wie `true` in Teams</span><span class="sxs-lookup"><span data-stu-id="f77fa-305">`startGroup` always treated as `true` in Teams</span></span>
* `originator`
* `correlationId`

### <a name="example-of-an-office-365-connector-card"></a><span data-ttu-id="f77fa-306">Beispiel für eine Office 365 Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="f77fa-306">Example of an Office 365 connector card</span></span>

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

## <a name="receipt-card"></a><span data-ttu-id="f77fa-307">Belegkarte</span><span class="sxs-lookup"><span data-stu-id="f77fa-307">Receipt card</span></span>

<span data-ttu-id="f77fa-308">Teams unterstützt die Belegkarte.</span><span class="sxs-lookup"><span data-stu-id="f77fa-308">Teams supports receipt card.</span></span> <span data-ttu-id="f77fa-309">Es handelt sich um eine Karte, mit der ein Bot dem Benutzer eine Quittung bereitstellen kann.</span><span class="sxs-lookup"><span data-stu-id="f77fa-309">It is a card that enables a bot to provide a receipt to the user.</span></span> <span data-ttu-id="f77fa-310">Sie enthält in der Regel die Liste der Elemente, die in den Beleg aufgenommen werden sollen, z. B. Steuer- und Gesamtinformationen.</span><span class="sxs-lookup"><span data-stu-id="f77fa-310">It typically contains the list of items to include on the receipt, such as tax and total information.</span></span>

### <a name="support-for-receipt-cards"></a><span data-ttu-id="f77fa-311">Unterstützung für Belegkarten</span><span class="sxs-lookup"><span data-stu-id="f77fa-311">Support for receipt cards</span></span>

| <span data-ttu-id="f77fa-312">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="f77fa-312">Bots in Teams</span></span> | <span data-ttu-id="f77fa-313">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="f77fa-313">Messaging extensions</span></span>  | <span data-ttu-id="f77fa-314">Connectors</span><span class="sxs-lookup"><span data-stu-id="f77fa-314">Connectors</span></span> | <span data-ttu-id="f77fa-315">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="f77fa-315">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="f77fa-316">✔</span><span class="sxs-lookup"><span data-stu-id="f77fa-316">✔</span></span> | <span data-ttu-id="f77fa-317">✔</span><span class="sxs-lookup"><span data-stu-id="f77fa-317">✔</span></span> | <span data-ttu-id="f77fa-318">✖</span><span class="sxs-lookup"><span data-stu-id="f77fa-318">✖</span></span> | <span data-ttu-id="f77fa-319">✔</span><span class="sxs-lookup"><span data-stu-id="f77fa-319">✔</span></span> |

### <a name="example-of-a-receipt-card"></a><span data-ttu-id="f77fa-320">Beispiel für eine Belegkarte</span><span class="sxs-lookup"><span data-stu-id="f77fa-320">Example of a receipt card</span></span>

![Beispiel für eine Belegkarte](~/assets/images/cards/receipt.png)

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

### <a name="additional-information-on-receipt-cards"></a><span data-ttu-id="f77fa-322">Zusätzliche Informationen zu Belegkarten</span><span class="sxs-lookup"><span data-stu-id="f77fa-322">Additional information on receipt cards</span></span>

<span data-ttu-id="f77fa-323">Bot Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="f77fa-323">Bot Framework reference:</span></span>

* [<span data-ttu-id="f77fa-324">Belegkarten Node.js</span><span class="sxs-lookup"><span data-stu-id="f77fa-324">Receipt card Node.js</span></span>](/javascript/api/botframework-schema/receiptcard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="f77fa-325">Belegkarte C #</span><span class="sxs-lookup"><span data-stu-id="f77fa-325">Receipt card C#</span></span>](/dotnet/api/microsoft.bot.schema.receiptcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="signin-card"></a><span data-ttu-id="f77fa-326">Signin-Karte</span><span class="sxs-lookup"><span data-stu-id="f77fa-326">Signin card</span></span>

<span data-ttu-id="f77fa-327">Mit der Anmeldekarte kann ein Bot einen Benutzer zur Anmeldung anfordern.</span><span class="sxs-lookup"><span data-stu-id="f77fa-327">Signin card enables a bot to request a user to sign in.</span></span> <span data-ttu-id="f77fa-328">Es wird in Teams in einer etwas anderen Form als im Bot Framework unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f77fa-328">It is supported in Teams in a slightly different form than is found in the Bot Framework.</span></span> <span data-ttu-id="f77fa-329">Die Anmeldekarte in Teams ähnelt der Anmeldekarte im Bot Framework, mit der Ausnahme, dass die Anmeldekarte in Teams nur zwei Aktionen `signin` unterstützt: und `openUrl` .</span><span class="sxs-lookup"><span data-stu-id="f77fa-329">The signin card in Teams is similar to the signin card in the Bot Framework except that the signin card in Teams only supports two actions: `signin` and `openUrl`.</span></span>

<span data-ttu-id="f77fa-330">Die Anmeldeaktion kann von jeder beliebigen Karte in Teams verwendet werden, nicht nur von der Anmeldekarte.</span><span class="sxs-lookup"><span data-stu-id="f77fa-330">The signin action can be used from any card in Teams, not just the signin card.</span></span> <span data-ttu-id="f77fa-331">Weitere Informationen zur Authentifizierung finden Sie [unter Microsoft Teams Authentifizierungsfluss für Bots](~/bots/how-to/authentication/auth-flow-bot.md).</span><span class="sxs-lookup"><span data-stu-id="f77fa-331">For more information on authentication, see [Microsoft Teams authentication flow for bots](~/bots/how-to/authentication/auth-flow-bot.md).</span></span>

### <a name="support-for-signin-cards"></a><span data-ttu-id="f77fa-332">Unterstützung für Anmeldekarten</span><span class="sxs-lookup"><span data-stu-id="f77fa-332">Support for signin cards</span></span>

| <span data-ttu-id="f77fa-333">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="f77fa-333">Bots in Teams</span></span> | <span data-ttu-id="f77fa-334">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="f77fa-334">Messaging extensions</span></span>  | <span data-ttu-id="f77fa-335">Connectors</span><span class="sxs-lookup"><span data-stu-id="f77fa-335">Connectors</span></span> | <span data-ttu-id="f77fa-336">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="f77fa-336">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="f77fa-337">✔</span><span class="sxs-lookup"><span data-stu-id="f77fa-337">✔</span></span> | <span data-ttu-id="f77fa-338">✖</span><span class="sxs-lookup"><span data-stu-id="f77fa-338">✖</span></span> | <span data-ttu-id="f77fa-339">✖</span><span class="sxs-lookup"><span data-stu-id="f77fa-339">✖</span></span> | <span data-ttu-id="f77fa-340">✔</span><span class="sxs-lookup"><span data-stu-id="f77fa-340">✔</span></span> |

### <a name="additional-information-on-signin-cards"></a><span data-ttu-id="f77fa-341">Zusätzliche Informationen zu Anmeldekarten</span><span class="sxs-lookup"><span data-stu-id="f77fa-341">Additional information on signin cards</span></span>

<span data-ttu-id="f77fa-342">Bot Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="f77fa-342">Bot Framework reference:</span></span>

* [<span data-ttu-id="f77fa-343">Signin card Node.js</span><span class="sxs-lookup"><span data-stu-id="f77fa-343">Signin card Node.js</span></span>](/javascript/api/botframework-schema/signincard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="f77fa-344">Signin-Karte C #</span><span class="sxs-lookup"><span data-stu-id="f77fa-344">Signin card C#</span></span>](/dotnet/api/microsoft.bot.schema.signincard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="thumbnail-card"></a><span data-ttu-id="f77fa-345">Miniaturansichtskarte</span><span class="sxs-lookup"><span data-stu-id="f77fa-345">Thumbnail card</span></span>

<span data-ttu-id="f77fa-346">Eine Karte, die in der Regel ein einzelnes Miniaturbild, eine oder mehrere Schaltflächen und Text enthält.</span><span class="sxs-lookup"><span data-stu-id="f77fa-346">A card that typically contains a single thumbnail image, one or more buttons, and text.</span></span>

### <a name="support-for-thumbnail-cards"></a><span data-ttu-id="f77fa-347">Unterstützung für Miniaturansichtskarten</span><span class="sxs-lookup"><span data-stu-id="f77fa-347">Support for thumbnail cards</span></span>

| <span data-ttu-id="f77fa-348">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="f77fa-348">Bots in Teams</span></span> | <span data-ttu-id="f77fa-349">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="f77fa-349">Messaging extensions</span></span>  | <span data-ttu-id="f77fa-350">Connectors</span><span class="sxs-lookup"><span data-stu-id="f77fa-350">Connectors</span></span> | <span data-ttu-id="f77fa-351">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="f77fa-351">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="f77fa-352">✔</span><span class="sxs-lookup"><span data-stu-id="f77fa-352">✔</span></span> | <span data-ttu-id="f77fa-353">✔</span><span class="sxs-lookup"><span data-stu-id="f77fa-353">✔</span></span> | <span data-ttu-id="f77fa-354">✖</span><span class="sxs-lookup"><span data-stu-id="f77fa-354">✖</span></span> | <span data-ttu-id="f77fa-355">✔</span><span class="sxs-lookup"><span data-stu-id="f77fa-355">✔</span></span> |

![Beispiel für eine Miniaturansichtskarte](~/assets/images/cards/thumbnail.png)

### <a name="properties-of-a-thumbnail-card"></a><span data-ttu-id="f77fa-357">Eigenschaften einer Miniaturansichtskarte</span><span class="sxs-lookup"><span data-stu-id="f77fa-357">Properties of a thumbnail card</span></span>

| <span data-ttu-id="f77fa-358">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="f77fa-358">Property</span></span> | <span data-ttu-id="f77fa-359">Typ</span><span class="sxs-lookup"><span data-stu-id="f77fa-359">Type</span></span>  | <span data-ttu-id="f77fa-360">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f77fa-360">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="f77fa-361">title</span><span class="sxs-lookup"><span data-stu-id="f77fa-361">title</span></span> | <span data-ttu-id="f77fa-362">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="f77fa-362">Rich text</span></span> | <span data-ttu-id="f77fa-363">Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="f77fa-363">Title of the card.</span></span> <span data-ttu-id="f77fa-364">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="f77fa-364">Maximum 2 lines.</span></span>|
| <span data-ttu-id="f77fa-365">subtitle</span><span class="sxs-lookup"><span data-stu-id="f77fa-365">subtitle</span></span> | <span data-ttu-id="f77fa-366">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="f77fa-366">Rich text</span></span> | <span data-ttu-id="f77fa-367">Untertitel der Karte.</span><span class="sxs-lookup"><span data-stu-id="f77fa-367">Subtitle of the card.</span></span> <span data-ttu-id="f77fa-368">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="f77fa-368">Maximum 2 lines.</span></span>|
| <span data-ttu-id="f77fa-369">text</span><span class="sxs-lookup"><span data-stu-id="f77fa-369">text</span></span> | <span data-ttu-id="f77fa-370">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="f77fa-370">Rich text</span></span> | <span data-ttu-id="f77fa-371">Text wird unter dem Untertitel angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f77fa-371">Text appears under the subtitle.</span></span> <span data-ttu-id="f77fa-372">Formatierungsoptionen finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md).</span><span class="sxs-lookup"><span data-stu-id="f77fa-372">For formatting options, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span> |
| <span data-ttu-id="f77fa-373">Bilder</span><span class="sxs-lookup"><span data-stu-id="f77fa-373">images</span></span> | <span data-ttu-id="f77fa-374">Array von Bildern</span><span class="sxs-lookup"><span data-stu-id="f77fa-374">Array of images</span></span> | <span data-ttu-id="f77fa-375">Bild, das oben auf der Karte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="f77fa-375">Image displayed at the top of the card.</span></span> <span data-ttu-id="f77fa-376">Seitenverhältnis 1:1 quadratisch.</span><span class="sxs-lookup"><span data-stu-id="f77fa-376">Aspect ratio 1:1 square.</span></span> |
| <span data-ttu-id="f77fa-377">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="f77fa-377">buttons</span></span> | <span data-ttu-id="f77fa-378">Array von Aktionsobjekten</span><span class="sxs-lookup"><span data-stu-id="f77fa-378">Array of action objects</span></span> | <span data-ttu-id="f77fa-379">Aktionssatz, der auf die aktuelle Karte anwendbar ist.</span><span class="sxs-lookup"><span data-stu-id="f77fa-379">Set of actions applicable to the current card.</span></span> <span data-ttu-id="f77fa-380">Maximal 6.</span><span class="sxs-lookup"><span data-stu-id="f77fa-380">Maximum 6.</span></span> |
| <span data-ttu-id="f77fa-381">tippen</span><span class="sxs-lookup"><span data-stu-id="f77fa-381">tap</span></span> | <span data-ttu-id="f77fa-382">Action-Objekt</span><span class="sxs-lookup"><span data-stu-id="f77fa-382">Action object</span></span> | <span data-ttu-id="f77fa-383">Wird aktiviert, wenn der Benutzer auf die Karte selbst tippt.</span><span class="sxs-lookup"><span data-stu-id="f77fa-383">Activated when the user taps on the card itself.</span></span> |

### <a name="example-of-a-thumbnail-card"></a><span data-ttu-id="f77fa-384">Beispiel für eine Miniaturansichtskarte</span><span class="sxs-lookup"><span data-stu-id="f77fa-384">Example of a thumbnail card</span></span>

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

### <a name="additional-information"></a><span data-ttu-id="f77fa-385">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f77fa-385">Additional information</span></span>

<span data-ttu-id="f77fa-386">Bot Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="f77fa-386">Bot Framework reference:</span></span>

* [<span data-ttu-id="f77fa-387">Miniaturansichtskarten Node.js</span><span class="sxs-lookup"><span data-stu-id="f77fa-387">Thumbnail card Node.js</span></span>](/javascript/api/botframework-schema/thumbnailcard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="f77fa-388">Miniaturansichtskarte C #</span><span class="sxs-lookup"><span data-stu-id="f77fa-388">Thumbnail card C#</span></span>](/dotnet/api/microsoft.bot.schema.thumbnailcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="card-collections"></a><span data-ttu-id="f77fa-389">Kartensammlungen</span><span class="sxs-lookup"><span data-stu-id="f77fa-389">Card collections</span></span>

<span data-ttu-id="f77fa-390">Teams unterstützt Kartensammlungen.</span><span class="sxs-lookup"><span data-stu-id="f77fa-390">Teams supports Card collections.</span></span>

<span data-ttu-id="f77fa-391">Kartensammlungen umfassen `builder.AttachmentLayout.carousel` und `builder.AttachmentLayout.list` .</span><span class="sxs-lookup"><span data-stu-id="f77fa-391">Card collections include `builder.AttachmentLayout.carousel` and `builder.AttachmentLayout.list`.</span></span> <span data-ttu-id="f77fa-392">Diese Sammlungen enthalten adaptive, Hero- oder Miniaturansichtskarten.</span><span class="sxs-lookup"><span data-stu-id="f77fa-392">These collections contain adaptive, hero, or thumbnail cards.</span></span>

## <a name="carousel-collection"></a><span data-ttu-id="f77fa-393">Karussellsammlung</span><span class="sxs-lookup"><span data-stu-id="f77fa-393">Carousel collection</span></span>

<span data-ttu-id="f77fa-394">Das [Karusselllayout](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-carousel-of-cards&preserve-view=true) zeigt ein Karussell mit Karten, optional mit zugeordneten Aktionsschaltflächen.</span><span class="sxs-lookup"><span data-stu-id="f77fa-394">The [carousel layout](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-carousel-of-cards&preserve-view=true) shows a carousel of cards, optionally with associated action buttons.</span></span>

### <a name="support-for-carousel-collections"></a><span data-ttu-id="f77fa-395">Unterstützung für Karussellsammlungen</span><span class="sxs-lookup"><span data-stu-id="f77fa-395">Support for carousel collections</span></span>

| <span data-ttu-id="f77fa-396">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="f77fa-396">Bots in Teams</span></span> | <span data-ttu-id="f77fa-397">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="f77fa-397">Messaging extensions</span></span>  | <span data-ttu-id="f77fa-398">Connectors</span><span class="sxs-lookup"><span data-stu-id="f77fa-398">Connectors</span></span> | <span data-ttu-id="f77fa-399">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="f77fa-399">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="f77fa-400">✔</span><span class="sxs-lookup"><span data-stu-id="f77fa-400">✔</span></span> | <span data-ttu-id="f77fa-401">✖</span><span class="sxs-lookup"><span data-stu-id="f77fa-401">✖</span></span> | <span data-ttu-id="f77fa-402">✖</span><span class="sxs-lookup"><span data-stu-id="f77fa-402">✖</span></span> | <span data-ttu-id="f77fa-403">✔</span><span class="sxs-lookup"><span data-stu-id="f77fa-403">✔</span></span> |

> [!NOTE]
> <span data-ttu-id="f77fa-404">Ein Karussell kann maximal zehn Karten pro Nachricht anzeigen.</span><span class="sxs-lookup"><span data-stu-id="f77fa-404">A carousel can display a maximum of ten cards per message.</span></span>

### <a name="properties-of-a-carousel-card"></a><span data-ttu-id="f77fa-405">Eigenschaften einer Karussellkarte</span><span class="sxs-lookup"><span data-stu-id="f77fa-405">Properties of a carousel card</span></span>

<span data-ttu-id="f77fa-406">Die Eigenschaften einer Karussellkarte sind mit denen der Hero- und Miniaturansichtskarten identisch.</span><span class="sxs-lookup"><span data-stu-id="f77fa-406">Properties of a carousel card are same as those of the hero and thumbnail cards.</span></span>

### <a name="example-of-a-carousel-collection"></a><span data-ttu-id="f77fa-407">Beispiel für eine Karussellsammlung</span><span class="sxs-lookup"><span data-stu-id="f77fa-407">Example of a carousel collection</span></span>

![Beispiel für ein Karussell von Karten](~/assets/images/cards/carousel.png)

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

### <a name="syntax-for-carousel-collections"></a><span data-ttu-id="f77fa-409">Syntax für Karussellsammlungen</span><span class="sxs-lookup"><span data-stu-id="f77fa-409">Syntax for carousel collections</span></span>

<span data-ttu-id="f77fa-410">`builder.AttachmentLayoutTypes.Carousel` ist die Syntax für Karussellsammlungen.</span><span class="sxs-lookup"><span data-stu-id="f77fa-410">`builder.AttachmentLayoutTypes.Carousel` is the syntax for carousel collections.</span></span>

## <a name="list-collection"></a><span data-ttu-id="f77fa-411">Listensammlung</span><span class="sxs-lookup"><span data-stu-id="f77fa-411">List collection</span></span>

### <a name="support-for-list-collections"></a><span data-ttu-id="f77fa-412">Unterstützung für Listensammlungen</span><span class="sxs-lookup"><span data-stu-id="f77fa-412">Support for list collections</span></span>

<span data-ttu-id="f77fa-413">Das Listenlayout zeigt eine vertikal gestapelte Liste von Karten, optional mit zugeordneten Aktionsschaltflächen.</span><span class="sxs-lookup"><span data-stu-id="f77fa-413">The list layout shows a vertically stacked list of cards, optionally with associated action buttons.</span></span>

| <span data-ttu-id="f77fa-414">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="f77fa-414">Bots in Teams</span></span> | <span data-ttu-id="f77fa-415">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="f77fa-415">Messaging extensions</span></span>  | <span data-ttu-id="f77fa-416">Connectors</span><span class="sxs-lookup"><span data-stu-id="f77fa-416">Connectors</span></span> | <span data-ttu-id="f77fa-417">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="f77fa-417">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="f77fa-418">✔</span><span class="sxs-lookup"><span data-stu-id="f77fa-418">✔</span></span> | <span data-ttu-id="f77fa-419">✔</span><span class="sxs-lookup"><span data-stu-id="f77fa-419">✔</span></span> | <span data-ttu-id="f77fa-420">✖</span><span class="sxs-lookup"><span data-stu-id="f77fa-420">✖</span></span> | <span data-ttu-id="f77fa-421">✔</span><span class="sxs-lookup"><span data-stu-id="f77fa-421">✔</span></span> |

### <a name="example-of-a-list-collection"></a><span data-ttu-id="f77fa-422">Beispiel für eine Listensammlung</span><span class="sxs-lookup"><span data-stu-id="f77fa-422">Example of a list collection</span></span>

![Beispiel für eine Liste von Karten](~/assets/images/cards/list.png)

<span data-ttu-id="f77fa-424">Die Eigenschaften sind identisch mit der Hero- oder Miniaturansichtskarte.</span><span class="sxs-lookup"><span data-stu-id="f77fa-424">Properties are the same as for the hero or thumbnail card.</span></span>

<span data-ttu-id="f77fa-425">Eine Liste kann maximal zehn Karten pro Nachricht anzeigen.</span><span class="sxs-lookup"><span data-stu-id="f77fa-425">A list can display a maximum of ten cards per message.</span></span>

> [!NOTE]
> <span data-ttu-id="f77fa-426">Einige Kombinationen von Listenkarten werden unter iOS und Android noch nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f77fa-426">Some combinations of list cards are not yet supported on iOS and Android.</span></span>

### <a name="syntax-for-list-collections"></a><span data-ttu-id="f77fa-427">Syntax für Listensammlungen</span><span class="sxs-lookup"><span data-stu-id="f77fa-427">Syntax for list collections</span></span>

<span data-ttu-id="f77fa-428">`builder.AttachmentLayout.list` ist die Syntax für Listensammlungen.</span><span class="sxs-lookup"><span data-stu-id="f77fa-428">`builder.AttachmentLayout.list` is the syntax for list collections.</span></span>

## <a name="cards-not-supported-in-teams"></a><span data-ttu-id="f77fa-429">Karten werden in der Teams</span><span class="sxs-lookup"><span data-stu-id="f77fa-429">Cards not supported in Teams</span></span>

<span data-ttu-id="f77fa-430">Die folgenden Karten werden vom Bot Framework implementiert, aber nicht von Teams:</span><span class="sxs-lookup"><span data-stu-id="f77fa-430">The following cards are implemented by the Bot Framework, but are not supported by Teams:</span></span>

* <span data-ttu-id="f77fa-431">Animationskarten</span><span class="sxs-lookup"><span data-stu-id="f77fa-431">Animation cards</span></span>
* <span data-ttu-id="f77fa-432">Audiokarten</span><span class="sxs-lookup"><span data-stu-id="f77fa-432">Audio cards</span></span>
* <span data-ttu-id="f77fa-433">Grafikkarten</span><span class="sxs-lookup"><span data-stu-id="f77fa-433">Video cards</span></span>
