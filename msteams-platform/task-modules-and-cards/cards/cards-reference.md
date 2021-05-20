---
title: Karten-Referenz
description: Beschreibt alle Karten und Kartenaktionen, die Bots in Teams
localization_priority: Normal
keywords: Bots-Karten-Referenz
ms.topic: reference
ms.openlocfilehash: cab7f1659759f40beb1aba59531ee6c1a84662c1
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566859"
---
# <a name="cards-reference"></a><span data-ttu-id="01d0f-104">Karten-Referenz</span><span class="sxs-lookup"><span data-stu-id="01d0f-104">Cards reference</span></span>

<span data-ttu-id="01d0f-105">Die in diesem Dokument aufgeführten Karten werden in Bots für Microsoft Teams unterstützt.</span><span class="sxs-lookup"><span data-stu-id="01d0f-105">The cards listed in this document are supported in bots for Microsoft Teams.</span></span> <span data-ttu-id="01d0f-106">Sie basieren auf Karten, die vom Bot Framework definiert sind, aber Teams nicht alle Bot Framework-Karten unterstützt und stattdessen einige Teams Karten hinzugefügt wurden.</span><span class="sxs-lookup"><span data-stu-id="01d0f-106">They are based on cards defined by the Bot Framework, but Teams does not support all Bot Framework cards and instead some Teams cards have been added.</span></span> <span data-ttu-id="01d0f-107">Unterschiede werden in den Verweisen in diesem Dokument herausgestellt.</span><span class="sxs-lookup"><span data-stu-id="01d0f-107">Differences are called out in the references in this document.</span></span>

## <a name="card-examples"></a><span data-ttu-id="01d0f-108">Kartenbeispiele</span><span class="sxs-lookup"><span data-stu-id="01d0f-108">Card examples</span></span>

<span data-ttu-id="01d0f-109">Weitere Informationen zur Verwendung von Karten finden Sie in der Dokumentation für das Bot Builder SDK v3.</span><span class="sxs-lookup"><span data-stu-id="01d0f-109">You can find additional information on how to use cards in the documentation for the Bot Builder SDK v3.</span></span> <span data-ttu-id="01d0f-110">Codebeispiele sind auch im Microsoft/BotBuilder-Samples-Repository auf GitHub verfügbar.</span><span class="sxs-lookup"><span data-stu-id="01d0f-110">Code samples are also available in the Microsoft/BotBuilder-Samples repository on GitHub.</span></span>

* <span data-ttu-id="01d0f-111">.NET</span><span class="sxs-lookup"><span data-stu-id="01d0f-111">.NET</span></span>
  * <span data-ttu-id="01d0f-112">[Fügen Sie Karten als Anlagen zu Nachrichten hinzu.](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="01d0f-112">[Add cards as attachments to messages](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true).</span></span>
  * <span data-ttu-id="01d0f-113">[Karten Beispielcode Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/06.using-cards).</span><span class="sxs-lookup"><span data-stu-id="01d0f-113">[Cards sample code Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/06.using-cards).</span></span>

* <span data-ttu-id="01d0f-114">Node.js</span><span class="sxs-lookup"><span data-stu-id="01d0f-114">Node.js</span></span>
  * <span data-ttu-id="01d0f-115">[Fügen Sie Karten als Anlagen zu Nachrichten hinzu.](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="01d0f-115">[Add cards as attachments to messages](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true).</span></span>
  * <span data-ttu-id="01d0f-116">[Karten Beispielcode Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/06.using-cards).</span><span class="sxs-lookup"><span data-stu-id="01d0f-116">[Cards sample code Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/06.using-cards).</span></span>

## <a name="types-of-cards"></a><span data-ttu-id="01d0f-117">Kartentypen</span><span class="sxs-lookup"><span data-stu-id="01d0f-117">Types of cards</span></span>

<span data-ttu-id="01d0f-118">Diese Tabelle zeigt die Kartentypen, die Ihnen zur Verfügung stehen:</span><span class="sxs-lookup"><span data-stu-id="01d0f-118">This table shows the types of cards available to you:</span></span>

| <span data-ttu-id="01d0f-119">Kartentyp</span><span class="sxs-lookup"><span data-stu-id="01d0f-119">Card type</span></span> | <span data-ttu-id="01d0f-120">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="01d0f-120">Description</span></span> |
| --- | --- |
| [<span data-ttu-id="01d0f-121">Adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="01d0f-121">Adaptive card</span></span>](#adaptive-card) | <span data-ttu-id="01d0f-122">Diese Karte ist eine hochgradig anpassbare Karte, die eine beliebige Kombination aus Text, Sprache, Bildern, Schaltflächen und Eingabefeldern enthalten kann.</span><span class="sxs-lookup"><span data-stu-id="01d0f-122">This card is highly customizable card that can contain any combination of text, speech, images, buttons, and input fields.</span></span> |
| [<span data-ttu-id="01d0f-123">Heldenkarte</span><span class="sxs-lookup"><span data-stu-id="01d0f-123">Hero card</span></span>](#hero-card) | <span data-ttu-id="01d0f-124">Diese Karte enthält in der Regel ein einzelnes großes Bild, eine oder mehrere Schaltflächen und eine kleine Menge Text.</span><span class="sxs-lookup"><span data-stu-id="01d0f-124">This card typically contains a single large image, one or more buttons, and a small amount of text.</span></span> |
| [<span data-ttu-id="01d0f-125">Listenkarte</span><span class="sxs-lookup"><span data-stu-id="01d0f-125">List card</span></span>](#list-card) | <span data-ttu-id="01d0f-126">Diese Karte ist eine Bildlaufliste von Elementen.</span><span class="sxs-lookup"><span data-stu-id="01d0f-126">This card is a scrolling list of items.</span></span> |
| [<span data-ttu-id="01d0f-127">Office 365-Anschlusskarte</span><span class="sxs-lookup"><span data-stu-id="01d0f-127">Office 365 connector card</span></span>](#office-365-connector-card) | <span data-ttu-id="01d0f-128">Diese Karte verfügt über ein flexibles Layout mit mehreren Abschnitten, Feldern, Bildern und Aktionen.</span><span class="sxs-lookup"><span data-stu-id="01d0f-128">This card has a flexible layout with multiple sections, fields, images, and actions.</span></span> |
| [<span data-ttu-id="01d0f-129">Empfangskarte</span><span class="sxs-lookup"><span data-stu-id="01d0f-129">Receipt card</span></span>](#receipt-card) | <span data-ttu-id="01d0f-130">Diese Karte stellt dem Benutzer eine Quittung zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="01d0f-130">This card provides a receipt to the user.</span></span> |
| [<span data-ttu-id="01d0f-131">Signin-Karte</span><span class="sxs-lookup"><span data-stu-id="01d0f-131">Signin card</span></span>](#signin-card) | <span data-ttu-id="01d0f-132">Diese Karte ermöglicht es einem Bot, anzufordern, dass sich ein Benutzer anmeldet.</span><span class="sxs-lookup"><span data-stu-id="01d0f-132">This card enables a bot to request that a user signs in.</span></span> |
| [<span data-ttu-id="01d0f-133">Thumbnail-Karte</span><span class="sxs-lookup"><span data-stu-id="01d0f-133">Thumbnail card</span></span>](#thumbnail-card) | <span data-ttu-id="01d0f-134">Diese Karte enthält in der Regel ein einzelnes Miniaturbild, einen kurzen Text und eine oder mehrere Schaltflächen.</span><span class="sxs-lookup"><span data-stu-id="01d0f-134">This card typically contains a single thumbnail image, some short text, and one or more buttons.</span></span> |
| [<span data-ttu-id="01d0f-135">Kartensammlungen</span><span class="sxs-lookup"><span data-stu-id="01d0f-135">Card collections</span></span>](#card-collections) | <span data-ttu-id="01d0f-136">Diese Karten werden verwendet, um mehrere Elemente in einer einzigen Antwort zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="01d0f-136">This cards is used to return multiple items in a single response.</span></span> |

## <a name="common-properties-for-all-cards"></a><span data-ttu-id="01d0f-137">Gemeinsame Eigenschaften für alle Karten</span><span class="sxs-lookup"><span data-stu-id="01d0f-137">Common properties for all cards</span></span>

### <a name="inline-card-images"></a><span data-ttu-id="01d0f-138">Inline-Kartenbilder</span><span class="sxs-lookup"><span data-stu-id="01d0f-138">Inline card images</span></span>

<span data-ttu-id="01d0f-139">Die Karte kann ein Inlinebild enthalten, indem sie einen Link zum öffentlich zugänglichen Bild enthält.</span><span class="sxs-lookup"><span data-stu-id="01d0f-139">The card can contain an inline image by including a link to the publicly available image.</span></span> <span data-ttu-id="01d0f-140">Aus Leistungsgründen wird dringend empfohlen, das Image in einem öffentlichen Content-Delivery-Netzwerk (CDN) zu hosten.</span><span class="sxs-lookup"><span data-stu-id="01d0f-140">For performance purposes, it is highly recommended you host the image on a public content-delivery network (CDN).</span></span>

<span data-ttu-id="01d0f-141">Bilder werden nach oben oder unten skaliert, während das Seitenverhältnis beibehalten wird, um den Bildbereich abzudecken.</span><span class="sxs-lookup"><span data-stu-id="01d0f-141">Images are scaled up or down in size while maintaining the aspect ratio to cover the image area.</span></span> <span data-ttu-id="01d0f-142">Bilder werden dann von der Mitte abgeschnitten, um das entsprechende Seitenverhältnis für die Karte zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="01d0f-142">Images are then cropped from center to achieve the appropriate aspect ratio for the card.</span></span>

<span data-ttu-id="01d0f-143">Bilder müssen höchstens 1024×1024 im PNG-, JPEG- oder GIF-Format vorliegen und animiertes GIF nicht unterstützen.</span><span class="sxs-lookup"><span data-stu-id="01d0f-143">Images must be at most 1024×1024, in PNG, JPEG, or GIF format, and do not support animated GIF.</span></span>

| <span data-ttu-id="01d0f-144">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="01d0f-144">Property</span></span> | <span data-ttu-id="01d0f-145">Typ</span><span class="sxs-lookup"><span data-stu-id="01d0f-145">Type</span></span>  | <span data-ttu-id="01d0f-146">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="01d0f-146">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="01d0f-147">url</span><span class="sxs-lookup"><span data-stu-id="01d0f-147">url</span></span> | <span data-ttu-id="01d0f-148">URL</span><span class="sxs-lookup"><span data-stu-id="01d0f-148">URL</span></span> | <span data-ttu-id="01d0f-149">HTTPS-URL zum Bild.</span><span class="sxs-lookup"><span data-stu-id="01d0f-149">HTTPS URL to the image.</span></span> |
| <span data-ttu-id="01d0f-150">alt</span><span class="sxs-lookup"><span data-stu-id="01d0f-150">alt</span></span> | <span data-ttu-id="01d0f-151">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="01d0f-151">String</span></span> | <span data-ttu-id="01d0f-152">Zugängliche Beschreibung des Bildes.</span><span class="sxs-lookup"><span data-stu-id="01d0f-152">Accessible description of the image.</span></span> |

> [!NOTE]
> <span data-ttu-id="01d0f-153">Wenn eine Karte eine Bild-URL enthält, die eine Umleitung vor dem endgültigen Bild durchläuft, wird die Umleitung in der Bild-URL nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="01d0f-153">If a card includes an image URL that goes through a redirect before the final image, the redirect in image URL is not supported.</span></span> <span data-ttu-id="01d0f-154">Dies tritt bei Bildern auf, die in der öffentlichen Cloud freigegeben wurden.</span><span class="sxs-lookup"><span data-stu-id="01d0f-154">This occurs for images shared on the public cloud.</span></span>

### <a name="buttons"></a><span data-ttu-id="01d0f-155">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="01d0f-155">Buttons</span></span>

<span data-ttu-id="01d0f-156">An der Unterseite der Karte werden Schaltflächen gestapelt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="01d0f-156">Buttons are shown stacked at the bottom of the card.</span></span> <span data-ttu-id="01d0f-157">Schaltflächentext befindet sich immer in einer einzelnen Zeile und wird abgeschnitten, wenn der Text die Schaltflächenbreite überschreitet.</span><span class="sxs-lookup"><span data-stu-id="01d0f-157">Button text is always on a single line and is truncated if the text exceeds the button width.</span></span> <span data-ttu-id="01d0f-158">Zusätzliche Schaltflächen, die über die von der Karte unterstützte maximale Anzahl hinausgehen, werden nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="01d0f-158">Any additional buttons beyond the maximum number supported by the card are not shown.</span></span>

<span data-ttu-id="01d0f-159">Weitere Informationen finden Sie unter [Kartenaktionen](~/task-modules-and-cards/cards/cards-actions.md).</span><span class="sxs-lookup"><span data-stu-id="01d0f-159">For more information, see [card actions](~/task-modules-and-cards/cards/cards-actions.md).</span></span>

### <a name="card-formatting"></a><span data-ttu-id="01d0f-160">Kartenformatierung</span><span class="sxs-lookup"><span data-stu-id="01d0f-160">Card formatting</span></span>

<span data-ttu-id="01d0f-161">Weitere Informationen zur Textformatierung in Karten finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md).</span><span class="sxs-lookup"><span data-stu-id="01d0f-161">For more information on text formatting in cards, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span>

## <a name="adaptive-card"></a><span data-ttu-id="01d0f-162">Adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="01d0f-162">Adaptive card</span></span>

<span data-ttu-id="01d0f-163">Eine adaptive Karte ist eine anpassbare Karte, die eine beliebige Kombination aus Text, Sprache, Bildern, Schaltflächen und Eingabefeldern enthalten kann.</span><span class="sxs-lookup"><span data-stu-id="01d0f-163">An adaptive card is a customizable card that can contain any combination of text, speech, images, buttons, and input fields.</span></span> <span data-ttu-id="01d0f-164">Weitere Informationen finden Sie unter [Adaptive Karten v1.2.0](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0).</span><span class="sxs-lookup"><span data-stu-id="01d0f-164">For more information, see [adaptive cards v1.2.0](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0).</span></span>

### <a name="support-for-adaptive-cards"></a><span data-ttu-id="01d0f-165">Unterstützung für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="01d0f-165">Support for adaptive cards</span></span>

| <span data-ttu-id="01d0f-166">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="01d0f-166">Bots in Teams</span></span> | <span data-ttu-id="01d0f-167">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="01d0f-167">Messaging extensions</span></span>  | <span data-ttu-id="01d0f-168">Connectors</span><span class="sxs-lookup"><span data-stu-id="01d0f-168">Connectors</span></span> | <span data-ttu-id="01d0f-169">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="01d0f-169">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="01d0f-170">✔</span><span class="sxs-lookup"><span data-stu-id="01d0f-170">✔</span></span> | <span data-ttu-id="01d0f-171">✔</span><span class="sxs-lookup"><span data-stu-id="01d0f-171">✔</span></span> | <span data-ttu-id="01d0f-172">✖</span><span class="sxs-lookup"><span data-stu-id="01d0f-172">✖</span></span> | <span data-ttu-id="01d0f-173">✔</span><span class="sxs-lookup"><span data-stu-id="01d0f-173">✔</span></span> |

> [!NOTE]
> * <span data-ttu-id="01d0f-174">Teams Plattform unterstützt v1.2 oder früher adaptive Kartenfunktionen.</span><span class="sxs-lookup"><span data-stu-id="01d0f-174">Teams platform supports v1.2 or earlier of adaptive card features.</span></span>
> * <span data-ttu-id="01d0f-175">Medienelemente werden derzeit in adaptivecard v1.2 auf der Teams Plattform nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="01d0f-175">Media elements are currently not supported in adaptive card v1.2 on the Teams platform.</span></span>

### <a name="example-of-an-adaptive-card"></a><span data-ttu-id="01d0f-176">Beispiel für eine adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="01d0f-176">Example of an adaptive card</span></span>

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

#### <a name="additional-information-on-adaptive-cards"></a><span data-ttu-id="01d0f-178">Zusätzliche Informationen zu adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="01d0f-178">Additional information on adaptive cards</span></span>

<span data-ttu-id="01d0f-179">Referenz für Bot Framework:</span><span class="sxs-lookup"><span data-stu-id="01d0f-179">Bot Framework reference:</span></span>

* [<span data-ttu-id="01d0f-180">Adaptive Karten Node.js</span><span class="sxs-lookup"><span data-stu-id="01d0f-180">Adaptive cards Node.js</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true)
* [<span data-ttu-id="01d0f-181">Adaptive Karte C #</span><span class="sxs-lookup"><span data-stu-id="01d0f-181">Adaptive card C#</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true)

## <a name="hero-card"></a><span data-ttu-id="01d0f-182">Heldenkarte</span><span class="sxs-lookup"><span data-stu-id="01d0f-182">Hero card</span></span>

<span data-ttu-id="01d0f-183">Eine Karte, die in der Regel ein einzelnes großes Bild, eine oder mehrere Schaltflächen und Text enthält.</span><span class="sxs-lookup"><span data-stu-id="01d0f-183">A card that typically contains a single large image, one or more buttons, and text.</span></span>

### <a name="support-for-hero-cards"></a><span data-ttu-id="01d0f-184">Unterstützung für Heldenkarten</span><span class="sxs-lookup"><span data-stu-id="01d0f-184">Support for hero cards</span></span>

| <span data-ttu-id="01d0f-185">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="01d0f-185">Bots in Teams</span></span> | <span data-ttu-id="01d0f-186">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="01d0f-186">Messaging extensions</span></span>  | <span data-ttu-id="01d0f-187">Connectors</span><span class="sxs-lookup"><span data-stu-id="01d0f-187">Connectors</span></span> | <span data-ttu-id="01d0f-188">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="01d0f-188">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="01d0f-189">✔</span><span class="sxs-lookup"><span data-stu-id="01d0f-189">✔</span></span> | <span data-ttu-id="01d0f-190">✔</span><span class="sxs-lookup"><span data-stu-id="01d0f-190">✔</span></span> | <span data-ttu-id="01d0f-191">✖</span><span class="sxs-lookup"><span data-stu-id="01d0f-191">✖</span></span> | <span data-ttu-id="01d0f-192">✔</span><span class="sxs-lookup"><span data-stu-id="01d0f-192">✔</span></span> |

### <a name="properties-of-a-hero-card"></a><span data-ttu-id="01d0f-193">Eigenschaften einer Heldenkarte</span><span class="sxs-lookup"><span data-stu-id="01d0f-193">Properties of a hero card</span></span>

| <span data-ttu-id="01d0f-194">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="01d0f-194">Property</span></span> | <span data-ttu-id="01d0f-195">Typ</span><span class="sxs-lookup"><span data-stu-id="01d0f-195">Type</span></span>  | <span data-ttu-id="01d0f-196">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="01d0f-196">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="01d0f-197">title</span><span class="sxs-lookup"><span data-stu-id="01d0f-197">title</span></span> | <span data-ttu-id="01d0f-198">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="01d0f-198">Rich text</span></span> | <span data-ttu-id="01d0f-199">Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="01d0f-199">Title of the card.</span></span> <span data-ttu-id="01d0f-200">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="01d0f-200">Maximum 2 lines.</span></span> |
| <span data-ttu-id="01d0f-201">Untertitel</span><span class="sxs-lookup"><span data-stu-id="01d0f-201">subtitle</span></span> | <span data-ttu-id="01d0f-202">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="01d0f-202">Rich text</span></span> | <span data-ttu-id="01d0f-203">Untertitel der Karte.</span><span class="sxs-lookup"><span data-stu-id="01d0f-203">Subtitle of the card.</span></span> <span data-ttu-id="01d0f-204">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="01d0f-204">Maximum 2 lines.</span></span>|
| <span data-ttu-id="01d0f-205">text</span><span class="sxs-lookup"><span data-stu-id="01d0f-205">text</span></span> | <span data-ttu-id="01d0f-206">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="01d0f-206">Rich text</span></span> | <span data-ttu-id="01d0f-207">Text wird unter dem Untertitel angezeigt.</span><span class="sxs-lookup"><span data-stu-id="01d0f-207">Text appears under the subtitle.</span></span> <span data-ttu-id="01d0f-208">Formatierungsoptionen finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md).</span><span class="sxs-lookup"><span data-stu-id="01d0f-208">For formatting options, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span> |
| <span data-ttu-id="01d0f-209">Bilder</span><span class="sxs-lookup"><span data-stu-id="01d0f-209">images</span></span> | <span data-ttu-id="01d0f-210">Array von Bildern</span><span class="sxs-lookup"><span data-stu-id="01d0f-210">Array of images</span></span> | <span data-ttu-id="01d0f-211">Bild oben auf der Karte angezeigt.</span><span class="sxs-lookup"><span data-stu-id="01d0f-211">Image displayed at the top of the card.</span></span> <span data-ttu-id="01d0f-212">Seitenverhältnis 16:9.</span><span class="sxs-lookup"><span data-stu-id="01d0f-212">Aspect ratio 16:9.</span></span> |
| <span data-ttu-id="01d0f-213">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="01d0f-213">buttons</span></span> | <span data-ttu-id="01d0f-214">Array von Aktionsobjekten</span><span class="sxs-lookup"><span data-stu-id="01d0f-214">Array of action objects</span></span> | <span data-ttu-id="01d0f-215">Satz von Aktionen, die für die aktuelle Karte gelten.</span><span class="sxs-lookup"><span data-stu-id="01d0f-215">Set of actions applicable to the current card.</span></span> <span data-ttu-id="01d0f-216">Maximal 6.</span><span class="sxs-lookup"><span data-stu-id="01d0f-216">Maximum 6.</span></span> |
| <span data-ttu-id="01d0f-217">Tippen</span><span class="sxs-lookup"><span data-stu-id="01d0f-217">tap</span></span> | <span data-ttu-id="01d0f-218">Action-Objekt</span><span class="sxs-lookup"><span data-stu-id="01d0f-218">Action object</span></span> | <span data-ttu-id="01d0f-219">Aktiviert, wenn der Benutzer auf die Karte selbst tippt.</span><span class="sxs-lookup"><span data-stu-id="01d0f-219">Activated when the user taps on the card itself.</span></span> |

### <a name="example-of-a-hero-card"></a><span data-ttu-id="01d0f-220">Beispiel für eine Heldenkarte</span><span class="sxs-lookup"><span data-stu-id="01d0f-220">Example of a hero card</span></span>

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

### <a name="additional-information-on-hero-cards"></a><span data-ttu-id="01d0f-222">Zusätzliche Informationen zu Heldenkarten</span><span class="sxs-lookup"><span data-stu-id="01d0f-222">Additional information on hero cards</span></span>

<span data-ttu-id="01d0f-223">Referenz für Bot Framework:</span><span class="sxs-lookup"><span data-stu-id="01d0f-223">Bot Framework reference:</span></span>

* [<span data-ttu-id="01d0f-224">Heldenkarte Node.js</span><span class="sxs-lookup"><span data-stu-id="01d0f-224">Hero card Node.js</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-a-hero-card&preserve-view=true)
* [<span data-ttu-id="01d0f-225">Heldenkarte C #</span><span class="sxs-lookup"><span data-stu-id="01d0f-225">Hero card C#</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-hero-card&preserve-view=true)

## <a name="list-card"></a><span data-ttu-id="01d0f-226">Listenkarte</span><span class="sxs-lookup"><span data-stu-id="01d0f-226">List card</span></span>

<span data-ttu-id="01d0f-227">Die Listenkarte wurde von Teams hinzugefügt, um Funktionen bereitzustellen, die über das hinausgehen, was die Listensammlung bereitstellen kann.</span><span class="sxs-lookup"><span data-stu-id="01d0f-227">The list card has been added by Teams to provide functions beyond what the list collection can provide.</span></span> <span data-ttu-id="01d0f-228">Die Listenkarte enthält eine Bildlaufliste der Elemente.</span><span class="sxs-lookup"><span data-stu-id="01d0f-228">The list card provides a scrolling list of items.</span></span>

### <a name="support-for-list-cards"></a><span data-ttu-id="01d0f-229">Unterstützung für Listenkarten</span><span class="sxs-lookup"><span data-stu-id="01d0f-229">Support for list cards</span></span>

| <span data-ttu-id="01d0f-230">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="01d0f-230">Bots in Teams</span></span> | <span data-ttu-id="01d0f-231">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="01d0f-231">Messaging extensions</span></span>  | <span data-ttu-id="01d0f-232">Connectors</span><span class="sxs-lookup"><span data-stu-id="01d0f-232">Connectors</span></span> | <span data-ttu-id="01d0f-233">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="01d0f-233">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="01d0f-234">✔</span><span class="sxs-lookup"><span data-stu-id="01d0f-234">✔</span></span> | <span data-ttu-id="01d0f-235">✖</span><span class="sxs-lookup"><span data-stu-id="01d0f-235">✖</span></span> | <span data-ttu-id="01d0f-236">✖</span><span class="sxs-lookup"><span data-stu-id="01d0f-236">✖</span></span> |<span data-ttu-id="01d0f-237">✔</span><span class="sxs-lookup"><span data-stu-id="01d0f-237">✔</span></span> |

### <a name="properties-of-a-list-card"></a><span data-ttu-id="01d0f-238">Eigenschaften einer Listenkarte</span><span class="sxs-lookup"><span data-stu-id="01d0f-238">Properties of a list card</span></span>

| <span data-ttu-id="01d0f-239">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="01d0f-239">Property</span></span> | <span data-ttu-id="01d0f-240">Typ</span><span class="sxs-lookup"><span data-stu-id="01d0f-240">Type</span></span>  | <span data-ttu-id="01d0f-241">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="01d0f-241">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="01d0f-242">title</span><span class="sxs-lookup"><span data-stu-id="01d0f-242">title</span></span> | <span data-ttu-id="01d0f-243">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="01d0f-243">Rich text</span></span> | <span data-ttu-id="01d0f-244">Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="01d0f-244">Title of the card.</span></span> <span data-ttu-id="01d0f-245">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="01d0f-245">Maximum 2 lines.</span></span>|
| <span data-ttu-id="01d0f-246">Elemente</span><span class="sxs-lookup"><span data-stu-id="01d0f-246">items</span></span> | <span data-ttu-id="01d0f-247">Array von Listenelementen</span><span class="sxs-lookup"><span data-stu-id="01d0f-247">Array of list items</span></span> ||
| <span data-ttu-id="01d0f-248">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="01d0f-248">buttons</span></span> | <span data-ttu-id="01d0f-249">Array von Aktionsobjekten</span><span class="sxs-lookup"><span data-stu-id="01d0f-249">Array of action objects</span></span> | <span data-ttu-id="01d0f-250">Satz von Aktionen, die für die aktuelle Karte gelten.</span><span class="sxs-lookup"><span data-stu-id="01d0f-250">Set of actions applicable to the current card.</span></span> <span data-ttu-id="01d0f-251">Maximal 6.</span><span class="sxs-lookup"><span data-stu-id="01d0f-251">Maximum 6.</span></span> |

### <a name="example-of-a-list-card"></a><span data-ttu-id="01d0f-252">Beispiel für eine Listenkarte</span><span class="sxs-lookup"><span data-stu-id="01d0f-252">Example of a list card</span></span>

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

## <a name="office-365-connector-card"></a><span data-ttu-id="01d0f-253">Office 365-Anschlusskarte</span><span class="sxs-lookup"><span data-stu-id="01d0f-253">Office 365 connector card</span></span>

<span data-ttu-id="01d0f-254">Die Office 365-Connectorkarte wird in Teams und nicht in Bot Framework unterstützt.</span><span class="sxs-lookup"><span data-stu-id="01d0f-254">The Office 365 connector card is supported in Teams, not in Bot Framework.</span></span> <span data-ttu-id="01d0f-255">Diese Karte bietet ein flexibles Layout mit mehreren Abschnitten, Feldern, Bildern und Aktionen.</span><span class="sxs-lookup"><span data-stu-id="01d0f-255">This card provides a flexible layout with multiple sections, fields, images, and actions.</span></span> <span data-ttu-id="01d0f-256">Diese Karte kapselt eine Connector-Karte, so dass sie von Bots verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="01d0f-256">This card encapsulates a connector card so that it can be used by bots.</span></span> <span data-ttu-id="01d0f-257">Unterschiede zwischen Anschlusskarten und O365-Karte finden Sie [unter Hinweise auf der Office 365-Anschlusskarte](#notes-on-the-office-365-connector-card).</span><span class="sxs-lookup"><span data-stu-id="01d0f-257">For differences between connector cards and the O365 card, see [Notes on the Office 365 connector card](#notes-on-the-office-365-connector-card).</span></span>

### <a name="support-for-office-365-connector-cards"></a><span data-ttu-id="01d0f-258">Unterstützung für Office 365-Anschlusskarten</span><span class="sxs-lookup"><span data-stu-id="01d0f-258">Support for Office 365 connector cards</span></span>

| <span data-ttu-id="01d0f-259">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="01d0f-259">Bots in Teams</span></span> | <span data-ttu-id="01d0f-260">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="01d0f-260">Messaging extensions</span></span>  | <span data-ttu-id="01d0f-261">Connectors</span><span class="sxs-lookup"><span data-stu-id="01d0f-261">Connectors</span></span> | <span data-ttu-id="01d0f-262">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="01d0f-262">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="01d0f-263">✔</span><span class="sxs-lookup"><span data-stu-id="01d0f-263">✔</span></span> | <span data-ttu-id="01d0f-264">✔</span><span class="sxs-lookup"><span data-stu-id="01d0f-264">✔</span></span> | <span data-ttu-id="01d0f-265">✔</span><span class="sxs-lookup"><span data-stu-id="01d0f-265">✔</span></span> | <span data-ttu-id="01d0f-266">✖</span><span class="sxs-lookup"><span data-stu-id="01d0f-266">✖</span></span> |

### <a name="properties-of-the-office-365-connector-card"></a><span data-ttu-id="01d0f-267">Eigenschaften der Office 365-Anschlusskarte</span><span class="sxs-lookup"><span data-stu-id="01d0f-267">Properties of the Office 365 connector card</span></span>

| <span data-ttu-id="01d0f-268">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="01d0f-268">Property</span></span> | <span data-ttu-id="01d0f-269">Typ</span><span class="sxs-lookup"><span data-stu-id="01d0f-269">Type</span></span>  | <span data-ttu-id="01d0f-270">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="01d0f-270">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="01d0f-271">title</span><span class="sxs-lookup"><span data-stu-id="01d0f-271">title</span></span> | <span data-ttu-id="01d0f-272">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="01d0f-272">Rich text</span></span> | <span data-ttu-id="01d0f-273">Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="01d0f-273">Title of the card.</span></span> <span data-ttu-id="01d0f-274">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="01d0f-274">Maximum 2 lines.</span></span> |
| <span data-ttu-id="01d0f-275">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="01d0f-275">summary</span></span> | <span data-ttu-id="01d0f-276">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="01d0f-276">Rich text</span></span> | <span data-ttu-id="01d0f-277">Zusammenfassung der Karte.</span><span class="sxs-lookup"><span data-stu-id="01d0f-277">Summary of the card.</span></span> <span data-ttu-id="01d0f-278">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="01d0f-278">Maximum 2 lines.</span></span> |
| <span data-ttu-id="01d0f-279">text</span><span class="sxs-lookup"><span data-stu-id="01d0f-279">text</span></span> | <span data-ttu-id="01d0f-280">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="01d0f-280">Rich text</span></span> | <span data-ttu-id="01d0f-281">Text wird unter dem Untertitel angezeigt.</span><span class="sxs-lookup"><span data-stu-id="01d0f-281">Text appears under the subtitle.</span></span> <span data-ttu-id="01d0f-282">Formatierungsoptionen finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md).</span><span class="sxs-lookup"><span data-stu-id="01d0f-282">For formatting options, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span> |
| <span data-ttu-id="01d0f-283">themeColor</span><span class="sxs-lookup"><span data-stu-id="01d0f-283">themeColor</span></span> | <span data-ttu-id="01d0f-284">HEX-String</span><span class="sxs-lookup"><span data-stu-id="01d0f-284">HEX string</span></span> | <span data-ttu-id="01d0f-285">Farbe, die die aus dem Anwendungsmanifest bereitgestellte accentColor überschreibt.</span><span class="sxs-lookup"><span data-stu-id="01d0f-285">Color that overrides the accentColor provided from the application manifest.</span></span> |

### <a name="notes-on-the-office-365-connector-card"></a><span data-ttu-id="01d0f-286">Hinweise auf der Office 365-Anschlusskarte</span><span class="sxs-lookup"><span data-stu-id="01d0f-286">Notes on the Office 365 connector card</span></span>

<span data-ttu-id="01d0f-287">Office 365-Anschlusskarten funktionieren in Microsoft Teams ordnungsgemäß, einschließlich [ActionCard-Aktionen](/outlook/actionable-messages/card-reference#actioncard-action).</span><span class="sxs-lookup"><span data-stu-id="01d0f-287">Office 365 connector cards function properly in Microsoft Teams, including [ActionCard actions](/outlook/actionable-messages/card-reference#actioncard-action).</span></span>

<span data-ttu-id="01d0f-288">Ein wichtiger Unterschied zwischen der Verwendung von Anschlusskarten von einem Stecker und der Verwendung von Anschlusskarten in Ihrem Bot ist die Handhabung von Kartenaktionen.</span><span class="sxs-lookup"><span data-stu-id="01d0f-288">One important difference between using connector cards from a connector and using connector cards in your bot is the handling of card actions.</span></span>

* <span data-ttu-id="01d0f-289">Bei einem Connector empfängt der Endpunkt die Kartennutzlast über HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="01d0f-289">For a connector, the endpoint receives the card payload through HTTP POST.</span></span>
* <span data-ttu-id="01d0f-290">Bei einem Bot löst die `HttpPOST` Aktion eine Aktivität aus, die nur die `invoke` Aktions-ID und den Körper an den Bot sendet.</span><span class="sxs-lookup"><span data-stu-id="01d0f-290">For a bot, the `HttpPOST` action triggers an `invoke` activity that sends only the action ID and body to the bot.</span></span>

<span data-ttu-id="01d0f-291">Jede Anschlusskarte kann maximal zehn Abschnitte anzeigen, und jeder Abschnitt kann maximal fünf Bilder und fünf Aktionen enthalten.</span><span class="sxs-lookup"><span data-stu-id="01d0f-291">Each connector card can display a maximum of ten sections, and each section can contain a maximum of five images and five actions.</span></span>

> [!NOTE]
> <span data-ttu-id="01d0f-292">Zusätzliche Abschnitte, Bilder oder Aktionen in einer Nachricht werden nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="01d0f-292">Any additional sections, images, or actions in a message do not appear.</span></span>

<span data-ttu-id="01d0f-293">Alle Textfelder unterstützen Markdown und HTML.</span><span class="sxs-lookup"><span data-stu-id="01d0f-293">All text fields support markdown and HTML.</span></span> <span data-ttu-id="01d0f-294">Sie können steuern, welche Abschnitte Markdown oder HTML verwenden, indem Sie die `markdown` Eigenschaft in einer Nachricht festlegen.</span><span class="sxs-lookup"><span data-stu-id="01d0f-294">You can control which sections use markdown or HTML by setting the `markdown` property in a message.</span></span> <span data-ttu-id="01d0f-295">Standardmäßig `markdown` ist auf `true` festgelegt.</span><span class="sxs-lookup"><span data-stu-id="01d0f-295">By default, `markdown` is set to `true`.</span></span> <span data-ttu-id="01d0f-296">Wenn Sie stattdessen HTML verwenden möchten, setzen Sie `markdown` auf `false` .</span><span class="sxs-lookup"><span data-stu-id="01d0f-296">If you want to use HTML instead, set `markdown` to `false`.</span></span>

<span data-ttu-id="01d0f-297">Wenn Sie die `themeColor` Eigenschaft angeben, wird die `accentColor` Eigenschaft im App-Manifest überschrieben.</span><span class="sxs-lookup"><span data-stu-id="01d0f-297">If you specify the `themeColor` property, it overrides the `accentColor` property in the app manifest.</span></span>

<span data-ttu-id="01d0f-298">Um den Renderstil für `activityImage` anzugeben, können Sie `activityImageType` wie folgt festlegen:</span><span class="sxs-lookup"><span data-stu-id="01d0f-298">To specify the rendering style for `activityImage`, you can set `activityImageType` as follows:</span></span>

| <span data-ttu-id="01d0f-299">Wert</span><span class="sxs-lookup"><span data-stu-id="01d0f-299">Value</span></span> | <span data-ttu-id="01d0f-300">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="01d0f-300">Description</span></span> |
| --- | --- |
| `avatar` | <span data-ttu-id="01d0f-301">Standard; `activityImage` wird als Kreis beschnitten.</span><span class="sxs-lookup"><span data-stu-id="01d0f-301">Default; `activityImage` is cropped as a circle.</span></span> |
| `article` | <span data-ttu-id="01d0f-302">`activityImage` wird als Rechteck angezeigt und behält sein Seitenverhältnis bei.</span><span class="sxs-lookup"><span data-stu-id="01d0f-302">`activityImage` is displayed as a rectangle and retains its aspect ratio.</span></span> |

<span data-ttu-id="01d0f-303">Weitere Informationen zu den Eigenschaften der Connectorkarte finden Sie unter [Verwertbare Meldungskartenreferenz](/outlook/actionable-messages/card-reference).</span><span class="sxs-lookup"><span data-stu-id="01d0f-303">For all other details about connector card properties, see [actionable message card reference](/outlook/actionable-messages/card-reference).</span></span> <span data-ttu-id="01d0f-304">Die einzigen Connectorkarteneigenschaften, die Microsoft Teams derzeit nicht unterstützt, sind:</span><span class="sxs-lookup"><span data-stu-id="01d0f-304">The only connector card properties that Microsoft Teams does not currently support are as follows:</span></span>

* `heroImage`
* `hideOriginalBody`
* <span data-ttu-id="01d0f-305">`startGroup`immer wie in Teams behandelt `true`</span><span class="sxs-lookup"><span data-stu-id="01d0f-305">`startGroup` always treated as `true` in Teams</span></span>
* `originator`
* `correlationId`

### <a name="example-of-an-office-365-connector-card"></a><span data-ttu-id="01d0f-306">Beispiel für eine Office 365-Anschlusskarte</span><span class="sxs-lookup"><span data-stu-id="01d0f-306">Example of an Office 365 connector card</span></span>

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

## <a name="receipt-card"></a><span data-ttu-id="01d0f-307">Empfangskarte</span><span class="sxs-lookup"><span data-stu-id="01d0f-307">Receipt card</span></span>

<span data-ttu-id="01d0f-308">Teams unterstützt die Empfangskarte.</span><span class="sxs-lookup"><span data-stu-id="01d0f-308">Teams supports receipt card.</span></span> <span data-ttu-id="01d0f-309">Es ist eine Karte, die es einem Bot ermöglicht, dem Benutzer eine Quittung zu geben.</span><span class="sxs-lookup"><span data-stu-id="01d0f-309">It is a card that enables a bot to provide a receipt to the user.</span></span> <span data-ttu-id="01d0f-310">Sie enthält in der Regel die Liste der Artikel, die in den Wareneingang aufgenommen werden sollen, z. B. Steuern und Gesamtinformationen.</span><span class="sxs-lookup"><span data-stu-id="01d0f-310">It typically contains the list of items to include on the receipt, such as tax and total information.</span></span>

### <a name="support-for-receipt-cards"></a><span data-ttu-id="01d0f-311">Unterstützung für Empfangskarten</span><span class="sxs-lookup"><span data-stu-id="01d0f-311">Support for receipt cards</span></span>

| <span data-ttu-id="01d0f-312">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="01d0f-312">Bots in Teams</span></span> | <span data-ttu-id="01d0f-313">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="01d0f-313">Messaging extensions</span></span>  | <span data-ttu-id="01d0f-314">Connectors</span><span class="sxs-lookup"><span data-stu-id="01d0f-314">Connectors</span></span> | <span data-ttu-id="01d0f-315">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="01d0f-315">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="01d0f-316">✔</span><span class="sxs-lookup"><span data-stu-id="01d0f-316">✔</span></span> | <span data-ttu-id="01d0f-317">✔</span><span class="sxs-lookup"><span data-stu-id="01d0f-317">✔</span></span> | <span data-ttu-id="01d0f-318">✖</span><span class="sxs-lookup"><span data-stu-id="01d0f-318">✖</span></span> | <span data-ttu-id="01d0f-319">✔</span><span class="sxs-lookup"><span data-stu-id="01d0f-319">✔</span></span> |

### <a name="example-of-a-receipt-card"></a><span data-ttu-id="01d0f-320">Beispiel für eine Empfangskarte</span><span class="sxs-lookup"><span data-stu-id="01d0f-320">Example of a receipt card</span></span>

![Beispiel für eine Empfangskarte](~/assets/images/cards/receipt.png)

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

### <a name="additional-information-on-receipt-cards"></a><span data-ttu-id="01d0f-322">Zusätzliche Informationen zu Denobkarten</span><span class="sxs-lookup"><span data-stu-id="01d0f-322">Additional information on receipt cards</span></span>

<span data-ttu-id="01d0f-323">Referenz für Bot Framework:</span><span class="sxs-lookup"><span data-stu-id="01d0f-323">Bot Framework reference:</span></span>

* [<span data-ttu-id="01d0f-324">Empfangskarte Node.js</span><span class="sxs-lookup"><span data-stu-id="01d0f-324">Receipt card Node.js</span></span>](/javascript/api/botframework-schema/receiptcard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="01d0f-325">Empfangskarte C #</span><span class="sxs-lookup"><span data-stu-id="01d0f-325">Receipt card C#</span></span>](/dotnet/api/microsoft.bot.schema.receiptcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="signin-card"></a><span data-ttu-id="01d0f-326">Signin-Karte</span><span class="sxs-lookup"><span data-stu-id="01d0f-326">Signin card</span></span>

<span data-ttu-id="01d0f-327">Mit der Anmeldekarte kann ein Bot einen Benutzer auffordern, sich anzumelden.</span><span class="sxs-lookup"><span data-stu-id="01d0f-327">Signin card enables a bot to request a user to sign in.</span></span> <span data-ttu-id="01d0f-328">Es wird in Teams in einer etwas anderen Form unterstützt, als es im Bot Framework zu finden ist.</span><span class="sxs-lookup"><span data-stu-id="01d0f-328">It is supported in Teams in a slightly different form than is found in the Bot Framework.</span></span> <span data-ttu-id="01d0f-329">Die Anmeldekarte in Teams ähnelt der Anmeldekarte im Bot Framework, mit der Ausnahme, dass die Anmeldekarte in Teams nur zwei Aktionen unterstützt: `signin` und `openUrl` .</span><span class="sxs-lookup"><span data-stu-id="01d0f-329">The signin card in Teams is similar to the signin card in the Bot Framework except that the signin card in Teams only supports two actions: `signin` and `openUrl`.</span></span>

<span data-ttu-id="01d0f-330">Die Signin-Aktion kann von jeder Karte in Teams verwendet werden, nicht nur von der Anmeldekarte.</span><span class="sxs-lookup"><span data-stu-id="01d0f-330">The signin action can be used from any card in Teams, not just the signin card.</span></span> <span data-ttu-id="01d0f-331">Weitere Informationen zur Authentifizierung finden Sie unter [Microsoft Teams Authentifizierungsablauf für Bots](~/bots/how-to/authentication/auth-flow-bot.md).</span><span class="sxs-lookup"><span data-stu-id="01d0f-331">For more information on authentication, see [Microsoft Teams authentication flow for bots](~/bots/how-to/authentication/auth-flow-bot.md).</span></span>

### <a name="support-for-signin-cards"></a><span data-ttu-id="01d0f-332">Unterstützung für Signin-Karten</span><span class="sxs-lookup"><span data-stu-id="01d0f-332">Support for signin cards</span></span>

| <span data-ttu-id="01d0f-333">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="01d0f-333">Bots in Teams</span></span> | <span data-ttu-id="01d0f-334">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="01d0f-334">Messaging extensions</span></span>  | <span data-ttu-id="01d0f-335">Connectors</span><span class="sxs-lookup"><span data-stu-id="01d0f-335">Connectors</span></span> | <span data-ttu-id="01d0f-336">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="01d0f-336">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="01d0f-337">✔</span><span class="sxs-lookup"><span data-stu-id="01d0f-337">✔</span></span> | <span data-ttu-id="01d0f-338">✖</span><span class="sxs-lookup"><span data-stu-id="01d0f-338">✖</span></span> | <span data-ttu-id="01d0f-339">✖</span><span class="sxs-lookup"><span data-stu-id="01d0f-339">✖</span></span> | <span data-ttu-id="01d0f-340">✔</span><span class="sxs-lookup"><span data-stu-id="01d0f-340">✔</span></span> |

### <a name="additional-information-on-signin-cards"></a><span data-ttu-id="01d0f-341">Zusätzliche Informationen zu Anmeldekarten</span><span class="sxs-lookup"><span data-stu-id="01d0f-341">Additional information on signin cards</span></span>

<span data-ttu-id="01d0f-342">Referenz für Bot Framework:</span><span class="sxs-lookup"><span data-stu-id="01d0f-342">Bot Framework reference:</span></span>

* [<span data-ttu-id="01d0f-343">Anmeldekarte Node.js</span><span class="sxs-lookup"><span data-stu-id="01d0f-343">Signin card Node.js</span></span>](/javascript/api/botframework-schema/signincard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="01d0f-344">Anmeldekarte C #</span><span class="sxs-lookup"><span data-stu-id="01d0f-344">Signin card C#</span></span>](/dotnet/api/microsoft.bot.schema.signincard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="thumbnail-card"></a><span data-ttu-id="01d0f-345">Thumbnail-Karte</span><span class="sxs-lookup"><span data-stu-id="01d0f-345">Thumbnail card</span></span>

<span data-ttu-id="01d0f-346">Eine Karte, die in der Regel ein einzelnes Miniaturbild, eine oder mehrere Schaltflächen und Text enthält.</span><span class="sxs-lookup"><span data-stu-id="01d0f-346">A card that typically contains a single thumbnail image, one or more buttons, and text.</span></span>

### <a name="support-for-thumbnail-cards"></a><span data-ttu-id="01d0f-347">Unterstützung für Miniaturkarten</span><span class="sxs-lookup"><span data-stu-id="01d0f-347">Support for thumbnail cards</span></span>

| <span data-ttu-id="01d0f-348">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="01d0f-348">Bots in Teams</span></span> | <span data-ttu-id="01d0f-349">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="01d0f-349">Messaging extensions</span></span>  | <span data-ttu-id="01d0f-350">Connectors</span><span class="sxs-lookup"><span data-stu-id="01d0f-350">Connectors</span></span> | <span data-ttu-id="01d0f-351">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="01d0f-351">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="01d0f-352">✔</span><span class="sxs-lookup"><span data-stu-id="01d0f-352">✔</span></span> | <span data-ttu-id="01d0f-353">✔</span><span class="sxs-lookup"><span data-stu-id="01d0f-353">✔</span></span> | <span data-ttu-id="01d0f-354">✖</span><span class="sxs-lookup"><span data-stu-id="01d0f-354">✖</span></span> | <span data-ttu-id="01d0f-355">✔</span><span class="sxs-lookup"><span data-stu-id="01d0f-355">✔</span></span> |

![Beispiel für eine Miniaturansichtskarte](~/assets/images/cards/thumbnail.png)

### <a name="properties-of-a-thumbnail-card"></a><span data-ttu-id="01d0f-357">Eigenschaften einer Miniaturansichtskarte</span><span class="sxs-lookup"><span data-stu-id="01d0f-357">Properties of a thumbnail card</span></span>

| <span data-ttu-id="01d0f-358">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="01d0f-358">Property</span></span> | <span data-ttu-id="01d0f-359">Typ</span><span class="sxs-lookup"><span data-stu-id="01d0f-359">Type</span></span>  | <span data-ttu-id="01d0f-360">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="01d0f-360">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="01d0f-361">title</span><span class="sxs-lookup"><span data-stu-id="01d0f-361">title</span></span> | <span data-ttu-id="01d0f-362">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="01d0f-362">Rich text</span></span> | <span data-ttu-id="01d0f-363">Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="01d0f-363">Title of the card.</span></span> <span data-ttu-id="01d0f-364">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="01d0f-364">Maximum 2 lines.</span></span>|
| <span data-ttu-id="01d0f-365">Untertitel</span><span class="sxs-lookup"><span data-stu-id="01d0f-365">subtitle</span></span> | <span data-ttu-id="01d0f-366">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="01d0f-366">Rich text</span></span> | <span data-ttu-id="01d0f-367">Untertitel der Karte.</span><span class="sxs-lookup"><span data-stu-id="01d0f-367">Subtitle of the card.</span></span> <span data-ttu-id="01d0f-368">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="01d0f-368">Maximum 2 lines.</span></span>|
| <span data-ttu-id="01d0f-369">text</span><span class="sxs-lookup"><span data-stu-id="01d0f-369">text</span></span> | <span data-ttu-id="01d0f-370">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="01d0f-370">Rich text</span></span> | <span data-ttu-id="01d0f-371">Text wird unter dem Untertitel angezeigt.</span><span class="sxs-lookup"><span data-stu-id="01d0f-371">Text appears under the subtitle.</span></span> <span data-ttu-id="01d0f-372">Formatierungsoptionen finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md).</span><span class="sxs-lookup"><span data-stu-id="01d0f-372">For formatting options, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span> |
| <span data-ttu-id="01d0f-373">Bilder</span><span class="sxs-lookup"><span data-stu-id="01d0f-373">images</span></span> | <span data-ttu-id="01d0f-374">Array von Bildern</span><span class="sxs-lookup"><span data-stu-id="01d0f-374">Array of images</span></span> | <span data-ttu-id="01d0f-375">Bild oben auf der Karte angezeigt.</span><span class="sxs-lookup"><span data-stu-id="01d0f-375">Image displayed at the top of the card.</span></span> <span data-ttu-id="01d0f-376">Seitenverhältnis 1:1 Quadrat.</span><span class="sxs-lookup"><span data-stu-id="01d0f-376">Aspect ratio 1:1 square.</span></span> |
| <span data-ttu-id="01d0f-377">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="01d0f-377">buttons</span></span> | <span data-ttu-id="01d0f-378">Array von Aktionsobjekten</span><span class="sxs-lookup"><span data-stu-id="01d0f-378">Array of action objects</span></span> | <span data-ttu-id="01d0f-379">Satz von Aktionen, die für die aktuelle Karte gelten.</span><span class="sxs-lookup"><span data-stu-id="01d0f-379">Set of actions applicable to the current card.</span></span> <span data-ttu-id="01d0f-380">Maximal 6.</span><span class="sxs-lookup"><span data-stu-id="01d0f-380">Maximum 6.</span></span> |
| <span data-ttu-id="01d0f-381">Tippen</span><span class="sxs-lookup"><span data-stu-id="01d0f-381">tap</span></span> | <span data-ttu-id="01d0f-382">Action-Objekt</span><span class="sxs-lookup"><span data-stu-id="01d0f-382">Action object</span></span> | <span data-ttu-id="01d0f-383">Aktiviert, wenn der Benutzer auf die Karte selbst tippt.</span><span class="sxs-lookup"><span data-stu-id="01d0f-383">Activated when the user taps on the card itself.</span></span> |

### <a name="example-of-a-thumbnail-card"></a><span data-ttu-id="01d0f-384">Beispiel für eine Miniaturansichtskarte</span><span class="sxs-lookup"><span data-stu-id="01d0f-384">Example of a thumbnail card</span></span>

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

### <a name="additional-information"></a><span data-ttu-id="01d0f-385">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="01d0f-385">Additional information</span></span>

<span data-ttu-id="01d0f-386">Referenz für Bot Framework:</span><span class="sxs-lookup"><span data-stu-id="01d0f-386">Bot Framework reference:</span></span>

* [<span data-ttu-id="01d0f-387">Thumbnail-Karte Node.js</span><span class="sxs-lookup"><span data-stu-id="01d0f-387">Thumbnail card Node.js</span></span>](/javascript/api/botframework-schema/thumbnailcard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="01d0f-388">Thumbnail-Karte C #</span><span class="sxs-lookup"><span data-stu-id="01d0f-388">Thumbnail card C#</span></span>](/dotnet/api/microsoft.bot.schema.thumbnailcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="card-collections"></a><span data-ttu-id="01d0f-389">Kartensammlungen</span><span class="sxs-lookup"><span data-stu-id="01d0f-389">Card collections</span></span>

<span data-ttu-id="01d0f-390">Teams unterstützt Kartensammlungen.</span><span class="sxs-lookup"><span data-stu-id="01d0f-390">Teams supports Card collections.</span></span>

<span data-ttu-id="01d0f-391">Kartensammlungen umfassen `builder.AttachmentLayout.carousel` und `builder.AttachmentLayout.list` .</span><span class="sxs-lookup"><span data-stu-id="01d0f-391">Card collections include `builder.AttachmentLayout.carousel` and `builder.AttachmentLayout.list`.</span></span> <span data-ttu-id="01d0f-392">Diese Sammlungen enthalten adaptive, Helden- oder Miniaturkarten.</span><span class="sxs-lookup"><span data-stu-id="01d0f-392">These collections contain adaptive, hero, or thumbnail cards.</span></span>

## <a name="carousel-collection"></a><span data-ttu-id="01d0f-393">Karussell-Kollektion</span><span class="sxs-lookup"><span data-stu-id="01d0f-393">Carousel collection</span></span>

<span data-ttu-id="01d0f-394">Das [Karussell-Layout](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-carousel-of-cards&preserve-view=true) zeigt ein Karussell von Karten, optional mit zugehörigen Aktionstasten.</span><span class="sxs-lookup"><span data-stu-id="01d0f-394">The [carousel layout](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-carousel-of-cards&preserve-view=true) shows a carousel of cards, optionally with associated action buttons.</span></span>

### <a name="support-for-carousel-collections"></a><span data-ttu-id="01d0f-395">Unterstützung für Karussell-Sammlungen</span><span class="sxs-lookup"><span data-stu-id="01d0f-395">Support for carousel collections</span></span>

| <span data-ttu-id="01d0f-396">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="01d0f-396">Bots in Teams</span></span> | <span data-ttu-id="01d0f-397">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="01d0f-397">Messaging extensions</span></span>  | <span data-ttu-id="01d0f-398">Connectors</span><span class="sxs-lookup"><span data-stu-id="01d0f-398">Connectors</span></span> | <span data-ttu-id="01d0f-399">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="01d0f-399">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="01d0f-400">✔</span><span class="sxs-lookup"><span data-stu-id="01d0f-400">✔</span></span> | <span data-ttu-id="01d0f-401">✖</span><span class="sxs-lookup"><span data-stu-id="01d0f-401">✖</span></span> | <span data-ttu-id="01d0f-402">✖</span><span class="sxs-lookup"><span data-stu-id="01d0f-402">✖</span></span> | <span data-ttu-id="01d0f-403">✔</span><span class="sxs-lookup"><span data-stu-id="01d0f-403">✔</span></span> |

> [!NOTE]
> <span data-ttu-id="01d0f-404">Ein Karussell kann maximal zehn Karten pro Nachricht anzeigen.</span><span class="sxs-lookup"><span data-stu-id="01d0f-404">A carousel can display a maximum of ten cards per message.</span></span>

### <a name="properties-of-a-carousel-card"></a><span data-ttu-id="01d0f-405">Eigenschaften einer Karussellkarte</span><span class="sxs-lookup"><span data-stu-id="01d0f-405">Properties of a carousel card</span></span>

<span data-ttu-id="01d0f-406">Die Eigenschaften einer Karussellkarte sind mit denen der Helden- und Miniaturkarten identisch.</span><span class="sxs-lookup"><span data-stu-id="01d0f-406">Properties of a carousel card are same as those of the hero and thumbnail cards.</span></span>

### <a name="example-of-a-carousel-collection"></a><span data-ttu-id="01d0f-407">Beispiel einer Karussellsammlung</span><span class="sxs-lookup"><span data-stu-id="01d0f-407">Example of a carousel collection</span></span>

![Beispiel für ein Kartenkarussell](~/assets/images/cards/carousel.png)

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

### <a name="syntax-for-carousel-collections"></a><span data-ttu-id="01d0f-409">Syntax für Karussellsammlungen</span><span class="sxs-lookup"><span data-stu-id="01d0f-409">Syntax for carousel collections</span></span>

<span data-ttu-id="01d0f-410">`builder.AttachmentLayoutTypes.Carousel` ist die Syntax für Karussellsammlungen.</span><span class="sxs-lookup"><span data-stu-id="01d0f-410">`builder.AttachmentLayoutTypes.Carousel` is the syntax for carousel collections.</span></span>

## <a name="list-collection"></a><span data-ttu-id="01d0f-411">Listensammlung</span><span class="sxs-lookup"><span data-stu-id="01d0f-411">List collection</span></span>

### <a name="support-for-list-collections"></a><span data-ttu-id="01d0f-412">Unterstützung für Listensammlungen</span><span class="sxs-lookup"><span data-stu-id="01d0f-412">Support for list collections</span></span>

<span data-ttu-id="01d0f-413">Das Listenlayout zeigt eine vertikal gestapelte Kartenliste, optional mit zugehörigen Aktionsschaltflächen.</span><span class="sxs-lookup"><span data-stu-id="01d0f-413">The list layout shows a vertically stacked list of cards, optionally with associated action buttons.</span></span>

| <span data-ttu-id="01d0f-414">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="01d0f-414">Bots in Teams</span></span> | <span data-ttu-id="01d0f-415">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="01d0f-415">Messaging extensions</span></span>  | <span data-ttu-id="01d0f-416">Connectors</span><span class="sxs-lookup"><span data-stu-id="01d0f-416">Connectors</span></span> | <span data-ttu-id="01d0f-417">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="01d0f-417">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="01d0f-418">✔</span><span class="sxs-lookup"><span data-stu-id="01d0f-418">✔</span></span> | <span data-ttu-id="01d0f-419">✔</span><span class="sxs-lookup"><span data-stu-id="01d0f-419">✔</span></span> | <span data-ttu-id="01d0f-420">✖</span><span class="sxs-lookup"><span data-stu-id="01d0f-420">✖</span></span> | <span data-ttu-id="01d0f-421">✔</span><span class="sxs-lookup"><span data-stu-id="01d0f-421">✔</span></span> |

### <a name="example-of-a-list-collection"></a><span data-ttu-id="01d0f-422">Beispiel für eine Listenauflistung</span><span class="sxs-lookup"><span data-stu-id="01d0f-422">Example of a list collection</span></span>

![Beispiel für eine Kartenliste](~/assets/images/cards/list.png)

<span data-ttu-id="01d0f-424">Die Eigenschaften sind die gleichen wie für die Helden- oder Miniaturansichtskarte.</span><span class="sxs-lookup"><span data-stu-id="01d0f-424">Properties are the same as for the hero or thumbnail card.</span></span>

<span data-ttu-id="01d0f-425">Eine Liste kann maximal zehn Karten pro Nachricht anzeigen.</span><span class="sxs-lookup"><span data-stu-id="01d0f-425">A list can display a maximum of ten cards per message.</span></span>

> [!NOTE]
> <span data-ttu-id="01d0f-426">Einige Kombinationen von Listenkarten werden auf iOS und Android noch nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="01d0f-426">Some combinations of list cards are not yet supported on iOS and Android.</span></span>

### <a name="syntax-for-list-collections"></a><span data-ttu-id="01d0f-427">Syntax für Listensammlungen</span><span class="sxs-lookup"><span data-stu-id="01d0f-427">Syntax for list collections</span></span>

<span data-ttu-id="01d0f-428">`builder.AttachmentLayout.list` ist die Syntax für Listensammlungen.</span><span class="sxs-lookup"><span data-stu-id="01d0f-428">`builder.AttachmentLayout.list` is the syntax for list collections.</span></span>

## <a name="cards-not-supported-in-teams"></a><span data-ttu-id="01d0f-429">Karten, die in Teams nicht unterstützt werden</span><span class="sxs-lookup"><span data-stu-id="01d0f-429">Cards not supported in Teams</span></span>

<span data-ttu-id="01d0f-430">Die folgenden Karten werden vom Bot Framework implementiert, werden jedoch nicht von Teams unterstützt:</span><span class="sxs-lookup"><span data-stu-id="01d0f-430">The following cards are implemented by the Bot Framework, but are not supported by Teams:</span></span>

* <span data-ttu-id="01d0f-431">Animationskarten</span><span class="sxs-lookup"><span data-stu-id="01d0f-431">Animation cards</span></span>
* <span data-ttu-id="01d0f-432">Audiokarten</span><span class="sxs-lookup"><span data-stu-id="01d0f-432">Audio cards</span></span>
* <span data-ttu-id="01d0f-433">Grafikkarten</span><span class="sxs-lookup"><span data-stu-id="01d0f-433">Video cards</span></span>
